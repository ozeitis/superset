# Shell-pipe regression and stale CLA refresh

The real shell test now checks its own stdout and stderr pipe closure in the registered Node integration suite. The detached daemon remains alive at assertion time. Pure environment/parser cases stay in Bun. Runtime source is unchanged. Independently removing either cleanup call in memory fails the new assertion.

Five older PR branches now include reviewed upstream `d962fd0`. Four branches preserve every feature blob. The watcher-test PR also corrects distinct-path readiness and exact cache assertions across its real-backend phases; it changes only its existing test file. This is a genuine base update, not an empty rerun commit. The existing CLA signature is already stored; the normal synchronize event refreshes old results. No signing/recheck comments, review requests or check bypasses are used. The full suite passed on the recorded pre-delta combined source. The only later combined change is this test file, requalified through its complete package suite, types and lint. Exact-head results and remaining qualification bounds are in [qualification.json](qualification.json).

The initial combined concurrent run also hit an unchanged upstream CLI process-inspection timeout. Its failure is retained; a serialized qualification passed with the original five-second deadline. This does not establish the precise timeout cause. Hosted CI authorization and maintainer approval remain separate from local verification. No application restart or existing-chat/server action occurred.

[Focused test and mutation output](regression-output.txt).
