# Severity, Likelihood and Detectability

---

A hospital has a long list of things that could go wrong.

A patient could be given the wrong medication. A piece of equipment could malfunction. A file could be misfiled. An appointment could be scheduled at the wrong time.

Not all of these are equal. The wrong medication could be fatal. A misfiled document causes a delay. The hospital does not treat all risks the same — it prioritises based on how serious each failure is, how likely it is to happen, and how quickly it would be detected.

The same three dimensions — severity, likelihood, and detectability — are what you use to assess failure modes in AI systems.

---

## The Three Dimensions

**Severity — how serious is the failure if it occurs?**

How much harm does this failure cause? To whom? How difficult is it to recover from?

Scale (1-3):
- 1 — Minor: inconvenient but easily corrected. The student notices, asks again, gets the right answer.
- 2 — Moderate: causes real problems but recoverable. The student studies incorrect information but has other sources to cross-check.
- 3 — Severe: causes significant harm that is hard to reverse. The student studies incorrect information, has no other source, and performs poorly in the exam as a result.

**Likelihood — how often is this failure likely to occur?**

Given the system's design, the user population, and the types of inputs it will receive — how frequently will this failure happen?

Scale (1-3):
- 1 — Rare: unusual conditions required, uncommon user behaviour.
- 2 — Occasional: happens in specific scenarios that real users will encounter.
- 3 — Frequent: happens regularly under normal use.

**Detectability — how quickly is this failure caught?**

If this failure occurs, how likely is it that the user — or a reviewer — will notice it?

Scale (1-3):
- 1 — Easily detected: the failure is obvious. The user immediately knows something went wrong.
- 2 — Sometimes detected: the user may or may not notice. Depends on their prior knowledge or attention.
- 3 — Hard to detect: the failure looks like a correct response. The user has no reason to doubt it.

---

## The Risk Score

Multiply the three scores together:

**Risk Score = Severity × Likelihood × Detectability**

Maximum score: 27 (3 × 3 × 3) — severe, frequent, undetectable.
Minimum score: 1 (1 × 1 × 1) — minor, rare, immediately obvious.

The risk score gives you a number to rank failure modes against each other. Higher score — higher priority to fix.

---

## Applying It to the Study Assistant Failure Modes

| FM | Name | Severity | Likelihood | Detectability | Risk Score |
|---|---|---|---|---|---|
| FM1 | Out-of-scope explanation | 2 | 2 | 3 | **12** |
| FM2 | Word limit exceeded | 1 | 2 | 1 | **2** |
| FM3 | Missing rubric element | 2 | 1 | 2 | **4** |
| FM4 | Silent failure — fabricated answer | 3 | 1 | 3 | **9** |
| FM5 | Constraint drift over long sessions | 2 | 2 | 2 | **8** |

---

**FM1 — Out-of-scope explanation — Score: 12**

Severity 2: Student receives explanation before prerequisites — real problem, but other sources available.
Likelihood 2: Happens when students ask politely-framed or indirect out-of-scope questions — not rare.
Detectability 3: The explanation looks correct. The student has no reason to doubt it unless they know the topic was not supposed to be covered yet.

High priority. The combination of moderate severity, moderate likelihood, and low detectability makes this the most urgent failure to address.

**FM4 — Silent failure — Score: 9**

Severity 3: Student studies fabricated information with no indication it was fabricated.
Likelihood 1: Rare — requires a query the model cannot answer from its knowledge or tools.
Detectability 3: Output looks like a normal correct response. No signal of failure.

High priority despite low likelihood — severity 3 and detectability 3 together are too dangerous to leave unaddressed.

**FM5 — Constraint drift — Score: 8**

Severity 2: Responses become inconsistent over long sessions.
Likelihood 2: Happens in sessions that run long without compaction.
Detectability 2: Drift is gradual — students may notice responses changing but not identify the cause.

Medium-high priority. Addressable through compaction instructions and session length guidance.

**FM3 — Missing rubric element — Score: 4**

Severity 2: Incomplete explanation — student missing one component.
Likelihood 1: Rare — the exemplars and rubric together make this unlikely.
Detectability 2: Student may notice the response feels incomplete.

Medium priority. Worth a specific test case but not urgent to fix before deployment.

**FM2 — Word limit exceeded — Score: 2**

Severity 1: Response too long — inconvenient but the information is still there.
Likelihood 2: Happens on comparison questions.
Detectability 1: Immediately obvious — student can see the response is long.

Low priority. Fix is simple (extend the limit for comparison questions) and the failure is obvious when it occurs.

---

## What the Scores Tell You

The ranking is: FM1 (12) > FM4 (9) > FM5 (8) > FM3 (4) > FM2 (2).

This means:
- Fix FM1 before deployment — out-of-scope explanations with high detectability score are the most dangerous
- Address FM4 before deployment — even rare silent failures need explicit mitigation
- Plan FM5 mitigation — compaction guidance and session length instructions
- Monitor FM3 — add test cases, watch in production
- Document FM2 as a known limitation — low enough priority to accept and note

The scores do not make the decisions for you. They give you a principled basis for prioritising your effort — fixing the most dangerous failures first, accepting the least dangerous as known limitations.

---

## Quick Recap

- Three dimensions: severity (how serious), likelihood (how often), detectability (how quickly caught)
- Risk Score = Severity × Likelihood × Detectability — maximum 27, minimum 1
- High detectability score (3) means the failure looks like a correct response — the most dangerous category
- The scores rank failure modes for prioritisation — fix highest scores before deployment, accept lowest scores as documented limitations

---

## What Is Next

The next topic is a worked example — applying severity, likelihood, and detectability to all five study assistant failure modes and producing a complete failure mode analysis document.
