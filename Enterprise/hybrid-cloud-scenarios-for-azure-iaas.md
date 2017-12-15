---
title: "Azure IaaS のハイブリッド クラウド シナリオ"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: "概要: ハイブリッド アーキテクチャと理解シナリオのインフラストラクチャのサービス (IaaS) としてのベースで、Azure クラウド サービスです。"
ms.openlocfilehash: 389ab2b7ce37423a1601a2f76d143370833085cb
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a>Azure IaaS のハイブリッド クラウド シナリオ

 **の概要:**サービス (IaaS) としてマイクロソフトのインフラストラクチャのハイブリッド アーキテクチャとシナリオを理解するので、Azure クラウド サービスをベースです。
  
クロスプレミスの Azure 仮想ネットワーク (VNet) で実行されている IT ワークロードをホストすることで、オンプレミスのコンピューティングおよび ID インフラストラクチャをクラウドに拡張します。  
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a>Azure IaaS のハイブリッド シナリオ アーキテクチャ

図 1 は、Microsoft IaaS ベースの Azure 内ハイブリッド シナリオのアーキテクチャを示しています。
  
**Azure で Microsoft ベースの IaaS ハイブリッド シナリオを図 1:**

![Microsoft IaaS ベースの Azure 内ハイブリッド シナリオ](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS.png)
  
アーキテクチャの各レイヤーについて:
  
- アプリとシナリオ
    
    IT ワークロードは、通常、Azure 仮想マシン (VM) で構成されている可用性の高い多層アプリケーションです。
    
- ID
    
    ローカル認証のために、Azure VNet で実行されているサーバーのセットに、Windows Server AD ドメイン コントローラーなどの ID サーバーを追加します。
    
- ネットワーク
    
    インターネット経由でのサイト間 VPN 接続、または Azure IaaS に対するプライベート ピアリングとの ExpressRoute 接続を使用します。
    
- オンプレミス
    
    Azure で実行されている ID サーバーと同期している ID サーバーが含まれています。ストレージおよびシステムの管理インフラストラクチャなど、Azure で実行されている VM がアクセスできるリソースが含まれる場合もあります。
    
## <a name="dirsync-server-for-office-365"></a>Office 365 向けの DirSync サーバー

図 2 に示すように、コンピューティングと ID インフラストラクチャをクラウドに拡張する一例として、ディレクトリ同期 (DirSync) サーバーを Azure VNet から実行するという方法があります。
  
**Azure IaaS で Office 365 のディレクトリ同期サーバーを図 2:**

![Azure IaaS の Office 365 向けの DirSync サーバー](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_DirSync.png)
  
図 2 に、オンプレミスのネットワークは、プロキシ サーバーとルーターの端に、Windows サーバーの AD インフラストラクチャをホストします。ルーターは、サイト間の VPN または ExpressRoute の接続を使用して、Azure の VNet の端に、Azure のゲートウェイに接続します。VNet の内部は、ディレクトリ同期サーバーは、Azure AD 接続を実行します。
  
Office 365 向けの DirSync サーバーは、Windows Server AD のアカウントの一覧を Office 365 サブスクリプションの Azure AD テナントと同期します。
  
DirSync サーバーは、Azure AD Connect を実行する Windows ベースのサーバーです。迅速なプロビジョニングを実現し、組織内のオンプレミスのサーバーの数を減らすには、Azure IaaS の仮想ネットワーク (VNet) で DirSync サーバーを展開します。
  
DirSync サーバーは、変更用に Windows Server AD をポーリングし、それらの変更点を Office 365 サブスクリプションと同期します。
  
詳細については、 [Azure で Office 365 のディレクトリ同期の展開](https://technet.microsoft.com/library/dn635310.aspx)を参照してください。
  
## <a name="line-of-business-lob-application"></a>基幹業務 (LOB) アプリケーション

図 3 は、Azure IaaS で実行されているサーバーベース LOB アプリケーションの構成を示しています。
  
**Azure IaaS に LOB アプリケーションを図 3:**

![Azure IaaS 内のサーバ ベース LOB アプリケーション](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_Ex.png)
  
図 3 では、オンプレミス ネットワークは、ID インフラストラクチャとユーザーをホストしています。サイト間 VPN または ExpressRoute の接続を使用して、Azure IaaS ゲートウェイに接続されています。Azure IaaS は、LOB アプリケーションのサーバーを含む仮想ネットワークをホストします。
  
Azure データ センター (所在地) で、Azure VNet のサブネット上に存在、Azure の Vm で実行されている LOB アプリケーションを作成することができます。
  
本質的にはオンプレミス インフラストラクチャを Azure に拡張しているので、VNet に独自のプライベート アドレス空間を割り当て、オンプレミス ルーティング テーブルを更新して、各 VNet への到達可能性を確保する必要があります 
  
接続が完了したら、オンプレミス サーバーと同様に、リモート デスクトップ接続またはシステム管理ソフトウェアを使用してこれらの VM を管理できます。
  
一般に公開されるポートを構成すると、これらの VM には、モバイル ユーザーまたはリモート ユーザーによってインターネットからもアクセスできます。
  
概念実証の構成では、 [Simulated 間設置型で、Azure の仮想ネットワーク](simulated-cross-premises-virtual-network-in-azure.md)を参照してください。
  
Azure VM でホストされている LOB アプリケーションの属性を次に示します。
  
- 複数の階層
    
    通常の LOB アプリケーションでは、階層型アプローチを使用します。サーバーのセットが、従業員や顧客のアクセスのために ID、データベース処理、アプリケーションおよびロジック処理、フロントエンド Web サーバーを提供します。  
    
- 高可用性
    
    通常の LOB アプリケーションでは、層ごとに複数のサーバーを使用することによって高可用性が実現します。Azure IaaS では、Azure の可用性セットでサーバーに 99.9% の稼働時間 SLA を提供します。  
    
- 負荷分散
    
    階層内の複数のサーバー間のネットワーク トラフィックの負荷を分散するには、インターネット接続済みまたは内部の Azure ロード バランサーを使用できます。または、Azure Marketplace から入手可能な専用のロード バランサー アプライアンスを使用できます。
    
- セキュリティ
    
    インターネットからの未承諾の着信トラフィックからサーバーを保護するには、Azure ネットワーク セキュリティ グループを使用できます。サブネットの許可または拒否されたトラフィック、または個々の仮想マシンのネットワーク インターフェイスを定義できます。
    
## <a name="sharepoint-server-2016-farm-in-azure"></a>Azure の SharePoint Server 2016 ファーム

Azure での可用性の高い多層 LOB アプリケーションの例として、図 4 に示すように SharePoint Server 2016 ファームがあります。
  
**図 4: 高可用性サーバー 2016 の SharePoint ファーム Azure IaaS で**

![Azure IaaS の高可用性 SharePoint Server 2016 ファーム](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_SP2016.png)
  
図 4 では、オンプレミス ネットワークは、ID インフラストラクチャとユーザーをホストしています。サイト間 VPN または ExpressRoute に接続して、Azure IaaS ゲートウェイに接続されています。Azure VNet には、SharePoint Server 2016 ファームのサーバーが含まれています。これには、フロント エンド サーバー、アプリケーション サーバー、SQL Server クラスター、およびドメイン コントローラーごとに個別の階層が存在します。
  
この構成には、次に示す Azure の LOB アプリケーションの属性が含まれています。  
  
- 階層
    
    ファーム内のさまざまな役割を実行しているサーバーは、階層を作成し、各階層には独自のサブネットです。
    
- 高可用性
    
    各階層で複数のサーバーを使用して、階層のすべてのサーバーを同じ可用性セットに配置することによって実現します。
    
- 負荷分散
    
    Azure の内部ロード バランサーは、クライアント Web の受信トラフィックをフロントエンド サーバー (WEB1 と WEB2) および SQL Server クラスターのリスナーの IP アドレス (SQL1、SQL2、MN1) に配布します。
    
- セキュリティ
    
    各サブネットのネットワーク セキュリティ グループを使用して、許可する受信トラフィックおよび送信トラフィックを構成できます。
    
正常に導入するために次のパスに従ってください。
  
1. 評価と試用
    
    Azure で実行中の SharePoint サーバーの 2016年の利点を理解するのには、 [Microsoft Azure 内の SharePoint サーバーの 2016年](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx)を参照してください。
    
    [イントラネットの SharePoint サーバー 2016 Azure 開発/テスト環境で](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)シミュレートされた開発/テスト環境を構築を参照してください。
    
2. デザイン
    
    Azure IaaS のネットワー キング、コンピューティング、およびファームとその設定をホストするストレージ ・ エレメントのセットを決定するためのプロセスをステップ実行するには[Azure の SharePoint サーバーの 2016年ファームの設計](https://technet.microsoft.com/library/mt779108%28v=office.16%29.aspx)を参照してください。
    
3. 展開
    
    [Azure で AlwaysOn 可用性グループを SQL Server と SharePoint サーバー 2016 を展開する](https://technet.microsoft.com/library/mt793552%28v=office.16%29.aspx)5 つの段階では、高可用性ファームのエンド ・ ツー ・ エンドの構成の手順を参照してください。
    
## <a name="federated-identity-for-office-365-in-azure"></a>Azure 内の Office 365 のフェデレートされた識別情報

Azure 内の複数の層、および高可用性の LOB アプリケーションの別の例は、Office 365 のフェデレーションの id です。
  
**図 5: Azure IaaS で Office 365 のフェデレートされた識別情報の高可用性インフラストラクチャが、**

![Azure での高可用性 Office 365 フェデレーション認証インフラストラクチャの最終構成](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_ADFS.png)
  
図 5 に、オンプレミスのネットワークとユーザーの識別情報のインフラストラクチャをホストします。サイト間の VPN または ExpressRoute の接続を使用して、Azure の IaaS のゲートウェイに接続されています。Azure VNet には、web プロキシ サーバー、Active Directory フェデレーション サービス (AD FS) サーバー、および Windows Server ・ Active Directory (AD) ドメイン コント ローラーが含まれています。
  
この構成には、次に示す Azure の LOB アプリケーションの属性が含まれています。 
  
- **層:**Web プロキシ サーバー、AD FS サーバー、および Windows Server AD ドメイン コント ローラーの階層があります。
    
- **負荷分散:**Azure の外部のロード バランサーは、web プロキシを受信したクライアントの認証要求を分散し、Azure の内部ロード バランサーが AD FS サーバーに認証要求を配布します。
    
正常に導入するために次のパスに従ってください。
  
1. 評価と試用
    
    Office 365 とフェデレーションの認証のためにシミュレートされた開発/テスト環境を構築するのには[、Office 365 の開発/テスト環境にフェデレーション ユーザー](federated-identity-for-your-office-365-dev-test-environment.md)を参照してください。
    
2. 展開
    
    5 つのフェーズでは、AD FS インフラストラクチャの高可用性のエンド ・ ツー ・ エンドの構成をステップ実行するには[Azure で Office 365 の展開の高可用性フェデレーション認証](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)を参照してください。
    
これらのその他のリソースを参照してください。
  
- [ハイブリッド クラウド環境の構築](https://gallery.technet.microsoft.com/Architecting-Hybrid-Cloud-a7dc9f24/file/147475/1/Architecting%20Hybrid%20Cloud%20Environments%20V1.docx)
    
- [クラウド マイクロソフト仮想アカデミー コースのページに、データ センターを拡張します。](https://mva.microsoft.com/en-US/training-courses/extend-your-datacenter-to-the-cloud-13908?l=7fG3tAouB_7100115881)
    
- [設計して、Azure で LOB アプリケーションを作成](https://techcommunity.microsoft.com/t5/CAAB-Cloud-Adoption-Advisory/EXTRA-November-2016-Webinar/m-p/30058#M41)
    
## <a name="see-also"></a>See Also

[エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)



