---
layout: post
title:  "UselessRS97 on Ubuntu"
date:   2018-06-20 09:08:41 +0100
categories: rs97 arcade fba
---
**UselessRS97 on Linux, install and set up using Linux**

[Dingoonity forum post][dingoonity]

I set to install the latest internal firmware for the RS-97, but I don't have a Windows or Mac machine to play with. In short, I tried to do all the installation procedure using Linux tools, on Ubuntu (16.04, 18.04 should work too).

First of all, check the version of your hardware by removing the battery and checking inside the battery compartment.

Download the firmware, unzip and install it on a SD card. I used [Etcher][etcher] to do this, because it has a nice UI and it is self-contained.

Then, disassemble the thingy, remove the old SD card and install the new one. Assemble, boot and see if everything is OK.

**Install Service Packs**

Turn off the RS-97, plug the RS-97 to your computer, and turn it on.

When prompted on the console, select the USB Drive option. 

Now turn to your computer and chech the output of dmesg:

``dmesg | tail -n 15``

```
[20781.237682] usb 1-2: new high-speed USB device number 12 using xhci_hcd
[20781.390218] usb 1-2: New USB device found, idVendor=0525, idProduct=a4a5
[20781.390221] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[20781.390222] usb 1-2: Product: File-backed Storage Gadget
[20781.390224] usb 1-2: Manufacturer: Linux 2.6.31.3 with musb_hdrc
[20781.390225] usb 1-2: SerialNumber: 3230204E6F76
[20781.728796] usb-storage 1-2:1.0: USB Mass Storage device detected
[20781.731190] usb-storage 1-2:1.0: Quirks match for vid 0525 pid a4a5: 10000
[20781.732429] scsi host3: usb-storage 1-2:1.0
[20781.732736] usbcore: registered new interface driver usb-storage
[20781.741522] usbcore: registered new interface driver uas
[20782.746489] scsi 3:0:0:0: Direct-Access     Linux    File-Stor Gadget 0316 PQ: 0 ANSI: 2
[20782.747274] scsi 3:0:0:1: Direct-Access     Linux    File-Stor Gadget 0316 PQ: 0 ANSI: 2
[20782.751721] sd 3:0:0:0: Attached scsi generic sg1 type 0
[20782.752649] sd 3:0:0:1: Attached scsi generic sg2 type 0
[20782.752790] sd 3:0:0:0: Power-on or device reset occurred
[20782.755828] sd 3:0:0:1: Power-on or device reset occurred
[20782.758776] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[20782.759345] sd 3:0:0:1: [sdc] Attached SCSI removable disk
[20844.285801] sd 3:0:0:0: [sdb] 29373614 512-byte logical blocks: (15.0 GB/14.0 GiB)
[20844.286696] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

So, we know now that the device file for the drive is /dev/sdb. So, now you have to mount it.

Create a mount pount, let's say, ``/media/rs-97``:

``mkdir /media/rs-97``

And mount the device

``sudo mount /dev/sdb /media/rs-97``

This will mount the device and the directories will be available at that location.

Unzip the Service Pack to that location. You might need to use ``sudo`` to copy the files. I normally use [Midnight Commander][mc] to manage files and if you decide to do so, you might need to disable the "Preserve file attribute" option when copying.

Once you copied the files, you can clear the buffers and write all data to the device by running

``sync``

Then, you can unmount the device with

``sudo umount /media/rs-97``

And you are done! Any time you need to copy files to the RS-97 (roms, or service pack updates), repeat the procedure.

For any purpose, the files on the SD card are located on 

``/mnt/int_sd/``

On the RS-97 operating system.

Hope this helps!

[dingoonity]: https://boards.dingoonity.org/ingenic-jz4760-devices/uselessrs97-internal-firmware-for-revision-2-1/
[etcher]: https://etcher.io/
[mc]: https://midnight-commander.org/
