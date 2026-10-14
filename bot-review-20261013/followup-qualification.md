# Final follow-up qualification

The next bot pass produced two new valid findings. Both are fixed in one publication batch:

- [#8400 /4267148094](https://github.com/superset-sh/superset/pull/8400#discussion_r4267148094), head `28bb0dd6ddbbfb2b297c065c45a2890efcbf17fa`: a per-draft in-flight token survives composer remounts. Edits, clearing and recovery cannot release it. Duplicate sends are declined before uploads or onSend; success, false and throws release the original token. Exact final regressions against the prior head:16 passed, six failed. Corrected full Composer subtree:34 passed; chat-ui:23 passed. Both package typechecks and scoped lint pass.
- [#8462 /4267160362](https://github.com/superset-sh/superset/pull/8462#discussion_r4267160362), head `1be3b18f41f96f3ee85cad080dc1cb1dc103b9a7`: the actual workspace page stores the Add Tab trigger before opening the terminal account dialog, matching the native-chat path. Three real Radix frame tests and six terminal-focus utility tests pass; scoped lint and all17 catalog checks pass. The page callback wiring was inspected; no fully mounted authenticated route or live-provider replay is claimed.

The [public source snapshot](https://github.com/ozeitis/superset/tree/e23a030d36914f44c42d8d6d58e164bfa8195bfb) has exactly the same Git tree (`537117fc4e4e1620e8e73485bf4f5015b0f63a80`) as tested combined source `f66866810387e748d87a2029c27d367df933cc75`. It adds only these two fixes to the [prior qualification](qualification.md).

- Standard full `bun run test`:28/28 tasks successful; **16,106 passed, zero failed, four skipped, eight TODO**. Desktop ran again;27 matching Turbo task results were reused.
- Full `bun run typecheck`:40/40 tasks passed. Cache reuse is retained in the local run log.
- Full `bun run lint`:passed, no fixes applied.
- Full `bun run check:i18n`:passed;17 strict locale compilations, no catalog changes left in the working tree.
- Native Node/PTY evidence from the prior qualification remains applicable:56 passed, two unavailable-fish skips. These two fixes do not change terminal host/runtime code.

The terminal lane's older private dependency store lacked autumn-js/yaml, so its full desktop typecheck was inconclusive. The final combined checks above ran successfully using the current frozen lockfile in an independent private store. No user dependency installation, application, provider session, credential, transcript or server was changed. Earlier failure records are retained; no test assertion or timeout was weakened.

[Machine-readable counts, source identity and log digests](followup-qualification.json). Hosted workflows still require maintainer approval. Bot status is not proof that hosted CI ran.

Review communication is now batched:one consolidated response per affected PR, with finding links and evidence; no per-thread acknowledgement burst.
