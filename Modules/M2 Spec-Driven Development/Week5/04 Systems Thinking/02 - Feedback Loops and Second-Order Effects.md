# Feedback Loops and Second-Order Effects

---

A thermostat keeps a room at 20 degrees.

When the temperature drops below 20, the heater turns on. The heater warms the room. When the temperature reaches 20, the heater turns off. The room cools. The heater turns on again.

This is a feedback loop. The output of the system (room temperature) feeds back into the input (heater on/off decision). The system regulates itself.

Feedback loops are everywhere — in nature, in economics, in software systems, in AI systems. Some keep systems stable. Some make them spiral out of control. Understanding which kind you are dealing with changes how you design and test.

---

## Two Types of Feedback Loops

**Balancing loops** — also called negative feedback loops — counteract change and push the system back toward a stable state. The thermostat is a balancing loop. When temperature rises, the heater turns off. When temperature falls, the heater turns on. The loop corrects deviation.

**Reinforcing loops** — also called positive feedback loops — amplify change. The more something happens, the more it tends to happen. These loops produce growth, collapse, or runaway behaviour — not stability.

Both types appear in AI systems. Balancing loops are generally what you want. Reinforcing loops are generally what you need to watch for.

---

## Feedback Loops in the Study Assistant

**A balancing loop — the eval harness cycle**

```
System fails a test case
    → Developer identifies the failing criterion
        → Developer fixes the context package
            → System passes the test case
                → Pass rate improves
                    → System is more reliable
```

This is a balancing loop. A failure triggers a fix that reduces the failure. The system converges toward reliability. This is the SDD cycle operating as intended.

**A reinforcing loop — the over-reliance spiral**

```
Student finds the assistant helpful
    → Student uses it more
        → Student uses it instead of reading textbooks
            → Student's independent reasoning weakens
                → Student becomes more dependent on the assistant
                    → Student finds it even more essential
```

This is a reinforcing loop. Each step amplifies the previous one. The student is not making a bad decision at any individual step — but the cumulative effect is increasing dependence on a tool that was designed to supplement, not replace, active study.

This loop was not visible in the test cases. It only emerges over time, through real usage patterns. Without systems thinking, you would not anticipate it.

**A reinforcing loop — constraint weakening**

```
Student asks polite out-of-scope question
    → Assistant provides a partial explanation (constraint weakened)
        → Student sees the system will respond to these requests
            → Student asks more politely-framed out-of-scope questions
                → Constraint is tested more often
                    → More violations occur
```

Once a constraint is seen to yield, users test it more. More testing means more violations. More violations mean the constraint is effectively gone — not because the context package changed, but because the usage pattern changed.

---

## Second-Order Effects in Practice

A second-order effect is the consequence of a first-order change — the thing that happens because the intended thing happened.

**Change: Add exemplars showing very detailed explanations**

First-order effect: Response quality improves — responses are more precise and complete.

Second-order effect: Students begin expecting detailed responses for every question. Simple questions that previously produced concise answers now produce longer ones. Session length increases. Context window fills faster. FM5 (constraint drift) becomes more likely.

The exemplars made the system better — and also made it more vulnerable to a specific failure mode.

**Change: Strengthen the out-of-scope redirect constraint**

First-order effect: FM1 (out-of-scope explanation) rate decreases.

Second-order effect: Students who receive redirects on legitimate boundary questions become frustrated. They stop using the assistant for those questions. They miss coverage on topics that were actually in scope but phrased in a way that triggered the redirect.

The fix for FM1 introduced a new failure mode — false negatives, where in-scope questions are incorrectly redirected. This is an over-correction second-order effect.

---

## How to Anticipate Second-Order Effects

For every change to the system, ask two questions before implementing:

**Question 1 — What does this change make easier or more likely?**

If the exemplars make detailed responses easier to produce — what does a detailed response make more likely downstream? Longer sessions. More context window consumption. Faster drift.

**Question 2 — What does this change make harder or less likely?**

If the strengthened constraint makes out-of-scope explanations less likely — what does that make harder? Students getting help on legitimate boundary questions. Nuanced cases at the edge of the covered list.

These questions do not always reveal second-order effects. But asking them consistently prevents the most common ones.

---

## Adding Second-Order Thinking to the Fix Queue

When you add a failure mode to the fix queue, add a second-order risk field:

```
PLANNED FIX: Strengthen out-of-scope constraint (FM1)

Second-order risk: Over-correction may cause false negatives 
on legitimate boundary questions. 

Mitigation: After fix, run boundary test cases (TC-EC1 through 
TC-EC4) specifically to check for false negatives. If false 
negative rate increases, add examples of legitimate boundary 
questions to the Exemplar role.
```

The fix is documented. The second-order risk is documented. The mitigation for the second-order risk is documented. This is what it looks like to manage a system, not just build one.

---

## Quick Recap

- Feedback loops are cycles where outputs feed back into inputs — balancing loops push toward stability, reinforcing loops amplify change
- The SDD cycle (fail → fix → re-verify) is a balancing loop — it pushes the system toward reliability
- Reinforcing loops in AI systems include over-reliance spirals and constraint-weakening patterns — both only visible over time through real usage
- Second-order effects are the consequences of first-order changes — every fix creates new conditions that may enable new failures
- For every change, ask: what does this make easier or more likely? What does this make harder or less likely?

---

## What Is Next

The next topic covers how specs constrain AI — the specific mechanism by which a well-written specification prevents the failure modes and second-order effects you have just studied.
