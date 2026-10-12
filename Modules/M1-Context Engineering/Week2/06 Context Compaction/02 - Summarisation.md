# Summarisation

---

After every lecture, a good student does not keep all their rough notes active on their desk for the rest of the semester.

They write a clean summary. Key points. Essential definitions. What was confusing and how it was resolved. One page instead of ten. That summary becomes the reference — compact, accurate, immediately useful.

The ten pages of rough notes did their job. The summary carries what actually matters forward.

Summarisation in context compaction works exactly this way. Take the conversation history that has grown long, identify what still matters, and distil it into a brief, accurate summary that replaces the original transcript.

---

## What Summarisation Is

Summarisation is the most common compaction technique. It uses the model itself to produce a compressed version of the conversation history — capturing the essential substance in a fraction of the original length.

The summary replaces the full conversation history. From that point forward, the model works from the summary plus the context package, rather than from the full transcript.

---

## What a Good Summary Contains

A good conversation summary has four parts:

**What was covered** — the topics discussed, the concepts explained, the questions answered. Not the full explanations — just what ground was covered.

**What was established** — anything agreed upon, any understanding reached, any decisions made. Things the conversation produced that still matter going forward.

**Where the student is** — what they understand now that they did not understand before. What is still unclear. Where they are in their learning.

**What comes next** — what the next part of the conversation is about. The starting point the summary should hand off to.

---

## A Summarisation Example

Here is the sample conversation used throughout the compaction topics — six exchanges between a student and the study assistant:

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

Six exchanges. The conversation is now pushing the context window. Time to summarise.

Here is the summary that replaces Exchanges 1-4 (the oldest four):

```
CONVERSATION SUMMARY (replaces Exchanges 1-4):

Topics covered: Stacks (LIFO) — explained with cafeteria tray 
analogy and book pile analogy. Queues (FIFO) — explained with 
ticket counter analogy.

What was established: Student confirmed physical object analogies 
work better than process analogies (Exchange 3). Both stack 
analogies landed well. Student now understands stacks and queues 
and can distinguish when to use each.

Student's current position: Confident on stacks and queues. 
Has just started trees (Exchange 6).

Coming next: Continuing with trees — structure, terminology, traversals.
```

Four exchanges compressed to one short paragraph. Exchanges 5 and 6 stay in full as the sliding window — the immediate thread the model needs to continue. Everything the model needs is preserved. The verbose back-and-forth is gone.

This same conversation and these same exchange numbers are used in the remaining compaction topics — Selective Retention and Compaction in Practice.

---

## How to Trigger Summarisation

You do not need to manually write the summary yourself. You ask the model to produce it.

A simple instruction added to the context package:

```
When instructed to compact, produce a summary of the conversation 
so far in this format:
- Topics covered: [list]
- What was established: [key understandings reached]
- Student's current position: [where they are now]
- Coming next: [what the next topic is]

Keep the summary under 100 words.
```

Then, when you want to compact:

```
USER: Compact the conversation.
```

The model produces the summary. You take that summary, start a new message with the full context package followed by the summary, and the conversation continues — lean, fresh, well-attended.

---

## What Summarisation Does Not Do

Summarisation removes the full explanations that were given. If the student needs to revisit an explanation — "can you explain stacks again?" — the model no longer has the original explanation in context. It will generate a new one from the summary and the context package.

This is fine for most cases. The new explanation will be consistent with the context package. But it means summarisation is a one-way operation — you cannot reconstruct the original conversation from the summary.

This is almost never a problem. The purpose of the conversation is learning, not archiving. What matters is that the student understands — not that every word exchanged is preserved.

---

## Quick Recap

- Summarisation uses the model to produce a compressed version of the conversation history — capturing essential substance, removing verbose back-and-forth
- A good summary covers: what was covered, what was established, where the student is, what comes next
- Trigger summarisation by asking the model to compact — define the summary format in the context package so the output is consistent
- Summarisation is one-way — the original conversation cannot be reconstructed from the summary, but this is rarely a problem

---

## What Is Next

The next topic covers truncation and sliding windows — two alternative approaches to compaction that work differently from summarisation, and when each is the right choice.
