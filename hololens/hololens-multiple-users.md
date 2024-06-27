---
title: Share your HoloLens with multiple people
description: You can configure HoloLens to be shared by multiple Microsoft Entra accounts, or by multiple users that use a single account.
ms.service: hololens
ms.sitesec: library
ms.topic: article
ms.localizationpriority: Low
ms.date: 06/27/2024
ms.reviewer: anisgup
appliesto:
- HoloLens 2
---

# Share your HoloLens with multiple people

## Overview

Businesses often invest in many shared HoloLens devices. How you use HoloLens is flexible across the board, depending on your individual requirements. Here’s an example of some multi-user experiences:

- A fleet of HoloLens 2 devices is set up via Windows Autopilot for HoloLens 2, with a consistent portfolio of company applications on each device. You've set up a few different Kiosk profiles, targeting different Microsoft Entra groups. Each user logs into the HoloLens using FIDO2 keys and signing into their own Microsoft Entra account, and is presented with a tailored experience.
- An independent software vendor (ISV) rents HoloLens 2 Devices with Dynamics 365 Remote Assist and their line of business (LOB) application to a customer's company. These devices are configured for Kiosks that include only their LOB app and Remote Assist, and are shared across multiple end users. WDAC is used to keep the Settings app and Microsoft Edge from launching. Included with the rental is a USB-C battery pack to keep the devices at full charge over multiple shifts.
- An end user at an enterprise attempts to make adjustments to Bluetooth on the device so they can connect a new device, but the Page Settings Visibility policy is enabled to limit the Devices page from being viewed. They're still allowed access to other pages as needed, such as Wi-Fi so they can use Remote Assist in multiple locations with that same HoloLens.

## Best practices

When planning to share your devices, there are several considerations to optimize your device environment based on your business needs.

- [Identity and Authentication](#identity-and-authentication)
- [Device Management](#device-management)
- [Advanced device management - Kiosk and WDAC](#advanced-device-management---kiosk-and-wdac)
- [Physical Management](#physical-management)

### [Identity and Authentication](hololens-identity.md)

If you're planning on having multiple accounts on a device, then you can have Microsoft Entra accounts with all modes of authentication. These authentication methods are based on [Windows Hello](/windows-hardware/design/device-experiences/windows-hello), including Iris, PIN, and FIDO2 keys. In the case of a [Shared Microsoft Entra account](/hololens/shared-aad-accounts), the authentication method used is Certificate-Based Authentication (CBA).

- FIDO 2 Security keys are excellent if you have multiple devices, many users, or are constantly using new devices.
- If one device is shared with multiple users, a [Shared Microsoft Entra account](/hololens/shared-aad-accounts) allows users to login via a single button-click.
- If you have 10 or fewer users, Iris is a fast solution to sign in users who have previously signed into the same device.

### [Device Management](hololens-csp-policy-overview.md)

If devices are being shared between users, then you may want to use device restrictions. By using device management, you can set some policies to either better enable your users to use the device, manage updates, or limit what the device can do. It's recommended you review our [common device ](hololens-common-device-restrictions.md)restrictions and see if these recommendations seem to fit with your organization. Once you know what policies you want to use, you can apply them through [Microsoft's Endpoint Manager (MDM)](hololens-mdm-configure.md) or provisioning packages.

### Advanced device management - [Kiosk](hololens-kiosk.md) and [WDAC](windows-defender-application-control-wdac.md)

In some cases, you may want to limit what applications can be accessed by the end users. You could be limiting what apps users are presented with on the start menu using [Kiosk mode](hololens-kiosk.md). Kiosk can be configured to present different start menus based on user, Microsoft Entra groups, or special user types; such visitor or excluding device owners. You can choose multiple apps, or just a single app. A multi app kiosk doesn't stop one app from launching another, so if the store or another app is available users can still launch another app.

You may also want to completely stop the launching of apps or services using [Windows Defender Application Control (WDAC)](windows-defender-application-control-wdac.md) to restrict apps. WDAC is different that Kiosk, because it doesn't change the UI of HoloLens but instead doesn't allow a blocked app to launch.

[Page Settings Visibility](settings-uri-list.md) is another way to add restrictions to a device. In the event you need to grant users access to some pages in the Settings app, but not all you can use Page Settings Visibility to limit access. This policy is useful, for example, if your users need to change the Wi-Fi, but you don't want them to access the Accounts page.

### Physical Management

When sharing the device between multiple users, there are some physical considerations.

- Ensure devices are charging between shifts.
- If a device needs to last multiple shifts, consider using an external battery at the start of a shift while the device still has significant charge per the [managing heat directions](hololens2-charging.md#managing-heat).
- When you're storing devices, keep them plugged in and connected to a network. This practice is the best way to ensure OS and apps stay up to date.
- Consider how you plan to [clean the device](hololens2-maintenance.md) between users.  If you plan to use Iris authentication, it's highly recommended that the visor is cleaned between each user.
- For a device with a single shared user if using a shared PIN/password for a single user, don't put the PIN/password on the side of the device.
- For multiple devices with a single shared user, use various PINs/passwords.
- Another option for multiple devices with a single shared user is to set up a [Shared Microsoft Entra account](/hololens/shared-aad-accounts) to allow signin with a single button-click.
- Label your devices so users can find ones they already used. Signing back into a previously used device to launch an app can take a little as 30 seconds with Iris, PIN, or FIDO2 security keys. Setting up a new device, either OOBE or adding a new user, and then launching an app can take as much as 5 minutes.

## Share with multiple people, each using their own account

Individual Microsoft Entra accounts are the preferred and most secure identity use case for HoloLens 2 users. When using their own Microsoft Entra accounts, multiple users can each keep their own user settings and user data on the device. Only one user can be signed in at a time. When a user signs in, HoloLens signs out the previous user.

To make sure that multiple people can use their own accounts on your HoloLens, follow these steps to configure it:

1. When you [set up the device](hololens2-start.md), select **My work or school owns it** and sign in by using a Microsoft Entra account.
1. After you finish setup, make sure that the account settings (Settings > Accounts) include **Other users**.

To use HoloLens, each user follows these steps:

1. If another user has been using the device, choose one of the following options:
   - Press the power button once to go to standby, and then press the power button again to return to the lock screen
   - Select the user tile from the **Start menu** or choose "sign out" from the **Power menu** to sign out the current user.

1. Use your Microsoft Entra account credentials to sign in to the device.  
   - If it's the first time you have are using the device, you're asked to [calibrate](hololens-calibration.md) the HoloLens to your own eyes.
   - If you previously used the device:
           - [Windows Holographic, version 20H2, build 19041.1128](hololens-release-notes-2004.md#windows-holographic-version-20h2) or higher, the display seamlessly adjusts for quality and a comfortable viewing experience.
      - Previous builds need manual calibration to adjust to your eyes.


      > [!TIP]
      > If a user hasn't signed into a device yet try one of these two methods for a faster login:
      > - **FIDO 2 Security key** : Your FIDO2 security key is automatically recognized and the user won't need to type in their user credentials or use MFA. This is the fastest method to sign in on a new device.
      > - **Web authentication** : When you sign into a new device, you can select the link **Sign in from another device** which generates a 9 character code you can use at [aka.ms/devicelogin](https://login.microsoftonline.com/common/oauth2/deviceauth) to either sign in as the user on the device, or type your user name and password using a keyboard for your convenience.
      >    

      To see a list of the device users or to remove a user from the device, go to **Settings** > **Accounts** > **Other users**. You can also remove users on a device by following the instructions below.

> [!TIP]
> If more than one user uses a device, it is important to keep the visor clean. See **[HoloLens 2 cleaning FAQ](/hololens/hololens2-maintenance)** for details on how to clean the device. We recommend that you clean the visor between each user. This best practice is particularly important if you use Iris authentication.

#### Remove users on a device

-  Organizations with scaled deployments of HoloLens 2 devices might encounter the 63-user limit per device that prevents adding users. To address this situation, we added controls that delete the least recent users from the device at controlled intervals, which is a feature you might have used on the Desktop version. Deleting users in a controlled way is useful for other reasons, too. Removing the inactive accounts speeds up the sign-in process and improves privacy and security by reducing retention of unused data. We use three criteria to determine when to remove user accounts on the device:

- When a user has been inactive on the device past a number of days, configurable via **ProfileInactivityThreshold.**
- When the device reaches a storage threshold, configurable via **StorageCapacityStartDeletion** and **StorageCapacityStopDeletion**.
- When the device reaches the maximum number of supported users (63).

Here's how to get started:

1. Set the boolean value for **UserProfileManagement/EnableProfileManager** to **true**.

1. Set the numerical **UserProfileManagement/ProfileInactivityThreshold**, which is the number of days a user must be inactive (not logged on to the device) before the user is deleted. The default value is **30**.
1. Set **UserProfileManagement/StorageCapacityStartDeletion**, a numerical value representing the percentage of free space left when the device begins deleting the least recent users. The Default value is **25%**.

1. Pair **UserProfileManagement/StorageCapacityStartDeletion** with **StorageCapacityStopDeletion** to determine when, based on the free storage percent, to stop deleting profiles.

1. Turn on the deletion policy **UserProfileManagement/DeletionPolicy**, and set it to **2**, which deletes users at both storage capacity threshold and profile inactivity threshold.

   If the **UserProfileManagement/DeletionPolicy** is on, when the device reaches the maximum number of users and is trying to add another, the device deletes the oldest user automatically.

To learn more about these policies, visit [AccountManagement CSP](/windows/client-management/mdm/accountmanagement-csp).

## Share with multiple people, all using the same account

Multiple users can also share a HoloLens device while using a single user account, or a [Shared Microsoft Entra account](/hololens/shared-aad-accounts). Although it is preferred for HoloLens users to log in to the device with their individual identities (Microsoft Entra accounts), this is not an option in some organizations.

There are two shared device methods available:

- **Multiple end users sharing 1 device** - a HoloLens device is allocated to a designated space where any employee can use the device. Examples would be a clean room or surgical suite.

- **Multiple end users sharing multiple devices** - HoloLens devices are in a shared storage space where employees can use any device. Examples would be an oil rig or an auto dealership/garage.

When a new user puts on the device for the first time while keeping the same account signed in, the device prompts the user to quickly calibrate and personalize the viewing experience. The device stores the calibration information to automatically optimize the quality and comfort of each user's viewing experience. Users won't need to calibrate the device again.

For more details on how a shared Microsoft Entra account can be used by multiple end users on one or more devices, see [Shared Microsoft Entra accounts in HoloLens](/hololens/shared-aad-accounts).



