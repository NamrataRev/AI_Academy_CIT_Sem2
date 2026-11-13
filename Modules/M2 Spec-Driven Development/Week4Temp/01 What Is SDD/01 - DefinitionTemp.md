# What Is SDD — Definition

---

Imagine you ask a friend to help you rearrange your room.

You say: "Just make it better." They move everything around. You come back and hate it. They spent two hours on something that was not what you wanted — and neither of you knew it until the end.

Now imagine you said: "Put the desk by the window, the bed against the left wall, and make sure I can open the wardrobe without hitting the desk." They do exactly that. You come back and it is exactly right.

Notice what changed between the two attempts. Your friend did not get more skilled. The instructions got clearer. The second version had three things the first did not:

- **A specific outcome** — desk by the window, bed against the left wall
- **A constraint** — the wardrobe must still open
- **A way to check** — you can walk in and confirm each point in ten seconds

The outcome was defined before the work started. That is the whole idea.

Spec-Driven Development is this. Define what you are building before you build it — in enough detail that when it is done, you can check whether it is actually done.

---

## What SDD Is

**Spec-Driven Development (SDD)** is a discipline where you write a specification — a precise description of what the system should do — before writing any code or building anything.

The specification is not a rough idea or a list of features. It is a **contract**. It defines four things:

| Part of the contract | The question it answers | Example (course FAQ chatbot) |
|---|---|---|
| **What the system does** | What is it responsible for? | Answers questions about deadlines and grading using the course handbook |
| **What it does not do** | Where does its job end? | Does not answer general knowledge questions or give personal advice |
| **How you will know it is working** | What does "correct" look like? | "When is Assignment 2 due?" returns the handbook date, with the section cited |
| **What counts as a failure** | What must never happen? | Any date or rule that is not in the handbook |

The second row is the one beginners skip most often. Saying what a system does *not* do feels unnecessary — until the system starts doing it.

### Idea vs feature list vs specification

The difference is easiest to see side by side:

| Level | Example | Can you test it? |
|---|---|---|
| **Rough idea** | "A chatbot that helps students" | No — helps with what? |
| **Feature list** | "Answers questions, cites sources, is friendly" | Partly — which questions? What counts as a source? |
| **Specification** | "Answers deadline and grading questions from the handbook only. Cites the section for every answer. Refuses anything outside the handbook." | Yes — every line can be checked |

A good test for whether something is a spec: **could two different people read it and agree on whether the finished system passes?** If not, it is still an idea.

### What a small spec looks like

A spec does not have to be a 50-page document. For a small system it can fit on one page:

```text
SYSTEM: Course FAQ assistant

DOES:
- Answers questions about schedule, deadlines and grading
  using only the uploaded course handbook
- Cites the handbook section for every answer

DOES NOT:
- Answer questions about topics outside the handbook
- Advise students on personal decisions (e.g. whether to drop a course)

WORKING CORRECTLY WHEN:
- "When is Assignment 2 due?" → handbook date, section cited
- "What is the capital of France?" → polite refusal

FAILURE:
- Any answer containing a date or rule not in the handbook
- Any answer with no citation
```

Every line here is something you can check by asking the system a question and reading the answer.

### Why write it first

Writing this contract before building has one fundamental benefit: it forces you to think through what you actually want before you commit to building it.

Most problems in software — and in AI systems — come from **unclear requirements that nobody noticed were unclear until the system was half-built.**

Take the rough idea "answer student questions." It sounds clear. Then you start building and the questions appear:

- What if the handbook does not mention late penalties — should it guess or refuse?
- What if a student asks about a deadline that was changed by email?
- Should it answer in one line or explain the policy?

Each of these is a decision. If you make it while writing the spec, it takes a minute. If you discover it after building, it means rework — and sometimes you discover it only when a student gets a wrong answer.

---

## Why It Is Called Spec-Driven

The specification **drives** everything that comes after it. Each step takes its direction from the spec:

```text
SPEC → TESTS → IMPLEMENTATION → EVALUATION

SPEC
What should the system do, not do, and how will we know?

TESTS
Questions and expected answers written directly from the spec.
"Working correctly when..." becomes a test case.

IMPLEMENTATION
The system is built to pass those tests —
prompts, documents, settings, or code.

EVALUATION
The finished system is checked against the spec.
Every "does", "does not" and "failure" line is verified.
```

### Why the order matters

When you write the spec first, the spec is **honest** — it reflects what you actually need, not what turns out to be easy to build.

When you write the spec after building, it reflects what you built — which may or may not be what was needed.

Here is how that goes wrong in practice. A team builds the FAQ chatbot first. It handles deadline questions well but gives unreliable answers about grading. When they finally write the spec, they quietly leave grading out — and the spec now says the system is "working." Nobody decided grading did not matter. It just disappeared because it was hard.

This is called **moving the goalposts**: changing the definition of success to match the result. A spec written first prevents it, because the goalposts were fixed before anyone started kicking.

| Build first, spec later | Spec first, build after |
|---|---|
| Spec describes what was built | Spec describes what was needed |
| Gaps are hidden | Gaps are visible as failing tests |
| "Done" means "it runs" | "Done" means "it passes every line of the spec" |

---

## SDD Is Not Just for Code

This is important for this course.

SDD applies to any system you are designing — including AI systems built with **context packages**. A context package is an implementation: the instructions, documents and examples you give a model so that it behaves a certain way. It does the same job that code does in traditional software.

That means a context package needs a specification just as much as code does. Before writing it, you need to answer:

- What should this system do?
- What should it not do?
- How will you know it is working?

Without those answers, you are writing instructions for a model the same way the first friend rearranged your room — doing a lot of work toward an outcome nobody defined.

### You have already been doing this

You have been practising parts of SDD informally in earlier weeks. Each tool you have used maps to a piece of a specification:

| What you have already built | What it is in SDD terms | Why |
|---|---|---|
| **Evaluation harness criteria** | Acceptance criteria | They define what a correct answer looks like — the "working correctly when" part |
| **Risk map** | A partial requirements document | It lists what must not go wrong — the "failure" and "does not" parts |
| **Documentation template** | A specification format | It gives a fixed structure for describing what a system does |

The pieces are there. What has been missing is putting them together, in the right order, before building starts.

This week makes it explicit and formal — so you can apply it consistently to every system you build.

---

## Quick Recap

- SDD is the discipline of writing a precise specification **before** building anything
- The specification is a contract with four parts: what the system does, what it does not do, how you will know it is working, and what counts as a failure
- A real spec is testable — two people reading it should agree on whether the system passes
- The order matters: spec first, then tests, then implementation, then evaluation. Writing the spec afterwards lets the goalposts move
- Most failures come from unclear requirements discovered too late — the spec surfaces them early, when they are cheap to fix
- SDD applies to AI systems, context packages and backend services — not just code. Your evaluation criteria, risk map and documentation template are already pieces of a spec

> **Interview tip:** If asked "what is spec-driven development?", do not stop at "writing requirements first." Say that a spec is a testable contract — what the system does, what it does not do, and how you verify it — and that it drives tests, implementation and evaluation in that order. Then add that it applies to AI systems too: a prompt or context package is an implementation and needs a spec before it is written. That last point shows you understand where the field is going.

---

## What Is Next

The next topic covers why SDD matters specifically for AI systems — where the cost of unclear requirements is higher than in traditional software, and what goes wrong when you build first and specify later.
