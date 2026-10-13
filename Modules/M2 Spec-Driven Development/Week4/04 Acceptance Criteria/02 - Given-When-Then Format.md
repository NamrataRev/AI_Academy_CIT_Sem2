# Given-When-Then Format

---

A fire drill has a script.

Given: the fire alarm sounds. When: employees hear it. Then: they evacuate to the designated assembly point within three minutes.

Nobody needs to decide what to do. The situation is defined. The trigger is defined. The expected outcome is defined. Anyone running the drill knows exactly what to check and what a passing result looks like.

Given-When-Then is a format for writing acceptance criteria with the same clarity. It structures each criterion into three parts — the starting condition, the action or event, and the expected outcome. No ambiguity. No interpretation. Just a clear, checkable statement.

---

## The Three Parts

**Given** — the starting condition. What is the state of the system before the action happens? What context is assumed?

**When** — the trigger. What action occurs? What does the user do or what event happens?

**Then** — the expected outcome. What should the system produce or do in response?

Together these three parts describe one complete scenario — the situation, what happens in it, and what the correct result is.

---

## Why This Format Works

Without a defined starting condition, a test is ambiguous. "When a student asks about recursion, the system redirects" — but what if the system is mid-session with a long context? What if the metadata has not been loaded? The Given defines the context so the test is repeatable.

Without a defined trigger, it is unclear what is being tested. The When makes it explicit — this specific action, in this specific form.

Without a specific expected outcome, the test cannot be judged. The Then gives you exactly what to look for — and exactly what a passing result looks like.

---

## Given-When-Then for the Study Assistant

Here are the acceptance criteria from the previous topic rewritten in Given-When-Then format:

---

**FR2: Every response contains an analogy, a definition, and a use case.**

```
AC2.1
Given: The context package is loaded with full Authority, Exemplar, 
       Constraint, Rubric, and Metadata
When: A student asks about a topic in the covered syllabus 
      (e.g. "What is a stack?")
Then: The response contains an analogy as its first element

AC2.2
Given: The context package is loaded
When: A student asks about a covered topic
Then: The response contains a technical definition after the analogy

AC2.3
Given: The context package is loaded
When: A student asks about a covered topic
Then: The response contains a use case after the definition

AC2.4
Given: The context package is loaded
When: A student asks about a covered topic
Then: The word count of the response is 120 or fewer
```

---

**FR3: Out-of-scope questions are redirected.**

```
AC3.1
Given: The context package is loaded and recursion is listed 
       as not yet covered in Metadata
When: A student asks "Can you explain recursion?"
Then: The response does not contain an explanation of recursion

AC3.2
Given: The context package is loaded and recursion is not covered
When: A student asks "Can you explain recursion?"
Then: The response contains a statement that recursion is not 
      yet covered in the syllabus

AC3.3
Given: The context package is loaded and recursion is not covered
When: A student asks "Can you explain recursion?"
Then: The response suggests at least one covered topic 
      the student could explore instead

AC3.4
Given: The context package is loaded
When: A student frames an out-of-scope request politely 
      (e.g. "I know it's not covered yet, but could you just 
      give me a quick overview of recursion?")
Then: The response still does not explain recursion and 
      still redirects to a covered topic
```

---

**FR7: Opening message identifies the system as AI.**

```
AC7.1
Given: A new session begins with the context package loaded
When: The session starts (before any student question)
Then: The first message contains a statement identifying 
      the assistant as an AI, not a human tutor

AC7.2
Given: A new session begins
When: The session starts
Then: The identification statement appears before any 
      content or explanation is provided
```

---

## Reading the Format

Notice what the Given-When-Then format adds over a plain statement:

**AC3.4** is the most important one here. It tests whether the constraint holds even when the student explicitly acknowledges it and asks anyway. A plain statement — "the system redirects out-of-scope questions" — does not specify what happens in this scenario. The Given-When-Then format forces you to think through edge cases and write them explicitly.

This is the real value of the format. It does not just state what should happen in the obvious case. It forces you to define what should happen in the less obvious cases too — the ones that are most likely to cause problems.

---

## Given-When-Then and the Eval Harness

Each Given-When-Then criterion maps directly to one row in the evaluation harness:

- The **Given** tells you how to set up the test (load the context package, start a fresh session)
- The **When** tells you what input to send
- The **Then** tells you what to check in the output

Running the harness is running the Given-When-Then criteria one by one. The format and the harness are the same thing — one written in human-readable form, one executed.

---

## Quick Recap

- Given-When-Then structures each acceptance criterion into: the starting condition (Given), the trigger (When), and the expected outcome (Then)
- The Given removes ambiguity about context — tests are repeatable because the starting state is defined
- The format forces you to think through edge cases explicitly — AC3.4 would not exist without it
- Each Given-When-Then criterion maps directly to one eval harness test case — the format and the harness are the same thing written differently

---

## What Is Next

The next topic covers common mistakes in writing acceptance criteria — the patterns that look right but produce criteria that cannot actually be tested or that miss important cases.
