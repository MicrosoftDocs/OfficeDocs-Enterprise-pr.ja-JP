---
title: アクセス可能な図 - Microsoft Lync 2013 プラットフォーム オプション
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: この記事は、Microsoft Lync 2013 プラットフォーム オプションという名前のダイアグラム (技術ダイアグラム で利用できます) のアクセス可能なテキスト バージョンです。
ms.openlocfilehash: 4a660df4bfacad2a00f5d9fbb5e1b668840e3b9f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487799"
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a><span data-ttu-id="64298-103">アクセス可能な図 - Microsoft Lync 2013 プラットフォーム オプション</span><span class="sxs-lookup"><span data-stu-id="64298-103">Accessible diagram - Microsoft Lync 2013 Platform Options</span></span>

<span data-ttu-id="64298-104">**概要:** この記事は、Microsoft Lync 2013 プラットフォーム オプションという名前のダイアグラム ([技術ダイアグラム](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)で利用できます) のアクセス可能なテキスト バージョンです。</span><span class="sxs-lookup"><span data-stu-id="64298-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Lync 2013 Platform Options, which is available at [Technical Diagrams](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="64298-105">このポスターは、ビジネスの意思決定者 (BDM) と設計者が Lync Online (Office 365) および Lync Server の展開に関して知る必要のある情報を説明しており、内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="64298-105">This poster describes what business decision makers (BDMs) and architects need to know about Lync Online (Office 365) and Lync Server deployments and includes:</span></span>
  
- <span data-ttu-id="64298-106">4 つの異なる展開オプションの比較:Lync Online (Office 365)、Lync Online/Server ハイブリッド、Lync Server、およびプロバイダー ホスト型の Lync Server。</span><span class="sxs-lookup"><span data-stu-id="64298-106">A comparison of four different deployment options: Lync Online (Office 365), Lync Online/Server Hybrid, Lync Server, and Provider-Hosted Lync Server.</span></span> 
    
- <span data-ttu-id="64298-107">Lync 2013 を展開するための 2 つのシナリオ例。</span><span class="sxs-lookup"><span data-stu-id="64298-107">Two example scenarios for deploying Lync 2013.</span></span>
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a><span data-ttu-id="64298-108">Lync 2013 プラットフォーム用の 4 つの異なる展開の比較</span><span class="sxs-lookup"><span data-stu-id="64298-108">Comparison of four different deployments for the Lync 2013 platform</span></span>

<span data-ttu-id="64298-109">比較の結果は以下の領域での各展開オプションに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="64298-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="64298-110">各種の展開機能の概要</span><span class="sxs-lookup"><span data-stu-id="64298-110">An overview of the different deployment features</span></span>
    
- <span data-ttu-id="64298-111">各展開オプションを実装するメリット</span><span class="sxs-lookup"><span data-stu-id="64298-111">Benefits of implementing each deployment option</span></span>
    
- <span data-ttu-id="64298-112">ライセンス要件</span><span class="sxs-lookup"><span data-stu-id="64298-112">Licensing requirements</span></span>
    
- <span data-ttu-id="64298-113">必要なアーキテクチャ タスク</span><span class="sxs-lookup"><span data-stu-id="64298-113">Required architectural tasks</span></span>
    
- <span data-ttu-id="64298-114">各展開オプションを実装するための IT 技術者の責任</span><span class="sxs-lookup"><span data-stu-id="64298-114">IT Pro responsibilities for implementing each deployment option</span></span>
    
### <a name="overview"></a><span data-ttu-id="64298-115">概要</span><span class="sxs-lookup"><span data-stu-id="64298-115">Overview</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="64298-116">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="64298-116">Lync Online (Office 365)</span></span>

<span data-ttu-id="64298-117">Office 365 マルチテナント プランを使用すると、効率を高めコストを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="64298-117">You gain efficiency and optimize for cost with Office 365 multitenant plans.</span></span>
  
<span data-ttu-id="64298-118">付随する図は Lync Online に伴う Azure Active Directory テナントを示しています。これは、オンプレミスの Active Directory ドメイン サービス (AD DS) 環境と Azure Active Directory テナントの間で、アカウント名およびパスワードを同期させます。</span><span class="sxs-lookup"><span data-stu-id="64298-118">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span> 
  
<span data-ttu-id="64298-119">フィーチャーと機能の説明:</span><span class="sxs-lookup"><span data-stu-id="64298-119">Description of features and functionality:</span></span>
  
- <span data-ttu-id="64298-120">サービスとしてのソフトウェア (SaaS)。</span><span class="sxs-lookup"><span data-stu-id="64298-120">Software as a Service (SaaS).</span></span>
    
- <span data-ttu-id="64298-121">常に最新の豊富な機能セット。</span><span class="sxs-lookup"><span data-stu-id="64298-121">Rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="64298-122">他のアプリケーションと共に使用できる、オンラインのアカウント用の Azure Active Directory テナントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="64298-122">Includes an Azure Active Directory tenant for online accounts, which can be used with other applications.</span></span> 
    
- <span data-ttu-id="64298-123">ディレクトリの統合には、社内 Active Directory Domain Services (AD DS) 環境と Azure Active Directory テナント間でアカウント名とパスワードを同期させることが含まれます。</span><span class="sxs-lookup"><span data-stu-id="64298-123">Directory integration includes synchronizing account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
    
- <span data-ttu-id="64298-124">シングル サインオン (SSO) が要件である場合、Active Directory フェデレーション サービス(AD FS) を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64298-124">If single sign-on (SSO) is a requirement, Active Directory Federation Services (AD FS) must be implemented.</span></span> 
    
- <span data-ttu-id="64298-125">インターネット経由のクライアント通信は、暗号化されて認証されます。</span><span class="sxs-lookup"><span data-stu-id="64298-125">Client communication over the Internet is encrypted and authenticated.</span></span>
    
- <span data-ttu-id="64298-126">従来の電話装置、公衆交換電話網 (PSTN)、接続は、サード パーティ プロバイダーを通じて利用可能です。</span><span class="sxs-lookup"><span data-stu-id="64298-126">Legacy phone equipment, public switched telephone network (PSTN), connectivity is available through third-party providers.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="64298-127">Lync Online/Server ハイブリッド (ドメインを分割)</span><span class="sxs-lookup"><span data-stu-id="64298-127">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="64298-128">Office 365 の利点を Lync 2013 の社内展開と組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="64298-128">You can combine the benefits of Office 365 with an on-premises deployment of Lync 2013.</span></span>
  
<span data-ttu-id="64298-p101">付属の図は、一部のユーザーは社内に配置され、一部のユーザーはオンラインに配置されている、Lync Online を使用する Office 365 を示しています。社内に展開されたエッジ サーバーも示されています。</span><span class="sxs-lookup"><span data-stu-id="64298-p101">The accompanying diagram shows Office 365 with Lync Online where some users are homed on-premises and some users are homed online. An Edge Server that is deployed on-premises is also shown.</span></span>
  
<span data-ttu-id="64298-131">フィーチャーと機能の説明:</span><span class="sxs-lookup"><span data-stu-id="64298-131">Description of features and functionality:</span></span>
  
- <span data-ttu-id="64298-132">一部のユーザーは社内に配置され、一部のユーザーはオンラインに配置されていますが、それらのユーザーは同じ SIP ドメイン (contoso.com など) を共有します。</span><span class="sxs-lookup"><span data-stu-id="64298-132">Some users are homed on premises and some users are homed online, but the users share the same SIP domain (such as contoso.com).</span></span>
    
- <span data-ttu-id="64298-133">PSTN への接続など、既存の Lync Server 2013 インフラストラクチャを活用します。</span><span class="sxs-lookup"><span data-stu-id="64298-133">Leverage your existing Lync Server 2013 infrastructure, including the connections to the PSTN.</span></span>
    
- <span data-ttu-id="64298-134">PSTN を必要としない場合は、新規の Lync オンライン ユーザーを簡単に追加します。</span><span class="sxs-lookup"><span data-stu-id="64298-134">Add new Lync Online users easily when they do not require PSTN.</span></span>
    
- <span data-ttu-id="64298-135">スケジュールに従って、時の経過と共に Lync オンプレミスから Lync Online に移行します。</span><span class="sxs-lookup"><span data-stu-id="64298-135">Migrate from Lync on-premises to Lync Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="64298-136">Exchange Online や SharePoint Online など、他の Office 365 アプリケーションと統合します。</span><span class="sxs-lookup"><span data-stu-id="64298-136">Integrate with other Office 365 applications, including Exchange Online and SharePoint Online.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="64298-137">Lync Server</span><span class="sxs-lookup"><span data-stu-id="64298-137">Lync Server</span></span>

<span data-ttu-id="64298-p102">この展開では、自らすべてを所有しています。付随する図は、社内の Active Directory ドメイン サービス (AD DS) 環境を持つ Lync Server インフラストラクチャを示しています。ここでは、ユーザーは社内に配置されています。</span><span class="sxs-lookup"><span data-stu-id="64298-p102">In this deployment, you own everything. The accompanying diagram shows a Lync Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="64298-140">フィーチャーと機能の説明:</span><span class="sxs-lookup"><span data-stu-id="64298-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="64298-141">容量計画とサイジング。</span><span class="sxs-lookup"><span data-stu-id="64298-141">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="64298-142">サーバーの購入とセットアップ。</span><span class="sxs-lookup"><span data-stu-id="64298-142">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="64298-143">展開。</span><span class="sxs-lookup"><span data-stu-id="64298-143">Deployment.</span></span>
    
- <span data-ttu-id="64298-144">スケール アウト、修正、および操作。</span><span class="sxs-lookup"><span data-stu-id="64298-144">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="64298-145">データのバックアップ。</span><span class="sxs-lookup"><span data-stu-id="64298-145">Backing up data.</span></span>
    
- <span data-ttu-id="64298-146">フェールオーバーと障害復旧の保守。</span><span class="sxs-lookup"><span data-stu-id="64298-146">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="64298-147">PSTN への Lync Server 2013 インフラストラクチャの接続。</span><span class="sxs-lookup"><span data-stu-id="64298-147">Connecting your Lync Server 2013 infrastructure to the PSTN.</span></span>
    
- <span data-ttu-id="64298-148">構内交換機 (PBX) など、既存の電話機器との統合。</span><span class="sxs-lookup"><span data-stu-id="64298-148">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="64298-149">プロバイダー ホスト型の Lync Server</span><span class="sxs-lookup"><span data-stu-id="64298-149">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="64298-p103">この展開では、すべてをプロバイダーが所有します。付属の図は、社内環境に接続されたサーバと機器など、プロバイダーのネットワークを示しています。</span><span class="sxs-lookup"><span data-stu-id="64298-p103">In this deployment, your provider owns everything. The accompanying diagram shows a provider's network including their servers and equipment with a connection to an on-premises environment.</span></span>
  
<span data-ttu-id="64298-152">フィーチャーと機能の説明:</span><span class="sxs-lookup"><span data-stu-id="64298-152">Description of features and functionality:</span></span>
  
- <span data-ttu-id="64298-153">容量計画とサイジング。</span><span class="sxs-lookup"><span data-stu-id="64298-153">Capacity planning and sizing.</span></span>
    
- <span data-ttu-id="64298-154">サーバーの購入とセットアップ。</span><span class="sxs-lookup"><span data-stu-id="64298-154">Server acquisition and setup.</span></span>
    
- <span data-ttu-id="64298-155">展開。</span><span class="sxs-lookup"><span data-stu-id="64298-155">Deployment.</span></span>
    
- <span data-ttu-id="64298-156">スケール アウト、修正、および操作。</span><span class="sxs-lookup"><span data-stu-id="64298-156">Scaling out, patching, and operations.</span></span>
    
- <span data-ttu-id="64298-157">データのバックアップ。</span><span class="sxs-lookup"><span data-stu-id="64298-157">Backing up data.</span></span>
    
- <span data-ttu-id="64298-158">フェールオーバーと障害復旧の保守。</span><span class="sxs-lookup"><span data-stu-id="64298-158">Maintaining failover and disaster recovery.</span></span>
    
- <span data-ttu-id="64298-159">構内交換機 (PBX) など、既存の電話機器との統合。</span><span class="sxs-lookup"><span data-stu-id="64298-159">Integration with existing phone equipment, such as private branch exchanges (PBXs).</span></span>
    
- <span data-ttu-id="64298-160">さらに、プロバイダーは以下を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="64298-160">In addition, the provider can:</span></span>
    
  - <span data-ttu-id="64298-161">自社の社内システムに接続するプロバイダー所有のネットワークに、サーバーや装置を設置する (実線)。</span><span class="sxs-lookup"><span data-stu-id="64298-161">Install their servers and equipment in their own network with a connection to your premises (solid line).</span></span>
    
  - <span data-ttu-id="64298-162">自社の社内システムに、プロバイダー所有のサーバーを設置する (点線)。</span><span class="sxs-lookup"><span data-stu-id="64298-162">Install their servers on your premises (dotted line).</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="64298-163">各展開オプションを実装するメリット</span><span class="sxs-lookup"><span data-stu-id="64298-163">Benefits of implementing each deployment option</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="64298-164">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="64298-164">Lync Online (Office 365)</span></span>

- <span data-ttu-id="64298-165">社内サーバーやサーバー ソフトウェアを運用するときのような負荷はありません。</span><span class="sxs-lookup"><span data-stu-id="64298-165">No operational burden of on-premises servers or server software.</span></span>
    
- <span data-ttu-id="64298-166">クラウド ベースのサービスとしての Lync Server 2013 の通信機能。</span><span class="sxs-lookup"><span data-stu-id="64298-166">Communication capabilities of Lync Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="64298-167">Lync プレゼンス、インスタント メッセージング、音声とビデオの通話、機能が豊富なオンライン会議、およびさまざまな Web 会議機能。</span><span class="sxs-lookup"><span data-stu-id="64298-167">Lync presence, instant messaging, audio and video calling, rich online meetings, and extensive web conferencing capabilities.</span></span>
    
- <span data-ttu-id="64298-168">地理的に分散した組織や、主にモバイルの従業員によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="64298-168">Used with geographically-dispersed organizations or with primarily mobile employees.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="64298-169">Lync Online/Server ハイブリッド (ドメインを分割)</span><span class="sxs-lookup"><span data-stu-id="64298-169">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="64298-170">リモート ユーザーのため、およびビジネス パートナーとの統合のために Lync Online を使用。</span><span class="sxs-lookup"><span data-stu-id="64298-170">Use Lync Online for remote users and integration with business partners.</span></span>
    
- <span data-ttu-id="64298-171">社内の Lync から Lync Online への移行が容易。</span><span class="sxs-lookup"><span data-stu-id="64298-171">Facilitate a migration from Lync on-premises to Lync Online.</span></span>
    
- <span data-ttu-id="64298-172">リモート サイトのサポートに、ブランチ オフィス アプライアンスが不要。</span><span class="sxs-lookup"><span data-stu-id="64298-172">Support remote sites without using a branch office appliance.</span></span>
    
- <span data-ttu-id="64298-173">新規事業取得時の Lync サポートの追加が容易。</span><span class="sxs-lookup"><span data-stu-id="64298-173">Ease of adding Lync support for new business acquisitions.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="64298-174">Lync Server</span><span class="sxs-lookup"><span data-stu-id="64298-174">Lync Server</span></span>

- <span data-ttu-id="64298-175">プライベート クラウド ソリューション。</span><span class="sxs-lookup"><span data-stu-id="64298-175">Private cloud solutions.</span></span>
    
- <span data-ttu-id="64298-176">高度にカスタマイズされたソリューション。</span><span class="sxs-lookup"><span data-stu-id="64298-176">Highly customized solutions.</span></span>
    
- <span data-ttu-id="64298-177">Lync Online でサポートされていないハードウェアおよびソフトウェアに依存するサード パーティ製コンポーネントを持つレガシー ソリューション。</span><span class="sxs-lookup"><span data-stu-id="64298-177">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="64298-178">AD DS アカウントと Office 365 との同期を防止するプライバシー制限。</span><span class="sxs-lookup"><span data-stu-id="64298-178">Privacy restrictions that prevent synchronization of AD DS accounts with Office 365.</span></span>
    
- <span data-ttu-id="64298-179">プラットフォームとソリューション全体のコントロールを望む企業。</span><span class="sxs-lookup"><span data-stu-id="64298-179">Organizations that desire control of the entire platform and solution.</span></span>
    
- <span data-ttu-id="64298-180">PBX の Lync エンタープライズ VoIP への置き換え。</span><span class="sxs-lookup"><span data-stu-id="64298-180">PBX replacement with Lync Enterprise Voice.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="64298-181">プロバイダー ホスト型の Lync Server</span><span class="sxs-lookup"><span data-stu-id="64298-181">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="64298-182">Lync Server の機能を必要としているものの、その展開と保守をアウトソース化することを希望する組織。</span><span class="sxs-lookup"><span data-stu-id="64298-182">Organizations that want Lync Server functionality but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="64298-183">プロバイダー ベースのソリューション。</span><span class="sxs-lookup"><span data-stu-id="64298-183">Provider-based solutions.</span></span>
    
- <span data-ttu-id="64298-184">高度にカスタマイズされたソリューション。</span><span class="sxs-lookup"><span data-stu-id="64298-184">Highly customized solutions.</span></span>
    
- <span data-ttu-id="64298-185">Lync Online でサポートされていないハードウェアおよびソフトウェアに依存するサード パーティ製コンポーネントを持つレガシー ソリューション。</span><span class="sxs-lookup"><span data-stu-id="64298-185">Legacy solutions with third-party components that depend on hardware and software that are not supported by Lync Online.</span></span>
    
- <span data-ttu-id="64298-186">PBX の Lync エンタープライズ VoIP への置き換え。</span><span class="sxs-lookup"><span data-stu-id="64298-186">PBX replacement with Lync Enterprise Voice.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="64298-187">ライセンス要件</span><span class="sxs-lookup"><span data-stu-id="64298-187">License requirements</span></span>

#### <a name="lync-online-office-365"></a><span data-ttu-id="64298-188">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="64298-188">Lync Online (Office 365)</span></span>

<span data-ttu-id="64298-189">サブスクリプション モデル。</span><span class="sxs-lookup"><span data-stu-id="64298-189">Subscription model.</span></span>
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="64298-190">Lync Online/Server ハイブリッド (ドメインを分割)</span><span class="sxs-lookup"><span data-stu-id="64298-190">Lync Online/Server Hybrid (split domain)</span></span>

- <span data-ttu-id="64298-p104">Office 365  サブスクリプション モデル。追加のライセンスは不要です。</span><span class="sxs-lookup"><span data-stu-id="64298-p104">Office 365 — Subscription model. No additional licenses needed.</span></span> 
    
- <span data-ttu-id="64298-193">オンプレミス — すべてのオンプレミス ライセンスが適用されます。</span><span class="sxs-lookup"><span data-stu-id="64298-193">On-premises — All on-premises licenses apply.</span></span> 
    
#### <a name="lync-server"></a><span data-ttu-id="64298-194">Lync Server</span><span class="sxs-lookup"><span data-stu-id="64298-194">Lync Server</span></span>

- <span data-ttu-id="64298-195">サーバー オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="64298-195">Server Operating System</span></span>
    
- <span data-ttu-id="64298-196">SQL Server</span><span class="sxs-lookup"><span data-stu-id="64298-196">SQL Server</span></span>
    
- <span data-ttu-id="64298-197">Lync 2013 Server のライセンス</span><span class="sxs-lookup"><span data-stu-id="64298-197">Lync 2013 Server License</span></span>
    
- <span data-ttu-id="64298-198">Lync 2013 クライアント アクセスのライセンス</span><span class="sxs-lookup"><span data-stu-id="64298-198">Lync 2013 Client Access License</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="64298-199">プロバイダー ホスト型の Lync Server</span><span class="sxs-lookup"><span data-stu-id="64298-199">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="64298-200">コストは、Lync のソリューション プロバイダーとの契約に基づいて決まります。</span><span class="sxs-lookup"><span data-stu-id="64298-200">Costs are based on the agreement with your Lync solution provider.</span></span>
  
### <a name="architecture-tasks"></a><span data-ttu-id="64298-201">アーキテクチャ タスク</span><span class="sxs-lookup"><span data-stu-id="64298-201">Architecture tasks</span></span>

<span data-ttu-id="64298-202">ここでは各展開オプションのアーキテクチャのタスクを示します。</span><span class="sxs-lookup"><span data-stu-id="64298-202">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="64298-203">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="64298-203">Lync Online (Office 365)</span></span>

- <span data-ttu-id="64298-204">ディレクトリ同期を計画および設計します。</span><span class="sxs-lookup"><span data-stu-id="64298-204">Plan and design directory synchronization.</span></span>
    
- <span data-ttu-id="64298-205">ファイアウォール、プロキシ サーバー、ゲートウェイ、および WAN リンク全体におけるネットワークの容量と可用性を確保します。</span><span class="sxs-lookup"><span data-stu-id="64298-205">Ensure network capacity and availability through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
- <span data-ttu-id="64298-206">Office 365 サービス内容にエンタープライズ セキュリティを付加するために、サード パーティの SSL 証明書を取得します。</span><span class="sxs-lookup"><span data-stu-id="64298-206">Acquire third-party SSL certificates to provide enterprise-security for Office 365 service offerings.</span></span>
    
- <span data-ttu-id="64298-207">インターネット プロトコル バージョン 6 (IPv6) を使用して Office 365 に接続するかどうかを決めます。</span><span class="sxs-lookup"><span data-stu-id="64298-207">Decide if you want to connect to Office 365 with Internet Protocol version 6 (IPv6).</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="64298-208">Lync Online/Server ハイブリッド (ドメインを分割)</span><span class="sxs-lookup"><span data-stu-id="64298-208">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="64298-209">Office 365 と社内環境の両方のタスクに加えて:</span><span class="sxs-lookup"><span data-stu-id="64298-209">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="64298-210">Exchange Server や SharePoint のオンプレミス バージョンとオンライン バージョンのうち、どれほどの機能を統合するかを決めます。</span><span class="sxs-lookup"><span data-stu-id="64298-210">Determine how much feature integration you want to use with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
- <span data-ttu-id="64298-211">必要な場合、Office 365 からの要求のためにどのプロキシ サーバー デバイスを使用するかを決めます。</span><span class="sxs-lookup"><span data-stu-id="64298-211">If required, determine which proxy server device will be used for requests from Office 365.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="64298-212">Lync Server</span><span class="sxs-lookup"><span data-stu-id="64298-212">Lync Server</span></span>

<span data-ttu-id="64298-213">既存の社内環境における Lync 環境の設計:</span><span class="sxs-lookup"><span data-stu-id="64298-213">Design the Lync environment in an existing on-premises environment:</span></span>
  
- <span data-ttu-id="64298-214">本店と支店での Lync のトポロジ。</span><span class="sxs-lookup"><span data-stu-id="64298-214">Lync topology for central and branch offices.</span></span>
    
- <span data-ttu-id="64298-215">仮想化を含む、サーバー ハードウェア。</span><span class="sxs-lookup"><span data-stu-id="64298-215">Server hardware, including virtualization.</span></span>
    
- <span data-ttu-id="64298-216">Active Directory ドメイン サービス (AD DS) と DNS の統合。</span><span class="sxs-lookup"><span data-stu-id="64298-216">Integration with Active Directory Domain Services (AD DS) and DNS.</span></span>
    
- <span data-ttu-id="64298-217">Lync Server プールの負荷分散 。</span><span class="sxs-lookup"><span data-stu-id="64298-217">Load balancing for Lync server pools.</span></span>
    
- <span data-ttu-id="64298-218">フェールオーバーと障害復旧。</span><span class="sxs-lookup"><span data-stu-id="64298-218">Failover and disaster recovery.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="64298-219">プロバイダー ホスト型の Lync Server</span><span class="sxs-lookup"><span data-stu-id="64298-219">Provider-Hosted Lync Server</span></span>

- <span data-ttu-id="64298-220">クラウド ベースのインストールでは、サービス プロバイダーのネットワークへの接続を決めます。</span><span class="sxs-lookup"><span data-stu-id="64298-220">For a cloud-based installation, determine the connection to the service provider's network.</span></span>
    
- <span data-ttu-id="64298-221">社内インストールでは、プロバイダーの Lync サーバーをネットワーク内のどこに配置するかを決めます。</span><span class="sxs-lookup"><span data-stu-id="64298-221">For an on-premises installation, determine the placement of the provider's Lync servers on your network.</span></span>
    
- <span data-ttu-id="64298-222">どちらのタイプの場合も、AD DS と PBX 機器との統合を決めます。</span><span class="sxs-lookup"><span data-stu-id="64298-222">For both types, determine the integration with AD DS and your PBX equipment.</span></span>
    
### <a name="it-pro-responsibilities"></a><span data-ttu-id="64298-223">IT 技術者の責任</span><span class="sxs-lookup"><span data-stu-id="64298-223">IT Pro responsibilities</span></span>

<span data-ttu-id="64298-224">ここでは、各展開オプションについて、IT 担当者の責任を示します。</span><span class="sxs-lookup"><span data-stu-id="64298-224">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="lync-online-office-365"></a><span data-ttu-id="64298-225">Lync Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="64298-225">Lync Online (Office 365)</span></span>

<span data-ttu-id="64298-226">Lync Online の展開と管理 (Office 365):</span><span class="sxs-lookup"><span data-stu-id="64298-226">Deploy and manage Lync Online (Office 365):</span></span>
  
- <span data-ttu-id="64298-227">ディレクトリ同期の計画を実装します。</span><span class="sxs-lookup"><span data-stu-id="64298-227">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="64298-228">内部および外部の DNS レコードとルーティングを計画し、実装します。</span><span class="sxs-lookup"><span data-stu-id="64298-228">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="64298-229">Office 365 の IP アドレスと URL 要件に合わせてプロキシまたはファイアウォールを構成します。</span><span class="sxs-lookup"><span data-stu-id="64298-229">Configure your proxy or firewall for Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="64298-230">ユーザー アカウントと Lync Online の設定を管理します。</span><span class="sxs-lookup"><span data-stu-id="64298-230">Administer user accounts and Lync Online settings.</span></span>
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a><span data-ttu-id="64298-231">Lync Online/Server ハイブリッド (ドメインを分割)</span><span class="sxs-lookup"><span data-stu-id="64298-231">Lync Online/Server Hybrid (split domain)</span></span>

<span data-ttu-id="64298-232">Office 365 と社内環境の両方のタスクに加えて:</span><span class="sxs-lookup"><span data-stu-id="64298-232">In addition to tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="64298-233">必要であれば、プロキシ サーバー デバイスを構成します。</span><span class="sxs-lookup"><span data-stu-id="64298-233">Configure the proxy server device, if required.</span></span>
    
- <span data-ttu-id="64298-234">Exchange Server や SharePoint の社内バージョンとオンライン バージョンの機能統合を構成します。</span><span class="sxs-lookup"><span data-stu-id="64298-234">Configure the integration of features with on-premises and online versions of Exchange Server and SharePoint.</span></span>
    
#### <a name="lync-server"></a><span data-ttu-id="64298-235">Lync Server</span><span class="sxs-lookup"><span data-stu-id="64298-235">Lync Server</span></span>

<span data-ttu-id="64298-236">社内環境で Lync Server を展開して管理します:</span><span class="sxs-lookup"><span data-stu-id="64298-236">Deploy and manage Lync Server in an on-premises environment:</span></span>
  
- <span data-ttu-id="64298-237">サーバーを準備します。</span><span class="sxs-lookup"><span data-stu-id="64298-237">Provision the servers.</span></span>
    
- <span data-ttu-id="64298-238">Lync トポロジを展開します。</span><span class="sxs-lookup"><span data-stu-id="64298-238">Deploy the Lync topology.</span></span>
    
- <span data-ttu-id="64298-239">Lync サーバーを更新します。</span><span class="sxs-lookup"><span data-stu-id="64298-239">Update Lync servers.</span></span>
    
- <span data-ttu-id="64298-240">使用状況に応じて、トポロジ サーバーを追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="64298-240">Add or remove topology servers as needed based on utilization.</span></span>
    
- <span data-ttu-id="64298-241">フェイル オーバーと障害復旧環境を実装します。</span><span class="sxs-lookup"><span data-stu-id="64298-241">Implement the failover and disaster recovery environment.</span></span>
    
#### <a name="provider-hosted-lync-server"></a><span data-ttu-id="64298-242">プロバイダー ホスト型の Lync Server</span><span class="sxs-lookup"><span data-stu-id="64298-242">Provider-Hosted Lync Server</span></span>

<span data-ttu-id="64298-243">プロバイダーと協力して次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="64298-243">Work with the provider to:</span></span>
  
- <span data-ttu-id="64298-244">Lync Server をネットワークに統合します。</span><span class="sxs-lookup"><span data-stu-id="64298-244">Integrate Lync Server into your network.</span></span>
    
- <span data-ttu-id="64298-245">Lync Server を他の Microsoft 製品やカスタム ソリューションと統合します。</span><span class="sxs-lookup"><span data-stu-id="64298-245">Integrate Lync Server with other Microsoft products or custom solutions.</span></span>
    
- <span data-ttu-id="64298-246">プロバイダーのサービス レベル契約 (SLA) の遵守を監視します。</span><span class="sxs-lookup"><span data-stu-id="64298-246">Monitor adherence with provider service level agreement (SLA).</span></span>
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a><span data-ttu-id="64298-247">Lync 2013 を展開するための 2 つのシナリオ例</span><span class="sxs-lookup"><span data-stu-id="64298-247">Two example scenarios for deploying Lync 2013</span></span>

### <a name="directory-synchronization-components-in-microsoft-azure"></a><span data-ttu-id="64298-248">Microsoft Azure のディレクトリ同期コンポーネント</span><span class="sxs-lookup"><span data-stu-id="64298-248">Directory Synchronization components in Microsoft Azure</span></span>

<span data-ttu-id="64298-249">Azure では仮想マシンをオンデマンドで展開できるため、Office 365 ディレクトリ統合コンポーネントをより速く展開できます。</span><span class="sxs-lookup"><span data-stu-id="64298-249">Deploying Office 365 directory synchronization components in Azure is faster due to the ability to deploy virtual machines on-demand.</span></span>
  
<span data-ttu-id="64298-250">付随する図は Lync Online に伴う Azure Active Directory テナントを示しています。これは、オンプレミスの Active Directory 環境と Azure Active Directory テナントの間で、アカウント名およびパスワードを同期させます。</span><span class="sxs-lookup"><span data-stu-id="64298-250">The accompanying diagram shows Lync Online with an Azure Active Directory tenant, which synchronizes account names and passwords between the on-premises Active Directory environment and the Azure Active Directory tenant.</span></span>
  
 <span data-ttu-id="64298-p105">**ディレクトリ同期サーバーのみ**。64 ビットのディレクトリ同期サーバーを社内環境に展開する代わりに、仮想マシンをインターネット上で Azure にプロビジョニングします。</span><span class="sxs-lookup"><span data-stu-id="64298-p105">**Directory synchronization server only**. Instead of deploying the 64-bit directory synchronization server in your on-premises environment, you provision a virtual machine in Azure over the Internet.</span></span>
  
 <span data-ttu-id="64298-p106">**ディレクトリ同期 + AD FS**。このオプションにより、社内インフラストラクチャにハードウェアを追加しなくても、Office 365 フェデレーション ID (SSO) をサポートできます。さらに、社内の Active Directory 環境が使用できない場合に、回復性を提供します。このオプションには以下の機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="64298-p106">**Directory synchronization + AD FS**. This option allows you to support Office 365 federated identities (SSO) without adding hardware to your on-premises infrastructure. It also provides resiliency if the on-premises Active Directory environment is unavailable. The features of this option include:</span></span>
  
- <span data-ttu-id="64298-257">Azure 仮想マシンとして実行するディレクトリ統合コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="64298-257">Directory integration components run as Azure virtual machines.</span></span>
    
- <span data-ttu-id="64298-258">AD FS は、Azure 仮想マシンとして実行している AD FS プロキシを介してインターネットに公開されます。</span><span class="sxs-lookup"><span data-stu-id="64298-258">AD FS is published to the Internet through AD FS proxies running as Azure virtual machines.</span></span>
    
- <span data-ttu-id="64298-259">任意の場所から接続するユーザーのためのクライアント認証トラフィックは、Azure 仮想マシンとして展開された AD FS サーバーおよびプロキシにより処理されます。</span><span class="sxs-lookup"><span data-stu-id="64298-259">Client authentication traffic, for users that are connecting from any location, is handled by AD FS servers and proxies that are deployed as Azure virtual machines.</span></span>
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a><span data-ttu-id="64298-260">Office 365 内での Lync と Exchange、SharePoint との統合</span><span class="sxs-lookup"><span data-stu-id="64298-260">Lync integration with Exchange and SharePoint in Office 365</span></span>

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a><span data-ttu-id="64298-261">Lync Server を Exchange Online および SharePoint Online と併用する</span><span class="sxs-lookup"><span data-stu-id="64298-261">Lync Server with Exchange Online and SharePoint Online</span></span>

<span data-ttu-id="64298-262">付属の図は、Exchange Online や SharePoint Online が社内 Lync Server 2013 ファームに接続された Office 365 を示しています。</span><span class="sxs-lookup"><span data-stu-id="64298-262">The accompanying diagram shows Office 365 with Exchange Online and SharePoint Online connected to an on-premises Lync Server 2013 farm.</span></span>
  
<span data-ttu-id="64298-263">この展開の利点により、以下が可能になります。</span><span class="sxs-lookup"><span data-stu-id="64298-263">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="64298-264">Lync Server 2013 のフル機能セットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="64298-264">Use the full feature set of Lync Server 2013.</span></span>
    
- <span data-ttu-id="64298-265">PBX などの既存の社内電話機器を活用できます。</span><span class="sxs-lookup"><span data-stu-id="64298-265">Leverage your existing on-premises phone equipment, such as PBXs.</span></span>
    
- <span data-ttu-id="64298-266">Exchange Online を電子メールに使用して、社内の電子メール サーバーとストレージの負荷を軽減します。</span><span class="sxs-lookup"><span data-stu-id="64298-266">Use Exchange Online for email, off-loading the burden of on-premises email servers and storage.</span></span>
    
- <span data-ttu-id="64298-267">SharePoint Online を共同作業に使用して、社内の SharePoint サーバーを保守する負荷を軽減します。</span><span class="sxs-lookup"><span data-stu-id="64298-267">Use SharePoint Online for collaboration, off-loading the burden of maintaining on-premises SharePoint servers.</span></span>
    
- <span data-ttu-id="64298-268">Office 365 のユニファイド メッセージング (UM) など、Lync、Exchange、および SharePoint の統合機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="64298-268">Use Lync, Exchange, and SharePoint integrated features, including Unified Messaging (UM) in Office 365.</span></span>
    
#### <a name="exchange-server-with-lync-online"></a><span data-ttu-id="64298-269">Exchange Server と Lync Online</span><span class="sxs-lookup"><span data-stu-id="64298-269">Exchange Server with Lync Online</span></span>

<span data-ttu-id="64298-270">付属の図は、Lync Online が社内 Exchange Server ファームに接続された Office 365 を示しています。</span><span class="sxs-lookup"><span data-stu-id="64298-270">The accompanying diagram shows Office 365 with Lync Online connected to an on-premises Exchange Server farm.</span></span>
  
<span data-ttu-id="64298-271">この展開の利点により、以下が可能になります。</span><span class="sxs-lookup"><span data-stu-id="64298-271">The advantages of this deployment allow you to:</span></span>
  
- <span data-ttu-id="64298-272">既存の Exchange のインフラストラクチャを活用します。</span><span class="sxs-lookup"><span data-stu-id="64298-272">Leverage your existing Exchange infrastructure.</span></span>
    
- <span data-ttu-id="64298-273">Lync Online をプレゼンス、インスタント メッセージング、および会議の機能のために使用します。</span><span class="sxs-lookup"><span data-stu-id="64298-273">Use Lync Online for presence, instant messaging, and conferencing capabilities.</span></span>
    

