# Infinite Loops

---

You know that feeling when you are studying for an exam and you just cannot stop.

You finish one topic. But you are not confident enough. So you read one more article. Still not confident. Watch a video. Still not sure. Read another article. Maybe one more. The exam starts in an hour. You have been "preparing" for six hours and have not written a single practice answer.

You never decided you had enough. So you never stopped.

Agents do exactly this. When they do not know what "done" looks like — they do not stop. They keep looping. They keep searching. They keep gathering. Forever, if nothing stops them.

This is an infinite loop.

---

## What It Is

An infinite loop happens when the agent has no clear definition of when the task is complete.

Every loop the brain reads the notepad, reasons about what to do next, and decides — do I have enough or do I need more? If "enough" was never defined, the brain can never confidently answer yes. So it always answers no. And the loop runs again.

---

## What It Looks Like

A student asks an agent: *"Find me some good resources to learn about neural networks."*

The agent searches. Finds five articles. But "good" was never defined. Are five enough? The brain is not sure. It searches again with different keywords. Finds more. Still not confident it found the best ones. Searches again. And again.

After thirty loops the agent either crashes, times out, or hits a limit set by the framework. The student gets nothing useful — or gets an error with no explanation.

Meanwhile every loop cost time and money.

---

## Why It Happens

The task description had no finish line.

"Find some good resources" — how many is some? What makes one resource better than another? The brain cannot answer these questions from the task alone. So it cannot decide when enough is enough.

It is not a bug. The brain is doing exactly what it should — asking "do I have enough?" before stopping. The problem is the question has no answer because nobody defined what enough means.

---

## How to Prevent It

**Define done explicitly in the task** — not "find resources" but "find 5 resources on neural networks, summarise each in one sentence, then stop." The brain now has a specific finish line it can check against.

**Set a maximum loop limit — always** — this is non-negotiable. Every agent, every task, every time. Ten loops is reasonable for most tasks. Twenty for complex research. Whatever the limit, set it before the agent starts. This is the safety net that stops the loop even when everything else fails.

**Add a progress check** — if the last two reasoning steps are nearly identical, the agent is stuck. Force a stop and return whatever has been found so far.

---

## Quick Recap

- An infinite loop happens when the agent has no clear definition of when the task is done
- The brain keeps asking "do I have enough?" and always answers no because "enough" was never defined
- Every extra loop costs time and money — an uncapped loop is a real problem in production
- Prevent it with an explicit finish line in the task description and a maximum loop limit on every agent

---

## What Is Next

The third failure mode is scope creep — when the agent finishes the task and then keeps going, doing things that were never asked for. The next topic explains why this happens and how boundaries prevent it.
