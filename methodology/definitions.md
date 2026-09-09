# Definitions

Every measured term, stated precisely. Where a term has a common informal meaning
that differs from the one used here, the difference is called out.

---

## Analysis

One resume compared against one job description. The unit of observation for the
main corpus. A single user running three different postings produces three
analyses; the data is not de-duplicated by user.

---

## ATS score

A blended 0–100 score describing how cleanly a resume can be read as a structured
document. It measures **parseability and readability, not job fit** — a resume can
score 95 and be entirely wrong for the posting.

Bands used throughout:

| Band | Meaning |
| --- | --- |
| Below 70 | Parsing or formatting problems serious enough to risk losing content before a human reads it |
| 70–84 | Readable, but losing points on layout or structure |
| 85 and above | Clean |

Two different scores appear in this repository and must not be conflated:

- The **analyser score** in the parsing benchmark — produced by the rule-based
  parsing analyser on extracted text.
- The **blended score** in the main corpus — produced by the analysis model as
  part of a full resume-vs-posting evaluation.

They are reported separately, on separate samples and windows.

---

## Keyword coverage

The share of requirements extracted from the job description that appear anywhere
in the resume text.

Coverage is a **presence** measure. A term counts as covered if it appears — the
measure says nothing about whether the resume demonstrates the skill. This is
deliberate, and the contrast between coverage and evidence is one of the findings
in the [alignment study](../research/resume-job-alignment.md).

---

## Missing skill

A requirement stated in the job description and **absent from the resume**.

"Absent" means it does not appear in the resume text, under its canonical name or
a known alias. It does not mean the candidate lacks the skill — only that the
document does not claim it.

---

## Weak skill

A skill the resume **names but does not evidence**: it appears in a skills
section or summary, but no experience or project bullet demonstrates its use.

This is distinct from a missing skill and is measured separately. A resume can
have high keyword coverage and a large number of weak skills simultaneously.

---

## Required vs preferred

Job descriptions typically distinguish must-haves from nice-to-haves. Each
extracted requirement is classified as **required** or **preferred** based on how
the posting frames it ("must have", "required", "X+ years of" versus "preferred",
"nice to have", "bonus").

The classification is of the *posting's framing*, not of the requirement's actual
importance to the employer.

---

## Quantified bullet

A resume bullet point containing a **measurable result**: a number, percentage,
currency amount, time span, volume or scale figure describing an outcome or the
size of the work.

Explicitly **not** counted:

- Dates and durations in job headers ("Jan 2023 – Present")
- Version and model numbers ("Python 3.11", "ISO 27001")
- Team sizes with no associated outcome, where the figure is context rather than result

The reported metric is the share of a resume's bullets that qualify, then the
median of that share across resumes.

---

## Application verdict

A single judgement for one resume against one posting:

| Verdict | Meaning |
| --- | --- |
| **Apply** | Ready to send as-is for this posting |
| **Optimize First** | A realistic fit, but the resume does not currently demonstrate it |
| **Skip** | Not a realistic fit for this posting |

The verdict is a **model judgement about a document**. It is not validated against
hiring outcomes, because no hiring-outcome data exists in this corpus.

---

## Shortlist odds

A model estimate of the likelihood of reaching a shortlist, reported as a current
percentage, a projected percentage after recommended fixes, and the uplift between
them.

**This is a calibrated model output, not an empirically measured base rate.** No
observed shortlist data underlies it.

---

## Parse check

One of twelve independent checks in the parsing benchmark, each returning:

| Result | Meaning |
| --- | --- |
| **Pass** | Element extracted cleanly |
| **Warn** | Extracted, but with ambiguity |
| **Fail** | Could not be reliably recovered |

"Flagged rate" is warn plus fail — the share of resumes where the check did not
come back clean.

---

## Confounded check

A parse check whose result is distorted by the measurement pipeline rather than by
the resume. These are marked in the data and excluded from interpretation.

The current example is bullet structure: text extraction normalises or strips
bullet glyphs, so a low bullet-marker count reflects the extractor, not the
document.

---

## Window

The date range a figure covers. Different signals were introduced at different
times, so different studies carry different windows. Figures from different
windows are reported separately and never pooled.
