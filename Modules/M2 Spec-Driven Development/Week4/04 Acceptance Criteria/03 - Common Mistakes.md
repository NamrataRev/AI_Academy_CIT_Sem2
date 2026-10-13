# Common Mistakes in Acceptance Criteria

---

A student spends two hours writing acceptance criteria for their system. They feel good about it. They run the eval harness. Every criterion passes. They deploy the system. Three days later, a user finds a problem that the harness completely missed.

The criteria were not wrong. They were incomplete. The harness tested exactly what was written — and what was written did not cover the scenario that failed in practice.

This is the most common mistake with acceptance criteria. Not writing bad criteria — writing criteria that look complete but are not. This topic covers the patterns that cause this, so you can catch them before they cause problems.

---

## Mistake 1 — Testing the Happy Path Only

The happy path is the scenario where everything goes as expected. The student asks a clear question about a covered topic. The system produces a correct response. The criterion passes.

But users do not only take the happy path. They ask ambiguous questions. They rephrase things in unexpected ways. They ask two questions in one sentence. They ask about topics that are on the boundary of covered and not-covered.

**What it looks like:**

```
AC2.1
Given: The context package is loaded
When: A student asks "What is a stack?"
Then: The response contains an analogy, definition, and use case
```

This tests one specific phrasing of one question. It says nothing about what happens when the student asks "Can u explain stacks?" or "I don't get stacks, help" or "What's the difference between a stack in programming and a stack of books?"

**The fix:**

Write criteria for at least three phrasings of the same question. Write criteria for informal language. Write criteria for partial or ambiguous questions. The happy path criterion stays — but it is not enough on its own.

---

## Mistake 2 — Criteria That Require Judgment

A criterion that requires someone to decide whether it passed is not a criterion — it is an opinion.

**What it looks like:**

```
AC: The analogy should be easy to understand for a second-year student
AC: The response should have a friendly and encouraging tone
AC: The explanation should be appropriately detailed
```

Who decides if the analogy is easy to understand? What does "friendly and encouraging" look like in practice? What is appropriate detail?

These sound like quality criteria. They are not testable. Two people evaluating the same response against these criteria will reach different conclusions.

**The fix:**

Either make the criterion specific enough to be objective — "the analogy uses a physical object, not a technical concept" is testable — or accept that some qualities require human review and mark them explicitly as qualitative review criteria, separate from the binary pass/fail criteria.

---

## Mistake 3 — One Criterion Covering Multiple Things

When a criterion tests two things at once, a partial failure becomes invisible.

**What it looks like:**

```
AC: The response contains an analogy and a definition and a use case 
    and is under 120 words and contains no Big O notation
```

If this response contains an analogy, a definition, and a use case but is 135 words — does it pass or fail? The response satisfied four of the five conditions. But the criterion is written as one pass/fail statement. The length failure is hidden.

**The fix:**

One criterion, one thing. Split:

```
AC2.1: The response contains an analogy
AC2.2: The response contains a definition
AC2.3: The response contains a use case
AC2.4: The response is 120 words or fewer
AC2.5: The response contains no Big O notation
```

Now each failure is visible and diagnosable independently.

---

## Mistake 4 — Missing the Negative Cases

Positive criteria check that the right things appear. Negative criteria check that the wrong things do not appear.

Most people write positive criteria and forget the negative ones.

**What is missed:**

```
FR6: No response contains recursion examples.
```

A positive criterion for this would be: "The response contains only analogies from the covered syllabus." But that does not explicitly test for recursion.

The negative criterion is: "The response does not contain the word 'recursion' or any explanation of recursive behaviour."

Negative criteria are often more important than positive ones for constraint requirements. The constraint says what must not happen — the criterion must explicitly test that it does not.

**The fix:**

For every constraint requirement, write at least one explicit negative criterion. Check that the prohibited thing is absent, not just that the permitted things are present.

---

## Mistake 5 — Not Testing the Edge Cases

Edge cases are the inputs that sit on the boundary of what the system is designed to handle. They are where most real-world failures occur — and they are the inputs most commonly missing from acceptance criteria.

**What is missed:**

A student asks: *"I know recursion is coming later, but can you just give me a quick overview?"*

This is an edge case — an out-of-scope request framed as a polite, reasonable question. A criterion that says "when a student asks about recursion, the system redirects" does not cover this scenario. The phrasing is different. The constraint pressure is different. The criterion passes in testing and fails in production.

**The fix:**

For every out-of-scope constraint, write at least two adversarial phrasings. One direct: "Explain recursion." One indirect: "I know it's not covered yet, but can you just give me a quick sense of recursion?" Both should redirect. Both need explicit criteria.

---

## A Checklist Before Finalising Criteria

Before marking acceptance criteria as complete, run through this checklist:

```
□ Have I tested the happy path?
□ Have I tested at least two alternative phrasings of each input?
□ Are all criteria binary — clear pass or fail with no judgment?
□ Is each criterion testing exactly one thing?
□ Have I written negative criteria for every constraint requirement?
□ Have I written at least two adversarial phrasings for out-of-scope constraints?
□ Have I written criteria for informal or unexpected phrasings?
□ Can someone else run these criteria without asking me any questions?
```

If any box is unchecked — the criteria are not finished yet.

---

## Quick Recap

- Five common mistakes: testing the happy path only, criteria that require judgment, one criterion covering multiple things, missing negative cases, not testing edge cases
- Happy path criteria are necessary but not sufficient — write criteria for alternative phrasings, informal language, and adversarial inputs
- One criterion, one thing — compound criteria hide partial failures
- For every constraint, write an explicit negative criterion that checks the prohibited thing is absent
- Use the checklist before finalising — if any box is unchecked, the criteria are incomplete

---

## What Is Next

The next topic introduces the SDD cycle — how definition, requirements, acceptance criteria, testing, building, and evaluation fit together as one continuous process rather than separate steps done once and forgotten.
