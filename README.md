# Assignment Polisher

Project entry for installing and maintaining the skill. See the [public overview](.github/README.md) or [中文介绍](.github/README.zh-CN.md) for examples and fit.

## Installation

```bash
git clone https://github.com/thejaytang/assignment-polisher.git
mkdir -p ~/.codex/skills
cp -R assignment-polisher ~/.codex/skills/
```

Use a new destination or review your existing installation before replacing files. The runtime instructions are in [SKILL.md](SKILL.md). Host loading behavior depends on your agent environment.

## Inputs and usage

Provide readable assignment text. Course excerpts, assignment requirements and writing samples are optional context. Choose `polish`, `polish+notes` or `critique`.

```text
Use $assignment-polisher in polish+notes mode with my draft, course excerpt and writing sample. Preserve facts, citations and my position.
```

The skill does not extract PDF/image text or invent missing evidence. Without writing samples it uses conservative editing rather than claiming to know the author's voice.

## Maintenance

- [Workflow](references/workflow.md): editing order and conflict handling.
- [Profile contract](references/profile-contract.md): optional local profile format.
- [Review cases](references/eval-cases.md): scenarios and manual checks.
- [Agent metadata](agents/openai.yaml): discovery information.

Keep public claims aligned with SKILL.md. No repository-wide license is currently declared.
