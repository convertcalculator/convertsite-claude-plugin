# Workspace guardrails

## Working style

- Act as a careful product and design partner, not only as an executor.
- Inspect the affected implementation and dependencies before making changes; reuse established context instead of remapping unrelated work.
- Preserve working structures, user choices, and unrelated settings.
- Make the smallest targeted change that satisfies the request.
- Do not broaden a styling request into product logic changes, or a functional request into a redesign, without stating this first.
- Lead with the outcome and communicate clearly what changed, what stayed untouched, and what was verified.

## ConvertSite change recovery

- ConvertSite supports undo and version history in the editor, including for changes made through MCP.
- MCP does not expose a transactional rollback command. Use ConvertSite's editor history or version history when a change needs to be recovered.
- Before writing, inspect the affected elements, styles, formulas, references, states, and dependencies.
- Prefer targeted edits for local requests, but do not block an authorized structural or broad change solely because MCP itself has no rollback command.
- Ask for confirmation only when the action is outside the user's authorization, destructive beyond normal editor recovery, or targets an ambiguous scope. Reuse authorization already established in the task; verifying a target identifier is an internal check, not a repeated permission request.
- Publication state and version history are separate concerns. Publish only after the user explicitly asks. The existing explicit `$cs-kopie` shortcut is a standing exception for its documented bounded validation publishes; it does not authorize publishing through other workflows. Explicit no-publish wording always overrides this exception.

## ConvertSite themes and styles

- Use the existing theme, stylesets, and component variants before adding local exceptions.
- Do not run `SetTheme` routinely. Use it only for initial setup or when the user explicitly requests a global theme change.
- Never reset or overwrite fonts, colors, or other theme choices that the user may have changed manually.
- Prefer shared styles for repeated patterns and local changes for genuinely local exceptions.

## Design quality

- Produce polished, designer-quality interfaces with intentional hierarchy, spacing, typography, borders, and interaction states.
- Follow the hierarchy: primary input or action, direct insight, then optional detail.
- Use progressive disclosure for advanced settings.
- Do not make every secondary action a large button; clear colored text links can be more appropriate.
- Avoid generic dashboard styling, unnecessary shadows, dull low-contrast text, and decorative complexity without purpose.
- When a visual reference is supplied, study and follow its relevant design system closely instead of inventing an unnecessarily different direction.

## Formulas, defaults, and state

- A visible default value is not proof that the value is available to formulas, especially inside hidden, collapsed, or not-yet-mounted views.
- Where initialization can be delayed, use effective values: the user's value when available, otherwise an explicit fallback.
- Ensure user-entered values override defaults.
- After structural or visual changes, verify the affected formulas, references, defaults, tabs, show/hide states, and calculated outputs. Trace shared dependencies to determine the relevant checks.
- Never consider a calculator finished merely because the interface renders correctly.

## Layout and responsiveness

- Respect configured column distributions regardless of expanded or collapsed content.
- Prefer simple whole-number column ratios when supported, such as `2 1`.
- Prevent content from forcing columns wider than intended; use `min-width: 0` where appropriate.
- Inputs, labels, and controls must never overlap.
- For affected collapsible content, check both collapsed and expanded states at relevant viewport widths.

## Verification

- After each coherent change batch, verify the requested result and affected dependencies.
- For styling changes, check the affected layout and interaction states; exercise calculations and defaults when controls, references, or visibility/mounting behavior are affected.
- For functional changes, check dependent calculations, defaults, user overrides, edge cases, and their presentation.
- Before delivery, exercise the relevant user journey and report any unverified behavior. Broaden or repeat checks only when a change, failure, or newly discovered dependency warrants it.
- If a regression appears, identify the actual cause and repair it with the narrowest possible change.
