# The SDD Cycle — Overview

---

Building a system without a cycle is like cooking without a recipe and then never tasting what you made.

You prepare ingredients. You cook. You serve. But you never check whether it tastes right before it reaches the table. If something is wrong, you find out too late.

The SDD cycle is the recipe and the tasting — built into the process from the start. Not a one-time sequence but a loop that keeps the system honest at every stage. You specify, you build, you verify, and when verification finds something wrong, you revise and go around again.

---

## The Four Stages

```
SPECIFY
  ↓
BUILD
  ↓
VERIFY
  ↓
REVISE
  ↑___|
```

Each stage has a clear input and a clear output. Each feeds directly into the next. And when Verify finds a problem, Revise feeds back into Specify — not into Build. The fix starts with the specification, not the implementation.

---

## Stage 1 — Specify

Define what you are building before you build it.

This is everything covered so far this week:
- Write functional requirements — what the system does
- Write non-functional requirements — how well it does it
- Write acceptance criteria in Given-When-Then format — the binary conditions that define done
- Apply the testability check — ensure every criterion can be evaluated without judgment

The output of Specify is a complete specification — precise enough that someone else could build to it, and precise enough that you could test it without asking the original author any questions.

If the specification is not complete enough to hand to someone else and get back what you intended — it is not finished. Do not move to Build.

---

## Stage 2 — Build

Implement the system to meet the specification.

For an AI system, Build means:
- Writing the context package (Authority, Exemplar, Constraint, Rubric, Metadata)
- Setting up the system prompt
- Configuring any tools or integrations
- Building the backend endpoint if one is needed

During Build, the specification is the reference. When a decision needs to be made — what format should the response take, how should the system handle this edge case — the answer is in the specification. If the specification does not cover it, go back to Specify and add it. Do not make the decision quietly during Build.

The output of Build is a working implementation — built to the specification, not to a vague intention.

---

## Stage 3 — Verify

Test the implementation against the acceptance criteria.

This is the evaluation harness from Week 3. Run the fixed input set. Score each response against each criterion. Record the pass rate.

Verify answers one question: does the implementation meet the specification?

Not "does it seem to work" or "does it look reasonable" — does it meet the specific, binary conditions defined in the acceptance criteria?

The output of Verify is a scored result — pass rate, patterns in failures, specific criteria that did not hold.

---

## Stage 4 — Revise

Fix what Verify found.

Revision has two parts, and the order matters:

**First: fix the specification if it was wrong.**
If a criterion failed because the criterion was poorly written — not because the implementation was wrong — fix the criterion. Update the specification. Re-run Verify.

**Second: fix the implementation if the specification was right.**
If a criterion failed because the implementation did not meet a correctly-written specification — fix the implementation. Update the changelog. Re-run Verify.

Do not fix the implementation without checking the specification first. A failing criterion sometimes reveals a gap in the specification, not a bug in the implementation.

The output of Revise is an updated specification and/or implementation — ready to re-enter Verify.

---

## Why It Is a Cycle, Not a Sequence

Most students think of SDD as a linear process: specify → build → test → done.

It is not. It is a cycle because:

- Verification almost always finds something — a failing criterion, a gap in the specification, an edge case not covered
- Revision feeds back into Specify — because fixing an implementation without updating the specification means the specification no longer reflects the system
- The cycle runs multiple times — until Verify confirms every criterion passes at the required threshold

A single pass through the cycle is not done. Done is when Verify confirms the system meets the specification at the required threshold — consistently, across multiple runs.

---

## The Cycle Applied to the Study Assistant

**Specify:** Write eight functional requirements, six non-functional requirements, and acceptance criteria in Given-When-Then format for all of them.

**Build:** Write the context package — Authority, Exemplar, Constraint, Rubric, Metadata — to meet each requirement.

**Verify:** Run the fifteen-input evaluation harness. Results: 12/15 pass. Three failures — two length violations on comparison questions, one constraint crossed on an adversarial input.

**Revise:** 
- Specification: add a criterion for comparison questions specifically — "for questions comparing two or more concepts, the total response is under 180 words"
- Implementation: strengthen the adversarial constraint — add explicit instruction for politely-framed out-of-scope requests
- Changelog: updated with both changes and the reason for each

**Verify again:** Run the same fifteen inputs. Results: 14/15 pass. One remaining failure — an edge case not previously tested.

**Revise again:** Add the edge case as a new test input. Fix the criterion. Re-run.

The cycle continues until the pass rate meets the threshold. Then the system is ready.

---

## Quick Recap

- The SDD cycle has four stages: Specify, Build, Verify, Revise — running as a loop until the system meets the specification
- Specify produces a complete specification before any building starts
- Verify answers one question: does the implementation meet the acceptance criteria?
- Revise fixes the specification first if it was wrong, then the implementation — never the implementation without checking the specification
- A single pass is not done — the cycle runs until Verify confirms the required pass rate consistently

---

## What Is Next

The next topic covers Spec, Build, Verify, Revise in depth — walking through one complete cycle for the study assistant so you can see exactly what each stage produces and how each feeds into the next.
