# AppOps (App Operator)

A Claude plugin with one expert skill per app you work in, so Claude uses each app the right way: its screens, settings, projects, exports, publishing, plans and integrations. **Nowa** (the visual Flutter builder) is first; more apps follow.

## How it works
`/appops` (or just ask to do something in a supported app) picks the app expert, which:
1. Plans the change and gets one approval.
2. Saves a way back (Git commit, export, history).
3. Operates the app the best available way: its MCP or API, its documented files, then keyboard shortcuts, then the screen.
4. Checks the result where users see it, and reports PASS / FAIL / NOT RUN.

## Works alone or with a developer plugin
AppOps never writes code. When a job needs code it hands a short request to a developer plugin (for Flutter: `fs-developer`) if installed, or gives you the manual step. Experts may follow a developer plugin's rules for that app's code; developer plugins never depend on AppOps.

## Experts
| App | Skill | Checked on |
|---|---|---|
| Nowa | `appops-nowa-expert` | Nowa 3.16.4 (28 Oct 2026) |

## Install
```
/plugin marketplace add <path-or-repo>
/plugin install appops@syncwin-appops
```

## License
MIT. See `CREDITS.md`. Contact: support@syncwin.com.
