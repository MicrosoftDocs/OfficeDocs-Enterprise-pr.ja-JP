---
title: Microsoft 365 への段階的な移行に PowerShell を使用する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: PowerShell を使用して、Microsoft 365 への段階的な移行を使用して、時間の経過と共にソース電子メールシステムからコンテンツを移動する方法について説明します。
ms.openlocfilehash: a50966f65bbec5e4b453c4caf02e4b89fa7d04b5
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606213"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a>Microsoft 365 への段階的な移行に PowerShell を使用する

*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*

段階的な移行を使用して、ユーザーメールボックスのコンテンツをソースメールシステムから Microsoft 365 に移行することができます。
  
この記事では、Exchange Online PowerShell を使用した段階的なメール移行に関連するタスクについて説明します。このトピックでは、[段階的なメールの移行について理解しておく必要がある](https://go.microsoft.com/fwlink/p/?LinkId=536487)ことを、移行プロセスの概要を示します。この記事の内容に慣れてきたら、この記事を使用してメールボックスを1つのメールシステムから別のメールシステムに移行する作業を開始します。
  
> [!NOTE]
> Exchange 管理センターを使用して、段階的な移行を実行することもできます。「 [Microsoft 365 へのメールの段階的な移行を実行する」を](https://go.microsoft.com/fwlink/p/?LinkId=536687)参照してください。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>始める前に把握しておくべき情報

このタスクの予想所要時間: 2-5 分、移行バッチを作成します。移行バッチの開始後、移行の期間は、バッチ内のメールボックスの数、各メールボックスのサイズ、および使用可能なネットワーク容量によって異なります。メールボックスを Microsoft 365 に移行するのにかかる時間に影響を与えるその他の要因の詳細については、「 [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079)」を参照してください。
  
この手順を実行する際には、あらかじめアクセス許可を割り当てる必要があります。必要なアクセス許可を確認するには、トピック「[受信者のアクセス許可](https://go.microsoft.com/fwlink/p/?LinkId=534105)」の中の「移行」エントリを参照してください。
  
Exchange Online PowerShell コマンドレットを使用するには、サインインしてコマンドレットをローカルの Windows PowerShell セッションにインポートする必要があります。手順については、「[リモート PowerShell による Exchange への接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)」を参照してください。
  
移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。
  
## <a name="migration-steps"></a>移行の手順

### <a name="step-1-prepare-for-a-staged-migration"></a>ステップ 1:段階的な移行を準備する

段階的な移行を使用してメールボックスを Microsoft 365 に移行する前に、Exchange 環境にいくつかの変更を加える必要があります。
  
 **社内の Exchange Server** に Outlook Anywhere を構成する: メール移行サービスは、Outlook Anywhere (RPC over HTTP としても知られる) を使用して社内の Exchange Server に接続します。Exchange Server 2007 と Exchange 2003 における Outlook Anywhere の設定方法の詳細については、以下を参照してください。
  
- 「[Exchange 2007:Outlook Anywhere を有効にする方法](https://go.microsoft.com/fwlink/?LinkID=167210)」
    
- 「[Exchange 2003 での Outlook Anywhere を構成する方法](https://go.microsoft.com/fwlink/?LinkID=167209)」
    
> [!IMPORTANT]
> Outlook Anywhere の構成には、信頼された証明機関 (CA) によって発行された証明書を使用する必要があります。Outlook Anywhere は、自己署名入りの証明書で構成することはできません。詳細については、「[Outlook Anywhere のために SSL を構成する方法](https://go.microsoft.com/fwlink/?LinkID=80875)」を参照してください。 
  
 **オプション:Outlook Anywhere**を使用して Exchange 組織に接続できることを確認する: 接続設定をテストするには、次のいずれかの方法を試します。
  
- 企業ネットワークの外部から Outlook を使用して社内の Exchange メールボックスに接続します。
    
- [Microsoft リモート接続アナライザー](https://https://testconnectivity.microsoft.com/)を使用して、接続設定をテストします。Outlook Anywhere (RPC over HTTP) または Outlook 自動検出テストを使用します。
    
- Exchange Online PowerShell で次のコマンドを実行します。
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **アクセス許可を設定**するオンプレミスの Exchange 組織 (移行管理者とも呼ばれます) に接続するために使用するオンプレミスのユーザーアカウントは、Microsoft 365 に移行する必要があるオンプレミスのメールボックスにアクセスするために必要なアクセス許可を持っている必要があります。このユーザーアカウントは、この手順の後半で移行エンドポイントを作成することによってメールシステムに接続するときに使用されます ([手順 3: 移行エンドポイントを作成](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint)します)。
  
メールボックスを移行するために、管理者には次のアクセス許可セットのいずれかが必要です。
  
- 社内組織の Active Directory の **Domain Admins** グループのメンバーであること。
    
    or
    
- 社内の各メールボックスに **FullAccess** のアクセス許可が割り当てられ、社内のユーザー アカウントの **TargetAddress** プロパティを変更するための **WriteProperty** のアクセス許可が割り当てられていること。
    
    or
    
- ユーザー メールボックスを格納する社内のメールボックス データベースに **受信者** のアクセス許可が割り当てられ、社内のユーザー アカウントの **TargetAddress** プロパティを変更するための **WriteProperty** のアクセス許可が割り当てられていること。
    
これらのアクセス許可を設定する方法については、「[メールボックスを Microsoft 365 に移行するためのアクセス許可を割り当てる](https://go.microsoft.com/fwlink/?LinkId=521656)」を参照してください。
  
 **ユニファイド メッセージング (UM) を無効にする**: 移行する社内のメールボックスで UM がオンになっている場合は、移行前に UM をオフにします。移行の完了後に、メールボックスの UM をオンにします。操作手順については、「[ユーザーのユニファイド メッセージングを無効にする方法](https://go.microsoft.com/fwlink/?LinkId=521891)」を参照してください。
  
 **ディレクトリ同期を使用して、Microsoft 365 で新しいユーザーを作成します。** ディレクトリ同期を使用して、Microsoft 365 組織のすべてのオンプレミスユーザーを作成します。
  
ユーザーの作成後にライセンスを付与する必要があります。ユーザーの作成後、ライセンスを追加するまでに 30 日間があります。ライセンスを追加する手順については、「[ステップ 8:移行後のタスクを完了する](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration)」を参照してください。
  
 Microsoft Azure Active Directory (Azure AD) 同期ツールまたは Microsoft Azure AD 同期サービスのいずれかを使用して、Microsoft 365 でオンプレミスユーザーを同期および作成できます。メールボックスを Microsoft 365 に移行した後は、社内組織のユーザーアカウントを管理し、Microsoft 365 組織と同期されます。詳細については、「[ディレクトリ統合](https://go.microsoft.com/fwlink/?LinkId=521788)」を参照してください。
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>ステップ 2:段階的な移行バッチ用の CSV ファイルを作成する

Microsoft 365 に移行する社内メールボックスのユーザーを特定した後、コンマ区切り値 (CSV) ファイルを使用して移行バッチを作成します。CSV ファイルの各行 (Microsoft 365 で移行を実行するために使用されます) には、社内メールボックスに関する情報が含まれています。 
  
> [!NOTE]
> 段階的な移行を使用して Microsoft 365 に移行できるメールボックスの数に制限はありません。移行バッチの CSV ファイルには、最大2000行を含めることができます。2000を超えるメールボックスを移行するには、追加の CSV ファイルを作成し、各ファイルを使用して新しい移行バッチを作成します。 
  
 **サポートされている属性**
  
段階的な移行用の CSV ファイルは、次の 3 つの属性をサポートします。CSV ファイルの各行はメールボックスに対応し、各属性の値を含める必要があります。
  
|**属性**|**説明**|**必須**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |プライマリ SMTP 電子メール アドレス (たとえば、社内メールボックスの場合は pilarp@contoso.com など) を指定します。  <br/> Microsoft 365 のユーザー Id ではなく、オンプレミスのメールボックスのプライマリ SMTP アドレスを使用します。たとえば、オンプレミスのドメインが contoso.com という名前で、Microsoft 365 の電子メールドメインが service.contoso.com という名前の場合は、CSV ファイルの電子メールアドレスに contoso.com ドメイン名を使用します。  <br/> |必須  <br/> |
|Password  <br/> |新しい Microsoft 365 メールボックスに設定するパスワードを指定します。Microsoft 365 組織に適用されるパスワード制限は、CSV ファイルに含まれるパスワードにも適用されます。  <br/> |省略可能  <br/> |
|ForceChangePassword  <br/> |ユーザーが新しい Microsoft 365 メールボックスに初めてサインインするときにパスワードを変更する必要があるかどうかを指定します。このパラメーターの値には、 **True**または**False**を使用します。<br/> > [!NOTE]> Active Directory フェデレーション サービス (AD FS) 以上を社内組織に展開してシングル サインオン (SSO) ソリューションを実装した場合、 **ForceChangePassword** 属性の値には **False** を使用する必要があります。          |省略可能  <br/> |
   
 **CSV ファイル形式**
  
CSV ファイルの形式の例を次に示します。この例では、3つのオンプレミスメールボックスが Microsoft 365 に移行されます。
  
CSV ファイルの最初の行、つまりヘッダー行には、後続の行で指定される属性 (つまり、フィールド) の名前が示されます。各属性名はコンマで区切られます。
  
```powershell
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

電子メールを正常に移行するには、Microsoft 365 が接続して、ソースメールシステムと通信する必要があります。これを行うために、Microsoft 365 では移行エンドポイントを使用しています。PowerShell を使用して Outlook Anywhere 移行エンドポイントを作成するには、段階的な移行では、最初[に Exchange Online に接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)します。 
  
移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。
  
Exchange Online PowerShell に "StagedEndpoint" という Outlook Anywhere 移行エンドポイントを作成するには、次のコマンドを実行します。
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

**New-MigrationEndpoint** コマンドレットの詳細については、「[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)」を参照してください。
  
> [!NOTE]
> **New-MigrationEndpoint** コマンドレットで **-TargetDatabase** オプションを使用することによって、使用するサービスに対してデータベースを指定することができます。それ以外の場合、データベースは、管理メールボックスが配置されている Active Directory フェデレーション サービス (AD FS) 2.0 サイトからランダムに割り当てられます。
  
#### <a name="verify-it-worked"></a>機能していることを確認する

Exchange Online PowerShell で、次のコマンドを実行して "StagedEndpoint" 移行エンドポイントに関する情報を表示します。
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>ステップ 4:段階的な移行のバッチを作成および開始する
<a name="BK_Endpoint"> </a>

Exchange Online PowerShell の **New-MigrationBatch** コマンドレットを使用すると、一括移行の移行バッチを作成できます。 _AutoStart_ パラメーターを含めると、移行バッチを作成して自動的に開始できます。また、別の方法として、 **Start-MigrationBatch** コマンドレットを使用することにより、移行バッチを作成して後で手動で開始できます。この例では、"StagedBatch1" という移行バッチを作成して、前の例で作成した移行エンドポイントを使用します。
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

この例でも、"StagedBatch1" という移行バッチを作成して、前の例で作成した移行エンドポイントを使用します。 _AutoStart_ パラメーターが含まれていないため、移行バッチは移行ダッシュボードで、または **Start-MigrationBatch** コマンドレットを使用して手動で開始する必要があります。前述のように、一度に存在できる一括移行バッチは 1 つだけです。
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>機能していることを確認する

Exchange Online PowerShell で次のコマンドを実行すると、「StagedBatch1」に関する情報が表示されます。
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

また、次のコマンドを実行すると、バッチが開始されたことを確認できます。
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

**Get-MigrationBatch** コマンドレットの詳細については、「[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)」を参照してください。
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>ステップ 5:社内メールボックスをメールが有効なユーザーに変換する
<a name="BK_Endpoint"> </a>

メールボックスのバッチを正常に移行したら、ユーザーがメールにアクセスできるようにする何らかの方法が必要になります。メールボックスが移行されたユーザーには、オンプレミスのメールボックスと Microsoft 365 の両方があります。Microsoft 365 のメールボックスを持つユーザーは、オンプレミスのメールボックスで新着メールの受信を停止します。 
  
移行が完了していないため、すべてのユーザーに電子メールの Microsoft 365 を送信する準備ができていません。そのため、両方を持つユーザーに対して何を行うのでしょうか。メールが有効なユーザーに移行済みの社内メールボックスを変更することができます。メールボックスをメールが有効なユーザーに変更する場合は、オンプレミスのメールボックスに移動するのではなく、電子メールに対して Microsoft 365 をユーザーに指示することができます。 
  
オンプレミスのメールボックスをメールが有効なユーザーに変換するもう1つの重要な理由は、プロキシアドレスをメールが有効なユーザーにコピーすることによって、Microsoft 365 メールボックスからのプロキシアドレスを保持することです。これにより、Active Directory を使用してオンプレミスの組織からクラウドベースのユーザーを管理することができます。また、すべてのメールボックスを Microsoft 365 に移行した後に、オンプレミスの Exchange Server 組織を使用停止にした場合、メールが有効なユーザーにコピーしたプロキシアドレスは、オンプレミスの Active Directory に残ります。
    
### <a name="step-6-delete-a-staged-migration-batch"></a>ステップ 6:段階的な移行バッチを削除する
<a name="BK_Endpoint"> </a>

 移行バッチ内のすべてのメールボックスが正常に移行された場合、バッチ内の社内メールボックスをメールが有効なユーザーに変換した後に、段階的な移行バッチを削除する準備が整います。 メールが移行バッチ内の Microsoft 365 メールボックスに転送されていることを確認してください。 段階的な移行バッチを削除すると、移行サービスによって、移行バッチに関連するすべてのレコードがクリーンアップされて移行バッチが削除されます。
  
Exchange Online PowerShell で "StagedBatch1" 移行バッチを削除するには、次のコマンドを実行します。
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

**Remove-MigrationBatch** コマンドレットの詳細については、「[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)」を参照してください。
  
#### <a name="verify-it-worked"></a>機能していることを確認する

Exchange Online PowerShell で次のコマンドを実行すると、"IMAPBatch1" に関する情報が表示されます。
  
```powershell
Get-MigrationBatch StagedBatch1
```

このコマンドによって、状態が **Removing** の移行バッチが返されるか、移行バッチが見つからず、削除されたことの確認を求めるエラーが返されます。
  
**Get-MigrationBatch** コマンドレットの詳細については、「[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)」を参照してください。
  
### <a name="step7-assign-licenses-to-microsoft-365-users"></a>Step7: Microsoft 365 ユーザーにライセンスを割り当てる
<a name="BK_Endpoint"> </a>

ライセンスを割り当てることにより、移行されたアカウントの Microsoft 365 ユーザーアカウントをアクティブ化します。 ライセンスを割り当てないと、猶予期間 (30 日) が終了したときにメールボックスが無効になります。 Microsoft 365 管理センターでライセンスを割り当てるには、「[ライセンスの割り当てまたは割り当て解除](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)」を参照してください。
  
### <a name="step-8-complete-post-migration-tasks"></a>ステップ 8:移行後のタスクを完了する
<a name="BK_Postmigration"> </a>

- **ユーザーが各自のメールボックスに簡単にアクセスできるように、自動検出 DNS レコードを作成します。** すべてのオンプレミスメールボックスが Microsoft 365 に移行された後、Microsoft 365 組織の自動検出 DNS レコードを構成して、ユーザーが Outlook およびモバイルクライアントを使用して新しい Microsoft 365 メールボックスに簡単に接続できるようにすることができます。 この新しい自動検出 DNS レコードは、Microsoft 365 組織に使用しているのと同じ名前空間を使用する必要があります。 たとえば、クラウドベースの名前空間が cloud.contoso.com の場合、作成する必要のある自動検出 DNS レコードは autodiscover.cloud.contoso.com となります。
    
    Microsoft 365 では CNAME レコードを使用して、Outlook およびモバイルクライアントの自動検出サービスを実装しています。 自動検出 CNAME レコードには以下の情報が含まれている必要があります。
    
  - **エイリアス:** autodiscover
    
  - **ターゲット:** autodiscover.outlook.com
    
    詳細については、「[ドメインを接続するための DNS レコードを追加する](https://go.microsoft.com/fwlink/p/?LinkId=535028)」を参照してください。
    
- **社内の Exchange サーバーの使用を停止します。** すべての電子メールが Microsoft 365 メールボックスに直接ルーティングされていることを確認し、オンプレミスの電子メール組織を管理する必要がなくなったか、SSO ソリューションの実装を計画していない場合は、サーバーから Exchange をアンインストールし、オンプレミスの Exchange 組織を削除することができます。
    
    詳細については、以下を参照してください。
    
  - 「[Exchange 2010 の変更または削除](https://go.microsoft.com/fwlink/?LinkId=217936)」
    
  - 「[Exchange 2007 組織を削除する方法](https://go.microsoft.com/fwlink/?LinkID=100485)」
    
  - 「[Exchange Server 2003 をアンインストールする方法](https://go.microsoft.com/fwlink/?LinkID=56561)」
    

