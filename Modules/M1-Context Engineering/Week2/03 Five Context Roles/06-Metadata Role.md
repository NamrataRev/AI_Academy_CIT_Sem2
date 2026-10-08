# Metadata Role

---

Imagine a substitute professor walking into your class with no briefing.

They know the subject — algorithms, let us say. They are competent. But they do not know which university this is, which year the students are in, what was covered last week, what textbook the course follows, or what the exam format looks like.

They start teaching. They cover things already done. They skip things assuming students know them — but they do not. They use examples from a different textbook. They pitch the level slightly wrong.

Nothing they said was incorrect. But very little of it was useful for these students at this point in the semester.

Now give them a one-page briefing before they walk in. Which year. What was covered. What is coming next. What the students find difficult. What the exam looks like.

Same professor. Completely different class.

That briefing is Metadata.

---

## What the Metadata Role Is

Metadata is the situational background the model needs to make good decisions — facts about the context that no other role provides.

Authority tells the model who it is. Exemplar shows what good looks like. Constraint sets the limits. Rubric defines the shape of the output. But none of these tell the model about the specific situation it is operating in right now.

That is what Metadata does.

---

## What Metadata Contains

Metadata answers the questions: *Who is asking? What do they already know? What is the context of this interaction? What will the output be used for?*

**About the audience:**
- Year of study, course, specialisation
- What topics have been covered and what have not
- Common misconceptions or areas of difficulty
- What the students are preparing for — exam, assignment, project

**About the context:**
- When this interaction is happening — start of semester, week before exams, during a lab session
- What triggered this interaction — a specific assignment, a concept from today's lecture, preparation for tomorrow's test

**About the output:**
- Where the response will go — into revision notes, displayed on a screen, read aloud, fed into another system
- What format constraints exist beyond what the Rubric specifies

---

## Metadata for the BTech Study Assistant

```
METADATA:
Course: Data Structures and Algorithms — Second Year BTech CSE
Current week: Week 6 of 14
Topics covered so far: Arrays, Linked Lists, Stacks, Queues, Trees, BSTs
Topics NOT yet covered: Graphs, Dynamic Programming, Recursion, Heaps
Upcoming: Mid-semester exam in 10 days covering all topics above
Common difficulty areas: Students confuse stack and queue behaviour; 
                         BST insertion order confuses many students
Output usage: Responses are used as revision notes — students copy 
              them directly into their notebooks
Interaction context: Students use this assistant in the evening 
                     to review concepts from that day's lecture
```

With this metadata, the model knows exactly where it is in the course. It knows what to reference ("as you saw with stacks last week") and what not to reference ("we will cover graphs later"). It knows the exam is coming and can calibrate the depth and precision of its explanations accordingly. It knows the output goes into notebooks — so it keeps responses concise and copy-friendly.

None of this comes from Authority, Exemplar, Constraint, or Rubric. It comes from Metadata.

---

## The Difference Metadata Makes

Without metadata, the model makes assumptions about the situation. Sometimes those assumptions are right. Often they are not.

It assumes the student is a beginner when they are in their second year. It assumes no prior knowledge when half the class has seen this before. It pitches explanations at the wrong level. It references topics not yet covered. It produces responses that are thorough and accurate — and completely wrong for where the student actually is.

With metadata, the model is not guessing. It knows. And responses that come from knowledge rather than assumption are reliably more useful.

---

## Metadata Is Not Static

One important property of metadata: it changes.

At the start of the semester, the covered topics list is short. Ten weeks in, it is much longer. Two days before the exam, the context is completely different from two weeks before. The audience's knowledge level changes as the course progresses.

Good metadata is updated to reflect the current situation — not written once and forgotten. A context package with outdated metadata is almost as bad as one with no metadata at all. The model operates on what it is given. If what it is given is stale, its responses will be miscalibrated.

---

## Quick Recap

- Metadata is the situational background — facts about who is asking, what they know, what the context is, and what the output will be used for
- The other four roles define who the model is and how it responds — Metadata tells it where it is and what the situation actually is
- Without Metadata, the model makes assumptions about the situation — and those assumptions are often wrong
- Metadata changes as the situation changes — a context package should be updated to stay current

---

## What Is Next

All five roles are now covered. The next topic brings them together differently — looking at context versus prompt as two distinct things, what each one is for, and why confusing them is one of the most common mistakes in building AI systems.
