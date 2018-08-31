---
title: Office 365 のディレクトリ同期の計画
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Office 365、Active Directory のクリーンアップ、Azure Active Directory 接続ツールとディレクトリの同期について説明します。
ms.openlocfilehash: cc2a2ca050facaf53f0a235898c31ae7aaeff4ae
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541670"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a><span data-ttu-id="59880-103">Office 365 のディレクトリ同期の計画</span><span class="sxs-lookup"><span data-stu-id="59880-103">Plan for directory synchronization for Office 365</span></span>
<span data-ttu-id="59880-p101">によって、ビジネス ・ ニーズと技術的な要件では、ディレクトリ同期処理は、Office 365 に移行する企業のお客様の最も一般的なプロビジョニングの選択です。ディレクトリ同期により、オンプレミスの Active Directory で管理するユーザーとそのユーザーにすべての更新プログラムが Office 365 に同期されます。</span><span class="sxs-lookup"><span data-stu-id="59880-p101">Depending on business need and technical requirements, directory synchronization is the most common provisioning choice for enterprise customers who are moving to Office 365. Directory synchronization allows identities to be managed in the on-premises Active Directory and all updates to that identity are synchronized to Office 365 .</span></span>
  
<span data-ttu-id="59880-p102">いくつかのディレクトリの準備、および要件と Azure Active Directory の機能を含め、ディレクトリの同期の実装を計画する際に留意することがあります。ディレクトリの準備では、非常に多くの領域について説明します。属性の更新、監査、およびドメイン コント ローラー配置の計画が含まれます。要件と機能の計画には、multiforest/ディレクトリの場合、容量計画、および双方向同期を計画する必要なアクセス許可の決定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="59880-p102">There are a couple of things to keep in mind when you plan an implementation of directory synchronization, including directory preparation, and the requirements and functionality of the Azure Active Directory. Directory preparation covers quite a few areas. They include attribute updates, auditing, and planning domain controller placement. Planning requirements and functionality includes determining the permissions that are required, planning for multiforest/directory scenarios, capacity planning, and two-way synchronization.</span></span>
  
## <a name="office-365-identity-models"></a><span data-ttu-id="59880-110">Office 365 のユーザー モデル</span><span class="sxs-lookup"><span data-stu-id="59880-110">Office 365 identity models</span></span>
<span data-ttu-id="59880-111">Office 365 は、2 つの主な認証と id モデルを使用して: クラウドの認証と統合認証します。</span><span class="sxs-lookup"><span data-stu-id="59880-111">Office 365 uses two main authentication and identity models: cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="59880-112">クラウドの認証</span><span class="sxs-lookup"><span data-stu-id="59880-112">Cloud authentication</span></span>
<span data-ttu-id="59880-113">[クラウドのアイデンティティ](about-office-365-identity.md)を作成し、Office 365 の管理センターでユーザーを管理、ユーザーを管理するために、Windows PowerShell、または Active Directory の Azure を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="59880-113">[Cloud identity](about-office-365-identity.md) - create and manage users in the Office 365 admin center, you can also use Windows PowerShell, or Azure Active Directory to manage your users.</span></span> 
  
<span data-ttu-id="59880-p103">[シームレスなシングル サインオンとパスワードのハッシュが同期](about-office-365-identity.md)の Azure AD で設置ディレクトリ オブジェクトの認証を有効にする簡単な方法です。パスワード ハッシュ (PHS)、同期に、オンプレミスの Active Directory ユーザー アカウント オブジェクトを Office 365 と同期して、ユーザーの設置型の管理します。</span><span class="sxs-lookup"><span data-stu-id="59880-p103">[Password hash sync with seamless single sign-on](about-office-365-identity.md) - The simplest way to enable authentication for on-premises directory objects in Azure AD. With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises.</span></span> 
  
<span data-ttu-id="59880-116">Azure AD の認証サービスと直接ユーザーを検証するためにソフトウェア エージェントは、1 つまたは複数のオンプレミスのサーバーで実行されているを使用して単純なパスワードの検証を提供する[シームレスなシングル サインオンでのパススルー認証](about-office-365-identity.md)が、Active Directory を設置します。</span><span class="sxs-lookup"><span data-stu-id="59880-116">[Pass-through authentication with seamless single sign-on](about-office-365-identity.md) - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory.</span></span> 
  
### <a name="federated-authentication"></a><span data-ttu-id="59880-117">フェデレーション認証</span><span class="sxs-lookup"><span data-stu-id="59880-117">Federated authentication</span></span>
<span data-ttu-id="59880-118">[に Active Directory フェデレーション サービスの AD FS のフェデレーション id](about-office-365-identity.md)でより複雑な認証の要件を持つ大規模な組織に主に設置型のディレクトリ オブジェクトは、Office 365 と同期し、ユーザー アカウントは、マネージ設置します。</span><span class="sxs-lookup"><span data-stu-id="59880-118">[Federated identity with Active Directory Federation Services AD FS](about-office-365-identity.md) - Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises.</span></span> 
  
<span data-ttu-id="59880-119">[サード ・ パーティ製の認証と id プロバイダー](about-office-365-identity.md)の設置型のディレクトリ オブジェクトが Office 365 に同期させることがあり、クラウドのリソースへのアクセスは、主にサードパーティの id プロバイダー (IdP) によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="59880-119">[Third-party authentication and identity providers](about-office-365-identity.md) - On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> 
  
## <a name="active-directory-cleanup"></a><span data-ttu-id="59880-120">Active Directory のクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="59880-120">Active Directory Cleanup</span></span>
<span data-ttu-id="59880-121">同期を使用して Office 365 へのシームレスな移行を確保するためには、強くお勧め、Office 365 のディレクトリ同期の展開を開始する前に、Active Directory フォレストを準備することです。</span><span class="sxs-lookup"><span data-stu-id="59880-121">To help ensure a seamless transition to Office 365 by using synchronization, we highly recommend that you prepare your Active Directory forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="59880-p104">[ダウンロードして IdFix ツールを実行](install-and-run-idfix.md)するときの手順の 1 つは[Office 365 のディレクトリ同期を設定](set-up-directory-synchronization.md)すると、.[ディレクトリのクリーンアップ](prepare-directory-attributes-for-synch-with-idfix.md)を支援する IdFix ツールを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="59880-p104">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md). You can use the IdFix tool to help with the [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="59880-124">ディレクトリのクリーンアップは、次のタスクに集中する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59880-124">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="59880-125">**メタベース**および**userPrincipalName**属性の重複を削除します。</span><span class="sxs-lookup"><span data-stu-id="59880-125">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="59880-126">空白および無効な **userPrincipalName** 属性を有効な **userPrincipalName** 属性で更新します。</span><span class="sxs-lookup"><span data-stu-id="59880-126">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="59880-p105">**GivenName**姓 ( **sn** )、 **sAMAccountName**、**表示名**、**メール**、 **proxyAddresses**、 **mailNickname**、 **userPrincipalName**で信用できない無効な文字を削除します。属性。属性を準備する方法の詳細は、 [Azure Active Directory 同期ツールで同期する、属性の一覧](https://go.microsoft.com/fwlink/p/?LinkId=396719)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59880-p105">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes. For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="59880-129">これらは、Azure AD 接続を同期するのと同じ属性です。</span><span class="sxs-lookup"><span data-stu-id="59880-129">These are the same attributes that Azure AD Connect syncs.</span></span> 
  
## <a name="multiforest-deployment-considerations"></a><span data-ttu-id="59880-130">マルチフォレスト展開について考慮事項</span><span class="sxs-lookup"><span data-stu-id="59880-130">Multiforest Deployment Considerations</span></span>
<span data-ttu-id="59880-131">複数のフォレストと SSO オプションでは、 [Azure のインストールをユーザー設定の AD 接続](https://go.microsoft.com/fwlink/p/?LinkId=698430)を使用します。</span><span class="sxs-lookup"><span data-stu-id="59880-131">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="59880-132">組織に認証 (ログオン フォレスト) に複数のフォレストがある場合は、強くお勧め以下。</span><span class="sxs-lookup"><span data-stu-id="59880-132">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="59880-p106">**、フォレストの統合を評価します**。一般に、複数のフォレストを維持するために必要な多くのオーバーヘッドがあります。組織に別々 のフォレストが必要になるセキュリティ上の制約がある場合を除き、オンプレミス環境の簡素化を検討してください。</span><span class="sxs-lookup"><span data-stu-id="59880-p106">**Evaluate consolidating your forests.** In general, there's more overhead required to maintain multiple forests. Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="59880-p107">**プライマリ ログオン フォレスト内でのみ使用します**。Office 365 の初期ロールアウトは、優先的にログオンするフォレストでのみ Office 365 の展開を検討してください。</span><span class="sxs-lookup"><span data-stu-id="59880-p107">**Use only in your primary logon forest.** Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 
    
<span data-ttu-id="59880-138">複数フォレストの Active Directory の展開を統合することはできませんか id を管理するその他のディレクトリ サービスを使用している場合は、マイクロソフトまたはパートナーの支援によりこれらを同期することができます。</span><span class="sxs-lookup"><span data-stu-id="59880-138">If you can't consolidate your multiforest Active Directory deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="59880-139">詳細については、[シングル サインオンのシナリオでディレクトリ同期を複数のフォレスト](https://go.microsoft.com/fwlink/p/?LinkId=525321)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59880-139">For more information, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="59880-140">ディレクトリ統合ツール</span><span class="sxs-lookup"><span data-stu-id="59880-140">Directory integration tools</span></span>
<span data-ttu-id="59880-p108">ディレクトリが同期ディレクトリのオブジェクト (ユーザー、グループ、および連絡先) の同期、オンプレミスの Active Directory 環境から Office 365 のディレクトリ インフラストラクチャにします。[ディレクトリの統合ツール](https://go.microsoft.com/fwlink/p/?LinkID=510956)を使用できるツールとその機能の一覧についてを参照してください。使用することをお勧めのツールでは、 [Azure Active Directory の接続です](https://go.microsoft.com/fwlink/?LinkId=525323)。</span><span class="sxs-lookup"><span data-stu-id="59880-p108">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure. See [directory integration tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality. The recommended tool to use is [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323).</span></span>
  
<span data-ttu-id="59880-p109">ユーザー アカウントは、最初に Office 365 のディレクトリと同期は、ときに、非アクティブとしてマークされています。送信したり、電子メールを受信できないし、サブスクリプション ライセンスを消費しません。特定のユーザーに Office 365 のサブスクリプションを割り当てる準備ができたら、選択して、有効なライセンスを割り当てることによってそれらをアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59880-p109">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as non-activated. They cannot send or receive email, and they don't consume subscription licenses. When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by assigning a valid license.</span></span>
  
<span data-ttu-id="59880-147">ディレクトリ同期は、次の機能と機能の必要です。</span><span class="sxs-lookup"><span data-stu-id="59880-147">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="59880-148">SSO</span><span class="sxs-lookup"><span data-stu-id="59880-148">SSO</span></span>
    
- <span data-ttu-id="59880-149">Lync の共存</span><span class="sxs-lookup"><span data-stu-id="59880-149">Lync coexistence</span></span>
    
- <span data-ttu-id="59880-150">Exchange ハイブリッド展開を含みます。</span><span class="sxs-lookup"><span data-stu-id="59880-150">Exchange hybrid deployment, including:</span></span>
    
  - <span data-ttu-id="59880-151">完全に、オンプレミスの Exchange 環境と Office 365 の間でグローバル アドレス一覧 (GAL) を共有します。</span><span class="sxs-lookup"><span data-stu-id="59880-151">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="59880-152">他のメール システムの GAL 情報の同期。</span><span class="sxs-lookup"><span data-stu-id="59880-152">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="59880-p110">ユーザーを追加し、Office 365 サービスからユーザーを削除する機能。次必要があります。</span><span class="sxs-lookup"><span data-stu-id="59880-p110">The ability to add users to and remove users from Office 365 service offerings. This requires the following:</span></span>
  - <span data-ttu-id="59880-p111">ディレクトリ同期のセットアップ中に、双方向同期を構成しなければなりません。既定では、ディレクトリ同期ツールは、クラウドへの移行のみディレクトリ情報を記述します。双方向同期を構成するとき、オブジェクトの属性の数に制限が、クラウドからコピーし、書きして、ローカルの Active Directory に戻すように、書き戻し機能が有効にします。書き戻しは、Exchange ハイブリッド モードとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="59880-p111">Two-way synchronization must be configured during directory synchronization setup. By default, directory synchronization tools write directory information only to the cloud. When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local Active Directory. Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="59880-159">オンプレミス Exchange ハイブリッド展開</span><span class="sxs-lookup"><span data-stu-id="59880-159">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="59880-160">他のユーザーのメールボックスの設置型を維持しながら Office 365 によってユーザーのメールボックスを移動する機能。</span><span class="sxs-lookup"><span data-stu-id="59880-160">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="59880-161">差出人セーフ リストと受信拒否リストの設置型は、Office 365 に複製されます。</span><span class="sxs-lookup"><span data-stu-id="59880-161">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="59880-162">基本的な委任と代理送信メールの機能。</span><span class="sxs-lookup"><span data-stu-id="59880-162">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="59880-163">オンプレミスで統合されたスマート カードまたは多要素認証ソリューションがあります。</span><span class="sxs-lookup"><span data-stu-id="59880-163">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
    
- <span data-ttu-id="59880-164">写真、サムネイル、会議室、およびセキュリティ グループの同期</span><span class="sxs-lookup"><span data-stu-id="59880-164">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>