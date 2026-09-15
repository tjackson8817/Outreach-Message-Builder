# Outreach Message Builder — User Guide

This tool is a single web page (`outreach_message_builder.html`) that turns your already-researched tracker rows into ready-to-send outreach message drafts. Like the other tools in this family, it runs entirely in your browser: no install, no account, nothing sent anywhere until you copy the prompt and paste it into a Claude chat yourself.

---

## Claude Settings You'll Need Before You Start

| Setting | Why you need it | Where to find it |
|---|---|---|
| **Code execution and file creation** | Always needed — every result now comes back as a downloadable Word document. | **Settings → Capabilities**, toggle it on. |

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
6. Check the parsed list that appears — every field is editable inline, and any row can be removed with the **×** button. A **Target Audience** dropdown appears next to each row — this isn't part of the bulk paste itself, so set it manually per row after parsing if you want it. If **Message Goal** (see Section 5) is set to anything other than "First outreach," a **Context Notes** field also appears per row — see Section 5.

### Adding rows manually

No paste at all? Click **+ Add row manually** to build a row from scratch — company, contact, warm intro path, category, target audience, and (if applicable) context notes, one at a time.

---

## 3. Message Settings

| Field | What it does |
|---|---|
| **Message goal** | First outreach, Follow-up, Thank-you, or Staying in touch. See Section 5 — this changes the actual instructions Claude gets, not just the wording of one instruction. Applies to the whole batch, like Channel and Tone. |
| **Channel** | LinkedIn connection request, LinkedIn InMail/message, or Email. LinkedIn connection requests get a strict ~300-character limit enforced automatically in the generated prompt — Claude is told to count characters, not estimate. **Email** additionally requires a specific Subject line for every variant, tied to the actual company/role/connection point — not a generic "Reaching out." |
| **Tone** | Warm/casual, Formal/executive, or Direct/concise. |
| **Your background** | Optional, same field as the other two tools — paste resume, CV, bio, or a few lines of relevant experience. Grounds the message in something real rather than generic filler. |

---

## 4. Target Audience (Per Row, Optional)

Each parsed or manually-added row gets a **Target Audience** dropdown: *(auto-detect)*, **Recruiter**, **Hiring Manager**, **Cold Outreach**, or **Warm Outreach (referral / existing connection)**.

This is a separate dimension from Warm Introduction Path, not a replacement for it. Warm Introduction Path carries the specific narrative detail (e.g. "former colleague, John Smith, now at this company"). Target Audience gives Claude an explicit, structured signal about *who* the message is going to and *how* it should be framed — a Recruiter is typically screening for fit across many roles, while a Hiring Manager cares more about the specific team and work; Cold Outreach has to establish relevance from scratch, while Warm Outreach can lean on an existing connection.

Leave it on *(auto-detect)* and Claude infers the closest fit from Warm Introduction Path instead — this field is there for when you want to be explicit rather than leave it to inference.

---

## 5. Message Goal & Context Notes

**Message Goal** is a global setting (applies to the whole batch, like Channel and Tone) with four options, each producing genuinely different instructions rather than a reworded version of the same one:

| Goal | Behavior |
|---|---|
| **First outreach** *(default)* | The original behavior — each message shaped by that company's Warm Introduction Path and Target Audience, as described in Section 4. |
| **Follow-up** | For when you already sent a first message and haven't heard back. Claude is told explicitly not to re-introduce yourself or repeat the original pitch, to acknowledge the earlier message without sounding anxious or guilt-tripping about the silence, and to lead with a genuinely new angle if Context Notes gives one — a follow-up with real news reads very differently from a bare "just checking in." Messages are kept noticeably shorter than a first-touch message. |
| **Thank-you** | For after an actual call or interview happened. The message must reference specifics from that company's Context Notes — what was actually discussed — rather than a generic "thank you for your time." If Context Notes is thin or blank for a company, the message stays honestly general instead of inventing details about what was supposedly discussed. If Context Notes mentions an agreed next step, it's referenced naturally. |
| **Staying in touch** | No explicit ask, no disguised pitch. Uses a real reason from Context Notes if you give one (news, a shared connection, something relevant to them); otherwise stays a genuine, low-pressure check-in rather than manufacturing a reason to reach out. |

**Context Notes** is a per-row field (unlike Message Goal, which applies to the whole batch) — it only appears in the row list once Message Goal is set to anything other than "First outreach." Its label and placeholder text change to match the selected goal:

- **Follow-up:** "when you first reached out, and anything new to add" — e.g. *"Sent a LinkedIn connection request Aug 1, no response yet"*
- **Thank-you:** "what you actually discussed (be specific — grounds the message, prevents fabrication)" — e.g. *"45-min call Aug 5 with Jane Doe, discussed their OT team's 2027 hiring plans and Q4 budget approval timeline"*
- **Staying in touch:** "reason for reaching out now (optional)" — e.g. *"Saw their Series C funding news"*

Leaving Context Notes blank is a legitimate choice, not an error — the message just stays appropriately general for that company rather than the tool inventing specifics to fill the gap.

**One setting per run, applied to the whole batch.** Message Goal, Channel, and Tone are all global — every company in a single generated prompt gets the same goal, channel, and tone. If you want a first-outreach email for some companies and a follow-up LinkedIn message for others, that's two separate tool runs (two separate generated prompts), not one — see `sample_prompt.txt` for what a single, real run actually looks like.

---

## 6. Why Every Company Gets a Different Message

The core design principle of this tool: **the same Warm Introduction Path value should produce a structurally different message, not just a name swap.** A company where Warm Introduction Path says "direct — former colleagues" should read differently from one where it says "no direct connection — executive search firm." The first can lean on real shared history; the second has to establish relevance without pretending a relationship exists.

This is why the bulk-paste columns matter — without Warm Introduction Path and Category, the tool would have nothing to differentiate on, and you'd get the same generic message with the company name changed each time.

---

## 7. The Reasoning Line (Not Optional)

For every company, the output includes one line of visible reasoning explaining which approach was taken and why — referencing whichever of Warm Introduction Path, Target Audience, or Context Notes actually applies to the Message Goal selected — e.g. *"Leans on shared history directly since this is a former-colleague connection"* or *"References the Q4 budget timeline mentioned on the call rather than a generic thank-you."*

This is deliberately not something you can turn off. It's how you catch it if a Warm Introduction Path (or Context Notes) got misread — before you've already sent the message. If the reasoning line says something that doesn't match what you know about a company, that's your signal to edit that specific message before using it, not a cosmetic detail to ignore.

---

## 8. The Grounding Guardrail

Same honesty philosophy as the rest of this toolkit, adapted to a different kind of risk. The other tools guard against fabricated *data* (a job posting that doesn't exist, a company statistic that was never verified). This tool guards against fabricated *relationships* — the generated prompt explicitly tells Claude not to invent shared history, mutual connections, or personal specifics that weren't actually provided, and — for Follow-up, Thank-you, and Staying in touch messages specifically — not to invent prior conversation details or a reason for reaching out that Context Notes didn't actually give.

If your Warm Introduction Path for a company is just "recruiter" or "executive search firm," the message should stay appropriately general rather than manufacturing a false personal connection to sound warmer. An honestly generic message — or a thank-you that stays general because Context Notes was left blank — is the correct output in that case, not a flaw to fix.

---

## 9. Output

Every result always comes back as a **downloadable Word document (.docx)** — there's no chat-table option anymore. It's formatted with one heading per company, each message variant labeled (with its Subject line shown for Email), and the reasoning line set apart in italics from the message text itself. This requires the **Code execution and file creation** setting (Settings → Capabilities) to be on; without it, Claude will fall back to a chat response.

---

## 10. Typical Workflow, Start to Finish

1. Run the Target Company Prompt Builder first; get your tracker with Key Contacts, Warm Introduction Path, and Category filled in.
2. Ctrl+click the four relevant columns in your tracker, copy, and paste into this tool's bulk-paste box.
3. Click **Parse rows**, check the preview.
4. Set **Message Goal**. If it's anything other than "First outreach," fill in **Context Notes** per row — specific beats vague, but blank is fine too.
5. Set **Target Audience** per row if you want to be explicit, and set your channel and tone.
6. Copy the generated prompt, paste into a new Claude chat.
7. Review every message *and* its reasoning line before sending anything — this tool drafts, it doesn't send.

---

## 11. Quick Troubleshooting

| Problem | Fix |
|---|---|
| Bulk paste didn't split into 4 clean fields | You likely copied adjacent columns instead of Ctrl+clicking the four specific ones — re-select using Ctrl+click in the exact order: Company, Key Contacts, Warm Introduction Path, Category. |
| A parsed row looks wrong | Edit any field directly in the preview list — Company, Key Contacts, Warm Introduction Path, and Category are all editable inline; Target Audience is a dropdown next to them. |
| Prompt panel just shows placeholder text | You need at least one parsed or manually added row with a Company filled in. |
| Messages feel generic | Check whether Warm Introduction Path and Category actually came through in the paste — a blank Warm Introduction Path gives Claude nothing to differentiate on. Setting Target Audience explicitly per row can also sharpen this. For Follow-up/Thank-you/Staying in touch, also check whether Context Notes is filled in for that row. |
| No Context Notes field appears next to a row | Only shows up when Message Goal is set to something other than "First outreach." Switching the goal re-renders the row list with the field added. |
| A follow-up reads too much like a repeat of the first message | That's by design if Context Notes is blank for that row — without a genuine new angle, the tool keeps follow-ups brief and low-key rather than fabricating a reason to reconnect. Add something to Context Notes if you have it. |
| A thank-you message feels generic | Check that Context Notes actually describes what was discussed — a blank or vague Context Notes intentionally produces a more general (but honest) thank-you rather than invented specifics. |
| LinkedIn connection request feels cut off | That's the ~300-character limit being enforced — try Formal/Direct tone, which tends to fit more information per character than Warm/casual phrasing. |
| Email output doesn't have a Subject line | This should be automatic when Channel is set to Email — if it's missing, ask Claude directly to add a specific Subject line above each message body. |
| In ChatGPT (or another tool), it asks clarifying questions instead of just running the task | The generated prompt now opens with an explicit "execute this directly, don't ask clarifying questions" instruction specifically to head this off — if it still happens, you can restate that instruction even more bluntly as a follow-up message. |
