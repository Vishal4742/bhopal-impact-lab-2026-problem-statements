# Data dictionary: Track 1, Bhumi Vikas Sahayak

## Files

| File | Rows | What it is |
|---|---|---|
| `bhumi_vikas_rules.jsonl` | 106 | One JSON object per rule: rules 1 to 105 plus rule 26-B |
| `bhumi_vikas_rules_sample.jsonl` | 5 | Rules 12, 17, 23, 52 and 56, for quick tests |
| `bhumi_vikas_rules_fulltext_by_page.txt` | 108 pages | The full English text. Each page starts with `===== PDF page N =====` |

## Fields in the JSONL files

| Field | Example | Meaning |
|---|---|---|
| `rule` | `"56"`, `"26-B"` | Rule number as printed. A text field, because of `26-B` |
| `title` | `"Residential Buildings"` | Rule heading as printed |
| `part` | `"Part V: General Building Requirements"` | The part of the rules the rule sits in |
| `page_start` | `77` | PDF page where the rule starts |
| `page_end` | `80` | PDF page where the rule ends |
| `text` | `"56. Residential Buildings.-Open Spaces..."` | Full rule text, including sub-rules, tables and footnotes |

Read one line in Python:

```python
import json
rules = [json.loads(line) for line in open("bhumi_vikas_rules.jsonl", encoding="utf-8")]
print(rules[0]["rule"], rules[0]["title"])
```

## Things to know

- **Page numbers** are the PDF's own page count, starting at 1. Open the PDF and jump to that page to check.
- **Page headers sit inside the text.** Lines such as `Rule 56   M.P. Bhumi Vikas Rules, 2012   78` are running headers from the PDF, not rule content.
- **Tables are flattened.** Columns keep their spacing, so a table stays readable, but treat any number from a table with care and check it against the PDF.
- **Footnote markers** such as `1[` and a lone `1` on a line mark amendments. The amendment notes sit at the bottom of the page in the PDF.
- **Sub-rules stay inside their parent.** Rule 17-a (agricultural tourist facility) sits inside the text of rule 17.
- **Rule 26-A** is referred to in the text but has no heading of its own in this PDF.
- **Not included:** the 28 Aug 2026 amendment to Rule 2(5)(c) and any other change after 6 Mar 2025. See `../PROBLEM.md`.

## How these files were made

`tools/split_rules.py` in the repo root splits `pdftotext -layout` output of the English PDF by rule heading. A heading counts as a rule only when its number is next in sequence, so numbered rows inside tables do not become rules. All 105 rule numbers appear in order.

## Sources

| Document | Link | Downloaded |
|---|---|---|
| MP Bhumi Vikas Rules 2012, English, consolidated to 6 Mar 2025 | https://mptownplan.gov.in/NewsPDF/bvn06032025E.pdf | 9 Oct 2026 |
| MP Bhumi Vikas Rules 2012, Hindi, consolidated to 6 Mar 2025 | https://mptownplan.gov.in/NewsPDF/bvn06032025H.pdf | 10 Oct 2026 |

No file in this folder holds personal data.
