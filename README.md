# Bhopal Impact Lab 2026: problem statements and data

Claude Impact Lab × Cerebras Café Compute, Bhopal · Sunday 11 October 2026 · SSR Global Skills Park

Today you build a working tool for a real Bhopal problem, in one day, with Claude and Claude Code. Everything you build is open source and offered to the Government of Madhya Pradesh through MPSeDC.

This repo has both problem statements, the data for each track, the original source documents and all the links.

## The two tracks

| | Track 1: Bhumi Vikas Sahayak | Track 2: Visarjan Ghat Watch |
|---|---|---|
| In one line | Ask the Bhopal building rulebook and get an answer with the rule number | Turn three years of ghat water tests into a risk warning before Durga visarjan |
| User | Building-permission clerk, Bhopal Municipal Corporation | BMC officer planning Durga visarjan at the ghats |
| Data | 105 rules from the MP Bhumi Vikas Rules 2012, split and page-referenced | 1,524 water-test readings at 7 Bhopal ghats, 2023 to 2025 |
| Problem statement | [Read it](track-1-bhumi-vikas-sahayak/PROBLEM-STATEMENT.md) · [PDF](track-1-bhumi-vikas-sahayak/Track%201%20-%20Bhumi%20Vikas%20Sahayak%20-%20Participant%20guide.pdf) | [Read it](track-2-visarjan-ghat-watch/PROBLEM-STATEMENT.md) · [PDF](track-2-visarjan-ghat-watch/Track%202%20-%20Visarjan%20Ghat%20Watch%20-%20Participant%20guide.pdf) |

Pick one track with your team at the opening.

## Key times

- Build starts at 10:15 AM. Code you submit must be written after that.
- Submissions close at 5:00 PM.

**Submit here:** https://docs.google.com/forms/d/e/1FAIpQLSfKNgfbYvYMI6xHgS0ir4kBhZWspGp37hIzbt9PhB-ZfK70vQ/viewform

Submit your public GitHub repo link and, if you have one, your 2-minute screen recording.

## What's in this repo

```
track-1-bhumi-vikas-sahayak/
  PROBLEM-STATEMENT.md       the problem statement and guide
  Track 1 ... guide.pdf      the same, as a PDF
  data/                      rules as JSONL (full and sample), full text by page, data dictionary
  resources/                 official English and Hindi PDFs of the rules, sample questions
track-2-visarjan-ghat-watch/
  PROBLEM-STATEMENT.md       the problem statement and guide
  Track 2 ... guide.pdf      the same, as a PDF
  data/                      Bhopal ghat readings, 2025 sample, statewide readings, CPCB limits, data dictionary
  resources/                 MPPCB visarjan reports 2023 to 2025 and lake water-quality reports
```

## Data files

**Track 1**

| File | Size | What it holds |
|---|---|---|
| `data/bhumi_vikas_rules.jsonl` | 106 lines | All 105 rules plus rule 26-B, with rule number, title, part, PDF page range and full text |
| `data/bhumi_vikas_rules_sample.jsonl` | 5 lines | Rules 12, 17, 23, 52 and 56, for quick tests |
| `data/bhumi_vikas_rules_fulltext_by_page.txt` | 108 pages | The whole English text, marked page by page |
| `data/DATA_DICTIONARY.md` | | What every field means |
| `resources/MP_Bhumi_Vikas_Rules_2012_upto_2025-03-06_EN.pdf` | 108 pages | Official English PDF (source of truth) |
| `resources/MP_Bhumi_Vikas_Rules_2012_upto_2025-03-06_HI.pdf` | 108 pages | Official Hindi PDF |
| `resources/sample_questions.md` | 17 questions | Questions to test your tool with |

**Track 2**

| File | Rows | What it holds |
|---|---|---|
| `data/bhopal_ghats_2023_2025.csv` | 1,524 | Every reading at 7 Bhopal ghats, 2023 to 2025. Start here |
| `data/sample_bhopal_2025.csv` | 453 | The 2025 rows, for quick testing |
| `data/mp_immersion_sites_2023_2025.csv` | 21,600 | The same tests across MP. Use as background |
| `data/cpcb_water_quality_criteria.csv` | 19 | Official CPCB limits, classes A to E |
| `data/DATA_DICTIONARY.md` | | Columns, codes, units and the 7 ghats |
| `resources/` | 6 PDFs | MPPCB reports 2023, 2024, 2025 and Upper / Lower Lake water-quality reports |

## Sources

**Track 1**

- MP Bhumi Vikas Rules 2012, English, consolidated to 6 March 2025: https://mptownplan.gov.in/NewsPDF/bvn06032025E.pdf
- MP Bhumi Vikas Rules 2012, Hindi, consolidated to 6 March 2025: https://mptownplan.gov.in/NewsPDF/bvn06032025H.pdf
- Amendment of 28 August 2026 to Rule 2(5)(c), plots up to 500 sq m: https://teamleaseregtech.com/updates/article/59469/government-of-madhya-pradesh-amendment-to-land-development-rules

**Track 2**

- MPPCB Ganesh and Durga Visarjan Report 2025: https://www.mppcb.mp.gov.in/proc/mon/Ganesh_and_Durga_visarjan_report-2025.pdf
- MPPCB Ganesh and Durga Visarjan Report 2024: https://www.mppcb.mp.gov.in/proc/mon/Ganesh_and_Durga_visarjan_report-2024.pdf
- MPPCB Idol Immersion Report 2023 (CPCB format): https://www.mppcb.mp.gov.in/proc/mon/Idol_immer._Report_23_CPCB.pdf
- Upper and Lower Lake monthly water quality 2025-26: https://xgn.mp.nic.in/File_Upload/MONITORING//Yearly%20Water%20Quality%20Status/2026/July/UPPER%20LAKE-2025-26..pdf
- Upper Lake water quality 2023-24: https://www.mppcb.mp.gov.in/proc/mon/Bhopal-2023-24_upper_lake.pdf
- Upper Lake water quality by station, 2003-04 to 2022-23: https://www.mppcb.mp.gov.in/proc/mon/comparatives-uppe-lak-lower-lake-2003-2023.pdf
- CPCB water quality criteria: https://cpcb.gov.in/water-quality-criteria/
- NGT immersion ban and new BMC ghats, Free Press Journal, 26 Feb 2026: https://www.freepressjournal.in/amp/bhopal/mp-news-idol-immersion-to-shift-from-lakes-to-safer-sites-ngt-ban-pushes-bmc-to-build-4-dedicated-ghats
- Durga visarjan date, Drik Panchang: https://www.drikpanchang.com/navratri/durga-puja/durga-visarjan-date-time.html?year=2026

## Credits

The data files and source PDFs come from the participant pack at https://github.com/Laaaaksh/bhopal-impact-lab-2026, prepared by Laksh Sadhwani.

Organisers: Aniket Sahu (Claude Community Ambassador) and Arun Pratap Singh Chandel (Cerebras Community Ambassador).
