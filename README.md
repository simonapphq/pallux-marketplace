# Pallux OS Marketplace

Agent templates, skills, workflows, and tool configurations for [Pallux OS](https://pallux-os.com) -- a privacy-first, self-hosted personal AI operating system.

## Structure

```
pallux-marketplace/
├── registry.json          # Canonical index of all marketplace items
├── items/
│   ├── templates/         # Agent templates
│   ├── skills/            # Skill packages
│   ├── workflows/         # Workflow definitions
│   └── tool-configs/      # Tool configuration bundles
└── README.md
```

## Registry Format

`registry.json` is fetched by Pallux OS instances to populate the Marketplace page. Each item includes:

| Field | Type | Description |
|---|---|---|
| `id` | string | Unique slug identifier |
| `name` | string | Display name |
| `description` | string | One-sentence description (NZ English) |
| `type` | string | `template`, `skill`, `workflow`, or `tool-config` |
| `tier` | string | `free` or `pro` |
| `author` | string | Publisher identifier |
| `tags` | string[] | Searchable tags |
| `version` | string | Semver version |
| `installs` | number | Install count |
| `config` | object | Type-specific configuration payload |
| `created_at` | ISO 8601 | Publication date |

## Bundled Templates

The registry ships with 23 agent templates covering five layers:

- **Orchestrator** -- AADIV (central router)
- **Life** -- PEPPER, JARVIS, JAMESON, RHODEY, HAPPY, Meeting Notes Bot, Content Writer
- **Intelligence** -- GANDALF, DR STRANGE, JP MORGAN, WIDOW, SHURI, Data Analyst
- **Project** -- STARK, VISION, NICK FURY, BANNER, THOR, Code Reviewer
- **System** -- FRIDAY, HAWKEYE, WONG

All bundled templates are free tier and authored by `pallux-os`.

## Contributing

1. Fork this repository
2. Add your item configuration under the appropriate `items/` subdirectory
3. Add an entry to `registry.json`
4. Open a pull request with a clear description

## Guidelines

- Descriptions must be in NZ English
- System prompts must not include hardcoded API keys or secrets
- All packages are reviewed for safety before merging

## Licence

MIT
