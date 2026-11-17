---
emoji: "🤖"
description: "Weekly maintenance of AGENTS.md based on merged pull requests and repository changes."

on:
  schedule:
    - cron: "0 9 * * 1"
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

# AGENTS.md Maintenance Agent

## Goal

Keep AGENTS.md accurate and up to date by reviewing repository changes since the previous run and proposing updates through a pull request.

## Instructions

Run once per week.

Review repository activity since the last successful workflow run.

Focus on:

- Merged pull requests
- Newly added source files
- Deleted source files
- Renamed files
- Architectural changes
- New workflows
- New agent responsibilities
- Changes to project structure
- Changes to development conventions

---

## Step 1: Review Merged Pull Requests

Analyze pull requests merged since the previous run.

Identify:

- New capabilities
- Removed capabilities
- Changes in ownership
- Process changes
- Workflow changes
- Documentation changes that affect contributors

Summarize the impact of each significant merged pull request.

Ignore trivial formatting-only changes unless they affect AGENTS.md guidance.

---

## Step 2: Review Repository Structure

Examine current repository structure.

Look for:

- New directories
- New components
- New services
- New workflows
- New tooling
- Removed or deprecated areas

Determine whether AGENTS.md still accurately reflects the repository.

---

## Step 3: Review Existing AGENTS.md

Read the current AGENTS.md.

Evaluate whether it accurately describes:

- Repository purpose
- Architecture
- Key components
- Development workflows
- Agent responsibilities
- Contributor guidance
- Automation workflows

Identify outdated, inaccurate, or missing content.

---

## Step 4: Draft Updates

If updates are warranted:

Prepare an improved AGENTS.md that:

- Preserves accurate existing content.
- Removes obsolete information.
- Adds newly relevant information.
- Keeps guidance concise and actionable.
- Reflects current repository structure.
- Reflects recently merged work.

Do not invent information that cannot be supported by repository evidence.

---

## Step 5: Create Pull Request

If meaningful changes are required:

Create a pull request that:

### Title

Update AGENTS.md based on recent repository changes

### Description

Include:

#### Summary

Brief explanation of why the update is needed.

#### Changes Identified

- Significant merged pull requests reviewed
- Repository structure changes
- Workflow changes
- New capabilities discovered

#### AGENTS.md Updates

Summarize every modification proposed.

Explain how each change improves accuracy.

---

## When to Use Noop

Use noop when:

- No meaningful repository changes occurred.
- AGENTS.md is already accurate.
- Proposed edits would only reword content without improving accuracy.

---

## Quality Rules

- Prefer accuracy over completeness.
- Do not fabricate ownership information.
- Do not infer architecture that is not present in the repository.
- Preserve existing guidance when still valid.
- Keep AGENTS.md human-readable.
- Create a pull request only when substantive updates are justified.