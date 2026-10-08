# Why Compaction

---

You have been studying for three hours. Your desk is covered in notes.

The first hour's notes are buried under everything else. You know they are there but finding something specific in them takes time. The most useful thing right now is what you wrote in the last thirty minutes — it is right in front of you, clear, easy to reference.

If you had to keep studying for three more hours, you would not just keep adding to the pile. At some point you would stop, organise what you have, write a clean summary of the key points, and set aside the original pages. You would not throw them away — but you would not keep them on top of the active pile either.

This is exactly what compaction does for a long AI conversation.

---

## The Problem Compaction Solves

You now know how memory degrades. As a conversation grows longer, the context window fills up. Early content — including the context package — moves further from the current message. Attention to it weakens. Responses start drifting.

The brute force solution is to restart the conversation every time it gets too long. Fresh context. Fresh attention. But restarting loses everything built up during the conversation — the established understanding, the refined examples, the ongoing thread of the interaction.

Compaction is the alternative. Instead of restarting, you compress. You take the growing conversation history, identify what is still essential, summarise it into a compact form, and replace the original history with the summary.

The conversation continues — but leaner. The context window has room again. The context package is near the current message again. Degradation is pushed back.

---

## What Compaction Preserves

Good compaction keeps three things:

**The context package** — Authority, Exemplar, Constraint, Rubric, Metadata. These never get summarised away. They are the foundation. They stay complete and intact.

**The essential thread** — what the conversation has established that still matters. In a study session: which topics have been covered, where the student got confused, what examples worked well. The substance of the interaction, not the full transcript.

**The current position** — where the conversation is right now. What was last discussed. What the student is working on. The starting point for what comes next.

---

## What Compaction Removes

Everything else. The verbose back-and-forth. The clarifying questions already resolved. The examples that were given and understood. The long explanations that have already served their purpose.

These were valuable when they happened. They are not valuable to keep verbatim. Their content has been absorbed. What remains is the outcome — which can be captured in a fraction of the original length.

---

## When to Compact

Do not wait until the conversation is broken. Compact before degradation is severe — not after.

A practical trigger: when the conversation has reached half the context window size, consider compaction. Do not wait until it is full. Compacting at half capacity is easier, produces a better summary, and extends the conversation's useful life significantly.

For a study assistant: compact between topics. The student finishes working through stacks. Before moving to queues, compact the stacks discussion into a summary. The new topic starts with a manageable context.

---

## Quick Recap

- Compaction compresses a growing conversation history into a compact summary — keeping what is essential, removing what has served its purpose
- It solves the degradation problem without losing the progress made in the conversation
- Good compaction always preserves the full context package, the essential thread, and the current position
- Compact before degradation is severe — at around half the context window, not when it is full

---

## What Is Next

The next topic covers the first compaction technique — summarisation. How to distil a long conversation into a brief, accurate summary that gives the model everything it needs to continue effectively.
