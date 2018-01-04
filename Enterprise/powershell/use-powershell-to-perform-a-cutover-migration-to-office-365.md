---
title: "PowerShell を使用して Office 365 へのカットオーバーの移行を実行する"
ms.author: sirkkuw
author: sirkkuw
manager: scotv
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: "概要:Windows PowerShell を使用して Office 365 の一括移行を実行する方法について説明します。"
ms.openlocfilehash: be5a3587538c32589c20fe6d27d69a84e0b8e7db
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a>PowerShell を使用して Office 365 へのカットオーバーの移行を実行する

 **概要:** Windows PowerShell を使用して Office 365 の一括移行を実行する方法について説明します。
  
一括移行を使用すると、移行元の電子メール システムから Office 365 へユーザーのメールボックスの内容を一度に移行できます。この記事では、Exchange Online PowerShell を使用した電子メールの一括移行の作業を順を追って説明します。 
  
トピック「[Office 365 への一括メール移行について知っておくべきこと](https://go.microsoft.com/fwlink/p/?LinkId=536688)」を確認すると、移行プロセスの概要を把握できます。記事の内容に満足いただけたら、段階的メール移行を使用して、あるメール システムから別のメール システムへのメールボックスの移行を開始してください。
  
> [!NOTE]
> また、一括移行を実行するには、Exchange 管理センターを使用することもできます。「[メールを Office 365 に一括で移行する](https://go.microsoft.com/fwlink/p/?LinkId=536689)」を参照してください。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>始める前に把握しておくべき情報

このタスクの予想所要時間:移行バッチの作成に 2 ～ 5 分。移行バッチ開始後の移行時間は、バッチ内のメールボックスの数、各メールボックスのサイズ、および使用可能なネットワーク容量によって異なります。Office 365 にメールボックスの移行時間を決定するその他の要因の詳細については、「[移行のパフォーマンス](https://go.microsoft.com/fwlink/p/?LinkId=275079)」を参照してください。
  
この手順を実行する際には、あらかじめアクセス許可を割り当てる必要があります。必要なアクセス許可を確認するには、トピック「[受信者のアクセス許可](https://go.microsoft.com/fwlink/p/?LinkId=534105)」内の表にある「移行」エントリを参照してください。
  
Exchange Online PowerShell コマンドレットを使用するには、サインインしてコマンドレットをローカルの Windows PowerShell セッションにインポートする必要があります。手順については、「[リモート PowerShell による Exchange への接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)」を参照してください。
  
移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。
  
## <a name="migration-steps"></a>移行の手順

### <a name="step-1-prepare-for-a-cutover-migration"></a>ステップ 1:一括移行を準備する
<a name="BK_Step1"> </a>

- **社内 Exchange 組織を Office 365 組織の承認済みドメインとして追加する。** 移行サービスは、社内メールボックスの SMTP アドレスを使用して、新しい Office 365 メールボックスに Microsoft Online Services のユーザー ID とメール アドレスを作成します。Exchange ドメインが Office 365 組織の承認済みドメイン (またはプライマリ ドメイン) でない場合は、移行が失敗します。詳細については、「[Office 365 でドメインを確認する](https://go.microsoft.com/fwlink/p/?LinkId=534110)」を参照してください。
    
- **社内 Exchange サーバーで Outlook Anywhere を構成する。** 電子メール移行サービスは、RPC over HTTP または Outlook Anywhere を使用して社内 Exchange サーバーに接続します。Exchange 2010、Exchange 2007、および Exchange 2003 で Outlook Anywhere をセットアップする方法については、以下のトピックを参照してください。
    
  - 「[Exchange 2010:Outlook Anywhere を有効にする](https://go.microsoft.com/fwlink/?LinkID=187249)」
    
  - 「[Exchange 2007:Outlook Anywhere を有効にする方法](https://go.microsoft.com/fwlink/?LinkID=167210)」
    
  - 「[Exchange 2003:RPC over HTTP の展開シナリオ](https://go.microsoft.com/fwlink/?LinkID=73657)」
    
  - 「[Exchange 2003 での Outlook Anywhere を構成する方法](https://go.microsoft.com/fwlink/?LinkID=167209)」
    
    > [!IMPORTANT]
    > Outlook Anywhere の構成は、信頼された証明機関 (CA) により発行された証明書を使用して行う必要があります。自己署名入りの証明書では構成できません。詳細については、「[Outlook Anywhere のために SSL を構成する方法](https://go.microsoft.com/fwlink/?LinkID=80875)」を参照してください。 
  
- **Outlook Anywhere を使用して Exchange 組織に接続できることを確認する。** 次のいずれかの方法で、接続設定をテストしてください:
    
  - 企業ネットワークの外部から Microsoft Outlook を使用して、社内 Exchange メールボックスに接続します。
    
  - Microsoft [Exchange リモート接続アナライザー]((https://www.testexchangeconnectivity.com/))を使用して接続設定をテストします。Outlook Anywhere (RPC over HTTP) または Outlook 自動検出テストを使用します。
    
  - Exchange Online PowerShell で次のコマンドを実行します。
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **Exchange 組織のメールボックスへのアクセスに必要なアクセス許可を社内ユーザー アカウントに割り当てる。** 社内 Exchange 組織への接続に使用する社内ユーザー アカウント (移行管理者とも呼ばれる) には、Office 365 に移行する社内メールボックスへのアクセスに必要なアクセス許可を付与する必要があります。このユーザー アカウントは、社内組織の移行エンドポイントを作成するために使用されます。
    
    以下の一覧に、一括移行を使用してメールボックスを移行するために必要な管理者権限を示します。3 つの可能なオプションがあります。
    
  - 移行管理者は、社内組織の Active Directory の **Domain Admins** グループのメンバーである必要がある。
    
    または
    
  - 移行管理者は、各社内メールボックスへの **フル アクセス**のアクセス許可が割り当てられている必要がある。
    
    または
    
  - 移行管理者は、ユーザーのメールボックスを格納する社内メールボックス データベースへの **受信者**アクセス許可が割り当てられている必要がある。
    
- **ユニファイド メッセージングを無効にする。** 移行する社内メールボックスでユニファイド メッセージング (UM) が有効である場合、メールボックスを移行する前にメールボックスで UM を無効にする必要があります。移行が完了すると、メールボックスで UM を有効にできます。
    
- **セキュリティ グループと委任** メール移行サービスでは、オンプレミスの Active Directory グループがセキュリティ グループであるかどうかを検出できないため、移行したグループをセキュリティ グループとして Office 365 でプロビジョニングすることができません。Office 365 テナント内にセキュリティ グループが必要な場合は、一括移行を開始する前に、あらかじめ Office 365 テナントに、メールが有効な空のセキュリティ グループをプロビジョニングする必要があります。さらに、この移行方法では、メールボックス、メール ユーザー、メール連絡先、およびメールが有効なグループのみを移動します。他の Active Directory オブジェクト (Office 365 に移行されないユーザーなど) を管理者として割り当てるか、または移行対象のオブジェクトに委任してある場合は、移行前にオブジェクトから削除する必要があります。
    
### <a name="step-2-create-a-migration-endpoint"></a>ステップ 2:移行エンドポイントを作成する
<a name="BK_Step2"> </a>

電子メールを正常に移行するためには、Office 365 は移行元の電子メール システムと接続して通信する必要があります。これを実行するため、Office 365 では移行エンドポイントを使用します。一括移行用に Outlook Anywhere の移行エンドポイントを作成するには、最初に [リモート PowerShell による Exchange への接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)を行います。 
  
移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。
  
Exchange Online PowerShell で次のコマンドを実行します。
  
```
$Credentials = Get-Credential
```

この例では、[Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) コマンドレットを使用して、社内の Exchange サーバーへの接続設定を取得およびテストしてから、この接続設定を使用して "CutoverEndpoint" という移行エンドポイントを作成します。
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> **New-MigrationEndpoint** コマンドレットで **-TargetDatabase** オプションを使用することによって、使用するサービスに対してデータベースを指定することができます。それ以外の場合、データベースは、管理メールボックスが配置されている Active Directory フェデレーション サービス (AD FS) 2.0 サイトからランダムに割り当てられます。
  
#### <a name="verify-it-worked"></a>機能していることを確認する

Exchange Online PowerShell で、次のコマンドを実行して "CutoverEndpoint" 移行エンドポイントに関する情報を表示します。
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>ステップ 3:一括移行バッチを作成する
<a name="BK_Step3"> </a>

Exchange Online PowerShell の **New-MigrationBatch** コマンドレットを使用すると、一括移行の移行バッチを作成できます。 _AutoStart_ パラメーターを含めると、移行バッチを作成して自動的に開始できます。また、別の方法として、 **Start-MigrationBatch** コマンドレットを使用することにより、移行バッチを作成して後で手動で開始できます。この例では、"CutoverBatch" という移行バッチを作成して、前の例で作成した移行エンドポイントを使用します。
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

この例でも、"CutoverBatch" という移行バッチを作成して、前の例で作成した移行エンドポイントを使用します。 _AutoStart_ パラメーターが含まれていないため、移行バッチは移行ダッシュボードで、または **Start-MigrationBatch** コマンドレットを使用して手動で開始する必要があります。前述のように、一度に存在できる一括移行バッチは 1 つだけです。
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>機能していることを確認する

一括移行用の移行バッチが正常に作成されたことを確認するには、Exchange Online PowerShell で次のコマンドを実行して、新しい移行バッチに関する情報を表示します。
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>ステップ 4:一括移行バッチを開始する
<a name="BK_Step4"> </a>

Exchange Online PowerShell で移行バッチを開始するには、次のコマンドを実行します。そうすると、"CutoverBatch" という移行バッチが作成されます。
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>機能していることを確認する

移行バッチが正常に開始されると、移行ダッシュボードのバッチの状態は「同期中」になります。Exchange Online PowerShell を使用して移行バッチが正常に開始したことを確認するには、次のコマンドを実行します。
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a>ステップ 5:電子メールを Office 365 にルーティングします。
<a name="BK_Step5"> </a>

電子メール システムは、MX レコードという DNS レコードを使用して、電子メールの配信先を見つけ出します。電子メールの移行プロセス中、MX レコードの宛先は移行元の電子メール システムでした。Office 365 への電子メール移行が完了したので、今度は MX レコードの宛先は Office 365 になります。 これにより、電子メールは Office 365 のメールボックスに確実に配信されます。MX レコードを移動することによって、準備ができたら古い電子メール システムをオフにすることもできます。 
  
多くの DNS プロバイダー向けに、[MX レコードの変更](https://go.microsoft.com/fwlink/p/?LinkId=279163)の具体的な説明があります。DNS プロバイダーが含まれていない場合や、全般的な方向を把握したい場合は、「[任意の DNS ホスティング プロバイダーで Office 365 用の DNS レコードを作成する](https://go.microsoft.com/fwlink/?LinkId=397449)」も用意されています。
  
御社のお客様およびパートナーの電子メール システムが MX レコードの変更を認識するまでに最大 72 時間かかることがあります。次の作業に進むまで、72 時間以上待ちます。 [ステップ 6:一括移行バッチを削除する](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6). 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a>ステップ 6:一括移行バッチを削除する
<a name="Bk_step6"> </a>

MX レコードを変更して、すべての電子メールが Office 365 にルーティングされていることを確認したら、ユーザーのメールが Office 365 に移動することをユーザーに通知します。その後、一括移行バッチを削除できます。移行バッチを削除する前に、次の点を確認します。
  
- すべてのユーザーが Office 365 メールボックスを使用している。バッチを削除した後は、社内 Exchange サーバー上のメールボックスに送信されるメールが、対応する Office 365 メールボックスにコピーされません。
    
- Office 365 のメールボックスが、メールが直接送信され始めてから 1 回以上同期した。これを行うには、移行バッチの [最終同期時刻] ボックスの値が、メールが Office 365 のメールボックスに直接ルーティングされ始めた時より後の時間であることを確認します。
    
Exchange Online PowerShell で "CutoverBatch" 移行バッチを削除するには、次のコマンドを実行します。
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>セクション 7:ユーザー ライセンスの割り当て
<a name="BK_Step7"> </a>

 **ライセンスを割り当てて、移行されたアカウントの Office 365 のユーザー アカウントをアクティブ化します。**ライセンスを割り当てないと、猶予期間が終了したとき (30 日) にメールボックスが無効になります。Office 365 管理センター でライセンスを割り当てるには、「[一般法人向け Office 365 ライセンスの割り当てまたは割り当て解除を行う](https://go.microsoft.com/fwlink/?LinkId=536681)」を参照してください。
  
### <a name="step-8-complete-post-migration-tasks"></a>ステップ 8:移行後のタスクを完了する
<a name="BK_Step8"> </a>

- **ユーザーが各自のメールボックスに簡単にアクセスできるように、自動検出 DNS レコードを作成します。**すべての社内メールボックスが Office 365 に移行されたら、Office 365 組織に自動検出レコードを構成して、Outlook クライアントとモバイル クライアントを持つ新しい Office 365 メールボックスにユーザーが簡単に接続できるようにします。この新しい自動検出 DNS レコードは、Office 365 組織に使用しているのと同じ名前空間を使用する必要があります。たとえば、クラウドベースの名前空間が cloud.contoso.com の場合、作成する必要のある自動検出 DNS レコードは autodiscover.cloud.contoso.com となります。
    
    Exchange Server を残す場合は、移行後に内部および外部 DNS の両方で自動検出 DNS CNAME レコードが Office 365 を指すようにして、Outlook クライアントが適切なメールボックスに接続するようにします。
    
    > [!NOTE]
    >  Exchange 2007、Exchange 2010、および Exchange 2013 では、 `Set-ClientAccessServer AutodiscoverInternalConnectionURI` を `Null` に設定する必要もあります。 
  
    Office 365 は CNAME レコードを使用して、Outlook クライアントとモバイル クライアントのための自動検出サービスを実装します。自動検出 CNAME レコードには以下の情報が含まれている必要があります。
    
  - **エイリアス:** autodiscover
    
  - **ターゲット:** autodiscover.outlook.com
    
    詳細については、「[DNS レコードを管理するときに Office 365 の DNS レコードを作成する](https://go.microsoft.com/fwlink/p/?LinkId=535028)」を参照してください。
    
- **社内の Exchange サーバーの使用を停止します。**すべての電子メールが Office 365 メールボックスに直接ルーティングされていることを確認した後、社内の電子メール組織を維持する必要がもはやないか、シングル サインオン (SSO) ソリューションを実装する予定がない場合は、Exchange をサーバーからアンインストールするとともに、社内の Exchange 組織を削除することができます。
    
    詳細については、以下を参照してください。
    
  - 「[Exchange 2010 の変更または削除](https://go.microsoft.com/fwlink/?LinkId=217936)」
    
  - 「[Exchange 2007 組織を削除する方法](https://go.microsoft.com/fwlink/?LinkID=100485)」
    
  - 「[Exchange Server 2003 をアンインストールする方法](https://go.microsoft.com/fwlink/?LinkID=56561)」
    

