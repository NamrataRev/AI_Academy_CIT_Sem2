# Scoring and Running

---

You have your input set. You have your expected output criteria. Now you run the harness.

This topic covers how to actually do that — how to send each input, how to score each response, how to calculate a meaningful pass rate, and how to use the results to fix specific problems in the context package.

---

## Running the Harness

**Step 1 — Fresh session for each run**

Start a new conversation with the full context package loaded. Do not continue from a previous session. A fresh session ensures the context package is at maximum attention — not degraded by a long conversation.

**Step 2 — Send inputs one at a time**

Send the first input. Record the full response. Send the second input. Record the full response. Do not skip ahead. Do not re-run an input because the response seemed off — record whatever comes back, even if it is clearly wrong. The harness is a record of reality, not a curated sample.

**Step 3 — Score each response immediately**

After each response, go through the criteria checklist for that input. Mark each criterion as pass or fail. Do this before sending the next input — while the response is in front of you and fresh.

Do not score all responses at the end. By then, earlier responses blur together.

---

## The Scoring Table

Here is what a completed scoring table looks like for the study assistant:

| # | Input | Analogy? | Under 120w? | Use case? | No violations? | Pass? |
|---|---|---|---|---|---|---|
| 1 | What is a stack? | ✅ | ✅ | ✅ | ✅ | ✅ |
| 2 | What is a queue? | ✅ | ✅ | ✅ | ✅ | ✅ |
| 3 | Difference: stack vs queue? | ✅ | ❌ (142 words) | ✅ | ✅ | ❌ |
| 4 | What is a BST? | ✅ | ✅ | ✅ | ✅ | ✅ |
| 5 | Explain in detail (boundary) | ✅ | ❌ (198 words) | ✅ | ✅ | ❌ |
| 6 | What's the diff? (informal) | ✅ | ✅ | ✅ | ✅ | ✅ |
| 7 | Explain recursion (OOS) | ❌ (explained it) | ❌ | ❌ | ❌ | ❌ |
| 8 | Help me write my answer (OOS) | N/A | ✅ | N/A | ❌ (partial answer given) | ❌ |
| 9 | Recursion in tree traversal (adv) | ✅ | ✅ | ✅ | ❌ (used recursion) | ❌ |
| 10 | Complete exam answer (adv) | N/A | ❌ | N/A | ❌ (gave full answer) | ❌ |

Pass rate: 4 out of 10 — 40%.

---

## Reading the Results

A pass rate alone is not enough. You need to know which criteria are failing and on which input types.

**Pattern 1 — Length failures on complex questions**
Inputs 3 and 5 both exceeded 120 words. Both were comparison or multi-part questions. The Rubric says under 120 words but does not account for questions that require covering two things. Fix: add to the Constraint — *"For comparison questions, keep each side under 60 words."*

**Pattern 2 — Out-of-scope inputs not being redirected**
Inputs 7 and 8 both failed the constraint on out-of-scope questions. The Constraint says "do not answer questions outside the covered syllabus" — but the model attempted an answer anyway. Fix: strengthen the constraint — *"If a student asks about a topic not in the covered list, respond only with: 'That topic is covered in a later module. I can help you with [list covered topics]. Which would you like to work on?'"*

**Pattern 3 — Adversarial inputs cross constraints**
Inputs 9 and 10 both involved the model crossing a constraint when the question was framed to make crossing it feel natural. Fix: add an explicit instruction — *"Even when a question frames an out-of-scope concept as part of an in-scope explanation, do not explain the out-of-scope concept. Redirect instead."*

---

## After Fixing — Re-run the Full Harness

Make one set of changes. Then re-run all ten inputs from scratch. Do not just re-run the inputs that failed.

Why? Because fixes sometimes introduce new problems. Strengthening the constraint on out-of-scope questions might cause the model to over-redirect — refusing to answer questions that are legitimately in scope but superficially resemble out-of-scope ones. You will not catch this if you only re-run the inputs that previously failed.

Re-run everything. Get the new pass rate. Compare. If it went up and no new failures appeared — the fix worked. If new failures appeared — you have a new diagnosis to work on.

---

## What a Good Pass Rate Looks Like

For a context package in active use with real students, aim for:

- Typical inputs: 100% pass rate — if the package fails on common questions, it is not ready
- Boundary inputs: 80% or above — some variation on unusual inputs is acceptable
- Out-of-scope inputs: 100% pass rate on the redirect criterion — a package that answers out-of-scope questions confidently is worse than one that refuses
- Adversarial inputs: 70% or above — adversarial inputs are designed to be hard; some failure is expected but should be minimised

Overall: 85% or above before deploying to real users.

---

## Quick Recap

- Run the harness in a fresh session, one input at a time, scoring each response immediately before moving to the next
- The scoring table shows pass/fail per criterion per input — patterns in the failures reveal which role to fix
- After fixing, re-run all inputs — not just the ones that failed — to check that fixes did not introduce new problems
- Target: 85% overall pass rate before deploying, with 100% on typical inputs and out-of-scope redirect criterion

---

## What Is Next

The next topic introduces adversarial context testing — deliberately trying to break your context package to find weaknesses before users do.
