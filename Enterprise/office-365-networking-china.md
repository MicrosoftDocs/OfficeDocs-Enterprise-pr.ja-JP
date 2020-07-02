---
title: 中国ユーザー向けの Microsoft 365 グローバルテナントのパフォーマンスの最適化
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
search.appverid: MET150
f1.keywords:
- NOCSH
description: この記事では、グローバルな Microsoft 365 テナントの中国ユーザーのネットワークパフォーマンスを最適化するためのガイダンスを提供します。
ms.openlocfilehash: e5d74bdae23545c1e7c65fae44010a8c5a3829e3
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997807"
---
# <a name="microsoft-365-global-tenant-performance-optimization-for-china-users"></a>中国ユーザー向けの Microsoft 365 グローバルテナントのパフォーマンスの最適化

>[!IMPORTANT]
>このガイダンスは、中国に配置されている**企業の microsoft 365 ユーザー**がグローバルな**microsoft 365 テナント**に接続する使用シナリオに固有のものです。 このガイダンスは、21Vianet が運用している Office 365 のテナントには適用**されません**。

グローバルな Microsoft 365 テナントと中国の企業のプレゼンスがある企業では、中国の電話会社のインターネットアーキテクチャに固有の要因によって、Microsoft 365 の中国ベースのユーザー向けのクライアントパフォーマンスが複雑になることがあります。

中国 Isp は、国境デバイスを通過するグローバルなパブリックインターネットへの海外の接続を規制しています。これは、境界を越えたネットワークの輻輳が発生する傾向があります。 この輻輳により、中国に出入りするすべてのインターネットトラフィックに対してパケット損失と待機時間が発生します。

![Microsoft 365 トラフィック非最適化](media/O365-networking/China-O365-unoptimized.png)

パケット損失と遅延は、ネットワークサービス、特に大規模なデータ交換 (大規模なファイル転送など) や、ほぼリアルタイムのパフォーマンス (オーディオおよびビデオアプリケーション) を必要とするサービスのパフォーマンスに悪影響を及ぼすことがあります。

このトピックの目的は、Microsoft 365 サービスにおける中国の国境を越えたネットワークの輻輳による影響を軽減するためのベストプラクティスを提供することです。 このトピックでは、中国の電話会社での複雑なルーティングによる高パケット待機時間の問題など、最終段階のパフォーマンスの問題に対処することはありません。

## <a name="corporate-network-best-practices"></a>企業ネットワークのベストプラクティス

中国のグローバルな Microsoft 365 テナントとユーザーを有する多くの企業は、中国のオフィスの場所と世界中の海外の場所との間で企業ネットワークトラフィックを伝送するプライベートネットワークを実装しています。 これらの企業は、このネットワークインフラストラクチャを活用して、国境を越えたネットワーク輻輳を防ぎ、中国における Microsoft 365 サービスのパフォーマンスを最適化することができます。

>[!IMPORTANT]
>すべてのプライベート WAN 実装と同様に、お客様の国や地域の規制要件を常に調べて、ネットワーク構成が準拠していることを確認する必要があります。

最初の手順として、「 [Microsoft 365 のネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)」にあるベンチマークネットワークガイダンスに従うことが重要です。 主要な目標は、可能であれば、中国でインターネットからのグローバルな Microsoft 365 サービスにアクセスしないようにすることです。

- 既存のプライベートネットワークを活用して、中国オフィスのネットワークと、中国外のパブリックインターネットで出てきた海外の場所との間で Microsoft 365 のネットワークトラフィックを行います。 中国外のほとんどすべての場所では、明確なメリットが得られます。 ネットワーク管理者は、egressing を使用して、 [Microsoft グローバルネットワーク](https://docs.microsoft.com/azure/networking/microsoft-global-network)との間で遅延のない相互接続を行うことにより、さらに多くの機能を最適化できます。 香港、日本、南韓国の例を示します。
- ユーザーデバイスを VPN 接続経由で企業ネットワークにアクセスするように構成し、Microsoft 365 トラフィックが企業ネットワークのプライベートな海外リンクを通過できるようにします。 VPN クライアントが分割トンネリングを使用するように構成されていないか、またはユーザーデバイスが Microsoft 365 トラフィックの分割トンネリングを無視するように構成されていることを確認します。
- プライベートな海外リンクを介してすべての Microsoft 365 トラフィックをルーティングするようにネットワークを構成します。 プライベートリンク上のトラフィックの量を最小限に抑える必要がある場合は、[**最適化**] カテゴリでのみエンドポイントをルーティングするように選択し、[**許可**] と [**既定**のエンドポイントを通過する要求をインターネットに転送できるようにする] を選択できます。 これにより、高遅延およびパケット損失に最も敏感になる重要なサービスに対して最適化されたトラフィックを制限することで、パフォーマンスが向上し、帯域幅の消費を最小限に抑えることができます。
- 可能であれば、ライブメディアストリーミングトラフィック (Teams など) に TCP の代わりに UDP を使用します。 UDP は、TCP よりも優れたライブメディアストリーミングパフォーマンスを提供します。

Microsoft 365 のトラフィックを選択的にルーティングする方法については、「 [Office 365 エンドポイントの管理](managing-office-365-endpoints.md)」を参照してください。 全世界の Office 365 の Url と IP アドレスの一覧については、「 [office 365 の url と ip アドレスの範囲](urls-and-ip-address-ranges.md)」を参照してください。

![Microsoft 365 のトラフィック最適化](media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a>ユーザーのベストプラクティス

中国のユーザーは、企業ネットワークに接続されていない自宅、コーヒーショップ、ホテル、支社などのリモートの場所からグローバルな Microsoft 365 テナントに接続することで、ネットワークのパフォーマンスが低下する可能性があります。デバイスと Microsoft 365 の間のトラフィックは、中国の混雑したクロスボーダーネットワーク回路を通過する必要があります。

国境を越えたプライベートネットワークや、企業ネットワークへの VPN アクセスがオプションではない場合でも、ユーザー単位のパフォーマンスの問題は、次のベストプラクティスに従って中国ベースのユーザーをトレーニングすることによって軽減できます。

- キャッシュ (Outlook、Teams、OneDrive など) をサポートするリッチな Office クライアントを利用し、web ベースのクライアントを使用しないようにします。 Office クライアントのキャッシュおよびオフラインアクセスの機能により、ネットワークの輻輳と遅延の影響が大幅に軽減されます。
- Microsoft 365 テナントが_電話会議_機能を使用して構成されている場合、Teams ユーザーは公衆交換電話網 (PSTN) 経由で会議に参加できます。 詳細については、「 [Office 365 の電話会議](https://docs.microsoft.com/microsoftteams/audio-conferencing-in-office-365)」を参照してください。
- ネットワークのパフォーマンスの問題が発生した場合は、トラブルシューティングのために IT 部門に報告し、Microsoft 365 サービスに関する問題が疑われる場合は、Microsoft サポートにエスカレーションする必要があります。 境界を越えたネットワークのパフォーマンスが原因で発生する問題があるわけではありません。

Microsoft は、さまざまな種類のネットワークアーキテクチャおよび特性を使用して、Microsoft 365 のユーザーの利便性とクライアントのパフォーマンスを改善するために継続的に取り組んでいます。 [Office 365 技術コミュニティ](https://techcommunity.microsoft.com/t5/office-365/bd-p/Office365General)にアクセスして、会話の開始や参加、リソースの検索、機能のリクエストと提案の提出を行います。

## <a name="related-topics"></a>関連トピック

[Microsoft 365 のネットワーク計画とパフォーマンス チューニング](https://aka.ms/tune)

[Microsoft 365 ネットワーク接続の原則](office-365-network-connectivity-principles.md)

[Office 365 エンドポイントの管理](managing-office-365-endpoints.md)

[Office 365 の URL および IP アドレスの範囲](urls-and-ip-address-ranges.md)

[Microsoft グローバルネットワーク](https://docs.microsoft.com/azure/networking/microsoft-global-network)
