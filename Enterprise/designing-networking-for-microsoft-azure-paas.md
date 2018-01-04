---
title: "Microsoft Azure PaaS のためのネットワーク デザイン"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: "概要: Microsoft Azure PaaS へのアクセスのためにネットワークを最適化する方法を理解します。"
ms.openlocfilehash: d63a7a20d4648b0044a24ea86ad4e9125779a027
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="designing-networking-for-microsoft-azure-paas"></a>Microsoft Azure PaaS のためのネットワーク デザイン

 **概要:** Microsoft Azure PaaS へのアクセスのためにネットワークを最適化する方法を理解します。
  
Azure PaaS アプリ用のネットワーキングを最適化するには、適切なインターネット帯域幅が必要であり、複数のサイトまたはアプリにまたがるネットワーク トラフィックの分散が必要とされる可能性があります。
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a>Azure において組織の PaaS アプリケーションをホストするための手順の計画

ここにセクション本文を挿入します。
  
1. [Microsoft クラウド接続の一般的な要素](common-elements-of-microsoft-cloud-connectivity.md)の「**Microsoft クラウド サービスを利用するためのネットワークの準備の手順**」セクションを読んでください。
    
2. [Microsoft SaaS のためのネットワーク デザイン](designing-networking-for-microsoft-saas.md)の「**Microsoft SaaS サービスを利用するためのネットワークの準備の手順**」セクションに記載されている手順 2 から 4 を使用して、インターネット帯域幅を最適化します。
    
3. Azure への ExpressRoute 接続が必要かどうかを判断します。
    
4. Web ベースのワークロードに関して、Azure アプリケーション ゲートウェイが必要かどうかを判断します。
    
5. 異なるデータ センターの異なるエンドポイントへトラフィックを分散させるため、Azure Traffic Manager が必要かどうかを判断します。
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a>組織の PaaS アプリケーションのためのインターネット帯域幅

Azure PaaS においてホストされている組織のアプリケーションは、イントラネット ユーザーのためのインターネット帯域幅を必要とします。次のような 2 つの選択肢があります。
  
- **オプション 1:** ピーク時の負荷を処理する能力を持つ、インターネット トラフィックに最適化された既存のパイプを使用します。インターネット エッジ、クライアントの使用、および IT 運用上の考慮事項については、[Microsoft SaaS のためのネットワーク デザイン](designing-networking-for-microsoft-saas.md) をご覧ください。
    
- **オプション 2:** 高帯域幅または低遅延のニーズのため、ExpressRoute を使用して Azure に接続します。
    
**図 1: Azure PaaS サービスに接続するための接続オプション**

![図 1: Azure PaaS サービスの接続オプション](images/Network_Poster/PaaS1.png)
  
図 1 はインターネット パイプまたは ExpressRoute によって Azure PaaS サービスに接続しているオンプレミスのネットワークを示しています。
  
## <a name="azure-application-gateway"></a>Azure アプリケーション ゲートウェイ

アプリケーション レベルのルーティングおよび負荷分散サービスを使用して、Web アプリケーション、クラウド サービス、および仮想マシンのために、Azure における拡張性と可用性の高い Web フロント エンドを構築します。 
  
**図 2: Azure アプリケーション ゲートウェイ**

![図 2:Azure アプリケーション ゲートウェイ サービス](images/Network_Poster/PaaS2.png)
  
図 2 は、Azure アプリケーション ゲートウェイと、インターネットからのユーザー要求がどのように Azure の Web アプリケーション、クラウド サービス、または仮想マシンに送られるのかを示しています。
  
アプリケーション ゲートウェイは現在、以下のためにレイヤー 7 のアプリケーションの配信をサポートしています。
  
- HTTP 負荷分散
    
- Cookie ベースのセッション類似性
    
- SSL オフロード
    
詳細については、[アプリケーション ゲートウェイ]((https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction)) をご覧ください。
  
## <a name="azure-traffic-manager"></a>Azure トラフィック マネージャー

トラフィックを異なるエンドポイントに分散させます。それには、異なるデータ センターまたは外部エンドポイントに置かれたクラウド サービスまたは Azure Web アプリケーションを含めることができます。
  
Traffic Manager は、次のルーティング方法を使用します。
  
- **フェールオーバー:** エンドポイントは、同じまたは異なる Azure データ センターにあります。通常はすべてのトラフィックに、プライマリ エンドポイントを使用するとしても、プライマリ エンドポイントまたはバックアップ エンドポイントが使用不可になった場合には、バックアップを提供します。
    
- **ラウンド ロビン:** 同じデータ センター内または異なるデータ センターに置かれたエンドポイントのセットの間で負荷を分散します。
    
- **パフォーマンス:** 複数の地理的な場所にエンドポイントを有し、要求元のクライアントは最小の待機時間となる "最も近い" エンドポイントを使用するようにします。
    
ここでは、3 つの地理的に分散した Web アプリケーションの例を挙げます。
  
**図 3: Azure Traffic Manager**

![図 3: Azure Traffic Manager](images/Network_Poster/PaaS3.png)
  
図 3 は、Traffic Manager が米国、ヨーロッパ、アジアの 3 つの異なる Azure Web アプリに要求を送信するために使用する基本的なプロセスを示しています。例の中で:
  
1. Web サイト URL に関するユーザーの DNS クエリは Azure Traffic Manager に送信され、それはパフォーマンス ルーティング メソッドに基づいて地域の Web アプリの名前を返します。
    
2. ユーザーは、ヨーロッパの地域の Web アプリケーションによってトラフィックを開始します。
    
詳細については、「[Traffic Manager]((https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview))」を参照してください。
  
## <a name="see-also"></a>関連項目

[エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

[Microsoft の Enterprise Cloud ロードマップ: IT の意思決定者向けのリソース]((https://sway.com/FJ2xsyWtkJc2taRD))



