---
name: campaign-evidence-review
description: Reviews a client's marketing evidence (platform or lead data plus customer voice such as surveys, reviews, win-loss notes, and support themes), compares it with the last review, and gives ranked recommendations. Use for the weekly review, channel performance checks, or deciding where to look next.
---

# Campaign evidence review

Turn two kinds of evidence into a short set of recommendations the lead can act on this week.

- **Evidence A** is what the platforms, store, or CRM say happened. It is precise and easy to game.
- **Evidence B** is what customers say. It is messy and honest.

Good recommendations come from setting the two side by side, and from knowing what we said last time. Follow the steps in order.

## Step 1: Load the client

Use the **client-brain** skill. Load the profile, targets, last review, open tests, and learnings. Load the frameworks `evidence-hierarchy` and `capture-vs-create`. For a client with a long sales cycle, also load `long-sales-cycle`.

If no targets exist, say so and carry on with what you have. Do not invent targets.

## Step 2: Get the evidence

- For the demo clients, call `list_evidence`, then `get_evidence` for each dataset.
- For other clients, use the connectors or files the person has provided.

Note the date range. If either evidence set is missing, say so before you go on. Do not review one set as if it were both.

**Check what is new.** Compare the end date of the evidence with the period of the last review. If nothing is newer, there is nothing to review. Say so in two sentences. List what still waits on the lead: open questions, open tests with their dates, and proposals. Then stop. Do not write or save a new review. If the lead says "run it anyway", carry on.

## Step 3: Check the data before you judge it

Write a short "Data quality" list. Look for each of these.

- **Tracking breaks.** Spend and clicks with zero orders for a week. Exclude that week from the campaign's return and flag it.
- **Partial runs.** A campaign that ran for fewer weeks than the others. Compare per week, not in total.
- **Double counting.** Total the platform-reported revenue and compare it with the store's total. Work out the over-claim ratio (platform total divided by store total). Use it to scale platform figures down. Say the scaled figures are estimates.
- **Blended campaigns.** Campaigns that mix brand and non-brand traffic hide what works. Flag them.
- **Process changes.** A form, tag, or tracking change can move volume and quality together. Check the notes column and the sudden jumps.
- **Immature outcomes.** In a long sales cycle, recent weeks have no closed outcomes yet. Judge them on leading measures only. Show how many proposals or sales sit behind any win rate.
- **Small groups.** Any survey group under 30 people, any campaign with fewer than 30 orders, or any source with fewer than 10 proposals. Say "directional only".
- **Capture versus create.** Brand search, retargeting, and email mostly collect demand that something else created. Their high return is not proof of impact.

## Step 4: Score each campaign on Evidence A

For each campaign or source, show:

- Spend and share of total spend
- Reported return, and the scaled return after the over-claim adjustment
- The cost of winning a customer, lead, or meeting, scaled in the same way
- The trend across the weeks: rising, flat, or falling

For lead-generation clients, use cost per qualified lead, cost per meeting, proposals sent, and win rate on resolved proposals only.

Then compare the totals with the targets. State which targets were met and missed.

## Step 5: Read Evidence B

Pull out why customers bought and where they came from.

- Where customers first heard of the brand, and how first order value and repeat rate differ by source.
- What customers praise, and what they complain about.
- Any gap between what the brand says and what customers say.
- Any behaviour that hides a channel's effect, such as people who see something and search for the brand later.

## Step 6: Set the two side by side

Build a table with one row per channel.

| Channel | Share of platform-claimed new customers or leads | Share of customer-reported source | Gap |

Read the gaps with the evidence hierarchy.

- **Customer share much higher than platform share:** the channel probably does more than the platform shows.
- **Platform share much higher than customer share:** the platform is probably collecting credit for demand created elsewhere.
- **Both agree:** you can trust the picture more.

Say which source you lean on for each channel, and why.

## Step 7: Give each campaign a verdict

| Verdict | Use when |
| --- | --- |
| **Scale** | Beats the targets after adjustment, and Evidence B supports it. |
| **Fix** | The idea works but something specific is broken. Name the fix. |
| **Protect** | Looks strong but mostly captures demand. Hold it at its current level. |
| **Test** | The evidence conflicts or is too thin. Name the test. |
| **Cut** | Misses the targets on both sets of evidence, with enough data to be sure. |

**Cut** needs both evidence sets to agree. If they conflict, use **Test**.

## Step 8: Write the recommendations

Write at most five, ranked by expected impact. For each give:

1. **Action.** One sentence that starts with a verb.
2. **Why.** The two or three numbers or customer points that support it.
3. **Confidence.** High, Medium, or Low.
4. **What would change my mind.** One sentence.
5. **Cost of being wrong.** Low, Medium, or High, with a few words on why.

Respect the budget limits in the profile. Do not suggest moving more than the stated share of a channel's budget in one cycle.

## Step 9: Compare with last time

Look at the last review's recommendations and open questions.

- For each recommendation, say whether the evidence shows it was acted on, whether it still stands, or whether events overtook it. If you cannot tell, list it as "open" and ask the lead.
- Say whether each open question is now answered, and how.
- If a recommendation has now appeared in two reviews in a row with no sign of action, say so plainly. Rank it higher and say what it is costing.
- Check the test log. Report on any test that is running or past its end date.
- If an open test's last full week is now in the evidence, judge it against the success rule set before it began, with the numbers. Say whether it won, lost, or was inconclusive, and what it teaches. If the rule used platform figures, check the store figures too. Ask the lead before you record the result with `save_test` and save what it taught as a learning. Record only the status, the result, and what it taught. Do not change the test's rules or dates.

## Step 10: Save to the brain

Use the **client-brain** skill. Call `log_review` with the headline, scorecard, verdicts, recommendations, data quality notes, and open questions. Add up to three learnings the evidence supports. If a new finding contradicts an old learning, replace the old one.

## Output format

Keep the review to about one page.

1. **Headline.** Two sentences. The one thing the lead must know, and what to do about it.
2. **Scorecard.** Targets against actuals. A small table.
3. **Since last review.** Bullets. What was done, what changed, what is still open.
4. **Data quality.** Bullets. Only the issues that change a decision.
5. **Where the evidence agrees and disagrees.** The table from step 6, plus two or three sentences.
6. **Recommendations.** The ranked list from step 8.
7. **What we cannot tell yet.** Bullets. Be honest.

## Rules

- State every figure in the client's currency.
- Mark estimates as estimates.
- Round sensibly. Say "about 18%", not "17.96%".
- Never write a recommendation you cannot trace to evidence in front of you.
- If the evidence does not answer the question, say so, then say what evidence would.
- You advise. The lead acts. Never say you changed anything in an ad account.
- Keep sentences short and plain. Cut anything that does not help the lead decide.
