# Data dictionary: Track 2, Visarjan Ghat Watch

## Files

| File | Rows | What it is |
|---|---|---|
| `bhopal_ghats_2023_2025.csv` | 1,524 | Every reading at 7 Bhopal ghats. 2023, 2024, 2025. Ganesh and Durga. **Start here** |
| `sample_bhopal_2025.csv` | 453 | The 2025 rows of the file above |
| `mp_immersion_sites_2023_2025.csv` | 21,600 | Same tests for about 200 sites across MP. Less checked |
| `cpcb_water_quality_criteria.csv` | 19 | Official CPCB limits for water classes A to E |

## Columns in the immersion CSVs

| Column | Example | Meaning |
|---|---|---|
| `year` | `2025` | Report year |
| `festival` | `Ganesh` or `Durga` | Which immersion the test covers |
| `site` | `Bairagarh (Sant Hirdaram) kund` | One standard name per Bhopal ghat (Bhopal file only) |
| `water_body` | `Upper Lake` | Lake or kund the ghat sits on (Bhopal file only) |
| `regional_office` | `R.O. Bhopal` | MPPCB regional office (statewide file only) |
| `phase` | `pre`, `during`, `after` | Before immersion, during immersion, one week after |
| `parameter` | `Dissolved oxygen` | Standard parameter name |
| `value` | `2.5` | Number. Empty when the report shows no number |
| `unit_assumed` | `mg/l` | Unit. **The reports print no units.** These are the standard units for each test |
| `flag` | `BDL`, `not sampled` | Why `value` is empty |
| `value_as_printed` | `BDL` | Exactly what the report shows |
| `parameter_as_printed` | `D.Oxygen` | Parameter name exactly as printed |
| `site_as_printed` | `Sant Hirdaram Visarjankund, Bairagarh, Bhopal` | Site name exactly as printed |
| `site_match_confidence` | `high`, `medium` | How sure the standard name is (Bhopal file only) |
| `needs_check` | `yes` | Site name could not be read (statewide file only) |
| `source_page` | `28` | PDF page in that year's report. Open the PDF and check |

## The 13 parameters

| Parameter | Unit assumed | Plain meaning | Bathing limit (CPCB class B) |
|---|---|---|---|
| pH | none | Acid or alkaline. 7 is neutral | 6.5 to 8.5 |
| Dissolved oxygen | mg/l | Oxygen in the water. Fish need it | 5 or more |
| BOD | mg/l | Biochemical oxygen demand. How much organic waste eats oxygen | 3 or less |
| COD | mg/l | Chemical oxygen demand. Total pollution that uses oxygen | none set |
| Total solids | mg/l | Everything left after the water dries | none set |
| Dissolved solids | mg/l | Solids dissolved in the water | none set |
| Suspended solids | mg/l | Particles floating in the water. Not tested in every year | none set |
| Turbidity | NTU | Cloudiness | none set |
| Conductivity | µS/cm | Dissolved salts. Class E caps it at 2,250 | none set for B |
| Chromium, Lead, Zinc, Copper | mg/l | Heavy metals, often from idol paint | none set for B |

## Codes you will see

| Code | Meaning | How to treat it |
|---|---|---|
| `BDL` | Below detection limit | Very low. Not zero, not missing |
| `ND` | Not detected | Very low |
| `not sampled` | Blank cell, `_` or `-` in the report | Missing. Never treat as clean |
| `*`, `**` | Not sampled at that stage | Missing |

## The 7 Bhopal ghats

| Standard name | Water body | Confidence | Note |
|---|---|---|---|
| Bairagarh (Sant Hirdaram) kund | Upper Lake | high | No Durga 2025 table in the report |
| Khatlapura ghat | Lower Lake | high | |
| Prempura ghat | Upper Lake | high | |
| Rani Kamlapati ghat / Kamla Park kund | Lower Lake | **medium** | Ganesh tables say "Kamla Park kund", Durga tables say "Lower Lake ghat". May be two places |
| Hathaikheda dam / kund | Hathaikheda dam | high | |
| Malikhedi kund | Kund | high | No Durga 2025 table in the report |
| Shahpura lake ghat | Shahpura Lake | high | |

## How these files were made, and how far to trust them

- `tools/parse_visarjan.py` reads `pdftotext -layout` output of each report and turns every table into rows.
- The Bhopal file was **spot-checked**: six tables across all three years were compared number by number with the PDF text, and all matched.
- The statewide file uses the same parser but was **not** checked table by table. 879 rows carry `needs_check` because the site name could not be read. Some tables run across two pages and appear twice with different `source_page` values.
- **Units are assumed.** The reports print none. The units above are the standard ones for these tests.

## Sources

| Document | Link | Downloaded |
|---|---|---|
| MPPCB Ganesh and Durga Visarjan Report 2025 (92 pages) | https://www.mppcb.mp.gov.in/proc/mon/Ganesh_and_Durga_visarjan_report-2025.pdf | 10 Oct 2026 |
| MPPCB Ganesh and Durga Visarjan Report 2024 (118 pages) | https://www.mppcb.mp.gov.in/proc/mon/Ganesh_and_Durga_visarjan_report-2024.pdf | 10 Oct 2026 |
| MPPCB Idol Immersion Report 2023, CPCB format (87 pages) | https://www.mppcb.mp.gov.in/proc/mon/Idol_immer._Report_23_CPCB.pdf | 10 Oct 2026 |
| Upper and Lower Lake monthly water quality 2025-26 | https://xgn.mp.nic.in/File_Upload/MONITORING//Yearly%20Water%20Quality%20Status/2026/July/UPPER%20LAKE-2025-26..pdf | 10 Oct 2026 |
| Upper Lake water quality 2023-24 | https://www.mppcb.mp.gov.in/proc/mon/Bhopal-2023-24_upper_lake.pdf | 10 Oct 2026 |
| Upper and Lower Lake comparison 2003 to 2023 | https://www.mppcb.mp.gov.in/proc/mon/comparatives-uppe-lak-lower-lake-2003-2023.pdf | 10 Oct 2026 |
| CPCB water quality criteria | https://cpcb.gov.in/water-quality-criteria/ | read 10 Oct 2026 |

No file in this folder holds personal data.
