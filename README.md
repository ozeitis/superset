# Account and conversation contribution review

- Terminal account selection: [#8460](https://github.com/superset-sh/superset/pull/8460).
- Exact ended-session recovery: [#8461](https://github.com/superset-sh/superset/pull/8461).
- Native ACP accounts: [#8462](https://github.com/superset-sh/superset/pull/8462).
- Saved native Claude conversations: [#8463](https://github.com/superset-sh/superset/pull/8463).
- Quota correctness: [#8399](https://github.com/superset-sh/superset/pull/8399), [#8464](https://github.com/superset-sh/superset/pull/8464).
- Composer acceptance: [#8400](https://github.com/superset-sh/superset/pull/8400).
- Separate storage migrations: [#8401](https://github.com/superset-sh/superset/pull/8401), [#8402](https://github.com/superset-sh/superset/pull/8402), [#8459](https://github.com/superset-sh/superset/pull/8459).

`qualification.json` records exact sources, commands and limits. The final integrated suite passes 15,920 tests; lint, 41 type tasks and 17 strict catalogs pass. Real Node/PTY tests pass 56 cases, with 2 unavailable fish-shell cases skipped.

`ui-manifest.json` and `ui-journeys.json` distinguish initial isolated Electron journeys from later component demonstrations. All accounts and histories shown are synthetic. The history GIF uses real PromptInput/ComposerBody with a controlled callback; no authenticated provider replay is claimed.

Hosted CI requires maintainer approval. Evidence binaries stay on this documentation branch, outside source PR diffs. T3V2/Codex history adoption and personal menu-bar/packaging changes are outside these PRs.
