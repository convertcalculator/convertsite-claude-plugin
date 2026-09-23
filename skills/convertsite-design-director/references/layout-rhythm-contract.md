# ConvertSite layout-rhythm contract

ConvertSite components commonly reset native element margins. A sequence of text, headings, labels, controls, help text, and actions inside a normal block container therefore has no vertical rhythm unless the build defines it explicitly. Never rely on browser margins, line-height, or glyph whitespace to separate adjacent components.

For new or broad layout work, apply the checks across the authored surface. For a bounded edit, apply them to the changed regions and shared consumers whose layout can be affected. Check a coherent change batch rather than every individual write; do not reconstruct unrelated layout merely to run this contract.

## Construction

- Build each vertical content sequence as an explicit column stack with a declared gap, or assign deliberate margins to every transition.
- Use nested stacks to express proximity: kicker with heading, heading with supporting copy, label with its control, control with help or error text, related fields, and the action row.
- Use the existing spacing scale or host-site variables. When no suitable token exists, use these starting ranges and adjust to the typography and density:
  - kicker to heading: `4–8px`
  - heading to supporting copy or the next form label: `8–16px`
  - label to its control: `4–8px`
  - control to help, caption, or error text: `4–8px`
  - between field groups or between content and actions: `16–24px`
- Treat `0px` as an intentional exception only for elements meant to touch, such as joined controls, rules, or border treatments. Never use zero separation between distinct text rows, a heading and a label, or unrelated controls.
- Do not compensate for a missing internal rhythm by adding more outer section padding. Fix the local stack that owns the relationship.
- At responsive breakpoints, re-evaluate gaps after text wraps. Do not let a mobile rule unintentionally increase display type or collapse spacing relative to the available width.

## Container fit

- Choose the lightest structural component that satisfies the role. Use a row or box for a navigation bar, utility strip, announcement, compact logo-and-action header, divider band, or similarly shallow element when a full content section is unnecessary.
- When a section is required for a full-width background, anchor, or page structure, explicitly override its wrapper padding and any `min-height` to fit the intended shallow content. Never leave generic content-section padding on a low-height band.
- Inspect both the outer section wrapper and its inner container. Avoid accidentally stacking default section padding with container, row, or component padding.
- Size a shallow band from its tallest child plus deliberate top and bottom breathing room. As a review signal, combined vertical padding should not normally exceed the content height unless the band is intentionally designed as a spacious visual chapter.
- Keep compact bands vertically centered and re-check their total rendered height at desktop and mobile widths. Do not let a header or utility element occupy a hero-like portion of the viewport without an explicit design reason.

## Rendered collision check

Verify the rendered result, not only declared style values.

- Measure adjacent rendered boxes for kicker → heading, heading → copy or label, label → control, control → help or error text, field group → field group, and content → actions.
- Require positive visual separation for distinct elements at desktop and narrow mobile widths. Reject touching or negative box gaps unless the elements are intentionally joined.
- Inspect a screenshot as well as box geometry because glyph ascenders, descenders, outlines, and inline spans can extend beyond their parent line box.
- Exercise the longest wrapping copy and every conditional state that adds or removes content. Hidden default content is not evidence that error, expanded, selected, or result states are collision-free.
- For every shallow band, compare the rendered content height, wrapper padding, nested padding, and total band height. Reject inherited section padding or `min-height` that creates unexplained empty vertical space.
- When a collision appears, repair the smallest owning stack or responsive rule instead of globally increasing page density or section padding.

## Rendered containment gate

Treat containment as a hard pass/fail condition. Absence of page-level horizontal overflow does not prove that a component fits its own layout.

At every reviewed desktop and mobile width, and in every relevant default, selected, focus, error, expanded, collapsed, and result state:

- Compare each visible control shell with the padding box of the grid cell, column, card, or other layout container intended to own it. Fail when any edge of the control crosses that owning boundary, allowing only normal subpixel rounding.
- Compare neighboring layout siblings that are intended to remain separate. Fail when their rendered rectangles intersect, including a control entering an adjacent column, card, result rail, action region, or label area.
- Exercise the longest real label, selected value, helper text, validation message, and conditional content. A shorter default state is not sufficient evidence.
- Ignore only deliberately floating layers such as an open menu, tooltip, or popover, and visual effects such as an outside focus ring or shadow. The resting control shell and its layout box must remain contained.
- Repair containment structurally with the owning width, `min-width: 0`, wrapping, intrinsic sizing, a safer column ratio, or an earlier stack breakpoint. Never hide the failure with clipping or `overflow: hidden`.

A failed containment check blocks completion. Repair it before delivery; when the platform prevents repair, record it as an unresolved blocker and do not describe the build as polished, responsive, verified, or complete. Publish it only when the user explicitly requests a clearly identified review artifact rather than a finished build.
