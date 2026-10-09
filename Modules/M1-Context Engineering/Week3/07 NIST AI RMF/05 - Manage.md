# Manage

---

A pilot gets a warning light in the cockpit.

They do not ignore it. They do not panic. They follow a procedure — identify what the warning means, assess the severity, take the appropriate action, monitor to confirm the action worked, log what happened.

The warning light is measurement. The procedure is management. Together they keep the aircraft safe not because problems never occur — but because when they do, there is a structured response.

The Manage function in NIST AI RMF is that procedure for AI systems. It takes the risks that Measure has identified and quantified, and responds to them — prioritising, mitigating, monitoring, and learning.

---

## What Manage Covers

Management is not a single action. It is an ongoing cycle with four activities:

**Prioritise** — not all risks are equally urgent. Some failures are frequent but minor. Some are rare but severe. Management starts by deciding which risks to address first.

**Respond** — take action to reduce the risk. For a context package, this usually means modifying a role, strengthening a constraint, adding an exemplar, or updating metadata.

**Monitor** — after responding, watch for whether the response worked. Did the pass rate improve? Did a new failure mode appear? Is the risk level acceptable now?

**Learn** — document what happened, what was done, and what the result was. This learning feeds back into Govern (updating policies), Map (refining the risk understanding), and Measure (improving the metrics).

---

## Prioritising Risks

Not every failure in the eval harness requires immediate action. Priority depends on two factors — likelihood and severity.

For the study assistant:

| Risk | Likelihood | Severity | Priority |
|---|---|---|---|
| Out-of-scope topic explained | Medium | Medium | High — fix before deployment |
| Response exceeds word limit | Medium | Low | Medium — fix in next version |
| Incorrect explanation of a concept | Low | High | High — monitor closely |
| Silent failure on an adversarial input | Low | High | High — add explicit instruction |
| Informal phrasing breaks structure | Low | Low | Low — document as known limitation |

High likelihood + high severity → fix before deployment.
Low likelihood + low severity → document as a known limitation, monitor.
Everything else → assess case by case.

---

## Responding to Risks

Once a risk is prioritised for action, the response depends on which role in the context package is failing.

**If the Constraint is being crossed** — strengthen the constraint. Make it more specific. Add the reason. Add an explicit instruction for what to do instead of the prohibited action.

**If the Rubric is not being followed consistently** — tighten the rubric. Add a completeness check. Specify what happens if the question type makes the standard structure difficult.

**If the Authority is too vague** — make it more specific. Add what the model is not, not just what it is. Specify the level of depth explicitly.

**If the Exemplar is miscalibrating** — replace or supplement the examples. A bad exemplar is worse than no exemplar — remove it and replace with a better one.

**If the Metadata is stale** — update it. Stale metadata is a silent risk — the model makes assumptions based on outdated context.

After every response, document the change in the changelog. Then re-run the full eval harness. Measure again. Confirm the response worked.

---

## Monitoring After Deployment

Management does not stop when the system is deployed. For any system used by real users, monitoring continues.

For the study assistant, monitoring looks like:

- Running the eval harness every time a significant change is made
- Reviewing a sample of real responses every few sessions — not just the harness inputs, but actual student questions
- Checking for degradation signals — responses getting longer, structure drifting, constraints being crossed
- Asking users: is this useful? What went wrong? What was confusing?

Monitoring does not need to be automated or complex. For a minimal-risk system, a weekly spot-check of five real responses against the rubric criteria is meaningful monitoring. The goal is to catch drift before it becomes a serious problem.

---

## Learning and Feeding Back

Every incident — every failure found in the harness, every problem reported by a user, every constraint that was crossed — is an opportunity to learn.

Document it. Understand why it happened. Update the Govern policies if the process failed. Update the Map if the risk understanding was incomplete. Update the Measure criteria if the harness did not catch it. Update the context package if the content was wrong.

This learning loop is what makes a system get better over time, rather than just staying at the level it was deployed at.

```
Measure reveals a problem
    ↓
Manage responds to it
    ↓
Govern updates the policies
    ↓
Map refines the risk understanding
    ↓
Measure improves its metrics
    ↓
System is more reliable than before
```

This is the cycle. It runs throughout the system's life — not just at deployment.

---

## Quick Recap

- Manage takes risks identified by Measure and responds to them — prioritise, respond, monitor, learn
- Prioritise by likelihood × severity — high on both means fix before deployment; low on both means document and monitor
- Response targets the specific role that is failing — tighten the constraint, update the exemplar, refresh the metadata
- Monitoring continues after deployment — spot-check real responses, watch for degradation signals, collect user feedback
- Learning feeds back into Govern, Map, and Measure — the cycle makes the system more reliable over time

---

## What Is Next

The next topic covers the White House Executive Order on AI — the US government's approach to AI safety and governance, and how it compares to the EU AI Act you have already studied.
