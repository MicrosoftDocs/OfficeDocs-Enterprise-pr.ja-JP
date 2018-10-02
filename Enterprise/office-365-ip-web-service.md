---
title: Office 365 IP アドレスと URL の Web サービス
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/4/2018
ms.audience: ITPro
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
description: Office 365 のネットワーク トラフィックをよりよく識別し区別するために、新しい Web サービスによって Office 365 エンドポイントが公開されます。これにより、変更を評価し、構成し、最新の状況を把握することが容易になります。この新しい Web サービスは、現在利用できるダウンロード可能な XML ファイルに代わるものです。
ms.openlocfilehash: 2b5763b9f8f08f2cc619331dac70743474a8515b
ms.sourcegitcommit: d67e73f6cdc1e8d220d90a239e23e218f24528d2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/21/2018
ms.locfileid: "24961826"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="bf79e-104">\*\*Office 365 IP アドレスと URL の Web サービス \*\*</span><span class="sxs-lookup"><span data-stu-id="bf79e-104">**Office 365 IP Address and URL Web service**</span></span>

<span data-ttu-id="bf79e-p102">Office 365 のネットワーク トラフィックをよりよく識別し区別するために、新しい Web サービスによって Office 365 エンドポイントが公開されます。これにより、変更を評価し、構成し、また変更の最新の状況を把握することが容易になります。この新しい Web サービスは、現在利用できるダウンロード可能な XML ファイルに代わるものです。XML 形式は、2018 年 10 月 2 日に廃止される予定です。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p102">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service replaces the XML downloadable files that are currently available. The XML format is planned to be phased out on October 2, 2018.</span></span>

<span data-ttu-id="bf79e-p103">顧客またはネットワーク境界デバイスのベンダーは、Office 365 の IP アドレスと FQDN エントリ用の新しい REST ベースの Web サービスに対してビルドできます。次の URL を使用して、Web ブラウザーで直接データにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p103">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span>

- <span data-ttu-id="bf79e-110">Office 365 の URL と IP アドレスの範囲の最新バージョンには、[https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="bf79e-110">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="bf79e-111">ファイアウォールおよびプロキシ サーバー用の Office 365 の URL と IP アドレスの範囲ページのデータには、[https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="bf79e-111">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="bf79e-112">この Web サービスが最初に使用できるようになる 2018 年 7 月末以降、最新の変更すべてを取得するには、[https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="bf79e-112">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="bf79e-113">顧客は、この Web サービスを使用して次のことを行えます。</span><span class="sxs-lookup"><span data-stu-id="bf79e-113">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="bf79e-114">PowerShell スクリプトを更新して Office 365 エンドポイント データを取得し、ネットワーク デバイスのフォーマットを変更します。</span><span class="sxs-lookup"><span data-stu-id="bf79e-114">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="bf79e-115">この情報を使用して、クライアント コンピューターに展開された PAC ファイルを更新します。</span><span class="sxs-lookup"><span data-stu-id="bf79e-115">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="bf79e-116">ネットワーク境界デバイスのベンダーは、この Web サービスを使用して次のことを行えます。</span><span class="sxs-lookup"><span data-stu-id="bf79e-116">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="bf79e-117">デバイス ソフトウェアを作成およびテストして、自動構成の一覧をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="bf79e-117">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="bf79e-118">現在のバージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="bf79e-118">Check for the current version.</span></span>
- <span data-ttu-id="bf79e-119">最近の変更を取得します。</span><span class="sxs-lookup"><span data-stu-id="bf79e-119">Get the current changes.</span></span>

<span data-ttu-id="bf79e-120">追加情報については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf79e-120">For additional information, see:</span></span>

- [<span data-ttu-id="bf79e-121">Office 365 技術コミュニティ フォーラムでのお知らせブログの投稿</span><span class="sxs-lookup"><span data-stu-id="bf79e-121">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="bf79e-122">Web サービスの使用に関する質問のための Office 365 技術コミュニティ フォーラム</span><span class="sxs-lookup"><span data-stu-id="bf79e-122">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="bf79e-123">**共通パラメーター**</span><span class="sxs-lookup"><span data-stu-id="bf79e-123">**Common parameters**</span></span>

<span data-ttu-id="bf79e-124">次のパラメーターは、すべての Web サービス メソッド共通です。</span><span class="sxs-lookup"><span data-stu-id="bf79e-124">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="bf79e-p104">**format=CSV | JSON** - クエリ文字列パラメーター。既定では、返されるデータ形式は JSON です。コンマ区切り値 (CSV) 形式でデータを返すには、このオプションのパラメーターを含めます。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p104">**format=CSV | JSON** - Query string parameter. By default, the returned data format is JSON. Include this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="bf79e-p105">**ClientRequestId** - クエリ文字列パラメーター。クライアントの関連付けのために生成する必要がある GUID。Web サービスを呼び出す各コンピューターに GUID を生成する必要があります。今後、この Web サービスによってブロックされる可能性があるため、次の例に示す GUID は使用しないでください。GUID 形式 _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_、x は 16 進数。GUID を生成するには、[New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p105">**ClientRequestId** - Query string parameter. A required GUID that you generate for client association. You should generate a GUID for each machine that calls the web service. Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future. GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number. To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span>

## <a name="version-web-method"></a><span data-ttu-id="bf79e-134">**バージョン Web メソッド**</span><span class="sxs-lookup"><span data-stu-id="bf79e-134">**Version web method**</span></span>

<span data-ttu-id="bf79e-p106">Microsoft では、Office 365 の IP アドレスと FQDN のエントリを毎月末に更新し、運用またはサポートの要件については不定期に更新します。公開済みの各インスタンスのデータには、バージョン番号が割り当てられます。バージョン Web メソッドを使用すると、Office 365 サービスの各インスタンスの最新のバージョンをポーリングできます。毎日、または最短で 1 時間ごとにバージョンを確認することをお勧めします。新しいバージョンは、毎月の初めに出る予定です。場合によっては、サポート インシデント、セキュリティ、その他の運用要件などのため、月の初め以外にも新しいバージョンが出ることもあります。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p106">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly. New versions should be expected at the start of each month. Sometimes due to support incident, security, or other operational requirements there will be new versions during the month.</span></span>

<span data-ttu-id="bf79e-141">バージョン Web メソッドには 1 つのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="bf79e-141">There is one parameter for the version web method:</span></span>

- <span data-ttu-id="bf79e-p107">**AllVersions=true** - クエリ文字列パラメーター。既定では、返されるバージョンは最新のものです。すべての公開済みバージョンを要求するには、このオプション パラメーターを含めます。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p107">**AllVersions=true** - Query string parameter. By default, the version returned is the latest. Include this optional parameter to request all published versions.</span></span>
- <span data-ttu-id="bf79e-p108">**Format=JSON** | **CSV** | **RSS** – JSON 形式および CSV 形式に加えて、バージョン Web メソッドは RSS もサポートしています。これを AllVersions=true パラメーターと共に使用して、Outlook や他の RSS リーダーで使用できる RSS フィードを要求できます。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p108">**Format=JSON** | **CSV** | **RSS** – In addition to the JSON and CSV formats, the version web method also supports RSS. You can use this along with the allVersions=true parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="bf79e-p109">**Instance** - ルート パラメーター。この省略可能なパラメーターは、バージョンを返すインスタンスを指定します。省略した場合は、すべてのインスタンスが返されます。有効なインスタンスは次のとおりです。Worldwide、China、Germany、USGovDoD、USGovGCCHigh。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p109">**Instance** - Route parameter. This optional parameter specifies the instance to return the version for. If omitted, all instances are returned. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="bf79e-p110">バージョン Web メソッドの結果は、単一レコードまたはレコードの配列です。各レコードの要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p110">The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>

- <span data-ttu-id="bf79e-153">instance - Office 365 サービス インスタンスの短い名前。</span><span class="sxs-lookup"><span data-stu-id="bf79e-153">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="bf79e-154">latest - 指定されたインスタンスのエンドポイントの最新バージョン。</span><span class="sxs-lookup"><span data-stu-id="bf79e-154">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="bf79e-p111">versions - 指定されたインスタンスの以前のバージョンすべてのリスト。この要素は、AllVersions パラメーターが true の場合にのみ含まれます。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p111">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

<span data-ttu-id="bf79e-p112">Microsoft Flow を使用して、IP アドレスや URL への変更のメール通知を受け取れます。「[Microsoft Flow を使用して、Office 365 IP アドレスや URL への変更のメール通知を受け取る](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p112">You can use Microsoft Flow to get email notifications of changes to the IP Addresses and URLs. See [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>

### <a name="examples"></a><span data-ttu-id="bf79e-159">**例:**</span><span class="sxs-lookup"><span data-stu-id="bf79e-159">**Examples:**</span></span>

<span data-ttu-id="bf79e-160">例 1 要求 URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bf79e-160">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bf79e-p113">この URI は、各 Office 365 サービス インスタンスの最新バージョンを返します。結果の例:</span><span class="sxs-lookup"><span data-stu-id="bf79e-p113">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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

[!IMPORTANT]
<span data-ttu-id="bf79e-p114">これらの URI での ClientRequestID パラメーターの GUID は、一例にすぎません。この Web サービスの URI を試すには、独自の GUID を生成してください。これらの例に示されている GUID は、今後この Web サービスではブロックされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p114">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="bf79e-166">例 2 要求 URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bf79e-166">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bf79e-p115">この URI は、指定された Office 365 サービス インスタンスの最新バージョンを返します。結果の例:</span><span class="sxs-lookup"><span data-stu-id="bf79e-p115">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}

```

<span data-ttu-id="bf79e-169">例 3 要求 URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bf79e-169">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bf79e-p116">この URI は CSV 形式で出力を表示します。結果の例:</span><span class="sxs-lookup"><span data-stu-id="bf79e-p116">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="bf79e-172">例 4 要求 URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bf79e-172">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bf79e-p117">この URI は、Office 365 ワールドワイド サービス インスタンスに対して発行された以前のバージョンすべてを表示します。結果の例:</span><span class="sxs-lookup"><span data-stu-id="bf79e-p117">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="bf79e-175">例 5 RSS フィード URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="bf79e-175">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="bf79e-p118">この URI は、各バージョンの変更リストへのリンクを含む、公開されたバージョンの RSS フィードを表示します。結果の例:</span><span class="sxs-lookup"><span data-stu-id="bf79e-p118">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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
...
```

## <a name="endpoints-web-method"></a><span data-ttu-id="bf79e-178">**エンドポイント Web メソッド**</span><span class="sxs-lookup"><span data-stu-id="bf79e-178">**Endpoints web method**</span></span>

<span data-ttu-id="bf79e-p119">エンドポイント Web メソッドは、Office 365 サービスを構成する IP アドレスの範囲および URL のすべてのレコードを返します。エンドポイント Web メソッドからの最新データをネットワーク デバイスの構成に使用する必要がありますが、追加の事前通知によって公開後 30 日間、データをキャッシュすることができます。エンドポイント Web メソッドのパラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p119">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service. While the latest data from the endpoints web method should be used for network device configuration, the data can be cached for up to 30 days after it is published due to the advance notice provided for additions. Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="bf79e-p120">**ServiceAreas** - クエリ文字列パラメーター。サービス エリアのコンマ区切りリスト。有効な項目は、Common、Exchange、SharePoint、Skype です。Common サービス エリア項目は、他のすべてのサービス エリアの前提条件であるため、この Web サービスに常に含まれます。このパラメーターを含めない場合は、すべてのサービス エリアが返されます。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p120">**ServiceAreas** - Query string parameter. A comma-separated list of service areas. Valid items are Common,Exchange,SharePoint,Skype. Because Common service area items are a prerequisite for all other service areas, the web service will always include them. If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="bf79e-p121">**TenantName** - クエリ文字列パラメーター。お使いの Office 365 テナント名。この Web サービスでは、指定された名前を、テナント名を含む URL の一部に挿入します。テナント名を指定しない場合、URL のこれらの部分にはワイルドカード文字 (\*) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p121">**TenantName** - Query string parameter. Your Office 365 tenant name. The web service takes your provided name and inserts it in parts of URLs that include the tenant name. If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="bf79e-p122">**NoIPv6** - クエリ文字列パラメーター。お使いのネットワークで IPv6 を使用しない場合など、出力から IPv6 アドレスを除外するには true に設定します。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p122">**NoIPv6** - Query string parameter. Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="bf79e-p123">**Instance** - ルート パラメーター。この必須パラメーターは、エンドポイントを返すインスタンスを指定します。有効なインスタンスは次のとおりです。Worldwide、China、Germany、USGovDoD、USGovGCCHigh。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p123">**Instance** - Route parameter. This required parameter specifies the instance to return the endpoints for. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="bf79e-p124">エンドポイント Web メソッドの結果は、エンドポイント セットを表す各レコードを含むレコードの配列です。各レコードの要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p124">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>

- <span data-ttu-id="bf79e-198">id - エンドポイント セットの不変 ID 番号。</span><span class="sxs-lookup"><span data-stu-id="bf79e-198">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="bf79e-199">serviceArea - Common、Exchange、SharePoint、Skype の一部であるサービス エリア。</span><span class="sxs-lookup"><span data-stu-id="bf79e-199">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="bf79e-p125">urls - エンドポイント セットの URL。DNS レコードの JSON 配列。空白の場合は省略します。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p125">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
- <span data-ttu-id="bf79e-p126">tcpPorts - エンドポイント セットの TCP ポート。すべてのポート要素は、コンマで区切られたポートまたはダッシュ文字 (-) で区切られたポート範囲のリストとです。ポートは、そのカテゴリのエンドポイント セットのすべての IP アドレスとすべての URL に適用されます。空白の場合は省略します。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p126">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
- <span data-ttu-id="bf79e-p127">udpPorts - このエンドポイント セット内の IP アドレス範囲の UDP ポート。空白の場合は省略します。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p127">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
- <span data-ttu-id="bf79e-p128">ips - 一覧表示された TCP ポートまたは UDP ポートに関連付けられたものとして、このエンドポイントセットに関連付けられている IP アドレスの範囲。IP アドレス範囲の JSON 配列。空白の場合は省略します。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p128">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span>
- <span data-ttu-id="bf79e-p129">category - エンドポイント セットの接続のカテゴリ。有効な値は、Optimize、Allow、Default です。エンドポイント データを使用して IP アドレスまたは URL のカテゴリを検索する場合、クエリが複数のカテゴリを返す可能性があります。これにはいくつかの原因が考えられますので、複数のカテゴリが返された場合は、最優先のカテゴリの推奨事項に従ってください。たとえば、エンドポイントが Optimize と Allow の両方に表示される場合は、Optimize の要件に従う必要があります。必須です。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p129">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. If using the endpoint data to search for the category of an IP Address or URL, it is possible that your query may return multiple categories. There are a few reasons why that may happen. In these cases you should follow the recommendations for the highest priority category. For example, if the endpoint appears in both Optimize and Allow, you should follow the requirements for Optimize. Required.</span></span> 
- <span data-ttu-id="bf79e-219">expressRoute - このエンドポイント セットが ExpressRoute を経由してルーティングされるかどうかを示す True または False。</span><span class="sxs-lookup"><span data-stu-id="bf79e-219">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="bf79e-p130">required - Office 365 のサポートを受けるためにこのエンドポイント セットの接続性が必要な場合は True。このエンドポイント セットが省略可能な場合は False。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p130">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span>
- <span data-ttu-id="bf79e-p131">notes - オプションのエンドポイントで、ネットワーク層でエンドポイント セットの IP アドレスまたは URL にアクセスできない場合に、このテキストは見つからない Office 365 の機能について説明します。空白の場合は省略します。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p131">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="bf79e-224">例:</span><span class="sxs-lookup"><span data-stu-id="bf79e-224">Examples:</span></span>

<span data-ttu-id="bf79e-225">例 1 要求 URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bf79e-225">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bf79e-p132">この URI は、すべてのワークロードの Office 365 ワールドワイド インスタンスのすべてのエンドポイントを取得します。出力の抜粋を示す結果の例:</span><span class="sxs-lookup"><span data-stu-id="bf79e-p132">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>

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
...
```

<span data-ttu-id="bf79e-228">この例では、追加のエンドポイント セットは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="bf79e-228">Additional endpoint sets are not included in this example.</span></span>

<span data-ttu-id="bf79e-229">例 2 要求 URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bf79e-229">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bf79e-230">この例では、Exchange Online および依存関係のみの Office 365 ワールドワイド インスタンスのエンドポイントを取得します。</span><span class="sxs-lookup"><span data-stu-id="bf79e-230">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="bf79e-231">例 2 の出力は、結果に SharePoint Online や Skype for Business Online のエンドポイントが含まれていないことを除けば、例 1 と類似しています。</span><span class="sxs-lookup"><span data-stu-id="bf79e-231">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="bf79e-232">変更 Web メソッド</span><span class="sxs-lookup"><span data-stu-id="bf79e-232">Changes web method</span></span>

<span data-ttu-id="bf79e-p133">変更 Web メソッドは、発行された最新の更新を返します。これは通常、IP アドレスの範囲と URL に対する前月の変更です。処理されるべき最も重要な変更は、ファイアウォール アクセス制御リストに IP アドレスを追加できないために新しい URL または IP アドレスが追加された場合、またはプロキシ サーバーのバイパス リストへの URL がネットワーク デバイスの背後で Office 365 ユーザーの停止を引き起こす可能性がある場合です。運用上の要件にかかわらず、_追加_の操作はそうした停止が発生する 30 日前に通知されてから実行されます。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p133">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs. The most critical changes to be processed are when new URLs or IP Addresses are added since failing to add an IP Address to a firewall access control list, or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device. Notwithstanding operational requirements, _Add_ operations are added with 30 days' notice before such an outage would occur.</span></span>

<span data-ttu-id="bf79e-237">変更 Web メソッドのパラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bf79e-237">The parameter for the changes web method is:</span></span>

- <span data-ttu-id="bf79e-p134">**Version** - 必須の URL ルート パラメーター。現在実装しているバージョンであり、そのバージョン以降の変更を確認する場合。形式は _YYYYMMDDNN_ です。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p134">**Version** - Required URL route parameter. The version that you have currently implemented, and you want to see the changes since that version. The format is _YYYYMMDDNN_.</span></span>

<span data-ttu-id="bf79e-p135">変更 Web メソッドの結果はレコードの配列であり、各レコードが特定のバージョンのエンドポイントでの変更を表しています。各レコードの要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p135">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>

- <span data-ttu-id="bf79e-243">id - 変更レコードの不変 ID。</span><span class="sxs-lookup"><span data-stu-id="bf79e-243">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="bf79e-p136">endpointSetId - 変更されたエンドポイント セット レコードの ID。必須です。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p136">endpointSetId - The ID of the endpoint set record that is changed. Required.</span></span>
- <span data-ttu-id="bf79e-p137">disposition - 変更、追加、削除のいずれかを指定し、エンドポイント セット レコードに対して行った変更の内容について説明します。必須です。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p137">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record. Required.</span></span>
- <span data-ttu-id="bf79e-p138">version - 変更が導入された公開エンドポイント セットのバージョン。バージョン番号は _YYYYMMDDNN_ の形式で、複数のバージョンを 1 日のうちに発行する必要がある場合、NN が自然数として増分されます。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p138">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="bf79e-p139">previous - エンドポイント セット上の変更された要素の以前の値を詳述したサブストラクチャ。これは、新しく追加されたエンドポイント セットには含まれません。tcpPorts、udpPorts、ExpressRoute、category、required、notes が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p139">previous - A substructure detailing previous values of changed elements on the endpoint set. This will not be included for newly added endpoint sets. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="bf79e-p140">current - エンドポイント セットの変更要素の更新された値を詳述するサブストラクチャ。tcpPorts、udpPorts、ExpressRoute、category、required、notes が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p140">current - A substructure detailing updated values of changes elements on the endpoint set. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="bf79e-p141">add - エンドポイント セット コレクションに追加する項目の詳細を示すサブストラクチャ。追加がない場合は省略します。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p141">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
  - <span data-ttu-id="bf79e-257">effectiveDate - 追加がサービス内で有効になる時点を示すデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="bf79e-257">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  - <span data-ttu-id="bf79e-258">ips - IP 配列に追加する項目。</span><span class="sxs-lookup"><span data-stu-id="bf79e-258">ips - Items to be added to the ips array.</span></span>
  - <span data-ttu-id="bf79e-259">urls - URL 配列に追加する項目。</span><span class="sxs-lookup"><span data-stu-id="bf79e-259">urls- Items to be added to the urls array.</span></span>
- <span data-ttu-id="bf79e-p142">remove - エンドポイント セットから削除するサブストラクチャの詳細項目。削除がない場合は省略します。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p142">remove - A substructure detailing items to be removed from the endpoint set. Omitted if there are no removals.</span></span>
  - <span data-ttu-id="bf79e-262">ips - IP 配列から削除する項目。</span><span class="sxs-lookup"><span data-stu-id="bf79e-262">ips - Items to be removed from the ips array.</span></span>
  - <span data-ttu-id="bf79e-263">urls - URL 配列から削除する項目。</span><span class="sxs-lookup"><span data-stu-id="bf79e-263">urls- Items to be removed from the urls array.</span></span>

### <a name="examples"></a><span data-ttu-id="bf79e-264">**例:**</span><span class="sxs-lookup"><span data-stu-id="bf79e-264">**Examples:**</span></span>

<span data-ttu-id="bf79e-265">例 1 要求 URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bf79e-265">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bf79e-p143">これにより、Office 365 ワールドワイド サービス インスタンスに対する以前の変更がすべて要求されます。結果の例:</span><span class="sxs-lookup"><span data-stu-id="bf79e-p143">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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
...
```

<span data-ttu-id="bf79e-268">例 2 要求 URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="bf79e-268">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="bf79e-p144">これにより、指定したバージョン以降の Office 365 ワールドワイド インスタンスへの変更が要求されます。この場合、指定されたバージョンは最新のものです。結果の例:</span><span class="sxs-lookup"><span data-stu-id="bf79e-p144">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="bf79e-272">**PowerShell のサンプル スクリプト**</span><span class="sxs-lookup"><span data-stu-id="bf79e-272">**Example PowerShell Script**</span></span>

<span data-ttu-id="bf79e-p145">ここに示した PowerShell スクリプトを実行して、更新されたデータに対して必要なアクションがあるかどうかを確認できます。このスクリプトは、Office 365 ワールドワイド インスタンス エンドポイントのバージョン番号をチェックします。変更がある場合は、エンドポイントをダウンロードし、&quot;Allow&quot; カテゴリと &quot;Optimize&quot; カテゴリのエンドポイントのフィルター処理を行います。また、複数の呼び出しにわたって一意の ClientRequestId を使用し、見つかった最新バージョンを一時ファイルに保存します。バージョンの更新を確認するために、1 時間に 1 回このスクリプトを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p145">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the &quot;Allow&quot; and &quot;Optimize&quot; category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

```powershell
# webservice root URL
$ws = "https://endpoints.office.com"
# path where client ID and latest version number will be stored
$datapath = $Env:TEMP + "\endpoints_clientid_latestversion.txt"
# fetch client ID and version if data file exists; otherwise create new file
if (Test-Path $datapath) {
    $content = Get-Content $datapath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
}
else {
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $datapath
}
# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"

    # write the new version number to the data file
    @($clientRequestId, $version.latest) | Out-File $datapath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
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
    $flatIps = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings have dots while IPv6 strings have colons
        $ip4s = $ips | Where-Object { $_ -like '*.*' }

        $ipCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ipCustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ipCustomObjects
    }
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

## <a name="example-python-script"></a><span data-ttu-id="bf79e-278">**Python のサンプル スクリプト**</span><span class="sxs-lookup"><span data-stu-id="bf79e-278">**Example Python Script**</span></span>

<span data-ttu-id="bf79e-p146">ここに示した Python スクリプトは、Windows 10 で Python 3.6.3 を使用してテストしたもので、これを実行すれば、更新されたデータに対して必要なアクションがあるかどうかを確認できます。このスクリプトは、Office 365 ワールドワイド インスタンス エンドポイントのバージョン番号をチェックします。変更がある場合は、エンドポイントをダウンロードし、_Allow_ カテゴリと _Optimize_ カテゴリのエンドポイントのフィルター処理を行います。また、複数の呼び出しにわたって一意の ClientRequestId を使用し、見つかった最新バージョンを一時ファイルに保存します。バージョンの更新を確認するために、1 時間に 1 回このスクリプトを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p146">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="bf79e-284">**Web サービス インターフェイスのバージョン管理**</span><span class="sxs-lookup"><span data-stu-id="bf79e-284">**Web Service interface versioning**</span></span>

<span data-ttu-id="bf79e-p147">今後、これらの Web サービス メソッドのパラメーターまたは結果の更新が必要になる場合があります。これらの Web サービスの一般的提供バージョンが公開された後、Microsoft では、Web サービスのマテリアル更新の事前通知を提供するために適切な努力を払います。Microsoft は、更新プログラムにより Web サービスを使用しているクライアントが変更を行う必要が生じると判断した場合、新しいバージョンのリリース後、少なくとも 12 か月間、その Web サービスの以前のバージョン (1 つ前のバージョン) を使用できるようにします。その間にアップグレードを行わない顧客は、Web サービスとそのメソッドにアクセスできなくなる場合があります。Web サービス インターフェイスのシグネチャに次の変更が加えられた場合、顧客は Web サービスのクライアントがエラーなしで引き続き動作することを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf79e-p147">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="bf79e-290">古いクライアントによって提供される必要がなく、古いクライアントが受け取る結果に影響を与えない、新しいオプションのパラメーターを既存の Web メソッドに追加する。</span><span class="sxs-lookup"><span data-stu-id="bf79e-290">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="bf79e-291">応答 REST 項目の 1 つに新しい名前付き属性を追加する、または応答 CSV に列を追加する。</span><span class="sxs-lookup"><span data-stu-id="bf79e-291">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="bf79e-292">新しい Web メソッドに、古いクライアントから呼び出されない新しい名前を追加する。</span><span class="sxs-lookup"><span data-stu-id="bf79e-292">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="related-topics"></a><span data-ttu-id="bf79e-293">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf79e-293">Related Topics</span></span>
  
[<span data-ttu-id="bf79e-294">Office 365 の URL と IP アドレスの範囲</span><span class="sxs-lookup"><span data-stu-id="bf79e-294">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="bf79e-295">Office 365 エンドポイントの FAQ</span><span class="sxs-lookup"><span data-stu-id="bf79e-295">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="bf79e-296">Office 365 ネットワーク接続の原則</span><span class="sxs-lookup"><span data-stu-id="bf79e-296">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="bf79e-297">Office 365 のネットワークとパフォーマンスのチューニング</span><span class="sxs-lookup"><span data-stu-id="bf79e-297">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="bf79e-298">Office 365 へのネットワーク接続</span><span class="sxs-lookup"><span data-stu-id="bf79e-298">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
[<span data-ttu-id="bf79e-299">Skype for Business Online でのメディア品質とネットワーク接続のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="bf79e-299">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="bf79e-300">Skype for Business Online 向けのネットワークの最適化</span><span class="sxs-lookup"><span data-stu-id="bf79e-300">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="bf79e-301">ベースラインとパフォーマンス履歴を使用した、Office 365 のパフォーマンスのチューニング</span><span class="sxs-lookup"><span data-stu-id="bf79e-301">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="bf79e-302">Office 365 のパフォーマンスに関するトラブルシューティングの計画</span><span class="sxs-lookup"><span data-stu-id="bf79e-302">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
