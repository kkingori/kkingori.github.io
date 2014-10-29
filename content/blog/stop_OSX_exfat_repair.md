+++
date = 2014-10-15T17:38:21Z
title = "stop_OSX_exfat_repair"
slug = "Stop-OSX"

+++

The ExFat filesystem is becoming the defacto filesystem for sharing between windows, linus and osx. It's terribly conveninet t

```sh

#!/bin/sh

sudo diskutil unmount force KEN
cd /Volumes
mkdir KEN
sudo /System/Library/Filesystems/exfat.fs/Contents/Resources/exfat.util -MU disk1s1 /Volumes/Ken removable writable nosuid nodev

```