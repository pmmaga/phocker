# phocker

An exercise in self-isolation using PHP

## Usage

The first step is to pick a minimal rootfs of your choice and copy its contents to the `rootfs/` folder.
One example of a minimal rootfs can be found in http://cdimage.ubuntu.com/ubuntu-base/releases/

Now you can use `phocker run [command]` to execute any command in the "container".

### Examples

```
pedro@earth ~/dev/pmmaga/phocker $ ./phocker run ls
bin  boot  dev	etc  home  lib	lib64  media  mnt  opt	proc  root  run  sbin  srv  sys  tmp  usr  var

pedro@earth ~/dev/pmmaga/phocker $ ./phocker run ps
  PID TTY          TIME CMD
    1 ?        00:00:00 php
    6 ?        00:00:00 sh
    7 ?        00:00:00 ps

pedro@earth ~/dev/pmmaga/phocker $ echo "Hello phocker!" | ./phocker run cat --
Hello phocker!

pedro@earth ~/dev/pmmaga/phocker $ ./phocker run /bin/bash
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
