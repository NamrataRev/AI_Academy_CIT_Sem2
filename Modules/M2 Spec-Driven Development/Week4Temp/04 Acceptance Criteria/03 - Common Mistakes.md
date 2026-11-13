# Common Mistakes

---

The FAQ assistant now has a clean set of acceptance criteria, all written in Given-When-Then. The late-penalty question is handled. The new tester's questions are answered. The tests run smoothly.

But the criteria did not start out that way.

Before the team got them right, there was a shared folder called `ac-drafts`. It is full of criteria that looked reasonable when they were written — and then caused problems the moment someone tried to test against them. One draft let a broken build pass. Another failed a perfectly good build. One started failing a month after it was written, even though nobody had changed the assistant.

This topic goes through that folder. Every mistake in it is a common one — almost every team makes most of them at least once. Knowing what they look like is the fastest way to avoid them.

The mistakes fall into three groups:

```text
1. MISTAKES IN THE SCENARIO   → how a single criterion is written
2. MISTAKES IN COVERAGE       → what the criteria check, and what they miss
3. MISTAKES IN THE PROCESS    → when and how the criteria are agreed
```

---

## Group 1 — Mistakes in the Scenario

### Mistake 1: A vague THEN

**From the drafts:**

```text
GIVEN  the handbook is loaded
WHEN   a student asks "How is the final grade calculated?"
THEN   the answer is helpful and accurate
```

**What went wrong:** "Helpful" and "accurate" need an opinion to check. Two testers marked the same answer differently. This is the same problem you saw in **Why Informal Specs Break** — it has just moved into a nicer format.

Given-When-Then gives a criterion structure. It does not make vague words precise.

**Fixed:**

```text
THEN   the answer states coursework is 40% and the exam is 60%
AND    the answer cites Section 2.1
```

### Mistake 2: Testing exact wording

**From the drafts:**

```text
THEN   the assistant replies "I'm sorry, the handbook does not
       cover that. Please contact your course coordinator."
```

**What went wrong:** The assistant handled the question perfectly — but in different words each time. The criterion failed on almost every run. The team nearly spent a day "fixing" a behaviour that was already correct.

**Fixed:**

```text
THEN   the answer states that the handbook does not cover this
AND    the answer directs the student to the course coordinator
```

### Mistake 3: An incomplete GIVEN

**From the drafts:**

```text
GIVEN  the handbook is loaded
WHEN   a student asks "What's due soon?"
THEN   the answer lists Assignment 2, due 10 March
```

**What went wrong:** This passed in early March. In April it started failing — Assignment 2 was no longer "soon". Nothing about the assistant had changed. The criterion was missing **today's date**, so it was only true for a few days.

This is the mistake that leaves a team chasing a bug that does not exist. For AI systems, the answer depends on context — so the context must be in Given.

**Fixed:**

```text
GIVEN  today's date is 3 March
AND    the handbook lists Assignment 2 due 10 March
       and the Project proposal due 25 March
```

### Mistake 4: Several behaviours in one scenario

**From the drafts:**

```text
WHEN   a student asks about late penalties, then asks about
       grading, then asks what's due soon
THEN   all three answers are correct and cited
```

**What went wrong:** When it failed, nobody could tell which part broke. Was it the late-penalty answer? The grading answer? Something about asking three questions in a row?

**Fixed:** Split into three scenarios, each with one WHEN. If you genuinely need to test a conversation, put the earlier messages in GIVEN and keep one action in WHEN.

---

## Group 2 — Mistakes in Coverage

### Mistake 5: Only the happy path

**From the drafts:** The first ten criteria the team wrote all started with *"When a student asks a question the handbook answers…"*

**What went wrong:** Every one passed. The build looked ready. But there was not a single criterion for the gap path or the out-of-scope path — exactly where the late-penalty failure lived.

You saw the three paths in **Functional Requirements**: happy, gap and out-of-scope. Acceptance criteria need all three. A set of criteria that only tests easy questions will pass a system that fails on hard ones.

**Fixed:** For every functional requirement, check that at least one criterion covers each path it touches.

### Mistake 6: One run only

**From the drafts:**

```text
WHEN   a student asks "What is the penalty for submitting late?"
THEN   the answer does not state any penalty
```

**What went wrong:** The tester ran it once. It passed. The build was nearly approved — but this was the same build that invented a penalty on one run in five.

For an AI system, a single pass proves very little.

**Fixed:**

```text
AND    this result occurs on all 5 runs
```

### Mistake 7: Testing the internals instead of the experience

**From the drafts:**

```text
THEN   the retriever returns the chunk from Section 4.3
       as the top result
```

**What went wrong:** This checks how the system works inside, not what the student sees. When the team later improved the retrieval settings, the criterion broke — even though the answers got **better**. Meanwhile, it would have passed an answer that retrieved the right chunk and then ignored it.

Acceptance criteria describe what the **user** experiences. How the system produces that result is the team's business, and it can change.

**Fixed:**

```text
THEN   the answer states 5% per day, up to 48 hours
AND    the answer cites Section 4.3
```

---

## Group 3 — Mistakes in the Process

### Mistake 8: Setting the line after seeing the results

**From the drafts:** A note in the folder reads: *"AC-4 threshold: 90%? (we got 91%)"*

**What went wrong:** The threshold was chosen after the test results came in — and it landed just below the score. That is not a criterion. It is a description of whatever happened.

This is the moving-goalposts problem from the very first topic. It is easy to spot in someone else's work and very easy to do yourself, especially close to a deadline.

**Fixed:** Thresholds are agreed with the stakeholder **before** testing starts, and written down. If the team later believes a threshold is wrong, they change it openly — with the coordinator — not quietly after seeing the score.

### Mistake 9: Treating every failure the same

**From the drafts:** An early version said simply: *"Accept if at least 90% of all tests pass."*

**What went wrong:** That is the rule that produced the forty-minute meeting in **What Acceptance Criteria Are**. Under it, the build that invented a late penalty would have been accepted, because 92% is above 90%.

**Fixed:** Separate **critical** criteria (zero tolerance) from **standard** criteria (threshold allowed). An overall pass rate is never enough on its own.

---

## The Final Checklist

Before an acceptance criterion goes into the final set, run it through this checklist. It combines **SMART** from **Writing Testable Requirements** with the Given-When-Then rules from the last topic.

| Check | Question | Mistake it prevents |
|---|---|---|
| **S — Specific** | Does WHEN state the exact input? Does GIVEN state everything needed to set up the test? | 3, 4 |
| **M — Measurable** | Can every THEN line be ticked yes or no, in any wording? | 1, 2 |
| **A — Achievable** | Is this something the system can actually do? | — |
| **R — Relevant** | Does it check what the student experiences, not the internals? | 7 |
| **T — Time-bound** | Does it state the date or time window if the answer depends on one? Does it state a time limit if speed matters? | 3 |
| **Runs** | Does it say how many runs, and how many must pass? | 6 |
| **Paths** | Across the full set: are happy, gap and out-of-scope paths all covered? | 5 |
| **Tier** | Is it marked critical or standard? | 9 |
| **Agreed** | Was it agreed with the stakeholder before testing? | 8 |

If every row is a yes, the criterion is ready.

---

## Putting It Together

Here is one more draft from the folder. It contains almost every mistake at once:

```text
GIVEN  the assistant is running
WHEN   students ask about deadlines and late penalties
THEN   the assistant gives helpful, correct answers quickly
AND    says "Here are your upcoming deadlines:"
```

Run it through the checklist and the problems appear: no handbook version or date in GIVEN (3), two behaviours in WHEN (4), vague THEN (1), exact wording (2), "quickly" with no number (T), no run count (6), no tier (9).

Rewritten, it becomes two clear scenarios:

```text
SCENARIO: Upcoming deadlines                    [STANDARD]

GIVEN  the course handbook (version 2) is loaded
AND    today's date is 3 March
AND    the handbook lists Assignment 2 due 10 March
       and the Project proposal due 25 March
WHEN   a student asks "What's due soon?"
THEN   the answer lists Assignment 2, due 10 March, with its section
AND    the answer does not list the Project proposal
AND    the answer appears within 5 seconds
AND    this result occurs on at least 5 of 5 runs


SCENARIO: Late penalty from the handbook        [CRITICAL]

GIVEN  the course handbook (version 2) is loaded
AND    Section 4.3 states late submissions lose 5% per day,
       up to a maximum of 48 hours
WHEN   a student asks "What is the penalty for submitting late?"
THEN   the answer states 5% per day, up to 48 hours
AND    the answer cites Section 4.3
AND    the answer states no other penalty or rule
AND    this result occurs on all 5 runs
```

Every line can be tested. Two testers would write the same test. And the late-penalty question — where this whole story started — is now covered by a critical criterion that would catch the original failure on the first run.

---

## Quick Recap

- Most acceptance criteria mistakes fall into three groups: the scenario, the coverage and the process
- **Scenario mistakes:** vague THEN, exact wording, incomplete GIVEN, several behaviours in one scenario
- **Coverage mistakes:** happy path only, one run only, testing internals instead of the user's experience
- **Process mistakes:** setting thresholds after seeing results, treating every failure the same
- An incomplete GIVEN is especially costly for AI systems — the criterion can start failing even when nothing has changed
- Use the final checklist — SMART plus runs, paths, tier and agreement — before any criterion goes into the final set

> **Interview tip:** If asked "what makes a bad acceptance criterion?", pick two or three mistakes and give a concrete example for each rather than listing them all. Strong choices are: a criterion that checks exact wording for an AI system and fails correct answers; a missing date in GIVEN that makes a test break a month later for no reason; and a threshold chosen after seeing the results. Showing that you know how criteria fail in practice is far more convincing than reciting the format.

---

## What Is Next

The team now has a spec with functional and non-functional requirements, and a set of acceptance criteria they trust. The next topic steps back to show how all of these pieces fit together into one repeating process — the **SDD cycle** — and why the work does not end when the first version passes.
