# Edge Case Tests

---

A bridge is designed to carry a maximum load of ten tonnes.

Engineers do not just test it at five tonnes and declare it safe. They test it at nine tonnes. At nine and a half. They want to know exactly where the boundary is and what happens right at it — because that is where the real risk lives.

The safe middle is easy. The boundary is where things break.

Edge case tests do the same thing for AI systems. They probe the boundaries of what the system is designed to handle — not to find the average behaviour, but to find where reliable behaviour ends.

---

## What an Edge Case Is

An edge case is an input that sits at or near the boundary of what the system was designed to handle.

Not completely outside scope — that is an out-of-scope test. Not a deliberate attack — that is an adversarial test. An edge case is the grey area: inputs that are almost in scope, or at the limit of a constraint, or phrased in a way the system was not explicitly designed for.

For the study assistant:

- A question about a topic that is covered but rarely asked about
- A question that combines two covered topics in a way that strains the word limit
- A question phrased very informally — abbreviations, incomplete sentences, slang
- A question about a topic at the boundary between covered and not-covered

None of these are attacks. They are the natural variation of how real students actually ask questions.

---

## Four Types of Edge Cases

**Type 1 — Boundary topics**

Topics that sit right at the edge of the Metadata. Just inside the covered list. Just outside it. Questions that reference both sides at once.

```
TC-EC1
Input: "How do you traverse a binary search tree?"
(BST is covered. Traversal is covered. But traversal is often 
taught recursively — and recursion is not covered.)
Expected: Response explains traversal using an iterative approach
Expected: Does not say recursion is not covered — 
          traversal IS in scope, just the recursive method is not
```

This is one of the hardest edge cases for the study assistant. The topic is in scope. The constraint still applies. The system must navigate both simultaneously.

**Type 2 — Informal phrasing**

Real students do not always write polished, grammatically correct questions — especially when revising late at night under pressure.

```
TC-EC2
Input: "what's a stack again"
Expected: Same rubric compliance as a formal question

TC-EC3
Input: "i dont get queues"
Expected: The system asks a clarifying question or explains 
          the concept — not a redirect or an error

TC-EC4
Input: "bst vs linked list??"
Expected: Response covers both, meets word limit for comparisons
```

If the system only works for well-phrased questions, it will fail many real users.

**Type 3 — Multi-part questions**

A student asking two things at once — or a question that requires covering multiple concepts to answer properly.

```
TC-EC5
Input: "What is a BST and why would I use it instead of a linked list?"
Expected: Response covers both BST and the comparison
Expected: Word count within the comparison limit (≤ 180 words)
Expected: Rubric structure maintained for both parts
```

The system was specified for single-concept questions. Multi-part questions test whether the specification was complete or whether it left a gap.

**Type 4 — Constraint limits**

Inputs that push right up against the boundaries set by constraints.

```
TC-EC6
Input: "Explain stacks, queues, trees, and how they differ"
(Four concepts — well beyond a standard comparison question)
Expected: System either handles it within an extended limit 
          or clearly states it will cover them one at a time
Expected: Does not produce a 400-word response with no structure
```

This tests what happens when the input strain exceeds what the constraints anticipated.

---

## What Edge Cases Reveal

Happy path tests reveal whether the system works in ideal conditions. Edge cases reveal whether the specification was complete.

When an edge case fails, it usually means one of two things:

**The specification had a gap** — the requirement covered the obvious cases but not the boundary. The fix is a specification update — add a requirement or acceptance criterion that covers the boundary case.

**The implementation was too brittle** — the context package was calibrated to specific phrasings but could not generalise. The fix is an implementation update — typically strengthening the Authority or adding exemplars that cover informal phrasings.

Either way, an edge case failure gives you specific, actionable information. It is not a vague "the system did not work well" — it is "this specific type of input at this specific boundary produced this specific problem."

---

## How Many Edge Case Tests

For a fifteen-input harness:
- 4 edge case tests is a reasonable number — one boundary topic, one informal phrasing, one multi-part question, one constraint limit test

For a more thorough harness:
- 6-8 edge case tests, covering all four types with at least one example each

Edge cases should make up the second largest category in the harness after happy path tests — because this is where specification gaps and implementation brittleness are most commonly found.

---

## Quick Recap

- Edge cases sit at the boundary of what the system was designed to handle — not attacks, but natural variation at the limits
- Four types: boundary topics, informal phrasing, multi-part questions, constraint limits
- Edge case failures reveal specification gaps or implementation brittleness — both are specific and fixable
- Aim for 4-8 edge case tests in the harness — the second largest category after happy path tests

---

## What Is Next

The next topic covers adversarial tests — inputs deliberately designed to make the system fail, and why testing against these before deployment is essential.
