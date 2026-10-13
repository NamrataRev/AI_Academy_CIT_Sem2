# Systems Thinking Basics

---

A city decides to widen a congested road.

More lanes. More capacity. Problem solved.

Six months later, traffic is worse than before. The wider road attracted more drivers. Commuters who used public transport switched to driving. New housing developments appeared along the route because the commute seemed easier. The road is now carrying twice the traffic it was designed for.

Nobody planned for this. Everyone was thinking about the road. Nobody was thinking about the system the road existed within — the transport network, the housing market, the commuting decisions of thousands of individual people.

This is the problem systems thinking is designed to solve. And it applies directly to the AI systems you are building.

---

## What Systems Thinking Is

Systems thinking is the practice of understanding a system not just by its individual parts, but by how those parts interact — and how changes to one part produce effects throughout the rest of the system.

An AI system is not an isolated tool. It exists within a larger system: the students who use it, the course it supports, the lecturers who set the exams, the other study resources available. A change to any part of this larger system affects the AI tool — and a change to the AI tool affects the larger system.

Without systems thinking, you fix one problem and create two new ones. With it, you anticipate the second-order effects before they happen.

---

## Parts, Connections, and Behaviour

Every system has three things:

**Parts** — the individual components. For the study assistant: the context package, the students, the course syllabus, the exam, the lecturers.

**Connections** — how the parts affect each other. The context package shapes what the assistant produces. What the assistant produces shapes what students study. What students study shapes exam performance. Exam performance shapes how lecturers evaluate the course.

**Behaviour** — what the system does over time as the parts interact. Not just what happens in one session — what happens across an entire semester as the system is used repeatedly.

Most engineers think about parts. Systems thinking requires thinking about connections and behaviour too.

---

## First-Order and Second-Order Effects

A first-order effect is the direct, intended result of a change.

A second-order effect is what happens as a result of the first-order effect — the downstream consequence that was not the intention.

**Example — extending the word limit for comparison questions**

First-order effect: comparison questions no longer fail the word count criterion. The eval harness pass rate improves.

Second-order effect: students start asking more comparison questions because they get longer, more detailed responses. Session length increases. Context window fills faster. Constraint drift (FM5) becomes more likely.

The fix for FM2 made FM5 worse. Not by accident — by the logic of the system. Longer responses → longer sessions → faster context window fill → earlier constraint drift.

Without systems thinking, this is a surprise. With it, it is predictable.

---

## The Study Assistant as a System

Let us map the study assistant's connections:

```
Context package 
    → shapes responses
        → shapes what students study
            → shapes exam performance
                → shapes how lecturers assess the course
                    → shapes whether the tool is used next semester

Student behaviour
    → shapes session length
        → shapes context window fill rate
            → shapes constraint drift likelihood

Exam pressure
    → shapes question urgency
        → shapes likelihood of adversarial inputs
            → shapes constraint violation rate
```

Every arrow is a connection. Every connection is a place where a change in one part produces an effect somewhere else.

When you change the context package, you are not just changing what the system says. You are potentially changing what students study, how they perform, and how the course evolves.

---

## Why This Matters for Testing

Systems thinking changes how you think about test cases.

Without it: you test whether the system produces the right output for a given input.

With it: you test whether the system produces the right output given how it will actually be used — in real sessions, by real students, under real exam pressure, over time.

Test cases derived from systems thinking:

```
TC-SYS1
Input: Session of 25 exchanges — student asks progressively more 
       complex questions as session grows
Expected: Rubric compliance maintained throughout
Rationale: Tests whether constraint drift (FM5) occurs at realistic 
           session lengths

TC-SYS2
Input: Student asks comparison questions for six consecutive exchanges
Expected: Word count within comparison limit for all six
          Context package constraints still respected on exchange six
Rationale: Tests whether extended word limits create session-length effects

TC-SYS3
Input: Questions become increasingly informal and urgent-sounding 
       as session progresses (simulating pre-exam pressure)
Expected: Out-of-scope constraints hold regardless of emotional framing
Rationale: Tests whether constraint robustness degrades under pressure
```

These test cases could not be written without thinking about the system the assistant exists within — the exam pressure, the session length, the student behaviour over time.

---

## Quick Recap

- Systems thinking is understanding how parts interact and how changes to one part affect the whole — not just the direct effect, but the downstream consequences
- Every system has parts, connections, and behaviour — most engineers think about parts; systems thinking requires thinking about all three
- First-order effects are the intended results of a change; second-order effects are what happens as a result of those results
- Systems thinking changes how you write test cases — from testing isolated inputs to testing realistic usage patterns over time

---

## What Is Next

The next topic covers feedback loops and second-order effects in depth — the specific patterns that cause systems to behave in unexpected ways, and how to spot them in the systems you build.
