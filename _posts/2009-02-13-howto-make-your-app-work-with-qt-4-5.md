---
tags: []
title: HOWTO make your app work with Qt 4.5
---
With Qt 4.5-rc1 recently released, we've stumbled over a strange issue with Quassel. A binary compiled against Qt 4.4 would completely freeze when used with Qt 4.5. This problem mostly hit users on binary distros trying out Qt 4.5. As it turned out, recompiling Quassel against Qt 4.5 magically fixed the problem - but of course, this is not an option for distro packagers, as they will have to provide packages built against 4.4 at least until 4.5 hits their distros proper.

So we hunted for that bug, to no avail at first, but then EgS <strike>stumbled over</strike> dug into the strange dungeons of his memory, and there found lurking a <a href="http://labs.trolltech.com/blogs/2008/11/04/910/">blog entry</a> by one of the Trolls:

<cite>
Well if you leave the code as it is then you will either get a crash in your code or it will simply cause the application to hang because the QRegExp object passed into QString::indexOf() is no longer modified. The good news is that there is a solution which you can use now even if you are not switching to Qt 4.5 straight away. What you should do is change the calls from QString::indexOf() to QRegExp::indexIn().
</cite>

We found one location in our code where we did this, and <a href="http://git.quassel-irc.org/?p=quassel.git;a=commit;h=7d7c70c5c27be65af2d53df5cca27265c2d1d666">changed that</a>:
<code>
-        matches[i] = str.indexOf(regExp[i], qMax(matchEnd[i], idx));
+        matches[i] = regExp[i].indexIn(str, qMax(matchEnd[i], idx));
</code>

This seems to fix the issue, and Quassel binaries built against Qt 4.4 now reportedly work with 4.5.

What I don't get: I can see how "not modifying the QRegExp object" causes our code to hang here, and why the above makes it work again. But why the fringle does a mere <em>recompile</em> against Qt 4.5 fix that issue as well? Does the regexp magically become modifiable again? Luck? Karma? Voodoo? Anybody can help me out there? ;-)
<!--break-->
