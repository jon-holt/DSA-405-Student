# P2: Data Audit, Cleaning Log & Provenance Brief

**DSA 405 · Fall 2026 · Project Milestone 2**

| | |
|---|---|
| **Introduced** | Week 3 (Sep 4), worked through Weeks 4–6 |
| **Due** | **Thursday, Oct 1, 11:59 PM** |
| **Weight** | 10% of course grade · scored on the P2 rubric, 5 criteria |
| **Submit** | Notebook + repo link to Moodle. Filename `DSA405_002_FA26_P2_[yourUnityID].ipynb` |
| **Also this window** | **Bench Check 1**, Weeks 5–7 |
| **Time** | 4–5 hours spread across three weeks |

---

## Purpose

P2 covers one of the project's two data sources: audit it, fix what can be fixed, and
**document every decision so that a stranger could reverse any one of them.**

That last clause is the assignment. The rubric puts its heaviest weight (×3) on the
cleaning log, not on the cleaning. By November, the reason 43 rows were dropped in
September will not be remembered by the author, the grader, or anyone who inherits the
work. The log is that record.

**Only one source needs cleaning for P2.** The second source, the join, and the
verification suite belong to P3.

---

## Deliverables

Five things, in one notebook, in this order.

### 1. The audit

A **systematic** pass over the raw data, with output that shows each check.

At minimum, for every column the analysis will use:

- dtype as loaded, and dtype as it should be
- count and rate of missing values, `dropna=False`
- number of distinct values
- min, max, and range for anything numeric
- the full set of distinct values for anything categorical with under about 30 levels

Then the part most often skipped:

**State which classes of defect were checked for and *not* found.** Sentinel values
posing as data. Total or subtotal rows inside the observations. Leading zeros in
identifiers. Encoding damage. Duplicate keys. Dates in more than one format. Numbers
stored as text.

Data that is genuinely clean is a legitimate finding and can score full marks on this
criterion.

### 2. The data dictionary

**At least five variables**, and every variable used in the analysis.

| Field | What goes in it |
|---|---|
| Variable name | as it appears in the cleaned data |
| Type | int, float, string, boolean, date, category |
| Units | dollars, people, percent, days, count. "Number" is not a unit. |
| Factor levels | the complete set, for categoricals |
| Valid range | what values are possible, rather than what occurred |
| Missingness | how many, and what missing *means* for this variable |
| Notes | anything a user would get wrong without being told |

**Flag any variable whose observed values contradict its documentation.** If the
codebook says 1–5 and the data contains a 7, record it in the notes; it is one of the
most valuable findings a dictionary can report.

### 3. The cleaning log

The heaviest-weighted criterion (×3). One row per **decision**, not per line of code.

| # | Column | Change made | Rows/cells affected | Why | What this costs |
|---|---|---|---|---|---|
| 1 | `score` | Stripped whitespace | 47 cells | Padding blocked numeric conversion | Nothing |
| 2 | `score` | Removed trailing `*` | 12 cells | Footnote marker glued to the value | A reader can no longer see which values were revised |
| 3 | `unit_code` | Re-read with `dtype=str` | 31 rows | Leading zeros were deleted by the default read | Nothing; the column was never numeric |
| 4 | | | | | |

Four rules, and they are the rubric:

**Every row has a number.** "Some rows" is not a number. 

**Every row has a reason, not a restatement.** "Converted to numeric" is *what*. "The
column was text because footnote markers were glued to the values, and the analysis
needs a mean" is *why*.

**Every row has a cost**, even when the cost is "nothing." Most cleaning discards
information, and the cost column records which. It is the column most often left blank.

**A reader can reverse any single decision** using only the log and the raw file.

Aim for **10 to 20 rows**.

### 4. Row and column accounting

These numbers must reconcile.

```
Rows in raw file                      _____
Rows removed as exact duplicates      _____
Rows removed as near-duplicates       _____
Rows removed for other reasons        _____   (each one logged above)
Rows in cleaned file                  _____

Columns in raw file                   _____
Columns dropped                       _____   (and why)
Columns added                         _____
Columns in cleaned file               _____
```

A mismatch means something happened that was not logged. 

### 5. The Provenance Brief

**200 words maximum.** Written for a smart reader who does not work with data.

Cover: what this dataset is, who produced it, why they produced it, what it contains,
and what it can and cannot support.

**No jargon.** "Records of 4,312 restaurant inspections carried out by the county
between 2023 and 2025," not "n=4,312 observations across 11 features."

The test: a reader in a different major should be able to say what the data is and
where it came from. Any clarifying question they ask marks a sentence to rewrite.

---

## Standing requirements, from P2 onward

Every milestone from here needs all four. They are part of the rubric and are not
re-explained in later handouts.

- [ ] Notebook runs **top to bottom on a restarted kernel**
- [ ] `README.md` states what the project is, where the data came from, and how to run it
- [ ] `requirements.txt` complete and pinned
- [ ] **Raw data preserved unmodified** in `data/raw/`, and project code never writes there

---

## How this is graded

| Criterion | Wt | The short version |
|---|---|---|
| Diagnosis & data dictionary | ×2 | Systematic audit, quantified problems, and what was checked for and not found |
| Cleaning execution | ×2 | Correct, proportionate, alternatives considered |
| **Cleaning log** | **×3** | Counts, reasons, costs, reversible |
| Provenance Brief | ×1 | A non-specialist understands it |
| Tidy structure & reproducibility | ×2 | Tidy, runs clean, README and requirements present |

Full descriptors in *DSA 405 Project Rubrics*. Proficient across the board is an 88.

**Submit a self-scored copy of the rubric.** It is ungraded and catches omissions before grading does.

---

## Two common failure modes

**The clean notebook with no log.** Correct code, correct output, and no record of a
single decision. Log while working; reconstructing the log afterward can miss decisions.

**The log that lists operations.** Twenty rows, every one saying what a line of code
did, none saying why. That is a changelog, not a cleaning log.

## If the data turns out to be clean

Some well-curated sources leave little to fix. That is not a problem and not a reason
to switch datasets.

Instead: document the audit thoroughly, report what was checked for and not found, and
spend the effort on the **provenance** and the **limits** of the data. A well-curated
dataset was curated by someone, for a purpose, and asking what they left out is a richer
question than fixing typos.

If unsure whether this applies, ask Dr. Holt.
