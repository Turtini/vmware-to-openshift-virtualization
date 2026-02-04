# Lab 04: Validate and Roll Back a Migrated Virtual Machine

## Purpose

This lab focuses on **validation discipline and rollback confidence** after a virtual machine has been migrated to OpenShift Virtualization.

Migration is not complete when a VM boots.
Migration is complete when you know — with evidence — that you can:
- Run the VM successfully, and
- Reverse the decision safely

Rollback is not failure.
Rollback is control.

---

## Lab Goals

By the end of this lab, you will:
- Perform structured validation of a migrated VM
- Confirm operational readiness
- Execute (or explicitly decline) rollback
- Document findings for future migrations

This lab turns a test into a repeatable practice.

---

## Scope & Safety

- One migrated VM
- No forced production cutover
- Rollback remains fully available
- No impact to other workloads

Nothing in this lab removes optionality.

---

## Prerequisites

- Completed `lab-03-migrate-single-vm.md`
- A migrated VM in OpenShift Virtualization
- Source VM still available in VMware
- Documented expectations from Lab 01

Do not proceed if rollback is not possible.

---

## Step 1: Establish Validation Criteria

Before testing, define success.

Document:
- Expected VM behavior
- Required services
- Network reachability
- Performance expectations (baseline)

Validation without criteria is just observation.

---

## Step 2: Validate VM Power and Access

Confirm:
- VM powers on reliably
- Console access works
- Guest OS boots cleanly
- No unexpected errors appear

This replaces “it booted once” with “it boots consistently.”

---

## Step 3: Validate Networking

Verify:
- IP address assignment
- DNS resolution
- Required inbound connectivity
- Required outbound connectivity

Networking issues are the most common migration failures.
Take your time here.

---

## Step 4: Validate Storage and Data Integrity

Confirm:
- All disks are present
- Filesystems mount correctly
- Application data is intact
- Read/write behavior is normal

If data looks wrong, stop.
Rollback exists for a reason.

---

## Step 5: Validate Application Behavior

If applicable:
- Start application services
- Perform basic functional checks
- Review application logs
- Confirm expected responses

You are validating *behavior*, not performance tuning.

---

## Step 6: Observe Platform Behavior

While the VM is running:
- Observe metrics
- Watch logs
- Note alert behavior
- Confirm visibility meets expectations

This is where Day-2 confidence is earned.

---

## Step 7: Decide: Keep, Pause, or Roll Back

Make an explicit decision:

### Option A: Keep the Migrated VM
- Validation criteria met
- No blocking issues
- Comfortable proceeding

### Option B: Pause
- VM works, but concerns remain
- More observation needed
- No pressure to decide today

### Option C: Roll Back
- Issues identified
- Confidence not sufficient
- Decision deferred intentionally

All three outcomes are valid.

---

## Step 8: Execute Rollback (If Chosen)

Rollback steps:
- Power down the migrated VM
- Leave or delete migrated resources
- Power on the source VMware VM
- Confirm normal operation

Rollback should feel controlled — not frantic.

---

## Step 9: Document Findings

Document:
- What worked
- What surprised you
- What slowed you down
- What you would change next time

This documentation is the real output of the lab.

---

## Deliverables

At the end of this lab, you should have:
- A validated VM (or a clean rollback)
- A documented outcome
- Increased confidence in the process
- A repeatable migration pattern

This is success.

---

## Key Takeaways

- Validation is an operational skill
- Rollback is part of design, not a failure state
- Confidence comes from reversibility
- One VM teaches more than a plan

If rollback felt calm, the platform did its job.

---

## What Comes Next

At this point, you can:
- Repeat Labs 01–04 for another VM
- Begin grouping similar workloads
- Socialize findings with your team
- Decide whether to scale migration

There is no mandate to move faster.

Control is the outcome.
