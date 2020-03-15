![logo](https://github.com/Botspot/Pi-Power-Tools/blob/master/icons/logo-64.png?raw=true)  
# Pi Power Tools
## The Ultimate Swiss Army Knife for Raspbian Disk Images and SD Cards.

### No other tool can do any of these:
 - **Boot** - Powered by [Vdesktop](https://github.com/Botspot/vdesktop). Runs the disk image in a virtual machine.
 - **Flash** - Flashes Raspbian directly from the Internet to the selected device.
 - **Mount** - Full control to manage loop devices and mountpoints.
 - **Edit** - Auto-creates a loop device for the disk image then opens it with Gparted.
 - **Resize** - Expand or shrink a disk image, thanks to RonR's [Image-utils](https://www.raspberrypi.org/forums/viewtopic.php?t=247568).

## To install:
#### Run this in the terminal:
`wget -O - https://raw.githubusercontent.com/Botspot/Pi-Power-Tools/master/update | bash`  

After installing, Pi Power Tools can be launched from the Menu:
![menu](https://i.ibb.co/PQthp6N/menu.png)  

## To uninstall:
```
sudo apt purge gparted yad systemd-container xserver-xephyr expect
rm -rf ${HOME}/Pi-Power-Tools ${HOME}/Pi-Power-Tools.old
rm ${HOME}/Desktop/ppt.desktop ${HOME}/.local/share/applications/ppt.desktop
```
---
# Instructions:
Pro tip: Most buttons display an explanation if you move your mouse over them.
 - **Home**  
![home page](https://i.ibb.co/vz4yR40/home.png)  
The menu button opens this window by default. Enter IMG Mode or USB Mode from here. The Update button will appear if an update is available.  
 - **Settings**  
Customize some aspects of Pi Power Tools.  
Currently, you can change what the menu button opens by default (Flash, IMG Mode, USB Mode, and Home), if the Boot Button launches the Desktop, and whether or not to run `zerofree` when the Shrink Button is clicked.

 - **USB Mode**  
Manage storage devices connected to your Pi.  
![usb mode](https://i.ibb.co/vJ68mRY/usb.png)  
Select a drive in the list, then click an action button on the bottom.  
*Please note that your Pi's root device (/dev/mmcblk0) cannot be flashed or booted.*  
Buttons explanations:  
 - - Home: Back to the home window.  
 - - Refresh: Check for any newly inserted storage devices.  
 - - Flash: Copy everything from an img to the selected device.  
 - - Boot: Attempt to "boot" the selected device using a virtual desktop. Instead of a Virtual Machine, this method of booting runs at 100% native speed (no emulation), because the guest runs the same kernel as the host device. Therefore, only Raspbian is supported, as other OSes require other kernels.  
 - - View: Mounts the device to `/media/pi/pi-power-tools`.  
![view files](https://i.ibb.co/RgbKJff/view-files.png)  
Intended for Raspbian devices only, as this button assumes there are 2 partitions. (and mounts partiton 1 to `/media/pi/pi-power-tools/boot`)
 - - Edit: Modify the partitions using Gparted.
![gparted](https://i.ibb.co/pww2C9h/gparted.png)
 - **IMG Mode**  
Customize Raspbian Images.
![img mode](https://i.ibb.co/yQnT2sC/img-mode.png)  
Before you can see that above page, you first have to select an img.  
![img mode page 1](https://i.ibb.co/TLcT6cD/img-mode1.png)  

Click the arrow to see previously used disk images.

---
## Action buttons of the Main Window:  

 - **Refresh**  
![Refresh button](https://i.ibb.co/94R5XHV/refresh.png)  
Click this if you plugged in a USB drive **after** starting Pi Power Tools.  

 - **Flash**  
*This is the only action button that does not require a device to be selected first.*  
First page:  
![Flash tool first page](https://i.ibb.co/j4yNNc6/flash1.png)  
Select an input disk image and an output usb drive. Notice that the filesystem root device is not listed.  
Pro tip: *In the `From` field, you can paste the path to a ZIP file.*  
Click the arrow on the right to view all available flash-from devices.  
If you chose to Download, this window will appear next asking which download program you want.  
![Flash tool second page](https://i.ibb.co/dmL3b7s/flash2.png)  
Depending on two factors, the flash time drastically varies:  
Fast Internet + fast usb device = **300 seconds or less**.  
Slow usb device or slow Internet connection = > **1500 seconds**.  

 - **Boot**  
Select a device (img file or usb drive), then click Boot. With this handy button, you can customize a disk image before flashing it to your SD card.  
A Console will appear and display the boot text like this:  
![boot console](https://i.ibb.co/Ypv0Wj3/terminal.png)  
*Under certain circumstances, Vdesktop will ask permission to change a UUID or a machine-id. This rarely corrupts anything, so typing `y` is usually appropriate.*  
After it has booted, a window similar to VNC will open and display the desktop.  
![xephyr](https://i.ibb.co/j4snZ8z/xephyr.png)  
*It is a known issue that the browser crashes with the `Aw, Snap!` error.*  

 - **View**  
Mounts the selected device to `/media/pi/pi-power-tools`.  
![view dialog](https://i.ibb.co/7r3Sc5Z/view-dialog.png)  
When you close the above window, the selected device will be unmounted (ejected).  

 - **Edit**  
Lets you edit the partitions of the selected device.  
![gparted opening a disk image](https://i.ibb.co/c1YNB2K/gparted.png)  
If Gparted is not already installed, you will be prompted to install it.  
---
## Image-specific tool buttons:  
![screenshot](https://i.ibb.co/0ccDxC9/image-specific-tools.png)  
 - **Image-Utils GUI**  
[RonR's image-utils](https://www.raspberrypi.org/forums/viewtopic.php?t=247568) wrapped in a graphical frontend.  
![home page](https://i.ibb.co/1q0SMFV/image-utils1.png)  
Paste in a location to a disk image, then click an action button. The **settings tab** lets you customize some aspects of the tools.  
![image-utils settings tab](https://i.ibb.co/wBfntjF/image-utils2.png)  
 - **Advanced Mount**  
Fine-tune control over loop devices and mountpoints for disk images.  
Select the disk image you want:  
![image-utils settings tab](https://i.ibb.co/Tk5R1wv/advmount-page-1.png)  
If there are multiple loop devices associated with it, you will be prompted to choose one. You can also delete unwanted loop devices:  
![image-utils settings tab](https://i.ibb.co/84zD9yk/advmount-page-2.png)  
Now you can mount and unmount each partition where you want to:  
![image-utils settings tab](https://i.ibb.co/m4d6YjW/advmount-page-3.png)  
When you're finished, be sure to click **Delete** to detach the loop device.
---
## For those who are interested in the inner workings of Pi Power Tools:
Pro tip: *There are many comments in the shell scripts. Not only does this help me while debugging, it also makes most of it self-explanatory.*  
### The filesystem is set up like this:
```
Pi-Power-Tools #This is the main folder that stores everything.
  #Scripts:
    advmount          #Advanced img mount tool
    image-utils-gui   #RonR's image-utils gui program. (The actual scripts are stored in the image-utils folder.) 
    installgui        #This prompts for packages to be installed
    flash             #This is the flash tool
    update            #This script is what installs/updates Pi Power Tools.
    pi-power-tools    #This is the main tool.
  #Other files:
    image-utils.conf  #Saves the settings of image-utils.
    installedpackages #Keeps a record of what the update script installed.
    README.md         #This is what you're reading right now.
    version           #Lets Pi Power Tools keep track of what version it is to see when an update is available.
    imglist           #Stores previously used disk images.
  #Folders:
    icons             #Stores all the icons used in the user interfaces of Pi Power Tools.
    image-utils       #Ships empty, but the get-latest-image-utils script populates this folder with the below files:
      #Scripts:
        image-backup      #Backs up the running operating system to the specified disk image. Disk image must be located on /mnt or /media.
        image-check       #Returns a bunch of data about the specified disk image.
        image-compare     #Lists the files image-backup would copy over if run.
        image-mount       #Mounts an img to a specified mountpoint. Not available in the GUI tool since it is buggy.
        image-set-ptuuid  #Not used in the GUI tool.
        image-shrink      #Makes the specified image as small as possible. An optional second word specifies additional free space in MB.
      #Other files:
        README.txt        #RonR wrote these instructions for image-tools.
    vdesktop        #Ships empty, but installgui populates this folder with the below files:
      #Scripts:
        rc.local    #This is temporarily mounted to the selected device during boot to display the blue message in the boot text.
        vdesktop    #The main boot script
      #Other files:
        profile     #This is temporarily mounted to the selected device to start the desktop session.
        autologin   #The existence of this file tells vdesktop to login automatically.
        shadow      #This is mounted to /etc/shadow of the selected device to ensure the pi's password is raspberry.
        version     #Lets Vdesktop keep track of what version it is to see when an update is available.
        README.md   #The instructions for running vdesktop standalone
```
### Basic script design:
 - The scripts all use YAD to handle the user interface.* I found that Zenity was way too limited.  
`*` Okay, `installgui` and `update` *do* use zenity because Raspbian does not include YAD by default.

## Q&A
 - Q: Unique logo. What inspired you?  
![logo](https://github.com/Botspot/Pi-Power-Tools/blob/master/icons/logo-64.png?raw=true)  
**A: It's a combination of BB-8, the RPi logo, and a saw blade to convey a power tool.**  
 - Q: What made you develop this tool?  
**A: I while back, I wanted to download Raspbian, uninstall all programming tools from it, add a chrome extension to the browser, then flash it to a SD card. It took several days to fumble around with terminal commands. It was so ridiculously tedious, that I realized there must be a better way.**  
 - Q: How long did it take to program this?  
**A: Several months. But it was entirely worth the effort.**  
