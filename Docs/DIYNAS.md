## My DIY NAS

This page is a short resume about my DIY (do it yourself) [NAS](https://en.wikipedia.org/wiki/Network-attached_storage). For some time I have wanted to upgrade the old NAS (from 2010). A server crash in October 2016 forced me to commence an upgrade both the OS and HW platform. Upgrade of the hardware can quickly become a challenge if the OS does not support the hardware. And some of the OS I tried out did not support my HW.

I do not spend much time building or maintaining my NAS. The main purposes of my NAS are:

- storing backup of my files
- and share out disk (by SMB/CIFS and/or AFP)

My knowledge about computer hardware is very limited. The hardware in new NAS is more or less selected by advices from the computer store. The most important objective is to get hardware which is supported by the OS. The form factor of the motherboard also narrows the possibilities. I want a small NAS and decided to go for a [mini-ITX](https://en.wikipedia.org/wiki/Mini-ITX) motherboard.  The hardware in my NAS is probably not the best solution. But it works (finally).

For me, backup is very important. And do backup to several locations and keep the backups in the different locations synchronised. Not loosing data is the obvious reason for doing backup. There are several ways to "loose" data. Disk crash is one. Highjacking by ransomware another. A **restore** of data is a cheap solution if either of the them occurs.

## Encrypt sensitive information

I am also observant of not storing personal and sensitive information unsecured at off site locations. There are several solutions to encrypt data. One is creating a secure folder or volume. Almost all OS supports [encrypted file systems](https://en.wikipedia.org/wiki/Filesystem-level_encryption) today. Another is to encrypt files containing personal and sensitive information (as tax reports). I am using the last one and encrypt files by using [GPG](https://en.wikipedia.org/wiki/GNU_Privacy_Guard). I also encrypt files containing sensitive information in case my MacBook is **compromised** (hopefully not likely to happen due to precautions).

I have **not** tested rsync on encrypted folders or volumes. I am quite sure it works, but I do not know how effective rsync is when there are changes within the encrypted folder or volume.


## Replace Oracle Solaris as NAS SW?

Until recently I have only used the trial version of Oracle Solaris 11.3. There are no updates and bug fixes for the trial version. Receiving updates and bug fixes cost money. There are several options for installing NAS by using free and open source SW. That is the main reason for choosing other OS for my NAS. There are two options :

- either go for a special NAS SW (as NAS4Free or FreeNAS) 
- or use stock OS (as FreeBSD 11 or Ubuntu 16.10).

After some testing of [FreeBSD 11](https://www.freebsd.org/), [NAS4free](http://www.nas4free.org/) and [FreeNAS](http://www.freenas.org/) I have decided to go for NAS4free. I did not try Ubuntu 16.10\. The decision to go for NAS4free is not scientific. I have two requirements for my NAS : ZFS and minimal effort to setup and use. And of course stability. There are other NAS solutions but they do not support ZFS.

### Other OS options

Other possible OS options supporting ZFS are:

- [OmniOS](https://omnios.omniti.com/) (recommended by [napp-it.org](http://napp-it.org/))
- [OpenIndiana Hipster](http://www.openindiana.org/) 

Both OS booted into single user mode (due to missing support of HW). And that was an effective stop of further testing.

## Why NAS4free?

[ZFS](https://en.wikipedia.org/wiki/ZFS) is an important part of my NAS. ZFS was developed by Sun Microsystems as part of OpenSolaris. [OpenZFS](http://open-zfs.org/wiki/Main_Page) is now the main developer of the open source ZFS used in FreeBSD and Linux.

I downloaded **FreeNAS** nightly build. FreeNAS did not boot properly on my hardware. I have read a lot of positive reviews of FreeNAS. Sorry it did not boot properly on my NAS and I dropped any further tests.

**FreeBSD 11** was installed and booted fine. I played around about one day before dropping FreeBSD 11 as well. I dropped FreeBSD for one reason only. There was to much tweaking and installing of various ports to get it up and running as NAS and sharing out filesystems. Creating and mounting zpools by command line using the correct parameters is not trivial. I also installed Samba (to test sharing [SMB](https://en.wikipedia.org/wiki/Server_Message_Block)). Even more tweaking and I managed to connect to a shared SMB filesystem. I am quite sure I would manage to get my NAS up and running by using FreeBSD 11. But there was to much time to set up and installing.

I dropped testing of Ubuntu 16.10 due to reasons as for FreeBSD 11.

I installed **NAS4free** and imported zpools created in FreeBSD. After installation I used about *one hour* to get it up and running. The GUI in NAS4free is easy, intuitive and nice to use. The current stable version of NAS4Free is based upon FreeBSD 10.3 and last release of NAS4Free was Oct 2016.

I have installed the latest release of NAS4free (version 11.0.0.4.3252 released 20 nov 2016) which is based on FreeBSD 11 (11.0-RELEASE-p3).

My NAS4Free based NAS is now setup to do the following:

- Mounted a mirrored zpool used for backup by using RsyncOSX. To use RsyncOSX (or rsync) I enabled ssh and rsync on the server (by using the GUI). I added a user (thomas) and enabled [passwordless login](https://github.com/rsyncOSX/Documentation/blob/master/PasswordlessLogin.md).
- Shared out a SMB filesystem.


## The NAS

The only piece from my old NAS to keep is an Intel RAID controller. All other HW is replaced (not the storage). Why keep the RAID controller? First of all it is supported by most OS. The motherboard has only four SATA ports. I have (including the boot disk) seven SATA disks. The RAID controller has 8-ports and all disks except the boot disk, is connected to the RAID controller. The controller is discontinued but it stills works.

<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody>
<tr><td style="text-align: center;"><a href="https://3.bp.blogspot.com/-BWVk5GOBXiU/V4Cv0O6GoVI/AAAAAAAALqk/I233yb6_lPIYsPK2BjX1ajNSupJLAvfQQCLcB/s1600/Small%2B%25281%2Bof%2B12%2529.jpg" imageanchor="1" style="margin-left: auto; margin-right: auto;"><img border="0" height="267" src="https://3.bp.blogspot.com/-BWVk5GOBXiU/V4Cv0O6GoVI/AAAAAAAALqk/I233yb6_lPIYsPK2BjX1ajNSupJLAvfQQCLcB/s320/Small%2B%25281%2Bof%2B12%2529.jpg" width="320" /></a></td></tr>
<tr><td class="tr-caption" style="text-align: center;">Fractal Design Cabinet</td></tr>
</tbody></table>


I am quite pleased to replace Oracle Solaris as OS with NAS4Free. NAS4Free is free software and it is under continuously development. The WebGUI is intuitive, nice and easy to use. It took med just a couple of minutes to format two drives, create a new mirrored zpool, create a new user and mount 1 TB of disk to use as backup for RsyncOSX.

Total disk in NAS is 6 [Terabyte](https://en.wikipedia.org/wiki/Terabyte) setup as mirror. My NAS is sharing out 3 TB.

The hardware of my 2016 NAS are:

1.  Fractal Design Node [304 Mini-ITX Black](http://www.fractal-design.com/home/product/cases/node-series/node-304-black)
2.  Fractal Design Integra M 450W PSU
3.  [Intel RAID Controller SASUC8I 8P, SAS/SATA](http://www.newegg.com/Product/Product.aspx?Item=N82E16816117157) RAID 0/1/1E/10E, PCIe x8 (2x int. mini-SAS SFF-8087) (the 8-port controller is from 2011 and still working)
4.  [MSI H110I](https://www.msi.com/Motherboard/H110I-PRO.html#hero-overview) Pro, Socket-1151 motherboard
5.  [Intel Core i5-6400](http://ark.intel.com/products/88185/Intel-Core-i5-6400-Processor-6M-Cache-up-to-3_30-GHz), Socket-LGA1151 processor
  - using the Intel Core i5 as CPU in NAS is probably an overkill
6.  Kingston ValueRAM DDR4 2133MHz 16GB
7.  Two WD Red 1TB NAS Hard drive, SATA 6Gb/s (SATA 3.0), 64MB, 3.5", 24x7 reliability, IntelliPower (bought in 2014)
8.  Two WD Desktop Green 2TB SATA 6Gb/s, (SATA 3.0), IntelliPower, 64MB, 3.5" (bought in 2012)
  - one disk HW failed and replaced in 2013 without any loss of data


## Setup of NAS - ZFS filesystem

The server has 3 Terabyte (TB) of storage. The storage is setup as a ZFS filesystem and all disks (four disks altogether, two disks of 2TB each and two disks of 1TB each) are all setup as a ZFS mirror. That is the two 2TB disks are mirroring each other as well as the two 1TB disks. If one disk fails ZFS is automatically restoring (by ZFS scrub) the failing disk. If one disk fails (by HW) and must be replaced ZFS has functionality for unmounting failed disk, mount a new one and put the new one into mirrored pool again.

It is easy and cheap to setup a backup server based on Linux or other server OS and rsync. There is an open source project [Netatalk](http://netatalk.sourceforge.net/) Apple Filing Protocol ([AFP](https://en.wikipedia.org/wiki/Apple_Filing_Protocol)) fileserver. Some years ago I testet Apple Time Machine and Netatalk on a Solaris 11 server. It worked for some time, but also failed. I dont know stable Netatalk and Apple Time Machine is now. But for me rsync is the best solution. And for backups to remote servers outside my house (by Internet connection) rsync is most likely the best tool to use. By using rsync I backup all data on my Macs. A complete reinstallation of a MacBook is done by a fresh install of OS X and then restore all data by rsync. Safe and reliable.

<div class="separator" style="clear: both; text-align: center;">
<a href="https://1.bp.blogspot.com/-HXJd4gxFSv4/V5296rU5ogI/AAAAAAAALwA/bcWuJ8nnipISjDrFeuCLCI7Xoo9EguS2gCLcB/s1600/WhatIsRsyncOSX.001.jpeg" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="480" src="https://1.bp.blogspot.com/-HXJd4gxFSv4/V5296rU5ogI/AAAAAAAALwA/bcWuJ8nnipISjDrFeuCLCI7Xoo9EguS2gCLcB/s640/WhatIsRsyncOSX.001.jpeg" width="640" /></a>
