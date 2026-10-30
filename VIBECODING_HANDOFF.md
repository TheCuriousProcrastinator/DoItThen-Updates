<!-- VIBE-CURRENT-STATE:START -->
## Current repository facts (generated, authoritative only for the facts listed)

- Repository: `TheCuriousProcrastinator/DoItThen-Updates`; local working branch: `main`.
- Version data below is read from the **Git index** (the files staged for commit).
- Source `appcast.xml`: version `1.0.31`, build `45`.
- GitHub publication: Published GitHub release `v1.0.31` (reported by GitHub API). Other distribution channels are **unverified**.
- This section does **not** establish local build success, manual QA, App Store/Chrome Web Store approval, notarization, live website deployment, or release-asset integrity.
- The narrative below maintains architecture, decisions, issues and test evidence. Its older status and version claims are **historical** unless explicitly reconciled with this section.
- Before executable changes, inspect the actual checkout and validate the **exact files** on the real Mac. No automatic GitHub Actions.

<!-- VIBE-CURRENT-STATE:END -->

# Doit Then Updates - Development Handoff

## Publish/release command - standing authorization (2026-10-13)

- When the user says "publish", "release", "make update", or equivalent, treat that statement as standing authorization to complete the full validated local release and publication workflow. Do not ask for additional publication consent or confirmation.
- Never create Terminal scripts that ask the user to type "PASS", "YES", or another validation or confirmation keyword before publishing. Never introduce case-sensitive validation gates. A user statement such as "pass", "passed", "works", or equivalent is an explicit confirmation of the corresponding manual tests, regardless of capitalization.
- If the exact source change has already passed required local build/tests and the user confirmed required manual verification, proceed immediately with committing the exact tested source, handoff update, release build/signing/packaging, GitHub releases, Sparkle appcast publication, and live verification. Do not ask the user to repeat validation.
- Keep the non-negotiable local validation gate: do not publish unvalidated executable/build-affecting changes. If required validation genuinely has not happened, stop and explain that blocker, with the minimum required local test instructions; do not pretend validation passed.
- Stop only for real blockers such as missing local validation, failed build/test, unsafe working tree, missing signing credentials, or a failed release step. Do not create arbitrary pauses, keyword prompts, or extra approvals. Do not run GitHub Actions automatically.
- If local Mac access is unavailable, supply one copy-pasteable, **noninteractive** Terminal block to carry out already-authorized release actions in the exact validated Mac checkout. Use existing credentials/keychain without inventing confirmation prompts. If genuine credentials or macOS prompts are unavoidable, report them as blockers, not additional publication-approval requests.
- This rule takes precedence over older handoff wording that might suggest an additional user confirmation after validation. It does not override mandatory validation or source-of-truth checks.


**Updated:** 2026-10-13

## Shared Vibe Coding workflow rules (2026-10-08)

### Documentation-only handoff exception
- When the user explicitly requests a documentation-only update, ChatGPT may edit the existing root `VIBECODING_HANDOFF.md` directly through GitHub without requiring a Mac build or a local checkout step.
- First inspect the actual repository, target branch, and existing handoff. Change only the handoff, preserve historical project context, and verify the resulting GitHub file and commit. Do not use this exception for application code, tests, scripts, configuration, workflows, version/build changes, release assets, or other build-affecting files.
- Before the next local development change, fetch the remote branch and reconcile the updated handoff with the local checkout. Never overwrite or silently reset unrelated local changes.
- The normal rule remains: validate the exact executable/build-affecting changes in the real Mac checkout before committing or pushing those changes. Include a current handoff with every meaningful validated development commit.

### Temporary worktrees, releases, and logs
- Create temporary Git worktrees under `/Users/alex/Desktop/tmp/<project>-...` using a project-specific name.
- Put release working folders, temporary release artifacts, staging directories, and build/release logs under `/Users/alex/Desktop/tmp/<project>-release-...`.
- Do not create disposable worktrees inside `/Users/alex/Documents/Vibe Coding`.
- Do not place release artifacts or logs directly on the Desktop root.
- After a successful verified release, remove temporary worktrees and temporary release artifacts when safe. Do not remove active worktrees, uncommitted work, published assets, or permanent project files.
- Retain failure logs only when useful for debugging; remove unnecessary temporary logs.
- These instructions govern future operations and take precedence over historical temporary-path examples elsewhere in this handoff.

### Low-overhead development defaults
- Use ChatGPT plus GitHub inspection and Mac-local Terminal scripts by default; do not use Codex, ChatGPT Work, separately billed API agents, or GitHub Actions runners unless explicitly requested.
- Prefer existing project scripts. Give one local command block to apply, build, test, and launch an executable change, then a separate commit/push block only after required validation is confirmed.
- Documentation-only updates under the exception above do not require a rebuild.

## Project

`DoItThen-Updates` is the public Sparkle update-feed and release-asset repository for Doit Then.

It is not the Doit Then application source repository.

## Repository

- GitHub: `TheCuriousProcrastinator/DoItThen-Updates`
- Default branch: `main`
- Source baseline before this policy migration: `d05c5d0e2805cf60a43b253f03458543521d057f`
- Primary tracked update file: `appcast.xml`

Always verify the repository HEAD and live appcast before modifying release metadata.

## Current verified update-feed state — 2026-10-18

Verified against the published `main/appcast.xml`, source release metadata, and both GitHub Releases:

- Product: **Doit Then**.
- Latest published version: **1.0.26**, build **40**; tag `v1.0.26`.
- Source release commit: `bbbf04dc4bd0a2cb59560619a58158b34d19e40e`; the source `main` HEAD later advances to documentation-only commits.
- Minimum macOS: **14.0**; hardware requirement: **arm64** in the Sparkle feed.
- Release asset: `DoItThen-1.0.26.zip`, **8,152,007 bytes** in both source and updates GitHub Releases.
- Release ZIP SHA-256 recorded by the app's verified release handoff: `fad69984084a067a90db6f132f352ac252a1d7339e7e166177a29f7881884c07`.
- Signed Sparkle feed: `https://raw.githubusercontent.com/TheCuriousProcrastinator/DoItThen-Updates/main/appcast.xml`; it advertises **1.0.26 / build 40** and the updates-repo v1.0.26 download URL.
- Latest verified updates repository `main` HEAD **before this documentation-only change**: `2dd1737e77854249c90f820b1b378cbe6b422073`. Fetch the new HEAD after this commit.
- Companion Chrome extension version **0.2.1** has been submitted for Chrome Web Store review; approval/publication remains unverified. The user reported production version 0.2.
- Earlier references to v1.0.17 below or in previous handoff revisions are **historical**. Do not mistake the old October 13 snapshot for the current release.
- No GitHub Actions workflows exist in this updates repository, and releases do not require automatic CI. This documentation-only commit does **not** modify the appcast or release assets.

## Repository role

This repository hosts:

- Sparkle `appcast.xml`
- Doit Then release tags
- downloadable release ZIPs

The application source lives in:

`TheCuriousProcrastinator/DoItThen`

Do not make application-source changes here.

## GitHub Actions policy

There are currently **no GitHub Actions workflows** in this repository.

Keep it that way unless the user explicitly requests a manual clean-environment workflow.

Do not introduce automatic Actions for pushes, pull requests, tags, schedules, release publication, or appcast updates.

Doit Then development, builds, tests, signing, notarization, packaging, and release validation are authoritative on the user's local Mac.

Publishing a Doit Then release does not depend on GitHub Actions.

## Release workflow

For a Doit Then release:

1. validate the exact application change locally in the Doit Then source checkout
2. build, sign, notarize, package, and verify locally as applicable
3. commit and push the exact validated source/release changes
4. create and push the release tag
5. publish the verified ZIP as a GitHub Release asset in this repository
6. update `appcast.xml` using exact metadata from the final local artifact
7. verify version, build, release URL, file length, and Sparkle signature
8. push the appcast update
9. verify the live release asset and live appcast
10. verify the update feed sees the intended release when appropriate

Do not invent release metadata.

## Important rule

A release-tag push must not automatically trigger GitHub Actions.

GitHub is source/release/update-feed hosting. Local Mac validation is authoritative.

## Policy migration scope

This migration adds only:

`VIBECODING_HANDOFF.md`

It does not change `appcast.xml`, README content, releases, assets, tags, signatures, or update behavior.

## Next task

Before the next Doit Then release, verify this handoff against both the Doit Then source repository and the current live update repository.


## Automatic handoff synchronization (2026-10-19)

- The tracked `.githooks/pre-commit` runs `Tools/vibe_handoff.py sync-staged` locally. It reads version/build from the Git index, reads the GitHub published release, refreshes only the bounded generated current-state section and stages the handoff in the same commit. It does **not** modify application code or establish build/manual-test validation.
- On a fresh Mac checkout, run `sh .githooks/install.sh` once. It refuses to replace an existing pre-commit hook. Do not bypass hooks with `--no-verify`. Changes to feature behavior, debugging decisions, known issues, manual validation, and next work still require a human-maintained narrative entry after the exact local test passes.
- Do not commit or push any executable change before successful validation in the real Mac checkout. The tool makes documentation updates only; GitHub Actions remain manual only.
- Sparkle applications' release scripts refresh generated release facts in source and update-feed handoffs once their respective release milestones are reached. Verify the live release/feed before claiming publication succeeded. Projects without a scripted release must refresh and commit the handoff after externally verifying publication.
- If GitHub release status cannot be verified, or the handoff contains unstaged edits, the hook blocks rather than guessing or overwriting your changes.
