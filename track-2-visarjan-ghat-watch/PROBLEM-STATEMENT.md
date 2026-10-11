# Track 2: Visarjan Ghat Watch

<p class="meta">Participant guide · Claude Impact Lab × Cerebras Café Compute, Bhopal · Sunday 11 October 2026 · SSR Global Skills Park</p>

<p class="lede">Turn three years of buried water tests into a warning Bhopal can act on before Durga visarjan.</p>

Today you build a working tool for a real Bhopal problem, in one day, with Claude and Claude Code. Everything you build is open source and offered to the Government of Madhya Pradesh through MPSeDC.

This guide puts everything for Track 2 in one place: the problem, the data, the rules and how you are judged.

All files are in the Drive folder and on GitHub (same files): https://github.com/Laaaaksh/bhopal-impact-lab-2026, folder `tracks/02-visarjan-ghat-watch`. To clone: `git clone https://github.com/Laaaaksh/bhopal-impact-lab-2026.git`

## Problem statement

**Background.** Every Ganesh and Durga festival, the MP Pollution Control Board (MPPCB) tests the water at Bhopal's idol-immersion ghats three times: before immersion, during, and one week after. The results go into reports of 90 to 120 pages. Nobody lines them up against the legal limits or compares one year with the next.

**What the reports show.** The numbers buried in those reports are alarming. At Bairagarh (Sant Hirdaram) kund, dissolved oxygen read 0 mg/l four times across 2023 and 2025. Water at zero oxygen supports no fish life at all, and the bathing-water standard asks for at least 5. Across all Bhopal ghat readings from 2023 to 2025, 42 of 116 dissolved-oxygen readings are below 5 mg/l, and 100 of 112 BOD readings are above the bathing limit of 3 mg/l.

**Why now.** The National Green Tribunal has banned immersion in the Upper and Lower Lakes, and Bhopal Municipal Corporation is building new ghats. Durga visarjan falls on 20 October 2026, nine days after this event.

**Who you are building for.** The Bhopal Municipal Corporation officer who plans Durga visarjan at the ghats. This officer decides where to send extra cleaning, aeration and water testing. Today that decision rests on memory, because the test results sit in PDFs nobody reads.

**Why it is hard.**

- The reports print no units. The units in the data are the standard ones for each test.
- A blank means "not sampled", not "clean", and some ghats were sampled only during immersion.
- BDL means below the detection limit: very low, but not zero and not missing.
- Only 4 metals were tested (chromium, lead, zinc, copper).
- One site name, "Rani Kamlapati ghat / Kamla Park kund", may cover two places.

**What to build.** A tool that gives the officer, before 20 October, a ranked list of Bhopal ghats by risk with the reason for each rank in plain words, the numbers behind every rank traceable to the report and page, and a short brief in Hindi and English the officer can forward. Report the readings against the CPCB limits, say honestly where the data is missing, and don't claim health effects the data doesn't show.

## The data

Everything is in the `data/` and `resources/` folders of this track.

### Files

| File | Rows | What it holds |
|---|---|---|
| `data/bhopal_ghats_2023_2025.csv` | 1,524 | Start here. Every reading at 7 Bhopal ghats, 2023 to 2025, Ganesh and Durga, before / during / after. Spot-checked against the PDFs |
| `data/sample_bhopal_2025.csv` | 453 | The 2025 rows of the file above, for quick testing |
| `data/mp_immersion_sites_2023_2025.csv` | 21,600 | The same tests at about 100 sites per festival across MP. Less checked. Rows marked `needs_check` have no readable site name |
| `data/cpcb_water_quality_criteria.csv` | 19 | The official CPCB water-quality limits, classes A to E |
| `resources/` | 6 PDFs | The original MPPCB reports (2023, 2024, 2025) and Upper / Lower Lake water-quality reports |

### Columns in the immersion CSVs

| Column | Example | Meaning |
|---|---|---|
| `year` | `2025` | Report year |
| `festival` | `Ganesh` or `Durga` | Which immersion the test covers |
| `site` | `Bairagarh (Sant Hirdaram) kund` | One standard name per Bhopal ghat (Bhopal file only) |
| `water_body` | `Upper Lake` | Lake or kund the ghat sits on (Bhopal file only) |
| `regional_office` | `R.O. Bhopal` | MPPCB regional office (statewide file only) |
| `phase` | `pre`, `during`, `after` | Before immersion, during immersion, one week after |
| `parameter` | `Dissolved oxygen` | Standard parameter name |
| `value` | `2.5` | The number. Empty when the report shows no number |
| `unit_assumed` | `mg/l` | Unit. The reports print no units; these are the standard units for each test |
| `flag` | `BDL`, `not sampled` | Why `value` is empty |
| `value_as_printed` | `BDL` | Exactly what the report shows |
| `parameter_as_printed` | `D.Oxygen` | Parameter name exactly as printed |
| `site_as_printed` | `Sant Hirdaram Visarjankund, Bairagarh, Bhopal` | Site name exactly as printed |
| `site_match_confidence` | `high`, `medium` | How sure the standard name is (Bhopal file only) |
| `needs_check` | `yes` | Site name could not be read (statewide file only) |
| `source_page` | `28` | PDF page in that year's report. Open the PDF and check |

### The 13 parameters

| Parameter | Unit assumed | Plain meaning | Bathing limit (CPCB class B) |
|---|---|---|---|
| pH | none | Acid or alkaline. 7 is neutral | 6.5 to 8.5 |
| Dissolved oxygen | mg/l | Oxygen in the water. Fish need it | 5 or more |
| BOD | mg/l | Biochemical oxygen demand: how much organic waste eats oxygen | 3 or less |
| COD | mg/l | Chemical oxygen demand: total pollution that uses oxygen | none set |
| Total solids | mg/l | Everything left after the water dries | none set |
| Dissolved solids | mg/l | Solids dissolved in the water | none set |
| Suspended solids | mg/l | Particles floating in the water. Not in the Durga 2023 and Durga 2025 tables | none set |
| Turbidity | NTU | Cloudiness | none set |
| Conductivity | µS/cm | Dissolved salts. Class E caps it at 2,250 | none set for B |
| Chromium, Lead, Zinc, Copper | mg/l | Heavy metals, often from idol paint | none set for B |

### Codes you will see

| Code | Meaning | How to treat it |
|---|---|---|
| `BDL` | Below detection limit | Very low. Not zero, not missing |
| `ND` | Not detected | Very low |
| `not sampled` | Blank cell, `_` or `-` in the report | Missing. Never treat it as clean |
| `*`, `**` | Not sampled at that stage | Missing |

### The 7 Bhopal ghats

| Standard name | Water body | Confidence | Note |
|---|---|---|---|
| Bairagarh (Sant Hirdaram) kund | Upper Lake | high | No Durga 2025 table in the report |
| Khatlapura ghat | Lower Lake | high | |
| Prempura ghat | Upper Lake | high | |
| Rani Kamlapati ghat / Kamla Park kund | Lower Lake | medium | Ganesh tables say "Kamla Park kund", Durga tables say "Lower Lake ghat". May be two places |
| Hathaikheda dam / kund | Hathaikheda dam | high | |
| Malikhedi kund | Kund | high | No Durga 2025 table in the report |
| Shahpura lake ghat | Shahpura Lake | high | |

### CPCB water-quality criteria

From `data/cpcb_water_quality_criteria.csv`:

| Class | Designated best use | Limits |
|---|---|---|
| A | Drinking water source without conventional treatment but after disinfection | Total coliform 50 MPN/100 ml or less · pH 6.5 to 8.5 · Dissolved oxygen 6 mg/l or more · BOD (5 days, 20°C) 2 mg/l or less |
| B | Outdoor bathing (organised) | Total coliform 500 MPN/100 ml or less · pH 6.5 to 8.5 · Dissolved oxygen 5 mg/l or more · BOD (5 days, 20°C) 3 mg/l or less |
| C | Drinking water source after conventional treatment and disinfection | Total coliform 5,000 MPN/100 ml or less · pH 6 to 9 · Dissolved oxygen 4 mg/l or more · BOD (5 days, 20°C) 3 mg/l or less |
| D | Propagation of wildlife and fisheries | pH 6.5 to 8.5 · Dissolved oxygen 4 mg/l or more · Free ammonia (as N) 1.2 mg/l or less |
| E | Irrigation, industrial cooling, controlled waste disposal | pH 6.0 to 8.5 · Electrical conductivity at 25°C 2,250 micromhos/cm or less · Sodium absorption ratio 26 or less · Boron 2 mg/l or less |

### Sources

| Document | Link | Date |
|---|---|---|
| MPPCB Ganesh and Durga Visarjan Report 2025 (92 pages) | https://www.mppcb.mp.gov.in/proc/mon/Ganesh_and_Durga_visarjan_report-2025.pdf | Downloaded 10 Oct 2026 |
| MPPCB Ganesh and Durga Visarjan Report 2024 (118 pages) | https://www.mppcb.mp.gov.in/proc/mon/Ganesh_and_Durga_visarjan_report-2024.pdf | Downloaded 10 Oct 2026 |
| MPPCB Idol Immersion Report 2023, CPCB format (87 pages) | https://www.mppcb.mp.gov.in/proc/mon/Idol_immer._Report_23_CPCB.pdf | Downloaded 10 Oct 2026 |
| Upper and Lower Lake monthly water quality 2025-26 | https://xgn.mp.nic.in/File_Upload/MONITORING//Yearly%20Water%20Quality%20Status/2026/July/UPPER%20LAKE-2025-26..pdf | Downloaded 10 Oct 2026 |
| Upper Lake water quality 2023-24 | https://www.mppcb.mp.gov.in/proc/mon/Bhopal-2023-24_upper_lake.pdf | Downloaded 10 Oct 2026 |
| Upper Lake water quality by station, 2003-04 to 2022-23 | https://www.mppcb.mp.gov.in/proc/mon/comparatives-uppe-lak-lower-lake-2003-2023.pdf | Downloaded 10 Oct 2026 |
| CPCB water quality criteria | https://cpcb.gov.in/water-quality-criteria/ | Read 10 Oct 2026 |
| NGT immersion ban and new BMC ghats, Free Press Journal, 26 Feb 2026 | https://www.freepressjournal.in/amp/bhopal/mp-news-idol-immersion-to-shift-from-lakes-to-safer-sites-ngt-ban-pushes-bmc-to-build-4-dedicated-ghats | |
| Durga visarjan date, 20 October 2026, Drik Panchang | https://www.drikpanchang.com/navratri/durga-puja/durga-visarjan-date-time.html?year=2026 | |

## Starting points

These are ideas, not instructions. Pick your own approach.

- Decide which CPCB class fits immersion ghats, and say why. Class B (outdoor bathing) is a reasonable start.
- Your non-technical teammates matter here: researching the NGT order and CPCB guidelines, placing the ghats on a map, writing the Hindi brief, checking numbers against the PDFs.

## Constraints

- Public data only. Everything you need is in this folder.
- No connection to any live government system.
- Don't claim health effects the data doesn't show. Report the readings against the limits.

## Rules for the day

1. **No pre-work.** Code you submit must be written from 10:15 AM today. Libraries, frameworks and your own general tools are fine.
2. **Use any tools.** Claude, Claude Code, Cerebras inference APIs, or anything else that fits.
3. **Use the data in this pack.** You may add other public data. Name it and link it in your README.
4. **No live government systems.** Don't log in to, scrape, or write to any government portal during the build.
5. **No personal data.** The data here has none. Keep it that way.
6. **One workflow, one user, one outcome.** Build the tool for the officer described above. Don't build a portal.
7. **Teams of 4 to 5,** mixed technical and non-technical. Everyone on the team should have real work.
8. **Your repo must be public on GitHub by 5:00 PM.** The code is offered to the department, so it has to be readable.

## How you are judged

The jury includes the organisers and a representative of the problem's real users: a department officer where possible, or a domain expert. Scoring leans toward day-one impact, meaning what the user gets the week after the event.

Submissions close at 5:00 PM. The jury and mentors then review every submission and pick who presents. Not every team presents. Teams chosen to present get 6 minutes to present and demo, then 4 minutes of questions.

Each judge fills one card per presenting team. Every criterion is scored 0 to 5, and day-one impact counts double, so the maximum is 25.

| Criterion | What is scored | Scoring guide |
|---|---|---|
| Day-one impact (×2) | Is it ready to use, with real impact, on day one? | 5 ready, high impact · 4 almost ready, high impact · 3 ready, mild impact · 2 almost ready, mild impact · 1 not ready or not impactful |
| Product | User experience, ease of use, onboarding | 5 polished, works first try · 4 well designed, fits the workflow · 3 usable with little learning · 2 functional, needs learning · 1 hard to use |
| Idea | How creative and impactful the idea is, whatever the result | 5 rare insight · 4 creative and original · 3 solid but predictable · 2 close to what exists · 1 already exists |
| Clarity of demo | Are the problem, the user and the outcome obvious? | 5 impeccable pitch and demo · 4 good pitch, convincing demo · 3 ok pitch, demo worked · 2 weak narrative · 1 no narrative or demo failed |

For Track 2 the jury looks for:

- The ranking of ghats is traceable to the readings and the CPCB limits.
- Missing data shows as missing, never as clean.
- The brief is short and readable by a BMC officer in Hindi and English.
- The team is honest about what the data doesn't cover.

If two teams tie, the higher day-one impact score wins.

## What to submit

Hard deadline: 5:00 PM, Sunday 11 October 2026. Late submissions are not judged.

1. **A public GitHub repo link.** Required.
2. **A screen recording of 2 minutes or less.** Optional, but strongly advised. Record it at 4:00 PM, when the room reminder goes out. A demo that fails live still counts if the recording works.

Submit both through the submission form: https://docs.google.com/forms/d/e/1FAIpQLSfKNgfbYvYMI6xHgS0ir4kBhZWspGp37hIzbt9PhB-ZfK70vQ/viewform

Your repo must contain:

| Item | Why |
|---|---|
| `README.md` with team name, members, track, and the one user you built for | The jury reads this first |
| How to run it, in 5 steps or fewer | The department must be able to run your work after the event |
| What works and what doesn't | Honesty scores better than a hidden gap |
| Any extra data you used, with links | Rule 3 |
| A `LICENSE` file | The code is offered to the department. Use MIT unless the organisers say otherwise |
| No API keys or secrets in the code | Use environment variables. Check before you push |

After the event, the organisers connect winning teams with the relevant department officers so the work moves toward real use. Keep your repo public.

## Get started in 10 minutes

1. Read the problem statement above.
2. Read "The data" section. It explains BDL, blanks and the units.
3. Open `data/sample_bhopal_2025.csv` and look at five rows together as a team.
4. Agree on your user, your one workflow, and what you will demo.
5. Split the work. Start building.

## Questions on the day

Ask a mentor. For anything about the data, check "The data" section of this guide first.

Organisers: Aniket Sahu (Claude Community Ambassador) and Arun Pratap Singh Chandel (Cerebras Community Ambassador).
