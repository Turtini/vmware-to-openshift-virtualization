# Migration Exercises

## Purpose

The labs in this directory provide a **safe, structured path** for evaluating and performing virtual machine migration from VMware to OpenShift Virtualization.

These exercises are intentionally:
- Small in scope
- Reversible by design
- Focused on learning, not speed

They are not a migration mandate.
They are a way to replace uncertainty with firsthand understanding.

---

## How These Labs Are Different

These labs are designed to:
- Give practitioners permission to slow down
- Allow learning without pressure or performance
- Support independent exploration before team decisions
- Build confidence through evidence, not assumptions

Nothing here assumes:
- Production cutover
- Organizational alignment
- Full platform commitment

You are always allowed to stop.

---

## Recommended Lab Flow

The labs are designed to be completed **in order**.

Each lab builds confidence without increasing risk.

### Lab 01: Assess a VMware Virtual Machine
**`lab-01-assess-vmware.md`**

- Read-only
- No changes
- No downtime

This lab focuses on understanding the source VM and its dependencies.
Many migration risks are discovered here — and that is success.

---

### Lab 02: Prepare an OpenShift Virtualization Environment
**`lab-02-install-ocpv.md`**

- Destination-only
- No VM creation required
- Fully reversible

This lab prepares the platform without touching VMware.
It builds environmental familiarity and trust.

---

### Lab 03: Migrate a Single Virtual Machine
**`lab-03-migrate-single-vm.md`**

- One VM
- Low-risk workload
- Controlled execution

This lab is intentionally anticlimactic.
The goal is to observe and understand the migration process — not to optimize or scale.

---

### Lab 04: Validate and Roll Back
**`lab-04-validate-and-rollback.md`**

- Structured validation
- Explicit decision-making
- Rollback always available

This lab proves that migration does not remove control.
Rollback is treated as a feature, not a failure.

---

## What Success Looks Like

Success does **not** mean:
- All VMs migrated
- Production cutover
- Faster timelines

Success means:
- Clear understanding
- Reduced fear
- Better questions in team discussions
- Informed decision-making

Completing a single lab — or stopping after one — is a valid outcome.

---

## Guidance for Team Leads

If you are sharing these labs with a team:
- Encourage private exploration
- Avoid status pressure
- Treat findings as input, not commitments
- Normalize “not ready yet” conclusions

Psychological safety improves technical outcomes.

---

## Guidance for Practitioners

If you are working through these labs on your own:
- Take notes
- Pause when something feels unclear
- Repeat labs if helpful
- Share only what you’re ready to share

Understanding compounds quietly.

---

## Key Principle

Migration should feel **boring before it feels bold**.

If these labs feel calm and controlled, they are working as intended.

---

## Where to Go Next

After completing these labs, you may choose to:
- Repeat the process for additional VMs
- Group workloads by similarity
- Share findings with leadership
- Decide not to migrate yet

All outcomes are valid.

Control is the goal.
