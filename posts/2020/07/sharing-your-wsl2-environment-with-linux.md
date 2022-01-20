---
title: "Sharing your WSL2 environment with Linux"
date: "2020-07-07"
categories: 
  - "hax"
tags: 
  - "ext4"
  - "filesystem"
  - "guestmount"
  - "linux"
  - "wsl2"
---

It seems like I'm in a constant state of switching between Windows 10 and Linux on my personal laptop, so I keep both environments available in a dual boot. I've really enjoyed using WSL2 on my Windows 10 side, so much so that I have a bunch of projects that are in active use within that environment.

WSL2 uses a lightweight virtual machine to boot a Linux kernel, and each WSL Linux distribution keeps a complete ext4 Linux filesystem as a virtual hard disk image for faster -- and native -- file access on your Windows 10 host. Luckily, it's pretty easy to mount this filesystem if you're booted on the Linux side.

I'm using Windows 10 2004 and Pop\_OS! 20.04, but this process will work with any Linux distribution that is set up to mount NTFS partitions read/write using ntfs-3g and can install the guestmount utility via libguestfs.

To do this, the Windows 10 disk will need to be mounted within your Linux environment. On my Linux installation, I mount my Windows 10 volume using ntfs-3g under /mnt/c.

You will need to find your root virtual disk, which is located in the application package directory of the WSL Linux distribution being used. In Windows, this follows the pattern "_C_:\\Users\\_username_\\AppData\\Local\\Packages\\_distribution_\\LocalState\\ext4.vhdx", where _C_ is your drive letter, _username_ is your Windows username, and _distribution_ is the generated name of the distribution used. If one is using Ubuntu, the generated name is "_CanonicalGroupLimited.UbuntuonWindows\_79rhkp1fndgsc_". I'm going to use this path in the example below.

The other tool we'll need is _guestmount_. This can be installed on Debian/Ubuntu/derivatives by installing the _libguestfs-tools_ package using APT.

sudo apt install libguestfs-tools

Now, let's mount the partition. The mount points in the image do not like being mounted as a normal user, and I'm happy to hear suggestions on how to get around this. We're using the _allow\_other_ flag to let other users have access to the filesystem, and mounting it under /mnt/wsl. You can alter the username, distribution, and mount point to match your system.

sudo mkdir -p /mnt/wsl
sudo guestmount -o allow\_other \\
  --add /mnt/c/Users/username/AppData/Local/Packages/CanonicalGroupLimited.UbuntuonWindows\_79rhkp1fndgsc/LocalState/ext4.vhdx \\
  -i /mnt/wsl

Your WSL2 distribution is now available under /mnt/wsl. I haven't found any odd side effects, except that Visual Studio Code reminds you to install the Remote - WSL extension, as WSL is available on your system. Go figure. :)

Remember to use guestunmount when complete, before the Windows filesystem is unmounted. Too many force unmounts will eventually cause problems with the WSL2 environment, and there isn't a lot of self-healing available.
