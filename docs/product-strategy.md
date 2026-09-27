# Prism MCP Plugins product strategy

Effective: 2026-09-27. Source-review evidence below retains its original review date, 2026-09-24. Active direction for new work. Implementation is tracked in the [plan](implementation-plan.md); proposed additions are not shipped features.

## Authority ecosystem alignment — 2026-09-27

PrismWorks builds authority infrastructure for autonomous AI. Databridle's first commercial package is delegated financial operations in existing ERP/payment environments. Its core object is a business mandate with authenticated delegation rights, trusted purpose/business objects, attenuated child grants, shared limits, expiry and revocation. Engineering/IT and security response expand the same core after the initial package is repeatable. This direction supersedes engineering-first or security-platform positioning in earlier planning.

**Prism MCP Plugins's boundary:** Optional executable adapter examples after implementation; no existing broad catalogue or trust-by-installation.

**Required implementation change:** Keep native plugin execution outside the protected scope until isolation and bypass acceptance pass. Use synthetic financial fixtures only where useful; a plugin cannot mint grants, union permissions or evade root budget accounting.

Carry mandate/root/parent/grant and current-authority revision through a versioned adapter, with exact request digest and reservation reference when applicable. Databridle's runtime Authority Graph and transactional reservation ledger are authoritative; no accelerator keeps a competing writable copy. Workflow/evidence dependencies do not grant authority. Child grants cannot multiply aggregate limits or silently combine permissions.

**Acceptance before claiming integration:** issuer has the right to delegate; changed beneficiary/resource/request rejected; cross-tenant references rejected; concurrent descendants cannot overrun a shared root limit; accepted-but-timed-out writes remain unknown and reserved until reconciled; revoked/stale authority cannot authorize the next protected use. Apply each check at the component's advertised boundary and use explicit substitution fixtures for responsibilities owned elsewhere. No real financial transaction is required.

**Scope removed or deferred:** independent enterprise authority platform, graph administration/federation ahead of runtime correctness, and any mandatory all-accelerator installation. Preserve existing useful behavior, licenses, ownership and independent use. These are planned adapter requirements, not a claim of deployed capabilities. Existing remediation and migration checks below remain prerequisites.

## Purpose and boundary

**A reserved home for a small number of executable integration examples, when justified.**

Own example adapter source and its tests. The SDK owns plugin mechanism, Tools owns runnable reference applications, Registry owns discovery metadata. Do not duplicate the same executable across all three.

## Current repository evidence

Review of the local working tree, including pre-existing changes; source presence is not deployment evidence.

| Source | Observation |
| --- | --- |
| [README.md](../README.md) | Previous README listed many plugins, templates, downloads and tests that are absent from this checkout. |
| [LICENSE](../LICENSE) | License file exists; this review preserves it. |
| [CLA.md](../CLA.md) | Contributor agreement exists; no licensing change is implied. |

Verification this review: Top-level/source inventory found README, LICENSE and CLA only; no implementation catalogue or test suite to validate.

## Retain

Retain working behavior, user data, existing integrations, tests, licensing and independent use within the boundary above. Maintain existing support obligations. Preserve local changes from other work; this review does not release or deploy code.

## Remove or defer

- Remove nonexistent plugin catalogue, download statistics, featured-plugin rankings, missing template commands and blanket coverage claims.
- Remove the retired Prism Platform upsell from the current story.

## Modify

- Keep the repository in a deferred examples role; prefer a fixture in MCP Tools until more than one consumer needs reusable plugin packaging.
- Describe native plugins as trusted in-process code, not sandboxed extensions.

## Add

- Only when justified: one minimal adapter, permissions manifest, build/test instructions and compatibility record.
- Security/release ownership and a process-isolation option before untrusted third-party execution is supported.

## Integration rules

This is the target integration design, not a claim of an existing Databridle adapter. Components communicate through versioned contracts and keep independent storage. No shared database, forced cloud account or mandatory all-product installation.

The host proposes work; Databridle decides protected enterprise actions; the credential provider enforces its own access conditions; the executor performs only the bound action. Local restrictions can deny but cannot widen an enterprise grant. Human software acceptance and credential approval remain distinct from exact-action security approval.

Carry tenant/principal/delegation/task/run/action identifiers, policy revision, exact request digest, expiry and decision/receipt references through authenticated adapters. Treat client-supplied identity and trace fields as untrusted until bound by the trusted host. Keep secrets and raw sensitive payloads out of default logs, prompts and project memory. Distinguish allow/deny from executed/failed/unknown and from independent verification.

Protected mode stops on missing authority or unavailable required controls; it cannot silently invoke an unprotected path. Retries need idempotency or reconciliation. Revocation of future access does not undo completed work or erase credentials already delivered. Record actual transport, version and bypass coverage before describing an integration as supported.

## Investment and success

Prioritize a supported, reusable protected workflow over feature breadth. Measure integration effort, correctly completed work, denied unauthorized operations, evidence completeness and ongoing maintenance. This component's role does not create a new license, transfer IP or approve a pricing/partnership claim.
