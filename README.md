# ResumeAtlas Research

Open research, datasets and methodology on how resumes actually perform against
real job descriptions and applicant tracking systems.

Everything published here comes from analyses run on
[ResumeAtlas](https://resumeatlas.io) — aggregated, anonymised, and released with
the sample size, the time window and the limitations attached to every number.

**Licence:** data and written research are [CC BY 4.0](LICENSE) — free to use, quote
and republish with attribution.

---

## Headline findings

<!-- GENERATED:headline -->

| Finding | Figure | Sample |
| --- | --- | --- |
| Resume bullet points containing a measurable result (median resume) | **4.7%** | n = 2,075 |
| Resumes with no quantified bullet anywhere | **27.4%** | n = 2,075 |
| Resume-posting pairs judged ready to send as-is | **44.1%** | n = 2,132 |
| Median keyword coverage against the target posting | **80%** | n = 3,218 |
| Skill gaps that were *required* rather than preferred | **81%** | n = 2,274 |
| Resumes where section detection did not come back clean | **39.4%** | n = 218 |

Snapshot: **2026-11-11**. Sample sizes differ because signals were introduced at different times — each figure carries its own `n`, and figures from different windows are never pooled.

> These are resume-vs-job-description analyses run on ResumeAtlas, not a survey of all resumes. The sample skews toward software, data and engineering roles, so the specific tools below reflect those postings more than hiring overall.

*(“the specific tools” in that caveat means the technologies named in the skill tables — see [skill gap analysis](research/skill-gap-analysis.md), not the ResumeAtlas tools listed below.)*

<!-- /GENERATED -->

Full numbers, definitions and caveats live in [`research/`](research/) and
[`methodology/`](methodology/).

---

## What is ResumeAtlas?

**One place for the whole resume problem.** Most resume tools solve one slice of
this and charge a monthly subscription for it, so job seekers end up paying for
three or four at once. ResumeAtlas covers the whole path — from a blank page to
the file you actually send — in one place.

| The job to be done | The tool |
| --- | --- |
| Should I apply to this job at all? | [Application Verdict](https://resumeatlas.io/check-resume-against-job-description) — rejection risks and shortlist odds for one posting |
| Can an ATS even read my resume? | [ATS checker and parser](https://resumeatlas.io/ats-resume-checker) — the exact profile an ATS builds from your file |
| My resume has columns, tables, and graphics | [ATS converter](https://resumeatlas.io/convert-resume-to-ats-format) — rebuilds it single-column and parseable, wording preserved |
| I need to write one from scratch | [ATS builder](https://resumeatlas.io/ats-resume-builder), with a free generic template plus 32 role-specific ones |
| I'm switching fields | [Career-change builder](https://resumeatlas.io/career-change-resume-builder) — reframes your experience as evidence for the new role |
| Rewrite this resume for this posting | [Tailor](https://resumeatlas.io/tailor-resume-to-job-description) — rewrites only the lines your real work supports, and marks every change |

Three further tools cover the smaller jobs — a
[keyword scanner](https://resumeatlas.io/resume-keyword-scanner), a
[work-experience bullet generator](https://resumeatlas.io/resume-bullet-generator),
and a [professional summary generator](https://resumeatlas.io/professional-summary-generator)
— nine in total. Every tool is free to use; you pay once, per tool, only to
download a finished file.

Site: <https://resumeatlas.io>

### Research coverage

The intent is to publish research from every tool on the platform. Coverage today
stands at two of the nine:

| Tool | Research status |
| --- | --- |
| Resume-versus-posting comparison | **Published** — the main corpus |
| ATS checker and parser | **Published** — the parsing benchmark |
| ATS converter | Planned |
| ATS builder | Planned |
| Career-change builder | Planned |
| Tailor | Planned |
| Keyword scanner | Planned |
| Bullet generator | Planned |
| Summary generator | Planned |

The two published corpora share a property that makes them worth reading: every
record is a resume measured against a *named job description* the user supplied,
or against a parser — rather than graded in the abstract. That is what lets the
data answer questions generic resume advice cannot, such as whether a resume fails
on keywords or on evidence.

Coverage expands as each remaining tool begins capturing aggregate statistics.
Nothing is published from a tool before it has a sample large enough to report and
can meet the same standard as everything else here: exact sample sizes, a stated
window, published limitations, and no resume content or personal data of any kind
— see [methodology](methodology/). Until a tool appears above as published,
nothing in this repository describes what people build, write or download through
it.

---

## What this repository contains

| Directory | Contents |
| --- | --- |
| [`research/`](research/) | Written studies — question, method, findings, limitations |
| [`datasets/`](datasets/) | The underlying aggregate data as CSV and JSON, versioned |
| [`insights/`](insights/) | Shorter analytical notes and observations that aren't full studies |
| [`methodology/`](methodology/) | How the data is collected, how every term is defined, what the sample can and cannot support |
| [`technical/`](technical/) | Technical research — resume parsing, text extraction, skill matching |
| [`questions/`](questions/) | The questions people actually ask, clustered into topics, each mapped to research or marked open |
| [`sources/`](sources/) | Provenance audit of the statistics that dominate this field, including the ones that are not ours |

The datasets are regenerated from the production database on every ResumeAtlas
deploy, so the figures here track the live sample rather than a one-off export.
Each file records its own `generatedAt`, sample size and window.

---

## Questions we investigate

Research here starts from real confusion rather than from a keyword list. Public
search data and recurring themes in career communities are collected, clustered
into topics, and mapped to the research that answers them — or marked open.

| Cluster | Core confusion | Status |
| --- | --- | --- |
| [ATS and parsing](questions/ats-and-parsing.md) | Does an ATS actually reject resumes, and what does it read? | Partly answered |
| [Resume–job matching](questions/resume-job-matching.md) | How closely must a resume match the posting? | Partly answered |
| [Resume writing](questions/resume-writing.md) | What should a bullet point actually contain? | Partly answered |
| [Keywords](questions/keywords.md) | Which keywords matter, and how many? | Open |

Two rules govern that directory: **no one's words are republished** — themes are
synthesised, never quoted from an individual's post — and **there is no page per
question.** Questions tell us what is worth measuring; a cluster earns a study
only when we hold data that can answer it. Most clusters are still open, and say so.

The strongest finding from this exercise was not any single question. It was that
a handful of **unsourced or very old statistics** govern the whole topic space —
the "60% of requirements" rule traces to an unpublished internal report; "75% of
resumes are rejected by an ATS" has no methodology we can find; "recruiters spend
7 seconds" comes from a small eye-tracking study over a decade old. Each is
recycled until search engines return it as fact. They are tracked, with
provenance and honest verification status, in
[`sources/recycled-statistics.md`](sources/recycled-statistics.md).

---

## Research

| Study | Question | n |
| --- | --- | --- |
| [Bullet quantification](research/resume-bullet-quantification.md) | How many resume bullet points contain a measurable result? | <!-- GENERATED:n-bullets -->2,075<!-- /GENERATED --> |
| [Resume–job alignment](research/resume-job-alignment.md) | How well do real resumes match the specific jobs they are sent to? | <!-- GENERATED:n-alignment -->3,218<!-- /GENERATED --> |
| [Skill gap analysis](research/skill-gap-analysis.md) | Which skills do postings require that resumes most often lack? | <!-- GENERATED:n-skills -->3,218<!-- /GENERATED --> |
| [ATS parsing benchmark](research/ats-parsing-benchmark.md) | What fails when a resume is read as a machine-readable document? | <!-- GENERATED:n-parsing -->218<!-- /GENERATED --> |

Each study states its own window, sample size and the questions its data
**cannot** answer.

Written up for a general audience: [how many job requirements do you actually need to meet?](https://resumeatlas.io/how-many-job-requirements-do-you-need-to-meet) — the coverage
question, measured, next to the provenance of the figure it replaces.

---

## Datasets

| File | Format | Description |
| --- | --- | --- |
| [`resume-insights-2026.csv`](datasets/resume-insights-2026.csv) | CSV | Flat, one-row-per-metric summary of the resume-vs-job-description corpus |
| [`resume-job-analysis-2026.json`](datasets/resume-job-analysis-2026.json) | JSON | The same corpus with full distributions and skill frequency tables |
| [`ats-parsing-benchmark-2026.json`](datasets/ats-parsing-benchmark-2026.json) | JSON | Per-check pass/warn/fail rates from the resume parsing benchmark |
| [`ats-parsing-benchmark-2026.csv`](datasets/ats-parsing-benchmark-2026.csv) | CSV | Flattened parsing benchmark for spreadsheet use |
| [`tool-insights-2026.json`](datasets/tool-insights-2026.json) | JSON | Aggregates from anonymous, content-free records of the free tools (resume length and page counts, skills-section size, career-change pairs, tailoring delta, action verbs, summary length, keyword gaps) plus structured facts from the job-description corpus. A section is `null` until it has 100 rows; per-role/country cuts need 30 |
| [`template-parse-test-2026.json`](datasets/template-parse-test-2026.json) | JSON | Canva gallery templates, 20 fonts, and 35 PDF/Word template pairs run through the ResumeAtlas parser |
| [`extractor-comparison-2026.json`](datasets/extractor-comparison-2026.json) | JSON | The same PDFs read by five open-source text extractors (pdf.js, Xpdf, pypdf, pdfminer.six, PyMuPDF) |

See [`datasets/README.md`](datasets/README.md) for the schema of each file.

---

## Methodology

Transparency about method matters more than the headline numbers, so it is
documented separately:

- [Data collection](methodology/data-collection.md) — where the data comes from, what is stored, what is discarded
- [Definitions](methodology/definitions.md) — precisely what "missing skill", "quantified bullet", "ATS score" and every other term mean
- [Limitations](methodology/limitations.md) — sample bias, confounds, and the claims this data does not support

Short version: this is a convenience sample of people who chose to use a resume
tool, it skews toward software, data and engineering roles, and **it contains no
hiring-outcome data at all**. Nothing here can tell you whether a resume got an
interview. Statements in this repository are about resume *content and structure*,
not about hiring results.

---

## Technical research

- [Resume parsing pipeline](technical/resume-parsing.md) — how a PDF or DOCX becomes structured text, and where that process loses information
- [Skill extraction and matching](technical/skill-matching.md) — how a requirement in a posting is matched to evidence in a resume

---

## Citing this work

<!-- GENERATED:citation -->

```
ResumeAtlas, "Resume Statistics" (2026-11-11). Analysis of 3,218 resume-to-job-description comparisons, March 2026 – November 2026. https://resumeatlas.io/resume-insights
```

For the parsing benchmark:

```
ResumeAtlas, "ATS Parsing Benchmark" (2026-09-20). 218 resumes, June 2026 – September 2026. https://resumeatlas.io/ats-resume-parsing-benchmark
```

<!-- /GENERATED -->

Machine-readable citation metadata: [`CITATION.cff`](CITATION.cff).

---

## Corrections

If you find an error in a number, a definition, or an inference, please
[open an issue](https://github.com/deepsyyt/resumeatlas-research/issues).
Corrections are applied to the source data and propagate to the published pages.

---

## About ResumeAtlas

ResumeAtlas builds tools and research around resume analysis, job matching and
career intelligence. The research here is published openly because the useful
findings — that resumes fail on evidence rather than keywords, that section
headings break parsers more often than fonts do — are more valuable shared than
kept.

<https://resumeatlas.io>
