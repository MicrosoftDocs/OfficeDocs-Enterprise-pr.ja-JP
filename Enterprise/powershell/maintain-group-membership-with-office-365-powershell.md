---
title: PowerShell を使用して Microsoft 365 グループメンバーシップを管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: PowerShell を使用して Microsoft 365 グループのメンバーシップを管理する方法について説明します。
ms.openlocfilehash: f75587c9c50a1fce3a5abfb00ddba2845318e9c4
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230653"
---
# <a name="maintain-microsoft-365-group-membership-with-powershell"></a><span data-ttu-id="f7bfd-103">PowerShell を使用して Microsoft 365 グループメンバーシップを管理する</span><span class="sxs-lookup"><span data-stu-id="f7bfd-103">Maintain Microsoft 365 group membership with PowerShell</span></span>

<span data-ttu-id="f7bfd-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="f7bfd-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="f7bfd-105">Microsoft 365 の PowerShell を microsoft 365 管理センターの代わりとして使用して、Microsoft 365 のグループメンバーシップを維持することができます。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-105">You can use PowerShell for Microsoft 365 as an alternative to the Microsoft 365 admin center to maintain group membership in Microsoft 365.</span></span> 

> [!TIP]
> <span data-ttu-id="f7bfd-106">ユーザーアカウントとグループ名を指定して、すぐに実行できる PowerShell コマンドを生成するには、この[グループメンテナンス Microsoft Excel ブック](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx)を使用します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-106">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="f7bfd-107">Graph 用 Azure Active Directory PowerShell モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="f7bfd-107">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="f7bfd-108">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="f7bfd-109">ユーザーアカウントをグループのメンバーとして追加または削除する</span><span class="sxs-lookup"><span data-stu-id="f7bfd-109">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="f7bfd-110">**Upn を使用してユーザーアカウントを追加するに**は、ユーザーアカウントのユーザープリンシパル名 (UPN) とグループ表示名を入力し、"<" と ">" 文字を削除して、これらのコマンドを powershell ウィンドウまたは Powershell 統合スクリプト環境 (ISE) で実行します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-110">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="f7bfd-111">**表示名を使用してユーザーアカウントを追加するに**は、ユーザーアカウントの表示名 (例: ベルギー Inda newman) とグループの表示名を入力し、powershell ウィンドウまたは powershell ISE でこれらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-111">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="f7bfd-112">**UPN によってユーザーアカウントを削除するに**は、ユーザーアカウントの upn (例: belindan@contoso.com) とグループの表示名を入力し、powershell ウィンドウまたは powershell ISE で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-112">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="f7bfd-113">**表示名を使用してユーザーアカウントを削除するに**は、ユーザーアカウントの表示名 (例: ベルギー Inda newman) とグループの表示名を入力し、powershell ウィンドウまたは powershell ISE でこれらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-113">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="f7bfd-114">グループのメンバーとしてグループを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="f7bfd-114">Add or remove groups as members of a group</span></span>

<span data-ttu-id="f7bfd-115">セキュリティグループには、他のグループをメンバーとして含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-115">Security groups can contain other groups as members.</span></span> <span data-ttu-id="f7bfd-116">ただし、Microsoft 365 グループはできません。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-116">Microsoft 365 groups, however, cannot.</span></span> <span data-ttu-id="f7bfd-117">このセクションでは、セキュリティグループに対してのみグループを追加または削除するための PowerShell コマンドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-117">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="f7bfd-118">**表示名でグループを追加するに**は、追加するグループの表示名と、メンバーグループを含むグループの表示名を入力して、powershell ウィンドウまたは powershell ISE で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-118">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="f7bfd-119">**表示名によってグループを削除するに**は、削除するグループの表示名と、メンバーグループを含むグループの表示名を入力して、powershell ウィンドウまたは powershell ISE で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-119">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="f7bfd-120">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="f7bfd-120">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="f7bfd-121">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-121">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="f7bfd-122">ユーザーアカウントをグループのメンバーとして追加または削除する</span><span class="sxs-lookup"><span data-stu-id="f7bfd-122">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="f7bfd-123">**Upn でユーザーアカウントを追加するに**は、ユーザーアカウントのユーザープリンシパル名 (UPN) (例: belindan@contoso.com) とグループの表示名を入力して、"<" と ">" 文字を削除し、これらのコマンドを powershell ウィンドウまたは powershell ISE で実行します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-123">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="f7bfd-124">**表示名を使用してユーザーアカウントを追加するに**は、ユーザーアカウントの表示名 (例: ベルギー Inda newman) とグループの表示名を入力し、powershell ウィンドウまたは powershell ISE でこれらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-124">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="f7bfd-125">**UPN によってユーザーアカウントを削除するに**は、ユーザーアカウントの upn (例: belindan@contoso.com) とグループの表示名を入力し、powershell ウィンドウまたは powershell ISE で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-125">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="f7bfd-126">**表示名を使用してユーザーアカウントを削除するに**は、ユーザーアカウントの表示名 (例: ベルギー Inda newman) とグループの表示名を入力し、powershell ウィンドウまたは powershell ISE でこれらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-126">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="f7bfd-127">グループのメンバーとしてグループを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="f7bfd-127">Add or remove groups as members of a group</span></span>

<span data-ttu-id="f7bfd-128">セキュリティグループには、他のグループをメンバーとして含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-128">Security groups can contain other groups as members.</span></span> <span data-ttu-id="f7bfd-129">ただし、Microsoft 365 グループはできません。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-129">Microsoft 365 groups, however, cannot.</span></span> <span data-ttu-id="f7bfd-130">このセクションでは、セキュリティグループに対してのみグループを追加または削除するための PowerShell コマンドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-130">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="f7bfd-131">**表示名でグループを追加するに**は、追加するグループの表示名と、メンバーグループを含むグループの表示名を入力して、powershell ウィンドウまたは powershell ISE で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-131">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="f7bfd-132">**表示名によってグループを削除するに**は、削除するグループの表示名と、メンバーグループを含むグループの表示名を入力して、powershell ウィンドウまたは powershell ISE で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7bfd-132">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="f7bfd-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7bfd-133">See also</span></span>

[<span data-ttu-id="f7bfd-134">PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="f7bfd-134">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="f7bfd-135">PowerShell を使用して Microsoft 365 を管理する</span><span class="sxs-lookup"><span data-stu-id="f7bfd-135">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f7bfd-136">Microsoft 365 の PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="f7bfd-136">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

