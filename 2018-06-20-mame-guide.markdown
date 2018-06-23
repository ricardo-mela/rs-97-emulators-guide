---
layout: post
title:  "MAME User Guide"
date:   2018-06-20 09:08:41 +0100
categories: rs97 arcade mame
---
Greetings! This is my first attempt at a guide, so bear with me on this.

**MAME4ALL, the guide**

[Main GitHub page][mame-github]

You know what MAME is. Read on.

**Config**

First, set up some directories on your ROMS partition.

For this example, I am using v1.8.1 external SD firmware.

I will store my roms in ``roms/MAME``.

This, on the RS-97 OS, will map to ``/mnt/int_sd/roms/MAME``

To easily modify the ROM paths (which you will need) you can edit the file on ``/mnt/int_sd/.mame4all/frontend/mame.cfg`` or if you are accessing the ROMS partition directly, ``.mame4all/frontend/mame.cfg`` by changing the last part of the string so that it looks like this:


```
336,16,10,0,-1,2,100,100,1,0,1368,0,/mnt/int_sd/roms/MAME
```

In-game controls and hotkeys can be checked using [this link][mame-controls].

**Standard in-game MAME controls:** | 
---- | ----
D-Pad and Analog Pad | UP, DOWN, LEFT and RIGHT.
Buttons A,B,X,Y,L,R | MAME buttons 1,2,3,4,5,6
Button SELECT | Insert credit
Button START |  Start game

**Extended controls in game (to access menus and options)** | 
---- | ----
Buttons START+SELECT | Mame menu
Buttons START+L+R | Esc (exit to mame frontend)
Buttons L+R | Pause     
Buttons SELECT+R | Show FPS.
Buttons START+L | Show profiler
Buttons L+B | Snapshot

[mame-github]: https://github.com/thefossilrecord/mame4all-rs97
[mame-controls]: https://github.com/thefossilrecord/mame4all-rs97/blob/master/distrib/mame4all/readme.txt
