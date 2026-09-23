---
name: convertsite-design-director
description: Build or edit ConvertSite websites and standalone embeds through MCP, including calculators, forms, and template adaptations. Use for ConvertSite implementation; use reference-recreator for matching an explicit visual reference.
---

# ConvertSite Design Director

If equivalent ConvertSite workspace rules are not already active, also read [references/workspace-guardrails.md](references/workspace-guardrails.md) and follow it for the duration of this skill. Do not load it again when the same rules are already supplied by `AGENTS.md`, `CLAUDE.md`, or another active workspace instruction file.

## Choose the work route

- Classify the request as a new build, template adaptation, local edit, structural edit, functional edit, or read-only review. Also identify `build_surface: site` or `build_surface: embed`; for embeds identify `embed_operation: create_custom`, `adapt_template`, or `edit_existing`.
- For a bounded edit to an existing target, use [references/local-edits.md](references/local-edits.md). This includes an isolated formula or state fix whose dependencies can be traced. Do not load the complete new-build prompt, art-direction library, or full build specification for this route.
- For a new build, template adaptation, or broad structural/functional change, read the shared scope sections 1–4 of [PROMPT.md](PROMPT.md), the relevant site or embed workflow (5A or 5B), and build/review sections 6–7. Preserve established design decisions unless changing them is part of the request.
- For a read-only review, inspect the requested target and use the applicable checks below; do not create a build card or mutate the target.

## Load guidance when it affects the task

- When creating or changing conversion hierarchy, use [references/conversion-guardrails.md](references/conversion-guardrails.md).
- When selecting a new site art direction, use [references/design-library.md](references/design-library.md). Skip it for edits that preserve the current direction.
- For a new embed or template adaptation, use [references/embed-build-contract.md](references/embed-build-contract.md). For an existing-embed edit, load only its relevant operation and verification sections. Keep the designated host's design system and the embed-only mutation boundary.
- Only when the user explicitly requests `Creative mode: explore`, read [references/concept-gate.md](references/concept-gate.md) and [references/creative-quality-bar.md](references/creative-quality-bar.md) before any MCP write.
- Before a ConvertSite write, read the scope, recovery, and applicable verification rules in [references/mcp-build-contract.md](references/mcp-build-contract.md). Use its full build gate for new or broad work; the local-edit route supplies the bounded-edit preflight.
- When changing layout, typography, or control styling, use [references/layout-rhythm-contract.md](references/layout-rhythm-contract.md).
- For site delivery or review, use the relevant sections of [references/quality-review.md](references/quality-review.md). For embeds, use the relevant verification scenarios in `embed-build-contract.md`. Review the whole experience for new builds and broad changes; verify affected behavior for local edits.
- Use [references/project-brief-template.md](references/project-brief-template.md) only when an unstructured build request needs it. Reuse context and infer safe omissions rather than making the user complete every field.

Read a reference once while its relevant content remains available; reread when the task, file, or missing context requires it. An embed must belong to a designated existing host site and inherit that site's design direction.

Provide a usable conversion endpoint for a new build or a requested conversion-flow change. For a local edit, preserve the existing endpoint and verify it when affected; report unrelated pre-existing issues without expanding scope.

For a new build, do not inspect or use other ConvertSite workspace sites as inspiration. For an edit, inspect only the user-designated target site. Use another site as a reference only when the user explicitly identifies it as one.

Do not publish unless the user explicitly asks.
