---
title: Installing VMWare Player on Ubuntu 22.04 LTS
author: rahul-bhadani
tags:
  - linux
  - vmware
  - ubuntu
---

In 2024, VMware made some significant changes to its product lineup. VMware Workstation Player and VMware Fusion Player were discontinued. However, if you are still looking to download VMWare Player, there is still a way to do that.

In this tutorial, I will walk you through how to download VMWare Player. This tutorial is based on software packages available to download from https://softwareupdate.vmware.com/cds/vmw-desktop/player/ at the time of writing. I have saved a version of VMWare Player 17.5.1 on https://github.com/rahulbhadani/medium.com/releases/tag/VMWarePlayer17.5.1 in case Broadcomm decided to purge the webpage.

Once you download, VMWare Player 17.5.1 zip file, extract it and run the following inside the extracted folder:

<code>
sudo bash VMware-Player-17.5.1-23298084.x86_64.bundle
</code>

It will install the player, however, you might encounter an error:

![Alt text](/images/error.png)

In order to rectify this error, follow the guideline below:
<code>
git clone https://github.com/mkubecek/vmware-host-modules
cd vmware-host-modules
git switch workstation-17.5.1
make
sudo make install
</code>

This was taken from https://community.broadcom.com/vmware-cloud-foundation/discussion/ubuntu-22044-lts-module-compile-fails. The above github repository for the branch 17.5.1 also been stored in https://github.com/rahulbhadani/medium.com/releases/tag/VMWarePlayer17.5.1.

This will install some necessary packages required to fix the error shown previously.

Next, you will be able to virtualize your favorite OS, in this case, say another Ubuntu 20.04

However, after sucessful virtualization, when you try to boot your virtual Ubuntu, you may encounter the following error:


![Alt text](/images/error2.png)

To solve this problem follow the steps below:

In the command line,

**Step 1:**

type:

<code>
vmware-modconfig --console --install-all
</code>

In 6.9 kernel, the above method might give an error

<code>
./arch/x86/include/asm/timex.h:12:24: error: implicit declaration of function ‘random_get_entropy_fallback’; did you mean ‘random_get_entropy’? [-Werror=implicit-function-declaration]
   12 |                 return random_get_entropy_fallback();
      |                        ^~~~~~~~~~~~~~~~~~~~~~~~~~~
      |                        random_get_entropy
</code>

To resolve that, I performed the following step:

*a.*

<code>
cd vmware-host-modules
</code>

*b.*

<code>
sudo cp -v vmmon.tar vmnet.tar /usr/lib/vmware/modules/source/  
</code>

*c. Then do the following*

<code>
sudo vmware-modconfig --console --install-all
</code>

The solution was proposed in https://www.linkedin.com/pulse/resolving-vmware-kernel-module-issues-ubuntu-2404-lts-vishal-ravi-xsfpc

**Step 2:**

then

<code>
openssl req -new -x509 -newkey rsa:2048 -keyout MOK.priv -outform DER -out MOK.der -nodes -days 36500 -subj "/CN=VMware/"
sudo mokutil --import MOK.der
</code>

It may ask you to enter a password. Enter and do not forget that password.

Then, reboot your machine.

Upon rebooting, it might ask for the password that you had entered above. Provide that password.

After successful reboot and login, open your terminal and enter the following commands:

<code>
sudo /usr/src/linux-headers-`uname -r`/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n vmmon)

sudo /usr/src/linux-headers-`uname -r`/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n vmnet)

sudo modprobe -v vmmon

sudo modprobe -v vmnet

sudo vmware-networks --start
</code>

Once it is down, now you can open your VMWare Player and boot your Virtual OS.

Enjoy!