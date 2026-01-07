# 🔧 Parameter Defaults & Definitions

These values define default behaviors and recognized options when interpreting control blocks.

---

## `audience`
- **Default**: `general_internal`
- **Recognized**:
  - `c_suite_external` → executive tone, plain English, business-first
  - `technical_peer` → domain-specific language, high density
  - `junior_engineer` → explanation-heavy, teaching tone
  - `non_technical_manager` → skip jargon, highlight impact

---

## `style`
- **Default**: `paragraph_summary`
- **Recognized**:
  - `bullet_list`
  - `numbered_steps`
  - `header_plus_text_box`
  - `code_block_plus_annotation`
  - `table_output`

---

## `risk_tolerance`
- **Default**: `moderate`
- **Values**:
  - `low` → cautious, hedged, evidence-only
  - `moderate` → safe inferences allowed
  - `high` → bold synthesis, willing to extrapolate

---

## `bullet_points`
- **Default**: `5`
- **Range**: 2–10  
- **Fallback**: infer based on content

---

## `object`
- **Default**: infer from input  
- **Examples**:
  - `table`, `python_function`, `sql_query`, `text_block`

---

## `tone`
- **Default**: `neutral_professional`
- **Recognized**:
  - `concise_confident`
  - `friendly_explanatory`
  - `skeptical_analytical`

---

## `debug_mode`
- **Default**: `false`
- **When true**: Add logging, print statements, or reasoning wrappers

---

## 🧱 Customization Notes

- These defaults can be changed per organization, workflow, or GPT project  
- Parameters may be added or removed — your job is to interpret what is defined
