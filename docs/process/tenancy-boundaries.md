# Tenancy boundaries (Client = Tenant)

## Isolation layers
1. **Identity & access**: RBAC + ABAC; every request must include `tenant_id`.
2. **Data**: canonical/memo storage partitioned by tenant; project-scoped partitions inside.
3. **Retrieval**: vector indexes are tenant-scoped (optionally project-scoped sub-indexes).
4. **Integrations**: GitHub/Notion tokens are tenant-scoped; repo/DB allowlists enforced.

## Known leakage paths (and controls)
- Shared vector index → use per-tenant/per-project indexes.
- Shared caches → partition by `(tenant_id, project_id)`.
- Agent memory reuse → store only in scoped memo domains.
- Overbroad tool tokens → vault + allowlists + policy checks.

## Tenant-wide knowledge base
- Only **promoted** artifacts enter the KB.
- Retrieval is allowed across projects only **within the same tenant**.
