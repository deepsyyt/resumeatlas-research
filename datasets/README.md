# Datasets

All files are aggregate-only. They contain no resume text, no job description
text, and no personal data of any kind.

**Licence:** [CC BY 4.0](../LICENSE) — free to use with attribution.

Every file carries its own `generatedAt` date, sample size and window. These
regenerate from the production database on deploy, so **cite the snapshot date
alongside any figure**.

---

## `resume-insights-2026.csv`

Flat, one-row-per-metric summary of the resume-to-job-description corpus. The
easiest file to open in a spreadsheet.

| Column | Meaning |
| --- | --- |
| `category` | Metric group — `overview`, `ats_score_distribution`, `bullet_evidence`, `verdict`, `experience`, `required_vs_preferred`, `top_missing_skills`, `skill_category_gap` |
| `metric` | Metric name |
| `value` | The figure |
| `unit` | `count`, `percent`, `years`, or `score 0-100` |
| `n` | Sample size for that row |
| `window` | Date range the row covers |
| `notes` | Definition or caveat where one applies |

Note that `n` varies by row. Signals were introduced at different times; rows are
not pooled across windows.

---

## `resume-job-analysis-2026.json`

The same corpus with full distributions and frequency tables.

| Key | Contents |
| --- | --- |
| `generatedAt`, `windowStart`, `windowEnd`, `analysisCount` | Snapshot metadata |
| `medianAtsScore`, `atsScoreDistribution` | Parse/readability score and its banded distribution |
| `medianKeywordCoverage` | Median share of posting requirements present in the resume |
| `topMissing`, `topMatched`, `topWeak` | Skill frequency tables — `term`, `count`, `share` (share of all analyses) |
| `distinctMissingTerms` | Count of distinct terms appearing as a gap |
| `categorySplit` | Per-category share of all missing vs all matched skills |
| `requiredVsPreferred` | Split of gaps by how the posting framed the requirement |
| `bulletEvidence` | Bullet counts, quantified share, and distribution buckets |
| `verdictSplit` | Apply / Optimize First / Skip counts with median shortlist odds |
| `medianResumeYears`, `medianRequiredYears`, `medianExperienceGap` | Experience against posting requirement |
| `roleCoverage` | Per-role breakdown, published only above a minimum sample threshold |
| `sampleCaveat` | The sample-skew statement — carried in the data so it travels with re-use |

`roleCoverage.roles` is currently empty: no individual role has yet reached the
minimum sample size for publication.

---

## `ats-parsing-benchmark-2026.json`

Per-check results from the parsing benchmark.

| Key | Contents |
| --- | --- |
| `generatedAt`, `windowStart`, `windowEnd`, `sampleSize`, `submissionCount` | Snapshot metadata |
| `parseChecks` | Twelve checks — `id`, `label`, `failsWhen`, `passRate`, `warnRate`, `failRate`, `flaggedRate`, `confounded` |
| `confoundedCheckIds` | Checks distorted by the extraction pipeline; excluded from interpretation |
| `fieldExtraction` | Share of resumes where each contact field was absent from parsed output |
| `sectionsRecognized` | Share recognising all three / two / one or none of the core sections |
| `analyzerScoreDistribution` | Rule-based analyser score, banded |
| `llmScore` | The blended model score from the larger corpus, on its own window — context only, do not pool |
| `notMeasured` | Explicit list of what this benchmark did not test |
| `sampleCaveat` | Sample-skew statement |

**Scope:** this tested one analyser, not any commercial ATS. See the
[benchmark study](../research/ats-parsing-benchmark.md).

---

## `ats-parsing-benchmark-2026.csv`

The parsing benchmark flattened for spreadsheet use. Same columns as the insights
CSV: `category`, `metric`, `value`, `unit`, `n`, `window`, `notes`.

---

## Citing

See [citation](../README.md#citing-this-work) and [`CITATION.cff`](../CITATION.cff).
