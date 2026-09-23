# Edits to an existing ConvertSite

Use this route for a bounded visual, content, formula, or state change to a designated existing site or embed. Broader work follows the build route; size alone does not require fresh permission when the user already authorized the change.

## Inspect and scope

- Reuse the established target, brief, design decisions, and authorization. Verify the target identifier from current MCP state; ask only if it is ambiguous.
- Inspect the affected elements and their shared styles, formulas, references, defaults, conditional states, and consumers. Trace enough dependencies to understand the impact; do not map unrelated sections or the entire workspace.
- For an embed, establish its designated host and inspect the host treatments needed for the edit. Do not change the host or a canonical/shared template. If isolation cannot be established, resolve that before writing.
- Preserve the current art direction and conversion flow unless the user requested changes to them. Do not run a concept gate, create a full build specification, or choose a new design direction for an isolated edit.
- State the intended target and change briefly, then carry out the authorized edit without another approval checkpoint. Honor any explicit budget, review checkpoint, or publication limit inherited from the invoking workflow.

## Implement and verify

Apply one coherent change batch using existing stylesets and native components. Inspect shared-style consumers before a shared edit; use a local exception when the request is genuinely local. Do not reset the theme.

Use the relevant verification categories in `mcp-build-contract.md`:

- **Copy or label:** check the actual text, wrapping, and neighboring controls at representative desktop/mobile widths. Exercise an affected action; do not rerun unrelated calculations for a label-only edit with no reference or behavioral impact.
- **Layout or control styling:** check containment, collisions, column ratios, contrast, and affected collapsed/expanded, focus, selected, and error states. Exercise the affected input-to-result path if its controls or mounting/visibility changed.
- **Formula, binding, or state:** trace dependent outputs and conditions; test explicit fallbacks before hidden views mount, user overrides, units, invalid/boundary inputs, and affected branches. Also check the output presentation and relevant responsive states.

After the batch, verify the saved change and rendered or functional result. Broaden checks when a failure or dependency warrants it; do not repeat unchanged checks without new evidence. Repair regressions caused by the change within the requested scope.

Finish when the requested change and affected behavior are verified. Report material limitations or unavailable verification honestly. Publication still requires the invoking workflow's authorization; a successful preview does not grant it.
