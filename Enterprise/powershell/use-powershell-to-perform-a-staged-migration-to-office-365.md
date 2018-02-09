---
title: "PowerShell を使用して Office 365 への段階的な移行を実行する"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: "概要:Windows PowerShell を使用して Office 365 への段階的な移行を実行する方法について説明します。"
ms.openlocfilehash: d30bb27700199379ea96b157051110af49bf95fa
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a><span data-ttu-id="e6982-103">PowerShell を使用して Office 365 への段階的な移行を実行する</span><span class="sxs-lookup"><span data-stu-id="e6982-103">Use PowerShell to perform a staged migration to Office 365</span></span>

 <span data-ttu-id="e6982-104">**概要:** Windows PowerShell を使用して Office 365 への段階的な移行を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e6982-104">**Summary:** Learn how to use Windows PowerShell to perform a staged migration to Office 365.</span></span>
  
<span data-ttu-id="e6982-105">段階的な移行を使用すると、ユーザーのメールボックスの内容を、元の電子メール システムから Office 365 に徐々に移行することができます。</span><span class="sxs-lookup"><span data-stu-id="e6982-105">You can migrate the contents of user mailboxes from a source email system to Office 365 over time using a staged migration.</span></span>
  
<span data-ttu-id="e6982-p101">この記事では、Exchange Online PowerShell を使用した段階的メール移行に関するタスクを順を追って説明します。トピック「[Office 365 への段階的メール移行について知っておくべきこと](https://go.microsoft.com/fwlink/p/?LinkId=536487)」では、移行プロセスについて概説しています。記事の内容に満足いただけたら、段階的メール移行を使用して、あるメール システムから別のメール システムへのメールボックスの移行を開始してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-p101">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell. The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e6982-p102">また、段階的な移行を実行するには、Exchange 管理センターを使用することもできます。「[Office 365 へのメールの段階的な移行を実行する](https://go.microsoft.com/fwlink/p/?LinkId=536687)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-p102">You can also use the Exchange admin center to perform staged migration. See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="e6982-111">始める前に把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="e6982-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="e6982-p103">このタスクの予想所要時間:移行バッチの作成に 2 ～ 5 分。移行バッチ開始後の移行時間は、バッチ内のメールボックスの数、各メールボックスのサイズ、および使用可能なネットワーク容量によって異なります。Office 365 にメールボックスの移行時間を決定するその他の要因の詳細については、「[移行のパフォーマンス](https://go.microsoft.com/fwlink/p/?LinkId=275079)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="e6982-p104">この手順を実行する際には、あらかじめアクセス許可を割り当てる必要があります。必要なアクセス許可を確認するには、トピック「[受信者のアクセス許可](https://go.microsoft.com/fwlink/p/?LinkId=534105)」の中の「移行」エントリを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="e6982-p105">Exchange Online PowerShell コマンドレットを使用するには、サインインしてコマンドレットをローカルの Windows PowerShell セッションにインポートする必要があります。手順については、「[リモート PowerShell による Exchange への接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="e6982-119">移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="e6982-120">移行の手順</span><span class="sxs-lookup"><span data-stu-id="e6982-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-staged-migration"></a><span data-ttu-id="e6982-121">ステップ 1:段階的な移行を準備する</span><span class="sxs-lookup"><span data-stu-id="e6982-121">Step 1: Prepare for a staged migration</span></span>

<span data-ttu-id="e6982-122">段階的な移行を使用してメールボックスを Office 365 に移行する前に、Exchange 環境に対していくつかの変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6982-122">Before you migrate mailboxes to Office 365 by using a staged migration, there are a few changes you must make to your Exchange environment.</span></span>
  
 <span data-ttu-id="e6982-p106">**社内の Exchange Server** に Outlook Anywhere を構成する: メール移行サービスは、Outlook Anywhere (RPC over HTTP としても知られる) を使用して社内の Exchange Server に接続します。Exchange Server 2007 と Exchange 2003 における Outlook Anywhere の設定方法の詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-p106">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server. For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span></span>
  
- <span data-ttu-id="e6982-125">「[Exchange 2007:Outlook Anywhere を有効にする方法](https://go.microsoft.com/fwlink/?LinkID=167210)」</span><span class="sxs-lookup"><span data-stu-id="e6982-125">[Exchange 2007: How to Enable Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=167210)</span></span>
    
- <span data-ttu-id="e6982-126">「[Exchange 2003 での Outlook Anywhere を構成する方法](https://go.microsoft.com/fwlink/?LinkID=167209)」</span><span class="sxs-lookup"><span data-stu-id="e6982-126">[How to configure Outlook Anywhere with Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)</span></span>
    
> [!IMPORTANT]
> <span data-ttu-id="e6982-p107">Outlook Anywhere の構成には、信頼された証明機関 (CA) によって発行された証明書を使用する必要があります。Outlook Anywhere は、自己署名入りの証明書で構成することはできません。詳細については、「[Outlook Anywhere のために SSL を構成する方法](https://go.microsoft.com/fwlink/?LinkID=80875)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-p107">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration. Outlook Anywhere can't be configured with a self-signed certificate. For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
 <span data-ttu-id="e6982-130">**オプション:Outlook Anywhere**を使用して Exchange 組織に接続できることを確認する: 接続設定をテストするには、次のいずれかの方法を試します。</span><span class="sxs-lookup"><span data-stu-id="e6982-130">**Optional: Verify that you can connect to your Exchange organization using Outlook Anywhere** Try one of the following methods to test your connection settings.</span></span>
  
- <span data-ttu-id="e6982-131">企業ネットワークの外部から Outlook を使用して社内の Exchange メールボックスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e6982-131">Use Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
- <span data-ttu-id="e6982-p108">[Microsoft Exchange リモート接続アナライザー](https://www.testexchangeconnectivity.com/)を使用して接続設定をテストします。Outlook Anywhere (RPC over HTTP) または Outlook 自動検出テストを使用します。</span><span class="sxs-lookup"><span data-stu-id="e6982-p108">Use the [Microsoft Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
- <span data-ttu-id="e6982-134">Exchange Online PowerShell で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e6982-134">Run the following commands in Exchange Online PowerShell:</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 <span data-ttu-id="e6982-p109">**アクセス許可を設定する**: 社内 Exchange 組織に接続するために使用する社内ユーザー アカウント (移行管理者ともいう) には、Office 365 に移行する社内メールボックスにアクセスするためのアクセス許可が必要です。このユーザー アカウントは、この手順の後半に記載する移行エンドポイント ([ステップ 3:移行エンドポイントを作成する](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint)) を作成して電子メール システムに接続するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="e6982-p109">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365. This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span></span>
  
<span data-ttu-id="e6982-137">メールボックスを移行するために、管理者には次のアクセス許可セットのいずれかが必要です。</span><span class="sxs-lookup"><span data-stu-id="e6982-137">To migrate the mailboxes, the admin must have one of the following permission sets:</span></span>
  
- <span data-ttu-id="e6982-138">社内組織の Active Directory の **Domain Admins** グループのメンバーであること。</span><span class="sxs-lookup"><span data-stu-id="e6982-138">Be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="e6982-139">or</span><span class="sxs-lookup"><span data-stu-id="e6982-139">or</span></span>
    
- <span data-ttu-id="e6982-140">社内の各メールボックスに **FullAccess** のアクセス許可が割り当てられ、社内のユーザー アカウントの **TargetAddress** プロパティを変更するための **WriteProperty** のアクセス許可が割り当てられていること。</span><span class="sxs-lookup"><span data-stu-id="e6982-140">Be assigned the **FullAccess** permission for each on-premises mailbox and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
    <span data-ttu-id="e6982-141">or</span><span class="sxs-lookup"><span data-stu-id="e6982-141">or</span></span>
    
- <span data-ttu-id="e6982-142">ユーザー メールボックスを格納する社内のメールボックス データベースに **受信者** のアクセス許可が割り当てられ、社内のユーザー アカウントの **TargetAddress** プロパティを変更するための **WriteProperty** のアクセス許可が割り当てられていること。</span><span class="sxs-lookup"><span data-stu-id="e6982-142">Be assigned the **Receive As** permission on the on-premises mailbox database that stores user mailboxes and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
<span data-ttu-id="e6982-143">これらのアクセス許可を設定する方法については、「[Exchange Online にメールボックスを移行するためのアクセス許可の割り当て](https://go.microsoft.com/fwlink/?LinkId=521656)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-143">For instructions about how to set these permissions, see [Assign permissions to migrate mailboxes to Office 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span></span>
  
 <span data-ttu-id="e6982-p110">**ユニファイド メッセージング (UM) を無効にする**: 移行する社内のメールボックスで UM がオンになっている場合は、移行前に UM をオフにします。移行の完了後に、メールボックスの UM をオンにします。操作手順については、「[ユーザーのユニファイド メッセージングを無効にする方法](https://go.microsoft.com/fwlink/?LinkId=521891)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-p110">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration. Turn on UM for the mailboxes after migration is complete. For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span></span>
  
 <span data-ttu-id="e6982-p111">**ディレクトリ同期を使用して Office 365 でユーザーを新規作成します。**ディレクトリ同期を使用すると、Office 365 組織のすべての社内ユーザーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e6982-p111">**Use directory synchronization to create new users in Office 365.** You use directory synchronization to create all the on-premises users in your Office 365 organization.</span></span>
  
<span data-ttu-id="e6982-p112">ユーザーの作成後にライセンスを付与する必要があります。ユーザーの作成後、ライセンスを追加するまでに 30 日間があります。ライセンスを追加する手順については、「[ステップ 8:移行後のタスクを完了する](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-p112">You need to license the users after they're created. You have 30 days to add licenses after the users are created. For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span></span>
  
 <span data-ttu-id="e6982-p113">Microsoft Azure Active Directory 同期ツール、または、Microsoft Azure Active Directory 同期サービス (AAD Sync) のいずれかを使用すると、Office 365 と同期して社内ユーザーを作成できます。メールボックスが Office 365 に移行されたら、社内組織内のユーザー アカウントを管理します。これにより、ユーザー アカウントは Office 365 組織と同期されます。詳細については、「[ディレクトリ統合](https://go.microsoft.com/fwlink/?LinkId=521788)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-p113">You can use either the Microsoft Azure Active Directory Synchronization Tool or the Microsoft Azure Active Directory Sync Services (AAD Sync) to synchronize and create your on-premises users in Office 365. After mailboxes are migrated to Office 365, you manage user accounts in your on-premises organization, and they're synchronized with your Office 365 organization. For more information, see[Directory Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .</span></span>
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a><span data-ttu-id="e6982-155">ステップ 2:段階的な移行バッチ用の CSV ファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="e6982-155">Step 2: Create a CSV file for a staged migration batch</span></span>

<span data-ttu-id="e6982-p114">Office 365 に移行する社内のメールボックスのユーザーを特定したら、コンマ区切りの値 (CSV) ファイルを使用して移行バッチを作成します。Office 365 が移行の実行に使用する CSV ファイルの各行には、社内メールボックスに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e6982-p114">After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch. Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="e6982-p115">段階的移行により Office 365 に移行する場合、移行可能なメールボックスの数に制限はありません。移行バッチ用の CSV ファイルに含めることができる行数は、最大 2,000 行までです。2,000 を超えるメールボックスを移行するには、追加の CSV ファイルを作成し、各ファイルを使用して新しい移行バッチを作成します。</span><span class="sxs-lookup"><span data-stu-id="e6982-p115">There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration. The CSV file for a migration batch can contain a maximum of 2,000 rows. To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span></span> 
  
 <span data-ttu-id="e6982-161">**サポートされている属性**</span><span class="sxs-lookup"><span data-stu-id="e6982-161">**Supported attributes**</span></span>
  
<span data-ttu-id="e6982-p116">段階的な移行用の CSV ファイルは、次の 3 つの属性をサポートします。CSV ファイルの各行はメールボックスに対応し、各属性の値を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6982-p116">The CSV file for a staged migration supports the following three attributes. Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span></span>
  
|<span data-ttu-id="e6982-164">**属性**</span><span class="sxs-lookup"><span data-stu-id="e6982-164">**Attribute**</span></span>|<span data-ttu-id="e6982-165">**説明**</span><span class="sxs-lookup"><span data-stu-id="e6982-165">**Description**</span></span>|<span data-ttu-id="e6982-166">**必須**</span><span class="sxs-lookup"><span data-stu-id="e6982-166">**Required?**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="e6982-167">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="e6982-167">EmailAddress</span></span>  <br/> |<span data-ttu-id="e6982-168">プライマリ SMTP 電子メール アドレス (たとえば、社内メールボックスの場合は pilarp@contoso.com など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="e6982-168">Specifies the primary SMTP email address, for example, pilarp@contoso.com, for on-premises mailboxes.</span></span>  <br/> <span data-ttu-id="e6982-p117">社内メールボックスには、プライマリ SMTP アドレスを使用し、Office 365 のユーザー ID は使用しないでください。たとえば、社内ドメインが contoso.com という名前で、Office 365 の電子メール ドメインが service.contoso.com という名前の場合、CSV ファイル内の電子メール アドレスにはドメイン名 contoso.com を使用します。</span><span class="sxs-lookup"><span data-stu-id="e6982-p117">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365. For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span></span>  <br/> |<span data-ttu-id="e6982-171">必須</span><span class="sxs-lookup"><span data-stu-id="e6982-171">Required</span></span>  <br/> |
|<span data-ttu-id="e6982-172">Password</span><span class="sxs-lookup"><span data-stu-id="e6982-172">Password</span></span>  <br/> |<span data-ttu-id="e6982-p118">新しい Office 365 メールボックスに設定されるパスワード。Office 365 の組織に適用されるパスワードの制約はすべて、CSV ファイル内のパスワードにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="e6982-p118">The password to be set for the new Office 365 mailbox. Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.</span></span>  <br/> |<span data-ttu-id="e6982-175">省略可能</span><span class="sxs-lookup"><span data-stu-id="e6982-175">Optional</span></span>  <br/> |
|<span data-ttu-id="e6982-176">ForceChangePassword</span><span class="sxs-lookup"><span data-stu-id="e6982-176">ForceChangePassword</span></span>  <br/> |<span data-ttu-id="e6982-p119">ユーザーが新しい Office 365 メールボックスに初めてサインインする場合に、パスワードを変更する必要があるかどうかを指定します。このパラメーターの値には **True** または **False** を使用してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-p119">Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox. Use **True** or **False** for the value of this parameter. </span></span><br/> <span data-ttu-id="e6982-179">> [!NOTE]> Active Directory フェデレーション サービス (AD FS) 以上を社内組織に展開してシングル サインオン (SSO) ソリューションを実装した場合、 **ForceChangePassword** 属性の値には **False** を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6982-179">> [!NOTE]> If you've implemented a single sign-on (SSO) solution by deploying Active Directory Federation Services (AD FS) or greater in your on-premises organization, you must use **False** for the value of the **ForceChangePassword** attribute.</span></span>          |<span data-ttu-id="e6982-180">省略可能</span><span class="sxs-lookup"><span data-stu-id="e6982-180">Optional</span></span>  <br/> |
   
 <span data-ttu-id="e6982-181">**CSV ファイル形式**</span><span class="sxs-lookup"><span data-stu-id="e6982-181">**CSV file format**</span></span>
  
<span data-ttu-id="e6982-p120">以下に、CSV ファイルの形式の例を示します。この例では、3 つの社内メールボックスが Office 365 に移行されます。</span><span class="sxs-lookup"><span data-stu-id="e6982-p120">Here's an example of the format for the CSV file. In this example, three on-premises mailboxes are migrated to Office 365.</span></span>
  
<span data-ttu-id="e6982-p121">CSV ファイルの最初の行、つまりヘッダー行には、後続の行で指定される属性 (つまり、フィールド) の名前が示されます。各属性名はコンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="e6982-p121">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow. Each attribute name is separated by a comma.</span></span>
  
```
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

<span data-ttu-id="e6982-p122">ヘッダー行の下の各行は個々のユーザーを表します。これらの行には、そのユーザーのメールボックスを移行するための情報が含まれます。各行の属性値は、ヘッダー行の属性名と同じ順序で並んでいる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6982-p122">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox. The attribute values in each row must be in the same order as the attribute names in the header row.</span></span> 
  
<span data-ttu-id="e6982-p123">CSV ファイルの作成には、任意のテキスト エディターや Excel などのアプリケーションを使用します。ファイルは .csv ファイルまたは .txt ファイルとして保存します。</span><span class="sxs-lookup"><span data-stu-id="e6982-p123">Use any text editor, or an application like Excel , to create the CSV file. Save the file as a .csv or .txt file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e6982-p124">CSV ファイルに非 ASCII 文字や特殊文字が含まれている場合は、UTF-8 などの Unicode エンコードで CSV ファイルを保存してください。アプリケーションによっては、コンピューターのシステム ロケールが CSV ファイルで使用されている言語と一致するときに、CSV ファイルを UTF-8 などの Unicode エンコードで保存した方が簡単な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e6982-p124">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding. Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span></span> 
  
### <a name="step-3-create-a-migration-endpoint"></a><span data-ttu-id="e6982-192">ステップ 3:移行エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="e6982-192">Step 3: Create a migration endpoint</span></span>
<span data-ttu-id="e6982-193"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="e6982-193"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="e6982-p125">電子メールを正常に移行するためには、Office 365 は移行元の電子メール システムと接続して通信する必要があります。これを実行するため、Office 365 では移行エンドポイントを使用します。PowerShell を使用して Outlook Anywhere 移行エンドポイントを作成するには、段階的な移行で、最初に[リモート PowerShell による Exchange への接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)を行います。</span><span class="sxs-lookup"><span data-stu-id="e6982-p125">To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="e6982-197">移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-197">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="e6982-198">Exchange Online PowerShell に "StagedEndpoint" という Outlook Anywhere 移行エンドポイントを作成するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e6982-198">To create an Outlook Anywhere migration endpoint called "StagedEndpoint" in Exchange Online PowerShell, run the following commands:</span></span>
  
```
$Credentials = Get-Credential
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

<span data-ttu-id="e6982-199">**New-MigrationEndpoint** コマンドレットの詳細については、「[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-199">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
> [!NOTE]
> <span data-ttu-id="e6982-p126">**New-MigrationEndpoint** コマンドレットで **-TargetDatabase** オプションを使用することによって、使用するサービスに対してデータベースを指定することができます。それ以外の場合、データベースは、管理メールボックスが配置されている Active Directory フェデレーション サービス (AD FS) 2.0 サイトからランダムに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="e6982-p126">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="e6982-202">機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="e6982-202">Verify it worked</span></span>

<span data-ttu-id="e6982-203">Exchange Online PowerShell で、次のコマンドを実行して "StagedEndpoint" 移行エンドポイントに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="e6982-203">In Exchange Online PowerShell, run the following command to display information about the "StagedEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a><span data-ttu-id="e6982-204">ステップ 4:段階的な移行のバッチを作成および開始する</span><span class="sxs-lookup"><span data-stu-id="e6982-204">Step 4: Create and start a stage migration batch</span></span>
<span data-ttu-id="e6982-205"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="e6982-205"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="e6982-p127">Exchange Online PowerShell の **New-MigrationBatch** コマンドレットを使用すると、一括移行の移行バッチを作成できます。 _AutoStart_ パラメーターを含めると、移行バッチを作成して自動的に開始できます。また、別の方法として、 **Start-MigrationBatch** コマンドレットを使用することにより、移行バッチを作成して後で手動で開始できます。この例では、"StagedBatch1" という移行バッチを作成して、前の例で作成した移行エンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="e6982-p127">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

<span data-ttu-id="e6982-p128">この例でも、"StagedBatch1" という移行バッチを作成して、前の例で作成した移行エンドポイントを使用します。 _AutoStart_ パラメーターが含まれていないため、移行バッチは移行ダッシュボードで、または **Start-MigrationBatch** コマンドレットを使用して手動で開始する必要があります。前述のように、一度に存在できる一括移行バッチは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="e6982-p128">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="e6982-213">機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="e6982-213">Verify it worked</span></span>

<span data-ttu-id="e6982-214">Exchange Online PowerShell で次のコマンドを実行すると、「StagedBatch1」に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e6982-214">Run the following command in Exchange Online PowerShell to display information about the "StagedBatch1":</span></span>
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

<span data-ttu-id="e6982-215">また、次のコマンドを実行すると、バッチが開始されたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e6982-215">You can also verify that the batch has started by running the following command:</span></span>
  
```
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

<span data-ttu-id="e6982-216">**Get-MigrationBatch** コマンドレットの詳細については、「[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-216">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a><span data-ttu-id="e6982-217">ステップ 5:社内メールボックスをメールが有効なユーザーに変換する</span><span class="sxs-lookup"><span data-stu-id="e6982-217">Step 5: Convert on-premises mailboxes to mail-enabled users</span></span>
<span data-ttu-id="e6982-218"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="e6982-218"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="e6982-p129">メールボックスのバッチが正常に移行されたら、何らかの方法でユーザーが各自のメールにアクセスできるようにする必要があります。メールボックスが移行されたユーザーには、社内のメールボックスと Office 365 のメールボックスの両方があります。Office 365 のメールボックスを持つユーザーは、社内のメールボックスで新着メールの受信が停止します。</span><span class="sxs-lookup"><span data-stu-id="e6982-p129">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail. A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365. Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox.</span></span> 
  
<span data-ttu-id="e6982-p130">移行が完了していないため、まだすべてのユーザーが Office 365 から各自の電子メールにアクセスできる状態ではありません。両方のメールボックスを持つユーザーに対してはどのようにすれば良いでしょうか。既に移行済みの社内メールボックスをメールが有効なユーザーに変更することができます。メールボックスからメールが有効なユーザーに変更した場合、社内メールボックスに移動するのではなく、ユーザーを Office 365 から各自の電子メールにアクセスさせることができます。</span><span class="sxs-lookup"><span data-stu-id="e6982-p130">Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email. So what do you do for those people who have both? What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users. When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox.</span></span> 
  
<span data-ttu-id="e6982-p131">社内メールボックスをメールが有効なユーザーに変換するもう 1 つの重要な理由は、プロキシ アドレスをメールが有効なユーザーにコピーすることで、Office 365 メールボックスからのプロキシ アドレスを保持するためです。これにより、Active Directory を使用して社内組織からクラウドベースのユーザーを管理できます。また、すべてのメールボックスを Office 365 に移行した後に、社内 Exchange Server 組織を停止する場合、メールが有効なユーザーにコピーされたプロキシ アドレスは、社内 Active Directory に残ります。</span><span class="sxs-lookup"><span data-stu-id="e6982-p131">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users. This lets you manage cloud-based users from your on-premises organization by using Active Directory. Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span></span>
  
<span data-ttu-id="e6982-229">メールボックスをメールが有効なユーザーに変換するために実行できるスクリプトの詳細とダウンロード方法については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-229">For more information, and to download scripts that you can run to convert mailboxes to mail-enabled users, see the following:</span></span>
  
- <span data-ttu-id="e6982-230">「[Exchange 2007 メールボックスをメールが有効なユーザーに変換する](https://go.microsoft.com/fwlink/p/?LinkId=233648)」</span><span class="sxs-lookup"><span data-stu-id="e6982-230">[Convert Exchange 2007 mailboxes to mail-enabled users](https://go.microsoft.com/fwlink/p/?LinkId=233648)</span></span>
    
- <span data-ttu-id="e6982-231">「[Exchange 2003 メールボックスをメールが有効なユーザーに変換する](https://go.microsoft.com/fwlink/p/?LinkId=233647)」</span><span class="sxs-lookup"><span data-stu-id="e6982-231">[Convert Exchange 2003 mailboxes to mail-enabled users](https://go.microsoft.com/fwlink/p/?LinkId=233647)</span></span>
    
### <a name="step-6-delete-a-staged-migration-batch"></a><span data-ttu-id="e6982-232">ステップ 6:段階的な移行バッチを削除する</span><span class="sxs-lookup"><span data-stu-id="e6982-232">Step 6: Delete a staged migration batch</span></span>
<span data-ttu-id="e6982-233"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="e6982-233"><a name="BK_Endpoint"> </a></span></span>

 <span data-ttu-id="e6982-p132">移行バッチ内のすべてのメールボックスが正常に移行された場合、バッチ内の社内メールボックスをメールが有効なユーザーに変換した後に、段階的な移行バッチを削除する準備が整います。メールが移行バッチ内の Office 365 メールボックスに転送されていることを確認してください。段階的な移行バッチを削除すると、移行サービスによって、移行バッチに関連するすべてのレコードがクリーンアップされて移行バッチが削除されます。</span><span class="sxs-lookup"><span data-stu-id="e6982-p132">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch. Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch. When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span></span>
  
<span data-ttu-id="e6982-237">Exchange Online PowerShell で "StagedBatch1" 移行バッチを削除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e6982-237">To delete the "StagedBatch1" migration batch in Exchange Online PowerShell, run the following command.</span></span>
  
```
Remove-MigrationBatch -Identity StagedBatch1
```

<span data-ttu-id="e6982-238">**Remove-MigrationBatch** コマンドレットの詳細については、「[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-238">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="e6982-239">機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="e6982-239">Verify it worked</span></span>

<span data-ttu-id="e6982-240">Exchange Online PowerShell で次のコマンドを実行すると、"IMAPBatch1" に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e6982-240">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```
Get-MigrationBatch StagedBatch1
```

<span data-ttu-id="e6982-241">このコマンドによって、状態が **Removing** の移行バッチが返されるか、移行バッチが見つからず、削除されたことの確認を求めるエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="e6982-241">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="e6982-242">**Get-MigrationBatch** コマンドレットの詳細については、「[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-242">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step7-assign-licenses-to-office-365-users"></a><span data-ttu-id="e6982-243">ステップ 7:Office 365 ユーザーにライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="e6982-243">Step7: Assign licenses to Office 365 users</span></span>
<span data-ttu-id="e6982-244"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="e6982-244"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="e6982-p133">ライセンスを割り当てて、移行されたアカウントの Office 365 のユーザー アカウントをアクティブ化します。ライセンスを割り当てないと、猶予期間 (30 日) が終了したときにメールボックスが無効になります。Office 365 管理センター でライセンスを割り当てるには、「[一般法人向け Office 365 ライセンスの割り当てまたは割り当て解除を行う](https://go.microsoft.com/fwlink/?LinkId=536681)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-p133">Activate Office 365 user accounts for the migrated accounts by assigning licenses. If you don't assign a license, the mailbox is disabled when the grace period (30 days) ends. To assign a license in the Office 365 admin center, see [Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="e6982-248">ステップ 8:移行後のタスクを完了する</span><span class="sxs-lookup"><span data-stu-id="e6982-248">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="e6982-249"><a name="BK_Postmigration"> </a></span><span class="sxs-lookup"><span data-stu-id="e6982-249"><a name="BK_Postmigration"> </a></span></span>

- <span data-ttu-id="e6982-p134">**ユーザーが各自のメールボックスに簡単にアクセスできるように、自動検出 DNS レコードを作成します。**すべての社内メールボックスが Office 365 に移行されたら、Office 365 組織に自動検出レコードを構成して、Outlook クライアントとモバイル クライアントを持つ新しい Office 365 メールボックスにユーザーが簡単に接続できるようにします。この新しい自動検出 DNS レコードは、Office 365 組織に使用しているのと同じ名前空間を使用する必要があります。たとえば、クラウドベースの名前空間が cloud.contoso.com の場合、作成する必要のある自動検出 DNS レコードは autodiscover.cloud.contoso.com となります。</span><span class="sxs-lookup"><span data-stu-id="e6982-p134">**Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="e6982-p135">Office 365 は CNAME レコードを使用して、Outlook クライアントとモバイル クライアントのための自動検出サービスを実装します。自動検出 CNAME レコードには以下の情報が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6982-p135">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="e6982-256">**エイリアス:** autodiscover</span><span class="sxs-lookup"><span data-stu-id="e6982-256">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="e6982-257">**ターゲット:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="e6982-257">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="e6982-258">詳細については、「[DNS レコードを管理するときに Office 365 の DNS レコードを作成する](https://go.microsoft.com/fwlink/p/?LinkId=535028)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-258">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="e6982-p136">**社内の Exchange サーバーの使用を停止します。**すべての電子メールが Office 365 メールボックスに直接ルーティングされていることを確認した後、社内の電子メール組織を維持する必要がもはやないか、SSO ソリューションを実装する予定がない場合は、Exchange をサーバーからアンインストールするとともに、社内の Exchange 組織を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="e6982-p136">**Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="e6982-261">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6982-261">For more information, see the following:</span></span>
    
  - <span data-ttu-id="e6982-262">「[Exchange 2010 の変更または削除](https://go.microsoft.com/fwlink/?LinkId=217936)」</span><span class="sxs-lookup"><span data-stu-id="e6982-262">[Modify or Remove Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)</span></span>
    
  - <span data-ttu-id="e6982-263">「[Exchange 2007 組織を削除する方法](https://go.microsoft.com/fwlink/?LinkID=100485)」</span><span class="sxs-lookup"><span data-stu-id="e6982-263">[How to Remove an Exchange 2007 Organization](https://go.microsoft.com/fwlink/?LinkID=100485)</span></span>
    
  - <span data-ttu-id="e6982-264">「[Exchange Server 2003 をアンインストールする方法](https://go.microsoft.com/fwlink/?LinkID=56561)」</span><span class="sxs-lookup"><span data-stu-id="e6982-264">[How to Uninstall Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)</span></span>
    

