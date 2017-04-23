# xscreensaver_autoset
Scripts to automatically inhibit and activate xscreensaver based on CPU load

Purpose
================================================================================
xscreensaver_autoset is a set of scripts that serve to automatically inhibit or
activate xscreensaver based on CPU load. It measures the CPU load periodically
(by default every 5 seconds). If the average load at every check over a
specified length of time (by default 15 seconds) is greater than a threshold
value (by default 3%), the screensaver is inhibited. You may tweak the
threshold and other settings as desired, but this value will probably work well
to ensure the screensaver is inhibited when watching movies, listening to music,
or doing other CPU-intensive tasks. If the average load is less than the
threshold at every check over a specified length of time (by default 30
seconds), the screensaver is activated again.

A script is also included to automatically suspend the computer two minutes
after xscreensaver blanks the screen. (So you need to set up xscreensaver to
blank the screen for this to work. You are also, of course, free to adjust the
script as desired.)

Installation
================================================================================
Just put all the scripts somewhere in the PATH, like /usr/local/bin, and make
sure they are user-executable.

Initial setup
================================================================================
Before running the script for the first time, start xscreensaver on Random
Screensaver mode and with Display Power Management enabled (on the Advanced
tab). Other settings can be whatever you prefer. After the first time running
it, xscreensaver will still need to be running for this tool to work, but you
don't need reset the screensaver mode and display power management. The scripts
will take care of that for you.

Running
================================================================================
As mentioned above, xscreensaver should be running, and there should not be any
other screensaver or screen blanking / power management tool running, because it
may interfere. To use this tool, simply run xscreensaver_autoset, either from
the command line or on startup of your window manager. notify-send is used to
display a notification whenever the screensaver is inhibited or activated.
Running from the command line will provide additional information about the CPU
load at each cycle when a change in mode is [potentially] about to occur.

To automatically suspend the computer after xscreensaver blanks the screen, run
the xscreensaver_suspend script. Like xscreensaver_autoset, it can be run either
from the command line or as a startup script.

The other two scripts not mentioned so far, xscreensaver_controller and
user_suspend, are supporting scripts for xscreensaver_autoset and
xscreensaver_suspend, respectively. They can also be used alone if desired.

Settings
================================================================================
Settings are hardcoded into xscreensaver_autoset, but they can be changed
manually if desired by modifying the script. The parameters are:

* interval: how frequently to check the CPU load (in seconds) (default 5)
* ss_cpu_threshold: threshold CPU load (in percent) to inhibit or activate the
  screensaver (default 3.0)
* ss_count_activate: number of consecutive cycles below the threshold before
  activating the screenaver (default 6)
* ss_count_inhibit: number of consecutive cycles below the threshold before
  inhibiting the screenaver (default 3)

Software versions
================================================================================
These tools have been tested on Slackware64-14.2 with xscreensaver 5.36 and
Python 2.7.13. They may or may not work with other versions of xscreensaver and
Python or on other systems.
