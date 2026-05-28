# Learning Skills

Learning Skills is a small library of portable agent instruction skills for learning with AI agents.

The goal is to make AI coding agents better teachers: more deliberate, more project-based, more willing to let the learner build by hand, and less likely to rush straight into implementation.

## Skills

| Skill | Description |
| --- | --- |
| [`build-by-learning`](skills/build-by-learning/SKILL.md) | A generic apprenticeship-style teaching protocol for learning technical topics through projects. It makes the agent act as teacher, guide, reviewer, and debugger while the user remains the primary implementer. |

## Installation And Use

Different agents use different names for persistent instructions. Codex can install this as a skill; most other coding agents should use the `SKILL.md` content as project instructions.

### Codex

Copy any skill folder into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
cp -R skills/build-by-learning ~/.codex/skills/
```

Then restart Codex or start a new session so the skill can be discovered.

Invoke the skill by name in chat, or by slash command if your Codex surface exposes one:

```text
Use build-by-learning. I want to learn LangChain agents by building a project step by step.
```

```text
/build-by-learning I want to learn LangChain agents by building a project step by step.
```

### Other Coding Agents

Use the skill file through your agent's normal project-instructions format:

| Agent | Where to put it |
| --- | --- |
| Agents that read `AGENTS.md` | Copy or reference `skills/build-by-learning/SKILL.md` from `AGENTS.md`. |
| Claude Code | Copy or reference it from `CLAUDE.md`. |
| Agents with custom rules or project instructions | Paste the `SKILL.md` content there, or tell the agent to read the file. |
| General chat agents | Paste, upload, or attach the `SKILL.md` file at the start of the session. |

Example:

```text
Follow skills/build-by-learning/SKILL.md as the teaching protocol. I want to learn Kubernetes deployments by building and deploying a small service.
```

## Progress Tracking

The `build-by-learning` skill instructs the agent to create a gitignored local state file:

```text
.build-by-learning-state.md
```

That file tracks the learning goal, curriculum, current step, completed steps, decisions, docs/resources used, and next action.

It is intentionally local working memory, not public documentation.
