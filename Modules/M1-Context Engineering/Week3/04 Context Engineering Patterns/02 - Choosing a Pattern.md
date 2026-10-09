# Choosing a Pattern

---

A doctor does not prescribe the same treatment for every patient.

They ask questions first. What are the symptoms? How long has this been happening? What has already been tried? The answers point toward the right treatment. The same symptom in two different patients might need two different approaches.

Choosing a context engineering pattern works the same way. You ask questions about the task, the audience, and the constraints. The answers point toward the right pattern. The same type of system built for two different audiences might need two different patterns.

This topic gives you the questions to ask — and shows how the answers map to the patterns from the previous topic.

---

## The Four Questions

**Question 1 — How well-defined is the output?**

Can you describe precisely what a good response looks like — structure, length, format — without needing to show an example?

*Yes, very precisely* → Zero-shot may be enough. A well-written Rubric can carry the calibration.

*Somewhat, but hard to describe exactly* → Few-shot. Show two or three examples of what you mean. Demonstration beats description when precision is hard to articulate.

*It depends on the reasoning process, not just the output* → Chain-of-thought. The output quality depends on showing the steps, not just producing a result.

---

**Question 2 — How sensitive is the domain?**

Are there topics, phrasings, or actions where crossing a boundary has serious consequences?

*Yes — specific things must never happen* → Role + Constraint pattern. The constraint list needs to be detailed and prioritised. The Authority must explicitly name what the model is not.

*No — the risks are low and the task is routine* → Zero-shot or Few-shot. Heavy constraint lists are unnecessary overhead for low-risk tasks.

---

**Question 3 — How much does the audience vary?**

Will the same context package serve one specific person, a consistent group, or widely different users?

*One specific person with known preferences and history* → Persona with rich Metadata. The package is worth personalising because the same person will use it many times.

*A consistent group with known shared characteristics* → Few-shot or Zero-shot with well-defined Metadata covering the group's shared level and background.

*Many different users with unknown characteristics* → Keep Metadata general. Use Zero-shot or Few-shot with Authority that defines the broadest reasonable audience. Avoid assumptions that will not hold across the full user range.

---

**Question 4 — How quickly does the context change?**

Does the Metadata need to be updated frequently — as the course progresses, as the user's understanding develops, as the situation evolves?

*Frequently — weekly or more* → Avoid Persona with rich Metadata unless you commit to updating it. Stale detailed Metadata is worse than general Metadata. Use a simpler pattern with lighter Metadata.

*Rarely — the context is stable* → Any pattern works. Richer Metadata is worth the setup time when it will stay accurate for a long time.

---

## A Decision Guide

| Situation | Recommended pattern |
|---|---|
| Task is narrow, output is precisely definable | Zero-shot |
| Output is hard to describe but easy to show | Few-shot |
| Task requires visible reasoning to be trustworthy | Chain-of-thought |
| Domain is sensitive with hard boundaries | Role + Constraint |
| Single known user with history and preferences | Persona with rich Metadata |
| Group of users with consistent characteristics | Few-shot with shared Metadata |
| Output format matters more than anything else | Few-shot (exemplars calibrate format best) |
| Speed of setup matters, task is low-risk | Zero-shot |

---

## An Example — Choosing for the Study Assistant

The study assistant for the BTech DSA course. Run through the four questions:

**How well-defined is the output?**
Precisely: analogy, definition, use case — in that order, under 120 words. Easy to specify without examples. But examples would still add calibration for tone and analogy style.
→ Few-shot leans ahead of zero-shot.

**How sensitive is the domain?**
Moderately. Recursion and out-of-scope topics must be handled correctly. The constraint list is important but the domain is not high-stakes in the sense of medical or legal.
→ Not Role + Constraint specifically, but Constraint section needs care.

**How much does the audience vary?**
A consistent group — second-year BTech CSE students with a shared syllabus.
→ Shared Metadata covering the group, not personalised per student.

**How quickly does context change?**
Weekly — covered topics grow each week.
→ Keep Metadata updatable. Do not use Persona pattern — too much maintenance overhead.

**Decision: Few-shot with shared Metadata.** This is exactly what was built across Weeks 2 and 3. The pattern choice was right — not by accident, but because the task characteristics point to it.

---

## When to Combine Patterns

Patterns are not mutually exclusive. The most effective context packages often combine elements.

Few-shot with Chain-of-thought: examples plus an instruction to show reasoning. Useful for tutoring tasks where the model should demonstrate how to think through a problem, not just what the answer is.

Role + Constraint with Metadata: detailed boundaries plus rich situational context. Useful for sensitive domains where the model needs both strict limits and deep situational awareness.

Start with one pattern. Add elements from another if testing reveals gaps. Do not combine for the sake of complexity — combine when a specific gap in the primary pattern needs to be filled.

---

## Quick Recap

- Choose a pattern by answering four questions: how well-defined is the output, how sensitive is the domain, how much does the audience vary, how quickly does context change
- The answers map directly to the five patterns — use the decision guide as a starting point
- Patterns can be combined — few-shot with chain-of-thought, role + constraint with rich metadata — when a single pattern leaves a specific gap
- Start simple, test, then add complexity only where testing reveals it is needed

---

## What Is Next

The next topic moves from context quality to AI governance — why the systems you are building have obligations beyond producing good responses, and what it means to move from writing prompts to building systems that affect real people.
