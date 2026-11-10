---
name: client-brain
description: Loads and saves a client's memory (profile, targets, past reviews, tests, and learnings) so work for each client builds on the last. Use at the start and end of any client marketing task, when onboarding a new client, or when asked what we know or decided about a client.
---

# Client brain

You work for a marketing lead who looks after one or more clients: brands, markets, or product lines in-house, or outside clients for a consultant. Each client has a brain: what we know, what we decided, and what we tried. Load it before you work. Save to it when you finish. Never mix clients.

## Which mode are you in?

- **Hosted mode.** A connector with tools such as `get_client_brain` and `log_review` is available. Use those tools.
- **File mode.** No such tools exist, but brain files do. In a Claude Project, each client is one file, `<client>-brain.md`, with the sections Profile, Targets, Review log, Test log, and Learnings, plus a shared `frameworks.md`. In Google Drive, each client may be a folder, `clients/<client>/`, with `profile.md`, `targets.md`, `review-log.md`, `test-log.md`, and `learnings.md`.
- **Neither.** Say so in one sentence. Offer to onboard the client now (see below) and give the person the files to keep.

## At the start of any client task

1. **Find the client.** Use the name in the request. If it is unclear, call `list_clients` and ask once. Never guess between clients.
2. **Load the brain.** Call `get_client_brain`, or read the client's brain file (or its five files).
3. **Load the frameworks you need.** Call `get_frameworks` for the ones that fit: `evidence-hierarchy`, `capture-vs-create`, `test-design-checklist`, `message-market-fit`, `long-sales-cycle`.
4. **Hold on to four things:** the targets, the last review's recommendations and open questions, any open tests, and the learnings.
5. **Use the brain. Do not recite it.** Do not read the profile back to the person. Let it shape your work.

Treat learnings as things we believed, not as facts. If new evidence contradicts one, say so plainly.

## At the end of the task

Save what will still matter in a month. Not more.

| What | When | How |
| --- | --- | --- |
| The review | After every weekly review | `log_review` |
| A test | When the person agrees to run it | `save_test`, with the status `planned` |
| A test result | When a test ends | `save_test` with its id, status, result, and what was learned |
| A learning | When the evidence supports a durable finding | `add_learning` |

Rules for learnings:

- One plain sentence. Add tags, a confidence level, and a source such as a review or test id.
- Save at most three per task. If you have more, keep the three that matter most.
- If a new learning replaces an old one, pass the old id as `supersedes`. Never delete.
- Do not save guesses as facts. Low confidence is fine. Speculation is not.

After you save in a chat, tell the person in one line what you saved. In a scheduled run, save without asking, and do not create or start tests. Put suggested tests in the review instead.

## Never save

- Personal details of customers or leads.
- Passwords, keys, tokens, or bank details.
- Raw data exports. The brain holds conclusions, not data.

## Onboarding a new client

Ask these questions in one message. Keep it short. Accept "not sure" as an answer.

1. What does the business sell, and what are the main commercial facts (price, margin, sales cycle)?
2. Who buys?
3. How does the business describe itself in one line?
4. Which channels run today, and what is the weekly spend?
5. What targets do you judge success by, and how are they measured?
6. What are the limits (budget, team capacity, things we must not do)?
7. What do you already know about where the numbers mislead?
8. How often should we review?

Then call `save_client` with a short id, the name, the profile, and the targets. Use the person's words. Write "not yet known" for gaps. Do not invent. Read back a three-line summary and ask them to correct it.

In file mode, write the whole `<id>-brain.md` instead, in the same layout as the other brain files, with empty logs. Give it to the person to save and add to the project.

## File mode: how to save

- Add each new review at the **top** of the Review log (the section in `<client>-brain.md`, or `review-log.md`), in the same layout as the existing entries.
- Add each test to the Test log, and update it in place when it ends.
- Add each learning to the top of the Learnings. To replace one, add the new line and mark the old one `[replaced by L-n]`.
- Number new items from the highest existing number.
- If you cannot write to the files, give the person the exact block to paste. Say which file and which section it goes in, and that it goes at the top of that section.
- Put those blocks at the end of your reply, under the heading "Save to the brain". Keep the headline and the rest of the work about the client, not about saving.

## Monthly tidy

When asked, or when a client has more than about 25 active learnings:

1. Find duplicates and near-duplicates. Replace them with one clear line.
2. Raise or lower confidence where later evidence supports it.
3. List open tests that are past their end date and ask what happened.
4. Show the person the changes before you save them.
