---
tags:
- security
- packagers
- release
title: 'Mandatory Upgrade: Quassel 0.9.1'
---
<strong>TL;DR: If you're running Quassel Core or the stand-alone, monolithic client with Qt 4.8.5+ and PostgreSQL, you need to upgrade immediately!</strong>

Looks like Qt changed the string escaping rules in their PostgreSQL driver for Qt 4.8.5, which unfortunately may cause database corruption or data loss if you're running Quassel Core or the monolithic client with a PostgreSQL database and that Qt version. Older versions of Qt are safe, as are the pre-built packages for Windows, MacOSX and the static core from our website. All other users (and distros!) should upgrade their core or monolithic build to the <a href="https://github.com/quassel/quassel/archive/0.9.1.tar.gz">brand-new 0.9.1 version of Quassel</a> immediately. Thanks in particular to Tucos and brot for finding that issue and its cause!

In addition to the fix for this issue, a number of other fixes went into this release, most notably several ones related to key handling for encrypted channels. Also, you should now see Quassel come up in your preferred UI language on MacOSX again (rather than in Japanese).

Note that because of the urgent nature of this release, we couldn't wait with the announcement until binary packages for 0.9.1 have been provided. Those will be added in the next few days.

That's it for now. Over and out.\
~ Sput
