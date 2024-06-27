---
title: HoloLens Device Troubleshooting
description: Stay up to date on the most common solutions to HoloLens device issues and troubleshooting techniques.
ms.date: 6/27/2024
ms.localizationpriority: Low
ms.service: hololens
ms.topic: article
audience: HoloLens
ms.custom: 
- CI 111456
- CSSTroubleshooting
keywords: issues, bug, troubleshoot, fix, help, support, HoloLens, emulator
---

# Device Troubleshooting

This article describes how to resolve several common HoloLens issues.

>[!IMPORTANT]
> Before you start any troubleshooting procedure, make sure that your device is charged to **20 to 40 percent** of battery capacity, if possible. The [battery indicator lights](hololens2-setup.md#lights-that-indicate-the-battery-level) located under the power button are a quick way to verify the battery capacity without logging into the device.

<a id="list"></a>

##### Fixed Known Issues

- [**Fixed** - Swipe to type on the virtual keyboard was not working correctly](#fixed---swipe-to-type-on-the-virtual-keyboard-was-not-working-correctly)
- [**Fixed** - Users opting in to Windows Insider after flashing to 23H1 are stuck](#fixed---users-opting-in-to-windows-insider-after-flashing-to-23h1-are-stuck)
- [**Fixed** - HoloLens user can’t launch Microsoft Edge](#fixed---hololens-user-cant-launch-microsoft-edge)
- [**Fixed** - Every time the power goes to 18 percent, the device suddenly shuts down automatically](#fixed---every-time-the-power-goes-to-18-percent-the-device-suddenly-shuts-down-automatically)
- [**Fixed** - OneDrive UWP app doesn't work for Microsoft Entra users](#fixed---onedrive-uwp-app-doesnt-work-for-azure-ad-users)
- [**Fixed** - Remote Assist video freezes after 20 minutes](#fixed---remote-assist-video-freezes-after-20-minutes)
- [**Fixed** - Downloading locked files doesn't show error](#fixed---downloading-locked-files-doesnt-error)
- [**Fixed** - Device Portal file upload/download times out](#fixed---device-portal-file-uploaddownload-times-out)
- [**Fixed** - OneDrive doesn't automatically upload pictures](#fixed---onedrive-doesnt-automatically-upload-pictures)

##### Known Issues

- [Users may be unable to cleanup temporary files completely](#users-may-be-unable-to-cleanup-temporary-files-completely)
- [Sometimes the Store app won't open after an OS update](#sometimes-the-store-app-wont-open-after-an-os-update)
- [After successful network connection users may receive incorrect error regarding internet connectivity during initial device setup](#after-successful-network-connection-users-may-receive-incorrect-error-regarding-internet-connectivity-during-initial-device-setup)
- [Sometimes Settings app won't open after update](#sometimes-settings-app-wont-open-after-update)
- [Update indicator may still be visible after OS update](#update-indicator-may-still-be-visible-after-os-update)
- [Resetting a device with low space doesn't reset](#resetting-a-device-with-low-space-doesnt-reset)
- [Remote Wipe doesn't remove device from Intune](#remote-wipe-doesnt-remove-device-from-intune)
- [Devices not getting the latest feature updates](#devices-not-getting-the-latest-feature-updates)
- [Why do I see 0x80180014 during Autopilot?](#why-do-i-see-0x80180014-during-autopilot)
- [Microsoft Store error code 0x80131500](#microsoft-store-error-code-0x80131500)
- [File Explorer and pickers can't select OneDrive](#file-explorer-and-pickers-cant-select-onedrive)
- [Microsoft Edge fails to start the microphone](#microsoft-edge-fails-to-start-the-microphone)
- [Auto-login asks for log-in](#auto-login-asks-for-log-in)
- [Some users may encounter an update failure with Insider build 20346.1466](#some-users-may-encounter-an-update-failure-with-insider-build-203461466)
- [Microsoft Edge fails to launch](#microsoft-edge-fails-to-launch)
- [Keyboard doesn't switch to special characters](#keyboard-doesnt-switch-to-special-characters)
- [Blue screen after unenrolling from Insider preview on a device flashed with an Insider build](#blue-screen-after-unenrolling-from-insider-preview-on-a-device-flashed-with-an-insider-build)

##### General

- [HoloLens is unresponsive or doesn't start](#hololens-is-unresponsive-or-wont-start)
- ["Low Disk Space" error](#low-disk-space-error)
- [Calibration Fails](#calibration-fails)
- [Can't sign in because my HoloLens was previously set up for someone else](#cant-sign-in-because-my-hololens-was-previously-set-up-for-someone-else)
- [Unity isn't working](#unity-isnt-working)
- [Windows Device Portal isn't working correctly](#windows-device-portal-isnt-working-correctly)
- [The HoloLens Emulator isn't working](#the-hololens-emulator-isnt-working)

##### Input

- [Voice commands aren't working](#voice-commands-arent-working)
- [Hand input isn't working](#hand-input-isnt-working)

##### Connectivity

- [Can't connect to Wi-Fi](#cant-connect-to-wi-fi)

##### External Devices

- [Bluetooth devices aren't pairing](#bluetooth-devices-arent-pairing)
- [USB-C Microphone isn't working](#usb-c-microphone-isnt-working)
- [Devices listed as available in Settings don't work](#devices-listed-as-available-in-settings-dont-work)

## **Fixed** - Swipe to type on the virtual keyboard was not working correctly

The swipe-to-type feature on the virtual keyboard was not working correctly, and affected Windows 11 builds only.  This issue was fixed in the Windows Holographic, version 23H2 - November 2023 Update with Build 22621.1152.

## **Fixed** - Users opting in to Windows Insider after flashing to 23H1 are stuck

> [!NOTE] 
> This was fixed in the [Windows Holographic, version 23H2 - November 2023 Update](/hololens/hololens-release-notes#windows-holographic-version-23h2---november-2023-update)

The issue occurred when users did a clean flash of their device to the June 2023 23H1 update, and then joined the Windows Insiders program.  In this situation, users were then stuck on that build until they followed the workaround.

### Workaround for opt-in to Insider after flashing 23H1

Users should flash their device to the July 2023, 22H2 build, allow the device to update to the June 2023 23H1 build and then join the Windows Insider program.


## **Fixed** - HoloLens user can’t launch Microsoft Edge

> [!NOTE]
> This was fixed in [Windows Holographic, version 22H1](hololens-release-notes.md#windows-holographic-version-22h1).

If you've having an issue launching Microsoft Edge on your HoloLens, you may have policy that's preventing launch. HoloLens can't launch Microsoft Edge if [ApplicationManagement/AllowAllTrustedApps](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowalltrustedapps) GPO is disabled. If AllowAllTrustedApps GPO is disabled, Appx doesn't trust the app as a Microsoft published app, which blocks installing / launching Microsoft Edge with HoloLens devices.

### Workarounds to launch Microsoft Edge

- Set ApplicationManagement/AllowAllTrustedApps GPO value to Enabled/ Default.
- User enables Developer mode.

## **Fixed** - Every time the power goes to 18 percent, the device suddenly shuts down automatically

> [!NOTE]
> This was fixed in [Windows Holographic, version 21H2 - November 2021 Update](hololens-release-notes.md#windows-holographic-version-21h2---november-2021-update)

A known issue is that when the device reaches 18% battery, it shuts down unexpectedly. This behavior is a software issue, not a hardware or battery issue, so don't exchange devices for this. If you're unsure if your issue matches this bug, try one of the following suggestions:

1. Ensure optional diagnostics are enabled on your devices
1. Reproduce the problem
1. Submit a [Feedback Hub](hololens-feedback.md) issue
1. Share the Feedback issue URL
1. [Contact support](https://aka.ms/hololenssupport)

[Back to list](#list)

<a name='fixed---onedrive-uwp-app-doesnt-work-for-azure-ad-users'></a>

## **Fixed** - OneDrive UWP app doesn't work for Microsoft Entra users

> [!NOTE]
> This issue is resolved in all apps that are version 19.xx and higher. If you still experience the same sign in issue while using app version 19.xx or later, please [send Feedback](hololens-feedback.md) then [contact support](https://aka.ms/hololenssupport) and share the Feedback item URL.
> Follow these [instructions to update your OneDrive app.](holographic-store-apps.md#update-apps) You can check which version of OneDrive you have by using the Microsoft Store app, then select the "See more" button represented by the **...** then select **Downloads and updates**.
> 

If you use OneDrive For Business using your Microsoft Entra account, you may encounter an error when signing into your inbox OneDrive app. Not being able to sign into the OneDrive app doesn’t affect automatic uploads of images and videos captured by the Camera app. Your files can still be saved and accessed from the OneDrive for Business cloud storage.

### Workarounds

Prerequisite: Customers can use Microsoft Edge and device OS is update to a Windows Holographic, 21H1 build or newer.

If you're experiencing this issue, try one of the following suggestions:

- Users can directly access OneDrive For Business from Microsoft Edge, and interact with their files the website from their browser.
- Users can install the OneDrive PWA app to HoloLens by downloading it from Microsoft Edge. This app allows users to view and manage files on the device again. Read and follow these [instructions for installing the OneDrive PWA app on your HoloLens.](holographic-store-apps.md#install-microsoft-onedrive-pwa-app)

[Back to list](#list)

## **Fixed** - Remote Assist video freezes after 20 minutes

> [!NOTE]
> There is a newer version of Remote Assist which has a fix for this issue. Please [update Remote Assist](holographic-store-apps.md#update-apps) to the latest version to avoid this issue.

> [!NOTE]
> Due to this Known Issue's severity we had temporarily paused the availability of Windows Holographic, version 21H1. The 21H1 build is now available again, so devices may once again be updated to the latest 21H1 build.

On the latest release of [Windows Holographic, version 21H1](hololens-release-notes.md#windows-holographic-version-21h1), some users of Remote Assist experienced video freezing during calls over 20 minutes. This behavior is a **known issue**.

### Workarounds to fix Remote Assist

If you're unable to update Remote Assist to a newer build, try the following workaround:

#### Restart in between calls

If your calls are going over a length of 20 minutes and you're experiencing this issue, try rebooting your device. Rebooting your device between Remote Assist calls refreshes your device and put it back into a good state.

To quickly restart a device on [Windows Holographic, version 21H1](hololens-release-notes.md#windows-holographic-version-21h1) open the start menu, and select the user icon, then select **Restart**.

[Back to list](#list)

## **Fixed** - Downloading locked files doesn't error

> [!NOTE]
> This is a **known issue** that was fixed in [Windows Holographic, version 21H1 - July 2021 Update](hololens-release-notes.md#windows-holographic-version-21h1---july-2021-update).

In previous builds of Windows Holographic, when attempting to download a locked file, the result would be an HTTP error page. In the Windows Holographic, version 21H1 update, trying to download a locked file results in nothing visible happening—the file doesn’t download and there’s no error.

[Back to list](#list)

## **Fixed** - Device Portal file upload/download times out

> [!NOTE]
> This is a **known issue** that was fixed in [Windows Holographic, version 21H1 - July 2021 Update](hololens-release-notes.md#windows-holographic-version-21h1---july-2021-update). If you previously disabled SSL Connection as part of the workaround, we highly recommend you re-enable it.

Some customers find, when attempting to upload or download files, the operation might appear to hang and then time out or never complete. This behavior is separate from the '[file locked' known issue](#fixed---downloading-locked-files-doesnt-error) -- this affects Windows Holographic, versions 2004, 20H2 and 21H1 in-market builds. The problem was root caused to a bug in Device Portal's handling of certain requests.  THe issue is hit most consistently when using https, which is the default.

### Workaround for device portal time out

This workaround, which applies equally to Wi-Fi and UsbNcm, is to disable the "required" option under "SSL Connection". To do so, navigate to Device Portal, **System**, and select the **Preferences** page. In the **Device Security** section, locate **SSL Connection**, and uncheck to disable **Required**.

The user should then go to http://, not https:// (IP address) and features like file upload and download work.

[Back to list](#list)

## **Fixed** - OneDrive doesn't automatically upload pictures

The OneDrive app for HoloLens doesn't support automatic camera upload for work or school accounts. This **known issue** is fixed.  For more information on automatically uploading your mixed reality photos and videos for work or school account, see [Share your mixed reality photos and videos](holographic-photos-and-videos.md#share-your-mixed-reality-photos-and-videos).

Workarounds before the fix:

- If viable for your business, automatic camera upload is supported on consumer Microsoft accounts. You can sign in to your Microsoft account in addition to your work or school account (the OneDrive app supports dual sign-in). From your Microsoft account profile within OneDrive you can enable automatic, background camera roll upload.

- If you can’t safely use a consumer Microsoft account for uploading your photos automatically, you can manually upload photos to your work or school account from the OneDrive app. To do that, make sure you're signed into your work or school account in the OneDrive app. Select the **+** button and choose **Upload**. Find the photos or videos you want to upload by navigating to **Pictures > Camera Roll**. Select the photos or videos you want to upload, and then select the **Open** button.

[Back to list](#list)

## Users may be unable to cleanup temporary files completely

Some temp files are not cleaned up completely.  Users are not able to free up all temporary files via the Storage setting page in the Settings app.

## Sometimes the Store app won't open after an OS update

Users who update from Windows 10 to Windows 11 may experience an issue trying to open the Store app.  If that situation occurs, follow these steps to fix the Store app:

1. Get microsoft.ui.xaml.2.7.3 ARM64 appx package

    1. Download nupkg from https://www.nuget.org/api/v2/package/Microsoft.UI.Xaml/2.7.3

    1. Rename nupkg to microsoft.ui.xaml.2.7.3.nupkg.zip

    1. Extract zip file and copy the arm64 xaml appx package from tools\AppX\arm64\Release\Microsoft.UI.Xaml.2.7.appx

1. Depending on your preferred method of app deployment, you can select one of the options from App Management: Overview. The recommendation for the Settings app is:

    1. If small deployment/single device, copy appx to device (USB drive or MTP), click on the appx from File Explorer.

    1. If large deployment with MDM, deploy the appx as a LOB app through MDM. There’s no need for additional licenses or certificates.

## After successful network connection users may receive incorrect error regarding internet connectivity during initial device setup

Older HoloLens devices that have never gone through initial device setup may display an incorrect error when they are ultimately setup for the first time. The error indicates "You need internet for this..." even though a successful network connection was already established. This error prevents the completion of the device setup process.

The workaround for this issue is to [download the latest build and reflash the device](/hololens/hololens-recovery#clean-reflash-the-device), and then proceed with the initial device setup process. This practice allows the device to acquire a datetime that is within the threshold required during initial device setup.

> [!NOTE] 
> If the device is registered for Autopilot, this error does not occur because Autopilot automatically forces a datetime sync.

## Sometimes Settings app won't open after update

There are two options to resolve this issue. Users can perform a clean flash of their device by [downloading the latest build and reflashing the device](/hololens/hololens-recovery#clean-reflash-the-device). 

Alternatively, users can follow these steps to fix the Settings app:

1. Get microsoft.ui.xaml.2.4.3 ARM64 appx package
    1. Download nupkg from https://www.nuget.org/api/v2/package/Microsoft.UI.Xaml/2.4.3


    1.  Rename nupkg to microsoft.ui.xaml.2.4.3.nupkg.zip


   1. Extract zip file and copy the arm64 xaml appx package from tools\AppX\arm64\Release\Microsoft.UI.Xaml.2.4.appx
   
1. Depending on your preferred method of app deployment, you can select one of the options from [App Management:  Overview](/hololens/app-deploy-overview). The recommendation for the Settings app is:


    1. If small deployment/single device, copy appx to device (USB drive or MTP), click on the appx from File Explorer.


    1. If large deployment with MDM, deploy the appx as a LOB app through MDM. There’s no need for more licenses or certificates.

## Update indicator may still be visible after OS update

After taking an OS update, users may still see the [update indicator](hololens-release-notes.md#update-indicator) menu even though there is no other update available.

### Workaround for update indicator

In most cases, the update indicator menu corrects itself within one hour.  No further action is required. It is best to allow the update indicator time to clear on its own, before rebooting the device. If the issue does not resolve itself after one or two days, reflash the device.

## Resetting a device with low space doesn't reset

When resetting a device that has low disk space, under 6 GB of free space, the user finds that it fails to reset. Instead it starts the restart process but fail to complete, resulting in the user needing to reflash the device to use it again.

### Who is affected - Low space reset

- Devices that are lower than 6 GB in space and that reset via the Settings app.
- Devices that are lower than 6 GB in space and, which are issued a remote wipe from Intune

### Who is not affected - Low space reset

- Devices that are reset with sufficient free space over 6 GB
- Devices that are wiped remotely with sufficient free space over 6 GB
- Devices that are flashed via ARC

### Workaround - Low space reset

- Delete files or apps until you have more than 6 GB of free storage space on the device. You can check free space via **Settings** -> **System** -> **Storage**. While there, you can enable or run storage sense to help you clear up space more easily.
- [Reflash the device using manual flashing mode](hololens-recovery.md#manual-flashing-mode-procedure). This step can be done to either bypass making free space, or to recover from the bad state created by resetting with low space.

## Remote Wipe doesn't remove device from Intune

When deleting a HoloLens device from Intune [via the Wipe command](hololens-recovery.md#wipe-the-device), the device is sent the wipe command. While this command wipes the device, Intune won't receive confirmation that the HoloLens was wiped. This inconsistency leaves the Wipe button as clicked, and "Wipe pending..." for the device.

![Wipe pending](./images/wipe-pending.jpg)

### Workaround for remote wipe

Immediately after selecting **Wipe** we suggest also selecting the **Delete** button next to wipe. Otherwise,device objects may remain or another known issue may arise for [Autopilot](#why-do-i-see-0x80180014-during-autopilot).

## Devices not getting the latest feature updates

You may notice that your devices are updating but not updating to the latest feature releases. If your device version is newer than 19041.1146, but the major build number is still 19041 then you’re still on an older servicing train.

### Symptom

Devices keep receiving servicing updates instead of FE updates.

### Who does this affect

Users who use “Feature updates for Windows 10 and later” instead of “Update rings for Windows 10 and later” to manage their devices.

![Feature update bad selection](./images/endpoint-update-select.png)

### Who is not affected

Users who didn't try to use “Feature updates for Windows 10 and later” to manage their devices.

### How to check if devices are subject to Intune feature update management, and how to opt out

You need your Microsoft Entra tenant ID. Here's [how to find your Microsoft Entra tenant ID](/azure/active-directory/fundamentals/active-directory-how-to-find-tenant).

1. Use Get azureADDevice beta Graph API to check against the Microsoft Entra device to determine if it's enrolled to update management.


```yaml
{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#admin/windows/updates/updatableAssets",
    "value": [
        {
            "@odata.type": "#microsoft.graph.windowsUpdates.updatableAssetGroup",
            "id": "c1758f08-18e6-4335-98fb-91dd8d17fc3c"
        },
        {
            "@odata.type": "#microsoft.graph.windowsUpdates.updatableAssetGroup",
            "id": "56142275-3286-41bb-a326-d91c84529b82"
        },
        {
            "@odata.type": "#microsoft.graph.windowsUpdates.azureADDevice",
            "id": "088de54c-c1a9-4c3d-bcdb-c500fd6e6db7",
            "errors": [],
            "enrollments": [
                {
                    "@odata.type": "#microsoft.graph.windowsUpdates.updateManagementEnrollment",
                    "updateCategory": "feature"
                }
            ]
        }
    ]
}
```

2. If device is enrolled, unenrollAssets Graph API can be used to unenroll a HoloLens device subject to Intune feature update.

```yaml
{
  "updateCategory": "String",
  "assets": [
    {
      "@odata.type": "#microsoft.graph.windowsUpdates.azureADDevice",
      "id": "088de54c-c1a9-4c3d-bcdb-c500fd6e6db7"
    }
  ]
}
```

3. Once the device is unenrolled then use Get azureADDevice or List azureADDevice resources to check if the device has unenrolled successfully.

## Why do I see 0x80180014 during Autopilot?

This error is typically encountered during device reset and reuse flows where a HoloLens device goes through Autopilot at least once. In order to resolve this issue, [delete the device from Microsoft Intune](/mem/autopilot/troubleshoot-device-enrollment#error-code-0x80180014-when-re-enrolling-using-self-deployment-or-pre-provisioning-mode) and reset it again to complete Autopilot flow.

For more info, refer to [troubleshooting steps on the autopilot page.](hololens2-autopilot.md#issue---mdm-enrollment-fails-with-error-0x80180014-error-code-during-autopilot)

## Microsoft Store error code 0x80131500

Some users may experience the Microsoft Store working not as expected, and see the error code 0x80131500. This is an issue caused by the region set on the HoloLens not being available in the Microsoft Store app on HoloLens. If you encounter error code 0x80131500, to work around:

1. Set Settings > Time & Language > Region > Country or region, to one of the following options:
    - United States, Japan, Germany, Canada, United Kingdom, Ireland, France, Australia, New Zealand.
1. Restart the Store app.
1. For the whole device to reflect the change, the device needs to be restarted.

The HoloLens team is working on adding support for more regions.

See here [for countries or regions to buy HoloLens 2.](hololens2-purchase.md)

## File Explorer and pickers can't select OneDrive

There were changes and updates to the OneDrive app over time. If you were previously using the File Explorer, or a file picker app to select files from OneDrive, you find this is no longer available since the [previously fixed OneDrive UWP app issue](#fixed---onedrive-uwp-app-doesnt-work-for-azure-ad-users). This issue is because the new app doesn't register itself as a file picker or share target.

**Work around** : Use the OneDrive app and move files locally to the device as needed.

For code samples using OneDrive via Microsoft Graph APIs, visit the [developer documentation for OneDrive.](https://developer.microsoft.com/onedrive)

## Microsoft Edge fails to start the microphone

When users using Microsoft Edge the microphone can fail to start, thus not being usable to interact with Microsoft Edge in HoloLens. This known issue is related to the version of the Microsoft Edge app.  Don't reflash your device to an earlier version as this doesn't fix this issue.

### Who is affected?

Users who have Microsoft Edge version 93, 94, or 95.
You can check which version of Microsoft Edge you have by using the Microsoft Store app, then select the "See more" button represented by the **...** then select **Downloads and updates**.

### Work around

The current fix is in version 96, which is available to users who have enrolled in Microsoft Edge Insiders. This fix is different than enrolling your device as a Windows Insider. Read these instructions for details on [how to enroll into Microsoft Edge’s insider program.](hololens-new-edge.md#microsoft-edge-insider-channels)

## Auto-login asks for log-in

A HoloLens 2 device can be configured to automatically log in through **Settings** -> **Accounts** -> **Sign-in Options** -> and under **Required** setting the value to **Never**. Some users may be required to log in to the device again during a substantially large update, such as a feature update. This behavior is a **known issue**.

Example of when this behavior could occur:

- Updating a device from Windows Holographic, version 2004 (Build 19041.xxxx) to Windows Holographic, version 21H1 (Build 20346.xxxx)
- Updating a device to take a large update on the same major build, for example, Windows Holographic, version 2004 to Windows Holographic, version 20H2
- Updating a device from a factory image to the latest image

This shouldn't occur during:

- Devices taking a monthly servicing update

Work around methods:

- Sign-in methods such as PIN, Password, Iris, Web Authentication, or FIDO2 keys.
- If device PIN can't be remembered, and other authentication methods aren't available, then a user can use [manual reflashing mode](hololens-recovery.md#manual-flashing-mode-procedure).

[Back to list](#list)

## Some users may encounter an update failure with Insider build 20346.1466

If a user takes an update to the Insider flight, 20346.1466, and it doesn’t appear to be finishing the boot, a clean reflash may be required to move forward again. To see if you encounter this behavior:

1. Reboot – Hold down the power until the LED’s step down.
1. Power up.
1. Confirm you see the Windows flag at the beginning of the boot and it goes black shortly after that view.
1. Connect your HoloLens2 to your PC with USB and run Advanced Recovery companion.
1. Select the HoloLens.
1. If the version says you’re running the 20346.1466 build, you likely hit this issue.

### Who does this tend to affect

Users who have been using their device without flashing it since [Windows Holographic, version 2004](hololens-release-notes-2004.md#windows-holographic-version-2004).

### Users who are typically unaffected

Users who flash their device, or unbox their device, and start using it since [Windows Holographic, version 21H1](hololens-release-notes.md#windows-holographic-version-21h1).

### Workaround for Insider update issue

- [Reflash your device.](hololens-recovery.md#clean-reflash-the-device)

## Microsoft Edge fails to launch

> [!NOTE]
> This issue was originally created with the shipping version of Microsoft Edge in-mind. This issue may be resolved in the [new Microsoft Edge](hololens-new-edge.md). If it is not, file feedback.

A few customers report an issue where Microsoft Edge fails to launch. For these customers, the issue persists through reboot and isn't resolved with Windows or application updates. If you're experiencing this issue and you confirm [Windows is up-to-date](hololens-updates.md#manually-check-for-updates), file a bug from the [Feedback Hub app](hololens-feedback.md) with the following category and subcategory: Install and Update > Downloading, installing, and configuring Windows Update.

There are no known workarounds as we've been unable to root cause the issue so far. Filing a bug via Feedback Hub helps our investigation! This problem is a **known issue**.

[Back to list](#list)

## Keyboard doesn't switch to special characters

There's an issue during OOBE that occurs when the user has chosen a work or school account and is entering their password.  If they try to to switch to the special characters on the keyboard by tapping the &123 button, it doesn't change to special characters. This is a **known issue**.

Work-arounds:

- Close the keyboard and reopen it by tapping the text field.
- Incorrectly enter your password. When the keyboard is relaunched next time, it then works as expected.
- Web Authentication, close the keyboard and select **Sign in from another device**.
- If entering only numbers, a user may press and hold certain keys to open an expanded menu.
- Using a USB keyboard.

This doesn't affect:

- Users who choose to use a personal account.

[Back to list](#list)

## Blue screen after unenrolling from Insider preview on a device flashed with an Insider build

This behavior is an issue affecting that affects users who are were on an Insider preview build, reflashed their HoloLens 2 with a new insider preview build, and then unenrolled from the Insider program. This behavior is a **known issue**.

This behavior doesn't affect:

- Users who aren't enrolled in Windows Insider
- Insiders:
  - If a device is enrolled since Insider builds were version 18362.x
  - If they flashed an Insider signed 19041.x build AND stay enrolled in the Insider program

Work-around:

- Avoid the issue
  - Flash a non-insider build. One of the regular monthly updates.
  - Stay on Insider Preview
- Reflash the device

    1. Put the [HoloLens 2 into flashing mode](hololens-recovery.md) manually by fully powering down while not connect. Then while holding the **Volume up** button, tap the **Power** button.

    1. Connect to the PC and open Advanced Recovery Companion.

    1. Flash the HoloLens 2 to the default build.

[Back to list](#list)

## HoloLens is unresponsive or won't start

If your HoloLens doesn't start:

- If the LEDs next to the power button don't light up, or only one LED briefly blinks, you may need to [charge your HoloLens.](hololens2-charging.md#charging-the-device)
- If the LEDs light up when you press the power button but you can't see anything on the displays, [do a hard reset of the device](hololens-recovery.md#hard-restart-procedure).

If your HoloLens becomes frozen or unresponsive:

- Turn off your HoloLens by pressing the power button until all five of the LEDs turn themselves off, or for 15 seconds if the LEDs are unresponsive. To start your HoloLens, press the power button again.

If these steps don't work, you can try [recovering your HoloLens 2 device](hololens-recovery.md) or [HoloLens (1st gen) device.](hololens1-recovery.md)

[Back to list](#list)

## "Low Disk Space" error

You need to free up some storage space by doing one or more of the following actions:

- Delete some unused spaces. Go to **Settings** > **System** > **Spaces**, select a space that you no longer need, and then select **Remove**.
- Remove some of the holograms that you placed.
- Delete some pictures and videos from the Photos app.
- Uninstall some apps from your HoloLens. In the **All apps** list, tap and hold the app you want to uninstall, and then select **Uninstall**.

[Back to list](#list)

## Calibration fails

Calibration should work for most people, but there are cases where calibration fails.
  
Some potential reasons for calibration failure include:

- Getting distracted and not following the calibration targets
- Dirty or scratched device visor or device visor not positioned properly
- Dirty or scratched glasses
- Certain types of contact lenses and glasses (colored contact lenses, some toric contact lenses, IR blocking glasses, some high prescription glasses, sunglasses, or similar)
- More-pronounced makeup and some eyelash extensions
- Hair or thick eyeglass frames if they're blocking the device from seeing your eyes
- Certain eye physiology, eye conditions, or eye surgery such as narrow eyes, long eyelashes, amblyopia, nystagmus, some cases of LASIK or other eye surgeries

If calibration is unsuccessful try:

- Cleaning your device visor
- Cleaning your glasses
- Pushing your device visor as close to your eyes as possible
- Moving objects in your visor out of the way (such as hair)
- Turning on a light in your room or moving out of direct sunlight

If you followed all guidelines and calibration is still failing, you can disable the calibration prompt in Settings. Also let us know by filing feedback in [Feedback Hub](hololens-feedback.md).

Also see related information for [image color or brightness troubleshooting.](hololens2-fit-comfort-faq.md#hologram-image-color-or-brightness-does-not-look-right)

Setting IPD isn't applicable for HoloLens 2, since the system computes eye positions.

[Back to list](#list)

## Can't sign in because my HoloLens was previously set up for someone else

You can [put the device into **Flashing Mode** and use Advanced Recovery Companion](hololens-recovery.md#clean-reflash-the-device) to recover the device.

[Back to list](#list)

## Unity isn't working

- See [Install the tools](/windows/mixed-reality/install-the-tools) for the most up-to-date version of Unity recommended for HoloLens development.
- Known issues with the Unity HoloLens Technical Preview are documented in the [HoloLens Unity forums](https://forum.unity3d.com/threads/known-issues.394627/).

[Back to list](#list)

## Windows Device Portal isn't working correctly

- The Live Preview feature in Mixed Reality capture may exhibit several seconds of latency.

- On the Virtual Input page, the Gesture and Scroll controls under the Virtual Gestures section aren't functional. Using them has no effect. The virtual keyboard on the virtual input page works correctly.

- After enabling Developer Mode in Settings, it may take a few seconds before the switch to turn on the Device Portal is enabled.

[Back to list](#list)

## The HoloLens Emulator isn't working

Information about the HoloLens emulator is located in our developer documentation.  Read more about [troubleshooting the HoloLens emulator](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator#troubleshooting).

- Not all apps in the Microsoft Store are compatible with the emulator. For example, Young Conker and Fragments aren't playable on the emulator.
- You can’t use the PC webcam in the Emulator.
- The Live Preview feature of the Windows Device Portal doesn't work with the emulator. You can still capture Mixed Reality videos and images.

[Back to list](#list)

## Voice commands aren't working

If Cortana isn't responding to your voice commands, make sure Cortana is turned on. On the All apps list, select **Cortana** > **Menu** > **Notebook** > **Settings** to make changes. To learn more about what you can say, see [Use your voice with HoloLens](hololens-cortana.md).

On HoloLens (1st gen), built-in speech recognition isn't configurable. It's always on. On HoloLens 2, you can choose whether to turn on both speech recognition and Cortana during device setup.

If your HoloLens 2 isn't responding to your voice, make sure Speech recognition is turned on. Go to **Start** > **Settings** > **Privacy** > **Speech** and turn on **Speech recognition**.

[Back to list](#list)

## Hand input isn't working

To ensure that HoloLens can see your hands, you need to keep them in the gesture frame.  The Mixed Reality Home provides feedback that lets you know when your hands are tracked.  The feedback is different on different versions of HoloLens:

- On HoloLens (1st gen), the gaze cursor changes from a dot to a ring
- On HoloLens 2, a fingertip cursor appears when your hand is close to a slate, and a hand ray appears when slates are further away

Many immersive apps follow input patterns that are similar to Mixed Reality Home.  Learn more about using hand input on [HoloLens (1st gen)](hololens1-basic-usage.md#use-hololens-with-your-hands) and [HoloLens 2](hololens2-basic-usage.md#the-hand-tracking-frame).

If you're wearing gloves, some types of gloves don't work with hand tracking.  A common example is black rubber gloves, which tend to absorb infrared light and the depth camera doesn't pick them up.  If your work involves rubber gloves, we recommend trying a lighter color such as blue or gray.  Another example is large baggy gloves, which tend to obscure the shape of your hand. We recommend using gloves that are as form-fitting as possible for best results.

If your visor has fingerprints or smudges, use the microfiber cleaning cloth that came with the HoloLens to clean your visor gently.

[Back to list](#list)

## Can't connect to Wi-Fi

Here are some things to try if you can't connect your HoloLens to a Wi-Fi network:

- Make sure that Wi-Fi is turned on. To check, use the Start gesture, then select **Settings** > **Network &amp; Internet** > **Wi-Fi**. If Wi-Fi is on, try turning it off and then on again.
- Move closer to the router or access point.
- Restart your Wi-Fi router, then [restart HoloLens](hololens-recovery.md). Try connecting again.
- If none of these things work, check to make sure that your router is using the latest firmware. You can find this information on the manufacturer website.

[Back to list](#list)

## Bluetooth devices aren't pairing

If you're having problems [pairing a Bluetooth device](hololens-connect-devices.md), try the following:

- Go to **Settings** > **Devices**, and make sure that Bluetooth is turned on. If it is, turn it off and on again.
- Make sure that your Bluetooth device is fully charged or has fresh batteries.
- If you still can't connect, [restart the HoloLens](hololens-recovery.md).

[Back to list](#list)

## USB-C Microphone isn't working

Some USB-C microphones incorrectly report themselves as both a microphone *and* a speaker. This occurrence is a problem with the microphone and not with HoloLens. When plugging one of these microphones into HoloLens, sound may be lost. Fortunately there's a simple fix.  

In **Settings** -> **System** -> **Sound**, explicitly set the built-in speakers **(Analog Feature Audio Driver)** as the **Default device**. HoloLens should remember this setting even if the microphone is removed and reconnected later.

![Troubleshooting USB-C microphones.](images/usbc-mic-4.png)

## Devices listed as available in Settings don't work

HoloLens (1st gen) doesn't support Bluetooth audio profiles. Bluetooth audio devices, such as speakers and headsets, may appear as available in HoloLens settings, but they aren't supported.

HoloLens 2 supports the Bluetooth A2DP audio profile for stereo playback. The Bluetooth Hands Free profile that enables microphone capture from a Bluetooth peripheral isn't supported on HoloLens 2.

If you're having trouble using a Bluetooth device, make sure that it's a supported device. Supported devices include the following list:

- English-language QWERTY Bluetooth keyboards (you can use these keyboards anywhere that you use the holographic keyboard).
- Bluetooth mice.
- The [HoloLens clicker](hololens1-clicker.md).

You can pair other Bluetooth HID and GATT devices together with your HoloLens. However, you may have to install corresponding companion apps from Microsoft Store to actually use the devices.

[Back to list](#list)
