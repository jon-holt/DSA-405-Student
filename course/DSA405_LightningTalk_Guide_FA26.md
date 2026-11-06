# Lightning Talk: What Goes on Each Slide

**DSA 405 · Fall 2026 · Nov 13 and Nov 20 · three minutes · 10% of the course grade**

You design your own slides. The layout is fixed so that every talk is the same shape:
**exactly three slides**, in this order, each saying the things listed below. The six
things every talk must cover (the same six on the peer-evaluation form) are split two to a
slide. The times add up to 2 minutes 45 seconds, which leaves 15 seconds of slack. A talk
that runs past three minutes loses points on Criterion 5 of the talk rubric.

You present from a **working notebook**, not from a finished report. The slides frame the
talk; the notebook is where you show the data problem live (see slide 2).

---

## Slide 1: the question and the sources (45 seconds)

| On the slide | What it must say |
|---|---|
| **Title** | Your question, in one plain sentence a stranger can understand. For example: *Do restaurants with more critical violations get lower inspection scores?* |
| **Why you chose it** | One sentence. |
| **Each source** | Who made it, what it covers, how you got it (downloaded, scraped, or through an API), and how many rows or records it has. One short block per source. Do not list columns. |
| **Footer** | Your name, your Unity ID, your tier (1, 2, or 3), and the repository link. |

Say the question first, before anything else. The first row of the peer-evaluation form
asks whether the audience knew what you asked within thirty seconds.

## Slide 2: the hardest data problem, and the fix (60 seconds)

| On the slide | What it must say |
|---|---|
| **Title** | What was wrong, in one sentence with a number in it. For example: *The join returned 5,800 rows instead of 1,200.* |
| **The evidence** | The output, the number, or the picture that showed you the problem. Paste it on the slide, or switch to your notebook here and show it live, then come back. The audience should see the problem, not only hear about it. |
| **The fix** | What you changed, and why that was the right change and not another one. For example: *joined on the composite key (restaurant_id, cuisine) because the second table has one row per cuisine tag.* |
| **How you verified it** | The check that would have failed if the fix were wrong, and the number it returns now. |

This slide gets a third of your time because it carries the most weight on the rubric:
Criterion 2 (the ugly problem, ×2) and Criterion 3 (the verification account, ×2). Pick the
hardest real problem you had, not the first one. "I checked it" scores Developing. "The
row-count assert now passes at 1,200" scores Proficient. Saying what would have failed if
you were wrong scores Excellent.

## Slide 3: what you found, and one limitation (60 seconds)

| On the slide | What it must say |
|---|---|
| **Title** | Your finding, as one sentence the audience could repeat afterward. For example: *Scores fall about 4 points per critical violation.* |
| **One figure or one table** | Only one. It is the largest thing on the slide. Axis labels at least 14 pt, one message per chart, no legend if there is one series, and a one-line caption. |
| **Takeaway** | Two sentences: what the data shows, and how sure you are. Say what is known and what you only suspect. |
| **One limitation** | Who or what the data leaves out, and one thing your finding cannot claim because of it. |

A limitation that would fit any project, such as "the sample could be bigger," scores
Developing. Name the specific people, places, or cases that are missing.

---

## Rules for all three slides

- **Three slides, no more.** No title slide, no "questions?" slide, no appendix. Your notebook is the fourth thing on screen, if you need it.
- **One line per title.** A title that wraps to two lines is too long for the back of the room.
- **Readable from the back of the room.** Body text 18 pt or larger. Any design, any colors, as long as the text can be read from the last row.
- **Rehearse once with a timer.** Most people run long on slide 2 the first time. That is normal; the fix is to cut words from slide 1, not to talk faster.
- **Bring the notebook open** in a second window, restarted and run from the top, so that switching to it on slide 2 takes two seconds.

## How this is graded

| Talk rubric criterion | Weight | Which slide shows it |
|---|---|---|
| 1. Question, sources, and findings | ×2 | Slides 1 and 3 |
| 2. The ugly problem | ×2 | Slide 2 |
| 3. Verification account | ×2 | Slide 2, the last line |
| 4. Limitations | ×1 | Slide 3 |
| 5. Comprehensibility and time | ×1 | All three: within three minutes, readable, and the audience can restate the main point |
| 6. Peer feedback | ×2 | Not your slides: the forms you fill out for the other presenters |

Delivery is scored on whether the audience understood the content, not on how polished the
performance was. Reading from notes, being nervous, and having an accent do not affect the
score. If presenting is a concern for any reason, contact me right away and we will arrange
a format that works.
