---
title: Microsoft 365 のネットワーク計画とパフォーマンス チューニング
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_Enterprise
f1.keywords:
- CSH
search.appverid:
- MET150
ms.assetid: e5f1228c-da3c-4654-bf16-d163daee8848
ms.custom:
- seo-marvel-apr2020
- Adm_O365
description: この記事では、Microsoft 365 のネットワーク帯域幅要件を計画し、パフォーマンスを微調整およびトラブルシューティングする方法について説明します。
ms.openlocfilehash: 4942d2d9d36123465dd15aecf6e72988c9952037
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606743"
---
# <a name="network-planning-and-performance-tuning-for-microsoft-365"></a>Microsoft 365 のネットワーク計画とパフォーマンス チューニング
最初にを展開するか、Microsoft 365 に移行する前に、これらのトピックの情報を使用して必要な帯域幅を推定し、Microsoft 365 に展開または移行するのに十分な帯域幅があることをテストして確認することができます。 概要については、「 [Microsoft 365 のネットワークと移行の計画](network-and-migration-planning.md)」を参照してください。
  
|||||
|:-----|:-----|:-----|:-----|
|**ネットワークの計画** <br/> ![ネットワーク](media/5e9dcd06-601b-4b28-88dc-f524e7548794.png)           <br/> |高速の接続とページが短時間で読み込まれるようにするか。  <br/> 「 [Microsoft 365 での最適な接続性とパフォーマンスを得る」](https://aka.ms/o365perfprinciples)をお読みください。 <br/> 概念については、「 [Microsoft 365 のネットワーク接続の概要」](https://docs.microsoft.com/office365/enterprise/office-365-networking-overview)を参照してください。  <br/> |**ネットワークの測定** <br/> ![Roi](media/d690a132-4884-40eb-a918-526bb3dff3cc.png)           <br/> |「Microsoft 365 のパフォーマンスのチューニング」を参照してください。[ベースラインとパフォーマンスの履歴](performance-tuning-using-baselines-and-history.md)と[パフォーマンスのトラブルシューティング計画](performance-troubleshooting-plan.md)を使用した microsoft 365。  <br/> これらのツールを使用し[て、既存のネットワークを評価](network-and-migration-planning.md#calculators)します。  <br/> |
|**ベスト プラクティス** <br/> ![ベスト プラクティス](media/2a659a5c-1007-47d3-a6c6-a19e018ab29b.png)           <br/> |[Microsoft 365 のネットワーク計画と移行のパフォーマンスを向上させるためのベストプラクティス](network-and-migration-planning.md#BestPractices)。 すぐにユーザーのサポートを開始する必要がありますか。 [低速のネットワークで Office 365 を使用するためのベストプラクティス](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)を参照してください。  <br/> [Microsoft 365 のネットワーク接続の原則](https://aka.ms/o365networkingprinciples)は、microsoft 365 ネットワーク接続を安全に最適化するための最新のガイダンスを理解するのに役立ちます。  <br/> |**Reference** <br/> ![ブックまたはジャーナル](media/56dff3c1-f605-48d8-811f-7d13ce639ecd.png)           <br/> |IP アドレスやポートの一覧などの詳細を必要とするかどうか。 [Microsoft 365 のネットワーク計画リファレンス](network-and-migration-planning.md#NetReference)を参照してください。  <br/> |
|![「エンタープライズアーキテクトのための Microsoft クラウドネットワーク」のポスターを参照してください。](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)           <br/> |Microsoft 365 およびその他の Microsoft クラウドプラットフォームおよびサービスに対してネットワークを最適化するための手順については、「[エンタープライズアーキテクトのための Microsoft クラウドネットワーク](https://aka.ms/cloudarchnetworking)」のポスターを参照してください。  <br/> |
   
## <a name="performance-tuning-and-troubleshooting-resources-for-microsoft-365"></a>Microsoft 365 のパフォーマンスのチューニングとトラブルシューティングのリソース
<a name="apptuning"> </a>

Microsoft 365 を展開した後で、このセクションのトピックを使用してパフォーマンスを最適化できます。 パフォーマンス低下が発生した場合は、以下のトピックを使用して問題のトラブルシューティングを行うこともできます。
  
 **[Office 365 のパフォーマンスをチューニング](tune-office-365-performance.md)** する: office 365 でのネットワークアドレス変換の使用の詳細については、「 [office 365 を使用した NAT サポート](nat-support-with-office-365.md)」を参照してください。 また、 [Office 365 のネットワーク接続を最適化しトラブルシューティングするための上位10のヒント](https://docs.microsoft.com/archive/blogs/onthewire/top-10-tips-for-optimising-troubleshooting-your-office-365-network-connectivity)を参照してください。 
  
 **[Exchange online のパフォーマンスをチューニング](tune-exchange-online-performance.md)** する: exchange online のパフォーマンスを微調整するには、次の記事を使用します。 
  
 **[Skype for Business online のパフォーマンスをチューニング](tune-skype-for-business-online-performance.md)** する: 以下の記事を使用して、Skype For business online のパフォーマンスを微調整します。 
  
 **[Sharepoint online のパフォーマンスをチューニング](tune-sharepoint-online-performance.md)** する: sharepoint online のパフォーマンスを微調整するには、以下の記事を使用します。 
  
 **[Project online のパフォーマンスをチューニング](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)** する: この記事を使用して、project online のパフォーマンスを微調整します。 
