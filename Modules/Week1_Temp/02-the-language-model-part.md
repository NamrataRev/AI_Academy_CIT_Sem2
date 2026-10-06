# The Language Model — The Brain

---

Think about a brilliant doctor who never leaves their office.

Patients send in their reports. The doctor reads everything carefully — symptoms, test results, history. Then writes back: "Run this test. Check this level. Prescribe this." Precise instructions. But the doctor never walks to the lab. Never picks up the prescription pad. Never examines the patient directly.

Everything happens through instructions.

That is exactly how the language model works inside an agent. It is the brain — the part that reads, thinks, and decides. But it never acts on its own.

---

## What the Brain Does

At every step of the loop, the brain gets a full picture:

- What is the goal?
- What has been found so far?
- What tools are available?

It reads all of this and produces one thing — **a decision**. Either: *call this tool with these inputs.* Or: *I have enough — here is the final answer.*

That is the entire job of the brain. Read. Think. Decide.

It does not search the internet. It does not open files. It does not run any code. Something else does all of that. The brain only produces the instruction.

---

## Why This Distinction Matters

When you ask a regular AI a question, the model produces the answer directly from what it already knows — its training data.

When an agent uses a tool, something different happens. The brain produces an instruction: *"Search for current laptop prices under $700."* The agent framework reads that instruction, runs the actual search, gets live results from the internet, and hands them back to the brain.

The brain never touched the internet. It only said what should be searched.

This is why the brain analogy fits perfectly. Your brain does not lift your arm — it sends a signal and your muscles do the lifting. The language model does not call APIs — it sends an instruction and the framework does the calling.

---

## What the Brain Reads Every Loop

Imagine the brain receives a briefing document at the start of every loop. That document grows as the agent works:

```
GOAL: Find the best laptop under $700 for coding

WHAT HAS HAPPENED SO FAR:
- Loop 1: Found five options in budget range
- Loop 2: Compared RAM — Acer Aspire 5 has 16GB, others have 8GB

TOOLS AVAILABLE:
- search_web
- calculate

WHAT SHOULD I DO NEXT?
```

The brain reads this every single time — not just the last result, but everything. This is what allows it to make connected decisions and not repeat work it already did.

---

## The Contrast

A language model alone — without tools, without a loop — can only answer from what it was trained on. Ask it the price of a laptop today and it gives you a price from months ago. Ask it about a course that launched last week and it has no idea.

The brain inside an agent is the same language model. What changes is what it can access. Because it can instruct tools, it can reach beyond its training data and work with real, current information.

The brain is not smarter. It is better connected.

---

## Quick Recap

- The language model is the brain — it reads the situation and decides what to do next at every loop
- It never acts directly — it produces instructions that the framework carries out
- Every loop it reads the full picture: goal, everything found so far, tools available
- The brain is the same model you have used before — what changes is that it can now instruct tools

---

## What Is Next

The brain gives instructions. But what receives those instructions and actually does the work? The next file covers tools — the hands of the agent — and how a tool call actually works from instruction to result.
