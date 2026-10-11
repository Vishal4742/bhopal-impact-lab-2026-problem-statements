# Track 1: Bhumi Vikas Sahayak

<p class="meta">Participant guide · Claude Impact Lab × Cerebras Café Compute, Bhopal · Sunday 11 October 2026 · SSR Global Skills Park</p>

<p class="lede">Ask the Bhopal building rulebook, and get an answer you can trust.</p>

Today you build a working tool for a real Bhopal problem, in one day, with Claude and Claude Code. Everything you build is open source and offered to the Government of Madhya Pradesh through MPSeDC.

This guide puts everything for Track 1 in one place: the problem, the data, the rules and how you are judged.

All files are in the Drive folder and on GitHub (same files): https://github.com/Laaaaksh/bhopal-impact-lab-2026, folder `tracks/01-bhumi-vikas-sahayak`. To clone: `git clone https://github.com/Laaaaksh/bhopal-impact-lab-2026.git`

## Problem statement

**Background.** Every house, shop or extra floor built in Bhopal has to follow the MP Bhumi Vikas Rules, 2012. The rulebook runs to 108 pages and 105 numbered rules. The numbers people ask about most, like fees, setbacks and floor-area limits, sit in tables spread across different parts of it. The state also keeps amending the rules. The latest consolidated copy stops at March 2025, and on 28 August 2026 the rule for plots up to 500 sq m changed again.

**The problem.** The people who need answers don't have time to read 108 pages. A clerk at the Bhopal Municipal Corporation building-permission counter answers the same questions all day. A plot owner pays fees, submits plans and waits, and only then learns the plan breaks a setback rule. A small architect checks the same tables by hand on every job.

**Who you are building for.** A building-permission clerk at the Bhopal Municipal Corporation. A citizen stands at the counter and asks: "My plot is 200 sq m on a 9 m road. How much gap do I leave at the front, how many floors can I build, and what fee do I pay?" The clerk needs a correct answer within a minute, with the rule number to show the citizen.

**Why it is hard.**

- Fee and setback numbers live in tables, and tables are easy to misread.
- The rules changed after March 2025, so the clerk has to know which version of the rules an answer comes from.
- Questions come in English and in Hindi, and the official Hindi PDF uses an old font that copies out as garbage.

**What to build.** A tool where the clerk asks a question in plain English or Hindi and gets a short answer in the same language, with the rule number and the exact text the answer came from. When the rules are silent, the tool says so clearly instead of guessing. The tool points to the rule; the clerk decides.

## The data

Everything is in the `data/` and `resources/` folders of this track.

### Files

| File | Size | What it holds |
|---|---|---|
| `data/bhumi_vikas_rules.jsonl` | 106 lines | All 105 rules plus rule 26-B, one per line, with rule number, title, part, PDF page range and full text |
| `data/bhumi_vikas_rules_sample.jsonl` | 5 lines | Rules 12, 17, 23, 52 and 56, for quick tests |
| `data/bhumi_vikas_rules_fulltext_by_page.txt` | 108 pages | The whole English text. Each page starts with `===== PDF page N =====` |
| `resources/MP_Bhumi_Vikas_Rules_2012_upto_2025-03-06_EN.pdf` | 108 pages | The official English PDF. This is the source of truth |
| `resources/MP_Bhumi_Vikas_Rules_2012_upto_2025-03-06_HI.pdf` | 108 pages | The official Hindi PDF. Its old font copies out as garbage, so read it, don't parse it |
| `resources/sample_questions.md` | 17 questions | Real questions to test against, including two the rules don't answer |

### Things to know

- **Page numbers** are the PDF's own page count, starting at 1. Open the PDF at that page to check.
- **Page headers sit inside the text.** Lines like `Rule 56   M.P. Bhumi Vikas Rules, 2012   78` are running headers from the PDF, not rule content.
- **Tables are flattened.** Columns keep their spacing, so a table stays readable, but check any number from a table against the PDF.
- **Footnote markers** such as `1[` and a lone `1` on a line mark amendments. The amendment notes are at the bottom of the page in the PDF.
- **Some inserted rules sit inside the rule before them.** The PDF prints 12-A, 17-a, 25(A), 26-A, 42-A and 93(a) with their own numbers, but in the rules file each one is part of the previous rule's text. For example, 17-a (agricultural tourist facility) is inside rule 17. Only 26-B has its own line.
- **Not included:** the 28 August 2026 amendment to Rule 2(5)(c), or any other change after 6 March 2025.

### Sources

| Document | Link | Date |
|---|---|---|
| MP Bhumi Vikas Rules 2012, English, consolidated to 6 March 2025 (Town and Country Planning Department) | https://mptownplan.gov.in/NewsPDF/bvn06032025E.pdf | Downloaded 9 Oct 2026 |
| MP Bhumi Vikas Rules 2012, Hindi, consolidated to 6 March 2025 | https://mptownplan.gov.in/NewsPDF/bvn06032025H.pdf | Downloaded 10 Oct 2026 |
| Amendment of 28 August 2026 to Rule 2(5)(c), plots up to 500 sq m | https://teamleaseregtech.com/updates/article/59469/government-of-madhya-pradesh-amendment-to-land-development-rules | Read 10 Oct 2026 |

## Starting points

These are ideas, not instructions. Pick your own approach.

- Fee and setback numbers live in tables, and tables are easy to misread. Check table answers against the PDF.
- Maths (fees, areas, floor counts) belongs in code, not in a language model's head.
- The rules changed after March 2025. Think about how your tool tells the clerk which version of the rules it used.
- Your non-technical teammates matter here: writing test questions from real Bhopal cases, checking answers, writing plain Hindi.

## Constraints

- Public data only. Everything you need is in this folder.
- No connection to any live government system.
- Don't present an answer as legal advice. The clerk decides; your tool points to the rule.

## Rules for the day

1. **No pre-work.** Code you submit must be written from 10:15 AM today. Libraries, frameworks and your own general tools are fine.
2. **Use any tools.** Claude, Claude Code, Cerebras inference APIs, or anything else that fits.
3. **Use the data in this pack.** You may add other public data. Name it and link it in your README.
4. **No live government systems.** Don't log in to, scrape, or write to any government portal during the build.
5. **No personal data.** The data here has none. Keep it that way.
6. **One workflow, one user, one outcome.** Build the tool for the clerk described above. Don't build a portal.
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

For Track 1 the jury looks for:

- Every answer shows its rule number and the text it came from.
- The tool says "not found" when the rules are silent, and never invents a rule.
- Numbers from tables (fees, setbacks) are right.
- The team shows how often the tool is right on the sample questions.

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
2. Read "The data" section.
3. Open `data/bhumi_vikas_rules_sample.jsonl` and look at five rows together as a team.
4. Agree on your user, your one workflow, and what you will demo.
5. Split the work. Start building.

## Questions on the day

Ask a mentor. For anything about the data, check "The data" section of this guide first.

Organisers: Aniket Sahu (Claude Community Ambassador) and Arun Pratap Singh Chandel (Cerebras Community Ambassador).
