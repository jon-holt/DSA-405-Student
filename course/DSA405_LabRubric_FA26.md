# DSA 405: Lab Rubric
### A1–A9, the take-home half of the weekly Lab — Fall 2026

> Published to you in Week 1, alongside the Project Rubrics. Four criteria, identical every
> week. By Week 3 you should be able to score your own Lab before you submit it.

---

## What this covers

Each week has **one Lab**. The half you work during Explore is in-class credit, scored on
engagement. The half you finish at home is the take-home, **A1 through A9**, and together
those are **30% of your course grade**. This rubric scores that take-home half.

Nine take-homes across fourteen weeks: A1 (Wk 1), A2 (Wk 2), A3 (Wk 3), A4 (Wk 4),
A5 (Wk 5), A6 (Wk 7), A7 (Wk 8), A8 (Wk 9), and A9 (Wk 11). Weeks 6, 10, and 12 have no
take-home; a project milestone or work session takes its place. Each is due the Thursday
after class at 11:59 PM, except A9, which is due **Thu Nov 12** — you get the extra week
because P3 lands Nov 5.

Budget: finishing the Lab at home should take **45–60 minutes** — finishing what Explore
started, not starting over. If it is routinely taking you longer, tell me; that is a defect
in my design, not in your effort.

Submission naming: `DSA405_001_FA26_A2_[yourUnityID]`, and so on.

---

## How Scoring Works

The same four-level scale as the project:

| Level | What it means |
|---|---|
| **4 — Excellent** | Correct, complete, and shows judgment about *why* this choice and not the alternatives |
| **3 — Proficient** | Correct and complete |
| **2 — Developing** | Attempted, but incomplete or partly wrong |
| **1 — Limited** | Missing, or present but unusable |

Your score is the **weighted mean** of the four criteria, converted with the same table as
the project rubrics:

| Weighted mean | Percentage | | Weighted mean | Percentage |
|---|---|---|---|---|
| 4.0 | 100 | | 2.4 | 79 |
| 3.8 | 98 | | 2.2 | 76 |
| 3.6 | 95 | | 2.0 | 73 |
| 3.4 | 93 | | 1.8 | 69 |
| 3.2 | 90 | | 1.6 | 66 |
| 3.0 | 88 | | 1.4 | 62 |
| 2.8 | 85 | | 1.2 | 59 |
| 2.6 | 82 | | 1.0 | 55 |

As with the project: **Proficient on everything earns an 88, a B+.** Correct and complete
work is good work. The A range asks for judgment — evidence you checked something that could
have been wrong, and can say why your choice beat the alternatives.

---

## The Four Criteria

| # | Criterion | Wt | 4 — Excellent | 3 — Proficient | 2 — Developing | 1 — Limited |
|---|---|---|---|---|---|---|
| 1 | **Correctness** | ×2 | Every answer right, and where the data allowed more than one defensible result, states which was chosen and why. | Answers match the data; nothing material missing. | Some answers wrong or missing, or right numbers from code that would not survive a rerun. | Answers missing, or unrelated to the data. |
| 2 | **Verification** | ×2 | Ran a check that could actually have failed — `value_counts(dropna=False)`, row counts before and after, an assertion — and shows the output. Also states what was checked for and *not* found. | At least one real check per major step, with the output shown. | Asserts correctness without evidence ("it looked right"), or runs checks that could not fail. | No checking visible anywhere. |
| 3 | **Interpretation** | ×2 | Says what the result means, what it cannot support, and names something specific the data leaves out. Every claim carries a number. | States what the numbers show, in plain language, with counts. | Restates the output without saying what it means, or claims outrun the evidence. | No prose, or prose the output contradicts. |
| 4 | **Documentation** | ×1 | A stranger could rerun and follow it: named steps, data source stated, AI note specific about what was used and what was changed. | Notebook runs top to bottom on a clean kernel; steps labeled; AI note present. | Runs only with manual intervention, or the AI note is missing or vague. | Does not run, or the saved outputs contradict the code. |

**On Criterion 2.** This is the course. "417 rows in, 392 out, 25 dropped as exact
duplicates" is verification. "The cleaning worked" is not. A check that cannot fail —
printing `.head()` and moving on — scores as no check.

**On Criterion 4.** Every submission carries a one-or-two-sentence AI note: which tools,
for what, what you changed (see the AI Use Policy in the syllabus). Restart your kernel and
run top to bottom before you submit; a notebook that only runs in the order you happened to
write it fails a stranger, and I am the stranger.

**On A1.** Week 1's take-home is your introduction and skills self-check, so there are no
wrong answers; Criterion 1 reads as *complete and specific* there. The other three apply
as written.
