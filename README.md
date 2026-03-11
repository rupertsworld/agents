# Workspace

Agent workspace — skills, docs, and logs.

```
├── AGENTS.md          # System prompt — identity, preferences, config
├── docs/              # Reference docs (filing rules, remote setup, etc.)
├── logs/              # Session logs (YYYY-MM-DD Topic.md)
├── skills/            # Agent skills (generic, shareable)
├── jobs/              # Background job definitions
└── user/              # Local — user content (Notes vault, etc.)
```

## Design

Skills are generic and shareable — no personal config baked in. Personal details (calendar IDs, file paths, workflow specifics) live in `docs/` and `AGENTS.md`, which skills reference via "consult any relevant documentation provided in context."

This separation means skills can eventually be published as a public repo while docs and AGENTS.md stay private.
