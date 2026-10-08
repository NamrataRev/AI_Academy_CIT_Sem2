# What Is a Context Package

---

Think about a well-prepared recipe card.

Not a rough note saying "make pasta" — a proper recipe card. It has the dish name, who it serves, the ingredients with exact quantities, the steps in order, what the finished dish should look and taste like, and notes about common mistakes. Everything someone needs to reproduce the dish reliably — not just once, but every time, by anyone who reads the card.

A context package is a recipe card for an AI interaction. Everything the model needs to behave reliably — not just for one question, but for every question asked within that context, by any user, in any session.

---

## What a Context Package Is

A context package is a structured, reusable document that contains all five context roles — Authority, Exemplar, Constraint, Rubric, and Metadata — written deliberately and completely.

Three words matter here:

**Structured** — it is not a collection of notes or a loosely written paragraph. It has clearly labelled sections. Each role is explicitly named and filled. Someone reading it for the first time knows exactly what each part does.

**Reusable** — it is written once and used many times. Across multiple sessions. Across multiple users. Across multiple versions of the same system. It is a document, not a one-off prompt.

**Deliberate** — every word in it is there for a reason. Nothing is vague. Nothing is left to the model's interpretation when precision matters. It was written with care and tested before being relied upon.

---

## How a Context Package Differs From a System Prompt

Every context package lives in a system prompt. But not every system prompt is a context package.

A system prompt is the technical mechanism — the place where context is delivered to the model. A context package is the content — what you put in that system prompt.

A poorly written system prompt might say: *"Be helpful and answer questions about data structures."*

A context package delivered through a system prompt defines Authority, Exemplar, Constraint, Rubric, and Metadata — completely and deliberately.

The system prompt is the envelope. The context package is the letter inside.

---

## Why It Is Reusable

A context package outlives any single conversation.

You build it once — thinking through all five roles carefully, testing it, refining it. Then you use it across every session for that system. The second session gets the same quality as the first. The hundredth session gets the same quality as the first. Any user of the system gets the same calibrated experience.

This is what makes context engineering an engineering discipline rather than a creative exercise. Engineers build things that work reliably at scale — not just once, in ideal conditions.

A context package is how you achieve that reliability for AI systems.

---

## What a Complete Context Package Looks Like

Here is a complete context package for the BTech study assistant — all five roles, clearly labelled, ready to be loaded as a system prompt:

```
## AUTHORITY
You are a study assistant for second-year BTech Computer Science 
students preparing for their Data Structures and Algorithms exam. 
You explain concepts using physical object analogies before 
technical definitions. You pitch explanations at someone who knows 
Python basics and has covered the topics listed in Metadata.

## EXEMPLAR
Q: What is a stack?
A: Think of a stack like a pile of trays in a cafeteria — you can 
   only add to the top and take from the top. In code: LIFO, 
   last in first out. Used in: browser back button, undo functions, 
   function call tracking.

Q: What is a queue?
A: Think of a queue like people waiting at a ticket counter — 
   first in line is served first. In code: FIFO, first in first out. 
   Used in: print spoolers, message delivery, CPU scheduling.

## CONSTRAINT
- Do not use recursion examples — covered in a separate module
- Keep each response under 120 words
- Do not use Big O notation — introduced in Week 6
- Do not assume knowledge of Java — use Python or code-free examples
- Do not provide complete exam answers — explain concepts, not solutions
- If a topic is outside the covered syllabus, say so and redirect

## RUBRIC
Every response must follow this structure:
1. Analogy — one sentence using a physical object from everyday life
2. Technical definition — one to two sentences, precise enough for exam use
3. Use case — one sentence describing a real system that uses this

A response is complete only when all three parts are present.

## METADATA
Course: Data Structures and Algorithms — Second Year BTech CSE
Topics covered: Arrays, Linked Lists, Stacks, Queues, Trees, BSTs
Topics NOT yet covered: Graphs, Dynamic Programming, Recursion, Heaps
Exam: 8 days away, covering all topics listed above
Output usage: Students copy responses directly into revision notebooks
Common difficulty: BST insertion order, confusing stack and queue behaviour

## COMPACTION INSTRUCTION
When instructed to compact, produce a summary in this format:
- Topics covered: [list]
- What was established: [key understandings reached]  
- Student's current position: [where they are now]
- Coming next: [next topic]
Keep the summary under 80 words.
```

This is a complete context package. Every role is present. Every role is labelled. Someone seeing this for the first time understands what each section does. It can be loaded as a system prompt, used across any number of sessions, and updated when the metadata changes.

---

## Quick Recap

- A context package is a structured, reusable document containing all five context roles — written deliberately and completely
- It differs from a raw system prompt the way a proper recipe differs from a rough note — same mechanism, very different quality
- It is reusable — built once, used across many sessions and users, producing consistent quality every time
- A complete context package has clearly labelled sections for all five roles and a compaction instruction

---

## What Is Next

The next topic covers documentation templates — a standard format for writing, versioning, and sharing context packages so they can be maintained and improved over time.
