---
title: Microsoft 365 で PowerShell を使用する必要がある理由
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: '概要: PowerShell を使用して Microsoft 365 を管理する必要がある理由について説明します。場合によっては効率的で、その他の場合は必要になることがあります。'
ms.openlocfilehash: ba786acd8b5ad08bad97b11812f0180004e55cb6
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229863"
---
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a>Microsoft 365 で PowerShell を使用する必要がある理由

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

Microsoft 365 管理センターを使用すると、Microsoft 365 のユーザーアカウントとライセンスを管理できるだけでなく、Exchange Online、Teams、SharePoint Online などの Microsoft 365 サービスを管理することもできます。 ただし、これらの要素を PowerShell コマンドで管理することもできます。これには、速度、自動化、および追加機能について、コマンドラインおよびスクリプト言語環境を利用できます。
  
この記事では、PowerShell を使用して Microsoft 365 を管理する方法について説明します。
  
- Microsoft 365 管理センターでは表示できない追加情報を確認する
    
- PowerShell でのみ使用可能な機能と設定を構成する
    
- 一括操作を実行する
    
- データのフィルター処理
    
- データを印刷または保存する
    
- サービス間で管理する
    
作業を開始する前に、「Microsoft 365 用の PowerShell」は、windows PowerShell 用のモジュールのセットで、Windows ベースのサービスとプラットフォーム用のコマンドライン環境です。 この環境では、コマンドシェル言語が作成されます。これにより、追加モジュールを使用して拡張することができ、単純なコマンドやスクリプトを実行することができます。 たとえば、microsoft 365 モジュールの PowerShell をインストールし、Microsoft 365 サブスクリプションに接続した後、次のコマンドを実行して Microsoft Exchange Online のすべてのユーザーメールボックスを一覧表示できます。
  
```powershell
Get-Mailbox
```

メールボックスのリストを取得することも、Microsoft 365 管理センターを使用して簡単に行うことができますが、すべての web アプリのすべてのサイトについて、すべてのリストのアイテム数をカウントすることは簡単に行えません。
  
Microsoft 365 用の PowerShell は、microsoft の365管理センターを置き換えるのではなく、Microsoft の365を管理する機能を強化し、強化するように設計されています。 管理者は、microsoft 365 コマンドの PowerShell でしか実行できない構成手順があるため、Microsoft 365 での PowerShell の使用に関して、少なくとも使い慣れておく必要があります。 このような場合は、次の方法を理解する必要があります。
  
- Microsoft 365 モジュールの PowerShell をインストールします (管理者のコンピューターごとに1回だけ実行されます)。
    
- Microsoft 365 サブスクリプションに接続します (PowerShell セッションごとに1回実行します)。
    
- Microsoft 365 コマンドに必要な PowerShell を実行するために必要な情報を収集します。
    
- Microsoft 365 コマンドの PowerShell を正常に実行します。
    
これらの基本的なスキルを習得すれば、 **Get-mailbox** コマンドを使用してメールボックス ユーザーの一覧を作成する必要もなければ、すべての Web アプリ用のすべてのサイトのすべての一覧に含まれるすべてのアイテムをカウントするための前述のコマンドのような新しいコマンドを作成する方法を理解する必要もありません。 Microsoft と管理者コミュニティは、必要に応じてお手伝いします。
  
## <a name="powershell-for-microsoft-365-can-reveal-additional-information-that-you-cannot-see-with-the-microsoft-365-admin-center"></a>Microsoft 365 の PowerShell では、Microsoft 365 管理センターでは表示できない追加情報を確認できます。

Microsoft 365 管理センターでは、多くの有益な情報が表示されますが、これは、ユーザー、ライセンス、メールボックス、サイトに Microsoft 365 が保存する可能性がある情報をすべて表示するという意味ではありません。 Microsoft 365 管理センターの**ユーザーとグループ**の例を次に示します。
  
![Microsoft 365 管理センターでのユーザーとグループの表示例。](media/o365-powershell-users-and-groups.png)
  
ここには、さまざまな理由で把握すべき情報が表示されます。 しかし、もっと多くの情報が必要な場合もあります。 たとえば、Microsoft 365 ライセンス (およびユーザーが使用できる Microsoft 365 機能) は、そのユーザーの地理的な場所によって異なります。 米国内に在住しているユーザーに対して拡張可能なポリシーと機能は、インドやベルギー在住のユーザーに対して拡張可能なポリシーと機能と同じではない場合があります。 Microsoft 365 管理センターを使用して、ユーザーの地理的な場所を確認するには、次の手順を実行します。
  
1. ユーザーの **表示名** をダブルクリックします。
    
2. ユーザーのプロパティを表示するウィンドウで、 **[詳細]** をクリックします。
    
3. 詳細表示で、 **[追加情報]** をクリックします。
    
4. **[国/地域]** という見出しが表示されるまでスクロールダウンします。
    
     ![Microsoft 365 管理センター内のユーザーの地域情報の例。](media/o365-powershell-usage-location.png)
  
5. ユーザーの表示名と場所を紙に書き留めるか、コピーしてメモ帳に貼り付けます。 
    
この手順をユーザーごとに繰り返す必要があります。 これは多くのユーザーにとって、面倒な作業でしょう。 Microsoft 365 の PowerShell では、次のコマンドを使用して、すべてのユーザーについてこの情報を表示することができます。
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
>PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
>

表示例:
  
```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプション ( **set-azureaduser** ) 内のすべてのユーザーを取得しますが、各ユーザーの名前と場所のみを表示します ( **DisplayName、使用場所の選択**)。
  
Microsoft 365 用の PowerShell はコマンドシェル言語をサポートしているため、 **set-azureaduser**コマンドで取得した情報をさらに操作することができます。 たとえば、これらのユーザーを場所によって並べ替えたり、すべてのブラジルユーザーを一緒にグループ化したり、すべての米国ユーザーを一緒にグループ化したりしたい場合があります。コマンドは次のとおりです。
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

表示例:
  
```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

> [!TIP]
>  この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプションのすべてのユーザーを取得しますが、各ユーザーの名前と場所のみを表示し、それらの名前と名前 (**並べ替えを使用した場所、DisplayName** ) を最初に並べ替えます。
  
また、フィルター処理を追加することもできます。たとえば、ブラジル在住のユーザーに関する情報のみを表示する場合には、次のコマンドを使用します。
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

表示例:
  
```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプションで、場所がブラジルであるすべてのユーザーを取得します ( **Where {$ \_ .[使用場所]-eq "BR"}** ) で、各ユーザーの名前と場所を表示します。
  
 **規模の大きいドメインに関する注意事項**
  
ドメインの規模が非常に大きい場合 (たとえば、何万人ものユーザーが属している場合)、この記事に記載する一部の例で、「スロットリング」が発生する場合があります。 これはつまり、計算能力や使用可能なネットワーク帯域幅などを上回る操作を、一度に実行しようとしていることを意味します。 そのため、大規模な組織では、Microsoft 365 コマンド用にこれらの PowerShell の一部を2つのコマンドに分割することをお勧めします。 たとえば、次の 1 つのコマンドはすべてのユーザー アカウントを返し、それぞれの名前と場所を示します。
  
```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

このコマンドは、規模が小さいドメインには最適に機能します。しかし大規模な組織では、これを 2 つのコマンドに分けて、一方のコマンドでユーザー アカウント情報を変数に格納し、もう一方のコマンドで必要な情報を表示することが必要になる可能性があります。次に例を示します。
  
```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

この PowerShell コマンドのセットは次のように解釈されます。
- 現在の Microsoft 365 サブスクリプション内のすべてのユーザーを取得し、その情報を $x ( **$x = set-azureaduser** ) という名前の変数に格納します。
- 変数 $x の内容のうち、各ユーザーの名前と場所のみを表示します (**$x | Select DisplayName, UsageLocation**)。
  
## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a>Microsoft 365 には、Microsoft 365 の PowerShell でのみ構成できる機能があります。

Microsoft 365 管理センターは、ほとんどのユーザーに適用される最も一般的な管理タスクまたは意味のある管理タスクへのアクセスを提供することを目的としています。 つまり、Microsoft 365 管理センターは、一般的な管理者がツールを使用して最も一般的な管理タスクを実行できるように設計されています。 この定義により、Microsoft 365 管理センターを使用して完了できないタスクがいくつかあることを意味します。
  
たとえば、Skype for Business Online 管理センターにはカスタムの会議出席依頼を作成するためのいくつかのオプションが備わっています。
  
![Skype for Business Online 管理センターでカスタムの会議出席依頼を表示する例です。](media/o365-powershell-meeting-invitation.png)
  
これらの設定を使用すると、会議出席依頼にパーソナルでプロフェッショナルな風合いを加えることができます。しかし、会議の構成設定には、カスタムの会議出席依頼を作成する以上の事柄が関係します。たとえば、既定では会議に関して以下の事柄が許可されています。
  
- 匿名ユーザーが、各会議に自動的に参加すること。
    
- 参加者が、会議を記録すること。
    
- 組織のすべてのユーザーが、会議に参加するときに発表者として指定されること。
    
これらの設定に関しては、Skype for Business Online 管理センターからは行うことができません。 ただし、Microsoft 365 については PowerShell を使用して制御できます。 これらの 3 つの設定を無効にするコマンドを次に示します。
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> このコマンドを実行するには、[Skype for Business Online PowerShell モジュール](https://www.microsoft.com/download/details.aspx?id=39366)をインストールする必要があります。 
  
> [!TIP]
>  この PowerShell コマンドの解釈は次のとおりです。新しい Skype for Business Online 会議 ( **AdmitAnonymousUsersByDefault $False** **) の**設定については、匿名ユーザーの会議への自動開始を許可しないようにします (- **AllowConferenceRecording $False** )。また、組織のすべてのユーザーを発表者として指定しない ( **-designateaspresenter "None"** )。
  
方針を変えて既定の設定に戻す (これらすべてを有効にする) 場合には、次のコマンドを実行します。
  
```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

これは一例に過ぎません。 他にもあります。このため、管理者は Microsoft 365 コマンドの PowerShell の実行に慣れている必要があります。
  
## <a name="powershell-for-microsoft-365-is-great-at-carrying-out-bulk-operations"></a>Microsoft 365 の PowerShell は一括操作を実行するのに適しています。

従来は、単一の操作を実行すると、Microsoft 365 管理センターのようなビジュアルインターフェイスが最も重要になります。 たとえば、1つのユーザーアカウントを無効にする必要がある場合は、Microsoft 365 管理センターを使用して、チェックボックスをすばやく見つけてクリアすることができます。 これは、PowerShell で同様の操作を実行するよりも簡単になります。
  
しかし、その他の多くの場合に、多数の項目や選択したものを変更する必要がある場合は、Microsoft 365 管理センターがお客様の時間を最適に使用しないことがあります。 たとえば、数千人の電話番号のプレフィックスを変更する必要がある場合や、特定のユーザー (Ken Myer) をすべての SharePoint Online サイトから削除する必要がある場合は、Microsoft 365 管理センターでどうすればよいでしょうか。
  
後者の例の場合、何百もの SharePoint Online サイトがあり、Ken Meyer がメンバーのサイトも判断できません。 そのため、Microsoft 365 管理センターから開始して、各サイトでこの手順を実行する必要があります。
  
1. サイトの **URL** をクリックします。
    
2. [ **サイト コレクションのプロパティ** ] ボックスで、[ **Web サイトのアドレス** ] リンクをクリックしてサイトを開きます。
    
3. サイトの [ **共有** ] をクリックします。
    
4. [ **共有** ] ダイアログ ボックスで、サイトへのアクセス権限を持つすべてのユーザーを表示するリンクをクリックします。
    
     ![SharePoint Online 管理センターの SharePoint Online サイトのメンバーを表示する例です。](media/o365-powershell-view-permissions.png)
  
5. [ **共有相手** ] ダイアログ ボックスで、[ **詳細設定** ] をクリックします。
    
6. ユーザーの一覧をスクロール ダウンし、Ken Myer (サイトへのアクセス権限を持っていることが前提) を見つけて選択してから、[ **ユーザー権限の削除** ] をクリックします。
    
何百ものサイトがある場合、長時間かかる可能性があります。
  
別の方法として、Microsoft 365 の PowerShell を使用し、次のコマンドを使用して、すべてのサイトから Ken Myer を削除します。
  
```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> このコマンドを実行するには、 [SharePoint Online PowerShell モジュール](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)をインストールする必要があります。 
  
> [!TIP]
>  この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプション ( **get-sposite** ) 内のすべての SharePoint サイトを取得し、各サイトについて、アクセス可能なユーザーのリストから Ken Meyer を削除し**ます (ForEach {Remove-Spouser-site $ \_ 。Url-ログイン "kenmyer@litwareinc.com"}** )。
  
ユーザーがアクセス権を持っていないものも含めて、すべてのサイトから Ken Meyer を削除するよう Microsoft 365 に指示しているため、このコマンドの表示では、現在アクセスできないサイトに関するエラーが表示されます。 このコマンドで追加の条件を使用して、彼がログインリストにあるサイトからのみキー Meyer のみを削除することができますが、リストされているエラーによってサイト自体に悪影響が生じることはありません。 このコマンドは、Microsoft 365 管理センターで作業する時間ではなく、数百のサイトに対して実行されるまでに数分かかる場合があります。
  
別の一括操作の例を次に示します。このコマンドを使用して、新しい SharePoint 管理者である Bonnie Kearney を組織内のすべてのサイトに追加します。
  
```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプション内のすべての SharePoint サイトを取得し、各サイトについて、サイトのメンバーグループにログイン名を追加して Bonnie Kearney access を許可します ( **ForEach {Add-SPOUser-site $ \_ 。Url-ログイン "bkearney@litwareinc.com"-グループ "メンバー"}** )。
  
## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a>Microsoft 365 の PowerShell は、データのフィルター処理に適しています。

Microsoft 365 管理センターでは、データをフィルター処理して、対象となる情報のサブセットを迅速かつ簡単に見つけられるように、さまざまな方法を使用できます。 たとえば、Exchange では、ユーザー メールボックスのほとんどすべてのプロパティに対するフィルターを簡単に適用できます。 たとえば、以下は、Bloomington 市に在住のすべてのユーザーのメールボックスを一覧表示する例です。
  
![ブルーミントンの市区町村に居住しているすべてのユーザーのメールボックスの一覧については、Microsoft 365 管理センターで高度な検索を実行する例を示します。](media/o365-powershell-advanced-search.png)
  
Exchange 管理センターでは、フィルター条件を組み合わせることもできます。たとえば、ブルーミントン市に住み、経理部で働いているすべての住民のメールボックスを見つけることができます。 
  
しかし、Exchange 管理センターで行えることには限界があります。たとえば、ブルーミントンかサンディエゴに住んでいる住民のメールボックスを検索したい場合や、ブルーミントンに住んでいないすべての住民のメールボックスを検索したい場合もあるでしょう。 
  
Microsoft 365 の PowerShell では、次のコマンドを使用して、ブルーミントンまたはサンディディエゴの都市に居住しているすべてのユーザーのメールボックスの一覧を取得できます。
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

表示例:
  
```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

> [!TIP]
>  この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプションで、メールボックスが San ディエゴまたはブルーミントン (Where {$) のいずれかの都市にあるすべてのユーザーを取得します** \_ 。[受信者] Typetypedetails-eq "UserMailbox"-and ($ \_ .City-eq "サンディエゴ"-または $ \_ 。City-eq "ブルーミントン")}** ) で、それぞれの名前と市区町村を表示します ( **DisplayName、City を選択**)。
  
ブルーミントン以外に居住しているユーザーのメールボックスをすべて一覧表示するには、次のコマンドを使用します。
  
```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

表示例:
  
```powershell
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

> [!TIP]
>  この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプションで、メールボックスがブルーミントンの city (Where {$) にないすべてのユーザーを取得します** \_ 。[受信者] Typetypedetails-eq "UserMailbox"-and $ \_ 。City-ne "ブルーミントン"}** ) で、それぞれの名前と市区町村を表示します。
  
また、PowerShell フィルターでワイルドカード文字を使用して、名前の一部と一致させることもできます。 たとえば、あるユーザー アカウントを探しているものの、名字が Anderson か Henderson であることしか思い出せず、もしかすると Jorgenson だったかもしれないとします。
  
検索ツールを使用して、次の3つの異なる検索を実行することによって、Microsoft 365 管理センターでそのユーザーを追跡することができます。
  
- *Anderson*  用のもの 
    
- *Henderson*  用のもの 
    
- *Jorgenson*  用のもの 
    
これらの3つの名前はすべて "son" で終わるので、名前が "son" で終わるすべてのユーザーを表示するように PowerShell に指示できます。 コマンドを次に示します。
  
```powershell
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  この PowerShell コマンドは、次のように解釈されます。現在の Microsoft 365 サブスクリプション内のすべてのユーザーを取得しますが、姓が "son" で終わるユーザーを一覧表示するフィルターを使用します ( **-filter ' {LastName-like " \* son"} '** )。 は、 \* 任意の文字セット (ユーザーの姓の場合は文字) で表します。
  
## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a>Microsoft 365 の PowerShell を使用すると、データの印刷や保存が容易になります。

Microsoft 365 管理センターでは、データの一覧を表示できます。 以下に、skype for business online 管理センターの例を示します。このリストには、Skype for business Online が有効になっているユーザーの一覧が表示されます。
  
![Skype for Business Online 管理センターで、Skype for Business Online に対して有効になっているユーザーの一覧を表示する例です。](media/o365-powershell-lync-users.png)
  
この情報をファイルに保存するには、コピーしてドキュメントまたは Excel に貼り付ける必要があります。 どちらの場合も、コピー操作には追加の書式設定が必要になる場合があります。 また、Microsoft 365 管理センターでは、表示されている一覧を直接印刷する方法は提供されていません。
  
さいわい、PowerShell を使用してリストを表示するだけでなく、Excel に簡単にインポートできるファイルに保存することもできます。 以下に、Skype for Business Online ユーザーデータをコンマ区切り値 (CSV) ファイルに保存するコマンドの例を示します。これは、Excel ワークシートのテーブルとして簡単にインポートできるファイルです。
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

表示例:
  
![Excel ワークシートにインポートされている、コンマ区切り値 (CSV) ファイルに保存された Skype for Business Online ユーザー データに関するテーブルの例です。](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプションのすべての Skype for Business Online ユーザーを取得します (**取得**します)。ユーザー名、UPN、および場所のみを取得し ( **DisplayName、UserPrincipalName、使用場所を選択**)、その情報を c: \\ Logs \\SfBUsers.csv ( **Export-csv-Path "C: \\ logs \\SfBUsers.csv"-notypeinformation** ) という名前で保存します。
  
また、オプションを使って、この一覧を XML ファイルや HTML ページとして保存できます。実際、追加の PowerShell コマンドを使い、必要なカスタム書式設定で直接 Excel ファイルとして保存できます。 
  
また、Windows の既定のプリンターにリストを直接表示する PowerShell コマンドの出力を送信することもできます。 コマンド例を次に示します。
  
```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

印刷されたドキュメントは次のようになります。
  
![Windows の既定のプリンターに直接表示されている PowerShell コマンドの出力である印刷されたドキュメントの例です。](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  この PowerShell コマンドの解釈は次のとおりです。現在の Microsoft 365 サブスクリプションの Skype for Business Online ユーザーをすべて取得し、ユーザー名、UPN、および場所のみを取得して、その情報を既定の Windows プリンター (**出力プリンター** ) に送信します。
  
印刷された文書の簡単な書式設定は PowerShell コマンドウィンドウでの表示と同じですが、必要なものを一覧表示する PowerShell コマンドを作成したら、追加するだけでも **|** コマンドの最後にプリンターを使用して、ハードコピーを取得します。
  
## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a>Microsoft 365 の PowerShell を使用すると、複数のサーバー製品を管理できます。

Microsoft 365 を構成するさまざまなコンポーネントは、連携して動作するように設計されています。 たとえば、Microsoft 365 に新しいユーザーを追加した場合に、ユーザーの部署や電話番号などの情報を指定するとします。 この情報は、Microsoft 365 サービスのいずれかを使用してユーザーの情報にアクセスすると、Skype for Business Online、Exchange、または SharePoint Online のいずれかを使用して利用できるようになります。
  
ただし、これは製品のスイートに共通する一般情報の場合です。製品固有の情報 (たとえば、ユーザーの Exchange メールボックスに関する情報など) は基本的にはスイートのすべての製品で入手できるようにはなっていません。たとえば、ユーザーのメールボックスが有効になっているかどうかを把握したい場合などには、Exchange 管理センターにおいてのみこの情報が取得できます。 
  
すべてのユーザーに関する次のような情報を示すレポートを作成するとします。
  
- ユーザーの表示名
    
- ユーザーが Microsoft 365 用にライセンスされているかどうか
    
- ユーザーの Exchange メールボックスが有効になっているかどうか
    
- ユーザーが Skype for Business Online に対して有効になっているかどうか
    
現時点では、Microsoft 365 管理センターを使用してこのようなレポートを簡単に作成することはできません。 その代わりに、Excel ワークシートのような情報を格納するための別のドキュメントを作成し、Microsoft 365 管理センターからすべてのユーザー名とライセンス情報を取得し、Exchange 管理センターからメールボックス情報を取得して、skype for business online 管理センターからの Skype for Business Online 情報を取得し、それらの情報を照合して組み合わせます。
  
別の方法として、PowerShell スクリプトを使用してレポートをコンパイルできます。
  
次のスクリプト例は、この記事でこれまでに示したコマンドの中で最も複雑です。 しかし、PowerShell を使用して情報のビューを作成することによって、そのような操作が非常に困難になる可能性があることがわかります。 必要な一覧をコンパイルして表示するスクリプトを次に示します。
  
```powershell
$x = Get-AzureADUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

表示例:
  
```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

この PowerShell スクリプトの解釈は次のとおりです。  

- 現在の Microsoft 365 サブスクリプション内のすべてのユーザーを取得し、その情報を $x ( **$x = set-azureaduser** ) という名前の変数に格納します。
- $x という変数内のすべてのユーザーに対して実行されるループを開始します (**foreach ($i in $x)**)。  
- $y という名前の変数を定義し、ユーザーのメールボックス情報をその変数に格納します (**$y = Get-Mailbox -Identity $i.UserPrincipalName**)。
- ユーザー情報に IsMailBoxEnabled という新しいプロパティを追加し、このプロパティの値に、ユーザーのメールボックスの IsMailBoxEnabled プロパティの値を設定します (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**)。
- $y という変数を定義し、ユーザーの Skype for Business Online 情報をその変数に格納します (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**)。
- EnabledForSfB という名前の新しいプロパティをユーザー情報に追加し、このプロパティの値に、ユーザーの Skype for Business Online 情報の Enabled プロパティの値を設定します (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**)。
- ユーザーの一覧を表示します。ただし、含めるのは、ユーザー名、ライセンス認定されているかどうか、およびメールボックスが使用可能かどうかと Skype for Business Online に対して有効かどうかを示す 2 つの新たなプロパティのみとします (**$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**)。
  
## <a name="see-also"></a>関連項目

[Microsoft 365 の PowerShell の概要](getting-started-with-office-365-powershell.md)
  
[PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Windows PowerShell を使用して Microsoft 365 でレポートを作成する](use-windows-powershell-to-create-reports-in-office-365.md)

