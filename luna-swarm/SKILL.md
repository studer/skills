---
name: luna-swarm
description: Coordinate parallel Luna Max workers and integrate their results. Use only when explicitly invoked for substantial research, analysis or implementation with independent workstreams; avoid forced parallelism for simple or sequential tasks.
---

# Luna Swarm

Keep the current primary agent as coordinator, integrator and final author. Apply the user's request in its conversational context, including established constraints and subsequent corrections.

## Delegate useful work

Choose independent assignments whose benefit justifies delegation overhead, usually two to four, within available concurrency. If fewer than two useful workstreams exist, handle the task directly and briefly explain why. Keep tightly coupled decisions and cross-cutting integration with the primary agent.

Spawn ordinary workers explicitly with `model: gpt-6-luna` and `reasoning_effort: max`. Use no inherited conversation or a bounded fork compatible with explicit routing. Do not depend on a named agent or global defaults. If delegation tools or explicit routing are unavailable, do not simulate independent workers or review, or claim this workflow completed. Explain the limitation and ask about an available alternative unless the user has already authorised one; never silently substitute.

Give each worker a bounded task, relevant context and evidence, success criteria, and permitted files or actions. Require findings with sources or file references, unresolved issues and relevant checks. Instruct workers not to delegate further or author the final response. Preserve the parent task's safety, permission, scope and source-quality requirements in every assignment.

Run independent assignments concurrently while doing useful coordinator work. Avoid duplicating their investigation. Assign disjoint files for concurrent edits; keep external mutations with the primary agent and check uncertain outcomes before retrying.

## Integrate and finish

Collect required results before synthesis. If a worker fails or stalls, recover its assignment with a targeted retry or complete it in the primary thread; disclose any remaining gap. Reuse workers for narrow follow-ups when helpful.

Resolve material conflicts from the underlying evidence, not majority agreement. Integrate changes and perform checks proportionate to the task's remaining risks. Stop expanding research once the requested deliverable is supported.

Write the final answer yourself, reflecting the user's original objective and material uncertainties. If Luna Critic is also active, let it provide the single fresh review of the integrated candidate before delivery; do not add separate Swarm or per-worker reviews.
