# Definitions and Differences

---

Think about the difference between a stage set and a script.

The stage set is built before the play begins. The lighting, the furniture, the backdrop — all of it is arranged to create the environment the actors will perform in. It does not change between scenes. It is the world the play happens inside.

The script is what the actors say. It changes every scene. Every line is different. But it only makes sense because the stage set exists.

Context is the stage set. The prompt is the script.

---

## What Context Is

Context is everything you provide to set up the environment the model operates in.

It is the system prompt — the part that loads before any conversation begins. It defines who the model is, what it knows about the situation, what it should and should not do, what good output looks like, and what the audience needs.

Context is stable. It does not change with every message. It is built once — carefully, deliberately — and it shapes every interaction that happens within it.

In the five-role framework you just learned:
- Authority — context
- Exemplar — context
- Constraint — context
- Rubric — context
- Metadata — context

All five roles live in the context. They are not part of the question. They are the environment around the question.

---

## What a Prompt Is

A prompt is the live request — what the user is asking right now, in this specific interaction.

*"Explain binary search."*
*"What is the difference between a stack and a queue?"*
*"Give me an example of a tree traversal."*

The prompt changes every time. Each student asks something different. Each session covers different material. The prompt is the moving part — it varies constantly.

A prompt on its own gives the model almost no information about the situation. It knows what is being asked but not who is asking, at what level, for what purpose, with what constraints.

---

## Why the Distinction Matters

Confusing context and prompt leads to one of the most common mistakes in building AI systems — putting everything in the prompt.

A student trying to get good responses from an AI model writes a long, detailed question every time. They include who they are, what course they are doing, what level they are at, what format they want. Every. Single. Time.

This works — for that one question. But it is exhausting. It is inconsistent — they remember different things each time. And it is not scalable — if ten students are using the same system, they cannot all write perfect detailed prompts every time.

The right approach: put the stable information in the context once. Let the prompt be just the question.

---

## The Boundary

**Context answers:** Who am I? Who is asking? What are the rules? What does good look like? What is the situation?

**Prompt answers:** What do I need right now?

Everything that is true across many interactions belongs in the context. Everything specific to this one interaction belongs in the prompt.

If you find yourself writing the same information in every prompt — that information belongs in the context.

---

## Quick Recap

- Context is the stable environment — set up once, shapes every interaction within it
- A prompt is the live request — changes every time, specific to this interaction
- All five context roles live in the context, not in the prompt
- If you are repeating the same information in every prompt, it belongs in the context instead

---

## What Is Next

The next topic shows context and prompt side by side with real examples — so you can see exactly what belongs where and how they work together to produce reliable responses.
