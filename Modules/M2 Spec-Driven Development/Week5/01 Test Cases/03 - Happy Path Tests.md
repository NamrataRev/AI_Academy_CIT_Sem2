# Happy Path Tests

---

When a new phone is unboxed in a store, the sales assistant demonstrates it under ideal conditions.

Full battery. Strong WiFi. A polished demo app. Every feature works exactly as advertised. The customer is impressed.

What the demonstration does not show: what happens when the battery is at 3%. What happens in an area with no signal. What happens when the customer installs ten apps and the storage fills up.

The demo is the happy path. Everything works as expected, in the best conditions, with the most straightforward inputs. It is a necessary starting point — but it is not the full picture.

Happy path tests work the same way. They are essential. They are not sufficient.

---

## What a Happy Path Test Is

A happy path test is a test case where everything goes as expected.

The input is clear and unambiguous. The input is well within scope. The user is asking exactly what the system was designed to handle. No unusual phrasing. No edge cases. No attempts to push boundaries.

For the study assistant, a happy path test looks like this:

```
TC-HP1
Input: "What is a stack?"
Context: Context package fully loaded, fresh session
Expected:
  ✓ Response contains an analogy as the first element
  ✓ Analogy uses a physical object
  ✓ Response contains a technical definition after the analogy
  ✓ Response contains a use case after the definition
  ✓ Word count ≤ 120
  ✓ No Big O notation
  ✓ No recursion mentioned

TC-HP2
Input: "What is a queue?"
Expected: Same criteria as TC-HP1

TC-HP3
Input: "What is a binary search tree?"
Expected: Same criteria as TC-HP1

TC-HP4
Input: "What is a linked list?"
Expected: Same criteria as TC-HP1

TC-HP5
Input: "What is the difference between a stack and a queue?"
Expected:
  ✓ Response covers both structures
  ✓ Analogy present for each
  ✓ Word count ≤ 180 (comparison question limit)
  ✓ No Big O notation
  ✓ No recursion mentioned
```

Five happy path test cases. Each one is a direct, clear question about a covered topic in the most natural phrasing a student would use.

---

## Why Happy Path Tests Matter

Happy path tests establish the baseline. If the system cannot handle the most straightforward inputs correctly — nothing else matters. An AI assistant that fails on "What is a stack?" is not ready for any further testing.

Happy path tests also give you a reference point. When you make changes to the context package and re-run the harness, happy path tests tell you immediately whether the change broke the basic behaviour. This is regression testing — confirming that fixing one thing did not break something else.

---

## Why Happy Path Tests Are Not Sufficient

The study assistant is not only used by students who ask perfect questions in ideal conditions.

A student revising the night before the exam types quickly and makes mistakes. A student who is confused phrases their question in an unusual way. A student who has just come from a lecture asks about something that overlaps with a topic not yet covered.

Happy path tests do not cover any of these scenarios. If the harness only contains happy path tests, you are testing a demo — not a real system.

The pass rate on a happy path-only harness is almost always high. This is not because the system is reliable — it is because the tests were easy. A 15/15 pass rate on fifteen happy path tests tells you much less than a 13/15 pass rate on a mix of happy path, boundary, and adversarial tests.

---

## The Right Role for Happy Path Tests

Happy path tests should make up roughly one third of your total test cases — enough to establish the baseline and catch regressions, not so many that they crowd out the more revealing test types.

For a fifteen-input harness:
- 5 happy path tests — one per major topic in the covered syllabus
- 4 boundary tests — topics at the edge of scope, unusual phrasings
- 3 out-of-scope tests — topics not in the covered list
- 3 adversarial tests — politely-framed out-of-scope, constraint-crossing requests

This distribution gives you a meaningful picture of system reliability — not just a demonstration that it works in the best case.

---

## Quick Recap

- A happy path test is a test case where everything goes as expected — clear input, well within scope, most natural phrasing
- Happy path tests establish the baseline — if these fail, nothing else matters
- Happy path tests are not sufficient — they test a demo, not a real system
- Happy path tests should make up roughly one third of the total harness — enough to catch regressions, not so many that they crowd out more revealing tests

---

## What Is Next

The next topic covers edge case tests — the inputs that sit at the boundary of what the system is designed to handle, and why this is where most real-world failures occur.
