---
title: Microsoft 365 Network Insights (プレビュー)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/31/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 Network Insights (プレビュー)
ms.openlocfilehash: baab4716ace0b15df5878d21987c037372a2754e
ms.sourcegitcommit: 6508db0a839427e1a21b1cde883d828e3c8886c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "43185758"
---
# <a name="microsoft-365-network-insights-preview"></a>Microsoft 365 Network Insights (プレビュー)

**Network insights**は、Microsoft 365 テナントから収集され、テナントの管理ユーザーのみが表示できるライブパフォーマンス指標です。 Insights は、Microsoft 365 管理センターのに表示<https://portal.microsoft.com/adminportal/home#/networkperformance>されます。

Insights は、オフィスの場所のネットワーク境界を設計するのに役立ちます。 各洞察では、ユーザーがテナントにアクセスする地理的な場所ごとに、特定の一般的な問題のパフォーマンス特性に関するライブ詳細が提供されます。

各オフィスの場所には、次の5つの特定のネットワーク洞察が表示されることがあります。

- [Backhauled ネットワークの出口](#backhauled-network-egress)
- [近距離のお客様のためのパフォーマンスの向上](#better-performance-detected-for-customers-near-you)
- [Exchange Online サービスのフロントドアの非最適な使用](#use-of-a-non-optimal-exchange-online-service-front-door)
- [最適ではない SharePoint Online サービスのフロントドアの使用](#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [SharePoint フロントドアからのダウンロード速度が低い](#low-download-speed-from-sharepoint-front-door)

>[!IMPORTANT]
>Network insights、Microsoft 365 Admin Center でのパフォーマンスに関する推奨事項と評価は現在プレビュー状態であり、機能プレビュープログラムに登録されている Microsoft 365 テナントに対してのみ使用できます。

## <a name="backhauled-network-egress"></a>Backhauled ネットワークの出口

Network insights service が、特定のユーザーの場所からネットワークの出口までの距離が500マイル (800 km) よりも大きいことを検出した場合に、この洞察が表示されます。これは、Microsoft 365 トラフィックが共通のインターネットエッジデバイスまたはプロキシに backhauled されていることを示します。

この洞察は、一部の要約ビューで "出口" として短縮されています。

![Backhauled ネットワークの出口](Media/m365-mac-perf/m365-mac-perf-insights-detail-backhauled.png)

### <a name="what-does-this-mean"></a>シナリオ

これは、オフィスの場所とネットワーク出口との間の距離が500マイル (800 km) を超えていることを示しています。 Office の場所は難読化されたクライアントコンピューターの場所で識別され、ネットワークの出口の場所は、逆引き IP アドレスを使用して場所データベースに識別されます。 Windows ロケーションサービスがコンピューターで無効になっている場合は、office の場所が不正確になることがあります。 逆引き IP アドレスデータベースの情報が正確でない場合は、ネットワークの出口の場所が不正確になることがあります。

この洞察の詳細には、オフィスの場所、現在のネットワーク出口の位置、出口位置の関連性、位置と現在の出口ポイント間の距離、条件が最初に検出された日付、および条件が解決された日付が含まれます。

### <a name="what-should-i-do"></a>どうすればよいですか?

この情報については、office の場所へのネットワーク出口をお勧めします。これにより、接続が Microsoft のグローバルネットワークおよび最寄りの Microsoft 365 service フロントドアに最適にルーティングされるようになります。 また、ユーザーのオフィスの場所に対してネットワークを閉じることにより、将来的に、Microsoft がネットワークポイントプレゼンスと Microsoft 365 サービスのフロントドアの両方を展開した場合にもパフォーマンスが向上します。

この問題を解決する方法の詳細については、「 [Office 365 のネットワーク接続の原則](office-365-network-connectivity-principles.md)」の「[ネットワーク接続をローカル](office-365-network-connectivity-principles.md#egress-network-connections-locally)に出力する」を参照してください。

## <a name="better-performance-detected-for-customers-near-you"></a>近距離のお客様のためのパフォーマンスの向上

この洞察は、このオフィスの場所にある組織のユーザーに比べて、メトロエリア内の多数の顧客の方がパフォーマンスが優れていることを network insights service が検出した場合に表示されます。

この洞察は、一部の概要ビューでは "ピア" として短縮されています。

![ネットワークの相対パフォーマンス](Media/m365-mac-perf/m365-mac-perf-insights-detail-cust-near-you.png)

### <a name="what-does-this-mean"></a>シナリオ

この洞察は、このオフィスの場所と同じ都市にある Microsoft 365 の顧客の総合的なパフォーマンスを調査します。 この洞察は、ユーザーの平均待機時間が近隣テナントの平均待機時間を10% 上回る場合に表示されます。

### <a name="what-should-i-do"></a>どうすればよいですか?

この条件には、企業ネットワークまたは ISP の待機時間、ボトルネック、アーキテクチャ設計上の問題など、さまざまな理由が考えられます。 Office ネットワークと現在の Microsoft 365 フロントドア間のルートで、各ホップ間の待機時間を調べます。 詳細については、「 [Office 365 のネットワーク接続の原則](office-365-network-connectivity-principles.md)」を参照してください。

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>Exchange Online サービスのフロントドアの非最適な使用

ネットワークインサイト内のユーザーが、最適な Exchange Online サービスのフロントドアに接続されていないことを検出した場合、この洞察が表示されます。

この洞察は、一部の概要ビューに "ルーティング" として短縮されています。

![非最適なフロントドア](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-exo.png)

### <a name="what-does-this-mean"></a>シナリオ

適切なパフォーマンスを備えた、office の場所の都市からの使用に適した Exchange Online サービスのフロントドアをリストしています。 現在のテストで、この一覧にない Exchange Online サービスのフロントドアの使用が示されている場合は、この推奨事項を呼び出します。

### <a name="what-should-i-do"></a>どうすればよいですか?

Exchange Online サービスのフロントドアを使用していない場合は、企業ネットワークの出口の前にネットワークのバックアウトが原因で、ローカルと直接のネットワーク出口が推奨されることがあります。 また、リモート DNS の再帰リゾルバーサーバーを使用して、DNS の再帰リゾルバーサーバーをネットワークの出口に配置することが推奨される場合もあります。

## <a name="use-of-a-non-optimal-sharepoint-online-service-front-door"></a>最適ではない SharePoint Online サービスのフロントドアの使用

ネットワーク insights サービスが、特定の場所にいるユーザーが最も近い SharePoint Online サービスのフロントドアに接続していないことを検出した場合、この洞察が表示されます。

この洞察は、一部の要約ビューでは "Afd" と略記されています。

![非最適なフロントドア](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-spo.png)

### <a name="what-does-this-mean"></a>シナリオ

テストクライアントが接続している SharePoint Online サービスのフロントドアを特定します。 次に、オフィスの所在地の市区町村に対して、その都市に対して予想される SharePoint Online サービスのフロントドアと比較します。 一致しない場合は、この推奨事項を行います。

### <a name="what-should-i-do"></a>どうすればよいですか?

最適でない SharePoint Online サービスのフロントドアの使用は、企業ネットワークの出口の前にネットワークバックが発生した場合に発生することがあります。これは、ローカルおよび直接ネットワークを出口にすることをお勧めします。 また、リモート DNS の再帰リゾルバーサーバーを使用して、DNS の再帰リゾルバーサーバーをネットワークの出口に配置することが推奨される場合もあります。

## <a name="low-download-speed-from-sharepoint-front-door"></a>SharePoint フロントドアからのダウンロード速度が低い

Network insights service が、特定のオフィスの場所と SharePoint Online の間の帯域幅が 1 MBps 未満であることを検出すると、この洞察が表示されます。

この洞察は、一部の要約ビューで "スループット" と短縮されています。

### <a name="what-does-this-mean"></a>シナリオ

ユーザーが SharePoint Online と OneDrive for business サービスのフロントドアから取得できるダウンロード速度は、1秒あたりのメガバイト数 (MBps) で測定されます。 この値が 1 Mb 未満の場合は、この洞察を提供します。

### <a name="what-should-i-do"></a>どうすればよいですか?

ダウンロード速度を向上させるには、帯域幅を増やす必要がある場合があります。 または、オフィスの場所と SharePoint Online サービスのフロントドアで、ユーザーのコンピューター間にネットワークの輻輳が発生する可能性があります。 これは、congestive 損失とも呼ばれ、十分な帯域幅が利用可能な場合でも、ユーザーが使用できるダウンロード速度を制限します。

## <a name="china-user-optimal-network-egress"></a>中国ユーザーにとって最適なネットワークの出口

この洞察は、中国のユーザーが他の地理的な場所にある Microsoft 365 テナントに接続している場合に表示されます。 

### <a name="what-does-this-mean"></a>シナリオ

組織のプライベート WAN 接続がある場合は、次のいずれかの場所でインターネットへのネットワーク出口を備えた中国のオフィスの場所からネットワーク WAN 回線を構成することをお勧めします。

- 香港特別行政区
- 日本
- 台湾
- 韓国
- シンガポール
- マレーシア

このような場所を超えるユーザーからのインターネット出口はパフォーマンスを低下させ、中国での出口によって、クロスボーダー輻輳が発生して遅延と接続の問題が発生する可能性があります。

### <a name="what-should-i-do"></a>どうすればよいですか?

この洞察に関連するパフォーマンスの問題を軽減する方法の詳細については、「 [Office 365 グローバルテナントパフォーマンスの最適化 (中国ユーザー向け](https://docs.microsoft.com/office365/enterprise/office-365-networking-china))」を参照してください。

## <a name="related-topics"></a>関連項目

[Microsoft 365 管理センター (プレビュー) でのネットワークパフォーマンスに関する推奨事項](office-365-network-mac-perf-overview.md)

[Microsoft 365 ネットワーク評価 (プレビュー)](office-365-network-mac-perf-score.md)

[M365 管理センターの Microsoft 365 ネットワークオンボードツール (プレビュー)](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 ネットワーク接続ロケーションサービス (プレビュー)](office-365-network-mac-location-services.md)
