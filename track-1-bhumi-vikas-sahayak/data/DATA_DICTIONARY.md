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

Load the file in Python:

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
- **Inserted rules stay inside the rule before them.** The PDF prints 12-A, 17-a, 25(A), 26-A, 42-A, 93(a) and 93(b) with their own numbers, but here each one is part of the previous rule's text. For example, rule 17-a (agricultural tourist facility) sits inside the text of rule 17. Only 26-B has its own line.
- **Not included:** the 28 Aug 2026 amendment to Rule 2(5)(c) and any other change after 6 Mar 2025. See `../PROBLEM-STATEMENT.md`.

## Known errors

- **`part` is wrong for rules 91 to 105.** It says Part VIII or Part IX, but the PDF has only Parts I to V. These rules are in Part V.
- **`page_end` is one page too high on some rules.** Rule 105 points to page 109 of a 108-page PDF.
- **Some amendment notes sit under the wrong rule.** Footnotes print at the bottom of the page, so each one lands in whichever rule is open there.
- **English and Hindi differ.** The two official PDFs give different numbers in 7 places. A court note on page 15 of the PDF says the Hindi version prevails.

## How these files were made

The files were made by splitting `pdftotext -layout` output of the English PDF by rule heading. A heading counts as a rule only when its number is next in sequence, so numbered rows inside tables do not become rules. All 105 rule numbers appear in order.

## Sources

| Document | Link | Downloaded |
|---|---|---|
| MP Bhumi Vikas Rules 2012, English, consolidated to 6 Mar 2025 | https://mptownplan.gov.in/NewsPDF/bvn06032025E.pdf | 9 Oct 2026 |
| MP Bhumi Vikas Rules 2012, Hindi, consolidated to 6 Mar 2025 | https://mptownplan.gov.in/NewsPDF/bvn06032025H.pdf | 10 Oct 2026 |

No file in this folder holds personal data.
