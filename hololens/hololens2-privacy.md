---
title: HoloLens 2 Privacy and Data Protection
description: Privacy documentation
keywords: HoloLens, GDPR, privacy, PII, data protection
ms.reviewer: sekerawa, evmiller
ms.date: 02/05/2021
ms.service: hololens
ms.topic: concept-article
ms.sitesec: library
ms.localizationpriority:
audience: HoloLens
ms.collection: essentials-privacy
appliesto:
- HoloLens 2
---

# HoloLens 2 Privacy and Data Protection

One of the core elements of the GDPR is ‘data protection by design’. This concept especially applies to mobile devices, like the HoloLens 2, because of their portability, unlimited internet connections and open communication channels. Resultingly, the HoloLens 2’s [security](/hololens/security-architecture) has been redesigned to provide advanced, innovative security and privacy protection, end-to-end, incorporating both Microsoft’s approach to [privacy and GDPR regulations](https://privacy.microsoft.com/).

 >[!NOTE]
> This document does not apply to HoloLens (1st gen).

## Privacy Overview

HoloLens 2 is a self-contained Windows computer, running Windows Holographic, that runs apps and solutions in an immersive mixed reality environment. It can be used as a secure offline device or deployed as a [managed device](/mem/intune/fundamentals/windows-holographic-for-business) within your organization. See the following links to understand how the HoloLens 2 and Microsoft use and protect your data:

1. [Microsoft Privacy Statement - HoloLens](https://privacy.microsoft.com/privacystatement) – expand the **Enterprise and developer** section in the left navigation menu and select **Enterprise and developer software and appliances**. Go to the **HoloLens** section.
2. [Windows 10 and your online services](https://privacy.microsoft.com/windows10privacy)
3. [Windows 10 & Privacy Compliance Guide](/windows/privacy/windows-10-and-privacy-compliance)
4. [Privacy and personal data in Intune](/mem/intune/protect/privacy-personal-data)

## Network Security
Following the HoloLens 2 [Common Deployment Scenarios](/hololens/common-scenarios), your data will be protected by [Azure’s world-class compliance](/azure/compliance/) along with legal/regulatory standards integration. If you are new to Microsoft Entra ID and Dynamics 365 Remote Assist, reference the [Azure and Dynamics 365 accountability readiness checklist for the GDPR](/compliance/regulatory/gdpr-arc-azure-dynamics-windows).

Furthermore, Windows Defender Firewall delivers critical functionality to secure device connectivity. With HoloLens 2, the firewall is always enabled and there are no ways to disable it programmatically or through the UI. When the HoloLens 2 is deployed as a managed device using [Intune](/mem/intune/protect/device-compliance-get-started), more compliance functionality is available with integration for [Endpoint with Microsoft Intune](/mem/intune/protect/advanced-threat-protection) as a Mobile Threat Defense solution.

Learn more about the HoloLens 2 [security and architecture](/hololens/security-architecture).

## OS Security
Updates are done automatically (by default) so your HoloLens 2 is always up to date with the latest release of Windows Holographic and any installed apps. See the following to understand more about how our OS is securely designed:

1. [State separation and isolation](/hololens/security-state-separation-isolation)
1. [Admin-less operating system](/hololens/security-adminless-os)
1. [Limiting password use](/hololens/security-limiting-password-use)

## Physical Security
HoloLens 2 has flash memory that is protected by [BitLocker encryption](/hololens/security-encryption-data-protection). Your device, and its local data, can be flashed offline using [Advanced Recovery Companion](https://www.microsoft.com/p/advanced-recovery-companion/9p74z35sfrs8#activetab=pivot:overviewtab) or remotely wiped via MDM if it has been deployed as a managed device.

## Data Protection
Windows updates are run automatically (by default) and [Azure integration](/hololens/security-encryption-data-protection#Azure-integration) protects data traveling between itself and the cloud.

When deploying HoloLens 2 to external clients, [Dynamics 365 Remote Assist](/hololens/hololens2-deployment-guide) ensures your sensitive company data and resources are both separate and safe.

The sharing of diagnostic data with Microsoft can be manually configured by MDM or by the user during OOBE. There are two choices: Optional diagnostic data and Required diagnostic data. If your original diagnostic setting needs to be changed at a later time for troubleshooting purposes, it can be changed by the user in **Settings -> Privacy -> Diagnostics & Feedback** or the IT Admin (MDM) if it is a managed device. See more about [Diagnostics, feedback, and privacy in Windows 10](https://support.microsoft.com/windows/diagnostics-feedback-and-privacy-in-windows-10-28808a2b-a31b-dd73-dcd3-4559a5199319).

> [!Important]
> Device diagnostic logs contain personally identifiable information (PII), such as about what processes or applications the user starts during typical operations. When multiple users share a HoloLens device (for example, users sign in to the same device by using different Microsoft Entra accounts) the diagnostic logs may contain PII information that applies to multiple users.

There are [several collection methods and data retention policies](/hololens/hololens-diagnostic-logs) for gathering diagnostic data from the HoloLens 2.  For more information about how Microsoft collects and uses diagnostic data, see [Microsoft Privacy Statement - Diagnostics](https://privacy.microsoft.com/privacystatement) - expand **Windows** in the left navigation menu and select **Diagnostics**. Go to the **Diagnostics** section.
