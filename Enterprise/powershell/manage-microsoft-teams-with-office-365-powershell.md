---
title: Office 365 PowerShell を使用して Microsoft Teams を管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/12/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: '概要: Office 365 PowerShell を使用して Microsoft Teams を管理します。'
ms.openlocfilehash: 0f15d71558ddb5166090b067da06e0a6321a2b99
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "44209123"
---
# <a name="manage-microsoft-teams-with-office-365-powershell"></a><span data-ttu-id="4d563-103">Office 365 PowerShell を使用して Microsoft Teams を管理する</span><span class="sxs-lookup"><span data-stu-id="4d563-103">Manage Microsoft Teams with Office 365 PowerShell</span></span>

<span data-ttu-id="4d563-104">Office 365 PowerShell を使用して Microsoft Teams を管理することができます。</span><span class="sxs-lookup"><span data-stu-id="4d563-104">You can manage Microsoft Teams with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="4d563-105">最初に、 [Microsoft Teams モジュール](https://www.powershellgallery.com/packages/MicrosoftTeams/)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="4d563-105">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="4d563-106">ユーザー名とパスワードを使用してサインインする</span><span class="sxs-lookup"><span data-stu-id="4d563-106">Sign in with a user name and password</span></span>

<span data-ttu-id="4d563-107">Office 365 ワールドワイド (+ GCC) クラウドの場合:</span><span class="sxs-lookup"><span data-stu-id="4d563-107">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="4d563-108">Office 365 米国政府 DoD のクラウドの場合:</span><span class="sxs-lookup"><span data-stu-id="4d563-108">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="4d563-109">Office 365 の米国政府機関 GCC 高クラウドの場合:</span><span class="sxs-lookup"><span data-stu-id="4d563-109">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="4d563-110">多要素認証 (MFA) を使用したサインイン</span><span class="sxs-lookup"><span data-stu-id="4d563-110">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="4d563-111">Office 365 ワールドワイド (+ GCC) クラウドの場合:</span><span class="sxs-lookup"><span data-stu-id="4d563-111">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="4d563-112">Office 365 米国政府 DoD のクラウドの場合:</span><span class="sxs-lookup"><span data-stu-id="4d563-112">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="4d563-113">Office 365 の米国政府機関 GCC 高クラウドの場合:</span><span class="sxs-lookup"><span data-stu-id="4d563-113">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="4d563-114">Microsoft Teams から切断する</span><span class="sxs-lookup"><span data-stu-id="4d563-114">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="4d563-115">次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4d563-115">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="4d563-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d563-116">See also</span></span>

[<span data-ttu-id="4d563-117">Teams PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="4d563-117">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="4d563-118">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="4d563-118">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="4d563-119">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="4d563-119">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

