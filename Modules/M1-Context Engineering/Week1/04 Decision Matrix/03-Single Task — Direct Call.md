# Single Task — Direct Call

---

You want to know what photosynthesis is.

You do not set up a research project. You do not hire someone to search multiple textbooks, compile findings, and verify the information across sources. You just ask. Someone tells you. Done.

Some questions are like this. The answer already exists. One question gets you there. The model already knows it.

This is when a direct call is exactly right — and when reaching for an agent is a mistake.

---

## What Makes a Task Single-Step

A task is single-step when all of this is true:

- One prompt is enough to describe the task completely
- The model already has the knowledge to answer it
- The answer does not require going anywhere, checking anything, or waiting for a result

The model reads the prompt. It generates the response from what it already knows. Done in one round.

---

## Examples That Belong Here

**Writing tasks** — *"Write a professional email declining a meeting."* The model knows what professional emails look like. No research needed.

**Explanations** — *"Explain what an API is in simple terms."* The model knows this. One response covers it.

**Code generation from a clear spec** — *"Write a Python function that takes a list and returns only the even numbers."* The spec is complete. The model can produce it directly.

**Summarisation of pasted content** — *"Summarise this paragraph in two sentences."* The content is right there in the prompt. No tools needed.

**Translation** — *"Translate this sentence into Spanish."* The model already has this capability. One call, done.

---

## Why Not Use an Agent Here

An agent adds a planning loop, tool calls, and memory management. Each of these has a cost — in time, in money, and in complexity.

For a single-step task, none of these additions help. The planning loop has nothing to plan. The tools have nothing to find. The memory has nothing to accumulate. You pay the costs of an agent and get none of the benefits.

Worse — adding unnecessary complexity introduces new failure points. An agent can hallucinate tool calls, loop unexpectedly, or creep out of scope. A direct call has none of these risks.

Use the simplest tool that gets the job done correctly. For single-step tasks, that is a direct call.

---

## The One Signal to Watch For

A task looks single-step but might not be if the correct answer requires information the model does not have.

*"What is the weather in my city right now?"* — looks simple, but the model does not have real-time data. This needs a tool. That makes it at least a two-step task.

*"Summarise the article at this URL."* — looks simple, but the model cannot read URLs. The article needs to be fetched first. Again, not single-step.

The question to ask: **does the model already have everything it needs to answer correctly?** If yes, direct call. If the model needs to go and get something, it is not single-step anymore.

---

## Quick Recap

- A single-step task needs one prompt, the model already has the knowledge, and no tools or loops are required
- Direct calls are faster, cheaper, and have fewer failure points than agents
- Do not use an agent for single-step tasks — you pay the costs with none of the benefits
- Watch for tasks that look simple but require real-time or external information — those are not single-step

---

## What Is Next

The next topic covers the second situation from the decision matrix — multiple steps with a fixed sequence. When you know the steps in advance, a chained call or fixed pipeline is the right choice — and it is simpler and more reliable than a full agent.
