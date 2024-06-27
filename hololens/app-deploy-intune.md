---
title: Intune and Company Portal
description: Learn how to set up, assign, and create a comfortable user experience with Intune, mobile device management, and the company portal.
keywords: intune, app management, app, company portal, portal, hololens
ms.date: 06/27/2024
ms.service: hololens
ms.custom: 
- CI 111456
- CSSTroubleshooting
ms.topic: article
ms.sitesec: library
ms.localizationpriority: Low
audience: HoloLens
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Intune & Company Portal

With Mobile Device Management (MDM), you can use your own custom apps through [Microsoft Endpoint Manager (Intune)](/intune/windows-holographic-for-business) to deploy it directly to your HoloLens devices. Microsoft Intune is a cloud-based service that focuses on mobile device management (MDM) and mobile application management (MAM). Intune is included in Microsoft's [Enterprise Mobility + Security (EMS) suite](https://www.microsoft.com/microsoft-365/enterprise-mobility-security), and enables users to be productive while keeping your organization data protected. To learn more about Intune, read [What is Intune](/mem/intune/fundamentals/what-is-intune).

## Setup

1. Upload an app to a Line of Business, or upload a custom app to your Intune tenant. See also: [Enterprise app management](/windows/client-management/mdm/enterprise-app-management).

2. [Assign your app to a group](/mem/intune/apps/apps-deploy). Based on the chosen assignment type, the app can be delivered automatically or available to be readily pulled down if you have a selection of apps.

> [!NOTE]
> When building your appx bundle make sure to account for including the architecture for the device(s) that you are deploying to. HoloLens 2 is ARM64, and HoloLens (1st Gen) is x86. You may include both in a single appx bundle if you plan on having a mixed devices environment.

## Assignment types

To have your app to be automatically installed on the device after enrollment, you should select **Required** for that group(s).
To make your app available for download to devices enrolled through the company portal, select **Available for enrolled devices**.

## End-User Experience

After you have set up configuration on Intune, you're ready for end users to receive your selected apps.

Follow these steps to automatically get your app(s):

1. Enroll your device with your tenant.
2. Once your device has completed enrollment, you should receive the app on your device.
3. If you aren't seeing your app immediately, go to **Settings** > **Accounts** > **Work or School** > *your account* Info, and scroll down to see information on installed app status.

How to get to apps through the Company Portal:

1. Open the **Start Menu** and select **Microsoft Store**.
2. Search for **Company Portal** and download the app.
3. Sign into your account.
4. Select the app you wish to receive and download it.

> [!Tip]
> Learn more about [auto-installing the Company Portal](/mem/intune/apps/company-portal-app) and [deploying and managing apps in Intune](/mem/intune/fundamentals/windows-holographic-for-business#deploy-and-manage-apps).

## About LOB app updates

LOB apps check for updates and status changes independently of syncs with Intune. This checking is due to the larger size of app than policies. In general Intune will automatically reinstall, update, or remove a required app within 24 hours, rather than waiting for the 7 day reevaluation cycle. There are certain conditions that cause Intune to update, reinstall, or remove an app in the 24 hour windows. To read the up-to-date list of triggers, read more about [installing, updating, or removing required apps](/mem/intune/apps/apps-add#installing-updating-or-removing-required-apps).