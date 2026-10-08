# Side-by-Side Examples

---

The previous topic defined context and prompt as two distinct things. This topic shows them working together — through real examples you can read, compare, and use as a model for your own context packages.

Three scenarios. Each one shows the same system built two ways — without a proper context package, and with one. The difference in output quality is the lesson.

---

## Scenario 1 — Study Assistant for Data Structures

**Without a context package — everything in the prompt:**

```
PROMPT:
I am a second-year BTech CSE student preparing for my DSA exam 
next week. I have covered arrays, linked lists, stacks, queues, 
and trees. I have not covered recursion yet. Please explain 
what a stack is using a simple analogy, keep it under 100 words, 
and give me one real-world use case. Do not use recursion examples.
```

This works. But the student has to write all of this every single time. If they forget one part — no analogy, or too long, or a recursion example appears.

**With a context package:**

```
CONTEXT (written once, loaded before every conversation):

AUTHORITY: You are a study assistant for second-year BTech CSE 
students preparing for their Data Structures and Algorithms exam.

EXEMPLAR: 
Q: What is a queue?
A: Think of people waiting at a ticket counter — first in line 
   is served first. In code: FIFO, first in first out. 
   Used in: print spoolers, message delivery systems.

CONSTRAINT: Do not use recursion. Keep responses under 100 words. 
            Do not use Big O notation.

RUBRIC: Every response — analogy, definition, one use case.

METADATA: Covered: arrays, linked lists, stacks, queues, trees. 
          Not yet covered: recursion, graphs, dynamic programming. 
          Exam in 10 days.

---

PROMPT (what the student types):
What is a stack?
```

Three words. The context does the rest.

The output will have an analogy, a definition, a use case, no recursion, under 100 words — because the context package guaranteed it.

---

## Scenario 2 — Code Review Assistant

**Without a context package:**

```
PROMPT:
Review this Python code for a first-year BTech student. 
They know loops and functions but not recursion or OOP. 
Point out mistakes in a friendly tone. Do not rewrite the code 
for them — give hints. Focus on logic errors, not style.

[code pasted here]
```

Again — this works once. But every review requires the student to repeat all of that context. Different students forget different parts. Inconsistent reviews.

**With a context package:**

```
CONTEXT:

AUTHORITY: You are a code review assistant for first-year BTech 
students who know loops, conditionals, and functions but have 
not encountered OOP or recursion.

EXEMPLAR:
Student code: [loop with off-by-one error]
Review: "Your loop is close — think about what value i has 
when the loop ends. Should it include that last element or stop 
before it? Try printing i at the end of the loop and see."

CONSTRAINT: Do not rewrite the code. Do not introduce OOP concepts. 
            Do not mention recursion. Keep feedback to two points maximum.

RUBRIC: Each review — identify the issue, ask one guiding question, 
        suggest one thing to try. Friendly tone throughout.

METADATA: First year, second semester. Students have done: 
          variables, loops, conditionals, functions, basic lists.

---

PROMPT:
[code pasted here]
```

The student just pastes their code. Everything else is handled.

---

## Scenario 3 — Exam Preparation Q&A

**Without a context package:**

```
PROMPT:
I have a DSA exam tomorrow. I am a second year CSE student. 
Give me a practice question on binary search trees with the 
answer, at medium difficulty, in the format my professor uses — 
state the question, give the answer in steps, then explain why.
```

Reasonable. But "medium difficulty" and "the format my professor uses" are vague. The output will vary.

**With a context package:**

```
CONTEXT:

AUTHORITY: You are an exam preparation assistant for second-year 
BTech CSE students the day before their DSA exam.

EXEMPLAR:
Q: What is the time complexity of searching in a balanced BST?
Practice question format:
"Question: [question text]
Step-by-step answer: [numbered steps]
Why this matters: [one sentence connecting to exam relevance]"

CONSTRAINT: Medium difficulty — assumes knowledge of BST structure 
            but not advanced balancing algorithms (AVL, Red-Black). 
            No recursion in answers.

RUBRIC: Question, step-by-step answer, one-sentence exam relevance note.

METADATA: Exam tomorrow. Topics: arrays, linked lists, stacks, 
          queues, trees, BSTs. Common difficulty: BST insertion order.

---

PROMPT:
Give me a practice question on binary search trees.
```

Six words. The context package produces a well-structured practice question at exactly the right level, in exactly the right format, every time.

---

## What the Examples Show

In every scenario, the context package moves the stable information out of the prompt and into a structure that is loaded once and works reliably for every interaction.

The prompt becomes shorter and simpler. The student thinks less about how to ask and more about what they actually need to know.

The output becomes more consistent. Not because the model is different — but because it is working with complete information every time instead of whatever the student remembered to include.

This is the practical value of context engineering. Not just better responses — reliable responses. Predictable responses. Responses you can build a system around.

---

## Quick Recap

- Context packages move stable information out of the prompt — written once, applies to every interaction
- The prompt becomes just the question — short, simple, focused on what is needed right now
- All three examples show the same pattern: long detailed prompt replaced by a short question backed by a complete context package
- The output is more consistent not because the model changed — but because it now has complete information every time

---

## What Is Next

The next topic introduces conversation memory degradation — what happens to context over a long conversation, why the model's behaviour drifts as the conversation grows longer, and why this matters for any AI system that runs over multiple turns.
