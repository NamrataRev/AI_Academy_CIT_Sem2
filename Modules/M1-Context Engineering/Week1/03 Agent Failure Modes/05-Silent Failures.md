# Silent Failures

---

You ask a friend what time a shop closes. They do not know. But instead of saying "I am not sure, let me check" — they confidently say "6pm."

You arrive at 5:45pm. The shop closed at 5pm.

The worst part is not that they were wrong. It is that they showed no sign of uncertainty. No hesitation. No "I think" or "probably." Just a confident, wrong answer delivered as fact. You had no reason to double-check.

This is a silent failure. And it is the most dangerous of the four failure modes.

---

## What It Is

A silent failure happens when the agent cannot complete the task — but instead of saying so, it fills the gap with something plausible and presents it as a real result.

The tool returned an error. Or the search found nothing useful. Or the information simply does not exist. The agent hits a dead end.

But it does not say "I could not find this." It generates what a good answer would look like — drawing from its training data — and delivers it confidently. The output looks complete. It looks researched. There is nothing in the response that signals anything went wrong.

---

## What It Looks Like

A student asks an agent: *"What is the current pass rate for the AWS Solutions Architect exam this year?"*

The agent searches. The search returns general study guides and old statistics — nothing current. The agent has no real answer.

But it produces:

*"The current pass rate for the AWS Solutions Architect Associate exam is approximately 65-70%, based on recent candidate reports."*

That number came from nowhere. Or from outdated training data. The agent generated it because generating a plausible answer is what language models do. The student reads it, trusts it, and uses it in a presentation.

There is no footnote saying "I could not verify this." No asterisk. No uncertainty. Just a confident, fabricated statistic.

---

## Why It Happens

Language models are trained to be helpful. Saying "I do not know" feels like a failure. Generating a plausible answer feels like success.

When a tool returns nothing useful, the agent faces a choice: admit the gap or fill it. Filling it is the more natural response for a language model — it is what the training optimised for. Nobody explicitly told the agent that "I could not find this" is also a valid and correct answer.

---

## Why It Is the Most Dangerous

The other three failure modes give you signals.

A hallucinated tool call — the tool name looks odd. An infinite loop — the agent keeps running. Scope creep — the output is far too long.

A silent failure gives you nothing. The output looks exactly like a correct answer. It is well-formatted, confident, and complete. The only way to detect it is to independently verify every claim — which defeats the purpose of using an agent in the first place.

---

## How to Prevent It

**Instruct the agent explicitly** — *"If a search returns no useful results, say so clearly. Do not generate information that did not come from a tool result."* This one instruction prevents most silent failures.

**Require citations** — if the agent must cite the specific search result behind every claim, fabricated answers become impossible to hide. A claim with no citation is a signal that something went wrong.

**Make "I could not find this" acceptable** — build your evaluation to treat honest uncertainty as a correct response, not a failure. If the agent is penalised for not answering, it will answer — correctly or not.

---

## Quick Recap

- A silent failure happens when the agent cannot complete the task but presents a confident answer anyway
- It happens because language models are trained to generate plausible responses — admitting uncertainty goes against that tendency
- It is the most dangerous failure mode because there is no signal that anything went wrong
- Prevent it by explicitly instructing the agent to report gaps, requiring citations, and treating honest uncertainty as a valid answer

---

## What Is Next

You now know all four failure modes. The next topic moves from what can go wrong to how to decide whether to use an agent at all — the decision framework that tells you when an agent is the right tool and when something simpler will do the job better.
