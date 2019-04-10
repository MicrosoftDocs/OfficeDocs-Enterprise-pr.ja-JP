---
title: Azure PaaS のハイブリッド クラウド シナリオ
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
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: '概要: Microsoft のサービスとしてのプラットフォーム (PaaS) ベースの Azure 内クラウド製品のハイブリッド アーキテクチャとシナリオについて説明します。'
ms.openlocfilehash: f4d90d51a7627063fae6fd168681bdf96cb4d6bc
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741373"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a><span data-ttu-id="dd8e0-103">Azure PaaS のハイブリッド クラウド シナリオ</span><span class="sxs-lookup"><span data-stu-id="dd8e0-103">Hybrid cloud scenarios for Azure PaaS</span></span>

 <span data-ttu-id="dd8e0-104">**概要:** Microsoft のサービスとしてのプラットフォーム (PaaS) ベースの Azure 内クラウド製品のハイブリッド アーキテクチャとシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Platform as a Service (PaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="dd8e0-105">オンプレミスのデータ リソースまたはコンピューティング リソースを、Azure PaaS で実行されている新規または変換後のアプリケーションと組み合わせます。これにより、クラウドのパフォーマンス、信頼性、およびスケールを利用し、モバイル ユーザーにより良いサポートを提供できます。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-105">Combine on-premises data or computing resources with new or converted applications running in Azure PaaS, which can take advantage of cloud performance, reliability, and scale and provide better support for mobile users.</span></span> 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a><span data-ttu-id="dd8e0-106">Azure PaaS のハイブリッド シナリオ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="dd8e0-106">Azure PaaS hybrid scenario architecture</span></span>

<span data-ttu-id="dd8e0-107">図 1 は、Microsoft PaaS ベースの Azure 内ハイブリッド シナリオのアーキテクチャを示しています。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-107">Figure 1 shows the architecture of Microsoft PaaS-based hybrid scenarios in Azure.</span></span>
  
**<span data-ttu-id="dd8e0-108">図 1:Microsoft PaaS ベースの Azure 内ハイブリッド シナリオ</span><span class="sxs-lookup"><span data-stu-id="dd8e0-108">Figure 1: Microsoft PaaS-based hybrid scenarios in Azure</span></span>**

![Microsoft PaaS ベースの Azure 内ハイブリッド シナリオ](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
<span data-ttu-id="dd8e0-110">アーキテクチャの各レイヤーについて:</span><span class="sxs-lookup"><span data-stu-id="dd8e0-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="dd8e0-111">アプリとシナリオ</span><span class="sxs-lookup"><span data-stu-id="dd8e0-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="dd8e0-112">ハイブリッド PaaS アプリケーションは Azure で実行され、オンプレミスのコンピューティング リソースまたはストレージ リソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-112">A hybrid PaaS application runs in Azure and uses on-premises compute or storage resources.</span></span>
    
- <span data-ttu-id="dd8e0-113">ID</span><span class="sxs-lookup"><span data-stu-id="dd8e0-113">Identity</span></span>
    
    <span data-ttu-id="dd8e0-114">サードパーティ ID プロバイダーとのディレクトリ同期またはフェデレーションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-114">Consists of either directory synchronization or federation with a third-party identity provider.</span></span>
    
- <span data-ttu-id="dd8e0-115">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="dd8e0-115">Network</span></span>
    
    <span data-ttu-id="dd8e0-p101">既存のインターネット パイプ、または Azure PaaS に対するパブリック ピアリングとの ExpressRoute 接続で構成されています。Azure PaaS アプリケーションがオンプレミスのコンピューティング リソースまたはストレージ リソースにアクセスするための手段を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-p101">Consists of either your existing Internet pipe or an ExpressRoute connection with public peering to Azure PaaS. You must include a way for the Azure PaaS application to access the on-premises compute or storage resource.</span></span>
    
- <span data-ttu-id="dd8e0-118">オンプレミス</span><span class="sxs-lookup"><span data-stu-id="dd8e0-118">On-premises</span></span>
    
    <span data-ttu-id="dd8e0-119">ID およびセキュリティ インフラストラクチャと、既存の基幹業務 (LOB) アプリケーションまたはデータベース サーバーで構成されています。これらには、Azure PaaS アプリケーションから安全にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-119">Consists of identity and security infrastructure and existing line of business (LOB) applications or database servers, which an Azure PaaS application can securely access.</span></span>
    
## <a name="azure-paas-hybrid-application"></a><span data-ttu-id="dd8e0-120">Azure PaaS ハイブリッド アプリケーション</span><span class="sxs-lookup"><span data-stu-id="dd8e0-120">Azure PaaS hybrid application</span></span>

<span data-ttu-id="dd8e0-121">図 2 は、Azure で実行されているハイブリッド アプリケーションの構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-121">Figure 2 shows the configuration of a hybrid application running in Azure.</span></span>
  
**<span data-ttu-id="dd8e0-122">図 2:Azure PaaS ベースのハイブリッド アプリケーション</span><span class="sxs-lookup"><span data-stu-id="dd8e0-122">Figure 2: Azure PaaS-based hybrid application</span></span>**

![Azure PaaS ベースのハイブリッド アプリケーション](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
<span data-ttu-id="dd8e0-p102">図 2 では、オンプレミスのネットワークは、サーバー上、およびプロキシ サーバーを含む DMZ 上のストレージまたはアプリをホストします。インターネット経由で、または ExpressRoute に接続して、Azure PaaS サービスに接続されています。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-p102">In Figure 2, an on-premises network hosts storage or apps on servers and a DMZ containing a proxy server. It is connected to Azure PaaS services either over the Internet or with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="dd8e0-126">組織は、次の方法により、コンピューティング リソースまたはストレージ リソースを Azure PaaS ハイブリッド アプリケーションで使用可能にできます。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-126">An organization can make its compute or storage resources available to the Azure PaaS hybrid application by:</span></span>
  
- <span data-ttu-id="dd8e0-127">DMZ のサーバー上のリソースをホストします。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-127">Hosting the resource on servers in the DMZ.</span></span>
    
- <span data-ttu-id="dd8e0-128">DMZ のリバース プロキシ サーバーをホストします。これにより、オンプレミスに配置されているリソースに対して、認証済みの HTTPS ベースの着信要求が許可されます。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-128">Hosting a reverse proxy server in the DMZ, which allows authenticated, inbound, HTTPS-based requests to the resource that is located on-premises.</span></span>
    
<span data-ttu-id="dd8e0-129">Azure アプリは、次の資格情報を使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-129">The Azure app can use credentials from:</span></span>
  
- <span data-ttu-id="dd8e0-130">Azure AD (Active Directory ドメインサービス (AD DS) など、オンプレミスの id プロバイダーと同期させることができます。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-130">Azure AD, which can be synchronized with your on-premises identity provider, such as Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="dd8e0-131">サードパーティ ID プロバイダー。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-131">A third-party identity provider.</span></span>
    
### <a name="example-azure-paas-hybrid-application"></a><span data-ttu-id="dd8e0-132">Azure PaaS ハイブリッド アプリケーションの例</span><span class="sxs-lookup"><span data-stu-id="dd8e0-132">Example Azure PaaS hybrid application</span></span>

<span data-ttu-id="dd8e0-133">図 3 は、Azure で実行されているハイブリッド アプリケーションの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-133">Figure 3 shows an example hybrid application running in Azure.</span></span>
  
**<span data-ttu-id="dd8e0-134">図 3:Azure PaaS ベースのハイブリッド アプリケーションの例</span><span class="sxs-lookup"><span data-stu-id="dd8e0-134">Figure 3: An example Azure PaaS-based hybrid application</span></span>**

![Azure PaaS ベースのハイブリッド アプリケーション例](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
<span data-ttu-id="dd8e0-p103">図 3 では、オンプレミスのネットワークは、LOB アプリをホストします。Azure PaaS は、カスタム モバイル アプリをホストします。インターネット上のスマートフォンは Azure 内のカスタム モバイル アプリにアクセスし、このアプリはオンプレミスの LOB アプリにデータ要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-p103">In Figure 3, an on-premises network hosts an LOB app. Azure PaaS hosts a custom mobile app. A smartphone on the Internet accesses the custom mobile app in Azure, which sends data requests to the on-premises LOB app.</span></span>
  
<span data-ttu-id="dd8e0-p104">この Azure PaaS ハイブリッド アプリケーションの例は、従業員の最新の連絡先情報を提供するカスタム モバイル アプリです。エンドツーエンドのハイブリッド シナリオは、次の要素で構成されています。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-p104">This example Azure PaaS hybrid application is a custom mobile app that provides up-to-date contact information on employees. The end-to-end hybrid scenario consists of:</span></span>
  
- <span data-ttu-id="dd8e0-141">スマートフォン アプリ。実行するために検証済みのオンプレミス資格情報を必要とします。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-141">A smartphone app that requires validated, on-premises credentials to run.</span></span>
    
- <span data-ttu-id="dd8e0-142">Azure PaaS で実行されているカスタム モバイル アプリ。このアプリは、ユーザーのスマートフォン アプリからのクエリに基づき、特定の従業員に関する情報を要求します。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-142">A custom mobile app running in Azure PaaS, which requests information about specific employees based on queries from a user's smartphone app.</span></span>
    
- <span data-ttu-id="dd8e0-143">DMZ のリバース プロキシ サーバー。カスタム モバイル アプリを検証し、要求を転送します。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-143">A reverse proxy server in the DMZ that validates the custom mobile app and forwards the request.</span></span>
    
- <span data-ttu-id="dd8e0-144">LOB アプリケーション サーバー ファーム。ユーザーのアカウントのアクセス許可に従い、連絡先要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-144">An LOB application server farm that services the contact request, subject to the permissions of the user's account.</span></span>
    
<span data-ttu-id="dd8e0-145">オンプレミスの ID プロバイダーは Azure AD と同期されているため、カスタム モバイル アプリと LOB アプリの両方が要求元ユーザーのアカウント名を検証できます。</span><span class="sxs-lookup"><span data-stu-id="dd8e0-145">Because the on-premises identity provider has been synchronized with Azure AD, both the custom mobile app and the LOB app can validate the requesting user's account name.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dd8e0-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd8e0-146">See Also</span></span>

[<span data-ttu-id="dd8e0-147">エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド</span><span class="sxs-lookup"><span data-stu-id="dd8e0-147">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="dd8e0-148">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="dd8e0-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

