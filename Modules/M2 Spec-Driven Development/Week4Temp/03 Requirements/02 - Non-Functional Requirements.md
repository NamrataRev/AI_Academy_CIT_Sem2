# Non-Functional Requirements

---

The FAQ assistant team now has seven functional requirements, FR-01 to FR-07. They build a new version and test it against every one.

It passes all seven. It answers handbook questions with citations. It handles the late-penalty question correctly — it says the handbook does not cover it and points the student to the course coordinator. It refuses "What is the capital of France?" politely.

They launch it. Within a week, students have stopped using it.

The feedback is not about wrong answers. It sounds like this:

- *"I waited almost 30 seconds for one answer."*
- *"I asked when Assignment 2 was due and got four paragraphs."*
- *"It told me 'That is not in the handbook. Contact someone else.' — felt like being brushed off."*
- *"I asked the same question twice and got two different dates."*

Every functional requirement passed. The product still failed.

The team had specified **what** the assistant does. They had not specified **how well** it does it. Those missing requirements have a name: **non-functional requirements**.

---

## What a Non-Functional Requirement Is

A **non-functional requirement (NFR)** describes a quality the system must have, or a limit it must stay within. It does not add a new behaviour. It sets the standard that existing behaviours must meet.

Go back to the food delivery app from the last topic:

- Functional: *"When a user places an order, the food is delivered."*
- Non-functional: *"Food arrives within 45 minutes, and hot."*

If the food arrives three hours late and cold, the functional requirement passed — the food was delivered. Nobody would call that a success.

That is exactly what happened to the FAQ assistant. The behaviours were right. The quality was not.

```text
FUNCTIONAL       →  WHAT the system does
                    "Answers handbook questions with a citation"

NON-FUNCTIONAL   →  HOW WELL it does it
                    "Within 5 seconds, in under 150 words,
                     with the same facts every time"
```

---

## The Main Types for AI Systems

Non-functional requirements come in a few common categories. These are the ones that matter most for an AI system like the FAQ assistant:

| Category | The question it answers | FAQ assistant example |
|---|---|---|
| **Performance** | How fast? | How long does a student wait for an answer? |
| **Faithfulness** | How closely does it stick to its sources? | How much of each answer is actually supported by the handbook? |
| **Consistency** | Does it give the same facts every time? | Does "When is Assignment 2 due?" always get the same date? |
| **Usability and tone** | Is it easy and pleasant to use? | Is the answer short, clear and respectful? |
| **Privacy and security** | What must it protect? | Does it avoid asking for or storing personal details? |
| **Cost** | What can it afford to spend? | How much does each answer cost to generate? |

Every complaint from the launch fits one of these rows. The 30-second wait is **performance**. The four-paragraph answer and the blunt refusal are **usability and tone**. The two different dates are **consistency**.

---

## Turning Quality Words Into Measurable Requirements

In the last topic, the team set aside three lines from the informal spec because they described quality, not behaviour: *accurate*, *friendly* and *quick*.

This is where those lines come back. The job is to turn each quality word into something with a **number** and a **way to check it**:

| Quality word | Question to ask | Measurable version |
|---|---|---|
| "Quick" | Quick for whom, measured how? | 95% of answers appear within 5 seconds |
| "Accurate" | Accurate compared to what? | Every date, deadline and penalty matches the handbook exactly |
| "Friendly" | What does friendly look like? | Answers use plain language, never blame the student, and offer a next step when refusing |
| "Not too long" | How long is too long? | Answers are under 150 words unless the student asks for more detail |

Notice the pattern. Each vague word gets replaced by:

1. **A number or a clear yes/no check** — 5 seconds, 150 words, "matches the handbook exactly"
2. **A defined way to measure it** — timing the response, counting words, comparing against the handbook

Without both, it is still a wish.

---

## Writing Them Down

Non-functional requirements are written the same way as functional ones — numbered, one quality per line. Each line also says **how it will be measured**.

```text
FAQ ASSISTANT — NON-FUNCTIONAL REQUIREMENTS

NFR-01  Performance
        95% of answers appear within 5 seconds.
        Measured: time from question sent to answer shown,
        across the full test question set.

NFR-02  Faithfulness
        Every date, deadline and penalty in an answer matches
        the handbook exactly.
        Measured: each test answer checked against the handbook.

NFR-03  Consistency
        The same question asked 5 times returns the same facts
        every time (wording may differ).
        Measured: repeat each test question 5 times and compare.

NFR-04  Length
        Answers are under 150 words unless the student asks for
        more detail.
        Measured: word count of each test answer.

NFR-05  Tone
        Answers use plain language, never blame the student, and
        every refusal includes a next step.
        Measured: two reviewers check each answer against these
        three points and must agree.

NFR-06  Privacy
        The assistant never asks for a student ID, email or other
        personal details.
        Measured: review of all test conversations.
```

Look at NFR-05. Tone is the hardest quality to measure, because it feels like an opinion. The trick is to break "friendly" into a few specific checks that two people can agree on. It is still a human judgement — but now it is a consistent one.

---

## Why AI Systems Need Rates, Not Single Checks

There is one important difference between NFRs for traditional software and NFRs for AI systems.

A traditional program gives the same output every time. Test it once and you know how it behaves.

An AI model can give **different answers to the same question**. The launch complaint — "I asked the same question twice and got two different dates" — is a direct result of this.

That means a single test proves very little. If you ask "When is Assignment 2 due?" once and get the right date, you do not know whether it will be right the next time.

So NFRs for AI systems are usually written as **rates across many runs**:

- Not *"the answer is fast"* but *"95% of answers within 5 seconds"*
- Not *"it gives the right date"* but *"the same question asked 5 times returns the same facts every time"*

If a requirement can only be checked once, it is not a reliable requirement for an AI system.

---

## How Functional and Non-Functional Work Together

Functional and non-functional requirements are not two separate lists that happen to sit next to each other. NFRs **attach to** functional requirements and set the standard for them.

| Functional requirement | Non-functional requirements that apply |
|---|---|
| FR-01 — Answers from the handbook | NFR-01 (within 5 s), NFR-02 (facts match), NFR-03 (same facts every time), NFR-04 (under 150 words) |
| FR-04 — Handbook silent → redirect to coordinator | NFR-05 (no blame, includes a next step) |
| FR-06 — Unclear question → ask for clarification | NFR-01 (within 5 s), NFR-05 (plain language) |

The blunt refusal — *"That is not in the handbook. Contact someone else."* — passed FR-04. It failed NFR-05. Only with both requirements in place does the team get the answer they actually wanted:

*"The handbook doesn't cover late penalties. Your course coordinator can confirm the current policy — you can reach them at the contact listed on the course page."*

---

## When Requirements Pull Against Each Other

Non-functional requirements sometimes conflict.

NFR-04 says answers stay under 150 words. But "How is the final grade calculated?" might need a longer explanation to be complete. Shorter answers are easier to read. Complete answers are more useful. Both are reasonable goals.

A good spec does not pretend the conflict is not there. It decides which one wins. That is why NFR-04 includes *"unless the student asks for more detail."* The team made the trade-off on paper, instead of leaving the model to make it differently each time.

---

## Common Traps

**Leaving out the number**
"The assistant should respond fast" is still a wish. Every NFR needs a number or a clear yes/no check.

**Choosing a number nobody can meet**
"100% of answers within 0.5 seconds" sounds impressive, but if the system cannot do it, the requirement will be ignored. A requirement must be realistic to be useful — this is the **Achievable** part of SMART, covered in the next topic.

**Testing once and calling it done**
One fast answer or one correct date says almost nothing about an AI system. Measure across many runs.

**Forgetting NFRs entirely**
This is the most common trap — and exactly what happened at launch. A system with perfect functional requirements and no NFRs can still be slow, inconsistent and unpleasant to use.

---

## Quick Recap

- Non-functional requirements describe **how well** the system does what it does — speed, faithfulness, consistency, tone, privacy, cost
- A system can pass every functional requirement and still fail its users, as the FAQ assistant did at launch
- Turn each quality word into a measurable requirement: a number or clear check, plus a defined way to measure it
- AI systems can give different answers to the same question, so NFRs should be measured as rates across many runs, not single checks
- NFRs attach to functional requirements and set the standard each behaviour must meet
- When NFRs conflict, the spec decides which one wins — not the model

> **Interview tip:** If asked "what is the difference between functional and non-functional requirements?", give the short answer — what the system does versus how well it does it — and then add something most candidates miss. For AI systems, NFRs like consistency and faithfulness must be measured as rates across many runs, because the same input can produce different outputs. Mentioning a concrete example, such as "the same question asked five times should return the same facts", shows you understand how AI systems are actually tested.

---

## What Is Next

The next topic covers **writing testable requirements**. The team now has functional and non-functional requirements — but some lines are still not as precise as they need to be. You will use the **SMART** framework to check every requirement and rewrite the weak ones, one letter at a time.
