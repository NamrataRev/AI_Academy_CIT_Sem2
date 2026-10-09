# The Governance Note — Worked Example

---

The previous topic covered the structure of a Governance Note. This topic shows one filled in completely — for the BTech DSA study assistant you have been working with throughout Weeks 2 and 3.

Read it once as a complete document. Then read it again section by section, noticing how each part connects to the work done earlier — the risk categories, the NIST functions, the context package documentation.

This is the model for every Governance Note you submit from this point forward.

---

## Complete Governance Note — BTech DSA Study Assistant

---

**GOVERNANCE NOTE**
System: BTech Data Structures and Algorithms Study Assistant
Version: v1.2
Date: Week 3, Semester 2
Builder: [Student Name]
Institution: [University Name]

---

### 1. System Description

This is an AI study assistant for second-year BTech Computer Science students preparing for their Data Structures and Algorithms semester exam. The system receives questions about DSA concepts and produces structured explanations — each containing an analogy, a technical definition, and a real-world use case — designed to be copied directly into revision notebooks.

The system is supplementary to formal teaching. It is not a replacement for lectures, textbooks, or human tutoring. Students retain full agency over how they use its outputs.

---

### 2. Risk Category

**EU AI Act: Minimal Risk**

The system provides explanatory text to students who read and evaluate the outputs themselves. It does not make automated decisions that affect assessment outcomes, access to education, or any rights or entitlements. Students can verify, disagree with, or discard any output.

Reclassification trigger: If this system were modified to automatically evaluate student answers and determine pass or fail, it would be reclassified as High Risk under EU AI Act Annex III, Category 3 (education and vocational training systems that determine access to or assessment in educational institutions).

**NIST AI RMF: Applicable as voluntary framework**
The four functions (Govern, Map, Measure, Manage) have been applied throughout the design and testing of this system. Documentation follows the NIST AI RMF structure.

**India MeitY: Advisory principles applied**
The system is used within an Indian educational institution. MeitY principles of safety, accountability, and inclusivity have been considered in the design. The system is evaluated for accuracy on the specific syllabus and audience rather than on general-purpose benchmarks.

**White House EO: Not directly applicable**
The system is not deployed by a US federal agency and does not involve a general-purpose AI model above the capability thresholds specified in the EO. The EO's principles of transparency and testing have been applied as good practice.

---

### 3. Applicable Obligations

**EU AI Act — Minimal Risk:**
No mandatory obligations under this risk category.
Good governance applied voluntarily as professional practice.

**Transparency — all frameworks:**
Obligation: Users must know they are interacting with an AI.
How met: Every session begins with the following statement, delivered before any content is provided:
*"I am an AI study assistant, not a human tutor. My explanations are based on the course syllabus as defined in my context package. For anything you are uncertain about, verify with your course materials or your lecturer."*

**NIST AI RMF — Govern:**
Obligation: Clear ownership, purpose definition, change policy.
How met: Context package documentation defines purpose, audience, change policy, and deployment threshold. Version history maintained in changelog.

**NIST AI RMF — Map:**
Obligation: Identify affected parties and specific risks.
How met: Risk map documented — see Section 4. Affected parties identified as direct users (students) and indirect parties (lecturers, institution).

**NIST AI RMF — Measure:**
Obligation: Quantify identified risks using defined metrics.
How met: Evaluation harness run with 15 fixed inputs covering typical, boundary, out-of-scope, and adversarial categories. Pass rate documented. Minimum threshold: 85% overall, 100% on typical inputs and out-of-scope redirect criterion.

**NIST AI RMF — Manage:**
Obligation: Respond to identified risks; monitor after deployment.
How met: All eval harness failures addressed before deployment. Changelog documents each change and the reason. Harness re-run after any change to the context package.

---

### 4. Known Risks and Mitigations

**Risk 1 — Inaccurate explanations**
Description: The system produces a factually incorrect explanation of a DSA concept.
Likelihood: Low — the model is generally accurate on well-covered, established topics.
Severity: Medium — a wrong explanation may affect exam performance.
Mitigation: Eval harness includes accuracy checks on all 15 inputs. Students are advised in the opening disclosure to verify with course materials for any concept they are uncertain about.
Residual risk: The eval harness cannot test every possible concept or phrasing. Some inaccuracy on rarely-asked or unusually-phrased questions is possible.

**Risk 2 — Out-of-scope topics explained without flagging**
Description: A student asks about a topic not yet covered in the syllabus (e.g. recursion, graphs) and the system explains it rather than redirecting.
Likelihood: Low with current constraint implementation.
Severity: Medium — explaining pre-requisite concepts before they are introduced may cause confusion.
Mitigation: Explicit constraint in context package. Out-of-scope redirect tested in eval harness — 100% pass rate required before deployment.
Residual risk: Novel phrasing of out-of-scope topics may occasionally bypass the constraint. Students advised to cross-check with the course syllabus.

**Risk 3 — Silent failure — confident wrong answer**
Description: A tool or retrieval process fails silently and the system generates a response from training data without flagging uncertainty.
Likelihood: Low. This system does not use external tools — it generates from the context package and training knowledge. Silent failure applies primarily to tool-using agents, not this system.
Severity: High if it occurs — wrong information presented confidently is harder to detect than an error message.
Mitigation: This risk is acknowledged in the opening disclosure. Students are advised to verify any response they are uncertain about.
Residual risk: Cannot be fully eliminated without output validation tooling, which is beyond this system's scope.

**Risk 4 — Over-reliance**
Description: Students use the assistant as a primary study tool rather than a supplement, producing shallow understanding.
Likelihood: Medium — depends on individual student behaviour.
Severity: Medium — affects depth of understanding, not just accuracy.
Mitigation: Authority role defines the system as supplementary. Opening disclosure reinforces this. Response design prioritises explanation over provision of answers.
Residual risk: Cannot be fully controlled — student behaviour is outside the system's control.

**Known Limitation — Three-topic combination questions**
Three-topic combination questions (e.g. "Compare stacks, queues, and BSTs") consistently produce responses exceeding the 120-word rubric limit. This is an accepted limitation. Students are advised that complex multi-part questions may produce longer responses.

---

### 5. Human Oversight

**Pre-deployment:**
Context package reviewed by builder. Evaluation harness run with all 15 inputs. Pass rate verified at or above threshold. Governance Note reviewed before any student use begins.

**During use:**
No automated monitoring. The system operates without continuous human oversight — appropriate for a minimal-risk system where students retain full agency over their use of outputs. Students are advised to flag any response that seems incorrect to their course lecturer.

**Post-deployment:**
Evaluation harness re-run after any change to the context package. Changelog updated with the change, reason, and new pass rate. Any significant failure reported to course faculty.

**Escalation path:**
If a student reports a response that is factually incorrect and the error is confirmed, the context package is updated, the harness is re-run, and the version number is incremented. The student is informed of the correction.

---

### 6. Responsible Party

Builder: [Student Name]
Institution: [University Name]
Course: Reliable AI Systems: Design, Test, and Deploy — Year 1, Semester 2

Responsibility: Design, testing, documentation, and maintenance of the context package. Responsible for ensuring the evaluation harness is run before deployment and after any significant change. Responsible for updating the changelog and Governance Note to reflect the current state of the system.

Scope of responsibility: This system is a course project used within an educational setting. It is not commercially deployed. Responsibility is limited to the course context and the students who use it within that context.

---

## What This Worked Example Shows

Every section connects to work done elsewhere:

- The risk category connects to the EU AI Act risk categories covered in this week
- The NIST AI RMF obligations connect to the Govern, Map, Measure, and Manage topics
- The risk descriptions connect to the risk map built during the Map function
- The eval harness references connect to the evaluation harness built in the previous section
- The opening disclosure connects to the transparency obligations across all three frameworks

The Governance Note is not a separate document created at the end. It is the synthesis of all the governance work done throughout design and testing — pulled together into one accountable, readable document.

---

## Quick Recap

- A complete Governance Note covers: system description, risk category, applicable obligations, known risks and mitigations, human oversight, and responsible party
- Every section connects to specific governance work done during design and testing
- The Governance Note is not created at the end — it synthesises governance work done throughout the process
- Use this worked example as the model for every Governance Note submitted in this course

---

## What Is Next

Week 3 is complete. The Week 3 Summary consolidates everything covered this week — context quality criteria, evaluation harnesses, adversarial testing, context engineering patterns, and AI governance frameworks — in one place for revision.
