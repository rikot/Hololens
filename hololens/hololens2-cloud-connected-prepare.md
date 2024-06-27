---
title: Deployment Guide – Cloud connected HoloLens 2 deployment at scale with Remote Assist - Prepare 
description: Learn how to prepare to enroll HoloLens devices over a Cloud Connected network using Microsoft Entra ID and identity management.
keywords: HoloLens, management, cloud connected, Remote Assist, AAD, Azure AD, MDM, Mobile Device Management
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

# Prepare - Cloud connected Guide

By the end of this article you will have set up Microsoft Entra ID, MDM, and understand more about using Microsoft Entra accounts and network requirements. This section of the guide will help you and your organization get prepared to deploy HoloLens 2 to the cloud and use Dynamics 365 Remote Assist. It will go over the importance of each piece of your infrastructure as well as providing links to guides to help you set up those pieces as needed.

## Infrastructure Essentials

For both personal and corporate deployment scenarios, an MDM system is the essential infrastructure required to deploy and manage Windows 10 Holographic devices. A Microsoft Entra ID P1 or P2 subscription is recommended as an identity provider and required to support certain capabilities.

<a name='azure-active-directory'></a>

### Microsoft Entra ID

Microsoft Entra ID is a cloud-based directory service that provides identity and access management. Organizations that use Microsoft Office 365 or Intune are already using Microsoft Entra ID, which has three editions: Free, Premium P1, and Premium P2 (see [Microsoft Entra editions](https://azure.microsoft.com/documentation/articles/active-directory-editions).) All editions support Microsoft Entra device registration, but Premium P1 is required to enable MDM auto-enrollment which we will be using in this guide later.

> [!IMPORTANT]
> It is essential to have a Microsoft Entra tenant as HoloLens devices do not support on-premises AD join. If you don't already have a Microsoft Entra tenant set up, go to [Create a new tenant in Microsoft Entra](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).

## Identity Management

Employees can use only one account to initialize a device so it&#39;s imperative that your organization controls which account is enabled first. The account chosen will determine who controls the device and influence your management capabilities.

In this guide we have chosen that for the [Identity](/hololens/hololens-identity) used we will use Microsoft Entra accounts, or Microsoft Entra accounts. There are several benefits to Microsoft Entra accounts we would like to use, such as:

- Employees use their Microsoft Entra account to register the device in Microsoft Entra ID and automatically enroll it with the organization&#39;s MDM solution (Microsoft Entra ID+MDM – requires Microsoft Entra ID P1 or P2).
- Microsoft Entra accounts support [Single Sign On](/azure/active-directory/manage-apps/what-is-single-sign-on). When a user signs into Remote Assist, their Identity from the signed in Microsoft Entra user will be recognized and the user will be signed into the app for a streamlined experience.
- Microsoft Entra accounts have additional [authentication options](/hololens/hololens-identity) via [Windows Hello for Business](/windows/security/identity-protection/hello-for-business/hello-identity-verification). In addition to Iris log-in users can sign in from another device or use FIDO security keys.

### Mobile Device Management

Microsoft [Intune](/mem/intune/fundamentals/what-is-intune), part of the Enterprise Mobility + Security, is a cloud-based MDM system that manages devices connected to your tenant. Like Office 365, Intune uses Microsoft Entra ID for identity management, so employees use the same credentials to enroll devices in Intune that they use to sign into Office 365. Intune also supports devices that run other operating systems, such as iOS and Android, to provide a complete MDM solution. For the purposes of this guide, we&#39;ll be focusing on using Intune for enabling a cloud deployment at scale with HoloLens 2.

> [!IMPORTANT]
> It is essential to have Mobile Device Management. If you don&#39;t already have it set up follow this guide and [Get started with Intune](/mem/intune/fundamentals/free-trial-sign-up).

> [!NOTE]
> Multiple MDM systems support Windows 10 and most support personal and corporate device deployment scenarios. MDM providers that support Windows 10 Holographic currently include: AirWatch, MobileIron, and others. Most industry-leading MDM vendors already support integration with Microsoft Entra ID. You can find the MDM vendors that support Microsoft Entra ID in [Azure Marketplace](https://azure.microsoft.com/marketplace/).

## Network

In this setup, we anticipate HoloLens 2 devices connecting to the Internet from any available open Wi-Fi network. Since a user could need to change the network connection based on location, they should learn how to [connect HoloLens devices to Wi-Fi.](/hololens/hololens-network)

For Dynamics 365 Remote Assist there are a variety of network conditions, including bandwidth, latency, jitter, and packet loss, that can impact your video calling experience. Although audio and video calls might be possible in environments with reduced bandwidth, you might experience feature degradation. When using Dynamics 365 Remote Assist on HoloLens here are the network requirements to keep in mind:

**Minimum** : 1.5 Mbps up/down is required for peer-to-peer HD quality video calling with resolution of HD 1080p at 30 fps.

**Optimal:** For peer-to-peer HD quality video calling with resolution of HD 1080p, 4-5 Mbps up/down should be expected.

More information:

- [Network requirements](/dynamics365/mixed-reality/remote-assist/requirements#network-requirements)
- [Network optimization recommendations](/dynamics365/mixed-reality/remote-assist/requirements#dynamics-365-remote-assist-hololens)

### Optional: Connect your HoloLens to VPN

The devices being connected into this guide are going to connect to the network via and external cloud network. It may be that to access company resources you&#39;ll need to connect your devices via VPN. There are several different ways to connect your devices to VPN, both where the end user can connect via using the device UI, or the devices can be managed and receive the VPN profile from either a PPKG or MDM. How to set up VPN won&#39;t be covered in this article, so if you&#39;d like to learn more about the different VPN protocols or ways to manage VPN visit [these guides for information on HoloLens and VPN.](/hololens/hololens-network#vpn)

## Next step

> [!div class="nextstepaction"]
> [Cloud connected deployment - Configure](hololens2-cloud-connected-configure.md)
