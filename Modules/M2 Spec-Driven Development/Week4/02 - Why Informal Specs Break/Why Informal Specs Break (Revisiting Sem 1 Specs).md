# Why Informal Specs Break

---

Think about a group assignment where the brief was: "Build something interesting using AI."

Everyone nods. Everyone has a different picture in their head of what "interesting" means, how complex "something" should be, and what "using AI" actually requires. Three weeks later, half the group built a chatbot, one person built a data visualisation, and another person wrote a report about AI instead of building anything.

Nobody did the wrong thing. Everyone interpreted the brief reasonably. But the brief was so informal that four people reading it produced four completely different outcomes.

Informal specs break for the same reason. Not because the people building the system are incompetent — because the specification left too much open to interpretation.

---

## What an Informal Spec Looks Like

An informal spec is any requirement that cannot be tested.

If you cannot write a test that definitively passes or fails based on the requirement — the requirement is informal.

Here are informal specs from systems exactly like the ones you are building:

*"The assistant should give helpful responses."*
How do you test helpfulness? What is the pass condition? What is the fail condition?

*"Keep responses concise."*
Concise compared to what? 50 words? 200 words? 500 words?

*"Don't answer inappropriate questions."*
What is inappropriate? Inappropriate for whom? What should happen instead — silence, a redirect, an explanation?

*"The system should work well for students."*
Work well at what? Which students? What does well mean?

Every one of these sounds reasonable. None of them can be tested. None of them can be used to write an eval harness criterion. None of them tell a builder what done looks like.

---

## Three Ways Informal Specs Break

**They create invisible disagreement**

Two people read the same informal spec and build toward two different outcomes. Neither realises there is a disagreement until the system is built and one person says "that is not what I meant."

A team building the study assistant: one person thinks "concise" means under 100 words, another thinks it means under 300 words. They build the same system together. The responses are inconsistently sized because each person made different judgment calls when writing different parts of the context package.

**They make evaluation impossible**

You cannot score a response against "helpful" or "concise" or "appropriate." You can score it against "between 80 and 120 words" or "contains all three rubric elements" or "does not explain topics outside the covered syllabus."

The eval harness from Week 3 requires testable criteria. Informal specs do not produce testable criteria. Without testable criteria, you cannot measure whether the system is working.

**They guarantee scope creep**

When requirements are vague, builders fill the gaps with their own judgment. A builder who thinks the system should "really help students" adds features nobody asked for. A builder who thinks "don't answer inappropriate questions" means all off-topic questions starts refusing questions that are legitimately in scope.

Without a precise specification, every builder builds a slightly different system — shaped by their own interpretation of what the informal requirement meant.

---

## Revisiting What You Built in Semester 1

Look back at any system prompt or context package you wrote in Semester 1.

How many of the requirements were informal? How many could be tested? If someone else read what you wrote, would they build the same system you intended?

This is not a criticism. Informal specs are the natural starting point — they capture intention before precision. The problem is not writing an informal spec to start with. The problem is stopping there.

SDD does not eliminate informal specs — it transforms them. You take the informal intention ("the assistant should give helpful responses") and turn it into testable requirements ("each response contains an analogy, a definition, and a use case, in that order, under 120 words").

The intention stays the same. The specification becomes testable.

---

## Quick Recap

- An informal spec is any requirement that cannot be tested — no pass condition, no fail condition
- Informal specs create invisible disagreement, make evaluation impossible, and guarantee scope creep
- The problem is not starting with an informal spec — the problem is stopping there
- SDD transforms informal intentions into testable requirements — same goal, precise enough to verify

---

## What Is Next

The next topic introduces functional requirements — the first formal type of requirement in SDD, and how to write them precisely enough that they can actually be tested.
