---
title: Office 365 のネットワーク計画とパフォーマンスのチューニング
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/15/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
ms.assetid: e5f1228c-da3c-4654-bf16-d163daee8848
description: Microsoft Office 365 のネットワーク帯域幅要件を計画するのに役立つ情報を示します。 展開後、Office 365 のパフォーマンスを微調整してトラブルシューティングを行うために、ここに戻ってください。
ms.openlocfilehash: c7ea169fbb39a16612c957f0d0275de60c83de1e
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616740"
---
# <a name="network-planning-and-performance-tuning-for-office-365"></a>Office 365 のネットワーク計画とパフォーマンス チューニング
Office 365 に初めて展開するか、Office に移行する前に、これらのトピックの情報を使用して必要な帯域幅を推定し、Office 365 に展開または移行するのに十分な帯域幅があるかどうかをテストして確認することができます。 概要については、「 [Office 365 のネットワークと移行の計画](network-and-migration-planning.md)」を参照してください。
  
|||||
|:-----|:-----|:-----|:-----|
|**ネットワークの計画** <br/> ![ネットワーク](media/5e9dcd06-601b-4b28-88dc-f524e7548794.png)           <br/> |高速の接続とページが短時間で読み込まれるようにするか。  <br/> 「 [Office 365 での最適な接続性とパフォーマンスを得る」](https://aka.ms/o365perfprinciples)を参照してください。 <br/> [Office 365 のネットワーク接続の概要](https://docs.microsoft.com/en-us/office365/enterprise/office-365-networking-overview)を読み、概念を理解してください。  <br/> |**ネットワークの測定** <br/> ![Roi](media/d690a132-4884-40eb-a918-526bb3dff3cc.png)           <br/> |Office 365 のベースラインとパフォーマンスの履歴および[パフォーマンスのトラブルシューティング計画](performance-troubleshooting-plan.md)[を使用して、「office 365 のパフォーマンスのチューニング](performance-tuning-using-baselines-and-history.md)」を参照してください。  <br/> これらのツールを使用し[て、既存のネットワークを評価](network-and-migration-planning.md#calculators)します。  <br/> |
|**ベスト プラクティス** <br/> ![ベスト プラクティス](media/2a659a5c-1007-47d3-a6c6-a19e018ab29b.png)           <br/> |[Office 365 のネットワーク計画と移行のパフォーマンスを向上させるためのベストプラクティス](network-and-migration-planning.md#BestPractices)。 すぐにユーザーのサポートを開始する必要がありますか。 [低速のネットワークで Office 365 を使用するためのベストプラクティス](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)を参照してください。  <br/> [Office 365 のネットワーク接続の原則](https://aka.ms/o365networkingprinciples)は、office 365 のネットワーク接続を安全に最適化するための最新のガイダンスを理解するのに役立ちます。  <br/> |**Reference** <br/> ![ブックまたはジャーナル](media/56dff3c1-f605-48d8-811f-7d13ce639ecd.png)           <br/> |IP アドレスやポートの一覧などの詳細を必要とするかどうか。 「 [Office 365 のネットワーク計画リファレンス」を](network-and-migration-planning.md#NetReference)参照してください。  <br/> |
|![「エンタープライズアーキテクトのための Microsoft クラウドネットワーク」のポスターを参照してください。](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)           <br/> |Office 365 およびその他の Microsoft クラウドプラットフォームおよびサービスに対してネットワークを最適化するための手順については、「[エンタープライズアーキテクトのための Microsoft クラウドネットワーク](https://aka.ms/cloudarchnetworking)」のポスターを参照してください。  <br/> |
   
## <a name="performance-tuning-and-troubleshooting-resources-for-office-365"></a>Office 365 のパフォーマンスのチューニングとトラブルシューティングのリソース
<a name="apptuning"> </a>

Office 365 を展開した後で、このセクションのトピックを使用してパフォーマンスを最適化することができます。 パフォーマンス低下が発生した場合は、以下のトピックを使用して問題のトラブルシューティングを行うこともできます。
  
 **[Office 365 のパフォーマンスをチューニング](tune-office-365-performance.md)** する: office 365 でのネットワークアドレス変換の使用の詳細については、「 [office 365 を使用した NAT サポート](nat-support-with-office-365.md)」を参照してください。 また、Paul Collinge で[Office 365 のネットワーク接続を最適化およびトラブルシューティングするための上位10のヒント](https://blogs.technet.com/b/onthewire/archive/2014/06/18/top-10-tips-for-optimising-amp-troubleshooting-your-office-365-network-connectivity.aspx)を参照してください。 
  
 **[Exchange online のパフォーマンスをチューニング](tune-exchange-online-performance.md)** する: exchange online のパフォーマンスを微調整するには、次の記事を使用します。 
  
 **[Skype for Business online のパフォーマンスをチューニング](tune-skype-for-business-online-performance.md)** する: 以下の記事を使用して、Skype For business online のパフォーマンスを微調整します。 
  
 **[Sharepoint online のパフォーマンスをチューニング](tune-sharepoint-online-performance.md)** する: sharepoint online のパフォーマンスを微調整するには、以下の記事を使用します。 
  
 **[Project online のパフォーマンスをチューニング](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)** する: この記事を使用して、project online のパフォーマンスを微調整します。 
  

