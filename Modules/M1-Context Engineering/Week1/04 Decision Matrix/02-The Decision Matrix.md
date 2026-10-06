# The Decision Matrix

---

A carpenter does not use a hammer for every job. A hammer is right for nails. A saw is right for cutting. A drill is right for screws. Using the wrong tool does not just make the job harder — it can damage the work.

Choosing between a direct LLM call and an agent is the same kind of decision. The right choice depends on the nature of the task. The decision matrix gives you a structured way to make that choice — quickly, every time.

---

## The Four Situations

Every task you might give an AI system falls into one of four situations. Each situation has a right answer.

---

**Situation 1 — Single task, answer exists in training data**

The task needs one response and the model already has the knowledge to produce it.

*Examples: Explain recursion. Translate this sentence. Write a function that reverses a string. Summarise this paragraph I am pasting.*

**Right choice: Direct LLM call.**

No tools needed. No loop needed. One prompt, one response, done. Adding an agent here adds cost and complexity with no benefit.

---

**Situation 2 — Multiple steps, but the steps are always the same**

The task needs more than one step — but the sequence never changes. The output of one step feeds into the next, and you know exactly what those steps are before you start.

*Examples: Extract key points from a document, then format them as a table, then translate the table. Always the same three steps, always in the same order.*

**Right choice: Chained calls or a fixed pipeline.**

You do not need an agent to decide what to do next — you already know. A fixed sequence of calls is more predictable, easier to debug, and cheaper than a full agent loop.

---

**Situation 3 — Multiple steps, and the steps depend on what is found**

The task needs more than one step — and you cannot know what those steps are until you see the results along the way. The path changes based on what is discovered.

*Examples: Research a topic across multiple sources, decide which sources are most relevant, go deeper on the relevant ones, and produce a synthesis. The steps depend entirely on what the searches return.*

**Right choice: Agent.**

This is what agents are built for. The planning loop exists precisely for tasks where the next step is unknown until the current step is done.

---

**Situation 4 — High stakes, and a wrong answer causes real harm**

The task involves decisions where an error has serious consequences — financial, legal, medical, safety-critical. The cost of a wrong answer is too high to leave to an automated system alone.

*Examples: Reviewing a contract for legal risk. Recommending a medical dosage. Approving a financial transaction.*

**Right choice: Agent with human-in-the-loop.**

Even a well-designed agent can fail silently. For high-stakes decisions, a human must review the agent's output before it is acted on. The agent does the research and drafts the recommendation. The human makes the final call.

---

## The Matrix at a Glance

| Situation | Right choice |
|---|---|
| Single task, knowledge already exists | Direct LLM call |
| Multiple steps, sequence is fixed | Chained calls or fixed pipeline |
| Multiple steps, sequence depends on findings | Agent |
| High stakes, wrong answer causes real harm | Agent + human-in-the-loop |

---

## How to Use It

When you get a new task, ask two questions in order:

**Is this one step or multiple?**
If one step and the model knows the answer — direct call. Done.

**If multiple steps — are they fixed or do they depend on what is found?**
Fixed sequence — chained calls. Depends on findings — agent. High stakes — add a human.

Most tasks sort themselves out with just these two questions.

---

## Quick Recap

- Every task falls into one of four situations — each has a right tool
- Single step with existing knowledge → direct call
- Multiple fixed steps → chained calls or fixed pipeline
- Multiple steps depending on findings → agent
- High stakes → agent with human review
- Two questions decide most cases: is it one step or multiple, and are the steps fixed or dependent on findings

---

## What Is Next

The matrix gives you the framework. The next four topics walk through each situation in depth — starting with the simplest: when a single direct call is exactly the right tool and why reaching for an agent would be a mistake.
