---
name: luna-swarm
description: Run a coordinated parallel subagent workflow in which the primary agent decomposes a substantial task, delegates independent workstreams to GPT-5.6 Luna subagents at max reasoning, reconciles their findings, and personally writes and quality-controls the final result. Use only when explicitly invoked for research, analysis, review, planning, or implementation tasks that contain at least two genuinely independent workstreams. Do not use automatically for simple, tightly sequential, or latency-sensitive requests.
---

# Luna Swarm

Treat the remainder of the user's prompt as the task. Keep the primary agent as coordinator, integrator, final author, and accountable decision-maker.

## Orchestrate

1. Identify the task's shared objective, constraints, deliverable, and success criteria.
2. Divide it into independent, non-overlapping workstreams. Prefer two to four meaningful workstreams, capped by available concurrency. Do not invent filler work merely to use more agents.
3. Spawn one ordinary subagent per workstream concurrently. Set every spawn model explicitly to `gpt-5.6-luna` and its reasoning effort explicitly to `max`. Do not select or depend on a named custom agent, and do not rely on inherited or globally configured subagent defaults. Use no inherited conversation or a bounded context fork as required by the spawn interface, then provide every worker with the context needed for its assignment.
4. Give each worker only the context and evidence needed for its bounded assignment. Require concise conclusions, supporting evidence or file references, uncertainties, and conflicts discovered. Tell workers not to perform the final synthesis or spawn further agents.
5. Continue useful coordinator-only work while the workers run, then wait for every required result.

If fewer than two genuinely independent workstreams exist, state that briefly and execute the task directly instead of forcing parallelism.

If the runtime cannot explicitly route subagents to GPT-5.6 Luna at max reasoning, do not silently substitute another model or effort level. State that the required worker configuration could not be guaranteed and ask whether to continue with the available subagent configuration.

## Control parallel work

- For research and analysis, separate sources, perspectives, systems, or evaluation criteria.
- For code or file changes, assign disjoint files or components. Never let workers edit overlapping areas concurrently. Keep integration and cross-cutting edits with the primary agent.
- For external or irreversible actions, let workers investigate or prepare only. The primary agent must perform any authorised mutation exactly once.
- Preserve the parent turn's safety, permission, scope, and source-quality requirements in every assignment.

## Reconcile and deliver

1. Compare all worker results for contradictions, duplicated assumptions, missing coverage, stale facts, weak sources, and incompatible recommendations.
2. Resolve material conflicts by checking the underlying evidence directly or, when necessary, sending a narrow follow-up to the relevant worker.
3. Independently verify that the result satisfies the original request and its constraints. For implementation work, integrate the changes and run the relevant checks from the primary thread.
4. Write the final response or deliverable from the primary thread. Do not paste a worker's answer as the final result and do not delegate final synthesis.
5. Present one coherent conclusion, clearly labelling unresolved uncertainty and material limitations. Mention the internal work split only when it helps the user understand the result.
