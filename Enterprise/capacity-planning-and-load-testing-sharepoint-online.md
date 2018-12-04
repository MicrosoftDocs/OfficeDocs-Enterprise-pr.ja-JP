---
title: 容量計画および SharePoint Online のテスト負荷
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/18/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: この資料では、従来の負荷が許可されていないためにテストを実行することがなく SharePoint Online に展開する方法について説明します。
ms.openlocfilehash: 490d05598c42cd5d94f61dd21ee5a11701d4b4a7
ms.sourcegitcommit: 033156d46ac0fb5f05d2b1a594d5ef368b93b893
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2018
ms.locfileid: "27134672"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a><span data-ttu-id="cdf12-103">容量計画および SharePoint Online のテスト負荷</span><span class="sxs-lookup"><span data-stu-id="cdf12-103">Capacity planning and load testing SharePoint Online</span></span>

<span data-ttu-id="cdf12-104">この資料では、従来の負荷が推奨であるためにテストを実行することがなく SharePoint Online に展開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cdf12-104">This article describes how you can deploy to SharePoint Online without performing traditional load testing since it is strongly discouraged.</span></span>
  
<span data-ttu-id="cdf12-105">SharePoint Online でのテスト作業中の負荷は強くお勧めはことを確認する他の方法がありますが、サイトが生成されませんユーザー エクスペリエンスの低下、サイトを起動すると。</span><span class="sxs-lookup"><span data-stu-id="cdf12-105">Although active load testing on SharePoint Online is strongly discouraged, there are other ways you can make sure that a site will not produce a poor user experience when you launch the site.</span></span> 
  
<span data-ttu-id="cdf12-p101">SharePoint Online での当社のサービスの一部として、これは、キャパシティ ・ プランニングを実行するがありません。オンプレミス環境でロード テストを使用してスケールの前提データを検証し、最終的には、ファームの限界点を検索するには負荷が飽和にします。SharePoint Online では、異なる方法で処理を実行する必要があります。ロード テストを制限するに自動的には、同じファーム内のすべてのテナントを保護するためにあるマルチ テナント環境であります。これは、期待が表示され、ロードしようとした場合の潜在的に誤解を招く結果、環境のテストを意味します。</span><span class="sxs-lookup"><span data-stu-id="cdf12-p101">With SharePoint Online you don't have to do capacity planning, as this is done for you as part of our service offering. With on-premises environments, load testing is used to validate scale assumption and ultimately find the breaking point of a farm; by saturating it with load. With SharePoint Online we need to do things differently. Being a multi-tenant environment, we have to protect all tenants in the same farm, so we will automatically throttle any load tests. This means you will receive disappointing and potentially misleading results if you attempt to load test your environment.</span></span>
  
<span data-ttu-id="cdf12-p102">設置型の展開を SharePoint Online の主な利点の 1 つは、クラウドの弾力性です。処理容量効果的と必要なとき自動的にファームを展開すると、重要なので、大規模な環境が毎日のようにユーザーの数百万のサービスに設定されています。この資料では、容量の増加と拡張性の計画について説明場所に出力します。負荷テストが関係しないことを使用する方法についても取り上げています。</span><span class="sxs-lookup"><span data-stu-id="cdf12-p102">One of the main benefits of SharePoint Online over an on-premises deployment is the elasticity of the cloud. Our large scale environment is set up to service millions of users on a daily basis so it is important that we handle capacity effectively by automatically expanding farms, as and when needed. This article explains how we plan for capacity growth and scale out in place. The article also covers approaches for you to use that don't involve load testing.</span></span>
  
## <a name="how-office-365-predicts-load-and-expands-capacity"></a><span data-ttu-id="cdf12-115">Office 365 の負荷を予測して容量を拡張</span><span class="sxs-lookup"><span data-stu-id="cdf12-115">How Office 365 predicts load and expands capacity</span></span>

<span data-ttu-id="cdf12-116">サーバー容量の管理作業を SharePoint Online は、2 つの方法によって行われます。</span><span class="sxs-lookup"><span data-stu-id="cdf12-116">SharePoint Online server capacity management work is done through two methods:</span></span>
  
- <span data-ttu-id="cdf12-117">容量予測</span><span class="sxs-lookup"><span data-stu-id="cdf12-117">Capacity forecasting</span></span>
    
- <span data-ttu-id="cdf12-118">1 台のサーバー ファームの負荷分散</span><span class="sxs-lookup"><span data-stu-id="cdf12-118">Load-balancing on single server farms</span></span>
    
<span data-ttu-id="cdf12-p103">SharePoint online では、容量を予測するため、オンプレミス環境の計画とは異なり統計をコンパイルし、潜在的な要件を特定のサーバー グループをグラフ化することがします。集計の需要のようになります要求 (ゾーンは、SharePoint ファームのグループ) のゾーンの下の画像のラインを拡張。</span><span class="sxs-lookup"><span data-stu-id="cdf12-p103">Unlike planning for an on-premises environment, for capacity forecasting in SharePoint Online, we are able to compile statistics and graph potential requirements in any given server group. The aggregate demand might look something like the Requests in zone (where a zone is a group of SharePoint farms) growth line in the image below:</span></span>
  
![容量の予測を示すグラフ:予測](media/ca800cb6-cc59-451f-98bd-55e035489af3.png)
  
<span data-ttu-id="cdf12-p104">増加が予測可能なすべて 1 つのファームで、集約されたゾーン内の要求の合計は、予測です。SharePoint Online で増加の傾向を識別するには、将来の拡張計画はできます。</span><span class="sxs-lookup"><span data-stu-id="cdf12-p104">While the growth is unpredictable in any one farm, the aggregated sum of requests in a zone is predictable. By identifying the growth trends in SharePoint Online, we can plan for future expansion.</span></span>
  
<span data-ttu-id="cdf12-p105">効率的に容量を使用し、すべてのファームでの予期しない増加に対処するためにフロント エンドの負荷を追跡し、必要な場合に、インプレースでは、スケール アップの自動化があります。事前に拡大または縮小する信号の終了を使用して主要なメトリックは、CPU の負荷です。私たちの目標は、ピーク時の CPU 負荷 40% 未満を維持します。予期しないスパイクを吸収するための十分なバッファーがあるためです。として安定した状態での負荷のアプローチの 40%、ファームにフロント エンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="cdf12-p105">In order to efficiently use capacity and deal with unexpected growth, in any farm, we have automation that tracks front-end load and scales up in place, when needed. The main metric we use as a signal to scale up front ends is CPU load. Our goal is to keep peak CPU load under 40%. This is in order to have enough buffer to absorb unexpected spikes. As load approaches 40% in steady state, we add front ends to farms.</span></span>
  
![容量の予測を示すグラフ:ファームの管理](media/6b2a8c63-24c1-4504-b7a3-3d3b3be2583a.png)
  
<span data-ttu-id="cdf12-130">使用率の予測を使用してゾーンをあらかじめ追加しているものを使用して、ファームに追加のサーバーをすばやく追加できます。</span><span class="sxs-lookup"><span data-stu-id="cdf12-130">Additional servers can be quickly added to a farm, using those which have been previously added to the zone through the usage forecast.</span></span> 
  
## <a name="how-do-i-plan-for-a-site-launch"></a><span data-ttu-id="cdf12-131">サイトの起動を計画する方法は?</span><span class="sxs-lookup"><span data-stu-id="cdf12-131">How do I plan for a site launch?</span></span>

<span data-ttu-id="cdf12-p106">ファームの新しいサイトを起動する自動的を監視するように、新しいフロント エンド サーバーを追加すると、上記で説明したはずです。このため、すべての通知、新しいサイトの起動の必要はありません。</span><span class="sxs-lookup"><span data-stu-id="cdf12-p106">You should expect that the farm on which your new site launches will automatically be monitored so that new front-end servers are added, as described above. For this reason, we don't need any notification for your new site launch.</span></span>
  
<span data-ttu-id="cdf12-134">SharePoint Online で特定のページでは他のベスト プラクティスに従って、100,000 人ものユーザーに、新しいサイト起動が、影響をファームする必要がある可能性が高いことはできません。</span><span class="sxs-lookup"><span data-stu-id="cdf12-134">Following other best practices for a single page on SharePoint Online it is unlikely that a new site launch to even 100,000 users will have any impact to the farm.</span></span>
  
<span data-ttu-id="cdf12-p107">新しい SharePoint Online サイトのリリースを計画するのには、いくつかの戦略があります。次の図のように、多くの場合、招待されたユーザーは、サイトを実際に使用されるものよりも大幅に高いです。このイメージは、リリースを展開する方法についての戦略を示しています。このメソッドは、読み込みのパフォーマンスでは、だけでなくもことができます、ユーザーの大多数はそれを参照してください前に、SharePoint サイトを改善する方法を識別します。</span><span class="sxs-lookup"><span data-stu-id="cdf12-p107">There are a few strategies to plan for a release of a new SharePoint Online site. As shown in the following image, often the amount of users that are invited is significantly higher than those that actually use the site. This image shows a strategy about how to roll out a release. This method not only helps with performance loading but also can help identify ways to improve the SharePoint site before the large majority of the users see it.</span></span>
  
![招待ユーザーとアクティブなユーザーを示すグラフ](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
<span data-ttu-id="cdf12-p108">パイロット フェーズでは、組織を信頼し、実施が認識していることにユーザーからフィードバックを取得することをお勧めします。この方法、システムの使用状況、それを実行する方法を判断することです。</span><span class="sxs-lookup"><span data-stu-id="cdf12-p108">In the pilot phase, it is good to get feedback from users that the organization trusts and knows will be engaged. This way it is possible to gauge how the system is being used, as well as how it is performing.</span></span>
  
<span data-ttu-id="cdf12-p109">その後、波はのすべてのユーザーにロール アウトを開始しますフィードバックを得ることと、パフォーマンスを定期的に確認します。ゆっくりシステムを導入することと、システムは複数の使用を取得するように改善をすることの利点があります。サイトがますます多くのユーザーにロールアウトに負荷の増大に対応することもできます。</span><span class="sxs-lookup"><span data-stu-id="cdf12-p109">After this, begins a roll out to all users in waves; getting feedback and reviewing the performance regularly. This has the advantage of slowly introducing the system and making improvements as the system gets more use. This also allows us to react to the increased load as the site is rolled out to more and more users.</span></span>
  
<span data-ttu-id="cdf12-p110">最後に、禁止されているロード テスト中に、お客様は、サービス可用性を測定し、待機時間に定期的な ping を設定する必要があります。これは、自分のサイト用のベースラインを識別します。ただし、調整の前に説明した問題を回避するのには低周波数にこれら保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cdf12-p110">Finally, while load tests are prohibited, customers may want to set up periodical pings to the service to measure availability and latency. This will identify a baseline for their site. However, these must be kept to low frequency to avoid throttling issues previously described.</span></span>
  

