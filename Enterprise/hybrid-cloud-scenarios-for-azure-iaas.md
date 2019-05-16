---
title: Azure IaaS のハイブリッド クラウドのシナリオ
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: '概要: Microsoft のサービスとしてのインフラストラクチャ (IaaS) ベースの Azure のクラウド製品のハイブリッドアーキテクチャとシナリオについて説明します。'
ms.openlocfilehash: 429af408ca3f21fe667b36cdb9767d3916a6b1a4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067353"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a>Azure IaaS のハイブリッド クラウドのシナリオ

 **概要:** Microsoft のサービスとしてのインフラストラクチャ (IaaS) ベースの Azure のクラウド製品のハイブリッドアーキテクチャとシナリオについて理解します。
  
クロスプレミスの Azure 仮想ネットワーク (Vnet) で実行されている IT ワークロードをホストすることにより、オンプレミスのコンピューティングおよび id インフラストラクチャをクラウドに拡張します。 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a>Azure IaaS ハイブリッドシナリオのアーキテクチャ

図1は、Microsoft IaaS ベースの Azure のハイブリッドシナリオのアーキテクチャを示しています。
  
**図 1: Microsoft IaaS ベースの Azure 内ハイブリッドシナリオ**

![Azure での Microsoft IaaS ベースのハイブリッドシナリオ](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
アーキテクチャの各レイヤーについて:
  
- アプリとシナリオ
    
    IT ワークロードは、通常、Azure 仮想マシン (Vm) で構成された複数層の高可用性アプリケーションです。
    
- ID
    
    Active Directory ドメインサービス (AD DS) ドメインコントローラーなどの id サーバーを、Azure Vnet で実行されているローカル認証用のサーバーのセットに追加します。
    
- ネットワーク
    
    インターネット経由でのサイト間 VPN 接続、または Azure IaaS に対するプライベートピアリングを備えた ExpressRoute 接続を使用します。
    
- 社内
    
    Azure で実行されている id サーバーと同期された id サーバーを含みます。 また、ストレージやシステム管理インフラストラクチャなど、Azure で実行されている Vm がアクセスできるリソースを含めることもできます。
    
## <a name="directory-synchronization-server-for-office-365"></a>Office 用ディレクトリ同期サーバー365

図2に示されているように、Azure VNet からディレクトリ同期サーバーを実行することは、コンピューティングおよび id インフラストラクチャをクラウドに拡張する例です。
  
**図 2: Azure IaaS の Office 365 用のディレクトリ同期サーバー**

![Azure IaaS の Office 365 用のディレクトリ同期サーバー](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
図2では、社内ネットワークが AD DS インフラストラクチャをホストしており、プロキシサーバーとルーターがエッジに配置されています。 ルーターは、サイト間 VPN または ExpressRoute 接続を使用して Azure VNet のエッジにある Azure ゲートウェイに接続します。 VNet 内で、ディレクトリ同期サーバーは Azure AD Connect を実行します。
  
Office 365 用のディレクトリ同期サーバーは、AD DS 内のアカウントの一覧を Office 365 サブスクリプションの Azure AD テナントと同期します。
  
ディレクトリ同期サーバーは、Azure AD Connect を実行する Windows ベースのサーバーです。 プロビジョニングを高速化したり、組織内のオンプレミスサーバーの数を少なくしたりするには、Azure IaaS の仮想ネットワーク (VNet) にディレクトリ同期サーバーを展開します。
  
ディレクトリ同期サーバーは、変更に関して AD DS をポーリングしてから、それらを Office 365 サブスクリプションと同期します。
  
詳細については、「 [Deploy Office 365 Directory Synchronization In Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)」を参照してください。
  
## <a name="line-of-business-lob-application"></a>基幹業務 (LOB) アプリケーション

図3は、Azure IaaS で実行されているサーバーベースの LOB アプリケーションの構成を示しています。
  
**図 3: Azure IaaS の LOB アプリケーション**

![Azure IaaS のサーバーベースの LOB アプリケーション](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
図3では、社内ネットワークによって id インフラストラクチャとユーザーがホストされます。 これは、サイト間 VPN または ExpressRoute 接続を使用して Azure IaaS gateway に接続されています。 Azure IaaS は、LOB アプリケーションのサーバーを含む仮想ネットワークをホストします。
  
Azure Vm で実行されている LOB アプリケーションを作成できます。これは、azure データセンター (場所とも呼ばれる) の Azure VNet のサブネット上に存在します。
  
基本的に社内インフラストラクチャを Azure に拡張するので、一意のプライベートアドレス空間を Vnet に割り当て、オンプレミスルーティングテーブルを更新して、各 VNet に到達できるようにする必要があります。
  
接続すると、これらの Vm は、オンプレミスのサーバーの場合と同様に、リモートデスクトップ接続またはシステム管理ソフトウェアを使用して管理できます。
  
公的で公開されたポートを構成することで、これらの Vm は、モバイルまたはリモートユーザーがインターネットからアクセスすることもできます。
  
概念実証の構成については、「 [Azure でのシミュレートされたクロスプレミスの仮想ネットワーク](simulated-cross-premises-virtual-network-in-azure.md)」を参照してください。
  
Azure Vm でホストされている LOB アプリケーションの属性は次のとおりです。
  
- 複数の階層
    
    一般的な LOB アプリケーションは、階層型のアプローチを使用します。 サーバーのセットは、id、データベース処理、アプリケーションとロジックの処理、および社員または顧客へのアクセスのためのフロントエンド web サーバーを提供します。 
    
- 高可用性
    
    一般的な LOB アプリケーションでは、各層で複数のサーバーを使用することで高可用性が実現されます。 Azure IaaS では、Azure の可用性セットのサーバーに 99.9% の稼働時間の SLA が提供されます。 
    
- 負荷分散
    
    階層内の複数のサーバー間でネットワークトラフィックの負荷を分散するには、インターネット接続または内部 Azure ロードバランサーを使用できます。 または、Azure marketplace から入手できる専用のロードバランサーアプライアンスを使用することもできます。
    
- セキュリティ
    
    インターネットからの一方的な着信トラフィックからサーバーを保護するには、Azure のネットワークセキュリティグループを使用できます。 サブネットまたは個々の仮想マシンのネットワークインターフェイスに対して許可または拒否されるトラフィックを定義できます。
    
## <a name="sharepoint-server-2016-farm-in-azure"></a>Azure の SharePoint Server 2016 ファーム

図4に示すように、Azure での多階層の高可用性 LOB アプリケーションの例としては、SharePoint Server 2016 ファームがあります。
  
**図 4: Azure IaaS の高可用性 SharePoint Server 2016 ファーム**

![Azure IaaS の高可用性 SharePoint Server 2016 ファーム](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
図4では、オンプレミスのネットワークが id インフラストラクチャとユーザーをホストしています。 これは、サイト間 VPN または ExpressRoute 接続を使用して Azure IaaS gateway に接続されています。 Azure VNet には、フロントエンドサーバー、アプリケーションサーバー、SQL Server クラスター、およびドメインコントローラーの各層を含む SharePoint Server 2016 ファームのサーバーが含まれています。
  
この構成には、Azure の LOB アプリケーションの次の属性があります。 
  
- 階層
    
    ファーム内でさまざまな役割を実行しているサーバーは、層を作成し、各層には独自のサブネットがあります。
    
- 高可用性
    
    各層で複数のサーバーを使用して、層のすべてのサーバーを同じ可用性セットに配置することによって実現されます。
    
- 負荷分散
    
    内部 Azure ロードバランサーは、受信クライアント web トラフィックをフロントエンドサーバー (WEB1 および WEB2) と、SQL Server クラスターのリスナー IP アドレス (SQL1、: SQL2、および: MN1) に分配します。
    
- セキュリティ
    
    各サブネットのネットワークセキュリティグループを使用すると、許可される受信および送信トラフィックを構成できます。
    
導入を成功させるには、次のパスを使用します。
  
1. 評価とテスト
    
    Azure で SharePoint Server 2016 を実行することの利点については、「 [Microsoft azure の Sharepoint server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) 」を参照してください。
    
    シミュレートされた開発/テスト環境を構築するには、「 [Azure 開発/テスト環境でのイントラネット SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) 」を参照してください。
    
2. デザイン
    
    「 [SharePoint Server 2016 ファームを設計](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure)する」を参照して、プロセスをステップ実行し、ファームをホストする azure IaaS ネットワーク、コンピューティング、およびストレージ要素のセットとそれらの設定を確認してください。
    
3. 展開
    
    高可用性ファームのエンドツーエンド構成を5段階で手順を追って説明するには、「 [Azure で SharePoint server 2016 を SQL Server AlwaysOn 可用性グループと共に展開](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in)する」を参照してください。
    
## <a name="federated-identity-for-office-365-in-azure"></a>Azure での Office 365 のフェデレーション id

Azure で高可用性を備えた複数層の LOB アプリケーションの別の例として、Office 365 のフェデレーション id があります。
  
**図 5: Azure IaaS の Office 365 用の高可用性フェデレーション id インフラストラクチャ**

![Azure での高可用性 Office 365 フェデレーション認証インフラストラクチャ](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
図5では、オンプレミスのネットワークが id インフラストラクチャとユーザーをホストしています。 これは、サイト間 VPN または ExpressRoute 接続を使用して Azure IaaS gateway に接続されています。 Azure VNet には、web プロキシサーバー、Active Directory フェデレーションサービス (AD FS) サーバー、および Active Directory ドメインサービス (AD DS) ドメインコントローラーが含まれています。
  
この構成には、Azure の LOB アプリケーションの次の属性があります。
  
- **層:** Web プロキシサーバー、AD FS サーバー、AD DS ドメインコントローラーには階層があります。
    
- **負荷分散:** 外部の Azure ロードバランサーは、受信クライアント認証要求を web プロキシに配布し、内部 Azure ロードバランサーは、認証要求を AD FS サーバーに配信します。
    
導入を成功させるには、次のパスを使用します。
  
1. 評価とテスト
    
    Office 365 を使用して、フェデレーション認証用のシミュレートされた開発/テスト環境を構築するには[、「office 365 開発/テスト環境のフェデレーション Id](federated-identity-for-your-office-365-dev-test-environment.md) 」を参照してください。
    
2. 展開
    
    高可用性 AD FS インフラストラクチャのエンドツーエンド構成を5段階で手順を追って説明するには、「 [Deploy high availability フェデレーション authentication For Office 365 For Azure」](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)を参照してください。
    
    
## <a name="see-also"></a>関連項目

[エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)


