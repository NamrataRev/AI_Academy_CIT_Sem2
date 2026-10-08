# Rubric Role

---

Every assignment you have ever submitted was evaluated against a rubric.

Sometimes it was explicit — ten marks for correctness, five for clarity, five for examples. Sometimes it was implicit — the professor just knew what a good answer looked like. But in both cases, there was a standard. A definition of what done well looked like.

When the rubric was clear, you knew exactly what to aim for. When it was vague, you guessed — and sometimes guessed wrong. You submitted something you thought was excellent and got feedback saying the structure was wrong, or the depth was off, or you included things that were not asked for.

The model faces the same problem. Without a rubric, it guesses what a complete, well-formed response looks like. Sometimes it guesses right. Often it does not — not because it lacks capability, but because nobody told it what the finished product should look like.

---

## What the Rubric Role Is

The Rubric role tells the model what a good response looks like when it is done.

Not what to include — that is Authority and Exemplar. Not what to avoid — that is Constraint. The Rubric defines the shape, structure, and criteria of the finished response.

It answers the question the model is always implicitly asking: *"How do I know when this response is complete and good?"*

---

## Rubric vs Constraint — The Difference

This distinction matters because people often confuse the two.

A **Constraint** says: *"Do not exceed 120 words."*
A **Rubric** says: *"Each response should have exactly three parts — analogy, definition, use case — each one sentence."*

The constraint sets a limit. The rubric defines the shape. Both are necessary. A response can stay within the word limit and still be poorly structured. A response can follow the structure perfectly and still be too long.

They work together — the rubric defines what to build, the constraint sets the boundaries within which to build it.

---

## What a Rubric Covers

**Structure** — what parts should a response have, and in what order?

*"Every explanation should follow this structure: analogy first, then technical definition, then one real-world use case."*

**Format** — how should the response be presented?

*"Use plain prose — no bullet points, no headers, no numbered lists."*
Or: *"Use a two-column format: term on the left, explanation on the right."*

**Completeness criteria** — what must be present for the response to be considered complete?

*"A response is complete when it has an analogy, a definition, and at least one use case. A response without all three is incomplete."*

**Quality criteria** — what makes one response better than another?

*"The analogy should be something a student encounters in daily life — not a technical or domain-specific comparison."*
*"The definition should be precise enough to use verbatim in an exam answer."*

---

## The Rubric for the BTech Study Assistant

```
RUBRIC:
Every response must follow this structure:
1. Analogy — one sentence using something from everyday student life
2. Technical definition — one to two sentences, precise enough for exam use
3. Use case — one sentence describing where this is used in real systems

A response is complete only when all three parts are present.
The analogy must not use technical computing concepts as the comparison.
The definition must be accurate enough that a student could write it 
in an exam and receive full marks.
```

With this rubric, the model knows exactly what done looks like. It does not have to guess whether to add more. It does not have to decide whether to include a use case. The rubric answered all of those questions before the question was even asked.

---

## What Happens Without a Rubric

Without a rubric, the model decides for itself what a complete response looks like.

Sometimes it produces three sentences. Sometimes fifteen. Sometimes it uses bullet points, sometimes prose, sometimes headers. Sometimes it includes examples, sometimes not. The format varies because nothing defined what the format should be.

This inconsistency is a problem — not just aesthetically, but practically. If the output of an AI system is going to be used downstream — fed into another system, displayed to a user, stored in a database — inconsistent format means every response needs to be manually checked and reformatted before use.

A well-written rubric eliminates this. Every response comes out in the same shape. Every time.

---

## Quick Recap

- The Rubric role defines what a good, complete response looks like — its structure, format, and quality criteria
- It is different from Constraint — constraint sets limits, rubric defines the shape
- A rubric answers the model's implicit question: "how do I know when this response is done and good?"
- Without a rubric, the model decides format and completeness for itself — producing inconsistent output that may need reformatting before use

---

## What Is Next

The next topic covers the final role — Metadata. This is the situational background the model needs to make good decisions — the facts about the context that no other role provides.
