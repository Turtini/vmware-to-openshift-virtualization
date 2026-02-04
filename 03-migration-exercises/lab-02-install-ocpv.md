# Lab 02: Prepare an OpenShift Virtualization Environment

## Purpose

This lab focuses on **preparing the destination environment** for migration by installing and validating OpenShift Virtualization.

No VMware systems are touched.
No workloads are moved.
No commitments are made.

The goal is to create a safe, observable environment where virtual machines *could* run — not to move anything yet.

---

## Lab Goals

By the end of this lab, you will:
- Understand where OpenShift Virtualization fits into an OpenShift cluster
- Install OpenShift Virtualization using supported operators
- Verify that the platform is ready to host virtual machines
- Gain familiarity with the OpenShift console and VM concepts

This lab builds **environmental confidence**, not migration momentum.

---

## Scope & Safety

- No impact to VMware environments
- No VM creation required
- No application downtime
- Reversible configuration changes only

If this environment is later discarded, nothing is lost.

---

## Prerequisites

- Access to an OpenShift cluster (lab, sandbox, or non-production)
- Cluster-admin or equivalent permissions
- Basic familiarity with the OpenShift web console

This lab does **not** require Kubernetes expertise.

---

## Step 1: Confirm Cluster Readiness

Before installing OpenShift Virtualization, confirm:

- Cluster is healthy
- All nodes are in `Ready` state
- Sufficient resources are available (CPU, memory, storage)
- StorageClasses are configured
- Networking is functional

If the cluster is not healthy, stop here.
Platform stability comes first.

---

## Step 2: Review Node Capabilities

OpenShift Virtualization requires:
- Hardware virtualization support (VT-x / AMD-V)
- Worker nodes capable of running VMs

Confirm:
- Nodes expose virtualization extensions
- You understand which nodes may host VMs
- Resource contention is acceptable for a lab environment

This mirrors host readiness checks in VMware.

---

## Step 3: Install the OpenShift Virtualization Operator

Using the OpenShift console:

1. Navigate to **Operators → OperatorHub**
2. Search for **OpenShift Virtualization**
3. Select the Red Hat–supported operator
4. Install using default settings

Installation is declarative and reversible.

No workloads are impacted.

---

## Step 4: Verify Operator Installation

Confirm:
- Operator status is `Succeeded`
- Required components are running
- No errors are present

This step replaces:
- Hypervisor enablement
- vCenter service validation

Same intent, different interface.

---

## Step 5: Enable OpenShift Virtualization

After installation:
- Navigate to the OpenShift Virtualization section
- Complete any required enablement steps
- Allow the platform to reconcile

Watch for:
- New controllers becoming ready
- VM-related resources appearing in the console

This is expected and observable.

---

## Step 6: Review Virtualization Resources

Explore (do not change yet):
- VirtualMachine objects
- Templates
- Storage options
- Network options

Notice:
- Familiar concepts expressed differently
- VM lifecycle controls
- Resource visibility

No action is required in this step.

---

## Step 7: Validate Storage Availability

Confirm:
- A default StorageClass exists
- PVCs can be created
- Snapshot support is available (if applicable)

VMs depend on storage.
This validation matters more than VM creation.

---

## Step 8: Validate Networking Availability

Confirm:
- Default pod networking is functional
- Secondary networks (if any) are visible
- You understand where VM traffic would flow

This mirrors validating port groups and VLANs before VM placement.

---

## Step 9: Pause and Reflect

At this point:
- No VMs have been created
- No data has moved
- No decisions have been forced

But you now know:
- Where VMs would live
- How they would be managed
- What the operational surface looks like

This is progress.

---

## Deliverables

By the end of this lab, you should have:
- An OpenShift cluster with Virtualization enabled
- Confidence that the platform is ready for VMs
- No changes to your existing virtualization environment

If something feels unclear, stop here.
That is the correct response.

---

## Key Takeaways

- Preparing the destination reduces migration anxiety
- Installation is controlled and observable
- Familiar concepts are present under new names
- Nothing irreversible has happened

This lab exists to build trust in the platform.

---

## Next Lab

When you are ready:
- `lab-03-migrate-single-vm.md`

That lab moves **one** VM, intentionally and safely.

There is no rush.
