# P3: Acquisition & Integration

**DSA 405 · Fall 2026 · Project Milestone 3**

| | |
|---|---|
| **Introduced** | Week 8 (Oct 9), as A8. Built across Weeks 9–11. |
| **Due** | **Thursday, Nov 5, 11:59 PM** |
| **Weight** | 12% of course grade |
| **Submit** | Notebook + repo link. `DSA405_002_FA26_P3_[yourUnityID].ipynb` |
| **Time** | 6–8 hours across four weeks. |

**Revision available once.**

---

## Purpose

P3 executes the plan you wrote in **A8**. It has three parts: code that collects your web
source, a join between your two sources, and **proof that the join is correct.**

For most of you, the web source is the second source you named in P1, the one P2 did not
use. Some of you already collected your web source for P1 or P2. P3 still grades the code
that collects it, and you do not need a new source. See "If you already collected your web
source" under Deliverable 1.

---

## Deliverables

### 1. Acquisition code

Working code that retrieves the web or API source and saves it to `data/raw/`.

**Requirements, all of which are in the rubric:**

- [ ] Rate limited. One request per second unless the source documents otherwise.
- [ ] Honest `User-Agent` identifying the request as coursework
- [ ] **Cached.** Never fetch the same resource twice in one run. Save the raw response to disk
      and read from there on re-runs.
- [ ] Handles pagination, if there is any.
- [ ] Handles the problems real websites cause: timeouts, non-200 responses, and
      **selectors that match nothing** (a selector is the pattern your code uses to
      find an element in a page).
- [ ] **Fails loudly.** "Fails loudly" means the code stops with an error message instead
      of continuing and producing wrong output with no message. Raise an error, or log a
      warning, on any condition that would otherwise produce wrong output silently.

The last point must be **demonstrated**: show one failure and prove that your code caught the failure ("failed loudly"). 

For an API source, read the rate limit **from the response headers**, not from the
documentation, and show that code in the notebook. The documentation can be out of date, but the headers state the limit that actually applies to your requests right now.

**If you already collected your web source.** Some of you collected your web source for P1
or P2, by scraping a site, by calling an API, or with `read_html`. In this case, copy that code into this
notebook, and modify it so that it satisfies requirements listed above.

### 2. Ethics and legality in practice

- Confirm that your data acquisition (scraping) matches the plan written in A8.
- **Where the final version differs from the plan, document why.** We call this
  difference *drift*. Drift is very common in real life. If your plan drifted, explain how it changed and why. 
- Re-confirm the legal and ethical guardrails: no login, no paywall, no personal data, no circumvention of any protection.

### 3. Join design

**Before writing the merge**, write down the following. The **grain** of a table is
what one row stands for: one row per restaurant, or one row per inspection.

| | |
|---|---|
| Join key(s) | |
| Grain of the left table | "one row per ___" |
| Grain of the right table | "one row per ___" |
| Relationship | one-to-one / one-to-many / many-to-one / many-to-many |
| Expected row count after the join | a number |
| Join type and why | inner / left / right / outer |
| What happens to unmatched rows | discarded? NA? Repeated? Other? |

Then run the merge with `validate=` set to the relationship you expect. A pandas error
here means your stated understanding of the data was wrong, which is exactly the mistake
the `validate` option is designed to catch.

There are two common failures that we discussed in class: a join can **add** rows that should not exist
(Week 6's fan-out) and it can **remove** rows that should remain (Week 6's wreck, the
inner join). Which of these two failures does your code guard against?

### 4. The verification suite

**At least three assertions**, each checking a real assumption about the data, each with
a comment stating **what it protects against**. 

Here are some common types of assertions

| Kind | The assumption |
|---|---|
| Row count | the join did not change the number of observations |
| Key uniqueness | no identifier appears twice where it should appear once |
| Cardinality | the relationship between the tables (one-to-one, one-to-many) is what was claimed |
| Value range | every value falls inside what is possible |
| Referential integrity | every key in the left table exists in the right |

**Optional**: Write it as a *function* that returns a list of failures, so you can call it repeatedly:

```python
def verify(df, n_expected):
    """Each check states an assumption about the data. If an assumption stops being true, this function reports it."""
    fails = []
    # protects against: a fan-out join silently multiplying rows
    if len(df) != n_expected:
        fails.append(f"row count {len(df)} != expected {n_expected}")
    # ... at least four more
    return fails
```

---

## Report one thing that surprised you

Over the course of this exercise, did you learn something new about your data? Was there a row count, a match rate, a duplicate you did not know about? A date range that cannot be right?

Write down one thing you learned or one thing that surprised you. If nothing surprised you, described what you checked. 

---

## How this is graded

| Criterion | Wt | The short version |
|---|---|---|
| Acquisition code | ×2 | Retrieves reliably, rate-limited, cached, and fails loudly, with one demonstrated catch |
| Ethics & legality in practice | ×2 | Matches the A8 plan; drift documented |
| Join design | ×2 | Keys and cardinality stated **before** the merge; alternatives ruled out |
| **Verification suite** | **×3** | three or more assertions |
| Reproducibility & readability | ×1 | Runs without errors, readable by a peer, README updated |

Standing requirements still apply: restarted-kernel run, `README.md`, raw data
untouched.

**Submit a self-scored rubric.**

---

