---
title: アクセス可能な図 - 設計サンプル SharePoint 2013 のための Microsoft Azure のインターネット サイト
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: 'この記事は、「設計サンプル: SharePoint 2013 のための Microsoft Azure のインターネット サイト」という名前の図のアクセス可能なテキスト バージョンです。'
ms.openlocfilehash: 52ae615cbdc6a355155e54e36bc6a3d733d84869
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "38027631"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a><span data-ttu-id="96a8d-103">アクセス可能な図 - 設計サンプル: SharePoint 2013 のための Microsoft Azure のインターネット サイト</span><span class="sxs-lookup"><span data-stu-id="96a8d-103">Accessible diagram - Design sample: Internet sites in Microsoft Azure for SharePoint 2013</span></span>

<span data-ttu-id="96a8d-104">**概要:** この記事は、「設計サンプル: SharePoint 2013 のための Microsoft Azure のインターネット サイト」という名前の図のアクセス可能なテキスト バージョンです。</span><span class="sxs-lookup"><span data-stu-id="96a8d-104">**Summary:** This article is an accessible text version of the diagram named Design sample: Internet sites in Microsoft Azure for SharePoint 2013.</span></span>
  
<span data-ttu-id="96a8d-105">SharePoint 2013 を使って、インターネットに直接接続されているサイトの開始点としてこの設計例を使用してください。</span><span class="sxs-lookup"><span data-stu-id="96a8d-105">Use this design example as a starting point for an Internet-facing site in Azure using SharePoint 2013.</span></span>
  
<span data-ttu-id="96a8d-106">このポスターは、SharePoint 2013 の次の側面を設計する方法の例を示しています。</span><span class="sxs-lookup"><span data-stu-id="96a8d-106">This poster shows an example of how to design the following aspects of SharePoint 2013:</span></span>
  
- <span data-ttu-id="96a8d-107">ユーザー</span><span class="sxs-lookup"><span data-stu-id="96a8d-107">Users</span></span>
    
- <span data-ttu-id="96a8d-108">領域と認証</span><span class="sxs-lookup"><span data-stu-id="96a8d-108">Zones and authentication</span></span>
    
- <span data-ttu-id="96a8d-109">サーバー ファーム</span><span class="sxs-lookup"><span data-stu-id="96a8d-109">Server farm</span></span>
    
- <span data-ttu-id="96a8d-110">管理サイト</span><span class="sxs-lookup"><span data-stu-id="96a8d-110">Administration site</span></span>
    
- <span data-ttu-id="96a8d-111">サービス</span><span class="sxs-lookup"><span data-stu-id="96a8d-111">Services</span></span>
    
- <span data-ttu-id="96a8d-112">アプリケーション プールと Web アプリケーション</span><span class="sxs-lookup"><span data-stu-id="96a8d-112">Application pools and web applications</span></span>
    
- <span data-ttu-id="96a8d-113">サイト コレクション</span><span class="sxs-lookup"><span data-stu-id="96a8d-113">Site collections</span></span>
    
- <span data-ttu-id="96a8d-114">サイト</span><span class="sxs-lookup"><span data-stu-id="96a8d-114">Sites</span></span>
    
- <span data-ttu-id="96a8d-115">コンテンツ データベース</span><span class="sxs-lookup"><span data-stu-id="96a8d-115">Content databases</span></span>
    
- <span data-ttu-id="96a8d-116">領域と URL</span><span class="sxs-lookup"><span data-stu-id="96a8d-116">Zones and URLs</span></span>
    
## <a name="users-zones-and-authentication"></a><span data-ttu-id="96a8d-117">ユーザー、領域、認証</span><span class="sxs-lookup"><span data-stu-id="96a8d-117">Users, zones and authentication</span></span>

<span data-ttu-id="96a8d-p101">この設計には、4 種類のユーザー アカウントがあります。各種類のアカウントは、アクセス用のサイト、および特定の種類の認証を使用する領域と関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="96a8d-p101">There are four types of user accounts in this design. Each type of account is associated with a site for access and with a zone that uses a specific type of authentication.</span></span> 
  
- <span data-ttu-id="96a8d-p102">匿名の顧客  匿名の顧客は、https://www.contoso.com などのサイトを介してアクセスします。使用する領域は、匿名認証を使用する "Internet zone / anonymous" です。</span><span class="sxs-lookup"><span data-stu-id="96a8d-p102">Anonymous customers — Anonymous customers have access through a site such as https://www.contoso.com. The zone they use is the "Internet zone / anonymous", which uses anonymous authentication.</span></span>
    
- <span data-ttu-id="96a8d-p103">認証済みの顧客  認証済みの顧客は、https://secure.contoso.com などのサイトを介してアクセスします。使用する領域は、Azure Active Directory および SAML 認証を使用する "Extranet zone / SAML" です。</span><span class="sxs-lookup"><span data-stu-id="96a8d-p103">Authenticated customers — Authenticated customers have access through a site such as https://secure.contoso.com. The zone they use is the "Extranet zone / SAML", which uses Azure Active Directory with SAML authentication.</span></span>
    
- <span data-ttu-id="96a8d-p104">サイトの作成者と開発者  サイトの作成者と開発者は、https://authoring.contoso.com:8000 または https://www.contoso.com:8000 などのサイトを介してアクセスします。使用する領域は、Active Directory ドメイン サービス (AD DS) を使用する "Default zone / Windows integrated" です。</span><span class="sxs-lookup"><span data-stu-id="96a8d-p104">Site authors and developers — Site authors and developers have access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000. The zone they use is the "Default zone / Windows integrated", which uses Active Directory Domain Services (AD DS).</span></span>
    
- <span data-ttu-id="96a8d-p105">検索クロール アカウント  検索クロール アカウントは、https://authoring.contoso.com:8000 または https://www.contoso.com:8000 などのサイトを介してアクセスします。使用する領域は、AD DS および Windows NTLM 認証を使用する "Default zone / Windows integrated" です。</span><span class="sxs-lookup"><span data-stu-id="96a8d-p105">Search Crawl Account — The search crawl account has access through sites such as https://authoring.contoso.com:8000 or https://www.contoso.com:8000. The zone it uses is the "Default zone / Windows integrated", which uses AD DS with Windows NTLM authentication.</span></span>
    
## <a name="server-farm"></a><span data-ttu-id="96a8d-128">サーバー ファーム</span><span class="sxs-lookup"><span data-stu-id="96a8d-128">Server farm</span></span>

<span data-ttu-id="96a8d-p106">ユーザーは、Azure を経由してサーバー ファームにアクセスします。サーバー ファームには 1 つ以上の Web サーバーがあります。</span><span class="sxs-lookup"><span data-stu-id="96a8d-p106">The users access the server farm through Azure. The server farm contains one or more Web servers.</span></span>
  
## <a name="administration-site"></a><span data-ttu-id="96a8d-131">管理サイト</span><span class="sxs-lookup"><span data-stu-id="96a8d-131">Administration site</span></span>

<span data-ttu-id="96a8d-p107">管理サイトには、複数のアプリケーション サーバーがあります。これらのサーバーは、Web アプリケーションの全体管理サイトを使用するアプリケーション プール (例ではアプリケーション プール 1) と通信します。全体管理サイトでは、組織内のサイト コレクションにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="96a8d-p107">The administration site contains several application servers, which communicate with an Application Pool (Application Pool 1 in the example) that uses the web application Central Administration Site. The Central Administration Site provides access to site collections within the organization.</span></span>
  
<span data-ttu-id="96a8d-134">管理サイトには、SQL Database サーバーも含まれています。これは、SQL クラスタリング、ミラーリング、または AlwaysOn (AlwaysOn は SQL Server 2012 にのみ適用されます) をサポートするようにインストールおよび構成された SQL Server を持つデータベース サーバーです。</span><span class="sxs-lookup"><span data-stu-id="96a8d-134">The administration site also contains SQL Database servers, which are database servers with SQL Server installed and configured to support SQL clustering, mirroring, or AlwaysOn (AlwaysOn applies to SQL Server 2012 only).</span></span>
  
## <a name="services"></a><span data-ttu-id="96a8d-135">サービス</span><span class="sxs-lookup"><span data-stu-id="96a8d-135">Services</span></span>

<span data-ttu-id="96a8d-p108">設計例は、インターネット インフォメーション サービス (IIS) Web サイト、SharePoint Web サービスを示しています。SharePoint Web サービスには、ユーザー プロファイル、検索、および管理されたメタデータという 3 つのサービスがあるアプリケーション プール (アプリケーション プール 2) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="96a8d-p108">The design example shows an Internet Information Services (IIS) website, SharePoint Web Services. SharePoint Web Services contains an application pool (Application Pool 2) with three services, User Profile, Search, and Managed Metadata.</span></span>
  
<span data-ttu-id="96a8d-138">インターネット サイト向けのサービスに関する注意事項:</span><span class="sxs-lookup"><span data-stu-id="96a8d-138">Notes on Services for Internet sites:</span></span>
  
> <span data-ttu-id="96a8d-139">管理されたメタデータ  必ず " **このサービス アプリケーションは列固有の用語セットの既定の格納場所です**" を選択してください。</span><span class="sxs-lookup"><span data-stu-id="96a8d-139">Managed Metadata — Be sure to select **This service application is the default storage location for column specific term sets**.</span></span>
    
> <span data-ttu-id="96a8d-140">アプリケーション管理 — Azure では、一般向けのインターネット サイトでアプリを使用することはお勧めしていません。</span><span class="sxs-lookup"><span data-stu-id="96a8d-140">App Management — We do not recommend using apps in a public-facing Internet site in Azure.</span></span>
    
## <a name="application-pools-and-web-applications"></a><span data-ttu-id="96a8d-141">アプリケーション プールと Web アプリケーション</span><span class="sxs-lookup"><span data-stu-id="96a8d-141">Application pools and web applications</span></span>

<span data-ttu-id="96a8d-p109">Azure の既定のグループは、Contoso Sites という名前の Web アプリケーションを含むアプリケーション プール 3 を示しています。このパスベースのサイト コレクションは https://internal:8000 にあります。</span><span class="sxs-lookup"><span data-stu-id="96a8d-p109">The Default Group in Azure shows Application Pool 3, which contains a web application named Contoso Sites. This path-based site collection is located at https://internal:8000.</span></span>
  
## <a name="site-collections-and-sites"></a><span data-ttu-id="96a8d-144">サイト コレクションおよびサイト</span><span class="sxs-lookup"><span data-stu-id="96a8d-144">Site collections and sites</span></span>

<span data-ttu-id="96a8d-145">アプリケーション プールに含まれるサイト コレクションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="96a8d-145">The site collections contained in the application pool include:</span></span>
  
- <span data-ttu-id="96a8d-146">クロール用のホスト名付きサイト コレクション 1 (場所の例: https://authoring.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="96a8d-146">Host-named site collection 1 for crawling (example location https://authoring.contoso.com:8000)</span></span>
    
- <span data-ttu-id="96a8d-147">クエリ用のホスト名付きサイト コレクション 2 (場所の例: https://www.contoso.com、https://secure.contoso.com、https://www.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="96a8d-147">Host-named site collection 2 for queries (sample locations https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000)</span></span>
    
- <span data-ttu-id="96a8d-148">クエリ用のホスト名付きサイト コレクション 3 (場所の例: https://assets.contoso.com、https://secureassets.contoso.com、https://assets.contoso.com:8000)</span><span class="sxs-lookup"><span data-stu-id="96a8d-148">Host-named site collection 3 for queries (sample locations https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000)</span></span>
    
## <a name="content-databases"></a><span data-ttu-id="96a8d-149">コンテンツ データベース</span><span class="sxs-lookup"><span data-stu-id="96a8d-149">Content databases</span></span>

<span data-ttu-id="96a8d-p110">例は、2 つのコンテンツ データベースを示しています。1 つは、クロール用のサイト コレクション 1 (https://authoring.contoso.com:8000) です。もう 1 つは、クエリ用の 2 つのサイト コレクション (サイト コレクション 2 および 3) (https://www.contoso.com、https://secure.contoso.com、https://www.contoso.com:8000、または https://assets.contoso.com、https://secureassets.contoso.com、https://assets.contoso.com:8000) です。</span><span class="sxs-lookup"><span data-stu-id="96a8d-p110">The example shows two content databases. One is for the site collection 1 used for crawling (https://authoring.contoso.com:8000). The other is for the two site collections 2 and 3 used for queries (https://www.contoso.com, https://secure.contoso.com, https://www.contoso.com:8000, or https://assets.contoso.com, https://secureassets.contoso.com, https://assets.contoso.com:8000).</span></span>
  
## <a name="zones-and-urls"></a><span data-ttu-id="96a8d-153">領域と URL</span><span class="sxs-lookup"><span data-stu-id="96a8d-153">Zones and URLs</span></span>

<span data-ttu-id="96a8d-154">例は、異なるユーザー アカウントで使用される、3 つの領域と関連する負荷分散された URL を示しています。</span><span class="sxs-lookup"><span data-stu-id="96a8d-154">The example shows three zones with the associated load-balanced URLs that are used by different user accounts.</span></span> 
  
<span data-ttu-id="96a8d-155">最初の領域と URL のリストはサイト コレクション 1 と関係し、次の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="96a8d-155">The first list of zones and URLs is related to site collection 1, and it contains the following information:</span></span>
  
- <span data-ttu-id="96a8d-156">ユーザー - サイトの作成者</span><span class="sxs-lookup"><span data-stu-id="96a8d-156">Users - Site authors</span></span>
    
- <span data-ttu-id="96a8d-157">領域 - 既定</span><span class="sxs-lookup"><span data-stu-id="96a8d-157">Zone - Default</span></span>
    
- <span data-ttu-id="96a8d-158">負荷分散された URL - https://authoring.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="96a8d-158">Load-balanced URL - https://authoring.contoso.com:8000</span></span>
    
<span data-ttu-id="96a8d-p111">2 番目の領域と URL のリストには、3 つの異なる領域に 3 種類のユーザーが含まれています。このリストはサイト コレクション 2 と関係し、次の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="96a8d-p111">The second list of zones and URLs has three different types of users in three different zones. It is related to site collection 2, and it contains the following information:</span></span>
  
<span data-ttu-id="96a8d-161">最初の領域:</span><span class="sxs-lookup"><span data-stu-id="96a8d-161">First zone:</span></span>
  
- <span data-ttu-id="96a8d-162">ユーザー - サイトの作成者</span><span class="sxs-lookup"><span data-stu-id="96a8d-162">Users - Site authors</span></span>
    
- <span data-ttu-id="96a8d-163">領域 - 既定</span><span class="sxs-lookup"><span data-stu-id="96a8d-163">Zone - Default</span></span>
    
- <span data-ttu-id="96a8d-164">負荷分散された URL - https://www.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="96a8d-164">Load-balanced URL - https://www.contoso.com:8000</span></span>
    
<span data-ttu-id="96a8d-165">2 番目の領域:</span><span class="sxs-lookup"><span data-stu-id="96a8d-165">Second zone:</span></span>
  
- <span data-ttu-id="96a8d-166">ユーザー - 匿名の顧客</span><span class="sxs-lookup"><span data-stu-id="96a8d-166">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="96a8d-167">領域 - インターネット</span><span class="sxs-lookup"><span data-stu-id="96a8d-167">Zone - Internet</span></span>
    
- <span data-ttu-id="96a8d-168">負荷分散された URL - https://www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="96a8d-168">Load-balanced URL - https://www.contoso.com</span></span>
    
<span data-ttu-id="96a8d-169">3 番目の領域:</span><span class="sxs-lookup"><span data-stu-id="96a8d-169">Third zone:</span></span>
  
- <span data-ttu-id="96a8d-170">ユーザー - 認証済みの顧客</span><span class="sxs-lookup"><span data-stu-id="96a8d-170">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="96a8d-171">領域 - エクストラネット</span><span class="sxs-lookup"><span data-stu-id="96a8d-171">Zone - Extranet</span></span>
    
- <span data-ttu-id="96a8d-172">負荷分散された URL - https://secure.contoso.com</span><span class="sxs-lookup"><span data-stu-id="96a8d-172">Load-balanced URL - https://secure.contoso.com</span></span>
    
<span data-ttu-id="96a8d-p112">3 番目の領域と URL のリストには、3 つの異なる領域に 3 種類のユーザーが含まれています。このリストはサイト コレクション 3 と関係し、次の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="96a8d-p112">The third list of zones and URLs has three different types of users in three different zones. It is related to site collection 3, and it contains the following information:</span></span>
  
<span data-ttu-id="96a8d-175">最初の領域:</span><span class="sxs-lookup"><span data-stu-id="96a8d-175">First zone:</span></span>
  
- <span data-ttu-id="96a8d-176">ユーザー - サイトの作成者</span><span class="sxs-lookup"><span data-stu-id="96a8d-176">Users - Site authors</span></span>
    
- <span data-ttu-id="96a8d-177">領域 - インターネット</span><span class="sxs-lookup"><span data-stu-id="96a8d-177">Zone - Internet</span></span>
    
- <span data-ttu-id="96a8d-178">負荷分散された URL - https://assets.contoso.com:8000</span><span class="sxs-lookup"><span data-stu-id="96a8d-178">Load-balanced URL - https://assets.contoso.com:8000</span></span>
    
<span data-ttu-id="96a8d-179">2 番目の領域:</span><span class="sxs-lookup"><span data-stu-id="96a8d-179">Second zone:</span></span>
  
- <span data-ttu-id="96a8d-180">ユーザー - 匿名の顧客</span><span class="sxs-lookup"><span data-stu-id="96a8d-180">Users - Anonymous customers</span></span>
    
- <span data-ttu-id="96a8d-181">領域 - インターネット</span><span class="sxs-lookup"><span data-stu-id="96a8d-181">Zone - Internet</span></span>
    
- <span data-ttu-id="96a8d-182">負荷分散された URL - https://assets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="96a8d-182">Load-balanced URL - https://assets.contoso.com</span></span>
    
<span data-ttu-id="96a8d-183">3 番目の領域:</span><span class="sxs-lookup"><span data-stu-id="96a8d-183">Third zone:</span></span>
  
- <span data-ttu-id="96a8d-184">ユーザー - 認証済みの顧客</span><span class="sxs-lookup"><span data-stu-id="96a8d-184">Users - Authenticated customers</span></span>
    
- <span data-ttu-id="96a8d-185">領域 - エクストラネット</span><span class="sxs-lookup"><span data-stu-id="96a8d-185">Zone - Extranet</span></span>
    
- <span data-ttu-id="96a8d-186">負荷分散された URL - https://secureassets.contoso.com</span><span class="sxs-lookup"><span data-stu-id="96a8d-186">Load-balanced URL - https://secureassets.contoso.com</span></span>
    

