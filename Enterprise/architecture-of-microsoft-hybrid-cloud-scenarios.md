---
title: Microsoft ハイブリッド クラウドのシナリオのアーキテクチャ
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: '概要: Microsoft のハイブリッド クラウド製品のアーキテクチャについて説明します。'
ms.openlocfilehash: f5493c0f008b22af412ee95ccb8b7581eee71476
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490270"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a>Microsoft ハイブリッド クラウド シナリオのアーキテクチャ

 **概要:** Microsoft のハイブリッド クラウド製品のアーキテクチャについて説明します。
  
アーキテクチャ アプローチを使用して、Microsoft クラウド サービスおよびプラットフォームを使用するハイブリッド クラウド シナリオを計画して実装します。
  
**図 1:Microsoft ハイブリッド クラウド スタック**

![Microsoft ハイブリッド クラウド スタック](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
図 1 は、Microsoft ハイブリッド クラウド スタックとそのレイヤーを示しています。レイヤーには、オンプレミス、ネットワーク、ID、アプリとシナリオ、およびクラウド サービスのカテゴリ (Microsoft SaaS、Azure PaaS、Azure PaaS) が含まれます。
  
アプリとシナリオのレイヤーには、このモデルの追加記事で詳しく説明されている特定のハイブリッドクラウドのシナリオがあります。 ID、ネットワーク、オンプレミスのレイヤーは、クラウド サービスのカテゴリ (SaaS、PaaS、または PaaS) では共通である場合があります。
  
- オンプレミス
    
    ハイブリッド シナリオのオンプレミス インフラストラクチャには、SharePoint、Exchange、Skype for Business のサーバーと、基幹業務アプリケーションが含まれます。データ ストア (データベース、リスト、ファイル) を含めることもできます。ExpressRoute 接続がない場合、オンプレミス データ ストアへのアクセスは、リバース プロキシを介すか、サーバーまたはデータを DMZ またはエクストラネットでアクセス可能にすることによって許可する必要があります。
    
- ネットワーク
    
    Microsoft クラウド プラットフォームとサービスに接続するには、既存のインターネット パイプか ExpressRoute のいずれかを使用します。 予測可能なパフォーマンスが重要な場合は、ExpressRoute 接続を使用します。 1つの ExpressRoute 接続を使用して、Microsoft SaaS services (Office 365 および Dynamics 365)、azure PaaS サービス、および azure IaaS services に直接接続することができます。
    
- ID
    
    クラウド ID インフラストラクチャについては、Microsoft クラウド プラットフォームによって、2 つの方法があります。 SaaS および Azure PaaS については、Azure AD にオンプレミス ID インフラストラクチャを統合するか、オンプレミス ID インフラストラクチャまたはサードパーティ ID プロバイダーでフェデレーションを行います。 Azure で実行されている vm では、Active Directory ドメインサービス (AD DS) などのオンプレミスの id インフラストラクチャを、vm が存在する仮想ネットワーク (vnet) に拡張できます。
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a>3 段階のクラウド導入プロセスのハイブリッド クラウド シナリオ

Microsoft を含む多くの企業は、クラウドの採用に 3 段階のアプローチを使用します。ハイブリッド クラウド シナリオは各段階で役割を果たすことができます。
  
1. 生産性ワークロードを SaaS に移行する
    
    現状の生産性ワークロード、またはオンプレミスで維持する必要がある生産性ワークロードについて、ハイブリッド シナリオでは対応するクラウド ワークロードと統合できます。
    
2. Azure PaaS で最新のアプリケーションを開発する
    
    Azure PaaS ハイブリッド アプリケーションは、オンプレミスのサーバーまたはストレージ リソースを安全に活用できます。
    
3. 既存のアプリケーションを Azure IaaS に移動する
    
    移行 (リフトアンドシフト) およびクラウド内構築シナリオでは、Azure VM で実行されているサーバーベースのアプリケーションが容易なプロビジョニングとスケーリングを提供します。
    
## <a name="see-also"></a>関連項目

[エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

