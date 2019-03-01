---
title: Office 365 のネットワークをセットアップする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/01/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: '概要: Office 365 のネットワークを理解するには、このページに記載されている記事を参照してください。'
ms.openlocfilehash: b86d4afaf204cfdd22cb4ca7c85608b384ca431a
ms.sourcegitcommit: eb52922c0ee34791fd71ae78338ab203f7761eec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "30341918"
---
# <a name="set-up-your-network-for-office-365"></a>Office 365 のネットワークをセットアップする

**概要**: Office 365 のネットワークを理解するには、このページに記載されている記事を参照してください。
  
Office 365 のオンボーディングで大切なのは、ネットワークとインターネット接続が最適化されたアクセスとなるように設定することです。オンプレミス ネットワークがグローバルに分散されたサービスとしてのソフトウェア (SaaS) のクラウドにアクセスできるように構成することは、オンプレミスのデータセンターへのトラフィックに最適化された、従来のネットワークを構成する場合とは異なります。 

以下の記事を活用して、主な違いを理解し、エッジ デバイス、クライアント コンピューター、オンプレミス ネットワークを変更して、ユーザーにとって最適となるパフォーマンスを実現させましょう。

## <a name="how-office-365-networking-works"></a>Office 365 ネットワークのしくみ

Office 365 の接続の概要については、次の記事を参照してください。

- [Office 365 ネットワーク接続の概要](office-365-networking-overview.md)
- [Office 365 ネットワーク接続の原則](office-365-network-connectivity-principles.md)
- [Office 365 へのネットワーク接続](network-connectivity.md)

パフォーマンスの向上に関するアドバイスについては、「[Office 365 のネットワーク計画とパフォーマンス チューニング](network-planning-and-performance.md)」を参照してください。

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a>ネットワーク機器業者として Office 365 ネットワークをサポートする

ネットワーク機器業者のお客様は、[Office 365 ネットワーク パートナー プログラム](office-365-networking-partner-program.md)にぜひご参加ください。ご参加いただくと、Office 365 のネットワーク接続の基本原則をお客様の会社の製品とソリューションに組み込んでいただけます。 

## <a name="office-365-endpoints"></a>Office 365 エンドポイント

エンドポイントとは、インターネット上の Office 365 トラフィックの宛先 IP アドレス、DNS ドメイン名、URL のセットのことです。 

Office 365 のクラウドベースのサービスのパフォーマンスを最適化するには、クライアント ブラウザーと境界ネットワーク内のデバイスでこれらのエンドポイントに対して特別な処理を行う必要があります。これらのデバイスには、ファイアウォール、SSL 中断/検査とパケット検査デバイス、およびデータ損失防止システムが含まれます。

詳細については、「[Office 365 エンドポイントの管理](managing-office-365-endpoints.md)」を参照してください。

現在、5 つの異なる Office 365 クラウドがあります。この表からそれぞれのクラウドのエンドポイント一覧へ移動できます。

|||
|:-------|:-----|
| [世界中のエンドポイント](urls-and-ip-address-ranges.md) | 米国政府機関向けコミュニティ クラウド (GCC) を含む、世界中の Office 365 サブスクリプションのエンドポイント。 |
| [米国政府の DoD エンドポイント](office-365-u-s-government-dod-endpoints.md) | 米国国防総省 (DoD) のサブスクリプションのエンドポイント。 |
| [米国政府の GCC High エンドポイント](office-365-u-s-government-gcc-high-endpoints.md) | 米国政府機関向けコミュニティ クラウド High (GCC High) サブスクリプションのエンドポイント。 |
| [21Vianet エンドポイントが運用している Office 365](urls-and-ip-address-ranges-21vianet.md) | 中国での Office 365 のニーズを満たすために設計された、21Vianet が運用する Office 365 のエンドポイント。 |
| [Office 365 Germany エンドポイント](office-365-germany-endpoints.md) | ヨーロッパにある、規制が最も厳しいドイツ、欧州連合 (EU)、および欧州自由貿易連合 (EFTA) のお客様向けの特別なクラウドのエンドポイント。 |
|||

Office 365 クラウドのエンドポイントの最新の一覧を自動的に取得するには、「[Office 365 IP アドレスと URL の Web サービス](office-365-ip-web-service.md)」を参照してください。

その他のエンドポイントについては次の記事を参照してください。

- [Web サービスに含まれていないその他のエンドポイント](additional-office365-ip-addresses-and-urls.md)
- [Office 2016 for Mac でのネットワーク要求](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-office-365-networking"></a>Office 365 ネットワークに関するその他のトピック

Office 365 ネットワークの専門的なトピックについては、次の記事を参照してください。

- [コンテンツ配信ネットワーク](content-delivery-networks.md)
- [Office 365 サービスでの IPv6 サポート](ipv6-support.md)
- [Office 365 の NAT サポート](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a>Office 365 向け ExpressRoute

Office 365 トラフィック向け ExpressRoute の使用についての詳細は、次の記事を参照してください。

- [Office 365 向け Azure ExpressRoute](azure-expressroute.md)
- [Office 365 向け ExpressRoute の実装](implementing-expressroute.md)
- [Office 365 向け ExpressRoute でのネットワーク計画](network-planning-with-expressroute.md)
- [Office 365 向け ExpressRoute でのルーティング](routing-with-expressroute.md)
