# JSON Schema — Part 1: Daily Sales Report

## Usage
Paste this into AI Agent → Output Parser → Structured Output Parser → Define Using JSON Schema.

---

## Schema

```json
{
  "type": "object",
  "properties": {
    "reportDate": {
      "type": "string",
      "description": "Date of the report"
    },
    "summary": {
      "type": "object",
      "properties": {
        "totalDeals": { "type": "number" },
        "totalAtRisk": { "type": "number" },
        "stageBreakdown": {
          "type": "array",
          "items": {
            "type": "object",
            "properties": {
              "stage": { "type": "string" },
              "count": { "type": "number" },
              "amount": { "type": "number" }
            }
          }
        }
      }
    },
    "atRiskDeals": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "dealId": { "type": "number" },
          "dealname": { "type": "string" },
          "amount": { "type": "number" },
          "stage": { "type": "string" },
          "daysOverdue": { "type": "number" },
          "problem": { "type": "string" },
          "recommendation": { "type": "string" },
          "priority": {
            "type": "string",
            "enum": ["urgent", "high", "medium", "low"]
          }
        }
      }
    },
    "topPriorityActions": {
      "type": "array",
      "items": { "type": "string" }
    }
  }
}
```

---

## Notes
- Select **Define Using JSON Schema** — not "Generate from JSON Example"
- `priority` is an enum — model can only return urgent/high/medium/low
- `topPriorityActions` is a flat array of strings, not objects
