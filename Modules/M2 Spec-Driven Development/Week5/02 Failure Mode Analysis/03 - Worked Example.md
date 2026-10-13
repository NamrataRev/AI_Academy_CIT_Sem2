# Failure Mode Analysis — Worked Example

---

The previous two topics covered how to identify failure modes and how to score them. This topic shows a complete failure mode analysis document — the full output of applying both steps to the BTech DSA study assistant.

Read it once as a complete document. Then read it again noticing how each field connects to the previous topics — identification, scoring, and the decisions that follow from the scores.

This is the model for the failure mode analysis you submit with your own systems.

---

## Complete Failure Mode Analysis — BTech DSA Study Assistant

**System:** BTech DSA Study Assistant v1.2
**Analysis date:** Week 5, Semester 2
**Analyst:** [Student Name]

---

### FM1 — Out-of-Scope Explanation

**Description:**
The system explains a topic that is not listed in the Metadata covered list — such as recursion, graphs, or dynamic programming — instead of redirecting to a covered topic.

**Cause:**
The constraint "redirect out-of-scope topics" is not specific enough to hold against all phrasings. Politely-framed requests ("I know it's not covered, but just a quick hint"), indirect references ("my professor mentioned recursion today"), and scope-blended questions ("how does recursion apply to BST traversal?") can bypass the constraint.

**Effect:**
The student receives an explanation of a concept before the prerequisites for that concept have been covered. In the best case, this causes confusion. In the worst case, the student studies an incomplete or context-free explanation and applies it incorrectly in the exam.

**Severity:** 2 — Moderate
Incorrect explanation received, but student has lectures, textbooks, and the lecturer as alternative sources. Effect is real but recoverable.

**Likelihood:** 2 — Occasional
Politely-framed and indirectly-referenced out-of-scope requests are a natural part of how students ask questions, especially under exam pressure. This will happen regularly.

**Detectability:** 3 — Hard to detect
The explanation looks correct. The student has no reason to doubt it unless they specifically know the topic should not be covered yet. Most students will not know this.

**Risk Score:** 2 × 2 × 3 = **12**

**Mitigation:**
Strengthen the constraint with explicit instructions for known framing types:
```
"If a student asks about a topic not in the covered list — 
even politely, even framing it as 'just a hint', even if 
their professor mentioned it — do not explain it. 
Redirect with: 'That topic comes later. I can help you 
with [covered topic] instead.'"
```

**Status:** Fix before deployment. Highest risk score.

---

### FM2 — Word Limit Exceeded

**Description:**
The system produces a response that exceeds the 120-word limit specified in the constraint.

**Cause:**
The 120-word constraint is appropriate for single-concept responses but insufficient for comparison questions or multi-part questions. The system does not distinguish between response types when applying the limit.

**Effect:**
The response is longer than the student's notebook format allows. Key information is present but buried in excess text. The student must manually identify the relevant parts.

**Severity:** 1 — Minor
All required information is present. The student is inconvenienced, not misled. They can still get what they need.

**Likelihood:** 2 — Occasional
Comparison questions are common in DSA revision — stacks vs queues, arrays vs linked lists, BST search vs linear search. These will regularly push against the 120-word limit.

**Detectability:** 1 — Easily detected
The response is visibly long. The student immediately notices it does not fit the expected format.

**Risk Score:** 1 × 2 × 1 = **2**

**Mitigation:**
Update FR4 and the constraint to distinguish response types:
- Single-concept responses: ≤ 120 words
- Comparison responses (two or more concepts): ≤ 180 words

**Status:** Fix in current revision cycle. Low risk score but simple fix — no reason to leave it unfixed.

---

### FM3 — Missing Rubric Element

**Description:**
The system produces a response that is missing one of the three required elements: analogy, technical definition, or use case.

**Cause:**
Certain question phrasings trigger response patterns that do not follow the rubric. Questions phrased as "why" rather than "what" tend to produce explanatory responses without a structured analogy. Very short one-word questions ("BST?") sometimes produce minimal responses that omit the use case.

**Effect:**
The student's revision note is incomplete. They have two of the three components needed for a complete understanding. They may not notice the missing element until they review their notes before the exam.

**Severity:** 2 — Moderate
One missing component leaves a gap in understanding. The student can ask again, but may not realise they need to.

**Likelihood:** 1 — Rare
The exemplars and rubric instruction together make this unlikely for well-phrased questions. Occurs mainly with unusual phrasings.

**Detectability:** 2 — Sometimes detected
A student who knows what to look for (analogy, definition, use case) will notice. A student who does not know the rubric may not.

**Risk Score:** 2 × 1 × 2 = **4**

**Mitigation:**
Add test cases for "why" phrasings and minimal question forms. Add to the Rubric: "Even for questions phrased as 'why' or 'when', structure the response as analogy, definition, use case."

**Status:** Monitor. Add test cases. Fix in next revision cycle if test cases reveal failures.

---

### FM4 — Silent Failure — Fabricated Answer

**Description:**
The system cannot produce a meaningful, grounded answer to a question — but presents a confident, well-formatted response anyway, drawn from training data rather than from verified sources.

**Cause:**
The model fills gaps with plausible-sounding content from training data when it cannot produce a verified answer. This is the silent failure pattern covered in Week 1. For this system specifically: questions about very recent changes to the DSA syllabus, or questions about concepts the model misremembers from training.

**Effect:**
The student studies incorrect information presented as correct. They have no signal that anything went wrong. The fabricated answer looks identical to a correct one.

**Severity:** 3 — Severe
The student studies wrong information with full confidence in its correctness. No alternative signal prompts them to verify. Exam performance is directly affected.

**Likelihood:** 1 — Rare
The study assistant operates within a narrow, well-established domain — classical DSA concepts that are stable and well-represented in training data. Fabrication is unlikely for standard questions.

**Detectability:** 3 — Hard to detect
Output looks identical to a correct response. Student has no reason to verify unless they have independent knowledge of the concept.

**Risk Score:** 3 × 1 × 3 = **9**

**Mitigation:**
Add explicit instruction to the context package:
```
"If you are uncertain about any aspect of your response, 
say so clearly. Do not present uncertain information 
as definitive fact. For any concept you are not fully 
confident about, add: 'Verify this with your course 
materials or lecturer.'"
```
Add to the opening disclosure: "Verify any response you are uncertain about with your course materials."

**Status:** Fix before deployment. Severity 3 and detectability 3 together are too dangerous to leave unaddressed, even at low likelihood.

---

### FM5 — Constraint Drift Over Long Sessions

**Description:**
The system respects constraints correctly early in a session but begins violating them as the session grows longer — responses exceed the word limit, the rubric structure becomes inconsistent, and out-of-scope constraints weaken.

**Cause:**
Context degradation. As the conversation grows, the context package moves further from the current message. The constraints receive less attention. This is the degradation pattern covered in Week 2.

**Effect:**
Students who use the system for extended revision sessions — the students most likely to rely on it heavily — receive progressively inconsistent responses. The system that works well for the first twenty minutes may not work as well for the hour-long session before the exam.

**Severity:** 2 — Moderate
Responses become inconsistent. Not fabricated — just less reliably structured and constrained.

**Likelihood:** 2 — Occasional
Sessions that run long without compaction will experience this. Students revising the night before an exam are exactly this type of user.

**Detectability:** 2 — Sometimes detected
Drift is gradual. A student may notice responses are getting longer or less structured, but may not identify the cause. The four detection signals from Week 2 (length changes, structure changes, constraint violations, tone drift) apply here.

**Risk Score:** 2 × 2 × 2 = **8**

**Mitigation:**
Add compaction instruction to the context package. Advise students to start a fresh session for each new topic block. Add a detection trigger: after every ten exchanges, review three responses for rubric compliance.

**Status:** Address before deployment. Compaction instruction is low effort and directly prevents this failure mode.

---

## Summary Table

| FM | Name | S | L | D | Score | Status |
|---|---|---|---|---|---|---|
| FM1 | Out-of-scope explanation | 2 | 2 | 3 | **12** | Fix before deployment |
| FM4 | Silent failure | 3 | 1 | 3 | **9** | Fix before deployment |
| FM5 | Constraint drift | 2 | 2 | 2 | **8** | Fix before deployment |
| FM3 | Missing rubric element | 2 | 1 | 2 | **4** | Monitor, fix next cycle |
| FM2 | Word limit exceeded | 1 | 2 | 1 | **2** | Fix in current cycle |

S = Severity, L = Likelihood, D = Detectability

---

## What This Document Produces

Three outputs come from this analysis:

**Specification updates** — FM1 requires a stronger constraint. FM2 requires an updated word limit requirement. FM3 requires an extended rubric instruction.

**Context package updates** — FM4 requires an uncertainty disclosure instruction. FM5 requires a compaction instruction.

**Governance Note updates** — all five failure modes and their mitigations are added to Section 4 (Known Risks and Mitigations) of the Governance Note.

The failure mode analysis does not stand alone — it feeds directly into the specification, the implementation, and the governance documentation.

---

## Quick Recap

- A complete failure mode analysis document has: description, cause, effect, severity, likelihood, detectability, risk score, mitigation, and status for each failure mode
- The summary table ranks all failure modes by risk score — highest scores get fixed first
- The analysis produces three outputs: specification updates, implementation updates, and governance note updates
- This document is the model for the failure mode analysis submitted with your own systems

---

## What Is Next

The next topic introduces the priority matrix — a visual tool for mapping all failure modes at once and deciding which to fix before deployment, which to fix in the next cycle, and which to accept as documented limitations.
