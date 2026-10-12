# Selective Retention

---

When you pack a bag for a long trip, you do not pack everything equally.

Some things go in because they are useful every day — charger, toothbrush, a change of clothes. Some things go in because they are essential for a specific moment — the document you need for check-in, the medicine you take once a week. And some things you deliberately leave behind because they are not worth the space.

You are making a judgment about what matters enough to carry.

Selective retention applies this same judgment to conversation history. Instead of summarising everything or truncating by age — you decide, explicitly, which specific pieces of information are important enough to keep verbatim, regardless of when they appeared.

---

## The Sample Conversation

To make this concrete, here is the conversation we will use across this topic and the next. Six exchanges between a student and the study assistant:

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

This is the reference conversation. Exchange numbers used in this topic and the next always refer back to these six exchanges.

---

## What Selective Retention Is

Selective retention is the practice of flagging specific exchanges, facts, or decisions as must-keep — preserved in full across any compaction that happens later.

Everything else can be summarised or truncated. The flagged items stay intact.

This is different from summarisation, which compresses everything. It is different from truncation, which drops by age. Selective retention says: this specific thing matters — keep it exactly as it is, no matter what else gets compressed.

---

## What Gets Selectively Retained

Not everything deserves selective retention. The question is: what information, if lost or paraphrased, would meaningfully degrade the conversation?

**User preferences established early**

Look at Exchange 3 in the sample conversation. The student said: *"I find the physical object analogies much easier than process analogies. The plate and book examples clicked immediately."*

This preference matters for every subsequent exchange. The assistant confirmed it would use physical object analogies throughout. If this gets lost in compaction — paraphrased into something like "student prefers clear analogies" — the specific instruction is gone. Future responses might drift back to process analogies.

Exchange 3 should be selectively retained verbatim.

**Key decisions made during the conversation**

Exchange 6: the student decided to move from stacks and queues to trees. This shapes everything that follows. If compaction happened between Exchange 6 and Exchange 7, the model needs to know the student has finished with stacks and queues and is now on trees — not in a summary, but as a clear decision point.

**Corrections made**

If a student says "that explanation was wrong, my professor explained it differently" — that correction is critical. A summary might lose the nuance of what exactly was corrected.

**Specific examples that worked**

The student confirmed in Exchange 3 that the plate stack and book stack examples clicked. Retaining this means future responses can reference these same examples — "like the cafeteria pile example we used earlier" — building continuity across the session.

---

## How to Implement Selective Retention

The simplest approach: add a section to your context package called RETAINED.

When something important is established during the conversation, move it into this section. It sits alongside the context package — always present, always attended to, never part of what gets compressed.

Using the sample conversation:

```
RETAINED (always keep — do not summarise or truncate):

From Exchange 3:
"Student explicitly said physical object analogies work better 
than process analogies. Plate stack and book stack examples 
clicked immediately. Use physical object analogies throughout."

From Exchange 6:
"Student has finished stacks and queues. Now moving to trees. 
Do not return to stacks or queues unless the student asks."
```

When compaction happens — whether summarisation or truncation — the RETAINED section stays. It is treated the same as the context package itself.

---

## The Risk of Over-Retaining

Selective retention is powerful but can be misused. If you flag everything as must-keep, you have simply recreated the full conversation history — defeating the purpose of compaction entirely.

The discipline is in being selective. A useful rule: if you can capture the essence of something accurately in two sentences in a summary, it does not need to be selectively retained. Only retain things where the exact phrasing or the specific detail matters — where paraphrasing would lose something important.

For the sample conversation — six exchanges — selective retention produces two retained items. That is the right scale.

---

## Quick Recap

- Selective retention flags specific pieces of information as must-keep — preserved verbatim across any compaction
- Use the sample conversation as reference: Exchange 3 (analogy preference) and Exchange 6 (topic decision) are the items worth retaining
- It is used for things that would meaningfully degrade if paraphrased — user preferences, key decisions, corrections, examples that worked
- Implement it with a RETAINED section in the context package — treated as permanent alongside the context package itself
- The discipline is in being selective — retain only what would genuinely be lost in a summary

---

## What Is Next

The next topic brings all compaction techniques together and shows them working on the same sample conversation — so you can see exactly how summarisation, truncation, sliding windows, and selective retention combine in a real session.
