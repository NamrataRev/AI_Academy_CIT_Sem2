# Identifying Failure Modes

---

Aircraft engineers do not wait for a plane to crash to find out what can go wrong.

Before any aircraft enters service, engineers systematically ask: what could fail? Not just the obvious failures — the engine stops — but everything. What happens if this valve sticks? What happens if this sensor gives a false reading? What happens if two things fail at the same time?

This process is called Failure Mode and Effects Analysis — FMEA. It identifies every way the system can fail before deployment, so the most serious failures can be designed out or guarded against.

You are not building aircraft. But the principle is identical. Identifying failure modes before deployment — not after users find them — is what separates a system that is safe to use from one that is quietly causing problems.

---

## What a Failure Mode Is

A failure mode is a specific way a system can produce an incorrect, incomplete, or harmful output.

Not a general statement like "the system might fail" — a specific, named failure with a specific cause and a specific effect.

For the study assistant, failure modes look like this:

**FM1 — Out-of-scope explanation**
The system explains a topic that is not yet in the covered syllabus.
Cause: constraint not specific enough for certain phrasings.
Effect: student receives explanation of a concept before prerequisites are covered — potential confusion in exam.

**FM2 — Word limit exceeded**
The system produces a response significantly longer than 120 words.
Cause: comparison or multi-part question not covered by the word limit constraint.
Effect: response too long for student's notebook — key information buried in excess text.

**FM3 — Missing rubric element**
The system produces a response without one of the three required elements — analogy, definition, or use case.
Cause: question phrasing triggers a response pattern that does not follow the rubric.
Effect: incomplete explanation — student missing a key component for exam revision.

**FM4 — Silent failure on an unsupported query**
The system cannot produce a meaningful response but presents a confident answer anyway.
Cause: question requires current information the model does not have.
Effect: student studies incorrect or fabricated information.

**FM5 — Constraint drift over long sessions**
The system respects constraints early in a session but violates them later as the context window fills.
Cause: context degradation — constraints receive less attention late in long conversations.
Effect: students using the system for extended sessions receive inconsistent responses.

---

## How to Identify Failure Modes Systematically

Do not wait for failures to appear in testing. Identify them proactively using three approaches:

**Approach 1 — Work through each requirement**

For every functional requirement, ask: what would it look like if this requirement was not met?

FR2: Every response contains an analogy, definition, and use case.
Failure: response missing one or more elements → FM3

FR4: Every response under 120 words.
Failure: response over 120 words → FM2

FR3: Out-of-scope questions redirected.
Failure: out-of-scope question explained instead → FM1

This approach generates one failure mode per requirement — the direct negation of each requirement.

**Approach 2 — Work through each context package role**

For each of the five roles, ask: what goes wrong if this role fails to do its job?

Authority fails → model drifts to a generic identity, produces wrong tone and level.
Exemplar fails → model loses calibration, produces inconsistent format.
Constraint fails → model crosses prohibited boundaries.
Rubric fails → model produces inconsistent structure.
Metadata is stale → model makes assumptions based on outdated context.

This approach generates failure modes rooted in the context package design.

**Approach 3 — Think about the user population**

Who will use this system? What will they do that was not anticipated?

A student under exam pressure asks increasingly desperate questions — emotional framing that puts pressure on constraints.
A student who does not read carefully pastes a question from a different subject entirely.
A student shares the assistant with a friend who is in a different year and asks about different topics.

This approach generates failure modes rooted in actual user behaviour rather than theoretical specification gaps.

---

## Documenting Failure Modes

Each identified failure mode should be documented with four fields:

```
Failure Mode ID: FM1
Name: Out-of-scope explanation
Description: System explains a topic not in the covered syllabus
Cause: Constraint not robust enough for politely-framed or 
       indirectly-phrased out-of-scope requests
Effect: Student receives explanation before prerequisites covered
Detection: Eval harness adversarial test cases
Mitigation: Strengthened constraint with explicit framing instructions
```

This documentation feeds directly into the next topic — severity, likelihood, and detectability — which determines how urgently each failure mode needs to be addressed.

---

## Quick Recap

- A failure mode is a specific way a system produces an incorrect, incomplete, or harmful output — not a general concern, a named failure with a cause and effect
- Identify failure modes proactively using three approaches: work through requirements, work through context package roles, think about the user population
- Each failure mode should be documented with ID, name, description, cause, effect, detection method, and mitigation
- Documented failure modes feed into severity and priority analysis — covered in the next topic

---

## What Is Next

The next topic covers severity, likelihood, and detectability — the three dimensions used to assess how serious each failure mode is, and how to use them to decide which failures to address first.
