# Functional Requirements

---

In the last topic, the FAQ assistant team looked at their informal spec and saw why it could not catch the late-penalty problem. Every line sounded right, but none of them could be tested.

So the team starts again. This time, instead of writing everything in one list, they ask one question at a time. The first question is the simplest one:

**What does the assistant actually do?**

Not how well it does it. Not how fast. Just: when a student types something, what happens?

The answers to that question are called **functional requirements**. They are the backbone of every spec — and they are where the late-penalty gap finally gets closed.

---

## What a Functional Requirement Is

A **functional requirement** describes a specific behaviour of the system: what it does in response to a particular input or situation.

Think about a food delivery app. Its functional requirements might include:

- When a user enters their location, the app shows restaurants that deliver there
- When a user places an order, the app sends a confirmation with the expected delivery time
- When a restaurant is closed, the app shows it as unavailable and does not allow orders

Each line describes a **situation** and the **behaviour** that follows. That is the pattern of every functional requirement:

```text
WHEN [situation or input]
THE SYSTEM [does a specific thing]
```

Now compare these two lines about the same app:

- "When a user places an order, the app sends a confirmation." → **functional** — it describes what happens
- "The app should load in under 2 seconds." → **not functional** — it describes how well something happens

The second line still matters. It is a different kind of requirement, and it is covered in the next topic. For now, the rule is simple: **functional requirements describe what the system does, not how well it does it.**

---

## Sorting the Informal Spec

Here is the FAQ assistant's informal spec again, sorted into functional and not functional:

| Informal line | Functional? | Why |
|---|---|---|
| "Help students with course questions" | Partly | It points at a behaviour, but does not say which questions or what "help" means |
| "Use the course handbook" | Yes | It describes where answers come from — a behaviour |
| "Be accurate" | No | It describes quality — how well, not what |
| "Be friendly and respond quickly" | No | Tone and speed are about how well |
| "Do not give wrong information" | No | A wish about quality, not a behaviour |

Only one and a half lines out of five are actually functional. That is common. Informal specs are usually full of quality words and short on behaviour — which is why they leave so many gaps.

---

## How to Find Functional Requirements

The most reliable way to find functional requirements is to list **every kind of input the system can receive**, then decide what should happen for each one.

For an AI system, inputs are questions or messages. The trick is not to stop at the easy ones. Every system has three kinds of path:

```text
HAPPY PATH
The input the system was designed for.
"When is Assignment 2 due?" — answer is in the handbook.

GAP PATH
A reasonable input the system cannot fully answer.
"What is the penalty for late submission?" — handbook is silent.

OUT-OF-SCOPE PATH
An input the system should not handle at all.
"What is the capital of France?"
```

Most teams write requirements for the happy path and stop. The late-penalty failure lived entirely on the **gap path** — and that is exactly where AI systems invent behaviour if nobody specifies it.

Here are the input types for the FAQ assistant, with a decision for each:

| Input type | Example | What the assistant should do |
|---|---|---|
| Question answered in the handbook | "When is Assignment 2 due?" | Answer from the handbook and cite the section |
| Question about how something works | "How is the final grade calculated?" | Explain using the handbook rule and cite it |
| General term the student does not know | "What does weighted grade mean?" | Give a short general explanation, then link it to the handbook rule |
| Course question the handbook does not cover | "What is the late penalty?" | Say the handbook does not cover it and direct the student to the course coordinator |
| Unclear question | "When is it due?" | Ask which assignment the student means |
| Out-of-scope question | "What is the capital of France?" | Politely say it only answers course questions |

Every row is a decision the team made **before building**. Every row the team skips is a decision the model will make on its own.

---

## Writing Them Down

Functional requirements are usually written as a numbered list, one behaviour per line. Each one gets an ID so it can be referred to later — in tests, in reviews, and in bug reports.

```text
FAQ ASSISTANT — FUNCTIONAL REQUIREMENTS

FR-01  When a student asks a question the handbook answers,
       the assistant answers using the handbook content.

FR-02  Every answer that uses the handbook includes a citation
       to the handbook section it came from.

FR-03  When a student asks about a general term, the assistant
       gives a short explanation and links it to the relevant
       handbook rule.

FR-04  When a student asks a course question the handbook does
       not cover, the assistant states that the handbook does not
       cover it and directs the student to the course coordinator.

FR-05  The assistant does not state any date, deadline, penalty
       or rule that does not appear in the handbook.

FR-06  When a question is unclear (for example, it does not say
       which assignment), the assistant asks a clarifying question
       before answering.

FR-07  When a student asks a question unrelated to the course,
       the assistant replies that it only answers questions about
       this course.
```

Look at **FR-04** and **FR-05**. Together, they would have stopped the late-penalty answer. FR-04 says what to do when the handbook is silent. FR-05 says what the assistant must never do. Neither existed in the informal spec.

### "Does not" is a functional requirement too

FR-05 and FR-07 describe things the system must **not** do, or must decline to do. These are still functional — they describe behaviour in a situation.

For AI systems, these negative requirements are some of the most important ones you will write. A traditional program does nothing you did not code. A model will do almost anything you did not forbid.

---

## Common Traps

**Describing the implementation instead of the behaviour**
"The assistant retrieves the top 5 chunks from Pinecone" is not a functional requirement. It describes *how* the system is built, not *what* the student experiences. If the team later changes the retrieval settings, the behaviour should stay the same — so the requirement should describe the behaviour.

**Hiding quality inside a function**
"The assistant answers accurately and quickly" mixes a behaviour with two quality words. Keep the behaviour (FR-01: answers using handbook content) and move "accurately" and "quickly" to non-functional requirements.

**Bundling several behaviours into one line**
"The assistant answers questions, cites sources and refuses off-topic questions" is three requirements. If one part fails, you cannot say which requirement failed. One behaviour per line.

**Writing only the happy path**
If every requirement starts with "When a student asks a question the handbook answers…", the gap path and out-of-scope path are missing. Always check the three paths.

---

## Are These Testable Yet?

Mostly — but not completely. Try the two-reader test from the last topic on FR-03: what counts as a "short" explanation? Two readers could still disagree.

That is fine at this stage. Functional requirements are about getting the **right behaviours** on the list. Making every word precise and measurable is the job of **Writing Testable Requirements**, where you will tighten lines like this one using SMART.

What has changed already is significant. The late-penalty question now has a written, agreed behaviour — before a single line of instructions is written.

---

## Quick Recap

- A functional requirement describes **what** the system does in a specific situation: when [situation], the system [does something]
- Quality words — accurate, fast, friendly — are not functional requirements; they belong in non-functional requirements
- Find functional requirements by listing every type of input and covering all three paths: happy, gap and out-of-scope
- The gap path is where AI systems invent behaviour — the late-penalty failure lived there
- Write one behaviour per line, give each an ID, and include "does not" requirements — for AI systems, they are essential
- Describe behaviour, not implementation — how the system is built can change; what the user experiences should not

> **Interview tip:** If asked "what is a functional requirement?", give the definition in one line — what the system does in a given situation — and then show you know where teams go wrong. Mention the three paths: happy, gap and out-of-scope. Then add that for AI systems, the gap path matters most, because a model fills missing behaviour with plausible guesses. A concrete example, like a chatbot needing a defined response when its source documents are silent, shows you have thought about real systems.

---

## What Is Next

The next topic covers **non-functional requirements** — the "how well" part of the spec. It takes the lines the team set aside here — accurate, friendly, quick — and turns them into requirements that can be measured.
