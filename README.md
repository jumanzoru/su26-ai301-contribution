# Contribution 1: Enable `listDeprecations` for Backstage Vault Workspace

**Contribution Number:** 1  
**Student:** Jefferson Umanzor  
**Issue:** [[GitHub issue link]  ](https://github.com/backstage/community-plugins/issues/5994)  
**Status:** Phase IV Complete / Awaiting Review

---

## Why I Chose This Issue

I chose this issue because it aligns strongly with my SWE goals & gives me experience contributing to a large TypeScript monorepo in the Backstage developer-platform ecosystem. The work involves repository tooling, deprecated API detection, plugin maintenance, & following existing contribution patterns in a production open-source codebase.

I'm especially interested in the `vault` workspace because Vault is related to infrastructure & secrets management, which gives the contribution a stronger backend/platform engineering angle than a purely frontend cleanup. My goal is to use this issue to practice reading an established codebase, running project tooling, identifying deprecated API usage, & making a focused PR that improves long-term maintainability.

---

## Understanding the Issue

### Problem Description

The Backstage community-plugins maintainers are enabling `listDeprecations` checks across maintainer-owned workspaces so deprecated Backstage APIs can be identified and removed. Some workspaces, including `vault`, haven't opted into this check yet. Without this tooling enabled, deprecated API usage can remain hidden & make the plugin harder to maintain as Backstage evolves.

### Expected Behavior

The `vault` workspace should have `listDeprecations` enabled in its `bcp.json` configuration. After enabling it, running `yarn backstage-cli repo list-deprecations` should identify any deprecated API usage in the workspace. Any reported deprecated usages should be updated so the workspace follows current Backstage APIs.

### Current Behavior

The vault workspace currently has a `bcp.json` file with `autoVersionBump` and `knipReports`, but it doesn't include `"listDeprecations": true`. Because of that, the workspace isn't opted into the deprecation-checking workflow.

### Affected Components

The main affected component is the `vault` workspace inside the Backstage community-plugins monorepo.

Potentially affected file:
- `workspaces/vault/bcp.json`

Other affected files may be identified in Phase II after running:
- `yarn install`
- `yarn backstage-cli repo list-deprecations`

---

## Reproduction Process

### Environment Setup

I cloned my fork of the Backstage `community-plugins` repository, created a working branch, and inspected the `vault` workspace configuration for issue #5994.

### Steps to Reproduce

1. Fork and clone the Backstage community-plugins repository.
2.  Create a working branch in the fork.
3.  Open the vault workspace configuration file:
     - workspaces/vault/bcp.json
4. Inspect the current configuration.
5. Observe that workspaces/vault/bcp.json includes existing tooling options such as autoVersionBump and knipReports, but does not include "listDeprecations": true.
6. Compare this with the issue requirement, which asks for listDeprecations to be enabled for the vault workspace.
7. Expected behavior: the vault workspace should include "listDeprecations": true so deprecated Backstage API usage can be detected.
8. Actual behavior: the vault workspace is missing the listDeprecations configuration.

### Reproduction Evidence

- Working branch: https://github.com/jumanzoru/community-plugins/tree/vault/list-deprecations
- Issue: https://github.com/backstage/community-plugins/issues/5994
- Relevant file: workspaces/vault/bcp.json
- Finding: This is a repository tooling/configuration issue. The vault workspace has not opted into the listDeprecations check, so the likely fix is to update workspaces/vault/bcp.json by adding "listDeprecations": true.

---

## Solution Approach

### Analysis

The root cause is that the vault workspace configuration is missing the listDeprecations option in workspaces/vault/bcp.json.

### Proposed Solution

Add "listDeprecations": true to workspaces/vault/bcp.json, following the existing configuration style used in the file and in other workspaces.

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** The issue asks for the vault workspace to opt into Backstage’s deprecation-checking workflow.

**Match:** I will compare workspaces/vault/bcp.json with other workspace bcp.json files that already include listDeprecations.

**Plan:** [Step-by-step implementation plan]
1. Open workspaces/vault/bcp.json.
2. Add "listDeprecations": true alongside the existing workspace tooling options.
3. Run the relevant repo validation/deprecation command.
4. If the command reports deprecated API usage, inspect whether those changes are in scope.
5. Commit the focused configuration change to my working branch.

**Implement:** Working branch: https://github.com/jumanzoru/community-plugins/tree/vault/list-deprecations

**Review:** Before opening a PR, I will confirm the change follows the repo’s existing JSON/configuration style and does not include unrelated cleanup.

**Evaluate:** I will verify the change by running the relevant Backstage deprecation-checking workflow and confirming the workspace is included without introducing unexpected failures.

---

## Testing Strategy

### Unit Tests

No unit tests were added for this phase because the change is a workspace configuration update rather than a code-path or function-level behavior change.

### Integration Tests

No integration tests were added for this phase. The relevant validation is the repository-level deprecation-checking workflow, which is run through the Backstage CLI instead of a traditional integration test.

### Manual Testing

I installed the project dependencies and ran the relevant Backstage deprecation-checking command:

`yarn backstage-cli repo list-deprecations`

The command started successfully, but it failed while linting `workspaces/rbac/eslint.frontend-shared.cjs` due to an ESLint parser configuration issue involving the `deprecation/deprecation` rule and missing TypeScript parser services.

Because this failure occurred in the `rbac` workspace rather than the `vault` workspace, I treated it as a repository-level validation blocker rather than evidence that my `vault` configuration change was incorrect.

I also manually verified that the intended change is limited to the `vault` workspace configuration:
- Relevant file: `workspaces/vault/bcp.json`
- Change made: added `"listDeprecations": true`
- Scope: focused configuration change only, no unrelated cleanup

---

## Implementation Notes

## Implementation Notes

### Week 4 Progress

I implemented the focused configuration change for Backstage community-plugins issue #5994. I updated `workspaces/vault/bcp.json` to enable `listDeprecations` for the `vault` workspace.

### Code Changes

- **Files modified:** `workspaces/vault/bcp.json`
- **Key commit:** https://github.com/jumanzoru/community-plugins/commit/71648d33e
- **Approach decision:** I kept the change scoped to the `vault` workspace configuration and did not include unrelated cleanup.

---

## Pull Request

**PR Link:** https://github.com/backstage/community-plugins/pull/9724

**PR Description:**  
This PR enables `listDeprecations` for the Backstage `vault` workspace by adding `"listDeprecations": true` to `workspaces/vault/bcp.json`.

**Maintainer Feedback:**
- No maintainer feedback yet.

**Status:** Awaiting review

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]
