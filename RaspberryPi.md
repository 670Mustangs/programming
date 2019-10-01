---
title: Raspberry Pi
parent: Coprocessors, Sensors, and LEDs
grand_parent: 2019 Tech Binder
nav_order: 1
---

![Pi](https://www.raspberrypi.org/homepage-9df4b/static/eef5d5d91acb34be0d7443b02cece1d1/bc3a8/8c67a3e02f41441dae98f8b91c792c1e1b4afef1_770a5842.jpg)

We use the Raspberry Pi to handle driver camera streams, as well as running a Python script which puts the vision
error code to NetworkTables if appropriate cameras are not found. 

The Raspberry Pi is being used to run driver camera streams as well as a python script that puts the vision error code to network tables if appropriate cameras are not found.

### Start scripts on boot<br>
The streaming script (written in bash) and the Python script are set to run when the Pi turns on. The script called `startup.sh` calls both scripts and is set to run on bootup with the `crontab` command. To set up a script to run on boot:
1. Open up a terminal window and type `crontab -e`
2. Select your editor of choice
3. Add the following line to the bottom of the file: `@reboot ` followed by the name of your script (for us this line looks like `@reboot /home/pi/startup.sh`)

### Static IP Address<br>
A static IP address was given to the Pi so that its IP address is the same regardless of which router it is connected to. This is useful especially for testing purposes since you may not always connect the Pi to the same router, in which case you would have to scan for its IP address each time. Also, since we are using mjpg-streamer for driver camera streams, which requires us to know the IP address of the device the cameras are plugged into, the static IP was necessary for the streams to function seamlessly. Use the instructions at [https://www.modmypi.com/blog/how-to-give-your-raspberry-pi-a-static-ip-address-update](https://www.modmypi.com/blog/how-to-give-your-raspberry-pi-a-static-ip-address-update) to set a static IP address for your Pi.

*Refer to the page on Driver Cameras for details on camera streaming* <br><br>

### Disable WiFi<br>
1. Open a terminal window and run `systemctl disable wpa_supplicant`
2. Open `/boot/config.txt` in an editor of your choice
3. Add `dtoverlay=pi3-disable-wifi` to the file

Credit to [https://irulan.net/disable-wifi-and-bluetooth-on-raspberry-pi-3/](https://irulan.net/disable-wifi-and-bluetooth-on-raspberry-pi-3/)

### Use this process to clone the contents of one SD card onto another<br>
This can be used to create two copies of an SD card for use on two Pi’s at once

*NOTE: this process requires Win32 Disk Imager to be installed*

SD1 = the SD card being copied from (the original)<br>
SD2 = the SD card being copied to (the new one)

**Do this with SD1:** <br>
Plug into laptop using an adapter if necessary <br>
Read the contents of the [D:] drive of the card to a convenient local destination using Win32 Disk Imager <br>
Unplug SD card from laptop <br><br>
**Then do this with SD2:** <br>
Plug into laptop using an adapter if necessary <br>
Windows should suggest formatting the disk, go ahead and do that <br>
Follow the instructions on this page to remove all partitions on the SD card: http://oddsnsods.net/blog/?p=100 <br>
Use Win32 Disk Imager to write the file read from SD1 in the previous part to the [E:] drive of the SD card <br>

Insert SD2 into the Pi, turn it on, and run ‘ls’ in the root directory to ensure all contents were copied over
