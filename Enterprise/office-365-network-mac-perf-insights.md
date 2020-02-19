---
title: Office 365 network performance insights (プレビュー)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Office 365 network performance insights (プレビュー)
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106380"
---
# <a name="office-365-network-performance-insights-preview"></a>Office 365 network performance insights (プレビュー)

Microsoft 365 管理センターのネットワークパフォーマンスページには、office の場所のネットワーク境界を設計するのに役立つ Office 365 ネットワークの洞察が表示されます。 各オフィスの場所に対して表示される可能性のある特定のネットワーク洞察が5つあります。

>[!IMPORTANT]
>Microsoft 365 管理センターでのネットワークパフォーマンスの推奨事項、洞察、評価は現在プレビュー状態であり、機能プレビュープログラムに登録されている Office 365 テナントに対してのみ使用できます。

## <a name="backhauled-network-egress"></a>Backhauled ネットワークの出口

ユーザーの場所からネットワーク出口への距離は500マイル (800 km) を超えるため、パフォーマンスに影響を与えることが予想されます。 ユーザーに近いローカル出口をお勧めします。

これは、オフィスの場所とネットワーク出口との間の距離が500マイルを超えていることを示しています。 Office の場所は難読化されたクライアントコンピューターの場所で識別され、ネットワークの出口の場所は、逆引き IP アドレスを使用して場所データベースに識別されます。 Windows ロケーションサービスがコンピューターで無効になっている場合は、office の場所が不正確になることがあります。 逆引き IP アドレスデータベースの情報が正確でない場合は、ネットワークの出口の場所が不正確になることがあります。

この洞察の詳細には、オフィスの場所、ネットワークの出口の場所、およびそれらの間の距離が含まれます。

この情報については、office の場所へのネットワーク出口をお勧めします。これにより、インターネット上の Microsoft ネットワークと Office 365 service のフロントドアに、接続が最適に Microsoft のネットワークにルーティングされます。 また、ユーザーのオフィスの場所にネットワークを閉じることにより、将来的に、ネットワークポイントのプレゼンスと Office 365 サービスのフロントドアの両方が将来的に展開されるため、パフォーマンスが向上します。

この洞察は、一部の要約ビューで "出口" として短縮されています。

## <a name="better-performance-detected-for-customers-near-you"></a>近距離のお客様のためのパフォーマンスの向上

このオフィスの場所では、組織内のユーザーに比べて、メトロエリア内の顧客数が多いため、パフォーマンスが向上します。

これは、このオフィスの場所と同じ都市にある Office 365 の顧客の総合的なパフォーマンスを見ます。

![ネットワークの相対パフォーマンス](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

同じ都市にある Office 365 のお客様の割合を、パフォーマンスのバケットが向上するように計算します。 この数値が10% を超える場合は、ネットワークの洞察が表示されます。

この洞察は、一部の概要ビューでは "ピア" として短縮されています。

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>Exchange Online サービスのフロントドアの非最適な使用

ユーザーが Office 365 の最適なフロントドアに接続しておらず、パフォーマンスに影響を与えることが予想されます。

適切なパフォーマンスを備えた、office の場所の都市からの使用に適した Exchange Online サービスのフロントドアをリストしています。 現在のテストで、この一覧にない Exchange Online サービスのフロントドアの使用が示されている場合は、この推奨事項を呼び出します。

Exchange Online サービスのフロントドアを使用していない場合は、企業ネットワークの出口の前にネットワークのバックアウトが原因で、ローカルと直接のネットワーク出口が推奨されることがあります。 また、リモート DNS の再帰リゾルバーサーバーを使用して、DNS の再帰リゾルバーサーバーをネットワークの出口に配置することが推奨される場合もあります。

この洞察は、一部の概要ビューに "ルーティング" として短縮されています。

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a>最適でない SharePoint Online サービスのフロントドアの使用

ユーザーが最も近い SharePoint Online サービスのフロントドアに接続していません。 これはパフォーマンスに影響を与えることが予想されます。

テストクライアントが接続している SharePoint Online サービスのフロントドアを特定します。 次に、オフィスの所在地の市区町村に対して、その都市に対して予想される SharePoint Online サービスのフロントドアと比較します。 一致しない場合は、この推奨事項を行います。

この洞察は、一部の要約ビューでは "Afd" と略記されています。

## <a name="low-download-speed-from-sharepoint-front-door"></a>SharePoint フロントドアからのダウンロード速度が低い

Sub 最適なネットワークダウンロード速度が検出され、OneDrive for Business からドキュメントを読み込むのにかかる時間に影響します。

ユーザーが SharePoint Online と OneDrive for business サービスのフロントドアから取得できるダウンロード速度は、1秒あたりのメガバイト数 (MBps) で測定されます。 この値が 1 Mb 未満の場合は、この洞察を提供します。

ユーザーが帯域幅を取得することができるダウンロード速度を向上させるには、帯域幅を増やす必要がある場合があります。 または、オフィスの場所と SharePoint Online サービスのフロントドアで、ユーザーのコンピューター間にネットワークの輻輳が発生する可能性があります。 これは、congestive 損失とも呼ばれ、十分な帯域幅が利用可能な場合でも、ユーザーが使用できるダウンロード速度を制限します。

この洞察は、一部の要約ビューで "スループット" と短縮されています。

## <a name="related-topics"></a>関連項目

[Microsoft 365 管理センター (プレビュー) でのネットワークパフォーマンスに関する推奨事項](office-365-network-mac-perf-overview.md)

[Office 365 ネットワーク評価 (プレビュー)](office-365-network-mac-perf-score.md)

[M365 管理センターの Office 365 ネットワークオンボードツール (プレビュー)](office-365-network-mac-perf-onboarding-tool.md)
