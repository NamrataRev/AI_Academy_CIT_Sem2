# ReAct in Practice

---

Reading about ReAct is one thing. Seeing it work on a real task is another.

This file walks through one complete task — every reason, every action, every observation. By the end you will be able to look at any agent's logs and immediately understand what the brain was thinking at each step.

---

## The Task

*"I want to learn machine learning. What is the best free online course available right now, and how long will it take to complete?"*

Two things needed: a course recommendation and a time estimate. Both require current information — courses get updated, new ones launch, old ones get discontinued.

---

## The Full ReAct Trace

**Loop 1**

```
REASON: I need the best free ML course right now. 
        "Right now" matters — availability changes. 
        I cannot rely on training data. I will search.

ACT: search_web → "best free machine learning course 2025"

OBSERVE: Three names come up consistently — Andrew Ng's 
         Machine Learning Specialisation on Coursera, 
         Google's ML Crash Course, and Fast.ai.
```

**Loop 2**

```
REASON: I have three candidates. I need to compare them — 
        which is best for a beginner, and are they 
        actually free? Let me look at all three together.

ACT: search_web → "Andrew Ng Coursera vs Google ML Crash 
     Course vs Fast.ai beginner comparison free 2025"

OBSERVE: Andrew Ng's is highly rated for beginners — 
         structured, thorough, widely recognised. 
         Google's is shorter and more practical. 
         Fast.ai requires prior coding knowledge. 
         Andrew Ng's is the most recommended starting point.
```

**Loop 3**

```
REASON: Andrew Ng's course is the strongest recommendation. 
        But I still need the time to complete it — 
        the question asked for that specifically. 
        I do not have it yet.

ACT: search_web → "Andrew Ng Machine Learning Specialisation 
     hours to complete 2025"

OBSERVE: Three courses in the specialisation. Estimated 
         3 months at 10 hours per week — roughly 120 hours total.
```

**Loop 4**

```
REASON: I now have both pieces — the course recommendation 
        and the time commitment. I can answer.

FINAL ANSWER: "The most recommended free starting point for 
machine learning is Andrew Ng's Machine Learning Specialisation 
on Coursera. It is free to audit — you only pay if you want 
the certificate. It takes approximately 3 months at 10 hours 
per week, or around 120 hours total. It is well structured 
for complete beginners and widely recognised by employers."
```

---

## What to Notice

**Loop 2 compared all three candidates together** — instead of searching each one separately. The reason step recognised that a side-by-side comparison was more efficient than three individual searches.

**Loop 3 was triggered by a gap** — the reason step in Loop 3 noticed the time estimate was still missing even though the course was identified. Without reasoning, the brain might have answered after Loop 2 with an incomplete response.

**No loop repeated work** — Loop 1 found candidates. Loop 2 compared them. Loop 3 got the time. Loop 4 answered. Each loop moved forward because the reason step checked the notepad before deciding what to do next.

---

## What This Looks Like in Agent Logs

When you build agents and inspect their logs, you will see exactly this structure:

```
Thought: I need current information about free ML courses...
Action: search_web
Action Input: "best free machine learning course 2025"
Observation: [results]

Thought: I have candidates but need to compare them...
Action: search_web
Action Input: "Andrew Ng vs Google ML Crash Course comparison"
Observation: [results]

Thought: Good recommendation found but time estimate missing...
Action: search_web
Action Input: "Andrew Ng ML Specialisation hours to complete"
Observation: [results]

Thought: I have everything I need.
Final Answer: [complete response]
```

This Thought / Action / Observation structure is ReAct made visible. When an agent behaves unexpectedly, reading these logs tells you exactly where the reasoning went wrong.

---

## Quick Recap

- Every loop follows: Reason → Act → Observe — the reason step decides what each loop does
- The reason step catches missing pieces before they become incomplete answers
- Agent logs show Thought / Action / Observation — reading them is how you debug agent behaviour
- No loop should repeat work already done — the reason step prevents this by checking the notepad first

---

## What Is Next

ReAct makes agents more reliable. But even well-structured agents fail in predictable ways. The next file gives you an overview of the four failure modes — what they are and why every agent builder needs to know them before deploying anything.
