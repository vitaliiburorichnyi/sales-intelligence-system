# JSON Schema — Part 2: Deal Health Score

## Usage
Paste this into AI Agent → Output Parser → Structured Output Parser → Define Using JSON Schema.

---

## Schema

```json
{
  "type": "object",
  "properties": {
    "dealId": {
      "type": "number"
    },
    "dealname": {
      "type": "string"
    },
    "score": {
      "type": "number",
      "description": "Health score 1-10"
    },
    "category_label": {
      "type": "string",
      "enum": ["Critical", "Medium", "Normal"]
    },
    "summary": {
      "type": "string",
      "description": "2-3 sentence overall assessment"
    },
    "risk_factors": {
      "type": "array",
      "items": { "type": "string" }
    },
    "recommendation_actions": {
      "type": "array",
      "items": { "type": "string" }
    }
  },
  "required": [
    "dealId",
    "dealname",
    "score",
    "category_label",
    "summary",
    "risk_factors",
    "recommendation_actions"
  ]
}
```

---

## Switch Node Routing (based on score output)

| Condition | Operator | Value | Output |
| --- | --- | --- | --- |
| score | Less Than or Equal To | 4 | Critical |
| score | Less Than or Equal To | 7 | Medium |
| score | Less Than or Equal To | 10 | Normal |

**Order is critical — do not reorder.**

---

## Notes
- `category_label` enum matches Switch node routing labels exactly
- `score` is a number, not a string — ensure JSON Schema type is `number`
- `required` array enforces all fields — model cannot skip any
