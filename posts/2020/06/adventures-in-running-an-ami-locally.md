---
title: "Adventures in running an AMI locally"
date: "2020-06-22"
categories: 
  - "infrastructure"
tags: 
  - "ami"
  - "aws"
  - "cloud"
---

I recently had to do some spelunking into a long-updated AMI image to move it over to automated builds. The AMI had been updated over the period of a few years with security updates, OS patches, configurations, and more, and very little documentation was generated on those changes, as organic growth tends to do. I wanted the opportunity to poke at it over time, but didn't necessarily want to burn the compute time in EC2 to maintain the instance, so I wanted to get it booting locally.

Of course, Amazon does not let you download AMIs unless you had them built and uploaded in the first place.

In this example, I'm using Linux to create disk images, and I'm running the resulting image in Hyper-V on Windows 10. Some commands can be altered to work with other environments.

### Tools Needed

- awscli
- gunzip or 7zip or WinRAR to decompress a .gz file
- qemu-img from [chocolatey](https://chocolatey.org/) or [here](https://cloudbase.it/qemu-img-windows/)

### The Process

1. Start a new instance with the AMI you'd like to work with. When creating the storage, uncheck delete on termination.
2. Once created, terminate the instance, it isn't needed anymore.
3. Create a new, nano Linux instance with default settings.
4. Within Volumes, attach the volume from your first instance to the new Linux instance.
5. Create or identify an S3 bucket to store your image to, and make sure the instance profile of the Linux EC2 instance can access that S3 bucket.
6. SSH into the Linux machine, and open a `screen` or `tmux` instance to shield you from disconnections.
7. Identify the device node of the new image. You can `dmesg | tail` or look in `/dev/nvme*` for new matching, unmounted nodes.
8. Now we image that device directly to S3. Replace `/dev/nvme1n1` with the device you found, and `your_bucket_name` with the destination you chose in S3. This command pulls a raw image, compresses it, and transmits it directly to S3:  
    `dd if=/dev/nvmen1 - | gzip | aws s3 cp - s3://your_bucket_name/ami-disk-image.img.gz`
9. With that image saved, you may now terminate the Linux EC2 instance you created, and delete the volume.
10. On your local machine, pull the disk image:  
    `aws s3 cp s3://your_bucket_name/ami-disk-image.img.gz .`
11. Use gunzip, 7zip, or WinRAR to gunzip the disk image
12. Use qemu-img to convert the image to Hyper-V:  
    `qemu-img.exe convert ami-disk-image.img -O vhdx -o subformat=dynamic C:\Users\Public\Documents\Hyper-V\ami-disk-image.vhdx`
13. Create a new Hyper-V instance in version 8, with this disk image mounted to IDE
14. Remove the generated image from S3

Congratulations, you now have your environment in a local VM to play with.
