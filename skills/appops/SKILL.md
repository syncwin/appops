---
name: appops
description: Entry point for operating the apps the user works in on PC and web - how to use each app's screens, panels, settings, projects, exports, publishing, plans and integrations, and how to drive it from Claude (its MCP, API, files or, last, the screen). Use whenever the user asks to do something in or with a supported app, asks how a feature of that app works, hits an error inside the app, or invokes /appops. Today it routes to appops-nowa-expert (Nowa, the visual Flutter builder: boards, screens, components, themes, Circuit logic, data panel, Git panel, Instant play, run, publish, Connect External Agent). Not for writing or reviewing app code - that belongs to a developer plugin such as fsdevops.
license: MIT
metadata:
  displayName: "AppOps"
  version: "0.1.4"
  author: "@wasimness"
  company: "SyncWin"
---

# AppOps: Router

Routes to one app expert and owns what they share (`references/house-rules.md`). Carries no app-specific rules.

## Routing

| App | Skill |
|---|---|
| Nowa (visual Flutter builder, Nowa Desktop, nowa.dev) | `appops-nowa-expert` |

Unsupported app: say so, then help with general guidance only, clearly marked as not verified for that app.

## Step 1. Define the job (one message, skip what's known)
1. Which app, and which project or account inside it?
2. What outcome (for example "a settings screen on the board", "web build published", "Git branch synced")?
3. How to reach the app: its MCP or API (best), its files on disk, or the screen (computer use, last resort)?
4. Live or test: is this a project people use?

## Step 2. Hand off to the expert
Load the expert skill and follow its order. Read `references/house-rules.md` first in every session.

## Working with a developer plugin
- AppOps operates apps; it never writes, refactors or reviews code.
- When a job needs code (a Dart file, a test, a build fix), check whether a developer plugin is installed (for Flutter: `fsdevops`). If yes, hand that part to it with a short code request (`references/house-rules.md` §Handoff). If not, give the user the manual step or a clear request they can take to a developer.
- An expert may follow a developer plugin's rules for the app's code (for example Nowa follows fsdevops's builder-safe ownership rules). The developer plugin never depends on AppOps.

Finish with a scratchpad: app, project, job, method used, what changed, what was verified, open items.
