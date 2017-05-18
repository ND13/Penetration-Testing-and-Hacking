# **_Penetration Testing and Hacking_**
# Setting Up the Lab Environment from, *Penetration Testing: A Hands-On Introduction to Hacking*

## Requirements:
* Virtual Box [Here](https://www.virtualbox.org/wiki/Downloads) (I recommend installing the extension pack on this page as well)
* Latest Kali Linux [Here](https://www.kali.org/downloads/)
* [Penetration Testing A Hands-On Introduction to Hacking](https://www.nostarch.com/pentesting)

*This guide is specifically written for the book, without it some of the instructions will be unclear.

## Introduction
Sometime in early 2017 I went out and grabbed a copy of Georgia Weidman's, *Penetration Testing A Hands-On Introduction to Hacking*.
I spent a lot of time researching what would be the most useful materials to not only learn penetration testing/hacking but also I
wanted something that would help prepare me for the OSCP course and exam. The online consensus indicated that this was the book
that I should use. Unfortunately technology moves fast and things get outdated quickly. While the content in this book is awesome
it can definitely be a struggle to get through even the first chapter to get the lab environment up and running. However instead of
quitting (which I've been notorious of doing in the past) I decided to figure it out myself. I'm writing this guide in hopes that it
will serve as useful reference material for others who may have encountered the same problems. 

## Issues
The biggest issues I ran into revolved around using the 32 bit version of Kali Linux as it contained outdated software and I was unable
to get additonal software like Nessus, Hyperion, and Ming C Compiler to install or run at all. For example, in Nessus I couldn't get the
web interface to load or connect properly due to a connection error. I thought it might be the Ice Weasel browser so I attempted to 
download Google Chrome or Firefox which turned out to be incompatible or not supported on the 32 bit operating system. However when I
decided to download the **latest** version of Kali Linux, 16.2 64 bit version at the time, everything set up perfectly when installing and
configuring Nessus. At this point I figured it might be useful to just stick with the latest version of Kali, an alternative suggestion
made in the book on page 10.

The second issue I ran into was more of a personal preference issue. The book suggests using VMware Workstation Player as the virtualization
software, now this is great because it is free but the drawback is that it has a number of limitations most essentially for me was taking
snapshots of my VMs. I considered purchasing the upgrade but found it was out of my price range, thus I decided to use Virtual Box. Now for
my first disclaimer, the book recommends using VMware and I decided to use Virtual Box I don't know how that affects the rest of the material
in the book. Nothing indicates to me that this would be a problem but I'm not a professional when it comes to any of this so take that with a
grain of salt. If you want to stick to the book and use VMware that is fine once you get the Kali Linux virtual machine installed on the VM
the installation process for the addtional software will be the same. However for those of you who value snapshots and other features that
the free version of VMware Workstation Player may not allow access to I will provide instructions on how to get everything set up in 
virtual box in the following section. For those of you who already know how to install an operating system to a VM feel free to skip this
next section.

## Before Getting Started 
I've already mentioned it but I'm not going by the book exactly. I'm also not doing any of the mobile penetration testing installs because
my focus is the OSCP. I'm using Virtual Box instead of VMware. I'm using a new 64 bit installation of Kali as opposed to the 32 bit one used
in the book, I wouldn't be surprised if I run into more problems down the line so follow this at your own risk. The only reason I am creating
this with any confidence at all is because this is the method that I was able to use to get Kali running with all of the additional software.
You might encounter different problems based on a variety of factors use this as reference and motivation to just figure a way out to get 
things working. 

## Installing Kali Linux on Virtual Box

Once you get Virtual Box and the extension pack installed and the latest Kali Linux iso we can get started with setting up the VM using
the following steps.

1. Open up virtual box and click new on the upper left hand corner of the window.
2. Type in a name for your virtual machine, it can be anything you want as long as you can look at it and know what it is.
3. Select the type drop down menu and choose Linux, then the version drop down menu and select Debian 64 bit. Before you ask yes,
we are using Kali Linux but it is based on Debian. Click next.
4. Set the memory size to 2048MB and click next.
5. Select ‘Create a virtual hard disk now’ and click create.
6. Select VDI and then click next.
7. Select dynamically allocated and click next.
8. Leave the first input field with the name of your virtual machine the same. In the second input field either, adjust the slider 
or type into the box on the right to set the storage space to 25.00GB. Click create.
9. At this point your machine will appear to be created but there is still some configuration to get it up and running. 
Right click the machine in the upper left hand panel and select settings, on the left hand window click network, select the
‘attached to’ drop down menu and select ‘bridged adapter’. A field called ‘name’ will appear and most likely this will default
to whatever network interface you are using. Make sure it is correct, if not change it to the correct one and then click ok.
10. Once again right click the machine, and now choose storage. Under the ‘storage tree’ section click the little graphic that looks like a disc.
Now on the right side you should see a section called ‘attributes’, underneath this section to the right there will be another section 
that looks like a disc. Click this and select ‘Choose virtual optical disc file’ navigate to your downloads folder where the .iso of the
Kali Linux you downloaded earlier should be saved. Select it and click open. Then click ok.
11. Now your machine is ready to start up. Do this by double clicking the machine in the left hand panel. You’ll be presented with a 
boot menu where you can use the arrow keys to move down to ‘graphical install’ and hit enter.
12. Wait for the install environment to load and then select your language settings, location settings, and keyboard settings. It will take a few minutes 
to finish, and then ask you for a hostname. Again you can name this anything you want; I just left mine as ‘kali’.
13. It will ask for a domain, leave this blank and continue. It will ask you to set up a password for administrator access, choose what you like but make 
sure you remember it. Continue. Set up the time zone, continue.
14. next you’ll be asked to set up partitioning of the disk. Just select ‘Guided-use entire disk’ and continue. It will then show the disk we will be installing 
to, click continue. Next you will select ‘All files in one partition’ and continue. Finally you will see a summary of information about how the disk is 
partitioned and configured for the install, select finish partitioning and write changes to disk, continue. It will ask you to confirm, select yes and continue.
The install will start, it will take some time so be patient. 
15. The installation and configuration is almost done. Just a couple more steps. It will ask you if you would like to use a network mirror. Select yes and then 
continue, it will then say configuring package manager, this may take a few minutes as well, be patient.
16. Next you will be asked to install GRUB boot loader, select yes and continue. The next window will show ‘select device manually’ and your virtual hard drive.
Select your virtual hard drive and continue.
17. The install will finish after a few minutes, the system will reboot and you’ll be presented with the boot menu. Select the GNU Kali/Linux option and hit enter
or wait 5 seconds and it will automatically boot into Kali for you. You’ll be presented with a login screen, username is root and password is what you setup back in
step 13. Login and then you’ll be in a fresh install of Kali Linux. Make sure your network is connected and setup. You can refer to chapter 1 of the book for these 
steps as the commands for setting up and testing network connections remain the same.

## Installing Additional Software
###### Nessus
Now that we have Kali installed and configured we can start installing and setting up the software that we need to run in order to use the book to its potential. 
First we will set up Nessus, it is essentially the same set up as is in the book so feel free to refer to that. Remember that we’re using a Debian/Kali 64 bit operating
system, after you register and get your code make sure you download the correct version of Nessus. The book mentions that Nessus will automatically 
download to your root directory. Most likely this is not the case and it will download to your Downloads directory instead. Simply move to that directory in the terminal 
and then you can follow the rest of the steps in the book for installation. Also Nessus downloading plugins and initializing will take quite some time.

###### Ming C Compiler
Now let’s move onto the Ming C compiler. We’ll have to install the 64 bit version which means we cannot use the commands in the book. But no fear we can refer to this 
resource [here](http://www.hackingtutorials.org/exploit-tutorials/mingw-w64-how-to-compile-windows-exploits-on-kali-linux/).

Basically all we have to do is open up a terminal and type:

```
apt-get update
apt-get install mingw-w64
```

This should work without any issues; however some have reported having issues with being unable to locate the packages. This means most likely something is wrong with 
the repositories or sources for the package manager. No fear, here are a few resources to help if you run into those issues:

* http://docs.kali.org/faq/kali-sources-list-faq
* https://www.linkedin.com/pulse/kali-linux-fix-unable-locate-package-eyripidis-stefanidis
* https://forums.kali.org/showthread.php?28304-mingw-w64-on-Kali-2


**NOTE**: Ming C Compiler is used for compiling C code for Microsoft systems. Furthermore the one in the book is aimed at use for 32 bit systems which we will be using for the target 
windows VMs. The good news is this new 64 bit version we installed is usable on 32 bit systems you just have to use the correct command to compile it. 
You can use this resource [here](https://fedoraproject.org/wiki/MinGW/Tutorial#Compiling_code) in order to better understand what commands you’ll have to run when the time comes. 

###### Hyperion
Next is the Hyperion encryption program. We will be downloading this from the web and compiling it from source using our newly installed ming C compiler. 
However first things first the version in the book is no longer in use so use this command instead to download the 1.2 version:

`wget https://github.com/nullsecuritynet/tools/raw/master/binary/hyperion/release/Hyperion-1.2.zip`

That should download to your root directory or your Downloads directory. Be sure that you locate which directory it is and move to that directory in the terminal 
before the next step which is unzipping the file.

`unzip Hyperion-1.2.zip`

Now we will use the Ming C Compiler to compile everything like so

`i686-w64-mingw32-c++ Hyperion-1.2/Src/Crypter/*.cpp -o hyperion.exe`

It will take a few seconds but if everything compiles correctly you should get a blank prompt waiting for your next command in the terminal. 

###### Veil-Evasion
Next we will do veil evasion. The easiest way to do this is to follow this video:

https://www.youtube.com/watch?v=Mr8-YtEtkzs 

which takes you step by step and is very clear.

###### Ettercap
Last we make the changes Ettercap which is exactly as it is described in the book.

## Conclusion
As far as the Kali Linux virtual machine that should be it. I hope this helps anyone that might have issues like I did. If there is
any trouble setting up the remaining target machines in the book I can try putting together a guide for those as well. I most likely will
end up doing so if I run into some more trouble myself. 
