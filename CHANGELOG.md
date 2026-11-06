# Changelog

## [Unreleased]

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
