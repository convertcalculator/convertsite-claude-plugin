# Quality review

Review the rendered result, not only its component tree.

For a new build or broad redesign, apply all relevant ship checks below. For a bounded edit, apply them to the changed regions and affected dependencies; reuse valid evidence for unchanged regions instead of rerunning the entire matrix. Repair regressions caused by the change, and report unrelated pre-existing issues without silently expanding scope. Completion claims must match what was actually checked.

## Required rendered matrix

- Inspect at least one common laptop viewport and one narrow mobile viewport around 390-412 px.
- At each width, inspect the first viewport, the primary interactive or choice module, and the final conversion endpoint.
- Exercise default, hover, focus-visible, active or pressed, selected, error, disabled, expanded, and collapsed states that exist. Test every distinct CTA variant and every repeated interactive-control family; do not infer all states from one representative control. Use the longest real labels and copy, not only the shortest case.
- For every interactive state, inspect the rendered foreground/background pair on the actual text and icon descendants. A parent background change does not preserve contrast when a child keeps a locally assigned foreground color. Define paired foreground and background values for hover, focus, active, and selected states when inheritance cannot guarantee legibility.
- On mobile, verify readable reflow rather than only absence of horizontal overflow. Reject squeezed multi-column cards, awkward word stacking, clipped CTA text, overlapping labels, and controls whose content escapes their bounds.
- Apply the rendered collision check from `layout-rhythm-contract.md` at desktop and mobile widths. Reject zero or negative separation between distinct text rows, headings and labels, labels and controls, field groups, or content and actions; screenshot inspection must also confirm that glyph overhang does not create a visual collision.
- Apply the rendered containment gate from `layout-rhythm-contract.md`. Measure every visible control against its owning layout container and neighboring siblings; reject a control that crosses its parent boundary or enters an adjacent column, card, result rail, label area, or action region. A page with no horizontal overflow can still fail this gate.
- Apply the container-fit check from `layout-rhythm-contract.md` to navigation, utility strips, announcements, compact headers, divider bands, and other shallow elements. Reject generic section padding, stacked wrapper padding, or inherited `min-height` that makes a low-content band disproportionately tall.
- Measure the longest CTA label inside its rendered button at desktop and mobile widths. It must retain intentional inline breathing room on both sides, including beside an arrow or icon. Reject controls that technically contain the text only by collapsing horizontal padding, squeezing type, or fixing the width to the text measurement. Prefer intrinsic width with a viewport-safe maximum, or full width on narrow screens; allow clean wrapping and height growth when needed.
- Inspect affected native fields to identify which element owns the visible shell. Text/email fields may use `input`; number and compound controls may use `wrapper`. Reject double borders or competing inner surfaces; put the shell on the observed owning element only, as specified in `mcp-build-contract.md`.
- Record enough direct evidence to support completion claims. Do not say “responsive,” “accessible,” “working,” or “verified” based only on the component tree or a desktop render.

Record completion evidence as a compact matrix of viewport, user-facing state, functional scenario, and observed outcome. A successful component-tree or XML read-back is structural evidence, not rendered or behavioral evidence. When the required render or interaction cannot be inspected, mark that check unresolved and narrow the delivery claim accordingly.

## Conversion

- Can a new visitor identify the offer, relevance, and primary action immediately?
- Is one action visually primary?
- Is proof close to important claims?
- Are major objections handled before the final CTA?
- Do visual choices strengthen rather than compete with the message?
- Are forms and interactive modules easy to find and use?
- Does the primary CTA lead to a form, booking flow, checkout, contact action, or another usable completion point?
- Can the visitor complete the intended action rather than only scroll to more information?
- When the brief distinguishes primary and secondary journeys, do they remain distinct instead of silently converging on the same fallback endpoint?
- Does public copy avoid leaking internal build sequencing or adding unrequested “coming soon”, waitlist, launch-status, or availability claims?
- When a later destination is outside the current scope, does the current endpoint still provide a coherent visitor outcome without pretending that destination exists?
- Does the presentation mode minimize navigation while preserving comprehension? Treat a calculator as `single_surface` unless progressive disclosure or separate views produce a concrete reduction in cognitive load.
- For every staged flow, is there still a qualifying reason such as a real sequential dependency, excessive post-compaction length, an intentional conversion gate, or an explicit user requirement? Reject staging based only on visual neatness, conceptual phases, or the existence of a result state.
- Can users relate frequently adjusted inputs and assumptions to the result without unnecessary backtracking? Reject a result-only view that contains an output-determining control while hiding the other inputs it works with, unless the staged task genuinely requires that separation.

## Hierarchy and attention

- At desktop and mobile widths, can a reviewer name the intended first, second, and third reading targets within three seconds? Reject a viewport when two or more independent regions plausibly claim first priority.
- Does the first-priority element or region remain dominant in grayscale and in a quick squint or thumbnail view? If hierarchy disappears without color or close reading, repair scale, spacing, placement, or grouping.
- Is font weight supporting hierarchy rather than carrying it alone? Reject modules where headings, option labels, result copy, metadata, and buttons cluster around the same semibold or bold weight.
- Are body copy and helper text visibly quieter than questions, recommendations, and actions while remaining readable? Do not solve hierarchy by lowering contrast below accessible levels.
- In choice-to-result modules, is the current question easiest to act on, the selected state easiest to relocate, and one recommendation easiest to interpret? Rationale, specifications, proof, and refinement should follow in that order or be progressively disclosed.
- When a result rail contains several surfaces, is only the answer visually dominant? Reference material and next-step detail must not look like co-equal primary outcomes.
- Do spacing and grouping make related content read as one unit, with a larger gap before the next priority tier? Reject layouts that depend on borders around every item to create structure.

## Distinctiveness

- Does the rendered result clearly express the selected creative position, rather than drifting toward the rejected alternative or a generic category average?
- Can the selected design direction be named from the screenshot alone?
- Is there one recurring signature motif?
- Does the page avoid repeating “heading + paragraph + three cards”?
- Do section scale, density, and composition vary intentionally?
- Are typography and imagery specific to the brand rather than generally tasteful?
- Would replacing the logo make the site feel like a different brand? If not, strengthen art direction.
- Is there a memorable compositional idea beyond large type, a bright accent color, or a large photograph?
- Does the result feel intentionally made for this business rather than like a polished theme demo?

## Visual communication

- Does each major section use the clearest carrier for its idea, rather than defaulting to another heading, paragraph, and card row?
- Beyond the opening hero, does a multi-section page contain meaningful visual information such as illustration, diagram, process visualization, category symbols, verified data, interface preview, or interaction where appropriate? Atmospheric photography establishes tone but does not by itself count as informational variety.
- Are two or more consecutive text-dominant sections repetitive enough that they should be shortened, merged, or given a more visual explanation?
- When a section contains three or more categories, steps, choices, comparisons, or future tools, does it have a scannable visual system rather than homogeneous text cards alone?
- Do icons and decorative assets clarify category, sequence, evidence, or action? Generic icons added only to make the page look less empty do not count.
- Does “premium restraint” still provide visual rhythm and information variety instead of becoming visual austerity?
- Is the copy volume appropriate for a homepage, with secondary explanation deferred or progressively disclosed when it interrupts scanning?

## Coherence

- Does the first viewport establish the visual system used later?
- Are image crops, color treatment, borders, corners, and spacing consistent?
- Are exceptions purposeful?
- Is the secondary influence subordinate to the primary direction?

## Safety and behavior

- Verify formulas, defaults, references, conditions, tabs, accordions, and result states.
- Verify collapsed and expanded states at relevant widths.
- Check that content cannot force columns wider than intended.
- Check contrast in every rendered interaction state, readable type sizes, focus clarity, touch targets, and text reflow with the longest labels. Hover and selected-state contrast must be verified separately from the default state.
- Verify that selectable controls expose their selected state programmatically, not only through color or borders.
- Verify that form controls have persistent programmatic labels and the intended semantic component type; placeholders alone do not count as labels. Verify accessible validation messages only for authored or changed validation behavior.
- Check that large media and motion do not create avoidable loading or interaction delay.

Treat unchanged native component behavior as platform-owned. Do not spend review time revalidating built-in internals such as email-format validation unless the task changed that behavior or the rendered experience shows a regression.

If ConvertSite cannot represent a required semantic or behavioral primitive, report it as an unresolved platform limitation. Do not omit the failure from the final message or convert “visually appears correct” into an accessibility or functionality pass.

## Revision rule

- In standard mode, repair functional, responsive, accessibility, and conversion failures without adding a separate aesthetic generation pass. When the chosen direction is not identifiable or the logo-replacement test fails, make one focused compositional or brand-specific correction as part of the initial build; do not regenerate the whole page.
- In explore mode, apply `creative-quality-bar.md` and perform at most one focused revision of the weakest underlying cause when the result fails its ship bar.
- Do not globally restyle the whole site unless the selected direction itself is the problem.
