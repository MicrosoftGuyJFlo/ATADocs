---
# required metadata

title: Configure SAM-R to enable lateral movement path detection in Azure ATP | Microsoft Docs
description: Describes how to configure SAM-R to enable lateral movement path detection in Azure ATP
keywords:
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/29/2018
ms.topic: get-started-article
ms.prod:
ms.service: azure-advanced-threat-protection
ms.technology:
ms.assetid: b09adce3-0fbc-40e3-a53f-31f57fe79ca3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: itargoet
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

*Applies to: Azure Advanced Threat Protection*

# Install Azure ATP - Step 8

>[!div class="step-by-step"]
[« Step 7](install-atp-step7.md)

## Step 8. Configure SAM-R required permissions

The [lateral movement path](use-case-lateral-movement-path.md) detection relies on queries that identify local admins on specific machines. These queries are performed using the SAM-R protocol, via the Azure ATP Service account created in [Step 2. Connect to AD](install-atp-step2.md).
 
To ensure Windows clients and servers allow Azure ATP account to perform this SAM-R operation, a modification to **Group Policy** must be made to add the Azure ATP service account in addition to the configured accounts listed in the **Network access** policy.

1. Locate the policy:

 - Policy Name:	Network access - Restrict clients allowed to make remote calls to SAM
 - Location: Computer configuration, Windows settings, Security settings, Local policies, Security options
  
  ![Locate the policy](./media/samr-policy-location.png)

2. Add the Azure ATP service to the list of approved accounts able to perform this action on your modern Windows systems.
 
  ![Add the service](./media/samr-add-service.png)

3. The **AATP Service** (the Azure ATP service created during installation) now has the proper privileges to perform SAMR in the environment.

For more on SAM-R and this Group Policy, see the [Network access: Restrict clients allowed to make remote calls to SAM](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-access-restrict-clients-allowed-to-make-remote-sam-calls).


>[!div class="step-by-step"]
[« Step 7](install-atp-step7.md)



## See Also
- [Investigating lateral movement path attacks with Azure ATP](use-case-lateral-movement-path.md)
- [Check out the ATP forum!](https://aka.ms/azureatpcommunity)