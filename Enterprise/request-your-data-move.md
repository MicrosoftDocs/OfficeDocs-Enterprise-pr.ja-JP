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
description: 既存の Office 365 のお客様は、参加している Microsoft 365 サービスのお客様のデータを新しい geo に移動するために、お住まいの国の期日前に要求を提出する必要があります。
ms.openlocfilehash: 9c78492584f49cf263916726b2272d3b9405446e
ms.sourcegitcommit: 58aa8b2e89685490f849e0392d566b7bfb7b933e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2020
ms.locfileid: "43547745"
---
# <a name="how-to-request-your-data-move"></a><span data-ttu-id="13e43-103">データ移行をリクエストする方法</span><span class="sxs-lookup"><span data-stu-id="13e43-103">How to request your data move</span></span>

> [!NOTE]
> <span data-ttu-id="13e43-104">このページの情報は、geo で新しいデータセンターを開始する前に、既存の Microsoft 365 テナントを持っているお客様にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="13e43-104">The information on this page only applies to customers who had existing Microsoft 365 tenants before the new datacenters in their geo launched.</span></span> 
  
<span data-ttu-id="13e43-105">既存の Microsoft 365 お客様は、組織の主要な顧客データ全体の移行を要求することができます。</span><span class="sxs-lookup"><span data-stu-id="13e43-105">Existing Microsoft 365 customers are eligible to request migration for their entire organization’s core customer data at rest.</span></span>  
  
## <a name="when-can-i-request-a-move"></a><span data-ttu-id="13e43-106">いつ移行をリクエストできますか?</span><span class="sxs-lookup"><span data-stu-id="13e43-106">When can I request a move?</span></span>

|<span data-ttu-id="13e43-107">**国がサインアップしているお客様**</span><span class="sxs-lookup"><span data-stu-id="13e43-107">**Customers with signup country in**</span></span>|<span data-ttu-id="13e43-108">**リクエスト期間の開始**</span><span class="sxs-lookup"><span data-stu-id="13e43-108">**Request period begins**</span></span>|<span data-ttu-id="13e43-109">**リクエストの期限**</span><span class="sxs-lookup"><span data-stu-id="13e43-109">**Request deadline**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="13e43-110">日本</span><span class="sxs-lookup"><span data-stu-id="13e43-110">Japan</span></span>  <br/> |<span data-ttu-id="13e43-111">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="13e43-111">January 1, 2020</span></span>  <br/> |<span data-ttu-id="13e43-112">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="13e43-112">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="13e43-113">オーストラリア、ニュージーランド、フィジー</span><span class="sxs-lookup"><span data-stu-id="13e43-113">Australia, New Zealand, Fiji</span></span>  <br/> |<span data-ttu-id="13e43-114">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="13e43-114">January 1, 2020</span></span>  <br/> |<span data-ttu-id="13e43-115">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="13e43-115">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="13e43-116">インド</span><span class="sxs-lookup"><span data-stu-id="13e43-116">India</span></span>  <br/> |<span data-ttu-id="13e43-117">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="13e43-117">January 1, 2020</span></span>  <br/> |<span data-ttu-id="13e43-118">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="13e43-118">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="13e43-119">カナダ</span><span class="sxs-lookup"><span data-stu-id="13e43-119">Canada</span></span>  <br/> |<span data-ttu-id="13e43-120">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="13e43-120">January 1, 2020</span></span>  <br/> |<span data-ttu-id="13e43-121">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="13e43-121">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="13e43-122">英国</span><span class="sxs-lookup"><span data-stu-id="13e43-122">United Kingdom</span></span>  <br/> |<span data-ttu-id="13e43-123">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="13e43-123">January 1, 2020</span></span>  <br/> |<span data-ttu-id="13e43-124">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="13e43-124">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="13e43-125">韓国</span><span class="sxs-lookup"><span data-stu-id="13e43-125">South Korea</span></span>  <br/> |<span data-ttu-id="13e43-126">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="13e43-126">January 1, 2020</span></span>  <br/> |<span data-ttu-id="13e43-127">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="13e43-127">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="13e43-128">フランス</span><span class="sxs-lookup"><span data-stu-id="13e43-128">France</span></span>  <br/> |<span data-ttu-id="13e43-129">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="13e43-129">January 1, 2020</span></span>  <br/> |<span data-ttu-id="13e43-130">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="13e43-130">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="13e43-131">アラブ首長国連邦</span><span class="sxs-lookup"><span data-stu-id="13e43-131">United Arab Emirates</span></span>  <br/> |<span data-ttu-id="13e43-132">2019 年 7 月 15 日</span><span class="sxs-lookup"><span data-stu-id="13e43-132">July 15, 2019</span></span>  <br/> |<span data-ttu-id="13e43-133">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="13e43-133">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="13e43-134">南アフリカ</span><span class="sxs-lookup"><span data-stu-id="13e43-134">South Africa</span></span>  <br/> |<span data-ttu-id="13e43-135">2019 年 7 月 25 日</span><span class="sxs-lookup"><span data-stu-id="13e43-135">July 25, 2019</span></span>  <br/> |<span data-ttu-id="13e43-136">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="13e43-136">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="13e43-137">スイス、リヒテンシュタイン</span><span class="sxs-lookup"><span data-stu-id="13e43-137">Switzerland, Liechtenstein</span></span>  <br/> |<span data-ttu-id="13e43-138">2019 年 12 月 10 日</span><span class="sxs-lookup"><span data-stu-id="13e43-138">December 10, 2019</span></span>  <br/> |<span data-ttu-id="13e43-139">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="13e43-139">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="13e43-140">ドイツ</span><span class="sxs-lookup"><span data-stu-id="13e43-140">Germany</span></span>  <br/> |<span data-ttu-id="13e43-141">計画</span><span class="sxs-lookup"><span data-stu-id="13e43-141">Planned</span></span>  <br/> |<span data-ttu-id="13e43-142">計画</span><span class="sxs-lookup"><span data-stu-id="13e43-142">Planned</span></span>  <br/> |
|<span data-ttu-id="13e43-143">ノルウェー</span><span class="sxs-lookup"><span data-stu-id="13e43-143">Norway</span></span>  <br/> |<span data-ttu-id="13e43-144">2020 年 4 月 15 日</span><span class="sxs-lookup"><span data-stu-id="13e43-144">April 15, 2020</span></span>  <br/> |<span data-ttu-id="13e43-145">2020年10月31日</span><span class="sxs-lookup"><span data-stu-id="13e43-145">October 31, 2020</span></span>  <br/> |
   
## <a name="how-to-request-a-move"></a><span data-ttu-id="13e43-146">移行をリクエストする方法</span><span class="sxs-lookup"><span data-stu-id="13e43-146">How to request a move</span></span>

<span data-ttu-id="13e43-147">対象となるお客様には、 [Microsoft 365 管理センター](https://aka.ms/365admin)にページが表示されます。これにより、お客様は自社のコア顧客データを新しいデータセンターリージョンに移動するよう要求できます。</span><span class="sxs-lookup"><span data-stu-id="13e43-147">Eligible customers will see a page in the [Microsoft 365 admin center](https://aka.ms/365admin), which will allow them to request to have their core customer data moved to their new datacenter region.</span></span>  
  
<span data-ttu-id="13e43-148">Microsoft 365 管理センターのページにアクセスするには、左側のナビゲーションウィンドウで [**設定**] を展開し、[**設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13e43-148">To access the page in the Microsoft 365 admin center, in the navigation pane on the left, expand **Settings**, and then click **Settings**.</span></span>
<span data-ttu-id="13e43-149">[] タブ [**組織] プロファイル**を選択し、[ **Data レジデンシー**] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="13e43-149">Select the tab **Organisation profile**, then select the option **Data residency**.</span></span>
  
<span data-ttu-id="13e43-150">**次のいずれかに該当する場合は、このセクションは表示されません**。</span><span class="sxs-lookup"><span data-stu-id="13e43-150">**You may not see this section if one of the following apply**:</span></span>
- <span data-ttu-id="13e43-151">テナントは Office 365 Move プログラムの対象外です。</span><span class="sxs-lookup"><span data-stu-id="13e43-151">Your tenant is not eligible for the Office 365 Move Program.</span></span>  <span data-ttu-id="13e43-152">資格は、テナントのサインアップ国によって決まります。</span><span class="sxs-lookup"><span data-stu-id="13e43-152">Eligibility is determined by tenant signup country.</span></span>
- <span data-ttu-id="13e43-153">Rest における主要な顧客データはすべて、既に新しい geo に配置されています (ページの [データの場所] セクションを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="13e43-153">All of your core customer data at rest is already located in the new geo (see Data Location section of the page).</span></span> 
  
<span data-ttu-id="13e43-154">データ常駐の要件があり、移行を要求する必要がある組織の場合は、セクションの右上にある [**オプトイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13e43-154">If your organization has data residency requirements and you need to request migration, click **Opt-in** on the top right of the section.</span></span> <span data-ttu-id="13e43-155">画面の右側に、Microsoft 365 Move プログラムの詳細を説明する新しいセクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13e43-155">A new section will appear on the right side of your screen explaining the details of the Microsoft 365 Move Program.</span></span> <span data-ttu-id="13e43-156">テキストの横にあるトグルボタンを選択して、[**組織のコア顧客データを**保存する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="13e43-156">Select the toggle button next to the text that says **I want my organization's core customer data at rest to migrate**.</span></span> <span data-ttu-id="13e43-157">次に、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13e43-157">Then, click **Save**.</span></span>
  
![データセンターのオプトイン操作画面](media/dataresidencyflyoutae.jpg)
  
<span data-ttu-id="13e43-159">「 **Data レジデンシー** 」セクションのテキストが、**組織がコア顧客データの移行を要求**したことを示すように変更されます。</span><span class="sxs-lookup"><span data-stu-id="13e43-159">You should see the text on the **Data Residency** section change to indicate **Your organization has requested to move its core customer data.**</span></span> <span data-ttu-id="13e43-160">メッセージ センターにも確認メッセージが届きます。</span><span class="sxs-lookup"><span data-stu-id="13e43-160">You'll also have a confirmation message in your message center.</span></span> <span data-ttu-id="13e43-161">これにより、移行が正常にリクエストされたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="13e43-161">This confirms that you have successfully requested a move.</span></span> 


  
## <a name="what-happens-after-requesting-a-move"></a><span data-ttu-id="13e43-162">移行をリクエストした後はどうなりますか?</span><span class="sxs-lookup"><span data-stu-id="13e43-162">What happens after requesting a move?</span></span>

<span data-ttu-id="13e43-163">移行をリクエストした後、運用上の制約が許容されるように、をすばやく移行することを計画します。</span><span class="sxs-lookup"><span data-stu-id="13e43-163">After requesting a move, we will plan to move you as quickly as our operational constraints allow.</span></span> <span data-ttu-id="13e43-164">予測不可能な性質の制約が数多くあるため、移行が実施される特定の日付や時間帯を共有することはできません。</span><span class="sxs-lookup"><span data-stu-id="13e43-164">Due to the unpredictable nature of many of the constraints, we cannot share a specific date or timeframe for the moves.</span></span> <span data-ttu-id="13e43-165">移行が完了した後、お客様に通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="13e43-165">You will see a notification after the move has completed.</span></span>
  
<span data-ttu-id="13e43-166">移行を完了するには、お住まいの国のリクエストの期限から最大 24 か月かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="13e43-166">Moves may take up to 24 months from the request deadline for your country to complete.</span></span>
  
## <a name="microsoft-teams"></a><span data-ttu-id="13e43-167">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="13e43-167">Microsoft Teams</span></span>

<span data-ttu-id="13e43-168">2020年1月の間、対象となる Office 365 諸国のお客様は、Microsoft Teams chat service データの移行をオプトインできます。</span><span class="sxs-lookup"><span data-stu-id="13e43-168">As of January 2020, customers in eligible Office 365 countries can opt-in for migration of Microsoft Teams chat service data.</span></span>  <span data-ttu-id="13e43-169">オプトインタイムラインは、対象となるすべての国に対して再オープンまたは拡張されています。これにより、お客様は、範囲内の Microsoft Teams で移行プログラムを検討する機会を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="13e43-169">Opt-in timelines have been reopened or extended for all eligible countries to give customers an opportunity to consider the migration program with Microsoft Teams in scope.</span></span> <span data-ttu-id="13e43-170">以前にデータ常駐移行をオプトインしていたお客様も、Teams をローカルデータセンター geo に移行することになります。</span><span class="sxs-lookup"><span data-stu-id="13e43-170">Customers that previously opted-in for a Data Residency move will also have Teams move to their local datacenter geo.</span></span>

## <a name="related-topics"></a><span data-ttu-id="13e43-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="13e43-171">Related topics</span></span>

[<span data-ttu-id="13e43-172">コア データを新しい Office 365 データ センター geo に移行する</span><span class="sxs-lookup"><span data-stu-id="13e43-172">Moving core data to new Office 365 datacenter geos</span></span>](moving-data-to-new-datacenter-geos.md)

[<span data-ttu-id="13e43-173">データ移行についての一般的な FAQ</span><span class="sxs-lookup"><span data-stu-id="13e43-173">Data move general FAQ</span></span>](data-move-faq.md)

[<span data-ttu-id="13e43-174">Microsoft Dynamics CRM Online の新しいデータ センター geo</span><span class="sxs-lookup"><span data-stu-id="13e43-174">New datacenter geos for Microsoft Dynamics CRM Online</span></span>](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[<span data-ttu-id="13e43-175">Azure のリージョン</span><span class="sxs-lookup"><span data-stu-id="13e43-175">Azure services by region</span></span>](https://azure.microsoft.com/regions/)
  

