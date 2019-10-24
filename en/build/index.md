---
title: "Build"
description: You may want to fetch data and render it on the server-side. Nuxt.js adds an `asyncData` method that lets you handle async operations before setting the component data.
---


# RK3399 Android Image Update SOP


## Update Android Image on Windows OS


<div class="Alert Alert--nuxt-blue">

<b>Pre- requisites</b>

</div> 

- **Windows_Tool.zip** 
- **Android Images for RK3399 platform:** 
        boot.img
        kernel.img
        MiniLoaderAll.bin
        misc.img
        oem.img (Android 8.1 only)
        parameter.txt
        recovery.img
        resource.img
        system.img
        trust.img
        uboot.img
        vendor.img (Android 8.1 only)


<div class="Alert Alert--nuxt-blue">

<b>Update Image</b>

</div> 

- **Unzip Windows_Tool.zip .** 
- **Execute AndroidTool.exe in administrator mode.** 
- **Put the device into LOADER or MASKROM state and connect it to Windows PC with USB cable.** 
- **The UI of AndroidTool.exe should show “Found One LOADER Device” or “Found One MASKROM Device”.** 
- **Set the path of all the Android images (oem.img and vendor.img only exist in Android 8.1), and check the boxes on UI.** 
- **Click “Run” button on UI to update images.** 

## Update Android Image on Linux OS


<div class="Alert Alert--nuxt-blue">

<b>Pre- requisites</b>

</div> 

- **Linux_Tool.zip**
- **Android Images for RK3399 platform:**
        boot.img
        kernel.img
        MiniLoaderAll.bin
        misc.img
        oem.img (Android 8.1 only)
        parameter.txt
        recovery.img
        resource.img
        system.img
        trust.img
        uboot.img
        vendor.img (Android 8.1 only)


<div class="Alert Alert--nuxt-blue">

<b>Update Image of Android 7.1</b>

</div> 

- **Unzip Linux_Tool.zip .**
- **Put the device into LOADER state and connect it to Linux PC with USB cable.**
- **Execute the following Linux shell command under the folder rockdev_71/**
        sudo chmod 777 *

- **Put all the release image files into the folder rockdev_71 Image/**
- **Execute the following Linux shell command under the folder rockdev_71/ to get update.img .**
        ./mkupdate.sh
- **Move update.img to folder Linux_Upgrade_Tool_71/**
- **Execute the following Linux shell command under the folder Linux_Upgrade_Tool_71/**
        sudo chmod 777 *
- **Execute the following Linux shell command under the folder Linux_Upgrade_Tool_71/ to update image**
        sudo ./upgrade_tool uf update.img


<div class="Alert Alert--nuxt-blue">

<b>Update Image of Android 8.1</b>

</div> 

- **Unzip Linux_Tool.zip .**
- **Put the device into LOADER state and connect it to Linux PC with USB cable. (If the device runs on Android 7.1, it should be put into MASKROM state to update Android 8.1 images)**
- **Execute the following Linux shell command under the folder rockdev_81/**
        sudo chmod 777 *
- **Put all the release image files into the folder rockdev_81/Image/**
- **Execute the following Linux shell command under the folder rockdev_81/ to get update.img .**
        ./mkupdate.sh
- **Move update.img to folder Linux_Upgrade_Tool_81/**
- **Execute the following Linux shell command under the folder Linux_Upgrade_Tool_81/**
        sudo chmod 777 *
- **Execute the following Linux shell command under the folder Linux_Upgrade_Tool_81/ to update image**
        sudo ./upgrade_tool uf update.img


# Rockchip RK3399 Platform Android 7.1

## To Run a Flash Tool

<div class="Alert Alert--nuxt-blue">

<b>Pre-requisites</b>

</div> 

- **Prepare an image compressed file. Its name will be like**
        Android_7.1_{OS_IF}.{PLF_IF}.{PJ_IF}.{BN}.zip
- **I.{OS_IF} is OS Information; e.g. AD71D which AD means Android, 71 means Android 7.1 and D means userdebug. If image is user build the latest character will be U, engineer build will be E -**
- **II. {PLF_IF} is Platform Information; e.g. RK3399**
- **III. {PJ_IF} is Project Information; e.g. RICO**
- **IV. {BN} is Build Number; e.g. 0,1,2,...,N**
- **2) Unzip this compressed file to D:\RKImages_RICO in a Windows system. The image files are as follows**



<div class="Alert Alert--nuxt-blue">

<b>In Windows Host</b>

</div> 

- **1) Download the Android Flash Tool of Rockchip. The latest version is AndroidTool_Release_v2.42.zip**
- **2) Unzip the compressed file to D:\AndroidTool_Release_v2.42 in a Windows system. The content will be as follows**

- **3) Run the AndroidTool.exe. The view of it will be like the following**

- **Be sure the tool points the paths of all images to the correct locations. If not, you can redirect the paths by clicking the blue field next to the Path field.**


## To Install Image

<div class="Alert Alert--nuxt-blue">

<b>Install Image to RICO Board</b>

</div> 


- **1) Disconnect any power source from your device board**
- **2) Connect your Windows host and device board via USB Type C cable**
<!-- USB Type C -->

- **3) Hold the Recovery button first and then connect 12V power source**
<!-- Recovery
12V -->

- **4) You should see the Android Flash Tool displaying that it discovers a LOADER device**

- **5) Repeat from Step 1 to Step 4 if you cannot see the LOADER text on the status bar of the Android Flash Tool**
- **6) Click 'Run' to start flashing images if you make sure all the paths of images are correct**


- **The Android Flash Tool will lock all buttons and you can see the flashing progress on the right text box**
- **7) System will automatically reboot and boot up to Android Home**



<!-- The result from asyncData will be **merged** with data.

```js
export default {
  data () {
    return { project: 'default' }
  },
  asyncData (context) {
    return { project: 'nuxt' }
  }
}
``` -->

<!-- ## RICO 3399


- **Build U-Boot**
            cd u-boot
            make rk3399_defconfig; make ARCHV=aarch64.

- **Build Kernel**
            cd kernel
            make ARCH=arm64 rockchip_defconfig -j8; make ARCH=arm64 rk3399-sapphire-excavator-edp.img -j12

- **Build System**
            source build/envsetup.sh; lunch rk3399_mid-userdebug; make -j16; ./mkimage.sh
 -->


<!-- - **Type:** `Function`


<div class="Alert Alert--nuxt-green">

<b>Info:</b> Please visit the [async data guide](/guide/async-data) as well!

</div>


`asyncData` is called every time before loading the **page** component and is only available for such.
It will be called server-side once (on the first request to the Nuxt app) and client-side when navigating to further routes. 
This method receives the [`context`](/api/context) object as the first argument, you can use it to fetch some data and return the component data.


The result from asyncData will be **merged** with data.

```js
export default {
  data () {
    return { project: 'default' }
  },
  asyncData (context) {
    return { project: 'nuxt' }
  }
}
```

<div class="Alert Alert--orange">

<b>Warning:</b> You **don't** have access to the component instance through `this` inside `asyncData` because it is called **before initiating** the component.

</div> -->
