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
ms.openlocfilehash: 3b0eb977754b86d626153d38d0d79e718dedfcdc
ms.sourcegitcommit: a578baeb0d8b85941c13afa268447d2592f89fae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2020
ms.locfileid: "43793700"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル

 **概要:** アーキテクチャ モデル、展開、および SharePoint、Exchange、Skype for Business、および Lync のプラットフォーム オプションについて説明している IT ポスターを取得します。
  
これらの IT ポスターは、SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデルと展開オプションについて説明し、Microsoft Azure で SharePoint を展開するための設計情報を提供します。
  
Office 365 では、ユーザーが慣れ親しんでいるコラボレーション サービスや通信サービスを、クラウドベースのサービスとして提供できます。いくつかの例外はありますが、オンプレミスの展開の場合も、Office 365 でも、ユーザー エクスペリエンスは同じです。この統合されたユーザー エクスペリエンスにより、それぞれの作業負荷の配置決定はより複雑になり、次のような疑問が生じます。
  
- 個々のワークロードに対して選択するプラットフォーム オプションをどのように決定するか。
    
- オンプレミスのサービスを残すことに意味はあるか。
    
- どのようなシナリオではハイブリッド展開が適切か。
    
- Microsoft Azure は図にどのように適合するか。
    
- Azure の Office Server ワークロードでサポートされている構成はどのようなものか。
    
> [!TIP]
> このページのポスターのほとんどは、中国語、英語、フランス語、ドイツ語、イタリア語、日本語、韓国語、ポルトガル語、ロシア語、スペイン語を含む複数の言語で提供されています。これらの言語のいずれかのポスターをダウンロードするには、ポスターの **[その他の言語]** リンクをクリックします。
  
ご意見を電子メールで [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com) 宛てにお送りください。 
  
このページには次のポスターへのリンクがあります。
  
- **アーキテクチャ モデルのポスター** これらのリソースを使用して、SharePoint 2016 および Skype for Business 2015 用の理想的なプラットフォームと構成を決定することができます。
    
  - [Microsoft SharePoint 2016 アーキテクチャ モデル](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [OneDrive の複数地域機能および Office 365 の SharePoint Online](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#MultiGeoO365ODB)
    
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

これらの SharePoint 2016 および Skype for Business 2015 向けの新しい IT ポスターは、印刷しやすい形式で、さまざまな展開の方法を比較する手段を提供します。各ポスターは利用可能な構成またはプラットフォーム オプションすべての一覧を示し、オプションごとに次の情報を説明します。
  
- **概要** 概念図などの、プラットフォームの簡単な要約です。
    
- **最適シナリオ** 特定のプラットフォームが最適な、一般的なシナリオです。
    
- **ライセンス要件** 展開に必要なライセンスです。
    
- **アーキテクチャ タスク** 事業計画担当が下す必要がある決定です。
    
- **IT 技術者のタスクまたは業務** IT スタッフが計画する必要がある毎日の業務です。
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-2016-architectural-models"></a>Microsoft SharePoint 2016 のアーキテクチャ モデル

|**アイテム**|**説明**|
|:-----|:-----|
|[![SharePoint 2016 アーキテクチャ モデル ポスターのサムネイル](media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)  \| [Visio](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=52650) <br/> | この IT ポスターでは、ビジネスの意思決定者とソリューション設計担当者が知っておく必要のある SharePoint Online、Microsoft Azure、SharePoint のオンプレミス構成について説明しています。 <br/><br/> - **SharePoint Online (SaaS)** - サービスとしてのソフトウェア (SaaS) サブスクリプション モデルを介して SharePoint を使用します。 <br/> - **SharePoint ハイブリッド** - 自分のペースで SharePoint サイトとアプリをクラウドに移動します。 <br/> - **Azure での SharePoint (IaaS)** - オンプレミス環境を Microsoft Azure に拡張して、そこに SharePoint 2016 Server を展開します (これは高可用性/障害復旧環境や開発/テスト環境の場合に推奨されます)。<br/> - **オンプレミスの SharePoint** - 保守しているデータセンター内で SharePoint 環境の計画、展開、保守、カスタマイズを行います。 <br/> |
   
<a name="MultiGeoO365ODB"> </a>
### <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a>OneDrive の複数地域機能および Office 365 の SharePoint Online

|**アイテム**|**説明**|
|:-----|:-----|
|[![Office 365 の OneDrive の複数地域機能に関するモデル](media/c6c1b7cd-7833-46fb-9eec-c12150c260d9.png)          ](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/Multi-Geo-ODB.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/Multi-Geo-ODB.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/Multi-Geo-ODB.vsdx) <br/> | このポスターは、Office 365 の OneDrive および SharePoint Online での Multi-Geo Capabilities の 1 ページの概要です。このモデルには以下が含まれます。<br/><br/> - メリット <br/> - 展開の手順 <br/> - 構成の例 <br/><br/>  Office 365 の OneDrive および SharePoint Online での Multi-Geo Capabilities について詳しくは、[こちら](https://aka.ms/onedrivemultigeo)をクリックしてください。  <br/> |
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>SharePoint Server 2016 Database

|**アイテム**|**説明**|
|:-----|:-----|
|[![SharePoint Server 2016 Database のポスターのサムネイル](media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)          ](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)  \| [Visio](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=55041) <br/> | この IT ポスターは、SharePoint Server 2016 データベースのクイック リファレンス ガイドです。各データベースには、以下の詳細情報があります。 <br/><br/> - サイズ <br/> - 拡大縮小のガイド <br/> - I/O パターン <br/> - 要件 <br/><br/>  最初のページには、SharePoint システム データベースと、データベースが複数存在するサービス アプリケーションが含まれています。2 番目のページには、1 つのデータベースを持つサービス アプリケーションのすべてが表示されます。<br/><br/>  SharePoint Server 2016 データベースの詳細については、「[データベースの種類と説明 (SharePoint Server 2016)](https://docs.microsoft.com/SharePoint/technical-reference/database-types-and-descriptions)」を参照してください。 <br/> |
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Microsoft Skype for Business 2015 のアーキテクチャ モデル

|**アイテム**|**説明**|
|:-----|:-----|
|[![Skype for Business アーキテクチャ モデル ポスターのサムネイル](media/132288c0-6ae4-4394-88ab-b57dae367714.png)          ](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)  \| [Visio](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=55022) <br/> |このポスターでは、ビジネスの意思決定者とソリューション設計担当者が知っておく必要のある Skype for Business Online、オンプレミス、ハイブリッド、クラウド PBX、ならびに Exchange および SharePoint との統合の構成について説明しています。 <br/><br/> これは、Skype for Business Online およびオンプレミスの Skype for Business を利用するための異なる基本的なアーキテクチャ モデルに対する IT 担当者の意識を高めることを目的としています。 <br/><br/>組織のニーズおよび将来の計画に最も適した構成から開始します。必要に応じて、他の構成を考慮して使用します。たとえば、Exchange および SharePoint との統合、または Microsoft のクラウド PBX を活用したソリューションを検討する必要がある場合があります。  <br/> |
   
## <a name="platform-options-posters"></a>プラットフォーム オプションのポスター

SharePoint 2013、Exchange 2013 および Lync 2013 向けのこれらの IT ポスターは、大きなポスターの形式で、一目でさまざまな展開の方法を比較する手段を提供します。各ポスターは利用可能な構成またはプラットフォーム オプションすべての一覧を示し、オプションごとに次の情報を説明します。
  
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
|[![SharePoint 2013 プラットフォーム オプションのサムネイル イメージ](media/SP-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=324593)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=40332) <br/> |ビジネス意思決定者 (BDM) およびアーキテクト向けです。このモデルでは SharePoint 2013 (Office 365 の SharePoint、Office 365 を搭載したオンプレミス ハイブリッド、Azure、およびオンプレミスのデプロイのみ) のプラットフォーム オプションを示します。これには、各アーキテクチャの概要、推奨事項、ライセンス要件、およびプラットフォームごとのアーキテクトと IT 担当者のタスクのリストが含まれています。Azure の SharePoint ソリューションのいくつかは強調表示されています。<br/><br/>このポスターのアクセス可能テキスト版については、「[アクセス可能な図 - Microsoft SharePoint 2013 プラットフォーム オプション](accessible-diagrammicrosoft-sharepoint-2013-platform-options.md)」をご覧ください。  <br/> |
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>Exchange 2013 プラットフォーム オプション

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![Exchange プラットフォーム オプションのサムネイル イメージ](media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=398742)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=42676) <br/> |このモデルは、管理職意思決定者と事業計画担当のために、Exchange 2013 の使用可能なプラットフォーム オプションを示しています。お客様は Office 365 による Exchange Online、Hybrid Exchange、オンプレミス Exchange Server、Hosted Exchange から選択できます。ポスターにはそれぞれのオプションに最適なシナリオ、ライセンス要件、および IT 技術者の業務などを含む、各アーキテクチャのオプションの詳細が含まれています。<br/><br/>このポスターのアクセス可能テキスト版については、「[アクセス可能な図 - Microsoft Exchange 2013 プラットフォーム オプション](accessible-diagrammicrosoft-exchange-2013-platform-options.md)」をご覧ください。  <br/> |
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>Lync 2013 プラットフォーム オプション

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![Lync プラットフォーム オプションのサムネイル イメージ](media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkID=391839)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=41677) <br/> |このモデルは、管理職意思決定者と事業計画担当のために、Lync 2013 の使用可能なプラットフォーム オプションを示しています。お客様は Office 365 による Lync Online、Hybrid Lync、オンプレミス Lync Server、Hosted Lync から選択できます。IT ポスターにはそれぞれのオプションに最適なシナリオ、ライセンス要件、および IT 技術者の業務などを含む、各アーキテクチャのオプションの詳細が含まれています。  <br/> |
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>Azure の SharePoint のソリューションのポスター

これらの IT ポスターは、大きなポスターの形式で、SharePoint Server 2013 を使用する Azure ベースのソリューションを示します。
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![SharePoint を使用した Azure のインターネット サイトのイメージ](media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=41992) <br/> |このポスターは、インターネットに接続された Azure のサイトの主要な設計活動と、推奨されるアーキテクチャの選択肢の概要を説明しています。このポスターのアクセス可能テキスト版については、「[アクセス可能な図 - SharePoint 2013 のための Microsoft Azure のインターネット サイト](accessible-diagraminternet-sites-in-microsoft-azure-for-sharepoint-2013.md)」をご覧ください。<br/><br/> 詳細については、以下の記事を参照してください。  <br/><br/> - [SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
<a name="DesignSampleInternetSites"> </a>
### <a name="design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>設計サンプル: SharePoint 2013 のための Microsoft Azure のインターネット サイト

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![設計サンプルのイメージ: Microsoft Azure for SharePoint 2013 のインターネット サイト](media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=41991) <br/> |この設計サンプルを、Azure を使用する、インターネットに接続された SharePoint Server 2013 のサイトの独自アーキテクチャの開始点として使用してください。このポスターのアクセス可能テキスト版については、「[アクセス可能な図 - 設計サンプル: SharePoint 2013 のための Microsoft Azure のインターネット サイト](accessible-diagramdesign-sample-internet-sites-in-microsoft-azure-for-sharepoint.md)」をご覧ください。<br/><br/> 詳細については、以下の記事を参照してください。  <br/><br/> - [SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>Microsoft Azure に対する SharePoint の障害復旧

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![Azure への SharePoint 障害回復プロセス](media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)  \| [その他の言語](https://www.microsoft.com/download/details.aspx?id=41993) <br/> |この IT ポスターは、Azure での障害復旧環境のアーキテクチャ原則を示しています。このポスターのアクセス可能テキスト版については、「[アクセス可能な図 - Microsoft Azure に対する SharePoint の障害復旧](accessible-diagramsharepoint-disaster-recovery-to-microsoft-azure.md)」をご覧ください。<br/><br/> 詳細については、以下の記事を参照してください。  <br/><br/> - [Microsoft Azure での SharePoint Server 2013 の障害復旧](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
<a name="Lync2013_Options"> </a>
## <a name="see-also"></a>関連項目

[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.yml)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)
  
[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[ハイブリッド ソリューション](hybrid-solutions.md)

