---
title: PowerShell を使用して Office 365 へのカットオーバーの移行を実行する
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: 概要:Windows PowerShell を使用して Office 365 の一括移行を実行する方法について説明します。
ms.openlocfilehash: b40c6ac53a173f700c6b931781d98d7965a2be7c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998572"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a>PowerShell を使用して Office 365 へのカットオーバーの移行を実行する

You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration. This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell. 
  
By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.
  
> [!NOTE]
> You can also use the Exchange admin center to perform a cutover migration. See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>始める前に把握しておくべき情報

Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.
  
To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.
  
移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。
  
## <a name="migration-steps"></a>移行の手順

### <a name="step-1-prepare-for-a-cutover-migration"></a>ステップ 1:一括移行を準備する
<a name="BK_Step1"> </a>

- **Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.** The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes. Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).
    
- **Configure Outlook Anywhere on your on-premises Exchange server.** The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server. For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:
    
  - 「[Exchange 2010:Outlook Anywhere を有効にする](https://go.microsoft.com/fwlink/?LinkID=187249)」
    
  - 「[Exchange 2007:Outlook Anywhere を有効にする方法](https://go.microsoft.com/fwlink/?LinkID=167210)」
    
  - 「[Exchange 2003:RPC over HTTP の展開シナリオ](https://go.microsoft.com/fwlink/?LinkID=73657)」
    
  - 「[Exchange 2003 での Outlook Anywhere を構成する方法](https://go.microsoft.com/fwlink/?LinkID=167209)」
    
    > [!IMPORTANT]
    > Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA). It can't be configured with a self-signed certificate. For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
- **Verify that you can connect to your Exchange organization using Outlook Anywhere.** Try one of these methods to test your connection settings:
    
  - 企業ネットワークの外部から Microsoft Outlook を使用して、社内 Exchange メールボックスに接続します。
    
  - Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.
    
  - Exchange Online PowerShell で次のコマンドを実行します。
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **Exchange 組織のメールボックスへのアクセスに必要なアクセス許可を社内ユーザー アカウントに割り当てる。** オンプレミスの Exchange 組織 (移行管理者とも呼ばれます) に接続するために使用するオンプレミスのユーザーアカウントは、Office 365 に移行する社内メールボックスにアクセスするために必要なアクセス許可を持っている必要があります。 このユーザー アカウントは、社内組織の移行エンドポイントを作成するために使用されます。
    
    The following list shows the administrative privileges required to migrate mailboxes using a cutover migration. There are three possible options.
    
  - 移行管理者は、社内組織の Active Directory の **Domain Admins** グループのメンバーである必要がある。
    
    または
    
  - 移行管理者は、各社内メールボックスへの **フル アクセス**のアクセス許可が割り当てられている必要がある。
    
    または
    
  - 移行管理者は、ユーザーのメールボックスを格納する社内メールボックス データベースへの **受信者**アクセス許可が割り当てられている必要がある。
    
- **Disable Unified Messaging.** If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them. You can then enable UM on the mailboxes after the migration is complete.
    
- **Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365. If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration. Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups. If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.
    
### <a name="step-2-create-a-migration-endpoint"></a>ステップ 2:移行エンドポイントを作成する
<a name="BK_Step2"> </a>

To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
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
> The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.
  
#### <a name="verify-it-worked"></a>機能していることを確認する

Exchange Online PowerShell で、次のコマンドを実行して "CutoverEndpoint" 移行エンドポイントに関する情報を表示します。
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>ステップ 3:一括移行バッチを作成する
<a name="BK_Step3"> </a>

You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.
  
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

To start the migration batch in Exchange Online PowerShell, run the following command. This will create a migration batch called "CutoverBatch".
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>機能していることを確認する

If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing. To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a>ステップ 5:電子メールを Office 365 にルーティングします。
<a name="BK_Step5"> </a>

Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also you turn off your old email system when you're ready. 
  
For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.
  
It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6). 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a>ステップ 6:一括移行バッチを削除する
<a name="Bk_step6"> </a>

After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the cutover migration batch. Verify the following before you delete the migration batch.
  
- All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.
    
- Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.
    
Exchange Online PowerShell で "CutoverBatch" 移行バッチを削除するには、次のコマンドを実行します。
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>セクション 7:ユーザー ライセンスの割り当て
<a name="BK_Step7"> </a>

 **ライセンスを割り当てて、移行されたアカウントの Office 365 のユーザー アカウントをアクティブ化します。** ライセンスを割り当てないと、猶予期間が終了したとき (30 日) にメールボックスが無効になります。 Microsoft 365 管理センターでライセンスを割り当てるには、「[365 Office 2013 for business のライセンスの割り当てまたは割り当て解除](https://go.microsoft.com/fwlink/?LinkId=536681)を行う」を参照してください。
  
### <a name="step-8-complete-post-migration-tasks"></a>ステップ 8:移行後のタスクを完了する
<a name="BK_Step8"> </a>

- **Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.
    
    Exchange Server を残す場合は、移行後に内部および外部 DNS の両方で自動検出 DNS CNAME レコードが Office 365 を指すようにして、Outlook クライアントが適切なメールボックスに接続するようにします。
    
    > [!NOTE]
    >  Exchange 2007、Exchange 2010、および Exchange 2013 では、 `Set-ClientAccessServer AutodiscoverInternalConnectionURI` を `Null` に設定する必要もあります。 
  
    Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:
    
  - **エイリアス:** autodiscover
    
  - **ターゲット:** autodiscover.outlook.com
    
    詳細については、「[DNS レコードを管理するときに Office 365 の DNS レコードを作成する](https://go.microsoft.com/fwlink/p/?LinkId=535028)」を参照してください。
    
- **Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.
    
    詳細については、以下を参照してください。
    
  - 「[Exchange 2010 の変更または削除](https://go.microsoft.com/fwlink/?LinkId=217936)」
    
  - 「[Exchange 2007 組織を削除する方法](https://go.microsoft.com/fwlink/?LinkID=100485)」
    
  - 「[Exchange Server 2003 をアンインストールする方法](https://go.microsoft.com/fwlink/?LinkID=56561)」
    

