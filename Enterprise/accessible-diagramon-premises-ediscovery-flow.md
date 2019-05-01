---
title: アクセス可能な図 - オンプレミスの電子情報開示のフロー
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: この記事は、「オンプレミスの電子情報開示のフロー」という名前の図のアクセス可能なテキスト バージョンです。
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487703"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="57710-103">アクセス可能な図 - オンプレミスの電子情報開示のフロー</span><span class="sxs-lookup"><span data-stu-id="57710-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="57710-104">**概要:** この記事は、「オンプレミスの電子情報開示のフロー」という名前の図のアクセス可能なテキスト バージョンです。</span><span class="sxs-lookup"><span data-stu-id="57710-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="57710-105">このポスターは、サーバー製品間のデータのアーキテクチャとフローについて詳しく説明しています。</span><span class="sxs-lookup"><span data-stu-id="57710-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="57710-106">SharePoint、Exchange、Lync、およびファイル共有にわたる流れ</span><span class="sxs-lookup"><span data-stu-id="57710-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="57710-p101">図は、2 つのサーバー ファーム (SharePoint 2013 エンタープライズ アプリ ファーム、および SharePoint 2013 サービス ファーム) にアクセスするクエリを送信するユーザーを示しています。SharePoint 2013 サービス ファームは、SharePoint 2013 コンテンツ ファーム、Exchange Server 2013 (Lync 2013 と通信する)、および Windows ファイル共有と通信します。</span><span class="sxs-lookup"><span data-stu-id="57710-p101">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm. The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="57710-109">電子情報開示フロー リストには、データ フローおよび SharePoint、Exchange、Lync、およびファイル共有の間で電子情報開示クエリのアクションが発生する順序が記載されています。</span><span class="sxs-lookup"><span data-stu-id="57710-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="57710-110">電子情報開示フロー リストは、最初に詳しい説明、続いて機能の詳細説明が図に表されて記載されています。</span><span class="sxs-lookup"><span data-stu-id="57710-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="57710-111">電子情報開示フロー リスト</span><span class="sxs-lookup"><span data-stu-id="57710-111">eDiscovery Flow List</span></span>

<span data-ttu-id="57710-p102">このリストに記載されている各手順の番号は、図に表された手順と関係しています。図については、このドキュメントの後半で詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="57710-p102">The numbers for each of the steps described in this list pertain to a step depicted in the diagram. The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="57710-p103">電子情報開示のケースは、電子情報開示センター (EDC) で作成、管理、および使用されます。EDC は SharePoint 2013 のサイト コレクションです。 ここで、ケースの定義、追跡するソースの識別、クエリの発行、クエリ結果の確認、コンテンツ保留の設定/解除を実行します。</span><span class="sxs-lookup"><span data-stu-id="57710-p103">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC). The EDC is a SharePoint 2013 site collection. This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="57710-p104">電子情報開示のクエリまたはアクション (保留、保留の解除、GetStatus など) は、EDC からエンタープライズ アプリ ファーム内の Search Service アプリケーション (SSA) プロキシへ中継されます。 次に、SSA プロキシは Services アプリ ファーム内の SSA へトラフィックを中継します。 この例における要求は、SharePoint コンテンツ ファーム内でファイル名に "CONTOSO" を含むものすべてを保留にすることです。</span><span class="sxs-lookup"><span data-stu-id="57710-p104">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm. The SSA proxy then relays the traffic to the SSA in the Services App Farm. In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="57710-p105">要求がケースのクエリを実行することである場合、SSA は検索インデックスを参照します。続いて、電子情報開示のクエリの結果セットが、EDC を介してユーザーに返されます。</span><span class="sxs-lookup"><span data-stu-id="57710-p105">If the request is to query a case, the SSA consults the search index. Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="57710-p106">要求が保留や保留の解除などのアクションである場合、そのアクションは SSA 管理データベース内の Actions_Table に書き込まれます。 この例では、SharePoint コンテンツ ファーム内で "CONTOSO" を含むものすべてに対する保留要求が Actions_Table に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="57710-p106">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database. In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="57710-124">コンテンツ ファームの eDiscovery インプレース保持タイマー ジョブは定期的に起動し、保留中のアクションに対して要求を生成します。さらに、SSA プロキシを通して SSA へステータス更新を送信します。</span><span class="sxs-lookup"><span data-stu-id="57710-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="57710-p107">保留中のアクションに対するクエリは中央の SSA へ中継され、そこでコンテンツ ファームの保留中のアクションについて Action_Table を参照します。 さらに、コンテンツ ファームのインプレース保持タイマー ジョブは、受信したオブジェクトおよびアクションのステータス更新を送信し、それらは ActionsTable に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="57710-p107">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm. The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="57710-127">SharePoint 2013 コンテンツ ファーム内の、名前に "CONTOSO" を含むすべてのコンテンツに対する保留要求は、SSA によりコンテンツ ファーム内の電子情報開示のインプレース保持タイマー ジョブへ送信されます。</span><span class="sxs-lookup"><span data-stu-id="57710-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="57710-128">電子情報開示のインプレース保持タイマー ジョブは、"CONTOSO サイト" と "CONTOSO コンテンツ" を保留にします。</span><span class="sxs-lookup"><span data-stu-id="57710-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="57710-129">電子情報開示のインプレース保持タイマー ジョブは、エンタープライズ アプリケーション ファーム内で定期的に実行され、検出アクションのステータスの確認およびステータスの更新を行います。</span><span class="sxs-lookup"><span data-stu-id="57710-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="57710-130">ステータス クエリは、エンタープライズ アプリケーション ファームの SSA プロキシを介して SharePoint Services ファームの SSA へ中継されます。</span><span class="sxs-lookup"><span data-stu-id="57710-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="57710-131">SSA は、アクション テーブルからステータスを取得し、エンタープライズ アプリケーション ファーム内のタイマー ジョブへ返します。それから、ステータス更新が EDC へ送信されます。</span><span class="sxs-lookup"><span data-stu-id="57710-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="57710-p108">電子情報開示ユーザーがメールボックスやアーカイブ済みの Lync コンテンツなどの Exchange ソースを検索 (またはアクションを実行) している場合、中央の SSA は Exchange Web Services (EWS) プロキシを使用して Exchange Web Services を照会します。 Exchange には独自の検索および電子情報開示インフラストラクチャがあり、すべての電子情報開示の呼び出しを内部で管理しています。</span><span class="sxs-lookup"><span data-stu-id="57710-p108">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services. Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="57710-134">Exchange Web サービスは、電子情報開示の検索結果により SSA に応答します。または、クエリベースの保留に対するステータス要求に応答して EDC へ中継します。</span><span class="sxs-lookup"><span data-stu-id="57710-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="57710-135">前提条件</span><span class="sxs-lookup"><span data-stu-id="57710-135">Prerequisites</span></span>

- <span data-ttu-id="57710-136">SharePoint エンタープライズ検索を設定する必要があり、コンテンツ ソース (SharePoint および Windows ファイル共有) の検索クロールが正常に実行され、すべてのコンテンツ ソースがインデックスにある。</span><span class="sxs-lookup"><span data-stu-id="57710-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="57710-137">SharePoint Services ファームと Exchange 間、および Exchange と Lync 間でサーバー間の信頼と認証を設定する必要がある。</span><span class="sxs-lookup"><span data-stu-id="57710-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="57710-138">図中の構成要素の説明</span><span class="sxs-lookup"><span data-stu-id="57710-138">Description of components in the diagram</span></span>

<span data-ttu-id="57710-p109">図は、2 つのサーバー ファーム (SharePoint 2013 エンタープライズ アプリ ファーム、および SharePoint 2013 サービス ファーム) にアクセスするクエリを送信するユーザーを示しています。SharePoint Services ファームは、SharePoint 2013 コンテンツ ファーム、Exchange Server 2013 (Lync 2013 とインターフェイスする)、および Windows ファイル共有とインターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="57710-p109">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm. The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="57710-141">SharePoint 2013 エンタープライズ アプリケーション ファーム</span><span class="sxs-lookup"><span data-stu-id="57710-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="57710-142">SharePoint 2013 エンタープライズ アプリケーション ファームには、次のコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="57710-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="57710-143">EDC</span><span class="sxs-lookup"><span data-stu-id="57710-143">EDC</span></span>
    
- <span data-ttu-id="57710-144">SSA プロキシ </span><span class="sxs-lookup"><span data-stu-id="57710-144">SSA proxy</span></span> 
    
- <span data-ttu-id="57710-145">タイマー ジョブ</span><span class="sxs-lookup"><span data-stu-id="57710-145">Timer job</span></span> 
    
<span data-ttu-id="57710-p110">ユーザーが送信するクエリまたはアクションは、エンタープライズ アプリケーション ファームの EDC に送信されます。次のアクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="57710-p110">A query or action sent by the user is sent to the EDC in the Enterprise App Farm. The following actions occur:</span></span> 
  
- <span data-ttu-id="57710-148">クエリまたはアクションは、SSA プロキシに移動します。</span><span class="sxs-lookup"><span data-stu-id="57710-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="57710-p111">SSA プロキシは、エンタープライズ アプリケーション ファームのタイマー ジョブにステータス クエリまたは応答を送信するとともに、SharePoint Services ファームの SSA サービスにもステータス クエリまたは応答を送信します。この結果として起こるアクションについては、SharePoint Services ファームに関するセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="57710-p111">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm. The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="57710-151">タイマー ジョブは、応答を受信すると、SSA のプロキシと EDC に応答を送信します。</span><span class="sxs-lookup"><span data-stu-id="57710-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="57710-152">クエリまたはアクションの結果はすべて、EDC のユーザーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="57710-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="57710-153">SharePoint 2013 Services ファーム</span><span class="sxs-lookup"><span data-stu-id="57710-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="57710-154">SharePoint 2013 Services ファームには、次のコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="57710-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="57710-155">SSA サービス</span><span class="sxs-lookup"><span data-stu-id="57710-155">SSA Service</span></span> 
    
- <span data-ttu-id="57710-156">検索インデックス データベース</span><span class="sxs-lookup"><span data-stu-id="57710-156">Search index database</span></span> 
    
- <span data-ttu-id="57710-p112">SSA admin_db データベース。このデータベースのアクション テーブルには次が含まれます。 保留、保留の解除、GetStatus</span><span class="sxs-lookup"><span data-stu-id="57710-p112">SSA admin_db database. The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="57710-159">EWS プロキシ</span><span class="sxs-lookup"><span data-stu-id="57710-159">EWS proxy</span></span> 
    
<span data-ttu-id="57710-160">SharePoint エンタープライズ アプリケーション ファームの SSA プロキシが SharePoint Services ファーム内の SSA にステータス クエリを送信すると、次のアクションが発生します。</span><span class="sxs-lookup"><span data-stu-id="57710-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="57710-p113">要求がクエリの場合、SSA は検索インデックスを参照します。検出の応答は SSA に返されてから、EDC を経由してユーザーに返されます。</span><span class="sxs-lookup"><span data-stu-id="57710-p113">If the request is a query, the SSA consults the search index. The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="57710-163">要求が書き込み操作の場合、SSA サービスは SSAadmin_db に書き込み操作を送信します。</span><span class="sxs-lookup"><span data-stu-id="57710-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="57710-164">クロールおよび結果応答要求は、SSA から SharePoint 2013 コンテンツ ファームに送信され、応答は SSA に返されます。</span><span class="sxs-lookup"><span data-stu-id="57710-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="57710-165">クロールおよび結果応答要求は、SSA から Windows ファイル共有に送信され、応答は SSA に返されます。</span><span class="sxs-lookup"><span data-stu-id="57710-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="57710-166">保留中のアクションのクエリ、応答、またはステータスの更新は、SSA から SharePoint コンテンツ ファーム内の SSA に送信され、応答は SSA に返されます。</span><span class="sxs-lookup"><span data-stu-id="57710-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="57710-167">Exchange のアクションまたはステータス要求は、SSA から EWS プロキシに送信されます。EWS プロキシは、Exchange のクエリ操作またはステータス要求を、Exchange 2013 サーバーの Exchange Web Service に送信します。</span><span class="sxs-lookup"><span data-stu-id="57710-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="57710-168">ステータスのクエリまたは応答は、SSA から SSA admin_db に送信され、SSA に返されます。</span><span class="sxs-lookup"><span data-stu-id="57710-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="57710-169">保留中のアクションのクエリまたは応答は、SSA から SSA admin_db に送信され、SSA に返されます。</span><span class="sxs-lookup"><span data-stu-id="57710-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="57710-170">SharePoint 2013 コンテンツ ファーム</span><span class="sxs-lookup"><span data-stu-id="57710-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="57710-171">SharePoint 2013 コンテンツ ファームには、次のコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="57710-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="57710-172">SSA プロキシ</span><span class="sxs-lookup"><span data-stu-id="57710-172">SSA proxy</span></span> 
    
- <span data-ttu-id="57710-173">タイマー ジョブ</span><span class="sxs-lookup"><span data-stu-id="57710-173">Timer job</span></span> 
    
- <span data-ttu-id="57710-174">Contoso SharePoint サイト</span><span class="sxs-lookup"><span data-stu-id="57710-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="57710-175">Contoso SharePoint のコンテンツ</span><span class="sxs-lookup"><span data-stu-id="57710-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="57710-176">SharePoint Services ファームの SSA が SharePoint コンテンツ ファーム内の SSA プロキシにステータス クエリを送信すると、次のアクションが発生します。</span><span class="sxs-lookup"><span data-stu-id="57710-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="57710-177">SharePoint コンテンツ ファームの SSA プロキシは、保留中のアクションに対するクエリまたはステータス応答をタイマー ジョブに送信します。</span><span class="sxs-lookup"><span data-stu-id="57710-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="57710-178">タイマー ジョブは、Contoso の SharePoint コンテンツを確認する Contoso 社の SharePoint サイトに要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="57710-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="57710-179">保留中のアクションまたはステータスのクエリに対する応答は、タイマー ジョブから、SharePoint コンテンツ ファームの SSA のプロキシに送信されてから、SharePoint Services ファームの SSA サービスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="57710-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="57710-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="57710-180">Exchange 2013</span></span>

<span data-ttu-id="57710-181">Exchange 2013 サーバー コンポーネントには、Exchange Web サービスが含まれ、以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="57710-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="57710-182">サーバー間の信頼または Oauth が、SharePoint 2013 2013 コンテンツ ファームと Exchange 2013 の間で処理されます。</span><span class="sxs-lookup"><span data-stu-id="57710-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="57710-183">サーバー間の信頼または Oauth が、Exchange 2013 と Lync 2013 の間で処理されます。</span><span class="sxs-lookup"><span data-stu-id="57710-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="57710-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="57710-184">Lync 2013</span></span>

<span data-ttu-id="57710-185">Lync 2013 コンポーネントは、Exchange 2013 に Lync のコンテンツをアーカイブします。</span><span class="sxs-lookup"><span data-stu-id="57710-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="57710-186">Windows ファイル共有</span><span class="sxs-lookup"><span data-stu-id="57710-186">Windows File Shares</span></span>

<span data-ttu-id="57710-187">Windows ファイル共有コンポーネントは、SharePoint Services ファーム内の SSA にクロールの結果を提供します。</span><span class="sxs-lookup"><span data-stu-id="57710-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="57710-188">凡例</span><span class="sxs-lookup"><span data-stu-id="57710-188">Legend</span></span>

<span data-ttu-id="57710-189">この図の凡例では、次のように異なる色を付けて、コンポーネント間に表された各種のトラフィックをグラフィカルに示しています。</span><span class="sxs-lookup"><span data-stu-id="57710-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="57710-190">水色の線: クエリ/アクション - 電子情報開示のクエリまたはアクションのデータ</span><span class="sxs-lookup"><span data-stu-id="57710-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="57710-191">オレンジ色の線: 電子情報開示の応答 - 電子情報開示のクエリの応答データ</span><span class="sxs-lookup"><span data-stu-id="57710-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="57710-192">緑色の線:ステータス クエリ/応答 - 電子情報開示のステータス クエリまたは応答のデータ</span><span class="sxs-lookup"><span data-stu-id="57710-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="57710-193">紫色の線:Exchange のアクション/ステータス要求 - Exchange トラフィックのアクション状態の電子情報開示要求</span><span class="sxs-lookup"><span data-stu-id="57710-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="57710-194">赤色の線:Exchange データ/ステータス応答 - Exchange からの電子情報開示クエリまたはステータス応答</span><span class="sxs-lookup"><span data-stu-id="57710-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="57710-195">黒い点線:サーバー間の信頼/OAuth</span><span class="sxs-lookup"><span data-stu-id="57710-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="57710-196">黒い実線:クロール/結果</span><span class="sxs-lookup"><span data-stu-id="57710-196">Solid black line: Crawl/results</span></span> 
    

