# How many resume bullet points contain a measurable result?

**Question.** Career advice is close to unanimous that resume bullet points should
be quantified — "increased conversion 18%" rather than "responsible for
conversion". If that advice is followed, most bullets on most resumes should
contain a number. Do they?

**Answer.** No, and not remotely. The median resume in this sample quantifies
about one bullet in twenty.

---

## Findings

<!-- GENERATED:stats-bullets -->

| Measure | Value |
| --- | --- |
| Median bullet points per resume | **35** |
| Median share of those bullets containing a measurable result | **5.3%** |
| Resumes with no quantified bullet anywhere | **25.6%** |

*n = 616, June 2026 – September 2026.*

<!-- /GENERATED -->

The distribution is not a bell curve around a low mean. It is heavily massed at
the bottom:

<!-- GENERATED:dist-bullets -->

| Share of bullets quantified | Resumes | % of sample |
| --- | --- | --- |
| 0–10% | 397 | 64.4% |
| 10–20% | 97 | 15.7% |
| 20–30% | 50 | 8.1% |
| 30–40% | 61 | 9.9% |
| 40%+ | 11 | 1.8% |

*n = 616, June 2026 – September 2026.*

<!-- /GENERATED -->

The modal resume is not "lightly quantified". It is a document where the reader
encounters a page and a half of responsibilities before meeting a single figure —
and in a quarter of cases, never meets one at all.

---

## Method

For each analysed resume, the analyser segments the experience and project
sections into individual bullet points, then classifies each bullet on whether it
contains a **measurable result**: a number, percentage, currency amount, time
span, volume, or scale figure that describes an outcome or the size of the work.

Deliberately excluded from the count:

- Dates and durations that are part of a job header ("Jan 2023 – Present")
- Version numbers, model numbers and other identifiers ("Python 3.11", "ISO 27001")
- Team sizes appearing without any associated outcome, where the number describes
  context rather than result

The reported metric is the **share of bullets on that resume** which qualify, then
the median across resumes. Medians are used throughout rather than means, because
a handful of heavily quantified resumes drag a mean upward and misdescribe the
typical document.

See [definitions](../methodology/definitions.md#quantified-bullet) for the exact
rule, and [limitations](../methodology/limitations.md) for what this measurement
is sensitive to.

---

## Interpretation

The gap between advice and practice here is unusually wide, and the most likely
explanation is not that job seekers disagree with the advice.

Quantifying a bullet requires the writer to recall or reconstruct a figure they
may never have been told. An engineer generally knows they migrated a service;
they frequently do not know what it cost before, what it cost after, or how many
requests it served. The advice "add numbers" is cheap to give and expensive to
follow, and the cost is highest precisely for the candidates who most need the
differentiation — earlier-career applicants with less access to business metrics.

This also reframes what a resume gap usually is. A resume can name every skill a
posting asks for and still not *evidence* any of them. Keyword coverage measures
whether a term appears; quantification measures whether the claim behind the term
is supported. In this corpus those two measures diverge sharply — see
[resume–job alignment](resume-job-alignment.md), where median keyword coverage is
high while quantification stays near the floor.

---

## What this does not show

- **Nothing about hiring outcomes.** No data here records whether any resume led
  to an interview. This study cannot support "quantified resumes get more
  interviews", however plausible that claim may be.
- **Nothing about causality.** Resumes with more quantification may differ from
  the rest in seniority, function and industry. No adjustment for those has been
  made.
- **Extraction sensitivity.** Bullets are counted from extracted text. A resume
  whose bullets are rendered as images or in a layout the extractor flattens will
  report a distorted bullet count. This affects the denominator, not the classifier.
- **Sample bias.** Skews toward software, data and engineering roles, where
  quantifiable metrics are arguably *more* available than in many other fields.
  If anything, that suggests the overall picture is not better elsewhere.

---

## Data

- [`datasets/resume-job-analysis-2026.json`](../datasets/resume-job-analysis-2026.json) → `bulletEvidence`
- [`datasets/resume-insights-2026.csv`](../datasets/resume-insights-2026.csv) → rows where `category = bullet_evidence`

Related page: <https://resumeatlas.io/quantify-resume-accomplishments>
