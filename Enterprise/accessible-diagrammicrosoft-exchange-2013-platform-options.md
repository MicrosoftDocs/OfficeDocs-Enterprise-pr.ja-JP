---
title: アクセス可能な図 - Microsoft Exchange 2013 プラットフォーム オプション
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 129f4e45-647e-4cf1-92a6-4d86d8396e73
f1.keywords:
- NOCSH
description: この記事は、Microsoft Exchange 2013 プラットフォーム オプションという名前のダイアグラム (技術ダイアグラム で利用できます) のアクセス可能なテキスト バージョンです。
ms.openlocfilehash: 56f77f7689270b60296848d41992652bf2068695
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844628"
---
# <a name="accessible-diagram---microsoft-exchange-2013-platform-options"></a><span data-ttu-id="f203d-103">アクセス可能な図 - Microsoft Exchange 2013 プラットフォーム オプション</span><span class="sxs-lookup"><span data-stu-id="f203d-103">Accessible diagram - Microsoft Exchange 2013 Platform Options</span></span>

<span data-ttu-id="f203d-104">**概要:** この記事は、Microsoft Exchange 2013 プラットフォーム オプションという名前のダイアグラム ([技術ダイアグラム](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409)で利用できます) のアクセス可能なテキスト バージョンです。</span><span class="sxs-lookup"><span data-stu-id="f203d-104">**Summary:** This article is an accessible text version of the diagram named Microsoft Exchange 2013 Platform Options, which is available at [Technical Diagrams](https://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).</span></span>
  
<span data-ttu-id="f203d-105">このポスターは、ビジネスの意思決定者 (Bdm) と設計者が Exchange Online および Exchange Server の展開に関して知る必要のある情報を説明しており、内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f203d-105">This poster describes what business decision makers (BDMs) and architects need to know about Exchange Online and Exchange Server deployments and includes:</span></span> 
  
- <span data-ttu-id="f203d-106">Exchange 2013 で使用可能な 4 つのプラットフォーム オプションの比較: Exchange Online (Office 365)、Exchange ハイブリッド、Exchange Server オンプレミス、プロバイダー向けのホスト型 Exchange。</span><span class="sxs-lookup"><span data-stu-id="f203d-106">A comparison of four available platform options for Exchange 2013: Exchange Online (Office 365), Exchange Hybrid, Exchange Server on-premises, and Provider-Hosted Exchange.</span></span> 
    
- <span data-ttu-id="f203d-107">Exchange 2013 での 3 つの新しいまたは更新された機能の説明。</span><span class="sxs-lookup"><span data-stu-id="f203d-107">Descriptions of three new or updated features in Exchange 2013.</span></span> 
    
## <a name="comparison-of-four-different-deployments-for-the-exchange-2013-platform"></a><span data-ttu-id="f203d-108">Exchange 2013 プラットフォーム用の 4 つの異なる展開の比較</span><span class="sxs-lookup"><span data-stu-id="f203d-108">Comparison of four different deployments for the Exchange 2013 platform</span></span>

<span data-ttu-id="f203d-109">比較の結果は以下の領域での各展開オプションに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f203d-109">The comparison provides information about each deployment option in the following areas:</span></span> 
  
- <span data-ttu-id="f203d-110">各種の展開機能の概要</span><span class="sxs-lookup"><span data-stu-id="f203d-110">An overview of the different deployment features</span></span> 
    
- <span data-ttu-id="f203d-111">各展開オプションを実装するメリット</span><span class="sxs-lookup"><span data-stu-id="f203d-111">Benefits of implementing each deployment option</span></span> 
    
- <span data-ttu-id="f203d-112">ライセンス要件</span><span class="sxs-lookup"><span data-stu-id="f203d-112">Licensing requirements</span></span> 
    
- <span data-ttu-id="f203d-113">必要なアーキテクチャ タスク</span><span class="sxs-lookup"><span data-stu-id="f203d-113">Required architectural tasks</span></span> 
    
- <span data-ttu-id="f203d-114">各展開オプションを実装するための IT 技術者の責任</span><span class="sxs-lookup"><span data-stu-id="f203d-114">IT Pro responsibilities for implementing each deployment option</span></span> 
    
### <a name="overview"></a><span data-ttu-id="f203d-115">概要</span><span class="sxs-lookup"><span data-stu-id="f203d-115">Overview</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="f203d-116">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="f203d-116">Exchange Online (Office 365)</span></span>

<span data-ttu-id="f203d-117">Office 365 によって効率を上げ、コストを下げられます。</span><span class="sxs-lookup"><span data-stu-id="f203d-117">You gain efficiency and reduce costs with Office 365.</span></span>
  
<span data-ttu-id="f203d-p101">付随する図は Exchange Online に伴う Azure Active Directory テナントを示しています。これは、オンプレミスの Active Directory ドメイン サービス (AD DS) 環境と Azure Active Directory テナントの間で、アカウント名およびパスワードを同期させます。シングル サインオンには Active Directory フェデレーション サービス (AD FS) が必要です。</span><span class="sxs-lookup"><span data-stu-id="f203d-p101">The accompanying diagram shows Exchange Online with an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span> 
  
<span data-ttu-id="f203d-120">フィーチャーと機能の説明:</span><span class="sxs-lookup"><span data-stu-id="f203d-120">Description of features and functionality:</span></span>
  
- <span data-ttu-id="f203d-121">サーバーおよびサーバー ソフトウェアの動作は、Microsoft によって処理されます。</span><span class="sxs-lookup"><span data-stu-id="f203d-121">The operation of servers and server software is handled by Microsoft.</span></span>
    
- <span data-ttu-id="f203d-122">クラウドベースのサービスとしての Exchange Server 2013 の豊富な機能セット。</span><span class="sxs-lookup"><span data-stu-id="f203d-122">Rich feature set of Exchange Server 2013 as a cloud-based service.</span></span>
    
- <span data-ttu-id="f203d-123">最新の機能で常に最新です。</span><span class="sxs-lookup"><span data-stu-id="f203d-123">Always up-to-date with the newest features.</span></span>
    
- <span data-ttu-id="f203d-124">スパム対策およびマルウェア対策の保護のため、Exchange Online Protection (EOP) が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="f203d-124">Exchange Online Protection (EOP) is included for anti-spam/anti-malware protection.</span></span>
    
- <span data-ttu-id="f203d-125">99.9% のサービス レベル契約 (SLA) を実現する組み込みの高可用性。</span><span class="sxs-lookup"><span data-stu-id="f203d-125">Built-in high availability with a 99.9% Service Level Agreement (SLA).</span></span>
    
- <span data-ttu-id="f203d-p102">オンプレミスの Active Directory ドメイン サービス (AD DS) と Azure Active Directory テナントとの間でのパスワードの同期を含む Directory 同期。シングル サインオンには Active Directory フェデレーション サービス (AD FS) が必要です。</span><span class="sxs-lookup"><span data-stu-id="f203d-p102">Directory synchronization including passwords between the on-premises Active Directory Domain Services (AD DS) and the Azure Active Directory tenant. Active Directory Federation Services (AD FS) is necessary for single sign-on.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="f203d-128">Exchange ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="f203d-128">Exchange Hybrid</span></span>

<span data-ttu-id="f203d-129">Exchange Server オンプレミスを維持しながら Office 365 の利点を活用できます。</span><span class="sxs-lookup"><span data-stu-id="f203d-129">You can leverage the benefits of Office 365 while maintaining Exchange Server on-premises.</span></span>
  
<span data-ttu-id="f203d-p103">付随する図は、一部のユーザーが社内に配置され、他のユーザーがオンラインに配置されている、Exchange Online での Office 365 を示しています。それには Azure Active Directory テナントも示されていますが、それは、オンプレミスの Active Directory ドメイン サービス (AD DS) 環境と Azure Active Directory テナントとの間でアカウント名およびパスワードを同期させます。</span><span class="sxs-lookup"><span data-stu-id="f203d-p103">The accompanying diagram shows Office 365 with Exchange Online where some users are homed on-premises and some users are homed online. It also shows an Azure Active Directory tenant which synchronizes account names and passwords between the on-premises Active Directory Domain Services (AD DS) environment and the Azure Active Directory tenant.</span></span>
  
<span data-ttu-id="f203d-132">フィーチャーと機能の説明:</span><span class="sxs-lookup"><span data-stu-id="f203d-132">Description of features and functionality:</span></span>
  
- <span data-ttu-id="f203d-133">一部のユーザーは社内に配置され、他のユーザーはオンラインに配置されていて、それらのユーザーは同じ電子メール アドレス スペースを共有します。</span><span class="sxs-lookup"><span data-stu-id="f203d-133">Some users are homed on-premises and some users are homed online, and users share the same e-mail address space.</span></span>
    
- <span data-ttu-id="f203d-134">既存の Exchange Server のインフラストラクチャを活用します。</span><span class="sxs-lookup"><span data-stu-id="f203d-134">Leverages your existing Exchange Server infrastructure.</span></span>
    
- <span data-ttu-id="f203d-135">スケジュールに従って、時の経過と共に Exchange オンプレミスから Exchange Online に移行します。</span><span class="sxs-lookup"><span data-stu-id="f203d-135">Migrate from Exchange on-premises to Exchange Online over time, on your schedule.</span></span>
    
- <span data-ttu-id="f203d-136">Lync Online や SharePoint Online など、他の Office 365 アプリケーションと統合します。</span><span class="sxs-lookup"><span data-stu-id="f203d-136">Integrate with other Office 365 applications, including Lync Online and SharePoint Online.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="f203d-137">Exchange Server オンプレミス</span><span class="sxs-lookup"><span data-stu-id="f203d-137">Exchange Server on-premises</span></span>

<span data-ttu-id="f203d-138">独自の Exchange Server 2013 インフラストラクチャを設計して管理できます。</span><span class="sxs-lookup"><span data-stu-id="f203d-138">You can design and manage your own Exchange Server 2013 infrastructure.</span></span>
  
<span data-ttu-id="f203d-139">付随する図は、オンプレミスの Active Directory ドメイン サービス (AD DS) 環境を持つ Exchange Server インフラストラクチャを示しています。ここでは、ユーザーは社内に配置されています。</span><span class="sxs-lookup"><span data-stu-id="f203d-139">The accompanying diagram shows an Exchange Server infrastructure with an on-premises Active Directory Domain Services (AD DS) environment where users are homed on-premises.</span></span>
  
<span data-ttu-id="f203d-140">フィーチャーと機能の説明:</span><span class="sxs-lookup"><span data-stu-id="f203d-140">Description of features and functionality:</span></span>
  
- <span data-ttu-id="f203d-141">ご使用の環境にとって最高度のコントロールとカスタマイズ。</span><span class="sxs-lookup"><span data-stu-id="f203d-141">Greatest degree of control and customization for your configuration.</span></span>
    
- <span data-ttu-id="f203d-142">負荷分散のレイヤーでセッション類似性を維持するための依存関係はありません。</span><span class="sxs-lookup"><span data-stu-id="f203d-142">No dependency on maintaining session affinity at the load balancing layer.</span></span>
    
- <span data-ttu-id="f203d-143">データベース可用性グループ (DAG) の使用によるシンプルな高可用性とサイト復元。</span><span class="sxs-lookup"><span data-stu-id="f203d-143">Simple high availability and site resilience using database availability groups (DAGs).</span></span>
    
- <span data-ttu-id="f203d-144">優れたユーザー エクスペリエンスを維持するのに役立つ、管理された可用性。</span><span class="sxs-lookup"><span data-stu-id="f203d-144">Managed availability that helps you maintain a great user experience.</span></span>
    
- <span data-ttu-id="f203d-145">既存のハードウェアと記憶域インフラストラクチャを活用できます。</span><span class="sxs-lookup"><span data-stu-id="f203d-145">Leverage existing hardware and storage infrastructure.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="f203d-146">プロバイダー向けのホスト型 Exchange</span><span class="sxs-lookup"><span data-stu-id="f203d-146">Provider-Hosted Exchange</span></span>

<span data-ttu-id="f203d-147">Exchange Server ワークロードを Exchange Server ソリューション プロバイダーにアウトソースすることができます。</span><span class="sxs-lookup"><span data-stu-id="f203d-147">You can outsource your Exchange Server workload to an Exchange Server solutions provider.</span></span>
  
<span data-ttu-id="f203d-148">付随する図は、プロバイダーによって操作され、管理される Exchange Server 環境を示しています。</span><span class="sxs-lookup"><span data-stu-id="f203d-148">The accompanying diagram shows an Exchange Server environment that is operated and maintained by a provider.</span></span>
  
<span data-ttu-id="f203d-149">フィーチャーと機能の説明:</span><span class="sxs-lookup"><span data-stu-id="f203d-149">Description of features and functionality:</span></span>
  
- <span data-ttu-id="f203d-150">サーバーおよびサーバー ソフトウェアの動作は、プロバイダーによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="f203d-150">The operation of servers and server software is handled by your provider.</span></span>
    
- <span data-ttu-id="f203d-151">Exchange Server インフラストラクチャの計画、サイズ変更、スケール、および保守は、プロバイダーに委任されます。</span><span class="sxs-lookup"><span data-stu-id="f203d-151">Planning, sizing, scaling, and maintenance of the Exchange Server infrastructure are delegated to your provider.</span></span>
    
- <span data-ttu-id="f203d-152">サービスの保守は、プロバイダーによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="f203d-152">Service maintenance is handled by your provider.</span></span>
    
- <span data-ttu-id="f203d-153">Exchange の機能セットは、プロバイダーで展開されているソフトウェアのバージョンに限定されます。</span><span class="sxs-lookup"><span data-stu-id="f203d-153">The Exchange feature set is limited to the software version deployed by your provider.</span></span>
    
### <a name="benefits-of-implementing-each-deployment-option"></a><span data-ttu-id="f203d-154">各展開オプションを実装するメリット</span><span class="sxs-lookup"><span data-stu-id="f203d-154">Benefits of implementing each deployment option</span></span>

#### <a name="exchange-online-office-365"></a><span data-ttu-id="f203d-155">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="f203d-155">Exchange Online (Office 365)</span></span>

<span data-ttu-id="f203d-156">この展開オプションは次の場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="f203d-156">This deployment option is best for:</span></span>
  
- <span data-ttu-id="f203d-157">オンプレミスの Exchange 展開のための運用コストの削減を検討している組織。</span><span class="sxs-lookup"><span data-stu-id="f203d-157">Organizations looking to reduce operations costs for on-premises Exchange deployments.</span></span>
    
- <span data-ttu-id="f203d-158">SharePoint Online や Lync Online など、他の Office 365 提供物を活用することを計画している組織。</span><span class="sxs-lookup"><span data-stu-id="f203d-158">Organizations that plan to leverage other Office 365 offerings, such as SharePoint Online and Lync Online.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="f203d-159">Exchange ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="f203d-159">Exchange Hybrid</span></span>

<span data-ttu-id="f203d-160">この展開オプションは次の場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="f203d-160">This deployment option is best for:</span></span>
  
- <span data-ttu-id="f203d-161">Exchange オンプレミスから Exchange Online への移行を容易にします。</span><span class="sxs-lookup"><span data-stu-id="f203d-161">Facilitating a migration from Exchange on-premises to Exchange Online.</span></span>
    
- <span data-ttu-id="f203d-162">支店のインフラストラクチャに投資することなく、リモート サイトをサポートします。</span><span class="sxs-lookup"><span data-stu-id="f203d-162">Supporting remote sites without investing in branch office infrastructure.</span></span>
    
- <span data-ttu-id="f203d-163">データを社内で保持する必要のある、子会社を持つ多国籍企業。</span><span class="sxs-lookup"><span data-stu-id="f203d-163">Multinational corporations with subsidiaries that require data to reside on-premises.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="f203d-164">Exchange Server オンプレミス</span><span class="sxs-lookup"><span data-stu-id="f203d-164">Exchange Server on-premises</span></span>

<span data-ttu-id="f203d-165">この展開オプションは次の場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="f203d-165">This deployment option is best for:</span></span>
  
- <span data-ttu-id="f203d-166">高度にカスタマイズされたソリューション。</span><span class="sxs-lookup"><span data-stu-id="f203d-166">Highly customized solutions.</span></span>
    
- <span data-ttu-id="f203d-167">Exchange Online でサポートされていないハードウェアおよびソフトウェアに依存するサード パーティ製コンポーネントを使用するレガシー ソリューション。</span><span class="sxs-lookup"><span data-stu-id="f203d-167">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
- <span data-ttu-id="f203d-168">データを社内で保持することを必要とするデータ ガバナンス規制のもとにある組織。</span><span class="sxs-lookup"><span data-stu-id="f203d-168">Organizations subject to data governance regulations that require data to reside on-premises.</span></span>
    
- <span data-ttu-id="f203d-169">プラットフォームとソリューションの全体のコントールを維持することを求める組織。</span><span class="sxs-lookup"><span data-stu-id="f203d-169">Organizations that wish to retain control of the entire platform and solution.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="f203d-170">プロバイダー向けのホスト型 Exchange</span><span class="sxs-lookup"><span data-stu-id="f203d-170">Provider-Hosted Exchange</span></span>

<span data-ttu-id="f203d-171">この展開オプションは次の場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="f203d-171">This deployment option is best for:</span></span>
  
- <span data-ttu-id="f203d-172">Exchange Server の機能を必要とするものの、その展開と保守を外部委託することを希望している組織。</span><span class="sxs-lookup"><span data-stu-id="f203d-172">Organizations that need Exchange Server functionality, but want to outsource its deployment and maintenance.</span></span>
    
- <span data-ttu-id="f203d-173">個人用のサポート オプションが必要な組織。</span><span class="sxs-lookup"><span data-stu-id="f203d-173">Organizations that need personalized support options.</span></span>
    
- <span data-ttu-id="f203d-174">カスタマイズしたソリューションと、プロバイダーによって提供されるカスタム アプリケーションとの統合。</span><span class="sxs-lookup"><span data-stu-id="f203d-174">Customized solutions and integration with custom applications offered by the provider.</span></span>
    
- <span data-ttu-id="f203d-175">Exchange Online でサポートされていないハードウェアおよびソフトウェアに依存するサード パーティ製コンポーネントを使用するレガシー ソリューション。</span><span class="sxs-lookup"><span data-stu-id="f203d-175">Legacy solutions with third-party components that depend on hardware and software that are not supported by Exchange Online.</span></span>
    
### <a name="license-requirements"></a><span data-ttu-id="f203d-176">ライセンス要件</span><span class="sxs-lookup"><span data-stu-id="f203d-176">License requirements</span></span>

<span data-ttu-id="f203d-177">次の表は、各展開オプションのライセンス要件の詳細を示しています。</span><span class="sxs-lookup"><span data-stu-id="f203d-177">The following table details the license requirements for each deployment option.</span></span>
  
|<span data-ttu-id="f203d-178">**展開オプション**</span><span class="sxs-lookup"><span data-stu-id="f203d-178">**Deployment option**</span></span>|<span data-ttu-id="f203d-179">**ライセンス要件**</span><span class="sxs-lookup"><span data-stu-id="f203d-179">**License requirements**</span></span>|
|:-----|:-----|
|<span data-ttu-id="f203d-180">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="f203d-180">Exchange Online (Office 365)</span></span>  <br/> |<span data-ttu-id="f203d-181">サブスクリプション モデル</span><span class="sxs-lookup"><span data-stu-id="f203d-181">Subscription model</span></span>  <br/> |
|<span data-ttu-id="f203d-182">Exchange ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="f203d-182">Exchange Hybrid</span></span>  <br/> | <span data-ttu-id="f203d-183">Office 365 - サブスクリプション モデル</span><span class="sxs-lookup"><span data-stu-id="f203d-183">Office 365 - Subscription model</span></span> <br/>  <span data-ttu-id="f203d-184">オンプレミス - すべてのオンプレミス ライセンスが当てはまります (Exchanges Server オンプレミスのライセンスを確認してください)</span><span class="sxs-lookup"><span data-stu-id="f203d-184">On-premises - All on-premises licenses apply (review licenses for Exchanges Server on-premises)</span></span> <br/>  <span data-ttu-id="f203d-185">ハイブリッド サーバー ライセンス \*</span><span class="sxs-lookup"><span data-stu-id="f203d-185">Hybrid server license\*</span></span> <br/> |
|<span data-ttu-id="f203d-186">Exchange Server オンプレミス</span><span class="sxs-lookup"><span data-stu-id="f203d-186">Exchange Server on-premises</span></span>  <br/> | <span data-ttu-id="f203d-187">サーバー オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="f203d-187">Server Operating System</span></span> <br/>  <span data-ttu-id="f203d-188">Exchange 2013 サーバー ライセンス</span><span class="sxs-lookup"><span data-stu-id="f203d-188">Exchange 2013 Server License</span></span> <br/>  <span data-ttu-id="f203d-189">Exchange 2013 クライアント アクセス ライセンス</span><span class="sxs-lookup"><span data-stu-id="f203d-189">Exchange 2013 Client Access License</span></span> <br/> |
|<span data-ttu-id="f203d-190">プロバイダー向けのホスト型 Exchange</span><span class="sxs-lookup"><span data-stu-id="f203d-190">Provider-Hosted Exchange</span></span>  <br/> |<span data-ttu-id="f203d-191">コストは、プロバイダーとの契約に基づきます</span><span class="sxs-lookup"><span data-stu-id="f203d-191">Costs are based on the agreement with the provider</span></span>  <br/> |
   
### <a name="architecture-tasks"></a><span data-ttu-id="f203d-192">アーキテクチャ タスク</span><span class="sxs-lookup"><span data-stu-id="f203d-192">Architecture tasks</span></span>

<span data-ttu-id="f203d-193">ここでは各展開オプションのアーキテクチャのタスクを示します。</span><span class="sxs-lookup"><span data-stu-id="f203d-193">This section lists the architectural tasks for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="f203d-194">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="f203d-194">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="f203d-195">ディレクトリ同期を計画および設計します。</span><span class="sxs-lookup"><span data-stu-id="f203d-195">Plan and design the directory synchronization.</span></span>
    
- <span data-ttu-id="f203d-196">ネットワーク容量を確認し、ファイアウォール、プロキシ サーバー、ゲートウェイ、および WAN リンクを介した接続を確認します。</span><span class="sxs-lookup"><span data-stu-id="f203d-196">Ensure network capacity and connectivity through firewalls, proxy servers, gateways, and across WAN links.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="f203d-197">Exchange ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="f203d-197">Exchange Hybrid</span></span>

<span data-ttu-id="f203d-198">Office 365 環境とオンプレミス環境の両方のアーキテクチャ タスクに加えて:</span><span class="sxs-lookup"><span data-stu-id="f203d-198">In addition to the architecture tasks for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="f203d-199">シングル サインオン エクスペリエンスを提供するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="f203d-199">Decide whether to provide a single-sign on experience.</span></span>
    
- <span data-ttu-id="f203d-200">受信インターネット メールを社内組織を通してルーティングするか、 Exchange Online Protection を介してルーティングするかを決定します。</span><span class="sxs-lookup"><span data-stu-id="f203d-200">Decide whether to route inbound Internet mail through an on-premises organization or through Exchange Online Protection.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="f203d-201">Exchange Server オンプレミス</span><span class="sxs-lookup"><span data-stu-id="f203d-201">Exchange Server on-premises</span></span>

- <span data-ttu-id="f203d-202">Exchange トポロジを設計します。</span><span class="sxs-lookup"><span data-stu-id="f203d-202">Design the Exchange topology.</span></span>
    
- <span data-ttu-id="f203d-203">サーバー ハードウェアの容量を計画します。</span><span class="sxs-lookup"><span data-stu-id="f203d-203">Plan the capacity for server hardware.</span></span>
    
- <span data-ttu-id="f203d-204">メッセージのルーティング トポロジを設計します。</span><span class="sxs-lookup"><span data-stu-id="f203d-204">Design the message routing topology.</span></span>
    
- <span data-ttu-id="f203d-205">クライアント アクセス サーバーの負荷分散を設計します。</span><span class="sxs-lookup"><span data-stu-id="f203d-205">Design load balancing for Client Access servers.</span></span>
    
- <span data-ttu-id="f203d-206">データベース可用性グループを使用して高可用性を計画します。</span><span class="sxs-lookup"><span data-stu-id="f203d-206">Plan for high availability using database availability groups.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="f203d-207">プロバイダー向けのホスト型 Exchange</span><span class="sxs-lookup"><span data-stu-id="f203d-207">Provider-Hosted Exchange</span></span>

<span data-ttu-id="f203d-208">ネットワーク容量を確認し、ファイアウォール、プロキシ サーバー、ゲートウェイ、および WAN リンクを介した可用性がプロバイダーで使用可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f203d-208">Ensure that the network capacity and availability through firewalls, proxy servers, gateways, and across WAN links are available to your provider.</span></span>
  
### <a name="it-pro-responsibilities"></a><span data-ttu-id="f203d-209">IT 技術者の責任</span><span class="sxs-lookup"><span data-stu-id="f203d-209">IT Pro responsibilities</span></span>

<span data-ttu-id="f203d-210">ここでは、各展開オプションについて、IT 担当者の責任を示します。</span><span class="sxs-lookup"><span data-stu-id="f203d-210">This section lists the IT Pro responsibilities for each deployment option.</span></span>
  
#### <a name="exchange-online-office-365"></a><span data-ttu-id="f203d-211">Exchange Online (Office 365)</span><span class="sxs-lookup"><span data-stu-id="f203d-211">Exchange Online (Office 365)</span></span>

- <span data-ttu-id="f203d-212">ディレクトリ同期の計画を実装します。</span><span class="sxs-lookup"><span data-stu-id="f203d-212">Implement the directory synchronization plan.</span></span>
    
- <span data-ttu-id="f203d-213">内部および外部の DNS レコードとルーティングを計画し、実装します。</span><span class="sxs-lookup"><span data-stu-id="f203d-213">Plan and implement internal and external DNS records and routing.</span></span>
    
- <span data-ttu-id="f203d-214">Office 365 の IP アドレスおよび URL の要件に合うように、プロキシ サーバーまたはファイアウォールを構成します。</span><span class="sxs-lookup"><span data-stu-id="f203d-214">Configure the proxy server or firewall for the Office 365 IP address and URL requirements.</span></span>
    
- <span data-ttu-id="f203d-215">ユーザー アカウントと Exchange Online の設定を管理します。</span><span class="sxs-lookup"><span data-stu-id="f203d-215">Administer the user accounts and the Exchange Online settings.</span></span>
    
#### <a name="exchange-hybrid"></a><span data-ttu-id="f203d-216">Exchange ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="f203d-216">Exchange Hybrid</span></span>

<span data-ttu-id="f203d-217">Office 365 環境とオンプレミス環境の両方の IT 技術者の責任に加えて:</span><span class="sxs-lookup"><span data-stu-id="f203d-217">In addition to the IT Pro responsibilities for both the Office 365 and on-premises environments:</span></span>
  
- <span data-ttu-id="f203d-218">Active Directory フェデレーション サービス (AD FS) をシングル サインオン用に構成します (希望する場合)。</span><span class="sxs-lookup"><span data-stu-id="f203d-218">Configure Active Directory Federation Services (AD FS) for single-sign on (if desired).</span></span>
    
- <span data-ttu-id="f203d-219">Exchange 2013 サーバーと Office 365 との保護された通信のために、Exchange 証明書を構成します。</span><span class="sxs-lookup"><span data-stu-id="f203d-219">Configure Exchange certificates for secure communications between Exchange 2013 servers and Office 365.</span></span>
    
- <span data-ttu-id="f203d-220">DNS レコードを、希望する受信インターネット メール パス向けに構成します。</span><span class="sxs-lookup"><span data-stu-id="f203d-220">Configure DNS records for the desired inbound Internet mail path.</span></span>
    
#### <a name="exchange-server-on-premises"></a><span data-ttu-id="f203d-221">Exchange Server オンプレミス</span><span class="sxs-lookup"><span data-stu-id="f203d-221">Exchange Server on-premises</span></span>

- <span data-ttu-id="f203d-222">Exchange サービスのために必要な証明書を構成します。</span><span class="sxs-lookup"><span data-stu-id="f203d-222">Configure the necessary certificates for Exchange services.</span></span>
    
- <span data-ttu-id="f203d-223">サーバーを準備します。</span><span class="sxs-lookup"><span data-stu-id="f203d-223">Provision the servers.</span></span>
    
- <span data-ttu-id="f203d-224">Exchange のメッセージ ルーティング トポロジを実装します。</span><span class="sxs-lookup"><span data-stu-id="f203d-224">Implement the Exchange message routing topology.</span></span>
    
- <span data-ttu-id="f203d-225">データベース可用性グループを実装します。</span><span class="sxs-lookup"><span data-stu-id="f203d-225">Implement database availability groups.</span></span>
    
- <span data-ttu-id="f203d-226">Exchange サーバーを更新し、維持します。</span><span class="sxs-lookup"><span data-stu-id="f203d-226">Update and maintain Exchange servers.</span></span>
    
- <span data-ttu-id="f203d-227">使用率に応じて、必要なときにサーバーを追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="f203d-227">Depending on utilization, add or remove servers as needed.</span></span>
    
#### <a name="provider-hosted-exchange"></a><span data-ttu-id="f203d-228">プロバイダー向けのホスト型 Exchange</span><span class="sxs-lookup"><span data-stu-id="f203d-228">Provider-Hosted Exchange</span></span>

<span data-ttu-id="f203d-229">プロバイダーの責任は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f203d-229">The provider's responsibilities include:</span></span>
  
- <span data-ttu-id="f203d-230">システムとサービスの保守。</span><span class="sxs-lookup"><span data-stu-id="f203d-230">System and service maintenance.</span></span>
    
- <span data-ttu-id="f203d-231">機能の展開。</span><span class="sxs-lookup"><span data-stu-id="f203d-231">Feature rollouts.</span></span>
    
- <span data-ttu-id="f203d-232">データの保護と災害復旧。</span><span class="sxs-lookup"><span data-stu-id="f203d-232">Data protection and disaster recovery.</span></span>
    
<span data-ttu-id="f203d-233">組織内の IT スタッフの責任には、ユーザー アカウントの作成と管理が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f203d-233">The IT staff's responsibilities in your organization include creating and managing user accounts.</span></span>
  
#### <a name="more-information"></a><span data-ttu-id="f203d-234">詳細情報</span><span class="sxs-lookup"><span data-stu-id="f203d-234">More information</span></span>

<span data-ttu-id="f203d-235">Exchange Online (Office 365) の詳細については、以下を参照してください:</span><span class="sxs-lookup"><span data-stu-id="f203d-235">To learn more about Exchange Online (Office 365), see the following:</span></span>
  
- [<span data-ttu-id="f203d-236">Exchange Online サービスの説明</span><span class="sxs-lookup"><span data-stu-id="f203d-236">Exchange Online service description</span></span>](https://aka.ms/EXOSD)
    
- [<span data-ttu-id="f203d-237">TechNet の Exchange Online のライブラリ</span><span class="sxs-lookup"><span data-stu-id="f203d-237">Exchange Online library on TechNet</span></span>](https://aka.ms/EXOTN)
    
- [<span data-ttu-id="f203d-238">Exchange Online ポータル</span><span class="sxs-lookup"><span data-stu-id="f203d-238">Exchange Online portal</span></span>](https://aka.ms/EXO)
    
<span data-ttu-id="f203d-239">Exchange ハイブリッドの詳細については、以下を参照してください:</span><span class="sxs-lookup"><span data-stu-id="f203d-239">To learn more about Exchange Hybrid, see the following:</span></span>
  
- <span data-ttu-id="f203d-p104">[Exchange 2013 ハイブリッド展開](https://aka.ms/ExchangeHybrid)。ハイブリッド サーバーのライセンスが必要になるのは、以下のシナリオの場合だけです: Exchange 2013 のハイブリッド サーバーと共に Exchange 2010 を持つ組織。Exchange 2013 または Exchange 2010 のハイブリッド サーバーと共に Exchange 2007 を持つ組織。</span><span class="sxs-lookup"><span data-stu-id="f203d-p104">[Exchange 2013 hybrid deployments](https://aka.ms/ExchangeHybrid). You should note that the Hybrid server license is only required for the following scenarios: Exchange 2010 organization with Exchange 2013 hybrid server and Exchange 2007 organization with Exchange 2013 or Exchange 2010 hybrid server.</span></span>
    
- [<span data-ttu-id="f203d-242">Office 365 へのサインイン</span><span class="sxs-lookup"><span data-stu-id="f203d-242">Office 365 Sign in</span></span>](https://aka.ms/HybridKey)
    
<span data-ttu-id="f203d-243">Exchange Server オンプレミスの詳細については、以下を参照してください:</span><span class="sxs-lookup"><span data-stu-id="f203d-243">To learn more about Exchange Server on-premises, see the following:</span></span>
  
- [<span data-ttu-id="f203d-244">TechNet の Exchange Server 2013 ライブラリ</span><span class="sxs-lookup"><span data-stu-id="f203d-244">Exchange Server 2013 library on TechNet</span></span>](https://aka.ms/Ex2013TN)
    
- [<span data-ttu-id="f203d-245">Exchange Server 2013 ポータル</span><span class="sxs-lookup"><span data-stu-id="f203d-245">Exchange Server 2013 portal</span></span>](https://aka.ms/Exchange2013)
    
- [<span data-ttu-id="f203d-246">Exchange Server 2013 のアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="f203d-246">Exchange Server 2013 architecture</span></span>](https://aka.ms/Ex2013SP1ArchPoster)
    
<span data-ttu-id="f203d-247">プロバイダー向けのホスト型 Exchange の詳細については、以下を参照してください:</span><span class="sxs-lookup"><span data-stu-id="f203d-247">To learn more about Provider-Hosted Exchange, see the following:</span></span>
  
[<span data-ttu-id="f203d-248">Exchange Server 2013 のホスティングおよびマルチ テナント ソリューションとガイダンス</span><span class="sxs-lookup"><span data-stu-id="f203d-248">Exchange Server 2013 hosting and multi-tenancy solutions and guidance</span></span>](https://aka.ms/Ex2013Hosting)
  
## <a name="descriptions-of-three-new-or-updated-features-in-exchange-2013"></a><span data-ttu-id="f203d-249">Exchange 2013 での 3 つの新規または更新された機能の説明</span><span class="sxs-lookup"><span data-stu-id="f203d-249">Descriptions of three new or updated features in Exchange 2013</span></span>

### <a name="exchange-online-protection"></a><span data-ttu-id="f203d-250">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="f203d-250">Exchange Online Protection</span></span>

<span data-ttu-id="f203d-p105">Exchange Online Protection (EOP) は、データ センターのグローバルなネットワークにまたがって展開された保護機能の層を提供することによって、任意の展開のためのスパム対策およびマルウェア対策の保護を提供します。これにより、メッセージング環境の管理を簡略化することができます。EOP は Exchange Online のサブスクリプションに含まれていますが、ハイブリッド展開およびオンプレミス展開のためにそれを活用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f203d-p105">Exchange Online Protection (EOP) provides anti-spam and anti-malware protection for any deployment by providing a layer of protection features that are deployed across a global network of data centers. This helps you to simplify the management of your messaging environments. EOP is included in Exchange Online subscriptions, but you can also leverage it for hybrid and on-premises deployments.</span></span>
  
<span data-ttu-id="f203d-254">付随する図は、グローバル ネットワーク内に EOP を含む、Exchange Online、Exchange ハイブリッド、および Exchange オンプレミスの展開を示しています。</span><span class="sxs-lookup"><span data-stu-id="f203d-254">The accompanying diagrams show deployments for Exchange Online, Exchange Hybrid, and Exchange on-premises that include the EOP layer in the global network.</span></span>
  
### <a name="exchange-server-deployment-assistant"></a><span data-ttu-id="f203d-255">Exchange Server 展開アシスタント</span><span class="sxs-lookup"><span data-stu-id="f203d-255">Exchange Server Deployment Assistant</span></span>

<span data-ttu-id="f203d-p106">Exchange Server 展開アシスタントは、現在の環境に関するいくつかの点に関して質問してから、カスタムのステップごとのチェックリストを生成することにより、各種のシナリオに対して Exchange Server を展開するのを支援する、Web ベースのツールです。以前のバージョンの Exchange から Exchange 2013 に移行しているか、Exchange Online に移行しているか、あるいはハイブリッド インフラストラクチャを計画しているかどうかに応じて、Exchange Server 展開アシスタントは、ご使用のシナリオ向けの、カスタマイズされた展開チェックリストを作成します。</span><span class="sxs-lookup"><span data-stu-id="f203d-p106">The Exchange Server Deployment Assistant is a web-based tool that asks you a few questions about your current environment, and then generates a custom step-by-step checklist to help you deploy Exchange Server for different types of scenarios. Whether you are migrating from a previous version of Exchange to Exchange 2013, migrating to Exchange Online, or planning a hybrid infrastructure, the Exchange Server Deployment Assistant creates a customized deployment checklist for your scenario.</span></span>
  
<span data-ttu-id="f203d-258">付随するスクリーン ショットは、Exchange Server 展開アシスタントを使用して作成されたチェックリスト例を示しています。</span><span class="sxs-lookup"><span data-stu-id="f203d-258">The accompanying screenshot shows an example checklist that was created using the Exchange Server Deployment Assistant.</span></span>
  
### <a name="integration-with-lync-and-sharepoint"></a><span data-ttu-id="f203d-259">Lync および SharePoint との統合</span><span class="sxs-lookup"><span data-stu-id="f203d-259">Integration with Lync and SharePoint</span></span>

<span data-ttu-id="f203d-p107">Exchange Server 2013 には、Lync Server 2013 および SharePoint Server 2013 と統合する多くの機能が含まれています。これらの製品が一緒になって、豊富な一連の機能が提供され、組織全体での共同作業が向上します。</span><span class="sxs-lookup"><span data-stu-id="f203d-p107">Exchange Server 2013 includes many features that integrate with Lync Server 2013 and SharePoint Server 2013. Together, these products offer a rich suite of features and improve collaboration across your organization.</span></span> 
  
<span data-ttu-id="f203d-262">付随する図はサーバー間認証のポスターを示し、ポスターへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f203d-262">An accompanying diagram shows the Server-to-Server Authentication poster and includes a link to the poster.</span></span> 
  
- <span data-ttu-id="f203d-263">アーカイブ、保持、および電子情報開示</span><span class="sxs-lookup"><span data-stu-id="f203d-263">Archiving, hold and eDiscovery</span></span>
    
- <span data-ttu-id="f203d-264">サイト メールボックス</span><span class="sxs-lookup"><span data-stu-id="f203d-264">Site mailboxes</span></span>
    
- <span data-ttu-id="f203d-265">統合連絡先ストア</span><span class="sxs-lookup"><span data-stu-id="f203d-265">Unified contact store</span></span>
    
- <span data-ttu-id="f203d-266">高解像度のユーザーの写真</span><span class="sxs-lookup"><span data-stu-id="f203d-266">High-resolution user photos</span></span>
    
- <span data-ttu-id="f203d-267">Outlook および Outlook Web App での Lync プレゼンス</span><span class="sxs-lookup"><span data-stu-id="f203d-267">Lync presence in Outlook and Outlook Web App</span></span>
    
- <span data-ttu-id="f203d-268">サーバー間認証</span><span class="sxs-lookup"><span data-stu-id="f203d-268">Server-to-server authentication</span></span>
    
- <span data-ttu-id="f203d-269">ボイスメール</span><span class="sxs-lookup"><span data-stu-id="f203d-269">Voicemail</span></span>
    
- <span data-ttu-id="f203d-270">ミーティングのレコーディング</span><span class="sxs-lookup"><span data-stu-id="f203d-270">Meeting recordings</span></span>
    
- <span data-ttu-id="f203d-271">Exchange タスクの同期</span><span class="sxs-lookup"><span data-stu-id="f203d-271">Exchange task synchronization</span></span>
    
<span data-ttu-id="f203d-272">付随する図は Exchange Server 2013 SP1 アーキテクチャのポスターを示し、ポスターへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f203d-272">An accompanying diagram shows the Exchange Server 2013 SP1 Architecture poster and includes a link to the poster.</span></span>
  

