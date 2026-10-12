# Bhopal Impact Lab 2026: problem statements and data

Claude Impact Lab Bhopal · Sunday 11 October 2026 · SSR Global Skills Park

Today you build a working tool for a real Bhopal problem, in one day, with Claude and Claude Code. Everything you build is open source and offered to the Government of Madhya Pradesh through MPSeDC.

This repo has both problem statements, the data for each track, the original source documents and all the links.

## The two tracks

| | Track 1: Bhumi Vikas Sahayak | Track 2: Visarjan Ghat Watch |
|---|---|---|
| In one line | Ask the Bhopal building rulebook and get an answer with the rule number | Turn three years of ghat water tests into a risk warning before Durga visarjan |
| User | Building-permission clerk, Bhopal Municipal Corporation | BMC officer planning Durga visarjan at the ghats |
| Data | 105 rules from the MP Bhumi Vikas Rules 2012, split and page-referenced | 1,524 water-test readings at 7 Bhopal ghats, 2023 to 2025 |
| Problem statement | [Read it](track-1-bhumi-vikas-sahayak/PROBLEM-STATEMENT.md) · [PDF](track-1-bhumi-vikas-sahayak/Track%201%20-%20Bhumi%20Vikas%20Sahayak%20-%20Participant%20guide.pdf) | [Read it](track-2-visarjan-ghat-watch/PROBLEM-STATEMENT.md) · [PDF](track-2-visarjan-ghat-watch/Track%202%20-%20Visarjan%20Ghat%20Watch%20-%20Participant%20guide.pdf) |

Pick one track with your team at the opening

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

## Submissions

67 teams submitted: 27 on Track 1 and 40 on Track 2. Each team's problem statement is in [SUBMISSIONS.md](SUBMISSIONS.md).

### Track 1: Bhumi Vikas Sahayak

| # | Project | Team | Links |
|---|---|---|---|
| 1 | [Bhumi Vikas Sahayak](SUBMISSIONS.md#track1-1) | Manikant Goutam (solo) | [Code](https://github.com/dev-redakai/bhumi-vikas-sahayak) |
| 2 | [MIRA - Municipal Intelligence for Rules & Architecture](SUBMISSIONS.md#track1-2) | ApeX.MD | [Code](https://github.com/ut3av/ImpactLab) · [Live](https://impact-lab-chi.vercel.app/) |
| 3 | [Bhumi Vikas Sahayak](SUBMISSIONS.md#track1-3) | Mavericks | [Code](https://github.com/PriyanshuRaj2077/Bhumi-Vikas-Sahayak) · [Live](https://bhumi-vikas-sahayak.onrender.com/) · [Demo](https://drive.google.com/open?id=1M0HoTPrTwojYxEovOpmtKlB-FWulu0L8) |
| 4 | [BhuVikas AI – Intelligent Building Regulation & Compliance Assistant for Madhya Pradesh](SUBMISSIONS.md#track1-4) | Gyan Sarthi | [Code](https://github.com/Aarohi1011/bhuvikas) · [Live](https://bhuvikas.vercel.app/) · [Demo](https://drive.google.com/open?id=1ei1IBuX1xCvaw8GayFuBrRsh0XE4GbIl) |
| 5 | [Kshiti (क्षिति) · Bhumi Vikas Sahayak](SUBMISSIONS.md#track1-5) | THETA1728 | [Code](https://github.com/Priyanshu12116/KSHITI) · [Live](https://kshiti-two.vercel.app) |
| 6 | [Bhumi Rule checker](SUBMISSIONS.md#track1-6) | Atalix | [Code](https://github.com/inxeoz/2026-10-11-bhopal-impact-sol-11th-oct.git) · [Live](https://bhumi.inxeoz.com) · [Demo](https://drive.google.com/open?id=119NMPpV0c9_TVGtW9VbxI00HWE3l4qRb) |
| 7 | [Land development supporter](SUBMISSIONS.md#track1-7) | Innovators | [Code](https://github.com/arzynx/Claude-Impact-lab-11-oct.git) · [Live](https://arzynx.github.io/Claude-Impact-lab-11-oct/) · [Demo](https://drive.google.com/open?id=1JdLAnEN7esaIFNzL--QY6t1qRbpXAKi_) |
| 8 | [Bhumi vikas sahayak](SUBMISSIONS.md#track1-8) | ERROR 404 | [Code](https://github.com/RavendraPatel09/claude-impact-lab-oct11) · [Live](https://bhumi-vikas-sahayak-frontend.onrender.com/) · [Demo](https://drive.google.com/open?id=1NZDkcP_f6ZjuQCV5LP6wBsvZIvMmVzhE) |
| 9 | [Bhumi Vikas Sahayak](SUBMISSIONS.md#track1-9) | Beyond Limits | [Code](https://github.com/TheRaj200/-Bhumi-Vikas-Sahayak-Frotnend.git) · [Code 2](https://github.com/TheRaj200/Bhumi-Vikas-Sahayak-backend.git) · [Live](https://bhumi-vikas-sahayak-frotnend.vercel.app/) · [Demo](https://drive.google.com/open?id=1wI2G_6sEqqhJKPKeu6LtYj5ksWM0lUzB) |
| 10 | [Context aware Land rule-book](SUBMISSIONS.md#track1-10) | 3 idiots | [Code](https://github.com/black-swas/bhumi-vikas-sahayak) · [Live](https://bhumi-vikas-sahayak-two.vercel.app/) · [Demo](https://drive.google.com/open?id=1g3ZkMC6go1NyQo2Z2V-8E09NJVkpfqkG) |
| 11 | [Bhopal Bhumi](SUBMISSIONS.md#track1-11) | Alone | [Code](https://github.com/kakarot07-git/bhopal-bhumi-vikas-sahayak) · [Live](https://bhopal-bhumi-vikas-sahayak.vercel.app/) |
| 12 | [NiyamSathi](SUBMISSIONS.md#track1-12) | Mavericks | [Code](https://github.com/ashwin-0005/niyamsathi) · [Live](https://niyamsathi.vercel.app) |
| 13 | [Bhumi Sahayak](SUBMISSIONS.md#track1-13) | AeroNerds | [Code](https://github.com/utkarshgupta188/aeronerds-CI) · [Live](https://bhumi.utkarshgupta.qzz.io/) · [Demo](https://drive.google.com/open?id=11C6VXQHsjN01hWYHBUolH9AotVoMasvV) |
| 14 | [NiyamSetu](SUBMISSIONS.md#track1-14) | vibe-coder | [Code](https://github.com/shivsingh78/NiyamSetu) · [Live](https://niyamsetu-t4r1.onrender.com) |
| 15 | [Bhumi Vikas Sahayak](SUBMISSIONS.md#track1-15) | Binary Brain | [Code](https://github.com/sachin29it059-gif/bhumi-vikas-sahayak) · [Live](https://bhumi-vikas-sahayak-vert.vercel.app/) · [Demo](https://drive.google.com/open?id=1j4dXKF90k-UYvxU7PvT9yI_iN5zp9el9) |
| 16 | [BHUMI VIKAS SHAYAK](SUBMISSIONS.md#track1-16) | UrbanNex | [Code](https://github.com/vermaanv01-boop/bhumi-vikas-sahayak) · [Live](https://bhumi-vikas-sahayak-1-frontend.onrender.com) · [Demo](https://drive.google.com/open?id=1W_km-yL8bwTyKMQnvLLNyISqzNk0YO8-) |
| 17 | [Sarthi](SUBMISSIONS.md#track1-17) | Clover | [Code](https://github.com/AWS-env/bhumi-vikas-sahayak) · [Live](https://bhumi-vikas-sahayak-beta.vercel.app/) |
| 18 | [Nirmaan Sahayak AI](SUBMISSIONS.md#track1-18) | Geeky Builders | [Code](https://github.com/Fahadkhan9/Nirmaan-Sahayak-AI) · [Live](https://nirmaan-sahayak-ai.vercel.app) · [Demo](https://drive.google.com/open?id=1zpYML39kLxOWivEEQQUzd-n-dTdT9yqx) |
| 19 | [NiyamSetu](SUBMISSIONS.md#track1-19) | Niyamsetu | [Code](https://github.com/aniruddhss/niyamsetu) · [Live](https://niyamsetu-two.vercel.app/) |
| 20 | [Doorabove](SUBMISSIONS.md#track1-20) | Doorabove | [Code](https://github.com/sumitrec/doorabove) · [Live](https://doorabove.vercel.app) |
| 21 | [Bhumi Vikas](SUBMISSIONS.md#track1-21) | F-Society | [Code](https://github.com/harshshrivastava24/Impact-lab-bhumi-vikas.git) · [Live](https://impact-lab-bhumi-vikas.onrender.com) |
| 22 | [Bhumi Vikas sahayak](SUBMISSIONS.md#track1-22) | Team Hawkeye | [Live](https://shvezkvmcvxgylvfwk3b34.streamlit.app/) |
| 23 | [**Bhumi Vikas Sahayak – AI-Powered Building Rules Assistant**](SUBMISSIONS.md#track1-23) | Runtime Rebel | [Code](https://github.com/raushanr64/Bhumi-Vikas-Sahayak-AI-Powered-Building-Rules-Assistant) · [Live](https://bhumi-vikas-sahayak.streamlit.app/) |
| 24 | [Bhumi-vikas-sahayak-claude-impact-lab](SUBMISSIONS.md#track1-24) | mind mavericks | [Code](https://github.com/anubhavg2210/bhumi-vikas-shayak-claude-impact-lab) · [Live](https://bhumi-vikas-shayak-claude-impact-la-ruby.vercel.app/) · [Demo](https://drive.google.com/open?id=1SNmWbLd4N06WLQbkK9WChmnNj6i5YWlw) |
| 25 | [BhoomiSetu](SUBMISSIONS.md#track1-25) | Syncup | [Code](https://github.com/Junaid-Develops/Bhumi-Vikas-Sahayak) |
| 26 | [bhumi shahayak](SUBMISSIONS.md#track1-26) | logicloop | [Code](https://github.com/lokeshh1312/Sahayak-dost-Ai) · [Live](https://track-1-bhumi-vikas-sahayak.vercel.app/) |
| 27 | [Bhumi vikas sahayk](SUBMISSIONS.md#track1-27) | cypherX | [Code](https://github.com/kumarranjankr06-spec/bhumi_vikas.git) · [Live](https://bhumi-vikas.onrender.com) |

### Track 2: Visarjan Ghat Watch

| # | Project | Team | Links |
|---|---|---|---|
| 1 | [Ghat Watch](SUBMISSIONS.md#track2-1) | SWAT | [Code](https://github.com/dopesing3-bita/ghat-watch) · [Live](https://ghat-watch-six.vercel.app) · [Demo](https://drive.google.com/open?id=1IHKLx9PUTtVun_oy25AsHD8eFEtJtjvD) |
| 2 | [Visarjan Sentinel](SUBMISSIONS.md#track2-2) | NikNextt | [Code](https://github.com/Nikhilncy/visarjan-sentinel) · [Demo](https://drive.google.com/open?id=1c3SnBNHOXoQx5mIdNxv_VlxBGNgofTw9) |
| 3 | [Jal Prahari](SUBMISSIONS.md#track2-3) | Jal Prahari | [Code](https://github.com/Yu-369/Jal-Prahari-The-Water-Sentinel) · [Live](https://jal-prahari-the-water-sentinel.vercel.app/) · [Demo](https://drive.google.com/open?id=1ywZjpQhxRVC6D-PxzU4rV9iHCDUfCQa9) |
| 4 | [ghat-watch](SUBMISSIONS.md#track2-4) | developer-dev | [Code](https://github.com/Devpatelgurjar/Ghat-watch) · [Live](https://ghat-watch-v15q.vercel.app/) · [Demo](https://drive.google.com/open?id=1L7AZtlmpvAthAAMqwtrF4BLHGjTaBatU) |
| 5 | [PRAN-VAYU](SUBMISSIONS.md#track2-5) | THETA172 | [Code](https://github.com/shriomverma100/Pran-Vayu.git) · [Live](https://pran-vayu.vercel.app/) |
| 6 | [bhopal_ghat](SUBMISSIONS.md#track2-6) | Abhiinfo | [Code](https://github.com/MishraAbhishek1999/hackthon) |
| 7 | [Visharjan Ghat Watch](SUBMISSIONS.md#track2-7) | Tech titan | [Code](https://github.com/NarayanRajput09/Visharjan-Ghat) · [Live](https://visharjanghat.vercel.app/) · [Demo](https://drive.google.com/open?id=191AppY9vJQf_86GqW3MMwbU6G1ZYlSs5) |
| 8 | [Jal Nirikshak](SUBMISSIONS.md#track2-8) | Reacher | [Code](https://github.com/anukalptripathi532-spec/Jal-Nirikshak) · [Live](https://anukalptripathi532-spec.github.io/Jal-Nirikshak/) |
| 9 | [Jal Drishti](SUBMISSIONS.md#track2-9) | X8 Studio | [Code](https://github.com/anugrah-eng/visarjan-ghat-watch) · [Live](https://anugrah-eng.github.io/visarjan-ghat-watch/site/) |
| 10 | [Visarjan Ghat Advisor](SUBMISSIONS.md#track2-10) | Cypher | [Code](https://github.com/rishabhsahu747422-star/visarjan-ghat.git) · [Live](https://visarjan-ghat.vercel.app/) |
| 11 | [Neel Tarang](SUBMISSIONS.md#track2-11) | Secretos | [Code](https://github.com/ashu-mishra06/Neel-Tarang) · [Live](https://neel-tarang.streamlit.app/) |
| 12 | [GhatWise](SUBMISSIONS.md#track2-12) | PromptPirates | [Code](https://github.com/bitCrafterDS/visarjan-ghat-watch) · [Live](https://bitcrafterds.github.io/visarjan-ghat-watch/) |
| 13 | [GhatWatch](SUBMISSIONS.md#track2-13) | AI BROS | [Code](https://github.com/priyanxs/ghatwatch) · [Live](https://ghatwatch.vercel.app/#bairagarh-sant-hirdaram-kund) · [Demo](https://drive.google.com/open?id=1zmReXZyD1nfksWYCkfirsycxFh2DD_2-) |
| 14 | [GhatShield-AI](SUBMISSIONS.md#track2-14) | Team Setu | [Code](https://github.com/Ayush-Tech-45/GhatSheild-AI) · [Live](https://ghatsheild-ai.onrender.com) |
| 15 | [Visarjan-Ghat-Watch](SUBMISSIONS.md#track2-15) | Nova | [Code](https://github.com/humble-sam/Visarjan-Ghat-Watch) · [Live](https://visarjan-ghat-watch-tau.vercel.app/) · [Demo](https://drive.google.com/open?id=16x6dJoC0Y_CbTTlc0SkHmiu-EEbkoIkB) |
| 16 | [Track 2: Visarjan Ghat Watch](SUBMISSIONS.md#track2-16) | Hack2Build | [Code](https://github.com/milendrakumarbaghel/visarjan-ghat-watch) · [Live](https://visarjan-ghat-watch-frontend.vercel.app/) |
| 17 | [JalDrishti (जलदृष्टि) – Smart Visarjan Ghat Watch & Safety Platform](SUBMISSIONS.md#track2-17) | Vairaba (A fearless Mind ) | [Code](https://github.com/adityasoni-0555/jaldrishti-bhopal-2026) · [Live](https://jaldrishti-bhopal-2026.netlify.app) |
| 18 | [Bhopal Jal Drishti](SUBMISSIONS.md#track2-18) | Wingy-Pari-Tosh | [Code](https://github.com/Pratham1-hue/bhopal_jal_drishti) · [Live](https://bhopal-jal-drishti.onrender.com/) · [Demo](https://drive.google.com/open?id=1PsYQZh5Ah1KbT9ccSI_8TVN_1TTxLLMU) |
| 19 | [Visarjan Ghat Watch](SUBMISSIONS.md#track2-19) | Team innovators | [Code](https://github.com/uttampandeyy987-gif/visarjan-ghat-watch) · [Live](https://visarjan-ghat-watch-flax.vercel.app/) |
| 20 | [Water-Quality-Overview](SUBMISSIONS.md#track2-20) | NeerWatch | [Code](https://github.com/Arpit2005hub/Water-Quality-Overview) · [Live](https://water-quality-zk0i.onrender.com) |
| 21 | [Jail Drishti](SUBMISSIONS.md#track2-21) | Codebloom | [Code](https://github.com/NimitSharma869/Oct-2026-Claude-Community-Bhopal) · [Live](https://jaldrishti-lyart.vercal.app) · [Demo](https://drive.google.com/open?id=1ByGX5JThdf5-VWudDS4zgora3JO8IPug) |
| 22 | [Visarjan Ghat Watch](SUBMISSIONS.md#track2-22) | NeerRakshak | [Code](https://github.com/AnoopShukla-ProjectWorld/claude-community-bhopal/tree/main/track-2-visarjan-ghat-watch/Track2-Visarjanghat-Prj) · [Live](https://visarjan-ghat-watch-iota.vercel.app/) |
| 23 | [GHATPULSE-MP](SUBMISSIONS.md#track2-23) | Parakram | [Code](https://github.com/adilrehman786/ghatpulse-mp) · [Live](https://ghatpulse-mp.vercel.app/) · [Demo](https://drive.google.com/open?id=1xgcvaa8bPq6HkkLZaRk72zGoUBc-Nfoh) |
| 24 | [Ghat Pehredaar](SUBMISSIONS.md#track2-24) | https://bhumi-vikas.onrender.com | [Code](https://github.com/avisinghdotdev/GhatPehredaar) · [Live](https://ca-ghatpehredaar-prod.redisland-50f365ba.centralindia.azurecontainerapps.io) |
| 25 | [ghat watch](SUBMISSIONS.md#track2-25) | ghatwatch | [Code](https://github.com/crystalcoderz/ghatvisarjan) · [Live](https://ghatwatch.prayaas.eu/) |
| 26 | [NeerNiti](SUBMISSIONS.md#track2-26) | Isomers | [Code](https://github.com/Lesjer-kun/NeerNiti) |
| 27 | [Ghat Watch](SUBMISSIONS.md#track2-27) | LOGORITHMS | [Code](https://github.com/nitin-inloop/Visarjan-claude-impact-lab.git) · [Live](https://ghat.flare-x.sh/) |
| 28 | [Visarjan ghat watch](SUBMISSIONS.md#track2-28) | Youthcoders | [Code](https://github.com/ANSHUMAN-570/visarjan-ghat-watch) · [Live](https://anshuman-570-visarjan-ghat-watch-app-mmpnpx.streamlit.app/) |
| 29 | [GhatSeva](SUBMISSIONS.md#track2-29) | Tech pookies | [Code](https://github.com/r3ban-hub/ghatseva-by-tech-pookies.git) · [Live](https://ghatseva-by-tech-pookies-1qds-two.vercel.app/en/) |
| 30 | [GhatWatch](SUBMISSIONS.md#track2-30) | Nexora | [Code](https://github.com/shanumakode/Safal) · [Live](https://golden-cendol-8f075a.netlify.app/) |
| 31 | [GhatRakshak](SUBMISSIONS.md#track2-31) | https://bhumi-vikas.onrender.com | [Code](https://github.com/gauravshivhare-prj/Impact-lab) · [Live](https://ghatwatch.onrender.com/) · [Demo](https://drive.google.com/open?id=1vF2yecXIYhERRm_vZsaCcKE8fWngMmCh) |
| 32 | [EcoNeer](SUBMISSIONS.md#track2-32) | X-Factor | [Code](https://github.com/Yuvraj1327/X-factor) · [Live](https://visarjan-ghat-watch-v2.vercel.app/) |
| 33 | [JalDrishti AI](SUBMISSIONS.md#track2-33) | Khonshu | [Code](https://github.com/1309harsh-oss/Environmental-Operation-System.git) · [Live](https://frontend-green-eight-6sryntgmnu.vercel.app/) |
| 34 | [visarjan-ghat](SUBMISSIONS.md#track2-34) | AquaSentinel | [Code](https://github.com/abhaysahu403/visarjan-ghat-watch) · [Live](https://visarjan-ghat-watch-omega.vercel.app/) |
| 35 | [GhatWatch](SUBMISSIONS.md#track2-35) | CreativeMinds | [Code](https://github.com/tejasavnema12/hackathon-project.git) · [Live](https://tejas.inxeoz.com) · [Demo](https://drive.google.com/open?id=1ehLBw1tqgDzer_myrNsXMY8T59Z6CooE) |
| 36 | [NeerSetu](SUBMISSIONS.md#track2-36) | NeerSetu | [Code](https://github.com/jayeshrajani/NeerSetu) · [Live](https://neersetu-umber.vercel.app/) |
| 37 | [Ghat Triage](SUBMISSIONS.md#track2-37) | Spectra Elite | [Code](https://github.com/U-jjwal/CLAUDE_HACKATHON.git) · [Live](https://ghattriage.up.railway.app/) · [Demo](https://drive.google.com/open?id=1iUfmBoHMSh6Vqd8vZRMR3ZEwX-WF3PTY) |
| 38 | [NirmalGhat](SUBMISSIONS.md#track2-38) | NirmalGhat | [Code](https://github.com/Paramdubey/nirmalghat) · [Live](https://nirmalghat.vercel.app) |
| 39 | [SankatGhat](SUBMISSIONS.md#track2-39) | SankatGhat | [Live](https://sankatghat.freebuff.app/brief) |
| 40 | [Green Visarjan](SUBMISSIONS.md#track2-40) | track_hawk | [Code](https://github.com/shaketraj156-ops/green-Visargan) · [Live](https://greenvisarjan.up.railway.app/) · [Demo](https://drive.google.com/open?id=1e2lgH4TXW9Jw0fdVtERde6R8TffRIqkO) |

## Credits

The data files and source PDFs come from the participant pack at https://github.com/Laaaaksh/bhopal-impact-lab-2026, prepared by Laksh Sadhwani.

Organisers: Aniket Sahu (Claude Community Ambassador) and Arun Pratap Singh Chandel (Cerebras Community Ambassador).
