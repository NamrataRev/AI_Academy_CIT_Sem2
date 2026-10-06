# Multi-Step Fixed Sequence

---

Every morning, millions of people make coffee the same way.

Boil water. Put the coffee in. Pour the water. Wait. Done. The steps never change. Nobody decides mid-process to check if a different method might work better today. The sequence is fixed. You just follow it.

Many AI tasks work the same way. Multiple steps — but the steps are always the same, always in the same order. You know what they are before you start.

For these tasks, you do not need an agent. You need a fixed sequence of calls.

---

## What a Fixed Sequence Is

A fixed sequence is two or more LLM calls chained together, where the output of one becomes the input to the next. The steps are defined in advance. They do not change based on what is found.

No planning loop. No tools deciding what to do next. Just: Step 1 happens, its output goes to Step 2, Step 2's output goes to Step 3, done.

---

## A Clear Example

A student wants to take a long research paper and turn it into revision flashcards.

**Step 1** — Extract the key concepts from the paper.
Input: the full paper. Output: a list of 10 key concepts.

**Step 2** — For each concept, write a one-sentence explanation.
Input: the list of concepts. Output: 10 concept-explanation pairs.

**Step 3** — Format these as flashcards.
Input: the pairs. Output: 10 formatted flashcards ready to study.

Three steps. Fixed order. The output of each step feeds directly into the next. You knew all three steps before you started. Nothing discovered along the way changed what Step 2 or Step 3 needed to do.

This is a fixed sequence — and it is the right tool for this task.

---

## Why Not Use an Agent Here

An agent would work — but it is the wrong choice.

The agent would plan the steps, decide what to do at each one, and loop through. But there is nothing to plan. You already know the steps. The agent's decision-making adds cost and complexity without adding any value.

More importantly, a fixed sequence is easier to debug. If Step 2 produces poor explanations, you know exactly where to look. With an agent, the path can vary — making it harder to isolate problems.

Predictability is a feature. When the steps are fixed, the system is easier to test, easier to maintain, and easier to trust.

---

## How to Recognise This Situation

Ask yourself: if I ran this task ten times with ten different inputs, would the steps be the same every time?

If yes — fixed sequence.
If the steps might change depending on what is found — that is Situation 3, which needs an agent.

---

## Quick Recap

- A fixed sequence chains multiple LLM calls where the steps are always the same and always in the same order
- The output of each step becomes the input to the next
- No agent needed — you already know the steps, so there is nothing for a planning loop to decide
- Fixed sequences are more predictable and easier to debug than agents
- If the steps would be the same across ten different inputs, it is a fixed sequence

---

## What Is Next

The next topic covers the situation where you cannot fix the steps in advance — because the next step depends on what the previous one found. That is when an agent becomes the right choice.
