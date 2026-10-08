# Selective Retention

---

When you pack a bag for a long trip, you do not pack everything equally.

Some things go in because they are useful every day — charger, toothbrush, a change of clothes. Some things go in because they are essential for a specific moment — the document you need for check-in, the medicine you take once a week. And some things you deliberately leave behind because they are not worth the space.

You are making a judgment about what matters enough to carry.

Selective retention applies this same judgment to conversation history. Instead of summarising everything or truncating by age — you decide, explicitly, which specific pieces of information are important enough to keep verbatim, regardless of when they appeared.

---

## What Selective Retention Is

Selective retention is the practice of flagging specific exchanges, facts, or decisions as must-keep — preserved in full across any compaction that happens later.

Everything else can be summarised or truncated. The flagged items stay intact.

This is different from summarisation, which compresses everything. It is different from truncation, which drops by age. Selective retention says: this specific thing matters — keep it exactly as it is, no matter what else gets compressed.

---

## What Gets Selectively Retained

Not everything deserves selective retention. The question is: what information, if lost or paraphrased, would meaningfully degrade the conversation?

**User preferences established early** — if a student said in the third exchange "I find code examples confusing, please use analogies only" — that preference matters for every subsequent exchange. It should be retained verbatim, not paraphrased into a summary.

**Key decisions made during the conversation** — if a student decided halfway through "let me focus only on trees this session, I will do graphs next time" — that decision shapes everything after it. Retain it explicitly.

**Corrections made** — if the model gave an incorrect explanation and the student corrected it — "actually, my professor explained it differently" — that correction is critical. A summary might lose the nuance of what was corrected.

**Specific examples that worked** — if a particular analogy landed well and the student said "that makes sense, use this kind of example again" — retain that. It calibrates future responses in a way no summary captures as precisely.

---

## How to Implement Selective Retention

The simplest approach: add a section to your context package called RETAINED or PINNED.

When something important is established during the conversation, move it into this section. It sits alongside the context package — always present, always attended to, never part of what gets compressed.

```
CONTEXT PACKAGE:
[Authority]
[Exemplar]
[Constraint]
[Rubric]
[Metadata]

RETAINED (always keep — do not summarise or truncate):
- Student prefers analogies over code examples (established exchange 3)
- Student is focusing on trees only this session (decided exchange 11)
- Student found the "filing cabinet" analogy for hash tables very clear 
  (exchange 8) — use similar physical object analogies
```

When compaction happens — whether summarisation or truncation — the RETAINED section stays. It is treated the same as the context package itself.

---

## The Risk of Over-Retaining

Selective retention is powerful but can be misused. If you flag everything as must-keep, you have simply recreated the full conversation history — defeating the purpose of compaction entirely.

The discipline is in being selective. A useful rule: if you can capture the essence of something accurately in two sentences in a summary, it does not need to be selectively retained. Only retain things where the exact phrasing or the specific detail matters — where paraphrasing would lose something important.

For a study assistant used in a one-hour session, selective retention might produce three to five retained items at most. More than that is a sign of over-retaining.

---

## Quick Recap

- Selective retention flags specific pieces of information as must-keep — preserved verbatim across any compaction
- It is used for things that would meaningfully degrade if paraphrased — user preferences, key decisions, corrections, examples that worked
- Implement it with a RETAINED section in the context package — treated as permanent alongside the context package itself
- The discipline is in being selective — retain only what would genuinely be lost in a summary, not everything that seems important

---

## What Is Next

The next topic brings all compaction techniques together — summarisation, truncation, sliding windows, and selective retention — and shows how they work in combination during a real conversation.
