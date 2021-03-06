---
title: "ハイブリッド クラウドの概要"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/31/2016
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
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: "概要: Microsoft ハイブリッド クラウドの定義と要素について説明します。"
---

# ハイブリッド クラウドの概要

 **概要:** Microsoft ハイブリッド クラウドの定義と要素について説明します。
  
ハイブリッド クラウドは、オンプレミス ネットワーク上またはクラウド内のコンピューティング リソースまたはストレージ リソースを使用します。全体的な IT 戦略の一環として、ビジネスおよびその IT のニーズをクラウドに移行するプロセスや、クラウド プラットフォームおよびサービスを既存のオンプレミス インフラストラクチャと統合するプロセスに、ハイブリッド クラウドを使用できます。
  
## Microsoft ハイブリッド クラウド

Microsoft ハイブリッド クラウドは、次のように Microsoft クラウド プラットフォームをオンプレミス コンポーネントと組み合わせるビジネス シナリオのセットです。 
  
- オンプレミスの SharePoint ファームと Office 365 の SharePoint Online の両方のコンテンツから検索結果を取得します。
    
- オンプレミス データ ストアに対してクエリを実行する、Azure で実行されているモバイル アプリ。
    
- Azure 仮想マシン上で実行されるイントラネット IT ワークロード。
    
**図 1:Microsoft ハイブリッド クラウドのコンポーネント**

![Microsoft ハイブリッド クラウドのコンポーネント](images/65dfb1c6-26be-45c2-ab3d-6d1cd4a0f823.png)
  
図 1 は、インターネットまたは ExpressRoute 接続を通して利用可能なオンプレミス ネットワークから Office 365 のセットまでの Microsoft ハイブリッド クラウド、Azure のサービスとしてのプラットフォーム (PaaS)、Azure のサービスとしてのインフラストラクチャ (IaaS) サービスを示しています。
  
Microsoft は、サービスとしてのソフトウェア (SaaS)、PaaS、および IaaS など、市場で最も包括的なクラウド ソリューションを有するため、次のことが可能です。
  
- ワークロードとアプリケーションをクラウドに移行する際に、既存のオンプレミスの投資を活用します。
    
- たとえば、特定のデータまたはワークロードをクラウドに移行することが規制やポリシーで許可されていない場合に、ハイブリッド クラウド シナリオを長期的な IT 計画に組み込みます。
    
- 複数の Microsoft クラウド サービスおよびプラットフォームを含む追加のハイブリッド シナリオを作成します。
    
Microsoft クラウド サービスを使用するハイブリッド クラウドのシナリオは、プラットフォームによって異なります。
  
- SaaS
    
    Microsoft SaaS サービスには、Office 365、Microsoft Intune および Microsoft Dynamics 365 が含まれます。Microsoft SaaS を使ったハイブリッド クラウド シナリオでは、これらのサービスをオンプレミス サービスまたはアプリケーションと統合します。たとえば、Office 365 で実行されている Exchange Online は、オンプレミスで展開されている Skype for Business 2015 と統合することができます。
    
- Azure PaaS
    
    Microsoft Azure PaaS サービスを使用すると、クラウドベースのアプリケーションを作成できます。Azure PaaS サービスを使ったハイブリッド クラウド シナリオでは、Azure PaaS アプリをオンプレミス リソースまたはアプリケーションと統合します。たとえば、Azure PaaS アプリ クラウドでは、モバイル アプリのユーザーに表示するのに必要な情報のオンプレミス データ ストアを安全に照会できます。
    
- Azure IaaS
    
    Azure IaaS サービスを使用すると、オンプレミス データセンターではなく、クラウドで、サーバーベースの IT ワークロードをビルドし実行できます。通常、Azure IaaS サービスを使ったハイブリッド クラウド シナリオは、オンプレミス ネットワークに透過的に接続されている仮想マシンで実行される IT ワークロードで構成されます。オンプレミス ユーザーはこの違いに気付かないでしょう。
    
## ハイブリッド クラウドの要素

Microsoft クラウド プラットフォームおよびサービスを使用するハイブリッド クラウド シナリオを計画して実装する際には、次の要素を考慮する必要があります。
  
- ネットワーク
    
    ハイブリッド クラウド シナリオのネットワークには、Microsoft クラウド プラットフォームおよびサービスへの接続と、負荷のピーク時に高パフォーマンスを実現するのに十分な帯域幅とが含まれています。詳細については、「[エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク](microsoft-cloud-networking-for-enterprise-architects.md)」をご覧ください。
    
- ID
    
    SaaS と Azure PaaS ハイブリッド シナリオの ID には、共通の ID プロバイダーとして Azure AD を含めることができます。このプロバイダーは、オンプレミスの Windows Server AD と同期するか、Windows Server AD またはその他の ID プロバイダーとフェデレーションすることができます。また、オンプレミスの ID インフラストラクチャを Azure IaaS に拡張することもできます。詳細については、「[エンタープライズ アーキテクトのための Microsoft クラウド ID](microsoft-cloud-identity-for-enterprise-architects.md)」をご覧ください。
    
- セキュリティ
    
    ハイブリッド クラウド シナリオのセキュリティには、ID の保護と管理、データ保護、管理権限の管理、脅威の認識、およびガバナンスとセキュリティ ポリシーの実装が含まれます。詳細については、「[エンタープライズ アーキテクトのための Microsoft クラウドのセキュリティ](https://technet.microsoft.com/library/dn919927.aspx#security)」を参照してください。
    
- 管理
    
    ハイブリッド クラウド シナリオの管理には、設定、データ、アカウント、ポリシー、およびアクセス許可を維持し、シナリオの要素の継続的な正常性およびそのパフォーマンスを監視する機能が含まれます。また、Azure IaaS での仮想マシンの管理にも、Systems Management Server などの同じツール セットを使用できます。
    
## See Also

#### 

[エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)
#### 

[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)

