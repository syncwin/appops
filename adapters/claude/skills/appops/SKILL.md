---
name: appops
description: Use whenever the user asks to do something in or with a supported app, asks how a feature of that app works, hits an error inside the app, or invokes /appops. Entry point for operating the apps the user works in on PC and web - how to use each app's screens, panels, settings, projects, exports, publishing, plans and integrations, and how to drive it from Claude (its MCP, API, files or, last, the screen). Today it routes to appops-nowa (Nowa, the visual Flutter builder: boards, screens, components, themes, Circuit logic, data panel, Git panel, Instant play, run, publish, Connect External Agent). Not for writing or reviewing app code - that belongs to a developer plugin such as fsdevops.
license: MIT
---

# AppOps: Router

Routes to one app expert and owns what they share (`references/house-rules.md`). Carries no app-specific rules.

## Routing table (exact slugs; first matching row wins)

Read top to bottom. A row matches when any trigger phrase appears in the request as whole words (case-insensitive) and none of its `!` phrases does. Checked against `evals/router/cases.json`.

| Order | Trigger phrases | Skill |
|---|---|---|
| 1 | nowa; nowa desktop; nowa.dev; nowa board; circuit logic; instant play; connect external agent | `appops-nowa` |

**Tie-break rules:** a request that names a supported app goes to that app's skill even when it also mentions code; the code part is handed off afterwards (see Working with a developer plugin). A request about writing, refactoring or reviewing app code with no app operation is not routed here.

**Default when no row matches:** if the request is about operating an app but names none, ask one closed question and stop: "Which app is this for: Nowa, or another app?" For an unsupported app, say so, then give general guidance only, clearly marked as not verified for that app. Never answer the task itself in the routing step; the router only picks a skill.

**How to load the chosen skill:** call the Skill tool with the full slug `appops:<skill>` (for example `appops:appops-nowa`) and follow it. On a surface without the Skill tool, read that skill's `SKILL.md` by relative path from the plugin root (`skills/<skill>/SKILL.md`) and follow it.

## Step 1. Define the job (one message, skip what's known)
1. Which app, and which project or account inside it?
2. What outcome (for example "a settings screen on the board", "web build published", "Git branch synced")?
3. How to reach the app: its MCP or API (best), its files on disk, or the screen (computer use, last resort)?
4. Live or test: is this a project people use?

## Step 2. Hand off to the expert
Load the expert skill (see "How to load") and follow its order. Read `references/house-rules.md` first in every session.

## Working with a developer plugin
- AppOps operates apps; it never writes, refactors or reviews code.
- When a job needs code (a Dart file, a test, a build fix), check whether a developer plugin is installed (for Flutter: `fsdevops`). If yes, hand that part to it with a short code request (`references/house-rules.md` §Handoff). If not, give the user the manual step or a clear request they can take to a developer.
- An expert may follow a developer plugin's rules for the app's code (for example Nowa follows fsdevops's builder-safe ownership rules). The developer plugin never depends on AppOps.

Finish with a scratchpad: app, project, job, method used, what changed, what was verified, open items.
