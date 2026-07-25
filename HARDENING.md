<!-- markdownlint-disable -->

# Hardening Report: GeekyEggo--delete-artifact/v6.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **GeekyEggo--delete-artifact/v6.0.0** was hardened automatically. 4 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple `uses:` references in .github/workflows/ci.yml are pinned to mutable version tags instead of full 40-character commit SHAs, making the workflow vulnerable to supply-chain attacks if the tag is moved. Failing references: `actions/checkout@v6` (line 18), `actions/upload-artifact@v6` (lines 23, 28, 33).

Locations:

- `.github/workflows/ci.yml:18`
- `.github/workflows/ci.yml:23`
- `.github/workflows/ci.yml:28`
- `.github/workflows/ci.yml:33`

### unpinned-uses (severity: high)

Multiple `uses:` references in .github/workflows/example.yml are pinned to mutable version tags instead of full 40-character commit SHAs, making the workflow vulnerable to supply-chain attacks if the tag is moved. Failing references: `actions/checkout@v4` (line 19), `actions/upload-artifact@v4` (lines 24, 29, 34), `geekyeggo/delete-artifact@v5` (lines 39, 44).

Locations:

- `.github/workflows/example.yml:19`
- `.github/workflows/example.yml:24`
- `.github/workflows/example.yml:29`
- `.github/workflows/example.yml:34`
- `.github/workflows/example.yml:39`
- `.github/workflows/example.yml:44`

### permissions (severity: medium)

Workflow .github/workflows/ci.yml has no top-level `permissions:` key and the single job (`test`) also has no `permissions:` key. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be broader than necessary.

Locations:

- `.github/workflows/ci.yml:1`

### permissions (severity: medium)

Workflow .github/workflows/example.yml has no top-level `permissions:` key and the single job (`test`) also has no `permissions:` key. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be broader than necessary.

Locations:

- `.github/workflows/example.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, permissions

**Notes:**

Fixed all four findings across both workflow files:

**ci.yml:**
- Added `permissions: {}` at the top level to restrict default token permissions
- Pinned `actions/checkout@v6` → `actions/checkout@d23441a48e516b6c34aea4fa41551a30e30af803 # v6`
- Pinned `actions/upload-artifact@v6` (3 occurrences) → `actions/upload-artifact@b7c566a772e6b6bfb58ed0dc250532a479d7789f # v6`

**example.yml:**
- Added `permissions: {}` at the top level to restrict default token permissions
- Pinned `actions/checkout@v4` → `actions/checkout@11d5960a326750d5838078e36cf38b85af677262 # v4`
- Pinned `actions/upload-artifact@v4` (3 occurrences) → `actions/upload-artifact@ea165f8d65b6e75b540449e92b4886f43607fa02 # v4`
- Pinned `geekyeggo/delete-artifact@v5` (2 occurrences) → `geekyeggo/delete-artifact@f275313e70c08f6120db482d7a6b98377786765b # v5`

All SHAs were resolved via lookup_action_sha. Original version tags are preserved as inline comments for readability.

