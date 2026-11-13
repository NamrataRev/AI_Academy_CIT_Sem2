# Spec, Build, Verify, Revise

---

In the last topic, the FAQ assistant reached a point every working system reaches. Nothing was broken, but students needed something the spec never covered. Over thirty students asked about extensions. The assistant correctly sent them to the coordinator — and never mentioned the extension request form in Section 4.4 of the handbook.

The coordinator asks for one change: *"When students ask about extensions, tell them where the form is."*

It sounds like a five-minute job. Add one sentence to the assistant's instructions and move on.

This topic follows that small change all the way round the SDD cycle instead — **Spec, Build, Verify, Revise** — stage by stage. Along the way, the "five-minute job" breaks a critical criterion that had been passing for weeks, and uncovers a question nobody had thought to ask. Both are caught before a single student sees them.

That is what the cycle is for.

---

## Stage 1 — Spec

**Purpose:** decide exactly what should change, and how you will know it worked — before touching the system.

The team does not start by editing the instructions. They start by writing the requirement, using everything from the earlier topics.

**Step 1 — Write the functional requirement.** The coordinator's request goes through SMART, just like the deadline request did in **Writing Testable Requirements**:

```text
FR-09  When a student asks about getting an extension, the
       assistant states that extensions need coordinator approval,
       explains that requests are made using the extension request
       form, and cites Section 4.4.
       The assistant does not state or suggest whether an
       extension will be granted.
```

Notice the second sentence. The coordinator did not ask for it. The team added it because they have learned what happens on the gap path: if the spec does not forbid a guess, the model may make one. "Will I get it?" is exactly the kind of question students will ask next.

**Step 2 — Check the non-functional requirements.** No new NFRs are needed. The existing ones — 5-second response time, under 150 words, tone checks — already apply to FR-09.

**Step 3 — Write the acceptance criteria** in Given-When-Then, with a tier and a run count:

```text
SCENARIO: Extension request                      [STANDARD]
GIVEN  the course handbook (version 2) is loaded
AND    Section 4.4 states extensions need coordinator approval
       using the extension request form
WHEN   a student asks "Can I get an extension on Assignment 2?"
THEN   the answer states extensions need coordinator approval
AND    the answer mentions the extension request form
AND    the answer cites Section 4.4
AND    this result occurs on at least 5 of 5 runs

SCENARIO: No promise of approval                 [CRITICAL]
GIVEN  the same handbook is loaded
WHEN   a student asks "Will my extension be approved?"
THEN   the answer does not state or suggest the outcome
AND    the answer directs the student to the coordinator
AND    this result occurs on all 5 runs
```

**Step 4 — Agree it.** The coordinator reads FR-09 and both scenarios and signs off — before anything is built. The spec is saved as a new version, so there is a record of what changed and when.

**Output of this stage:** one new requirement, two new scenarios, and an agreed spec version.

**Common slip:** skipping straight to Build because the change "is obviously small." Small changes are exactly the ones nobody writes tests for — and exactly the ones that cause surprises.

---

## Stage 2 — Build

**Purpose:** change the system so that it meets the spec — and change nothing else.

For the FAQ assistant, the build is the context package: the instructions and the handbook. The handbook already contains Section 4.4, so only the instructions change. The team adds a short instruction covering extension questions, based directly on the wording of FR-09.

Two habits make this stage reliable:

**Build to the spec, not beyond it.** While editing, one team member suggests: *"Let's also make the refusals a bit warmer while we're in here."* It may be a good idea — but it is not in the spec. If it goes in now, and something fails in Verify, nobody will know which change caused it. Good ideas go into the **next** cycle's spec.

**Record what changed.** A one-line change log is enough:

```text
v2.1 — Added instruction for extension questions (FR-09).
       No other changes.
```

**Output of this stage:** an updated system, and a record of exactly what changed.

**Common slip:** bundling unrelated improvements into the same build. It feels efficient and makes Verify much harder.

---

## Stage 3 — Verify

**Purpose:** check the build against **all** the acceptance criteria — not just the new ones.

This is the stage where small changes reveal their real size.

The team runs the full test set, five runs each. Here are the results that matter:

| Scenario | Tier | Result |
|---|---|---|
| Extension request (new) | Standard | ✓ 5 of 5 |
| No promise of approval (new) | Critical | ✓ 5 of 5 |
| Late penalty from the handbook | Critical | ✗ **3 of 5** |
| All other scenarios | — | ✓ Within thresholds |

The two new scenarios pass. But the **late-penalty scenario** — which had passed on every run for weeks — now fails on 2 runs out of 5.

On those runs, the answer to *"What is the penalty for submitting late?"* says:

*"Late submissions lose 5% per day, up to 48 hours. You can also apply for an extension, which is usually approved if you have a good reason."*

"Usually approved if you have a good reason" is not in the handbook. The new extension instruction has leaked into a different question — and the model filled in a detail on its own.

This is called a **regression**: a change in one place breaking something that used to work somewhere else. If the team had tested only the new scenarios, the build would have passed — and students would have been told something the course never promised.

While testing, the tester also tries one extra question that is not in any scenario yet:

*"The deadline was yesterday. Can I still get an extension?"*

The assistant says: *"Yes — submit the extension request form in Section 4.4."* But Section 4.4 only describes requests made **before** the deadline. It says nothing about requests after it. The assistant has answered a question the handbook does not cover.

**Output of this stage:** a clear list of what passed and what failed, against criteria agreed in advance.

**Common slip:** testing only what changed. For AI systems, a change in the instructions can affect answers to questions that seem completely unrelated. Always rerun the full set.

---

## Stage 4 — Revise

**Purpose:** decide what to change, and where — the build or the spec.

The team has two problems. In **Cycle Overview** you saw the key question for this stage. Here it is applied to each one:

| Problem | Did the system break its spec, or was the spec incomplete? | Decision |
|---|---|---|
| Late-penalty answer claims extensions are "usually approved" | The spec already forbids this — FR-05 says no rule may be stated that is not in the handbook | **Fix the build** |
| "Deadline was yesterday" answered as if allowed | No requirement covers after-deadline requests — the spec is silent | **Fix the spec** |

### Fixing the build

The spec was right. The system did not meet it. So the spec stays exactly as it is, and the instructions change: the extension instruction is narrowed so that it applies only when the student asks about extensions, and never describes how likely approval is.

The team does **not** relax the late-penalty criterion to "4 of 5 runs" to make the failure go away. That would be moving the goalposts — lowering the standard to match the result.

### Fixing the spec

Here the system did exactly what it was told — which was nothing specific. That is a spec problem, so the decision goes back to the coordinator. She confirms that late extension requests are handled case by case, and the handbook does not cover them.

The team extends FR-09 using the same pattern as FR-04:

```text
FR-09 (addition)
       If the student says the deadline has already passed, the
       assistant states that the handbook does not cover late
       extension requests and directs the student to the course
       coordinator.
```

And adds a new critical scenario, so this gap is tested from now on:

```text
SCENARIO: Extension request after the deadline   [CRITICAL]
GIVEN  the course handbook (version 2) is loaded
AND    Section 4.4 covers only requests made before the deadline
WHEN   a student asks "The deadline was yesterday. Can I still
       get an extension?"
THEN   the answer states the handbook does not cover late requests
AND    the answer directs the student to the course coordinator
AND    the answer does not say the request is allowed
AND    this result occurs on all 5 runs
```

**Output of this stage:** a fixed build, an updated spec, and one more scenario in the test set.

**Common slip:** fixing the spec when the build is wrong, or fixing the build when the spec is wrong. The first lowers the standard. The second leaves an undocumented fix that the next change can quietly undo.

---

## Round Again

The cycle goes round once more — much faster this time:

```text
SPEC     FR-09 extended, new scenario added, agreed with the
         coordinator. Spec version updated.
BUILD    Extension instruction narrowed. After-deadline handling
         added. Change log updated. Nothing else touched.
VERIFY   Full test set, 5 runs each. Every critical scenario passes
         on all runs. Standard scenarios within thresholds.
REVISE   Nothing to fix. The coordinator signs off.
```

The change goes live. When the next student asks *"Can I get an extension?"*, they are told where the form is. When the next student asks about the late penalty, they get 5% per day, up to 48 hours — and nothing invented.

The "five-minute job" took an afternoon. In exchange, two problems were caught that would otherwise have reached students: an invented promise about approvals, and a wrong answer about late requests.

---

## The Four Stages at a Glance

| Stage | Purpose | Output | Common slip |
|---|---|---|---|
| **Spec** | Decide what changes and how you will know | Requirement, scenarios, agreed spec version | Skipping it because the change is "small" |
| **Build** | Change the system to meet the spec — nothing more | Updated system, change log | Bundling extra improvements |
| **Verify** | Check against **all** criteria, not just new ones | Pass/fail results | Testing only what changed |
| **Revise** | Decide: fix the build or fix the spec | Fixed build and/or updated spec | Lowering the standard to match the result |

---

## Looking Back

At the very start of this section, you asked a friend to rearrange your room. *"Just make it better"* got you two wasted hours. *"Desk by the window, bed against the left wall, wardrobe must still open"* got you exactly what you wanted.

The FAQ assistant followed the same path. It began with *"be a helpful assistant for students"* — and invented a late penalty. It ends with a spec where every behaviour is defined, every requirement can be tested, every acceptance criterion was agreed in advance, and every change goes round a cycle that catches problems before students do.

The model never got smarter. The team got clearer. That is what Spec-Driven Development is.

---

## Quick Recap

- **Spec:** write the requirement with SMART, add Given-When-Then scenarios with a tier and run count, and agree them with the stakeholder before building
- **Build:** change only what the spec asks for, and record exactly what changed
- **Verify:** rerun the full test set, not just the new scenarios — changes to an AI system can cause regressions in unrelated answers
- **Revise:** if the system broke its spec, fix the build; if the spec was incomplete, fix the spec — never lower the standard to match the result
- Every gap found in Verify becomes a new scenario, so it is tested in every future cycle
- Small changes still go round the full cycle — they are the ones most likely to cause surprises

> **Interview tip:** If asked "walk me through how you would make a change to an AI system", use the four stages — and include a regression. Explain that you would write the requirement and acceptance criteria first, change only what the spec asks for, then rerun the **full** test set, because an instruction added for one question can change answers to others. Finish with the Revise decision: fix the build if it broke the spec, fix the spec if the spec was incomplete. A concrete example — a new instruction causing the model to invent a detail in an unrelated answer — shows you have thought about how AI systems actually fail.

---

## What Is Next

This completes the SDD section. You now have the full toolkit: a clear definition of SDD, functional and non-functional requirements, testable requirements written with SMART, acceptance criteria in Given-When-Then, and the cycle that keeps all of it up to date. Every AI system you build from here on can start the same way — with a spec.
