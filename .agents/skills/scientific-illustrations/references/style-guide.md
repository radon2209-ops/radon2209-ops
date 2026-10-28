# PaperBanana style observations from NeurIPS 2025

Adapted from [PaperBanana](https://arxiv.org/abs/2601.23265) (Zhu et al.,
2026), Appendix F. The paper's Stylist agent used these observations as its
aesthetic guideline, G.

Use this as an option library for figures that suit the paper's sampled NeurIPS
2025 conventions. It is not a NeurIPS requirement or a general scientific style
standard. Start with the user's reference, scientific meaning, required labels
and legends, accessibility needs, and publication constraints. Do not import a
palette, icon, shape, or line meaning without checking that it fits the figure.
After design selection, the Penpot redraw follows the selected image rather than
restyling it from this guide.

---

## Part 1: Methodology Diagrams

### 1. Observed visual character

Appendix F describes one common pattern as "Soft Tech & Scientific Pastels":
light backgrounds group related content, while stronger color marks emphasis.
The sampled diagrams also use modular grouping and clear directional flow. Treat
this as one option when the user supplies no stronger style reference.

### 2. Style options

#### A. Color palettes

Use color to group logic and encode meaning. Avoid saturated backgrounds when
they reduce contrast or compete with the content.

**Background fills and zones**

Light, desaturated fills can separate stages or environments. Cream, pale blue,
mint, and lavender are examples from Appendix F. White regions with colored
borders are another option. Use exact colors from the user's reference when one
exists, and choose opacity from the target medium and required contrast.

**Functional colors**

The appendix lists several contrasting, medium-saturation color pairs. Define
their meaning from the source or reference, retain any required legend, and use
strong saturation only where emphasis is intentional. Do not infer trainable,
frozen, input, output, or error states from hue alone.

#### B. Shapes and containers

Use geometry consistently so shape differences carry a clear meaning.

**Core components**

- **Process nodes:** Rounded rectangles are one common option for layers or
  steps. Set corner radius in proportion to the canvas and reference.
- **Tensors and data:** Stacks or cuboids can imply depth; flat grids can depict
  matrices, tokens, or attention maps; cylinders can depict stores. Use these
  associations only when they fit the brief.

**Grouping and hierarchy**

- **Macro-micro:** A light container can hold the global view while a connector
  leads to a detailed breakout of one module.
- **Borders:**
  - **Solid:** One option for concrete components or primary groups.
  - **Dashed:** One option for logical stages, optional paths, or scope boundaries.

#### C. Lines and arrows

Assign line styles from the source semantics, then use them consistently.

**Connector styles**

- **Orthogonal or elbow:** Useful for dense network architectures and aligned
  tensor flows.
- **Curved or Bezier:** Useful for feedback loops or high-level connections.

**Line semantics**

- **Solid black or gray:** An observed choice for primary forward flow.
- **Dashed:** May indicate gradients, skip connections, losses, uncertainty, or
  another secondary relation. A required legend or explicit label defines the
  meaning; dashed lines have no universal scientific semantics.
- **Integrated math:** Operators can sit on a line or intersection when their
  operation is explicit and the notation matches the source.

#### D. Typography and icons

Keep typography legible and distinguish prose labels from mathematical notation
when that distinction matches the manuscript.

**Typography**

- **Labels:** Sans-serif faces such as Arial, Roboto, or Helvetica are common;
  bold can distinguish headers from details.
- **Variables:** Serif italic is an option for matching LaTeX notation. Follow
  the manuscript, venue, or supplied reference rather than changing notation to
  satisfy this guide.

**Iconography**

Use icons only when their meaning is clear from the brief or reference. Build
them as editable vector objects for the final Penpot figure. Keep labels or a
legend where an icon could be ambiguous. Do not replace a required scientific
structure with a generic decorative symbol.

### 3. Potential mismatches

- Heavy outlines and saturated preset colors can compete with small labels.
- Unplanned font mixing weakens hierarchy and can change math meaning.
- Mixing flat and isometric geometry needs a semantic reason, such as flat shapes
  for logic and cuboids for tensors.
- Saturated grouping backgrounds can reduce contrast.
- Identical connectors for relations with different meanings create ambiguity.

### 4. Domain-specific styles

Appendix F reports different visual patterns across domains. These are options,
not subject-area requirements.

**Agent or language-model papers**

- Illustrative or narrative treatments can fit user-facing workflows.
- Chat bubbles and document icons can represent prompts or retrieval.
- Characters or avatars should appear only when they clarify the process and fit
  the requested tone.

**Computer vision or 3D papers**

- Spatial, dense, geometric layouts can show frustums, rays, and point clouds.
- RGB axis conventions or heatmaps should follow the source data and field
  convention. Choose a color map appropriate for the encoded values.

**Theoretical or optimization papers**

- Minimal, abstract layouts can emphasize graphs, manifolds, and equations.
- Grayscale with one highlight color can keep attention on structure.

---

## Part 2: Statistical Plots

### 1. Observed plot priorities

Appendix F emphasizes precision, accessibility, and contrast. These priorities do
not define one visual style.

- **Backgrounds:** White and light gray are both reported options. Choose for the
  target medium and contrast requirements.
- **Accessibility:** When readers must distinguish series without color, combine
  color with patterns, line styles, direct labels, or marker shapes.

### 2. Style options

#### Color palettes

- **Categorical data:**
  - **Soft pastels:** Salmon, sky blue, mint, and lavender.
  - **Muted earth tones:** Olive, beige, slate gray, and navy.
  - **Higher-contrast colors:** Useful when categories need clear separation.
  - **Redundant encoding:** Hatches, dots, stripes, or shapes can supplement color.
- **Sequential and heatmaps:**
  - **Sequential:** Perceptually uniform maps such as Viridis, Magma, or Plasma
    are common options.
  - **Diverging:** Use a meaningful neutral midpoint and verify that both
    directions remain distinguishable.
  - **Rainbow maps:** Avoid them when uneven perceptual steps would distort value
    comparisons. Retain them when the user or domain standard requires them and
    the mapping remains scientifically clear.

#### Axes and grids

- **Grid style:**
  - Light dashed or dotted lines, or no grid, are common options.
  - Keep grids behind data marks when present.
- **Spines:**
  - **Boxed:** Four visible spines provide a complete frame.
  - **Open:** Removing top and right spines reduces visual weight.
- **Ticks:** Subtle inward ticks and grid-aligned plots without ticks are both
  observed choices.

#### Layout and typography

- **Font family:** Sans-serif faces such as Helvetica, Arial, and DejaVu Sans are
  common. Match the manuscript or supplied reference when it uses another face.
- **Label rotation:** Keep labels horizontal when they fit. If they overlap, use
  rotation, wrapping, spacing, or another layout supported by the reference.
- **Legends:** Place required legends where they do not occlude data. Reported
  options include a free corner inside the axes or a horizontal row above them.
- **Annotations:** Direct labels can reduce lookup when they remain legible.

### 3. Plot-type options

#### Bar charts and histograms

- **Borders:** Outlined and borderless bars are both observed options.
- **Grouping:** Set bar and group spacing so categories remain distinguishable.
- **Error bars:** Use the analysis-defined uncertainty, cap style, and color.
  Keep it legible without overpowering the data.

#### Line charts

- **Markers:** Add geometric markers when individual samples matter or sparse
  points would otherwise be ambiguous.
- **Line styles:** Use solid, dashed, or dotted lines according to source-defined
  series meaning. Preserve or add a required legend.
- **Uncertainty:** Shaded bands and error bars are both valid. Use the encoding
  defined by the analysis and label what it represents.

#### Treemaps, pie charts, and donut charts

- **Separators:** White borders can separate slices or treemap blocks.
- **Structure:** Pie and donut forms are reported options; choose the form that
  communicates the intended comparison.
- **Emphasis:** A detached slice can highlight a specified statistic, but it
  must not imply unsupported importance.

#### Scatter plots

- **Shape coding:** Marker shapes can encode a categorical dimension alongside
  color when the mapping is defined.
- **Fills:** Solid markers work for separated points; transparency can show
  overplotting.
- **3D plots:** Use walls, grids, or drop-lines only when depth encodes real data.

#### Heatmaps

- **Aspect ratio:** Square cells help when row and column dimensions are directly
  comparable; other aspect ratios may fit the data or available space better.
- **Annotation:** Exact values can appear inside cells when requested and legible.
- **Borders:** Borderless cells and thin separators are both observed options.

#### Radar charts

- **Fills:** Translucent fills can preserve grid visibility. Choose opacity from
  the number of series and overlap.
- **Perimeter:** A darker boundary can distinguish the polygon from the grid.

### 4. Plot checks

- Do not use 3D effects or shadows that alter perceived values.
- Check color maps for perceptual ordering, accessibility, and domain meaning.
- Add markers when sparse samples are otherwise ambiguous.
- Add a non-color channel when the accessibility requirement calls for one.
- Reduce or remove grid lines when they compete with the data.
