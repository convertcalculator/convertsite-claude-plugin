# ConvertSite MCP recreation contract

## Safety and scope

- Treat the reference as read-only.
- For a new build, create a separate unpublished target.
- For an edit, inspect and mutate only the user-designated target.
- Do not inspect unrelated workspace sites.
- Default to `publication_mode: prohibited`. Explicit no-publish wording always overrides other authorization.
- With `first_iteration`, publish only the first completed iteration. With `validation_loop`, publish each completed validation iteration within the selected fidelity's comparison-round limit.
- Verify the exact target app identifier against current state before every publish, then use its published URL for rendered validation. This is an internal check; request approval only if the existing authorization does not cover that publish. Never publish a partial or knowingly broken iteration.
- Inspect affected formulas, references, themes, stylesets, states, and dependencies before editing an existing target.

## Build order

Use this order for new or broad recreations. For a bounded correction, reuse the established blueprint and inspect the affected regions and dependencies; apply a coherent correction batch without rebuilding unchanged sections. Keep the selected fidelity, source protections, and publication limits.

1. Create macro page structure and section geometry.
2. Reproduce each section's component topology, internal zones, complete repeated-item count, and overflow model.
3. Establish grid, widths, spacing, and responsive transformations.
4. Map target content into the reference hierarchy.
5. Establish typography roles and scale.
6. Place media with matched aspect ratios, framing, layering, and crop behavior.
7. Apply colors, surfaces, borders, radii, and shadows.
8. Recreate observable interactions and states that matter to the target experience.
9. Connect the target conversion endpoint.
10. Run the structural-completeness audit before publishing, then validate and consolidate all open discrepancies into one correction batch per allowed round.

## ConvertSite mapping

- Translate the reference visual system into semantic ConvertSite design-system variables before styling repeated components. Map typography, color roles, surfaces, borders, radii, shadows, spacing, and control dimensions.
- Make shared stylesets and components reference those variables rather than repeating resolved literal values. Use local values only for genuine one-off geometry or a reference detail without a suitable semantic variable.
- For edits, preserve existing target variables unless the requested recreation explicitly requires a scoped design-system change; inspect dependencies before changing any shared variable.
- Prefer existing ConvertSite primitives and shared styles that reproduce the observed relationship.
- Do not substitute a simpler component family merely to reduce authoring cost.
  Before approximating a composite or dynamic section, check the source asset
  inventory and relevant native primitives, then record the concrete limitation.
- For repeated or interactive patterns, inspect native component capabilities and style elements before constructing a visual approximation. Use state-specific style overrides for observed active, checked, open, or selected states.
- Do not force every repeated item through one template when the reference has a
  featured or terminal variant. Share tokens and shells where appropriate, but
  preserve each variant's topology and media treatment.
- Do not call `SetTheme` routinely when editing an existing target.
- Use a local approximation when a reference feature lacks a native equivalent.
- Avoid broad tree replacement when a local correction can restore fidelity.
- Preserve formulas, defaults, user overrides, conditional visibility, and responsive behavior.

## Structural-completeness audit

Before the first publish, compare the built tree with the reference blueprint.
Fail the audit when any major section has:

- a different component family or wrong text/media order
- missing or extra repeated items
- missing internal zones that create the observed card depth or hierarchy
- media on the wrong side, with the wrong framing, or omitted without a recorded constraint
- missing horizontal overflow, clipping, neighboring-card visibility, or controls
- missing or extra media compared with the section's media-slot count
- a default repeated-item template applied to a featured or terminal variant
- a section fingerprint borrowed from another section, including an image added
  to an image-free CTA or a full-bleed treatment replacing a contained panel
- an unsupported carousel represented as a one-item view when a horizontal rail
  is the selected fallback
- a form whose field count, order, semantic types, labels, consent, or responsive
  arrangement differs from the control contract

Do not use approximate section height as a substitute for this audit.

For high-fidelity builds, use an unpublished proof checkpoint before bulk
styling: author the header/hero and one composition-heavy repeated section, read
their ConvertSite trees back, and compare them with the topology blueprint.
Repair the mapping at this point rather than repeating the same structural error
across every section. Do not publish this partial checkpoint.

For `close` fidelity, run the same proof checkpoint for any split-card,
interactive, or variant-bearing family. A family may be duplicated only after
its rendered box model, media slots, resting state, active state, and terminal
variant pass.

## Layout and component traps

- A full-width child does not escape a constrained section content container. For full-bleed regions, inspect and, when needed, set the section `content` element to block layout with zero margin/padding, visible overflow, no max-width, and full width.
- Do not assume `wrapper.position="sticky"` survives when a section has `background_image-asset`. ConvertSite may render that section wrapper as `position: relative` even while the saved XML still says `sticky`.
- Sticky navigation also depends on its generated ancestor chain. Audit ancestor
  overflow, containment, and component boundaries in the rendered page. When a
  ConvertSite section boundary prevents the observed multi-region sticky header,
  use a fixed utility/nav stack plus one explicit normal-flow spacer equal to the
  combined desktop and mobile heights. Verify both bars at the top and at two
  scroll offsets; never add an unresolved viewport-height spacer.
- When the reference shows a full-viewport hero that remains behind the following content, use this proven topology:
  - Keep the section in normal flow with `wrapper.position="relative"`, `wrapper.height="100vh"`, full width, and clipped overflow. This section is the only viewport-height spacer.
  - Put the image or video in the section's `background_image-asset` property.
  - Style the section's `background-image` element with `position: fixed`, `inset: 0`, `width: 100%`, `height: 100vh`, `object-fit: cover`, and a low z-index.
  - Style the section's `content` element with `position: fixed`, `inset: 0`, `width: 100%`, `height: 100vh`, clipped overflow, and a z-index above the background.
  - Keep the next section in normal flow with `position: relative` and a higher z-index so it scrolls over both fixed hero layers.
  - Keep fixed navigation above the foreground sections.
- Do not combine this topology with an empty `100vh` box, `margin-top: 100vh`, or negative mobile margin. Those compensations duplicate or distort the space already reserved by the hero section.
- Use a nested media layer instead only when the section-background pattern cannot express the required crop or interaction. Validate that alternative live before adopting it.
- Use explicit `min-width: 0` on constrained columns and explicit crop behavior on full-column media.
- Preserve box-model ownership. When the reference pads the outer card, apply
  that inset to the outer card rather than recreating the text offset with child
  padding. Reduce fixed child/media height when necessary so adding the parent
  inset does not inflate the observed total card height.
- Treat the measured four-side padding, direct-child offsets, media rectangle,
  and total card height as one indivisible contract. Do not approve a card when
  only its text alignment looks similar. Recheck the contract after responsive
  overrides and after inserting real content.
- Reproduce the measured responsive rule, not one sampled result. Prefer
  percentages for container-relative padding, aspect ratios for proportional
  media, and `min()`, `max()`, or `clamp()` only when multiple reference samples
  demonstrate a floor or cap. Re-read the rendered target on both sides of the
  inferred cap before accepting the mapping.
- Use semantic components for visible controls: `email` or `text-input` for fields, `link` for navigation, and `button` for actions. Decorative boxes may support layout but must not impersonate controls.
- For native controls, inspect the rendered component and available style elements to identify the visible shell owner. Text/email fields may use `input`; number or compound controls may use `wrapper`. Apply the border and background to that owner only; keep the other element layout-only with no competing surface. Do not prescribe wrapper ownership for every input type.
- Preserve the complete form-control contract: count, order, semantic type,
  labels, required state, action, consent, desktop row structure, and mobile
  stacking. Read the rendered inputs back before handoff.
- Do not retest unchanged platform-owned component internals such as built-in email-format validation. Test authored validation, changed configuration, integration behavior, or a visible regression.
- Build footer navigation, legal items, contact details, and social labels as real `link` components whenever they are presented as actionable in the reference. Preserve the appropriate destination type—page, anchor, external URL, `mailto:`, or `tel:`—and never downgrade them to text merely because text is easier to style.
- Do not compress a multi-zone footer into one newsletter column and one generic
  link grid. Reproduce each observed row and zone separately, reuse existing
  destinations, and validate new desktop width constraints at the mobile
  breakpoint. When a desktop `content.width` uses a viewport subtraction, add an
  explicit mobile width override so nested cards and footer grids do not remain
  artificially narrow.
- When target text should be near-black, set component-level heading, text, and link colors explicitly instead of relying on theme inheritance.
- Use state-specific style attributes such as `wrapper:hover.*` for observed
  hover treatments. Confirm that the generated rendered CSS contains the
  expected `:hover` selector and computed value. Also exercise the pointer state
  live when the validation browser exposes hover; if it does not, report that
  limitation instead of claiming live pointer verification.
- For sibling-resizing hover patterns, use one flex parent with equal base flex
  values and a larger hovered flex value so the remaining cards shrink
  automatically. Verify the rendered parent is actually `display: flex`:
  component-generated grid rules may override saved wrapper styles. If they do,
  replace only that repeated-item container with a neutral flex box while
  preserving every card, id, action, and responsive mobile stack.
- Bind required media before styling interactive cards. Fail the family when any
  resting or active item has an empty media slot, a zero-sized image, a failed
  load, or an asset copied from a different section. Verify the default item and
  every featured or terminal variant separately.
- For unsupported carousels, implement the explicitly selected fallback. When
  the fallback is horizontal scrolling, keep every item in one overflow-x rail,
  preserve fixed or capped card widths and scroll order, and validate touch and
  desktop overflow. Do not introduce carousel counters or controls that no
  longer operate on the chosen fallback.

## Conversion boundary

Follow the reference's visual treatment without reproducing a broken conversion path. Keep the user's primary action visible, understandable, and complete.
