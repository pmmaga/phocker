# phocker

An exercise in self-isolation using PHP

## Requirements

- linux 3.8+
- util-linux package
- PHP 7.0+
- ext-posix

## Installation

- Clone this repository
- Pick a minimal rootfs of your choice and copy its contents to the `images/[name of the image]` folder.
  Some root filesystems you may try:
  - [Ubuntu](http://cdimage.ubuntu.com/ubuntu-base/releases/)
  - [CentOS](https://github.com/CentOS/sig-cloud-instance-images/tree/CentOS-7/docker)
  - [Alpine](https://alpinelinux.org/downloads/)
  - Most images on [LXC's Jenkins](https://jenkins.linuxcontainers.org/view/Images/) should work fine.

## Usage

Now you can use `./phocker run [image] [command]` to execute any command in the container.

The container is not being removed after exiting. Periodical cleanup of the `containers/` folder may be advisable.

### Examples

```
pedro@host ~/dev/pmmaga/phocker $ ./phocker run alpine ls
bin  boot  dev	etc  home  lib	lib64  media  mnt  opt	proc  root  run  sbin  srv  sys  tmp  usr  var

pedro@host ~/dev/pmmaga/phocker $ ./phocker run alpine ps
  PID TTY          TIME CMD
    1 ?        00:00:00 php
    6 ?        00:00:00 sh
    7 ?        00:00:00 ps

pedro@host ~/dev/pmmaga/phocker $ echo "Hello phocker!" | ./phocker run alpine cat --
Hello phocker!

pedro@host ~/dev/pmmaga/phocker $ ./phocker run ubuntu /bin/bash
root@phocker:/# whoami
root
root@phocker:/# hostname
phocker
root@phocker:/# exit
exit
```

## Motivation

Heavily inspired by Liz Rice's talk [Containers from scratch](https://www.youtube.com/watch?v=Utf-A4rODH8) and the corresponding [repository](https://github.com/lizrice/containers-from-scratch) I set out to try to accomplish the same using PHP.

It also helped me better understand the process behind the isolation achieved by container runtime engines.
