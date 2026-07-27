# Outreach Message Builder

A single self-contained HTML tool that turns your already-researched tracker rows into ready-to-send outreach message drafts — tailored per company, not a generic template with the name swapped in.

**[Open the live tool](https://tjackson8817.github.io/Outreach-Message-Builder/outreach_message_builder.html)**

No install, no account, nothing sent anywhere — it's a static form that assembles text entirely in your browser.

## Third tool in this family

This is the third companion tool, alongside:
- **[Target-Company-Prompt-Builder](https://tjackson8817.github.io/Target-Company-Prompt-Builder/prompt_builder.html)** — researches and ranks companies
- **[Job-Posting-Finder](https://tjackson8817.github.io/Job-Posting-Finder/job_posting_finder.html)** — checks who's actively hiring, right now

This tool takes a shortlist from that research — with Key Contacts, Warm Introduction Path, and Category already filled in — and drafts the actual messages. Same reasoning as the other two: this couldn't be baked into the original research prompt, because it needs data that only exists after that research is done.

## Files in this repo

| File | What it is |
|---|---|
| `outreach_message_builder.html` | The interactive tool. Open it directly in any browser, or use the GitHub Pages link above. |
| `Outreach_Message_Builder_User_Guide.md` | Full usage guide — bulk-paste setup, message settings, and why the reasoning line is never optional. |
| `Outreach_Message_Builder_User_Guide.docx` | Same guide, as a Word document. |

## Quick start

1. Open `outreach_message_builder.html` (via GitHub Pages, or download and double-click it).
2. In your tracker, Ctrl+click (Cmd+click on Mac) the Company, Key Contacts / Priority Titles, Warm Introduction Path, and Category column headers, in that order, then copy.
3. Paste into the tool's bulk-paste box and click **Parse rows**.
4. Set your channel (LinkedIn connection request, LinkedIn message, or Email) and tone.
5. Copy the generated prompt and paste it into a new Claude chat.
6. Review every message *and* its reasoning line before sending anything — this tool drafts, it doesn't send.

See `Outreach_Message_Builder_User_Guide.md` for the full walkthrough.

## What makes this different from a generic message template

Three things, all non-optional in the generated prompt:

- **A visible reasoning line for every company**, explaining which approach was taken and why, tied to that company's specific Warm Introduction Path (and Target Audience, if set) — so you can catch it if a connection type got misread before you send anything.
- **A grounding guardrail against fabricated relationships.** If a company's Warm Introduction Path is vague (e.g. just "recruiter"), the message stays honestly general rather than inventing false shared history to sound warmer. A generic-but-honest message is the correct output in that case, not a flaw.
- **An optional per-row Target Audience** (Recruiter, Hiring Manager, Cold Outreach, or Warm Outreach) that further shapes each message's framing — a Recruiter message reads differently from a Hiring Manager message, independent of the Warm Introduction Path.

## Notes

- This repo can be public or private — GitHub Pages on the free tier requires a public repo (or a paid plan for private-repo Pages).
- Unlike the other two tools in this family, this one doesn't strictly require the Web search capability in Claude — it drafts from research you already provide, not a live lookup.
- Choosing Email as the channel automatically requires a specific Subject line for every drafted variant, not a generic one.
- The generated prompt opens with an explicit "execute this directly, don't ask clarifying questions" instruction, aimed at other AI tools (e.g. ChatGPT) that sometimes respond with questions instead of just running the task.
