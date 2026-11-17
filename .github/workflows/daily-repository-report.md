---
emoji: "📊"
description: "Create a daily repository activity report summarizing issues, pull requests, and blockers."

on:
  schedule:
    - cron: "0 8 * * *"
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
  create-issue:
  noop:
---

# Daily Repository Activity Report

## Goal

Generate a daily report of repository activity and publish it as a GitHub issue.

The report should help maintainers quickly understand:

- New issues opened
- Pull requests merged
- Potential blockers
- Overall repository health

## Instructions

Analyze activity from the previous 24 hours.

### 1. Review Newly Opened Issues

Identify issues created during the reporting period.

For each notable issue include:

- Issue number
- Title
- Type (bug, feature, documentation, etc.)
- Current status
- Any issue requiring urgent attention

Summarize recurring themes or trends.

---

### 2. Review Merged Pull Requests

Identify pull requests merged during the reporting period.

For each merged pull request summarize:

- Pull request number
- Title
- High-level purpose
- Impact on the repository

Group related pull requests when appropriate.

---

### 3. Identify Open Blockers

Review open issues and pull requests.

Flag items that appear blocked because:

- Waiting for reviewer response
- Waiting for author response
- Missing information
- Failed checks
- Merge conflicts
- Dependency on another issue or pull request

For each blocker include:

- Reference number
- Short description
- Reason it appears blocked

Only report blockers supported by repository evidence.

---

### 4. Repository Highlights

Provide a concise summary including:

- Most significant issue reported
- Most impactful pull request merged
- Major risks or concerns
- Areas requiring maintainer attention

Keep observations objective and evidence-based.

---

### 5. Create Daily Report Issue

Create a new issue with the title:

Daily Repository Report - YYYY-MM-DD

Use the following format:

# Daily Repository Report

## New Issues

- Summary of newly opened issues

## Merged Pull Requests

- Summary of recently merged pull requests

## Open Blockers

- Summary of blocked work items

## Highlights

- Key accomplishments
- Risks
- Recommended follow-up actions

## Overall Assessment

Provide a short assessment of repository activity and health.

---

## Safe Output Usage

Use:

- create-issue for publishing the report

Use:

- noop if no meaningful repository activity occurred during the reporting window.

---

## Quality Rules

- Focus on the previous 24 hours.
- Be concise and actionable.
- Do not duplicate large amounts of issue or pull request content.
- Do not speculate.
- Use repository evidence only.
- Highlight important trends, risks, and blockers.