# P0 — Workspace

**DSA 405 · Fall 2026 · Project Milestone 0**

| | |
|---|---|
| **Introduced** | Week 1 (Aug 21), in class |
| **Due** | **Thursday, Aug 27, 11:59 PM** |
| **Weight** | In-class credit, completion-graded. No rubric. Done on time is done. |
| **Submit** | Colab share link + repo URL to Moodle. Name the notebook `DSA405_001_FA26_P0_[yourUnityID]` |
| **Time** | 30–45 minutes: smoke test ~10, Drive folder ~5, GitHub account and repo ~15–25 |

---

## What P0 is

Proof that your tools work before anything depends on them.

Next Friday you load real data in class. A student who discovers on Aug 28 that Colab will
not sign in, or that their browser blocks Drive, spends the 25-minute Explore block fixing
their laptop instead of working the Lab. This milestone moves that discovery to a week when
it costs nothing.

Three things, none of them graded on quality. They either work or they don't, and "they
don't" is exactly what I want to hear about *this* week.

---

## 1. A working Colab notebook

This course runs in **Google Colab**. Nothing to install; every Lab reads its data over
HTTPS.

1. Go to [colab.research.google.com](https://colab.research.google.com) and sign in with a
   Google account.
2. Open a new notebook and rename it `DSA405_001_FA26_P0_[yourUnityID]`.
3. Run this cell:

```python
import pandas as pd

DATA = "https://raw.githubusercontent.com/jon-holt/DSA-405-Student/main/datasets/"
dining = pd.read_csv(DATA + "wolfpack_dining_raw.csv")
print(len(dining), "rows,", dining.shape[1], "columns")
```

**Expected output: `366 rows, 10 columns`.** That exact line. Any error, and any other
number, means something is wrong — post it to the Week 1 forum with the full message and I
will sort it out before Friday. Do not sit on a broken environment; that is the one way P0
can hurt you.

You have now loaded the dataset we spend Weeks 2–4 taking apart. Feel free to look around.

## 2. A `DSA405` folder in your Google Drive

Make a folder named `DSA405` in your Drive and save the notebook into it (**File → Move**
in Colab). Every notebook you write this term lives there, named by the course convention
`DSA405_001_FA26_[assignment]_[yourUnityID]`, so that in November you are not excavating
`Untitled27.ipynb`.

## 3. A GitHub account and your project repo

Your course project ships, in Week 14, as a **public repository** — a documented,
reproducible pipeline you can show an employer. It starts as an empty box, today.

1. Create a [GitHub](https://github.com) account if you do not have one. Any professional
   username is fine; you will be sharing this.
2. Create a new **public** repository named `dsa405-project`.
3. Initialize it with a `README.md` (one sentence about you is plenty for now) and the
   **Python** `.gitignore` template GitHub offers on the same screen.

That is all Git you need this week. From P2 onward the repo fills up with your project —
raw data preserved untouched in `data/raw/`, cleaned data, notebooks, a cleaning log — and
the P2 handout walks you through that structure when you need it.

**One rule starts now: never commit personal or identifiable information about anyone.**
The repo is public. So is your future.

---

## Submit

Two links on Moodle, by Thursday, Aug 27, 11:59 PM:

- [ ] Your Colab notebook, shared so that anyone at NC State with the link can **view** it,
      showing the `366 rows, 10 columns` output
- [ ] Your repo URL

If either one refused to cooperate, submit what you have plus a sentence saying what broke.
A described failure gets full credit and gets fixed; a silent one surfaces in Week 2 at the
worst possible moment.
