---
title: PowerShell を使用して Office 365 へのカットオーバーの移行を実行する
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: 概要:Windows PowerShell を使用して Office 365 の一括移行を実行する方法について説明します。
ms.openlocfilehash: 0f284e2dcccd3d7fc6958922ac4e87da4fc086ec
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574081"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a><span data-ttu-id="2e6ec-103">PowerShell を使用して Office 365 へのカットオーバーの移行を実行する</span><span class="sxs-lookup"><span data-stu-id="2e6ec-103">Use PowerShell to perform a cutover migration to Office 365</span></span>

 <span data-ttu-id="2e6ec-104">**概要:** Windows PowerShell を使用して Office 365 の一括移行を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-104">**Summary:** Learn how to use Windows PowerShell to perform a cutover migration to Office 365.</span></span>
  
<span data-ttu-id="2e6ec-p101">一括移行を使用すると、移行元の電子メール システムから Office 365 へユーザーのメールボックスの内容を一度に移行できます。この記事では、Exchange Online PowerShell を使用した電子メールの一括移行の作業を順を追って説明します。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p101">You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration. This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="2e6ec-p102">トピック「[Office 365 への一括メール移行について知っておくべきこと](https://go.microsoft.com/fwlink/p/?LinkId=536688)」を確認すると、移行プロセスの概要を把握できます。記事の内容に満足いただけたら、段階的メール移行を使用して、あるメール システムから別のメール システムへのメールボックスの移行を開始してください。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p102">By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2e6ec-p103">また、一括移行を実行するには、Exchange 管理センターを使用することもできます。「[メールを Office 365 に一括で移行する](https://go.microsoft.com/fwlink/p/?LinkId=536689)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p103">You can also use the Exchange admin center to perform a cutover migration. See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="2e6ec-111">始める前に把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="2e6ec-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="2e6ec-p104">このタスクの予想所要時間:移行バッチの作成に 2 ～ 5 分。移行バッチ開始後の移行時間は、バッチ内のメールボックスの数、各メールボックスのサイズ、および使用可能なネットワーク容量によって異なります。Office 365 にメールボックスの移行時間を決定するその他の要因の詳細については、「[移行のパフォーマンス](https://go.microsoft.com/fwlink/p/?LinkId=275079)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p104">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="2e6ec-p105">この手順を実行する際には、あらかじめアクセス許可を割り当てる必要があります。必要なアクセス許可を確認するには、トピック「[受信者のアクセス許可](https://go.microsoft.com/fwlink/p/?LinkId=534105)」内の表にある「移行」エントリを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p105">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="2e6ec-p106">Exchange Online PowerShell コマンドレットを使用するには、サインインしてコマンドレットをローカルの Windows PowerShell セッションにインポートする必要があります。手順については、「[リモート PowerShell による Exchange への接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p106">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="2e6ec-119">移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="2e6ec-120">移行の手順</span><span class="sxs-lookup"><span data-stu-id="2e6ec-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-cutover-migration"></a><span data-ttu-id="2e6ec-121">ステップ 1:一括移行を準備する</span><span class="sxs-lookup"><span data-stu-id="2e6ec-121">Step 1: Prepare for a cutover migration</span></span>
<span data-ttu-id="2e6ec-122"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="2e6ec-122"></span></span>

- <span data-ttu-id="2e6ec-p107">**社内 Exchange 組織を Office 365 組織の承認済みドメインとして追加する。** 移行サービスは、社内メールボックスの SMTP アドレスを使用して、新しい Office 365 メールボックスに Microsoft Online Services のユーザー ID とメール アドレスを作成します。Exchange ドメインが Office 365 組織の承認済みドメイン (またはプライマリ ドメイン) でない場合は、移行が失敗します。詳細については、「[Office 365 でドメインを確認する](https://go.microsoft.com/fwlink/p/?LinkId=534110)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p107">**Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.** The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes. Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="2e6ec-p108">**社内 Exchange サーバーで Outlook Anywhere を構成する。** 電子メール移行サービスは、RPC over HTTP または Outlook Anywhere を使用して社内 Exchange サーバーに接続します。Exchange 2010、Exchange 2007、および Exchange 2003 で Outlook Anywhere をセットアップする方法については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p108">**Configure Outlook Anywhere on your on-premises Exchange server.** The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server. For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span></span>
    
  - <span data-ttu-id="2e6ec-130">「[Exchange 2010:Outlook Anywhere を有効にする](https://go.microsoft.com/fwlink/?LinkID=187249)」</span><span class="sxs-lookup"><span data-stu-id="2e6ec-130">[Exchange 2010: Enable Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=187249)</span></span>
    
  - <span data-ttu-id="2e6ec-131">「[Exchange 2007:Outlook Anywhere を有効にする方法](https://go.microsoft.com/fwlink/?LinkID=167210)」</span><span class="sxs-lookup"><span data-stu-id="2e6ec-131">[Exchange 2007: How to Enable Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=167210)</span></span>
    
  - <span data-ttu-id="2e6ec-132">「[Exchange 2003:RPC over HTTP の展開シナリオ](https://go.microsoft.com/fwlink/?LinkID=73657)」</span><span class="sxs-lookup"><span data-stu-id="2e6ec-132">[Exchange 2003: Deployment Scenarios for RPC over HTTP](https://go.microsoft.com/fwlink/?LinkID=73657)</span></span>
    
  - <span data-ttu-id="2e6ec-133">「[Exchange 2003 での Outlook Anywhere を構成する方法](https://go.microsoft.com/fwlink/?LinkID=167209)」</span><span class="sxs-lookup"><span data-stu-id="2e6ec-133">[How to Configure Outlook Anywhere with Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="2e6ec-p109">Outlook Anywhere の構成は、信頼された証明機関 (CA) により発行された証明書を使用して行う必要があります。自己署名入りの証明書では構成できません。詳細については、「[Outlook Anywhere のために SSL を構成する方法](https://go.microsoft.com/fwlink/?LinkID=80875)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p109">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA). It can't be configured with a self-signed certificate. For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
- <span data-ttu-id="2e6ec-p110">**Outlook Anywhere を使用して Exchange 組織に接続できることを確認する。** 次のいずれかの方法で、接続設定をテストしてください:</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p110">**Verify that you can connect to your Exchange organization using Outlook Anywhere.** Try one of these methods to test your connection settings:</span></span>
    
  - <span data-ttu-id="2e6ec-139">企業ネットワークの外部から Microsoft Outlook を使用して、社内 Exchange メールボックスに接続します。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-139">Use Microsoft Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
  - <span data-ttu-id="2e6ec-p111">Microsoft [Exchange リモート接続アナライザー](https://www.testexchangeconnectivity.com/)を使用して接続設定をテストします。Outlook Anywhere (RPC over HTTP) または Outlook 自動検出テストを使用します。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p111">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
  - <span data-ttu-id="2e6ec-142">Exchange Online PowerShell で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-142">Run the following commands in Exchange Online PowerShell.</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- <span data-ttu-id="2e6ec-143">**Exchange 組織のメールボックスへのアクセスに必要なアクセス許可を社内ユーザー アカウントに割り当てる。**</span><span class="sxs-lookup"><span data-stu-id="2e6ec-143">**Assign an on-premises user account the necessary permissions to access mailboxes in your Exchange organization.**</span></span> <span data-ttu-id="2e6ec-144">オンプレミスの Exchange 組織 (移行管理者とも呼ばれます) に接続するために使用するオンプレミスのユーザーアカウントは、Office 365 に移行する社内メールボックスにアクセスするために必要なアクセス許可を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-144">The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365.</span></span> <span data-ttu-id="2e6ec-145">このユーザー アカウントは、社内組織の移行エンドポイントを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-145">This user account is used to create a migration endpoint to your on-premises organization.</span></span>
    
    <span data-ttu-id="2e6ec-p113">以下の一覧に、一括移行を使用してメールボックスを移行するために必要な管理者権限を示します。3 つの可能なオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p113">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration. There are three possible options.</span></span>
    
  - <span data-ttu-id="2e6ec-148">移行管理者は、社内組織の Active Directory の **Domain Admins** グループのメンバーである必要がある。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-148">The migration administrator must be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="2e6ec-149">または</span><span class="sxs-lookup"><span data-stu-id="2e6ec-149">Or</span></span>
    
  - <span data-ttu-id="2e6ec-150">移行管理者は、各社内メールボックスへの **フル アクセス**のアクセス許可が割り当てられている必要がある。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-150">The migration administrator must be assigned the **FullAccess** permission for each on-premises mailbox.</span></span>
    
    <span data-ttu-id="2e6ec-151">または</span><span class="sxs-lookup"><span data-stu-id="2e6ec-151">Or</span></span>
    
  - <span data-ttu-id="2e6ec-152">移行管理者は、ユーザーのメールボックスを格納する社内メールボックス データベースへの **受信者**アクセス許可が割り当てられている必要がある。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-152">The migration administrator must be assigned the **Receive As** permission on the on-premises mailbox database that stores the user mailboxes.</span></span>
    
- <span data-ttu-id="2e6ec-p114">**ユニファイド メッセージングを無効にする。** 移行する社内メールボックスでユニファイド メッセージング (UM) が有効である場合、メールボックスを移行する前にメールボックスで UM を無効にする必要があります。移行が完了すると、メールボックスで UM を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p114">**Disable Unified Messaging.** If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them. You can then enable UM on the mailboxes after the migration is complete.</span></span>
    
- <span data-ttu-id="2e6ec-p115">**セキュリティ グループと委任** メール移行サービスでは、オンプレミスの Active Directory グループがセキュリティ グループであるかどうかを検出できないため、移行したグループをセキュリティ グループとして Office 365 でプロビジョニングすることができません。Office 365 テナント内にセキュリティ グループが必要な場合は、一括移行を開始する前に、あらかじめ Office 365 テナントに、メールが有効な空のセキュリティ グループをプロビジョニングする必要があります。さらに、この移行方法では、メールボックス、メール ユーザー、メール連絡先、およびメールが有効なグループのみを移動します。他の Active Directory オブジェクト (Office 365 に移行されないユーザーなど) を管理者として割り当てるか、または移行対象のオブジェクトに委任してある場合は、移行前にオブジェクトから削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p115">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365. If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration. Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups. If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span></span>
    
### <a name="step-2-create-a-migration-endpoint"></a><span data-ttu-id="2e6ec-160">ステップ 2:移行エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="2e6ec-160">Step 2: Create a migration endpoint</span></span>
<span data-ttu-id="2e6ec-161"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="2e6ec-161"></span></span>

<span data-ttu-id="2e6ec-p116">電子メールを正常に移行するためには、Office 365 は移行元の電子メール システムと接続して通信する必要があります。これを実行するため、Office 365 では移行エンドポイントを使用します。一括移行用に Outlook Anywhere の移行エンドポイントを作成するには、最初に [リモート PowerShell による Exchange への接続](https://go.microsoft.com/fwlink/p/?LinkId=534121)を行います。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p116">To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="2e6ec-165">移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-165">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="2e6ec-166">Exchange Online PowerShell で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-166">Run the following commands in Exchange Online PowerShell:</span></span>
  
```
$Credentials = Get-Credential
```

<span data-ttu-id="2e6ec-167">この例では、[Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) コマンドレットを使用して、社内の Exchange サーバーへの接続設定を取得およびテストしてから、この接続設定を使用して "CutoverEndpoint" という移行エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-167">The example uses the [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet to obtain and test the connection settings to the on-premises Exchange server, and then uses those connection settings to create the migration endpoint called "CutoverEndpoint".</span></span>
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> <span data-ttu-id="2e6ec-p117">**New-MigrationEndpoint** コマンドレットで **-TargetDatabase** オプションを使用することによって、使用するサービスに対してデータベースを指定することができます。それ以外の場合、データベースは、管理メールボックスが配置されている Active Directory フェデレーション サービス (AD FS) 2.0 サイトからランダムに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p117">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="2e6ec-170">機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="2e6ec-170">Verify it worked</span></span>

<span data-ttu-id="2e6ec-171">Exchange Online PowerShell で、次のコマンドを実行して "CutoverEndpoint" 移行エンドポイントに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-171">In Exchange Online PowerShell, run the following command to display information about the "CutoverEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a><span data-ttu-id="2e6ec-172">ステップ 3:一括移行バッチを作成する</span><span class="sxs-lookup"><span data-stu-id="2e6ec-172">Step 3: Create the cutover migration batch</span></span>
<span data-ttu-id="2e6ec-173"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="2e6ec-173"></span></span>

<span data-ttu-id="2e6ec-p118">Exchange Online PowerShell の **New-MigrationBatch** コマンドレットを使用すると、一括移行の移行バッチを作成できます。 _AutoStart_ パラメーターを含めると、移行バッチを作成して自動的に開始できます。また、別の方法として、 **Start-MigrationBatch** コマンドレットを使用することにより、移行バッチを作成して後で手動で開始できます。この例では、"CutoverBatch" という移行バッチを作成して、前の例で作成した移行エンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p118">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

<span data-ttu-id="2e6ec-p119">この例でも、"CutoverBatch" という移行バッチを作成して、前の例で作成した移行エンドポイントを使用します。 _AutoStart_ パラメーターが含まれていないため、移行バッチは移行ダッシュボードで、または **Start-MigrationBatch** コマンドレットを使用して手動で開始する必要があります。前述のように、一度に存在できる一括移行バッチは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p119">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="2e6ec-181">機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="2e6ec-181">Verify it worked</span></span>

<span data-ttu-id="2e6ec-182">一括移行用の移行バッチが正常に作成されたことを確認するには、Exchange Online PowerShell で次のコマンドを実行して、新しい移行バッチに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-182">To verify that you've successfully created a migration batch for a cutover migration, run the following command in Exchange Online PowerShell to display information about the new migration batch:</span></span>
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a><span data-ttu-id="2e6ec-183">ステップ 4:一括移行バッチを開始する</span><span class="sxs-lookup"><span data-stu-id="2e6ec-183">Step 4: Start the cutover migration batch</span></span>
<span data-ttu-id="2e6ec-184"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="2e6ec-184"></span></span>

<span data-ttu-id="2e6ec-p120">Exchange Online PowerShell で移行バッチを開始するには、次のコマンドを実行します。そうすると、"CutoverBatch" という移行バッチが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p120">To start the migration batch in Exchange Online PowerShell, run the following command. This will create a migration batch called "CutoverBatch".</span></span>
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a><span data-ttu-id="2e6ec-187">機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="2e6ec-187">Verify it worked</span></span>

<span data-ttu-id="2e6ec-p121">移行バッチが正常に開始されると、移行ダッシュボードのバッチの状態は「同期中」になります。Exchange Online PowerShell を使用して移行バッチが正常に開始したことを確認するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p121">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing. To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span></span>
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="2e6ec-190">ステップ 5:電子メールを Office 365 にルーティングします。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-190">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="2e6ec-191"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="2e6ec-191"></span></span>

<span data-ttu-id="2e6ec-p122">電子メール システムは、MX レコードという DNS レコードを使用して、電子メールの配信先を見つけ出します。電子メールの移行プロセス中、MX レコードの宛先は移行元の電子メール システムでした。Office 365 への電子メール移行が完了したので、今度は MX レコードの宛先は Office 365 になります。 これにより、電子メールは Office 365 のメールボックスに確実に配信されます。MX レコードを移動することによって、準備ができたら古い電子メール システムをオフにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p122">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also you turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="2e6ec-p123">多くの DNS プロバイダー向けに、[MX レコードの変更](https://go.microsoft.com/fwlink/p/?LinkId=279163)の具体的な説明があります。DNS プロバイダーが含まれていない場合や、全般的な方向を把握したい場合は、「[任意の DNS ホスティング プロバイダーで Office 365 用の DNS レコードを作成する](https://go.microsoft.com/fwlink/?LinkId=397449)」も用意されています。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p123">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="2e6ec-p124">御社のお客様およびパートナーの電子メール システムが MX レコードの変更を認識するまでに最大 72 時間かかることがあります。次の作業に進むまで、72 時間以上待ちます。 [ステップ 6:一括移行バッチを削除する](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p124">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span></span> 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a><span data-ttu-id="2e6ec-201">ステップ 6:一括移行バッチを削除する</span><span class="sxs-lookup"><span data-stu-id="2e6ec-201">Step 6: Delete the cutover migration batch</span></span>
<span data-ttu-id="2e6ec-202"><a name="Bk_step6"> </a></span><span class="sxs-lookup"><span data-stu-id="2e6ec-202"></span></span>

<span data-ttu-id="2e6ec-p125">MX レコードを変更して、すべての電子メールが Office 365 にルーティングされていることを確認したら、ユーザーのメールが Office 365 に移動することをユーザーに通知します。その後、一括移行バッチを削除できます。移行バッチを削除する前に、次の点を確認します。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p125">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the cutover migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="2e6ec-p126">すべてのユーザーが Office 365 メールボックスを使用している。バッチを削除した後は、社内 Exchange サーバー上のメールボックスに送信されるメールが、対応する Office 365 メールボックスにコピーされません。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p126">All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="2e6ec-p127">Office 365 のメールボックスが、メールが直接送信され始めてから 1 回以上同期した。これを行うには、移行バッチの [最終同期時刻] ボックスの値が、メールが Office 365 のメールボックスに直接ルーティングされ始めた時より後の時間であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p127">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="2e6ec-210">Exchange Online PowerShell で "CutoverBatch" 移行バッチを削除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-210">To delete the "CutoverBatch" migration batch in Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a><span data-ttu-id="2e6ec-211">セクション 7:ユーザー ライセンスの割り当て</span><span class="sxs-lookup"><span data-stu-id="2e6ec-211">Section 7: Assign user licenses</span></span>
<span data-ttu-id="2e6ec-212"><a name="BK_Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="2e6ec-212"></span></span>

 <span data-ttu-id="2e6ec-213">**ライセンスを割り当てて、移行されたアカウントの Office 365 のユーザー アカウントをアクティブ化します。**</span><span class="sxs-lookup"><span data-stu-id="2e6ec-213">**Activate Office 365 user accounts for the migrated accounts by assigning licenses.**</span></span> <span data-ttu-id="2e6ec-214">ライセンスを割り当てないと、猶予期間が終了したとき (30 日) にメールボックスが無効になります。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-214">If you don't assign a license, the mailbox is disabled when the grace period ends (30 days).</span></span> <span data-ttu-id="2e6ec-215">Microsoft 365 管理センターでライセンスを割り当てるには、「[Office 2013 for business のライセンスの割り当てまたは割り当て解除](https://go.microsoft.com/fwlink/?LinkId=536681)を行う」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-215">To assign a license in the Microsoft 365 admin center, see[Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="2e6ec-216">ステップ 8:移行後のタスクを完了する</span><span class="sxs-lookup"><span data-stu-id="2e6ec-216">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="2e6ec-217"><a name="BK_Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="2e6ec-217"></span></span>

- <span data-ttu-id="2e6ec-p129">**ユーザーが各自のメールボックスに簡単にアクセスできるように、自動検出 DNS レコードを作成します。** すべての社内メールボックスが Office 365 に移行されたら、Office 365 組織に自動検出レコードを構成して、Outlook クライアントとモバイル クライアントを持つ新しい Office 365 メールボックスにユーザーが簡単に接続できるようにします。この新しい自動検出 DNS レコードは、Office 365 組織に使用しているのと同じ名前空間を使用する必要があります。たとえば、クラウドベースの名前空間が cloud.contoso.com の場合、作成する必要のある自動検出 DNS レコードは autodiscover.cloud.contoso.com となります。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p129">**Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="2e6ec-222">Exchange Server を残す場合は、移行後に内部および外部 DNS の両方で自動検出 DNS CNAME レコードが Office 365 を指すようにして、Outlook クライアントが適切なメールボックスに接続するようにします。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-222">If you keep your Exchange Server, you should also make sure that Autodiscover DNS CNAME record has to point to Office 365 in both internal and external DNS after the migration so that the Outlook client will to connect to the correct mailbox.</span></span>
    
    > [!NOTE]
    >  <span data-ttu-id="2e6ec-223">Exchange 2007、Exchange 2010、および Exchange 2013 では、 `Set-ClientAccessServer AutodiscoverInternalConnectionURI` を `Null` に設定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-223">In Exchange 2007, Exchange 2010, and Exchange 2013 you should also set `Set-ClientAccessServer AutodiscoverInternalConnectionURI` to `Null`.</span></span> 
  
    <span data-ttu-id="2e6ec-p130">Office 365 は CNAME レコードを使用して、Outlook クライアントとモバイル クライアントのための自動検出サービスを実装します。自動検出 CNAME レコードには以下の情報が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p130">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="2e6ec-226">**エイリアス:** autodiscover</span><span class="sxs-lookup"><span data-stu-id="2e6ec-226">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="2e6ec-227">**ターゲット:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="2e6ec-227">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="2e6ec-228">詳細については、「[DNS レコードを管理するときに Office 365 の DNS レコードを作成する](https://go.microsoft.com/fwlink/p/?LinkId=535028)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-228">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="2e6ec-p131">**社内の Exchange サーバーの使用を停止します。** すべての電子メールが Office 365 メールボックスに直接ルーティングされていることを確認した後、社内の電子メール組織を維持する必要がもはやないか、シングル サインオン (SSO) ソリューションを実装する予定がない場合は、Exchange をサーバーからアンインストールするとともに、社内の Exchange 組織を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-p131">**Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="2e6ec-231">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e6ec-231">For more information, see the following:</span></span>
    
  - <span data-ttu-id="2e6ec-232">「[Exchange 2010 の変更または削除](https://go.microsoft.com/fwlink/?LinkId=217936)」</span><span class="sxs-lookup"><span data-stu-id="2e6ec-232">[Modify or Remove Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)</span></span>
    
  - <span data-ttu-id="2e6ec-233">「[Exchange 2007 組織を削除する方法](https://go.microsoft.com/fwlink/?LinkID=100485)」</span><span class="sxs-lookup"><span data-stu-id="2e6ec-233">[How to Remove an Exchange 2007 Organization](https://go.microsoft.com/fwlink/?LinkID=100485)</span></span>
    
  - <span data-ttu-id="2e6ec-234">「[Exchange Server 2003 をアンインストールする方法](https://go.microsoft.com/fwlink/?LinkID=56561)」</span><span class="sxs-lookup"><span data-stu-id="2e6ec-234">[How to Uninstall Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)</span></span>
    

