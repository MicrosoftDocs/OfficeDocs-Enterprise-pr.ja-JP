---
title: データ移行をリクエストする方法
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5bb64310-36fc-473d-b791-a0176f21707f
f1.keywords:
- NOCSH
description: 既存の Office 365 のお客様は、お住まいの国が新しい geo に Microsoft 365 サービスデータを移動する前に、要求を提出する必要があります。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 72b7c7d1f6b6b19ff5749787fd8ea6e789c3372a
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606163"
---
# <a name="how-to-request-your-data-move"></a><span data-ttu-id="42dba-103">データ移行をリクエストする方法</span><span class="sxs-lookup"><span data-stu-id="42dba-103">How to request your data move</span></span>

> [!NOTE]
> <span data-ttu-id="42dba-104">このページの情報は、geo で新しいデータセンターを開始する前に、既存の Microsoft 365 テナントを持っているお客様にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="42dba-104">The information on this page only applies to customers who had existing Microsoft 365 tenants before the new datacenters in their geo launched.</span></span> <span data-ttu-id="42dba-105">移行の適格性は、特定のワークロードプロビジョニングの日付にも依存しているため、テナントの作成日は常に重要な1つの日付になるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="42dba-105">Migration eligibility also depends on the specific workload provisioning date, so tenant creation date may not always be the single date that matters.</span></span>
  
<span data-ttu-id="42dba-106">既存の Microsoft 365 お客様は、組織の主要な顧客データ全体の移行を要求することができます。</span><span class="sxs-lookup"><span data-stu-id="42dba-106">Existing Microsoft 365 customers are eligible to request migration for their entire organization’s core customer data at rest.</span></span>  
  
## <a name="when-can-i-request-a-move"></a><span data-ttu-id="42dba-107">いつ移行をリクエストできますか?</span><span class="sxs-lookup"><span data-stu-id="42dba-107">When can I request a move?</span></span>

|<span data-ttu-id="42dba-108">**国がサインアップしているお客様**</span><span class="sxs-lookup"><span data-stu-id="42dba-108">**Customers with signup country in**</span></span>|<span data-ttu-id="42dba-109">**リクエスト期間の開始**</span><span class="sxs-lookup"><span data-stu-id="42dba-109">**Request period begins**</span></span>|<span data-ttu-id="42dba-110">**リクエストの期限**</span><span class="sxs-lookup"><span data-stu-id="42dba-110">**Request deadline**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="42dba-111">日本</span><span class="sxs-lookup"><span data-stu-id="42dba-111">Japan</span></span>  <br/> |<span data-ttu-id="42dba-112">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="42dba-112">January 1, 2020</span></span>  <br/> |<span data-ttu-id="42dba-113">2020 年 6 月 30 日</span><span class="sxs-lookup"><span data-stu-id="42dba-113">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="42dba-114">オーストラリア、ニュージーランド、フィジー</span><span class="sxs-lookup"><span data-stu-id="42dba-114">Australia, New Zealand, Fiji</span></span>  <br/> |<span data-ttu-id="42dba-115">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="42dba-115">January 1, 2020</span></span>  <br/> |<span data-ttu-id="42dba-116">2020 年 6 月 30 日</span><span class="sxs-lookup"><span data-stu-id="42dba-116">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="42dba-117">インド</span><span class="sxs-lookup"><span data-stu-id="42dba-117">India</span></span>  <br/> |<span data-ttu-id="42dba-118">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="42dba-118">January 1, 2020</span></span>  <br/> |<span data-ttu-id="42dba-119">2020 年 6 月 30 日</span><span class="sxs-lookup"><span data-stu-id="42dba-119">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="42dba-120">カナダ</span><span class="sxs-lookup"><span data-stu-id="42dba-120">Canada</span></span>  <br/> |<span data-ttu-id="42dba-121">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="42dba-121">January 1, 2020</span></span>  <br/> |<span data-ttu-id="42dba-122">2020 年 6 月 30 日</span><span class="sxs-lookup"><span data-stu-id="42dba-122">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="42dba-123">英国</span><span class="sxs-lookup"><span data-stu-id="42dba-123">United Kingdom</span></span>  <br/> |<span data-ttu-id="42dba-124">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="42dba-124">January 1, 2020</span></span>  <br/> |<span data-ttu-id="42dba-125">2020 年 6 月 30 日</span><span class="sxs-lookup"><span data-stu-id="42dba-125">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="42dba-126">韓国</span><span class="sxs-lookup"><span data-stu-id="42dba-126">South Korea</span></span>  <br/> |<span data-ttu-id="42dba-127">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="42dba-127">January 1, 2020</span></span>  <br/> |<span data-ttu-id="42dba-128">2020 年 6 月 30 日</span><span class="sxs-lookup"><span data-stu-id="42dba-128">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="42dba-129">フランス</span><span class="sxs-lookup"><span data-stu-id="42dba-129">France</span></span>  <br/> |<span data-ttu-id="42dba-130">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="42dba-130">January 1, 2020</span></span>  <br/> |<span data-ttu-id="42dba-131">2020 年 6 月 30 日</span><span class="sxs-lookup"><span data-stu-id="42dba-131">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="42dba-132">アラブ首長国連邦</span><span class="sxs-lookup"><span data-stu-id="42dba-132">United Arab Emirates</span></span>  <br/> |<span data-ttu-id="42dba-133">2019 年 7 月 15 日</span><span class="sxs-lookup"><span data-stu-id="42dba-133">July 15, 2019</span></span>  <br/> |<span data-ttu-id="42dba-134">2020 年 6 月 30 日</span><span class="sxs-lookup"><span data-stu-id="42dba-134">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="42dba-135">南アフリカ</span><span class="sxs-lookup"><span data-stu-id="42dba-135">South Africa</span></span>  <br/> |<span data-ttu-id="42dba-136">2019 年 7 月 25 日</span><span class="sxs-lookup"><span data-stu-id="42dba-136">July 25, 2019</span></span>  <br/> |<span data-ttu-id="42dba-137">2020 年 6 月 30 日</span><span class="sxs-lookup"><span data-stu-id="42dba-137">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="42dba-138">スイス、リヒテンシュタイン</span><span class="sxs-lookup"><span data-stu-id="42dba-138">Switzerland, Liechtenstein</span></span>  <br/> |<span data-ttu-id="42dba-139">2019 年 12 月 10 日</span><span class="sxs-lookup"><span data-stu-id="42dba-139">December 10, 2019</span></span>  <br/> |<span data-ttu-id="42dba-140">2020 年 6 月 30 日</span><span class="sxs-lookup"><span data-stu-id="42dba-140">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="42dba-141">ドイツ</span><span class="sxs-lookup"><span data-stu-id="42dba-141">Germany</span></span>  <br/> |<span data-ttu-id="42dba-142">計画</span><span class="sxs-lookup"><span data-stu-id="42dba-142">Planned</span></span>  <br/> |<span data-ttu-id="42dba-143">計画</span><span class="sxs-lookup"><span data-stu-id="42dba-143">Planned</span></span>  <br/> |
|<span data-ttu-id="42dba-144">ノルウェー</span><span class="sxs-lookup"><span data-stu-id="42dba-144">Norway</span></span>  <br/> |<span data-ttu-id="42dba-145">2020 年 4 月 15 日</span><span class="sxs-lookup"><span data-stu-id="42dba-145">April 15, 2020</span></span>  <br/> |<span data-ttu-id="42dba-146">2020年10月31日</span><span class="sxs-lookup"><span data-stu-id="42dba-146">October 31, 2020</span></span>  <br/> |
   
## <a name="how-to-request-a-move"></a><span data-ttu-id="42dba-147">移行をリクエストする方法</span><span class="sxs-lookup"><span data-stu-id="42dba-147">How to request a move</span></span>

<span data-ttu-id="42dba-148">対象となるお客様には、 [Microsoft 365 管理センター](https://aka.ms/365admin)にページが表示されます。これにより、お客様は自社のコア顧客データを新しいデータセンターリージョンに移動するよう要求できます。</span><span class="sxs-lookup"><span data-stu-id="42dba-148">Eligible customers will see a page in the [Microsoft 365 admin center](https://aka.ms/365admin), which will allow them to request to have their core customer data moved to their new datacenter region.</span></span>  
  
<span data-ttu-id="42dba-149">Microsoft 365 管理センターのページにアクセスするには、左側のナビゲーションウィンドウで [**設定**] を展開し、[**組織の設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="42dba-149">To access the page in the Microsoft 365 admin center, in the navigation pane on the left, expand **Settings**, and then click **Org Settings**.</span></span>
<span data-ttu-id="42dba-150">Tab**組織プロファイル**を選択して、[ **Data レジデンシー**] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="42dba-150">Select the tab **Organization profile**, then select the option **Data residency**.</span></span>
  
<span data-ttu-id="42dba-151">**次のいずれかに該当する場合は、このセクションは表示されません**。</span><span class="sxs-lookup"><span data-stu-id="42dba-151">**You may not see this section if one of the following apply**:</span></span>
- <span data-ttu-id="42dba-152">テナントは Office 365 Move プログラムの対象外です。</span><span class="sxs-lookup"><span data-stu-id="42dba-152">Your tenant is not eligible for the Office 365 Move Program.</span></span>  <span data-ttu-id="42dba-153">資格は、テナントのサインアップ国によって決まります。</span><span class="sxs-lookup"><span data-stu-id="42dba-153">Eligibility is determined by tenant signup country.</span></span>
- <span data-ttu-id="42dba-154">Rest における主要な顧客データはすべて、既に新しい geo に配置されています (ページの [データの場所] セクションを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="42dba-154">All of your core customer data at rest is already located in the new geo (see Data Location section of the page).</span></span> 
  
<span data-ttu-id="42dba-155">データ常駐の要件があり、移行を要求する必要がある組織の場合は、チェックボックスをオンにして、**保存**します。</span><span class="sxs-lookup"><span data-stu-id="42dba-155">If your organization has data residency requirements and you need to request migration, mark the checkbox and then **Save**.</span></span>
  
![データセンターのオプトイン操作画面](media/dataresidencyflyoutae.jpg)
  
<span data-ttu-id="42dba-157">「 **Data レジデンシー** 」セクションのテキストが、組織が適切な国および日付に**データを移動するように要求**したことを示すように変化することを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42dba-157">You should see the text on the **Data residency** section change to indicate **Your organization has requested to move its data** to the appropriate country and date.</span></span> <span data-ttu-id="42dba-158">メッセージ センターにも確認メッセージが届きます。</span><span class="sxs-lookup"><span data-stu-id="42dba-158">You'll also have a confirmation message in your message center.</span></span> <span data-ttu-id="42dba-159">これにより、移行が正常にリクエストされたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="42dba-159">This confirms that you have successfully requested a move.</span></span> 


  
## <a name="what-happens-after-requesting-a-move"></a><span data-ttu-id="42dba-160">移行をリクエストした後はどうなりますか?</span><span class="sxs-lookup"><span data-stu-id="42dba-160">What happens after requesting a move?</span></span>

<span data-ttu-id="42dba-161">移行をリクエストした後、運用上の制約が許容されるように、をすばやく移行することを計画します。</span><span class="sxs-lookup"><span data-stu-id="42dba-161">After requesting a move, we will plan to move you as quickly as our operational constraints allow.</span></span> <span data-ttu-id="42dba-162">予測不可能な性質の制約が数多くあるため、移行が実施される特定の日付や時間帯を共有することはできません。</span><span class="sxs-lookup"><span data-stu-id="42dba-162">Due to the unpredictable nature of many of the constraints, we cannot share a specific date or timeframe for the moves.</span></span> <span data-ttu-id="42dba-163">移行が完了した後、お客様に通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="42dba-163">You will see a notification after the move has completed.</span></span>
  
<span data-ttu-id="42dba-164">移行を完了するには、お住まいの国のリクエストの期限から最大 24 か月かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="42dba-164">Moves may take up to 24 months from the request deadline for your country to complete.</span></span>
  
## <a name="microsoft-teams"></a><span data-ttu-id="42dba-165">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="42dba-165">Microsoft Teams</span></span>

<span data-ttu-id="42dba-166">2020年1月の間、対象となる Office 365 諸国のお客様は、Microsoft Teams chat service データの移行をオプトインできます。</span><span class="sxs-lookup"><span data-stu-id="42dba-166">As of January 2020, customers in eligible Office 365 countries can opt-in for migration of Microsoft Teams chat service data.</span></span>  <span data-ttu-id="42dba-167">オプトインタイムラインは、対象となるすべての国に対して再オープンまたは拡張されています。これにより、お客様は、範囲内の Microsoft Teams で移行プログラムを検討する機会を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="42dba-167">Opt-in timelines have been reopened or extended for all eligible countries to give customers an opportunity to consider the migration program with Microsoft Teams in scope.</span></span> <span data-ttu-id="42dba-168">以前にデータ常駐移行をオプトインしていたお客様も、Teams をローカルデータセンター geo に移行することになります。</span><span class="sxs-lookup"><span data-stu-id="42dba-168">Customers that previously opted-in for a Data Residency move will also have Teams move to their local datacenter geo.</span></span>

## <a name="related-topics"></a><span data-ttu-id="42dba-169">関連トピック</span><span class="sxs-lookup"><span data-stu-id="42dba-169">Related topics</span></span>

[<span data-ttu-id="42dba-170">コア データを新しい Office 365 データ センター geo に移行する</span><span class="sxs-lookup"><span data-stu-id="42dba-170">Moving core data to new Office 365 datacenter geos</span></span>](moving-data-to-new-datacenter-geos.md)

[<span data-ttu-id="42dba-171">データ移行についての一般的な FAQ</span><span class="sxs-lookup"><span data-stu-id="42dba-171">Data move general FAQ</span></span>](data-move-faq.md)

[<span data-ttu-id="42dba-172">Microsoft Dynamics CRM Online の新しいデータ センター geo</span><span class="sxs-lookup"><span data-stu-id="42dba-172">New datacenter geos for Microsoft Dynamics CRM Online</span></span>](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[<span data-ttu-id="42dba-173">Azure のリージョン</span><span class="sxs-lookup"><span data-stu-id="42dba-173">Azure services by region</span></span>](https://azure.microsoft.com/regions/)
  

