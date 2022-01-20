---
title: "Installing ChromeOS on Surface Go"
date: "2019-02-17"
categories: 
  - "hax"
tags: 
  - "chromeos"
  - "chromium"
  - "croissant"
  - "tablet"
---

![](https://i0.wp.com/www.nicholasmelnick.com/wp-content/uploads/2019/02/IMG_20190217_085545.jpg?fit=760%2C961)

**Note**: Hi from the past, everyone! This post is likely very out of date. There are new tools to replace Project Croissant, and new driver packs available for Surface products including the Go. This hasn't been updated since February of 2019.

I'm a tablet hopper. I love the idea of a tablet, but they always seem to fall short in one way or another. I've had a ton of Surface devices, iPads, and even a few Galaxy Tabs. My favorite device of all time is probably the first generation ThinkPad 10, but it's just slow enough at this point that it's not as fun as it once was. My current primary is a 10.5" iPad Pro.

I do love the Surface lineup, but Windows 10 is a surprising shortcoming. Don't get me wrong, I really like Windows 10, but from a tablet perspective, it's a huge step back from Windows 8. Do note, however, that's the only nice thing I'll say about Windows 8.

What I've really been waiting for is a really good 10-11" ChromeOS tablet. ChromeOS has a great core, Android support, Linux support for the apps you need, all wrapped up in easy updates and elegant consistency. Usually. The only devices in this form factor are the Acer Chromebook Tab 10, and the clone tablets that are based on that form factor. The ARM chip is somewhat anemic, but I'm mostly okay with that. My concern is the lack of supporting hardware -- namely, decent cases, and nicely integrated keyboard designs. Once something comes out that fits that niche, I'm first in line.

Until then? Haxxxxx.

Enter [Project Croissant](https://github.com/imperador/chromefy). Croissant, formerly Chromefy, is a tool to convert a ChromiumOS image to a full ChromeOS image. ChromiumOS is the open source version of ChromeOS, consisting of most of what makes ChromeOS good, but missing closed source bits, including Android support. By utilizing a ChromeOS recovery image, Croissant can generate a ChromeOS image that can be installed on most anything with some reasonable driver support. Armed with this, I'm hoping to make a Surface Go, arguably one of the best form factors out there right now, a much more useful tablet for me.

ymmv.

**What definitely doesn't work:**

- Front and Rear Cameras
- Power button to wake, but other touch events or keys seem fine

**What's fiddly:**

- Touch response is odd, a press event occurs even on light touches or drags
- The type cover function key icons do not correspond to their ChromeOS functionality
- Sleep still burns some battery

**What really works:**

- Wi-fi and bluetooth seem to work splendidly
- The stylus responds well, and the pen icon appears
- The type cover attaches and disconnects as one expects, backlight works, everything is fine
- The SD card mounts just fine
- USB-C devices work exactly as they should
- Audio output
- Lid sensor with Type Cover

To create this image, I used another machine running Linux. This can be done in a virtual machine, or using a Linux live image.

1. To begin, we need to gather dependencies
    1. Obtain [chromefy.sh from GitHub](https://github.com/imperador/chromefy)
    2. Obtain the [nocturne 71 recovery image](https://cros-updates-serving.appspot.com/)
    3. Obtain the [caroline 71 recovery image](https://cros-updates-serving.appspot.com/)
    4. Obtain the [ArnoldTheBat R72 Special image](https://chromium.arnoldthebat.co.uk/index.php?dir=special&order=modified&sort=desc)
2. We'll also need to grab updated firmware for wi-fi and bluetooth support within Chromium/Chrome
    1. Retrieve an up to date [firmware-6.bin](https://raw.githubusercontent.com/kvalo/ath10k-firmware/master/QCA6174/hw3.0/4.4.1/firmware-6.bin_WLAN.RM.4.4.1-00051-QCARMSWP-1) from ath10k firmware
    2. Retrieve updated [board.bin](http://www.killernetworking.com/support/K1535_Debian/board.bin) from Killer Networking wireless firmware
3. With all of our dependencies gathered, we can actually create our installation image
    1. Uncompress each image into a directory
    2. Copy chromefy.sh into the same directory
    3. Execute chromefy to create the image, using something similar to _sudo bash chromefy.sh chromiumos\_image.img chromeos\_11151.113.0\_nocturne\_recovery\_stable-channel\_mp.bin chromeos\_11151.113.0\_caroline\_recovery\_stable-channel\_mp.bin_
4. Write the updated chromiumos\_image.bin to a USB stick using [Etcher](https://www.balena.io/etcher/) or similar
5. Upon completion, remove and reinsert the USB stick
6. Insert updated firmware and configuration to our ChromeOS image
    1. Find the partition containing the rootfs, which may have automounted under /media/your-username/, and contains directories like 'bin', and 'lib'
    2. Remove _\[path-to-rootfs\]/lib/firmware/ath10k/QCA6174/hw3.0/board-2.bin_
    3. Replace _\[path-to-rootfs\]/lib/firmware/ath10k/QCA6174/hw3.0/board.bin_ with the previously downloaded file
    4. Replace _\[path-to-rootfs\]/lib/firmware/ath10k/QCA6174/hw3.0/firmware-6.bin_ with the previously downloaded file
    5. Create _\[path-to-rootfs\]/etc/modprobe.d/ath10k.conf_ and add `options ath10k_core skip_otp=y`to the file
7. Unmount the mounted USB filesystems
8. Get your Surface Go and running
    1. Within Windows, go to Settings > Update and Recovery > Recovery
    2. Under Advanced Startup, select Restart Now
    3. Navigate to Troubleshoot > Advanced, and select UEFI Firmware Settings
    4. Under Boot Configuration, disable Secure Boot and set USB Storage to the top of the boot order
    5. Select Reboot to boot from USB stick

This is a bit of the test front for the image. One is able to log in and poke around a bit within the USB live image. The installation process got a little hairy, though, at least for ArnoldTheBat 72 + Eve 71. Note that the first command run **will** blow away the copy of Windows installed on the Surface Go. There are instructions available on the Project Croissant GitHub README for doing multiboot. As I have the 64gb Go, multiboot makes no sense for me. Also note that the 128gb Go uses SSD instead of eMMC, so the device name is going to change, likely to some derivative of /dev/nvme0n1.

- Execute _/usr/sbin/chromeos-install --dst /dev/mmcblk0 --skip\_postinstall_
- Reboot into a live image of Linux
- Using Gparted, or similar, resize /dev/mmcblk0p3 (H-STATE) down one gigabyte
- Remove /dev/mmcblk0p12, the EFI\_SYSTEM partition
- Create a new partition, 1gb, fat32, with a partition name of EFI\_SYSTEM
- Apply
- Right click the EFI\_SYSTEM partition and then "Manage Flags"
- Select legacy\_boot, boot, esp
- Open a terminal
- _sudo mkdir /mnt/cros /mnt/efi_
- Insert the USB stick containing your ChromeOS image
- Find the device of the USB stick, likely /dev/sdb, and replace _sdx_ with the device found, and execute _mount /dev/sdb12 /mnt/cros_ to mount the Chrome image's EFI partition
- Execute _mount /dev/mmcblk0p12 /mnt/efi_ to mount the installed EFI partition
- Execute _cp -Rp /mnt/cros/\* /mnt/efi/_ to copy the EFI partition over
- Reboot and remove the USB stick

Welcome to your new ChromeOS installation!
