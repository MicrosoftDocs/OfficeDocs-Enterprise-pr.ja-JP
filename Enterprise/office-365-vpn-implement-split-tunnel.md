---
title: Office 365 向け VPN スプリット トンネリングの実装
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/24/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: Office 365 向けに VPN スプリット トンネリングを実装する方法
ms.openlocfilehash: 0594be194bda222fafa0d00a93e0ee43814cd334
ms.sourcegitcommit: 2c4092128fb12bda0c98b0c5e380d2cd920e7c9b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "43804056"
---
# <a name="implementing-vpn-split-tunneling-for-office-365"></a>Office 365 向け VPN スプリット トンネリングの実装

>[!NOTE]
>これは、リモート ユーザーを対象とした Office 365 の最適化について説明している一連のトピックの中の一つです。
>- リモート ユーザー向けの Office 365 接続を最適化するため、VPN スプリット トンネリングを使用する方法の概要については、「[概要: Office 365 向け VPN スプリット トンネリング](office-365-vpn-split-tunnel.md)」を参照してください。
>- 中国のユーザー向けの Office 365 ワールドワイド テナント パフォーマンスの最適化については、「[中国ユーザー向けの Office 365 パフォーマンスの最適化](office-365-networking-china.md)」を参照してください。

企業は長年にわたり、ユーザーのリモートでの環境を支援するため、VPN を使用してきました。 中心となる作業領域はオンプレミスにありましたが、企業のネットワーク上のデータセンターを通じてルーティングされるリモート クライアントからの VPN は、リモート ユーザーが企業のリソースにアクセスするための主要な方法でした。 接続を保護するため、企業は VPN パスに沿ってネットワーク セキュリティ ソリューションのレイヤを構築します。 これは、内部のインフラストラクチャを保護するとともに、トラフィックを VPN に再ルーティングしてからオンプレミスのインターネット境界に通すことで、外部 Web サイトのモバイル ブラウズを保護するために行われてきました。  VPN、ネットワーク境界、および関連するセキュリティ インフラストラクチャは、多くの場合、決められたトラフィック量に合わせて構築および拡張され、通常は大部分の接続が企業のネットワーク内で開始され、その大部分はトラフィックの内部ネットワーク境界に留まります。

長い間、リモート ユーザー デバイスからのすべての接続がオンプレミス ネットワークにルーティングされる VPN モデル (いわゆる **強制トンネリング**) は、リモート ユーザーの同時接続規模を控えめにし、VPN を横断するトラフィック量を少なく済ませる限りは、ほぼ持続可能でした。  一部の企業は、アプリケーションが企業の境界内からパブリック SaaS クラウドに移行した後でも、VPN 強制トンネリングをそのまま使用し続けてきました。Office365 がその代表的な例です。

分けられていたり、パフォーマンスに敏感なクラウド アプリケーションへの接続に強制トンネリングされた VPN を使用することは、とても適切とは言えませんが、セキュリティの観点から現状を維持するために、そのマイナスの影響も一部の企業では受け入れられてきたのかもしれません。 このシナリオの例となる図を次に示します。

![スプリット トンネル VPN 構成](media/vpn-split-tunneling/vpn-ent-challenge.png)

この問題は年々増加しており、多くの企業がネットワークのトラフィック パターンの大きな変化を訴えています。 以前はオンプレミスにあったトラフィックが、外部のクラウド エンドポイントに接続するようになりました。 Microsoft ユーザーの多くから、以前はネットワーク トラフィックの約 80 ％は内部ソース (上記の図の点線で示した部分) に送られるものだったという報告があります。 2020 年には、主要な作業領域をクラウドに移行したことにより、その割合は約 20 ％以下になりました。この傾向は他の企業でも珍しいことではありません。 クラウドへの移行の旅を進めていくほど、上記のモデルはますます扱いにくく、持続不可能になり、組織がすばやくクラウド ファーストの世界へ足を踏み入れることを妨げます。

世界的な COVID-19 禍により、この問題に対する即時の対応が必要とされています。 IT 企業には、社員の安全を確保するため、大規模な在宅勤務の生産性を援助しなければいけないというこれまでにない要求が生じています。 Microsoft Office 365 は、企業のそういった需要を満たすうってつけの製品ですが、自宅で同時に作業するユーザーの割合が高くなると、Office 365 のトラフィックが大量に生成され、強制トンネリング VPN とオンプレミスのネットワークの境界を介してルーティングされると、急速な飽和を引き起こし、VPN インフラストラクチャが容量不足となります。 現在の状況下では、VPN を使用して Office 365 にアクセスすることは、単なるパフォーマンスの障害になるだけでなく、Office 365、さらに VPN に依存して動作する重要な社内業務に影響を与えます。

Microsoft は、お客様や幅広い業界と長年にわたって緊密に連携し、これらの問題に対して、当社のサービス内から効果的かつ最新のソリューションを提供し、より最適な業務の実現をサポートしています。 Office 365 サービスの「[接続の原則](https://aka.ms/pnc)」は、組織がセキュリティを維持し、接続を制御できるようにしつつ、リモート ユーザーに対して効率的に機能するように設計されています。 このソリューションは、少ない作業量ですばやく対処が可能で、上記で説明した問題に対し大きなプラスの影響を与えます。

リモート ワーカーの接続を最適化するため Microsoft が推進している戦略として、従来のアプローチの問題を迅速に緩和し、簡単な数ステップで高いパフォーマンスを提供することを目指しています。 この段階では、ボトルネックとなる VPN サーバをバイパスする、少数の決められたエンドポイントに対する従来の VPN アプローチを調整します。 同等、あるいはより優れたセキュリティ モデルを異なるレイヤに適用することで、企業ネットワークの出口ですべてのトラフィックを保護する必要がなくなります。 ほとんどの場合、これは数時間以内に効果的に実現でき、要件と時間が許す限りは、他の作業領域に対しても拡張性があります。

## <a name="common-vpn-scenarios"></a>一般的な VPN のシナリオ

以下のリストには、企業での環境で最も一般的な VPN のシナリオを表示しています。 ほとんどの企業は、従来モデル 1 (VPN 強制トンネリング) を運用しています。 当項目では、比較的少ない労力で実現可能で、ネットワークのパフォーマンスとユーザー環境に大きなメリットをもたらす「**モデル 2**」にすばやく安全に移行するご案内を行います。

| **モデル l** | **説明** |
| --- | --- |
| [1. VPN 強制トンネリング](#1-vpn-forced-tunnel) | オンプレミス、インターネット、すべての O365/M365 を含むトラフィックの 100% が VPN トンネルに入る。 |
| [2. いくつかの例外を含む VPN 強制トンネリング](#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) | VPN トンネルが既定で使用され (既定のルート ポイントが VPNに繋がっている)、直接のアクセスが許可される最も重要な除外シナリオはほとんど使用されない。 |
| [3. 広範囲な例外を含む VPN 強制トンネリング](#3-vpn-forced-tunnel-with-broad-exceptions) | VPN トンネルが既定で使用されているものの (既定のルートが VPN を指し示している)、直接アクセスが許可されている例外が広範囲にある (すべての Office 365、すべての Salesforce、すべての Zoom など) |
| [4. VPN 選択的トンネリング](#4-vpn-selective-tunnel) | VPN トンネルは、企業専用サービスにのみ使用される。 既定のルート (インターネットとすべてのインターネット ベースのサービス) は直接アクセスとなる。 |
| [5. VPN なし](#5-no-vpn) | 従来の VPN の代わりに、すべての企業専用サービスが最新のセキュリティ アプローチ (Zscaler ZPA、AAD プロキシ/MCAS など) を通じて公開される。#2の変化型。 |

### <a name="1-vpn-forced-tunnel"></a>1. VPN 強制トンネリング

これは、ほとんどの企業ユーザーにとっては最も一般的なスタート地点になります。 強制 VPN を使用するということは、エンドポイントが企業ネットワーク内に存在するかどうかにかかわらず、100% のトラフィックが企業ネットワークに送信されることになります。 Office 365 や、インターネットの閲覧などの外部 (インターネット) に向かうトラフィックは、プロキシなどのオンプレミスのセキュリティ機器から一度出た後戻ってきます。 現在の時勢により、ユーザーのほぼ 100% がリモートで作業を行うため、このモデルは VPN インフラストラクチャに非常に高い負荷を与え、企業トラフィック、さらに緊急時の効率的な運用へのパフォーマンスを著しく低下させる可能性があります。

![VPN の強制トンネルモデル 1](media/vpn-split-tunneling/vpn-model-1.png)

### <a name="2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions"></a>2. 少数の認可された例外を含む VPN 強制トンネル

このモデルでは、高負荷で遅延の影響を受けやすい、制御され決められた少数のエンドポイントが VPN トンネルをバイパスし、この例ならば Office 365 サービスに直接移動ができます。企業にとってははるかに効率的な運用になります。 これにより、実行されたサービスのパフォーマンスが大幅に向上し、また、VPN インフラストラクチャの負荷が軽減されるため、リソースの競合を抑えて動作させなければいけない要素も実現可能になります。 簡略で決められたアクションをすばやく実行でき、多くのプラスの結果につながるため、当記事ではこのモデルへの移行を支援することに集中しています。

![スプリット トンネリング VPN モデル2](media/vpn-split-tunneling/vpn-model-2.png)

### <a name="3-vpn-forced-tunnel-with-broad-exceptions"></a>3. 広範囲な例外を含む VPN 強制トンネリング

3 番目のモデルでは、決められた小さいエンドポイントのグループを直接送信するのではなく、モデル 2 の範囲を広げ、Office 365、SalesForce などの信頼されたサービスにすべてのトラフィックを直接送信します。 これにより、企業の VPN インフラストラクチャの負荷がさらに軽減され、決められたサービスのパフォーマンスが向上します。 このモデルは、実現性を評価し、実装するためにはより多くの時間がかかる可能性があるため、モデル 2 の実装に成功してから、後日繰り進むことができる段階に入ることになるでしょう。

![スプリット トンネリング VPN モデル3](media/vpn-split-tunneling/vpn-model-3.png)

### <a name="4-vpn-selective-tunnel"></a>4. VPN 選択的トンネリング

このモデルは、企業 IP アドレスを持つトラフィックのみが VPN トンネルに送信され、他の全ての既定のルートはインターネット パスになるため、3番目のモデルの逆になります。 このモデルでは、組織が[ゼロ トラスト](https://www.microsoft.com/security/zero-trust?rtc=1)への道を歩み、安全な実装ができる必要があります。 このモデルや、そこからの変化型は、企業ネットワークからクラウドに移行するサービスが増えるにつれて、既定のモデルとなることが求められてくるでしょう。 Microsoft では、このモデルを内部で使用しています。Microsoft の VPN スプリット トンネリングの実装の詳細については、「[VPN で実行: Microsoft がリモート ワークの従業員をどのように接続させているか](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)」をご覧ください。

![スプリット トンネリング VPN モデル4](media/vpn-split-tunneling/vpn-model-4.png)

### <a name="5-no-vpn"></a>5. VPN なし

モデル番号 2 のより高度なバージョンであり、内部サービスは最新のセキュリティ アプローチまたは Azure AD プロキシ、MCAS、Zscaler ZPA などの SDWAN ソリューションを通じて公開されます。

![スプリット トンネリング VPN モデル5](media/vpn-split-tunneling/vpn-model-5.png)

## <a name="implement-vpn-split-tunneling"></a>スプリット トンネル VPN の実装

当項目では、「[共通 VPN シナリオ](#common-vpn-scenarios)」項目から、お使いの VPN クライアントのアーキテクチャを 「_VPN 強制トンネリング_」から「_少数の認可された例外を含む VPN 強制トンネリング_」、「[VPN スプリット トンネリング モデル #2](#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions)」 に移行するための簡単な手順について説明します。

次の図は、推奨している VPN スプリット トンネリング ソリューションのしくみを示しています。

![スプリット トンネリング VPN ソリューションの詳細](media/vpn-split-tunneling/vpn-split-detail.png)

### <a name="1-identify-the-endpoints-to-optimize"></a>1. 最適化するエンドポイントを決める

「[Office 365 の URL と IP アドレスの範囲](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)」のトピックでは、Microsoft は最適化する必要のある主要なエンドポイントを明確に識別し、それらを「**最適化**」として分類しています。 現在、最適化が必要な URL は 4 つ、IP サブネットは 20 のみです。 この小さいエンドポイントのグループは、Teams のメディアなどの遅延の影響を受けやすいエンドポイントを含め、Office 365 のサービスへのトラフィック量の約70%〜80%を占めます。 これは、元々私たちが特別に注意を払わなければいけないトラフィックであり、従来のネットワーク パスと VPN インフラストラクチャに激しい圧力をかけるトラフィックでもあります。

このカテゴリの URL には、次のような特性があります。

- Microsoft インフラストラクチャにホストされている Microsoft が所有および管理するエンドポイントである
- IP が提供されている
- 変化率が低く、数も少ないと予想される (現在 20 の IP サブネット)
- 帯域幅や遅延の影響を受けやすい
- 必要なセキュリティ要素をネットワーク上で、インラインではなくサービスで提供することができる
- Office 365 サービスへのトラフィック量の約 70 - 80% を対象としたアカウント

>[!NOTE]
>Microsoft は、少なくとも **2020 年 6 月 30 日**までは、Office 365向けの**最適化**エンドポイントの変更を中断することを約束しており、お客様が当初実装したエンドポイントのホワイトリストを維持するのではなく、他の課題に集中できるようにしています。 当記事は、今後の変更を反映して更新されます。

Office 365 エンドポイント、およびその分類と管理方法の詳細については、「[Office 365 エンドポイントを管理する](managing-office-365-endpoints.md)」の記事を参照してください。

#### <a name="optimize-urls"></a>URL を最適化する

現在の最適化 URL は次の表に記載されています。 ほとんどの状況では、エンドポイントがプロキシにではなく直接送信されるように設定されている[ブラウザ PAC ファイル](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic)の URL エンドポイントのみを使用する必要があります。

| URL を最適化する | ポート/プロトコル | 用途 |
| --- | --- | --- |
| <https://outlook.office365.com> | TCP 443 | これは、Outlook が Exchange Online サーバーへの接続に使用する主要なURL の 1 つであり、帯域幅の使用数と接続数が大量になります。 クイック検索、その他のメールボックス 予定表、空き時間の検索、ルールと通知の管理、Exchange オンラインのアーカイブ、送信トレイからのメール送信などといったオンライン上の機能では、ネットワークの遅延を少なくしておく必要があります。 |
| <https://outlook.office.com> | TCP 443 | このURLは Outlook Online Web Access が Exchange Online のサーバーに接続するために使用され、ネットワーク遅延の影響を受けやすくなっています。 SharePoint Online での大きなファイルのアップロードとダウンロードには、特に接続性が必要です。 |
| https://\<tenant\>.sharepoint.com | TCP 443 | これは SharePoint Online の主要な URL で、帯域幅の使用率が高くなっています。 |
| https://\<tenant\>-my.sharepoint.com | TCP 443 | これは OneDrive for Business の標準 URL で、帯域幅の使用率が高く、OneDrive for Business Sync ツールからの接続数が多くなることがあります。 |
| Teams のメディア IP (URL なし) | UDP 3478、3479、3480、および3481 | リレー検出の割り当てとリアルタイムトラフィック (3478)、オーディオ (3479)、ビデオ (3480)、ビデオ画面共有 (3481)。 これらは、Skype for Business および Microsoft Teams メディアのトラフィック (通話、会議など) に使用されるエンドポイントです。 ほとんどのエンドポイントは、Microsoft Teams クライアントが発信を確立するときに提供されます(サービスのリストにある必要な IP 内に含まれています)。 メディアの品質を最適化するには、UDP プロトコルを使用する必要があります。   |

上記の例では、**テナント**をお使いの Office 365 のテナント名に置き換える必要があります。  たとえば、**contoso.onmicrosoft.com** では、_contoso.sharepoint.com_ および_constoso-my.sharepoint.com_ を使用します。

#### <a name="optimize-ip-address-ranges"></a>IP アドレスの範囲を最適化する

これらのエンドポイントが対応する IP 範囲を記述する時は、次のように記述します。 設定を適用するときに更新を確認し、定期的に実行するポリシーを定めておくために、この例のような[スクリプト](https://github.com/microsoft/Office365NetworkTools/tree/master/Scripts/Display%20URL-IPs-Ports%20per%20Category)、[Office 365 IP および URL Web サービス](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)、または[URL/IPページ](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)を使用することを**大変強く**推奨します。

```
104.146.128.0/17
13.107.128.0/22
13.107.136.0/22
13.107.18.10/31
13.107.6.152/31
13.107.64.0/18
131.253.33.215/32
132.245.0.0/16
150.171.32.0/22
150.171.40.0/22
191.234.140.0/22
204.79.197.215/32
23.103.160.0/20
40.104.0.0/15
40.108.128.0/17
40.96.0.0/13
52.104.0.0/14
52.112.0.0/14
52.96.0.0/14
52.120.0.0/14
```

### <a name="2-optimize-access-to-these-endpoints-via-the-vpn"></a>2. VPN を介して、これらのエンドポイントへのアクセスを最適化する

こういった重要なエンドポイントを特定したら、それを VPN トンネルから逸らし、ユーザーのローカル インターネット接続を使用してサービスに直接接続できるようにする必要があります。  これを実現する方法は、使用する VPN 製品とマシンのプラットフォームによって異なりますが、ほとんどの VPN ソリューションでは、この手法を適用するポリシーを簡単に構成することができます。 VPN プラットフォーム固有のスプリット  トンネリングを行う方法については、「[一般 VPN プラットフォームの HOWTO ガイド](#howto-guides-for-common-vpn-platforms)」をご覧ください。

ソリューションを手動でテストしたい場合は、次の PowerShell の例を実行して、ルート テーブルからソリューションをエミュレートできます。 この例では、それぞれの Teams メディア IP サブネットのルートをルート テーブルに追加します。 Teams のメディアの前後でのパフォーマンスをテストをし、指定されたエンドポイントのルートの違いを観察できます。

#### <a name="example-add-teams-media-ip-subnets-into-the-route-table"></a>例: Teams メディア IP サブネットをルート テーブルに追加する

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18" # Teams Media endpoints
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

上記のスクリプトで、 _$intIndex_ は、インターネットに接続されたインターフェースの索引 (PowerShellで **get-netadapter** を実行して検索し、_ifIndex_ の値を探します) であり、 _$gateway_ はそのインターフェースの既定のゲートウェイです (コマンド プロンプトの **ipconfig** か、 **(Get-NetIPConfiguration | Foreach IPv4DefaultGateway).NextHop** を PowerShellで実行し検索します)。

ルートを追加したら、コマンド プロンプトまたは PowerShell で「**印刷のルーティング**」を実行して、ルート テーブルが正しいことを確認できます。  出力には、追加したルートが含まれ、インターフェースのインデックス (この例では _22_) とそのインターフェースのゲートウェイ (この例では _192.168.1.1_) が表示されます。

![印刷結果をルーティングする](media/vpn-split-tunneling/vpn-route-print.png)

「最適化」カテゴリにある**すべての**現在の IP アドレス範囲のルートを追加するには、次のスクリプトの型を使用して、現在の最適化 IPの一連のサブネットの [Office 365 IP および URL Web サービス](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)にクエリを実行し、それをルート テーブルに追加します。

#### <a name="example-add-all-optimize-subnets-into-the-route-table"></a>例: すべての最適化サブネットをルート テーブルに追加する 

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
# Query the web service for IPs in the Optimize category
$ep = Invoke-RestMethod ("https://endpoints.office.com/endpoints/worldwide?clientrequestid=" + ([GUID]::NewGuid()).Guid)
# Output only IPv4 Optimize IPs to $optimizeIps
$destPrefix = $ep | where {$_.category -eq "Optimize"} | Select-Object -ExpandProperty ips | Where-Object { $_ -like '*.*' }
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

うっかり誤ったパラメーターでルートを追加してしまった場合、あるいは単に変更を元に戻したい場合は、次のコマンドを使用して、追加したルートを削除できます。

```powershell
foreach ($prefix in $destPrefix) {Remove-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

<!--- remmed until we add more reliable interface selection logic
#### Example script to add Teams Media subnets to the route table

```powershell
$adapter = get-netadapter | ? {$_.Status -eq "Up"}
$adapterIndex = $adapter.ifIndex
$gateway = (Get-NetIPConfiguration | Foreach IPv4DefaultGateway).NextHop

$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18"
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```
-->

VPN クライアントの設定を行い、**最適化** IP へのトラフィックがこの方法でルーティングされるようにしてください。 これは、Office 365 サービスと接続エンドポイントをできるかぎりユーザーの近くに提供する [Azure フロントドア](https://azure.microsoft.com/blog/azure-front-door-service-is-now-generally-available/)、 Office 365 サービス フロントドアなどのローカルの Microsoft リソースをトラフィックが活用できるようにします。 これにより、ユーザーが世界中のどこにいても非常に高いパフォーマンスを発揮することを可能にし、送信してからわずか数ミリ秒の範囲内で [Microsoft のワールドクラスのグローバル ネットワーク](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)を最大限に活用することがきます。 

## <a name="configuring-and-securing-teams-media-traffic"></a>Teams メディア トラフィックの構成と保護

一部の管理者は、スプリット トンネリング モデルを使用した Teams での発信フローの動作方法と接続のセキュリティを保護する方法に関して詳細な情報が必要かもしれません。

### <a name="configuration"></a>構成

通話と会議の両方で、Teams のメディアに必要な最適化 IP サブネットがルートテーブルに正しく配置されている限り、Teams が _GetBestRoute_ メソッドを呼び出して特定の宛先に使用するインターフェイスを決定すると、上記の Microsoft IP ブロックにある Microsoft の宛先にローカルのインターフェイスが返されます。

一部の VPN クライアント ソフトウェアでは、URL に基づいてルーティング操作が可能です。 ただし、Teams のメディア トラフィックには URL が関連付けられていないため、このトラフィックのルーティングの制御は IP サブネットを使用して行う必要があります。

特定の状況では、Teams クライアントの設定とは関係なく、メディア トラフィックは正しいルートが設定されていても VPN トンネルを通過します。 この状況下では、ファイアウォール規則を用い、Teams IP サブネットまたはポートが VPN を使用するのをブロックすればいいでしょう。

>[!IMPORTANT]
>すべての VPN シナリオで目的の方法を通じて Teams のメディア トラフィックがルーティングされていることを確認するために、次のクライアント バージョン以降は、使用可能なネットワーク パスを検出する方法が改善されているため、これらのいずれかを実行してください。<br>Windows のバージョン番号: **1.3.00.9267**<br>Mac のバージョン番号: **1.3.00.9221**

出力トラフィックは HTTPS を介して実行され、メディア トラフィックよりも遅延の影響を受けにくく、URL/IP データで「**許可**」とマークされているため、必要に応じて VPN クライアントを介して安全にルーティングできます。

### <a name="security"></a>セキュリティ

スプリット トンネリングを避けるべきか考える上でよくある議論の 1 つは、安全性が低いことです。 たとえば、VPN トンネルを通過しないトラフィックは、VPN トンネルに適用される暗号化スキームの恩恵を受けないため、安全性が低下します。

これに対する主な反論は、機密性、認証、および RTP トラフィックに対する再生攻撃の保護を提供するリアルタイム転送プロトコル (RTP) のプロファイルである「_Secure Real-Time Transport Protocol (SRTP)_」によってメディアのトラフィックがすでに暗号化されていることです。  SRTP 自体は、ランダムに生成されたセッションキーに依存します。これは、TLS で保護された出力チャネルを介して交換されます。 これについては、[セキュリティガイド](https://docs.microsoft.com/skypeforbusiness/optimizing-your-network/security-guide-for-skype-for-business-online)で詳しく説明していますが、重要な部分はメディアの暗号化です。

メディア トラフィックは SRTP を使用して暗号化されます。SRTP は、セキュリティ保護された乱数ジェネレータによって生成され、シグナル出力 TLS チャネルで交換されるセッションキーを使用します。 さらに、仲介サーバーとその内部の次ホップの間で双方向に流れるメディアも、SRTP を使用して暗号化されます。

Skype for Business Online は、_Traversal Using Relay around NAT (TURN)_ を介したメディア リレーへの安全なアクセスのためのユーザー名/パスワードを生成します。 メディア リレーは、TLS で保護された SIP チャネル上でユーザー名/パスワードを交換します。 VPN トンネルを使用してクライアントを企業ネットワークに接続する場合でも、トラフィックが企業ネットワークを離れてサービスに到達するときは、SRTP フォームでトラフィックを流す必要があります。

Teams が音声や _Session Traversal Utilities for NAT (STUN)_ 増幅攻撃などのよくあるセキュリティの問題をどのように軽減するかに関する情報は、[こちらの記事](https://docs.microsoft.com/openspecs/office_protocols/ms-ice2/69525351-8c68-4864-b8a6-04bfbc87785c)に記載されています。

リモートワーク環境での最新のセキュリティ管理については、「[セキュリティ専門家と IT による、現代のユニークなリモート ワーク シナリオで最新のセキュリティ管理を実現するための代替的な方法 (Microsoft セキュリティ チーム ブログ)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)」を参照してください。

## <a name="testing"></a>テスト

ポリシーを設定したら、予測どおりに機能していることを確認しましょう。 ローカル インターネット接続を使用するようにパスが正しく設定されているかどうかテストするには、いくつかの方法があります。

- 上記の追跡ルートを含む接続テストを実行する [Microsoft 365 接続テスト](https://aka.ms/netonboard)を実行します。 また、VPN テストをこのツールに追加し、より詳しい情報を観察できるようにします。

- スプリット トンネリングの範囲にあるエンドポイントへ簡単に tracert を行うには、たとえば、次のようなパスを示す必要があります。

  ```powershell
  tracert worldaz.tr.teams.microsoft.com
  ```

  次に、ローカルの ISP を介してこのエンドポイントへのパスが表示されていれば、スプリット トンネリング用に構成した Teams の範囲の IP アドレスに解決されるはずです。

- Wireshark などのツールを使用してネットワーク キャプチャを取得します。  発信中に UDP でフィルタリングすると、 Teams の「**最適化**」範囲の IP アドレスに流れるトラフィックが表示されます。 VPN トンネルがこのトラフィックに使用されている場合、メディア トラフィックは追跡情報に表示されません。

### <a name="additional-support-logs"></a>追加のサポート ログ

トラブル シューティングのためにさらにデータが必要な場合、または Microsoft のサポートが必要な場合は、次の情報を集めておくと、解決策を迅速に見つけることができます。 Microsoft サポートの 「**TSS Windows CMD ベース汎用トラブル シューティング スクリプト ツール セット**」は、関連するログを簡単な方法で収集できるよう手助けしてくれます。 ツールと使用手順は <https://aka.ms/TssTools.> をご参照ください。

## <a name="howto-guides-for-common-vpn-platforms"></a>一般 VPN プラットフォームのHOWTO ガイド

当項目では、この分野の最も一般的なパートナーが Office 365 トラフィックにスプリット トンネリングを実装する詳細なガイドへのリンクを示します。 ガイドは利用可能になり次第、追加する予定です。

- **Windows 10 VPN クライアント**: [ネイティブ Windows 10 VPN クライアントでリモートワーカーのための Office 365 のトラフィックを最適化する](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-office-365-optimization)
- **Cisco Anyconnect**：[ Anyconnect スプリット トンネリングを Office365 向けに最適化する](https://www.cisco.com/c/en/us/support/docs/security/anyconnect-secure-mobility-client/215343-optimize-anyconnect-split-tunnel-for-off.html)
- **Palo Alto GlobalProtect**: [VPN スプリット トンネリングで、 Office 365 のトラフィックを最適化する。アクセスルートは除外](https://live.paloaltonetworks.com/t5/Prisma-Access-Articles/GlobalProtect-Optimizing-Office-365-Traffic/ta-p/319669)
- **F5 ネットワーク BIG-IP APM**: [BIG IP APM を使用している場合に、VPN を介したリモートアクセスで Office 365 のトラフィックを最適化する](https://devcentral.f5.com/s/articles/SSL-VPN-Split-Tunneling-and-Office-365)
- **Citrix Gateway**: [Office365 向けのCitrix Gateway VPN スプリット トンネルの最適化](https://docs.citrix.com/ja-JP/citrix-gateway/13/optimizing-citrix-gateway-vpn-split-tunnel-for-office365.html)
- **Pulse Secure**: [VPN トンネリング: 分割トンネリングを構成して Office365 アプリケーションを除外する方法](https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB44417)

## <a name="faq"></a>FAQ

Microsoft セキュリティ チームは、セキュリティの専門家と IT が今日の特殊なリモートワーク環境で最新のセキュリティ制御を実現できる主要な方法を概説する[記事](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)を公開しました。 さらに、この件に関してお客様からよく寄せられる質問と回答を以下に示します。

### <a name="how-do-i-stop-users-accessing-other-tenants-i-do-not-trust-where-they-could-exfiltrate-data"></a>データを引き出される可能性がある、信頼していない他のテナントにユーザーがアクセスすることを防ぐにはどうすればいいですか？

[「テナントの制限」と呼ばれる機能](https://docs.microsoft.com/azure/active-directory/manage-apps/tenant-restrictions)が回答になります。 認証トラフィックは、量が多くない、もしくは特に遅延の影響を受けにくいため、VPN ソリューションを介して、機能が設定されているオンプレミスのプロキシに送信できます。 信頼されたテナントのアクセス許可リストがこの中に保持され、クライアントが信頼されていないテナントへのトークンを取得しようとした場合、プロキシは要求を拒否します。 信頼されているテナントの場合、ユーザーが適切な資格情報とアクセス権限を持っていると、トークンを取得できます。

したがって、ユーザーは上記の「最適化」のマークがあるエンドポイントに TCP/UDP 接続を確立できますが、問題のテナントにアクセスするための有効なトークンがないと、ログインしてデータにアクセス、または移動することはできません。

### <a name="does-this-model-allow-access-to-consumer-services-such-as-personal-onedrive-accounts"></a>このモデルでは、個人の OneDrive アカウントなど、コンシューマー サービスへのアクセスはできますか？

いいえ、できません。Office 365 のエンドポイントはコンシューマーサービス (例として Onedrive.live.com) と同じではないため、スプリット トンネリングではユーザーはコンシューマー サービスに直接アクセスできません。 コンシューマー エンドポイントへのトラフィックは引き続き VPN トンネルを使用し、既存のポリシーが引き続き適用されます。

### <a name="how-do-i-apply-dlp-and-protect-my-sensitive-data-when-the-traffic-no-longer-flows-through-my-on-premises-solution"></a>トラフィックがオンプレミスのソリューションを通過しなくなったときに、DLP を適用して機密データを保護するにはどうすればよいですか？

機密情報が不注意により漏洩することを防ぐため、Office 365 には豊富な[組み込みツール](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies?view=o365-worldwide)のセットがあります。 Teams と SharePoint の組み込みの [ DLP 機能](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies?view=o365-worldwide)を使用して、不適切に保存または共有された機密情報を検出できます。 リモート ワーク戦略の一部にデバイスの持ち込み (BYOD) ポリシーが含まれているなら、「[条件付きアクセス アプリ コントロール](https://docs.microsoft.com/azure/active-directory/conditional-access/app-based-conditional-access)」を使用して、機密データがユーザーの個人デバイスにダウンロードされるのを防ぐことができます。

### <a name="how-do-i-evaluate-and-maintain-control-of-the-users-authentication-when-they-are-connecting-directly"></a>ユーザーが直接接続を行っている時に、ユーザーの認証制御を評価、維持するにはどうすればよいですか？

Q1 に記載されているテナント制限機能に加えて、「[条件付きアクセス ポリシー](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)」を適用して、認証リクエストのリスクを動的に評価し、適切な対応を行うことができます。 Microsoft は、今後「[ゼロ トラスト モデル](https://www.microsoft.com/security/zero-trust?rtc=1)」を実装することを推奨しており、そこからモバイル、クラウド ファーストの世界で Azure AD の条件付きアクセス ポリシーを使用して制御を維持することができます。 条件付きアクセス ポリシーを使用すると、次のようなさまざまな要因に基づいて、認証要求が成功したかどうかをリアルタイムで判断できます。

- デバイス、デバイスは既知/信頼済み/ドメインに参加しているか？
- IP アドレス – 認証要求は既知の企業 IP アドレスからのものか？ または信頼していない場所からのものか？
- アプリケーション – ユーザーはこのアプリケーションの使用を許可されているか？

次に、承認、MFA のトリガー、またはこれらのポリシーに基づく認証のブロックなどのポリシーをトリガーできます。

### <a name="how-do-i-protect-against-viruses-and-malware"></a>ウイルスやマルウェアからの保護はどうすればいいですか？

同じく、Office 365 は、サービス自体のさまざまな層にある「最適化」のマークのあるエンドポイントを保護します。これは[このドキュメントで概説されています](https://docs.microsoft.com/office365/Enterprise/office-365-malware-and-ransomware-protection)。 前述のように、プロトコルやトラフィックを完全に把握していない可能性のあるデバイスに合わせるよりも、サービス自体にこれらのセキュリティ要素を加えておく方がはるかに効率的です。既定では、SharePoint Online は既知のマルウェアに関して[ファイルのアップロードを自動的にスキャンします](https://docs.microsoft.com/microsoft-365/security/office-365-security/virus-detection-in-spo?view=o365-worldwide)。

上記の Exchange エンドポイントの場合、[Exchange Online Protection](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) および [Office 365 Advanced Threat Protection](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) は、サービスにトラフィックのセキュリティを提供するという優れた機能を果たします。

### <a name="can-i-send-more-than-just-the-optimize-traffic-direct"></a>「最適化」トラフィック以外にも直接送信は行えますか？

「**最適化**」マークの付いたエンドポイントが優先されます。これらのエンドポイントは、下位レベルでの作業に最大の利益をもたらすからです。 ただし、お望みであれば、サービスが機能し、必要に応じて使用できる IP アドレスがエンドポイントに提供されるよう、「許可」マークの付いたエンドポイントが必要になります。

また、さまざまなベンダーが「セキュア Web ゲートウェイ」と呼ばれる、クラウド ベースのプロキシ/セキュリティ ソリューションを提供しており、ここでは一般的な Web ブラウジングのために重要なセキュリティ、制御、企業ポリシー のアプリケーションを提供しています。 これらのソリューションは、可用性、パフォーマンスが高く、ユーザーの近くに準備されていれば、ユーザー近くのクラウド ベースの場所から安全なインターネット アクセスを提供できるため、クラウド ファーストの世界で能力を発揮します。  これにより、中央でのセキュリティ制御を可能にしつつ、VPN /企業ネットワークを介した全体的なブラウジング トラフィックの巻き戻しをする必要がなくなります。

ただし、このソリューションが導入されていても、「最適化」マーク済みの Office 365 トラフィックをサービスに直接送信することを強くお勧めします。

Azure Virtual Network への直接アクセスを許可する方法については、「[Azure VPN ゲートウェイ ポイント ツー サイトを使用したリモート ワーク](https://docs.microsoft.com/azure/vpn-gateway/work-remotely-support)」の記事をご覧ください。

### <a name="why-is-port-80-required-is-traffic-sent-in-the-clear"></a>なぜポート 80 が必要なのですか？ トラフィックは平文で送信されていますか？

ポート 80 はポート 443 セッションへのリダイレクトなどにのみ使用され、顧客データは送信されないか、ポート 80 経由ではアクセスできません。 [こちらの記事](https://docs.microsoft.com/microsoft-365/compliance/encryption?view=o365-worldwide)では、Office 365 の転送中および保存中のデータの暗号化について、[こちらの記事](https://docs.microsoft.com/microsoftteams/microsoft-teams-online-call-flows#types-of-traffic)では、SRTP を使用してTeams のメディア トラフィックを保護する方法について概説しています。

### <a name="does-this-advice-apply-to-users-in-china-using-a-worldwide-instance-of-office-365"></a>この内容は、Office 365 のワールドワイド インスタンスを使用している中国のユーザーにも適用されますか？

**いいえ**、されません。  上記内容で 1 つ注意していただきたいことは、ワールドワイド Office 365 インスタンスに接続している PRC のユーザーです。 この地域ではクロスボーダー ネットワークの混雑が頻繁に発生するため、直接のインターネットの下りのパフォーマンスは変動する可能性があります。 当地域のほとんどのユーザーは、VPN を使用して企業ネットワークにトラフィックを取り込み、許可された MPLS 回線などを利用し、最適化されたパスを介して国外への送信を行っています。 これについては、[中国ユーザー向けのOffice 365 パフォーマンス最適化](office-365-networking-china.md)の記事で詳しく説明しています。

## <a name="related-topics"></a>関連項目

[概要: Office 365 の VPN スプリット トンネリング](office-365-vpn-split-tunnel.md)

[中国ユーザー向けの Office 365 パフォーマンスの最適化](office-365-networking-china.md)

[セキュリティ専門家と IT による、現代のユニークなリモート ワーク シナリオで最新のセキュリティ管理を実現するための代替的な方法 (Microsoft セキュリティ チーム ブログ)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Microsoft での VPN のパフォーマンス強化: Windows 10 の VPN プロファイルを使用して自動接続を許可する](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[VPN で実行: Microsoft がリモート ワークの従業員をどのように接続させているか](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Office 365 ネットワーク接続の原則](office-365-network-connectivity-principles.md)

[Office 365 のネットワーク接続の評価](assessing-network-connectivity.md)

[Office 365 のネットワークとパフォーマンスのチューニング](network-planning-and-performance.md)
