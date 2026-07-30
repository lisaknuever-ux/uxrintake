# Notion template: "UXR Briefing Agent"

This is the content of the UXR Roadmap template that points requesters at the assistant.
Keep it in sync with the live template if either side changes.

- **Database:** UXR Roadmap — `collection://151d894d-d22a-815d-afc4-000b31967acd`
  (database page `151d894d-d22a-802e-826d-ce09e46f2958`)
- **Registered template, and the source of truth:**
  `3add894d-d22a-80b8-bc68-e7fe4b6e3795` — "UXR Briefing Agent". This is the one that
  appears in the template picker, so it is the page stakeholders actually get. The content
  documented below is what lives here.
- **Default template:** `15ad894d-d22a-8078-848d-e5f89589029b` — "New UXR Request". It
  deliberately still carries the old content with no mention of the assistant, because the
  team wants to run both variants side by side for a while.

> **Note on the surplus copies.** Two further pages carry the same content but are *not*
> registered templates — they are ordinary database rows left over from the rebuild, and
> both are meant to be cleaned up:
>
> - `3add894d-d22a-8158-af84-fc4617aa7cd3` — "New UXR Request (with Agent)". Despite the
>   name, Notion does not know it as a template. This file previously named it as the
>   source of truth, which was wrong.
> - `3add894d-d22a-80cf-8662-c52650bdeea5` — "DUPLICATE — do not use · UXR Briefing Agent".
>   Carries a red callout marking it as scheduled for deletion.
>
> They are currently kept in sync by hand. If you change one, change all of them — or
> better, archive the two surplus copies and leave only the registered template.
>
> This confusion is the whole reason for this section: four near-identical pages existed and
> nobody could tell which one Notion actually served. Verify against the database's
> `page_templates` field, not against a page's title.

To check which page is really the template:

```
page_templates       → the registered non-default templates
default_page_template → the one used when you just click "New"
```

Both are fields on the UXR Roadmap database `151d894d-d22a-802e-826d-ce09e46f2958`.

## Why it is built this way

Four constraints shaped it:

1. **The instruction has to be the first thing you see.** A requester who opens a blank
   brief starts typing. The callout has to interrupt that before it happens — hence the
   opening line "Don't fill this in", which is blunt on purpose.
2. **Nobody installs a plugin without a reason.** The "Why use the assistant instead of
   typing this yourself?" toggle exists to earn the two minutes of setup. It is collapsed,
   so it costs nothing to the people who are already convinced, and it is there for the
   ones who would otherwise close the page and type the brief by hand.
3. **The manual path must stay available.** Not everyone has the plugin installed, and a
   template that only works with an AI assistant is a template that blocks people. The
   old instructions live in a collapsed toggle — present, but not competing for attention.
4. **The brief headings stay untouched.** The assistant writes into them, and UXR
   reviewers read them in a fixed order. Changing them breaks both.

**Installation is two commands, not one.** An earlier version of this template showed a
single `/plugin install lisaknuever-ux/uxrintake`. That was simply wrong — the marketplace
has to be registered first — and people ran it, got an error, and gave up. The setup toggle
now shows both commands in the right order.

**The setup toggle can be short because the plugin carries the Notion connection.** As of
v0.7.0 the Notion MCP server ships inside the plugin, so the setup section no longer has to
walk anyone through `/mcp add`, a JSON config file, or a per-tool connector. What is left is
one browser approval with a normal Notion login. The manual route still exists in the
[setup guide](https://github.com/lisaknuever-ux/uxrintake) and the toggle links there for the
cases where the bundled connection does not take effect.

The assistant removes the callout, all three toggles, and the divider once it has written
the brief, since instructions are noise in a finished ticket.

## Content

Below the properties, the page body is:

---

> 🤖 **Don't fill this in. Let the UXR Intake Assistant do it — about 10 minutes, one question at a time.**
>
> It turns a rough idea into a research brief our team can act on: it sharpens your
> question, checks whether we already have the answer, and picks the right method for you.
> Then it writes this page.
>
> **1. Copy this page's URL** — top right → Copy link.
>
> **2. Open GitHub Copilot** (CLI or desktop app) **and paste:** `UXR Intake for <your URL>`
>
> **3. Answer in your own words.** No research jargon required.
>
> You will see the finished brief and its recommendations before a single word lands on this page.
>
> *First time? Open "One-time setup" below — it takes two minutes.*

*(Blue background callout, robot icon.)*

---

▸ **Why use the assistant instead of typing this yourself?** *(toggle, collapsed)*

> Because a good brief is the difference between research that changes a decision and
> research that gets read once and forgotten. The assistant does the parts that are
> genuinely hard:
>
> - **It sharpens your question.** It reflects back what it understood, names the
>   assumptions hidden in your wording, and offers a stronger version. "Do users like the
>   new dashboard?" becomes something that can actually be answered.
> - **It checks what we already know.** Before recommending anything, it searches our
>   research repository. The cheapest study is the one you don't have to run — and you
>   might get your answer in five minutes instead of five weeks.
> - **It picks the method for you.** Method, sample size, tool, and the bias risks to watch
>   out for. You do not need to know what a diary study is, or how many participants make a
>   finding trustworthy.
> - **It tells you straight whether you can run it yourself.** Operational research you can
>   self-serve; foundational or sensitive work gets routed to a researcher — with a strong
>   brief already attached, so nothing stalls.
> - **It will tell you when research is the wrong tool.** Sometimes what you need is a
>   workshop, an analytics pull, or a decision. A brief that says so honestly saves everyone
>   weeks.
> - **It writes the ticket.** Every section below, filled in properly, in the order our
>   reviewers expect. No blank fields, no "we'll come back to you for more detail".
>
> The short version: you bring the problem, it brings the research craft.

---

▸ **One-time setup (two minutes)** *(toggle, collapsed)*

> **GitHub Copilot — CLI or desktop app**
>
> Run these two commands in the Copilot chat composer:
>
> ```
> /plugin marketplace add lisaknuever-ux/uxrintake
> /plugin install uxr-intake@uxrintake
> ```
>
> The first registers this repository as a plugin source, the second installs the
> assistant. Restart Copilot afterwards.
>
> **Notion access**
>
> The assistant needs to read our past research and write to this page, so it connects to
> Notion. The connection ships with the plugin — you only have to approve it once in your
> browser with your normal Notion login. It then sees exactly the pages you can see,
> nothing more.
>
> If no login prompt appears, or the assistant says it cannot reach Notion, follow the
> *Notion access* section in the [setup guide](https://github.com/lisaknuever-ux/uxrintake)
> to add the connection manually.
>
> **Claude Code, Claude Desktop, ChatGPT, or anything else**
>
> The assistant works there too. The
> [setup guide](https://github.com/lisaknuever-ux/uxrintake) has a section for each.
>
> **Check it worked**
>
> Ask your tool: *"Search Notion for the UXR Roadmap."* If you get results back, you are ready.

---

▸ **Rather fill it in manually?** *(toggle, collapsed)*

> That is completely fine — the brief below works on its own.
>
> 1. **Rename** the title "New UXR Request" above with your topic.
> 2. Add your name under **Requester**.
> 3. Leave the other properties empty.
> 4. **Fill out the brief below** with the needed information. We will come back to you if
>    we need more information.

---

# UX Research Brief

## Project topic & team
*What's the initiative, feature, … that needs to explored? Who is the responsible team?*

## Background
*What's the background of this research project? e.g.: What is happening that makes this research relevant right now? What do you already know? Where do you lack understanding or confidence to move forward?*

## Stakeholders
*Who are the relevant stakeholders and what are their roles on this project? (You can use the RACI logic, if applicable)*

## Business objectives
*What business goal or KPIs does this research project contribute to?*

## Research objectives
*What is the goal of this research project? What are you seeking to learn / understand? What decisions will this research inform?*

## Research questions
*Do you already have specific questions / hypothesis / assumptions in mind that should be explored? If so, what are they based on?*

## Target Group
*Who is the relevant target group we want to learn from in this research project? Are there specific recruitment criteria (e.g. customer behaviour, demographics) that should apply to participants who take part in the research? Are there already existing contacts we could use?*

## Timeline
*What's the expected timeline to have the research results? Are there any important milestones / deadlines / dependencies that should be kept in mind?*

## Additional input / material
*Is there any additional input related to this project that you feel is important to share?*

---

## Rebuilding it in Notion

The Notion API cannot register a page as a database template, so this step is manual:

1. Open the **UXR Roadmap** database.
2. Click the arrow next to **New** → **New template**.
3. Name it `UXR Briefing Agent`.
4. Paste the content above.
5. Optionally set it as the default template so it is what people get by default.

> **Write the new page ID into this file straight away.** A template created through the UI
> gets a fresh page ID that nothing else knows about. Skipping this step is exactly how the
> repo ended up documenting a page that was never a registered template, while four
> near-identical copies drifted apart and the one people actually saw went stale. Update the
> ID list at the top of this file, and the known-template list in
> `skills/uxr-research-readiness-assistant/SKILL.md`, in the same commit.

The registered template page is `3add894d-d22a-80b8-bc68-e7fe4b6e3795`. If you edit it in
Notion, mirror the change here in the same commit — this file is the only version-controlled
copy.
