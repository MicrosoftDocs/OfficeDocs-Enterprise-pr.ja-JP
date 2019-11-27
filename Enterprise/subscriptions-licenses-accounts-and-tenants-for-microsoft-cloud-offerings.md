---
title: マイクロソフトのクラウド プランのサブスクリプション、ライセンス、アカウント、およびテナント
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/08/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
description: '概要: Microsoft のクラウド プラン全体に渡る組織、サブスクリプション、ライセンス、ユーザー アカウント、およびテナントの関係について理解します。'
ms.openlocfilehash: 3e10ed7752fc4763aef77c7cb683532cf0d5c2ce
ms.sourcegitcommit: fbd2f3fb297c508212baed3ee9d1ce51765cc8bb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2019
ms.locfileid: "39254586"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="ae1ad-103">マイクロソフトのクラウド プランのサブスクリプション、ライセンス、アカウント、およびテナント</span><span class="sxs-lookup"><span data-stu-id="ae1ad-103">Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings</span></span>

 <span data-ttu-id="ae1ad-104">**概要:** Microsoft のクラウド プラン全体に渡る組織、サブスクリプション、ライセンス、ユーザー アカウント、およびテナントの関係について理解します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-104">**Summary:** Understand the relationships of organizations, subscriptions, licenses, user accounts, and tenants across Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="ae1ad-105">Microsoft は、クラウド プラン全体で ID の使用と課金の一貫性を維持するために、組織、サブスクリプション、ライセンス、ユーザー アカウントなどの階層を提供しています。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-105">Microsoft provides a hierarchy of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="ae1ad-106">Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="ae1ad-106">Microsoft Office 365</span></span>
- <span data-ttu-id="ae1ad-107">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="ae1ad-107">Microsoft Azure</span></span>
- <span data-ttu-id="ae1ad-108">Microsoft Intune および Enterprise Mobility + Security (EMS)</span><span class="sxs-lookup"><span data-stu-id="ae1ad-108">Microsoft Intune and the Enterprise Mobility + Security (EMS)</span></span>
- <span data-ttu-id="ae1ad-109">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="ae1ad-109">Microsoft Dynamics 365</span></span>

<span data-ttu-id="ae1ad-110">[Microsoft 365](https://docs.microsoft.com/microsoft-365/) Office 365、EMS、および Windows 10 Enterprise が 1 つのサブスクリプションと統合型サービスセットに結合されます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-110">[Microsoft 365](https://docs.microsoft.com/microsoft-365/) combines Office 365, EMS, and Windows 10 Enterprise into a single subscription and set of integrated services.</span></span>

## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="ae1ad-111">階層の要素</span><span class="sxs-lookup"><span data-stu-id="ae1ad-111">Elements of the hierarchy</span></span>

<span data-ttu-id="ae1ad-112">階層の要素を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-112">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="ae1ad-113">組織</span><span class="sxs-lookup"><span data-stu-id="ae1ad-113">Organization</span></span>

<span data-ttu-id="ae1ad-p101">組織は、Microsoft クラウド製品を使用しているビジネス エンティティを表します。通常は、1 つ以上のパブリック ドメイン ネーム システム (DNS) のドメイン名 (例: contoso.com) で識別されます。組織は、サブスクリプションのコンテナーになります。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-p101">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="ae1ad-116">サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="ae1ad-116">Subscriptions</span></span>

<span data-ttu-id="ae1ad-117">サブスクリプションとは、1 つ以上の Microsoft クラウドのプラットフォームやサービスを使用するための Microsoft との契約のことです。この契約では、ユーザー単位のライセンス料またはクラウドベースのリソース消費量に基づいて請求されます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-117">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption.</span></span> 

- <span data-ttu-id="ae1ad-118">Microsoft のサービスとしてのソフトウェア (SaaS) ベースのクラウド商品 (Office 365、Intune/EMS、および Dynamics 365) では、ユーザーごとのライセンス料金が請求されます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-118">Microsoft's Software as a Service (SaaS)-based cloud offerings (Office 365, Intune/EMS, and Dynamics 365) charge per-user license fees.</span></span> 
- <span data-ttu-id="ae1ad-119">Microsoft のサービスとしてのプラットフォーム (PaaS) およびサービスとしてのインフラストラクチャ (IaaS) のクラウド サービス (Azure) では、クラウド リソースの消費量に基づいて請求されます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-119">Microsoft's Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
 
<span data-ttu-id="ae1ad-p102">試用版サブスクリプションを使用することもできます。ただし、このサブスクリプションは、特定の期間を過ぎるか、特定の消費料金を超えると失効します。試用版サブスクリプションは、有料サブスクリプションに変更できます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-p102">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="ae1ad-122">組織は、Microsoft のクラウド商品の複数のサブスクリプションを所有できます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-122">Organizations can have multiple subscriptions for Microsoft's cloud offerings.</span></span> <span data-ttu-id="ae1ad-123">図 1 は、複数の Office 365 サブスクリプション、1 つの Intune サブスクリプション、1 つの Dynamics 365 サブスクリプション、複数の Azure サブスクリプションを持つ 1 つの組織を示しています。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-123">Figure 1 shows a single organization that has multiple Office 365 subscriptions, an Intune subscription, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>

<span data-ttu-id="ae1ad-124">**図 1: 1 つの組織に複数のサブスクリプションの例**</span><span class="sxs-lookup"><span data-stu-id="ae1ad-124">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![Microsoft のクラウド プランの複数のサブスクリプションのある組織の例。](media/Subscriptions/Subscriptions-Fig1.png)

  
### <a name="licenses"></a><span data-ttu-id="ae1ad-126">ライセンス</span><span class="sxs-lookup"><span data-stu-id="ae1ad-126">Licenses</span></span>

<span data-ttu-id="ae1ad-127">Microsoft の SaaS クラウド商品の場合、1 つのライセンスで、1 つの特定のユーザー アカウントがクラウド商品のサービスを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-127">For Microsoft's SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering.</span></span> <span data-ttu-id="ae1ad-128">サブスクリプションの一環として、月間の固定料金が課金されます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-128">You are charged a fixed monthly fee as part of your subscription.</span></span> <span data-ttu-id="ae1ad-129">管理者は、サブスクリプション内で個別のユーザー アカウントにライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-129">Administrators assign licenses to individual user accounts in the subscription.</span></span> <span data-ttu-id="ae1ad-130">図 2 の例では、Contoso Corporation は 100 ライセンスの Office 365 Enterprise E5 サブスクリプションを所有しています。このサブスクリプションにより、最大 100 件の個別のユーザー アカウントが Office 365 Enterprise E5 の機能とサービスを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-130">For the example in Figure 2, the Contoso Corporation has an Office 365 Enterprise E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Office 365 Enterprise E5 features and services.</span></span>
  
<span data-ttu-id="ae1ad-131">**図 2:1 つの組織の SaaS ベースのサブスクリプションに含まれるライセンス**</span><span class="sxs-lookup"><span data-stu-id="ae1ad-131">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Microsoft の SaaS ベース クラウド プランのサブスクリプション内の複数ライセンスの例。](media/Subscriptions/Subscriptions-Fig2.png)
  
<span data-ttu-id="ae1ad-133">Azure PaaS ベースのクラウド サービスの場合、サービス料金にソフトウェア ライセンスが組み込まれています。  </span><span class="sxs-lookup"><span data-stu-id="ae1ad-133">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="ae1ad-p105">Azure IaaS ベースの仮想マシン場合、仮想マシン イメージにインストールしたソフトウェアまたはアプリケーションを使用するために、追加ライセンスが必要になることがあります。一部の仮想マシン イメージにはライセンス付きバージョンのソフトウェアがインストールされていて、サーバーに対する分単位の料金が費用に含まれます。その例として、SQL Server 2014 および SQL Server 2016 の仮想マシン イメージが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-p105">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="ae1ad-p106">一部の仮想マシン イメージには、アプリケーションの試用版がインストールされていて、試用期間の経過後も使用する場合は追加のソフトウェア アプリケーション ライセンスが必要になります。たとえば、SharePoint Server 2016 試用版仮想マシン イメージには、プレインストールされた試用版の SharePoint Server 2016 が含まれています。試用期間後に SharePoint Server 2016 の使用を続けるには、SharePoint Server 2016 のライセンスとクライアントのライセンスを Microsoft から購入する必要があります。こうした課金は Azure サブスクリプションとは別であり、仮想マシンを実行する分単位の料金がそのまま適用されます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-p106">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="ae1ad-141">ユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="ae1ad-141">User accounts</span></span>

<span data-ttu-id="ae1ad-142">すべての Microsoft のクラウド商品のユーザー アカウントは、Azure Active Directory (Azure AD) テナントに保存されます。これには、ユーザー アカウントとグループが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-142">User accounts for all of Microsoft's cloud offerings are stored in an Azure Active Directory (Azure AD) tenant, which contains user accounts and groups.</span></span> <span data-ttu-id="ae1ad-143">Azure AD テナントは、Windows サーバーベースのサービスである Azure AD Connect を使用して、既存の Active Directory Domain Services (AD DS) アカウントと同期できます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-143">An Azure AD tenant can be synchronized with your existing Active Directory Domain Services (AD DS) accounts using Azure AD Connect, a Windows server-based service.</span></span> <span data-ttu-id="ae1ad-144">これはディレクトリ同期と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-144">This is known as directory synchronization (DirSync).</span></span>
  
<span data-ttu-id="ae1ad-145">図 3 は、共通の Azure AD テナントを使用する組織の複数サブスクリプションの例を示しています。このテナントに組織のアカウントが格納されています。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-145">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="ae1ad-146">**図 3:同じ Azure AD テナントを使用する組織の複数のサブスクリプション**</span><span class="sxs-lookup"><span data-stu-id="ae1ad-146">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![すべてのサブスクリプションが同じ Azure AD テナントを使用する、複数のサブスクリプションのある組織の例。](media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="ae1ad-148">テナント</span><span class="sxs-lookup"><span data-stu-id="ae1ad-148">Tenants</span></span>

<span data-ttu-id="ae1ad-p108">SaaS クラウド商品の場合、テナントとはクラウド サービスを提供しているサーバーが収容された地域の場所のことです。たとえば、Contoso Corporation は、パリ本社の 15,000 人の従業員用の Office 365、EMS、および Dynamics 365 テナントのホストに欧州地域を選択しています。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-p108">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. For example, the Contoso Corporation chose the European region to host its Office 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="ae1ad-p109">Azure PaaS サービスと、Azure IaaS でホストされる仮想マシン ベースのワークロードは、世界中の Azure データセンターのテナントを持つことができます。場所と呼ばれる Azure データセンターは、Azure PaaS のアプリやサービスまたは IaaS ワークロードの要素を作成するときに、ユーザーが指定します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-p109">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="ae1ad-p110">Azure AD テナントは、アカウントおよびグループを収容する Azure AD の特定のインスタンスです。Office 365、Dynamics 365、または Intune/EMS の有料または試用版サブスクリプションには、無料の Azure AD テナントが含まれています。この Azure AD テナントには、その他の Azure サービスは含まれていません。これは、Azure の試用版または有料のサブスクリプションと同じものではありません。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-p110">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups. Paid or trial subscriptions of Office 365, Dynamics 365, or Intune/EMS include a free Azure AD tenant. This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="ae1ad-156">階層の概要</span><span class="sxs-lookup"><span data-stu-id="ae1ad-156">Summary of the hierarchy</span></span>

<span data-ttu-id="ae1ad-157">ここに、簡単なまとめを示します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-157">Here is a quick recap:</span></span>
  
- <span data-ttu-id="ae1ad-158">1 つの組織には複数のサブスクリプションを含めることができる</span><span class="sxs-lookup"><span data-stu-id="ae1ad-158">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="ae1ad-159">1 つのサブスクリプションには複数のライセンスを含めることができる</span><span class="sxs-lookup"><span data-stu-id="ae1ad-159">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="ae1ad-160">ライセンスは個別のユーザー アカウントに割り当てできる</span><span class="sxs-lookup"><span data-stu-id="ae1ad-160">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="ae1ad-161">ユーザー アカウントは Azure AD テナントに保存できる</span><span class="sxs-lookup"><span data-stu-id="ae1ad-161">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="ae1ad-162">組織、サブスクリプション、ライセンス、ユーザー アカウントの関係の例を示します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-162">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="ae1ad-163">パブリック ドメイン名によって識別される組織。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-163">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="ae1ad-164">ユーザー ライセンスがある Office 365 Enterprise E3 サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-164">An Office 365 Enterprise E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="ae1ad-165">ユーザー ライセンスがある Office 365 Enterprise E5 サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-165">An Office 365 Enterprise E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="ae1ad-166">ユーザー ライセンスがある EMS サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-166">An EMS subscription with user licenses.</span></span>
    
    <span data-ttu-id="ae1ad-167">ユーザー ライセンスがある Dynamics 365 サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-167">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="ae1ad-168">複数の Azure サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-168">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="ae1ad-169">共通の Azure AD テナントにある組織のユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-169">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="ae1ad-170">複数の Microsoft クラウド商品のサブスクリプションは、同じ Azure AD テナントを使用できます。このテナントは、共通の ID プロバイダーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-170">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider.</span></span> <span data-ttu-id="ae1ad-171">オンプレミスの AD DS の同期されたユーザー アカウントを収容しているセントラル Azure AD テナントを使用することで、組織にサービス (IDaaS) としてのクラウドベース ID が提供されます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-171">A central Azure AD tenant that contains the synchronized accounts of your on-premises AD DS provides cloud-based Identity as a Service (IDaaS) for your organization.</span></span> 
  
<span data-ttu-id="ae1ad-172">**図 4: 同期されたオンプレミスのアカウントと組織の IDaaS**</span><span class="sxs-lookup"><span data-stu-id="ae1ad-172">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![組織のサービスとしての ID (IaaS) IDaaS。](media/Subscriptions/Subscriptions-Fig4.png)
  
<span data-ttu-id="ae1ad-p112">図 4 は、Microsoft の SaaS クラウド プラン、Azure PaaS アプリ、Azure AD Domain Services を使用する Azure IaaS の仮想マシンにより、共通の Azure AD テナントがどのように使用されるかを示します。Azure AD Connect は、オンプレミスの AD DS フォレストを Azure AD テナントと同期します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-p112">Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="ae1ad-176">複数の Microsoft クラウド プランのサブスクリプションの組み合わせ</span><span class="sxs-lookup"><span data-stu-id="ae1ad-176">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="ae1ad-177">次の表では、既に所有している 1 つの種類のクラウド商品のサブスクリプション (最初の列に列挙したラベル) と、追加する別の種類のクラウド商品のサブスクリプション (列間を横切る) に基づいた、複数の Microsoft クラウド商品の可能な組み合わせ方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-177">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="ae1ad-178">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="ae1ad-178">**Office 365**</span></span>|<span data-ttu-id="ae1ad-179">**Azure**</span><span class="sxs-lookup"><span data-stu-id="ae1ad-179">**Azure**</span></span>|<span data-ttu-id="ae1ad-180">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="ae1ad-180">**Intune/EMS**</span></span>|<span data-ttu-id="ae1ad-181">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="ae1ad-181">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="ae1ad-182">**Office 365**</span><span class="sxs-lookup"><span data-stu-id="ae1ad-182">**Office 365**</span></span> <br/> |<span data-ttu-id="ae1ad-183">該当なし</span><span class="sxs-lookup"><span data-stu-id="ae1ad-183">NA</span></span>  <br/> |<span data-ttu-id="ae1ad-184">Azure ポータルから Azure のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-184">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="ae1ad-185">Microsoft 365 管理センターから Intune/EMS のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-185">You add an Intune/EMS subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |<span data-ttu-id="ae1ad-186">Microsoft 365 管理センターから Dynamics 365 のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-186">You add a Dynamics 365 subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |
|<span data-ttu-id="ae1ad-187">**Azure**</span><span class="sxs-lookup"><span data-stu-id="ae1ad-187">**Azure**</span></span> <br/> |<span data-ttu-id="ae1ad-188">Office 365 のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-188">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="ae1ad-189">該当なし</span><span class="sxs-lookup"><span data-stu-id="ae1ad-189">NA</span></span>  <br/> |<span data-ttu-id="ae1ad-190">Intune/EMS サブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-190">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="ae1ad-191">Dynamics 365 サブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-191">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="ae1ad-192">**Intune/EMS**</span><span class="sxs-lookup"><span data-stu-id="ae1ad-192">**Intune/EMS**</span></span> <br/> |<span data-ttu-id="ae1ad-193">Office 365 のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-193">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="ae1ad-194">Azure ポータルから Azure のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-194">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="ae1ad-195">該当なし</span><span class="sxs-lookup"><span data-stu-id="ae1ad-195">NA</span></span>  <br/> |<span data-ttu-id="ae1ad-196">Dynamics 365 サブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-196">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="ae1ad-197">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="ae1ad-197">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="ae1ad-198">Office 365 のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-198">You add an Office 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="ae1ad-199">Azure ポータルから Azure のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-199">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="ae1ad-200">Intune/EMS サブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-200">You add an Intune/EMS subscription to your organization.</span></span>  <br/> |<span data-ttu-id="ae1ad-201">該当なし</span><span class="sxs-lookup"><span data-stu-id="ae1ad-201">NA</span></span>  <br/> |
   
<span data-ttu-id="ae1ad-202">Microsoft SaaS ベース サービスの場合は、管理センターを使用すると、組織にサブスクリプションを簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-202">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the admin center:</span></span>
  
1. <span data-ttu-id="ae1ad-203">全体管理者アカウントを使用して、Microsoft 365 管理センター ([https://admin.microsoft.com](https://admin.microsoft.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-203">Sign in to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) with your global administrator account.</span></span>
    
2. <span data-ttu-id="ae1ad-204">**管理センター**のホームページ左側にあるナビゲーションで、**[課金]**、**[サービスを購入する]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-204">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="ae1ad-205">**[サービスを購入する]** ページで、新しいサブスクリプションを購入します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-205">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="ae1ad-206">管理センターは、Office 365 サブスクリプションの組織と Azure AD テナントを SaaS ベースのクラウド製品の新しいサブスクリプションに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-206">The admin center assigns the organization and Azure AD tenant of your Office 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="ae1ad-207">Office 365 サブスクリプションと同じ組織および Azure AD テナントに Azure サブスクリプションを追加するには</span><span class="sxs-lookup"><span data-stu-id="ae1ad-207">To add an Azure subscription with the same organization and Azure AD tenant as your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="ae1ad-208">Office 365 全体管理者アカウントを使用して、Azure portal ([https://portal.azure.com](https://portal.azure.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-208">Sign in to the Azure portal ([https://portal.azure.com](https://portal.azure.com)) with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="ae1ad-209">左側のナビゲーションで、**[サブスクリプション]**、**[追加]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-209">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="ae1ad-210">**[サブスクリプションの追加]** ページでプランを選択し、支払情報を記入して契約します。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-210">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="ae1ad-211">Azure と Office 365 のサブスクリプションを個別に購入済みで、Azure サブスクリプションから Office 365 の Azure AD テナントへのアクセスを希望する場合は、「[既存の Azure サブスクリプションを Azure Active Directory テナントに追加する](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory)」の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae1ad-211">If you purchased Azure and Office 365 subscriptions separately and want to access the Office 365 Azure AD tenant from your Azure subscription, see the instructions in [Add an existing Azure subscription to your Azure Active Directory tenant](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).</span></span>
 
## <a name="see-also"></a><span data-ttu-id="ae1ad-212">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae1ad-212">See also</span></span>

[<span data-ttu-id="ae1ad-213">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="ae1ad-213">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="ae1ad-214">SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル</span><span class="sxs-lookup"><span data-stu-id="ae1ad-214">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="ae1ad-215">ハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="ae1ad-215">Hybrid solutions</span></span>](hybrid-solutions.md)

## <a name="next-step"></a><span data-ttu-id="ae1ad-216">次の手順</span><span class="sxs-lookup"><span data-stu-id="ae1ad-216">Next step</span></span>

[<span data-ttu-id="ae1ad-217">Office 365 のネットワーク接続の評価</span><span class="sxs-lookup"><span data-stu-id="ae1ad-217">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)
  
