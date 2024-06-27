---
title: Certificate Manager
description: Learn how to manually install, manage, and remove certificates on HoloLens 2 mixed reality devices.
ms.service: hololens
ms.sitesec: library
ms.topic: article
ms.localizationpriority: Low
ms.date: 06/27/2024
audience: ITPro
appliesto:
- HoloLens 2
---

# Certificate Manager

- Improved auditing, diagnosis, and validation tooling for device security and compliance through the new Certificate Manager. This capability will enable you to deploy, troubleshoot, and validate your certificates at scale in commercial environments.

In Windows Holographic, version 20H2, we are adding a Certificate Manager in the HoloLens 2 Settings app. Go to **Settings > Update & Security > Certificates**. This feature provides a simple and user-friendly way to view, install and remove certificates on your device. With the new Certificate Manager, admins and users now have improved auditing, diagnosis and validation tooling to ensure that devices remain secure and compliant.

- **Auditing:** Ability to validate that a certificate is deployed correctly or to confirm that it was removed appropriately.
- **Diagnosis:** When issues arise, validating that the appropriate certificates exist on the device saves time and helps with troubleshooting.
- **Validation:** Verifying that a certificate serves the intended purpose and is functional, can save significant time, particularly in commercial environments before deploying certificates at larger scale.

To find a specific certificate in the list quickly, there are options to sort by name, store or expiration date. Users may also directly search for a certificate. To view individual certificate properties, select the certificate and click on **Info**.

Certificate installation currently supports .cer and .crt files. Device Owners can install certificates in Local Machine and Current User;  all other users can only install into Current User.

## To install a certificate

1. Connect your HoloLens 2 to a PC.
1. Place the certificate file you want to install in a location on your HoloLens 2.
1. Navigate to **Settings App > Update & Security > Certificates**, and select Install a certificate.
1. Click **Import File** and navigate to the location you saved the certificate.
1. Select **Store Location**.
1. Select **Certificate Store**.
1. Click **Install**.

The certificate should now be installed on the device.

> [!NOTE]
> Adding certificates to Local Machine is only allowed to users who are device owners. Read about [device owners](security-adminless-os.md#device-owner) for details on that concept.

![Certificate viewer in the Settings app under Certificates.](images/certificate-viewer-device.jpg)

![Picture showing how to use Certificate UI to install a certificate in Settings.](images/certificate-device-install.jpg)

## To remove a certificate

> [!WARNING]
> Using Certificate Manager, users can only remove certificates installed directly from the Settings UI. If a certificate has been installed through other means, it must also be removed by the same mechanism and cannot be removed from Certificate Manager. Although you can view MDM-deployed certificates in Certificate Manager, you cannot uninstall them in Certificate Manager. You must uninstall them through MDM.

1. Navigate to **Settings App > Update and Security > Certificates**.
1. Search for the certificate by name in the search box.
1. Select the certificate.
1. Click **Remove**
1. Select **Yes** when prompted for confirmation.

## PFX file support for Certificate Manager

- Introduced in [Windows Holographic, version 21H2](hololens-release-notes.md#windows-holographic-version-21h2).

 We’ve added support to the Certificate Manager to now use .pfx certificates. When users navigate to **Settings** > **Update & Security** > **Certificates**, and select **Install a certificate** the UI now supports .pfx certificate file.
Users can import .pfx certificate, with private key, to user store or machine store.
