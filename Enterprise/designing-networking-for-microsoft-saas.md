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
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487300"
---
# <a name="designing-networking-for-microsoft-saas"></a>Microsoft SaaS のためのネットワーク デザイン

 **概要:** Office 365、Microsoft Intune、Dynamics 365 を含む Microsoft の SaaS サービスにアクセスするためにネットワークを最適化する方法を理解します。
  
Microsoft SaaS サービスに対してネットワークを最適化するには、あらゆるカテゴリのトラフィックを Microsoft SaaS サービスを別のカテゴリのトラフィックをルーティングするために内部デバイスとエッジ デバイスを構成する必要があります。
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Microsoft SaaS サービスを利用するためのネットワークの準備の手順

Microsoft SaaS サービス向けにネットワークを最適化するには、次の手順に従います。
  
1. [Microsoft クラウド接続の一般的な要素](common-elements-of-microsoft-cloud-connectivity.md)の「**Microsoft クラウド サービスを利用するためのネットワークの準備の手順**」セクションを読んでください。
    
2. 各オフィスにインターネット接続を追加します。
    
3. すべてのインターネット接続の isp が、ローカル IP アドレスを持つ DNS サーバーを使用していることを確認します。
    
4. ネットワークヘアピン、クラウドベースのセキュリティサービスなどの中間にある宛先を調べ、可能であれば削除します。
    
5. Microsoft SaaS トラフィックの最適化と許可のカテゴリの処理をバイパスするようにエッジデバイスを構成します。

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>Microsoft の SaaS サービスへのトラフィックを最適化する    

Microsoft SaaS トラフィックには、次の3つのカテゴリがあります。

- 最適化

  すべての microsoft saas サービスに接続するために必要です。また、microsoft saas の帯域幅、接続、およびデータ量の 75% を表しています。

- 許可

  特定の Microsoft SaaS サービスおよび機能への接続に必須ですが、ネットワークパフォーマンスや待機時間は、最適化カテゴリの場合と同じではありません。

- 既定

  Microsoft SaaS サービスと、最適化を必要としない依存関係を表します。 既定のカテゴリトラフィックを通常のインターネットトラフィックと同じように扱うことができます。


**図 1: すべてのオフィスの Microsoft SaaS トラフィックに推奨される構成**

![図 1: すべてのオフィスの Microsoft SaaS トラフィックに推奨される構成](media/Network-Poster/SaaS1.png)

図1は、ブランチオフィス、地域または中央1つを含むすべてのオフィスに推奨される構成を示しています。

- **既定**のカテゴリと一般的なインターネットトラフィックは、プロキシサーバーやその他のエッジデバイスを使用してインターネットベースのセキュリティリスクに対する保護を提供するオフィスにルーティングされます。
- [**最適化**と**許可**] カテゴリトラフィックは、接続しているユーザーが含まれている office に最も近い Microsoft ネットワークフロントエンドの端に直接転送されます。プロキシサーバーやその他のエッジデバイスは使用しません。

ブランチオフィスのソフトウェア定義ワイドエリアネットワーク (SD) デバイスは、トラフィックを分離して、次のことを行います。 

- **既定**のカテゴリと一般的なインターネットトラフィックは、WAN バックボーン上の中央または地域のオフィスに送られます。 
- カテゴリトラフィックの**最適化**と**許可**は、ローカルインターネット接続を提供する ISP に送られます。
  
詳細については、以下を参照してください。
  
- [ネットワーク接続の原則](https://aka.ms/expressrouteoffice365)

- [Office 365 のネットワークと移行の計画](https://aka.ms/tune)
    
## <a name="next-step"></a>次の手順

[Microsoft Azure PaaS のためのネットワーク デザイン](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>関連項目

[エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

