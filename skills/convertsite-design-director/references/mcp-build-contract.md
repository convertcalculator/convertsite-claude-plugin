# ConvertSite MCP build contract

## Before writing

- Confirm `build_surface: site` or `build_surface: embed` and use only the corresponding ConvertSite MCP product mode.
- Never create a website container for a standalone embed or flatten a requested website into an embed.
- For a custom embed, resolve one existing host site, inspect only that site's design system, and constrain all writes to the embed. For template adaptation or an existing-embed edit, also inspect only the explicitly designated or unambiguous selected source or target. Do not modify the host theme or unrelated site content.
- Determine whether the request is a new build, template adaptation, local restyle, structural edit, or functional change.
- For template adaptation, resolve and inspect only the explicitly designated or unambiguous selected source template and host site. Establish whether the template is canonical or shared, create a separate instance before customization, and keep the source untouched.
- If a separate template instance cannot be created or isolation cannot be established, ask before any write that could affect the source or other consumers.
- If the request says create or build and does not identify a target site, classify it as a new build.
- For a new build, do not list, open, inspect, compare, or use other workspace sites as inspiration. Create a separate unpublished site.
- For an edit, inspect affected elements, styles, formulas, references, variants, defaults, conditional states, and dependencies only within the user-designated target site.
- Do not call a site-listing operation to look for inspiration. Use it only when necessary to locate a site the user has already identified.
- Use another site as a reference only when the user explicitly designates it as one.
- Preserve working structures and unrelated user choices.
- For the designated existing site, reuse its current theme and stylesets before creating exceptions. Never borrow them from unrelated sites.
- Do not run `SetTheme` unless initializing a new site or the user explicitly requests a global theme change.
- Do not add custom CSS, custom stylesheet blocks, or script-injected styling unless the user explicitly requests CSS. Visual fidelity alone is not authorization. Use native components, exposed element properties, existing variables, stylesets, and variants; prefer a narrow local property change over a shared or global style mutation.
- When a requested detail cannot be achieved with native controls, record the exact platform limitation and leave that detail unresolved rather than silently introducing CSS.
- Use ConvertSite editor undo/version history for recovery; MCP has no transactional rollback command. Ask only when a mutation exceeds existing authorization, is destructive beyond normal editor recovery, or has an ambiguous target/scope. Do not request fresh permission solely because an authorized change is broad.

## Pre-write build gate

For a new build, template adaptation, or broad structural/functional change, create a compact internal Build Card before the first mutation. For a bounded existing-target edit, use the preflight in `local-edits.md` instead; do not create a complete Build Card. For broad work, record only the fields relevant to the requested change and reuse established decisions. The card identifies:

- the selected presentation mode for each primary interactive module: `single_surface`, `progressive_disclosure`, or `staged_flow`;
- the interaction states that exist without assuming they require separate views;
- for `staged_flow`, at least one qualifying trigger, why a single surface fails, the added navigation cost, and what is simultaneously visible in each planned view;
- the single primary focus and primary action for each surface or justified view;
- the observed host or target treatments the build will reuse, including typography weights, text colors, controls, interaction states, spacing, and surfaces relevant to the task;
- the result hierarchy when the build produces an answer or recommendation;
- the highest-risk authored assumption and the smallest representative thin slice that can prove it;
- the rendered and functional evidence required before completion can be claimed, including the parent-containment and sibling-intersection evidence required by the rendered containment gate in `layout-rhythm-contract.md`.

Default to `single_surface`. Do not begin a broad build when these fields are unresolved, and do not create separate views when the staged-flow justification is weak or empty. Do not expose the full Build Card to the user unless it clarifies a material interpretation or risk, but state the interpreted target, scope, structural approach, and publication mode before writing.

## Build order

For a site, establish visual foundations, conversion hierarchy, page structure, art direction, modules, endpoint, responsive behavior, and verification.

For an embed, inspect and map the designated host site's design-system variables first, then follow the selected operation. For a custom build, establish inputs, effective defaults, formula or scoring model, conditional states, results, conversion handoff, compact presentation, and responsive behavior. For a template adaptation, inspect and preserve the source behavior, instantiate it, and apply only the authorized visual, content, and functional deltas. Reference mapped variables through stylesets and components instead of duplicating their resolved values. Do not add website sections, mutate the canonical template, or change the host site outside the embed.

Build and verify the representative thin slice before replicating any risky authored pattern. Typical proof targets include one table-driven control, one repeated item, one hidden-default formula, one state transition, one result calculation, or one document action. Read back its structure and exercise its behavior. Replicate only after the expected value, transition, or action is proven. Skip this extra checkpoint when the complete requested build is already smaller than a meaningful thin slice.

For time- or call-bounded work, reserve capacity for rendered review before expanding the build. Reaching a mutation quota with an unreviewed full tree is a worse checkpoint than stopping at a smaller verified boundary.

## Scope boundaries

- A visual request does not authorize formula or product-logic changes.
- A functional request does not authorize a redesign.
- Interactive modules may receive visual styling consistent with the site, but their logic remains unchanged unless explicitly requested.
- Use shared styles for repeated patterns and local styling for genuine exceptions.
- Before delivery, audit the target for custom CSS and broad style mutations introduced during the task. Remove anything not explicitly authorized and verify that shared consumers and the host theme remain unchanged.
- For every native control, inspect which rendered element and styleset target owns its visible shell before styling it. Text and email controls may require the shell on `input`, while number inputs and compound controls may require it on `wrapper`; never style both. Leave the non-owning element layout-only so default, focus, and error states cannot produce nested rounded borders.
- Avoid broad tree replacements for local improvements.
- Treat a platform template as a functional base, not permission to copy its visual brand into an unrelated host.

## Verification after each coherent change batch

Use the categories below to select checks for the requested result and affected dependencies. A new build or broad change requires a review of the whole relevant experience; a bounded edit requires the changed behavior and dependent scenarios. These are not a checklist to rerun after each individual write. Read back the saved change and exercise it in the rendered result; broaden or repeat checks when new evidence warrants it. Preserve any stricter explicit task budget or review checkpoint.

- Requested visual result
- Primary CTA visibility and hierarchy
- Primary CTA destination and successful path to a real conversion endpoint
- Navigation and section anchors
- Calculations and field references
- User-entered values overriding defaults
- Hidden, collapsed, expanded, and not-yet-mounted states
- Tabs, accordions, conditions, result panels, and validation
- Desktop and mobile layout
- Column ratios, `min-width`, labels, controls, and the vertical-rhythm, container-fit, rendered collision, and rendered containment gates in `layout-rhythm-contract.md`. Absence of page-level overflow is not a containment pass: directly reject any control that leaves its owning layout container or intersects a neighboring layout sibling.
- Rendered native fields have exactly one coherent border and surface on the correct component element. Treat nested wrapper/input borders, an error label enclosed by the outer border, or different shell geometry between default and error states as a failed check.
- Do not retest unchanged platform-owned component internals such as native email-format validation. Test only authored validation rules, changed configuration, integration behavior, or a visible regression.
- For template adaptations, canonical source integrity and isolation of unrelated instances

Before final delivery, record which viewport widths, user-facing states, functional scenarios, and conversion endpoints were directly exercised. Structural XML or component-tree read-back proves structure only. If rendered or behavioral evidence cannot be obtained, label that verification unresolved and do not describe the build as polished, responsive, working, or complete.

## Publication

Never publish unless the user explicitly asks. Verify the exact target identifier against current state before publishing; do not request the same permission again when it already covers this action. Publication is separate from editor undo/version history and never follows merely from a successful preview.
