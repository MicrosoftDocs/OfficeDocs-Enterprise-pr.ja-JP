---
title: Microsoft SaaS のためのネットワーク デザイン
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: '概要: Office 365、Microsoft Intune、Dynamics 365 を含む Microsoft の SaaS サービスにアクセスするためにネットワークを最適化する方法を理解します。'
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872268"
---
# <a name="designing-networking-for-microsoft-saas"></a>Microsoft SaaS のためのネットワーク デザイン

 **概要:** Office 365、Microsoft Intune、Dynamics 365 を含む Microsoft の SaaS サービスにアクセスするためにネットワークを最適化する方法を理解します。
  
マイクロソフトの SaaS サービスのネットワークを最適化するには、内部の構成とマイクロソフトの SaaS サービスをさまざまなカテゴリのトラフィックをルーティングするエッジ デバイスが必要です。
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Microsoft SaaS サービスを利用するためのネットワークの準備の手順

Microsoft SaaS サービス向けにネットワークを最適化するには、次の手順に従います。
  
1. [Microsoft クラウド接続の一般的な要素](common-elements-of-microsoft-cloud-connectivity.md)の「**Microsoft クラウド サービスを利用するためのネットワークの準備の手順**」セクションを読んでください。
    
2. 各オフィスには、インターネットに接続を追加します。
    
3. すべてのインターネット接続を Isp がローカル IP アドレスで DNS サーバーを使用することを確認します。
    
4. ネットワーク hairpins、クラウド ベースのセキュリティ サービスでは、介在する宛先を確認し、可能であればそれを排除します。
    
5. 最適化の処理をバイパスし、カテゴリのマイクロソフトの SaaS のトラフィックを許可する、エッジ ・ デバイスを構成します。

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>マイクロソフトの SaaS のサービスへのトラフィックを最適化します。    

マイクロソフトの SaaS のトラフィックの次の 3 つに分類されます。

- 最適化

  すべてのマイクロソフトの SaaS サービスとマイクロソフトの SaaS の帯域幅、接続、およびデータの量の 75% 以上を表すへの接続が必要です。

- 許可

  特定への接続に必要なマイクロソフトの SaaS サービスし機能が、ネットワークのパフォーマンスと最適化のカテゴリとしての待機時間に影響はありません。

- 既定値

  マイクロソフトの SaaS サービスとすべての最適化を必要としない依存関係を表します。通常のインターネット トラフィックのように既定のカテゴリのトラフィックを扱うことができます。


**図 1: は、マイクロソフトの SaaS のトラフィックをすべてのオフィスの構成を推奨します。**

![図 1: は、マイクロソフトの SaaS のトラフィックをすべてのオフィスの構成を推奨します。](media/Network-Poster/SaaS1.png)

図 1 は、ブランチ オフィスで、または地域の中心的なものなど、すべてのオフィスの推奨構成を示しています。

- **既定**のカテゴリと全般的なインターネット トラフィックがプロキシ サーバーやその他のインター ネット ベースのセキュリティ リスクに対する保護を提供するエッジ ・ デバイスのあるオフィスにルーティングします。
- カテゴリのトラフィックを**最適化**し、**許可**は、Microsoft ネットワークのフロント エンド プロキシ サーバーやその他のエッジ デバイスをバイパスして、接続しているユーザーが含まれているオフィスに最も近いエッジに直接転送されます。

ブランチ オフィスでの広域のソフトウェア定義 (SD wan を経由するネットワーク デバイスがトラフィックを分離できるようにします。 

- **既定**のカテゴリと全般的なインターネット トラフィックが WAN のバックボーンを介して中央または地域のオフィスに移動します。 
- カテゴリのトラフィックを**最適化**し、**許可**は、ローカルのインターネット接続を提供する ISP に移動します。
  
詳細については、次のトピックを参照してください。
  
- [ネットワーク接続性の原則](https://aka.ms/expressrouteoffice365)

- [Office 365 のネットワークと移行の計画](https://aka.ms/tune)
    
## <a name="next-step"></a>次の手順

[Microsoft Azure PaaS のためのネットワーク デザイン](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>関連項目

[エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

