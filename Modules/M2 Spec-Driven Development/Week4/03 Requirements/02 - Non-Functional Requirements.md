# Non-Functional Requirements

---

Two restaurants serve the same dish — same recipe, same ingredients, same portion size.

One takes forty-five minutes to bring it. The other brings it in ten. One serves it in a clean, well-lit room. The other is noisy and poorly maintained. One has staff who explain what is in the dish and check back to see if everything is okay. The other disappears after taking your order.

The dish — the functional requirement — is identical. The experience — everything around the dish — is completely different.

Non-functional requirements are everything around the dish. Not what the system does, but how well it does it, how reliably, how quickly, and under what conditions.

---

## What Non-Functional Requirements Are

Non-functional requirements describe the quality characteristics of a system — the standards it must meet in how it operates, not just in what it produces.

For an AI system, non-functional requirements answer questions like:
- How fast must responses arrive?
- How consistent must the behaviour be across different users and sessions?
- How reliable must the system be — what is an acceptable failure rate?
- What are the resource or cost constraints?
- What security or privacy standards apply?

---

## Common Non-Functional Requirement Categories

**Performance** — how fast the system must respond.

*"The system must produce a response within 5 seconds of receiving a student question under normal network conditions."*

**Reliability** — how often the system must work correctly.

*"The system must produce a rubric-compliant response for at least 90% of questions about covered topics across any session of up to 30 exchanges."*

**Consistency** — how similar responses must be across different users and different sessions.

*"Two students asking the same question in separate sessions should receive responses with the same structure and within 20 words of each other in length."*

**Scalability** — how the system behaves as load increases.

*"The system must maintain its response quality when used simultaneously by up to 30 students."*

**Cost constraints** — what the system is allowed to spend per interaction.

*"The average cost per student session must not exceed $0.05 in API usage."*

**Privacy and security** — what data the system can and cannot retain.

*"The system must not retain personally identifiable student information beyond the current session."*

---

## Why Both Types Are Necessary

Functional requirements alone are not enough to specify a system completely.

A system that produces the correct output in 45 seconds is functionally correct and practically unusable if students expect an immediate response.

A system that works perfectly for one user but behaves inconsistently for others is functionally correct per test and unreliable in practice.

A system that produces excellent responses but costs $2 per session is functionally correct and economically impossible to run at scale.

Non-functional requirements are what separate a system that works in a demo from one that works in production.

---

## Non-Functional Requirements for the Study Assistant

```
NFR1 — Performance:
The system must produce a response within 8 seconds of receiving 
a student question.

NFR2 — Reliability:
The system must produce a rubric-compliant response (all three 
elements present, under 120 words, no constraint violations) 
for at least 90% of questions about covered topics.

NFR3 — Consistency:
The system must follow the analogy-definition-use case structure 
in every response, regardless of how the question is phrased.

NFR4 — Session length:
The system must maintain response quality (rubric compliance and 
constraint adherence) across sessions of up to 25 exchanges 
without compaction.

NFR5 — Cost:
The average API cost per student session must not exceed $0.10.

NFR6 — Privacy:
The system must not store or log student questions or responses 
beyond the current session.
```

---

## Writing Non-Functional Requirements Well

The same rules apply as for functional requirements — be specific and testable.

**Weak NFR:** The system should be fast.
**Strong NFR:** The system must produce a response within 8 seconds.

**Weak NFR:** The system should be consistent.
**Strong NFR:** The system must produce rubric-compliant responses for at least 90% of covered-topic questions across any 15-input eval harness run.

**Weak NFR:** The system should not be too expensive.
**Strong NFR:** Average API cost per session must not exceed $0.10.

Vague non-functional requirements are just as useless as vague functional ones. "Fast", "consistent", and "affordable" mean different things to different people. The number is what makes it testable.

---

## Quick Recap

- Non-functional requirements describe how well the system does what the functional requirements define — performance, reliability, consistency, cost, privacy
- Both types are necessary — functional correctness alone does not make a system usable in practice
- Write non-functional requirements with specific, testable numbers — "within 8 seconds" not "fast", "90% pass rate" not "reliable"
- Non-functional requirements separate a system that works in a demo from one that works in production

---

## What Is Next

The next topic covers writing testable requirements — a practical guide to taking any requirement, functional or non-functional, and making sure it can actually be verified before you build and after you build.
