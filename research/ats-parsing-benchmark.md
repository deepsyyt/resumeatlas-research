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
| Resumes tested | **218** |
| Submissions seen | 322 |
| Median analyser score (0–100) | **84** |
| Scoring below 70 | 16.1% |
| Recognised all three core sections | **60.6%** |

*n = 218, June 2026 – September 2026.* Snapshot 2026-09-20.

> These are resumes real people submitted to ResumeAtlas between the dates above, run through ResumeAtlas's own ATS-parse analyzer. The sample is small, skews toward software, data and engineering roles, and covers signed-in users only. Treat it as a directional ResumeAtlas study, not a definitive measure of every resume or every ATS.

<!-- /GENERATED -->

### Per-check results

Each resume is run through twelve independent checks. **Pass** means the element
was extracted cleanly, **warn** means it was extracted with ambiguity, **fail**
means it could not be reliably recovered.

<!-- GENERATED:parse-checks -->

| Check | Pass | Warn | Fail | Fails when |
| --- | --- | --- | --- | --- |
| Bullet structure ⚠️ | 57.8% | 3.2% | 39% | **Confounded — excluded from interpretation.** Dense paragraphs with no bullet markers |
| Tables & columns | 59.2% | 22% | 18.8% | Two-column layouts and tables for core content |
| Section detection | 60.6% | 23.4% | 16.1% | Creative headings like “My Journey” or “Toolbox” |
| Icons & graphics | 71.6% | 9.2% | 19.3% | Contact icons, emoji, and decorative glyphs |
| Skills | 72.9% | 4.1% | 22.9% | Skill grids, rating bars, or column layouts |
| Work experience | 74.3% | 14.7% | 11% | Roles merged or missing title/date pairing |
| Education | 74.3% | 25.7% | 0% | Degrees buried in prose or unlabeled sections |
| Dates | 90.8% | 2.3% | 6.9% | Mixed styles, “’21-’23”, or dates in graphics |
| Name | 92.2% | 0% | 7.8% | Name inside a header band, logo, or image |
| Headers & footers | 92.2% | 7.8% | 0% | Name/email/phone trapped in header or footer bands |
| Phone | 93.1% | 6.9% | 0% | Number split across table cells or stylized |
| Email | 95% | 0% | 5% | Email shown only as an icon or in a graphic |

Sorted worst-performing first. *n = 218, June 2026 – September 2026.*

<!-- /GENERATED -->

### Field extraction

<!-- GENERATED:field-extraction -->

| Field | Absent from parsed output |
| --- | --- |
| Name | 7.8% |
| Email | 5% |
| Phone | 6.9% |
| Location | 46.3% |
| LinkedIn | 62.8% |

*n = 218, June 2026 – September 2026.* “Absent” cannot be distinguished from “never present in the resume”.

<!-- /GENERATED -->

### Section recognition

<!-- GENERATED:sections -->

| Core sections recognised | Share of resumes |
| --- | --- |
| All three | **60.6%** |
| Two | 23.4% |
| One or none | 16.1% |

*n = 218, June 2026 – September 2026.*

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

- PDF vs DOCX parse rates on the submitted resumes — the source file type is not stored. The page answers the question from 35 template pairs rendered both ways instead (see the PDF or Word card).
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
