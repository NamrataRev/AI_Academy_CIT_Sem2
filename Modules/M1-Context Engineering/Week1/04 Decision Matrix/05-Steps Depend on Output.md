# Steps Depend on Output

---

Imagine a doctor examining a patient.

They do not walk in with a fixed list of tests to run. They ask about symptoms. Based on what they hear, they decide what to check next. The blood test result comes back — and depending on what it shows, they either order a scan or prescribe something or run another test entirely.

Every next step depends on what the previous step revealed. Nobody could have written the full sequence in advance. It only becomes clear as the examination unfolds.

This is exactly the situation where an agent is the right choice.

---

## What Makes a Task Depend on Output

A task depends on output when you cannot know what Step 2 is until Step 1 is done.

The result of the first action determines what comes next. And the result of the second determines what comes after that. The path through the task is not fixed — it emerges as the agent works.

---

## A Clear Example

A student asks: *"Find me the most relevant recent research on using transformers for medical imaging and summarise the three most cited papers."*

**What the agent cannot know in advance:**
- Which papers will appear in the search
- Whether those papers are actually recent
- Whether they are specifically about medical imaging or just tangentially related
- Which three are most cited

**What actually happens:**

Step 1 — Search for recent research on transformers in medical imaging. Results come back: twelve papers from the last two years.

Step 2 — The agent reads the results. Two of the twelve are actually about a different domain. It filters them out. Ten remain. This step only makes sense after seeing Step 1's output.

Step 3 — The agent checks citation counts for the ten remaining papers. The top three are identified. This step only makes sense after Step 2's filtering.

Step 4 — Summarise the three most cited papers. Only possible after Step 3.

None of these steps could have been written into a fixed sequence before the task started. Each one depended on what the previous one found.

---

## The Signal That Tells You This Is Situation 3

Ask: if I ran this task with a different input, would the steps change?

If yes — you are in Situation 3. An agent is the right choice.

For the research example: run it with a different topic and the papers are completely different, the filtering finds different outliers, the citation counts lead to different top three. The steps are structurally similar but their content is entirely determined by what is found.

This is the core of what agents are designed for. The planning loop exists for exactly this situation — reading what was found, deciding what to do next, and repeating until the task is complete.

---

## Why a Fixed Sequence Would Fail Here

A fixed sequence for this task would look like: search → filter → rank → summarise. That sounds right.

But a fixed sequence cannot filter intelligently — it does not know what "off-topic" looks like until it sees the results. It cannot rank by citation count without knowing which papers remain after filtering. Each step requires genuine judgment based on what the previous step returned.

A fixed sequence applies the same operations regardless of what came before. An agent adapts. That adaptability is the entire point.

---

## Quick Recap

- A task depends on output when the next step cannot be known until the current step is done
- This is when an agent is the right choice — the planning loop reads each result and decides what comes next
- The signal: if you ran the task with a different input and the steps would change, it is Situation 3
- A fixed sequence fails here because it applies the same operations regardless of what was found — an agent adapts

---

## What Is Next

The next topic covers the fourth situation — when the task is not just multi-step but high stakes. When a wrong answer causes real harm, even a well-designed agent is not enough on its own. That is when a human must stay in the loop.
