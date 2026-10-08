# Authority Role

---

Walk into any classroom and you can tell within thirty seconds who the teacher is.

Not because of a nameplate. Not because someone introduced them. Because of how they carry themselves, the vocabulary they use, the way they frame questions, the level they pitch their explanations at. Their identity shapes everything about how the session runs.

Now imagine a substitute who walks in with no briefing. They do not know the subject level, the course, the students' background, or what was covered last week. They default to something generic — too basic for some students, too advanced for others, wrong tone, wrong examples.

The Authority role in a context package is the briefing that prevents this. It tells the model who it is — specifically, purposefully, and completely enough to shape every response it produces.

---

## What the Authority Role Is

The Authority role defines the model's identity within this context package.

It is not just a job title. It is a complete enough description that the model understands:
- What kind of entity it is
- Who it is serving
- What level of expertise it operates at
- What its purpose is in this interaction

A weak authority: *"You are a helpful assistant."*

Every model defaults to this. It tells the model nothing it did not already assume. The response will be generic.

A strong authority: *"You are a study assistant for second-year BTech Computer Science students who are preparing for their semester exams. You explain concepts clearly using analogies before technical definitions, and you pitch your explanations at someone who has completed first-year programming but has not yet encountered advanced mathematics."*

Same model. Completely different responses. Because now it knows who it is.

---

## What Changes When Authority Is Well Defined

**Vocabulary** — a well-defined authority stops the model from using jargon the audience does not know, or oversimplifying for an audience that does.

**Tone** — a study assistant for exam revision sounds different from a research assistant for a faculty member. Authority sets the register.

**Depth** — knowing the audience's level stops the model from going too deep or too shallow. It calibrates automatically.

**Perspective** — an authority that says "you explain concepts using analogies first" changes not just what the model says but how it approaches every explanation.

---

## How to Write a Good Authority

A useful authority answers four questions:

**Who is the model?**
Not just a role title — a purposeful description. "A study assistant for BTech students" not just "an assistant."

**Who is it serving?**
The audience, their level, their background. "Second-year BTech Computer Science students who have covered arrays, linked lists, and sorting algorithms."

**What is its purpose?**
What is this assistant for? Exam revision. Assignment help. Concept explanation. Code review. Each purpose produces different behaviour even with the same role title.

**What expertise level does it operate at?**
Where on the spectrum from beginner to expert does it pitch its responses? This one detail changes vocabulary, depth, and example choice significantly.

---

## A Weak Authority vs a Strong One

**Weak:**
```
You are a helpful AI assistant.
```

**Strong:**
```
You are a study assistant for second-year BTech Computer Science 
students preparing for their Data Structures and Algorithms exam. 
You explain concepts by starting with a simple real-world analogy, 
then giving the technical definition, then one concrete example. 
You pitch your explanations at someone who knows Python basics and 
has covered arrays and linked lists but has not yet encountered 
recursion or dynamic programming.
```

The weak version produces a generic explanation suitable for nobody in particular. The strong version produces something calibrated to this specific student, this specific course, this specific moment in the semester.

---

## What Happens Without Authority

Without a defined authority, the model fills in the gap itself. It becomes a generic helpful assistant — polite, thorough, and completely uncalibrated to your situation.

The vocabulary will be wrong for the level. The examples will be random rather than relevant. The tone will be either too formal or too casual. The depth will be either too introductory or too advanced.

None of this is the model's fault. It was never told who it was supposed to be. It did the best it could with no briefing.

Authority is the briefing. Write it first. Write it fully.

---

## Quick Recap

- The Authority role defines who the model is — its identity, purpose, audience, and operating level
- A weak authority ("helpful assistant") produces generic responses — a strong one calibrates everything
- A good authority answers four questions: who is the model, who is it serving, what is its purpose, what expertise level does it operate at
- Without authority, the model defaults to a generic identity and produces responses suited to nobody in particular

---

## What Is Next

The next topic covers the Exemplar role — how showing the model examples of good responses is more powerful than describing what good looks like, and how to choose examples that actually calibrate the model's output.
