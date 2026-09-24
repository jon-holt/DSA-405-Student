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
September will not be remembered by the author, the grader, or anyone who takes over the
work later. The log is that record.

**Only one source needs cleaning for P2.** The second source, the join, and the
verification suite belong to P3.

---

## Deliverables

Five things, in one notebook, in this order.

### 1. The audit

A **systematic** pass over the raw data, with output that shows each check.

At minimum, for every column the analysis will use:

- dtype as loaded, and dtype as it should be (the dtype is the data type pandas
  assigned to the column)
- count and rate of missing values, `dropna=False`
- number of distinct values
- min, max, and range for anything numeric
- the full set of distinct values for anything categorical with under about 30 levels

Then the part most often skipped:

**State which classes of defect were checked for and *not* found.** Sentinel values
recorded as if they were real data (a sentinel is a special value, such as 999 or "N/A",
written inside a data column to mean "no real value here"). Total or subtotal rows mixed
in with the observations. Leading zeros in identifiers. Text garbled by reading the file
with the wrong character encoding. Duplicate keys. Dates in more than one format. Numbers
stored as text.

Data that is genuinely clean is a legitimate finding and can earn the top score on this
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

| # | Column | Change made | Rows/cells affected | Why | What is lost |
|---|---|---|---|---|---|
| 1 | `score` | Stripped whitespace | 47 cells | Extra spaces prevented numeric conversion | Nothing |
| 2 | `score` | Removed trailing `*` | 12 cells | A footnote marker was attached to the end of the value | A reader can no longer see which values were revised |
| 3 | `unit_code` | Re-read with `dtype=str` | 31 rows | Leading zeros were deleted by the default read | Nothing; the column was never numeric |
| 4 | | | | | |

Four rules. The rubric scores the log on exactly these four:

**Every row has a number.** Write the exact count of rows or cells the change touched.

**Every row has a reason, not a restatement.** "Converted to numeric" is *what*. "The
column was text because footnote markers were attached to the values, and the analysis
needs a mean" is *why*.

**Every row records what information is lost**, even when the answer is "nothing." Most
cleaning discards some information, and this column records which information is gone. It
is the column most often left blank.

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

**200 words maximum.** Provenance means the origin of the data: who made it, how, and
why. The brief is written for a smart reader who does not work with data.

Cover: what this dataset is, who produced it, why they produced it, what it contains,
and what it can and cannot support.

**No jargon.** "Records of 4,312 restaurant inspections carried out by the county
between 2023 and 2025," not "n=4,312 observations across 11 features."

The test: a reader in a different major should be able to say what the data is and
where it came from. Any clarifying question they ask marks a sentence to rewrite.

---

## Standing requirements, from P2 onward

Every milestone from here needs all of these. They are part of the rubric and are not
re-explained in later handouts.

- [ ] Notebook runs **top to bottom on a restarted kernel**
- [ ] `README.md` states what the project is, where the data came from, and how to run it
- [ ] **Raw data preserved unmodified** in `data/raw/`, and project code never writes there

---

## Moving files between Colab and GitHub

You write your notebook in Google Colab. GitHub stores your project files. These are two
separate websites. A change you make in one place does not appear in the other, so you
move files between them yourself. This section explains how.

One rule keeps this simple: **edit each file in only one of the two places.** You edit
the notebook in Colab. You edit every other file on GitHub. No file is edited in both.

### On GitHub: the data folder and the README

GitHub has no button for making a new folder. You make a folder by typing its path into
the name box when you create a file.

1. Open your repository. Click **Add file**, then **Create new file**.
2. In the name box, type `data/raw/SOURCES.md`. Each slash you type creates a folder.
   This makes a folder named `data`, a folder named `raw` inside it, and a file named
   `SOURCES.md` inside that.
3. In that file, write one line for each data file you are about to add. Give the web
   address you downloaded it from, and the date you downloaded it. Click **Commit
   changes** (a commit is one saved set of changes, with a short message saying what
   changed).
4. Open the `data/raw/` folder. Click **Add file**, then **Upload files**, and add your
   raw data files. Click **Commit changes**.
5. Go back to the top of your repository and open `README.md`. Click the pencil icon to
   edit it. Write what the project is, where the data came from, and how to run it. Click
   **Commit changes**.

After step 4, do not edit the files in `data/raw/` again, and do not let your notebook
write to that folder. That is what "preserved unmodified" means in the standing
requirements above.

### In Colab: the notebook

1. Write and run your notebook in Colab as usual.
2. Choose **File**, then **Save a copy in GitHub**. The first time you do this, a window
   opens asking you to let Colab use your GitHub account. Allow it. If nothing opens,
   your browser blocked the window, so allow popups for Colab and try again.
3. A box appears. Choose your repository. The file path is already filled in with your
   notebook's name, and you keep it the same every time you save. Using the same path
   means each save updates one file, instead of adding another copy of the notebook to
   your repository.
4. Check the box labeled **Include a link to Colab**. This puts a button at the top of
   your notebook on GitHub. Anyone reading your repository can click that button and open
   the notebook in Colab, ready to run.
5. Write a short message saying what changed, then click **OK**.

### Reading your data back from the repository

Once your raw data files are in `data/raw/` in a public repository, your notebook can
read them over the web, the same way every Lab in this course reads the class data:

```python
DATA = "https://raw.githubusercontent.com/YOUR-USERNAME/dsa405-project/main/data/raw/"
df = pd.read_csv(DATA + "your_file.csv")
```

Written this way, your notebook runs for anyone who opens it, with nothing to download
first. It also means your code cannot change your raw data, because reading from a web
address cannot write to the file at the other end.

---

## How this is graded

| Criterion | Wt | The short version |
|---|---|---|
| Diagnosis & data dictionary | ×2 | Systematic audit, quantified problems, and what was checked for and not found |
| Cleaning execution | ×2 | Correct, proportionate, alternatives considered |
| **Cleaning log** | **×3** | Counts, reasons, what was lost, reversible |
| Provenance Brief | ×1 | A non-specialist understands it |
| Tidy structure & reproducibility | ×2 | Tidy, runs without errors, README present |

Full descriptors in *DSA 405 Project Rubrics*. Proficient on every criterion is an 88.

**Submit a self-scored copy of the rubric.** It is ungraded, and it helps you notice missing pieces before we grade.

---

## Two common failure modes

**The clean notebook with no log.** Correct code, correct output, and no record of a
single decision. Log while working; reconstructing the log afterward can miss decisions.

**The log that lists operations.** Twenty rows, every one saying what a line of code
did, none saying why. A log without reasons is a record of code changes, not a
cleaning log.

## If the data turns out to be clean

Some well-curated sources leave little to fix. That is not a problem and not a reason
to switch datasets.

Instead: document the audit thoroughly, report what was checked for and not found, and
put the effort into the **provenance** and the **limits** of the data. A well-curated
dataset was curated by someone, for a purpose, and asking what they left out is a more
valuable question than fixing typos.

If unsure whether this applies, ask Dr. Holt.
