# Changelog

## [0.2.1] - 2026-11-14

### Fixed
- `house-rules.md` used the old skill pattern `appops-<app>-expert`; it now reads `appops-<app>`.
- The unused icon image moved out of the shipped plugin to `docs/assets/` (the manifest no longer references it).

## [0.2.0] - 2026-11-14

### Changed
- Directory layout: the shipped plugin moved to `adapters/claude/` (plugin.json, skills, prompts, assets, router evals). The repository root keeps `.claude-plugin/marketplace.json` (source `./adapters/claude`), docs, `.github/` and the live model evals in `evals/` (not shipped).
- Renamed the skill `appops-nowa-expert` to `appops-nowa` (user-approved). All references, the router table and the evals are updated. Old name: `appops-nowa-expert`; the old invocation `appops:appops-nowa-expert` is now `appops:appops-nowa`.
- Frontmatter is text-only: removed the nested `metadata:` maps and rewrote both descriptions to start with "Use when" or "Use whenever". The version lives in `plugin.json` and the marketplace entry.
- Dropped the `icon` field from plugin.json (the icon image stays in the assets folder).
- The router now has a routing table with exact slugs, tie-breaks, a default question and Skill-tool loading, checked by `adapters/claude/evals/router/cases.json`.
- The release workflow builds `appops.plugin` from `adapters/claude` (text files only; hooks, scripts and `.mcp.json` are refused) on a `v*` tag.
- Public safety: `PUBLIC-SAFETY.md`, `.public-safety-allow`, `.gitignore` preset; the root AGENTS.md no longer contains local drive paths.

### Fixed
- `prompts/appops.json`: an HTML entity in a variable description is now a plain apostrophe.

### Added
- GitHub Actions workflow `release-plugin.yml` builds `appops.plugin` and attaches it to each release for a one-click download link (README).

## [0.1.4] - 2026-11-06

### Changed
- Standing rule: research before building. Check current official docs and widely recommended, secure practice before choosing an approach, file, tool, config or dependency; cite the source; mark anything unverified; never guess; keep research scoped to the task.

## [0.1.3] - 2026-11-05

### Added
- Security notes: least privilege, no secrets in project files or exports, one-line threat model for a new integration, and safe use of the Nowa external-agent MCP.

## [0.1.2] - 2026-11-04
### Fixed
Behaviour tests rebuilt the same way as fsdevops 0.3.1 (8/8 pass, was 2/8). The Nowa expert now lists the desktop settings: Local setup paths and the Git panel credentials.

## [0.1.1] - 2026-11-03
### Changed
- Developer plugin handoff now names Full-Stack DevOps (`fsdevops`), the renamed fs-developer.

## [0.1.0] - 2026-11-03
### Added
- Router `appops` (`/appops`) with shared house rules: plan, snapshot, operate (MCP/API → files → shortcuts → clicks), check, report; handoff format to developer plugins.
- `appops-nowa-expert` for Nowa 3.16.4: access methods (external agent MCP is Enterprise-gated; local project files by default), visual-vs-code split, projects, two-way sync and round-trip rules, Git panel, data connectors, publishing, Nowa AI, shortcuts and troubleshooting.
