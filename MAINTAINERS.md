# Maintainer Guide

This guide documents the development, packaging, and release processes for maintainers of `agent-skills`.

---

## Creating Releases

Releases and distribution bundles are automated via GitHub Actions:

1. **Verify Workspace & Tests:** Ensure all changes are verified and committed on the `main` branch.
2. **Create and Push a Version Tag:**
   ```bash
   git tag v1.0.0
   git push origin v1.0.0
   ```
3. **Automated Packaging:** The [Release Packages workflow](.github/workflows/release.yml) triggers automatically on any `v*` tag push. It will:
   - Assemble `dist/founder-prd-builder-plugin.zip` (containing `plugin.json`, `.claude-plugin/`, `skills/`, `src/`, and `README.md`).
   - Assemble `dist/founder-prd-builder-plugin.tar.gz`.
   - Generate `dist/founder-prd-builder-web-bundle.md` (standalone prompt for ChatGPT / Claude web users).
   - Publish the GitHub Release with auto-generated release notes and attached distribution assets.

---

## Package Manifest Maintenance

When bumping versions:
1. Update `version` in [`plugin.json`](plugin.json).
2. Update `version` in [`.claude-plugin/plugin.json`](.claude-plugin/plugin.json).
3. Update `version` in [`src/founder-prd-builder/SKILL.md`](src/founder-prd-builder/SKILL.md) frontmatter.
4. Verify the symlink [`skills/founder-prd-builder/SKILL.md`](skills/founder-prd-builder/SKILL.md) resolves cleanly.
