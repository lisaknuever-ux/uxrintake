# UXR Intake Assistant

A guided front door for UX research requests.

Instead of handing a PM or Designer a nine-section brief template and hoping for the
best, this assistant has a short conversation with them. It sharpens the research
question, challenges leading framing, checks whether the topic was already researched,
recommends a method and sample that will actually answer the question, and then writes
the finished brief into the UXR Roadmap in Notion.

The requester does not need to know what a method is, how many participants they need,
or whether their study counts as foundational or operational. That is the assistant's job.

---

## What it does

| | |
|---|---|
| **Starts with the question, not a form** | The first prompt is open-ended. A topic, a hunch, or even a proposed solution is a valid starting point. |
| **Improves the question out loud** | It reflects back what it understood, names the assumptions baked into the wording, and offers a stronger version. |
| **Checks what we already know** | Searches the Notion research repository before recommending new research. The cheapest study is the one you don't have to run. |
| **Recommends method and rigor** | Method, sample, tool, bias risks, and the EGYM research classification — operational (self-serve) vs. foundational (researcher partnership required). |
| **Writes the ticket** | Fills an existing UXR Roadmap page or creates a new one, keeping the brief headings UXR reviewers expect. |
| **Knows when to escalate** | Foundational, sensitive, or high-risk work gets routed to a human researcher with a strong brief attached. |

It is grounded in Erika Hall's *Just Enough Research* and EGYM's research policy.

---

## Installation

The skill is a single `SKILL.md` file. Every tool below reads that same format —
only the packaging differs.

### GitHub Copilot (CLI or app)

```
/plugin install lisaknuever-ux/uxrintake
```

That is it. The skill appears in your available skills immediately.

### Claude Code

```
/plugin marketplace add lisaknuever-ux/uxrintake
/plugin install uxr-intake@uxrintake
```

If your Claude Code version predates plugin support, copy the skill folder instead:

```bash
git clone https://github.com/lisaknuever-ux/uxrintake.git
cp -r uxrintake/skills/uxr-research-readiness-assistant ~/.claude/skills/
```

### Claude Desktop / claude.ai

1. Download this repository as a ZIP.
2. Zip the folder `skills/uxr-research-readiness-assistant/` on its own.
3. Upload it under **Settings → Capabilities → Skills**.

### Anything else (ChatGPT, Gemini, custom agents)

Paste the contents of
[`skills/uxr-research-readiness-assistant/SKILL.md`](skills/uxr-research-readiness-assistant/SKILL.md)
into the system prompt, custom instructions, or project knowledge of your tool. You lose
the automatic triggering, but the behaviour is identical once invoked.

---

## Required: Notion access

The assistant reads prior research and writes the intake ticket, so it needs a connected
**Notion MCP server** with access to the EGYM UX Research space — specifically the
UXR Roadmap database.

- **Copilot CLI:** `/mcp add` and follow the Notion OAuth flow.
- **Claude Code:** `claude mcp add notion` (or add the Notion server to `.mcp.json`).
- **Claude Desktop:** enable the Notion connector under Settings → Connectors.

Without Notion access the assistant still runs the full intake conversation and hands you
the finished brief as copy-pasteable Markdown. It will tell you up front that it cannot
write the ticket rather than pretending it did.

---

## How to use it

**The normal path** — you already created a page in the UXR Roadmap:

```
UXR Intake for https://www.notion.so/<your-new-page>
```

**Starting from scratch** — no page yet:

```
I want to request UX research on onboarding drop-off
```

Either way, answer the questions in your own words. The assistant shows you the complete
brief and its recommendations before it writes anything to Notion.

Expect roughly 10 minutes and one question at a time.

---

## The Notion side

The UXR Roadmap database carries a template called **"New UXR Request (with Agent)"**.
It opens with a short callout telling requesters how to start the assistant, keeps the
manual instructions in a collapsed toggle for people who would rather type it themselves,
and then lists the usual brief headings for the assistant to fill.

The exact callout markup lives in [`docs/notion-template.md`](docs/notion-template.md)
if you need to rebuild or adapt it.

---

## Repository layout

```
.github/plugin/plugin.json                      Copilot plugin manifest
.claude-plugin/plugin.json                      Claude Code plugin manifest
.claude-plugin/marketplace.json                 Makes the repo its own Claude marketplace
skills/uxr-research-readiness-assistant/
└── SKILL.md                                    The assistant itself
docs/notion-template.md                         Notion template content, copy-paste ready
```

## Contributing

The skill is plain Markdown — no build step, no dependencies. Edit `SKILL.md`, bump the
`version` in the frontmatter and in all three manifests (`.github/plugin/plugin.json`,
`.claude-plugin/plugin.json`, `.claude-plugin/marketplace.json`), add an entry to the
Version History section at the bottom of the skill, and open a pull request.

Behaviour changes are best validated the boring way: run a real intake conversation
against a throwaway page in the UXR Roadmap and read what it writes.

## License

MIT — see [LICENSE](LICENSE).
