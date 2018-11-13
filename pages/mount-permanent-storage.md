---
title: Instructions for Mounting Permanent Storage
#subtitle: By Riccardo Murri
author: Riccardo Murri
layout: page
hide: true
---



It is possible to attach permanent disk space to Elasticluster, but at the moment it's still a manual process.  It usually goes like this:

1. Create cluster
2. Create volume
3. Attach volume to cluster frontend (OpenStack has an "attach" command,
other clouds might use a different term)
4. (First time only) Find out what device name the volume has gotten in
Linux (e.g. `/dev/vdb` -- it can usually be seen by running `sudo
dmesg | tail`)
5. (First time only) Format the volume::

```
mkfs.ext4 -L /myvolume /dev/vdb
```

6. (First time only) Define volume mount in `/etc/fstab`::
```
    # add this line to /etc/fstab
    LABEL=/myvolume /myvolume ext4  defaults 0 0
```
7. Mount the volume::
```
    sudo mkdir -pv /myvolume
    sudo mount /myvolume
```
If you do not want the volume to be automatically mounted after a
reboot, replace `defaults` with `defaults,noauto` in the `/etc/fstab`
line at step 6.
