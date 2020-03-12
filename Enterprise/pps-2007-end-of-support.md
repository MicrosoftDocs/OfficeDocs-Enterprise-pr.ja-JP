---
title: PerformancePoint Server 2007 のサポート終了ロードマップ
ms.author: deniseb
author: denisebmsft
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- PSV120
- PDD140
- MET150
ms.assetid: 89d9feee-2285-419c-8c14-0f7f583536e0
f1.keywords:
- NOCSH
description: PerformancePoint Server 2007、ProClarity、および SharePoint Server 2007 がサポートの終了に達しました。 この記事は、BI ソリューションのアップグレードを計画する場合にお読みください。
ms.openlocfilehash: 37ac5425e282efd4a9e8e0fc2a8f6b5c897ec105
ms.sourcegitcommit: 1c646afb10db9d3d1e6a346089b7845268b0c9d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "42605618"
---
# <a name="performancepoint-server-2007-end-of-support-roadmap"></a>PerformancePoint Server 2007 のサポート終了ロードマップ

*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*

Office 2007 のサーバーとアプリケーションは、ビジネスインテリジェンス (BI) ソリューションの一部として使用される可能性のあるサーバーやアプリケーションを含む、サポートの最後まで到達しました。 次の表に、影響を受ける BI アプリケーションの一覧を示します。
  
|**Microsoft BI アプリケーション**|**サポート終了日**|
|:-----|:-----|
|ProClarity Analytics Server 6.3 Service Pack 3  <br/> ProClarity デスクトップ Professional 6.3  <br/> ProClarity SharePoint Viewer 6.3  <br/> |2017 年 7 月 11 日  <br/> |
|SharePoint Server 2007 Service Pack 3  <br/> |2017 年 10 月 10 日  <br/> |
|PerformancePoint Server 2007 Service Pack 3  <br/> |2018 年 1 月 9 日  <br/> |
   
詳細については、「 [Office 2007 サーバーおよびクライアントからのアップグレードに役立つリソース](upgrade-from-office-2007-servers-and-products.md)」を参照してください。
  
## <a name="what-does-end-of-support-mean"></a>サポートが終了するとどうなるのか

PerformancePoint Server 2007 SP3、ProClarity software、SharePoint Server 2007 SP3 などの microsoft 製品には、Microsoft が新機能、バグ修正プログラム、およびセキュリティ更新プログラムを提供するサポートライフサイクルがありました。 製品のライフサイクルは通常、製品の最初のリリースから10年の間存続しており、そのライフサイクルの終了日は製品のサポート終了と呼ばれます。 ProClarity、PerformancePoint Server、および SharePoint Server 2007 のサポートが終了すると、Microsoft は提供しなくなります。
  
- 発生する可能性のある問題のテクニカルサポート
    
- 検出された問題と、サーバーの安定性と有用性に影響する可能性のあるバグの修正
    
- 検出された脆弱性に対するセキュリティの修正。サーバーまたはアプリケーションがセキュリティ侵害に対して脆弱になる可能性がある
    
- タイムゾーンの更新
    
ProClarity、SharePoint Server 2007 SP3、および PerformancePoint Server 2007 SP3 のインストールは、サポートが終了した場合でも引き続き実行されます。 ただし、これらのアプリケーションからできるだけ早く移行することを強くお勧めします。
  
## <a name="what-are-my-options"></a>使用できるオプション

これらの BI アプリケーションがサポートの終了に達すると、オプションを調査してアップグレード計画を準備するのに非常に時間がかかるようになります。 2007以降の Microsoft BI アプリケーションには多くの変更が加えられており、次の表に要約されているように、いくつかのオプションを考慮する必要があります。
  
|**使用していた場合**|**次のオプションを参照してください...**|**次の点に注意してください。**|
|:-----|:-----|:-----|
| PerformancePoint Server 2007 の&amp;監視分析機能 (次のものが含まれる)  <br/><br/>  PerformancePoint Monitoring Server  <br/><br/>  PerformancePoint ダッシュボード デザイナー  <br/><br/>  SharePoint Services のダッシュボードビューアー (PerformancePoint ダッシュボード、スコアカード、およびレポートのレンダリングに使用されます)  <br/> |**ブラウザー内**の excel (クラウドまたはオンプレミス) 概要については、「 [Excel および Office の BI 機能 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx) 」を参照してください。 <br/><br/> **POWER BI** (クラウドまたはオンプレミス)。 概要については、「 [POWER BI とは](https://go.microsoft.com/fwlink/?linkid=841341)」を参照してください。 <br/><br/> **SQL Server Reporting Services** (オンプレミス)。 概要については、「 [SQL Server Reporting Services (SSRS): モバイルおよび改ページレポートを作成、展開、および管理](https://go.microsoft.com/fwlink/?linkid=841342)する」を参照してください。 <br/><br/> **PerformancePoint Services** (オンプレミス)。 概要については、「 [PerformancePoint Services の新機能 (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=841343) 」を参照してください。 <br/> |Excel は、オンライン (クラウドベース) またはオンプレミスのソリューションとして使用できます。 Excel の機能を使用すると、レポートとダッシュボードに関する多くのニーズを満たすことができます。  <br/><br/> Power BI は、オンラインまたはオンプレミスのソリューションとして使用できます。 Power BI は Office 365 には含まれていませんが、Power BI for free を使い始めることができます。また、データの使用状況とビジネスニーズに応じて、Power BI Pro にアップグレードできます。 <br/> <br/> Reporting Services と PerformancePoint Services は、どちらもオンプレミスのソリューションです。  <br/><br/> PerformancePoint Services は、SharePoint Server 2010、SharePoint Server 2013、および SharePoint Server 2016 で利用できます。 <br/> <br/> PerformancePoint Server 2007 で使用できる一部の機能とレポートの種類は、Excel、Power BI、Reporting Services、または PerformancePoint Services では使用できません。 利用可能な機能を確認して、ビジネスニーズに最適なソリューションを決定する必要があります。  <br/> |
| ProClarity ソフトウェア (以下を含む) <br/> <br/>  ProClarity デスクトップ Professional  <br/> <br/> ProClarity Analytics Server  <br/> <br/> ProClarity SharePoint Viewer  <br/> |**Microsoft パートナーと協力**して、お客様のニーズに最適なソリューションを特定します。 [Microsoft パートナーセンター](https://go.microsoft.com/fwlink/?linkid=841249)にアクセスする <br/><br/> また、excel で excel をブラウザー、Power BI、SQL Server Reporting Services、または PerformancePoint Services で使用することを検討することもできます。  <br/> |ProClarity ソフトウェアで利用できる一部の機能と機能は、Excel、Power BI、Reporting Services、PerformancePoint Services など、他の Microsoft 製品で利用できます。  <br/> |
|SharePoint Server 2007 Kpi (MOSS Kpi とも呼ばれる)  <br/> |Excel **Services を使用した excel**。 概要については、「 [excel および Excel Services のビジネスインテリジェンス (SharePoint Server 2013)](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx) 」を参照してください。 <br/> |Sharepoint Server 2007 を使用して作成された MOSS Kpi は、SharePoint Server 2010、SharePoint Server 2013、および SharePoint Server 2016 で使用できます。ただし、新しい MOSS Kpi を作成することはできません。  <br/> |
|Excel 2007  <br/> |**Excel** (クラウドまたはオンプレミス)。 概要については、「 [Excel および Office の BI 機能 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx) 」を参照してください。 <br/><br/> **POWER BI** (クラウドまたはオンプレミス)。 概要については、「 [POWER BI とは](https://go.microsoft.com/fwlink/?linkid=841341)」を参照してください。 <br/> |Excel と Power BI はどちらも、さまざまなデータソースをサポートしており、組織のクラウドベースのソリューションとオンプレミスのソリューションを提供しています。  <br/> |
   
### <a name="what-if-i-need-help-selecting-a-solution"></a>ソリューションの選択についてのヘルプが必要な場合は、どうすればよいですか?

多くの BI 選択を利用できるようになると、どのオプションが最適かを判断するのが圧倒的なものになるかもしれません。 お客様にご支援できるオンラインガイドが用意されています。 「 [Microsoft ビジネスインテリジェンス (BI) ツールを選択する」を参照して、分析とレポート作成を](https://go.microsoft.com/fwlink/?linkid=839877)行います。
  
### <a name="what-happens-if-i-dont-upgrade-now"></a>今アップグレードしていない場合はどうなりますか?

この時点でアップグレードしないことを選択できます。 既存のサーバーとアプリケーションは引き続き実行されます。 ただし、追加の更新プログラム (サポートの終了後にセキュリティ更新プログラムを含む) を受け取ることはありません。 また、サーバーアプリケーションに問題が発生した場合は、Microsoft テクニカルサポートからサポートを受けることができなくなります。
  
## <a name="how-do-i-plan-my-upgrade"></a>アップグレードを計画する方法

アップグレードオプションを調査したら、次の手順として、アップグレード計画を準備します。 次のセクションでは、ソリューションの計画に役立つ情報とその他のリソースへのリンクを示します。 Microsoft BI アプリケーションに関しては、次の4つの主要なオプションがあります。これには、クラウドまたはオンプレミスの両方で機能する2つと、オンプレミスのみのソリューションである2つのオプションがあります。
  
|**オプション**|**クラウドまたはオンプレミスの場合**|
|:-----|:-----|
|[Excel](#excel-with-sharepoint-server-on-premises) <br/> |Both/フォーム/データシート  <br/> |
|[Power BI](#use-power-bi-in-the-cloud-or on-premises) <br/> |Both/フォーム/データシート  <br/> |
|[レポート サービス](#use-reporting-services-on-premises) <br/> |オンプレミスのみ  <br/> |
|[PerformancePoint Services](#use-performancepoint-services-on-premises) <br/> |オンプレミスのみ  <br/> |
   
### <a name="use-excel-in-the-cloud-or-on-premises"></a>Excel を使用する (クラウドまたはオンプレミスの場合)

Excel (SharePoint Server の Excel Services とも呼ばれます) では、ユーザーは、コンピューターに Excel がインストールされていなくても、ブラウザーウィンドウでブックを表示して使用できます。 Excel を使用して、レポート、スコアカード、およびダッシュボードを作成し、ブラウザーで Excel を使用して、他のユーザーとブックを共有できます。これには、Office 365 の一部として SharePoint Online を使用しているか、オンプレミスの SharePoint Server を使用しているかを指定します。 また、オンプレミスまたはクラウドに保存されているデータを使用して、さまざまなデータソースを使用することができます。
  
次の表では、Office 365 で Excel を使用して SharePoint Server で Excel を使用する場合の主な利点と、以下の追加情報を比較しています。
  
|**[Office 365 を使用した Excel (クラウド)](#excel-with-office-365-in-the-cloud)**|**[SharePoint Server (オンプレミス) を含む Excel](#excel-with-sharepoint-server-on-premises)**|
|:-----|:-----|
|**最新の最大バージョンの Excel を取得**します。 Office 365 では、強力で新しいグラフの種類、グラフや表をすばやく簡単に作成する機能、およびより多くのデータソースをサポートする機能を含む最新バージョンの Excel を入手できます。 <br/> <br/> **セットアップがより簡単に**なりました。 Excel は Office 365 for business に付属しているため、お客様の側ではあまり複雑ではありません。 サインアップしてサインインすると、オンプレミスのサーバーをアップグレードするよりも迅速かつ効率的に稼働することができます。 <br/> <br/> **ユーザーがブックにアクセスできる場所があり**ます。 ユーザーは、自分のコンピューター、スマートフォン、タブレットを使用して、どこからでもブックを安全に表示できます。 <br/> <br/> **他にもあり**ます。 「 [Excel および Office の BI 機能 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx) 」を参照してください。 <br/> |**グローバル設定を管理し**ます。 SharePoint 管理者は、セキュリティ、負荷分散、セッション管理、ブックのキャッシュ、外部データ接続などのグローバル設定を指定できます。 <br/> <br/> **PerformancePoint services で Excel Services を使用することができ**ます。 SharePoint Server のインストールの一部として Excel Services と PerformancePoint Services を構成し、PerformancePoint ダッシュボードに Excel Services レポートを含めることができます。 <br/> <br/> **他にもあり**ます。 「 [Excel Services および Excel Services のビジネスインテリジェンス (SharePoint Server 2013)」を](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx)参照してください。 <br/> |
   
#### <a name="excel-with-office-365-in-the-cloud"></a>Office 365 を使用した Excel (クラウド)

Office 365 に移行すると、最新のサービスとアプリケーション (Excel 2016 を含む) が使用できるようになります。 PerformancePoint Services は Office 365 では使用できないため、PerformancePoint ダッシュボードの内容を Excel ブックまたは他のレポートに置き換えます。 この記事では、Excel 2016 に多くの種類のグラフがあり、Excel で優れたダッシュボードを作成する方がはるかに簡単になりました。 そして、新しい機能が定期的に追加されています。 詳細については、「 [Excel 2016 For Windows の新機能](https://support.office.com/article/5fdb9208-ff33-45b6-9e08-1f5cdb3a6c73.aspx)」を参照してください。
  
また、50またはそれ以上の Office 365 を購入した場合は、Microsoft FastTrack チームがセットアップに役立てることができます。 詳細については、 [Fasttrack](https://www.microsoft.com/fasttrack/microsoft-365/office-365)を参照してください。
  
#### <a name="excel-with-sharepoint-server-on-premises"></a>SharePoint Server (オンプレミス) を含む Excel

新しいバージョンの SharePoint にアップグレードする場合は、次のように excel Services またはブラウザーで Excel を使用できます。
  
- SharePoint Server 2010 の Excel Services
    
- SharePoint Server 2013 の Excel Services
    
- Office Online Server の一部であり、SharePoint Server 2016 とは別にインストールされる Excel
    
SharePoint Server の新しいバージョンで PerformancePoint Services を構成し、それを Excel と組み合わせて使用することもできます。
  
SharePoint のアップグレードオプションの詳細については、「 [Sharepoint Server 2007 のサポート終了ロードマップ](sharepoint-2007-end-of-support.md)」を参照してください。
  
Excel Services の詳細については、「 [Excel services の概要 (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=841362)」を参照してください。
  
### <a name="use-power-bi-in-the-cloud-or-on-premises"></a>Power BI (クラウドまたはオンプレミス) を使用する

Power BI は、データを分析し、insights を共有するためのビジネス分析ツールのスイートです。 Power BI では、オンプレミスまたはオンラインのデータソースを使用して、対話型のレポートとダッシュボードを作成できます。 ユーザーは、自分のコンピューターまたはモバイルデバイスを使用して、レポートやダッシュボードを表示して使用できます。
  
Power BI は、Office 365 または SharePoint Server には含まれていませんが、Power BI デスクトップ、Power BI ゲートウェイ、Power BI サービスを含む個別のオファーリングです。 Power BI は、SharePoint Online とも統合されています。 Power BI を無料で使い始めることができます。また、データの使用状況とビジネスニーズに応じて、Power BI Pro にアップグレードできます。 詳細については、「 [POWER BI とは](https://go.microsoft.com/fwlink/?linkid=841341)」を参照してください。
  
### <a name="use-reporting-services-on-premises"></a>Reporting Services を使用する (オンプレミス)

SQL Server Reporting Services は、強力なレポートソリューションを提供します。また、レポートサービスをネイティブモードまたは SharePoint 統合モードでインストールして構成することもできます。 レポートデザイナー、レポートビルダー、Power View などのさまざまなツールを使用して、レポートを作成できます。 SQL Server の最新リリースでは、SQL Server Mobile Report Publisher を使用して、任意の画面サイズにスケールされるレポートを配信することもできます。これにより、組織は自分のモバイルデバイスでレポートを使用できるようになります。 詳細については、「 [SQL Server Reporting Services (SSRS): モバイルおよび改ページレポートを作成、展開、管理](https://go.microsoft.com/fwlink/?linkid=841342)する」を参照してください。
  
### <a name="use-performancepoint-services-on-premises"></a>PerformancePoint Services を使用する (オンプレミス)

ご存知のように、PerformancePoint Server 2007 は SharePoint Server 2007 とは別に購入されました。 SharePoint Server 2010 以降では、PerformancePoint Services は SharePoint Server のサービスアプリケーションです。 これは、PerformancePoint Services を使用するために、個別のサーバーライセンスまたはハードウェアを購入する必要がないことを意味します。
  
PerformancePoint Server 2007 から PerformancePoint Services に移動するには、より新しいバージョンの SharePoint Server に移動して、PerformancePoint Services を構成します。 移動先の SharePoint Server のバージョンによって、既存のダッシュボードコンテンツを PerformancePoint Server 2007 から PerformancePoint Services にインポートできるかどうかが決まります。
  
- SharePoint Server 2010 にアップグレードしている場合は、performancepoint Server 2007 から performancepoint ダッシュボードのコンテンツを SharePoint Server 2010 の performancepoint Services にインポートできます。 このしくみの詳細については、「 [Import Wizard: PerformancePoint server 2007 content To SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=838873)」を参照してください。
    
- SharePoint Server 2013 または SharePoint Server 2016 に移行している場合は、ほとんどの場合、新しいダッシュボードコンテンツ (データソース、レポート、スコアカード、およびダッシュボードページ) を作成する必要があります。
    
PerformancePoint Services アップグレードプランを開始するには、次のリソースを参照してください。
  
1. [SharePoint Server 2007 サポート終了ロードマップ](sharepoint-2007-end-of-support.md)
    
2. 移動先の SharePoint のバージョンがわかっている場合は、PerformancePoint Services の対応する記事を参照してください。
    
  - [PerformancePoint Services を計画する (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=841363)
    
  - [SharePoint Server の PerformancePoint Services 2013 の概要](https://go.microsoft.com/fwlink/?linkid=841551)
    
  - [SharePoint Server 2016 の PerformancePoint Services の概要](https://go.microsoft.com/fwlink/?linkid=874704)
    
PerformancePoint Services にアップグレードすると、いくつかの新機能と拡張機能が利用できるようになります。 PerformancePoint Services では、強化されたスコアカード、新しい視覚エフェクト (分解ツリー、KPI 詳細レポートなど) や、より多くのグラフの種類、タイムインテリジェンスフィルター処理能力の向上、およびアクセシビリティへの対応の向上が提供されます。 詳細については、「 [PerformancePoint Services の新機能 (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=841343)」を参照してください。
  
## <a name="where-can-i-get-help-with-my-upgrade"></a>アップグレードに関するヘルプはどこで入手できますか?

オンプレミスでアップグレードしているか、Office 365 に移行しているかにかかわらず、Microsoft パートナーと連携することをお勧めします。 認定パートナーは、ビジネスニーズに最も適したソリューションを特定し、展開に役立てることができます。 [Microsoft パートナーセンター](https://go.microsoft.com/fwlink/?linkid=841249)にアクセスし、検索フィルターを使用してソリューションプロバイダーを検索します。
  
## <a name="related-topics"></a>関連項目

[Office 2007 のサーバーとクライアントからのアップグレードに役立つリソース](upgrade-from-office-2007-servers-and-products.md)