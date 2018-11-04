---
title: Microsoft クラウド接続の一般的な要素
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: '概要: ネットワーク インフラストラクチャの一般的な要素とネットワークを準備する方法を理解します。'
ms.openlocfilehash: 1bd56da2b3ede08a8ef6be3834b246200970a690
ms.sourcegitcommit: 236bf086f0596de8b612a9d8f40df4f3ce199146
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2018
ms.locfileid: "25897030"
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a>Microsoft クラウド接続の一般的な要素

 **概要:** ネットワーク インフラストラクチャの一般的な要素とネットワークを準備する方法を理解します。
  
ネットワーキングと Microsoft クラウドの統合によって、広範なサービスへの最適なアクセスが提供されます。
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a>Microsoft クラウド サービスを利用するためのネットワークの準備の手順
<a name="steps"> </a>

オンプレミス ネットワークの場合:
  
1. クライアント コンピューターを分析し、ネットワーク ハードウェア、ソフトウェア ドライバー、プロトコル設定、およびインターネット ブラウザーに関して最適化します。
    
2. トラフィックの待機時間およびインターネット エッジ デバイスに最適化されたルーティングに関して、オンプレミス ネットワークを分析します。
    
3. インターネット エッジ デバイスの容量とパフォーマンスを分析し、より高いレベルのトラフィック向けに最適化します。
    
インターネット接続の場合:
  
1. インターネット エッジ デバイス (外部ファイアウォール等) と、接続先の Microsoft クラウド サービスの地域の間の待機時間を分析します。
    
2. 現在のインターネット接続の容量と使用率を分析し、必要に応じて容量を追加します。または、ExpressRoute 接続を追加します。
    
## <a name="microsoft-cloud-connectivity-options"></a>Microsoft クラウド接続のオプション
<a name="steps"> </a>

既存のインターネット パイプまたは ExpressRoute 接続により、Office 365、Azure、Dynamics 365 を使用します。
  
**図 1: Microsoft クラウド接続のオプション**

![図 1:Microsoft クラウド接続のオプション](media/Network-Poster/CommonElements.png)

  
図 1 は、既存のインターネット パイプまたは ExpressRoute を使用して、どのようにオンプレミスのネットワークを Microsoft クラウド製品に接続するかを示します。インターネット パイプは DMZ を表し、次のコンポーネントを有する場合があります。
  
- **内部ファイアウォール:** 信頼されているネットワークと信頼されていないネットワーク間の障壁です。(ルールに基づいて) トラフィックのフィルター処理および監視を行います。
    
- **外部ワークロード:** インターネット上で、外部のユーザーに対して利用可能になっている Web サイトまたはその他のワークロード。
    
- **プロキシ サーバー:** イントラネット ユーザーの代わりに web コンテンツの要求をサービスします。リバース プロキシでは、未承諾の受信要求を許可します。
    
- **外部ファイアウォール:** 送信トラフィックおよび指定した着信トラフィックを許可します。アドレス変換を実行できます。
    
- **ISP への WAN 接続:** 接続およびルーティングに関してインターネットと同等であるキャリア ベースの ISP への接続。
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a>すべての Microsoft クラウド サービスに共通のネットワークの領域
<a name="steps"> </a>

Microsoft クラウド サービスのいずれかを採用するときは、ネットワークに関する次の領域を検討する必要があります。
  
- **イントラネット パフォーマンス:** クライアント コンピューターを含むイントラネットが最適化されていない場合、インターネット ベースのリソースはパフォーマンスの低いものになります。
    
- **エッジ デバイス:** ネットワークのエッジにあるデバイスは出口点であり、それにはネットワーク アドレス変換 (NAT)、プロキシ サーバー (リバース プロキシを含む)、ファイアウォール、侵入検出デバイス、またはこれらの組み合わせが含まれます。
    
- **インターネット接続:** ISP とインターネットへの WAN 接続には、ピーク時の負荷を処理するのに十分な容量が必要です。ExpressRoute 接続を使用することもできます。
    
- **インターネット DNS:** Microsoft クラウドまたはクラウドでホストされているサービスを検索するための、A、AAAA、CNAME、MX、PTR、その他のレコード。たとえば、Azure PaaS でホストされているアプリのために、CNAME レコードが必要な場合があります。
    

## <a name="next-step"></a>次の手順

[Microsoft クラウド接続のための ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a>関連項目

<a name="steps"> </a>

[エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)


