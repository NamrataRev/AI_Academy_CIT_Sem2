# When Not to Use an Agent

---

A Swiss Army knife is useful. But if you are cooking dinner, you use a proper kitchen knife. The Swiss Army knife can do the job — technically. But it is slower, less precise, and harder to control. The right tool is the one designed for the task.

Agents are powerful. But they are not the right tool for every task. Knowing when not to use one is just as important as knowing when to use one.

---

## The Most Common Mistake

The most common mistake when people first learn about agents is reaching for one by default.

The task seems interesting. Agents seem capable. So they build an agent.

Then they discover: the agent is slower than expected, costs more than a direct call, fails in unexpected ways, and is harder to debug when something goes wrong. All for a task that a single prompt would have handled correctly in under a second.

The agent was not wrong. It was just the wrong tool.

---

## Do Not Use an Agent When the Answer Already Exists

If the model already has the knowledge to answer the question correctly — there is no reason for a loop.

*"What is the time complexity of binary search?"*
*"Explain object-oriented programming in simple terms."*
*"Write a function that checks if a number is prime."*

These answers exist in the model's training. One prompt retrieves them. Adding a planning loop, tools, and memory adds nothing except cost and complexity.

---

## Do Not Use an Agent When the Steps Are Fixed

If you know the steps before you start — and those steps will not change based on what is found — a fixed sequence of calls is better.

Agents are designed for uncertainty. When there is no uncertainty about what comes next, the agent's decision-making machinery is wasted overhead.

---

## Do Not Use an Agent When Speed Matters More Than Depth

An agent loop takes time. Each iteration is a model call. Tool calls add latency. For tasks where a near-instant response is required, an agent is often the wrong architecture.

A user asking a quick question in a chat interface does not want to wait ten seconds for an agent to run three loops. A direct call answers in under a second.

---

## Do Not Use an Agent When the Task Is Not Well Defined

This one surprises people. Agents seem like the right choice for vague, open-ended tasks — because they can explore and adapt.

But a vague task given to an agent produces scope creep, infinite loops, and unpredictable results. The agent needs clear success criteria to know when it is done. Without those, all the autonomy in the world does not help.

If the task is not well defined yet — define it first. Then decide whether an agent is needed.

---

## The Simple Test

Before building an agent, ask:

- Can a single prompt handle this correctly? → Direct call
- Are the steps fixed and known in advance? → Fixed pipeline
- Is speed more important than depth? → Direct call
- Is the task not yet well defined? → Define it first

If none of these apply — then an agent is worth considering.

---

## Quick Recap

- Agents are not the default — use them only when the task genuinely needs a planning loop
- Do not use an agent when the answer already exists in the model's knowledge
- Do not use an agent when the steps are fixed — a pipeline is simpler and more predictable
- Do not use an agent when speed matters more than depth
- Do not use an agent when the task is not yet well defined — define it first, then decide

---

## What Is Next

The final topic of Week 1 explains why building a full agent from scratch is a Year 2 skill — and what that means for what you are already equipped to do right now.
