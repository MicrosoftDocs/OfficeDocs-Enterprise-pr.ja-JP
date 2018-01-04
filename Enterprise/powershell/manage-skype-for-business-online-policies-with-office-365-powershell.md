---
title: "Office 365 PowerShell を使用して Skype for Business Online を管理する"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: "概要:Office 365 PowerShell を使用して、ポリシーが割り当てられている Skype for Business Online ユーザー アカウントのプロパティを管理します。"
ms.openlocfilehash: 9b3877d2680b2b36d155cb5dd2a69fa21c972fe3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a>Office 365 PowerShell を使用して Skype for Business Online を管理する

 **概要:** Office 365 PowerShell を使用して、ポリシーが割り当てられている Skype for Business Online ユーザー アカウントのプロパティを管理します。
  
Skype for Business Online のユーザー アカウントの多数のプロパティを管理するには、Office 365 PowerShell を使用してポリシーのプロパティとして指定する必要があります。
  
## <a name="before-you-begin"></a>はじめに

次の手順にしたがってコマンドを実行するためのセットアップを行います (すでに終わっている場合はこれらの手順は省略可能です)。
  
1. [Skype for Business Online Connector モジュール](https://www.microsoft.com/en-us/download/details.aspx?id=39366)をダウンロードしてインストールします。
    
2. Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します: 
    
```
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

ダイアログ ボックスが表示されたら、Skype for Business Online 管理者のアカウント名とパスワードを入力します。
    
## <a name="manage-user-account-policies"></a>ユーザー アカウント ポリシーの管理

多くの Skype for Business Online ユーザー アカウント プロパティは、ポリシーを使用して設定します。ポリシーは、1 人以上のユーザーに適用可能な設定の集合に過ぎません。ポリシーの構成方法については、FederationAndPICDefault ポリシーに関するサンプル コマンドを実行して確認できます。
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

これにより、次のように表示されるはずです。
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

このポリシー内の値は、ユーザーがフェデレーション ユーザーとの通信に関して実際にできることとできないことを示しています。たとえば、組織外部のユーザーと通信できるようにするためには、EnableOutsideAccess プロパティを True に設定する必要があります。このプロパティは Office 365 管理センターには表示されません。代わりに、このプロパティはその他の選択内容に基づいて自動的に True または False に設定されます。関心のある他の 2 つのプロパティについては、次のようになります。
  
- **EnableFederationAccess** は、ユーザーがフェデレーション ドメインからのユーザーと通信できるかどうかを示します。
    
- **EnablePublicCloudAccess** は、ユーザーが Windows Live ユーザーと通信できるかどうかを示します。
    
つまり、ユーザー アカウント上のフェデレーション関連プロパティを直接変更したわけではなく (**Set-CsUser -EnableFederationAccess $True** など)、必要なプロパティ値が事前に構成された外部アクセス ポリシーをアカウントに割り当てただけです。ユーザーがフェデレーション ユーザーおよび Windows Live ユーザーと通信できるようにするには、ユーザー アカウントにこれらの種類の通信を可能にするポリシーを割り当てる必要があります。
  
特定のユーザーが組織外部のユーザーと通信できるかどうかを知りたい場合は、次のようにする必要があります。
  
- そのユーザーに割り当てられている外部アクセス ポリシーを特定します。
    
- そのポリシーで許可または禁止されている機能を特定します。
    
設定するには、次のコマンドを使用します。
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

このコマンドでは、ユーザーに割り当てられたポリシーを探してから、そのポリシー内で有効または無効になっている機能を探します。
  
ただし、ポリシーを作成または変更するためのコマンドレットは存在しないため、Office 365 から事前に提供されているポリシーを使用する必要があります。他に使用可能なポリシーを調べたい場合は、次のコマンドを使用できます。
  
- Get-CsClientPolicy       
- Get-CsConferencingPolicy        
- Get-CsDialPlan            
- Get-CsExternalAccessPolicy                         
- Get-CsHostedVoicemailPolicy                        
- Get-CsPresencePolicy                               
- Get-CsVoicePolicy                                  

> [!NOTE]
> Skype for Business Online ダイヤル プランは、名前以外はポリシーそのものです。「ダイヤル プラン」という名前は、Office Communications Server と Exchange との下位互換性を維持するために「ダイヤル ポリシー」の代わりに選択されたものです。 
  
たとえば、用途に使用可能なすべての音声ポリシーを調べるには、次のコマンドを実行します。
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> このコマンドは、使用可能なすべての音声ポリシーのリストを返します。ただし、すべてのポリシーをすべてのユーザーに割り当てられるとは限らない点に注意してください。これは、ライセンスや地理的な位置など、さまざまな制限によります (いわゆる「[使用場所]((https://msdn.microsoft.com/ja-JP/library/azure/dn194136.aspx))」のことです)。特定のユーザーに割り当てることが可能な外部アクセス ポリシーと会議ポリシーを知りたい場合は、次のようなコマンドを使用します。 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

ApplicableTo パラメーターは、返すデータを、指定されたユーザー (Alex Darrow など) に割り当てることが可能なポリシーに限定します。ライセンスと利用場所の制限によっては、使用可能なすべてのポリシーの一部しか表示しない場合があります。 
  
Office 365 ではポリシーのプロパティを使用しない場合もあり、また、Microsoft のサポート担当者のみが管理可能なプロパティもあります。 
  
Skype for Business Online を使用している場合は、何らかのポリシーによってユーザーを管理する必要があります。有効なポリシーに関連するプロパティが空白の場合、当該ユーザーには、ユーザーごとのポリシーが割り当てられていない場合に自動的に適用されるグローバル ポリシーによって管理されていることを意味します。ユーザー アカウントではクライアント ポリシーが表示されていないため、グローバル ポリシーによって管理されています。グローバル クライアント ポリシーを設定するには次のコマンドを使用します。
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>関連項目

#### 

[Office 365 PowerShell を使用して Skype for Business Online を管理する](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)

