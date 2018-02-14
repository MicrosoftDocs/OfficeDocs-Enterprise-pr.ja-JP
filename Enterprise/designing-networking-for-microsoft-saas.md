---
title: "Microsoft SaaS のためのネットワーク デザイン"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "概要: Office 365、Microsoft Intune、Dynamics 365 を含む Microsoft の SaaS サービスにアクセスするためにネットワークを最適化する方法を理解します。"
ms.openlocfilehash: e4d83f9ab88408b3eb5ca98379bbc709ec8f31a7
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="designing-networking-for-microsoft-saas"></a>Microsoft SaaS のためのネットワーク デザイン

 **概要:** Office 365、Microsoft Intune、Dynamics 365 を含む Microsoft の SaaS サービスにアクセスするためにネットワークを最適化する方法を理解します。
  
Microsoft SaaS サービス向けにネットワークを最適化するには、インターネット エッジ、クライアント デバイス、および標準の IT 運用を慎重に分析する必要があります。
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Microsoft SaaS サービスを利用するためのネットワークの準備の手順

Microsoft SaaS サービス向けにネットワークを最適化するには、次の手順に従います。
  
1. [Microsoft クラウド接続の一般的な要素](common-elements-of-microsoft-cloud-connectivity.md)の「**Microsoft クラウド サービスを利用するためのネットワークの準備の手順**」セクションを読んでください。
    
2. プロキシ サーバーの推奨事項を使用して、Microsoft SaaS サービス向けにインターネット出口を最適化します。
    
3. 近接性および場所に関する推奨事項を使用して、インターネット スループットを最適化します。
    
4. クライアント使用の考慮事項に基づいて配置されたクライアント コンピューターおよびイントラネットのパフォーマンスを最適化します。
    
5. 必要に応じて、IT 運用上の考慮事項に基づき、データの移行と同期のパフォーマンスを最適化します。
    
## <a name="internet-edge-considerations"></a>インターネット エッジの考慮事項

ここでは、インターネット エッジおよびMicrosoft SaaS サービスへのスループットを最適化するための考慮事項を説明します。
  
**図 1:マイクロソフト SaaS サービスの接続オプション**

![図 1:マイクロソフト SaaS サービスの接続オプション](images/Network_Poster/SaaS1.png)
  
図 1 はインターネット パイプまたは ExpressRoute によって Microsoft SaaS サービスに接続しているオンプレミスのネットワークを示しています。
  
プロキシ サーバーを最適化するための推奨事項を以下に示します。
  
- WPAD、PAC、または GPO を使用して Web クライアントを構成します
    
- SSL インターセプトを使用しません
    
- PAC ファイルを使用して、Microsoft SaaS サービスの DNS 名に関するプロキシをバイパスします
    
- CRL/OCSP 検証のためのトラフィックを許可します
    
確認する必要のあるプロキシ サーバーのボトルネックを以下に示します。
  
- 不十分な常時接続 (Outlook)
    
- 容量の不足
    
- オフ ネットワーク評価の実行
    
- 認証の要求
    
- UDP トラフィックがサポートされていない (Skype for Business)
    
近接性と場所に関する推奨事項を以下に示します。
  
- プライベート WAN によってインターネット トラフィックをルーティングしないようにします
    
- 地域外ユーザーに対して地域内 DNS とインターネット トラフィック フローを使用します
    
- Office 365 のための高帯域幅、および Azure サービスとの同時接続のために、ExpressRoute を使用します
    
Office 365 のトラフィックに必要な送信ポートを以下に示します。
  
- TCP 80 (CRL/OCSP チェックのため)
    
- TCP 443
    
- UDP 3478
    
- TCP 5223
    
- TCP 50000 ～ 59999
    
- UDP 50000 ～ 59999
    
## <a name="client-usage-considerations"></a>クライアント使用に関する考慮事項

最初に、次のようなクライアントが使用するサービスのセットを構成します。
  
- Azure Active Directory
    
- Office 365
    
  - Office クライアント アプリ
    
  - SharePoint Online
    
  - Exchange Online
    
  - Skype for Business
    
- Microsoft Intune
    
- Dynamics 365
    
クライアント コンピューターに関して、以下の点を決定します。
  
- 同時に接続できる最大数 (時刻、季節、使用状況のピークと谷)
    
- ピーク時に必要な帯域幅の合計
    
- インターネット出口デバイスの待機時間
    
- 元の国 vs. データセンター コロケーションの国
    
各種のクライアント (PC、スマート フォン、タブレット) に関して、以下の現状を確認します。
  
- オペレーティング システム
    
- インターネット ブラウザー
    
- TCP/IP スタック
    
- ネットワーク ハードウェア
    
- ネットワーク ハードウェアの OS ドライバー
    
- 更新と修正プログラムがインストールされている
    
さらに、イントラネット接続のスループット (有線、ワイヤレス、または VPN) を最適化します。
  
詳細については、[Office 365 の NAT サポート](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9)をご覧ください。
  
ExpressRoute with Office 365 の使用に関する最新の推奨事項については、「[Office 365 向け Azure ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)」をご覧ください。
  
イントラネットのパフォーマンスを最適化するには、次の操作を行います。
  
- ツールを使用して、インターネット エッジ デバイス (PsPing、Ping、Tracert、TraceTCP、ネットワーク モニター) へのラウンド トリップ時間(RTT) を計測します
    
- フロー プロトコルを使用して出口パスの解析を行います
    
- 中間デバイスの分析 (使用年数、正常性など) を実行します
    
詳細については、[PsPing ツール](https://technet.microsoft.com/sysinternals/jj729731.aspx) を参照してください。
  
## <a name="it-operations-considerations"></a>IT 運用上の考慮事項

Microsoft SaaS サービスで IT ワークロードを操作する場合の考慮事項を以下に示します。
  
### <a name="one-time-migrations"></a>ワン タイム移行

ワン タイム移行の例としては、クラウド ベース アプリケーションまたはアーカイブ ストレージのための一括データ移行が挙げられます。
  
ワン タイム移行のためにネットワークを最適化するには:
  
- ネットワーク使用状況のピーク時およびコンピューターのパッチ処理時を避けます
    
- ベースラインおよびパイロットであるべきで、実際に移行する前にネットワークの正常性を評価し、問題を解決する必要があります
    
- 将来の移行のために事後分析を行います
    
### <a name="ongoing-synchronizations"></a>継続的な同期

継続的な同期の例として、ディレクトリ情報、設定、またはファイルがあります。
  
継続的な同期のためにネットワークを最適化するには:
  
- ネットワーク帯域幅監視システムが機能していることを確認し、収集したエラーを解決するか、消します
    
- 帯域幅監視の結果に基づいて、ネットワークの変更の必要性 (スケール アップまたはアウト、新しい回線、またはデバイスの追加) を判断します。
    
詳細については、以下を参照してください。
  
- [Office 365 のネットワークと移行の計画](https://aka.ms/tune)
    
- [Office 365 のパフォーマンス管理 Microsoft Virtual Academy コース](https://aka.ms/o365perf)
    
- [Office 365 用 ExpressRoute](https://aka.ms/expressrouteoffice365)

## <a name="next-step"></a>次の手順

[Microsoft Azure PaaS のためのネットワーク デザイン](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>関連項目

[エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)



