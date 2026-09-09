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
| Resume bullet points containing a measurable result (median resume) | **5.2%** | n = 613 |
| Resumes with no quantified bullet anywhere | **25.8%** | n = 613 |
| Resume-posting pairs judged ready to send as-is | **6.5%** | n = 581 |
| Median keyword coverage against the target posting | **79%** | n = 1,667 |
| Skill gaps that were *required* rather than preferred | **72.8%** | n = 1,342 |
| Resumes where section detection did not come back clean | **44.9%** | n = 138 |

Snapshot: **2026-09-09**. Sample sizes differ because signals were introduced at different times — each figure carries its own `n`, and figures from different windows are never pooled.

> These are resume-vs-job-description analyses run on ResumeAtlas, not a survey of all resumes. The sample skews toward software, data and engineering roles, so the specific tools below reflect those postings more than hiring overall.

<!-- /GENERATED -->

Full numbers, definitions and caveats live in [`research/`](research/) and
[`methodology/`](methodology/).

---

## What is ResumeAtlas?

ResumeAtlas is a resume-to-job-matching platform. A user pastes a resume and one
specific job description, and the system analyses how well the two align: which
required skills are present, which are claimed but not evidenced, which are
missing entirely, how the resume parses as a machine-readable document, and
whether the application is realistically worth submitting.

Because every analysis is a resume measured against a *named posting* rather than
graded in the abstract, the resulting dataset can answer questions that generic
resume advice cannot — for example, whether a resume fails on keywords or on
evidence, and which of the two actually moves the outcome.

Site: <https://resumeatlas.io>

---

## What this repository contains

| Directory | Contents |
| --- | --- |
| [`research/`](research/) | Written studies — question, method, findings, limitations |
| [`datasets/`](datasets/) | The underlying aggregate data as CSV and JSON, versioned |
| [`insights/`](insights/) | Shorter analytical notes and observations that aren't full studies |
| [`methodology/`](methodology/) | How the data is collected, how every term is defined, what the sample can and cannot support |
| [`technical/`](technical/) | Technical research — resume parsing, text extraction, skill matching |

The datasets are regenerated from the production database on every ResumeAtlas
deploy, so the figures here track the live sample rather than a one-off export.
Each file records its own `generatedAt`, sample size and window.

---

## Research

| Study | Question | n |
| --- | --- | --- |
| [Bullet quantification](research/resume-bullet-quantification.md) | How many resume bullet points contain a measurable result? | <!-- GENERATED:n-bullets -->613<!-- /GENERATED --> |
| [Resume–job alignment](research/resume-job-alignment.md) | How well do real resumes match the specific jobs they are sent to? | <!-- GENERATED:n-alignment -->1,667<!-- /GENERATED --> |
| [Skill gap analysis](research/skill-gap-analysis.md) | Which skills do postings require that resumes most often lack? | <!-- GENERATED:n-skills -->1,667<!-- /GENERATED --> |
| [ATS parsing benchmark](research/ats-parsing-benchmark.md) | What fails when a resume is read as a machine-readable document? | <!-- GENERATED:n-parsing -->138<!-- /GENERATED --> |

Each study states its own window, sample size and the questions its data
**cannot** answer.

---

## Datasets

| File | Format | Description |
| --- | --- | --- |
| [`resume-insights-2026.csv`](datasets/resume-insights-2026.csv) | CSV | Flat, one-row-per-metric summary of the resume-vs-job-description corpus |
| [`resume-job-analysis-2026.json`](datasets/resume-job-analysis-2026.json) | JSON | The same corpus with full distributions and skill frequency tables |
| [`ats-parsing-benchmark-2026.json`](datasets/ats-parsing-benchmark-2026.json) | JSON | Per-check pass/warn/fail rates from the resume parsing benchmark |
| [`ats-parsing-benchmark-2026.csv`](datasets/ats-parsing-benchmark-2026.csv) | CSV | Flattened parsing benchmark for spreadsheet use |

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

## ResumeAtlas tools

The analyses in this repository are produced by these tools:

- **Resume ↔ job description matching** — [check-resume-against-job-description](https://resumeatlas.io/check-resume-against-job-description)
- **ATS resume checker and parser** — [ats-resume-checker](https://resumeatlas.io/ats-resume-checker)
- **ATS format converter** — [convert-resume-to-ats-format](https://resumeatlas.io/convert-resume-to-ats-format)
- **Resume tailoring** — [tailor-resume-to-job-description](https://resumeatlas.io/tailor-resume-to-job-description)
- **Keyword scanner** — [resume-keyword-scanner](https://resumeatlas.io/resume-keyword-scanner)
- **Chrome extension** — job-description matching from the posting page

---

## Citing this work

<!-- GENERATED:citation -->

```
ResumeAtlas, "Resume Statistics" (2026-09-09). Analysis of 1,667 resume-to-job-description comparisons, March 2026 – September 2026. https://resumeatlas.io/resume-insights
```

For the parsing benchmark:

```
ResumeAtlas, "ATS Parsing Benchmark" (2026-09-04). 138 resumes, June 2026 – September 2026. https://resumeatlas.io/ats-resume-parsing-benchmark
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
