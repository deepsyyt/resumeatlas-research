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
| Distinct skill terms appearing as a gap | **7,589** |
| Median required skills missing per resume | **6** |
| Median skills named but not evidenced | **7** |
| Share of gaps that were required, not preferred | **72.8%** |

*n = 1,667, March 2026 – September 2026.*

<!-- /GENERATED -->

### Required, not preferred

<!-- GENERATED:required-preferred -->

| Framing in the posting | Share of all gaps |
| --- | --- |
| **Required** | **72.8%** |
| Preferred / nice to have | 27.2% |

*n = 1,342, March 2026 – September 2026.*

<!-- /GENERATED -->

Postings routinely separate must-haves from nice-to-haves, and the gaps in this
corpus fall mostly on the must-have side. A missing skill in this data is usually
not a bonus qualification the candidate happens to lack; it is something the
posting listed as necessary.

### Most frequently missing skills

<!-- GENERATED:top-missing -->

| # | Skill | Analyses missing it | Share of all analyses |
| --- | --- | --- | --- |
| 1 | AWS | 104 | 6.2% |
| 2 | Angular | 94 | 5.6% |
| 3 | Kubernetes | 87 | 5.2% |
| 4 | Python | 70 | 4.2% |
| 5 | GCP | 48 | 2.9% |
| 6 | Docker | 47 | 2.8% |
| 7 | Azure | 40 | 2.4% |
| 8 | C++ | 38 | 2.3% |
| 9 | Jenkins | 37 | 2.2% |
| 10 | Kafka | 36 | 2.2% |
| 11 | Azure DevOps | 32 | 1.9% |
| 12 | Oracle | 32 | 1.9% |
| 13 | Snowflake | 28 | 1.7% |
| 14 | Tableau | 28 | 1.7% |
| 15 | Node.js | 28 | 1.7% |
| 16 | MongoDB | 28 | 1.7% |
| 17 | MySQL | 26 | 1.6% |
| 18 | Power BI | 26 | 1.6% |
| 19 | Terraform | 25 | 1.5% |
| 20 | Java | 23 | 1.4% |

*n = 1,667, March 2026 – September 2026.* Share is of **all analyses**, not of all gaps.

<!-- /GENERATED -->

Note how low the individual shares are. Even the single most commonly missing
skill appears as a gap in only a small minority of analyses. There is no dominant
universal gap — the distribution is extremely long-tailed.

### Most frequently matched skills

For contrast, the skills resumes reliably *do* carry:

<!-- GENERATED:top-matched -->

| # | Skill | Analyses matching it | Share of all analyses |
| --- | --- | --- | --- |
| 1 | SQL | 458 | 27.5% |
| 2 | Python | 453 | 27.2% |
| 3 | GIT | 307 | 18.4% |
| 4 | C# | 262 | 15.7% |
| 5 | Communication | 236 | 14.2% |
| 6 | JavaScript | 223 | 13.4% |
| 7 | Cross-functional collaboration | 217 | 13% |
| 8 | Stakeholder management | 190 | 11.4% |
| 9 | Problem-solving | 175 | 10.5% |
| 10 | Agile | 167 | 10% |
| 11 | AWS | 162 | 9.7% |
| 12 | Microservices | 161 | 9.7% |

*n = 1,667, March 2026 – September 2026.*

<!-- /GENERATED -->

### Category asymmetry

The clearest structural finding comes from bucketing skills by category and
comparing each category's share of all **missing** skills against its share of all
**matched** skills:

<!-- GENERATED:category-split -->

| Category | Share of all *missing* skills | Share of all *matched* skills | Direction |
| --- | --- | --- | --- |
| Cloud & infrastructure | 32.3% | 13% | **Over-represented among gaps** |
| Languages & frameworks | 28.7% | 28.7% | Roughly balanced |
| Data & databases | 20% | 22.1% | Roughly balanced |
| CI/CD & tooling | 12.5% | 14.1% | Roughly balanced |
| Ways of working | 6.6% | 22.1% | Over-represented among matches |

*n = 1,667, March 2026 – September 2026.* Terms outside the explicit category lists fall into “Other” and are excluded here.

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
| 1 | Python | 76 | 4.6% |
| 2 | Stakeholder management | 75 | 4.5% |
| 3 | SQL | 61 | 3.7% |
| 4 | Team leadership | 61 | 3.7% |
| 5 | Cross-functional collaboration | 60 | 3.6% |
| 6 | AWS | 59 | 3.5% |
| 7 | Communication | 57 | 3.4% |
| 8 | Problem solving | 46 | 2.8% |
| 9 | Communication skills | 42 | 2.5% |
| 10 | Cross-functional leadership | 42 | 2.5% |
| 11 | A/b testing | 40 | 2.4% |
| 12 | GCP | 38 | 2.3% |

*n = 534, March 2026 – September 2026.*

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
