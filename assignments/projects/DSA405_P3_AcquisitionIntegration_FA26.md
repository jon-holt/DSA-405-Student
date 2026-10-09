# P3: Acquisition & Integration

**DSA 405 · Fall 2026 · Project Milestone 3**

| | |
|---|---|
| **Introduced** | Week 8 (Oct 9), as A8. Built across Weeks 9–11. |
| **Due** | **Thursday, Nov 5, 11:59 PM** |
| **Weight** | 12% of course grade · scored on the P3 rubric, 5 criteria |
| **Submit** | Notebook + repo link. `DSA405_002_FA26_P3_[yourUnityID].ipynb` |
| **Also this window** | **Bench Check 2**, Weeks 10–12. This is the final Bench Check window. |
| **Time** | 6–8 hours across four weeks. The acquisition usually takes longer than students expect. |

**Revision available once.**

---

## Purpose

P3 executes the plan you wrote in **A8**. It has three parts: code that collects your web
source, a join between your two sources, and **proof that the join is correct.**

For most of you, the web source is the second source you named in P1, the one P2 did not
use. Some of you already collected your web source for P1 or P2. P3 still grades the code
that collects it, and you do not need a new source. See "If you already collected your web
source" under Deliverable 1.

The rubric's heaviest weight (×3) is on the **verification suite** rather than the
acquisition. Writing retrieval code now takes very little time. Checking whether the
result is correct still takes real time and judgment, and that checking is the skill
this milestone builds.

---

## Deliverables

Five things, in one notebook.

### 1. Acquisition code

Working code that retrieves the web or API source and saves it to `data/raw/`.

**Requirements, all of which are in the rubric:**

- [ ] Rate limited. One request per second unless the source documents otherwise.
- [ ] Honest `User-Agent` identifying the request as coursework, with contact information.
- [ ] **Cached.** Never fetch the same resource twice in one run. Save the raw response to disk
      and read from there on re-runs.
- [ ] Handles pagination, if there is any.
- [ ] Handles the problems real websites cause: timeouts, non-200 responses, and
      **selectors that match nothing** (a selector is the pattern your code uses to
      find an element in a page).
- [ ] **Fails loudly.** "Fails loudly" means the code stops with an error message instead
      of continuing and producing wrong output with no message. Raise an error, or log a
      warning, on any condition that would otherwise produce wrong output silently.

The last point must be **demonstrated**, not only claimed: show one such condition
being caught, with the output. Until you have seen the code catch one bad condition,
you cannot know that it fails loudly.

For an API source, read the rate limit **from the response headers**, not from the
documentation, and show that code in the notebook. The documentation can be out of date;
the headers state the limit that actually applies to your requests right now.

**If you already collected your web source.** Some of you collected your web source for P1
or P2, by scraping a site, by calling an API, or with `read_html`. Deliverable 1 still
applies to you, and it grades the code that collects that source. Put that code in this
notebook, and bring it up to every requirement in the list above. Most collection code
written before now has no cache, no pause between requests, and no demonstrated failure,
so expect to add those three things. A cell that only loads a file you saved earlier does
not count as acquisition code, because it does not show how the data was collected.

### 2. Ethics and legality in practice

A short section, mostly a pointer back to A8.

- Confirm the acquisition as built matches the plan written in A8.
- **Where the built version differs from the plan, document why.** We call this
  difference drift. Sources change between planning and execution, so documented drift is
  a normal part of the work. What the rubric cannot credit is drift with no explanation,
  because your reader cannot tell it apart from a mistake.
- Re-confirm: no login, no paywall, no personal data, no circumvention of any protection.

### 3. Join design

**Before writing the merge**, write down the following. The **grain** of a table is
what one row stands for: one row per restaurant, or one row per inspection.

| | |
|---|---|
| Join key(s) | |
| Grain of the left table | "one row per ___" |
| Grain of the right table | "one row per ___" |
| Relationship | one-to-one / one-to-many / many-to-one / many-to-many |
| Expected row count after the join | a number, committed to in advance |
| Join type and why | inner / left / right / outer |
| What happens to unmatched rows | and whether that is the intended outcome |

Then run the merge with `validate=` set to the relationship you claimed. A pandas error
here means your stated understanding of the data was wrong, which is exactly the mistake
the `validate` option is designed to catch. An error now is much better than a wrong analysis later,
because the error appears while there is still time to fix the join.

Two failure modes, both covered this term: a join can **add** rows that should not exist
(Week 6's fan-out) and it can **remove** rows that should remain (Week 6's wreck, the
inner join). State which one your design guards against, and how.

### 4. The verification suite

The heaviest-weighted criterion (×3), and the subject of the Bench Check 2
conversation.

**At least five assertions**, each encoding a real assumption about the data, each with
a comment stating **what it protects against**. If you cannot say what an assertion
protects against, the assertion is not doing useful work yet, and writing the comment
first is the fastest way to find that out.

Cover at least these five kinds:

| Kind | The assumption |
|---|---|
| Row count | the join did not change the number of observations |
| Key uniqueness | no identifier appears twice where it should appear once |
| Cardinality | the relationship between the tables (one-to-one, one-to-many) is what was claimed |
| Value range | every value falls inside what is possible, rather than what occurred |
| Referential integrity | every key in the left table exists in the right |

Write it as a function that returns a list of failures, so you can call it repeatedly:

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

### 5. Prove the suite works

Until a suite has caught something, you do not know that it can, so we test it the same
way Lab 7 did.

Take a copy of the joined data, **break it three different ways**, and show the suite
catching each one. A mutation is a deliberate change that makes the data wrong. The three
mutations must cause three *different* checks to fail. Print the output.

```python
mutations = {}
m1 = df.copy(); m1.loc[m1.index[0], "score"] = 9999
mutations["out-of-range value"] = m1
# ... two more

for label, mutated in mutations.items():
    print(f"{label:34} -> {verify(mutated, len(df))}")
```

Then the required final step:

**Design a mutation the suite would NOT catch.** A change that makes the data wrong
while every check still passes. Show it passing. Then write the check that would catch
it.

A verification suite is not a proof of correctness. It is a list of the specific things
someone thought to check. Knowing what yours does not check is part of the deliverable,
because the gap you've named is the one you can watch for by other means.

---

## Report one thing that surprised you

Somewhere in this milestone, a number will come out different from what you expected: a
row count, a match rate, a duplicate you did not know about, a date range that cannot be right.

**Write it down: what you expected, what appeared, and what it turned out to be.**

If nothing surprised you, there are two possibilities: either the data is unusually
clean, in which case say so and describe what you checked, or you have not yet examined
the data closely enough. The mutation exercise above is a good way to tell which of the
two is true.

---

## How this is graded

| Criterion | Wt | The short version |
|---|---|---|
| Acquisition code | ×2 | Retrieves reliably, rate-limited, cached, and fails loudly, with one demonstrated catch |
| Ethics & legality in practice | ×2 | Matches the A8 plan; drift documented |
| Join design | ×2 | Keys and cardinality stated **before** the merge; alternatives ruled out |
| **Verification suite** | **×3** | Five-plus real assertions, demonstrated catching mutated data |
| Reproducibility & readability | ×1 | Runs without errors, readable by a peer, README updated |

Standing requirements still apply: restarted-kernel run, `README.md`, raw data
untouched.

**Submit a self-scored rubric.**

---

## If a source becomes unavailable

Websites change their structure, APIs are shut down or changed, and terms of service
change. If this happens to you, it will most likely happen in October, because that is
when you are building P3.

If a source documented in A8 becomes unavailable through no fault of yours:

1. **Email me within 48 hours.**
2. Bring the evidence: the old plan, the new response, what changed.
3. We agree on a substitute or a reduced scope from there.

**Documented adaptation counts as a strength on the rubric.** Showing that an endpoint
was shut down, and finding a substitute within a week, demonstrates exactly the judgment
this course is about. The harmful choice is saying nothing: a pipeline that broke weeks
earlier and is submitted in November with no message in between, because by then there
is no time left to adapt the plan.

---

## Practical advice, in order of how much time it saves

**Cache from the first request**, not later. Save every raw response to `data/raw/` and
read from disk during development. Your parsing code will run fifty times; the site
should receive only one request for each page.

**Get one record working end to end before looping.** One page, one record, one join, one
assertion, then scale up. Debugging code inside a loop over 400 pages is slow and
frustrating. Debugging one page first is much faster.

**Write the assertion before the code it checks.** State the expected row count, then
write the merge. The reverse order produces an assertion that describes whatever
happened to come out.

**Do not scale up on the last day.** A scraper that needs 40 minutes to run will use up
40 minutes of Thursday night, plus however long it takes you to notice that page 31
failed to load.
