# Recycled statistics: a provenance audit

Resume and ATS advice is governed by a handful of numbers that appear on hundreds
of pages. This page records what each claims, where search engines currently
attribute it, and whether it can be traced to a published methodology.

**Verification status is stated honestly.** "Traced" means we followed it to a
named original. "Not traced" means we have not verified it and are not asserting
anything about it — it is logged as an open item, not debunked.

Audit run 2026-09-09, from live US/English search results.

---

## 1. "You only need to meet 60% of the requirements"

**The claim.** Apply if you meet roughly 60% of a posting's requirements, because
job descriptions are wish lists.

**Status: traced — to an unpublished internal report.**

The figure is most commonly attributed to an internal Hewlett-Packard report
referenced second-hand in a widely read *Harvard Business Review* article. The
underlying report has not been published, so the sample, method and definition of
"requirement" are all unavailable. Sources that trace the number, rather than just
repeating it, say the same thing.

**What we observed.** Asked three closely related questions on the same day,
Google's AI Overview gave three different answers — "60% to 70%" twice and
"40% to 60%" once — citing career forums, a 2018 news survey and a 2021 magazine
column. No cited source presented primary measurement.

**What can be measured instead.** Resumes checked against a specific posting show
a median keyword coverage of **79%** — see
[resume–job alignment](../research/resume-job-alignment.md). Note this is not the
same population as "all applicants": people who run a matching check have
self-selected. It is, however, measured rather than recalled.

---

## 2. "75% of resumes are rejected by an ATS before a human sees them"

**The claim.** An applicant tracking system automatically discards around
three-quarters of applications.

**Status: not traced.** This figure recurs constantly in vendor marketing and
advice content. We have not established an original methodology for it and make
no claim about whether it is accurate. Logged as an open item.

**Why it is hard to test.** The claim conflates two different things: a resume
that a system could not *parse*, and a resume a recruiter *rejected* after
reading a parsed profile. Distinguishing them requires hiring-outcome data, which
we do not hold and do not collect.

**What can be measured instead.** Only the parsing half, and only for one
analyser: **18.8%** of resumes scored below 70 on machine-readability — see the
[parsing benchmark](../research/ats-parsing-benchmark.md). That is a statement
about documents, not about rejections, and it tested no commercial ATS.

---

## 3. "Recruiters spend 7 seconds on a resume"

**The claim.** The average recruiter spends about six to seven seconds on an
initial resume scan.

**Status: partially traced.** Attributed to an eye-tracking study by a job board,
originally published over a decade ago and later updated. The original had a very
small participant count. We have not independently reviewed the methodology.

**What we observed.** This question surfaced in "People also ask" on three
unrelated queries — bullet formatting, resume customisation and keywords —
suggesting it functions as general folklore rather than as an answer to any
specific question.

**What can be measured instead.** Nothing here. We hold no recruiter-behaviour
data, and no study in this repository speaks to how long anyone reads a resume.

---

## 4. "Is 80% a good ATS score?"

**The claim.** That some threshold — usually 75% or 80% — represents a passing
resume score.

**Status: no source at all.** This is a question, not a finding, and it appeared
in "People also ask" on multiple queries. There is no industry-standard ATS score.
Each tool computes its own number on its own scale, so a score is only meaningful
relative to the tool that produced it. A threshold quoted without naming the tool
is not a benchmark.

**What can be measured instead.** For the ResumeAtlas scale specifically, the
median is **80**, with **20.3%** below 70 and **39.9%** at 85 or above — see
[alignment](../research/resume-job-alignment.md). That describes the distribution
of one tool's own scale. It does not establish a pass mark, and it says nothing
about any other tool's score.

---

## The pattern

These four have something in common. Each is a plausible-sounding number that
answers a question people genuinely have; each is repeated far more often than it
is checked; and in each case the recycling has outlived any methodology that might
once have supported it.

That is the gap this repository is trying to fill — not by claiming better
numbers, but by publishing numbers with their sample size, their window and their
limitations attached, so the next person can check them.
