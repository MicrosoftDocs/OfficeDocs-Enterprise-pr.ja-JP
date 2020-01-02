---
title: データ移行をリクエストする方法
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5bb64310-36fc-473d-b791-a0176f21707f
description: 既存の Office 365 のお客様は、Office 365 サービスに参加しているお客様のデータを新しい geo へ移行するために、お住まいの国の期限より前にリクエストを送信する必要があります。
ms.openlocfilehash: 6c5b576b0d099f4a46aca63a72390d27ae39984b
ms.sourcegitcommit: 761dd21a6b7a2650ef26fd8d6b303c04fa2546f2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2020
ms.locfileid: "40923879"
---
# <a name="how-to-request-your-data-move"></a><span data-ttu-id="61f4a-103">データ移行をリクエストする方法</span><span class="sxs-lookup"><span data-stu-id="61f4a-103">How to request your data move</span></span>

> [!NOTE]
> <span data-ttu-id="61f4a-104">このページの情報は、geo で新しいデータセンターが開設される前に、既存の Office 365 テナントを使用していたお客様にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="61f4a-104">The information on this page only applies to customers who had existing Office 365 tenants before the new datacenters in their geo launched.</span></span> 
  
<span data-ttu-id="61f4a-105">既存の Office 365 のお客様は、組織の主要な顧客データ全体の移行を事前に要請することができます。</span><span class="sxs-lookup"><span data-stu-id="61f4a-105">Existing Office 365 customers are eligible to request early migration for their entire organization’s core customer data at rest.</span></span>  
  
## <a name="when-can-i-request-a-move"></a><span data-ttu-id="61f4a-106">いつ移行をリクエストできますか?</span><span class="sxs-lookup"><span data-stu-id="61f4a-106">When can I request a move?</span></span>

|<span data-ttu-id="61f4a-107">**国がサインアップしているお客様**</span><span class="sxs-lookup"><span data-stu-id="61f4a-107">**Customers with signup country in**</span></span>|<span data-ttu-id="61f4a-108">**リクエスト期間の開始**</span><span class="sxs-lookup"><span data-stu-id="61f4a-108">**Request period begins**</span></span>|<span data-ttu-id="61f4a-109">**リクエストの期限**</span><span class="sxs-lookup"><span data-stu-id="61f4a-109">**Request deadline**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="61f4a-110">日本</span><span class="sxs-lookup"><span data-stu-id="61f4a-110">Japan</span></span>  <br/> |<span data-ttu-id="61f4a-111">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="61f4a-111">January 1, 2020</span></span>  <br/> |<span data-ttu-id="61f4a-112">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="61f4a-112">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="61f4a-113">オーストラリア、ニュージーランド、フィジー</span><span class="sxs-lookup"><span data-stu-id="61f4a-113">Australia, New Zealand, Fiji</span></span>  <br/> |<span data-ttu-id="61f4a-114">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="61f4a-114">January 1, 2020</span></span>  <br/> |<span data-ttu-id="61f4a-115">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="61f4a-115">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="61f4a-116">インド</span><span class="sxs-lookup"><span data-stu-id="61f4a-116">India</span></span>  <br/> |<span data-ttu-id="61f4a-117">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="61f4a-117">January 1, 2020</span></span>  <br/> |<span data-ttu-id="61f4a-118">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="61f4a-118">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="61f4a-119">カナダ</span><span class="sxs-lookup"><span data-stu-id="61f4a-119">Canada</span></span>  <br/> |<span data-ttu-id="61f4a-120">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="61f4a-120">January 1, 2020</span></span>  <br/> |<span data-ttu-id="61f4a-121">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="61f4a-121">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="61f4a-122">英国</span><span class="sxs-lookup"><span data-stu-id="61f4a-122">United Kingdom</span></span>  <br/> |<span data-ttu-id="61f4a-123">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="61f4a-123">January 1, 2020</span></span>  <br/> |<span data-ttu-id="61f4a-124">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="61f4a-124">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="61f4a-125">韓国</span><span class="sxs-lookup"><span data-stu-id="61f4a-125">South Korea</span></span>  <br/> |<span data-ttu-id="61f4a-126">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="61f4a-126">January 1, 2020</span></span>  <br/> |<span data-ttu-id="61f4a-127">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="61f4a-127">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="61f4a-128">フランス</span><span class="sxs-lookup"><span data-stu-id="61f4a-128">France</span></span>  <br/> |<span data-ttu-id="61f4a-129">2020年1月1日</span><span class="sxs-lookup"><span data-stu-id="61f4a-129">January 1, 2020</span></span>  <br/> |<span data-ttu-id="61f4a-130">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="61f4a-130">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="61f4a-131">アラブ首長国連邦</span><span class="sxs-lookup"><span data-stu-id="61f4a-131">United Arab Emirates</span></span>  <br/> |<span data-ttu-id="61f4a-132">2019 年 7 月 15 日</span><span class="sxs-lookup"><span data-stu-id="61f4a-132">July 15, 2019</span></span>  <br/> |<span data-ttu-id="61f4a-133">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="61f4a-133">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="61f4a-134">南アフリカ</span><span class="sxs-lookup"><span data-stu-id="61f4a-134">South Africa</span></span>  <br/> |<span data-ttu-id="61f4a-135">2019 年 7 月 25 日</span><span class="sxs-lookup"><span data-stu-id="61f4a-135">July 25, 2019</span></span>  <br/> |<span data-ttu-id="61f4a-136">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="61f4a-136">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="61f4a-137">スイス、リヒテンシュタイン</span><span class="sxs-lookup"><span data-stu-id="61f4a-137">Switzerland, Liechtenstein</span></span>  <br/> |<span data-ttu-id="61f4a-138">2019 年 12 月 10 日</span><span class="sxs-lookup"><span data-stu-id="61f4a-138">December 10, 2019</span></span>  <br/> |<span data-ttu-id="61f4a-139">2020年6月30日</span><span class="sxs-lookup"><span data-stu-id="61f4a-139">June 30, 2020</span></span>  <br/> |
|<span data-ttu-id="61f4a-140">ドイツ</span><span class="sxs-lookup"><span data-stu-id="61f4a-140">Germany</span></span>  <br/> |<span data-ttu-id="61f4a-141">計画</span><span class="sxs-lookup"><span data-stu-id="61f4a-141">Planned</span></span>  <br/> |<span data-ttu-id="61f4a-142">計画</span><span class="sxs-lookup"><span data-stu-id="61f4a-142">Planned</span></span>  <br/> |
   
## <a name="how-to-request-a-move"></a><span data-ttu-id="61f4a-143">移行をリクエストする方法</span><span class="sxs-lookup"><span data-stu-id="61f4a-143">How to request a move</span></span>

<span data-ttu-id="61f4a-144">対象となるお客様には、 [Microsoft 365 管理センター](https://aka.ms/365admin)にページが表示されます。これにより、お客様は自社のコア顧客データを新しいデータセンターリージョンに移動するよう要求できます。</span><span class="sxs-lookup"><span data-stu-id="61f4a-144">Eligible customers will see a page in the [Microsoft 365 admin center](https://aka.ms/365admin), which will allow them to request to have their core customer data moved to their new datacenter region.</span></span>  
  
<span data-ttu-id="61f4a-145">Microsoft 365 管理センターのページにアクセスするには、左側のナビゲーションウィンドウで [**設定**] を展開し、[**組織プロファイル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61f4a-145">To access the page in the Microsoft 365 admin center, in the navigation pane on the left, expand **Settings**, and then click **Organization Profile**.</span></span>
  
![組織プロファイルが強調表示されている [設定] メニュー](media/22799fac-32b4-4f79-ae60-3f6ffb7cfbd7.png)
  
<span data-ttu-id="61f4a-147">**[Organization Profile]** ページで **[データ所在地のオプション]** セクションまで下方向にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="61f4a-147">On the **Organization Profile** page, scroll down to the **Data Residency Option** section.</span></span> 
  
![データ常駐のカード](media/dataresidencyae.jpg)
  
<span data-ttu-id="61f4a-149">**次のいずれかに該当する場合は、このセクションは表示されません**。</span><span class="sxs-lookup"><span data-stu-id="61f4a-149">**You may not see this section if one of the following apply**:</span></span>
- <span data-ttu-id="61f4a-150">テナントは Office 365 Move プログラムの対象外です。</span><span class="sxs-lookup"><span data-stu-id="61f4a-150">Your tenant is not eligible for the Office 365 Move Program.</span></span>  <span data-ttu-id="61f4a-151">資格は、テナントのサインアップ国によって決まります。</span><span class="sxs-lookup"><span data-stu-id="61f4a-151">Eligibility is determined by tenant signup country.</span></span>
- <span data-ttu-id="61f4a-152">Rest における主要な顧客データはすべて、既に新しい geo に配置されています (ページの [データの場所] セクションを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="61f4a-152">All of your core customer data at rest is already located in the new geo (see Data Location section of the page).</span></span> 
  
<span data-ttu-id="61f4a-153">データ常駐の要件があり、事前に移行を依頼する必要がある組織の場合は、セクションの右上にある [**オプトイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61f4a-153">If your organization has data residency requirements and you need to request early migration, click **Opt-in** on the top right of the section.</span></span> <span data-ttu-id="61f4a-154">画面の右側に、Office 365 Move プログラムの詳細を説明する新しいセクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="61f4a-154">A new section will appear on the right side of your screen explaining the details of the Office 365 Move Program.</span></span> <span data-ttu-id="61f4a-155">テキストの横にあるトグルボタンを選択して、[**組織のコア顧客データを**保存する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="61f4a-155">Select the toggle button next to the text that says **I want my organization's core customer data at rest to migrate**.</span></span> <span data-ttu-id="61f4a-156">次に、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61f4a-156">Then, click **Save**.</span></span>
  
![データセンターのオプトイン操作画面](media/dataresidencyflyoutae.jpg)
  
<span data-ttu-id="61f4a-158">「 **Data レジデンシー** 」セクションのテキストが、**組織がコア顧客データの移行を要求**したことを示すように変更されます。</span><span class="sxs-lookup"><span data-stu-id="61f4a-158">You should see the text on the **Data Residency** section change to indicate **Your organization has requested to move its core customer data.**</span></span> <span data-ttu-id="61f4a-159">メッセージ センターにも確認メッセージが届きます。</span><span class="sxs-lookup"><span data-stu-id="61f4a-159">You'll also have a confirmation message in your message center.</span></span> <span data-ttu-id="61f4a-160">これにより、移行が正常にリクエストされたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="61f4a-160">This confirms that you have successfully requested a move.</span></span> 


  
## <a name="what-happens-after-requesting-a-move"></a><span data-ttu-id="61f4a-161">移行をリクエストした後はどうなりますか?</span><span class="sxs-lookup"><span data-stu-id="61f4a-161">What happens after requesting a move?</span></span>

<span data-ttu-id="61f4a-162">移行をリクエストした後、運用上の制約が許容されるように、をすばやく移行することを計画します。</span><span class="sxs-lookup"><span data-stu-id="61f4a-162">After requesting a move, we will plan to move you as quickly as our operational constraints allow.</span></span> <span data-ttu-id="61f4a-163">予測不可能な性質の制約が数多くあるため、移行が実施される特定の日付や時間帯を共有することはできません。</span><span class="sxs-lookup"><span data-stu-id="61f4a-163">Due to the unpredictable nature of many of the constraints, we cannot share a specific date or timeframe for the moves.</span></span> <span data-ttu-id="61f4a-164">移行が完了した後、お客様に通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="61f4a-164">You will see a notification after the move has completed.</span></span>
  
<span data-ttu-id="61f4a-165">移行を完了するには、お住まいの国のリクエストの期限から最大 24 か月かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="61f4a-165">Moves may take up to 24 months from the request deadline for your country to complete.</span></span>
  
## <a name="microsoft-teams"></a><span data-ttu-id="61f4a-166">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="61f4a-166">Microsoft Teams</span></span>

<span data-ttu-id="61f4a-167">2020年1月の間、対象となる Office 365 諸国のお客様は、Microsoft Teams chat service データの移行をオプトインできます。</span><span class="sxs-lookup"><span data-stu-id="61f4a-167">As of January 2020, customers in eligible Office 365 countries can opt-in for migration of Microsoft Teams chat service data.</span></span>  <span data-ttu-id="61f4a-168">オプトインタイムラインは、対象となるすべての国に対して再オープンまたは拡張されています。これにより、お客様は、Microsoft Teams のスコープ内で初期移行プログラムを検討する機会を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="61f4a-168">Opt-in timelines have been reopened or extended for all eligible countries to give customers an opportunity to consider the early migration program with Microsoft Teams in scope.</span></span>   

## <a name="optional-actions-before-you-request-a-move"></a><span data-ttu-id="61f4a-169">移行をリクエストする前に選択可能なアクション</span><span class="sxs-lookup"><span data-stu-id="61f4a-169">Optional actions before you request a move</span></span>

<span data-ttu-id="61f4a-170">必要に応じて、以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="61f4a-170">Perform the following steps as appropriate.</span></span>
  
### <a name="if-you-use-an-ip-based-firewall-add-allow-rules-for-the-new-ip-addresses"></a><span data-ttu-id="61f4a-171">IP ベースのファイアウォールを使用している場合は、新しい IP アドレスの許可ルールを追加する</span><span class="sxs-lookup"><span data-stu-id="61f4a-171">If you use an IP-based firewall, add allow rules for the new IP addresses</span></span>

<span data-ttu-id="61f4a-p106">IP アドレスではなく、DNS フィルターをファイアウォールに使用するようお勧めします。新しい DNS エントリは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="61f4a-p106">We recommend using DNS filtering for firewalls instead of IP addresses. There are no new DNS entries required.</span></span>
  
<span data-ttu-id="61f4a-p107">IP ベースのファイアウォールをインターネット接続に使用する場合には、移行先のデータセンター geo のための新しい IP アドレスの許可ルールを追加する必要があります。新しいサーバーに加え、新しいデータセンター geo の IP アドレスは、「[Office 365 の URL と IP アドレスの範囲](https://go.microsoft.com/fwlink/p/?LinkId=229631)」に継続的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="61f4a-p107">If you use an IP-based firewall for Internet connectivity, you must add allow rules for the new IP addresses for the destination datacenter geo. IP addresses for new datacenter geos in addition to new servers are continuously added to [Office 365 URLs and IP Address Ranges](https://go.microsoft.com/fwlink/p/?LinkId=229631).</span></span>
  
<span data-ttu-id="61f4a-176">許可ルール (ホワイトリストとも呼ばれる) の追加方法については、ファイアウォールのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="61f4a-176">Consult your firewall documentation for information about how to add allow rules (also known as whitelisting.)</span></span>
  
<span data-ttu-id="61f4a-p108">IP アドレスを追加した後には、新しいデータセンター geo への接続をテストするとよいでしょう。これを実行するため、新しいデータセンター geo が利用可能になったらすぐに、[新しくなった無料の 30 日間の試用版テナント](https://go.microsoft.com/fwlink/?LinkId=522463)を作成するようお勧めします。</span><span class="sxs-lookup"><span data-stu-id="61f4a-p108">After adding IP addresses, you may want to test connectivity to the new datacenter geo. To do this, we recommend creating a [new free 30-day trial](https://go.microsoft.com/fwlink/?LinkId=522463) tenant as soon as the new datacenter geo is available.</span></span> 
  
### <a name="test-using-a-new-tenant"></a><span data-ttu-id="61f4a-179">新しいテナントを使ってテストする</span><span class="sxs-lookup"><span data-stu-id="61f4a-179">Test using a new tenant</span></span>

<span data-ttu-id="61f4a-180">移行前に接続をテストする場合、新しいデータセンター geo が利用可能になった後に、[新しくなった無料の 30 日間の試用版テナント](https://go.microsoft.com/fwlink/?LinkId=522463)を設定し、それを使用して、新しいデータセンター geo でホストされる Office 365 を操作することができます。</span><span class="sxs-lookup"><span data-stu-id="61f4a-180">If you'd like to test connectivity prior to the move, you can set up a [new free 30-day trial tenant](https://go.microsoft.com/fwlink/?LinkId=522463) after the new datacenter geo is available, and use it to experience Office 365 hosted in the new datacenter geo.</span></span> 
  
<span data-ttu-id="61f4a-181">試用版テナントを既存のテナントと結合することはできません。</span><span class="sxs-lookup"><span data-stu-id="61f4a-181">The trial tenant can't be combined with your existing tenant:</span></span>
  
- <span data-ttu-id="61f4a-182">ユーザーはテストのために別個の試用版アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61f4a-182">Users must use a separate trial account for their testing.</span></span>
    
- <span data-ttu-id="61f4a-183">テナント間でデータを移行する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="61f4a-183">There is no way to move data between tenants.</span></span>
    
### <a name="notify-users-to-update-out-of-date-exchange-settings-on-mobile-devices"></a><span data-ttu-id="61f4a-184">モバイル デバイス上の古い Exchange 設定を更新するようユーザーに通知する</span><span class="sxs-lookup"><span data-stu-id="61f4a-184">Notify users to update out-of-date Exchange settings on mobile devices</span></span>

<span data-ttu-id="61f4a-185">Exchange Server が**m.outlook.com**または**podxxxxx.outlook.com**に設定されているモバイルデバイスをユーザーが所有している場合は、「[セットアップするモバイルデバイスをアカウントと同期](https://support.office.com/article/c9139caf-01ab-41a0-827c-3c06ee569ed3)させる」の手順に従って、 **outlook.office365.com**に切り替えることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="61f4a-185">If users have a mobile device with the Exchange Server set to **m.outlook.com** or **podxxxxx.outlook.com**, we recommend that they switch to **outlook.office365.com**, following the instructions in [Set up a mobile device to synchronize with your account](https://support.office.com/article/c9139caf-01ab-41a0-827c-3c06ee569ed3).</span></span>

## <a name="related-topics"></a><span data-ttu-id="61f4a-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="61f4a-186">Related topics</span></span>

[<span data-ttu-id="61f4a-187">コアデータを新しい Office 365 データセンター geo に移行する</span><span class="sxs-lookup"><span data-stu-id="61f4a-187">Moving core data to new Office 365 datacenter geos</span></span>](moving-data-to-new-datacenter-geos.md)

[<span data-ttu-id="61f4a-188">データ移行についての一般的な FAQ</span><span class="sxs-lookup"><span data-stu-id="61f4a-188">Data move general FAQ</span></span>](data-move-faq.md)

[<span data-ttu-id="61f4a-189">Microsoft Dynamics CRM Online の新しいデータ センター geo</span><span class="sxs-lookup"><span data-stu-id="61f4a-189">New datacenter geos for Microsoft Dynamics CRM Online</span></span>](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[<span data-ttu-id="61f4a-190">Azure のリージョン</span><span class="sxs-lookup"><span data-stu-id="61f4a-190">Azure services by region</span></span>](https://azure.microsoft.com/regions/)
  

