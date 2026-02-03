# Lab 01: Assess a VMware Virtual Machine

## Purpose

This lab focuses on **assessment, not migration**.

Before any virtual machine is moved, cloned, or powered on in a new platform, it must be understood. This lab guides you through evaluating an existing VMware virtual machine to determine its suitability for migration to OpenShift Virtualization.

No changes will be made to the source environment.

---

## Lab Goals

By the end of this lab, you will be able to:
- Identify candidate virtual machines for migration
- Understand resource, network, and storage dependencies
- Document operational requirements
- Decide whether a VM should migrate, wait, or remain where it is

This lab produces **confidence**, not action.

---

## Scope & Safety

- Read-only assessment
- No configuration changes
- No downtime
- No tools required beyond existing VMware access

If you can view a VM in vCenter, you can complete this lab.

---

## Prerequisites

- Access to vCenter (read-only is sufficient)
- Basic familiarity with the VM’s purpose
- Willingness to document what you find

---

## Step 1: Identify a Candidate VM

Select a VM that meets the following criteria:
- Non-production or low-risk
- Single-purpose workload
- Minimal external dependencies
- Known owner or team

Avoid:
- Domain controllers
- Clustered databases
- Latency-sensitive workloads
- VMs with unclear ownership

This lab is about learning, not bravery.

---

## Step 2: Capture Basic VM Details

Document the following:

- VM name
- Operating system and version
- CPU count
- Memory allocation
- Disk count and sizes
- Power state
- VMware tools status

These details map directly to OpenShift Virtualization definitions.

---

## Step 3: Assess Resource Usage

Review historical performance:
- CPU utilization
- Memory consumption
- Disk I/O patterns
- Network throughput

Look for:
- Consistent usage patterns
- Over-provisioning
- Idle capacity

Migration is a good opportunity to right-size safely.

---

## Step 4: Identify Storage Dependencies

For each disk:
- Datastore location
- Provisioning type (thin/thick)
- Snapshot usage
- Backup inclusion

Questions to answer:
- Is storage performance critical?
- Are snapshots used operationally?
- Is the VM part of a backup job?

Storage choices will matter later.

---

## Step 5: Identify Network Dependencies

Document:
- Network(s) attached
- VLAN or port group
- Static or DHCP addressing
- DNS dependencies
- Firewall rules (if known)

Pay attention to:
- Hardcoded IPs
- External firewall dependencies
- Assumed network proximity

Networking assumptions often hide here.

---

## Step 6: Review Availability & Recovery Expectations

Answer:
- Is the VM expected to auto-restart on failure?
- Is live migration used?
- Is downtime acceptable?
- What is the expected RTO/RPO?

These expectations guide platform configuration — not the other way around.

---

## Step 7: Review OS & Application Constraints

Check for:
- Unsupported or end-of-life OS versions
- Special kernel modules
- Hardware passthrough
- Licensing tied to hardware identifiers

These do not block migration — they inform planning.

---

## Step 8: A
