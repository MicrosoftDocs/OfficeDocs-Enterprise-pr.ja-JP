---
title: SharePoint 2013 用の Microsoft Azure アーキテクチャ
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Architecture
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: 'Summary: SharePoint 2013 solutions can be hosted in Microsoft Azure virtual machines. Learn which type of solutions are a good fit and how to set up Microsoft Azure to host one.'
ms.openlocfilehash: fee388f56faf2b30534d9a56926d9d62a176df19
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997899"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a>SharePoint 2013 用の Microsoft Azure アーキテクチャ

Azure は SharePoint Server 2013 ソリューションをホストするための優れた環境です。 ほとんどの場合、Microsoft 365 をお勧めしますが、Azure でホストされている SharePoint Server ファームは特定のソリューションに適したオプションになります。 この記事では、SharePoint ソリューションが Azure プラットフォームに適合するように設計する方法について説明します。 次の 2 つのソリューションが例として使用されています。
  
- [Microsoft Azure での SharePoint Server 2013 の障害復旧](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a>推奨されている Azure インフラストラクチャ サービスの SharePoint ソリューション

Azure infrastructure services is a compelling option for hosting SharePoint solutions. Some solutions are a better fit for this platform than others. The following table shows recommended solutions.
  
|**解決方法**|**Azure でそのソリューションが推奨されている理由**|
|:-----|:-----|
|開発環境とテスト環境  <br/> |これらの環境を簡単に作成して管理できます。  <br/> |
|Azure に対するオンプレミス SharePoint ファームの障害復旧  <br/> |**ホストされているセカンダリ データセンター** 別の地域にあるセカンダリ データセンターに投資するのではなく、Azure を使用します。 <br/> **Lower-cost disaster-recovery environments** Maintain and pay for fewer resources than an on-premises disaster recovery environment. The number of resources depends on the disaster recovery environment you choose: cold standby, warm standby, or hot standby. <br/> **More elastic platform** In the event of a disaster, easily scale-out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources. <br/> 「[Microsoft Azure での SharePoint Server 2013 の障害復旧](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)」をご覧ください。  <br/> |
|Microsoft 365 で利用できない機能とスケールを使用する、インターネットに接続されたサイト  <br/> |**作業の重点** インフラストラクチャの構築ではなく、魅力的なサイトの構築のほうに集中できます。 <br/> **Take advantage of elasticity in Azure** Size the farm for the demand by adding new servers, and pay only for resources you need. Dynamic machine allocation is not supported (auto scale). <br/> **Azure Active Directory (AD) の使用** ユーザー アカウントに関して Azure AD を活用します。 <br/> **Microsoft 365 で利用できない SharePoint 機能の追加**詳細なレポートおよび web 分析を追加します。 <br/> 「[SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)」をご覧ください。  <br/> |
|Microsoft 365 またはオンプレミス環境をサポートするためのアプリファーム  <br/> |**アプリのビルド、テスト、ホスト** Azure で、オンプレミス環境とクラウド環境の両方をサポートできます。 <br/> **このロールのホスト** オンプレミス環境用の新しいハードウェアを購入する代わりに、Azure で行います。 <br/> |
   
イントラネットとコラボレーションのソリューション、およびワークロードに関しては、以下の選択肢を考慮してください。
  
- Microsoft 365 がビジネス要件を満たしているかどうか、またはソリューションの一部であるかどうかを判断します。 Microsoft 365 には、常に最新の豊富な機能セットが用意されています。
    
- Microsoft 365 がお客様のすべてのビジネス要件を満たしていない場合は、Microsoft コンサルティングサービス (MCS) からの SharePoint 2013 の標準実装を検討してください。 標準のアーキテクチャは、カスタマイズされたアーキテクチャよりもソリューションの実装が迅速かつ安価で、なおかつ簡単です。 
    
- 標準実装がビジネス要件を満たさない場合には、カスタマイズされたオンプレミスのソリューションを考慮します。
    
- If using a cloud platform is important for your business requirements, consider a standard or customized implementation of SharePoint 2013 hosted in Azure infrastructure services. SharePoint solutions are much easier to support in Azure than other non-native Microsoft public cloud platforms.
    
## <a name="before-you-design-the-azure-environment"></a>Azure 環境を設計する前に

While this article uses example SharePoint topologies, you can use these design concepts with any SharePoint farm topology. Before you design the Azure environment, use the following topology, architecture, capacity, and performance guidance to design the SharePoint farm:
  
- [SharePoint 2013 の IT 担当者向けアーキテクチャ設計](https://technet.microsoft.com/sharepoint/fp123594.aspx)
    
- [Plan for performance and capacity management in SharePoint Server 2013](https://technet.microsoft.com/library/8dd52916-f77d-4444-b593-1f7d6f330e5f.aspx)
    
## <a name="determine-the-active-directory-domain-type"></a>Active Directory ドメインの種類の決定

Each SharePoint Server farm relies on Active Directory to provide administrative accounts for farm setup. At this time, there are two options for SharePoint solutions in Azure. These are described in the following table.
  
|**オプション**|**説明**|
|:-----|:-----|
|専用ドメイン  <br/> |You can deploy a dedicated and isolated Active Directory domain to Azure to support your SharePoint farm. This is a good choice for public-facing Internet sites.  <br/> |
|クロスプレミス接続を使用したオンプレミス ドメインの拡張  <br/> |When you extend the on-premises domain through a cross-premises connection, users access the SharePoint farm via your intranet as if it were hosted on-premises. You can take advantage of your on-premises Active Directory and DNS implementation.  <br/> オンプレミスのファームとの間でフェールオーバーするために Azure で障害復旧環境を構築するには、クロスプレミス接続が必要になります。  <br/> |
   
This article includes design concepts for extending the on-premises domain through a cross-premises connection. If your solution uses a dedicated domain, you don't need a cross-premises connection.
  
## <a name="design-the-virtual-network"></a>仮想ネットワークの設計

First you need a virtual network in Azure, which includes subnets on which you will place your virtual machines. The virtual network needs a private IP address space, portions of which you assign to the subnets.
  
クロスプレミス接続を使用して Azure にオンプレミス ネットワークを拡張する場合は (このことは障害回復環境で必要となります)、オンプレミス環境と他の Azure 仮想ネットワークを含む組織ネットワークの他のどの場所にも使用されていないプライベート アドレス空間を選択する必要があります。 
  
**図 1:Azure での仮想ネットワークを使用したオンプレミス環境**

![Microsoft Azure virtual network design for a SharePoint solution. One subnet for the Azure gateway. One subnet for the virtual machines.](media/OPrrasconWA-AZarch.png)
  
この図では次のようになっています。
  
- A virtual network in Azure is illustrated side-by-side to the on-premises environment. The two environments are not yet connected by a cross-premises connection, which can be a site-to-site VPN connection or ExpressRoute.
    
- At this point, the virtual network just includes the subnets and no other architectural elements. One subnet will host the Azure gateway and other subnets host the tiers of the SharePoint farm, with an additional one for Active Directory and DNS.
    
## <a name="add-cross-premises-connectivity"></a>クロスプレミス接続の追加

The next deployment step is to create the cross-premises connection (if this applies to your solution). For cross-premises connections, a Azure gateway resides in a separate gateway subnet, which you must create and assign an address space. 
  
クロスプレミス接続を計画する場合は、Azure ゲートウェイと、オンプレミス ゲートウェイ デバイスへの接続を定義して作成します。
  
**図 2:オンプレミス環境と Azure 間でサイト間接続を提供するための Azure ゲートウェイとオンプレミス ゲートウェイ デバイスの使用**

![オンプレミス環境はクロスプレミス接続 (サイト間 VPN 接続または ExpressRoute が可能) を介して Azure 仮想ネットワークに接続されています](media/AZarch-VPNgtwyconnct.png)
  
この図では次のようになっています。
  
- 前述の図に加えられた点として、オンプレミス環境がクロスプレミス接続 (サイト間 VPN 接続または ExpressRoute である場合もあります) を介して Azure 仮想ネットワークに接続されています。
    
- Azure ゲートウェイはゲートウェイ サブネット上に配置します。
    
- オンプレミス環境には、ルーターまたは VPN サーバーなどのゲートウェイ デバイスが含まれます。
    
クロスプレミス仮想ネットワークの計画と作成に関する詳細については、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」をご参照ください。
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a>Active Directory ドメインサービス (AD DS) と DNS を追加する

Azure における障害復旧の場合、Windows Server AD と DNS をハイブリッド シナリオで展開します。このとき、Windows Server AD は、オンプレミスと Azure 仮想マシンの両方に展開されます。
  
**図 3: Active Directory ドメインのハイブリッド構成**

![Azure の仮想ネットワークと SharePoint ファームのサブネットに配置された 2 つの仮想マシンは、レプリカ ドメイン コントローラーおよび DNS サーバーです](media/AZarch-HyADdomainConfig.png)
  
This diagram builds on the previous diagrams by adding two virtual machines to a Windows Server AD and DNS subnet. These virtual machines are replica domain controllers and DNS servers. They are an extension of the on-premises Windows Server AD environment. 
  
The following table provides configuration recommendations for these virtual machines in Azure. Use these as a starting point for designing your own environment—even for a dedicated domain where your Azure environment doesn't communicate with your on-premises environment.
  
|**アイテム**|**構成**|
|:-----|:-----|
|Azure での仮想マシンのサイズ  <br/> |標準層の A1 または A2 サイズ  <br/> |
|オペレーティング システム  <br/> |Windows Server 2012 R2  <br/> |
|Active Directory ロール  <br/> |AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the cross-premises connection.  <br/> 変更率の高いマルチドメイン環境の場合 (一般的ではありません)、オンプレミスのドメイン コントローラーが、Azure 内のグローバル カタログ サーバーと同期しないように構成して、レプリケーション トラフィックを削減します。  <br/> |
|DNS ロール  <br/> |ドメイン コントローラーで DNS サーバー サービスをインストールして構成します。  <br/> |
|データ ディスク  <br/> |Place the Active Directory database, logs, and SYSVOL on additional Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure.  <br/> |
|IP アドレス  <br/> |静的 IP アドレスを使用して仮想ネットワークを構成し、ドメイン コントローラーの構成後にこれらのアドレスを仮想ネットワーク内の仮想マシンに割り当てます。  <br/> |
   
> [!IMPORTANT]
> Before you deploy Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These help you determine if a different architecture or different configuration settings are needed for your solution. 
  
## <a name="add-the-sharepoint-farm"></a>SharePoint ファームの追加

該当するサブネット上の層に SharePoint ファームの仮想マシンを配置します。
  
**図 4: SharePoint 仮想マシンの配置**

![SharePoint ファーム サブネット内の Azure 仮想ネットワークに追加された、データベース サーバーと SharePoint サーバーの役割](media/AZarch-SPVMsinCloudSer.png)
  
この図は前の図に基づいて作成されていて、それぞれの層で SharePoint ファーム サーバー ロールが追加されています。
  
- SQL Server を実行する 2 つのデータベース仮想マシンによってデータベース層が作成されます。
    
- それぞれのロール (フロント エンド サーバー、分散キャッシュ サーバー、バック エンド サーバー) ごとに、SharePoint Server 2013 を実行する 2 つの仮想マシンが含まれています。
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a>可用性セットと障害ドメイン用のサーバー ロールの設計と調整

A fault domain is a grouping of hardware in which role instances run. Virtual machines within the same fault domain can be updated by the Azure infrastructure at the same time. Or, they can fail at the same time because they share the same rack. To avoid the risk of having two virtual machines on the same fault domain, you can configure your virtual machines as an availability set, which ensures that each virtual machine is in a different fault domain. If three virtual machines are configured as an availability set, Azure guarantees that no more than two of the virtual machines are located in the same fault domain.
  
When you design the Azure architecture for a SharePoint farm, configure identical server roles to be part of an availability set. This ensures that your virtual machines are spread across multiple fault domains.
  
**図 5: SharePoint ファーム層の高可用性を確保するための Azure 可用性セットの使用**

![SharePoint 2013 ソリューションのための Azure インフラストラクチャ内の可用性セットの構成](media/AZenv-WinAzureAvailSetsHA.png)
  
This diagram calls out the configuration of availability sets within the Azure infrastructure. Each of the following roles share a separate availability set:
  
- Active Directory と DNS
    
- データベース
    
- バック エンド
    
- 分散キャッシュ
    
- フロント エンド
    
The SharePoint farm might need to be fine tuned in the Azure platform. To ensure high availability of all components, ensure that the server roles are all configured identically.
  
Here is an example that shows a standard Internet Sites architecture that meets specific capacity and performance goals. This example is featured in the following architecture model: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).
  
**図 6: 3 層ファームにおけるキャパシティとパフォーマンスの目標に関する計画例**

![特定の容量とパフォーマンスの目標を達成するコンポーネント割り当てを含む標準的な SharePoint 2013 のインターネット サイトのアーキテクチャ](media/AZarch-CapPerfexmpArch.png)
  
この図では次のようになっています。
  
- 3 層ファームは、Web サーバー、アプリケーション サーバー、データベース サーバーで表されます。
    
- 3 つの Web サーバーは複数のコンポーネントを含んでおり、同一に構成されています。
    
- 2 つのデータベース サーバーは同一に構成されています。
    
- The three application servers are not configured identically. These server roles require fine tuning for availability sets in Azure.
    
アプリケーション サーバー層について詳しく見てみましょう。
  
**図 7: 調整前のアプリケーション サーバー層**

![Microsoft Azure 可用性セットのために調整する前の SharePoint Server 2013 アプリケーション サーバー層の例](media/AZarch-AppServtierBefore.png)
  
この図では次のようになっています。
  
- 3 つのサーバーがアプリケーション層に含まれています。
    
- 最初のサーバーには 4 つのコンポーネントが含まれています。
    
- 2　番目のサーバーには、3 つのコンポーネントが含まれています。
    
- 3 番目のサーバーには、2 つのコンポーネントが含まれています。
    
You determine the number of components by the performance and capacity targets for the farm. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.
  
**図 8: 調整後のアプリケーション サーバー層**

![Microsoft Azure 可用性セットのために調整した後の SharePoint Server 2013 アプリケーション サーバー層の例](media/AZarch-AppServtierAfter.png)
  
この図は、同じ 4 つのコンポーネントを含み、同一に構成されている 3 つのアプリケーション サーバーすべてを示しています。
  
SharePoint ファームの各層に可用性セットを追加すると、実装作業が完了します。
  
**図 9:Azure インフラストラクチャ サービスに実装された SharePoint ファーム**

![仮想ネットワーク、クロスプレミス接続、サブネット、VM、および可用性の設定を含む Azure インフラストラクチャ サービスの SharePoint 2013 ファームの例](media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
この図は、Azure インフラストラクチャ サービスに実装された、各層内のサーバー用の障害ドメインを提供する可用性セットを備えた SharePoint ファームを示しています。
  
## <a name="see-also"></a>関連項目

[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.yml)
  
[SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[Microsoft Azure での SharePoint Server 2013 の障害復旧](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)


