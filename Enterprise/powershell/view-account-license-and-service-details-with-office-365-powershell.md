---
title: "Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- DecEntMigration
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: "Office 365 の PowerShell を使用してユーザーに割り当てられている Office 365 のサービスを確認する方法について説明します。"
ms.openlocfilehash: 59a6444e0f6618fd837e8eae567661499e795c69
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する

**の概要:**Office 365 の PowerShell を使用してユーザーに割り当てられている Office 365 のサービスを確認する方法について説明します。
  
、Office 365 では、計画のライセンスからライセンス (も呼び出された Sku または Office 365 プラン) ユーザーにそれらの計画に定義されている Office 365 サービスへのアクセスを提供します。ただし、[ユーザーはそれらに現在割り当てられているライセンスで使用可能なすべてのサービスへのアクセスをいない可能性があります。ユーザー アカウントのサービスの状態を表示するのには、Office 365 の PowerShell を使用できます。 

## <a name="before-you-begin"></a>開始する前に
<a name="RTT"> </a>

- このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
    
- コマンドを使用して、`Get-MsolAccountSku`と`(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus`、次の情報を検索します。
    
  - 組織で使用可能なライセンス プラン。
    
  - 各ライセンス プランで使用可能なサービス、およびサービスがリストされる順序 (インデックス番号)。
    
     計画、ライセンス、およびサービスのライセンスの詳細については、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)を参照してください。
    
- コマンドを使用して`Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses`(インデックス番号) を一覧には、ユーザー、および順に割り当てられているライセンスが見つかりません。
    
- _All_ パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。
    
## <a name="the-short-version-instructions-without-explanations"></a>簡略版 (説明なしの手順)
<a name="ShortVersion"> </a>

ユーザーへのアクセス権を持っている Office 365 の PowerShell のすべてのサービスを表示するには、次の構文を使用します。
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

この例では、BelindaN@litwareinc.com のユーザーのアクセスを持っているサービスを使用します。自分のアカウントに割り当てられているすべてのライセンスに関連付けられているサービスが表示されます。
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

次の例では、ユーザー BelindaN@litwareinc.com が、アカウントに割り当てられている最初のライセンス (インデックス番号 0) からアクセスできるサービスが表示されます。
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

特定のサービスが有効、または無効なすべてのライセンス ユーザーを調べるには、次の構文を使用します。
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

以下の例では、次の情報を使用します。
  
- Office 365 サービスに関心をへのアクセスを提供するライセンスは、(インデックス番号は 0 になります) すべてのユーザーに割り当てられている最初のライセンスです。
    
- 関心を Office 365 サービスは、オンライン ビジネスおよび Exchange Online の Skype です。ライセンス プランに関連付けられているライセンス、ビジネス オンラインの Skype は、6 番目の項目に記載されているサービス (インデックス番号が 5)、9 のサービスを Exchange Online には、(インデックス番号は、8) に表示されています。
    
この例が有効になっている Skype のオンライン ビジネスおよび Exchange Online ライセンスを付与されたすべてのユーザーを返します。
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

この例では、すべてのライセンスを受けたユーザーは有効になっている Skype のビジネス オンラインまたは Exchange Online を返します。
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>詳細版 (詳細な説明付きの手順)
<a name="LongVersion"> </a>

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a>Office 365 の PowerShell サービスへのアクセスを持つユーザーを見つける

ユーザーに Office 365 のライセンスが発行されているし、どのユーザーがいないを理解するが明らかに重要です。(詳細については[Office 365 の PowerShell でのライセンスおよびライセンスのないユーザーを表示する](view-licensed-and-unlicensed-users-with-office-365-powershell.md)資料を参照してください)。ただし、Office 365 のライセンスがあるだけはわかります何もそのユーザーが実際に何と Office 365 について。彼または彼女を使用して Exchange Online または Skype オンライン ビジネスのでしょうか。このユーザーが SharePoint のオンラインでアクセスできますか。彼または彼女が、Office Professional Plus へのアクセスですか。ユーザーがこれらのサービスにアクセスする可能性を持っていること、ライセンスのことです。ただし、ユーザーに利用できる機能は、彼または彼女のライセンスを有効になっているサービスに依存します。
  
どのように確認するが Office 365 の機能ユーザーへのアクセス権を持っているでしょうか。このいずれかのようなコマンドを実行する必要があることを実行します。
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

このコマンドで、BelindaN@litwareinc.com のアカウントに関する情報を取得する**Get MsolUser**コマンドレットを使用している私たち。その情報を取得して、アカウント データを**Select-object**コマンドレットにパイプし、**ライセンス**のプロパティの値を「拡張」を**選択オブジェクト**を確認します。
  
 `Select-Object -ExpandProperty Licenses`
  
理由で実行するでしょうか。既定では**ライセンス**のプロパティのみがわかりますから Belinda のライセンスが付属していたライセンス パックの名前。
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

**ライセンス**プロパティを「拡大」は、少しの詳細については。
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

**サービス ステータス**のプロパティを展開することによって取得できますより多くの情報。
  
|****サービス プラン****|****説明****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online プラン 2  <br/> |
   
> [!NOTE]
> 入力することが多すぎることがあると答えるとしますか。配置するには、ほとんどの Windows PowerShell obtuseness を実行できますこの縮小バージョンのコマンドの代わりに: >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`
  
念のため、「展開」**のライセンス**は**ライセンス**が複数値を持つプロパティであるため: 複数の値を格納できる単一のプロパティです。展開してプロパティの値を単に下にドリル ダウンするときの取得次の値を既定では、表示されていない画面に表示されます。
  
> [!NOTE]
> どのようにするになっている値は、複数値を持つプロパティであることでしょうか。アウト ボックスが、次のようなコマンドを実行している実行してください: > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> **get-member**コマンドレットは、オブジェクト自体に関する情報を返しますこの例では、プロパティに関する情報は、ユーザー アカウント オブジェクトを構成する値です。**ライセンス**のプロパティについては、**メンバーの取得**を次のとおりです: > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> プロパティ定義のコレクションのある場合 (この例では、 `System.Collections.Generic.List`) 複数値を持つプロパティを扱うことがわかって、します。 
  
このすべての意味は何ですか。それに答える、最初にもう 1 つ見てみましょう**Get MsolUser**コマンドレットによって返される情報。
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

見て奇妙という名前のサービス プランが実際に表すかを説明する表にします。
  
|****サービス プラン****|****説明****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online プラン 2  <br/> |
   
おわかりでしょうか。 `MCOSTANDARD`ビジネス オンラインでは、Skype の内部プログラミング名だけでは、中に`OFFICESUSBCRIPTION`は、Office Professional Plus の内部のプログラミング名だけ。世界では、最も直感的なものではありませんが、次の表を手元にする限り、Office 365 サービスを使用する際に多くの問題を必要はありません。
  
待て: はありません。**ProvisioningStatus**設定されている場合、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)の記事で学んだように`Success`つまり、サービスが完全に有効になっています。などの場合は`MCOSTANDARD`に設定されて`Success`、ユーザーがオンライン ビジネスの Skype にアクセスできることを意味します。**ProvisioningStatus**設定されている場合`PendingInput`Office 365 のサービス要求がまだ処理することを意味します。ただし、ユーザー通常ログオンし、要求が処理を終了するときにサービスにアクセスします。(`YAMMER_ENTERPRISE`として常に表示される`PendingInput`が、[ok]: Yammer へのログオンからユーザーを停止をしない)。
  
> [!IMPORTANT]
> ユーザーがインストールし、新しい Office Professional Plus インストール中にアクティブにすることができます`OFFICESUBSCRIPTION`では、`PendingInput`の状態です。
  
言うまでも、サービスに設定されて`Disabled`問題のサービスのユーザーが利用できるがないことを意味します。
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a>Office 365 の PowerShell の特定のサービスへのアクセス権を持つユーザーを検索します。

別の資料では、サービスへのユーザー アクセスを無効にするのには、Office 365 の PowerShell を使用する方法を見られました。(場合は、その記事を参照してください[Office 365 の PowerShell を使用してサービスへのアクセスを無効にする](disable-access-to-services-with-office-365-powershell.md))。により次のような疑問が生じます: どの*ユーザー*を決定する方法はあります (は、複数のユーザー) が有効か無効にするサービスがあるでしょうか。
  
その他のご質問があると願っていました。その質問に解答するために最初に考えた[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)の記事で当社のみ使用可能なライセンス プランのサービスのテーブルを見てみましょう`litwareinc:ENTERPRISEPACK`。
  
|****サービス プラン****|****説明****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online プラン 2  <br/> |
   
サービス計画では、プログラミングの内部名は製品よりもそれ以上、思い出して、たとえば、 `OFFICESUBSCRIPTION`、1 つの名前には、Office Professional Plus の内部のプログラミングの名前です。場合`OFFICESUBSCRIPTION`として表示される`SUCCESS`ユーザーのサービス プランでは、上、つまり Office Professional Plus にアクセスするユーザーができることです。場合`EXCHANGE_S_ENTERPRISE`と表示されている`DISABLED`ユーザーは Exchange Online を使用できないことを意味します。
  
> [!IMPORTANT]
> ユーザーがインストールし、新しい Office Professional Plus インストール中にアクティブにすることができます`OFFICESUBSCRIPTION`では、`PendingInput`の状態です。
  
今こそ、サービスの表示順序が非常に重要です。Windows PowerShell には、リスト内の各エントリにインデックス番号が割り当てられます。最初のエントリは 0 で、次のエントリは、1 というように。結果は、次の表で説明します。
  
|インデックス番号。|****サービス プラン****|
|:-----|:-----|
|0  <br/> | `SWAY` <br/> |
|1  <br/> | `INTUNE_O365` <br/> |
|2  <br/> | `YAMMER_ENTERPRISE` <br/> |
|3  <br/> | `RMS_S_ENTERPRISE` <br/> |
|4  <br/> | `OFFICESUBSCRIPTION` <br/> |
|5  <br/> | `MCOSTANDARD` <br/> |
|6  <br/> | `SHAREPOINTWAC` <br/> |
|7  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|8  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
ご覧のように、`SWAY`最初のサービスがあるので、インデックス番号 0 が割り当てられます。
  
> [!CAUTION]
> 理由 0 と 1 がありませんか。プログラミングのことです。プログラミング言語では、インデックスは、項目は「オフセット」配列の先頭からどれだけを指示します。最初の項目*が*のオフセットが 0 であるため、配列の先頭。2 番目の項目は、オフセットが 1 であるため、配列の先頭から 1 個のアイテムです。
  
例を試してみましょう。ご Exchange Online を有効になっていないすべてのライセンスを付与されたユーザーの一覧があるとします。次のコマンドを使用できます。
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

正直なところ、ある暗号のようなほとんどのコマンドのしくみを説明する 1 分を見てみましょう。これは、実際に次の 2 つのコマンドと、最初の部分は非常に単純な: 当社のすべての Office 365 ユーザーのコレクションを取得する**Get MsolUser**コマンドレットを使用しています (ライセンスおよびライセンスのない)。
  
```
Get-MsolUser
```

その情報は、 **Where-object**コマンドレットにパイプします。**場所オブジェクト**では、すべてのユーザー アカウントを経由し、次の条件の両方に一致するこれらのアカウントを探します。
  
- **IsLicensed**プロパティは ( `-eq`) `True` ( `$true`)。により、ライセンスのないユーザーを除外します。
    
- **ライセンス [0] の値です。サービス ステータス [8]。ProvisioningStatus**プロパティは ( `-eq`) `Disabled`。当社の当面の目的のこの扱いプロパティ名の重要な部分は、
    
     `ServiceStatus[8]`
    
    `[8]` Exchange オンラインのインデックス番号を表します。(それがわかったから数分前にテーブルを参照)。Skype オンライン ビジネスの有効なすべてのユーザーを検索する場合はどうでしょうか。ビジネス オンラインの Skype のインデックス番号は、5、私たちには、この構文を使用するようにします。
    
     `ServiceStatus[5]`
    
    その他も同様です。
    
    ちなみに、`Licenses[0]`ライセンス計画を確認することを示します。1 つのライセンスについては、テスト ドメインであるためこれも関係ありません。ですが、2 つの異なるライセンス計画からライセンスが割り当てられているユーザーがあるとします。その場合は、 `Licenses[0]` 、ライセンスも最初のプランを表すと`Licenses[1]`2 つ目のライセンス プランを表します。
    
    ユーザーに割り当てられているライセンス、およびライセンスがリストされる順序を調べるには、次のコマンドを実行します。
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

どのように動作が発生するかOffice Professional Plus のインデックス番号は、4 です。したがって、このコマンドは、Office Professional Plus を有効になっていないすべてのユーザーの一覧を返します。
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

たい場合は*有効な*Office Professional Plus をされているユーザーのリストですか。そうまで有効になって場合、**サービス ステータス**を行うか、`PendingInput`または`Success`。**サービス ステータス**のつまり、等しく*ない*( `-ne`) `Disabled`。行うには、前のコマンドを実行して、スワップ アウトすることを意味する、`-eq`の演算子、`-ne`演算子。
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

言っているように、そのコード可能性がありますされません勝利を収めて多くの利点を競う。真実のように設定、さらに多くのコードを取得できますタングル。たとえばが有効になって両方の Skype のオンライン ビジネス、オンラインの Exchange ユーザーを検索したいとします。
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

心配 gnarly 方法を次の方法が多すぎる: 重要なことですが、比較的少ない労力でこの情報を取得できます。Office 365 管理センターを使用するこれと同じ情報を取得できませんか。理論的には、[はい] ですが、具体的には、なし。Office 365 管理センターを使用するこれと同じ情報を取得するには、各ユーザーのライセンス情報を一度に 1 人のユーザーを確認し、手動での記録の*X*を有効になっているし、付け加えている必要があります。使用できますが、正直に: 10 または 11 を複数のユーザーであれば、しないことにこれを行う。すぎて手間と時間がかかるをお勧めします。
  
、言うまでもなく、あるため、Windows PowerShell がある: Windows PowerShell を節約するなどの手間と時間のかかるタスクからです。
  
そう思いますが、最終的なサービスの情報を表示するコマンドです。
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[0].ProvisioningStatus}}, @{Name="MDM";Expression={$_.Licenses[0].ServiceStatus[1].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[2].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[3].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[4].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[5].ProvisioningStatus}}, @{Name="OfficeWeb";Expression={$_.Licenses[0].ServiceStatus[6].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[8].ProvisioningStatus}} | ConvertTo-Html > "C:\\My Documents\\Service Info.html"
```

非常に複雑に見えるコマンドです。ですが、すべてのユーザーとすべてのサービスのステータスの表示、CSV ファイルを作成します。

  
## <a name="see-also"></a>See also
<a name="SeeAlso"> </a>

Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。
  
- [Office 365 PowerShell を使用してユーザー アカウントを作成する](create-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell でユーザー アカウントをブロックする](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。
  
- [Convertto-html コマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [形式リスト](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合


||
|:-----|
|![LinkedIn Learning の小さいアイコン](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Office 365 を初めて使用する場合は、**         LinkedIn Learning が提供する [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5) のための無料のビデオ コースをご覧ください。 |
   

