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
ms.openlocfilehash: b6c68dc611d22579f81db838b2b5d08e99f7519a
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "38746270"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-office-365"></a><span data-ttu-id="a629d-103">PowerShell を使用した Office 365 への IMAP 移行の実行</span><span class="sxs-lookup"><span data-stu-id="a629d-103">Use PowerShell to perform an IMAP migration to Office 365</span></span>

<span data-ttu-id="a629d-p101">Office 365 を展開するプロセスの一部として、Internet Mail Access Protocol (IMAP) 電子メール サービスから Office 365 に、ユーザーのメールボックスの内容を移行することができます。この記事では、Exchange Online PowerShell を使用した電子メールの IMAP 移行作業を順を追って説明します。</span><span class="sxs-lookup"><span data-stu-id="a629d-p101">As part of the process of deploying Office 365, you can choose to migrate the contents of user mailboxes from an Internet Mail Access Protocol (IMAP) email service to Office 365. This article walks you through the tasks for an email IMAP migration by using Exchange Online PowerShell.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="a629d-p102">また、IMAP 移行を実行するには、Exchange 管理センターを使用することもできます。「[IMAP メールボックスを Office 365 に移行する](https://go.microsoft.com/fwlink/p/?LinkId=536685)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629d-p102">You can also use the Exchange admin center to perform an IMAP migration. See [Migrate your IMAP mailboxes to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536685).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="a629d-108">始める前に把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="a629d-108">What do you need to know before you begin?</span></span>

<span data-ttu-id="a629d-p103">このタスクの予想所要時間:移行バッチの作成に 2 ～ 5 分。移行バッチ開始後の移行時間は、バッチ内のメールボックスの数、各メールボックスのサイズ、および使用可能なネットワーク容量によって異なります。Office 365 にメールボックスの移行時間を決定するその他の要因の詳細については、「[移行のパフォーマンス](https://go.microsoft.com/fwlink/p/?LinkId=275079)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629d-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="a629d-p104">この手順を実行する際には、あらかじめアクセス許可を割り当てる必要があります。必要なアクセス許可を確認するには、トピック「[受信者のアクセス許可](https://go.microsoft.com/fwlink/p/?LinkId=534105)」内の表にある「移行」エントリを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629d-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="a629d-p105">Exchange Online PowerShell コマンドレットを使用するには、サインインしてコマンドレットをローカルの Windows PowerShell セッションにインポートする必要があります。手順については、「[リモート PowerShell による Exchange への接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629d-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="a629d-116">移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629d-116">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="a629d-117">IMAP の移行には次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="a629d-117">The following restrictions apply to IMAP migrations:</span></span>
  
- <span data-ttu-id="a629d-p106">ユーザーの受信トレイまたは他のメール フォルダー内のアイテムのみ、移行できます。連絡先、予定表アイテム、またはタスクを移行することはできません。</span><span class="sxs-lookup"><span data-stu-id="a629d-p106">Only items in a user's inbox or other mail folders can be migrated. You can't migrate contacts, calendar items, or tasks.</span></span>
    
- <span data-ttu-id="a629d-120">最大で 500,000 アイテムをユーザーのメールボックスから移行できます。</span><span class="sxs-lookup"><span data-stu-id="a629d-120">A maximum of 500,000 items can be migrated from a user's mailbox.</span></span>
    
- <span data-ttu-id="a629d-121">移行できるメッセージの最大サイズは 35 MB です。</span><span class="sxs-lookup"><span data-stu-id="a629d-121">The maximum message size that can be migrated is 35 MB.</span></span>
    
## <a name="migration-steps"></a><span data-ttu-id="a629d-122">移行の手順</span><span class="sxs-lookup"><span data-stu-id="a629d-122">Migration steps</span></span>

### <a name="step-1-prepare-for-an-imap-migration"></a><span data-ttu-id="a629d-123">ステップ 1:IMAP 移行を準備する</span><span class="sxs-lookup"><span data-stu-id="a629d-123">Step 1: Prepare for an IMAP migration</span></span>
<span data-ttu-id="a629d-124"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="a629d-124"></span></span>

- <span data-ttu-id="a629d-p107">**IMAP 組織のドメインをお持ちの場合は、Office 365 組織の承認済みドメインとして追加します。** Office 365 のメールボックス用に既に所有している同じドメインを使用する場合は、最初にこのドメインを承認済みドメインとして Office 365 に追加する必要があります。追加したら、Office 365 でユーザーを作成できます。詳細については、「[Office 365 でドメインを確認する](https://go.microsoft.com/fwlink/p/?LinkId=534110)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629d-p107">**If you have a domain for you IMAP organization, add it as an accepted domain of your Office 365 organization.** If you want to use the same domain you already own for your Office 365 mailboxes, you first have to add it as an accepted domain to Office 365. After you have added it, you can create your users in Office 365. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="a629d-p108">**各ユーザーを Office 365 に追加します。そうすることで、ユーザーは Office 365 メールボックスを持つことができます。** 手順については、「[一般法人向け Office 365 にユーザーを追加する](https://go.microsoft.com/fwlink/p/?LinkId=535065)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629d-p108">**Add each user to Office 365 so that they have an Office 365 mailbox.** For instructions, see[Add users to Office 365 for business](https://go.microsoft.com/fwlink/p/?LinkId=535065).</span></span>
    
- <span data-ttu-id="a629d-p109">**IMAP サーバーの FQDN を取得します**。IMAP 移行エンドポイントを作成するときに、メールボックス データの移行元の IMAP サーバーの完全修飾ドメイン名 (FQDN) (フル コンピューター名ともいう) を指定する必要があります。IMAP クライアントまたは PING コマンドを使用して、インターネット経由での FQDN サーバーとの通信に FQDN を使用できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a629d-p109">**Obtain the FQDN of the IMAP server**. You need to provide the fully qualified domain name (FQDN) (also called the full computer name) of the IMAP server that you will migrate mailbox data from when you create an IMAP migration endpoint. Use an IMAP client or the PING command to verify that you can use the FQDN to communicate with the IMAP server over the Internet.</span></span>
    
- <span data-ttu-id="a629d-p110">**IMAP 接続を許可するファイアウォールを構成します**。IMAP サーバーをホストする組織のファイアウォールでポートを開く必要があります。そうすることで、移行中 Microsoft データセンターから発信するネットワーク トラフィックが IMAP サーバーをホストする組織に入ることができます。Microsoft データセンターが使用する IP アドレスの一覧については、「[Office 365 の URL と IP アドレスの範囲](https://go.microsoft.com/fwlink/p/?LinkId=535066)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629d-p110">**Configure the firewall to allow IMAP connections**. You might have to open ports in the firewall of the organization that hosts the IMAP server so network traffic originating from the Microsoft datacenter during the migration is allowed to enter the organization that hosts the IMAP server. For a list of IP addresses used by Microsoft datacenters, see [Exchange Online URLs and IP Address Ranges](https://go.microsoft.com/fwlink/p/?LinkId=535066).</span></span>
    
- <span data-ttu-id="a629d-p111">**IMAP 組織内のメールボックスにアクセスする管理者アカウントのアクセス許可を割り当てます**。CSV ファイルで管理者の資格情報を使用する場合は、使用するアカウントに、社内メールボックスへのアクセスに必要なアクセス許可が必要になります。ユーザーのメールボックスへのアクセスに必要なアクセス許可は、特定の IMAP サーバーによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="a629d-p111">**Assign the administrator account permissions to access mailboxes in your IMAP organization**. If you use administrator credentials in the CSV file, the account that you use must have the necessary permissions to access the on-premises mailboxes. The permissions required to access user mailboxes is determined by the particular IMAP server.</span></span> 
    
- <span data-ttu-id="a629d-p112">**Exchange Online PowerShell コマンドレットを使用するには**、サインインしてコマンドレットをローカルの Windows PowerShell セッションにインポートする必要があります。手順については、「[リモート PowerShell による Exchange への接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629d-p112">**To use the Exchange Online PowerShell cmdlets**, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
    
    <span data-ttu-id="a629d-142">移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629d-142">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
    
- <span data-ttu-id="a629d-p113">**IMAP サーバーに接続できることを確認します**。IMAP サーバーへの接続設定をテストするには、Exchange Online PowerShell で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a629d-p113">**Verify that you can connect to your IMAP server**. Run the following command in Exchange Online PowerShell to test the connection settings to your IMAP server.</span></span>
    
  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    <span data-ttu-id="a629d-145">**Port** パラメーターの値については、通常、暗号化されていない接続やトランスポート層セキュリティ (TLS) 接続には 143 を使用し、SSL 接続には 993 を使用します。</span><span class="sxs-lookup"><span data-stu-id="a629d-145">For the value of the **Port** parameter, it's typical to use 143 for unencrypted or Transport Layer Security (TLS) connections and to use 993 for SSL connections.</span></span>
    
### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a><span data-ttu-id="a629d-146">ステップ 2:IMAP 移行バッチ用の CSV ファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="a629d-146">Step 2: Create a CSV file for an IMAP migration batch</span></span>
<span data-ttu-id="a629d-147"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="a629d-147"></span></span>

<span data-ttu-id="a629d-p114">IMAP 移行バッチでそのメールボックスを移行するユーザーのグループを特定します。CSV ファイルの各行には、IMAP メッセージング システム内のメールボックスに接続するために必要な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a629d-p114">Identify the group of users whose mailboxes you want to migrate in an IMAP migration batch. Each row in the CSV file contains information necessary to connect to a mailbox in the IMAP messaging system.</span></span>
  
<span data-ttu-id="a629d-150">各ユーザーの必須属性は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a629d-150">Here are the required attributes for each user:</span></span> 
  
- <span data-ttu-id="a629d-151">**EmailAddress** ユーザーの Office 365 メールボックスのユーザー ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="a629d-151">**EmailAddress** specifies the user ID for the user's Office 365 mailbox.</span></span>
    
- <span data-ttu-id="a629d-152">**UserName** は、IMAP サーバー上のメールボックスへのアクセスに使用するアカウントのログオン名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a629d-152">**UserName** specifies the logon name for the account to use to access the mailbox on the IMAP server.</span></span>
    
- <span data-ttu-id="a629d-153">**Password** は、 **UserName** 列のアカウントのパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a629d-153">**Password** specifies the password for the account in the **UserName** column.</span></span>
    
<span data-ttu-id="a629d-p115">以下に、CSV ファイルの形式の例を示します。この例では、3 人のメールボックスが移行されます。</span><span class="sxs-lookup"><span data-stu-id="a629d-p115">Here's an example of the format for the CSV file. In this example, three mailboxes are migrated:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

<span data-ttu-id="a629d-156">**UserName** 属性については、ユーザー名に加えて、IMAP サーバーのメールボックスへのアクセスに必要なアクセス許可が割り当てられているアカウントの資格情報を使用できます。以下はいくつかの IMAP サーバーで使用されている特定の形式の一部です。</span><span class="sxs-lookup"><span data-stu-id="a629d-156">For the **UserName** attribute, in addition to the user name, you can use the credentials of an account that has been assigned the necessary permissions to access mailboxes on the IMAP server, the following are some of the specific formats used for some of the IMAP servers:</span></span>
  
 <span data-ttu-id="a629d-157">**Microsoft Exchange:**</span><span class="sxs-lookup"><span data-stu-id="a629d-157">**Microsoft Exchange:**</span></span>
  
<span data-ttu-id="a629d-p116">Microsoft Exchange の IMAP 実装から電子メールを移行する場合、CSV ファイルでは **UserName** 属性に **Domain/Admin_UserName/User_UserName** という形式を使用します。Terry Adams、Ann Beebe、および Paul Cannon の電子メールを Exchange から移行するとします。メールの管理者アカウントは、ユーザー名は **mailadmin** 、パスワードは **P@ssw0rd** とします。CSV ファイルは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a629d-p116">If you're migrating email from the IMAP implementation for Microsoft Exchange, use the format **Domain/Admin_UserName/User_UserName** for the **UserName** attribute in the CSV file. Let's say you're migrating email from Exchange for Terry Adams, Ann Beebe, and Paul Cannon. You have a mail administrator account, where the user name is **mailadmin** and the password is **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 <span data-ttu-id="a629d-162">**Dovecot:**</span><span class="sxs-lookup"><span data-stu-id="a629d-162">**Dovecot:**</span></span>
  
<span data-ttu-id="a629d-p117">Simple Authentication and Security Layer (SASL) をサポートしている IMAP サーバー (Dovecot IMAP サーバーなど) では、**User_UserName\*Admin_UserName** の形式を使用します。ここで、アスタリスク (\*) は、構成可能な区切り文字です。たとえば、管理者の資格情報 ( **mailadmin** と **P@ssw0rd** ) を使用して、上記の同じユーザーの電子メールを Dovecot IMAP サーバーから移行するとします。CSV ファイルは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a629d-p117">For IMAP servers that support Simple Authentication and Security Layer (SASL), such as a Dovecot IMAP server, use the format **User_UserName\*Admin_UserName**, where the asterisk ( \* ) is a configurable separator character. Let's say you're migrating those same users' email from a Dovecot IMAP server using the administrator credentials **mailadmin** and **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 <span data-ttu-id="a629d-166">**Mirapoint:**</span><span class="sxs-lookup"><span data-stu-id="a629d-166">**Mirapoint:**</span></span>
  
<span data-ttu-id="a629d-p118">Mirapoint Message Server から電子メールを移行する場合は、管理者の資格情報に **#user@domain#Admin_UserName#** の形式を使用します。管理者の資格情報である **mailadmin** と **P@ssw0rd** を使用して Mirapoint から電子メールを移行する場合、CSV ファイルは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a629d-p118">If you're migrating email from Mirapoint Message Server, use the format **#user@domain#Admin_UserName#** for the administrator credentials. To migrate email from Mirapoint using the administrator credentials **mailadmin** and **P@ssw0rd**, your CSV file would look like this:</span></span>
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 <span data-ttu-id="a629d-169">**Courier IMAP:**</span><span class="sxs-lookup"><span data-stu-id="a629d-169">**Courier IMAP:**</span></span>
  
<span data-ttu-id="a629d-p119">Courier IMAP のような一部の移行元の電子メール システムでは、Office 365 にメールボックスを移行するためにメールボックスの管理者の資格情報を使用することをサポートしていません。代わりに、仮想共有フォルダーを使用するように移行元の電子メール システムを設定することができます。仮想共有フォルダーを使用すると、移行元の電子メール システムのユーザーのメールボックスにアクセスするためにメールボックスの管理資格情報を使用できます。Courier IMAP の仮想共有フォルダーを構成する方法の詳細については、「[共有フォルダー](https://go.microsoft.com/fwlink/p/?LinkId=398870)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629d-p119">Some source email systems, such as Courier IMAP, don't support using mailbox admin credentials to migrate mailboxes to Office 365. Instead, you can set up your source email system to use virtual shared folders. By using virtual shared folders, you can use the mailbox admin credentials to access user mailboxes on the source email system. For more information about how to configure virtual shared folders for Courier IMAP, see [Shared Folders](https://go.microsoft.com/fwlink/p/?LinkId=398870).</span></span>
  
<span data-ttu-id="a629d-p120">移行元の電子メール システムで仮想共有フォルダーをセットアップしてからメールボックスを移行するには、オプション属性 **UserRoot** を移行ファイルに含める必要があります。この属性では、移行元電子メール システムの仮想共有フォルダー構造にある各ユーザーのメールボックスの場所を指定します。たとえば、Terry のメールボックスへのパスは /users/terry.adams です。</span><span class="sxs-lookup"><span data-stu-id="a629d-p120">To migrate mailboxes after you set up virtual shared folders on your source email system, you have to include the optional attribute **UserRoot** in the migration file. This attribute specifies the location of each user's mailbox in the virtual shared folder structure on the source email system. For example, the path to Terry's mailbox is /users/terry.adams.</span></span>
  
<span data-ttu-id="a629d-177">以下に、 **UserRoot** 属性を含む CSV ファイルの例を示します。</span><span class="sxs-lookup"><span data-stu-id="a629d-177">Here's an example of a CSV file that contains the **UserRoot** attribute:</span></span>
  
```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a><span data-ttu-id="a629d-178">ステップ 3:IMAP 移行エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="a629d-178">Step 3: Create an IMAP migration endpoint</span></span>
<span data-ttu-id="a629d-179"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="a629d-179"></span></span>

<span data-ttu-id="a629d-p121">電子メールを正常に移行するためには、Office 365 は移行元の電子メール システムと接続して通信する必要があります。これを行うため、Office 365 では移行エンドポイントを使用します。移行エンドポイントは、同時に移行するメールボックスの数、および 24 時間ごとに 1 回行われる増分同期中に同時に同期するメールボックスの数も定義します。IMAP 移行用に移行エンドポイントを作成するには、最初に[リモート PowerShell による Exchange への接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)を行います。</span><span class="sxs-lookup"><span data-stu-id="a629d-p121">To migrate email successfully, Office 365 needs to connect to and communicate with the source email system. To do this, Office 365 uses a migration endpoint. The migration endpoint also defines the number of mailboxes to migrate simultaneously and the number of mailboxes to synchronize simultaneously during incremental synchronization, which occurs once every 24 hours. To create a migration end point for IMAP migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="a629d-184">移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629d-184">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="a629d-185">Exchange Online PowerShell で "IMAPEndpoint" という IMAP 移行エンドポイントを作成するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a629d-185">To create the IMAP migration endpoint called "IMAPEndpoint" in Exchange Online PowerShell, run the following command:</span></span>
  
```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

<span data-ttu-id="a629d-p122">また、同時移行、増分の同時移行、および使用するポートを指定するパラメーターを追加することもできます。次の Exchange Online PowerShell コマンドは、50 の同時移行と最大 25 の同時増分同期をサポートする "IMAPEndpoint" という IMAP 移行エンドポイントを作成します。さらに、このエンドポイントを TLS 暗号化用にポート 143 を使用するように構成します。</span><span class="sxs-lookup"><span data-stu-id="a629d-p122">You can also add parameters to specify concurrent migrations, concurrent incremental migrations, and the port to use. The following Exchange Online PowerShell command creates an IMAP migration endpoint called "IMAPEndpoint" that supports 50 concurrent migrations and up to 25 concurrent incremental synchronizations. It also configures the endpoint to use port 143 for TLS encryption.</span></span>
  
```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

<span data-ttu-id="a629d-189">**New-MigrationEndpoint** コマンドレットの詳細については、「[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629d-189">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="a629d-190">機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="a629d-190">Verify it worked</span></span>

<span data-ttu-id="a629d-191">Exchange Online PowerShell で次のコマンドを実行すると、"IMAPEndpoint" に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a629d-191">Run the following command in Exchange Online PowerShell to display information about the "IMAPEndpoint":</span></span>
  
```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a><span data-ttu-id="a629d-192">ステップ 4:IMAP 移行バッチを作成および開始する</span><span class="sxs-lookup"><span data-stu-id="a629d-192">Step 4: Create and start an IMAP migration batch</span></span>
<span data-ttu-id="a629d-193"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="a629d-193"></span></span>

<span data-ttu-id="a629d-p123">[New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) コマンドレットを使用すると、IMAP 移行用の移行バッチを作成できます。 _AutoStart_ パラメーターを含めると、移行バッチを作成して自動的に開始できます。代わりに、移行バッチを作成してから、後で[Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440) コマンドレットを使用して開始することができます。</span><span class="sxs-lookup"><span data-stu-id="a629d-p123">You can use the [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) cmdlet to create a migration batch for an IMAP migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then start it afterwards by using the[Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440) cmdlet.</span></span>
  
<span data-ttu-id="a629d-197">次の Exchange Online PowerShell コマンドは、"IMAPEndpoint" という IMAP エンドポイントを使用して "IMAPBatch1" という移行バッチを自動的に開始します。</span><span class="sxs-lookup"><span data-stu-id="a629d-197">The following Exchange Online PowerShell command will automatically start the migration batch called "IMAPBatch1" using the IMAP endpoint called "IMAPEndpoint":</span></span>
  
```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a><span data-ttu-id="a629d-198">機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="a629d-198">Verify it worked</span></span>

<span data-ttu-id="a629d-199">[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) コマンドレットを実行すると、"IMAPBatch1" に関する情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="a629d-199">Run the [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) cmdlet to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

<span data-ttu-id="a629d-200">また、次のコマンドを実行すると、バッチが開始されたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="a629d-200">You can also verify that the batch has started by running the following command:</span></span>
  
```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="a629d-201">ステップ 5:電子メールを Office 365 にルーティングします。</span><span class="sxs-lookup"><span data-stu-id="a629d-201">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="a629d-202"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="a629d-202"></span></span>

<span data-ttu-id="a629d-p124">電子メール システムは、MX レコードという DNS レコードを使用して、電子メールの配信先を見つけ出します。電子メールの移行プロセス中、MX レコードの宛先は移行元の電子メール システムでした。Office 365 への電子メール移行が完了したので、今度は MX レコードの宛先は Office 365 になります。 これにより、電子メールは Office 365 のメールボックスに確実に配信されます。MX レコードを移動することによって、準備ができたら古い電子メール システムをオフにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a629d-p124">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="a629d-p125">多くの DNS プロバイダー向けに、[MX レコードの変更](https://go.microsoft.com/fwlink/p/?LinkId=279163)の具体的な説明があります。DNS プロバイダーが含まれていない場合や、全般的な方向を把握したい場合は、「[任意の DNS ホスティング プロバイダーで Office 365 用の DNS レコードを作成する](https://go.microsoft.com/fwlink/?LinkId=397449)」も用意されています。</span><span class="sxs-lookup"><span data-stu-id="a629d-p125">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="a629d-p126">御社のお客様およびパートナーの電子メール システムが MX レコードの変更を認識するまでに最大 72 時間かかることがあります。次の作業に進むまで、72 時間以上待ちます。手順 6: IMAP 移行バッチを削除する。</span><span class="sxs-lookup"><span data-stu-id="a629d-p126">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: Step 6: Delete IMAP migration batch.</span></span> 
  
### <a name="step-6-delete-imap-migration-batch"></a><span data-ttu-id="a629d-212">ステップ 6:IMAP 移行バッチを削除する</span><span class="sxs-lookup"><span data-stu-id="a629d-212">Step 6: Delete IMAP migration batch</span></span>
<span data-ttu-id="a629d-213"><a name="BK_Step6"> </a></span><span class="sxs-lookup"><span data-stu-id="a629d-213"></span></span>

<span data-ttu-id="a629d-p127">MX レコードを変更して、すべての電子メールが Office 365 のメールボックスにルーティングされていることを確認したら、ユーザーのメールが Office 365 に移動することをユーザーに通知します。その後、IMAP 移行バッチを削除できます。移行バッチを削除する前に、次の点を確認します。</span><span class="sxs-lookup"><span data-stu-id="a629d-p127">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the IMAP migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="a629d-p128">すべてのユーザーが Office 365 メールボックスを使用している。バッチを削除した後は、社内 Exchange サーバー上のメールボックスに送信されるメールが、対応する Office 365 メールボックスにコピーされません。</span><span class="sxs-lookup"><span data-stu-id="a629d-p128">All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="a629d-p129">Office 365 のメールボックスが、メールが直接送信され始めてから 1 回以上同期した。これを行うには、移行バッチの [最終同期時刻] ボックスの値が、メールが Office 365 のメールボックスに直接ルーティングされ始めた時より後の時間であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a629d-p129">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="a629d-221">Exchange Online PowerShell から "IMAPBatch1" 移行バッチを削除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a629d-221">To delete the "IMAPBatch1" migration batch from Exchange Online PowerShell, run the following command:</span></span>
  
```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

<span data-ttu-id="a629d-222">**Remove-MigrationBatch** コマンドレットの詳細については、「[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629d-222">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="a629d-223">機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="a629d-223">Verify it worked</span></span>

<span data-ttu-id="a629d-224">Exchange Online PowerShell で次のコマンドを実行すると、"IMAPBatch1" に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a629d-224">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch IMAPBatch1"
```

<span data-ttu-id="a629d-225">このコマンドによって、状態が **Removing** の移行バッチが返されるか、移行バッチが見つからず、削除されたことの確認を求めるエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="a629d-225">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="a629d-226">**Get-MigrationBatch** コマンドレットの詳細については、「[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629d-226">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a629d-227">関連項目</span><span class="sxs-lookup"><span data-stu-id="a629d-227">See also</span></span>

[<span data-ttu-id="a629d-228">IMAP の移行に関するトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a629d-228">IMAP Migration Troubleshooter</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536482)

