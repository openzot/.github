<p align="center">
  <img width="96" height="96" alt="zot-icon-dark" src="https://github.com/user-attachments/assets/44908dda-fa7c-4698-815a-82343cf54a44" />
</p>

<h1 align="center">zot</h1>

<p align="center">
  <strong>Stop prompting. Start shipping.</strong>
</p>

<p align="center">
  <a href="https://zot.im">Website</a> · <a href="https://github.com/openzot/openzot">Repository</a> · <a href="https://github.com/openzot/openzot/releases">Releases</a>
</p>

---

zot is an **open source automated software factory**. Give it a software brief
and its autonomous coding harness plans, edits, runs, and verifies your code
until the work is complete.

**Start a factory run** - grab a release, export a provider key, and give it a
brief:

```bash
export ZAI_API_KEY="..."
zot "scaffold a tiny http server in go"
```

That is the default pair (`zai` + `glm-5.2`). Any other provider is a pair of
flags:

```bash
export ANTHROPIC_API_KEY="sk-ant-..."
zot --backend anthropic --model claude-5-sonnet "..."
```

<p align="center">
  <img width="1504" height="1080" alt="zot demo" src="https://github.com/user-attachments/assets/d12de01c-f13e-451c-93a3-d025b5b39dc6" />
</p>

### Why zot exists

Most coding tools optimize the conversation. zot optimizes the production run:
one software brief goes in, then the harness plans, edits, runs, and verifies the
work on its own. The agentic loop - thread assembly, compaction, loop detection,
settle mode - runs inside the binary and talks straight to a model provider over
the OpenAI-compatible API. There is no hosted engine and no account beyond the
provider's own, and nothing leaves your machine except the request to the
provider you configured.

The UI is deliberately read-only. There is no text input, because there is no
turn to take: you watch the run, and the working tree is the output.

### What you get

- **Brief-to-build automation** - one job enters the factory and the harness
  runs it to completion.
- **Real tools** - reads, writes, and edits files and runs shell commands in
  your repo.
- **Visible production run** - watch the plan, edits, commands, and verification
  stream by; `--diff` shows a syntax-highlighted diff under every write.
- **Any provider** - fourteen backends ship built in, plus anything else that
  speaks the same API.
- **Project context** - picks up `AGENT.md` and skills from your repo.
- **Resumable** - every run is logged to disk as it happens, so an unattended
  run that stopped can be read back and picked up where it left off.
- **Tiny and open source** - one Go binary, no hosted service, no telemetry.

### Bring your own provider

`openai`, `anthropic`, `groq`, `mistral`, `deepseek`, `openrouter`, `together`,
`cerebras`, `xai`, `moonshot`, `zai`, `qwen`, `vercel` and a local `ollama` are
built in, each reading its provider's conventional environment variable - so
switching is a flag rather than a configuration exercise. Anything else that
speaks the OpenAI chat-completions API works as a `custom` backend with a base
URL and a key.

Model gateways are first class. OpenRouter, the Vercel AI Gateway and
Cloudflare's AI Gateway each route by a creator-qualified model name, and each
spells the creator differently - so zot supplies the right prefix from its own
catalogue and sizes the context budget to the real model behind it:

```bash
zot --backend openrouter --model glm-5.2 "..."   # sent as z-ai/glm-5.2
zot --backend vercel     --model glm-5.2 "..."   # sent as zai/glm-5.2
```

On OpenAI, reasoning models use the Responses API automatically, so reasoning
state carries between tool rounds instead of being re-derived each time.

### Runs you can answer for

An autonomous run is unattended by definition: nobody watched it, and by the
time you look the terminal is gone. Every run is written to
`~/.local/state/zot/sessions/` line by line as it happens - the brief, the model,
every message and tool call, and how it ended.

```bash
zot sessions                                  # what has run, newest first
zot --resume last "now add the tests you skipped"
zot --resume last                             # or continue the original brief
```

### Run it in a container

Official Linux amd64 and arm64 images are published to GHCR from every release
tag. The agent works in `/workspace`, which is also the practical answer to a
tool that has real shell access - it can only touch the volume you mounted:

```bash
docker run --rm -it \
  --user "$(id -u):$(id -g)" --env HOME=/tmp \
  --env ZAI_API_KEY \
  --volume "$PWD":/workspace \
  ghcr.io/openzot/openzot:latest "add a /health endpoint and a test for it"
```

### Repositories

| Repo                                                  | Description                  |
| ----------------------------------------------------- | ---------------------------- |
| [openzot/openzot](https://github.com/openzot/openzot) | The zot software factory CLI |

### Ecosystem

| Project                                       | Role                                                             |
| --------------------------------------------- | ---------------------------------------------------------------- |
| [Rook](https://github.com/pdparchitect/rook)  | An AI bug-hunting and security-audit agent built on zot's engine |
| [Pantalk](https://github.com/pantalk/pantalk) | Connect coding agents to the chat platforms people already use   |
| [MCPShim](https://github.com/mcpshim/mcpshim) | Turn MCP servers and HTTP APIs into standard CLI commands        |
| [crmkit](https://github.com/crmkit/crmkit)    | Give agents a shared CRM and system of record over HTTP or MCP   |
