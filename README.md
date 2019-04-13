# Introduction

This project's goals are to provide a framework, compatible with the format
described in [rcorder(8)](https://www.freebsd.org/cgi/man.cgi?rcorder(8)), which
will allow FreeBSD to do move beyond serial booting to permit parallel booting.

The initial proof-of-concept will be written in a format usable with python 3.7,
but will be reworked/rewritten in modern (C++14+) C++, so it can be added to
the FreeBSD base system.

# Problem Statement

Many contemporary operating systems permit parallel booting, which is a boon
for multi-processor enabled machines. Examples: launchd on Mac OSX, systemd on
Linux, or SMF on Solaris.

FreeBSD however, is using the RC-ng framework from NetBSD, which was originally
imported back in the FreeBSD 5.x release era, almost 2 decades ago, and only
supports serial booting via
[rc(8)](https://www.freebsd.org/cgi/man.cgi?query=rc&sektion=8).

While this rc(8) can be optimized to run quickly, long-running processes that
rely on system events, e.g., dhclient(8), block system boot until it has
received a DHCP ticket. Long-running/slow services like this in aggregate can
become a hinderance for boot progress.
