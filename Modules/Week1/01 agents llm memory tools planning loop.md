# Agents — LLM + Memory + Tools + Planning Loop

## Learning Objectives

By the end of this file you will be able to:

- Define what an AI agent is in precise technical terms
- Identify the four components every agent has and explain what each one does
- Trace the planning loop from input to action to observation to next decision
- Explain how an agent differs from a single LLM call and from a fixed pipeline
- Recognise agents you have already encountered in Semester 1

---

## What You Already Know

In Semester 1 you used Claude to answer questions, generate code, and process structured data. Every one of those interactions followed the same shape: you wrote a prompt, Claude produced a response, you read it and decided what to do next.

You were the agent. You were the one reading the output, deciding if it was good enough, and choosing the next step. Claude was a very capable tool — but it was not making decisions about what to do next. You were.

An AI agent changes this. It takes the decision-making loop — read output, evaluate, decide next step — and runs it inside the system itself, without waiting for you to intervene at each step.

---

## The Definition

An AI agent is a system that:

1. Receives a goal or task (not just a single question)
2. Breaks the task into steps
3. Executes each step using available tools
4. Observes the result of each step
5. Decides what to do next based on what it observed
6. Repeats until the task is complete or it determines it cannot proceed

The key word is **decides**. An agent does not follow a fixed script. It makes choices at runtime based on what it finds.

---

## The Four Components

Every agent — regardless of how it is built or what framework it uses — has four components. Understanding these components is more important than understanding any specific tool or library, because they are what make something an agent rather than a pipeline.

### 1. The LLM (Language Model)

The LLM is the reasoning engine. It reads the current situation — the goal, the conversation so far, the results of previous tool calls — and decides what to do next.

In practice this is Claude, GPT-4, Gemini, or another foundation model. The LLM does not execute code. It does not call APIs. It does not write to databases. It reasons and produces text — and that text is interpreted as an instruction to do something.

**What it does:** reads the current state and produces a decision about the next action.

**What it cannot do:** act on the world directly. It can only produce text that describes an action.

### 2. Memory

Memory is how the agent keeps track of what has happened. Without memory, every step the agent takes is effectively its first — it has no context about what it already tried, what worked, or what failed.

There are two kinds of memory:

**In-context memory** is everything currently in the LLM's context window — the original task, the conversation history, the results of every tool call made so far. It is fast and immediately accessible, but it is limited by the context window size and it disappears when the conversation ends.

**External memory** is stored outside the context window — in a database, a vector store, or a file. The agent retrieves what it needs when it needs it. This allows memory to persist across sessions and scale beyond what fits in a context window.

In Semester 1, when you built RAG pipelines, you were building a form of external memory — the vector database stored knowledge the LLM could retrieve at query time. That same principle applies inside an agent.

**What it does:** gives the agent continuity — the ability to know what it already tried and what it already knows.

### 3. Tools

Tools are functions the agent can call to interact with the world. They are the only way an agent can do anything beyond generating text.

A tool is defined by:
- A name (what the agent calls it by)
- A description (what it does — written in natural language, because the LLM reads this to decide when to use it)
- A schema (what inputs it expects and what it returns)

Examples of tools:

| Tool name | What it does |
|---|---|
| `search_web` | Takes a query string, returns search results |
| `read_file` | Takes a file path, returns the file contents |
| `query_database` | Takes a SQL query, returns rows |
| `call_api` | Takes a URL and parameters, returns the API response |
| `write_file` | Takes a path and content, writes to disk |
| `run_python` | Takes a code string, executes it, returns stdout |

When the LLM decides to use a tool, it produces structured output naming the tool and providing the inputs. The agent framework intercepts this, calls the actual function, and returns the result to the LLM as the next input.

**What it does:** gives the agent the ability to act — to retrieve information, to write data, to call services, to execute code.

**What it does not do:** decide when or how to use them. That is the LLM's job.

### 4. The Planning Loop

The planning loop is what turns the other three components into an agent. It is the cycle that runs repeatedly until the task is done.

```
RECEIVE TASK
      ↓
LLM reads current state (task + memory + tool results so far)
      ↓
LLM produces next action (use a tool / produce final answer)
      ↓
      ├── If action = use a tool:
      │       Call the tool
      │       Observe the result
      │       Add result to memory
      │       Return to top of loop
      │
      └── If action = final answer:
              Return the answer
              End the loop
```

This loop is what makes an agent different from a single LLM call. A single LLM call runs once and returns. An agent runs the loop as many times as needed — using each tool result to inform the next decision.

---

## A Concrete Example

Suppose you give an agent this task:

> "Find out what the current interest rate set by the Reserve Bank of India is, then calculate how much interest would accrue on a ₹10,00,000 loan over 3 years at that rate."

A single LLM call cannot reliably do this. The LLM's training data has a cutoff — it may not know the current rate. And even if it guesses, it cannot verify.

An agent with a `search_web` tool and a `calculate` tool handles it like this:

```
Task received: "Find current RBI rate and calculate interest on ₹10L over 3 years"

Loop iteration 1:
  LLM decision: I need the current rate. I will search for it.
  Tool call: search_web("RBI repo rate 2025")
  Result: "The RBI repo rate as of September 2025 is 6.5%"
  Memory updated.

Loop iteration 2:
  LLM decision: I have the rate. Now I will calculate.
  Tool call: calculate("10_00_000 * 0.065 * 3")
  Result: "195000"
  Memory updated.

Loop iteration 3:
  LLM decision: I have everything I need.
  Final answer: "The current RBI repo rate is 6.5%. Interest on ₹10,00,000
  over 3 years at this rate would be ₹1,95,000."
  Loop ends.
```

Notice what happened: the LLM never produced the answer from memory. It searched for the current information, then calculated. The agent did something that a single LLM call cannot reliably do.

---

## How This Differs from What You Built in Semester 1

In Semester 1 you built:

**Direct LLM calls** — one prompt in, one response out. You made the decisions about what to ask next.

**RAG pipelines** — a fixed sequence: retrieve chunks from a vector database, inject them into a prompt, call the LLM, return the response. The sequence was always the same. There was no decision-making at runtime about which step to take next.

An agent is different in one critical way: **the sequence of steps is not fixed**. The agent decides at runtime what to do based on what it finds. Some tasks need one tool call. Some need five. Some need the same tool called three times with different inputs. The agent figures this out as it goes.

| | Semester 1 direct LLM call | Semester 1 RAG pipeline | Agent |
|---|---|---|---|
| Fixed sequence | Yes | Yes | No |
| Uses tools | No | One (vector DB) | Many |
| Decides next step | You do | Pre-defined | The LLM does |
| Can adapt based on results | No | No | Yes |
| Memory | Context only | Context + vector DB | Context + external |

---

## Where Agents Appear in the Real World

You have already encountered systems that behave like agents, even if they were not labelled as such:

- **GitHub Copilot** completing multi-file refactors — it reads a codebase, plans changes, and applies them across files
- **Customer service bots** that look up your account, check order status, and process a refund — three separate tool calls in a single conversation
- **AI coding assistants** that run your tests, read the error, fix the code, and run the tests again — the loop runs until the tests pass
- **Claude's web search feature** — when Claude searches for current information, reads the results, and incorporates them into an answer, it is executing a minimal one-iteration planning loop

---

## What This Module Covers

This week covers the concepts and design decisions around agents. It does not build a full agent from scratch — that is a Year 2 skill, and for good reason. Building a production-grade agent requires handling:

- Tool call failures and retries
- Infinite loops (the agent keeps calling tools without making progress)
- Context overflow (the loop runs so long the context window fills up)
- Cost management (each loop iteration is an API call with a cost)
- Evaluation (how do you measure whether the agent completed the task correctly?)

What this module does build: the ability to design an agent for a domain problem — to decide which tools it needs, what memory it should use, where the loop should terminate, and what the failure modes are. That design skill is what this semester is about.

---

## Key Takeaways

- An AI agent is a system that receives a goal, breaks it into steps, executes steps using tools, observes results, and decides what to do next — repeating until the task is complete
- Every agent has four components: an LLM (reasoning), memory (continuity), tools (ability to act), and a planning loop (the cycle that ties them together)
- The planning loop is what distinguishes an agent from a single LLM call or a fixed pipeline — the sequence of steps is decided at runtime, not predetermined
- In Semester 1 you were the planning loop. An agent runs the loop itself
- Full agent builds are a Year 2 skill. This module covers design decisions — what tools, what memory, where to terminate, what can go wrong

---

## What Is Next

The next file covers the ReAct pattern — the specific structure most agents use to organise their reasoning. ReAct stands for Reason, Act, Observe — and it is the clearest way to understand what is happening inside the planning loop step by step.
