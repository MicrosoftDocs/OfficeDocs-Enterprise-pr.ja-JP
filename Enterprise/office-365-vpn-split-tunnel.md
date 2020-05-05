---
title: '概要: Office 365 の VPN スプリット トンネリング'
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/3/2020
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
description: Office 365 で VPN スプリット トンネリングを使用して、リモート ユーザーの Office 365 の接続を最適化する方法のガイダンスです。
ms.openlocfilehash: d40a5c3f81baae24253bc8a24d5916c6729e393b
ms.sourcegitcommit: c2f90c022ca323736d9c43929b5681c3f8db0e6f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "43901220"
---
# <a name="optimize-office-365-connectivity-for-remote-users-using-vpn-split-tunneling"></a>VPN スプリット トンネリングを使用してリモート ユーザーの Office 365 の接続を最適化する
<!---
>[!NOTE]
>This topic is part of a set of topics that address Office 365 optimization for remote users.
>- For VPN split tunnel implementation guidance, see [Implementing VPN split tunneling for Office 365](office-365-vpn-implement-split-tunnel.md).
>- For information about optimizing Office 365 worldwide tenant performance for users in China, see [Office 365 performance optimization for China users](office-365-networking-china.md).
-->

リモート ワーカー デバイスを社内ネットワークまたはクラウド インフラストラクチャに接続しているお客様の場合、主要な Office 365 (**Microsoft Teams**、**SharePoint Online**、**Exchange Online**) で _VPN スプリット トンネリング_構成を介してルーティングすることをお勧めします。 これは特に、COVID-19 禍など、大多数の従業員に対して在宅勤務が要求される状況で、従業員の生産性を維持するための最前線の戦略として特に重要になっています。

![スプリット トンネル VPN 構成](media/vpn-split-tunneling/vpn-model-2.png)

_図 1: サービスに直接送信された、定義済み Office 365 例外を使用している VPN スプリット トンネル ソリューション。他のすべてのトラフィックは、接続先に関係なく VPN トンネルを通過します。_

このアプローチの本質は、企業が VPN インフラストラクチャの飽和リスクを軽減し、可能な限り短い時間枠で Office 365 のパフォーマンスを劇的に向上させるためのシンプルな方法を提供することにあります。 VPN クライアントを設定して、最も重要で大量の Office 365 トラフィックが VPN トンネルを迂回できるようにすると、次のようなメリットが得られます。

- Office 365 のユーザー エクスペリエンスに影響を与えるエンタープライズ VPN アーキテクチャにおける、お客様から報告されたパフォーマンスとネットワーク キャパシティの問題の大半の根本的な原因を即座に軽減する
  
  推奨されるソリューションは、トピック「[Office 365 の URL と IP アドレスの範囲](https://aka.ms/o365ips)」で「**最適化**」として分類されている Office 365 のサービス エンドポイントを特に対象としています。 これらのエンドポイントへのトラフィックは待機時間および帯域幅の調整の影響を非常に受けやすいため、VPN トンネルを迂回できるようにすることで、エンドユーザーの操作環境を劇的に向上させ、社内ネットワーク負荷を軽減することができます。 帯域幅やユーザー エクスペリエンスのフットプリントの大部分を構成していない Office 365 接続は、残りのインターネット経由のトラフィックと一緒に VPN トンネルを経由し続けることができます。 詳細については、「[VPN スプリット トンネル戦略](#the-vpn-split-tunnel-strategy)」を参照してください。

- インフラストラクチャやアプリケーションの要件を追加することなく、お客様が迅速に構成、テスト、実装することができる

  VPN プラットフォームやネットワーク アーキテクチャによっては、実装に数時間かかる場合があります。 詳細については、「[VPN スプリット トンネリングの実装](office-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling)」を参照してください。

- インターネットへのトラフィックを含む他の接続のルーティング方法を変更しないことで、お客様の VPN 実装のセキュリティ体制を維持する

  推奨される構成では、VPN トラフィックの例外に対する**最小限の特権**の原則に従い、ユーザーやインフラストラクチャを追加のセキュリティ リスクにさらすことなく、スプリット トンネル VPN を実装することができます。 Office 365 エンドポイントに直接ルーティングされるネットワーク トラフィックは暗号化され、Office クライアント アプリケーション スタックによって整合性が検証され、アプリケーション レベルとネットワーク レベルの両方で強化された Office 365 サービス専用のIPアドレスのみに使用されます。 詳細については、「[セキュリティ専門家と IT による、現代のユニークなリモート ワーク シナリオで最新のセキュリティ管理を実現するための代替的な方法 (Microsoft セキュリティ チーム ブログ)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)」を参照してください。

- ほとんどのエンタープライズ VPN プラットフォームでネイティブにサポートされている

  Microsoft は引き続き商用 VPN ソリューションを製造している業界のパートナーと協力して、上記の推奨事項に沿ったソリューションのための、ターゲットを絞ったガイダンスや構成テンプレートをパートナーが開発できるように支援していきます。 詳細については、「[一般 VPN プラットフォームのHOWTO ガイド](office-365-vpn-implement-split-tunnel.md#howto-guides-for-common-vpn-platforms)」を参照してください。

>[!TIP]
>Office 365 サービス用の文書化された専用 IP 範囲には、スプリット トンネル VPN 構成を集中させることをお勧めします。 特定の VPN クライアント プラットフォームで使用できる FQDN または AppID ベースのスプリット トンネル構成は、Office 365 の主要なシナリオを完全にカバーしていない可能性があります。また、IP ベースの VPN ルーティング ルールと競合する場合があります。 このため、スプリット トンネル VPN の構成に Office 365 FQDN を使用することはお勧めしません。 FQDN 構成の使用は、その他の関連するシナリオ (.pac ファイルのカスタマイズやプロキシ バイパスの実装など) に役立つ場合があります。

完全な実装の詳細については、「[Office 365 向け VPN スプリット トンネリングの実装](office-365-vpn-implement-split-tunnel.md)」を参照してください。

## <a name="the-vpn-split-tunnel-strategy"></a>VPN スプリット トンネリング戦略

従来の社内ネットワークは、大多数のユーザーがそうであるように、ほとんどの重要なデータ、サービス、アプリケーションが構内でホストされ、内部の社内ネットワークに直接接続するという、クラウド以前の環境で安全に動作するように設計されていることが多いです。 したがって、支社は_マルチプロトコル ラベル スイッチング (MPLS)_ ネットワークを介して本社に接続し、オンプレミスのエンドポイントとインターネットの両方にアクセスするリモート ユーザーは、VPN 経由で社内ネットワークに接続する必要があるという要素を中心に、ネットワーク インフラストラクチャが構築されます。 このモデルでは、リモート ユーザーからのすべてのトラフィックが社内ネットワークを通過し、共通の出口ポイントを通ってクラウド サービスにルーティングされます。

![強制 VPN 構成](media/vpn-split-tunneling/vpn-model-1.png)

_図 2: 接続先に関係なく、すべてのトラフィックを社内ネットワークに強制的に戻すリモート ユーザー用の一般 VPN ソリューション_

組織がデータやアプリケーションをクラウドに移行するにつれて、このモデルはすぐに煩雑になり、コストが高くなり、拡張性が低くなり、ネットワークのパフォーマンスやユーザーの効率性に大きな影響を与え、組織が変化するニーズに適応する能力を制限してしまうため、効果が小さくなってきました。 数年前はネットワーク トラフィックの 80% が内部の送信先であったのに、2020 年には 80% 以上のトラフィックが外部のクラウド ベースのリソースに接続していることが、多くの Microsoft のお客様から報告されています。

新型コロナウイルス感染症の危機により、この問題はさらに悪化し、大多数の組織に即時のソリューションが必要になりました。 この危機で必要とされているような 100% リモート ワークのシナリオには、強制 VPN モデルでは十分なスケーラビリティやパフォーマンスが得られないことに、多くのお客様が気付きました。 これらの組織が効率的に運用し続けるには、迅速なソリューションが必要です。

Office 365 サービスについては、Microsoft はこの問題を念頭に置いてサービスに接続するための要件を設計しました。これで、集中的で厳密に制御された比較的静的なサービス エンドポイントのセットを、非常に簡単かつ迅速に最適化して、サービスにアクセスするユーザーに高いパフォーマンスを提供できます。また、VPN インフラストラクチャの負荷を軽減して、それを必要とするトラフィックで使用できるようになります。

Office 365 では、Office 365 に必要なエンドポイントは 3 つのカテゴリ (**最適化**、**許可**、**既定**) に分類されています。 **最適化** のエンドポイントはここでの焦点であり、次の特徴があります。

- Microsoft インフラストラクチャにホストされている Microsoft が所有および管理するエンドポイントである
- Exchange Online、SharePoint Online、Skype for Business Online、Microsoft Teams など、Office 365 のコア ワークロード専用
- IP が提供されている
- 変化率が低く、数も少ないと予想される (現在 20 の IP サブネット)
- 大量のトラフィックや遅延の影響を受けやすい
- 必要なセキュリティ要素をネットワーク上で、インラインではなくサービスで提供することができる
- Office 365 サービスへのトラフィック量の約 70 - 80% を対象としたアカウント

このように範囲が厳密なエンドポイントは強制 VPN トンネルから切り離すことができ、ユーザーのローカル インターフェイスを介して、Office 365 サービスに安全に送信されます。 これは**スプリット トンネリング**と呼ばれます。

DLP、AV 保護、認証、アクセス制御などのセキュリティ要素は、これらのエンドポイントに対して、サービス内のさまざまなレイヤーでより効率的に提供されます。 また、トラフィック量の大部分を VPN ソリューションから迂回させることで、VPN に依存しているビジネス クリティカルなトラフィックのために VPN の容量を解放します。 この新しい動作方法に対処するための、多くの場合長期にわたり費用のかかるアップグレード プログラムを実行する必要もなくなります。

![スプリット トンネル VPN 構成](media/vpn-split-tunneling/vpn-model-2.png)

_図 3: サービスに直接送信された、定義済み Office 365 例外を使用している VPN スプリット トンネル ソリューション。他のすべてのトラフィックは、接続先に関係なく社内ネットワークに強制的に戻されます。_

セキュリティの観点では、Microsoft には、オンプレミスのセキュリティ スタックによるインライン検査で提供されるセキュリティと同様の、またはより強化されたセキュリティを提供する機能が豊富に用意されています。 Microsoft セキュリティ チームのブログ投稿「[セキュリティ専門家と IT による、現代のユニークなリモート ワーク シナリオで最新のセキュリティ管理を実現するための代替的な方法](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)」には、利用可能な機能が明確にまとめられていますので、より詳細なガイダンスを確認できます。 また、Microsoft による VPN スプリット トンネリングの実装については、「[VPN で実行: Microsoft がリモート ワークの従業員の接続を維持している方法](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)」を参照してください。

多くの場合、この実装は数時間のうちに実現できます。本格的なリモート ワークへの移行を急速に進めるにつれ、組織が直面している最も差し迫った問題の 1 つを迅速に解決することができます。 VPN スプリット トンネルの実装については、「[Office 365 向け VPN スプリット トンネリングの実装](office-365-vpn-implement-split-tunnel.md)」を参照してください。

>[!NOTE]
>Microsoft は、少なくとも **2020 年 6 月 30 日**までは、Office 365向けの**最適化**エンドポイントの変更を中断することを約束しており、お客様が当初実装したエンドポイントのホワイトリストを維持するのではなく、他の課題に集中できるようにしています。

## <a name="related-topics"></a>関連項目

[Office 365 向け VPN スプリット トンネリングの実装](office-365-vpn-implement-split-tunnel.md)

[中国ユーザー向けの Office 365 パフォーマンスの最適化](office-365-networking-china.md)

[セキュリティ専門家と IT による、現代のユニークなリモート ワーク シナリオで最新のセキュリティ管理を実現するための代替的な方法 (Microsoft セキュリティ チーム ブログ)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Microsoft での VPN のパフォーマンス強化: Windows 10 の VPN プロファイルを使用して自動接続を許可する](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[VPN で実行: Microsoft がリモート ワークの従業員をどのように接続させているか](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Office 365 ネットワーク接続の原則](office-365-network-connectivity-principles.md)

[Office 365 のネットワーク接続の評価](assessing-network-connectivity.md)

[Microsoft 365 の接続テスト](https://aka.ms/netonboard)
