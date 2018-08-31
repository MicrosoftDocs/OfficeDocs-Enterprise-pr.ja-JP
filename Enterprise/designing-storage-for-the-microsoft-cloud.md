---
title: Microsoft クラウドのストレージを設計する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: '概要: クラウド ストレージが必要な理由を理解し、一連の Microsoft のクラウド ストレージ オプションおよび主要なストレージ シナリオを確認します。'
ms.openlocfilehash: d96992d63115095dd6a1b7277886d0a4bb2bc02f
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915232"
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="b0953-103">Microsoft クラウドのストレージを設計する</span><span class="sxs-lookup"><span data-stu-id="b0953-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="b0953-104">**概要:** クラウド ストレージが必要な理由を理解し、一連の Microsoft のクラウド ストレージ オプションおよび主要なストレージ シナリオを確認します。</span><span class="sxs-lookup"><span data-stu-id="b0953-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="b0953-105">ご使用のストレージを Microsoft のクラウド サービスと統合すると、広範なサービスとクラウド プラットフォームのオプションにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="b0953-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="b0953-106">クラウド ストレージを選ぶ理由</span><span class="sxs-lookup"><span data-stu-id="b0953-106">Why cloud storage?</span></span>

<span data-ttu-id="b0953-107">クラウド ストレージを使用する 2 つの主な理由</span><span class="sxs-lookup"><span data-stu-id="b0953-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="b0953-108">市場投入のスピード：</span><span class="sxs-lookup"><span data-stu-id="b0953-108">Speed to market:</span></span>
    
  - <span data-ttu-id="b0953-109">高可用性および障害復旧のための迅速な構成</span><span class="sxs-lookup"><span data-stu-id="b0953-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="b0953-110">ストレージ ハードウェアの購入が不要</span><span class="sxs-lookup"><span data-stu-id="b0953-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="b0953-111">Microsoft のクラウド製品による組み込みの設備</span><span class="sxs-lookup"><span data-stu-id="b0953-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="b0953-112">世界中どこからでも利用可能</span><span class="sxs-lookup"><span data-stu-id="b0953-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="b0953-113">メンテナンス コストの削減: </span><span class="sxs-lookup"><span data-stu-id="b0953-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="b0953-114">ストレージの需要に応じた柔軟な拡大および縮小</span><span class="sxs-lookup"><span data-stu-id="b0953-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="b0953-115">ストレージ ハードウェアのメンテナンスや移行が不要</span><span class="sxs-lookup"><span data-stu-id="b0953-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="b0953-116">Microsoft はインフラストラクチャのメンテナンスや改善のための組み込みの設備を提供</span><span class="sxs-lookup"><span data-stu-id="b0953-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="b0953-117">継続的な改善による市場で最高のストレージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b0953-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="b0953-118">Microsoft クラウドのストレージ オプション</span><span class="sxs-lookup"><span data-stu-id="b0953-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="b0953-119">さまざまなクラウド ストレージ オプションを理解するために、建設にたとえて表現しています。</span><span class="sxs-lookup"><span data-stu-id="b0953-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="b0953-120">いつでも使用可能</span><span class="sxs-lookup"><span data-stu-id="b0953-120">Move-in ready</span></span>

<span data-ttu-id="b0953-p101">既存のサービスに付属している、事前にパッケージ化された以下のソリューションを使用します。最小限の構成ですぐに使用できます。</span><span class="sxs-lookup"><span data-stu-id="b0953-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="b0953-123">Office 365</span><span class="sxs-lookup"><span data-stu-id="b0953-123">Office 365</span></span>
    
- <span data-ttu-id="b0953-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="b0953-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="b0953-125">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="b0953-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="b0953-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="b0953-126">Dynamics 365</span></span>
    
- <span data-ttu-id="b0953-127">Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="b0953-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="b0953-128">Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="b0953-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="b0953-129">Yammer Site Sharing</span><span class="sxs-lookup"><span data-stu-id="b0953-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="b0953-130">Azure Backup</span><span class="sxs-lookup"><span data-stu-id="b0953-130">Azure Backup</span></span>
    
<span data-ttu-id="b0953-131">各クラウド ストレージ オプションの詳細については、[いつでも使用可能](move-in-ready.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0953-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="b0953-132">いくらかのアセンブリが必要</span><span class="sxs-lookup"><span data-stu-id="b0953-132">Some assembly required</span></span>

<span data-ttu-id="b0953-133">既存のサービスを、カスタム調整用の追加の構成やコーディングを伴うストレージ ソリューションの開始点として使用します。</span><span class="sxs-lookup"><span data-stu-id="b0953-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="b0953-134">Azure Content Delivery Network</span><span class="sxs-lookup"><span data-stu-id="b0953-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="b0953-135">Azure Media Services</span><span class="sxs-lookup"><span data-stu-id="b0953-135">Azure Media Services</span></span>
    
- <span data-ttu-id="b0953-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="b0953-136">HdInsight</span></span>
    
- <span data-ttu-id="b0953-137">Azure Redis Cache</span><span class="sxs-lookup"><span data-stu-id="b0953-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="b0953-138">Azure SQL データベース</span><span class="sxs-lookup"><span data-stu-id="b0953-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="b0953-139">Azure VM 内の SQL Server</span><span class="sxs-lookup"><span data-stu-id="b0953-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="b0953-140">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="b0953-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="b0953-141">StorSimple</span><span class="sxs-lookup"><span data-stu-id="b0953-141">StorSimple</span></span>
    
- <span data-ttu-id="b0953-142">Azure SQL Data Warehouse</span><span class="sxs-lookup"><span data-stu-id="b0953-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="b0953-143">Azure Data Lake Store</span><span class="sxs-lookup"><span data-stu-id="b0953-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="b0953-144">各クラウド ストレージ オプションの詳細については、[いくらかのアセンブリが必要](some-assembly-required.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0953-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="b0953-145">新規に構築</span><span class="sxs-lookup"><span data-stu-id="b0953-145">Build from the ground up</span></span>

<span data-ttu-id="b0953-146">これらのストレージ文書パーツとコードを使用して、独自のストレージ ソリューションまたはアプリを最初から作成します。</span><span class="sxs-lookup"><span data-stu-id="b0953-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="b0953-147">Azure Storage (ファイル)</span><span class="sxs-lookup"><span data-stu-id="b0953-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="b0953-148">Azure Storage (BLOB)</span><span class="sxs-lookup"><span data-stu-id="b0953-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="b0953-149">Azure Storage (キュー)</span><span class="sxs-lookup"><span data-stu-id="b0953-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="b0953-150">Azure Storage (テーブル)</span><span class="sxs-lookup"><span data-stu-id="b0953-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="b0953-151">各クラウド ストレージ オプションの詳細については、[新規に構築](build-from-the-ground-up.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0953-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="b0953-152">キー ストレージのシナリオ</span><span class="sxs-lookup"><span data-stu-id="b0953-152">Key storage scenarios</span></span>

<span data-ttu-id="b0953-153">クラウド ベースのストレージを必要とする主要シナリオは以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b0953-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="b0953-154">データのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="b0953-154">Cache data</span></span>
    
    <span data-ttu-id="b0953-155">高速キャッシュで保存することによって、使用頻度の高いデータへのアクセスを促進します。</span><span class="sxs-lookup"><span data-stu-id="b0953-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="b0953-156">チーム メンバーとの共同作業</span><span class="sxs-lookup"><span data-stu-id="b0953-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="b0953-157">複数のユーザーにクラウド ストレージのデータへアクセス許可を付与します。</span><span class="sxs-lookup"><span data-stu-id="b0953-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="b0953-158">データ管理</span><span class="sxs-lookup"><span data-stu-id="b0953-158">Manage data</span></span>
    
    <span data-ttu-id="b0953-159">内部または外部のバルク データを保存、移動、または削除します。</span><span class="sxs-lookup"><span data-stu-id="b0953-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="b0953-160">ソース コードの管理</span><span class="sxs-lookup"><span data-stu-id="b0953-160">Manage source code</span></span>
    
    <span data-ttu-id="b0953-161">クラウド内のアプリケーション コア ファイルをアップロード、共同作業、および実行します。</span><span class="sxs-lookup"><span data-stu-id="b0953-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="b0953-162">ファイルのバックアップ</span><span class="sxs-lookup"><span data-stu-id="b0953-162">Backup files</span></span>
    
    <span data-ttu-id="b0953-163">複数のクラウドの場所で、内部データまたはオフサイトの外部データのコピーを保存します。</span><span class="sxs-lookup"><span data-stu-id="b0953-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="b0953-164">会社の通信の公開</span><span class="sxs-lookup"><span data-stu-id="b0953-164">Publish company communications</span></span>
    
    <span data-ttu-id="b0953-165">内部または外部メッセージの 1 つの公開ポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="b0953-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="b0953-166">数百万のイベントの配信</span><span class="sxs-lookup"><span data-stu-id="b0953-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="b0953-167">Web サイト、アプリケーション、デバイスからのテレメトリ取り込みのためのストレージを作成します。</span><span class="sxs-lookup"><span data-stu-id="b0953-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="b0953-168">ビデオの管理と提供</span><span class="sxs-lookup"><span data-stu-id="b0953-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="b0953-169">顧客または組織ユーザー向けのビデオ コンテンツを保存し、提供します。</span><span class="sxs-lookup"><span data-stu-id="b0953-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="b0953-170">次の手順</span><span class="sxs-lookup"><span data-stu-id="b0953-170">Next step</span></span>

<span data-ttu-id="b0953-171">[いつでも使用可能](move-in-ready.md) クラウド ストレージ オプションを確認します。</span><span class="sxs-lookup"><span data-stu-id="b0953-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b0953-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0953-172">See Also</span></span>

[<span data-ttu-id="b0953-173">エンタープライズ アーキテクトのための Microsoft クラウド ストレージ</span><span class="sxs-lookup"><span data-stu-id="b0953-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="b0953-174">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="b0953-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="b0953-175">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span><span class="sxs-lookup"><span data-stu-id="b0953-175">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


