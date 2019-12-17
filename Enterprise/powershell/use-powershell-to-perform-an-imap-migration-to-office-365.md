---
title: PowerShell を使用した Office 365 への IMAP 移行の実行
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: 概要:Windows PowerShell を使用して Office 365 の IMAP 移行を実行する方法について説明します。
ms.openlocfilehash: 411c60f78284c4d7405cd0a1b1d737f99155c1d3
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072469"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-office-365"></a>PowerShell を使用した Office 365 への IMAP 移行の実行

Office 365 を展開するプロセスの一部として、Internet Mail Access Protocol (IMAP) 電子メール サービスから Office 365 に、ユーザーのメールボックスの内容を移行することができます。この記事では、Exchange Online PowerShell を使用した電子メールの IMAP 移行作業を順を追って説明します。 
  
> [!NOTE]
> また、IMAP 移行を実行するには、Exchange 管理センターを使用することもできます。「[IMAP メールボックスを Office 365 に移行する](https://go.microsoft.com/fwlink/p/?LinkId=536685)」を参照してください。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>始める前に把握しておくべき情報

このタスクの予想所要時間:移行バッチの作成に 2 ～ 5 分。移行バッチ開始後の移行時間は、バッチ内のメールボックスの数、各メールボックスのサイズ、および使用可能なネットワーク容量によって異なります。Office 365 にメールボックスの移行時間を決定するその他の要因の詳細については、「[移行のパフォーマンス](https://go.microsoft.com/fwlink/p/?LinkId=275079)」を参照してください。
  
この手順を実行する際には、あらかじめアクセス許可を割り当てる必要があります。必要なアクセス許可を確認するには、トピック「[受信者のアクセス許可](https://go.microsoft.com/fwlink/p/?LinkId=534105)」内の表にある「移行」エントリを参照してください。
  
Exchange Online PowerShell コマンドレットを使用するには、サインインしてコマンドレットをローカルの Windows PowerShell セッションにインポートする必要があります。手順については、「[リモート PowerShell による Exchange への接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)」を参照してください。
  
移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。
  
IMAP の移行には次の制限が適用されます。
  
- ユーザーの受信トレイまたは他のメール フォルダー内のアイテムのみ、移行できます。連絡先、予定表アイテム、またはタスクを移行することはできません。
    
- 最大で 500,000 アイテムをユーザーのメールボックスから移行できます。
    
- 移行できるメッセージの最大サイズは 35 MB です。
    
## <a name="migration-steps"></a>移行の手順

### <a name="step-1-prepare-for-an-imap-migration"></a>ステップ 1:IMAP 移行を準備する
<a name="BK_Step1"> </a>

- **IMAP 組織のドメインをお持ちの場合は、Office 365 組織の承認済みドメインとして追加します。** Office 365 のメールボックス用に既に所有している同じドメインを使用する場合は、最初にこのドメインを承認済みドメインとして Office 365 に追加する必要があります。追加したら、Office 365 でユーザーを作成できます。詳細については、「[Office 365 でドメインを確認する](https://go.microsoft.com/fwlink/p/?LinkId=534110)」を参照してください。
    
- **各ユーザーを Office 365 に追加します。そうすることで、ユーザーは Office 365 メールボックスを持つことができます。** 手順については、「[一般法人向け Office 365 にユーザーを追加する](https://go.microsoft.com/fwlink/p/?LinkId=535065)」を参照してください。
    
- **IMAP サーバーの FQDN を取得します**。IMAP 移行エンドポイントを作成するときに、メールボックス データの移行元の IMAP サーバーの完全修飾ドメイン名 (FQDN) (フル コンピューター名ともいう) を指定する必要があります。IMAP クライアントまたは PING コマンドを使用して、インターネット経由での FQDN サーバーとの通信に FQDN を使用できることを確認します。
    
- **IMAP 接続を許可するファイアウォールを構成します**。IMAP サーバーをホストする組織のファイアウォールでポートを開く必要があります。そうすることで、移行中 Microsoft データセンターから発信するネットワーク トラフィックが IMAP サーバーをホストする組織に入ることができます。Microsoft データセンターが使用する IP アドレスの一覧については、「[Office 365 の URL と IP アドレスの範囲](https://go.microsoft.com/fwlink/p/?LinkId=535066)」を参照してください。
    
- **IMAP 組織内のメールボックスにアクセスする管理者アカウントのアクセス許可を割り当てます**。CSV ファイルで管理者の資格情報を使用する場合は、使用するアカウントに、社内メールボックスへのアクセスに必要なアクセス許可が必要になります。ユーザーのメールボックスへのアクセスに必要なアクセス許可は、特定の IMAP サーバーによって決定されます。 
    
- **Exchange Online PowerShell コマンドレットを使用するには**、サインインしてコマンドレットをローカルの Windows PowerShell セッションにインポートする必要があります。手順については、「[リモート PowerShell による Exchange への接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)」を参照してください。
    
    移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。
    
- **IMAP サーバーに接続できることを確認します**。IMAP サーバーへの接続設定をテストするには、Exchange Online PowerShell で次のコマンドを実行します。
    
  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    **Port** パラメーターの値については、通常、暗号化されていない接続やトランスポート層セキュリティ (TLS) 接続には 143 を使用し、SSL 接続には 993 を使用します。
    
### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a>ステップ 2:IMAP 移行バッチ用の CSV ファイルを作成する
<a name="BK_Step2"> </a>

IMAP 移行バッチでそのメールボックスを移行するユーザーのグループを特定します。CSV ファイルの各行には、IMAP メッセージング システム内のメールボックスに接続するために必要な情報が含まれています。
  
各ユーザーの必須属性は次のとおりです。 
  
- **EmailAddress** ユーザーの Office 365 メールボックスのユーザー ID を指定します。
    
- **UserName** は、IMAP サーバー上のメールボックスへのアクセスに使用するアカウントのログオン名を指定します。
    
- **Password** は、 **UserName** 列のアカウントのパスワードを指定します。
    
以下に、CSV ファイルの形式の例を示します。この例では、3 人のメールボックスが移行されます。
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

**UserName** 属性については、ユーザー名に加えて、IMAP サーバーのメールボックスへのアクセスに必要なアクセス許可が割り当てられているアカウントの資格情報を使用できます。以下はいくつかの IMAP サーバーで使用されている特定の形式の一部です。
  
 **Microsoft Exchange:**
  
Microsoft Exchange の IMAP 実装から電子メールを移行する場合、CSV ファイルでは **UserName** 属性に **Domain/Admin_UserName/User_UserName** という形式を使用します。Terry Adams、Ann Beebe、および Paul Cannon の電子メールを Exchange から移行するとします。メールの管理者アカウントは、ユーザー名は **mailadmin** 、パスワードは **P@ssw0rd** とします。CSV ファイルは次のようになります。
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 **Dovecot:**
  
Simple Authentication and Security Layer (SASL) をサポートしている IMAP サーバー (Dovecot IMAP サーバーなど) では、**User_UserName*Admin_UserName** の形式を使用します。ここで、アスタリスク (*) は、構成可能な区切り文字です。たとえば、管理者の資格情報 ( **mailadmin** と **P@ssw0rd** ) を使用して、上記の同じユーザーの電子メールを Dovecot IMAP サーバーから移行するとします。CSV ファイルは次のようになります。
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 **Mirapoint:**
  
Mirapoint Message Server から電子メールを移行する場合は、管理者の資格情報に **#user@domain#Admin_UserName#** の形式を使用します。管理者の資格情報である **mailadmin** と **P@ssw0rd** を使用して Mirapoint から電子メールを移行する場合、CSV ファイルは次のようになります。
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 **Courier IMAP:**
  
Courier IMAP のような一部の移行元の電子メール システムでは、Office 365 にメールボックスを移行するためにメールボックスの管理者の資格情報を使用することをサポートしていません。代わりに、仮想共有フォルダーを使用するように移行元の電子メール システムを設定することができます。仮想共有フォルダーを使用すると、移行元の電子メール システムのユーザーのメールボックスにアクセスするためにメールボックスの管理資格情報を使用できます。Courier IMAP の仮想共有フォルダーを構成する方法の詳細については、「[共有フォルダー](https://go.microsoft.com/fwlink/p/?LinkId=398870)」を参照してください。
  
移行元の電子メール システムで仮想共有フォルダーをセットアップしてからメールボックスを移行するには、オプション属性 **UserRoot** を移行ファイルに含める必要があります。この属性では、移行元電子メール システムの仮想共有フォルダー構造にある各ユーザーのメールボックスの場所を指定します。たとえば、Terry のメールボックスへのパスは /users/terry.adams です。
  
以下に、 **UserRoot** 属性を含む CSV ファイルの例を示します。
  
```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a>ステップ 3:IMAP 移行エンドポイントを作成する
<a name="BK_Step3"> </a>

電子メールを正常に移行するためには、Office 365 は移行元の電子メール システムと接続して通信する必要があります。これを行うため、Office 365 では移行エンドポイントを使用します。移行エンドポイントは、同時に移行するメールボックスの数、および 24 時間ごとに 1 回行われる増分同期中に同時に同期するメールボックスの数も定義します。IMAP 移行用に移行エンドポイントを作成するには、最初に[リモート PowerShell による Exchange への接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)を行います。 
  
移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。
  
Exchange Online PowerShell で "IMAPEndpoint" という IMAP 移行エンドポイントを作成するには、次のコマンドを実行します。
  
```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

また、同時移行、増分の同時移行、および使用するポートを指定するパラメーターを追加することもできます。次の Exchange Online PowerShell コマンドは、50 の同時移行と最大 25 の同時増分同期をサポートする "IMAPEndpoint" という IMAP 移行エンドポイントを作成します。さらに、このエンドポイントを TLS 暗号化用にポート 143 を使用するように構成します。
  
```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

**New-MigrationEndpoint** コマンドレットの詳細については、「[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)」を参照してください。
  
#### <a name="verify-it-worked"></a>機能していることを確認する

Exchange Online PowerShell で次のコマンドを実行すると、"IMAPEndpoint" に関する情報が表示されます。
  
```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a>ステップ 4:IMAP 移行バッチを作成および開始する
<a name="BK_Step4"> </a>

[New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) コマンドレットを使用すると、IMAP 移行用の移行バッチを作成できます。 _AutoStart_ パラメーターを含めると、移行バッチを作成して自動的に開始できます。代わりに、移行バッチを作成してから、後で[Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440) コマンドレットを使用して開始することができます。
  
次の Exchange Online PowerShell コマンドは、"IMAPEndpoint" という IMAP エンドポイントを使用して "IMAPBatch1" という移行バッチを自動的に開始します。
  
```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a>機能していることを確認する

[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) コマンドレットを実行すると、"IMAPBatch1" に関する情報を表示できます。
  
```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

また、次のコマンドを実行すると、バッチが開始されたことを確認できます。
  
```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a>ステップ 5:電子メールを Office 365 にルーティングします。
<a name="BK_Step5"> </a>

電子メール システムは、MX レコードという DNS レコードを使用して、電子メールの配信先を見つけ出します。電子メールの移行プロセス中、MX レコードの宛先は移行元の電子メール システムでした。Office 365 への電子メール移行が完了したので、今度は MX レコードの宛先は Office 365 になります。 これにより、電子メールは Office 365 のメールボックスに確実に配信されます。MX レコードを移動することによって、準備ができたら古い電子メール システムをオフにすることもできます。 
  
多くの DNS プロバイダー向けに、MX レコードの変更の具体的な説明があります。 DNS プロバイダーが含まれていない場合や、全般的な方向を把握したい場合は、「[任意の DNS ホスティング プロバイダーで Office 365 用の DNS レコードを作成する](https://go.microsoft.com/fwlink/?LinkId=397449)」も用意されています。
  
御社のお客様およびパートナーの電子メール システムが MX レコードの変更を認識するまでに最大 72 時間かかることがあります。次の作業に進むまで、72 時間以上待ちます。手順 6: IMAP 移行バッチを削除する。 
  
### <a name="step-6-delete-imap-migration-batch"></a>ステップ 6:IMAP 移行バッチを削除する
<a name="BK_Step6"> </a>

MX レコードを変更して、すべての電子メールが Office 365 のメールボックスにルーティングされていることを確認したら、ユーザーのメールが Office 365 に移動することをユーザーに通知します。その後、IMAP 移行バッチを削除できます。移行バッチを削除する前に、次の点を確認します。
  
- すべてのユーザーが Office 365 メールボックスを使用している。バッチを削除した後は、社内 Exchange サーバー上のメールボックスに送信されるメールが、対応する Office 365 メールボックスにコピーされません。
    
- Office 365 のメールボックスが、メールが直接送信され始めてから 1 回以上同期した。これを行うには、移行バッチの [最終同期時刻] ボックスの値が、メールが Office 365 のメールボックスに直接ルーティングされ始めた時より後の時間であることを確認します。
    
Exchange Online PowerShell から "IMAPBatch1" 移行バッチを削除するには、次のコマンドを実行します。
  
```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

**Remove-MigrationBatch** コマンドレットの詳細については、「[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)」を参照してください。
  
#### <a name="verify-it-worked"></a>機能していることを確認する

Exchange Online PowerShell で次のコマンドを実行すると、"IMAPBatch1" に関する情報が表示されます。
  
```powershell
Get-MigrationBatch IMAPBatch1"
```

このコマンドによって、状態が **Removing** の移行バッチが返されるか、移行バッチが見つからず、削除されたことの確認を求めるエラーが返されます。
  
**Get-MigrationBatch** コマンドレットの詳細については、「[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)」を参照してください。
  
## <a name="see-also"></a>関連項目

[IMAP の移行に関するトラブルシューティング](https://go.microsoft.com/fwlink/p/?LinkId=536482)

