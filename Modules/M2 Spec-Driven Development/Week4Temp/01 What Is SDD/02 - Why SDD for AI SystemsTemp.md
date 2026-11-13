# Why SDD for AI Systems

---

In the last topic you met the course FAQ assistant — a chatbot that answers student questions about deadlines and grading using the course handbook. You also saw what its spec could look like.

Now imagine the team had skipped the spec.

They upload the handbook, write a short instruction — "You are a helpful assistant for students on this course" — and run a demo. It goes well. "When is Assignment 2 due?" gets the right date. "How is the final grade calculated?" gets the right breakdown. Everyone is impressed. The chatbot goes live.

Three weeks later, a student asks: "What is the penalty for submitting late?"

The handbook does not say. The chatbot answers anyway: *"Late submissions lose 10% per day."* It sounds official. The student plans around it. The real policy, sent by email in week one, was 5% per day with a 48-hour cap.

Nothing crashed. No error appeared. The answer was fluent, confident and wrong — and nobody on the team had ever decided what the chatbot should do when the handbook did not have the answer.

Remember the friend rearranging your room? An AI model is that friend — except it will never tell you it guessed. It fills every gap in your instructions with its own best idea, and presents the result as if it were exactly what you asked for.

That is why SDD matters more for AI systems than almost anywhere else.

---

## Why AI Systems Are Different

In traditional software, behaviour comes from code. A developer writes the logic line by line. If something is not written, it does not happen.

In an AI system, behaviour comes from **instructions and context** — a prompt, some documents, a few examples. Everything you did not write down, the model decides for itself.

That difference creates four problems traditional software does not have:

| | Traditional software | AI system |
|---|---|---|
| **Same input, same output?** | Yes — the same input always gives the same result | Not always — the same question can get different answers |
| **How does it fail?** | Loudly — an error message, a crash, a blank screen | Quietly — a confident, well-written answer that is wrong |
| **What inputs can it get?** | Limited — buttons, forms, fixed fields | Unlimited — users type anything, in any wording |
| **Who fills the gaps?** | Nobody — unwritten behaviour does not exist | The model — unwritten behaviour gets invented |

The last row is the most important one. In normal code, a gap in the requirements usually shows up as a missing feature. In an AI system, a gap shows up as **made-up behaviour** — and it looks exactly like real behaviour.

The late-penalty answer is a perfect example. The team never wrote "if the handbook does not say, refuse." So the model did what it does best: it produced a plausible answer.

---

## The Cost of Unclear Requirements Is Higher

Every system has unclear requirements somewhere. The question is how expensive they are to find.

```text
TRADITIONAL SOFTWARE — unclear requirement
Requirement missing → feature does not work → error is visible
→ developer notices during testing → fixed before release

AI SYSTEM — unclear requirement
Requirement missing → model invents behaviour → answer looks correct
→ passes a quick demo → goes live → a student finds it
→ by acting on the wrong answer
```

In traditional software, the system usually tells you something is wrong. In an AI system, the person who discovers the problem is often the **user** — and they discover it by being harmed by it.

For the FAQ assistant, that means a student losing marks on a late submission. For a medical or financial AI system, the cost is far higher.

A spec moves that discovery to the cheapest possible moment: **before anything is built**. Writing "What should happen when the handbook does not answer the question?" takes one minute. Finding out the answer after a student complains takes much longer — and costs trust that is hard to get back.

---

## What Goes Wrong When You Build First

Teams that build AI systems without a spec almost always fall into the same loop. It is worth knowing the pattern so you can recognise it.

**Step 1 — The demo works.**
The team tests with a few easy questions they thought of themselves. Everything passes. Easy questions are exactly the ones a model handles well.

**Step 2 — Real users find a problem.**
The late-penalty answer is reported. The team adds a line to the instructions: *"Only answer from the handbook."*

**Step 3 — The fix breaks something else.**
Now the chatbot refuses "Can you explain what a weighted grade means?" — a reasonable question that needs a little general explanation. Students complain it has become useless.

**Step 4 — Another fix.**
The team adds: *"Be helpful and explain concepts when needed."* Refusals drop. But guessing comes back, because "be helpful" now competes with "only from the handbook."

**Step 5 — Nobody can tell if it is better.**
After five rounds of changes, the team cannot say whether the chatbot is better or worse than it was in week one. There is no fixed definition of "better" to measure against.

This loop is often called **prompt whack-a-mole**: every fix pushes the problem somewhere else. The team is not short of effort. They are short of a **target**.

You have seen this risk before. In the RAG module, the advice was to fix one thing at a time and test the same questions before and after every change. That advice only works if someone has decided what the right answers are. That decision is the spec.

---

## How a Spec Changes the Story

Now replay the same chatbot, built spec-first. Before writing any instructions, the team writes down a few decisions:

```text
DOES:
- Answers deadline and grading questions from the handbook,
  with the section cited
- Explains general terms (e.g. "weighted grade") briefly,
  then links the explanation to the handbook rule

DOES NOT:
- State any policy, date or penalty that is not in the handbook

WHEN THE HANDBOOK DOES NOT ANSWER:
- Says the handbook does not cover it
- Directs the student to the course coordinator

FAILURE:
- Any penalty, date or rule not found in the handbook
```

Every problem from the build-first story now has an answer **before** it happens:

| Problem in the build-first story | What the spec already decided |
|---|---|
| Invented late penalty | Not in the handbook → refuse and redirect |
| Refusing "what is a weighted grade?" | General terms may be explained briefly |
| "Only from handbook" vs "be helpful" conflict | The spec states exactly where the boundary is |
| No way to know if a change helped | Each spec line becomes a test question with an expected answer |

The late-penalty question becomes a **test case** on day one. The team asks it before launch, sees the chatbot invent "10% per day", and fixes it — before a single student sees it.

The model did not change. The team's clarity did.

---

## Quick Recap

- In AI systems, behaviour comes from instructions and context — anything you do not specify, the model invents
- AI systems differ from traditional software in four ways: answers can vary, failures are quiet, inputs are unlimited, and gaps get filled with made-up behaviour
- Unclear requirements cost more in AI because the wrong answer looks right — the user is often the one who finds it
- Building first leads to prompt whack-a-mole: each fix breaks something else, and nobody can tell if the system is improving
- A spec gives the team a fixed target — every decision is made upfront, and every spec line becomes a test

> **Interview tip:** If asked "why do AI systems need specifications?", avoid a generic answer like "requirements are always important." Say that AI systems fail **quietly** — a model fills gaps in its instructions with plausible behaviour, so a missing requirement shows up as a confident wrong answer instead of an error. Then explain that without a spec, prompt changes become trial and error because there is no fixed definition of "correct" to test against. Giving a concrete example — like a chatbot inventing a policy it was never given — makes the answer memorable.

---

## What Is Next

The next topic looks at informal specs — the short, everyday-language briefs most projects start with — and shows exactly where they break down, using the same FAQ assistant to test them.
