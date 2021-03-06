---
tags:
- release
title: 'Bumping Quassel: 0.6.1'
---
It's that time of the year again, when we proudly do <a href="/downloads">new feature release</a> of Quassel IRC! You might wonder why we've skipped the announcement for 0.6.0, though. The reason for this is that shortly after tagging, we've discovered two serious bugs in that version. One could make the monolithic client try to select the PostgreSQL backend rather than SQlite; the other would lead to a crash on startup in some setups. Since we usually let some days pass between tagging and announcing a release, those bugs were found and fixed before we'd officially released 0.6.0. Two days later, we tagged 0.6.1.

There are several major features in this release:

<ul>
<li>Completely reworked client/core connection featuring the long-awaited reconnection and Solid support as well as a streamlined UI</li>
<li>Support for the new DBus-based system tray of KDE and, in some distros, Gnome (StatusNotifier spec)</li>
<li>Improved notification handling</li>
<li>Support for inputting formatted (colored/bold/...) text</li>
<li>SASL auth support (replaces NickServ e.g. in Freenode)</li>
<li>Several new languages and improved translations for alreay existing ones</li>
<li>Build system improvements</li>
</ul>

See the <a href="http://git.quassel-irc.org/?p=quassel.git;a=blob;f=ChangeLog;hb=refs/heads/0.6">ChangeLog</a> for a more exhausting list of new features. Of course, we've also fixed many bugs and optimized some things in this release ;-)

As usual, we'll maintain the 0.6.x branch in feature and string freeze at least until 0.7.0 is released. This means that we'll backport bugfixes where it makes sense, but don't introduce new stuff in 0.6.x versions, in order to make packagers of freeze-loving distros happy.

Now go and grab <a href="/downloads">this latest release</a> of your favorite IRC client!

~ Sputnick
