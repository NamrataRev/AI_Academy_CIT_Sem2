# Hallucinated Tool Calls

---

You ask a friend what the capital of Australia is. They do not know. But instead of saying "I am not sure" — they confidently say "Sydney."

It sounds right. It is wrong. And the most important part — they showed no sign of uncertainty. No hesitation. No "I think" or "maybe." Just a confident, wrong answer delivered as fact.

Agents do the exact same thing. When they need a tool they do not have, they do not stop and say "I cannot do this." They invent the tool. And then they invent the result.

This is a hallucinated tool call.

---

## What It Is

A hallucinated tool call happens when the agent needs a capability that was not given to it.

Instead of stopping, it generates what a tool call and a result would look like — because generating plausible text is exactly what language models are trained to do. The output looks completely real. The tool name looks legitimate. The result looks like it came from somewhere.

None of it did.

---

## What It Looks Like

An agent is asked: *"What is the current price of gold per gram?"*

The agent has only a `search_web` tool. But it decides it needs a more precise financial data tool. So it produces this:

```
Tool: get_commodity_price
Input: {"commodity": "gold", "unit": "gram", "currency": "USD"}
Result: "$62.14 per gram as of market close today"
```

The tool `get_commodity_price` does not exist. The agent invented it. The price $62.14 came from nowhere. But the output looks like a real financial data query with a precise, current result.

The student reading this has no reason to doubt it. They use the number. It is wrong.

---

## Why It Happens

Language models are trained to produce the most plausible next response. When the agent realises it needs something it does not have, it does not stop — stopping does not feel like the natural next thing to generate. Producing a tool call and a result does.

It is not lying deliberately. It has no concept of lying. It is doing what it was trained to do — produce the most coherent continuation of the text. The fact that the tool does not exist does not stop it from generating what one would look like.

---

## How to Prevent It

**Give the agent a clear list of exactly what tools it has** — and nothing else. Before every task, the agent knows: these are your tools, these are what they do, these are the only things you can call.

**Add an explicit instruction** — *"If no tool in your list can help with this step, say so clearly. Do not call tools that are not in your list."*

**Validate every tool call** — before the framework runs anything, check that the tool name exists in the registered list. If it does not, stop immediately and report it. Do not let a fabricated tool call produce a fabricated result.

---

## Quick Recap

- A hallucinated tool call happens when the agent invents a tool it was not given and fabricates the result
- It happens because language models generate plausible text — inventing a tool call is more natural than stopping
- The output looks completely real — there is no obvious signal that something went wrong
- Prevent it by giving the agent an explicit tool list, instructing it to say when no tool fits, and validating every call before it runs

---

## What Is Next

The second failure mode is the infinite loop — when the agent never decides the task is done and keeps running forever. The next topic explains what causes it and how a simple ceiling prevents it.
