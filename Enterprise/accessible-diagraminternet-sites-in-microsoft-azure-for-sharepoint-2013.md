---
title: "アクセス可能な図 - SharePoint 2013 のための Microsoft Azure のインターネット サイト"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
description: "この資料は、「SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト」という名前の図のアクセス可能なテキスト バージョンです。"
ms.openlocfilehash: 59c84e34ab4d748a80ab0a597817ae4d3464a43c
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="55667-103">アクセス可能な図 - SharePoint 2013 のための Microsoft Azure のインターネット サイト</span><span class="sxs-lookup"><span data-stu-id="55667-103">Accessible diagram - Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="55667-104">**概要:** この資料は、「SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト」という名前の図のアクセス可能なテキスト バージョンです。</span><span class="sxs-lookup"><span data-stu-id="55667-104">**Summary:** This article is an accessible text version of the diagram named Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="55667-p101">このポスターは、一般向けインターネット サイトがクラウドの弾力性と顧客アカウント用の Microsoft Azure AD を活用することで得られるメリットについて説明し、図解しています。Azure からインターネット サイトが得られるメリットを説明する 6 つの異なるシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="55667-p101">This poster describes and illustrates how public-facing Internet sites benefit from cloud elasticity and Azure AD for customer accounts. There are six different scenarios that describe how Internet sites benefit from Azure:</span></span> 
  
- <span data-ttu-id="55667-107">ファーム トポロジを設計およびサイズ調整します。</span><span class="sxs-lookup"><span data-stu-id="55667-107">Design and size the farm topology.</span></span> 
    
- <span data-ttu-id="55667-108">Azure を微調整します。</span><span class="sxs-lookup"><span data-stu-id="55667-108">Fine-tune for Azure.</span></span> 
    
- <span data-ttu-id="55667-109">Active Directory モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="55667-109">Choose the Active Directory model.</span></span> 
    
- <span data-ttu-id="55667-110">ID 管理、ゾーン、認証を設計します。</span><span class="sxs-lookup"><span data-stu-id="55667-110">Design for identity management, zones, and authentication.</span></span> 
    
- <span data-ttu-id="55667-111">クロスサイト発行のためのサイトと URL を設計します。</span><span class="sxs-lookup"><span data-stu-id="55667-111">Design sites and URLs for cross-site publishing.</span></span> 
    
- <span data-ttu-id="55667-112">Azure 環境を設計します。</span><span class="sxs-lookup"><span data-stu-id="55667-112">Design the Azure environment.</span></span> 
    
## <a name="design-and-size-the-farm-topology"></a><span data-ttu-id="55667-113">ファーム トポロジを設計およびサイズ調整する</span><span class="sxs-lookup"><span data-stu-id="55667-113">Design and size the farm topology</span></span>

<span data-ttu-id="55667-114">TechNet で SharePoint 2013 のトポロジ、キャパシティ、パフォーマンスのガイダンスを参照して、ファームのトポロジを設計します。</span><span class="sxs-lookup"><span data-stu-id="55667-114">Use the topology, capacity, and performance guidance for SharePoint 2013 on TechNet to design the farm topology.</span></span> 
  
<span data-ttu-id="55667-115">設計するファームがキャパシティとパフォーマンスの目標を満たすようにします。</span><span class="sxs-lookup"><span data-stu-id="55667-115">Ensure the farm you design meets the objectives for capacity and performance.</span></span> 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a><span data-ttu-id="55667-116">例:中規模のインターネット サイト ファーム (1 秒間に最大 85 ページ表示可能)</span><span class="sxs-lookup"><span data-stu-id="55667-116">Example: Medium Internet Sites farm (~85 page views per second)</span></span>

<span data-ttu-id="55667-117">このファームは、フォールト トレランスを備えた SharePoint 2013 検索ファーム トポロジを提供します。これは、3,400,000 個のアイテムを含むコーパスに最適化されています。</span><span class="sxs-lookup"><span data-stu-id="55667-117">This farm provides a fault-tolerant SharePoint 2013 search farm topology that is optimized for a corpus that contains 3,400,000 items.</span></span> 
  
<span data-ttu-id="55667-118">この例におけるファームは、言語に応じて 1 秒間に 100 ～ 200 個のドキュメントを処理します。さらに、1 秒間に 85 のページ ビューと 100 個のクエリに対応できます。</span><span class="sxs-lookup"><span data-stu-id="55667-118">The example farm processes 100-200 documents per second, depending on the language, and it accommodates 85 page views per second and 100 queries per second.</span></span> 
  
<span data-ttu-id="55667-119">付属図は 3 種類のサーバーのあるインターネット サイト ファームを示しています。</span><span class="sxs-lookup"><span data-stu-id="55667-119">The accompanying diagram shows a medium internet sites farm with three types of servers:</span></span> 
  
- <span data-ttu-id="55667-120">Web サーバー</span><span class="sxs-lookup"><span data-stu-id="55667-120">Web servers</span></span> 
    
- <span data-ttu-id="55667-121">アプリケーション サーバー</span><span class="sxs-lookup"><span data-stu-id="55667-121">Application servers</span></span> 
    
- <span data-ttu-id="55667-122">データベース サーバー</span><span class="sxs-lookup"><span data-stu-id="55667-122">Database servers</span></span> 
    
#### <a name="web-servers"></a><span data-ttu-id="55667-123">Web サーバー</span><span class="sxs-lookup"><span data-stu-id="55667-123">Web servers</span></span>

<span data-ttu-id="55667-p102">[Web サーバー] セクションには、ホスト A、ホスト B、ホスト C の 3 台の Web サーバーがあります。各 Web サーバーには、分散キャッシュ、ユーザー プロファイル、管理されたメタデータ、およびクエリ処理機能が含まれます。各サーバーには、インデックス パーティションのレプリカも含まれます。</span><span class="sxs-lookup"><span data-stu-id="55667-p102">In the web servers section, there are three web servers, Host A, Host B, and Host C. Each web server contains a distributed cache, user profiles, managed metadata, and query processing capabilities. They also contain an index partition replica that is in each server.</span></span> 
  
<span data-ttu-id="55667-126">スケール アウトのために、同じ機能を持つ Web サーバーを追加することにより、1 秒間に表示可能なページが 28 ページ増加します。</span><span class="sxs-lookup"><span data-stu-id="55667-126">To scale out, add an additional web server with the same capabilities, which allows for an additional 28 page views per second.</span></span> 
  
#### <a name="application-servers"></a><span data-ttu-id="55667-127">アプリケーション サーバー</span><span class="sxs-lookup"><span data-stu-id="55667-127">Application servers</span></span>

<span data-ttu-id="55667-p103">[アプリケーション サーバー] セクションには、ホスト D、ホスト E、ホスト F の 3 つのアプリケーション サーバーがあります。ホスト D には、クロール、管理、分析、コンテンツ処理コンポーネントが含まれます。ホスト E には、クロール、管理、およびコンテンツ処理コンポーネントが含まれます。ホスト F には、クロールおよびコンテンツ処理コンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="55667-p103">In the application servers section, there are three application servers, Host D, Host E, and Host F. Host D contains Crawl, Admin, Analytics, and Content processing components. Host E contains Crawl, Admin, and Content processing components. Host F contains Crawl and Content processing components.</span></span> 
  
<span data-ttu-id="55667-131">スケール アウトのために、クロール コンポーネントおよびコンテンツ処理コンポーネントを備えたアプリケーション サーバーを 1 台追加することにより、1 秒間に処理可能なドキュメントが 40 個増加します。</span><span class="sxs-lookup"><span data-stu-id="55667-131">To scale out, add one application server with a crawl component and a content processing component to process an additional 40 documents per second.</span></span> 
  
#### <a name="database-servers"></a><span data-ttu-id="55667-132">データベース サーバー</span><span class="sxs-lookup"><span data-stu-id="55667-132">Database servers</span></span>

<span data-ttu-id="55667-133">[データベース サーバー] セクションには、ホスト G とホスト H の 2 つのサーバーがあります。データベース サーバーは、フォールト トレランス用のペアのホストです。</span><span class="sxs-lookup"><span data-stu-id="55667-133">In the database servers section, there are two servers, Host G and Host H. The database servers are in paired hosts for fault tolerance.</span></span> 
  
<span data-ttu-id="55667-p104">ホスト G には、すべての SharePoint データベースがあります。それには、検索管理データベース、リンク データベース、2 つのクロール データベース、分析データベース、および他のすべての SharePoint データベースが含まれます。ホスト H には、すべての SharePoint データベースがあります。それには、SQL クラスタリング、ミラーリング、または SQL Server 2012 AlwaysOn を使用したすべてのデータベースの冗長コピーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="55667-p104">Host G contains all SharePoint database, including Search admin database, Link database, two Crawl databases, an Analytics database, and all other SharePoint databases. Host H contains all SharePoint databases, including redundant copies of all databases using SQL clustering, mirroring, or SQL Server 2012 AlwaysOn.</span></span> 
  
## <a name="fine-tune-for-azure"></a><span data-ttu-id="55667-136">Azure を微調整する</span><span class="sxs-lookup"><span data-stu-id="55667-136">Fine-tune for Azure</span></span>

<span data-ttu-id="55667-p105">SharePoint ファームを Azure プラットフォームで可用性セットのために微調整しなければならない場合があります。すべてのコンポーネントで高可用性を確保するには、サーバー ロールがすべて同じ構成になっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="55667-p105">The SharePoint farm might need to be fine-tuned for availability sets in the Azure platform. To ensure high availability of all components, ensure that the server roles are all identically configured.</span></span> 
  
<span data-ttu-id="55667-139">トポロジの例の図:</span><span class="sxs-lookup"><span data-stu-id="55667-139">In the example topology in the diagram:</span></span> 
  
- <span data-ttu-id="55667-140">Web サーバーとデータベース サーバーが同一の構成です。</span><span class="sxs-lookup"><span data-stu-id="55667-140">The web servers and the database servers are identically configured.</span></span> 
    
- <span data-ttu-id="55667-p106">3 つのアプリケーション サーバーの構成は同一ではありません。これらのサーバー ロールに関しては、Azure で可用性セット用に微調整が必要です。</span><span class="sxs-lookup"><span data-stu-id="55667-p106">The three application servers are not identically configured. These server roles require fine tuning for availability sets in Azure.</span></span> 
    
### <a name="before"></a><span data-ttu-id="55667-143">Before</span><span class="sxs-lookup"><span data-stu-id="55667-143">Before</span></span>

<span data-ttu-id="55667-p107">図の上部は、Azure で可用性セット用に微調整される前の SharePoint ファームを示しています。図の 3 つのホスト アプリケーション サーバーは同一の構成ではありません。コンポーネントの数は、ファームのパフォーマンスとパフォーマンスの目標によって決定されます。3 台のサーバーが次のように構成されています。</span><span class="sxs-lookup"><span data-stu-id="55667-p107">The top portion of the diagram shows the SharePoint farm before it has been fine-tuned for availability sets in Azure. In the diagram, the three host application servers are not identically configured. The number of components is determined by the performance and capacity targets for the farm. The three servers are configured as follows:</span></span> 
  
- <span data-ttu-id="55667-148">ホスト D アプリケーション サーバーは、クロール、管理、分析、およびコンテンツ処理の役割で構成されます。</span><span class="sxs-lookup"><span data-stu-id="55667-148">Host D application server is configured with Crawl, Admin, Analytics, and Content processing roles.</span></span> 
    
- <span data-ttu-id="55667-149">ホスト E アプリケーション サーバーは、クロール、管理、およびコンテンツ処理の役割で構成されます。</span><span class="sxs-lookup"><span data-stu-id="55667-149">Host E application server is configured with Crawl, Admin, and Content processing roles.</span></span> 
    
- <span data-ttu-id="55667-150">ホスト F アプリケーション サーバーは、クロールおよびコンテンツ処理の役割で構成されます。</span><span class="sxs-lookup"><span data-stu-id="55667-150">Host F application server is configured with Crawl and Content processing roles.</span></span> 
    
### <a name="after"></a><span data-ttu-id="55667-151">After</span><span class="sxs-lookup"><span data-stu-id="55667-151">After</span></span>

<span data-ttu-id="55667-p108">図のこの部分は、Azure で可用性セット用に微調整された後の SharePoint ファームを示しています。Azure でこのアーキテクチャを採用するには、3 つすべてのサーバーで 4 つのコンポーネントのレプリカを作成します。これにより、パフォーマンスとキャパシティに関して必要とされる以上にコンポーネント数が増えます。これは、これら 3 つの仮想マシンが 1 つの可用性セットに割り当てられる場合に、この設計で Azure プラットフォームの 4 つすべてのコンポーネントの高可用性を確保するためのトレードオフとなります。</span><span class="sxs-lookup"><span data-stu-id="55667-p108">This part of the diagram shows the SharePoint farm after it has been fine-tuned for availability sets in Azure. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span> 
  
<span data-ttu-id="55667-156">3 つのすべてのサーバーが、クロール、管理、分析、およびコンテンツ処理の役割を持つよう構成されます。</span><span class="sxs-lookup"><span data-stu-id="55667-156">The three servers are configured to all have the Crawl, Admin, Analytics, and Content processing roles.</span></span> 
  
## <a name="choose-the-active-directory-model"></a><span data-ttu-id="55667-157">Active Directory モデルを選択する</span><span class="sxs-lookup"><span data-stu-id="55667-157">Choose the Active Directory model</span></span>

<span data-ttu-id="55667-p109">すべての SharePoint ソリューションに Windows Active Directory ドメイン サービス (AD DS) が必要です。現在、Azure の SharePoint ソリューションには次の 2 つの選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="55667-p109">All SharePoint solutions require Windows Active Directory Domain Services (AD DS). At this time, there are two options for SharePoint solutions in Azure.</span></span> 
  
- <span data-ttu-id="55667-p110">オプション 1: 専用ドメイン  Azure に対して専用で独立したドメインを展開し、SharePoint ファームをサポートできます。一般のインターネット サイトに適しています。</span><span class="sxs-lookup"><span data-stu-id="55667-p110">Option 1: Dedicated domain — You can deploy a dedicated and isolated domain to Azure to support a SharePoint farm. This is a good choice for public-facing Internet sites.</span></span> 
    
- <span data-ttu-id="55667-p111">オプション 2: サイト間 VPN 接続を使用してオンプレミス ドメインを拡張します。サイト間 VPN 接続を介してオンプレミス ドメインを拡張すると、ユーザーはオンプレミスでホストされている場合と同じように SharePoint ファームにアクセスできます。既存の Active Directory および DNS の実装を活用できます。</span><span class="sxs-lookup"><span data-stu-id="55667-p111">Option 2: Extend the on-premises domain through a site-to-site VPN connection. When you extend the on-premises domain through a site-to-site VPN connection, users access the SharePoint farm as if it were hosted on-premises. You can take advantage of your existing Active Directory and DNS implementations.</span></span> 
    
## <a name="design-for-identity-management-zones-and-authentication"></a><span data-ttu-id="55667-165">ID 管理、ゾーン、認証を設計する</span><span class="sxs-lookup"><span data-stu-id="55667-165">Design for identity management, zones, and authentication</span></span>

### <a name="design-for-accounts-and-authentication"></a><span data-ttu-id="55667-166">アカウントと認証を設計する</span><span class="sxs-lookup"><span data-stu-id="55667-166">Design for accounts and authentication</span></span>

<span data-ttu-id="55667-167">アカウントを管理する方法と、使用する認証の種類を決定します。</span><span class="sxs-lookup"><span data-stu-id="55667-167">Determine how accounts will be managed and which type of authentication will be used.</span></span> 
  
#### <a name="accounts-for-site-developers-and-authors"></a><span data-ttu-id="55667-168">サイトの開発者と作成者のアカウント</span><span class="sxs-lookup"><span data-stu-id="55667-168">Accounts for site developers and authors</span></span>

- <span data-ttu-id="55667-169">Azure のドメインにアカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="55667-169">Add accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="55667-170">オンプレミスで Active Directory フェデレーション サービス (AD FS) を使用して、Azure 内のドメインに内部アカウントのフェデレーションを行います。</span><span class="sxs-lookup"><span data-stu-id="55667-170">Use Active Directory Federation Services (AD FS) on premises to federate the internal accounts to the domain in Azure.</span></span> 
    
- <span data-ttu-id="55667-171">サイト ツー サイト VPN 接続を設計する場合は、内部アカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="55667-171">If the design includes a site-to-site VPN connection, use the internal accounts.</span></span> 
    
#### <a name="accounts-for-customers"></a><span data-ttu-id="55667-172">お客様のアカウント</span><span class="sxs-lookup"><span data-stu-id="55667-172">Accounts for customers</span></span>

- <span data-ttu-id="55667-173">Azure Active Directory を使用します。</span><span class="sxs-lookup"><span data-stu-id="55667-173">Use Azure Active Directory.</span></span> 
    
- <span data-ttu-id="55667-174">別の SAML ベースのプロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="55667-174">Use a different SAML-based provider.</span></span> 
    
### <a name="design-for-zones"></a><span data-ttu-id="55667-175">ゾーンの設計</span><span class="sxs-lookup"><span data-stu-id="55667-175">Design for zones</span></span>

<span data-ttu-id="55667-176">SharePoint 2013 では、ID 管理はゾーン構成と認証に分けられています。</span><span class="sxs-lookup"><span data-stu-id="55667-176">In SharePoint 2013, identity management is factored into the configuration of zones and authentication.</span></span> 
  
<span data-ttu-id="55667-177">この設計は、顧客アカウントとそれ以外のアカウントを明確に分離します。</span><span class="sxs-lookup"><span data-stu-id="55667-177">This design provides clear separation of customer accounts from all other accounts.</span></span> 
  
- <span data-ttu-id="55667-178">この設計は、顧客アカウントを作成者やサイト開発者用の内部アカウントから完全に分離する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="55667-178">Use this design if you want customer accounts to be treated entirely different from the internal accounts for authors and site developers.</span></span> 
    
- <span data-ttu-id="55667-179">この設計を使用することで、Web アプリケーション内の顧客のアクションを制限するのにゾーンのポリシーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="55667-179">By using this design, you can use zone policies to limit customer actions within a web application.</span></span> 
    
- <span data-ttu-id="55667-180">このデザインでは、顧客アカウントと内部アカウントは別の URL になります。</span><span class="sxs-lookup"><span data-stu-id="55667-180">This design results in different URLs for customer accounts and internal accounts.</span></span> 
    
<span data-ttu-id="55667-181">この例では次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="55667-181">In this example:</span></span> 
  
- <span data-ttu-id="55667-182">内部アカウント用の既定のゾーンを構成します。</span><span class="sxs-lookup"><span data-stu-id="55667-182">Configure the default zone for internal accounts.</span></span> 
    
- <span data-ttu-id="55667-p112">顧客の認証済みアクセスのためのエクストラネット ゾーンを構成します。Azure Active Directory (AD) を顧客アカウントに使用するか、別の SAML ベースのプロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="55667-p112">Configure the extranet zone for customer authenticated access. Use Azure Active Directory (AD) for customer accounts, or use a different SAML-based provider.</span></span> 
    
- <span data-ttu-id="55667-185">匿名アクセスのためのインターネット ゾーンを構成します。</span><span class="sxs-lookup"><span data-stu-id="55667-185">Configure the Internet zone for anonymous access.</span></span> 
    
<span data-ttu-id="55667-186">すべての認証済みユーザーが既定のゾーンを使用するように構成する 2 ゾーンの設計は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="55667-186">Don't use a two-zone design in which all authenticated users are configured to use the default zone.</span></span> 
  
<span data-ttu-id="55667-187">付属図に、内部アカウントと顧客アカウントが分離された 3 ゾーン設計を示します。</span><span class="sxs-lookup"><span data-stu-id="55667-187">The accompanying diagram shows a three-zone design with separation of internal and customer accounts.</span></span> 
  
<span data-ttu-id="55667-p113">訪問者および顧客は、2 つのゾーンの 1 つにある Web アプリケーションから SharePoint 2013 ファームのAzure AD テナントにアクセスします。2 つのゾーンは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="55667-p113">Visitors and customers access the Azure AD Tenant in the SharePoint 2013 farm through web applications in one of two zones. The two zones include:</span></span> 
  
- <span data-ttu-id="55667-190">ゾーン:匿名ユーザーのためのインターネット</span><span class="sxs-lookup"><span data-stu-id="55667-190">Zone: Internet for anonymous users</span></span> 
    
- <span data-ttu-id="55667-191">ゾーン:認証されたユーザーのためのエクストラネット</span><span class="sxs-lookup"><span data-stu-id="55667-191">Zone: Extranet for authenticated users</span></span> 
    
<span data-ttu-id="55667-p114">内部アカウントを持つユーザーは、VPN トンネルから Azure AD を経由して、オンプレミス環境の AD DS および AD FS から Azure Active Directory テナントにアクセスします。既定のゾーンは、Windows 認証 (NTLM) を提供します。</span><span class="sxs-lookup"><span data-stu-id="55667-p114">Users with internal accounts access the Azure Active Directory Tenant from AD DS and AD FS in the on-premises environment through the VPN tunnel to Azure AD. The Default zone provides Windows Authentication (NTLM).</span></span> 
  
### <a name="design-for-connecting-to-azure-ad"></a><span data-ttu-id="55667-194">Azure AD に接続するために設計する</span><span class="sxs-lookup"><span data-stu-id="55667-194">Design for connecting to Azure AD</span></span>

 <span data-ttu-id="55667-p115">Azure AD は、クラウド サービスに ID 管理機能とアクセス制御機能を提供します。クラウド ベースのディレクトリ データ ストアや ID サービスのコア セット (ユーザー ログオン プロセス、認証サービス、AD FS) の機能があります。Azure AD に含まれる ID サービスは、オンプレミス Azure AD の展開と簡単に統合でき、サード パーティの ID プロバイダーを十分にサポートしています。</span><span class="sxs-lookup"><span data-stu-id="55667-p115">Azure AD provides identity management and access control capabilities for cloud services. Capabilities include a cloud-based store for directory data and a core set of identity services, including user logon processes, authentication services, and AD FS. The identity services that are included with Azure AD easily integrate with your on-premises AD DS deployments and fully support third-party identity providers.</span></span>
  
<span data-ttu-id="55667-198">付属の図は、次のシナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="55667-198">The accompanying diagram shows the following scenario:</span></span> 
  
<span data-ttu-id="55667-199">SharePoint 2013 と Azure Active Directory を統合する場合、Azure アクセス制御サービス (ACS) は 2 つの目的を果たします。</span><span class="sxs-lookup"><span data-stu-id="55667-199">When integrating SharePoint 2013 with Azure Active Directory, an Azure Access Control Service (ACS) serves two purposes:</span></span> 
  
-  <span data-ttu-id="55667-p116">Azure AD は SAML 2.0 を使用し、SharePoint は SAML 1.1 でのみ動作します。ACS は両方の形式を理解し、SharePoint と Azure AD のトークン形式を変換する中間コンポーネントとして機能します。</span><span class="sxs-lookup"><span data-stu-id="55667-p116">Azure AD uses SAML 2.0, and SharePoint only works with SAML 1.1. ACS understands both formats and serves as the intermediary to transform the token formats between SharePoint and Azure AD.</span></span>
    
- <span data-ttu-id="55667-202">ACS によって、この SAML シナリオでは ID プロバイダー セキュリティ トークン サービス (IP-STS) が不要になります。</span><span class="sxs-lookup"><span data-stu-id="55667-202">ACS replaces the need for the identity provider security token service (IP-STS) for this SAML scenario.</span></span> 
    
<span data-ttu-id="55667-203">詳細については、TechNet ライブラリの SharePoint 2013 での Azure AD の構成に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55667-203">For more information, see Configure Azure AD with SharePoint 2013 in the TechNet library.</span></span> 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a><span data-ttu-id="55667-204">クロスサイト発行のためのサイトと URL を設計する</span><span class="sxs-lookup"><span data-stu-id="55667-204">Design sites and URLs for cross-site publishing</span></span>

<span data-ttu-id="55667-205">発行のためのシナリオでは、1 つの Web アプリケーションの設計をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="55667-205">A one web-application design is recommended for publishing scenarios.</span></span> 
  
- <span data-ttu-id="55667-206">オーサリング サイトと公開サイトの両方が、同じ Web アプリケーションにあります。</span><span class="sxs-lookup"><span data-stu-id="55667-206">Both authoring and publishing sites are in the same web application.</span></span> 
    
- <span data-ttu-id="55667-207">クロスサイト発行は資産を公開する場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="55667-207">Cross-site publishing is used to publish assets.</span></span> 
    
<span data-ttu-id="55667-208">パス ベースでホスト名が付いたサイト コレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="55667-208">Use path-based and host-named site collections.</span></span> 
  
- <span data-ttu-id="55667-p117">ルート サイト コレクションが必要です。パス ベースのサイトとしてこのサイトを作成します。</span><span class="sxs-lookup"><span data-stu-id="55667-p117">A root site collection is a requirement. Create this site as a path-based site.</span></span> 
    
- <span data-ttu-id="55667-211">その他すべてのサイト コレクションをホスト名付きサイト コレクションとして作成します。</span><span class="sxs-lookup"><span data-stu-id="55667-211">Create all other site collections as host-named site collections.</span></span> 
    
<span data-ttu-id="55667-212">Web アプリケーションとルート サイトの URL</span><span class="sxs-lookup"><span data-stu-id="55667-212">Web application and root site URLs</span></span> 
  
- <span data-ttu-id="55667-p118">Web アプリケーションの URL には内部名を使用します。別の名前を指定しない場合、SharePoint では既定の名前としてローカル コンピューター名が使用されます。内部ネットワーク環境用に予約されているドメイン名を使用できます。</span><span class="sxs-lookup"><span data-stu-id="55667-p118">Use an internal name for the web application URL. SharePoint uses the local machine name as the default name unless a different name is specified. You can use a domain name that is reserved for the internal network environment.</span></span> 
    
- <span data-ttu-id="55667-p119">SharePoint では、Web アプリケーションの作成時に標準以外のポート番号が割り当てられます。ポート 80 やポート 443 の代わりに、このポート番号を使用します。または別の、標準以外のポート番号を使用します。</span><span class="sxs-lookup"><span data-stu-id="55667-p119">SharePoint assigns a nonstandard port number when the web application is created. Use this port number instead of port 80 or port 443. Or use a different but nonstandard port number.</span></span> 
    
- <span data-ttu-id="55667-219">パス ベースのサイト コレクションであるルート サイト コレクションに、同じ名前とポート番号を使用します。</span><span class="sxs-lookup"><span data-stu-id="55667-219">Use the same name and port number for the root site collection, which is a path-based site collection.</span></span> 
    
<span data-ttu-id="55667-p120">Web アプリケーションを使用してサイト コレクションとやり取りする検索などのアプリケーション プールサービスを付属図に示します。図のサイト コレクションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="55667-p120">The accompanying diagram shows application pool services such as Search interacting with site collections using web applications. The site collections shown include:</span></span> 
  
- <span data-ttu-id="55667-222">http://internal:8000 (ルート サイト) にあるパスベースのサイト コレクション。</span><span class="sxs-lookup"><span data-stu-id="55667-222">Path-based site collection located at http://internal:8000 (root site).</span></span> 
    
- <span data-ttu-id="55667-223">クロール:https://authoring.contoso.com:8000 などのアドレスにある、ホスト名が付いたサイト コレクション。</span><span class="sxs-lookup"><span data-stu-id="55667-223">Crawl: Host-named site collections located at an address such as https://authoring.contoso.com:8000.</span></span> 
    
- <span data-ttu-id="55667-224">クエリ:以下のようなアドレスにある、2 つの別々のホスト名が付いたサイト コレクション。</span><span class="sxs-lookup"><span data-stu-id="55667-224">Queries: 2 separate Host-named site collections located at addresses such as:</span></span> 
    
  - <span data-ttu-id="55667-225">http://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="55667-225">http://www.contoso.com</span></span> 
    
  - <span data-ttu-id="55667-226">https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="55667-226">https://secure.contoso.com</span></span> 
    
  - <span data-ttu-id="55667-227">http://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="55667-227">http://www.contoso.com:8000</span></span> 
    
  - <span data-ttu-id="55667-228">http://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="55667-228">http://assets.contoso.com</span></span> 
    
  - <span data-ttu-id="55667-229">https://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="55667-229">https://secureassets.contoso.com</span></span> 
    
  - <span data-ttu-id="55667-230">http://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="55667-230">http://assets.contoso.com:8000</span></span> 
    
## <a name="design-the-azure-environment"></a><span data-ttu-id="55667-231">Azure 環境を設計する</span><span class="sxs-lookup"><span data-stu-id="55667-231">Design the Azure environment</span></span>

<span data-ttu-id="55667-232">この例のアーキテクチャには次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="55667-232">This example architecture includes the following elements:</span></span> 
  
- <span data-ttu-id="55667-233">サイト間 VPN 接続はオプションであり、オンプレミス Windows AD DS と DNS の環境を Azure の仮想ネットワークに拡張します。</span><span class="sxs-lookup"><span data-stu-id="55667-233">A site-to-site VPN connection is optional and extends the on-premises Windows AD DS and DNS environment to the virtual network in Azure.</span></span> 
    
- <span data-ttu-id="55667-234">必要に応じて、SharePoint ファームをサポートするために Azure で専用のドメインを使用します。</span><span class="sxs-lookup"><span data-stu-id="55667-234">Optionally, use a dedicated domain in Azure to support the SharePoint farm.</span></span> 
    
- <span data-ttu-id="55667-235">サーバーは、Azure クラウド サービス間で役割に基づいて分割されます。</span><span class="sxs-lookup"><span data-stu-id="55667-235">Servers are split across Azure cloud services based on role.</span></span> 
    
- <span data-ttu-id="55667-236">可用性設定により、同一に構成されたサーバーの役割で高可用性が確保されます。</span><span class="sxs-lookup"><span data-stu-id="55667-236">Availability sets ensure high availability of identically configured server roles.</span></span> 
    
<span data-ttu-id="55667-237">詳細については、TechNet の以下の記事を参照してください。「SharePoint 2013 用の Microsoft Azure アーキテクチャ」。</span><span class="sxs-lookup"><span data-stu-id="55667-237">For more information, see the following article on TechNet: Azure Architectures for SharePoint Solutions.</span></span> 
  
<span data-ttu-id="55667-238">付属の図は、Azure の仮想ネットワークに接続するオンプレミス環境の例を示します。</span><span class="sxs-lookup"><span data-stu-id="55667-238">The accompanying diagram shows an example of an on-premises environment connecting with an Azure virtual network.</span></span> 
  
<span data-ttu-id="55667-239">オンプレミス環境には、Azure 環境のオプションの要素である次のコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="55667-239">Included in the on-premises environment, which is an optional element of the Azure environment, are the following components:</span></span> 
  
- <span data-ttu-id="55667-240">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="55667-240">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="55667-241">AD DS</span><span class="sxs-lookup"><span data-stu-id="55667-241">AD DS</span></span> 
    
- <span data-ttu-id="55667-242">Windows サーバーおよび AD DS からアクティブな VPN ゲートウェイのサブネットへの VPN ゲートウェイ</span><span class="sxs-lookup"><span data-stu-id="55667-242">A VPN gateway from Windows Server and AD DS to the Active VPN Gateway subnet</span></span> 
    
<span data-ttu-id="55667-243">Azure の仮想ネットワーク環境には、次のコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="55667-243">The Azure virtual network environment includes the following components:</span></span> 
  
- <span data-ttu-id="55667-244">アクティブな VPN ゲートウェイのサブネット (該当する場合、オンプレミス環境と重複)</span><span class="sxs-lookup"><span data-stu-id="55667-244">The Active VPN Gateway subnet (overlapping with the on-premises environment, if applicable)</span></span> 
    
- <span data-ttu-id="55667-245">AD DS および DNS の可用性セットが含まれているクラウド サービス (2 台のサーバー)</span><span class="sxs-lookup"><span data-stu-id="55667-245">Cloud service that includes AD DS and DNS availability set (two servers)</span></span> 
    
- <span data-ttu-id="55667-246">フロント エンド サーバーの可用性セットを含む (3 台の SharePoint サーバー) クラウド サービスとアプリケーション サーバーの可用性セット (3 台の SharePoint サーバー)</span><span class="sxs-lookup"><span data-stu-id="55667-246">Cloud service that include the front-end server availability set (three SharePoint servers) and the App server availability set (three SharePoint servers)</span></span> 
    
- <span data-ttu-id="55667-247">2 台のデータベースの可用性セットを含むクラウド サービス</span><span class="sxs-lookup"><span data-stu-id="55667-247">Cloud service that contains two database availability sets</span></span> 
    

