# DSA 405: Project Rubrics & Checklists
### P1–P4, Bench Checks, Lightning Talk — Fall 2026

> Published to you in Week 1. You know what you are measured on before you write a line of code. Nothing here is a surprise.

---

## How Scoring Works

Every criterion is scored on one four-level scale:

| Level | What it means |
|---|---|
| **4 — Excellent** | Correct, complete, and shows judgment about *why* this choice and not the alternatives |
| **3 — Proficient** | Correct and complete |
| **2 — Developing** | Attempted, but incomplete or partly wrong |
| **1 — Limited** | Missing, or present but unusable |

Criteria carry weights of ×1, ×2, or ×3 depending on how much they matter. Your milestone score is the **weighted mean** of your criterion scores, converted with this table:

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

Read that carefully: **Proficient on everything earns an 88, a B+.** Correct and complete work is good work and is graded as such. Reaching the A range requires showing judgment, not just correctness. That is the standard for a 400-level course.

| Milestone | Criteria | Weight in course grade |
|---|---|---|
| P1 — Framing a data problem | 4 | 5% |
| P2 — Audit, cleaning log, Provenance Brief | 5 | 10% |
| P3 — Acquisition & integration | 5 | 12% |
| P4 — Synthesis | 7 | 18% |
| Lightning talk & peer feedback | 6 | 10% |
| **Project total** | | **55%** |

Remaining 45%: in-class activities and participation 15%, Labs take-home half A1–A9 30%.

### What P4 Does and Does Not Re-Score

P2 and P3 grade your dictionary, cleaning log, join, and verification. **P4 does not grade those again.** P4 asks whether the whole thing holds together as one argument, what you found, who your data leaves out, and whether a stranger can reproduce it. One P4 row checks that your earlier documentation was *updated* to match the final state. Do not expect a strong P2 to carry your P4.

### The Tier Gate

Declare a tier at P1. You may raise it up to P3; you may not lower it after P3. Tier affects exactly one row, **P4 Criterion 5 (Technical Ambition)**:

| Tier | Ceiling on Criterion 5 |
|---|---|
| **1 — Solid** | 3 (Proficient) |
| **2 — Ambitious** | 4 (Excellent) |
| **3 — Stretch** | 4 (Excellent) |

Every other row on every rubric is tier-blind. Tier 1 executed with real care scores 3s and 4s across the other six P4 rows and lands in the A-minus range honestly. It is a respectable choice and I will help you make it well.

**Stretch bonus: +2 percentage points on your final course grade, capped at 100.** Available to **any** student, at any declared tier, who adds a stretch component that is present, working, **and verified**: a schema-validated extraction you actually checked, or a many-to-many resolution with cardinality tested before and after. Attempted-but-unverified earns nothing.

### If Your Source Breaks

Sites restructure. APIs deprecate. Terms change. In a course like this it will happen to someone, probably in October.

If a source you documented in P1 becomes unavailable through no fault of yours, **notify me within 48 hours** and bring the evidence: the old plan, the new response, what changed. Documented adaptation is scored as a strength, not a penalty. Silently submitting a broken pipeline in November is not.

### Self-Assessment

Score yourself on the rubric and submit it with each milestone. One sentence per row where you scored below 4, naming what you would fix with another week.

Ungraded, ten minutes. It catches your own omissions before I do and turns my feedback into a reply rather than a verdict.

### Revision

**P1, P2, and P3 may each be revised once**, within one week of feedback, with a note on what changed. The revised score replaces the original, capped at 3 on any criterion that first scored 1. No revision on P4 or the talk; the term ends.

Each milestone feeds the next. A student carrying an uncorrected P2 into P3 is building on a broken foundation, and no grade fixes that.

---

## P1 — Framing a Data Problem
**Due Thursday, Sep 3, 11:59 PM · 5% · Weighted mean of 4 criteria**

| # | Criterion | Wt | 4 — Excellent | 3 — Proficient | 2 — Developing | 1 — Limited |
|---|---|---|---|---|---|---|
| 1 | **Question & motivation** | ×1 | Specific, answerable question with a stated reason it matters to someone besides the grader, and what an answer would change. | Clear, answerable question with a plausible motivation. | Question vague, or unanswerable with the stated data. | A topic named in place of a question. |
| 2 | **Sources & access evidence** | ×2 | Two or more sources named precisely (publisher, URL, coverage, time span, approximate size), at least one off the web. Shows evidence each is reachable: a status code, a row count, a screenshot. Names the likeliest failure point. | Two sources named specifically, at least one off the web, with a plausible stated access path for each. | Sources named vaguely, or the web requirement is unmet, or access is asserted without evidence. | Fewer than two sources, or no access plan that could work. |
| 3 | **Applicable constraints & guardrails** | ×2 | Identifies the constraints that actually apply to each source and cites them: robots.txt directives and terms for anything scraped, license and attribution terms for downloads and APIs. Certifies the project against every course guardrail with reasoning. | Identifies and checks the applicable constraints for each source and certifies against the guardrails. | Constraint check is partial or generic, or cites nothing specific. | No check performed, or the plan violates a guardrail. |
| 4 | **Tier declaration & fit** | ×1 | Declares a tier justified against current skill and the work these sources will demand. Names what would make them raise it. | Declares a tier matching the described project. | Tier declared but mismatched to the project. | No tier declared. |

### P1 Student Checklist
- [ ] One sentence stating my question, answerable with my data
- [ ] Two or more sources, each with publisher, URL, coverage, and size
- [ ] At least one source comes off the web (scrape or API)
- [ ] Evidence each source is reachable, pasted in
- [ ] The constraint that applies to each source, quoted
- [ ] Every course guardrail addressed by name
- [ ] Tier declared, with one sentence on why
- [ ] Self-scored rubric attached

---

## P2 — Audit, Cleaning Log & Provenance Brief
**Due Thursday, Oct 1, 11:59 PM · 10% · Bench Check 1 window: Weeks 5–7**

| # | Criterion | Wt | 4 — Excellent | 3 — Proficient | 2 — Developing | 1 — Limited |
|---|---|---|---|---|---|---|
| 1 | **Diagnosis & data dictionary** | ×2 | Ran a systematic audit and can show it: per-column type, range, missingness rate, and distinct-value review. Every problem found is quantified. Dictionary documents all variables with type, units, factor levels, and flags any variable whose observed values contradict its documentation. **Also states which classes of defect were checked for and not found.** | Documented at least five variables with type, units, and factor levels, and reported the problems found with counts. | Fewer than five variables documented, or problems reported without counts, or the audit was not systematic. | No dictionary, or a bare column list. |
| 2 | **Cleaning execution** | ×2 | Cleaning is correct and proportionate. Where several approaches were defensible, states the alternatives and why this one. Nothing dropped that could have been repaired. | Cleaning is correct and addresses the problems found. | Cleaning is partial, or introduces new problems such as silent coercion or unintended row loss. | Data not meaningfully cleaned, or cleaning broke it. |
| 3 | **Cleaning log** | ×3 | Every decision logged with what changed, how many rows or cells it touched, and why. Records the judgment calls, not just the operations. A reader could reverse any single decision. | Every decision logged with a stated reason. | Operations listed without reasons, or decisions visible in the code are absent from the log. | No log, or a log that contradicts the code. |
| 4 | **Provenance Brief** (≤200 words) | ×1 | A non-specialist could read it and correctly describe what the data is, who made it, why, and what it can support. No jargon smuggled in. | Clearly states source, producer, purpose, and contents. | Explains the data but assumes technical knowledge, or omits producer or purpose. | Missing, over length, or unintelligible to a non-specialist. |
| 5 | **Tidy structure & reproducibility** | ×2 | Result satisfies tidy principles and the student can name which rule the raw layout violated. Notebook runs top to bottom on a clean kernel. README states provenance; `requirements.txt` complete and pinned; raw data preserved unmodified. | Result is tidy. Notebook runs top to bottom. README and `requirements.txt` present and adequate. | Partially reshaped, or runs only with manual intervention, or documentation files are thin. | Not tidy, does not run, or files missing. |

### P2 Student Checklist
- [ ] Systematic audit output included, not just prose about it
- [ ] Every variable in the dictionary has type, units, and levels
- [ ] I listed defect types I checked for and did **not** find
- [ ] Every problem I report has a count attached
- [ ] Cleaning log has a reason on every line, not just an operation
- [ ] Row and column counts before and after cleaning
- [ ] Provenance Brief under 200 words, no jargon
- [ ] Notebook restarted and run top to bottom, clean
- [ ] `README.md` and `requirements.txt` present; raw data untouched
- [ ] Bench Check scheduled
- [ ] Self-scored rubric attached

---

## P3 — Acquisition & Integration
**Due Thursday, Nov 5, 11:59 PM · 12% · Bench Check 2 window: Weeks 10–12**

| # | Criterion | Wt | 4 — Excellent | 3 — Proficient | 2 — Developing | 1 — Limited |
|---|---|---|---|---|---|---|
| 1 | **Acquisition code** | ×2 | Retrieves reliably and handles the real world: pagination, timeouts, non-200 responses, empty selector matches. Rate-limited, honest user-agent, cached so no resource is fetched twice. Raises or logs on any condition that would otherwise produce silently wrong output, and demonstrates one such condition being caught. | Retrieves the intended data correctly, with rate limiting and caching, and includes checks that would surface an empty or malformed response. | Retrieves some data but fails on pagination, or lacks rate limiting, or has a bare `except` that swallows errors. | Does not retrieve the data, or data obtained by hand and presented as code. |
| 2 | **Ethics & legality in practice** | ×2 | Acquisition matches the P1 plan and every guardrail. Where terms or robots.txt forced a change of approach, documents it. No personal data, no authenticated access. | Complies with guardrails and terms. | Complies but cannot demonstrate it, or drifted from the P1 plan without documenting why. | Violates a guardrail, scrapes behind a login, or collects personal data. |
| 3 | **Join design** | ×2 | Correct join type, with keys and expected cardinality stated **before** the merge. Explains why the alternatives were wrong here. Unmatched rows handled deliberately. | Correct join type; keys identified; unmatched rows handled. | Join runs but the type is wrong for the relationship, or keys were not examined first. | No join, or a join producing data the student cannot explain. |
| 4 | **Verification suite** | ×3 | At least **five** assertions encoding real assumptions: row counts, key uniqueness, cardinality, value ranges, no unexpected nulls. **Demonstrates the suite catching a defect on a deliberately mutated copy of their own data**, with the failure output shown. Explains what each assertion protects against. | At least five working assertions covering row counts, key uniqueness, and cardinality, with a demonstrated catch on mutated data. | Fewer than five assertions, or assertions present but never demonstrated catching anything. | No verification, or "the result looked right." |
| 5 | **Reproducibility & readability** | ×1 | Runs clean end to end. Readable by a peer without narration: named steps, no magic numbers, comments explaining intent. README updated with new sources. | Runs clean, readable, README updated. | Runs with intervention, or code is hard to follow. | Does not run, or the pipeline is absent. |

### P3 Student Checklist
- [ ] Acquisition code runs from scratch on a clean cache
- [ ] Rate limiting present; user-agent identifies me honestly
- [ ] At least one deliberate failure demonstrated being caught
- [ ] Keys and expected cardinality written down **before** my merge
- [ ] Row counts before and after the join
- [ ] Five or more assertions, each with a comment saying what it protects
- [ ] I mutated a copy of my own data and showed my suite catching it
- [ ] Acquisition matches my P1 plan, or the drift is documented
- [ ] README updated
- [ ] Bench Check scheduled
- [ ] Self-scored rubric attached

---

## P4 — Synthesis
**Due Friday, Nov 20, 11:59 PM · 18%**

P4 assesses the whole, not a re-audit of P2 and P3.

| # | Criterion | Wt | 4 — Excellent | 3 — Proficient | 2 — Developing | 1 — Limited |
|---|---|---|---|---|---|---|
| 1 | **Findings & interpretation** | ×2 | Findings supported, appropriately hedged, interpreted in context. Distinguishes what the data shows from what the student suspects. | Findings clearly presented and interpreted. | Findings stated with little interpretation, or claims outrunning the evidence. | Findings unclear, unsupported, or absent. |
| 2 | **Narrative coherence** | ×2 | Reads as one argument from question to conclusion. A reader can reconstruct the path from raw data to finding without opening the notebook. Shows how the question was reshaped by what the data turned out to be. | Sections connect; a reader can follow how the data became the finding. | A collection of sections that do not reference each other. | Disconnected fragments; no through-line. |
| 3 | **Who is missing** | ×2 | Names specific people, places, or cases the data excludes and traces the consequence for the conclusions. Identifies at least one question this data cannot answer no matter how well it is cleaned. | Identifies real exclusions and limitations, with some consequence stated. | Generic caveats such as "the sample could be bigger." | No discussion of limits or exclusions. |
| 4 | **AI use log & reflection** | ×2 | Specific account of tools, tasks, and outputs. Reports at least one thing a model got wrong, how it was caught, and what that changed about how they now use these tools. | Discloses tools and tasks, and notes how output was verified. | Vague disclosure such as "used ChatGPT for help." | No disclosure, or a disclosure the work contradicts. |
| 5 | **Technical ambition** *(tier-gated)* | ×2 | **Tier 2–3 only.** The acquisition or integration work is genuinely demanding and executed well: robust multi-page scraping, a validated extraction, or a resolved many-to-many relationship. | Meets the declared tier's requirements competently. **Ceiling for Tier 1.** | Falls short of the declared tier, or the demanding component does not work. | No meaningful acquisition or integration work. |
| 6 | **Repository & reproducibility** | ×2 | A stranger clones the repo, follows the README, and reproduces the result. No credentials committed. Raw data preserved or its retrieval scripted. | Repo runnable with README and `requirements.txt`. | Repo present; a stranger could not reproduce it without asking questions. | No repo, or it does not run. |
| 7 | **Documentation carried forward** | ×1 | Dictionary, cleaning log, and provenance all present and **updated to the final state of the data**, including anything that changed after P3. | Present and consistent with the final data. | Present but stale relative to the final data. | Missing. |

### P4 Student Checklist
- [ ] All nine report headings present (see syllabus)
- [ ] Report readable start to finish as one argument
- [ ] Every claim traceable to something in the notebook
- [ ] Named specific groups or cases my data excludes
- [ ] Named one question my data cannot answer at all
- [ ] AI log includes something a model got wrong and how I caught it
- [ ] Dictionary and cleaning log updated to final state
- [ ] Cloned my own repo into a fresh folder and ran it from the README
- [ ] No API keys or credentials in the repo
- [ ] Self-scored rubric attached

---

## Bench Checks
**Two windows: Weeks 5–7 and Weeks 10–12. Three minutes each, during Explore.**

Sign up for one slot per window; four to six slots run per session while everyone else works
the Lab. Office hours if no slot fits.

You choose one code block from your own project and walk me through it. I ask what it does and why.

| Outcome | What it means | What happens |
|---|---|---|
| **Pass** | You explained your own code, including why you made a choice. | Nothing further. |
| **Revise** | You could not explain a block you submitted. | Return within one week having either learned it or replaced it. No grade penalty on the first pass. |
| **Not attempted** | No slot taken anywhere in the three-week window, and none arranged in office hours. | Zero on that week's in-class credit, and the corresponding milestone is capped at Proficient on every criterion. |

Bench Checks are how the AI policy in this course is actually enforced. They are also how I find students who are quietly drowning at the two moments when finding them still helps. Bring something you are unsure about; that is a better use of three minutes than showing me something easy.

---

## Lightning Talk & Peer Feedback
**Weeks 13–14 (Nov 13 & 20) · 10%**

Three minutes. Attendance both days is required and part of this grade.

| # | Criterion | Wt | 4 — Excellent | 3 — Proficient | 2 — Developing | 1 — Limited |
|---|---|---|---|---|---|---|
| 1 | **Question, sources & findings** | ×2 | Audience knows within thirty seconds what was asked and where the data came from, and leaves knowing what was found. | States question, sources, and findings clearly. | Slow to become clear, or one of the three is vague. | Audience cannot tell what was asked or found. |
| 2 | **The ugly problem** | ×2 | Picks a genuinely hard problem, shows the evidence of it, and walks the room through the fix well enough that they could do it themselves. | Describes a real problem and how it was solved. | Names a problem without showing it, or picks a trivial one. | No problem discussed. |
| 3 | **Verification account** | ×2 | Explains how they knew the result was right, including what they checked that could have proved them wrong. | States what was verified and how. | Asserts correctness without saying how they know. | No verification mentioned. |
| 4 | **Limitations** | ×1 | Names a specific limitation or exclusion and what it costs the conclusion. | Names a real limitation. | Generic caveat. | None offered. |
| 5 | **Comprehensibility & time** | ×1 | Finishes within three minutes. Visuals legible from the back. The audience can restate the main point afterward. | Close to time, legible visuals, main point lands. | Runs long, or visuals unreadable, or the main point does not land. | Substantially over time, or the talk cannot be followed. |
| 6 | **Peer feedback** | ×2 | Every assigned presenter gets one substantive question and one constructive suggestion engaging with *their* specific project. Supportive and useful. | A question and a comment for each assigned presenter, relevant and respectful. | Incomplete, or generic enough to apply to anyone. | Little or none; or dismissive. |

**On Criterion 5:** this measures whether your audience understood you, not how you performed. Reading from notes is fine. Nervousness is fine. An accent is fine. Slides in a language you think in and then translate are fine. If you have a concern about presenting, talk to me by Week 11 and we will find a format that works.

**On Criterion 2:** the ugly-problem slide is the one people remember and the one that gets you hired. "The time I found 4,000 duplicate inspection records hiding behind an inner join" is an interview answer. "I made a chart" is not. Spend a third of your three minutes here.
