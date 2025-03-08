# Debian DKMS package for ntsync kernel module

The [ntsync](https://lore.kernel.org/all/20241213193511.457338-1-zfigura@codeweavers.com/) driver implementing NT synchronization primitives was merged for Linux 6.14.
This repository contains the source of a Debian package that uses DKMS to automatically build and install the ntsync kernel modules on Debian Bookworm (Linux 6.1).
Although untested, it should also work on Debian derivates like Ubuntu.

Current ntsync version is [6.14-rc1](https://web.git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/log/drivers/misc/ntsync.c?h=v6.14-rc1)
from [mainline](https://web.git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/log/drivers/misc/ntsync.c).
Additionally, it includes [fa2e558](https://web.git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git/commit/drivers/misc/ntsync.c?id=fa2e55811ae25020a5e9b23a8932e67e6d6261a4)
from [linux-next](https://web.git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git/log/drivers/misc/ntsync.c)
that sets the `/dev/ntsync` mode to 0666 to facilitate access from user accounts.

Build and install the .deb package as follows:

```sh
sudo dpkg-deb -b ntsync-dkms.deb.d ntsync-dkms_6.14-rc1+fa2e558_all.deb
sudo apt install ./ntsync-dkms_6.14-rc1+fa2e558_all.deb
```


## Known Issues

* Incompatible with Debian Trixie (Linux 6.12) version of linux-libc-dev, which includes `/usr/include/linux/ntsync.h`.
