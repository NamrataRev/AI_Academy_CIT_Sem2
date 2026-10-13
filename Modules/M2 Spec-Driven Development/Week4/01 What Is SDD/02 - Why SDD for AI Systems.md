# Why SDD for AI Systems

---

Building a traditional software feature without a spec is risky. The feature might not do what was wanted. You fix it. You move on.

Building an AI system without a spec is a different kind of problem.

Traditional software does exactly what the code says. If the code is wrong, the behaviour is consistently wrong — the same wrong answer every time. You test it, spot the pattern, fix the code.

An AI system does not work this way. Given the same input twice, it may produce slightly different outputs. Given a slightly different input, it may produce a completely different output. The behaviour is probabilistic and context-dependent. Without a specification that defines what correct looks like — you have no way to know whether the system is working, failing occasionally, or failing most of the time on inputs you have not tested.

This is why SDD matters more for AI systems than for traditional software — not less.

---

## The Cost of Unclear Requirements in AI

When requirements are unclear in a traditional system, the cost is usually one thing built wrong that needs to be rebuilt.

When requirements are unclear in an AI system, the costs compound:

**You do not know what to test.** Without a specification, you test the inputs you thought of. The system passes. You deploy it. Users generate inputs you did not think of. The system fails. You had no way to know because you had no specification to test against.

**You cannot tell improvement from change.** You modify the context package. The responses feel different. Are they better or worse? Without a specification defining what better means, you cannot answer this question with evidence. You are guessing.

**Failure is invisible.** A traditional bug throws an error. An AI system with unclear requirements produces responses that look reasonable — but may consistently miss what was needed. Nobody knows because nobody defined what was needed.

**Evaluation is impossible.** The eval harness from Week 3 requires criteria to score against. Those criteria come from the specification. Without a specification, the harness has nothing to measure against.

---

## What Goes Wrong Without SDD — A Student Example

A student is building an AI study assistant. They write a context package, test it on a few questions, and it looks good. They share it with their study group.

Three days later, one friend says: "It explained graph traversal and I got confused because it used recursion." Another says: "I asked it to help me with my assignment and it basically wrote the answer for me." A third says: "The responses are way too long, I cannot fit them in my notes."

Three different failures. All preventable. None of them were caught because there was no specification.

If there had been a specification, it would have said:
- Do not explain topics outside the covered syllabus (catches the recursion problem)
- Do not produce complete assignment answers (catches the academic integrity problem)
- Keep all responses under 120 words (catches the length problem)

These constraints existed in the context package. But without a specification that formally defines them as requirements — and acceptance criteria that define what a violation looks like — they were guidelines, not contracts.

---

## SDD Gives You Three Things

**Something to build to.** A specification answers the question: when is this done? Without it, done means "when it seems okay" — which is not the same as done.

**Something to test against.** Every test case needs an expected outcome. The specification provides that outcome. The eval harness tests whether the system meets it.

**Something to communicate with.** When you share a system with someone — a teammate, a lecturer, a user — the specification tells them what the system is supposed to do. They can evaluate it against that, not against their own unarticulated expectations.

---

## Quick Recap

- AI systems are harder to evaluate than traditional software because behaviour is probabilistic — you need a specification to know what correct looks like
- Without a spec, you cannot know what to test, cannot tell improvement from change, cannot detect invisible failures, and cannot run a meaningful evaluation
- SDD gives you something to build to, something to test against, and something to communicate with
- The evaluation harness requires a specification — the criteria come from the spec

---

## What Is Next

The next topic covers what happens when informal specs are used — the specific ways vague or missing requirements cause problems, using real examples from systems like the ones you are building.
