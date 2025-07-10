# momentic

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
