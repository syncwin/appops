# Shortcuts and troubleshooting

## Shortcuts (from Nowa docs/changelog)
| Keys | Action |
|---|---|
| Ctrl+1 | AI Assistant panel |
| Ctrl+6 | Data panel |
| Ctrl+. | Shortcuts list |
| V / C (Instant play) | Select / Comment |
| Esc | Back |
| + / − | Zoom |
| Shift+1 / Shift+2 / Shift+0 | Fit all / fit selection / 100% |
| Enter / Shift+Enter / Ctrl+click | Select children / parent / deepest |
| Shift+A | Auto layout |
| Alt+A / Alt+H / Alt+D | Align left / center / right |
| Alt+W / Alt+V / Alt+S | Align top / middle / bottom |
| Shift+H / Shift+V | Flip horizontal / vertical |
| Hold Alt | Measure |

Concepts: boards, screens, components (closed like design-tool instances; double-click to edit), wrappers (Padding/Container chips folded into Details), `@Preview` variants, prototypes, Themes panel (all `ThemeData` widget themes).

## Troubleshooting
| Symptom | Fix |
|---|---|
| "Flutter isn't set up" though Flutter is on PATH | Update to 3.16.4+ (fixed) |
| AI chat won't open | Needs 3.16.4+ |
| Desktop app shows an upgrade page | Server didn't confirm desktop access; sign out/in is a user action; contact Nowa support |
| Blank web editor | GPU memory ran out; reload, close other GPU apps (mitigated 3.16.2) |
| Widget shows as a sealed box | It's built by a helper method; split into a widget class (code handoff) |
| Code changed oddly after a Nowa save | Known save-path edge cases; revert the hunk from Git, report to Nowa, run `flutter analyze` |
| Packages failed to load | Problems panel lists them; run `flutter pub get` from code |
| Git sync issues with renamed branches or worktrees | Update to 3.16.4+ |
| `pubspec.yaml` edit not picked up | Start a new run |
| Android emulator very slow | Use a phone over USB or wireless debugging |
