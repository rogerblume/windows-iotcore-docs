---
title: Mobile Broadband Connection
ms.date: 06/12/2018
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Use Mobile Broadband Connection for Windows 10 IoT Core. Use the MBBConnect tool to help set up configurations for mobile broadband connection in IoT Core.
keywords: windows iot, MBB, mobile broadband connection
---

# Mobile Broadband Connection

Mobile Broadband Connection is supported on [Windows 10 IoT Core](http://windowsondevices.com). If your IoT gateway supports the mobile broadband modem module, you can use the `MBBConnect` tool to help set up configurations for mobile broadband connection in IoT Core.

`MBBConnect` retrieves the relevant information for connect, such as subscriber ID, SIM ICC ID, interface name, and home provider name, etc. Then, it creates the connection profile. The only thing you’ll need to do is to provide APN, and it will set up connection automatically.

`MBBConnect` is developed and tested with MinnowBoard Max based IoT gateway running IoT Core version 16299 and the mobile broadband modem module with the SIM card from major telecom provider in Taiwan.

### Usage

1. Copy `MBBConnect.exe` to IoT gateway.

   * [FTP](./ftp.md)

2. Connect gateway by PowerShell or SSH.

   * [PowerShell](./powershell.md)

   * [SSH](./ssh.md)

3. Switch to the folder where `MBBConnect.exe` is located. 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### Example
The example below uses MBBConnect.exe in PowerShell. For example, if the APN of the SIM card is “Internet”, use `MBBConnect.exe Internet` to connect.
 
The output message will show the flow:

* The state is changed from Not Connected to Connected. 

* WWAN network is configured successfully.

Try the sample for Mobile Broadband Connection [here](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect).