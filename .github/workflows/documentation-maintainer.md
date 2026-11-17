---
emoji: "📚"
description: "Keep repository documentation synchronized with recent code and repository changes."

on:
  schedule:
    - cron: "0 7 * * *"
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
  noop:
---

# Documentation Maintenance Agent

## Goal

Keep repository documentation accurate and current.

Review recent repository activity, identify documentation that is no longer aligned with the current codebase, and create a pull request containing necessary updates.

Focus on maintaining accuracy rather than rewriting documentation unnecessarily.

---

## Scope

Review documentation including:

- README.md
- CONTRIBUTING.md
- AGENTS.md
- Architecture documentation
- Setup guides
- Developer guides
- Operational runbooks
- Workflow documentation
- Documentation under docs/
- Inline examples referenced by documentation

---

## Review Recent Changes

Analyze repository activity since the previous successful run.

Review:

- Recently merged pull requests
- New source files
- Deleted source files
- Renamed files
- New workflows
- Changed APIs
- Updated configuration files
- Changes to commands, scripts, or tooling

Identify documentation that may have been affected.

---

## Detect Documentation Drift

Look for situations where documentation and implementation differ.

Examples include:

- Referencing files that no longer exist
- Missing newly introduced features
- Outdated setup instructions
- Incorrect command examples
- Incorrect workflow descriptions
- Missing references to new directories
- Stale configuration guidance
- Obsolete troubleshooting instructions

Only flag drift when supported by repository evidence.

---

## Determine Required Updates

Prioritize:

1. Incorrect documentation
2. Missing documentation for important changes
3. Broken references
4. Missing workflow explanations
5. Missing contributor guidance
6. Minor wording improvements

Do not perform speculative edits.

Do not rewrite documentation solely for style.

---

## Prepare Changes

Update only the documentation files that require correction.

The updates should:

- Reflect current repository behavior
- Match the current repository structure
- Reference current workflows and files
- Preserve valid existing information
- Remain concise and maintainable

Avoid unrelated edits.

---

## Validation

Before proposing changes:

- Verify referenced files exist.
- Verify commands match repository contents.
- Verify workflow names are accurate.
- Verify paths are correct.
- Verify documentation examples remain valid.

Record validation results.

---

## Pull Request Creation

When documentation changes are warranted, create a draft pull request.

### Pull Request Title

Documentation Maintenance: synchronize docs with repository

### Pull Request Description

Include:

## Summary

Explain why documentation updates were required.

## Documentation Drift Detected

List discrepancies discovered.

## Files Updated

List modified documentation files.

## Validation Results

Summarize validation checks performed.

## Risk Assessment

Explain why the changes are low risk.

---

## When to Use Noop

Use noop when:

- Documentation accurately reflects repository state.
- No meaningful drift is detected.
- Evidence is insufficient to justify an update.

Provide a concise explanation.

---

## Quality Standards

- Accuracy takes priority over completeness.
- Base changes only on repository evidence.
- Prefer small focused updates.
- Avoid assumptions.
- Keep pull requests easy to review.
- Do not modify source code.
- Update documentation only.