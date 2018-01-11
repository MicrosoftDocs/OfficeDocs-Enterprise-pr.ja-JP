---
title: "Contoso Corporation のサブスクリプション、ライセンス、およびユーザー アカウント"
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
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: "概要: は、contoso 社のクラウドのサブスクリプション、ライセンス、ユーザー アカウント、およびテナントの構造を理解します。"
ms.openlocfilehash: 0fdd72a697edb312be13c9794e543a81bf9a8e54
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a><span data-ttu-id="4f32c-103">Contoso Corporation のサブスクリプション、ライセンス、およびユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="4f32c-103">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>

 <span data-ttu-id="4f32c-104">**の概要:**Contoso 社のクラウドのサブスクリプション、ライセンス、ユーザー アカウント、およびテナントの構造を理解します。</span><span class="sxs-lookup"><span data-stu-id="4f32c-104">**Summary:** Understand the structure of Contoso's cloud subscriptions, licenses, user accounts, and tenants.</span></span>
  
<span data-ttu-id="4f32c-105">すべてのクラウド製品について ID の一貫した使用と課金を実現するために、Microsoft は、組織/サブスクリプション/ライセンス/ユーザー アカウントの階層を提供します。</span><span class="sxs-lookup"><span data-stu-id="4f32c-105">To provide a consistent use of identities and billing for all cloud offerings, Microsoft provides an organization/subscriptions/licenses/user accounts hierarchy:</span></span>
  
- <span data-ttu-id="4f32c-106">組織</span><span class="sxs-lookup"><span data-stu-id="4f32c-106">Organization</span></span>
    
    <span data-ttu-id="4f32c-107">Microsoft クラウド製品を使用しているビジネス エンティティ。通常は、パブリック DNS ドメイン名 (例: contoso.com) で識別されます。</span><span class="sxs-lookup"><span data-stu-id="4f32c-107">The business entity that is using Microsoft cloud offerings, typically identified by a public DNS domain name, such as contoso.com.</span></span>
    
- <span data-ttu-id="4f32c-108">サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="4f32c-108">Subscriptions</span></span>
    
    <span data-ttu-id="4f32c-p101">マイクロソフトの SaaS では、製品 (Office 365、Intune と EMS では、Dynamics 365) をクラウドでのサブスクリプションは、特定の製品およびユーザー ライセンスの購入のセットです。Azure のサブスクリプションにより、組織に消費されたクラウド サービスの通話料金です。</span><span class="sxs-lookup"><span data-stu-id="4f32c-p101">For Microsoft SaaS cloud offerings (Office 365, Intune/EMS, and Dynamics 365), a subscription is a specific product and a purchased set of user licenses. For Azure, a subscription allows for billing of consumed cloud services to the organization.</span></span>
    
- <span data-ttu-id="4f32c-111">ライセンス</span><span class="sxs-lookup"><span data-stu-id="4f32c-111">Licenses</span></span>
    
    <span data-ttu-id="4f32c-p102">マイクロソフト SaaS クラウド製品のライセンスにより、クラウド サービスを使用する特定のユーザー アカウントです。Azure のソフトウェア ・ ライセンスは、追加のソフトウェア ライセンスを購入する必要がありますが、サービスの料金に構築されています。</span><span class="sxs-lookup"><span data-stu-id="4f32c-p102">For Microsoft SaaS cloud offerings, a license allows a specific user account to use cloud services. For Azure, software licenses are built into service pricing, but in some cases you will need to purchase additional software licenses.</span></span>
    
- <span data-ttu-id="4f32c-114">ユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="4f32c-114">User accounts</span></span>
    
    <span data-ttu-id="4f32c-115">ユーザー アカウントは Azure AD テナントに格納され、Windows Server AD などのオンプレミスの ID プロバイダーから同期できます。</span><span class="sxs-lookup"><span data-stu-id="4f32c-115">User accounts are stored in an Azure AD tenant and can be synchronized from an on-premises identity provider such as Windows Server AD.</span></span>
    
## <a name="contosos-structure"></a><span data-ttu-id="4f32c-116">Contoso 社の構造</span><span class="sxs-lookup"><span data-stu-id="4f32c-116">Contoso's structure</span></span>

<span data-ttu-id="4f32c-117">Contoso 社では、組織とそのサブスクリプション、ライセンス、アカウント、テナントに対して、次の構造を決定しました。</span><span class="sxs-lookup"><span data-stu-id="4f32c-117">Contoso determined the following structure for the organization and its subscriptions, licenses, accounts, and tenants:</span></span>
  
<span data-ttu-id="4f32c-118">**図 1: Contoso の組織、サブスクリプション、ライセンス、ユーザー アカウントおよびテナント**</span><span class="sxs-lookup"><span data-stu-id="4f32c-118">**Figure 1: Contoso's organization, subscriptions, licenses, user accounts and tenants**</span></span>

![Contoso 社の組織、サブスクリプション、ライセンス、ユーザー アカウント、テナント](images/Contoso_Poster/Subscriptions.png)
  
<span data-ttu-id="4f32c-120">図 1 は、Contoso 社の組織が、どのように複数のサブスクリプションを含み、contoso.com Windows Server AD フォレストから同期されたユーザー アカウントを含む共通の Azure AD テナントに関連付けられているかを示しています。</span><span class="sxs-lookup"><span data-stu-id="4f32c-120">Figure 1 shows how the Contoso organization includes multiple subscriptions and is tied to a common Azure AD tenant that contains the user accounts synchronized from the contoso.com Windows Server AD forest.</span></span>
  
- <span data-ttu-id="4f32c-121">**組織**コントソ株式会社は、そのパブリック ドメイン名 contoso.com によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="4f32c-121">**Organization** The Contoso Corporation is identified by its public domain name contoso.com.</span></span>
    
  - <span data-ttu-id="4f32c-122">**サブスクリプションとライセンス**コントソ株式会社は、次の使用しています。</span><span class="sxs-lookup"><span data-stu-id="4f32c-122">**Subscriptions and licenses** The Contoso Corporation is using the following:</span></span>
    
  - <span data-ttu-id="4f32c-123">5,000 ライセンスで Office 365 エンタープライズ E3 製品</span><span class="sxs-lookup"><span data-stu-id="4f32c-123">The Office 365 Enterprise E3 product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="4f32c-124">200 個のライセンスがある Office 365 Enterprise E5 製品</span><span class="sxs-lookup"><span data-stu-id="4f32c-124">The Office 365 Enterprise E5 product with 200 licenses</span></span>
    
  - <span data-ttu-id="4f32c-125">EMS 製品 5,000 ライセンス</span><span class="sxs-lookup"><span data-stu-id="4f32c-125">The EMS product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="4f32c-126">100 のライセンスを持つ Dynamics 365 製品</span><span class="sxs-lookup"><span data-stu-id="4f32c-126">The Dynamics 365 product with 100 licenses</span></span>
    
  - <span data-ttu-id="4f32c-127">地域に基づく複数の Azure サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="4f32c-127">Multiple Azure subscriptions based on regions</span></span>
    
  - <span data-ttu-id="4f32c-128">**ユーザー アカウント**一般的な Azure AD テナントには、ユーザー アカウントの一覧が含まれているし、Azure サブスクリプションにより、contoso 社のサブスクリプションでは、開発/テスト以外のすべてのグループを使用します。</span><span class="sxs-lookup"><span data-stu-id="4f32c-128">**User accounts** A common Azure AD tenant contains the list of user accounts and groups used by all of Contoso's subscriptions, with the exception of dev/test Azure subscriptions.</span></span>
    
<span data-ttu-id="4f32c-129">Contoso 社のテナントの場合:</span><span class="sxs-lookup"><span data-stu-id="4f32c-129">For Contoso's tenants:</span></span>
  
- <span data-ttu-id="4f32c-p103">Saas クラウドのテナントは、クラウド サービスを提供するサーバーを収容している地域の場所です。Contoso 社は、その Office 365、EMS、Dynamics 365 のテナントをホストするためのヨーロッパの地域を選択しました。</span><span class="sxs-lookup"><span data-stu-id="4f32c-p103">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. Contoso chose the European region to host its Office 365, EMS, and Dynamics 365 tenants.</span></span> 
    
- <span data-ttu-id="4f32c-p104">Azure PaaS サービスとアプリケーションおよび IaaS IT 作業負荷は、世界中に、Azure データ センター内のテナントを持つことができます。Azure AD、テナントは、Azure AD のアカウントおよびグループを含むの特定のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="4f32c-p104">Azure PaaS services and apps and IaaS IT workloads can have tenancy in any Azure datacenter across the world. An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span>
    
- <span data-ttu-id="4f32c-134">Contoso 社の Windows サーバー AD フォレストの同期されたアカウントを含む一般的な Azure AD テナントには、マイクロソフトのクラウド サービスの間での IDaaS が用意されています。</span><span class="sxs-lookup"><span data-stu-id="4f32c-134">The common Azure AD tenant that contains the synchronized accounts for the Contoso Windows Server AD forest provides IDaaS across Microsoft's cloud offerings.</span></span>
    
<span data-ttu-id="4f32c-135">詳細については、[ライセンス、サブスクリプション、アカウント、およびマイクロソフトのクラウド サービスのテナント](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f32c-135">For more information, see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span></span>
  
## <a name="contosos-azure-subscriptions"></a><span data-ttu-id="4f32c-136">Contoso 社の Azure サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="4f32c-136">Contoso's Azure subscriptions</span></span>

<span data-ttu-id="4f32c-137">図 2 は、contoso 社の Azure サブスクリプションの階層の設計を示しています。</span><span class="sxs-lookup"><span data-stu-id="4f32c-137">Figure 2 shows the hierarchical design of Contoso's Azure subscriptions:</span></span>
  
<span data-ttu-id="4f32c-138">**Azure サブスクリプションの contoso 社の構造を図 2:**</span><span class="sxs-lookup"><span data-stu-id="4f32c-138">**Figure 2: Contoso's structure for Azure subscriptions**</span></span>

![Azure サブスクリプションの Contoso 社の構造](images/Contoso_Poster/Subscriptions_Nested.png)
  
- <span data-ttu-id="4f32c-140">Microsoft とのエンタープライズ契約に基づき、Contoso 社は最上位です。</span><span class="sxs-lookup"><span data-stu-id="4f32c-140">Contoso is at the top, based on its Enterprise Agreement with Microsoft.</span></span>
    
- <span data-ttu-id="4f32c-141">世界中の contoso 社の Windows サーバーの AD フォレストのドメインの Contoso 社のそれぞれの地域に対応するアカウントのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="4f32c-141">There are a set of accounts corresponding to the different regions of the Contoso Corporation around the world, based on the domains of Contoso's Windows Server AD forest.</span></span>
    
- <span data-ttu-id="4f32c-142">各領域内では、地域の開発、テスト、および運用展開のニーズに基づいて 1 つまたは複数のサブスクリプションがあります。</span><span class="sxs-lookup"><span data-stu-id="4f32c-142">Within each region, there are one or more subscriptions based on the region's development, testing, and production deployment needs.</span></span>
    
<span data-ttu-id="4f32c-p105">各 Azure サブスクリプションは、Azure サービスへの認証と承認のために、ユーザー アカウントとグループを含む単一の Azure AD テナントと関連付けることができます。運用サブスクリプションでは、Contoso 社の共通の Azure AD テナントを使用します。</span><span class="sxs-lookup"><span data-stu-id="4f32c-p105">Each Azure subscription can be associated with a single Azure AD tenant that contains user accounts and groups for authentication and authorization to Azure services. Production subscriptions use the common Contoso Azure AD tenant.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4f32c-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f32c-145">See Also</span></span>

[<span data-ttu-id="4f32c-146">Microsoft Cloud の Contoso</span><span class="sxs-lookup"><span data-stu-id="4f32c-146">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="4f32c-147">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="4f32c-147">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="4f32c-148">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span><span class="sxs-lookup"><span data-stu-id="4f32c-148">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




