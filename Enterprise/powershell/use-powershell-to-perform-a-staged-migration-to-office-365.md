---
title: PowerShell を使用して Office 365 への段階的な移行を実行する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: 概要:Windows PowerShell を使用して Office 365 への段階的な移行を実行する方法について説明します。
ms.openlocfilehash: ca50edd079e17808c46ff5a956ed2efad34eb322
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052560"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a>PowerShell を使用して Office 365 への段階的な移行を実行する

段階的な移行を使用すると、ユーザーのメールボックスの内容を、元の電子メール システムから Office 365 に徐々に移行することができます。
  
This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell. The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.
  
> [!NOTE]
> You can also use the Exchange admin center to perform staged migration. See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>始める前に把握しておくべき情報

Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.
  
To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.
  
移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。
  
## <a name="migration-steps"></a>移行の手順

### <a name="step-1-prepare-for-a-staged-migration"></a>ステップ 1:段階的な移行を準備する

段階的な移行を使用してメールボックスを Office 365 に移行する前に、Exchange 環境に対していくつかの変更を加える必要があります。
  
 **Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server. For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:
  
- 「[Exchange 2007:Outlook Anywhere を有効にする方法](https://go.microsoft.com/fwlink/?LinkID=167210)」
    
- 「[Exchange 2003 での Outlook Anywhere を構成する方法](https://go.microsoft.com/fwlink/?LinkID=167209)」
    
> [!IMPORTANT]
> You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration. Outlook Anywhere can't be configured with a self-signed certificate. For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
 **オプション:Outlook Anywhere**を使用して Exchange 組織に接続できることを確認する: 接続設定をテストするには、次のいずれかの方法を試します。
  
- 企業ネットワークの外部から Outlook を使用して社内の Exchange メールボックスに接続します。
    
- [Microsoft リモート接続アナライザー](https://https://testconnectivity.microsoft.com/)を使用して、接続設定をテストします。 Outlook Anywhere (RPC over HTTP) または Outlook 自動検出テストを使用します。
    
- Exchange Online PowerShell で次のコマンドを実行します。
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365. This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).
  
メールボックスを移行するために、管理者には次のアクセス許可セットのいずれかが必要です。
  
- 社内組織の Active Directory の **Domain Admins** グループのメンバーであること。
    
    または
    
- 社内の各メールボックスに **FullAccess** のアクセス許可が割り当てられ、社内のユーザー アカウントの **TargetAddress** プロパティを変更するための **WriteProperty** のアクセス許可が割り当てられていること。
    
    or
    
- ユーザー メールボックスを格納する社内のメールボックス データベースに **受信者** のアクセス許可が割り当てられ、社内のユーザー アカウントの **TargetAddress** プロパティを変更するための **WriteProperty** のアクセス許可が割り当てられていること。
    
これらのアクセス許可を設定する方法については、「[Exchange Online にメールボックスを移行するためのアクセス許可の割り当て](https://go.microsoft.com/fwlink/?LinkId=521656)」を参照してください。
  
 **Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration. Turn on UM for the mailboxes after migration is complete. For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).
  
 **Use directory synchronization to create new users in Office 365.** You use directory synchronization to create all the on-premises users in your Office 365 organization.
  
You need to license the users after they're created. You have 30 days to add licenses after the users are created. For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).
  
 Microsoft Azure Active Directory (Azure AD) 同期ツールまたは Microsoft Azure AD 同期サービスのいずれかを使用して、Office 365 でオンプレミスユーザーを同期および作成できます。 メールボックスを Office 365 に移行した後、社内組織のユーザーアカウントを管理し、Office 365 組織と同期します。 詳細については、「[ディレクトリ統合](https://go.microsoft.com/fwlink/?LinkId=521788)」を参照してください。
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>ステップ 2:段階的な移行バッチ用の CSV ファイルを作成する

After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch. Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox. 
  
> [!NOTE]
> There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration. The CSV file for a migration batch can contain a maximum of 2,000 rows. To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch. 
  
 **サポートされている属性**
  
The CSV file for a staged migration supports the following three attributes. Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.
  
|**属性**|**説明**|**必須**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |プライマリ SMTP 電子メール アドレス (たとえば、社内メールボックスの場合は pilarp@contoso.com など) を指定します。  <br/> Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365. For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.  <br/> |必須  <br/> |
|Password  <br/> |The password to be set for the new Office 365 mailbox. Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.  <br/> |省略可能  <br/> |
|ForceChangePassword  <br/> |Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox. Use **True** or **False** for the value of this parameter. <br/> > [!NOTE]> Active Directory フェデレーション サービス (AD FS) 以上を社内組織に展開してシングル サインオン (SSO) ソリューションを実装した場合、 **ForceChangePassword** 属性の値には **False** を使用する必要があります。          |省略可能  <br/> |
   
 **CSV ファイル形式**
  
Here's an example of the format for the CSV file. In this example, three on-premises mailboxes are migrated to Office 365.
  
The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow. Each attribute name is separated by a comma.
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox. The attribute values in each row must be in the same order as the attribute names in the header row. 
  
Use any text editor, or an application like Excel , to create the CSV file. Save the file as a .csv or .txt file.
  
> [!NOTE]
> If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding. Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file. 
  
### <a name="step-3-create-a-migration-endpoint"></a>ステップ 3:移行エンドポイントを作成する
<a name="BK_Endpoint"> </a>

To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
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
> The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.
  
#### <a name="verify-it-worked"></a>機能していることを確認する

Exchange Online PowerShell で、次のコマンドを実行して "StagedEndpoint" 移行エンドポイントに関する情報を表示します。
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>ステップ 4:段階的な移行のバッチを作成および開始する
<a name="BK_Endpoint"> </a>

You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.
  
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

After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail. A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365. Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox. 
  
Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email. So what do you do for those people who have both? What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users. When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox. 
  
Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users. This lets you manage cloud-based users from your on-premises organization by using Active Directory. Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.
    
### <a name="step-6-delete-a-staged-migration-batch"></a>ステップ 6:段階的な移行バッチを削除する
<a name="BK_Endpoint"> </a>

 After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch. Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch. When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.
  
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
  
### <a name="step7-assign-licenses-to-office-365-users"></a>ステップ 7:Office 365 ユーザーにライセンスを割り当てる
<a name="BK_Endpoint"> </a>

ライセンスを割り当てて、移行されたアカウントの Office 365 のユーザー アカウントをアクティブ化します。 ライセンスを割り当てないと、猶予期間 (30 日) が終了したときにメールボックスが無効になります。 Microsoft 365 管理センターでライセンスを割り当てるには、「[一般法人向け Office 365 ライセンスの割り当てまたは割り当て解除を行う](https://go.microsoft.com/fwlink/?LinkId=536681)」を参照してください。
  
### <a name="step-8-complete-post-migration-tasks"></a>ステップ 8:移行後のタスクを完了する
<a name="BK_Postmigration"> </a>

- **Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.
    
    Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:
    
  - **エイリアス:** autodiscover
    
  - **ターゲット:** autodiscover.outlook.com
    
    詳細については、「[DNS レコードを管理するときに Office 365 の DNS レコードを作成する](https://go.microsoft.com/fwlink/p/?LinkId=535028)」を参照してください。
    
- **Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.
    
    詳細については、以下を参照してください。
    
  - 「[Exchange 2010 の変更または削除](https://go.microsoft.com/fwlink/?LinkId=217936)」
    
  - 「[Exchange 2007 組織を削除する方法](https://go.microsoft.com/fwlink/?LinkID=100485)」
    
  - 「[Exchange Server 2003 をアンインストールする方法](https://go.microsoft.com/fwlink/?LinkID=56561)」
    

