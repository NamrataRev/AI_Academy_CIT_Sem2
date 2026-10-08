# Constraint Role

---

Every exam has rules.

No calculators. No notes. Answer in the space provided. Maximum 200 words per answer. These rules do not tell you what to write — they tell you what not to do and what the boundaries are. A student who ignores them might write a brilliant answer that still gets zero marks because it violated the format.

Constraints define the space inside which good work happens. Without them, every student would interpret the exam differently. The playing field would be uneven and the responses incomparable.

A context package works the same way. The Authority role tells the model who it is. The Exemplar shows it what good looks like. But without Constraints — the model fills the response space freely, producing something that may be excellent in a vacuum but completely wrong for your specific situation.

---

## What the Constraint Role Is

The Constraint role tells the model what not to do.

Not what to include — what to avoid. The boundaries. The limits. The things that would make a response technically correct but practically wrong for this audience, this context, this purpose.

Constraints are the guardrails that keep the model inside the space where its responses are actually useful.

---

## Why Constraints Are As Important As Instructions

Most people focus on telling the model what to do. They write detailed instructions about format, tone, and content. But they forget to tell the model what not to do.

The result: the model produces something that follows all the instructions — and then adds three paragraphs of additional context nobody asked for. Or uses a technical term that was explicitly outside the scope of the course. Or gives an example from a domain completely unrelated to the student's situation.

None of this violates the instructions. But all of it makes the response less useful.

Constraints close the gaps that instructions leave open.

---

## Types of Constraints

**Topic constraints** — what subjects or areas to avoid.

*"Do not cover recursion — that topic is in a separate module."*
*"Do not reference sorting algorithms — students have not covered them yet."*

**Vocabulary constraints** — what words or terminology to avoid.

*"Do not use Big O notation — students encounter this in Week 6."*
*"Avoid mathematical proofs — this is a conceptual introduction, not a formal course."*

**Length constraints** — how much to say.

*"Keep each explanation under 120 words."*
*"Do not produce more than three examples per response."*

**Assumption constraints** — what not to assume about the reader.

*"Do not assume the student has seen Java — the course uses Python only."*
*"Do not assume prior knowledge of databases."*

**Action constraints** — what the model should not do.

*"Do not provide complete assignment solutions — give hints and direction only."*
*"Do not answer questions outside the scope of Data Structures and Algorithms."*

---

## Constraints for the BTech Study Assistant

Here is what the constraint section of the study assistant context package looks like:

```
CONSTRAINTS:
- Do not use recursion examples — covered in a separate module
- Do not exceed 120 words per explanation
- Do not use Big O notation — students encounter this in Week 6
- Do not assume knowledge of Java — all examples should use Python or be code-free
- Do not provide complete exam answers — explain concepts, not solutions
- Do not cover graphs or dynamic programming — not yet in the syllabus
- If a student asks about a topic outside the covered syllabus, say so clearly 
  and redirect to what has been covered
```

Each constraint closes a specific gap. Without it, the model would eventually cross that line — not out of error, but because nothing told it not to.

---

## How to Write Good Constraints

**Be specific** — "keep it short" is not a constraint. "Keep each response under 120 words" is.

**Explain the reason when it helps** — *"Do not use recursion examples — that topic is in a separate module"* is more effective than just *"Do not use recursion."* The model understands the intent and applies the spirit of the constraint, not just the letter.

**Test your constraints** — after writing them, ask questions that should trigger each constraint. If the model still crosses the line, the constraint needs to be more specific.

---

## What Happens Without Constraints

Without constraints, the model operates with no guardrails. It produces the most statistically useful response for the average user asking that question — which is rarely the most useful response for your specific user in your specific context.

A study assistant without constraints will explain recursion when asked about stacks. It will use Big O notation before the student has encountered it. It will give complete assignment answers when the student just needed a nudge. It will produce 400-word responses when 100 words was what the student needed before their next class.

Every one of these is a failure. Every one is preventable with a well-written constraint.

---

## Quick Recap

- The Constraint role tells the model what not to do — the boundaries that keep responses inside the space where they are actually useful
- Constraints close the gaps that instructions leave open — the model follows your instructions and then does whatever else seems reasonable, unless you constrain it
- Types of constraints: topic, vocabulary, length, assumption, action
- Be specific, explain the reason where it helps, and test each constraint with a question that should trigger it

---

## What Is Next

The next topic covers the Rubric role — how to tell the model what a finished response should look like, and why defining the shape of the output is different from constraining what goes into it.
