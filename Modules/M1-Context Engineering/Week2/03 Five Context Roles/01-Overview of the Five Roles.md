# Overview of the Five Roles

---

Think about how a good professor prepares before walking into a lecture.

They know who they are — an expert in the subject, at the right level for this class. They have examples ready that they know work well for this group of students. They know what to avoid — topics too advanced, vocabulary not yet introduced. They know how they will judge whether students understood — the quality of questions asked, the look of recognition or confusion. And they know the background — which module this is, what was covered last week, where this fits in the course.

Five different kinds of preparation. Each one shapes how the lecture goes. Remove any one of them and something breaks down.

A context package works exactly the same way. It has five roles. Each one does a different job. All five together produce something reliable. Fewer than five and something is always missing.

---

## The Five Roles

**Authority** — who the model is

This defines the model's identity for this context. Not just "you are an AI" — but a specific, purposeful role. "You are a study assistant for second-year BTech Computer Science students." The authority role shapes everything that follows — tone, vocabulary, depth, perspective.

**Exemplar** — what good looks like

This shows the model examples of the responses you want. Not descriptions — actual examples. A model that has seen three good responses is better calibrated than one that has only been told what good means. Exemplars are the most powerful way to communicate quality without writing a lengthy specification.

**Constraint** — what not to do

This draws the boundary around the response space. What topics to avoid. What length not to exceed. What assumptions not to make. What vocabulary not to use. Constraints are what prevent the model from producing something technically correct but practically wrong for your situation.

**Rubric** — how to evaluate the response

This tells the model the criteria by which a good response is judged. Format, structure, length, completeness. A rubric is different from a constraint — a constraint says what to avoid, a rubric says what the finished response should look like when it is done well.

**Metadata** — what the model needs to know

This is the situational background. The facts about the context that the model cannot infer from the question alone. Which course, which level, what has already been covered, who the audience is, what the output will be used for. Metadata gives the model the awareness it needs to make good decisions at every step.

---

## Why All Five Matter

Each role fills a gap that the others cannot.

Without Authority — the model does not know what kind of entity it is. It defaults to a generic helpful assistant and produces generic responses.

Without Exemplar — the model knows what good means in theory but has no calibration for your specific standard. It produces something that fits the description but not the taste.

Without Constraint — the model fills the response space freely. It produces something that may be excellent for a different context but wrong for yours.

Without Rubric — the model produces the right content in the wrong shape. The information is there but not organised in a way that is immediately usable.

Without Metadata — the model is operating without situational awareness. It makes assumptions about who it is talking to, what they already know, and what they need. Those assumptions are often wrong.

---

## What a Complete Context Package Looks Like

Here is a simple example — a context package for a BTech study assistant:

```
AUTHORITY:
You are a study assistant for second-year BTech Computer Science 
students preparing for their Data Structures and Algorithms exam.

EXEMPLAR:
When explaining a concept, follow this structure:
"A [concept] is like [familiar analogy]. 
In technical terms: [precise definition].
Example: [one concrete code-free example]."

CONSTRAINT:
Do not use recursion examples — that topic is in a separate module.
Do not exceed 120 words per explanation.
Do not assume knowledge of Big O notation.

RUBRIC:
Each response should have three parts: analogy, definition, example.
The analogy must use something from everyday student life.
The definition must be precise enough to use in an exam answer.

METADATA:
This assistant is used the week before exams.
Students have covered: arrays, linked lists, stacks, queues, trees.
Students have NOT yet covered: graphs, dynamic programming, recursion.
```

Every role is present. Every role is doing something specific. The model that receives this context package has everything it needs to produce a useful response to almost any question a student asks — not just the one you tested it with.

---

## Quick Recap

- A context package has five roles — Authority, Exemplar, Constraint, Rubric, Metadata
- Each role fills a gap the others cannot — remove any one and something breaks down
- Authority defines who the model is, Exemplar shows what good looks like, Constraint sets the boundaries, Rubric defines the output shape, Metadata provides situational awareness
- All five together produce consistent, reliable responses across many different inputs

---

## What Is Next

The next topic covers the Authority role in depth — what it is, how to write it well, and what happens to responses when it is missing or poorly defined.
