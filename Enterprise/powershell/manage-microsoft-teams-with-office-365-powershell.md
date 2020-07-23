---
title: PowerShell を使用して Microsoft Teams を管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: '概要: PowerShell を使用して Microsoft Teams を管理します。'
ms.openlocfilehash: 8958c6ec6f0c17c21461cbee4cb1a6441ceed8d6
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230613"
---
# <a name="manage-microsoft-teams-with-powershell"></a><span data-ttu-id="e429e-103">PowerShell を使用して Microsoft Teams を管理する</span><span class="sxs-lookup"><span data-stu-id="e429e-103">Manage Microsoft Teams with PowerShell</span></span>

<span data-ttu-id="e429e-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="e429e-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="e429e-105">PowerShell を使用して Microsoft Teams を管理することができます。</span><span class="sxs-lookup"><span data-stu-id="e429e-105">You can manage Microsoft Teams with PowerShell.</span></span>
  
<span data-ttu-id="e429e-106">最初に、 [Microsoft Teams モジュール](https://www.powershellgallery.com/packages/MicrosoftTeams/)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="e429e-106">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="e429e-107">ユーザー名とパスワードを使用してサインインする</span><span class="sxs-lookup"><span data-stu-id="e429e-107">Sign in with a user name and password</span></span>

<span data-ttu-id="e429e-108">Office 365 ワールドワイド (+ GCC) クラウドの場合:</span><span class="sxs-lookup"><span data-stu-id="e429e-108">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="e429e-109">Office 365 米国政府 DoD のクラウドの場合:</span><span class="sxs-lookup"><span data-stu-id="e429e-109">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="e429e-110">Office 365 の米国政府機関 GCC 高クラウドの場合:</span><span class="sxs-lookup"><span data-stu-id="e429e-110">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="e429e-111">多要素認証 (MFA) を使用したサインイン</span><span class="sxs-lookup"><span data-stu-id="e429e-111">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="e429e-112">Office 365 ワールドワイド (+ GCC) クラウドの場合:</span><span class="sxs-lookup"><span data-stu-id="e429e-112">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="e429e-113">Office 365 米国政府 DoD のクラウドの場合:</span><span class="sxs-lookup"><span data-stu-id="e429e-113">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="e429e-114">Office 365 の米国政府機関 GCC 高クラウドの場合:</span><span class="sxs-lookup"><span data-stu-id="e429e-114">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="e429e-115">Microsoft Teams から切断する</span><span class="sxs-lookup"><span data-stu-id="e429e-115">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="e429e-116">次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e429e-116">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="e429e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e429e-117">See also</span></span>

[<span data-ttu-id="e429e-118">Teams PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="e429e-118">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="e429e-119">PowerShell を使用して Microsoft 365 を管理する</span><span class="sxs-lookup"><span data-stu-id="e429e-119">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e429e-120">Microsoft 365 の PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="e429e-120">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

