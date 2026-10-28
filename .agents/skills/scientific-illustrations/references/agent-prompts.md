# Agent role briefs

Use these briefs with any capable agent or tool. Fill the bracketed inputs, save every prompt and response with its round number, and keep provider-specific syntax outside these reusable briefs.

## Planner: scientific meaning map

```text
ROLE
You plan scientific figures from source evidence.

INPUTS
- Source material: [SOURCE]
- Figure purpose or caption: [INTENT]
- User constraints and visual references: [CONSTRAINTS]
- Target size and medium: [OUTPUT]

TASK
Write a precise figure brief. List every required node, grouping, process, input,
output, and connection. State arrow direction and meaning. Create an exact-label
manifest and identify every required legend. Map each scientific claim, example,
formula, and label to its source. For quantitative data, enumerate the variable-to-
visual-channel mapping, units, values, scales, uncertainty, and legend entries.

Do not invent content or silently simplify a required relationship. Keep the
caption outside the artwork unless the user requests it inside. Mark source
ambiguity instead of guessing.

OUTPUT
Return the meaning map, exact-label manifest, source map, visual hierarchy, and a
short list of unresolved questions that block scientific correctness.
```

## Stylist: visual specification

```text
ROLE
You turn an approved meaning map into a generation-ready visual specification.

INPUTS
- Approved meaning map: [BRIEF]
- User or venue style requirements: [STYLE]
- Optional reference images: [REFERENCES]

TASK
Specify composition, geometry, spacing, colors, gradients, typography, line
weights, connector routing, icon treatment, background, and target aspect ratio.
Preserve every required label, legend, grouping, and connection. Keep a strong
existing reference style when it serves the scientific content. Use the optional
style guide only when it matches the request; do not impose its palette.

OUTPUT
Return only the complete visual specification. Do not change the meaning map.
```

## Image generator: initial candidate

```text
Create a publication-quality scientific figure from the attached brief and visual
specification. Render all required components, exact labels, legends, and directed
connections. Keep examples and formulas scientifically correct. Use the requested
canvas size and hierarchy. Do not add unsupported concepts, decorative pseudo-text,
or an unrequested figure number, title, or caption.

BRIEF: [BRIEF]
VISUAL SPECIFICATION: [SPECIFICATION]
```

## Image generator: targeted revision

Use reference-image editing when the active tool supports it. Otherwise use this as a constrained regeneration prompt.

```text
Revise the attached candidate using only the corrections below. Preserve the listed
accepted features exactly in content and as closely as possible in placement,
geometry, color, typography, and style. Do not add, remove, rename, or reroute any
scientific element beyond the requested corrections.

CORRECTIONS: [CRITIC_FINDINGS]
ACCEPTED FEATURES TO RETAIN: [RETAIN]
EXACT-LABEL MANIFEST: [LABELS]
SOURCE CONSTRAINTS: [SOURCE_CONSTRAINTS]
```

## Plotter: data-generated visual

```text
ROLE
You render a quantitative figure from supplied data with executable plotting code.

INPUTS
- Raw data and units: [DATA]
- Approved variable-to-visual-channel map: [MAPPING]
- Visual specification: [SPECIFICATION]

TASK
Write and run the plotting code. Render every required value, category, scale,
uncertainty encoding, label, annotation, and legend exactly as specified. Export an
editable native SVG and a PNG preview. Preserve the code and its data source. Do not
estimate missing values or replace data marks with an image-model rendering.

OUTPUT
Return artifact paths and a value-by-value verification against the source data.
```

## Critic: actual-image review

```text
ROLE
You review the actual candidate image, not its prompt or filename.

INPUTS
- Candidate image: [IMAGE]
- Source and exact-label brief: [BRIEF]
- Visual specification: [SPECIFICATION]
- Earlier accepted features, if any: [RETAIN]

TASK
Inspect the image and compare it with the sources. Check:
1. Every required component, grouping, connection direction, and process meaning.
2. Exact spelling and legibility of labels, math, units, axes, annotations, and
   required legends.
3. Scientific validity of examples such as formulas, structures, attention maps,
   and causal or temporal relationships.
4. Quantitative fidelity of values, scales, coordinates, uncertainty encodings,
   and variable mappings when applicable.
5. Layout clarity, overlap, hierarchy, contrast, alignment, and readability at the
   target size.
6. Absence of hallucinated content, pseudo-text, and an unrequested caption or title.

Required scientific legends and labels are content. Never remove them merely to
reduce clutter; repair their layout instead.

OUTPUT
- Verdict: ACCEPT, REVISE, or REJECT.
- Scientific and label findings, each tied to a source or manifest item.
- Presentation findings.
- Corrections for the next round, ordered by impact.
- Accepted features that the next round must retain.

Use ACCEPT only when scientific content is correct. A purely typographic generator
artifact may be accepted with an explicit native-text correction from the exact-label
manifest; an ambiguous or missing scientific label remains a blocker.
```

## Selector: freeze the reference

```text
Compare all candidate images and their critiques against the fixed brief. Select
the best candidate that has no unresolved scientific error. Carry any explicitly
accepted typographic corrections from the exact-label manifest into the redraw. Do not
prefer a candidate because it is newest. State the selected round, source-backed
reason, remaining non-blocking visual limitations, pixel dimensions, and the
provenance fields that must be recorded. If no candidate is scientifically correct,
return BLOCKED and list the unresolved errors; do not select one.
```

## Penpot redraw reviewer

Before review, the redrawer follows [penpot-redraw.md](penpot-redraw.md), recreates the selected image
with native Penpot objects, and exports a same-size PNG for comparison.

```text
Compare the current Penpot export with design-selected.png at the same dimensions.
Check canvas and layout, icon geometry, color and gradient stops, typography,
connectors, line weights, spacing, labels, legends, and hierarchy. Check that all
content is native editable vector geometry or imported native plot SVG, with no
embedded raster standing in for the drawing. Return targeted native edits in impact
order. Treat the selected design as fixed. Permit a label difference only when the
brief's exact-label manifest corrects a known raster glyph error, and record it as a
QA exception.
```
