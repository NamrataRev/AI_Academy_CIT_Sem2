# Agents — LLM + Memory + Tools + Planning Loop

---

## The Decision You Keep Putting Off

You need to buy a laptop. You have a budget. You want something good for programming.

You check one review. It recommends something. You check another — it recommends something different and says the first option has a heating issue. You go to a shopping site to check prices. The prices are different from what the reviews mentioned. You check if there is a newer model. There is. Now you are reading about that one. It looks good but you are not sure if it fits your budget after taxes and delivery.

An hour later you have eleven tabs open, no decision made, and you are more confused than when you started.

Now imagine something that could do all of that for you — go through the reviews, compare options, check current prices, figure out what matters for your use case, and come back with a clear recommendation. No eleven tabs. No confusion. Just an answer.

That is an AI agent.

---

## What an Agent Actually Is

A regular AI model does one thing: you ask, it answers. One round. Done. You decide what to ask next, you decide if the answer is good enough, you decide what to do with it.

An agent is different in one fundamental way — **it decides for itself what to do next.**

You give it a goal. Not a question — a goal. And it figures out the steps. It decides what to look up first. It looks it up. It reads what came back. It decides what is still missing. It looks that up too. It keeps going until it has enough to give you a real answer.

The key word is **decides**. No script. No fixed steps. It figures out the path as it goes.

---

## The Four Parts — How It Actually Works

Every agent in the world — no matter what it is built with — has exactly four parts. Once you know these four parts, you can look at any agent and immediately understand what it is doing.

**The language model** is the part that thinks. It reads the current situation — the goal, what has been found so far, what tools are available — and decides what to do next. It only produces text. It cannot search anything, check anything, or act on anything by itself. It just decides what should happen next and writes it down as an instruction.

**Tools** are the only way the agent can actually do something. A tool is a function — search the web, read a file, run code, call an API. When the language model decides to search for laptop prices, it produces an instruction: "call the search tool with this query." Something reads that instruction and runs the actual search. The model never touches the tool directly — it only says what should be called.

**Memory** is how the agent holds on to what it found. When the first search returns five laptop options, the agent needs to remember those while it does the second search to compare specs. Without memory, every step starts from zero with no idea what just happened. In most agents, this is simply the conversation history — everything found so far stays in the current session.

**The planning loop** is what ties everything together. After each tool call the agent reads the result, decides if it has enough to answer, and if not — goes around again. This loop is what makes an agent different from a single call. A single call runs once. The loop runs as many times as the task needs.

---

## Watching It Work — The Laptop Example

Here is what the agent actually does with the laptop goal:

**Round 1** — The agent thinks: *I need current options within budget. Prices change constantly — I cannot rely on what I know from training.* It searches: `"best programming laptop under 55000 rupees 2025"`. Gets back five options with rough price ranges. Saves them. Goes around again.

**Round 2** — The agent thinks: *I have options but I need to know which ones are actually good for programming. RAM and processor matter most.* It searches: `"Lenovo IdeaPad Slim 5 vs ASUS Vivobook programming performance"`. Finds that the Lenovo has 16GB RAM, the ASUS has 8GB at a similar price. Clear difference. Saves it. Goes around again.

**Round 3** — The agent thinks: *I have a strong candidate. But I need to verify the actual current price and check it is in stock.* It searches: `"Lenovo IdeaPad Slim 5 Ryzen 5 16GB price India 2025"`. Finds it at ₹52,499, in stock. Within budget. Saves it. Goes around again.

**Round 4** — The agent thinks: *I have current options, a comparison on what matters for programming, and a verified price. I can answer now.*

```
"For ₹55,000 and programming work, the Lenovo IdeaPad Slim 5 
(Ryzen 5, 16GB RAM) is your best option right now.

Current price: ₹52,499 — in stock.

Why this over the others: 16GB RAM means you can run your editor, 
a browser, and a local server simultaneously without slowdown. 
The other options in this range mostly have 8GB, which becomes a 
bottleneck fast once your projects grow."
```

Four loops. Three searches. One specific, verified, reasoned answer.

---

## What a Regular AI Would Have Said

*"I would recommend looking at the Lenovo IdeaPad or HP Pavilion range for your budget."*

Vague. Based on training data that could be a year old. No current prices. No stock check. No reasoning about what specifically matters for programming. It guessed. The agent went and found out.

This is the difference. Not that the agent is smarter — it is using the same language model. The difference is that it can go and get real information and make decisions based on what it finds.

---

## The One Thing to Remember

An agent is not a smarter chatbot. It is a system that can take action, observe results, and decide what to do next — looping until the job is done.

---

## What Is Next

You have seen what an agent does. The next file covers **how** it decides — the specific pattern it uses to think before every action. That pattern is called ReAct, and understanding it is what lets you build agents that actually work reliably.
