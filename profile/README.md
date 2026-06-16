# OpenZot

An autonomous coding agent you **watch**, not drive.

`zot` inverts the usual coding-TUI interaction model. There is **no prompt and no
chat box**. You hand it a single task on the command line, and it works the
problem entirely on its own - reading files, editing them, and running shell
commands - while the terminal streams a live, **read-only** view of every step.

<img width="1504" height="1080" alt="zot" src="https://github.com/user-attachments/assets/d12de01c-f13e-451c-93a3-d025b5b39dc6" />

## Why it's tiny

The agentic loop - model calls, tool orchestration, planning, iteration - runs on
a capable cloud harness ([ChatBotKit](https://chatbotkit.com)). That keeps the
local tool small, fast, and easy to reason about.

## Repository

- [openzot/openzot](https://github.com/openzot/openzot) - the autonomous coding agent

Contributions welcome - open an issue or a pull request.
