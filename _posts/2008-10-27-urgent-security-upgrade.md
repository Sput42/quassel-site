---
tags: release
title: 'Urgent: Security Upgrade!'
---
Well, looks like 0.3.0.2 was not the last 0.3.0 release after all. coekie found an issue with CTCP handling in Quassel Core that allows attackers to send arbitrary IRC messages on your behalf. This issue is present in all versions prior to 0.3.0.3 and Git older than October 26th (rev. d7a0381).

This has been fixed in the <a href="/downloads">quassel-0.3.0.3</a> release and also in Git and the nightly builds. Gentoo and *buntu already ship the new version, with more distributions hopefully following ASAP. If you still use a 0.2-rc1 core, please consider updating to 0.3.x as soon as possible. Note that we provide <a href="/nightly/debian">unstable, but fixed packages</a> for Debian now, thanks to dileX.

Note that this affects (only) the core, so you'll need to update and restart your core. Clients are not affected. Also, this exploit can not be used to affect anything on your system, including your local account, as it is purely IRC related.

We are sorry for any inconvenience this causes to you, and hope this first will also be our last security fix for a long time to come...
