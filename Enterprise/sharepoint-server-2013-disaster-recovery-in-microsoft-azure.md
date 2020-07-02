---
title: Microsoft Azure での SharePoint Server 2013 の障害復旧
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 04/17/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Deployment
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: 'Summary: Using Azure, you can create a disaster-recovery environment for your on-premises SharePoint farm. This article describes how to design and implement this solution.'
ms.openlocfilehash: 101d87b1a25d2b3ac8a7ae29832e52c805ecdc4c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998169"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>Microsoft Azure での SharePoint Server 2013 の障害復旧

 Azure を使用すると、オンプレミス SharePoint ファーム用の障害復旧環境を作成できます。 この記事では、このソリューションの設計と実装の方法を取り上げます。

 **SharePoint Server 2013 障害復旧の概要ビデオをご覧ください**
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]
  
 When disaster strikes your SharePoint on-premises environment, your top priority is to get the system running again quickly. Disaster recovery with SharePoint is quicker and easier when you have a backup environment already running in Microsoft Azure. This video explains the main concepts of a SharePoint warm failover environment and complements the full details available in this article.
  
この記事では、ソリューション モデル「 **Microsoft Azure における SharePoint 障害復旧** 」を使用します。
  
[![Azure への SharePoint 障害回復プロセス](media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)
  
 [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)
  
## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>障害復旧のための Azure インフラストラクチャ サービスの使用

Many organizations do not have a disaster recovery environment for SharePoint, which can be expensive to build and maintain on-premises. Azure Infrastructure Services provides compelling options for disaster recovery environments that are more flexible and less expensive than the on-premises alternatives.
  
Azure インフラストラクチャ サービス を使用する利点には、以下が含まれます。
  
- **Fewer costly resources** Maintain and pay for fewer resources than on-premises disaster recovery environments. The number of resources depends on which disaster-recovery environment you choose: cold standby, warm standby, or hot standby.
    
- **Better resource flexibility** In the event of a disaster, easily scale out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources.
    
- **低額なデータセンターのコミットメント** 別の地域にあるセカンダリ データセンターに投資するのではなく、Azure インフラストラクチャ サービス を使用します。
    
There are less-complex options for organizations just getting started with disaster recovery and advanced options for organizations with high-resilience requirements. The definitions for cold, warm, and hot standby environments are a little different when the environment is hosted on a cloud platform. The following table describes these environments for building a SharePoint recovery farm in Azure.
  
**表: 復旧環境**

|**復旧環境の種類**|**説明**|
|:-----|:-----|
|ホット  <br/> |フルサイズのファームが、スタンバイ状態で準備、更新、実行されています。  <br/> |
|ウォーム  <br/> |ファームが構築され、仮想マシンが実行状態で、更新されています。  <br/> 復旧には、コンテンツ データベースの接続、サービス アプリケーションの準備、コンテンツのクロールが含まれます。  <br/> このファームは、運用ファームよりも小規模にでき、フルサイズのユーザー ベースに対応するためにスケールアウトできます。  <br/> |
|コールド  <br/> |ファームは完全に構築されますが、仮想マシンは停止状態です。  <br/> 環境の保守には、仮想マシンを時折始動すること、環境への修正プログラムの適用、更新、検証が含まれます。  <br/> 障害発生時に、環境全体を開始します。  <br/> |
   
It's important to evaluate your organization's Recovery Time Objectives (RTOs) and Recovery Point Objectives (RPOs). These requirements determine which environment is the most appropriate investment for your organization.
  
The guidance in this article describes how to implement a warm standby environment. You can also adapt it to a cold standby environment, although you need to follow additional procedures to support this kind of environment. This article does not describe how to implement a hot standby environment.
  
障害復旧ソリューションの詳細については、「[High availability and disaster recovery concepts in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114)」および「[Choose a disaster recovery strategy for SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=203228)」をご覧ください。
  
## <a name="solution-description"></a>ソリューションの説明

ウォーム スタンバイ障害復旧ソリューションには、以下の環境が必要です。
  
- オンプレミスの SharePoint 運用ファーム
    
- Azure の SharePoint 復旧ファーム
    
- 2 つの環境間のサイト間 VPN 接続
    
次の図に、これら 3 つの要素を示します。
  
**図: Azure におけるウォーム スタンバイ ソリューションの要素**

![Azure の SharePoint ウォーム スタンバイ ソリューションの要素](media/AZarch-AZWarmStndby.png)
  
分散ファイル システム レプリケーション (DFSR) を使用した SQL Server ログ配布により、データベース バックアップとトランザクション ログを Azure 内の復旧ファームにコピーします。 
  
- DFSR transfers logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.
    
- ログは、Azure の復旧環境で SQL Server に再生されます。
    
- 復旧手順が実行されるまでは、復旧環境にあるログ配布対象の SharePoint コンテンツ データベースには接続しません。
    
次のステップを実行してファームを復旧します。
  
1. ログ配布を停止します。
    
2. プライマリ ファームへのトラフィックの受け入れを停止します。
    
3. 最後のトランザクション ログを再生します。
    
4. コンテンツ データベースをファームに接続します。
    
5. レプリケートされたサービス データベースに基づいてサービス アプリケーションを復元します。
    
6. 復旧ファームを指すように、ドメイン ネーム システム (DNS) レコードを更新します。
    
7. フル クロールを開始します。
    
We recommend that you rehearse these steps regularly and document them to help ensure that your live recovery runs smoothly. Attaching content databases and restoring service applications can take some time and typically involves some manual configuration.
  
復旧が実行されると、このソリューションにより次の表に示すアイテムが提供されます。
  
**表: ソリューションによる復旧対象**

|**アイテム**|**説明**|
|:-----|:-----|
|サイトおよびコンテンツ  <br/> |復旧環境で、サイトとコンテンツを利用できます。  <br/> |
|検索の新しいインスタンス  <br/> |In this warm standby solution, search is not restored from search databases. Search components in the recovery farm are configured as similarly as possible to the production farm. After the sites and content are restored, a full crawl is started to rebuild the search index. You do not need to wait for the crawl to complete to make the sites and content available.  <br/> |
|サービス  <br/> | Services that store data in databases are restored from the log-shipped databases. Services that do not store data in databases are simply started. <br/>  Not all services with databases need to be restored. The following services do not need to be restored from databases and can simply be started after failover: <br/>  Usage and Health Data Collection <br/>  State Service <br/>  Word Automation <br/>  データベースを使用しないその他のサービス <br/> |
   
You can work with Microsoft Consulting Services (MCS) or a partner to address more-complex recovery objectives. These are summarized in the following table.
  
**表: MCS またはパートナーが対応できるその他のアイテム**

|**アイテム**|**説明**|
|:-----|:-----|
|カスタム ファーム ソリューションの同期  <br/> |Ideally, the recovery farm configuration is identical to the production farm. You can work with a consultant or partner to evaluate whether custom farm solutions are replicated and whether the process is in place for keeping the two environments synchronized.  <br/> |
|オンプレミスのデータ ソースへの接続  <br/> |バックアップ ドメイン コントローラー (BDC) 接続などのバックエンド データ システムへの接続のレプリケート、およびコンテンツ ソースの検索は実際的ではない場合があります。  <br/> |
|検索の復元シナリオ  <br/> |Because enterprise search deployments tend to be fairly unique and complex, restoring search from databases requires a greater investment. You can work with a consultant or partner to identify and implement search restore scenarios that your organization might require.  <br/> |
   
この記事で示されているガイダンスでは、オンプレミス ファームの設計と展開が既に行われていると想定しています。
  
## <a name="detailed-architecture"></a>詳細なアーキテクチャ

Azure の復旧ファーム構成は、以下を含め、オンプレミスの運用ファームと同じであることが理想的です。
  
- 同じ表記のサーバー ロール
    
- 同じカスタマイズ構成
    
- 同じ検索コンポーネント構成
    
The environment in Azure can be a smaller version of the production farm. If you plan to scale out the recovery farm after failover, it's important that each type of server role be initially represented.
  
Some configurations might not be practical to replicate in the failover environment. Be sure to test the failover procedures and environment to help ensure that the failover farm provides the expected service level.
  
This solution doesn't prescribe a specific topology for a SharePoint farm. The focus of this solution is to use Azure for the failover farm and to implement log shipping and DFSR between the two environments.
  
### <a name="warm-standby-environments"></a>ウォーム スタンバイ環境

In a warm standby environment, all virtual machines in the Azure environment are running. The environment is ready for a failover exercise or event.
  
次の図は、オンプレミス SharePoint ファームから、ウォーム スタンバイ環境として構成されている Azure ベースの SharePoint ファームに対する障害復旧ソリューションを示しています。
  
**図: 運用ファームとウォーム スタンバイ復旧ファームのトポロジと主な要素**

![SharePoint ファームとウォーム スタンバイ復旧ファームのトポロジ](media/AZarch-AZWarmStndby.png)
  
この図では次のようになっています。
  
- オンプレミス SharePoint ファームと Azure 内のウォーム スタンバイ ファームの 2 つの環境が並べて示されています。
    
- それぞれの環境には、ファイル共有が含まれます。
    
- Each farm includes four tiers. To achieve high availability, each tier includes two servers or virtual machines that are configured identically for a specific role, such as front-end services, distributed cache, back-end services, and databases. It isn't important in this illustration to call out specific components. The two farms are configured identically.
    
- The fourth tier is the database tier. Log shipping is used to copy logs from the secondary database server in the on-premises environment to the file share in the same environment.
    
- DFSR が、オンプレミス環境にあるファイル共有のファイルを、Azure 環境のファイル共有にコピーします。
    
- ログ配布により、Azure 環境のファイル共有のログが、復旧環境の SQL Server AlwaysOn 可用性グループのプライマリ レプリカに再生されます。
    
### <a name="cold-standby-environments"></a>コールド スタンバイ環境

In a cold standby environment, most of the SharePoint farm virtual machines can be shut down. (We recommend occasionally starting the virtual machines, such as every two weeks or once a month, so that each virtual machine can sync with the domain.) The following virtual machines in the Azure recovery environment must remain running to help ensure continuous operations of log shipping and DFSR:
  
- ファイル共有
    
- プライマリ データベース サーバー
    
- Windows Server Active Directory ドメイン サービスと DNS を実行している少なくとも 1 つの仮想マシン
    
The following figure shows an Azure failover environment in which the file share virtual machine and the primary SharePoint database virtual machine are running. All other SharePoint virtual machines are stopped. The virtual machine that is running Windows Server Active Directory and DNS is not shown.
  
**図: 稼働中の仮想マシンが含まれるコールド スタンバイ復旧ファーム**

![Azure の SharePoint コールド スタンバイ ソリューションの要素](media/AZarch-AZColdStndby.png)
  
コールド スタンバイ環境にフェールオーバーした後、すべての仮想マシンが始動されます。SQL Server AlwaysOn 可用性グループなど、データベース サーバーの高可用性を実現するための方式が構成されていなければなりません。
  
複数のストレージ グループが実装されている場合 (複数のデータベースが複数の SQL Server 高可用性セットに分散されている場合)、そのストレージ グループに関連付けられているログを受け入れるために、各ストレージ グループのプライマリ データベースが実行中でなければなりません。
  
### <a name="skills-and-experience"></a>スキルと経験

Multiple technologies are used in this disaster recovery solution. To help ensure that these technologies interact as expected, each component in the on-premises and Azure environment must be installed and configured correctly. We recommend that the person or team who sets up this solution have a strong working knowledge of and hands-on skills with the technologies described in the following articles:
  
- [DFS (Distributed File System) レプリケーション サービス](https://go.microsoft.com/fwlink/p/?LinkId=392698)
    
- [Windows Server フェールオーバー クラスタリング (WSFC) と SQL Server](https://go.microsoft.com/fwlink/p/?LinkId=392701)
    
- [AlwaysOn 可用性グループ (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392725)
    
- [SQL Server データベースのバックアップと復元](https://go.microsoft.com/fwlink/p/?LinkId=392728)
    
- [SharePoint Server 2013 のインストールとファーム展開](https://go.microsoft.com/fwlink/p/?LinkId=393119)
    
- [Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=392729)
    
Finally, we recommend scripting skills that you can use to automate tasks associated with these technologies. It's possible to use the available user interfaces to complete all the tasks described in this solution. However, a manual approach can be time consuming and error prone and delivers inconsistent results.
  
In addition to Windows PowerShell, there are also Windows PowerShell libraries for SQL Server, SharePoint Server, and Azure. Don't forget T-SQL, which can also help reduce the time to configure and maintain your disaster-recovery environment.
  
## <a name="disaster-recovery-roadmap"></a>障害復旧のロードマップ

![SharePoint 障害回復のロードマップを示す図。](media/Azure-DRroadmap.png)
  
このロードマップでは、SharePoint Server 2013 ファームが既に運用環境に展開されていることが前提となります。
  
**表: 障害復旧のロードマップ**

|**フェーズ**|**説明**|
|:-----|:-----|
|フェーズ 1  <br/> |障害回復環境を設計します。  <br/> |
|フェーズ 2  <br/> |Azure Virtual Network と VPN 接続を作成します。  <br/> |
|フェーズ 3  <br/> |Windows Active Directory とドメイン ネーム サービスを Azure Virtual Network に展開します。  <br/> |
|フェーズ 4  <br/> |Azure に SharePoint 復旧ファームを展開します。  <br/> |
|フェーズ 5  <br/> |ファーム間の DFSR を設定します。  <br/> |
|フェーズ 6  <br/> |復旧ファームに対するログ配布を設定します。  <br/> |
|フェーズ 7  <br/> | Validate failover and recovery solutions. This includes the following procedures and technologies: <br/>  ログ配布を停止します。 <br/>  バックアップを復元します。 <br/>  コンテンツをクロールします。 <br/>  サービスを復元します。 <br/>  DNS レコードを管理します。 <br/> |
   
## <a name="phase-1-design-the-disaster-recovery-environment"></a>フェーズ 1: 障害復旧環境の設計

「[SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md)」に記されているガイダンスに従って、SharePoint 復旧ファームを含む、障害復旧環境を設計します。 Azure Visio ファイル[の SharePoint 障害復旧ソリューション](https://go.microsoft.com/fwlink/p/?LinkId=392554)のグラフィックスを使用して、設計プロセスを開始できます。 環境全体を設計してから、Azure 環境で作業を開始することをお勧めします。
  
「[SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md)」に記されている仮想ネットワーク、VPN 接続、Active Directory、および SharePoint ファームを設計するためのガイダンスに加え、Azure 環境にファイル共有ロールを追加してください。
  
To support log shipping in a disaster-recovery solution, a file share virtual machine is added to the subnet where the database roles reside. The file share also serves as the third node of a Node Majority for the SQL Server AlwaysOn availability group. This is the recommended configuration for a standard SharePoint farm that uses SQL Server AlwaysOn availability groups. 
  
> [!NOTE]
> It is important to review the prerequisites for a database to participate in a SQL Server AlwaysOn availability group. For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups](https://go.microsoft.com/fwlink/p/?LinkId=510870). 
  
**図: 障害復旧ソリューションに使用するファイル サーバーの配置**

![SharePoint データベース サーバーの役割を含む同じクラウド サービスに追加されたファイル共有 VM を示します。](media/AZenv-FSforDFSRandWSFC.png)
  
In this diagram, a file share virtual machine is added to the same subnet in Azure that contains the database server roles. Do not add the file share virtual machine to an availability set with other server roles, such as the SQL Server roles.
  
If you are concerned about the high availability of the logs, consider taking a different approach by using [SQL Server backup and restore with Azure Blob Storage Service](https://go.microsoft.com/fwlink/p/?LinkId=393113). This is a new feature in Azure that saves logs directly to a blob storage URL. This solution does not include guidance about using this feature.
  
When you design the recovery farm, keep in mind that a successful disaster recovery environment accurately reflects the production farm that you want to recover. The size of the recovery farm is not the most important thing in the recovery farm's design, deployment, and testing. Farm scale varies from organization to organization based on business requirements. It might be possible to use a scaled-down farm for a short outage or until performance and capacity demands require you to scale the farm.
  
Configure the recovery farm as identically as possible to the production farm so that it meets your service level agreement (SLA) requirements and provides the functionality that you need to support your business. When you design the disaster recovery environment, also look at your change management process for your production environment. We recommend that you extend the change management process to the recovery environment by updating the recovery environment at the same interval as the production environment. As part of the change management process, we recommend maintaining a detailed inventory of your farm configuration, applications, and users. 
  
## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>フェーズ 2: Azure Virtual Network と VPN 接続の作成

[Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) shows you how to plan and deploy the virtual network in Azure and how to create the VPN connection. Follow the guidance in the topic to complete the following procedures:
  
- 仮想ネットワーク のプライベート IP アドレス空間を計画します。
    
- 仮想ネットワーク のルーティング インフラストラクチャの変更を計画します。
    
- オンプレミス VPN デバイスとの間のトラフィックのファイアウォール規則を計画します。
    
- Azure でクロスプレミスの仮想ネットワークを作成します。
    
- オンプレミス ネットワークと 仮想ネットワーク 間のルーティングを構成します。
    
## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>フェーズ 3: Active Directory とドメイン ネーム サービスの Azure Virtual Network への展開

このフェーズでは、「[SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md)」で説明されているハイブリッド シナリオを使用して、次の図に示されているように、Windows Server Active Directory と DNS の両方を 仮想ネットワーク に展開します。
  
**図: Active Directory ドメインのハイブリッド構成**

![Azure 仮想ネットワークに展開された2つの仮想マシンと、SharePoint ファームサブネットがレプリカドメインコントローラーおよび DNS サーバーである](media/AZarch-HyADdomainConfig.png)
  
In the illustration, two virtual machines are deployed to the same subnet. These virtual machines are each hosting two roles: Active Directory and DNS.
  
Before deploying Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These guidelines help you determine whether you need a different architecture or different configuration settings for your solution.
  
Azure におけるドメイン コントローラーの設定に関する詳しいガイドラインは、「[Azure の仮想ネットワークでのレプリカ Active Directory ドメイン コントローラーのインストール](https://go.microsoft.com/fwlink/p/?LinkId=392687)」をご覧ください。
  
Before this phase, you didn't deploy virtual machines to the Virtual Network. The virtual machines for hosting Active Directory and DNS are likely not the largest virtual machines you need for the solution. Before you deploy these virtual machines, first create the largest virtual machine that you plan to use in your Virtual Network. This helps ensure that your solution lands on a tag in Azure that allows the largest size you need. You do not need to configure this virtual machine at this time. Simply create it, and set it aside. If you do not do this, you might run into a limitation when you try to create larger virtual machines later, which was an issue at the time this article was written. 
  
## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>フェーズ 4: Azure における SharePoint 復旧ファームの展開

Deploy the SharePoint farm in your Virtual Network according to your design plans. It might be helpful to review [Planning for SharePoint 2013 on Azure Infrastructure Services](https://go.microsoft.com/fwlink/p/?LinkId=400984) before you deploy SharePoint roles in Azure.
  
概念実証環境の構築を介して学んだ以下の点を考慮に入れてください。
  
- Azure ポータルまたは PowerShell を使用して仮想マシンを作成します。
    
- Azure and Hyper-V do not support dynamic memory. Be sure this is factored into your performance and capacity plans.
    
- Restart virtual machines through the Azure interface, not from the virtual machine logon itself. Using the Azure interface works better and is more predictable.
    
- If you want to shut down a virtual machine to save costs, use the Azure interface. If you shut down from the virtual machine logon, charges continue to accrue.
    
- 仮想マシンの命名規則を使用します。
    
- 仮想マシンの展開先のデータセンターの場所に注意します。
    
- Azure の自動スケール機能は、SharePoint ロールに関してはサポートされていません。
    
- サイト コレクションなど、ファーム内にある復元対象のアイテムは構成できません。 
    
## <a name="phase-5-set-up-dfsr-between-the-farms"></a>フェーズ 5: ファーム間の DFSR の設定

To set up file replication by using DFSR, use the DNS Management snap-in. However, before the DFSR setup, log on to your on-premises file server and Azure file server and enable the service in Windows.
  
サーバー マネージャーのダッシュボードから、以下のステップを実行します。
  
- ローカル サーバーを構成します。
    
- [ **役割と機能の追加ウィザード**] を起動します。
    
- [ **ファイル サービスと記憶域サービス**] ノードを開きます。
    
- [ **DFS 名前空間**] および [ **DFS レプリケーション**] を選択します。
    
- [ **次へ**] をクリックして、ウィザードのステップを完了します。
    
次の表に、DFSR リファレンスの記事とブログ投稿へのリンクを示します。
  
**表: DFSR のリファレンス記事**

|**タイトル**|**説明**|
|:-----|:-----|
|[レプリケーション](https://go.microsoft.com/fwlink/p/?LinkId=392732) <br/> |レプリケーションに関するリンクが含まれる DFS 管理のための TechNet トピック  <br/> |
|[DFS レプリケーション: サバイバル ガイド](https://go.microsoft.com/fwlink/p/?LinkId=392737) <br/> |DFS 情報へのリンクが含まれる Wiki  <br/> |
|[DFS レプリケーション: よく寄せられる質問 (FAQ)](https://go.microsoft.com/fwlink/p/?LinkId=392738) <br/> |DFS レプリケーションに関する TechNet トピック  <br/> |
|[Jose Barreto のブログ](https://go.microsoft.com/fwlink/p/?LinkId=392739) <br/> |Microsoft のファイル サーバー チームのプリンシパル プログラム マネージャーが書き込んだブログ  <br/> |
|[Microsoft のストレージ チーム - ファイル キャビネット ブログ](https://go.microsoft.com/fwlink/p/?LinkId=392740) <br/> |Windows Server のファイル サービスとストレージ機能に関するブログ  <br/> |
   
## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>フェーズ 6: 復旧ファームに対するログ配布の設定

Log shipping is the critical component for setting up disaster recovery in this environment. You can use log shipping to automatically send transaction log files for databases from a primary database server instance to a secondary database server instance. To set up log shipping, see [Configure log shipping in SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-log-shipping). 
  
> [!IMPORTANT]
> Log shipping support in SharePoint Server is limited to certain databases. For more information, see [Supported high availability and disaster recovery options for SharePoint databases (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121). 
  
## <a name="phase-7-validate-failover-and-recovery"></a>フェーズ 7: フェールオーバーと復旧の検証

The goal of this final phase is to verify that the disaster recovery solution works as planned. To do this, create a failover event that shuts down the production farm and starts up the recovery farm as a replacement. You can start a failover scenario manually or by using scripts.
  
The first step is to stop incoming user requests for farm services or content. You can do this by disabling DNS entries or by shutting down the front-end web servers. After the farm is "down," you can fail over to the recovery farm.
  
### <a name="stop-log-shipping"></a>ログ配布の停止

You must stop log shipping before farm recovery. Stop log shipping on the secondary server in Azure first, and then stop it on the primary server on-premises. Use the following script to stop log shipping on the secondary server first and then on the primary server. The database names in the script might be different, depending on your environment.
  
```
-- This script removes log shipping from the server.
-- Commands must be executed on the secondary server first and then on the primary server.

SET NOCOUNT ON
DECLARE  @PriDB nvarchar(max)
,@SecDB nvarchar(250)
,@PriSrv nvarchar(250)
,@SecSrv nvarchar(250)

Set @PriDB= ''
SET @PriDB = UPPER(@PriDB)
SET @PriDB = REPLACE(@PriDB, ' ', '')
SET @PriDB = '''' + REPLACE(@PriDB, ',', ''', ''') + ''''

Set @SecDB = @PriDB

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_secondary '' + '''''''' + prm.Primary_Database + '''''', '''''' + sec.Secondary_Server + '''''', '''''' + sec.Secondary_database + ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_primary '' + '''''''' + prm.primary_server + '''''', '''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

```

### <a name="restore-the-backups"></a>バックアップの復元

Backups must be restored in the order in which they were created. Before you can restore a particular transaction log backup, you must first restore the following previous backups without rolling back uncommitted transactions (that is, by using  `WITH NORECOVERY`):
  
- The full database backup and the last differential backup - Restore these backups, if any exist, taken before the particular transaction log backup. Before the most recent full or differential database backup was created, the database was using the full recovery model or bulk-logged recovery model.
    
- All transaction log backups - Restore any transaction log backups taken after the full database backup or the differential backup (if you restore one) and before the particular transaction log backup. Log backups must be applied in the sequence in which they were created, without any gaps in the log chain.
    
To recover the content database on the secondary server so that the sites render, remove all database connections before recovery. To restore the database, run the following SQL statement.
  
```
restore database WSS_Content with recovery

```

> [!IMPORTANT]
> When you use T-SQL explicitly, specify either **WITH NORECOVERY** or **WITH RECOVERY** in every RESTORE statement to eliminate ambiguity—this is very important when writing scripts. After the full and differential backups are restored, the transaction logs can be restored in SQL Server Management Studio. Also, because log shipping is already stopped, the content database is in a standby state, so you must change the state to full access.
  
In SQL Server Management Studio, right-click the **WSS_Content** database, point to **Tasks** > **Restore**, and then click **Transaction Log** (if you have not restored the full backup, this is not available). For more information, see[Restore a Transaction Log Backup (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392778).
  
### <a name="crawl-the-content-source"></a>コンテンツ ソースのクロール

You must start a full crawl for each content source to restore the Search Service. Note that you lose some analytics information from the on-premises farm, such as search recommendations. Before you start the full crawls, use the Windows PowerShell cmdlet **Restore-SPEnterpriseSearchServiceApplication** and specify the log-shipped and replicated Search Administration database, **Search_Service__DB_<GUID>**. This cmdlet gives the search configuration, schema, managed properties, rules, and sources and creates a default set of the other components.
  
フル クロールを開始するには、以下のステップを実行します。
  
1. SharePoint 2013 サーバーの全体管理で、**[アプリケーション管理]** > **[サービス アプリケーション]** > **[サービス アプリケーションの管理]** と移動し、クロールする Search Service アプリケーションをクリックします。
    
2. [ **検索管理**] ページで、[ **コンテンツ ソース**] をクリックし、必要なコンテンツ ソースをポイントしてから矢印をクリックし、[ **フル クロールの開始**] をクリックします。
    
### <a name="recover-farm-services"></a>ファーム サービスの復旧

次の表に、ログ配布先データベースが含まれるサービスの復元方法、データベースが含まれるもののログ配布を使用して復元することが推奨されないサービス、およびデータベースが含まれないサービスについて示します。
  
> [!IMPORTANT]
> オンプレミス SharePoint データベースを Azure 環境に復元しても、Azure に手動でまだインストールされていない SharePoint サービスに関しては復元されません。 
  
**表: サービス アプリケーション データベースのリファレンス**

|**ログ配布先データベースから復元するサービス**|**データベースが含まれるものの、データベースを復元しないでサービスを開始することが推奨されているサービス**|**データベースにデータを格納しないサービス (フェールオーバー後にサービスを開始します)。**|
|:-----|:-----|:-----|
| Machine Translation Service <br/>  Managed Metadata Service <br/>  Secure Store Service <br/>  User Profile. (Only the Profile and Social Tagging databases are supported. The Synchronization database is not supported.) <br/>  Microsoft SharePoint Foundation Subscription Settings Service <br/> | Usage and Health Data Collection <br/>  State Service <br/>  Word Automation <br/> | Excel Services <br/>  PerformancePoint Service <br/>  PowerPoint Conversion <br/>  Visio Graphics Service <br/>  Work Management <br/> |
   
次の例は、データベースから Managed Metadata Service を復元する方法を示しています。
  
This uses the existing Managed_Metadata_DB database. This database is log shipped, but there is no active service application on the secondary farm, so it needs to be connected after the service application is in place.
  
最初に、 `New-SPMetadataServiceApplication` を使用して、復元対象のデータベース名を使用して `DatabaseName` スイッチを指定します。
  
次に、以下のようにしてセカンダリ サーバーで新しい Managed Metadata Service アプリケーションを構成します。
  
- 名前: Managed Metadata Service
    
- データベース サーバー: 配布されたトランザクション ログに基づくデータベース名
    
- データベース名:Managed_Metadata_DB
    
- アプリケーション プール: SharePoint サービス アプリケーション 
    
### <a name="manage-dns-records"></a>DNS レコードの管理

ご使用の SharePoint ファームを指す DNS レコードを手動で作成しなければなりません。
  
In most cases where you have multiple front-end web servers, it makes sense to take advantage of the Network Load Balancing feature in Windows Server 2012 or a hardware load balancer to distribute requests among the web-front-end servers in your farm. Network load balancing can also help reduce risk by distributing requests to the other servers if one of your web-front-end servers fails. 
  
Typically, when you set up network load balancing, your cluster is assigned a single IP address. You then create a DNS host record in the DNS provider for your network that points to the cluster. (For this project, we put a DNS server in Azure for resiliency in case of an on-premises datacenter failure.) For instance, you can create a DNS record, in DNS Manager in Active Directory, for example, called  `https://sharepoint.contoso.com`, that points to the IP address for your load-balanced cluster.
  
SharePoint ファームへの外部アクセスの場合は、 `https://sharepoint.contoso.com` ファイアウォールの外部 IP アドレスをポイントするイントラネット上でクライアントが使用するのと同じ URL を使用して、外部 DNS サーバー上にホストレコードを作成できます。 (この例を使用して、 `contoso.com` dns 要求を外部 dns サーバーにルーティングするのではなく、内部 dns サーバーが権限を持ち、要求を直接 SharePoint ファームクラスターにルーティングするように、分割 DNS を設定するのがベストプラクティスです。)その後、外部 IP アドレスをオンプレミスクラスターの内部 IP アドレスにマップして、クライアントが探しているリソースを見つけられるようにすることができます。
  
以下に、考えられるいくつかの異なる障害復旧シナリオを記します。
  
 **Example scenario: The on-premises SharePoint farm is unavailable because of hardware failure in the on-premises SharePoint farm.** In this case, after you have completed the steps for failover to the Azure SharePoint farm, you can configure network load balancing on the recovery SharePoint farm's web-front-end servers, the same way you did with the on-premises farm. You can then redirect the host record in your internal DNS provider to point to the recovery farm's cluster IP address. Note that it can take some time before cached DNS records on clients are refreshed and point to the recovery farm.
  
 **Example scenario: The on-premises datacenter is lost completely.** This scenario might occur due to a natural disaster, such as a fire or flood. In this case, for an enterprise, you would likely have a secondary datacenter hosted in another region as well as your Azure subnet that has its own directory services and DNS. As in the previous disaster scenario, you can redirect your internal and external DNS records to point to the Azure SharePoint farm. Again, take note that DNS-record propagation can take some time.
  
ホスト名付き[サイトコレクションのアーキテクチャと展開 (SharePoint 2013)](https://docs.microsoft.com/SharePoint/administration/host-named-site-collection-architecture-and-deployment)で推奨されているように、ホスト名付きサイトコレクションを使用している場合は、sharepoint ファーム内の同じ web アプリケーションによってホストされている複数のサイトコレクションがあり、一意の DNS 名 (たとえば、など) があり `https://sales.contoso.com` `https://marketing.contoso.com` ます。 その場合、使用しているクラスター IP アドレスを指すサイト コレクションごとに、DNS レコードを作成できます。 SharePoint Web フロントエンド サーバーに要求が到着すると、適切なサイト コレクションにそれぞれの要求がルーティングされます。
  
## <a name="microsoft-proof-of-concept-environment"></a>Microsoft の概念実証環境

We designed and tested a proof-of-concept environment for this solution. The design goal for our test environment was to deploy and recover a SharePoint farm that we might find in a customer environment. We made several assumptions, but we knew that the farm needed to provide all of the out-of-the-box functionality without any customizations. The topology was designed for high availability by using best practice guidance from the field and product group.
  
次の表に、オンプレミス テスト環境用に作成して構成した Hyper-V 仮想マシンについて取り上げます。
  
**表: オンプレミス テストの仮想マシン**

|**サーバー名**|**ロール**|**構成**|
|:-----|:-----|:-----|
|DC1  <br/> |Active Directory を使用したドメイン コントローラー。  <br/> |2 つのプロセッサ  <br/> 512 MB ～ 4 GB の RAM  <br/> 1 x 127 GB のハードディスク  <br/> |
|RRAS  <br/> |ルーティングとリモート アクセス サービス (RRAS) ロールで構成されたサーバー。  <br/> |2 つのプロセッサ  <br/> 2 ～ 8 GB の RAM  <br/> 1 x 127 GB のハードディスク  <br/> |
|FS1  <br/> |バックアップと DFSR 用のエンドポイントのための共有ファイルが含まれるファイル サーバー。  <br/> |4 つのプロセッサ  <br/> 2 から 12 GB の RAM  <br/> 1 x 127 GB のハードディスク  <br/> 1 x 1 TB のハードディスク (SAN)  <br/> 1 x 750 GB のハードディスク  <br/> |
|SP-WFE1、SP-WFE2  <br/> |フロントエンド Web サーバー。  <br/> |4 つのプロセッサ  <br/> 16 GB の RAM  <br/> |
|SP-APP1、SP-APP2、SP-APP3  <br/> |アプリケーション サーバー。  <br/> |4 つのプロセッサ  <br/> 2 ～16 GB の RAM  <br/> |
|SP-SQL-HA1、SP-SQL-HA2  <br/> |Database servers, configured with SQL Server 2012 AlwaysOn availability groups to provide high availability. This configuration uses SP-SQL-HA1 and SP-SQL-HA2 as the primary and secondary replicas.  <br/> |4 つのプロセッサ  <br/> 2 ～16 GB の RAM  <br/> |
   
以下の表に、オンプレミス テスト環境のフロントエンド Web サーバーおよびアプリケーション サーバー用に作成して構成した Hyper-V 仮想マシンのドライブ構成について取り上げます。
  
**表: オンプレミス テストのフロントエンド Web サーバーおよびアプリケーション サーバー用の仮想マシンのドライブ要件**

|**ドライブ文字**|**サイズ**|**ディレクトリ名**|**パス**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |システム ドライブ  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\  <br/> |
|E  <br/> |80  <br/> |ログ ドライブ (40 GB)  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|F  <br/> |80  <br/> |ページ (36 GB)  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL\\DATA  <br/> |
   
The following table describes drive configurations for the Hyper-V virtual machines created and configured to serve as the on-premises database servers. On the **Database Engine Configuration** page, access the **Data Directories** tab to set and confirm the settings shown in the following table.
  
**表: オンプレミス テスト用データベース サーバーの仮想マシンのドライブ要件**

|**ドライブ文字**|**サイズ**|**ディレクトリ名**|**パス**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |データのルート ディレクトリ  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\  <br/> |
|E  <br/> |500  <br/> |ユーザーのデータベース ディレクトリ  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|F  <br/> |500  <br/> |ユーザーのデータベース ログ ディレクトリ  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|G  <br/> |500  <br/> |Temp DB ディレクトリ  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|H  <br/> |500  <br/> |Temp DB ログ ディレクトリ  <br/> |<DriveLetter>:\\Program Files\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
   
### <a name="setting-up-the-test-environment"></a>テスト環境の設定

During the different deployment phases, the test team typically worked on the on-premises architecture first and then on the corresponding Azure environment. This reflects the general real-world cases where in-house production farms are already running. What is even more important is that you should know the current production workload, capacity, and typical performance. In addition to building a disaster recovery model that can meet business requirements, you should size the recovery farm servers to deliver a minimum level of service. In a cold or warm standby environment, a recovery farm is typically smaller than a production farm. After the recovery farm is stable and in production, the farm can be scaled up and out to meet workload requirements.
  
以下の 3 つのフェーズで、テスト環境を展開しました。
  
- ハイブリッド インフラストラクチャの設定
    
- サーバーの準備
    
- SharePoint ファームの展開
    
#### <a name="set-up-the-hybrid-infrastructure"></a>ハイブリッド インフラストラクチャの設定

This phase involved setting up a domain environment for the on-premises farm and for the recovery farm in Azure. In addition to the normal tasks associated with configuring Active Directory, the test team implemented a routing solution and a VPN connection between the two environments.
  
#### <a name="provision-the-servers"></a>サーバーの準備

In addition to the farm servers, it was necessary to provision servers for the domain controllers and configure a server to handle RRAS as well as the site-to-site VPN. Two file servers were provisioned for the DFSR service, and several client computers were provisioned for testers.
  
#### <a name="deploy-the-sharepoint-farms"></a>SharePoint ファームの展開

The SharePoint farms were deployed in two stages in order to simplify environment stabilization and troubleshooting, if required. During the first stage, each farm was deployed on the minimum number of servers for each tier of the topology to support the required functionality.
  
We created the database servers with SQL Server installed before creating the SharePoint 2013 servers. Because this was a new deployment, we created the availability groups before deploying SharePoint. We created three groups based on MCS best practice guidance. 
  
> [!NOTE]
> Create placeholder databases so that you can create availability groups before the SharePoint installation. For more information, see [Configure SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=517626)
  
ファームと、関係する他のサーバーを次の順序で作成しました。
  
- SP-SQL-HA1 と SP-SQL-HA2 を準備します。
    
- AlwaysOn を構成し、ファームの 3 つの可用性グループを作成します。 
    
- サーバーの全体管理をホストするための SP-APP1 を準備します。
    
- 分散キャッシュをホストするための SP-WFE1 と SP-WFE2 を準備します。 
    
コマンド ラインで _psconfig.exe_ を実行する際、 **skipRegisterAsDistributedCachehost** パラメーターを使用しました。 詳細については、「[SharePoint Server 2013 でフィードおよび Distributed Cache service を計画する](https://docs.microsoft.com/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service)」を参照してください。 
  
復旧環境で次のステップを繰り返しました。
  
- AZ-SQL-HA1 と AZ-SQL-HA2 を準備します。
    
- AlwaysOn を構成し、ファームの 3 つの可用性グループを作成します。
    
- サーバーの全体管理をホストするための AZ-APP1 を準備します。
    
- 分散キャッシュをホストするための AZ-WFE1 と AZ-WFE2 を準備します。
    
After we configured the distributed cache and added test users and test content, we started stage two of the deployment. This required scaling out the tiers and configuring the farm servers to support the high-availability topology described in the farm architecture.
  
次の表に、復旧ファームで設定した仮想マシン、サブネット、可用性セットを取り上げます。
  
**表: 復旧ファーム インフラストラクチャ**

|**サーバー名**|**ロール**|**構成**|**サブネット**|**可用性セット**|
|:-----|:-----|:-----|:-----|:-----|
|spDRAD  <br/> |Active Directory を使用したドメイン コントローラー  <br/> |2 つのプロセッサ  <br/> 512 MB ～ 4 GB の RAM  <br/> 1 x 127 GB のハードディスク  <br/> |sp-ADservers  <br/> ||
|AZ-SP-FS  <br/> |>バックアップと DFSR 用のエンドポイントのための共有ファイルが含まれるファイル サーバー  <br/> | A5 構成: <br/>  2 つのプロセッサ <br/>  14 GB の RAM <br/>  1 x 127 GB のハードディスク <br/>  1 x 135 GB のハードディスク <br/>  1 x 127 GB のハードディスク <br/>  1 x 150 GB のハードディスク <br/> |sp-databaseservers  <br/> |DATA_SET  <br/> |
|AZ-WFE1、AZ -WFE2  <br/> |フロントエンド Web サーバー  <br/> | A5 構成: <br/>  2 つのプロセッサ <br/>  14 GB の RAM <br/>  1 x 127 GB のハードディスク <br/> |sp-webservers  <br/> |WFE_SET  <br/> |
|AZ -APP1、AZ -APP2、AZ -APP3  <br/> |アプリケーション サーバー  <br/> | A5 構成: <br/>  2 つのプロセッサ <br/>  14 GB の RAM <br/>  1 x 127 GB のハードディスク <br/> |sp-applicationservers  <br/> |APP_SET  <br/> |
|AZ -SQL-HA1、AZ -SQL-HA2  <br/> |データベース サーバー、および AlwaysOn 可用性グループのプライマリおよびセカンダリのレプリカ  <br/> | A5 構成: <br/>  2 つのプロセッサ <br/>  14 GB の RAM <br/> |sp-databaseservers  <br/> |DATA_SET  <br/> |
   
### <a name="operations"></a>運用

テスト チームがファーム環境を安定化させ、機能テストを完了した後、オンプレミス復旧環境を構成するために必要な以下の運用タスクを開始しました。
  
- 完全バックアップと差分バックアップの構成。
    
- オンプレミス環境と Azure 環境間でトランザクション ログを転送する、ファイル サーバー上における DFSR の構成。
    
- プライマリ データベース サーバーにおけるログ配布の構成。
    
- Stabilize, validate, and troubleshoot log shipping, as required. This included identifying and documenting any behavior that might cause issues, such as network latency, which would cause log shipping or DFSR file synchronization failures.
    
### <a name="databases"></a>データベース

実行したフェールオーバー テストには、以下のデータベースが関係しました。 
  
- WSS_Content
    
- ManagedMetadata
    
- プロファイル データベース
    
- 同期データベース
    
- ソーシャル データベース
    
- コンテンツ タイプ ハブ (専用のコンテンツ タイプ シンジケート ハブ用データベース)
    
## <a name="troubleshooting-tips"></a>トラブルシューティングのヒント

このセクションでは、テスト中に生じた問題とその解決方法について説明します。 
  
### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>用語ストアの管理ツールを使用すると、「Managed Metadata Store または接続を現在利用できません」というエラーが生じる

Web アプリケーションで使用されるアプリケーション プール アカウントに、用語ストアのアクセス許可への読み取りアクセスが設定されていることを確認します。
  
### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>サイト コレクションでカスタム用語セットが使用できない

Check for a missing service application association between your content site collection and your content type hub. In addition, under the **Managed Metadata - <site collection name> Connection** properties screen, make sure this option is enabled: **This service application is the default storage location for column specific term sets.**
  
### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>Get-ADForest Windows PowerShell コマンドによって、「用語 'Get-ADForest' は、コマンドレット、関数、スクリプト ファイル、操作可能なプログラムのいずれの名前としても認識されません。」というエラーが生成される

When setting up user profiles, you need the Active Directory forest name. In the Add Roles and Features Wizard, ensure that you have enabled the Active Directory Module for Windows PowerShell (under the **Remote Server Administration Tools>Role Administration Tools>AD DS and AD LDS Tools** section). In addition, run the following commands before using **Get-ADForest** to help ensure that your software dependencies are loaded.
  
```
Import-module servermanager
Import-module activedirectory

```

### <a name="availability-group-creation-fails-at-starting-the-alwayson_health-xevent-session-on-server-name"></a>'<サーバー名>'の 'AlwaysOn_health' XEvent セッションを開始すると可用性グループの作成が失敗する

フェールオーバー クラスターの両方のノードの状態が「実行中」で、「一時停止」または「停止」になっていないことを確認してください。 
  
### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>SQL Server ログ配布ジョブがファイル共有に接続しようとすると、「アクセスが拒否されました」というエラーで失敗する

SQL Server エージェントが、既定の資格情報ではなく、ネットワーク資格情報で実行されていることを確認してください。
  
### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>SQL Server ログ配布ジョブは成功したことを示すが、ファイルがコピーされない

This happens because the default backup preference for an availability group is **Prefer Secondary**. Ensure that you run the log shipping job from the secondary server for the availability group instead of the primary; otherwise, the job will fail silently. 
  
### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>Managed Metadata Service (または他の SharePoint サービス) がインストール後に自動的に開始されない

サービスは、SharePoint Server のパフォーマンスとその時点における負荷によっては開始するまでに数分かかる場合があります。 **[開始]** をクリックしてサービスを手動で開始し、[サーバーのサービス] 画面をときどき更新して状態を監視しながら、サービスが開始されるまで適切な時間を取ります。 サービスが依然として停止状態の場合には、SharePoint 診断ログを有効にしてからサービスの開始をもう一度試みて、ログでエラーを確認します。 詳細については、「 [Configure diagnostic logging In SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-diagnostic-logging) 」を参照してください。
  
### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>DNS を Azure フェールオーバー環境に変更した後も、SharePoint サイトに関して従来の IP アドレスをクライアント ブラウザーが使用し続ける

Your DNS change might not be visible to all clients immediately. On a test client, perform the following command from an elevated command prompt and attempt to access the site again.
  
```
Ipconfig /flushdns
```

## <a name="additional-resources"></a>その他の技術情報

[サポートされている SharePoint データベース用の高可用性のオプションと障害復旧のオプション](https://docs.microsoft.com/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)
  
[SQL Server 2012 の AlwaysOn 可用性グループを SharePoint 2013 用に構成する](https://go.microsoft.com/fwlink/p/?LinkId=393122)
  
## <a name="see-also"></a>関連項目

[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.yml)



