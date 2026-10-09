# The Governance Note — Structure

---

Every engineering drawing has a title block.

Not because the drawing would be technically wrong without it — the design is the design regardless. But the title block says who drew it, when, what standard it was designed to, what revision it is, and who approved it. Without it, the drawing is a set of lines. With it, it is a document — accountable, traceable, usable by anyone who needs to work with it.

The Governance Note is the title block for AI systems.

It does not change what the system does. It makes the system accountable — stating what it is for, what risks it carries, what framework applies, and who is responsible. Without it, a context package is a useful tool. With it, it is a responsible artefact.

From this point forward, every system you build includes a Governance Note.

---

## What the Governance Note Contains

A Governance Note has six sections. Each one answers a specific question about the system and its governance.

---

**Section 1 — System Description**

*What does this system do?*

One to two sentences. Plain language. What the system is for, who it serves, and what it produces.

```
This is a study assistant for second-year BTech Computer Science 
students preparing for their Data Structures and Algorithms exam. 
It explains concepts on request using structured analogies, 
definitions, and use cases.
```

---

**Section 2 — Risk Category**

*What risk category does this system fall into, and why?*

Name the applicable framework, state the category, and give a one-sentence justification.

```
EU AI Act: Minimal Risk
Justification: The system provides educational explanations to 
students who retain full agency over how they use the information. 
It does not make automated decisions that affect access to education, 
assessment outcomes, or any rights.

Note: If the system were used to automatically assess or grade 
students, it would be reclassified as High Risk under EU AI Act 
category 3 (education and vocational training).
```

---

**Section 3 — Applicable Obligations**

*What does the risk category require?*

List the specific obligations that apply, and state how they are being met.

```
EU AI Act (Minimal Risk):
- No mandatory obligations. Good governance practices applied voluntarily.

Transparency (all frameworks):
- Obligation: Users must know they are interacting with an AI.
- How met: Every session begins with: "I am an AI study assistant, 
  not a human tutor."

NIST AI RMF:
- Govern: Context package documentation maintained with version history
- Map: Risk map documented in context package documentation
- Measure: Evaluation harness run before deployment and after changes
- Manage: Failed eval harness criteria addressed before deployment
```

---

**Section 4 — Known Risks and Mitigations**

*What are the specific risks this system carries, and how are they mitigated?*

Draw directly from the risk map completed in the Map function.

```
Risk 1: Inaccurate explanations
Mitigation: Eval harness includes accuracy checks; students advised 
to verify with course materials

Risk 2: Out-of-scope topics explained without flagging
Mitigation: Explicit constraint in context package; tested in 
eval harness with 100% pass rate required

Risk 3: Silent failure — confident wrong answer
Mitigation: Adversarial inputs in eval harness; governance note 
advises students to verify uncertainty

Risk 4: Residual risks not fully mitigated
Three-topic combination questions may produce responses exceeding 
the word limit. Documented as known limitation. Students advised 
that complex questions may produce longer responses.
```

---

**Section 5 — Human Oversight**

*What human oversight is in place?*

Describe what human review exists — or be honest if there is none.

```
Pre-deployment: Context package reviewed and eval harness run 
by builder before any student use.

During use: No automated monitoring. Students are advised to 
flag any responses that seem incorrect to their course lecturer.

Post-deployment: Eval harness re-run after any change to the 
context package. Changelog updated with what changed and why.

Note: This system is minimal risk and does not make automated 
decisions — continuous human oversight is not required. 
Students retain full agency over how they use its outputs.
```

---

**Section 6 — Responsible Party**

*Who is responsible for this system?*

Name the responsible party and what their responsibility covers.

```
Builder: [Name]
Institution: [University name]
Responsibility: Design, testing, documentation, and maintenance 
of the context package. Responsible for ensuring the eval harness 
is run before deployment and after significant changes.

This system is a course project and is not deployed commercially. 
Responsibility is limited to the course context.
```

---

## The Complete Governance Note — At a Glance

```
GOVERNANCE NOTE

System: BTech DSA Study Assistant v1.2

1. SYSTEM DESCRIPTION
   [What it does, who it serves, what it produces]

2. RISK CATEGORY
   [Framework, category, justification, reclassification triggers]

3. APPLICABLE OBLIGATIONS
   [What is required and how each requirement is met]

4. KNOWN RISKS AND MITIGATIONS
   [Each risk, its mitigation, and any residual unmitigated risk]

5. HUMAN OVERSIGHT
   [Pre-deployment, during use, post-deployment]

6. RESPONSIBLE PARTY
   [Who, what institution, what they are responsible for]
```

Six sections. One page. Answers every governance question a reviewer, a user, or a future maintainer would ask.

---

## Why This Becomes a Habit

The Governance Note is required for every assessed submission from this point in the course. Not because it is bureaucratic overhead — because it builds the habit of thinking about governance before, during, and after building.

An engineer who has written fifty Governance Notes over their student years will write them automatically in professional practice. They will ask "what risk category is this?" as naturally as they ask "what language should I use?" or "what database does this need?"

Governance thinking is not a step you add at the end. It is a lens you apply throughout. The Governance Note is where that lens becomes visible.

---

## Quick Recap

- The Governance Note has six sections: system description, risk category, applicable obligations, known risks and mitigations, human oversight, and responsible party
- It makes a system accountable — stating what it is, what risks it carries, what framework applies, and who is responsible
- Required for every assessed submission from this week forward
- The goal is not compliance with a template — it is building the habit of governance thinking as a natural part of engineering practice

---

## What Is Next

The next topic shows a complete worked example of a Governance Note — the full document for the BTech study assistant, filled in completely, so you have a concrete model to follow for your own submissions.
