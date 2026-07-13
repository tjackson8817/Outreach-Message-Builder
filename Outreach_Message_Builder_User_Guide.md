# Outreach Message Builder — User Guide

This tool is a single web page (`outreach_message_builder.html`) that turns your already-researched tracker rows into ready-to-send outreach message drafts. Like the other tools in this family, it runs entirely in your browser: no install, no account, nothing sent anywhere until you copy the prompt and paste it into a Claude chat yourself.

---

## Claude Settings You'll Need Before You Start

| Setting | Why you need it | Where to find it |
|---|---|---|
| **Code execution and file creation** | Only needed if you choose the downloadable Word document output format — lets Claude build and hand you a real `.docx` instead of a table in chat. | **Settings → Capabilities**, toggle it on. |

Unlike the other two tools in this family, this one doesn't strictly require **Web search** — it's drafting messages from research you've already provided, not looking anything up live. If you want Claude to double-check a detail (like confirming a contact's current title) while drafting, Web search would help, but it's optional here, not load-bearing the way it is for the Job Posting Finder.

---

## 1. How This Fits With the Other Two Tools

Three tools now, each solving a different stage of the same job-hunting workflow:

| Tool | Solves |
|---|---|
| Target Company Prompt Builder | Researches and ranks companies |
| Job Posting Finder | Checks who's actively hiring, right now |
| **Outreach Message Builder** (this tool) | Drafts the actual messages to send |

Same reasoning as the other two: this couldn't be baked into the original research prompt, because it needs data (Key Contacts, Warm Introduction Path, Category) that only exists *after* that research is done.

---

## 2. Building Your Row List

### Bulk paste from your tracker

The tracker's relevant columns — Company, Key Contacts / Priority Titles, Warm Introduction Path, Category — aren't adjacent to each other in the sheet. To copy them together anyway:

1. Click the **Company** column header.
2. **Ctrl+click** (Cmd+click on Mac) the **Key Contacts / Priority Titles**, **Warm Introduction Path**, and **Category** column headers, in that order.
3. Copy (**Ctrl/Cmd+C**) — Excel copies multi-selected non-adjacent columns together, tab-separated, in the order you clicked them.
4. Paste into the **Bulk paste** box.
5. Click **Parse rows**.
6. Check the parsed list that appears — every field is editable inline, and any row can be removed with the **×** button.

### Adding rows manually

No paste at all? Click **+ Add row manually** to build a row from scratch — four fields, one row at a time.

---

## 3. Message Settings

| Field | What it does |
|---|---|
| **Channel** | LinkedIn connection request, LinkedIn InMail/message, or Email. LinkedIn connection requests get a strict ~300-character limit enforced automatically in the generated prompt — Claude is told to count characters, not estimate. |
| **Tone** | Warm/casual, Formal/executive, or Direct/concise. |
| **Your background** | Optional, same field as the other two tools — paste resume, CV, bio, or a few lines of relevant experience. Grounds the message in something real rather than generic filler. |

---

## 4. Why Every Company Gets a Different Message

The core design principle of this tool: **the same Warm Introduction Path value should produce a structurally different message, not just a name swap.** A company where Warm Introduction Path says "direct — former colleagues" should read differently from one where it says "no direct connection — executive search firm." The first can lean on real shared history; the second has to establish relevance without pretending a relationship exists.

This is why the bulk-paste columns matter — without Warm Introduction Path and Category, the tool would have nothing to differentiate on, and you'd get the same generic message with the company name changed each time.

---

## 5. The Reasoning Line (Not Optional)

For every company, the output includes one line of visible reasoning explaining which approach was taken and why — e.g. *"Leans on shared history directly since this is a former-colleague connection"* or *"Opens with relevance rather than a relationship, since there's no existing connection to draw on."*

This is deliberately not something you can turn off. It's how you catch it if a Warm Introduction Path got misread — before you've already sent the message. If the reasoning line says something that doesn't match what you know about a company, that's your signal to edit that specific message before using it, not a cosmetic detail to ignore.

---

## 6. The Grounding Guardrail

Same honesty philosophy as the rest of this toolkit, adapted to a different kind of risk. The other tools guard against fabricated *data* (a job posting that doesn't exist, a company statistic that was never verified). This tool guards against fabricated *relationships* — the generated prompt explicitly tells Claude not to invent shared history, mutual connections, or personal specifics that weren't actually provided.

If your Warm Introduction Path for a company is just "recruiter" or "executive search firm," the message should stay appropriately general rather than manufacturing a false personal connection to sound warmer. An honestly generic message is the correct output in that case — not a flaw to fix.

---

## 7. Output Format

- **Table in chat** (default) — one section per company, each message variant labeled, with the reasoning line visually set apart (italics or a blockquote) from the message text itself.
- **Downloadable Word document** — same structure, formatted as a `.docx` with a heading per company.

---

## 8. Typical Workflow, Start to Finish

1. Run the Target Company Prompt Builder first; get your tracker with Key Contacts, Warm Introduction Path, and Category filled in.
2. Ctrl+click the four relevant columns in your tracker, copy, and paste into this tool's bulk-paste box.
3. Click **Parse rows**, check the preview.
4. Set your channel and tone.
5. Copy the generated prompt, paste into a new Claude chat.
6. Review every message *and* its reasoning line before sending anything — this tool drafts, it doesn't send.

---

## 9. Quick Troubleshooting

| Problem | Fix |
|---|---|
| Bulk paste didn't split into 4 clean fields | You likely copied adjacent columns instead of Ctrl+clicking the four specific ones — re-select using Ctrl+click in the exact order: Company, Key Contacts, Warm Introduction Path, Category. |
| A parsed row looks wrong | Edit any field directly in the preview list — all four are editable inline. |
| Prompt panel just shows placeholder text | You need at least one parsed or manually added row with a Company filled in. |
| Messages feel generic | Check whether Warm Introduction Path and Category actually came through in the paste — a blank Warm Introduction Path gives Claude nothing to differentiate on. |
| LinkedIn connection request feels cut off | That's the ~300-character limit being enforced — try Formal/Direct tone, which tends to fit more information per character than Warm/casual phrasing. |
