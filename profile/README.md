<p align="center">
  <img src="https://zot.im/icon-dark.svg" alt="zot" width="96" height="96" />
</p>

<h1 align="center">zot</h1>

<p align="center">
  <strong>Stop prompting. Start shipping.</strong>
</p>

<p align="center">
  <a href="https://github.com/openzot/openzot">Repository</a> · <a href="https://chatbotkit.com/apps/code">Get a token</a>
</p>

---

zot is an **open source automated software factory**. Give it a job and its
autonomous coding harness plans, edits, runs, and verifies your code until the
work is complete.

**Start a factory run** - grab a release and give it a software brief:

```bash
zot "scaffold a tiny http server in go"
```

<p align="center">
  <img width="1504" height="1080" alt="zot demo" src="https://github.com/user-attachments/assets/d12de01c-f13e-451c-93a3-d025b5b39dc6" />
</p>

### Why zot exists

Most coding tools optimize the conversation. zot optimizes the production run:
one software brief goes in, then the harness plans, edits, runs, and verifies the
work on its own. The agentic loop runs on a capable cloud harness. The default
backend is [ChatBotKit](https://chatbotkit.com); the built-in relay backend can
use your OpenAI or OpenRouter key instead. Either way, the binary stays tiny and
the local code is small enough to read in one sitting.

### What you get

- **Brief-to-build automation** - one job enters the factory and the harness
  runs it to completion.
- **Real tools** - reads, writes, and edits files and runs shell commands in
  your repo.
- **Visible production run** - watch the plan, edits, commands, and verification
  stream by.
- **Project context** - picks up `AGENT.md` and skills from your repo.
- **Tiny and open source** - a single Go binary over an autonomous coding
  harness.

### Repositories

| Repo                                                  | Description                  |
| ----------------------------------------------------- | ---------------------------- |
| [openzot/openzot](https://github.com/openzot/openzot) | The zot software factory CLI |

### Ecosystem

| Project                                       | Role                                                           |
| --------------------------------------------- | -------------------------------------------------------------- |
| [Pantalk](https://github.com/pantalk/pantalk) | Connect coding agents to the chat platforms people already use |
| [MCPShim](https://github.com/mcpshim/mcpshim) | Turn MCP servers and HTTP APIs into standard CLI commands      |
| [crmkit](https://github.com/crmkit/crmkit)    | Give agents a shared CRM and system of record over HTTP or MCP |
