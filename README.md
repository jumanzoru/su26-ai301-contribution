# Contribution [#]: [Issue Title]

**Contribution Number:** 1  
**Student:** Jefferson Umanzor  
**Issue:** [[GitHub issue link]  ](https://github.com/backstage/community-plugins/issues/5994)  
**Status:** Phase I Complete  

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

[Notes on setting up your local development environment - challenges you faced, how you solved them]

### Steps to Reproduce

1. [Step 1]
2. [Step 2]
3. [Observed result]

### Reproduction Evidence

- **Commit showing reproduction:** [Link to commit in your fork]
- **Screenshots/logs:** [If applicable]
- **My findings:** [What you discovered during reproduction]

---

## Solution Approach

### Analysis

[Your analysis of the root cause - what's causing the issue?]

### Proposed Solution

[High-level description of your fix approach]

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** [Restate the problem]

**Match:** [What similar patterns/solutions exist in the codebase?]

**Plan:** [Step-by-step implementation plan]
1. [Modify file X to do Y]
2. [Add function Z]
3. [Update tests]

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]

---

## Testing Strategy

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week [X] Progress

[What you built this week, challenges faced, decisions made]

### Week [Y] Progress

[Continue documenting as you work]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

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
