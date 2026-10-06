# Agent Failure Modes — Overview

---

It is the night before an assignment deadline.

One student cannot find a source to back up their argument. Instead of leaving it unsupported or asking for help — they cite a paper that does not exist. The reference looks completely real. The professor checks. It is not there.

Another student starts researching. Finds one article. It links to another. That links to another. They keep reading, keep finding more, never deciding they have enough to start writing. The deadline passes. The assignment is not submitted.

A third student gets going and writes well — but then keeps going. The question asked for 500 words on one topic. They submit 2,000 words covering five related topics, three historical examples, and a full conclusion about the future of the field. The marker wanted 500 words on one thing.

A fourth student does not fully understand the question. Instead of clarifying, they write a confident, well-structured answer — to a slightly different question. It looks complete. It is thorough. It is answering the wrong thing entirely.

Four students. Four different failures. All from the same root cause — nobody prepared them for the uncertain situation they hit.

Agents fail the exact same way.

---

## The One Root Cause

Before naming the failures, understand this:

**Every agent failure comes from the same place — the agent hit a situation it was not prepared for.**

The agent needed a tool it did not have. It did not know when to stop. It did not know where its boundaries were. It did not know what to do when a tool returned nothing useful.

In each case, the agent did what language models always do when uncertain — it produced the most plausible-sounding response. Sometimes that means inventing something. Sometimes looping forever. Sometimes doing too much. Sometimes confidently returning a wrong answer with no warning.

The four failure modes are four versions of this same problem.

---

## The Four Failures

**Hallucinated Tool Calls** — The agent needs a capability it does not have. Instead of saying so, it invents a tool that does not exist and fabricates the result. Like the student who cited a paper that was never written.

**Infinite Loops** — The agent does not know when the task is done. It keeps searching, gathering, going — never deciding it has enough to answer. Like the student who kept researching until the deadline passed.

**Scope Creep** — The agent was not told where to stop. It finishes the task and keeps going — doing related things nobody asked for. Like the student who submitted 2,000 words when 500 were asked for.

**Silent Failures** — A tool fails or returns nothing useful. Instead of reporting this, the agent fills the gap with something plausible from its training data and presents it as real. Like the student who answered the wrong question but made it look complete and confident.

---

## Why This Order Matters

These four failures are introduced in order of how visible they are.

A hallucinated tool call is somewhat detectable — the tool name looks odd, the result seems too convenient.

An infinite loop is very visible — the agent keeps running and costs time and money.

Scope creep is noticeable — the output is far larger than expected.

Silent failure is almost invisible — the output looks exactly like a correct answer. Nothing signals that something went wrong.

The most dangerous failure is the last one. It is the one you are least likely to catch.

---

## Quick Recap

- All four agent failures share one root cause — the agent hit a situation it had no instruction for
- The four failures are: hallucinated tool calls, infinite loops, scope creep, and silent failures
- They range from somewhat visible to almost completely invisible
- Silent failure is the most dangerous because the output looks correct even when it is not

---

## What Is Next

The first failure — hallucinated tool calls — is where the agent invents tools and results that do not exist. The next file explains what causes it, what it looks like, and exactly how to prevent it.
