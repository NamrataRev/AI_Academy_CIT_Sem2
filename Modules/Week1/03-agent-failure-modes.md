# Agent Failure Modes — What Goes Wrong and Why

---

## Learning Objectives

By the end of this file you will be able to:

- Name the four main ways an agent fails and explain what causes each one
- Recognise which failure mode is happening when you see an agent behave unexpectedly
- Describe what each failure looks like from the outside — what the user experiences
- Apply practical fixes for each failure mode

---

## Start Here — Agents Fail Differently From Regular AI

When a regular LLM call goes wrong, it is usually obvious. The answer is incorrect, or it hallucinates a fact, or it misunderstands the question. You read it, spot the problem, and try again.

Agents fail in more subtle and more expensive ways. Because an agent runs a loop — sometimes ten, twenty, or more iterations — a small problem early in the loop can silently snowball. By the time the agent produces a final answer, you may not even realise something went wrong along the way.

Worse, every loop iteration costs money. An agent stuck in a bad loop can burn through API budget before anyone notices.

This is why understanding failure modes before you build agents is not optional — it is the difference between an agent that is useful in production and one that is a liability.

There are four failure modes every agent builder needs to know.

---

## Failure Mode 1 — Hallucinated Tool Calls

### What it is

The agent calls a tool that does not exist, calls a real tool with made-up inputs, or reports that it called a tool when it actually did not.

### Why it happens

The language model is very good at generating plausible-sounding text. When it cannot figure out what tool to use — or when the tool it wants does not exist — it sometimes generates a tool call that looks correct but is not. It is doing what language models always do: producing the most plausible next token. The fact that the tool call is fictional does not stop the model from generating it confidently.

### What it looks like

The agent produces an observation that seems too convenient — exactly the right information, with no noise, formatted perfectly. Or the framework throws an error saying the tool does not exist. Or the agent references information in its reasoning that no tool actually returned.

### A concrete example

An agent is asked to check flight prices. It has a `search_web` tool but not a dedicated flight API. It generates:

```
Action: check_flight_prices
Action Input: {"from": "Chennai", "to": "Mumbai", "date": "2025-10-15"}
Observation: "Chennai to Mumbai on Oct 15 — ₹4,200 (IndiGo, 6am)"
```

The `check_flight_prices` tool does not exist. The agent invented both the tool call and the result. The user receives a specific price that came from nowhere.

### How to fix it

- Define tools precisely and give the agent an explicit list of what is available
- Instruct the agent that if no tool fits, it should say so rather than invent one
- Validate every observation — if the framework did not actually call a tool, the observation should not exist
- Log all tool calls and cross-check them against the list of registered tools

---

## Failure Mode 2 — Infinite Loop

### What it is

The agent keeps calling tools over and over without making meaningful progress toward an answer. It never decides the task is complete.

### Why it happens

Three common causes:

**The agent does not have enough information to proceed** — every search comes back with results that do not answer the question, so the agent keeps searching with slightly different queries, hoping for a better result.

**The termination condition is unclear** — the agent was not told clearly enough what "done" looks like, so it keeps gathering more information even when it already has enough.

**The agent gets into a cycle** — one tool's output triggers another call which triggers another call which circles back to the first.

### What it looks like

The agent runs for a very long time and produces no final answer. Costs accumulate. Or it eventually hits a maximum iteration limit and stops with a partial or empty response.

### A concrete example

An agent is asked: "Find me research papers on transformer models published this year."

It searches, finds papers, but is not sure if it has found enough. It searches again with a different query. Finds more. Still not sure. Searches again. The task never specified how many papers were "enough," so the agent has no way to decide it is done.

After 25 iterations it hits the maximum limit and returns an incomplete list with no explanation.

### How to fix it

- Always set a maximum number of iterations — treat this as non-negotiable
- Be explicit in the task description about when the agent should stop: "find 5 papers and then answer" not "find research papers"
- Add a reasoning check: if the agent's last three thoughts are nearly identical, it is stuck — force a stop
- After each iteration, compare what the agent knows now to what it knew before — if nothing changed, it is looping

---

## Failure Mode 3 — Scope Creep

### What it is

The agent does much more than was asked. It follows interesting tangents, gathers information it was not asked for, takes actions beyond the scope of the task, and produces a sprawling answer that addresses questions the user never had.

### Why it happens

The agent's reasoning stage is supposed to keep it focused. But if the task description is broad or if the agent's instructions do not clearly define boundaries, the reasoning stage generates increasingly ambitious plans. "While I am at it, I should also check..." is scope creep in action.

### What it looks like

The agent takes a very long time. It calls many tools. The final answer contains far more than was asked — multiple sections, unsolicited recommendations, related information the user did not request. It may even have taken actions (sent emails, modified files) that were never authorised.

### A concrete example

A user asks: "Check if our API endpoint is returning status 200."

The agent checks the endpoint. Finds it returns 200. But then thinks: "While I am here, I should also check response time. And validate the response schema. And check the error endpoint too. And check if the authentication token is about to expire."

Twenty minutes later the user gets a full API health report when they just wanted a yes or no.

### How to fix it

- Be specific in the task description — "check endpoint X and return whether it is 200 or not, nothing else"
- Explicitly list what the agent should not do as well as what it should do
- Set a tool call budget — if the agent has used more than N tools, it should stop and report what it has
- Review the agent's reasoning logs — scope creep is visible in the thought stage before the action is taken

---

## Failure Mode 4 — Silent Failure

### What it is

The agent encounters an error, cannot complete the task, or produces a wrong result — but presents it confidently as if everything went fine. The user has no idea something went wrong.

### Why it happens

Language models are trained to be helpful and to produce complete-sounding responses. When a tool call fails or returns an unexpected result, the model may fill in the gap from its training data — producing an answer that sounds correct but has no grounding in what the tools actually returned. This is the most dangerous failure mode because it is the hardest to detect.

### What it looks like

The agent produces a confident, well-formatted final answer. Nothing looks wrong. But the answer contains information that no tool actually returned — it was generated from the model's training data to fill a gap. The user acts on this information without knowing it is unverified.

### A concrete example

An agent is asked to check whether a specific regulation applies to a company's product. The `search_web` tool returns no relevant results — the regulation is too niche and recent to appear in search results.

Instead of saying "I could not find information about this regulation," the agent fills in from training data:

```
"Based on the regulatory framework, this product is likely exempt 
from the requirement under Section 4(b) of the Act."
```

This sounds authoritative. The company acts on it. The regulation actually does apply.

### How to fix it

- Instruct the agent explicitly: if a tool returns no useful result, say so in the final answer — do not fill in from general knowledge
- Require the agent to cite the specific tool and observation that supports each claim in its final answer
- Build output validation — if the final answer contains claims that do not trace to any observation, flag it
- Design the system prompt to treat "I could not find this" as an acceptable and correct answer

---

## The Four Failure Modes — Quick Reference

| Failure mode | What happens | Main cause | Key fix |
|---|---|---|---|
| **Hallucinated tool call** | Agent invents a tool or a result | Model generates plausible text even when no real tool fits | Define tools precisely; validate all observations |
| **Infinite loop** | Agent never decides it is done | Unclear termination condition; no progress check | Set max iterations; define "done" explicitly |
| **Scope creep** | Agent does far more than asked | Broad task description; no boundaries set | Be specific; list what not to do; set tool budgets |
| **Silent failure** | Agent fills gaps with training data and presents it as fact | Model trained to be helpful; fills gaps naturally | Require citations; make "I don't know" an acceptable answer |

---

## How These Failures Connect

Notice that all four failure modes have the same root cause: **the agent does not have clear enough instructions about what to do in an uncertain situation.**

- Hallucinated tool call: "I need a tool but don't have one — I'll invent it"
- Infinite loop: "I don't know when to stop — I'll keep going"
- Scope creep: "I don't know where the boundaries are — I'll keep expanding"
- Silent failure: "I don't have the information — I'll fill it in"

In every case, the agent is trying to be helpful in an uncertain situation, and doing the wrong thing because it was not told what the right thing is.

This is the most important design lesson in this file: **agent failures are almost always design failures.** The agent behaved exactly as a language model would behave given the instructions it had. The fix is almost never "use a smarter model" — it is "write clearer instructions and add the right guardrails."

---

## Best Practices

- Log every tool call and every observation — if you cannot see what the agent did, you cannot fix what went wrong
- Test each failure mode deliberately before deploying — give the agent a task where no tool will help and see if it hallucinates; give it a task with no clear stopping condition and see if it loops
- Build failure handling into the agent's instructions, not as an afterthought — tell the agent what to do when tools fail, when results are unclear, and when it is not sure

## Common Beginner Mistakes

- **Assuming the agent will say it failed** — by default, language models avoid saying they could not do something. Silent failure is the default, not the exception. You have to explicitly instruct the agent to say when it is stuck or when information is missing
- **Not setting a maximum iteration limit** — this is the single most common mistake with new agents. Always set one. It is your safety net for every other failure mode
- **Blaming the model when the instructions are the real problem** — if your agent keeps failing, read the reasoning logs before you switch to a different model. Nine times out of ten the instructions are the issue, not the model's capability

---

## Key Takeaways

- Agents fail in four main ways: hallucinated tool calls, infinite loops, scope creep, and silent failures
- All four failure modes trace back to the same root cause — unclear instructions about what to do in uncertain situations
- Silent failure is the most dangerous because the agent presents wrong information confidently — the user has no signal that something went wrong
- Every deployed agent needs a maximum iteration limit — no exceptions
- Agent failures are almost always design failures — the fix is clearer instructions and better guardrails, not a smarter model

> **Interview tip:** If asked "what can go wrong with an AI agent?" — name all four failure modes, give one concrete example of each, and explain the common root cause. Then say how you would prevent them: clear task descriptions, maximum iteration limits, explicit termination conditions, and output validation that requires every claim to trace to a real observation. Most people answer this question with "the AI can hallucinate." Naming four distinct failure modes — each with a different cause and a different fix — shows you have actually thought about deploying agents, not just reading about them.

---

## Reference Links

- 📎 [Building Effective Agents — Anthropic Research](https://www.anthropic.com/research/building-effective-agents)
- 📎 [Evaluating AI Agents — Common Failure Patterns](https://www.anthropic.com/research/evaluating-ai-systems)
- 📎 [LangChain — Agent Debugging Guide](https://python.langchain.com/docs/how_to/debugging/)
