# Agent Comms

A simple, markdown-based communication channel for AI agents and humans.

Everything lives in plain markdown files that you can read, edit, and review yourself. Agents talk to each other through a shared conversation log (`AGENTS_CONVERSATION.MD`), governed by a rules file (`AGENT_COMMUNICATION_RULES.md`) that you control. There is no backend, no database, no lock-in — just markdown in your repo.

**You are a first-class participant.** You can read what your agents are saying to each other, jump into the conversation, reply to messages, hand off tasks, and change the communication rules whenever you want.

## What it does

- Creates a shared message log that any agent (or human) can append to
- Structures communication with identity headers, message types, and thread archival
- On first skill invocation, the agent is instructed to bootstrap the repo if the comms files are missing
- Works with any coding agent that can read and write files

## Install

```bash
npx skills add Abbiirr/agent-comms
```

For Claude Code with non-interactive install:

```bash
npx skills add Abbiirr/agent-comms --agent claude-code --yes --copy
```

After installing, invoke the skill normally. On first invocation, the skill instructs the agent to run bootstrap if the comms files are missing.

**Codex:**
```
Use $agent-comms to bootstrap this repository.
```

**Claude Code:**
```
/agent-comms bootstrap this repository
```

## Any other agent

No special install needed. Just run `setup.sh` to bootstrap the files, then point your agent at `AGENT_COMMUNICATION_RULES.md` and `AGENTS_CONVERSATION.MD`. Any agent that can read and write markdown can participate.

```bash
bash scripts/setup.sh --root /path/to/your/repo
```

## What gets created

| File | Purpose |
|------|---------|
| `AGENT_COMMUNICATION_RULES.md` | The rules — you own this, change it whenever you want |
| `AGENTS_CONVERSATION.MD` | The conversation log — append-only, shared by everyone |
| `docs/communication/old/` | Archive for resolved threads |

## Manual setup (fallback)

```bash
# Codex
bash .agents/skills/agent-comms/scripts/setup.sh

# Claude Code
bash .claude/skills/agent-comms/scripts/setup.sh
```

Run `--help` for options like `--force`, `--no-inject-agents-md`, or `--root <path>`.

## License

[MIT](LICENSE)
