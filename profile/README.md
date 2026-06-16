<p align="center">
  <img width="1504" height="1080" alt="zot" src="https://github.com/user-attachments/assets/d12de01c-f13e-451c-93a3-d025b5b39dc6" />
</p>

<h1 align="center">zot</h1>

<p align="center">
  <strong>Stop prompting. Start shipping.</strong>
</p>

<p align="center">
  <a href="https://github.com/openzot/openzot">Repository</a> · <a href="https://chatbotkit.com/apps/code">Get a token</a>
</p>

---

zot is an **autonomous coding agent** for your terminal. You brief it once on the
command line and it plans, edits, and runs your code until the whole job is done -
no prompting, no babysitting, no chat box. A read-only viewer streams every step.

**Fastest way in** - grab a release, point it at a task, and let it run:

```bash
zot "add a /health endpoint to the server and a test for it"
```

### Why zot exists

Coding agents are usually copilots: they wait for a prompt, suggest, and hand the
keyboard back. zot flips that - you describe the job once and it runs the whole
loop (plan → edit → run → verify → exit) without you in it. The agentic loop runs
on a capable cloud harness ([ChatBotKit](https://chatbotkit.com)), so the binary
stays tiny and the local code is small enough to read in one sitting.

### What you get

- **Fully autonomous** - one brief in, a finished job out. No prompt loop.
- **Read-only viewer** - watch the plan, edits, commands, and output stream by.
- **Real tools** - reads, writes, and edits files and runs shell commands in your repo.
- **Project context** - picks up `AGENT.md` and skills from your repo.
- **Tiny and open source** - a single Go binary over a cloud harness.

### Repositories

| Repo                                                  | Description                |
| ----------------------------------------------------- | -------------------------- |
| [openzot/openzot](https://github.com/openzot/openzot) | The zot coding agent (CLI) |
