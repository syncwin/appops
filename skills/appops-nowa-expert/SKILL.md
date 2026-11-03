---
name: appops-nowa-expert
description: Operate Nowa, the visual Flutter app builder (Nowa Desktop and nowa.dev), the right way. Use when the user mentions Nowa, a Nowa board, screen, component, theme, Circuit logic, the Data panel, APIs tab, Supabase or Firebase in Nowa, Nowa AI (Design, Plan, Agent modes), Instant play, local projects, Project Sync, the Git panel, Save & Commit, running on a device, publishing a web, Android or iOS build from Nowa, plans and credits, or Connect External Agent; or when the appops router sends Nowa work here. Covers what to do visually in Nowa versus in code, the two-way file sync and round-trip rules, Git workflow, data connectors, publishing, the external-agent MCP (Enterprise-gated), shortcuts and known issues. Not for writing Dart by hand - code goes to fs-developer when installed.
license: MIT
metadata:
  displayName: "AppOps Nowa Expert"
  version: "0.1.0"
  author: "@wasimness"
  company: "SyncWin"
---

# AppOps Nowa Expert

Checked against Nowa 3.16.4 (28 Oct 2026) docs and changelog. On another version, re-check the step in the app first (`appops/references/house-rules.md` §5).

**Needs:** `${CLAUDE_PLUGIN_ROOT}/skills/appops/references/house-rules.md` (read first). Nowa Desktop for local projects; a Nowa account.

## 1. What Nowa is
A visual editor that works on **real Flutter projects**. Local projects are ordinary Flutter folders on disk; Nowa adds a small `.nowa/` folder (comments, board settings, git-ignored run args). Edits made in code and in Nowa sync both ways, and since 3.15 Nowa hot-reloads edits made outside it. Details: `references/projects-sync-git.md`.

## 2. Pick the access method
| Method | Status | Use for |
|---|---|---|
| **External agent (MCP)**: ⋮ → Connect External Agent | **Enterprise only** as of 3.16.4; shown only if the account has access | Open projects, read boards and widget tree, build with Nowa tools, screenshots (`references/agent-and-ai.md`) |
| **Project files** (local project + Git) | Every plan via Nowa Desktop | Default for Claude: edit through a developer plugin, Nowa picks it up live |
| **Nowa AI** (in-app chat) | Uses plan credits | The user drives it; Claude can write the prompt |
| **Computer use** on Nowa Desktop | User grants the app | Buttons with no file or MCP route: Deploy, settings, Run |

If the user has no external-agent access, say so once, suggest emailing team@nowa.dev, and use project files.

## 3. Visual in Nowa vs. code
| Do in Nowa | Do in code (developer plugin) |
|---|---|
| Screens, components, layout, theme and component themes, ARB translations, `@Preview` states, images and fonts, API connections from cURL/Swagger, Supabase/Firebase setup, platform permissions | App shell, routing, state management, data layer and sync, background work, push, tests, CI, anything built by helper methods |
Recommended repo shape: Nowa opens one UI package (`packages/<prefix>_ui`); the rest is code. Record it in `.claude/ownership.md` (fs-developer reads it).

## 4. Common jobs
- **New project**: Desktop → Local Projects → New Local Project (folder under the user's dev folder, not Documents), or Import a local repo and pick the package.
- **Change UI**: on the board, or via the agent tools; keep components as real widget classes so they stay editable.
- **Data**: `references/data-and-publish.md` (APIs tab, Supabase, Firebase, models).
- **Run and test**: Run → Instant play (phone, tablet, desktop frames) or a real device; Windows has no iOS simulator; low-end PCs should use a phone over USB instead of the Android emulator.
- **Git**: Git panel → branch per task, Save & Commit, pull before work (`references/projects-sync-git.md`).
- **Publish**: `references/data-and-publish.md`; needs the user's yes and a paid plan for store and web deploys.

## 5. Hand off code
Any Dart change, test or build fix: follow `appops/references/house-rules.md` §4 to `fs-developer`. Before the developer edits, Save & Commit in Nowa; after, check the board and Instant play.

## 6. When something breaks
`references/shortcuts-and-troubleshooting.md`.

Finish with a scratchpad: project, Nowa version, method, changes, checks (PASS / FAIL / NOT RUN), open items.
