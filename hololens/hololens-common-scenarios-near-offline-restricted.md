---
title: Common Scenarios – Near Offline or Restricted for HoloLens 2
description: Learn how to set up a secure, near offline, or restricted deployment and app deployment scenario with provisioning for HoloLens devices.
keywords: HoloLens, management, offline, offline secure
ms.date: 06/27/2024
ms.service: hololens
ms.sitesec: library
ms.reviewer: mata
ms.topic: article
audience: ITPro
ms.localizationpriority: Low
appliesto:
- HoloLens 2
---

# Common Scenarios – Near Offline or isolated environments for HoloLens 2

## Overview

This guide provides guidance for deploying HoloLens 2 in areas where networking is restricted. This could either be for secure environments or for areas where networking can't be assured such as power plants, ships, or other areas.

This scenario is designed to deliver the best user and administrator experience. This scenario allows for the use of Microsoft Entra ID, Intune, Windows updates and multiple user support with IRIS sign-in, whilst meeting the needs of organizations who have more security or networking challenges.

> [!NOTE]
> This scenario describes one possible approach. We expect each organization deploying in this scenario will have unique requirements, which can be mapped into this solution as required.

[![Offline Secure scenario.](./images/restricted-deployment-scenario-d.png)](./images/restricted-deployment-scenario-d.png#lightbox)

## Prepare

The cloud functionality of this guide matches the requirements for the [Cloud Connected Scenario](hololens2-cloud-connected-prepare.md). The following decisions will need to be made with reference to both your infrastructure and security teams.

### Determine level of cloud connectivity required

This guide assumes the following services are being used:

- [Microsoft Entra ID for user sign in and authentication](hololens-identity.md)
- Microsoft Entra multifactor authentication and Windows Hello for Business
- [Autopilot for device deployment](/mem/autopilot/existing-devices)
- [Intune for Device Management](/mem/intune/remote-actions/device-management)
- [Windows Update for Device Updates](hololens-update-hololens.md)

> [!NOTE]
> If these services are already used within your organization, then your security team may be able to reuse any security assessments already completed.

### Determine level of network connection during usage

Consider whether or not devices are connected to a network during usage:

- If devices are able to be connected, then more services can be used such as Dynamics 365 Remote Assist or Dynamics 365 Guides.
- LOB applications can be developed to use local data storage either on device, or on a server contained within the organizations network.

### Governance processes for User Enrollment and Updates

- Users need to make their initial sign into the device when connected to the network. After setting up their PIN and IRIS, they can sign in offline.
- Devices should be reconnected at a regular schedule (once a month) to enable any MDM policy changes and Windows updates to be completed.

### Network Configurations

Detailed network configurations are out of the scope of this article, and will vary depending on unique configuration needs.

- Firewalls should support URL based filtering, as IP filtering may be difficult to manage.
- Proxy Servers, with or without SSL inspection can be utilized, either in transparent mode or configured on the device.
- Devices will need to be able to access the relevant endpoints listed in the tables below.

> [!NOTE]
> It is likely that during initial configuration, a network engineer will need to validate the endpoints are accessible.

> [!IMPORTANT]
> Read more about how to deploy your app with the [Deployment Guide – Corporate connected HoloLens 2 with Dynamics 365 Guides - Prepare | Microsoft Docs.](hololens2-corp-connected-prepare.md)

## Configure

The key configuration elements relate to the network restrictions. Following our Connected HoloLens 2 [Deployment Guide – Cloud connected HoloLens 2 deployment at scale with Remote Assist - Configure | Microsoft Docs](hololens2-cloud-connected-configure.md) will allow for most cloud configurations to be completed.

The key [endpoints](hololens-offline.md) to enable access on your network are:

|Group                                  |   Purpose                                              |
|---------------------------------------|--------------------------------------------------------|
|Near Offline Setup                     |   Initial OOBE                                         |
|Microsoft Entra multifactor authentication                           |   MFA Requests (Optional if not using Azure MFA)       |
|Intune and MDM Configurations          |   Intune Enrollment (Optional if not using Intune)      |
|Certificates                           |   Check Microsoft Certificate Status                   |
|Device Metadata                        |   Device Information                                   |
|Diagnostic Data                        |   Sending Telemetry to Microsoft (Strongly Recommended)|
|Licensing                              |   Validate software licensing                          |
|Network Connection Status Indicator    |   Used to confirm whether the device has network access|
|Windows Defender                       |   Used to update Windows Defender Information          |
|Windows Update                         |   Used for Windows Update                              |
|Settings                               |   Used in the Settings Application                     |

> [!TIP]
> These are the key endpoints to utilize Autopilot, complete OOBE and allow a Microsoft Entra user to sign in with Windows Hello for Business. Your organization may require other endpoints to allow for the desired functionality. 

## Deploy and maintain
Deployment and Maintenance steps are identical to the [Cloud connected guide](hololens2-cloud-connected-deploy.md). We've included basic suggestions here.

When the device is reconnected to the corporate network, we suggest you perform manual updates at-least once a month (that is, the second Wednesday of the month) to ensure your device(s) are up-to-date and secure.

### Manually update store apps

To update an app you installed from the Microsoft Store, you can update the app from the Microsoft Store app. For apps installed for the Microsoft Store for Business, you can also update those apps from the Microsoft Store for Business.

See how at [Manually update apps](holographic-store-apps.md).

### Manually update OS

Check for updates anytime in settings. To see available updates:

1. Open the **Settings** app.
1. Navigate to **Update & Security** > **Windows Update**.
1. Select **Check for updates**.

Read more at [Update HoloLens](hololens-update-hololens.md).

### Manually sync with MDM

Based on your specific needs, ensure that you perform updates and sync with MDM.

Read more at [Using MDM to manage HoloLens devices](hololens-mdm-configure.md).

> [!div class="nextstepaction"]
> [Cloud connected deployment - Deploy](hololens2-cloud-connected-deploy.md)
