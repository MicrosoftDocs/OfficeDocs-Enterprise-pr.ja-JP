---
title: PowerShell を使用して Skype for Business Online のポリシーを管理する
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
description: '概要: PowerShell を使用して、ポリシーを使用して Skype for Business Online のユーザーアカウントのプロパティを管理します。'
ms.openlocfilehash: 4310de23d47025468ea78a597f6379b51deaaa96
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230433"
---
# <a name="manage-skype-for-business-online-policies-with-powershell"></a>PowerShell を使用して Skype for Business Online のポリシーを管理する

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

Skype for Business Online のユーザーアカウントの多数のプロパティを管理するには、Microsoft 365 の PowerShell を使用してポリシーのプロパティとして指定する必要があります。
  
## <a name="before-you-begin"></a>はじめに

次の手順にしたがってコマンドを実行するためのセットアップを行います (すでに終わっている場合はこれらの手順は省略可能です)。
  
1. [Skype for Business Online Connector モジュール](https://www.microsoft.com/download/details.aspx?id=39366)をダウンロードしてインストールします。
    
2. Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します: 
    
```powershell
Import-Module SkypeOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

ダイアログ ボックスが表示されたら、Skype for Business Online 管理者のアカウント名とパスワードを入力します。
    
## <a name="manage-user-account-policies"></a>ユーザー アカウント ポリシーの管理

多くの Skype for Business Online ユーザー アカウント プロパティは、ポリシーを使用して設定します。ポリシーは、1 人以上のユーザーに適用可能な設定の集合に過ぎません。ポリシーの構成方法については、FederationAndPICDefault ポリシーに関するサンプル コマンドを実行して確認できます。
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

これにより、次のように表示されるはずです。
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

この例では、このポリシー内の値によって、フェデレーションユーザーとの通信に使用できる、またはできない処理を決定します。たとえば、ユーザーが組織外のユーザーと通信できるようにするには、EnableOutsideAccess プロパティを True に設定する必要があります。このプロパティは、Microsoft 365 管理センターには表示されないことに注意してください。代わりに、その他の選択に基づいて、プロパティは自動的に True または False に設定されます。その他の重要なプロパティは次の2つです。
  
- **EnableFederationAccess** は、ユーザーがフェデレーション ドメインからのユーザーと通信できるかどうかを示します。
    
- **EnablePublicCloudAccess** は、ユーザーが Windows Live ユーザーと通信できるかどうかを示します。
    
つまり、ユーザー アカウント上のフェデレーション関連プロパティを直接変更したわけではなく (**Set-CsUser -EnableFederationAccess $True** など)、必要なプロパティ値が事前に構成された外部アクセス ポリシーをアカウントに割り当てただけです。ユーザーがフェデレーション ユーザーおよび Windows Live ユーザーと通信できるようにするには、ユーザー アカウントにこれらの種類の通信を可能にするポリシーを割り当てる必要があります。
  
特定のユーザーが組織外部のユーザーと通信できるかどうかを知りたい場合は、次のようにする必要があります。
  
- そのユーザーに割り当てられている外部アクセス ポリシーを特定します。
    
- そのポリシーで許可または禁止されている機能を特定します。
    
設定するには、次のコマンドを使用します。
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

このコマンドでは、ユーザーに割り当てられたポリシーを探してから、そのポリシー内で有効または無効になっている機能を探します。
  
PowerShell を使用して Skype for Business Online のポリシーを管理するには、次のコマンドレットを参照してください。

- [クライアント ポリシー](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [会議ポリシー](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [モバイルポリシー](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [オンラインボイスメールポリシー](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [音声ルーティングポリシー](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> Skype for Business Online ダイヤル プランは、名前以外はポリシーそのものです。「ダイヤル プラン」という名前は、Office Communications Server と Exchange との下位互換性を維持するために「ダイヤル ポリシー」の代わりに選択されたものです。 
  
たとえば、用途に使用可能なすべての音声ポリシーを調べるには、次のコマンドを実行します。
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> このコマンドは、使用可能なすべての音声ポリシーのリストを返します。ただし、すべてのポリシーをすべてのユーザーに割り当てられるとは限らない点に注意してください。これは、ライセンスや地理的な位置など、さまざまな制限によります (いわゆる「[使用場所](https://msdn.microsoft.com/library/azure/dn194136.aspx)」のことです)。特定のユーザーに割り当てることが可能な外部アクセス ポリシーと会議ポリシーを知りたい場合は、次のようなコマンドを使用します。 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

ApplicableTo パラメーターは、返すデータを、指定されたユーザー (Alex Darrow など) に割り当てることが可能なポリシーに限定します。ライセンスと利用場所の制限によっては、使用可能なすべてのポリシーの一部しか表示しない場合があります。 
  
場合によっては、ポリシーのプロパティは Microsoft 365 では使用されず、Microsoft サポート担当者のみが管理できるものがあります。 
  
Skype for Business Online を使用している場合は、何らかのポリシーによってユーザーを管理する必要があります。有効なポリシーに関連するプロパティが空白の場合、当該ユーザーには、ユーザーごとのポリシーが割り当てられていない場合に自動的に適用されるグローバル ポリシーによって管理されていることを意味します。ユーザー アカウントではクライアント ポリシーが表示されていないため、グローバル ポリシーによって管理されています。グローバル クライアント ポリシーを設定するには次のコマンドを使用します。
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>関連項目

[PowerShell を使用して Skype for Business Online を管理する](manage-skype-for-business-online-with-office-365-powershell.md)
  
[PowerShell を使用して Microsoft 365 を管理する](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 の PowerShell の概要](getting-started-with-office-365-powershell.md)

