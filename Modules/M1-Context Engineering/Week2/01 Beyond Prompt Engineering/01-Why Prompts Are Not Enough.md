# Why Prompts Are Not Enough

---

You ask a classmate to help you revise for your algorithms exam.

They are smart. They know the subject. But you just said "help me revise" — nothing else. So they start from the very beginning. Data structures. Sorting. Things you already know well. They have no idea you are specifically struggling with dynamic programming. They do not know your exam is tomorrow. They do not know your professor focuses on time complexity analysis over implementation.

Thirty minutes later you have revised things you already knew and run out of time for what actually mattered.

Same classmate. Same knowledge. Completely different outcome if you had given them more to work with.

This is exactly what happens when you give an AI model a prompt without context.

---

## What a Prompt Does

A prompt is the instruction you give the model. *"Explain dynamic programming."* *"Summarise this chapter."* *"Write a function that sorts a list."*

For simple tasks, this works fine. The model uses its training knowledge and produces a reasonable response.

But the moment your task becomes specific — specific to your course, your syllabus, your professor's style, your level of understanding — a bare prompt is not enough. The model has no way to know what good looks like for your specific situation. It produces something generic that technically answers the question but does not actually help you.

---

## Where Prompts Break Down

A student is building an AI study assistant for their Object-Oriented Programming course.

They type: *"Explain inheritance."*

The model explains inheritance. Correctly. But it uses Java examples when the course uses Python. It covers abstract classes which are not in the syllabus yet. It uses technical vocabulary the professor has not introduced. It is three times longer than what would fit in the student's notes.

The answer is not wrong. It is just not right for this student, this course, this moment.

The prompt told the model what to do. It did not tell the model who it is talking to, what format to use, what to avoid, or how to judge whether the response is good.

That is the gap prompts cannot fill on their own.

---

## The Shift

Prompt engineering asks: *"How do I phrase this question to get a better answer?"*

Context engineering asks: *"What does the model need to know about the situation, the student, the course, and the expected output — so it behaves reliably every single time?"*

One optimises a single question. The other designs a system that works consistently across hundreds of different questions from different students at different points in the semester.

This is what this week is about — moving from asking better questions to building better systems.

---

## Quick Recap

- A prompt alone works for simple tasks — it breaks down when the task is specific to a person, course, or situation
- The model cannot guess what good looks like for your specific context — it needs to be told
- Prompt engineering optimises one question — context engineering builds a reliable system
- The goal is consistent, useful responses across many inputs — not just one good answer

---

## What Is Next

The next topic introduces context — what it actually is, how it is different from a prompt, and why giving the model more structured information changes what it can do.
