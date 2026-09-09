# Methodology

- [Data collection](data-collection.md) — where the data comes from, what is stored, what is never stored
- [Definitions](definitions.md) — the exact meaning of every measured term
- [Limitations](limitations.md) — sample bias, confounds, and claims this data cannot support

## Principles

These are the rules the data pipeline enforces. They are listed because they are
the reason the numbers can be trusted, and because they constrain what can
honestly be published.

**Print the real sample size.** Sample counts are never rounded up to a rhetorically
convenient number. If `n` is 1,663, the published figure is 1,663.

**Every rate carries its `n` and its window.** Different signals were introduced at
different times, so studies report several different sample sizes rather than a
single sitewide one. Figures from different windows are not pooled.

**Medians, not means.** Resume metrics are skewed. Medians describe the typical
document; means describe an artefact of the tail.

**Publish the caveat with the number.** The sample skew is carried in the dataset
files themselves, not only in the prose, so it travels with the data when someone
re-uses it.

**Aggregate only.** No resume text, no personal data, no employer names, no
identifying fields are published, in any form.

**Regenerate before quoting.** The datasets are rebuilt from the production
database on every deploy. Numbers quoted anywhere new are taken from a fresh
snapshot rather than copied from an older document.
