<p align="center">
  <img width="96" height="96" alt="zot" src="https://github.com/user-attachments/assets/2577f5e5-ce2e-4c96-b7b5-9c48ac05e4ca" />
</p>

<h1 align="center">Zot</h1>

<p align="center">
  <strong>Stop prompting. Start shipping.</strong>
</p>

<p align="center">
  <a href="https://zot.im">Website</a> · <a href="https://github.com/openzot/openzot">Repository</a> · <a href="https://github.com/openzot/openzot/releases">Releases</a> · <a href="https://openzot.github.io/arcade/">Arcade</a> · <a href="https://openzot.github.io/machinery/">Machinery</a>
</p>

<p align="center">
  <img width="3260" height="2160" alt="zot running a work order" src="https://github.com/user-attachments/assets/a3b74447-85a8-4a0e-be3d-6c88aeed8649" />
</p>

zot is an automated software factory in a single ~11 MiB binary. It takes a
work order - an objective, the acceptance criteria that define done, the
constraints to hold - and plans, edits, builds, tests and fixes until the work
is done. No chat loop, no approving each edit, no hosted engine, no telemetry.
It talks straight to any OpenAI-compatible model provider with your own key.

```bash
curl -fsSL https://zot.im/install.sh | bash
zot new "add input validation to the signup handler and a test"
zot
```

### Why Zot

- **Orders, not prompts.** Files that queue, batch and stream. [→ work orders](https://github.com/openzot/openzot/blob/main/docs/orders.md)
- **Nothing in the way.** Your key, your provider, your machine. [→ philosophy](https://github.com/openzot/openzot/blob/main/docs/philosophy.md)
- **Built to run unattended.** Compaction, loop detection, resumable logs. [→ how it works](https://github.com/openzot/openzot/blob/main/docs/how-it-works.md)
- **Orchestration is content.** No sub-agent framework; skills decide. [→ sub-agents](https://github.com/openzot/openzot/blob/main/docs/how-it-works.md#sub-agents-and-coordination)

Watch it work: the factories run in public, each from one standing order with
no human in the loop.

| Factory | Makes | Repo | Sessions |
| --- | --- | --- | --- |
| [Arcade](https://openzot.github.io/arcade/) | One brand-new browser game per shift, playtested and published | [openzot/arcade](https://github.com/openzot/arcade) | [openzot/arcade](https://huggingface.co/datasets/openzot/arcade) |
| [Machinery](https://openzot.github.io/machinery/) | One working control panel per shift - a live simulation, faults, and its operating manual | [openzot/machinery](https://github.com/openzot/machinery) | [openzot/machinery](https://huggingface.co/datasets/openzot/machinery) |

### Repositories

| Repo                                                  | Description                                                                    |
| ----------------------------------------------------- | ------------------------------------------------------------------------------ |
| [openzot/openzot](https://github.com/openzot/openzot) | The zot software factory CLI                                                   |
| [openzot/actions](https://github.com/openzot/actions) | Official GitHub Actions: run orders, or turn issues into orders, in CI         |
| [openzot/arcade](https://github.com/openzot/arcade)   | A live factory: one browser game every 30 minutes, unattended                  |
| [openzot/machinery](https://github.com/openzot/machinery) | A live factory: one machine per shift - a control panel, its simulation, its manual |

### Ecosystem

| Project                                       | Role                                                                             |
| --------------------------------------------- | -------------------------------------------------------------------------------- |
| [Rook](https://github.com/pdparchitect/rook)  | A fully automated offensive security harness                                     |
| [Pion](https://github.com/pdparchitect/pion)  | A defensive AI security harness for automatic monitoring and incident prevention |
| [Pantalk](https://github.com/pantalk/pantalk) | Connect coding agents to the chat platforms people already use                   |
| [MCPShim](https://github.com/mcpshim/mcpshim) | Turn MCP servers and HTTP APIs into standard CLI commands                        |
| [crmkit](https://github.com/crmkit/crmkit)    | Give agents a shared CRM and system of record over HTTP or MCP                   |
