---
title: Admin-less operating system security
description: Learn about admin-less operating systems, device owners, and security on HoloLens mixed reality devices.
ms.service: hololens

ms.reviewer: tagran
ms.date: 6/30/2020
ms.topic: article
keywords: security, hololens, adminless, admin-less, operating system, admin-less operating system, admin os, admin-less os, hololens 2, hololens2 security, 
ms.localizationpriority: high

appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Admin-less operating system

HoloLens 2 minimizes the surface area for privilege escalation by disabling support for the Administrators group and limiting all third-party UWP application code to only execute as standard users within the AppContainer sandbox. This code is only granted access to those resources protected by capabilities explicitly manifested in the application for an unelevated user in addition to resources accessible to all AppContainers.
These application capabilities continue to have the three-tiered classification model:
  * General
  * Restricted
  * Windows

Windows components can also leverage the AppContainer sandbox through System UWPs. To learn more about Universal Windows Platform (UWP), see [UWP documentation](/windows/uwp/). Additionally, Windows components with greater privilege reduction needs (like browser content pages or parsers) use the Less Privileged AppContainer (LPAC) sandbox, which cuts off access to the set of resources accessible to all AppContainers.

## Device owner

Finally, the execution of specific device-wide operations, such as joining the device to a tenant or user management, is only permitted for “device owners”. This group is populated by users on the device through one of the following steps:
  * The first user on the device is always designated an Owner. 
> [!IMPORTANT]
>For Microsoft Entra users, the exception to this rule is that if the device is Microsoft Entra joined via Autopilot or bulk Microsoft Entra enrollment, which uses a non-real user. In this case, the first Microsoft Entra user to sign into the device may not be made device owner automatically unless that user has the "Global Administrator" or "Microsoft Entra Joined Device Local Administrator" role assigned in Azure portal. For more information, see the note below.  

  * When a user is promoted to be an Owner from the Settings UX by another Owner on the device.
  * If the device owner is no longer available (leaves the company) and the device is Microsoft Entra joined, the Tenant Admin can change the device owner to a new user in Azure portal. Global Administrators and Microsoft Entra Joined Device Local Administrators of a Microsoft Entra tenant are implicitly signed in as Owners on the device without requiring either of the previous steps.

 IT administrators can manage what apps can access through [Privacy](/windows/client-management/mdm/policy-csp-privacy) policies. 

> [!NOTE]
> To understand more about who is made a device owner on a Microsoft Entra joined device, see [“Assign Local Admin” documentation](/azure/active-directory/devices/assign-local-admin) (but read ‘local admin’ as ‘device owner’ since admin does not exist on HoloLens).

> [!IMPORTANT]
> Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.