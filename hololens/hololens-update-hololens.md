---
title: Update HoloLens 2
description: Learn how to check your HoloLens build number, keep up to date with device updates, join the Insiders Program, and roll back updates.
keywords: how-to, update, roll back, HoloLens, check build, build number
ms.service: hololens
ms.sitesec: library
ms.topic: article
ms.localizationpriority: Low
ms.date: 06/27/2024
audience: ITPro
ms.reviewer: 
appliesto:
- HoloLens 2
---

# Update HoloLens 2

## Overview

We’re always working on new features, bug fixes, and security updates. You'll be notified when these updates are ready.

Based on your preference, your HoloLens will automatically download and install system updates whenever it is plugged in to power, connected to the Internet, and even in standby.

To ensure your HoloLens is always updated, leave it plugged in with the charger that came with it. You also want your HoloLens connected to the internet. This way, it will automatically download and install system updates.

With Windows Update service, you’ll control multiple aspects of the update process, such as which devices get which updates at what time. This control is helpful because you can roll out updates to a subset of HoloLens devices for testing. Then, roll out updates to the remaining ones. Or, you can define different update schedules for different types of updates.

## Types of updates

For HoloLens, you can automatically manage two types of updates.

- Feature updates: released two times a year.
- Quality updates: include critical security updates. They’re released monthly, or as required.

Use **Update**/**AllowAutoUpdate** to manage scanning, downloading, and installation of updates.

## Scheduling updates

You can also set an update schedule. It can be on a particular day, or every day, at a particular time. For instance, at 5 p.m., or outside of active hours.

Finally, a few words about planning your update strategy. We support update deferrals, so you can decide how long to wait after Microsoft releases an update to install that update on devices.

Sometimes a company likes to try all the new features first to make sure everything works, and they are familiar with the new updates so their support team is prepared. Once they’ve confirmed that all is good, they roll out the updates to the entire company. By associating subsets of your devices with different deferral policies, known as update rings, you can coordinate an update rollout strategy for your organization.

Check this guide for [how to optimize your HoloLens updates](hololens-updates.md#how-to-optimize-hololens-updates).

## HoloLens update tools

This section will walk you through HoloLens tools for:

- checking for updates
- manually updating HoloLens
- viewing your current operating system version (build number)
- rolling back to an older update

### Check for updates and manually update

You can check for updates anytime in settings.  To see available updates and check for new updates:

1. Open the **Settings** app.
1. Navigate to **Update & Security** > **Windows Update**.
1. Select **Check for updates**.

If an update is available, it will start downloading the new version. After the download is complete, select the **Restart Now** button to trigger the installation. If your device is below 40% and not plugged in, restarting will not start installing the update.

While your HoloLens is installing the update, it will display spinning gears and a progress indicator. Do not turn off your HoloLens during this time. It will restart automatically once it has completed the installation.

HoloLens applies one update at a time.  If your HoloLens is more than one version behind the latest, you may need to run through the update process multiple times to get it fully up to date.

### Check your operating system version (build number)

You can verify the system version number (build number) by opening **Settings** and select **System** > **About**.

### Go back to a previous version

In some cases, you might want to go back to a previous version of the HoloLens software. The recommended steps are:

1. Contact Support to see if they can fix your issue.
    1. Ensure that **Optional** or **Full** telemetry is enabled -  this makes your bug more actionable and easier for engineers to diagnose.
    1. In [File Feedback](hololens-feedback.md) be as descriptive as possible. Take note of the title, or use the share feature so you can share your bug with Support.
    1. Contact [Support](https://aka.ms/hlsupport). If your issue is one that needs to be solved by returning to a previous version, they can supply you the FFU to flash your device.

1. Alternatively, you can [reflash your HoloLens 2 with the Advanced Recovery Companion](hololens-recovery.md#clean-reflash-the-device). When you flash your device choose which version you want to flash to:

    - You can download the [most recent HoloLens 2 release](https://aka.ms/hololens2download).
    - You can use the default build that ARC hosts.
    - You can use a build Support provided you with.

> [!NOTE]
> Going back to an earlier version deletes your personal files and settings.

Additionally, if you would like to stay on your currently installed release, you can also manually [pause updates](hololens-updates.md#pause-updates-via-device). This will give the Engineering Team time to fix the issue.

## Windows Insider Program on HoloLens

Want to see the latest features in HoloLens?  If so, join the Windows Insider Program; you'll get access to preview builds of HoloLens software updates before they're available to the general public.

[Get Windows Insider preview for Microsoft HoloLens](hololens-insider.md).
