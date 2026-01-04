# Bluera Marketplace

Claude Code plugins by Bluera Inc.

## Installation

```bash
# Add the Bluera marketplace
/plugin marketplace add blueraai/bluera-marketplace

# Install a plugin
/plugin install <plugin-name>@bluera
```

## Available Plugins

| Plugin | Description |
|--------|-------------|
| [bluera-knowledge](https://github.com/blueraai/bluera-knowledge) | Project-specific knowledge stores for definitive library sources. Clone and index important dependencies for authoritative reference. |

## Updating the Marketplace

The marketplace is the **source of truth** for available plugins and versions. Claude Code checks this marketplace to determine what's available for installation.

### When to update `marketplace.json`:

- **Plugin version bumps** - Update the `version` field when a plugin releases a new version
- **Description/metadata changes** - Any display info users see when browsing
- **Adding new plugins** - When publishing a new plugin to this marketplace

### When updates are NOT needed:

- Internal implementation changes in plugin repos
- Bug fixes that don't warrant a version bump
- Changes to files not reflected in marketplace entry fields

### Auto-update behavior

- Third-party marketplaces (like this one) have auto-update **disabled by default**
- Users can enable it via `/plugin` → Marketplaces → Enable auto-update
- When enabled, Claude Code refreshes marketplace data at startup

### Version sync workflow

1. Update plugin code in the plugin repository
2. Bump version in the plugin's `.claude-plugin/plugin.json`
3. Update version in this repo's `.claude-plugin/marketplace.json`
4. Push both repos
5. Users run `/plugin marketplace update bluera` or rely on auto-update

## Releasing

The marketplace uses semantic versioning independent of plugin versions. Bump the marketplace version when:
- **patch** - Fix marketplace.json formatting, typos, or metadata
- **minor** - Add new plugins to the marketplace
- **major** - Breaking schema changes

```bash
# Bump version, commit, tag, and push (triggers GitHub Actions release)
npm run release:patch
npm run release:minor
npm run release:major

# If version already bumped but not tagged
npm run release:current
```

**Workflow:**
1. Update `marketplace.json` as needed
2. When ready to release: `npm run release:patch` (or minor/major)
3. GitHub Actions creates the Release with auto-generated notes

## License

MIT
