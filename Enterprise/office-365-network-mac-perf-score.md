---
title: Office 365 ネットワーク評価 (プレビュー)
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
description: Office 365 ネットワーク評価 (プレビュー)
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106373"
---
# <a name="office-365-network-assessment-preview"></a>Office 365 ネットワーク評価 (プレビュー)

Office 365 ネットワーク評価は、顧客のネットワーク接続に対するユーザーの相対的な影響を示します。 Microsoft が所有しているネットワーク接続の影響は、お客様が責任を持つネットワーク設計を最適化できるように、このから除外されています。

これは、Office 365 の主要なワークロードのユーザーの環境に影響する測定値から計算され、0 ~ 100 の範囲のパーセンテージで表示されます。

非常に低いネットワークスコアを設定すると、Office 365 クライアントでは、ユーザーが応答しない、またはその他の問題が発生することがあります。 80% のスコアは、ネットワークのパフォーマンスのために Office 365 のユーザー環境に関してユーザーの苦情を受けないようにする必要があるネットワーク接続を表します。 ネットワーク接続の改良が行われると、このスコアはユーザーの操作に合わせて向上します。

>[!IMPORTANT]
>Microsoft 365 管理センターでのネットワークパフォーマンスの推奨事項、洞察、評価は現在プレビュー状態であり、機能プレビュープログラムに登録されている Office 365 テナントに対してのみ使用できます。

## <a name="exchange-online"></a>Exchange Online

Exchange Online の場合、クライアントマシンから Exchange フロントエンドサーバーへの TCP 遅延が測定されます。 これは、ネットワークが顧客の LAN および WAN を通過する距離の影響を受ける可能性があります。 また、ネットワークの仲介装置やサービスによって影響を受けたり、接続が遅延したり、パケットが再送信されたりする可能性もあります。

## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online の場合、ドキュメントにアクセスするユーザーが使用できるダウンロード速度が測定されます。 このことは、クライアントコンピューターと Microsoft のネットワーク間のネットワーク回線で利用可能な帯域幅の影響を受ける可能性があります。 また、複雑なネットワークデバイスや、混雑している Wi-fi エリアでボトルネックに存在するネットワーク輻輳による影響を受けることもあります。

## <a name="microsoft-teams"></a>Microsoft Teams

Microsoft Teams では、ネットワーク品質は UDP 遅延、UDP ジッタ、および UDP パケット損失として測定されます。 UDP は、Microsoft Teams の通話と電話会議の音声およびビデオメディア接続に使用されます。 これは、より一般的な TCP プロトコルに対して UDP が個別に構成されているため、ネットワークの UDP サポートの接続のギャップに加えて、遅延とダウンロードの速度の場合と同じ要因によって影響を受ける可能性があります。

## <a name="tenant-network-score-and-office-location-network-score"></a>テナントのネットワークスコアとオフィスの場所のネットワークスコア

ネットワークスコアは、オフィスの場所のネットワーク境界の設計を Microsoft のネットワークに測定します。 ネットワーク境界の改善は、各オフィスの場所で行うことをお勧めします。または、ネットワーク接続が集約されている場合は、複数の場所に影響を与える改良が行われることがあります。
ネットワークパフォーマンスの概要ページにある Office 365 テナント全体のネットワークスコアと、その場所の要約ページにある検出された各オフィスの場所の特定のネットワークスコアを示します。

## <a name="network-score-panel"></a>ネットワークスコアパネル

各ネットワークスコアテナントに対して、または特定のオフィスの場所に対して、スコアの詳細が表示されているパネルが表示されます。 このパネルには、測定データを受信したワークロードのみを含む、各コンポーネントワークロードの割合と合計ポイントの両方で、スコアの棒グラフが表示されます。 オフィスの場所のネットワークスコアについても、office の場所と同じ都市にデータを報告したすべての Office 365 クライアントの中央にあるベンチマークを示しています。

パネルのスコア表示には、各コンポーネントのワークロードのスコアが表示されます。

スコア履歴には、過去30日間のスコアとベンチマークが表示されます。

## <a name="related-topics"></a>関連項目

[Microsoft 365 管理センター (プレビュー) でのネットワークパフォーマンスに関する推奨事項](office-365-network-mac-perf-overview.md)

[Office 365 network performance insights (プレビュー)](office-365-network-mac-perf-insights.md)

[M365 管理センターの Office 365 ネットワークオンボードツール (プレビュー)](office-365-network-mac-perf-onboarding-tool.md)
