# Do It Then Updates - Development Handoff

**Updated:** 2026-10-02

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

`DoItThen-Updates` is the public Sparkle update-feed and release-asset repository for Do It Then.

It is not the Do It Then application source repository.

## Repository

- GitHub: `TheCuriousProcrastinator/DoItThen-Updates`
- Default branch: `main`
- Source baseline before this policy migration: `d05c5d0e2805cf60a43b253f03458543521d057f`
- Primary tracked update file: `appcast.xml`

Always verify the repository HEAD and live appcast before modifying release metadata.

## Current verified update-feed state

At this handoff:

- product: Do It Then
- latest version: **1.0.3**
- latest build: **17**
- minimum macOS: **14.0**
- architecture requirement: **arm64**
- release asset: `DoItThen-1.0.3.zip`
- release tag referenced by appcast: `v1.0.3`

## Repository role

This repository hosts:

- Sparkle `appcast.xml`
- Do It Then release tags
- downloadable release ZIPs

The application source lives in:

`TheCuriousProcrastinator/DoItThen`

Do not make application-source changes here.

## GitHub Actions policy

There are currently **no GitHub Actions workflows** in this repository.

Keep it that way unless the user explicitly requests a manual clean-environment workflow.

Do not introduce automatic Actions for pushes, pull requests, tags, schedules, release publication, or appcast updates.

Do It Then development, builds, tests, signing, notarization, packaging, and release validation are authoritative on the user's local Mac.

Publishing a Do It Then release does not depend on GitHub Actions.

## Release workflow

For a Do It Then release:

1. validate the exact application change locally in the Do It Then source checkout
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

Before the next Do It Then release, verify this handoff against both the Do It Then source repository and the current live update repository.
