# Reading Python When You Already Speak Something Else

**DSA 405 · Week 0 · one page · for experienced coders**

A phrasebook for readers already fluent in R, SQL, or spreadsheet formulas: it maps
idioms from those languages onto the Python/`pandas` read all semester. Skim it during
Week 0; keep it open during Weeks 2–5.

*(This is deliberately the only student document in the course that names other languages.
All submissions are Python.)*

## The phrasebook

| You want to… | R (dplyr) | SQL | Excel | Python / `pandas` |
|---|---|---|---|---|
| Load a CSV | `read_csv("f.csv")` | `COPY` / import wizard | File > Open | `pd.read_csv("f.csv")` |
| Peek at it | `glimpse(df)` | `SELECT * … LIMIT 5` | scroll | `df.head()`, `df.info()` |
| Keep some rows | `filter(df, score < 90)` | `WHERE score < 90` | AutoFilter | `df[df.score < 90]` |
| Keep some columns | `select(df, name, score)` | `SELECT name, score` | hide columns | `df[["name", "score"]]` |
| New column from old | `mutate(df, z = x/y)` | `SELECT x/y AS z` | formula fill-down | `df["z"] = df.x / df.y` |
| Sort | `arrange(df, desc(score))` | `ORDER BY score DESC` | Sort dialog | `df.sort_values("score", ascending=False)` |
| Group and summarize | `group_by(city) %>% summarise(m = mean(score))` | `GROUP BY city` + `AVG(score)` | PivotTable | `df.groupby("city").score.mean()` |
| Count categories | `count(df, city)` | `GROUP BY … COUNT(*)` | COUNTIF | `df.city.value_counts()` |
| Join two tables | `left_join(a, b, by = "id")` | `LEFT JOIN … ON a.id = b.id` | VLOOKUP/XLOOKUP | `a.merge(b, on="id", how="left")` |
| Wide → long | `pivot_longer()` | — | unpivot (Power Query) | `df.melt(...)` |
| Long → wide | `pivot_wider()` | — | PivotTable | `df.pivot(...)` |
| Missing values | `NA`, `is.na(x)` | `NULL`, `IS NULL` | blank cell | `NaN` / `None`, `df.x.isna()` |
| Chain steps | `x %>% f() %>% g()` | nested subqueries | helper columns | `df.f().g()` (method chaining) |

## Six differences that cause bugs

1. **Indexing starts at 0**, and slices *exclude* their endpoint: `x[0:3]` is the first
   three items. R counts from 1 and includes both ends. This is the #1 source of
   off-by-one bugs for R speakers.
2. **`df[...]` is overloaded.** `df["score"]` is a column; `df[df.score < 90]` is rows.
   When confused, be explicit: `df.loc[rows, cols]` by label, `df.iloc[i, j]` by position.
3. **`NaN` never equals anything, including itself**, matching SQL's `NULL`.
   `df.score == np.nan` is always `False`; use `df.score.isna()`. And unlike SQL,
   `NaN` in a *grouping* column silently drops those rows from `groupby`, so count first.
4. **Assignment doesn't copy.** `b = a` makes two names for one DataFrame; mutating `b`
   mutates `a`. Use `b = a.copy()` when you mean a copy. (R's copy-on-modify prevents
   this; Python's assignment does not.)
5. **Method chaining is dplyr's pipe**, read left to right:
   `df.query("score < 90").groupby("city").score.mean()` ≈
   `df %>% filter(score < 90) %>% group_by(city) %>% summarise(mean(score))`.
6. **Vectorize as in R**: `df.score * 2` beats a `for` loop over rows. A
   `for i in range(len(df))` loop can almost always be replaced by a column operation.

## Finding the pandas name for an R/SQL idiom

Search "*pandas equivalent of* `pivot_longer`". The pandas docs include a
[comparison-with-R / comparison-with-SQL section](https://pandas.pydata.org/docs/getting_started/comparison/)
aimed at exactly this situation. If a tool performed the translation, cite it in the
AI-use note like any other assistance.
