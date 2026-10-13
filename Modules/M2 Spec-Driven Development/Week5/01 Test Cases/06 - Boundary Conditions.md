# Boundary Conditions

---

A speed limit sign says 60 km/h.

At 59 km/h you are within the limit. At 60 km/h you are exactly at the limit. At 61 km/h you have crossed it. Three inputs. Three different outcomes. The boundary is the most important point to test — because that is where the rule changes.

Boundary condition testing focuses on exactly these points. Not the comfortable middle. Not a clear violation. The exact limit — and the values immediately on either side of it.

---

## What Boundary Conditions Are

A boundary condition is the exact value at which a requirement changes from pass to fail.

Every requirement that has a number, a limit, or a threshold has boundary conditions:

- "Under 120 words" — boundary is at 120 words
- "At least 90% pass rate" — boundary is at 90%
- "Response within 8 seconds" — boundary is at 8 seconds
- "Topics in the covered list" — boundary is the last topic added to the list

Boundary conditions matter because systems fail at boundaries more often than anywhere else. The middle is safe. The boundary is where off-by-one errors live, where rounding differences cause surprises, and where the model's interpretation of "under" versus "at" versus "over" may differ from yours.

---

## The Three Boundary Test Cases

For every boundary, write three test cases:

**Just inside the limit** — the value that should pass, right at the edge.
**Exactly at the limit** — the value that sits precisely on the boundary.
**Just outside the limit** — the value that should fail, right at the edge.

For the 120-word limit:

```
TC-BC1 — Just inside
Input: Question that should produce ~110-word response
Expected: Response ≤ 120 words ✓ PASS

TC-BC2 — Exactly at the limit  
Input: Question that produces exactly 120-word response
Expected: Response = 120 words ✓ PASS (≤ 120 includes 120)

TC-BC3 — Just outside
Input: Question that produces ~125-130 word response
(e.g. a comparison question without the extended limit)
Expected: Response > 120 words ✗ FAIL
```

If TC-BC1 passes and TC-BC3 fails — the boundary is being respected correctly. If TC-BC2 fails when it should pass — the system is treating ≤ 120 as < 120. That is a specification ambiguity worth clarifying.

---

## Boundary Conditions for the Study Assistant

**Word limit boundaries:**

```
TC-BC-WL1
Input: Simple concept question (should produce ~80-100 words)
Expected: Response well within 120-word limit ✓

TC-BC-WL2  
Input: Concept question with examples (should produce ~115-120 words)
Expected: Response right at the limit ✓

TC-BC-WL3
Input: Two-concept comparison without extended limit applied
Expected: Response exceeds 120 words — failure caught ✗
```

**Scope boundary:**

```
TC-BC-SC1
Input: "What is a BST?" 
(BST is the last topic added to the covered list)
Expected: Explained correctly ✓

TC-BC-SC2
Input: "What is a heap?"
(Heaps are the first topic just outside the covered list)
Expected: Redirected — not covered ✓

TC-BC-SC3
Input: "What is the relationship between BSTs and heaps?"
(One in scope, one just outside — the exact boundary)
Expected: Explains BST part, redirects on heap part ✓
```

TC-BC-SC3 is the most revealing boundary test. It straddles the exact line between covered and not-covered. How the system handles it shows whether the boundary is sharp or fuzzy.

---

## Why Boundaries Fail More Than the Middle

Three reasons:

**Specification ambiguity** — "under 120 words" — does that mean less than 120 (so 119 is the max) or at most 120 (so 120 is allowed)? Both are reasonable interpretations of "under." The system may implement one, the test may check for the other.

**Model interpretation** — language models do not count words precisely. A response the model believes is "about 100 words" might be 118 words. A response "kept concise" might be 127 words. The model is estimating, not measuring.

**Gradual drift** — constraints that are respected early in a conversation may drift as the conversation grows longer. The word limit is one of the first things to drift. Testing right at the boundary reveals this faster than testing in the middle.

---

## Quick Recap

- A boundary condition is the exact value at which a requirement changes from pass to fail
- For every boundary, write three test cases: just inside, exactly at, just outside
- Boundaries fail more than midpoints — due to specification ambiguity, model estimation, and gradual drift
- The most revealing boundary test straddles exactly the line between two categories — like a question combining one covered and one not-covered topic

---

## What Is Next

The next topic moves from test cases to failure modes — shifting from "how do we test the system?" to "what are the ways the system can fail?" and how to identify them systematically before users do.
