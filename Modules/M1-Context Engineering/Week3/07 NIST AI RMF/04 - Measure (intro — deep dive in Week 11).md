# Measure

---

A doctor does not just identify that a patient has high blood pressure. They measure it — 140 over 90, taken three times over two weeks, compared against a reference range. The measurement tells them how serious the problem is, whether it is getting better or worse, and whether the treatment is working.

Without measurement, you have a concern. With measurement, you have evidence.

The Measure function in NIST AI RMF turns identified risks into quantified assessments — so you know not just that a risk exists, but how significant it is, how often it occurs, and whether your mitigations are actually working.

---

## What Measure Covers

The Measure function asks: how do we know if the risks we identified in Map are actually happening, and at what level?

It has three parts:

**Define metrics** — what will you measure, and how will you measure it?

**Collect data** — run the system against defined inputs, observe the outputs, record what happens.

**Interpret results** — what do the numbers mean? Are the risks within acceptable levels? Is the system improving or degrading over time?

---

## The Evaluation Harness as a Measure Tool

You have already built the primary measurement tool for context packages — the evaluation harness.

The harness is a direct implementation of the Measure function:

| Measure component | How the harness implements it |
|---|---|
| Define metrics | The criteria checklist — analogy present, under 120 words, no constraint violations |
| Collect data | Running the fixed input set and recording every response |
| Interpret results | The pass rate — 12/15 (80%), patterns in failures, which criteria fail most |

When you run the eval harness and get a pass rate of 80%, you are doing measurement. When you identify that length failures cluster on comparison questions, you are interpreting results. When you fix the constraint and re-run to see if the pass rate improved, you are using measurement to verify that management worked.

---

## Connecting Measure to the Risk Map

The Measure function should connect directly to the risks identified in Map. For each risk, there should be a metric that tells you whether that risk is occurring and at what level.

For the study assistant:

| Risk (from Map) | Metric | How measured | Acceptable level |
|---|---|---|---|
| Inaccurate explanations | Accuracy criterion in eval harness | Manual check — is the content correct? | 100% on typical inputs |
| Out-of-scope topics explained | Constraint violation rate | Out-of-scope inputs in eval harness | 0% — any violation is unacceptable |
| Silent failure | Confidence without grounding | Adversarial inputs — does the model answer when it should redirect? | 0% on flagged categories |
| Over-reliance | Cannot be measured by the harness | User observation, not automated | Monitor qualitatively |

Notice the last row. Some risks cannot be measured by the eval harness. Over-reliance depends on how students choose to use the system — something the harness cannot observe. Measure does not mean everything must be quantified. It means being honest about what you can measure and what you can only monitor qualitatively.

---

## This is an Introduction — Week 11 Goes Deeper

This topic gives you the foundation of the Measure function — what it is, why it matters, and how it connects to the work you have already done.

Week 11 goes significantly deeper. It covers:

- Evaluation dataset design for AI systems — how to build test sets that are representative, balanced, and resistant to gaming
- Measuring AI reliability — consistency across runs, accuracy vs calibration, failure clustering
- Regression testing — detecting when a change to the system degraded its performance
- Evaluation-driven development — writing the evaluation dataset before building the feature, not after
- Benchmark literacy — understanding what published AI benchmarks actually measure and what they miss

All of this is Measure in practice. The foundation you are building now — understanding what measurement is for and how the harness implements it — is what Week 11 builds on.

---

## Quick Recap

- Measure turns identified risks into quantified assessments — how often do they occur, how serious are they, are mitigations working?
- The evaluation harness is a direct implementation of Measure: define metrics (criteria), collect data (run inputs), interpret results (pass rate and patterns)
- Connect each risk from Map to a metric — so you know whether each risk is actually occurring and at what level
- Some risks cannot be quantified — be honest about what requires qualitative monitoring instead
- Week 11 covers evaluation in depth — this topic is the foundation

---

## What Is Next

The next topic covers the Manage function — how to respond to the risks that measurement reveals, and what managing risk looks like in practice for the systems you build.
