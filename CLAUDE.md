# macrocraft

Godot 4 RTS built around programmable unit behavior. Read `docs/design.md` before design work; it holds the pillars and the open questions.

- Engine: Godot 4.x, GDScript. Project root is the repo root (`project.godot`).
- Layout: `scenes/` (.tscn), `scripts/` (.gd), `docs/` (design + glossary).
- Record every new or renamed term in `docs/glossary.md`.
- Repo and CI identity are managed by infra-bootstrap tofu (`ci_only`, no hosting). Don't create GitHub/Azure settings for this repo by hand.
