---
title: Exchange Online のパフォーマンスをチューニングする
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/14/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: この資料には、一般的なヒントとオンラインの Exchange のパフォーマンスを向上させる方法については、その他のリソースへのリンクが含まれています。
ms.openlocfilehash: 20a3a61517212df88cb380ade47c268c429e52a8
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541879"
---
# <a name="tune-exchange-online-performance"></a><span data-ttu-id="f2429-103">Exchange Online のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="f2429-103">Tune Exchange Online performance</span></span>

<span data-ttu-id="f2429-p101">この資料には、一般的なヒントとオンラインの Exchange のパフォーマンスを向上させる方法については、その他のリソースへのリンクが含まれています。この資料は、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://aka.ms/tune)のプロジェクトの一部です。</span><span class="sxs-lookup"><span data-stu-id="f2429-p101">This article contains general tips and links to other resources that tell you how to improve performance of Exchange Online. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a><span data-ttu-id="f2429-106">Exchange のオンライン パフォーマンスを向上させるために考慮すべき事項</span><span class="sxs-lookup"><span data-stu-id="f2429-106">Things to consider in order to improve Exchange Online performance</span></span>

<span data-ttu-id="f2429-107">移行の速度が向上し、Exchange online 組織の帯域幅の制約を軽減、次の手順を検討します。</span><span class="sxs-lookup"><span data-stu-id="f2429-107">To improve the speed of migration and reduce your organization's bandwidth constraints for Exchange Online, consider the following:</span></span>
  
- <span data-ttu-id="f2429-p102">**メールボックスのサイズを減らす。** メールボックスのサイズが小さいと、移行速度が上昇します。</span><span class="sxs-lookup"><span data-stu-id="f2429-p102">**Reduce mailbox sizes.** Smaller mailbox size improves migration speed.</span></span> 
    
- <span data-ttu-id="f2429-p103">**Exchange のハイブリッド展開でメールボックスの移行機能を使用する。** Exchange ハイブリッド展開では、オフライン メール (.OST ファイル形式) は、Exchange Online への移行時に再ダウンロードを必要としません。これは大幅にダウンロード帯域幅の要件を軽減します。</span><span class="sxs-lookup"><span data-stu-id="f2429-p103">**Use the mailbox move capabilities with an Exchange hybrid deployment.** With an Exchange hybrid deployment, offline mail (in the form of .OST files) does not require re-download when migrating to Exchange Online. This significantly reduces your download bandwidth requirements.</span></span> 
    
- <span data-ttu-id="f2429-p104">**インターネット トラフィックが低く、オンプレミスの Exchange があまり使用されていない場合にメールボックスの移動が実行されるようにスケジュールする。** スケジュールの移動時に、移行要求がメールボックスのレプリケーション プロキシに送信されますが、すぐには実行されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="f2429-p104">**Schedule mailbox moves to occur during periods of low Internet traffic and low on-premises Exchange use.** When scheduling moves, migration requests are submitted to the mailbox replication proxy and may not take place immediately.</span></span> 
    
- <span data-ttu-id="f2429-p105">**Web 上で Outlook の無駄のない popouts を使用しています**。無駄のない popouts をサーバー上のいくつかのコンポーネントをレンダリングすることによってマイクロソフトのエッジまたは Internet Explorer で特定の電子メール メッセージのバージョンがメモリを消費するより小さい、提供します。詳細については、[メール メッセージを読むときに使用されるメモリを減らすために無駄のない popouts を使用して](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf)参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2429-p105">**Use lean popouts for Outlook on the web.** Lean popouts provide smaller, less memory-intensive versions of certain email messages in Microsoft Edge or Internet Explorer by rendering some components on the server. For more information, see [Use lean popouts to reduce memory used when reading mail messages](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).</span></span>
    
<span data-ttu-id="f2429-118">Exchange 移行時のパフォーマンスの詳細については、 [Office 365 移行時のパフォーマンスとベスト ・ プラクティス](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2429-118">For more information about Exchange migration performance, see [Office 365 migration performance and best practices](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).</span></span>
  

