---
name: luna-critic
description: Critically review a proposed answer with one GPT-5.6 Luna subagent at max reasoning before the primary agent replies. Use for substantial comparisons, recommendations, option selection, troubleshooting, planning, and problem-solving, especially follow-ups such as "what about this one?", requests for the best approach, or conversations where prior constraints and explored options must remain stable. Check intent, context, assumption drift, evidence depth, recency, calculations, missing alternatives, and unconventional approaches; then require the primary agent to verify the feedback and rewrite the final answer. Skip simple factual, purely stylistic, or latency-sensitive requests.
---

# Luna Critic

Do not send the first plausible answer. Keep the primary agent responsible for research, judgement, any authorised action, and the final response. Use one Luna reviewer as an adversarial quality gate, not as the final author.

## Establish the context contract

Before drafting, extract the relevant context from the conversation:

- the user's actual objective and the precise scope of the latest question;
- established decision criteria, preferences, constraints, and priorities;
- earlier recommendations and the evidence supporting them;
- options already explored or rejected and the reasons why;
- what, if anything, the latest message genuinely changes.

Treat a newly mentioned product or approach as a request to evaluate it within the existing frame unless the user explicitly asks to restart or re-rank the whole decision. Do not infer endorsement from mere mention. Preserve the existing recommendation unless new evidence changes the ranking under the established criteria.

## Prepare a candidate answer

1. Research and draft a complete candidate answer privately. Do not show it to the user yet.
2. For recommendations or temporally unstable topics, search current sources and prefer primary evidence. First map the option space broadly, then investigate the strongest candidates deeply.
3. Consider categories beyond the already discussed options, including newer approaches, hybrids, the status quo, and credible unconventional solutions. Do not manufacture novelty when the known options genuinely cover the field.
4. Record a concise review packet containing the exact user request, context contract, candidate answer, material assumptions, calculations, and key evidence. Provide conclusions and supporting work, not private chain-of-thought.

## Run the Luna review

Spawn exactly one ordinary subagent as a critical reviewer. Set the spawn model explicitly to `gpt-5.6-luna` and its reasoning effort explicitly to `max`. Do not select or depend on a named custom agent, and do not rely on inherited or globally configured subagent defaults. Use no inherited conversation or a bounded context fork as required by the spawn interface, then include all necessary context in the review packet.

If the runtime cannot explicitly route the subagent to GPT-5.6 Luna at max reasoning, do not silently substitute another model or effort level. State that the required reviewer configuration could not be guaranteed and ask whether to continue with the available subagent configuration.

Give the reviewer only the relevant conversation context and the review packet. Require it to challenge the candidate independently across these dimensions:

1. **Intent and context:** Does the answer address what the user actually asked? Did it ignore prior constraints, rejected options, or the distinction between comparing a new option and changing the recommendation?
2. **Search depth and coverage:** Were the relevant solution categories mapped before narrowing? Are stronger, newer, hybrid, adjacent, or unconventional options missing? Is the answer merely recycling the options already discussed?
3. **Assumptions and evidence:** Which assumptions are unsupported? Are claims based on marketing, weak sources, stale information, or false equivalence? What counterexamples or failure modes could overturn the conclusion?
4. **Facts and calculations:** Independently check material facts, dates, comparisons, units, estimates, and arithmetic. Identify uncertainty that the candidate hides.
5. **Decision integrity:** Is any recommendation change justified by the user's established criteria and comparative evidence, or is it recency bias caused by the newly introduced option?

Allow the reviewer to use available research tools when current evidence or missing alternatives must be checked. Require concise structured feedback with: verdict (`pass`, `minor revision`, or `major rethink`), interpretation of the request, context deviations, missing options, factual or calculation corrections, strongest counterargument, recommended changes, and confidence. Tell it not to write the final answer or spawn further agents.

## Reconcile and rewrite

1. Wait for the reviewer before replying or taking an external action.
2. Assess every criticism independently. Verify material corrections and reject weak or irrelevant objections; do not follow the reviewer blindly.
3. Perform targeted additional research or recalculation when the review exposes a real gap.
4. Rewrite the answer from the primary thread so it directly answers the actual request and incorporates all validated improvements. Do not merely append caveats to the original draft.
5. Distinguish clearly between evaluating an additional option and changing the overall recommendation. If the recommendation changes, explain which established criterion and new evidence changed it. If it does not, say where the new option fits without promoting it artificially.
6. Present one coherent final answer. Mention the internal review only when it materially helps the user understand uncertainty or a corrected conclusion.

If `luna-swarm` is also active, run this critical review after the swarm findings have been reconciled into a candidate answer and before the primary agent writes the final response.
