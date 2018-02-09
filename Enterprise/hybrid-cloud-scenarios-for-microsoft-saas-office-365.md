---
title: "Microsoft SaaS (Office 365) のハイブリッド クラウド シナリオ"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: "概要: マイクロソフトの SaaS ベースの理解するハイブリッド アーキテクチャとシナリオ クラウドの製品 (Office 365)。"
ms.openlocfilehash: 65b1841a155e286af8862c2fb7c37d0bfb61e1e8
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="abeab-103">Microsoft SaaS (Office 365) のハイブリッド クラウド シナリオ</span><span class="sxs-lookup"><span data-stu-id="abeab-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="abeab-104">**の概要:**ハイブリッド アーキテクチャとシナリオを理解するマイクロソフトの SaaS ベースのクラウド ・ ソリューション (Office 365)。</span><span class="sxs-lookup"><span data-stu-id="abeab-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="abeab-105">クラウド移行または長期的な統合戦略の一環として、Exchange、SharePoint、または Skype for Business のオンプレミス展開を Office 365 内の対応する展開と組み合わせます。</span><span class="sxs-lookup"><span data-stu-id="abeab-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="abeab-106">Microsoft SaaS のハイブリッド シナリオ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="abeab-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="abeab-107">図 1 は、Microsoft SaaS ベースの Office 365 向けハイブリッド シナリオのアーキテクチャを示しています。</span><span class="sxs-lookup"><span data-stu-id="abeab-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="abeab-108">**Office 365 の図 1: マイクロソフトの SaaS ベースのハイブリッド シナリオ**</span><span class="sxs-lookup"><span data-stu-id="abeab-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Microsoft SaaS ベースの Office 365 向けハイブリッド シナリオ](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS.png)
  
<span data-ttu-id="abeab-110">アーキテクチャの各レイヤーについて:</span><span class="sxs-lookup"><span data-stu-id="abeab-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="abeab-111">アプリとシナリオ</span><span class="sxs-lookup"><span data-stu-id="abeab-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="abeab-112">SaaS ベースのさまざまなハイブリッド シナリオがあります。Office サーバー製品とそれに対応する Office 365 製品に沿って以下に示します。</span><span class="sxs-lookup"><span data-stu-id="abeab-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="abeab-113">Exchange Server を Exchange Online と組み合わせる (Exchange Server ハイブリッド)</span><span class="sxs-lookup"><span data-stu-id="abeab-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="abeab-114">Skype for Business Server を Skype for Business Online および新しいクラウド PBX とクラウド コネクタ エディションと組み合わせたシナリオ</span><span class="sxs-lookup"><span data-stu-id="abeab-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="abeab-115">SharePoint Server 2016 または SharePoint Server 2013 を SharePoint Online と組み合わせる (複数のシナリオ)</span><span class="sxs-lookup"><span data-stu-id="abeab-115">SharePoint Server 2016 or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="abeab-116">また、Exchange Online をオンプレミスの Skype for Business Server と組み合わせる製品間ハイブリッド シナリオもあります。</span><span class="sxs-lookup"><span data-stu-id="abeab-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="abeab-117">ID</span><span class="sxs-lookup"><span data-stu-id="abeab-117">Identity</span></span>
    
    <span data-ttu-id="abeab-p101">オンプレミスの Windows Server AD とのディレクトリ同期を含めることができます。代わりに、サード パーティの ID プロバイダーとフェデレーションを行うように Azure AD を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="abeab-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="abeab-120">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="abeab-120">Network</span></span>
    
    <span data-ttu-id="abeab-121">Office 365 か Dynamics 365 用の既存のインターネット パイプか、Microsoft ピアリングとの ExpressRoute 接続で構成されています。</span><span class="sxs-lookup"><span data-stu-id="abeab-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="abeab-122">オンプレミス</span><span class="sxs-lookup"><span data-stu-id="abeab-122">On-premises</span></span>
    
    <span data-ttu-id="abeab-p102">Exchange、SharePoint、Skype for Business の既存のサーバーで構成でき、これらの製品は最新バージョンに更新する必要があります。その後、ハイブリッド シナリオで Office 365 の対応する製品と組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="abeab-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="abeab-125">独自の[Office 365 の開発/テスト環境](office-365-dev-test-environment.md)を設定します。</span><span class="sxs-lookup"><span data-stu-id="abeab-125">Set up your own [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="skype-for-business-2015-hybrid"></a><span data-ttu-id="abeab-126">Skype for Business 2015 ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="abeab-126">Skype for Business 2015 Hybrid</span></span>

<span data-ttu-id="abeab-p103">ビジネス 2015年ハイブリッドの Skype を使用すると、オンライン ビジネスの Skype で既存のオンプレミスの展開を組み合わせることができます。一部のユーザー ホーム設置型で、一部のユーザーがオンラインで置かれているにもかかわらず、ユーザーが contoso.com など、同じセッション開始プロトコル (SIP) ドメインを共有します。このハイブリッド構成を使用すると、スケジュールに時間の経過と共に Office 365 の設置から移行します。ビジネス 2015年の Skype は、Exchange のオンラインとも統合できます。</span><span class="sxs-lookup"><span data-stu-id="abeab-p103">Skype for Business 2015 Hybrid allows you to combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business 2015 can also be integrated with Exchange Online.</span></span>
  
<span data-ttu-id="abeab-130">**図 2: ビジネス 2015年のハイブリッド構成の Skype**</span><span class="sxs-lookup"><span data-stu-id="abeab-130">**Figure 2: The Skype for Business 2015 hybrid configuration**</span></span>

![Skype for Business 2015 のハイブリッド構成](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB.png)
  
<span data-ttu-id="abeab-132">ビジネス 2015年のフロント エンド プール、エッジ サーバーとの通信 Skype Office 365 のオンライン ビジネスのため、設置型 Skype から成るビジネス 2015年ハイブリッド構成では、Skype を図 2 に示します。</span><span class="sxs-lookup"><span data-stu-id="abeab-132">Figure 2 shows the Skype for Business 2015 hybrid configuration, consisting of an on-premises Skype for Business 2015 front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="abeab-133">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abeab-133">For more information, see:</span></span>
  
- [<span data-ttu-id="abeab-134">Skype ビジネス サーバーとビジネス オンラインの Skype との間のハイブリッド接続を計画します。</span><span class="sxs-lookup"><span data-stu-id="abeab-134">Plan hybrid connectivity between Skype for Business Server and Skype for Business Online</span></span>](https://technet.microsoft.com/library/jj205403.aspx)
    
- [<span data-ttu-id="abeab-135">ビジネス サーバー 2015 の Skype のサポートされているハイブリッドの構成</span><span class="sxs-lookup"><span data-stu-id="abeab-135">Supported hybrid configurations for Skype for Business Server 2015</span></span>](https://technet.microsoft.com/library/jj945633.aspx)
    
- [<span data-ttu-id="abeab-136">Skype ビジネスのハイブリッド</span><span class="sxs-lookup"><span data-stu-id="abeab-136">Skype for Business Hybrid</span></span>](http://hybrid.office.com/skype-for-business/)
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="abeab-137">Skype for Business Server と組み合わされたクラウド PBX</span><span class="sxs-lookup"><span data-stu-id="abeab-137">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="abeab-138">Skype for Business Server と組み合わされたクラウド PBX を使用すると、既存の Skype for Business Server のオンプレミス展開を、オンプレミスの公衆交換電話網 (PSTN) 接続を備えたトポロジに移行できます。 </span><span class="sxs-lookup"><span data-stu-id="abeab-138">Cloud PBX with Skype for Business Server allows you to transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="abeab-139">**図 3: クラウド PBX ビジネス サーバーの Skype で**</span><span class="sxs-lookup"><span data-stu-id="abeab-139">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![Skype for Business Server と組み合わされたクラウド PBX](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SfB_CloudPBX.png)
  
<span data-ttu-id="abeab-141">図 3 は、Skype でクラウド PBX の設置では、Office 365 は、ビジネス用の Skype は、マイクロソフト クラウド PBX に接続されている既存の PBX または通信ゲートウェイ、ビジネスのサーバーで、Skype、PSTN のビジネス サーバー構成オンライン。</span><span class="sxs-lookup"><span data-stu-id="abeab-141">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="abeab-142">クラウドに所属する組織内のユーザーは、Microsoft クラウドから通知やボイスメールを含む構内交換機 (PBX) サービスを受信できますが、PSTN 接続 (ダイヤル トーン) はオンプレミスの Skype for Business Server 展開からエンタープライズ VoIP 経由で提供されます。</span><span class="sxs-lookup"><span data-stu-id="abeab-142">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="abeab-p104">これは、段階的にクラウド ベースのサービスに移行することを可能にするハイブリッド構成の優れた例です。Skype for Business Online への移動を開始するときに、ユーザーのボイス機能を保持することができます。所属する場所にかかわりなく、ユーザーの音声機能は継続されることがわかっているので、自分のペースでユーザーを移動させることができます。 </span><span class="sxs-lookup"><span data-stu-id="abeab-p104">This is a great example of a hybrid configuration that allows you to gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="abeab-146">詳細については、[サーバーのビジネスとビジネス オンラインまたは Lync Server 2013 の Skype の Skype 間のハイブリッド接続の計画](https://technet.microsoft.com/library/jj205403.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abeab-146">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online or Lync Server 2013](https://technet.microsoft.com/library/jj205403.aspx).</span></span>
  
<span data-ttu-id="abeab-147">既存の Lync Server または Skype for Business Server 展開がまだない場合は、クラウド PBX とのオンプレミス PSTN 接続を実装するパッケージ化された仮想マシン (VM) のセットである、Skype for Business クラウド コネクタ エディションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="abeab-147">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="abeab-148">詳細については、 [Skype ビジネス クラウド コネクタ ・ エディションの計画](https://technet.microsoft.com/library/mt605227.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abeab-148">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://technet.microsoft.com/library/mt605227.aspx).</span></span>
  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="abeab-149">SharePoint ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="abeab-149">SharePoint Hybrid</span></span>

<span data-ttu-id="abeab-150">SharePoint ハイブリッドは、両方のメリットを活かした接続エクスペリエンスを実現するために、Office 365 の SharePoint Online をオンプレミスの SharePoint ファームと組み合わせます。
</span><span class="sxs-lookup"><span data-stu-id="abeab-150">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="abeab-151">**図 4: SharePoint のハイブリッド構成**</span><span class="sxs-lookup"><span data-stu-id="abeab-151">**Figure 4: The SharePoint hybrid configuration**</span></span>

![SharePoint のハイブリッド構成](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_SP.png)
  
<span data-ttu-id="abeab-153">図 4 は、SharePoint Online では、Office 365 との通信、設置型の SharePoint ファームで構成される、SharePoint のハイブリッド構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="abeab-153">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="abeab-154">SharePoint ハイブリッド シナリオ</span><span class="sxs-lookup"><span data-stu-id="abeab-154">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="abeab-155">ビジネスのハイブリッド OneDrive</span><span class="sxs-lookup"><span data-stu-id="abeab-155">Hybrid OneDrive for Business</span></span>](https://technet.microsoft.com/library/mt147425%28v=office.16%29.aspx)
    
- [<span data-ttu-id="abeab-156">ハイブリッド チーム サイト</span><span class="sxs-lookup"><span data-stu-id="abeab-156">Hybrid team sites</span></span>](https://technet.microsoft.com/library/mt346110%28v=office.16%29.aspx)
    
- [<span data-ttu-id="abeab-157">エクストラネットの B2B のハイブリッド</span><span class="sxs-lookup"><span data-stu-id="abeab-157">Hybrid Extranet B2B</span></span>](https://support.office.com/article/SharePoint-Business-to-Business-Collaboration-Extranet-for-Partners-with-Office-365-7b087413-165a-4e94-8871-4393e0b9c037)
    
- [<span data-ttu-id="abeab-158">ハイブリッド検索</span><span class="sxs-lookup"><span data-stu-id="abeab-158">Hybrid search</span></span>](https://technet.microsoft.com/library/dn720906%28v=office.16%29.aspx)
    
- [<span data-ttu-id="abeab-159">ハイブリッド プロファイル</span><span class="sxs-lookup"><span data-stu-id="abeab-159">Hybrid profiles</span></span>](https://support.office.com/article/Plan-hybrid-profiles-96d1eaf0-94eb-40c5-ab76-c82907777db4)
    
- [<span data-ttu-id="abeab-160">ハイブリッドの選択</span><span class="sxs-lookup"><span data-stu-id="abeab-160">Hybrid Picker</span></span>](https://support.office.com/article/Hybrid-picker-in-the-SharePoint-Online-admin-center-efce8417-c9bc-4a2c-ac9d-cce6c4e84a9c)
    
    <span data-ttu-id="abeab-161">ハイブリッド シナリオは、Office 365 の SharePoint Online 管理センターから入手できる、ハイブリッド構成を自動化するウィザードを使用して、簡単に有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="abeab-161">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="abeab-162">拡張可能なハイブリッド アプリケーションの起動プログラム</span><span class="sxs-lookup"><span data-stu-id="abeab-162">Extensible hybrid app launcher</span></span>](https://support.office.com/article/The-extensible-hybrid-app-launcher-617a7cb5-53da-4128-961a-64a840c0ab91)
    
    <span data-ttu-id="abeab-163">ユーザーは Office 365 ビデオや Delve アプリを表示および使用し、オンプレミスの SharePoint ファームのページ内で体験することができます。</span><span class="sxs-lookup"><span data-stu-id="abeab-163">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="abeab-164">これらのすべての SharePoint ハイブリッド シナリオは、拡張可能なハイブリッド アプリ起動ツールを除き、SharePoint 2016 と SharePoint 2013 の両方のユーザーが使用できます。</span><span class="sxs-lookup"><span data-stu-id="abeab-164">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
<span data-ttu-id="abeab-165">詳細については、 [SharePoint のハイブリッド](http://hybrid.office.com/sharepoint/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abeab-165">For more information, see [SharePoint Hybrid](http://hybrid.office.com/sharepoint/).</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="abeab-166">Exchange Server 2016 ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="abeab-166">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="abeab-167">Exchange Server 2016 ハイブリッドを使用すると、オンライン ユーザーにとっての Office 365 の Exchange Online のメリットを実感できます。一方、オンプレミス ユーザーは既存の Exchange Server インフラストラクチャを引き続き使用します。 </span><span class="sxs-lookup"><span data-stu-id="abeab-167">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="abeab-168">**図 5: Exchange 2016 のハイブリッド構成**</span><span class="sxs-lookup"><span data-stu-id="abeab-168">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Exchange 2016 のハイブリッド構成](images/Hybrid_Poster/Hybrid_Cloud_Stack_SaaS_EX.png)
  
<span data-ttu-id="abeab-170">図 5 は、Exchange の 2016年ハイブリッドな構成、オンプレミスの Exchange メールボックス サーバーが Exchange のオンライン保護と Office 365 のメールボックスとの通信を示しています。</span><span class="sxs-lookup"><span data-stu-id="abeab-170">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="abeab-171">オンプレミスのメール サーバーを使用するユーザーと Exchange Online を使用するユーザーがいますが、すべてのユーザーは同じメール アドレス空間を共有しています。 </span><span class="sxs-lookup"><span data-stu-id="abeab-171">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="abeab-172">このハイブリッド構成の特徴は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="abeab-172">This hybrid configuration:</span></span>
  
- <span data-ttu-id="abeab-173">スケジュールで時間の経過と共に Exchange Online に移行するときに、既存の Exchange Server インフラストラクチャを活用します。</span><span class="sxs-lookup"><span data-stu-id="abeab-173">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="abeab-174">支店のインフラストラクチャに投資することなく、リモート サイトをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="abeab-174">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="abeab-175">Office 365 の Exchange Online Protection 経由で着信インターネット電子メールをルーティングできます。</span><span class="sxs-lookup"><span data-stu-id="abeab-175">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="abeab-176">データをオンプレミスで保持する必要のある、子会社を持つ多国籍企業のニーズに対応します。</span><span class="sxs-lookup"><span data-stu-id="abeab-176">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="abeab-177">このハイブリッド構成は、Skype for Business Online や SharePoint Online などのその他の Microsoft Office 365 アプリケーションと統合することもできます。</span><span class="sxs-lookup"><span data-stu-id="abeab-177">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="abeab-178">詳細については、[ハイブリッド展開の Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)および[Exchange ハイブリッド](http://hybrid.office.com/exchange/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abeab-178">For more information, see [Exchange Server Hybrid Deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx) and [Exchange Hybrid](http://hybrid.office.com/exchange/).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="abeab-179">関連項目</span><span class="sxs-lookup"><span data-stu-id="abeab-179">See Also</span></span>

[<span data-ttu-id="abeab-180">エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド</span><span class="sxs-lookup"><span data-stu-id="abeab-180">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="abeab-181">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="abeab-181">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="abeab-182">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span><span class="sxs-lookup"><span data-stu-id="abeab-182">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



