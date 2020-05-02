---
title: Office 365 PowerShell を使用してグループメンバーシップを管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
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
description: Office 365 PowerShell を使用して Office 365 のグループのメンバーシップを管理する方法について説明します。
ms.openlocfilehash: 0e6c5f2e27f9d146bb2a053bd3bdb6694fb07276
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004630"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a><span data-ttu-id="f8c7a-103">Office 365 PowerShell を使用してグループメンバーシップを管理する</span><span class="sxs-lookup"><span data-stu-id="f8c7a-103">Maintain group membership with Office 365 PowerShell</span></span>

<span data-ttu-id="f8c7a-104">Office 365 のグループメンバーシップを維持するために、Microsoft 365 管理センターの代わりに Office 365 PowerShell を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-104">You can use Office 365 PowerShell as an alternative to the Microsoft 365 admin center to maintain group membership in Office 365.</span></span> 

> [!TIP]
> <span data-ttu-id="f8c7a-105">ユーザーアカウントとグループ名を指定して、すぐに実行できる PowerShell コマンドを生成するには、この[グループメンテナンス Microsoft Excel ブック](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx)を使用します。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-105">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="f8c7a-106">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="f8c7a-106">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="f8c7a-107">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="f8c7a-108">ユーザーアカウントをグループのメンバーとして追加または削除する</span><span class="sxs-lookup"><span data-stu-id="f8c7a-108">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="f8c7a-109">**Upn を使用してユーザーアカウントを追加するに**は、ユーザーアカウントのユーザープリンシパル名 (UPN) とグループ表示名を入力し、"<" と ">" 文字を削除して、これらのコマンドを powershell ウィンドウまたは Powershell 統合スクリプト環境 (ISE) で実行します。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-109">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="f8c7a-110">**表示名を使用してユーザーアカウントを追加するに**は、ユーザーアカウントの表示名 (例: ベルギー Inda newman) とグループの表示名を入力し、powershell ウィンドウまたは powershell ISE でこれらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-110">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="f8c7a-111">**UPN によってユーザーアカウントを削除するに**は、ユーザーアカウントの upn (例: belindan@contoso.com) とグループの表示名を入力し、powershell ウィンドウまたは powershell ISE で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-111">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="f8c7a-112">**表示名を使用してユーザーアカウントを削除するに**は、ユーザーアカウントの表示名 (例: ベルギー Inda newman) とグループの表示名を入力し、powershell ウィンドウまたは powershell ISE でこれらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-112">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="f8c7a-113">グループのメンバーとしてグループを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="f8c7a-113">Add or remove groups as members of a group</span></span>

<span data-ttu-id="f8c7a-114">セキュリティグループには、他のグループをメンバーとして含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-114">Security groups can contain other groups as members.</span></span> <span data-ttu-id="f8c7a-115">ただし、Office 365 グループはできません。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-115">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="f8c7a-116">このセクションでは、セキュリティグループに対してのみグループを追加または削除するための PowerShell コマンドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-116">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="f8c7a-117">**表示名でグループを追加するに**は、追加するグループの表示名と、メンバーグループを含むグループの表示名を入力して、powershell ウィンドウまたは powershell ISE で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-117">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="f8c7a-118">**表示名によってグループを削除するに**は、削除するグループの表示名と、メンバーグループを含むグループの表示名を入力して、powershell ウィンドウまたは powershell ISE で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-118">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="f8c7a-119">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="f8c7a-119">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="f8c7a-120">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-120">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="f8c7a-121">ユーザーアカウントをグループのメンバーとして追加または削除する</span><span class="sxs-lookup"><span data-stu-id="f8c7a-121">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="f8c7a-122">**Upn でユーザーアカウントを追加するに**は、ユーザーアカウントのユーザープリンシパル名 (UPN) (例: belindan@contoso.com) とグループの表示名を入力して、"<" と ">" 文字を削除し、これらのコマンドを powershell ウィンドウまたは powershell ISE で実行します。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-122">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="f8c7a-123">**表示名を使用してユーザーアカウントを追加するに**は、ユーザーアカウントの表示名 (例: ベルギー Inda newman) とグループの表示名を入力し、powershell ウィンドウまたは powershell ISE でこれらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-123">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="f8c7a-124">**UPN によってユーザーアカウントを削除するに**は、ユーザーアカウントの upn (例: belindan@contoso.com) とグループの表示名を入力し、powershell ウィンドウまたは powershell ISE で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-124">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="f8c7a-125">**表示名を使用してユーザーアカウントを削除するに**は、ユーザーアカウントの表示名 (例: ベルギー Inda newman) とグループの表示名を入力し、powershell ウィンドウまたは powershell ISE でこれらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-125">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="f8c7a-126">グループのメンバーとしてグループを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="f8c7a-126">Add or remove groups as members of a group</span></span>

<span data-ttu-id="f8c7a-127">セキュリティグループには、他のグループをメンバーとして含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-127">Security groups can contain other groups as members.</span></span> <span data-ttu-id="f8c7a-128">ただし、Office 365 グループはできません。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-128">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="f8c7a-129">このセクションでは、セキュリティグループに対してのみグループを追加または削除するための PowerShell コマンドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-129">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="f8c7a-130">**表示名でグループを追加するに**は、追加するグループの表示名と、メンバーグループを含むグループの表示名を入力して、powershell ウィンドウまたは powershell ISE で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-130">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="f8c7a-131">**表示名によってグループを削除するに**は、削除するグループの表示名と、メンバーグループを含むグループの表示名を入力して、powershell ウィンドウまたは powershell ISE で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8c7a-131">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="f8c7a-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8c7a-132">See also</span></span>

[<span data-ttu-id="f8c7a-133">Office 365 PowerShell を使用してユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="f8c7a-133">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="f8c7a-134">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="f8c7a-134">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f8c7a-135">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="f8c7a-135">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

