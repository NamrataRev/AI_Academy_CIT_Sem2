# Building the Priority Matrix

---

A doctor in a busy emergency room cannot treat every patient at the same time.

They triage. The patient with a broken arm waits. The patient with chest pain goes first. The patient who is unconscious goes before both. The doctor is not ignoring the broken arm — they are making a principled decision about who needs help most urgently, based on how serious each case is and how quickly it will get worse without treatment.

The priority matrix is triage for failure modes. It takes the risk scores from the failure mode analysis and maps them visually — so you can see at a glance which failures need immediate attention, which can wait, and which can be accepted as known limitations.

---

## What the Priority Matrix Is

The priority matrix is a two-dimensional grid that plots failure modes by two dimensions:

**Horizontal axis — Likelihood** (how often the failure occurs): Low → High

**Vertical axis — Severity** (how serious the failure is): Low → High

Each failure mode is placed on the grid based on its likelihood and severity scores. The position on the grid immediately tells you the priority:

```
HIGH SEVERITY
     |  Monitor      |  Fix before    |
     |  closely      |  deployment    |
     |               |                |
     |---------------|----------------|
     |  Accept as    |  Fix in next   |
     |  limitation   |  cycle         |
     |               |                |
LOW SEVERITY
     LOW LIKELIHOOD    HIGH LIKELIHOOD
```

Top right — high severity, high likelihood — fix before deployment. No exceptions.
Top left — high severity, low likelihood — monitor closely and mitigate.
Bottom right — low severity, high likelihood — fix in next cycle.
Bottom left — low severity, low likelihood — accept as documented limitation.

---

## Why Two Dimensions Instead of One Score

The risk score from the previous topic (Severity × Likelihood × Detectability) gives you a single number for ranking. That is useful. But it collapses three dimensions into one — and that can hide important distinctions.

A failure mode with Severity 3, Likelihood 1, Detectability 1 has a risk score of 3. A failure mode with Severity 1, Likelihood 1, Detectability 3 also has a score of 3. But these are very different problems.

The first is a severe failure that is rare and obvious when it occurs. The second is a minor failure that is rare and invisible. They need different responses — even though their scores are identical.

The priority matrix keeps severity and likelihood visible separately — so you never lose sight of what each failure actually is, even while comparing them.

Detectability is still used — in the placement decision and in the mitigation approach — but the visual matrix focuses on the two dimensions most useful for prioritisation decisions.

---

## Building the Matrix for the Study Assistant

From the worked example in the previous topic:

| FM | Severity | Likelihood | Detectability | Risk Score |
|---|---|---|---|---|
| FM1 | 2 | 2 | 3 | 12 |
| FM2 | 1 | 2 | 1 | 2 |
| FM3 | 2 | 1 | 2 | 4 |
| FM4 | 3 | 1 | 3 | 9 |
| FM5 | 2 | 2 | 2 | 8 |

Plotted on the matrix (using severity and likelihood only):

```
HIGH
SEVERITY  3 |         | FM4      |
            |         |          |
          2 | FM3     | FM1, FM5 |
            |         |          |
          1 |         | FM2      |
            |---------|----------|
              LOW       HIGH
              LIKELIHOOD
```

**FM4** — top left quadrant. High severity, low likelihood. Monitor closely, mitigate before deployment.

**FM1, FM5** — middle right. Moderate severity, moderate likelihood. Fix before deployment.

**FM3** — middle left. Moderate severity, low likelihood. Monitor, fix in next cycle.

**FM2** — bottom right. Low severity, moderate likelihood. Fix in current cycle (easy fix, no reason to delay).

---

## Adding Detectability to the Decision

Once failures are placed on the matrix, detectability adjusts the urgency:

**FM4** sits in the monitor quadrant — but detectability is 3 (hard to detect). A severe failure that is invisible when it occurs needs mitigation even at low likelihood. Detectability 3 pushes FM4 toward "fix before deployment" despite its low likelihood.

**FM2** sits in the fix-next-cycle quadrant — but detectability is 1 (immediately obvious). A minor failure that the user instantly notices is self-correcting — the user asks again and gets the right answer. Detectability 1 confirms FM2 is low urgency.

The rule: high detectability (3) always increases urgency. Low detectability (1) decreases it.

---

## The Complete Decision for Each Failure Mode

| FM | Matrix position | Detectability adjustment | Final decision |
|---|---|---|---|
| FM1 | Fix before deployment | D=3 confirms urgency | Fix before deployment |
| FM2 | Fix next cycle | D=1 reduces urgency | Accept as limitation, document |
| FM3 | Monitor | D=2 no change | Monitor, add test cases |
| FM4 | Monitor closely | D=3 increases urgency | Fix before deployment |
| FM5 | Fix before deployment | D=2 no change | Fix before deployment |

Three failures fixed before deployment (FM1, FM4, FM5). One monitored with test cases (FM3). One accepted as a documented limitation (FM2).

This is a principled, documented decision — not a judgment call made under time pressure.

---

## Quick Recap

- The priority matrix plots failure modes by severity (vertical) and likelihood (horizontal) — four quadrants: fix before deployment, monitor closely, fix next cycle, accept as limitation
- Two dimensions instead of one score keeps severity and likelihood visible separately — important because equal risk scores can represent very different problems
- Detectability adjusts urgency after matrix placement — detectability 3 always increases urgency, detectability 1 decreases it
- The matrix produces a principled, documented decision for each failure mode — not a judgment call

---

## What Is Next

The next topic covers prioritising fixes — how to sequence the work of addressing failure modes, and what to do when you have limited time before deployment.
