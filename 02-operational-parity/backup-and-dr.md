# Backup and Disaster Recovery: VMware and OpenShift Virtualization

## Purpose

This document explains how **backup and disaster recovery (DR)** responsibilities translate from VMware environments to OpenShift Virtualization.

Backup and DR are not features — they are operational disciplines.
This document focuses on parity, not promises.

The goal is to show that OpenShift Virtualization supports the same recovery outcomes VMware administrators expect today, using different primitives and tooling.

---

## Shared Truths (Before Comparing)

Regardless of platform:

- Backups must be tested
- Snapshots are not backups by themselves
- Recovery objectives (RPO/RTO) must be defined
- DR complexity scales with environment complexity
- Tooling does not replace process

These truths do not change with OpenShift Virtualization.

---

## Snapshot Capabilities

### VMware

- VM-level snapshots
- Storage-backed
- Commonly used for short-term protection
- Often integrated into backup tools

### OpenShift Virtualization

- VolumeSnapshots (CSI-based)
- VM snapshots supported
- Storage-provider dependent
- API-driven and declarative

**Parity Point:**  
Snapshots exist in both platforms and serve the same purpose — short-term recovery and backup integration.

---

## Backup Tooling Model

### VMware

- Vendor backup platforms
- Agentless VM backups
- Image-level recovery
- Storage-integrated workflows

### OpenShift Virtualization

- Operator-based backup tools
- CSI-integrated snapshots
- VM-level and disk-level restore
- Ecosystem-driven solutions

**Important Difference:**  
OpenShift provides **primitives**, not a single mandated backup product.

This mirrors modern infrastructure practice, not a loss of capability.

---

## Recovery Scenarios (Mapped)

| Scenario | VMware Approach | OpenShift Virtualization Approach |
|--------|-----------------|----------------------------------|
| Single VM restore | Backup tool | Backup operator |
| Disk-level restore | Storage tools | CSI snapshot restore |
| Point-in-time recovery | Snapshot + backup | Snapshot + backup |
| Application-level restore | Guest tools | Guest tools |
| Site failure | DR orchestration | DR orchestration |

The recovery goals remain the same.

---

## Disaster Recovery Patterns

### VMware

- Secondary site
- Replicated storage
- SRM or vendor tooling
- Manual or automated failover

### OpenShift Virtualization

- Secondary cluster
- Replicated storage
- Operator-driven workflows
- Declarative failover

**Key Insight:**  
DR is still a **design decision**, not a checkbox.

---

## RPO and RTO Considerations

| Factor | VMware | OpenShift Virtualization |
|------|--------|--------------------------|
| RPO | Tool & storage dependent | Tool & storage dependent |
| RTO | Automation maturity | Automation maturity |
| Testing | Often manual | API-driven testing |
| Documentation | Runbooks | Runbooks + manifests |

Recovery targets depend more on **planning** than platform.

---

## Testing & Validation

### VMware
- Scheduled DR tests
- Snapshot validation
- Manual failover drills

### OpenShift Virtualization
- Declarative test environments
- Repeatable restore workflows
- Non-disruptive testing patterns

Testing remains mandatory.
OpenShift improves repeatability.

---

## What Changes (and What Does Not)

### What Does Not Change
- Backup ownership
- Compliance responsibility
- Audit expectations
- Recovery accountability

### What Changes
- Backup workflows become API-driven
- Infrastructure definitions can be versioned
- Recovery steps can be documented as code

This increases confidence over time — not risk.

---

## Common Backup & DR Concerns

- “Are snapshots reliable?”  
  → As reliable as the storage backing them.

- “Do we lose vendor support?”  
  → Support shifts to ecosystem partners.

- “Is DR harder?”  
  → No. It is more explicit.

- “Can we meet compliance requirements?”  
  → Yes, with documented processes.

---

## Key Takeaways

- Backup and DR parity exists
- OpenShift Virtualization provides modern primitives
- Tool choice remains intentional
- Process still determines success

If you trust your backup discipline today, you can trust it tomorrow.

---

## Next Steps

Recommended follow-on documents:
- `networking-and-storage.md`
- `03-migration-exercises/lab-01-assess-vmware.md`

Backup confidence enables migration confidence.
This document exists to reinforce that relationship.
