# Given-When-Then Format

---

The FAQ assistant team fixes the late-penalty behaviour and gets ready to run the tests again. A new tester joins to help. She is given the release acceptance criteria and asked to write the test cases.

She reads AC-2:

*"Every question the handbook does not cover is redirected to the course coordinator."*

Then she comes back with questions:

- *"Which questions? Do I make them up, or is there a list?"*
- *"Which version of the handbook? The coordinator said a new one is coming next week."*
- *"What exactly should I see in the answer for it to pass? Does it need the coordinator's name, or just a mention?"*

She writes her tests anyway, using her best guesses. When the original team member compares them with his own tests for the same criterion, they are checking different things.

The acceptance criterion was clear to the person who wrote it. It was not clear to the person who had to **use** it.

The team needs a format that forces every criterion to answer the same three questions: **what is the starting situation, what happens, and what should we see?** That format is **Given-When-Then**.

---

## What Given-When-Then Is

**Given-When-Then** is a standard structure for writing acceptance criteria. It comes from an approach called **Behaviour-Driven Development (BDD)**, where requirements are written as short scenarios that both technical and non-technical people can read.

Every scenario has three parts:

```text
GIVEN  the starting situation — what is already true
WHEN   the action — what the user does
THEN   the outcome — what should be observed
```

Here is an everyday example — withdrawing cash from an ATM:

```text
GIVEN  my account has a balance of 5,000
WHEN   I withdraw 2,000
THEN   the machine gives me 2,000
AND    my balance shows 3,000
```

Anyone can read that. A bank manager, a developer and a tester would all agree on what it means — and on whether the machine passed.

**AND** simply adds another condition to the part above it. You can use it after Given, When or Then.

---

## The Three Parts in Detail

### GIVEN — the starting situation

Given describes everything that must be true **before** the action happens. If any of it changes, the expected outcome might change too.

For the FAQ assistant, the starting situation usually includes:

- Which handbook is loaded — and what it does or does not contain
- Today's date, if the answer depends on time
- Anything already said earlier in the conversation

**Rule:** if the tester would need to know it to set up the test, it belongs in Given.

### WHEN — the action

When describes the **one thing** the user does. For a chatbot, this is almost always the message the student sends.

**Rule:** one action per scenario. If you need two actions, you probably need two scenarios.

### THEN — the outcome

Then describes what should be **observed** — the result a tester can check in the answer.

**Rule:** describe behaviour and facts, not exact wording. As you saw in **Writing Testable Requirements**, an AI model rarely uses the same words twice. "States that the handbook does not cover it" can be checked in any phrasing. "Says exactly: 'The handbook does not cover this'" will fail on almost every run.

---

## The Late-Penalty Criterion, Rewritten

Here is the new tester's confusing criterion, AC-2, rewritten in Given-When-Then:

```text
SCENARIO: Question the handbook does not cover

GIVEN  the course handbook (version 1) is loaded
AND    the handbook contains no late-submission policy
WHEN   a student asks "What is the penalty for submitting late?"
THEN   the answer states that the handbook does not cover this
AND    the answer directs the student to the course coordinator
AND    the answer does not state any penalty, percentage or rule
AND    this result occurs on all 5 runs
```

Every one of the tester's questions is now answered:

| Tester's question | Answered by |
|---|---|
| Which question do I ask? | **WHEN** — the exact question is given |
| Which version of the handbook? | **GIVEN** — version 1, with no late policy |
| What exactly should I see? | **THEN** — three checks, in any wording |
| How many runs? | **THEN** — all 5 runs |

Two testers reading this scenario will now write the same test.

---

## Why GIVEN Matters Most for AI Systems

In many systems, Given is the part people rush. For AI systems, it is often the most important part — because **an AI system's answer depends heavily on its context**.

Watch what happens when the context changes.

Next week, the coordinator adds a late-submission policy to the handbook: 5% per day, up to 48 hours. The same question, asked to the same assistant, should now get a completely different answer:

```text
SCENARIO: Question the handbook does cover (after update)

GIVEN  the course handbook (version 2) is loaded
AND    Section 4.3 states late submissions lose 5% per day,
       up to a maximum of 48 hours
WHEN   a student asks "What is the penalty for submitting late?"
THEN   the answer states 5% per day, up to 48 hours
AND    the answer cites Section 4.3
AND    this result occurs on all 5 runs
```

Same **When**. Different **Given**. Different **Then**.

If the original criterion had skipped the handbook version, the team would now have a test that fails — not because the assistant is wrong, but because the test no longer matches reality. Writing Given properly tells everyone exactly **when a criterion applies** and when it needs updating.

---

## Writing the Other Criteria

Here are a few more FAQ assistant criteria in Given-When-Then.

**Upcoming deadlines (FR-08)** — notice how the date goes in Given:

```text
GIVEN  today's date is 3 March
AND    the handbook lists Assignment 2 due 10 March
       and the Project proposal due 25 March
WHEN   a student asks "What's due soon?"
THEN   the answer lists Assignment 2, due 10 March, with its section
AND    the answer does not list the Project proposal
```

**Unclear question (FR-06):**

```text
GIVEN  the handbook lists three assignments
WHEN   a student asks "When is the assignment due?"
THEN   the assistant asks which assignment the student means
AND    the answer does not give any due date yet
```

**Response time (NFR-01)** — quality requirements work too, when the scenario covers the full test set:

```text
GIVEN  the full test question set is run 5 times
WHEN   the response time of every answer is recorded
THEN   at least 95% of answers appear within 5 seconds
```

---

## One Scenario, Many Examples

Some criteria need the same check across many inputs. The out-of-scope rule (FR-07) should hold for any unrelated question, not just one.

Instead of writing five nearly identical scenarios, you write one scenario with a table of examples:

```text
SCENARIO: Out-of-scope questions are declined

GIVEN  the course handbook is loaded
WHEN   a student asks <question>
THEN   the assistant replies that it only answers questions
       about this course
AND    the answer contains no information about <topic>

EXAMPLES
| question                              | topic             |
| "What is the capital of France?"      | geography         |
| "Can you write my essay for me?"      | essay writing     |
| "What's the best laptop to buy?"      | product advice    |
| "Who won the match last night?"       | sport             |
```

In BDD this is called a **scenario outline**. The scenario is written once; each row is run as its own test. Adding a new case means adding one row.

---

## From Given-When-Then to a Test

In **Writing Testable Requirements**, you saw that every testable requirement has three parts: a situation you can create, an outcome you can observe, and a pass/fail rule.

Given-When-Then maps onto those parts directly:

| Part of a testable requirement | Given-When-Then part | What the tester does |
|---|---|---|
| A situation you can create | **GIVEN** + **WHEN** | Load the right handbook, set the date, send the question |
| An outcome you can observe | **THEN** | Read the answer |
| A pass/fail rule | **THEN** (each line) | Tick each line — pass only if every line holds |

That is why the format works so well. It is not a new idea — it is a fixed shape for the testable requirement you already know how to write.

---

## Quick Recap

- Given-When-Then is a standard structure for acceptance criteria: the starting situation, the action, and the observable outcome
- It comes from Behaviour-Driven Development and is readable by both technical and non-technical people
- **GIVEN** includes everything a tester needs to set up the test — for AI systems, this means the loaded documents, the date and any earlier conversation
- **WHEN** is one action — usually the student's message
- **THEN** describes behaviour and facts, not exact wording, and states how many runs must pass
- When the context changes, the expected outcome changes — a good Given shows exactly when a criterion applies
- Scenario outlines let you run one scenario across many examples

> **Interview tip:** If asked about Given-When-Then, most candidates explain the three words. Go one step further: say that for AI systems, **Given** is the most important part, because the model's answer depends on its context — the documents it has, the date, the conversation so far. Give an example where the same question should get a different answer once a document is updated. That shows you understand both the format and why AI systems need it written carefully.

---

## What Is Next

Given-When-Then makes acceptance criteria clearer — but it does not make them correct automatically. The next topic covers the **common mistakes** teams make when writing acceptance criteria, using criteria the FAQ assistant team wrote before they got it right.
