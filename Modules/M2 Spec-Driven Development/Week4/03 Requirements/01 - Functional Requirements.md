# Functional Requirements

---

When you order food at a restaurant, you do not say "bring me something good."

You say: "I want a margherita pizza, medium size, with extra cheese, no olives." The waiter writes it down. The kitchen makes exactly that. When it arrives, you can check immediately whether it is what you ordered.

That order is a functional requirement. It describes precisely what the system should do — specific enough that there is no ambiguity about whether it was done correctly.

A functional requirement defines what a system does. Not how it does it. Not how well it does it. Just what it does — precisely enough to verify.

---

## What Functional Requirements Are

Functional requirements describe the specific behaviours, actions, and outputs a system must produce.

For an AI system, functional requirements answer questions like:
- What does the system do when a user sends a message?
- What does it produce as output?
- What does it do when an input is out of scope?
- What format does the output take?

Each functional requirement describes one specific behaviour. It can be tested. It either happens or it does not.

---

## The Difference Between Functional and Non-Functional

This distinction matters and is easy to confuse.

**Functional:** what the system does.
**Non-functional:** how well it does it.

| Functional | Non-Functional |
|---|---|
| The system produces a response to every student question | The system responds within 3 seconds |
| The system redirects out-of-scope questions | The redirect is clear and not dismissive |
| The system includes an analogy in every response | The analogy uses a physical object, not a process |
| The system stays under 120 words | — |

Notice the last row. "Stays under 120 words" is functional — it either does or it does not. Word count is measurable. "The analogy uses a physical object" is also functional — it either uses one or it does not.

Non-functional requirements are covered in the next topic. For now, focus on functional — what the system does.

---

## Writing a Functional Requirement

A well-written functional requirement has three properties:

**It is specific** — no vague words like "appropriate", "helpful", or "good". Every word should be precise enough that two people reading it would build the same thing.

**It is testable** — you can write a test that definitively passes or fails. If you cannot write the test, the requirement is not specific enough.

**It describes behaviour, not implementation** — it says what the system does, not how it does it. The implementation is the builder's choice. The requirement is the contract.

---

## Examples — Weak vs Strong

**Weak:** The assistant should give helpful responses.
**Why it fails:** "Helpful" cannot be tested. Two people will interpret it differently.

**Strong:** The assistant produces a response to every student question that contains an analogy, a technical definition, and a use case.
**Why it works:** Testable — each element either appears or it does not.

---

**Weak:** The assistant should handle off-topic questions appropriately.
**Why it fails:** "Appropriately" is undefined. What should it actually do?

**Strong:** When a student asks about a topic not listed in the Metadata covered list, the assistant responds with: a statement that the topic is not yet covered, and a suggestion of one covered topic the student could explore instead.
**Why it works:** Specific, testable, describes exact behaviour.

---

**Weak:** The assistant should be consistent.
**Why it fails:** Consistent at what? In what way?

**Strong:** The assistant produces responses that follow the rubric structure (analogy, definition, use case) for every question about a covered topic.
**Why it works:** Defines exactly what consistency means in this context.

---

## Functional Requirements for the Study Assistant

Here is a complete functional requirements list for the BTech DSA study assistant:

```
FR1: The system produces a response to every question about a 
     topic in the covered syllabus.

FR2: Every response contains three elements in this order: 
     an analogy, a technical definition, and a use case.

FR3: When a student asks about a topic not in the covered syllabus, 
     the system states clearly that the topic is not yet covered 
     and redirects to one covered topic.

FR4: Every response is 120 words or fewer.

FR5: No response contains Big O notation.

FR6: No response contains recursion examples.

FR7: The opening message of every session identifies the system 
     as an AI assistant, not a human tutor.

FR8: When asked to compact, the system produces a summary 
     containing: topics covered, what was established, 
     student's current position, and what comes next.
```

Eight requirements. Each one testable. Each one describes a specific behaviour. Together they define what the system does — completely enough to build an evaluation harness against.

---

## Quick Recap

- Functional requirements describe what the system does — specific enough to test, not how it does it
- A functional requirement must be specific, testable, and describe behaviour not implementation
- Weak requirements use vague words like "helpful", "appropriate", "consistent" — strong ones define exactly what should happen
- Write functional requirements before building — if you cannot write them, you do not yet know what you are building

---

## What Is Next

The next topic covers non-functional requirements — how well the system does what the functional requirements define, and why both types are necessary for a complete specification.
