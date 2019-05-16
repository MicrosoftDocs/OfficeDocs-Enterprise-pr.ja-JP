---
title: Microsoft SaaS (Office 365) のハイブリッド クラウドのシナリオ
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: '概要: Microsoft の SaaS ベースのクラウド製品のハイブリッドアーキテクチャとシナリオについて説明します (Office 365)。'
ms.openlocfilehash: 84092fe419ab31fca7763f434e328eb855d46835
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067223"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="b818c-103">Microsoft SaaS (Office 365) のハイブリッド クラウドのシナリオ</span><span class="sxs-lookup"><span data-stu-id="b818c-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="b818c-104">**概要:** Microsoft の SaaS ベースのクラウド製品のハイブリッドアーキテクチャとシナリオについて説明します (Office 365)。</span><span class="sxs-lookup"><span data-stu-id="b818c-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="b818c-105">クラウド移行または長期的な統合戦略の一環として、Exchange、SharePoint、または Skype for Business のオンプレミスの展開を Office 365 の対応する組み合わせと組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="b818c-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="b818c-106">Microsoft SaaS ハイブリッドシナリオアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="b818c-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="b818c-107">図1は、Office 365 の Microsoft SaaS ベースのハイブリッドシナリオのアーキテクチャを示しています。</span><span class="sxs-lookup"><span data-stu-id="b818c-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="b818c-108">**図 1: Microsoft SaaS ベースの Office 365 のハイブリッドシナリオ**</span><span class="sxs-lookup"><span data-stu-id="b818c-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Office 365 の Microsoft SaaS ベースのハイブリッドシナリオ](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
<span data-ttu-id="b818c-110">アーキテクチャの各レイヤーについて:</span><span class="sxs-lookup"><span data-stu-id="b818c-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="b818c-111">アプリとシナリオ</span><span class="sxs-lookup"><span data-stu-id="b818c-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="b818c-112">さまざまな SaaS ベースのハイブリッドシナリオでは、Office Server 製品と Office 365 に対応しています。</span><span class="sxs-lookup"><span data-stu-id="b818c-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="b818c-113">Exchange Server と Exchange Online の組み合わせ (Exchange Server ハイブリッド)</span><span class="sxs-lookup"><span data-stu-id="b818c-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="b818c-114">Skype for business Server と Skype for business Online との組み合わせ、新しいクラウド PBX および Cloud Connector エディションのシナリオ</span><span class="sxs-lookup"><span data-stu-id="b818c-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="b818c-115">Sharepoint Server 2019、SharePoint Server 2016、または sharepoint Server 2013 と SharePoint Online の組み合わせ (複数のシナリオ)</span><span class="sxs-lookup"><span data-stu-id="b818c-115">SharePoint Server 2019, SharePoint Server 2016, or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="b818c-116">また、クロス積ハイブリッドシナリオであるオンプレミスの Skype for Business Server を使用した Exchange Online もあります。</span><span class="sxs-lookup"><span data-stu-id="b818c-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="b818c-117">ID</span><span class="sxs-lookup"><span data-stu-id="b818c-117">Identity</span></span>
    
    <span data-ttu-id="b818c-118">オンプレミスの Active Directory ドメインサービス (AD DS) とのディレクトリ同期を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b818c-118">Can include directory synchronization with your on-premises Active Directory Domain Services (AD DS).</span></span> <span data-ttu-id="b818c-119">または、サードパーティの id プロバイダーとフェデレーションを行うように Azure AD を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b818c-119">Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="b818c-120">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="b818c-120">Network</span></span>
    
    <span data-ttu-id="b818c-121">既存のインターネットパイプ、または Office 365 または Dynamics 365 用の Microsoft ピアリングを備えた ExpressRoute 接続から構成されます。</span><span class="sxs-lookup"><span data-stu-id="b818c-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="b818c-122">社内</span><span class="sxs-lookup"><span data-stu-id="b818c-122">On-premises</span></span>
    
    <span data-ttu-id="b818c-123">Exchange、SharePoint、および Skype for Business の既存のサーバーから構成することができます。これは、最新のバージョンに更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b818c-123">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions.</span></span> <span data-ttu-id="b818c-124">その後、ハイブリッドシナリオ用の Office 365 と組み合わせて使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b818c-124">You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="b818c-125">独自の Office 365 開発/テスト環境をセットアップするには、「 [office 365 のテストラボガイド](cloud-adoption-test-lab-guides-tlgs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b818c-125">Set up your own Office 365 dev/test environment, see [Office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).</span></span>
  
## <a name="skype-for-business-hybrid"></a><span data-ttu-id="b818c-126">Skype for Business ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="b818c-126">Skype for Business Hybrid</span></span>

<span data-ttu-id="b818c-127">Skype for Business ハイブリッドを使用すると、既存のオンプレミス展開と Skype for Business Online を組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="b818c-127">Skype for Business Hybrid lets you combine an existing on-premises deployment with Skype for Business Online.</span></span> <span data-ttu-id="b818c-128">一部のユーザーはオンプレミスに所属しており、一部のユーザーはオンラインに所属していますが、ユーザーは contoso.com などの同じセッション開始プロトコル (SIP) ドメインを共有しています。</span><span class="sxs-lookup"><span data-stu-id="b818c-128">Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com.</span></span> <span data-ttu-id="b818c-129">このハイブリッド構成を使用して、オンプレミスから Office 365 への移行をスケジュールで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b818c-129">You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule.</span></span> <span data-ttu-id="b818c-130">また、Skype for Business を[Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint)と統合することもできます。</span><span class="sxs-lookup"><span data-stu-id="b818c-130">Skype for Business can also be integrated with [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span></span>
  
<span data-ttu-id="b818c-131">**図 2: Skype for Business のハイブリッド構成**</span><span class="sxs-lookup"><span data-stu-id="b818c-131">**Figure 2: The Skype for Business hybrid configuration**</span></span>

![Skype for Business のハイブリッド構成](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
<span data-ttu-id="b818c-133">図2は、Office 365 で Skype for business Online と通信するオンプレミスの Skype for Business フロントエンドプールとエッジサーバーで構成される Skype for Business ハイブリッド構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="b818c-133">Figure 2 shows the Skype for Business hybrid configuration, consisting of an on-premises Skype for Business front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="b818c-134">詳細については、「 [skype For Business Server と skype for Business Online の間のハイブリッド接続を計画](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b818c-134">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="b818c-135">Skype for Business Server を使用したクラウド PBX</span><span class="sxs-lookup"><span data-stu-id="b818c-135">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="b818c-136">クラウド PBX と Skype for business Server を使用すると、既存の Skype for Business Server のオンプレミス展開を、オンプレミスの公衆交換電話網 (PSTN) 接続を備えたトポロジに移行できます。</span><span class="sxs-lookup"><span data-stu-id="b818c-136">Cloud PBX with Skype for Business Server lets you transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="b818c-137">**図 3: Skype for Business Server を使用したクラウド PBX**</span><span class="sxs-lookup"><span data-stu-id="b818c-137">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![Skype for Business Server を使用したクラウド PBX](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
<span data-ttu-id="b818c-139">図3は、オンプレミスの既存の PBX または電気通信ゲートウェイ、Skype for Business Server、および Office 365 の Microsoft クラウド PBX に接続された PSTN (Skype for business を含む) で構成される、Skype for Business Server の構成を含むクラウド PBX を示しています。オンライン。</span><span class="sxs-lookup"><span data-stu-id="b818c-139">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="b818c-140">クラウドに所属している組織内のユーザーは、信号とボイスメールを含む Microsoft cloud から構内交換 (PBX) サービスを受けることができますが、オンプレミスのエンタープライズ Voip を介して PSTN 接続 (ダイヤルトーン) が提供されます。Skype for Business Server の展開。</span><span class="sxs-lookup"><span data-stu-id="b818c-140">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="b818c-141">これは、クラウドベースのサービスに段階的に移行できるハイブリッド構成の良い例です。</span><span class="sxs-lookup"><span data-stu-id="b818c-141">This is a great example of a hybrid configuration that lets you gradually migrate to a cloud-based service.</span></span> <span data-ttu-id="b818c-142">Skype for Business Online への移行を開始するときに、ユーザーの音声機能を保持することができます。</span><span class="sxs-lookup"><span data-stu-id="b818c-142">You can retain your users' voice capabilities as you begin to move them to Skype for Business Online.</span></span> <span data-ttu-id="b818c-143">ユーザーが所属している場所にかかわらず、自分の音声機能が続行されることを確認して、自分のペースでユーザーを移動することができます。</span><span class="sxs-lookup"><span data-stu-id="b818c-143">You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="b818c-144">詳細については、「 [skype For Business Server と skype for Business Online の間のハイブリッド接続を計画](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b818c-144">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
  
<span data-ttu-id="b818c-145">既存の Lync Server または Skype for Business Server の展開をまだ持っていない場合は、Skype for Business Cloud Connector エディションを使用できます。これは、クラウド PBX でオンプレミスの PSTN 接続を実装するパッケージ化された仮想マシン (Vm) のセットです。</span><span class="sxs-lookup"><span data-stu-id="b818c-145">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="b818c-146">詳細については、「 [Plan For Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b818c-146">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span></span>

  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="b818c-147">SharePoint ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="b818c-147">SharePoint Hybrid</span></span>

<span data-ttu-id="b818c-148">SharePoint ハイブリッドは、Office 365 の SharePoint Online とオンプレミスの SharePoint ファームを組み合わせて、接続された機能を最大限に活用しています。</span><span class="sxs-lookup"><span data-stu-id="b818c-148">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="b818c-149">**図 4: SharePoint ハイブリッド構成**</span><span class="sxs-lookup"><span data-stu-id="b818c-149">**Figure 4: The SharePoint hybrid configuration**</span></span>

![SharePoint ハイブリッド構成](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
<span data-ttu-id="b818c-151">図4は、Office 365 で SharePoint Online と通信するオンプレミスの SharePoint ファームで構成される SharePoint ハイブリッド構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="b818c-151">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="b818c-152">SharePoint ハイブリッドシナリオ:</span><span class="sxs-lookup"><span data-stu-id="b818c-152">SharePoint hybrid scenarios:</span></span>
  
- [<span data-ttu-id="b818c-153">ハイブリッドの OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="b818c-153">Hybrid OneDrive for Business</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [<span data-ttu-id="b818c-154">ハイブリッドエクストラネットの B2B</span><span class="sxs-lookup"><span data-stu-id="b818c-154">Hybrid Extranet B2B</span></span>](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [<span data-ttu-id="b818c-155">ハイブリッド検索</span><span class="sxs-lookup"><span data-stu-id="b818c-155">Hybrid search</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [<span data-ttu-id="b818c-156">ハイブリッド プロファイル</span><span class="sxs-lookup"><span data-stu-id="b818c-156">Hybrid profiles</span></span>](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [<span data-ttu-id="b818c-157">ハイブリッドピッカー</span><span class="sxs-lookup"><span data-stu-id="b818c-157">Hybrid Picker</span></span>](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    <span data-ttu-id="b818c-158">Office 365 の SharePoint Online 管理センターから利用できるハイブリッド構成を自動化するウィザードを使用して、ハイブリッドシナリオを有効にすることが容易になります。</span><span class="sxs-lookup"><span data-stu-id="b818c-158">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="b818c-159">拡張ハイブリッド アプリ起動ツール</span><span class="sxs-lookup"><span data-stu-id="b818c-159">Extensible hybrid app launcher</span></span>](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    <span data-ttu-id="b818c-160">オンプレミスの SharePoint ファームのページ内で、ユーザーが Office 365 video および Delve アプリとエクスペリエンスを表示して使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b818c-160">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="b818c-161">これらの SharePoint ハイブリッドシナリオは、拡張可能なハイブリッドアプリ起動ツールを除くすべて、SharePoint 2016 ユーザーと SharePoint 2013 ユーザーの両方で使用できます。</span><span class="sxs-lookup"><span data-stu-id="b818c-161">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="b818c-162">Exchange Server 2016 ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="b818c-162">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="b818c-163">Exchange Server 2016 ハイブリッドを使用すると、オンプレミスのユーザーが既存の Exchange Server インフラストラクチャを引き続き使用している間に、Office 365 での Exchange Online の利点を実感することができます。</span><span class="sxs-lookup"><span data-stu-id="b818c-163">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="b818c-164">**図 5: Exchange 2016 ハイブリッド構成**</span><span class="sxs-lookup"><span data-stu-id="b818c-164">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Exchange 2016 ハイブリッド構成](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
<span data-ttu-id="b818c-166">図5は、Office 365 の Exchange Online Protection とメールボックスと通信するオンプレミスの Exchange メールボックスサーバーで構成される Exchange 2016 ハイブリッド構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="b818c-166">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="b818c-167">一部のユーザーはオンプレミスの電子メールサーバーを所有しており、一部のユーザーは Exchange Online を使用していますが、すべてのユーザーが同じ電子メールアドレススペースを共有しています。</span><span class="sxs-lookup"><span data-stu-id="b818c-167">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="b818c-168">このハイブリッド構成:</span><span class="sxs-lookup"><span data-stu-id="b818c-168">This hybrid configuration:</span></span>
  
- <span data-ttu-id="b818c-169">時間の経過とともに、お客様のスケジュールに基づいて Exchange Online に移行する際に、既存の Exchange Server インフラストラクチャを活用できます。</span><span class="sxs-lookup"><span data-stu-id="b818c-169">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="b818c-170">ブランチオフィスのインフラストラクチャに投資することなく、リモートサイトをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="b818c-170">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="b818c-171">Office 365 で Exchange Online Protection 経由で受信インターネットメールをルーティングできるようにします。</span><span class="sxs-lookup"><span data-stu-id="b818c-171">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="b818c-172">データをオンプレミスで使用する必要がある子会社を持つ多国籍企業のニーズに対応します。</span><span class="sxs-lookup"><span data-stu-id="b818c-172">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="b818c-173">このハイブリッド構成は、Skype for Business Online や SharePoint Online など、他の Microsoft Office 365 アプリケーションと統合することもできます。</span><span class="sxs-lookup"><span data-stu-id="b818c-173">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="b818c-174">詳細については、「 [Exchange Server のハイブリッド展開](https://docs.microsoft.com/exchange/exchange-hybrid)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b818c-174">For more information, see [Exchange Server Hybrid Deployments](https://docs.microsoft.com/exchange/exchange-hybrid).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b818c-175">関連項目</span><span class="sxs-lookup"><span data-stu-id="b818c-175">See Also</span></span>

[<span data-ttu-id="b818c-176">エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド</span><span class="sxs-lookup"><span data-stu-id="b818c-176">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="b818c-177">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="b818c-177">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

