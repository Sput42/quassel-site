---
tags: []
title: Nightly Snapshots
---
We now provide nightly <a href="/nightly/source">source tarballs</a>, as well as a <a href="/nightly/linux">statically linked core</a> for Linux, MacOSX <a href="/nightly/macosx">client binaries</a> and <a href="/nightly/windows">Windows binaries</a>. Please be aware of the fact that these binaries are generated automatically from current SVN HEAD, which means they might be in an untested and/or non-working state. We do not recommend using them until you know what you're doing, but since people kept asking for them, well, <a href="/nightly">here</a> they are :)

Please note that we still tweak and break the core/client protocol on a regular basis. This means that your client sometimes will require a certain core revision and the other way round. For example, the current nightly clients do not run with alpha4 cores. Both client and core will warn in this case, but you should be aware of that fact anyway (especially since downgrades of config files or the database are usually not possible, so using a client or core that is "too new" might require you to upgrade the other component as well! You'll find even more disclaimers on the <a href="/downloads">download page.</a>
