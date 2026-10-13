# What Is SDD — Definition

---

Imagine you ask a friend to help you rearrange your room.

You say: "Just make it better." They move everything around. You come back and hate it. They spent two hours on something that was not what you wanted — and neither of you knew it until the end.

Now imagine you said: "Put the desk by the window, the bed against the left wall, and make sure I can open the wardrobe without hitting the desk." They do exactly that. You come back and it is exactly right. Because the outcome was defined before the work started.

Spec-Driven Development is this. Define what you are building before you build it. In enough detail that when it is done, you can check whether it is actually done.

---

## What SDD Is

Spec-Driven Development is a discipline where you write a specification — a precise description of what the system should do — before writing any code or building anything.

The specification is not a rough idea or a list of features. It is a contract. It defines:

- What the system does
- What it does not do
- How you will know when it is working correctly
- What counts as a failure

Writing this contract before building has one fundamental benefit: it forces you to think through what you actually want before you commit to building it. Most problems in software — and in AI systems — come from unclear requirements that nobody noticed were unclear until the system was half-built.

---

## Why It Is Called Spec-Driven

The specification drives everything. The spec comes first. Then the tests — written to verify the spec. Then the implementation — built to pass the tests. Then the evaluation — checking the implementation against the spec.

This order matters. When you write the spec first, the spec is honest — it reflects what you actually need, not what turns out to be easy to build. When you write the spec after building, it reflects what you built — which may or may not be what was needed.

---

## SDD Is Not Just for Code

This is important for this course.

SDD applies to any system you are designing — including AI systems built with context packages. A context package is an implementation. Before writing it, you need a specification: what should this system do, what should it not do, and how will you know it is working?

You have already been doing this informally. The evaluation harness criteria are acceptance criteria. The risk map is a partial requirements document. The documentation template is a specification format.

This week makes it explicit and formal — so you can apply it consistently to every system you build.

---

## Quick Recap

- SDD is the discipline of writing a precise specification before building anything
- The specification is a contract — what the system does, what it does not do, and how you will know it is working
- The order matters: spec first, then tests, then implementation, then evaluation
- SDD applies to AI systems, context packages, and backend services — not just code

---

## What Is Next

The next topic covers why SDD matters specifically for AI systems — where the cost of unclear requirements is higher than in traditional software, and what goes wrong when you build first and specify later.
