---
title: "The Uni Server Had Other Plans"
date: 2026-07-02 00:00:00 +0300
categories: [Security]
tags: [linux, privilege-escalation, copyfail, cve-2026-31431]
---

## From 2026, my plan

I thought 2026 was going to be calm.

Maybe travel.  
Maybe Florence.  
Maybe peace.

![From 2026, my plan](/assets/img/writeups/copyfail/lome_meme.png)

## But the Uni machine had other plans

During an authorized security assessment on a university lab server, I managed to escalate privileges to root using **Copy Fail**, tracked as **CVE-2026-31431**.

![God's plan root](/assets/img/writeups/copyfail/batman_sad_meme.jpg)

No sensitive data was accessed, copied, modified, or disclosed.  
The finding was handled responsibly and reported to the appropriate people.

## What is Copy Fail?

Copy Fail is a Linux kernel local privilege escalation vulnerability.

The official project page describes it as a small, reliable Linux LPE affecting major distributions:

[copy.fail](https://copy.fail/)

At a high level, the issue affects the Linux kernel crypto interface and can allow an unprivileged local user to gain root privileges on vulnerable systems.

## Proof of impact

After exploitation, the user context changed from a normal student account to root:

![Root proof](/assets/img/writeups/copyfail/UN1_S3RV3R_PWN3D.png)

## Impact

If an attacker already has local shell access on a vulnerable machine, Copy Fail can potentially allow full root compromise.

That means:

- full control of the affected host
- access to privileged files and services
- ability to modify system state
- possible pivoting risk depending on the environment

In this case, testing was authorized and limited in scope.

Final mood:

> 2026 plan: Florence.  
> Kernel plan: `uid=0`.