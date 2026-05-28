# Learning Skills

Reusable `SKILL.md` instructions for turning AI coding agents into better learning partners.

These skills are meant for project-based learning: the agent teaches, guides, reviews, and debugs while the learner stays actively involved in the work.

## Available Skills

| Skill | Use it when |
| --- | --- |
| [`build-by-learning`](skills/build-by-learning/SKILL.md) | You want to learn a technical topic by building a real project step by step, with the agent acting as teacher and reviewer instead of quietly doing all the work. |

## Quick Start

The best default is to keep the skill in the repo where you are learning. That makes the teaching protocol visible, versioned, and easy to share with the same project.

Copy the skill folder into your project:

```bash
mkdir -p .agents/skills
cp -R skills/build-by-learning .agents/skills/
```

Then tell your agent to use it from your project instructions, for example in `AGENTS.md`:

```md
Use `.agents/skills/build-by-learning/SKILL.md` when I ask to learn a technical topic by building a project.
```

Start a session with:

```text
Use build-by-learning. I want to learn LangChain agents by building a small project step by step.
```

## Agent Setup

Different agents discover persistent instructions differently. Use the most native option for your tool:

| Agent or setup | Recommended setup |
| --- | --- |
| Codex, personal reuse | Copy `skills/build-by-learning` to `${CODEX_HOME:-$HOME/.codex}/skills/build-by-learning`. |
| Claude Code, project-local | Copy it to `.claude/skills/build-by-learning`. The skill can be invoked directly as `/build-by-learning` or triggered naturally by matching requests. |
| Agents that read `AGENTS.md` | Keep the skill in the repo, then reference it from `AGENTS.md`. |
| Agents with custom rules | Paste the `SKILL.md` content into project rules, or add the file to the repo and tell the agent to follow it. |
| General chat agents | Upload, attach, or paste the `SKILL.md` file at the start of the session. |

For Codex global install:

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R skills/build-by-learning "${CODEX_HOME:-$HOME/.codex}/skills/"
```

Restart Codex or start a new session so the skill can be discovered.

## Repository Layout

```text
skills/
  build-by-learning/
    SKILL.md
```

Each skill is self-contained in its own folder. `SKILL.md` contains YAML frontmatter for discovery plus the instructions the agent should follow when the skill is active.

## Adding Skills

New skills should be:

- focused on one reusable learning workflow
- useful across more than one project
- written as instructions an agent can actually follow
- concise enough to load into context without wasting attention
- packaged as `skills/<skill-name>/SKILL.md`

Add the new skill to the table above with a plain-language description of when to use it.

## Contributing

Contributions are welcome, but all pull requests should go through the repository owner for now. Open an issue or PR with the proposed skill or change, and wait for review before assuming it will be merged.
