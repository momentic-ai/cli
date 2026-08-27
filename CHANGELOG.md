# momentic

## 3.52.3

### Patch Changes

- 8f6419a: Improve failure recovery safety, diagnostics, and execution latency.
- 4d6f4f2: Fix spurious git errors when the system uses a non-English locale
- 1e26c49: Show failure recovery errors when failed actions run inside modules.
- 8116d0c: Enable AI action shorthand by default for newly initialized projects, improve its editor validation, and allow any stable kebab-case V2 ID.
- ee93445: Treat no-edit triage outcomes as successful without repair charges, and keep pull request summaries scoped to the latest run state.
- 4d6f4f2: Retry rate-limited API requests during setup and report a clear message when the limit persists.
- 6bb0877: Explore commands now require Explore to be enabled for your organization.

## 3.52.2

### Patch Changes

- b769d76: Prevent failure recovery from masking application bugs.

## 3.52.1

### Patch Changes

- 03b3abc: Prevent large result ZIP uploads from timing out.
- 28af23e: Hide explore and bugbash from the CLI help.
- 2d6eb4f: Improve result classification cache behavior for runs without Git context.

## 3.52.0

### Minor Changes

- 2571568: Allow MCP agents to set run and preview soft timeouts, poll long-running previews, and batch-preview AI actions and modules.
- 3fa3974: Allow bare strings in simplified test steps to represent AI action V3 goals, with an advanced setting to preserve the shorthand when saving.

### Patch Changes

- 4ff74d8: Reduce memory use when checking, healing, and uploading large result archives.

## 3.51.4

### Patch Changes

- d83ea9a: Prevent large JavaScript steps from exhausting memory while restoring test history.
- 44fb245: Improve generated pull request summaries with a newer AI model.
- e4c5fc1: Preserve result upload errors and report leftover temporary archives when cleanup fails.

## 3.51.3

### Patch Changes

- e5c6cc3: Keep large CI result uploads within bounded memory.

## 3.51.2

### Patch Changes

- a652e33: Make `ignorePageLoadTimeouts` avoid repeated delays when a page does not finish loading.
- bcb52cb: Capture the initial document request for tabs opened with `window.open()` in network logs.

## 3.51.1

### Patch Changes

- 7018b24: Preserve recent service logs that are already streaming into the test output directory so AI failure classification can inspect them, while pruning entries older than one hour.

## 3.51.0

### Minor Changes

- 472a9b6: Add Turbo mode to project-wide and per-test browser settings to reduce latency by skipping selected readiness and stability waits.
- fd64b96: Auto-heal pull requests now link to the originating CI run. Supported providers: GitHub Actions, GitLab, CircleCI, Buildkite, and Bitrise.
- dbb3031: Keep comments in test and module files when they are saved from the editor
- 472a9b6: Make MCP workflows faster with reusable daemon sessions, batched previews, and parallel element location.
- 72c725c: Let independent CLI invocations upload into one caller-selected run group with
  `momentic run <test> --run-group-id <uuid> --upload-results`.

### Patch Changes

- 1e97e10: Saving a renamed module in the editor now updates the module path in every test that uses it
- 171516d: Preserve response status and headers in network logs when a request does not finish.
- 293eebc: Improve iframe caching reliability for tests that use iframes with dynamic URLs
- 5666036: Stop attempting AI failure recovery when the application under test is broadly failing, and skip retrying repairs that recently failed for the same step.
- c5cf322: Report quarantined test failures without attributing coverage loss to the current run, and stop new triage summaries from recommending coverage review without complete failed-heal quarantine provenance.
- 4243e94: Wait for a concurrent browser install to finish instead of crashing when the install lock is held, and show clear instructions if it is still locked.

## 3.50.1

### Patch Changes

- b3f3213: Improve latency of triage agents.

## 3.50.0

### Minor Changes

- 032f72a: The local editors now show a "What's new" card with the latest Momentic product update, and the support chat bubble no longer overlaps the editor UI.

### Patch Changes

- 7abe4b0: Fix a streaming failure that could interrupt AI steps mid-run
- 4c7d62d: Remove the `why-is-node-running` dependency so that CLI installs no longer fail when the package manager blocks it as an untrusted release
- 9bb3935: Correct keyboard shortcuts when tests use hosted browsers.

## 3.49.0

### Minor Changes

- 5c9a93c: Allow MCP to filter run history by failure category and minimum attempt count.

## 3.48.2

### Patch Changes

- 9cfa2b6: Remove a bundled dependency to resolve two high-severity security advisories
- 5f2c602: Share one knowledge-base retrieval across parallel child explorers in a bugbash run
- 77e66e8: Improve knowledge base retrieval performance and reliability under high load

## 3.48.1

### Patch Changes

- e293627: Improve AI test selection with pull request and commit context, explicit test requests, and reliable shallow-checkout support.

## 3.48.0

### Minor Changes

- 4365e49: Add rule-based routing for Slack notifications: send auto-heal and Explore alerts to different channels based on project name, project directory, repository, or branch, configured in the dashboard.
- 2a42af9: Add conditionals to AI actions.

### Patch Changes

- 0d4d780: Improve how the recovery assessor uses failure classifications before sending recovered runs to triage.
- 5d087fa: Quarantined tests run again by default, restoring the behavior from before 3.47.0. Pass --skip-quarantined to skip them.
- fd3a53d: Improve remote browser durability with provider fallback.
- c829d93: Resolves an issue where an AI action could cache and repeat an action its goal explicitly prohibited

## 3.47.2

### Patch Changes

- 1a7c9e7: Tune recovery assessor behavior to recognize durable test-owned fixes when targeting or configuration changes expose brittle actions.

## 3.47.1

### Patch Changes

- fc97977: Fix a retries value of 1 not being saved in test settings.
- 118c0b2: Failure notifications no longer say a test needs review when its failure was classified recoverable — they report that it failed and note that Momentic's triage agent will review it if your CI runs one.
- ca34e9f: Triage can now identify who a failure belongs to when CI checks out a shallow clone, and auto-heal pull requests and commits explain what broke and where the repair came from.
- 4039549: Review requests are now sent one name at a time instead of as a single batch. GitHub rejects an entire batch with a 422 when it will not accept one of the names, so a coding-agent account among the commit authors cost the review request for every human beside it. Candidates are also checked for merge access before the first request, and a routed repair whose owner GitHub refuses now falls to another person from the same commits, then to the configured default reviewer, rather than reaching nobody.
- b3df020: Auto-heal notifications now say when a repair was already committed to your branch instead of reporting that no healing happened, and auto-heal commit messages are short and link to the run.
- 8cc2664: Auto-heal notifications no longer let one routing decision speak for tests it did not repair, so a test whose heal failed is reported as still needing you instead of being covered by another test's fix, and a batch that was partly committed to your branch and partly routed elsewhere now names each owner.

## 3.47.0

### Minor Changes

- 605026d: Allow triage to revise result classifications when live browser evidence disproves the original diagnosis.

### Patch Changes

- 605026d: Resolves an issue where AI action healing could pass a step whose goal was practically unachievable due to an application issue
- 605026d: Failure recovery can now clear a stale AI Action (v3) cache so future runs regenerate the action
- df0f93c: Upgrade the model for the recovery assessor in the triage command.

## 3.46.1

### Patch Changes

- 3a35bfe: Reject legacy beforeSteps and afterSteps keys in simplified test files instead of failing the run during cache resolution

## 3.46.0

### Minor Changes

- 6bfd774: Add global default overrides in momentic.config.yaml for element check timeouts and key press delays (browser.elementCheckTimeoutSeconds / browser.typeDelayMs / browser.pressDelayMs for web, emulator.elementCheckTimeoutSeconds / emulator.keyPressDelayMs for mobile). Steps that set their own timeout or delay are unaffected.
- 1ccdb8c: Show an "Outdated" indicator next to the CLI version in the run viewer when a newer CLI release is available.
- 2e9f58a: AI Actions now verify success with a goal check against the live app state instead of an auto-generated postcondition.

### Patch Changes

- 3967801: Local editor is now built with the React Compiler for automatic memoization.
- 67a5eea: Fix sorting and filtering controls in the local editor test list
- 21f1d7e: AI action steps can now read the page's accessibility snapshot when a screenshot is not enough
- 3808526: Show the CLI tip after a command finishes instead of before it, and never alongside JSON or quiet output
- a43c3d3: Show an actionable error when sign-in cannot reach Momentic or WorkOS, instead of a bare "fetch failed" or a misleading "invalid API key" message, and tolerate brief network blips while waiting for browser sign-in to complete.
- c76b925: Show a rotating tip when the CLI starts, and call out in the wizard and CLI next steps that naming a skill (e.g. /momentic-test) is what guarantees your coding agent uses it
- 3209994: Routed triage repairs request a review instead of assigning, and always reach a person or team via the new `healing.defaultReviewer` setting.
- fa0b745: Exclude steps added by failure recovery from the completed step counts in progress.json

## 3.45.0

### Minor Changes

- 74486c9: Skip result classification when at least 90% of an org's recent runs are failing, instead of classifying every failed run during a widespread outage.

### Patch Changes

- 294bcb3: Improve error reporting when result classification fails, including a clear message when usage limits are exceeded
- afc15d9: Improve result classification reliability when an Anthropic provider is unavailable.

## 3.44.0

### Minor Changes

- 50b7ecd: Support disabling caching on AI actions to run the agent on every execution instead of replaying previously generated steps.
- 1f3442e: Add an experimental opt-in `ai-routing` value for `healing.onSuccess`, which attributes each repaired failure and delivers it to whoever owns the code rather than to whoever ran the tests.

### Patch Changes

- f1ac00f: Improve result classification reliability

## 3.43.1

### Patch Changes

- d1971c3: Improve the local run viewer: reorganized detail tabs, tidier feedback controls, and simplified run-state chips with hover cards.
- 315c6d9: Improve AI network diagnostics with status, method, URL, and resource-type filters.
- 114324c: Fix element caching so cached elements with long attribute values are reused instead of re-resolved on every step
- a0c8d8f: Deterministically reuse a previous result classification when the same authored test fails at the same step for the same execution failure reason.
- b426e3a: Skip triage, and exit non-zero, when a run group has at least 20 failures and at least half its tests failed — a suite that fails that way is one outage rather than many bugs worth diagnosing separately. Quarantined failures and runs that recovered on retry are excluded from both numbers, and naming runs with `--run-id` always triages them. The check runs before the recovery assessor, so an outage skips those model calls too.

## 3.43.0

### Minor Changes

- 506e63e: Quarantined tests are now skipped by default. Pass --skip-quarantined false to run them without affecting pipeline status.
- a538d00: Support `browser.userAgent: null` to disable the default desktop Chrome user agent override and use the browser's native user agent. The default UA is unchanged.
- 6e0e123: AI Action can dismiss and reauthor stale postconditions if the goal has been achieved.
- 0cf6214: Add momentic ai triage --from-quarantine to heal currently-quarantined tests earliest-first, with --from-quarantine-budget and automatic skipping of tests previously marked unhealable.

### Patch Changes

- 58f4d2b: Fixed triage and heal agents failing to open the artifact files that tool results point at when the CLI runs from a subdirectory of the project
- de54ef8: Fix heal cache candidates failing to load when triaging many runs at once.
- 60808a7: Use the latest text in a step when running it from the editor, instead of the previously saved value.
- 0cf6214: Improve quarantine backlog triage output and let users clear heal status from the quarantine board instead of retrying unhealable tests.
- ee0dbcb: --skip-quarantined now rejects values other than true or false instead of silently disabling the flag, and can be combined with --from-snapshot.
- 25e5acb: Give cloud MCP ability to access quarantined runs
- 1fef34a: Prevent test runs from hanging indefinitely when the browser stops responding during failure recovery

## 3.42.1

### Patch Changes

- 0a92cb6: Discover repo-committed agent skills from the nearest `.momentic/skills` directory at or above the project root, so repo-root skills apply when `momentic.config.yaml` lives in a subdirectory, and warn when healing is configured to follow a triage skill that cannot be found.
- 8242e90: Show AI test selection details in the product: the run group viewer gains an AI test selection tab explaining which tests were selected and why, and the run viewer's AI settings tab shows whether the run came from an AI-selected run group.
- 6ab8e87: Improve the fidelity of archived HTML snapshots in run artifacts
- 0a92cb6: Make zero-test AI selections first-class in results handling: uploads accept a run group without runs when the recorded selection chose zero tests, `results merge`, `results upload`, and `results check` gain `--allow-empty` so the merge keeps zero-run shards' selection plans and the whole chain tolerates a missing or empty results path, `results check` reports a metadata-only results directory as clean instead of failing, and the GitHub PR comment explains why zero tests ran.
- f493d8a: Show how much of a cache resolution was spent evaluating the element versus waiting for it in the run viewer
- 16e5f9f: Ignore machine-generated attribute values (useId tokens, hashes, UUIDs, record ids) in the l-dist cache comparison so rotating framework ids no longer bust otherwise-identical cached elements

## 3.42.0

### Minor Changes

- 5af6d6d: Let the checked-out repository triage skill select successful-heal delivery from the existing cloud AI setting.

### Patch Changes

- 7305085: Show a clear error message when conflicting cache flags are combined instead of exiting unexpectedly.
- ef9c33f: AI Action failures now explain what blocked the agent, not just the last step that failed

## 3.41.0

### Minor Changes

- a520f7d: Add a fill alias for fast text input without per-keystroke delays.

### Patch Changes

- 418ebaa: AI Action no longer runs Playwright code in JavaScript steps; the `usePlaywrightPage` option has been removed
- 4b575a6: Show a clear, actionable error when a --custom-headers value isn't in HEADER=VALUE form (for example when test paths are passed after the flag) instead of exiting unexpectedly.
- 152b3c8: Object and array env vars referenced in templates now render as JSON instead of `[object Object]`
- 4b575a6: Show clear guidance when browser installation fails because the browser download directory is not writable
- 4b575a6: Prevent the CLI from crashing when a run artifact file cannot be written
- 4ae0b11: AI Action failures now say when the agent hit the step budget
- 332a64b: Update bundled dependencies to address security advisories
- 4b575a6: Test runs no longer fail to start when organization settings cannot be loaded from Momentic
- 4b575a6: Skip noisy error logs when collecting git metadata in a repository that has no commits yet
- 4b575a6: Show a clear error message when browsers are not available for your operating system, with a workaround, instead of a raw installation failure
- a81fa26: Improve performance monitoring for unexpectedly slow browser test steps.
- 4b575a6: Show a clear, actionable message when your Momentic API key is invalid or expired instead of failing with an unexpected error.
- c37bdda: AI Action steps can now look up the environment variables available to a run, and see the goal you wrote alongside the version with `{{env.X}}` references filled in
- 07f94cd: Fix bug bash results double-counting a finding that was reported more than once
- 2fed62b: Sign-in automatically issues a new code if you don't finish signing in before the first one expires

## 3.40.0

### Minor Changes

- 8a7bbe7: AI Action steps are now aware of the surrounding test steps, helping them choose end states that set up the steps that come next

### Patch Changes

- 956c3fc: Remove Raindrop analytics integration
- fdff230: Show a clear "page not found" screen when opening an out-of-date link in the local app

## 3.39.0

### Minor Changes

- f089da6: AI Action can now run Playwright code in JavaScript steps via the new `usePlaywrightPage` option, letting the agent inspect the live page while exploring and building steps
- f7af475: Allow AI triage to skip recovered tests that do not need permanent healing.

### Patch Changes

- e3e23ad: Show a clear, actionable message when your Momentic API key is invalid or unauthorized instead of failing with an unexpected error.
- 1a9ea1a: Keep pending heals non-blocking until healing conclusively leaves them unattempted or fails them.
- 51c6130: Improve reliability of uploading large exploration results
- 7e180d6: Explore findings now distinguish product bugs from UX issues, and exploration timelines reliably show every sub-agent lane.

## 3.38.0

### Minor Changes

- 1f00b19: Rebase iterative auto-heal pull requests and review changed Momentic files

### Patch Changes

- 315c5c3: Fix a rare failure that could corrupt run result archives when they grew past the zip size limit
- 7f9b9fc: Fix ambiguous tab selection in the local editor when multiple tabs share the same URL
- c849a74: Element checks stop re-running AI element location when the page has not changed since the last time it could not find the element.
- 8cfad70: Improve cached element validation to avoid stale cache hits when an element's text content was truncated
- d731fe9: Smart waiting no longer re-asks the AI about a page that has not changed since the last time it answered "not ready", and its model chain now demotes providers that are failing or responding slowly instead of retrying them first on every request.
- 3281b0a: Fix a rare crash when authoring or healing a test with a malformed step
- f6ce0b9: Allow AI Select runs to target test paths, consider pull or merge request descriptions, append custom selection instructions with repeatable `--prompt` flags, and honor their configured test budget.
- 0f0b51c: Smart waiting now paces by the minimum gap between checks rather than sleeping a fixed interval after each one, so a slow check adds no extra delay.
- d0a93c9: Raise network-log circuit-breaker thresholds for remote browsers and auto-resume capture 30s after it trips

## 3.37.0

### Minor Changes

- 4e2a001: Give the Explore agent live network-log inspection tools (search_network_requests, get_network_request) as supplemental bug confirmation

### Patch Changes

- 812ddd5: Stop rewriting test and module files with formatting-only changes; saving a test or module whose content doesn't change no longer produces a diff.
- 9f73635: Result classification can now inspect browser console and network logs when diagnosing failed web runs.

## 3.36.0

### Minor Changes

- 52f2168: Fail heal invocations before quarantining eligible non-bug tests that were not repaired or attempted.

### Patch Changes

- 3a82b5a: Cancel in-progress browser steps when an AI agent run stops.
- 9a9772e: Keep failed heal attempts for quarantined tests non-blocking unless quarantine is explicitly ignored.

## 3.35.0

### Minor Changes

- f51d01d: Add `momentic_submit_result_classification` MCP tool for recording the result classification on a specific run.
- ae3e0f0: Add support for agent skills under .momentic/skills for tuning agents such as explore, result-classification, and triage agents.

### Patch Changes

- 4b3d4c7: Discover agent skills recursively within .momentic/skills.
- e53d24c: Change how model streams recover when they fail to call tools correctly.
- 36e0fd1: Improve git context in result classification.
- 106bafd: Teach triage agents how to read file-backed evidence in nested Momentic projects.

## 3.34.0

### Minor Changes

- 275a8e1: Stop AI Triage at its wall-clock timeout while preserving and uploading partial results.

### Patch Changes

- 360fc53: Improve the way manual classification overrides feed into future classifications.
- b7671cd: Improve `--share-diagnostics` trace clarity.

## 3.33.0

### Minor Changes

- 7d0ee56: Add run assertions: plain-English checks verified after each test run by an agent that watches the recorded video.
- 8072ec8: Allow AI Triage healing agents to inspect code and use file-backed evidence.

### Patch Changes

- 2339b11: Make triage repairs model each required user action explicitly instead of relying on ambiguous retries or side effects.
- cf4bca5: Tune the triage agent's adherence to surrounding authorship styles.
- 22fb8bb: Protect browser responsiveness by stopping excessive console diagnostics and recovering stalled scoped CDP sessions.
- 1ca26f6: Improve tracing for ai explore and triage.

## 3.32.1

### Patch Changes

- 8fa82d4: Capture step screenshots by default during AI triage.
- a046445: Return web and mobile editor step results faster.
- c97b061: Improve reliability and reduce AI usage during ai heal orchestration.
- 10a0aa8: Prevent agents from making unnecessary tool calls while editing test state.
- 9831058: Stop writing AI action cache data into test files when healing tests

## 3.32.0

### Minor Changes

- 30d85e4: Apply the configured heal failure behavior when failed tests cannot be attempted.

### Patch Changes

- 9d2a7ee: Improve reliability for long-running AI agent conversations.
- 7ee727a: Make run_step faster by allowing eligible work to finish asynchronously.

## 3.31.1

### Patch Changes

- 34f251a: Improve consistency of AI-generated tests and bug bashes
- 730b885: Print the results URL after an AI bugbash/explore run uploads its results
- f0020b3: Reset interactive test fixtures consistently between browser and emulator replays.
- bfe2e02: Keep concurrent browser sessions responsive while timeline videos are collected.
- dcfccac: Cleaner, unified terminal output for AI classify, triage, and explore commands
- f0020b3: Make triage step screenshots opt-in and reuse recent trace boundary captures to reduce browser contention.
- eeed495: Improve AI triage performance when recording detailed test-healing activity.
- 997b395: Bugbash sub-agents now receive the product URL, credentials, and test-data context, and set up their own preconditions and retry recoverable failures instead of guessing URLs or reporting false blockers.
- 461067a: Fix explore bug reproduction videos showing a frozen page when the agent switched browser tabs during the recording

## 3.31.0

### Minor Changes

- a67c7f7: Add a dot reporter for compact CI output, a Vitest-style run summary footer with a suggested next step after failures, and clickable links in terminal output
- 653d5db: Include test labels in usage reporting so usage can be broken down by label.
- 507cbf1: Unhide the `momentic ai bugbash` command: run `momentic ai bugbash latest` to discover user journeys like explore and report product bugs instead of building tests.

### Patch Changes

- 10f34eb: Add search to folder dropdown in create module and move dialogs
- d036747: Improve AI explore to stop flagging not-yet-available features as bugs and to fully cover the flows you ask it to test.
- a67c7f7: Improve terminal output for AI test selection
- 2151995: Improve result-classification and heal cache reuse across repeated CLI runs of the same test
- b9c3404: Update a dependency to resolve a security advisory

## 3.30.0

### Minor Changes

- 33d9fd9: Persist heal timelines and normal-run web trace assets asynchronously so filesystem writes do not block Playwright operations.

### Patch Changes

- 33d9fd9: Use Sharp when available to reduce screenshot stability comparison overhead while retaining the portable fallback.
- 33d9fd9: Triage now disables console and network debug collection by default and adds `--console-logs` for opt-in console capture. Optional browser debug collection stops after repeated Playwright lag without disabling mocks, custom headers, or explicit request recording.
- 33d9fd9: Record lightweight root-triage resource summaries and capture process-level details only under resource pressure, including peak details in shared diagnostic traces.
- 96c1f1c: Pass full active and overridden classification context to triage subagents as well as clarifying the orchestrator handoff.

## 3.29.0

### Minor Changes

- f8c9c1e: Add `momentic list --changed` to list only the tests changed against the base branch, including tests that use a changed module.
- a91fe78: Show before and after screenshots for executed heal substeps in the run viewer.

### Patch Changes

- f89937c: Fix a high-severity vulnerability in ZIP archive handling
- 991446e: Show both active and overridden classifications to triage agents.

## 3.28.2

### Patch Changes

- b16278f: Report an accurate cancellation reason when an explore run is stopped by its --timeout budget
- a2699ba: Prevent concurrent MCP tool calls from overwriting or corrupting artifact files.
- 3ddb670: Attribute credit usage to the originating environment and platform for more precise usage reporting.
- 3142684: Fix environment scoping for knowledge base entries
- 46f6417: Editor polish: the code editor now focuses automatically when you add a JavaScript step, and the Retries field shows a default placeholder.

## 3.28.1

### Patch Changes

- bd9ca2a: Prevent triage heals from reporting success when an attempted verification cannot run past every edit, and guide heals toward clear, actionable checks.

## 3.28.0

### Minor Changes

- e4f6082: Assign base pull request authors to healing pull requests and include assignees when requesting reviewers.
- 6bac659: Let AI triage respect video settings and keep heal timelines usable without recordings.
- a9ba0f2: Remove deprecated cloud-vs-CLI overlaps: classification enabled/overrideExitCode are now CLI-only (ai.classification), healing behavior (onFail/onSuccess) is cloud-only and the ai.triage config path is removed, and the explore custom prompt is cloud-removed (stays CLI-only via --prompt/--prompt-file).

### Patch Changes

- 5c58761: Reduce AI triage startup time in large repositories and prevent hangs when its streaming connection stops responding.
- 70a2476: Reduce delays from git metadata collection and show preparation progress during AI triage and classification.
- a2fcf6e: Always save cache during AI explore runs
- ae13c01: Restore line wrapping when saving tests so long text steps stay readable, while keeping JavaScript steps exactly as written
- 12ce6c1: Fix missing bug reproduction videos when explore and bug bash runs open new tabs

## 3.27.0

### Minor Changes

- 5736260: Add a hidden `momentic ai bugbash latest` command that reuses the explorer to discover journeys, then delegates each test plan to a bugbash agent that verifies the behavior in a live browser and reports product bugs instead of building tests.

### Patch Changes

- 6def30b: Stop adding module display names to saved legacy Momentic YAML files.
- 19a2ab5: Speed up screenshot resize and crop operations with optional `sharp` support while retaining the portable Jimp fallback
- 33ab726: Explore now generates more focused test plans, splitting distinct journey variations into their own plans.
- acbd2da: Explore now keeps meaningful journey variations as separate tests instead of collapsing them into one.

## 3.26.0

### Minor Changes

- 359bd9a: Add custom classification and triage instructions, and rename the Healing
  settings page to Triage while preserving its previous URL as a redirect.

## 3.25.3

### Patch Changes

- dda2971: Show a clear, actionable message when a test has no base URL configured instead of a generic error

## 3.25.2

### Patch Changes

- 39ff13d: Add explore results links to Slack notifications when results are uploaded.
- 14097a9: Improve explore agent reliability so it retains its reasoning across steps when generating tests.
- ded3ef8: Prevent a failing background start command from crashing the test run
- 063a280: Make failure recovery cache busting durable across future test runs.
- c4a10b3: Fix tab switching reliability and allow separate page-load and retry timeouts.

## 3.25.1

### Patch Changes

- 883abc1: Fix a bug causing reproduction videos to point at the wrong asset

## 3.25.0

### Minor Changes

- 1cc2d7a: `momentic ai explore` can now upload its results — run metadata, the explorer agents' timeline, and browser session recordings — to the Momentic dashboard with `--upload-results` (replaces the previous `--output-dir` archive output).
- 5b399bb: Allow MCP environment tools to recursively filter variables and mobile installed apps.
- 1528f4e: Explore now links each reported bug to a video recording of its reproduction, with start and end timestamps

### Patch Changes

- e1623da: Reject test heals that replace gated destinations with weaker coverage.
- 95b56c2: Improvements to result classification's ability to identify infra
- b1d0d77: Prevent failed Switch Tab steps from being reported as unexpected CLI errors.
- e593779: Install video recording support automatically when installing browsers.
- 93d4a06: AI Action pre-condition and post-condition fields now use the same multi-line editor as the goal.
- 6c858de: Help test healing inspect environment values before updating references.
- 143683b: Fix test runs failing when a page load timeout exceeds the 60 second maximum
- e4c05ec: Explore bug reports now include the expected and actual behavior for each bug.
- ae338d5: Stop triage attempts when persistent browser infrastructure failures prevent reliable investigation.
- 96d8bec: Preserve readiness-check wait budgets when healing tests.
- 854623c: Warn agents when browser state retrieval or session reset responds slowly.

## 3.24.0

### Minor Changes

- 7117ade: `momentic ai explore` now writes a trace archive (run metadata, the explorer agents' timeline, and browser session recordings) to `--output-dir` when one is provided.
- bed389e: Add the momentic_quarantine_list MCP tool for paginated quarantine triage with latest failed run and healing details
- 0984474: Add a new `steps` reporter (`--reporter steps`) that logs each step as it starts and finishes, with nesting, sections (setup/main/teardown), and per-step durations — useful for CI logs

### Patch Changes

- cbab3d0: Teach the healing agent that `{{env.X}}` in a step preserves the intent to render an earlier captured or generated trait.
- 5e1fa6d: Reduce redundant AI Select test selections by retaining representative coverage for distinct changed behaviors.

## 3.23.0

### Minor Changes

- b5ae023: Support passing --prompt and --prompt-file multiple times for `ai explore`; all values are appended to the explorer's instructions in order.

### Patch Changes

- 762c4ff: Tune the heal agent to make complete, minimal repairs and reject access-gate workarounds
- 6de87b2: Fix run output stacking duplicate status lines instead of updating in place on some terminals
- 461e0af: Show a clear, actionable message when no Momentic project configuration can be found instead of failing with an unexpected error.
- 35c132a: Improve result classification's recognition of MOMENTIC_ISSUE and conditional steps related to INFRA
- 16866f1: Improve result classification accuracy for small copy changes and clarify momentic_list_runs branch filtering
- 61bfbee: Improved the healing agent's reliability with clearer definitions of error cases and guidance

## 3.22.2

### Patch Changes

- 7e30b87: Fix the local editor's test options save button becoming disabled after switching tabs.
- 93f1fc8: Refine explore --granularity levels: low covers the happy path of the main flows plus important failure states, medium covers the happy path of every interaction, and high covers every flow in depth including its failure modes.
- 9893873: Improve result classification's ability to identify infra issues
- e245598: Tune the heal agent to reject unfixable app changes and repair all affected steps
- 1f1dbf0: Fix a bug where explore and heal browsers would sometimes close mid-run.
- cd07de1: Tune heal guidance for stale UI repair decisions

## 3.22.1

### Patch Changes

- 2d8b250: Fix `momentic ai explore --build` sometimes leaving a browser window open after a test builder finishes
- df2c548: Explore now shows reasoning and tool calls in a fixed-height window that scrolls to the latest activity, so the output no longer wipes and is easier to follow.

## 3.22.0

### Minor Changes

- 371601c: Add `momentic ai explore diff [commit range]` and `momentic ai explore latest` subcommands. `momentic ai explore` now runs `diff` by default; existing `--base`/`--head`/`--seed` flags still work but are deprecated. `explore` now defaults `--parallel` to `auto`.
- f30ea8d: The explore agent now builds tests by default; pass --dry-run to only discover and log changed journeys without writing tests.

### Patch Changes

- 683dffa: Explore now proposes tests for refactored user flows that aren't yet covered, instead of skipping them as unchanged.
- 683dffa: Fix the explore builder's completion summary sometimes showing earlier progress text instead of the finished test.
- 7156208: Fix Ctrl-C sometimes not cancelling promptly during `momentic ai explore` while the agent is running or validating steps
- 683dffa: Explore now saves new tests in a folder that matches your existing test layout.
- 9b200c5: PR status comments and Slack notifications now show a status icon and a per-run-group status table.
- 1f0ae50: Improve step guidance for AI test agents

## 3.21.0

### Minor Changes

- a3e7bfc: Include reported bugs in `ai explore --json` output
- 9c65d9e: Improve terminal output: home-directory paths are shown as `~`, remedy commands are highlighted, warnings that repeat per test are shown once, the cursor is restored after live progress output (including on Ctrl-C), API keys are redacted from console output, and environment-error hints are shown at most once per day. The CLI also honors `CLICOLOR`/`CLICOLOR_FORCE` color conventions, detects color support separately for stdout and stderr, and no longer crashes when output is piped to a command that exits early (e.g. `momentic ... | head`).
- 9c65d9e: Add a `doctor` command that checks installation health (CLI and Node versions, authentication, browsers, project configuration), warns when project configuration is out of date (legacy file format or older agent versions, with `upgrade` as the remedy), and can remove deprecated configuration options with `--fix`. Environment-related errors now suggest running `doctor`.

  `doctor` also checks connectivity to the Momentic server (HTTPS reachability, TLS certificate verification with a `NODE_EXTRA_CA_CERTS` remedy when a proxy intercepts traffic, WebSocket upgrade, and system clock skew) and reports proxy environment variables, free disk space, and whether the temp and results directories are writable. The mobile `doctor` additionally checks the bundled Appium drivers and reachability of the remote emulator provider, treats Java and `ANDROID_HOME` as local-emulator-only (only `adb` is required for remote emulators), and notes that iOS uses remote simulators with no local setup. Pass `--json` to emit the full report for support tickets.

### Patch Changes

- b9571b6: Improve ai explore test-plan quality and ensure findings from parallel exploration are fully aggregated
- 2f67c6a: Improve the readability of the `apply patch` preview diff
- 4443a48: Improve error reporting when AI model calls fail during AI actions
- 2f67c6a: Improve the readability of the `upgrade` command output, including the dry-run preview
- 6570ef5: Improve heal triage guidance to preserve step metadata and validate upstream repairs before rewriting assertions.

## 3.20.0

### Minor Changes

- fd327bb: Add "Move to top" / "Move to bottom" to the editor step right-click menu, for both a single step and a multi-step selection

### Patch Changes

- 0d82b72: Optimize for broader coverage when seeding tests rather than doubling down on existing coverage
- 16a81fc: Clarify heal guidance for maximum timeout rules.
- 0d82b72: Improve explorer agent adherence to existing patterns

## 3.19.0

### Minor Changes

- 93a24b7: Enable result-classification cache reads by default for multi-run `ai classify`, write new cache entries only when `--save` is set, and add `--no-cache` to skip cache reads and writes.
- 67e87ff: Duplicate multiple selected steps at once from the editor's right-click menu

### Patch Changes

- 06d1bb6: Installing Chrome for Testing now also downloads the browser build required for headful runs
- cdc143a: `upgrade` now asks for confirmation before rewriting tests to the simplified format when the project is not already using it (skip with --yes)
- 06d1bb6: Improve the error message shown when the installed browser does not match the version expected by the CLI, such as after upgrading

## 3.18.0

### Minor Changes

- 4dd6a58: Add a newrelic reporter that pushes test results to New Relic as custom events, configured via the reporting.newrelic block in momentic.config.yaml

### Patch Changes

- e453d8c: Improve heal repairs by verifying each previewed step actually produced its intended effect on the page
- 557e934: Improve auto-heal rejection behavior when a product gate makes the original tested flow unreachable.
- 600eb6b: Improve explore agent reliability when working on large surface areas
- b128379: Show how long each step takes in the AI action agent trajectory in the run viewer

## 3.17.0

### Minor Changes

- 64d4911: Add `disableLdistCacheValidation` browser config option to skip Levenshtein distance checks during cached element resolution.
- 680d785: Add `saveCacheOnCancel` config option to save partial step caches when a test run is cancelled or times out

### Patch Changes

- 591201d: Tune how agents handle infra flakes with readiness checks.

## 3.16.5

### Patch Changes

- f2bbb5f: Fix a rare crash that could occur when an operation was cancelled or timed out
- f712ea3: Stream the browser-execution trace live into the editor step detail so the trace waterfall fills in as spans open/close, instead of only appearing when the step finishes.

## 3.16.4

### Patch Changes

- cb50758: Improve triage agent's understanding of locator caches
- dde657b: Improve triage repairs to preserve the original intent of a check rather than re-anchoring to recently changed copy
- 5ffc925: Show before and after steps in the heal attempt test state viewer
- 620d825: Modules are expanded by default when added via the step picker
- c552c9f: Gracefully handle system dependency installation failures (e.g. spawn su EACCES) during browser setup instead of crashing
- 2f35261: Add --interactive support for momentic ai triage so users can continue from triage results into an interactive follow-up session.
- 5578285: Honor manual classification overrides during triage agent runs.

## 3.16.3

### Patch Changes

- 1d49ffe: Improve triage repairs when the product replaces a checked element, and reduce unnecessary re-anchoring of assertions on slow-loading content

## 3.16.2

### Patch Changes

- 6dde41d: Fix step migration that incorrectly renamed user-defined JavaScript variables named `inputs` to `env`
- b062ab7: Upload heal traces (timeline + videos) to the Momentic dashboard when triaging already uploaded runs with --save
- 0164f00: Fix saving of tests with long multi-line JavaScript steps introducing unwanted line breaks in the code
- 246feb8: Fix heal timeline videos being timestamped at the end of the heal session instead of the actual recording start on remote browser runs

## 3.16.1

### Patch Changes

- 8a803d6: Improve auto-heal reliability with more intent-preserving repairs and stronger assertion choices
- 05bcc22: Improve test healing to re-target checks onto the element that replaced a removed one when it serves the same purpose in the flow.
- 001dd65: Improve latency of running cached steps in the ai triage command.
- 2338385: Improve AI agent guidance around step cache usage

## 3.16.0

### Minor Changes

- 619218d: Record a heal trace during heal sessions so healed runs include a browsable timeline of the heal in the run viewer

### Patch Changes

- c25b2ae: Fix run viewer heal playback: clicking a step now seeks correctly, play resumes instead of restarting, and playback continues across multiple recorded videos.

## 3.15.1

### Patch Changes

- c98a9e1: Pressing Escape in the editor now dismisses one layer at a time — a layered modal or a focused input is cleared before the side panel closes.
- 10e1432: Improve cached element resolution reliability for elements with dynamic content
- 594612a: Include screenshots on failure recovery steps

## 3.15.0

### Minor Changes

- 75eb654: Explore agent can now switch between environments at runtime

### Patch Changes

- a1be78f: Fix Run To in editor to resume after last executed step instead of re-running from the beginning

## 3.14.0

### Minor Changes

- 6dac91a: Support running only multi-selected steps via context menu or keyboard shortcut

## 3.13.1

### Patch Changes

- 36270c6: Improve AI action reliability on bulk, multi-step, and form-entry tasks.
- af61e64: Modules are expanded by default when created
- 0dc6ad0: Fix type steps without a target failing instead of typing into the focused element
- a87f5b0: Allow passing an optional timeoutSeconds to momentic_poll_runner to wait for active runs to finish.
- 9a0ae2e: The explore agent always runs with a live browser session; --browser is now a no-op.
- dd8f42d: Improve explore agent journey capture during long runs.

## 3.13.0

### Minor Changes

- 87661b6: Add a soft timeout to momentic_run_step which responds after 30 seconds with the currently executing step and how to poll for the result
- 87661b6: Add momentic_poll_runner tool which responds with the status of executing steps on the session
- f33cc04: Auto-heal now considers what changed in your code when grouping and fixing failing tests, for more accurate repairs.
- 87661b6: Significant skill update for how to handle the new run step status tool and polling pattern

### Patch Changes

- 48a0bc4: Improve triage agent's judgment to not treat recovered runs as the test's intended flow when healing
- 0b5555e: Improve triage agent's ability to discern when it should not edit functioning target descriptions

## 3.12.1

### Patch Changes

- 151f2cd: Auto-scroll step list to keep the executing step in view during test runs

## 3.12.0

### Minor Changes

- d19a07d: Save a video recording of each heal attempt's browser session as a local artifact

### Patch Changes

- 465a07e: Fix collapsed conditional steps unexpectedly expanding during test execution
- 44bf5b5: Restore editor autoscroll behavior for streaming step output.
- d4fadc2: Round scroll pixel values in step display

## 3.11.0

### Minor Changes

- dd92c87: Add --share-diagnostics support to `ai triage` for when you need momentic's help debugging what went wrong
- f3e61d2: Add setting to request original commit authors as reviewers on heal and explore pull requests.

### Patch Changes

- 25f34f7: The explorer agent is more rigorous when surfacing bugs
- 25f34f7: The explore builder is more consistent with existing environment usage
- 9d99843: Pause editor trajectory autoscroll while users are scrolled away from the bottom.
- d70920c: MCP server now cleans up active sessions and emulators when the MCP client disconnects

## 3.10.3

### Patch Changes

- 231dd9d: Fix issue introduced in 91a9ddb that caused test saving and the auto-save indicator not to work in the local editor on the initial load

## 3.10.2

### Patch Changes

- be1fef2: Keep the MCP daemon alive while long-running steps are executing
- f80d082: Add `momentic checks unused` to report modules that aren't referenced by any test.

## 3.10.1

### Patch Changes

- 272c754: Fix folder dropdown scroll behavior in create module and move dialogs

## 3.10.0

### Minor Changes

- da7ac6e: Improve self-healing's ability to detect and repair steps that fail due to a race with an unfinished page state transition

### Patch Changes

- fb7d6c1: Improve self-healing's diagnosis of why a page state transition failed to occur and repair it

## 3.9.2

### Patch Changes

- 91a9ddb: Simplified v2 YAML output no longer includes schema version metadata, default viewport (1920x1080), or default browser type (Chromium).
- cbe07bc: Make the recovery assessor more accurate in passing forward recovery information and at assessing whether we should triage a recovered test.
- fcbd94d: Improve AI Action reliability for value-setting goals (set/select/toggle) and recovery from recoverable validation errors like required-field warnings.
- 50a677b: Triage and explore agents follow rules in your knowledge base for guidance around REFRESH and timeout usage

## 3.9.1

### Patch Changes

- 15b966a: Fix misleading error when ffmpeg is missing — now names the actual missing component instead of incorrectly blaming the browser
- 104196f: Fix CLI hanging indefinitely when failure classification encounters a provider error

## 3.9.0

### Minor Changes

- 5b90439: Add --budget flag to control the maximum number of tests generated by the explorer

### Patch Changes

- ce118d4: Simplify progress tracking to count each step as one unit regardless of nesting
- 43bc4aa: The momentic, momentic-mobile, and wizard CLIs now require Node.js ^22.12.0 || >=24.0.0 and exit at startup with an actionable message when run on an unsupported version.

## 3.8.2

### Patch Changes

- 4dad99f: Fix clearing cached steps for AI Actions nested inside modules in the editor

## 3.8.1

### Patch Changes

- 04a27e0: Fix live progress reporting: completedSteps in progress.json now increments after each step finishes instead of only at run completion
- 1c5489f: Ensure `ai explore` wraps up and submits its findings before hitting its turn limit, so long explorations no longer end without results.

## 3.8.0

### Minor Changes

- cc6fa40: Show cache status (hit, miss, busted, or not cached) and the reason in the run viewer step details
- 069f9d1: Add a while loop step that repeats a set of steps while a condition holds and/or up to a maximum number of iterations

### Patch Changes

- a51477a: Add --save/--no-save support for ai triage heal metadata persistence and improve remote-browser initial navigation reliability.
- fc42367: Write a live progress.json file to the run output directory during local test runs, reporting per-test and overall completed/total step counts so long runs can be monitored (e.g. forwarded to external reporting).
- f10ceae: Preserve the real failure reason (e.g. configuration error) when a TestFailureError escapes the test runner, instead of always reporting "Unknown Momentic platform error"
- 8b40178: Update notification now shows the version you'll actually upgrade to and warns when it's a new major version with potential breaking changes
- e6831ad: Make browser installation more reliable: re-install partially-downloaded browsers instead of later failing with "browser is not installed", and fix garbled progress output during the download.

## 3.7.3

### Patch Changes

- 1554b9a: The "update available" notice now links to GitHub Releases for the changelog.

## 3.7.2

### Patch Changes

- 2fd5279: Improve reliability of the explore and build agents with an additional AI model provider fallback

## 3.7.1

### Patch Changes

- 507f5aa: Ensure `ai explore --build` reliably proceeds to build the tests it discovers instead of sometimes stopping after planning.

## 3.7.0

### Minor Changes

- 12923d7: Triage can now decide to heal recovered tests as well to make them stable.

### Patch Changes

- e4adcef: Running a test with no base URL and no BASE_URL environment variable set now reports a clear configuration error instead of failing with an internal error.
- 8c3d0ff: Default the explore --timeout to 60 minutes when running in --seed mode
- 9734965: Fix knowledge base citation links in the local run results viewer to correct url

## 3.6.0

### Minor Changes

- 59ee659: Add JSON run reporter

## 3.5.1

### Patch Changes

- e90f87c: Fix `ai explore` live output so builders nested under sub-explorers are shown.

## 3.5.0

### Minor Changes

- 2d2119a: Add a `--timeout <minutes>` flag to `ai explore` (default 15) that aborts the run when the wall-clock budget is exhausted and emits partial results instead of running until the CI job is killed. A timed-out run exits with a non-zero code so CI surfaces it as incomplete. Build/edit sub-agents are each capped at two-thirds of the timeout so a single stuck builder can't consume the whole budget.
- d475fd9: Test healing now consults your organization's knowledge base, scoped to the test being repaired, so agent rules, terminology, and known flows you've documented are taken into account when fixing failing tests.

### Patch Changes

- 9280903: Improve `ai explore` test planning to lead with positive, end-to-end assertions on intended behavior (rather than over-indexing on regression checks that a fixed bug no longer occurs) and to propose broader coverage for changed behaviors (control variants, alternate paths, boundary/inverse states, and persistence). Both improvements apply to the planning and build phases.
- 2641609: Improve `ai explore` to avoid spinning up unnecessary parallel exploration, reserving it for splitting genuinely large workloads

## 3.4.1

### Patch Changes

- 17157a0: Reduce quarantined test detail representation in GitHub comments.

## 3.4.0

### Minor Changes

- fad7310: Add a `--granularity <low|medium|high>` flag to `ai explore` to control how specific the generated test plans are. At `high`, seed runs now explore exhaustively and propose a plan per control, option, and state — far more granular coverage for dense surfaces like editors.

### Patch Changes

- 4adf641: Share triage and result classification caches across branches when the classification isn't app change or bug
- fa1191b: Improve cached element matching on pages with autogenerated attribute values.

  This may negatively impact cache resolution the first time this version is used for elements that contain attributes that look auto-generated.

- 903220a: Add opt-in multi-process `momentic run` via `MOMENTIC_WORKER_PROCESSES`, splitting `--parallel` across worker processes.
- e7fa08d: Fix explorer browser sessions closing mid-run during exploration
- e819f52: Improve auto-heal craftsmanship by de-brittling inherited literals when authoring replacement steps during a repair

## 3.3.0

### Minor Changes

- 3218c78: `ai explore` now surfaces potential product bugs it spots in the Slack notification (org channel and author DMs), alongside the existing terminal and markdown summaries.

### Patch Changes

- 850aee3: Describe `force` / "disable stability checks" in the CLI step authoring guide as risky and guide against their usage. Add guardrails for triage to drop stale modifiers when unnecessary and part of the break site
- c5a2626: Smooth out the run progress spinner animation
- 8fdca59: Improve reliability of long `ai explore` runs: transient connection and service errors are now retried, a failed sub-explorer no longer aborts the whole run, and partial results are preserved when a run is interrupted

## 3.2.0

### Minor Changes

- 96dc532: Add a `--json` flag to `ai explore` that prints the explorer result (changed journeys and proposed test plans) as JSON to stdout and suppresses the live streaming UI.
- ab65626: Add an explore agent granularity setting (low, medium, high) that controls how specific generated tests are, from high-level features down to individual UI elements.
- 23e869b: `ai explore` now surfaces potential product bugs it spots while analyzing changes and building tests, listing them in both the terminal output and the markdown summary.
- c0ac14a: Add a `--no-classify` flag to `momentic run` to skip AI classification of failed runs. Show a clear "classifying failure" indicator while classification runs (in both interactive and non-interactive terminals), and fix the live test status line repeating itself on very narrow terminals.
- 635db83: Add `momentic snapshot` to create self-contained test snapshot zips (resolved caches, modules, environment, and Momentic version baked in) and `momentic run --from-snapshot` to replay them in complete isolation with no cache reads or writes

### Patch Changes

- 23e869b: Improve reliability of long `ai explore` runs by retrying dropped streaming connections instead of failing the run
- 46ffb2c: Always save AI classifications to uploaded runs with --save flag
- ab638ce: Show a clean, actionable error message instead of a stack trace when a command fails with an expected error such as an unknown run group or run ID.

## 3.1.0

### Minor Changes

- 2836e29: Add browser.exposeNetwork config option to expose additional hosts to remote browsers via the connecting client's network

### Patch Changes

- a99ab79: Improve auto-heal accuracy when intentional copy or label changes break brittle assertions
- 693f21d: Resolve security advisories in bundled dependencies.
- 4678268: `click` with `waitForDownload` now captures downloads that open in a new tab (via a `target="_blank"` link or `window.open`), and closes the transient tab opened for the download.
- 4081c30: Editor Run button is now a split button to choose which sections (Setup, Main, Teardown) to run.
- 7eb2fd5: Fix run-group links in auto-heal pull request descriptions pointing to localhost instead of the Momentic app

## 3.0.2

### Patch Changes

- 595b021: Fix the run viewer's expand-editor modal so the code editor fills the modal height

## 3.0.1

### Patch Changes

- 2c7e648: Editor tab filters (Console, Network, and others) now persist when switching between tabs, clearing only on page refresh
- 280b186: The Momentic editor now validates AI agent versions when it launches, so starting it with a retired agent version pinned in ai.agentConfig fails immediately with a clear error instead of only erroring once a step runs.

## 3.0.0

### Major Changes

- 209ade0: Removed the `browser.bustCacheOnBoundingBoxChange` config option. The element
  cache is now invalidated automatically when an element's bounding box changes,
  so the setting is no longer needed — remove it from `momentic.config.yaml`.
- 209ade0: The legacy `v1` AI agent configurations for the locator, assertion, visual
  assertion, and text extraction agents have been retired and can no longer be
  selected. Runs that pin one of these agents to `v1` (via `ai.agentConfig` in
  `momentic.config.yaml`) will now error — switch to a current version.
- 209ade0: Dropped support for Node.js 20, which has reached end of life. The CLIs now
  require Node.js 22 or newer.
- 209ade0: AI Action steps now default to the V3 agent everywhere. The older V2 agent is marked "Legacy" and can no longer be selected for new AI Action steps in the editor; existing V2 steps continue to run.

### Minor Changes

- 209ade0: New projects created with `momentic init` now set
  `browser.disableSecondaryCacheResolution: true` by default. Existing projects are
  unaffected; set it to `false` in `momentic.config.yaml` to change this behavior.

### Patch Changes

- 209ade0: Hybrid selectors are now enabled by default: `browser.hybridSelectorMode` now
  defaults to `prefer` when unset. Set it to `off`, `test`, or `always` in
  `momentic.config.yaml` to change this behavior.
- 209ade0: Test run videos now default to `on-fail`: a recording is captured for every run
  but kept only when the test fails. Pass `--video true` (or set `recordVideo: true`)
  to keep every recording, or `--video false` to disable recording entirely. The
  deprecated `--record-video` flag has been removed — use `--video` instead.
- 209ade0: Updated the bundled Playwright to 1.60.0, picking up the latest browser engines
  and upstream bug fixes.
- 209ade0: New projects now default to the latest version of each AI agent, pinned to an
  exact sub-version. Pinning keeps the default from changing unexpectedly when a
  newer revision of the same agent ships. Existing projects that already set
  `ai.agentConfig` are unaffected.
- 209ade0: Element checks now surface a caching caveat in the editor — reminding you that
  they reuse the cached locator and suggesting an AI check for complex assertions.
  The "Visible" condition shows a tooltip clarifying it uses Playwright's
  definition of visibility, and the "Exists" condition is no longer offered for
  new checks (existing checks that use it continue to work).

## 2.144.0

### Minor Changes

- 4b7dcfd: Add a `--regenerate-heal` flag to `momentic triage`/`heal` that re-heals failures from scratch instead of reusing previously cached heal solutions.
- bc0925e: Feedback for agent actions will autogenerate knowledge base entries

### Patch Changes

- d73b634: The CLI now shows important announcements from Momentic after checking for updates.
- 5013c68: Automatically reapply a previous successful heal when the same test fails the same way again, so healing is faster and more consistent.

## 2.143.0

### Minor Changes

- ea406bc: Add a --no-code mode to `momentic ai explore` that runs the explorer without git or filesystem access, grounding its analysis in the live app through the browser (force-enabled in this mode).

### Patch Changes

- 2a37eee: Reuse successful heal solutions across runs: when a previously accepted repair matches a failing step's classification, autohealing can re-apply that repair instead of healing from scratch.
- 0ff4f2e: Fix crash when saving a test that removes all route mocks (a removeRouteMock step with no key)
- 6befe45: ai explore now tags each proposed test plan with an importance of low, medium, or high
- 08c1115: Auto-heal can now submit shared module changes in the pull requests, commits, and patches it creates, not just test-file changes.

## 2.142.0

### Minor Changes

- faae2f6: Remove the --exit-code-on-heal flag and the ai.triage.exitCodeOnHeal config option from momentic ai triage/heal. Successfully healed tests no longer change the exit code on their own; configure post-heal behavior in your cloud Healing settings instead.
- 7d8b115: Add --on-heal-success and --on-heal-fail flags to `ai triage`/`ai heal` to override the post-heal action (e.g. open a pull request or print a git patch) without editing momentic.config.yaml.
- 87590a6: Agent-generated PRs now append a links section to the PR description pointing at the source and results they're based on.
- 471798f: Restore the --prompt and --prompt-file flags for ai explore (and ai seed), letting you append custom instructions to the explorer agent inline or from a file.
- 1e3cbcd: Add a --browser flag to ai explore (and --no-browser to ai seed) that gives the explorer and seed cartographer a live browser session, starting on a blank page, so they can navigate the running app to ground their analysis.

### Patch Changes

- eefda9b: Improve triage reliability by continuing further through the failed test after repairing a step, so later steps impacted by the same or an unrelated change are also resolved
- bfa8b08: Improve auto-healing reliability so harder fixes are less likely to be abandoned before completing
- 70a8d80: Patch high-severity security vulnerabilities in bundled dependencies
- 7c7ea1a: Improve triage agent to recover faster when a UI element has moved or been removed, spending fewer steps before settling on the correct fix.
- 870a0a2: Triage orchestrator now passes more content into the subagent's context to further minimized duplicate work.
- 52ef59b: Add CLI commands (session-start, session-terminate, session-state, session-env, preview-step, run-step, splice-steps) that mirror the Momentic MCP tools and share the same long-lived daemon session. Agents can now author over MCP and run long-running AI Action steps via bash, avoiding the 60-second MCP tool-call timeout.
- 291bba9: Fix run viewer video player sizing issues, add spacebar keyboard shortcut for pause/play
- 4064902: Keep running when project configuration cannot be reloaded after a file change (e.g. a temporary network issue); the previously loaded configuration is kept instead of surfacing an error.
- 82ccff9: Dragging a step over a collapsed module or conditional now auto-expands it after a brief hold, so you can drop steps directly inside. It re-collapses if you drag away without dropping.

## 2.141.1

### Patch Changes

- 7f50db5: Fix triage so retrying a group of related test failures re-runs the repair instead of incorrectly marking the tests as unfixable

## 2.141.0

### Minor Changes

- 4f73ab7: The `momentic ai classify` and `momentic ai triage` commands now accept multiple run IDs or URLs via `--run-id`, letting you classify or triage several runs in one invocation.

### Patch Changes

- 580da5a: Update ai triage sub-agents to recognize custom result directories
- 8503263: Improve auto-heal accuracy by looking ahead through the rest of the test to repair every later step broken by the same change
- 0c4a8ca: Cap the number of AI element re-resolutions during an element check so checks with long timeouts no longer make redundant locator calls.
- 546d7ae: Mobile AI checks now support a visual-only assertion mode that evaluates the screen using the screenshot alone, without the accessibility tree
- 89a9dd2: Fix tests failing to launch after renaming a module: references to the renamed module are now updated automatically.

## 2.140.0

### Minor Changes

- 161895b: Full support for `--run-id`, `--git-commit`, and `--run-group-id` in `ai classify` and `ai triage`.
- 2c32dde: Add `--skip-quarantined` to `momentic ai triage`/`heal` to exclude quarantined tests from healing (mirrors `momentic run`).
- 4234a76: Show the past results the AI recalled from memory inline in each step's execution trace, including whether a new result was saved.

### Patch Changes

- 76735ab: ai explore (build mode) can now delete obsolete tests for removed journeys, and rename/redescribe tests via the test-settings tool
- 7310f04: Explore Slack notifications now only fire from CI runs that discovered journeys and attempted to build tests.
- 1cc1f61: ai explore and ai heal now leave changes on disk and ignore cloud delivery settings when run outside CI; pass --patch to print a git patch to stdout instead.
- 0582312: Improve triage agents' understanding of a test's original intent to avoid silently dropping implicit checks when repairing failures
- ed9a584: Fix mobile AI action runs sometimes showing an empty agent trajectory in the editor, and show the correct AI action version in the run viewer
- 1806f1f: Improve consistency of failure classification by reusing prior classification results for the same test
- e71233b: Show a clear configuration error when a file upload step points at a directory instead of a file
- f5f6085: Improve AI test authoring guidance to describe element targets and assertions against the current page state
- 59b662d: Improve reliability of run telemetry delivery on networks with restricted egress
- e3161d1: Improve AI test authoring and healing to favor semantic assertions over brittle exact-text matching unless the exact value is genuinely required

## 2.139.0

### Minor Changes

- bf0a6b4: Add ability to ungroup a module instance in the editor, inlining its steps in place

### Patch Changes

- e5be34f: Add guidance to the explore and triage agents to better decide the strength of their implicit secondary assertions and to stop referencing stale state in assertions.
- f9bfd98: Clarify the agent guidance for JavaScript steps, and explicitly forbid certain browser interactions for Explore and Triage agents.
- ae2e6dd: Fix a rare error that could cause AI Action steps to fail to complete

## 2.138.3

### Patch Changes

- 338eb6c: Fix `install-browsers` so installed browsers are no longer unexpectedly removed when another Playwright-based tool shares the same browser cache, which previously caused "required browser executables are not installed" errors when running tests.

## 2.138.2

### Patch Changes

- c600158: Improve element targeting and assertions for icons and images that appear differently in the screenshot than in the page structure for explore and triage agents.

## 2.138.1

### Patch Changes

- 2ff02a0: Improve the triage agent's ability to instil scaleable testing patterns.
- 56599a9: Remove the unsupported --prompt flag from ai explore
- 225ed71: Make the momentic agents use --timeout less when it is unnecessary to specify

## 2.138.0

### Minor Changes

- a943b3a: Add a --allow-recovered flag to `momentic results check` that treats runs which passed via in-run failure recovery as clean (exit 0).
- a943b3a: Add `momentic results check`, which exits non-zero unless every non-quarantined run in a merged results archive passed cleanly (no failures, cancellations, in-run failure recoveries, or failure classifications). Use it as a CI gate after `momentic results merge`. `--json` prints per-run detail for each not-clean run plus a `summary` of descriptive per-category counts (total, clean, quarantined, failed, cancelled, recovered, classified).
- a943b3a: Classification is now controlled from your project instead of the cloud dashboard (app.momentic.ai). Whether classification runs and how it affects your CI exit code now live in momentic.config.yaml (ai.classification: true, or { enabled, overrideExitCode }); your failure categories and their actions stay managed in the dashboard. Enabling classification no longer changes exit codes on its own: overriding the exit code is now opt-in (default off), so the classifier records categories while failed tests still fail CI unless you opt in. Opt in via ai.classification.overrideExitCode: true or the bare --classify-override-exit-code switch on momentic run. Add --exit-code-on-heal <0|1> to momentic triage/heal to control the exit code when tests are auto-healed. Existing dashboard classification settings still apply as a fallback until you move them into your config.
- a943b3a: Add an `ai.triage` block to momentic.config.yaml for configuring `momentic ai triage`: set the post-heal behavior (`onHealFail`/`onHealSuccess`) and the exit code used when tests are healed (`exitCodeOnHeal`). These settings take precedence over the equivalent options in the cloud dashboard, and the `--exit-code-on-heal` flag overrides them per run.

### Patch Changes

- 1e53ab9: When a required browser isn't installed, the error now names the missing browser and gives the exact command to install just that browser. Command suggestions printed by the CLI now include a runnable prefix so they can be copy-pasted and run directly.
- ec1e633: Fix missing spacing between fields and sections in the app's dialogs and panels
- 247b20b: Improve AI Action observability metadata and agent issue reporting

## 2.137.0

### Minor Changes

- 320bda0: The v4 locator, assertion, and visual-assertion agents are now the recommended default. New projects use them automatically, and existing projects that don't pin those agents in `ai.agentConfig` will pick them up as well. v4 is faster and more reliable than v3.
- f11d769: Improve observability for AI Action test steps
- c2634ec: Result classification can now use git history, branch diffs, and service logs stored in the test output directory as additional context when categorizing test failures

### Patch Changes

- 22f7005: Exclude bot accounts from automatically attributed pull request co-authors
- d661a26: Add unsaved changes dialog to editor
- a93adc0: Refine auto-heal risk PR comment summary

## 2.136.0

### Minor Changes

- a105599: Add `momentic results check [folder]` to report which runs failed, were canceled, or were quarantined in a results folder (use `--json` for machine-readable output).

### Patch Changes

- 0cf1966: Include a link to the pull request in heal details when healing opens a PR
- a2e7a04: Show clearer error message when runs are blocked due to usage limits
- ebad3af: Add guidance for the triage agent to better use environment variables.
- 51eee5c: The triage command now streams agent reasoning in its output panes
- 36363fe: Fix renamed module name not updating immediately in the editor's repository view

## 2.135.1

### Patch Changes

- 52deec7: AI test generation now builds broader baseline coverage, persists more of the tests it successfully builds, and finishes with a synthesized report covering each surface, the tests written to disk, gaps, and recommended next steps.
- 3df9e07: Tune the behavior of the healing agent to properly choose the write style of check and stop over using checks when implicit state changes are enough validation.
- ab6decc: Update dependencies to resolve a security advisory

## 2.135.0

### Minor Changes

- 215e08a: Integrate Knowledge Base into AI Action v3

### Patch Changes

- a078d46: Improved reliability when switching between tests in the editor
- 6f203c7: Stop stray internal warning messages from appearing in CLI output, so machine-readable output such as `ai classify --output-format json` always stays valid JSON
- 34695af: Improve test step cache reliability for apps that render non-deterministic element ids, reducing repeated cache misses and AI re-heals across consecutive runs

## 2.134.2

### Patch Changes

- 310c61a: Improved CSS selector generation reliability for deeply nested elements and reduced selector churn from auto-generated framework attributes
- 7cca197: Auto-heal and explore pull requests now credit contributors as co-authors: when running against an existing pull request, every author of that PR's commits is credited, and otherwise the author of the originating commit is credited.
- c3cc5da: Improve test run speed by reducing redundant page-stability waits during element resolution
- ed97c17: Added observability around element target resolution.
- e5a50e1: Don't abort momentic run when snapshot step-identity cache restoration fails; degrade to minting fresh step ids instead.
- 03466c3: Make the triage summarizer agent more aware of the implications of dry runs when making the github comment.
- 774b9f9: Added observability around browser actions.
- ed03d46: Run viewer now clarifies when a slow "Resolve element from cache" step is actually time spent retrying while waiting for the element to appear (up to the smart waiting timeout), rather than slow cache resolution.
- 6d92514: Show a clear, file-specific error when a test or module file contains invalid YAML, instead of an unexpected crash.
- c077d2f: Improve test run reliability when an AI action step's cached data is outdated

## 2.134.1

### Patch Changes

- 6be52b6: Explore notifications sent as private DMs now reach every author and co-author across the explored changes, not just the primary commit author.
- 41ae542: Fix a crash in the test editor when undoing or redoing after switching to a different test
- 2102778: Explore notifications now identify the author of the explored change via their GitHub account, so private DMs reach the right person even when their git email isn't linked.
- 8b2a6a8: Fix editor keyboard shortcuts (like delete) firing while typing into the page in the interactive editor
- d510ed9: Allow leaving a Type step's value blank in the editor to clear an input field
- b97e346: Explore notifications no longer report test builds that were blocked from producing a test; added an explore `blockedTestBuilds` setting to optionally include blocked builds with their blocker reason
- eda44bc: Explore notifications can now identify the author of the explored change so they can be delivered as a private Slack DM
- 08e2d50: Fix auto-heal direct-commit delivery so healed tests commit reliably in CI, including pull-request runs that check out a detached HEAD
- 75bb980: Improve test run performance by reducing unnecessary screenshot processing.
- bb59557: Explore agent Slack notifications now link the pull request and the originating commit, and show fuller test descriptions

## 2.134.0

### Minor Changes

- d175387: Add the `momentic ai explore` command, which discovers the user journeys changed by a git diff and can author Momentic tests to cover them

### Patch Changes

- a21a7ac: Fix a crash in the test editor that could close the editor during drag-and-drop interactions
- 47223c0: Improve browser screenshot diagnostic traces.

## 2.133.0

### Minor Changes

- 5a453cf: Send a Slack notification summarizing the tests built when the explore agent runs
- dc3ea1b: Add ability to drag and drop multiple steps at once in editor

### Patch Changes

- 9093a2f: Tune the github pr comment's severity to better match the failing tests.

## 2.132.1

### Patch Changes

- 17a0807: Show a clear, actionable error when renaming or creating a test with a name that already exists, instead of an unexpected internal error
- 68f764e: Resolve a moderate-severity security advisory in a third-party dependency
- 10b4ca9: Fix JavaScript step timeout max bounds
- eed8ae3: Make the github notification summary aware of the entire run state and not just limiting it to healed runs.
- 737c623: Make triage agent's github comment aware of what your classification config and healing config are set to as well as the intention of quarantining tests.
- 74aa15c: Show a clear, actionable message instead of an unexpected crash when sign-in credentials can't be saved due to file permissions

## 2.132.0

### Minor Changes

- ff3d671: Improve results classification accuracy and add the ability to search thru HTML snapshots, additional past runs, and failure recovery contents

### Patch Changes

- 50df05f: Improve web element cache hit rate on pages with repeated, visually-distinct elements (e.g. duplicate menus/popups) so cached steps resolve more reliably instead of falling back to AI
- cf587c7: Fix an issue where a single unresolvable module could prevent tests and modules from loading
- 7c66f08: Record the browser viewport in run attempt metadata.json so run artifacts capture the pixel dimensions the test rendered at.
- d1eb26a: Fix issue where empty folders would not show up when choosing folder to create or move a module

## 2.131.2

### Patch Changes

- 9dda778: Fix issue where panels would not persist layout through certain interactions

## 2.131.1

### Patch Changes

- b0e6014: Show a clear, file-specific error when a simplified-format test file is invalid, instead of a raw validation dump.
- db50551: When creating a module from selected steps in the editor, the folder picker now defaults to the folder of the test you're editing instead of the project root.

## 2.131.0

### Minor Changes

- 9b3494b: Add knowledge base access to failure recovery agent

### Patch Changes

- 5b47d81: Improved fallback models for the triage agents and fixed context overflow that could occur on fallback
- d1398fa: Fix duplicating a step in the editor producing a duplicate command ID that failed the duplicate-IDs check on v1-format projects
- b1e1aa2: Restore the editor warning that caches are not saved when editing tests on a protected branch
- a822d20: Make the PR notification made by triage aware of failures that crash the healing agents and tune its style of response.
- e6e55f7: Add the ability to move modules and tests between folders in the local editor. Moving a module or test now automatically rewrites every internal reference (relative module paths in tests and other modules) so relocating entities no longer breaks with "could not find module file" errors.

## 2.130.0

### Minor Changes

- c19585e: Automatically upload local results after `momentic ai triage`, use --no-upload to disable.

### Patch Changes

- cc1d1a1: Show clear messages for missing, moved, or conflicting module files instead of unexpected errors.
- 6354b9f: Add indexes to step list in the editor

## 2.129.2

### Patch Changes

- 24811c5: The run viewer now shows a "Failure recovery not eligible" callout in the step list when a failed step could not be recovered, with the short reason inline.
- a7495d3: Restore folder selection when creating modules in the editor
- 527bd09: Add keyboard shortcut to delete steps (backspace)
- c11075c: When running with --share-diagnostics, the CLI now reports remote-browser CDP round-trip latency and the runner's egress IP/region to help diagnose slow remote-browser runs.
- 83729f9: Fix shift to also respect j and k in the editor for selecting, shift j and k now mirrors shift down and up arrows.
- 4b899f8: Fix "Module is no longer on disk" error that could block saving right after creating a module from selected steps in the editor. New modules are now created alongside the test that uses them.

## 2.129.1

### Patch Changes

- ddcbb0f: Element checks with long timeouts now finish as soon as the element is found, instead of waiting out the entire timeout when the page has changed since the check started.
- 8f123ee: Add keybindings for adding steps after (o) and before (shift+o) selected step in editor

## 2.129.0

### Minor Changes

- c1a0c79: Roll out updated web test editor experience

### Patch Changes

- 3f2eeee: Improve reliability of automatic failure recovery: provider timeouts now fail over instead of aborting a run, and recovery degrades gracefully when an attempt is interrupted.

## 2.128.1

### Patch Changes

- e5dfffa: Fix the AI Action V3 "Clear cached steps" button hanging when clicked before the editor session finished loading
- 203057f: Unified the CLI's terminal output across `momentic run`, `ai explore`, `ai heal`, and `ai classify` with a shared banner, status glyphs, spinner, and live progress panes, compact tool-call summaries, and consistent result sections with muted explanations instead of raw `#`/`**` markup.
- 281789d: The `--share-diagnostics` flag can now be enabled by passing it on its own (e.g. `momentic run --share-diagnostics`), without an explicit value, and it no longer swallows a following test path.

## 2.128.0

### Minor Changes

- 0968da7: Enable direct commit and push functionality for the heal agent.
- 48d6880: Add knowledge base access to assertion agent
- e1f69e9: AI Action auto generates overridable post-conditions to improve reliability of browser state handoff to next step

### Patch Changes

- 0e36eee: Fix email helpers (fetchLatest, fetchAll, sendEmail) to correctly handle a full email address being passed instead of just the inbox name
- 2a7ec1e: Failures in post heal behaviors now tell you what failed.
- 4c792b1: Improvements for display of traces

## 2.127.1

### Patch Changes

- c25caf0: The `heal` command (alias `triage`) now reports the name of each test it could not fix alongside its ID, instead of printing the ID alone.
- c25caf0: The heal command now publishes its risk summary to GitHub pull request comments.

## 2.127.0

### Minor Changes

- c4bf7a5: Generate an AI risk summary for healed result archives and persist it during upload.

### Patch Changes

- 5d41efa: Fix a spurious validation error when an agent-authored module step sets a default value or enum for a parameter the module already declares.
- e619965: Fix AI Heal compatibility with remote browsers.
- a19d30d: Improve agent assertion usage to reduce unnecessary settings and brittle checks

## 2.126.0

### Minor Changes

- 8211d39: Add a new selectable locator version (v4.2) that improves element cache stability when locating elements inside large containers such as modals and dialogs, reducing unnecessary cache misses on repeat runs.
- 5b146a8: Move successful heals that fail on success behavior to their own status so users can know to look at their job that ran it to recover the patch.

### Patch Changes

- efaf78f: Improve element cache reliability by excluding very large text content from element-cache matching, so frequently-changing text in large containers (e.g. big modals) no longer causes unnecessary cache misses
- bbf1212: Fix `momentic app` incorrectly showing "No projects found" when launched with `-c` pointing at a config file outside the current directory
- e689555: Reduce the default worker count for `--parallel auto` with local browsers to half the available CPU cores (minimum 1) to avoid CPU saturation and timeouts.
- 0918705: Emit detailed diagnostic traces for the full result classification computation, including model inference time and per-tool calls, when running with --share-diagnostics.
- b251c6e: Ctrl+C now immediately cancels the CLI while it is checking your API key or resolving the project config.
- 1e1f250: Simplified YAML now lists the primary field first for each step (module path for module steps, goal for act steps).

## 2.125.0

### Minor Changes

- 720a3cb: Add Antigravity to the coding agents the onboarding wizard can wire Momentic into
- 34f77ec: Add `ai triage` as an alias of `ai heal`, plus a `--dry-run` flag on both that previews how failed tests would be grouped for healing and exits without making any changes.
- 71cb7ab: Name each failure bucket in `ai heal` / `ai triage` output with a short, human-readable label describing the shared issue, making bucketed results easier to scan.
- 7bebecc: Add a "quarantine" on-failed-heal option that quarantines tests auto-heal can't fix.
- ec7913f: Add a `--json` flag to `ai triage` that suppresses progress output and prints the result as machine-readable JSON, making it easy to pipe triage results into other tools.

### Patch Changes

- 2fed53f: After `init`, print accurate next steps (install editor skills, wire up the Momentic MCP, open the local editor, and docs) instead of pointing at the onboarding wizard, which does nothing once a project is already initialized
- 13b43bc: Failure classification and auto-heal are now configured only in the Momentic dashboard. The `ai.classification` and `ai.healing` keys in `momentic.config.yaml` are ignored.

## 2.124.0

### Minor Changes

- 09f404e: Recorded HTTP request/response data in run output is no longer cut off and shown as empty objects.

### Patch Changes

- 17af9a0: AI Action can now perform a wider range of actions when generating steps, including going forward, refreshing, waiting for a URL, checking elements and pages, copying and pasting, making network requests, reading and writing local storage, handling dialogs, and running JavaScript.
- aada171: Lint validation errors are now shown ESLint/Vale-style — `line:col  error  message  location` — with a codeframe (line numbers, `>` marker, and surrounding context) pointing at the exact line in your test/module YAML, matching the style of the run-failure trace. Unreadable Zod messages were replaced with actionable ones: invalid IDs, `coords`, and mobile percent values now say what's expected instead of dumping a raw regex or `Invalid input`. Affects `momentic lint`, `momentic checks duplicate-ids`, and the preflight checks before `run`/`app`.
- dc9673c: Use the source branch name as-is in auto-heal branch names instead of URL-encoding it
- 80684e4: Fix issue in editor where code editor inputs would resize incorrectly when resizing step list panel
- 2b7e8cf: AI Action can now work across multiple browser tabs while generating steps — opening new tabs, switching between open tabs, and closing tabs.
- 9eab96c: Improve result classification accuracy by giving the classifier additional application context.
- 24ce328: Show a clear, actionable message telling you to run install-browsers when a run fails because the required browser executables aren't installed, instead of a raw Playwright error.

## 2.123.0

### Minor Changes

- 39e7e80: Add `--parallel auto` to `momentic run` and `ai heal`. Workers are sized from the host's CPU count using the project-level `browser.remoteBrowser` flag: remote-browser projects scale to `cores * 4 - 2` (IO-bound), local-browser projects cap at `cores` (CPU-bound).
- 51e9b7e: Healing can now open its pull requests as drafts by selecting "Draft pull request" as the on-successful-heal behavior.
- 567eea4: Add `login` and `logout` commands to sign in with your Momentic account and save an API key

### Patch Changes

- 5443e94: Fix retries on browser connection failures.
- 4168b71: Treat non-recoverable heal-category failures as warnings instead of failing the run

## 2.122.0

### Minor Changes

- b1e98d6: Include citations to knowledge base entries in trace

### Patch Changes

- 5373cf5: Fix the exclude flag to match the run command's behavior for the heal command.
- b0dd0c5: Update dependencies to resolve a security vulnerability.
- ecab97f: Add the ability to heal a run group directly by passing its ID to `momentic ai heal --run-group-id <id>`, without needing a local results archive.
- 9e657df: Test runs no longer exit with a non-zero status when the only failures are classified as warn.

## 2.121.0

### Minor Changes

- e033a97: Speed up the healing and bucketing agents via a better parallel tool interface.

### Patch Changes

- 530e0bc: Fix AI Action v3 date serialization and running replays before committing
- 95946aa: AI Action v3 step caching is now reliably reapplied on subsequent runs.
- 2cf9721: Fix a bug where `--only-quarantined` stopped reporting exit code 1 for failures.

## 2.120.0

### Minor Changes

- 53bbf0a: Move heal and classification configs to the cloud. Cloud configurations of heal or classification will override local configurations.
- d209b5c: Add knowledge base access to locator agent

### Patch Changes

- ad2655a: Bias the healing subagent towards doing more exploration when stuck in a state different from its previous runs.
- 29237ac: Add `--share-diagnostics` flag (env `MOMENTIC_SHARE_DIAGNOSTICS`) to opt into sharing full CLI run telemetry. AI Action telemetry continues to be shared by default.
- 4b3dec4: Patch security vulnerabilities
- ce961b8: Improve auto-heal pull request titles and descriptions to follow your repository's `.github/PULL_REQUEST_TEMPLATE.md` when present.
- 86dba3c: Improve handling of oversized page snapshots so massive pages no longer blow the context window during failure recovery or multi-turn agent runs.
- ea0aab8: Improve remote browser reliability during CLI test retries.
- 5a4e16e: Improve target cache reliability so that caches are less likely to resolve to the wrong element.
- 4237e96: Fix duplicate test action so conditional step IDs are regenerated alongside other step IDs.
- f271cc3: Log the configured on-success mode (e.g. pull request, patch) before applying it to healed tests.

## 2.119.0

### Minor Changes

- 0657473: Use knowledge base context for result classification
- b5f8fea: Ungate public documentation and CLI commands for the simplified format migration

### Patch Changes

- 452a176: Show `[recovered]` next to each test in the live results when failure recovery successfully rescued the run.
- 42a4f17: AI Action v3 performance telemetry collection enabled.
- 692226a: AI Action UI bugfix
- 9451f61: AI Action v3 now works to fulfill the postcondition instead of just failing on it
- 07f8cb2: Failure recovery agent shows full trajectory (reasoning, tool calls, substep executions) in run viewer instead of just a flat substep list.

## 2.118.1

### Patch Changes

- 35da597: Fix repository name being mis-detected on some CircleCI configurations.

## 2.118.0

### Minor Changes

- b86973b: Add `--exclude` flag to `ai heal` to skip tests whose name matches the provided regex patterns.

### Patch Changes

- 4b24209: Improve element-cache invalidation during failure recovery to reduce wrong-element interactions
- 39d44ff: Fix repository metadata not being detected on some CircleCI configurations.
- 068d985: Javascript step on run viewer can now be viewed in larger window

## 2.117.1

### Patch Changes

- b9285d7: Improve test context in result classification.

## 2.117.0

### Minor Changes

- b0441da: Add `npx momentic ai classify --interactive` (`-i`) to keep the chat session open after classification for follow-up questions about the run.

### Patch Changes

- b2f7d66: Cancelled runs (from `--timeout-minutes`, `SIGINT`, `SIGTERM`, etc.) now print their run URL and cancellation reason in the final summary, alongside failed runs — so any cancelled run can be opened in the run viewer with one click.
- 76b9bbc: Allow for permanent recovery with failure classification v2 if one-time recovery fails.
- 8d4a8c9: Refine CLI test run output and performance warnings for clarity.
- 4b0f641: When sharding (`--shard-count` or `--shard-index` > 1), the post-run output now prints a `merge shards:` instruction instead of an `after upload:` run-group URL. The per-shard run group is replaced after the merge step in CI, so the original link was misleading.
- 4b0f641: Trace viewer now collapses consecutive "Smart waiting" rows into a single row with the summed duration and a `(N waits)` count, so repeated stability waits during a retry loop render as one combined row instead of many separate rows.

## 2.116.0

### Minor Changes

- 4a5da36: `momentic upgrade` and `momentic-mobile upgrade` now migrate existing projects to the v2 file format end to end. Each command installs the latest matching CLI release, flips the project file format to v2, refreshes the recommended agent configuration while preserving any pinned sub-versions, and rewrites every legacy test and module YAML through the v2 serializer. Files already in v2 are skipped, and a new `--dry-run` flag previews the migration without writing anything to disk. The narrower `momentic migrate v2-format` and `momentic-mobile migrate v2-format` commands are now publicly documented as the file-only path -- use them when you want to rewrite just the YAML files without any other config changes. The `lint`, `upgrade`, and `migrate` commands now have CLI-reference pages on the docs site for both `momentic` and `momentic-mobile`.
- 9080050: Scaffold new projects in the simplified v2 file format. `momentic init`, `momentic-mobile init`, and `@momentic/wizard` now create configs with `fileFormat: v2` and emit v2 sample tests. When the wizard finds an existing `momentic.config.yaml`, it stops and points you at `momentic upgrade` / `momentic-mobile upgrade` so the existing project can be brought to the latest format on its own.
- a5b50d2: Add CDP performance summary table when running with --verbose flag

### Patch Changes

- 58f8a5b: Fix duplicate lines in the test-runner output when remote browsers and video recording are both enabled. The "performance may be degraded" warning now prints once at the start of the run, before any test rows are drawn, instead of firing in the middle of the first test.
- 82c5112: Reduce noise in v2 YAML output by omitting optional fields that match their runtime default (e.g. `pressEnter: false` on `type`, `skipped: false` on any step).
- d1f0b11: Surface a clear permission-denied error when deleting a folder is blocked by the operating system (e.g. macOS system-protected folders), instead of failing with a generic crash.
- 8f1270b: Improve element-check locator reliability on cluttered pages so check steps are less likely to return the wrong element when several candidates share similar text.
- d241da5: Local run viewer now preserves sidebar and panel sizes when the window is resized.
- a8810a5: MCP prefers AI Action v3 for web/android when creating AI Action steps
- f6d5e31: Show a clearer, user-facing error when a `press`, `keyDown`, or `keyUp` step is given an invalid key name (e.g. `Esc` instead of `Escape`).
- 71de7b1: Emit detailed diagnostic traces for AI Action steps when running with --share-diagnostics.
- 9e34feb: Improve AI model provider routing reliability for failure-recovery, locator, and assertion steps. Run metadata now includes a schema version so future migrations can be applied automatically.
- 279785f: Fix issues with failure classification running twice in some cases

## 2.115.0

### Minor Changes

- 1585ed6: Add includeTrace flag to get_step_result tool
- 99c0e91: Updated category definitions for result classification including splitting "Test can be improved" into "Test authorship" and "Test setup", wrapping "Performance" into "Infrastructure", removing Related/Unrelated from "Application change" and "Bug", and adding an "Other" category
- b69bd56: `momentic import` now accepts folder paths (e.g. `momentic import auth/onboarding`) to pull every test and module inside a cloud folder. The cloud folder hierarchy is recreated on disk so tests land in matching local directories. Tests already on disk stay in their current location to avoid duplicates.

### Patch Changes

- 358fa75: Improve the skills guidance in choosing between AI actions and native steps.
- 1376f2e: Improvements to `--share-diagnostics`.
- ef6b742: AI Action V3 can now generate AI_EXTRACT steps to extract structured data from the page.
- e949573: Do not fail CLI runs when AI failure classification elects to heal the test

## 2.114.1

### Patch Changes

- ac04b6f: Improve web cache reliability by ignoring script and style content when comparing element text.
- 3d7c646: Raise the default JavaScript step timeout to 90 seconds (was 15 seconds) and allow configuring it up to 10 minutes.
- 1065b19: Fix resource-pressure hint appearing in the middle of the post-run failure summary.
- e13819e: Improve token efficiency and speed of failure recovery

## 2.114.0

### Minor Changes

- 0ec0404: New browser setting option to include bounding box coords for all elements

### Patch Changes

- 190776b: Fix MCP run step tool throwing after splice steps on unfrozen yaml files.
- 847f3f3: Improve AI Action v3 ability to handle dynamic content

## 2.113.1

### Patch Changes

- 97c4c6a: Fix long test titles overflowing and making attempt dropdown inaccessible
- 16a13bc: Make transient healing dependent on the "recoverable" output of failure classification
- e521688: Fix failure categorization sometimes getting partial results.
- 7c2f488: Update OpenTelemetry dependencies for compatibility with newer Sentry peer requirements

## 2.113.0

### Minor Changes

- d689c66: Add `momentic check lint` command for validating v2 project files, resolving local file references, and detecting entity ID conflicts.
- 25a0f2e: Show YAML code pointer in failure summary
- aebb86e: Add `--reporter` flag to `momentic run` and `momentic-mobile run`. Pass multiple times to combine reporters (e.g. `--reporter=list --reporter=junit`); file reporters write to `--reporter-dir`. Cloud run URLs are now clickable in supporting terminals, and end-of-run output is quieter overall.
- d689c66: Convert imported tests and modules to your project's v2 format automatically when running `momentic import` in v2 workspaces.

### Patch Changes

- 1b6ccf9: Identify authenticated CLI users to product analytics for better support and self-serve activation diagnostics.

## 2.112.0

### Minor Changes

- 959e589: Add a `momentic_test_get` MCP tool that returns a fully resolved test by id, including stable step ids and parent chains.
- e5e5f19: Move test-steps fetching out of `momentic_get_run`'s `includeTestSteps` flag into a dedicated `momentic_get_test_steps_for_run` tool. `momentic_get_run` no longer accepts `includeTestSteps`; consumers that need stepsSnapshots must call the new tool.

### Patch Changes

- 1d8a758: Do not fail the run when archiving artifacts is blocked by a transient file lock on Windows (OneDrive sync, antivirus).
- ec59187: Move the test output to respect your agents output to file or inline for mcp.
- eab626e: Enable the mcp to change clicks to force clicks.
- e1daa0c: `consoleLogger` now writes `.error` and `.warn` output to stderr while `.info`, `.success`, `.debug`, and other variants continue writing to stdout, so `momentic run > out.log 2> err.log` cleanly separates progress from errors. `--log-level error` now silences `.success`, `.dimmed`, `.bold`, `.underline`, and `.grey` decorative variants as users expect.
- e5e5f19: Performance improvements for result-classification
- 4f2eb35: Improve schema validation performance and error messages
- 0e5015a: `momentic run` and `momentic-mobile run` now print a two-line summary banner at the top (CLI version, Node version, project, test count, shard). Per-test status badges fall back to plain ASCII `[PASS]` / `[FAIL]` on terminals without truecolor + unicode + TTY, and completed status rows no longer carry the running-progress counter.

## 2.111.0

### Minor Changes

- ac6b7e3: Extend `momentic ai classify --save` to allow cloud runs' classifications to be persisted.

### Patch Changes

- c1e6c6f: `momentic app` and `momentic-mobile app` now show a clean startup banner with the local URL and version. Update-available notices are shown as a boxed message and skipped in CI / non-TTY shells. List commands (`momentic list`, `momentic-mobile list`, `momentic quarantine list`) are now safe to pipe — only test paths go to stdout. `momentic-mobile` now also checks for new releases on startup.
- f0ae1cd: Speed up the module recommend tool.
- 41bbc60: Fix run viewer video player flickering selected step back to its parent during gaps between substeps in a module or conditional.
- c3277a3: When AI failure classification is enabled in momentic.config.yaml, GitHub PR comments now lead with an AI-generated risk summary (clean run vs. likely regression) instead of just the test result tables. The detailed tables are preserved in a collapsed section.
- 8cd5e14: `ai classify` now stops cleanly on Ctrl-C.
- d698a36: Improve AI Action v3 healing by including completed step results and the final screenshot from the last successful run.
- b893bb2: Improvements to classification accuracy for in-flow AI failure categorization.
- 9dbc7e0: Fix unexpected error when a directory being written to doesn't already exist.
- 45e126e: Fix Pylon chat support widget not appearing in the local app sidebar
- 82fbd0a: Promote web AI Action V3 from alpha to beta
- 37d950b: Improve reliability of in-flight failure classification.
- 943797f: Fix zod4 external dependency issue

## 2.110.0

### Minor Changes

- a9355c9: Improve v2 failure recovery so the agent can decide when memory is poisoned and clear it surgically.

### Patch Changes

- 58bbf3a: Improve performance when opening, saving, or running tests in the local editor. Most noticeable on large workspaces.
- a9355c9: Improve failure recovery for failures that happen inside a module in a test's setup or teardown steps — the recovery now considers the surrounding setup/teardown steps as context instead of just the failed module's inner steps.
- 58bbf3a: Improve performance of the module details panel and folder browsing in the local editor. Most noticeable on large workspaces.

## 2.109.0

### Minor Changes

- f851010: Add visual assertion v4 configuration for improved screenshot-based assertion evaluation.
- e2dbb11: Allow disabling of cache for relevant step types through the CLI and MCP

### Patch Changes

- 75402b5: The local editor sidebar no longer fans out a request for every nested folder when the app first opens — sub-folders only fetch their contents when you actually expand them. Opening a test in the editor also stops issuing a separate full-project entity scan for the folder picker; it uses a glob-only `/api/entities/folders` lookup so the create-module dialog still surfaces every folder containing a test or module without parsing any YAML. Largest improvements on workspaces with deep folder trees or thousands of tests.
- 2a83857: Avoid CLI crash on startup when local diagnostics telemetry initialization fails

## 2.108.1

### Patch Changes

- 1fc0149: In some cases, cancelled runs would not show their current step results.
- 1c4e0b8: Add `--save` to `momentic ai classify` to persist the classification back into the local run archive, saving to cloud runs is not yet supported.
- d509349: Fix issue where resizing editor and run viewer stacked panels would trap element focus and prevent step keyboard navigation

## 2.108.0

### Minor Changes

- 6bdb3ef: Add get_step_result mcp tool and some updates to better reference steps within results
- 6bdb3ef: For result MCP tools that deal with run attempts, by default the first attempt is returned for failing runs and the last attempt is returned for passing runs

### Patch Changes

- 6bdb3ef: Return confidence level for result classification determination
- 0187563: Improve cache stability when interacting with elements whose look-alikes appear elsewhere on the page

## 2.107.1

### Patch Changes

- 063d5c3: Improve step search relevance.
- 11e7140: Fix "(intermediate value).env is not a function" crash on startup that could occur in some package manager layouts.

## 2.107.0

### Minor Changes

- 08a0f00: Add opt-in OpenTelemetry tracing for shared local CLI diagnostics.

### Patch Changes

- 9ce2e44: Local run viewer: left/right arrow keys now swap between before/after screenshots.
- d35564a: Slim down install size by removing unused dependencies.
- 61388c3: Redesign the run viewer header and details panel: the failure classification chip is now hover-only, the details panel defaults to closed, and browse vs. action buttons are visually separated.
- 068752d: Fix issue with relative position xy input labels causing values to be hidden
- f8a12dd: Only mark runs as recovered when the heal actually saved the run
- 52c56ce: Fix issue with jumping back to beginning of video when reaching second step
- 61388c3: Fix JavaScript step type declarations so that the email.create() API shows up in editor autocomplete and type checking.
- 61388c3: Stop the CLI from crashing with broken-pipe and Sentry errors when its output is piped into commands like head or aborted mid-stream.
- 2186f2d: Improve efficiency of git resolution for editor sessions, making the run button faster to begin executing steps.
- 61388c3: Make run viewer step rows keyboard-accessible: Tab moves focus through steps and Enter or Space selects a focused step.
- 85cf7c8: Fix issue with test editor inputs rejecting pasted text with new lines
- 61388c3: Tidy up run rows and tables: replace stacked badges with a single chip cluster for clearer status, classification, and label information.

## 2.106.0

### Minor Changes

- 8ccad2e: AI ACTION v3 trajectory shows screenshots

### Patch Changes

- 21092a5: Fix issue with run viewer panels overflowing for some tests
- c6caa20: Display further details about conditional step configuration in run viewer

## 2.105.0

### Minor Changes

- 04cd455: [beta] Result classification now runs before failure recovery, so you can configure recovery behavior per failure category.
- 3d2f9b3: Added `email.create()` for provisioning fresh ephemeral email inboxes from inside a test at runtime. The returned inbox auto-expires after 24h.
- 7560379: Update run viewer UI to be two panel layout
- decb6d7: Result classification responses now include a `recoverable` field.
- 55f156c: Added `sms.lease()` and `sms.release()` for checking a free number out of your org's pool for the duration of a test. See [SMS docs](https://docs.momentic.ai/integrations/sms#sms-lease-and-sms-release).
- 8c45334: Make the results path optional in `momentic results upload`, defaulting to the same `test-results` directory that `momentic run` writes to.

### Patch Changes

- 94f7d5c: Crash from EPIPE in retina-display detection no longer takes down the CLI when output is piped or aborted under npx.
- 4ce7421: Make fetching test metadata significantly faster.
- ca2f435: Fail more gracefully when a run has no attempts
- 9de4134: Hide the `--api-key` default value in `--help` output so the CLI no longer prints the API key from `~/.momentic/auth.json`.
- eba24ff: Step tooltips on the video player timeline and resource usage charts now show "JavaScript" instead of the raw code for JavaScript steps, and the timeline tooltips dismiss when you move off the step rather than staying pinned open while hovering the tooltip itself.
- 8420b06: Show the actions taken by failure recovery in the run viewer

## 2.104.3

### Patch Changes

- c9a69b0: Fix the self-hosted local results viewer (the static bundle shipped at
  `node_modules/momentic/run-viewer-static`) failing with "Unexpected
  Application Error! 404 Not Found" when opened directly via `index.html`.
  The viewer now once again shows the requested run whenever the URL
  includes a `?zipUrl=` query parameter.

## 2.104.2

### Patch Changes

- f9fb144: Run group timeline now anchors each run's bar at the run group's start time, so the "Waited for" segment is visible for CLI runs (which don't have a queuedAt). Wall time stat also stays accurate when the latest run finishes after the run group's recorded finishedAt.
- c358018: Improve reliability of usage telemetry.
- 78d1a4b: AI Action v3 TYPE steps now clear the target's existing text before typing by default, matching the documented schema behavior. Previously they were silently appending to whatever was already in the input. To preserve the old append-without-clearing behavior, pass `--clear-content NEVER` on the TYPE step.
- d50b82a: Clear the assertion's cache when failure recovery succeeds, so a recovered run no longer leaves a stale "false" memory trace that could cause future runs to incorrectly fail.
- b6f66b1: Address edge case caused by Chrome Dev Tools where some images would have no accessibility role, causing AI Assertion and locator inconsistencies
- 30e676e: Editor's run spinner now clears as soon as the step finishes, shaving ~300ms off every Run click.

## 2.104.1

### Patch Changes

- ebc273f: Reevaluate element location for case when selector changes after timeout

## 2.104.0

### Minor Changes

- c01cf0d: Summarize children for get_step_result MCP tool to reduce context bloat

### Patch Changes

- 36b44d0: Improve cache reliability for browser interactions with SVG elements

## 2.103.0

### Minor Changes

- d7f2135: Add a close tab test step to close a browser tab

## 2.102.0

### Minor Changes

- 9ca8aff: Show Agent Trajectory for AI ACTION v3 in Run Viewer

### Patch Changes

- 4c7b693: `momentic ai classify --output-format json` now prints only the final JSON to stdout so it can be piped directly into other tools. Errors that prevent classification are still printed.
- 2505fd1: Local results viewer (`cli results view` / `mobile-cli results view`) now
  renders per-attempt timeline segments for runs that retried. Previously the
  viewer showed a single bar per run regardless of how many attempts it took;
  now each attempt appears as its own colored segment with transparent gaps
  between attempts, matching the cloud run-group page.
- d1a22f0: Fix race condition in the local desktop app caused by duplicating a module shortly after editing it

## 2.101.3

### Patch Changes

- 5556ee3: Fix CLI sometimes hanging after a successful run.

## 2.101.2

### Patch Changes

- 4cf851c: Reduce CLI bundle size for faster installs.
- afc42a2: Show clear error when automatic parallelism is configured for web test runs
- 81c9920: Patch transitive `axios` dependency to 1.15.2 to address a critical Prototype Pollution vulnerability ([CVE-2026-42264](https://security.snyk.io/vuln/SNYK-JS-AXIOS-16417750)).
- 29aa90d: Add AI model minor version pinning in CLI

## 2.101.1

### Patch Changes

- 8b13b14: Hide trace on the run details page for parent AI action

## 2.101.0

### Minor Changes

- 12700cd: Removed the `ai.generate()` helper from JavaScript steps. Use a regular HTTP call to your preferred LLM API from inside the step instead.
- d40190d: AI action V3 (alpha) is now the recommended version. The version dropdown is labeled "V3 (alpha)" in both the web and mobile editors, with help text explaining when to use V3 vs V2. V2 is described as the previous-generation fallback.

### Patch Changes

- 72ce2d6: Fixed lag when opening "View details" on the tests table.

## 2.100.2

### Patch Changes

- c5b52d1: Add in-app support chat widget to the local app.
- 4f9519e: The setup wizard now adds the sample environment(s) the scaffolded test depends on, even when a `momentic.config.yaml` already exists, so the very first run no longer fails with a missing-environment error. Mobile projects also get a sample environment so it's clear how to configure variables. Failures during the sample test, the editor-skills install, and the CLI install now show the full underlying output instead of being truncated to the last few lines. CLI command help, log messages, and READMEs now refer to the "Momentic dashboard" instead of "Momentic Cloud".

## 2.100.1

### Patch Changes

- 2fc0994: Reduced redundant network requests from the local app frontend.
- 4859c54: Show a warning when momentic.config.yaml contains unrecognized keys
- a036c08: Speed up local app load times by caching filesystem operations
- c284376: Align init and upgrade configs with wizard defaults: add useMemory, failure recovery v2.0, and mobile upgrade command

## 2.100.0

### Minor Changes

- 29a7e5b: Upgrade failure recovery categorization agent to use the latest SOTA models

### Patch Changes

- 44011c1: Improve agent prompting for working with Momentic artifacts and their relative paths.
- dbc0f7c: Allow elements to be targeted upon retry even if they change identity.
- d9f320b: Fix occasional crash in long Copilot sessions and improve long-context performance of agents.
- fd1da59: Generated `momentic.config.yaml` files no longer set an unused default failure-recovery agent version.
- 839bd43: Upgrade the javascript editor with types and intellisense
- 1fb746c: Improve telemetry for test run completion events.

## 2.99.1

### Patch Changes

- 5351691: Display redacted env var values as "-" in the run viewer.
- 8e72dd4: Improve the reliability of result classification responses.

## 2.99.0

### Minor Changes

- f9e5aeb: Add run history tools to copilot for viewing previous test runs

### Patch Changes

- bf7acd8: AI actions now recover gracefully when the AI model returns without explicitly finishing the action.
- 15c6cb7: Fix edge case where test inputs fail to resolve, resulting in an orphaned browser instance.
- f4448f1: Patch transitive axios vulnerability (CVE-2026-42035, CVE-2026-42033).

## 2.98.0

### Minor Changes

- 99cdc29: Add global timezone configuration: defaultTimezone and useHostTimezone browser settings

### Patch Changes

- fb6bdf0: Upgrade internal dependencies to fix known security vulnerabilities.
- bf4cd1c: Copilot now rejects out-of-scope requests.
- cac4d74: Patch axios to 1.15.1 to fix critical HTTP Response Splitting and Prototype Pollution vulnerabilities.
- 559eb16: Cache git metadata fetches to improve app load performance.
- ee72ad5: MCP server now streams progress updates when `--daemon` is enabled, so long-running tools can report incremental status.

## 2.97.0

### Minor Changes

- f5ff932: Add a new `bannedAttributes` browser setting that excludes the listed HTML attributes from the context passed to AI agents and from cache element comparisons. This is the inverse of `importantAttributes` and is useful for stripping out dynamic attributes that would otherwise bust the cache. Attributes may be specified by exact name or with a trailing `*` to match a prefix (for example `data-dynamic-*`).
- 9392532: Add `failure-recovery: v2`. The new recovery flow can inspect browser state, execute steps, retry the failed step, and refresh stale step caches — surfacing the same per-step UI as AI action v3 with a "Failure recovery" label.

### Patch Changes

- dc5b130: When `--api-key` falls back to `~/.momentic/auth.json`, `--server` now also defaults to the server URL stored alongside that key, so signing in against a non-default server no longer silently sends that key to the production server.
- dc5b130: - `momentic init` now writes only `momentic.config.yaml`; sample module and test scaffolding moved into the `@momentic/wizard` onboarding flow so manual installs stay minimal.
  - `momentic install-skills` and `momentic-mobile install-skills` are now deprecated. They still work, but prefer `npx skills@latest add momentic-ai/skills` — it auto-detects `.claude/`, `.cursor/`, `.agents/`, `.opencode/`, `.github/copilot/` and lets skill updates ship independently of the CLI.
  - The CLI now falls back to `~/.momentic/auth.json` (written by `momentic-wizard login`) when `MOMENTIC_API_KEY` isn't set.

## 2.96.0

### Minor Changes

- 5ed5ab4: Increase maximum individual session duration for classification and AI action to 5 minutes.

### Patch Changes

- 65b77ff: Result classification command now retries automatically if the model returns without a result.

## 2.95.2

### Patch Changes

- 46b15f2: Fix error introduced in 2.95.1 that caused failure classification to never return a response
- d9faeae: Update result classification cli command model and add better error handling
- b0de5f2: Correctly cancel runs on SIGINT rather than exiting immediately

## 2.95.1

### Patch Changes

- 2c77f29: Improve reliability of AI agent streaming responses while preserving reasoning context where possible.
- f74776f: The `momentic_get_run`, `momentic_get_step_result`, and `momentic_list_runs` MCP tools now validate that the `runId` / `testId` inputs are well-formed UUIDs, giving a clear validation error up front instead of a downstream failure.

## 2.95.0

### Minor Changes

- eaa7edf: `momentic ai classify` now accepts a full run URL (e.g. https://app.momentic.ai/runs/<runId>) in addition to a run ID.

## 2.94.1

### Patch Changes

- 00e377a: Default `allowPartialAccessibilityTree` to `true` to prevent browser crashes and stalls on very large pages. Set it to `false` to restore the previous behavior on pages where AI targeting needs a more complete accessibility tree. Also keep run recordings streaming after a browser crash by restarting the screencast whenever Momentic reconnects to the browser.

## 2.94.0

### Minor Changes

- 6fcfc99: Default `aiPageFiltering` to `true` and deprecate the previous filtering engine.

### Patch Changes

- 6fcfc99: Add a buffer between page loads and any attempt to fetch an HTML snapshot from the page, which was causing some renderers to crash

## 2.93.2

### Patch Changes

- 4313b4f: Show AI Action version in run viewer
- a007398: Add a short wait between selecting all and clearing content

## 2.93.1

### Patch Changes

- cc4fcbd: Fix a bug where tests were not shown in the local app UI on Windows

## 2.93.0

### Minor Changes

- ce25160: MCP: Consolidate session and step schema retrieval into the session start tool. Updated the `momentic-test` skill to match.

### Patch Changes

- e6d1b37: Fix issue with execution not stopping after running "Run to" on a child
- 6259dbc: Update Run Viewer UI to have resizable panels, floating step info card
- fbe5a7d: Fix unreadable text in video player hover tooltip

## 2.92.0

### Minor Changes

- 2c0e5c3: Add `momentic ai classify` CLI command

### Patch Changes

- 7c7aa07: Improve globbing performance
- 7c7aa07: Exclude dependency directories from config yaml file search
- 99e77ec: Make the daemon not connect to daemons from other cli versions.

## 2.91.0

### Minor Changes

- e73369a: Add a --daemon flag to the MCP to enable a background daemon to maintain sessions across separate server invocations. Note: this is not available for windows yet.

## 2.90.0

### Minor Changes

- d73b126: Add `momentic_get_step_result` MCP tool

## 2.89.1

### Patch Changes

- b9e11f1: Fix issue with not showing some canceled runs as canceled

## 2.89.0

### Minor Changes

- 368c32f: Add `--video` for `momentic run` with support for `true`, `false`, and `on-fail`. `--record-video` remains supported as a deprecated alias that enables video (`true`).

### Patch Changes

- df3138a: Exclude more directories from globbing by default
- 640d70f: Duplicate-ids check now detects duplicates inside conditional blocks and else branches

## 2.88.2

### Patch Changes

- 370e885: Improve click step behavior for pages with large iframes

## 2.88.1

### Patch Changes

- 312aec5: Fix error in some AI model fallback paths that caused fatal message mismatches

## 2.88.0

### Minor Changes

- e393f31: Add relative position to hover steps.
- 4b30678: Support filtering runs by quarantined and recovered status in the list_runs MCP tool
- e393f31: Enable the MCP server to create and use steps with relative positions.

### Patch Changes

- 7cbb2b5: Improve auth check error messages with actionable guidance
- eaa328f: Preserve partial step results when test runs are cancelled by timeout

## 2.87.1

### Patch Changes

- ccba13b: Start the MCP server before running project validation in the mcp CLI command in order to improve startup performance.
- ef7f299: Conditional step status now reflects only the conditional itself, not its substeps.

## 2.87.0

### Minor Changes

- 1d986d8: Improve copilot speed and stream reliability

### Patch Changes

- 1d986d8: Improve reliability of AI response streaming.

## 2.86.0

### Minor Changes

- d3adba8: Add `simplifiedTestSteps` field to `momentic_get_run` responses and use it for better test intent inference in result classification.

### Patch Changes

- 66fdd71: Improve observability for mcp traces.
- 8c5a78b: Properly cancel in-progress runs on sigterm

## 2.85.0

### Minor Changes

- 0dc1e46: Make testId and gitBranchName optional in momentic_list_runs and add pagination support

### Patch Changes

- 296e1d7: Address security vulnerabilities
- 72733af: Update return data structure of momentic_get_run MCP tool to provide more fields

## 2.84.2

### Patch Changes

- aa38559: Ignore .momentic-mcp from globbing

## 2.84.1

### Patch Changes

- 7259435: Improve error collection
- 782c501: Fix git repo detection to work in repositories with no commits.
- 51908d6: Use exit code 1 for all test cancellations
- 2ce4ca3: Add Bitrise CI detection for automatic git metadata extraction

## 2.84.0

### Minor Changes

- baf8991: Add traces for AI extract step

### Patch Changes

- 8da3f1b: Improve the momentic-test skill's ability to use variables in Momentic.

## 2.83.4

### Patch Changes

- 0fd3520: Support pngs in run viewer

## 2.83.3

### Patch Changes

- 65a00b0: Support pngs in run viewer

## 2.83.2

### Patch Changes

- a392554: Display setup and teardown sections in run viewer
- b4fc065: Fix migration of graphql step variable inputs.

## 2.83.1

### Patch Changes

- 35ae277: Show element screenshots in the run viewer for all interactive steps
- 35ae277: Surface UI toggle for the "disableBrowserMonitoring" advanced setting in the test editor

## 2.83.0

### Minor Changes

- dd638cf: Add new momentic-result-classification skill

### Patch Changes

- dd638cf: Some fixes in the results MCP tools, including some extra data returned by the get-result tool
- dd638cf: Improve result-classification skill to use detailed step data

## 2.82.2

### Patch Changes

- 1b75fc3: Fix issue where scroll to failed step would sometimes scroll ancestor scroll container

## 2.82.1

### Patch Changes

- a1283ce: Fix merge command hanging

## 2.82.0

### Minor Changes

- 2811ad4: Add trace for auto-follow new tabs operation

## 2.81.1

### Patch Changes

- 953296d: Improve mcp trace observability.
- 373a6ee: Improve result and step serialization for conditional steps and modules.

## 2.81.0

### Minor Changes

- 6f1fc63: Add result processing tools to web MCP

### Patch Changes

- bc5fc8a: Improve mcp session logging.

## 2.80.0

### Minor Changes

- 07821c5: Change install-skills to do local installs instead of global.
- 66862b0: Changed the install-skills command to use --editor [your editor] instead of ide specific flags.

### Patch Changes

- 9afa048: Revert to old console log viewer
- 421353b: fix: skip iframe URL in recorded steps when autoExpandIframes is enabled
- 66862b0: Ship skill markdown as separate file assets under `skills/` for easier inspection.
- 5a4a5bc: Add tracing spans to MCP and emit span output as an artifact when sessions terminate.
- 4891204: Fix alignment of step indices on run viewer
- da622af: Reduce npm package size by removing unused files.

## 2.79.2

### Patch Changes

- 0d5c6c0: Add --video flag to MCP command for recording browser session videos

## 2.79.1

### Patch Changes

- edc3095: Print run links for cancelled runs if --timeout-minutes is hit
- bc06489: Fix issue dropdown options in module params dialog were not clickable
- 3de30d1: Improve the skill for how to handle edits and execution logic within sections (setup, main, teardown).

## 2.79.0

### Minor Changes

- 260b9e4: Add run URL and attempts fields to the buildkite reporter

## 2.78.0

### Minor Changes

- 36fcdce: Prevent playwright force clicking when we can't find an element to redirect to. Now enabled only through forceClickForMissingRedirectElement setting.

## 2.77.0

### Minor Changes

- 980356a: Added 'always' hybrid selector mode option and truncated hybrid selector logging in step output.

### Patch Changes

- f7cc3e2: Change default element check condition from "exists" to "is visible"
- c87cc4a: Fix failed step auto scroll bug

## 2.76.0

### Minor Changes

- 42d95af: Add ability to delete a test from the test details pane in the desktop app
- c7038d2: Add UI for ai action v3

## 2.75.1

### Patch Changes

- 4f3568b: Make copilot use cache keys better.
- 68d1185: Fix crash in local editor when deleting child step
- 7a00b75: Change the splice tool to return a recovery artifact to enable agents to undo bad splices accurately.
- 6a7caae: Improve the skill to improve the model's usage of cache keys to persist caches from previewed steps.

## 2.75.0

### Minor Changes

- 0a7c024: Improve UI for the console log viewer and add search functionality
- 9f341ea: Allow Chrome args to be removed using the MOMENTIC_CHROME_REMOVE_ARGS environment variable.
- 9f341ea: Improve detection of long-running scripts in the page and distinguish Momentic vs non-Momentic sources.

## 2.74.0

### Minor Changes

- 2c49514: Rename the get attributes tool to get artifacts and updated the momentic-test skill.

### Patch Changes

- 0515419: Update the skill to not push through errors when the session has clear errors.
- f6de50e: Improve the skill to prevent the model from over using javascript steps for actions native momentic steps already perform.
- e7fbb6e: Fixes for copilot including better logging and preview tool call structure
- 5fa34ba: Tune tool descriptions to encourage better agent behavior when editing.

## 2.73.0

### Minor Changes

- 893e28a: Removed the momentic_module_list tool from the mcp and moved its functionality to the get attributes tool.
- 893e28a: Renamed the momentic_attributes_list to momentic_get_attributes.

### Patch Changes

- 893e28a: Improved the error handling and description of the get attributes tool.
- 893e28a: Improved the momentic-test skill to better understand the get attributes tool.

## 2.72.1

### Patch Changes

- a272075: Fix default parameters not showing up on modules when changing step type

## 2.72.0

### Minor Changes

- b850fcf: Add support for REQUEST step body-type (json|form-urlencoded) in the mcp.

### Patch Changes

- 889afe5: Update run viewer details panel styles
- b850fcf: Fix mcp bug where invalid json for graphql request headers would fail silently.
- de63f5c: Improve response message to the model when cache entries fail to save inside the mcp's splice tool.
- e749e10: Sentence case step type names (AI check, Element check, Page check) across UI labels, error messages, and agent prompts

## 2.71.2

### Patch Changes

- 42fc41e: Fix support for conditional commands in the run viewer
- 4a7f565: Make relative element cache checks stricter
- 4a7f565: Fix a bug where some required elements were incorrectly failing relativity checks

## 2.71.1

### Patch Changes

- e69d482: Add query param for displaying detailed traces

## 2.71.0

### Minor Changes

- 90dbec5: Add --session-idle-timeout-minutes flag and MOMENTIC_SESSION_IDLE_TIMEOUT_MINUTES env var to configure MCP session idle timeout

### Patch Changes

- c22e44c: Split asset details into separate Channel and Tag sections
- 4d89166: Exclude failure_section tag from buildkite JSON report for non-failed tests
- 38ec4a1: Minor UI updates on run viewer step list
- 3ccb48d: Revert --port flag to use PORT env var instead of MOMENTIC_PORT
- 96e97fe: Prevent code snippets from shrinking in run viewer step content

## 2.70.0

### Minor Changes

- 12338df: Support running the local app on a custom port via --port flag or MOMENTIC_PORT env var

## 2.69.0

### Minor Changes

- 9c486cb: New buildkite-json reporter for run granularity reporter data for buildkite.

### Patch Changes

- 9c486cb: Fix junit reporter to properly identify whether a step failed in setup, main, or teardown.

## 2.68.3

### Patch Changes

- 1d46d33: Speed up code paths that fetch Git metadata for the current user and branch before the test editor opens

## 2.68.2

### Patch Changes

- a231894: Strengthen language in skill around never splicing un-validated steps

## 2.68.1

### Patch Changes

- c4f5ed9: Update run details panel to be detachable and error text easier to read
- f675781: Fix the bug where if a run step tool call took more than 5 min the session would be purged.

## 2.68.0

### Minor Changes

- 5b03448: Add the disable cache option flag on the mcp command to enable disabling caches by the mcp, with proper validation at the command level.

### Patch Changes

- 12e5b5f: Restore smart waiting retry logic for tab switching with at least 1 retry regardless of timeout

## 2.67.0

### Minor Changes

- 3f88169: Add the save cache option flag on the mcp command to enable force cache overwrites by the mcp.

### Patch Changes

- 4ffebd1: Fix issue where tests page scroll position reset when opening test details panel
- b27f822: Add wait for stability span and change previous wait for stability description to smart waiting
- b541fd6: Update resources tab on run viewer to have split charts for cpu/memory
- c91cc09: Adjust the cache saving for mcp servers to not overwrite caches on main when executing run step.

## 2.66.0

### Minor Changes

- 7dcbe42: Move the get browser state tool to get session state to be consistent with the mobile mcp. Adjust the skill to mirror the new unified behavior.
- 1803ae7: Add ignorePageLoadTimeouts browser setting to allow ignoring domcontentloaded timeouts

## 2.65.0

### Minor Changes

- 989b8ef: Remove the momentic_test_get tool in favor of just directly reading the test from the yaml

### Patch Changes

- 989b8ef: Remove environment default from agent step schema

## 2.64.1

### Patch Changes

- 99436cc: Fix bug where MCP could create nested modules through conditional steps.

## 2.64.0

### Minor Changes

- 2558c8e: Update MCP step schema time units to match the units that are stored on the resulting momentic steps. Previously, all units were in ms but units will now vary depending on the step configuration

## 2.63.0

### Minor Changes

- 2b8e2ee: Add --browser flag to the run command to allow selecting a browser that overrides test and config defaults
- db9d803: Make AI actions always-on. The `ai.aiAction` config option is no longer needed in `momentic.config.yaml`.

### Patch Changes

- f76d03d: Add browser setting forceClickForMissingRedirectElement
- 592fca6: Fixes for MCP including better schema examples for single quotes and missing envKey parameter on modules

## 2.62.0

### Minor Changes

- 4113175: Support element check condition in conditional step
- 4f8d041: Rename momentic_test_environment_list to momentic_attributes_list with structured output.

### Patch Changes

- ff84a5c: Lock down the behavior of the mcp create module tool to only be able to input valid entity names.
- ff84a5c: The MCP tool for creating a module now ignores both testPath and startIndex when one is omitted.
- ff84a5c: Add support for absolute paths to tests in the create module tools.

## 2.61.0

### Minor Changes

- 3454a30: CLI mcp command no longer allows a --yes flag, instead it uses the old default value (true) as the value.

### Patch Changes

- 13aa0b1: Momentic module list mcp tool now also respects the flag to output into chat or into a file (default). The module list tool also now removes unnecessary fields from the module output to make it easier for models to utilize.

## 2.60.0

### Minor Changes

- 3919ff5: Element checks return much faster when the element eventually appears (checks will attempt to reuse the cache on every attempt as opposed to only the first attempt)

## 2.59.0

### Minor Changes

- 5ad3706: Display web step traces in run viewer

### Patch Changes

- 8a78b7f: Add images to AI assertion and locator traces for run viewer

## 2.58.2

### Patch Changes

- 0fefab8: Filter folder listings in mobile CLI to only show mobile tests and modules (and vice versa for the desktop CLI)
- a6a81fc: Fix bug where errors in project configuration, duplicate id errors, or other crashes would crash the stdio mcp server

## 2.58.1

### Patch Changes

- 5a30cb3: Serialize class names for <i> elements by default, improving icon interactions

## 2.58.0

### Minor Changes

- 0f6d2c1: Add example data to the momentic init command

### Patch Changes

- 2984701: Fix bug where local app exits on non-critical errors

## 2.57.0

### Minor Changes

- bf11867: Replace module_update tool in copilot with additional options for splice_steps tool, along with prompting changes to clarify how to use the splice tool to edit modules for both MCP and Copilot.

- fd2812e: Avoid fetching the accessibility tree when resolving elements with a cache to improve execution performance and browser stability.

### Patch Changes

- fd2812e: Add browser option to disable the Chrome zygote process, which can reduce crashes in resource-limited environments

## 2.56.0

### Minor Changes

- c356206: Add support for the module creation tool in the MCP.

### Patch Changes

- c6fa1e9: Fix a bug where sigint was unhandled for desktop servers
- c2cf2cc: Update the momentic-test skill to be more hesitant about making unnecessary semantic changes like filling in unused fields on steps, changing quote types, etc.

## 2.55.0

### Minor Changes

- ca92267: Add support for isolating step caches by environment

## 2.54.2

### Patch Changes

- abed478: Minor UI fixes

## 2.54.1

### Patch Changes

- 1029c6b: Fix a bug where caches were incorrectly being saved after failed runs
- bd74012: Improve copilot's underlying model.

## 2.54.0

### Minor Changes

- 6c2fa73: Support conditional steps in MCP/copilot
- b1f7e8a: Change the install-skill tool to install-skills in the cli.

### Patch Changes

- b1f7e8a: Rename the momentic-agent skill to momentic-test.
- c40e39c: Always show run link input field when run group request fails in the local run viewer
- a816ca4: Update the momentic skill to utilize modules better.

## 2.53.1

### Patch Changes

- ff41a83: Add support for previewing modules to the MCP tool.
- fc300b4: Add OpenCode to skill installer command.

## 2.53.0

### Minor Changes

- a53f786: New install-skill command added to the cli.

### Patch Changes

- 40a5289: Preview tool now skips smart waiting to reduce latency during agent-driven test creation.
- 40a5289: Improve logging in create session tool response to prevent LLMs from mislabeling functioning sessions as errored out.
- 40a5289: Added screenshots to the tool response of the start session tool to prevent wasted get browser state calls.

## 2.52.0

### Minor Changes

- 8ad9dc9: Add momentic_get_initial_data MCP tool to get state of momentic project before calling other tools
- 8ad9dc9: Update input schema for MCP to be a cli-style string

### Patch Changes

- 8861888: Improve MCP splice tool responses so the model can understand test updates without needing an additional `get test` call.
- 0b9fdb3: Fix issue with video recording timestamp being off after switching tabs during high machine resource usage
- 39ac893: Fix issue with html parser failing on specific tags

## 2.51.1

### Patch Changes

- 054e94e: Fix issue where run viewer steps would not collapse if selected

## 2.51.0

### Minor Changes

- 26bb35f: Update run viewer to use new hierarchy structure for nested steps

### Patch Changes

- b7bec68: Pressing Escape closes the details panel when viewing a row (tests, suites, files, test plans, run groups).

## 2.50.2

### Patch Changes

- 49da689: Limit width of tooltips in video player

## 2.50.1

### Patch Changes

- 956aee0: Add local run viewer text to browser CLI run output.

## 2.50.0

### Minor Changes

- f587556: Edit test tool removed from MCP.

### Patch Changes

- 941b14a: Change defaults of the get browser state tool and added better text descriptions for how to use the tool.

## 2.49.2

### Patch Changes

- fc6f312: When the agent sends an incorrect config path to the MCP to create a session, catch the error and send it back.

## 2.49.1

### Patch Changes

- 7a07184: Consolidate step schemas in MCP tools to reduce context bloat

## 2.49.0

### Minor Changes

- bb3d060: Tighten the criteria for scenarios in which failure recovery can be triggered. Specifically, do not trigger on permanent user flow changes that require updating the test. In addition, reduce cases where failure recovery re-adds the step that will be re-attempted.

### Patch Changes

- 03d78db: Change orientation of label for run viewer step settings that include code blocks

## 2.48.3

### Patch Changes

- 8a1a981: Improved copilot tracking.
- 9983451: Fix overflow issue when resizing local run viewer

## 2.48.2

### Patch Changes

- 7cb2c54: Fix overflow issue when resizing local run viewer

## 2.48.1

### Patch Changes

- 5818d33: Update UI for failure recovery steps

## 2.48.0

### Minor Changes

- 3daba60: Adds support for custom browser settings when running the Momentic MCP server via the mcp command.

### Patch Changes

- 0a98032: Save cache info when running preview step with MCP/copilot so that future execution is cached
- b3099d1: Fix issues with run Viewer UI

## 2.47.0

### Minor Changes

- a1a17d4: Removed support for SSE transport for MCP to keep inline with standard.
- 3076456: Update Run Viewer UI to match mobile editor experience

### Patch Changes

- 46751da: Add a progress token for the run step tool to give updates for what is being currently executed in the test.
- a1a17d4: Clean up potential memory leaks from mcp sessions' browsers not being killed when server crashes.

## 2.46.5

### Patch Changes

- c6f0f27: Improve error handling in environments where git is not installed

## 2.46.4

### Patch Changes

- 344b092: Optimize MCP image return formatting so that images render correctly in more coding agents
- 344b092: Change MCP sessions to use headful browsers by default

## 2.46.3

### Patch Changes

- 1b597d1: Fix issue with dependency causing an error in some scenarios when copilot attempts tool calls.
- 8c15cbc: Fix stdio MCP server crash when running steps with reset session.

## 2.46.2

### Patch Changes

- 43c4fa9: Improve error reporting

## 2.46.1

### Patch Changes

- 33653fd: Trim fields from the momentic_test_list tool's test summaries to save tokens for mcp consumers.
- 1aaf3dc: Automatically scroll into view elements when visual actions is on and globalLocatorRedirect is off

## 2.46.0

### Minor Changes

- e38ab14: Added request listener, request recording, and mock route step types for agents.

### Patch Changes

- eb74162: Capture more exceptions for internal reporting
- 2f21e56: Add a new flag to the MCP run step tool to allow the model to re-run from a freshly reset session.

## 2.45.6

### Patch Changes

- b6f5964: Apply the same logic for validating element identity for newly AI-located elements as was applied for cached elements in 2.45.2
- a409a84: Add a CLI flag to the stdio MCP server command to override the default headful/headless from the environment variable.
- b6f5964: Fix bug that was preventing redirecting clicks from 1x1 inputs if the input had a long, auto-generated ID

## 2.45.5

### Patch Changes

- 918868b: Add a new parameter to MCP server initialization allowing the user to decide if they want the tool response to write to a file or get it inline.
- a008a69: Exclude head, header, and footer elements from PAGE_CHECK assertions

## 2.45.4

### Patch Changes

- 446e4b0: Change Copilot and MCP to be more screenshot reliant to decrease context bloat
- d70d307: Update tab switching timeout language to be more specific to the tab switching step and better represent the timeouts intended functionality
- 14a3bba: Fix the minimum width of the navigation bar in the local app

## 2.45.3

### Patch Changes

- 91c384b: Improve redirect logging and increase the timeout to find a label.

## 2.45.2

### Patch Changes

- 81f8526: Ungate the feature to detect element targets that change mid-interaction (part of the last minor release)

## 2.45.1

### Patch Changes

- 4d54e1e: Fix issue where toggling through test details panels would not update test name input value
- f6f3084: Fix issue where failed condition substeps would be ran when executing Run To command

## 2.45.0

### Minor Changes

- dbea1b0: Makes retries optional on test configs, enables fallback to momentic.config.yaml
- b1afdff: Improve interaction model to detect element targets that change mid-interaction and retry execution.

### Patch Changes

- b2d4aae: Agent tools now keep browser controls open by default, so Copilot can keep working after you cancel an action.
- cf06ba9: Fix stdio mcp to correctly use the passed in config.yaml

## 2.44.1

### Patch Changes

- e549d0a: When running a single step within a conditional or module, don't show the status of the step on the parent container.
- 720ea84: Don't run assertions on conditional steps if running a single step inside a conditional.

## 2.44.0

### Minor Changes

- b2d21c4: Allow redirectable elements to be selected even if they would otherwise be filtered out.

### Patch Changes

- 247ad9f: Fix a sharding bug where some shards included duplicate items
- 8444e96: Remove click redirection for invalid elements to target parent hitboxes.

## 2.43.0

### Minor Changes

- ad9fcf4: Show AI settings in run viewer

## 2.42.2

### Patch Changes

- 905727b: Change Copilot editing procedure to cause fewer unnecessary tool calls.
- 8ecb17f: AI checks now fire one last attempt at the end of the timeout rather than finishing at the timeout. Behavior unified with pre 2.33.1 momentic.

## 2.42.1

### Patch Changes

- ca1e82d: Make copilot's edits instantly fire an editor save to fix module edit vs autosave race condition.
- 5f5a62b: Removed the MCP flag that allowed edits to bypass disk persistence; edits now always follow the project-level persistence setting.

## 2.42.0

### Minor Changes

- 12ffbd8: Copilot now uses step caches if available when executing test steps

### Patch Changes

- 0f05e51: Removed step linting.
- 9ed4176: Fix module edit tool not saving modules edits when using Copilot.

## 2.41.0

### Minor Changes

- 32beeea: Show quarantined badge on run with --only-quarantined

## 2.40.0

### Minor Changes

- 1f7e786: Adds quarantined_at to CLI and Mobile CLI report outputs

## 2.39.2

### Patch Changes

- 6852592: Fix bug where browser would sometimes scroll when not necessary.

## 2.39.1

### Patch Changes

- 55575cb: Fix bug where duplicating conditional steps doesn't create new command Ids for sub steps.

## 2.39.0

### Minor Changes

- 32c1eff: New MCP commands for starting and terminating browser sessions. MCP managed browser sessions can be headful & auto terminate if not interacted with for 5 min.
- 32c1eff: New MCP tool to view the start of a given browser session. This includes a browser snapshot and image. Warning: this is often token heavy.
- 603c177: New MCP tool for previewing step inputs on a test browser session.
- 32c1eff: MCP stdio support under mcp command. EX: npx momentic mcp.
- a2f8bcd: Record system and process memory and cpu resource data during text execution and display in Run Viewer
- 603c177: New MCP tool for retrieving environment variables from a browser test session.
- 603c177: New MCP function to run step ranges on a test browser session.
- 603c177: New MCP tool for editing the session in use via splicing steps into the test.

### Patch Changes

- 668918b: Convert MCP responses to using multiple content parts in responses.

## 2.38.2

### Patch Changes

- 7232de7: Fix copilot bug where it was throwing errors when editing tool-calls.
- 43b0ba0: Fix a bug where element checks on attributes that do not exist pass

## 2.38.1

### Patch Changes

- 08f45e6: Unify copilot preview step tools.
- 9ad2177: Copilot only uses splice to edit the test.
- 94cb48e: Bug fix for retries flag in CLI. Now the Cli flag overrides the test.retries which overrides the config.retries.

## 2.38.0

### Minor Changes

- 42e6e61: List runs on landing page for local run viewer and make runId optional in results view command

### Patch Changes

- 296bc95: Improve enforcement of relative elements in caches

## 2.37.2

### Patch Changes

- 8db77a1: Copilot reset session reloads environment variables.

## 2.37.1

### Patch Changes

- 7fc78d8: Fix playwright dependency installation on windows

## 2.37.0

### Minor Changes

- 244330c: Add results view command to launch local run viewer and view local results

### Patch Changes

- 48fecad: Hide incorrect credit estimate from the test details pane
- eca74d8: Step selection now defaults to alphabetical order.
- 48fecad: Sort modules alphabetically when creating a new step
- 48fecad: Fix an issue where cleanup would fail after creating test results archives.

## 2.36.0

### Minor Changes

- 94abe57: Conditional steps now support page checks as the condition to if else with.

### Patch Changes

- d6bb10c: Fix a11y tree serialization for em elements, which was causing AI locate calls to pick text elements and throw a DOM error in rare instances
- 6d0bf80: Automate windows dependencies during momentic install-browsers

## 2.35.1

### Patch Changes

- 4520016: Patch minor security vulnerability with diff-lines
- 976ff82: Adjust accessibility tree serialization for elements with the same "name" and text content, removing the "name" but preserving the child text content

## 2.35.0

### Minor Changes

- 51a3b3a: Be able to view tests that are using a module when viewing a module in the app

### Patch Changes

- 9e40a82: Improve handling of ambiguous global locator redirect cases

## 2.34.0

### Minor Changes

- 47b8d73: Prompt tuning for how to handle single quotes around textual arguments when locating elements.

### Patch Changes

- 08de2ea: Copilot and MCP now have access to the waitForDownload, downloadTimeoutMs, and delayMs settings on click steps.

## 2.33.3

### Patch Changes

- 7fb96b9: Locator rules for ineligible elements adjusted.

## 2.33.2

### Patch Changes

- 50b81cd: Conditional steps now allow javascript conditionals with a truthy return evaluated as true.

## 2.33.1

### Patch Changes

- bba2c7b: Fix a bug where caches were being saved incorrectly for failing test runs

## 2.33.0

### Minor Changes

- abf8fbd: Add support for overriding git metadata using environment variables

## 2.32.0

### Minor Changes

- 9766cdf: Prompt tuning for more stable model responses.

## 2.31.1

### Patch Changes

- a85b860: Fix cache saving for the assertions inside conditionals

## 2.31.0

### Minor Changes

- 5e032c0: Tune Locator to respect multiple single quote strict queries in one request.

### Patch Changes

- 712604f: Fix async promise rejection error when node highlights fail

## 2.30.2

### Patch Changes

- 77807f9: Fixed intermittent cache misses in cached modules using the “Treat as auth module” setting with redirecting login pages.

## 2.30.1

### Patch Changes

- 7f73bce: Fix cache resolution bug when running tests outside of CI on main

## 2.30.0

### Minor Changes

- 1e74ae7: Locator model improvement and prompt tuning.

## 2.29.6

### Patch Changes

- 3a23aa4: Support session storage when loading and saving auth state

## 2.29.5

### Patch Changes

- 24048a0: Prevent modules from being added to other modules in the "all" tab of adding a new step

## 2.29.4

### Patch Changes

- 388067e: Improve cache v3 requirement generation

## 2.29.3

### Patch Changes

- dcdbae8: Fix a bug that caused certain caches to bust unnecessarily inside iframes
- 9104af2: Default creation of new tests to 1 retry
- d1edaa0: Added undo redo for the editor on local app, copilot actions are included in the undoable actions.
- 9104af2: Fix bug where defaults with "-" in them were not interpolated correctly in the momentic.config.yaml

## 2.29.2

### Patch Changes

- f088b16: Prevent launching app when an invalid test schema is detected, and show which files as well as steps must be fixed.

## 2.29.1

### Patch Changes

- 7e2d3f8: Revert numerical inputs to allow invalid entries until blur / enter.
- ba87e1d: Add ability to edit name and description of tests from Repository view

## 2.29.0

### Minor Changes

- 8b8c2be: Add setting to only grant specific permissions to sites

## 2.28.10

### Patch Changes

- bc1bfe9: Add momentic.config browser setting defaultBrowserType to specify org default browser to use in tests

## 2.28.9

### Patch Changes

- c059bbd: Fix request step schema parsing errors

## 2.28.8

### Patch Changes

- a33a3b1: Update momentic.config file to allow specifying repository root to display in UI

## 2.28.7

### Patch Changes

- 9fdae76: Fix issue with handling numerical values in DOM processing

## 2.28.6

### Patch Changes

- ea9db74: AI Action evaluate agent prompt tuning.

## 2.28.5

### Patch Changes

- 5cf5758: Fix request recording step picking up requests that started before recording

## 2.28.4

### Patch Changes

- 8ce9747: Model improvement for AI Actions.

## 2.28.3

### Patch Changes

- 19de55d: Fix issue where editing conditional step assertion was removing child steps

## 2.28.2

### Patch Changes

- 4c7094b: Copilot and MCP more prone to search for modules when making tests.
- e30ad26: Copilot and MCP are now significantly better at understanding visual descriptions when editing tests.
- 16eea66: MCP now returns a structured response after a test-editing session, indicating whether it accomplished its goal and whether it is safe to continue.
- a690374: Drastically improve Allure reporting with module name support, before/after screenshots, context, api request data, and video attachments
- 4c7094b: Copilot and MCP now adhere more strongly to the edit protocol.

## 2.28.1

### Patch Changes

- d80023c: Normalize headers in request command

## 2.28.0

### Minor Changes

- 1d05bfc: Upgrade models for AI action and failure recovery

## 2.27.2

### Patch Changes

- 889f0ba: Fix issues with adding conditional steps to modules
- 03b67be: Module tools can now create subdirectories from the copilot. Metadata-only changes to modules are now supported via copilot.
- 15bcd22: The test editing MCP tool now advertises how it can edit modules.
- f0b8c4e: Highlight the from and to target during drag and drop steps

## 2.27.1

### Patch Changes

- a52493d: Update navigation section header link styles to appear clickable

## 2.27.0

### Minor Changes

- 2e1b0d0: Add more granular settings to opt out of console and network logs

### Patch Changes

- c146c24: Improve test search performance

## 2.26.0

### Minor Changes

- 6983b6e: Add support for form-urlencoded API request bodies

### Patch Changes

- e801f0d: Fix a bug in the REQUEST step where content type was not set according to the body type chosen
- 0d56868: Added GraphQL step support to Agents (Copilot & MCP).
- 85b109a: Agents evaluate whether they can run the step after their changes to ensure they don't break you test.
- d4b4c70: Make git repository metadata more consistent when running on CircleCI
- 06c656c: Copilot tuned to better understand how tools are failing from their responses.
- 7eb152a: MCP linting step is now less strict when rejecting improper usage.
- 847ae7d: Also serialize elements with background images and no children as images in the accessibility tree
- 1ad35ae: Enable Agents to save API step results to EnvKeys.

## 2.25.8

### Patch Changes

- 7f7d6d3: Fixed Node 25 incompatibility.

## 2.25.7

### Patch Changes

- 4431744: Fixed tracing error log.

## 2.25.6

### Patch Changes

- 946822c: Add more checks to make sure that selectors still resolve to the same element after cache resolution

## 2.25.5

### Patch Changes

- dce3a05: Improve tracking for Agents.

## 2.25.4

### Patch Changes

- 6cc766e: Fix a bug where request and/or response content was being redacted from recorded requests
- 6cc766e: Fix a bug where requests bodies were not being passed to mocks

## 2.25.3

### Patch Changes

- 30c1182: Add 'disableFullStory' flag so that users can selectively enable fullstory blocking

## 2.25.2

### Patch Changes

- 65aec9f: Block self-hosted FullStory scripts to prevent performance degradation in test environments
- 5c37b7c: MCP test_edit tool has better guidelines on how to interpret the response messages array.

## 2.25.1

### Patch Changes

- 7116222: Copilot and MCP are now less likely to ignore failures in steps.
- dd2af11: Copilot sticks to its edit protocol better and adds steps more frequently instead of splicing large sets.

## 2.25.0

### Minor Changes

- 25e6091: Drag and drop step added to AI actions, failure recovery, auto-healing, and test generation.

### Patch Changes

- dcf8df2: Fix issues with step actions including adding modules before/after modules and adding children to AI Action steps
- f8294ce: MCP edit test tool now returns diffs as additions and deletions instead of the full test.

## 2.24.1

### Patch Changes

- 2caba7c: Update visual assertion primary model for the V3 agent
- 547a02c: Remove the diff from disk dialog.

## 2.24.0

### Minor Changes

- 629fea6: Add a flag to incrementally evict old caches
- c7000f2: Locator v3 improved to be more accurate and nitpick less.

## 2.23.4

### Patch Changes

- c878f84: Always serialize labels in the web a11y tree
- c878f84: Serialize parents of momentic-ineligible elements to provide more context

## 2.23.3

### Patch Changes

- d636332: Record reason why caches did not resolve
- d636332: Support resolving caches with a single selector

## 2.23.2

### Patch Changes

- 4c63a68: Stream HAR entries to disk during test runs to avoid excessive memory usage

## 2.23.1

### Patch Changes

- c0e487f: Fix a bug where caches were being discarded despite being usable

## 2.23.0

### Minor Changes

- 55249d2: Add conditional step type

## 2.22.5

### Patch Changes

- 00b1be0: Fix vulnerable dependencies
- 90805ba: MCP sends back notifications for tools and reasoning.

## 2.22.4

### Patch Changes

- 152c0b4: Add AI smart waiting when cache cannot be used
- cbc6461: Add an extra layer of validation to ensure that the page doesn't change after caches are resolved
- ad093ce: Copilot receives cache information when it uses the test get tool.

## 2.22.3

### Patch Changes

- c725b84: Each element check attempt now uses a copy of the original step cache instead of inheriting the cache from the last attempt
- d0148c5: Fix a bug causing mouse drag to not work on pages with certain cursor event handlers
- 202374b: Search bar for variables in the Context tab of the editor.

## 2.22.2

### Patch Changes

- ad81bed: Fix issue where memory would not be saved if the overall test status is failed
- a07d939: Copilot test_get tool no longer truncates steps.
- ad81bed: Fix cache saving issue where memory from element checks that have any failed attempts would not be saved

## 2.22.1

### Patch Changes

- 61aaa3d: Use System.PullRequest.SourceBranch to infer branch for Azure devops workflows triggered by PRs
- 6505a99: Copilot reset session properly resets environment variables.
- 61aaa3d: Grant local-network-access permission to browsers during CLI runs
- 527caea: Only check CLI version for commands that don't require specific output

## 2.22.0

### Minor Changes

- d3f4d0f: Upgrade to latest playwright

### Patch Changes

- 9ac963d: Upgrade dependencies to address security vulnerabilities

## 2.21.4

### Patch Changes

- 99f3794: Add a visual indicator when caches aren't being saved in the editor
- fbfac02: Diff from disk pop up now cancels execution upon selecting a choice.

## 2.21.3

### Patch Changes

- 397cebd: More verbose logging for momentic upgrade command

## 2.21.2

### Patch Changes

- d65ea00: Add the ability to use a proxy server when running tests. Proxies can be configured at the test and environment level.

## 2.21.1

### Patch Changes

- 5c848d1: Pin AI SDK version to prevent message-mismatch errors in the copilot UI.

## 2.21.0

### Minor Changes

- ca32829: Add a --regenerate-caches flag to rebuild caches from scratch
- 7d30562: Add the ability to upload videos of test runs
- 80f40ad: Update default settings for AI agents to use the latest models
- 80f40ad: momentic upgrade command to update existing configurations to the latest defaults

### Patch Changes

- bfed3bb: Agents now have access to Copy, GoForward, LocalStorage, MouseDrag, Paste, Refresh, and APIRequest steps.
- aeaaddb: Agents no longer remove and replace tools. They are now given better context for the test and steps indices and prioritize accurate splicing.
- 7eee99f: MCP edit test tool has full description of the subagent it fires off.

## 2.20.4

### Patch Changes

- e191cba: Fixed race case in the desktop editor for disk diff alert when manually hitting the save button.
- b55b738: Agents less likely to use javascript steps to avoid unsupported step types
- d1546f1: Added drag and drop step to agents.
- 7cf94ce: Support different tolerances in web caches

## 2.20.3

### Patch Changes

- 86d48a2: Fix a bug where we were calling functions only supported on HTMLElements on non-HTMLElements

## 2.20.2

### Patch Changes

- bfd938e: Improve accuracy of collecting resource usage data on Mac OS

## 2.20.1

### Patch Changes

- e6acbe2: Improve context management for agents and prevent unresponsive copilot UI crash.

## 2.20.0

### Minor Changes

- e02a69b: Add quarantine list command

### Patch Changes

- cc97caf: Agents kindly reject working with step types they cannot use.
- b7f9758: Improve error messages when merging results fails due to validation errors

## 2.19.3

### Patch Changes

- 4863fce: Opt out of FullStory scripts during test runs

## 2.19.2

### Patch Changes

- 4f22c07: Consider data-index as an important attribute by default for hybrid selector resolution.
- ab0d09b: Reduce log volume for critical resource usage

## 2.19.1

### Patch Changes

- eee297e: Fix global locator redirect bug where coordinates could be returned far away from the original element.

## 2.19.0

**Warning**: Please avoid this version and upgrade to 2.19.1 instead.

### Minor Changes

- 7db4ca2: Add new 'always' setting for global locator redirect

### Patch Changes

- 7db4ca2: Try to click a visible point on the element when stability checks are disabled

## 2.18.3

### Patch Changes

- 3b72364: Disable service workers by default to reduce flakiness when intercepting requests and to combat an instance where Playwright can hang indefinitely on sites using service workers: https://github.com/microsoft/playwright/issues/37347.
- ec6b3e0: Type steps can now use relative position.
- 71c4ec4: Visual improvements to the network viewer in the editor
- 71c4ec4: Visual improvements to the accessibility tree and HTML viewers in the editor

## 2.18.2

### Patch Changes

- 57ea719: Improve performance of AI locator on pages over 900K tokens large

## 2.18.1

### Patch Changes

- 48ff698: Agents now self prune messages, are protected from max hitting max context window, have access to more command types, recieved significant performance tuning, and no longer silently fail.

## 2.18.0

### Minor Changes

- 36b5816: Add support for initializing local storage on browser setup

### Patch Changes

- ff5fe3f: Bug fix for an issue where the editor could incorrectly show the “state differs from disk” pop up after using the step recorder.

## 2.17.19

### Patch Changes

- c2ca54f: Avoid enabling the Chrome crash reporter if the home directory is not accessible

## 2.17.18

### Patch Changes

- aeb2376: Agents respect setup and teardown as sections and will edit them on direction
- 499e764: Desktop editor now has a pop up to prevent automatic overwriting if a tests disk state changes.
- 1ace51f: Module edit tool updates the editor state to match the new module.

## 2.17.17

### Patch Changes

- b89cf21: Copilot module changes in editor render in desktop editor.
- 17d40ee: Fix bundling issue that may cause the AI SDK to crash on start

## 2.17.16

### Patch Changes

- 77f2d34: Agents understand modules better, can edit/create parameters, and consistently input the correct type for javascript inputs.
- 3e490ad: Agents now prune browser snapshot leading to longer chats and more accurate computer use.
- 40dc4e9: Agents now aware of the difference between BROWSER and NODE in javascript steps.

## 2.17.15

### Patch Changes

- 885fb80: Desktop editor state revalidated on when opening test editor.

## 2.17.14

### Patch Changes

- ef12e2e: Agents have access to new module look up tool and have hard constraints on input parameters for modules.
- 61c28fa: Agents can now create and preview AI action steps.

## 2.17.13

### Patch Changes

- 44c1b76: Allow global locator redirect to choose zero opacity elements

## 2.17.12

### Patch Changes

- e9b3019: Copilot returns to user when unable to figure out how to proceed instead of overwriting steps to bypass failure.
- 255a565: MCP blocked from editing a test with multiple sessions.

## 2.17.11

### Patch Changes

- 7310e70: Fix a bug preventing caches from being updated after element checks
- 34ea56c: Set default value for global locator redirect setting to true

## 2.17.10

### Patch Changes

- 628e66b: Send browser crash dumps to Momentic
- 770e27a: Fixed copilot bug where it is able to edit other tests.
- a0a176b: Added a linter to block poor instructions for the MCP's test edit tool.

## 2.17.9

### Patch Changes

- 7ca8d7f: Fix nav item styling
- 39d5ad7: Improve retries for errors caused by page state changing
- b1b2c92: Display toast when attempting to reset the browser with unsaved changes.
- 40c9817: Fix a bug causing certain browser-level errors to not be retried correctly
- 28b3921: Attempt to send logs on node crashes
- 28b3921: Prevent test recording from generating steps with single quotes in them
- ea4a258: Agents' given better guardrails and smarter tools (MCP & Copilot).

## 2.17.8

### Patch Changes

- 6656832: Allow much larger results arrays to be uploaded and processed

## 2.17.7

### Patch Changes

- c5313ed: Reset the command ID when changing an assertion description to bust memory.
- 05c6071: Agents (Copilot & MCP) now respect test functionality and don't edit after failing steps.
- 3bd871e: Always include i tags in the serialized a11y tree

## 2.17.6

### Patch Changes

- 9a2e745: Copilot updated to use newer frontier model.
- ce65799: Fix edge case where negated visibility element checks can use caches from failing attempts
- fdccc42: Provide AI with more positioning information for elements with absolute, sticky or fixed positions

## 2.17.5

### Patch Changes

- f9c4d4c: Copilot and MCP agents now support javascript steps.
- de4f292: Failure recovery fixed to see the most recent error rather than just the first.

## 2.17.4

### Patch Changes

- 9e593d1: MCP & Copilot can now insert module steps into tests.
- 04d2088: MCP and Copilot Agents are now fully capable of module manipulation and editing.

## 2.17.3

### Patch Changes

- 0f5ba29: AI extract for the V2 AI agents now accept non-object JSON schemas.
- 396310e: The Copilot agent (editor and MCP) can now create modules from tests.
- 722ef30: Fixed bug causing failure recovery to proceed even if the retried step failed
- 0f5ba29: Do not fallback to cloud AI agent configurations if local ones are not provided.

## 2.17.2

### Patch Changes

- e3ad980: Support merging caches back into main using the Gitlab API

## 2.17.1

### Patch Changes

- b43a4ec: Merge caches back into main when a branch is merged on github
- 29b484f: Allow failure recovery to execute in before and after steps.
- 76e70c8: Redact certain content types entirely in the network viewer

## 2.17.0

### Minor Changes

- ceeba05: Allow important CSS class names, styles, and HTML attributes to be configured in the local CLI, enabling customization of available context for AI agents

### Patch Changes

- c247d2d: Label responses that have been mocked in the network viewer
- c247d2d: Truncate oversized content in network requests rather than fully removing it
- e15a143: Return a 500 server error if mocking code fails to evaluate rather than just hanging
- 3737163: Fix a bug in JSON serialization of GraphQL variables
- c247d2d: Make env truncation in the run viewer more lenient so that we don't loose keys
- ceeba05: Apply fix for case where Chrome Dev Tools Protocol omits intermediate <span> elements from the accessibility tree

## 2.16.0

### Minor Changes

- 4f96c58: Added support for mocking network requests
- 028e793: Configuration option to disable html snapshots in results
- 2c51e4a: Add support for other url matching methods and http method matching to 'record request', 'request listener', 'add header', and 'mock route' steps

## 2.15.2

### Patch Changes

- ade6220: Fix cases where tests can continue running even if failure recovery does not succeed

## 2.15.1

### Patch Changes

- 8c81fd0: Show failed failure recovery attempts in the run viewer, as well as reasoning for when failure recovery is not eligible.

## 2.15.0

### Minor Changes

- aa78586: Add support for an ignoreHttpsErrors boolean in the config.
- af31c5a: Fix JSON circular dependency error thrown if a failed step throws a non-serializable error (e.g. `AxiosError`).

### Patch Changes

- 9f1159f: Filter out non-applicable test types from local apps

## 2.14.4

### Patch Changes

**Warning**: Please avoid this version and upgrade to 2.15.0 instead.

- 2844c51: Send proper run attributes for logs emitted during CLI runs

## 2.14.3

### Patch Changes

**Warning**: Please avoid this version and upgrade to 2.15.0 instead.

- de4b76b: Improvements to folder handling
- 7e5e667: Change Momentic remote logger provider
- 4a239d2: Fix edge case where AI page filtering was not being triggered for assertions.

## 2.14.2

### Patch Changes

- 24380bb: Fixed network request recording bug which caused all requests's start times to be set to epoch
- b398d6f: Escape unicode characters in cache headers
- 24380bb: Network viewer visual improvements

## 2.14.1

### Patch Changes

- e19b1a1: Fix edge case where aria-hidden elements are not serialized because CDP constructs invalid IDs for them
- 73ef386: Enable caching for negated element checks
- e024835: Reduce log volume sent from the Momentic CLI to avoid network congestion issues

## 2.14.0

### Minor Changes

- 76ea5e9: Add junit label if the main body of the test failed
- c03f3a6: Memory now supports negated element checks and failing assertion and locator calls.
- ec9dfda: Negated element checks (i.e. X does not exist) now use the assertion agent rather than the locator agent.

## 2.13.1

### Patch Changes

- e00d997: Fix a11y tree pruning bug

## 2.13.0

### Minor Changes

- 063e7e5: Update setup and teardown behavior to always fail tests when any step fails
- 063e7e5: Add setup_failed and teardown_failed fields to junit reports

### Patch Changes

- c782d52: Discard ineligible candidates earlier in click redirection
- c42c174: Fix a11y tree pruning logic to remove all nodes with invalid bounding boxes
- 73042c6: Fix saving for module retries

## 2.12.1

### Patch Changes

- e2628e6: Fix API key validation for AI proxy

## 2.12.0

### Minor Changes

- 8120ff2: Copilot in the editor
- 8120ff2: Drop support for Node.js 18 https://nodejs.org/en/blog/announcements/node-18-eol-support

### Patch Changes

- ac34b3d: Updated CLI-originated test quarantines to capture Git author information (name, email, username).

## 2.11.3

### Patch Changes

- be24a53: Updated Junit failure description so that the URL is valid even if strings are merged.
- 6366b81: Adjust a11y tree serialization to preserve grouping between inputs and labels.

## 2.11.2

### Patch Changes

- 87df545: Fix edge case where setting hybrid selectors to 'prefer' while not using visual actions caused interactive steps to perform extra waiting

## 2.11.1

### Patch Changes

- 1e91864: Be able to edit while the test is executing

## 2.11.0

### Minor Changes

- 33e7e0b: Move failure recovery into beta with updated behavior. Failure recovery can now be triggered multiple times per test and can execute multiple steps to recover from the failure. Failure recovery no longer proposes step updates that can be applied through the CLI.

### Patch Changes

- 218b97b: `--ignore-failed-setup` flag will set failed tests status to cancelled

## 2.10.2

### Patch Changes

- 8c9446e: Tests in the table now displays fileName

## 2.10.1

### Patch Changes

- 20225db: Add dd_tags for quarantined attributes

## 2.10.0

### Minor Changes

- e8bb935: Element checks now support tag name and computed styles assertions
- 82929e0: Support step-level retries
- 3890bc1: Add `--only-quarantined` and `--skip-quarantined` flags to `run` command, and update `run` behavior to run quarantined tests by default, but not count failures towards pipeline results
- 8729bba: Update V2 assertion models to use latest Gemini and OpenAI models

### Patch Changes

- b3039c5: Remove extra log line from start of `list` output
- 82929e0: Be able to rename a module from the details pane
- 4e44ba9: Allow the text-extraction agent version to be configured and release the v2 text-extraction agent.
- 82929e0: Folders now respect `exclude`
- e8bb935: `check duplicate-ids` command now also checks for duplicate test IDs
- 8729bba: Add new V2 agent configuration for visual assertions

## 2.9.0

### Minor Changes

- ff679fe: Add the ability to add/remove quarantined tests using the CLI
- 67f9869: Skip quarantined tests in runs

### Patch Changes

- 8ab4885: Update look and feel of user input prompts
- af15d62: Add `dd_tags` support for attempts and environment in JUnit report

## 2.8.0

### Minor Changes

- 146cf2b: Remove parent-based redirect and GA global locator redirect
- c263770: store labels on run groups that are triggered with the `--labels` argument

### Patch Changes

- c4295f0: Allow `showZeroOpacityElements` to be set to `inputs-only` to show zero opacity `<input>` elements
- caec33c: Validate that test IDs are valid UUIDs in preflight checks
- df85343: Infinite rerender bug in network viewer
- 7488ee9: Allow merging of run groups with partial metadata

## 2.7.3

### Patch Changes

- d58022d: Support asserting on focus state in element checks
- 3921d96: Support turning on/off offline mode
- ab243cb: Fix a bug that caused before/after/main step results to overwrite each other
- af6320a: When `disableSecondaryCacheResolution` is on, caches that were generated previously using secondary methods are now dropped before executing tests
- 7317c50: `--parallel` takes precedence over `momentic.config.yaml`
- 8e37516: Add `child_process` to JavaScript step

## 2.7.2

### Patch Changes

- a91cacd: When `showZeroOpacityElements` is set to false (which is the default for versions 2.0+), all interactive steps are now prevented from actioning on `opacity: 0` elements. This does not apply to element checks, which commonly need to locate and verify hidden elements.
- 86041ae: Fixed bug that prevented switching between projects in the local app

## 2.7.1

### Patch Changes

- b47024c: Make Gitlab merge base determination non-blocking for CLI test execution
- 2a43dce: Make descriptions required when creating tests

## 2.7.0

### Minor Changes

- d7e5b78: Module parameters now support enum options

### Patch Changes

- b67db64: Added support for deleting and renaming folders

## 2.6.0

### Minor Changes

- Add support for setup and teardown steps
- Added support for partial accessibility fetches

### Patch Changes

- Removed Sentry tracing and profiling to reduce memory usage
- Fixed validation logic for results upload directory contents
- Fixed class checking spacing issues
- Fixed retry logic for generic locator timeouts
- Fixed handling of scroll behavior with pixel values
- Fixed validation for CLI options

## 2.5.0

### Minor Changes

- Added auto-linting on save for test files
- Improved negative element check locators
- Added CLI output for runs and run groups

### Patch Changes

- Fixed API server retry timeout logic
- Fixed cache usage issues in module resolution
- Fixed various performance issues when loading and navigating the app

## 2.4.0

### Minor Changes

- Improved JUnit and Allure reporters to include skipped tests and labels
- Added support for custom reporter and result directories

### Patch Changes

- Fixed issues with test creation directory defaults
- Fixed various UI issues in the test editor

## 2.3.0

### Minor Changes

- New UI for adding steps and modules with enhanced search
- New repository UI for viewing folders, tests, and modules

### Patch Changes

- Fixed issue with test editing and YAML diffs
- Adding a new step now auto-focuses the input field

## 2.2.0

### Minor Changes

- Added new CLI command for checking duplicate test/module names and IDs
- Interactive mode now requires explicit confirmation

## 2.1.0

### Minor Changes

- Added support for more metadata in analytics

### Patch Changes

- Fixed error handling for API requests with empty body
- Fixed issue with environment variable interpolation

## 2.0.0

### Major Changes

- Results are now written locally and must be uploaded explicitly
- Browsers must be installed explicitly
- Tests will fail to run if there are duplicate step or command IDs
- Tests no longer auto-follows newly opened tabs
- Wait for URL step no longer auto-switches to newly opened tabs
- Browsers are now using `headless=new`

### Minor Changes

- Step caches are now isolated to each Git branch to prevent pollution
- Unified commands with `momentic check` and `momentic import`
- Added support for `Chrome for Testing`
