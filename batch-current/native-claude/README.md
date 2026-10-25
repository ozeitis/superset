# Native Claude subscription usage verification

Consumer fix: PR #8464, `7f2a262e282c85f6354ccd726bb9b9da452bb2e0`.
Producer source: `4205c0796de07da658dd334b3ba87de81d904681`.

One genuine Claude Code 2.1.310 terminal response produced both subscription windows. The real owner-bound store and common cache-only reader accepted them. Idle readback retained the original observation dates; HTTP and financial dates stayed unchanged. The test used one ordinary usage preflight, one model turn and no authentication renewal. The selected settings file was unchanged, and the disposable worker exited normally. All 63 bundled source modules matched pinned Git objects. This was an isolated terminal/store/reader test, not a production desktop or live ACP test. Transport ACK latency is not qualified.

The live test found a real precision mismatch: an HTTP reset carried milliseconds while the documented native reset used epoch seconds. All three reader/store comparisons now use second identity, preserve finer timestamps, reject older windows and forbid a usage decrease within the same window. No receipt, counter, credential or owner guard was relaxed.

## Validation

The final producer source passes root lint, all 40 typecheck tasks, 351 provider/native tests, 413 agent-setup tests, 431 chat-runtime tests, 702 tRPC tests and 94 chat tests. Three existing cases were skipped. An overlapping 61-test focused native subset also passes. PR #8464 was separately checked on its exact head: 317 provider tests, host types and root lint pass. Product test deadlines were unchanged. See `native-proof.json` for exact commands, heads and boundaries.

The earlier broad run remains failed: eight cases in unchanged upstream integration tests. Seven hit the default five-second deadline; one failed before its helper started and before the disposal assertion. Pure upstream runtime reproduction was not performed. No full-suite pass is claimed.

`producer-increment.patch` shows the 16 producer-only files over the combined account/quota prerequisites. Its base composition includes the already reviewed two shared-module resolutions. The upstream PR also contains those prerequisite histories; they must land first. No new schema or UI is added by this increment.

Native collection stays opt-in (`SUPERSET_NATIVE_CLAUDE_USAGE=1`) for newly selected launches. Existing/attached workers retain their original configuration. Missing or old readings fall back to the existing tracker. Wallet and reset-credit observations stay independent. ACP is covered by synthetic transport tests only. No running user chat/server or installed app was stopped, restarted or replaced for this verification.

Provider contract: [official statusline data](https://code.claude.com/docs/en/statusline#available-data).
