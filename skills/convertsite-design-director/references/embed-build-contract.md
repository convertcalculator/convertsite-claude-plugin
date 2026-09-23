# ConvertSite embed build contract

Use for `build_surface: embed` only.

## Operation contract

Set exactly one operation before planning:

- `create_custom`: create a new embed without using an existing embed as its functional base.
- `adapt_template`: instantiate an explicitly designated, or unambiguous currently selected, platform template and adapt that instance to the designated host site.
- `edit_existing`: change an explicitly designated existing embed instance.

Do not treat a template adaptation as a blank-canvas generation. Do not infer a source template from visual similarity or inspect several templates for inspiration.

## Host-site contract

Every embed belongs to one existing host site.

- Resolve a single designated host site before any write. Use the current/selected MCP target only when unambiguous; otherwise ask.
- Inspect only that host site. Do not inspect other workspace sites for inspiration.
- Set `mutation_scope: embed_only`.
- Never change the host site's global theme, stylesets, page structure, content, or unrelated modules while building the embed.
- If the intended placement section is known, match both the global theme and that section's local context.

Extract and inherit:

- Font families, weights, type scale, labels, and numeric styling
- Primary, secondary, accent, surface, border, muted, and error colors
- Button, input, select, radio, checkbox, and focus treatments
- Border widths, radii, shadows, and surface hierarchy
- Spacing scale, control height, content width, and information density

Prefer existing shared styles and variants. Add embed-scoped exceptions only when the interaction requires them.

### Variable-first host fingerprint

- Inspect the host site's design-system variables and their use in rendered components before choosing any embed styling.
- Create a compact internal mapping from semantic roles to existing variables: typography, text, muted text, primary action, secondary action, background, surfaces, borders, focus, error, radii, shadows, spacing, and control height.
- Inventory only the components the embed needs. Mark each treatment as `observed` when it exists on the host or `derived` when it must be inferred from the nearest observed component.
- Bind embed styles and stylesets to the mapped variables. Do not copy resolved hex values, font values, radii, or spacing into local styles when a suitable variable exists.
- When no exact variable exists, prefer the nearest semantically correct host variable. Create a narrowly scoped exception only when reuse would change meaning, accessibility, or interaction clarity.
- Do not mutate host variables merely to fit the embed. The fingerprint describes and consumes the host design system; it does not restyle the host.

## Existing-template adaptation contract

Treat the template as functional infrastructure to preserve and the host site as the visual system to inherit.

- Resolve the exact explicitly designated or unambiguous selected source template and host site before any write.
- Determine whether the source is canonical, shared, or already an isolated instance. Never assume an editable target is isolated merely because it is unpublished.
- Inspect the source structure, component topology, formulas, references, units, constants, defaults, conditional states, variants, validation, result outputs, conversion handoff, reset behavior, and responsive behavior.
- Record a preservation manifest and separate requested changes into `visual`, `content`, and `functional` deltas.
- Instantiate or copy a canonical or shared template before adapting it. Never customize the canonical source in place.
- If the platform cannot create a separate instance or cannot prove isolation from other consumers, stop before writing and ask the user to approve the exact mutation risk.
- Keep formulas, references, defaults, states, validation, result behavior, and conversion flow unchanged unless the user explicitly requests a functional delta.
- Apply host-site variables and existing component variants to the new instance. Replace template-local visual choices only as needed to inherit the host; do not carry over the template's visual brand when it conflicts with the host.
- Make narrow, dependency-aware edits. Avoid full-tree replacement, broad restyling, and rebuilding working template logic.
- Confirm after adaptation that the canonical source and unrelated instances are unchanged.

For `edit_existing`, preserve the same source-isolation and behavior boundaries, but inspect the affected elements and their dependencies rather than repeating the full template-adaptation inventory. Edit only the explicitly designated isolated instance; do not create a copy unless the user requests one or isolation cannot be established. Use `local-edits.md` for a bounded change.

## Product boundary

Build a self-contained embeddable experience, not a webpage.

- Do not add navigation, hero copy, footer, portfolio, testimonials, FAQ sections, or other website chrome unless the requested embed itself requires that content.
- Keep the flow focused on input, useful output, and the next conversion action.
- Use compact supporting explanation, tooltips, summaries, or progressive disclosure when needed.

## Sparse-brief behavior

- Infer routine control, layout, and implementation details from the requested flow, supplied facts, and established calculation rules.
- Do not invent material pricing, scoring, eligibility, or conversion-destination decisions. Ask a focused question before implementing behavior that depends on missing business rules; continue useful work that does not depend on the answer.
- Do not invent externally verifiable company facts or expand a sparse brief into additional product features.
- Use a provisional model only when the user explicitly requests an illustrative prototype or authorizes those assumptions. Label provisional outputs as estimates, state the assumptions, and centralize constants so they can be replaced easily.
- Never present provisional assumptions as confirmed company policy. A template's existing rules remain the source unless a functional change is requested.

## Interaction hierarchy

1. Short purpose or instruction
2. Primary inputs
3. Conditional or advanced inputs only when relevant
4. Immediate result or clear calculate action
5. Transparent breakdown or explanation
6. Relevant conversion endpoint such as quote request, booking request, or lead form

Give value before requesting contact data whenever possible.

## Presentation-mode decision

Choose one presentation mode before writing:

- `single_surface` by default: the primary inputs, direct result, and relevant refinements share one continuous calculator surface.
- `progressive_disclosure`: optional or advanced content expands, collapses, or appears conditionally without turning the main task into separate navigated views.
- `staged_flow`: the main task is divided into separate views only when staging is materially justified.

An interaction state is not a view. Default, selected, valid, invalid, calculated, disabled, expanded, and collapsed are normally states of the same surface. A result appearing or updating beside its inputs is not a separate view. An accordion or conditional advanced section is progressive disclosure, not multistep navigation.

Use `staged_flow` only when at least one qualifying trigger applies:

- the user explicitly requests a staged or multistep experience;
- later questions genuinely depend on earlier answers;
- the flow remains excessively long or cognitively dense after compact layout and progressive disclosure have been considered;
- a conversion gate intentionally separates teaser, contact capture, and revealed value.

Conceptual phases, visual neatness, the mere existence of input and result states, or difficulty fitting a side-by-side desktop layout do not justify separate views. Before selecting `staged_flow`, record the qualifying trigger, why a single surface fails, and the added navigation cost. If that case is weak or empty, use `single_surface` or `progressive_disclosure`.

When staging is justified:

- Define each view's purpose, simultaneously visible content, single primary focus, and primary action.
- Place persistent navigation or context outside a changing view only when it genuinely helps orientation. Do not duplicate navigation controls inside and outside the same view.
- Disabled, previous, and next behavior must reflect the actual reachable views. A disabled route must look inactive without changing control geometry.
- Preserve entered values when moving between views and keep the next required action easy to locate.

Treat an explicitly supplied layout as a hard constraint only when the user requests exact reproduction. Otherwise treat it as a proposed presentation and improve the structure when needed to protect hierarchy, conversion, responsiveness, or platform reliability; disclose that choice before writing.

## Formula and state contract

- Define units, currency, rounding, minimums, maximums, tiers, inclusivity of boundaries, and invalid combinations.
- Use effective values when a visible default may not yet be mounted or available to formulas.
- Ensure user-entered values override defaults.
- Keep hidden inputs from contributing stale values unless explicitly intended.
- Update results after every relevant input change or provide one unmistakable calculate action.
- Explain why a result cannot be produced when inputs are invalid.
- Preserve the user's selections when revealing results or lead capture.

## Presentation

- Make the primary input or choice dominant, the direct insight second, and optional detail third.
- Use progressive disclosure for advanced choices.
- Keep labels, inputs, units, errors, and result relationships unambiguous.
- Inspect the rendered component and its styleset before choosing the visual-shell target; do not assume every input kind uses the same element. Style the single element that actually owns the control surface: commonly `input` for text and email fields, and `wrapper` for number inputs or compound controls. Keep the other element layout-only with a transparent zero-width border and no competing background.
- Keep component geometry identical across default, hover, focus, checked, active, and error states. Never introduce a thicker border on interaction; change color, background, or an inset shadow while preserving border width, padding, and box sizing.
- Avoid dashboard styling, unnecessary cards, decorative charts, and large website-like headings.
- Match the designated host site's existing brand styling. Do not invent a separate visual direction for the embed.

### Result story

Plan the result as a decision sequence rather than a collection of available outputs:

1. One dominant answer or recommendation
2. A small set of supporting insights needed to interpret it
3. Assumptions, rationale, breakdown, or refinements as quieter optional detail
4. One clear next action

Do not give every metric an equally prominent card, color, border, and heading. Use meaningful icons only when they improve scanning, category recognition, or interpretation; decoration does not repair weak hierarchy.

Keep frequently adjusted assumptions beside the result they affect or with the primary inputs. Do not move an output-determining control into a separate result view merely to make the input surface look simpler. Prefer live result updates when the calculation is immediate and valid input changes are easy to interpret; use an explicit calculate action when it prevents premature, expensive, or misleading output.

## Conversion endpoint

- Connect the result to a usable next action.
- Carry the relevant input selections and result summary into the quote or lead request when supported.
- Ask only for contact information needed for follow-up.
- Explain what happens after submission.

## Verification matrix

For a new embed or template adaptation, test the applicable scenarios below. For an existing-embed edit, select the scenarios affected by the change and its shared dependencies. Verify each coherent change batch, reuse valid evidence for unchanged behavior, and broaden checks when a new failure or dependency warrants it. Preserve checks for hidden defaults and user overrides whenever formulas, inputs, visibility, or mounting behavior change.

- Default state before user interaction
- Minimum valid values
- Values immediately below and above every pricing or scoring boundary
- Maximum supported values
- Empty, zero, negative, non-numeric, and otherwise invalid inputs where applicable
- Every option and conditional branch
- User overrides of every visible default
- Hidden, collapsed, expanded, and not-yet-mounted states
- Result total, breakdown, rounding, units, and currency
- Reset or restart behavior when present
- Lead capture with the calculated context preserved
- Narrow mobile width with no overlap or forced horizontal expansion
- Explicit vertical rhythm plus the rendered collision and containment gates from `layout-rhythm-contract.md` at desktop and mobile widths, including longest wrapping copy and conditional content. Fail the build when a control leaves its owning column, card, or grid cell, or intersects an adjacent sibling, even when the page itself has no horizontal overflow.
- Native fields render with exactly one coherent shell on the element that owns the visible surface; fail the check on a double border, a wrapper enclosing a second rounded input border, or an error label trapped inside a bordered wrapper
- Interactive states preserve dimensions; fail the check when hover, focus, checked, active, or error styling changes border thickness, padding, or control size and causes layout shift
- Embed appearance inside the actual host site at desktop and mobile widths
- No unintended changes to host-site theme, pages, sections, or unrelated modules
- For template adaptations, preserved behavior matches the inspected source after each coherent batch of authorized changes
- The canonical source template and unrelated template instances remain unchanged

Do not retest unchanged platform-owned component internals such as built-in email-format validation. Test authored validation rules, calculation constraints, changed configuration, handoff behavior, and visible regressions.

Repair the narrowest underlying cause of any failed case before delivery.
