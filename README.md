# prompt-interface-language
> A declarative control interface for LLMs — bridging human-readable prompts and structured automation.


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

## 🧩 Architecture and Integration

This repository doesn’t just define a prompt format — it defines a **specification layer** that can be added to any GPT or LLM-driven system to introduce consistent interpretive semantics.  
The `Prompt Interface Language` acts as a **soft contract** that describes *how* prompts should be read and *how* responses should be shaped, without dictating task-specific content or model weights.

### 🧱 Layered Model

| Layer | Purpose | Example |
|--------|----------|----------|
| **Spec Layer** | Defines syntax, recognized parameters, and default behaviors. Lives in `spec/` and can be versioned independently. | `risk_tolerance = low`, `audience = c_suite_external` |
| **Interpreter Layer** | Reads the spec and applies its semantics. This repo’s reference Custom GPT (the *Prompt Interface Language Interpreter*) serves as a test harness for validating the rules. | Ensures tone, format, and reasoning follow spec defaults. |
| **Application Layer** | Any GPT, agent, or automation that embeds the spec in its own instructions to inherit the same semantics. | A “Report Generator” GPT or internal agent using the spec for repeatable structure. |

### 🧭 Why This Matters

Separating the **specification** from the **interpreter** makes this approach modular and maintainable:
- Multiple GPTs can share one spec for consistent behavior.
- The spec can evolve (e.g., new tone definitions) without rewriting every prompt.
- The interpreter can be swapped or extended to suit different workflows or hosting environments.

### ⚙️ Integration Patterns

- **As a Custom GPT layer:** paste the contents of the spec into the “instructions” field of any GPT to instantly apply structured control-block semantics.  
- **As a library component:** import the syntax and parameter defaults into programmatic workflows to standardize LLM behavior across pipelines.  
- **As a governance tool:** treat the spec as a versioned contract defining communication tone, clarity, and risk tolerance for enterprise or multi-agent systems.


## 🚫 Not Trying to Be

- A full DSL or parser  
- A code execution layer  
- A prompt IDE  

This is a **soft contract** — meant to reduce ambiguity and increase reuse across human and machine-facing prompt interfaces.

---

## 🧾 Status
Current spec: v0.1 (draft)  
Reference interpreter: active  
Next step: publish default parameter set for reuse across GPTs


## 🧪 Verified Output Example

See [`examples/generated/analyze_summarize_exec_brief_debug.txt`](examples/generated/analyze_summarize_exec_brief_debug.txt) for a tested control block prompt and structured GPT output using the Prompt Interpreter spec (v0.1).

Includes:
- Executive audience targeting
- Inferred parameters
- Debug output block with reasoning trace



---

## 📬 About

Built by Jason Garbacz  
Focused on AI-literate tooling, reusable LLM interfaces, and systems that replace ambiguity with clarity.
