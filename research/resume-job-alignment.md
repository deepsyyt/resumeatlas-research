# How well do real resumes match the jobs they are sent to?

**Question.** When someone runs their resume against a specific job posting they
are considering, how aligned are the two actually? And where does the misalignment
sit — in keywords, in evidence, or in raw experience?

**Answer.** Keyword coverage is high, evidence is thin, and on a whole-application
judgement only a small minority of resume-posting pairs are ready to send as-is.

---

## Findings

<!-- GENERATED:stats-alignment -->

| Measure | Value | Sample |
| --- | --- | --- |
| Median keyword coverage vs the posting | **79%** | 1,667 |
| Median ATS score (parse/readability, 0–100) | **80** | 1,667 |
| Resumes scoring below 70 on that check | 20.3% | 1,667 |
| Median required skills missing per resume | **6** | 1,667 |
| Median skills named but not evidenced | **7** | 534 |
| Median resume years of experience | 4 | 997 |
| Median years the posting asked for | 4 | 997 |

*n = 1,667, March 2026 – September 2026.* Sub-measures carry their own sample sizes, shown above.

<!-- /GENERATED -->

### Application verdict

Each analysis produces a single judgement for that resume against that posting:
**Apply** (send it as-is), **Optimize First** (a realistic fit, but the document
undersells it), or **Skip** (not a realistic fit for this posting).

<!-- GENERATED:verdict-table -->

| Verdict | Share | Count | Median shortlist odds |
| --- | --- | --- | --- |
| **Apply** | 6.5% | 38 | 72% |
| **Optimize First** | 77.8% | 452 | 42% |
| **Skip** | 15.7% | 91 | 12% |

*n = 581, June 2026 – September 2026.* Shortlist odds are a calibrated model estimate, not an observed base rate.

<!-- /GENERATED -->

The interesting number is the middle one. The dominant failure mode in this corpus
is not "wrong candidate for the job" — that is the smallest group. It is
**a plausible candidate whose resume does not demonstrate the fit**.

---

## Method

Each row is one resume compared against one real job description that the user
supplied. The comparison produces:

- **Keyword coverage** — share of the posting's extracted requirements that appear
  anywhere in the resume
- **ATS score** — a 0–100 blended parse-and-readability score for the document
- **Missing skills** — requirements present in the posting and absent from the resume
- **Experience delta** — years of experience the resume evidences, against years
  the posting asks for
- **Verdict** and **shortlist odds** — the whole-application judgement

Verdicts and bullet-level evidence were introduced later than the core analysis,
so those cuts carry smaller sample sizes and their own windows. Each figure above
prints the `n` it was computed from; they are deliberately not pooled.

---

## Interpretation

### Keyword coverage is a solved problem; evidence is not

Median coverage against the target posting is high. If a resume is failing, in
this sample it is usually not because the words are absent. That runs against the
common framing of ATS optimisation as fundamentally a keyword-stuffing exercise —
by the time someone is checking a resume against a posting, the keywords are
largely already there.

What is missing is the second layer: whether the resume *demonstrates* the skill
it names. Read alongside the
[bullet quantification study](resume-bullet-quantification.md), where the median
resume quantifies about 5% of its bullets, a consistent picture emerges. Resumes
in this corpus are keyword-complete and evidence-poor.

### The experience gap is small

Median resume experience and median posting requirement are close. The population
running these checks is broadly applying to roles in its own range, rather than
reaching far beyond it. That is worth noting because it removes the simplest
explanation for the low "Apply" rate: these are mostly not unqualified people.

### What "Optimize First" actually means

A large majority verdict of "Optimize First" is a statement about documents, not
about candidates. It means the analyser judged the underlying fit realistic while
finding the resume's presentation of that fit inadequate for the specific posting
— typically required skills the candidate plausibly has but has not evidenced, or
achievements described without outcome.

---

## What this does not show

- **No hiring outcomes.** The verdict is a model judgement about a document, not a
  prediction validated against interview or offer data. No data in this corpus
  records what happened after the application.
- **Shortlist odds are a model estimate**, calibrated to the analyser's own
  scoring — not an empirically measured base rate.
- **Self-selected postings.** Users choose which posting to check. People may run
  checks disproportionately on jobs they are uncertain about, which would depress
  measured alignment relative to all applications they send.
- **Self-selected users.** Someone using a resume-matching tool has already
  decided their resume might need work.
- **The verdict is not a blind human judgement.** It is produced by the same
  system that produces the component scores, so the components and the verdict are
  not independent measurements.

---

## Data

- [`datasets/resume-job-analysis-2026.json`](../datasets/resume-job-analysis-2026.json) → `verdictSplit`, `medianKeywordCoverage`, `atsScoreDistribution`, `medianResumeYears`, `medianRequiredYears`
- [`datasets/resume-insights-2026.csv`](../datasets/resume-insights-2026.csv) → rows where `category` is `overview`, `verdict`, `experience` or `ats_score_distribution`

Related page: <https://resumeatlas.io/resume-insights>
