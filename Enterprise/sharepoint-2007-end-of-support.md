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
description: 2017 年 10 月 10日には、SharePoint Server 2007 のサポートが終了しました。、ベスト ・ プラクティス、トラブルシューティングのシステム要件、アップグレード手順は、マイクロソフトのパートナーからのヘルプを表示する方法、アップグレードのオプションの詳細については、この資料を参照してください。
ms.openlocfilehash: b548e7623a72d57793c18409a80506bb832df858
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169799"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a><span data-ttu-id="963f3-104">SharePoint Server 2007 のサポート終了ロードマップ</span><span class="sxs-lookup"><span data-stu-id="963f3-104">SharePoint Server 2007 end of support roadmap</span></span>

<span data-ttu-id="963f3-p102">**2017 年 10 月 10日**、[Microsoft Office SharePoint Server 2007 はサポート終了に達しました。Office 365 または SharePoint のサーバーの設置型の新しいバージョンの SharePoint Server 2007 からの移行を開始していない場合はここで計画を開始します。この資料では、SharePoint Online では、データを移行またはアップグレード、SharePoint サーバーの設置型の人々 を支援するためのリソースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="963f3-p102">On **October 10, 2017**, Microsoft Office SharePoint Server 2007 reached end of support. If you haven't begun your migration from SharePoint Server 2007 to Office 365 or a newer version of SharePoint Server on-premises, now's the time to start planning. This article details resources to help people migrate data to SharePoint Online, or upgrade your SharePoint Server on-premises.</span></span> 
  
## <a name="what-does-end-of-support-mean"></a><span data-ttu-id="963f3-108">サポートの平均の最後は何でしょうか。</span><span class="sxs-lookup"><span data-stu-id="963f3-108">What does end of support mean?</span></span>

<span data-ttu-id="963f3-p103">SharePoint サーバーでは、ほとんどすべてのマイクロソフト製品と同じようにする時に、マイクロソフトでは、新機能、バグ修正、セキュリティ修正プログラム、およびなどが提供していますサポート ライフ サイクルがあります。このライフ サイクルは、通常製品の初期リリースの日付から 10 年間持続し、このライフ サイクルの最後は、製品のサポート終了と呼ばれます。。サポートの終わりは、マイクロソフトが提供されなくなります。</span><span class="sxs-lookup"><span data-stu-id="963f3-p103">SharePoint Server, like almost all Microsoft products, has a support lifecycle during which Microsoft provides new features, bug fixes, security fixes, and so on. This lifecycle typically lasts for 10 years from the date of the product's initial release, and the end of this lifecycle is known as the product's end of support. At end of support, Microsoft no longer provides:</span></span>
  
- <span data-ttu-id="963f3-112">テクニカル サポートに問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="963f3-112">Technical support for problems that may occur;</span></span>
    
- <span data-ttu-id="963f3-113">バグの修正で問題が検出され、サーバーの使いやすさと安定性に影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="963f3-113">Bug fixes for issues that are discovered and that may impact the stability and usability of the server;</span></span>
    
- <span data-ttu-id="963f3-114">セキュリティ上の脆弱性が検出され、セキュリティ違反の影響を受けるサーバーを構成することがありますの修正プログラムそして</span><span class="sxs-lookup"><span data-stu-id="963f3-114">Security fixes for vulnerabilities that are discovered and that may make the server vulnerable to security breaches; and</span></span> 
    
- <span data-ttu-id="963f3-115">タイム ゾーンを更新します。</span><span class="sxs-lookup"><span data-stu-id="963f3-115">Time zone updates.</span></span>
    
<span data-ttu-id="963f3-p104">ただし、SharePoint Server 2007 ファームになります運用後 2017年 10 月 10日、なしの更新プログラムではさらに、修正プログラム、または修正プログラム (セキュリティ更新プログラムと修正プログラムを含む)、製品の出荷し、マイクロソフトのサポートが完全に移ってきていますへのサポートを行って製品の最新バージョンです。インストールはサポートされなくなりましたまたは修正プログラムを適用するためサポート ・ アプローチの終わりとして、製品をアップグレードするか重要なデータを移行します。</span><span class="sxs-lookup"><span data-stu-id="963f3-p104">Though your SharePoint Server 2007 farm will still be operational after October 10, 2017, no further updates, patches, or fixes will be shipped for the product (including security patches/fixes), and Microsoft Support will have fully shifted its support efforts to more recent versions of the product. Because your installation will no longer supported or patched, as end of support approaches you should upgrade the product, or migrate important data.</span></span>
  
> [!TIP]
> <span data-ttu-id="963f3-p105">アップグレードや移行を既に計画していない場合を参照してください: [SharePoint 2007 の移行オプションを考慮する](sharepoint-2007-migration-options.md)を開始する場所の例をいくつか。アップグレード Office 365 移行 (またはその両方) を持つことができます[マイクロソフトのパートナー企業](https://go.microsoft.com/fwlink/?linkid=841249)の検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="963f3-p105">If you haven't already planned for upgrade or migration, please see: [SharePoint 2007 migration options to consider](sharepoint-2007-migration-options.md), for some examples of where to begin. You can also search for [Microsoft Partners](https://go.microsoft.com/fwlink/?linkid=841249) who can help with upgrade or Office 365 migration (or both).</span></span> 
  
<span data-ttu-id="963f3-120">サポートの末尾に到達する Office 2007 サーバーの詳細については、 [Office 2007 サーバーのアップグレードを計画する](https://support.office.com/article/4e5eab5f-05db-4627-9e17-421a6bf89606.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="963f3-120">For more information about Office 2007 servers reaching the end of support, see [Plan your upgrade for Office 2007 servers](https://support.office.com/article/4e5eab5f-05db-4627-9e17-421a6bf89606.aspx).</span></span>
  
## <a name="what-are-my-options"></a><span data-ttu-id="963f3-121">オプションを挙げてください。</span><span class="sxs-lookup"><span data-stu-id="963f3-121">What are my options?</span></span>

<span data-ttu-id="963f3-p106">最初の位置は、[製品のライフ サイクルのサイト](https://go.microsoft.com/fwlink/?linkid=843148)があります。エージングされているマイクロソフトの設置をした場合の確認事項サポート日の最後のため、1 年間またはアウトのためか、通常、移行が必要である限り、アップグレードや移行をスケジュールできます。次のステップを選択するときは、十分、向上、および最高の製品の機能に何と考えると役立つ場合があります。例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="963f3-p106">Your first stop should be the [Product Lifecycle site](https://go.microsoft.com/fwlink/?linkid=843148). If you have an on-premises Microsoft product that is aging, you should check for its end of support date so that, a year or so out - or as long as your migrations generally require - you can schedule upgrade or migrations. When choosing the next step, it might help to think in terms of what would be good enough, better, and best when it comes to product features. Here's an example:</span></span>
  
|<span data-ttu-id="963f3-126">**中**</span><span class="sxs-lookup"><span data-stu-id="963f3-126">**Good**</span></span>|<span data-ttu-id="963f3-127">**良い**</span><span class="sxs-lookup"><span data-stu-id="963f3-127">**Better**</span></span>|<span data-ttu-id="963f3-128">**高**</span><span class="sxs-lookup"><span data-stu-id="963f3-128">**Best**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="963f3-129">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="963f3-129">SharePoint Server 2010</span></span>  <br/> |<span data-ttu-id="963f3-130">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="963f3-130">SharePoint Server 2013</span></span>  <br/> |<span data-ttu-id="963f3-131">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="963f3-131">SharePoint Online</span></span>  <br/> |
||<span data-ttu-id="963f3-132">SharePoint ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="963f3-132">SharePoint Hybrid</span></span>  <br/> |<span data-ttu-id="963f3-133">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="963f3-133">SharePoint Server 2016</span></span>  <br/> |
|||<span data-ttu-id="963f3-134">SharePoint ハイブリッド</span><span class="sxs-lookup"><span data-stu-id="963f3-134">SharePoint Hybrid</span></span>  <br/> |
   
<span data-ttu-id="963f3-p107">(不十分) のスケールのローエンドのオプションは、SharePoint Server 2007 からの移行後は非常にすぐにアップグレードの計画を開始する必要が注意してください」を選択する場合が完了しました。(SharePoint Server 2007 用のサポートの終了は、2017 年 10 月 10 日です。注意してくださいこれらの日付が変更され、[製品のライフ サイクルのサイト](https://support.microsoft.com/en-us/lifecycle)を確認します。)</span><span class="sxs-lookup"><span data-stu-id="963f3-p107">If you choose options on the low end of the scale (good enough), remember you will need to begin planning for upgrade very soon after migration from SharePoint Server 2007 is complete. (end of support for SharePoint Server 2007 is October 10, 2017. Please note that these dates are subject to change and check the [Product Lifecycle site](https://support.microsoft.com/en-us/lifecycle).)</span></span>
  
## <a name="where-can-i-go-next"></a><span data-ttu-id="963f3-138">次へ移動先は?</span><span class="sxs-lookup"><span data-stu-id="963f3-138">Where can I go next?</span></span>

<span data-ttu-id="963f3-p108">SharePoint サーバーは、インストールされている設置型、独自のサーバー上または SharePoint Online では、これは、Microsoft Office 365 の一部であるオンライン サービスを使用できます。を選択できます。</span><span class="sxs-lookup"><span data-stu-id="963f3-p108">SharePoint Server can be installed on-premises on your own servers, or you can use SharePoint Online, which is an online service that is part of Microsoft Office 365. You can choose to:</span></span>
  
- <span data-ttu-id="963f3-141">SharePoint Online に移行する</span><span class="sxs-lookup"><span data-stu-id="963f3-141">Migrate to SharePoint Online</span></span>
    
- <span data-ttu-id="963f3-142">アップグレードの SharePoint サーバーの設置型</span><span class="sxs-lookup"><span data-stu-id="963f3-142">Upgrade SharePoint Server on-premises</span></span>
    
- <span data-ttu-id="963f3-143">上記の両方の操作を行います</span><span class="sxs-lookup"><span data-stu-id="963f3-143">Do both of the above</span></span>
    
- <span data-ttu-id="963f3-144">[SharePoint のハイブリッド](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)ソリューションを実装します。</span><span class="sxs-lookup"><span data-stu-id="963f3-144">Implement a [SharePoint hybrid](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) solution</span></span> 
    
<span data-ttu-id="963f3-p109">非表示に伴うコストの今後は、サーバー ファームの管理を維持するか、カスタマイズを移行して SharePoint Server が依存しているハードウェアのアップグレードに注意します。設置型の SharePoint サーバー ファームのことは、やりがいは増しますは必要です。それ以外の場合、大量のカスタマイズを行わなくても、従来の SharePoint サーバーに、ファームを実行する場合を享受できます計画的な移行 SharePoint Online にします。</span><span class="sxs-lookup"><span data-stu-id="963f3-p109">Be aware of hidden costs associated with maintaining a server farm going forward, maintaining or migrating customizations, and upgrading the hardware upon which SharePoint Server depends. Having an on-premises SharePoint Server farm is rewarding if it is a necessity; otherwise, if you run your farm on legacy SharePoint Servers, without heavy customization, you can benefit from a planned migration to SharePoint Online.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="963f3-p110">別の方法で SharePoint 2007 のコンテンツは、使用頻度の低い場合。SharePoint 管理者によってでは[、Office 365 のサブスクリプションを作成](https://go.microsoft.com/fwlink/?linkid=843152)、新しい SharePoint Online サイトを設定し、SharePoint 2007 から完全にカットするのには最新の SharePoint Online サイトに最も重要なドキュメントのみを取得ができます。そこからデータ消耗する SharePoint 2007 サイトからアーカイブにします。思考方法のユーザー データを処理する、SharePoint 2007 のインストールを提供します。この問題を解決するのには創造的な方法がある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="963f3-p110">There is another option if the content in SharePoint 2007 is infrequently used. Some SharePoint Administrators may choose to [create an Office 365 Subscription](https://go.microsoft.com/fwlink/?linkid=843152), set up a brand new SharePoint Online site, and then cut away from SharePoint 2007, cleanly, taking only the most essential documents to the fresh SharePoint Online sites. From there, data may be drained from the SharePoint 2007 site into archives. Give thought to how users work with data your SharePoint 2007 installation. There may be creative ways to resolve this problem!</span></span> 
  
|<span data-ttu-id="963f3-152">**SharePoint オンライン (SPO)**</span><span class="sxs-lookup"><span data-stu-id="963f3-152">**SharePoint Online (SPO)**</span></span>|<span data-ttu-id="963f3-153">**SharePoint サーバー設置**</span><span class="sxs-lookup"><span data-stu-id="963f3-153">**SharePoint Server on-premises**</span></span>|
|:-----|:-----|
|<span data-ttu-id="963f3-154">時間のコストが高い (計画と実行と検証)</span><span class="sxs-lookup"><span data-stu-id="963f3-154">High cost in time (plan / execution / verification)</span></span>  <br/> |<span data-ttu-id="963f3-155">時間のコストが高い (計画と実行と検証)</span><span class="sxs-lookup"><span data-stu-id="963f3-155">High cost in time (plan / execution / verification)</span></span>  <br/> |
|<span data-ttu-id="963f3-156">資金 (ハードウェアの購入なし) でのコストを削減</span><span class="sxs-lookup"><span data-stu-id="963f3-156">Lower cost in funds (no hardware purchases)</span></span>  <br/> |<span data-ttu-id="963f3-157">資金のコストが高い (ハードウェア + 開発者と管理者)</span><span class="sxs-lookup"><span data-stu-id="963f3-157">Higher cost in funds (hardware + devs / admins)</span></span>  <br/> |
|<span data-ttu-id="963f3-158">移行での 1 回限りの料金</span><span class="sxs-lookup"><span data-stu-id="963f3-158">One-time cost in migration</span></span>  <br/> |<span data-ttu-id="963f3-159">将来の移行につき 1 回限りのコストが繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="963f3-159">One-time cost repeated per future migration</span></span>  <br/> |
|<span data-ttu-id="963f3-160">低い総所有コストとメンテナンス</span><span class="sxs-lookup"><span data-stu-id="963f3-160">Low total cost of ownership / maintenance</span></span>  <br/> |<span data-ttu-id="963f3-161">高の総所有コストとメンテナンス</span><span class="sxs-lookup"><span data-stu-id="963f3-161">High total cost of ownership / maintenance</span></span>  <br/> |
   
<span data-ttu-id="963f3-p111">Office 365 に移行するときに 1 回限りの移動は、データを整理し、クラウドへの対処およびのままにするのにはどのような決定している間に先行、重いコストがあります。ただし、アップグレードをその時点から自動的に行われます、ハードウェアとソフトウェアの更新を管理する必要がないと、マイクロソフトのサービス レベル契約 ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) によって、ファームのアップ時間がバックアップされます。</span><span class="sxs-lookup"><span data-stu-id="963f3-p111">When you migrate to Office 365, the one-time move will have a heavier cost up-front, while you're organizing data and deciding what to take to the cloud and what to leave behind. However, upgrades will be automatic from that point, you will no longer need to manage hardware and software updates, and the up-time of your farm will be backed by a Microsoft Service Level Agreement ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)).</span></span>
  
### <a name="migrate-to-sharepoint-online"></a><span data-ttu-id="963f3-164">SharePoint Online に移行する</span><span class="sxs-lookup"><span data-stu-id="963f3-164">Migrate to SharePoint Online</span></span>

<span data-ttu-id="963f3-p112">SharePoint Online が関連付けられているサービスの説明を確認して、必要なすべての機能を確認します。すべての Office 365 サービスの説明へのリンクを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="963f3-p112">Make sure that SharePoint Online has all the features you need by reviewing the associated service description. Here's the link to all Office 365 Service Descriptions:</span></span>
  
[<span data-ttu-id="963f3-167">Office 365 サービスの説明</span><span class="sxs-lookup"><span data-stu-id="963f3-167">Office 365 Service Descriptions</span></span>](https://go.microsoft.com/fwlink/?linkid=272060)
  
<span data-ttu-id="963f3-p113">SharePoint 2007 からの移行は、SharePoint Online; までする直接的な方法はありません。SharePoint Online への移行を手動で実行するとします。SharePoint Server 2013 または SharePoint サーバーの 2016年をアップグレードする場合の移動もあります (ビジネス、OneDrive に情報を移行するなど) を SharePoint 移行 API を使用します。</span><span class="sxs-lookup"><span data-stu-id="963f3-p113">There is no direct way to migrate from SharePoint 2007 to SharePoint Online; your move to SharePoint Online would be done manually. If you upgrade to SharePoint Server 2013 or SharePoint Server 2016, your move might also involve using the SharePoint Migration API (to migrate information into OneDrive for Business, for example).</span></span>
  
|<span data-ttu-id="963f3-170">**オンライン Pro**</span><span class="sxs-lookup"><span data-stu-id="963f3-170">**Online Pro**</span></span>|<span data-ttu-id="963f3-171">**オンライン詐欺**</span><span class="sxs-lookup"><span data-stu-id="963f3-171">**Online Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="963f3-172">Microsoft では、SPO のハードウェアおよびハードウェアのすべての管理を提供します。</span><span class="sxs-lookup"><span data-stu-id="963f3-172">Microsoft supplies SPO hardware and all hardware administration.</span></span>  <br/> |<span data-ttu-id="963f3-173">使用可能な機能は、SharePoint サーバーの設置型と SPO の間で異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="963f3-173">Available features may be different between SharePoint Server on-premises and SPO.</span></span>  <br/> |
|<span data-ttu-id="963f3-174">グローバル管理者は、サブスクリプションのと、SPO のサイトに管理者を割り当てることがあります。</span><span class="sxs-lookup"><span data-stu-id="963f3-174">You are the global administrator of your subscription, and may assign administrators to SPO sites.</span></span>  <br/> |<span data-ttu-id="963f3-175">設置型が存在しない (または必要はありません)、SharePoint サーバーのファーム管理者に利用可能ないくつかの操作は、Office 365 で SharePoint の管理者ロールに含まれます。</span><span class="sxs-lookup"><span data-stu-id="963f3-175">Some actions available to a Farm Administrator in SharePoint Server on-premises do not exist (or are not necessary) included in the SharePoint Administrator role in Office 365.</span></span>  <br/> |
|<span data-ttu-id="963f3-176">マイクロソフトは、修正プログラムを適用、修正および基になるハードウェアとソフトウェアを更新します。</span><span class="sxs-lookup"><span data-stu-id="963f3-176">Microsoft applies patches, fixes and updates to underlying hardware and software.</span></span>  <br/> |<span data-ttu-id="963f3-177">サービスの基になるファイル ・ システムへのアクセス権がないため、一部のカスタマイズが制限されています。</span><span class="sxs-lookup"><span data-stu-id="963f3-177">Because there is no access to the underlying file system in the service, some customizations are limited.</span></span>  <br/> |
|<span data-ttu-id="963f3-178">マイクロソフトでは、[サービス レベル合意書](https://go.microsoft.com/fwlink/?linkid=843153)の発行し、サービス ・ レベルの問題を解決するのには迅速に移動します。</span><span class="sxs-lookup"><span data-stu-id="963f3-178">Microsoft publishes [Service Level Agreements](https://go.microsoft.com/fwlink/?linkid=843153) and moves quickly to resolve service level incidents.</span></span>  <br/> |<span data-ttu-id="963f3-179">バックアップと復元、およびその他のリカバリ ・ オプションは、SharePoint Online のサービスで自動化された - バックアップが上書きされるかどうかを使用します。</span><span class="sxs-lookup"><span data-stu-id="963f3-179">Backup and restore and other recovery options are automated by the service in SharePoint Online - backups are overwritten if not used.</span></span>  <br/> |
|<span data-ttu-id="963f3-180">セキュリティのテストとサーバーのパフォーマンスのチューニングを実施するサービスで継続的にマイクロソフトによって。</span><span class="sxs-lookup"><span data-stu-id="963f3-180">Security testing and server performance tuning are carried out on an ongoing basis in the service by Microsoft.</span></span>  <br/> |<span data-ttu-id="963f3-181">ユーザー インターフェイスおよびその他の SharePoint の機能は、サービスがインストールされているし、オンとオフを切り替える必要がありますに変更します。</span><span class="sxs-lookup"><span data-stu-id="963f3-181">Changes to the user interface and other SharePoint features are installed by the service and may need to be toggled on or off.</span></span>  <br/> |
|<span data-ttu-id="963f3-182">Office 365 は、多くの業界標準を満たしている: [Office 365 のコンプライアンス](https://go.microsoft.com/fwlink/?linkid=843165)です。</span><span class="sxs-lookup"><span data-stu-id="963f3-182">Office 365 meets many industry standards: [Office 365 Compliance](https://go.microsoft.com/fwlink/?linkid=843165).</span></span>  <br/> |<span data-ttu-id="963f3-183">[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597)移行支援は、制限されています。</span><span class="sxs-lookup"><span data-stu-id="963f3-183">[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) assistance for migration is limited.</span></span>  <br/> <span data-ttu-id="963f3-184">アップグレードの多くは、手動または SPO の移行 API を使用して、 [SharePoint Online と OneDrive 移行コンテンツのロードマップ](https://go.microsoft.com/fwlink/?linkid=843184)に記載されています。</span><span class="sxs-lookup"><span data-stu-id="963f3-184">Much of the upgrade will be manual, or via the SPO Migration API described in the [SharePoint Online and OneDrive Migration Content Roadmap](https://go.microsoft.com/fwlink/?linkid=843184).</span></span>  <br/> |
|<span data-ttu-id="963f3-185">マイクロソフト サポート エンジニアも、データ センター内の従業員に無制限に管理者のアクセス、サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="963f3-185">Neither Microsoft Support Engineers nor employees in the datacenter have unrestricted admin access to your subscription.</span></span>  <br/> |<span data-ttu-id="963f3-186">ハードウェア ・ インフラストラクチャは、SharePoint の新しいバージョンをサポートするためにアップグレードする必要がある場合、またはセカンダリ ファームのアップグレードに必要な場合、追加のコストが存在することができます。</span><span class="sxs-lookup"><span data-stu-id="963f3-186">There can be additional costs if hardware infrastructure needs to be upgraded to support the newer version of SharePoint, or if a secondary farm is required for upgrade.</span></span>  <br/> |
|<span data-ttu-id="963f3-187">SharePoint Online に、データを移行するための一時的なジョブ パートナーを支援できます。</span><span class="sxs-lookup"><span data-stu-id="963f3-187">Partners can assist with the one-time job of migrating your data to SharePoint Online.</span></span>  <br/> ||
|<span data-ttu-id="963f3-188">オンラインの製品は、機能を廃止可能性があります、ただしはありませんサポートの本来の終了を意味するサービスの間で自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="963f3-188">Online products are updated automatically across the service meaning that though features may deprecate, there is no true end of support.</span></span>  <br/> ||
   
<span data-ttu-id="963f3-189">新しい Office 365 サイトを作成するし、手動で移行データには、必要に応じて、Office 365 のオプション権利をここで見ることができます。</span><span class="sxs-lookup"><span data-stu-id="963f3-189">If you've decided to create a new Office 365 site, and will manually migrate data to it as is needed, you can look at your Office 365 options right here:</span></span>
  
[<span data-ttu-id="963f3-190">Office 365 プランのオプション</span><span class="sxs-lookup"><span data-stu-id="963f3-190">Office 365 Plan Options</span></span>](https://go.microsoft.com/fwlink/?linkid=843151)
  
### <a name="upgrade-sharepoint-server-on-premises"></a><span data-ttu-id="963f3-191">アップグレードの SharePoint サーバーの設置型</span><span class="sxs-lookup"><span data-stu-id="963f3-191">Upgrade SharePoint Server on-premises</span></span>

<span data-ttu-id="963f3-p114">これは、SharePoint サーバーの 2016 年のリリースの時点で、少なくとも、SharePoint のアップグレードでバージョンをスキップする方法はこれまでありません。つまり、アップグレードが連続的に移動します。</span><span class="sxs-lookup"><span data-stu-id="963f3-p114">There is historically no way to skip versions in SharePoint Upgrades, at least not as of the release of SharePoint Server 2016. That means upgrades go serially:</span></span>
  
|||
|:-----|:-----|
||<span data-ttu-id="963f3-194">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="963f3-194">SharePoint 2007</span></span> | <span data-ttu-id="963f3-195">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="963f3-195">SharePoint Server 2010</span></span> | <span data-ttu-id="963f3-196">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="963f3-196">SharePoint Server 2013</span></span> | <span data-ttu-id="963f3-197">SharePoint Server 2016</span><span class="sxs-lookup"><span data-stu-id="963f3-197">SharePoint Server 2016</span></span> |
   
<span data-ttu-id="963f3-p115">SharePoint 2007 から完全なパスを実行するには、SharePoint サーバーの 2016年は膨大な時間のことを意味し、コスト (SQL サーバーもアップグレードする必要があることに注意する)、アップグレードされたハードウェアで、ソフトウェア、および管理が含まれます。カスタマイズはアップグレードまたは機能の重要度に応じて、破棄する必要があります。</span><span class="sxs-lookup"><span data-stu-id="963f3-p115">To take the entire path from SharePoint 2007 to SharePoint Server 2016 will mean a significant investment of time and will involve a cost in terms of upgraded hardware (be aware that SQL servers must also be upgraded), software, and administration. Customizations will need to be upgraded or abandoned, according to the criticality of the feature.</span></span>
  
> [!NOTE]
> <span data-ttu-id="963f3-p116">終了の SharePoint 2007 ファームを維持、(別のファームでは、サイド バイ サイドを実行) のための新しいハードウェアは、[SharePoint のサーバーの 2016年ファームのインストール、計画し、(とコンテンツのダウンロードのコンテンツを再アップロードするを手動での移行を実行することはなど)。など移動のドキュメントが最後に修正されたアカウントを手動での移動を実行するアカウントのエイリアスに置き換える)、手動での移動と、サイト、サブサイト、アクセス許可、リストの再作成などの時間の前に行う必要がある作業の注意事項のいくつかに注意してください。構造体)。繰り返しますが、これは、どのようなデータのストレージ、または不要になったが、移行の影響を減らすことができるアクションに移動することを検討する時間です。</span><span class="sxs-lookup"><span data-stu-id="963f3-p116">It's possible to maintain your end-of-life SharePoint 2007 farm, install a SharePoint Server 2016 farm on new hardware (so the separate farms run side-by-side), and then plan and execute a manual migration of content (for downloading and re-uploading content, for example). Be aware of some of the gotchas of manual moves (such as moves of documents replacing the last modified account with the alias of the account doing the manual move), and the work that must be done ahead of time (such as recreating sites, sub-sites, permissions and list structures). Again, this is the time to consider what data you can move into storage, or no longer need, an action that can reduce the impact of migration.</span></span>
  
<span data-ttu-id="963f3-p117">どちらの方法は、環境の前に、アップグレードをクリーニングします。既存のファームでは、アップグレードする前に機能し、解除する前に (確認) を特定します。</span><span class="sxs-lookup"><span data-stu-id="963f3-p117">Either way, clean your environment prior to upgrade. Be certain your existing farm is functional before you upgrade, and (for sure) before you decommission!</span></span> 
  
<span data-ttu-id="963f3-205">**サポート対象およびサポートされていないアップグレード ・ パス**を確認するのには注意してください。</span><span class="sxs-lookup"><span data-stu-id="963f3-205">Remember to review the **supported and unsupported upgrade paths**:</span></span> 
  
- <span data-ttu-id="963f3-206">
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)</span><span class="sxs-lookup"><span data-stu-id="963f3-206">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)</span></span>
    
- [<span data-ttu-id="963f3-207">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="963f3-207">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [<span data-ttu-id="963f3-208">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="963f3-208">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843157)
    
<span data-ttu-id="963f3-209">**カスタマイズ**をした場合は、計画がある、ステップごとに、アップグレード、移行パスでが重要です。</span><span class="sxs-lookup"><span data-stu-id="963f3-209">If you have **customizations**, it's critical you have a plan your upgrade for each step in the migration path:</span></span> 
  
- [<span data-ttu-id="963f3-210">SharePoint 2007</span><span class="sxs-lookup"><span data-stu-id="963f3-210">SharePoint 2007</span></span>](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [<span data-ttu-id="963f3-211">SharePoint Server 2010</span><span class="sxs-lookup"><span data-stu-id="963f3-211">SharePoint Server 2010</span></span>](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [<span data-ttu-id="963f3-212">SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="963f3-212">SharePoint Server 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843162)
    
|<span data-ttu-id="963f3-213">**オンプレミス Pro**</span><span class="sxs-lookup"><span data-stu-id="963f3-213">**On-premises Pro**</span></span>|<span data-ttu-id="963f3-214">**設置詐欺**</span><span class="sxs-lookup"><span data-stu-id="963f3-214">**On-premises Con**</span></span>|
|:-----|:-----|
|<span data-ttu-id="963f3-215">サーバー ハードウェアを SharePoint ファームのすべての側面に対するフル コントロール。</span><span class="sxs-lookup"><span data-stu-id="963f3-215">Full control of all aspects of your SharePoint Farm, from the server hardware up.</span></span>  <br/> |<span data-ttu-id="963f3-216">すべての破断や修正プログラムは、(取り組むことができますマイクロソフトの有償サポート、製品サポートの端にある場合)、会社の責任。</span><span class="sxs-lookup"><span data-stu-id="963f3-216">All breaks and fixes are the responsibility of your company (can engage paid Microsoft Support if your product is not at end of support):</span></span>  <br/> |
|<span data-ttu-id="963f3-217">SharePoint サーバー設置型のハイブリッドを使用して SharePoint Online サブスクリプションに、オンプレミスのファームに接続するためのオプションの完全な機能セットです。</span><span class="sxs-lookup"><span data-stu-id="963f3-217">Full feature set of SharePoint Server on-premises with the option to connect your on-premises farm to a SharePoint Online subscription via hybrid.</span></span>  <br/> |<span data-ttu-id="963f3-218">アップグレード、修正プログラム、セキュリティ修正プログラム、および SharePoint サーバーのすべての保守作業は、設置型を管理します。</span><span class="sxs-lookup"><span data-stu-id="963f3-218">Upgrade, patches, security fixes, and all maintenance of SharePoint Server managed on-premises.</span></span>  <br/> |
|<span data-ttu-id="963f3-219">アクセスより詳細にカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="963f3-219">Full access for greater customization.</span></span>  <br/> |<span data-ttu-id="963f3-220">[Office 365 でサポートされているコンプライアンス基準](https://go.microsoft.com/fwlink/?linkid=843165)には、オンプレミスで手動で構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="963f3-220">[Compliance standards supported by Office 365](https://go.microsoft.com/fwlink/?linkid=843165) must be manually configured on-premises.</span></span>  <br/> |
|<span data-ttu-id="963f3-221">セキュリティ テスト、およびサーバーのパフォーマンスのチューニング、上で実行されるお客様のサイト (制御です)。</span><span class="sxs-lookup"><span data-stu-id="963f3-221">Security testing, and server performance tuning, carried out on your premises (is under your control).</span></span>  <br/> |<span data-ttu-id="963f3-222">Office 365 にすることが機能使用可能な SharePoint オンラインの SharePoint サーバーの設置型と相互運用できません。</span><span class="sxs-lookup"><span data-stu-id="963f3-222">Office 365 may make features available to SharePoint Online that do not interoperate with SharePoint Server on-premises</span></span>  <br/> |
|<span data-ttu-id="963f3-223">パートナーは、移行を支援できる SharePoint サーバーの (および外) は、次のバージョンへのデータ。</span><span class="sxs-lookup"><span data-stu-id="963f3-223">Partners can assist with migrating data to the next version of SharePoint Server (and beyond).</span></span>  <br/> |<span data-ttu-id="963f3-224">SharePoint サーバーのサイトに自動的には使用されません[SSL や TLS](https://go.microsoft.com/fwlink/?linkid=843167)証明書 SharePoint Online] に表示されるように。</span><span class="sxs-lookup"><span data-stu-id="963f3-224">Your SharePoint Server sites will not automatically use [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) certificates as is seen in SharePoint Online.</span></span>  <br/> |
|<span data-ttu-id="963f3-225">名前付け規則、バックアップと復元、および SharePoint サーバーの設置型の場合は、他の回復オプションのフル コントロール。</span><span class="sxs-lookup"><span data-stu-id="963f3-225">Full control of naming conventions, backup and restore and other recovery options in SharePoint Server on-premises.</span></span>  <br/> |<span data-ttu-id="963f3-226">SharePoint サーバーの設置型は、製品のライフ サイクルに重要です。</span><span class="sxs-lookup"><span data-stu-id="963f3-226">SharePoint Server on-premises is sensitive to product lifecycles.</span></span>  <br/> |
   
### <a name="upgrade-resources"></a><span data-ttu-id="963f3-227">リソースをアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="963f3-227">Upgrade Resources</span></span>

<span data-ttu-id="963f3-228">ハードウェアとソフトウェアの要件に対応し、次のことを知ることによって開始には、アップグレードの方法がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="963f3-228">Begin by knowing that you meet hardware and software requirements, then follow supported upgrade methods.</span></span>
  
- <span data-ttu-id="963f3-229">**ハードウェア/ソフトウェアの要件**:</span><span class="sxs-lookup"><span data-stu-id="963f3-229">**Hardware/software requirements for**:</span></span> 
    
    <span data-ttu-id="963f3-230">[SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint サーバー 2016年](https://go.microsoft.com/fwlink/?linkid=843207)</span><span class="sxs-lookup"><span data-stu-id="963f3-230">[SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)</span></span>
    
- <span data-ttu-id="963f3-231">**ソフトウェアの境界と制限**します。</span><span class="sxs-lookup"><span data-stu-id="963f3-231">**Software boundaries and limits for**:</span></span> 
    
    <span data-ttu-id="963f3-232">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint サーバー 2016年](https://go.microsoft.com/fwlink/?linkid=843249)</span><span class="sxs-lookup"><span data-stu-id="963f3-232">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)</span></span>
    
- <span data-ttu-id="963f3-233">**のアップグレード プロセスの概要**:</span><span class="sxs-lookup"><span data-stu-id="963f3-233">**The upgrade process overview for**:</span></span> 
    
    <span data-ttu-id="963f3-234">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint サーバー 2016年](https://go.microsoft.com/fwlink/?linkid=843359)</span><span class="sxs-lookup"><span data-stu-id="963f3-234">[SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250) | [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251) | [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252) | [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)</span></span>
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a><span data-ttu-id="963f3-235">SharePoint Online と設置型の SharePoint のハイブリッド ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="963f3-235">Create a SharePoint hybrid solution between SharePoint Online and on-premises</span></span>

<span data-ttu-id="963f3-p118">回答した場合、移行のニーズにはどこかに設置し、SharePoint Online で提供されている所有権の低コストで提供されている放置の間を組み合わせたものを SharePoint Online では、SharePoint Server 2013 または 2016 ファームを接続できます。[ハイブリッド ソリューションの SharePoint について理解します。](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)</span><span class="sxs-lookup"><span data-stu-id="963f3-p118">If the answer to your migration needs is somewhere between the self-control offered by on-premises, and the lower cost of ownership offered by SharePoint Online, you can connect SharePoint Server 2013 or 2016 farms to SharePoint Online, through hybrids. [Learn about SharePoint hybrid solutions](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)</span></span>
  
<span data-ttu-id="963f3-238">ハイブリッドの SharePoint サーバー ファームにお客様のビジネス メリットをもたらすことを決定する場合、設置型の SharePoint ファームと Office 365 サブスクリプション間の接続を構成する方法と、ハイブリッドの既存の型を確認します。</span><span class="sxs-lookup"><span data-stu-id="963f3-238">If you decide that a hybrid SharePoint Server farm will benefit your business, familiarize yourself with the existing types of hybrid and how to configure the connection between your on-premises SharePoint farm and your Office 365 subscription.</span></span>
  
<span data-ttu-id="963f3-p119">この動作を確認する方法の 1 つは、 [Office 365 の開発/テスト環境](https://go.microsoft.com/fwlink/?linkid=843152)を作成することによってです。試用版があるか、Office 365 のサブスクリプションを購入するには、なりますようにデータを移行することができますし、SharePoint Online サイト コレクション、web、およびドキュメント ライブラリを作成する (使用するか、手動での移行 API、または移行する場合は、マイサイトのコンテンツのビジネス ・ OneDrive にハイブリッドのウィザードを使用)。</span><span class="sxs-lookup"><span data-stu-id="963f3-p119">One good way to see how this works is by creating an [Office 365 dev/test environment](https://go.microsoft.com/fwlink/?linkid=843152). Once you have a trial or purchased Office 365 subscription, you'll be on your way to creating the site collections, webs, and document libraries in SharePoint Online to which you can migrate data (either manually, by use of the Migration API, or - if you want to migrate My Site content to OneDrive for Business - through the hybrid wizard).</span></span>
  
> [!NOTE]
> <span data-ttu-id="963f3-241">SharePoint 2007 ファームをアップグレードする必要があることに注意してください、設置型、型、または SharePoint Server 2013 ハイブリッド オプションを使用する SharePoint サーバー 2016年</span><span class="sxs-lookup"><span data-stu-id="963f3-241">Remember that your SharePoint 2007 farm will need to be upgraded, on-premises, to either SharePoint Server 2013 or SharePoint Server 2016 to use the hybrid option</span></span> 
  
## <a name="related-topics"></a><span data-ttu-id="963f3-242">関連項目</span><span class="sxs-lookup"><span data-stu-id="963f3-242">Related topics</span></span>

[<span data-ttu-id="963f3-243">トラブルシューティングを行うし、(Office SharePoint Server 2007) のアップグレードを再開します。</span><span class="sxs-lookup"><span data-stu-id="963f3-243">Troubleshoot and resume upgrade (Office SharePoint Server 2007)</span></span>](https://go.microsoft.com/fwlink/?linkid=843192)
  
[<span data-ttu-id="963f3-244">(SharePoint Server 2010) のアップグレードの問題のトラブルシューティングを行う</span><span class="sxs-lookup"><span data-stu-id="963f3-244">Troubleshoot upgrade issues (SharePoint Server 2010)</span></span>](https://go.microsoft.com/fwlink/?linkid=843194)
  
[<span data-ttu-id="963f3-245">SharePoint 2013 でのデータベース アップグレードの問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="963f3-245">Troubleshoot database upgrade issues in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/?linkid=843195)
  
[<span data-ttu-id="963f3-246">アップグレードを支援するマイクロソフトのパートナーの検索</span><span class="sxs-lookup"><span data-stu-id="963f3-246">Search for Microsoft Partners to help with Upgrade</span></span>](https://go.microsoft.com/fwlink/?linkid=841249)
  
[<span data-ttu-id="963f3-247">2007 のサーバーとクライアントの Office からアップグレードするためのリソース</span><span class="sxs-lookup"><span data-stu-id="963f3-247">Resources to help you upgrade from Office 2007 servers and clients</span></span>](upgrade-from-office-2007-servers-and-products.md)
  

