# Edge-Case Testing

---

A light switch works perfectly in the middle of the day.

But what about at 3am when you are half asleep and press it with your elbow? What about when the power flickers? What about when a child presses it repeatedly thirty times in a row?

The switch was designed for normal use. Edge cases are everything outside normal use — the unusual, the unexpected, the boundary conditions that real users will eventually produce, even without meaning to.

A context package that only works in normal conditions is not reliable. Edge-case testing finds where normal ends and unreliable begins — so you can either fix it or document it honestly.

---

## What Edge Cases Are for a Context Package

Edge cases are inputs that sit at or near the boundary of what the package is designed to handle.

Not completely out of scope — those are just out-of-scope inputs. Not adversarial — those are deliberate attacks. Edge cases are the grey area: inputs that are almost in scope, almost too complex, almost too simple, or phrased in a way the package was not explicitly designed for.

For the study assistant:

- A question about a topic covered in class but not listed in Metadata yet
- A question that combines two covered topics in a way that requires a longer-than-usual response
- A very simple question from a concept that is technically covered but rarely asked about
- A question phrased entirely in informal language — slang, abbreviations, incomplete sentences
- A question that references something outside the course but uses course vocabulary

None of these are attacks. They are just the natural variation in how real students ask questions.

---

## How to Find Edge Cases

**Work outward from the boundaries of your Metadata**

The Metadata defines what is covered and what is not. Edge cases live right at that boundary.

If trees are covered but graphs are not — *"what is the difference between a tree and a graph?"* is an edge case. It requires discussing both sides of the boundary.

If Big O notation is excluded — *"is BST search fast?"* is an edge case. Answering it meaningfully without using notation is harder than a straightforward concept question.

**Vary the phrasing of normal questions**

Take a question that passes the harness cleanly. Rephrase it five different ways:

*"What is a stack?"* →
- *"Can u explain stacks?"*
- *"How does a stack work?"*
- *"I don't get stacks, help"*
- *"Stack — what is it"*
- *"Tell me about the stack data structure"*

Do all five produce responses that meet the rubric criteria? If one phrasing fails, the Authority or Rubric may be too brittle — calibrated to a specific phrasing style rather than to the underlying question.

**Combine covered topics**

Questions that span two covered topics are harder than single-topic questions.

*"How do stacks and queues differ, and when would you use a BST instead of either?"* — this is three topics in one question. The Rubric says analogy, definition, use case — but for three concepts, that structure needs interpretation.

---

## What to Do With Edge Case Results

**If the package handles the edge case well** — document it in the Known Limitations section as a confirmed working boundary. *"Package handles informal phrasing without degradation — tested with five rephrasing variants."*

**If the package fails the edge case** — decide: fix or document?

Some edge case failures are worth fixing. If informal phrasing consistently breaks the rubric structure, strengthen the Authority to explicitly address phrasing variation.

Some edge case failures are acceptable limitations. If a three-topic combination question produces a response that is slightly over the word limit, that may be an acceptable trade-off — documented in Known Limitations, not necessarily fixed.

The decision depends on how often this edge case will appear in real use. If it is rare and the failure is minor — document it. If it will appear frequently and the failure is significant — fix it.

---

## Documenting Edge Case Results

Add a section to the context package documentation:

```
EDGE CASE RESULTS:

Tested: 12 edge cases across four categories
Pass rate: 9/12 (75%)

Failures:
1. Three-topic combination questions exceed 120-word limit 
   (appeared in 2/3 combination questions tested)
   Decision: accepted limitation — document to users that 
   combination questions may produce longer responses

2. Informal phrasing with abbreviations (e.g. "u", "rn", "lol") 
   occasionally produces responses that drop the analogy structure
   Decision: fixed — added to Authority: "maintain response 
   structure regardless of how informally the question is phrased"

3. Questions referencing the upcoming exam ("will this be on 
   the exam?") produce inconsistent responses
   Decision: fixed — added to Constraint: "do not speculate 
   about exam content; redirect to the concept being asked about"
```

This documentation makes the package's behaviour transparent — for you, for your teammates, and for anyone who uses or maintains it later.

---

## Quick Recap

- Edge cases are inputs at the boundary of what the package is designed to handle — not attacks, but the natural variation real users produce
- Find them by working outward from Metadata boundaries, varying the phrasing of normal questions, and combining covered topics
- For each failure: decide whether to fix it or document it as an accepted limitation — based on how often it will appear and how significant the failure is
- Document all edge case results in the context package documentation — what was tested, what passed, what failed, and what was done about it

---

## What Is Next

The next topic introduces context engineering patterns — a catalogue of proven approaches for structuring context packages for different types of tasks, so you do not have to design from scratch every time.
