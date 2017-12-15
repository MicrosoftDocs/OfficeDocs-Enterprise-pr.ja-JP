---
title: "単一の Windows PowerShell ウィンドウですべての Office 365 サービスに接続する"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- DecEntMigration
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: "概要: は、Windows PowerShell を 1 つの Windows PowerShell のウィンドウ内のすべての Office 365 サービスに接続します。"
ms.openlocfilehash: 28016342fff77e33bd18369ae08b773ecea32644
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>単一の Windows PowerShell ウィンドウですべての Office 365 サービスに接続する

 **の概要:**別の PowerShell コンソール ウィンドウで別の Office 365 サービスを管理するには、代わりにすべての Office 365 サービスに接続し、それらを 1 つのコンソール ウィンドウから管理できます。
  
PowerShell を使用して、Office 365 を管理するために、することは最大 5 つの異なる Windows PowerShell セッションとに対応する Office 365 管理センター、SharePoint のオンライン、Exchange オンライン、ビジネス オンラインでは、Skype セキュリティ&amp;コンプライアンス センターです。別の Windows PowerShell セッションで 5 つの別の接続方法、デスクトップ次のようになります。
  
![一度に実行している 5 つの Windows PowerShell コンソール](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
これは Office 365 の管理に最適な状況ではありません。サービス間管理のために 5 つのウィンドウ間でデータを交換できないからです。このトピックでは、Office 365、Skype for Business Online、Exchange Online、SharePoint Online、および セキュリティ センターとコンプライアンス センター を管理する Windows PowerShell のインスタンスを使用する方法について説明します。
  
## <a name="before-you-begin"></a>開始する前に
<a name="BeforeYouBegin"> </a>

Windows PowerShell の単一のインスタンスからすべての Office 365 を管理する前に、次の前提条件を考慮してください。
  
- これらの手順に使用する Office 365職場または学校のアカウント は、Office 365 管理者役割のメンバーである必要があります。詳細については、「[Office 365 の管理者の役割](https://go.microsoft.com/fwlink/p/?LinkId=532367)」を参照してください。これは Office 365 PowerShell の要件であり、他のすべての Office 365 サービスについては必ずしも当てはまりません。
    
- 次の Windows の 64 ビット バージョンを使用できます。
    
  - Windows 10
    
  - Windows 8.1 または Windows 8
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 または Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * Microsoft.NET Framework 4.5 をインストールする必要があります。_x_とし、いずれかの Windows Management Framework 3.0 または Windows Management Framework 4.0 です。詳細については、 [ [.NET Framework をインストールして](https://go.microsoft.com/fwlink/p/?LinkId=257868)Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)または[4.0 の Windows Management Framework](https://go.microsoft.com/fwlink/p/?LinkId=391344)を参照してください。
    
    Skype for Business Online モジュール、および Office 365 モジュールの 1 つの要件のため、64 ビット バージョンの Windows を使用する必要があります。
    
- Office 365、SharePoint Online、および Skype for Business Online に必要な以下のモジュールをインストールする必要があります。
    
  - [IT プロフェッショナル用 Microsoft Online Services サインイン アシスタント RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)
    
  - [Windows PowerShell 用 Windows Azure Active Directory モジュール (64 ビット バージョン)](https://go.microsoft.com/fwlink/p/?linkid=236297)
    
  - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
    
  - [Skype for Business Online、Windows PowerShell モジュール](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell は、Skype のオンライン ビジネス、オンラインの Exchange セキュリティの署名済みスクリプトを実行するように構成する必要があります&amp;コンプライアンス センターです。これを行うには、管理者特権の Windows PowerShell セッションで次のコマンドを実行 (**管理者として実行**を選択して開く Windows PowerShell のウィンドウ) です。
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="the-short-version-instructions-without-explanations"></a>簡略版 (説明なしの手順)
<a name="ShortVersion"> </a>

このセクションでは、接続の手順を簡単に説明しています。疑問点がある場合や詳細情報が必要な場合には、このトピックの残りの部分を参照してください。ここでの手順の番号は、このトピックの残りの部分で手順番号が付けられたセクションに対応しています。
  
1. 管理者として Windows PowerShell を開きます ( **[管理者として実行]** を使用)。
    
2. 次のコマンドを実行し、Office 365職場または学校のアカウント の資格情報を入力します。
    
  ```
  $credential = Get-Credential
  ```

3. 次のコマンドを実行して、Office 365 に接続します。
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. SharePoint Online に接続するためのこれらのコマンドを実行します。交換_\<domainhost >_ドメインの実際の値とします。たとえば、 `litwareinc.onmicrosoft.com`、 _ \<domainhost >_の値は、 `litwareinc`。
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. オンライン ビジネス用の Skype への接続にこれらのコマンドを実行します。増加についての警告、`WSMan NetworkDelayms`最初に、期待される値に接続し、無視する必要があります。
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. 次のコマンドを実行して、Exchange Online に接続します。
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. 次のコマンドを実行して、セキュリティ センターとコンプライアンス センター に接続します。
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> テキスト プレフィックス"cc"は、*すべて*のセキュリティに追加されます&amp;コンプライアンス センターのコマンドレット名をコマンドレットを実行できるようには、Exchange Online とセキュリティの両方に存在&amp;同じ Windows PowerShell セッションでのコンプライアンスの中心です。たとえば、 **Get RoleGroup**になり、セキュリティでは、 **Get ccRoleGroup** &amp;コンプライアンス センターです。
  
次に 1 つのブロック内のすべてのコマンドを示します。ドメイン ホストの名前を指定してから、それらすべてを同時に実行します。
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Import-Module MsOnline
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
Import-PSSession $ccSession -Prefix cc
```

オンライン ビジネス、オンラインの Exchange、SharePoint Online では、およびセキュリティの Skype へのアクティブなセッションを削除するのにはこのコマンドを実行している Windows PowerShell のウィンドウを終了する準備ができたら、&amp;コンプライアンス センター。
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>詳細版 (詳細な説明付きの手順)
<a name="LongVersion"> </a>

### <a name="step-1-open-windows-powershell-as-an-administrator"></a>手順 1: 管理者として Windows PowerShell を開く
<a name="Step1"> </a>

Windows 10、Windows 8、Windows 8.1、Windows Server 2016、Windows Server 2012 R2、または Windows Server 2012 R2 を実行している場合は、次のようにします。
  
1. 以下のいずれかの方法を使用して、 **Windows PowerShell** のショートカットを見つけます。
    
  - スタート画面で、空の領域をクリックして、Windows PowerShell と入力します。
    
  - デスクトップまたはスタート画面で、Windows キー + Q キーを押します。[検索] チャームに Windows PowerShell と入力します。
    
  - デスクトップまたはスタート画面で、右上隅にカーソルを移動するか、画面の右端から左にスワイプして、チャームを表示します。[検索] チャームを選択して、「Windows PowerShell」と入力します。
    
2. 結果の中の **Windows PowerShell** を右クリックし、 **[管理者として実行]** をクリックします。
    
3. **[ユーザー アカウント制御]** ダイアログ ボックスが表示されたら、 **[はい]** を選択して、管理者の資格情報を使用して Windows PowerShell を実行することを確認します。
    
Windows 7 SP1 (または Windows Server 2008 R2 SP1) を実行している場合は、次の操作を行います。
  
1. **[スタート]** メニューで、 **[すべてのプログラム]** > **アクセサリ** > **Windows PowerShell** の順に選択します。 **Windows PowerShell** を右クリックし、 **[管理者として実行]** を選択します。
    
2. **[ユーザー アカウント制御]** ダイアログ ボックスが表示されたら、 **[はい]** を選択して、管理者の資格情報を使用して Windows PowerShell を実行することを確認します。
    
Windows PowerShell は管理者として実行する必要があります。管理者として実行しないと、必要なモジュールのいずれかをインポートした時に、以下のようなエラー メッセージが表示されます。
  
```
The specified module 'Microsoft.Online.SharePoint.Online.PowerShell' was not loaded because no valid module file was found in any directory.
```

この問題を解決する唯一の方法は、Windows PowerShell を閉じて再起動する (管理者として) ことです。ここでは、管理者として Windows PowerShell を実行しているかどうか手早く簡単に確認する方法を示します。プロンプトは  `PS C:\Windows\System32>` です ( `PS C:\Users\YourUserName>` ではありません)。

  
### <a name="step-2-create-a-windows-powershell-credentials-object"></a>手順 2: Windows PowerShell 資格情報オブジェクトを作成する
<a name="Step2"> </a>

資格情報オブジェクトは Windows PowerShell にユーザー名とパスワードを渡す暗号化された手段を提供します。資格情報オブジェクトを作成するには、Windows PowerShell で次のコマンドを実行します。
  
```
$credential = Get-Credential
```

> [!NOTE]
>  `$credential` は、資格情報オブジェクトを格納する変数です。この変数に `$credential` という名前を付ける必要はありませんが、こうすることによって、どの変数に資格情報オブジェクトが格納されているかを覚えやすくなります (この変数は何度も繰り返し使用することになるため、このことは重要です)。この資料では資格情報オブジェクトを表現するときに、必ず `$credential` を使用するため、例がわかりやすくなるという効果もあります。
  
Windows PowerShell に次のようなダイアログ ボックスが表示されます。
  
![空の [資格情報の要求] ダイアログ ボックス。](images/o365_powershell_empty_credentials_box.png)
  
**[ユーザー名]** ボックスに 職場または学校のアカウント ユーザー名を _username@domainname_ という形式 (kenmyer@litwareinc.onmicrosoft.com など) で入力し、 **[パスワード]** ボックスにパスワードを入力してから、 **[OK]** をクリックします。
  
![完成した [資格情報の要求] ダイアログ ボックス。](images/o365_powershell_completed_credentials_box.png)
  
大抵の場合、資格情報オブジェクトが作成されても確認が表示されないことに注意してください (Windows PowerShell は、問題が起きると通知しますが、正常に実行されると必ずしも通知しません)。資格情報オブジェクトが作成されたことを確認するには、Windows PowerShell で次のコマンドを入力して、Enter キーを押します。
  
```
$credential
```

次のような画面が表示されるはずです。
  
```
UserName                               Password
--------                               --------
kenmyer@litwareinc.onmicrosoft.com     System.Security.SecureString
```

ここで注意することは、[資格情報の Get](https://go.microsoft.com/fwlink/p/?LinkId=389618)コマンドレットでは、資格情報オブジェクトのみを作成ユーザーを認証したりそれ以外の場合、ユーザー名とパスワードが正しいことを確認しません。たとえば、kenmyer@litwareinc.onmicrosoft.com としてユーザー名の入力に誤りがあるとします。**資格情報の取得**がそのユーザー名を使用して、資格情報オブジェクトを作成、操作を行う場合とするが実際に有効なユーザー名であるかどうかをチェックすることがなく。Office 365 サービスに接続しようとするには実際にそのオブジェクトを使用するまで、本当に有効な資格情報オブジェクトを作成したかどうかがわかりません。
  
### <a name="step-3-connect-to-office-365"></a>手順 3:Office 365 に接続する
<a name="Step3"> </a>

Office 365 に接続することから始めます。 
  
ここで最初に行うべきことは、Office 365 モジュール (Microsoft PowerShell の Microsoft Azure Active Directory モジュール) のインポートです。そのために、Windows PowerShell で次のコマンドを実行します。
  
```
Import-Module MsOnline
```

モジュールがインポートされたことを確認する場合は、次のコマンドを実行します。
  
```
Get-Module
```

このコマンドによって返されるモジュールの一覧に次のように表示されている箇所があるはずです:  `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`。
  
`MSOnline` が表示されていれば、すべてが予定どおり進んだことを意味します。
  
作成した資格情報オブジェクトに (を参照してください[手順 2: Windows PowerShell の資格情報オブジェクトを作成する](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) と、`MsOnline`モジュールをロードすると、今すぐ接続できる Office 365 に[接続 MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)コマンドレットと次のコマンドを使用しています。
  
```
Connect-MsolService -Credential $credential
```

資格情報オブジェクト ( `$credential`) だけを入力すればいいことに注目してください。この資格情報に基づいて、Office 365 が自動的に正しいドメインに接続します。 **Connect-MsolService** を実行するときに、ドメイン名を指定する必要はありません。
  
*実際に*  Office 365Office 365 に接続されていることを確認するには、次のコマンドを実行します。
  
```
Get-MsolDomain
```

これにより、次のように表示されるはずです。
  
```
Name                         Status          Authentication
----                         ------          --------------
litwareinc.onmicrosoft.com   Verified        Managed
```

### <a name="step-4-connect-to-sharepoint-online"></a>手順 4:SharePoint Online に接続する
<a name="Step4"> </a>

次のコマンドを使用して、SharePoint Online モジュールをインポートします。
  
```
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
```

_DisableNameChecking_ スイッチは、次の警告を表示しないようにします。
  
```
WARNING: The names of some imported commands from the module 'Microsoft.Online.SharePoint.PowerShell' include unapproved verbs that might make them less discoverable. To find the commands with unapproved verbs, run the Import-Module command again with the Verbose parameter. For a list of approved verbs, type Get-Verb.
```

SharePoint Online に接続する 2 つの情報を提供する必要があります: ユーザーの資格情報と、SharePoint Online の管理サイトの URL です。資格情報の一部は簡単: 既に格納されている変数に`$credential`(を参照してください[手順 2: Windows PowerShell の資格情報オブジェクトを作成する](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2))。管理サイトの URL とは調べるには、同様に簡単に行えます。Office 365 にドメイン名があると`litwareinc.onmicrosoft.com`。
  
管理サイトの URL を特定するには、次の手順を実行します。
  
1. プレフィックスの  `https://` で始めます。
    
2. ドメイン名のドメイン ホスト部分を追加します。たとえば、 `litwareinc.onmicrosoft.com` の場合、ドメイン ホスト名は `litwareinc` です。 `contoso.onmicrosoft.com` では、ドメイン ホスト名は `contoso` です。
    
3. ハイフン (-) に続けて  `admin.sharepoint.com` を入力します。
    
次のようになります。
  
 `https://` + `litwareinc` + `-admin.sharepoint.com` = `https://litwareinc-admin.sharepoint.com`
  
URL を組み立てたら、その URL と資格情報オブジェクトを使用して SharePoint Online に接続できます。次のようなコマンドを使用して、[Connect-SPOService](https://go.microsoft.com/fwlink/p/?LinkId=532436) コマンドレットを呼び出すだけです。
  
```
Connect-SPOService -Url https://litwareinc-admin.sharepoint.com -credential $credential
```

接続が確立されたことを確認するには、Windows PowerShell で次のコマンドを実行します。
  
```
Get-SPOSite
```

すべての SharePoint Online サイトの一覧を取得する必要があります。例を以下に示します。
  
```
Url                                       Owner          Storage Quota
---                                       -----          -------------
http://litwareinc-public.sharepoint.com/                 1000
https://litwareinc.sharepoint.com/                       1000
https://litwareinc.sharepoint.com/search                 1000
```

Office 365 コマンド (「[手順 3:Office 365 に接続する](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)」で説明) がここでも機能します ( **Get-MsolUser** を実行して確認してください)。これで、Windows PowerShell の 1 つのインスタンスから Office 365 と SharePoint Online の両方を管理できるようになります。
  
### <a name="step-5-connect-to-skype-for-business-online"></a>手順 5:Skype for Business Online に接続する
<a name="Step5"> </a>

Skype for Business Online (および Exchange Online または セキュリティ センターとコンプライアンス センター) への接続は、Office 365 や SharePoint Online への接続とは異なります。Skype for Business Online コマンドレットと Exchange Online コマンドレットは、Office 365 コマンドレットや SharePoint Online コマンドレットと違い、コンピューターにインストールされていないためです。代わりに、ユーザーが該当するコマンドレットにサインインするたびに一時的にコンピューターにコピーされます。ユーザーがサインオフすると、これらのコマンドレットがコンピューターから削除されます。
  
Skype for Business Online に接続するには、Skype for Business Online モジュールをインポートする必要があります。そのために、次のコマンドを実行します。
  
```
Import-Module SkypeOnlineConnector
```

初めてこれを実行する場合、次の警告メッセージが表示される場合がありますが、無視しても問題ありません。
  
```
WARNING: WSMan NetworkDelayms has been set to 30000 milliseconds. The previous value was 5000 milliseconds.
WARNING: To improve the performance of the Lync Online Connector, it is recommended that the network delay be set to
30000 milliseconds (30 seconds). However, you can use Set-WinRMNetworkDelayMS to change the network delay to any
integer value.
```

モジュールがインポートされたら、次のコマンドを実行します。
  
```
$sfboSession = New-CsOnlineSession -Credential $credential
```

リモート PowerShell セッションは既に作成済みです。この場合は、Office 365 サーバーのいずれかで動作している Windows PowerShell のインスタンスに接続されたことを意味します。 
  
Office 365 への接続は確立済みですが、Skype for Business Online を管理するために必要なスクリプト、コマンドレット、およびその他の項目は、まだダウンロードしていません。それらを行うために、このコマンドを実行する必要があります。
  
```
Import-PSSession $sfboSession
```

Windows PowerShell セッションをインポートするときに、次のような進行状況バーが表示されるはずです。進行状況バーには、コンピューターにインポート中のすべての Skype for Business Online コマンドレットの状況が表示されます。
  
![Lync Online 進行状況バー。](images/o365_powershell_lync_progress_bar.png)
  
進行状況バーが消えると、次のような出力が表示されるはずです。
  
```
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     1.0        tmp_swc5mp4v.1ck  {Copy-CsVoicePolicy, Disabl...
```

### <a name="step-6-connect-to-exchange-online"></a>ステップ 6: Exchange Online に接続する
<a name="Step6"> </a>

Exchange Online とのリモート Windows PowerShell セッションを作成する、次のコマンドを実行します。
  
```
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
```

> [!NOTE]
> Exchange オンライン ビジネス オンラインの Skype に接続するためのコマンドよりも複雑に接続するためのコマンドがなぜですか。技術的には、: 両方のコマンドは、まったく同じことを行います。ただし、ビジネス オンライン チームの Skype は、独自のコマンドレットを作成-**新規 CsOnlineSession** -(「_認証_」、「 _AllowRedirection_」など)、Exchange Online に接続するときに使用されるパラメーターの一部を非表示にします。自分でその情報を入力する必要はありません、_認証_および_AllowRedirection_パラメーターは効果的に組み込まれている**新規 CsOnlineSession**コマンドレットです。Exchange オンライン Office 365 に接続する標準的な[新規 PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)コマンドレットを使用するために、Exchange Online に接続するときにこれらのパラメーターを入力する必要が。欠点を実行するのには、もう少し入力があること。利点をダウンロードし、Exchange のオンライン ・ モジュールをインストールすることもできます。
  
ここでやるべきことは、Skype for Business Online でやったように、このリモート セッションをインポートすることだけです。
  
```
Import-PSSession $exchangeSession -DisableNameChecking
```

次のような画面が表示されます。
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_nweiqjvl.geu {Add-AvailabilityAddressSpace...
```

ここで、次のコマンドを実行してみてください。
  
```
Get-AcceptedDomain
```

これにより、Exchange Online の電子メール アドレス用に構成された Office 365 ドメインに関する情報が表示されるはずです。
  
```
Name            DomainName          DomainType      Default
----            ----------          ----------      -------
litwareinc.com  litwareinc.com      Authoritative   True
```

### <a name="step-7-connect-to-the-security-amp-compliance-center"></a>手順 7: セキュリティ センターとコンプライアンス センターに接続する
<a name="Step7"> </a>

セキュリティ&amp;コンプライアンス センターはコンプライアンス機能を 1 か所から管理することができる Office 365 のサービスです。詳細については、 [Office 365 のコンプライアンス センター](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx)を参照してください。
  
セキュリティ センターとコンプライアンス センター の接続手順は、Exchange Online の手順とよく似ていますが、ちょっとした違いがあります。これはすぐに説明します。
  
セキュリティ センターとコンプライアンス センター とのリモート PowerShell セッションを作成する次のコマンドを実行します。
  
```
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
```

次に、次のコマンドを実行します。
  
```
Import-PSSession $ccSession -Prefix cc
```

もう一度このコマンドは、Exchange Online のコマンドによく似ています。セキュリティで許可されていない動詞が存在しないため、 _DisableNameChecking_スイッチは必要ありません&amp;コンプライアンス センターです。についてはさらに`-Prefix cc`パラメーターと値ですか。について言いましたねじれの追加です。
  
Exchange Online とセキュリティ&amp;コンプライアンス センターが正確に同じ名前し、同じ機能を提供するいくつかのコマンドレットを共有します。**Get RoleGroup**は、例です。
  
同じ名前のコマンドレットが含まれている 2 つのセッションをインポートしようとする場合の動作ですか。競合が発生します。という、大きな黄色い警告メッセージが表示されます`WARNING: Proxy creation has been skipped for the following command:`後にインポートすることができませんでしたが競合しているコマンドレットのリストです。最終的な結果ですか。接続してある 1 つは、セキュリティで**Get RoleGroup**を実行することはできませんので、Exchange Online で**Get RoleGroup**を実行することができます&amp;コンプライアンス ・ センターのため、接続してある最後と競合するコマンドレットがインポートするのには拒否されました。
  
インポートされたセキュリティを保護する、任意のテキストのプレフィックスを追加するのにはこの問題に対処する最も簡単な方法は、&amp;コンプライアンス センター コマンドレットです。**インポート PSSession**コマンドレットでは、"cc"の値を持つ_プレフィックス_パラメーターを使用することでした。何が行われるのでしょうか。(少しだけ) のセキュリティを変更して、競合を排除して&amp;、このセッションのコマンドレット名のコンプライアンス センターです。すべてのインポートされたセキュリティ&amp;コンプライアンス センター コマンドレットを開始"cc"とコマンドレット名の名詞部分 (の右側に、"-")。たとえば、 **Get RoleGroup**コマンドレットを使わないようになります**Get ccRoleGroup**セキュリティ&amp;コンプライアンス センターの Exchange Online の**Get RoleGroup**と競合しないようにします。
  
欠点でしょうか。 *すべて* セキュリティ&amp;コンプライアンス センター コマンドレット名には"cc"のプレフィックスが表示される、独自のコマンドレットを必要としないのも。たとえば、 **Get ComplianceSearch**がなくてもないこのようなコマンドレット Exchange オンライン**取得 ccComplianceSearch**になります。悩みの種のですが、悪くない 1 つの Windows PowerShell セッションでのすべての Office 365 サービスの管理の利点を検討するとき。セキュリティのすべての手順については、コマンドレット名に"cc"を追加するのには注意してください&amp;コンプライアンス センターです。
  
すべてが順調に進めば、次のような画面が表示されます。
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_xbbx5exr.ehm {Add-ccRoleGroupMember, Get-ccAdminAuditLogConfig, Get-ccA...
```

これで、すべての Office 365 サービスを単一の Windows PowerShell セッションで自由に管理できるようになりました。
  
### <a name="step-8-gracefully-end-your-powershell-sessions"></a>手順 8: PowerShell セッションを終了する
<a name="Step8"> </a>

Windows PowerShell ウィンドウを閉じても、その後 15 分ぐらいは Skype for Business Online リモート接続がアクティブなままになります。1 人のユーザーまたは 1 つのドメインで開いていることができる同時接続数が Skype for Business Online によって制限されているため、これは問題を引き起こす可能性があります。Skype for Business Online の場合、1 人の管理者が開いていることができる接続は一度に最大 3 つで、1 つのドメインでは最大 9 つです。Skype for Business Online にサインインしてセッションを適切に閉じずに終了した場合、そのセッションがその後約 15 分間開いたままになります。その結果、自分で利用できる接続も、ドメイン内で他の管理者が利用できる接続も 1 つ少なくなります。
  
代わりに、Skype for Business Online、Exchange Online、および セキュリティ センターとコンプライアンス センター 用に開かれたリモート セッションを閉じます。その前に、次のコマンドを実行します。
  
```
Get-PSSession
```

[Get PSSession](https://go.microsoft.com/fwlink/p/?LinkId=532437)コマンドレットかがわかるとがあることには、少なくとも 3 つのリモート セッションを開く、ビジネス オンラインの Skype のいずれか、Exchange のオンラインのいずれかのセキュリティのいずれかの&amp;(ことの可能な場合がありますよりも 3 つのリモート ・ コンプライアンス センターセッションが実行されて、Office 365 のサービスだけでなく他の何かに接続する Windows PowerShell のこのインスタンスを使用したかどうかによって異なります)。次のような画面が表示されます。
  
```
Id Name     ComputerName     State   ConfigurationName    Availability
-- ----     ------------     -----   -----------------    ------------
 1 Session1 webdir0a.onl...  Opened  Microsoft.PowerShell    Available
 2 Session2 outlook.offi...  Opened  Microsoft.Exchange      Available
 3 Session3 ps.complianc...  Opened  Microsoft.Exchange      Available
```

これら 3 つのセッションを閉じるには、次のコマンドを一度に 1 つずつ実行します。最初のコマンドは Skype for Business Online セッション、2 番目は Exchange Online セッション、3 番目は セキュリティ センターとコンプライアンス センター セッションをそれぞれ閉じます。
  
```
Remove-PSSession $sfboSession
Remove-PSSession $exchangeSession
Remove-PSSession $ccSession
```

ここで **Get-PSSession** コマンドレットを実行しても、何も表示されません (他のリモート セッションが動作していない場合)。
  
![リモート セッションのない Windows PowerShell コンソール](images/o365_powershell_no_remote_sessions.png)
  
> [!NOTE]
> すべてのリモート セッションを同時に閉じたい場合は、次のコマンドを使用することができます。 >  `Get-PSSession | Remove-PSSession`
  
ここで、これらの閉じたセッションのいずれかからコマンドレット (たとえば、Skype for Business Online で **Get-CsMeetingConfiguration** ) を実行しようとすると、次のようなエラー メッセージが表示されます。
  
```
Get-CsMeetingConfiguration : The term 'Get-CsMeetingConfiguration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

このエラー メッセージが表示されるのは、リモート セッションを閉じたときに Skype for Business Online コマンドレット、Exchange Online コマンドレット、および セキュリティ センターとコンプライアンス センター コマンドレットが削除されたためです。
  
SharePoint Online セッションを閉じるには、次のコマンドを入力します。
  
```
Disconnect-SPOService
```

ここで **Get-SPOSite** コマンドレットを実行しようとすると、次のようなエラー メッセージが表示されます。
  
```
get-sposite : No connection available. Use Connect-SPOService before running this CmdLet.
```

もう SharePoint Online には接続されていないため、サイト情報を取得できません。
  
Office 365 への接続とが**接続する MsolService**コマンドレットは**切断-MsolService**の対応するコマンドレットです。したがって、Office 365 のだけ Windows PowerShell の] ウィンドウを閉じます。これを行うことをお勧めすることがまだそれにもかかわらず、最後のことができます正しく接続を切断する sharepoint サイトからオンラインで Skype オンライン ビジネス、オンラインの Exchange セキュリティのため&amp;コンプライアンス センターです。
  
## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合
<a name="LongVersion"> </a>

||
|:-----|
|![LinkedIn Learning の小さいアイコン](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Office 365 を初めて使用する場合は、**         LinkedIn Learning が提供する [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5) のための無料のビデオ コースをご覧ください。 |
   
## <a name="see-also"></a>See also

#### 

[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)
  
[Office 365 PowerShell を使用して SharePoint Online を管理する](manage-sharepoint-online-with-office-365-powershell.md)
  
[Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Windows PowerShell を使用して Office 365 でレポートを作成する](use-windows-powershell-to-create-reports-in-office-365.md)

