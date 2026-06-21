# Agent

## Document Generator Agent

Implementation: `carisma/agent.py`

This agent generates professional documents in DOCX format using skills.

### Skills Used

- **docx** (`carisma/skills/docx/skill.py`): Generates DOCX files with customizable content and formatting

### Usage

```bash
# Generate from JSON spec
python -m carisma.agent spec.json

# Generate sample document
python -m carisma.agent
```

### JSON Spec Format

```json
{
  "template": "business_report",
  "properties": { "title": "Report", "author": "Carisma" },
  "margins": { "top": 1.0, "bottom": 1.0, "left": 1.0, "right": 1.0 },
  "content": [
    { "type": "heading", "text": "Title", "level": 1 },
    { "type": "paragraph", "text": "Body text", "bold": true },
    { "type": "list", "items": ["item1", "item2"] },
    { "type": "table", "headers": ["Col1", "Col2"], "rows": [["a", "b"]] }
  ],
  "output": "output.docx"
}
```