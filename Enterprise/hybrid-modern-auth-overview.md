---
title: ハイブリッド現代の認証の概要とビジネスと Exchange サーバーの設置型の Skype で使用するための前提条件
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: 10/02/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
description: '現代の認証より安全なユーザー認証と承認を提供する id 管理の方法です。ビジネス サーバー設置型 Exchange サーバー設置とビジネスの混成のドメインを分割 Skype の Skype のハイブリッド展開で使用可能になります。この資料へのリンクでは、ドキュメントに関する最新の認証のセットアップと無効化の前提条件と関連するクライアント (例: Outlook、Skype クライアント) の情報の一部に関連します。'
ms.openlocfilehash: c10e5660d43ccce50497fccfd9d830d31ac07d55
ms.sourcegitcommit: c5761d3c41aa2d26815f0d24c73dbcd53ab37957
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "27371111"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a><span data-ttu-id="d7b1f-106">ハイブリッド現代の認証の概要とビジネスと Exchange サーバーの設置型の Skype で使用するための前提条件</span><span class="sxs-lookup"><span data-stu-id="d7b1f-106">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>

<span data-ttu-id="d7b1f-p102">現代の認証より安全なユーザー認証と承認を提供する id 管理の方法です。ビジネス サーバー設置と Exchange サーバーの設置型と同様、分割ドメインの Skype ビジネス混成の Skype の Office 365 のハイブリッド展開で使用可能になります。この資料へのリンクでは、ドキュメントに関する最新の認証のセットアップと無効化の前提条件と関連するクライアント (例: Outlook、Skype クライアント) の情報の一部に関連します。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-p102">Modern Authentication is a method of identity management that offers more secure user authentication and authorization. It's available for Office 365 hybrid deployments of Skype for Business server on-premises and Exchange server on-premises, as well as, split-domain Skype for Business hybrids. This article links to related docs about prerequisites, setup/disabling Modern Authentication, and to some of the related client (ex. Outlook and Skype clients) information.</span></span> 
  
- [<span data-ttu-id="d7b1f-111">現代の認証とは何ですか。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-111">What is Modern Authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [<span data-ttu-id="d7b1f-112">現代の認証を使用すると、変更は何ですか。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-112">What changes when I use Modern Authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [<span data-ttu-id="d7b1f-113">オンプレミス環境の最新の認証状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-113">Check the Modern Authentication status of your on-premises environment</span></span>](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [<span data-ttu-id="d7b1f-114">現代の認証の前提条件を満たしているか。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-114">Do you meet Modern Authentication prerequisites?</span></span>](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [<span data-ttu-id="d7b1f-115">始める前に他に何が必要でしょうか。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-115">What else do I need to know before I begin?</span></span>](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [<span data-ttu-id="d7b1f-116">現代の認証 Url の一覧</span><span class="sxs-lookup"><span data-stu-id="d7b1f-116">List of Modern Authentication URLs</span></span>](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a><span data-ttu-id="d7b1f-117">現代の認証とは何ですか。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-117">What is Modern Authentication?</span></span>
<span data-ttu-id="d7b1f-118"><a name="BKMK_WhatisModAuth"> </a></span><span class="sxs-lookup"><span data-stu-id="d7b1f-118"></span></span>

<span data-ttu-id="d7b1f-119">(ノート型コンピューターや携帯電話などの) クライアントとサーバー間の通信を話題にする場合、マイクロソフトは、'現代 ' の認証の語句を使用します。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-119">When talking about communication between a client (for example, your laptop or your phone) and a server, Microsoft uses the phrase 'Modern authentication'.</span></span>
  
<span data-ttu-id="d7b1f-p103">現代の認証は、認証と承認の方法と同様の場合によく使われるアクセス ポリシーに依存するいくつかのセキュリティ対策の組み合わせを総称する用語です。含まれています。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-p103">Modern authentication is an umbrella term for a combination of authentication and authorization methods, as well as some security measures that rely on access policies that you may already be familiar with. It includes:</span></span>
  
- <span data-ttu-id="d7b1f-122">**認証方法**: 多要素認証です。クライアント証明書ベースの認証です。Active Directory 認証ライブラリ ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx))。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-122">**Authentication methods**: Multi-factor Authentication; Client Certificate-based authentication; and the Active Directory Authentication Library ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx)).</span></span>
    
- <span data-ttu-id="d7b1f-123">**認証方式**: オープン認証 (OAuth) のマイクロソフトの実装です。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-123">**Authorization methods**: Microsoft's implementation of Open Authorization (OAuth).</span></span> 
    
- <span data-ttu-id="d7b1f-124">**条件付きアクセス ポリシー**: モバイル アプリケーションの管理 (MAM) と Azure Active Directory の条件付きアクセスします。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-124">**Conditional access policies**: Mobile Application Management (MAM) and Azure Active Directory Conditional Access.</span></span> 
    
<span data-ttu-id="d7b1f-125">管理者は多くのさまざまなツールとリソースをセキュリティで保護するのには両方設置 (Exchange およびビジネス用の Skype) に id 管理のより安全な方法が用意されていますを使用して、ハイブリッドを交換する、最新の認証とユーザー id を管理します。、およびビジネスのハイブリッド/分割ドメインのシナリオの Skype です。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-125">Managing user identities with Modern Authentication gives administrators many different tools to use when it comes to securing resources and offers more secure methods of identity management to both on-premises (Exchange and Skype for Business), Exchange hybrid, and Skype for Business hybrid/split-domain scenarios.</span></span>
  
<span data-ttu-id="d7b1f-p104">ビジネス用の Skype は、Exchange と緊密に動作をするためのログイン動作 Skype ビジネス クライアントのユーザーが参照してくださいの影響を受ける Exchange の最新の認証状態があります。これは、ビジネス ドメインを分割ハイブリッドに、Skype がある場合にも適用されます。また、Skype の最新の認証の使用をサポートしているビジネスのハイブリッドの種類とも呼ばれます、' 分割ドメイン ' (分割・ ドメインで、ビジネス オンラインの Skype とのビジネス上の prem、Skype の両方があり、ユーザーが両方の場所に置かれている)。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-p104">Be aware that because Skype for Business works closely with Exchange, the login behaviour Skype for Business client users will see will be effected by the Modern Authentication status of Exchange. This will also apply if you have a Skype for Business split-domain hybrid. Also, the type of Skype for Business Hybrid that supports the use of Modern Authentication is often called a 'split-domain' (in a split-domain, you have both Skype for Business Online and Skype for Business on-prem, and users are homed in both locations).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="d7b1f-p105">2017 年 8 月の現在オンライン ビジネスの Skype を含めるし、オンラインで交換できるすべての新しい Office 365 テナントが現代の認証が既定で有効になっているとご存知ですか。既存のテナントでは、既定の MA 状態の変更がありませんが、すべての新しいテナントは、上記を参照してくださいユーザー機能の拡張セットを自動的にサポートします。オンライン ビジネスの Skype の MA の状態を確認するには、グローバル管理者の資格情報を持つビジネス オンラインの PowerShell の Skype を使用できます。実行`Get-CsOAuthConfiguration`- ClientADALAuthOverride の出力を確認します。-ClientADALAuthOverride が可能な場合' '、現在の認証には。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-p105">Did you know that, as of August of 2017, all new Office 365 tenants that include Skype for Business online and Exchange online will have Modern Authentication enabled by default? Pre-existing tenants won't have a change in their default MA state, but all new tenants automatically support the expanded set of identity features you see listed above. To check your MA status for Skype for Business online, you can use Skype for Business online PowerShell with Global Admin credentials. Run `Get-CsOAuthConfiguration` to check the output of -ClientADALAuthOverride. If -ClientADALAuthOverride is 'Allowed' your Modern Authentication is on.</span></span> 
  
## <a name="what-changes-when-i-use-modern-authentication"></a><span data-ttu-id="d7b1f-134">現代の認証を使用すると、変更は何ですか。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-134">What changes when I use Modern Authentication?</span></span>
<span data-ttu-id="d7b1f-135"><a name="BKMK_WhatChanges"> </a></span><span class="sxs-lookup"><span data-stu-id="d7b1f-135"></span></span>

<span data-ttu-id="d7b1f-p106">ビジネスまたは Exchange サーバーの設置型の Skype で最新の認証を使用すると、あなたはまだ*認証*ユーザー設置が*承認する*ストーリー (ファイル、電子メールなど) のリソースの変更へのアクセス。これは最新の認証については、クライアントとサーバーの通信では、MA の結果を evoSTS (セキュリティ トークン サービス Azure AD で使用される) の構成中に実行される手順を実行、理由は、Skype のビジネスおよび Exchange サーバーの設置型の認証サーバーとして設定されています。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-p106">When using Modern Authentication with on-premises Skype for Business or Exchange server, you're still  *authenticating*  users on-premises, but the story of  *authorizing*  their access to resources (like files or emails) changes. This is why, though Modern Authentication is about client and server communication, the steps taken during configuring MA result in evoSTS (a Security Token Service used by Azure AD) being set as Auth Server for Skype for Business and Exchange server on-premises.</span></span> 
  
<span data-ttu-id="d7b1f-p107">EvoSTS への変更は、活用する OAuth (トークンの発行)、クライアントを認証するサーバーでの設置し、設置使用セキュリティ共通のメソッドのような多要素認証) の雲の中にもできます。さらに、evoSTS は、ユーザー要求の一部として、パスワードを入力しなくても、リソースへのアクセスを要求できるようにするためのトークンを発行します。ユーザーが置かれている場所に関係なく (オンラインのまたは設置型)、どの場所では、必要なリソースをホストしているに関係なく EvoSTS は現代の認証を構成したら、ユーザーとクライアントを承認するコアになります。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-p107">The change to evoSTS allows your on-premises servers to take advantage of OAuth (token issuance) for authorizing your clients, and also lets your on-premises use security methods common in the cloud (like Multi-factor Authentication). Additionally, the evoSTS issues tokens that allow users to request access to resources without supplying their password as part of the request. No matter where your users are homed (of online or on-premises), and no matter which location hosts the needed resource, EvoSTS will become the core of authorizing users and clients once Modern Authentication is configured.</span></span>
  
<span data-ttu-id="d7b1f-p108">ここでは、何かの例です。ビジネス クライアント用の Skype は、ユーザーの代理として予定表の情報を取得するのに Exchange サーバーにアクセスするのに必要がある、Active Directory 認証ライブラリ (ADAL) がこれを行うに使用されます。ADAL コード ライブラリは、OAuth のセキュリティ トークンを使用するクライアント アプリケーションに使用可能なディレクトリにセキュリティで保護されたリソースを作成です。ADAL OAuth トークン (パスワードの代わり)、リソースへのユーザー アクセスを許可するを交換してクレームを確認するのには。以前は、このような-- ユーザーの要求を検証し、必要なトークンを発行する方法を知っているサーバー--トランザクションの権限あった可能性がありますセキュリティ トークン サービスの設置型、または Active Directory フェデレーション サービスもします。ただし、最新の認証では、クラウド内の Azure Active Directory (Azure AD) とは、その機関が集中化されます。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-p108">Here's an example of what I mean. If Skype for Business client needs to access Exchange server to get calendar information on behalf of a user, it uses the Active Directory Authentication Library (ADAL) to do so. ADAL is a code library designed to make secured resources in your directory available to client applications using OAuth security tokens. ADAL works with OAuth to verify claims and to exchange tokens (rather than passwords), to grant a user access to a resource. In the past, the authority in a transaction like this one -- the server that knows how to validate user claims and issue the needed tokens -- might have been a Security Token Service on-premises, or even Active Directory Federation Services. However, Modern Authentication centralizes that authority with Azure Active Directory (Azure AD) in the Cloud.</span></span>
  
<span data-ttu-id="d7b1f-147">つまり、Exchange サーバーと Skype のビジネス環境が完全に設置型でも、認証サーバーがオンラインにして、オンプレミス環境を作成し、Office への接続を維持することが必要クラウド (と、Azure Active Directory インスタンスのディレクトリとして、サブスクリプションを使用する) で 365 サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-147">This also means that even though your Exchange server and Skype for Business environments may be entirely on-premises, the authorizing server will be online, and your on-premises environment must have the ability to create and maintain a connection to your Office 365 subscription in the Cloud (and the Azure Active Directory instance that your subscription uses as its directory).</span></span>
  
<span data-ttu-id="d7b1f-p109">何が変わらないか。分割ドメイン ハイブリッドまたは Skype を使用して、ビジネスおよび Exchange サーバーの設置型の中には、かどうかすべてのユーザーは最初*設置*を認証する必要があります。認証の最新のハイブリッド実装では、Lyncdiscovery 自動検出は、オンプレミスのサーバーをポイントします。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-p109">What doesn't change? Whether you're in a split-domain hybrid or using Skype for Business and Exchange server on-premises, all users must first authenticate  *on-premises*  . In a hybrid implementation of Modern Authentication, Lyncdiscovery and Autodiscovery point to your on-premises server.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="d7b1f-151">MA でサポートされているビジネス ・ トポロジーの特定の Skype を知っている場合は、[右側には、ここに記載されている](https://technet.microsoft.com/en-us/library/mt803262.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-151">If you need to know the specific Skype for Business topologies supported with MA, that's [documented right here](https://technet.microsoft.com/en-us/library/mt803262.aspx).</span></span>
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a><span data-ttu-id="d7b1f-152">オンプレミス環境の最新の認証状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-152">Check the Modern Authentication status of your on-premises environment</span></span>
<span data-ttu-id="d7b1f-153"><a name="BKMK_CheckStatus"> </a></span><span class="sxs-lookup"><span data-stu-id="d7b1f-153"></span></span>

<span data-ttu-id="d7b1f-p110">現代の認証は、サービスが OAuth と S2S を活用するときに使用される認証サーバーを変更、ためには、最新の認証がオンまたはオフのビジネス環境、Skype の知っている必要があります。ビジネス上のサーバーを設置型では、Exchange または Skype のステータスをチェックするには実行することによって、`Get-CSOAuthConfiguration`の PowerShell コマンドです。コマンドには、空の 'OAuthServers' プロパティが返されます、現代の認証が無効です。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-p110">Because Modern Authentication changes the authorization server used when services leverage OAuth/S2S, you need to know if Modern Authentication is On or Off for your Skype for Business and Exchange environment. You can check the status on your Exchange or Skype for Business servers, on premises, by running the `Get-CSOAuthConfiguration` command in PowerShell. If the command returns an empty 'OAuthServers' property, then Modern Authentication is disabled.</span></span>
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a><span data-ttu-id="d7b1f-157">現代の認証の前提条件を満たしているか。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-157">Do you meet Modern Authentication prerequisites?</span></span>

<span data-ttu-id="d7b1f-158">確認し、続行する前に、一覧からこれらの項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-158">Verify and check these items off your list before you continue:</span></span>
  
- <span data-ttu-id="d7b1f-159">**Skype ビジネスの特定の**</span><span class="sxs-lookup"><span data-stu-id="d7b1f-159">**Skype for Business specific**</span></span>
    
  - <span data-ttu-id="d7b1f-160">すべてのサーバーはデバイス サーバー 2015 CU5 を持つ必要がありますまたはそれ以降</span><span class="sxs-lookup"><span data-stu-id="d7b1f-160">All servers must have SFB Server 2015 CU5 or later</span></span>
    
  - <span data-ttu-id="d7b1f-161">**例外**の存続可能性ブランチ アプライアンス (SBA) は、(Lync 2013 に基づく) の現在のバージョンにすることができます</span><span class="sxs-lookup"><span data-stu-id="d7b1f-161">**Exception** - Survivability Branch Appliance (SBA) can be on the current version (based on Lync 2013)</span></span> 
    
  - <span data-ttu-id="d7b1f-162">SIP ドメインが Office 365 のフェデレーション ドメインとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-162">Your SIP domain is added as a Federated domain in Office 365</span></span>
    
  - <span data-ttu-id="d7b1f-163">Office 365 認証 Url (TCP 443) に、インターネットへの送信接続を持つ必要がありますすべてデバイス フロント エンドし、Office 365 の Url と IP 行 56 と ' 365 一般的な Microsoft Office オンライン '」の[の 125 でよく知られている証明書のルート Crl (TCP 80) が表示されます。アドレス範囲](urls-and-ip-address-ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-163">All SFB Front Ends must have connections outbound to the internet, to Office 365 Authentication URLs (TCP 443) and well known certificate root CRLs (TCP 80) listed in Rows 56 and 125 of the 'Microsoft 365 Common and Office Online' section of [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
    
 <span data-ttu-id="d7b1f-164">**メモ**ビジネスのフロント エンド サーバーについて、Skype は、インターネット アクセスにプロキシ サーバーを使用、する場合は、各フロント エンド用の web.config ファイルの構成セクションで使用されるプロキシ サーバーの IP とポート番号を入力してください。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-164">**Note** If your Skype for Business front-end servers use a proxy server for Internet access, the proxy server IP and Port number used must be entered in the configuration section of the web.config file for each front end.</span></span> 
  
- <span data-ttu-id="d7b1f-165">ビジネス サーバー ・ 2015\Web ・ Components\Web の C:\Program Files\Skype ticket\int\web.config</span><span class="sxs-lookup"><span data-stu-id="d7b1f-165">C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\int\web.config</span></span>
    
- <span data-ttu-id="d7b1f-166">ビジネス サーバー ・ 2015\Web ・ Components\Web の C:\Program Files\Skype ticket\ext\web.config</span><span class="sxs-lookup"><span data-stu-id="d7b1f-166">C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config</span></span>
    
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
> <span data-ttu-id="d7b1f-167">[Office 365 の Url と IP アドレスの範囲](urls-and-ip-address-ranges.md)に必要な Url の最新の番組で最新の RSS フィードを購読することを確認します。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-167">Be sure to subscribe to the RSS feed for [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md) to stay current with the latest listings of required URLs.</span></span> 
  
- <span data-ttu-id="d7b1f-168">**Exchange Server の特定**</span><span class="sxs-lookup"><span data-stu-id="d7b1f-168">**Exchange Server specific**</span></span>
    
  - <span data-ttu-id="d7b1f-169">いずれかの Exchange server 2013 CU19 を使用している、またはサーバー 2016 CU8 を交換し、アップします。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-169">You're using either Exchange server 2013 CU19 and up, or Exchange server 2016 CU8 and up.</span></span>
    
  - <span data-ttu-id="d7b1f-170">環境内の Exchange server 2010 ではありません。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-170">There is no Exchange server 2010 in the environment.</span></span>
    
  - <span data-ttu-id="d7b1f-p111">SSL オフロードが構成されていません。SSL ターミネーションと再暗号化がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-p111">SSL Offloading is not configured. SSL termination and re-encryption is supported.</span></span>
    
  - <span data-ttu-id="d7b1f-173">お客様の環境は、サーバーがインターネットに接続できるようにするのにはプロキシ サーバーのインフラストラクチャを利用して、イベントには、 [InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx)プロパティで定義されているプロキシ サーバーをすべての Exchange サーバーがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-173">In the event your environment utilizes a proxy server infrastructure to allow servers to connect to the Internet, be sure all Exchange servers have the proxy server defined in the [InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx) property.</span></span>
    
- <span data-ttu-id="d7b1f-174">**Exchange クライアントとプロトコルの要件**</span><span class="sxs-lookup"><span data-stu-id="d7b1f-174">**Exchange client and protocol requirements**</span></span>
  
  - <span data-ttu-id="d7b1f-175">以下のクライアントでは、最新の認証をサポートします。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-175">The following clients support modern authentication:</span></span>

  |<span data-ttu-id="d7b1f-176">**クライアント**</span><span class="sxs-lookup"><span data-stu-id="d7b1f-176">**Clients**</span></span>|<span data-ttu-id="d7b1f-177">**プライマリ プロトコル**</span><span class="sxs-lookup"><span data-stu-id="d7b1f-177">**Primary Protocol**</span></span>|<span data-ttu-id="d7b1f-178">**メモ**</span><span class="sxs-lookup"><span data-stu-id="d7b1f-178">**Notes**</span></span>|
  |:-----|:-----|:-----|
  |<span data-ttu-id="d7b1f-179">Outlook 2013、Outlook 2016</span><span class="sxs-lookup"><span data-stu-id="d7b1f-179">Outlook 2013 and Outlook 2016</span></span>  <br/> |<span data-ttu-id="d7b1f-180">MAPI over HTTP</span><span class="sxs-lookup"><span data-stu-id="d7b1f-180">MAPI over HTTP</span></span>  <br/> |<span data-ttu-id="d7b1f-181">HTTP 経由で MAPI は Exchange 内で通常有効になっている (true を設定して、Exchange 2013 の Service Pack 1 の上に新規インストール) は、これらのクライアントを最新の認証を利用するために有効にする必要があります。詳細については、 [Office 2013 および Office 2016 のクライアント アプリケーションの現在の認証のしくみ](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-181">MAPI over HTTP must be enabled within Exchange in order to leverage modern authentication with these clients (usually enabled or True for new installs of Exchange 2013 Service Pack 1 and above); for more information see [How modern authentication works for Office 2013 and Office 2016 client apps](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).</span></span>  <br/> <span data-ttu-id="d7b1f-182">Outlook での最低限必要なビルドを実行していることを確認します。[Windows インストーラー (MSI) を使用する Outlook のバージョンの最新の更新プログラム](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-182">Ensure you are running the minimum required build of Outlook; see [Latest updates for versions of Outlook that use Windows Installer (MSI)](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).</span></span>  <br/> |
  |<span data-ttu-id="d7b1f-183">Outlook 2016 for Mac</span><span class="sxs-lookup"><span data-stu-id="d7b1f-183">Outlook 2016 for Mac</span></span>  <br/> |<span data-ttu-id="d7b1f-184">Exchange Web サービス</span><span class="sxs-lookup"><span data-stu-id="d7b1f-184">Exchange Web Services</span></span>  <br/> |  <br/> |
  |<span data-ttu-id="d7b1f-185">iOS および Android 用の Outlook</span><span class="sxs-lookup"><span data-stu-id="d7b1f-185">Outlook for iOS and Android</span></span>  <br/> |  <br/> |<span data-ttu-id="d7b1f-186">詳細について[を使用するハイブリッド iOS および Android は、Outlook を使用して現代の認証](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-186">See [Using hybrid Modern Authentication with Outlook for iOS and Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) for more information.</span></span>  <br/> |
  |<span data-ttu-id="d7b1f-187">Exchange ActiveSync クライアント (たとえば、iOS11 のメール)</span><span class="sxs-lookup"><span data-stu-id="d7b1f-187">Exchange ActiveSync clients (e.g., iOS11 Mail)</span></span>  <br/> |<span data-ttu-id="d7b1f-188">Exchange ActiveSync</span><span class="sxs-lookup"><span data-stu-id="d7b1f-188">Exchange ActiveSync</span></span>  <br/> |<span data-ttu-id="d7b1f-189">現代の認証をサポートする Exchange ActiveSync クライアントは、最新の認証に基本認証から切り替えるには、プロファイルを作り直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-189">For Exchange ActiveSync clients that support modern authentication, you must recreate the profile in order to switch from basic authentication to modern authentication.</span></span>  <br/> |

- <span data-ttu-id="d7b1f-190">**一般的な前提条件**</span><span class="sxs-lookup"><span data-stu-id="d7b1f-190">**General prerequisites**</span></span>
    
  - <span data-ttu-id="d7b1f-191">ADFS を使用する場合 Windows 2012 R2 の ad FS の 3.0年が必要以上のフェデレーション</span><span class="sxs-lookup"><span data-stu-id="d7b1f-191">If you use ADFS, you should have Windows 2012 R2 ADFS 3.0 and above for federation</span></span>
    
  - <span data-ttu-id="d7b1f-192">識別情報の構成は、AAD の接続がサポートする型のいずれか (など、パスワード ハッシュの同期、パススルー認証は、オンプレミス Office 365 でサポートされている STS、et cetera)。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-192">Your identity configurations are any of the types supported by AAD Connect (such as password hash sync, pass-through authentication, on-premises STS supported by Office 365, et cetera.)</span></span>
    
  - <span data-ttu-id="d7b1f-193">AAD 接続の構成し、ユーザーの複製と同期の機能があります。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-193">You have AAD Connect configured and functioning for user replication and sync.</span></span>
    
  - <span data-ttu-id="d7b1f-194">そのハイブリッドは、オンプレミスと Office 365 の間で正常に動作を確認しました。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-194">You have verified that hybrid is working between your on-premises and Office 365:</span></span>
    
  - <span data-ttu-id="d7b1f-195">Exchange ハイブリッドの公式なサポート ステートメントでは、現在 CU または現在 CU - 1 のいずれかする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-195">Official support statement for Exchange hybrid says you must have either current CU or current CU - 1.</span></span>
    
  - <span data-ttu-id="d7b1f-196">作成ことを確認両方ハイブリッド テスト ユーザーと同様に、オンプレミスのテスト ユーザーが、Office 365 でホーム ログインできるように、Skype のビジネス デスクトップ クライアントの場合 Skype で最新の認証を使用するには) および Microsoft Outlook (そのために最新の認証を使用する場合交換)。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-196">Make sure both an on-premises test user, as well as a hybrid test user homed in Office 365, can login to the Skype for Business desktop client (if you want to use Modern Authentication with Skype) and Microsoft Outlook (if you want so use Modern Authentication with Exchange).</span></span>
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a><span data-ttu-id="d7b1f-197">始める前に他に何が必要でしょうか。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-197">What else do I need to know before I begin?</span></span>
<span data-ttu-id="d7b1f-198"><a name="BKMK_Whatelse"> </a></span><span class="sxs-lookup"><span data-stu-id="d7b1f-198"></span></span>

1. <span data-ttu-id="d7b1f-p112">設置型サーバーのすべてのシナリオを含む最新の認証の設置型の設定 (実際には、ビジネス用の Skype はサポートされているトポロジの一覧があります) のサーバーの認証と承認を担当するが、マイクロソフトのクラウド (になるようAAD のセキュリティ トークン サービス、'evoSTS' と呼ばれる)、Azure Active Directory (AAD) の Url または、設置、Skype のビジネスや Exchange によって使用される名前空間についての更新とします。したがって、オンプレミスのサーバーは、マイクロソフトのクラウドの依存関係をとる。この操作を実行すると考えることが 'ハイブリッド認証' を構成します。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-p112">All the scenarios for on-premises servers involve setting up Modern Authentication on-premises (in fact, for Skype for Business there is a list of Supported topologies) so that the server responsible for authentication and authorization is in the Microsoft Cloud (AAD's security token service, called 'evoSTS'), and updating Azure Active Directory (AAD) about the URLs or namespaces used by your on-premises installation of either Skype for Business or Exchange. Therefore, on-premises servers take on a Microsoft Cloud dependency. Taking this action could be considered configuring 'hybrid auth'.</span></span>
    
2. <span data-ttu-id="d7b1f-p113">この資料へのリンクを他のユーザーを選択するために (Skype ビジネスのためにのみ必要)、現代の認証のトポロジと操作方法がサポートされているセットアップ手順では、そのアウトラインを記事や手順、最新の認証を無効にする Exchange の設置型およびビジネス用の Skype 設置します。好きなサーバー環境の最新の認証を使用するため、本拠地を必要とする場合、お使いのブラウザーでこのページです。</span><span class="sxs-lookup"><span data-stu-id="d7b1f-p113">This article links out to others that will help you choose supported Modern Authentication topologies (necessary only for Skype for Business), and how-to articles that outline the setup steps, or steps to disable Modern Authentication, for Exchange on-premises and Skype for Business on-premises. Favourite this page in your browser if you're going to need a home-base for using Modern Authentication in your server environment.</span></span>
    
## <a name="list-of-modern-authentication-urls"></a><span data-ttu-id="d7b1f-204">現代の認証 Url の一覧</span><span class="sxs-lookup"><span data-stu-id="d7b1f-204">List of Modern Authentication URLs</span></span>
<span data-ttu-id="d7b1f-205"><a name="BKMK_URLListforMA"> </a></span><span class="sxs-lookup"><span data-stu-id="d7b1f-205"></span></span>

- [<span data-ttu-id="d7b1f-206">現代の認証を使用するオンプレミスの Exchange Server を構成する方法</span><span class="sxs-lookup"><span data-stu-id="d7b1f-206">How to configure Exchange Server on-premises to use Modern Authentication</span></span>](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [<span data-ttu-id="d7b1f-207">現代の認証でサポートされているビジネス ・ トポロジーの Skype</span><span class="sxs-lookup"><span data-stu-id="d7b1f-207">Skype for Business topologies supported with Modern Authentication</span></span>](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [<span data-ttu-id="d7b1f-208">現代の認証を使用する設置型のビジネスの Skype を構成する方法</span><span class="sxs-lookup"><span data-stu-id="d7b1f-208">How to configure Skype for Business on-premises to use Modern Authentication</span></span>](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [<span data-ttu-id="d7b1f-209">Skype for Business および Exchange からのハイブリッド先進認証の削除または無効化</span><span class="sxs-lookup"><span data-stu-id="d7b1f-209">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

