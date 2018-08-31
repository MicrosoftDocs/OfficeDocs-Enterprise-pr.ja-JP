---
title: Office Online Server および Office Web Apps Server の GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: オンプレミスの Exchange Server で GDPR の要件に対応する方法について説明します。
ms.openlocfilehash: 1d77abc759bb5c7b4a5a8dfef80d5bd6bac38311
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915612"
---
# <a name="gdpr-for-office-web-apps-server-and-office-online-server"></a><span data-ttu-id="7b7ee-103">Office Web Apps Server および Office Online Server の GDPR</span><span class="sxs-lookup"><span data-stu-id="7b7ee-103">GDPR for Office Web Apps Server and Office Online Server</span></span>

<span data-ttu-id="7b7ee-p101">Office Online Server および Office Web Apps Server のテレメトリ データは、ULS ログの形で保存されます。[ULS Viewer](https://www.microsoft.com/en-us/download/details.aspx?id=44020) を使用することにより、オンプレミス テナントから ULS のログを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7b7ee-p101">Office Online Server and Office Web Apps Server telemetry data is stored in the form of ULS logs. You can use [ULS Viewer](https://www.microsoft.com/en-us/download/details.aspx?id=44020) to view ULS logs from your on-premises tenant.</span></span>

<span data-ttu-id="7b7ee-p102">ログの各行には、それぞれ 1 つの CorrelationID が含まれています。関連するログ行は同じ CorrelationID を共有します。各 CorrelationID は単一の SessionID に結び付いており、1 つの SessionID は複数の CorrelationID に関連付けられている場合があります。各 SessionID を単一の UserID に関連付けることが可能ですが、いくつかのセッションは匿名のことがあり、その場合は関連する UserID がありません。そのため、特定のユーザーに関連付けられているのがどのデータかを判別するため、単一 UserID をそのユーザーに関連する SessionID に、それらの SessionID を対応する CorrelationID に、そしてそれらの CorrelationID をその関連付けのすべてのログにマッピングすることが可能です。さまざまな ID の間の関係については、次の図を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b7ee-p102">Every log line contains a CorrelationID. Related log lines share the same CorrelationID. Each CorrelationID is tied to a single SessionID, and one SessionID may be related to many CorrelationIDs. Each SessionID may be related to a single UserID, although some sessions can be anonymous and therefore not have an associated UserID. In order to determine what data is associated with a particular user, it is therefore possible to map from a single UserID to the SessionIDs associated with that user, from those SessionIDs to the associated CorrelationIDs, and from those CorrelationIDs to all the logs in those correlations. See the below diagram for the relationship between the different IDs.</span></span>

![](media/gdpr-for-office-online-server-image1.jpg)

## <a name="gathering-logs"></a><span data-ttu-id="7b7ee-112">ログの収集</span><span class="sxs-lookup"><span data-stu-id="7b7ee-112">Gathering Logs</span></span>

<span data-ttu-id="7b7ee-p103">たとえば、UserID 1 に関連するすべてのログを収集するための最初のステップは、UserID 1 に関連するすべてのセッション (つまり SessionID 1 と SessionID 2) を収集することです。次のステップは、SessionID 1 に関連するすべての関連付け (CorrelationID 1、2、および 3)、および SessionID 2 に関連するすべての関連付け (CorrelationID 4) を収集することです。最後に、リスト内の関連付けのそれぞれに関連するすべてのログを収集します。</span><span class="sxs-lookup"><span data-stu-id="7b7ee-p103">In order to gather all logs associated with UserID 1, for example, the first step would be to gather all sessions associated with UserID 1 (i.e. SessionID 1 and SessionID2). The next step would be to gather all correlations associated with SessionID 1 (i.e. CorrelationIDs 1, 2, and 3) and with SessionID 2 (i.e. CorrelationID 4). Finally, gather all logs associated with each of the correlations in the list.</span></span>

1.  <span data-ttu-id="7b7ee-116">UlsViewer の起動</span><span class="sxs-lookup"><span data-stu-id="7b7ee-116">Launch UlsViewer</span></span>

2.  <span data-ttu-id="7b7ee-117">対象となる期間に対応する uls ログを開きます。ULS ログは、%PROGRAMDATA%\\Microsoft\\OfficeWebApps\\Data\\Logs\\ULS の中に保存されています。</span><span class="sxs-lookup"><span data-stu-id="7b7ee-117">Open up the uls log corresponding to the intended timeframe; ULS logs are stored in %PROGRAMDATA%\\Microsoft\\OfficeWebApps\\Data\\Logs\\ULS</span></span>

3.  <span data-ttu-id="7b7ee-118">フィルターの編集 | 変更</span><span class="sxs-lookup"><span data-stu-id="7b7ee-118">Edit | Modify Filter</span></span>

4.  <span data-ttu-id="7b7ee-119">次のフィルターを適用します。</span><span class="sxs-lookup"><span data-stu-id="7b7ee-119">Apply a filter that is:</span></span>

    -   <span data-ttu-id="7b7ee-120">EventID が apr3y に等しい、または</span><span class="sxs-lookup"><span data-stu-id="7b7ee-120">EventID equals apr3y Or</span></span>

    -   <span data-ttu-id="7b7ee-121">EventID が bp2d6 に等しい</span><span class="sxs-lookup"><span data-stu-id="7b7ee-121">EventID equals bp2d6</span></span>

5.  <span data-ttu-id="7b7ee-122">ハッシュ UserID が、これら 2 つのイベントのうちのいずれか 1 つのメッセージ内に含まれます</span><span class="sxs-lookup"><span data-stu-id="7b7ee-122">Hashed UserIds will be in the Message of either one of these two events</span></span>

6.  <span data-ttu-id="7b7ee-123">apr3y の場合、メッセージには UserID 値および PUID 値が含まれます</span><span class="sxs-lookup"><span data-stu-id="7b7ee-123">For apr3y, the Message will contain a UserID value and a PUID value</span></span>

7.  <span data-ttu-id="7b7ee-p104">bp2d6 の場合、メッセージにかなりの情報が含まれます。LoggableUserId 値フィールドがハッシュ UserID です。</span><span class="sxs-lookup"><span data-stu-id="7b7ee-p104">For bp2d6, the Message will contain quite a bit of information. The LoggableUserId Value field is the hashed UserID.</span></span>

8.  <span data-ttu-id="7b7ee-126">これらの 2 つのタグのうちのいずれか 1 つからハッシュ UserID が取得されると、ULSViewer のその行の WacSessionId 値の内容は、そのユーザーに関連する WacSessionId になります</span><span class="sxs-lookup"><span data-stu-id="7b7ee-126">Once the hashed UserId is obtained from either of these two tags, the WacSessionId value of that row in ULSViewer will contain the WacSessionId associated with that user</span></span>

9.  <span data-ttu-id="7b7ee-127">問題のユーザーに関連する WacSessionId 値をすべて収集します</span><span class="sxs-lookup"><span data-stu-id="7b7ee-127">Collect all of the WacSessionId values associated with the user in question</span></span>

10. <span data-ttu-id="7b7ee-128">リスト内の最初の WacSessionId で、EventId が "xmnv" に等しく、Message が "UserSessionId=\<WacSessionId\>" に等しいものすべてをフィルター処理します (フィルターの \<WacSessionId\> の部分を実際の WacSessionId に置き換える)</span><span class="sxs-lookup"><span data-stu-id="7b7ee-128">Filter for all EventId equals "xmnv", Message equals "UserSessionId=\<WacSessionId\>" for the first WacSessionId in the list (replacing the \<WacSessionId\> part of the filter with your WacSessionId)</span></span>

11. <span data-ttu-id="7b7ee-129">その WacSessionId に一致する Correlation のすべての値を収集します</span><span class="sxs-lookup"><span data-stu-id="7b7ee-129">Collect all values of Correlation that match that WacSessionId</span></span>

12. <span data-ttu-id="7b7ee-130">ステップ 10-11 を、リスト内にある対象ユーザーの WacSessionId の値すべてについて繰り返します</span><span class="sxs-lookup"><span data-stu-id="7b7ee-130">Repeat steps 10-11 for all values of WacSessionId in your list for the user in question</span></span>

13. <span data-ttu-id="7b7ee-131">Correlation がリスト内の最初の Correlation に等しいものすべてをフィルター処理します</span><span class="sxs-lookup"><span data-stu-id="7b7ee-131">Filter for all Correlation equals the first Correlation in your list</span></span>

14. <span data-ttu-id="7b7ee-132">その Correlation に一致するログすべてを収集します</span><span class="sxs-lookup"><span data-stu-id="7b7ee-132">Collect all logs matching that Correlation</span></span>

15. <span data-ttu-id="7b7ee-133">ステップ 13-14 を、リスト内にある対象ユーザーの Correlation の値すべてについて繰り返します</span><span class="sxs-lookup"><span data-stu-id="7b7ee-133">Repeat steps 13-14 for all values of Correlation in your list for the user in question</span></span>

## <a name="types-of-data"></a><span data-ttu-id="7b7ee-134">データの種類</span><span class="sxs-lookup"><span data-stu-id="7b7ee-134">Types of Data</span></span>

<span data-ttu-id="7b7ee-p105">Office Online のログには、さまざまな異なるタイプのデータが含まれます。ULS ログに含まれるデータの例を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="7b7ee-p105">Office Online logs contain a variety of different types of data. The following are examples of the data that ULS logs may contain:</span></span>

-   <span data-ttu-id="7b7ee-137">製品使用中に発生した問題のエラー コード</span><span class="sxs-lookup"><span data-stu-id="7b7ee-137">Error codes for issues encountered during use of the product</span></span>

-   <span data-ttu-id="7b7ee-138">ボタンのクリックおよびアプリ使用状況についてのその他のデータ</span><span class="sxs-lookup"><span data-stu-id="7b7ee-138">Button clicks and other pieces of data about app usage</span></span>

-   <span data-ttu-id="7b7ee-139">アプリについて、またアプリ内の特定の機能についてのパフォーマンス データ</span><span class="sxs-lookup"><span data-stu-id="7b7ee-139">Performance data about the app and/or particular features within the app</span></span>

-   <span data-ttu-id="7b7ee-140">ユーザーのコンピューターの所在地を示す一般的な位置情報 (IP アドレスから派生する国 / 地域、県、市町村)、ただし正確な地理的位置ではありません</span><span class="sxs-lookup"><span data-stu-id="7b7ee-140">General location information about where the user’s computer is (e.g. country / region, state, and city, derived from the IP address), but not precise geolocation</span></span>

-   <span data-ttu-id="7b7ee-141">ブラウザーに関する基本的なメタデータ (つまりブラウザーの名前とバージョン)、およびコンピューターに関する基本的なメタデータ (OS の種類とバージョン)</span><span class="sxs-lookup"><span data-stu-id="7b7ee-141">Basic metadata about the browser, e.g. browser name and version, and the computer, e.g. OS type and version</span></span>

-   <span data-ttu-id="7b7ee-142">ドキュメント ホストからのエラー メッセージ (OneDrive、SharePoint、Exchange など)</span><span class="sxs-lookup"><span data-stu-id="7b7ee-142">Error messages from the document host (e.g. OneDrive, SharePoint, Exchange)</span></span>

-   <span data-ttu-id="7b7ee-143">ユーザーのアクションには関係しないアプリの内部プロセスに関する情報</span><span class="sxs-lookup"><span data-stu-id="7b7ee-143">Information about processes internal to the app, unrelated to any action the user has taken</span></span>
