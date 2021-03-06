---
title: "Azure PaaS のハイブリッド クラウド シナリオ"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/1/2016
ms.audience: ITPro
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: "概要: Microsoft のサービスとしてのプラットフォーム (PaaS) ベースの Azure 内クラウド製品のハイブリッド アーキテクチャとシナリオについて説明します。"
---

# Azure PaaS のハイブリッド クラウド シナリオ

 **概要:** Microsoft のサービスとしてのプラットフォーム (PaaS) ベースの Azure 内クラウド製品のハイブリッド アーキテクチャとシナリオについて説明します。
  
オンプレミスのデータ リソースまたはコンピューティング リソースを、Azure PaaS で実行されている新規または変換後のアプリケーションと組み合わせます。これにより、クラウドのパフォーマンス、信頼性、およびスケールを利用し、モバイル ユーザーにより良いサポートを提供できます。 
  
## Azure PaaS のハイブリッド シナリオ アーキテクチャ

図 1 は、Microsoft PaaS ベースの Azure 内ハイブリッド シナリオのアーキテクチャを示しています。
  
**図 1:Microsoft PaaS ベースの Azure 内ハイブリッド シナリオ**

![Microsoft PaaS ベースの Azure 内ハイブリッド シナリオ](images/b003b15c-db66-4a3f-8cd9-3ab2e01601fe.png)
  
アーキテクチャの各レイヤーについて:
  
- アプリとシナリオ
    
    ハイブリッド PaaS アプリケーションは Azure で実行され、オンプレミスのコンピューティング リソースまたはストレージ リソースを使用します。
    
- ID
    
    サードパーティ ID プロバイダーとのディレクトリ同期またはフェデレーションで構成されています。
    
- ネットワーク
    
    既存のインターネット パイプ、または Azure PaaS に対するパブリック ピアリングとの ExpressRoute 接続で構成されています。Azure PaaS アプリケーションがオンプレミスのコンピューティング リソースまたはストレージ リソースにアクセスするための手段を含める必要があります。
    
- オンプレミス
    
    ID およびセキュリティ インフラストラクチャと、既存の基幹業務 (LOB) アプリケーションまたはデータベース サーバーで構成されています。これらには、Azure PaaS アプリケーションから安全にアクセスできます。
    
## Azure PaaS ハイブリッド アプリケーション

図 2 は、Azure で実行されているハイブリッド アプリケーションの構成を示しています。
  
**図 2:Azure PaaS ベースのハイブリッド アプリケーション**

![Azure PaaS ベースのハイブリッド アプリケーション](images/7d945c8e-346b-4610-8a02-dbaa9396e1f7.png)
  
図 2 では、オンプレミスのネットワークは、サーバー上、およびプロキシ サーバーを含む DMZ 上のストレージまたはアプリをホストします。インターネット経由で、または ExpressRoute に接続して、Azure PaaS サービスに接続されています。
  
組織は、次の方法により、コンピューティング リソースまたはストレージ リソースを Azure PaaS ハイブリッド アプリケーションで使用可能にできます。
  
- DMZ のサーバー上のリソースをホストします。
    
- DMZ のリバース プロキシ サーバーをホストします。これにより、オンプレミスに配置されているリソースに対して、認証済みの HTTPS ベースの着信要求が許可されます。
    
Azure アプリは、次の資格情報を使用できます。
  
- Azure AD。Windows Server AD などのオンプレミスの ID プロバイダーと同期させることができます。
    
- サードパーティ ID プロバイダー。
    
### Azure PaaS ハイブリッド アプリケーションの例

図 3 は、Azure で実行されているハイブリッド アプリケーションの例を示しています。
  
**図 3:Azure PaaS ベースのハイブリッド アプリケーションの例**

![Azure PaaS ベースのハイブリッド アプリケーション例](images/63051bbc-918b-4ae9-aa87-a43668a0067b.png)
  
図 3 では、オンプレミスのネットワークは、LOB アプリをホストします。Azure PaaS は、カスタム モバイル アプリをホストします。インターネット上のスマートフォンは Azure 内のカスタム モバイル アプリにアクセスし、このアプリはオンプレミスの LOB アプリにデータ要求を送信します。
  
この Azure PaaS ハイブリッド アプリケーションの例は、従業員の最新の連絡先情報を提供するカスタム モバイル アプリです。エンドツーエンドのハイブリッド シナリオは、次の要素で構成されています。
  
- スマートフォン アプリ。実行するために検証済みのオンプレミス資格情報を必要とします。
    
- Azure PaaS で実行されているカスタム モバイル アプリ。このアプリは、ユーザーのスマートフォン アプリからのクエリに基づき、特定の従業員に関する情報を要求します。
    
- DMZ のリバース プロキシ サーバー。カスタム モバイル アプリを検証し、要求を転送します。
    
- LOB アプリケーション サーバー ファーム。ユーザーのアカウントのアクセス許可に従い、連絡先要求を処理します。
    
オンプレミスの ID プロバイダーは Azure AD と同期されているため、カスタム モバイル アプリと LOB アプリの両方が要求元ユーザーのアカウント名を検証できます。
  
## Stretch Database および SQL Server 2016

Stretch Database は SQL Server 2016 の機能であり、顧客の発注情報を含む大きなテーブル内の処理済みビジネス データなど、コールド データを Azure の SQL Stretch Database に透過的かつ安全に移動できます。
  
ストレッチ時には、SQL Server インスタンス、データベース、または単一のテーブルのコンテンツは、SQL Server 2016 サーバーのローカル データと Azure のリモート データとを組み合わせたものです。ストレッチの対象となるデータは、SQL Server 2016 によって Azure に自動的に移動されます。
  
図 4 は、Stretch Database および SQL Server 2016 を示しています。
  
**図 4:Stretch Database および SQL Server 2016**

![Stretch Database および SQL Server 2016](images/bab0812e-eef0-4667-9939-cd398d33a196.png)
  
図 4 では、オンプレミスのネットワークは、小規模なローカル データベースを使用する SQL Server 2016 を実行しているサーバーをホストします。Azure PaaS は、データベースのストレッチ部分を含む Azure SQL Server Stretch Database のインスタンスをホストします。オンプレミスのユーザーからオンプレミスの SQL Server に送信された T-SQL クエリは、Azure SQL Stretch Database に安全に転送され、要求元のユーザーに結果が返されます。
  
 履歴データを含むユーザー クエリは、Azure SQL Stretch Database に透過的に転送されます。テーブルがストレッチされても、クエリを書き換える必要はありません。
  
Stretch Database は、長期ストレージ、および履歴データへの透過的アクセスのためのコスト パフォーマンスに優れたオプションを提供します。テーブルが非常に大きくなると発生するパフォーマンスと可用性の問題も解決します。
  
詳細については、「[Stretch Database](https://msdn.microsoft.com/ja-jp/library/dn935011.aspx)」を参照してください。
  
## See Also

#### 

[エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)
#### 

[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)

