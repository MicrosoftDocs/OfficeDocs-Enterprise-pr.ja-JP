---
title: SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 5/14/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Office 365 コンテンツ配信ネットワーク (CDN) を使用して、自分の場所やコンテンツへのアクセス方法に関係なく、すべてのユーザーに対して SharePoint Online アセットの配信を高速化する方法について説明します。
ms.openlocfilehash: ffb464b31a5f5a87a09334e2c5f7ae3c3027af65
ms.sourcegitcommit: 77a25920511c54d7d613f552bdff7ad14cdd8324
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "36385195"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a><span data-ttu-id="20269-103">SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用</span><span class="sxs-lookup"><span data-stu-id="20269-103">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>

<span data-ttu-id="20269-104">組み込みの Office 365 コンテンツ配信ネットワーク (CDN) を使用して静的資産をホストすることで、SharePoint Online ページのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="20269-104">You can use the built-in Office 365 Content Delivery Network (CDN) to host static assets to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="20269-105">Office 365 CDN では、静的資産を要求しているブラウザーの近くに静的資産をキャッシュするとパフォーマンスが向上します。これにより、ダウンロードが速くなり、待ち時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="20269-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="20269-106">また、Office 365 CDN は、強化された圧縮と HTTP パイプライン処理に[http/2 プロトコル](https://en.wikipedia.org/wiki/HTTP/2)を使用します。</span><span class="sxs-lookup"><span data-stu-id="20269-106">Also, the Office 365 CDN uses the [HTTP/2 protocol](https://en.wikipedia.org/wiki/HTTP/2) for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="20269-107">Office 365 CDN サービスは、SharePoint Online サブスクリプションの一部として含まれます。</span><span class="sxs-lookup"><span data-stu-id="20269-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

> [!NOTE]
> <span data-ttu-id="20269-108">Office 365 CDN を使用する場合の制限事項:</span><span class="sxs-lookup"><span data-stu-id="20269-108">Restrictions for use of the Office 365 CDN:</span></span>
> + <span data-ttu-id="20269-109">Office 365 CDN は、**運用環境**(世界規模) のクラウドのテナントでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="20269-109">The Office 365 CDN is only available to tenants in the **Production** (worldwide) cloud.</span></span> <span data-ttu-id="20269-110">米国政府機関のテナント、中国およびドイツのクラウドでは、現在 Office 365 CDN をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="20269-110">Tenants in the US Government, China and Germany clouds do not currently support the Office 365 CDN.</span></span>
> + <span data-ttu-id="20269-111">Office 365 CDN は、現在、カスタムまたは "バニティ" ドメインで構成されているテナントをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="20269-111">The Office 365 CDN does not currently support tenants configured with custom or "vanity" domains.</span></span> <span data-ttu-id="20269-112">「[ドメインを 365 office に追加](https://docs.microsoft.com/en-us/office365/admin/setup/add-domain?view=o365-worldwide)する」の手順に従って office 365 テナントのコンポーネントにドメインを追加した場合、cdn からコンテンツにアクセスしようとすると、OFFICE 365 CDN によってエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="20269-112">If you have added a domain to any component in your Office 365 tenant using the instructions in the topic [Add a domain to Office 365](https://docs.microsoft.com/en-us/office365/admin/setup/add-domain?view=o365-worldwide), the Office 365 CDN will return errors when you try to access content from the CDN.</span></span>

<span data-ttu-id="20269-113">Office 365 CDN は静的資産を複数の場所 _(元の場所)_ でホストできる複数の CDN で構成されているため、静的資産をグローバルな高速ネットワークから提供することができます。</span><span class="sxs-lookup"><span data-stu-id="20269-113">The Office 365 CDN is composed of multiple CDNs that allow you to host static assets in multiple locations, or _origins_, and serve them from global high-speed networks.</span></span> <span data-ttu-id="20269-114">Office 365 CDN でホストするコンテンツの種類に応じて、**公開**、**非公開**、またはその両方の元の場所を追加できます。</span><span class="sxs-lookup"><span data-stu-id="20269-114">Depending on the kind of content you want to host in the Office 365 CDN, you can add **public** origins, **private** origins or both.</span></span> <span data-ttu-id="20269-115">パブリックとプライベートオリジンの違いに関する詳細については、[各配信元がパブリックかプライベートかを選択](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)するを参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-115">See [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) for more information on the difference between public and private origins.</span></span>

<span data-ttu-id="20269-116">![Office 365 CDN の概念図](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN の概念図")</span><span class="sxs-lookup"><span data-stu-id="20269-116">![Office 365 CDN conceptual diagram](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN conceptual diagram")</span></span>

<span data-ttu-id="20269-117">CDNs のしくみに精通している場合は、テナントに対して Office 365 CDN を有効にするための手順をいくつか実行するだけで十分です。</span><span class="sxs-lookup"><span data-stu-id="20269-117">If you are already familiar with the way that CDNs work, you only need to complete a few steps to enable the Office 365 CDN for your tenant.</span></span> <span data-ttu-id="20269-118">このトピックでは、その方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="20269-118">This topic describes how.</span></span> <span data-ttu-id="20269-119">静的アセットのホスティングを開始する方法については、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-119">Read on for information about how to get started hosting your static assets.</span></span>

> [!TIP]
> <span data-ttu-id="20269-120">特別な使用シナリオで Office 365 と共に使用できるその他の Microsoft ホストされた CDNs がありますが、このトピックでは Office 365 CDN の範囲外にあるため、このトピックでは説明していません。</span><span class="sxs-lookup"><span data-stu-id="20269-120">There are other Microsoft-hosted CDNs that can be used with Office 365 for specialized usage scenarios, but are not discussed in this topic because they fall outside the scope of the Office 365 CDN.</span></span> <span data-ttu-id="20269-121">詳細については、「[その他の Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-121">For more information, see [Other Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns).</span></span>

 <span data-ttu-id="20269-122">**[Office 365 のネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)に戻ります。**</span><span class="sxs-lookup"><span data-stu-id="20269-122">**Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).**</span></span>

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a><span data-ttu-id="20269-123">SharePoint Online での Office 365 CDN の使用の概要</span><span class="sxs-lookup"><span data-stu-id="20269-123">Overview of working with the Office 365 CDN in SharePoint Online</span></span>

<span data-ttu-id="20269-124">組織で Office 365 CDN をセットアップするには、次の基本的な手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="20269-124">To set up the Office 365 CDN for your organization, you follow these basic steps:</span></span>

- [<span data-ttu-id="20269-125">Office 365 CDN の展開を計画する</span><span class="sxs-lookup"><span data-stu-id="20269-125">Plan for deployment of the Office 365 CDN</span></span>](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  - <span data-ttu-id="20269-126">[CDN でホストする静的アセットを決定](use-office-365-cdn-with-spo.md#CDNAssets)します。</span><span class="sxs-lookup"><span data-stu-id="20269-126">[Determine which static assets you want to host on the CDN](use-office-365-cdn-with-spo.md#CDNAssets).</span></span>
  - <span data-ttu-id="20269-127">[アセットを格納する場所を決定](use-office-365-cdn-with-spo.md#CDNStoreAssets)します。</span><span class="sxs-lookup"><span data-stu-id="20269-127">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span></span> <span data-ttu-id="20269-128">この場所は SharePoint サイト、ライブラリ、またはフォルダーで、_元_の名前と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="20269-128">This location can be a SharePoint site, library or folder and is called an _origin_.</span></span>
  - <span data-ttu-id="20269-129">[各配信元をパブリックまたはプライベートにする必要があるかどうかを選択し](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)ます。</span><span class="sxs-lookup"><span data-stu-id="20269-129">[Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span> <span data-ttu-id="20269-130">パブリックとプライベートの両方の種類のオリジンを複数追加できます。</span><span class="sxs-lookup"><span data-stu-id="20269-130">You can add multiple origins of both public and private types.</span></span>

- <span data-ttu-id="20269-131">PowerShell または SharePoint Online CLI のいずれかを使用して CDN をセットアップおよび構成する</span><span class="sxs-lookup"><span data-stu-id="20269-131">Set up and configure the CDN, using either PowerShell or the SharePoint Online CLI</span></span>

  - [<span data-ttu-id="20269-132">SharePoint Online 管理シェルを使用して CDN を設定および構成する</span><span class="sxs-lookup"><span data-stu-id="20269-132">Set up and configure the CDN by using the SharePoint Online Management Shell</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  - [<span data-ttu-id="20269-133">Office 365 CLI を使用して CDN をセットアップおよび構成する</span><span class="sxs-lookup"><span data-stu-id="20269-133">Set up and configure the CDN by using the Office 365 CLI</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  <span data-ttu-id="20269-134">この手順を完了すると、次のことができます。</span><span class="sxs-lookup"><span data-stu-id="20269-134">When you complete this step, you will have:</span></span>

  - <span data-ttu-id="20269-135">組織の CDN を有効にしました。</span><span class="sxs-lookup"><span data-stu-id="20269-135">Enabled the CDN for your organization.</span></span>
  - <span data-ttu-id="20269-136">オリジンを追加し、各オリジンをパブリックまたはプライベートとして識別しました。</span><span class="sxs-lookup"><span data-stu-id="20269-136">Added your origins, identifying each origin as public or private.</span></span>

<span data-ttu-id="20269-137">セットアップが完了したら、次の方法で、時間の経過と共に[Office 365 CDN を管理](use-office-365-cdn-with-spo.md#CDNManage)できます。</span><span class="sxs-lookup"><span data-stu-id="20269-137">Once you're done with setup, you can [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span>
  
- <span data-ttu-id="20269-138">アセットの追加、更新、および削除</span><span class="sxs-lookup"><span data-stu-id="20269-138">Adding, updating, and removing assets</span></span>
- <span data-ttu-id="20269-139">オリジンを追加および削除する</span><span class="sxs-lookup"><span data-stu-id="20269-139">Adding and removing origins</span></span>
- <span data-ttu-id="20269-140">CDN ポリシーを構成する</span><span class="sxs-lookup"><span data-stu-id="20269-140">Configuring CDN policies</span></span>
- <span data-ttu-id="20269-141">必要に応じて、CDN を無効にする</span><span class="sxs-lookup"><span data-stu-id="20269-141">If necessary, disabling the CDN</span></span>

<span data-ttu-id="20269-142">最後に、「 [cdn アセットを使用](use-office-365-cdn-with-spo.md#using-your-cdn-assets)して、パブリックとプライベートの両方から cdn アセットにアクセスする方法について知る」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-142">Finally, see [Using your CDN assets](use-office-365-cdn-with-spo.md#using-your-cdn-assets) to learn about accessing your CDN assets from both public and private origins.</span></span>

<span data-ttu-id="20269-143">一般的な問題の解決に関するガイダンスについて[は、「Office 365 CDN のトラブルシューティング](use-office-365-cdn-with-spo.md#CDNTroubleshooting)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-143">See [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) for guidance on resolving common issues.</span></span>

## <a name="plan-for-deployment-of-the-office-365-cdn"></a><span data-ttu-id="20269-144">Office 365 CDN の展開を計画する</span><span class="sxs-lookup"><span data-stu-id="20269-144">Plan for deployment of the Office 365 CDN</span></span>

<span data-ttu-id="20269-145">Office 365 テナントの Office 365 CDN を展開する前に、計画プロセスの一部として、以下の要因を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20269-145">Before you deploy the Office 365 CDN for your Office 365 tenant, you should consider the following factors as part of your planning process.</span></span>

  - [<span data-ttu-id="20269-146">CDN でホストする静的アセットを決定する</span><span class="sxs-lookup"><span data-stu-id="20269-146">Determine which static assets you want to host on the CDN</span></span>](use-office-365-cdn-with-spo.md#CDNAssets)
  - [<span data-ttu-id="20269-147">アセットを格納する場所を決定する</span><span class="sxs-lookup"><span data-stu-id="20269-147">Determine where you want to store your assets</span></span>](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  - [<span data-ttu-id="20269-148">各配信元をパブリックまたはプライベートにする必要があるかどうかを選択する</span><span class="sxs-lookup"><span data-stu-id="20269-148">Choose whether each origin should be public or private</span></span>](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a><span data-ttu-id="20269-149">CDN でホストする静的アセットを決定する</span><span class="sxs-lookup"><span data-stu-id="20269-149">Determine which static assets you want to host on the CDN</span></span>
<span data-ttu-id="20269-150"><a name="CDNAssets"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-150"></span></span>

<span data-ttu-id="20269-151">通常、CDNs は_静的アセット_のホスティングや、頻繁に変更されないアセットに最も効果的です。</span><span class="sxs-lookup"><span data-stu-id="20269-151">In general, CDNs are most effective for hosting _static assets_, or assets that don't change very often.</span></span> <span data-ttu-id="20269-152">目安として、これらの条件の一部またはすべてを満たすファイルを特定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="20269-152">A good rule of thumb is to identify files that meet some or all of these conditions:</span></span>

- <span data-ttu-id="20269-153">ページの読み込み時間に大きな影響を与える可能性があるページ (スクリプトや画像など) に埋め込まれる静的ファイル</span><span class="sxs-lookup"><span data-stu-id="20269-153">Static files embedded in a page (like scripts and images) that may have a significant incremental impact on page load times</span></span>
- <span data-ttu-id="20269-154">実行可能ファイルやインストールファイルなどの大きなファイル</span><span class="sxs-lookup"><span data-stu-id="20269-154">Large files like executables and installation files</span></span>
- <span data-ttu-id="20269-155">ストリーミングメディアファイル</span><span class="sxs-lookup"><span data-stu-id="20269-155">Streaming media files</span></span>
- <span data-ttu-id="20269-156">クライアント側のコードをサポートするリソースライブラリ</span><span class="sxs-lookup"><span data-stu-id="20269-156">Resource libraries that support client-side code</span></span>

<span data-ttu-id="20269-157">たとえば、サイトの画像やスクリプトなど繰り返し要求された小さいファイルは、サイトのレンダリングパフォーマンスを大幅に向上させ、CDN の配信元に追加するときに、SharePoint Online サイトの負荷を徐々に軽減できます。</span><span class="sxs-lookup"><span data-stu-id="20269-157">For example, small files that are repeatedly requested like site images and scripts can significantly improve site rendering performance and incrementally reduce the load on your SharePoint Online sites when you add them to a CDN origin.</span></span> <span data-ttu-id="20269-158">インストールの実行可能ファイル、ビデオファイルなどの大規模なファイルは、CDN からダウンロードまたはストリーム転送することができます。これにより、頻繁にアクセスされていない場合でも、SharePoint Online サイトの負荷が大幅に低下します。</span><span class="sxs-lookup"><span data-stu-id="20269-158">Larger files such as installation executables or video files can be downloaded or streamed from the CDN, delivering a positive performance impact and subsequent reduction of the load on your SharePoint Online site, even if they are not accessed as often.</span></span>

<span data-ttu-id="20269-159">ファイル単位でのパフォーマンスの向上は、最も近い CDN エンドポイントへのクライアントの近接度、ローカルネットワーク上の一時的な状態など、多くの要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="20269-159">Performance improvement on a per-file basis is dependent on many factors, including the client's proximity to the nearest CDN endpoint, transient conditions on the local network, and so forth.</span></span> <span data-ttu-id="20269-160">多くの静的ファイルは非常に小さく、Office 365 からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="20269-160">Many static files are quite small, and can be downloaded from Office 365 in less than a second.</span></span> <span data-ttu-id="20269-161">ただし、web ページには、ダウンロード時間が数秒になる多くの埋め込みファイルが含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="20269-161">However, a web page may contain many embedded files with a cumulative download time of several seconds.</span></span> <span data-ttu-id="20269-162">これらのファイルを CDN から処理することにより、ページ全体の読み込み時間が大幅に短縮されます。</span><span class="sxs-lookup"><span data-stu-id="20269-162">Serving these files from the CDN can significantly reduce the overall page load time.</span></span> <span data-ttu-id="20269-163">CDN で提供される[パフォーマンスの向上](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide)については、例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-163">See [What performance gains does a CDN provide?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) for an example.</span></span>

### <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="20269-164">アセットを格納する場所を決定する</span><span class="sxs-lookup"><span data-stu-id="20269-164">Determine where you want to store your assets</span></span>
<span data-ttu-id="20269-165"><a name="CDNStoreAssets"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-165"></span></span>

<span data-ttu-id="20269-166">CDN は、_送信元_と呼ばれる場所からアセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="20269-166">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="20269-167">起点として、URL でアクセスできる SharePoint サイト、ドキュメントライブラリ、またはフォルダーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="20269-167">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span> <span data-ttu-id="20269-168">組織のオリジンを指定する場合は、非常に柔軟に設定できます。</span><span class="sxs-lookup"><span data-stu-id="20269-168">You have great flexibility when you specify origins for your organization.</span></span> <span data-ttu-id="20269-169">たとえば、すべての CDN アセットを配置する複数のオリジンまたは単一の発信元を指定できます。</span><span class="sxs-lookup"><span data-stu-id="20269-169">For example, you can specify multiple origins or a single origin where you want to put all your CDN assets.</span></span> <span data-ttu-id="20269-170">組織にパブリックまたはプライベートのどちらを使用するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="20269-170">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="20269-171">大部分の組織では、2つの組み合わせを実装することを選択します。</span><span class="sxs-lookup"><span data-stu-id="20269-171">Most organizations will choose to implement a combination of the two.</span></span>

<span data-ttu-id="20269-172">フォルダーやドキュメントライブラリなどの作成元に新しいコンテナーを作成し、CDN から使用できるようにするファイルを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="20269-172">You can create new container for your origins such as folders or document libraries, and add files you want to make available from the CDN.</span></span> <span data-ttu-id="20269-173">これは、CDN から使用できるようにする特定のアセットのセットがあり、その一連の CDN アセットをコンテナー内のファイルのみに制限する場合に適した方法です。</span><span class="sxs-lookup"><span data-stu-id="20269-173">This is a good approach if you have a specific set of assets you want to be available from the CDN, and want to restrict the set of CDN assets to only those files in the container.</span></span>

<span data-ttu-id="20269-174">既存のサイトコレクション、サイト、ライブラリ、またはフォルダーを作成元として構成することもできます。これにより、コンテナー内の対象となるすべてのアセットが CDN から利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="20269-174">You can also configure an existing site collection, site, library or folder as an origin, which will make all eligible assets in the container available from the CDN.</span></span> <span data-ttu-id="20269-175">既存のコンテナーを送信元として追加する前に、そのコンテンツとアクセス許可を確認して、匿名アクセスや権限のないユーザーに資産を誤って公開しないようにすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="20269-175">Before you add an existing container as an origin, it's important to make sure you are aware of its contents and permissions so you do not inadvertently expose assets to anonymous access or unauthorized users.</span></span>

<span data-ttu-id="20269-176">Cdn_ポリシー_を定義して、その出所のコンテンツを cdn から除外することができます。</span><span class="sxs-lookup"><span data-stu-id="20269-176">You can define _CDN policies_ to exclude content in your origins from the CDN.</span></span> <span data-ttu-id="20269-177">CDN ポリシーでは、_ファイルの種類_や_サイト分類_などの属性によってパブリックまたはプライベートの出所のアセットが除外されます。また、ポリシーで指定する CdnType (プライベートまたはパブリック) のすべてのオリジンに適用されます。</span><span class="sxs-lookup"><span data-stu-id="20269-177">CDN policies exclude assets in public or private origins by attributes such as _file type_ and _site classification_, and are applied to all origins of the CdnType (private or public) you specify in the policy.</span></span> <span data-ttu-id="20269-178">たとえば、複数のサブサイトが含まれるサイトで構成されるプライベートオリジンを追加する場合は、**機密**としてマークされたサイトを除外するポリシーを定義して、その分類を適用したサイトのコンテンツが CDN から提供されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="20269-178">For example, if you add a private origin consisting of a site that contains multiple subsites, you can define a policy to exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span> <span data-ttu-id="20269-179">このポリシーは、CDN に追加した_すべて_のプライベートオリジンのコンテンツに適用されます。</span><span class="sxs-lookup"><span data-stu-id="20269-179">The policy will apply to content from _all_ private origins you have added to the CDN.</span></span>
  
<span data-ttu-id="20269-180">オリジンの数が大きいほど、CDN サービスが要求を処理するのにかかる時間に大きな影響があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="20269-180">Keep in mind that the greater the number of origins, the greater the impact on the time it takes the CDN service to process requests.</span></span> <span data-ttu-id="20269-181">元の数を可能な限り制限することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="20269-181">We recommend that you limit the number of origins as much as possible.</span></span>
  
### <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="20269-182">各配信元をパブリックまたはプライベートにする必要があるかどうかを選択する</span><span class="sxs-lookup"><span data-stu-id="20269-182">Choose whether each origin should be public or private</span></span>
<span data-ttu-id="20269-183"><a name="CDNOriginChoosePublicPrivate"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-183"></span></span>

<span data-ttu-id="20269-184">発信元を識別する場合は、_パブリック_または_プライベート_にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="20269-184">When you identify an origin, you specify whether it should be made _public_ or _private_.</span></span> <span data-ttu-id="20269-185">公開されている出所の CDN アセットへのアクセスは匿名になり、プライベートな出所の CDN コンテンツは、セキュリティを強化するために動的に生成されたトークンによって保護されます。</span><span class="sxs-lookup"><span data-stu-id="20269-185">Access to CDN assets in public origins is anonymous, and CDN content in private origins is secured by dynamically generated tokens for greater security.</span></span> <span data-ttu-id="20269-186">どのオプションを選択したとしても、Microsoft では、CDN 自体の管理に関して、多くの処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="20269-186">Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself.</span></span> <span data-ttu-id="20269-187">また、CDN を設定して、出所を特定した後で、後で考えを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="20269-187">Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>

<span data-ttu-id="20269-188">パブリックおよびプライベートのどちらのオプションもパフォーマンスの向上に似ていますが、それぞれに固有の属性と利点があります。</span><span class="sxs-lookup"><span data-stu-id="20269-188">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span>

<span data-ttu-id="20269-189">Office 365 CDN 内の**公開**元は匿名でアクセス可能で、ホストされたアセットには、そのアセットへの URL を持つすべてのユーザーがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="20269-189">**Public** origins within the Office 365 CDN are accessible anonymously, and hosted assets can be accessed by anyone who has the URL to the asset.</span></span> <span data-ttu-id="20269-190">公開されている元の場所のコンテンツへのアクセスは匿名になるため、アクセスしたコンテンツは、機密データ以外の一般的なコンテンツ (JavaScript ファイル、スクリプト、アイコン、画像など) をキャッシュする場合にのみ使用するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="20269-190">Because access to content in public origins is anonymous, you should only use them to cache non-sensitive generic content such as javascript files, scripts, icons and images.</span></span>

<span data-ttu-id="20269-191">Office 365 CDN 内の**非公開**の元の場所は、SharePoint Online ドキュメント ライブラリ、サイト、メディア (例: 動画) など、ユーザー コンテンツへのプライベート アクセスを行う場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="20269-191">**Private** origins within the Office 365 CDN provide private access to user content such as SharePoint Online document libraries, sites and media such as videos.</span></span> <span data-ttu-id="20269-192">プライベートオリジンにあるコンテンツへのアクセスは、元のドキュメントライブラリまたは保存場所へのアクセス許可を持つユーザーのみがアクセスできるように、動的に生成されたトークンによってセキュリティ保護されます。</span><span class="sxs-lookup"><span data-stu-id="20269-192">Access to content in private origins is secured by dynamically generated tokens so it can only be accessed by users with permissions to the original document library or storage location.</span></span> <span data-ttu-id="20269-193">Office 365 CDN の出所は、SharePoint Online のコンテンツにのみ使用できます。また、SharePoint Online テナントからリダイレクトすることによって、プライベートの出所のアセットにのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="20269-193">Private origins in the Office 365 CDN can only be used for SharePoint Online content, and you can only access assets in private origins through redirection from your SharePoint Online tenant.</span></span>

<span data-ttu-id="20269-194">プライベートな出所のアセットに対する CDN アクセスのしくみについては、「[プライベートオリジンでアセットを使用](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-194">You can read more about how CDN access to assets in a private origin works in [Using assets in private origins](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a><span data-ttu-id="20269-195">公共の出所でのアセットのホスティングの属性と利点</span><span class="sxs-lookup"><span data-stu-id="20269-195">Attributes and advantages of hosting assets in public origins</span></span>
  
- <span data-ttu-id="20269-196">パブリックの配信元で公開されている資産には、すべてのユーザーが匿名でアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="20269-196">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="20269-197">ユーザー情報が含まれているリソース、または組織にとって公共の出所であると見なされるリソースは、決して配置しないでください。</span><span class="sxs-lookup"><span data-stu-id="20269-197">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>
- <span data-ttu-id="20269-198">パブリックの配信元から資産を削除した場合、その資産は最大 30 日間はキャッシュから引き続き使用できます。ただし、CDN 内の資産へのリンクは 15 分以内に無効になります。</span><span class="sxs-lookup"><span data-stu-id="20269-198">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
- <span data-ttu-id="20269-199">パブリックの配信元にスタイル シート (CSS ファイル) をホストする場合は、コード内で相対パスと URI を使用できます。</span><span class="sxs-lookup"><span data-stu-id="20269-199">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code.</span></span> <span data-ttu-id="20269-200">つまり、背景画像と他のオブジェクトの場所を、呼び出し元の資産の場所からの相対位置で参照することができます。</span><span class="sxs-lookup"><span data-stu-id="20269-200">This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
- <span data-ttu-id="20269-201">パブリックの配信元の URL をハード コーディングすることはできますが、お勧めできません。</span><span class="sxs-lookup"><span data-stu-id="20269-201">While you can hard code a public origin's URL, doing so is not recommended.</span></span> <span data-ttu-id="20269-202">CDN にアクセスできなくなった場合、SharePoint Online でその URL は自動的に組織に対して解決されず、結果としてリンクが壊れて他のエラーが発生する可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="20269-202">The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
- <span data-ttu-id="20269-203">パブリックの配信元用に含まれている既定のファイルの種類は、css、.eot、.gif、.ico、.jpeg、.jpg、.js、.map、.png、.svg、.ttf、.woff です。</span><span class="sxs-lookup"><span data-stu-id="20269-203">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff.</span></span> <span data-ttu-id="20269-204">その他のファイルの種類を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="20269-204">You can specify additional file types.</span></span>
- <span data-ttu-id="20269-205">指定したサイト分類で識別されたアセットを除外するようにポリシーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="20269-205">You can configure a policy to exclude assets that have been identified by site classifications that you specify.</span></span> <span data-ttu-id="20269-206">たとえば、許可されているファイルの種類のもので、パブリックの配信元にある資産であっても、"社外秘" または "制限付き" としてマークされている資産はすべて除外する、といったことができます。</span><span class="sxs-lookup"><span data-stu-id="20269-206">For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a><span data-ttu-id="20269-207">プライベートな出所でアセットをホスティングするための属性と利点</span><span class="sxs-lookup"><span data-stu-id="20269-207">Attributes and advantages of hosting assets in private origins</span></span>

- <span data-ttu-id="20269-208">プライベートオリジンは、SharePoint Online アセットにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="20269-208">Private origins can only be used for SharePoint Online assets.</span></span>
- <span data-ttu-id="20269-209">ユーザーは、コンテナーにアクセスする権限を持っている場合にのみ、プライベートの配信元からアセットにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="20269-209">Users can only access the assets from a private origin if they have permissions to access the container.</span></span> <span data-ttu-id="20269-210">これらの資産に匿名でアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="20269-210">Anonymous access to these assets is prevented.</span></span>
- <span data-ttu-id="20269-211">プライベートの出所のアセットは、SharePoint Online テナントから参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20269-211">Assets in private origins must be referred from the SharePoint Online tenant.</span></span> <span data-ttu-id="20269-212">プライベート CDN アセットへの直接アクセスは機能しません。</span><span class="sxs-lookup"><span data-stu-id="20269-212">Direct access to private CDN assets does not work.</span></span>
- <span data-ttu-id="20269-213">プライベートオリジンからアセットを削除すると、キャッシュから1時間以内に資産が利用可能になります。ただし、アセットの削除から15分以内に CDN のアセットへのリンクが無効になります。</span><span class="sxs-lookup"><span data-stu-id="20269-213">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes of the asset's removal.</span></span>
- <span data-ttu-id="20269-214">プライベートの配信元用に含まれている既定のファイルの種類は、.gif、.ico、.jpeg、.jpg、.js、.png です。</span><span class="sxs-lookup"><span data-stu-id="20269-214">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png.</span></span> <span data-ttu-id="20269-215">その他のファイルの種類を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="20269-215">You can specify additional file types.</span></span>
- <span data-ttu-id="20269-216">公開元の場合と同様に、ワイルドカードを使用してフォルダーまたはドキュメントライブラリ内のすべてのアセットを含める場合でも、指定したサイト分類で識別されたアセットを除外するようにポリシーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="20269-216">Just like with public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or document library.</span></span>

<span data-ttu-id="20269-217">Office 365 CDN、一般的な CDN 概念、および Office 365 テナントで使用できるその他の Microsoft CDNs を使用する理由の詳細については、「 [Content Delivery Networks](content-delivery-networks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-217">For more information about why to use the Office 365 CDN, general CDN concepts, and other Microsoft CDNs you can use with your Office 365 tenant, see [Content Delivery Networks](content-delivery-networks.md).</span></span>

### <a name="default-cdn-origins"></a><span data-ttu-id="20269-218">既定の CDN オリジン</span><span class="sxs-lookup"><span data-stu-id="20269-218">Default CDN origins</span></span>

<span data-ttu-id="20269-219">特に指定しない限り、office 365 では、Office 365 CDN を有効にすると、既定の出所が設定されます。</span><span class="sxs-lookup"><span data-stu-id="20269-219">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN.</span></span> <span data-ttu-id="20269-220">最初に設定しなかった場合は、セットアップの完了後にこれらのオリジンを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="20269-220">If you initially opt not to provision them, you can add these origins after you complete setup.</span></span> <span data-ttu-id="20269-221">既定の元の設定をスキップして、特定の理由がある場合は、CDN を有効にしたときに作成できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="20269-221">Unless you understand the consequences of skipping the setup of default origins and have a specific reason for doing so, you should allow them to be created when you enable the CDN.</span></span>
  
<span data-ttu-id="20269-222">既定のプライベート CDN の出所:</span><span class="sxs-lookup"><span data-stu-id="20269-222">Default private CDN origins:</span></span>
  
- <span data-ttu-id="20269-223">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="20269-223">\*/userphoto.aspx</span></span>
- <span data-ttu-id="20269-224">\*/siteassets</span><span class="sxs-lookup"><span data-stu-id="20269-224">\*/siteassets</span></span>

<span data-ttu-id="20269-225">既定のパブリック CDN の出所:</span><span class="sxs-lookup"><span data-stu-id="20269-225">Default public CDN origins:</span></span>
  
- <span data-ttu-id="20269-226">\*/マスター</span><span class="sxs-lookup"><span data-stu-id="20269-226">\*/masterpage</span></span>
- <span data-ttu-id="20269-227">\*/スタイルライブラリ</span><span class="sxs-lookup"><span data-stu-id="20269-227">\*/style library</span></span>
- <span data-ttu-id="20269-228">\*/clientsideアセット</span><span class="sxs-lookup"><span data-stu-id="20269-228">\*/clientsideassets</span></span>

> [!NOTE]
> <span data-ttu-id="20269-229">_clientsideassets_は、2017年12月に OFFICE 365 CDN サービスに追加された既定のパブリックの配信元です。</span><span class="sxs-lookup"><span data-stu-id="20269-229">_clientsideassets_ is a default public origin that was added to the Office 365 CDN service in December 2017.</span></span> <span data-ttu-id="20269-230">CDN で SharePoint Framework ソリューションを動作させるには、この配信元が存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="20269-230">This origin must be present in order for SharePoint Framework solutions in the CDN to work.</span></span> <span data-ttu-id="20269-231">2017年12月より前に Office 365 CDN を有効にした場合、または CDN を有効にしたときに既定の出所のセットアップをスキップした場合は、この配信元を手動で追加することができます。</span><span class="sxs-lookup"><span data-stu-id="20269-231">If you enabled the Office 365 CDN prior to December 2017, or if you skipped setup of default origins when you enabled the CDN, you can manually add this origin.</span></span> <span data-ttu-id="20269-232">詳細については、「[クライアント側の web パーツまたは SharePoint Framework ソリューションが動作しない](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-232">For more information, see [My client-side web part or SharePoint Framework solution isn't working](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="20269-233">SharePoint Online 管理シェルを使用して Office 365 CDN をセットアップおよび構成する</span><span class="sxs-lookup"><span data-stu-id="20269-233">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>
<span data-ttu-id="20269-234"><a name="CDNSetupinPShell"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-234"></span></span>

<span data-ttu-id="20269-235">このセクションの手順では、sharepoint online 管理シェルを使用して SharePoint Online に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20269-235">The procedures in this section require you to use the SharePoint Online Management Shell to connect to SharePoint Online.</span></span> <span data-ttu-id="20269-236">手順については、「[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-236">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>
  
<span data-ttu-id="20269-237">SharePoint online 管理シェルを使用して SharePoint Online でアセットをホストする CDN を設定および構成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="20269-237">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the SharePoint Online Management Shell.</span></span>
  
### <a name="enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="20269-238">組織で Office 365 CDN を使用できるようにする</span><span class="sxs-lookup"><span data-stu-id="20269-238">Enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="20269-239">テナントの CDN 設定に変更を加える前に、Office 365 テナントのプライベート CDN 構成の現在の状態を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20269-239">Before you make changes to the tenant CDN settings, you should retrieve the current status of the private CDN configuration in your Office 365 tenant.</span></span> <span data-ttu-id="20269-240">SharePoint Online 管理シェルを使用して、テナントに接続します。</span><span class="sxs-lookup"><span data-stu-id="20269-240">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

<span data-ttu-id="20269-241">次に、 **SPOTenantCdnEnabled**コマンドレットを使用して、テナントから CDN の状態設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="20269-241">Now use the **Get-SPOTenantCdnEnabled** cmdlet to retrieve the CDN status settings from the tenant:</span></span>

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

<span data-ttu-id="20269-242">指定した CdnType の CDN の状態は、画面に出力されます。</span><span class="sxs-lookup"><span data-stu-id="20269-242">The status of the CDN for the specified CdnType will output to the screen.</span></span>

<span data-ttu-id="20269-243">**SPOTenantCdnEnabled**コマンドレットを使用して、組織で OFFICE 365 CDN を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="20269-243">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN.</span></span> <span data-ttu-id="20269-244">組織でパブリックオリジン、プライベートオリジン、またはその両方を一度に使用できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="20269-244">You can enable your organization to use public origins, private origins, or both at once.</span></span> <span data-ttu-id="20269-245">既定のオリジンのセットアップを有効にした場合にスキップするように CDN を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="20269-245">You can also configure the CDN to skip the setup of default origins when you enable it.</span></span> <span data-ttu-id="20269-246">このトピックで説明されているように、いつでもこれらのオリジンを追加できます。</span><span class="sxs-lookup"><span data-stu-id="20269-246">You can always add these origins later as described in this topic.</span></span>
  
<span data-ttu-id="20269-247">SharePoint Online の Windows Powershell の場合:</span><span class="sxs-lookup"><span data-stu-id="20269-247">In Windows Powershell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="20269-248">たとえば、組織でパブリックオリジンとプライベートオリジンの両方を使用できるようにするには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="20269-248">For example, to enable your organization to use both public and private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="20269-249">組織でパブリックとプライベートの両方を使用できるようにし、既定のオリジンの設定をスキップするには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="20269-249">To enable your organization to use both public and private origins but skip setting up the default origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="20269-250">Office 365 CDN を有効にしたときに既定でプロビジョニングされるオリジンに関する情報、および既定のオリジンのセットアップをスキップすることによる影響を受ける可能性がある場合は、「 [DEFAULT CDN オリジン](use-office-365-cdn-with-spo.md#default-cdn-origins)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-250">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN, and the potential impact of skipping the setup of default origins.</span></span>

<span data-ttu-id="20269-251">組織でパブリックオリジンを使用できるようにするには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="20269-251">To enable your organization to use public origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="20269-252">組織でプライベートオリジンを使用できるようにするには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="20269-252">To enable your organization to use private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="20269-253">このコマンドレットの詳細については、「 [SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-253">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a><span data-ttu-id="20269-254">Office 365 CDN に含めるファイルの種類のリストを変更する (オプション)</span><span class="sxs-lookup"><span data-stu-id="20269-254">Change the list of file types to include in the Office 365 CDN (Optional)</span></span>
<span data-ttu-id="20269-255"><a name="Office365CDNforSPOFileType"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-255"></span></span>

> [!TIP]
> <span data-ttu-id="20269-256">**Set-spotenantcdnpolicy**コマンドレットを使用してファイルの種類を定義するときは、現在定義されているリストを上書きします。</span><span class="sxs-lookup"><span data-stu-id="20269-256">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="20269-257">他のファイルの種類を一覧に追加する場合は、コマンドレットを最初に使用して、既に許可されているファイルの種類を確認し、新しいファイルの種類を一覧に含めます。</span><span class="sxs-lookup"><span data-stu-id="20269-257">If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span>
  
<span data-ttu-id="20269-258">**Set-spotenantcdnpolicy**コマンドレットを使用して、CDN でパブリックおよびプライベートの出所でホストできる静的ファイルの種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="20269-258">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN.</span></span> <span data-ttu-id="20269-259">既定では、css、.gif、.jpg、.js などの一般的なアセットタイプが許可されています。</span><span class="sxs-lookup"><span data-stu-id="20269-259">By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span>

<span data-ttu-id="20269-260">SharePoint Online の Windows PowerShell の場合:</span><span class="sxs-lookup"><span data-stu-id="20269-260">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="20269-261">たとえば、CDN を有効にして .css ファイルと .png ファイルをホストできるようにするには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="20269-261">For example, to enable the CDN to host .css and .png files, you would enter the command:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

<span data-ttu-id="20269-262">CDN で現在許可されているファイルの種類を確認するには、 **get-spotenantcdnpolicies**コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="20269-262">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="20269-263">これらのコマンドレットの詳細については、「 [set-spotenantcdnpolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) 」および「 [get-spotenantcdnpolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-263">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a><span data-ttu-id="20269-264">Office 365 CDN から除外するサイト分類の一覧を変更する (オプション)</span><span class="sxs-lookup"><span data-stu-id="20269-264">Change the list of site classifications you want to exclude from the Office 365 CDN (Optional)</span></span>
<span data-ttu-id="20269-265"><a name="Office365CDNforSPOSiteClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-265"></span></span>

> [!TIP]
> <span data-ttu-id="20269-266">**Set-spotenantcdnpolicy**コマンドレットを使用してサイト分類を除外する場合は、現在定義されているリストを上書きします。</span><span class="sxs-lookup"><span data-stu-id="20269-266">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="20269-267">追加のサイト分類を除外する場合は、最初にコマンドレットを使用して、既に除外されている分類を確認し、新しい分類項目と共にそれらを追加します。</span><span class="sxs-lookup"><span data-stu-id="20269-267">If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span>

<span data-ttu-id="20269-268">
  \*\*Set-SPOTenantCdnPolicy\*\* コマンドレットを使用して、CDN で利用できるようにしないサイトの分類を除外します。</span><span class="sxs-lookup"><span data-stu-id="20269-268">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="20269-269">既定で除外されるサイトの分類はありません。</span><span class="sxs-lookup"><span data-stu-id="20269-269">By default, no site classifications are excluded.</span></span>

<span data-ttu-id="20269-270">SharePoint Online の Windows PowerShell の場合:</span><span class="sxs-lookup"><span data-stu-id="20269-270">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="20269-271">現在制限されているサイト分類を確認するには、 **get-spotenantcdnpolicies**コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="20269-271">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="20269-272">返されるプロパティには、 _IncludeFileExtensions_、 _ExcludeRestrictedSiteClassifications_ 、 _excludeifnoscriptdisabled_があります。</span><span class="sxs-lookup"><span data-stu-id="20269-272">The properties that will be returned are _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ and _ExcludeIfNoScriptDisabled_.</span></span>

<span data-ttu-id="20269-273">_IncludeFileExtensions_プロパティには、CDN から提供されるファイル拡張子の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="20269-273">The _IncludeFileExtensions_ property contains the list of file extensions that will be served from the CDN.</span></span>

> [!NOTE]
> <span data-ttu-id="20269-274">既定のファイル拡張子は、パブリックとプライベートの間で異なります。</span><span class="sxs-lookup"><span data-stu-id="20269-274">The default file extensions are different between public and private.</span></span>

<span data-ttu-id="20269-275">_ExcludeRestrictedSiteClassifications_プロパティには、CDN から除外するサイトの分類が含まれています。</span><span class="sxs-lookup"><span data-stu-id="20269-275">The _ExcludeRestrictedSiteClassifications_ property contains the site classifications that you want to exclude from the CDN.</span></span> <span data-ttu-id="20269-276">たとえば、**機密**としてマークされたサイトを除外して、その分類が適用されたサイトのコンテンツが CDN から提供されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="20269-276">For example, you can exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span>

<span data-ttu-id="20269-277">_Excludeifnoscriptdisabled_プロパティは、サイトレベルの_NoScript_属性の設定に基づいて CDN からコンテンツを除外します。</span><span class="sxs-lookup"><span data-stu-id="20269-277">The _ExcludeIfNoScriptDisabled_ property excludes content from the CDN based on the site-level _NoScript_ attribute settings.</span></span> <span data-ttu-id="20269-278">既定では、 _NoScript_属性は_モダン_サイトに対し**て [有効**] に設定され、_クラシック_サイトでは**無効**になっています。</span><span class="sxs-lookup"><span data-stu-id="20269-278">By default, the _NoScript_ attribute is set to **Enabled** for _Modern_ sites and **Disabled** for _Classic_ sites.</span></span> <span data-ttu-id="20269-279">これはテナントの設定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="20269-279">This depends on your tenant settings.</span></span>

<span data-ttu-id="20269-280">これらのコマンドレットの詳細については、「 [set-spotenantcdnpolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) 」および「 [get-spotenantcdnpolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-280">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="add-an-origin-for-your-assets"></a><span data-ttu-id="20269-281">アセットの送信元を追加する</span><span class="sxs-lookup"><span data-stu-id="20269-281">Add an origin for your assets</span></span>
<span data-ttu-id="20269-282"><a name="Office365CDNforSPOOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-282"></span></span>

<span data-ttu-id="20269-283">**Add-spotenantcdnorigin**コマンドレットを使用して、発信元を定義します。</span><span class="sxs-lookup"><span data-stu-id="20269-283">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin.</span></span> <span data-ttu-id="20269-284">複数の配信元を定義できます。</span><span class="sxs-lookup"><span data-stu-id="20269-284">You can define multiple origins.</span></span> <span data-ttu-id="20269-285">配信元は、CDN でホストする資産が含まれる SharePoint ライブラリまたはフォルダーを指す URL です。</span><span class="sxs-lookup"><span data-stu-id="20269-285">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="20269-286">ユーザー情報が含まれているリソース、または組織にとって公共の出所であると見なされるリソースは、決して配置しないでください。</span><span class="sxs-lookup"><span data-stu-id="20269-286">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

<span data-ttu-id="20269-287">_Path_の値は、アセットが格納されているライブラリまたはフォルダーへの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="20269-287">The value of _path_ is the relative path to the library or folder that contains the assets.</span></span> <span data-ttu-id="20269-288">相対パスに加え、ワイルドカードも使用できます。</span><span class="sxs-lookup"><span data-stu-id="20269-288">You can use wildcards in addition to relative paths.</span></span> <span data-ttu-id="20269-289">オリジンは、URL に付加されたワイルドカードをサポートします。</span><span class="sxs-lookup"><span data-stu-id="20269-289">Origins support wildcards prepended to the URL.</span></span> <span data-ttu-id="20269-290">これにより、複数のサイトにまたがるオリジンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="20269-290">This allows you to create origins that span multiple sites.</span></span> <span data-ttu-id="20269-291">たとえば、すべてのサイトのすべてのアセットを CDN 内のパブリックの配信元として masterpages フォルダーに含めるには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="20269-291">For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

- <span data-ttu-id="20269-292">ワイルドカード修飾子は**/** 、パスの先頭にのみ使用でき、指定した url の下にあるすべての url セグメントに一致します。</span><span class="sxs-lookup"><span data-stu-id="20269-292">The wildcard modifier \***/** can only be used at the beginning of the path, and will match all URL segments under the specified URL.</span></span>
- <span data-ttu-id="20269-293">パスは、ドキュメントライブラリ、フォルダー、またはサイトを指すことができます。</span><span class="sxs-lookup"><span data-stu-id="20269-293">The path can point to a document library, folder or site.</span></span> <span data-ttu-id="20269-294">たとえば、パス _\*/site1_は、サイトのすべてのドキュメントライブラリに一致します。</span><span class="sxs-lookup"><span data-stu-id="20269-294">For example, the path _\*/site1_ will match all the document libraries under the site.</span></span>

<span data-ttu-id="20269-295">特定の相対パスを持つ発信元を追加できます。</span><span class="sxs-lookup"><span data-stu-id="20269-295">You can add an origin with a specific relative path.</span></span> <span data-ttu-id="20269-296">完全なパスを使用して発信元を追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="20269-296">You cannot add an origin using the full path.</span></span>

<span data-ttu-id="20269-297">この例では、特定のサイトに siteassets ライブラリのプライベートオリジンを追加します。</span><span class="sxs-lookup"><span data-stu-id="20269-297">This example adds a private origin of the siteassets library on a specific site:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="20269-298">この例では、サイトコレクションのサイトアセットライブラリに_folder1_フォルダーのプライベートオリジンを追加します。</span><span class="sxs-lookup"><span data-stu-id="20269-298">This example adds a private origin of the _folder1_ folder in the site collection's site assets library:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

<span data-ttu-id="20269-299">パスにスペースが含まれている場合は、パスを二重引用符で囲むか、スペースを URL エンコーディング% 20 に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="20269-299">If there is a space in the path, you can either surround the path in double quotes or replace the space with the URL encoding %20.</span></span> <span data-ttu-id="20269-300">次の例では、サイトコレクションのサイトアセットライブラリに_フォルダー 1_フォルダーのプライベートオリジンを追加します。</span><span class="sxs-lookup"><span data-stu-id="20269-300">The following examples add a private origin of the _folder 1_ folder in the site collection's site assets library:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

<span data-ttu-id="20269-301">このコマンドとその構文の詳細については、「 [add-spotenantcdnorigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-301">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="20269-302">プライベートオリジンでは、送信元から共有されるアセットは、CDN からアクセスする前に、メジャーバージョンを発行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20269-302">In private origins, assets being shared from an origin must have a major version published before they can be accessed from the CDN.</span></span>
  
<span data-ttu-id="20269-303">コマンドを実行すると、システムによってデータセンター間の構成が同期されます。</span><span class="sxs-lookup"><span data-stu-id="20269-303">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="20269-304">これには最大15分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="20269-304">This can take up to 15 minutes.</span></span>
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="20269-305">例: SharePoint Online 用のマスターページおよびスタイルライブラリのパブリックの配信元を構成する</span><span class="sxs-lookup"><span data-stu-id="20269-305">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>
<span data-ttu-id="20269-306"><a name="ExamplePublicOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-306"></span></span>

<span data-ttu-id="20269-307">通常、これらの出所は、Office 365 CDN を有効にしたときに既定で設定されます。</span><span class="sxs-lookup"><span data-stu-id="20269-307">Normally, these origins are set up for you by default when you enable the Office 365 CDN.</span></span> <span data-ttu-id="20269-308">ただし、これらを手動で有効にする場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="20269-308">However, if you want to enable them manually, follow these steps.</span></span>
  
- <span data-ttu-id="20269-309">**Add-spotenantcdnorigin**コマンドレットを使用して、スタイルライブラリをパブリックの配信元として定義します。</span><span class="sxs-lookup"><span data-stu-id="20269-309">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- <span data-ttu-id="20269-310">**Add-spotenantcdnorigin**コマンドレットを使用して、マスターページをパブリックの配信元として定義します。</span><span class="sxs-lookup"><span data-stu-id="20269-310">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

<span data-ttu-id="20269-311">このコマンドとその構文の詳細については、「 [add-spotenantcdnorigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-311">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="20269-312">コマンドを実行すると、システムによってデータセンター間の構成が同期されます。</span><span class="sxs-lookup"><span data-stu-id="20269-312">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="20269-313">これには最大15分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="20269-313">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="20269-314">例: SharePoint Online のサイトアセット、サイトページ、および発行画像のプライベートオリジンを構成する</span><span class="sxs-lookup"><span data-stu-id="20269-314">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>
<span data-ttu-id="20269-315"><a name="ExamplePrivateOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-315"></span></span>

- <span data-ttu-id="20269-316">**Add-spotenantcdnorigin**コマンドレットを使用して、サイトの assets フォルダーをプライベートの配信元として定義します。</span><span class="sxs-lookup"><span data-stu-id="20269-316">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- <span data-ttu-id="20269-317">**Add-spotenantcdnorigin**コマンドレットを使用して、サイトページフォルダーをプライベートの配信元として定義します。</span><span class="sxs-lookup"><span data-stu-id="20269-317">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- <span data-ttu-id="20269-318">**Add-spotenantcdnorigin**コマンドレットを使用して、公開画像フォルダーをプライベートの配信元として定義します。</span><span class="sxs-lookup"><span data-stu-id="20269-318">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

<span data-ttu-id="20269-319">このコマンドとその構文の詳細については、「 [add-spotenantcdnorigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-319">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>

<span data-ttu-id="20269-320">コマンドを実行すると、システムによってデータセンター間の構成が同期されます。</span><span class="sxs-lookup"><span data-stu-id="20269-320">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="20269-321">これには最大15分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="20269-321">This can take up to 15 minutes.</span></span>

### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="20269-322">例: SharePoint Online のサイトコレクションのプライベートオリジンを構成する</span><span class="sxs-lookup"><span data-stu-id="20269-322">Example: Configure a private origin for a site collection for SharePoint Online</span></span>
<span data-ttu-id="20269-323"><a name="ExamplePrivateOriginSiteCollection"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-323"></span></span>

<span data-ttu-id="20269-324">**Add-spotenantcdnorigin**コマンドレットを使用して、サイトコレクションをプライベートの配信元として定義します。</span><span class="sxs-lookup"><span data-stu-id="20269-324">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin.</span></span> <span data-ttu-id="20269-325">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="20269-325">For example:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="20269-326">このコマンドとその構文の詳細については、「 [add-spotenantcdnorigin](https://technet.microsoft.com/en-us/library/mt790772.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-326">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="20269-327">コマンドを実行すると、システムによってデータセンター間の構成が同期されます。</span><span class="sxs-lookup"><span data-stu-id="20269-327">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="20269-328">SharePoint Online テナントが CDN サービスに接続すると予想される_構成保留_メッセージが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="20269-328">You may see a _Configuration pending_ message which is expected as the SharePoint Online tenant connects to the CDN service.</span></span> <span data-ttu-id="20269-329">これには最大15分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="20269-329">This can take up to 15 minutes.</span></span>

### <a name="manage-the-office-365-cdn"></a><span data-ttu-id="20269-330">Office 365 CDN を管理する</span><span class="sxs-lookup"><span data-stu-id="20269-330">Manage the Office 365 CDN</span></span>
<span data-ttu-id="20269-331"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-331"></span></span>

<span data-ttu-id="20269-332">CDN を設定したら、このセクションで説明するように、コンテンツを更新するとき、または必要に応じて変更を加えたときに構成を変更できます。</span><span class="sxs-lookup"><span data-stu-id="20269-332">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="20269-333">Office 365 CDN でアセットを追加、更新、または削除する</span><span class="sxs-lookup"><span data-stu-id="20269-333">Add, update, or remove assets from the Office 365 CDN</span></span>
<span data-ttu-id="20269-334"><a name="Office365CDNforSPOaddremoveasset"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-334"></span></span>

<span data-ttu-id="20269-335">セットアップの手順を完了すると、必要に応じて、新しいアセットを追加したり、既存のアセットを更新または削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="20269-335">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want.</span></span> <span data-ttu-id="20269-336">元として識別したフォルダーまたは SharePoint ライブラリのアセットを変更するだけです。</span><span class="sxs-lookup"><span data-stu-id="20269-336">Just make your changes to the assets in the folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="20269-337">新しいアセットを追加すると、そのアセットは CDN ですぐに使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="20269-337">If you add a new asset, it is available through the CDN immediately.</span></span> <span data-ttu-id="20269-338">ただし、アセットを更新する場合は、新しいコピーが伝達されて CDN で利用可能になるまで最大15分かかります。</span><span class="sxs-lookup"><span data-stu-id="20269-338">However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="20269-339">送信元の場所を取得する必要がある場合は、 **get-spotenantcdnorigins**コマンドレットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="20269-339">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet.</span></span> <span data-ttu-id="20269-340">このコマンドレットの使用方法については、「 [get-spotenantcdnorigins](https://technet.microsoft.com/en-us/library/mt790770.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-340">For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span></span>
  
#### <a name="remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="20269-341">Office 365 CDN から発信元を削除する</span><span class="sxs-lookup"><span data-stu-id="20269-341">Remove an origin from the Office 365 CDN</span></span>
<span data-ttu-id="20269-342"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-342"></span></span>

<span data-ttu-id="20269-343">送信元として指定したフォルダーまたは SharePoint ライブラリへのアクセスを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="20269-343">You can remove access to a folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="20269-344">これを行うには、 **add-spotenantcdnorigin**コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="20269-344">To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet.</span></span>

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

<span data-ttu-id="20269-345">このコマンドレットの使用方法については、「 [add-spotenantcdnorigin](https://technet.microsoft.com/en-us/library/mt790761.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-345">For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span></span>
  
#### <a name="modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="20269-346">Office 365 CDN の配信元を変更する</span><span class="sxs-lookup"><span data-stu-id="20269-346">Modify an origin in the Office 365 CDN</span></span>
<span data-ttu-id="20269-347"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-347"></span></span>

<span data-ttu-id="20269-348">作成した元を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="20269-348">You cannot modify an origin you've created.</span></span> <span data-ttu-id="20269-349">代わりに、元を削除してから、新しいものを追加します。</span><span class="sxs-lookup"><span data-stu-id="20269-349">Instead, remove the origin and then add a new one.</span></span> <span data-ttu-id="20269-350">詳細については、「 [Office 365 CDN から発信元を削除する](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin)」および「[アセットの送信元を追加](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin)するには」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-350">For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>
  
#### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="20269-351">Office 365 CDN を無効にする</span><span class="sxs-lookup"><span data-stu-id="20269-351">Disable the Office 365 CDN</span></span>
<span data-ttu-id="20269-352"><a name="Office365CDNforSPODisable"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-352"></span></span>

<span data-ttu-id="20269-353">組織の CDN を無効にするには、 **SPOTenantCdnEnabled**コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="20269-353">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization.</span></span> <span data-ttu-id="20269-354">CDN に対してパブリックおよびプライベートオリジンの両方を有効にしている場合は、次の例に示すように、コマンドレットを2回実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20269-354">If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span>
  
<span data-ttu-id="20269-355">CDN でパブリックオリジンを使用できないようにするには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="20269-355">To disable use of public origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="20269-356">CDN でプライベートオリジンを使用できないようにするには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="20269-356">To disable use of the private origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="20269-357">このコマンドレットの詳細については、「 [SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-357">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>

## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a><span data-ttu-id="20269-358">Office 365 CLI を使用して Office 365 CDN をセットアップおよび構成する</span><span class="sxs-lookup"><span data-stu-id="20269-358">Set up and configure the Office 365 CDN using the Office 365 CLI</span></span>
<span data-ttu-id="20269-359"><a name="CDNSetupinCLI"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-359"></span></span>

<span data-ttu-id="20269-360">このセクションの手順では、 [Office 365 CLI](https://aka.ms/o365cli)がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="20269-360">The procedures in this section require that you have installed the [Office 365 CLI](https://aka.ms/o365cli).</span></span> <span data-ttu-id="20269-361">次に、[spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) コマンドを使用してご利用の SharePoint Online テナントに接続します。</span><span class="sxs-lookup"><span data-stu-id="20269-361">Next, connect to your SharePoint Online tenant using the [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) command.</span></span>

<span data-ttu-id="20269-362">Office 365 CLI を使用して SharePoint Online でアセットをホストする CDN を設定および構成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="20269-362">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the Office 365 CLI.</span></span>

### <a name="enable-the-office-365-cdn"></a><span data-ttu-id="20269-363">Office 365 CDN を有効にする</span><span class="sxs-lookup"><span data-stu-id="20269-363">Enable the Office 365 CDN</span></span>

<span data-ttu-id="20269-364">テナントの Office 365 CDN の状態は [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) コマンドを使用して管理できます。</span><span class="sxs-lookup"><span data-stu-id="20269-364">You can manage the state of the Office 365 CDN in your tenant using the [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) command.</span></span>

<span data-ttu-id="20269-365">テナントで Office 365 パブリック CDN を有効にするには、次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="20269-365">To enable the Office 365 Public CDN in your tenant execute:</span></span>

```sh
spo cdn set --type Public --enabled true
```

<span data-ttu-id="20269-366">Office 365 SharePoint CDN を有効にするには、次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="20269-366">To enable the Office 365 SharePoint CDN, execute:</span></span>

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a><span data-ttu-id="20269-367">Office 365 CDN の現在の状況を確認する</span><span class="sxs-lookup"><span data-stu-id="20269-367">View the current status of the Office 365 CDN</span></span>

<span data-ttu-id="20269-368">特定の種類の Office 365 CDN が有効か無効かを確認するには、 [spo CDN get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/)コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="20269-368">To check if the particular type of Office 365 CDN is enabled or disabled, use the [spo cdn get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) command.</span></span>

<span data-ttu-id="20269-369">Office 365 パブリック CDN が有効かどうかを確認するには、次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="20269-369">To check if the Office 365 Public CDN is enabled, execute:</span></span>

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a><span data-ttu-id="20269-370">Office 365 CDN の配信元を表示する</span><span class="sxs-lookup"><span data-stu-id="20269-370">View the Office 365 CDN origins</span></span>

<span data-ttu-id="20269-371">現在構成されている Office 365 パブリック CDN の配信元を確認するには、次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="20269-371">To view the currently configured Office 365 Public CDN origins execute:</span></span>

```sh
spo cdn origin list --type Public
```

<span data-ttu-id="20269-372">Office 365 CDN を有効にしたときに既定でプロビジョニングされるオリジンに関する情報については、「 [DEFAULT CDN オリジン](use-office-365-cdn-with-spo.md#default-cdn-origins)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-372">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN.</span></span>

### <a name="add-an-office-365-cdn-origin"></a><span data-ttu-id="20269-373">Office 365 CDN の配信元を追加する</span><span class="sxs-lookup"><span data-stu-id="20269-373">Add an Office 365 CDN origin</span></span>

> [!IMPORTANT]
> <span data-ttu-id="20269-374">パブリックの配信元として構成された SharePoint ドキュメントライブラリで、組織に機密であると見なされるリソースを決して配置しないでください。</span><span class="sxs-lookup"><span data-stu-id="20269-374">You should never place resources that are considered sensitive to your organization in a SharePoint document library configured as a public origin.</span></span>

<span data-ttu-id="20269-375">[spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) コマンドを使用して CDN の配信元を定義します。</span><span class="sxs-lookup"><span data-stu-id="20269-375">Use the [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) command to define a CDN origin.</span></span> <span data-ttu-id="20269-376">複数の配信元を定義できます。</span><span class="sxs-lookup"><span data-stu-id="20269-376">You can define multiple origins.</span></span> <span data-ttu-id="20269-377">配信元は、CDN でホストする資産が含まれる SharePoint ライブラリまたはフォルダーを指す URL です。</span><span class="sxs-lookup"><span data-stu-id="20269-377">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

<span data-ttu-id="20269-378">ここ`path`で、はアセットを含むフォルダーへの相対パスです。</span><span class="sxs-lookup"><span data-stu-id="20269-378">Where `path` is the relative path to the folder that contains the assets.</span></span> <span data-ttu-id="20269-379">相対パスに加え、ワイルドカードも使用できます。</span><span class="sxs-lookup"><span data-stu-id="20269-379">You can use wildcards in addition to relative paths.</span></span>

<span data-ttu-id="20269-380">すべてのサイトの**マスターページギャラリー**内のすべてのアセットをパブリックの配信元として含めるには、次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="20269-380">To include all assets in the **Master Page Gallery** of all sites as a public origin, execute:</span></span>

```sh
spo cdn origin add --type Public --origin */masterpage
```

<span data-ttu-id="20269-381">特定のサイト コレクションのプライベートの配信元を構成するには、次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="20269-381">To configure a private origin for a specific site collection, execute:</span></span>

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> <span data-ttu-id="20269-382">CDN の配信元の追加後、CDN サービス経由でファイルを取得できるようになるまで最大 15 分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="20269-382">After adding a CDN origin, it might take up to 15 minutes for you to be able to retrieve files via the CDN service.</span></span> <span data-ttu-id="20269-383">特定の配信元が既に有効かどうかは、[spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) コマンドを使用して検証できます。</span><span class="sxs-lookup"><span data-stu-id="20269-383">You can verify if the particular origin has already been enabled using the [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command.</span></span>

### <a name="remove-an-office-365-cdn-origin"></a><span data-ttu-id="20269-384">Office 365 CDN の配信元を削除する</span><span class="sxs-lookup"><span data-stu-id="20269-384">Remove an Office 365 CDN origin</span></span>

<span data-ttu-id="20269-385">[spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) コマンドを使用して、指定した種類の CDN の配信元を削除します。</span><span class="sxs-lookup"><span data-stu-id="20269-385">Use the [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) command to remove a CDN origin for the specified CDN type.</span></span>

<span data-ttu-id="20269-386">CDN 構成からパブリックの配信元を削除するには、次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="20269-386">To remove a public origin from the CDN configuration, execute:</span></span>

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> <span data-ttu-id="20269-387">CDN の配信元を削除しても、その配信元に一致するドキュメントライブラリに格納されているファイルには影響しません。</span><span class="sxs-lookup"><span data-stu-id="20269-387">Removing a CDN origin doesn't affect the files stored in any document library matching that origin.</span></span> <span data-ttu-id="20269-388">これらのアセットが SharePoint URL を使用して参照されている場合、SharePoint はドキュメントライブラリを指す元の URL に自動的に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="20269-388">If these assets have been referenced using their SharePoint URL, SharePoint will automatically switch back to the original URL pointing to the document library.</span></span> <span data-ttu-id="20269-389">ただし、アセットがパブリック CDN URL を使用して参照されている場合は、発信元を削除するとリンクが解除され、手動で変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20269-389">If, however, assets have been referenced using a public CDN URL, then removing the origin will break the link and you will need to manually change them.</span></span>

### <a name="modify-an-office-365-cdn-origin"></a><span data-ttu-id="20269-390">Office 365 CDN の配信元を変更する</span><span class="sxs-lookup"><span data-stu-id="20269-390">Modify an Office 365 CDN origin</span></span>

<span data-ttu-id="20269-391">既存の CDN の配信元を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="20269-391">It's not possible to modify an existing CDN origin.</span></span> <span data-ttu-id="20269-392">代わりに、`spo cdn origin remove` コマンドを使用して定義済みの CDN の配信元を削除して、`spo cdn origin add` コマンドで新しい配信元を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20269-392">Instead, you should remove the previously defined CDN origin using the `spo cdn origin remove` command and add a new one using the `spo cdn origin add` command.</span></span>

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a><span data-ttu-id="20269-393">Office 365 CDN に含めるファイルの種類を変更する</span><span class="sxs-lookup"><span data-stu-id="20269-393">Change the types of files to include in the Office 365 CDN</span></span>

<span data-ttu-id="20269-394">既定で CND に含まれるファイルの種類は、_.css、.eot、.gif、.ico、.jpeg、.jpg、.js、.map、.png、.svg、.ttf、.woff_ です。</span><span class="sxs-lookup"><span data-stu-id="20269-394">By default, the following file types are included in the CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff_.</span></span> <span data-ttu-id="20269-395">CDN に他の種類のファイルを含める必要がある場合、[spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) コマンドを使用して CDN 構成を変更できます。</span><span class="sxs-lookup"><span data-stu-id="20269-395">If you need to include additional file types in the CDN, you can change the CDN configuration using the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command.</span></span>

> [!NOTE]
> <span data-ttu-id="20269-396">ファイルの種類のリストを変更する場合、現在定義されているリストを上書きします。</span><span class="sxs-lookup"><span data-stu-id="20269-396">When changing the list of file types, you overwrite the currently defined list.</span></span> <span data-ttu-id="20269-397">他のファイルの種類を追加する場合は、[spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) コマンドを最初に使用して現在構成されているファイルの種類を確認します。</span><span class="sxs-lookup"><span data-stu-id="20269-397">If you want to include additional file types, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command to find out which file types are currently configured.</span></span>

<span data-ttu-id="20269-398">_JSON_ファイルの種類を、パブリック CDN に含まれるファイルの種類の既定のリストに追加するには、次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="20269-398">To add the _JSON_ file type to the default list of file types included in the public CDN, execute:</span></span>

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="20269-399">Office 365 CDN から除外するサイトの分類のリストを変更する</span><span class="sxs-lookup"><span data-stu-id="20269-399">Change the list of site classifications you want to exclude from the Office 365 CDN</span></span>

<span data-ttu-id="20269-400">[spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) コマンドを使用して、CDN で利用できるようにしないサイトの分類を除外します。</span><span class="sxs-lookup"><span data-stu-id="20269-400">Use the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="20269-401">既定で除外されるサイトの分類はありません。</span><span class="sxs-lookup"><span data-stu-id="20269-401">By default, no site classifications are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="20269-402">除外するサイトの分類のリストを変更する場合、現在定義されているリストを上書きします。</span><span class="sxs-lookup"><span data-stu-id="20269-402">When changing the list of excluded site classifications, you overwrite the currently defined list.</span></span> <span data-ttu-id="20269-403">他の分類を除外する場合は、[spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) コマンドを最初に使用して現在構成されている分類を確認します。</span><span class="sxs-lookup"><span data-stu-id="20269-403">If you want to exclude additional classifications, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) command to find out which classifications are currently configured.</span></span>

<span data-ttu-id="20269-404">_HBI_として分類されたサイトをパブリック CDN から除外するには、execute</span><span class="sxs-lookup"><span data-stu-id="20269-404">To exclude sites classified as _HBI_ from the public CDN, execute</span></span>

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="20269-405">Office 365 CDN を無効にする</span><span class="sxs-lookup"><span data-stu-id="20269-405">Disable the Office 365 CDN</span></span>

<span data-ttu-id="20269-406">Office 365 CDN を無効にするには、`spo cdn set` コマンドを使用します。たとえば、次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="20269-406">To disable the Office 365 CDN use the `spo cdn set` command, for example:</span></span>

```sh
spo cdn set --type Public --enabled false
```

## <a name="using-your-cdn-assets"></a><span data-ttu-id="20269-407">CDN アセットの使用</span><span class="sxs-lookup"><span data-stu-id="20269-407">Using your CDN assets</span></span>

<span data-ttu-id="20269-408">CDN および構成されたオリジンとポリシーが有効になったので、CDN アセットの使用を開始できます。</span><span class="sxs-lookup"><span data-stu-id="20269-408">Now that you have enabled the CDN and configured origins and policies, you can begin using your CDN assets.</span></span>

<span data-ttu-id="20269-409">このセクションでは、sharepoint ページとコンテンツで CDN Url を使用する方法を理解するのに役立ちます。これにより、SharePoint はパブリックとプライベートの両方のアセットに対する要求を CDN にリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="20269-409">This section will help you understand how to use CDN URLs in your SharePoint pages and content so that SharePoint redirects requests for assets in both public and private origins to the CDN.</span></span>

- [<span data-ttu-id="20269-410">CDN アセットへのリンクの更新</span><span class="sxs-lookup"><span data-stu-id="20269-410">Updating links to CDN assets</span></span>](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
- [<span data-ttu-id="20269-411">パブリックの出所でアセットを使用する</span><span class="sxs-lookup"><span data-stu-id="20269-411">Using assets in public origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
- [<span data-ttu-id="20269-412">プライベートの出所でアセットを使用する</span><span class="sxs-lookup"><span data-stu-id="20269-412">Using assets in private origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

<span data-ttu-id="20269-413">クライアント側の web パーツをホストするために CDN を使用する方法については、「 [Office 365 CDN からクライアント側の web パーツをホストする (Hello World パート 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-413">For information on how to use the CDN for hosting client-side web parts, see the topic [Host your client-side web part from Office 365 CDN (Hello World part 4)](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span></span>

### <a name="updating-links-to-cdn-assets"></a><span data-ttu-id="20269-414">CDN アセットへのリンクの更新</span><span class="sxs-lookup"><span data-stu-id="20269-414">Updating links to CDN assets</span></span>

<span data-ttu-id="20269-415">オリジナルに追加したアセットを使用するには、元のファイルへのリンクを元のファイルへのパスで更新するだけです。</span><span class="sxs-lookup"><span data-stu-id="20269-415">To use assets that you have added to an origin, you simply update links to the original file with the path to the file in the origin.</span></span>

- <span data-ttu-id="20269-416">送信元に追加したアセットへのリンクが含まれているページまたはコンテンツを編集します。</span><span class="sxs-lookup"><span data-stu-id="20269-416">Edit the page or content that contains links to assets you have added to an origin.</span></span> <span data-ttu-id="20269-417">また、複数の方法のうちの1つを使用して、サイトまたはサイトコレクション内の特定のアセットにリンクを更新する場合は、そのすべてのリンクをグローバルに検索して置換することもできます。</span><span class="sxs-lookup"><span data-stu-id="20269-417">You can also use one of several methods to globally search and replace links across an enter site or site collection if you want to update the link to a given asset everywhere it appears.</span></span>
- <span data-ttu-id="20269-418">送信元のアセットへのリンクごとに、パスを CDN の配信元のファイルへのパスに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="20269-418">For each link to an asset in an origin, replace the path with the path to the file in the CDN origin.</span></span> <span data-ttu-id="20269-419">相対パスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="20269-419">You can use relative paths.</span></span>
- <span data-ttu-id="20269-420">ページまたはコンテンツを保存します。</span><span class="sxs-lookup"><span data-stu-id="20269-420">Save the page or content.</span></span>

<span data-ttu-id="20269-421">たとえば、ドキュメントライブラリフォルダー _/site¥_/site/SiteAssets/images/image.png にコピーしたイメージの__ について考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="20269-421">For example, consider the image _/site/SiteAssets/images/image.png_, which you have copied to the document library folder _/site/CDN_origins/public/_.</span></span> <span data-ttu-id="20269-422">CDN アセットを使用するには、元のパスを画像ファイルの場所に置き換え、新しい URL の _/site/CDN_origins/public/image.png_を作成します。</span><span class="sxs-lookup"><span data-stu-id="20269-422">To use the CDN asset, replace the original path to the image file location with the path to the origin to make the new URL _/site/CDN_origins/public/image.png_.</span></span>

<span data-ttu-id="20269-423">相対パスではなく、アセットへの完全な URL を使用する場合は、次のようなリンクを作成します。</span><span class="sxs-lookup"><span data-stu-id="20269-423">If you want to use the full URL to the asset instead of a relative path, construct the link like so:</span></span>

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> <span data-ttu-id="20269-424">一般的に、CDN のアセットに直接 Url をハードコーディングしないでください。</span><span class="sxs-lookup"><span data-stu-id="20269-424">In general, you should not hardcode URLs directly to assets in the CDN.</span></span> <span data-ttu-id="20269-425">ただし、必要に応じて、パブリックの出所でアセットの Url を手動で作成することができます。</span><span class="sxs-lookup"><span data-stu-id="20269-425">However, you can manually construct URLs for assets in public origins if needed.</span></span> <span data-ttu-id="20269-426">詳細については、「[パブリックアセットのハード CDN url](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-426">For more information, see [Hardcoding CDN URLs for public assets](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span></span>

<span data-ttu-id="20269-427">CDN からアセットが提供されているかどうかを確認する方法については、「 [Office 365 cdn のトラブルシューティング](use-office-365-cdn-with-spo.md#CDNTroubleshooting)」セクションの「[アセットが cdn によって提供さ](use-office-365-cdn-with-spo.md#CDNConfirm)れていることを確認する方法」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-427">To learn about how to verify that assets are being served from the CDN, see [How do I confirm that assets are being served by the CDN?](use-office-365-cdn-with-spo.md#CDNConfirm) in the [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) section.</span></span>

### <a name="using-assets-in-public-origins"></a><span data-ttu-id="20269-428">パブリックの出所でアセットを使用する</span><span class="sxs-lookup"><span data-stu-id="20269-428">Using assets in public origins</span></span>

<span data-ttu-id="20269-429">SharePoint Online の**発行機能**によって、パブリックの配信元に格納されているアセットの url が自動的に cdn に書き換えられ、アセットが SharePoint ではなく cdn サービスから提供されるようになります。</span><span class="sxs-lookup"><span data-stu-id="20269-429">The **Publishing feature** in SharePoint Online automatically rewrites URLs of assets stored in public origins to their CDN equivalents so that assets are served from the CDN service instead of SharePoint.</span></span>

<span data-ttu-id="20269-430">発行機能が有効になっているサイトに送信元があり、CDN にオフロードするアセットが次のいずれかのカテゴリに含まれている場合、SharePoint はそのアセットが CDN によって除外されていないことを前提として、送信元のアセットの Url を自動的にリライトします。 原則.</span><span class="sxs-lookup"><span data-stu-id="20269-430">If your origin is in a site with the Publishing feature enabled, and the assets you want to offload to the CDN are in one of the following categories, SharePoint will automatically rewrite URLs for assets in the origin, provided that the asset has not been excluded by a CDN policy.</span></span>

<span data-ttu-id="20269-431">SharePoint 発行機能によって自動的に書き換えられるのは次のようなリンクです。</span><span class="sxs-lookup"><span data-stu-id="20269-431">The following is an overview of which links are automatically rewritten by the SharePoint Publishing feature:</span></span>

- <span data-ttu-id="20269-432">従来の発行ページの HTML 応答の IMG/LINK/CSS URL</span><span class="sxs-lookup"><span data-stu-id="20269-432">IMG/LINK/CSS URLs in classic publishing page HTML responses</span></span>
  - <span data-ttu-id="20269-433">これには、ページの HTML コンテンツ内に作成者によって追加された画像が含まれます。</span><span class="sxs-lookup"><span data-stu-id="20269-433">This includes images added by authors within the HTML content of a page</span></span>
- <span data-ttu-id="20269-434">画像ライブラリ スライドショー Web パーツの画像 URL</span><span class="sxs-lookup"><span data-stu-id="20269-434">Picture Library SlideShow webpart image URLs</span></span>
- <span data-ttu-id="20269-435">SPList REST API (RenderListDataAsStream) 結果の画像フィールド</span><span class="sxs-lookup"><span data-stu-id="20269-435">Image fields in SPList REST API (RenderListDataAsStream) results</span></span>
  - <span data-ttu-id="20269-436">新しいプロパティ_Imagefieldstotryrewritetocdnurls_を使用して、フィールドのコンマ区切りリストを指定します。</span><span class="sxs-lookup"><span data-stu-id="20269-436">Use the new property _ImageFieldsToTryRewriteToCdnUrls_ to provide a comma separated list of fields</span></span>
  - <span data-ttu-id="20269-437">ハイパーリンクフィールドと発行先イメージフィールドをサポートします。</span><span class="sxs-lookup"><span data-stu-id="20269-437">Supports hyperlink fields and PublishingImage fields</span></span>
- <span data-ttu-id="20269-438">SharePoint image レンディション</span><span class="sxs-lookup"><span data-stu-id="20269-438">SharePoint image renditions</span></span>

<span data-ttu-id="20269-439">次の図は、SharePoint がパブリックの配信元からアセットを含むページに対する要求を受信した場合のワークフローを示しています。</span><span class="sxs-lookup"><span data-stu-id="20269-439">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a public origin.</span></span>

<span data-ttu-id="20269-440">![ワークフローダイアグラム: パブリックの配信元から Office 365 CDN アセットを取得する](media/O365-CDN/o365-cdn-public-steps-transparent.svg "ワークフロー: パブリックの配信元から Office 365 CDN アセットを取得する")</span><span class="sxs-lookup"><span data-stu-id="20269-440">![Workflow diagram: Retrieving Office 365 CDN assets from a public origin](media/O365-CDN/o365-cdn-public-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a public origin")</span></span>

> [!TIP]
> <span data-ttu-id="20269-441">ページ上の特定の Url に対する自動書き換えを無効にする場合は、ページをチェックアウトし、クエリ文字列パラメーターを追加し**ます。** 無効にする各リンクの最後に、NoAutoReWrites = true を指定します。</span><span class="sxs-lookup"><span data-stu-id="20269-441">If you want to disable auto-rewriting for specific URLs on a page, you can check out the page and add the query string parameter **?NoAutoReWrites=true** to the end of each link you want to disable.</span></span>

#### <a name="hardcoding-cdn-urls-for-public-assets"></a><span data-ttu-id="20269-442">パブリックアセットの CDN の Url をハードコーディングする</span><span class="sxs-lookup"><span data-stu-id="20269-442">Hardcoding CDN URLs for public assets</span></span>

<span data-ttu-id="20269-443">_発行_機能がパブリックの配信元に対して有効になっていない場合、またはアセットが cdn サービスの自動リライト機能によってサポートされているリンクの種類のいずれでもない場合は、アセットの cdn の場所に url を手動で作成して、コンテンツ内でこれらの url を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="20269-443">If the _Publishing_ feature is not enabled for a public origin, or the asset is not one of the link types supported by the auto-rewrite feature of the CDN service, you can manually construct URLs to the CDN location of the assets and use these URLs in your content.</span></span>

> [!NOTE]
> <span data-ttu-id="20269-444">URL の最後のセクションを形成する必要なアクセストークンがリソースの要求時に生成されるため、プライベートな出所のアセットに CDN Url をハードコーディングすることはできません。</span><span class="sxs-lookup"><span data-stu-id="20269-444">You cannot hardcode CDN URLs to assets in a private origin because the required access token that forms the last section of the URL is generated at the time the resource is requested.</span></span>

<span data-ttu-id="20269-445">パブリック CDN アセットの場合、URL の形式は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="20269-445">For public CDN assets, the URL format will look like the following:</span></span>

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

<span data-ttu-id="20269-446">**TenantHostName**をテナント名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="20269-446">Replace **TenantHostName** with your tenant name.</span></span> <span data-ttu-id="20269-447">例:</span><span class="sxs-lookup"><span data-stu-id="20269-447">Example:</span></span>

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a><span data-ttu-id="20269-448">プライベートの出所でアセットを使用する</span><span class="sxs-lookup"><span data-stu-id="20269-448">Using assets in private origins</span></span>

<span data-ttu-id="20269-449">プライベートオリジンでアセットを使用するには、追加の構成は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="20269-449">No additional configuration is required to use assets in private origins.</span></span> <span data-ttu-id="20269-450">SharePoint Online は、プライベートの送信元でアセットの Url を自動的にリライトするので、それらのアセットに対する要求は常に CDN から提供されます。</span><span class="sxs-lookup"><span data-stu-id="20269-450">SharePoint Online automatically rewrites URLs for assets in private origins so requests for those assets will always be served from the CDN.</span></span> <span data-ttu-id="20269-451">これらの Url には、アセットが要求されたときに SharePoint Online によって自動生成される必要があるトークンが含まれるため、プライベートの出所に CDN アセットの Url を手動で作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="20269-451">You cannot manually build URLs to CDN assets in private origins because these URLs contain tokens that must be auto-generated by SharePoint Online at the time the asset is requested.</span></span>

<span data-ttu-id="20269-452">プライベートオリジン内のアセットへのアクセスは、次のセクションで説明する警告を使用して、発信元へのユーザーの権限に基づいて、動的に生成されたトークンによって保護されます。</span><span class="sxs-lookup"><span data-stu-id="20269-452">Access to assets in private origins is protected by dynamically generated tokens based on user permissions to the origin, with the caveats described in the following sections.</span></span> <span data-ttu-id="20269-453">コンテンツをレンダリングするには、ユーザーが CDN に対して少なくとも**読み取り**アクセス権を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="20269-453">Users must have at least **read** access to the origins for the CDN to render content.</span></span>

<span data-ttu-id="20269-454">次の図は、SharePoint が私的な出所からアセットを含むページに対する要求を受信した場合のワークフローを示しています。</span><span class="sxs-lookup"><span data-stu-id="20269-454">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a private origin.</span></span>

<span data-ttu-id="20269-455">![ワークフローダイアグラム: 私的な出所から Office 365 CDN アセットを取得する](media/O365-CDN/o365-cdn-private-steps-transparent.svg "ワークフロー: 私的な出所から Office 365 CDN アセットを取得する")</span><span class="sxs-lookup"><span data-stu-id="20269-455">![Workflow diagram: Retrieving Office 365 CDN assets from a private origin](media/O365-CDN/o365-cdn-private-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a private origin")</span></span>

#### <a name="token-based-authorization-in-private-origins"></a><span data-ttu-id="20269-456">プライベートオリジンでのトークンベース認証</span><span class="sxs-lookup"><span data-stu-id="20269-456">Token-based authorization in private origins</span></span>

<span data-ttu-id="20269-457">Office 365 CDN のプライベートオリジンにあるアセットへのアクセスは、SharePoint Online によって生成されたトークンによって付与されます。</span><span class="sxs-lookup"><span data-stu-id="20269-457">Access to assets in private origins in the Office 365 CDN is granted by tokens generated by SharePoint Online.</span></span> <span data-ttu-id="20269-458">送信元によって指定されたフォルダーまたはライブラリへのアクセス許可を持っているユーザーには、アクセス許可レベルに基づいてファイルへのアクセスをユーザーに許可するトークンが自動的に与えられます。</span><span class="sxs-lookup"><span data-stu-id="20269-458">Users who already have permission to access to the folder or library designated by the origin are automatically granted tokens that permit the user to access the file based on their permission level.</span></span> <span data-ttu-id="20269-459">これらのアクセストークンは、トークンリプレイ攻撃を防ぐために生成されてから90分以内に有効になります。</span><span class="sxs-lookup"><span data-stu-id="20269-459">These access tokens are valid for 30 to 90 minutes after they are generated to help prevent token replay attacks.</span></span>

<span data-ttu-id="20269-460">アクセストークンが生成されると、SharePoint Online は、2つの承認パラメーター (エッジ認証__ トークン) と_oat_ (元の認証トークン) を含むクライアントにカスタム URI を返します。</span><span class="sxs-lookup"><span data-stu-id="20269-460">Once the access token is generated, SharePoint Online returns a custom URI to the client containing two authorization parameters _eat_ (edge authorization token) and _oat_ (origin authorization token).</span></span> <span data-ttu-id="20269-461">各トークンの構造は、「 _>__< ' secure signature ' >」の「< の有効期限 (エポック時間形式_)」です。</span><span class="sxs-lookup"><span data-stu-id="20269-461">The structure of each token is _<'expiration time in Epoch time format'>__<'secure signature'>_.</span></span> <span data-ttu-id="20269-462">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="20269-462">For example:</span></span>

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> <span data-ttu-id="20269-463">トークンを所有するすべてのユーザーが CDN 内のリソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="20269-463">Anyone in possession of the token can access the resource in the CDN.</span></span> <span data-ttu-id="20269-464">ただし、これらのアクセストークンを含む Url は HTTPS でのみ共有されるため、トークンの有効期限が切れる前にエンドユーザーが URL を明示的に共有しない限り、権限のないユーザーがアセットにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="20269-464">However, URLs containing these access tokens are only shared over HTTPS, so unless the URL is explicitly shared by an end user before the token expires, the asset won’t be accessible to unauthorized users.</span></span>

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a><span data-ttu-id="20269-465">アイテムレベルのアクセス許可は、プライベートな出所のアセットではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="20269-465">Item-level permissions are not supported for assets in private origins</span></span>

<span data-ttu-id="20269-466">SharePoint Online では、プライベートな出所のアセットに対してアイテムレベルのアクセス許可がサポートされていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="20269-466">It is important to note that SharePoint Online does not support item-level permissions for assets in private origins.</span></span> <span data-ttu-id="20269-467">たとえば、に`https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`あるファイルの場合、次の条件に該当するファイルへのアクセスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="20269-467">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, users have effective access to the file given the following conditions:</span></span>

|<span data-ttu-id="20269-468">ユーザー</span><span class="sxs-lookup"><span data-stu-id="20269-468">User</span></span>  |<span data-ttu-id="20269-469">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="20269-469">Permissions</span></span>  |<span data-ttu-id="20269-470">有効なアクセス</span><span class="sxs-lookup"><span data-stu-id="20269-470">Effective access</span></span>  |
|---------|---------|---------|
|<span data-ttu-id="20269-471">ユーザー1</span><span class="sxs-lookup"><span data-stu-id="20269-471">User 1</span></span>     |<span data-ttu-id="20269-472">Folder1 へのアクセス権</span><span class="sxs-lookup"><span data-stu-id="20269-472">Has access to folder1</span></span>         |<span data-ttu-id="20269-473">CDN から image1 にアクセスできる</span><span class="sxs-lookup"><span data-stu-id="20269-473">Can access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="20269-474">User 2</span><span class="sxs-lookup"><span data-stu-id="20269-474">User 2</span></span>     |<span data-ttu-id="20269-475">Folder1 へのアクセス権がありません。</span><span class="sxs-lookup"><span data-stu-id="20269-475">Does not have access to folder1</span></span>         |<span data-ttu-id="20269-476">CDN から image1 にアクセスできません</span><span class="sxs-lookup"><span data-stu-id="20269-476">Cannot access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="20269-477">ユーザー3</span><span class="sxs-lookup"><span data-stu-id="20269-477">User 3</span></span>     |<span data-ttu-id="20269-478">Folder1 にはアクセスできませんが、SharePoint Online で image1 にアクセスするための明示的なアクセス許可が付与されます。</span><span class="sxs-lookup"><span data-stu-id="20269-478">Does not have access to folder1, but is granted explicit permission to access image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="20269-479">SharePoint Online から直接アセット image1 にアクセスできますが、CDN からはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="20269-479">Can access the asset image1.jpg directly from SharePoint Online, but not from the CDN</span></span>         |
|<span data-ttu-id="20269-480">ユーザー4</span><span class="sxs-lookup"><span data-stu-id="20269-480">User 4</span></span>     |<span data-ttu-id="20269-481">Folder1 にはアクセスできますが、SharePoint Online で image1 へのアクセスを明示的に拒否されています。</span><span class="sxs-lookup"><span data-stu-id="20269-481">Has access to folder1, but has been explicitly denied access to image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="20269-482">SharePoint Online からアセットにアクセスすることはできませんが、SharePoint Online でのファイルへのアクセスが拒否されているにもかかわらず、CDN からアセットにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="20269-482">Cannot access the asset from SharePoint Online, but can access the asset from the CDN despite being denied access to the file in SharePoint Online</span></span>         |

## <a name="troubleshooting-the-office-365-cdn"></a><span data-ttu-id="20269-483">Office 365 CDN のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="20269-483">Troubleshooting the Office 365 CDN</span></span>
<span data-ttu-id="20269-484"><a name="CDNTroubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-484"></span></span>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a><span data-ttu-id="20269-485">アセットが CDN によって提供されていることを確認するにはどうすればよいですか?</span><span class="sxs-lookup"><span data-stu-id="20269-485">How do I confirm that assets are being served by the CDN?</span></span>
<span data-ttu-id="20269-486"><a name="CDNConfirm"> </a></span><span class="sxs-lookup"><span data-stu-id="20269-486"></span></span>

<span data-ttu-id="20269-487">CDN アセットへのリンクをページに追加すると、そのページを参照して、アセットが CDN から提供されていることを確認できます。これにより、イメージを表示した後、イメージの URL を表示して確認することができます。</span><span class="sxs-lookup"><span data-stu-id="20269-487">Once you have added links to CDN assets to a page, you can confirm that the asset is being served from the CDN by browsing to the page, right clicking on the image once it has rendered and reviewing the image URL.</span></span>

<span data-ttu-id="20269-488">また、ブラウザーの開発者ツールを使用して、ページ上の各アセットの URL を表示したり、サードパーティのネットワークトレースツールを使用したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="20269-488">You can also use your browser's developer tools to view the URL for each asset on a page, or use a 3rd party network trace tool.</span></span>

> [!NOTE]
> <span data-ttu-id="20269-489">Fiddler などのネットワークツールを使用して、SharePoint ページからアセットをレンダリングするのではない状態でアセットをテストする場合は、URL が SharePoint `https://yourdomain.sharepoint.com`Online テナントのルート url である GET 要求に、参照元のヘッダー "参照元" を手動で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20269-489">If you use a network tool such as Fiddler to test your assets outside of rendering the asset from a SharePoint page, you must manually add the referrer header “Referrer: `https://yourdomain.sharepoint.com`” to the GET request where the URL is the root URL of your SharePoint Online tenant.</span></span>

<span data-ttu-id="20269-490">SharePoint Online からの参照が必要になるため、web ブラウザーで CDN Url を直接テストすることはできません。</span><span class="sxs-lookup"><span data-stu-id="20269-490">You cannot test CDN URLs directly in a web browser because you must have a referrer coming from SharePoint Online.</span></span> <span data-ttu-id="20269-491">ただし、CDN アセット URL を SharePoint ページに追加し、そのページをブラウザーで開くと、CDN アセットがページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="20269-491">However, if you add the CDN asset URL to a SharePoint page and then open the page in a browser, you will see the CDN asset rendered on the page.</span></span>

<span data-ttu-id="20269-492">Microsoft Edge ブラウザーでの開発者ツールの使用の詳細については、「 [Microsoft Edge Developer tools](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20269-492">For more information on using the developer tools in the Microsoft Edge browser, see [Microsoft Edge Developer Tools](https://docs.microsoft.com/en-us/microsoft-edge/devtools-guide).</span></span>

### <a name="why-are-assets-from-a-new-origin-unavailable"></a><span data-ttu-id="20269-493">新しい配信元からのアセットが利用できないのはなぜですか?</span><span class="sxs-lookup"><span data-stu-id="20269-493">Why are assets from a new origin unavailable?</span></span>
<span data-ttu-id="20269-494">新しいオリジンにあるアセットは、登録が CDN 経由で伝達され、アセットを送信元から CDN ストレージにアップロードするのに時間がかかるため、すぐに使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="20269-494">Assets in new origins will not immediately be available for use, as it takes time for the registration to propagate through the CDN and for the assets to be uploaded from the origin to CDN storage.</span></span> <span data-ttu-id="20269-495">CDN でアセットを使用できるようになるために必要な時間は、アセットとファイルのサイズによって異なります。</span><span class="sxs-lookup"><span data-stu-id="20269-495">The time required for assets to be available in the CDN depends on how many assets and the files sizes.</span></span>

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a><span data-ttu-id="20269-496">クライアント側の web パーツまたは SharePoint Framework ソリューションが動作していない</span><span class="sxs-lookup"><span data-stu-id="20269-496">My client-side web part or SharePoint Framework solution isn't working</span></span>

<span data-ttu-id="20269-497">パブリックの配信元に対して Office 365 CDN を有効にすると、CDN サービスによってこれらの既定のオリジンが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="20269-497">When you enable the Office 365 CDN for public origins, the CDN service automatically creates these default origins:</span></span>

- <span data-ttu-id="20269-498">\*/マスターページ</span><span class="sxs-lookup"><span data-stu-id="20269-498">\*/MASTERPAGE</span></span>
- <span data-ttu-id="20269-499">\*/スタイルライブラリ</span><span class="sxs-lookup"><span data-stu-id="20269-499">\*/STYLE LIBRARY</span></span>
- <span data-ttu-id="20269-500">\*/Clientsideアセット</span><span class="sxs-lookup"><span data-stu-id="20269-500">\*/CLIENTSIDEASSETS</span></span>

<span data-ttu-id="20269-501">\*/Clientsideassets の送信元が見つからない場合、SharePoint Framework ソリューションは失敗し、警告やエラーメッセージは生成されません。</span><span class="sxs-lookup"><span data-stu-id="20269-501">If the \*/clientsideassets origin is missing, SharePoint Framework solutions will fail, and no warning or error messages are generated.</span></span> <span data-ttu-id="20269-502">このオリジンは、 _-nodefaultorigins_パラメーターが **$true**に設定されているか、または送信元が手動で削除されたために、CDN が有効になっていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="20269-502">This origin may be missing either because the CDN was enabled with the _-NoDefaultOrigins_ parameter set to **$true**, or because the origin was manually deleted.</span></span>

<span data-ttu-id="20269-503">\*/Clientsideassets の送信元が存在するかどうかは、次の PowerShell コマンドを使用して確認できます。</span><span class="sxs-lookup"><span data-stu-id="20269-503">You can check to see if the \*/CLIENTSIDEASSETS origin is present with the following PowerShell command:</span></span>

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="20269-504">または、Office 365 CLI を使用して確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="20269-504">Or you can check with the Office 365 CLI:</span></span>

``` powershell
spo cdn origin list
```

<span data-ttu-id="20269-505">PowerShell で送信元を追加するには:</span><span class="sxs-lookup"><span data-stu-id="20269-505">To add the origin in PowerShell:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="20269-506">Office 365 CLI で送信元を追加するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="20269-506">To add the origin in the Office 365 CLI:</span></span>

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a><span data-ttu-id="20269-507">Office 365 CDN を操作するために必要な PowerShell モジュールと CLI シェルは何ですか。</span><span class="sxs-lookup"><span data-stu-id="20269-507">What PowerShell modules and CLI shells do I need to work with the Office 365 CDN?</span></span>

<span data-ttu-id="20269-508">Office 365 CDN の操作は、 **SharePoint Online Management Shell** PowerShell モジュールまたは**office 365 CLI**のどちらかを使用して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="20269-508">You can choose to work with the Office 365 CDN using either the **SharePoint Online Management Shell** PowerShell module or the **Office 365 CLI**.</span></span>

- [<span data-ttu-id="20269-509">SharePoint Online 管理シェルの概要</span><span class="sxs-lookup"><span data-stu-id="20269-509">Getting started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
- [<span data-ttu-id="20269-510">Office 365 CLI のインストール</span><span class="sxs-lookup"><span data-stu-id="20269-510">Installing the Office 365 CLI</span></span>](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a><span data-ttu-id="20269-511">関連項目</span><span class="sxs-lookup"><span data-stu-id="20269-511">See also</span></span>

[<span data-ttu-id="20269-512">Content Delivery Network</span><span class="sxs-lookup"><span data-stu-id="20269-512">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="20269-513">Office 365 のネットワーク計画とパフォーマンス チューニング</span><span class="sxs-lookup"><span data-stu-id="20269-513">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

