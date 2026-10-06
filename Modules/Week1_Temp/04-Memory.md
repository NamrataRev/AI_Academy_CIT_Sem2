# Memory — The Notepad

---

Imagine you are researching something across multiple websites.

You find a great price on the first site. You open a second site to compare. By the time you are on the third site, you have forgotten the first price. You go back. You find it again. You move to the fourth site. You forget again.

Now imagine you have a notepad next to you. Every time you find something useful, you write it down. You never lose anything. Each new site you visit builds on everything you already noted.

That notepad is memory inside an agent.

---

## Why Memory Exists

Without memory, every loop the agent runs starts completely fresh.

The brain reads the goal — but has no idea what happened in any previous loop. It has forgotten the search results from Loop 1 by the time Loop 2 starts. It would search for the same things again. And again. Never making progress.

Memory is what gives the agent continuity. Each loop builds on the last because everything found so far is written down and available to read.

---

## Two Kinds of Memory

**In-context memory — the notepad on the desk**

This is everything sitting in the current conversation. Every tool result, every piece of information found so far — all of it stays active and the brain can read it instantly.

Fast. Immediate. But limited — there is only so much that fits. And when the session ends, it is gone. Like a whiteboard that gets wiped clean at the end of the day.

Most agents only use in-context memory. For tasks that fit within a single session, it is enough.

**External memory — the filing cabinet**

This is information stored outside the conversation — in a database, a file, or a vector store. The agent retrieves what it needs when it needs it.

Holds far more. Persists across sessions — still there tomorrow, next week, next month. Like a filing cabinet full of notes from every previous conversation.

More sophisticated agents use both — keeping active information on the notepad during a task, and reaching into the filing cabinet for things from previous sessions.

---

## Memory in the Laptop Example

After Loop 1, the notepad looks like this:

```
Goal: best laptop under $700 for coding
Found: Acer Aspire 5 ($649), Lenovo IdeaPad ($629), HP Pavilion ($679)
```

In Loop 2, the brain reads this first. It knows which laptops to compare. It does not search for laptops again — it asks specifically about the ones already found.

After Loop 2, the notepad grows:

```
Goal: best laptop under $700 for coding
Found: Acer Aspire 5 ($649), Lenovo IdeaPad ($629), HP Pavilion ($679)
Comparison: Acer has 16GB RAM — others have 8GB at similar prices
Leading candidate: Acer Aspire 5
```

In Loop 3, the brain reads this richer picture. It knows the leading candidate. It does not repeat the comparison — it moves to verification.

Each loop is smarter than the last because the notepad keeps growing.

---

## What Breaks Without Memory

An agent without working memory is like trying to solve a jigsaw puzzle but every few seconds someone scrambles the pieces you already placed.

You start again. You place some pieces. They get scrambled. You start again.

You never make progress because each attempt erases the previous one.

For an agent, this means the same searches run over and over. The goal is never reached. Memory is what makes multi-step tasks possible.

---

## Quick Recap

- Memory is the notepad — every result gets written down so the next loop builds on it instead of starting over
- In-context memory is fast but temporary — like a whiteboard, wiped when the session ends
- External memory persists across sessions and holds much more — like a filing cabinet
- Without memory, every loop starts from zero and the agent never makes progress

---

## What Is Next

You now have three of the four parts — the brain, the hands, and the notepad. The last part is what connects them into a working system. That is the planning loop, and that is what the next file covers.
