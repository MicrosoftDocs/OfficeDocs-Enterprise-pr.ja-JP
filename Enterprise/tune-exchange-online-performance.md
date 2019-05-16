---
title: Exchange Online のパフォーマンスをチューニングする
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: この記事には、Exchange Online のパフォーマンスを向上させる方法を説明する一般的なヒントとその他のリソースへのリンクが含まれています。
ms.openlocfilehash: d736568687da5ffe0ebed5a57a6afa6f93173c54
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070353"
---
# <a name="tune-exchange-online-performance"></a><span data-ttu-id="809f1-103">Exchange Online のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="809f1-103">Tune Exchange Online performance</span></span>

<span data-ttu-id="809f1-104">この記事では、特に移行の前に Exchange Online のパフォーマンスを向上させる方法を説明する一般的なヒントとその他のリソースへのリンクを掲載しています。</span><span class="sxs-lookup"><span data-stu-id="809f1-104">This article contains general tips and links to other resources that tell you how to improve performance of Exchange Online, particularly in front of a migration.</span></span> <span data-ttu-id="809f1-105">この記事は、 [Office 365 プロジェクトのネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)に含まれています。</span><span class="sxs-lookup"><span data-stu-id="809f1-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a><span data-ttu-id="809f1-106">Exchange Online のパフォーマンスを向上させるための考慮事項</span><span class="sxs-lookup"><span data-stu-id="809f1-106">Things to consider in order to improve Exchange Online performance</span></span>

<span data-ttu-id="809f1-107">移行速度を向上させ、Exchange Online の帯域幅制限を減らすには、次の点を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="809f1-107">To improve the speed of migration and reduce your organization's bandwidth constraints for Exchange Online, consider the following:</span></span>
  
- <span data-ttu-id="809f1-108">**メールボックスのサイズを小さくします。**</span><span class="sxs-lookup"><span data-stu-id="809f1-108">**Reduce mailbox sizes.**</span></span> <span data-ttu-id="809f1-109">メールボックスのサイズが小さくなると、移行速度が向上します。</span><span class="sxs-lookup"><span data-stu-id="809f1-109">Smaller mailbox size improves migration speed.</span></span> 
    
- <span data-ttu-id="809f1-110">**Exchange ハイブリッド展開でメールボックスの移動機能を使用します。**</span><span class="sxs-lookup"><span data-stu-id="809f1-110">**Use the mailbox move capabilities with an Exchange hybrid deployment.**</span></span> <span data-ttu-id="809f1-111">Exchange ハイブリッド展開では、オフラインメール (の形式) を使用します。OST ファイル) は、Exchange Online に移行するときに再ダウンロードする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="809f1-111">With an Exchange hybrid deployment, offline mail (in the form of .OST files) does not require re-download when migrating to Exchange Online.</span></span> <span data-ttu-id="809f1-112">これにより、ダウンロード帯域幅の要件を大幅に削減できます。</span><span class="sxs-lookup"><span data-stu-id="809f1-112">This significantly reduces your download bandwidth requirements.</span></span> 
    
- <span data-ttu-id="809f1-113">**メールボックスの移動は、インターネットトラフィックが少ない時間帯やオンプレミスの Exchange の使用中に発生するようにスケジュールします。**</span><span class="sxs-lookup"><span data-stu-id="809f1-113">**Schedule mailbox moves to occur during periods of low Internet traffic and low on-premises Exchange use.**</span></span> <span data-ttu-id="809f1-114">移動をスケジュールするとき、メールボックスレプリケーションプロキシに移行要求が送信され、すぐには実行されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="809f1-114">When scheduling moves, migration requests are submitted to the mailbox replication proxy and may not take place immediately.</span></span> 
    
- <span data-ttu-id="809f1-115">**Web 上の Outlook のリーンポップアウトを使用します。**</span><span class="sxs-lookup"><span data-stu-id="809f1-115">**Use lean popouts for Outlook on the web.**</span></span> <span data-ttu-id="809f1-116">リーンポップアウトは、サーバー上にいくつかのコンポーネントをレンダリングすることによって、Microsoft Edge または Internet Explorer で特定の電子メールメッセージのより小さなメモリを消費するバージョンを少なくします。</span><span class="sxs-lookup"><span data-stu-id="809f1-116">Lean popouts provide smaller, less memory-intensive versions of certain email messages in Microsoft Edge or Internet Explorer by rendering some components on the server.</span></span> <span data-ttu-id="809f1-117">詳細については、「[リーンポップアウトを使用してメールメッセージの読み取り時に使用されるメモリを減らす](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="809f1-117">For more information, see [Use lean popouts to reduce memory used when reading mail messages](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span></span>


## <a name="general-advice"></a><span data-ttu-id="809f1-118">一般的なアドバイス</span><span class="sxs-lookup"><span data-stu-id="809f1-118">General advice</span></span>

- <span data-ttu-id="809f1-119">Outlook.office.com の DNS 参照が、場所の論理的なエントリの場所で MS データセンターに入力されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="809f1-119">Make certain that DNS lookup for outlook.office.com enters the MS-datacenter at a logical entry location for your location.</span></span>

- <span data-ttu-id="809f1-120">メールボックスのキャッシュを調査し、適切なオプション (re を選択します。</span><span class="sxs-lookup"><span data-stu-id="809f1-120">Research mailbox caching and choose the appropriate options (re.</span></span> <span data-ttu-id="809f1-121">キャッシュ期間、共有メールボックスのキャッシュ、et cetera)。</span><span class="sxs-lookup"><span data-stu-id="809f1-121">caching period, shared mailbox caching, et cetera).</span></span>

- <span data-ttu-id="809f1-122">インターネット経由に移行する前に、Outlook データが VPN 接続 (中央オフィスへ) を通過しないようにします。</span><span class="sxs-lookup"><span data-stu-id="809f1-122">Keep your Outlook data from passing over VPN connections (to a central office) before it goes over the Internet.</span></span>

- <span data-ttu-id="809f1-123">メールボックスデータがフォルダー、アイテム、量の制限に準拠していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="809f1-123">Be sure your mailbox data adheres to the limitations on folder, and item, amounts.</span></span>
    
<span data-ttu-id="809f1-124">Exchange の移行のパフォーマンスの詳細については、「 [Office 365 移行のパフォーマンスとベストプラクティス](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="809f1-124">For more information about Exchange migration performance, see [Office 365 migration performance and best practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span></span>
  

