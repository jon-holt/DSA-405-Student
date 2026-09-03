# DSA 405: Lab Rubric
### A1–A9, the take-home half of the weekly Lab · Fall 2026

---

## Scope

Each week has **one Lab**. The half worked during Explore is in-class credit, scored on
engagement. The half finished at home is the take-home, **A1 through A9**; together the
take-homes are **30% of the course grade**. This rubric scores the take-home half.

Nine take-homes across fourteen weeks: A1 (Wk 1), A2 (Wk 2), A3 (Wk 3), A4 (Wk 4),
A5 (Wk 5), A6 (Wk 7), A7 (Wk 8), A8 (Wk 9), and A9 (Wk 11). Weeks 6, 10, and 12 have no
take-home; a project milestone or work session takes its place. Each is due the Thursday
after class at 11:59 PM, except A9, which is due **Thu Nov 12**; the extra week accounts
for P3 being due Nov 5.

Budget: finishing the Lab at home should take **45–60 minutes**, continuing what Explore
started rather than starting over. If it routinely takes longer, report that to the
instructor; the time budget is a design commitment, and overruns indicate a problem with
the Lab, not with the student.

Submission naming: `DSA405_002_FA26_A2_[yourUnityID]`, and so on.

---

## How Scoring Works

The same four-level scale as the project:

| Level | What it means |
|---|---|
| **4 — Excellent** | Correct, complete, and shows judgment about *why* this choice and not the alternatives |
| **3 — Proficient** | Correct and complete |
| **2 — Developing** | Attempted, but incomplete or partly wrong |
| **1 — Limited** | Missing, or present but unusable |

The score is the **weighted mean** of the four criteria, converted with the same table as
the project rubrics:

The conversion is one linear formula: **percentage = 88 + (weighted mean − 3) × 12**,
rounded to the nearest whole number. Reference points:

| Weighted mean | Percentage | | Weighted mean | Percentage |
|---|---|---|---|---|
| 4.0 | 100 | | 2.4 | 81 |
| 3.8 | 98 | | 2.2 | 78 |
| 3.6 | 95 | | 2.0 | 76 |
| 3.4 | 93 | | 1.8 | 74 |
| 3.2 | 90 | | 1.6 | 71 |
| 3.0 | 88 | | 1.4 | 69 |
| 2.8 | 86 | | 1.2 | 66 |
| 2.6 | 83 | | 1.0 | 64 |

As with the project rubrics: Proficient on every criterion converts to an 88, a B+.
Correct and complete work earns that grade. The A range requires evidence of judgment,
meaning a check that could have failed and a stated reason the chosen approach beat the
alternatives.

---

## The Four Criteria

| # | Criterion | Wt | 4 — Excellent | 3 — Proficient | 2 — Developing | 1 — Limited |
|---|---|---|---|---|---|---|
| 1 | **Correctness** | ×2 | Every answer right, and where the data allowed more than one defensible result, states which was chosen and why. | Answers match the data; nothing material missing. | Some answers wrong or missing, or right numbers from code that would not survive a rerun. | Answers missing, or unrelated to the data. |
| 2 | **Verification** | ×2 | Ran a check that could have failed (`value_counts(dropna=False)`, row counts before and after, an assertion) and shows the output. Also states what was checked for and *not* found. | At least one real check per major step, with the output shown. | Asserts correctness without evidence ("it looked right"), or runs checks that could not fail. | No checking visible anywhere. |
| 3 | **Interpretation** | ×2 | Says what the result means, what it cannot support, and names something specific the data leaves out. Every claim carries a number. | States what the numbers show, in plain language, with counts. | Restates the output without saying what it means, or claims outrun the evidence. | No prose, or prose the output contradicts. |
| 4 | **Documentation** | ×1 | A stranger could rerun and follow it: named steps, data source stated, AI note specific about what was used and what was changed. | Notebook runs top to bottom on a clean kernel; steps labeled; AI note present. | Runs only with manual intervention, or the AI note is missing or vague. | Does not run, or the saved outputs contradict the code. |

**On Criterion 2.** "417 rows in, 392 out, 25 dropped as exact duplicates" is
verification. "The cleaning worked" is not. A check that cannot fail, such as printing
`.head()` and moving on, scores as no check.

**On Criterion 4.** Every submission carries a one-or-two-sentence AI note: which tools,
for what, and what was changed (see the AI Use Policy in the syllabus). Restart the kernel
and run the notebook top to bottom before submitting; a notebook that only runs in the
order it was written does not satisfy this criterion.

**On A1.** Week 1's take-home is an introduction and skills self-check, so it has no
wrong answers; Criterion 1 reads as *complete and specific* there. The other three
criteria apply as written.
