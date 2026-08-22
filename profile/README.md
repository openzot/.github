<p align="center">
  <img width="96" height="96" alt="zot-icon-dark" src="https://github.com/user-attachments/assets/44908dda-fa7c-4698-815a-82343cf54a44" />
</p>

<h1 align="center">zot</h1>

<p align="center">
  <strong>Stop prompting. Start shipping.</strong>
</p>

<p align="center">
  <strong>≈11 MiB · one native binary · no hosted engine · no telemetry</strong>
</p>

<p align="center">
  <a href="https://zot.im">Website</a> · <a href="https://github.com/openzot/openzot">Repository</a> · <a href="https://github.com/openzot/openzot/releases">Releases</a>
</p>

---

zot is an **open source automated software factory**. It takes **work orders,
not prompts**: a work order is a small YAML file - the durable objective, the
acceptance criteria that define "done", the constraints the work must hold
to - and each order becomes one autonomous run in which zot plans, edits, runs,
and verifies your code until the work is complete.

**Start a factory run** - grab a release, export a provider key, write an
order, and run it:

```bash
export ZAI_API_KEY="..."
zot new "scaffold a tiny http server in go"  # writes .zot/orders/<slug>.yaml
zot                                          # runs your project's book
```

That is the default pair (`zai` + `glm-5.2`). Any other provider is a pair of
flags:

```bash
export ANTHROPIC_API_KEY="sk-ant-..."
zot --provider anthropic --model claude-5-sonnet .zot/orders/scaffold-a-tiny-http-server-in-go.yaml
```

<p align="center">
  <img width="1504" height="1080" alt="zot demo" src="https://github.com/user-attachments/assets/d12de01c-f13e-451c-93a3-d025b5b39dc6" />
</p>

### Why zot exists

Most coding tools optimize the conversation. zot optimizes the production run:
one work order goes in, then the harness plans, edits, runs, and verifies the
work on its own. The agentic loop - thread assembly, compaction, loop detection,
settle mode - runs inside the binary and talks straight to a model provider over
the OpenAI-compatible API. There is no hosted engine and no account beyond the
provider's own, and nothing leaves your machine except the request to the
provider you configured.

The UI is deliberately read-only. There is no text input, because there is no
turn to take: you watch the run, and the working tree is the output.

### What you get

- **Order-to-build automation** - one work order enters the factory and the
  harness runs it to completion; `zot .zot/orders/*.yaml` runs a batch, each order
  its own run, stopping at the first that does not end in success.
- **Done, defined up front** - an order carries acceptance criteria and
  constraints alongside the objective, and `zot new --draft` has your model
  survey the repo (read-only) and propose criteria grounded in its real build
  and test setup, for you to review and edit.
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
zot --provider openrouter --model glm-5.2 .zot/orders/mission.yaml   # sent as z-ai/glm-5.2
zot --provider vercel     --model glm-5.2 .zot/orders/mission.yaml   # sent as zai/glm-5.2
```

On OpenAI, reasoning models use the Responses API automatically, so reasoning
state carries between tool rounds instead of being re-derived each time.

### Runs you can answer for

An autonomous run is unattended by definition: nobody watched it, and by the
time you look the terminal is gone. Every run is written to
`~/.local/state/zot/sessions/` line by line as it happens - the order, the
model, every message and tool call, and how it ended. And every order you ever
ran stays on disk as a file, to be re-run, diffed, or committed.

```bash
zot sessions          # what has run, newest first
zot --resume last     # continue the order the session was started with
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
  ghcr.io/openzot/openzot:latest .zot/orders/add-a-health-endpoint.yaml
```

### Run it from GitHub Actions

An unattended run is exactly the shape of a CI job, so the official
[actions](https://github.com/openzot/actions) put the factory in your
workflows: run the orders committed under `.zot/orders/`, write an order inline for
recurring work on a schedule, or label an issue and have zot draft the order
from it and run it to completion - with the result opened as a pull request.
Provider, model and the full configuration can live in the workflow, with keys
passed as secrets.

```yaml
- uses: openzot/actions/run@v0
  with:
    orders: .zot/orders/*.yaml
    provider: zai
    model: glm-5.2
  env:
    ZAI_API_KEY: ${{ secrets.ZAI_API_KEY }}
```

### Repositories

| Repo                                                  | Description                  |
| ----------------------------------------------------- | ---------------------------- |
| [openzot/openzot](https://github.com/openzot/openzot) | The zot software factory CLI |
| [openzot/actions](https://github.com/openzot/actions) | Official GitHub Actions: run orders, or turn issues into orders, in CI |

### Ecosystem

| Project                                       | Role                                                             |
| --------------------------------------------- | ---------------------------------------------------------------- |
| [Rook](https://github.com/pdparchitect/rook)  | An AI bug-hunting and security-audit agent built on zot's engine |
| [Pantalk](https://github.com/pantalk/pantalk) | Connect coding agents to the chat platforms people already use   |
| [MCPShim](https://github.com/mcpshim/mcpshim) | Turn MCP servers and HTTP APIs into standard CLI commands        |
| [crmkit](https://github.com/crmkit/crmkit)    | Give agents a shared CRM and system of record over HTTP or MCP   |
