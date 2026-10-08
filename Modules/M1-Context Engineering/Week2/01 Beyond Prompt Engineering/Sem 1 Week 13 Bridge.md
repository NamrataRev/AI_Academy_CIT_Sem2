# Sem 1 Week 13 Bridge

---

In Semester 1, you learned to talk to AI models. By the end of Week 13, you could write system prompts, assign roles, add examples, set constraints, and control output format.

That was real skill. You were getting noticeably better results than someone who just typed a bare question and hoped for the best.

But here is something you probably did not realise at the time — everything you did in Semester 1 Week 13 was context engineering. You just did not have a framework for it. You were doing it by instinct, adding things when you remembered to, leaving them out when you forgot.

This week gives that instinct a structure.

---

## What You Did in Semester 1 — And What It Actually Was

Look at everything you learned in Week 13 and what each technique was really doing:

**System prompt vs user prompt**

You learned that the system prompt sets up the environment and the user prompt is the live request. You were already separating two different kinds of information — background setup versus the immediate task.

This is the foundation of context engineering. The system prompt is where most of your context lives.

**Role assignment — telling the model who it is**

*"You are a teaching assistant for a BTech Computer Science course."*

You were giving the model an identity. Telling it what kind of entity it should be as it responds. This shapes tone, vocabulary, depth, and perspective.

In the five-role framework you are about to learn, this is called the **Authority role**. You were already doing it. Now you will do it deliberately.

**Few-shot examples — showing the model what good output looks like**

You gave the model examples of the kind of response you wanted before asking your question. Instead of describing what you needed, you showed it.

This is called the **Exemplar role**. Examples are more powerful than descriptions — a model that has seen three good responses is better calibrated than one that has only been told what good means.

**Constraints — telling AI what NOT to do**

*"Do not use jargon the student has not encountered yet. Do not exceed 150 words. Do not reference topics not covered in this module."*

You were drawing a boundary around what the model should and should not do. Limiting the space of possible responses to the ones actually useful for your situation.

This is the **Constraint role**. Without constraints, the model produces the most statistically average response. With constraints, it produces one that fits your specific need.

**Output format control — getting JSON, numbered lists, or fixed structure**

*"Respond in the following format: concept name, one-line definition, one example."*

You were telling the model not just what to produce but how to structure it — so the output could be used directly, without reformatting.

This is the **Rubric role**. It tells the model how to evaluate its own output — what the response should look like when it is done well.

**System prompt background information**

The information you put in the system prompt that was not about role or constraints — the background context the model needed to understand the situation. Which course. Which level of students. What has already been covered.

This is the **Metadata role**. It gives the model the situational awareness it needs to make good decisions.

---

## The Full Mapping

| What you did in Semester 1 | The role it plays | What it does |
|---|---|---|
| Role assignment | **Authority** | Tells the model who it is — shapes tone, depth, perspective |
| Few-shot examples | **Exemplar** | Shows the model what good looks like — more powerful than describing it |
| Constraints | **Constraint** | Tells the model what not to do — narrows the response space |
| Output format control | **Rubric** | Tells the model how to structure its response — so output is immediately usable |
| Background information | **Metadata** | Gives the model situational awareness — course, level, what has been covered |

---

## What Was Missing

You were applying these techniques when you remembered to. Some prompts had role assignment but no examples. Some had constraints but no format control. Some had all of them but written inconsistently — slightly different phrasing each time, different order, different level of detail.

The result was inconsistent output. Sometimes excellent. Sometimes generic. Hard to predict which you would get.

This is the gap the five-role framework fills.

When you have a named framework with a defined role for each type of information — you stop forgetting things. You stop being inconsistent. You build context packages that work reliably because they are complete, not because you happened to remember all the right pieces on that particular day.

---

## What Changes This Week

In Semester 1 you were writing prompts. Good ones, sometimes great ones — but prompts.

This week you start building context packages. The difference is intentionality and completeness. A context package is not a prompt with some extras added. It is a structured document that deliberately fills all five roles — every time, for every system you build.

By the end of this week you will look back at your Semester 1 system prompts and immediately see what was missing. Not because they were bad — but because you will have a framework to evaluate them against.

---

## Quick Recap

- Everything you did in Semester 1 Week 13 was context engineering — you just did not have a framework for it
- Role assignment = Authority, Few-shot examples = Exemplar, Constraints = Constraint, Output format = Rubric, Background info = Metadata
- The five roles were already present in your work — inconsistently applied and sometimes missing
- This week gives those techniques a structure so they are applied deliberately and completely every time

---

## What Is Next

The next topic introduces the five context roles formally — what each one is, what it does, and why all five together produce something more reliable than any combination of fewer than five.
