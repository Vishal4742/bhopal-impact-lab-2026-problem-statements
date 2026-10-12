# Track 1: Bhumi Vikas Sahayak

<p class="meta">Problem statement · Claude Impact Lab Bhopal · Sunday 11 October 2026 · SSR Global Skills Park</p>

<p class="lede">Ask the Bhopal building rulebook and get an answer the clerk can trust.</p>

Claude Impact Lab Bhopal was a one-day build event. Teams had from 10:15 AM to 5:00 PM to build a working tool for a real Bhopal problem with Claude and Claude Code. The projects are open source, and the work is offered to the Government of Madhya Pradesh through MPSeDC.

This document covers Track 1: the problem, the data given to teams, the rules of the day and how projects were judged.

## Problem statement

**Background.** Every house, shop or extra floor built in Bhopal has to follow the MP Bhumi Vikas Rules, 2012. The rulebook runs to 108 pages and 105 numbered rules. The numbers people ask about most, like fees, setbacks and floor-area limits, sit in tables spread across different parts of it. The state also keeps amending the rules. The latest consolidated copy stops at March 2025, and on 28 August 2026 the rule for plots up to 500 sq m changed again.

**The problem.** The people who need answers don't have time to read 108 pages. A clerk at the Bhopal Municipal Corporation building-permission counter answers the same questions all day. A plot owner pays fees, submits plans and waits, and only then learns the plan breaks a setback rule. A small architect checks the same tables by hand on every job.

**Who it is for.** A building-permission clerk at the Bhopal Municipal Corporation. A citizen stands at the counter and asks: "My plot is 200 sq m on a 9 m road. How much gap do I leave at the front, how many floors can I build, and what fee do I pay?" The clerk needs a correct answer within a minute, with the rule number to show the citizen.

**Why it is hard.**

- Fee and setback numbers live in tables, and tables are easy to misread.
- The rules changed after March 2025, so the clerk has to know which version of the rules an answer comes from.
- Questions come in English and in Hindi, and the official Hindi PDF uses an old font that copies out as garbage.

**What teams were asked to build.** A tool where the clerk asks a question in plain English or Hindi and gets a short answer in the same language, with the rule number and the exact text the answer came from. When the rules are silent, the tool says so clearly instead of guessing. The tool points to the rule; the clerk decides.

## The data

Everything is in the `data/` and `resources/` folders of this track.

### Files

| File | Size | What it holds |
|---|---|---|
| `data/bhumi_vikas_rules.jsonl` | 106 lines | All 105 rules plus rule 26-B, one per line, with rule number, title, part, PDF page range and full text |
| `data/bhumi_vikas_rules_sample.jsonl` | 5 lines | Rules 12, 17, 23, 52 and 56, for quick tests |
| `data/bhumi_vikas_rules_fulltext_by_page.txt` | 108 pages | The whole English text. Each page starts with `===== PDF page N =====` |
| `resources/MP_Bhumi_Vikas_Rules_2012_upto_2025-03-06_EN.pdf` | 108 pages | The official English PDF. This is the source of truth |
| `resources/MP_Bhumi_Vikas_Rules_2012_upto_2025-03-06_HI.pdf` | 108 pages | The official Hindi PDF. Its old font copies out as garbage, so it has to be read, not parsed |
| `resources/sample_questions.md` | 17 questions | Test questions, including two the rules don't answer |

### Things to know

- **Page numbers** are the PDF's own page count, starting at 1. Open the PDF at that page to check.
- **Page headers sit inside the text.** Lines like `Rule 56   M.P. Bhumi Vikas Rules, 2012   78` are running headers from the PDF, not rule content.
- **Tables are flattened.** Columns keep their spacing, so a table stays readable, but any number from a table should be checked against the PDF.
- **Footnote markers** such as `1[` and a lone `1` on a line mark amendments. The amendment notes are at the bottom of the page in the PDF.
- **Some inserted rules sit inside the rule before them.** The PDF prints 12-A, 17-a, 25(A), 26-A, 42-A, 93(a) and 93(b) with their own numbers, but in the rules file each one is part of the previous rule's text. For example, 17-a (agricultural tourist facility) is inside rule 17. Only 26-B has its own line.
- **Known errors in the rules file.** The `part` field is wrong for rules 91 to 105: it says Part VIII or Part IX, but the PDF has only Parts I to V and these rules are in Part V. `page_end` is one page too high on some rules; rule 105 points to page 109 of a 108-page PDF. Because footnotes print at the bottom of the page, some amendment notes land in the wrong rule's text.
- **English and Hindi differ.** The two official PDFs give different numbers in 7 places. A court note on page 15 of the PDF says the Hindi version prevails.
- **Not included:** the 28 August 2026 amendment to Rule 2(5)(c), or any other change after 6 March 2025.

### Sources

| Document | Link | Date |
|---|---|---|
| MP Bhumi Vikas Rules 2012, English, consolidated to 6 March 2025 (Town and Country Planning Department) | https://mptownplan.gov.in/NewsPDF/bvn06032025E.pdf | Downloaded 9 Oct 2026 |
| MP Bhumi Vikas Rules 2012, Hindi, consolidated to 6 March 2025 | https://mptownplan.gov.in/NewsPDF/bvn06032025H.pdf | Downloaded 10 Oct 2026 |
| Amendment of 28 August 2026 to Rule 2(5)(c), plots up to 500 sq m | https://teamleaseregtech.com/updates/article/59469/government-of-madhya-pradesh-amendment-to-land-development-rules | Read 10 Oct 2026 |

## Hints given to teams

These were ideas, not instructions. Teams chose their own approach.

- Fee and setback numbers live in tables, and tables are easy to misread. Check table answers against the PDF.
- Maths (fees, areas, floor counts) belongs in code, not in a language model's head.
- The rules changed after March 2025. A good tool tells the clerk which version of the rules it used.
- Non-technical team members had real work here: writing test questions from real Bhopal cases, checking answers and writing plain Hindi.

## Constraints

- Public data only. Everything teams needed was in this folder.
- No connection to any live government system.
- No answer presented as legal advice. The clerk decides; the tool points to the rule.

## Rules of the day

1. **No pre-work.** Submitted code had to be written from 10:15 AM on the day. Libraries, frameworks and a team's own general tools were allowed.
2. **Any tools.** Teams could use Claude, Claude Code, Cerebras inference APIs or anything else that fit.
3. **The data in this pack.** Teams could add other public data, named and linked in their README.
4. **No live government systems.** No logging in to, scraping or writing to any government portal during the build.
5. **No personal data.** The data here has none.
6. **One workflow, one user, one outcome.** The tool was for the clerk described above, not a portal.
7. **Teams of 4 to 5,** mixed technical and non-technical, with real work for everyone.
8. **Public repo by 5:00 PM.** The code is offered to the department, so it has to be readable.

## How projects were judged

The jury brief called for the organisers plus a representative of the problem's real users: a department officer where possible, or a domain expert. Scoring leaned toward day-one impact, meaning what the user gets the week after the event.

Submissions were due at 5:00 PM. The jury and mentors then reviewed the submissions and picked the teams to present. Each presenting team had 6 minutes to present and demo, then 4 minutes of questions.

Each judge filled one card per presenting team. Every criterion was scored 0 to 5, and day-one impact counted double, so the maximum was 25.

| Criterion | What is scored | Scoring guide |
|---|---|---|
| Day-one impact (×2) | Is it ready to use, with real impact, on day one? | 5 ready, high impact · 4 almost ready, high impact · 3 ready, mild impact · 2 almost ready, mild impact · 1 not ready or not impactful |
| Product | User experience, ease of use, onboarding | 5 polished, works first try · 4 well designed, fits the workflow · 3 usable with little learning · 2 functional, needs learning · 1 hard to use |
| Idea | How creative and impactful the idea is, whatever the result | 5 rare insight · 4 creative and original · 3 solid but predictable · 2 close to what exists · 1 already exists |
| Clarity of demo | Are the problem, the user and the outcome obvious? | 5 impeccable pitch and demo · 4 good pitch, convincing demo · 3 ok pitch, demo worked · 2 weak narrative · 1 no narrative or demo failed |

For Track 1 the jury looked for:

- Every answer shows its rule number and the text it came from.
- The tool says "not found" when the rules are silent, and never invents a rule.
- Numbers from tables (fees, setbacks) are right.
- The team shows how often the tool is right on the sample questions.

If two teams tied, the higher day-one impact score won.

## What teams submitted

1. **A public GitHub repo link.** Required.
2. **A screen recording of 2 minutes or less.** Optional. A demo that failed live still counted if the recording worked.

Each repo had to contain:

| Item | Why |
|---|---|
| `README.md` with team name, members, track, and the one user the tool is for | The jury read this first |
| How to run it, in 5 steps or fewer | The department must be able to run the work after the event |
| What works and what doesn't | Honesty scored better than a hidden gap |
| Any extra data used, with links | Rule 3 |
| A `LICENSE` file | The code is offered to the department. MIT unless the organisers said otherwise |
| No API keys or secrets in the code | Keys belong in environment variables |

After the event, the organisers connect winning teams with the relevant department officers so the work can move toward real use.

The projects submitted for this track are listed at https://github.com/Vishal4742/bhopal-impact-lab-2026-problem-statements#track-1-bhumi-vikas-sahayak
