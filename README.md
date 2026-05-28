# Learning Skills

Learning Skills is a small library of portable agent instruction skills for learning with AI agents.

The goal is to make AI coding agents better teachers: more deliberate, more project-based, more willing to let the learner build by hand, and less likely to rush straight into implementation.

## Skills

| Skill | Description |
| --- | --- |
| [`build-by-learning`](skills/build-by-learning/SKILL.md) | A generic apprenticeship-style teaching protocol for learning technical topics through projects. It makes the agent act as teacher, guide, reviewer, and debugger while the user remains the primary implementer. |

## Installation And Use

Different agents use different names for persistent instructions. Codex can install this as a skill; most other agents should use the `SKILL.md` content as project instructions, custom rules, or session context.

### Codex

Copy any skill folder into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
cp -R skills/build-by-learning ~/.codex/skills/
```

Then restart Codex or start a new session so the skill can be discovered.

Example invocation:

```text
Use build-by-learning. I want to learn LangChain agents by building a project step by step.
```

### Claude Code

Claude Code does not use Codex skill folders directly. Use the skill as project instructions.

Recommended options:

1. Copy the contents of a skill's `SKILL.md` into your project `CLAUDE.md`.
2. Or reference/paste the skill contents at the start of a learning session.

Example:

```text
Use the instructions in skills/build-by-learning/SKILL.md. I want to learn Rust async by building a small project step by step.
```

### Cursor

Cursor does not use Codex skill folders directly. Use the skill as rules or custom instructions.

Recommended options:

1. Add `skills/build-by-learning/SKILL.md` to the repo and tell Cursor to follow it.
2. Copy the contents into Cursor project rules or user rules.
3. Start a session by explicitly referencing the file.

Example:

```text
Follow skills/build-by-learning/SKILL.md as the teaching protocol. I want to learn Next.js server actions by building a small project.
```

### Windsurf

Windsurf does not use Codex skill folders directly. Use the skill as persistent rules or session instructions.

Recommended options:

1. Add `skills/build-by-learning/SKILL.md` to the repo and ask Windsurf to follow it.
2. Copy the contents into Windsurf rules/custom instructions.
3. Paste the skill at the start of a learning session when persistent rules are not available.

Example:

```text
Use the teaching protocol in skills/build-by-learning/SKILL.md. I want to learn FastAPI by building an API from scratch.
```

### Cline / Roo Code

Cline and Roo Code do not use Codex skill folders directly. Use the skill as custom instructions or project context.

Recommended options:

1. Add `skills/build-by-learning/SKILL.md` to the repo.
2. Add a project instruction telling the agent to read and follow that file.
3. Or paste the skill contents into the agent's custom instructions.

Example:

```text
Read and follow skills/build-by-learning/SKILL.md. Teach me Terraform by having me build and deploy a small stack step by step.
```

### Aider

Aider does not use Codex skill folders directly. Use the skill as context/instructions.

Recommended options:

1. Keep `skills/build-by-learning/SKILL.md` in the repo and add it to the chat context.
2. Copy the relevant instructions into your project conventions/instructions file if you use one.
3. Paste the skill instructions at the start of the session.

Example:

```text
Use skills/build-by-learning/SKILL.md as the collaboration protocol. I want to learn Django by building a small app.
```

### Continue

Continue does not use Codex skill folders directly. Use the skill as custom instructions or referenced context.

Recommended options:

1. Add `skills/build-by-learning/SKILL.md` to the workspace.
2. Reference the file in chat when starting the learning project.
3. Copy the content into your Continue assistant/system instructions if you maintain a custom assistant config.

Example:

```text
Follow skills/build-by-learning/SKILL.md. I want to learn vector search by building a small RAG app.
```

### GitHub Copilot Chat

GitHub Copilot Chat does not use Codex skill folders directly. Use the skill as repository instructions or chat context.

Recommended options:

1. Add `skills/build-by-learning/SKILL.md` to the repo and reference it in chat.
2. Copy the teaching protocol into your repository's Copilot instructions if your setup uses them.

Example:

```text
Follow the learning protocol in skills/build-by-learning/SKILL.md. I want to learn GitHub Actions by building a CI workflow step by step.
```

### ChatGPT, Claude, Gemini, And Other Chat Agents

For general chat agents, use the skill as session instructions.

Recommended options:

1. Paste `skills/build-by-learning/SKILL.md` at the start of the conversation.
2. Upload or attach the file if the agent supports files.
3. Ask the agent to create and maintain a local state file if it has filesystem access.

Example:

```text
Use the attached build-by-learning skill. I want to learn SQL query optimization through a hands-on project.
```

### Generic Coding Agent Pattern

For any other coding agent, use `SKILL.md` as project or session instructions.

Typical options:

- paste `SKILL.md` into the agent's custom instructions
- add it to the repo and ask the agent to follow it
- copy the relevant sections into that tool's preferred instruction file

Example:

```text
Follow the teaching protocol in skills/build-by-learning/SKILL.md. I want to learn Kubernetes deployments by building and deploying a small service.
```

## Progress Tracking

The `build-by-learning` skill instructs the agent to create a gitignored local state file:

```text
.build-by-learning-state.md
```

That file tracks the learning goal, curriculum, current step, completed steps, decisions, docs/resources used, and next action.

It is intentionally local working memory, not public documentation.
