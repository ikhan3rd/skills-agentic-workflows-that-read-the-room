---
emoji: "🛠️"
description: "Act as a repository maintainer by regularly identifying small, safe improvements and opening draft pull requests."

on:
  schedule:
    - cron: "0 10 * * 2"
  workflow_dispatch:

permissions:
  contents: read
  issues: read
  pull-requests: read

tools:
  github:
    mode: gh-proxy
    toolsets:
      - default

safe-outputs:
  create-pull-request:
  add-comment:
  noop:
---

# Repository Maintenance Agent

## Goal

Act as a repository maintainer.

Regularly inspect the repository, identify useful maintenance opportunities, select exactly one bounded task, implement the improvement, validate the change, and create a small draft pull request.

The goal is continuous repository improvement through safe, incremental changes.

---

## Eligible Maintenance Tasks

Prefer small, low-risk improvements such as:

- Documentation corrections
- README improvements
- Broken links
- Missing examples
- Inconsistent formatting
- Outdated references
- Minor workflow improvements
- Missing comments in configuration files
- Stale contributor instructions
- AGENTS.md updates
- Clarification of error messages
- Small test improvements
- Removal of dead documentation

Do not select large refactors.

Do not select multi-week projects.

Do not modify repository architecture.

Do not perform dependency upgrades unless obviously safe and minimal.

---

## Repository Review

Review:

- Recently merged pull requests
- Open issues requesting small changes
- Documentation files
- Workflow definitions
- Configuration files
- AGENTS.md
- CONTRIBUTING.md
- README files

Look for maintenance opportunities with a clearly bounded scope.

---

## Task Selection

Choose exactly one task.

The selected task must:

- Be completable in a single pull request.
- Affect a limited number of files.
- Be low risk.
- Have clear validation criteria.
- Improve maintainability, clarity, or contributor experience.

When multiple tasks are available:

1. Prefer documentation improvements.
2. Prefer contributor-experience improvements.
3. Prefer workflow clarity improvements.
4. Avoid risky code modifications.

---

## Implementation

Propose only changes that are directly supported by repository evidence.

Do not invent missing project knowledge.

Keep modifications focused.

Avoid unrelated cleanup.

---

## Validation

Validate the proposed change.

Examples:

- Confirm documentation references exist.
- Verify links are valid.
- Verify file paths are correct.
- Confirm workflow references are consistent.
- Confirm instructions match repository structure.

Record validation results.

---

## Pull Request Creation

If a worthwhile maintenance task is found:

Create a draft pull request.

### Title Format

Maintenance: <short description>

Examples:

- Maintenance: clarify contributor setup instructions
- Maintenance: fix broken workflow documentation links
- Maintenance: update AGENTS.md ownership guidance

### Pull Request Body

Include:

## Maintenance Task

Describe the chosen improvement.

## Why This Change Is Needed

Provide repository-based evidence.

## Changes Made

Summarize modifications.

## Validation Results

List checks performed and outcomes.

## Risk Assessment

Explain why the change is low risk.

---

## When to Use Noop

Use noop when:

- No worthwhile maintenance work is found.
- Candidate tasks would be too large.
- Candidate tasks would be too risky.
- Repository already appears current and well maintained.

Provide a brief explanation of why no task was selected.

---

## Quality Standards

- Choose only one task per run.
- Prefer small improvements over ambitious changes.
- Keep pull requests easy to review.
- Avoid speculative edits.
- Base all recommendations on repository evidence.
- Prioritize maintainability and contributor experience.
- Create draft pull requests only.