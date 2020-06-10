# Huawei P8 Lite (alice)

# Sources needed
### Kernel
This device tree is intended to be used with this kernel repo:

See: https://github.com/DarkJoker360/android_kernel_huawei_alice

branch: lineage-15.1
### Vendor
This device tree is intented to be used with this vendor repo

https://github.com/DarkJoker360/android_vendor_huawei_alice

branch: lineage-15.1


### Set up local manifest.

The local manifest is different for every device. It contains those repos that are device specific, where as the ROM code you just "repo sync'd" is code that is general to any device.

Execute the following commands in a linux terminal:
```bash
mkdir /home/$USER/los/.repo/local_manifests
gedit /home/$USER/los/.repo/local_manifests/alice.xml
```
Copy the following into alice_oreo.xml, save and close.
```bash
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
  <project name="DarkJoker360/android_kernel_huawei_alice" path="kernel/huawei/alice" remote="github" revision="lineage-15.1"/>
  <project name="masemoel/device_huawei_alice" path="device/huawei/alice" remote="github" revision="master"/>
  <project name="DarkJoker360/android_vendor_huawei_alice" path="vendor/huawei/alice" remote="github" revision="lineage-15.1"/>
</manifest>
```

Execute the following commands in a linux terminal:
```bash
cd /home/$USER/los
repo sync
```

NOTE: Yes we are syncing again and No, it shouldn't take quite as long. Every time you repo sync just new data is downloaded. So we are downloading the 4 repo's we just put in and any 
updates that may have occured to the repo's we already have.

### Building

Now you will want to apply the repo patches. These patches modify code in the ROM to work with this device.
Execute the following commands in a linux terminal:
NOTE: you have to run the chmod command if you have some issues on the script 
```bash
cd /home/$USER/los/device/huawei/alice/patches
chmod a+x 'patches.sh'
cd /home/$USER/los
./device/huawei/alice/patches/patches.sh
```
NOTE: If you are going to be offline while you are building, you will need download some prebuilts first.
```bash
cd /home/$USER/los
make fetchprebuilts
```
Time to build!
It may take anywhere from 5 hours to 15 hours depending on system specs for a complete build.
Execute the following commands in a linux terminal:
```bash
cd /home/$USER/los
. build/envsetup.sh
lunch dot_alice-userdebug
make bacon
```

Huawei P8Lite detailed specifications:
======================================

Basic         |Spec Sheet
-------------:|:--------------------------------------------------------------------------------------------------------------------------
Network	      | GSM / HSPA / LTE
Launch	      |2015, April
Body	      |143 x 70.6 x 7.7 mm (5.63 x 2.78 x 0.30 in); 131 g (4.62 oz); Dual SIM (Nano-SIM/ Micro-SIM, dual stand-by)
Display	      |IPS LCD capacitive touchscreen, 16M colors; 5.0 inches; 720 x 1280 pixels; Corning Gorilla Glass 3
Platform      |Android OS, v5.0.2 (Lollipop), upgradable to v6.0 (Marshmallow)
Chipset	      |HiSilicon Kirin 620
CPU	      |Octa-core 1.2 GHz Cortex-A53
GPU	      |Mali-450MP4
Memory	      |16 GB, 2 GB RAM; microSD, up to 256 GB (uses SIM 2 slot)
Rear Camera   |13 MP, f/2.0, 27mm, autofocus, dual-LED flash, Geo-tagging, touch focus, face/smile detection, panorama, HDR, 1080p@30fps
Front Camera  |5 MP, 720p
Sound	      |- Active noise cancellation with dedicated mic
WLAN	      |Wi-Fi 802.11 a/b/g/n, WiFi Direct, hotspot
Bluetooth     |v4.0, A2DP, EDR, LE
GPS	      |Yes, with A-GPS, GLONASS
NFC	      |Yes
Radio	      |FM radio
USB	      |microUSB v2.0
Sensors	      |Accelerometer, proximity, compass
Battery	      |Non-removable Li-Ion 2200 mAh battery
Colors 	      |Black, White, Gold


![Huawei P8Lite](http://cdn2.gsmarena.com/vv/pics/huawei/huawei-p8-lite.jpg "Huawei P8Lite")
