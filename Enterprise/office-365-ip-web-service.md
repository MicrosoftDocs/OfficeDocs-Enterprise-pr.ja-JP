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
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: Office 365 IP アドレスと URL の Web サービスを利用することにより、Office 365 のネットワーク トラフィックの識別と区別がより効率的になり、変更の評価、構成、および最新情報の取得が容易になります。
ms.openlocfilehash: 7a1d882b6bc5e34e3d59cf4bade30a58a1c76d6f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843600"
---
# <a name="office-365-ip-address-and-url-web-service"></a>Office 365 IP アドレスと URL の Web サービス

Office 365 IP アドレスと URL の Web サービスを利用することにより、Office 365 のネットワーク トラフィックの識別と区別がより効率的になり、変更の評価、構成、および最新情報の取得が容易になります。 この REST ベースの Web サービスは、2018 年 10 月 2 日に廃止されたダウンロード可能な XML ファイルに代わるものです。

顧客またはネットワーク境界デバイスのベンダーは、Office 365 の IP アドレスと FQDN エントリ用の Web サービスに対してビルドできます。 次の URL を使用して、Web ブラウザーで直接データにアクセスできます。

- Office 365 の URL と IP アドレスの範囲の最新バージョンには、[https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) を使用してください。
- ファイアウォールおよびプロキシ サーバー用の Office 365 の URL と IP アドレスの範囲ページのデータには、[https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) を使用してください。
- この Web サービスが最初に使用できるようになった 2018 年 7 月以降の最新の変更すべてを取得するには、[https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) を使用してください。

顧客は、この Web サービスを使用して次のことを行えます。

- PowerShell スクリプトを更新して Office 365 エンドポイント データを取得し、ネットワーク デバイスのフォーマットを変更します。
- この情報を使用して、クライアント コンピューターに展開された PAC ファイルを更新します。

ネットワーク境界デバイスのベンダーは、この Web サービスを使用して次のことを行えます。

- デバイス ソフトウェアを作成およびテストして、自動構成の一覧をダウンロードします。
- 現在のバージョンを確認します。
- 最近の変更を取得します。

> [!NOTE]
> Azure ExpressRoute を使って Office 365 に接続する場合は、Azure ExpressRoute でサポートされている Office 365 サービスについて詳しく説明している[Office 365 の Azure ExpressRoute](https://docs.microsoft.com/office365/enterprise/azure-expressroute) をお読みください。 また、Office 365 アプリのネットワーク 要求でインターネット接続が必要なものについて [Office 365 URL と IP アドレス範囲](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) もお読みください。 これは、perimeter セキュリティ デバイスの設定に役立ちます。

詳しくは、次のトピックを参照してください。

- [Office 365 技術コミュニティ フォーラムでのお知らせブログの投稿](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Web サービスの使用に関する質問のための Office 365 技術コミュニティ フォーラム](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>共通パラメーター

これらのパラメーターは、すべての Web サービス メソッドで共通です。

- **format=<JSON | CSV>** — 既定では、返されるデータ形式は JSON です。 コンマ区切り値 (CSV) 形式でデータを返すには、このオプションのパラメーターを使用します。
- **ClientRequestId=\<guid>** — クライアントの関連付けのために必要な GUID です。 Web サービスを呼び出すコンピューターごとに一意の GUID を生成します (このページに含まれるスクリプトでは、GUID が自動的に生成されます)。 次の例に示す GUID は、今後この Web サービスによってブロックされる可能性があるため使用しないでください。 GUID 形式は _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_で、x は 16 進数を表します。

  GUID を作成するには、[New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell コマンドを使用することも、[Online GUID Generator
](https://www.guidgenerator.com/) などのオンライン サービスを利用することもできます。

## <a name="version-web-method"></a>バージョン Web メソッド

Microsoft は、Office 365 の IP アドレスと FQDN エントリを毎月末に更新しています。 サポート インシデント、セキュリティ更新プログラム、またはその他の運用要件により、不定期の更新プログラムが公開されることがあります。

公開済みの各インスタンスのデータには、バージョン番号が割り当てられます。バージョン Web メソッドを使用すると、Office 365 サービスの各インスタンスの最新のバージョンを確認できます。 バージョンの確認を行うのは、1 時間に 1 回以下にすることをお勧めします。

バージョン Web メソッドのパラメーターは次のとおりです。

- **AllVersions=<true | false>** — 初期設定では、返されるバージョンは最新のものです。 Web サービスの最初のリリース以降のすべての公開済みバージョンを要求するには、このパラメーターのオプションを含めます。
- **Format=<JSON | CSV | RSS>** — JSON 形式と CSV 形式に加えて、このバージョン Web メソッドでは RSS もサポートされます。 このパラメーターのオプションは、_AllVersions=true_ パラメーターと共に使用でき、Outlook や その他の RSS リーダーで使用できる RSS フィードを要求できます。
- **Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** — このパラメーターのオプションはバージョンを返すインスタンスを指定します。 省略する場合は、すべてのインスタンスが返されます。 有効なインスタンスは次の通りです。Worldwide、China、Germany、USGovDoD、USGovGCCHigh。

バージョン Web メソッドはレート制限されていないため、429 HTTP 応答コードが返されることはありません。 バージョン Web メソッドへの応答には、1 時間のデータのキャッシュを推奨する cache-control ヘッダーが含まれます。 バージョン Web メソッドからの結果は、単一のレコードの場合も、レコードの配列の場合もあります。 各レコードの要素は、次のとおりです。

- instance — Office 365 サービス インスタンスの短い名前です。
- latest — 指定されたインスタンスのエンドポイントの最新バージョンです。
- versions — 指定されたインスタンスの以前のすべてのバージョンのリストです。 この要素は、_AllVersions_ パラメーターが "true" の場合にのみ含まれます。

### <a name="examples"></a>例:

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

> [!IMPORTANT]
> これらの URI での ClientRequestID パラメーターの GUID は、一例にすぎません。この Web サービスの URI を試すには、独自の GUID を生成してください。これらの例に示されている GUID は、今後この Web サービスではブロックされる可能性があります。

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
<rss version="2.0" xmlns:a10="https://www.w3.org/2005/Atom">
<channel>
<link>https://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
```

## <a name="endpoints-web-method"></a>エンドポイント web メソッド

エンドポイント web メソッドは、Office 365 サービスを構成する IP アドレスの範囲および URL のすべてのレコードを返します。 ネットワーク デバイスの構成には、常にエンドポイント Web メソッドからの最新データを使用する必要があります。 Microsoft では、お客様が時間の余裕を持ってアクセス制御リストおよびプロキシ サーバーのバイパス リストを更新できるよう、新規追加を公開する 30 日前に事前通知を提供しています。 エンドポイント Web メソッドをもう一度呼び出す場合は、バージョン Web メソッドにより新しいデータのバージョンが使用可能なことが示された場合にのみ行うことをお勧めします。

エンドポイント Web メソッドのパラメーターは次のとおりです。

- **ServiceAreas=<Common | Exchange | SharePoint | Skype>** — サービス エリアのコンマ区切リストです。 有効な項目は、_Common_、_Exchange_、_SharePoint_、および_Skype_です。 _Common_ サービス エリア項目はその他のすべてのサービス エリアの前提条件であるため、Web サービスに常に含まれます。 このパラメーターを含めない場合は、すべてのサービス エリアが返されます。
- **TenantName=<tenant_name>** — Office 365 のテナント名です。 この web サービスでは、指定した名前を テナント名を含む URL の一部に挿入します。 テナント名を指定しない場合、URL のそれらの部分にワイルドカード文字が使用されます (\*)。
- **NoIPv6=<true | false>** — お使いのネットワークで IPv6 を使用しない場合は、値を _true_ に設定して出力から IPv6 アドレスを除外します。
- **Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** — このパラメーターはエンドポイントを返すインスタンスを指定します。 有効なインスタンスは、_Worldwide_、_China_、_Germany_、_USGovDoD_、_USGovGCCHigh_ です。

同じクライアント IP アドレスからのエンドポイント Web メソッドの呼び出し回数が多すぎる場合、 HTTP Response Code _429 (要求が多すぎます)_ の応答コードが返される場合があります。 この応答コードを受け取った場合、リクエストを再度行うまでに 1 時間待つか、リクエスト用に新しい GUID を生成します。 一般的なベスト プラクティスとして、バージョン Web メソッドで新しいバージョンのデータが使用可能だと示された場合にのみ、エンドポイント Web メソッドを呼び出すようにします。

エンドポイント Web メソッドの結果は、各レコードが特定のエンドポイント セットを表すレコードの配列です。 各レコードの要素は次のとおりです。

- id — エンドポイント セットの不変 ID 番号です。
- serviceArea — _Common_、_Exchange_、_SharePoint_、または _Skype_ の一部であるサービス エリアのことです。
- urls — エンドポイント セットの URL です。 DNS レコードの JSON 配列です。 空白の場合は省略します。
- tcpPorts — エンドポイント セットの TCP ポートです。 すべてのポート要素は、ポートのカンマ区切りのリストまたはダッシュ文字 (-) で区切られたポート範囲により書式設定されています。 特定のカテゴリのポートは、すべての IP アドレスおよびエンド ポイント内のすべての URL に適用されます。 空白の場合は省略します。
- udpPorts — このエンドポイント セット内の IP アドレス範囲の UDP ポートです。 空白の場合は省略します。
- ips — 一覧表示された TCP ポートまたは UDP ポートに関連付けられたものとして、このエンドポイント セットに関連付けられている IP アドレスの範囲です。 IP アドレス範囲の JSON 配列です。 空白の場合は省略します。
- category — エンドポイント セットの接続性カテゴリです。 有効な値は、_Optimize_、_Allow_、および _Default_ です。 特定の IP アドレスまたは URL についてエンドポイント Web メソッドの出力を検索する場合、クエリで複数のカテゴリが返される場合があります。 最優先のカテゴリの推奨事項に従ってください。 たとえば、エンドポイントが _Optimize_ と _Allow_ の両方に表示される場合は、_Optimize_ の要件に従う必要があります。 必須です。
- expressRoute — このエンドポイント セットが ExpressRoute を経由してルーティングされる場合は _True_ で、されない場合は _False_ です。
- required — Office 365 のサポートを受けるためにこのエンドポイント セットの接続性が必要な場合は _True_ です。 このエンドポイント セットが省略可能な場合は _False_ です。
- notes — このテキストは、省略可能のエンドポイントについて、ネットワーク層でこのエンドポイント セットの IP アドレスまたは URL にアクセスできない場合に利用できなくなる Office 365 の機能について説明します。 空白の場合は省略します。

### <a name="examples"></a>例:

例 1 要求 URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

この URI は、すべてのワークロードについて Office 365 ワールドワイド インスタンスのすべてのエンドポイントを取得します。 出力の抜粋を示す結果の例:

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

この例では、要求の完全な出力に他のエンドポイント セットが含まれる点に注意してください。

例 2 要求 URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

この例では、Exchange Online および依存関係のみの Office 365 ワールドワイド インスタンスのエンドポイントを取得します。

例 2 の出力は例 1 と似ていますが、結果に SharePoint Online または Skype for Business Online のエンドポイントが含まれない点が異なります。

## <a name="changes-web-method"></a>変更 Web メソッド

変更 Web メソッドは、発行された最新の更新を返します。これは通常、IP アドレスの範囲と URL に対する前月の変更です。

エンドポイント データへの最も重要な変更は、新しい URL と IP アドレスです。 IP アドレスがファイアウォール アクセス制御リストに追加されなかったり、URL がプロキシ サーバーのバイパス リストに追加されなかったりした場合、そのネットワークデバイスの背後にいる Office 365 ユーザーのサービスが停止する場合があります。 運用上の要件にかかわらず、お客様が時間の余裕を持ってアクセス制御リストおよびプロキシ サーバーのバイパス リストを更新できるよう、新しいエンドポイントは、エンドポイントの使用がプロビジョニングされる日の 30 日前に Web サービスに公開されます。

変更 Web メソッドのパラメーターは次のとおりです。

- **Version=\<YYYYMMDDNN>** — 必要な URL ルート パラメーターです。 この値は、現在実装しているバージョンです。 この web サービスはそのバージョン以降の変更を返します。 形式は _YYYYMMDDNN_ で、_NN_ は 1 日に発行する必要がある複数のバージョンがある場合に増加する自然数で、_00_ は特定日における最初の更新を表します。 Web サービスでは、この_バージョン_のパラメーターが正確に 10 桁であることが要求されます。

エンドポイント Web メソッドと同様に、変更 Web メソッドはレート制限されています。 429 HTTP の応答コードを受け取った場合、リクエストを再度行うまでに 1 時間待つか、リクエスト用に新しい GUID を生成します。

変更 Web メソッドの結果は、各レコードが特定のバージョンのエンドポイントでの変更を表すレコードの配列です。 各レコードの要素は次のとおりです。

- id — 変更レコードの不変 ID です。
- endpointSetId — 変更されたエンドポイント セット レコードの ID です。
- disposition — エンドポイント セット レコードに対して行われた変更について説明します。 値は、_change_、_add_、または _remove_ です。
- impact — すべての変更がどの環境に対しても同じ重要度を持つわけではありません。 この要素は、予想されるこの変更による エンタープライズ ネットワーク境界環境に対する影響を示します。 この属性は、バージョン **2018112800** 以降の変更レコードにのみ含まれます。
   impact のオプションは次のとおりです。— AddedIp – Office 365 に IP アドレスが追加され、間もなくサービスで有効になります。 これは、ファイアウォールまたは他のレイヤー 3 ネットワーク境界デバイスに加える必要のある変更を表します。 これが追加されないままその使用が開始された場合、サービスが停止する可能性があります。
  — AddedUrl – Office 365 に URL が追加され、間もなくサービスで有効になります。 これは、プロキシ サーバーまたは URL 解析ネットワーク境界デバイスに加える必要がある変更を表します。 この URL が追加されないままその使用が開始された場合、サービスが停止する可能性があります。
  — AddedIpAndUrl — IP アドレスと URL の両方が追加されました。 これは、ファイアウォールのレイヤー 3 デバイス、プロキシ サーバー、または URL 解析デバイスのいずれかに加える必要がある変更を表します。 この IP/URL のペアの使用開始前にこれを追加しない場合、サービスが停止する可能性があります。
  — RemovedIpOrUrl – 少なくとも 1 つの IP アドレスまたは URL が Office 365 から削除されました。 境界デバイスからネットワークエンドポイントを削除します。ただし、これを行うための期限はありません。
  — ChangedIsExpressRoute – ExpressRoute サポート属性が変更されました。 ExpressRoute を使用する場合は、構成に応じてアクションを実行する必要がある場合があります。
  — MovedIpOrUrl – このエンドポイント セットと他のエンドポイント セットの間で、IP アドレスまたは URL を移動しました。 通常、必要なアクションはありません。
  — RemovedDuplicateIpOrUrl – 重複する IP アドレスまたは URL を削除しましたが、引き続き Office 365 用に公開されています。 通常、必要なアクションはありません。
  — OtherNonPriorityChanges – メモ フィールドなど、その他のすべてのオプションよりも重要度が低いものを変更しました。
- version — 変更が導入された公開済みのエンドポイント セットのバージョンです。 バージョン番号の形式は _YYYYMMDDNN_ で、_NN_ は 1 日に発行する必要があるバージョンが複数ある場合に増加する自然数です。
- previous — エンドポイント セットで変更された要素の以前の値を詳述するサブストラクチャです。 これは、新しく追加されたエンドポイント セットには含まれません。 _ExpressRoute_、_serviceArea_、_category_、_required_、_tcpPorts_、_udpPorts_、および _notes_ が含まれます。
- current — エンドポイント セットで変更された要素の変更後の値を詳述するサブストラクチャです。 _ExpressRoute_、_serviceArea_、_category_、_required_、_tcpPorts_、_udpPorts_、および _notes_が含まれます。
- add — エンドポイント セット コレクションに追加する項目の詳細を示すサブストラクチャです。 追加がない場合は省略します。
  — effectiveDate — 追加がサービス内で有効になる時点を示すデータを定義します。
  — ips — _ips_ 配列に追加する項目です。
  — urls- _urls_ 配列に追加する項目です。
- remove — エンドポイント セットから削除するサブストラクチャの詳細項目です。 削除するものがない場合は省略します。
  — ips — _ips_ 配列から削除する項目です。
  — urls- _urls_ 配列から削除する項目です。

### <a name="examples"></a>例:

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

## <a name="example-powershell-script"></a>PowerShell スクリプト

更新されたデータに対して行う必要があるアクションがあるかどうかを確認するには、この PowerShell スクリプトを実行します。 このスクリプトは、バージョンの更新を確認するために、スケジュールされたタスクとして実行できます。 Web サービスへ過剰な負荷を与えないために、スクリプトは 1 時間に 1 回以上実行しないようにします。

このスクリプトでは、次のことが行われます。

- Web サービスの REST API を呼び出して、現在の Office 365 ワールドワイド インスタンスのエンドポイントのバージョン番号を確認します。
- _$Env:TEMP\O365_endpoints_latestversion.txt_ で現在のバージョンのファイルを確認します。 通常、グローバル変数 **$Env:TEMP** のパスは、_C:\Users\\<ユーザー名\>\AppData\Local\Temp_ です。
- このスクリプトの実行が今回が初めての場合、スクリプトは現在のバージョンとすべての現在の IP アドレスおよび URL を返し、エンドポイント バージョンを _$Env:TEMP\O365_endpoints_latestversion.txt_ に書き込み、エンドポイント データ出力をファイル _$Env:TEMP\O365_endpoints_data.txt_ に書き込みます。 出力ファイルのパスまたは名前を変更するには、次の行を編集します。

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- これ以降のスクリプト実行では、最新の Web サービス バージョンが _O365_endpoints_latestversion.txt_ ファイルのバージョンと同じである場合、スクリプトは何も変更せずに終了します。
- 最新の Web サービスのバージョンが _O365_endpoints_latestversion.txt_ ファイル内でのバージョンよりも新しい場合、スクリプトはエンドポイントを返し、**Allow** カテゴリおよび **Optimize** カテゴリのエンドポイントをフィルタリングし、_O365_endpoints_latestversion.txt_ ファイル内でバージョンを更新し、更新されたデータを _O365_endpoints_data.txt_ ファイルに書き込みます。

スクリプトは、スクリプトが実行されるコンピューター用に一意の _ClientRequestId_ を生成し、複数の呼び出しでこの ID を再利用します。 この ID は _O365_endpoints_latestversion.txt_ ファイルに格納されます。

### <a name="to-run-the-powershell-script"></a>PowerShell スクリプトを実行するには

1. スクリプトをコピーし、_Get-O365WebServiceUpdates.ps1_ としてローカルのハード ドライブまたはスクリプトの場所に保存します。
1. お好みのスクリプト エディター (PowerShell ISE や VS Code など) でスクリプトを実行します。または、次のコマンドを使用して PowerShell コンソールからスクリプトを実行します。

    ``` powershell
   powershell.exe -file <path>\Get-O365WebServiceUpdates.ps1
    ```

    スクリプトに渡すパラメーターはありません。

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

## <a name="example-python-script"></a>Python スクリプト

ここに示した Python スクリプトは、Windows 10 で Python 3.6.3 を使用してテストしたもので、これを実行すれば、更新されたデータに対して必要なアクションがあるかどうかを確認できます。このスクリプトは、Office 365 ワールドワイド インスタンス エンドポイントのバージョン番号をチェックします。変更がある場合は、エンドポイントをダウンロードし、_Allow_ カテゴリと _Optimize_ カテゴリのエンドポイントのフィルター処理を行います。また、複数の呼び出しにわたって一意の ClientRequestId を使用し、見つかった最新バージョンを一時ファイルに保存します。バージョンの更新を確認するために、1 時間に 1 回このスクリプトを呼び出す必要があります。

```python
import json
import tempfile
from pathlib import Path
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
datapath = Path(tempfile.gettempdir() + '/endpoints_clientid_latestversion.txt')
# fetch client ID and version if data exists; otherwise create new file
if datapath.exists():
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

## <a name="web-service-interface-versioning"></a>Web サービス インターフェース バージョニング

今後、これらの Web サービス メソッドのパラメーターまたは結果の更新が必要になる場合があります。 これらの Web サービスの一般的提供バージョンが公開された後、Microsoft では、Web サービスの重要な更新について事前通知を提供するよう合理的な範囲で努めます。 Microsoft は、更新プログラムにより Web サービスを使用しているクライアントが変更を行う必要が生じると判断した場合、新しいバージョンのリリース後、少なくとも 12 か月間、その Web サービスの以前のバージョン (1 つ前のバージョン) を使用できるようにします。 お客様がその間にアップグレードを行わない場合、Web サービスとそのメソッドにアクセスできなくなる場合があります。 Web サービス インターフェイスのシグネチャに次の変更が加えられた場合、お客様は Web サービスのクライアントがエラーが発生することなく引き続き動作することを確認する必要があります。

- 古いクライアントによって提供される必要がなく、古いクライアントが受け取る結果に影響を与えない、新しいオプションのパラメーターを既存の Web メソッドに追加する。
- 応答 REST 項目の 1 つに新しい名前付き属性を追加する、または応答 CSV に列を追加する。
- 新しい Web メソッドに、古いクライアントから呼び出されない新しい名前を追加する。

## <a name="update-notifications"></a>更新の通知

IP アドレスと URL の変更が Web サービスに発行された際にメール通知を受け取るには、いくつかの方法があります。

- Microsoft Flow ソリューションを使用する方法については、「[Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs (Microsoft Flow を使用して Office 365 IP アドレスと URL への変更の通知メールを受け取る)](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651)」を参照してください。
- ARM テンプレートを使用して Azure Logic App を展開する場合は、「[Office 365 Update Notification (v1.1) (Office 365 更新通知 (v 1.1))](https://aka.ms/ipurlws-updates-template)」を参照してください。
- PowerShell を使用して独自の通知スクリプトを作成するには、「[Send-MailMessage](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage)」 を参照してください。

## <a name="exporting-a-proxy-pac-file"></a>プロキシ PAC ファイルのエクスポート

[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) は Office 365 の IP アドレスと URL Web サービスから最新のネットワーク エンドポイントを読み取る PowerShell スクリプトで、サンプルの PAC ファイルを作成します。 Get-PacFile の使用に関する詳細情報については、「[重要な Office 365 トラフィックの直接ルーティング用 PAC ファイルの使用](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic)」を参照してください。

## <a name="related-topics"></a>関連項目
  
[Office 365 の URL と IP アドレスの範囲](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[Office 365 エンドポイントの管理](managing-office-365-endpoints.md)
  
[Office 365 エンドポイントの FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Office 365 ネットワーク接続の原則](office-365-network-connectivity-principles.md)

[Office 365 のネットワークとパフォーマンスのチューニング](network-planning-and-performance.md)

[Office 365 ネットワーク接続の評価](assessing-network-connectivity.md)
  
[Skype for Business Online でのメディア品質とネットワーク接続のパフォーマンス](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Skype for Business Online 向けのネットワークの最適化](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[ベースラインとパフォーマンス履歴を使用した、Office 365 のパフォーマンスのチューニング](performance-tuning-using-baselines-and-history.md)
  
[Office 365 のパフォーマンスに関するトラブルシューティングの計画](performance-troubleshooting-plan.md)
