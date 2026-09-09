# Skill matching: from requirement to evidence

Matching a job description against a resume looks like a string-matching problem
and is not one. This note describes the stages and the reasoning behind the
three-state model that produces the
[skill gap findings](../research/skill-gap-analysis.md).

---

## Stage 1 — Requirement extraction

Requirements are pulled from the posting, then classified as **required** or
**preferred** based on the posting's own framing: "must have", "required" and
"X+ years of" against "preferred", "nice to have" and "bonus".

The classification captures how the *posting frames* a requirement, not how
important it actually is to the employer. Postings are frequently inaccurate about
their own must-haves; that inaccuracy is preserved rather than corrected, because
correcting it would mean substituting a guess for the stated text.

**Difficulty:** requirements arrive in prose, in bullets, and buried in
responsibility descriptions. A responsibility ("you will own our Terraform
modules") implies a requirement without stating one.

---

## Stage 2 — Normalisation

Extracted terms are collapsed to canonical forms. `aws`, `AWS` and
`Amazon Web Services` are one term. `Node.js`, `NodeJS` and `node` are one term.

Normalisation uses an explicit alias list rather than fuzzy similarity. The
trade-off is deliberate: an alias not on the list is counted as a separate term,
which **under-counts** a skill's true frequency. Fuzzy matching would reduce that
under-count at the cost of false merges — and a false merge silently corrupts a
published frequency table in a way that is very hard to detect afterwards. Given
the choice, the pipeline prefers a known undercount to an unknown error.

Casing is preserved for display through an exact-form map, so `C++`, `CI/CD` and
`Power BI` render correctly rather than being title-cased into nonsense.

---

## Stage 3 — Three-state matching

Each normalised requirement is resolved against the resume into one of three
states. This is the core design decision.

| State | Condition |
| --- | --- |
| **Matched** | Named in the resume *and* evidenced in experience or project content |
| **Weak** | Named in the resume, but no bullet demonstrates its use |
| **Missing** | Not named at all |

A two-state model — present or absent — cannot express the most common finding in
this corpus. A resume that lists twenty technologies in a skills block and
describes none of them in its experience section scores as fully covered under
presence matching, and as substantially unevidenced under this model. Both
statements are true about different things, and separating them is what makes the
[alignment finding](../research/resume-job-alignment.md) legible: high keyword
coverage sitting alongside thin evidence.

**Difficulty:** evidence detection requires judging whether a bullet actually
demonstrates a skill or merely mentions it in passing. This is a model judgement
and carries model error.

---

## Stage 4 — Aggregation

For published statistics, matched, weak and missing terms are counted across
analyses. Two rules shape the output:

**Frequency is reported as a share of all analyses**, not as a share of gaps.
Reporting "AWS is 6% of all gaps" would make the gaps look concentrated; reporting
"AWS is missing in 6% of analyses" shows what is actually true — that no single
skill is a common gap, and the distribution is long-tailed across thousands of
distinct terms.

**Category buckets are explicit term lists**, not inferred clusters. This makes the
category split in the skill gap study reproducible from the published data, and
means "Other" is an honest bucket rather than a dumping ground disguised by
clustering.

---

## Caveats

Extraction and evidence detection are both model-mediated, so both carry error.
Terms outside the alias list are undercounted, and terms outside the category
lists fall into "Other" and are excluded from the category split. See
[limitations](../methodology/limitations.md).
