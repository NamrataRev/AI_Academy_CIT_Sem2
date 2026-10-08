# Truncation and Sliding Windows

---

Imagine reading a very long WhatsApp conversation that you joined halfway through.

You do not go back to the very first message from three weeks ago. You scroll back a reasonable amount — maybe the last fifty messages — and that gives you enough context to understand what is happening now. The older messages are still there if you really need them. But for the current conversation, you only actively read the recent ones.

This is the intuition behind truncation and sliding windows. Instead of summarising the full history, you simply limit how far back the model looks — keeping the most recent exchanges and letting the older ones drop off.

---

## Truncation — The Simplest Approach

Truncation is exactly what it sounds like. When the conversation gets too long, you cut the oldest exchanges and keep only the most recent ones.

If your context window comfortably holds twenty exchanges — you keep the last twenty. Exchange twenty-one pushes exchange one out. Exchange twenty-two pushes exchange two out. The window moves forward as the conversation grows.

**What it preserves:** The most recent exchanges — which are usually the most relevant to what is happening right now.

**What it loses:** Everything older than the cutoff. Any understanding built in early exchanges that is not reflected in recent ones.

**When it works well:** Conversations where each exchange is relatively self-contained. Customer support queries. Question-and-answer sessions where each question does not depend heavily on earlier ones.

**When it breaks down:** Conversations where early context matters continuously. If the student established an important preference in exchange three — "I learn better with code examples than analogies" — and that gets truncated, the model loses it.

---

## Sliding Windows — A Refinement

A sliding window is truncation with one important addition: the context package is always kept.

In pure truncation, if the conversation gets long enough, even the context package might get cut. The model loses its Authority, Constraints, and Rubric — everything that made it reliable.

A sliding window protects against this. It works like this:

```
[Context package — always kept, never truncated]
[Last N exchanges — the sliding window]
```

The context package stays at the top, fully intact. Below it, the conversation history keeps only the last N exchanges. As new exchanges come in, old ones drop off — but the context package never moves.

This is the most common approach for production AI systems that need to handle long conversations. It is simple to implement, predictable in behaviour, and guarantees the context package always has strong attention.

---

## Truncation vs Summarisation — Which to Use

| | Truncation / Sliding Window | Summarisation |
|---|---|---|
| **How it works** | Drops oldest content | Compresses content into a summary |
| **What is lost** | All older exchanges | Verbose details — substance is preserved |
| **Implementation** | Simple — just limit history length | Requires model call to generate summary |
| **Best for** | Self-contained exchanges | Conversations with accumulated understanding |
| **Risk** | Losing important early context | Summary may miss something important |

For the study assistant: summarisation is usually better. A student's understanding builds across the session — what they established in exchange five matters in exchange twenty. Dropping exchange five entirely is worse than summarising it.

For a simple Q&A assistant where each question is independent: truncation is simpler and works just as well.

---

## Combining Both

The most robust approach combines both techniques:

1. Keep the context package always — never truncate it
2. Keep a short sliding window of the most recent exchanges — for immediate context
3. Summarise anything older than the window into a compact summary

The result:

```
[Context package — full, always present]
[Conversation summary — everything older than the window]
[Last 5-10 exchanges — the sliding window]
```

This gives the model its identity and rules (context package), the accumulated understanding of the session (summary), and the immediate conversational thread (sliding window) — without the full weight of every exchange ever made.

---

## Quick Recap

- Truncation drops the oldest exchanges when the conversation gets too long — simple but risks losing important early context
- A sliding window keeps the context package intact while truncating only the conversation history — the most common production approach
- Summarisation preserves substance but requires a model call to generate — better for conversations where understanding accumulates
- Combining both is the most robust approach: context package always present, older history summarised, recent exchanges kept in full

---

## What Is Next

The next topic covers selective retention — a more deliberate approach where specific pieces of information are explicitly flagged to be kept, regardless of how old they are or where they sit in the conversation.
