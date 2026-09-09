# What breaks when a resume is read as a machine-readable document?

**Question.** Before any judgement about fit, a resume has to survive being turned
into structured text. Which parts of a real resume actually fail that step?

**Answer.** Contact details survive well. Structure does not. The failures cluster
in section headings, skills blocks and multi-column layouts — not in the fonts and
file formats that most resume advice focuses on.

> **Scope warning, stated up front.** This benchmark tested **one** analyser — the
> ResumeAtlas parser, which models the text-extraction stage that commercial
> systems share. It did **not** test Workday, Greenhouse, Lever, iCIMS, Taleo, SAP
> or any other named ATS. Read it as a directional study of machine-readability,
> not as a measurement of any vendor's product.

---

## Findings

<!-- GENERATED:benchmark-headline -->

| Measure | Value |
| --- | --- |
| Resumes tested | **138** |
| Submissions seen | 198 |
| Median analyser score (0–100) | **83** |
| Scoring below 70 | 18.8% |
| Recognised all three core sections | **55.1%** |

*n = 138, June 2026 – September 2026.* Snapshot 2026-09-04.

> These are resumes real people submitted to ResumeAtlas between the dates above, run through ResumeAtlas's own ATS-parse analyzer. The sample is small, skews toward software, data and engineering roles, and covers signed-in users only. Treat it as a directional ResumeAtlas study, not a definitive measure of every resume or every ATS.

<!-- /GENERATED -->

### Per-check results

Each resume is run through twelve independent checks. **Pass** means the element
was extracted cleanly, **warn** means it was extracted with ambiguity, **fail**
means it could not be reliably recovered.

<!-- GENERATED:parse-checks -->

| Check | Pass | Warn | Fail | Fails when |
| --- | --- | --- | --- | --- |
| Tables & columns | 54.3% | 23.2% | 22.5% | Two-column layouts and tables for core content |
| Bullet structure ⚠️ | 54.3% | 4.3% | 41.3% | **Confounded — excluded from interpretation.** Dense paragraphs with no bullet markers |
| Section detection | 55.1% | 26.8% | 18.1% | Creative headings like “My Journey” or “Toolbox” |
| Skills | 67.4% | 6.5% | 26.1% | Skill grids, rating bars, or column layouts |
| Education | 70.3% | 29.7% | 0% | Degrees buried in prose or unlabeled sections |
| Work experience | 72.5% | 16.7% | 10.9% | Roles merged or missing title/date pairing |
| Icons & graphics | 74.6% | 8.7% | 16.7% | Contact icons, emoji, and decorative glyphs |
| Dates | 89.1% | 3.6% | 7.2% | Mixed styles, “’21-’23”, or dates in graphics |
| Name | 90.6% | 0% | 9.4% | Name inside a header band, logo, or image |
| Headers & footers | 90.6% | 9.4% | 0% | Name/email/phone trapped in header or footer bands |
| Phone | 92% | 8% | 0% | Number split across table cells or stylized |
| Email | 93.5% | 0% | 6.5% | Email shown only as an icon or in a graphic |

Sorted worst-performing first. *n = 138, June 2026 – September 2026.*

<!-- /GENERATED -->

### Field extraction

<!-- GENERATED:field-extraction -->

| Field | Absent from parsed output |
| --- | --- |
| Name | 9.4% |
| Email | 6.5% |
| Phone | 8% |
| Location | 43.5% |
| LinkedIn | 58% |

*n = 138, June 2026 – September 2026.* “Absent” cannot be distinguished from “never present in the resume”.

<!-- /GENERATED -->

### Section recognition

<!-- GENERATED:sections -->

| Core sections recognised | Share of resumes |
| --- | --- |
| All three | **55.1%** |
| Two | 26.8% |
| One or none | 18.1% |

*n = 138, June 2026 – September 2026.*

<!-- /GENERATED -->

---

## Method

Every distinct resume whose extracted text was stored was run through the
production parsing analyser — the same code path that serves the public ATS
checker, not a research reimplementation. Each of the twelve checks returns
pass, warn or fail independently.

An important property of the input: the analyser runs on **already-extracted
text**, downstream of PDF and DOCX extraction. That means these results measure
what survives the *whole* pipeline, which is the right unit for the question
"will a machine read my resume" — but it also means some signals measure the
extractor rather than the document.

One check is explicitly confounded by this and is excluded from interpretation:

<!-- GENERATED:confounded -->

- **Bullet structure** — text extraction normalises or strips bullet glyphs, so this measures the extractor rather than the resume.

<!-- /GENERATED -->

The blended 0–100 score from the larger resume-vs-posting corpus is reported
alongside for context, on a much bigger sample and a different window. The two
should not be pooled.

---

## Interpretation

**Contact details are mostly fine.** Name, email and phone extract cleanly in the
large majority of resumes. The classic warning about contact information being
lost in a header band is real but uncommon in this sample.

**Structure is where resumes fail.** Section detection, skills blocks and
table/column layouts are the weakest checks by a wide margin. The failure mode is
consistent: a resume that a human reads instantly as having an experience section
is not necessarily one a parser can segment, because the segmentation depends on
recognisable headings and a linear reading order.

**Creative headings are expensive.** "My Journey" instead of "Experience", or
"Toolbox" instead of "Skills", costs nothing in human readability and a great deal
in machine readability. This is close to a free fix and one of the more actionable
findings in this repository.

**Skills grids defeat extraction.** Rating bars, star ratings and multi-column
skill matrices are a common design choice and among the worst-performing elements.
The information is visible to a human and structurally unavailable to a parser.

**LinkedIn and location are frequently absent** — but note the ambiguity: the
analyser cannot distinguish "present but unextractable" from "the candidate did
not include it". Read those two rows as *missing from the parsed output*, not as
*failed to parse*.

---

## What this does not show

<!-- GENERATED:not-measured -->

- PDF vs DOCX parse rates — the source file type is not stored, so the analyzer ran on extracted text only.
- Page-count effects — not stored.
- Bullet structure — text extraction normalises or strips bullet glyphs, so a low bullet count here is an extraction artefact, not the resume.
- Any specific commercial ATS (Workday, Greenhouse, Lever, iCIMS, Taleo, SAP). This benchmark tested the ResumeAtlas analyzer, which models the shared text-extraction stage — not any one vendor's parser.
- Hiring outcomes — nothing here records whether a resume led to an interview.

<!-- /GENERATED -->

Additional limits:

- **Small sample.** Substantially smaller than the resume-vs-posting corpus, and
  drawn from signed-in users only. Treat per-check rates as directional.
- **One analyser.** Pass rates would differ on a different parser. The relative
  ordering of checks is likely more robust than the absolute rates.
- **No outcome data.** A parsing failure is not observed to cause a rejection
  anywhere in this data.

---

## Data

- [`datasets/ats-parsing-benchmark-2026.json`](../datasets/ats-parsing-benchmark-2026.json)
- [`datasets/ats-parsing-benchmark-2026.csv`](../datasets/ats-parsing-benchmark-2026.csv)

Related page: <https://resumeatlas.io/ats-resume-parsing-benchmark>
