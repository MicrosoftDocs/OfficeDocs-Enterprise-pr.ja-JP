---
title: "PowerShell を使用して Office 365 への段階的な移行を実行する"
ms.author: sirkkuw
author: sirkkuw
manager: scotv
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: "概要:Windows PowerShell を使用して Office 365 への段階的な移行を実行する方法について説明します。"
ms.openlocfilehash: 5143b039937389d965386de0e09f4f59db071c86
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a>PowerShell を使用して Office 365 への段階的な移行を実行する

 **概要:** Windows PowerShell を使用して Office 365 への段階的な移行を実行する方法について説明します。
  
段階的な移行を使用すると、ユーザーのメールボックスの内容を、元の電子メール システムから Office 365 に徐々に移行することができます。
  
この記事では、Exchange Online PowerShell を使用した段階的メール移行に関するタスクを順を追って説明します。トピック「[Office 365 への段階的メール移行について知っておくべきこと](https://go.microsoft.com/fwlink/p/?LinkId=536487)」では、移行プロセスについて概説しています。記事の内容に満足いただけたら、段階的メール移行を使用して、あるメール システムから別のメール システムへのメールボックスの移行を開始してください。
  
> [!NOTE]
> また、段階的な移行を実行するには、Exchange 管理センターを使用することもできます。「[Office 365 へのメールの段階的な移行を実行する](https://go.microsoft.com/fwlink/p/?LinkId=536687)」を参照してください。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>始める前に把握しておくべき情報

このタスクの予想所要時間:移行バッチの作成に 2 ～ 5 分。移行バッチ開始後の移行時間は、バッチ内のメールボックスの数、各メールボックスのサイズ、および使用可能なネットワーク容量によって異なります。Office 365 にメールボックスの移行時間を決定するその他の要因の詳細については、「[移行のパフォーマンス](https://go.microsoft.com/fwlink/p/?LinkId=275079)」を参照してください。
  
この手順を実行する際には、あらかじめアクセス許可を割り当てる必要があります。必要なアクセス許可を確認するには、トピック「[受信者のアクセス許可](https://go.microsoft.com/fwlink/p/?LinkId=534105)」の中の「移行」エントリを参照してください。
  
Exchange Online PowerShell コマンドレットを使用するには、サインインしてコマンドレットをローカルの Windows PowerShell セッションにインポートする必要があります。手順については、「[リモート PowerShell による Exchange への接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)」を参照してください。
  
移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。
  
## <a name="migration-steps"></a>移行の手順

### <a name="step-1-prepare-for-a-staged-migration"></a>ステップ 1:段階的な移行を準備する

段階的な移行を使用してメールボックスを Office 365 に移行する前に、Exchange 環境に対していくつかの変更を加える必要があります。
  
 **社内の Exchange Server** に Outlook Anywhere を構成する: メール移行サービスは、Outlook Anywhere (RPC over HTTP としても知られる) を使用して社内の Exchange Server に接続します。Exchange Server 2007 と Exchange 2003 における Outlook Anywhere の設定方法の詳細については、以下を参照してください。
  
- 「[Exchange 2007:Outlook Anywhere を有効にする方法](https://go.microsoft.com/fwlink/?LinkID=167210)」
    
- 「[Exchange 2003 での Outlook Anywhere を構成する方法](https://go.microsoft.com/fwlink/?LinkID=167209)」
    
> [!IMPORTANT]
> Outlook Anywhere の構成には、信頼された証明機関 (CA) によって発行された証明書を使用する必要があります。Outlook Anywhere は、自己署名入りの証明書で構成することはできません。詳細については、「[Outlook Anywhere のために SSL を構成する方法](https://go.microsoft.com/fwlink/?LinkID=80875)」を参照してください。 
  
 **オプション:Outlook Anywhere**を使用して Exchange 組織に接続できることを確認する: 接続設定をテストするには、次のいずれかの方法を試します。
  
- 企業ネットワークの外部から Outlook を使用して社内の Exchange メールボックスに接続します。
    
- [Microsoft Exchange リモート接続アナライザー]((https://www.testexchangeconnectivity.com/))を使用して接続設定をテストします。Outlook Anywhere (RPC over HTTP) または Outlook 自動検出テストを使用します。
    
- Exchange Online PowerShell で次のコマンドを実行します。
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **アクセス許可を設定する**: 社内 Exchange 組織に接続するために使用する社内ユーザー アカウント (移行管理者ともいう) には、Office 365 に移行する社内メールボックスにアクセスするためのアクセス許可が必要です。このユーザー アカウントは、この手順の後半に記載する移行エンドポイント ([ステップ 3:移行エンドポイントを作成する](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint)) を作成して電子メール システムに接続するときに使用します。
  
メールボックスを移行するために、管理者には次のアクセス許可セットのいずれかが必要です。
  
- 社内組織の Active Directory の **Domain Admins** グループのメンバーであること。
    
    or
    
- 社内の各メールボックスに **FullAccess** のアクセス許可が割り当てられ、社内のユーザー アカウントの **TargetAddress** プロパティを変更するための **WriteProperty** のアクセス許可が割り当てられていること。
    
    or
    
- ユーザー メールボックスを格納する社内のメールボックス データベースに **受信者** のアクセス許可が割り当てられ、社内のユーザー アカウントの **TargetAddress** プロパティを変更するための **WriteProperty** のアクセス許可が割り当てられていること。
    
これらのアクセス許可を設定する方法については、「[Exchange Online にメールボックスを移行するためのアクセス許可の割り当て](https://go.microsoft.com/fwlink/?LinkId=521656)」を参照してください。
  
 **ユニファイド メッセージング (UM) を無効にする**: 移行する社内のメールボックスで UM がオンになっている場合は、移行前に UM をオフにします。移行の完了後に、メールボックスの UM をオンにします。操作手順については、「[ユーザーのユニファイド メッセージングを無効にする方法](https://go.microsoft.com/fwlink/?LinkId=521891)」を参照してください。
  
 **ディレクトリ同期を使用して Office 365 でユーザーを新規作成します。**ディレクトリ同期を使用すると、Office 365 組織のすべての社内ユーザーを作成できます。
  
ユーザーの作成後にライセンスを付与する必要があります。ユーザーの作成後、ライセンスを追加するまでに 30 日間があります。ライセンスを追加する手順については、「[ステップ 8:移行後のタスクを完了する](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration)」を参照してください。
  
 Microsoft Azure Active Directory 同期ツール、または、Microsoft Azure Active Directory 同期サービス (AAD Sync) のいずれかを使用すると、Office 365 と同期して社内ユーザーを作成できます。メールボックスが Office 365 に移行されたら、社内組織内のユーザー アカウントを管理します。これにより、ユーザー アカウントは Office 365 組織と同期されます。詳細については、「[ディレクトリ統合](https://go.microsoft.com/fwlink/?LinkId=521788)」を参照してください。
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>ステップ 2:段階的な移行バッチ用の CSV ファイルを作成する

Office 365 に移行する社内のメールボックスのユーザーを特定したら、コンマ区切りの値 (CSV) ファイルを使用して移行バッチを作成します。Office 365 が移行の実行に使用する CSV ファイルの各行には、社内メールボックスに関する情報が含まれています。 
  
> [!NOTE]
> 段階的移行により Office 365 に移行する場合、移行可能なメールボックスの数に制限はありません。移行バッチ用の CSV ファイルに含めることができる行数は、最大 2,000 行までです。2,000 を超えるメールボックスを移行するには、追加の CSV ファイルを作成し、各ファイルを使用して新しい移行バッチを作成します。 
  
 **サポートされている属性**
  
段階的な移行用の CSV ファイルは、次の 3 つの属性をサポートします。CSV ファイルの各行はメールボックスに対応し、各属性の値を含める必要があります。
  
|**属性**|**説明**|**必須**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |プライマリ SMTP 電子メール アドレス (たとえば、社内メールボックスの場合は pilarp@contoso.com など) を指定します。  <br/> 社内メールボックスには、プライマリ SMTP アドレスを使用し、Office 365 のユーザー ID は使用しないでください。たとえば、社内ドメインが contoso.com という名前で、Office 365 の電子メール ドメインが service.contoso.com という名前の場合、CSV ファイル内の電子メール アドレスにはドメイン名 contoso.com を使用します。  <br/> |必須  <br/> |
|Password  <br/> |新しい Office 365 メールボックスに設定されるパスワード。Office 365 の組織に適用されるパスワードの制約はすべて、CSV ファイル内のパスワードにも適用されます。  <br/> |省略可能  <br/> |
|ForceChangePassword  <br/> |ユーザーが新しい Office 365 メールボックスに初めてサインインする場合に、パスワードを変更する必要があるかどうかを指定します。このパラメーターの値には **True** または **False** を使用してください。<br/> > [!NOTE]> Active Directory フェデレーション サービス (AD FS) 以上を社内組織に展開してシングル サインオン (SSO) ソリューションを実装した場合、 **ForceChangePassword** 属性の値には **False** を使用する必要があります。          |省略可能  <br/> |
   
 **CSV ファイル形式**
  
以下に、CSV ファイルの形式の例を示します。この例では、3 つの社内メールボックスが Office 365 に移行されます。
  
CSV ファイルの最初の行、つまりヘッダー行には、後続の行で指定される属性 (つまり、フィールド) の名前が示されます。各属性名はコンマで区切られます。
  
```
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

ヘッダー行の下の各行は個々のユーザーを表します。これらの行には、そのユーザーのメールボックスを移行するための情報が含まれます。各行の属性値は、ヘッダー行の属性名と同じ順序で並んでいる必要があります。 
  
CSV ファイルの作成には、任意のテキスト エディターや Excel などのアプリケーションを使用します。ファイルは .csv ファイルまたは .txt ファイルとして保存します。
  
> [!NOTE]
> CSV ファイルに非 ASCII 文字や特殊文字が含まれている場合は、UTF-8 などの Unicode エンコードで CSV ファイルを保存してください。アプリケーションによっては、コンピューターのシステム ロケールが CSV ファイルで使用されている言語と一致するときに、CSV ファイルを UTF-8 などの Unicode エンコードで保存した方が簡単な場合があります。 
  
### <a name="step-3-create-a-migration-endpoint"></a>ステップ 3:移行エンドポイントを作成する
<a name="BK_Endpoint"> </a>

電子メールを正常に移行するためには、Office 365 は移行元の電子メール システムと接続して通信する必要があります。これを実行するため、Office 365 では移行エンドポイントを使用します。PowerShell を使用して Outlook Anywhere 移行エンドポイントを作成するには、段階的な移行で、最初に[リモート PowerShell による Exchange への接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)を行います。 
  
移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。
  
Exchange Online PowerShell に "StagedEndpoint" という Outlook Anywhere 移行エンドポイントを作成するには、次のコマンドを実行します。
  
```
$Credentials = Get-Credential
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

**New-MigrationEndpoint** コマンドレットの詳細については、「[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)」を参照してください。
  
> [!NOTE]
> **New-MigrationEndpoint** コマンドレットで **-TargetDatabase** オプションを使用することによって、使用するサービスに対してデータベースを指定することができます。それ以外の場合、データベースは、管理メールボックスが配置されている Active Directory フェデレーション サービス (AD FS) 2.0 サイトからランダムに割り当てられます。
  
#### <a name="verify-it-worked"></a>機能していることを確認する

Exchange Online PowerShell で、次のコマンドを実行して "StagedEndpoint" 移行エンドポイントに関する情報を表示します。
  
```
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>ステップ 4:段階的な移行のバッチを作成および開始する
<a name="BK_Endpoint"> </a>

Exchange Online PowerShell の **New-MigrationBatch** コマンドレットを使用すると、一括移行の移行バッチを作成できます。 _AutoStart_ パラメーターを含めると、移行バッチを作成して自動的に開始できます。また、別の方法として、 **Start-MigrationBatch** コマンドレットを使用することにより、移行バッチを作成して後で手動で開始できます。この例では、"StagedBatch1" という移行バッチを作成して、前の例で作成した移行エンドポイントを使用します。
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

この例でも、"StagedBatch1" という移行バッチを作成して、前の例で作成した移行エンドポイントを使用します。 _AutoStart_ パラメーターが含まれていないため、移行バッチは移行ダッシュボードで、または **Start-MigrationBatch** コマンドレットを使用して手動で開始する必要があります。前述のように、一度に存在できる一括移行バッチは 1 つだけです。
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>機能していることを確認する

Exchange Online PowerShell で次のコマンドを実行すると、「StagedBatch1」に関する情報が表示されます。
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

また、次のコマンドを実行すると、バッチが開始されたことを確認できます。
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

**Get-MigrationBatch** コマンドレットの詳細については、「[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)」を参照してください。
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>ステップ 5:社内メールボックスをメールが有効なユーザーに変換する
<a name="BK_Endpoint"> </a>

メールボックスのバッチが正常に移行されたら、何らかの方法でユーザーが各自のメールにアクセスできるようにする必要があります。メールボックスが移行されたユーザーには、社内のメールボックスと Office 365 のメールボックスの両方があります。Office 365 のメールボックスを持つユーザーは、社内のメールボックスで新着メールの受信が停止します。 
  
移行が完了していないため、まだすべてのユーザーが Office 365 から各自の電子メールにアクセスできる状態ではありません。両方のメールボックスを持つユーザーに対してはどのようにすれば良いでしょうか。既に移行済みの社内メールボックスをメールが有効なユーザーに変更することができます。メールボックスからメールが有効なユーザーに変更した場合、社内メールボックスに移動するのではなく、ユーザーを Office 365 から各自の電子メールにアクセスさせることができます。 
  
社内メールボックスをメールが有効なユーザーに変換するもう 1 つの重要な理由は、プロキシ アドレスをメールが有効なユーザーにコピーすることで、Office 365 メールボックスからのプロキシ アドレスを保持するためです。これにより、Active Directory を使用して社内組織からクラウドベースのユーザーを管理できます。また、すべてのメールボックスを Office 365 に移行した後に、社内 Exchange Server 組織を停止する場合、メールが有効なユーザーにコピーされたプロキシ アドレスは、社内 Active Directory に残ります。
  
メールボックスをメールが有効なユーザーに変換するために実行できるスクリプトの詳細とダウンロード方法については、以下を参照してください。
  
- 「[Exchange 2007 メールボックスをメールが有効なユーザーに変換する](https://go.microsoft.com/fwlink/p/?LinkId=233648)」
    
- 「[Exchange 2003 メールボックスをメールが有効なユーザーに変換する](https://go.microsoft.com/fwlink/p/?LinkId=233647)」
    
### <a name="step-6-delete-a-staged-migration-batch"></a>ステップ 6:段階的な移行バッチを削除する
<a name="BK_Endpoint"> </a>

 移行バッチ内のすべてのメールボックスが正常に移行された場合、バッチ内の社内メールボックスをメールが有効なユーザーに変換した後に、段階的な移行バッチを削除する準備が整います。メールが移行バッチ内の Office 365 メールボックスに転送されていることを確認してください。段階的な移行バッチを削除すると、移行サービスによって、移行バッチに関連するすべてのレコードがクリーンアップされて移行バッチが削除されます。
  
Exchange Online PowerShell で "StagedBatch1" 移行バッチを削除するには、次のコマンドを実行します。
  
```
Remove-MigrationBatch -Identity StagedBatch1
```

**Remove-MigrationBatch** コマンドレットの詳細については、「[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)」を参照してください。
  
#### <a name="verify-it-worked"></a>機能していることを確認する

Exchange Online PowerShell で次のコマンドを実行すると、"IMAPBatch1" に関する情報が表示されます。
  
```
Get-MigrationBatch StagedBatch1
```

このコマンドによって、状態が **Removing** の移行バッチが返されるか、移行バッチが見つからず、削除されたことの確認を求めるエラーが返されます。
  
**Get-MigrationBatch** コマンドレットの詳細については、「[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)」を参照してください。
  
### <a name="step7-assign-licenses-to-office-365-users"></a>ステップ 7:Office 365 ユーザーにライセンスを割り当てる
<a name="BK_Endpoint"> </a>

ライセンスを割り当てて、移行されたアカウントの Office 365 のユーザー アカウントをアクティブ化します。ライセンスを割り当てないと、猶予期間 (30 日) が終了したときにメールボックスが無効になります。Office 365 管理センター でライセンスを割り当てるには、「[一般法人向け Office 365 ライセンスの割り当てまたは割り当て解除を行う](https://go.microsoft.com/fwlink/?LinkId=536681)」を参照してください。
  
### <a name="step-8-complete-post-migration-tasks"></a>ステップ 8:移行後のタスクを完了する
<a name="BK_Postmigration"> </a>

- **ユーザーが各自のメールボックスに簡単にアクセスできるように、自動検出 DNS レコードを作成します。**すべての社内メールボックスが Office 365 に移行されたら、Office 365 組織に自動検出レコードを構成して、Outlook クライアントとモバイル クライアントを持つ新しい Office 365 メールボックスにユーザーが簡単に接続できるようにします。この新しい自動検出 DNS レコードは、Office 365 組織に使用しているのと同じ名前空間を使用する必要があります。たとえば、クラウドベースの名前空間が cloud.contoso.com の場合、作成する必要のある自動検出 DNS レコードは autodiscover.cloud.contoso.com となります。
    
    Office 365 は CNAME レコードを使用して、Outlook クライアントとモバイル クライアントのための自動検出サービスを実装します。自動検出 CNAME レコードには以下の情報が含まれている必要があります。
    
  - **エイリアス:** autodiscover
    
  - **ターゲット:** autodiscover.outlook.com
    
    詳細については、「[DNS レコードを管理するときに Office 365 の DNS レコードを作成する](https://go.microsoft.com/fwlink/p/?LinkId=535028)」を参照してください。
    
- **社内の Exchange サーバーの使用を停止します。**すべての電子メールが Office 365 メールボックスに直接ルーティングされていることを確認した後、社内の電子メール組織を維持する必要がもはやないか、SSO ソリューションを実装する予定がない場合は、Exchange をサーバーからアンインストールするとともに、社内の Exchange 組織を削除することができます。
    
    詳細については、以下を参照してください。
    
  - 「[Exchange 2010 の変更または削除](https://go.microsoft.com/fwlink/?LinkId=217936)」
    
  - 「[Exchange 2007 組織を削除する方法](https://go.microsoft.com/fwlink/?LinkID=100485)」
    
  - 「[Exchange Server 2003 をアンインストールする方法](https://go.microsoft.com/fwlink/?LinkID=56561)」
    

