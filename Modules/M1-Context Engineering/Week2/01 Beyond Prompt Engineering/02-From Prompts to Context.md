# From Prompts to Context

---

Think about the difference between asking a stranger for directions and asking a friend.

You ask a stranger: "How do I get to the library?" They give you generic directions. Turn left, go straight, it is the big building on the right. Technically correct.

You ask a friend who knows you: "How do I get to the library?" They say — "Are you walking or on your bike? If walking, go through the campus shortcut, it is faster. If you are coming from the hostel side, avoid the construction near Block C. The main entrance is closed today, use the side gate." 

Same question. Completely different answer. Because the friend has context — they know who you are, where you are coming from, what your situation is, and what actually useful looks like for you specifically.

Context is what turns a generic response into a useful one.

---

## What Context Actually Is

Context is everything you give the model beyond the immediate question.

It is the background the model needs to understand the situation. The constraints it should work within. The examples that show what good looks like. The criteria by which its response will be judged.

A prompt says: *"Explain binary search."*

A prompt with context says:
- You are a teaching assistant for a second-year BTech Computer Science course
- The students have covered arrays and loops but not recursion yet
- Explanations should use simple analogies before any code
- Keep responses under 150 words — they are used for revision cards
- Avoid Big O notation — that is covered in a separate module

Same question. The model now knows who it is, who it is talking to, what constraints to follow, and what the output will be used for. The response it produces will be fundamentally different — and fundamentally more useful.

---

## The Three Layers of Context

Context is not one thing. It has three layers that work together.

**The system layer** — who the model is and what its overall role is. This is set once and applies to every interaction. "You are a study assistant for second-year BTech students."

**The task layer** — what the model needs to know about this specific type of task. Constraints, format requirements, what to include, what to avoid. "Responses should be under 150 words. Use analogies before code."

**The input layer** — what the user is actually asking right now. "Explain binary search." This is what most people think of as the prompt — but it is only one layer.

All three layers together form a complete context package. Remove any one of them and the model is working with incomplete information.

---

## Why This Changes Everything

When a model has only the input layer — the bare question — it defaults to producing the most statistically average response it has seen for that type of question. Correct, generic, unhelpful for your specific situation.

When it has all three layers — its role, the constraints, and the question — it produces something calibrated to your actual need.

This is the shift from prompting to context engineering. You are not just asking a better question. You are building the environment the model operates in — so that any question asked within that environment gets a useful answer.

---

## Quick Recap

- Context is everything beyond the immediate question — the background, constraints, examples, and criteria the model needs to respond well
- A prompt with context tells the model who it is, what constraints to follow, and what good looks like — not just what to do
- Context has three layers: the system layer (who the model is), the task layer (how to respond), and the input layer (what is being asked)
- Without all three layers, the model defaults to generic — with all three, it produces something calibrated to the actual situation

---

## What Is Next

The next topic introduces the Sem 1 Week 13 bridge — connecting what you already know about prompting from last semester to the five-role framework you will build this week.
