# House rules (every AppOps expert)

## 1. Fixed order
1. **Plan**: a short checklist of what will change in the app; one approval. Approved plans run without asking again inside the app; anything outside it (publishing, payments, sending, deleting) needs its own yes.
2. **Snapshot**: before changing a project, save a way back (the app's history, a Git commit, an export).
3. **Operate** through the app's own tools: MCP or API first, then its documented files, then keyboard shortcuts, then clicking. Never edit an app's private data files or databases directly.
4. **Check the result where users see it** (the running app, the published page), not only inside the editor.
5. **Report**: what changed, what was verified, what was not (PASS / FAIL / NOT RUN).

## 2. Access methods (best first)
| Method | When |
|---|---|
| App MCP server or API | Connected and the plan allows it |
| Files the app documents as editable | The app syncs them both ways (for example a project folder) |
| Keyboard shortcuts and menus via computer use | No MCP/API; the user granted the app |
| Mouse clicks via computer use | Last resort; slow and brittle |
Never reverse-engineer a gated or undocumented endpoint.

## 3. Safety
- Accounts, plans and billing belong to the user: never upgrade, buy, sign out, change passwords or invite people without a yes.
- Secrets (API keys, tokens, signing keys) are typed by the user into the app; never into chat, files or logs.
- Publishing, deploying, pushing and store uploads need an explicit yes for that action.

## 4. Handoff to a developer plugin
When the job needs code, write a short request and pass it on (or give it to the user):
```
Code request (from appops-<app>-expert)
Project: <path>   Owned paths: <from .claude/ownership.md>
Need: <behaviour>   Why: <app limit that needs code>
Done when: <check in the app>
```
After the developer plugin finishes, re-open the result in the app and check it (§1.4).

## 5. Facts
State the app version the guidance was checked on. When the app shows something different, trust the app, say so, and log it for an update.
