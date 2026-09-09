# Limitations

What this data cannot support. This page is deliberately long, because the
usefulness of the rest of the repository depends on it being honest.

---

## 1. There is no hiring-outcome data. None.

This is the single most important limitation.

Nothing in this corpus records whether a resume led to a screen, an interview, an
offer, or a rejection. No study here can support a claim of the form "resumes that
do X get more interviews", however plausible that claim may be and however often
similar claims are made elsewhere.

Every finding is a statement about **resume content and structure**, and about how
those align with the **stated requirements of postings**. The step from there to
hiring results is not in the data.

If you are citing this research, this is the constraint most likely to be lost in
summary. Please carry it.

---

## 2. Convenience sample

The population is people who chose to run their resume through a resume tool. That
selects for:

- People who suspect their resume needs work
- People actively applying, rather than passively employed
- People who reach for online tools
- People aware of ATS concerns in the first place

A random sample of job seekers would look different. A random sample of *resumes*
would look different again.

---

## 3. Heavy domain skew

The sample skews toward software, data and engineering roles. Every skill-level
finding reflects those postings.

This matters in both directions. The specific technologies in the
[skill gap study](../research/skill-gap-analysis.md) obviously do not generalise
to nursing or accountancy. Less obviously, the
[quantification finding](../research/resume-bullet-quantification.md) is measured
in a domain where numeric outcomes are arguably *more* available than average —
so the low quantification rate is unlikely to be a domain artefact in the
optimistic direction.

---

## 4. Self-selected postings

Users choose which posting to check. If people preferentially check jobs they feel
uncertain about — which seems likely — measured alignment will be lower than the
alignment of all applications those users actually send.

---

## 5. Extraction confounds the input

All analysis runs on text extracted from PDF and DOCX files. Some measurements
therefore describe the extraction pipeline as much as the document:

- **Bullet counts** are affected by how extraction handles bullet glyphs. The
  bullet-structure parse check is marked confounded and excluded from
  interpretation for exactly this reason.
- **Layout-dependent content** — tables, columns, text boxes, graphics — may be
  reordered or dropped before analysis begins.
- **Missing fields** cannot be distinguished from unextractable fields. A resume
  with no LinkedIn URL in the parsed output may never have had one.

---

## 6. The parsing benchmark tested one parser

It tested the ResumeAtlas analyser, which models the text-extraction stage that
commercial systems share. It did **not** test Workday, Greenhouse, Lever, iCIMS,
Taleo, SAP or any other named system, and no claim about any of them is supported.

The *relative ordering* of checks — that section detection fails far more often
than email extraction — is likely more robust across parsers than the absolute
rates.

Not measured, because the source data does not contain it:

- PDF versus DOCX parse rates — the source file type is not stored
- Page-count effects — not stored
- Any specific commercial ATS
- Hiring outcomes

---

## 7. Model outputs are not ground truth

Verdicts, shortlist odds, skill classification and bullet classification are
produced by models. They carry model error, and they are not independent of one
another: the component scores and the overall verdict come from the same system,
so agreement between them is not corroboration.

Where a number is a model estimate rather than a measurement, the studies say so.

---

## 8. Sample sizes differ, and are sometimes small

Signals were introduced at different times. The parsing benchmark in particular
runs on a substantially smaller sample than the main corpus, and its per-check
rates should be read as directional.

Figures from different windows are never pooled. Each printed figure carries its
own `n`.

---

## 9. Snapshots move

The datasets regenerate from the production database. A figure quoted today may
not match the file next month. Cite the `generatedAt` date with the number.

---

## 10. No causal claims

No study here adjusts for confounders, and no study has a control group. Resumes
that differ on any measured dimension also differ on seniority, function,
industry and country, none of which are controlled.

Descriptive statements about what resumes contain are supported. Causal statements
about what makes a resume work are not.
