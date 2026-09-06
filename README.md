# Luna Skills for Codex

Two portable Codex skills that use GPT-5.6 Luna at Max reasoning for delegated work while keeping the primary agent responsible for synthesis, judgement and the final response.

## Included skills

### Luna Swarm

Divides a substantial task into useful independent workstreams, usually two to four, delegates them concurrently to Luna Max subagents and integrates the results. The primary agent owns the final answer. Simple or sequential tasks run directly.

Invoke it explicitly:

```text
$luna-swarm <substantial task with independent workstreams>
```

### Luna Critic

Challenges a proposed answer before it reaches the user. It checks conversational context, intent, assumptions, evidence, recency, calculations, missing alternatives and unconventional approaches, then requires the primary agent to verify consequential criticism and incorporate justified changes. A supported answer can pass without a cosmetic rewrite.

Invoke it explicitly when desired:

```text
$luna-critic <comparison, recommendation or problem to review>
```

It may also activate automatically for substantial comparisons, recommendations, troubleshooting, planning and problem-solving.

When used together, Swarm completes its work first and Critic reviews the integrated result once with a fresh reviewer. Narrow follow-ups retain the existing decision criteria; an earlier recommendation can change when evidence, priorities or corrected reasoning warrants it.

## Requirements

- A current Codex release with subagent support.
- Access to `gpt-5.6-luna` with `max` reasoning effort.

The skills select Luna Max explicitly for every subagent. They do not require a custom agent file or global subagent model defaults, and they keep whichever primary model you selected. The runtime must expose explicit per-spawn model and effort controls; a skill cannot add missing runtime capabilities.

## Installation

Clone the repository and copy the skill folders into your personal skills directory:

```bash
git clone https://github.com/studer/skills.git theo-skills
mkdir -p ~/.agents/skills
cp -R theo-skills/luna-swarm ~/.agents/skills/
cp -R theo-skills/luna-critic ~/.agents/skills/
```

Open a new Codex chat or refresh the Skills page after installation.

## Repository structure

```text
luna-swarm/
  SKILL.md
  agents/openai.yaml
  assets/icon.svg

luna-critic/
  SKILL.md
  agents/openai.yaml
  assets/icon.svg
```

## Licence

BSD 3-Clause. See [LICENSE](LICENSE).
