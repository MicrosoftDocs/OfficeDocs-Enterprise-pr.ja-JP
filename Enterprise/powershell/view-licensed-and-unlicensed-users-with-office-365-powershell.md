---
title: PowerShell を使用してライセンスを付与された Microsoft 365 ユーザーを表示する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/21/2020
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: PowerShell を使用してライセンスを付与された Microsoft 365 ユーザーアカウントを表示する方法について説明します。
ms.openlocfilehash: 02b1f76bab0e64e4e7e72f5e5556f5047d956d11
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230253"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a><span data-ttu-id="182fc-103">PowerShell を使用してライセンスを付与された Microsoft 365 ユーザーを表示する</span><span class="sxs-lookup"><span data-stu-id="182fc-103">View licensed and unlicensed Microsoft 365 users with PowerShell</span></span>

<span data-ttu-id="182fc-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="182fc-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="182fc-105">Microsoft 365 組織のユーザーアカウントには、組織で使用可能なライセンスプランから割り当てられている利用可能なライセンスの一部、またはすべてがある場合があります。</span><span class="sxs-lookup"><span data-stu-id="182fc-105">User accounts in your Microsoft 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization.</span></span> <span data-ttu-id="182fc-106">Microsoft 365 の PowerShell を使用して、組織内のライセンスを取得したユーザーとライセンスのないユーザーをすばやく見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="182fc-106">You can use PowerShell for Microsoft 365 to quickly find the licensed and unlicensed users in your organization.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="182fc-107">Graph 用 Azure Active Directory PowerShell モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="182fc-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="182fc-108">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。</span><span class="sxs-lookup"><span data-stu-id="182fc-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
<span data-ttu-id="182fc-109">ライセンスプラン (ライセンスのないユーザー) が割り当てられていない組織内のすべてのユーザーアカウントの一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="182fc-109">To view the list of all user accounts in your organization that have NOT been assigned any of your licensing plans (unlicensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

<span data-ttu-id="182fc-110">ライセンスプラン (ライセンスユーザー) のいずれかが割り当てられている組織内のすべてのユーザーアカウントの一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="182fc-110">To view the list of all user accounts in your organization that have been assigned any of your licensing plans (licensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
><span data-ttu-id="182fc-111">サブスクリプション内のすべてのユーザーを一覧表示するには、コマンドを使用し `Get-AzureAdUser -All $true` ます。</span><span class="sxs-lookup"><span data-stu-id="182fc-111">To list all of the users in your subscription, use the `Get-AzureAdUser -All $true` command.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="182fc-112">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="182fc-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="182fc-113">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。</span><span class="sxs-lookup"><span data-stu-id="182fc-113">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="182fc-114">組織内のすべてのユーザーアカウントとライセンスの状態の一覧を表示するには、PowerShell で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="182fc-114">To view the list of all user accounts and their licensing status in your organization, run the following command in PowerShell:</span></span>
  
```powershell
Get-MsolUser -All
```

>[!Note]
><span data-ttu-id="182fc-115">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="182fc-115">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="182fc-116">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="182fc-116">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="182fc-117">組織内でライセンスのないすべてのユーザー アカウントの一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="182fc-117">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="182fc-118">組織内でライセンスのあるすべてのユーザー アカウントの一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="182fc-118">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="182fc-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="182fc-119">See also</span></span>

[<span data-ttu-id="182fc-120">PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="182fc-120">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="182fc-121">PowerShell を使用して Microsoft 365 を管理する</span><span class="sxs-lookup"><span data-stu-id="182fc-121">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="182fc-122">Microsoft 365 の PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="182fc-122">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
