# Terminology Translation: VMware to OpenShift Virtualization

## Purpose

This document provides a plain-language translation between common VMware terminology and the equivalent concepts used in OpenShift Virtualization.

It is written for practitioners who already understand virtualization deeply and want a fast, accurate mental mapping — without learning an entirely new vocabulary upfront.

If you know VMware, you already know most of this.
You just need a translation layer.

---

## Why Terminology Matters

Most migration anxiety is not technical — it is linguistic.

When familiar concepts are renamed, it can feel like:
- Old skills no longer apply
- Proven practices are being replaced
- Operational certainty is being removed

In reality, most concepts remain the same.  
They are expressed through a different control plane.

---

## Core Terminology Mapping

| VMware Term | OpenShift Virtualization Term | What Actually Changed |
|------------|------------------------------|------------------------|
| Virtual Machine | VirtualMachine | Name and API representation |
| Host | Node | Scheduling and lifecycle control |
| Cluster | Cluster | Same concept, broader scope |
| Hypervisor | KVM | Implementation detail |
| vCenter | OpenShift API | Declarative control plane |
| Datastore | StorageClass | Policy abstraction |
| Network | NetworkAttachmentDefinition | Explicit intent |
| Template | Template | Same goal, same outcome |

---

## Control Plane Language

| VMware Language | OpenShift Language | Meaning |
|----------------|-------------------|--------|
| Configure | Declare | Desired state |
| Click to apply | Define and apply | API-driven |
| Imperative action | Declarative intent | System reconciles |
| Manual remediation | Automated reconciliation | Controller-driven |
| GUI-first | API-first | UI reflects state |

This is the single biggest shift in mindset — and it does **not** remove control.

It changes *how* control is expressed.

---

## Operational Concepts (Translated)

### “Where does my VM run?”
- **VMware:** DRS decides placement
- **OpenShift:** Scheduler decides placement

Same question. Same answer. Different mechanism.

---

### “What happens if a host fails?”
- **VMware:** HA restarts the VM
- **OpenShift:** Controllers restart the VM

Outcome is the same: workload recovery.

---

### “How do I keep workloads separated?”
- **VMware:** Resource pools and folders
- **OpenShift:** Namespaces and quotas

OpenShift enforces separation more explicitly — not less.

---

### “How do I move workloads safely?”
- **VMware:** vMotion
- **OpenShift:** Live migration

Live migration exists. It is supported. It is observable.

---

## Storage Language (Translated)

| VMware Phrase | OpenShift Phrase | Meaning |
|--------------|------------------|--------|
| Attach disk | Bind PVC | Same lifecycle |
| Thin disk | Thin PVC | Storage-backed |
| Storage policy | StorageClass | Policy-driven |
| Snapshot | VolumeSnapshot | CSI-based |
| Backup job | Backup workflow | Tool-driven |

If you understand storage today, you still do.

---

## Networking Language (Translated)

| VMware | OpenShift | Notes |
|------|----------|------|
| Port group | Network attachment | Explicit definition |
| VLAN | Secondary network | Same L2/L3 concerns |
| vSwitch | SDN | Software-defined |
| Firewall rule | NetworkPolicy | Declarative |
| Load balancer | Service / Route | Integrated |

Networking remains networking.
Design discipline still matters.

---

## Security & Access (Translated)

| VMware | OpenShift | Difference |
|------|----------|-----------|
| vCenter RBAC | Kubernetes RBAC | More granular |
| Host isolation | Node isolation | Same boundary |
| Audit events | API audit logs | Stronger traceability |
| Compliance tooling | Policy engines | Code-based |

Nothing becomes *less* secure by default.
Many things become more observable.

---

## Mental Model Reset (The Important Part)

If you remember nothing else:

- A **VirtualMachine** is still a virtual machine
- A **Node** is still a host
- A **Cluster** still fails the same way
- Storage still fills up
- Networking still breaks if misconfigured
- Someone is still on-call

What changes is **how intent is expressed and enforced** — not responsibility.

---

## Common Translation Mistakes

- Assuming containers are required (they are not)
- Treating OpenShift Virtualization as “VMs on Kubernetes” instead of “VMs *managed by* Kubernetes”
- Expecting vCenter-style workflows instead of API-driven ones
- Ignoring Day-2 operations until after migration

This repository exists to prevent those mistakes.

---

## Next Steps

Recommended reading:
- `day-2-operations.md`
- `04-common-fears-and-myths.md`
- `03-migration-exercises/lab-01-assess-vmware.md`

Once the language feels familiar, everything else becomes easier.
