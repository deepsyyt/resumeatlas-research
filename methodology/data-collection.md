# Data collection

## Source

The data comes from analyses that users voluntarily ran on ResumeAtlas. There are
two distinct corpora, collected differently, and they are kept separate throughout
this repository.

### 1. Resume-to-job-description analyses

The larger corpus. Each record is created when a user submits a resume together
with one specific job description and requests an analysis. The stored record is
the **analysis result** — scores, extracted requirement lists, per-skill match
states, verdict — not the submitted documents.

This corpus supports the [alignment](../research/resume-job-alignment.md),
[skill gap](../research/skill-gap-analysis.md) and
[bullet quantification](../research/resume-bullet-quantification.md) studies.

### 2. Parsing benchmark

A smaller corpus, drawn from signed-in users whose extracted resume text was
retained. Each resume is run through the production parsing analyser to produce
per-check pass/warn/fail results.

This corpus supports the [parsing benchmark](../research/ats-parsing-benchmark.md).

## What is published

Aggregates only:

- Counts, shares and medians across the corpus
- Frequency tables of normalised skill terms
- Distribution buckets

## What is never published

- Resume text, in whole or in part
- Names, email addresses, phone numbers, links or locations
- Employer names, job titles tied to an individual, or education details
- Job description text
- Any field that could identify a user or an employer
- Any per-record data at all

A minimum sample threshold is applied before any subgroup is published, so that
thin slices — a role with only a handful of records, for instance — are withheld
rather than reported. In the current snapshot the role-level breakdown is empty
for exactly this reason: no role has yet accumulated enough records to publish.

## Generation and freshness

The published datasets are regenerated from the production database as part of
the deploy pipeline, and a scheduled job triggers a rebuild so that a quiet period
cannot let the snapshot silently go stale.

Consequences worth knowing if you are citing this data:

- **Numbers move.** Each file carries a `generatedAt` date and a window. Cite the
  snapshot date alongside the figure.
- **Sample sizes grow.** A figure quoted from an older snapshot will not match the
  current file. This is expected; the versioned files in
  [`datasets/`](../datasets/) are the record.
- **The snapshot is built, not queried live.** The underlying table is not exposed
  to the public site at request time.

## Aggregation choices

- **Medians over means** for all resume-level metrics.
- **Share of all analyses**, not share of gaps, when reporting skill frequency —
  reporting a skill as a share of gaps would inflate its apparent prominence.
- **Normalisation before counting** for skill terms: casing and known aliases are
  collapsed to one canonical term. Unknown aliases are counted separately, which
  under-counts rather than over-counts any given skill.
- **Explicit category term lists**, not inferred clustering, so the category split
  is reproducible from the published data.
