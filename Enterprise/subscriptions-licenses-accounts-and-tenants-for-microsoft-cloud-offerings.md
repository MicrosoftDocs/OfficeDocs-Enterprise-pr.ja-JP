---
title: "ライセンス、サブスクリプション、アカウント、およびマイクロソフトのクラウド サービスのテナント"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: "概要: は、マイクロソフトのクラウド サービスの間で、組織、サブスクリプション、ライセンス、ユーザー アカウント、およびテナント間の関係を理解します。"
ms.openlocfilehash: a1bcc040d046e4e5674f16432aeffb0a34b9031b
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2018
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="c1647-103">ライセンス、サブスクリプション、アカウント、およびマイクロソフトのクラウド サービスのテナント</span><span class="sxs-lookup"><span data-stu-id="c1647-103">Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings</span></span>

 <span data-ttu-id="c1647-104">**の概要:**マイクロソフトのクラウド サービスの間では、組織、サブスクリプション、ライセンス、ユーザー アカウント、およびテナント間の関係を理解します。</span><span class="sxs-lookup"><span data-stu-id="c1647-104">**Summary:** Understand the relationships of organizations, subscriptions, licenses, user accounts, and tenants across Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="c1647-105">マイクロソフトでは、そのクラウド サービス間での id と請求の一貫した使用法の組織、サブスクリプション、ライセンス、およびユーザー アカウントの階層構造を提供します。</span><span class="sxs-lookup"><span data-stu-id="c1647-105">Microsoft provides a hierarchy of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="c1647-106">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="c1647-106">Microsoft Office 365</span></span>
    
    <span data-ttu-id="c1647-107">[ビジネス プランと価格設定](https://products.office.com/business/compare-office-365-for-business-plans)の詳細についてを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1647-107">See [business plans and pricing](https://products.office.com/business/compare-office-365-for-business-plans) for more information.</span></span>
    
- <span data-ttu-id="c1647-108">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="c1647-108">Microsoft Azure</span></span>
    
    <span data-ttu-id="c1647-109">詳細については、 [Azure の価格](https://azure.microsoft.com/pricing/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1647-109">See [Azure pricing](https://azure.microsoft.com/pricing/) for more information.</span></span>
    
- <span data-ttu-id="c1647-110">Microsoft Intune と、エンタープライズ モビリティとセキュリティ (EMS)</span><span class="sxs-lookup"><span data-stu-id="c1647-110">Microsoft Intune and the Enterprise Mobility + Security (EMS)</span></span>
    
    <span data-ttu-id="c1647-111">詳細については、 [Intune の価格](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1647-111">See [Intune pricing](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing) for more information.</span></span>
    
- <span data-ttu-id="c1647-112">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="c1647-112">Microsoft Dynamics 365</span></span>
    
    <span data-ttu-id="c1647-113">詳細については、 [Dynamics 365 の価格](https://dynamics.microsoft.com/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1647-113">See [Dynamics 365 pricing](https://dynamics.microsoft.com/) for more information.</span></span>
    
## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="c1647-114">階層の要素</span><span class="sxs-lookup"><span data-stu-id="c1647-114">Elements of the hierarchy</span></span>

<span data-ttu-id="c1647-115">階層の要素を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="c1647-115">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="c1647-116">組織</span><span class="sxs-lookup"><span data-stu-id="c1647-116">Organization</span></span>

<span data-ttu-id="c1647-117">組織は、Microsoft クラウド製品を使用しているビジネス エンティティを表します。通常は、パブリック ドメイン ネーム システム (DNS) のドメイン名 (例: contoso.com) で識別されます。組織は、サブスクリプションのコンテナーになります。</span><span class="sxs-lookup"><span data-stu-id="c1647-117">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by a public Domain Name System (DNS) domain name such as contoso.com. The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="c1647-118">サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="c1647-118">Subscriptions</span></span>

<span data-ttu-id="c1647-p101">サブスクリプションは、1 つを使用するには、Microsoft と契約、またはユーザーごとのライセンス料金またはクラウド ベースのリソースの消費量に基づくさらにマイクロソフトのクラウド プラットフォームやサービス、諸費用を計上します。サービス (SaaS) としてマイクロソフトのソフトウェア ・ ベースのクラウド ・ サービス (Office 365、Intune と EMS では、Dynamics 365) は、ユーザーごとのライセンス料金を請求します。(PaaS) およびインフラストラクチャをクラウド リソースの消費量に基づくサービス (IaaS) クラウド製品 (Azure) 料としてマイクロソフトのプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="c1647-p101">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption. Microsoft's Software as a Service (SaaS)-based cloud offerings (Office 365, Intune/EMS, and Dynamics 365) charge per-user license fees. Microsoft's Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
  
<span data-ttu-id="c1647-p102">試用版サブスクリプションを使用することもできます。ただし、このサブスクリプションは、特定の期間を過ぎるか、特定の消費料金を超えると失効します。試用版サブスクリプションは、有料サブスクリプションに変更できます。</span><span class="sxs-lookup"><span data-stu-id="c1647-p102">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="c1647-p103">組織は、マイクロソフトのクラウド ソリューションの複数のサブスクリプションを持つことができます。例を図 1 に示します。</span><span class="sxs-lookup"><span data-stu-id="c1647-p103">Organizations can have multiple subscriptions for Microsoft's cloud offerings. Figure 1 shows an example.</span></span>
  
<span data-ttu-id="c1647-126">**組織の複数のサブスクリプションの使用例を図 1:**</span><span class="sxs-lookup"><span data-stu-id="c1647-126">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![Microsoft のクラウド プランの複数のサブスクリプションのある組織の例。](images/Subscriptions/Subscriptions_Fig1.png)

  
<span data-ttu-id="c1647-128">図 1 は、複数の Office 365 サブスクリプション、1 つの Intune サブスクリプション、1 つの Dynamics 365 サブスクリプション、複数の Azure サブスクリプションを持つ単一の組織を示しています。</span><span class="sxs-lookup"><span data-stu-id="c1647-128">Figure 1 shows a single organization that has multiple Office 365 subscriptions, an Intune subscription, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>
  
### <a name="licenses"></a><span data-ttu-id="c1647-129">ライセンス</span><span class="sxs-lookup"><span data-stu-id="c1647-129">Licenses</span></span>

<span data-ttu-id="c1647-p104">マイクロソフトの SaaS クラウド製品のライセンスにより、クラウドのサービスを使用する特定のユーザー アカウントを提供します。サブスクリプションの一部として、固定の月額料金が課金されます。管理者は、サブスクリプション内の個々 のユーザー アカウントにライセンスを割り当てます。図 2 の使用例は、Contoso 社のエンタープライズ E5 の機能とサービスを使用する最大 100 個の個別のユーザー アカウントに許可する、Office 365 エンタープライズ E5 サブスクリプション ライセンスでは 100、</span><span class="sxs-lookup"><span data-stu-id="c1647-p104">For Microsoft's SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering. You are charged a fixed monthly fee as part of your subscription. Administrators assign licenses to individual user accounts in the subscription. For the example in Figure 2, the Contoso Corporation has an Office 365 Enterprise E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Enterprise E5 features and services.</span></span>
  
<span data-ttu-id="c1647-134">**SaaS ベースのサブスクリプションを組織内の図 2: ライセンス**</span><span class="sxs-lookup"><span data-stu-id="c1647-134">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Microsoft の SaaS ベース クラウド プランのサブスクリプション内の複数ライセンスの例。](images/Subscriptions/Subscriptions_Fig2.png)
  
<span data-ttu-id="c1647-136">Azure PaaS ベースのクラウド サービスの場合、サービス料金にソフトウェア ライセンスが組み込まれています。  </span><span class="sxs-lookup"><span data-stu-id="c1647-136">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="c1647-p105">Azure IaaS ベースの仮想マシン場合、仮想マシン イメージにインストールしたソフトウェアまたはアプリケーションを使用するために、追加ライセンスが必要になることがあります。一部の仮想マシン イメージにはライセンス付きバージョンのソフトウェアがインストールされていて、サーバーに対する分単位の料金が費用に含まれます。その例として、SQL Server 2014 および SQL Server 2016 の仮想マシン イメージが挙げられます。 </span><span class="sxs-lookup"><span data-stu-id="c1647-p105">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="c1647-p106">一部の仮想マシン イメージには、アプリケーションの試用版がインストールされていて、試用期間の経過後も使用する場合は追加のソフトウェア アプリケーション ライセンスが必要になります。たとえば、SharePoint Server 2016 試用版仮想マシン イメージには、プレインストールされた試用版の SharePoint Server 2016 が含まれています。試用期間後に SharePoint Server 2016 の使用を続けるには、SharePoint Server 2016 のライセンスとクライアントのライセンスを Microsoft から購入する必要があります。こうした課金は Azure サブスクリプションとは別であり、仮想マシンを実行する分単位の料金がそのまま適用されます。</span><span class="sxs-lookup"><span data-stu-id="c1647-p106">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trail expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="c1647-144">ユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="c1647-144">User accounts</span></span>

<span data-ttu-id="c1647-p107">マイクロソフトのクラウド ソリューションのすべてのユーザー アカウントは、ユーザー アカウントとグループが含まれている Azure Active Directory (AD) テナントに格納されます。Azure の AD 接続では、Windows サーバー ベースのサービスを使用して既存の Windows サーバーを AD アカウントには、Azure AD テナントを同期できます。これは、ディレクトリ同期 (DirSync) と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c1647-p107">User accounts for all of Microsoft's cloud offerings are stored in an Azure Active Directory (AD) tenant, which contains user accounts and groups. An Azure AD tenant can be synchronized with your existing Windows Server AD accounts using Azure AD Connect, a Windows server-based service. This is known as directory synchronization (DirSync).</span></span>
  
<span data-ttu-id="c1647-148">図 3 は、共通の Azure AD テナントを使用する組織の複数サブスクリプションの例を示しています。このテナントに組織のアカウントが格納されています。</span><span class="sxs-lookup"><span data-stu-id="c1647-148">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="c1647-149">**図 3: 複数の組織を使用するサブスクリプション同じ Azure AD テナント**</span><span class="sxs-lookup"><span data-stu-id="c1647-149">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![すべてのサブスクリプションが同じ Azure AD テナントを使用する、複数のサブスクリプションのある組織の例。](images/Subscriptions/Subscriptions_Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="c1647-151">テナント</span><span class="sxs-lookup"><span data-stu-id="c1647-151">Tenants</span></span>

<span data-ttu-id="c1647-p108">SaaS クラウド商品の場合、テナントとはクラウド サービスを提供しているサーバーが収容された地域の場所のことです。たとえば、Contoso Corporation は、パリ本社の 15,000 人の従業員用の Office 365、EMS、および Dynamics 365 テナントのホストに欧州地域を選択しています。</span><span class="sxs-lookup"><span data-stu-id="c1647-p108">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="c1647-p109">Azure PaaS サービスと、Azure IaaS でホストされる仮想マシン ベースのワークロードは、世界中の Azure データセンターのテナントを持つことができます。場所と呼ばれる Azure データセンターは、Azure PaaS のアプリやサービスまたは IaaS ワークロードの要素を作成するときに、ユーザーが指定します。</span><span class="sxs-lookup"><span data-stu-id="c1647-p109">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="c1647-p110">Azure AD テナントは、アカウントおよびグループを収容する Azure AD の特定のインスタンスです。Office 365、Dynamics 365、または Intune/EMS の有料または試用版サブスクリプションには、無料の Azure AD テナントが含まれています。この Azure AD テナントには、その他の Azure サービスは含まれていません。これは、Azure の試用版または有料のサブスクリプションと同じものではありません。</span><span class="sxs-lookup"><span data-stu-id="c1647-p110">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups. Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant. This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="c1647-159">階層の概要</span><span class="sxs-lookup"><span data-stu-id="c1647-159">Summary of the hierarchy</span></span>

<span data-ttu-id="c1647-160">ここに、簡単なまとめを示します。</span><span class="sxs-lookup"><span data-stu-id="c1647-160">Here is a quick recap:</span></span>
  
- <span data-ttu-id="c1647-161">1 つの組織には複数のサブスクリプションを含めることができる</span><span class="sxs-lookup"><span data-stu-id="c1647-161">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="c1647-162">1 つのサブスクリプションには複数のライセンスを含めることができる</span><span class="sxs-lookup"><span data-stu-id="c1647-162">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="c1647-163">ライセンスは個別のユーザー アカウントに割り当てできる</span><span class="sxs-lookup"><span data-stu-id="c1647-163">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="c1647-164">ユーザー アカウントは Azure AD テナントに保存できる</span><span class="sxs-lookup"><span data-stu-id="c1647-164">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="c1647-165">組織、サブスクリプション、ライセンス、ユーザー アカウントの関係の例を示します。</span><span class="sxs-lookup"><span data-stu-id="c1647-165">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="c1647-166">パブリック ドメイン名によって識別される組織。</span><span class="sxs-lookup"><span data-stu-id="c1647-166">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="c1647-167">ユーザー ライセンスがある Office 365 Enterprise E3 サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="c1647-167">An Office 365 Enterprise E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="c1647-168">ユーザー ライセンスがある Office 365 Enterprise E5 サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="c1647-168">An Office 365 Enterprise E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="c1647-169">ユーザー ライセンスがある EMS サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="c1647-169">An EMS subscription with user licenses.</span></span>
    
    <span data-ttu-id="c1647-170">ユーザー ライセンスがある Dynamics 365 サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="c1647-170">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="c1647-171">複数の Azure サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="c1647-171">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="c1647-172">共通の Azure AD テナントにある組織のユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="c1647-172">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="c1647-p111">複数の Microsoft クラウド製品のサブスクリプションは、同じ Azure AD テナントを使用できます。このテナントは、共通 ID プロバイダーとして機能します。オンプレミスの Windows Server AD の同期されたアカウントを収容する中央 Azure AD テナントを使用すると、クラウドをベースとしたサービスとしての ID (IDaaS) が組織に提供されます。これを図 4 に示します。</span><span class="sxs-lookup"><span data-stu-id="c1647-p111">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider. A central Azure AD tenant that contains the synchronized accounts of your on-premises Windows Server AD provides cloud-based Identity as a Service (IDaaS) for your organization. This is shown in Figure 4.</span></span>
  
<span data-ttu-id="c1647-176">**図 4: アカウントの同期の設置型と組織の IDaaS**</span><span class="sxs-lookup"><span data-stu-id="c1647-176">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![組織のサービスとしての ID (IaaS) IDaaS。](images/Subscriptions/Subscriptions_Fig4.png)
  
<span data-ttu-id="c1647-p112">図 4 は、Microsoft の SaaS クラウド製品、Azure PaaS アプリ、Azure AD ドメイン サービスを使用する Azure IaaS の仮想マシンにより、共通の Azure AD テナントがどのように使用されるかを示します。Azure AD Connect は、オンプレミスの Windows Server AD フォレストを Azure AD テナントと同期します。</span><span class="sxs-lookup"><span data-stu-id="c1647-p112">Figure 4 shows how a common Azure AD tenant is utilized by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises Windows Server AD forest with the Azure AD tenant.</span></span>
  
<span data-ttu-id="c1647-180">マイクロソフトのクラウド サービスの間でアイデンティティの統合の詳細については、[エンタープライズ設計者向けのマイクロソフトのクラウド Id](https://aka.ms/cloudarchidentity)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1647-180">For more information about identity integration across Microsoft's cloud offerings, see [Microsoft Cloud Identity for Enterprise Architects](https://aka.ms/cloudarchidentity).</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="c1647-181">複数の Microsoft クラウド商品のサブスクリプションの組み合わせ</span><span class="sxs-lookup"><span data-stu-id="c1647-181">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="c1647-182">次の表では、既に所有している 1 つの種類のクラウド商品のサブスクリプション (最初の列に列挙したラベル) と、追加する別の種類のクラウド商品のサブスクリプション (列間を横切る) に基づいた、複数の Microsoft クラウド商品の可能な組み合わせ方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="c1647-182">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="c1647-183">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="c1647-183">**Office 365**</span></span>|<span data-ttu-id="c1647-184">**Azure**</span><span class="sxs-lookup"><span data-stu-id="c1647-184">**Azure**</span></span>|<span data-ttu-id="c1647-185">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="c1647-185">**Intune/EMS**</span></span>|<span data-ttu-id="c1647-186">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="c1647-186">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="c1647-187">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="c1647-187">**Office 365**</span></span> <br/> |<span data-ttu-id="c1647-188">該当なし</span><span class="sxs-lookup"><span data-stu-id="c1647-188">NA</span></span>  <br/> |<span data-ttu-id="c1647-189">Azure ポータルから Azure のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="c1647-189">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="c1647-190">Office 365 ポータルから Intune/EMS のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="c1647-190">You add an Intune/EMS subscription to your organization from the Office 365 portal.</span></span>  <br/> |<span data-ttu-id="c1647-191">Office 365 ポータルから Dynamics 365 のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="c1647-191">You add a Dynamics 365 subscription to your organization from the Office 365 portal.</span></span>  <br/> |
|<span data-ttu-id="c1647-192">**Azure**</span><span class="sxs-lookup"><span data-stu-id="c1647-192">**Azure**</span></span> <br/> |<span data-ttu-id="c1647-193">Office 365 のサブスクリプションを組織に追加します。 </span><span class="sxs-lookup"><span data-stu-id="c1647-193">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="c1647-194">該当なし</span><span class="sxs-lookup"><span data-stu-id="c1647-194">NA</span></span>  <br/> |<span data-ttu-id="c1647-195">Intune/EMS サブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="c1647-195">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="c1647-196">Dynamics 365 サブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="c1647-196">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="c1647-197">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="c1647-197">**Intune/EMS**</span></span> <br/> |<span data-ttu-id="c1647-198">Office 365 のサブスクリプションを組織に追加します。 </span><span class="sxs-lookup"><span data-stu-id="c1647-198">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="c1647-199">Azure ポータルから Azure のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="c1647-199">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="c1647-200">該当なし</span><span class="sxs-lookup"><span data-stu-id="c1647-200">NA</span></span>  <br/> |<span data-ttu-id="c1647-201">Dynamics 365 サブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="c1647-201">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="c1647-202">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="c1647-202">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="c1647-203">Office 365 のサブスクリプションを組織に追加します。 </span><span class="sxs-lookup"><span data-stu-id="c1647-203">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="c1647-204">Azure ポータルから Azure のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="c1647-204">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="c1647-205">Intune/EMS サブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="c1647-205">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="c1647-206">該当なし</span><span class="sxs-lookup"><span data-stu-id="c1647-206">NA</span></span>  <br/> |
   
<span data-ttu-id="c1647-207">Microsoft SaaS ベース サービスの場合は、Office 365 管理センターを使用すると、組織にサブスクリプションを簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="c1647-207">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the Office 365 Admin center:</span></span>
  
1. <span data-ttu-id="c1647-208">グローバル管理者アカウントを Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) にサインインし、し、[**管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1647-208">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with your global administrator account, and then click **Admin**.</span></span>
    
2. <span data-ttu-id="c1647-209">**管理センター**ホーム ページの左側のナビゲーションから、**請求**、および、**購買サービス**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1647-209">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="c1647-210">[**サービスの購入**] ページで、新しいサブスクリプションを購入します。</span><span class="sxs-lookup"><span data-stu-id="c1647-210">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="c1647-211">Office 365 管理センターは、Office 365 サブスクリプションの組織と Azure AD テナントを SaaS ベースのクラウド製品の新しいサブスクリプションに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c1647-211">The Office 365 Admin center assigns the organization and Azure AD tenant of your Office 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="c1647-212">Office 365 サブスクリプションと同じ組織および Azure AD テナントに Azure サブスクリプションを追加するには</span><span class="sxs-lookup"><span data-stu-id="c1647-212">To add an Azure subscription with the same organization and Azure AD tenant as your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="c1647-213">Azure ポータル ([https://portal.azure.com](https://portal.azure.com))、Office 365 のグローバル管理者アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="c1647-213">Sign in to the Azure portal ([https://portal.azure.com](https://portal.azure.com)) with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="c1647-214">左側のナビゲーションでは、**サブスクリプション**をクリックし、し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1647-214">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="c1647-215">[**サブスクリプションの追加**] ページで、サービスを選択し、支払情報と契約を完了します。</span><span class="sxs-lookup"><span data-stu-id="c1647-215">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="c1647-216">Azure と Office 365 のサブスクリプションを個別に購入して、Azure サブスクリプションから Office 365 の Azure AD テナントにアクセスする場合は、 [Azure サブスクリプションの Office 365 テナントに関連付ける](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription)手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1647-216">If you purchased Azure and Office 365 subscriptions separately and want to access the Office 365 Azure AD tenant from your Azure subscription, see the instructions in [Associate an Office 365 tenant with an Azure subscription](https://channel9.msdn.com/Series/Microsoft-Azure-Tutorials/Associate-an-Office-365-tenant-with-an-Azure-subscription).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c1647-217">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1647-217">See Also</span></span>

[<span data-ttu-id="c1647-218">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="c1647-218">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="c1647-219">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="c1647-219">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="c1647-220">SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル</span><span class="sxs-lookup"><span data-stu-id="c1647-220">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="c1647-221">ハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="c1647-221">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="c1647-222">Contoso Corporation のサブスクリプション、ライセンス、およびユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="c1647-222">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>](subscriptions-licenses-and-user-accounts-for-the-contoso-corporation.md)



