---
title: Office 365 PowerShell を使用してユーザーごとに Skype for Business Online のポリシーを割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 概要:Office 365 PowerShell を使用して、ユーザーごとに Skype for Business Online のポリシーを適用した通信の設定を割り当てます。
ms.openlocfilehash: 615deca2790e206e6cf117283321307aa01eac74
ms.sourcegitcommit: f2aefbc2dbbe969fea9db3a4c558651496532413
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2020
ms.locfileid: "43146812"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a>Office 365 PowerShell を使用してユーザーごとに Skype for Business Online のポリシーを割り当てる

Office 365 PowerShell を使用することで、効率的にユーザーごとに Skype for Business Online のポリシーを適用した通信の設定を割り当てることができます。
  
## <a name="before-you-begin"></a>はじめに

次の手順にしたがってコマンドを実行するためのセットアップを行います (すでに終わっている場合はこれらの手順は省略可能です)。
  
1. [Skype for Business Online Connector モジュール](https://www.microsoft.com/download/details.aspx?id=39366)をダウンロードしてインストールします。
    
2. Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します: 
    
```powershell
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

ダイアログ ボックスが表示されたら、Skype for Business Online 管理者のアカウント名とパスワードを入力します。
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>ユーザー アカウントの外部通信設定を更新する

ユーザー アカウントの外部通信設定を変更するとします。たとえば、Alex がフェデレーション ユーザーと通信できるようにする (EnableFederationAccess を True に設定) と同時に、Windows Live ユーザーとは通信できないようにするとします (EnablePublicCloudAccess を False に設定)。この場合、次の 2 つの手順が必要になります。
  
1. この条件を満たす外部アクセス ポリシーを探す。
    
2. その外部アクセス ポリシーを Alex に割り当てる。
    
> [!NOTE]
>  自分だけのカスタム ポリシーを作成することはできません。これは、Skype for Business Online がカスタム ポリシーの作成を許可していないためです。代わりに、Office 365 用に特別に作成されたポリシーの 1 つを割り当てる必要があります。このように事前に作成されたポリシーは次のとおりです。4 種類のクライアント ポリシー、224 種類の会議ポリシー、5 種類のダイヤル プラン、5 種類の外部アクセス ポリシー、1 つのホスト型ボイスメール ポリシー、4 種類の音声ポリシー。
  
Alex に割り当てる外部アクセス ポリシーを特定するにはどうしたらいいでしょうか。次のコマンドは、EnableFederationAccess が True に設定され、EnablePublicCloudAccess が False に設定されたすべての外部アクセス ポリシーを返します。
  
```powershell
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

このコマンドでは、EnableFederationAccess プロパティが True に設定され、EnablePublicCloudAccess プロパティが False に設定されているという 2 つの条件を満たしているすべてのポリシーを返します。こうして、このコマンドは指定された条件を満たす 1 つのポリシー (FederationOnly) を返します。以下に例を示します。
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> ポリシー ID は Tag:FederationOnly になっています。ただし、Tag: プレフィックスは Microsoft Lync 2013 に対して実行された早期プレリリース作業から継承されたものです。ユーザーに対するポリシーの割り当てに関して言えば、Tag: プレフィックスを削除してポリシー名の FederationOnly だけを使用すべきです。 
  
これで、Alex に割り当てるポリシーが特定されたため、このポリシーを [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) コマンドレットを使用して割り当てることができます。以下に例を示します。
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

ポリシーの割り当ては簡単にでき、割り当てるユーザーの ID とポリシー名を指定するだけでポリシーを割り当てることができます。 
  
ポリシーとポリシー割り当てに関して言えば、一度に処理するユーザー アカウントの数は 1 つに制限されません。たとえば、フェデレーション パートナーおよび Windows Live ユーザーとの通信が許可されているすべてのユーザーのリストが必要だとします。このようなユーザーには外部ユーザー アクセス ポリシーの FederationAndPICDefault が割り当てられていることはすでにわかっています。それがわかっているため、1 つの単純なコマンドを実行するだけで、このようなすべてのユーザーのリストを表示することができます。以下にコマンドを示します。
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

つまり、ExternalAccessPolicy プロパティが FederationAndPICDefault に設定されているすべてのユーザーが表示されます (画面上に表示される情報量を制限するには、Select-Object コマンドレットを使用して各ユーザーの表示名だけを出力するようにします)。 
  
すべてのユーザー アカウントが同じポリシーを使用するように構成する場合は次のコマンドを使用します。
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

このコマンドでは、Get-CsOnlineUser を使用して、Lync に対して有効になっているすべてのユーザーのコレクションを返します。その後、そのすべての情報が Grant-CsExternalAccessPolicy に送信され、FederationAndPICDefault ポリシーがコレクション内のすべてのユーザーそれぞれに割り当てられます。
  
もう一つの例として、Alex にすでに FederationAndPICDefault ポリシーを割り当てていたものの、グローバルな外部アクセス ポリシーで管理することにしたとします。グローバル ポリシーは誰かに明示的に割り当てることはできません。他のユーザーごとのポリシーが割り当てられていない場合にのみ使用されます。つまり、Alex をグローバル ポリシーで管理する場合は、事前に彼に割り当てられたユーザーごとのポリシーを *解除する*  必要があります。コマンドの例を以下に示します。
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

このコマンドでは、Alex に割り当てられた外部アクセス ポリシーの名前を Null 値 ($Null) に設定します。Null は "何もない" という意味です。言い換えれば、どの外部アクセス ポリシーも Alex に割り当てられていないということになります。どの外部アクセス ポリシーもユーザーに割り当てられていなければ、そのユーザーはグローバル ポリシーによって管理されます。
  
Windows PowerShell を使用してユーザー アカウントを削除するには、Azure Active Directory コマンドレットを使用して Alex の Skype for Business Online ライセンスを削除します。詳しくは、「[Office 365 PowerShell を使ったサービスへのアクセスを無効にする](assign-licenses-to-user-accounts-with-office-365-powershell.md)」をご覧ください。

## <a name="managing-large-numbers-of-users"></a>多数のユーザーを管理する

多数のユーザー (1000 以上) を管理するには、[コマンド](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7)レットを使用してスクリプトブロックでコマンドをバッチ処理する必要があります。  前の例では、コマンドレットが実行されるたびに、呼び出しを設定し、その結果が返されるまで待機してから、再度送信する必要があります。  スクリプトブロックを使用すると、コマンドレットをリモートで実行し、完了したらデータを返送できます。 

```powershell
Import-Module LyncOnlineConnector
$sfbSession = New-CsOnlineSession
$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

これにより、クライアントポリシーを持たない時間に500ユーザーが検索されます。 これにより、クライアントポリシー "ClientPolicyNoIMURL" と "FederationAndPicDefault" という外部アクセスポリシーが付与されます。 結果は50のグループにバッチ処理され、50の各バッチがリモートコンピューターに送信されます。
  
## <a name="see-also"></a>関連項目

[Office 365 PowerShell を使用して Skype for Business Online を管理する](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)
