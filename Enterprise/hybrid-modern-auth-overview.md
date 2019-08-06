---
title: ハイブリッド先進認証の概要と、オンプレミスの Skype for Business および Exchange サーバーで使用するための前提条件
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
description: モダン認証は、よりセキュリティで保護されたユーザー認証と承認を提供する id 管理の方法です。 このサービスは、オンプレミスの Skype for Business server とオンプレミスの Exchange server のハイブリッド展開、およびスプリットドメインの Skype for Business ハイブリッドで利用できます。 この記事では、前提条件に関する関連ドキュメント、先進認証のセットアップ/無効化、および関連するクライアントのいくつか (例) へのリンクを示します。 Outlook および Skype クライアント) 情報。
ms.openlocfilehash: a8395a4d1bc212f23309b4ea273588d44eef69a3
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782457"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a><span data-ttu-id="917c6-106">ハイブリッド先進認証の概要と、オンプレミスの Skype for Business および Exchange サーバーで使用するための前提条件</span><span class="sxs-lookup"><span data-stu-id="917c6-106">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>

<span data-ttu-id="917c6-107">モダン認証は、よりセキュリティで保護されたユーザー認証と承認を提供する id 管理の方法です。</span><span class="sxs-lookup"><span data-stu-id="917c6-107">Modern Authentication is a method of identity management that offers more secure user authentication and authorization.</span></span> <span data-ttu-id="917c6-108">これは、オンプレミスの Skype for Business server とオンプレミスの Exchange server の Office 365 ハイブリッド展開、およびスプリットドメイン Skype for Business ハイブリッドで利用できます。</span><span class="sxs-lookup"><span data-stu-id="917c6-108">It's available for Office 365 hybrid deployments of Skype for Business server on-premises and Exchange server on-premises, as well as, split-domain Skype for Business hybrids.</span></span> <span data-ttu-id="917c6-109">この記事では、前提条件に関する関連ドキュメント、先進認証のセットアップ/無効化、および関連するクライアントのいくつか (例) へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="917c6-109">This article links to related docs about prerequisites, setup/disabling Modern Authentication, and to some of the related client (ex.</span></span> <span data-ttu-id="917c6-110">Outlook および Skype クライアント) 情報。</span><span class="sxs-lookup"><span data-stu-id="917c6-110">Outlook and Skype clients) information.</span></span> 
  
- [<span data-ttu-id="917c6-111">先進認証とは</span><span class="sxs-lookup"><span data-stu-id="917c6-111">What is Modern Authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [<span data-ttu-id="917c6-112">モダン認証を使用した場合の変更点</span><span class="sxs-lookup"><span data-stu-id="917c6-112">What changes when I use Modern Authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [<span data-ttu-id="917c6-113">オンプレミス環境の先進認証の状態を確認する</span><span class="sxs-lookup"><span data-stu-id="917c6-113">Check the Modern Authentication status of your on-premises environment</span></span>](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [<span data-ttu-id="917c6-114">先進認証の前提条件を満たしているか。</span><span class="sxs-lookup"><span data-stu-id="917c6-114">Do you meet Modern Authentication prerequisites?</span></span>](#do-you-meet-modern-authentication-prerequisites)
    
- [<span data-ttu-id="917c6-115">開始する前に知っておくべきその他の情報</span><span class="sxs-lookup"><span data-stu-id="917c6-115">What else do I need to know before I begin?</span></span>](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [<span data-ttu-id="917c6-116">モダン認証 Url の一覧</span><span class="sxs-lookup"><span data-stu-id="917c6-116">List of Modern Authentication URLs</span></span>](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a><span data-ttu-id="917c6-117">先進認証とは</span><span class="sxs-lookup"><span data-stu-id="917c6-117">What is Modern Authentication?</span></span>
<span data-ttu-id="917c6-118"><a name="BKMK_WhatisModAuth"> </a></span><span class="sxs-lookup"><span data-stu-id="917c6-118"></span></span>

<span data-ttu-id="917c6-119">クライアント (たとえば、ラップトップまたは電話) とサーバー間の通信について話す際、Microsoft では "モダン認証" という語句を使用しています。</span><span class="sxs-lookup"><span data-stu-id="917c6-119">When talking about communication between a client (for example, your laptop or your phone) and a server, Microsoft uses the phrase 'Modern authentication'.</span></span>
  
<span data-ttu-id="917c6-120">先進認証は、認証方法と承認方法の組み合わせに加えて、既に熟知している可能性のあるアクセスポリシーに依存するいくつかのセキュリティ対策をするための包括的な用語です。</span><span class="sxs-lookup"><span data-stu-id="917c6-120">Modern authentication is an umbrella term for a combination of authentication and authorization methods, as well as some security measures that rely on access policies that you may already be familiar with.</span></span> <span data-ttu-id="917c6-121">次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="917c6-121">It includes:</span></span>
  
- <span data-ttu-id="917c6-122">**認証方法**: 多要素認証。クライアント証明書ベースの認証。</span><span class="sxs-lookup"><span data-stu-id="917c6-122">**Authentication methods**: Multi-factor Authentication; Client Certificate-based authentication.</span></span>
    
- <span data-ttu-id="917c6-123">**承認方法**: Microsoft がオープン認証を実装しています (OAuth)。</span><span class="sxs-lookup"><span data-stu-id="917c6-123">**Authorization methods**: Microsoft's implementation of Open Authorization (OAuth).</span></span> 
    
- <span data-ttu-id="917c6-124">**条件付きアクセスポリシー**: モバイルアプリケーション管理 (MAM) と Azure Active Directory の条件付きアクセス。</span><span class="sxs-lookup"><span data-stu-id="917c6-124">**Conditional access policies**: Mobile Application Management (MAM) and Azure Active Directory Conditional Access.</span></span> 
    
<span data-ttu-id="917c6-125">モダン認証を使用してユーザー id を管理すると、リソースを保護し、オンプレミス (Exchange と Skype for business) の両方により安全な id 管理方法を提供するために、さまざまなツールを管理者に提供できます。、Skype for Business ハイブリッド/スプリットドメインシナリオ。</span><span class="sxs-lookup"><span data-stu-id="917c6-125">Managing user identities with Modern Authentication gives administrators many different tools to use when it comes to securing resources and offers more secure methods of identity management to both on-premises (Exchange and Skype for Business), Exchange hybrid, and Skype for Business hybrid/split-domain scenarios.</span></span>
  
<span data-ttu-id="917c6-126">Skype for Business は Exchange と密接に連携するため、Skype for business クライアントユーザーに表示されるログイン動作は、Exchange の先進認証状態によって影響を受けることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="917c6-126">Be aware that because Skype for Business works closely with Exchange, the login behaviour Skype for Business client users will see will be effected by the Modern Authentication status of Exchange.</span></span> <span data-ttu-id="917c6-127">このことは、Skype for Business の分割ドメインハイブリッドを使用している場合にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="917c6-127">This will also apply if you have a Skype for Business split-domain hybrid.</span></span> <span data-ttu-id="917c6-128">また、先進認証の使用をサポートする Skype for Business ハイブリッドの種類は、「スプリットドメイン」と呼ばれます (スプリットドメインでは、Skype for business Online と Skype for business の両方がオンプレミスで使用され、ユーザーは両方の場所に所属しています)。</span><span class="sxs-lookup"><span data-stu-id="917c6-128">Also, the type of Skype for Business Hybrid that supports the use of Modern Authentication is often called a 'split-domain' (in a split-domain, you have both Skype for Business Online and Skype for Business on-prem, and users are homed in both locations).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="917c6-129">2017年8月現在、Skype for Business online と Exchange online を含むすべての新しい Office 365 テナントでは、既定で先進認証が有効になっていることをご存知ですか?</span><span class="sxs-lookup"><span data-stu-id="917c6-129">Did you know that, as of August of 2017, all new Office 365 tenants that include Skype for Business online and Exchange online will have Modern Authentication enabled by default?</span></span> <span data-ttu-id="917c6-130">既存のテナントは既定の MA 状態に変更されませんが、すべての新しいテナントは上記に示した一連の拡張された id 機能を自動的にサポートしています。</span><span class="sxs-lookup"><span data-stu-id="917c6-130">Pre-existing tenants won't have a change in their default MA state, but all new tenants automatically support the expanded set of identity features you see listed above.</span></span> <span data-ttu-id="917c6-131">Skype for business online の MA の状態を確認するには、グローバル管理者の資格情報で Skype for Business online PowerShell を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="917c6-131">To check your MA status for Skype for Business online, you can use Skype for Business online PowerShell with Global Admin credentials.</span></span> <span data-ttu-id="917c6-132">を`Get-CsOAuthConfiguration`実行して、-ClientADALAuthOverride の出力を確認します。</span><span class="sxs-lookup"><span data-stu-id="917c6-132">Run `Get-CsOAuthConfiguration` to check the output of -ClientADALAuthOverride.</span></span> <span data-ttu-id="917c6-133">-ClientADALAuthOverride が ' Allowed ' の場合は、先進認証が有効になります。</span><span class="sxs-lookup"><span data-stu-id="917c6-133">If -ClientADALAuthOverride is 'Allowed' your Modern Authentication is on.</span></span> 
  
## <a name="what-changes-when-i-use-modern-authentication"></a><span data-ttu-id="917c6-134">モダン認証を使用した場合の変更点</span><span class="sxs-lookup"><span data-stu-id="917c6-134">What changes when I use Modern Authentication?</span></span>
<span data-ttu-id="917c6-135"><a name="BKMK_WhatChanges"> </a></span><span class="sxs-lookup"><span data-stu-id="917c6-135"></span></span>

<span data-ttu-id="917c6-136">オンプレミスの Skype for Business または Exchange server で先進認証を使用している場合でも、オンプレミスのユーザーを*認証*していますが、リソースへのアクセスを*承認*するためのストーリー (ファイルまたはメールなど) が変更されています。</span><span class="sxs-lookup"><span data-stu-id="917c6-136">When using Modern Authentication with on-premises Skype for Business or Exchange server, you're still  *authenticating*  users on-premises, but the story of  *authorizing*  their access to resources (like files or emails) changes.</span></span> <span data-ttu-id="917c6-137">このため、先進認証はクライアントとサーバーの通信に関するものですが、evoSTS (Azure AD によって使用されるセキュリティトークンサービス) では、認証サーバーとしてオンプレミスとして設定されているように、MA (Azure AD によって使用されるセキュリティトークンサービス) として設定されています。</span><span class="sxs-lookup"><span data-stu-id="917c6-137">This is why, though Modern Authentication is about client and server communication, the steps taken during configuring MA result in evoSTS (a Security Token Service used by Azure AD) being set as Auth Server for Skype for Business and Exchange server on-premises.</span></span> 
  
<span data-ttu-id="917c6-138">EvoSTS への変更により、オンプレミスのサーバーは、クライアントを承認するために OAuth (トークンの発行) を利用したり、オンプレミスのクラウドに共通のセキュリティメソッド (多要素認証など) を使用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="917c6-138">The change to evoSTS allows your on-premises servers to take advantage of OAuth (token issuance) for authorizing your clients, and also lets your on-premises use security methods common in the cloud (like Multi-factor Authentication).</span></span> <span data-ttu-id="917c6-139">また、evoSTS はトークンを発行して、ユーザーが要求の一部としてパスワードを入力せずに、リソースへのアクセスを要求できるようにします。</span><span class="sxs-lookup"><span data-stu-id="917c6-139">Additionally, the evoSTS issues tokens that allow users to request access to resources without supplying their password as part of the request.</span></span> <span data-ttu-id="917c6-140">ユーザーの所属先 (オンラインまたはオンプレミス) に関係なく、どの場所が必要なリソースをホストしているかにかかわらず、EvoSTS は、先進認証が構成されたときにユーザーとクライアントを承認する中心になります。</span><span class="sxs-lookup"><span data-stu-id="917c6-140">No matter where your users are homed (of online or on-premises), and no matter which location hosts the needed resource, EvoSTS will become the core of authorizing users and clients once Modern Authentication is configured.</span></span>
  
<span data-ttu-id="917c6-141">ここでの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="917c6-141">Here's an example of what I mean.</span></span> <span data-ttu-id="917c6-142">ユーザーに代わって予定表情報を取得するために Skype for Business クライアントが Exchange server にアクセスする必要がある場合は、Active Directory 認証ライブラリ (ADAL) を使用します。</span><span class="sxs-lookup"><span data-stu-id="917c6-142">If Skype for Business client needs to access Exchange server to get calendar information on behalf of a user, it uses the Active Directory Authentication Library (ADAL) to do so.</span></span> <span data-ttu-id="917c6-143">ADAL は、OAuth セキュリティトークンを使用して、クライアントアプリケーションがディレクトリ内のセキュリティで保護されたリソースを使用できるようにするためのコードライブラリです。</span><span class="sxs-lookup"><span data-stu-id="917c6-143">ADAL is a code library designed to make secured resources in your directory available to client applications using OAuth security tokens.</span></span> <span data-ttu-id="917c6-144">ADAL は OAuth と連携して、クレームを検証し、パスワードではなく exchange トークンを使用して、ユーザーがリソースにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="917c6-144">ADAL works with OAuth to verify claims and to exchange tokens (rather than passwords), to grant a user access to a resource.</span></span> <span data-ttu-id="917c6-145">以前は、このようなトランザクションの権限は、ユーザーの要求を検証し、必要なトークンを発行する方法を知っているサーバーであり、オンプレミスのセキュリティトークンサービス、または Active Directory フェデレーションサービスであった可能性があります。</span><span class="sxs-lookup"><span data-stu-id="917c6-145">In the past, the authority in a transaction like this one -- the server that knows how to validate user claims and issue the needed tokens -- might have been a Security Token Service on-premises, or even Active Directory Federation Services.</span></span> <span data-ttu-id="917c6-146">ただし、先進認証は、クラウド内の Azure Active Directory (Azure AD) を使用して、この権限を集中化します。</span><span class="sxs-lookup"><span data-stu-id="917c6-146">However, Modern Authentication centralizes that authority with Azure Active Directory (Azure AD) in the Cloud.</span></span>
  
<span data-ttu-id="917c6-147">これは、Exchange サーバーと Skype for Business 環境が完全にオンプレミスになっている場合でも、認証サーバーがオンラインになり、オンプレミスの環境で Office への接続を作成して管理できるようにする必要があることを意味します。クラウド内の365サブスクリプション (およびサブスクリプションがディレクトリとして使用する Azure Active Directory インスタンス)。</span><span class="sxs-lookup"><span data-stu-id="917c6-147">This also means that even though your Exchange server and Skype for Business environments may be entirely on-premises, the authorizing server will be online, and your on-premises environment must have the ability to create and maintain a connection to your Office 365 subscription in the Cloud (and the Azure Active Directory instance that your subscription uses as its directory).</span></span>
  
<span data-ttu-id="917c6-148">変更されないのはなぜですか?</span><span class="sxs-lookup"><span data-stu-id="917c6-148">What doesn't change?</span></span> <span data-ttu-id="917c6-149">分割ドメインハイブリッドにいるか、オンプレミスの Skype for Business と Exchange server を使用しているかにかかわらず、すべてのユーザーは最初*にオンプレミスで*認証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="917c6-149">Whether you're in a split-domain hybrid or using Skype for Business and Exchange server on-premises, all users must first authenticate  *on-premises*  .</span></span> <span data-ttu-id="917c6-150">先進認証のハイブリッド実装では、Lyncdiscovery と Autodiscovery はオンプレミスサーバーを指します。</span><span class="sxs-lookup"><span data-stu-id="917c6-150">In a hybrid implementation of Modern Authentication, Lyncdiscovery and Autodiscovery point to your on-premises server.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="917c6-151">MA でサポートされている特定の Skype for Business のトポロジを知る必要がある場合は、[ここに記載](https://technet.microsoft.com/en-us/library/mt803262.aspx)されています。</span><span class="sxs-lookup"><span data-stu-id="917c6-151">If you need to know the specific Skype for Business topologies supported with MA, that's [documented right here](https://technet.microsoft.com/en-us/library/mt803262.aspx).</span></span>
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a><span data-ttu-id="917c6-152">オンプレミス環境の先進認証の状態を確認する</span><span class="sxs-lookup"><span data-stu-id="917c6-152">Check the Modern Authentication status of your on-premises environment</span></span>
<span data-ttu-id="917c6-153"><a name="BKMK_CheckStatus"> </a></span><span class="sxs-lookup"><span data-stu-id="917c6-153"></span></span>

<span data-ttu-id="917c6-154">モダン認証は、サービスが OAuth/S2S を利用する際に使用される認証サーバーを変更するため、Skype for Business と Exchange 環境で先進認証がオンまたはオフになっているかどうかを知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="917c6-154">Because Modern Authentication changes the authorization server used when services leverage OAuth/S2S, you need to know if Modern Authentication is On or Off for your Skype for Business and Exchange environment.</span></span> <span data-ttu-id="917c6-155">PowerShell で`Get-CSOAuthConfiguration`コマンドを実行することにより、オンプレミスの Exchange サーバーまたは Skype for business サーバーの状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="917c6-155">You can check the status on your Exchange or Skype for Business servers, on premises, by running the `Get-CSOAuthConfiguration` command in PowerShell.</span></span> <span data-ttu-id="917c6-156">コマンドが空の ' OAuthServers ' プロパティを返す場合、モダン認証は無効になります。</span><span class="sxs-lookup"><span data-stu-id="917c6-156">If the command returns an empty 'OAuthServers' property, then Modern Authentication is disabled.</span></span>
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a><span data-ttu-id="917c6-157">先進認証の前提条件を満たしているか。</span><span class="sxs-lookup"><span data-stu-id="917c6-157">Do you meet Modern Authentication prerequisites?</span></span>

<span data-ttu-id="917c6-158">続行する前に、リストからこれらの項目を確認して確認してください。</span><span class="sxs-lookup"><span data-stu-id="917c6-158">Verify and check these items off your list before you continue:</span></span>
  
- <span data-ttu-id="917c6-159">**Skype for Business 固有**</span><span class="sxs-lookup"><span data-stu-id="917c6-159">**Skype for Business specific**</span></span>
    
  - <span data-ttu-id="917c6-160">すべてのサーバーに SFB Server 2015 CU5 以降がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="917c6-160">All servers must have SFB Server 2015 CU5 or later</span></span>
    
  - <span data-ttu-id="917c6-161">**例外**-存続性 Branch APPLIANCE (SBA) は現在のバージョンになります (Lync 2013 に基づいて)。</span><span class="sxs-lookup"><span data-stu-id="917c6-161">**Exception** - Survivability Branch Appliance (SBA) can be on the current version (based on Lync 2013)</span></span> 
    
  - <span data-ttu-id="917c6-162">Office 365 でフェデレーションドメインとして追加された SIP ドメイン</span><span class="sxs-lookup"><span data-stu-id="917c6-162">Your SIP domain is added as a Federated domain in Office 365</span></span>
    
  - <span data-ttu-id="917c6-163">すべての SFB フロントエンドは、インターネットへの接続を、office 365 認証 Url (TCP 443) および既知の証明書ルート Crl (TCP 80) のように、「Office の制限[url および IP アドレス」の「Microsoft 125 Common And Office」セクションの「56」および「365」に記載されている必要があります。範囲](urls-and-ip-address-ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="917c6-163">All SFB Front Ends must have connections outbound to the internet, to Office 365 Authentication URLs (TCP 443) and well known certificate root CRLs (TCP 80) listed in Rows 56 and 125 of the 'Microsoft 365 Common and Office' section of [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
- <span data-ttu-id="917c6-164">**ハイブリッド Office 365 環境の Skype for Business オンプレミス**</span><span class="sxs-lookup"><span data-stu-id="917c6-164">**Skype for Business on-premises in a hybrid Office 365 environment**</span></span>
  - <span data-ttu-id="917c6-165">Skype for business Server 2019 を Skype for business Server 2019 を実行しているすべてのサーバーと共に展開します。</span><span class="sxs-lookup"><span data-stu-id="917c6-165">A Skype for Business Server 2019 deployment with all servers running Skype for Business Server 2019.</span></span>
  
  - <span data-ttu-id="917c6-166">Skype for business Server 2015 を Skype for business Server 2015 を実行しているすべてのサーバーと共に展開します。</span><span class="sxs-lookup"><span data-stu-id="917c6-166">A Skype for Business Server 2015 deployment with all servers running Skype for Business Server 2015.</span></span>
  
  - <span data-ttu-id="917c6-167">以下にリストされているように、2つの異なるサーバーバージョンを持つ展開。</span><span class="sxs-lookup"><span data-stu-id="917c6-167">A deployment with a maximum of two different server versions as listed below:</span></span>
  
     - <span data-ttu-id="917c6-168">Skype for Business Server 2015 と Skype for business Server 2019</span><span class="sxs-lookup"><span data-stu-id="917c6-168">Skype for Business Server 2015 and Skype for Business Server 2019</span></span>
     
  - <span data-ttu-id="917c6-169">すべての Skype for Business サーバーに最新の cummulative 更新プログラムがインストールされている必要があります。使用可能なすべての更新プログラムを検索して管理するには、 [skype For Business Server 更新](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates)プログラムを参照してください</span><span class="sxs-lookup"><span data-stu-id="917c6-169">All Skype for Business servers must have the latest cummulative updates installed, see [Skype for Business Server updates](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates) to find and manage all available updates.</span></span>
  - <span data-ttu-id="917c6-170">ハイブリッド環境に Lync Server 2010 または2013がありません。</span><span class="sxs-lookup"><span data-stu-id="917c6-170">There is no Lync Server 2010 or 2013 in the hybrid environment.</span></span>
    
 <span data-ttu-id="917c6-171">**メモ**Skype for Business フロントエンドサーバーがインターネットアクセスにプロキシサーバーを使用している場合は、使用するプロキシサーバーの IP アドレスとポート番号を、各フロントエンドの web.config ファイルの構成セクションに入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="917c6-171">**Note** If your Skype for Business front-end servers use a proxy server for Internet access, the proxy server IP and Port number used must be entered in the configuration section of the web.config file for each front end.</span></span> 
  
- <span data-ttu-id="917c6-172">C:\Program Files\Skype for Business Server 2015 (Web Components\Web ticket\int\web.config</span><span class="sxs-lookup"><span data-stu-id="917c6-172">C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\int\web.config</span></span>
    
- <span data-ttu-id="917c6-173">C:\Program Files\Skype for Business Server 2015 (Web Components\Web ticket\ext\web.config</span><span class="sxs-lookup"><span data-stu-id="917c6-173">C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config</span></span>
    
```xml
<system.identityModel.services>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="http://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</system.identityModel.services>
```
    
> [!IMPORTANT]
> <span data-ttu-id="917c6-174">[Office 365 の url と IP アドレス範囲](urls-and-ip-address-ranges.md)の RSS フィードを購読して、必要な url の最新リストを最新の状態に保つようにしてください。</span><span class="sxs-lookup"><span data-stu-id="917c6-174">Be sure to subscribe to the RSS feed for [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md) to stay current with the latest listings of required URLs.</span></span> 
  
- <span data-ttu-id="917c6-175">**Exchange Server 固有**</span><span class="sxs-lookup"><span data-stu-id="917c6-175">**Exchange Server specific**</span></span>
    
  - <span data-ttu-id="917c6-176">Exchange server 2013 CU19 以上と up、または Exchange server 2016 CU8 と up のどちらかを使用している。</span><span class="sxs-lookup"><span data-stu-id="917c6-176">You're using either Exchange server 2013 CU19 and up, or Exchange server 2016 CU8 and up.</span></span>
    
  - <span data-ttu-id="917c6-177">環境内に Exchange server 2010 がありません。</span><span class="sxs-lookup"><span data-stu-id="917c6-177">There is no Exchange server 2010 in the environment.</span></span>
    
  - <span data-ttu-id="917c6-178">SSL オフロードが構成されていません。</span><span class="sxs-lookup"><span data-stu-id="917c6-178">SSL Offloading is not configured.</span></span> <span data-ttu-id="917c6-179">SSL の終了と再暗号化がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="917c6-179">SSL termination and re-encryption is supported.</span></span>
    
  - <span data-ttu-id="917c6-180">環境がプロキシサーバーインフラストラクチャを利用して、サーバーをインターネットに接続できるようにする場合は、すべての Exchange サーバーに[Internetwebproxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx)プロパティで定義されたプロキシサーバーがあることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="917c6-180">In the event your environment utilizes a proxy server infrastructure to allow servers to connect to the Internet, be sure all Exchange servers have the proxy server defined in the [InternetWebProxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx) property.</span></span>
  
- <span data-ttu-id="917c6-181">**ハイブリッド Office 365 環境の Exchange Server オンプレミス**</span><span class="sxs-lookup"><span data-stu-id="917c6-181">**Exchange Server on-premises in a hybrid Office 365 environment**</span></span>

  - <span data-ttu-id="917c6-182">Exchange server 2013 を使用している場合は、少なくとも1つのサーバーにメールボックスとクライアントアクセスサーバーの役割がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="917c6-182">If you are using Exchange server 2013, At least one server must have the Mailbox and Client Access server roles installed.</span></span> <span data-ttu-id="917c6-183">メールボックスとクライアントアクセスの役割を別々のサーバーにインストールすることもできますが、信頼性を高め、パフォーマンスを向上させるために、各サーバーに両方の役割をインストールすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="917c6-183">While it is possible to install the Mailbox and Client Access roles on separate servers, we strongly recommend that you install both roles on each server to provide additional reliability and improved performance.</span></span>
  
  - <span data-ttu-id="917c6-184">Exchange server 2016 以降のバージョンを使用している場合は、少なくとも1つのサーバーにメールボックスサーバーの役割がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="917c6-184">If you are using Exchange server 2016 or later version, at least one server must have the Mailbox server role installed.</span></span>
  
  - <span data-ttu-id="917c6-185">ハイブリッド環境では、Exchange server 2007 または2010はありません。</span><span class="sxs-lookup"><span data-stu-id="917c6-185">There is no Exchange server 2007 or 2010 in the Hybrid environment.</span></span>
  
  - <span data-ttu-id="917c6-186">すべての Exchange サーバーに最新の cummulative 更新プログラムがインストールされている必要があります。すべての利用可能な更新を検索して管理するには、「 [exchange を最新の累積更新プログラムにアップグレード](https://docs.microsoft.com/en-us/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019)する」を参照</span><span class="sxs-lookup"><span data-stu-id="917c6-186">All Exchange servers must have the latest cummulative updates installed, see [Upgrade Exchange to the latest Cumulative Updates](https://docs.microsoft.com/en-us/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019) to find and manage all available updates.</span></span>
    
- <span data-ttu-id="917c6-187">**Exchange クライアントとプロトコルの要件**</span><span class="sxs-lookup"><span data-stu-id="917c6-187">**Exchange client and protocol requirements**</span></span>
  
  - <span data-ttu-id="917c6-188">先進認証をサポートしているクライアントは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="917c6-188">The following clients support modern authentication:</span></span>

  |<span data-ttu-id="917c6-189">**クライアント**</span><span class="sxs-lookup"><span data-stu-id="917c6-189">**Clients**</span></span>|<span data-ttu-id="917c6-190">**プライマリプロトコル**</span><span class="sxs-lookup"><span data-stu-id="917c6-190">**Primary Protocol**</span></span>|<span data-ttu-id="917c6-191">**メモ**</span><span class="sxs-lookup"><span data-stu-id="917c6-191">**Notes**</span></span>|
  |:-----|:-----|:-----|
  |<span data-ttu-id="917c6-192">Outlook 2013、Outlook 2016</span><span class="sxs-lookup"><span data-stu-id="917c6-192">Outlook 2013 and Outlook 2016</span></span>  <br/> |<span data-ttu-id="917c6-193">MAPI over HTTP</span><span class="sxs-lookup"><span data-stu-id="917c6-193">MAPI over HTTP</span></span>  <br/> |<span data-ttu-id="917c6-194">これらのクライアントとの先進認証を利用するには、Exchange 内で MAPI over HTTP を有効にする必要があります (通常、Exchange 2013 Service Pack 1 以降の新規インストールでは有効または True)。詳細については[、「office 2013 および office 2016 クライアントアプリでの先進認証のしくみ](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="917c6-194">MAPI over HTTP must be enabled within Exchange in order to leverage modern authentication with these clients (usually enabled or True for new installs of Exchange 2013 Service Pack 1 and above); for more information see [How modern authentication works for Office 2013 and Office 2016 client apps](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).</span></span>  <br/> <span data-ttu-id="917c6-195">最低限必要な Outlook のビルドを実行していることを確認します。[Windows インストーラー (MSI) を使用するバージョンの Outlook については、「最新の更新プログラム」を](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi)参照してください。</span><span class="sxs-lookup"><span data-stu-id="917c6-195">Ensure you are running the minimum required build of Outlook; see [Latest updates for versions of Outlook that use Windows Installer (MSI)](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).</span></span>  <br/> |
  |<span data-ttu-id="917c6-196">Outlook 2016 for Mac</span><span class="sxs-lookup"><span data-stu-id="917c6-196">Outlook 2016 for Mac</span></span>  <br/> |<span data-ttu-id="917c6-197">Exchange Web サービス</span><span class="sxs-lookup"><span data-stu-id="917c6-197">Exchange Web Services</span></span>  <br/> |  <br/> |
  |<span data-ttu-id="917c6-198">iOS および Android 用の Outlook</span><span class="sxs-lookup"><span data-stu-id="917c6-198">Outlook for iOS and Android</span></span>  <br/> |  <br/> |<span data-ttu-id="917c6-199">詳細については[、「iOS および Android 用の Outlook でのハイブリッド先進認証の使用](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="917c6-199">See [Using hybrid Modern Authentication with Outlook for iOS and Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) for more information.</span></span>  <br/> |
  |<span data-ttu-id="917c6-200">Exchange ActiveSync クライアント (たとえば、iOS11 メール)</span><span class="sxs-lookup"><span data-stu-id="917c6-200">Exchange ActiveSync clients (e.g., iOS11 Mail)</span></span>  <br/> |<span data-ttu-id="917c6-201">Exchange ActiveSync</span><span class="sxs-lookup"><span data-stu-id="917c6-201">Exchange ActiveSync</span></span>  <br/> |<span data-ttu-id="917c6-202">先進認証をサポートする Exchange ActiveSync クライアントでは、基本認証からモダン認証に切り替えるためにプロファイルを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="917c6-202">For Exchange ActiveSync clients that support modern authentication, you must recreate the profile in order to switch from basic authentication to modern authentication.</span></span>  <br/> |

- <span data-ttu-id="917c6-203">**一般的な前提条件**</span><span class="sxs-lookup"><span data-stu-id="917c6-203">**General prerequisites**</span></span>
    
  - <span data-ttu-id="917c6-204">ADFS を使用する場合は、フェデレーションに Windows 2012 R2 ADFS 3.0 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="917c6-204">If you use ADFS, you should have Windows 2012 R2 ADFS 3.0 and above for federation</span></span>
    
  - <span data-ttu-id="917c6-205">Id 構成は、AAD Connect (パスワードハッシュ同期、パススルー認証、Office 365 でサポートされているオンプレミス STS、et cetera など) でサポートされている任意の種類のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="917c6-205">Your identity configurations are any of the types supported by AAD Connect (such as password hash sync, pass-through authentication, on-premises STS supported by Office 365, et cetera.)</span></span>
    
  - <span data-ttu-id="917c6-206">ユーザーのレプリケーションと同期のために、AAD Connect が構成され、機能している。</span><span class="sxs-lookup"><span data-stu-id="917c6-206">You have AAD Connect configured and functioning for user replication and sync.</span></span>
    
  - <span data-ttu-id="917c6-207">オンプレミスの環境と Office 365 環境の間で、Exchange の従来のハイブリッドトポロジモードを使用してハイブリッドが構成されていることを確認していること。</span><span class="sxs-lookup"><span data-stu-id="917c6-207">You have verified that hybrid is configured using Exchange Classic Hybrid Topology mode between your on-premises and Office 365 environment.</span></span> <span data-ttu-id="917c6-208">Exchange ハイブリッドの公式サポートステートメントは、現在の CU または現在の CU-1 のいずれかが必要であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="917c6-208">Official support statement for Exchange hybrid says you must have either current CU or current CU - 1.</span></span>
    
    > [!Note]
    > <span data-ttu-id="917c6-209">ハイブリッドの先進認証は、[ハイブリッドエージェント](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent)ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="917c6-209">Hybrid Modern Authentication is not supported with the [Hybrid Agent](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent).</span></span>
    
  - <span data-ttu-id="917c6-210">オンプレミスのテストユーザーと、Office 365 に所属するハイブリッドテストユーザーの両方が Skype for Business デスクトップクライアント (Skype で先進認証を使用する場合) と Microsoft Outlook (必要な場合) にログインできることを確認してください。Exchange)。</span><span class="sxs-lookup"><span data-stu-id="917c6-210">Make sure both an on-premises test user, as well as a hybrid test user homed in Office 365, can login to the Skype for Business desktop client (if you want to use Modern Authentication with Skype) and Microsoft Outlook (if you want so use Modern Authentication with Exchange).</span></span>
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a><span data-ttu-id="917c6-211">開始する前に知っておくべきその他の情報</span><span class="sxs-lookup"><span data-stu-id="917c6-211">What else do I need to know before I begin?</span></span>
<span data-ttu-id="917c6-212"><a name="BKMK_Whatelse"> </a></span><span class="sxs-lookup"><span data-stu-id="917c6-212"></span></span>

1. <span data-ttu-id="917c6-213">オンプレミスサーバーのすべてのシナリオには、オンプレミスの先進認証のセットアップが含まれています (実際には、サポートされるトポロジのリストがあります)。これにより、認証と承認を担当するサーバーが Microsoft Cloud (AAD のセキュリティトークンサービスを ' evoSTS ' と呼びます)、Skype for Business または Exchange のオンプレミスインストールで使用される Url または名前空間に関する Azure Active Directory (AAD) を更新します。</span><span class="sxs-lookup"><span data-stu-id="917c6-213">All the scenarios for on-premises servers involve setting up Modern Authentication on-premises (in fact, for Skype for Business there is a list of Supported topologies) so that the server responsible for authentication and authorization is in the Microsoft Cloud (AAD's security token service, called 'evoSTS'), and updating Azure Active Directory (AAD) about the URLs or namespaces used by your on-premises installation of either Skype for Business or Exchange.</span></span> <span data-ttu-id="917c6-214">そのため、オンプレミスサーバーは Microsoft クラウドの依存関係を利用します。</span><span class="sxs-lookup"><span data-stu-id="917c6-214">Therefore, on-premises servers take on a Microsoft Cloud dependency.</span></span> <span data-ttu-id="917c6-215">この操作を実行すると、' hybrid auth ' を構成することになります。</span><span class="sxs-lookup"><span data-stu-id="917c6-215">Taking this action could be considered configuring 'hybrid auth'.</span></span>
    
2. <span data-ttu-id="917c6-216">この記事では、サポートされている先進認証トポロジ (Skype for Business にのみ必要) を選択するのに役立つ他のユーザーや、セットアップ手順の概要または先進認証を無効にするための手順について説明する、Exchange オンプレミスの操作方法に関する記事にリンクしています。およびオンプレミスの Skype for Business。</span><span class="sxs-lookup"><span data-stu-id="917c6-216">This article links out to others that will help you choose supported Modern Authentication topologies (necessary only for Skype for Business), and how-to articles that outline the setup steps, or steps to disable Modern Authentication, for Exchange on-premises and Skype for Business on-premises.</span></span> <span data-ttu-id="917c6-217">サーバー環境で先進認証を使用するために、ホームベースが必要になる場合は、このページをブラウザーでお気に入りにしてください。</span><span class="sxs-lookup"><span data-stu-id="917c6-217">Favourite this page in your browser if you're going to need a home-base for using Modern Authentication in your server environment.</span></span>
    
## <a name="list-of-modern-authentication-urls"></a><span data-ttu-id="917c6-218">モダン認証 Url の一覧</span><span class="sxs-lookup"><span data-stu-id="917c6-218">List of Modern Authentication URLs</span></span>
<span data-ttu-id="917c6-219"><a name="BKMK_URLListforMA"> </a></span><span class="sxs-lookup"><span data-stu-id="917c6-219"></span></span>

- [<span data-ttu-id="917c6-220">モダン認証を使用するようにオンプレミスの Exchange Server を構成する方法</span><span class="sxs-lookup"><span data-stu-id="917c6-220">How to configure Exchange Server on-premises to use Modern Authentication</span></span>](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [<span data-ttu-id="917c6-221">先進認証でサポートされている Skype for Business のトポロジ</span><span class="sxs-lookup"><span data-stu-id="917c6-221">Skype for Business topologies supported with Modern Authentication</span></span>](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [<span data-ttu-id="917c6-222">Skype for Business のオンプレミスで先進認証を使用するように構成する方法</span><span class="sxs-lookup"><span data-stu-id="917c6-222">How to configure Skype for Business on-premises to use Modern Authentication</span></span>](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [<span data-ttu-id="917c6-223">Skype for Business および Exchange からのハイブリッド先進認証の削除または無効化</span><span class="sxs-lookup"><span data-stu-id="917c6-223">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

