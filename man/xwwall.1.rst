xwwall
######

######
Xwwall
######

:Copyright: GPLv2+
:Manual section: 1

SYNOPSIS
========
| **xwwall** [options]

DESCRIPTION
===========
**xwwall** is a graphical wallpaper setter for the X Window System
often known as **X11** and **Wayland** desktops for Linux and other
\*nix distributions. It should run in light weight desktop environments
like Openbox, fluxbox, JWM for X11 and Labwc, Sway and others for
Wayland. It supports up to 6 monitors. It is a shell script written
in **bash**.
It requires **Gtk3dialog** for the graphical user interface which is
a gtk+-3.0 based UI program that describes dialog boxes from a shell
script.
In X11 it utilises **feh** as the engine to set the wallpaper and
**xrandr** to get screen dimensions and placement of monitors.
In Wayland it uses **swaybg** to set wallpapers and **wlr-randr** for
screen dimensions and placement.

OPTIONS
=======
**xwwall** can be invoked with the following options.

-h | --help
  show help and exit.

-v | --version
  print version and exit.

-d|--delconf
  delete the user configuration file ``$HOME/.config/xwwall/xwwall.conf``
  in case it gets messed up from manual intervention.
  
--restore [ optional arg ]
  restore backgrounds at session start.
  
  ``--restore`` takes an optional ``profile`` argument.
  See **Advanced Startup** further below.

USAGE
========
Normally, **xwwall** is started from a menu entry without any options
although you could start it from a keyboard shortcut.

Main GUI
--------
The first thing you may see is a splash window warning you if you
have too many wallpapers and cuts off at a 250 limit and then a
window opens showing your wallpapers. Just select one and it will
open in a **Sub GUI** window; select the image by pressing it or **no**
to reject.
You can also select if you want the image to strecth, center, tile or fit
your screen. If you do select **no** the program goes back to the main
window.
If you have more than 1 monitor the program cycles through those so you can
choose different backgrounds for each of them.
Once done a confirmation window opens and you can either press **Yes**,
**Refresh** or **No**; **Yes** sets your wallpaper(s) while **No** exits
the program. **Refresh** restarts the program so you can try again.
You can exit the program safely at any stage via **Cancel** or 
the **X** (close) button of your window manager or compositor.

Sub GUI
-------
This pops up after your selection in **Main GUI** and if on a single monitor
sets the background directly or otherwise cycles through your outputs
and the pops the **Confirm GUI** at the end. 

Preferences
-----------
There is a **Preferences** button in the bottom left of the main window
to set the following:

1. Background directory - any directory where you have read access
2. Optional extra directories for wallpaper search.
   If extra directories are enabled a preference checkbox is shown
   so that the user can switch between the main background directory or
   the configured extra background directories. Up to 3 extra directories
   are allowed. Checked enables extras, unchecked for the default.
3. Splash checkbox screen for multiple monitors only:
   checked to show, unchecked to hide.
4. Slight adjustments to width of the main interface.
5. A background color for centered or transparent images.


Configuration
-------------
The config files are stored in ``$HOME/.config/xwwall/`` directory.
Here the main configuration is stored from *Preferences* and if using
*wayland* the ``cmd`` file which is sourced at startup with the
``--restore`` option in your startup configuration. On *X11* the ``feh``
program generates a ``$HOME/.fehbg`` executable file which is executed
at startup  with the ``--restore`` option if configured in your startup
configuration.

Extra background directories are stored in a **bash array** in the config
file from the **Preferences** interface.

Startup
-------
You can start the program to restore your background choices from
your **autostart** or similar file with the following:

``xwwall --restore``

Consult your window manager or compositor documentation for the
correct procedure.

Advanced Startup
----------------
**xwwall** supports *profiles* such that you can have separate profile
directories under the ``$HOME/.config/xwwall/`` directory. This is
useful if you have different graphical environments setup so that you
can have different wallpapers in different sessions. For example, you
may have ``labwc`` and ``openbox`` on your system. You can create
separate profiles for each of these, and as many as you want, named
whatever you want. ``$HOME/.config/xwwall/labwc/`` profile directory
for *labwc* and ``$HOME/.config/xwwall/openbox/`` profile directory
for *openbox*.

Since *labwc* is a *wayland* compositor then to make the profile useful
you copy the ``$HOME/.config/xwwall/cmd`` file to
``$HOME/.config/xwwall/labwc/cmd``

And since *openbox* is an *X11* window manager the approach is slightly
different. You need to copy the ``$HOME/.fehbg`` executable file to
``$HOME/.config/xwwall/openbox/.fehbg``, making sure to preserve the
executable permissions on the copied file.

Similar procedures can be followed for respective *wayland* compositors
and *X11* window managers.

Once you have created your profile it then needs to be included in your
startup routine. You can simply append the name of the profile directory
to the ``--restore`` option in your startup routine like so:

``xwwall --restore openbox``

or whatever desired profile directory name you have used.

Running from a differnt Directory
---------------------------------
**xwwall** can be run from a different location then you HOME dir. For
this to be useful delete or rename your configuration so that the
directory where you run from is picked up.

BUGS
====

Please report any bugs or feature requests to:

https://github.com/01micko/xwwall/issues

SEE ALSO
========

gtk3dialog(1), feh(1), swaybg(1)
