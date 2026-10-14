Latest: [final follow-up fixes and qualification](followup-qualification.md). The record below is the earlier tested checkpoint.

# Bot review qualification

All bot notes present at the pre-publication readback were reviewed, including inline threads and review-body-only suggestions. Valid findings have targeted fixes and regression tests. Replies explain retained behavior where a suggestion would weaken identity, recovery or credential correctness. Four other PRs needed no new code; their earlier fixes were checked again.

## Exact feature heads

| PR | Qualified head |
|---|---|
| [#8400](https://github.com/superset-sh/superset/pull/8400) | `6d1ded07659dd543d147b47b833934ba05695b87` |
| [#8460](https://github.com/superset-sh/superset/pull/8460) | `7b1ddf1a2aa41f90abf6ca2cb039f5c7bfd4d66e` |
| [#8461](https://github.com/superset-sh/superset/pull/8461) | `0ce9f3949686d0f2a0284c1fbe3890360e934a38` |
| [#8462](https://github.com/superset-sh/superset/pull/8462) | `e098cb8091b74ec99abd8eb0ec8e568c543e7898` |
| [#8463](https://github.com/superset-sh/superset/pull/8463) | `88be4d64be272645b7f69c37b404f07e59509343` |
| [#8464](https://github.com/superset-sh/superset/pull/8464) | `704e1ad1d2d7f06f689de3eb8715a8a30c00bc28` |

Each exact head passes changed-module lint, focused tests, canonical catalog extraction, strict compilation of all 17 locales and a catalog semantic audit. #8463's final merge changes only an already-reviewed RegExp line wrap; its saved-history tests and catalogs were rerun afterward.

## Combined repository checks

The [public qualification source](https://github.com/ozeitis/superset/tree/70b27f8f6527760815bac1ed96517f5deb906b65) has exactly the same Git tree (`7ce0ddb2288d935e10e99df044f0d2edfb31ebe1`) as locally tested integration `a3e18f166ed6ac68f57428097c584401da9b0288`. It combines the six feature fixes on official main `cc31d024c8f266caad52ea15d14311f5d22ba5cc`, plus the independent watcher-test repair below. It is a verification snapshot, not a combined upstream feature PR.

- `bun run test`: 28/28 tasks successful; **16,101 passed, zero failed, four skipped, eight TODO**. The final standard run reused 27 matching Turbo task results; desktop ran again. Package counts and log digests are in [qualification.json](qualification.json).
- `bun run typecheck`: 40/40 tasks successful, 31 matching cached results.
- `bun run lint`: passed, 10,303 files, no fixes applied.
- Strict catalog compilation: all 17 locales pass. No missing translation or discarded upstream translation was accepted.
- Real Node/PTY integration: 56 passed, zero failed; two fish-shell cases skipped because fish is unavailable. This ran before the test-only watcher change; terminal code is identical.
- [Account modal walkthrough and scope](README.md): actual frontend components, keyboard trapping/restoration and pending/accepted behavior, driven in Chrome with synthetic launches. This is not authenticated Claude/Codex end-to-end proof.

Tests use the Bun binary pinned by official CI (`bun@1.4.2-canary.20261007.1`, reporting `1.4.3-canary.1+bd599f5af`); install/type/lint use pinned stable Bun 1.4.2. Node is 24.21.0. Tests ran with private HOME/config/temp folders and external provider/Keychain command guards. No running user app, provider session, transcript, credential or server was changed.

## Failures retained and corrected

The unchanged native watcher regression twice advanced after 12 events without observing all 12 expected paths. A separate test-only fix waits for each path; the native backend, four-second deadline and assertions remain. Its isolated branch `6fc95b753de5a66e52e04e03b82ca2804757dcc9` also passes the entire upstream suite: **15,722 passed, zero failed**, full lint and all 40 typecheck tasks. It is not mixed into the six feature PRs.

One later full run hit an unchanged host Git fixture's five-second setup timeout. The fixture is byte-identical to official main; its isolated control and full host package (2,851 tests) passed. No timeout or assertion was weakened. The final standard combined run passed using matching cached package results as disclosed above.

Hosted CI still requires maintainer approval. These local results do not establish human approval, merge permission, production deployment or unrestricted real multi-account qualification.
