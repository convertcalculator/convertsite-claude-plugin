---
name: convertsite-reference-recreator
description: Recreate an explicitly supplied URL or screenshot in ConvertSite when the user asks to match its visual structure. Do not use for ordinary site generation or implicit inspiration.
---

# ConvertSite Reference Recreator

For a new recreation or a changed reference, read [PROMPT.md](PROMPT.md) and follow the selected fidelity workflow. For a bounded correction to an established recreation, reuse the existing blueprint, target, content authorization, fidelity, and validation ledger. Inspect the changed reference/target regions and their dependencies; do not recreate the complete inventory or restart the build. If required context is unavailable, recover it from the designated reference and target, or ask only for the missing decision.

If equivalent ConvertSite workspace rules are not already active, also read [references/workspace-guardrails.md](references/workspace-guardrails.md) and follow it for the duration of this skill. Do not load it again when the same rules are already supplied by `AGENTS.md`, `CLAUDE.md`, or another active workspace instruction file.

Load references progressively:

- For new reference analysis, read [references/reference-analysis.md](references/reference-analysis.md); for corrections, use the sections relevant to the changed component or behavior.
- When establishing or changing fidelity or asset/content use, read [references/fidelity-and-assets.md](references/fidelity-and-assets.md). Reuse permissions already established in the active task.
- Before a ConvertSite write, read the safety/scope rules and applicable mapping constraints in [references/mcp-recreation-contract.md](references/mcp-recreation-contract.md). Its full build order is for new or broad recreations.
- Before delivery, use [references/visual-validation.md](references/visual-validation.md): full comparison for a new or broad recreation, affected regions and dependencies for a bounded correction. Keep unresolved ledger items visible; a local correction does not certify the rest of an unfinished build.

Read guidance once while its relevant content remains available. Continue through the requested implementation and verification within the invoking workflow's explicit budgets and review checkpoints.

Activate only for an explicit reference supplied by the user. Never inspect other workspace projects or carry the reference into later unrelated builds.

Treat the reference as read-only. Build only in a new unpublished target or a user-designated existing target.

Publication is opt-in unless an explicitly invoked wrapper grants validation-loop authorization. Use one of these modes:

- `prohibited`: never publish; explicit no-publish wording always selects this mode.
- `first_iteration`: publish the first completed iteration once when explicitly authorized.
- `validation_loop`: publish each completed iteration needed for rendered comparison, within the selected fidelity's comparison-round limit, when an explicitly invoked wrapper states that its invocation grants this authorization.

Verify the exact target identifier against current state before every publish; this is an internal target check, not a new approval request when authorization already covers that publish. Never publish a partial or knowingly broken iteration. Treat publication as validation, not completion.

## ConvertSite fidelity guardrails

- Treat XML values as intent, not proof of rendered behavior. Verify critical layout rules in the published or preview DOM at the requested viewports.
- For full-bleed sections, remove constraints from the section `content` element as well as sizing the child wrapper. A `width: 100%` child can still be limited by the section content container.
- For a sticky-looking media hero, use the proven section-background pattern in `references/mcp-recreation-contract.md` when ConvertSite forces a section with `background_image-asset` to render as `position: relative`. Let the `100vh` section reserve normal flow space; fix its `background-image` and `content` style elements to the viewport. Do not add a duplicate viewport spacer or margin compensation.
- When the reference has this fixed-hero/following-section overlap and it is being built or affected by an edit, validate at scroll position `0` and at two known offsets. The hero layers must remain at viewport top while the following section advances over them. Do not impose this pattern on references without it.
- Use real ConvertSite inputs, links, buttons, and questions for interactive UI. Do not approximate them with decorative boxes and multiline text.
- Set important text colors explicitly on light and dark surfaces when theme inheritance changes the reference contrast.
- If an experimental correction degrades width, media, interaction, or responsiveness, restore the last known-good structure before continuing.
