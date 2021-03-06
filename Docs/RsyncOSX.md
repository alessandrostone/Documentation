
## Install RsyncOSX

RsyncOSX is a GUI for the rsync command-line tool. The main uses are:

- **backup** (and restore) of local files on Mac to **remote servers** connected to **Internet** or **local network** 
	- the above is why I wrote RsyncOSX to use myself
- backup (and restore) local files on Mac to local storage (attached disks)
	- if this is *the only use* there might be *other tools* more useful than RsyncOSX

## YouTube video

I have uploaded a short (about 4 minutes) [YouTube video of RsyncOSX](https://www.youtube.com/watch?v=ty1r7yvgExo) : "Downloading RsyncOSX, installing, first time configuration and using RsyncOSX for the first time. Backup (as demo) of about 120 MB of data and 4000 files to a VirtualBox FreeBSD machine."

## Download link and install

RsyncOSX is released in version 3.6.5 (updated 23 November 2016).

- [download](https://dl.dropboxusercontent.com/u/52503631/RsyncOSX.dmg) latest version of RsyncOSX
- shasum : fbe75fbb18e78afce17f67f6828c14724f306627
- see the [Changelog](https://github.com/rsyncOSX/Documentation/blob/master/Docs/Changelog.md) for info

<code>/usr/bin/shasum ~/PathToDownload/RsyncOSX.dmg</code> to verify hash

To install the application copy it to Desktop or any other folder in your home catalog. The application is installed and used at your own risk and developer accepts no responsibility for any errors, omissions or loss of data by using the application.

The application is signed with my Apple Developer ID certificate.

## Password-less logins

Backup to **remote servers** require ssh password-less logins (by ssh-keygen and ssh public and private keys). Here is how to [setup password-less](https://github.com/rsyncOSX/Documentation/blob/master/Docs/PasswordlessLogin.md) logins.

## Idea behind RsyncOSX

I have two MacBooks, one is used primarily at work and the other is my private. Data is backed up to server (NAS) at home and to one offsite servers. Both MacBooks and all backup locations are kept in sync. I am using my private MacBook for Pictures (I have about 100 GB of raw picture files). Whenever I have added new picture files or done some work on pictures, changes are backup up on all servers and then restored on my MacBook used at work. The rsync command-line tool is one of the best tools around for backup and synchronizing storage. A GUI ontop of rsync might hide all the details about parameters to rsync and make rsync execute the correct actions.

Some more details about the [idea](https://github.com/rsyncOSX/Documentation/blob/master/Docs/Idea.md) for RsyncOSX.