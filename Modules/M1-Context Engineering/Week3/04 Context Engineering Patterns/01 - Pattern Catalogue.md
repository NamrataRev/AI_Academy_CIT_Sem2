# Pattern Catalogue

---

Architects do not design buildings from scratch every time.

They use established patterns — a load-bearing wall here, a standard doorframe there, a known approach for ventilation in this climate. These patterns were developed and refined over decades. Using them does not make the building generic. It makes it reliable. The creativity goes into combining and adapting the patterns, not into reinventing structural principles.

Context engineering has patterns too. Proven approaches for common situations. You do not have to design every context package from first principles — you choose the pattern that fits the task, adapt it to your specific audience and constraints, and build on something that already works.

This topic catalogues the most useful patterns. The next topic covers how to choose between them.

---

## Pattern 1 — Zero-Shot

**What it is:** Authority, Constraint, and Rubric only. No examples.

**When to use it:** When the task is well-defined enough that a clear role, clear constraints, and a clear output format are sufficient — and when finding good examples would take longer than just writing precise role and rubric definitions.

**Looks like:**
```
AUTHORITY: You are a code reviewer for first-year BTech students 
           who know Python basics but not OOP.
CONSTRAINT: Point out one issue at a time. Do not rewrite the code.
RUBRIC: Issue, why it matters, one hint toward fixing it.
```

**Strength:** Fast to set up. Works well when the task is narrow and well-specified.
**Weakness:** Relies entirely on the precision of the language. If the rubric or constraint is even slightly vague, the model interprets it freely.

---

## Pattern 2 — Few-Shot

**What it is:** Authority, Exemplar (two to three examples), Constraint, Rubric.

**When to use it:** When the task has a specific style or format that is easier to demonstrate than describe. When you have found that zero-shot produces inconsistent results and adding examples stabilises the output.

**Looks like:**
```
AUTHORITY: [role definition]
EXEMPLAR:
  Q: [example input 1]
  A: [example output 1]
  
  Q: [example input 2]
  A: [example output 2]
CONSTRAINT: [constraints]
RUBRIC: [output criteria]
```

**Strength:** More powerful calibration than zero-shot. Examples communicate style, tone, and format more efficiently than descriptions.
**Weakness:** Requires good examples. A bad example is worse than no example — it calibrates the model toward the wrong standard.

---

## Pattern 3 — Chain-of-Thought

**What it is:** Authority and Rubric that explicitly instruct the model to show its reasoning before producing the final answer.

**When to use it:** When the task requires multi-step reasoning and you need the model to work through the problem, not just produce an answer. When incorrect answers are hard to spot without seeing the reasoning behind them.

**Looks like:**
```
AUTHORITY: You are a maths tutor for BTech students.
RUBRIC: For every problem:
        Step 1 — restate what is being asked
        Step 2 — identify the approach
        Step 3 — work through each step, showing all working
        Step 4 — state the final answer and check it makes sense
```

**Strength:** Makes reasoning visible — errors in the chain can be caught before the wrong answer is delivered. Significantly improves accuracy on complex reasoning tasks.
**Weakness:** Produces longer responses. Not suitable for tasks where speed or brevity is the priority.

---

## Pattern 4 — Role + Constraint

**What it is:** A strong, specific Authority combined with a detailed Constraint list. Minimal or no exemplar.

**When to use it:** When the task is about what the model should not do as much as what it should do. Systems that must avoid certain topics, stay within certain ethical boundaries, or redirect specific types of requests.

**Looks like:**
```
AUTHORITY: You are a mental health information assistant. 
           You provide general information about mental health 
           topics and signpost to professional resources. 
           You are not a therapist and do not provide diagnosis 
           or personalised advice.
CONSTRAINT:
- Do not provide diagnosis of any condition
- Do not give personalised treatment recommendations  
- Always include a signpost to professional help
- If a user appears to be in distress, prioritise signposting 
  over information provision
```

**Strength:** Very clear about boundaries. Works well for sensitive domains where crossing a constraint has serious consequences.
**Weakness:** Heavy on constraints can make the model feel overly restricted — responses can become formulaic if the constraints leave too little room.

---

## Pattern 5 — Persona with Metadata-Rich Context

**What it is:** A richly defined Authority combined with detailed Metadata. The model is given a complete picture of who it is and exactly what it knows about the situation.

**When to use it:** Long-running systems where the audience and context change over time. Systems used by different user groups with different needs. Situations where the model needs deep situational awareness to calibrate correctly.

**Looks like:**
```
AUTHORITY: You are a personalised study assistant for [student name]. 
           You adapt your explanations based on what [student name] 
           finds difficult and what approaches have worked for them.
METADATA:
  Student: [name]
  Year: Second year BTech CSE
  Strengths: Arrays, Linked Lists — confident and fast
  Difficulties: BSTs — specifically insertion order
  Preferred learning style: Physical object analogies
  Previous session: Covered stacks and queues. 
                    Resolved confusion about FIFO using ticket counter analogy.
  Current session goal: BST insertion and deletion
```

**Strength:** Deeply calibrated to a specific situation. Produces responses that feel personalised rather than generic.
**Weakness:** Metadata goes stale quickly and must be actively maintained. More setup time per session.

---

## Quick Recap

- Pattern 1 — Zero-shot: Authority + Constraint + Rubric. Fast to set up, works for narrow well-defined tasks
- Pattern 2 — Few-shot: adds Exemplar. More powerful calibration, requires good examples
- Pattern 3 — Chain-of-thought: Rubric instructs the model to show reasoning. Improves accuracy on complex tasks, produces longer responses
- Pattern 4 — Role + Constraint: strong Authority with detailed Constraint. Best for sensitive domains with clear boundaries
- Pattern 5 — Persona with rich Metadata: deeply calibrated to a specific situation. Powerful but requires active maintenance

---

## What Is Next

The next topic covers how to choose between these patterns — the questions to ask about your task, audience, and constraints that point toward the right pattern for each situation.
