# Good vs Bad Examples

---

Reading about quality criteria is one thing. Seeing what passing and failing actually looks like is another.

This topic takes the four criteria from the previous topic — consistency, accuracy, format compliance, edge case handling — and applies them to real context package examples. Two versions of the same study assistant. One that passes. One that fails. The difference between them is specific and diagnosable.

---

## The Setup

Both versions are for the same BTech study assistant. Both are trying to do the same thing. The difference is in how carefully each role was written.

---

## Version 1 — The Weak Package

```
AUTHORITY: You are a helpful study assistant.

EXEMPLAR: [none]

CONSTRAINT: Keep it simple. Be accurate.

RUBRIC: Give clear answers.

METADATA: This is for BTech students studying DSA.
```

Now test it against the four criteria.

---

**Consistency test** — ten questions asked, ranging from simple to complex.

Simple question: *"What is a stack?"*
Response: A reasonable three-paragraph explanation with code examples, Big O notation, and implementation details.

Complex question: *"When would you use a stack instead of a queue?"*
Response: A one-sentence answer with no examples.

The quality varies dramatically between questions. The package is not consistent — the Authority gives no guidance on depth, and the Constraint ("keep it simple") means different things for different questions.

**Verdict: Fails consistency.**

---

**Accuracy test** — response checked against the audience definition.

The response to "what is a stack" included Python implementation code and Big O notation. The Metadata says "BTech students studying DSA" but gives no information about what has and has not been covered. The response assumes a level that may be too advanced for some students and uses notation that may not yet have been introduced.

**Verdict: Fails accuracy** — Metadata is too vague to calibrate responses to the actual audience.

---

**Format compliance test** — structure checked against the Rubric.

The Rubric says "give clear answers." This is not a rubric — it is a hope. It defines no structure, no required elements, no format. Every response has a different structure because nothing specified what structure means.

**Verdict: Fails format compliance** — no measurable rubric exists.

---

**Edge case test** — student asks about recursion, which is not yet covered.

Response: A full explanation of recursion with examples.

The Constraint said "be accurate" — and the explanation was accurate. But nothing told the model to redirect out-of-scope questions. It answered a question it should have flagged.

**Verdict: Fails edge case handling.**

**Overall: Fails all four criteria.** Not because the roles are missing — they are all present. Because they are too vague to do any work.

---

## Version 2 — The Strong Package

```
AUTHORITY: You are a study assistant for second-year BTech CSE 
students preparing for their DSA exam. You explain concepts using 
physical object analogies before technical definitions. You pitch 
explanations at someone who knows Python basics and has covered 
the topics in Metadata.

EXEMPLAR:
Q: What is a stack?
A: Think of a stack like a pile of trays in a cafeteria — you can 
   only add to the top and take from the top. In code: LIFO, 
   last in first out. Used in: browser back button, undo functions, 
   function call tracking.

Q: What is a queue?
A: Think of a queue like people at a ticket counter — first in 
   line is served first. In code: FIFO, first in first out. 
   Used in: print spoolers, message delivery, CPU scheduling.

CONSTRAINT:
- Do not use recursion — covered in a separate module
- Keep responses under 120 words
- Do not use Big O notation
- Do not answer questions outside the covered syllabus — 
  say clearly what is not yet covered and redirect

RUBRIC:
Every response: analogy (one sentence), definition (one to two 
sentences), use case (one sentence). All three must be present.

METADATA:
Course: DSA — Second Year BTech CSE
Covered: Arrays, Linked Lists, Stacks, Queues, Trees, BSTs
Not covered: Graphs, Dynamic Programming, Recursion, Heaps
Exam: 8 days away
```

Now test it against the four criteria.

---

**Consistency test** — ten questions, simple to complex.

Simple: *"What is a stack?"* → analogy, definition, use case, under 120 words.
Complex: *"When would you use a stack instead of a queue?"* → comparison structured as analogy-first, definition of the distinction, use case for each. Under 120 words.

Quality is consistent. The Authority, Exemplar, and Rubric together calibrate depth across question types.

**Verdict: Passes consistency.**

---

**Accuracy test** — response checked against audience.

No Big O notation. No recursion. Analogies use physical objects. Vocabulary matches the level defined. Every response is pitched correctly for the audience defined in Metadata.

**Verdict: Passes accuracy.**

---

**Format compliance test** — structure checked.

Ten responses checked: analogy present in 10/10, definition present in 10/10, use case present in 9/10. One response on a comparison question had two use cases instead of one — minor violation, easy to fix by tightening the Rubric.

**Verdict: Passes format compliance** — with one minor refinement needed.

---

**Edge case test** — student asks about recursion.

Response: *"Recursion is covered in a separate module later in the semester. For now, I can help you with any of the topics already covered: arrays, linked lists, stacks, queues, trees, or BSTs. Which would you like to work on?"*

The Constraint handled it. Clear redirect. No unauthorised explanation.

**Verdict: Passes edge case handling.**

**Overall: Passes all four criteria.**

---

## What the Comparison Shows

The difference between the two versions is not the presence of roles — both have all five. The difference is specificity.

Version 1 has vague roles that sound reasonable but give the model nothing measurable to work with. Version 2 has specific roles that give the model precise guidance — and can be tested against clear criteria.

Vague = unmeasurable = unreliable.
Specific = measurable = reliable.

---

## Quick Recap

- Both packages had all five roles — the difference was specificity, not presence
- Vague roles (helpful assistant, keep it simple, give clear answers) cannot be tested and produce inconsistent results
- Specific roles (physical object analogies, under 120 words, analogy-definition-use case structure) are measurable and produce consistent results
- Testing against the four criteria reveals exactly which role is causing a problem — making diagnosis and fixing straightforward

---

## What Is Next

The next topic introduces the evaluation harness — the systematic process for testing a context package against these four criteria at scale, rather than checking manually one response at a time.
