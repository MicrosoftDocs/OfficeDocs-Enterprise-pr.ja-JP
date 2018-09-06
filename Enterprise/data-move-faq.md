---
title: データ移行についての一般的な FAQ
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 09/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: ここでは、コア データを新しいデータセンター geo に移行することについての一般的な質問に対する回答を示します。
ms.openlocfilehash: fe2399afa81a189416c41e3acba67e53eb99c674
ms.sourcegitcommit: 75ad9af1fa8adc73611fc6140546222b001861d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "23839595"
---
# <a name="data-move-general-faq"></a><span data-ttu-id="a0d79-103">データ移行についての一般的な FAQ</span><span class="sxs-lookup"><span data-stu-id="a0d79-103">Data move general FAQ</span></span>

<span data-ttu-id="a0d79-104">ここでは、コア データを新しいデータセンター geo に移行することについての一般的な質問に対する回答を示します。</span><span class="sxs-lookup"><span data-stu-id="a0d79-104">Here are answers to general questions about moving core data to a new datacenter geo.</span></span>
  
 <span data-ttu-id="a0d79-105">**Q. どのように確実に移行中の顧客データを保護し、ダウンタイムが発生しないようにするのですか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-105">**Q. How do you make sure my customer data is safe during the move and that I won't experience downtime?**</span></span>
  
<span data-ttu-id="a0d79-p101">A: データの移動は、エンド ・ ユーザーへの影響を最小限に抑えるとバックエンド ・ サービスの操作です。[中とデータの移動後](during-and-after-your-data-move.md)に、影響を受けることができる機能が一覧表示されます。おは、お客様は、準備や移動中に監視する必要があることはありませんので場合に、可用性を実現する[Microsoft Online Services サービス レベル契約 (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897)に準拠します。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p101">A. Data moves are a back-end service operation with minimal impact to end-users. Features that can be impacted are listed in [During and after your data move](during-and-after-your-data-move.md). We adhere to the [Microsoft Online Services Service Level Agreement (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) for availability so there is nothing that customers need to prepare for or to monitor during the move.</span></span> 
  
<span data-ttu-id="a0d79-p102">Office 365 サービスは、どのデータセンターでもすべて同じバージョンが実行されるため、機能の一貫性が確保されます。このプロセス中、サービスは完全にサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p102">All Office 365 services run the same versions in the datacenters, so you can be assured of consistent functionality. Your service is fully supported throughout the process.</span></span>
  
 <span data-ttu-id="a0d79-112">**Q. 異なる geo に異なるサービスがあることには、どんな影響がありますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-112">**Q. What is the impact of having different services located in different geos?**</span></span>
  
<span data-ttu-id="a0d79-p103">A. 一部の既存のお客様と移行プロセス中のお客様は、いくつかの Office 365 サービスが異なる geo にあることがあります。当社のサービスはそれぞれ独立して動作するため、この場合、ユーザーへの影響はありません。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p103">A. For some existing customers and customers in the middle of the move process, some of the Office 365 services may be located in different geos. Our services run independently of each other and there is no user impact if this is the case.</span></span>
  
 <span data-ttu-id="a0d79-116">**Q. 新しい Office 365 のユーザーは自動的に新しいデータセンター geo でプロビジョニングされますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-116">**Q. Will new Office 365 customers be automatically provisioned in the new datacenter geos?**</span></span>
  
<span data-ttu-id="a0d79-p104">A. はい。新しいデータセンター geo が利用可能になると、サインアップ中に自分の国として新しい geo の対象となる国を選択した新しい Office 365 ビジネス ユーザーのコア データは、新しいデータセンター geo でホストされます。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p104">A. Yes. Once a new datacenter geo is available, new Office 365 for business customers who select a country eligible for the new geo as their country during sign-up will have their core data hosted in the new datacenter geo.</span></span>
  
 <span data-ttu-id="a0d79-120">**Q. データの保存場所はどこですか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-120">**Q. Where is my data is located?**</span></span>
  
<span data-ttu-id="a0d79-p105">[ Office 365 対話型データ センター マップ ](https://o365datacentermap.azurewebsites.net) で、データセンター geo の場所、データセンター、および顧客データの場所を公開します。8 月 1 日現在、顧客データの場所は、Office 365 管理センターの [組織プロファイル] の [データ場所] セクションから確認できます。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p105">We publish the location of datacenter geos, datacenters, and location of customer data on the [ Office 365 interactive datacenter maps ](https://o365datacentermap.azurewebsites.net). As of August 1, you will be able to verify the location of your customer data at rest via the Data Location section under your Organization Profile in the Office 365 Admin Center.</span></span>
  
 <span data-ttu-id="a0d79-123">**Q. 既存の Office 365 のユーザーは新しいデータ センター geo に移行されますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-123">**Q. Will existing Office 365 customers be moved to the new datacenter geos?**</span></span>
  
<span data-ttu-id="a0d79-p106">A. 対象となる Office 365 のユーザーは、コア データを新しい geo に移行することをリクエストできます。お客様は、自分の geo の期限までにリクエストを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p106">A. Eligible Office 365 customers can request to have their core data moved to the new geos. Customers will need to submit a request before the deadline for their geo in order to participate.</span></span> 
  
 <span data-ttu-id="a0d79-127">**Q. 移行をリクエストする対象となるのは、どんなお客様ですか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-127">**Q. What customers are eligible to request a move?**</span></span>
  
<span data-ttu-id="a0d79-p107">A. 新しいデータセンター geo の対象となる国を選択した既存の Office 365 の商用ユーザーは、移行をリクエストできます。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p107">A. Existing Office 365 commercial customers who selected a country eligible for the new datacenter geo will be able to request a move.</span></span> 
  
 <span data-ttu-id="a0d79-130">**Q. いつから移行をリクエストできますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-130">**Q. When will I be able to request a move?**</span></span>
  
<span data-ttu-id="a0d79-p108">A. リクエスト期間は [データ移行をリクエストする方法](request-your-data-move.md) ページで発表されます。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p108">A. The request period will be announced on the [How to request your data move](request-your-data-move.md) page.</span></span> 
  
 <span data-ttu-id="a0d79-133">**Q. どのように移行をリクエストしますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-133">**Q. How can I request to be moved?**</span></span>
  
<span data-ttu-id="a0d79-p109">A. 対象となるお客様には、[Office 365 管理ポータル](https://portal.office.com/)のページが表示されます。移行をリクエストする手順については「[データ移行をリクエストする方法](request-your-data-move.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p109">A. Eligible customers will see a page in their [Office 365 Admin Portal](https://portal.office.com/). Please see [How to request your data move](request-your-data-move.md) for instructions on how to request a move.</span></span> 
  
 <span data-ttu-id="a0d79-137">**Q. 移行をリクエストした後で自分の決定を変更できますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-137">**Q. Can I change my selection after requesting a move?**</span></span>
  
<span data-ttu-id="a0d79-p110">A. リクエストを送信した後に、Microsoft 側で移行プロセスからお客様を削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p110">A. It is not possible for us to remove you from the process after you submit your request.</span></span>
  
 <span data-ttu-id="a0d79-140">**Q. 期限までに移行をリクエストしないと、どうなりますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-140">**Q. What happens if I do not request a move before the deadline?**</span></span>
  
<span data-ttu-id="a0d79-p111">A. 各 geo の期限が過ぎた後に、移行に関するリクエストを受け付けることはできません。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p111">A. We are unable to accept requests to be moved after the deadline in each geo.</span></span>
  
 <span data-ttu-id="a0d79-143">**Q. ネットワークのパフォーマンスを向上するために、データを移動したらどうなりますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-143">**Q. What if I want to move my data in order to get better network performance?**</span></span>
  
<span data-ttu-id="a0d79-p112">Office 365 のデータ センターの距離が近いことは、ネットワークのパフォーマンスを向上させる保証ではありません。多くの要因とエンド ・ ユーザーと Office 365 サービスの間のネットワーク パフォーマンスに影響を与えるコンポーネントがあります。詳細については、パフォーマンス ・ チューニング、[ネットワークを計画し Office 365 のパフォーマンスの調整](network-planning-and-performance.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p112">Being close to an Office 365 datacenter is not a guarantee for a better networking performance. There are many factors and components that impact the network performance between the end user and the Office 365 service. For more information about this and performance tuning see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>
  
 <span data-ttu-id="a0d79-147">**Q. すべてのサービスは同じ日にデータを移行しますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-147">**Q. Do all the services move their data on the same day?**</span></span>
  
<span data-ttu-id="a0d79-p113">A. サービスはデータを同時に移行しません。各サービスはデータを個別に移行します。移行する時期も異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p113">A. The services do not move their data at the same time. Each service will move independently and will likely move their data at different times.</span></span>
  
 <span data-ttu-id="a0d79-151">**Q. データを移行する時期を自分で選ぶことはできますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-151">**Q. Can I choose when I want my data to be moved?**</span></span>
  
<span data-ttu-id="a0d79-p114">A. お客様は特定の日を選択したり、移行を遅らせたりできません。Microsoft が移行の具体的な日付や期間を共有することもできません。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p114">A. Customers are not able to select a specific date, they cannot delay their move, and we cannot share a specific date or timeframe for the moves.</span></span>
  
 <span data-ttu-id="a0d79-154">**Q. データの移動時に共有することは可能ですか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-154">**Q. Can you share when my data will be be moved?**</span></span>
  
<span data-ttu-id="a0d79-p115">A.データの移行は、エンドユーザーへの影響を最小限に抑えたバックエンドの操作です。グローバルに操作され自動化された環境内でデータ移動を実行する際に必要になる複雑さ、精度およびスケールは、テナントまたはその他の任意の単一テナントがデータ移動の完了を期待しているときに、共有の妨げになります。お客様のデータ移動が完了すると、お客様はメッセージ センターで、参加しているサービスごとに 1 つの確認メッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p115">A. Data moves are a back-end operation with minimal impact to end-users. The complexity, precision and scale at which we need to perform data moves within a globally operated and automated environment prohibit us from sharing when a data move is expected to complete for your tenant or any other single tenant. Customers will receive one confirmation in Message Center per participating service when its data move has completed.</span></span> 
  
 <span data-ttu-id="a0d79-159">**Q. データの移行中に、ユーザーがサービスにアクセスすると、どうなりますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-159">**Q. What happens if users access services while the data is being moved?**</span></span>
  
<span data-ttu-id="a0d79-p116">A. 各サービスのデータの移行中に制限される機能の詳細な一覧については「[データの移行中および移行後](during-and-after-your-data-move.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p116">A. See [During and after your data move](during-and-after-your-data-move.md) for a complete list of features that may be limited during portions of the data move for each service.</span></span> 
  
 <span data-ttu-id="a0d79-162">**Q. 移行が完了したことはどのようにわかりますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-162">**Q. How do I know the move is complete?**</span></span>
  
<span data-ttu-id="a0d79-p117">A. Office 365 メッセージ センターをご覧いただき、各サービスのデータ移行が完了したことをご確認ください。各サービスのデータ移行時には完了通知が投稿されます。そのため、Exchange Online、SharePoint Online、Skype for Business Online の 3 件の完了通知を受け取ることになります。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p117">A. Watch the Office 365 message center for confirmation that the move of each service's data is complete. When each service's data is moved, we'll post a completion notice so you'll get three completion notices: one each for Exchange Online, SharePoint Online, and Skype for Business Online.</span></span>
  
<span data-ttu-id="a0d79-166">移行後に問題が見られた場合は、[Office 365 サポート](https://go.microsoft.com/fwlink/p/?LinkID=522459)にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="a0d79-166">If you see any issues after the move, contact [Office 365 Support](https://go.microsoft.com/fwlink/p/?LinkID=522459) to get assistance.</span></span> 
  
 <span data-ttu-id="a0d79-167">**Q. 新しいデータセンター geo には、Office 365 のどのデータが格納されますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-167">**Q. What data for Office 365 is stored in the new datacenter geos?**</span></span>
  
<span data-ttu-id="a0d79-p118">A. お客様が新しいデータセンター geo のいずれか 1 つにテナントをプロビジョニングする場合、Microsoft はその geo に次の顧客データを格納します。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p118">A. If a customer provisions its tenant in one of the new datacenter geos, Microsoft stores the following customer data at rest within the geo:</span></span>
  
- <span data-ttu-id="a0d79-170">ExchangeOnline メールボックスのコンテンツ (メール本文、予定表のエントリ、メール添付ファイルのコンテンツ)。</span><span class="sxs-lookup"><span data-stu-id="a0d79-170">Exchange Online mailbox content (e-mail body, calendar entries, and the content of email attachments)</span></span>
    
- <span data-ttu-id="a0d79-171">SharePointOnline サイトのコンテンツとそのサイト内に入っているファイル (Project Online と Access Online のコンテンツを含む)。</span><span class="sxs-lookup"><span data-stu-id="a0d79-171">SharePoint Online site content and the files stored within that site, including Project Online and Access Online content.</span></span>
    
<span data-ttu-id="a0d79-172">さらに、このデータは geo の外ではレプリケートされません。</span><span class="sxs-lookup"><span data-stu-id="a0d79-172">In addition, this data is not replicated outside of the geo.</span></span>
  
 <span data-ttu-id="a0d79-173">**Q. 私は新しいデータセンター geo にいる Office 365 のユーザーですが、サインアップ時には別の国を選択しました。新しいデータセンター geo に移行するにはどうすればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-173">**Q. I am an Office 365 customer in one of the new datacenter geos, but when I signed up, I selected a different country. How can I be moved to the new datacenter geo?**</span></span>
  
<span data-ttu-id="a0d79-p119">A. 残念ながら、テナントに関連付けられた国を変更することはできません。代わりに、新しいサブスクリプションで新しい Office 365 テナントを作成し、ユーザーとデータを手動で新しいテナントに移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p119">A. Unfortunately, it is not possible to change the country associated with your tenant. Instead, you need to create a new Office 365 tenant with a new subscription and manually move your users and data to the new tenant.</span></span>
  
 <span data-ttu-id="a0d79-177">**Q. 課金については、何らかの変更がありますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-177">**Q. Will there be any changes on my bill?**</span></span>
  
<span data-ttu-id="a0d79-p120">A. ほとんどの場合、お客様がご覧になる請求書に変更はありません。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p120">A. In most cases there are no changes that customers in will see on their billing statement.</span></span>
  
<span data-ttu-id="a0d79-p121">Microsoft は Office 365 のオーストラリアのすべてのお客様に対して、Office 365 サービスのオーストラリア物品サービス税 (GST) を加算して課金し、税の請求書を発行いたします。これは、オーストラリアの商品サービス税の課税対象がオーストラリア国内で提供される商品サービスであることに伴う変更です。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p121">Microsoft will charge all Australian customers of Office 365 an additional amount equal to the Australian GST for Office 365 services and will issue tax invoices. This change will occur because Australian GST is payable on taxable supplies of goods and services provided and offered in Australia.</span></span>
  
 <span data-ttu-id="a0d79-182">**Q. Exchange Online の移行中にメール データの Office 365 への移行が進行中の場合、どんなことが生じますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-182">**Q. What happens if we are in process of email data migration to Office 365 during the Exchange Online move?**</span></span>
  
<span data-ttu-id="a0d79-p122">A. メールの移行が進行中の場合、現在移行中のそれぞれのメールボックスはテナントの移行が完了するまでキャンセルされ、こうしたメールボックスの移行はテナントが宛先のデータセンターに配置されると自動的に再開されます。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p122">A. If email migrations are in progress, any individual mailboxes that are currently being migrated will be canceled while the tenant move finalizes, and migration of those mailboxes will automatically restart once the tenant is in the target datacenters.</span></span>
  
 <span data-ttu-id="a0d79-185">**Q. データが以前のデータセンター geo から移行した後、そのデータは元のデータセンターから削除されるのですか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-185">**Q. After data is moved out of the previous datacenter geo, is it removed from those datacenters?**</span></span>
  
<span data-ttu-id="a0d79-p123">A. はい。前のデータは、一定期間後に削除されます。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p123">A. Yes, the old data will be purged after a period of time.</span></span>
  
 <span data-ttu-id="a0d79-188">**Q. 一部のユーザーを先に移行できますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-188">**Q. Can I pilot some users?**</span></span>
  
<span data-ttu-id="a0d79-p124">A. Office 365 テナントが新しいデータセンター geo に移行されるときには、すべてのユーザーが一度に移行されます。接続をテストするために別の試用版テナントを作成することはできますが、試用版テナントと既存のテナントを統合することはできません。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p124">A. When your Office 365 tenant is moved to a new datacenter geo, all users are moved at once. You can create a separate trial tenant to test connectivity, but the trial tenant can't be combined in any way with your existing tenant.</span></span>
  
 <span data-ttu-id="a0d79-192">**Q. 移行について私にはどのように通知され、私の会社ではだれに通知されますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-192">**Q. How will I be notified about the move and who at my company will be notified?**</span></span>
  
<span data-ttu-id="a0d79-p125">A. Office 365 メッセージ センターを利用します。これは、Office 365 で管理者アクセス許可を持つすべてのユーザーが閲覧できます。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p125">A. We'll use the Office 365 message center, which is visible to anyone with any admin permissions in Office 365.</span></span>
  
 <span data-ttu-id="a0d79-195">**Q. Microsoft が私のデータを移行するのを待ちたくありません。新しいテナントを作成して自分で移行することはできますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-195">**Q. I don't want to wait for Microsoft to move my data. Can I just create a new tenant and move myself?**</span></span>
  
<span data-ttu-id="a0d79-p126">A: はい。だたし、プロセスは Microsoft がデータ移行を実行するときと同じようにシームレスではありません。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p126">A. Yes, however the process will not be as seamless as if Microsoft were to perform the data move.</span></span>
  
<span data-ttu-id="a0d79-p127">新しいデータセンター geo が利用可能になった後に新しいテナントを作成すると、新しいテナントは新しい geo でホストされます。この新しいテナントは以前のテナントとは完全に別個のものであり、すべてのユーザー メールボックス、サイトのコンテンツ、ドメイン名、その他のデータの移行をお客様自身の責任で実行していただくことになります。なお、テナント名は 1 つのテナントから別のテナントへ移行できないことに注意してください。Microsoft によって提供される移行プログラムをお待ちいただくことをお勧めします。すべての設定、データ、ユーザーのサブスクリプションの移行は、弊社にお任せください。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p127">If you create a new tenant after the new datacenter geo is available, the new tenant will be hosted in the new geo. This new tenant is completely separate from your previous tenant and you would be responsible for moving all user mailboxes, site content, domain names, and any other data. Note that you can't move the tenant name from one tenant to another. We recommend that you wait for the move program provided by Microsoft as we'll take care of moving all settings, data, and subscriptions for your users.</span></span>
  
 <span data-ttu-id="a0d79-202">**Q. 移行の準備がまだできていないので、特定の移行日を選ぶことはできますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-202">**Q. I'm not ready to be moved, can I pick a specific move date?**</span></span>
  
<span data-ttu-id="a0d79-p128">A. 各サービスの顧客データの移行日は変更できません。データの移行は、エンドユーザーへの影響を最小限に抑えたバックエンドの操作です。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p128">A. It is not possible for you to change when each service's customer data will be moved. Data moves are a back-end operation with minimal impact to end-users.</span></span>
  
 <span data-ttu-id="a0d79-206">**Q. 私の顧客データは新しいデータセンター geo に既に移行しました。戻すことはできますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-206">**Q. My customer data has already been moved to a new datacenter geo. Can I move back?**</span></span>
  
<span data-ttu-id="a0d79-p129">A. できません。新しい geo のデータセンターに移行したお客様は、元の geo に戻ることはできません。任意の geo の顧客として、サービスの品質、パフォーマンス、およびセキュリティ コントロールに関して、これまでと同様のエクスペリエンスを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p129">A. This is not possible. Customers who have been moved to new geo datacenters cannot be moved back. As a customer in any geo, you will experience the same quality of service, performance, and security controls as you did before.</span></span>
  
 <span data-ttu-id="a0d79-211">**Q. 新しいデータセンター geo では、現在のデータセンター geo と同じバージョンの Office 365 サービスを使いますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-211">**Q. Do the new datacenter geos use the same versions of Office 365 services as the current datacenter geos?**</span></span>
  
<span data-ttu-id="a0d79-p130">A. はい。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p130">A. Yes.</span></span>
  
 <span data-ttu-id="a0d79-214">**Q. 新しいデータセンターでホストされる Office 365 テナントは、国外のユーザーも利用できますか?**</span><span class="sxs-lookup"><span data-stu-id="a0d79-214">**Q. Will Office 365 tenants hosted in the new datacenters be available to users outside of the country?**</span></span>
  
<span data-ttu-id="a0d79-p131">A. はい。Microsoft は、世界中の 23 か国の 50 を超える場所で公衆インターネットに接続する大規模なグローバル ネットワークを保有しており、1,500 を超えるインターネット サービス プロバイダー (ISP) と相互接続契約を結んでいます。インターネット上のどの場所にいるユーザーでも、データセンターにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a0d79-p131">A. Yes. Microsoft maintains a large global network with public Internet connections in more than 50 locations in 23 countries around the world with peering agreements with more than 1,500 Internet Service Providers (ISPs). Users will be able to access the datacenters from wherever they are on the Internet.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="a0d79-219">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0d79-219">Related topics</span></span>

[<span data-ttu-id="a0d79-220">コア データを新しい Office 365 データ センター geo に移行する</span><span class="sxs-lookup"><span data-stu-id="a0d79-220">Moving core data to new Office 365 datacenter geos</span></span>](moving-data-to-new-datacenter-geos.md)

[<span data-ttu-id="a0d79-221">データ移行をリクエストする方法</span><span class="sxs-lookup"><span data-stu-id="a0d79-221">How to request your data move</span></span>](request-your-data-move.md)

[<span data-ttu-id="a0d79-222">Microsoft Dynamics CRM Online の新しいデータ センター geo</span><span class="sxs-lookup"><span data-stu-id="a0d79-222">New datacenter geos for Microsoft Dynamics CRM Online</span></span>](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[<span data-ttu-id="a0d79-223">Azure のリージョン</span><span class="sxs-lookup"><span data-stu-id="a0d79-223">Azure services by region</span></span>](https://azure.microsoft.com/en-us/regions/)
