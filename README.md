# 💠 Token Budget Advisor

[![ClawHub Skill](https://img.shields.io/badge/ClawHub-Skill-blue)](https://clawhub.ai/djc00p/token-budget-advisor) [![Agent Skill](https://img.shields.io/badge/Agent-Skill-blue)](#) [![Context](https://img.shields.io/badge/Token-Budget-FF6B6B.svg)](https://en.wikipedia.org/wiki/Context_(computing) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Token Budget Advisor** intercepts the response flow so you can **choose the depth before the answer is written** — rather than discovering after the fact that it was too long (or too short).

Four levels, each with a stated cost, each producing a materially different answer. You pick; the response follows.

---

## 🎯 When to Use

* User mentions tokens, budget, depth, or response length
* User says *"short version"*, *"tldr"*, *"brief"*, *"exhaustive"*
* User wants to control detail level upfront

**Do not trigger** when: the user already set depth this session, or the answer is trivially one line.

---

## 📋 Depth Options

Presented before answering:

```text
Input: ~[N] tokens | Type: [type] | Complexity: [level]

[1] Essential (25%)   -> ~[tokens]   Direct answer only
[2] Moderate (50%)    -> ~[tokens]   Answer + context + example
[3] Detailed (75%)    -> ~[tokens]   Multiple examples + alternatives
[4] Exhaustive (100%) -> ~[tokens]   Everything
```

---

## 📏 Level Guide

| Level | Length | Include | Omit |
|-------|--------|---------|------|
| **25%** | 2–4 sentences | Direct answer, conclusion | Context, examples |
| **50%** | 1–3 paragraphs | Answer + context + 1 example | Deep analysis, edge cases |
| **75%** | Structured | Examples, pros/cons, alternatives | Extreme cases |
| **100%** | No limit | Everything | Nothing |

---

## ⚡ Shortcuts

If the user signals depth, respond at that level immediately — no menu:

| Signal | Level |
|--------|-------|
| `"1"` / `"25%"` / `"short"` / `"brief"` / `"tldr"` | 25% |
| `"2"` / `"50%"` / `"moderate"` | 50% |
| `"3"` / `"75%"` / `"detailed"` | 75% |
| `"4"` / `"100%"` / `"exhaustive"` | 100% |

**Maintain the user's chosen level for the rest of the session** unless they change it.

---

## 📐 Estimation

Heuristic-based (no real tokenizer):

* **Input tokens** — estimated from prompt size
* **Response window** — input × complexity multiplier
* **Accuracy** — ~85–90%, variance ±15%

The estimate is an *ordering* signal, not a promise. Use it to pick a level, not to bill anyone.

---

## 💡 Why It Exists

Every answer has a length distribution, and the reader usually knows which one they wanted before the first token arrives. Making the choice explicit turns an implicit mismatch into a one-keypress decision — and the cost estimate makes the tradeoff concrete instead of abstract.

---

## 📚 References

* `references/estimation.md` — token estimation heuristics and complexity multipliers
* `references/level-templates.md` — structural templates for each depth level

---

**Published by [@djc00p](https://github.com/djc00p)**
