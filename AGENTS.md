# appops agent guide

AppOps Claude plugin: one expert skill per desktop or web app (Nowa first). It operates apps and never writes code.

**Structure (single branch, `main`):** the shipped plugin is `adapters/claude/` (`.claude-plugin/plugin.json`, `skills/appops` router and `skills/appops-nowa`, `prompts/`, `assets/icon.png`, `evals/router/cases.json` and `evals/evals.json`, plus copies of README, CHANGELOG, LICENSE, CREDITS, PUBLIC-SAFETY, `.gitignore`). The root keeps `.claude-plugin/marketplace.json` (source `./adapters/claude`), the same docs, `evals/` (live model cases, not shipped) and `.github/` (release workflow). Edit the docs in both places and keep the copies identical.

## Commands
- Validate: `claude plugin validate adapters/claude --strict` and `claude plugin validate . --strict` (marketplace)
- Directory check: `python <aiaddon-repo>/dev/aiaddon-review/scripts/validate_extension.py adapters/claude --strict --target directory --require-meta author,company`
- Router check: `python <aiaddon-repo>/dev/aiaddon-review/scripts/route_check.py adapters/claude`
- Secret and private-data scan: `python <aiaddon-repo>/dev/aiaddon-review/scripts/scan_secrets.py . --history`; false positives only in `.public-safety-allow`
- Evals (real model calls; cases live in root `evals/`, and `claude plugin eval` reads cases from inside the plugin folder, so copy `adapters/claude` and `evals/` into one scratch folder outside the repo and run it there): `claude plugin eval <scratch-copy> --trust-plugin --ablation none --scaffold --allow-tools Read Glob Grep Skill -j 4 --no-publish`. Write results outside the repo; the packager includes repo files.

## Workflow
1. Read the skill or script you change, plus its neighbours.
2. Make the smallest change; run the closest check, then the full gate.
3. Update `CHANGELOG.md` for behavior changes; log ideas in `IMPROVEMENTS.md`.

## Rules
- **Directory compliance:** the shipped plugin (`adapters/claude/`, built into the release `.plugin` on a `v*` tag) is Markdown, JSON and YAML only (plus LICENSE, `.gitignore`, the icon image): no hooks, no scripts, text-only frontmatter.
- **Never publish secrets or private data** (keys, tokens, passwords, personal contact data, client names, internal URLs, local paths) in this repo or anything it builds.
- Run the closest check and the full gate before committing. Never delete or weaken tests or evals. Report failed, skipped or timed-out runs honestly; NOT RUN is never a pass.
- Follow neighbouring files. Keep each `SKILL.md` under 500 lines; move detail into `references/`.
- On release, bump `version` in `adapters/claude/.claude-plugin/plugin.json` and the plugin entry in `.claude-plugin/marketplace.json`; add a `CHANGELOG.md` entry per behavior change (root and `adapters/claude/` copies). Release: push a `v<version>` tag; `release-plugin.yml` builds `appops.plugin`.
- No commits, pushes or PRs unless asked. Work on a branch and open a PR; never push to main.
- No new dependencies without asking (scripts stay on the Python standard library).
- Never commit secrets. Never pick names or slugs without user confirmation.
- Skills are named `appops-<app>` (router `appops`). Hand code work to Full-Stack DevOps; never the other way round.
- `evals/results/` is git-ignored.

## Model routing
Opus plans, decides, writes self-contained briefs with a report word limit, and reviews every result. Haiku for search, reading and mechanical edits. Sonnet for coding, tests and multi-step work. Do 1-2 tool calls inline.

## Docs
README.md, CHANGELOG.md, CREDITS.md, PUBLIC-SAFETY.md; ideas and feedback in `IMPROVEMENTS.md`.
