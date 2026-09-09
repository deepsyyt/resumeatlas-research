# Resume parsing: how a document becomes data

A resume is a visual artefact. Every automated system that processes one has to
first convert it into something structured, and information is lost at each step.
This note describes the stages and the characteristic failure at each.

---

## Stage 1 — Text extraction

The file becomes a stream of text.

PDF is the harder case. A PDF does not store paragraphs; it stores glyphs
positioned on a page. Reading order has to be *reconstructed* from coordinates,
and the reconstruction is where multi-column layouts break: a two-column resume
can extract as interleaved fragments from both columns, producing text that is
locally valid and globally nonsense.

DOCX carries more structure, but content inside tables, text boxes and headers or
footers lives in separate parts of the document model and can be emitted out of
order or omitted.

**Characteristic failures at this stage:** column interleaving; header/footer
content detached from the body; text rendered as images extracted as nothing at
all; bullet glyphs normalised or stripped.

That last one is why the bullet-structure check in the
[parsing benchmark](../research/ats-parsing-benchmark.md) is marked confounded —
by the time the analyser sees the text, the evidence it would need has already
been removed by the extractor.

---

## Stage 2 — Section segmentation

The text stream is split into logical sections: experience, education, skills,
summary.

Segmentation depends almost entirely on **heading recognition**. A line is treated
as a heading based on its content and its position relative to surrounding text.
That works when headings are conventional and fails when they are not — which is
the most consequential finding in the parsing benchmark. "My Journey" is a heading
to a human and an ordinary line of text to a segmenter.

Failure here cascades. If the experience section is not identified, every
downstream extraction that depends on it degrades: role boundaries, date pairing,
bullet attribution.

**Characteristic failures:** creative headings; headings styled visually but not
structurally (large text with no other marker); sections that begin without a
heading at all.

---

## Stage 3 — Entity extraction

Within sections, individual fields are recovered: name, contact details, employers,
titles, dates, degrees.

Contact fields are the easiest because they have strong intrinsic patterns — an
email address is recognisable without any context. This is why contact extraction
posts the highest pass rates in the benchmark while structural checks post the
lowest. Pattern-matchable fields survive; relationally-defined fields do not.

Role extraction is harder, because it requires pairing a title with an employer
with a date range across a layout that may present them in any arrangement.

**Characteristic failures:** merged consecutive roles; dates in abbreviated or
mixed formats; titles and employers on the same line with no separator;
information trapped in a header band.

---

## Stage 4 — Structure recovery

Finally, remaining content is attributed: bullets to roles, skills to a canonical
vocabulary, dates to a timeline.

**Characteristic failures:** skills presented as a grid or with rating bars, where
the visual arrangement carries meaning the text stream does not; bullets attributed
to the wrong role after a segmentation error.

---

## Design consequences

Three things follow from this pipeline, and they explain most of the benchmark
results:

**Errors cascade downward.** A segmentation failure at stage 2 produces what looks
like an extraction failure at stage 3. Diagnosing the visible symptom rather than
the actual stage leads to the wrong fix.

**Visual structure is not structural structure.** Anything a human reads from
layout alone — a column boundary, a rating bar, a heading indicated only by font
size — is invisible downstream. This is the general form of the skills-grid
failure.

**Conventional beats clever, mechanically.** Standard section headings, a single
column, and text as text rather than as graphics survive the pipeline. This is not
an aesthetic claim; it is a statement about which documents retain their
information content after extraction.

---

## Caveats

This describes the approach taken by the ResumeAtlas analyser. Other systems make
different trade-offs, and commercial ATS platforms are closed — their behaviour is
inferred from shared constraints, not observed. See
[limitations](../methodology/limitations.md#6-the-parsing-benchmark-tested-one-parser).
