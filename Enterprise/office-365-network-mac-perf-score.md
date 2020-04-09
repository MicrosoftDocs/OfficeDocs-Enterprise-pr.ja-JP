---
title: Microsoft 365 ネットワーク評価 (プレビュー)
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
description: Microsoft 365 ネットワーク評価 (プレビュー)
ms.openlocfilehash: 2ee18f50e841982e8f677964d2e7e57d95a209d8
ms.sourcegitcommit: 6508db0a839427e1a21b1cde883d828e3c8886c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "43185748"
---
# <a name="microsoft-365-network-assessment-preview"></a>Microsoft 365 ネットワーク評価 (プレビュー)

Microsoft 365 管理センターの Microsoft 365 ページへの接続において、**ネットワーク評価**は、多くのネットワークパフォーマンス指標の集合を、1-100 からのポイント値で表された、エンタープライズネットワークの正常性のスナップショットに分割します。 ネットワーク評価は、テナント全体と、ユーザーがテナントに接続する各地理的位置の両方に適用されます。 Microsoft 365 管理者は、企業のネットワーク正常性の gestalt をすばやく把握して、グローバルなオフィスの場所についての詳細レポートにすばやくドリルダウンすることが簡単にできます。

ネットワーク評価ポイントの値は、表示時に有効になっている待機時間、帯域幅、ダウンロード速度、および接続品質指標の平均測定値です。 Microsoft が所有するネットワークのパフォーマンス指標は、これらの測定値から除外され、評価結果が明確になり、企業ネットワークに固有のものであることを確認できます。

![ネットワーク評価の値](Media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

非常に低いネットワーク評価の値は、Microsoft 365 クライアントがテナントに接続したり、応答性の高いユーザー操作を維持したりする際に重大な問題が発生することを示唆していますが、高価値は、継続的なパフォーマンスの問題があることを示しています。 80% の値は、ネットワークパフォーマンスによって Microsoft 365 接続または応答性に関して通常のユーザーからの苦情を受けないようにする必要がある正常な基準を表します。 ネットワーク接続の反復的な改善が行われると、この値はユーザーの操作に合わせて増加します。

>[!IMPORTANT]
>Network insights、Microsoft 365 Admin Center でのパフォーマンスに関する推奨事項と評価は現在プレビュー状態であり、機能プレビュープログラムに登録されている Microsoft 365 テナントに対してのみ使用できます。

## <a name="network-assessment-panel"></a>ネットワーク評価パネル

テナントまたは特定のオフィスの場所にスコープが設定されているかどうかにかかわらず、各ネットワーク評価には、評価に関する詳細情報がパネルに表示されます。 このパネルには、評価の棒グラフがパーセンテージとして表示されます。また、測定データを受け取ったワークロードのみを含む各コンポーネントワークロードの合計ポイントとして評価されます。 オフィスの場所のネットワーク評価では、office の場所と同じ都市にデータを報告したすべての Microsoft 365 クライアントの中央にあるベンチマークも示しています。

![ネットワーク評価の値の例](Media/m365-mac-perf/m365-mac-perf-overview-score.png)

パネルの [**評価] ブレークダウン**には、各コンポーネントのワークロードの評価が表示されます。

**評価履歴**には、過去30日間の評価とベンチマークが表示されます。

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a>テナントのネットワーク評価とオフィスの場所ネットワークの評価

ネットワーク評価は、Microsoft のネットワークへのオフィスの場所のネットワーク境界の設計を測定します。 ネットワーク境界の改善は、各オフィスの場所で行うことをお勧めします。または、ネットワーク接続が集約されている場合は、複数の場所に影響を与える改良が行われることがあります。

ネットワークパフォーマンスの概要ページにある Microsoft 365 テナント全体のネットワーク評価の値と、その場所の要約ページにある検出された各オフィスの場所の特定の値を示します。

## <a name="exchange-online"></a>Exchange Online

Exchange Online の場合、クライアントマシンから Exchange フロントエンドサーバーへの TCP 遅延が測定されます。 これは、ネットワークが顧客の LAN および WAN を通過する距離の影響を受ける可能性があります。 また、ネットワークの仲介装置やサービスによって影響を受けたり、接続が遅延したり、パケットが再送信されたりする可能性もあります。

## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online の場合、ドキュメントにアクセスするユーザーが使用できるダウンロード速度が測定されます。 このことは、クライアントコンピューターと Microsoft のネットワーク間のネットワーク回線で利用可能な帯域幅の影響を受ける可能性があります。 また、複雑なネットワークデバイスや、混雑している Wi-fi エリアでボトルネックに存在するネットワーク輻輳による影響を受けることもあります。

## <a name="microsoft-teams"></a>Microsoft Teams

Microsoft Teams では、ネットワーク品質は UDP 遅延、UDP ジッタ、および UDP パケット損失として測定されます。 UDP は、Microsoft Teams の通話と電話会議の音声およびビデオメディア接続に使用されます。 これは、より一般的な TCP プロトコルに対して UDP が個別に構成されているため、ネットワークの UDP サポートの接続のギャップに加えて、遅延とダウンロードの速度の場合と同じ要因によって影響を受ける可能性があります。

## <a name="related-topics"></a>関連項目

[Microsoft 365 管理センター (プレビュー) でのネットワークパフォーマンスに関する推奨事項](office-365-network-mac-perf-overview.md)

[Microsoft 365 network performance insights (プレビュー)](office-365-network-mac-perf-insights.md)

[M365 管理センターの Microsoft 365 ネットワークオンボードツール (プレビュー)](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 ネットワーク接続ロケーションサービス (プレビュー)](office-365-network-mac-location-services.md)
