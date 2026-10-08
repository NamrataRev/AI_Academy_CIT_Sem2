# Detecting Degradation

---

A frog placed in boiling water jumps out immediately. A frog placed in cold water that slowly heats up does not notice until it is too late.

Context degradation works the same way. It does not happen suddenly. It creeps in gradually — one response slightly longer than the rubric specified, the next response missing the analogy, the one after that crossing a constraint. Each individual drift is small enough to miss. By the time the responses are clearly wrong, the conversation has been unreliable for a while.

Detecting degradation means knowing what signals to watch for — so you catch the drift early, not late.

---

## The Four Signals

**Signal 1 — Response length changes**

The Rubric specified responses under 120 words. Early responses were 90-110 words. Now they are 180-200 words.

Length is the easiest signal to detect because it is measurable. If your rubric specified a length and the responses are consistently longer or shorter than that length — something has drifted.

This is usually the first thing to drift because length constraints require ongoing attention. As the context package moves further from the current message, the model holds the length requirement less precisely.

**Signal 2 — Structure changes**

The Rubric specified: analogy, definition, use case — in that order. Early responses followed this structure precisely. Now responses start with the definition. The analogy appears sometimes, sometimes not. The use case has disappeared.

When the structure of responses starts varying — appearing in different orders, with some parts missing — the Rubric is no longer being applied consistently.

**Signal 3 — Constraints being crossed**

A constraint said: no recursion examples. For the first fifteen responses, no recursion appeared. Response sixteen contains a recursion example.

When a specific constraint that was being respected suddenly stops being respected — this is a clear sign of degradation. The constraint is technically still in the context. But it is no longer receiving enough attention to influence the response.

**Signal 4 — Tone and voice shifting**

The Authority defined a specific tone — warm, encouraging, pitched at a second-year student. Early responses matched this precisely. Now responses sound more formal, more textbook-like, more generic.

Tone drift is the subtlest signal and the hardest to measure — but it is often the most noticeable to the user. When students say "it suddenly feels different" or "it stopped being as helpful" — tone drift is often the cause.

---

## How to Check Systematically

For any AI system you build that runs across multiple turns, build a simple check into your evaluation:

**After every ten interactions**, review three things:
1. Pick three recent responses and measure their length. Does it match the Rubric?
2. Check the structure of those three responses. Are all required parts present in the right order?
3. Look for any constraint violations — topics, vocabulary, format rules that should not have appeared.

This takes five minutes. It catches drift before it becomes a significant problem.

For more sophisticated systems, automate this check — run the same ten test questions against the system at regular intervals and compare the outputs against the rubric criteria.

---

## What to Do When You Detect Degradation

**Option 1 — Restart the conversation**

The simplest fix. Start a new session with the full context package. The context package is fresh, at the top of the window, fully attended to. Degradation resets.

For a study assistant used in sessions — this is the natural approach. Each session starts fresh.

**Option 2 — Reinsert the context package**

Mid-conversation, paste the context package again as a message. This brings the key instructions back near the current message — closer to where attention is strongest.

This works but is not elegant. It is more of a patch than a fix.

**Option 3 — Use compaction**

Summarise the conversation so far into a compact representation that preserves the essential information. Replace the growing conversation history with this summary. This reduces the context length, brings the context package closer to the current message, and extends the conversation's useful life.

Compaction is covered in depth in the next section — it is the systematic solution to the degradation problem.

---

## Quick Recap

- Context degradation happens gradually — catch it early through systematic checking, not when responses are obviously wrong
- Four signals: response length changes, structure changes, constraints being crossed, tone and voice shifting
- Check every ten interactions — measure length, check structure, look for constraint violations
- Three options when degradation is detected: restart the conversation, reinsert the context package, or use compaction

---

## What Is Next

The next topic introduces context compaction — the systematic approach to extending a conversation's useful life by summarising earlier turns without losing the essential information the model needs.
