# ReAct — Reason, Act, Observe

---

Watch someone assemble furniture without reading the instructions.

They pick up a piece. Try to fit it somewhere. It does not work. They try somewhere else. Flip it around. Eventually something clicks — but by accident. Lots of action, very little thinking in between.

Now watch someone who stops before each step. They look at the diagram. They identify the piece. They find where it goes. Then they pick it up and place it. Each action is preceded by a moment of deliberate thinking.

The second person makes far fewer mistakes. Not because they are smarter — but because they think before they act.

ReAct gives agents this same discipline.

---

## What ReAct Is

ReAct stands for **Reason, Act, Observe**.

It is the pattern the brain follows inside every loop. Instead of jumping straight to a tool call, the brain first reasons — what do I know, what is still missing, what should I do next and why. Then it acts. Then it observes what came back. Then it reasons again.

**Reason → Act → Observe. Repeat.**

This came from a research paper published in 2022. The finding was straightforward: agents that reason before acting make significantly fewer mistakes than agents that act directly. The reasoning step surfaces gaps — things the agent does not yet have — before committing to an action.

---

## The Three Steps

**Reason** — The brain thinks out loud before doing anything. What do I know so far? What is still missing? What should I do next and why? This is internal — not shown to the user. Like someone thinking through a problem before speaking.

**Act** — Based on that reasoning, the brain produces a specific tool call with exact inputs. Not a vague intention — a precise instruction.

**Observe** — The tool runs. The result comes back. The brain reads it carefully. This observation becomes the foundation for the next round of reasoning.

Then the cycle repeats.

---

## Why the Reason Step Matters

Without it, the brain picks tools based on instinct. Results come back. Another tool gets picked. Eventually an answer appears — but it may be incomplete because the brain never stopped to check what was still missing.

With the reason step, the brain explicitly asks before every action: *"Do I have what I need? What is the gap?"* This one question catches problems before they become wrong answers.

---

## Seeing It Work

Goal: *"What is the current exchange rate between the dollar and the euro, and how much would $500 convert to?"*

```
REASON: I need two things — the current rate and a conversion 
        calculation. Rates change daily. I cannot use training 
        data. Search first.

ACT: search_web → "dollar to euro exchange rate today"

OBSERVE: 1 USD = 0.92 EUR as of today.

---

REASON: I have the rate. The next step is the calculation. 
        I already have everything I need for it — no more 
        searching required.

ACT: calculate → 500 × 0.92

OBSERVE: 460

---

REASON: I have both pieces — the rate and the converted amount. 
        I can answer now.

FINAL ANSWER: "The current rate is 1 USD = 0.92 EUR. 
               $500 converts to approximately €460."
```

Notice Loop 2. The reason step recognised that searching was done — the next step was calculation, not another search. Without reasoning, the brain might have searched "$500 in euros" instead of using the rate it already had. The reason step caught that shift.

---

## Quick Recap

- ReAct stands for Reason, Act, Observe — the three-step pattern the brain follows inside every loop
- The reason step comes before every action — what do I know, what is missing, what should I do next
- Reasoning before acting catches gaps before they become wrong or incomplete answers
- Agents that use ReAct make significantly fewer mistakes than agents that act directly

---

## What Is Next

ReAct makes the brain more disciplined inside each loop. But even well-structured agents fail in predictable ways. The next topic introduces failure modes — what they are, why they happen, and why you need to know them before you build anything.
