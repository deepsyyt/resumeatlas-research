# Cluster: ATS and parsing

**The core confusion.** People do not know whether an applicant tracking system
is a filter that rejects them, or a database that stores them — and that
uncertainty drives most of the anxiety in this cluster.

## Recurring themes

- Whether an ATS automatically rejects a resume, or whether a human always reads it
- What proportion of resumes are discarded before a person sees them
- What an ATS actually extracts from a document, and what it cannot read
- Whether a resume will "pass" — treated as a binary outcome
- What a given ATS score means, and whether some threshold is a pass mark
- Whether AI-written resumes can be detected

## What we can answer

The [parsing benchmark](../research/ats-parsing-benchmark.md) measures the half
of this that is measurable: what survives when a real resume is turned into
structured text. Structure fails far more often than contact details — section
detection, skills blocks and multi-column layouts are the weak points, while
name, email and phone extract cleanly in the large majority of cases.

## What we cannot answer

Whether any resume was rejected, by an ATS or a person. **This repository holds
no hiring-outcome data**, so the central question in this cluster — does the
machine reject you — is outside what our data can address.

We also tested one analyser, not any commercial ATS. See
[limitations](../methodology/limitations.md#6-the-parsing-benchmark-tested-one-parser).

## Related provenance

"75% of resumes are rejected by an ATS" and "is 80% a good ATS score" are both
examined in [recycled statistics](../sources/recycled-statistics.md).
