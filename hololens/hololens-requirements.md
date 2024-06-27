---
title: Common Deployment Scenarios
description: Learn more about deploying and managing HoloLens in enterprise environments, including infrastructure, Microsoft Entra ID, and mobile device management.
ms.service: hololens
ms.sitesec: library
ms.assetid: 88bf50aa-0bac-4142-afa4-20b37c013001
audience: ITPro
ms.topic: concept-article
ms.localizationpriority: Low
ms.date: 06/27/2024
appliesto:
- HoloLens 2
ms.collection: essentials-get-started
---

# Common Deployment Scenarios

## Overview

Figuring out how to deploy a new device can be a struggle when you try it the first time. Here, we share different ways to deploy and manage Microsoft HoloLens 2 devices within the organization.

You want solutions - deployed at scale. We want to get you there. Let's first talk about the steps to deploy devices, therefore holograms, to achieve value for your target mixed reality scenario. Whether you are using D365 Remote Assist, Guides, or an Azure mixed reality service-enabled application you created - our Common Deployment Scenarios will guide your journey.

You may be a business decision-maker, IT professional, or an innovation team looking to adopt HoloLens within your organization. As you build from proof of concept to a scaled deployment, our deployment guides make sense of HoloLens within your IT infrastructure - no matter how big or small. The following deployment scenarios are the most common:

| Scenario |Usage | Key points |
|---------|---------|---------|
| [Scenario A: Cloud connected devices](hololens2-cloud-connected-overview.md) | When you first begin your deployment, you may start small and deploy a single device connected to the cloud just to see the basic process. | Devices will be connected to cloud services and public internet. Most suitable for customer use cases, field services, and proof of concept.|
| [Scenario B: Organization's network](hololens2-corp-connected-overview.md) | As you deploy to production at scale, you may need to integrate with your own organization's network. | Devices will be connected to a "Corporate" wi-fi network. Most suitable for Internal users, or use within the corporate environment.|
| [Scenario C: Offline secure environment](hololens-common-scenarios-offline-secure.md) | Some mission-critical processes or some corporate policies may demand the use of offline environments. | Devices will be connected to a highly restrictive network or will be purely offline devices. Most suitable for highly secure environments, or internet connectivity restrictions in remote areas. |
| [Scenario D: Near offline or isolated environments](hololens-common-scenarios-near-offline-restricted.md) | Guidance for deploying where networking cannot be assured or secure environments and cloud tools are desired. | Device setup via a restricted network then used on this network, or taken offline with periodic reconnects for management. Most suitable for restricted or offline scenarios where access to cloud or administrator tools are still desired. |

## Scenario A: Deploy to cloud connected devices

This scenario is comparable to deploying managed mobile devices within a company. HoloLens 2 is deployed for use primarily in environments external to a corporate network. Corporate resources aren't accessed or may be limited through VPN.

[![Scenario A diagram.](images/deployment-guides-revised-scenario-a.png)](images/deployment-guides-revised-scenario-a.png#lightbox)

### When to use

Consider this deployment model for:

* Deploying proof of concept, pilots and field services
* Deploying [Remote Assist](hololens2-options-remote-assist.md)

### Basic Common Configurations

* Wi-Fi networks are typically fully open to the internet and cloud services
* Microsoft Entra join with Mobile Device Management (MDM) Auto Enrollment--MDM (Intune) Managed
* Users sign in with their own corporate account (Microsoft Entra ID)
  * Single or multiple users per device supported
* Varying levels of device lockdown configurations are applied based on specific use cases, from Fully Open to Single App Kiosk.
* One or more applications are deployed via MDM

### Common Challenges

* Determining which MDM configurations to apply to the HoloLens 2 based on scenario requirements

The corresponding Cloud Connected guide covers how to enroll HoloLens 2 into your device management, apply licenses as needed, and validate that your end users are able to immediately use Remote Assist upon device setup.

> [!div class="nextstepaction"]
> [Cloud Connected deployment guide](hololens2-cloud-connected-overview.md)

Use the External Clients guide to deploy devices to a remote site for short-term or long-term external use.

> [!div class="nextstepaction"]
> [Cloud Connected (External Clients) deployment guide](hololens2-deployment-guide.md)

## Scenario B: Deploy inside your organization's network

This scenario is identical to a classic deployment for most Windows 10 PCs. HoloLens 2 is deployed for use primarily on the corporate network with access to internal corporate resources. Internet and cloud services may be limited. 

[![Scenario B1 diagram.](images/deployment-guides-revised-scenario-b-01-1.png)](images/deployment-guides-revised-scenario-b-01-1.png#lightbox)

[![Scenario B2 diagram.](images/deployment-guides-revised-scenario-b-02-1.png)](images/deployment-guides-revised-scenario-b-02-1.png#lightbox)

### When to use

Consider this deployment model for:

* Internal users
* Deploying at scale (Pilot and Production) within the corporate environment

### Basic Common Configurations

* Wi-Fi network is an internal corporate network with access to internal resources, and limited access to the internet or Cloud services.
* Microsoft Entra join with MDM Auto Enrollment
* MDM (Intune) Managed
* Users sign in with their own corporate account (Microsoft Entra ID)
  * Single or multiple users per device supported
* Varying levels of device lockdown configurations are applied based on specific use cases, from Fully Open to Single App Kiosk.
* One or more applications are deployed via MDM

### Common Challenges

* HoloLens 2 doesn't support on premises AD join or System Center Configuration Manager (SCCM). Only Microsoft Entra join with MDM. Many companies today still deploy Windows 10 PCs in this scenario as on premises AD joined devices, managed by SCCM and may not have the infrastructure deployed/configured for managing internal Windows 10 devices via cloud-based MDM solutions.
* As HoloLens 2 is a cloud first device, it relies heavily on internet and cloud connected services for user authentication, OS updates, MDM management, and so on. When connecting to a corporate network, proxy/firewall rules will most likely need to be adjusted to enable access for HoloLens 2 and the applications that run on it.
* Corporate Wi-Fi connectivity typically requires certificates to authenticate the device or user to the network. The required infrastructure or settings to deploy certificates to Windows 10 devices through MDM can be challenging to configure.

The corresponding Corporate Connected guide instructs on how to enroll HoloLens 2 into your existing device management, apply licenses as needed, and validate that your end users are able to operate a Dynamics 365 Guide, as well as use custom line of business apps, after device setup.

> [!div class="nextstepaction"]
> [Corporate Connected deployment guide](hololens2-corp-connected-overview.md)

## Scenario C: Deploy in secure offline environment

This is a typical deployment for highly secure or confidential locations. HoloLens 2 is deployed for use primarily offline with no network or internet access.

[![Offline Secure diagram 1.](images/deployment-guides-revised-scenario-c-01.png)](images/deployment-guides-revised-scenario-c-01.png#lightbox)

### When to use

Consider this deployment model for:

* Highly secure environments where data needs to be retained in house
* "Experiences" where the public will be using the devices
* Internet connectivity issue in the remote area

### Basic Common Configurations

* Wi-Fi connectivity is disabled. Ethernet via USB may be enabled for LAN connectivity if necessary
* Not Managed
* Local user account for device sign-in
  * HoloLens 2 supports only one local account
* Varying levels of device lockdown configurations are applied via Provisioning Packages based on specific use cases. These configurations are typically restricted because of secure environment requirements
* One or more applications are deployed via Provisioning Package

### Common Challenges

* There's a limited set of configurations available through provisioning packages
* Cloud services aren't able to be used, therefore limiting the HoloLens 2 capabilities.
* Higher administrative overhead since these devices have to be set up, configured, and updated manually.

The corresponding Offline secure guide provides instruction for applying a sample Provisioning Package that will lock down a HoloLens 2 for use in secure environments.

> [!div class="nextstepaction"]
> [Offline secure environment deployment guide](hololens-common-scenarios-offline-secure.md)

## Scenario D: Deploy in near offline or isolated environments

This is ideal for devices that may use cloud services in restricted or secure environments with periodic network or internet access.


[![Near offline diagram 1.](images/restricted-deployment-scenario-d.png)](images/restricted-deployment-scenario-d.png#lightbox)

### When to use

Consider this deployment model for:

* Device can be initially connected to a restricted network for setup
* Device can be use on this restricted network or taken offline
* Device is periodically returned to the restricted network for updates and management

### Basic Common Configurations

* Wi-Fi connectivity can be enabled or disabled, but periodic connections are required
* Microsoft Entra ID for sign-in & authentication
* Azure MFA and Windows Hello for Business
* Autopilot for device deployment
* Intune for Device Management
* Windows Update for Device Updates
* Users perform initial sign in when connected then can sign in offline thereafter
  * Multiple users are supported
* Varying levels of device lockdown configurations are applied via Provisioning Packages based on specific use cases. These configurations are typically restricted because of secure environment requirements
* One or more applications are deployed via Provisioning Package

### Common Challenges

* There's a limited set of configurations available through provisioning packages.
* Cloud services are only available when device is connected to a network.
* Devices will need access to relevant endpoints and validation of access may be needed.
* Higher administrative overhead since these devices have to be set up to work while on a restricted network or while offline.

The corresponding restricted or near offline guide provides instruction for applying a sample Provisioning Package that will set up a HoloLens 2 for use in near offline or isolated environments.

> [!div class="nextstepaction"]
> [Restricted or near offline environment deployment guide](hololens-common-scenarios-offline-secure.md)
