# Running a Ubuntu server on an old mac laptop

This document contains notes for setting up older mac laptops as
UI-less Ubuntu servers.

Some of the notes and utilities described were developed on old
Lenovo and Dell laptops, but I haven't tested them on any non-mac
hardware for a while, so I don't know if they still work.

## Intro

Older mac laptops that are no longer supported by Apple with current
versions of MacOS make LAMP good servers for light use.  The older
ones (the ones that still had Ethernet, actual USB-A connections,
and a DVD drive) are particularly useful.  As long as their battery
is still functional, they make good servers that can tolerate
momentary power loss.

In addition, console-only laptops can also be very useful for simple
hacking and writing, simply because they don't have a distracting
web browser or UI.  For programmers whose workflow is centered
around the commandline and vim or emacs, it can be refreshing, fun,
and surprisingly productive.

## Method

Start with a base install of a server distro.  I use Ubuntu 18.04
LTS for this, but I'll probably move on to something more modern
soon.

### Installing Linux

I typically do this from DVD, which means that your laptop needs a
DVD drive.  I haven't done this from a USB thumb drive yet, although
newer macs will support this and it's probably much faster.

Notes:

 * The default 18.04 installer doesn't create a EFI partition, but
    you will need one.  If you get a warning message, after the disk
    partitioning step, that warns you that you don't have an EFI
    partition, go back and add one.  It should be at least 250MB
    in size, and of type EFI (aka ESP) and bootable.

 * When choosing the install options, make sure that you add
    openssh-server.  I don't know why this is the case, but
    it works better if it is installed this way than by installing
    it manually.  (there's no obvious reason for this, but it
    has definitely caused problems in the past)

### Configuring things

 * To swap the control and caps-lock keys

   Edit /etc/default/keyboard, and change XKBDOPTIONS="ctrl:swapcaps"

 * To change the console font

   sudo dpkg-reconfigure console-setup

   Then follow the menus to choose a font.  Which font depends
   on the resolution of your screen, but for the higher-res screens
   you'll probably want to use a Terminus font.  Somewhere between
   a screen width of 80 and 180 is good for most purposes (also
   depending on how large your screen is, not just its resolution).

 * To keep the system from sleeping when the lid is closed

   Edit /etc/systemd/logind.conf and make sure that
   HandleLidSwitch=ignore.
   Then restart systemd-logind (sudo service systemd-logind restart)
  
## Useful utilities

 * battery
 * brightness



