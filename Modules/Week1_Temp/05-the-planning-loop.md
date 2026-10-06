# The Planning Loop

---

Think about how you make a cup of tea.

You do not do everything at once. You boil water. You wait. You put the teabag in. You pour. You check if it is strong enough. If not, you wait more. Each step depends on what happened before. You only move forward when the current step is done.

Nobody told you to check the water before pouring. You just looped through the steps naturally — act, check, decide what is next, act again.

The planning loop is exactly this. It is the cycle that connects the brain, the hands, and the notepad into something that can actually finish a task.

---

## How the Loop Works

Every time the loop runs, three things happen in order.

**The brain reads the full picture** — the goal, everything on the notepad, what tools are available. It asks: do I have enough to answer, or do I need to do something else?

**The brain makes a decision** — two possible outcomes. Either: *I need more — call this tool with these inputs.* Or: *I have enough — produce the final answer and stop.*

**If a tool was called, the result comes back** — the framework runs the tool, the result is written on the notepad, and the loop starts again from the top.

That is it. The loop runs until the brain decides the job is done.

---

## The Full Loop — Laptop Example

Goal: *"Best laptop under $700 for coding right now."*

```
LOOP 1
Brain reads: goal only — notepad is empty
Brain decides: I need current options. Prices change — 
               I cannot rely on training data. Search.
Tool: search_web → "best coding laptop under $700 2025"
Result: Acer Aspire 5 ($649), Lenovo IdeaPad ($629), 
        HP Pavilion ($679)
Written to notepad. Loop again.

LOOP 2
Brain reads: goal + three options on notepad
Brain decides: I need to compare these on what matters 
               for coding — RAM and processor.
Tool: search_web → "Acer Aspire 5 vs Lenovo IdeaPad 
      coding RAM performance"
Result: Acer has 16GB RAM. Others have 8GB at similar price.
Written to notepad. Loop again.

LOOP 3
Brain reads: goal + options + Acer leading on specs
Brain decides: Strong candidate found. Verify price 
               is current and it is in stock.
Tool: search_web → "Acer Aspire 5 16GB price stock 2025"
Result: $649, in stock at major retailers.
Written to notepad. Loop again.

LOOP 4
Brain reads: goal + options + comparison + verified price
Brain decides: I have everything I need.

Final answer:
"The Acer Aspire 5 (Ryzen 5, 16GB RAM) at $649 is your best 
option right now. 16GB RAM means you can run a code editor, 
browser, and local server at the same time without slowdown. 
Currently in stock at major retailers."

Loop ends.
```

Four loops. Each one built on the previous. The brain never repeated a search because the notepad had the results. Each decision was smarter than the last.

---

## What Makes the Loop Powerful

A single AI call happens once. You ask, it answers from whatever it already knows. If the answer needs current information or multiple steps — a single call cannot do it reliably.

The loop changes this. It gives the agent multiple passes — gather, compare, verify, then answer. The final answer in Loop 4 is better than anything Loop 1 could have produced because it is built on three rounds of real research.

---

## The Loop Needs a Ceiling

Every agent must have a maximum number of loops it is allowed to run.

Without a ceiling, a confused agent loops forever — searching, finding something, searching again, never deciding it has enough. Every loop costs time and money. A loop that runs twenty times when three were enough is wasteful. A loop with no limit at all is dangerous.

Setting the ceiling — five loops, ten, twenty depending on the task — is one of the first decisions you make when designing an agent.

---

## Quick Recap

- The planning loop is the cycle: brain reads → decides → tool called → result to notepad → brain reads again
- It runs until the brain decides it has enough to give a final answer
- Each loop is smarter than the last because the notepad grows with every result
- Every agent needs a maximum loop limit — without one a confused agent runs forever

---

## What Is Next

The loop is the engine. But inside every loop, the brain follows a specific pattern for how it thinks before it acts. That pattern has a name — ReAct — and understanding it is what lets you build agents that make good decisions reliably. That is the next file.
