---
title: SharePoint Server 2007 のサポート終了ロードマップ
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: conceptual
f1_keywords:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: SharePoint Server 2007 のサポートは 2017 年 10 月 10 日に終了しました。アップグレード オプション、トラブルシューティング、ベスト プラクティス、システム要件、アップグレード手順、および Microsoft パートナーからサポートを受ける方法については、この記事をお読みください。
ms.openlocfilehash: b548e7623a72d57793c18409a80506bb832df858
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169799"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a><span data-ttu-id="ede6a-104">SharePoint Server 2007 のサポート終了ロードマップ</span><span class="sxs-lookup"><span data-stu-id="ede6a-104">SharePoint Server 2007 end of support roadmap</span></span>

<span data-ttu-id="ede6a-p102">Microsoft Office SharePoint Server 2007 のサポートは **2017 年 10 月 10 日**に終了しました。SharePoint Server 2007 から Office 365 またはオンプレミスの新しいバージョンの SharePoint Server への移行を開始していない場合は、今すぐ移行を実施する必要があります。この記事では、ユーザーが SharePoint Online にデータを移行したり、オンプレミスの SharePoint Server をアップグレードしたりする際に役立つリソースについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p102">On **October 10, 2017**, Microsoft Office SharePoint Server 2007 reached end of support. If you haven't begun your migration from SharePoint Server 2007 to Office 365 or a newer version of SharePoint Server on-premises, now's the time to start planning. This article details resources to help people migrate data to SharePoint Online, or upgrade your SharePoint Server on-premises.</span></span> 
  
## <a name="what-does-end-of-support-mean"></a><span data-ttu-id="ede6a-108">サポートが終了するとどうなるのか</span><span class="sxs-lookup"><span data-stu-id="ede6a-108">What does end of support mean?</span></span>

<span data-ttu-id="ede6a-p103">ほとんどの Microsoft 製品と同様に、SharePoint Server にはサポート ライフサイクルがあり、該当期間内に Micosoft は新しい機能、バグ修正プログラム、セキュリティ修正プログラムなどを提供しています。このライフサイクルは通常、製品の最初のリリース日から 10 年間続きます。このライフサイクルが終わると、製品のサポートも終了となります。サポートが終了すると、以下のものが提供されなくなります。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p103">SharePoint Server, like almost all Microsoft products, has a support lifecycle during which Microsoft provides new features, bug fixes, security fixes, and so on. This lifecycle typically lasts for 10 years from the date of the product's initial release, and the end of this lifecycle is known as the product's end of support. At end of support, Microsoft no longer provides:</span></span>
  
- <span data-ttu-id="ede6a-112">発生する可能性のある問題のテクニカル サポート。</span><span class="sxs-lookup"><span data-stu-id="ede6a-112">Technical support for problems that may occur;</span></span>
    
- <span data-ttu-id="ede6a-113">サーバーの安定性と運用に影響を与える可能性のある問題が検出された場合のバグ修正プログラム。</span><span class="sxs-lookup"><span data-stu-id="ede6a-113">Bug fixes for issues that are discovered and that may impact the stability and usability of the server;</span></span>
    
- <span data-ttu-id="ede6a-114">セキュリティ違反に対するサーバーの精度を低下させるような脆弱性が検出された場合のセキュリティ修正プログラム。</span><span class="sxs-lookup"><span data-stu-id="ede6a-114">Security fixes for vulnerabilities that are discovered and that may make the server vulnerable to security breaches; and</span></span> 
    
- <span data-ttu-id="ede6a-115">タイム ゾーンの更新。</span><span class="sxs-lookup"><span data-stu-id="ede6a-115">Time zone updates.</span></span>
    
<span data-ttu-id="ede6a-p104">2017 年 10 月 10 日以降も、SharePoint Server 2007 ファームは引き続き稼働しますが、製品の更新プログラム、パッチ、修正プログラム (セキュリティのパッチや修正プログラムも含む) のサポートは行われません。Microsoft サポートによるサポート対象も製品の最新バージョンに切り替わります。製品のサポートが終了すると、パッチなどのサポートの対象外となるため、製品をアップグレードするか、重要なデータを移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p104">Though your SharePoint Server 2007 farm will still be operational after October 10, 2017, no further updates, patches, or fixes will be shipped for the product (including security patches/fixes), and Microsoft Support will have fully shifted its support efforts to more recent versions of the product. Because your installation will no longer supported or patched, as end of support approaches you should upgrade the product, or migrate important data.</span></span>
  
> [!TIP]
> <span data-ttu-id="ede6a-p105">アップグレードまたは移行の計画をまだ行っていない場合は、「[考慮すべき SharePoint 2007 の移行オプション](sharepoint-2007-migration-options.md)」で、実施すべき作業の例を参照してください。アップグレードまたは Office 365 の移行 (あるいはその両方) を支援する [Microsoft パートナー](https://go.microsoft.com/fwlink/?linkid=841249)を検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p105">If you haven't already planned for upgrade or migration, please see: [SharePoint 2007 migration options to consider](sharepoint-2007-migration-options.md), for some examples of where to begin. You can also search for [Microsoft Partners](https://go.microsoft.com/fwlink/?linkid=841249) who can help with upgrade or Office 365 migration (or both).</span></span> 
  
<span data-ttu-id="ede6a-120">Office 2007 のサーバーのサポート終了の詳細については、「[Office 2007 のサーバーのアップグレードを計画する](https://support.office.com/article/4e5eab5f-05db-4627-9e17-421a6bf89606.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ede6a-120">For more information about Office 2007 servers reaching the end of support, see [Plan your upgrade for Office 2007 servers](https://support.office.com/article/4e5eab5f-05db-4627-9e17-421a6bf89606.aspx).</span></span>
  
## <a name="what-are-my-options"></a><span data-ttu-id="ede6a-121">使用できるオプション</span><span class="sxs-lookup"><span data-stu-id="ede6a-121">What are my options?</span></span>

<span data-ttu-id="ede6a-p106">まず、[製品のライフサイクルのサイト](https://go.microsoft.com/fwlink/?linkid=843148)にアクセスします。オンプレミスの古い Microsoft 製品を使用している場合は、サポート終了日を確認する必要があります。そうすれば、1 年ほどでサポートが終わる、あるいは、一般的に移行が必要とされる限度などを考慮に入れて、アップグレードまたは移行のスケジュールを立てることができます。次の手順を選ぶときには、製品機能に関して段階的 (標準、良い、最良の 3 段階) に検討すると良いでしょう。以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p106">Your first stop should be the [Product Lifecycle site](https://go.microsoft.com/fwlink/?linkid=843148). If you have an on-premises Microsoft product that is aging, you should check for its end of support date so that, a year or so out - or as long as your migrations generally require - you can schedule upgrade or migrations. When choosing the next step, it might help to think in terms of what would be good enough, better, and best when it comes to product features. Here's an example:</span></span>
  
|<span data-ttu-id="ede6a-126">**標準**</span><span class="sxs-lookup"><span data-stu-id="ede6a-126">**Good**</span></span>|<span data-ttu-id="ede6a-127">**良い**</span><span class="sxs-lookup"><span data-stu-id="ede6a-127">**Better**</span></span>|<span data-ttu-id="ede6a-128">**最良**</span><span class="sxs-lookup"><span data-stu-id="ede6a-128">**Best**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="ede6a-129">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="ede6a-129">SharePoint Server 2010</span></span>  <br/> |<span data-ttu-id="ede6a-130">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="ede6a-130">SharePoint Server 2013</span></span>  <br/> |<span data-ttu-id="ede6a-131">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="ede6a-131">SharePoint Online</span></span>  <br/> |
||<span data-ttu-id="ede6a-132">SharePoint ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="ede6a-132">SharePoint Hybrid</span></span>  <br/> |<span data-ttu-id="ede6a-133">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="ede6a-133">SharePoint Server 2016</span></span>  <br/> |
|||<span data-ttu-id="ede6a-134">SharePoint ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="ede6a-134">SharePoint Hybrid</span></span>  <br/> |
   
<span data-ttu-id="ede6a-p107">終了までの期間が短い (標準) オプションを選択した場合は、SharePoint Server 2007 からの移行が完了したらすぐにアップグレードの計画を立てる必要があります。(SharePoint Server 2007 のサポート終了日は 2017 年 10 月 10 日ですが、この日付は変更される可能性がありますので、[製品のライフサイクルのサイト](https://support.microsoft.com/ja-JP/lifecycle)を確認するようにしてください。)</span><span class="sxs-lookup"><span data-stu-id="ede6a-p107">If you choose options on the low end of the scale (good enough), remember you will need to begin planning for upgrade very soon after migration from SharePoint Server 2007 is complete. (end of support for SharePoint Server 2007 is October 10, 2017. Please note that these dates are subject to change and check the [Product Lifecycle site](https://support.microsoft.com/ja-JP/lifecycle).)</span></span>
  
## <a name="where-can-i-go-next"></a><span data-ttu-id="ede6a-138">次に行う操作</span><span class="sxs-lookup"><span data-stu-id="ede6a-138">Where can I go next?</span></span>

<span data-ttu-id="ede6a-p108">SharePoint Server は、オンプレミスの自分のサーバー上にインストールすることができます。あるいは、Microsoft Office 365 の一部を成すオンライン サービスである SharePoint Online を使用できます。以下を選択することができます。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p108">SharePoint Server can be installed on-premises on your own servers, or you can use SharePoint Online, which is an online service that is part of Microsoft Office 365. You can choose to:</span></span>
  
- <span data-ttu-id="ede6a-141">SharePoint Online への移行</span><span class="sxs-lookup"><span data-stu-id="ede6a-141">Migrate  to SharePoint Online</span></span>
    
- <span data-ttu-id="ede6a-142">オンプレミスの SharePoint Server のアップグレード</span><span class="sxs-lookup"><span data-stu-id="ede6a-142">Upgrade SharePoint Server on-premises</span></span>
    
- <span data-ttu-id="ede6a-143">上記の両方の実施</span><span class="sxs-lookup"><span data-stu-id="ede6a-143">Do both of the above</span></span>
    
- <span data-ttu-id="ede6a-144">[SharePoint ハイブリッド](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) ソリューションの実装</span><span class="sxs-lookup"><span data-stu-id="ede6a-144">Implement a [SharePoint hybrid](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) solution</span></span> 
    
<span data-ttu-id="ede6a-p109">サーバー ファームの管理、カスタマイズの保守や移行、および SharePoint Server が依存するハードウェアのアップグレードには、関連する潜在的コストが発生しますので、ご注意ください。オンプレミスの SharePoint Server ファームが必要な場合、このファームを使用することには価値があります。一方、大幅なカスタマイズをせずに、従来の SharePoint Server でファームを実行している場合は、SharePoint Online への計画的な移行から益を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p109">Be aware of hidden costs associated with maintaining a server farm going forward, maintaining or migrating customizations, and upgrading the hardware upon which SharePoint Server depends. Having an on-premises SharePoint Server farm is rewarding if it is a necessity; otherwise, if you run your farm on legacy SharePoint Servers, without heavy customization, you can benefit from a planned migration to SharePoint Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="ede6a-p110">SharePoint 2007 のコンテンツを頻繁に使用しない場合は、別のオプションを使用できます。一部の SharePoint 管理者は、[Office 365 サブスクリプションを作成](https://go.microsoft.com/fwlink/?linkid=843152)し、新しい SharePoint Online サイトをセットアップすることを選択するかもしれません。新しい SharePoint Online サイトに必要なドキュメントのみが取り入れられた、完全に独立したサイトとなり、SharePoint 2007 からは切り離されます。そしてデータは、SharePoint 2007 サイトからアーカイブに排出することができます。SharePoint 2007 インストールでのデータの操作方法については、ユーザーが検討します。この問題を解決する創造的な方法が登場することでしょう。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p110">There is another option if the content in SharePoint 2007 is infrequently used. Some SharePoint Administrators may choose to [create an Office 365 Subscription](https://go.microsoft.com/fwlink/?linkid=843152), set up a brand new SharePoint Online site, and then cut away from SharePoint 2007, cleanly, taking only the most essential documents to the fresh SharePoint Online sites. From there, data may be drained from the SharePoint 2007 site into archives. Give thought to how users work with data your SharePoint 2007 installation. There may be creative ways to resolve this problem!</span></span> 
  
|<span data-ttu-id="ede6a-152">**SharePoint Online (SPO)**</span><span class="sxs-lookup"><span data-stu-id="ede6a-152">**SharePoint Online (SPO)**</span></span>|<span data-ttu-id="ede6a-153">**オンプレミスの SharePoint Server**</span><span class="sxs-lookup"><span data-stu-id="ede6a-153">**SharePoint Server on-premises**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ede6a-154">時間コストが高い (計画 / 実行 / 確認)</span><span class="sxs-lookup"><span data-stu-id="ede6a-154">High cost in time (plan / execution / verification)</span></span>  <br/> |<span data-ttu-id="ede6a-155">時間コストが高い (計画 / 実行 / 確認)</span><span class="sxs-lookup"><span data-stu-id="ede6a-155">High cost in time (plan / execution / verification)</span></span>  <br/> |
|<span data-ttu-id="ede6a-156">資金コストが安い (ハードウェアの購入の必要なし)</span><span class="sxs-lookup"><span data-stu-id="ede6a-156">Lower cost in funds (no hardware purchases)</span></span>  <br/> |<span data-ttu-id="ede6a-157">資金コストが高い (ハードウェア + 開発/管理者)</span><span class="sxs-lookup"><span data-stu-id="ede6a-157">Higher cost in funds (hardware + devs / admins)</span></span>  <br/> |
|<span data-ttu-id="ede6a-158">一度の移行でのコスト</span><span class="sxs-lookup"><span data-stu-id="ede6a-158">One-time cost in migration</span></span>  <br/> |<span data-ttu-id="ede6a-159">将来繰り返される一度の移行でのコスト</span><span class="sxs-lookup"><span data-stu-id="ede6a-159">One-time cost repeated per future migration</span></span>  <br/> |
|<span data-ttu-id="ede6a-160">所有権および保守の費用合計が低い</span><span class="sxs-lookup"><span data-stu-id="ede6a-160">Low total cost of ownership / maintenance</span></span>  <br/> |<span data-ttu-id="ede6a-161">所有権および保守の費用合計が高い</span><span class="sxs-lookup"><span data-stu-id="ede6a-161">High total cost of ownership / maintenance</span></span>  <br/> |
   
<span data-ttu-id="ede6a-p111">Office 365 に移行する場合、データを整理して、クラウドに取り入れるべきものと残すべきものを決定しますが、一度の移行ではコストがかかります。ただし、移行の時点からアップグレードが自動的に行われるため、ハードウェアとソフトウェアの更新を管理する必要はなくなり、ファームの稼働時間は Microsoft サービス レベル契約 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) に基づいたものとなります。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p111">When you migrate to Office 365, the one-time move will have a heavier cost up-front, while you're organizing data and deciding what to take to the cloud and what to leave behind. However, upgrades will be automatic from that point, you will no longer need to manage hardware and software updates, and the up-time of your farm will be backed by a Microsoft Service Level Agreement ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)).</span></span>
  
### <a name="migrate-to-sharepoint-online"></a><span data-ttu-id="ede6a-164">SharePoint Online への移行</span><span class="sxs-lookup"><span data-stu-id="ede6a-164">Migrate  to SharePoint Online</span></span>

<span data-ttu-id="ede6a-p112">関連するサービスの説明を確認し、SharePoint Online に必要なすべての機能が備わっていることを確認してください。以下のリンクをクリックすると、Office 365 サービスのすべての説明を確認できます。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p112">Make sure that SharePoint Online has all the features you need by reviewing the associated service description. Here's the link to all Office 365 Service Descriptions:</span></span>
  
[<span data-ttu-id="ede6a-167">Office 365 サービスの説明</span><span class="sxs-lookup"><span data-stu-id="ede6a-167">Office 365 Service Descriptions</span></span>](https://go.microsoft.com/fwlink/?linkid=272060)
  
<span data-ttu-id="ede6a-p113">SharePoint 2007 から SharePoint Online に直接移行する方法はありません。SharePoint Online への移行は手動で行います。SharePoint Server 2013 または SharePoint Server 2016 にアップグレードする際には、SharePoint 移行 API の使用が必要になる場合があります (OneDrive for Business への情報の移行などのため)。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p113">There is no direct way to migrate from SharePoint 2007 to SharePoint Online; your move to SharePoint Online would be done manually. If you upgrade to SharePoint Server 2013 or SharePoint Server 2016, your move might also involve using the SharePoint Migration API (to migrate information into OneDrive for Business, for example).</span></span>
  
|<span data-ttu-id="ede6a-170">**オンラインの利点**</span><span class="sxs-lookup"><span data-stu-id="ede6a-170">**Online Pro**</span></span>|<span data-ttu-id="ede6a-171">**オンラインの欠点**</span><span class="sxs-lookup"><span data-stu-id="ede6a-171">**Online Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ede6a-172">Microsoft が SPO ハードウェアおよびすべてのハードウェアの管理を行う。</span><span class="sxs-lookup"><span data-stu-id="ede6a-172">Microsoft supplies SPO hardware and all hardware administration.</span></span>  <br/> |<span data-ttu-id="ede6a-173">オンプレミスの SharePoint Server で利用できる機能と、SPO で利用できる機能が異なる。</span><span class="sxs-lookup"><span data-stu-id="ede6a-173">Available features may be different between SharePoint Server on-premises and SPO.</span></span>  <br/> |
|<span data-ttu-id="ede6a-174">サブスクリプションの全体管理者であると、SPO サイトに管理者を割り当てることができる。</span><span class="sxs-lookup"><span data-stu-id="ede6a-174">You are the global administrator of your subscription, and may assign administrators to SPO sites.</span></span>  <br/> |<span data-ttu-id="ede6a-175">オンプレミスの SharePoint Server のファーム管理者が使用できる操作の一部が、Office 365 の SharePoint 管理者ロールに含まれない (または必要ない)。</span><span class="sxs-lookup"><span data-stu-id="ede6a-175">Some actions available to a Farm Administrator in SharePoint Server on-premises do not exist (or are not necessary) included in the SharePoint Administrator role in Office 365.</span></span>  <br/> |
|<span data-ttu-id="ede6a-176">Microsoft が、基になるハードウェアとソフトウェアに、パッチ、修正プログラム、更新プログラムを適用する。</span><span class="sxs-lookup"><span data-stu-id="ede6a-176">Microsoft applies patches, fixes and updates to underlying hardware and software.</span></span>  <br/> |<span data-ttu-id="ede6a-177">サービスの基となるファイル システムへのアクセスがないため、一部のカスタマイズが制限される。</span><span class="sxs-lookup"><span data-stu-id="ede6a-177">Because there is no access to the underlying file system in the service, some customizations are limited.</span></span>  <br/> |
|<span data-ttu-id="ede6a-178">Microsoft が[サービス レベル契約](https://go.microsoft.com/fwlink/?linkid=843153)を発行し、サービス レベルの問題に迅速に対応する。</span><span class="sxs-lookup"><span data-stu-id="ede6a-178">Microsoft publishes [Service Level Agreements](https://go.microsoft.com/fwlink/?linkid=843153) and moves quickly to resolve service level incidents.</span></span>  <br/> |<span data-ttu-id="ede6a-179">バックアップと復元、その他の回復オプションは、SharePoint Online のサービスによって自動化される。バックアップは、使用されていない場合に上書きされる。</span><span class="sxs-lookup"><span data-stu-id="ede6a-179">Backup and restore and other recovery options are automated by the service in SharePoint Online - backups are overwritten if not used.</span></span>  <br/> |
|<span data-ttu-id="ede6a-180">セキュリティ テストとサーバーのパフォーマンス チューニングは、Microsoft によって、継続的なサービスとして実施される。</span><span class="sxs-lookup"><span data-stu-id="ede6a-180">Security testing and server performance tuning are carried out on an ongoing basis in the service by Microsoft.</span></span>  <br/> |<span data-ttu-id="ede6a-181">ユーザー インターフェイスとその他の SharePoint 機能の変更はサービスによってインストールされ、オン/オフの切り替えが必要な場合がある。</span><span class="sxs-lookup"><span data-stu-id="ede6a-181">Changes to the user interface and other SharePoint features are installed by the service and may need to be toggled on or off.</span></span>  <br/> |
|<span data-ttu-id="ede6a-182">Office 365 が、[Office 365 のコンプライアンス](https://go.microsoft.com/fwlink/?linkid=843165)に記載されている多くの業界標準に対応している。</span><span class="sxs-lookup"><span data-stu-id="ede6a-182">Office 365 meets many industry standards: [Office 365 Compliance](https://go.microsoft.com/fwlink/?linkid=843165).</span></span>  <br/> |<span data-ttu-id="ede6a-183">移行の際に [FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) でできることが限られる。</span><span class="sxs-lookup"><span data-stu-id="ede6a-183">[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) assistance for migration is limited.</span></span>  <br/> <span data-ttu-id="ede6a-184">アップグレードの多くは、手動か、[SharePoint Online と OneDrive 移行コンテンツ ロードマップ](https://go.microsoft.com/fwlink/?linkid=843184)に記載されている SPO 移行 API により実施される。</span><span class="sxs-lookup"><span data-stu-id="ede6a-184">Much of the upgrade will be manual, or via the SPO Migration API described in the [SharePoint Online and OneDrive Migration Content Roadmap](https://go.microsoft.com/fwlink/?linkid=843184).</span></span>  <br/> |
|<span data-ttu-id="ede6a-185">Microsoft のサポート エンジニアもデータセンターの従業員も、ユーザーのサブスクリプションに対する無制限の管理アクセス権はない。</span><span class="sxs-lookup"><span data-stu-id="ede6a-185">Neither Microsoft Support Engineers nor employees in the datacenter have unrestricted admin access to your subscription.</span></span>  <br/> |<span data-ttu-id="ede6a-186">新しいバージョンの SharePoint に対応するために、ハードウェア インフラストラクチャをアップグレードする必要がある場合や、アップグレードにセカンダリ ファームが必要な場合は、追加のコストがかかる可能性がある。</span><span class="sxs-lookup"><span data-stu-id="ede6a-186">There can be additional costs if hardware infrastructure needs to be upgraded to support the newer version of SharePoint, or if a secondary farm is required for upgrade.</span></span>  <br/> |
|<span data-ttu-id="ede6a-187">パートナーが、SharePoint Online へのデータの移行を一度で行えるようにサポートできる。</span><span class="sxs-lookup"><span data-stu-id="ede6a-187">Partners can assist with the one-time job of migrating your data to SharePoint Online.</span></span>  <br/> ||
|<span data-ttu-id="ede6a-188">オンライン製品に関しては、サービス全体における更新が自動的に行われる。機能は廃止になる可能性もあるが、サポート自体は継続する。</span><span class="sxs-lookup"><span data-stu-id="ede6a-188">Online products are updated automatically across the service meaning that though features may deprecate, there is no true end of support.</span></span>  <br/> ||
   
<span data-ttu-id="ede6a-189">新しい Office 365 サイトを作成し、必要に応じてデータを手動で移行することにした場合は、以下の Office 365 のオプションを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ede6a-189">If you've decided to create a new Office 365 site, and will manually migrate data to it as is needed, you can look at your Office 365 options right here:</span></span>
  
[<span data-ttu-id="ede6a-190">Office 365 プランのオプション</span><span class="sxs-lookup"><span data-stu-id="ede6a-190">Office 365 Plan Options</span></span>](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a><span data-ttu-id="ede6a-191">オンプレミスの SharePoint Server のアップグレード</span><span class="sxs-lookup"><span data-stu-id="ede6a-191">Upgrade SharePoint Server on-premises</span></span>

<span data-ttu-id="ede6a-p114">SharePoint のバージョンをスキップしてアップグレードする方法はありません。SharePoint Server 2016 のリリースの場合も同様です。アップグレードは以下のように順次に行われます。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p114">There is historically no way to skip versions in SharePoint Upgrades, at least not as of the release of SharePoint Server 2016. That means upgrades go serially:</span></span>
  
|||
|:-----|:-----|
||<span data-ttu-id="ede6a-194">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="ede6a-194">SharePoint 2007</span></span> | <span data-ttu-id="ede6a-195">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="ede6a-195">SharePoint Server 2010</span></span> | <span data-ttu-id="ede6a-196">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="ede6a-196">SharePoint Server 2013</span></span> | <span data-ttu-id="ede6a-197">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="ede6a-197">SharePoint Server 2016</span></span> |
   
<span data-ttu-id="ede6a-p115">SharePoint 2007 から SharePoint Server 2016 へのパス全体を取得するには、多くの時間を要します。また、アップグレードされたハードウェア (SQL サーバーもアップグレードする必要があります)、ソフトウェア、管理に関するコストも発生します。機能の重要度に応じて、カスタマイズをアップグレードしたり、カスタマイズした内容を破棄したりする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p115">To take the entire path from SharePoint 2007 to SharePoint Server 2016 will mean a significant investment of time and will involve a cost in terms of upgraded hardware (be aware that SQL servers must also be upgraded), software, and administration. Customizations will need to be upgraded or abandoned, according to the criticality of the feature.</span></span>
  
> [!NOTE]
> <span data-ttu-id="ede6a-p116">サポートが終了した SharePoint 2007 ファームの使用を継続し、新しいハードウェアに SharePoint Server 2016 ファームをインストールして (ファームが共存している状態で別々に実行)、コンテンツの手動による移行 (コンテンツのダウンロードや再アップロードなど) を計画したり実行したりすることは可能です。ただし、手動による移動 (最後に変更されたアカウントを、手動で移動するアカウントのエイリアスに置き換えたドキュメントの移動など) に関する問題には注意を払う必要があり、サイト、サブサイト、アクセス許可、リスト構造の再構成などの作業は早めに行う必要があります。ストレージに移行するデータと、必要ないデータを区別し、どういった操作が移行による負担を軽減できるのかを今検討することが非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p116">It's possible to maintain your end-of-life SharePoint 2007 farm, install a SharePoint Server 2016 farm on new hardware (so the separate farms run side-by-side), and then plan and execute a manual migration of content (for downloading and re-uploading content, for example). Be aware of some of the gotchas of manual moves (such as moves of documents replacing the last modified account with the alias of the account doing the manual move), and the work that must be done ahead of time (such as recreating sites, sub-sites, permissions and list structures). Again, this is the time to consider what data you can move into storage, or no longer need, an action that can reduce the impact of migration.</span></span>
  
<span data-ttu-id="ede6a-p117">いずれにしても、アップグレードする前に環境を整えることが重要です。アップグレードする前に既存のファームが機能していることを確認してください。使用を停止するものについても、念のため確認してください。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p117">Either way, clean your environment prior to upgrade. Be certain your existing farm is functional before you upgrade, and (for sure) before you decommission!</span></span> 
  
<span data-ttu-id="ede6a-205">以下の、**サポートされるアップグレード パスとサポート外のアップグレード パス**を確認してください。</span><span class="sxs-lookup"><span data-stu-id="ede6a-205">Remember to review the **supported and unsupported upgrade paths**:</span></span> 
  
- [<span data-ttu-id="ede6a-206">SharePoint Server 2007</span><span class="sxs-lookup"><span data-stu-id="ede6a-206">SharePoint Server 2007</span></span>](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [<span data-ttu-id="ede6a-207">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="ede6a-207">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [<span data-ttu-id="ede6a-208">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="ede6a-208">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843157)
    
<span data-ttu-id="ede6a-209">**カスタマイズ**を行っている場合は、移行パスの手順ごとにアップグレードの計画を立てることが重要となります。詳細は以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ede6a-209">If you have **customizations**, it's critical you have a plan your upgrade for each step in the migration path:</span></span> 
  
- [<span data-ttu-id="ede6a-210">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="ede6a-210">SharePoint 2007</span></span>](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [<span data-ttu-id="ede6a-211">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="ede6a-211">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [<span data-ttu-id="ede6a-212">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="ede6a-212">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843162)
    
|<span data-ttu-id="ede6a-213">**オンプレミスの利点**</span><span class="sxs-lookup"><span data-stu-id="ede6a-213">**On-premises Pro**</span></span>|<span data-ttu-id="ede6a-214">**オンプレミスの欠点**</span><span class="sxs-lookup"><span data-stu-id="ede6a-214">**On-premises Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ede6a-215">サーバー ハードウェアからの、SharePoint ファームの機能すべての完全なコントロール。</span><span class="sxs-lookup"><span data-stu-id="ede6a-215">Full control of all aspects of your SharePoint Farm, from the server hardware up.</span></span>  <br/> |<span data-ttu-id="ede6a-216">下記の破損と修理のすべてが貴社の責任になる (製品のサポートが終了していない場合は、有料の Microsoft サポートの利用が可能)。</span><span class="sxs-lookup"><span data-stu-id="ede6a-216">All breaks and fixes are the responsibility of your company (can engage paid Microsoft Support if your product is not at end of support):</span></span>  <br/> |
|<span data-ttu-id="ede6a-217">ハイブリッドの SharePoint Online サブスクリプションにオンプレミス ファームを接続するオプションを備えた、オンプレミスの SharePoint Server のフル機能一式。</span><span class="sxs-lookup"><span data-stu-id="ede6a-217">Full feature set of SharePoint Server on-premises with the option to connect your on-premises farm to a SharePoint Online subscription via hybrid.</span></span>  <br/> |<span data-ttu-id="ede6a-218">オンプレミスに管理される SharePoint Server のアップグレード、パッチ、セキュリティ修正プログラム、およびすべての保守。</span><span class="sxs-lookup"><span data-stu-id="ede6a-218">Upgrade, patches, security fixes, and all maintenance of SharePoint Server managed on-premises.</span></span>  <br/> |
|<span data-ttu-id="ede6a-219">高度なカスタマイズのためのフル アクセス許可。</span><span class="sxs-lookup"><span data-stu-id="ede6a-219">Full access for greater customization.</span></span>  <br/> |<span data-ttu-id="ede6a-220">[Office 365 でサポートされるコンプライアンス基準](https://go.microsoft.com/fwlink/?linkid=843165)を、オンプレミスで手動で構成しなければならない。</span><span class="sxs-lookup"><span data-stu-id="ede6a-220">[Compliance standards supported by Office 365](https://go.microsoft.com/fwlink/?linkid=843165) must be manually configured on-premises.</span></span>  <br/> |
|<span data-ttu-id="ede6a-221">オンプレミスで実行される、セキュリティ テストとサーバーのパフォーマンス チューニング (自分でコントロール)。</span><span class="sxs-lookup"><span data-stu-id="ede6a-221">Security testing, and server performance tuning, carried out on your premises (is under your control).</span></span>  <br/> |<span data-ttu-id="ede6a-222">オンプレミスの SharePoint Server と相互運用しない SharePoint Online での機能が、Office 365 によって、有効になることがある</span><span class="sxs-lookup"><span data-stu-id="ede6a-222">Office 365 may make features available to SharePoint Online that do not interoperate with SharePoint Server on-premises</span></span>  <br/> |
|<span data-ttu-id="ede6a-223">パートナーが、SharePoint Server の次のバージョン (さらにその先も対象) へのデータ移行をサポートできる。</span><span class="sxs-lookup"><span data-stu-id="ede6a-223">Partners can assist with migrating data to the next version of SharePoint Server (and beyond).</span></span>  <br/> |<span data-ttu-id="ede6a-224">SharePoint Server サイトでは、SharePoint Online で表示される [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) 証明書が自動的に使用されることはない。</span><span class="sxs-lookup"><span data-stu-id="ede6a-224">Your SharePoint Server sites will not automatically use [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) certificates as is seen in SharePoint Online.</span></span>  <br/> |
|<span data-ttu-id="ede6a-225">オンプレミスの SharePoint Server での、名前付け規則、バックアップと復元、その他の回復オプションの完全なコントロール。</span><span class="sxs-lookup"><span data-stu-id="ede6a-225">Full control of naming conventions, backup and restore and other recovery options in SharePoint Server on-premises.</span></span>  <br/> |<span data-ttu-id="ede6a-226">製品のライフサイクルによって、オンプレミスの SharePoint Server の機能が異なる。</span><span class="sxs-lookup"><span data-stu-id="ede6a-226">SharePoint Server on-premises is sensitive to product lifecycles.</span></span>  <br/> |
   
### <a name="upgrade-resources"></a><span data-ttu-id="ede6a-227">アップグレードのリソース</span><span class="sxs-lookup"><span data-stu-id="ede6a-227">Upgrade Resources</span></span>

<span data-ttu-id="ede6a-228">ハードウェアとソフトウェアの要件を満たしていることを確認してから、サポートされているアップグレード方法に従って操作を行ってください。</span><span class="sxs-lookup"><span data-stu-id="ede6a-228">Begin by knowing that you meet hardware and software requirements, then follow supported upgrade methods.</span></span>
  
- <span data-ttu-id="ede6a-229">**ハードウェア/ソフトウェア要件**:</span><span class="sxs-lookup"><span data-stu-id="ede6a-229">**Hardware/software requirements for**:</span></span> 
    
    <span data-ttu-id="ede6a-230">[SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)</span><span class="sxs-lookup"><span data-stu-id="ede6a-230">[SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)</span></span>
    
- <span data-ttu-id="ede6a-231">**ソフトウェアの境界と制限**:</span><span class="sxs-lookup"><span data-stu-id="ede6a-231">**Software boundaries and limits for SharePoint 2013**</span></span> 
    
    <span data-ttu-id="ede6a-232">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)</span><span class="sxs-lookup"><span data-stu-id="ede6a-232">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)</span></span>
    
- <span data-ttu-id="ede6a-233">**アップグレード プロセスの概要**:</span><span class="sxs-lookup"><span data-stu-id="ede6a-233">**The upgrade process overview for**:</span></span> 
    
    <span data-ttu-id="ede6a-234">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)</span><span class="sxs-lookup"><span data-stu-id="ede6a-234">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)</span></span>
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a><span data-ttu-id="ede6a-235">SharePoint Online とオンプレミスの間で、SharePoint ハイブリッド ソリューションを作成する</span><span class="sxs-lookup"><span data-stu-id="ede6a-235">Create a SharePoint hybrid solution between SharePoint Online and on-premises</span></span>

<span data-ttu-id="ede6a-p118">オンプレミスでの完全コントロールでの移行か、SharePoint Online の低コストの所有権による移行かを検討している場合、SharePoint Server 2013 のファームあるいは 2016 のファームをハイブリッドとして、SharePoint Online に接続できます。[SharePoint ハイブリッド ソリューションの詳細情報](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)</span><span class="sxs-lookup"><span data-stu-id="ede6a-p118">If the answer to your migration needs is somewhere between the self-control offered by on-premises, and the lower cost of ownership offered by SharePoint Online, you can connect SharePoint Server 2013 or 2016 farms to SharePoint Online, through hybrids. [Learn about SharePoint hybrid solutions](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)</span></span>
  
<span data-ttu-id="ede6a-238">ハイブリッドの SharePoint Server ファームをビジネスに活用することにした場合は、既存のハイブリッドの種類はもちろん、オンプレミスの SharePoint ファームと Office 365 サブスクリプションとの接続方法を理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="ede6a-238">If you decide that a hybrid SharePoint Server farm will benefit your business, familiarize yourself with the existing types of hybrid and how to configure the connection between your on-premises SharePoint farm and your Office 365 subscription.</span></span>
  
<span data-ttu-id="ede6a-p119">動作を確認するお勧めの方法の 1 つは、[Office 365 の開発/テスト環境](https://go.microsoft.com/fwlink/?linkid=843152)を作成することです。試用版や購入済みの Office 365 サブスクリプションがあれば、SharePoint Online でサイト コレクション、Web、ドキュメント ライブラリを作成し、データを移行できるようになります (手動で、移行 API を使用して、あるいは個人用サイトのコンテンツを OneDrive for Business に移行する場合は、ハイブリッド ウィザードで行うこともできます)。</span><span class="sxs-lookup"><span data-stu-id="ede6a-p119">One good way to see how this works is by creating an [Office 365 dev/test environment](https://go.microsoft.com/fwlink/?linkid=843152). Once you have a trial or purchased Office 365 subscription, you'll be on your way to creating the site collections, webs, and document libraries in SharePoint Online to which you can migrate data (either manually, by use of the Migration API, or - if you want to migrate My Site content to OneDrive for Business - through the hybrid wizard).</span></span>
  
> [!NOTE]
> <span data-ttu-id="ede6a-241">なお、ハイブリッド オプションを使用するには、SharePoint Server 2007 ファームを SharePoint Server 2013 または SharePoint Server 2016 にオンプレミスでアップグレードする必要があります</span><span class="sxs-lookup"><span data-stu-id="ede6a-241">Remember that your SharePoint 2007 farm will need to be upgraded, on-premises, to either SharePoint Server 2013 or SharePoint Server 2016 to use the hybrid option</span></span> 
  
## <a name="related-topics"></a><span data-ttu-id="ede6a-242">関連項目</span><span class="sxs-lookup"><span data-stu-id="ede6a-242">Related topics</span></span>

[<span data-ttu-id="ede6a-243">アップグレードのトラブルシューティングおよび再開 (Office SharePoint Server 2007)</span><span class="sxs-lookup"><span data-stu-id="ede6a-243">Troubleshoot and resume upgrade (Office SharePoint Server 2007)</span></span>](https://go.microsoft.com/fwlink/?linkid=843192)
  
[<span data-ttu-id="ede6a-244">アップグレードの問題のトラブルシューティング (SharePoint Server 2010)</span><span class="sxs-lookup"><span data-stu-id="ede6a-244">Troubleshoot upgrade issues (SharePoint Server 2010)</span></span>](https://go.microsoft.com/fwlink/?linkid=843194)
  
[<span data-ttu-id="ede6a-245">SharePoint 2013 でのデータベース アップグレードの問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ede6a-245">Troubleshoot database upgrade issues in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843195)
  
[<span data-ttu-id="ede6a-246">アップグレードを支援する Microsoft パートナーの検索</span><span class="sxs-lookup"><span data-stu-id="ede6a-246">Search for Microsoft Partners to help with Upgrade</span></span>](https://go.microsoft.com/fwlink/?linkid=841249)
  
[<span data-ttu-id="ede6a-247">Office 2007 のサーバーとクライアントからのアップグレードに役立つリソース</span><span class="sxs-lookup"><span data-stu-id="ede6a-247">Resources to help you upgrade from Office 2007 servers and clients</span></span>](upgrade-from-office-2007-servers-and-products.md)
  

