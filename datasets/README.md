# DSA 405: Class Datasets

Course datasets, used in class in the weeks listed below. Every file contains planted
defects that the coursework requires finding.

All data is **simulated**. No file describes a real restaurant, school, permit,
inspection, or person. Anything built on these files can be published without privacy
or licensing concern.

| File | Used in | Contents |
|---|---|---|
| `wolfpack_dining_raw.csv` | Weeks 2, 3, 4 | Campus dining locations with inspection scores |
| `nc_schools_dirty.xlsx` | Weeks 2, 5 | School proficiency rates, two years, as exported by an agency |
| `permits_raleigh.json` | Weeks 2, 11 | Building permits, nested, straight from a source system |
| `inspections_a.csv` | Weeks 6, 7 | Restaurant inspections, one row per inspection |
| `inspections_b.csv` | Weeks 6, 7 | Restaurant reference table |
| `restaurant_notes.txt` | Week 12 | Inspector notes written as prose |
| `inspection_report_*.pdf` | Week 12 | Three inspection reports as PDFs |

## Before starting

Inspect a file before trusting it. Open the raw text or the sheet directly before
opening it in `pandas`. Several of these files load without a single error message and
still return wrong answers.

Three standing habits:

1. **Count rows before and after every operation.** Write the number down.
2. **Run `.value_counts(dropna=False)` on every column that will be used.** Missing
   values appear under several encodings.
3. **Stop at any surprising number.** The surprise is information; investigate it
   before moving on.

## `read_csv` defaults

`pd.read_csv("file.csv")` guesses a type for every column, and a wrong guess is silent.
At least one column in these files loses information the instant it is read with
defaults.
