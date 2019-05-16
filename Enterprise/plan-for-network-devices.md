---
title: Office 365 サービスに接続するネットワーク デバイスの計画
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
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
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: '概要: Office 365 への接続に使用されるネットワーク容量、WAN アクセラレータ、および負荷分散デバイスに関する考慮事項について説明します。'
ms.openlocfilehash: 6ff63232d4efe581ed4a6ba0a83730a5362ecff7
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069373"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Office 365 サービスに接続するネットワーク デバイスの計画

 **概要**: Office 365 への接続に使用されるネットワーク容量、WAN アクセラレータ、および負荷分散デバイスに関する考慮事項について説明します。
  
ネットワークハードウェアによっては、サポートされている同時セッション数に制限がある場合があります。 ユーザー数が2000を超える組織では、ネットワークデバイスを監視して、追加の Office 365 サービストラフィックを処理できることを確認することをお勧めします。 簡易ネットワーク管理プロトコル (SNMP) 監視ソフトウェアを使用すると、この操作を行うことができます。

||
|:-----|
| この記事は[、Office 365 のネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)に含まれています。|

オンプレミスの送信インターネットプロキシ設定も、クライアントアプリケーションの Office 365 サービスへの接続に影響します。 また、Microsoft クラウドサービスの Url とアプリケーションへの接続を許可するように、ネットワークプロキシデバイスを構成する必要もあります。 すべての組織が異なります。 Microsoft がこのプロセスと、プロビジョニングする帯域幅の量をどのように管理しているかを把握するには、[ケーススタディをお読み](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)ください。
  
次の Skype for Business ヘルプの記事には、Skype for Business の設定に関する詳細が記載されています。
  
- [管理者向けの Skype for Business Online サインインエラーのトラブルシューティング](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [オンプレミスのファイアウォールによって接続がブロックされているため、Skype for Business に接続できないか、一部の機能が動作しません。](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> これらの設定の多くは Skype for Business に固有のものですが、ネットワーク構成に関する一般的なガイダンスはすべての Office 365 サービスで役立ちます。
  
## <a name="determining-network-capacity"></a>ネットワークの容量を決定する

接続上に存在するすべてのネットワークデバイスに容量の制限があります。 これらのデバイスには、それらを相互に接続するクライアントおよびサーバーのネットワークアダプター、ルーター、スイッチ、ハブが含まれます。 十分なネットワークの容量は、飽和していないことを意味します。 ネットワークアクティビティを監視することは、すべてのネットワークデバイスの実際の負荷が最大容量を下回っていることを確認するために不可欠です。 ネットワーク容量は、プロキシデバイスのパフォーマンスに影響します。
  
ほとんどの場合、インターネット接続の帯域幅はトラフィック量の制限を設定します。 ピークトラフィック時間中のパフォーマンスが低い場合は、インターネットリンクの過剰な使用が原因である可能性があります。 この状況は、ブランチオフィスのプロキシサーバーコンピューターが低速のワイドエリアネットワーク (WAN) リンクを介して支社の本社のプロキシデバイスに接続されている場合にも当てはまります。
  
ネットワーク容量をテストするには、プロキシネットワークインターフェイスでネットワークアクティビティを監視します。 ネットワークインターフェイスの最大帯域幅が 75% を超えている場合は、ネットワークインフラストラクチャの帯域幅が不十分であることを考慮してください。 または、HTTP 圧縮などの高度な機能を使用することを検討してください。
  
## <a name="wan-accelerators"></a>WAN アクセラレータ

ワイドエリアネットワーク (WAN) アクセラレータプロキシアプライアンスを使用している場合は、Office 365 サービスにアクセスすると問題が発生することがあります。 ユーザーが Office 365 にアクセスするときに一貫した環境を確保するために、ネットワークデバイスを最適化する必要がある場合があります。 たとえば、Office 365 サービスは一部の Office 365 コンテンツと TCP ヘッダーを暗号化します。 デバイスがこの種のトラフィックを処理できない可能性があります。
  
「 [Office 365 での WAN 最適化コントローラーまたはトラフィック/検査デバイスの使用](https://support.microsoft.com/kb/2690045)に関するサポートに関する声明」をお読みください。
  
## <a name="hardware-and-software-load-balancing-devices"></a>ハードウェアおよびソフトウェア負荷分散デバイス

組織は、ハードウェアロードバランサー (HLB) またはネットワーク負荷分散 (NLB) ソリューションを使用して、Active Directory フェデレーションサービス (AD FS) サーバーまたは Exchange ハイブリッドサーバーに要求を分散する必要があります。 負荷分散デバイスは、社内サーバーへのネットワークトラフィックを制御します。 これらのサーバーは、シングルサインオンと Exchange ハイブリッド展開の可用性を確保するうえで非常に重要です。
  
Windows Server に組み込まれているソフトウェアベースの NLB ソリューションを提供しています。 Office 365 は、このソリューションをサポートすることによって負荷分散を実現します。
  
## <a name="firewalls-and-proxies"></a>ファイアウォールとプロキシ

Office 365 に接続するためのファイアウォールとプロキシの構成の詳細については、「 [office 365 エンドポイントの管理](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)」、「 [office 365 へのネットワーク接続](network-connectivity.md)」、および「 [office 365 エンドポイント](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)に関する FAQ」を参照して、デバイスと回線の選択について確認してください。
  
## <a name="see-also"></a>関連項目

[Office 365 サービスの展開アドバイザー](deployment-advisors-for-office-365.md)
