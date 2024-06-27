---
title: Common Device Restrictions
description: Keep up to date with common device restrictions and settings for the HoloLens mixed reality device. 
ms.service: hololens
ms.sitesec: library
ms.topic: article
ms.localizationpriority: Low
ms.date: 06/27/2024
ms.reviewer: aboeger
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Common Device Restrictions

This guide helps IT professionals understand the more commonly used management options available for the Windows 10 Holographic OS in the enterprise. Please consult your MDM system documentation to understand how these policies are enabled by your MDM vendor. Not all MDM systems support every setting described in this guide. Some support custom policies through OMA-URI XML files. See [Microsoft Intune support for Custom Policies](/mem/intune/configuration/custom-settings-windows-10). Naming conventions may also vary among MDM vendors.

Find more details on policy options in the HoloLens supported [Policy CSPs](/windows/client-management/mdm/policy-csps-supported-by-hololens2)

## Prevent changing of settings

Employees are usually allowed to change certain personal device settings that you may want to lock down on corporate devices. Employees can interactively adjust certain settings of the HoloLens through the settings UI. Using MDM, you can limit what users are allowed to change.
The following lists commonly used MDM settings that Windows 10 Holographic supports to configure settings restrictions:

- [Allow VPN:](/windows/client-management/mdm/policy-csp-settings#settings-allowvpn) Allows the user to change VPN settings
- [Allow Manual WiFi Configuration:](/windows/client-management/mdm/policy-csp-wifi#wifi-allowmanualwificonfiguration) Allows users to make Wi-Fi connections outside of MDM provisioned networks
- [Allow Manual MDM Unenrollment](/windows/client-management/mdm/policy-csp-experience#experience-allowmanualmdmunenrollment) Whether users are allowed to delete the workplace account (i.e., unenroll the device from the MDM system)

Added in [Windows Holographic, version 20H2](hololens-release-notes-2004.md#windows-holographic-version-20h2) for HoloLens 2 devices:

- [Allow Add Provisioning Package:](/windows/client-management/mdm/policy-csp-security#security-allowaddprovisioningpackage) Toggle if users can add new provisioning packages, overwriting with new values.
- [Allow Remove Provisioning Package:](/windows/client-management/mdm/policy-csp-security#security-allowremoveprovisioningpackage) Toggle if users can remove provisioning packages, allowing them to toggle previously locked settings.

Added in [Windows Holographic, version 21H2](hololens-release-notes.md#windows-holographic-version-21h2):

- [RequirePrivateStoreOnly](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-requireprivatestoreonly) policy enables the Microsoft Store app to be configured to only show the private store configured for your organization, limiting access to only the apps you’ve made available.

## Hardware restrictions

Windows 10 Holographic devices use state-of-the-art technology that includes popular hardware features such as cameras, microphones, speakers, USB interfaces, Bluetooth interfaces, and Wi-Fi. You can use hardware restrictions to control the availability of these features.
The following lists commonly used MDM settings that Windows 10 Holographic supports to configure hardware restrictions:

> [!NOTE]
> Some of these hardware restrictions affect connectivity and assist in data protection.

- [Allow Wi-Fi:](/windows/client-management/mdm/policy-csp-wifi#wifi-allowwifi) Whether users can enable and use the WiFi radio on their devices.
- [Allow USB Connection:](/windows/client-management/mdm/policy-csp-connectivity#connectivity-allowusbconnection) Whether the USB connection is enabled (doesn’t affect USB charging.)
- [Allow Bluetooth:](/windows/client-management/mdm/policy-csp-connectivity#connectivity-allowbluetooth) Whether users can enable and use the Bluetooth radio on their devices.
- [Restrict Camera:](/windows/client-management/mdm/policy-csp-privacy#privacy-letappsaccesscamera) Specifies whether Windows apps can access the camera.
- [Restrict Microphones:](/windows/client-management/mdm/policy-csp-privacy#privacy-letappsaccessmicrophone) Specifies whether Windows apps can access the microphone.

Added in [Windows Holographic, version 20H2](hololens-release-notes-2004.md#windows-holographic-version-20h2) for HoloLens 2 devices:

- [DisplayOffTimeoutOnBattery](/windows/client-management/mdm/policy-csp-power#power-displayofftimeoutonbattery) Set amount of time until display turns off, and by turning off the display, locks the device.
- [DisplayOffTimeoutPluggedIn](/windows/client-management/mdm/policy-csp-power#power-displayofftimeoutpluggedin) Set amount of time until display turns off, and by turning off the display, locks the device.

## Policy interactions and expectations

Some policies interact well and some can have complications. Here are some examples:

- If you apply provision packages using a USB during OOBE, and one of them applies [System/AllowStorageCard](/windows/client-management/mdm/policy-csp-system#system-allowstoragecard), no more policies will be applied from your USB as it can no longer be read.
- If you set [Connectivity/AllowUSBConnection](/windows/client-management/mdm/policy-csp-connectivity#connectivity-allowusbconnection) you will still be able to use USB Microphones and Ethernet adapters.
- If you set [System/AllowStorageCard](/windows/client-management/mdm/policy-csp-system#system-allowstoragecard) you will still be able to use Ethernet adapters.
