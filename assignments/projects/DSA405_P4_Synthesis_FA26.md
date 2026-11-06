# P4: Project Synthesis

**DSA 405 · Fall 2026 · Project Milestone 4**

| | |
|---|---|
| **Introduced** | Week 12 (Nov 6) work session |
| **Due** | **Friday, Nov 20, 11:59 PM** |
| **Weight** | 18% of course grade · scored on the P4 rubric, 7 criteria |
| **Lightning talk** | Nov 13 or Nov 20 · separate 10% · see below |
| **Submit** | Repo URL + notebook + report to Moodle, with a self-scored rubric |
| **Time** | 8–10 hours. Start on Nov 6, not on Nov 18. |

**There is no revision on this milestone.** Nov 20 is the last meeting of the
semester, so there is no week after it in which a revision could be returned.

---

## What P4 asks for

**P4 does not grade P2 and P3 again.** Your data dictionary, cleaning log, join, and
verification suite were already scored. Carrying them forward earns one row of the
rubric (Criterion 7), and only if you **updated them to match the final state of the
data**.

P4 asks four new questions:

1. **What did the project find?**
2. **Does the whole project form one consistent argument, from the question to the
   conclusion?**
3. **Who does the data leave out?**
4. **Can a stranger reproduce it?**

**Synthesis** means putting the separate parts of the project together into one
argument. P4 grades synthesis as its own skill. That is why strong P2 and P3 work that
is placed side by side with nothing new added scores in the low 70s here: the four
questions above are new questions, and the report is where you answer them.

---

## What you turn in

Three things go in your public repo: the notebook, the report, and the README. The
fourth, the self-scored rubric, goes to Moodle with your submission.

### 1. The reproducible notebook

The notebook runs from top to bottom on a restarted kernel, from the raw data to the
final figures, with no errors.

### 2. The written report

Nine sections, with these headings, in this order. Write it as Markdown cells in the
notebook or as a separate `.md` file in the repo. Either is fine.

| § | Section | What it must contain |
|---|---|---|
| 1 | **Data motivation** | The question, why you chose it, and **how the question changed** once you had the real data |
| 2 | **Sources, provenance & terms** | For each source: who produced it, why they produced it, how it was collected, what it covers, its license, how you accessed it, and the date you accessed it |
| 3 | **Data dictionary & metadata** | Updated to describe the **final** data, not the P2 version |
| 4 | **Wrangling narrative** | The path from raw data to final data, readable **without opening the notebook**. Every decision that required judgment is explained. Every row and column is accounted for. |
| 5 | **Integration & verification** | The join, the keys, the cardinality (one-to-one, one-to-many, or many-to-many), and **how you know the result is correct** |
| 6 | **Findings** | What the project learned, with honest statements about what is uncertain |
| 7 | **Who is missing** | The specific people, places, or cases the data excludes, and how each exclusion affects the conclusions |
| 8 | **AI use log & reflection** | Which tools you used, for which tasks, and at least one thing a model got wrong |
| 9 | **Reproducibility** | The repo link and instructions a stranger can follow |

**Length:** whatever those nine sections need. Most reports come out between 1,500 and
2,500 words. Word count is not graded in either direction.

### 3. `README.md`

A stranger reads only this file. It must contain:

- One paragraph that says what the project is and what it found
- The data sources, with links and licenses
- How to run the project, written as commands
- Which packages it needs, with version numbers
- The structure of the repo, so a reader knows where each file is

---

## Four sections that most people underestimate

### § 1: how the question changed

Nearly every real project's question changes once you have the data. **Name that
change.** Naming it is evidence that you read the data instead of only processing it.
A Section 1 question that is word-for-word identical to your P1 question usually means
the change happened and you did not notice it, not that it never happened.

### § 4: the wrangling narrative

The test is this: a reader should be able to follow the path from raw data to final
data without opening the notebook.

Write a narrative, which means connected sentences that give reasons, not a list of
operations. For example: "The county publishes scores as text with revision markers
attached to the values, so 12 values would not convert to numbers. I removed the
markers and recorded the affected rows, because a revised score means something
different from an original one."

### § 7: who is missing

**Name specific people, places, or cases the data excludes, and say what that does to
your conclusions.**

A sentence that would fit any dataset, such as "the sample could be larger" or "there
may be selection bias," tells your reader nothing about this data. Compare it with this:
"Inspections before 2024 for one municipality were never digitized, so any trend starts
in 2024 for that city and in 2023 for the others. The year-over-year comparison excludes
it, and we do not know which direction that pushes the result." That version names who
is missing, since when, and what it does to the conclusions. That is what this
criterion is looking for.

Then **name one question this data cannot answer, no matter how well it is cleaned.**

### § 8: the AI use log

**Report at least one thing a model got wrong, how you caught it, and what that changed
about how you now use these tools.**

"Used Claude for debugging" could describe any project this semester, so it shows your
reader nothing. Compare: "I asked for a merge and got `how='inner'`, which removed 340
unmatched rows with no error message. I caught it because I had written the row-count
assertion first." That version shows exactly the working method this course has been
building.

---

## Technical ambition and your tier

Criterion 5 is the **only** row in the entire course where your declared tier matters.
A **tier-gated** criterion is one where the highest score you can receive depends on
the tier you declared.

| Tier | Highest score possible on Criterion 5 |
|---|---|
| Tier 1 — Solid | 3 (Proficient) |
| Tier 2 — Ambitious | 4 (Excellent) |
| Tier 3 — Stretch | 4 (Excellent) |

Every other row on every rubric ignores tier. **A Tier 1 project done with care scores
3s and 4s across the other six rows and reaches the A-minus range.**

**Stretch bonus: +2 percentage points on your final course grade, capped at 100.** It is
open to **any** student at any declared tier who adds a stretch component that is
present, working, **and verified**:

- Structured extraction from unstructured text or PDF, checked against a schema you
  defined (a schema is a written definition of the fields and value types the output
  must contain), or
- A third source that requires a many-to-many resolution, with the cardinality tested
  before and after the join

**A stretch component that is attempted but not verified earns nothing.** The
verification is the thing being rewarded.

---

## The lightning talk

**Nov 13 or Nov 20. Three minutes. Separately worth 10%.** Sign-up opened in Week 11.

You present from a working notebook, not from a finished report. The report is due Nov
20, after both talk days, so you have time to act on the feedback you get.

Cover six things:

1. The question, and why you chose it
2. The sources, and how you got them
3. **The most difficult data problem you ran into, and how you solved it**
4. How you verified the result
5. What you found
6. One limitation

**Spend a third of the time on item 3.** A concrete story of finding and fixing a real
problem ("4,000 duplicate records that only appeared after an inner join, and how I
caught them") is the part an audience remembers.

**Attending both talk days is part of this grade**, and you complete a peer evaluation
for every presenter.

Delivery is scored on whether the audience understood the content, not on how polished
the performance was. Reading from notes, being nervous, and having an accent do not
affect the score. If presenting is a concern for any reason, contact me right away and
we will arrange a format that works.

---

## Before you submit: the stranger test

This test takes about ten minutes, and it is the single most useful thing you can do
before submitting.

1. Clone your repo into a **brand new folder**.
2. Make a fresh environment and install the packages your README names.
3. Follow the README exactly as written, changing nothing.
4. Run the notebook from top to bottom.

It is common for a notebook to run only because of a file that exists only on the
author's own computer, a package installed in September and forgotten, or a hard-coded
file path that contains the author's username. Finding this on Nov 18 is far better
than hearing about it after grading.

Also check:

- [ ] No API keys, tokens, or passwords committed anywhere in the repo's history
- [ ] Raw data preserved in the repo, or a script included that downloads it
- [ ] Notebook outputs are from the final run, not from a version three edits ago
- [ ] Every claim in the report can be traced to something in the notebook

---

## How this is graded

| Criterion | Wt | The short version |
|---|---|---|
| Findings & interpretation | ×2 | Supported by the data, honest about uncertainty, and separates what is known from what is suspected |
| Narrative coherence | ×2 | One argument from the question to the conclusion |
| Who is missing | ×2 | Specific exclusions, their consequences, and one question the data cannot answer |
| AI use log & reflection | ×2 | Something a model got wrong and how you caught it |
| Technical ambition *(tier-gated)* | ×2 | Demanding work, executed well |
| Repository & reproducibility | ×2 | A stranger clones the repo, follows the README, and gets the same result |
| Documentation carried forward | ×1 | Dictionary, log, and provenance **updated to the final state of the data** |

Proficient on every criterion is an 88. The A range requires judgment beyond
correctness.

**Submit a self-scored rubric** with your work.

---

## What you will have at the end

The finished project is a public repository that contains a documented, reproducible,
multi-source data pipeline, with a data dictionary, a cleaning log, a verification
suite, and an honest account of what the data cannot support. That is a **portfolio
piece**: a finished project you can show an employer as evidence of your skills. Week
14 includes ten minutes on how to present it as one, because "cleaned some data"
understates what you did, and "built a validated multi-source pipeline with documented
provenance" describes it accurately.
