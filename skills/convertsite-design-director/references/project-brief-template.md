# Project brief template

Fill only what is known. Infer low-risk omissions.

```yaml
project:
  name:
  website_language:
  build_surface: # site or embed
  new_build_or_existing:
  creative_mode: standard # use explore only when explicitly requested
  concept_selection: auto # auto or user; used only in explore mode
offer:
  product_or_service:
  primary_value:
  differentiators: []
audience:
  primary_audience:
  concerns: []
  desired_impression: []
conversion:
  primary_goal:
  primary_cta:
  secondary_goal:
content:
  required_sections_or_topics: []
  available_proof: []
  available_assets: []
embed:
  operation: # create_custom, adapt_template, or edit_existing
  host_site:
  intended_placement:
  mutation_scope: embed_only
  source_template_or_embed:
  mutation_target:
  preserve_behavior: true
  requested_visual_changes: []
  requested_content_changes: []
  requested_functional_changes: []
  purpose:
  expected_inputs: []
  expected_outputs: []
  known_formula_or_scoring_rules: []
  assumptions_allowed: false
interactive_modules:
  existing: []
  required: []
  logic_must_remain_unchanged: true
brand:
  existing_theme_or_styles:
  desired_character: []
  avoid: []
constraints:
  deadline:
  legal_or_accessibility:
  other: []
```

When the user gives an ordinary natural-language brief, silently map it to these fields. Routine implementation choices remain allowed; `assumptions_allowed` concerns material business/pricing/scoring assumptions and becomes true only when the user explicitly authorizes them. Ask only when a missing answer would materially change the product, business rules, target, or scope; continue independent authorized work while waiting.
