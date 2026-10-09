# Map

---

Before a doctor treats a patient, they take a history.

Not because they already know what is wrong — because they need to understand the specific situation before they can assess and manage it. Who is this patient? What is their background? What are the risk factors specific to them? What could go wrong?

The Map function works the same way. Before you can measure risks or manage them, you need to understand what the risks actually are for this specific system, in this specific context, affecting these specific people.

Mapping is the work of understanding — before measuring or managing begins.

---

## What Map Covers

The Map function asks three questions:

**Who is affected by this system?**
**What could go wrong?**
**What is the context this system operates in?**

These questions sound simple. Answering them rigorously is what makes Map valuable.

---

## Who Is Affected

Start with the users — but do not stop there. A system affects more people than just the ones who interact with it directly.

For the study assistant:

*Direct users:* Second-year BTech CSE students who ask it questions and use its responses for revision.

*Indirect affected parties:* The students' professors — who will grade exams based on what students have understood. The students' future employers — who will hire based on the qualifications those exams lead to. The institution — whose reputation is linked to the quality of its graduates' education.

For most minimal-risk systems, the indirect effects are small and the direct users are the primary concern. But even thinking through the question surfaces things you would otherwise miss.

For a higher-risk system — one that affects hiring decisions or access to services — the affected parties analysis becomes essential. People who are rejected by an automated system are affected just as much as people who use it directly.

---

## What Could Go Wrong

This is where you identify the specific failure modes and risks for your system.

For the study assistant, a structured risk map looks like this:

```
RISK 1: Inaccurate explanations
Who is harmed: Students who study incorrect information
How likely: Low — the model is generally accurate on well-covered topics
How serious: Medium — a wrong explanation affects exam performance
Mitigation: Eval harness tests accuracy; students encouraged to 
            cross-reference with course materials

RISK 2: Out-of-scope topics explained without flagging
Who is harmed: Students who receive explanations of concepts they 
               are not prepared to encounter yet
How likely: Medium without constraints; low with well-written constraints
How serious: Medium — confusion about advanced concepts before 
             prerequisites are covered
Mitigation: Constraint role explicitly prohibits this; 
            eval harness includes out-of-scope test inputs

RISK 3: Silent failure — confident wrong answer
Who is harmed: Students who trust a response that is subtly incorrect
How likely: Low but non-zero for edge cases
How serious: High — hardest to detect, most likely to affect exam
Mitigation: Governance note acknowledges this risk; 
            students advised to verify with course materials 
            for any concept they are uncertain about

RISK 4: Over-reliance
Who is harmed: Students who use the assistant instead of actively 
               studying, producing shallow understanding
How likely: Medium — depends on how students choose to use it
How serious: Medium — affects depth of understanding, not just accuracy
Mitigation: Authority defines the assistant's role as supplementary, 
            not primary; responses designed to explain, not to replace 
            active engagement
```

This is a risk map. Not a guarantee that nothing will go wrong — but a structured understanding of what the risks are, who they affect, how likely and serious each is, and what mitigation is in place.

---

## What Context the System Operates In

The same system in different contexts carries different risks.

A study assistant used by a student the night before an exam carries more risk than one used casually during a revision session — because the stakes of that interaction are higher. A study assistant used by students who have no other support resource carries more risk than one used alongside regular tutoring — because there is no backup if it fails.

Mapping the context means being honest about these factors:

- What are the stakes of this specific use?
- What alternatives do users have if this system fails?
- Is the system being used in conditions its design assumed?

For the study assistant: it is designed as a supplementary tool for students who also attend lectures, have access to textbooks, and can ask their professor questions. Its risk profile is different if it is being used as the primary or only source of explanation.

---

## Quick Recap

- Map identifies who is affected, what could go wrong, and what context the system operates in — before measuring or managing
- Affected parties include direct users and anyone indirectly affected by the system's outputs
- A risk map documents each risk: who is harmed, how likely, how serious, and what mitigation is in place
- Context matters — the same system in different use conditions carries different risks

---

## What Is Next

The next topic covers the Measure function — how to quantify the risks identified in Map, what metrics to use, and how the evaluation harness connects directly to the Measure function of NIST AI RMF.
