---
title: Office 365 のネットワーク接続の評価
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: ITPro
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
description: Office 365 は、世界中のお客様がインターネット接続を使用してサービスに接続できるように設計されています。 サービスの進化に伴って、Office 365 のセキュリティ、パフォーマンス、および信頼性は、インターネットを使用してサービスへの接続を確立するお客様によって改善されています。
ms.openlocfilehash: 3ea80ddccaf9fabbe158a10f0af1d35dbf3a9889
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "34724827"
---
# <a name="assessing-office-365-network-connectivity"></a>Office 365 のネットワーク接続の評価

Office 365 は、世界中のお客様がインターネット接続を使用してサービスに接続できるように設計されています。 サービスの進化に伴って、Office 365 のセキュリティ、パフォーマンス、および信頼性は、インターネットを使用してサービスへの接続を確立するお客様によって改善されています。
  
Office 365 の使用を計画しているお客様は、展開プロジェクトの一環として、既存および予測されるインターネット接続のニーズを評価する必要があります。 エンタープライズクラスの展開の場合は、信頼性が高く、適切なサイズのインターネット接続は、Office 365 の機能とシナリオの重要な部分です。
  
ネットワークの評価は、サイズと基本設定に応じて、多くの人や組織が行うことができます。 評価のネットワークスコープは、展開プロセスのどこにいるかによっても異なります。 ネットワーク評価を実行するために必要なことを理解するのに役立つように、ネットワーク評価ガイドを作成しました。使用可能なオプションを理解するのに役立ちます。 この評価では、Office 365 を正常に導入できるようにするために、展開プロジェクトにどのような手順とリソースを追加する必要があるかを決定します。
  
[Skype Operations Framework](https://www.skypeoperationsframework.com/)で規定されているような包括的なネットワーク評価は、実装の詳細に加えて、ネットワーク設計の課題に対するソリューションを提供します。 ほとんどのネットワーク評価では、Office 365 へのネットワーク接続が可能であることを示しています。これは、小規模な構成や、既存のネットワークとインターネットの出口インフラストラクチャに[対する設計の変更](https://aka.ms/manageo365endpoints)に対応できます。

一部の評価では、Office 365 へのネットワーク接続が必要になります。これには、ネットワークコンポーネントへの追加の投資が必要になります。 たとえば、WAN 帯域幅への投資、または Office 365 へのインターネット接続をサポートするための最適化されたルーティングインフラストラクチャ。 場合によっては、Office 365 へのネットワーク接続が表示されることがあります。 [Skype For Business Online メディア品質](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)などのシナリオの規制またはパフォーマンス要件の影響を受ける可能性があります。 これらの追加要件により、インターネット接続インフラストラクチャ、ルーティングの最適化、および特別な直接接続への投資が可能になります。
  
> [!NOTE]
> Office 365 の ExpressRoute を使用するには、Microsoft の承認が必要です。 Microsoft は、お客様の規制要件で直接的な接続が義務付けられている場合に限り、お客様のすべての要求を見直し、Office 365 の ExpressRoute の使用を承認します。 このような要件がある場合は、テキストの抜粋と web リンクを入力してください。これは、Microsoft レビューを開始するために、 [Office 365 の ExpressRoute の要求フォーム](https://aka.ms/O365ERReview)に直接接続する必要があることを意味します。 承認されていないサブスクリプション Office 365 のルートフィルターを作成しようとすると、[エラーメッセージ](https://support.microsoft.com/kb/3181709)が表示されます。
  
Office 365 のネットワーク評価を計画する際に考慮すべき重要な点は次のとおりです。
  
- Office 365 は、パブリックインターネット上で動作する、セキュリティで保護された、信頼性の高い高パフォーマンスのサービスです。 弊社は、サービスのこれらの側面を強化するための投資を継続しています。 すべての Office 365 サービスは、インターネット接続経由で利用できます。

- Microsoft は、可用性、グローバルなリーチ、およびインターネットベースの接続のパフォーマンスなど、Office 365 のコア要素を継続的に最適化しています。 たとえば、多くの Office 365 サービスでは、拡張されたインターネット上のエッジノードのセットが利用されます。 このエッジネットワークによって、インターネット経由で接続する際に最適な類似性とパフォーマンスが提供されます。

- Skype for Business Online の音声、ビデオ、会議の機能など、含まれるサービスのいずれかに Office 365 の使用を検討する場合、お客様は、Skype Operations Framework を使用してエンドツーエンドのネットワーク評価を完了し、要件を満たす必要があります。 これらのお客様には、ExpressRoute を含む、クラウド接続の特定の要件を満たすためのいくつかのオプションがあります。

Microsoft [Office 365 のネットワークパフォーマンスを最適化](https://msdn.microsoft.com/en-us/library/mt450488.aspx)する microsoft のケーススタディを参照してください。 Office 365 を評価していて、ネットワーク評価の開始位置がわからない場合や、解決のためにサポートが必要なネットワーク設計の課題が見つかった場合は、Microsoft アカウントチームと協力してください。
  
また、「 [office 365 のネットワーク接続の原則](https://aka.ms/o365networkingprinciples)」を参照して、office 365 トラフィックを安全に管理し、最適なパフォーマンスを得るための接続の原則について理解します。 この記事は、Office 365 ネットワーク接続を安全に最適化するための最新のガイダンスを理解するのに役立ちます。

## <a name="the-office-365-network-onboarding-tool"></a>Office 365 ネットワークオンボードツール

新しい概念実証 (POC) ツールである[office 365 ネットワークオンボードツール](https://aka.ms/netonboard)を使用して、特定のユーザーの場所と Office 365 の間で、ネットワーク接続の向上に関する具体的なガイダンスを提供する基本的な接続テストを実行することができます。

ネットワークオンボードツールは、次の処理を行います。

- 場所を検出するか、テストする場所を指定することができます。
- ネットワークの出口の場所を確認します。
- 最も近い Office 365 サービスのフロントドアへのネットワークパスをテストします。

このツールには、次の情報が表示されます。

- [結果と影響] タブ
  - 使用中のサービスのフロントドアのマップ上の場所
  - 接続を最適化するために、他のサービスのフロントドアのマップ上にある場所
  - 近辺の他の Office 365 のお客様と比較した場合の相対的なパフォーマンス
- [詳細とソリューション] タブ
  - 市区町村および国別のユーザーの場所
  - 市区町村、都道府県、および国別のネットワーク出口の場所
  - ユーザーからネットワークの出口までの距離
  - Office 365 Exchange Online サービスのフロントドアの場所
  - ユーザーの場所に最適な Office 365 Exchange Online サービスのフロントドア
  - 優れたパフォーマンスを備えた、メトロエリア内のお客様

Office 365 ネットワークオンボードツールリリースに関する情報を参照して、 [office 365 Network Performance TOOL POC リリース](https://techcommunity.microsoft.com/t5/Office-365-Networking/Office-365-Network-Performance-tool-POC-release/m-p/319579#M102)ブログ投稿にフィードバックを提供することができます。 このツールおよびその他の Office 365 ネットワーク更新プログラムに関する今後の更新プログラムについては、「 [office 365 のネットワーク](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)ブログ」に掲載されています。
  
次の短いリンクを使用して、に戻ることができます。 [ https://aka.ms/o365networkconnectivity](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>関連項目

[Office 365 のネットワーク接続の概要](office-365-networking-overview.md)

[Office 365 ネットワーク接続の原則](https://aka.ms/o365networkingprinciples)

[Office 365 エンドポイントの管理](managing-office-365-endpoints.md)

[Office 365 の URL と IP アドレスの範囲](urls-and-ip-address-ranges.md)

[Office 365 IP アドレスと URL の Web サービス ](office-365-ip-web-service.md)

[Office 365 のネットワークとパフォーマンスのチューニング](network-planning-and-performance.md)
