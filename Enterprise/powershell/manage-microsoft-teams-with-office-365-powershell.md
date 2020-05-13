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
# <a name="manage-microsoft-teams-with-office-365-powershell"></a>Office 365 PowerShell を使用して Microsoft Teams を管理する

Office 365 PowerShell を使用して Microsoft Teams を管理することができます。
  
最初に、 [Microsoft Teams モジュール](https://www.powershellgallery.com/packages/MicrosoftTeams/)をインストールします。
    
## <a name="sign-in-with-a-user-name-and-password"></a>ユーザー名とパスワードを使用してサインインする

Office 365 ワールドワイド (+ GCC) クラウドの場合:

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

Office 365 米国政府 DoD のクラウドの場合: 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

Office 365 の米国政府機関 GCC 高クラウドの場合:

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a>多要素認証 (MFA) を使用したサインイン

Office 365 ワールドワイド (+ GCC) クラウドの場合:

```powershell
Connect-MicrosoftTeams
```

Office 365 米国政府 DoD のクラウドの場合: 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

Office 365 の米国政府機関 GCC 高クラウドの場合:

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a>Microsoft Teams から切断する

次のコマンドを使用します。

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a>関連項目

[Teams PowerShell の概要](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)

