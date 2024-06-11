## stock debian bookworm linux for the nanopi r5c & r5s

<i>
Note: This script is intended to be run:
* on a Debian machine
* with docker.io package installed
* with qemu-user-static package installed (unless the machine has an ARM64 cpu)
* by a user allowed to use docker (sudo usermod -a -G docker USER)
</i>
<br/>

**build debian bookworm using debootstrap**
```
sudo sh make_debian_img.sh
```

<i>the build will produce the target file mmc_2g.img.xz</i>

<br/>

**copy the image to mmc media**
```
sudo sh -c 'xzcat mmc_2g.img.xz > /dev/sdX && sync'
```
* note: to write to emmc while booted from mmc, use ```/dev/mmcblk1``` for ```/dev/sdX```

<br/>

**login information**
```
user: debian
pass: debian
```

<br/>

**multiple build options are available by editing debian/env.sh**
```
media='mmc_2g.img' # or block device '/dev/sdX'
deb_dist='bookworm'
hostname='nanopi5-arm64'
acct_uid='debian'
acct_pass='debian'
disable_ipv6=true
extra_pkgs='pciutils, sudo, wget, u-boot-tools, xxd, xz-utils, zip, unzip'
```

