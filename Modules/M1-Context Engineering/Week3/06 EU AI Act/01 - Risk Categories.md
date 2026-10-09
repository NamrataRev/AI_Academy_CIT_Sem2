# Risk Categories

---

Not all risks are equal.

A speed bump in a car park slows you down by a few seconds if you ignore it. A red light on a highway can kill someone. Both are traffic rules — but the consequences of ignoring them are completely different. We treat them differently because the stakes are different.

The EU AI Act works on the same principle. Not every AI system is equally risky. A system that recommends films is not in the same risk category as a system that helps decide whether someone gets a loan or a job. Treating them the same would be both inefficient and unfair — over-regulating low-risk systems and under-protecting people from high-risk ones.

The EU AI Act categorises AI systems into four risk levels. Every system you build — now and in your career — falls into one of them.

---

## The Four Risk Categories

**Unacceptable Risk — Prohibited**

These are AI applications that the EU considers fundamentally incompatible with fundamental rights and human dignity. They are banned entirely.

Examples:
- Social scoring systems — governments or companies rating citizens on their social behaviour and restricting their rights based on that score
- Real-time biometric surveillance in public spaces — mass facial recognition by law enforcement (with narrow exceptions)
- AI systems that exploit psychological vulnerabilities to manipulate people against their own interests
- AI used to infer sensitive characteristics (race, political views, religion) from biometric data

No compliance path exists. These systems cannot be made compliant — they are prohibited.

**High Risk — Permitted with Strict Obligations**

These are AI systems that are permitted but face the heaviest regulatory requirements. They operate in domains where errors cause serious harm to individuals.

Eight specific domains are designated high risk:
1. Biometric identification and categorisation
2. Management of critical infrastructure (water, electricity, transport)
3. Education and vocational training — systems that determine access to education or assess students
4. Employment — CV screening, hiring decisions, performance monitoring
5. Access to essential services — credit scoring, insurance, social benefits
6. Law enforcement — crime prediction, evidence assessment
7. Migration and border control
8. Administration of justice

Requirements for high-risk systems include: rigorous testing before deployment, human oversight mechanisms, detailed documentation, registration in an EU database, ongoing monitoring after deployment.

**Limited Risk — Transparency Obligations**

These systems are lower risk but still have specific transparency requirements. The core requirement: users must know they are interacting with an AI.

Examples:
- Chatbots — users must be told they are talking to an AI, not a human
- Deepfakes — AI-generated content must be disclosed as such
- Emotion recognition systems — users must be informed when their emotions are being analysed

The obligation is disclosure, not restriction. These systems can operate freely as long as they are transparent about what they are.

**Minimal Risk — No Specific Obligations**

The vast majority of AI applications fall here. Spam filters. Recommendation engines. AI features in video games. Grammar checkers.

These systems carry negligible risk of harm. The regulation does not impose specific requirements on them, though good governance practices are still encouraged.

---

## Where the Systems You Build Fall

For the course:

A study assistant for BTech students sits in **minimal risk** — it helps students learn, the stakes of a wrong answer are low, and there is no automated decision that affects rights or access to services.

A system that automatically grades assignments and determines which students pass or fail would be **high risk** — it falls under the education and vocational training category (domain 3), where AI is used to assess students.

A system that screens job applications for internships would be **high risk** — it falls under employment (domain 4).

A customer service chatbot that users might mistake for a human would be **limited risk** — transparency obligation applies.

Understanding which category your system falls into is the first governance question to answer. The category determines which obligations apply.

---

## Quick Recap

- The EU AI Act categorises AI systems into four risk levels: unacceptable (prohibited), high risk (strict obligations), limited risk (transparency obligations), minimal risk (no specific obligations)
- Eight domains are designated high risk — including education and assessment, employment, and access to essential services
- The category a system falls into determines which obligations apply — not the technology used, but the domain and impact
- Study assistants are typically minimal risk; automated grading or hiring tools are high risk

---

## What Is Next

The next topic covers what the high-risk obligations actually require — what documentation, testing, and oversight mechanisms must be in place before a high-risk AI system can be deployed.
