---
title: Azure PaaS のハイブリッド クラウド シナリオ
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: '概要: Microsoft のサービスとしてのプラットフォーム (PaaS) ベースの Azure 内クラウド製品のハイブリッド アーキテクチャとシナリオについて説明します。'
ms.openlocfilehash: e536d81b6b14b05bef49d7c91b0404faec64303b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123334"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a>Azure PaaS のハイブリッド クラウド シナリオ

 **概要:** Microsoft のサービスとしてのプラットフォーム (PaaS) ベースの Azure 内クラウド製品のハイブリッド アーキテクチャとシナリオについて説明します。
  
オンプレミスのデータ リソースまたはコンピューティング リソースを、Azure PaaS で実行されている新規または変換後のアプリケーションと組み合わせます。これにより、クラウドのパフォーマンス、信頼性、およびスケールを利用し、モバイル ユーザーにより良いサポートを提供できます。 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a>Azure PaaS のハイブリッド シナリオ アーキテクチャ

図 1 は、Microsoft PaaS ベースの Azure 内ハイブリッド シナリオのアーキテクチャを示しています。
  
**図 1:Microsoft PaaS ベースの Azure 内ハイブリッド シナリオ**

![Microsoft PaaS ベースの Azure 内ハイブリッド シナリオ](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
アーキテクチャの各レイヤーについて:
  
- アプリとシナリオ
    
    ハイブリッド PaaS アプリケーションは Azure で実行され、オンプレミスのコンピューティング リソースまたはストレージ リソースを使用します。
    
- ID
    
    サードパーティ ID プロバイダーとのディレクトリ同期またはフェデレーションで構成されています。
    
- ネットワーク
    
    既存のインターネット パイプ、または Azure PaaS に対するパブリック ピアリングとの ExpressRoute 接続で構成されています。Azure PaaS アプリケーションがオンプレミスのコンピューティング リソースまたはストレージ リソースにアクセスするための手段を含める必要があります。
    
- オンプレミス
    
    ID およびセキュリティ インフラストラクチャと、既存の基幹業務 (LOB) アプリケーションまたはデータベース サーバーで構成されています。これらには、Azure PaaS アプリケーションから安全にアクセスできます。
    
## <a name="azure-paas-hybrid-application"></a>Azure PaaS ハイブリッド アプリケーション

図 2 は、Azure で実行されているハイブリッド アプリケーションの構成を示しています。
  
**図 2:Azure PaaS ベースのハイブリッド アプリケーション**

![Azure PaaS ベースのハイブリッド アプリケーション](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
図 2 では、オンプレミスのネットワークは、サーバー上、およびプロキシ サーバーを含む DMZ 上のストレージまたはアプリをホストします。インターネット経由で、または ExpressRoute に接続して、Azure PaaS サービスに接続されています。
  
組織は、次の方法により、コンピューティング リソースまたはストレージ リソースを Azure PaaS ハイブリッド アプリケーションで使用可能にできます。
  
- DMZ のサーバー上のリソースをホストします。
    
- DMZ のリバース プロキシ サーバーをホストします。これにより、オンプレミスに配置されているリソースに対して、認証済みの HTTPS ベースの着信要求が許可されます。
    
Azure アプリは、次の資格情報を使用できます。
  
- Azure AD。Windows Server AD などのオンプレミスの ID プロバイダーと同期させることができます。
    
- サードパーティ ID プロバイダー。
    
### <a name="example-azure-paas-hybrid-application"></a>Azure PaaS ハイブリッド アプリケーションの例

図 3 は、Azure で実行されているハイブリッド アプリケーションの例を示しています。
  
**図 3:Azure PaaS ベースのハイブリッド アプリケーションの例**

![Azure PaaS ベースのハイブリッド アプリケーション例](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
図 3 では、オンプレミスのネットワークは、LOB アプリをホストします。Azure PaaS は、カスタム モバイル アプリをホストします。インターネット上のスマートフォンは Azure 内のカスタム モバイル アプリにアクセスし、このアプリはオンプレミスの LOB アプリにデータ要求を送信します。
  
この Azure PaaS ハイブリッド アプリケーションの例は、従業員の最新の連絡先情報を提供するカスタム モバイル アプリです。エンドツーエンドのハイブリッド シナリオは、次の要素で構成されています。
  
- スマートフォン アプリ。実行するために検証済みのオンプレミス資格情報を必要とします。
    
- Azure PaaS で実行されているカスタム モバイル アプリ。このアプリは、ユーザーのスマートフォン アプリからのクエリに基づき、特定の従業員に関する情報を要求します。
    
- DMZ のリバース プロキシ サーバー。カスタム モバイル アプリを検証し、要求を転送します。
    
- LOB アプリケーション サーバー ファーム。ユーザーのアカウントのアクセス許可に従い、連絡先要求を処理します。
    
オンプレミスの ID プロバイダーは Azure AD と同期されているため、カスタム モバイル アプリと LOB アプリの両方が要求元ユーザーのアカウント名を検証できます。
  
## <a name="see-also"></a>関連項目

[エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

