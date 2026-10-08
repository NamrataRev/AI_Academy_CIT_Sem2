# Documentation Template

---

You build a context package that works well. You test it. You refine it. The study assistant produces exactly the right responses.

Three weeks later, a teammate wants to use the same system for a different course. They ask you what the context package looks like. You send them the system prompt. They read it and ask: "Why is recursion excluded? What version is this? Has it been tested? What changed between this and the earlier version?"

You do not know. You never wrote any of that down.

This is why documentation matters. A context package without documentation is a tool only you can use — and only while you remember how it works. Documentation makes it transferable, maintainable, and improvable over time.

---

## What Context Package Documentation Contains

A fully documented context package has two parts: the package itself and the record around it.

**The package** — the five roles, written and labelled as covered in the previous topic.

**The record** — everything about the package that is not in the package itself. Why decisions were made. What was tested. What changed. Who it is for.

The record is what makes the package a professional document rather than a personal note.

---

## The Standard Documentation Template

Here is the template. Every context package you build for this course should follow this format.

---

```
# CONTEXT PACKAGE DOCUMENTATION

## Package Name
[Short, descriptive name — e.g. "BTech DSA Study Assistant v1.2"]

## Purpose
[One to two sentences. What is this package for? What problem does it solve?]
Example: "Provides consistent, exam-ready explanations of Data Structures 
and Algorithms concepts for second-year BTech CSE students."

## Audience
[Who is this for? Be specific.]
Example: "Second-year BTech CSE students. Assumed knowledge: Python basics, 
first-year programming. No prior DSA exposure assumed."

## Version
[Version number and date of last update]
Example: "v1.2 — updated Week 6 to add graphs to covered topics"

## Status
[Current state of the package]
Options: Draft | Under Test | Active | Deprecated

---

## THE PACKAGE

### AUTHORITY
[Full authority role text]

### EXEMPLAR
[Full exemplar section — all examples]

### CONSTRAINT
[Full constraint list]

### RUBRIC
[Full rubric definition]

### METADATA
[Full metadata section]

### COMPACTION INSTRUCTION
[Compaction trigger and summary format]

---

## DESIGN DECISIONS

[This section explains why key choices were made. 
Write one paragraph per significant decision.]

Example entries:
- "Recursion excluded from constraints because the course covers it 
  in a separate module (Week 9). Including recursion examples before 
  Week 9 would create confusion rather than clarity."

- "Physical object analogies specified in Authority after testing showed 
  students found process analogies (e.g. assembly lines) harder to 
  remember than object analogies (e.g. pile of trays)."

- "120-word limit set after testing showed responses over 150 words 
  were not being copied into revision notebooks in full."

---

## TEST RESULTS

[Record of how the package was tested and what the results were]

Format:
- Test date:
- Number of test questions:
- Pass rate (responses meeting all rubric criteria):
- Constraint violations found:
- Changes made after testing:

Example:
- Test date: Week 3
- Test questions: 15 (5 direct concept questions, 5 comparison questions, 
  5 edge cases — topics near the boundary of covered/not-covered)
- Pass rate: 13/15 met all rubric criteria
- Violations found: 2 responses exceeded 120 words; 
  1 response used Big O notation despite constraint
- Changes: Strengthened constraint wording — 
  "Do not use Big O notation" → "Do not use O() notation 
  or discuss time complexity in mathematical terms"

---

## CHANGELOG

[Record of every significant change to the package, newest first]

Format: [Version] — [Date] — [What changed and why]

Example:
v1.2 — Week 6 — Added graphs to covered topics in Metadata after 
        Week 5 lecture. No other changes.
v1.1 — Week 3 — Strengthened Big O constraint after test found 
        one violation. Added third exemplar for tree traversal.
v1.0 — Week 1 — Initial version. All five roles written and tested.

---

## KNOWN LIMITATIONS

[Anything the package does not handle well — be honest]

Example:
- "Package does not handle questions about topics not on the DSA 
  syllabus well — model sometimes attempts an answer instead of 
  redirecting. Workaround: student should be told to only ask 
  DSA-related questions."
- "Compaction summary sometimes omits confusion points that were 
  resolved mid-session. Check RETAINED section is used for 
  important resolved confusions."
```

---

## Why Each Section Matters

**Design Decisions** — Without this, nobody knows why the constraint on recursion exists. A future maintainer removes it thinking it was an oversight. Responses start including recursion. The package breaks for its intended audience.

**Test Results** — Without this, nobody knows whether the package actually works. "Looks good" is not evidence. Test results are evidence.

**Changelog** — Without this, v1.2 and v1.0 are indistinguishable. Nobody knows what changed or why. Rolling back to an earlier version becomes impossible.

**Known Limitations** — Without this, users hit a problem and assume the whole package is broken. Documenting limitations sets accurate expectations and provides workarounds.

---

## How to Use the Template in This Course

Every context package you build as part of your assessments should follow this template. Not because documentation is administrative overhead — but because:

A package without documentation is a personal tool. A package with documentation is a professional asset. The difference is whether someone else — or future you — can understand, maintain, and improve it.

---

## Quick Recap

- A fully documented context package has two parts: the package itself and the record around it
- The record contains: purpose, audience, version, status, design decisions, test results, changelog, and known limitations
- Design decisions explain why — without them, future maintainers make changes that break the package's intent
- Test results are evidence — "looks good" is not
- Documentation makes a context package transferable, maintainable, and improvable — not just usable by the person who built it

---

## What Is Next

Week 2 is complete. Before moving to Week 3, the Week 2 summary covers everything covered this week — all five context roles, conversation memory, compaction techniques, and context package documentation — in one place for revision.
