---
title: Office 365 へのネットワーク接続
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365 は、世界中のお客様は、インターネット接続を使用してサービスへの接続を有効にするよう設計されています。サービスの拡大に伴って、セキュリティ、パフォーマンス、および Office 365 の信頼性が向上しましたベース サービスへの接続を確立するためにインターネットを使用しているお客様に。
ms.openlocfilehash: b72b0a4584542e4c8673c7cf009c66aa97c6b81c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541756"
---
# <a name="network-connectivity-to-office-365"></a>Office 365 へのネットワーク接続

Office 365 は、世界中のお客様は、インターネット接続を使用してサービスへの接続を有効にするよう設計されています。サービスの拡大に伴って、セキュリティ、パフォーマンス、および Office 365 の信頼性が向上しましたベース サービスへの接続を確立するためにインターネットを使用しているお客様に。
  
Office 365 を使用する予定のユーザーは、展開プロジェクトの一部として、既存の予測とインターネットの接続性のニーズを評価する必要があります。エンタープライズ クラスの導入インターネット接続の信頼性が高く、適切なサイズの使用 Office 365 の機能およびシナリオの重要な部分です。
  
多くのさまざまな人々 や組織によっては、サイズと初期設定では、ネットワークの評価を実行できます。評価のネットワーク範囲にしているので、展開プロセスによって異なります。ネットワークを評価するためにかかるを把握するために、ネットワークの評価ガイド」に使用できるオプションを理解するために開発しました。この評価が可能かどうかの手順とリソースを正常に Office 365 を採用することを有効にする配置プロジェクトに追加します。
  
これら所定の宿[Skype の運用フレームワーク](https://www.skypeoperationsframework.com/)のような包括的なネットワークの評価と実装の詳細ネットワーク設計上の課題の解決策の候補が提供されます。[マイナーの構成やデザインの変更](https://aka.ms/manageo365endpoints)、既存のネットワークとインターネットの出口のインフラストラクチャに、Office 365 へのネットワーク接続を確保できるほとんどのネットワークの評価が示されます。

いくつかの評価には、Office 365 へのネットワーク接続のネットワーク コンポーネントの追加投資が必要になりますが表示されます。たとえば、WAN の帯域幅、または Office 365 へのインターネット接続をサポートするためにルーティング インフラストラクチャの最適化に投資します。場合によっては評価では、[ビジネス オンラインのメディアの品質の Skype](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)などの場合に、規制やパフォーマンスの要件は、影響を受ける Office 365 へのネットワーク接続が表示されます。これらの要件は、インターネット接続インフラストラクチャ、ルーティングの最適化では、専用のダイレクト接続への投資する可能性があります。
  
> [!NOTE]
> マイクロソフトでは、Azure ExpressRoute の Microsoft Peering ルーティング ドメインを確認する方法を変更します。2017 年 7 月 31日の開始 Azure ExpressRoute のすべての顧客ができます Microsoft Peering Azure の管理コンソールから直接、または PowerShell を使用しています。Microsoft Peering を有効にすると、すべてのお客様は、Dynamics 365 お客様との契約のアプリケーション (CRM Online と呼ばれていました) の BGP ルートのアドバタイズを受信するルート フィルターを作成できます。Office 365 の Azure ExpressRoute を必要とするお客様は、ルート フィルターを作成するには Office 365 の前に、マイクロソフトからレビューを取得しなければなりません。Office 365 の ExpressRoute を有効にするためのレビューを要求する方法の詳細については、マイクロソフト アカウント チームにお問い合わせください。承認されていないサブスクリプションの Office 365 のルート フィルターを作成しようとして[エラー メッセージ](https://support.microsoft.com/kb/3181709)が表示されます。
  
Office 365 は、ネットワークの評価を計画する際に考慮すべき重要なポイント。
  
- Office 365 は、パブリック インターネット経由で実行されるセキュリティで保護された、信頼性の高い、高パフォーマンスのサービスです。サービスのこれらの側面を強化するために投資していきます。すべての Office 365 サービスは、インターネット接続経由で使用できます。

- コアの Office 365 の可用性、グローバルなどの側面に達したを最適化する継続的に私たちとインターネットのパフォーマンス ベースの接続性。たとえば、多くの Office 365 サービスは、インターネットへのエッジのノードの一連の拡張を活用します。このネットワークのエッジでは、最高レベルの近接性と、インターネット経由で送信される接続のパフォーマンスを提供します。

- Office 365 を使用して、含まれている Skype などのサービス ビジネス オンラインの音声、ビデオ、または会議の機能のいずれかを検討するときお客様がエンド ツー エンドのネットワークの評価を完了や、Skype の運用フレームワークを使用して要件を満たす必要があります。このようなお客様は、ExpressRoute を含む、クラウドの接続の特定の要件を満たすためにいくつかのオプションがあります。

[Microsoft Office 365 のネットワーク パフォーマンスを最適化する](https://msdn.microsoft.com/en-us/library/mt450488.aspx)マイクロソフトの事例を見てください。Office 365 の評価からしていない場合を確認、ネットワークの評価、またはネットワークの設計を発見する場所の課題をしてください Microsoft アカウント ・ チームとともに作業を克服するための支援をする必要があります。
  
また、Office 365 のトラフィックを安全に管理し、最高のパフォーマンスを取得するための接続の原理を理解するのには[Office 365 のネットワーク接続性の原則](https://aka.ms/o365networkingprinciples)を参照してください。この資料では Office 365 のネットワーク接続を安全に最適化するため、最新のガイダンスを理解できます。
  
戻るを使用することができます短いリンクを次のとおりです: [ https://aka.ms/o365networkconnectivity。](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>関連項目

[Office 365 エンドポイントを管理します。](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 エンドポイントに関する FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[Office 365 のネットワークとパフォーマンスの調整](network-planning-and-performance.md)
  
[Office 365 向け Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 向け ExpressRoute でのルーティング](routing-with-expressroute.md)
  
[Office 365 向け ExpressRoute でのネットワーク計画](network-planning-with-expressroute.md)
  
[ExpressRoute に BGP のコミュニティを使用して Office 365 シナリオ (プレビュー)](bgp-communities-in-expressroute.md)
  
[メディアの品質とオンライン ビジネスの Skype でのネットワーク接続のパフォーマンス](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Office 365 の URL と IP アドレス範囲](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 ネットワーク接続の原則](https://aka.ms/o365networkingprinciples)
