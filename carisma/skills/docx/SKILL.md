# Skill

## DOCX Document Generation Skill

Implementation: `carisma/skills/docx/skill.py`

Generates professional DOCX documents using python-docx.

### Dependencies

- `python-docx>=1.1.0`

### Actions

| Action | Parameters | Description |
|--------|-----------|-------------|
| `create` | `template` (optional) | Create blank doc or from template |
| `add_heading` | `text`, `level` | Add heading (level 1-9) |
| `add_paragraph` | `text`, `bold`, `italic`, `font_size`, `font_color`, `alignment` | Add formatted paragraph |
| `add_table` | `headers`, `rows`, `style` | Add table with header row |
| `add_list` | `items`, `ordered` | Add bullet or numbered list |
| `add_image` | `image_path`, `width`, `height` | Insert image |
| `add_page_break` | - | Insert page break |
| `set_header` | `text`, `alignment` | Set document header |
| `set_footer` | `text`, `alignment` | Set document footer |
| `add_page_numbers` | - | Add page numbers to footer |
| `set_properties` | `title`, `author`, `category` | Set document metadata |
| `set_margins` | `top`, `bottom`, `left`, `right` | Set page margins (inches) |
| `save` | `output_path` | Save document to file |

### Example

```python
from carisma.skills.docx import DocxSkill

skill = DocxSkill()
skill.execute("create")
skill.execute("add_heading", text="Report", level=1)
skill.execute("add_paragraph", text="Content", bold=True)
skill.execute("save", output_path="report.docx")
```