# Two-phase commit (Propose → Approve → Apply)

## Purpose
Prevent silent mutation of canonical project truth while letting agents work quickly.

## Phases
### 1) Propose
- Output is a **Proposal** with:
  - target (Notion page/DB entry, GitHub PR/issue)
  - diff / intended changes
  - evidence links (sources, prior decisions)
  - required reviewers (if any)

### 2) Approve
- Human (or authorized role) approves in an approvals inbox.
- Approvals are recorded in an immutable audit log.

### 3) Apply
- System executes the write using scoped tokens.
- Result is an **ActionResult** event with links + artifacts.

## Defaults
- Agents can always write to Memo.
- Draft writes are allowed only into designated areas:
  - Notion tenant-wide Drafts DB
  - GitHub draft PRs in the same repo
