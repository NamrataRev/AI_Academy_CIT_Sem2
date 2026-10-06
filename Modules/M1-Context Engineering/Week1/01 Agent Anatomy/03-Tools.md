# Tools — The Hands

---

Imagine the most knowledgeable person you know. They have read everything, remember everything, and can reason through any problem perfectly.

But they have no hands.

They can tell you exactly which shelf the book is on, which page has the answer, which number to call. The plan is perfect. But nothing actually happens unless someone else carries it out.

Tools are the hands of an agent. They are the only way the agent can do anything beyond producing text.

---

## What a Tool Is

A tool is a function the agent can call to interact with the real world.

Search the internet. Read a file. Run a calculation. Send a message. Query a database. Check a price. Each of these is a tool — a specific capability the agent can reach for when the brain decides it is needed.

Without tools, an agent is just a language model. Smart, but stuck. It can reason about current stock prices but cannot check them. It can plan a research task but cannot read any papers. It can decide what code to run but cannot run it.

Tools are what turn a thinking machine into an acting one.

---

## Three Things Every Tool Has

**A name** — what the brain calls it. Simple and clear. Like `search_web` or `read_file` or `calculate`.

**A description** — a plain English explanation of what the tool does and when to use it. This is critical. The brain reads this description to decide which tool to reach for. A vague description leads to wrong choices. A precise description leads to smart ones.

**A schema** — what inputs the tool expects and what it returns. The brain uses this to form the instruction correctly.

---

## How a Tool Call Actually Works

This is the part most people picture wrong.

The brain does not run the tool. It never touches it directly. Here is what actually happens:

The brain decides it needs to search for something. It produces a structured instruction — not a thought, but a formatted call: *"Use search_web with this exact query."*

The agent framework reads that instruction. It runs the search. It gets results back from the internet. It hands those results to the brain as the next input.

Think of it like a surgeon and a scrub nurse. The surgeon says *"scalpel"* — they do not reach across and grab it. The nurse places it in their hand. The surgeon never touches the instrument tray directly. Every tool goes through the nurse.

The brain is the surgeon. The framework is the nurse. The tools are the instruments.

---

## Common Tools

| Tool | What it does |
|---|---|
| `search_web` | Searches the internet and returns results |
| `read_file` | Opens a file and returns its contents |
| `run_code` | Executes code and returns the output |
| `calculate` | Performs a calculation and returns the result |
| `call_api` | Makes a web request and returns the response |
| `query_database` | Runs a query and returns matching rows |

Different agents need different tools. A research agent might only need `search_web`. A data agent might need `read_file` and `calculate`. A customer service agent might need `query_database` and `send_email`. You only give an agent the tools it actually needs — nothing more.

---

## Why the Description Matters So Much

Here is something that surprises most people when they first build agents.

If your `search_web` tool has the description *"searches for things"* — the brain does not know when to use it versus any other tool. It makes guesses. Sometimes wrong ones.

If the description says *"searches the internet for current, live information — use this when you need today's prices, recent news, or anything that changes over time"* — the brain knows exactly when this is the right tool to reach for.

Writing tool descriptions is one of the most important skills in agent design. The brain is only as smart as the instructions it receives about what is available to it.

---

## Quick Recap

- Tools are the only way an agent can act — without them the brain can think but nothing happens
- Every tool has a name, a plain English description, and a schema — the brain reads these to decide when and how to use each tool
- The brain never runs a tool directly — it produces an instruction, the framework executes it
- Only give an agent the tools it actually needs — every extra tool is another decision point that can go wrong

---

## What Is Next

Every time a tool runs, a result comes back. That result needs to go somewhere — somewhere the brain can read it in the next loop. That is memory. The next topic covers how the agent holds on to everything it finds.
