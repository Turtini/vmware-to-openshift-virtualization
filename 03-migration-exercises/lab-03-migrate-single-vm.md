# Lab 03: Migrate a Single Virtual Machine

## Purpose

This lab performs a **single, low-risk virtual machine migration** from VMware to OpenShift Virtualization.

It is intentionally anticlimactic.

The goal is not speed, scale, or optimization — it is to demonstrate that a VM can move safely, predictably, and observably using supported tooling.

Only one VM is migrated.
Nothing else changes.

---

## Lab Goals

By the end of this lab, you will:
- Migrate a single VMware VM to OpenShift Virtualization
- Observe the migration process end-to-end
- Validate the migrated VM without cutting over production
- Confirm that rollback remains possible

This lab builds **trust through completion**.

---

## Scope & Safety

- One VM
- Non-production or low-risk workload
- No mass migration
- No irreversible changes

If this lab feels boring, it is working.

---

## Prerequisites

- Completed `lab-01-assess-vmware.md`
- Completed `lab-02-install-ocpv.md`
- A selected VM classified as **Ready for migration**
- Access to both VMware and OpenShift environments
- Migration tooling available (e.g., Migration Toolkit for Virtualization)

Do not proceed if prerequisites are not met.

---

## Step 1: Reconfirm the Migration Candidate

Before proceeding, reconfirm:
- VM identity and purpose
- Owner approval
- Acceptable downtime (if any)
- Rollback plan

If anything feels uncertain, stop.
Pausing is success.

---

## Step 2: Prepare the Destination Environment

In OpenShift Virtualization:
- Confirm available resources
- Confirm storage class selection
- Confirm network mapping

Do not customize aggressively.
Defaults are acceptable for this lab.

---

## Step 3: Configure Migration Tooling

Using your migration tooling:
- Connect to the VMware source
- Authenticate read-only where possible
- Discover the selected VM

Verify:
- VM details match assessment
- Disks and networks are detected
- No unexpected dependencies appear

Discovery should match what you already documented.

---

## Step 4: Map Resources

Explicitly map:
- Source networks → destination networks
- Source storage → destination storage classes
- VM CPU and memory sizing

Avoid optimization.
Match the source intentionally.

---

## Step 5: Initiate the Migration

Start the migration process.

Observe:
- Data transfer progress
- Warnings or notices
- Resource utilization

Nothing else should be happening at the same time.
This is a controlled exercise.

---

## Step 6: Monitor the Migration

While the migration runs:
- Watch logs and status updates
- Note how failures are reported
- Observe where visibility is provided

This is about understanding the system,
not racing the clock.

---

## Step 7: Validate the Migrated VM (Without Cutover)

Once complete:
- Verify VM exists in OpenShift
- Confirm power state
- Inspect VM configuration

Do not shut down the source VM yet.

Validation includes:
- Boot success
- Console access
- Network presence
- Disk attachment

---

## Step 8: Perform Functional Validation

If appropriate:
- Log into the guest OS
- Verify basic services
- Confirm expected behavior

No users should be impacted.
This is still a test.

---

## Step 9: Decide on Cutover or Pause

At this point, you have options:
- Leave the VM powered off (test only)
- Perform a planned cutover
- Roll back and stop

All options are valid.

The success criteria is **understanding**, not production use.

---

## Rollback (Always Available)

Rollback means:
- Leaving the source VM untouched
- Powering down or deleting the migrated VM
- Documenting findings

Rollback is not failure.
It is part of the design.

---

## Deliverables

At the end of this lab, you should have:
- One migrated VM
- Observations about the process
- Confidence in tooling behavior
- A documented decision on next steps

Nothing more is required.

---

## Key Takeaways

- Migration can be controlled and observable
- One VM is enough to learn
- Nothing forces scale
- Anticlimactic is good

If this felt boring, the platform did its job.

---

## Next Lab

When ready:
- `lab-04-validate-and-rollback.md`

That lab focuses on validation discipline and rollback confidence —
the final ingredients before scaling responsibly.
