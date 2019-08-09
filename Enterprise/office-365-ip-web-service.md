---
title: Office 365 IP アドレスと URL の Web サービス
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/6/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: Office 365 IP アドレスと URL の Web サービスを利用することにより、Office 365 のネットワーク トラフィックの識別と区別がより効率的になり、変更の評価、構成、および最新情報の取得が容易になります。
ms.openlocfilehash: 90de20f28e271e3fb174a883eb9cda3fb1228fb4
ms.sourcegitcommit: 6db61b95b1b5b4312dd6bc42bec6597e359b1bd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2019
ms.locfileid: "36212982"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="dc0fb-103">Office 365 IP アドレスと URL の Web サービス</span><span class="sxs-lookup"><span data-stu-id="dc0fb-103">Office 365 IP Address and URL Web service</span></span>

<span data-ttu-id="dc0fb-104">Office 365 IP アドレスと URL の Web サービスを利用することにより、Office 365 のネットワーク トラフィックの識別と区別がより効率的になり、変更の評価、構成、および最新情報の取得が容易になります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-104">The Office 365 IP Address and URL web service helps you better identify and differentiate Office 365 network traffic, making it easier for you to evaluate, configure, and stay up to date with changes.</span></span> <span data-ttu-id="dc0fb-105">この REST ベースの Web サービスは、2018 年 10 月 2 日に廃止されたダウンロード可能な XML ファイルに代わるものです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-105">This REST-based web service replaces the previous XML downloadable files, which were phased out on October 2, 2018.</span></span>

<span data-ttu-id="dc0fb-106">顧客またはネットワーク境界デバイスのベンダーは、Office 365 の IP アドレスと FQDN エントリ用の Web サービスに対してビルドできます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-106">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span> <span data-ttu-id="dc0fb-107">次の URL を使用して、Web ブラウザーで直接データにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-107">You can access the data directly in a web browser using these URLs:</span></span>

- <span data-ttu-id="dc0fb-108">Office 365 の URL と IP アドレスの範囲の最新バージョンには、[https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-108">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="dc0fb-109">ファイアウォールおよびプロキシ サーバー用の Office 365 の URL と IP アドレスの範囲ページのデータには、[https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-109">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="dc0fb-110">この Web サービスが最初に使用できるようになった 2018 年 7 月以降の最新の変更すべてを取得するには、[https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-110">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="dc0fb-111">顧客は、この Web サービスを使用して次のことを行えます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-111">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="dc0fb-112">PowerShell スクリプトを更新して Office 365 エンドポイント データを取得し、ネットワーク デバイスのフォーマットを変更します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-112">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="dc0fb-113">この情報を使用して、クライアント コンピューターに展開された PAC ファイルを更新します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-113">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="dc0fb-114">ネットワーク境界デバイスのベンダーは、この Web サービスを使用して次のことを行えます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-114">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="dc0fb-115">デバイス ソフトウェアを作成およびテストして、自動構成の一覧をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-115">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="dc0fb-116">現在のバージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-116">Check for the current version.</span></span>
- <span data-ttu-id="dc0fb-117">最近の変更を取得します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-117">Get the current changes.</span></span>

> [!NOTE]
> <span data-ttu-id="dc0fb-118">Azure ExpressRoute を使って Office 365 に接続する場合は、Azure ExpressRoute でサポートされている Office 365 サービスについて詳しく説明している[Office 365 の Azure ExpressRoute](https://docs.microsoft.com/office365/enterprise/azure-expressroute) をお読みください。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-118">If you are using Azure ExpressRoute to connect to Office 365, please review [Azure ExpressRoute for Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) to familiarize yourself with the Office 365 services supported over Azure ExpressRoute.</span></span> <span data-ttu-id="dc0fb-119">また、Office 365 アプリのネットワーク 要求でインターネット接続が必要なものについて [Office 365 URL と IP アドレス範囲](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) もお読みください。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-119">Also review the article [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) to understand which network requests for Office 365 applications require Internet connectivity.</span></span> <span data-ttu-id="dc0fb-120">これは、perimeter セキュリティ デバイスの設定に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-120">This will help to better configure your perimeter security devices.</span></span>

<span data-ttu-id="dc0fb-121">詳しくは、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-121">For more information, see:</span></span>

- [<span data-ttu-id="dc0fb-122">Office 365 技術コミュニティ フォーラムでのお知らせブログの投稿</span><span class="sxs-lookup"><span data-stu-id="dc0fb-122">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="dc0fb-123">Web サービスの使用に関する質問のための Office 365 技術コミュニティ フォーラム</span><span class="sxs-lookup"><span data-stu-id="dc0fb-123">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="dc0fb-124">共通パラメーター</span><span class="sxs-lookup"><span data-stu-id="dc0fb-124">Common parameters</span></span>

<span data-ttu-id="dc0fb-125">これらのパラメーターは、すべての Web サービス メソッドで共通です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-125">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="dc0fb-126">**format=<JSON | CSV>** — 既定では、返されるデータ形式は JSON です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-126">**format=<JSON | CSV>** - By default, the returned data format is JSON.</span></span> <span data-ttu-id="dc0fb-127">コンマ区切り値 (CSV) 形式でデータを返すには、このオプションのパラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-127">Use this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="dc0fb-128">**ClientRequestId=\<guid>** — クライアントの関連付けのために必要な GUID です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-128">**ClientRequestId=\<guid>** - A required GUID that you generate for client association.</span></span> <span data-ttu-id="dc0fb-129">Web サービスを呼び出すコンピューターごとに一意の GUID を生成します (このページに含まれるスクリプトでは、GUID が自動的に生成されます)。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-129">Generate a unique GUID for each machine that calls the web service (the scripts included on this page generate a GUID for you).</span></span> <span data-ttu-id="dc0fb-130">次の例に示す GUID は、今後この Web サービスによってブロックされる可能性があるため使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-130">Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future.</span></span> <span data-ttu-id="dc0fb-131">GUID 形式は _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_で、x は 16 進数を表します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-131">GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number.</span></span>

  <span data-ttu-id="dc0fb-132">GUID を作成するには、[New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell コマンドを使用することも、[Online GUID Generator
](https://www.guidgenerator.com/) などのオンライン サービスを利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-132">To generate a GUID, you can use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command, or use an online service such as [Online GUID Generator](https://www.guidgenerator.com/).</span></span>

## <a name="version-web-method"></a><span data-ttu-id="dc0fb-133">バージョン Web メソッド</span><span class="sxs-lookup"><span data-stu-id="dc0fb-133">Version web method</span></span>

<span data-ttu-id="dc0fb-134">Microsoft は、Office 365 の IP アドレスと FQDN エントリを毎月末に更新しています。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-134">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month.</span></span> <span data-ttu-id="dc0fb-135">サポート インシデント、セキュリティ更新プログラム、またはその他の運用要件により、不定期の更新プログラムが公開されることがあります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-135">Out-of-band updates are sometimes published due to support incidents, security updates or other operational requirements.</span></span>

<span data-ttu-id="dc0fb-136">公開済みの各インスタンスのデータには、バージョン番号が割り当てられます。バージョン Web メソッドを使用すると、Office 365 サービスの各インスタンスの最新のバージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-136">The data for each published instance is assigned a version number, and the version web method enables you to check for the latest version of each Office 365 service instance.</span></span> <span data-ttu-id="dc0fb-137">バージョンの確認を行うのは、1 時間に 1 回以下にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-137">We recommend that you check the version not more than once an hour.</span></span>

<span data-ttu-id="dc0fb-138">バージョン Web メソッドのパラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-138">Parameters for the version web method are:</span></span>

- <span data-ttu-id="dc0fb-139">**AllVersions=<true | false>** — 初期設定では、返されるバージョンは最新のものです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-139">**AllVersions=<true | false>** - By default, the version returned is the latest.</span></span> <span data-ttu-id="dc0fb-140">Web サービスの最初のリリース以降のすべての公開済みバージョンを要求するには、このパラメーターのオプションを含めます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-140">Include this optional parameter to request all published versions since the web service was first released.</span></span>
- <span data-ttu-id="dc0fb-141">**Format=<JSON | CSV | RSS>** — JSON 形式と CSV 形式に加えて、このバージョン Web メソッドでは RSS もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-141">**Format=<JSON | CSV | RSS>** – In addition to the JSON and CSV formats, the version web method also supports RSS.</span></span> <span data-ttu-id="dc0fb-142">このパラメーターのオプションは、_AllVersions=true_ パラメーターと共に使用でき、Outlook や その他の RSS リーダーで使用できる RSS フィードを要求できます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-142">You can use this optional parameter along with the _AllVersions=true_ parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="dc0fb-143">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** — このパラメーターのオプションはバージョンを返すインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-143">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This optional parameter specifies the instance to return the version for.</span></span> <span data-ttu-id="dc0fb-144">省略する場合は、すべてのインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-144">If omitted, all instances are returned.</span></span> <span data-ttu-id="dc0fb-145">有効なインスタンスは次の通りです。Worldwide、China、Germany、USGovDoD、USGovGCCHigh。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-145">Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="dc0fb-146">バージョン Web メソッドはレート制限されていないため、429 HTTP 応答コードが返されることはありません。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-146">The version web method is not rate limited and does not ever return 429 HTTP Response Codes.</span></span> <span data-ttu-id="dc0fb-147">バージョン Web メソッドへの応答には、1 時間のデータのキャッシュを推奨する cache-control ヘッダーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-147">The response to the version web method does include a cache-control header recommending caching of the data for 1 hour.</span></span> <span data-ttu-id="dc0fb-148">バージョン Web メソッドからの結果は、単一のレコードの場合も、レコードの配列の場合もあります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-148">The result from the version web method can be a single record or an array of records.</span></span> <span data-ttu-id="dc0fb-149">各レコードの要素は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-149">The elements of each record are:</span></span>

- <span data-ttu-id="dc0fb-150">instance — Office 365 サービス インスタンスの短い名前です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-150">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="dc0fb-151">latest — 指定されたインスタンスのエンドポイントの最新バージョンです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-151">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="dc0fb-152">versions — 指定されたインスタンスの以前のすべてのバージョンのリストです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-152">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span> <span data-ttu-id="dc0fb-153">この要素は、_AllVersions_ パラメーターが "true" の場合にのみ含まれます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-153">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

### <a name="examples"></a><span data-ttu-id="dc0fb-154">例:</span><span class="sxs-lookup"><span data-stu-id="dc0fb-154">Examples:</span></span>

<span data-ttu-id="dc0fb-155">例 1 要求 URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="dc0fb-155">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="dc0fb-p113">この URI は、各 Office 365 サービス インスタンスの最新バージョンを返します。結果の例:</span><span class="sxs-lookup"><span data-stu-id="dc0fb-p113">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

```json
[
 {
  "instance": "Worldwide",
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD",
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
]
```

> [!IMPORTANT]
> <span data-ttu-id="dc0fb-p114">これらの URI での ClientRequestID パラメーターの GUID は、一例にすぎません。この Web サービスの URI を試すには、独自の GUID を生成してください。これらの例に示されている GUID は、今後この Web サービスではブロックされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-p114">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="dc0fb-161">例 2 要求 URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="dc0fb-161">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="dc0fb-p115">この URI は、指定された Office 365 サービス インスタンスの最新バージョンを返します。結果の例:</span><span class="sxs-lookup"><span data-stu-id="dc0fb-p115">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

<span data-ttu-id="dc0fb-164">例 3 要求 URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="dc0fb-164">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="dc0fb-p116">この URI は CSV 形式で出力を表示します。結果の例:</span><span class="sxs-lookup"><span data-stu-id="dc0fb-p116">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="dc0fb-167">例 4 要求 URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="dc0fb-167">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="dc0fb-p117">この URI は、Office 365 ワールドワイド サービス インスタンスに対して発行された以前のバージョンすべてを表示します。結果の例:</span><span class="sxs-lookup"><span data-stu-id="dc0fb-p117">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

```json
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

<span data-ttu-id="dc0fb-170">例 5 RSS フィード URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="dc0fb-170">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="dc0fb-p118">この URI は、各バージョンの変更リストへのリンクを含む、公開されたバージョンの RSS フィードを表示します。結果の例:</span><span class="sxs-lookup"><span data-stu-id="dc0fb-p118">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<rss version="2.0" xmlns:a10="http://www.w3.org/2005/Atom">
<channel>
<link>http://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
```

## <a name="endpoints-web-method"></a><span data-ttu-id="dc0fb-173">エンドポイント web メソッド</span><span class="sxs-lookup"><span data-stu-id="dc0fb-173">Endpoints web method</span></span>

<span data-ttu-id="dc0fb-174">エンドポイント web メソッドは、Office 365 サービスを構成する IP アドレスの範囲および URL のすべてのレコードを返します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-174">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service.</span></span> <span data-ttu-id="dc0fb-175">ネットワーク デバイスの構成には、常にエンドポイント Web メソッドからの最新データを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-175">The latest data from the endpoints web method should always be used for network device configuration.</span></span> <span data-ttu-id="dc0fb-176">Microsoft では、お客様が時間の余裕を持ってアクセス制御リストおよびプロキシ サーバーのバイパス リストを更新できるよう、新規追加を公開する 30 日前に事前通知を提供しています。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-176">Microsoft provides advance notice 30 days prior to publishing new additions to give you time to update access control lists and proxy server bypass lists.</span></span> <span data-ttu-id="dc0fb-177">エンドポイント Web メソッドをもう一度呼び出す場合は、バージョン Web メソッドにより新しいデータのバージョンが使用可能なことが示された場合にのみ行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-177">We recommend you only call the endpoints web method again when the version web method indicates a new version of the data is available.</span></span>

<span data-ttu-id="dc0fb-178">エンドポイント Web メソッドのパラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-178">Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="dc0fb-179">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** — サービス エリアのコンマ区切リストです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-179">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** - A comma-separated list of service areas.</span></span> <span data-ttu-id="dc0fb-180">有効な項目は、_Common_、_Exchange_、_SharePoint_、および_Skype_です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-180">Valid items are _Common_, _Exchange_, _SharePoint_, and _Skype_.</span></span> <span data-ttu-id="dc0fb-181">_Common_ サービス エリア項目はその他のすべてのサービス エリアの前提条件であるため、Web サービスに常に含まれます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-181">Because Common service area items are a prerequisite for all other service areas, the web service will always include them.</span></span> <span data-ttu-id="dc0fb-182">このパラメーターを含めない場合は、すべてのサービス エリアが返されます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-182">If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="dc0fb-183">**TenantName=<tenant_name>** — Office 365 のテナント名です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-183">**TenantName=<tenant_name>** - Your Office 365 tenant name.</span></span> <span data-ttu-id="dc0fb-184">この web サービスでは、指定した名前を テナント名を含む URL の一部に挿入します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-184">The web service takes your provided name and inserts it in parts of URLs that include the tenant name.</span></span> <span data-ttu-id="dc0fb-185">テナント名を指定しない場合、URL のそれらの部分にワイルドカード文字が使用されます (\*)。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-185">If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="dc0fb-186">**NoIPv6=<true | false>** — お使いのネットワークで IPv6 を使用しない場合は、値を _true_ に設定して出力から IPv6 アドレスを除外します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-186">**NoIPv6=<true | false>** - Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="dc0fb-187">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** — このパラメーターはエンドポイントを返すインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-187">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** - This required parameter specifies the instance to return the endpoints for.</span></span> <span data-ttu-id="dc0fb-188">有効なインスタンスは、_Worldwide_、_China_、_Germany_、_USGovDoD_、_USGovGCCHigh_ です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-188">Valid instances are: _Worldwide_, _China_, _Germany_, _USGovDoD_, and _USGovGCCHigh_.</span></span>

<span data-ttu-id="dc0fb-189">同じクライアント IP アドレスからのエンドポイント Web メソッドの呼び出し回数が多すぎる場合、 HTTP Response Code _429 (要求が多すぎます)_ の応答コードが返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-189">If you call the endpoints web method a large number of times from the same client IP address, you may receive HTTP response code 429 (Too Many Requests).</span></span> <span data-ttu-id="dc0fb-190">この応答コードを受け取った場合、リクエストを再度行うまでに 1 時間待つか、リクエスト用に新しい GUID を生成します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-190">If you get this response code, wait 1 hour before repeating your request, or generate a new GUID for the request.</span></span> <span data-ttu-id="dc0fb-191">一般的なベスト プラクティスとして、バージョン Web メソッドで新しいバージョンのデータが使用可能だと示された場合にのみ、エンドポイント Web メソッドを呼び出すようにします。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-191">Plan to only call the endpoints web method when the version web method indicates there is a new version available.</span></span>

<span data-ttu-id="dc0fb-192">エンドポイント Web メソッドの結果は、各レコードが特定のエンドポイント セットを表すレコードの配列です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-192">The result from the endpoints web method is an array of records in which each record represents a specific endpoint set.</span></span> <span data-ttu-id="dc0fb-193">各レコードの要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-193">The elements for each record are:</span></span>

- <span data-ttu-id="dc0fb-194">id — エンドポイント セットの不変 ID 番号です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-194">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="dc0fb-195">serviceArea — _Common_、_Exchange_、_SharePoint_、または _Skype_ の一部であるサービス エリアのことです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-195">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="dc0fb-196">urls — エンドポイント セットの URL です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-196">urls — URLs for the endpoint set.</span></span> <span data-ttu-id="dc0fb-197">DNS レコードの JSON 配列です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-197">A JSON array of DNS records.</span></span> <span data-ttu-id="dc0fb-198">空白の場合は省略します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-198">Omitted if blank.</span></span>
- <span data-ttu-id="dc0fb-199">tcpPorts — エンドポイント セットの TCP ポートです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-199">tcpPorts — TCP ports for the endpoint set.</span></span> <span data-ttu-id="dc0fb-200">すべてのポート要素は、ポートのカンマ区切りのリストまたはダッシュ文字 (-) で区切られたポート範囲により書式設定されています。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-200">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span> <span data-ttu-id="dc0fb-201">特定のカテゴリのポートは、すべての IP アドレスおよびエンド ポイント内のすべての URL に適用されます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-201">Ports apply to all IP addresses and all URLs in the endpoint set for a given category.</span></span> <span data-ttu-id="dc0fb-202">空白の場合は省略します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-202">Omitted if blank.</span></span>
- <span data-ttu-id="dc0fb-203">udpPorts — このエンドポイント セット内の IP アドレス範囲の UDP ポートです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-203">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span> <span data-ttu-id="dc0fb-204">空白の場合は省略します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-204">Omitted if blank.</span></span>
- <span data-ttu-id="dc0fb-205">ips — 一覧表示された TCP ポートまたは UDP ポートに関連付けられたものとして、このエンドポイント セットに関連付けられている IP アドレスの範囲です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-205">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span> <span data-ttu-id="dc0fb-206">IP アドレス範囲の JSON 配列です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-206">A JSON array of IP address ranges.</span></span> <span data-ttu-id="dc0fb-207">空白の場合は省略します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-207">Omitted if blank.</span></span>
- <span data-ttu-id="dc0fb-208">category — エンドポイント セットの接続性カテゴリです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-208">category — The connectivity category for the endpoint set.</span></span> <span data-ttu-id="dc0fb-209">有効な値は、_Optimize_、_Allow_、および _Default_ です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-209">Valid values are _Optimize_, _Allow_, and _Default_.</span></span> <span data-ttu-id="dc0fb-210">特定の IP アドレスまたは URL についてエンドポイント Web メソッドの出力を検索する場合、クエリで複数のカテゴリが返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-210">If you search the endpoints web method output for the category of a specific IP address or URL, it is possible that your query will return multiple categories.</span></span> <span data-ttu-id="dc0fb-211">最優先のカテゴリの推奨事項に従ってください。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-211">In such a case, follow the recommendation for the highest priority category.</span></span> <span data-ttu-id="dc0fb-212">たとえば、エンドポイントが _Optimize_ と _Allow_ の両方に表示される場合は、_Optimize_ の要件に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-212">For example, if the endpoint appears in both _Optimize_ and _Allow_, you should follow the requirements for _Optimize_.</span></span> <span data-ttu-id="dc0fb-213">必須です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-213">Required.</span></span>
- <span data-ttu-id="dc0fb-214">expressRoute — このエンドポイント セットが ExpressRoute を経由してルーティングされる場合は _True_ で、されない場合は _False_ です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-214">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="dc0fb-215">required — Office 365 のサポートを受けるためにこのエンドポイント セットの接続性が必要な場合は _True_ です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-215">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span> <span data-ttu-id="dc0fb-216">このエンドポイント セットが省略可能な場合は _False_ です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-216">_False_ if this endpoint set is optional.</span></span>
- <span data-ttu-id="dc0fb-217">notes — このテキストは、省略可能のエンドポイントについて、ネットワーク層でこのエンドポイント セットの IP アドレスまたは URL にアクセスできない場合に利用できなくなる Office 365 の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-217">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span> <span data-ttu-id="dc0fb-218">空白の場合は省略します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-218">Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="dc0fb-219">例:</span><span class="sxs-lookup"><span data-stu-id="dc0fb-219">Examples:</span></span>

<span data-ttu-id="dc0fb-220">例 1 要求 URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="dc0fb-220">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="dc0fb-221">この URI は、すべてのワークロードについて Office 365 ワールドワイド インスタンスのすべてのエンドポイントを取得します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-221">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span> <span data-ttu-id="dc0fb-222">出力の抜粋を示す結果の例:</span><span class="sxs-lookup"><span data-stu-id="dc0fb-222">Example result that shows an excerpt of the output:</span></span>

```json
[
 {
  "id": 1,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.protection.outlook.com"
   ],
  "ips":
   [
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32"
   ],
  "tcpPorts": "443",
  "expressRoute": true,
  "category": "Allow"
 },
 {
  "id": 2,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.mail.protection.outlook.com"
   ],
```

<span data-ttu-id="dc0fb-223">この例では、要求の完全な出力に他のエンドポイント セットが含まれる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-223">Note that the full output of the request in this example would contain other endpoint sets.</span></span>

<span data-ttu-id="dc0fb-224">例 2 要求 URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="dc0fb-224">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="dc0fb-225">この例では、Exchange Online および依存関係のみの Office 365 ワールドワイド インスタンスのエンドポイントを取得します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-225">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="dc0fb-226">例 2 の出力は例 1 と似ていますが、結果に SharePoint Online または Skype for Business Online のエンドポイントが含まれない点が異なります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-226">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="dc0fb-227">変更 Web メソッド</span><span class="sxs-lookup"><span data-stu-id="dc0fb-227">Changes web method</span></span>

<span data-ttu-id="dc0fb-228">変更 Web メソッドは、発行された最新の更新を返します。これは通常、IP アドレスの範囲と URL に対する前月の変更です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-228">The changes web method returns the most recent updates that have been published, typically the previous month's changes to IP address ranges and URLs.</span></span>

<span data-ttu-id="dc0fb-229">エンドポイント データへの最も重要な変更は、新しい URL と IP アドレスです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-229">The most critical changes to endpoints data are new URLs and IP addresses.</span></span> <span data-ttu-id="dc0fb-230">IP アドレスがファイアウォール アクセス制御リストに追加されなかったり、URL がプロキシ サーバーのバイパス リストに追加されなかったりした場合、そのネットワークデバイスの背後にいる Office 365 ユーザーのサービスが停止する場合があります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-230">Failure to add an IP address to a firewall access control list or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device.</span></span> <span data-ttu-id="dc0fb-231">運用上の要件にかかわらず、お客様が時間の余裕を持ってアクセス制御リストおよびプロキシ サーバーのバイパス リストを更新できるよう、新しいエンドポイントは、エンドポイントの使用がプロビジョニングされる日の 30 日前に Web サービスに公開されます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-231">Notwithstanding operational requirements, new endpoints are published to the web service 30 days in advance of the date the endpoints are provisioned for use to give you time to update access control lists and proxy server bypass lists.</span></span>

<span data-ttu-id="dc0fb-232">変更 Web メソッドのパラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-232">The required parameter for the changes web method is:</span></span>

- <span data-ttu-id="dc0fb-233">**Version=\<YYYYMMDDNN>** — 必要な URL ルート パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-233">**Version=\<YYYYMMDDNN>** - Required URL route parameter.</span></span> <span data-ttu-id="dc0fb-234">この値は、現在実装しているバージョンです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-234">This value should be the version that you have currently implemented.</span></span> <span data-ttu-id="dc0fb-235">この web サービスはそのバージョン以降の変更を返します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-235">The web service will return the changes since that version.</span></span> <span data-ttu-id="dc0fb-236">形式は _YYYYMMDDNN_ で、_NN_ は 1 日に発行する必要がある複数のバージョンがある場合に増加する自然数で、_00_ は特定日における最初の更新を表します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-236">The format is _YYYYMMDDNN_, where _NN_ is a natural number incremented if there are multiple versions required to be published on a single day, with _00_ representing the first update for a given day.</span></span> <span data-ttu-id="dc0fb-237">Web サービスでは、この_バージョン_のパラメーターが正確に 10 桁であることが要求されます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-237">The web service requires the _version_ parameter to contain exactly 10 digits.</span></span>

<span data-ttu-id="dc0fb-238">エンドポイント Web メソッドと同様に、変更 Web メソッドはレート制限されています。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-238">The changes web method is rate limited in the same way as the endpoints web method.</span></span> <span data-ttu-id="dc0fb-239">429 HTTP の応答コードを受け取った場合、リクエストを再度行うまでに 1 時間待つか、リクエスト用に新しい GUID を生成します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-239">If you receive a 429 HTTP response code, wait 1 hour before repeating your request or generate a new GUID for the request.</span></span>

<span data-ttu-id="dc0fb-240">変更 Web メソッドの結果は、各レコードが特定のバージョンのエンドポイントでの変更を表すレコードの配列です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-240">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span> <span data-ttu-id="dc0fb-241">各レコードの要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-241">The elements for each record are:</span></span>

- <span data-ttu-id="dc0fb-242">id — 変更レコードの不変 ID です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-242">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="dc0fb-243">endpointSetId — 変更されたエンドポイント セット レコードの ID です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-243">endpointSetId - The ID of the endpoint set record that is changed.</span></span>
- <span data-ttu-id="dc0fb-244">disposition — エンドポイント セット レコードに対して行われた変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-244">disposition — Describes what the change did to the endpoint set record.</span></span> <span data-ttu-id="dc0fb-245">値は、_change_、_add_、または _remove_ です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-245">Values are _change_, _add_, or _remove_.</span></span>
- <span data-ttu-id="dc0fb-246">impact — すべての変更がどの環境に対しても同じ重要度を持つわけではありません。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-246">impact — Not all changes will be equally important to every environment.</span></span> <span data-ttu-id="dc0fb-247">この要素は、予想されるこの変更による エンタープライズ ネットワーク境界環境に対する影響を示します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-247">This element describes the expected impact to an enterprise network perimeter environment as a result of this change.</span></span> <span data-ttu-id="dc0fb-248">この属性は、バージョン **2018112800** 以降の変更レコードにのみ含まれます。
  </span><span class="sxs-lookup"><span data-stu-id="dc0fb-248">This element is included only in change records of version **2018112800** and later.</span></span> <span data-ttu-id="dc0fb-249">impact のオプションは次のとおりです。— AddedIp – Office 365 に IP アドレスが追加され、間もなくサービスで有効になります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-249">Options for the impact are: — AddedIp – An IP address was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="dc0fb-250">これは、ファイアウォールまたは他のレイヤー 3 ネットワーク境界デバイスに加える必要のある変更を表します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-250">This represents a change you need to take on a proxy server or URL parsing network perimeter device.</span></span> <span data-ttu-id="dc0fb-251">これが追加されないままその使用が開始された場合、サービスが停止する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-251">If you don’t add this before we start using it, you may experience an outage.</span></span>
  <span data-ttu-id="dc0fb-252">— AddedUrl – Office 365 に URL が追加され、間もなくサービスで有効になります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-252">AddedUrl – A URL was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="dc0fb-253">これは、プロキシ サーバーまたは URL 解析ネットワーク境界デバイスに加える必要がある変更を表します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-253">This represents a change you need to take on a proxy server or URL parsing network perimeter device.</span></span> <span data-ttu-id="dc0fb-254">この URL が追加されないままその使用が開始された場合、サービスが停止する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-254">If you don’t add this before we start using it, you may experience an outage.</span></span>
  <span data-ttu-id="dc0fb-255">— AddedIpAndUrl — IP アドレスと URL の両方が追加されました。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-255">— AddedIpAndUrl — Both an IP address and a URL were added.</span></span> <span data-ttu-id="dc0fb-256">これは、ファイアウォールのレイヤー 3 デバイス、プロキシ サーバー、または URL 解析デバイスのいずれかに加える必要がある変更を表します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-256">AddedIpAndUrl - Both an IP Address and a URL were added. This represents a change you need to take on either a firewall layer 3 device or a proxy server or URL parsing device. If you don’t add this before we start using it, you may experience an outage.</span></span> <span data-ttu-id="dc0fb-257">この IP/URL のペアの使用開始前にこれを追加しない場合、サービスが停止する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-257">If you don’t add this before we start using it, you may experience an outage.</span></span>
  <span data-ttu-id="dc0fb-258">— RemovedIpOrUrl – 少なくとも 1 つの IP アドレスまたは URL が Office 365 から削除されました。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-258">— RemovedIpOrUrl – At least one IP address or URL was removed from Office 365.</span></span> <span data-ttu-id="dc0fb-259">境界デバイスからネットワークエンドポイントを削除します。ただし、これを行うための期限はありません。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-259">RemovedIpOrUrl – At least one IP Address or URL was removed from Office 365. You should remove the network endpoints from your perimeter devices, but there’s no deadline for you to do this.</span></span>
  <span data-ttu-id="dc0fb-260">— ChangedIsExpressRoute – ExpressRoute サポート属性が変更されました。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-260">— ChangedIsExpressRoute – The ExpressRoute support attribute was changed.</span></span> <span data-ttu-id="dc0fb-261">ExpressRoute を使用する場合は、構成に応じてアクションを実行する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-261">ChangedIsExpressRoute – The ExpressRoute support attribute was changed. If you use ExpressRoute then you may need to take action depending on your configuration.</span></span>
  <span data-ttu-id="dc0fb-262">— MovedIpOrUrl – このエンドポイント セットと他のエンドポイント セットの間で、IP アドレスまたは URL を移動しました。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-262">MovedIpOrUrl – We moved an IP Address or Url between this endpoint set and another one. Generally no action is required.</span></span> <span data-ttu-id="dc0fb-263">通常、必要なアクションはありません。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-263">Indicates that no action is required</span></span>
  <span data-ttu-id="dc0fb-264">— RemovedDuplicateIpOrUrl – 重複する IP アドレスまたは URL を削除しましたが、引き続き Office 365 用に公開されています。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-264">RemovedDuplicateIpOrUrl – We removed a duplicate IP Address or Url but it’s still published for Office 365. Generally no action is required.</span></span> <span data-ttu-id="dc0fb-265">通常、必要なアクションはありません。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-265">Indicates that no action is required</span></span>
  <span data-ttu-id="dc0fb-266">— OtherNonPriorityChanges – メモ フィールドなど、その他のすべてのオプションよりも重要度が低いものを変更しました。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-266">OtherNonPriorityChanges – We changed something less critical than all of the other options like a note field</span></span>
- <span data-ttu-id="dc0fb-267">version — 変更が導入された公開済みのエンドポイント セットのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-267">version — The version of the published endpoint set in which the change was introduced.</span></span> <span data-ttu-id="dc0fb-268">バージョン番号の形式は _YYYYMMDDNN_ で、_NN_ は 1 日に発行する必要があるバージョンが複数ある場合に増加する自然数です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-268">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="dc0fb-269">previous — エンドポイント セットで変更された要素の以前の値を詳述するサブストラクチャです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-269">previous - A substructure detailing previous values of changed elements on the endpoint set.</span></span> <span data-ttu-id="dc0fb-270">これは、新しく追加されたエンドポイント セットには含まれません。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-270">This will not be included for newly added endpoint sets.</span></span> <span data-ttu-id="dc0fb-271">_ExpressRoute_、_serviceArea_、_category_、_required_、_tcpPorts_、_udpPorts_、および _notes_ が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-271">Includes  _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="dc0fb-272">current — エンドポイント セットで変更された要素の変更後の値を詳述するサブストラクチャです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-272">current - A substructure detailing updated values of changes elements on the endpoint set.</span></span> <span data-ttu-id="dc0fb-273">_ExpressRoute_、_serviceArea_、_category_、_required_、_tcpPorts_、_udpPorts_、および _notes_が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-273">Includes _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="dc0fb-274">add — エンドポイント セット コレクションに追加する項目の詳細を示すサブストラクチャです。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-274">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span> <span data-ttu-id="dc0fb-275">追加がない場合は省略します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-275">Omitted if there are no removals.</span></span>
  <span data-ttu-id="dc0fb-276">— effectiveDate — 追加がサービス内で有効になる時点を示すデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-276">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  <span data-ttu-id="dc0fb-277">— ips — _ips_ 配列に追加する項目です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-277">ips - Items to be added to the _ips_ array.</span></span>
  <span data-ttu-id="dc0fb-278">— urls- _urls_ 配列に追加する項目です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-278">urls- Items to be added to the _urls_ array.</span></span>
- <span data-ttu-id="dc0fb-279">remove — エンドポイント セットから削除するサブストラクチャの詳細項目です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-279">remove - A substructure detailing items to be removed from the endpoint set.</span></span> <span data-ttu-id="dc0fb-280">削除するものがない場合は省略します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-280">Omitted if there are no removals.</span></span>
  <span data-ttu-id="dc0fb-281">— ips — _ips_ 配列から削除する項目です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-281">ips - Items to be removed from the _ips_ array.</span></span>
  <span data-ttu-id="dc0fb-282">— urls- _urls_ 配列から削除する項目です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-282">urls- Items to be removed from the _urls_ array.</span></span>

### <a name="examples"></a><span data-ttu-id="dc0fb-283">例:</span><span class="sxs-lookup"><span data-stu-id="dc0fb-283">Examples:</span></span>

<span data-ttu-id="dc0fb-284">例 1 要求 URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="dc0fb-284">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="dc0fb-p144">これにより、Office 365 ワールドワイド サービス インスタンスに対する以前の変更がすべて要求されます。結果の例:</span><span class="sxs-lookup"><span data-stu-id="dc0fb-p144">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

```json
[
 {
  "id": 424,
  "endpointSetId": 32,
  "disposition": "Change",
  "version": "2018062700",
  "remove":
   {
    "urls":
     [
      "*.api.skype.com", "skypegraph.skype.com"
     ]
   }
 },
 {
  "id": 426,
  "endpointSetId": 31,
  "disposition": "Change",
  "version": "2018062700",
  "add":
   {
    "effectiveDate": "20180609",
    "ips":
     [
      "51.140.203.190/32"
     ]
   },
  "remove":
   {
    "ips":
     [
```

<span data-ttu-id="dc0fb-287">例 2 要求 URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="dc0fb-287">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="dc0fb-p145">これにより、指定したバージョン以降の Office 365 ワールドワイド インスタンスへの変更が要求されます。この場合、指定されたバージョンは最新のものです。結果の例:</span><span class="sxs-lookup"><span data-stu-id="dc0fb-p145">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

```json
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]
```

## <a name="example-powershell-script"></a><span data-ttu-id="dc0fb-291">PowerShell スクリプト</span><span class="sxs-lookup"><span data-stu-id="dc0fb-291">Example PowerShell Script</span></span>

<span data-ttu-id="dc0fb-292">更新されたデータに対して行う必要があるアクションがあるかどうかを確認するには、この PowerShell スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-292">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data.</span></span> <span data-ttu-id="dc0fb-293">このスクリプトは、バージョンの更新を確認するために、スケジュールされたタスクとして実行できます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-293">You can run this script as a scheduled task to check for a version update.</span></span> <span data-ttu-id="dc0fb-294">Web サービスへ過剰な負荷を与えないために、スクリプトは 1 時間に 1 回以上実行しないようにします。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-294">To avoid excessive load on the web service, try not to run the script more than once an hour.</span></span>

<span data-ttu-id="dc0fb-295">このスクリプトでは、次のことが行われます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-295">The ExchUcUtil.ps1 script does the following:</span></span>

- <span data-ttu-id="dc0fb-296">Web サービスの REST API を呼び出して、現在の Office 365 ワールドワイド インスタンスのエンドポイントのバージョン番号を確認します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-296">Checks the version number of the current Office 365 Worldwide instance endpoints by calling the web service REST API.</span></span>
- <span data-ttu-id="dc0fb-297">_$Env:TEMP\O365_endpoints_latestversion.txt_ で現在のバージョンのファイルを確認します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-297">Checks for a current version file at _$Env:TEMP\O365_endpoints_latestversion.txt_.</span></span> <span data-ttu-id="dc0fb-298">通常、グローバル変数 **$Env:TEMP** のパスは、_C:\Users\\<ユーザー名\>\AppData\Local\Temp_ です。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-298">The path of the global variable **$Env:TEMP** is usually _C:\Users\\<username\>\AppData\Local\Temp_.</span></span>
- <span data-ttu-id="dc0fb-299">このスクリプトの実行が今回が初めての場合、スクリプトは現在のバージョンとすべての現在の IP アドレスおよび URL を返し、エンドポイント バージョンを _$Env:TEMP\O365_endpoints_latestversion.txt_ に書き込み、エンドポイント データ出力をファイル _$Env:TEMP\O365_endpoints_data.txt_ に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-299">If this is the first time the script has been run, the script returns the current version and all current IP addresses and URLs, writes the endpoints version to the file _$Env:TEMP\O365_endpoints_latestversion.txt_ and the endpoints data output to the file _$Env:TEMP\O365_endpoints_data.txt_.</span></span> <span data-ttu-id="dc0fb-300">出力ファイルのパスまたは名前を変更するには、次の行を編集します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-300">You can modify the path and/or name of the output file by editing these lines:</span></span>

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- <span data-ttu-id="dc0fb-301">これ以降のスクリプト実行では、最新の Web サービス バージョンが _O365_endpoints_latestversion.txt_ ファイルのバージョンと同じである場合、スクリプトは何も変更せずに終了します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-301">On each subsequent execution of the script, if the latest web service version is identical to the version in the _O365_endpoints_latestversion.txt_ file, the script exits without making any changes.</span></span>
- <span data-ttu-id="dc0fb-302">最新の Web サービスのバージョンが _O365_endpoints_latestversion.txt_ ファイル内でのバージョンよりも新しい場合、スクリプトはエンドポイントを返し、**Allow** カテゴリおよび **Optimize** カテゴリのエンドポイントをフィルタリングし、_O365_endpoints_latestversion.txt_ ファイル内でバージョンを更新し、更新されたデータを _O365_endpoints_data.txt_ ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-302">When the latest web service version is newer than the version in the _O365_endpoints_latestversion.txt_ file, the script returns the endpoints and filters for the **Allow** and **Optimize** category endpoints, updates the version in the _O365_endpoints_latestversion.txt_ file, and writes the updated data to the _O365_endpoints_data.txt_ file.</span></span>

<span data-ttu-id="dc0fb-303">スクリプトは、スクリプトが実行されるコンピューター用に一意の _ClientRequestId_ を生成し、複数の呼び出しでこの ID を再利用します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-303">The script generates a unique _ClientRequestId_ for the computer it is executed on, and reuses this ID across multiple calls.</span></span> <span data-ttu-id="dc0fb-304">この ID は _O365_endpoints_latestversion.txt_ ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-304">This ID is stored in the _O365_endpoints_latestversion.txt_ file.</span></span>

### <a name="to-run-the-powershell-script"></a><span data-ttu-id="dc0fb-305">PowerShell スクリプトを実行するには</span><span class="sxs-lookup"><span data-stu-id="dc0fb-305">To run the ExchUCUtil Windows PowerShell script</span></span>

1. <span data-ttu-id="dc0fb-306">スクリプトをコピーし、_Get-O365WebServiceUpdates.ps1_ としてローカルのハード ドライブまたはスクリプトの場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-306">Copy the script and save it to your local hard drive or script location as _Get-O365WebServiceUpdates.ps1_.</span></span>
1. <span data-ttu-id="dc0fb-307">お好みのスクリプト エディター (PowerShell ISE や VS Code など) でスクリプトを実行します。または、次のコマンドを使用して PowerShell コンソールからスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-307">Execute the script in your preferred script editor such as the PowerShell ISE or VS Code, or from a PowerShell console using the following command:</span></span>

    ``` powershell
   powershell.exe -file <path>\Get-O365WebServiceUpdates.ps1
    ```

    <span data-ttu-id="dc0fb-308">スクリプトに渡すパラメーターはありません。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-308">There are no parameters to pass to the script.</span></span>

```powershell
<# Get-O365WebServiceUpdates.ps1
From https://aka.ms/ipurlws
v1.1 8/6/2019

DESCRIPTION
This script calls the REST API of the Office 365 IP and URL Web Service (Worldwide instance)
and checks to see if there has been a new update since the version stored in an existing
$Env:TEMP\O365_endpoints_latestversion.txt file in your user directory's temp folder
(usually C:\Users\<username>\AppData\Local\Temp).
If the file doesn't exist, or the latest version is newer than the current version in the
file, the script returns IPs and/or URLs that have been changed, added or removed in the latest
update and writes the new version and data to the output file $Env:TEMP\O365_endpoints_data.txt.

USAGE
Run as a scheduled task every 60 minutes.

PARAMETERS
n/a

PREREQUISITES
PS script execution policy: Bypass
PowerShell 3.0 or later
Does not require elevation
#>

#Requires -Version 3.0

# web service root URL
$ws = "https://endpoints.office.com"
# path where output files will be stored
$versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
$datapath = $Env:TEMP + "\O365_endpoints_data.txt"

# fetch client ID and version if version file exists; otherwise create new file and client ID
if (Test-Path $versionpath) {
    $content = Get-Content $versionpath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
    Write-Output ("Version file exists! Current version: " + $lastVersion)
}
else {
    Write-Output ("First run! Creating version file at " + $versionpath + ".")
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $versionpath
}

# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"
    # write the new version number to the version file
    @($clientRequestId, $version.latest) | Out-File $versionpath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    # URL results
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    # IPv4 results
    $flatIp4s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings contain dots
        $ip4s = $ips | Where-Object { $_ -like '*.*' }
        $ip4CustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ip4CustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip4CustomObjects
    }
    # IPv6 results
    $flatIp6s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv6 strings contain colons
        $ip6s = $ips | Where-Object { $_ -like '*:*' }
        $ip6CustomObjects = @()
        if ($endpointSet.category -in ("Optimize")) {
            $ip6CustomObjects = $ip6s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip6CustomObjects
    }

    # write output to screen
    Write-Output ("Client Request ID: " + $clientRequestId)
    Write-Output ("Last Version: " + $lastVersion)
    Write-Output ("New Version: " + $version.latest)
    Write-Output ""
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "IPv6 Firewall IP Address Ranges"
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    Write-Output ("IP and URL data written to " + $datapath)

    # write output to data file
    Write-Output "Office 365 IP and UL Web Service data" | Out-File $datapath
    Write-Output "Worldwide instance" | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output ("Version: " + $version.latest) | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv4 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv6 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "URLs for Proxy Server" | Out-File $datapath -Append
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-File $datapath -Append
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date."
}
```

## <a name="example-python-script"></a><span data-ttu-id="dc0fb-309">Python スクリプト</span><span class="sxs-lookup"><span data-stu-id="dc0fb-309">Example Python Script</span></span>

<span data-ttu-id="dc0fb-p150">ここに示した Python スクリプトは、Windows 10 で Python 3.6.3 を使用してテストしたもので、これを実行すれば、更新されたデータに対して必要なアクションがあるかどうかを確認できます。このスクリプトは、Office 365 ワールドワイド インスタンス エンドポイントのバージョン番号をチェックします。変更がある場合は、エンドポイントをダウンロードし、_Allow_ カテゴリと _Optimize_ カテゴリのエンドポイントのフィルター処理を行います。また、複数の呼び出しにわたって一意の ClientRequestId を使用し、見つかった最新バージョンを一時ファイルに保存します。バージョンの更新を確認するために、1 時間に 1 回このスクリプトを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-p150">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

```python
import json
import os
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = os.environ['TEMP'] + '\endpoints_clientid_latestversion.txt'
# fetch client ID and version if data exists; otherwise create new file
if os.path.exists(datapath):
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))

    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

## <a name="web-service-interface-versioning"></a><span data-ttu-id="dc0fb-315">Web サービス インターフェース バージョニング</span><span class="sxs-lookup"><span data-stu-id="dc0fb-315">Web Service interface versioning</span></span>

<span data-ttu-id="dc0fb-316">今後、これらの Web サービス メソッドのパラメーターまたは結果の更新が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-316">Updates to the parameters or results for these web service methods may be required in the future.</span></span> <span data-ttu-id="dc0fb-317">これらの Web サービスの一般的提供バージョンが公開された後、Microsoft では、Web サービスの重要な更新について事前通知を提供するよう合理的な範囲で努めます。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-317">After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service.</span></span> <span data-ttu-id="dc0fb-318">Microsoft は、更新プログラムにより Web サービスを使用しているクライアントが変更を行う必要が生じると判断した場合、新しいバージョンのリリース後、少なくとも 12 か月間、その Web サービスの以前のバージョン (1 つ前のバージョン) を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-318">When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least 12 months after the release of the new version.</span></span> <span data-ttu-id="dc0fb-319">お客様がその間にアップグレードを行わない場合、Web サービスとそのメソッドにアクセスできなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-319">Customers who do not upgrade during that time may be unable to access the web service and its methods.</span></span> <span data-ttu-id="dc0fb-320">Web サービス インターフェイスのシグネチャに次の変更が加えられた場合、お客様は Web サービスのクライアントがエラーが発生することなく引き続き動作することを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-320">Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="dc0fb-321">古いクライアントによって提供される必要がなく、古いクライアントが受け取る結果に影響を与えない、新しいオプションのパラメーターを既存の Web メソッドに追加する。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-321">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="dc0fb-322">応答 REST 項目の 1 つに新しい名前付き属性を追加する、または応答 CSV に列を追加する。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-322">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="dc0fb-323">新しい Web メソッドに、古いクライアントから呼び出されない新しい名前を追加する。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-323">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="update-notifications"></a><span data-ttu-id="dc0fb-324">更新の通知</span><span class="sxs-lookup"><span data-stu-id="dc0fb-324">Update notifications</span></span>

<span data-ttu-id="dc0fb-325">IP アドレスと URL の変更が Web サービスに発行された際にメール通知を受け取るには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-325">You can use a few different methods to get email notifications when changes to the IP addresses and URLs are published to the web service.</span></span>

- <span data-ttu-id="dc0fb-326">Microsoft Flow ソリューションを使用する方法については、「[Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs (Microsoft Flow を使用して Office 365 IP アドレスと URL への変更の通知メールを受け取る)](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-326">For information about a Microsoft Flow sample and template, see [Use Microsoft Flow to receive an email for changes to Office 365 IP addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>
- <span data-ttu-id="dc0fb-327">ARM テンプレートを使用して Azure Logic App を展開する場合は、「[Office 365 Update Notification (v1.1) (Office 365 更新通知 (v 1.1))](https://aka.ms/ipurlws-updates-template)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-327">To deploy an Azure Logic App using an ARM template, see [Office 365 Update Notification (v1.1)](https://aka.ms/ipurlws-updates-template).</span></span>
- <span data-ttu-id="dc0fb-328">PowerShell を使用して独自の通知スクリプトを作成するには、「[Send-MailMessage](https://docs.microsoft.com/ja-JP/powershell/module/microsoft.powershell.utility/send-mailmessage)」 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-328">To write your own notification script using PowerShell, see [Send-MailMessage](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/send-mailmessage).</span></span>

## <a name="exporting-a-proxy-pac-file"></a><span data-ttu-id="dc0fb-329">プロキシ PAC ファイルのエクスポート</span><span class="sxs-lookup"><span data-stu-id="dc0fb-329">Exporting a Proxy PAC file</span></span>

<span data-ttu-id="dc0fb-330">[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) は Office 365 の IP アドレスと URL Web サービスから最新のネットワーク エンドポイントを読み取る PowerShell スクリプトで、サンプルの PAC ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-330">[PowerShell Gallery Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) is a PowerShell script that reads the latest network endpoints from the Office 365 IP Address and URL Web service and creates a sample PAC file. You can modify the script so that it integrates with your existing PAC file management.</span></span> <span data-ttu-id="dc0fb-331">Get-PacFile の使用に関する詳細情報については、「[重要な Office 365 トラフィックの直接ルーティング用 PAC ファイルの使用](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc0fb-331">For information on using Get-PacFile, see [Use a PAC file for direct routing of vital Office 365 traffic](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic).</span></span>

## <a name="related-topics"></a><span data-ttu-id="dc0fb-332">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc0fb-332">Related Topics</span></span>
  
[<span data-ttu-id="dc0fb-333">Office 365 の URL と IP アドレスの範囲</span><span class="sxs-lookup"><span data-stu-id="dc0fb-333">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[<span data-ttu-id="dc0fb-334">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="dc0fb-334">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)
  
[<span data-ttu-id="dc0fb-335">Office 365 エンドポイントの FAQ</span><span class="sxs-lookup"><span data-stu-id="dc0fb-335">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="dc0fb-336">Office 365 ネットワーク接続の原則</span><span class="sxs-lookup"><span data-stu-id="dc0fb-336">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="dc0fb-337">Office 365 のネットワークとパフォーマンスのチューニング</span><span class="sxs-lookup"><span data-stu-id="dc0fb-337">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="dc0fb-338">Office 365 ネットワーク接続の評価</span><span class="sxs-lookup"><span data-stu-id="dc0fb-338">Office 365 network connectivity principles</span></span>](assessing-network-connectivity.md)
  
[<span data-ttu-id="dc0fb-339">Skype for Business Online でのメディア品質とネットワーク接続のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="dc0fb-339">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="dc0fb-340">Skype for Business Online 向けのネットワークの最適化</span><span class="sxs-lookup"><span data-stu-id="dc0fb-340">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="dc0fb-341">ベースラインとパフォーマンス履歴を使用した、Office 365 のパフォーマンスのチューニング</span><span class="sxs-lookup"><span data-stu-id="dc0fb-341">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="dc0fb-342">Office 365 のパフォーマンスに関するトラブルシューティングの計画</span><span class="sxs-lookup"><span data-stu-id="dc0fb-342">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
