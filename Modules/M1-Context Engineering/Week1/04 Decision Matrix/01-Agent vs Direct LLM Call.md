# Agent vs Direct LLM Call

---

You need to know the capital of France.

You would not hire a research assistant, ask them to search multiple sources, compile findings, verify the information, and come back with a report. You would just look it up yourself. Or ask someone. One question, one answer, done.

But if you needed to research the visa requirements for five different countries, compare them, identify which one suits your situation, and summarise the key steps — that is a different kind of task. That one might actually benefit from a research assistant.

The same logic applies to agents. Using an agent for every task is like hiring a research team every time you need to check the time. The tool is right for some tasks and completely wrong for others.

---

## What a Direct LLM Call Is

A direct LLM call is the simplest interaction with a language model. You send a prompt. The model generates a response. Done. One step, no tools, no loop.

This is what you do when you ask a model to explain a concept, write a paragraph, summarise something you paste in, or answer a question from its training knowledge.

It is fast. It is cheap. It is predictable. And for a large number of tasks, it is exactly the right choice.

---

## What an Agent Adds

An agent adds three things on top of a direct call: tools, memory across steps, and a planning loop that decides what to do next.

These additions are powerful — but they come with costs. Every loop is an additional model call. Every tool call takes time and may have its own cost. The more loops, the more expensive and the slower the response.

An agent is the right choice when those costs are justified by what the task actually needs. And a direct call is the right choice when those additions are not needed.

---

## The Core Question

Before reaching for an agent, ask one question:

**Can this task be completed correctly with a single prompt and the model's existing knowledge?**

If yes — use a direct call.
If no — consider an agent.

That single question handles most decisions. The next topic introduces the full decision matrix for the cases where the answer is not immediately obvious.

---

## Quick Recap

- A direct LLM call is one prompt, one response — fast, cheap, and predictable
- An agent adds tools, memory, and a planning loop — powerful but slower and more expensive
- The core question: can this task be completed correctly with a single prompt and existing knowledge?
- If yes, use a direct call. If no, consider an agent.

---

## What Is Next

The next topic introduces the decision matrix — a structured framework that maps four types of tasks to the right approach, so you can make this choice quickly and consistently.
