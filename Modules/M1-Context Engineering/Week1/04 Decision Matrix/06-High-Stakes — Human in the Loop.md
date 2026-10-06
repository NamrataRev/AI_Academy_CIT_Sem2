# High-Stakes — Human in the Loop

---

Aeroplanes have autopilot. It handles altitude, speed, and navigation automatically. It is reliable, well-tested, and handles the vast majority of a flight without the pilot touching anything.

But autopilot does not land the plane. Not because it cannot — modern systems can. Because the consequences of a failure at that moment are too severe to leave entirely to an automated system. A human is in the loop for the parts where getting it wrong matters most.

This is the principle behind human-in-the-loop design. Automate what can be automated. Keep a human involved where the cost of a wrong answer is too high to accept without verification.

---

## What High Stakes Means

A task is high stakes when a wrong answer causes real harm — not just inconvenience, but consequences that are difficult or impossible to reverse.

Financial decisions that move money. Medical recommendations that affect treatment. Legal analysis that determines rights or obligations. Safety-critical systems where errors injure people.

In these situations, an agent can do the research, find the information, and draft a recommendation. But a human must review that output before it is acted on. The agent reduces the work. The human takes responsibility for the decision.

---

## What Human-in-the-Loop Looks Like

The agent runs its full loop — searching, reasoning, compiling. It produces a well-structured output with its findings and recommendation.

Then it stops.

It does not act on the recommendation itself. It does not send the email, approve the transaction, or update the record. It presents what it found and waits.

A human reads it. They check the key claims. They apply their judgment. They decide whether to proceed, modify, or reject. Only then does the action happen.

The agent is the research assistant. The human is the decision-maker.

---

## A Concrete Example

A company uses an agent to review contracts for unusual clauses before signing.

The agent reads the contract, searches for relevant legal precedents, identifies three clauses that appear non-standard, and produces a summary flagging the risks.

The agent does not sign the contract. It does not say "this is safe to proceed." It presents its findings to the legal team.

A lawyer reads the summary. They examine the three flagged clauses. They apply their professional judgment. They decide whether to proceed, negotiate, or reject.

The agent saved the lawyer hours of initial reading. The lawyer caught the one thing the agent's risk assessment missed. Both are necessary.

---

## Why an Agent Alone Is Not Enough Here

All four failure modes are possible in any agent. Silent failures in particular — where the agent presents a confident answer based on fabricated or incomplete information — are almost undetectable without independent verification.

For low-stakes tasks, the cost of an occasional silent failure is manageable. For high-stakes tasks, the cost is not. One wrong recommendation in a medical, financial, or legal context can cause harm that no amount of correct answers before it can undo.

Human oversight is not a backup for when things go wrong. It is a required part of the design for any high-stakes application.

---

## Quick Recap

- High-stakes tasks are those where a wrong answer causes real, difficult-to-reverse harm
- In these situations, an agent does the research and drafts the recommendation — a human reviews before any action is taken
- The agent is the research assistant; the human is the decision-maker
- Human-in-the-loop is not optional for high-stakes applications — it is a required design choice, not a fallback

---

## What Is Next

The next topic covers the judgment framework — a set of questions that help you decide not just which tool to use, but when agent autonomy is acceptable and when it is not.
