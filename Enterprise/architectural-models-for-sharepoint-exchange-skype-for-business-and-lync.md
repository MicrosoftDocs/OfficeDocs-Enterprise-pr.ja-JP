---
title: "SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: 5b49fa68-f8f2-4705-af96-5f5475e8539a
description: "概要: モデルのアーキテクチャ、展開、および SharePoint、Exchange、Skype のビジネス、および Lync のプラットフォーム ・ オプションを説明する IT のポスターを取得します。"
ms.openlocfilehash: 9dd8ba6e7a9455f3b567fa88077748116292e1fc
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル

 **の概要:**モデルのアーキテクチャ、展開、および SharePoint、Exchange、Skype のビジネス、および Lync のプラットフォーム ・ オプションを説明する IT のポスターを取得します。
  
これらの IT ポスターは、SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデルと展開オプションについて説明し、Microsoft Azure で SharePoint を展開するための設計情報を提供します。
  
Office 365 では、コラボレーションと通信サービスが、ユーザーがクラウド ベースのサービスとしてよく使わを提供できます。いくつかの例外では、ユーザーの操作性は同じです、設置型の配置を維持するか、Office 365 を使用するかどうか。この統一されたユーザー エクスペリエンスでは、各作業負荷を配置する場所を決定するのには単純し、疑問を次のように。
  
- 個々のワークロードに対して選択するプラットフォーム オプションをどのように決定するか。
    
- オンプレミスのサービスを残すことに意味はあるか。
    
- どのようなシナリオではハイブリッド展開が適切か。
    
- Microsoft Azure は、画像にどのように合わせてでしょうか。
    
- Azure の Office Server ワークロードでサポートされている構成はどのようなものか。
    
> [!TIP]
> このページのポスターのほとんどは、中国語、英語、フランス語、ドイツ語、イタリア語、日本語、韓国語、ポルトガル語、ロシア語、スペイン語を含む複数の言語で提供されています。これらの言語のいずれかのポスターをダウンロードするには、ポスターの **[その他の言語]** リンクをクリックします。
  
ご意見をお知らせください。[cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com) に電子メールを送信してください。 
  
このページには次のポスターへのリンクがあります。
  
- **設計モデルのポスター**これらのリソースを使用するには、理想的なプラットフォームと SharePoint 2016 とビジネス 2015年の Skype の構成を決定します。
    
  - [Microsoft SharePoint 2016 のアーキテクチャ モデル](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [Office 365 の OneDrive の複数の地域のプレビュー](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#MultiGeoO365ODB)
    
  - [SharePoint Server 2016 データベース](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [マイクロソフトの Skype ビジネス 2015年のアーキテクチャ モデル](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **プラットフォームのオプションのポスター**これらのリソースを使用するには、理想的なプラットフォームと SharePoint 2013、Exchange 2013 では、Lync 2013 の構成を決定します。
    
  - [SharePoint 2013 のプラットフォーム ・ オプション](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Exchange 2013 のプラットフォーム ・ オプション](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Lync 2013 のプラットフォーム ・ オプション](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **Azure ソリューション ポスターで、SharePoint Server 2013**デザインと Azure インフラストラクチャ サービスに、SharePoint Server 2013 の作業負荷の構成を確認するのには、これら IT のポスターを使用できます。
    
  - [SharePoint Server 2013 を使用して Microsoft Azure 内のインターネット サイト](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [設計サンプル: SharePoint 2013 の Microsoft Azure 内のインターネット サイト](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [Microsoft Azure への SharePoint 災害復旧](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>アーキテクチャ モデルのポスター

これらの SharePoint 2016 および Skype for Business 2015 向けの新しい IT ポスターは、印刷しやすい形式で、さまざまな展開の方法を比較する手段を提供します。各ポスターは利用可能な構成またはプラットフォーム オプションすべての一覧を示し、オプションごとに次の情報を説明します。
  
- **概要**概念図を含む、プラットフォームの概要です。
    
- **最適**適している特定のプラットフォームの一般的なシナリオです。
    
- **ライセンスの要件**展開に必要なライセンスです。
    
- **アーキテクチャ タスク**アーキテクトとして作成する必要があります決定します。
    
- **IT プロフェッショナルのタスクや責任の範囲**計画を立てる必要があるお客様の IT スタッフが日常業務です。
    
### <a name="microsoft-sharepoint-2016-architectural-models"></a>Microsoft SharePoint 2016 のアーキテクチャ モデル
<a name="SP2016_ArchModel"> </a>

|**アイテム**|**説明**|
|:-----|:-----|
|[![SharePoint 2016 設計モデルのポスターの縮小版](images/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> ![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)  \| ![Visio ファイルが](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)  \| ![他の言語のバージョンのページを参照してください](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[その他の言語](https://www.microsoft.com/download/details.aspx?id=52650) <br/> | この IT ポスターでは、ビジネスの意思決定者とソリューション設計担当者が知っておく必要のある SharePoint Online、Microsoft Azure、SharePoint のオンプレミス構成について説明しています。 <br/><br/> - **SharePoint Online (SaaS)**のサービス (SaaS) のサブスクリプション モデルとソフトウェアを SharePoint を消費します。 <br/> - **SharePoint のハイブリッド**に、SharePoint サイトおよびアプリケーションを自分のペースでクラウドに移行します。 <br/> - **Azure (IaaS) で SharePoint**の Microsoft Azure に設置環境を拡張し、ある 2016年の SharePoint のサーバーを展開します。(これは推奨高可用性/災害復旧/開発/テスト環境で)<br/> - **SharePoint 設置**の計画、展開、管理および保存されているデータ ・ センターの SharePoint 環境をカスタマイズします。 <br/> |
   
### <a name="multi-geo-preview-for-onedrive-in-office-365"></a>Office 365 の OneDrive の複数の地域のプレビュー
<a name="MultiGeoO365ODB"> </a>

|**アイテム**|**説明**|
|:-----|:-----|
|[![Office 365 のモデルでは複数地域の OneDrive](images/c6c1b7cd-7833-46fb-9eec-c12150c260d9.png)          ](http://download.microsoft.com/download/0/5/9/0594634F-7893-4201-938A-C2FF2F21B655/Multi-Geo-ODB.pdf) <br/> ![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](http://download.microsoft.com/download/0/5/9/0594634F-7893-4201-938A-C2FF2F21B655/Multi-Geo-ODB.pdf)  \| ![Visio ファイル](images/ITPro_Other_VisioIcon.jpg)[Visio](http://download.microsoft.com/download/0/5/9/0594634F-7893-4201-938A-C2FF2F21B655/Multi-Geo-ODB.vsdx) <br/> | このモデルは、Office 365 は、プライベートのプレビューでは、現在の複数の地域の OneDrive の 1 ページの概要です。このモデルが含まれています。<br/><br/> メリット <br/> 導入のステップ <br/> -構成の例 <br/><br/>  Office 365 の OneDrive の複数地域のプレビューの詳細についてをクリックして[ここ](https://aka.ms/onedrivemultigeo)。  <br/> |
   
### <a name="sharepoint-server-2016-databases"></a>SharePoint Server 2016 Database
<a name="SP2016_Databases"> </a>

|**アイテム**|**説明**|
|:-----|:-----|
|[![SharePoint Server 2016 データベース ポスターの縮小版](images/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)          ](https://www.microsoft.com/download/details.aspx?id=55041) <br/> ![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)  \| ![Visio ファイルが](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)  \| ![他の言語のバージョンのページを参照してください](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[その他の言語](https://www.microsoft.com/download/details.aspx?id=55041) <br/> | この IT ポスターは、SharePoint Server 2016 データベースのクイック リファレンス ガイドです。各データベースには、以下の詳細情報があります。<br/><br/> サイズ <br/> -ガイダンスをスケーリングします。 <br/> -I/O パターン <br/> 要件 <br/><br/>  最初のページには、SharePoint のシステム データベースとデータベースが複数存在するサービス アプリケーションが含まれています。2 番目のページには、1 つのデータベースが存在するサービス アプリケーションのすべてが表示されます。<br/><br/>  SharePoint サーバー 2016年データベースの詳細については、[データベースの種類と SharePoint サーバーの 2016年の説明](https://technet.microsoft.com/en-us/library/cc678868%28v=office.16%29.aspx)参照してください。 <br/> |
   
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Microsoft Skype for Business 2015 のアーキテクチャ モデル
<a name="SfB2015_ArchModel"> </a>

|**アイテム**|**説明**|
|:-----|:-----|
|[![ビジネス アーキテクチャ モデルのポスターの Skype の縮小表示](images/132288c0-6ae4-4394-88ab-b57dae367714.png)          ](https://www.microsoft.com/download/details.aspx?id=55022) <br/> ![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)  \| ![Visio ファイルが](images/ITPro_Other_VisioIcon.jpg)[Visio](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)  \| ![他の言語のバージョンのページを参照してください](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[その他の言語](https://www.microsoft.com/download/details.aspx?id=55022) <br/> |このポスターは、ビジネス オンライン、社内設置型で、ハイブリッドに、Skype を説明、クラウド PBX、および Exchange と SharePoint の構成との統合、ビジネスの意思決定者とソリューション ・ アーキテクトを知る必要があります。 <br/><br/> ビジネス オンラインの Skype と設置型のビジネス用の Skype を消費することができます、別の基本的なアーキテクチャ モデルの認識を高めるための IT プロフェッショナルのユーザー向けのものです。 <br/><br/>ベストのどちらの構成に適した、組織のニーズと将来の計画を開始します。考慮し、必要に応じて他のユーザーを使用します。などの Exchange と SharePoint またはマイクロソフトのクラウド PBX ソリューションを活用するソリューションとの統合を検討します。  <br/> |
   
## <a name="platform-options-posters"></a>プラットフォーム オプションのポスター

SharePoint 2013、Exchange 2013 および Lync 2013 向けのこれらの IT ポスターは、大きなポスターの形式で、一目でさまざまな展開の方法を比較する手段を提供します。各ポスターは利用可能な構成またはプラットフォーム オプションすべての一覧を示し、オプションごとに次の情報を説明します。
  
- **概要**概念図を含む、プラットフォームの概要です。
    
- **最適**適している特定のプラットフォームの一般的なシナリオです。
    
- **ライセンスの要件**展開に必要なライセンスです。
    
- **アーキテクチャ タスク**アーキテクトとして作成する必要があります決定します。
    
- **IT プロフェッショナルのタスクや責任の範囲**計画を立てる必要があるお客様の IT スタッフが日常業務です。
    
## <a name="sharepoint-2013-platform-options"></a>SharePoint 2013 プラットフォーム オプション
<a name="SP2013_Options"> </a>

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![SharePoint 2013 のプラットフォーム ・ オプションのサムネイル イメージ](images/SP_PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=40332) <br/> ![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](http://go.microsoft.com/fwlink/p/?LinkId=324594)  \| ![Visio ファイルが](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=324593)  \| ![他の言語のバージョンのページを参照してください](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[その他の言語](https://www.microsoft.com/download/details.aspx?id=40332) <br/> |ビジネス ディシジョン メーカー (Bdm) と設計者は、このモデルは、SharePoint 2013、SharePoint で、Office 365、Office 365、Azure では、設置型のみの展開とオンプレミスのハイブリッドのプラットフォーム ・ オプションを示します。各アーキテクチャ、推奨事項、ライセンス契約の要件、およびアーキテクトおよびプラットフォームごとの IT プロフェッショナルの作業の一覧の概要を掲載しています。Azure 上のいくつかの SharePoint ソリューションを強調表示されます。<br/><br/>アクセシブルなテキストには、このポスターのバージョンが、[アクセス可能なダイアグラムを Microsoft SharePoint 2013 のプラットフォーム ・ オプション](accessible-diagrammicrosoft-sharepoint-2013-platform-options.md)を参照してください。  <br/> |
   
## <a name="exchange-2013-platform-options"></a>Exchange 2013 プラットフォーム オプション
<a name="Exch2013_options"> </a>

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![Exchange プラットフォーム ・ オプションのサムネイル イメージ](images/ITPro_Other_Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> ![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)  \| ![Visio ファイルが](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkID=398742)  \| ![他の言語のバージョンのページを参照してください](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[その他の言語](https://www.microsoft.com/download/details.aspx?id=42676) <br/> |Bdm とアーキテクトは、このモデルは、Exchange 2013 の利用可能なプラットフォームのオプションを説明します。お客様は、Office 365 では、ハイブリッドの交換、Exchange Server、オンプレミスおよびホストされている Exchange で Exchange のオンラインから選択できます。ポスターには、各ライセンス要件、IT プロフェッショナルの責任の最も理想的なシナリオを含め、アーキテクチャの各オプションの詳細が含まれています。<br/><br/>アクセシブルなテキストには、このポスターのバージョンが、[アクセス可能なダイアグラムを Microsoft Exchange 2013 のプラットフォーム ・ オプション](accessible-diagrammicrosoft-exchange-2013-platform-options.md)を参照してください。  <br/> |
   
## <a name="lync-2013-platform-options"></a>Lync 2013 プラットフォーム オプション
<a name="Lync2013_Options"> </a>

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![Lync プラットフォーム ・ オプションのサムネイル イメージ](images/Lync_PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> ![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)  \| ![Visio ファイルが](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkID=391839)  \| ![他の言語のバージョンのページを参照してください](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[その他の言語](https://www.microsoft.com/download/details.aspx?id=41677) <br/> |このモデルは、管理職意思決定者と事業計画担当のために、Lync 2013 の使用可能なプラットフォーム オプションを示しています。お客様は Office 365 による Lync Online、Hybrid Lync、オンプレミス Lync Server、Hosted Lync から選択できます。IT ポスターにはそれぞれのオプションに最適なシナリオ、ライセンス要件、および IT 技術者の業務などを含む、各アーキテクチャのオプションの詳細が含まれています。  <br/> |
   
## <a name="sharepoint-in-azure-solutions-posters"></a>Azure の SharePoint のソリューションのポスター
<a name="Lync2013_Options"> </a>

これら IT のポスターは、SharePoint Server 2013 を使用して大規模なポスター形式で Azure ベースのソリューションを表示します。
  
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト
<a name="Azure_sharepoint2013"> </a>

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![SharePoint を使用した Azure のインターネット サイトのイメージ](images/MS_AZ_SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> ![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| ![Visio ファイルが](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  \| ![他の言語のバージョンのページを参照してください](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[その他の言語](https://www.microsoft.com/download/details.aspx?id=41992) <br/> |このポスターは、主要な設計活動の概要について説明し、Azure でインターネットに接続するサイトのアーキテクチャの選択肢をお勧めします。アクセシブルなテキストには、このポスターのバージョンが、[アクセス可能なダイアグラム - SharePoint 2013 の Microsoft Azure 内のインターネット サイト](accessible-diagraminternet-sites-in-microsoft-azure-for-sharepoint-2013.md)を参照してください。<br/><br/> 詳細については、以下の記事を参照してください。  <br/><br/> - [SharePoint Server 2013 を使用して Microsoft Azure 内のインターネット サイト](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [SharePoint 2013 の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> - [Azure Active Directory を使用して SharePoint 2013 の認証のため](using-microsoft-azure-active-directory-for-sharepoint-2013-authentication.md) <br/> |
   
### <a name="design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>設計サンプル: SharePoint 2013 のための Microsoft Azure のインターネット サイト
<a name="DesignSampleInternetSites"> </a>

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![設計サンプルのイメージ: Microsoft Azure for SharePoint 2013 のインターネット サイト](images/MS_AZ_InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> ![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| ![Visio ファイルが](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)  \| ![他の言語のバージョンのページを参照してください](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[その他の言語](https://www.microsoft.com/download/details.aspx?id=41991) <br/> |独自アーキテクチャのインターネットに接続するサイトで、SharePoint Server 2013 を使用して、Azure の開始点としてこの設計サンプルを使用します。アクセシブルなテキストには、このポスターのバージョンが、次を参照してください。[アクセス可能な図の設計サンプル: インターネットのサイトで、SharePoint 2013 の Microsoft Azure](accessible-diagramdesign-sample-internet-sites-in-microsoft-azure-for-sharepoint.md)。<br/><br/> 詳細については、以下の記事を参照してください。  <br/><br/> - [SharePoint Server 2013 を使用して Microsoft Azure 内のインターネット サイト](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [SharePoint 2013 の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> - [Azure Active Directory を使用して SharePoint 2013 の認証のため](using-microsoft-azure-active-directory-for-sharepoint-2013-authentication.md) <br/> |
   
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>Microsoft Azure に対する SharePoint の障害復旧
<a name="sharepoint_recovery_Azure"> </a>

****

|**アイテム**|**説明**|
|:-----|:-----|
|[![Azure に SharePoint 災害復旧のプロセス](images/SP_DR_Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> ![PDF ファイル](images/ITPro_Other_PDFicon.png)[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)  \| ![Visio ファイルが](images/ITPro_Other_VisioIcon.jpg)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)  \| ![他の言語のバージョンのページを参照してください](images/e16c992d-b0f8-48ae-bf44-db7a9fcaab9e.png)[その他の言語](https://www.microsoft.com/download/details.aspx?id=41993) <br/> |この IT のポスターは、Azure での災害復旧環境のアーキテクチャの原則を示しています。アクセシブルなテキストには、このポスターのバージョンが、[アクセス可能なダイアグラム - Microsoft Azure に SharePoint の災害復旧](accessible-diagramsharepoint-disaster-recovery-to-microsoft-azure.md)を参照してください。<br/><br/> 詳細については、以下の記事を参照してください。  <br/><br/> - [Microsoft Azure では SharePoint Server 2013 の災害復旧](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [SharePoint 2013 の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md) <br/> |
   
## <a name="see-also"></a>See Also

<a name="Lync2013_Options"> </a>

[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)
  
[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[ハイブリッド ソリューション](hybrid-solutions.md)




