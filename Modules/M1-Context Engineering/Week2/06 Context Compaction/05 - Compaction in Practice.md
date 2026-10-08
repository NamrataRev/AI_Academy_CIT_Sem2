# Compaction in Practice

---

The previous four topics covered the tools — summarisation, truncation, sliding windows, selective retention. This topic shows them working together in a real conversation.

One study session. One student. Watch what happens to the context as the conversation grows — and how compaction keeps it functional.

---

## The Setup

A second-year BTech student starts a revision session using the study assistant. The context package is loaded:

```
AUTHORITY: Study assistant for second-year BTech CSE students 
           preparing for their DSA exam.

EXEMPLAR: [two examples — stack and queue explained with analogies]

CONSTRAINT: No recursion. Under 120 words. No Big O notation.

RUBRIC: Analogy, definition, use case — in that order.

METADATA: Covered: arrays, linked lists, stacks, queues, trees, BSTs.
          Not covered: graphs, dynamic programming, recursion.
          Exam in 8 days. Student uses responses as notebook entries.
```

Session begins.

---

## Exchanges 1-8 — Normal Operation

The student asks about stacks, queues, and their differences. Responses follow the rubric. Length stays under 120 words. No constraint violations.

At exchange 4, the student says: *"I find the physical object analogies much easier than process analogies. The plate stack example clicked immediately."*

This is flagged for selective retention. It gets added to a RETAINED section.

```
RETAINED:
- Student learns better from physical object analogies than 
  process analogies (established exchange 4)
```

The session continues. By exchange 8, the context window is holding the full context package plus eight exchanges. Still comfortable.

---

## Exchanges 9-16 — Approaching the Trigger Point

The student moves to trees. More exchanges. The conversation is now sixteen exchanges long. The context window is reaching half capacity — the trigger point for compaction.

The student has just asked about BST insertion. Before answering, compaction runs.

**Step 1 — Identify what to retain selectively.**

The physical object analogy preference is already in RETAINED. No new items to add.

**Step 2 — Summarise exchanges 1-14.**

```
CONVERSATION SUMMARY (exchanges 1-14):

Topics covered: Stacks (LIFO), Queues (FIFO), differences between 
them, real-world uses, when to use each. Binary trees — structure, 
parent/child/leaf terminology, height. BSTs — structure, ordering 
property, search behaviour.

What was established: Student is confident on stacks and queues. 
Initial confusion about tree height resolved — student now understands 
height as number of edges from root to deepest leaf. BST ordering 
property is clear.

Student's current position: Working through BST insertion. 
Understanding the concept but wants a concrete example.

Coming next: BST insertion with a step-by-step example.
```

**Step 3 — Keep the last two exchanges as the sliding window.**

Exchanges 15 and 16 — the most recent — stay in full. They provide the immediate conversational thread.

**Step 4 — Reconstruct the context.**

```
[Full context package — unchanged]

[RETAINED section]
- Student learns better from physical object analogies (exchange 4)

[CONVERSATION SUMMARY — exchanges 1-14]
[Exchange 15 — full]
[Exchange 16 — full]
```

The context window went from sixteen full exchanges to: context package + retained item + summary + two exchanges.

Significantly leaner. The context package is close to the current message again. The model has everything it needs to continue effectively.

---

## The Session Continues — Exchanges 17-25

The student works through BST insertion, deletion, and search. The sliding window keeps the last two exchanges in full. The summary absorbs anything older.

At exchange 25, another compaction runs. The summary is updated to include exchanges 15-23. Exchanges 24 and 25 form the new sliding window.

The student never notices. The responses remain consistent — right length, right structure, right analogies, no constraint violations.

---

## What Would Have Happened Without Compaction

Without compaction, by exchange 25:

- The context package is far from the current message
- Responses start exceeding 120 words
- The analogy-first structure disappears from some responses
- A recursion example appears in exchange 22 — the constraint has drifted
- The student's preference for physical object analogies is no longer being applied

The system is still producing responses. But they are inconsistent, longer than specified, and less calibrated to this specific student.

Compaction prevented all of this — not by changing the model, but by managing what the model could see.

---

## The Practical Takeaway

Compaction is not a fix for a broken system. It is maintenance for a working one.

Build it in from the start:
- Define the summary format in the context package
- Set the trigger point — compact at half context window capacity
- Use selective retention for preferences and decisions established early
- Keep a sliding window of the last two to five exchanges

A well-maintained context window produces consistent responses across a full session. A neglected one drifts — slowly at first, then noticeably, then badly.

---

## Quick Recap

- Compaction combines all four techniques: selective retention for must-keep items, summarisation for older history, sliding window for recent exchanges, context package always preserved
- Trigger compaction at half context window capacity — before degradation is visible, not after
- Build the summary format into the context package so compaction is consistent and can be triggered with a simple instruction
- Compaction is maintenance — built in from the start, not retrofitted when things go wrong

---

## What Is Next

The next topic covers context packages as reusable documents — how to structure, name, version, and share them so the work you put into building a good context package benefits more than one session or one person.
