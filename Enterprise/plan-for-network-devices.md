---
title: Office 365 サービスに接続するネットワーク デバイスの計画
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
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
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 概要:Office 365 に接続するために使用されるネットワーク容量、WAN アクセラレータ、負荷分散装置に関する考慮事項について説明します。
ms.openlocfilehash: 023eb3f5ed4d81d1d49d18c69ef8c81032fd5851
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933124"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Office 365 サービスに接続するネットワーク デバイスの計画

 **概要**:Office 365 に接続するために使用されるネットワーク容量、WAN アクセラレータ、負荷分散装置に関する考慮事項について説明します。
  
いくつかのネットワーク ハードウェアによっては、サポートされている同時セッションの数に制限があります。2,000 を超えるユーザーを持つ組織では、それらが他の Office 365 サービスのトラフィックを処理することを確認するようにネットワーク デバイスを監視するをお勧めします。簡易ネットワーク管理プロトコル (SNMP) 監視ソフトウェアは、この操作を行うのに役立ちます。

||
|:-----|
| この資料は、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://aka.ms/tune)の一部です。|

設置送信インターネット プロキシ設定は、クライアント アプリケーションで Office 365 サービスへの接続も影響します。マイクロソフトのクラウド サービスの Url とアプリケーションの接続を許可するネットワーク プロキシ デバイスを構成することもあります。すべての組織では異なります。準備マイクロソフトがこのプロセスおよび帯域幅の量を管理する方法を理解するため、[ケーススタディを読みます](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。
  
次の Skype のビジネスに役立つ記事があるビジネス設定の Skype の詳細について。
  
- [管理者の Skype をビジネス オンラインのサインインのエラーのトラブルシューティング](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [ビジネス用の Skype に接続できない場合や、オンプレミスのファイアウォールが接続をブロックするため、特定の機能は使用できません。](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> これらの設定の多くは、ビジネス固有の Skype です、ネットワークの構成に関する一般的なガイダンスはすべての Office 365 サービスに便利です。
  
## <a name="determining-network-capacity"></a>ネットワーク キャパシティの決定

接続上に存在するすべてのネットワーク デバイスには、キャパシティの限界があります。このようなデバイスとしては、クライアントおよびサーバーのネットワーク アダプター、ルーター、スイッチ、それらを相互接続するハブなどがあります。適切なネットワーク キャパシティとは、これらのネットワーク デバイスのいずれもが過負荷にならないことです。ネットワーク アクティビティを監視することは、すべてのネットワーク デバイス上の実際の負荷が最大容量以下であることを確認するために不可欠です。ネットワーク容量は、プロキシ デバイスの性能に影響を与えます。
  
ほとんどの状況では、インターネット接続の帯域幅は、トラフィック量の制限を設定します。トラフィックのピーク時にパフォーマンスは、インターネット リンクの過度の使用による可能性があります。このような場合は、ブランチ オフィス シナリオでは、低速のワイド エリア ネットワーク (WAN) リンク経由でブランチ オフィスの本社にプロキシ デバイスにブランチ オフィスのプロキシ サーバー コンピューターが接続されているにも適用されます。
  
ネットワーク容量をテストするには、プロキシのネットワーク インターフェイスのネットワーク活動を監視します。すべてのネットワーク インターフェイスの最大帯域幅の 75% 以上である場合が不適切なネットワーク インフラストラクチャの帯域幅を増やすことを検討してください。または、HTTP 圧縮などの高度な機能の使用を検討します。
  
## <a name="wan-accelerators"></a>WAN アクセラレータ

組織は、ワイド エリア ネットワーク (WAN) アクセラレータ プロキシ ・ アプライアンスを使用して、Office 365 サービスにアクセスするときに問題が発生する可能性があります。または、ユーザーが Office 365 にアクセスするとき、一貫した機能できるようにするのにはの複数のネットワーク デバイスを最適化する必要があります。などの Office 365 サービスは、いくつかの Office 365 のコンテンツと TCP ヘッダーを暗号化します。デバイスは、このようなトラフィックを処理することがない場合があります。
  
[WAN 最適化コント ローラーの使用、または Office 365 とのトラフィックの検査とデバイス](https://support.microsoft.com/kb/2690045)に関するサポートの声明を読みます。
  
## <a name="hardware-and-software-load-balancing-devices"></a>ハードウェアおよびソフトウェア負荷分散デバイス

Active Directory フェデレーション サービス (AD FS) サーバーおよび/または Exchange ハイブリッド サーバーに対するリクエストを分散させるために、ハードウェア負荷分散 (HLB) またはネットワーク負荷分散 (NLB) ソリューションを使用する必要があります。負荷分散デバイスは社内サーバーへのネットワーク トラフィックを制御します。これらのサーバーはシングル サインオンおよび Exchange ハイブリッド展開の可用性を確保するうえで重要です。
  
Windows Server に組み込まれたソフトウェア ・ ベースの NLB ソリューションを提供しています。Office 365 には、負荷分散を実現するには、このソリューションがサポートされています。
  
## <a name="firewalls-and-proxies"></a>ファイアウォールとプロキシ

ファイアウォール、およびデバイスと回路の選択に関する詳細については、 [Office 365 の管理の端点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)、 [Office 365 へのネットワーク接続](network-connectivity.md)、および[Office 365 エンドポイントに関する FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)を参照して、Office 365 への接続にプロキシを設定する方法についての詳細については。
  
## <a name="see-also"></a>関連項目

[Office 365 サービスの展開アドバイザー](deployment-advisors-for-office-365.md)
