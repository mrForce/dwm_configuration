Notice: This is very much alpha quality software. Be careful.


This is my customized version of the DWM window manager.

Suppose you have two windows, A and B. These are completely new windows. You have you mouse point in A, at location (x1, y1). You use the keyboard to set the focus
on window B. The mouse pointer will move to the center of B (this is part of my modification to DWM). Suppose this is at (x2, y2). You move the mouse to a new location in window B, at location (x3, y3).

Now, suppose you use your keyboard to set the focus on window A. It will move the mouse pointer back to point (x1, y1). If you focus on B using the keyboard, it will move the mouse to location (x3, y3).


This is what it looks like:


![Alt text](http://i.giphy.com/3o85g9H2yx8msdNu12.gif)


See how the location of the mouse pointer gets saved when you change focus with the keyboard, and is restored? These changes are made in the dwm.c file. I made a new struct called MouseLocation, and modified the Client struct. I also added things to the focusmon and focusstack functions.

This also includes the gapless grid layout; you can use it by pressing META-g

This config uses the windows key as META.

It uses Terminator for the terminal.


dwm - dynamic window manager
============================
dwm is an extremely fast, small, and dynamic window manager for X.


Requirements
------------
In order to build dwm you need the Xlib header files.


Installation
------------
Edit config.mk to match your local setup (dwm is installed into
the /usr/local namespace by default).

Afterwards enter the following command to build and install dwm (if
necessary as root):

    make clean install

If you are going to use the default bluegray color scheme it is highly
recommended to also install the bluegray files shipped in the dextra package.


Running dwm
-----------
Add the following line to your .xinitrc to start dwm using startx:

    exec dwm

In order to connect dwm to a specific display, make sure that
the DISPLAY environment variable is set correctly, e.g.:

    DISPLAY=foo.bar:1 exec dwm

(This will start dwm on display :1 of the host foo.bar.)

In order to display status info in the bar, you can do something
like this in your .xinitrc:

    while xsetroot -name "`date` `uptime | sed 's/.*,//'`"
    do
    	sleep 1
    done &
    exec dwm


Configuration
-------------
The configuration of dwm is done by creating a custom config.h
and (re)compiling the source code.
