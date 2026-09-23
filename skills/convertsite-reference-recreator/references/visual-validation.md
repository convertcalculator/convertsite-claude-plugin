# Visual validation

Compare reference and target at matched viewport dimensions.

Run the full applicable pass for a new or broad recreation. For a bounded correction to an established recreation, verify the changed regions, shared consumers, and affected behavior after each coherent batch. Reuse valid evidence for unchanged regions; broaden checks when a failure or dependency warrants it. Preserve the existing discrepancy ledger and comparison-round limits. A passing local correction does not close unrelated unresolved items or certify an unfinished site.

## Pass order

### 1. Silhouette

- Header and hero height
- Section sequence and relative heights
- Full-bleed versus contained regions
- Major light and dark blocks
- Image and text mass distribution

Before passing silhouette, confirm section topology and repeated-item counts.
Matching outer blocks cannot pass when the internal component model differs.
Also compare each section fingerprint. Equal height does not pass when a
contained panel became full-bleed, an image-free section gained media, or a
terminal card inherited the default card structure.

### 2. Geometry

- Content width and margins
- Column ratios and alignment
- Gaps, padding, overlap, and image aspect ratios
- CTA position and scale
- Internal card zones, text/media order, visible neighboring items, and overflow axis
- Parent padding ownership and direct-child offsets; a matching text position
  does not pass when media begins at a different top or left inset

### 3. System

- Typography scale, weight, line-height, and line breaks
- Computed font family and exact available weight; a visually similar category
  does not pass when it causes different wrapping or density
- Color roles and contrast
- Borders, radii, shadows, and control treatment
- Image crop and overlay behavior

For typography, keep a rendered text-style ledger covering every distinct
treatment and every local exception. Compare computed family, loaded font face,
real available weight, size, style, line-height, tracking, casing, color,
opacity, alignment, text width, wrapping, and line count. Check font-face
availability rather than accepting a requested family or weight at face value.
Include visible `::before` and `::after` content and motifs. A typography pass
fails when the target depends on a missing face, synthetic weight, different
wrap, or omitted pseudo-element.
For high fidelity, record numeric computed styles at the same viewport for at
least the hero heading, section heading, repeated-card heading, body text,
button, final CTA, and footer heading in both reference and target. Require the
font family and weight to match exactly; fail when font size or line-height
differs by more than the larger of 1 CSS pixel or 2%. Sample both an early and
late occurrence of repeated text roles so a correct upper page cannot hide
typography drift near the bottom.
Compare pseudo-element owner, geometry, exact color, opacity, and breakpoint
visibility. An inherited dark marker does not pass an observed accent-color
square.

### 4. Behavior

- Navigation and sticky behavior
- Responsive reordering and collapse
- Interactive states observed in the reference
- Target forms, calculators, defaults, conditions, and conversion endpoint

For sticky, fixed-layer, or overlapping sections, do not validate from XML alone:

1. At scroll position `0`, record the flow section height, visual hero layer height and width, following-section top, border radius, computed positions, and stacking order.
2. Scroll to two known offsets and re-read the same rectangles and computed positions.
3. For the fixed section-background pattern, pass only when `background-image` and `content` remain at viewport `top: 0`, the `100vh` flow section moves normally, and the following section moves toward and over the hero.
4. At an overlap position, use a hit test such as `elementFromPoint` to confirm that the topmost element belongs to the following section.
5. Confirm the same relationship at the mobile viewport and check that no desktop spacer or negative-margin compensation reappears.

For sticky or fixed multi-region headers, validate every region independently at
scroll position `0` and two known offsets. Record each rectangle, computed
position, top offset, stacking order, and the normal-flow spacer. Both the
utility bar and primary navigation must reproduce their observed visibility and
motion without covering the first content section. Do not force either region
to remain visible when the reference hides or translates it after scroll.

For hover states, saved XML alone does not pass. Confirm the rendered stylesheet
contains the expected `:hover` selector and value, then verify the computed state
with a real pointer movement when the browser surface supports it. If pointer
state is unavailable, record the CSS verification and the unobserved live state
separately.

For hover states that resize siblings, also verify the rendered parent display,
base child flex values, hovered flex rule, transition duration, desktop resting
widths, and mobile stacking. A valid hover rule on a child does not pass when a
generated grid parent keeps all columns fixed.

For full-bleed regions, verify both the section and its content wrapper span the intended viewport width. If preview is PIN-gated or otherwise inaccessible, publish the current completed iteration only when the active publication mode authorizes it, then validate through the published URL. Otherwise state that the behavior is structurally unverified or request access; do not describe it as visually confirmed.

## Comparison rounds

- Inspired: 0 unless explicitly requested
- Close: 1
- High: up to 2

In each round, fix the largest perceptual mismatch first. Do not spend a round polishing icons while macro geometry is wrong.

Maintain a validation ledger across all rounds. Every observed discrepancy must remain visible until it is:

- applied and verified on the rendered target, or
- explicitly reported as an accepted approximation.

Run both a full-page comparison and component-level checks. For every major component verify its container, media crop and framing, typography hierarchy, semantic component type, and relevant interaction states. In headers and footers, confirm that every observed navigation, legal, contact, and social action is a real link with the intended destination type; matching text alone does not pass. Consolidate all open items into one correction batch per round; do not use serial publish-and-fix cycles for individual details.

Give the footer its own section-level validation row. Compare newsletter and
field layout, consent text, brand/social placement, navigation-group and item
counts, divider geometry, legal-link order, copyright alignment, total height,
and mobile column collapse. Also compare card content zones in both resting and
active states; an image-overlay title cannot pass for a below-image title.
For the form, compare rendered control count, order, semantic type, labels,
required state, button, consent copy, desktop row structure, and mobile stacking.
For native fields, inspect whether `input` or `wrapper` owns the visible shell
and verify that only that element carries the border and background. Fail on a
double border or competing inner surface. Do not retest unchanged
platform-owned internals such as built-in email-format validation; validate only
authored rules, changed configuration, integration behavior, or a visible
regression.

For split cards, record the rendered outer rectangle, computed four-side
padding, and the text and media child rectangles. Fail the geometry pass when
the target achieves a similar text inset through child padding while the
reference pads the outer shell, or when adding the inset changes total height.
Keep the outer rectangle, four-side padding, direct-child rectangles, media
rectangle, and total height in one row; every value must pass together.

For every media-bearing section, compare required media-slot count with loaded,
non-zero target images and verify section-level provenance. Fail on missing
images, zero-sized images, cross-section substitutions, or extra images in a
reference section that intentionally has none.

For unsupported carousel fallbacks, validate the recorded fallback rather than
the unavailable original primitive. A horizontal-scroll fallback passes only
with the full item count, one overflow-x rail, stable card widths, preserved
order and zones, touch scrolling, and no misleading nonfunctional carousel
counter or navigation controls.
Validate responsive card geometry with a minimum three-width matrix: one fluid
desktop width, one intermediate width, and one width beyond the observed
max-width cap; add mobile when the topology changes. Compare absolute values,
normalized ratios, and the inferred dimension class. Check every repeated card
for equal shell behavior. Fail when a target matches one sample but diverges in
growth rate, aspect ratio, cap position, or content-driven expansion. For high
fidelity, use a tolerance of the larger of 2 CSS pixels or 0.5% for primary
container, padding, and media dimensions unless a documented platform
constraint requires otherwise.

When the page has more than four structurally distinct sections, organize the
work into internal batches, but keep one ledger spanning all batches. Do not let
batch boundaries drop already observed discrepancies or make the user repeat
them.

For high fidelity, keep a section comparison table with one row per major
section and these minimum fields: `component_family`, `item_count`,
`internal_zones`, `media_geometry`, `overflow_behavior`, `desktop`, and
`mobile`. A section passes only when every observed structural field matches or
has a recorded, proven platform constraint. Validate composition-heavy sections
with a section-level screenshot or equivalent bounded DOM geometry check; a
full-page screenshot alone is insufficient.

At every validation viewport, add a global geometry row for each major section:
`top`, `height`, `container_width`, `side_margins`, and `following_gap`, plus the
total page height. Fail when individually plausible sections produce cumulative
vertical drift or inconsistent shared alignment lines.

Keep a breakpoint state matrix for all major components with at least
`visibility`, `order`, `column_count`, `navigation_mode`, `cta_presence`, and
`interaction_revealed_content`. A responsive pass requires the observed
re-composition, not merely a layout that avoids overflow.

## Pre-handoff gate

Before the first user-facing handoff, require all of the following:

1. Structural-completeness audit for every major section.
2. Rendered typography and font-face ledger.
3. Breakpoint state matrix at every validation viewport.
4. Section-level geometry and interaction checks.
5. Full-page geometry and cumulative-drift check.
6. No unresolved ledger item without a concrete proven platform constraint.
7. Media-slot and asset-provenance audit, including explicitly image-free sections.
8. Repeated-family variant audit for default, featured, terminal, resting, and active states.
9. Form-control contract audit for every form-like region.

Consolidate discovered mismatches into no more than two internal correction
batches before handoff. Saved XML or editor configuration is evidence of intent,
not evidence that any gate has passed.

## Delivery

State the fidelity achieved, important approximations, viewports checked, any unobserved reference states, and which validation iterations were published. Do not declare completion with any unresolved or unreported ledger item. Publish correction rounds only when `publication_mode: validation_loop` is active or the user gives new explicit permission.
