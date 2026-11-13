# Why Informal Specs Break

---

Most specs start out the same way: a short project brief — a few sentences or bullet points describing what the system should do.

Here is what that looks like for the course FAQ assistant:

```text
FAQ ASSISTANT — SPEC

- The assistant should help students with course questions.
- It should use the course handbook and be accurate.
- It should be friendly and respond quickly.
- It should not give wrong information.
```

Read it once. It looks fine. Every line sounds sensible. Nobody would argue with any of it.

Now remember the late-penalty question from the last topic. The chatbot answered *"Late submissions lose 10% per day"* — a rule that does not exist in the handbook.

Did the chatbot break this spec?

Try to answer honestly. It *helped* the student with a course question. It sounded *friendly*. It responded *quickly*. It probably *used the handbook* for everything else that day. It did give wrong information — but how would the team have tested for "wrong information" before launch?

This spec could not have caught the problem. Not because it was written badly, but because it was written **informally**. This topic explains exactly where informal specs break — so you can recognise the same weaknesses in any spec you write.

---

## What Makes a Spec Informal

An informal spec is written in everyday language and describes **intentions** — what you hope the system will be like.

A formal spec describes **behaviour** — what the system will do in specific situations, in a way someone can check.

| Informal (intention) | Formal (behaviour) |
|---|---|
| "It should be accurate" | "Every date and penalty in an answer must appear in the handbook" |
| "It should respond quickly" | "Answers appear within 5 seconds for 95% of questions" |
| "It should be friendly" | "Answers use plain language and never blame the student" |

Informal specs are not useless. They capture what the team cares about — and that matters. The problem is that intentions cannot be **tested**. You cannot ask a chatbot a question and check the answer against "be accurate."

---

## Five Ways Informal Specs Break

### 1 — Vague words

**The line:** "It should be friendly and respond quickly."

**What goes wrong:** "Friendly" and "quickly" mean different things to different people. One reviewer thinks 10 seconds is quick. Another thinks anything over 3 seconds is slow. Both are reading the same spec.

**Watch for words like:** good, fast, accurate, user-friendly, appropriate, reasonable, robust, simple. If a word needs an opinion to check, it is vague.

### 2 — Missing boundaries

**The line:** "The assistant should help students with course questions."

**What goes wrong:** It says what the system does. It never says what it does **not** do, or what happens when it **cannot** answer. This is exactly the gap the late-penalty question fell into. The handbook had no answer, the spec had no instruction, so the model invented one.

As you saw in the last topic: in an AI system, a missing boundary does not mean "nothing happens." It means the model decides.

### 3 — Hidden conflicts

**The lines:** "Help students with course questions" and "Use the course handbook."

**What goes wrong:** These sound like they agree. They do not. What if a student asks a course question the handbook does not cover? "Help" says answer it. "Use the handbook" says you cannot.

The spec does not say which one wins. This is the conflict that caused the prompt whack-a-mole loop in the last topic — "only from the handbook" versus "be helpful", fixed and re-broken again and again.

### 4 — Wishes instead of requirements

**The line:** "It should not give wrong information."

**What goes wrong:** Everyone wants this. But it does not tell anyone what to build or what to test. Wrong compared to what? Checked how? It is a wish, not a requirement.

A requirement version would be: *"Any date, deadline or penalty in an answer must appear in the handbook. If it does not, the answer fails."* Now there is something to check.

### 5 — Mixing "what" and "how well"

**The line:** "It should use the course handbook and be accurate."

**What goes wrong:** One sentence mixes two different kinds of requirement — what the system does (uses the handbook) and how well it does it (accuracy). When they are tangled together, it is hard to test either one cleanly.

Separating these two kinds of requirement is the subject of the next two topics.

---

## The Two-Reader Test

Here is a simple way to expose an informal spec: give it to two people, show them the same answer, and ask "does this pass?"

The answer being judged: *"Late submissions lose 10% per day."*

| Spec line | Reader A says | Reader B says |
|---|---|---|
| "Help students with course questions" | Pass — it answered the question | Pass — it answered the question |
| "Use the handbook and be accurate" | Pass — sounds like handbook language | Fail — I cannot find this in the handbook |
| "Be friendly and respond quickly" | Pass | Pass |
| "Do not give wrong information" | Cannot tell — I do not know the real policy | Fail — I checked the email, it is 5% |

Two careful people, the same spec, the same answer — and they reach different verdicts. Reader A would launch the chatbot. Reader B would not.

When a spec gives different verdicts to different readers, **the spec is the problem**, not the readers. Recall the test from the first topic: a real spec is one where two people agree on whether the system passes.

---

## A Quick Diagnostic: SMART

There is a well-known checklist for testing whether a requirement is clear enough. It is called **SMART**:

| Letter | Means | The question to ask |
|---|---|---|
| **S** | Specific | Does it say exactly what, in which situation? |
| **M** | Measurable | Can you check it with a yes/no or a number? |
| **A** | Achievable | Can the system realistically do this? |
| **R** | Relevant | Does it matter to the people using the system? |
| **T** | Time-bound | Does it say how fast, or when it applies? |

Run the informal FAQ spec through it:

| Spec line | S | M | A | R | T |
|---|---|---|---|---|---|
| "Help students with course questions" | ✗ | ✗ | ✓ | ✓ | ✗ |
| "Use the handbook and be accurate" | ✗ | ✗ | ✓ | ✓ | ✗ |
| "Be friendly and respond quickly" | ✗ | ✗ | ✓ | ✓ | ✗ |
| "Do not give wrong information" | ✗ | ✗ | ✗ | ✓ | ✗ |

Every line passes **Relevant** — the team clearly knew what mattered. Almost every line fails **Specific** and **Measurable** — which is exactly why none of them could have caught the late-penalty answer.

Notice the last line fails **Achievable** too. "Never give wrong information" is not something any AI system can promise in general. A narrower version — "never state a penalty that is not in the handbook" — is something you can actually test and enforce.

This is just a first look. In **Writing Testable Requirements** you will use SMART properly, rewriting weak requirements one letter at a time.

---

## What Informal Specs Get Right

Informal specs are not a waste of time. They do something important: they capture **what the team cares about**. Every line in the informal FAQ spec points at a real concern — accuracy, helpfulness, speed, tone.

An informal spec is a good **first draft**. The mistake is treating it as the final version and building from it.

The job now is to take those intentions and turn each one into something testable:

```text
INTENTION (informal)
"It should not give wrong information."

        ↓  make it specific and checkable

REQUIREMENT (formal)
"Any date, deadline or penalty in an answer must appear in the
handbook. If the handbook does not cover the question, the
assistant says so and directs the student to the course coordinator."
```

The concern did not change. Only the precision did. And the second version would have caught the late-penalty answer before launch.

---

## Quick Recap

- Informal specs describe intentions; formal specs describe behaviour that can be checked
- Informal specs break in five common ways: vague words, missing boundaries, hidden conflicts, wishes instead of requirements, and mixing "what" with "how well"
- The two-reader test exposes an informal spec — if two people reach different verdicts on the same answer, the spec needs work
- SMART is a quick diagnostic: most informal requirements pass Relevant but fail Specific and Measurable
- An informal spec is a useful first draft — it shows what the team cares about. The next step is turning that into requirements you can test

> **Interview tip:** If asked "what makes a good requirement?", show it rather than define it. Take a vague requirement like "the system should be accurate" and explain why it cannot be tested, then rewrite it into something specific and measurable. Mention SMART as the checklist you use. Interviewers remember candidates who can turn a vague line into a testable one in front of them.

---

## What Is Next

The next topic starts formalising the spec. It covers **functional requirements** — the "what the system does" part — and shows how to write them for the FAQ assistant so that each one describes a clear, checkable behaviour.
