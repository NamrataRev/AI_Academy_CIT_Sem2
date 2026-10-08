# Exemplar Role

---

You are learning a new sport. Your coach watches you play and says: "Hit the ball cleanly."

You try. Wrong. They say it again. Still wrong. You are trying your best but you genuinely do not know what "cleanly" means in practice — where to position your body, how much force, which part of the bat to use.

Then they step in and demonstrate one shot. You watch it. Everything clicks. The stance, the timing, the follow-through. Thirty seconds of demonstration did what ten minutes of instruction could not.

The instruction told you the standard. The demonstration showed you what meeting that standard actually looks like.

This is the Exemplar role. And it is the most powerful tool in a context package.

---

## What the Exemplar Role Is

The Exemplar role gives the model examples of the responses you want — before you ask your actual question.

Not descriptions of what good looks like. Actual examples. Real input-output pairs that demonstrate the standard you expect.

The model reads these examples and calibrates its behaviour to match them. Tone, length, structure, vocabulary, depth — all of it gets adjusted to match what the examples show.

---

## Why Examples Beat Descriptions

You can tell a model: *"Keep responses concise, use simple language, avoid jargon, and always include a practical example."*

Or you can show it:

```
Q: What is a stack?
A: Think of a stack like a pile of plates in a cafeteria. 
   You can only add to the top and take from the top. 
   In code, this means last in, first out — LIFO.
   Used in: undo functions, browser back buttons, function call tracking.
```

The second approach is more powerful every time. The model sees exactly what "concise" means for you — not in the abstract, but in practice. It sees what "simple language" looks like for this audience. It sees the structure: analogy, definition, abbreviation, use cases.

No description covers all of that as efficiently as one example.

---

## What Good Exemplars Look Like

A good exemplar has three properties:

**It represents the standard you actually want** — not a mediocre response, not a perfect one you could never reproduce consistently. The example should be the quality you are genuinely aiming for.

**It covers the format you want** — if you want responses in a specific structure, the example should use that structure. The model learns format from examples far better than from instructions.

**It is realistic for the task** — the example should be close enough to the real questions that will be asked. An exemplar about a completely different topic from a completely different domain gives weak calibration.

---

## How Many Exemplars Do You Need

One exemplar is better than none. Two or three is significantly better than one. Beyond five, the returns diminish — and you start consuming context window space that would be better used for the actual task.

For most context packages, two to three well-chosen exemplars is the right number.

---

## Exemplars for the BTech Study Assistant

Here is what three exemplars look like in the study assistant context package:

```
EXEMPLAR 1:
Q: What is a queue?
A: Think of a queue like people waiting in line at a canteen — 
   first person in is first to be served. In code: FIFO — 
   first in, first out. Used in: print spoolers, CPU scheduling, 
   message queues between services.

EXEMPLAR 2:
Q: What is the difference between a stack and a queue?
A: A stack is like a pile of books — you always take from the top 
   (last in, first out). A queue is like a line of people — 
   first in line is served first (first in, first out). 
   Use a stack when order of processing should be reversed. 
   Use a queue when order should be preserved.

EXEMPLAR 3:
Q: What is a hash table?
A: Imagine a library where every book has a specific numbered shelf 
   assigned by a formula — so you go directly to the right shelf 
   without searching. A hash table does this for data: it uses a 
   function to calculate exactly where to store and find each item. 
   Result: lookup in constant time, O(1), regardless of size.
```

Three examples. Three different question types. The model now knows: analogy first, technical definition second, abbreviation or complexity third, use cases or comparison fourth. It will apply this pattern to every question it receives — including ones it has never seen before.

---

## What Happens Without Exemplars

Without exemplars, the model has only the descriptions in Authority and Constraint to go on. It produces something that fits those descriptions — but "simple" and "concise" mean different things to different people. The model picks an interpretation. It may not be yours.

The response might be too long. Or too short. The analogy might be too abstract. The vocabulary might be slightly off for this audience.

Exemplars eliminate this ambiguity. They show the model your interpretation of the standard — not in words, but in actual output.

---

## Quick Recap

- The Exemplar role gives the model examples of the responses you want — before asking the actual question
- Examples beat descriptions because they show the exact standard — tone, length, structure, vocabulary — more efficiently than words can describe it
- Two to three well-chosen exemplars is the right number for most context packages
- Without exemplars, the model interprets the standard for itself — and its interpretation may not match yours

---

## What Is Next

The next topic covers the Constraint role — how to tell the model what not to do, why boundaries are as important as instructions, and how well-written constraints prevent the most common ways AI responses go wrong for a specific audience.
