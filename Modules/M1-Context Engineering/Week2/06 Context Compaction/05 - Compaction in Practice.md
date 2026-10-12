# Compaction in Practice

---

The previous four topics covered the tools — summarisation, truncation, sliding windows, selective retention. This topic shows them working together using the same sample conversation introduced in the previous topic.

If you have not read the previous topic, the six-exchange sample conversation is reproduced at the top of this file for reference.

---

## The Sample Conversation — Reference

```
EXCHANGE 1
Student: What is a stack?
Assistant: Think of a stack like a pile of trays in a cafeteria — 
you can only add to the top and take from the top. In code: LIFO, 
last in first out. Used in: browser back button, undo functions, 
function call tracking.

EXCHANGE 2
Student: Can you give me another example?
Assistant: Think of a stack like a pile of books on your desk — 
you place a new book on top and always pick up from the top. 
The last book placed is the first one you pick up. Used in: 
compiler syntax checking, expression evaluation.

EXCHANGE 3
Student: I find the physical object analogies much easier than 
process analogies. The plate and book examples clicked immediately.
Assistant: Noted — I will keep using physical object analogies 
throughout our session.

EXCHANGE 4
Student: What is a queue?
Assistant: Think of a queue like people waiting at a ticket counter — 
first in line is served first. In code: FIFO, first in first out. 
Used in: print spoolers, message delivery, CPU scheduling.

EXCHANGE 5
Student: What is the difference between a stack and a queue?
Assistant: A stack is like a pile of books — last placed is first 
picked up (LIFO). A queue is like a ticket counter line — first 
in line is first served (FIFO). Use a stack when order needs to 
be reversed. Use a queue when order needs to be preserved.

EXCHANGE 6
Student: Got it. Can we move to trees now?
Assistant: Of course. A tree is like a family tree — one root at 
the top, branches going down, each person (node) connected to 
those below them (children). In code: hierarchical data structure 
with one root node and child nodes. Used in: file systems, 
HTML document structure, decision trees.
```

This is the reference conversation. All compaction decisions below refer to these six exchanges by number.

---

## The Setup

A student starts a revision session with the study assistant. The context package is loaded:

```
AUTHORITY: Study assistant for second-year BTech CSE students 
           preparing for their DSA exam.

EXEMPLAR: [two examples — stack and queue explained with analogies]

CONSTRAINT: No recursion. Under 120 words. No Big O notation.

RUBRIC: Analogy, definition, use case — in that order.

METADATA: Covered: arrays, linked lists, stacks, queues, trees, BSTs.
          Not covered: graphs, dynamic programming, recursion.
          Exam in 8 days.
```

The six sample exchanges happen. The context window now holds the full context package plus these six exchanges. Still comfortable — but the session continues.

---

## Step 1 — Selective Retention

Before any compaction runs, identify what must be kept verbatim.

Looking at the six exchanges:

**Exchange 3** — the student said physical object analogies work better than process analogies. This preference must be carried forward exactly. A summary might say "student prefers clear analogies" — which loses the specific instruction. Retain verbatim.

**Exchange 6** — the student decided to move from stacks and queues to trees. This is a topic decision. Retain it so the model knows stacks and queues are done.

These two items go into the RETAINED section:

```
RETAINED:
- Exchange 3: Student explicitly prefers physical object analogies 
  over process analogies. Plate and book stack examples clicked. 
  Use physical object analogies throughout.
- Exchange 6: Student has finished stacks and queues. 
  Currently working on trees.
```

---

## Step 2 — Summarise Exchanges 1-4

The conversation has now grown further — the student has asked several tree questions beyond Exchange 6. Exchanges 1-4 are the oldest content. Time to summarise them.

These four exchanges covered: what a stack is (two examples), the student's analogy preference, and what a queue is.

**Summary of Exchanges 1-4:**

```
CONVERSATION SUMMARY (Exchanges 1-4):

Topics covered: Stacks (LIFO) — explained with cafeteria tray 
analogy and book pile analogy. Queues (FIFO) — explained with 
ticket counter analogy.

What was established: Student confirmed physical object analogies 
work better than process analogies (Exchange 3). Both stack 
analogies landed well.

Student position at end of Exchange 4: Confident on stacks. 
Had just received the queue explanation.
```

The four full exchanges — which together were several hundred words — are now one short paragraph. Everything essential is preserved. The verbose back-and-forth is gone.

---

## Step 3 — Sliding Window for Exchanges 5-6

Exchanges 5 and 6 are the most recent of the original six. They stay in full as the sliding window — providing the immediate conversational thread.

```
[Exchange 5 — full text]
[Exchange 6 — full text]
```

---

## Step 4 — Reconstruct the Context

After compaction, the context looks like this:

```
[Full context package — unchanged, always at the top]

[RETAINED section]
- Exchange 3: physical object analogy preference
- Exchange 6: student has moved to trees

[CONVERSATION SUMMARY — Exchanges 1-4]

[Exchange 5 — full]
[Exchange 6 — full]
```

Compare what we started with versus what we have now:

| Before compaction | After compaction |
|---|---|
| Full context package | Full context package |
| 6 full exchanges | RETAINED (2 items) + Summary (1 paragraph) + 2 full exchanges |
| Growing context window | Lean, manageable context window |
| Context package moving away from current message | Context package stays at the top, close to current message |

The student's session continues. The model has everything it needs — the context package, the retained preference, the summary of what was covered, and the two most recent exchanges in full.

---

## What the Student Experiences

Nothing. The student asks their next question about trees. The response follows the rubric. The analogy uses a physical object — because Exchange 3 was retained and the preference is still active. The length is under 120 words. The structure is correct.

The compaction happened invisibly. The session continues as if nothing changed — because from the student's perspective, nothing did.

---

## What Would Have Happened Without Compaction

If the session continued to thirty exchanges without compaction:

- The context package would be far from the current message — receiving weak attention
- Responses would start exceeding 120 words
- The analogy-first structure would begin to disappear
- Exchange 3's preference for physical object analogies would stop being applied — it would be buried too deep in the context to influence responses
- Eventually, a recursion example might appear — the constraint has drifted

Compaction prevented all of this. Not by changing the model — by managing what the model could see.

---

## The Practical Takeaway

Build compaction in from the start — before you need it, not after you notice the system is drifting.

For any AI session expected to run more than ten exchanges:

1. Identify what deserves selective retention as the session begins (usually: preferences and decisions)
2. Set the trigger — compact when the context reaches roughly half capacity
3. Summarise everything older than the last two to five exchanges
4. Keep the last two to five exchanges as the sliding window
5. Always keep the full context package at the top — never summarise or truncate it

A well-maintained context window produces consistent responses across a full session. A neglected one drifts — slowly at first, then noticeably, then badly.

---

## Quick Recap

- All four compaction techniques work together: selective retention for must-keep items (Exchanges 3 and 6), summarisation for older history (Exchanges 1-4), sliding window for recent exchanges (Exchanges 5-6), context package always preserved at the top
- Compaction is invisible to the student — the session continues without interruption
- Without compaction, long sessions drift: longer responses, dropped structure, violated constraints
- Build compaction in from the start — compact at half capacity, before degradation is visible

---

## What Is Next

The next topic covers context packages as reusable documents — how to structure, name, version, and share them so the work you put into building a good context package benefits more than one session or one person.
