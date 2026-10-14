# Account picker focus checks

**Passed within component scope.** These are the actual `AddTabMenu`, `AccountTerminalDialogFrame` and `AccountTerminalForm`, with synthetic accounts and controlled launch responses. Source: `f1ce85270884515834a7ebef37c6dff25ce67675`.

- Both terminal and native-chat pickers retained focus through 12 forward and 12 reverse Tab presses.
- Cancel returned focus to the Add Tab trigger. Return reopened its menu.
- Pending launches ignored Escape, disabled Cancel and fields, and removed Close.
- Accepted responses closed the picker and preserved focus in the synthetic target. Typed text confirmed it. The nested Codex selector also worked.

![Account picker focus walkthrough](account-modal-focus-walkthrough.gif)

The walkthrough contains ten actual CUA screenshot keyframes over 18 seconds, not a continuous recording. It is resized and GIF quantized; the original PNGs below are unchanged.

![Native-chat focus stays inside the picker](05-chat-trap-qualified.png)

![Pending terminal launch cannot be dismissed](08-terminal-pending-escape-qualified.png)

![Accepted terminal launch keeps target focus](09-terminal-accepted-focus-qualified.png)

All identities use reserved synthetic `.test` addresses. The unrelated shortcut label is an inert stub to avoid Electron IPC. The launch target is a textarea; no provider, terminal or backend runs. **This demonstrates frontend behavior, not authenticated provider replay or full desktop E2E.** [Structured proof](proof.json) records the source hashes, journeys and asset hashes.
