---
title: Network 3D Printer with Windows 10 IoT Core
ms.date: 09/05/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about how to turn your Windows 10 IoT Core device into a print server and connect your 3D Printer to it.
keywords: windows iot, 3D, 3D printer, print server, network 3D printer
---

# Network 3D Printer with Windows 10 IoT Core

Turn your Windows 10 IoT Core device into a print server and connect your 3D Printer to it. You will be able to access your printer wirelessly from other devices.

## 1. Install Windows 10 IoT Core on your device
___
Before you start, you will need:

* A board with the latest version of Windows 10 IoT Core Insider Preview installed. Follow the [Get Started guide](https://developer.microsoft.com/en-us/windows/iot/getstarted) to get the IoT Dashboard app and install Windows 10 IoT Core.
* A 3D Printer compatible with our Network 3D Printer app:

    * Lulzbot Taz 6
    * Makergear M2
    * Printrbot Play, Plus and Simple
    * Prusa i3 Mk2
    * Ultimaker Original and Original+
    * Ultimaker 2 and 2+
    * Ultimaker 2 Extended and Extended+
    * CraftBot 2
    * CraftBot PLUS
    * LulzBot Mini
    * Velleman K8200

## 2. Connect your 3D Printer to your device
___
* Plug-in your 3D printer to your Windows 10 IoT Core board using the USB cable.

    ![Connect your 3D Printer to the device](../media/3DPrintServer/connect-3d-printer.png)

* Open the IoT Dashboard app and verify that your device shows up in the **My devices** tab.

    ![Verify that your device shows up in IoT Dashboard](../media/3DPrintServer/selectDevice.png)

## 3. Deploy the Network 3D Printer app
___
* In IoT Dashboard, click on the **Try some samples** section.
* Select the Network 3D Printer sample app.

   ![Install 3D Network Printer](../media/3dprintserver/dashboard-samples.png)

* Select your 3D Printer model and press the **Deploy and run** button to deploy the app to your IoT Core device.

    ![Install 3D Network Printer 1](../media/3dprintserver/dashboard-app.png)

    [LulzBot TAZ 6 image](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) by [Aleph Objects, Inc.](https://www.alephobjects.com/) is licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

    If you wish to install a custom printer select the "Custom" option from the list of Printers. Custom 3d Printers need a configuration xml called the PrintDeviceCapabilities.xml file to be provided to correctly connect and print to the 3d printer. A sample PrintDeviceCapabilities.xml file can be found in [Sample configuration XML](/windows-hardware/drivers/3dprint/sample-configuration-xml)

   The minimum changes you need to make in the xml file are to update the following sections with the correct values specific to your compatible printer.

These values specify the print bed dimensions of your 3d printer to the slicer when processing the 3d model
```
    <psk3d:Job3DOutputAreaWidth>200000</psk3d:Job3DOutputAreaWidth>
    <psk3d:Job3DOutputAreaDepth>200000</psk3d:Job3DOutputAreaDepth>
    <psk3d:Job3DOutputAreaHeight>200000</psk3d:Job3DOutputAreaHeight>
```

The value in the psk3dx:baudrate xml tag controls the specific baud rate to use while communicating with the 3d printer from the raspberry pi3. Set the appropriate baud rate specific to your 3d printer.

```
\<psk3dx:baudrate\>115200</psk3dx:baudrate>
```

The other values in the PrintDeviceCapabilities xml are used to notify the slicer in the 3d print driver to fine tune how it works with your specific compatible printer.
More information on all these values are provided [here](/windows-hardware/drivers/3dprint/slicer-settings).



## 4. Add your 3D Printer
___
* Go to your Windows 10 PC and go to **Settings** -> **Devices** -> **Printers & Scanners**.
* Press **Add a printer or scanner**.

     ![Windows Settings Add Device](../media/3dprintserver/add-printer.png)

* Select your 3D Printer and press **Add device**. The printer will install automatically.

     ![Windows Settings Add Device 1](../media/3dprintserver/add-device.png)

Congratulations your printer is now installed and will behave exactly as if it was connected with a USB cable.
You can now print to it using [3D Builder](https://msdn.microsoft.com/windows/hardware/mt561568.aspx).
