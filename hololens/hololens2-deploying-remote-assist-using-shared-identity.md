---
title: Deploying Remote Assist using a shared identity across multiple users
description: This article contains high-level steps involved in deploying Remote Assist using shared Microsoft Entra identity across multiple users. The guidance provided in this document focuses on provisioning Microsoft Entra user accounts, assigning required licenses and HoloLens 2 device configuration for a shared device environment. For more detailed scenario-based deployment guidance, refer to [Common Deployment Scenarios](hololens-requirements.md).
ms.service: hololens
ms.date: 11/15/2021
ms.localizationpriority:
ms.topic: article
audience: HoloLens 2
keywords: HoloLens, shared device, deployment
appliesto:
- HoloLens 2
---

# Deploying Remote Assist using a shared identity across multiple users

This article contains high-level steps involved in deploying Remote Assist using shared Microsoft Entra identity across multiple users. The guidance provided in this document focuses on provisioning Microsoft Entra user accounts, assigning required licenses and HoloLens 2 device configuration for a shared device environment. For more detailed scenario-based deployment guidance, refer to [Common Deployment Scenarios](hololens-requirements.md).

## Deployment Tasks

<a name='1-azure-ad-accounts'></a>

### 1. Microsoft Entra accounts

Create Microsoft Entra security groups and shared Microsoft Entra user accounts to be used to log in to HoloLens 2 devices.

1. Login to [Microsoft Entra admin center](https://aad.portal.azure.com/) as at least a Groups Administrator and User Administrator.
1. Navigate to [New Group admin center](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/AddGroupBlade) blade and create a Microsoft Entra ID **Security** Group to manage the HoloLens 2 shared user accounts. See [Create a basic group and add members](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal#create-a-basic-group-and-add-members) for step-by-step instructions.
1. Navigate to [New user - Microsoft Entra admin center](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/MsGraphUsers) blade and create new user accounts to be shared by multiple people to log in to the HoloLens 2 device. One Microsoft Entra user account per HoloLens 2 device is recommended. For step-by-step instructions, see [Add or delete users](/azure/active-directory/fundamentals/add-users-azure-active-directory).
1. Navigate to [Groups - Microsoft Entra admin center](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups), select the *Microsoft Entra security group name* -> **Members** -> + **Add members** and add the above user accounts to the security group. For step-by-step instructions, see [Add or remove group members](/azure/active-directory/fundamentals/active-directory-groups-members-azure-portal).

### 2. License Assignments

Assign required licenses to the Microsoft Entra user accounts.

1. You can assign licenses required to use Dynamics 365 Remote Assist on HoloLens 2 to a user or user group. To assign licenses to a user group, follow [Assign licenses to a group](/azure/active-directory/enterprise-users/licensing-groups-assign) step-by-step guide to assign the following licenses. To assign licenses to a user follow [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users) step-by-step guide to assign the following licenses.
    - Dynamics 365 Remote Assist
    - Microsoft Teams
    - Common Data Service for Remote Assist

    For more information, see [Requirements for Dynamics 365 Remote Assist](/dynamics365/mixed-reality/remote-assist/requirements#dynamics-365-remote-assist-app-user).

1. To manage HoloLens 2 using Microsoft Endpoint Manager (Intune), follow [Assign Microsoft Intune licenses](/mem/intune/fundamentals/licenses-assign) step-by-step guide to assign the following licenses.
    - Microsoft Intune

1. To use advanced capabilities of Remote Assist, like accessing OneDrive files, scheduling one-time call, and integrating with Dynamics 365 Field Service you must assign another licenses to the HoloLens 2 user accounts. For more information, see [Requirements for Dynamics 365 Remote Assist](/dynamics365/mixed-reality/remote-assist/requirements#dynamics-365-remote-assist-app-user).

> [!NOTE]
> For more information, see [Scenarios, limitations, and known issues using groups to manage licensing in Microsoft Entra ID](/azure/active-directory/enterprise-users/licensing-group-advanced).

### 3. Device Configuration

To share HoloLens 2 devices with multiple people using shared Microsoft Entra user accounts, configure the following to secure user credentials and restrict apps to be used by the HoloLens 2 users. Follow [Set up your HoloLens 2](hololens2-start.md) to set up the HoloLens 2 devices for first time, using the shared Microsoft Entra user accounts created in Microsoft Entra accounts section above. Use one Microsoft Entra user account per HoloLens 2 device. During HoloLens 2 initial setup skip IRIS login configuration and configure Windows Hello PIN to log in into the device (see more details below).

#### Login PIN

Use Windows Hello PIN to log in to HoloLens 2 devices. Do not share shared account passwords with end users. Configuring Windows Hello PIN allows you to not share the user account password with end users and allows end users to log in to HoloLens 2 devices using Windows Hello PIN configured for the user account on a specific HoloLens 2 device. The configured Windows Hello PIN is cryptographically tied to the HoloLens 2 device and cannot be used to log in to the user account using a browser on a PC or on a different HoloLens 2 device.

For more information, see [Share your HoloLens with multiple people](hololens-multiple-users.md).

#### Auto Login

You can also use AutoLogonUser policy to automatically log in to the device with an identity tied to that device. This bypasses the HoloLens 2 login experience, and the user will be able to pick up the device and start using the device straight away.
For more information, see [Auto login policy controlled by CSP](hololens-release-notes.md#auto-login-policy-controlled-by-csp).

#### Kiosk Mode

For shared HoloLens 2 devices, Kiosk mode is recommended to control which applications are shown in Start menu when a user signs-in to HoloLens. By just allowing only required apps like Remote Assist, you can restrict users signing into the user account settings page using Edge browser by SSO and access user account details inside HoloLens 2 device.

- **If you use Microsoft Endpoint Manager (Intune) to manage the devices**

    Navigate to [Microsoft Endpoint Manager admin center](https://endpoint.microsoft.com/), and create a single or multiple app kiosk mode configuration in [Devices | Configuration profiles](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/configurationProfiles) blade.

- **If you use Provisioning Packages to manage the devices**

    Use Windows Configuration Designer to configure and deploy single or multiple app kiosk mode provisioning packages.
For more information, see [Set up HoloLens as a kiosk](hololens-kiosk.md?tabs=intunecustom%2Cnonaadlogon#steps-in-configuring-kiosk-mode-for-hololens).

#### Windows Defender Application Control (WDAC)

WDAC allows you to configure HoloLens to block the launch of apps. It is different from the Kiosk mode, where the UI hides the apps but they can still be launched. With WDAC, you can see the apps tile but they cannot be launched. For more information, see [Windows Defender Application Control (WDAC)](windows-defender-application-control-wdac.md).

## Limitations

Using shared Microsoft Entra account has the following limitations (including but not limited to):

1. Identity – Users cannot use IRIS to sign in on the HoloLens 2 device and are unable to access their work account related content in Microsoft 365.
1. Caller ID / Contacts – Accessing a user’s personal contacts list / most recently called contacts is not possible, and caller ID will show the shared account name rather than the user’s name.
1. User-Based Workflows – It is not possible to use the advanced integrations with field service, as the user being “assigned” work items, is not the user signed into Remote Assist.
1. PIN Sharing – As IRIS sign-in is not possible, Windows Hello PIN number must be shared between the users.

## Issues

Using shared Microsoft Entra account poses the following issues to be addressed (including but not limited to):

1. Lack of accountability – With a shared account, there is no way to prove who has used the device, and what was done with the device.
1. Lack of auditing – Audit records will be incomplete, and in the event of an incident, it could be impossible to identify the user.
1. Lacks individual tracking / analytics.
1. Permissions – Advanced permissions cannot be done on a shared account basis.
1. MFA ownership – multifactor authentication (MFA) should be owned by a central authority for shared accounts.
1. PIN reset – When PIN needs to be reset and knowledge as to who owns the MFA on the devices is challenging.

## Considerations

You must review and make changes to the following Microsoft Entra settings (including but not limited to) when you want to use shared Microsoft Entra user accounts. When enabling and disabling the following Microsoft Entra settings, extreme care should be taken to make sure that changing theses settings does not cause any issues for existing and new user accounts.

1. Review Administrator Portal access setting in [Users | User Settings](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/UserSettings) blade.
1. Review App Registrations setting in [Users | User Settings](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/UserSettings) blade.
1. Review Linked account connections setting in [Users | User Settings](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/UserSettings) blade.
1. Review User features setting in [Users | User features](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/FeatureSettingsBlade) blade.
1. Review Self-service password reset setting in [Password reset | Properties](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/PasswordResetMenuBlade/Properties) blade.
1. Review Join devices to Microsoft Entra setting in [Devices | Device settings](https://aad.portal.azure.com/#blade/Microsoft_AAD_Devices/DevicesMenuBlade/DeviceSettings/menuId/) blade.
1. Review Enterprise State Roaming setting in [Devices | Enterprise State Roaming](https://aad.portal.azure.com/#blade/Microsoft_AAD_Devices/DevicesMenuBlade/RoamingSettings/menuId/) blade.

> [!WARNING]
> Do NOT share, shared account passwords with end users. End users should always use Microsoft Entra account name and associated Windows Hello PIN or use auto login feature to login to HoloLens 2 devices in a shared environment.
