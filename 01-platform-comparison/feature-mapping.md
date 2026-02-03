# Feature Mapping: VMware to OpenShift Virtualization

## Purpose

This document provides a practical, side-by-side mapping of common VMware concepts, features, and operational patterns to their equivalents in OpenShift Virtualization.

It is intended to help VMware practitioners quickly orient themselves, understand functional parity, and identify where operational models are similar — and where they differ.

This is not a value judgment. It is a translation.

---

## High-Level Platform Comparison

| Area | VMware | OpenShift Virtualization | Notes |
|-----|--------|--------------------------|------|
| Hypervisor | ESXi | KVM (via KubeVirt) | Enterprise-grade, widely used |
| Control Plane | vCenter | OpenShift API & Console | Declarative vs imperative |
| Compute Unit | Virtual Machine | VirtualMachine (CR) | Still a VM |
| Cluster | vSphere Cluster | OpenShift Cluster | Similar failure domain thinking |
| Management UI | vSphere Client | OpenShift Console | Web-based, role-aware |
| Automation | PowerCLI | kubectl / oc / YAML | API-first |
| Licensing | Per-socket / core | Subscription-based | Model differs, outcome similar |

---

## Compute & VM Lifecycle

| VMware Concept | OpenShift Virtualization Equivalent | Notes |
|---------------|------------------------------------|------|
| Virtual Machine | VirtualMachine (KubeVirt) | Same lifecycle concepts |
| VM Template | VM Template | Reusable, standardized builds |
| Clone VM | VM Clone | Supported via templates |
| Power On / Off | Start / Stop VM | Declarative state |
| Suspend / Resume | Not primary pattern | Use snapshots/checkpoints |
| VM Hardware | CPU / Memory spec | Defined in VM spec |
| Guest OS | Same | No OS change required |

---

## Availability & Scheduling

| VMware | OpenShift Virtualization | Notes |
|------|--------------------------|------|
| HA | Pod / VM restart policies | Automatic recovery |
| DRS | Scheduler & Affinity | Policy-driven placement |
| vMotion | Live Migration | Supported for VMs |
| Host Maintenance Mode | Node Cordon / Drain | Controlled workload movement |
| Resource Pools | Namespaces & Quotas | Stronger multi-tenancy |

---

## Storage

| VMware Concept | OpenShift Virtualization Equivalent | Notes |
|---------------|------------------------------------|------|
| Datastore | StorageClass | Abstracted storage |
| VMDK | PVC-backed disk | Portable, managed |
| Thin Provisioning | Thin PVCs | Storage-dependent |
| Storage Policies | StorageClass parameters | Policy-based |
| Snapshots | VolumeSnapshots | CSI-driven |
| Backup | Vendor tools | Ecosystem-driven |

---

## Networking

| VMware Concept | OpenShift Virtualization Equivalent | Notes |
|---------------|------------------------------------|------|
| vSwitch | OpenShift SDN / OVN-K | Software-defined |
| Port Group | NetworkAttachmentDefinition | Explicit network intent |
| VLAN-backed Network | Secondary network | Multus-based |
| VM NIC | VM Network Interface | Same abstraction |
| Load Balancing | OpenShift Services / Routes | Platform-integrated |
| Firewall Rules | NetworkPolicies | Declarative enforcement |

---

## Operations & Day-2

| VMware | OpenShift Virtualization | Notes |
|------|--------------------------|------|
| Monitoring | vRealize / Plugins | Prometheus & ecosystem |
| Logging | Log Insight | Cluster logging stack |
| Alerts | vCenter Alarms | Alertmanager |
| Patching | ESXi lifecycle | Node & operator lifecycle |
| Access Control | vCenter RBAC | Kubernetes RBAC |
| Audit Logs | vCenter events | API audit logs |

---

## Security & Governance

| VMware | OpenShift Virtualization | Notes |
|------|--------------------------|------|
| RBAC | Kubernetes RBAC | More granular |
| VM Isolation | Hypervisor-based | KVM isolation |
| Secure Boot | Supported | Platform-dependent |
| Compliance | Tool-driven | Policy-as-code capable |
| Encryption | Storage / vMotion | Storage & network layers |

---

## Key Takeaways

- Virtual machines remain first-class citizens
- Core operational concepts transfer directly
- Differences are primarily **control-plane driven**
- OpenShift emphasizes **declarative intent** over manual action
- Day-2 operations require different tools, not different discipline

If you understand VMware operations, you already understand most of OpenShift Virtualization.

---

## What This Mapping Does *Not* Cover

This document intentionally does not cover:
- Container-native application design
- Cloud-native refactoring
- Platform modernization strategies

Those topics are optional and separate from VM migration.

---

## Next Steps

Recommended follow-on reading:
- `terminology-translation.md`
- `day-2-operations.md`
- `03-migration-exercises/lab-01-assess-vmware.md`

Understanding comes before migration. This document exists to support that order.
