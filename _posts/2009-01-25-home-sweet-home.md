---
tags: []
title: "$HOME, sweet $HOME"
---
One of the more enduser-confusing issues with Quassel used to be its storage locations for settings and the backlog. The various platforms Quassel supports handle the storage of configuration much differently. Qt helps us there with abstracting this away, and giving us for example QSettings, which allows for the storage of configuration data in the platform's native format without having to bother about platform issues. In particular, this means that settings go into the XDG location on Linux (usually in $HOME/.config/<appname>), into .plist files on Mac, and into the Registry on Windows.

All nice and dandy, but what to do with data files, such as the sqlite storage? Well, Mac has a standard location for that, as does Windows (%APPDATA%). On Unixoids, such data traditionally goes into $HOME/.<appname>. And that's where the trouble started.
<!--break-->
First of all, on Linux (and other Unixoids, of course) we ended up with configuration data stored in two locations, $HOME/.config and $HOME/.quassel. Since users tend to expect the latter, they often only backup'd or transferred this, and never knew about the other location. Windows users, on the other hand, complained about Quassel polluting the Registry, making a config transfer to another box infeasible, and leaving traces on the machine even when running from a USB stick.

One of the most annoying issues in particular for distro packagers, however, was the need to have a writable $HOME directory. Many distributions like running daemons like quasselcore without a home directory (e.g. as user "nobody"), putting the global configuration into /etc or even /var. This could be workarounded, of course, by adding a special user with some home directory in one of these locations; but then, you'd end up e.g. with /etc/quassel/.quassel/Quassel Client.conf. Not pretty.

Now, a couple days ago, I have fixed this issue in git master. On Linux, Quassel will now store the configuration, the database and the core certificate in a common location. By default, this is using XDG, e.g. $HOME/.config/quassel-irc.org. It can be configured, however, by starting the binaries with --configdir=/any/path/you/like. Note that in any case, the ugly spaces in the file and folder names are gone.

On Windows, settings move out of the registry into .ini files in %APPDATA%/quassel-irc.org. On Mac, nothing changes for the time being, as the locations we used there always adhered to standards quite firmly entrenched on that platform.

To make the switch as seamlessly as possible, all files will be migrated automatically to their new location, if possible (i.e. if you didn't specify the now obsolete --datadir option before) as soon as you run a current Quassel for the first time. Note that the database file will be moved (not copied), but settings will be copied (i.e. the old version won't be touched). On Windows, the contents of the relevant registry keys is copied into the new .ini files.

If migration does not work, be sure to move all files into the locations described above yourself. The settings files are now called quasselclient.conf and quasselcore.conf (or .ini on Windows). The folder names changed from Quassel, Quassel Project and .quassel to quassel-irc.org, since this is the new pink now.

I hope that those changes will make life for some people a bit easier, and not annoy most other users :)
