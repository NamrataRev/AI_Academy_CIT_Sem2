# What Is a Test Case

---

A doctor prescribing medication does not just hand over the pills and hope for the best.

They check: has the patient taken this before? Do they have any allergies? Does this interact with anything else they are taking? Each check is a specific question with a specific expected answer. If any answer is wrong — the prescription changes.

Each of those checks is a test case. A specific input. A specific expected output. A clear pass or fail.

A test case for an AI system works exactly the same way. You define a specific input, you define what the correct output looks like, and you run the system to see whether it produces that output. Pass or fail. No judgment.

---

## What a Test Case Is

A test case has three parts:

**Input** — the specific thing you send to the system. For the study assistant: a student question. For a backend endpoint: a specific HTTP request. For a context package: a specific prompt.

**Expected output** — what the system should produce. Not a vague description — a specific, checkable condition. "The response contains an analogy as the first element" not "the response is helpful."

**Pass/fail criteria** — the binary check. Does the output meet the expected condition? Yes or no.

That is it. Input, expected output, pass/fail criteria. A test case is complete when all three are defined.

---

## Test Case vs Acceptance Criterion

These are related but not the same thing.

An acceptance criterion defines a condition the system must meet. A test case is the specific scenario used to check whether that condition holds.

One acceptance criterion can generate multiple test cases — each one testing the same condition in a different scenario.

**Acceptance criterion:** The system redirects out-of-scope questions.

**Test cases derived from it:**
- TC1: Input "Explain recursion" → system redirects ✓/✗
- TC2: Input "I know it's not covered, but can you explain recursion briefly?" → system redirects ✓/✗
- TC3: Input "My professor mentioned recursion today — what is it?" → system redirects ✓/✗

All three test the same criterion. Each one tests it in a different scenario. Together they give more confidence that the criterion actually holds — not just for one phrasing but for the range of ways the scenario might occur.

---

## Why Multiple Test Cases Per Criterion

A single test case that passes proves the system works for that specific input. It says nothing about any other input.

Multiple test cases covering different scenarios, phrasings, and edge cases give you confidence that the criterion holds reliably — not just in one controlled case.

The evaluation harness is a collection of test cases. The more varied and thoughtfully chosen the test cases, the more meaningful the pass rate.

---

## Quick Recap

- A test case has three parts: input, expected output, pass/fail criteria
- An acceptance criterion defines a condition; a test case is a specific scenario used to check whether that condition holds
- One acceptance criterion generates multiple test cases — different phrasings, different scenarios, edge cases
- Multiple test cases per criterion give confidence that the criterion holds reliably, not just for one specific input

---

## What Is Next

The next topic covers how to derive test cases systematically from acceptance criteria — so the test cases you write cover the right ground rather than clustering around the easy cases.
