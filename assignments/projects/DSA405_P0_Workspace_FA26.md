# P0: Workspace

**DSA 405 · Fall 2026 · Project Milestone 0**

| | |
|---|---|
| **Introduced** | Week 1 (Aug 21), in class |
| **Due** | **Thursday, Aug 27, 11:59 PM** |
| **Weight** | In-class credit, completion-graded. No rubric. |
| **Submit** | Colab share link + repo URL to Moodle. Name the notebook `DSA405_002_FA26_P0_[yourUnityID]` |
| **Time** | 30–45 minutes: smoke test ~10, Drive folder ~5, GitHub account and repo ~15–25 |

---

## Purpose

P0 confirms that the required tools work before any coursework depends on them.

---

## 1. A working Colab notebook

The course runs in **Google Colab**. There is nothing to install; every Lab reads its
data over HTTPS.

1. Go to [colab.research.google.com](https://colab.research.google.com) and sign in with a
   Google account.
2. Open a new notebook and rename it `DSA405_002_FA26_P0_[yourUnityID]`.
3. Run this cell:

```python
import pandas as pd

DATA = "https://raw.githubusercontent.com/jon-holt/DSA-405-Student/main/datasets/"
dining = pd.read_csv(DATA + "wolfpack_dining_raw.csv")
print(len(dining), "rows,", dining.shape[1], "columns")
```

**Expected output: `366 rows, 10 columns`.** That exact line. On any error, or any other
number, post the full error message to the Week 1 forum before Friday. Do not sit on a
broken environment.

This is the dataset used throughout Weeks 2–4.

## 2. A `DSA405` folder in Google Drive

Make a folder named `DSA405` in Drive and save the notebook into it (**File → Move**
in Colab). Every notebook written this term goes in this folder, named by the course
convention `DSA405_002_FA26_[assignment]_[yourUnityID]`.

## 3. A GitHub account and the project repo

The course project is submitted in Week 14 as a **public repository** containing a
documented, reproducible pipeline. This milestone creates the empty repository.

1. Create a [GitHub](https://github.com) account if needed. Choose a professional
   username; the repository will be shared publicly.
2. Create a new **public** repository named `dsa405-project`.
3. Initialize it with a `README.md` (one sentence is sufficient for now) and the
   **Python** `.gitignore` template GitHub offers on the same screen.

No further Git work is required this week. From P2 onward the repo holds the project:
raw data preserved untouched in `data/raw/`, cleaned data, notebooks, and a cleaning
log. The P2 handout describes that structure.

**One rule applies from now on: never commit personal or identifiable information about
anyone.** The repository is public.

---

## Submit

Two links on Moodle, by Thursday, Aug 27, 11:59 PM:

- [ ] The Colab notebook, shared so that anyone at NC State with the link can **view** it,
      showing the `366 rows, 10 columns` output
- [ ] The repo URL

If either part failed, submit what exists plus a sentence describing what broke. A
described failure receives full credit and gets fixed; an unreported one surfaces in
Week 2.
