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
# <a name="use-powershell-to-perform-a-staged-migration-to-office-365"></a><span data-ttu-id="c63ee-103">PowerShell を使用して Office 365 への段階的な移行を実行する</span><span class="sxs-lookup"><span data-stu-id="c63ee-103">Use PowerShell to perform a staged migration to Office 365</span></span>

<span data-ttu-id="c63ee-104">段階的な移行を使用すると、ユーザーのメールボックスの内容を、元の電子メール システムから Office 365 に徐々に移行することができます。</span><span class="sxs-lookup"><span data-stu-id="c63ee-104">You can migrate the contents of user mailboxes from a source email system to Office 365 over time using a staged migration.</span></span>
  
<span data-ttu-id="c63ee-105">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c63ee-105">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell.</span></span> <span data-ttu-id="c63ee-106">The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process.</span><span class="sxs-lookup"><span data-stu-id="c63ee-106">The topic, [What you need to know about a staged email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process.</span></span> <span data-ttu-id="c63ee-107">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span><span class="sxs-lookup"><span data-stu-id="c63ee-107">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c63ee-108">You can also use the Exchange admin center to perform staged migration.</span><span class="sxs-lookup"><span data-stu-id="c63ee-108">You can also use the Exchange admin center to perform staged migration.</span></span> <span data-ttu-id="c63ee-109">See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span><span class="sxs-lookup"><span data-stu-id="c63ee-109">See [Perform a staged migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="c63ee-110">始める前に把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="c63ee-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="c63ee-111">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span><span class="sxs-lookup"><span data-stu-id="c63ee-111">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span></span> <span data-ttu-id="c63ee-112">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span><span class="sxs-lookup"><span data-stu-id="c63ee-112">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span></span> <span data-ttu-id="c63ee-113">For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="c63ee-113">For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="c63ee-114">You need to be assigned permissions before you can perform this procedure or procedures.</span><span class="sxs-lookup"><span data-stu-id="c63ee-114">You need to be assigned permissions before you can perform this procedure or procedures.</span></span> <span data-ttu-id="c63ee-115">To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span><span class="sxs-lookup"><span data-stu-id="c63ee-115">To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="c63ee-116">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session.</span><span class="sxs-lookup"><span data-stu-id="c63ee-116">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session.</span></span> <span data-ttu-id="c63ee-117">See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span><span class="sxs-lookup"><span data-stu-id="c63ee-117">See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="c63ee-118">移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c63ee-118">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="c63ee-119">移行の手順</span><span class="sxs-lookup"><span data-stu-id="c63ee-119">Migration steps</span></span>

### <a name="step-1-prepare-for-a-staged-migration"></a><span data-ttu-id="c63ee-120">ステップ 1:段階的な移行を準備する</span><span class="sxs-lookup"><span data-stu-id="c63ee-120">Step 1: Prepare for a staged migration</span></span>

<span data-ttu-id="c63ee-121">段階的な移行を使用してメールボックスを Office 365 に移行する前に、Exchange 環境に対していくつかの変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="c63ee-121">Before you migrate mailboxes to Office 365 by using a staged migration, there are a few changes you must make to your Exchange environment.</span></span>
  
 <span data-ttu-id="c63ee-122">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="c63ee-122">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server.</span></span> <span data-ttu-id="c63ee-123">For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span><span class="sxs-lookup"><span data-stu-id="c63ee-123">For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span></span>
  
- <span data-ttu-id="c63ee-124">「[Exchange 2007:Outlook Anywhere を有効にする方法](https://go.microsoft.com/fwlink/?LinkID=167210)」</span><span class="sxs-lookup"><span data-stu-id="c63ee-124">[Exchange 2007: How to Enable Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=167210)</span></span>
    
- <span data-ttu-id="c63ee-125">「[Exchange 2003 での Outlook Anywhere を構成する方法](https://go.microsoft.com/fwlink/?LinkID=167209)」</span><span class="sxs-lookup"><span data-stu-id="c63ee-125">[How to configure Outlook Anywhere with Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)</span></span>
    
> [!IMPORTANT]
> <span data-ttu-id="c63ee-126">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration.</span><span class="sxs-lookup"><span data-stu-id="c63ee-126">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration.</span></span> <span data-ttu-id="c63ee-127">Outlook Anywhere can't be configured with a self-signed certificate.</span><span class="sxs-lookup"><span data-stu-id="c63ee-127">Outlook Anywhere can't be configured with a self-signed certificate.</span></span> <span data-ttu-id="c63ee-128">For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="c63ee-128">For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
 <span data-ttu-id="c63ee-129">**オプション:Outlook Anywhere**を使用して Exchange 組織に接続できることを確認する: 接続設定をテストするには、次のいずれかの方法を試します。</span><span class="sxs-lookup"><span data-stu-id="c63ee-129">**Optional: Verify that you can connect to your Exchange organization using Outlook Anywhere** Try one of the following methods to test your connection settings.</span></span>
  
- <span data-ttu-id="c63ee-130">企業ネットワークの外部から Outlook を使用して社内の Exchange メールボックスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c63ee-130">Use Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
- <span data-ttu-id="c63ee-131">[Microsoft リモート接続アナライザー](https://https://testconnectivity.microsoft.com/)を使用して、接続設定をテストします。</span><span class="sxs-lookup"><span data-stu-id="c63ee-131">Use the [Microsoft Remote Connectivity Analyzer](https://https://testconnectivity.microsoft.com/) to test your connection settings.</span></span> <span data-ttu-id="c63ee-132">Outlook Anywhere (RPC over HTTP) または Outlook 自動検出テストを使用します。</span><span class="sxs-lookup"><span data-stu-id="c63ee-132">Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
- <span data-ttu-id="c63ee-133">Exchange Online PowerShell で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c63ee-133">Run the following commands in Exchange Online PowerShell:</span></span>
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 <span data-ttu-id="c63ee-134">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365.</span><span class="sxs-lookup"><span data-stu-id="c63ee-134">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365.</span></span> <span data-ttu-id="c63ee-135">This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span><span class="sxs-lookup"><span data-stu-id="c63ee-135">This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span></span>
  
<span data-ttu-id="c63ee-136">メールボックスを移行するために、管理者には次のアクセス許可セットのいずれかが必要です。</span><span class="sxs-lookup"><span data-stu-id="c63ee-136">To migrate the mailboxes, the admin must have one of the following permission sets:</span></span>
  
- <span data-ttu-id="c63ee-137">社内組織の Active Directory の **Domain Admins** グループのメンバーであること。</span><span class="sxs-lookup"><span data-stu-id="c63ee-137">Be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="c63ee-138">または</span><span class="sxs-lookup"><span data-stu-id="c63ee-138">or</span></span>
    
- <span data-ttu-id="c63ee-139">社内の各メールボックスに **FullAccess** のアクセス許可が割り当てられ、社内のユーザー アカウントの **TargetAddress** プロパティを変更するための **WriteProperty** のアクセス許可が割り当てられていること。</span><span class="sxs-lookup"><span data-stu-id="c63ee-139">Be assigned the **FullAccess** permission for each on-premises mailbox and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
    <span data-ttu-id="c63ee-140">or</span><span class="sxs-lookup"><span data-stu-id="c63ee-140">or</span></span>
    
- <span data-ttu-id="c63ee-141">ユーザー メールボックスを格納する社内のメールボックス データベースに **受信者** のアクセス許可が割り当てられ、社内のユーザー アカウントの **TargetAddress** プロパティを変更するための **WriteProperty** のアクセス許可が割り当てられていること。</span><span class="sxs-lookup"><span data-stu-id="c63ee-141">Be assigned the **Receive As** permission on the on-premises mailbox database that stores user mailboxes and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
<span data-ttu-id="c63ee-142">これらのアクセス許可を設定する方法については、「[Exchange Online にメールボックスを移行するためのアクセス許可の割り当て](https://go.microsoft.com/fwlink/?LinkId=521656)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c63ee-142">For instructions about how to set these permissions, see [Assign permissions to migrate mailboxes to Office 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span></span>
  
 <span data-ttu-id="c63ee-143">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration.</span><span class="sxs-lookup"><span data-stu-id="c63ee-143">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration.</span></span> <span data-ttu-id="c63ee-144">Turn on UM for the mailboxes after migration is complete.</span><span class="sxs-lookup"><span data-stu-id="c63ee-144">Turn on UM for the mailboxes after migration is complete.</span></span> <span data-ttu-id="c63ee-145">For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span><span class="sxs-lookup"><span data-stu-id="c63ee-145">For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span></span>
  
 <span data-ttu-id="c63ee-146">**Use directory synchronization to create new users in Office 365.**</span><span class="sxs-lookup"><span data-stu-id="c63ee-146">**Use directory synchronization to create new users in Office 365.**</span></span> <span data-ttu-id="c63ee-147">You use directory synchronization to create all the on-premises users in your Office 365 organization.</span><span class="sxs-lookup"><span data-stu-id="c63ee-147">You use directory synchronization to create all the on-premises users in your Office 365 organization.</span></span>
  
<span data-ttu-id="c63ee-148">You need to license the users after they're created.</span><span class="sxs-lookup"><span data-stu-id="c63ee-148">You need to license the users after they're created.</span></span> <span data-ttu-id="c63ee-149">You have 30 days to add licenses after the users are created.</span><span class="sxs-lookup"><span data-stu-id="c63ee-149">You have 30 days to add licenses after the users are created.</span></span> <span data-ttu-id="c63ee-150">For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span><span class="sxs-lookup"><span data-stu-id="c63ee-150">For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span></span>
  
 <span data-ttu-id="c63ee-151">Microsoft Azure Active Directory (Azure AD) 同期ツールまたは Microsoft Azure AD 同期サービスのいずれかを使用して、Office 365 でオンプレミスユーザーを同期および作成できます。</span><span class="sxs-lookup"><span data-stu-id="c63ee-151">You can use either the Microsoft Azure Active Directory (Azure AD) Synchronization Tool or the Microsoft Azure AD Sync Services  to synchronize and create your on-premises users in Office 365.</span></span> <span data-ttu-id="c63ee-152">メールボックスを Office 365 に移行した後、社内組織のユーザーアカウントを管理し、Office 365 組織と同期します。</span><span class="sxs-lookup"><span data-stu-id="c63ee-152">After mailboxes are migrated to Office 365, you manage user accounts in your on-premises organization, and they're synchronized with your Office 365 organization.</span></span> <span data-ttu-id="c63ee-153">詳細については、「[ディレクトリ統合](https://go.microsoft.com/fwlink/?LinkId=521788)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c63ee-153">For more information, see[Directory Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .</span></span>
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a><span data-ttu-id="c63ee-154">ステップ 2:段階的な移行バッチ用の CSV ファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="c63ee-154">Step 2: Create a CSV file for a staged migration batch</span></span>

<span data-ttu-id="c63ee-155">After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch.</span><span class="sxs-lookup"><span data-stu-id="c63ee-155">After you identify the users whose on-premises mailboxes you want to migrate to Office 365, you use a comma separated value (CSV ) file to create a migration batch.</span></span> <span data-ttu-id="c63ee-156">Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox.</span><span class="sxs-lookup"><span data-stu-id="c63ee-156">Each row in the CSV file—used by Office 365 to run the migration—contains information about an on-premises mailbox.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="c63ee-157">There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration.</span><span class="sxs-lookup"><span data-stu-id="c63ee-157">There isn't a limit for the number of mailboxes that you can migrate to Office 365 using a staged migration.</span></span> <span data-ttu-id="c63ee-158">The CSV file for a migration batch can contain a maximum of 2,000 rows.</span><span class="sxs-lookup"><span data-stu-id="c63ee-158">The CSV file for a migration batch can contain a maximum of 2,000 rows.</span></span> <span data-ttu-id="c63ee-159">To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span><span class="sxs-lookup"><span data-stu-id="c63ee-159">To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span></span> 
  
 <span data-ttu-id="c63ee-160">**サポートされている属性**</span><span class="sxs-lookup"><span data-stu-id="c63ee-160">**Supported attributes**</span></span>
  
<span data-ttu-id="c63ee-161">The CSV file for a staged migration supports the following three attributes.</span><span class="sxs-lookup"><span data-stu-id="c63ee-161">The CSV file for a staged migration supports the following three attributes.</span></span> <span data-ttu-id="c63ee-162">Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span><span class="sxs-lookup"><span data-stu-id="c63ee-162">Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span></span>
  
|<span data-ttu-id="c63ee-163">**属性**</span><span class="sxs-lookup"><span data-stu-id="c63ee-163">**Attribute**</span></span>|<span data-ttu-id="c63ee-164">**説明**</span><span class="sxs-lookup"><span data-stu-id="c63ee-164">**Description**</span></span>|<span data-ttu-id="c63ee-165">**必須**</span><span class="sxs-lookup"><span data-stu-id="c63ee-165">**Required?**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="c63ee-166">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="c63ee-166">EmailAddress</span></span>  <br/> |<span data-ttu-id="c63ee-167">プライマリ SMTP 電子メール アドレス (たとえば、社内メールボックスの場合は pilarp@contoso.com など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="c63ee-167">Specifies the primary SMTP email address, for example, pilarp@contoso.com, for on-premises mailboxes.</span></span>  <br/> <span data-ttu-id="c63ee-168">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365.</span><span class="sxs-lookup"><span data-stu-id="c63ee-168">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Office 365.</span></span> <span data-ttu-id="c63ee-169">For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span><span class="sxs-lookup"><span data-stu-id="c63ee-169">For example, if the on-premises domain is named contoso.com but the Office 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span></span>  <br/> |<span data-ttu-id="c63ee-170">必須</span><span class="sxs-lookup"><span data-stu-id="c63ee-170">Required</span></span>  <br/> |
|<span data-ttu-id="c63ee-171">Password</span><span class="sxs-lookup"><span data-stu-id="c63ee-171">Password</span></span>  <br/> |<span data-ttu-id="c63ee-172">The password to be set for the new Office 365 mailbox.</span><span class="sxs-lookup"><span data-stu-id="c63ee-172">The password to be set for the new Office 365 mailbox.</span></span> <span data-ttu-id="c63ee-173">Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.</span><span class="sxs-lookup"><span data-stu-id="c63ee-173">Any password restrictions that are applied to your Office 365 organization also apply to the passwords included in the CSV file.</span></span>  <br/> |<span data-ttu-id="c63ee-174">省略可能</span><span class="sxs-lookup"><span data-stu-id="c63ee-174">Optional</span></span>  <br/> |
|<span data-ttu-id="c63ee-175">ForceChangePassword</span><span class="sxs-lookup"><span data-stu-id="c63ee-175">ForceChangePassword</span></span>  <br/> |<span data-ttu-id="c63ee-176">Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox.</span><span class="sxs-lookup"><span data-stu-id="c63ee-176">Specifies whether a user must change the password the first time they sign in to their new Office 365 mailbox.</span></span> <span data-ttu-id="c63ee-177">Use **True** or **False** for the value of this parameter.</span><span class="sxs-lookup"><span data-stu-id="c63ee-177">Use **True** or **False** for the value of this parameter.</span></span> <br/> <span data-ttu-id="c63ee-178">> [!NOTE]> Active Directory フェデレーション サービス (AD FS) 以上を社内組織に展開してシングル サインオン (SSO) ソリューションを実装した場合、 **ForceChangePassword** 属性の値には **False** を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c63ee-178">> [!NOTE]> If you've implemented a single sign-on (SSO) solution by deploying Active Directory Federation Services (AD FS) or greater in your on-premises organization, you must use **False** for the value of the **ForceChangePassword** attribute.</span></span>          |<span data-ttu-id="c63ee-179">省略可能</span><span class="sxs-lookup"><span data-stu-id="c63ee-179">Optional</span></span>  <br/> |
   
 <span data-ttu-id="c63ee-180">**CSV ファイル形式**</span><span class="sxs-lookup"><span data-stu-id="c63ee-180">**CSV file format**</span></span>
  
<span data-ttu-id="c63ee-181">Here's an example of the format for the CSV file.</span><span class="sxs-lookup"><span data-stu-id="c63ee-181">Here's an example of the format for the CSV file.</span></span> <span data-ttu-id="c63ee-182">In this example, three on-premises mailboxes are migrated to Office 365.</span><span class="sxs-lookup"><span data-stu-id="c63ee-182">In this example, three on-premises mailboxes are migrated to Office 365.</span></span>
  
<span data-ttu-id="c63ee-183">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow.</span><span class="sxs-lookup"><span data-stu-id="c63ee-183">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow.</span></span> <span data-ttu-id="c63ee-184">Each attribute name is separated by a comma.</span><span class="sxs-lookup"><span data-stu-id="c63ee-184">Each attribute name is separated by a comma.</span></span>
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

<span data-ttu-id="c63ee-185">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox.</span><span class="sxs-lookup"><span data-stu-id="c63ee-185">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox.</span></span> <span data-ttu-id="c63ee-186">The attribute values in each row must be in the same order as the attribute names in the header row.</span><span class="sxs-lookup"><span data-stu-id="c63ee-186">The attribute values in each row must be in the same order as the attribute names in the header row.</span></span> 
  
<span data-ttu-id="c63ee-187">Use any text editor, or an application like Excel , to create the CSV file.</span><span class="sxs-lookup"><span data-stu-id="c63ee-187">Use any text editor, or an application like Excel , to create the CSV file.</span></span> <span data-ttu-id="c63ee-188">Save the file as a .csv or .txt file.</span><span class="sxs-lookup"><span data-stu-id="c63ee-188">Save the file as a .csv or .txt file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c63ee-189">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding.</span><span class="sxs-lookup"><span data-stu-id="c63ee-189">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding.</span></span> <span data-ttu-id="c63ee-190">Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span><span class="sxs-lookup"><span data-stu-id="c63ee-190">Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span></span> 
  
### <a name="step-3-create-a-migration-endpoint"></a><span data-ttu-id="c63ee-191">ステップ 3:移行エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="c63ee-191">Step 3: Create a migration endpoint</span></span>
<span data-ttu-id="c63ee-192"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="c63ee-192"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="c63ee-193">To migrate email successfully, Office 365 needs to connect and communicate with the source email system.</span><span class="sxs-lookup"><span data-stu-id="c63ee-193">To migrate email successfully, Office 365 needs to connect and communicate with the source email system.</span></span> <span data-ttu-id="c63ee-194">To do this, Office 365 uses a migration endpoint.</span><span class="sxs-lookup"><span data-stu-id="c63ee-194">To do this, Office 365 uses a migration endpoint.</span></span> <span data-ttu-id="c63ee-195">To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="c63ee-195">To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="c63ee-196">移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=534750)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c63ee-196">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="c63ee-197">Exchange Online PowerShell に "StagedEndpoint" という Outlook Anywhere 移行エンドポイントを作成するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c63ee-197">To create an Outlook Anywhere migration endpoint called "StagedEndpoint" in Exchange Online PowerShell, run the following commands:</span></span>
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

<span data-ttu-id="c63ee-198">**New-MigrationEndpoint** コマンドレットの詳細については、「[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c63ee-198">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c63ee-199">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option.</span><span class="sxs-lookup"><span data-stu-id="c63ee-199">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option.</span></span> <span data-ttu-id="c63ee-200">Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span><span class="sxs-lookup"><span data-stu-id="c63ee-200">Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="c63ee-201">機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="c63ee-201">Verify it worked</span></span>

<span data-ttu-id="c63ee-202">Exchange Online PowerShell で、次のコマンドを実行して "StagedEndpoint" 移行エンドポイントに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c63ee-202">In Exchange Online PowerShell, run the following command to display information about the "StagedEndpoint" migration endpoint:</span></span>
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a><span data-ttu-id="c63ee-203">ステップ 4:段階的な移行のバッチを作成および開始する</span><span class="sxs-lookup"><span data-stu-id="c63ee-203">Step 4: Create and start a stage migration batch</span></span>
<span data-ttu-id="c63ee-204"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="c63ee-204"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="c63ee-205">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="c63ee-205">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration.</span></span> <span data-ttu-id="c63ee-206">You can create a migration batch and start it automatically by including the _AutoStart_ parameter.</span><span class="sxs-lookup"><span data-stu-id="c63ee-206">You can create a migration batch and start it automatically by including the _AutoStart_ parameter.</span></span> <span data-ttu-id="c63ee-207">Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c63ee-207">Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet.</span></span> <span data-ttu-id="c63ee-208">This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span><span class="sxs-lookup"><span data-stu-id="c63ee-208">This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

<span data-ttu-id="c63ee-209">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span><span class="sxs-lookup"><span data-stu-id="c63ee-209">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span> <span data-ttu-id="c63ee-210">Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c63ee-210">Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet.</span></span> <span data-ttu-id="c63ee-211">As previously stated, only one cutover migration batch can exist at a time.</span><span class="sxs-lookup"><span data-stu-id="c63ee-211">As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="c63ee-212">機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="c63ee-212">Verify it worked</span></span>

<span data-ttu-id="c63ee-213">Exchange Online PowerShell で次のコマンドを実行すると、「StagedBatch1」に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c63ee-213">Run the following command in Exchange Online PowerShell to display information about the "StagedBatch1":</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

<span data-ttu-id="c63ee-214">また、次のコマンドを実行すると、バッチが開始されたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="c63ee-214">You can also verify that the batch has started by running the following command:</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

<span data-ttu-id="c63ee-215">**Get-MigrationBatch** コマンドレットの詳細については、「[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c63ee-215">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a><span data-ttu-id="c63ee-216">ステップ 5:社内メールボックスをメールが有効なユーザーに変換する</span><span class="sxs-lookup"><span data-stu-id="c63ee-216">Step 5: Convert on-premises mailboxes to mail-enabled users</span></span>
<span data-ttu-id="c63ee-217"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="c63ee-217"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="c63ee-218">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail.</span><span class="sxs-lookup"><span data-stu-id="c63ee-218">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail.</span></span> <span data-ttu-id="c63ee-219">A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365.</span><span class="sxs-lookup"><span data-stu-id="c63ee-219">A user whose mailbox has been migrated now has both a mailbox on-premises and one in Office 365.</span></span> <span data-ttu-id="c63ee-220">Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox.</span><span class="sxs-lookup"><span data-stu-id="c63ee-220">Users who have a mailbox in Office 365 will stop receiving new mail in their on-premises mailbox.</span></span> 
  
<span data-ttu-id="c63ee-221">Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email.</span><span class="sxs-lookup"><span data-stu-id="c63ee-221">Because you are not done with your migrations, you are not yet ready to direct all users to Office 365 for their email.</span></span> <span data-ttu-id="c63ee-222">So what do you do for those people who have both?</span><span class="sxs-lookup"><span data-stu-id="c63ee-222">So what do you do for those people who have both?</span></span> <span data-ttu-id="c63ee-223">What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users.</span><span class="sxs-lookup"><span data-stu-id="c63ee-223">What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users.</span></span> <span data-ttu-id="c63ee-224">When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox.</span><span class="sxs-lookup"><span data-stu-id="c63ee-224">When you change from a mailbox to a mail-enabled user, you can direct the user to Office 365 for their email instead of going to their on-premises mailbox.</span></span> 
  
<span data-ttu-id="c63ee-225">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users.</span><span class="sxs-lookup"><span data-stu-id="c63ee-225">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Office 365 mailboxes by copying proxy addresses to the mail-enabled users.</span></span> <span data-ttu-id="c63ee-226">This lets you manage cloud-based users from your on-premises organization by using Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c63ee-226">This lets you manage cloud-based users from your on-premises organization by using Active Directory.</span></span> <span data-ttu-id="c63ee-227">Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c63ee-227">Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Office 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span></span>
    
### <a name="step-6-delete-a-staged-migration-batch"></a><span data-ttu-id="c63ee-228">ステップ 6:段階的な移行バッチを削除する</span><span class="sxs-lookup"><span data-stu-id="c63ee-228">Step 6: Delete a staged migration batch</span></span>
<span data-ttu-id="c63ee-229"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="c63ee-229"><a name="BK_Endpoint"> </a></span></span>

 <span data-ttu-id="c63ee-230">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch.</span><span class="sxs-lookup"><span data-stu-id="c63ee-230">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch.</span></span> <span data-ttu-id="c63ee-231">Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch.</span><span class="sxs-lookup"><span data-stu-id="c63ee-231">Be sure to verify that mail is being forwarded to the Office 365 mailboxes in the migration batch.</span></span> <span data-ttu-id="c63ee-232">When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span><span class="sxs-lookup"><span data-stu-id="c63ee-232">When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span></span>
  
<span data-ttu-id="c63ee-233">Exchange Online PowerShell で "StagedBatch1" 移行バッチを削除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c63ee-233">To delete the "StagedBatch1" migration batch in Exchange Online PowerShell, run the following command.</span></span>
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

<span data-ttu-id="c63ee-234">**Remove-MigrationBatch** コマンドレットの詳細については、「[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c63ee-234">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="c63ee-235">機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="c63ee-235">Verify it worked</span></span>

<span data-ttu-id="c63ee-236">Exchange Online PowerShell で次のコマンドを実行すると、"IMAPBatch1" に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c63ee-236">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch StagedBatch1
```

<span data-ttu-id="c63ee-237">このコマンドによって、状態が **Removing** の移行バッチが返されるか、移行バッチが見つからず、削除されたことの確認を求めるエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="c63ee-237">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="c63ee-238">**Get-MigrationBatch** コマンドレットの詳細については、「[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c63ee-238">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step7-assign-licenses-to-office-365-users"></a><span data-ttu-id="c63ee-239">ステップ 7:Office 365 ユーザーにライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="c63ee-239">Step7: Assign licenses to Office 365 users</span></span>
<span data-ttu-id="c63ee-240"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="c63ee-240"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="c63ee-241">ライセンスを割り当てて、移行されたアカウントの Office 365 のユーザー アカウントをアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="c63ee-241">Activate Office 365 user accounts for the migrated accounts by assigning licenses.</span></span> <span data-ttu-id="c63ee-242">ライセンスを割り当てないと、猶予期間 (30 日) が終了したときにメールボックスが無効になります。</span><span class="sxs-lookup"><span data-stu-id="c63ee-242">If you don't assign a license, the mailbox is disabled when the grace period (30 days) ends.</span></span> <span data-ttu-id="c63ee-243">Microsoft 365 管理センターでライセンスを割り当てるには、「[一般法人向け Office 365 ライセンスの割り当てまたは割り当て解除を行う](https://go.microsoft.com/fwlink/?LinkId=536681)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c63ee-243">To assign a license in the Microsoft 365 admin center, see [Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="c63ee-244">ステップ 8:移行後のタスクを完了する</span><span class="sxs-lookup"><span data-stu-id="c63ee-244">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="c63ee-245"><a name="BK_Postmigration"> </a></span><span class="sxs-lookup"><span data-stu-id="c63ee-245"><a name="BK_Postmigration"> </a></span></span>

- <span data-ttu-id="c63ee-246">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span><span class="sxs-lookup"><span data-stu-id="c63ee-246">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span></span> <span data-ttu-id="c63ee-247">After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients.</span><span class="sxs-lookup"><span data-stu-id="c63ee-247">After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients.</span></span> <span data-ttu-id="c63ee-248">This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization.</span><span class="sxs-lookup"><span data-stu-id="c63ee-248">This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization.</span></span> <span data-ttu-id="c63ee-249">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="c63ee-249">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="c63ee-250">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span><span class="sxs-lookup"><span data-stu-id="c63ee-250">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span></span> <span data-ttu-id="c63ee-251">The Autodiscover CNAME record must contain the following information:</span><span class="sxs-lookup"><span data-stu-id="c63ee-251">The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="c63ee-252">**エイリアス:** autodiscover</span><span class="sxs-lookup"><span data-stu-id="c63ee-252">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="c63ee-253">**ターゲット:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="c63ee-253">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="c63ee-254">詳細については、「[DNS レコードを管理するときに Office 365 の DNS レコードを作成する](https://go.microsoft.com/fwlink/p/?LinkId=535028)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c63ee-254">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="c63ee-255">**Decommission on-premises Exchange servers.**</span><span class="sxs-lookup"><span data-stu-id="c63ee-255">**Decommission on-premises Exchange servers.**</span></span> <span data-ttu-id="c63ee-256">After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span><span class="sxs-lookup"><span data-stu-id="c63ee-256">After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="c63ee-257">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c63ee-257">For more information, see the following:</span></span>
    
  - <span data-ttu-id="c63ee-258">「[Exchange 2010 の変更または削除](https://go.microsoft.com/fwlink/?LinkId=217936)」</span><span class="sxs-lookup"><span data-stu-id="c63ee-258">[Modify or Remove Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)</span></span>
    
  - <span data-ttu-id="c63ee-259">「[Exchange 2007 組織を削除する方法](https://go.microsoft.com/fwlink/?LinkID=100485)」</span><span class="sxs-lookup"><span data-stu-id="c63ee-259">[How to Remove an Exchange 2007 Organization](https://go.microsoft.com/fwlink/?LinkID=100485)</span></span>
    
  - <span data-ttu-id="c63ee-260">「[Exchange Server 2003 をアンインストールする方法](https://go.microsoft.com/fwlink/?LinkID=56561)」</span><span class="sxs-lookup"><span data-stu-id="c63ee-260">[How to Uninstall Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)</span></span>
    

