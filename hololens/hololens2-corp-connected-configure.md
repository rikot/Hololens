---
title: Deployment Guide - Corporate connected HoloLens 2 with Dynamics 365 Guides - Configure
description: Learn how to set up configurations to deploy HoloLens 2 devices over a corporate Connected network with Dynamics 365 Guides.
keywords: HoloLens, management, corporate connected, Dynamics 365 Guides, AAD, Azure AD, MDM, Mobile Device Management
ms.reviewer: aboeger
ms.date: 06/27/2024
ms.service: hololens
ms.topic: article
ms.sitesec: library
ms.localizationpriority: Low
audience: HoloLens
appliesto:
- HoloLens 2
---

# Configure - Corporate Connected Guide

## Azure Users and Groups

Azure, and Intune by that extension, uses users and groups to help assign configurations and licenses. For the sake of validating this deployment flow and being able to check that you can author and operate a guide, you&#39;ll need a user account.

We can make a single user group specifically for assigning licenses.

If you don't already have access to two Microsoft Entra accounts in a user group that you can use, here are the quick start guides for:

- [How to create a user](/mem/intune/fundamentals/quickstart-create-user)
- [How to create a group](/mem/intune/fundamentals/quickstart-create-group)
- [Add users to a group](/azure/active-directory/fundamentals/active-directory-groups-members-azure-portal) – Add created users to create group
- [Configure Microsoft Entra ID to allow a User Group to join devices](/azure/active-directory/devices/azureadjoin-plan#configure-your-device-settings) – Ensure new user group has permission to enroll devices to Microsoft Entra ID

## Auto Enrollment on HoloLens 2

In order to have a smooth and seamless experience, setting up Microsoft Entra join (AADJ) and Auto Enrollment to Intune for HoloLens 2 devices is the way to go. This allows users to input their organization log-in credentials during OOBE and automatically register with Microsoft Entra ID and enroll the device into MDM.

By using [Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home), we can select services and navigate a few pages until we can select Get a Premium trial. You may notice there's Microsoft Entra ID P1 or P2 and 2 - for Automatic Enrollment P1 is sufficient. We can select Intune and select the user scope for automatic enrollment and select the group that was previously created.

For full details and steps, read the guide on [how to enable auto enrollment for Intune](/mem/intune/enrollment/quickstart-setup-auto-enrollment).

## Corporate Wi-Fi Connectivity

Corporate Wi-Fi connections will commonly require certificate-based authentication for customers using HoloLens 2. You'll need to deploy such certificates by using a Simple Certificate Enrollment Protocol (SCEP) or Public Key Cryptography Standard (PKCS) certificate infrastructure that is integrated with your MDM solution. Using Intune to deploy Wi-Fi profiles, certificates, and proxy settings creates a seamless experience for end users.
 
### Deploy certificates and Wi-Fi profiles

To deploy certificates and profiles through Microsoft Endpoint Manager, follow these steps:

1. Create a profile for each of the Root and Intermediate certificates (see [Create trusted certificate profiles](/intune/protect/certificates-configure#create-trusted-certificate-profiles)). Each of these profiles must have a description that includes an expiration date in DD/MM/YYYY format.

    > [!CAUTION]
    > **Certificate profiles without an expiration date will not be deployed**.

2. Create a profile for each SCEP or PKCS certificates (see [Create a SCEP certificate profile or Create a PKCS certificate profile](/intune/protect/certficates-pfx-configure#create-a-pkcs-certificate-profile)) Each of these profiles must have a description that includes an expiration date in DD/MM/YYYY format.

    > [!CAUTION]
    > **Certificate profiles without an expiration date will not be deployed.**

    > [!Note]
    > As the HoloLens 2 is considered for many to be a shared device, i.e., multiple users per device, it is recommended to deploy Device certificates instead of User certificates for Wi-Fi authentication where possible.

3. Create a profile for your corporate Wi-Fi network (see [Wi-Fi settings for Windows 10 and later devices](/intune/wi-fi-settings-windows)). Within your Wi-Fi profile, you can select to use the proxy settings within your organization.

    Your options:
    - **None**: No proxy settings are configured.
    - **Manually configure**: Enter the **Proxy server IP address** and its **Port number**.
    - **Automatically configure**: Enter the URL pointing to a proxy auto configuration (PAC) script. For example, enter `http://proxy.contoso.com/proxy.pac`.

    For more information on PAC files, see [Proxy Auto-Configuration (PAC) file](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_(PAC)_file) (opens a non-Microsoft site).
 
    > [!Note]
    > It is recommended that the Wi-Fi profile be assigned to Device groups rather than User groups where possible.
     
    > [!Tip]
    > You also can export a working Wi-Fi profile from a Windows 10 PC on your corporate network. This export creates an XML file with all the current settings. Then, import this file into Intune, and use it as the Wi-Fi profile for your HoloLens 2 devices. See [Export and import Wi-Fi settings for Windows devices](/mem/intune/configuration/wi-fi-settings-import-windows-8-1).

1.	[Assign](/mem/intune/configuration/device-profile-assign) the device profiles to the HoloLens device group.

2.	[Monitor](/mem/intune/configuration/device-profile-monitor) the device profiles in Intune.

If there are issues with Wi-Fi profiles, reference [Troubleshoot Wi-Fi device configuration profiles in Intune](/troubleshoot/mem/intune/troubleshoot-wi-fi-profiles).

## Troubleshooting External Internet Access When Corp Connected
When services try to not go through a set Proxy, they may attempt to connect through the firewall. You can add a list of endpoint specifics to your firewall rules to troubleshoot these issues.

If you're blocked at firewall ports, enable some common [endpoints](/hololens/hololens-offline) for HoloLens.

You can also enable the Guides specific ports: [Internet accessible URLs required for connectivity to Microsoft Dynamics CRM Online](https://support.microsoft.com/help/2655102/internet-accessible-urls-required-for-connectivity-to-microsoft-dynami).

## App Deployment

Deploying a LOB app via MDM is a method that's easily scalable and can be automatically deployed to your devices upon enrollment in a created group.

If you're still developing your Apps or don't have one yet, you can use a sample app of the MRTK examples hub. This sample app is ready to use, and won't require the use of either Unity or Visual Studio. [Download the MRTK Examples Sample app](https://aka.ms/HoloLensDocs-Sample-MRTK-Examples-App).

If you would prefer to use your own app or are interested in app development for Mixed Reality, then feel free to review our [Mixed Reality developer documentation](/windows/mixed-reality/design/design).

> [!NOTE]
> The System Requirements for HoloLens devices are based on the architecture of the app build. HoloLens 2 devices use ARM architecture. When building your apps in Visual Studio, ensure that you have selected the correct architecture for the device and include any needed dependencies.

> [!IMPORTANT]
> When deploying LOB apps, it's important to also upload the certificate to Intune, and assign it to the same group that is intended to use the app or it will not install properly.

### Upload and Assign the App

1. Navigate to the [MEM admin center](https://endpoint.microsoft.com/#home).

2. Select **Apps** -> **All apps** and select the **+ Add** button.

3. Underneath Other, Select **Line-of-business app**. Click **select**.

4. Select the app package file, this is your APPXBUNDLE file, or in our case of this example the app is _MRTK Examples Hub\_2.4.2.0\_arm\_Master.appxbundle_.

5. You'll be notified of missing dependencies. In this case, we need to upload _Microsoft.VCLibs.ARM.14.00.appx_. Search for it under **Select a file**.

6. Select OK.

7. In the next screen, the required fields will be auto-filled. Select **Next**.

8. Under Required, add our previously created group to make this app required for the group. This causes the app to automatically download to enrolled devices in the group. Select **Next**.

9. Select **Create**.

Read more: [Assign apps to groups in Microsoft Intune](/mem/intune/apps/apps-deploy#assign-an-app)

## Setup Guides: Application licenses, dataverse, and authoring

In order to use Dynamics 365 Guides, you'll need to do some preparation. There are three areas in which we'll need to prepare; users, dataverse, and the guides themselves.

### Users and application licenses

For someone to use Guides, they'll need to use a Microsoft Entra account, which we have set up in this guide previously.

You'll also need to assign Dynamics 365 Guides license to the user you've created. You'll do this from the [Microsoft 365 admin center](https://admin.microsoft.com/AdminPortal/Home). Also assign the license to your primary Azure Account.

Follow [this short guide](/dynamics365/mixed-reality/guides/setup-step-one#assign-the-dynamics-365-guides-license-to-user-accounts) with pictures for step-by-step instructions on applying application licenses.

### Set up the Dataverse

In order to [set up a production environment](/dynamics365/mixed-reality/guides/setup-step-two#set-up-a-production-environment-for-purchased-licenses-only) you'll need to meet two prerequisites. You must have the [**System Administrator**](/power-platform/admin/database-security) role,  **and**  you must have a [**Power Apps license**](/power-platform/admin/signup-question-and-answer) (or a [**Dynamics 365 Guides license**](/dynamics365/mixed-reality/guides/setup-step-one) that includes a Power Apps license). If following this guide you created the Microsoft Entra ID, then you meet the role requirements for System Administrator. We also have assigned a Guides License in the previous step.

Within this guide to [create a Microsoft Dataverse environment](/dynamics365/mixed-reality/guides/setup-step-two):

1. Start by using the [Power Platform admin center](https://admin.powerplatform.microsoft.com/environments) and creating a New Environment.
2. When creating the **New Environment**, for the **Type** you&#39;ll be selecting **Production**.
3. It's important that you toggle **Create a database for this environment?**  option to  **Yes**.
4. In the  **Add database**  dialog box, set the  **Enable Dynamics 365 apps**  option to  **Yes.**

You'll want to increase the maximum file size of items in your dataverse. Increasing the max file size allows you to upload larger 3D models or video files that you'll use later in your guides. Follow a short guide [to change the maximum upload file size](/dynamics365/mixed-reality/guides/setup-step-two#change-the-maximum-upload-file-size).

Lastly, you'll need to [install and configure the solution](/dynamics365/mixed-reality/guides/setup-step-two#install-and-configure-the-solution). In the [Power Platform admin center](https://admin.powerplatform.microsoft.com/environments), select  **Resources**  \&gt;  **Dynamics 365 apps**, select  **Dynamics 365 Guides**  in the list, and then select  **Install**.

You need [add a Guides security role](/dynamics365/mixed-reality/guides/assign-role) before you’re able to use the apps.

### Create a test Guide on your PC via Authoring

When creating Guides, you'll always start on your PC. Creating the steps, selecting models, and how to anchor the guide. This is followed by placing content for your guide later in authoring mode on your HoloLens device. For the purposes of this guide, we suggest making a short test guide with minimal steps and models.

If you'd like to start learning about authoring for Guides, start here with the [authoring overview](/dynamics365/mixed-reality/guides/authoring-overview). Or to get a fast track overview, watch this short video.

> [!VIDEO https://www.youtube.com/embed/EC24dMlAy90]

## Optional: Kiosk mode

Kiosk mode is a mode that let's an IT Admin configure the start menu's UI to show only a single app, or selection of apps. A kiosk can also be applied to specific users, groups, or at the device level; and in some cases, exclude certain users from the Kiosk still allowing them access to the regular start menu.

Kiosk mode has many different variables, both in scope and configurations that can be set as well as methods of deploying the Kiosk to the HoloLens. Because of all these variables, Kiosk mode is being left as _optional_ for this guide and won't be revisited. If you believe you have a business need to restrict available apps to users or would like to learn more, then feel free to learn how to [Set up HoloLens as a kiosk](/hololens/hololens-kiosk).

## Optional: WDAC

WDAC allows an IT Admin to configure their devices to block the launch of apps on devices. This is different than methods of device restriction, such as Kiosk mode, where the user is presented with a UI that hides the apps on the device, but they can still be launched. While WDAC is implemented, the apps are still visible in the All Apps list, but WDAC stops those apps and processes from being able to be launched by the device user.

For more information, reference [Use WDAC and Windows PowerShell to allow or block apps on HoloLens 2 devices with Microsoft Intune](/mem/intune/configuration/custom-profile-hololens).

[Windows Defender Application Control - WDAC](/hololens/windows-defender-application-control-wdac)

## Next step 
> [!div class="nextstepaction"]
> [Corporate connected deployment - Deploy](hololens2-corp-connected-deploy.md)
