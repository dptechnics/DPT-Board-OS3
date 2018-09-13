# DPT-Module V1 toolchain, based on the OpenWRT 18.06 distribution.

## Jumpstart 

To get an firmware image for your DPT-Module working you need to do the 
following:
1. Clone the repository to your build host `git clone git@github.com:dptechnics/DPT-Board-OS3.git`
2. Go to the `DPT-Board-OS3` directory
3. Execute the command `make menuconfig` and select the following options:
⋅⋅* Target System: Atheros AR7xxx/AR9xxx
⋅⋅* Subtarget: Generic
⋅⋅* Target Profile: DPTechnics DPT-Module V1
4. Save by double pressing the Escape key and choosing 'Yes' to save.
5. Build the toolchain and OS by typing `make`. When you have multiple cores available you can type `make -jx` where x is the number of cores in your pc plus one.
6. When the OS is compiled you can find an image in `bin/targets/ar71xx/generic/openwrt-ar71xx-generic-dpt-module-v1-squashfs-sysupgrade.bin`
7. Copy the file to the `/tmp` directory on your DPT-Module
8. Run `sysupgrade -n -v /tmp/openwrt-ar71xx-generic-dpt-module-v1-squashfs-sysupgrade.bin` to upgrade your DPT-Module. Be aware that all settings and files will be lost.

## Login to your DPT-Module/DPT-Board

The DPT-Board OS has a default root account:

username: root
password: dptechnics

Make sure that you change the root password to one of your own to make the
board secure. You can do this by logging in through SSH and issuing the `passwd`
command.

## Requirements

You need to have installed gcc, binutils, bzip2, flex, python, perl, make,
find, grep, diff, unzip, gawk, getopt, subversion, libz-dev and libc headers.

To build your own firmware you need to have access to a Linux, BSD or MacOSX system
(case-sensitive filesystem required). Cygwin will not be supported because of
the lack of case sensitiveness in the file system.

## Extra packages

Run "./scripts/feeds update -a" to get all the latest package definitions
defined in feeds.conf / feeds.conf.default respectively
and "./scripts/feeds install -a" to install symlinks of all of them into
package/feeds/.

## Support

Yu can contact DPTechnics support the DPTechnics website: https://www.dptechnics.com.
Alternatively you can post bugs via the github issue tracker.

