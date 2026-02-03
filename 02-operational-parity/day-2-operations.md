# Day-2 Operations: Operational Parity Between VMware and OpenShift Virtualization

## Purpose

This document focuses on **Day-2 operations** — the activities that occur *after* a virtual machine is running.

Most platform decisions succeed or fail here.

The goal of this document is to demonstrate that OpenShift Virtualization supports the same operational responsibilities VMware administrators already manage today, using different tools and interfaces but similar discipline.

This is not about innovation.
It is about continuity.

---

## What “Day-2” Means in Practice

Day-2 operations include:
- Monitoring and alerting
- Backup and recovery
- Patch and lifecycle management
- Capacity planning
- Failure response
- Access control and auditability

If these concerns are not addressed, platforms do not survive first contact with production.

---

## Monitoring & Visibility

### VMware Model
- vCenter metrics
- Host and VM performance views
- External tools (vRealize, plugins)
- Alert-driven troubleshooting

### OpenShift Virtualization Model
- Cluster-wide metrics via Prometheus
- VM, node, and storage metrics integrated
- Grafana dashboards (built-in and extensible)
- Alertmanager for notifications

**Operational Reality:**  
You still:
- Watch CPU, memory, disk, and network
- Respond to alerts
- Troubleshoot degraded performance

The difference is **integration**, not responsibility.

---

## Logging & Troubleshooting

### VMware
- vCenter events
- Host logs
- Guest OS logs
- Centralized log tools

### OpenShift Virtualization
- Cluster logging stack
- Node, VM, and operator logs
- Namespaced log isolation
- Centralized collection and retention

Logs are:
- More accessible
- More queryable
- More auditable

Troubleshooting remains a skill, not a feature.

---

## Backup & Recovery

### VMware
- Snapshot-based workflows
- Third-party backup tools
- VM-level restore
- Storage-dependent recovery patterns

### OpenShift Virtualization
- CSI-based snapshots
- Backup operators and ecosystem tools
- VM-level restore supported
- Declarative recovery workflows

**Key Parity Point:**  
Backup remains **tool-driven**.

The platform provides primitives — not assumptions.

---

## Patch & Lifecycle Management

### VMware
- ESXi patch cycles
- Host maintenance windows
- vCenter upgrades
- Manual coordination

### OpenShift Virtualization
- Node-based lifecycle
- Operator-managed updates
- Rolling upgrades
- Controlled disruption budgets

Maintenance still exists.
Change control still matters.
Downtime planning still applies.

Automation increases consistency — not risk.

---

## Capacity Planning

### VMware
- Host resource tracking
- Overcommit ratios
- Cluster capacity views
- Forecast-based planning

### OpenShift Virtualization
- Node resource metrics
- Quotas and limits
- Scheduler visibility
- API-driven reporting

Capacity planning remains:
- Predictive
- Conservative
- Human-led

Nothing becomes “set and forget.”

---

## Failure Domains & Recovery

### Host Failure

- **VMware:** HA restarts VMs
- **OpenShift:** Controllers restart VMs

Same outcome.
Different mechanism.

---

### Node Maintenance

- **VMware:** Maintenance mode
- **OpenShift:** Cordon and drain

Workloads are moved intentionally.
Disruption is managed, not avoided.

---

## Access Control & Auditability

### VMware
- vCenter RBAC
- Role-based permissions
- Event logs

### OpenShift Virtualization
- Kubernetes RBAC
- Namespaced access
- API audit logs

Access becomes:
- More granular
- More explicit
- More traceable

This is particularly important in regulated environments.

---

## Change Management & Governance

Day-2 success depends on **process**, not tooling.

OpenShift Virtualization supports:
- Git-based change tracking
- Declarative configuration review
- Peer approval workflows
- Automated drift detection

This strengthens governance rather than weakening it.

---

## What Does *Not* Change

- Someone is still on-call
- Incidents still happen
- Root cause analysis still matters
- Documentation still saves time
- Humans still own outcomes

Platforms do not remove accountability.
They expose it more clearly.

---

## Common Day-2 Concerns (Addressed)

- “Is this harder to operate?”  
  → No. It is different, not harder.

- “Do I need Kubernetes experts?”  
  → Not to run VMs. Familiar skills transfer.

- “Is this less stable?”  
  → Stability depends on operations, not branding.

- “Can we run this alongside VMware?”  
  → Yes. Phased coexistence is normal.

---

## Key Takeaways

- Day-2 operations remain the critical success factor
- OpenShift Virtualization supports operational parity
- Discipline matters more than tooling
- Confidence comes from observability and control

If you can operate VMware in production, you can operate OpenShift Virtualization.

---

## Next Steps

Recommended follow-on documents:
- `backup-and-dr.md`
- `networking-and-storage.md`
- `03-migration-exercises/lab-01-assess-vmware.md`

Understanding operations comes before migration.
This document exists to reinforce that order.
