---
name: luna-critic
description: Use one independent Luna Max reviewer to challenge substantial comparisons, recommendations, troubleshooting and plans before delivery. Especially useful for "what about this option?" follow-ups, context drift and overlooked alternatives. Skip simple facts, purely stylistic edits and latency-sensitive requests.
---

# Luna Critic

Keep the primary agent responsible for judgement, authorised actions and the final answer. Use an independent review to find consequential errors, not to manufacture disagreement.

## Prepare the review

Establish the user's objective, scope, decision criteria, constraints, prior conclusions and rejected options, and what the latest message changes. Separate explicit preferences from assumptions and earlier assistant claims.

Evaluate newly mentioned options within that frame. Mention does not imply endorsement or a request to replace the recommendation. Correct an earlier conclusion when new evidence, changed priorities or a discovered reasoning error warrants it; explain the basis.

Prepare a candidate answer or concrete proposed change with supporting evidence and material calculations. For open-ended problems, consider whether the shortlist misses a stronger category, newer approach, hybrid, status quo or credible unconventional solution. For narrow follow-ups, focus on what changed without automatically reopening the whole search. Verify unstable claims with current primary sources; reuse suitable evidence already gathered.

Provide the reviewer with the exact request, relevant context, candidate, assumptions, evidence and calculations. Include enough original context to let it challenge your interpretation; provide conclusions and supporting work, not private chain-of-thought.

## Obtain one independent review

Spawn one fresh ordinary subagent with `model: gpt-6-luna` and `reasoning_effort: max`, using no inherited conversation or a bounded fork compatible with explicit routing. Do not depend on a named agent or global defaults. If delegation tools or explicit routing are unavailable, do not simulate independent workers or review, or claim this workflow completed. Explain the limitation and ask about an available alternative unless the user has already authorised one; never silently substitute.

Ask the reviewer to check:

- Whether the candidate answers the actual request and respects its context, including the grounds for any recommendation change.
- Unsupported assumptions, weak or stale evidence, material factual or calculation errors, and counterexamples that could change the conclusion.
- Missing solution categories or alternatives that could materially improve the result, including challenges to the problem framing.

Allow targeted independent research where it can resolve these questions. Require a verdict (`pass`, `minor revision` or `major rethink`) and only substantive findings, each with its basis, consequence, proposed correction and uncertainty. A pass without invented objections is valid. Tell the reviewer to remain read-only, avoid external actions, and neither delegate nor write the final answer.

## Resolve and deliver

Review before the final answer or external action implementing the candidate; preparation and read-only work may continue. Verify consequential criticism independently and incorporate justified changes. A supported pass need not trigger a cosmetic rewrite. Use targeted follow-up only for material unresolved issues, not repeated reviews until agreement.

When combined with Luna Swarm, review the primary agent's integrated candidate once, after the workers finish. Keep the reviewer separate from those who produced it. Deliver one coherent answer yourself, identifying any material unresolved limitations.
