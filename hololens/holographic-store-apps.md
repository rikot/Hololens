---
title: Find, install, and uninstall applications
description: The Microsoft Store is your source for apps and games that work with HoloLens.  Learn more about finding, installing, and uninstalling holographic apps.
ms.assetid: cbe9aa3a-884f-4a92-bf54-8d4917bc3435
ms.date: 3/7/2022
ms.reviewer: qizho
keywords: hololens, store, uwp, app, install
ms.service: hololens
ms.sitesec: library
ms.topic: article
ms.localizationpriority: high
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Find, install, and uninstall applications from the Microsoft Store

The Microsoft Store is your go-to source for apps and games that work with HoloLens. When you go to the Store on your HoloLens, any apps you see there will run on it.

Apps on HoloLens use either 2D view or holographic view. Apps that use 2D view look like windows and can be positioned all around you. Apps that use holographic view surround you and become the only app you see.

HoloLens supports many existing applications from the Microsoft Store, and new apps built specifically for HoloLens.  This article focuses on holographic applications from the Microsoft Store.

To learn more about installing and running custom apps, read [Custom holographic applications](holographic-custom-apps.md).

## New look for the store

There is a new version of the Microsoft Store app for the HoloLens 2. This app update occurs seamlessly when the Microsoft Store app itself is updated. When the update is complete, you see a storefront very similar to the store app that is available on desktop. Since this is an app update it is distributed to all HoloLens 2 devices, regardless of OS version.

![Image of new store app that became availble in May 2022](images/store-app-hololens2-censored.jpg)

Much of the store's functionality is the same; however some placement of items or changes in icons occurred. One such instance is that the see more button "**...**" was removed. To find your apps and updates you can use the **Library** button.

## Find apps

Open the Microsoft Store from the **Start** menu. Then browse for apps and games. You can use [voice commands](hololens-cortana.md) to search by saying "Search", once the search window opens say "Start dictating" and then when prompted begin saying your search terms.

> [!NOTE]
> The System Requirements for HoloLens devices are based on the architecture of the app build. If an app build for HoloLens (1st gen) has not been updated with to a newer UWP in the store to include the ARM architecture package, then it will not be available for HoloLens 2 devices. Likewise, if a HoloLens 2 app does not include the x86 architecture package, it will not be available for HoloLens (1st gen) devices. HoloLens device architectures:
>
> - x86 = HoloLens (1st gen)
> - ARM = HoloLens 2

> [!NOTE]
> On January 12, 2021 the following apps will reach End of Support on HoloLens devices. We encourage you to use the following link on your device to use the web version of the app.

| App        | Link                                          |
|------------|-----------------------------------------------|
| Excel mobile      | [https://office.live.com/start/Excel.aspx](https://office.live.com/start/Excel.aspx)      |
| Word mobile       | [https://office.live.com/start/Word.aspx](https://office.live.com/start/Word.aspx)       |
| PowerPoint mobile | [https://office.live.com/start/PowerPoint.aspx](https://office.live.com/start/PowerPoint.aspx) |

> [!NOTE]
> The OneDrive app is not currently supported for Microsoft Entra accounts on HoloLens. We recommend downloading the Microsoft OneDrive PWA app. [Follow these steps to download the app.]

## Install apps

To download apps, you must be signed in with a Microsoft account. Some apps are free and can be downloaded right away. For apps that require a purchase, you must be signed in to the Store with your Microsoft account and have a valid payment method.

> [!NOTE]
> The account you use on Microsoft Store doesn't have to be the same as the account you are signed in with. If you are using a Work or School account on your HoloLens then you may need to sign in with your personal account in the Store App to make a purchase.

> [!TIP]
> To set up a payment method, go to [account.microsoft.com](https://account.microsoft.com/) and select **Payment & billing** > **Payment options** > **Add a payment option**.

1. To open the [**Start** menu](holographic-home.md), perform a [Start gesture](/hololens/hololens2-basic-usage#start-gesture) or [bloom](hololens1-basic-usage.md) gesture on HoloLens (1st gen).

1. Select the Microsoft Store app. After the Store app opens:
   1. Use the search bar to look for applications.
   1. Select essential apps or apps made specifically for HoloLens from one of the curated categories.
   1. On the top right of the Store app, select the **"..."** button and then select **My Library** to view any previously purchased apps.

1. Select **Get** or **Install** on the application's page (a purchase may be required).

### Install Microsoft OneDrive PWA App

> [!NOTE]
> PWA cannot be managed or deployed via Microsoft Intune / MDM.

Pre-Requisites: User has already joined the HoloLens 2 device to their work tenant.

1. Open start menu and launch Edge browser.

    ![Start menu](images/office-pwa-1.jpg)

1. On your HoloLens go to [https://onedrive.live.com/about/signin](https://onedrive.live.com/about/signin) and enter your Work account credentials

    ![Work sign in](images/office-pwa-2.jpg)

1. Once you have successfully logged into your OneDrive web portal, wait for 30 to 60 secs for PWA download button to show up

    ![PWA install button](images/office-pwa-3.jpg)

1. Select the PWA download button and install the app

    ![Install prompt](images/office-pwa-4.jpg)

1. Close the Edge browser and from the Start menu, select the **All Apps** button and launch the OneDrive PWA App labeled **Microsoft OneDrive**

    ![All apps showing both apps.](images/office-pwa-5.jpg)

    > [!NOTE]
    > The “Microsoft OneDrive” is the PWA app where as “OneDrive” is the older UWP.

1. You'll then be able to see your OneDrive files.

    ![OneDrive PWA](images/office-pwa-6.jpg)

See also: [Enabling automatic uploads to OneDrive for business](hololens-release-notes.md#onedrive-for-work-or-school-camera-roll-upload)

## Update Apps

### Manual updates

While apps from the Microsoft Store are kept up to date automatically by the device, sometimes you may want to manually check for updates to get those app updates sooner. This can be done from either the Settings app or the Microsoft Store app.

#### Settings app

To manually check for updates to Store apps from the Settings app, go to Apps -> App updates.  This is particularly useful if access to the Microsoft Store is blocked in your environment.

IT admins are able to block or allow this page with the [Settings/PageVisibilityList policy](/windows/client-management/mdm/policy-csp-settings) with the URI `ms-settings:appupdate`.

See the following screenshot of the Settings app where this feature can be seen.

![app update from settings](media/holographic-store-apps/app-update-from-settings.png)

> [!NOTE]
> The ability to check for app updates from the Settings app is only available to users on 23H1 and later builds.

#### Microsoft Store app

1. To open the [**Start** menu](holographic-home.md), perform a [Start gesture](/hololens/hololens2-basic-usage#start-gesture).

1. Select the Store app.

1. Look at the bottom left of the store app.

1. Select the **Library** icon and **Get updates**. 

Want to know what version an app is on? From the **Library** screen select an app installed on your device to go to that apps page, and scroll to the bottom and look for **>_ Installed version**.

> [!NOTE]
> If the apps on your device were distributed by your organization they can be updated through the same commercial app management methods. If this applies to your situation, read more via our [overview of commercial app deployment.](app-deploy-overview.md)
>
> If you would like to update a custom app that has been sideloaded or deployed, you will need to use the same method with the updated version of your app. To learn more about installing and running custom apps, read [custom holographic applications](holographic-custom-apps.md).

### Automatic app updates

Automatic updates apply to Microsoft Store apps, and they can be updated automatically only if they have been installed directly from the Store or installed using the store package via Intune. If installed from Intune using a private package, IT can push updates down from MDM.

> [!NOTE]
> With the [retirement](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/update-to-intune-integration-with-the-microsoft-store-on-windows/ba-p/3585077) of the Microsoft Store for Business, please see [Microsoft Store for Business & Intune](app-deploy-store-business.md).
#### How automatic updates work

Automatic app updates are scheduled to occur daily subject to network availability. These updates occur approximately every 24 hours, although updates per device can be random. Keep your device either active or plugged into AC to receive updates. Even if app updates are downloaded during active daily usage, they will only be applied when the app to be updated is no longer in use.

> [!TIP]
> If possible, charge your device overnight while it is connected to the corporate network. If updates can be downloaded and installed overnight, they are less likely to interrupt active device usage.

#### How IT administrators can control automatic updates

IT administrators can control automatic app updates through the [ApplicationManagement/AllowAppStoreAutoUpdate](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowappstoreautoupdate) policy. This policy allows them to enable or disable automatic app updates completely, but it does not control when updates occur.

As of [21H2](hololens-release-notes.md#windows-holographic-version-21h1), IT administrators can also use the [ScheduleForceRestartForUpdateFailures](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-scheduleforcerestartforupdatefailures) policy to control when apps that were in use, but could not be updated in previous attempts, should be forcibly restarted.

## Uninstall apps

There are three ways to uninstall applications. You can uninstall applications through the Microsoft Store, Start menu or from Settings.

> [!WARNING]
> You cannot uninstall a system app or the Microsoft Store itself.

> [!IMPORTANT]
> If your HoloLens 2 has multiple users, you must be logged in as the user who installed the app to uninstall it.

### Uninstall from the Microsoft Store

Open the Microsoft Store from the **Start** menu, and then browse for the application you want to uninstall.  On the Store page, each installed application has an **Uninstall** button.

### Uninstall from the Start menu

On the **Start** menu or in the **All apps** list, browse to the app. Select and hold until the menu appears, then select **Uninstall**.

### Uninstall from Settings

On the **Start** menu, select **Settings > Apps.** Find the app from the list, select it and then click **Uninstall**.

## HoloLens 1 only

1. To open the [**Start** menu](holographic-home.md), perform a [Start gesture](/hololens/app-deploy-store-business) or [bloom](hololens1-basic-usage.md) gesture on HoloLens (1st gen).

1. Select the Store app.

1. Look to the top right of the Store app.

1. Select the **"..."** or “See more” button.

   > [!div class="mx-imgBorder"]
   > ![Microsoft Store app screenshot.](images/store-update-1.png)

1. Select **Downloads and updates**.
    1. If your device previously identified updates, there may be a down arrow and a number that represents pending updates.

1. Select **Get updates**. Your device will now search for updates and set them to download and install.

   > [!div class="mx-imgBorder"]
   > ![Microsoft Store app screenshot of getting updates..](images/store-update-2.png.jpg)





If you are unable to uninstall an app, please file [feedback](/hololens/hololens-feedback) using the Feedback Hub.
