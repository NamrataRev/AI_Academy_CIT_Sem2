# The Judgment Framework

---

A junior doctor can diagnose many conditions correctly. But there are situations where they stop and consult a senior colleague — not because they are incompetent, but because they have learned to recognise when a situation is beyond what they should handle alone.

That judgment — knowing when to act independently and when to escalate — is one of the most important skills a professional develops. It is not taught through rules alone. It develops through understanding the consequences of getting it wrong.

Building agents requires the same judgment. Not just knowing how to build one — but knowing when to let it act on its own and when to hold it back.

---

## What the Judgment Framework Is

The judgment framework is a set of four questions you ask before deciding how much autonomy to give an agent. The answers determine whether the agent should act fully independently, check in at key points, or hand every decision to a human.

The framework does not replace the decision matrix. The decision matrix tells you which tool to use. The judgment framework tells you how much freedom to give that tool once you have chosen it.

---

## The Four Questions

**Question 1 — How reversible is the action?**

If the agent takes the wrong action, can it be undone easily?

Sending a search query — fully reversible. Deleting a file — irreversible. Sending an email to a client — cannot be unsent. Posting publicly — seen immediately.

The less reversible the action, the more human oversight is needed before the agent takes it.

**Question 2 — How verifiable is the output?**

Can a human quickly check whether the agent's output is correct?

A summary of a document — the human can read the document and verify. A legal interpretation — requires a lawyer to evaluate. A medical recommendation — requires clinical judgment.

The harder the output is to verify, the more caution is needed before acting on it.

**Question 3 — What is the cost of a wrong answer?**

If the agent gets this wrong, what happens?

Low cost: the student gets a slightly unhelpful study resource. They try again. High cost: a financial transaction is processed incorrectly. Funds move. Reversing it is painful, expensive, or impossible.

Higher cost of failure means lower acceptable autonomy for the agent.

**Question 4 — How well understood is this task?**

Has this type of task been tested thoroughly with this agent? Is it a known, routine task with a clear success pattern — or is it novel, ambiguous, or first-of-its-kind?

Well-understood tasks can be given more autonomy. Novel or ambiguous tasks need more oversight until confidence is established.

---

## How to Apply It

Run through the four questions for any task you are considering giving to an agent.

If the action is reversible, the output is verifiable, the cost of failure is low, and the task is well understood — the agent can act with significant autonomy.

If any of those conditions is not met — pull back. Add a checkpoint. Require human approval before the critical action. Or do not automate it at all yet.

---

## A Practical Example

Task: an agent that automatically replies to student questions about a course schedule.

| Question | Answer |
|---|---|
| How reversible? | Emails sent cannot be unsent — low reversibility |
| How verifiable? | Schedule information can be checked against the source — verifiable |
| Cost of wrong answer? | Student misses a deadline or shows up at the wrong time — medium cost |
| How well understood? | Routine task with a clear pattern — well understood |

**Judgment:** the agent can draft replies automatically, but a human should review before sending — at least until the error rate is established and trust is built.

---

## Quick Recap

- The judgment framework asks four questions: how reversible, how verifiable, what is the cost of failure, and how well understood is the task
- The answers determine how much autonomy the agent should have — from full independence to human approval at every step
- The framework works alongside the decision matrix — the matrix chooses the tool, the framework decides how much freedom to give it
- When in doubt, give the agent less autonomy and increase it as trust is established

---

## What Is Next

The next topic covers the final piece of Week 1 — why a full agent build is a Year 2 skill, what that means for what you are learning now, and what you are already equipped to do.
