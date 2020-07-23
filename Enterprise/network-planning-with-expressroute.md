---
title: Office 365 向け ExpressRoute のネットワーク計画
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: Office 365 用 ExpressRoute は、ネットワークと Microsoft のデータセンターとの間にレイヤー3接続を提供します。 回線は、Office 365 のフロントエンドサーバーの境界ゲートウェイプロトコル (BGP) ルートアドバタイズを使用します。 オンプレミスデバイスの観点から、Office 365 への正しい TCP/IP パスを選択する必要がある場合、Azure ExpressRoute はインターネットの代わりとして認識されます。
ms.openlocfilehash: f147003491b2186a05edbaf73acc86e60dbe3110
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230883"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Office 365 向け ExpressRoute のネットワーク計画

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

Office 365 用 ExpressRoute は、ネットワークと Microsoft のデータセンターとの間にレイヤー3接続を提供します。 回線は、Office 365 のフロントエンドサーバーの境界ゲートウェイプロトコル (BGP) ルートアドバタイズを使用します。 オンプレミスデバイスの観点から、Office 365 への正しい TCP/IP パスを選択する必要がある場合、Azure ExpressRoute はインターネットの代わりとして認識されます。
  
Azure ExpressRoute は、Microsoft のデータセンター内の Office 365 サーバーによって提供される、サポートされている機能とサービスの特定のセットへの直接パスを追加します。 Azure ExpressRoute は、インターネット接続を Microsoft データセンターまたはドメイン名解決などの基本的なインターネットサービスに置き換わるものではありません。 Azure ExpressRoute とインターネット回線はセキュリティで保護され、冗長である必要があります。
  
次の表は、Office 365 のコンテキストにおけるインターネットと Azure ExpressRoute の接続の違いを示しています。

|**ネットワーク計画の相違点**|**インターネットネットワーク接続**|**ExpressRoute ネットワーク接続**|
|:-----|:-----|:-----|
| 必要なインターネットサービスへのアクセス (を含む)  <br/>  DNS 名前解決  <br/>  証明書失効の検証  <br/>  コンテンツ配信ネットワーク (CDNs)  <br/> |はい  <br/> |Microsoft が所有する DNS または CDN インフラストラクチャへの要求は、ExpressRoute ネットワークを使用する場合があります。  <br/> |
| Office 365 サービスへのアクセス (以下を含む)  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype for Business Online  <br/>  ブラウザー内の Office  <br/>  Office 365 ポータルと認証  <br/> |○ (すべてのアプリケーションと機能)  <br/> |はい、[特定のアプリケーションおよび機能](https://aka.ms/o365endpoints) <br/> |
|境界でのオンプレミスのセキュリティ。  <br/> |はい  <br/> |はい  <br/> |
|高可用性の計画。  <br/> |代替のインターネットネットワーク接続へのフェールオーバー  <br/> |代替 ExpressRoute 接続へのフェールオーバー  <br/> |
|予測可能なネットワークプロファイルを使用した直接接続。  <br/> |いいえ  <br/> |はい  <br/> |
|IPv6 接続。  <br/> |はい  <br/> |はい  <br/> |

ネットワーク計画のガイダンスについては、以下のタイトルを展開してください。 また、dives の詳細については、「 [Office 365 用の10個の Azure ExpressRoute](https://channel9.msdn.com/series/aer)を提供しています。

## <a name="existing-azure-expressroute-customers"></a>既存の Azure ExpressRoute のお客様

既存の Azure ExpressRoute サーキットを使用していて、この回路に Office 365 接続を追加したい場合は、使用している Office 365 の使用状況に合っているかどうかを確認するには、回路の数、出口の位置、および回路のサイズを確認する必要があります。 多くのお客様は、追加の帯域幅を必要とし、多くの回線が必要です。
  
既存の Azure ExpressRoute 回路で Office 365 へのアクセスを有効にするには、Office 365 サービスがアクセス可能になるように[ルートフィルターを構成](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)します。
  
Azure ExpressRoute サブスクリプションは顧客中心で、サブスクリプションは顧客に結び付けられています。 お客様は、複数の Azure ExpressRoute 回路を持ち、それらの回線を介して多くの Microsoft クラウドリソースにアクセスできます。 たとえば、Azure でホストされている仮想マシン、Office 365 テストテナント、および1組の冗長 Azure ExpressRoute 回路の Office 365 運用テナントにアクセスすることを選択できます。
  
次の表に、回線で実装するために選択できる2種類のピアリング関係を示します。

|**ピアリング関係**|**Azure プライベート**|**Microsoft**|
|:-----|:-----|:-----|
|**サービス** <br/> |IaaS: Azure 仮想マシン  <br/> |PaaS: Azure パブリックサービス  <br/> SaaS: Office 365  <br/> SaaS: Dynamics 365  <br/> |
|接続の開始 * * * * <br/> |お客様から Microsoft へ  <br/> Microsoft からお客様  <br/> |お客様から Microsoft へ  <br/> Microsoft からお客様  <br/> |
|**QoS のサポート** <br/> |QoS なし  <br/> |QoS<sup>1</sup> <br/> |

<sup>1</sup>この時点では、QoS は Skype for Business のみをサポートします。
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Azure ExpressRoute の帯域幅計画

各 Office 365 のお客様には、各場所のユーザー数、各 Office 365 アプリケーションでの使用をアクティブにする方法、オンプレミスまたはハイブリッド機器、ネットワークセキュリティ構成などの他の要因に応じて、それぞれ固有の帯域幅が必要になります。
  
帯域幅が少なすぎると、輻輳が発生し、データが再送信され、予測不能な遅延が発生します。 帯域幅が多すぎると、不必要なコストが発生します。 既存のネットワークでは、帯域幅は多くの場合、回線上で使用可能なヘッドの量をパーセンテージとして参照します。 10% のヘッドルームの場合は輻輳が発生し、通常は80% のヘッドルームが必要となるため、不必要なコストが発生します。 通常、ヘッドルームターゲットの割り当ては 20% ~ 50% です。
  
適切な帯域幅を見つけるには、既存のネットワーク消費をテストするのが最善の方法です。 これは、実際の使用法を得るための唯一の方法であり、すべてのネットワーク構成とアプリケーションが固有の方法である必要があります。 測定時に、総帯域幅消費、遅延、TCP 輻輳によく注目して、ネットワークのニーズを理解する必要があります。
  
すべてのネットワークアプリケーションを含む予測基準を取得したら、組織内のさまざまなユーザープロファイルを構成する小規模なグループを使用して Office 365 を試験運用し、実際の使用状況を確認し、2つの測定値を使用して、各オフィスの場所に必要な帯域幅の量を予測します。 テストで待機時間または TCP 輻輳の問題が検出された場合は、Office 365 を使用しているユーザーに近い場所に移動したり、SSL の解読/検査などの集中的なネットワークスキャンを削除したりする必要がある場合があります。
  
推奨されるネットワーク処理の種類に関するすべての推奨事項は、ExpressRoute とインターネット回線の両方に適用されます。 [パフォーマンスチューニングサイト](https://aka.ms/tune)に関するその他のガイダンスについても同じことが言えます。
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Office 365 のシナリオでの Azure ExpressRoute へのセキュリティ制御の適用

Azure ExpressRoute 接続のセキュリティ保護は、インターネット接続のセキュリティ保護と同じ原則に従って開始されます。 多くのお客様は、オンプレミスネットワークを Office 365 およびその他の Microsoft クラウドに接続する ExpressRoute のパスに沿って、ネットワークと周辺のコントロールを展開することを選択します。 これらのコントロールには、ファイアウォール、アプリケーションプロキシ、データ漏洩防止、侵入検知、侵入防止システムなどが含まれます。 多くの場合、お客様は、オンプレミスの Microsoft から開始されたトラフィックに対して、microsoft によって開始されたトラフィックに対して、オンプレミスからのトラフィックに対するさまざまなレベルの制御を適用します。
  
ここでは、展開するために選択した[ExpressRoute 接続モデル](https://docs.microsoft.com/azure/expressroute/expressroute-connectivity-models)にセキュリティを統合する例をいくつか示します。

|**ExpressRoute の統合オプション**|**ネットワークセキュリティ境界モデル**|
|:-----|:-----|
|Cloud Exchange でのコロケーション  <br/> |ExpressRoute 接続が確立されたコロケーション機能で、新しいをインストールするか、既存のセキュリティ/境界インフラストラクチャを活用します。  <br/> ルーティング/相互接続を目的とした、またはコロケーション施設から社内のセキュリティ/境界部のインフラストラクチャへの接続を行うために、コロケーション機能を利用します。  <br/> |
|ポイントツーポイントのイーサネット  <br/> |既存のオンプレミスのセキュリティ/境界のインフラストラクチャの場所で、ポイントツーポイントの ExpressRoute 接続を終了します。  <br/> ExpressRoute のパスに固有の新しいセキュリティ/境界インフラストラクチャをインストールし、そこでポイントツーポイント接続を終了します。  <br/> |
|任意の IPVPN  <br/> |Office 365 接続の ExpressRoute に使用される IPVPN に出てきたすべての場所で、既存のオンプレミスのセキュリティ/境界インフラストラクチャを活用します。  <br/> ヘアピン Office 365 の ExpressRoute に使用される IPVPN は、セキュリティ/境界として機能するように指定された特定のオンプレミスの場所に対して使用されます。  <br/> |

一部のサービスプロバイダーでは、Azure ExpressRoute を使用した統合ソリューションの一部として、管理されたセキュリティ/境界機能を提供しています。
  
Office 365 接続の ExpressRoute に使用されるネットワーク/セキュリティ境界オプションのトポロジの配置を検討する場合は、次の点に注意してください。
  
- 深さと種類のネットワーク/セキュリティコントロールは、Office 365 ユーザー環境のパフォーマンスとスケーラビリティに影響を与える可能性があります。

- 送信 (社内- \> microsoft) および着信 (microsoft \> オンプレミス) [有効] のフローでは、要件が異なる場合があります。 一般的なインターネットの宛先への送信とは異なる可能性があります。

- Office 365 のポート、プロトコル、および必要な IP サブネットの要件は、トラフィックを Office 365 またはインターネット経由で ExpressRoute を経由してルーティングする場合と同じです。

- 「Customer network/security controls」のトポロジでは、ユーザーと Office 365 サービスとの間の究極のエンドツーエンドネットワークが決定され、ネットワークの待ち時間と輻輳に大きく影響する可能性があります。

- お客様は、冗長性、高可用性、および障害復旧のベストプラクティスに従って、Office 365 用 ExpressRoute で使用するためのセキュリティ/境界トポロジを設計することをお勧めします。

さまざまな Azure ExpressRoute 接続オプションと上記の境界セキュリティモデルを比較する Woodgrove Bank の例を次に示します。
  
### <a name="example-1-securing-azure-expressroute"></a>例 1: Azure ExpressRoute のセキュリティ保護
  
Woodgrove Bank は、Azure ExpressRoute を実装することを検討しており、 [Office 365 用の ExpressRoute](routing-with-expressroute.md)に最適なアーキテクチャを計画した後、また、帯域幅の要件を理解するために上記のガイダンスを使用した後に、境界を保護するための最善の方法を決定しています。
  
複数の大陸に拠点を持つ複数国内の組織の場合、Woodgrove では、セキュリティはすべての境界にまたがる必要があります。 Woodgrove の最適な接続オプションは、大陸内に複数のピアリング場所があり、各大陸の従業員のニーズを処理するためのマルチポイント接続です。 各大陸には、大陸内に冗長な Azure ExpressRoute の回路があり、セキュリティはこれらすべてにまたがる必要があります。
  
Woodgrove の既存のインフラストラクチャは信頼性が高く、追加の作業を処理することができます。そのため、Woodgrove Bank は Azure ExpressRoute とインターネット境界セキュリティにインフラストラクチャを使用することができます。 このようになっていない場合、Woodgrove は、既存の装置を補足するため、または別の種類の接続を処理するために、追加の機器を購入することを選択できます。
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Azure ExpressRoute を使用した高可用性とフェールオーバー
<a name="BKMK_high-availability"> </a>

Expressroute プロバイダーに対して ExpressRoute を使用して、少なくとも2つのアクティブな回線を各出口からプロビジョニングすることをお勧めします。 これは、お客様に障害が発生した場合の最も一般的な場所であり、アクティブ/アクティブの ExpressRoute 回路のペアをプロビジョニングすることで簡単に回避できます。 多くの Office 365 サービスはインターネットを介してのみ利用できるため、少なくとも2つのアクティブ/アクティブインターネット回線が推奨されています。
  
ネットワークの出口の内側には、ユーザーが可用性を認識する方法において重要な役割を果たす他の多くのデバイスと回路があります。 接続シナリオのこれらの部分は、ExpressRoute または Office 365 の Sla でカバーされていませんが、組織内のユーザーが認識できるエンドツーエンドサービスの可用性において重要な役割を果たします。
  
Office 365 を使用しているユーザーに重点を置いて、いずれかのコンポーネントに障害が発生した場合に、そのサービスを使用してユーザーの操作に影響を与える可能性がある場合は、影響を受けるユーザーの合計割合を制限する方法を探します。 フェールオーバーモードが複雑な場合は、復旧に長い時間がかかることを考慮して、運用のシンプルで自動化されたフェールオーバーモードを探します。
  
ネットワークの外部では、Office 365、ExpressRoute、および ExpressRoute プロバイダーの可用性のレベルがそれぞれ異なります。
  
### <a name="service-availability"></a>サービスの可用性
  
- Office 365 サービスには、適切に定義された[サービスレベル契約](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx)が適用されています。これには、個々のサービスの稼働時間と可用性の指標が含まれます。 Office 365 でそのような高サービスの可用性レベルを維持できる理由の1つは、グローバルな Microsoft ネットワークを使用して、個々のコンポーネントが多数の Microsoft データセンター間をシームレスにフェールオーバーできるようにすることです。 このフェールオーバーは、データセンターとネットワークから複数のインターネット出口ポイントにまで及び、そのサービスを使用するユーザーの視点からのシームレスなフェールオーバーを可能にします。

- ExpressRoute は、Microsoft ネットワークエッジと ExpressRoute プロバイダーまたはパートナーインフラストラクチャ間の個々の専用回線に[99.9% の可用性 SLA を提供](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/)します。 これらのサービスレベルは、ExpressRoute 回線レベルで適用されます。これは、各ピアの場所にある冗長な Microsoft 機器とネットワークプロバイダ機器との間の[2 つの独立](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)した相互接続で構成されます。

### <a name="provider-availability"></a>プロバイダーの可用性
  
- Microsoft のサービスレベルの手配は、ExpressRoute プロバイダーまたはパートナーで停止します。 これは、可用性レベルに影響を与える選択を可能にするための最初の場所でもあります。 Microsoft の各ピアリングの場所では、ExpressRoute プロバイダーがネットワーク境界とプロバイダー接続の間で提供するアーキテクチャ、可用性、および復元性特性を正確に評価する必要があります。 冗長性、ピアリング機器、WAN 回路の提供、およびその他の付加価値の両方の論理的および物理的な側面に注意してください。また、NAT サービスや管理されたファイアウォールなどのサービスを追加します。

### <a name="designing-your-availability-plan"></a>可用性計画を設計する
  
Office 365 のエンドツーエンドの接続シナリオで、高可用性と復元を計画および設計することを強くお勧めします。 設計には、以下を含める必要があります。
  
- インターネットと ExpressRoute の両方の回路を含む単一障害点はありません。

- 影響を受けるユーザー数を最小限に抑え、最も予想されるエラーモードに対する影響の期間を最小化します。

- 最も予想されるエラーモードを使用して、シンプルで、反復可能で、自動回復プロセスを最適化します。

- 冗長なパスを使用してネットワークトラフィックと機能の完全な要求をサポートします。これには、十分なパフォーマンスがありません。

接続のシナリオには、Office 365 への独立した複数のネットワークパスに対して最適化されたネットワークトポロジを含める必要があります。 これにより、個々のデバイスまたは装置レベルで冗長性を得るために最適化されたトポロジよりも優れたエンドツーエンドの可用性が得られます。
  
> [!TIP]
> ユーザーが複数の大陸または地理的な地域に分散していて、それぞれの場所が冗長 WAN 回線を使用して、1つの ExpressRoute 回線が配置されている単一のオンプレミスの場所に接続されている場合、ユーザーは、異なる地域を最も近いピアの場所に接続する独立した ExpressRoute 回路を含むネットワークトポロジ設計より
  
各回路を異なる地理的なピアリングの場所に接続して、少なくとも2つの ExpressRoute 回路をプロビジョニングすることをお勧めします。 ユーザーが Office 365 サービスの ExpressRoute 接続を使用するすべての地域に対して、このアクティブ-アクティブな回線のペアをプロビジョニングする必要があります。 これにより、データセンターやピアリングの場所などの主要な場所に影響を与える障害が発生しても、各地域を接続したままにすることができます。 をアクティブ/アクティブとして構成することにより、エンドユーザーのトラフィックを複数のネットワークパスに分散させることができます。 これにより、デバイスやネットワーク機器の停止中に影響を受けるユーザーの範囲を減らすことができます。
  
バックアップとして、1つの ExpressRoute 回線でインターネットを使用することはお勧めしません。
  
### <a name="example-2-failover-and-high-availability"></a>例 2: フェールオーバーと高可用性
  
Woodgrove Bank の複数地域設計では、ルーティング、帯域幅、セキュリティをレビューし、現在は高可用性レビューを行う必要があります。 Woodgrove は、3つのカテゴリについては高可用性について考えています。復元、信頼性、および冗長性。
  
回復性によって、Woodgrove は障害から迅速に回復することができます。 信頼性により、Woodgrove はシステム内で一貫した結果を提供できます。 冗長性により、インフラストラクチャの1つ以上のミラー化されたインスタンス間を移動できます。
  
各エッジ構成内で、Woodgrove はファイアウォール、プロキシ、および ID を冗長化しています。 北米の場合、Woodgrove はダラスデータセンターに1つのエッジ構成を持ち、バージニアデータセンターには別のエッジ構成があります。 各場所の冗長機器は、その場所に対する復元性を提供します。
  
Woodgrove Bank のネットワーク構成は、いくつかの重要な原則に基づいて構築されています。
  
- 各地域内に複数の Azure ExpressRoute 回路があります。

- 地域内の各回路は、その地域内のすべてのネットワークトラフィックをサポートできます。

- ルーティングでは、可用性、場所などに応じて、1つまたは他のパスが明確に優先されます。

- Azure ExpressRoute の回線間のフェールオーバーは、Woodgrove が追加の構成やアクションを必要とせずに自動的に行われます。

- インターネット回線間のフェールオーバーは、Woodgrove が追加の構成やアクションを必要とせずに自動的に行われます。

この構成では、物理レベルおよび仮想レベルで冗長性を備えており、Woodgrove Bank は、信頼できる方法で、ローカルの復元、地域の復元、および全体的な復元を提供できます。 Woodgrove は、地域ごとに1つの Azure ExpressRoute 回路を評価した後、インターネットにフェールオーバーする可能性を示しています。
  
Woodgrove が地域ごとに複数の Azure ExpressRoute 回路を持つことができなかった場合、北アメリカでは、アジア太平洋地域の Azure ExpressRoute サーキットへのトラフィックのルーティングによって許容範囲外の待機時間が追加され、必要な DNS フォワーダー構成によって複雑さが増します。
  
バックアップ構成としてインターネットを活用することは推奨されません。 これにより、Woodgrove の信頼性の原則が失われ、接続を使用した一貫性のない動作が発生します。 さらに、構成されている BGP アドバタイズ、NAT 構成、DNS 構成、およびプロキシ構成を考慮してフェールオーバーするには、手動による構成が必要になります。 このようなフェールオーバーの複雑さによって、必要な手順の診断とトラブルシューティングを行うための時間が短縮されます。
  
引き続き、トラフィック管理または Azure ExpressRoute を計画して実装する方法についての質問がありますか。 その他の[ネットワークとパフォーマンスのガイダンス](https://aka.ms/tune)または[AZURE ExpressRoute の FAQ](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)を参照してください。
  
## <a name="working-with-azure-expressroute-providers"></a>Azure ExpressRoute プロバイダの使用
<a name="BKMK_high-availability"> </a>

帯域幅、待機時間、セキュリティ、高可用性の計画に基づいて、回線の場所を選択します。 サーキットを配置する最適な場所を把握したら、[地域別の現在のプロバイダーの一覧を確認](https://azure.microsoft.com/documentation/articles/expressroute-locations/)します。
  
プロバイダーまたはプロバイダーと協力して、最適な接続オプション、ポイントツーポイント、マルチポイント、またはホストされているものを選択します。 帯域幅やその他の冗長コンポーネントがルーティングと高可用性の設計をサポートする限り、接続オプションを混在させることができます。
  
ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>関連項目
<a name="BKMK_high-availability"> </a>

[Office 365 のネットワーク接続の評価](assessing-network-connectivity.md)
  
[Office 365 向け Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 向け ExpressRoute の管理](managing-expressroute-for-connectivity.md)
  
[Office 365 向け ExpressRoute でのルーティング](routing-with-expressroute.md)
  
[Office 365 向け ExpressRoute の実装](implementing-expressroute.md)
  
[Office 365 シナリオで ExpressRoute の BGP コミュニティを使用する](bgp-communities-in-expressroute.md)
  
[Skype for Business Online でのメディア品質とネットワーク接続のパフォーマンス](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Skype for Business Online 向けのネットワークの最適化](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[Skype for Business Online での ExpressRoute および QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute を使用したコール フロー](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[ベースラインとパフォーマンス履歴を使用した、Office 365 のパフォーマンスのチューニング](performance-tuning-using-baselines-and-history.md)
  
[Office 365 のパフォーマンスに関するトラブルシューティングの計画](performance-troubleshooting-plan.md)
  
[Office 365 の URL と IP アドレスの範囲](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 のネットワークとパフォーマンスのチューニング](network-planning-and-performance.md)
  
[Office 365 エンドポイントの FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
