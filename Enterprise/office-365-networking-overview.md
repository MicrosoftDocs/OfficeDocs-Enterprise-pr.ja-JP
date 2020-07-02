---
title: Microsoft 365 のネットワーク接続の概要
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- NOCSH
description: SaaS サービスでネットワークの最適化が重要な理由、Microsoft 365 ネットワークの目標、および他のワークロードとの間で SaaS が異なるネットワークを必要とする理由について説明します。
ms.openlocfilehash: bc754337eea5e04d6851509114763004b53a19a7
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997827"
---
# <a name="microsoft-365-network-connectivity-overview"></a>Microsoft 365 のネットワーク接続の概要

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

Microsoft 365 は、さまざまなマイクロサービスおよびアプリケーションを使用して生産性とコラボレーションのシナリオを実現する、サービスとして配布される、サービスとしてのソフトウェア (SaaS) クラウドです。 Outlook、Word、PowerPoint などの Microsoft 365 のクライアントコンポーネントは、ユーザーのコンピューター上で実行され、microsoft データセンターで実行される Microsoft 365 の他のコンポーネントに接続します。 Microsoft 365 エンドユーザー環境の品質を決定する最も重要な要素は、microsoft 365 クライアントと Microsoft 365 サービスのフロントドアの間でのネットワークの信頼性と遅延が少ないことです。

この記事では、Microsoft 365 ネットワークの目標について説明します。また、Microsoft 365 ネットワークが一般的なインターネットトラフィックとは異なる方法で最適化する必要がある理由について説明します。

## <a name="microsoft-365-networking-goals"></a>Microsoft 365 ネットワークの目標

Microsoft 365 ネットワークの究極の目標は、クライアントと、最も近い Microsoft 365 エンドポイントとの間で最も制限の少ないアクセスを可能にすることによって、エンドユーザーの環境を最適化することです。 エンドユーザーの環境の品質は、ユーザーが使用しているアプリケーションのパフォーマンスと応答性に直接関係しています。 たとえば、Microsoft Teams では、ユーザーの電話会議、会議、および共有の画面コラボレーションが故障しないように、低遅延を使用しています。 Outlook は、サーバー側のインデックス作成と AI 機能を活用するクイック検索機能に対する強力なネットワーク接続に依存しています。

ネットワーク設計の主な目標は、クライアントコンピューターからのラウンドトリップ時間 (RTT) を Microsoft のグローバルネットワークにまで減らして、microsoft のパブリックネットワークバックボーンである microsoft のパブリックネットワークバックボーン (世界中に分散している Microsoft のすべてのデータセンターを低遅延、高可用性クラウドアプリケーションのエントリポイント) に相互接続することです。 Microsoft グローバルネットワークの詳細については、 [microsoft が高速で信頼性の高いグローバルネットワークを構築する方法](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)を参照してください。

Microsoft 365 ネットワークパフォーマンスの最適化は複雑ではありません。 いくつかの重要な原則に従って、パフォーマンスを最大限に向上させることができます。

- Microsoft 365 ネットワークトラフィックを特定する
- ユーザーが Microsoft 365 に接続する各場所から、インターネットへの Microsoft 365 ネットワークトラフィックのローカルブランチ出口を許可する
- Microsoft 365 トラフィックがプロキシおよびパケット検査デバイスをバイパスすることを許可する

Microsoft 365 ネットワーク接続の原則の詳細については、「 [microsoft 365 ネットワーク接続の原則](office-365-network-connectivity-principles.md)」を参照してください。

## <a name="traditional-network-architectures-and-saas"></a>従来のネットワークアーキテクチャと SaaS

クライアント/サーバーワークロードの従来のネットワークアーキテクチャの原則は、クライアントとエンドポイント間のトラフィックが企業ネットワーク境界の外側に拡張されないという前提に基づいて設計されています。 また、多くのエンタープライズネットワークでは、すべての送信インターネット接続が企業ネットワークを通過し、1つの場所から出口を出します。

従来のネットワークアーキテクチャでは、ネットワーク境界のセキュリティを維持するために、一般的なインターネットトラフィックの待機時間が必要となり、インターネットトラフィックのパフォーマンスを最適化するには、通常、ネットワークの出口ポイントで機器をアップグレードまたはスケールアウトする必要があります。 ただし、このアプローチでは、Microsoft 365 などの SaaS サービスの最適なネットワークパフォーマンスの要件は解決されません。

## <a name="identifying-microsoft-365-network-traffic"></a>Microsoft 365 ネットワークトラフィックを特定する

マイクロソフトは、Microsoft 365 ネットワークトラフィックを識別し、ネットワーク id の管理を簡単にすることを容易にしています。

- ネットワークエンドポイントの新しいカテゴリ。これにより、非常に重要なネットワークトラフィックを、インターネットの遅延の影響を受けないネットワークトラフィックから差別化できます。 最も重要な "最適化" カテゴリには、少数の Url とサポートされている IP アドレスがあります。
- Web サービスのスクリプトの使用、またはデバイスの直接構成と、Microsoft 365 ネットワーク id の変更管理。 変更内容は、web サービス、RSS 形式、または Microsoft Flow テンプレートを使用した電子メールから入手できます。
- Microsoft パートナーとの[Office 365 ネットワークパートナープログラム](https://aka.ms/Office365NPP)。 microsoft の365ネットワーク接続の原則に準拠し、簡単な構成を行うデバイスまたはサービスを提供します。

## <a name="securing-microsoft-365-connections"></a>Microsoft 365 接続をセキュリティで保護する

従来のネットワークセキュリティの目的は、侵入や悪意のある攻略から企業ネットワークの境界を強化することです。 ほとんどのエンタープライズネットワークは、プロキシサーバー、ファイアウォール、SSL ブレークと検査、詳細なパケット検査、データ損失防止システムなどのテクノロジを使用して、インターネットトラフィックにネットワークセキュリティを適用します。 これらのテクノロジは、一般的なインターネット要求に対して重要なリスクを軽減しますが、Microsoft 365 エンドポイントに適用された場合、パフォーマンス、スケーラビリティ、およびエンドユーザー環境の品質を大幅に軽減することができます。

Microsoft 365 は、Microsoft 365 の機能とワークロードに特化して設計された組み込みのセキュリティ機能とデータ使用法に関する組織のニーズを満たすために役に立ちます。 Microsoft 365 のセキュリティとコンプライアンスの詳細については、「 [Office 365 のセキュリティロードマップ](https://docs.microsoft.com/office365/securitycompliance/security-roadmap)」を参照してください。 Microsoft の推奨事項と、Microsoft 365 トラフィックの高度な処理を実行する高度なネットワークソリューションに関するサポートの詳細については、「 [Office 365 でサードパーティ製のネットワークデバイスまたはソリューションを使用](https://support.microsoft.com/help/2690045)する」を参照してください。

## <a name="why-is-microsoft-365-networking-different"></a>Microsoft 365 のネットワークが異なるのはなぜですか?

Microsoft 365 は、エンドポイントセキュリティと暗号化されたネットワーク接続を使用して最適なパフォーマンスが得られるように設計されており、境界のセキュリティの適用を軽減します。 Microsoft 365 データセンターは世界中に配置されており、サービスはさまざまな方法でクライアントを利用可能なサービスエンドポイントに接続するように設計されています。 ユーザーデータと処理は多くの Microsoft データセンターに分散されているため、クライアントコンピューターが接続できる単一のネットワークエンドポイントはありません。 実際、Microsoft 365 テナントのデータとサービスは、エンドユーザーがアクセスする地理的な場所に適応するように Microsoft グローバルネットワークによって動的に最適化されています。

Microsoft 365 トラフィックがパケット検査と集中型出口の対象となる場合、一般的なパフォーマンス上の問題がいくつか作成されます。

- 待機時間が長いと、ビデオやオーディオストリームのパフォーマンスが低下し、データの取得、検索、リアルタイムコラボレーション、予定表の空き時間情報、製品内のコンテンツ、およびその他のサービスの応答が遅くなる可能性があります。
- 中央の場所からの Egressing 接続によって、Microsoft 365 グローバルネットワークの動的ルーティング機能が損なわれ、遅延と往復時間が増加する
- SSL でセキュリティ保護された Microsoft 365 ネットワークトラフィックの暗号化を解除して再暗号化すると、プロトコルエラーが発生し、セキュリティリスクが発生することがあります。

クライアントトラフィックをできるだけ近い場所に移動できるようにすることで、Microsoft 365 エントリポイントへのネットワークパスを短縮することで、Microsoft 365 での接続のパフォーマンスとエンドユーザーの作業を向上させることができます。 また、Microsoft 365 のパフォーマンスと信頼性に関する今後のネットワークアーキテクチャへの変更による影響を軽減するためにも役立ちます。 最適な接続モデルは、これが企業ネットワーク上にあるか、自宅、ホテル、コーヒーショップ、空港などのリモートの場所にあるかにかかわらず、常にユーザーの場所でネットワークを出口として提供することです。 一般的なインターネットトラフィックと WAN ベースの企業ネットワークトラフィックは個別にルーティングされ、ローカル直接出口モデルを使用することはありません。 このローカル直接出口モデルは、次の図で示されています。

![ローカル出口ネットワークアーキテクチャ](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

従来のモデルでの Microsoft 365 ネットワークトラフィックには、ローカル出口アーキテクチャについて次のような利点があります。
  
- ルートの長さを最適化することで、最適な Microsoft 365 のパフォーマンスを提供します。 エンドユーザーの接続は、Microsoft グローバルネットワークの_分散サービスフロントドア_インフラストラクチャによって、最も近い microsoft 365 エントリポイントに動的にルーティングされ、トラフィックは、microsoft の超低遅延高可用性の高可用性の濃いファイバーを介してデータとサービスエンドポイントに内部ルーティングされます。
- プロキシやトラフィック検査デバイスをバイパスして、Microsoft 365 トラフィックのローカル出口を許可することにより、企業ネットワークインフラストラクチャの負荷を軽減します。
- クライアントエンドポイントのセキュリティ機能とクラウドセキュリティ機能を活用して、ネットワークセキュリティの冗長テクノロジを適用せずに、両端の接続をセキュリティで保護します。

> [!NOTE]
> _分散サービスのフロントドア_インフラストラクチャは、地理的に分散した場所を持つ Microsoft グローバルネットワークの可用性と拡張性の高いネットワークエッジです。 エンドユーザー接続が終了し、Microsoft グローバルネットワーク内で効率的にルーティングされます。 Microsoft グローバルネットワークの詳細については、 [microsoft が高速で信頼性の高いグローバルネットワークを構築する方法](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)を参照してください。

Microsoft 365 ネットワーク接続の原則を理解し、適用する方法の詳細については、「 [microsoft 365 ネットワーク接続の原則](office-365-network-connectivity-principles.md)」を参照してください。

## <a name="conclusion"></a>まとめ

Microsoft 365 ネットワークパフォーマンスの最適化は、不必要な障害を排除することになります。 Microsoft 365 接続を信頼されたトラフィックとして扱うことにより、プロキシ帯域幅に関するパケット検査と競合によって遅延が発生するのを防ぐことができます。 クライアントコンピューターと Office 365 エンドポイント間のローカル接続を許可することで、トラフィックを Microsoft グローバルネットワーク経由で動的にルーティングできるようになります。

## <a name="related-topics"></a>関連項目

[Microsoft 365 ネットワーク接続の原則](office-365-network-connectivity-principles.md)

[Office 365 エンドポイントの管理](managing-office-365-endpoints.md)

[Office 365 の URL および IP アドレスの範囲](urls-and-ip-address-ranges.md)

[Office 365 IP アドレスと URL の Web サービス ](office-365-ip-web-service.md)

[Microsoft 365 ネットワーク接続の評価](assessing-network-connectivity.md)

[Microsoft 365 のネットワーク計画とパフォーマンス チューニング](network-planning-and-performance.md)

[ベースラインとパフォーマンス履歴を使用した、Office 365 のパフォーマンスのチューニング](performance-tuning-using-baselines-and-history.md)

[Office 365 のパフォーマンスに関するトラブルシューティングの計画](performance-troubleshooting-plan.md)

[Content Delivery Network](content-delivery-networks.md)

[Microsoft 365 の接続テスト](https://aka.ms/netonboard)

[Microsoft が高速で信頼性の高いグローバルネットワークを構築する方法](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Office 365 ネットワークのブログ](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
