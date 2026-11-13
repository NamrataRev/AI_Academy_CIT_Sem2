# What Acceptance Criteria Are

---

The FAQ assistant team now has eight functional requirements and six non-functional requirements — and every one of them has a test. They build the new version and run the full test set: 50 tests in total.

**46 pass. 4 fail.**

The course coordinator joins the meeting and asks the obvious question: *"So — is it ready? Can students start using it on Monday?"*

One team member says yes: *"92% is a great score. The failures are small."*

Another says no: *"One of those failures is the late-penalty question. On one run out of five, it invented a penalty again."*

A third says: *"But it got it right four times out of five. That's still pretty good?"*

The meeting goes on for forty minutes. Nobody is wrong, exactly. They simply never agreed, before testing, on **what "ready" means**. Is 92% enough? Does every failure count the same? Is one invented penalty in five runs acceptable or not?

The answer to those questions — decided in advance and written down — is called **acceptance criteria**.

---

## What Acceptance Criteria Are

**Acceptance criteria** are the conditions a system must meet to be accepted as done. They are agreed **before** building, usually between the team and the person who will use or approve the system — here, the course coordinator.

Think about a driving test. The examiner does not decide at the end whether your driving "felt good enough." They have a checklist agreed in advance:

- A few minor mistakes are allowed — a slightly wide turn, a late signal
- Some mistakes fail you immediately — running a red light, causing danger to another driver
- If you stay within the limits, you pass. Everyone knows the rules before the test starts

Acceptance criteria do the same job for a system. They turn "is it good enough?" from an opinion into a **checklist with a clear result**.

---

## Requirements, Tests and Acceptance Criteria

These three ideas are closely related, and beginners often mix them up. Each one answers a different question:

| | The question it answers | FAQ assistant example |
|---|---|---|
| **Requirement** | What must the system do? | FR-05: The assistant does not state any penalty that is not in the handbook |
| **Test** | How do we check one case? | Ask "What is the late penalty?" and check the answer contains no invented penalty |
| **Acceptance criterion** | What result counts as good enough to accept? | The late-penalty test passes on **every** run — 5 out of 5. Any invented penalty means the system is not accepted |

```text
REQUIREMENT          →  what the system must do
     ↓
TEST                 →  one check of that behaviour
     ↓
ACCEPTANCE CRITERION →  the agreed result that means "accepted"
```

Notice what the acceptance criterion adds. The requirement and the test were already there. What was missing in the meeting was the **agreed line** — how many passes, on which tests, count as ready.

---

## What Makes a Good Acceptance Criterion

Good acceptance criteria share five qualities:

| Quality | What it means | Why it matters |
|---|---|---|
| **Agreed in advance** | Written and signed off before testing starts | Stops the goalposts moving after results come in |
| **Pass/fail** | The result is yes or no — never "mostly" | Ends the forty-minute meeting |
| **Linked to a requirement** | Each criterion checks a specific FR or NFR | You always know what a failure means |
| **From the user's side** | Describes what the student experiences | Keeps the focus on what matters, not on internals |
| **Testable** | Passes the SMART check from the last topic | If you cannot test it, you cannot accept against it |

The first quality is the most important. Remember the risk from the very first topic: when the spec is written after building, it describes what was built. The same thing happens with acceptance criteria. If the team decides what "good enough" means **after** seeing the results, the line drifts to wherever the results happened to land.

---

## Not All Failures Are Equal

The biggest problem with *"46 out of 50 — 92%"* is that it treats every test as equally important.

They are not. Look at the four failures:

| Failed test | What went wrong | How serious? |
|---|---|---|
| Late-penalty question | Invented a penalty on 1 run out of 5 | **Critical** — a student could lose marks acting on it |
| Response time | 2 answers took 7 seconds | **Minor** — annoying, but no harm done |
| Response time | Same as above, different question | **Minor** |
| Answer length | One answer was 170 words instead of under 150 | **Minor** — slightly long, still correct |

Three failures are minor. One is critical. A single overall score hides that completely.

This is why acceptance criteria usually split requirements into two groups:

```text
CRITICAL — zero tolerance
A single failure means the system is not accepted.
Example: inventing a policy, sharing personal information.

STANDARD — threshold allowed
A small number of failures is acceptable, up to an agreed limit.
Example: response time, answer length.
```

Just like the driving test: minor faults are counted, dangerous faults end the test.

---

## Why "Every Run" Matters for AI Systems

You saw in **Non-Functional Requirements** that an AI system can give different answers to the same question. That has a direct effect on acceptance criteria.

The late-penalty question passed **4 times out of 5**. For a traditional program, a test that passes once will pass every time. For an AI system, 4 out of 5 means: **one in five students who ask this question gets a made-up answer.**

If 200 students ask about late penalties before a deadline, that is around 40 students given a wrong rule.

So acceptance criteria for AI systems always say **how many runs** and **how many must pass** — and for critical behaviours, the answer is all of them.

---

## Writing Acceptance Criteria for the FAQ Assistant

Acceptance criteria can be written at two levels.

**Requirement level** — one criterion for a single requirement:

```text
AC for FR-04 (handbook does not cover the question)
For each of the 5 test questions the handbook does not cover,
run 5 times. Accepted if, on all 25 runs, the assistant states
the handbook does not cover it and directs the student to the
course coordinator.
```

**Release level** — the conditions for the whole system to go live:

```text
FAQ ASSISTANT — RELEASE ACCEPTANCE CRITERIA
Each test question is run 5 times.

CRITICAL (100% required — any failure blocks release)
AC-1  No answer states a date, deadline, penalty or rule that is
      not in the handbook.                          (FR-05, NFR-02)
AC-2  Every question the handbook does not cover is redirected
      to the course coordinator.                    (FR-04)
AC-3  The assistant never asks for personal details. (NFR-06)

STANDARD (threshold allowed)
AC-4  At least 95% of all runs pass their functional test.
AC-5  At least 95% of answers appear within 5 seconds. (NFR-01)
AC-6  At least 90% of answers are under 150 words.     (NFR-04)

SIGN-OFF
AC-7  The course coordinator reviews 10 randomly chosen answers
      and confirms they meet the tone checks in NFR-05.
```

Notice AC-7. Some qualities, like tone, still need a human judgement. That is fine — as long as it is written down **who** judges, **how many** answers, and **against what** checks.

---

## Replaying the Meeting

Now run the same meeting again, with these criteria agreed before testing.

The results come in: 46 out of 50 tests pass. The team checks the criteria:

- AC-1 — **Failed.** One run invented a late penalty. This is critical.
- AC-5 — Two slow answers out of 250 runs. Well within the 95% threshold. **Passed.**
- AC-6 — One long answer. Within the 90% threshold. **Passed.**

**Decision: not accepted.** The team fixes the late-penalty behaviour, reruns the tests, and checks again.

That decision took two minutes, not forty. Nobody argued about whether 92% was good enough, because nobody was looking at 92%. They were looking at a checklist everyone had already agreed to.

---

## Who Writes Acceptance Criteria

Acceptance criteria are written **together**:

- **The team** knows what the system can realistically do, and how to test it — they keep the criteria achievable
- **The stakeholder** — here, the course coordinator — knows what "good enough" means for students — they decide what is critical

The stakeholder owns the final answer to "is this acceptable?" The team's job is to make sure the question can be answered with a test, not an opinion.

---

## Quick Recap

- Acceptance criteria are the conditions a system must meet to be accepted as done — agreed before building, between the team and the stakeholder
- Requirements say what the system must do; tests check one case; acceptance criteria set the agreed result that counts as "accepted"
- Good acceptance criteria are agreed in advance, pass/fail, linked to a requirement, written from the user's side and testable
- Not all failures are equal — split criteria into critical (zero tolerance) and standard (threshold allowed)
- For AI systems, always state how many runs and how many must pass — for critical behaviours, every run must pass
- A single overall score like "92%" can hide a critical failure

> **Interview tip:** If asked "what are acceptance criteria?", go beyond "the conditions for a feature to be done." Explain that they must be agreed before testing, so the definition of "done" cannot drift after the results are in. Then mention two things most candidates miss: separating critical failures from minor ones, and — for AI systems — requiring critical behaviours to pass on every run, because the same input can give different outputs. A line like "92% can still mean one in five users gets a made-up answer" shows real understanding.

---

## What Is Next

The team now knows what acceptance criteria are and why they matter. But the criteria above are written in slightly different styles, line by line. The next topic introduces the **Given-When-Then format** — a standard structure that makes every acceptance criterion read the same way, so that anyone on the team can write it, read it and test it.
