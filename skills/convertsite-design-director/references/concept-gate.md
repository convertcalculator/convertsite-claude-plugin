# Optional ConvertSite concept gate

Activate only when the user explicitly requests `Creative mode: explore` during a ConvertSite MCP build. Never activate it automatically and never use it for ordinary chat, advice, or non-MCP work.

## Cost boundary

- Create exactly three concise concepts.
- Do not render three websites.
- Create a visual comparison only for `build_surface: site` with explicit user selection.
- Do not search or inspect unrelated workspace sites.
- Reuse the same conversion architecture across all three concepts.
- Build only the selected concept.
- Allow at most one post-render creative revision.

## Gate 1: create three concept cards

Make the concepts structurally different, not merely different palettes.

Before creating them, record one shared grounding note with the audience, the page's single job, and three to five concrete visual or content cues from the actual subject (such as materials, tools, environments, artifacts, or category conventions). Use these cues as raw material; reject concepts that could fit an unrelated industry after changing only the copy and logo.

For `build_surface: site`, limit each internal card to:

```yaml
name:
primary_direction:
big_idea:
first_viewport:
signature_composition:
image_or_graphic_system:
section_rhythm:
conversion_safety:
main_risk:
```

For `build_surface: embed`, limit each internal card to:

```yaml
name:
interaction_model:
input_strategy:
result_strategy:
conversion_handoff:
signature_interaction_or_visual_device:
complexity_cost:
main_risk:
```

Reject a set when two concepts share the same hero structure, signature device, or section rhythm.

## Gate 2: select

Score each concept from 1–5 on:

- Brand and category fit
- Conversion clarity
- Memorability
- Asset feasibility
- ConvertSite feasibility

Use `concept_selection: auto` unless the user explicitly asks to see multiple directions and choose among them.

- **Auto:** select the strongest concept, briefly record why, and continue without interrupting the user.
- **User, site:** create one lightweight, self-contained local HTML comparison containing the three directions side by side. Keep the copy, information, CTA hierarchy, and available assets constant so the comparison isolates design direction. Show only a desktop first viewport, a compact mobile preview, the concept name, and one main tradeoff for each direction. Do not add controls, export logic, persistent state, full click-through flows, or additional pages. Deliver the comparison and stop before any MCP write until the user chooses A, B, or C.
- **User, embed:** show the three concise concept cards as text and stop before any MCP write until the user chooses. Do not create a visual comparison artifact.

Do not create the visual comparison for standard mode, auto selection, local styling edits, functional changes, bug fixes, template adaptation, or work whose visual direction is already fixed by an existing design or explicit reference.

Do not select a concept with conversion clarity or feasibility below 3.

## Gate 3: lock before MCP writes

Record the selected concept in the build specification:

```yaml
creative_mode: explore
selected_concept:
rejected_concepts: []
signature_composition:
non_negotiables: []
prohibited_fallbacks: []
```

Do not begin ConvertSite mutations until these fields are complete. For a site, do not fall back to a generic split hero, repeated three-card grid, or interchangeable stock treatment. For an embed, do not fall back to website sections, dashboard chrome, or a long undifferentiated form.

## Gate 4: one visual review

After rendering, apply `creative-quality-bar.md`. If it fails, perform one focused revision of the underlying concept execution. Do not generate three new concepts or restart the entire build.
