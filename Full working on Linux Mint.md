## INTRODUCTION

I have tried Ubuntu, Arch Linux, Manjaro and Linux Mint on this Laptop and, in my opinion, Linux Mint is the better and most stable Linux distro for this laptop.

My laptop has the wifi card AX500, that is the most conflictive hardware for Arch distros. 

Since the laptop has the [certificate](https://ubuntu.com/certified/202007-28063) from Ubuntu, I think is a good decision use an Ubuntu based distribution for better stability. So, Ubuntu, Linux Mint, MX Linux, Elementary OS,... would be good options and the installation will be like this. 

## BASIC STUFF, DELL REPOSITORIES AND KERNEL (BASIC HARDWARE)

[Download](https://linuxmint.com) and install Linux Mint using the last ISO and [Rufus](https://rufus.ie/en/) for create the bootable USB.

After the install, WIFI and other hardware will not work. You need to connect to Internet with a wire connection (f.e. with your smartphone).

Download and install [from here](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta-oem-5.6):

          linux-headers-oem-20.04_5.6.0.1007.7_amd64.deb
          
          linux-image-oem-20.04_5.6.0.1007.7_amd64.deb
          
          linux-tools-oem-20.04_5.6.0.1007.7_amd64.deb
          
          linux-oem-20.04_5.6.0.1007.7_amd64.deb

Download and install [from here](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/):

          linux-firmware_1.199_all.deb
          
After that, add repositories:

          $ sudo nano /etc/apt/sources.list.d/somerville-dla-team-ubuntu-ppa-bionic.list
      
And paste this:

          deb http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu bionic main
          # deb-src http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu bionic main
          # deb-src http://ppa.launchpad.net/somerville-dla-team/ppa/ubuntu bionic main
         
Also:
               
         $ sudo nano /etc/apt/sources.list.d/focal-oem.list
           
And paste this:

          deb http://oem.archive.canonical.com/ focal oem
          #deb-src http://oem.archive.canonical.com/ focal oem
          
And also:

          sudo nano /etc/apt/sources.list.d/oem-somerville-bulbasaur-meta.list
          
And paste this:

          deb http://dell.archive.canonical.com/ focal somerville
          # deb-src http://dell.archive.canonical.com/ focal somerville
          deb http://dell.archive.canonical.com/ focal somerville-bulbasaur
          # deb-src http://dell.archive.canonical.com/ focal somerville-bulbasaur
         
Now, update all:

          $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F992900E3BBF9275 F9FDA6BED73CDC22 F9FDA6BED73CDC22 78BD65473CB3BD13
          $ sudo apt-get update
          $ sudo apt-get dist-upgrade
          $ sudo apt-get install ubuntu-oem-keyring oem-somerville-meta oem-somerville-bulbasaur-meta
          
Reboot and hardware like wifi will work.

## FINGERPRINT

Install needed packages:

          $ sudo apt install libfprint-2-tod1-goodix tlp-config
 
Add a fingerprint:
 
          $ fprintd-enroll
          
Check your fingerprint added:
 
          $ fprintd-list
      
Verify your fingerprint:
 
          $ fprintd-verify
          
## FACE RECOGNITION

Install needed packages:

          $ sudo add-apt-repository ppa:boltgolt/howdy
          $ sudo apt update
          $ sudo apt install howdy
          
Configure the path of the camera:
          
          $ sudo howdy config
          
Change the device_path= by:
          
          device_path = /dev/video0
          
Add your face:

          $ sudo howdy add
          
Check it is correctly added with:

          $ sudo howdy list
          
## LOGIN WITH FINGERPRINT AND/OR FACE RECOGNITION

Install needed packages:

          $ sudo apt install libpam-fprintd
          
Configure with your preferences:

          $ sudo pam-auth-update
    
Check or uncheck your prefered login auth with SPACE BAR.

#### And that's all, your Dell XPS 13 (9310) is full working in Linux Mint.

## CREDITS

https://torlenor.org/linux/2020/10/31/mint_on_dell_xps_13.html

https://wiki.archlinux.org/title/Dell_XPS_13_(9310)

https://www.dell.com/community/XPS/XPS-13-9300-Does-fingerprint-reader-work-on-linux/m-p/7628310/highlight/true#M63982

https://itsfoss.com/face-unlock-ubuntu/

https://dyn.manpages.debian.org/stretch/fprintd/fprintd-enroll.1.en.html

https://www.reddit.com/r/linuxmint/comments/hmkj7h/fingerprint_scanner_on_lm20/
          