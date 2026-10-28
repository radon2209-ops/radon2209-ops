# Redraw the selected design in Penpot

Read this after the image-generation critique loop has selected a design. The
selected image is the visual target; the source brief and exact labels remain
the authority for scientific content. Preserve that image and its checksum.

## Connect and inspect

Use the exposed Penpot MCP tools. Read their overview and the API documentation
for the shapes and export operations needed by this figure. Confirm the active
file and page before writing. Tool names and API members can vary by version;
check the available schema rather than assuming a remembered method exists.

If MCP is not connected, check an existing configured Penpot instance and its
plugin before setting up another instance. Use the current official
[MCP guide](https://help.penpot.app/mcp/). Keep setup within the task's existing
authorization. A missing connection does not justify claiming a Penpot redraw
or delivering an embedded image as editable vectors. Retain the selected design
and report the specific remaining connection or permission requirement.

For a local setup, bind the HTTP, plugin, and WebSocket listeners separately to
loopback. Some local MCP versions ignore the HTTP host setting for WebSocket.
Keep the owning browser tab active while using MCP. Demo accounts can expire;
export a durable native file before ending the session.

## Reconstruct objects, preserving appearance

1. Inspect the selected image at full size and inspect dense regions as crops.
   Record its canvas size, object bounds, alignment, color/gradient stops,
   line widths, connector endpoints, typography, and layer order in the run
   record. Use proportions to map pixel coordinates to the Penpot canvas.
2. Create a board with the same aspect ratio. If useful, import a locked
   reference onto a separate page or outside the export board. Keep it separate
   from the actual drawing and exclude it from the figure export.
3. Build each visible object with native rectangles, ellipses, paths, fills,
   strokes, gradients, and text. Name objects by meaning and group related
   objects without merging unrelated parts. Draw complex contours when needed
   to match the reference; do not replace distinctive icons with generic symbols
   merely to reduce object count.
4. Preserve gradient direction, extent, stops, and transparency with native
   gradient fills. A triangular wedge should usually be one closed three-corner
   path with a gradient, not hundreds of color-band fragments. Retain complex
   geometry where the reference actually requires it.
5. Recreate labels as editable text using the exact-label inventory. Match font
   family, weight, style, size, line breaks, and placement. Correct generator
   spelling artifacts from that inventory and record the correction. Inspect
   actual text bounds after layout settles; missing fonts and asynchronous
   layout can change wrapping and alignment.
6. Preserve arrow direction, branching, dashed/solid meanings, legends, panel
   labels, and biological structures. Keep quantitative plots generated from
   their source data as vector assets; do not redraw measured curves or invent
   microscopy detail from a generated concept image.

Match the reference with objects that remain useful to edit. Preserve the
selected composition and recognizable icon details during this phase. If a
scientific problem requires a design change, resolve and record the correction
explicitly; do not silently replace the reference with a new layout.

## Compare, correct, and prove editing

Export a preview through Penpot and compare it with the selected image at the
same dimensions. Inspect the full figure side by side, then use overlays or
aligned crops for important differences. Check geometry, relative positions,
icon details, colors, gradient behavior, text, and connectors. Fix the largest
visible mismatch in the native objects and compare again. Retain previews and
the critic's observations; do not choose a candidate solely by a global pixel
score dominated by empty background.

Use the agreed refinement budget and report visible residual differences if
the budget is reached. Do not report full fidelity while critical scientific
content is missing or unreadable. An independent visual critic is useful for a
complex figure; it must inspect the rendered image, not just element counts.

Before delivery, select and move a representative object or group, confirm that
its intended children follow, edit a text label, and edit a fill or gradient
stop. Restore every test change and verify the restored appearance and values.
The final SVG must contain real geometry and editable text, not a hidden raster
or text entirely converted to outlines. Keep gradients editable as gradients.

## Export and verify the saved files

Save `figure.penpot`, `figure.svg`, and `figure.png` beside `design-selected.png`.
Include the run record, needed licensed fonts, and short editing instructions.
Wait for Penpot to save before downloading the native file. Inspect or reopen
that file to confirm it contains the latest shapes and excludes temporary test
objects. Verify the written SVG parses, preserves labels, has no raster objects
on the final figure board, and does not depend on private or localhost URLs.

Render the saved SVG outside Penpot, preferably in the user's target editor.
Check text, gradients, clipping, and completeness there. Record the target
renderer, result, and font requirements. Browser font embedding may not provide
the typeface in desktop editors; include licensed font files when needed.

## Compatibility notes from a tested redraw

Check for these observed failure modes when the corresponding operation fails:

- A font name search matched `Roboto Mono` for `Roboto`. Use an exact family
  match and verify the applied family and variants on the actual text object.
- A documented layout-wait method was absent in the connected runtime. Consult
  the live API and wait for layout using a supported method before reading bounds.
- One MCP SVG export wrapper serialized byte data incorrectly. The native
  `shape.export({type: "svg", scale: 1})` still worked through `execute_code`.
  Returning `Array.from(bytes)` across that bridge and decoding the array as
  UTF-8 on the client preserved the SVG. Validate file content rather than
  trusting the tool's success message. Do not assume `TextDecoder` is available
  inside the plugin sandbox.
- Penpot exported a gradient through a same-size SVG pattern and referenced
  fonts on its local server. Where present, normalize the pattern to an
  equivalent direct gradient, preserve object names, and make fonts portable.
  This is export preparation of the Penpot drawing, not a separate redraw.
  Re-render after normalization to check that geometry and appearance agree.
- A native-file download raced the deletion of test objects. Re-download after
  persistence and check the saved document, not just the current canvas.

Keep any compatibility changes small and tied to a reproduced issue. Preserve
the raw export for diagnosis and distribute the verified portable export.
