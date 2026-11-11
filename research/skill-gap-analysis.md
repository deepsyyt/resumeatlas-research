# Which skills do postings require that resumes most often lack?

**Question.** When a resume misses a requirement, which requirement is it? Is the
gap concentrated in a few technologies, spread thinly across thousands, or
clustered by category?

**Answer.** The long tail dominates by volume, but the gaps are structurally
concentrated in one category — cloud and infrastructure — and they are
overwhelmingly *required* skills rather than nice-to-haves.

---

## Findings

<!-- GENERATED:skills-overview -->

| Measure | Value |
| --- | --- |
| Distinct skill terms appearing as a gap | **9,885** |
| Median required skills missing per resume | **4** |
| Median skills named but not evidenced | **3** |
| Share of gaps that were required, not preferred | **81%** |

*n = 3,218, March 2026 – November 2026.*

<!-- /GENERATED -->

### Required, not preferred

<!-- GENERATED:required-preferred -->

| Framing in the posting | Share of all gaps |
| --- | --- |
| **Required** | **81%** |
| Preferred / nice to have | 19% |

*n = 2,274, March 2026 – November 2026.*

<!-- /GENERATED -->

Postings routinely separate must-haves from nice-to-haves, and the gaps in this
corpus fall mostly on the must-have side. A missing skill in this data is usually
not a bonus qualification the candidate happens to lack; it is something the
posting listed as necessary.

### Most frequently missing skills

<!-- GENERATED:top-missing -->

| # | Skill | Analyses missing it | Share of all analyses |
| --- | --- | --- | --- |
| 1 | AWS | 119 | 3.7% |
| 2 | Kubernetes | 108 | 3.4% |
| 3 | Python | 103 | 3.2% |
| 4 | Angular | 102 | 3.2% |
| 5 | Docker | 60 | 1.9% |
| 6 | Power BI | 58 | 1.8% |
| 7 | SQL | 56 | 1.7% |
| 8 | Azure | 54 | 1.7% |
| 9 | GCP | 54 | 1.7% |
| 10 | Stakeholder management | 51 | 1.6% |
| 11 | C++ | 48 | 1.5% |
| 12 | Java | 46 | 1.4% |
| 13 | CI/CD | 45 | 1.4% |
| 14 | Snowflake | 44 | 1.4% |
| 15 | Tableau | 41 | 1.3% |
| 16 | Team leadership | 40 | 1.2% |
| 17 | Communication | 40 | 1.2% |
| 18 | Excel | 39 | 1.2% |
| 19 | Kafka | 38 | 1.2% |
| 20 | Risk management | 37 | 1.1% |

*n = 3,218, March 2026 – November 2026.* Share is of **all analyses**, not of all gaps.

<!-- /GENERATED -->

Note how low the individual shares are. Even the single most commonly missing
skill appears as a gap in only a small minority of analyses. There is no dominant
universal gap — the distribution is extremely long-tailed.

### Most frequently matched skills

For contrast, the skills resumes reliably *do* carry:

<!-- GENERATED:top-matched -->

| # | Skill | Analyses matching it | Share of all analyses |
| --- | --- | --- | --- |
| 1 | Python | 690 | 21.4% |
| 2 | SQL | 635 | 19.7% |
| 3 | Communication | 491 | 15.3% |
| 4 | Cross-functional collaboration | 377 | 11.7% |
| 5 | GIT | 362 | 11.2% |
| 6 | Problem-solving | 340 | 10.6% |
| 7 | Stakeholder management | 335 | 10.4% |
| 8 | Communication skills | 325 | 10.1% |
| 9 | Problem solving | 303 | 9.4% |
| 10 | Team leadership | 285 | 8.9% |
| 11 | JavaScript | 271 | 8.4% |
| 12 | C# | 270 | 8.4% |

*n = 3,218, March 2026 – November 2026.*

<!-- /GENERATED -->

### Category asymmetry

The clearest structural finding comes from bucketing skills by category and
comparing each category's share of all **missing** skills against its share of all
**matched** skills:

<!-- GENERATED:category-split -->

| Category | Share of all *missing* skills | Share of all *matched* skills | Direction |
| --- | --- | --- | --- |
| Languages & frameworks | 27.5% | 27.2% | Roughly balanced |
| Cloud & infrastructure | 27% | 11.5% | **Over-represented among gaps** |
| Data & databases | 21.4% | 20.9% | Roughly balanced |
| CI/CD & tooling | 12.6% | 12.8% | Roughly balanced |
| Ways of working | 11.6% | 27.6% | Over-represented among matches |

*n = 3,218, March 2026 – November 2026.* Terms outside the explicit category lists fall into “Other” and are excluded here.

<!-- /GENERATED -->

Two categories sit far off the diagonal, in opposite directions:

- **Cloud and infrastructure** accounts for a much larger share of gaps than of
  matches. It is the category resumes most consistently under-cover relative to
  what postings ask for.
- **Ways of working** (agile, communication, stakeholder management,
  cross-functional collaboration) is the mirror image: heavily represented among
  matched skills, barely present among gaps. These terms are close to universally
  claimed, which makes them close to useless as a differentiator.

### Claimed but not evidenced

A separate signal tracks skills the resume *lists* but does not *demonstrate*
anywhere in its experience bullets:

<!-- GENERATED:top-weak -->

| # | Skill named but not evidenced | Analyses | Share of all analyses |
| --- | --- | --- | --- |
| 1 | Python | 109 | 3.4% |
| 2 | SQL | 104 | 3.2% |
| 3 | Stakeholder management | 103 | 3.2% |
| 4 | Communication | 95 | 3% |
| 5 | Team leadership | 93 | 2.9% |
| 6 | AWS | 74 | 2.3% |
| 7 | Cross-functional collaboration | 70 | 2.2% |
| 8 | Problem solving | 65 | 2% |
| 9 | Communication skills | 63 | 2% |
| 10 | Mentoring | 59 | 1.8% |
| 11 | Cross-functional leadership | 57 | 1.8% |
| 12 | A/b testing | 47 | 1.5% |

*n = 2,085, March 2026 – November 2026.*

<!-- /GENERATED -->

This is a different failure from a missing skill, and arguably a more addressable
one: the candidate has the skill and has named it, but the document gives a reader
no reason to believe it. Note that the same terms recur here and in the matched
list — a skill can be present in the skills section and absent from the evidence.

---

## Method

Requirements are extracted from each job description and classified as **required**
or **preferred** based on how the posting frames them. Each requirement is then
matched against the resume, yielding one of three states: **matched** (present and
evidenced), **weak** (named but not evidenced in experience), or **missing**.

Skill names are normalised for casing and common aliases before counting, so that
`aws`, `AWS` and `Amazon Web Services` aggregate to one term. Category buckets are
assigned by an explicit term list rather than inferred, so the category split is
reproducible from the published data.

Frequency is reported both as a raw count and as a share of all analyses in the
window — not as a share of *gaps*, which would overstate the prominence of any
individual skill.

---

## Interpretation

**The long tail is the finding.** With thousands of distinct terms appearing as
gaps and no single term exceeding a small share of analyses, "learn the top
missing skill" is not a viable strategy. The gaps are specific to individual
resume-posting pairs, which is an argument for per-posting analysis over generic
resume advice.

**Cloud infrastructure is the systematic gap.** Its over-representation among gaps
relative to matches is the strongest category-level signal in the data. A plausible
reading is that infrastructure requirements have propagated into postings for roles
that are not primarily infrastructure roles, faster than they have propagated into
the resumes of people doing those jobs.

**Soft skills are table stakes, not differentiators.** The "ways of working"
asymmetry is stark: these terms are matched constantly and missing almost never.
Adding more of them to a resume cannot close a gap, because the gap is not there.

---

## What this does not show

- **Not a labour-market survey.** These are postings that users chose to check,
  not a representative sample of open roles. Frequency here reflects what this
  sample checked against, not what the market broadly demands.
- **Heavy domain skew.** Software, data and engineering roles dominate. The
  specific technologies listed reflect those postings and should not be read as
  cross-industry.
- **Extraction is imperfect.** A requirement phrased unusually may not be
  extracted, and an alias not in the normalisation list will be counted separately.
- **No outcome data.** Nothing here shows that closing a given gap changes a
  hiring result.
- **Categories are a coarse instrument.** The buckets are defined by an explicit
  term list; terms outside it fall into "Other" and are excluded from the
  category split.

---

## Data

- [`datasets/resume-job-analysis-2026.json`](../datasets/resume-job-analysis-2026.json) → `topMissing`, `topMatched`, `topWeak`, `categorySplit`, `requiredVsPreferred`, `distinctMissingTerms`
- [`datasets/resume-insights-2026.csv`](../datasets/resume-insights-2026.csv) → rows where `category` is `top_missing_skills`, `skill_category_gap` or `required_vs_preferred`
