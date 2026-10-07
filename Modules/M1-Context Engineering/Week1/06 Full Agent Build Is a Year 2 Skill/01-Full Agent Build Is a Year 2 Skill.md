# Full Agent Build Is a Year 2 Skill

---

A pilot spends months in a simulator before flying a real aircraft.

Not because the simulator is the goal. The simulator is not the destination — the real aircraft is. But flying a real aircraft before you understand what every instrument does, how failures cascade, and how to make decisions under pressure is not learning. It is guessing with consequences.

Building a full agent from scratch works the same way. The goal is absolutely to build one. But building one before you understand how the planning loop works, what failure modes look like, and how to design for them is not skill-building. It is copy-pasting code you do not understand and hoping it works.

This course sequences things deliberately. Year 1 builds the understanding. Year 2 builds the full system.

---

## What This Module Actually Covers

This module — and this week — is about **design decisions and architectural choices**.

Not code. Not frameworks. Not which library to install.

The decisions that happen before any of that. The thinking that separates an engineer who builds something reliable from one who builds something that works in demos and breaks the first time a real user touches it.

---

## What Design Decisions Look Like — A Real Example

Here is a task a BTech final-year student might actually build for their capstone:

> *"An assistant that helps students find relevant research papers for their project topic, filters out papers that are too advanced or too old, and summarises the top three in plain language."*

Before writing a single line of code, a good engineer makes these decisions:

---

**Decision 1 — Which situation is this?**

The steps depend on what is found. You cannot know in advance which papers will appear, which will be too advanced, or which three will be most relevant. Each step depends on the previous one's output.

**→ This is Situation 3. An agent is the right tool.**

---

**Decision 2 — What tools does the agent need?**

It needs to search for papers — so `search_web` or a dedicated academic search tool.
It needs to read paper abstracts — so `read_url` or a document fetch tool.
It does not need to write files, send emails, or run code.

**→ Two tools maximum. No more.**

Giving it more tools than it needs creates more decisions for the brain to make and more ways to go wrong.

---

**Decision 3 — What is the loop limit?**

Finding papers: 1-2 loops. Filtering: 1 loop. Summarising top three: 1 loop. That is 4-5 loops in a clean run.

**→ Set the maximum at 10.** Generous enough for variation. Tight enough to prevent runaway loops.

---

**Decision 4 — What failure modes are most likely?**

Silent failure is the biggest risk here. If the search returns nothing useful, the agent might summarise papers that are not relevant at all — confidently. The student acts on a fabricated summary.

**→ Add an explicit instruction:** "If no relevant papers are found, say so clearly. Do not summarise papers that do not match the topic."

---

**Decision 5 — What level of autonomy does the judgment framework suggest?**

| Question | Answer |
|---|---|
| How reversible? | Fully reversible — it is just a summary |
| How verifiable? | The student can check the papers cited |
| Cost of wrong answer? | Low — worst case, unhelpful summary |
| How well understood? | Standard research task — well understood |

**→ The agent can run fully autonomously.** No human checkpoint needed for this task.

---

## What Just Happened

Five decisions. Made before writing a single line of code.

Which tool type to use. Which tools specifically. The loop ceiling. The failure mode to guard against. The autonomy level.

This is architectural thinking. This is what separates a system that works reliably from one that works once and breaks unpredictably.

Every engineer who builds production agents makes these decisions — either deliberately before building, or painfully after something goes wrong in production.

---

## What You Are Building Towards

By the end of this year, you will have the skills to make every one of these decisions confidently:

- Context engineering — so the agent's brain gets well-structured inputs and makes better decisions
- Spec-driven development — so you know what "correct" means before you build
- Failure handling — so your agent fails safely and visibly, never silently
- Evaluation — so you can measure whether your agent is actually reliable

These are not prerequisites to the real work. These are the real work.

---

## Quick Recap

- Full agent builds are a Year 2 skill — this year builds the design thinking that makes them reliable
- Design decisions happen before code — which situation, which tools, loop limit, failure modes, autonomy level
- A research assistant agent for students is a Situation 3 task — steps depend on findings, two tools, loop limit of 10, guard against silent failure, full autonomy acceptable
- Every reliable agent starts with these decisions made deliberately, not discovered painfully after deployment

---

## What Is Next

Week 1 is complete. The next topic begins Week 2 — context engineering. You will learn why even a well-designed agent produces poor results when its inputs are not constructed carefully, and how the five context roles give you systematic control over what the model does.
