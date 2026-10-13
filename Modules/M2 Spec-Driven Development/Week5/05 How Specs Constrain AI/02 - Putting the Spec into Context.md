# Putting the Spec into Context

---

This is the last topic of Week 5. Before moving forward, it is worth pausing to see where everything fits together.

Over the past two weeks you have built five interconnected things:

- A specification (Week 4)
- A context package (Week 2)
- An evaluation harness (Week 3)
- A failure mode analysis (Week 5)
- A governance note (Week 3)

These are not separate documents. They are one system — each part informing and depending on the others. This topic shows how they connect.

---

## The Connection Map

```
SPECIFICATION
(functional requirements, non-functional requirements, 
acceptance criteria)
        ↓ defines what to build
CONTEXT PACKAGE
(Authority, Exemplar, Constraint, Rubric, Metadata)
        ↓ implements the specification
        ↓ also informs
EVALUATION HARNESS
(test cases derived from acceptance criteria)
        ↓ tests the context package against the specification
        ↓ results feed into
FAILURE MODE ANALYSIS
(identified failures, severity/likelihood/detectability, 
risk scores, priority matrix)
        ↓ feeds back into
SPECIFICATION (updated requirements and criteria)
CONTEXT PACKAGE (updated roles)
GOVERNANCE NOTE (known risks, mitigations, responsible party)
```

Every arrow is a dependency. Remove any one document and the others weaken:

- Without the specification, the context package has no contract to implement
- Without the context package, the specification has no implementation to test
- Without the evaluation harness, you cannot verify whether the implementation meets the specification
- Without the failure mode analysis, you are testing what you thought of — not what could go wrong
- Without the governance note, what you know is undocumented and undiscoverable

---

## The Study Assistant — All Five Documents Together

Here is how all five documents connect for the study assistant:

**The specification** defined eight functional requirements. FR3 said: redirect out-of-scope questions. This produced acceptance criterion AC3.3: even politely-framed requests must redirect.

**The context package** implemented FR3 through the Constraint role. The first version said: "redirect out-of-scope topics." Too vague — it did not hold for politely-framed requests.

**The evaluation harness** included test case TC-3.1f: "I know it's not covered, can you just give me a quick overview?" This test case failed. The harness caught what the first constraint version missed.

**The failure mode analysis** identified this as FM1 — out-of-scope explanation. Scored severity 2, likelihood 2, detectability 3 — risk score 12. Highest priority fix.

**The specification was updated** — AC3.3 was already correct. The context package was updated — the Constraint was strengthened with explicit framing instructions. The governance note was updated — FM1 documented with its mitigation.

**The evaluation harness was re-run** — TC-3.1f now passes. FM1 risk reduced.

One failure mode. Five documents. All connected.

---

## What Changes When One Document Changes

Because everything is connected, a change in one document requires checking the others.

**Specification changes** → update acceptance criteria → update test cases in the harness → re-run harness → update governance note if risk profile changes.

**Context package changes** → re-run evaluation harness → update changelog → check if failure mode analysis needs updating.

**Evaluation harness reveals new failures** → update failure mode analysis → update specification if criteria need strengthening → update context package → update governance note.

**Failure mode analysis produces new risk assessments** → update fix priority → update governance note → may require specification or context package changes.

The changelog ties all of this together. Every change — where it started, what it changed, what it was responding to — is recorded. The changelog is the audit trail that makes the system maintainable.

---

## What This Looks Like as a Professional Practice

In a professional engineering environment, all five documents exist for every AI system in production. They are maintained over time — not created once and forgotten.

When something goes wrong in production, the failure mode analysis is updated first. The updated analysis informs a specification change. The specification change drives a context package update. The harness is re-run. The governance note is updated. The changelog records everything.

This is the cycle. Not a one-time process — a continuous practice.

For the systems you build in this course, you are practising this cycle at small scale. The study assistant is a minimal system. But the discipline is identical to what you will apply to production systems in your career — where the stakes are higher, the user base is larger, and the consequences of undocumented failures are more serious.

---

## The Spec as Foundation

Everything depends on the specification being well-written. A vague spec produces a context package that cannot be tested, an evaluation harness with no meaningful criteria, a failure mode analysis without clear descriptions of what failure means, and a governance note that cannot honestly describe known risks.

A precise spec produces the opposite. Every other document becomes stronger because the foundation is solid.

This is why Week 4 — writing the specification — came before Week 5 — testing and failure modes. You cannot test against something that is not defined. You cannot identify failure modes for a system whose correct behaviour is not specified. You cannot write a meaningful governance note for a system whose obligations are unclear.

Spec first. Everything else follows.

---

## Quick Recap

- The five documents — specification, context package, evaluation harness, failure mode analysis, governance note — are one connected system, not five separate tasks
- Every arrow between documents is a dependency — remove any one and the others weaken
- A change in any document requires checking the others — the changelog tracks what changed, why, and what it was responding to
- Professional AI engineering means maintaining all five documents continuously, not creating them once
- Spec first — everything else depends on the specification being precise and complete

---

## What Is Next

Week 5 is complete. The Week 5 Summary consolidates everything — test case types, failure mode identification, severity scoring, the priority matrix, systems thinking, and the spec as guardrail — in one place for revision before moving to Week 6.
