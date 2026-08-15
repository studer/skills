# Luna Skills for Codex

Two portable Codex skills that use GPT-5.6 Luna at Max reasoning for delegated work while keeping the primary agent responsible for synthesis, judgement and the final response.

## Included skills

### Luna Swarm

Divides a substantial task into two to four independent workstreams, delegates them concurrently to Luna Max subagents, reconciles their findings and requires the primary agent to write and quality-control the final result.

Invoke it explicitly:

```text
$luna-swarm <substantial task with independent workstreams>
```

### Luna Critic

Challenges a proposed answer before it reaches the user. It checks conversational context, intent, assumptions, evidence, recency, calculations, missing alternatives and unconventional approaches, then requires the primary agent to verify the criticism and rewrite the answer.

Invoke it explicitly when desired:

```text
$luna-critic <comparison, recommendation or problem to review>
```

It may also activate automatically for substantial comparisons, recommendations, troubleshooting, planning and problem-solving.

## Requirements

- A current Codex release with subagent support.
- Access to `gpt-5.6-luna` with `max` reasoning effort.

The skills select Luna Max explicitly for every subagent. They do not require a custom agent file or global subagent model defaults.

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
