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

--restore
  restore backgrounds at session start.

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
2. Splash checkbox screen for multiple monitors only:
   checked to show, unchecked to hide
3. Slight adjustments to width of the main interface
4. A background color for centered or transparent images

Startup
-------
You can start the program to restore your background choices from
your **autostart** or similar file with the following:

``xwwall --restore``

Consult your window manager or compositor documentation for the
correct procedure.

SEE ALSO
========

gtk3dialog(1), feh(1), swaybg(1)
