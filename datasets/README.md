# DSA 405 — Class Datasets

We work these files together in class. **Every one of them is broken in ways you will
have to find.** That is the point.

All data here is **simulated**. No file describes a real restaurant, school, permit,
inspection, or person. You can publish anything you build on it without any privacy
or licensing concern.

| File | We use it in | What it is |
|---|---|---|
| `wolfpack_dining_raw.csv` | Weeks 2, 3, 4 | Campus dining locations with inspection scores |
| `nc_schools_dirty.xlsx` | Weeks 2, 5 | School proficiency rates, two years, as exported by an agency |
| `permits_raleigh.json` | Weeks 2, 11 | Building permits, nested, straight from a source system |
| `inspections_a.csv` | Weeks 6, 7 | Restaurant inspections, one row per inspection |
| `inspections_b.csv` | Weeks 6, 7 | Restaurant reference table |
| `restaurant_notes.txt` | Week 12 | Inspector notes written as prose |
| `inspection_report_*.pdf` | Week 12 | Three inspection reports as PDFs |

## Before you start

Read a file before you trust it. Open the raw text or the sheet with your own eyes
before you open it in `pandas`. Several of these files will load without a single
error message and hand you the wrong answer.

Three habits that will serve you all semester:

1. **Count rows before and after every operation.** Write the number down.
2. **Run `.value_counts(dropna=False)` on every column you plan to use.** Missing
   values wear disguises.
3. **When a number surprises you, stop.** The surprise is information. Chase it before
   you move on.

## A warning about `read_csv`

`pd.read_csv("file.csv")` is a decision, not a neutral act. It guesses a type for
every column, and a wrong guess is silent. At least one column in these files loses
information the instant you read it with defaults.
