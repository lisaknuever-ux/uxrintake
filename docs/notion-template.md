# Notion template: "New UXR Request (with Agent)"

This is the content of the UXR Roadmap template that points requesters at the assistant.
Keep it in sync with the live template if either side changes.

- **Database:** UXR Roadmap — `collection://151d894d-d22a-815d-afc4-000b31967acd`
- **Template page:** `3add894d-d22a-8158-af84-fc4617aa7cd3`

## Why it is built this way

Three constraints shaped it:

1. **The instruction has to be the first thing you see.** A requester who opens a blank
   brief starts typing. The callout has to interrupt that before it happens.
2. **The manual path must stay available.** Not everyone has the plugin installed, and a
   template that only works with an AI assistant is a template that blocks people. The
   old instructions live in a collapsed toggle — present, but not competing for attention.
3. **The brief headings stay untouched.** The assistant writes into them, and UXR
   reviewers read them in a fixed order. Changing them breaks both.

The assistant removes the callout, the toggle, and the divider once it has written the
brief, since instructions are noise in a finished ticket.

## Content

Below the properties, the page body is:

---

> 🤖 **Fill this brief with the UXR Intake Assistant — it takes about 10 minutes.**
>
> The assistant asks you a handful of questions, sharpens your research question, checks
> whether we already researched this, recommends a method, and then writes this page for you.
>
> **1. Install it once** (Copilot CLI: `/plugin install lisaknuever-ux/uxrintake` ·
> Claude and other tools: see the [setup guide](https://github.com/lisaknuever-ux/uxrintake)).
>
> **2. Copy this page's URL** (top right → Copy link).
>
> **3. Start the conversation** by pasting: `UXR Intake for <paste URL>`
>
> Answer the questions in your own words. You do not need to know the right method, sample
> size, or research type — that is the assistant's job. It will show you the finished brief
> before anything is written here.

*(Blue background callout, robot icon.)*

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
3. Name it `New UXR Request (with Agent)`.
4. Paste the content above.
5. Optionally set it as the default template so it is what people get by default.
