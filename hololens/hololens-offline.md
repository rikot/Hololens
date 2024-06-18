---
title: Manage connection endpoints for HoloLens 
description: Learn how to set up a HoloLens over a Wi-Fi network while managing and configuring connection endpoints.
keywords: hololens, offline, OOBE
audience: ITPro
ms.date: 07/01/2019
ms.assetid: b86f603c-d25f-409b-b055-4bbc6edcd301
ms.custom: 
- CI 111456
- CSSTroubleshooting
ms.topic: article
ms.service: hololens
ms.sitesec: library
ms.localizationpriority: high
appliesto:
- HoloLens (1st gen)
- HoloLens 2
---

# Manage connection endpoints for HoloLens

Some HoloLens components, apps, and related services transfer data to Microsoft network endpoints. This article lists different endpoints and URLs that need to be allowed in your network configuration (e.g. proxy or firewall) for those components to be functional.    

## Near-offline setup

HoloLens supports a limited set of offline experiences for customers who have network environment restrictions. However, HoloLens needs network connection to go through initial device set up and the following URLs have to be enabled:

| Purpose | URL |
|------|------|
| IDPS | https://sdx.microsoft.com/frx/idps |
| [NCSI](/windows/privacy/manage-connections-from-windows-operating-system-components-to-microsoft-services#bkmk-ncsi) |  http://www.msftconnecttest.com/connecttest.txt  |
| AADv9 | https://login.microsoftonline.com/WebApp/CloudDomainJoin/9 |
| AADv10 | https://login.microsoftonline.com/WebApp/CloudDomainJoin/10 |
| Microsoft Entra ID Pin | https://account.live.com/aadngc?uiflavor=win10&showSuccess=1 |
| MSA | https://login.live.com/ppsecure/inlineconnect.srf?id=80600 |
| MSA Pin | https://account.live.com/msangc?fl=enroll |

## Endpoint configuration

In addition to the list above, to take full advantage of HoloLens functionality, the following endpoints need to be enabled in your network configuration.


| Purpose | URL |
|------|------|
| Azure                                               | wd-prod-fe.cloudapp.azure.com                                       |
|                                                     | ris-prod-atm.trafficmanager.net                                     |
|                                                     | validation-v2.sls.trafficmanager.net                                |
| Microsoft Entra multifactor authentication                | https:\/\/secure\.aadcdn.microsoftonline-p.com                         |
| Intune and MDM Configurations                       | activation-v2.sls.microsoft.com/*                                   |
|                                                     | cdn.onenote.net                                                     |
|                                                     | client.wns.windows.com                                              |
|                                                     | crl.microsoft.com/pki/crl/*                                         |
|                                                     | ctldl.windowsupdate.com                                             |
|                                                     | *displaycatalog.mp.microsoft.com                                    |
|                                                     | dm3p.wns.windows.com                                                |
|                                                     | *microsoft.com/pkiops/*                                             |
|                                                     | ocsp.digicert.com/*                                                 |
|                                                     | r.manage.microsoft.com                                              |
|                                                     | tile-service.weather.microsoft.com                                  |
|                                                     | settings-win.data.microsoft.com                                     |
|  Windows Autopilot for HoloLens 2                   | *.microsoftaik.azure.net                                            |
|                                                     | enterpriseregistration.windows.net                                  |
|                                                     | aadcdn.msauth.net                                                   |
|                                                     | aadcdn.msauthimages.net                                             |
|                                                     | aadcdn.msftauth.net                                                 |
|                                                     | aadcdn.msftauthimages.net                                           |
|                                                     | acctcdn.msftauth.net                                                |
|                                                     | acctcdn.msauth.net                                                  |
| Certificates                                        | activation-v2.sls.microsoft.com/*                                   |
|                                                     | crl.microsoft.com/pki/crl/*                                         |
|                                                     | ocsp.digicert.com/*                                                 |
|                                                     | `https://www.microsoft.com/pkiops/`*                                          |
| Cortana and Search                                  | store-images.*microsoft.com                                         |
|                                                     | `www.bing.com/client`                                                 |
|                                                     | www.bing.com                                                        |
|                                                     | `www.bing.com/proactive`                                              |
|                                                     | `www.bing.com/threshold/xls.aspx `                                    |
|                                                     | exo-ring.msedge.net                                                 |
|                                                     | fp.msedge.net                                                       |
|                                                     | fp-vp.azureedge.net                                                 |
|                                                     | odinvzc.azureedge.net                                               |
|                                                     | spo-ring.msedge.net                                                 |
| Device Authentication                               | login.live.com*                                                     |
| Device metadata                                     | dmd.metaservices.microsoft.com                                      |
| Location                                            | inference.location.live.net                                         |
|                                                     | location-inference-westus.cloudapp.net                              |
| Diagnostic Data                                     | v10.events.data.microsoft.com                                       |
|                                                     | v10.vortex-win.data.microsoft.com/collect/v1                        |
|                                                     | https://www.microsoft.com                                                   |
|                                                     | co4.telecommand.telemetry.microsoft.com                             |
|                                                     | cs11.wpc.v0cdn.net                                                  |
|                                                     | cs1137.wpc.gammacdn.net                                             |
|                                                     | modern.watson.data.microsoft.com*                                   |
|                                                     | watson.telemetry.microsoft.com                                      |
| Licensing                                           | licensing.mp.microsoft.com                                          |
| Microsoft Account                                   | login.msa.akadns6.net                                               |
|                                                     | us.configsvc1.live.com.akadns.net                                   |
| Microsoft Edge                                      | iecvlist.microsoft.com                                              |
| Microsoft forward link redirection service (FWLink) | go.microsoft.com                                                    |
| Microsoft Store                                     | *.wns.windows.com                                                   |
|                                                     | storecatalogrevocation.storequality.microsoft.com                   |
|                                                     | img-prod-cms-rt-microsoft-com*                                      |
|                                                     | store-images.microsoft.com                                          |
|                                                     | .md.mp.microsoft.com                                                |
|                                                     | *displaycatalog.mp.microsoft.com                                    |
|                                                     | pti.store.microsoft.com                                             |
|                                                     | storeedgefd.dsx.mp.microsoft.com                                    |
|                                                     | markets.books.microsoft.com                                         |
|                                                     | share.microsoft.com                                                 |
| Network Connection Status Indicator (NCSI)          | www.msftconnecttest.com*                                            |
| Office                                              | *.c-msedge.net                                                      |
|                                                     | *.e-msedge.net                                                      |
|                                                     | *.s-msedge.net                                                      |
|                                                     | nexusrules.officeapps.live.com                                      |
|                                                     | ocos-office365-s2s.msedge.net                                       |
|                                                     | officeclient.microsoft.com                                          |
|                                                     | outlook.office365.com                                               |
|                                                     | client-office365-tas.msedge.net                                     |
|                                                     | https://www.office.com                                                      |
|                                                     | onecollector.cloudapp.aria                                          |
|                                                     | v10.events.data.microsoft.com/onecollector/1.0/                     |
|                                                     | self.events.data.microsoft.com                                      |
|                                                     | to-do.microsoft.com                                                 |
| OneDrive                                            | g.live.com/1rewlive5skydrive/*                                      |
|                                                     | msagfx.live.com                                                     |
|                                                     | oneclient.sfx.ms                                                    |
| Photos App                                          | evoke-windowsservices-tas.msedge.net                                |
| Settings                                            | cy2.settings.data.microsoft.com.akadns.net                          |
|                                                     | settings.data.microsoft.com                                         |
|                                                     | settings-win.data.microsoft.com                                     |
| Windows Defender                                    | wdcp.microsoft.com                                                  |
|                                                     | definitionupdates.microsoft.com                                     |
|                                                     | go.microsoft.com                                                    |
|                                                     | *smartscreen.microsoft.com                                          |
|                                                     | smartscreen-sn3p.smartscreen.microsoft.com                          |
|                                                     | unitedstates.smartscreen-prod.microsoft.com                         |
| Windows Spotlight                                   | *.search.msn.com                                                    |
|                                                     | arc.msn.com                                                         |
|                                                     | g.msn.com*                                                          |
|                                                     | query.prod.cms.rt.microsoft.com                                     |
|                                                     | ris.api.iris.microsoft.com                                          |
| Windows Update                                      | *.prod.do.dsp.mp.microsoft.com                                      |
|                                                     | cs9.wac.phicdn.net                                                  |
|                                                     | emdl.ws.microsoft.com                                               |
|                                                     | *.dl.delivery.mp.microsoft.com                                      |
|                                                     | *.windowsupdate.com                                                 |
|                                                     | *.delivery.mp.microsoft.com                                         |
|                                                     | *.update.microsoft.com                                              |




## References

> [!NOTE]
> If you are deploying D365 Remote Assist, you will have to enable the endpoints listed for SharePoint Online and OneDrive for Business in [Office 365 URLs and IP address ranges](/office365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams).

- [Configure Windows diagnostic data in your organization](/windows/privacy/configure-windows-diagnostic-data-in-your-organization)
- [Manage connection endpoints for Windows 10 Enterprise, version 1903](/windows/privacy/manage-windows-1903-endpoints)
- [Manage connections from Windows 10 operating system components to Microsoft services](/windows/privacy/manage-connections-from-windows-operating-system-components-to-microsoft-services)
- [Manage connections from Windows 10 operating system components to Microsoft services using Microsoft Intune MDM Server](/windows/privacy/manage-connections-from-windows-operating-system-components-to-microsoft-services-using-mdm)
- [Intune network configuration requirements and bandwidth](/intune/fundamentals/network-bandwidth-use#network-communication-requirements)
- [Network endpoints for Microsoft Intune](/intune/fundamentals/intune-endpoints)
- [Office 365 URLs and IP address ranges](/office365/enterprise/urls-and-ip-address-ranges)
- [Prerequisites for Microsoft Entra Connect](/azure/active-directory/hybrid/how-to-connect-install-prerequisites)


## HoloLens limitations

After your HoloLens is set up, you can use it without a Wi-Fi connection, but apps that use Internet connections will have limited capabilities when you use HoloLens offline.
