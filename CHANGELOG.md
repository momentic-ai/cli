# momentic

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
