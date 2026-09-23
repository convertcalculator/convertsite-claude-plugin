# Conversion guardrails

Use these as constraints, not as a prescribed page template.

## Conversion contract

- Define one primary conversion for each page.
- Use at most one secondary conversion in the first viewport.
- Make the offer, audience relevance, and next action understandable without scrolling.
- Provide at least one usable endpoint where the primary conversion can be completed.
- Ensure every primary CTA reaches that endpoint directly or through a clear, intentional intermediate step.
- When primary and secondary CTAs promise different outcomes, keep their journeys behaviorally distinct. Do not make both terminate at the secondary endpoint unless the brief explicitly permits that convergence.
- Treat deferred pages, calculators, or later phases as internal build scope, not automatic public messaging. Never add “coming soon”, waitlist, launch-status, or availability language unless the user explicitly requests it for visitors.
- When a primary destination is outside the current scope, provide a purpose-matched current endpoint or honest route structure without pretending the deferred product exists and without collapsing the journey into the secondary CTA. Ask only if the interim behavior would materially change the product decision.
- Do not treat scrolling to more information as conversion completion.
- When no external booking, checkout, or scheduling destination is provided, create a minimal relevant lead form inside the site rather than inventing a URL or leaving the CTA unresolved.
- Ask only for information needed to fulfill the stated action and explain what the visitor receives next.
- Use persistent programmatic labels for every field; placeholders are hints, not labels. Use the correct input type and expose validation errors accessibly.
- Place proof near the claims it supports.
- Handle major objections before the final conversion request.
- Keep labels specific to the value received: prefer “Get my cost estimate” over “Submit”.
- Preserve familiar form, navigation, accordion, tab, and calculator behavior.
- On mobile, keep the primary action early, fields comfortable, and content scannable.

## Creative freedom that is normally safe

- Art-directed typography with readable body text
- Asymmetric grids that preserve reading order
- Full-bleed or offset imagery with controlled contrast
- Varied section height and composition
- Brand-specific borders, rules, annotations, crops, and color fields
- Editorial project storytelling
- Contextual proof and testimonials
- Subtle motion that clarifies hierarchy or state

## Visual hierarchy contract

- Define the intended `1 → 2 → 3` attention sequence before styling each first viewport and primary interactive module. Priority 1 must be one element or one tightly grouped region, not several independent cards or headings.
- Establish hierarchy with size, spacing, position, grouping, and contrast before increasing font weight. Boldness is an accent, not the structure.
- Keep body copy regular, controls and option labels medium, and reserve the heaviest available weight for the single most important short heading or action. Do not render headings, option labels, result copy, metadata, and buttons all at similar heavy weights.
- Use no more than three visibly distinct emphasis tiers inside one module. Supporting explanation, metadata, proof, and helper copy must be quieter than the active question or current recommendation.
- In a choice-to-result module, make the current task the primary focus while the user is choosing. Once an answer exists, make one concise recommendation the dominant result; keep rationale and specifications subordinate and place proof or refinement in a quieter secondary treatment.
- Do not stack several equal-sized, equally bordered result cards when one is the answer and the others are supporting evidence or next steps. Merge related information, reduce container emphasis, or progressively disclose optional detail.
- Make selected options easier to locate than unselected options without making every option visually loud. Selection needs a clear state cue, but the option grid must remain subordinate to its question.
- Preserve the attention order without relying on color. A grayscale or quick-squint view should still reveal the intended first, second, and third reading targets.

## Conversion risks

- Hidden or low-contrast CTAs
- Multiple equally dominant actions
- Text placed over uncontrolled photography
- Novel navigation mechanics
- Long visual introductions before the offer becomes clear
- Motion that delays interaction or causes layout shift
- Repeated decorative cards that obscure priority
- Several equally dominant panels, headings, or heavy text blocks competing in one viewport
- Using similar semibold or bold weights for headings, body copy, options, metadata, and actions
- Lead forms that ask for information without explaining the value received
- Primary CTAs that only scroll to information and never reach a form, booking flow, checkout, contact action, or other completion point
- Visual restructuring that changes formulas, field references, defaults, or conditional states

## Interactive modules

Treat calculators, quote flows, forms, and configurators as functional modules inside the website.

- The surrounding page should establish relevance, trust, and motivation.
- The module should visually fit the selected art direction.
- Its interface must remain clear and familiar.
- Do not make the module the signature motif unless specifically requested.
- Do not alter its logic during a visual redesign without explicit scope.

## Minimum mobile checks

- No overlapping controls or labels
- No content forcing columns wider than the viewport
- Reflow repeated choices to one column when two columns create cramped headings, excessive word stacking, or narrow reading measures.
- Test the longest real heading, CTA label, option copy, and validation message; do not verify only short placeholder content.
- Touch targets remain usable
- Progress, results, errors, and the next action remain visible
- Collapsed and expanded states preserve the intended hierarchy
