---
title: Office 365 向け Azure ExpressRoute
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: Office 365 で Azure ExpressRoute を使用する方法と、Office 365 で使用するために Azure ExpressRoute を展開する場合に必要となるネットワーク実装プロジェクトを計画する方法について説明します。
ms.openlocfilehash: 80b42fc43f395d9dd94384d456d40eb536541746
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997951"
---
# <a name="azure-expressroute-for-office-365"></a>Office 365 向け Azure ExpressRoute

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

Office 365 で Azure ExpressRoute を使用する方法と、Office 365 で使用するために Azure ExpressRoute を展開する場合に必要となるネットワーク実装プロジェクトを計画する方法について説明します。 多くの場合、Azure で実行されるインフラストラクチャおよびプラットフォームサービスは、ネットワークアーキテクチャとパフォーマンスに関する考慮事項に対処することでメリットを得られます。 このような場合は、Azure に ExpressRoute をお勧めします。 Office 365 や Dynamics 365 などのサービスとしてのソフトウェアは、インターネットを介して安全かつ確実にアクセスできるように構築されています。 「 [Office 365 のネットワーク接続の評価](assessing-network-connectivity.md)」の記事では、インターネットのパフォーマンスとセキュリティについて説明し、「office 365 用の Azure ExpressRoute」を検討することができます。

> [!NOTE]
> Office 365 の ExpressRoute を使用するには、Microsoft の承認が必要です。 お客様の規制要件で直接的な接続が義務付けられている場合、Microsoft はお客様のすべての要求をレビューし、Office 365 の使用状況を承認します。 このような要件がある場合は、テキストの抜粋と web リンクを入力してください。これは、Microsoft レビューを開始するために、 [Office 365 の ExpressRoute の要求フォーム](https://aka.ms/O365ERReview)に直接接続する必要があることを意味します。 承認されていないサブスクリプション Office 365 のルートフィルターを作成しようとすると、[エラーメッセージ](https://support.microsoft.com/kb/3181709)が表示されます。

これで、選択した Office 365 のネットワークトラフィックに対して、Office 365 への直接ネットワーク接続を追加できるようになります。 Azure ExpressRoute は直接接続で予測可能なパフォーマンスを提供し、Microsoft ネットワークコンポーネントの稼働時間の SLA を99.95% にします。 Azure ExpressRoute でサポートされていないサービスに対しては、インターネット接続が依然として必要になります。

## <a name="planning-azure-expressroute-for-office-365"></a>Office 用 Azure ExpressRoute の計画365

インターネット接続に加えて、Office 365 ネットワークトラフィックのサブセットを、予測可能で、Microsoft ネットワークコンポーネントに対して99.95% の稼働時間の SLA を提供する直接接続でルーティングするように選択することもできます。 Azure ExpressRoute には、Office 365 およびその他の Microsoft クラウドサービスへの専用ネットワーク接続が用意されています。

既存の MPLS WAN を使用しているかどうかに関係なく、ExpressRoute は3つの方法のいずれかでネットワークアーキテクチャに追加できます。サポートされているクラウド exchange コロケーションプロバイダー、イーサネットポイントツーポイント接続プロバイダー、または MPLS 接続プロバイダを介して。 [お客様の地域で利用可能なプロバイダーを](https://azure.microsoft.com/documentation/articles/expressroute-locations/)参照してください。 Direct ExpressRoute 接続を使用すると、 [Office 365 サービスに含まれて](azure-expressroute.md#BKMK_WhatDoIGet)いるアプリケーションへの接続を有効にすることができます。次の説明を参照してください。 他のすべてのアプリケーションおよびサービスのネットワークトラフィックは、引き続きインターネットをスキャンします。

Office 365、Windows Update、TechNet などのすべての Microsoft アプリケーションにアクセスするためにインターネット経由で Microsoft のデータセンターに接続する一般的な Office 365 ユーザーの場合は、次のような高レベルのネットワーク図を検討してください。 お客様は、オンプレミスのネットワークから接続しているか、独立したインターネット接続から接続しているかに関係なく、同じネットワークパスを使用します。

![Office 365 のネットワーク接続](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

次に、インターネットと ExpressRoute の両方を使用して Office 365 に接続する Office 365 お客様を示す、更新された図を見てみましょう。 パブリック DNS およびコンテンツ配信ネットワークノードなどの一部の接続では、依然としてパブリックインターネット接続が必要です。 また、お客様の ExpressRoute の接続構築に配置されていないユーザーは、インターネットを介して接続していることにも注意してください。

![ExpressRoute を使用した Office 365 接続](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

さらに情報が必要な場合 [Azure expressroute For office 365 を使用してネットワークトラフィックを管理](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)する方法と、 [office 365 用に azure expressroute を構成](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)する方法について説明します。 また、より詳細な概念を説明するため、Channel 9 の「 [Office 365 の Azure ExpressRoute のための10の](https://channel9.msdn.com/series/aer)パーツを記録しました。

## <a name="what-office-365-services-are-included"></a>どの Office 365 サービスが含まれていますか?
<a name="BKMK_WhatDoIGet"> </a>

次の表に、ExpressRoute でサポートされている Office 365 サービスの一覧を示します。 [Office 365 エンドポイントの記事](https://aka.ms/o365endpoints)を参照して、これらのアプリケーションのネットワーク要求がインターネット接続を必要とするかを確認してください。

|**含まれるアプリケーション**|
|:-----|
|Exchange Online<sup>1</sup> <br/> Exchange Online Protection<sup>1</sup> <br/> Delve<sup>1</sup> <br/> |
|Skype for Business Online<sup>1</sup> <br/> Microsoft Teams <sup>1</sup> <br/> |
|SharePoint Online<sup>1</sup> <br/> OneDrive for Business<sup>1</sup> <br/> Project Online<sup>1</sup> <br/> |
|ポータルと共有<sup>1</sup> <br/> Azure Active Directory<sup>1</sup> <br/> AAD Connect<sup>1</sup> <br/> Office<sup>1</sup> <br/> |

<sup>1</sup>これらの各アプリケーションには、ExpressRoute でサポートされていないインターネット接続要件があります。詳細については、「 [Office 365 endpoints](https://aka.ms/o365endpoints) 」の記事を参照してください。

Office 365 用の ExpressRoute に含まれていないサービスは、エンタープライズクライアントのダウンロード用の Microsoft 365 アプリ、オンプレミスの Id プロバイダーのサインイン、および中国での Office 365 (21 Vianet) サービスを対象としています。

## <a name="implementing-expressroute-for-office-365"></a>Office 365 向け ExpressRoute の実装

ExpressRoute を実装するには、ネットワークとアプリケーションの所有者の関与が必要であり、新しい[ネットワークルーティングアーキテクチャ](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)、帯域幅の要件、セキュリティを実装する場所、高可用性などを決定するための慎重な計画が必要です。 ExpressRoute を実装するには、次のことを行う必要があります。

1. Office 365 の接続計画で ExpressRoute が満たす必要があることを完全に理解します。 インターネットまたは ExpressRoute を使用するアプリケーションについて理解し、Office 365 トラフィック用のインターネットと ExpressRoute の両方を使用して、ネットワークの容量、セキュリティ、高可用性の要件を十分に計画します。

2. インターネットと ExpressRoute の両方のトラフィックについて、出口およびピアリングの場所を<sup>決定します</sup>。

3. インターネットおよび ExpressRoute の接続に必要な容量を決定します。

4. セキュリティおよびその他の標準的な境界のコントロール<sup>1</sup>を実装するための計画を立ててください。

5. ExpressRoute にサブスクライブするには、有効な Microsoft Azure アカウントが必要です。

6. 接続モデルと[承認済みプロバイダー](https://azure.microsoft.com/documentation/articles/expressroute-locations/)を選択します。 お客様は複数の接続モデルまたはパートナーを選択できるため、パートナーは既存のネットワークプロバイダーと同じである必要はありません。

7. ExpressRoute にトラフィックを誘導する前に展開を検証します。

8. 必要に応じて[QoS を実装](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)し、地域の拡張を評価します。

<sup>1</sup>パフォーマンスに関する重要な考慮事項。 ここでの決定は、Skype for Business などのアプリケーションにとって重要な待機時間に大きな影響を与える可能性があります。

その他の参照については、 [ExpressRoute のドキュメント](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)に加えて、[ルーティングガイド](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)を使用してください。

Office 365 の ExpressRoute を購入するには、1つまたは複数の[承認](https://azure.microsoft.com/documentation/articles/expressroute-locations/)されたプロバイダーと連携して、必要な数とサイズの回路を ExpressRoute Premium サブスクリプションでプロビジョニングする必要があります。 Office 365 から購入する追加のライセンスはありません。

ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)

[Office 365 の ExpressRoute](https://aka.ms/ert)にサインアップする準備ができましたか?

## <a name="related-topics"></a>関連項目

[Office 365 のネットワーク接続の評価](assessing-network-connectivity.md)

[Office 365 向け ExpressRoute の管理](managing-expressroute-for-connectivity.md)

[Office 365 向け ExpressRoute でのルーティング](routing-with-expressroute.md)

[Office 365 向け ExpressRoute でのネットワーク計画](network-planning-with-expressroute.md)

[Office 365 向け ExpressRoute の実装](implementing-expressroute.md)

[Office 365 シナリオ用の ExpressRoute での BGP コミュニティの使用 (プレビュー)](bgp-communities-in-expressroute.md)

[Skype for Business Online でのメディア品質とネットワーク接続のパフォーマンス](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[ベースラインとパフォーマンス履歴を使用した、Office 365 のパフォーマンスのチューニング](performance-tuning-using-baselines-and-history.md)

[Office 365 のパフォーマンスに関するトラブルシューティングの計画](performance-troubleshooting-plan.md)

[Office 365 の URL および IP アドレスの範囲](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

[Office 365 のネットワークとパフォーマンスのチューニング](network-planning-and-performance.md)

## <a name="see-also"></a>関連項目

[Microsoft 365 Enterprise の概要](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
