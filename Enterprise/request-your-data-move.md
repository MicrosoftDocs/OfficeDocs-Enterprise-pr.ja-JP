---
title: データ移行をリクエストする方法
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 07/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5bb64310-36fc-473d-b791-a0176f21707f
description: 既存の Office 365 のお客様は、Office 365 サービスに参加しているお客様のデータを新しい geo へ移行するために、お住まいの国の期限より前にリクエストを送信する必要があります。
ms.openlocfilehash: 4df9c3481782f6d3f0b8431bd91677fb1262812c
ms.sourcegitcommit: 842ac51577317dfc8d2adc46d09b4d735f29bc4f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "35907650"
---
# <a name="how-to-request-your-data-move"></a><span data-ttu-id="7a30b-103">データ移行をリクエストする方法</span><span class="sxs-lookup"><span data-stu-id="7a30b-103">How to request your data move</span></span>

> [!NOTE]
> <span data-ttu-id="7a30b-104">このページの情報は、geo で新しいデータセンターが開設される前に、既存の Office 365 テナントを使用していたお客様にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="7a30b-104">The information on this page only applies to customers who had existing Office 365 tenants before the new datacenters in their geo launched.</span></span> 
  
<span data-ttu-id="7a30b-105">既存の Office 365 のお客様は、組織の主要な顧客データ全体の移行を事前に要請することができます。</span><span class="sxs-lookup"><span data-stu-id="7a30b-105">Existing Office 365 customers are eligible to request early migration for their entire organization’s core customer data at rest.</span></span>  
  
## <a name="when-can-i-request-a-move"></a><span data-ttu-id="7a30b-106">いつ移行をリクエストできますか?</span><span class="sxs-lookup"><span data-stu-id="7a30b-106">When can I request a move?</span></span>

|<span data-ttu-id="7a30b-107">**請求先住所のお客様**</span><span class="sxs-lookup"><span data-stu-id="7a30b-107">**Customers with billing address in**</span></span>|<span data-ttu-id="7a30b-108">**リクエスト期間の開始**</span><span class="sxs-lookup"><span data-stu-id="7a30b-108">**Request period begins**</span></span>|<span data-ttu-id="7a30b-109">**リクエストの期限**</span><span class="sxs-lookup"><span data-stu-id="7a30b-109">**Request deadline**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="7a30b-110">日本</span><span class="sxs-lookup"><span data-stu-id="7a30b-110">Japan</span></span>  <br/> |<span data-ttu-id="7a30b-111">2016 年 8 月 1 日</span><span class="sxs-lookup"><span data-stu-id="7a30b-111">August 1, 2016</span></span>  <br/> |<span data-ttu-id="7a30b-112">2016 年 10 月 31 日</span><span class="sxs-lookup"><span data-stu-id="7a30b-112">October 31, 2016</span></span>  <br/> |
|<span data-ttu-id="7a30b-113">オーストラリア、ニュージーランド、フィジー</span><span class="sxs-lookup"><span data-stu-id="7a30b-113">Australia, New Zealand, Fiji</span></span>  <br/> |<span data-ttu-id="7a30b-114">2016 年 8 月 1 日</span><span class="sxs-lookup"><span data-stu-id="7a30b-114">August 1, 2016</span></span>  <br/> |<span data-ttu-id="7a30b-115">2016 年 10 月 31 日</span><span class="sxs-lookup"><span data-stu-id="7a30b-115">October 31, 2016</span></span>  <br/> |
|<span data-ttu-id="7a30b-116">インド</span><span class="sxs-lookup"><span data-stu-id="7a30b-116">India</span></span>  <br/> |<span data-ttu-id="7a30b-117">2016 年 8 月 1 日</span><span class="sxs-lookup"><span data-stu-id="7a30b-117">August 1, 2016</span></span>  <br/> |<span data-ttu-id="7a30b-118">2016 年 10 月 31 日</span><span class="sxs-lookup"><span data-stu-id="7a30b-118">October 31, 2016</span></span>  <br/> |
|<span data-ttu-id="7a30b-119">カナダ</span><span class="sxs-lookup"><span data-stu-id="7a30b-119">Canada</span></span>  <br/> |<span data-ttu-id="7a30b-120">2016 年 8 月 1 日</span><span class="sxs-lookup"><span data-stu-id="7a30b-120">August 1, 2016</span></span>  <br/> |<span data-ttu-id="7a30b-121">2016 年 10 月 31 日</span><span class="sxs-lookup"><span data-stu-id="7a30b-121">October 31, 2016</span></span>  <br/> |
|<span data-ttu-id="7a30b-122">英国</span><span class="sxs-lookup"><span data-stu-id="7a30b-122">United Kingdom</span></span>  <br/> |<span data-ttu-id="7a30b-123">2017 年 3 月 15 日</span><span class="sxs-lookup"><span data-stu-id="7a30b-123">March 15, 2017</span></span>  <br/> |<span data-ttu-id="7a30b-124">2017 年 9 月 15 日</span><span class="sxs-lookup"><span data-stu-id="7a30b-124">September 15, 2017</span></span>  <br/> |
|<span data-ttu-id="7a30b-125">韓国</span><span class="sxs-lookup"><span data-stu-id="7a30b-125">South Korea</span></span>  <br/> |<span data-ttu-id="7a30b-126">2017 年 5 月 1 日</span><span class="sxs-lookup"><span data-stu-id="7a30b-126">May 1, 2017</span></span>  <br/> |<span data-ttu-id="7a30b-127">2017 年 10 月 31 日</span><span class="sxs-lookup"><span data-stu-id="7a30b-127">October 31, 2017</span></span>  <br/> |
|<span data-ttu-id="7a30b-128">フランス</span><span class="sxs-lookup"><span data-stu-id="7a30b-128">France</span></span>  <br/> |<span data-ttu-id="7a30b-129">2018 年 3 月 14 日</span><span class="sxs-lookup"><span data-stu-id="7a30b-129">March 14, 2018</span></span>  <br/> |<span data-ttu-id="7a30b-130">2018 年 9 月 15 日</span><span class="sxs-lookup"><span data-stu-id="7a30b-130">September 15, 2018</span></span>  <br/> |
|<span data-ttu-id="7a30b-131">アラブ首長国連邦</span><span class="sxs-lookup"><span data-stu-id="7a30b-131">United Arab Emirates</span></span>  <br/> |<span data-ttu-id="7a30b-132">2019年7月15日</span><span class="sxs-lookup"><span data-stu-id="7a30b-132">July 15, 2019</span></span>  <br/> |<span data-ttu-id="7a30b-133">2020年1月31日</span><span class="sxs-lookup"><span data-stu-id="7a30b-133">January 31, 2020</span></span>  <br/> |
|<span data-ttu-id="7a30b-134">南アフリカ</span><span class="sxs-lookup"><span data-stu-id="7a30b-134">South Africa</span></span>  <br/> |<span data-ttu-id="7a30b-135">2019年7月25日</span><span class="sxs-lookup"><span data-stu-id="7a30b-135">July 25, 2019</span></span>  <br/> |<span data-ttu-id="7a30b-136">2020年1月31日</span><span class="sxs-lookup"><span data-stu-id="7a30b-136">January 31, 2020</span></span>  <br/> |
   
## <a name="how-to-request-a-move"></a><span data-ttu-id="7a30b-137">移行をリクエストする方法</span><span class="sxs-lookup"><span data-stu-id="7a30b-137">How to request a move</span></span>

<span data-ttu-id="7a30b-138">対象となるお客様には、[管理センター](https://aka.ms/365admin)にページが表示されます。これにより、自社のコア顧客データを新しいデータセンターリージョンに移行することを要求することができます。</span><span class="sxs-lookup"><span data-stu-id="7a30b-138">Eligible customers will see a page in their [admin center](https://aka.ms/365admin), which will allow them to request to have their core customer data moved to their new datacenter region.</span></span>  
  
<span data-ttu-id="7a30b-139">Microsoft 365 管理センターのページにアクセスするには、左側のナビゲーションウィンドウで [**設定**] を展開し、[**組織プロファイル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a30b-139">To access the page in the Microsoft 365 admin center, in the navigation pane on the left, expand **Settings**, and then click **Organization Profile**.</span></span>
  
![組織プロファイルが強調表示されている [設定] メニュー](media/22799fac-32b4-4f79-ae60-3f6ffb7cfbd7.png)
  
<span data-ttu-id="7a30b-141">**[Organization Profile]** ページで **[データ所在地のオプション]** セクションまで下方向にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="7a30b-141">On the **Organization Profile** page, scroll down to the **Data Residency Option** section.</span></span> 
  
![データ常駐のカード](media/dataresidencyae.jpg)
  
<span data-ttu-id="7a30b-143">**次のいずれかに該当する場合は、このセクションは表示されません**。</span><span class="sxs-lookup"><span data-stu-id="7a30b-143">**You may not see this section if one of the following apply**:</span></span>
- <span data-ttu-id="7a30b-144">テナントは Office 365 Move プログラムの対象外です。</span><span class="sxs-lookup"><span data-stu-id="7a30b-144">Your tenant is not eligible for the Office 365 Move Program.</span></span>  <span data-ttu-id="7a30b-145">資格は、テナントのサインアップ国によって決まります。</span><span class="sxs-lookup"><span data-stu-id="7a30b-145">Eligibility is determined by tenant signup country.</span></span>
- <span data-ttu-id="7a30b-146">Rest における主要な顧客データはすべて、既に新しい geo に配置されています (ページの [データの場所] セクションを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="7a30b-146">All of your core customer data at rest is already located in the new geo (see Data Location section of the page).</span></span> 
  
<span data-ttu-id="7a30b-147">データ常駐の要件があり、事前に移行を依頼する必要がある組織の場合は、セクションの右上にある [**オプトイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a30b-147">If your organization has data residency requirements and you need to request early migration, click **Opt-in** on the top right of the section.</span></span> <span data-ttu-id="7a30b-148">画面の右側に、Office 365 Move プログラムの詳細を説明する新しいセクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a30b-148">A new section will appear on the right side of your screen explaining the details of the Office 365 Move Program.</span></span> <span data-ttu-id="7a30b-149">テキストの横にあるトグルボタンを選択して、[**組織のコア顧客データを**保存する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7a30b-149">Select the toggle button next to the text that says **I want my organization's core customer data at rest to migrate**.</span></span> <span data-ttu-id="7a30b-150">次に、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a30b-150">Then, click **Save**.</span></span>
  
![データセンターのオプトイン操作画面](media/dataresidencyflyoutae.jpg)
  
<span data-ttu-id="7a30b-152">「 **Data レジデンシー** 」セクションのテキストが、**組織がコア顧客データの移行を要求**したことを示すように変更されます。</span><span class="sxs-lookup"><span data-stu-id="7a30b-152">You should see the text on the **Data Residency** section change to indicate **Your organization has requested to move its core customer data.**</span></span> <span data-ttu-id="7a30b-153">メッセージ センターにも確認メッセージが届きます。</span><span class="sxs-lookup"><span data-stu-id="7a30b-153">You'll also have a confirmation message in your message center.</span></span> <span data-ttu-id="7a30b-154">これにより、移行が正常にリクエストされたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7a30b-154">This confirms that you have successfully requested a move.</span></span> 


  
## <a name="what-happens-after-requesting-a-move"></a><span data-ttu-id="7a30b-155">移行をリクエストした後はどうなりますか?</span><span class="sxs-lookup"><span data-stu-id="7a30b-155">What happens after requesting a move?</span></span>

<span data-ttu-id="7a30b-156">移行をリクエストした後、運用上の制約が許容されるように、をすばやく移行することを計画します。</span><span class="sxs-lookup"><span data-stu-id="7a30b-156">After requesting a move, we will plan to move you as quickly as our operational constraints allow.</span></span> <span data-ttu-id="7a30b-157">予測不可能な性質の制約が数多くあるため、移行が実施される特定の日付や時間帯を共有することはできません。</span><span class="sxs-lookup"><span data-stu-id="7a30b-157">Due to the unpredictable nature of many of the constraints, we cannot share a specific date or timeframe for the moves.</span></span> <span data-ttu-id="7a30b-158">移行が完了した後、お客様に通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a30b-158">You will see a notification after the move has completed.</span></span>
  
<span data-ttu-id="7a30b-159">移行を完了するには、お住まいの国のリクエストの期限から最大 24 か月かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7a30b-159">Moves may take up to 24 months from the request deadline for your country to complete.</span></span>
  
## <a name="microsoft-teams"></a><span data-ttu-id="7a30b-160">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7a30b-160">Microsoft Teams</span></span>

<span data-ttu-id="7a30b-161">Microsoft Teams では、Microsoft Teams のデータ常駐サービスが利用可能な国内のデータセンターへの、お客様のコンテンツのインプレース移行はまだサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7a30b-161">Microsoft Teams does not yet support migration of customer content at rest from in-region to in-country data centers where data residency for Microsoft Teams is available.</span></span>  <span data-ttu-id="7a30b-162">そのため、Microsoft Teams がデータ常駐をサポートしている新しい地域では、新しい顧客のみが国内にデータを格納することになります。</span><span class="sxs-lookup"><span data-stu-id="7a30b-162">Therefore, only new customers will have all of their data stored within country in the new regions where Microsoft Teams supports data residency.</span></span>  <span data-ttu-id="7a30b-163">Office 365 データ常駐の詳細については、「データの保存場所」を参照[してください。](https://products.office.com/where-is-your-data-located)</span><span class="sxs-lookup"><span data-stu-id="7a30b-163">Learn more about Office 365 data residency for your company location at [Where is your data located?](https://products.office.com/where-is-your-data-located)</span></span>   

## <a name="optional-actions-before-you-request-a-move"></a><span data-ttu-id="7a30b-164">移行をリクエストする前に選択可能なアクション</span><span class="sxs-lookup"><span data-stu-id="7a30b-164">Optional actions before you request a move</span></span>

<span data-ttu-id="7a30b-165">必要に応じて、以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7a30b-165">Perform the following steps as appropriate.</span></span>
  
### <a name="if-you-use-an-ip-based-firewall-add-allow-rules-for-the-new-ip-addresses"></a><span data-ttu-id="7a30b-166">IP ベースのファイアウォールを使用している場合は、新しい IP アドレスの許可ルールを追加する</span><span class="sxs-lookup"><span data-stu-id="7a30b-166">If you use an IP-based firewall, add allow rules for the new IP addresses</span></span>

<span data-ttu-id="7a30b-p106">IP アドレスではなく、DNS フィルターをファイアウォールに使用するようお勧めします。新しい DNS エントリは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="7a30b-p106">We recommend using DNS filtering for firewalls instead of IP addresses. There are no new DNS entries required.</span></span>
  
<span data-ttu-id="7a30b-p107">IP ベースのファイアウォールをインターネット接続に使用する場合には、移行先のデータセンター geo のための新しい IP アドレスの許可ルールを追加する必要があります。新しいサーバーに加え、新しいデータセンター geo の IP アドレスは、「[Office 365 の URL と IP アドレスの範囲](https://go.microsoft.com/fwlink/p/?LinkId=229631)」に継続的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="7a30b-p107">If you use an IP-based firewall for Internet connectivity, you must add allow rules for the new IP addresses for the destination datacenter geo. IP addresses for new datacenter geos in addition to new servers are continuously added to [Office 365 URLs and IP Address Ranges](https://go.microsoft.com/fwlink/p/?LinkId=229631).</span></span>
  
<span data-ttu-id="7a30b-171">許可ルール (ホワイトリストとも呼ばれる) の追加方法については、ファイアウォールのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a30b-171">Consult your firewall documentation for information about how to add allow rules (also known as whitelisting.)</span></span>
  
<span data-ttu-id="7a30b-p108">IP アドレスを追加した後には、新しいデータセンター geo への接続をテストするとよいでしょう。これを実行するため、新しいデータセンター geo が利用可能になったらすぐに、[新しくなった無料の 30 日間の試用版テナント](https://go.microsoft.com/fwlink/?LinkId=522463)を作成するようお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7a30b-p108">After adding IP addresses, you may want to test connectivity to the new datacenter geo. To do this, we recommend creating a [new free 30-day trial](https://go.microsoft.com/fwlink/?LinkId=522463) tenant as soon as the new datacenter geo is available.</span></span> 
  
### <a name="test-using-a-new-tenant"></a><span data-ttu-id="7a30b-174">新しいテナントを使ってテストする</span><span class="sxs-lookup"><span data-stu-id="7a30b-174">Test using a new tenant</span></span>

<span data-ttu-id="7a30b-175">移行前に接続をテストする場合、新しいデータセンター geo が利用可能になった後に、[新しくなった無料の 30 日間の試用版テナント](https://go.microsoft.com/fwlink/?LinkId=522463)を設定し、それを使用して、新しいデータセンター geo でホストされる Office 365 を操作することができます。</span><span class="sxs-lookup"><span data-stu-id="7a30b-175">If you'd like to test connectivity prior to the move, you can set up a [new free 30-day trial tenant](https://go.microsoft.com/fwlink/?LinkId=522463) after the new datacenter geo is available, and use it to experience Office 365 hosted in the new datacenter geo.</span></span> 
  
<span data-ttu-id="7a30b-176">試用版テナントを既存のテナントと結合することはできません。</span><span class="sxs-lookup"><span data-stu-id="7a30b-176">The trial tenant can't be combined with your existing tenant:</span></span>
  
- <span data-ttu-id="7a30b-177">ユーザーはテストのために別個の試用版アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a30b-177">Users must use a separate trial account for their testing.</span></span>
    
- <span data-ttu-id="7a30b-178">テナント間でデータを移行する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="7a30b-178">There is no way to move data between tenants.</span></span>
    
### <a name="notify-users-to-update-out-of-date-exchange-settings-on-mobile-devices"></a><span data-ttu-id="7a30b-179">モバイル デバイス上の古い Exchange 設定を更新するようユーザーに通知する</span><span class="sxs-lookup"><span data-stu-id="7a30b-179">Notify users to update out-of-date Exchange settings on mobile devices</span></span>

<span data-ttu-id="7a30b-180">Exchange Server が**m.outlook.com**または**podxxxxx.outlook.com**に設定されているモバイルデバイスをユーザーが所有している場合は、 **outlook.office365.com**に切り替えることをお勧めします。「[同期するモバイルデバイスの設定」の手順に従ってください。自分のアカウントを使用](https://support.office.com/article/c9139caf-01ab-41a0-827c-3c06ee569ed3)します。</span><span class="sxs-lookup"><span data-stu-id="7a30b-180">If users have a mobile device with the Exchange Server set to **m.outlook.com** or **podxxxxx.outlook.com**, we recommend that they switch to **outlook.office365.com**, following the instructions in [Set up a mobile device to synchronize with your account](https://support.office.com/article/c9139caf-01ab-41a0-827c-3c06ee569ed3).</span></span>

## <a name="related-topics"></a><span data-ttu-id="7a30b-181">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a30b-181">Related topics</span></span>

[<span data-ttu-id="7a30b-182">コアデータを新しい Office 365 データセンター geo に移行する</span><span class="sxs-lookup"><span data-stu-id="7a30b-182">Moving core data to new Office 365 datacenter geos</span></span>](moving-data-to-new-datacenter-geos.md)

[<span data-ttu-id="7a30b-183">データ移行についての一般的な FAQ</span><span class="sxs-lookup"><span data-stu-id="7a30b-183">Data move general FAQ</span></span>](data-move-faq.md)

[<span data-ttu-id="7a30b-184">Microsoft Dynamics CRM Online の新しいデータ センター geo</span><span class="sxs-lookup"><span data-stu-id="7a30b-184">New datacenter geos for Microsoft Dynamics CRM Online</span></span>](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[<span data-ttu-id="7a30b-185">Azure のリージョン</span><span class="sxs-lookup"><span data-stu-id="7a30b-185">Azure services by region</span></span>](https://azure.microsoft.com/en-us/regions/)
  

