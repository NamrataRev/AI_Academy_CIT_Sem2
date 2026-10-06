# Scope Creep

---

You ask a friend to proofread your essay.

They fix the spelling errors. Then they rewrite a paragraph they did not like. Then they add a new section they thought was missing. Then they change your conclusion. Then they send it back and say they also restructured the introduction while they were at it.

You asked for proofreading. You got a co-author.

Agents do exactly this. When nobody tells them where to stop, they do not stop at the task — they keep going, adding, expanding, doing related things that were never asked for.

This is scope creep.

---

## What It Is

Scope creep happens when the agent completes the task it was given — and then keeps going.

It finishes what was asked. Then its reasoning produces: *"While I am here, I should also..."* And it does that too. Then another *"while I am here."* And another.

The agent is not malfunctioning. It is trying to be helpful. The problem is nobody defined where helpful ends.

---

## What It Looks Like

A student asks an agent: *"Summarise this research paper in three bullet points."*

The agent summarises the paper in three bullet points. Then it thinks: *"The student might also want to know about related papers."* It searches for those. Then: *"I should explain the methodology in more detail."* It does. Then: *"A comparison with other approaches would be useful."* It adds that too.

The student asked for three bullet points. They receive a five-page document.

Now imagine the agent had access to actions — sending emails, creating calendar reminders, posting to a platform. Scope creep with real actions means the agent starts doing things that were never authorised. It is not just annoying at that point. It is a problem.

---

## Why It Happens

The task description had no boundary.

*"Summarise this paper"* does not say what to leave out. The agent's reasoning, trying to be thorough, keeps finding adjacent things that seem relevant. Without a line that says *"stop here"* — it crosses every line it finds.

---

## How to Prevent It

**Say what the task is and what it is not** — *"Summarise this paper in exactly three bullet points. Do not include anything beyond those three points."* The boundary is now explicit.

**Set a tool call limit** — if the task should take one search and one generation, tell the agent that. If it has made more calls than expected, something has gone out of scope.

**Name what to exclude** — *"Do not search for related papers. Do not explain the methodology. Do not make comparisons."* This feels overly specific but it works.

---

## Quick Recap

- Scope creep happens when the agent finishes the task and keeps going — doing things that were never asked for
- It happens because the task had no defined boundary — the agent keeps finding adjacent things that seem helpful
- With action tools, scope creep is not just annoying — it means unauthorised actions are taken
- Prevent it by naming the boundary explicitly, setting a tool call limit, and stating what to exclude

---

## What Is Next

The next topic covers the fourth and most dangerous failure mode — silent failures. This is where the agent cannot complete the task but presents a confident answer anyway, and there is no signal to tell you something went wrong.
