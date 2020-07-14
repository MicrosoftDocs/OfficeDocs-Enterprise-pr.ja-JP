---
title: SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/16/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: 5b49fa68-f8f2-4705-af96-5f5475e8539a
search.appverid:
- MET150
description: '概要: アーキテクチャ モデル、展開、および SharePoint、Exchange、Skype for Business、および Lync のプラットフォーム オプションについて説明している IT ポスターを取得します。'
ms.openlocfilehash: 9e6e4f2b32bb2e5b39f8891d8acddc0699cdbf8d
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102565"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル

これらの IT ポスターは、SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデルと展開オプションについて説明し、Microsoft Azure で SharePoint を展開するための設計情報を提供します。
  
Microsoft 365 では、クラウドベースのサービスとしてユーザーが使い慣れた共同作業とコミュニケーションのサービスを提供できます。 いくつかの例外があります。オンプレミスの展開を行っている場合でも、Microsoft 365 を使用している場合でも、ユーザー エクスペリエンスは変わりません。 この統合されたユーザー エクスペリエンスにより、それぞれの作業負荷の配置決定はより複雑になり、次のような疑問が生じます:
  
- 個々のワークロードに対して選択するプラットフォーム オプションをどのように決定するか。
    
- オンプレミスのサービスを残すことに意味はあるか。
    
- どのようなシナリオではハイブリッド展開が適切か。
    
- Microsoft Azure は図にどのように適合するか。
    
- Azure の Office Server ワークロードでサポートされている構成はどのようなものか。
    
> [!TIP]
> Most of the posters on this page are available in multiple languages, including Chinese, English, French, German, Italian, Japanese, Korean, Portuguese, Russian, and Spanish. To download a poster in one of these languages, click the **More languages** link for that poster.
  
Let us know what you think! Send us email at [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 
  
このページには次のポスターへのリンクがあります。
  
- **アーキテクチャ モデルのポスター** これらのリソースを使用して、SharePoint 2016 および Skype for Business 2015 用の理想的なプラットフォームと構成を決定することができます。
    
  - [Microsoft SharePoint 2016 アーキテクチャ モデル](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [SharePoint Server 2016 データベース](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Microsoft Skype for Business 2015 アーキテクチャ モデル](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **プラットフォーム オプションのポスター** これらのリソースを使用して、SharePoint 2013、Exchange 2013、Lync 2013 用の理想的なプラットフォームと構成を決定することができます。
    
  - [SharePoint 2013 プラットフォーム オプション](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Exchange 2013 プラットフォーム オプション](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Lync 2013 プラットフォーム オプション](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **Azure の SharePoint Server 2013 のソリューションのポスター** これらの IT ポスターを使用して、Azure インフラストラクチャ サービスの SharePoint Server 2013 ワークロード用の設計および構成を決定することができます。
    
  - [SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [設計サンプル: SharePoint 2013 のための Microsoft Azure のインターネット サイト](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [Microsoft Azure に対する SharePoint の障害復旧](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>アーキテクチャ モデルのポスター

These new IT posters for SharePoint 2016 and Skype for Business 2015 provide a way to compare the various deployment methods in an easy-to-print format. Each poster provides a list of all the configurations or platform options available and gives you the following information for each option:
  
- **概要** 概念図などの、プラットフォームの簡単な要約です。
    
- **最適シナリオ** 特定のプラットフォームが最適な、一般的なシナリオです。
    
- **ライセンス要件** 展開に必要なライセンスです。
    
- **アーキテクチャ タスク** 事業計画担当が下す必要がある決定です。
    
- **IT 技術者のタスクまたは業務** IT スタッフが計画する必要がある毎日の業務です。
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-2016-architectural-models"></a>Microsoft SharePoint 2016 のアーキテクチャ モデル

|**アイテム**|**説明**|
|:-----|:-----|
|[![SharePoint 2016 アーキテクチャ モデル ポスターのサムネイル](media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)  \| [Visio](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=52650) <br/> | この IT ポスターでは、ビジネスの意思決定者とソリューション設計担当者が知っておく必要のある SharePoint Online、Microsoft Azure、SharePoint のオンプレミス構成について説明しています。 <br/><br/> - **SharePoint Online (SaaS)** - サービスとしてのソフトウェア (SaaS) サブスクリプション モデルを介して SharePoint を使用します。 <br/> - **SharePoint ハイブリッド** - 自分のペースで SharePoint サイトとアプリをクラウドに移動します。 <br/> - **SharePoint in Azure (IaaS)** - You extend your on-premises environment into Microsoft Azure and deploy SharePoint 2016 Servers there. (This is recommended for High Availability/Disaster Recovery and dev/test environments.) <br/> - **オンプレミスの SharePoint** - 保守しているデータセンター内で SharePoint 環境の計画、展開、保守、カスタマイズを行います。 <br/> |
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>SharePoint Server 2016 Database

|**アイテム**|**説明**|
|:-----|:-----|
|[![SharePoint Server 2016 Database のポスターのサムネイル](media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)          ](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)  \| [Visio](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=55041) <br/> | This IT poster is a quick reference guide for SharePoint Server 2016 databases. Each database has the following details: <br/><br/> - サイズ <br/> - 拡大縮小のガイド <br/> - I/O パターン <br/> - 要件 <br/><br/>  The first page has the SharePoint system databases and the service applications that have multiple databases. The second page shows all of the service applications that have single databases. <br/><br/>  SharePoint Server 2016 データベースの詳細については、「[データベースの種類と説明 (SharePoint Server 2016)](https://docs.microsoft.com/SharePoint/technical-reference/database-types-and-descriptions)」を参照してください。 <br/> |
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Microsoft Skype for Business 2015 のアーキテクチャ モデル

|**アイテム**|**説明**|
|:-----|:-----|
|[![Skype for Business アーキテクチャ モデル ポスターのサムネイル](media/132288c0-6ae4-4394-88ab-b57dae367714.png)          ](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)  \| [Visio](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=55022) <br/> |このポスターでは、ビジネスの意思決定者とソリューション設計担当者が知っておく必要のある Skype for Business Online、オンプレミス、ハイブリッド、クラウド PBX、ならびに Exchange および SharePoint との統合の構成について説明しています。 <br/><br/> これは、Skype for Business Online およびオンプレミスの Skype for Business を利用するための異なる基本的なアーキテクチャ モデルに対する IT 担当者の意識を高めることを目的としています。 <br/><br/>Start with whichever configuration best suits your organization's needs and future plans. Consider and use others as needed. For example, you might want to consider integration with Exchange and SharePoint or a solution that takes advantage of Microsoft's Cloud PBX offering.  <br/> |
   
## <a name="platform-options-posters"></a>プラットフォーム オプションのポスター

These IT posters for SharePoint 2013, Exchange 2013, and Lync 2013 provide a way to compare the various deployment methods at a single glance in a large poster format. Each poster provides a list of all the configurations or platform options available and gives you the following information for each option:
  
- **概要** 概念図などの、プラットフォームの簡単な要約です。
    
- **最適シナリオ** 特定のプラットフォームが最適な、一般的なシナリオです。
    
- **ライセンス要件** 展開に必要なライセンスです。
    
- **アーキテクチャ タスク** 事業計画担当が下す必要がある決定です。
    
- **IT 技術者のタスクまたは業務** IT スタッフが計画する必要がある毎日の業務です。
    
<a name="SP2013_Options"> </a>
## <a name="sharepoint-2013-platform-options"></a>SharePoint 2013 プラットフォーム オプション

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![SharePoint 2013 プラットフォーム オプションのサムネイル イメージ](media/SP-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=324593)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=40332) <br/> |このモデルは、ビジネス上の意思決定者 (BDM) やアーキテクトを対象にして、SharePoint 2013、Microsoft 365 の SharePoint、Microsoft 365 とのオンプレミス ハイブリッド、Azure、およびオンプレミスのみの展開に使用する、プラットフォーム オプションを示します。 これには、各アーキテクチャの概要、推奨事項、ライセンス要件、各プラットフォームのアーキテクトおよび IT 担当者向けタスクのリストが含まれています。 Azure 上のいくつかの SharePoint ソリューションが強調表示されています。 <br/> |
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>Exchange 2013 プラットフォーム オプション

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![Exchange プラットフォーム オプションのサムネイル イメージ](media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=398742)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=42676) <br/> |このモデルでは、BDM やアーキテクトを対象にして、Exchange 2013 で利用可能なプラットフォームのオプションについて説明します。 お客様は Microsoft 365 による Exchange Online、Hybrid Exchange、オンプレミス Exchange Server、Hosted Exchange から選択できます。 ポスターには、それぞれに最も理想的なシナリオ、ライセンスの要件、IT プロフェッショナルの責任など、アーキテクチャーに関するオプションの詳細が含まれています。 <br/> |
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>Lync 2013 プラットフォーム オプション

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![Lync プラットフォーム オプションのサムネイル イメージ](media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=391839)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=41677) <br/> |このモデルでは、BDM やアーキテクトを対象にして、Lync 2013 で利用可能なプラットフォームのオプションについて説明します。 お客様は Microsoft 365 による Lync Online、Hybrid Lync、オンプレミス Lync Server、Hosted Lync から選択できます。 IT ポスターには、それぞれに最も理想的なシナリオ、ライセンスの要件、IT プロフェッショナルの責任など、アーキテクチャーに関するオプションの詳細が含まれています。  <br/> |
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>Azure の SharePoint のソリューションのポスター

これらの IT ポスターは、大きなポスターの形式で、SharePoint Server 2013 を使用する Azure ベースのソリューションを示します。
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![SharePoint を使用した Azure のインターネット サイトのイメージ](media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=41992) <br/> |このポスターは、Azure のインターネット接続サイト用の主な設計活動および推奨アーキテクチャ選択の概要を示しています。  <br/><br/> 詳細については、次の記事を参照してください。  <br/><br/> - [SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
<a name="DesignSampleInternetSites"> </a>
### <a name="design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>設計サンプル: SharePoint 2013 のための Microsoft Azure のインターネット サイト

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![設計サンプルのイメージ: Microsoft Azure for SharePoint 2013 のインターネット サイト](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=41991) <br/> |SharePoint Server 2013 を使用した Azure のインターネット接続サイトの独自アーキテクチャ用の開始点としてこの設計サンプルを使用してください。 <br/><br/> 詳細については、次の記事を参照してください。  <br/><br/> - [SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>Microsoft Azure に対する SharePoint の障害復旧

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![Azure への SharePoint 障害回復プロセス](media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=41993) <br/> |この IT ポスターは、Azure の障害復旧環境のためのアーキテクチャ原則を示しています。 <br/><br/> 詳細については、次の記事を参照してください。  <br/><br/> - [Microsoft Azure での SharePoint Server 2013 の障害復旧](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
## <a name="see-also"></a>関連項目

[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.yml)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)
  
[Microsoft 365 Enterprise のテスト ラボ ガイド](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)
  
[ハイブリッド ソリューション](hybrid-solutions.md)

