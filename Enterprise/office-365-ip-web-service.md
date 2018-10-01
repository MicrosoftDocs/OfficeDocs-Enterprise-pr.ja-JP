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
ms.openlocfilehash: 21222f4c1c2010517bdfe1a425b47c8f4fde8b0e
ms.sourcegitcommit: ca4d3ec34300d7d39f1a42dc6f29a34915de5c87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "23831902"
---
# <a name="office-365-ip-address-and-url-web-service"></a>**Office 365 IP アドレスと URL の Web サービス **

Office 365 のネットワーク トラフィックをよりよく識別し区別するために、新しい Web サービスによって Office 365 エンドポイントが公開されます。これにより、変更を評価し、構成し、また変更の最新の状況を把握することが容易になります。この新しい Web サービスは、現在利用できるダウンロード可能な XML ファイルに代わるものです。XML 形式は、2018 年 10 月 2 日に廃止される予定です。

顧客またはネットワーク境界デバイスのベンダーは、Office 365 の IP アドレスと FQDN エントリ用の新しい REST ベースの Web サービスに対してビルドできます。次の URL を使用して、Web ブラウザーで直接データにアクセスできます。

- Office 365 の URL と IP アドレスの範囲の最新バージョンには、[https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) を使用してください。
- ファイアウォールおよびプロキシ サーバー用の Office 365 の URL と IP アドレスの範囲ページのデータには、[https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) を使用してください。
- この Web サービスが最初に使用できるようになる 2018 年 7 月末以降、最新の変更すべてを取得するには、[https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) を使用してください。

顧客は、この Web サービスを使用して次のことを行えます。

- PowerShell スクリプトを更新して Office 365 エンドポイント データを取得し、ネットワーク デバイスのフォーマットを変更します。
- この情報を使用して、クライアント コンピューターに展開された PAC ファイルを更新します。

ネットワーク境界デバイスのベンダーは、この Web サービスを使用して次のことを行えます。

- デバイス ソフトウェアを作成およびテストして、自動構成の一覧をダウンロードします。
- 現在のバージョンを確認します。
- 最近の変更を取得します。

追加情報については、次を参照してください。

- [Office 365 技術コミュニティ フォーラムでのお知らせブログの投稿](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Web サービスの使用に関する質問のための Office 365 技術コミュニティ フォーラム](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>**共通パラメーター**

次のパラメーターは、すべての Web サービス メソッド共通です。

- **format=CSV | JSON** - クエリ文字列パラメーター。既定では、返されるデータ形式は JSON です。コンマ区切り値 (CSV) 形式でデータを返すには、このオプションのパラメーターを含めます。
- **ClientRequestId** - クエリ文字列パラメーター。クライアントの関連付けのために生成する必要がある GUID。Web サービスを呼び出す各コンピューターに GUID を生成する必要があります。今後、この Web サービスによってブロックされる可能性があるため、次の例に示す GUID は使用しないでください。GUID 形式 _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_、x は 16 進数。GUID を生成するには、[New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell コマンドを使用します。

## <a name="version-web-method"></a>**バージョン Web メソッド**

Microsoft では、Office 365 の IP アドレスと FQDN のエントリを毎月末に更新し、運用またはサポートの要件については不定期に更新します。公開済みの各インスタンスのデータには、バージョン番号が割り当てられます。バージョン Web メソッドを使用すると、Office 365 サービスの各インスタンスの最新のバージョンをポーリングできます。毎日、または最短で 1 時間ごとにバージョンを確認することをお勧めします。新しいバージョンは、毎月の初めに出る予定です。場合によっては、サポート インシデント、セキュリティ、その他の運用要件などのため、月の初め以外にも新しいバージョンが出ることもあります。

バージョン Web メソッドには 1 つのパラメーターがあります。

- **AllVersions=true** - クエリ文字列パラメーター。既定では、返されるバージョンは最新のものです。すべての公開済みバージョンを要求するには、このオプション パラメーターを含めます。
- **Format=JSON** | **CSV** | **RSS** – JSON 形式および CSV 形式に加えて、バージョン Web メソッドは RSS もサポートしています。これを AllVersions=true パラメーターと共に使用して、Outlook や他の RSS リーダーで使用できる RSS フィードを要求できます。
- **Instance** - ルート パラメーター。この省略可能なパラメーターは、バージョンを返すインスタンスを指定します。省略した場合は、すべてのインスタンスが返されます。有効なインスタンスは次のとおりです。Worldwide、China、Germany、USGovDoD、USGovGCCHigh。

バージョン Web メソッドの結果は、単一レコードまたはレコードの配列です。各レコードの要素は次のとおりです。

- instance - Office 365 サービス インスタンスの短い名前。
- latest - 指定されたインスタンスのエンドポイントの最新バージョン。
- versions - 指定されたインスタンスの以前のバージョンすべてのリスト。この要素は、AllVersions パラメーターが true の場合にのみ含まれます。

Microsoft Flow を使用して、IP アドレスや URL への変更のメール通知を受け取れます。「[Microsoft Flow を使用して、Office 365 IP アドレスや URL への変更のメール通知を受け取る](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651)」をご覧ください。

### <a name="examples"></a>**例:**

例 1 要求 URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

この URI は、各 Office 365 サービス インスタンスの最新バージョンを返します。結果の例:

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
これらの URI での ClientRequestID パラメーターの GUID は、一例にすぎません。この Web サービスの URI を試すには、独自の GUID を生成してください。これらの例に示されている GUID は、今後この Web サービスではブロックされる可能性があります。

例 2 要求 URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

この URI は、指定された Office 365 サービス インスタンスの最新バージョンを返します。結果の例:

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}

```

例 3 要求 URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

この URI は CSV 形式で出力を表示します。結果の例:

```csv
instance,latest
Worldwide,2018063000
```

例 4 要求 URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

この URI は、Office 365 ワールドワイド サービス インスタンスに対して発行された以前のバージョンすべてを表示します。結果の例:

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

例 5 RSS フィード URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)

この URI は、各バージョンの変更リストへのリンクを含む、公開されたバージョンの RSS フィードを表示します。結果の例:

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

## <a name="endpoints-web-method"></a>**エンドポイント Web メソッド**

エンドポイント Web メソッドは、Office 365 サービスを構成する IP アドレスの範囲および URL のすべてのレコードを返します。エンドポイント Web メソッドからの最新データをネットワーク デバイスの構成に使用する必要がありますが、追加の事前通知によって公開後 30 日間、データをキャッシュすることができます。エンドポイント Web メソッドのパラメーターは次のとおりです。

- **ServiceAreas** - クエリ文字列パラメーター。サービス エリアのコンマ区切りリスト。有効な項目は、Common、Exchange、SharePoint、Skype です。Common サービス エリア項目は、他のすべてのサービス エリアの前提条件であるため、この Web サービスに常に含まれます。このパラメーターを含めない場合は、すべてのサービス エリアが返されます。
- **TenantName** - クエリ文字列パラメーター。お使いの Office 365 テナント名。この Web サービスでは、指定された名前を、テナント名を含む URL の一部に挿入します。テナント名を指定しない場合、URL のこれらの部分にはワイルドカード文字 (\*) が使用されます。
- **NoIPv6** - クエリ文字列パラメーター。お使いのネットワークで IPv6 を使用しない場合など、出力から IPv6 アドレスを除外するには true に設定します。
- **Instance** - ルート パラメーター。この必須パラメーターは、エンドポイントを返すインスタンスを指定します。有効なインスタンスは次のとおりです。Worldwide、China、Germany、USGovDoD、USGovGCCHigh。

エンドポイント Web メソッドの結果は、エンドポイント セットを表す各レコードを含むレコードの配列です。各レコードの要素は次のとおりです。

- id - エンドポイント セットの不変 ID 番号。
- serviceArea - Common、Exchange、SharePoint、Skype の一部であるサービス エリア。
- urls - エンドポイント セットの URL。DNS レコードの JSON 配列。空白の場合は省略します。
- tcpPorts - エンドポイント セットの TCP ポート。すべてのポート要素は、コンマで区切られたポートまたはダッシュ文字 (-) で区切られたポート範囲のリストとです。ポートは、そのカテゴリのエンドポイント セットのすべての IP アドレスとすべての URL に適用されます。空白の場合は省略します。
- udpPorts - このエンドポイント セット内の IP アドレス範囲の UDP ポート。空白の場合は省略します。
- ips - 一覧表示された TCP ポートまたは UDP ポートに関連付けられたものとして、このエンドポイントセットに関連付けられている IP アドレスの範囲。IP アドレス範囲の JSON 配列。空白の場合は省略します。
- category - エンドポイント セットの接続性カテゴリ。有効な値は、Optimize、Allow、Default。必須です。
- expressRoute - このエンドポイント セットが ExpressRoute を経由してルーティングされるかどうかを示す True または False。
- required - Office 365 のサポートを受けるためにこのエンドポイント セットの接続性が必要な場合は True。このエンドポイント セットが省略可能な場合は False。
- notes - オプションのエンドポイントで、ネットワーク層でエンドポイント セットの IP アドレスまたは URL にアクセスできない場合に、このテキストは見つからない Office 365 の機能について説明します。空白の場合は省略します。

### <a name="examples"></a>例:

例 1 要求 URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

この URI は、すべてのワークロードの Office 365 ワールドワイド インスタンスのすべてのエンドポイントを取得します。出力の抜粋を示す結果の例:

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

この例では、追加のエンドポイント セットは含まれていません。

例 2 要求 URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

この例では、Exchange Online および依存関係のみの Office 365 ワールドワイド インスタンスのエンドポイントを取得します。

例 2 の出力は、結果に SharePoint Online や Skype for Business Online のエンドポイントが含まれていないことを除けば、例 1 と類似しています。

## <a name="changes-web-method"></a>変更 Web メソッド

変更 Web メソッドは、発行された最新の更新を返します。これは通常、IP アドレスの範囲と URL に対する前月の変更です。処理されるべき最も重要な変更は、ファイアウォール アクセス制御リストに IP アドレスを追加できないために新しい URL または IP アドレスが追加された場合、またはプロキシ サーバーのバイパス リストへの URL がネットワーク デバイスの背後で Office 365 ユーザーの停止を引き起こす可能性がある場合です。運用上の要件にかかわらず、_追加_の操作はそうした停止が発生する 30 日前に通知されてから実行されます。

変更 Web メソッドのパラメーターは次のとおりです。

- **Version** - 必須の URL ルート パラメーター。現在実装しているバージョンであり、そのバージョン以降の変更を確認する場合。形式は _YYYYMMDDNN_ です。

変更 Web メソッドの結果はレコードの配列であり、各レコードが特定のバージョンのエンドポイントでの変更を表しています。各レコードの要素は次のとおりです。

- id - 変更レコードの不変 ID。
- endpointSetId - 変更されたエンドポイント セット レコードの ID。必須です。
- disposition - 変更、追加、削除のいずれかを指定し、エンドポイント セット レコードに対して行った変更の内容について説明します。必須です。
- version - 変更が導入された公開エンドポイント セットのバージョン。バージョン番号は _YYYYMMDDNN_ の形式で、複数のバージョンを 1 日のうちに発行する必要がある場合、NN が自然数として増分されます。
- previous - エンドポイント セット上の変更された要素の以前の値を詳述したサブストラクチャ。これは、新しく追加されたエンドポイント セットには含まれません。tcpPorts、udpPorts、ExpressRoute、category、required、notes が含まれます。
- current - エンドポイント セットの変更要素の更新された値を詳述するサブストラクチャ。tcpPorts、udpPorts、ExpressRoute、category、required、notes が含まれます。
- add - エンドポイント セット コレクションに追加する項目の詳細を示すサブストラクチャ。追加がない場合は省略します。
  - effectiveDate - 追加がサービス内で有効になる時点を示すデータを定義します。
  - ips - IP 配列に追加する項目。
  - urls - URL 配列に追加する項目。
- remove - エンドポイント セットから削除するサブストラクチャの詳細項目。削除がない場合は省略します。
  - ips - IP 配列から削除する項目。
  - urls - URL 配列から削除する項目。

### <a name="examples"></a>**例:**

例 1 要求 URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

これにより、Office 365 ワールドワイド サービス インスタンスに対する以前の変更がすべて要求されます。結果の例:

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

例 2 要求 URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

これにより、指定したバージョン以降の Office 365 ワールドワイド インスタンスへの変更が要求されます。この場合、指定されたバージョンは最新のものです。結果の例:

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

## <a name="example-powershell-script"></a>**PowerShell のサンプル スクリプト**

ここに示した PowerShell スクリプトを実行して、更新されたデータに対して必要なアクションがあるかどうかを確認できます。このスクリプトは、Office 365 ワールドワイド インスタンス エンドポイントのバージョン番号をチェックします。変更がある場合は、エンドポイントをダウンロードし、&quot;Allow&quot; カテゴリと &quot;Optimize&quot; カテゴリのエンドポイントのフィルター処理を行います。また、複数の呼び出しにわたって一意の ClientRequestId を使用し、見つかった最新バージョンを一時ファイルに保存します。バージョンの更新を確認するために、1 時間に 1 回このスクリプトを呼び出す必要があります。

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

## <a name="example-python-script"></a>**Python のサンプル スクリプト**

ここに示した Python スクリプトは、Windows 10 で Python 3.6.3 を使用してテストしたもので、これを実行すれば、更新されたデータに対して必要なアクションがあるかどうかを確認できます。このスクリプトは、Office 365 ワールドワイド インスタンス エンドポイントのバージョン番号をチェックします。変更がある場合は、エンドポイントをダウンロードし、_Allow_ カテゴリと _Optimize_ カテゴリのエンドポイントのフィルター処理を行います。また、複数の呼び出しにわたって一意の ClientRequestId を使用し、見つかった最新バージョンを一時ファイルに保存します。バージョンの更新を確認するために、1 時間に 1 回このスクリプトを呼び出す必要があります。

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

## <a name="web-service-interface-versioning"></a>**Web サービス インターフェイスのバージョン管理**

今後、これらの Web サービス メソッドのパラメーターまたは結果の更新が必要になる場合があります。これらの Web サービスの一般的提供バージョンが公開された後、Microsoft では、Web サービスのマテリアル更新の事前通知を提供するために適切な努力を払います。Microsoft は、更新プログラムにより Web サービスを使用しているクライアントが変更を行う必要が生じると判断した場合、新しいバージョンのリリース後、少なくとも 12 か月間、その Web サービスの以前のバージョン (1 つ前のバージョン) を使用できるようにします。その間にアップグレードを行わない顧客は、Web サービスとそのメソッドにアクセスできなくなる場合があります。Web サービス インターフェイスのシグネチャに次の変更が加えられた場合、顧客は Web サービスのクライアントがエラーなしで引き続き動作することを確認する必要があります。

- 古いクライアントによって提供される必要がなく、古いクライアントが受け取る結果に影響を与えない、新しいオプションのパラメーターを既存の Web メソッドに追加する。
- 応答 REST 項目の 1 つに新しい名前付き属性を追加する、または応答 CSV に列を追加する。
- 新しい Web メソッドに、古いクライアントから呼び出されない新しい名前を追加する。

## <a name="related-topics"></a>関連項目
  
[Office 365 の URL と IP アドレスの範囲](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 エンドポイントの FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Office 365 ネットワーク接続の原則](office-365-network-connectivity-principles.md)

[Office 365 のネットワークとパフォーマンスのチューニング](network-planning-and-performance.md)

[Office 365 へのネットワーク接続](network-connectivity.md)
  
[Skype for Business Online でのメディア品質とネットワーク接続のパフォーマンス](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Skype for Business Online 向けのネットワークの最適化](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[ベースラインとパフォーマンス履歴を使用した、Office 365 のパフォーマンスのチューニング](performance-tuning-using-baselines-and-history.md)
  
[Office 365 のパフォーマンスに関するトラブルシューティングの計画](performance-troubleshooting-plan.md)