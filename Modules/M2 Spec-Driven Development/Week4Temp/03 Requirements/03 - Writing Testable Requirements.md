# Writing Testable Requirements

---

The FAQ assistant team now has a proper spec: seven functional requirements and six non-functional requirements. Before building again, they share it with the course coordinator for review.

The coordinator likes it. Then she adds one request of her own:

*"The assistant should remind students about upcoming deadlines and make sure they don't miss them."*

It sounds like a great idea. Everyone agrees. Someone starts typing it into the spec as FR-08.

Then one of the team asks a simple question: **"How would we test that?"**

Nobody can answer. Remind them how — the assistant only replies when a student asks something. Which deadlines count as "upcoming" — this week, this month? And "make sure they don't miss them" — how would anyone check that the assistant achieved it?

While they are at it, the team rereads their own lines. FR-03 says the assistant gives a *"short"* explanation of general terms. FR-06 talks about an *"unclear"* question. Both words still need an opinion to check.

A requirement you cannot test is a requirement you cannot verify. This topic is about fixing that — and the main tool for it is **SMART**.

---

## What "Testable" Means

A requirement is **testable** when you can write a test for it that has three parts:

```text
1. A SITUATION YOU CAN CREATE
   An input you can actually give the system.
   "Ask: When is Assignment 2 due?"

2. AN OUTCOME YOU CAN OBSERVE
   Something visible in the answer.
   "The answer contains a date and a handbook citation."

3. A PASS/FAIL RULE
   A clear line between right and wrong.
   "Pass if the date is 14 March and Section 3.2 is cited."
```

If any of the three is missing, the requirement is not testable yet.

There is a simple habit that catches most problems: **write the test at the same time as the requirement.** If you cannot write the test, the requirement is not finished.

Try it on the coordinator's request. What situation do you create to test "make sure they don't miss them"? What do you observe? There is no answer — so the requirement needs rewriting.

---

## The SMART Framework

You saw SMART briefly as a diagnostic in **Why Informal Specs Break**. Now you will use it properly — as a step-by-step way to rewrite a weak requirement until it is testable.

| Letter | Means | The question to ask |
|---|---|---|
| **S** | Specific | Does it say exactly what happens, in which situation? |
| **M** | Measurable | Can the result be checked with a number or a clear yes/no? |
| **A** | Achievable | Can this system realistically do it? |
| **R** | Relevant | Does it serve a real need of the people using the system? |
| **T** | Time-bound | Does it say how fast, or over what time period it applies? |

SMART was first used for setting goals. For requirements, each letter keeps the same spirit, with one adjustment: **Time-bound** means the requirement states its time limits — how fast the system must respond, or what time window the behaviour covers.

---

## Rewriting a Requirement, One Letter at a Time

Here is the coordinator's request, taken through SMART step by step.

**Starting point:**
*"The assistant should remind students about upcoming deadlines and make sure they don't miss them."*

### S — Specific

**Problem:** "Remind" and "upcoming deadlines" are open to interpretation. Remind when? Which deadlines?

**Fix:** State the exact situation and the exact behaviour.

*"When a student asks about upcoming deadlines, the assistant lists the deadlines from the handbook."*

### M — Measurable

**Problem:** "Lists the deadlines" — all of them? In what form? Two reviewers could still disagree on whether an answer passes.

**Fix:** Define what a correct answer contains, so it can be checked line by line.

*"…lists each deadline with its date and the handbook section it comes from, in date order."*

### A — Achievable

**Problem:** "Make sure they don't miss them" cannot be achieved. The assistant only responds when a student asks something. It cannot send alerts, and it cannot control whether a student submits on time.

**Fix:** Remove the part the system cannot do, and keep the part it can.

The promise changes from *"students won't miss deadlines"* to *"students who ask get a complete, correct list."* That is less impressive on paper — but it is honest, and it can be tested.

If the coordinator really wants alerts, that is a different system with different capabilities. The spec should say so openly rather than promise it quietly.

### R — Relevant

**Check:** Does this serve a real need? Yes. Students do ask "what's due soon?" — it is one of the most common questions any course gets. This requirement passes.

Relevant also works as a filter. If the coordinator had asked for *"the assistant should tell students a motivational quote each day,"* the team could ask: does this help students get correct course information? If not, it does not belong in this spec.

### T — Time-bound

**Problem:** "Upcoming" has no time window. Tomorrow? This semester?

**Fix:** State the window, and how the assistant handles an empty result.

*"…that fall within the next 14 days. If there are none, the assistant says there are no deadlines in the next 14 days."*

### The finished requirement

```text
BEFORE
"The assistant should remind students about upcoming deadlines
and make sure they don't miss them."

AFTER — FR-08
When a student asks about upcoming deadlines, the assistant lists
every handbook deadline that falls within the next 14 days, with
its date and handbook section, in date order. If there are none,
it states that there are no deadlines in the next 14 days.
```

And now the test can be written:

```text
TEST FOR FR-08
Situation:  Today is 3 March. Handbook deadlines: 10 March
            (Assignment 2) and 25 March (Project proposal).
            Ask: "What's due soon?"
Observe:    Which deadlines are listed, with dates and sections.
Pass if:    Only Assignment 2 (10 March) is listed, with its
            handbook section. Project proposal is not listed.
```

Same intention as the coordinator's original request. Now everyone — the team, the coordinator, a tester — can agree on whether it works.

---

## Tightening the Existing Spec

SMART is not only for new requests. The team runs their existing lines through it too. Most pass. A few need tightening:

| Requirement | What fails | Rewritten version |
|---|---|---|
| FR-03 — "gives a **short** explanation of a general term" | Measurable — "short" is an opinion | "gives an explanation of **60 words or fewer**, then links it to the handbook rule" |
| FR-06 — "when a question is **unclear**, asks a clarifying question" | Specific — "unclear" is an opinion | "when a question refers to an assignment or exam **without naming it**, and the handbook has more than one, the assistant asks which one the student means" |
| NFR-05 — "answers use **plain language**" | Measurable — "plain" is an opinion | "answers explain any course term the handbook defines, and contain no terms the handbook does not use" |

Notice what happened to FR-06. "Unclear" became a precise situation you can recreate: ask "When is the assignment due?" when the handbook lists three assignments. That is something a tester can actually do.

---

## Words That Signal a Requirement Is Not Testable

Some words almost always mean a requirement needs another pass through SMART. When you see one, replace it:

| Weak word | Replace it with |
|---|---|
| short, brief, concise | A word or sentence limit |
| fast, quick, responsive | A time, plus a rate ("95% within 5 seconds") |
| upcoming, recent, soon | A time window ("next 14 days") |
| unclear, appropriate, relevant | The exact situation that counts |
| accurate, correct | What it must match ("matches the handbook exactly") |
| friendly, helpful | Specific observable checks ("includes a next step") |
| make sure, guarantee, always prevent | What the system can actually do |

---

## Test the Behaviour, Not the Exact Words

There is one trap that is specific to AI systems.

Once teams learn to make requirements precise, some go too far:

*"When the handbook does not cover a question, the assistant says exactly: 'The handbook does not cover this. Please contact your course coordinator.'"*

This is very testable — but it is the wrong thing to test. An AI model rarely produces the same wording twice. This requirement would fail on almost every run, even when the assistant behaves perfectly.

The fix is to test **facts and behaviour**, not wording:

*"…the assistant states that the handbook does not cover the question, and directs the student to the course coordinator."*

A reviewer can check both parts in any phrasing. The requirement is still testable — and now it tests what actually matters.

---

## Common Traps

**Writing the requirement first and the test "later"**
Later rarely comes. Write the test at the same time. If you cannot, the requirement is not finished.

**Skipping Achievable to keep a stakeholder happy**
It is tempting to leave "make sure they don't miss them" in the spec because the coordinator asked for it. A requirement the system cannot meet will either be quietly ignored or reported as a failure forever. Be honest early.

**Measuring what is easy instead of what matters**
Word count is easy to measure. Whether the answer is actually correct is harder. Relevant reminds you to test what matters to students, not just what is convenient.

**Locking in exact wording for an AI system**
Test facts and behaviours. Allow the wording to vary.

---

## Quick Recap

- A requirement is testable when you can write a test with three parts: a situation you can create, an outcome you can observe, and a pass/fail rule
- Write the test at the same time as the requirement — if you cannot write it, the requirement is not finished
- SMART turns a weak requirement into a testable one: Specific, Measurable, Achievable, Relevant, Time-bound
- Achievable keeps the spec honest — remove promises the system cannot keep, and say so openly
- Words like short, fast, upcoming, unclear and accurate signal that a requirement needs another pass
- For AI systems, test facts and behaviour, not exact wording

> **Interview tip:** If asked "how do you make a requirement testable?", walk through a real rewrite instead of listing SMART letters. Take something vague like "the system should remind users about deadlines", then show each step — what makes it specific, how you measure it, why "make sure they don't miss them" is not achievable, and what time window applies. Finish by writing the test out loud. Doing the rewrite live shows the interviewer you can actually use SMART, not just recite it.

---

## What Is Next

The next topic introduces **acceptance criteria**. The team now has requirements that can be tested — but who decides when the whole system is good enough to launch? Acceptance criteria answer that question, and they build directly on the tests you started writing in this topic.
