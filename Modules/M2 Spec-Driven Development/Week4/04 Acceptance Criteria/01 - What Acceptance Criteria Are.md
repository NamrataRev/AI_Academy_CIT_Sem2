# What Acceptance Criteria Are

---

When you submit an assignment, there is a marking rubric.

The rubric does not say "write a good assignment." It says: "Clearly states the problem — 10 marks. Provides a solution with justification — 20 marks. Includes at least two test cases — 10 marks. References formatted correctly — 5 marks." Each criterion is specific. Each one is either met or not. The marker does not decide whether you are a good student — they check whether you met each criterion.

Acceptance criteria work exactly this way. They are the marking rubric for a system — the specific, binary conditions that define when the system is accepted as working correctly.

---

## What Acceptance Criteria Are

Acceptance criteria are the conditions a system must meet to be considered complete and correct for a given requirement.

Three properties define good acceptance criteria:

**Binary** — each criterion is either met or not met. Pass or fail. There is no partial credit, no "mostly met", no judgment call. The condition either holds or it does not.

**Specific to one requirement** — each criterion tests one thing. Not "the system works well" — that is a requirement. The acceptance criteria are the specific conditions that prove the requirement is met.

**Written before building** — acceptance criteria are written when the requirement is written, not after the system is built. Written after building, they will reflect what was built — not what was needed.

---

## Requirements vs Acceptance Criteria — The Difference

This is where students often get confused. Here is the distinction:

A **requirement** describes what the system should do.
**Acceptance criteria** describe how you will know the system is doing it.

| Requirement | Acceptance Criteria |
|---|---|
| FR2: Every response contains an analogy, a definition, and a use case | ✅ An analogy is present in the response |
| | ✅ The analogy appears before the definition |
| | ✅ A technical definition is present |
| | ✅ A use case is present after the definition |
| | ✅ No other elements appear between analogy, definition, and use case |
| FR4: Every response is 120 words or fewer | ✅ Word count of response is ≤ 120 |
| FR3: Redirects out-of-scope questions | ✅ Response does not explain the out-of-scope topic |
| | ✅ Response states the topic is not yet covered |
| | ✅ Response suggests at least one covered topic instead |

One requirement can have multiple acceptance criteria. Each criterion tests one specific aspect of that requirement.

---

## Why Acceptance Criteria Matter

**They make requirements unambiguous**

A requirement says "every response contains an analogy." But what counts as an analogy? Is a code example an analogy? Is a definition-by-comparison an analogy? The acceptance criteria answer this — by specifying exactly what must be present and where.

**They become test cases directly**

Each acceptance criterion is a test. You run the system, look at the output, and check whether the criterion holds. The eval harness is built from acceptance criteria — each row in the scoring table is one criterion being checked.

**They define done**

When every acceptance criterion passes — the system is done. Not "looks good", not "seems to work" — done. This is what makes SDD rigorous. Done has a definition.

---

## Acceptance Criteria for the Study Assistant

Here is the complete set for three of the eight functional requirements:

```
FR2: Every response contains an analogy, a definition, and a use case.

AC2.1: The response contains text that functions as an analogy 
       (a comparison to a familiar real-world object or situation)
AC2.2: The analogy appears as the first element of the response
AC2.3: The response contains a technical definition of the concept
AC2.4: The definition appears after the analogy
AC2.5: The response contains at least one real-world use case
AC2.6: The use case appears after the definition
AC2.7: No additional structural elements appear between the three required parts

---

FR3: Out-of-scope questions are redirected.

AC3.1: When a student asks about a topic not in the covered list, 
       the response does not contain an explanation of that topic
AC3.2: The response contains a statement that the topic is not yet covered
AC3.3: The response contains the name of at least one covered topic 
       the student could explore instead
AC3.4: The response does not refuse or dismiss — tone remains helpful

---

FR4: Every response is 120 words or fewer.

AC4.1: Word count of the response body is ≤ 120
AC4.2: The word limit applies to all response types — 
       concept explanations, comparisons, and redirects
```

Notice how each acceptance criterion is binary — it either holds or it does not. AC2.2 does not say "the analogy should generally come first" — it says the analogy appears as the first element. Pass or fail.

---

## Quick Recap

- Acceptance criteria are the specific, binary conditions that define when a requirement is met
- Each criterion tests one thing — pass or fail, no judgment, no partial credit
- Requirements describe what the system should do; acceptance criteria describe how you know it is doing it
- One requirement can have multiple acceptance criteria — each one tests a different aspect
- Acceptance criteria written before building become test cases in the evaluation harness

---

## What Is Next

The next topic covers the Given-When-Then format — a structured way of writing acceptance criteria that makes them even clearer and directly usable as automated or manual test cases.
