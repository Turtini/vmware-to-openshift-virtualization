# Networking and Storage: Operational Parity Between VMware and OpenShift Virtualization

## Purpose

This document explains how **networking and storage** concepts translate from VMware environments to OpenShift Virtualization.

These two areas are often the source of the most anxiety during platform transitions because they are:
- Deeply environment-specific
- Historically fragile
- Closely tied to performance and availability

The goal of this document is to demonstrate that the same design discipline applies — even though the implementation details differ.

---

## Shared Realities (Before Comparing)

Regardless of platform:
- Bad networking design causes outages
- Storage performance matters more than abstractions
- Latency is physics, not software
- Documentation prevents incidents

These truths remain unchanged.

---

## Networking Architecture Overview

### VMware Model
- vSwitches and distributed switches
- Port groups for network segmentation
- VLAN-backed isolation
- External firewalls and load balancers

### OpenShift Virtualization Model
- Software-defined networking (OVN-K)
- Primary and secondary networks
- Explicit network attachment definitions
- Integrated service exposure

The outcome is the same:
controlled connectivity and isolation.

---

## Network Segmentation & Isolation

| VMware Concept | OpenShift Virtualization Equivalent | Notes |
|---------------|------------------------------------|------|
| Port Group | NetworkAttachmentDefinition | Explicit intent |
| VLAN | Secondary network | Same L2/L3 constraints |
| vSwitch | OpenShift SDN | Centralized control |
| Firewall Rule | NetworkPolicy | Declarative enforcement |
| DMZ | Dedicated namespace/network | Stronger boundaries |

Network isolation is not removed.
It becomes more explicit.

---

## VM Networking (Day-2)

### VMware
- NIC attached to port group
- VLAN assigned at network layer
- Firewall enforced externally

### OpenShift Virtualization
- VM interface bound to network
- Network defined declaratively
- Policy enforced in-cluster and externally

Troubleshooting still involves:
- IP addressing
- Routing
- MTU mismatches
- DNS failures

No shortcuts are introduced.

---

## Load Balancing & Ingress

### VMware
- External load balancers
- Application-specific configuration
- Often manually integrated

### OpenShift Virtualization
- Platform-native Services and Routes
- External load balancers supported
- Declarative exposure patterns

**Key Point:**  
You are not forced to change how traffic enters your environment.
OpenShift supports existing patterns.

---

## Storage Architecture Overview

### VMware
- Centralized or distributed datastores
- VM disks (VMDK)
- Storage policies
- Vendor-specific integrations

### OpenShift Virtualization
- StorageClasses
- PersistentVolumeClaims (PVCs)
- CSI drivers
- Policy-driven provisioning

The abstraction changes.
The responsibility does not.

---

## Disk Lifecycle & Performance

| VMware | OpenShift Virtualization | Notes |
|------|--------------------------|------|
| VMDK | PVC-backed disk | Same intent |
| Thin provisioning | Thin PVC | Storage dependent |
| Storage policy | StorageClass | Explicit |
| IOPS limits | Storage configuration | Enforced at backend |
| Performance tuning | Storage tuning | Same discipline |

Performance problems are still solved at the storage layer.

---

## Data Protection & Mobility

### VMware
- Datastore replication
- Storage-based snapshots
- Vendor DR tooling

### OpenShift Virtualization
- CSI snapshots
- Storage replication
- Operator-driven workflows

Mobility improves through abstraction, not automation alone.

---

## Failure Domains

### Networking
- **VMware:** Switch, VLAN, firewall dependencies
- **OpenShift:** SDN, CNI, external network dependencies

Failures still occur at boundaries.
Visibility improves.

---

### Storage
- **VMware:** Datastore or array failures
- **OpenShift:** Storage backend or CSI failures

Designing for failure remains mandatory.

---

## Common Networking & Storage Concerns

- “Is SDN less reliable?”  
  → Reliability depends on design and operations.

- “Do we lose control?”  
  → Control becomes declarative, not hidden.

- “Is performance worse?”  
  → Performance depends on backend choices.

- “Is troubleshooting harder?”  
  → It is different, but often more observable.

---

## What Changes (Explicitly)

- Network intent is defined as configuration
- Storage behavior is declared via policy
- Infrastructure definitions can be versioned
- Drift is easier to detect

These changes support stability over time.

---

## What Does Not Change

- Networking still breaks first
- Storage still fills up
- Capacity planning still matters
- Humans still diagnose incidents

Platforms do not remove complexity.
They make it visible.

---

## Key Takeaways

- Networking and storage parity exists
- Design discipline remains essential
- Abstractions improve consistency
- Operational responsibility does not disappear

If you can design and operate VMware networking and storage,
you can do the same with OpenShift Virtualization.

---

## Next Steps

Recommended follow-on documents:
- `04-common-fears-and-myths.md`
- `03-migration-exercises/lab-01-assess-vmware.md`

Once networking and storage feel familiar,
migration becomes a controlled exercise instead of a leap of faith.
