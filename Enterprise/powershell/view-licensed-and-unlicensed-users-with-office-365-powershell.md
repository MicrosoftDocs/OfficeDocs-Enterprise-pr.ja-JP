---
title: ライセンスのあるユーザーとライセンスのないユーザーを Office 365 PowerShell で表示する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/18/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Office 365 PowerShell を使って、ライセンスのあるユーザー アカウントとライセンスのないユーザー アカウントを表示する方法について説明します。
ms.openlocfilehash: 832e073ad5443181f1c72af591cc99e3702d6b84
ms.sourcegitcommit: de4240ae8026e3e9a433c7ae23c938dc5b514ace
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2019
ms.locfileid: "40738269"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="cf127-103">ライセンスのあるユーザーとライセンスのないユーザーを Office 365 PowerShell で表示する</span><span class="sxs-lookup"><span data-stu-id="cf127-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="cf127-p101">Office 365 組織のユーザー アカウントには、組織で使用可能なライセンス プランからユーザー アカウントに割り当てることのできるライセンスが一部またはすべて存在する場合や、まったく存在しない場合があります。Office 365 PowerShell を使うと、組織内でライセンスのあるユーザーとライセンスのないユーザーをすばやく検索できます。</span><span class="sxs-lookup"><span data-stu-id="cf127-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="cf127-106">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="cf127-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="cf127-107">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="cf127-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
<span data-ttu-id="cf127-108">ライセンスプラン (ライセンスのないユーザー) が割り当てられていない組織内のすべてのユーザーアカウントの一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="cf127-108">To view the list of all user accounts in your organization that have NOT been assigned any of your licensing plans (unlicensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

<span data-ttu-id="cf127-109">ライセンスプラン (ライセンスユーザー) のいずれかが割り当てられている組織内のすべてのユーザーアカウントの一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="cf127-109">To view the list of all user accounts in your organization that have been assigned any of your licensing plans (licensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
><span data-ttu-id="cf127-110">サブスクリプション内のすべてのユーザーを一覧表示するには`Get-AzureAdUser -All $true` 、コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="cf127-110">To list all of the users in your subscription, use the `Get-AzureAdUser -All $true` command.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="cf127-111">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="cf127-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="cf127-112">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="cf127-112">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="cf127-113">組織内のすべてのユーザー アカウントとライセンスの状態を一覧表示するには、Office 365 PowerShell で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="cf127-113">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```powershell
Get-MsolUser -All
```

>[!Note]
><span data-ttu-id="cf127-114">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="cf127-114">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="cf127-115">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf127-115">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="cf127-116">組織内でライセンスのないすべてのユーザー アカウントの一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="cf127-116">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="cf127-117">組織内でライセンスのあるすべてのユーザー アカウントの一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="cf127-117">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="cf127-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf127-118">See also</span></span>

[<span data-ttu-id="cf127-119">Office 365 PowerShell を使用してユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="cf127-119">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="cf127-120">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="cf127-120">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="cf127-121">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="cf127-121">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
