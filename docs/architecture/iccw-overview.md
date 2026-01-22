# ICCW Overview

## Tenancy model
- **Tenant = Client** (hard boundary)
- Data stores, caches, indexes, and credentials are partitioned by `tenant_id`
- Default retrieval is project-scoped; tenant-wide KB retrieval is explicit and tenant-only

## Write domains
- **Canonical** (human-owned): decisions, requirements, final architecture, approved outputs
- **Memo** (agent-owned): scratchpads, ideation variants, research dumps
- **Draft** (controlled): Notion Drafts DB entries + GitHub draft PRs (same repo)

## Two-phase commit
1. **Propose**: agent generates a structured change (diff) with evidence
2. **Approve**: human (or delegated reviewer) approves
3. **Apply**: tools execute write; audit log records provenance

## Integrations
- **GitHub**: issues/discussions for work, PRs for versioned change (draft PRs allowed)
- **Notion**: narrative, research library, decision records, and tenant-wide Drafts DB
