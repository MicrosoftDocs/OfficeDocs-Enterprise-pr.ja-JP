---
title: Office 365 のネットワーク計画とパフォーマンスのチューニング
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/23/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
ms.assetid: e5f1228c-da3c-4654-bf16-d163daee8848
description: Microsoft Office 365 のネットワーク帯域幅要件を計画することができます。次のように展開している、ここで微調整を返し、Office 365 のパフォーマンスのトラブルシューティングを行います。
ms.openlocfilehash: da8618381664a0ddf4d670cfbb2907236c468ac0
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22915892"
---
# <a name="network-planning-and-performance-tuning-for-office-365"></a>Office 365 のネットワーク計画とパフォーマンスのチューニング
初めて展開した場合、または Office 365 に移行する前に情報を使用して、これらのトピックで必要な帯域幅を推定するし、テストし、十分な帯域幅を展開するか、Office 365 に移行することを確認します。概要についてを参照してください:[ネットワークと Office 365 の移行計画](network-and-migration-planning.md)。
  
|||||
|:-----|:-----|:-----|:-----|
|**ネットワークの計画** <br/> ![ネットワーク](media/5e9dcd06-601b-4b28-88dc-f524e7548794.png)           <br/> |高速接続し、迅速にロードするページをしますか。  <br/> [最適な接続および Office 365 のパフォーマンスを取得する](https://aka.ms/o365perfprinciples)読み取り <br/> 監視の概念を理解するのには、 [Office 365 を使用して、パフォーマンスを最適化するためにネットワーク接続を把握します。](https://blogs.office.com/2015/03/04/understanding-network-connectivity-optimize-performance-office-365/)  <br/> |**ネットワークの測定** <br/> ![[電卓] ](media/d690a132-4884-40eb-a918-526bb3dff3cc.png)           <br/> |[ベースラインとパフォーマンスの履歴を使用して Office 365 のパフォーマンス ・ チューニング](performance-tuning-using-baselines-and-history.md)[パフォーマンスのトラブルシューティング Office 365 のプラン](performance-troubleshooting-plan.md)を参照してください。  <br/> [既存のネットワークを評価](network-and-migration-planning.md#calculators)するためにこれらのツールを使用します。  <br/> |
|**ベスト プラクティス** <br/> ![ベスト ・ プラクティス](media/2a659a5c-1007-47d3-a6c6-a19e018ab29b.png)           <br/> |[最適なネットワークを計画し、Office 365 に移行、パフォーマンスが向上](network-and-migration-planning.md#BestPractices)します。ユーザーをすぐに支援を開始するか。[低速のネットワーク上の Office 365 を使用するためのベスト プラクティス](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)を参照してください。<br/> [Office 365 のネットワーク接続性の原則](https://aka.ms/o365networkingprinciples)を使用すると、Office 365 のネットワーク接続を安全に最適化するため、最新のガイダンスを理解できます。  <br/> |**参照** <br/> ![帳または仕訳帳](media/56dff3c1-f605-48d8-811f-7d13ce639ecd.png)           <br/> |IP アドレスとポートのリストのように、詳細をしますか。[ネットワーク計画の Office 365 への参照](network-and-migration-planning.md#NetReference)を参照してください。<br/> |
|![エンタープライズ設計者のポスターのクラウドのネットワークを参照してください。](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)           <br/> |、Office 365 とその他のマイクロソフトのクラウド プラットフォームおよびサービスのネットワークを最適化するための手順は、[エンタープライズ設計者向けのマイクロソフト クラウド ネットワーク](https://aka.ms/cloudarchnetworking)のポスターを参照してください。  <br/> |
   
## <a name="performance-tuning-and-troubleshooting-resources-for-office-365"></a>Office 365 のパフォーマンス チューニングとトラブルシューティングのリソース
<a name="apptuning"> </a>

Office 365 の展開を作成したら、このセクションのトピックを使用して、パフォーマンスを最適化できます。パフォーマンスの低下が発生した場合は、問題のトラブルシューティングにもこれらのトピックを使用できます。
  
 **[Office 365 のチューニングのパフォーマンス](tune-office-365-performance.md)**: Office 365 でネットワーク アドレス変換を使用する方法の詳細については、 [NAT は、Office 365 のサポート](nat-support-with-office-365.md)を参照してください。Paul Collinge、 [10 のヒントを最適化して、Office 365 のネットワーク接続のトラブルシューティング](https://blogs.technet.com/b/onthewire/archive/2014/06/18/top-10-tips-for-optimising-amp-troubleshooting-your-office-365-network-connectivity.aspx)を見ても、です。 
  
 **[Exchange Online のチューニングのパフォーマンス](tune-exchange-online-performance.md)**: これらの記事を使用して、Exchange のオンライン パフォーマンスを微調整します。 
  
 **[オンライン ビジネスのパフォーマンスのチューニングの Skype](tune-skype-for-business-online-performance.md)**: Skype のオンライン ビジネスのパフォーマンスを微調整するのにはこれらの資料を使用します。 
  
 **[パフォーマンスのチューニングの SharePoint Online](tune-sharepoint-online-performance.md)**: SharePoint Online のパフォーマンスを微調整するのにはこれらの資料を使用します。 
  
 **[パフォーマンスのチューニングのプロジェクトのオンライン](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)**: オンライン プロジェクトのパフォーマンスを微調整するのにはこの資料を使用します。 
  

