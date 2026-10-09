# NIST AI RMF — Govern

---

Before a hospital opens, it does not just hire doctors and start treating patients.

It establishes policies — who can prescribe what, how errors are reported, what happens when a patient complains, how staff are trained, who is accountable for what. These structures exist before any patient walks through the door. They are the foundation that makes safe, consistent care possible.

The Govern function in the NIST AI RMF works the same way. It is the foundation layer — the policies, roles, and culture that must exist before you build, deploy, or modify an AI system.

---

## What Govern Covers

Govern is about establishing the conditions under which responsible AI development happens. It has five areas:

**Policies and procedures** — documented rules for how AI systems are built, tested, deployed, and maintained. For the systems you are building: the documentation template, the evaluation harness process, the requirement for a Governance Note.

**Roles and accountability** — who is responsible for what. Who built the system? Who approved it for use? Who monitors it after deployment? Who is contacted when something goes wrong?

For a course project, this might be simple — you built it, you are responsible. In a professional team, it is more complex: a developer, a product owner, a risk officer, a legal reviewer might all have defined roles.

**Risk culture** — does the team take risks seriously? Are people encouraged to raise concerns? Is it safe to say "I think this system has a problem" without being dismissed?

**Resources and competencies** — does the team have the knowledge and tools to build and govern the system responsibly? Are people trained on the relevant frameworks?

**Engagement with affected parties** — have the people affected by the system been considered? For the study assistant: have students been told it exists and what it does? Have they been told how to report problems?

---

## What Govern Looks Like for Your Systems

For a study assistant used in a course, a lightweight version of Govern looks like this:

```
GOVERN — Study Assistant

Policy: Context package must be tested against the evaluation 
        harness before being used with students. Pass rate must 
        be 85% or above on typical inputs.

Roles: 
  Builder: [your name] — responsible for design, testing, and 
           documentation
  Reviewer: [teammate or faculty] — reviews documentation and 
            test results before deployment

Risk culture: Known limitations are documented honestly in the 
              context package documentation. Problems found 
              during use are reported and addressed.

Affected parties: Students using the assistant are told:
                  - It is an AI, not a human
                  - It covers only topics in the current syllabus
                  - They should verify anything they are unsure about
                    with their professor
```

This is not bureaucratic overhead. It is the minimum set of structures that makes the system governable — meaning: if something goes wrong, you know who is responsible, what the policy was, and how to fix it.

---

## Why Govern Comes First

Govern is the first function because everything else depends on it.

If you have no policy for testing, you cannot consistently measure quality. If you have no defined accountability, nobody knows who fixes problems when they occur. If you have not engaged with affected parties, you may not know what problems matter most to them.

Map, Measure, and Manage can only work if Govern has established the foundation they operate on.

A team that skips Govern and goes straight to building is like a hospital that hires doctors and starts treating patients before establishing any policies. Things might go fine. Or they might go badly in ways that nobody is equipped to catch or correct.

---

## Quick Recap

- Govern establishes the foundation: policies, roles, risk culture, resources, and engagement with affected parties
- It comes first because Map, Measure, and Manage depend on the structures it creates
- For small systems: lightweight Govern is enough — a testing policy, defined accountability, honest disclosure to users
- A system with no Govern is ungovernable — when something goes wrong, nobody knows who is responsible or what to do

---

## What Is Next

The next topic covers the Map function — identifying and understanding the specific risks of an AI system and the context it operates in.
