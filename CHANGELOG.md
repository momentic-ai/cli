# momentic

## 2.64.1

### Patch Changes

- 99436cc: Fix bug where MCP could create nested modules through conditional steps.

## 2.64.0

### Minor Changes

- 2558c8e: Update MCP step schema time units to match the units that are stored on the resulting momentic steps. Previously, all units were in ms but units will now vary depending on the step configuration

## 2.63.0

### Minor Changes

- 2b8e2ee: Add --browser flag to the run command to allow selecting a browser that overrides test and config defaults
- db9d803: Make AI actions always-on by removing the aiAction feature gate. Users no longer need to set ai.aiAction: true in momentic.config.yaml to use AI action steps.

### Patch Changes

- f76d03d: Add browser setting enableForceClickForMissingRedirectElement
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
- c2cf2cc: Update the momentic-test skill to be more hesistant to make unnecessary semantic changes like filling in unnecesary fields on steps, changing quote types, etc.

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

- 40a5289: Change preview tool to bypass smart waiting to improve latency for test creation via repeating[preview -> think] -> splice pattern.
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

- b2d21c4: Preprocess redirectable elements to no longer be momentic-ineligible.

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
- 5f5a62b: Removed the MCP flag that allowed edits to bypass disk persistence; edits now always follow the context-level persistence setting.

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
- eca74d8: Step selection defaults to ordered by alphabetical order.
- 48fecad: Sort modules alphabetically when creating a new step
- 48fecad: Fix an issue where cleanup would fail after creating test results archives due to open file streams

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

- 9fdae76: Fix issue with hanlding numerical values in DOM processing

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
- 16eea66: MCP now summarizes your test_edit session and uses it to return a structured response telling you if it accomplished its goal and if it is safe to continue"
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
- 7eb152a: MCP linting step adjusted to be less nitty in rejecting improper usage.
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

- 65aec9f: Block fullstory scripts that have been vendored to prevent performance degradation in test environments
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

- 5c848d1: Lock "ai" to prevent toast error upon finish message mismatch between copilot's frontend and streamText.

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

- ceeba05: Allow important CSS class names, styles, and HTML attributes to be configured in the local CLI, enabling customization of avaialble context for AI agents

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
- Fixed verious performance issues when loading and navigating the app

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
