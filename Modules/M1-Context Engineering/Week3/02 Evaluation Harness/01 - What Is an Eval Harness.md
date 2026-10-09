# What Is an Eval Harness

---

Imagine you are a professor setting a standardised test.

You do not evaluate each student differently — you use the same questions, the same marking scheme, and the same criteria for everyone. Every student is measured against the same standard. The results are comparable. If one student does badly, you know exactly which questions they failed and why.

An evaluation harness does the same thing for a context package. Instead of checking responses one at a time by feel — "this seems good, this seems off" — you run the same set of inputs through the package every time, score every response against defined criteria, and get a result you can compare across versions.

It turns a subjective judgment into a measurable process.

---

## What an Eval Harness Is

An evaluation harness is a structured testing process for a context package. It has three components:

**A fixed set of test inputs** — questions or prompts that cover the range of things the system will actually encounter. Not just easy questions. A mix of typical inputs, edge cases, and inputs designed to trigger potential failure points.

**Expected outputs** — for each test input, what does a good response look like? Not the exact words — but the criteria a good response must meet. Does it have an analogy? Is it under 120 words? Does it redirect correctly for out-of-scope questions?

**A scoring method** — a clear way to decide whether each response passed or failed each criterion. Applied consistently to every response, every time.

Together these three components let you run the harness, get a score, change the context package, run it again, and see whether the score improved.

---

## Why This Matters

Without an evaluation harness, testing a context package looks like this: you ask a few questions, the responses look reasonable, you decide it is good enough.

The problem: "looks reasonable" is not reproducible. The next person who tests it might ask different questions and reach a different conclusion. You cannot tell whether a change you made improved or degraded the package. You cannot catch regressions — cases where a fix for one problem introduced a new problem elsewhere.

With an evaluation harness, testing looks like this: you run fifteen fixed inputs, score each response against defined criteria, get a pass rate. You make a change. You run the same fifteen inputs again. The pass rate either went up or went down. You know exactly whether the change helped.

This is the difference between testing by instinct and testing by evidence.

---

## What an Eval Harness Is Not

An eval harness is not an automated system — at least not for the purposes of this course. You do not need to write code to run one.

A simple eval harness for a context package can be a table:

| # | Input | Criterion 1: Analogy present? | Criterion 2: Under 120 words? | Criterion 3: Use case present? | Criterion 4: No constraint violations? | Pass? |
|---|---|---|---|---|---|---|
| 1 | What is a stack? | ✅ | ✅ | ✅ | ✅ | ✅ |
| 2 | Explain recursion | ✅ | ✅ | ✅ | ❌ (recursion explained) | ❌ |

You fill in the table manually. You run it before and after changes. You track the pass rate over time.

Simple. No code required. But rigorous — because you are applying the same criteria to every response, every time.

---

## Quick Recap

- An evaluation harness is a structured testing process: fixed inputs, expected outputs, consistent scoring
- It turns "this looks reasonable" into a measurable pass rate that can be tracked across versions
- It does not need to be automated — a table with fixed inputs and criteria, filled in manually, is a valid eval harness
- Without a harness, you cannot tell whether changes improve or degrade a context package

---

## What Is Next

The next topic covers how to build the input set and expected outputs — the two hardest parts of setting up an eval harness, and how to choose inputs that actually test what matters.
