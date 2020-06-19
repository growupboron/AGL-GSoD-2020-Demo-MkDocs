---
edit_link: ''
title: Introduction
origin_url: >-
  https://raw.githubusercontent.com/automotive-grade-linux/docs-sources/halibut/docs/security-blueprint/part-2/0_Abstract.md
---

<!-- WARNING: This file is generated by fetch_docs.js using /home/boron/Documents/AGL/docs-webtemplate/site/_data/tocs/architecture/halibut/security_blueprint-security-blueprint-book.yml -->

# Part 2 - Secure boot

## Abstract

<!-- section-todo -->

Domain          | Improvement
--------------- | ----------------------------------------------------
Boot-Abstract-1 | More generic and add examples (The chain of trust).

<!-- end-section-todo -->

Secure boot refers to preventing malicious software applications and
“unauthorized” operating systems from loading during the system start-up process.
The goal is to protect users from rootkits and other low-level malware attacks.
Modern bootloaders come with features that can be used to enable secure boot in the system.

**Boot Hardening**: Steps/requirements to configure the boot sequence, in order
to restrict the device from executing anything other than the approved software
image.

In this part, we will see a series of settings that will allow us to improve
security during boot phase. For the purposes of reference and explanation, we
are providing guidance on how to configure an embedded device that runs with a
3.10.17 Linux kernel. If the integrity is not checked or if a critical error
occurs, the system must boot on a very stable backup image.

**Requirements**: These requirements must be met even if an alternative version
of the Linux kernel is chosen.

**Recommendations**: Detailed best practices that should be applied in order to
secure a device. Although they are not currently listed as hard requirements,
they may be upgraded to requirements status in the future. In addition, specific
operators may change some of these recommendations into requirements based on
their specific needs and objectives.

<!-- section-todo -->

Domain          | Improvement
--------------- | -------------------------------------------
Boot-Abstract-1 | Review the definition of the "boot loader".

<!-- end-section-todo -->

**Boot loader**: The boot loader consists of the Primary boot loader residing
in **OTP** memory, sboot, U-Boot and Secure loader residing in external flash
(NAND or SPI/NOR flash memory). The CPU on power on or reset executes the
primary boot loader. The **OTP** primary boot loader makes the necessary initial
system configuration and then loads the secondary boot loader sboot from
external flash memory to ram memory. The sboot then loads the U-Boot along with
the Secure loader. U-Boot then verifies the Kernel/system image integrity, then
loads the Kernel/system image before passing control to it.

--------------------------------------------------------------------------------

## Acronyms and Abbreviations

The following table lists the terms utilized within this part of the document.

Acronyms or Abbreviations | Description
------------------------- | -----------------------------------------------------------------------
_FUSE_                    | **F**ilesystem in **U**ser**S**pac**E**
_OTP_                     | **O**ne-**T**ime-**P**rogrammable
_DOCSIS_                  | **D**ata **O**ver **C**able **S**ervice **I**nterface **S**pecification