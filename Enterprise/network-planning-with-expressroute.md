---
title: Office 365 向け ExpressRoute でのネットワーク計画
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
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
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: Office 365 の ExpressRoute の間のレイヤー 3 接続を提供する、ネットワークと Microsoft のデータ センターです。回路では、Office 365 のフロント エンド サーバーのルートのアドバタイズを罫線ゲートウェイ プロトコル (BGP) を使用します。設置型デバイスの観点から、Office 365 に TCP/IP の正しいパスを選択する必要がある場合は、Azure ExpressRoute の代わりに、インターネットとして認識されます。
ms.openlocfilehash: 79cad16a619f048d1ba98b6058127f901211344d
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541762"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Office 365 向け ExpressRoute でのネットワーク計画

Office 365 の ExpressRoute の間のレイヤー 3 接続を提供する、ネットワークと Microsoft のデータ センターです。回路では、Office 365 のフロント エンド サーバーのルートのアドバタイズを罫線ゲートウェイ プロトコル (BGP) を使用します。設置型デバイスの観点から、Office 365 に TCP/IP の正しいパスを選択する必要がある場合は、Azure ExpressRoute の代わりに、インターネットとして認識されます。
  
Azure の ExpressRoute は、サポートされている機能とマイクロソフトのデータ センター内の Office 365 のサーバーによって提供されるサービスの特定のセットに直接パスを追加します。Azure の ExpressRoute には、マイクロソフトのデータ センターまたはドメインの名前解決などの基本的なインターネット サービスへのインターネット接続は交換してください。Azure の ExpressRoute と、インターネット回線、セキュリティで保護された、冗長化された必要があります。
  
次の表には、インターネットと Office 365 のコンテキストでの Azure ExpressRoute 接続のいくつかの違いが強調表示されます。

|**ネットワークの計画の違い**|**インターネット ネットワーク接続**|**ExpressRoute ネットワーク接続**|
|:-----|:-----|:-----|
| などを含む、インターネットの必要なサービスへのアクセス  <br/>  DNS 名の解決  <br/>  証明書失効の確認  <br/>  コンテンツ配信ネットワーク  <br/> |はい  <br/> |マイクロソフトへの要求は、DNS や CDN のインフラストラクチャを使用して、可能性があります ExpressRoute ネットワークを所有しています。  <br/> |
| などを含む、Office 365 サービスへのアクセス  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype for Business Online  <br/>  Office Online  <br/>  Office 365 ポータルと認証  <br/> |はい、すべてのアプリケーションと機能  <br/> |はい、[特定のアプリケーションと機能](https://aka.ms/o365endpoints) <br/> |
|境界でのセキュリティを設置します。  <br/> |はい  <br/> |はい  <br/> |
|高可用性を計画します。  <br/> |別のインターネットのネットワーク接続へのフェイル オーバー  <br/> |代替の ExpressRoute 接続へのフェイル オーバー  <br/> |
|予測可能なネットワーク プロファイルを使用して直接接続します。  <br/> |いいえ  <br/> |はい  <br/> |
|IPv6 接続します。  <br/> |はい  <br/> |はい  <br/> |

ガイダンスを計画する複数のネットワークには、下記のタイトルを展開します。深く潜りを 10 回[Office 365 のトレーニングの Azure ExpressRoute](https://channel9.msdn.com/series/aer)シリーズ記録しました。

## <a name="existing-azure-expressroute-customers"></a>Azure ExpressRoute の既存のお客様

既存の Azure ExpressRoute 回路を使用するいるし、この回路上で Office 365 の接続を追加するには、回路、出口の場所、およびサイズが、Office 365 の使用状況のニーズに適合するようにするのには回路の数を見てする必要があります。ほとんどのお客様は、追加の帯域幅を必要として、多くは、追加の回線を必要とします。
  
既存 Azure ExpressRoute 回路上の Office 365 へのアクセスを有効にするには、[ルート フィルターを構成](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal)して、Office 365 サービスにアクセス可能です。
  
Azure ExpressRoute のサブスクリプションは、顧客を中心とした、意味のサブスクリプションは、顧客に関連付けられてです。お客様は、複数の Azure ExpressRoute 回路を持つことができ、その回路上で多くのマイクロソフトのクラウド リソースにアクセスできます。などのことができます、Azure にアクセスするための Azure ExpressRoute 回路の冗長ペアの上で仮想マシン、Office 365 テスト テナントでは、Office 365 の生産テナントをホストします。
  
この表は、2 種類の選択を実装するのには、回線を介したピアリングの関係を示しています。

|**ピアリング関係**|**Azure の秘密**|**Microsoft**|
|:-----|:-----|:-----|
|**サービス** <br/> |IaaS: Azure の仮想マシン  <br/> |PaaS: Azure パブリック サービス  <br/> SaaS: Office 365  <br/> SaaS: Dynamics 365  <br/> |
|接続開始。 <br/> |マイクロソフト製品への顧客に  <br/> Microsoft 顧客  <br/> |マイクロソフト製品への顧客に  <br/> Microsoft 顧客  <br/> |
|**QoS のサポート** <br/> |ない QoS  <br/> |QoS<sup>1</sup> <br/> |

<sup>1</sup>QoS は、この時点でのみ、ビジネスの Skype をサポートします。
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>帯域幅の Azure ExpressRoute の計画

すべての Office 365 のお客様は、それぞれの Office 365 アプリケーションでは、設置型またはハイブリッド機器およびネットワーク セキュリティの構成の使用などの他の要因には、アクティブな状態に、それぞれの場所に人の数によっては独自の帯域幅のニーズを持ちます。
  
狭すぎる帯域幅を持つと、輻輳、データ、および予期しない遅延の再送信が発生します。多くの帯域幅を持つと、不要なコストが発生します。既存のネットワークの帯域幅は、回線で利用可能なヘッドルームの量の観点からと呼ば割合。10% の余裕と、輻輳の可能性、不要なコストは、一般に 80% の余裕を持ちます。ヘッドルームの代表的なターゲットの割り当ては、20 ~ 50% です。
  
帯域幅の適切なレベルを検索するは、最適なメカニズムは、既存のネットワークの使用量をテストします。これは使用率の真の判断基準を取得し、すべてのネットワーク構成に必要な唯一の方法であり、アプリケーションは、固有のいくつかの方法に。測定する必要があります合計帯域幅の消費量、待ち時間、および TCP の輻輳、ネットワークを理解するには細心の注意を払う必要があります。
  
1 回パイロットの Office 365 の実際の使用状況を確認するのには、組織内のユーザー別のプロファイルで構成される小規模なグループで、すべてのネットワーク アプリケーションを含む推定の基準使用している 2 つの測定値の量を見積もる帯域幅が各事業所に必要なことです。待ち時間やテストについては、TCP の混雑の問題があるか場合、は、Office 365 を使用するユーザーに、出口に近い場所に移動または集中的なネットワークが SSL の暗号化の解除と検査などのスキャンを削除する必要があります。
  
すべてのネットワーク処理の種類をお勧めすることで当社の推奨事項は、ExpressRoute とインターネットの両方の回路に適用されます。[パフォーマンス チューニングのサイト](https://aka.ms/tune)でこのガイドの残りの部分に対しても同様です。
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Office 365 シナリオの Azure ExpressRoute にセキュリティ制御を適用します。

Azure ExpressRoute 接続をセキュリティで保護するインターネット接続をセキュリティで保護する場合と同じ原則から始まります。Office 365 とその他のマイクロソフトのクラウド、オンプレミスのネットワークを接続する ExpressRoute のパスに沿ったネットワークと境界部のコントロールを配置するのには多くの顧客を選択します。これらのコントロールには、ファイアウォール、アプリケーション プロキシ、データ漏洩の防止、侵入検知、侵入防止システム、およびなどがあります。多くの場合顧客はオンプレミス マイクロソフトでは、しようとしてマイクロソフトを設置しようとして、[全般] から開始されたトラフィックではなく、お客様設置のネットワークへのトラフィックとの比較からのトラフィックをコントロールのさまざまなレベルを適用します。インターネット上の送信先です。
  
[ExpressRoute 接続モデル](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-connectivity-models)を展開するとセキュリティを統合するいくつかの例を次に示します。

|**ExpressRoute 統合オプション**|**ネットワーク セキュリティ境界モデル**|
|:-----|:-----|
|Cloud Exchange でのコロケーション  <br/> |新規インストールまたは ExpressRoute の接続を確立する、コロケーション施設内の既存の/境界領域のセキュリティ インフラストラクチャを活用します。  <br/> 純粋なオンプレミス/境界領域のセキュリティ インフラストラクチャを共用施設から戻る haul 接続ルーティング相互接続の目的に活用してコロケーション施設です。  <br/> |
|ポイント ツー ポイントのイーサネット  <br/> |既存のオンプレミス/境界領域のセキュリティ インフラストラクチャの場所に ExpressRoute のポイント ツー ポイント接続を終了します。  <br/> ExpressRoute パスに固有の新しい/境界領域のセキュリティ インフラストラクチャをインストールし、ポイント ツー ポイント接続が終了します。  <br/> |
|あらゆる IPVPN  <br/> |ExpressRoute の Office 365 の接続として使用される IPVPN に出口のすべての場所にある既存のオンプレミス/境界領域のセキュリティ インフラストラクチャを活用します。  <br/> Hairpin セキュリティとの境界として機能するのには、オンプレミスで特定の場所に Office 365 の ExpressRoute 用に使用される IPVPN が指定されています。  <br/> |

一部のサービス プロバイダーでは、Azure の ExpressRoute との統合ソリューションの一部として管理されたセキュリティの境界の機能も提供します。
  
追加の考慮事項を次に示します、ネットワークとセキュリティ境界に使用するオプション ExpressRoute の Office 365 の接続の配置トポロジを検討する場合
  
- 深さと型のネットワークとセキュリティ コントロールは、Office 365 のユーザー エクスペリエンスのスケーラビリティ、パフォーマンスへの影響があります。

- 送信 (に-設置型の\>マイクロソフト) と受信 (マイクロソフト ・\>設置) [有効] の場合フロー要件が異なる場合があります。これらは一般的なインターネットの宛先に送信とは異なります。

- ポート/プロトコルと必要な IP サブネットの要件を office 365 は、Office 365 の ExpressRoute、またはインターネットを通じてトラフィックをルーティングするかどうかは同じです。

- 顧客のネットワークとセキュリティ制御の位相的な配置により、ユーザーと Office 365 サービスの間で最終的なエンド ツー エンド ネットワークと、ネットワークの遅延や輻輳に大きな影響を与えることができます。

- お客様は、トポロジを設計する、セキュリティの境界と使用の ExpressRoute と Office 365 の冗長性、可用性、および災害復旧のためのベスト プラクティスに従ってことをお勧めします。

ここでは、上で説明した境界部のセキュリティ モデルと Azure の ExpressRoute のさまざまな接続オプションを比較する Woodgrove Bank の例です。
  
### <a name="example-1-securing-azure-expressroute"></a>例 1: セキュリティで保護する Azure ExpressRoute
  
Woodgrove Bank は Azure の ExpressRoute を実装することを検討して、それらを決定するしている[Office 365 の ExpressRoute でのルーティング](routing-with-expressroute.md)の最適なアーキテクチャを計画した後は、帯域幅の要件を理解する上のガイダンスを使用した後、その境界部を保護するための最良の方法です。
  
Woodgrove では、拠点とし、複数の大陸では、多国籍組織のセキュリティは、すべての境界を広げる必要があります。Woodgrove の最適な接続性オプションは、大陸ごとに、従業員のニーズにサービスを提供する世界中でピアリング ・ マルチ ・ ポイント接続です。各大陸には、大陸内の冗長の Azure ExpressRoute 回路が含まれていて、セキュリティは、これらすべてを広げる必要があります。
  
Woodgrove の既存のインフラストラクチャの信頼性し、追加の作業を処理することができます、その結果、Woodgrove Bank の Azure ExpressRoute とインターネットの境界セキュリティのインフラストラクチャを利用することです。場合は、いずれにしても Woodgrove の既存の設備を補足するために、または別の種類の接続を処理するために他の機器を購入するように選択します。
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>高可用性を実現し、Azure の ExpressRoute を使用したフェイル オーバー
<a name="BKMK_high-availability"> </a>

ExpressRoute プロバイダーに ExpressRoute を持つ各出口から 2 つ以上アクティブ回路を準備することをお勧めします。ここでは最も一般的な顧客のエラーが発生しましたし、アクティブ/アクティブの ExpressRoute の回路の 2 つのプロビジョニングを容易に回避できます。お勧めを少なくとも 2 つのアクティブ/アクティブのインターネット回線のため、多くの Office 365 サービスは、インターネット経由でのみ利用できます。
  
ネットワークの出口のポイントは他の多くのデバイスや人での可用性を認識する方法で重要な役割を果たす回路です。接続シナリオでは、これらの部分は、ExpressRoute または Office 365 の Sla では説明しませんが、組織内で認識されるエンド ツー エンド サービスの可用性の重要な役割を再生します。
  
使用するユーザーに注目し、各人は 1 つのコンポーネントの障害の影響を受ける場合、Office 365 の運用サービスを使用してを影響を受ける人の割合の合計を制限する方法を模索します。フェイル オーバー ・ モードが複雑な運用の場合は、回復に時間の人々 の経験を考慮し、単純な運用と、自動フェールオーバー モードを探します。
  
ネットワーク、Office 365、ExpressRoute、および ExpressRoute は、プロバイダー以外すべてには、さまざまなレベルの可用性があります。
  
### <a name="service-availability"></a>サービスの可用性
  
- Office 365 サービスは、覆われて明確に定義された[サービス レベル契約](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx)では、個々 のサービスのアップタイムと可用性の測定基準が含まれています。Office 365 はこのような高度なサービスの可用性のレベルは、Microsoft のグローバル ネットワークを使用して、多くの Microsoft データ センターの間でシームレスにフェイル オーバー ・個々 のコンポーネントの機能を維持できる理由の 1 つです。このフェイル オーバーでは、データ センターとネットワークから複数のインターネット出口のポイントへの拡張し、サービスを使用するユーザーの視点からシームレスにフェイル オーバーを有効にします。

- ExpressRoute は Microsoft ネットワークのエッジと ExpressRoute のプロバイダーまたはパートナーのインフラストラクチャとの間の個々 の専用回線で[99.9% の可用性の SLA を提供](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/)します。これらのサービス ・ レベルは、 [2 つの独立の相互接続](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)を冗長化された Microsoft の機器とピアリングのそれぞれの場所でネットワーク プロバイダーの機器との間で構成される ExpressRoute の回路レベルで適用されます。

### <a name="provider-availability"></a>プロバイダーの可用性
  
- ExpressRoute プロバイダーやパートナーのサービス レベル契約を停止します。これは、まず、可用性のレベルに影響を与える選択を行うことができます。ネットワークの境界部と各 Microsoft ピアリングの場所に、プロバイダーの接続の間で、アーキテクチャ、可用性、および ExpressRoute は、プロバイダーは、弾力性の特性を綿密に評価する必要があります。冗長性、ピアリング装置、キャリアが用意されている WAN 回線では、論理的および物理的な側面の両方に注意し、付加価値サービスの NAT またはファイアウォールの管理などのサービスを追加します。

### <a name="designing-your-availability-plan"></a>可用性計画を立てる
  
計画し、Office 365 用にエンド ・ ツー ・ エンドの接続シナリオでは、高可用性と耐障害性を設計することを強くお勧めします。設計に含める必要があります。
  
- 単一点の障害、インターネットと ExpressRoute の両方の回路を含みます。

- 影響を受ける人の数と予想される最も障害モードの影響の期間を最小限にします。

- 障害モードが最も期待されてから、単純な反復可能な自動復旧プロセスを最適化します。

- ネットワーク トラフィックと大幅な低下させることがなく、冗長パスを使用して機能のフル アクセス要求をサポートします。

接続シナリオでは、Office 365 に複数の独立した、アクティブなネットワーク パスに最適なネットワーク トポロジを含める必要があります。優れたエンド ・ ツー ・ エンドの可用性のみ、個々 のデバイスや機器レベルでの冗長性に最適なトポロジよりも得られます。
  
> [!TIP]
> ユーザーと少ないユーザーは、複数の大陸や地域に分散されて、単一 ExpressRoute 回路が格納されている 1 つ設置場所への冗長 WAN 回線を介した接続する各サイトの場合は、発生します。それぞれの地域に最も近いピアリング接続を独立した ExpressRoute 回路を含むネットワーク トポロジの設計よりも、エンド ・ ツー ・ エンドのサービスの可用性の場所です。
  
各回路への接続にピアリングのさまざまな地域で、少なくとも 2 つの ExpressRoute 回路を準備することをお勧めします。このアクティブ-アクティブのペアのユーザーが Office 365 サービスの ExpressRoute の接続を使用、すべての領域の回路を準備する必要があります。これにより、データ センターなどの主要な場所またはピアリングの場所に影響を与える障害時に接続を維持するには、各地域です。としてアクティブ/アクティブ構成にすると、複数のネットワーク パスに分散するようにエンド ・ ユーザー トラフィックが許可されます。これにより、デバイスやネットワーク機器のシステム停止時の影響を受ける範囲が減少します。
  
インターネットと単一の ExpressRoute 回路を使用してバックアップとしてはお勧めしません。
  
### <a name="example-2-failover-and-high-availability"></a>例 2: フェールオーバーと高可用性を実現
  
Woodgrove Bank の複数の地理的なデザインでは、ルーティング、帯域幅、セキュリティの調査を行ったし、高可用性の確認を今すぐ移動する必要があります。Woodgrove が考える; 3 つのカテゴリをカバーすると高可用性を実現します。弾力性、信頼性、および冗長性です。
  
弾力性は、Woodgrove の障害から迅速に回復を使用できます。信頼性は、システム内で一貫した結果を提供するための Woodgrove を使用できます。冗長性は、Woodgrove をインフラストラクチャの 1 つまたは複数のミラー インスタンス間の移動に使用できます。
  
各エッジの構成では、Woodgrove 必要が冗長化されたファイアウォール、プロキシ、および ID。北アメリカでは、Woodgrove は、ダラスのデータ センターのエッジを 1 つ設定し、バージニア州のデータ センター内の別のエッジ構成します。それぞれの場所に冗長化設備には、その場所に復元機能が用意されています。
  
Woodgrove Bank のネットワーク構成は、いくつか重要な原則にに基づいて構成されています。
  
- 各地理的領域内では、複数の Azure ExpressRoute 回路があります。

- 領域内の各回路には、その地域内のネットワーク トラフィックのすべてをサポートできます。

- ルーティングは明確に 1 つまたはその他の利用可能度、場所によってパスを好むと。

- Azure ExpressRoute 回路間でのフェイル オーバーは、追加の構成または Woodgrove で必要な操作をしなくても自動的に行われます。

- インターネット回線間のフェイル オーバーは、追加の構成または Woodgrove で必要な操作をしなくても自動的に行われます。

物理および仮想レベルで冗長性を備えた、この構成では、Woodgrove Bank は信頼性の高い方法でローカルの弾力性、弾力性の地域、グローバル耐障害性を提供することです。Woodgrove では、インターネットへのフェイル オーバーが発生する可能性と、地域ごとの 1 つの Azure ExpressRoute 回路を評価した後は、この構成を選択します。
  
Woodgrove は、地域ごとの複数の Azure ExpressRoute 回路を持つことができませんだった場合も、アジア太平洋地域で Azure ExpressRoute 回路に北アメリカで発生したトラフィックのルーティングには許容できない待機時間と必要な DNS フォワーダー構成のレベルは追加複雑さを追加します。
  
バックアップの構成としてインターネットを活用することはお勧めしません。これは、Woodgrove の信頼性の原則に従って、接続を使用して不整合が発生してその結果を分割します。さらに、手動の構成はフェールオーバーが構成されている BGP 広告を検討して、NAT の構成、DNS の構成、およびプロキシの構成に必要になります。これは追加フェイル オーバーの複雑性が回復する時間が長くなるし、診断し、必要な手順のトラブルシューティングを行う能力が低下します。
  
計画し、トラフィック管理または Azure ExpressRoute を実装する方法について疑問があるでしょうか。他の[ネットワークとパフォーマンスのガイダンス](https://aka.ms/tune)や[Azure ExpressRoute の FAQ](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)を参照してください。
  
## <a name="working-with-azure-expressroute-providers"></a>Azure ExpressRoute プロバイダーを使用します。
<a name="BKMK_high-availability"> </a>

帯域幅、待ち時間、セキュリティ、および高可用性の計画に基づいて、回路の場所を選択します。配置するには最適な場所がわかったら回線が[現在の地域別のプロバイダーの一覧を確認](https://azure.microsoft.com/documentation/articles/expressroute-locations/)します。
  
最適な接続オプションでは、ポイント ツー ポイント、マルチポイント、またはホストを選択するのには、プロバイダーまたはプロバイダーを使用します。記憶を混在させるし、帯域幅およびその他の冗長コンポーネントがルーティングと高可用性の設計をサポートしている限り、接続オプションを一致させることができます。
  
戻るを使用することができます短いリンクを以下に示します。[https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>関連項目
<a name="BKMK_high-availability"> </a>

[Office 365 へのネットワーク接続](network-connectivity.md)
  
[Office 365 向け Azure ExpressRoute](azure-expressroute.md)
  
[Office 365 向け ExpressRoute の管理](managing-expressroute-for-connectivity.md)
  
[Office 365 向け ExpressRoute でのルーティング](routing-with-expressroute.md)
  
[Office 365 向け ExpressRoute での実装](implementing-expressroute.md)
  
[ExpressRoute に BGP のコミュニティを使用して Office 365 シナリオ (プレビュー)](bgp-communities-in-expressroute.md)
  
[メディアの品質とオンライン ビジネスの Skype でのネットワーク接続のパフォーマンス](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Skype のオンライン ビジネスのネットワークを最適化します。](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute とオンライン ビジネスの Skype での QoS](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[ExpressRoute を使用して通話フロー](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[ベースラインとパフォーマンス履歴を使用した、Office 365 のパフォーマンスのチューニング](performance-tuning-using-baselines-and-history.md)
  
[Office 365 のパフォーマンスに関するトラブルシューティングの計画](performance-troubleshooting-plan.md)
  
[Office 365 の URL と IP アドレス範囲](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 のネットワークとパフォーマンスの調整](network-planning-and-performance.md)
  
[Office 365 エンドポイントに関する FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
