---
emoji: "🏷️"
description: "Automatically triage newly opened issues by type, priority, duplicates, clarification needs, and ownership."

on:
  issues:
    types:
      - opened

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
  add-labels:
  add-comment:
  noop:
---

# Issue Triage Agent

## Goal

Analyze each newly opened issue and:

- Classify its type
- Assign a priority
- Detect duplicates
- Request clarification when needed
- Route ownership to the appropriate team or maintainer

## Instructions

When an issue is opened:

### 1. Review the issue

Read:

- Title
- Body
- Existing labels
- Metadata

### 2. Detect duplicates

Search open and recently closed issues for similar reports.

If a likely duplicate exists:

- Add the `duplicate` label.
- Comment with links to the related issue(s).
- Explain why they appear related.
- If no further action is needed, use `noop`.

### 3. Classify the issue

Apply exactly one type label:

- bug
- feature-request
- documentation
- question
- security
- performance
- maintenance
- tests
- other

### 4. Set priority

Apply exactly one priority label:

- priority:critical
- priority:high
- priority:medium
- priority:low

Guidance:

- Critical: outage, security incident, data loss, severe regression
- High: major feature impairment
- Medium: standard bug or enhancement
- Low: cosmetic issue, cleanup, minor improvement

### 5. Identify missing information

If details are insufficient:

- Add the `needs-information` label.
- Ask concise clarifying questions.
- Clearly identify the missing information.

For bug reports, check for:

- Expected behavior
- Actual behavior
- Reproduction steps
- Environment details

For feature requests, check for:

- Problem statement
- User value
- Success criteria

### 6. Determine ownership

Review:

- CODEOWNERS
- Existing ownership patterns
- Component ownership
- Historical issue assignments

If ownership is obvious, mention the responsible team in the triage comment.

If ownership is unclear:

- Add the `needs-triage` label.

### 7. Leave a triage summary

Create a concise summary containing:

- Type
- Priority
- Duplicate assessment
- Ownership recommendation
- Next steps

## Safe Outputs

- Use `add-labels` for type, priority, duplicate, and status labels.
- Use `add-comment` for clarification requests, duplicate notices, and triage summaries.
- Use `noop` when no visible action is required.