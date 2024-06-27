---
title: Planning HoloLens 2 deployment in a commercial environment
description: Learn about the core needs for deploying and managing HoloLens in enterprise environments, including infrastructure, Microsoft Entra ID, and Mobile Device Management.
ms.service: hololens
ms.sitesec: library
ms.assetid: 88bf50aa-0bac-4142-afa4-20b37c013001
audience: ITPro
ms.topic: article
ms.localizationpriority: Low
ms.date: 06/27/2024
appliesto:
- HoloLens 2
---
# Planning HoloLens 2 deployment in a commercial environment

## Overview

HoloLens 2 is a Windows device. It runs on Windows 10 Holographic, which provides organizations with robust, flexible, built-in mobile device and app management technologies.

Windows 10 Holographic supports end-to-end device lifecycle management, giving you control over your devices, data, and apps. HoloLens 2 uses a comprehensive mobile device management solution that enables it to be incorporated into standard lifecycle practices, from device enrollment, configuration, and application management up through maintenance and retirement.

The following steps and video will help guide you through the process of deploying HoloLens 2 within your organization.

<br/>

> [!VIDEO https://channel9.msdn.com/Shows/IT-Ops-Talk/HoloLens-2-Deployment-Overview/player]

| &nbsp; | &nbsp; |
|--|--|
| ![Step 1.](images/1green.png) | <br/> **[Prepare](#prepare)**: &nbsp; Learn about Microsoft tools and services used for deployment.|
| ![Step 2.](images/2green.png) | <br/> **[Configure](#configure)**: &nbsp; Learn about setting up and adding devices to your deployment.|
| ![Step 3.](images/3green.png) | <br/> **[Deploy](#deploy)**: &nbsp; Learn about deploying your applications and devices.|
| ![Step 4.](images/4green.png) | <br/> **[Maintain](#maintain)**: &nbsp; Learn about maintaining and managing your deployment.|

## Before you start

If you already know the basics of HoloLens, you can skip this step.  If not, you can learn:

- [What HoloLens can do for you](hololens-commercial-features.md)
- [Where to buy HoloLens 2](hololens2-purchase.md)
- [What editions are available](hololens2-options.md)
- [About licensing requirements](hololens-licenses-requirements.md)

You can start learning to use HoloLens 2 by:

- [Understanding how it works in your environment](hololens-environment-considerations.md)
- [Setting up HoloLens2 for the first time](hololens2-setup.md)
- [Learning to navigate, manage, and manipulate holograms](holographic-home.md)

### Deployment types

Learn about the [Common Deployment Scenarios](hololens-requirements.md):

- [Cloud Connected deployments](hololens2-cloud-connected-overview.md)
- [Corporate Connected deployments](hololens2-corp-connected-overview.md)
- [Restricted offline deployments](hololens-common-scenarios-offline-secure.md)

The deployment method for your commercial device deployment will depend on your use case.

|Use case | What it will do |
| --- | --- |
|Remote Assistance  |Enable your employees to remote in an expert anytime they need it. |
|Guides & Task Management  |Walk employees step-by-step through guided experiences to help them complete tasks faster and more accurately than ever before. |
| Restricted offline device deployment | Lock down HoloLens 2 for use in secure environments |
|Training & Simulation |Train and onboard new employees faster than ever using a "learning by doing" approach. |
|Design & Prototyping  |Convert your CAD and BIM files to 3D digital twins to quickly iterate and collaborate on new product designs. |
|Sales Assistance  |Carry less inventory and close large ticket sales faster by using mixed reality to showcase any configuration or customization to your customer. |
|Contextual Data Overlays  |Make pertinent and real-time data available when and where it is needed, enabling your employees to make better, faster, more informed decisions. |

The tools and processes you use to deploy HoloLens 2 will vary depending on your use case, so determine your objectives before proceeding.

## Prepare

Learn about the tools and services you'll need for your HoloLens device deployment.

Microsoft tools and services used for deployment:

- [What is the Microsoft Store for Business?](app-deploy-store-business.md)
- [What is Microsoft Entra ID?](/azure/active-directory/fundamentals/active-directory-whatis)
- [What is Windows Autopilot?](/mem/autopilot/windows-autopilot)
- [What is Microsoft Intune?](/mem/intune/fundamentals/what-is-intune)
- [What is Microsoft Endpoint Manager?](/mem/endpoint-manager-overview)

How Microsoft tools and services used to deploy HoloLens 2 devices:

- [Find, install, and uninstall HoloLens applications](holographic-store-apps.md)
- [Manage user identity and login for HoloLens](hololens-identity.md)
- [Windows Autopilot for HoloLens 2](hololens2-autopilot.md)
- [Enroll HoloLens in Modern Device Management](hololens-enroll-mdm.md)
- [Using Endpoint Manager Intune to manage HoloLens devices](hololens-mdm-configure.md)
- [Manage HoloLens devices with Intune](/mem/intune/fundamentals/windows-holographic-for-business)

## Configure

Learn about setting up a new network for your HoloLens 2 devices and adding them to a Microsoft Entra tenant.

### Identity

- [Create a new tenant](/azure/active-directory/develop/quickstart-create-new-tenant)
- [Create Azure Users and Groups](hololens2-cloud-connected-configure.md#azure-users-and-groups)
- [Manage user identity and login for HoloLens](hololens-identity.md)
- [Share your HoloLens with multiple users](hololens-multiple-users.md)
- [Limit password use](security-limiting-password-use.md)
- [Apply application licenses](hololens2-cloud-connected-configure.md#application-licenses)

### Network

- [Prepare certificates and network profiles to meet company requirements](hololens-certificates-network.md)
- [Configure your network for HoloLens](hololens-commercial-infrastructure.md)
- [Learn how to connect HoloLens to a network](hololens-network.md)
- [Manage connection endpoints for HoloLens](hololens-offline.md)

### Device Management

- [Configure Autopilot for HoloLens 2](hololens2-autopilot.md)
- [Enroll HoloLens automatically](hololens-enroll-mdm.md)
- [Register HoloLens devices with Windows Autopilot](hololens2-autopilot-registration-support.md)
- [Manage HoloLens devices with Microsoft Endpoint Manager](hololens-mdm-configure.md)
- [Configure HoloLens by using a provisioning package](hololens-provisioning.md)

## Deploy

Learn about distributing your HoloLens 2 applications and validating your HoloLens 2 devices.

- [Application deployment overview](app-deploy-overview.md)
- [Deploy apps to your HoloLens devices](app-deploy-intune.md)
- [Update your LOB apps through your MDM system or the Microsoft Store](app-deploy-overview.md)
- [Deploy apps via Microsoft Store for Business](app-deploy-store-business.md)
- [Deploy apps using provisioning packages](app-deploy-provisioning-package.md)
- [Install apps using the App Installer app](app-deploy-app-installer.md)

## Maintain

Learn about updating, validating, supporting, and managing your HoloLens 2 device deployments.

### Updates

- [Windows Update for Business](hololens-updates.md)
- [HoloLens 2 release notes](hololens-release-notes.md)
- [Insider preview updates](hololens-insider.md)

### Validation

- [Update HoloLens automatically](hololens-updates.md)
- [Enrolling HoloLens devices when MAC addresses are restricted](mac-address-options.md)
- [Use Certificate Manager to install or remove certificates](certificate-manager.md)
- [Validate HoloLens enrollment](hololens2-corp-connected-deploy.md#enrollment-validation)
- [Verify that apps are operating effectively](hololens2-corp-connected-deploy.md)
- [Validate HoloLens WiFi certificates](hololens2-corp-connected-deploy.md#wi-fi-certificate-validation)

### Support

Self troubleshoot:

- [HoloLens device troubleshooting](hololens-troubleshooting.md)
- [Holograms and interactions troubleshooting](hololens-faq.md)
- [Display troubleshooting](hololens2-display.md)
- [Troubleshooting implementation and managed devices](hololens2-enterprise-troubleshooting.md)
- [HoloLens 2 Cleaning FAQ](hololens2-maintenance.md)
- [Restart, reset, or recover HoloLens](hololens-recovery.md)

Get help:

- [Microsoft HoloLens support](hololens2-support.md)
- [How to give Feedback](hololens-feedback.md)
- [HoloLens Community](hololens2-support.md#community-help-options)
- [Stack Overflow support](hololens2-support.md#post-a-question-on-stack-overflow)
