# Obligations by Risk Level

---

Knowing which risk category your system falls into is only the first step.

The second step is understanding what that category actually requires you to do. Different risk levels come with different obligations — some light, some substantial. This topic walks through each level and what it means in practice.

---

## Minimal Risk — Encouraged but Not Required

For minimal risk systems — the study assistant, the recommendation engine, the grammar checker — the EU AI Act imposes no specific obligations.

This does not mean governance does not matter. It means regulation does not mandate it. Good governance is still the right practice:

- Document what the system does and does not do
- Test it before deploying to real users
- Be honest about its limitations

These are engineering professionalism, not regulatory compliance. But for minimal risk systems, a regulator will not knock on your door if you skip them.

For the work in this course, treat minimal risk systems as an opportunity to practise good governance voluntarily — building the habits you will need when you work on higher-risk systems professionally.

---

## Limited Risk — Transparency is the Obligation

For limited risk systems — chatbots, deepfakes, emotion recognition — the primary obligation is disclosure.

**What must be disclosed:**

If the system is a chatbot or conversational agent, users must be told they are interacting with an AI — not a human. This disclosure must happen at the start of the interaction, not buried in a terms-of-service document.

If the system generates synthetic content — images, videos, audio — that could be mistaken for real content, it must be labelled as AI-generated.

If the system analyses emotions, the user must be informed that their emotional state is being processed.

**What this means for you:**

If you build a system that users interact with conversationally — even for a course project — and there is any possibility a user might not realise they are talking to an AI, add a disclosure. A simple line at the start of every interaction: *"I am an AI study assistant, not a human tutor."*

This is not onerous. It is a single sentence. But it is the obligation that applies, and it reflects an important principle: users have a right to know they are interacting with an AI.

---

## High Risk — Eight Obligations Before Deployment

For high-risk systems, the EU AI Act specifies eight obligations that must be met before the system can be deployed. These are substantial — they represent real engineering and documentation work.

**Obligation 1 — Risk management system**
A documented process for identifying, assessing, and mitigating risks throughout the system's lifecycle. Not a one-time assessment — an ongoing process that continues after deployment.

**Obligation 2 — Data governance**
Training, validation, and test datasets must meet defined quality standards. The data must be representative, free from biases that would cause discriminatory outcomes, and appropriate for the intended purpose.

**Obligation 3 — Technical documentation**
Comprehensive documentation of the system's design, capabilities, limitations, training process, and performance metrics. Must be detailed enough for a regulator to assess compliance.

**Obligation 4 — Transparency and user information**
Users must receive clear information about what the system does, its capabilities and limitations, what human oversight is in place, and how to interpret its outputs.

**Obligation 5 — Human oversight**
High-risk systems must include mechanisms for human oversight. This means: humans can monitor the system's operation, understand what it is doing and why, intervene when necessary, and override its outputs. Fully automated high-stakes decisions without human oversight are not compliant.

**Obligation 6 — Accuracy, robustness, and cybersecurity**
The system must achieve an appropriate level of accuracy for its intended purpose. It must be robust against errors, faults, and inconsistencies. It must be protected against adversarial attacks — including prompt injection and data poisoning.

**Obligation 7 — Registration**
High-risk AI systems must be registered in an EU database before deployment. This creates a public record of what systems are in use and who is responsible for them.

**Obligation 8 — Conformity assessment**
Before deployment, the system must go through a conformity assessment — a formal evaluation that verifies the system meets all applicable requirements. For some categories (biometrics, critical infrastructure), this must be done by an independent third party.

---

## What High-Risk Obligations Look Like in Practice

Imagine a university that wants to use an AI system to help assess student assignments and flag potential plagiarism.

This system falls into high-risk category 3 — education and vocational training. Before deploying it, the university would need to:

- Document the system's design, how it was trained, and what it flags and why
- Test it extensively for bias — does it flag certain writing styles more than others? Does it treat students from different backgrounds differently?
- Put human oversight in place — every flag must be reviewed by a human before any action is taken against a student
- Tell students the system is being used and what it does
- Register the system in the EU database
- Complete a conformity assessment

None of this is optional. And none of it is completed once — the risk management system must continue operating after deployment, monitoring for new problems.

This is why high-risk systems require significant engineering investment before they go live — not as bureaucratic overhead, but as genuine protection for the people they affect.

---

## Quick Recap

- Minimal risk: no specific obligations — good governance is encouraged but not required by regulation
- Limited risk: transparency is the primary obligation — disclose that an AI is being used before or at the start of the interaction
- High risk: eight obligations before deployment — risk management, data governance, technical documentation, transparency, human oversight, accuracy and robustness, registration, conformity assessment
- High-risk obligations are substantial and ongoing — not a one-time checklist but a continuous engineering and governance commitment

---

## What Is Next

The next topic introduces the NIST AI Risk Management Framework — the US government's approach to AI governance, which provides a practical structure for managing AI risk that complements the EU AI Act's regulatory approach.
