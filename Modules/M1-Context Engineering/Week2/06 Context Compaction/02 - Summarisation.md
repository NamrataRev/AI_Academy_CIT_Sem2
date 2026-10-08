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

A student has been using the study assistant for thirty minutes. The conversation history is long — twelve exchanges about stacks and queues. Here is what the original history contains:

```
[Student asks what a stack is]
[Assistant explains with analogy]
[Student asks for another example]
[Assistant gives browser back button example]
[Student asks how stack differs from queue]
[Assistant explains LIFO vs FIFO]
[Student confused about FIFO]
[Assistant gives ticket counter analogy]
[Student gets it, asks about real-world uses]
[Assistant gives three examples]
[Student asks which to use when]
[Assistant explains decision criteria]
```

Twelve exchanges. Long. Pushing the context window.

Here is the summary that replaces it:

```
CONVERSATION SUMMARY (replaces previous 12 exchanges):

Topics covered: Stacks (LIFO) and Queues (FIFO) — concepts, 
analogies, real-world uses, and when to use each.

What was established: Student now understands both structures. 
Initial confusion about FIFO was resolved using the ticket counter 
analogy. Student can distinguish when to use stack vs queue based 
on whether order needs to be reversed or preserved.

Student's current position: Confident on stacks and queues. 
Ready to move to trees.

Coming next: Binary trees — structure, terminology, traversals.
```

Four sentences. Twelve exchanges compressed to four sentences. Everything the model needs to continue the conversation effectively — nothing it does not need.

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
