# Mini Agentic Lab Lite

**A weekly marketing review that remembers each brand, by [T.ǓR](https://thisistur.com).** Lite edition, version 1.0, November 2026. Free to use, change, and share (MIT licence).

You set up a marketing agent inside Claude. No code. Each week you give it your evidence: what your ad platforms and shop report, and what your customers say. It checks the data, scores you against your targets, gives each campaign a verdict, and ranks up to five things to do next. It keeps a memory of each brand, so the next review starts where the last one stopped.

It advises. You decide.

**The demo.** T.ǓR is the marketing lead running the agent. Fernhill Outdoor, a trail running brand, is its client. Fernhill and every figure about it are invented, so you can try the whole thing before you use your own data.

**Time:** about 30 minutes to set up and run the demo. **Cost:** nothing beyond a paid Claude plan.

---

## What is in this kit

| Folder or file | What it holds |
| --- | --- |
| `PDF` | This guide, a sample review, and the answer key, ready to read or print |
| `01-setup` | The project instructions, and the two skills zipped for upload. The unzipped skills are there too, so you can read and change them |
| `02-brain` | The demo brand's memory (`fernhill-brain.md`), the methods the agent reasons with (`frameworks.md`), and a blank brain for your own brand |
| `03-evidence` | Eight weeks of demo evidence for Fernhill, and blank templates for your own brand |
| `04-check-your-work` | A sample review and the answer key. Read the key after your run, not before |
| `LICENSE` | MIT. Use it, change it, share it |

The kit says "client" throughout, because it also serves consultants and agencies. For an in-house team, read "brand": anything with its own budget, targets, and customers.

---

## Before you start

- [ ] A paid Claude plan: Pro, Max, Team, or Enterprise.
- [ ] Code execution switched on, because skills need it. On Pro or Max: **Settings > Capabilities**, then turn on **Code execution and file creation** (it may be called **Create and edit files**). On Team or Enterprise, an owner turns it on under **Organization settings > Plugins & skills**, on the **Policy** tab, and must allow skills there too.
- [ ] The kit unzipped somewhere easy, such as `Documents/mini-agentic-lab-lite`.

---

## Step 1. Create the project

- [ ] In Claude, create a new Project. Call it **Marketing Agent**.
- [ ] Open `01-setup/project-instructions.md` in any text editor.
- [ ] It says the agent works for **T.ǓR**, the demo's marketing lead. Leave that for the demo, or put in your own name or team. Change the writing style under **How to write** if you like.
- [ ] Copy everything below the line `---`.
- [ ] Paste it into the project's **Instructions** box. Save.

## Step 2. Install the two skills

A skill is a set of steps that tells Claude how to do one job well. The zips are in `01-setup/skill-zips`. Do this twice, once per zip:

- [ ] Go to **Customize > Skills**.
- [ ] Click **+**, then **+ Create skill**, then **Upload a skill**.
- [ ] Choose the zip. Do not unzip it or rename it.
- [ ] Check the skill shows as switched on.

The two are:

- `client-brain`: loads and saves each brand's memory.
- `campaign-evidence-review`: runs the weekly review.

If you cannot see **+ Create skill** or **Upload a skill**, code execution is off. See "Before you start".

## Step 3. Add the brain and the evidence

Add six files to the project's files:

- [ ] From `02-brain`: `fernhill-brain.md` and `frameworks.md`. Leave `blank-client-brain.md` for now.
- [ ] From `03-evidence/fernhill`: all four files.

**Check:** open a new chat in the project and ask: "What clients are in the brain, and what evidence can you see?" It should name Fernhill and list four evidence files.

---

## Step 4. Run the weekly review

In a new chat in the project, paste:

```
Run the weekly review for Fernhill.
Use the client-brain skill to load the brain, then the campaign-evidence-review skill.
Read both evidence sets before you recommend anything.
Compare with the last review, and save the new review when you finish.
```

It takes a few minutes. You get:

- **A headline:** the answer first, in two or three sentences.
- **A scorecard:** each target, the actual figure, and met or missed.
- **Since last review:** what changed, what was done, and what is still waiting.
- **Data checks:** what is broken or missing, and what it left out because of it.
- **A verdict per campaign:** Scale, Fix, Protect, Test, or Cut, with the reason.
- **Up to five recommendations,** ranked, each with a confidence level.
- **A block to save** to the brain.

Pass if:

- [ ] It loaded the brain before it reviewed anything.
- [ ] It compared platform revenue with the store. The platforms over-claim by about 1.37 times.
- [ ] It left the TikTok week of 12 October out, because the tracking tag was missing.
- [ ] It said what changed since the last review (R-1).
- [ ] Five recommendations or fewer, each with a confidence level.
- [ ] It did not cut TikTok, cut the podcast, or put more money into brand search.

Now open `04-check-your-work/answer-key-fernhill.md`. It lists the eleven things planted in the evidence. A good review need not find all of them. It must not get any of them wrong.

`04-check-your-work/sample-weekly-review.md` shows a full review from a test run, so you can compare.

## Step 5. Save it, and see the memory work

The memory is what makes this an agent and not a one-off prompt. Each review starts from the last one: what you were told to do, whether you did it, and what is still open.

Claude cannot change project files. So at the end of a review, it gives you a block of text and says where it goes, such as "the top of the Review log in `fernhill-brain.md`".

- [ ] Open `fernhill-brain.md` on your computer.
- [ ] Paste the block where it says. Save the file.
- [ ] In the project, remove the old `fernhill-brain.md` and add the new one.

Now paste the Step 4 prompt again, in a new chat.

- [ ] It says no new evidence has arrived, lists what is still waiting on you, and does **not** write a second review.

That is the agent checking its own memory before it spends your time. Next week, replace the evidence files with the new week's, and it picks up from there.

---

## Put your own brand in

The steps use T.ǓR, id `tur`, as the worked example. Put in your own brand's name and id wherever you see them. The id is short, all lower case, with no spaces.

### 1. Gather the facts

Rough answers are fine. You can correct them later.

| What | Example answer (from the Fernhill demo) |
| --- | --- |
| What the brand sells, to whom, and the numbers that matter | "Trail running apparel, online in Australia. Average order AUD 118, margin 62%." |
| Who buys, and what they care about | "Club runners, 28 to 50. They trust friends over ads." |
| What the brand says it stands for, in its own words | "Ultralight, ultra warm." |
| The channels, named exactly | Meta, Google, TikTok creators, Email |
| The most any one channel's budget may move in a week | 15% |
| Two or three targets, with a number each | "MER at least 3.0", "New customer cost no more than AUD 90" |
| How your data misleads | "Platforms over-claim against the store." |
| Currency | AUD |

### 2. Gather the evidence

The agent needs two kinds of evidence. It needs both, because the gap between them is where most of its insight comes from.

- **Evidence A: what your systems report.** Ad platforms, plus your shop or CRM.
- **Evidence B: what customers say.** A survey, reviews, support tickets, and sales notes.

Blank files with the right headings are in `03-evidence/templates`. Pick the ones that fit:

| Business type | File | What goes in it, one row per week | Where it usually comes from |
| --- | --- | --- | --- |
| Online sales | `evidence-a1-platform-performance.csv` | Per campaign: spend, impressions, clicks, and the orders, revenue, and new customers the platform claims | Ads Manager exports from Meta, Google, TikTok, and the like, set to weekly and by campaign |
| Online sales | `evidence-a2-store-totals.csv` | What the shop actually recorded: orders, revenue, new and returning customers | Your shop's sales and customer reports (Shopify, WooCommerce, or similar) |
| Leads and deals | `evidence-a1-leads-by-source.csv` | Per source: spend, leads, qualified leads, meetings, proposals, deals won and lost, and value won | Your CRM's report by original source (HubSpot, Salesforce, Pipedrive, or similar) |
| Any | `evidence-b1-customer-survey.csv` | Answers to "How did you first hear about us?", counted by answer | A post-purchase survey, or a field on your enquiry form |
| Any | `evidence-b2-customer-voice.md` | Themes from reviews, support, and sales calls, each with a count. Also your main message per channel, and anything unusual that week | Review sites, your help desk, call notes, and your own team |

**How much:** four weeks of Evidence A and any customer voice at all is enough to start. Eight weeks is better. After that, add one more week each time.

**Rules for every file:**

- `week_start` is the Monday, written `2026-11-02`.
- Money as plain numbers in the brand's currency: `5426`, not `$5,426`.
- Platform claims and shop or CRM figures stay in separate files.
- Use the `notes` column for anything odd: tracking breaks, bulk orders, sales, price changes.
- No personal data: no customer names, emails, or phone numbers. Paraphrase quotes.

No customer voice at all? Add "How did you first hear about us?" to your order confirmation or enquiry form today, with a fixed list of answers. In a month you will have the agent's best evidence.

### 3. Add the brand

- [ ] Copy `02-brain/blank-client-brain.md`. Rename the copy `tur-brain.md`.
- [ ] Fill in its Profile and Targets sections from step 1. Leave the three logs as they are.
- [ ] Add it to the project.
- [ ] Add your evidence files. If the project holds more than one brand, start each file name with the brand's id, such as `tur-evidence-a1-platform-performance.csv`, so names never clash.
- [ ] Remove the Fernhill files from the project when you no longer need the demo.

### 4. Run it

Use the Step 4 prompt with your brand's name instead of Fernhill, and add one line: "The evidence files are in the project files." Read the first review closely, and check every number before it goes to a colleague. Then save it to the brain, as in Step 5.

### 5. Make the thinking yours

The judgement lives in the skills, not in Claude. Read `01-setup/skills/campaign-evidence-review/SKILL.md` as a team. Agree the verdict rules (when to Scale, Fix, Protect, Test, or Cut), and change them to fit. One hour on what "Cut" means saves weeks of arguing with the reports.

After you change a skill, zip its folder (on a Mac, right-click and choose **Compress**), then upload it again in **Customize > Skills**, replacing the old one.

To add your own methods, add them to the end of `frameworks.md` and upload it again.

---

## Rules for real work

- The agent can be wrong. Check any number before it goes to a colleague or a client.
- Keep personal customer data, passwords, and bank details out of the brain.
- Check your contracts and your company's data rules before you put business data into any tool.

## If something goes wrong

| What you see | What to do |
| --- | --- |
| No **Upload a skill** option, or the skills do not appear | Code execution is off. Turn it on (see "Before you start"). On Team or Enterprise, ask an owner to allow skills |
| A skill will not upload | Upload the zip from `01-setup/skill-zips` as it is. Do not unzip it or rename it |
| Claude ignores a skill | Name the skill in your prompt, as the Step 4 prompt does |
| Claude says it cannot see the evidence | Add the four files from `03-evidence/fernhill` to the project, not only the brain files |
| It writes a second review on the same evidence | The new review was not saved into the brain file. Redo Step 5 |
| A review invents a number | Ask: "Which of these figures are in the evidence, and which did you estimate?" |
| A review is too long | Say "Keep it to one page", and add that rule to the project instructions |

---

## Want the full version? It'll cost you a coffee

Lite does the weekly review. The full Mini Agentic Lab turns it into a marketing team that works while you do something else.

| | Lite | Full |
| --- | --- | --- |
| Weekly evidence review, with memory | Yes | Yes |
| Budget and test plan, within your limits | No | Yes |
| Creative brief built from what customers say | No | Yes |
| Positioning check: each brand claim against why people buy | No | Yes |
| Judges its own tests when they finish, and asks before it records the result | No | Yes |
| A hosted brain that saves by itself, so no copying and pasting | No | Yes |
| A weekly schedule in Claude, so the review arrives on Monday | No | Yes |
| The code version: an agent that fetches your evidence, runs the weekly cycle on GitHub, and waits for your approval before anything changes | No | Yes |
| A second demo client (a B2B accounting firm), two more weeks of demo evidence, and four sample outputs | No | Yes |
| The step-by-step SOP with a test log, and the answer keys for every test | No | Yes |

**[Get the Full edition for the price of a coffee](https://buymeacoffee.com/thisistur/e/596835)**

buymeacoffee.com/thisistur/e/596835

_Mini Agentic Lab Lite, by [T.ǓR](https://thisistur.com). MIT licence._
