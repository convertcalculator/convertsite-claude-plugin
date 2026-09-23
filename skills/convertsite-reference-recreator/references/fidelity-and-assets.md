# Fidelity and asset rules

## Fidelity modes

### Inspired

- Preserve broad principles and mood
- Allow different composition and component choices
- No visual comparison round by default

### Close

- Preserve section sequence, macro composition, proportions, hierarchy, and responsive behavior
- Adapt target content and available ConvertSite primitives
- Use one visual comparison round by default

### High

- Match observable geometry, spacing, typography scale, crops, surfaces, and responsive transformations as closely as practical
- Match observable component family, internal zones, repeated-item count, item
  order, media placement, and overflow behavior
- Treat a structurally simpler substitute as unresolved until a checked source
  asset or ConvertSite limitation proves the original structure impractical
- Use two visual comparison rounds by default
- Activate only when explicitly requested because it costs more and may require more inspection

## Content and asset boundary

- Recreate layout and visual relationships, not ownership.
- Do not copy reference logos, protected copy, photography, illustration, icons, or proprietary fonts unless the user supplied them or explicitly confirms the right to reuse them.
- When no separate target content is supplied, establish whether the reference itself is the target and whether its visible content and assets may be reused. Reuse explicit authorization from the active task; ask before building only when that decision is missing. Never create a substitute to avoid asking.
- Never invent a fictional brand, business, proposition, copy deck, logo, or image set merely because reuse rights or target content are missing.
- Do not hotlink reference assets unless the user explicitly authorizes reuse of the original source asset URLs for validation.
- When reuse is authorized, preserve a one-to-one mapping to the original source asset URLs where supported; do not inline large base64 or data-URL payloads into the ConvertSite tree or task context.
- Replace unavailable assets with user assets, licensed alternatives, or newly created equivalents that serve the same compositional role.
- Match font character, metrics, weight, and contrast when the exact font is unavailable.
- Keep a separately supplied target brand distinct from reference content. When `reference_as_target` is explicitly authorized, preserve the reference identity instead of fabricating a distinction.

## Accuracy language

Say `matched closely`, `approximated`, or `adapted` when exact assets, states, fonts, or platform primitives differ. Reserve `pixel-perfect` for a verified result at stated viewports.
