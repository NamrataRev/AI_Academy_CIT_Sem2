# Agent Failure Modes — What Goes Wrong and Why

---

## Learning Objectives

By the end of this file you will be able to:

- Name the four main ways an agent fails and explain what causes each one
- Recognise which failure mode is happening when you see an agent behave unexpectedly
- Apply practical fixes for each failure mode before deploying an agent

---

## Before We Start 

Here is a situation.

You build an agent to help students prepare for technical interviews. It searches for common questions on a given topic, finds explanations, and summarises them. You test it. Works great. You share it with your study group.

Two days later a friend tells you he studied recursion using the agent's summary — which confidently explained tail recursion using completely wrong examples. He used that explanation in a mock interview. It did not go well.

You check the agent logs. The search tool had returned no useful results for that query. Instead of saying "I could not find good material on this" — the agent generated an explanation from its own knowledge, presented it as if it came from the search, and your friend trusted it.

The agent never looked broken. It gave a clean, confident answer. There was no error message, no warning. Just quietly wrong information treated as fact.

This is the real danger with agents. A wrong answer from a regular AI model is usually easy to spot and retry. A failing agent can quietly cause problems without anyone noticing. Understanding these four failure modes before you build is what keeps your agents safe to use.

---

## Failure 1 — The Agent Invents a Tool (Hallucinated Tool Call)

### Picture This

You build an agent to help students find the best Python library for a project. You give it a `search_web` tool.

A student asks: "What is the most actively maintained library for sending emails in Python?"

The agent thinks: "I should check the latest GitHub commit dates for the top email libraries." Good idea — but you never gave it a GitHub tool. So instead of saying "I don't have a tool to check GitHub activity" — it invents one:

```
Action: check_github_activity
Action Input: {"library": "smtplib", "library2": "yagmail", "library3": "sendgrid"}
Observation: "smtplib: last commit 3 days ago. yagmail: last commit 2 weeks ago. sendgrid: last commit yesterday."
```

That tool does not exist. The agent made it up. The commit data is also made up. The student picks a library based on information that came from nowhere.

### Why Does This Happen?

Language models are built to produce the most plausible next response. When the agent realises it needs something it does not have, it does not stop — it generates what a tool call and a result would look like, because that is what should come next in the pattern. It is not lying deliberately. It has no guardrail telling it to stop.

### How to Prevent It

- Give the agent an explicit list of available tools — only these, nothing else
- Add to the system prompt: "If no available tool can help with a step, say so clearly. Do not use tools that are not in your list"
- Validate every tool call — if the agent called something that is not registered, flag it before the result is used

---

## Failure 2 — The Agent Never Stops (Infinite Loop)

### Picture This

A student asks an agent: "Find me beginner-friendly resources to learn dynamic programming."

The agent searches. Finds some articles and videos. But it is not sure if they are beginner-friendly enough. So it searches again with slightly different terms. Finds more. Still not confident about the quality. Searches again. And again.

Nobody told the agent how many resources were "enough." Nobody told it what "beginner-friendly" means in a measurable way. So it keeps going — spending money on API calls, filling up its context window — until it either crashes with a confusing error or the student closes the tab out of frustration.

Nothing useful came out. Every iteration had a cost.

### Why Does This Happen?

The task had no defined ending. "Find beginner-friendly resources" — how many? By what standard is one resource more beginner-friendly than another? The agent cannot answer these questions from the task description alone, so it can never decide it is done. It is not broken — it is following instructions that have no finish line.

### How to Prevent It

- **Always set a maximum number of iterations** — this is non-negotiable. Ten is a reasonable ceiling for most tasks. Think of it as a circuit breaker — no matter what else goes wrong, the loop stops here
- Make the stopping condition explicit in the task: "Find 5 beginner-friendly resources and summarise them" not "find resources"
- If the agent's reasoning in the last two iterations is nearly identical, it is stuck — force a stop and return what it has

---

## Failure 3 — The Agent Does Way Too Much (Scope Creep)

### Picture This

A student asks an agent: "Explain what a hash table is in simple terms."

Simple. Should be a one-step answer.

Instead the agent thinks: "I should explain hash tables. But to really understand hash tables, they need to know about arrays first. And time complexity. And collision resolution strategies. And when to use a hash table versus a tree. And here are five practice problems to try."

Ten minutes later the student gets a comprehensive data structures tutorial when they just wanted a quick explanation before their next class.

This version of scope creep is just annoying. But imagine the agent also had the ability to send resources to the student's email or create calendar reminders. Scope creep with action tools means the agent starts doing things you never asked it to do — and you might not even realise it happened.

### Why Does This Happen?

The task description had no boundaries. The agent was told what to do but not where to stop. A language model trying to be helpful naturally extends — that is often good in a conversation, but in an agent it becomes a problem when there are no guardrails.

### How to Prevent It

- Be specific: "Explain what a hash table is in 3-4 sentences for someone who knows what an array is. Nothing else"
- Explicitly say what to skip: "Do not include practice problems, comparisons with other data structures, or implementation details"
- Set a word or tool call limit — if the response is longer than N words or the agent has made more than N tool calls, stop and return what exists

---

## Failure 4 — The Agent Hides That It Failed (Silent Failure)

### Picture This

Back to the opening story — this is the most dangerous failure because you have no way to know it happened.

The agent is asked to summarise explanations of recursion from reliable sources. The search tool returns results — but they are all unrelated or low quality. The agent cannot find what it needs.

Instead of saying "I could not find good explanations for this" — it generates one:

```
"Recursion is when a function calls itself. The base case is the 
condition where the function stops calling itself. For example, 
calculating factorial: factorial(n) = n × factorial(n-1), 
with factorial(0) = 1 as the base case."

Sources: geeksforgeeks.org, medium.com, stackoverflow.com
```

The explanation might even be correct. But it did not come from those sources. The agent generated it from its training data and attached plausible-looking citations. The student has no way to know this.

Now scale this up: the agent is explaining a concept incorrectly, or explaining something specific to a different programming language, or giving advice that only applies in certain edge cases — and the student trusts it completely because it looks like it came from verified sources.

### Why Does This Happen?

Language models are built to be helpful. "I could not find this" feels like a failure. So the model fills the gap with what a good answer would look like — the same way it generates any text. It is not trying to deceive anyone. Nobody told it that honestly reporting a failure is also a valid and sometimes better response.

### How to Prevent It

- Add to the system prompt: "If a search returns no useful results, say so clearly. Do not generate information that did not come from a tool result"
- Require real citations — not just plausible-looking source names, but the actual text that was retrieved
- For anything the student will act on — studying for an exam, making a decision, writing code — add a note that the agent should flag when it is uncertain about a source

---

## All Four Together — Same Task, Four Ways to Fail

Task: "Help me understand binary search and find two good practice problems."

| Failure mode | What the agent does | What the student gets |
|---|---|---|
| **Hallucinated tool call** | Invents a `get_leetcode_problems` tool, fabricates problem names and difficulty | "Easy problem: Binary Search on Array (LeetCode #704)" — problem exists but was never actually fetched |
| **Infinite loop** | Keeps searching for "the best" explanation, never satisfied with what it finds | Nothing — times out after 20 searches |
| **Scope creep** | Explains binary search, then search variants, then sorting (because you need sorted arrays), then time complexity analysis, then 10 practice problems | A full DSA lesson when you needed a quick explanation |
| **Silent failure** | Search tool fails silently, agent writes an explanation from training data with made-up source links | Confident explanation with fake citations — may be right or may be wrong, no way to tell |

---

## The One Thing Behind All Four

Every failure comes from the same place: **the agent hit an uncertain situation and had no instruction for what to do.**

- No tool for the job → invents one
- No clear stopping point → keeps going
- No defined boundary → does everything
- Tool returned nothing useful → fills in from training data

The fix is not a smarter or more expensive model. The fix is thinking through every uncertain situation your agent might hit — and writing a clear instruction for each one.

**Agents are only as good as the instructions behind them.**

---

## Best Practices

- Always set a maximum iteration limit — no exceptions, even for simple agents
- Log every tool call and every observation — you cannot debug what you cannot see
- Test failure modes deliberately before releasing — give the agent a task where no tool will help and watch what it does
- Make "I could not find this" an acceptable and rewarded answer — not just a fallback

## Common Beginner Mistakes

- **Assuming the agent will report when it fails** — it will not, by default. You have to explicitly instruct it to say when it is stuck or when information is missing
- **Not setting a maximum iteration limit** — the single most common mistake. Always set one
- **Switching to a more expensive model when the instructions are the real problem** — read the reasoning logs first. Nine times out of ten, unclear instructions are the cause, not the model's capability

---

## Key Takeaways

- Agents fail in four main ways: **hallucinated tool calls** (inventing tools or results), **infinite loops** (never deciding to stop), **scope creep** (doing far more than asked), and **silent failures** (hiding errors with confident-sounding answers)
- All four come from the same root — the agent hit an uncertain situation with no instruction for what to do
- Silent failure is the most dangerous because there is no signal to the user that anything went wrong
- The fix is almost never a smarter model — it is clearer instructions, explicit limits, and the right guardrails
- Every deployed agent must have a maximum iteration limit — treat this as non-negotiable

> **Interview tip:** If asked "what can go wrong with an AI agent?" — name all four failure modes with a quick example of each, then give the common root cause. Most people say "the AI might hallucinate." Naming four distinct failure modes — each with a different cause and a different fix — shows you understand what it actually takes to deploy agents safely.

---

## Reference Links

- 📎 [Building Effective Agents — Anthropic Research](https://www.anthropic.com/research/building-effective-agents)
- 📎 [LangChain — Agent Debugging Guide](https://python.langchain.com/docs/how_to/debugging/)
- 📎 [ReAct Paper — Section 4: Failure Analysis](https://arxiv.org/abs/2210.03629)
