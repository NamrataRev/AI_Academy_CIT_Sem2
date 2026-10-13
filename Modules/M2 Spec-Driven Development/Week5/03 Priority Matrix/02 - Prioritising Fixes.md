# Prioritising Fixes

---

You have identified five failure modes. Three need to be fixed before deployment. You have two days.

This is the reality of building systems. Time and effort are always limited. You cannot fix everything at once. You need a principled way to decide what to fix first — so the most important fixes happen before the most important deadline.

Prioritising fixes is not about doing less. It is about doing the right things in the right order.

---

## The Prioritisation Order

Within the "fix before deployment" category, use three rules to sequence the work:

**Rule 1 — Fix the highest risk score first**

Among the failures that must be fixed before deployment, start with the highest risk score. It is the most dangerous. If you run out of time, you want the highest-risk failures addressed, not the most recently remembered ones.

For the study assistant: FM1 (score 12) before FM4 (score 9) before FM5 (score 8).

**Rule 2 — Fix the easiest high-risk failure first if scores are close**

When two failures have similar risk scores and similar priority, fix the easier one first. An easy fix that takes thirty minutes produces a measurable improvement in the pass rate immediately. That improvement gives you evidence the system is getting better — and it frees mental space to focus on the harder fix.

FM5 (constraint drift — fix: add compaction instruction) is easier to address than FM4 (silent failure — fix: add uncertainty disclosure and revise opening statement). If time is short, fixing FM5 first is a defensible choice even though FM4 has a higher score — because FM5's fix is low-effort and high-impact.

**Rule 3 — Fix specification before implementation**

When a failure requires both a specification update and an implementation update, fix the specification first. The specification change defines what correct looks like. The implementation change makes the system produce it. Getting the specification wrong first means fixing the implementation against the wrong target.

For FM1: update FR3 and the constraint wording (specification) before updating the context package (implementation).

---

## When Time Is Genuinely Limited

Sometimes the deadline is fixed and the fixes are not all completable in time. Here is how to handle this responsibly:

**Fix severity-3 failures first — no exceptions**

Any failure with severity 3 must be addressed before deployment, regardless of likelihood or time pressure. A severe, undetectable failure that slips into production is harder to fix after the fact than it was to prevent beforehand.

FM4 (silent failure, severity 3) gets fixed before deployment even if everything else has to wait.

**Document unfixed failures explicitly**

If a failure mode cannot be fixed before deployment, it must be documented in the Governance Note under Known Risks. The documentation should include:
- What the failure is
- Why it was not fixed before deployment
- What the workaround is for users
- When it will be addressed

Deploying with a known unfixed failure is sometimes acceptable. Deploying with an undocumented known failure is not.

**Reduce scope if necessary**

If there is not enough time to fix all required failures and maintain full scope — reduce scope. Deploy a more limited version of the system that does not encounter the unfixed failure modes.

For the study assistant: if FM1 cannot be fixed in time, deploy with a reduced covered topic list — fewer topics means fewer boundary cases where FM1 is likely to trigger.

Reduced scope, properly documented, is better than full scope with undisclosed known failures.

---

## After Deployment — The Fix Queue

Failures that were not addressed before deployment do not disappear. They go into a fix queue — prioritised and scheduled.

The fix queue is part of the changelog:

```
KNOWN ISSUES — FIX QUEUE:

FM3 — Missing rubric element
Priority: Medium (risk score 4)
Planned fix: Add "why" phrasing test cases, extend rubric instruction
Target: v1.3

FM2 — Word limit exceeded on comparison questions  
Priority: Low (risk score 2)
Planned fix: Update FR4 to distinguish response types
Target: v1.2 (already included in current release)
```

The fix queue makes unfixed failures visible — to you, to teammates, and to anyone who inherits the system. It is the difference between "we know about this and are addressing it" and "we have no idea what is wrong."

---

## Communicating Prioritisation Decisions

When you document the priority matrix and the fix decisions, include the reasoning.

Not just: "FM1 fixed, FM3 deferred."

But: "FM1 fixed before deployment — risk score 12, detectability 3, student impact on exam performance. FM3 deferred to v1.3 — risk score 4, low likelihood, student can re-ask if response incomplete."

The reasoning makes the decision auditable. Someone reading the documentation later — including you, three months from now — can understand why each decision was made. This is governance in practice.

---

## Quick Recap

- Prioritise within "fix before deployment" by: highest risk score first, easiest high-risk fix if scores are close, specification before implementation
- Severity-3 failures must be fixed before deployment regardless of time pressure — no exceptions
- Unfixed failures must be documented in the Governance Note — deploying with undocumented known failures is not acceptable
- Reduce scope rather than deploy with undisclosed failures
- Unfixed failures go into a documented fix queue — making them visible and scheduled, not forgotten

---

## What Is Next

The next topic introduces systems thinking — how to see the study assistant not as an isolated tool but as part of a larger system, and why changes to one part produce unexpected effects in other parts.
