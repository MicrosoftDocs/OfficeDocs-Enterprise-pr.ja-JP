---
title: ハイブリッド クラウドの概要
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: '概要: Microsoft ハイブリッド クラウドの定義と要素について説明します。'
ms.openlocfilehash: 04c1a80009b1136ae4575ea4d454cebdb26bed3c
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123314"
---
# <a name="hybrid-cloud-overview"></a><span data-ttu-id="a6e42-103">ハイブリッド クラウドの概要</span><span class="sxs-lookup"><span data-stu-id="a6e42-103">Hybrid cloud overview</span></span>

 <span data-ttu-id="a6e42-104">**概要:** Microsoft ハイブリッド クラウドの定義と要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6e42-104">**Summary:** Understand the definition and elements of Microsoft hybrid cloud.</span></span>
  
<span data-ttu-id="a6e42-p101">ハイブリッド クラウドは、オンプレミス ネットワーク上またはクラウド内のコンピューティング リソースまたはストレージ リソースを使用します。全体的な IT 戦略の一環として、ビジネスおよびその IT のニーズをクラウドに移行するプロセスや、クラウド プラットフォームおよびサービスを既存のオンプレミス インフラストラクチャと統合するプロセスに、ハイブリッド クラウドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6e42-p101">Hybrid cloud uses compute or storage resources on your on-premises network and in the cloud. You can use hybrid cloud as a path to migrate your business and its IT needs to the cloud or integrate cloud platforms and services with your existing on-premises infrastructure as part of your overall IT strategy.</span></span>
  
## <a name="microsoft-hybrid-cloud"></a><span data-ttu-id="a6e42-107">Microsoft ハイブリッド クラウド</span><span class="sxs-lookup"><span data-stu-id="a6e42-107">Microsoft hybrid cloud</span></span>

<span data-ttu-id="a6e42-108">Microsoft ハイブリッド クラウドは、次のように Microsoft クラウド プラットフォームをオンプレミス コンポーネントと組み合わせるビジネス シナリオのセットです。</span><span class="sxs-lookup"><span data-stu-id="a6e42-108">Microsoft hybrid cloud is a set of business scenarios that combine a Microsoft cloud platform with an on-premises component, such as:</span></span> 
  
- <span data-ttu-id="a6e42-109">オンプレミスの SharePoint ファームと Office 365 の SharePoint Online の両方のコンテンツから検索結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="a6e42-109">Getting search results from content both in an on-premises SharePoint farm and in SharePoint Online in Office 365.</span></span>
    
- <span data-ttu-id="a6e42-110">オンプレミス データ ストアに対してクエリを実行する、Azure で実行されているモバイル アプリ。</span><span class="sxs-lookup"><span data-stu-id="a6e42-110">A mobile app running in Azure that queries an on-premises data store.</span></span>
    
- <span data-ttu-id="a6e42-111">Azure 仮想マシン上で実行されるイントラネット IT ワークロード。</span><span class="sxs-lookup"><span data-stu-id="a6e42-111">An intranet IT workload running on Azure virtual machines.</span></span>
    
<span data-ttu-id="a6e42-112">**図 1:Microsoft ハイブリッド クラウドのコンポーネント**</span><span class="sxs-lookup"><span data-stu-id="a6e42-112">**Figure 1: Components of the Microsoft hybrid cloud**</span></span>

![Microsoft ハイブリッド クラウドのコンポーネント](media/Hybrid-Poster/MS-Hybrid-Cloud.png)
  
<span data-ttu-id="a6e42-114">図 1 は、インターネットまたは ExpressRoute 接続を通して利用可能なオンプレミス ネットワークから Office 365 のセットまでの Microsoft ハイブリッド クラウド、Azure のサービスとしてのプラットフォーム (PaaS)、Azure のサービスとしてのインフラストラクチャ (IaaS) サービスを示しています。</span><span class="sxs-lookup"><span data-stu-id="a6e42-114">Figure 1 shows the components of the Microsoft hybrid cloud, from an on-premises network to the set of Office 365, Azure Platform as a Service (PaaS), and Azure Infrastructure as a Service (IaaS) services available across the Internet or an ExpressRoute connection.</span></span>
  
<span data-ttu-id="a6e42-115">Microsoft は、サービスとしてのソフトウェア (SaaS)、PaaS、および IaaS など、市場で最も包括的なクラウド ソリューションを有するため、次のことが可能です。</span><span class="sxs-lookup"><span data-stu-id="a6e42-115">Because Microsoft has the most complete cloud solution in the marketplace—including Software as a Service (SaaS), PaaS, and IaaS—you can:</span></span>
  
- <span data-ttu-id="a6e42-116">ワークロードとアプリケーションをクラウドに移行する際に、既存のオンプレミスの投資を活用します。</span><span class="sxs-lookup"><span data-stu-id="a6e42-116">Leverage your existing on-premises investments as you migrate workloads and applications to the cloud.</span></span>
    
- <span data-ttu-id="a6e42-117">たとえば、特定のデータまたはワークロードをクラウドに移行することが規制やポリシーで許可されていない場合に、ハイブリッド クラウド シナリオを長期的な IT 計画に組み込みます。</span><span class="sxs-lookup"><span data-stu-id="a6e42-117">Incorporate hybrid cloud scenarios into your long-term IT plans, for example, when regulations or policies do not permit moving specific data or workloads to the cloud.</span></span>
    
- <span data-ttu-id="a6e42-118">複数の Microsoft クラウド サービスおよびプラットフォームを含む追加のハイブリッド シナリオを作成します。</span><span class="sxs-lookup"><span data-stu-id="a6e42-118">Create additional hybrid scenarios that include multiple Microsoft cloud services and platforms.</span></span>
    
<span data-ttu-id="a6e42-119">Microsoft クラウド サービスを使用するハイブリッド クラウドのシナリオは、プラットフォームによって異なります。</span><span class="sxs-lookup"><span data-stu-id="a6e42-119">Scenarios for hybrid cloud with Microsoft cloud services vary with the platform.</span></span>
  
- <span data-ttu-id="a6e42-120">SaaS</span><span class="sxs-lookup"><span data-stu-id="a6e42-120">SaaS</span></span>
    
    <span data-ttu-id="a6e42-p102">マイクロソフトの SaaS のサービスには、Office 365、Microsoft Intune では、Microsoft Dynamics 365 などがあります。マイクロソフトの saas を利用してハイブリッド クラウドのシナリオでは、オンプレミスのサービスまたはアプリケーションでこれらのサービスを組み合わせます。たとえば、Office 365 で実行されている Exchange Online と統合できます Skype ビジネス 2019 は、オンプレミスで導入するのです。</span><span class="sxs-lookup"><span data-stu-id="a6e42-p102">Microsoft SaaS services include Office 365, Microsoft Intune, and Microsoft Dynamics 365. Hybrid cloud scenarios with Microsoft SaaS combine these services with on-premises services or applications. For example, Exchange Online running in Office 365 can be integrated with Skype for Business 2019 that is deployed on-premises.</span></span>
    
- <span data-ttu-id="a6e42-124">Azure PaaS</span><span class="sxs-lookup"><span data-stu-id="a6e42-124">Azure PaaS</span></span>
    
    <span data-ttu-id="a6e42-p103">Microsoft Azure PaaS サービスを使用すると、クラウドベースのアプリケーションを作成できます。Azure PaaS サービスを使ったハイブリッド クラウド シナリオでは、Azure PaaS アプリをオンプレミス リソースまたはアプリケーションと統合します。たとえば、Azure PaaS アプリ クラウドでは、モバイル アプリのユーザーに表示するのに必要な情報のオンプレミス データ ストアを安全に照会できます。</span><span class="sxs-lookup"><span data-stu-id="a6e42-p103">Microsoft Azure PaaS services allow you to create cloud-based applications. Hybrid cloud scenarios with Azure PaaS services combine an Azure PaaS app with on-premises resources or applications. For example, an Azure PaaS app could securely query an on-premises data store for information needed to display to mobile app users.</span></span>
    
- <span data-ttu-id="a6e42-128">Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="a6e42-128">Azure IaaS</span></span>
    
    <span data-ttu-id="a6e42-p104">Azure IaaS サービスを使用すると、オンプレミス データセンターではなく、クラウドで、サーバーベースの IT ワークロードをビルドし実行できます。通常、Azure IaaS サービスを使ったハイブリッド クラウド シナリオは、オンプレミス ネットワークに透過的に接続されている仮想マシンで実行される IT ワークロードで構成されます。オンプレミス ユーザーはこの違いに気付かないでしょう。</span><span class="sxs-lookup"><span data-stu-id="a6e42-p104">Azure IaaS services allow you to build and run server-based IT workloads in the cloud, rather than in your on-premises datacenter. Hybrid cloud scenarios with Azure IaaS services typically consist of an IT workload that runs on virtual machines that is transparently connected to your on-premises network. Your on-premises users will not notice the difference.</span></span>
    
## <a name="elements-of-hybrid-cloud"></a><span data-ttu-id="a6e42-132">ハイブリッド クラウドの要素</span><span class="sxs-lookup"><span data-stu-id="a6e42-132">Elements of hybrid cloud</span></span>

<span data-ttu-id="a6e42-133">Microsoft クラウド プラットフォームおよびサービスを使用するハイブリッド クラウド シナリオを計画して実装する際には、次の要素を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6e42-133">You must account for the following elements when planning and implementing hybrid cloud scenarios with Microsoft cloud platforms and services.</span></span>
  
- <span data-ttu-id="a6e42-134">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="a6e42-134">Networking</span></span>
    
    <span data-ttu-id="a6e42-p105">ハイブリッド クラウド シナリオのネットワークには、Microsoft クラウド プラットフォームおよびサービスへの接続と、負荷のピーク時に高パフォーマンスを実現するのに十分な帯域幅とが含まれています。詳細については、「[エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク](microsoft-cloud-networking-for-enterprise-architects.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a6e42-p105">Networking for hybrid cloud scenarios includes the connectivity to Microsoft cloud platforms and services and enough bandwidth to be performant under peak loads. For more information, see [Microsoft Cloud Networking for Enterprise Architects](microsoft-cloud-networking-for-enterprise-architects.md).</span></span>
    
- <span data-ttu-id="a6e42-137">Identity</span><span class="sxs-lookup"><span data-stu-id="a6e42-137">Identity</span></span>
    
    <span data-ttu-id="a6e42-p106">SaaS と Azure PaaS ハイブリッド シナリオの ID には、共通の ID プロバイダーとして Azure AD を含めることができます。このプロバイダーは、オンプレミスの Windows Server AD と同期するか、Windows Server AD またはその他の ID プロバイダーとフェデレーションすることができます。また、オンプレミスの ID インフラストラクチャを Azure IaaS に拡張することもできます。詳細については、「[エンタープライズ アーキテクトのための Microsoft クラウド ID](microsoft-cloud-it-architecture-resources.md#identity)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a6e42-p106">Identity for SaaS and Azure PaaS hybrid scenarios can include Azure AD as a common identity provider, which can be synchronized with your on-premises Windows Server AD, or federated with Windows Server AD or other identity providers. You can also extend your on-premises Identity infrastructure to Azure IaaS. For more information, see [Microsoft Cloud Identity for Enterprise Architects](microsoft-cloud-it-architecture-resources.md#identity).</span></span>
    
- <span data-ttu-id="a6e42-141">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a6e42-141">Security</span></span>
    
    <span data-ttu-id="a6e42-p107">ハイブリッド クラウド シナリオのセキュリティには、ID の保護と管理、データ保護、管理権限の管理、脅威の認識、およびガバナンスとセキュリティ ポリシーの実装が含まれます。詳細については、「[エンタープライズ アーキテクトのための Microsoft クラウドのセキュリティ](https://technet.microsoft.com/library/dn919927.aspx#security)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6e42-p107">Security for hybrid cloud scenarios includes protection and management for your identities, data protection, administrative privilege management, threat awareness, and the implementation of governance and security policies. For more information, see [Microsoft Cloud Security for Enterprise Architects](https://technet.microsoft.com/library/dn919927.aspx#security).</span></span>
    
- <span data-ttu-id="a6e42-144">管理</span><span class="sxs-lookup"><span data-stu-id="a6e42-144">Management</span></span>
    
    <span data-ttu-id="a6e42-p108">ハイブリッド クラウド シナリオの管理には、設定、データ、アカウント、ポリシー、およびアクセス許可を維持し、シナリオの要素の継続的な正常性およびそのパフォーマンスを監視する機能が含まれます。また、Azure IaaS での仮想マシンの管理にも、Systems Management Server などの同じツール セットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6e42-p108">Management for hybrid cloud scenarios includes the ability to maintain settings, data, accounts, policies, and permissions and to monitor the ongoing health of the elements of the scenario and its performance. You can also use the same tool set, such as Systems Management Server, for managing virtual machines in Azure IaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="a6e42-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6e42-147">See Also</span></span>

[<span data-ttu-id="a6e42-148">エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド</span><span class="sxs-lookup"><span data-stu-id="a6e42-148">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="a6e42-149">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="a6e42-149">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

