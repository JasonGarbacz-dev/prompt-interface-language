# prompt-interface-language

This repo showcases a declarative, reusable interface pattern for controlling LLM behavior — without relying on brittle natural language prompts or verbose JSON contracts.

It’s built for:
- 🔁 Repeatable output structures  
- 🧑‍💼 Audience-aware communication  
- 🧭 Tone, risk, and clarity alignment  
- 🧱 Prompt reuse across workflows  

---

## 💡 Why This Exists

Most prompt design is fragile:

- Natural language is too vague  
- JSON schemas are too rigid (and un-GPT-friendly)  
- System messages don’t scale across changing tasks  

This pattern introduces a **soft specification language** — think: Python-like, function-call format — to express LLM instructions with clarity and structure.

---

## ✨ Core Idea

A prompt begins with a control block:

```python
Analyze_Summarize(
    object = table,
    audience = c_suite_external,
    style = header_plus_text_box,
    bullet_points = 4,
    risk_tolerance = low
)
```

Then follows freeform input (e.g. pasted notes, SQL, or source data).

The control block:

- Defines intent  
- Locks tone and format  
- Prevents ambiguity  
- Supports flexible input while allowing defaults to fill in gaps  

---

## 📄 How the Format Is Interpreted

The control block is interpreted by the LLM using a simple rule set and a configurable set of parameter defaults.

To understand how this works behind the scenes:

- See [`spec/syntax_rules.md`](spec/syntax_rules.md) for how the control block is structured  
- See [`spec/parameter_defaults.md`](spec/parameter_defaults.md) for default behaviors and recognized parameter values  

These two documents together form the **soft spec** that guides both human and machine interaction.

If you're using this inside a Custom GPT or API workflow, the contents of these specs can be combined into system instructions.

---

## 🧩 Examples

- `examples/Analyze_Summarize.txt`  
- `examples/Explain_Transform.txt`  
- `examples/RedTeam_Questioning.txt`

Each includes:
- A control block (top of prompt)  
- A task body  
- A formatting or tone behavior implied by the control structure  

---

## 🧠 Design Principles

- Keyword arguments only — no positional ambiguity  
- Defaults are not prompt-specific — they’re defined in the spec  
- Composable across tools and teams  
- Designed for *operational clarity*, not prompt novelty  

---

## 🚫 Not Trying to Be

- A full DSL or parser  
- A code execution layer  
- A prompt IDE  

This is a **soft contract** — meant to reduce ambiguity and increase reuse across human and machine-facing prompt interfaces.

---

## 📬 About

Built by Jason Garbacz  
Focused on AI-literate tooling, reusable LLM interfaces, and systems that replace ambiguity with clarity.
