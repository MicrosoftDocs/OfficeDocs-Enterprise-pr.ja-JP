---
title: コア データを新しい Office 365 データ センター geo に移行する
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 3/22/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
description: '新しいデータ センターの地域では、容量を追加し、継続的な顧客の需要と使用率の増大をサポートするためにリソースを計算します。さらに、新しいデータ センターの地域は、主要な顧客データの地域のデータの常駐サービスを提供しています。コア カスタマー データは、Microsoft Online Services の用語で定義されている顧客データのサブセットを参照する用語: Exchange Online のメールボックスの内容 (電子メールの本文、予定表エントリ、および電子メールの添付ファイルの内容) と、SharePoint Online サイトのコンテンツとファイル、そのサイト内に格納し、ビジネスの OneDrive にファイルをアップロードします。'
ms.openlocfilehash: 1f3af15852b1221daf2e2d994653c8bb9cf697e4
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541765"
---
# <a name="moving-core-data-to-new-office-365-datacenter-geos"></a><span data-ttu-id="10732-105">コア データを新しい Office 365 データ センター geo に移行する</span><span class="sxs-lookup"><span data-stu-id="10732-105">Moving core data to new Office 365 datacenter geos</span></span>

<span data-ttu-id="10732-p102">私たちは、ビジネス サービスを Office 365 に新しいデータ センターの地域を開く」に進みます。これら新しいデータ センターの地域は、容量を追加し、継続的な顧客の需要と使用率の増大をサポートするためにリソースを計算します。さらに、新しいデータ センターの地域は、主要な顧客データの地域のデータの常駐サービスを提供しています。</span><span class="sxs-lookup"><span data-stu-id="10732-p102">We continue to open new datacenter geos for Office 365 for business services. These new datacenter geos add capacity and compute resources to support our ongoing customer demand and usage growth. Additionally, the new datacenter geos offer in-geo data residency for core customer data.</span></span> 

<span data-ttu-id="10732-109">コア カスタマー データは、 [Microsoft Online Services の用語](https://go.microsoft.com/fwlink/p/?LinkID=249048)で定義されている顧客データのサブセットを参照する用語です。</span><span class="sxs-lookup"><span data-stu-id="10732-109">Core customer data is a term that refers to a subset of customer data defined in the [Microsoft Online Services Terms](https://go.microsoft.com/fwlink/p/?LinkID=249048):</span></span> 
- <span data-ttu-id="10732-110">Exchange Online のメールボックスの内容 (電子メールの本文、予定表エントリ、および電子メールの添付ファイルの内容)</span><span class="sxs-lookup"><span data-stu-id="10732-110">Exchange Online mailbox content (email body, calendar entries, and the content of email attachments)</span></span>
- <span data-ttu-id="10732-111">SharePoint Online サイトのコンテンツとそのサイト内に保存されたファイル</span><span class="sxs-lookup"><span data-stu-id="10732-111">SharePoint Online site content and the files stored within that site</span></span>
- <span data-ttu-id="10732-112">ビジネスの OneDrive にアップロードされたファイル</span><span class="sxs-lookup"><span data-stu-id="10732-112">Files uploaded to OneDrive for Business</span></span> 
  
<span data-ttu-id="10732-p103">既存のデータセンター geo に保存されるコア カスタマー データを持つ既存のお客様は、新しいデータセンター geo の導入による影響を受けません。新しいデータセンター geo では、独自機能や準拠証明書を導入していしません。これら 2 つの任意の geo のお客様として、サービスの品質、パフォーマンス、およびセキュリティ コントロールに関して、これまでと同様のエクスペリエンスを得ることができます。次の表にリストされている、厳格なデータ常駐の要件を持つ既存のお客様には、お客様のコア カスタマー データを新しい geo へ移動するオプションを提供しています。</span><span class="sxs-lookup"><span data-stu-id="10732-p103">Existing customers that have their core customer data stored in an already existing datacenter geo are not impacted by the launch of a new datacenter geo. We introduce no unique capabilities, features or compliance certifications with the new datacenter geo. As a customer in any of those two geos, you will experience the same quality of service, performance and security controls as you did before. We offer existing customers that have strict data residency requirements, and that are listed in the table below, an option to have their core customer data moved to the new geo.</span></span>
  
|<span data-ttu-id="10732-117">****請求先住所のお客様****</span><span class="sxs-lookup"><span data-stu-id="10732-117">****Customers with billing address in****</span></span>|<span data-ttu-id="10732-118">****以前のデータ センター geo****</span><span class="sxs-lookup"><span data-stu-id="10732-118">****Previous datacenter geo****</span></span>|<span data-ttu-id="10732-119">****新しいデータ センター geo****</span><span class="sxs-lookup"><span data-stu-id="10732-119">****New datacenter geo****</span></span>|<span data-ttu-id="10732-120">****以降は geo が利用可能****</span><span class="sxs-lookup"><span data-stu-id="10732-120">****Geo available since****</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="10732-121">****日本****</span><span class="sxs-lookup"><span data-stu-id="10732-121">****Japan****</span></span>| <span data-ttu-id="10732-122">アジア/太平洋地域</span><span class="sxs-lookup"><span data-stu-id="10732-122">Asia/Pacific</span></span> | <span data-ttu-id="10732-123">日本</span><span class="sxs-lookup"><span data-stu-id="10732-123">Japan</span></span> | <span data-ttu-id="10732-124">2014 年 12 月</span><span class="sxs-lookup"><span data-stu-id="10732-124">December 2014</span></span> |
|<span data-ttu-id="10732-125">****オーストラリア、ニュージーランド、フィジー****</span><span class="sxs-lookup"><span data-stu-id="10732-125">****Australia, New Zealand, Fiji****</span></span>| <span data-ttu-id="10732-126">アジア/太平洋地域</span><span class="sxs-lookup"><span data-stu-id="10732-126">Asia/Pacific</span></span> | <span data-ttu-id="10732-127">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="10732-127">Australia</span></span> | <span data-ttu-id="10732-128">2015 年 3 月</span><span class="sxs-lookup"><span data-stu-id="10732-128">March 2015</span></span> |
|<span data-ttu-id="10732-129">****インド****</span><span class="sxs-lookup"><span data-stu-id="10732-129">****India****</span></span>| <span data-ttu-id="10732-130">アジア/太平洋地域</span><span class="sxs-lookup"><span data-stu-id="10732-130">Asia/Pacific</span></span> | <span data-ttu-id="10732-131">インド</span><span class="sxs-lookup"><span data-stu-id="10732-131">India</span></span> | <span data-ttu-id="10732-132">2015 年 10 月</span><span class="sxs-lookup"><span data-stu-id="10732-132">October 2015</span></span> |
|<span data-ttu-id="10732-133">****カナダ****</span><span class="sxs-lookup"><span data-stu-id="10732-133">****Canada****</span></span>| <span data-ttu-id="10732-134">北アメリカ</span><span class="sxs-lookup"><span data-stu-id="10732-134">North America</span></span> | <span data-ttu-id="10732-135">カナダ</span><span class="sxs-lookup"><span data-stu-id="10732-135">Canada</span></span> | <span data-ttu-id="10732-136">2016 年 5 月</span><span class="sxs-lookup"><span data-stu-id="10732-136">May 2016</span></span> |
|<span data-ttu-id="10732-137">****英国****</span><span class="sxs-lookup"><span data-stu-id="10732-137">****United Kingdom****</span></span>| <span data-ttu-id="10732-138">ヨーロッパ</span><span class="sxs-lookup"><span data-stu-id="10732-138">Europe</span></span> | <span data-ttu-id="10732-139">英国</span><span class="sxs-lookup"><span data-stu-id="10732-139">United Kingdom</span></span> | <span data-ttu-id="10732-140">2016 年 9 月</span><span class="sxs-lookup"><span data-stu-id="10732-140">September 2016</span></span> |
|<span data-ttu-id="10732-141">****韓国****</span><span class="sxs-lookup"><span data-stu-id="10732-141">****South Korea****</span></span>| <span data-ttu-id="10732-142">アジア/太平洋地域</span><span class="sxs-lookup"><span data-stu-id="10732-142">Asia/Pacific</span></span> | <span data-ttu-id="10732-143">韓国</span><span class="sxs-lookup"><span data-stu-id="10732-143">South Korea</span></span> | <span data-ttu-id="10732-144">2017 年 4 月</span><span class="sxs-lookup"><span data-stu-id="10732-144">April 2017</span></span> |
|<span data-ttu-id="10732-145">****フランス****</span><span class="sxs-lookup"><span data-stu-id="10732-145">****France****</span></span>| <span data-ttu-id="10732-146">ヨーロッパ</span><span class="sxs-lookup"><span data-stu-id="10732-146">Europe</span></span> | <span data-ttu-id="10732-147">フランス</span><span class="sxs-lookup"><span data-stu-id="10732-147">France</span></span> | <span data-ttu-id="10732-148">2018 年 3 月</span><span class="sxs-lookup"><span data-stu-id="10732-148">March 2018</span></span> |
   
> [!NOTE]
> <span data-ttu-id="10732-p104">データ常駐オプション、およびお客様のデータを新しい geo へ移動するための可用性は、マイクロソフトが立ち上げる新しい geo のすべてに既定になるわけではありません。将来、新しい geo に拡張する際には、geo ごとの単位でデータ移動の可用性と条件を評価する予定です。</span><span class="sxs-lookup"><span data-stu-id="10732-p104">The data residency option, and the availability to move customer data into the new geo, is not a default for every new geo we launch. As we expand into new geos in the future, we'll evaluate the availability and the conditions of data moves on a geo by geo basis.</span></span> 
  
<span data-ttu-id="10732-151">新規のお客様、または新しいデータセンター geo の後に作成された Office 365 テナントには、自動的に新しいデータセンター geo に格納されているコア カスタマー データがあります。</span><span class="sxs-lookup"><span data-stu-id="10732-151">New customers or Office 365 tenants created after the availability of the new datacenter geo will have their core customer data stored at rest in the new datacenter geo automatically.</span></span>
  
<span data-ttu-id="10732-152">すべてのデータセンター geo、データセンター、格納されているお客様データの場所のリストは、[対話型のデータセンター マップ](https://aka.ms/dcmaps)の一部として利用できます。</span><span class="sxs-lookup"><span data-stu-id="10732-152">A complete list of all datacenter geos, datacenters, and the location of customer data at rest is available as part of the [interactive datacenter maps](https://aka.ms/dcmaps).</span></span> 
  
## <a name="data-residency-option"></a><span data-ttu-id="10732-153">データ常駐のオプション</span><span class="sxs-lookup"><span data-stu-id="10732-153">Data residency option</span></span>

<span data-ttu-id="10732-p105">上記の表にリストされているデータセンター geo でカバーされている、既存の Office 365 のお客様には、データ常駐のオプションを提供しています。このオプションにより、データ常駐の要件があるお客様は、コア カスタマー データを新しい geo に移動するよう要求できます。お客様には、お客様の組織が各自の新しいデータセンター geo で保存されているコア カスタマー データを必要としない限り、何もしないことをお勧めします。データの移行を選択することにより、お客様は、コア カスタマー データをお客様の現在の geo か新しいデータセンター geo のどちらか最適な場所にある、Microsoft の可能性を制限します。これら 2 つの任意の geo のお客様として、サービスの品質、パフォーマンス、およびセキュリティ コントロールに関して、これまでと同様のエクスペリエンスを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="10732-p105">We provide a data residency option to existing Office 365 customers who are covered by the datacenter geos listed in the table above. With this option, customers with data residency requirements can request to move their core customer data into the new geo. We recommend our customers to take no action, unless their organization needs core customer data to be stored at rest in their respective new datacenter geo. By choosing to move their data, customers limit Microsoft's possibilities to optimize the location of core customer data at rest in either their current or the new datacenter geo. As a customer in any of those two geos, you will experience the same quality of service, performance and security controls as you did before.</span></span>
  
<span data-ttu-id="10732-159">コア データを新しい geo に移動する必要があるお客様の場合。</span><span class="sxs-lookup"><span data-stu-id="10732-159">For customers who need to have their core data moved to the new geo:</span></span>
  
- <span data-ttu-id="10732-p106">お客様は、お客様のデータを登録設定のウィンドウ内に移動するように、要求を行う必要があります。geo の登録ウィンドウと、プログラムに登録する手順の詳細については、「[データ移行をリクエストする方法](request-your-data-move.md)」ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="10732-p106">Customers will need to request to have their data moved within a set enrollment window. Review the [How to request your data move](request-your-data-move.md) page for more details about the enrollment window for your geo and the steps to enroll into the program.</span></span> 
    
- <span data-ttu-id="10732-162">要求期間の後、データの移動が完了するまでに、最大で 24 か月間かかります。</span><span class="sxs-lookup"><span data-stu-id="10732-162">Data moves can take up to 24 months after the request period to complete.</span></span>
    
- <span data-ttu-id="10732-163">新しいデータセンター geo では、独自機能や準拠証明書を導入していません。</span><span class="sxs-lookup"><span data-stu-id="10732-163">We introduce no unique capabilities, features or compliance certifications with the new datacenter geo.</span></span>
    
- <span data-ttu-id="10732-p107">グローバルに操作され自動化された環境内でデータ移動を実行する際に必要になる複雑さ、精度およびスケールは、テナントまたはその他の任意の単一テナントがデータ移動の完了を期待しているときに、共有の妨げになります。お客様のデータ移動が完了すると、お客様はメッセージ センターで、参加しているサービスごとに 1 つの確認メッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="10732-p107">The complexity, precision and scale at which we need to perform data moves within a globally operated and automated environment prohibit us from sharing when a data move is expected to complete for your tenant or any other single tenant. Customers will receive one confirmation in Message Center per participating service when its data move has completed.</span></span> 
    
- <span data-ttu-id="10732-p108">データの移行は、エンドユーザーへの影響を最小限に抑えたバックエンド サービスの操作です。影響を受ける機能については「[データの移行中および移行後](during-and-after-your-data-move.md)」ページに記載されています。可用性については、[Microsoft Online Services サービス レベル契約 (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897)に準拠しています。お客様が、移行に伴って準備や監視を行う必要はありません。必要に応じて、サービス メンテナンスの通知が行われます。</span><span class="sxs-lookup"><span data-stu-id="10732-p108">Data moves are a back-end service operation with minimal impact to end-users. Features that can be impacted are listed on the [During and after your data move](during-and-after-your-data-move.md) page. We adhere to the [Microsoft Online Services Service Level Agreement (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) for availability so there is nothing that customers need to prepare for or to monitor during the move. Notification of any service maintenance is done if needed.</span></span> 
    
## <a name="related-topics"></a><span data-ttu-id="10732-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="10732-170">Related topics</span></span> 
 
[<span data-ttu-id="10732-171">データ移行をリクエストする方法</span><span class="sxs-lookup"><span data-stu-id="10732-171">How to request your data move</span></span>](request-your-data-move.md)
    
[<span data-ttu-id="10732-172">データ移行についての一般的な FAQ</span><span class="sxs-lookup"><span data-stu-id="10732-172">Data move general FAQ</span></span>](data-move-faq.md)
  
[<span data-ttu-id="10732-173">Microsoft Dynamics CRM Online の新しいデータ センター geo</span><span class="sxs-lookup"><span data-stu-id="10732-173">New datacenter geos for Microsoft Dynamics CRM Online</span></span>](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[<span data-ttu-id="10732-174">Azure のリージョン</span><span class="sxs-lookup"><span data-stu-id="10732-174">Azure services by region</span></span>](https://azure.microsoft.com/en-us/regions/)
  

