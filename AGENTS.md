# AGENTS.md - Agent Instructions for Document Skill Project

## Project Overview
This is a document generator that builds DOCX files using a skill-based architecture. The main components are:

- **Agent**: `carisma/agent.py` - DocumentAgent that orchestrates skills
- **Skill**: `carisma/skills/docx/skill.py` - DocxSkill for generating DOCX files
- **CLI**: Run via `python -m carisma.agent [spec.json]`

## Architecture

```
DocumentAgent (carisma/agent.py)
    └── DocxSkill (carisma/skills/docx/skill.py)
            └── python-docx library
```

## Key Files
- `carisma/agent.py` - Main agent with `generate_document(spec)` method
- `carisma/skills/docx/skill.py` - DocxSkill with actions: create, add_heading, add_paragraph, add_table, add_list, add_image, set_header, set_footer, add_page_numbers, set_properties, set_margins, save
- `carisma/AGENT.md` - Agent documentation
- `carisma/skills/docx/SKILL.md` - Skill documentation

## JSON Spec Format
```json
{
  "template": "business_report",
  "properties": { "title": "Report", "author": "Author" },
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

## Running the Agent
```bash
# Generate from JSON spec
python -m carisma.agent spec.json

# Generate sample document
python -m carisma.agent
```

## Dependencies
- python-docx (see requirements.txt)

## Development Commands
```bash
# Install dependencies
pip install -r requirements.txt

# Run agent
python -m carisma.agent

# Run with spec
python -m carisma.agent spec.json
```

## Adding New Skills
1. Create `carisma/skills/<name>/skill.py` with a class inheriting the skill pattern
2. Add `carisma/skills/<name>/SKILL.md` documentation
3. Register in `DocumentAgent._register_skills()`

## Testing
No formal test suite exists. Test by running the agent with a spec file and verifying output.docx.