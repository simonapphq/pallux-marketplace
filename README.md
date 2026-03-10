# Pallux OS Marketplace Registry

This repository is the community marketplace registry for [Pallux OS](https://pallux-os.com) — a privacy-first, self-hosted personal AI operating system.

## Registry Format

The `registry.json` file at the root of this repository is the canonical index of all published packages. Pallux OS instances fetch this file to populate the Marketplace page.

### Package Fields

| Field | Type | Description |
|---|---|---|
| `id` | string | Unique slug identifier (e.g. `research-assistant`) |
| `name` | string | Display name shown in the UI |
| `type` | `"agent"` \| `"workflow"` | Package type |
| `description` | string | One-sentence description (NZ English) |
| `author` | string | GitHub username of the author |
| `version` | string | Semver version string |
| `installs` | number | Total install count (updated by registry maintainers) |
| `popular` | boolean | Whether to show the Popular badge |
| `tags` | string[] | Searchable tags |
| `install_url` | string | Raw GitHub URL to the package JSON file |
| `created_at` | ISO 8601 | Publication date |

## Package JSON Schemas

Individual package files live under `packages/agents/` or `packages/workflows/` and contain the full configuration used by Pallux OS to install the package.

### Agent Package Schema

```json
{
  "id": "my-agent",
  "name": "My Agent",
  "type": "agent",
  "version": "1.0.0",
  "author": "your-github-username",
  "description": "What this agent does.",
  "tags": ["tag1", "tag2"],
  "model": "claude-3-5-sonnet-20241022",
  "system_prompt": "You are...",
  "tools": ["tool_name"],
  "memory_blocks": [
    {
      "label": "block_label",
      "value": "Initial memory content.",
      "limit": 2000
    }
  ],
  "autonomy_level": "supervised",
  "daily_budget_usd": 1.00
}
```

### Workflow Package Schema

```json
{
  "id": "my-workflow",
  "name": "My Workflow",
  "type": "workflow",
  "version": "1.0.0",
  "author": "your-github-username",
  "description": "What this workflow does.",
  "tags": ["tag1", "tag2"],
  "trigger": {
    "type": "schedule",
    "cron": "0 8 * * *",
    "timezone": "Pacific/Auckland"
  },
  "steps": [
    {
      "id": "step-id",
      "name": "Step name",
      "action": "service.action",
      "params": {}
    }
  ]
}
```

## Contributing

1. Fork this repository
2. Create your package JSON under `packages/agents/` or `packages/workflows/`
3. Add an entry to `registry.json` pointing to your package file
4. Open a pull request with a clear description of what your package does
5. Maintainers review and merge — install counts update automatically

## Guidelines

- Descriptions must be in NZ English
- System prompts must not include hardcoded API keys or secrets
- Agents must specify an `autonomy_level` of `supervised` or `autonomous`
- Daily budget must be reasonable (under $5.00 USD for community packages)
- All packages are reviewed for safety before merging

## Licence

MIT — see [LICENSE](LICENSE) for details.
