---
title: Microsoft SaaS (Office 365) のハイブリッド クラウド シナリオ
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: '概要: マイクロソフトの SaaS ベースの理解するハイブリッド アーキテクチャとシナリオ クラウドの製品 (Office 365)。'
ms.openlocfilehash: 063cbd03a2cc65a6cd278ab2efcea235079f801b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123414"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a><span data-ttu-id="2ac8e-103">Microsoft SaaS (Office 365) のハイブリッド クラウドのシナリオ</span><span class="sxs-lookup"><span data-stu-id="2ac8e-103">Hybrid cloud scenarios for Microsoft SaaS (Office 365)</span></span>

 <span data-ttu-id="2ac8e-104">**の概要:** ハイブリッド アーキテクチャとシナリオを理解するマイクロソフトの SaaS ベースのクラウド ・ ソリューション (Office 365)。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's SaaS-based cloud offerings (Office 365).</span></span>
  
<span data-ttu-id="2ac8e-105">クラウド移行または長期的な統合戦略の一環として、Exchange、SharePoint、または Skype for Business のオンプレミス展開を Office 365 内の対応する展開と組み合わせます。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-105">Combine on-premises deployments of Exchange, SharePoint, or Skype for Business with their counterparts in Office 365 as part of a cloud migration or long-term integration strategy.</span></span>
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a><span data-ttu-id="2ac8e-106">Microsoft SaaS のハイブリッド シナリオ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="2ac8e-106">Microsoft SaaS hybrid scenario architecture</span></span>

<span data-ttu-id="2ac8e-107">図 1 は、Microsoft SaaS ベースの Office 365 向けハイブリッド シナリオのアーキテクチャを示しています。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-107">Figure 1 shows the architecture of Microsoft SaaS-based hybrid scenarios for Office 365.</span></span>
  
<span data-ttu-id="2ac8e-108">**図 1:Microsoft SaaS ベースの Office 365 向けハイブリッド シナリオ**</span><span class="sxs-lookup"><span data-stu-id="2ac8e-108">**Figure 1: Microsoft SaaS-based hybrid scenarios for Office 365**</span></span>

![Microsoft SaaS ベースの Office 365 向けハイブリッド シナリオ](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
<span data-ttu-id="2ac8e-110">アーキテクチャの各レイヤーについて:</span><span class="sxs-lookup"><span data-stu-id="2ac8e-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="2ac8e-111">アプリとシナリオ</span><span class="sxs-lookup"><span data-stu-id="2ac8e-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="2ac8e-112">SaaS ベースのさまざまなハイブリッド シナリオがあります。Office サーバー製品とそれに対応する Office 365 製品に沿って以下に示します。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-112">There are a variety of SaaS-based hybrid scenarios, aligning around Office Server products and their Office 365 counterparts:</span></span>
    
  - <span data-ttu-id="2ac8e-113">Exchange Server を Exchange Online と組み合わせる (Exchange Server ハイブリッド)</span><span class="sxs-lookup"><span data-stu-id="2ac8e-113">Exchange Server combined with Exchange Online (Exchange Server hybrid)</span></span>
    
  - <span data-ttu-id="2ac8e-114">Skype for Business Server を Skype for Business Online および新しいクラウド PBX とクラウド コネクタ エディションと組み合わせたシナリオ</span><span class="sxs-lookup"><span data-stu-id="2ac8e-114">Skype for Business Server combined with Skype for Business Online and the new Cloud PBX and Cloud Connector Edition scenarios</span></span>
    
  - <span data-ttu-id="2ac8e-115">SharePoint サーバー 2019年、SharePoint サーバーの 2016、または SharePoint Server 2013 は、SharePoint Online (複数の場合) と組み合わせる</span><span class="sxs-lookup"><span data-stu-id="2ac8e-115">SharePoint Server 2019, SharePoint Server 2016, or SharePoint Server 2013 combined with SharePoint Online (multiple scenarios)</span></span>
    
    <span data-ttu-id="2ac8e-116">また、Exchange Online をオンプレミスの Skype for Business Server と組み合わせる製品間ハイブリッド シナリオもあります。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-116">There is also Exchange Online with Skype for Business Server on-premises, a cross-product hybrid scenario.</span></span>
    
- <span data-ttu-id="2ac8e-117">ID</span><span class="sxs-lookup"><span data-stu-id="2ac8e-117">Identity</span></span>
    
    <span data-ttu-id="2ac8e-p101">オンプレミスの Windows Server AD とのディレクトリ同期を含めることができます。代わりに、サード パーティの ID プロバイダーとフェデレーションを行うように Azure AD を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-p101">Can include directory synchronization with your on-premises Windows Server AD. Alternately, you can configure Azure AD to federate with a third-party identity provider.</span></span>
    
- <span data-ttu-id="2ac8e-120">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="2ac8e-120">Network</span></span>
    
    <span data-ttu-id="2ac8e-121">Office 365 か Dynamics 365 用の既存のインターネット パイプか、Microsoft ピアリングとの ExpressRoute 接続で構成されています。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-121">Consists of either your existing Internet pipe or an ExpressRoute connection with Microsoft peering for Office 365 or Dynamics 365.</span></span>
    
- <span data-ttu-id="2ac8e-122">オンプレミス</span><span class="sxs-lookup"><span data-stu-id="2ac8e-122">On-premises</span></span>
    
    <span data-ttu-id="2ac8e-p102">Exchange、SharePoint、Skype for Business の既存のサーバーで構成でき、これらの製品は最新バージョンに更新する必要があります。その後、ハイブリッド シナリオで Office 365 の対応する製品と組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-p102">Can consist of existing servers for Exchange, SharePoint, and Skype for Business, which should be updated to their latest versions. You can then combine them with their Office 365 counterparts for hybrid scenarios.</span></span>
    
<span data-ttu-id="2ac8e-125">Office 365 の開発/テスト環境のセットアップは、 [Office 365 のテスト ラボ ガイド](cloud-adoption-test-lab-guides-tlgs.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-125">Set up your own Office 365 dev/test environment, see [Office 365 Test Lab Guides](cloud-adoption-test-lab-guides-tlgs.md).</span></span>
  
## <a name="skype-for-business-hybrid"></a><span data-ttu-id="2ac8e-126">Skype ビジネスのハイブリッド</span><span class="sxs-lookup"><span data-stu-id="2ac8e-126">Skype for Business Hybrid</span></span>

<span data-ttu-id="2ac8e-p103">ビジネスのハイブリッドの Skype を使用して、オンライン ビジネスの Skype で既存のオンプレミスの展開を結合できます。一部のユーザー ホーム設置型で、一部のユーザーがオンラインで置かれているにもかかわらず、ユーザーが contoso.com など、同じセッション開始プロトコル (SIP) ドメインを共有します。このハイブリッド構成を使用すると、スケジュールに時間の経過と共に Office 365 の設置から移行します。ビジネス用の Skype は、 [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint)とも統合できます。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-p103">Skype for Business Hybrid lets you combine an existing on-premises deployment with Skype for Business Online. Some users are homed on-premises and some users are homed online, but the users share the same Session Initiation Protocol (SIP) domain, such as contoso.com. You can use this hybrid configuration to migrate from on-premises to Office 365 over time, on your schedule. Skype for Business can also be integrated with [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).</span></span>
  
<span data-ttu-id="2ac8e-131">**図 2: ビジネスのハイブリッド構成の Skype**</span><span class="sxs-lookup"><span data-stu-id="2ac8e-131">**Figure 2: The Skype for Business hybrid configuration**</span></span>

![ビジネスのハイブリッド構成の Skype](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
<span data-ttu-id="2ac8e-133">ビジネスのフロント エンド プール、エッジ サーバーとの通信 Skype Office 365 のオンライン ビジネスのため、設置型 Skype から成るビジネス ハイブリッド構成では、Skype を図 2 に示します。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-133">Figure 2 shows the Skype for Business hybrid configuration, consisting of an on-premises Skype for Business front end pool and edge server communicating with Skype for Business Online in Office 365.</span></span>
  
<span data-ttu-id="2ac8e-134">詳細については、[サーバーのビジネスとオンライン ビジネスの Skype の Skype 間のハイブリッド接続の計画](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-134">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
    
## <a name="cloud-pbx-with-skype-for-business-server"></a><span data-ttu-id="2ac8e-135">Skype for Business Server と組み合わされたクラウド PBX</span><span class="sxs-lookup"><span data-stu-id="2ac8e-135">Cloud PBX with Skype for Business Server</span></span>

<span data-ttu-id="2ac8e-136">クラウド ビジネス サーバーの Skype での PBX では、設置の公衆交換電話網 (PSTN) 接続を備えたビジネス サーバー設置型の展開トポロジを既存の Skype に移行することができます。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-136">Cloud PBX with Skype for Business Server lets you transition an existing Skype for Business Server on-premises deployment to a topology with on-premises Public Switched Telephone Network (PSTN) connectivity.</span></span> 
  
<span data-ttu-id="2ac8e-137">**図 3:Skype for Business Server と組み合わされたクラウド PBX**</span><span class="sxs-lookup"><span data-stu-id="2ac8e-137">**Figure 3: Cloud PBX with Skype for Business Server**</span></span>

![Skype for Business Server と組み合わされたクラウド PBX](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
<span data-ttu-id="2ac8e-139">図 3 は、Skype でクラウド PBX の設置では、Office 365 は、ビジネス用の Skype は、マイクロソフト クラウド PBX に接続されている既存の PBX または通信ゲートウェイ、ビジネスのサーバーで、Skype、PSTN のビジネス サーバー構成オンライン。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-139">Figure 3 shows the Cloud PBX with Skype for Business Server configuration, consisting of an on-premises existing PBX or Telco gateway, a Skype for Business Server, and the PSTN connected to the Microsoft Cloud PBX in Office 365, which includes Skype for Business Online.</span></span>
  
<span data-ttu-id="2ac8e-140">クラウドに所属する組織内のユーザーは、Microsoft クラウドから通知やボイスメールを含む構内交換機 (PBX) サービスを受信できますが、PSTN 接続 (ダイヤル トーン) はオンプレミスの Skype for Business Server 展開からエンタープライズ VoIP 経由で提供されます。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-140">Users in the organization who are homed in the cloud can receive private branch exchange (PBX) services from the Microsoft cloud that include signaling and voicemail, but PSTN connectivity (dial tone) is provided through Enterprise Voice from your on-premises Skype for Business Server deployment.</span></span>
  
<span data-ttu-id="2ac8e-p104">これは、段階的にクラウド ベースのサービスに移行することができるハイブリッド構成の優れた例です。ビジネス オンラインの Skype に移動を開始すると、ユーザーのボイス機能を保持できます。場所に置かれているペースで、音声機能がなしで続けることを知るだけで、ユーザーを移動することができます。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-p104">This is a great example of a hybrid configuration that lets you gradually migrate to a cloud-based service. You can retain your users' voice capabilities as you begin to move them to Skype for Business Online. You can move your users at your own pace, knowing that their voice features will continue no matter where they are homed.</span></span> 
  
<span data-ttu-id="2ac8e-144">詳細については、[サーバーのビジネスとオンライン ビジネスの Skype の Skype 間のハイブリッド接続の計画](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-144">For more information, see [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).</span></span>
  
<span data-ttu-id="2ac8e-145">既存の Lync Server または Skype for Business Server 展開がまだない場合は、クラウド PBX とのオンプレミス PSTN 接続を実装するパッケージ化された仮想マシン (VM) のセットである、Skype for Business クラウド コネクタ エディションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-145">If you do not already have an existing Lync Server or Skype for Business Server deployment, you can use Skype for Business Cloud Connector Edition, a set of packaged virtual machines (VMs) that implement on-premises PSTN connectivity with Cloud PBX.</span></span>
  
<span data-ttu-id="2ac8e-146">詳細については、 [Skype ビジネス クラウド コネクタ ・ エディションの計画](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-146">For more information, see [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).</span></span>

  
## <a name="sharepoint-hybrid"></a><span data-ttu-id="2ac8e-147">SharePoint ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="2ac8e-147">SharePoint Hybrid</span></span>

<span data-ttu-id="2ac8e-148">SharePoint ハイブリッドは、両方のメリットを活かした接続エクスペリエンスを実現するために、Office 365 の SharePoint Online をオンプレミスの SharePoint ファームと組み合わせます。
</span><span class="sxs-lookup"><span data-stu-id="2ac8e-148">SharePoint hybrid combines SharePoint Online in Office 365 with your on-premises SharePoint farm for a best of both worlds, connected experience.</span></span>
  
<span data-ttu-id="2ac8e-149">**図 4:SharePoint のハイブリッド構成**</span><span class="sxs-lookup"><span data-stu-id="2ac8e-149">**Figure 4: The SharePoint hybrid configuration**</span></span>

![SharePoint のハイブリッド構成](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
<span data-ttu-id="2ac8e-151">図 4 は、SharePoint Online では、Office 365 との通信、設置型の SharePoint ファームで構成される、SharePoint のハイブリッド構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-151">Figure 4 shows the SharePoint hybrid configuration, consisting of an on-premises SharePoint farm communicating with SharePoint Online in Office 365.</span></span>
  
<span data-ttu-id="2ac8e-152">SharePoint ハイブリッド シナリオ</span><span class="sxs-lookup"><span data-stu-id="2ac8e-152">SharePoint hybrid scenarios:</span></span>
  
- <span data-ttu-id="2ac8e-153">ユーザーは SharePoint Server サイトと SharePoint Online サイトをフォローし、両者を 1 つのリストに統合して参照することができます。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-153">[Hybrid OneDrive for Business](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)</span></span>
    
- [<span data-ttu-id="2ac8e-154">エクストラネットの B2B のハイブリッド</span><span class="sxs-lookup"><span data-stu-id="2ac8e-154">Hybrid Extranet B2B</span></span>](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [<span data-ttu-id="2ac8e-155">ハイブリッド検索</span><span class="sxs-lookup"><span data-stu-id="2ac8e-155">Hybrid search</span></span>](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [<span data-ttu-id="2ac8e-156">ハイブリッド プロファイル</span><span class="sxs-lookup"><span data-stu-id="2ac8e-156">Hybrid profiles</span></span>](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [<span data-ttu-id="2ac8e-157">ハイブリッドの選択</span><span class="sxs-lookup"><span data-stu-id="2ac8e-157">Hybrid Picker</span></span>](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    <span data-ttu-id="2ac8e-158">ハイブリッド シナリオは、Office 365 の SharePoint Online 管理センターから入手できる、ハイブリッド構成を自動化するウィザードを使用して、簡単に有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-158">It is easy to enable hybrid scenarios using the wizards that automate hybrid configuration, available from the SharePoint Online admin center in Office 365.</span></span>
    
- [<span data-ttu-id="2ac8e-159">拡張ハイブリッド アプリ起動ツール</span><span class="sxs-lookup"><span data-stu-id="2ac8e-159">Extensible hybrid app launcher</span></span>](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    <span data-ttu-id="2ac8e-160">ユーザーは Office 365 ビデオや Delve アプリを表示および使用し、オンプレミスの SharePoint ファームのページ内で体験することができます。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-160">Allows users to view and use Office 365 video and Delve apps and experiences within the pages of their on-premises SharePoint farm.</span></span>
    
<span data-ttu-id="2ac8e-161">これらのすべての SharePoint ハイブリッド シナリオは、拡張可能なハイブリッド アプリ起動ツールを除き、SharePoint 2016 と SharePoint 2013 の両方のユーザーが使用できます。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-161">All of these SharePoint hybrid scenarios, except the Extensible hybrid app launcher, are available for both SharePoint 2016 and SharePoint 2013 users.</span></span>
  
## <a name="exchange-server-2016-hybrid"></a><span data-ttu-id="2ac8e-162">Exchange Server 2016 ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="2ac8e-162">Exchange Server 2016 Hybrid</span></span>

<span data-ttu-id="2ac8e-163">Exchange Server 2016 ハイブリッドを使用すると、オンライン ユーザーにとっての Office 365 の Exchange Online のメリットを実感できます。一方、オンプレミス ユーザーは既存の Exchange Server インフラストラクチャを引き続き使用します。 </span><span class="sxs-lookup"><span data-stu-id="2ac8e-163">With Exchange Server 2016 Hybrid, you can realize the benefits of Exchange Online in Office 365 for online users while on-premises users continue to use existing Exchange Server infrastructure.</span></span> 
  
<span data-ttu-id="2ac8e-164">**図 5:Exchange 2016 のハイブリッド構成**</span><span class="sxs-lookup"><span data-stu-id="2ac8e-164">**Figure 5: The Exchange 2016 hybrid configuration**</span></span>

![Exchange 2016 のハイブリッド構成](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
<span data-ttu-id="2ac8e-166">図 5 は、Exchange の 2016年ハイブリッドな構成、オンプレミスの Exchange メールボックス サーバーが Exchange のオンライン保護と Office 365 のメールボックスとの通信を示しています。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-166">Figure 5 shows the Exchange 2016 hybrid configuration, consisting of on-premises Exchange mailbox servers communicating with Exchange Online Protection and mailboxes in Office 365.</span></span>
  
<span data-ttu-id="2ac8e-167">オンプレミスのメール サーバーを使用するユーザーと Exchange Online を使用するユーザーがいますが、すべてのユーザーは同じメール アドレス空間を共有しています。 </span><span class="sxs-lookup"><span data-stu-id="2ac8e-167">Some users have an on-premises email server and some users use Exchange Online, but all users share the same e-mail address space.</span></span> 
  
<span data-ttu-id="2ac8e-168">このハイブリッド構成の特徴は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-168">This hybrid configuration:</span></span>
  
- <span data-ttu-id="2ac8e-169">スケジュールに従って段階的に Exchange Online に移行する間、既存の Exchange Server インフラストラクチャを活用します。


</span><span class="sxs-lookup"><span data-stu-id="2ac8e-169">Leverages your existing Exchange Server infrastructure while you migrate to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="2ac8e-170">支店のインフラストラクチャに投資することなく、リモート サイトをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-170">Allows you to support remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="2ac8e-171">Office 365 の Exchange Online Protection 経由で着信インターネット電子メールをルーティングできます。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-171">Allows you to route incoming Internet email through Exchange Online Protection in Office 365.</span></span>
    
- <span data-ttu-id="2ac8e-172">データをオンプレミスで保持する必要のある、子会社を持つ多国籍企業のニーズに対応します。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-172">Serves the needs of multinational organizations with subsidiaries that require data to reside on-premises.</span></span>
    
<span data-ttu-id="2ac8e-173">このハイブリッド構成は、Skype for Business Online や SharePoint Online などのその他の Microsoft Office 365 アプリケーションと統合することもできます。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-173">You can also integrate this hybrid configuration with other Microsoft Office 365 applications, including Skype for Business Online and SharePoint Online.</span></span>
  
<span data-ttu-id="2ac8e-174">詳細については、 [Exchange Server のハイブリッド展開](https://docs.microsoft.com/exchange/exchange-hybrid)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ac8e-174">For more information, see [Exchange Server Hybrid Deployments](https://docs.microsoft.com/exchange/exchange-hybrid).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2ac8e-175">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ac8e-175">See Also</span></span>

[<span data-ttu-id="2ac8e-176">エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド</span><span class="sxs-lookup"><span data-stu-id="2ac8e-176">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="2ac8e-177">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="2ac8e-177">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

