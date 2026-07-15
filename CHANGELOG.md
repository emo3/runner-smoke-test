# Changelog

All notable changes to this smoke-test project are documented here.

## 2026-07-14

- Verify that both `dig` and `nslookup` are available in the runner image.
- Removed the obsolete loopback registry-image documentation; the job inherits
  the runner's pinned default image.

## 2026-07-09

- Added Apache License 2.0 project licensing.
- Added this changelog.
- Updated the smoke-test runner tag from `k8s` to `local`.
- Expanded the README with project purpose, CI behavior, prerequisites,
  troubleshooting, and documentation history.

## 2026-07-07

- Created the initial smoke-test project.
