---
title: Office 用のディレクトリ同期の計画365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Office 365、Active directory クリーンアップ、および Azure active directory Connect ツールとのディレクトリ同期について説明します。
ms.openlocfilehash: 1a7c63f699c51c829aaab5b70cb6a1a203bca3be
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001830"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a><span data-ttu-id="e3ad4-103">Office 用のディレクトリ同期の計画365</span><span class="sxs-lookup"><span data-stu-id="e3ad4-103">Plan for directory synchronization for Office 365</span></span>

<span data-ttu-id="e3ad4-104">ビジネスニーズと技術上の要件に応じて、Office 365 に移行するエンタープライズお客様にとって最も一般的なプロビジョニングの選択として、ディレクトリ同期があります。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-104">Depending on business need and technical requirements, directory synchronization is the most common provisioning choice for enterprise customers who are moving to Office 365.</span></span> <span data-ttu-id="e3ad4-105">ディレクトリ同期を使用すると、オンプレミスの Active Directory で id を管理でき、その id に対するすべての更新が Office 365 に同期されます。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-105">Directory synchronization allows identities to be managed in the on-premises Active Directory and all updates to that identity are synchronized to Office 365.</span></span>
  
<span data-ttu-id="e3ad4-106">ディレクトリの準備を含むディレクトリ同期の実装を計画するときには、Azure Active directory の要件と機能について、いくつかの点に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-106">There are a couple of things to keep in mind when you plan an implementation of directory synchronization, including directory preparation, and the requirements and functionality of the Azure Active Directory.</span></span> <span data-ttu-id="e3ad4-107">ディレクトリの準備には、多くの領域が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-107">Directory preparation covers quite a few areas.</span></span> <span data-ttu-id="e3ad4-108">これには、属性の更新、監査、およびドメインコントローラーの配置計画が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-108">They include attribute updates, auditing, and planning domain controller placement.</span></span> <span data-ttu-id="e3ad4-109">要件と機能の計画には、必要なアクセス許可の決定、複数フォレスト/ディレクトリシナリオの計画、処理能力の計画、双方向同期などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-109">Planning requirements and functionality includes determining the permissions that are required, planning for multi-forest/directory scenarios, capacity planning, and two-way synchronization.</span></span>
  
## <a name="office-365-identity-models"></a><span data-ttu-id="e3ad4-110">Office 365 の id モデル</span><span class="sxs-lookup"><span data-stu-id="e3ad4-110">Office 365 identity models</span></span>

<span data-ttu-id="e3ad4-111">Office 365 では、2つの主要な認証と id モデルを使用しています。クラウド認証とフェデレーション認証です。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-111">Office 365 uses two main authentication and identity models: cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="e3ad4-112">クラウド認証</span><span class="sxs-lookup"><span data-stu-id="e3ad4-112">Cloud authentication</span></span>

<span data-ttu-id="e3ad4-113">[クラウド id](about-office-365-identity.md) -ユーザーの作成と管理[Microsoft 365 管理センター](https://admin.microsoft.com)では、Windows PowerShell または Azure Active Directory を使用してユーザーを管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-113">[Cloud identity](about-office-365-identity.md) - create and manage users in the [Microsoft 365 admin center](https://admin.microsoft.com), you can also use Windows PowerShell, or Azure Active Directory to manage your users.</span></span>
  
<span data-ttu-id="e3ad4-114">[シームレスなシングルサインオンを使用したパスワードハッシュ同期](about-office-365-identity.md)Azure AD でオンプレミスのディレクトリオブジェクトの認証を有効にする最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-114">[Password hash sync with seamless single sign-on](about-office-365-identity.md) - The simplest way to enable authentication for on-premises directory objects in Azure AD.</span></span> <span data-ttu-id="e3ad4-115">パスワードハッシュ同期 (phs) を使用して、オンプレミスの Active Directory ユーザーアカウントオブジェクトを Office 365 と同期し、オンプレミスでユーザーを管理します。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-115">With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises.</span></span>
  
<span data-ttu-id="e3ad4-116">[シームレスなシングルサインオンを使用したパススルー認証](about-office-365-identity.md)-1 つまたは複数のオンプレミスサーバーで実行されているソフトウェアエージェントを使用して Azure AD 認証サービスのパスワード検証を行い、ユーザーの直接の確認をオンプレミスの Active Directory。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-116">[Pass-through authentication with seamless single sign-on](about-office-365-identity.md) - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="e3ad4-117">フェデレーション認証</span><span class="sxs-lookup"><span data-stu-id="e3ad4-117">Federated authentication</span></span>

<span data-ttu-id="e3ad4-118">[Active Directory フェデレーションサービス AD FS を使用したフェデレーション id](about-office-365-identity.md) -主に、より複雑な認証要件を持つ大規模な企業組織では、オンプレミスのディレクトリオブジェクトは Office 365 と同期され、ユーザーアカウントはオンプレミスで管理されます。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-118">[Federated identity with Active Directory Federation Services AD FS](about-office-365-identity.md) - Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises.</span></span>
  
<span data-ttu-id="e3ad4-119">[サードパーティの認証および id プロバイダー](about-office-365-identity.md) -オンプレミスのディレクトリオブジェクトは、Office 365 に同期される場合があります。また、クラウドリソースへのアクセスは、主にサードパーティの id プロバイダー (IdP) によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-119">[Third-party authentication and identity providers](about-office-365-identity.md) - On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span>
  
## <a name="active-directory-cleanup"></a><span data-ttu-id="e3ad4-120">Active Directory のクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="e3ad4-120">Active Directory Cleanup</span></span>

<span data-ttu-id="e3ad4-121">同期を使用して office 365 にシームレスに移行できるようにするには、office 365 ディレクトリ同期の展開を開始する前に、Active Directory フォレストを準備することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-121">To help ensure a seamless transition to Office 365 by using synchronization, we highly recommend that you prepare your Active Directory forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="e3ad4-122">[Office 365 でディレクトリ同期](set-up-directory-synchronization.md)をセットアップする場合の手順の1つとして、 [idfix ツールをダウンロードして実行](install-and-run-idfix.md)する方法があります。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-122">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="e3ad4-123">idfix ツールを使用して、[ディレクトリのクリーンアップ](prepare-directory-attributes-for-synch-with-idfix.md)に役立てることができます。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-123">You can use the IdFix tool to help with the [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="e3ad4-124">ディレクトリのクリーンアップでは、次のタスクに焦点を当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-124">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="e3ad4-125">重複している**proxyAddress**属性と**userPrincipalName**属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-125">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="e3ad4-126">空白および無効な**userprincipalname**属性を有効な**userprincipalname**属性で更新します。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-126">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="e3ad4-127">**givenName**、姓 ( **sn** )、 **sAMAccountName**、 **displayName**、 **mail**、 **proxyAddresses**、 **mailNickname**、および**userPrincipalName**の無効な文字と疑わしい文字を削除するattributes.</span><span class="sxs-lookup"><span data-stu-id="e3ad4-127">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="e3ad4-128">属性の準備の詳細については、「 [Azure Active Directory 同期ツールによって同期される属性の一覧](https://go.microsoft.com/fwlink/p/?LinkId=396719)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-128">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="e3ad4-129">Azure AD Connect が同期するのと同じ属性です。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-129">These are the same attributes that Azure AD Connect syncs.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="e3ad4-130">複数フォレストの展開に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="e3ad4-130">Multi-forest Deployment Considerations</span></span>

<span data-ttu-id="e3ad4-131">複数のフォレストおよび SSO オプションでは、 [Azure AD Connect のカスタムインストール](https://go.microsoft.com/fwlink/p/?LinkId=698430)を使用します。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-131">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="e3ad4-132">組織に認証用に複数のフォレストがある場合 (ログオンフォレスト)、次のことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-132">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="e3ad4-133">**フォレストの統合を評価します。**</span><span class="sxs-lookup"><span data-stu-id="e3ad4-133">**Evaluate consolidating your forests.**</span></span> <span data-ttu-id="e3ad4-134">一般に、複数のフォレストを維持するには、より多くのオーバーヘッドが必要になります。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-134">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="e3ad4-135">個別のフォレストの必要性を判断するセキュリティ上の制約が組織にない限り、オンプレミスの環境を簡素化することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-135">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="e3ad4-136">**プライマリのログオンフォレストでのみ使用します。**</span><span class="sxs-lookup"><span data-stu-id="e3ad4-136">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="e3ad4-137">office 365 を最初に展開する場合は、プライマリのログオンフォレストにのみ office 365 を展開することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-137">Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 

<span data-ttu-id="e3ad4-138">複数フォレストの Active Directory 展開を統合できない場合や、他のディレクトリサービスを使用して id を管理している場合は、Microsoft またはパートナーのヘルプと同期することができます。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-138">If you can't consolidate your multi-forest Active Directory deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="e3ad4-139">詳細については、「[マルチフォレストディレクトリ同期とシングルサインオンシナリオ](https://go.microsoft.com/fwlink/p/?LinkId=525321)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-139">For more information, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="e3ad4-140">ディレクトリ統合ツール</span><span class="sxs-lookup"><span data-stu-id="e3ad4-140">Directory integration tools</span></span>

<span data-ttu-id="e3ad4-141">ディレクトリ同期とは、オンプレミスの Active directory 環境から Office 365 ディレクトリインフラストラクチャへのディレクトリオブジェクト (ユーザー、グループ、および連絡先) の同期です。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-141">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure.</span></span> <span data-ttu-id="e3ad4-142">使用可能なツールとその機能の一覧については、「[ディレクトリ統合ツール](https://go.microsoft.com/fwlink/p/?LinkID=510956)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-142">See [directory integration tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality.</span></span> <span data-ttu-id="e3ad4-143">使用する推奨ツールは、 [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323)です。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-143">The recommended tool to use is [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323).</span></span>
  
<span data-ttu-id="e3ad4-144">ユーザーアカウントが初めて Office 365 ディレクトリと同期されると、それらは非アクティブとしてマークされます。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-144">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as non-activated.</span></span> <span data-ttu-id="e3ad4-145">電子メールを送受信することはできません。サブスクリプションのライセンスは使用されません。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-145">They cannot send or receive email, and they don't consume subscription licenses.</span></span> <span data-ttu-id="e3ad4-146">Office 365 サブスクリプションを特定のユーザーに割り当てる準備ができたら、有効なライセンスを割り当てることによって、それらを選択してアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-146">When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by assigning a valid license.</span></span>
  
<span data-ttu-id="e3ad4-147">次の機能には、ディレクトリ同期が必要です。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-147">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="e3ad4-148">SSO</span><span class="sxs-lookup"><span data-stu-id="e3ad4-148">SSO</span></span>
- <span data-ttu-id="e3ad4-149">Skype の共存</span><span class="sxs-lookup"><span data-stu-id="e3ad4-149">Skype coexistence</span></span>
- <span data-ttu-id="e3ad4-150">Exchange ハイブリッド展開 (次のものが含まれる)</span><span class="sxs-lookup"><span data-stu-id="e3ad4-150">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="e3ad4-151">オンプレミスの Exchange 環境と Office 365 間の完全に共有されたグローバルアドレス一覧 (GAL)。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-151">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="e3ad4-152">別のメールシステムから GAL 情報を同期します。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-152">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="e3ad4-153">Office 365 サービスオファーリングにユーザーを追加したり、ユーザーを削除したりする機能。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-153">The ability to add users to and remove users from Office 365 service offerings.</span></span> <span data-ttu-id="e3ad4-154">これには、次のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-154">This requires the following:</span></span>
  - <span data-ttu-id="e3ad4-155">ディレクトリ同期のセットアップ中に、双ウェイの同期を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-155">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="e3ad4-156">既定では、ディレクトリ同期ツールは、ディレクトリ情報をクラウドにのみ書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-156">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="e3ad4-157">双ウェイの同期を構成する場合は、制限された数のオブジェクト属性がクラウドからコピーされるように書き戻し機能を有効にしてから、ローカルの Active Directory に書き戻します。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-157">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local Active Directory.</span></span> <span data-ttu-id="e3ad4-158">書き戻しは、Exchange ハイブリッドモードとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-158">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="e3ad4-159">オンプレミスの Exchange ハイブリッド展開</span><span class="sxs-lookup"><span data-stu-id="e3ad4-159">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="e3ad4-160">他のユーザーのメールボックスをオンプレミスに保持したまま、一部のユーザーメールボックスを Office 365 に移動する機能。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-160">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="e3ad4-161">社内の信頼できる差出人と受信拒否リストは、Office 365 に複製されます。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-161">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="e3ad4-162">基本的な委任および代理送信電子メール機能。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-162">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="e3ad4-163">オンプレミスのスマートカードまたは多要素認証ソリューションが統合されている。</span><span class="sxs-lookup"><span data-stu-id="e3ad4-163">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="e3ad4-164">写真、サムネイル、会議室、セキュリティグループの同期</span><span class="sxs-lookup"><span data-stu-id="e3ad4-164">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>