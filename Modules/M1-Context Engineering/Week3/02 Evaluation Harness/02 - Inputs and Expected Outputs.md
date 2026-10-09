# Inputs and Expected Outputs

---

A professor writing a standardised test does not pick questions randomly.

They think carefully: what concepts must every student know? What are the common mistakes? What questions reveal whether a student truly understands — not just memorised? What edge cases separate a student who gets it from one who almost gets it?

Building the input set for an eval harness requires the same thinking. The inputs you choose determine what the harness can and cannot detect. A weak input set misses real problems. A strong one catches them before users do.

---

## Building the Input Set

A good input set for a context package has four types of inputs. For a harness of fifteen questions, aim for roughly this distribution:

**Typical inputs (5-6 questions)** — the questions the system will encounter most often. For the study assistant: straightforward concept questions about topics in the covered syllabus.

```
Examples:
- "What is a linked list?"
- "Explain the difference between a stack and a queue."
- "What is a binary search tree?"
```

These test whether the package works for the common case. If the package fails here, nothing else matters.

**Boundary inputs (3-4 questions)** — questions at the edges of what the package is designed to handle. Topics just inside the scope. Unusual phrasings of normal questions. Questions that are technically in scope but push the constraints.

```
Examples:
- "What is a BST and how does insertion work?" (two-part question)
- "Can you give me a very detailed explanation of trees?" (pushes length constraint)
- "What's the diff between stack and queue?" (informal phrasing)
```

These test whether the package handles variation gracefully.

**Out-of-scope inputs (3-4 questions)** — questions outside the defined scope. Topics not yet covered. Topics from a different subject. Requests for things the package explicitly should not do.

```
Examples:
- "Explain recursion." (not yet covered)
- "Help me write my assignment solution." (explicitly excluded)
- "What is a graph?" (not yet covered)
```

These test the Constraint role. The correct response is a clear redirect — not an attempt to answer.

**Adversarial inputs (2-3 questions)** — inputs specifically designed to trigger failure modes. Ambiguous questions. Questions that try to get the model to cross a constraint. Questions that combine in-scope and out-of-scope elements.

```
Examples:
- "Explain how recursion is used in tree traversal." 
  (combines in-scope topic with out-of-scope concept)
- "Give me a complete exam answer for the question on stacks."
  (tries to get a complete answer despite the constraint)
- "What would happen if you used a stack where a queue was needed?"
  (tests reasoning beyond definition)
```

These test robustness. A package that passes typical inputs but fails adversarial ones is fragile.

---

## Defining Expected Outputs

For each input, you need to define what a passing response looks like. Not the exact words — the criteria.

This is done as a checklist per input:

```
Input: "What is a linked list?"

Expected output criteria:
✓ Analogy present (physical object, not a process)
✓ Technical definition present (one to two sentences)
✓ Use case present (one real system)
✓ Response under 120 words
✓ No Big O notation
✓ No recursion mentioned
✓ Structure: analogy first, definition second, use case third
```

For out-of-scope inputs, the expected output looks different:

```
Input: "Explain recursion."

Expected output criteria:
✓ Does NOT explain recursion
✓ States clearly that recursion is not yet covered
✓ Redirects to a covered topic
✓ Tone remains helpful, not dismissive
```

Writing expected outputs before running the harness is important. If you write them after seeing the responses, you will unconsciously calibrate them to match what the model produced — which defeats the purpose.

---

## How Many Inputs Do You Need

For a context package used by a small group — a study assistant for a class of thirty students — fifteen inputs is a reasonable harness. It covers the main cases without taking excessive time to run and score.

For a more complex system used at larger scale, the harness should be larger. But start with fifteen. Run it. Fix what fails. Then expand if needed.

The goal is not an exhaustive test of every possible input. It is a representative test that catches the most likely failure modes before users encounter them.

---

## Quick Recap

- A good input set has four types: typical inputs, boundary inputs, out-of-scope inputs, and adversarial inputs
- Aim for roughly 5-6 typical, 3-4 boundary, 3-4 out-of-scope, 2-3 adversarial — fifteen total for most packages
- Expected outputs are criteria checklists, not exact answers — written before running the harness, not after
- The goal is a representative test that catches the most likely failure modes — not an exhaustive test of every possible input

---

## What Is Next

The next topic covers scoring and running the harness — how to apply the criteria consistently, calculate a pass rate, and use the results to diagnose and fix problems in the context package.
