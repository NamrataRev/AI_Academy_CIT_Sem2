# Writing Testable Requirements

---

A driving examiner does not ask: "Are you a good driver?"

They watch you do a three-point turn. They check your mirror checks. They time how long you wait at a stop sign. They are not assessing a vague quality — they are checking specific, observable behaviours against defined criteria.

Every requirement in a specification should work the same way. Not "is this system good?" but "did this specific thing happen or not?" The test either passes or fails. There is no room for interpretation.

This is what testable means. And writing testable requirements is the skill that separates a specification that can be verified from one that can only be argued about.

---

## The Testability Test

Before finalising any requirement, apply one check:

**Can you write a test that produces a clear pass or fail result — without any judgment call?**

If yes — the requirement is testable.
If no — it needs to be made more specific.

Here is the check applied to real requirements:

*"The assistant should give helpful responses."*
Test attempt: Run the assistant and decide if responses are helpful. → Requires judgment. **Not testable.**

*"Every response contains an analogy, a definition, and a use case."*
Test attempt: Check whether each element is present. It either is or it is not. → No judgment needed. **Testable.**

*"The assistant should respond quickly."*
Test attempt: Time the response and decide if it is quick enough. → Requires judgment about what "quick" means. **Not testable.**

*"The assistant produces a response within 8 seconds."*
Test attempt: Time the response. If under 8 seconds — pass. If over — fail. → No judgment needed. **Testable.**

---

## The Four Signals of an Untestable Requirement

**Signal 1 — Subjective adjectives**

Words like: helpful, appropriate, good, clear, simple, engaging, professional, friendly.

These words mean different things to different people. They cannot be objectively verified. Replace them with specific, observable behaviours.

*"Clear explanations"* → *"Explanations that contain an analogy using a physical object familiar to a second-year student"*

**Signal 2 — Comparatives without anchors**

Words like: faster, better, more accurate, more consistent.

Faster than what? Better than what? These are only testable when there is a baseline to compare against.

*"Responses should be more concise"* → *"Responses must be under 120 words"*

**Signal 3 — Frequency words without numbers**

Words like: usually, often, generally, mostly, rarely.

These words suggest tendencies, not requirements. A requirement that is met "usually" is not a requirement — it is a hope.

*"The assistant usually follows the rubric structure"* → *"The assistant follows the rubric structure in at least 9 out of every 10 responses on covered topics"*

**Signal 4 — Compound requirements**

A single requirement that describes two or more distinct things. When the test runs, which thing is being tested?

*"The assistant should give accurate and concise responses."*
This is two requirements bundled together. Split them:
- *"Every response is factually accurate for the concept being explained"*
- *"Every response is under 120 words"*

Now each can be tested independently.

---

## A Practical Process for Writing Testable Requirements

**Step 1 — Write the informal version first**

Start with what you want, in plain language: *"The assistant should not confuse students by covering topics too advanced for them."*

**Step 2 — Identify what is untestable**

"Confuse" — subjective. "Too advanced" — undefined. Neither can be tested.

**Step 3 — Define the observable behaviour**

What would you actually see if this requirement was met? What would you see if it was violated?

Met: responses only use vocabulary introduced in the course up to the current week.
Violated: a response uses Big O notation before Week 6, or explains recursion before it is covered.

**Step 4 — Write the testable version**

*"The assistant does not use Big O notation in any response. The assistant does not explain recursion, graphs, or dynamic programming until those topics appear in the Metadata covered list."*

Now it can be tested. A response either contains Big O notation or it does not.

---

## Applying This to the Study Assistant Specification

Take the functional requirements from the previous topic and run the testability check:

| Requirement | Testable? | If not — fix |
|---|---|---|
| FR1: Produces a response to every covered-topic question | ✅ Yes — it either responds or it does not | — |
| FR2: Every response contains analogy, definition, use case in order | ✅ Yes — each element either present or not | — |
| FR3: Redirects out-of-scope questions | ✅ Yes — redirect either happens or it does not | — |
| FR4: Every response under 120 words | ✅ Yes — word count is measurable | — |
| FR5: No Big O notation | ✅ Yes — notation either appears or it does not | — |
| FR6: No recursion examples | ✅ Yes — recursion either appears or it does not | — |
| FR7: Opening message identifies system as AI | ✅ Yes — statement either present or not | — |
| FR8: Compact summary has four required parts | ✅ Yes — each part either present or not | — |

All eight pass the testability check. This is not an accident — they were written with testability in mind from the start.

---

## Quick Recap

- A testable requirement produces a clear pass or fail without any judgment call
- Four signals of an untestable requirement: subjective adjectives, comparatives without anchors, frequency words without numbers, compound requirements bundled together
- Process: write the informal version → identify what is untestable → define the observable behaviour → write the testable version
- If you cannot write a test for a requirement, the requirement is not finished yet

---

## What Is Next

The next topic introduces acceptance criteria — a specific format for writing requirements that makes them even more precise, and directly usable as test cases in the evaluation harness.
