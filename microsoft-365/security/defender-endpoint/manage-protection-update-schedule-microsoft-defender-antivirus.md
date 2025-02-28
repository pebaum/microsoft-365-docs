---
title: Schedule Microsoft Defender Antivirus protection updates
description: Schedule the day, time, and interval for when protection updates should be downloaded
keywords: updates, security baselines, schedule updates
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
search.appverid: met150
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
---

# Manage the schedule for when protection updates should be downloaded and applied

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Applies to:**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

Microsoft Defender Antivirus lets you determine when it should look for and download updates.

You can schedule updates for your endpoints by:

- Specifying the day of the week to check for protection updates
- Specifying the interval to check for protection updates
- Specifying the time to check for protection updates

You can also randomize the times when each endpoint checks and downloads protection updates. See the [Schedule scans](scheduled-catch-up-scans-microsoft-defender-antivirus.md) topic for more information.

## Use Configuration Manager to schedule protection updates

1. On your Microsoft Endpoint Manager console, open the antimalware policy you want to change (click **Assets and Compliance** in the navigation pane on the left, then expand the tree to **Overview** \> **Endpoint Protection** \> **Antimalware Policies**)

2. Go to the **Security intelligence updates** section.

3. To check and download updates at a certain time:
      1. Set **Check for Endpoint Protection security intelligence updates at a specific interval...** to **0**.
      2. Set **Check for Endpoint Protection security intelligence updates daily at...** to the time when updates should be checked.
      3
4. To check and download updates on a continual interval, Set **Check for Endpoint Protection security intelligence updates at a specific interval...** to the number of hours that should occur between updates.

5. [Deploy the updated policy as usual](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## Use Group Policy to schedule protection updates

> [!IMPORTANT]
> By default, Microsoft Defender Antivirus will check for an update 15 minutes before the time of any scheduled scans. Enabling these settings will override that default.

1. On your Group Policy management machine, open the [Group Policy Management Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), right-click the Group Policy Object you want to configure and click **Edit**.

2. In the **Group Policy Management Editor** go to **Computer configuration**.

3. Click **Policies** then **Administrative templates**.

4. Expand the tree to **Windows components** \> **Microsoft Defender Antivirus** \> **Signature Intelligence Updates** and configure the following settings:

    1. Double-click the **Specify the day of the week to check for security intelligence updates** setting and set the option to **Enabled**. Enter the day of the week to check for updates. Click **OK**.
    2. Double-click the **Specify the interval to check for security intelligence updates** setting and set the option to **Enabled**. Enter the number of hours between updates. Click **OK**.
    3. Double-click the **Specify the time to check for security intelligence updates** setting and set the option to **Enabled**. Enter the time when updates should be checked. The time is based on the local time of the endpoint. Click **OK**.

## Use PowerShell cmdlets to schedule protection updates

Use the following cmdlets:

```PowerShell
Set-MpPreference -SignatureScheduleDay
Set-MpPreference -SignatureScheduleTime
Set-MpPreference -SignatureUpdateInterval
```

See [Use PowerShell cmdlets to configure and run Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)  and [Defender cmdlets](/powershell/module/defender/) for more information on how to use PowerShell with Microsoft Defender Antivirus.

## Use Windows Management Instruction (WMI) to schedule protection updates

Use the [**Set** method of the **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) class for the following properties:

```WMI
SignatureScheduleDay
SignatureScheduleTime
SignatureUpdateInterval
```

See the following for more information and allowed parameters:

- [Windows Defender WMIv2 APIs](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## Related articles

- [Deploy Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
- [Manage Microsoft Defender Antivirus updates and apply baselines](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Manage updates for endpoints that are out of date](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Manage event-based forced updates](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Manage updates for mobile devices and virtual machines (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus in Windows 10](microsoft-defender-antivirus-in-windows-10.md)
