---
title: "トランザクション履歴データのクラウドへの移動"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: "概要: Contoso 社が SQL Server Stretch Database を実装することで、オンプレミスのデータ ストレージの必要性と毎日の運営コストを縮小した方法を示します。"
ms.openlocfilehash: f1a44a14da49c394974755f7c557013717c4ccef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a><span data-ttu-id="72c77-103">トランザクション履歴データのクラウドへの移動</span><span class="sxs-lookup"><span data-stu-id="72c77-103">Moving historical transaction data to the cloud</span></span>

 <span data-ttu-id="72c77-104">**概要:** Contoso 社が SQL Server Stretch Database を実装することで、オンプレミスのデータ ストレージの必要性と毎日の運営コストを縮小した方法を示します。</span><span class="sxs-lookup"><span data-stu-id="72c77-104">**Summary:** How Contoso implemented SQL Server stretch database to reduce its on-premises data storage needs and daily running costs.</span></span>
  
<span data-ttu-id="72c77-p101">Contoso 社のエンタープライズ ストレージ システムには大量のトランザクション履歴データが保存されています。その内容は、規制要件への準拠に関するデータや、支出の傾向のマーケティング調査と BI 分析に関するデータです。Contoso 社では、磁気テープからアーカイブ済みのデータを復元する必要もありますが、これは時間のかかるプロセスです。Contoso 社のエンタープライズ ストレージ システム内のハードウェアの寿命が近づいており、交換すると非常に高価になります。</span><span class="sxs-lookup"><span data-stu-id="72c77-p101">Contoso's enterprise storage system stores a large amount of historical transaction data for adherence with regulatory requirements and for marketing research and BI analysis of spending trends. Contoso also needs to restore archived data from magnetic tape, a time-intensive process. The hardware in Contoso's enterprise storage system was nearing its end of life and replacing it would be very expensive.</span></span> 
  
<span data-ttu-id="72c77-p102">オンプレミスのデータセンターを縮小するという業務上の必要の一部として、Contoso 社は SQL Server 2016 へのアップグレードを選択しました。その理由は、Stretch Database のハイブリッド機能を使用でき、Azure とシームレスに統合できるからです。Contoso 社で Stretch Database を使用すると、テーブル内のコールド データをオンプレミスからクラウド ストレージに移動して、ローカル ディスク領域を解放したりメンテナンスを縮小したりできます。ホット データとコールド データが両方とも同じテーブル内にあり、アプリケーションとそのユーザーが常に利用可能で、バックアップや復元などのメンテナンスにも常に利用できます。図 1 は、Stretch Database を示しています。</span><span class="sxs-lookup"><span data-stu-id="72c77-p102">As part of its business need to scale down its on-premises datacenters, Contoso chose to upgrade to SQL Server 2016 because of the Stretch Database hybrid feature and its seamless integration with Azure. Stretch Database allows Contoso to move the cold data in its tables from on-premises to cloud storage, freeing up local disk space and reducing maintenance. Both hot and cold data are in the same tables and are always available to applications and their users and for maintenance, such as backups and restores. Figure 1 shows Stretch Database.</span></span>
  
<span data-ttu-id="72c77-112">**図 1:SQL Server Stretch Database**</span><span class="sxs-lookup"><span data-stu-id="72c77-112">**Figure 1: SQL Server Stretch Database**</span></span>

![ハイブリッド データ ソリューションとしての SQL Server Stretch Database](images/Contoso_Poster/StretchDB01.png)
  
<span data-ttu-id="72c77-114">図 1 は、SQL クライアントから SQL Server 2016 を実行しているサーバーに T-SQL クエリを送信し、さらに Azure PaaS 内の Azure SQL Stretch Database に転送する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="72c77-114">Figure 1 shows how a SQL client sends T-SQL queries to a server running SQL Server 2016, which forwards them to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="72c77-115">詳細については、「[Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72c77-115">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
<span data-ttu-id="72c77-116">Contoso 社では、次の手順を使用して、履歴データをクラウドに移動しました。</span><span class="sxs-lookup"><span data-stu-id="72c77-116">Contoso used these steps to move their historical data to the cloud:</span></span>
  
1. <span data-ttu-id="72c77-117">データベースの分析</span><span class="sxs-lookup"><span data-stu-id="72c77-117">Analyze databases</span></span>
    
    <span data-ttu-id="72c77-p103">クラウドに移動しようとしているデータベース内のテーブルの分析を実行し、問題を修正しました。新しい Stretch Database Advisor により、SQL Server 2016 のすべての機能で行えることに関する全概要が示されます。たとえば、クラウドを伸縮するコールド データがどのテーブルにあるかを示す機能があります。</span><span class="sxs-lookup"><span data-stu-id="72c77-p103">Performed an analysis of the tables in the databases that they intended to move to the cloud and fixed any issues. The new Stretch Database Advisor gave them a full overview of what they can expect from all features in SQL Server 2016, including which tables have cold data that could be stretched.</span></span>
    
2. <span data-ttu-id="72c77-120">アップグレード</span><span class="sxs-lookup"><span data-stu-id="72c77-120">Upgrade</span></span>
    
    <span data-ttu-id="72c77-121">パリ本社のデータセンター内の既存の SQL サーバーを SQL Server 2016 に更新しました。</span><span class="sxs-lookup"><span data-stu-id="72c77-121">Updated existing SQL servers in the Paris headquarters datacenter to SQL Server 2016.</span></span>
    
3. <span data-ttu-id="72c77-122">コールド データのクラウドへの移行</span><span class="sxs-lookup"><span data-stu-id="72c77-122">Migrate cold data to the cloud</span></span>
    
    <span data-ttu-id="72c77-p104">SQL Management Studio を使用して、伸縮対象のデータベースと、Azure 内の Stretch Database のインスタンスに移行するテーブルを識別しました。やがてバックグラウンドで、SQL Server 2016 は履歴データを Azure 内の Stretch Database に移動しました。</span><span class="sxs-lookup"><span data-stu-id="72c77-p104">Using SQL Management Studio, they identified the databases to stretch and the tables to migrate to instances of Stretch Database in Azure. Over time and in the background, SQL Server 2016 moved the historical data to stretch databases in Azure.</span></span>
    
<span data-ttu-id="72c77-125">その結果、パリ本社の SQL Server 2016 を実行している 1 つのサーバーは次のように構成されました。</span><span class="sxs-lookup"><span data-stu-id="72c77-125">Here is the resulting configuration for one server running SQL Server 2016 in the Paris headquarters.</span></span>
  
<span data-ttu-id="72c77-126">**図 2:Contoso 社のデータセンター内のサーバーに対する Stretch Database の使用状況**</span><span class="sxs-lookup"><span data-stu-id="72c77-126">**Figure 2: Using Stretch Database for a server in Contoso's datacenter**</span></span>

![SQL Server を実行している 1 台のコンピューター向け Contoso 社の構成 SQL Server Stretch Database](images/Contoso_Poster/StretchDB02.png)

  
<span data-ttu-id="72c77-128">図 2 は、Contoso 社のデータセンター内のアプリケーション サーバーに対するユーザー クエリが、Azure PaaS 内の Azure SQL Stretch Database に渡される SQL クエリになる様子を示しています。</span><span class="sxs-lookup"><span data-stu-id="72c77-128">Figure 2 shows how user queries to an application server in Contoso's datacenter become SQL queries that are passed to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="72c77-p105">ユーザーは既存のアプリとクエリでデータにアクセスします。アクセス ポリシーは変わりません。作業を進める際に、テープのバックアップを取る必要はありません。メンテナンスは、ホット データのバックアップと復元から成ります。</span><span class="sxs-lookup"><span data-stu-id="72c77-p105">Users access the data through existing apps and queries. Access policies remain the same. Moving forward, there is no need for tape backups. Maintenance consists of backing up and restoring hot data.</span></span>
  
<span data-ttu-id="72c77-133">Stretch Database の実装後、Contoso 社は次のような状況になりました。</span><span class="sxs-lookup"><span data-stu-id="72c77-133">After implementing Stretch Database, Contoso:</span></span>
  
- <span data-ttu-id="72c77-134">オンプレミスのデータ ストレージの必要性が 85% 縮小しました。</span><span class="sxs-lookup"><span data-stu-id="72c77-134">Reduced its on-premises data storage needs by 85%.</span></span>
    
- <span data-ttu-id="72c77-135">エンタープライズ ストレージ システムが更新され、磁気テープのアーカイブに依存する必要性がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="72c77-135">Made the update of the enterprise storage system and reliance on magnetic tape archives unnecessary.</span></span>
    
- <span data-ttu-id="72c77-136">毎日の運営コストが大幅に縮小されました。</span><span class="sxs-lookup"><span data-stu-id="72c77-136">Reduced its daily running costs significantly.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="72c77-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="72c77-137">See Also</span></span>

[<span data-ttu-id="72c77-138">Contoso Corporation のエンタープライズのシナリオ</span><span class="sxs-lookup"><span data-stu-id="72c77-138">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="72c77-139">Microsoft Cloud の Contoso</span><span class="sxs-lookup"><span data-stu-id="72c77-139">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="72c77-140">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="72c77-140">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="72c77-141">Stretch Database</span><span class="sxs-lookup"><span data-stu-id="72c77-141">Stretch Database</span></span>](https://msdn.microsoft.com/library/dn935011.aspx)
  
[<span data-ttu-id="72c77-142">Microsoft の Enterprise Cloud ロードマップ:IT の意思決定者向けのリソース</span><span class="sxs-lookup"><span data-stu-id="72c77-142">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




