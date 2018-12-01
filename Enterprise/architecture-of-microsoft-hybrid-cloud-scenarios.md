---
title: Microsoft ハイブリッド クラウド シナリオのアーキテクチャ
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
ms.openlocfilehash: 74fc046d1f60b29338e7f12184dec018538ba9da
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123394"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a>Microsoft ハイブリッド クラウド シナリオのアーキテクチャ

 **概要:** Microsoft のハイブリッド クラウド製品のアーキテクチャについて説明します。
  
アーキテクチャ アプローチを使用して、Microsoft クラウド サービスおよびプラットフォームを使用するハイブリッド クラウド シナリオを計画して実装します。
  
**図 1:Microsoft ハイブリッド クラウド スタック**

![Microsoft ハイブリッド クラウド スタック](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
図 1 は、Microsoft ハイブリッド クラウド スタックとそのレイヤーを示しています。レイヤーには、オンプレミス、ネットワーク、ID、アプリとシナリオ、およびクラウド サービスのカテゴリ (Microsoft SaaS、Azure PaaS、Azure PaaS) が含まれます。
  
アプリケーションおよびシナリオのレイヤーでは、このモデルの他の資料に詳細については、特定のハイブリッド クラウド シナリオを持っています。Id、ネットワーク、および設置レイヤーは、SaaS、PaaS、(PaaS) のクラウド サービスのカテゴリに共通することができます。
  
- オンプレミス
    
    ハイブリッド シナリオのオンプレミス インフラストラクチャには、SharePoint、Exchange、Skype for Business のサーバーと、基幹業務アプリケーションが含まれます。データ ストア (データベース、リスト、ファイル) を含めることもできます。ExpressRoute 接続がない場合、オンプレミス データ ストアへのアクセスは、リバース プロキシを介すか、サーバーまたはデータを DMZ またはエクストラネットでアクセス可能にすることによって許可する必要があります。
    
- ネットワーク
    
    マイクロソフトのクラウド プラットフォームおよびサービスへの接続用の 2 つの選択肢があります。 インターネットの既存のパイプと ExpressRoute。予測可能なパフォーマンスが重要な場合は、ExpressRoute 接続を使用します。マイクロソフトの SaaS サービス (Office 365 と Dynamics 365)、Azure PaaS サービス、および Azure IaaS サービスに直接接続する 1 つの ExpressRoute 接続を使用できます。
    
- ID
    
    クラウド ID インフラストラクチャについては、Microsoft クラウド プラットフォームによって、2 つの方法があります。SaaS および Azure PaaS については、Azure AD にオンプレミス ID インフラストラクチャを統合するか、オンプレミス ID インフラストラクチャまたはサードパーティ ID プロバイダーでフェデレーションを行います。Azure で実行されている VM については、Windows Server AD などのオンプレミス ID インフラストラクチャを、VM が存在する仮想ネットワーク (VNet) に拡張できます。
    
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

