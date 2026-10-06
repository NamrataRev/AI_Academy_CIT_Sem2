# ReAct Limitations

---

ReAct makes agents significantly more reliable. But it is not perfect.

Think about a student who always plans before they act. They read the question. They think through their approach. They write their answer step by step. This student will outperform one who just starts writing without thinking.

But even this careful student can still get a question wrong. Planning before acting reduces mistakes — it does not eliminate them. The plan itself can be flawed.

ReAct has the same problem. The reasoning step helps. But the reasoning can still go wrong.

---

## Limitation 1 — The Reasoning Can Be Wrong

The reason step produces a thought like: *"I have enough information to answer now."*

But what if that thought is wrong? What if the agent thinks it has enough when it does not?

This happens more than you might expect. The agent reads its notepad, sees several results, and concludes it is ready — when in reality a critical piece is still missing. The reasoning step did not catch the gap because the agent did not know the gap existed.

A student who does not know what they do not know will also not realise their plan is incomplete. Same problem.

---

## Limitation 2 — Reasoning Costs Tokens

Every thought the agent produces uses tokens. On a short task — three or four loops — this is negligible. On a complex task with twenty loops, the reasoning steps alone can consume a significant portion of the context window and add meaningful cost.

This is why ReAct is not always the right pattern for every agent. For simple, single-step tasks, the reasoning overhead adds cost without adding value. ReAct is most useful when the task is genuinely multi-step and the path is uncertain.

---

## Limitation 3 — The Agent Can Reason Itself Into a Loop

Sometimes the reasoning step becomes part of the problem.

The agent thinks: *"I need more information to be confident."* It searches. It gets results. It thinks: *"These results are helpful but I am still not fully confident."* It searches again. Same conclusion. Same search. Same doubt.

The reasoning step is running correctly — it is honestly reporting uncertainty. But the action it produces each time is the same search, which returns similar results, which produces the same uncertainty. The agent reasons itself into a loop it cannot escape through reasoning alone.

This is why maximum iteration limits exist. ReAct reduces loops — it does not eliminate the need for a ceiling.

---

## Limitation 4 — Reasoning Does Not Guarantee Correct Tool Choice

The agent reasons: *"I need current stock prices."* It decides to call `search_web`. But `search_web` returns news articles about a company, not live stock prices. A dedicated financial data tool would have been better — but the agent did not have one, and its reasoning did not surface this gap.

The reasoning step produces the best decision the agent can make given its tools and knowledge. If the tools are limited or the agent's understanding of them is incomplete, the reasoning will still lead to a suboptimal action — even though the reasoning process itself was sound.

---

## What This Means in Practice

ReAct is a significant improvement over acting without reasoning. Use it for multi-step tasks where the path is uncertain.

But do not treat it as a guarantee. An agent using ReAct still needs:

- A maximum iteration limit — reasoning does not prevent loops, it only reduces them
- Well-defined tool descriptions — reasoning about tools is only as good as the descriptions provided
- Clear task instructions — reasoning cannot compensate for a vague or contradictory goal

---

## Quick Recap

- ReAct reduces mistakes but does not eliminate them — the reasoning itself can be flawed or incomplete
- Reasoning costs tokens — on long tasks this adds up, and ReAct is overkill for simple single-step tasks
- The agent can reason itself into a loop — honest uncertainty repeated across many loops leads to the same problem as any other loop
- Correct reasoning does not guarantee the right tool choice — if the tools are limited the best reasoning still produces a suboptimal action
- Maximum iteration limits are still required even with ReAct

---

## What Is Next

You now know how agents work and how they can go wrong inside the loop. The next topics cover the four failure modes — what happens when things go wrong from the outside. The first is when the agent invents capabilities it was never given.
