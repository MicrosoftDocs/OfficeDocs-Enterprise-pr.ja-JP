---
title: "新規に構築"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "概要: は、クラウドの設定の詳細については独自のストレージ ・ サービスやソリューションの作成に使用できるストレージ構成要素を取得します。"
ms.openlocfilehash: eabf38e0ccef3335b2d198a33f5622d0d449589a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="build-from-the-ground-up"></a><span data-ttu-id="531ed-103">新規に構築</span><span class="sxs-lookup"><span data-stu-id="531ed-103">Build from the ground up</span></span>

 <span data-ttu-id="531ed-104">**の概要:**クラウドの設定の詳細については独自のストレージ ・ サービスやソリューションの作成に使用できるストレージ構成要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="531ed-104">**Summary:** Get the details on the set of cloud storage building blocks that you can use to create your own storage service or solution.</span></span>
  
<span data-ttu-id="531ed-105">"新規に構築" ストレージ ソリューション:</span><span class="sxs-lookup"><span data-stu-id="531ed-105">"Build from the ground up" storage solutions:</span></span>
  
- <span data-ttu-id="531ed-106">独自のストレージ ・ ソリューションを最初から作成すること。</span><span class="sxs-lookup"><span data-stu-id="531ed-106">Allow you to create your own storage solution from scratch.</span></span> 
    
- <span data-ttu-id="531ed-107">REST Api を使用してプログラミングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="531ed-107">Requires programming using the REST APIs.</span></span>
    
- <span data-ttu-id="531ed-108">究極のカスタマイズと柔軟性を提供します。</span><span class="sxs-lookup"><span data-stu-id="531ed-108">Provide the ultimate in customization and flexibility.</span></span>
    
<span data-ttu-id="531ed-109">次のセクションでは、"新規に構築" ストレージのそれぞれのオプションの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="531ed-109">The following sections describe the details of each "Build from the ground up" storage option.</span></span>
  
## <a name="azure-storage-files"></a><span data-ttu-id="531ed-110">Azure Storage (ファイル)</span><span class="sxs-lookup"><span data-stu-id="531ed-110">Azure Storage (files)</span></span>

### <a name="features"></a><span data-ttu-id="531ed-111">機能</span><span class="sxs-lookup"><span data-stu-id="531ed-111">Features</span></span>

- <span data-ttu-id="531ed-112">レガシ アプリケーションからクラウドへの移行を促進</span><span class="sxs-lookup"><span data-stu-id="531ed-112">Makes it easier to move legacy applications to the cloud</span></span>
    
- <span data-ttu-id="531ed-113">新しいアプリケーション向けに BLOB ストレージを推奨</span><span class="sxs-lookup"><span data-stu-id="531ed-113">Blob storage preferred for new applications</span></span>
    
- <span data-ttu-id="531ed-114">Azure 仮想マシンからマウントが可能</span><span class="sxs-lookup"><span data-stu-id="531ed-114">Can mount from an Azure virtual machine</span></span>
    
- <span data-ttu-id="531ed-115">SMB 3.0 でオンプレミスでのマウントが可能</span><span class="sxs-lookup"><span data-stu-id="531ed-115">Can mount on-premises with SMB 3.0</span></span>
    
- <span data-ttu-id="531ed-116">Linux および Windows で動作</span><span class="sxs-lookup"><span data-stu-id="531ed-116">Works with Linux and Windows</span></span>
    
- <span data-ttu-id="531ed-117">Azure AD ベースの認証または (Azure ストレージ アカウント キーは、認証およびファイル共有へのアクセスの認証を提供) の Acl をサポートしていません</span><span class="sxs-lookup"><span data-stu-id="531ed-117">Doesn't support Azure AD-based authentication or ACLs (Azure Storage account keys provide authentication and authorized access to the file share)</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="531ed-118">一般的な使用目的</span><span class="sxs-lookup"><span data-stu-id="531ed-118">Common uses</span></span>

- <span data-ttu-id="531ed-119">ファイル共有に依存しているレガシ アプリケーションのクラウドへの移行</span><span class="sxs-lookup"><span data-stu-id="531ed-119">Migrating legacy applications to the cloud that rely on file shares</span></span>
    
- <span data-ttu-id="531ed-120">開発およびテスト ツールの共有</span><span class="sxs-lookup"><span data-stu-id="531ed-120">Share development and testing tools</span></span>
    
- <span data-ttu-id="531ed-121">分散アプリではログ、診断データ、クラッシュ ダンプの保存が可能</span><span class="sxs-lookup"><span data-stu-id="531ed-121">Distributed apps can store logs, diagnostic data, and crash dumps</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="531ed-122">キー ストレージのシナリオ</span><span class="sxs-lookup"><span data-stu-id="531ed-122">Key storage scenarios</span></span>

- <span data-ttu-id="531ed-123">ファイルのバックアップ</span><span class="sxs-lookup"><span data-stu-id="531ed-123">Backup files</span></span>
    
### <a name="resources"></a><span data-ttu-id="531ed-124">リソース</span><span class="sxs-lookup"><span data-stu-id="531ed-124">Resources</span></span>

<span data-ttu-id="531ed-125">追加情報については、[こちら](https://msdn.microsoft.com/library/azure/dn166972.aspx)をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="531ed-125">For additional information, click [here](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span></span>
  
<span data-ttu-id="531ed-126">コストの情報については、[こちら](http://azure.microsoft.com/pricing/details/storage/)をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="531ed-126">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-blobs"></a><span data-ttu-id="531ed-127">Azure Storage (BLOB)</span><span class="sxs-lookup"><span data-stu-id="531ed-127">Azure Storage (blobs)</span></span>

### <a name="features"></a><span data-ttu-id="531ed-128">機能</span><span class="sxs-lookup"><span data-stu-id="531ed-128">Features</span></span>

- <span data-ttu-id="531ed-129">各ストレージ アカウントは、最大で 500 TB を保持できます (1 つのサブスクリプションは、複数のストレージ アカウントを持つことができます)</span><span class="sxs-lookup"><span data-stu-id="531ed-129">Each storage account can hold up to 500 TB (one subscription can have multiple storage accounts)</span></span>
    
- <span data-ttu-id="531ed-130">ストレージ アカウントはストレージに構成され、そこでセキュリティを適用し、BLOB を含めることが可能</span><span class="sxs-lookup"><span data-stu-id="531ed-130">Storage accounts are organized into containers, which can have security applied to them and can contain blobs</span></span>
    
- <span data-ttu-id="531ed-131">ブロック BLOB は、200 GB までのクラウド オブジェクトのストリーミングと保管のために最適化済み</span><span class="sxs-lookup"><span data-stu-id="531ed-131">Block blobs are optimized for streaming and storing cloud objects, up to 200 GB in size</span></span>
    
- <span data-ttu-id="531ed-132">ページ BLOB は、1 TB までの PaaS ディスクの表示とランダム書き込みのサポートのために最適化済み</span><span class="sxs-lookup"><span data-stu-id="531ed-132">Page blobs are optimized for representing PaaS disks and supporting random writes, up to 1 TB in size</span></span>
    
- <span data-ttu-id="531ed-133">BLOB の追加は 195 GB までの追加操作のために最適化済み</span><span class="sxs-lookup"><span data-stu-id="531ed-133">Append blobs are optimized for append operations, up to 195 GB</span></span>
    
- <span data-ttu-id="531ed-134">Premium Storage は SSD ストレージによる高速 IOPS を提供</span><span class="sxs-lookup"><span data-stu-id="531ed-134">Premium Storage provides faster IOPS through SSD storage</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="531ed-135">一般的な使用目的</span><span class="sxs-lookup"><span data-stu-id="531ed-135">Common uses</span></span>

- <span data-ttu-id="531ed-136">Web アプリケーションのファイル、コンピューター、データベース、およびデバイスのイメージとテキストのバックアップ</span><span class="sxs-lookup"><span data-stu-id="531ed-136">Backups of files, computers, databases, and devices Images and text for web applications</span></span>
    
- <span data-ttu-id="531ed-137">クラウド アプリケーションの構成データ</span><span class="sxs-lookup"><span data-stu-id="531ed-137">Configuration data for cloud applications</span></span>
    
- <span data-ttu-id="531ed-138">ログやその他の大規模なデータセットなどのビッグ データ</span><span class="sxs-lookup"><span data-stu-id="531ed-138">Big data, such as logs and other large datasets</span></span>
    
- <span data-ttu-id="531ed-139">Azure では、HDInsight や仮想マシン ディスクなど、独自のサービスに BLOG ストレージを使用</span><span class="sxs-lookup"><span data-stu-id="531ed-139">Azure uses blob storage for its own services, such as HDInsight and virtual machine disks</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="531ed-140">キー ストレージのシナリオ</span><span class="sxs-lookup"><span data-stu-id="531ed-140">Key storage scenarios</span></span>

- <span data-ttu-id="531ed-141">データ管理</span><span class="sxs-lookup"><span data-stu-id="531ed-141">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="531ed-142">リソース</span><span class="sxs-lookup"><span data-stu-id="531ed-142">Resources</span></span>

<span data-ttu-id="531ed-143">追加情報については、[こちら](https://msdn.microsoft.com/library/azure/dd179376.aspx)をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="531ed-143">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span></span>
  
<span data-ttu-id="531ed-144">コストの情報については、[こちら](http://azure.microsoft.com/pricing/details/storage/)をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="531ed-144">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-queues"></a><span data-ttu-id="531ed-145">Azure Storage (キュー)</span><span class="sxs-lookup"><span data-stu-id="531ed-145">Azure Storage (queues)</span></span>

### <a name="features"></a><span data-ttu-id="531ed-146">機能</span><span class="sxs-lookup"><span data-stu-id="531ed-146">Features</span></span>

- <span data-ttu-id="531ed-147">ストレージ アカウントには任意の数のキューの登録が可能</span><span class="sxs-lookup"><span data-stu-id="531ed-147">Storage account can contain any number of queues</span></span>
    
- <span data-ttu-id="531ed-148">キューには任意の数のメッセージの登録が可能 (ストレージ アカウントの限界まで)</span><span class="sxs-lookup"><span data-stu-id="531ed-148">Queue can contain any number of messages (until the storage account is full)</span></span>
    
- <span data-ttu-id="531ed-149">キュー メッセージはアプリケーションによって取得または削除されない場合、7 日後に自動的に削除される</span><span class="sxs-lookup"><span data-stu-id="531ed-149">Queue messages are automatically deleted after seven days if not retrieved and deleted by an application</span></span>
    
- <span data-ttu-id="531ed-150">メッセージ サイズは 64 KB まで</span><span class="sxs-lookup"><span data-stu-id="531ed-150">Messages may be up to 64 KB in size</span></span>
    
- <span data-ttu-id="531ed-151">ストレージ アカウント レベルのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="531ed-151">Secured at storage account level</span></span>
    
- <span data-ttu-id="531ed-152">キューは生データではなく、コントロール メッセージを渡すために使用</span><span class="sxs-lookup"><span data-stu-id="531ed-152">Queues are intended to pass control messages, not raw data</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="531ed-153">一般的な使用目的</span><span class="sxs-lookup"><span data-stu-id="531ed-153">Common uses</span></span>

- <span data-ttu-id="531ed-154">非同期で処理する作業のバックログを作成</span><span class="sxs-lookup"><span data-stu-id="531ed-154">Create a backlog of work to process asynchronously</span></span>
    
- <span data-ttu-id="531ed-155">ログ メッセージの処理</span><span class="sxs-lookup"><span data-stu-id="531ed-155">Processing log messages</span></span>
    
- <span data-ttu-id="531ed-156">アプリケーションの切り離し</span><span class="sxs-lookup"><span data-stu-id="531ed-156">Decouple applications</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="531ed-157">キー ストレージのシナリオ</span><span class="sxs-lookup"><span data-stu-id="531ed-157">Key storage scenarios</span></span>

- <span data-ttu-id="531ed-158">イベント配信</span><span class="sxs-lookup"><span data-stu-id="531ed-158">Distribute events</span></span>
    
### <a name="resources"></a><span data-ttu-id="531ed-159">リソース</span><span class="sxs-lookup"><span data-stu-id="531ed-159">Resources</span></span>

<span data-ttu-id="531ed-160">追加情報については、[こちら](https://msdn.microsoft.com/library/azure/dd179353.aspx)をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="531ed-160">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span></span>
  
<span data-ttu-id="531ed-161">コストの情報については、[こちら](http://azure.microsoft.com/pricing/details/storage/)をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="531ed-161">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-tables"></a><span data-ttu-id="531ed-162">Azure Storage (テーブル)</span><span class="sxs-lookup"><span data-stu-id="531ed-162">Azure Storage (tables)</span></span>

### <a name="features"></a><span data-ttu-id="531ed-163">機能</span><span class="sxs-lookup"><span data-stu-id="531ed-163">Features</span></span>

- <span data-ttu-id="531ed-164">半構造化データセットに最適</span><span class="sxs-lookup"><span data-stu-id="531ed-164">Best for semi-structured datasets</span></span>
    
- <span data-ttu-id="531ed-165">一般的に、従来の SQL より低コスト</span><span class="sxs-lookup"><span data-stu-id="531ed-165">Typically lower cost than traditional SQL</span></span>
    
- <span data-ttu-id="531ed-166">値のクエリを実行する場合に低速のキー、クエリを実行する場合に非常に高速</span><span class="sxs-lookup"><span data-stu-id="531ed-166">Very fast if querying for key, slow if querying for value</span></span>
    
- <span data-ttu-id="531ed-167">ストレージ アカウントの上限まで、テーブル数を大規模に拡張可能</span><span class="sxs-lookup"><span data-stu-id="531ed-167">Massively scalable; any amount of tables up to the limits of the storage account</span></span>
    
- <span data-ttu-id="531ed-168">REST API、限定された oData プロトコル、.NET を介してアクセス可能</span><span class="sxs-lookup"><span data-stu-id="531ed-168">Accessible through REST API, limited oData protocol, .NET</span></span>
    
- <span data-ttu-id="531ed-169">値はシリアル化する必要あり</span><span class="sxs-lookup"><span data-stu-id="531ed-169">Values must be serialized</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="531ed-170">一般的な使用目的</span><span class="sxs-lookup"><span data-stu-id="531ed-170">Common uses</span></span>

- <span data-ttu-id="531ed-171">Web アプリケーションのユーザー データ</span><span class="sxs-lookup"><span data-stu-id="531ed-171">User data for web applications</span></span>
    
- <span data-ttu-id="531ed-172">アドレス帳</span><span class="sxs-lookup"><span data-stu-id="531ed-172">Address books</span></span>
    
- <span data-ttu-id="531ed-173">デバイス情報</span><span class="sxs-lookup"><span data-stu-id="531ed-173">Device information</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="531ed-174">キー ストレージのシナリオ</span><span class="sxs-lookup"><span data-stu-id="531ed-174">Key storage scenarios</span></span>

- <span data-ttu-id="531ed-175">データ管理</span><span class="sxs-lookup"><span data-stu-id="531ed-175">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="531ed-176">リソース</span><span class="sxs-lookup"><span data-stu-id="531ed-176">Resources</span></span>

<span data-ttu-id="531ed-177">追加情報については、[こちら](https://msdn.microsoft.com/library/azure/dd179463.aspx)をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="531ed-177">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span></span>
  
<span data-ttu-id="531ed-178">コストの情報については、[こちら](http://azure.microsoft.com/pricing/details/storage/)をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="531ed-178">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="microsoft-azure-storage-recommendations"></a><span data-ttu-id="531ed-179">Microsoft Azure Storage の推奨事項</span><span class="sxs-lookup"><span data-stu-id="531ed-179">Microsoft Azure Storage recommendations</span></span>

<span data-ttu-id="531ed-180">Azure Storage を使用してカスタム ストレージ ソリューションを設計するときは、以下の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="531ed-180">When designing your custom storage solution with Azure Storage, keep the following in mind:</span></span>
  
- <span data-ttu-id="531ed-181">複数のストレージ アカウントを利用して、サイズ増加 (100 TB 以上) またはスループット向上 (1 秒あたり 5,000 以上の操作) に対応する拡張性を実現。</span><span class="sxs-lookup"><span data-stu-id="531ed-181">Leverage multiple storage accounts for greater scalability, either for increased size (> 100 TB) or for more throughput (> 5,000 operations per second).</span></span>
    
- <span data-ttu-id="531ed-182">コード変更ではなく、構成変更によるストレージ アカウントの追加を可能にする設計。</span><span class="sxs-lookup"><span data-stu-id="531ed-182">Design the ability for adding additional storage accounts as a configuration change, not as a code change.</span></span>
    
- <span data-ttu-id="531ed-183">テーブル ストレージのパーティショニング機能を慎重に選択し、挿入とクエリのパフォーマンスの面から必要な拡張を実現。</span><span class="sxs-lookup"><span data-stu-id="531ed-183">Carefully select partitioning functions for table storage to enable the desired scale in terms of insert and query performance.</span></span>
    
- <span data-ttu-id="531ed-184">メタデータ (プロパティ名) がインバンドに保存されるため、テーブル プロパティの短い形式の列名を選択 (列名も 1 MB の行サイズ制限に計上される)。</span><span class="sxs-lookup"><span data-stu-id="531ed-184">Choose short column names for table properties as the metadata (property names) are stored in-band (the column names also count towards the maximum row size of 1 MB).</span></span>
    
- <span data-ttu-id="531ed-185">可能な場合は、バッチ操作もストレージに格納。</span><span class="sxs-lookup"><span data-stu-id="531ed-185">When possible, batch operations into storage.</span></span>
    
- <span data-ttu-id="531ed-186">構成データベースのキャッシュ情報を積極的に分散キャッシュに格納。</span><span class="sxs-lookup"><span data-stu-id="531ed-186">Aggressively cache information in the configuration database into a distributed cache.</span></span>
    
- <span data-ttu-id="531ed-187">アプリケーションのパフォーマンスや信頼性が、キャッシュ内で利用できる特定のデータ セグメントに依存している場合、キャッシュにデータが入れられるまで、アプリケーションは着信要求を拒否する必要がある。</span><span class="sxs-lookup"><span data-stu-id="531ed-187">If application performance or reliability is dependent on having a certain segment of data available in the cache, your application should refuse incoming requests until the cache has been pre-populated.</span></span>
    
- <span data-ttu-id="531ed-188">データを垂直 (テーブル単位) または水平 (複数のシャードにおよぶセグメント テーブル) に分割し、負荷を複数のデータベースに分散。</span><span class="sxs-lookup"><span data-stu-id="531ed-188">Partition the data in either vertically (by table) or horizontally (segment table across multiple shards) to spread the load across multiple databases.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="531ed-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="531ed-189">See Also</span></span>

[<span data-ttu-id="531ed-190">エンタープライズ アーキテクトのための Microsoft クラウド ストレージ</span><span class="sxs-lookup"><span data-stu-id="531ed-190">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="531ed-191">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="531ed-191">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="531ed-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span><span class="sxs-lookup"><span data-stu-id="531ed-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



