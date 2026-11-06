# claude-skills

Sergio's personal plugin marketplace for Claude. One catalog for both:

- **claude.ai / Claude Desktop**: added in Customize → Plugins as a marketplace from this repo, with automatic sync on push.
- **Claude Code**:
  ```
  /plugin marketplace add Zelek1118/claude-skills
  /plugin install <plugin>@claude-skills
  ```

## Plugins

| Plugin | Source | What it does |
|---|---|---|
| `taste-skill` | [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) → `skills/taste-skill` | Professional company websites, checked in a real browser |

## Adding a skill

Every plugin is one entry in `.claude-plugin/marketplace.json`.

**Someone else's skill**: point at its folder in their repo, no copying:

```json
{
  "name": "<plugin-name>",
  "description": "<one line>",
  "source": { "source": "git-subdir", "url": "https://github.com/<owner>/<repo>.git", "path": "<path/to/skill>" },
  "strict": false,
  "skills": ["./"]
}
```

**Own skill**: put the folder in `plugins/<name>/` (with `SKILL.md` and any `scripts/`, `references/`, `assets/`) and add:

```json
{ "name": "<name>", "description": "<one line>", "source": "./plugins/<name>", "strict": false, "skills": ["./"] }
```

`"strict": false` is required for claude.ai when the plugin folder has no `.claude-plugin/plugin.json`.

Check before pushing: `claude plugin validate .`

After a push, claude.ai syncs on its own. A **new** plugin still has to be installed once (Add in claude.ai, `/plugin install` in Claude Code). Updates in someone else's repo do not trigger a sync here; press Sync on the marketplace or push any change to this repo.
