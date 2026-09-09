# Keywords are not the bottleneck

A short note on the most consistent cross-study pattern in this data.

---

## The observation

Three measurements from the same corpus, each pointing the same direction:

<!-- GENERATED:insight-keywords -->

| Measure | Median | Sample |
| --- | --- | --- |
| Keyword coverage against the target posting | **79%** | 1,667 |
| Required skills missing | **6** | 1,667 |
| Skills named but not evidenced in any bullet | **7** | 534 |
| Bullets containing a measurable result | **5.2%** | 613 |

*Snapshot 2026-09-09. Sample sizes differ by signal; windows are not pooled.*

<!-- /GENERATED -->

Read together: the median resume already contains most of the words the posting
asks for, is missing a handful of genuine requirements, and supports almost none
of its claims with a measurable result.

---

## Why this matters

The dominant public framing of resume optimisation is a keyword problem — get the
right terms in, beat the filter. In this sample that problem is largely already
solved by the time someone checks a resume against a posting. Coverage is high.
Adding more terms has little room to help.

The gap that remains is evidence. A resume can name every requirement and
demonstrate none of them, and this corpus contains a great many resumes that do
exactly that: high coverage, a substantial count of skills named but not evidenced
in any bullet, and a median of roughly one bullet in twenty carrying a number.

The [three-state matching model](../technical/skill-matching.md#stage-3--three-state-matching)
exists precisely to make this visible. Under a simple present/absent model these
resumes look complete.

---

## The obvious objection

Keyword coverage might be high *because* the people running these checks already
optimised for keywords — the advice worked, and this sample is downstream of it.

That is entirely plausible and cannot be ruled out with this data. It does not
change the practical implication, though: for someone whose coverage is already
high, further keyword work has little left to give, and the unevidenced-claim
count is where the remaining headroom sits.

---

## What this note does not claim

It does not claim that evidence-rich resumes perform better in hiring. **There is
no hiring-outcome data in this corpus** — see
[limitations](../methodology/limitations.md#1-there-is-no-hiring-outcome-data-none).

This is a statement about where resumes are and are not complete, relative to what
postings ask for. Whether closing the evidence gap changes an outcome is not
measured here.

---

## Sources

- [Resume–job alignment](../research/resume-job-alignment.md)
- [Bullet quantification](../research/resume-bullet-quantification.md)
- [Skill gap analysis](../research/skill-gap-analysis.md)
