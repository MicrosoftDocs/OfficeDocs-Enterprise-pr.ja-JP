---
title: Project Server 2007 のサポート終了ロードマップ
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
ms.assetid: d379018f-72b7-4284-b40a-6c23c8ae38fe
description: 2017年10月10日に、Project Server 2007、Project ポートフォリオサーバー、および Project 2007 のサポートが終了しました。 この記事を使用して、今すぐアップグレードを計画します。
ms.openlocfilehash: 4a2b046ca68de3571cd5be15bce48a6c30b8bf51
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "44775076"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Project Server 2007 のサポート終了ロードマップ

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

2017で Office 2007 サーバーおよびアプリケーションのサポートが終了し、移行の計画を検討する必要があります。 現在 Project Server 2007 を使用している場合は、その関連製品に次のサポート終了日があることに注意してください。
  
|**Product**|**サポート終了日**|
|:-----|:-----|
|Project Server 2007  <br/> |2017 年 10 月 10 日  <br/> |
|Project ポートフォリオサーバー2007  <br/> |2017 年 10 月 10 日  <br/> |
|Project 2007 Standard  <br/> |2017 年 10 月 10 日  <br/> |
|Project 2007 Professional  <br/> |2017 年 10 月 10 日  <br/> |
   
退職に到達する Office 2007 サーバーの詳細については、「 [Upgrade From office 2007 servers and client products](upgrade-from-office-2007-servers-and-products.md)」を参照してください。
  
## <a name="what-does-end-of-support-mean"></a>サポートが終了するとどうなるのか

ほぼすべての Microsoft 製品と同様に、Project Server には、新機能、バグ修正、セキュリティ修正プログラムなどを提供する、サポートライフサイクルがあります。 このライフサイクルは通常、製品の最初のリリースから10年後に持続し、このライフサイクルの最後は製品のサポート終了と呼ばれます。 Project Server 2007 は、2017年10月10日にサポート終了に達したため、Microsoft は提供しなくなりました。
  
- 発生する可能性のある問題のテクニカルサポート。
    
- 検出された問題についてバグ修正を行い、サーバーの安定性と有用性に影響を与える可能性があります。
    
- 検出された脆弱性に対するセキュリティ修正プログラムによって、サーバーがセキュリティ侵害に対して脆弱になる可能性がある。
    
- タイム ゾーンの更新。
    
Project Server 2007 のインストールは、この日付以降も引き続き実行されます。 ただし、上記の変更によって、Project Server 2007 からできるだけ早く移行することを強くお勧めします。
  
## <a name="what-are-my-options"></a>使用できるオプション

Project Server 2007 を使用している場合は、次のような移行オプションを調べる必要があります。
  
- Project Online への移行
    
- 新しいオンプレミスバージョンの Project Server に移行します (Project Server 2016 を推奨)。
    
|**Project Online への移行を希望する理由**|**Project Server 2016 への移行を希望する理由**|
|:-----|:-----|
| モバイルユーザーがいます。  <br/>  移行のコストは大きな懸念事項です (ハードウェア、ソフトウェア、時間と導入の労力など)。  <br/>  移行後に、環境を維持するためのコストは大きな懸念事項です (たとえば、自動更新、稼働状態の保証など)。  <br/> | ビジネスルールは、クラウドでのビジネスの運営から制限されています。  <br/>  環境に対して更新プログラムを制御する必要がある。  <br/> |
   
> [!NOTE]
> Office 2007 サーバーから移行するためのオプションの詳細については、「 [office 2007 サーバーおよびクライアントからのアップグレードに役立つリソース](upgrade-from-office-2007-servers-and-products.md)」を参照してください。 Project server と Project Online は同じリソース共有元を共有できないため、Project Server はハイブリッド構成をサポートしていないことに注意してください。 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2007"></a>Project Server 2007 からの移行を計画する際に必要となる重要な考慮事項

Project Server 2007 からの移行を計画する場合は、次の点を考慮する必要があります。
  
- **Microsoft パートナーからのヘルプを取得**する-Project Server 2007 からのアップグレードは難しい場合があり、多くの準備と計画が必要になります。 Project Server 2007 を最初にセットアップして構成する必要がない場合は、特に難しいことがあります。 さいわい、Project Server 2016 への移行または Project Online への移行を計画している場合でも、Microsoft のパートナーによって、この作業を行うことができます。 Microsoft パートナーを検索して、 [Microsoft パートナーセンター](https://go.microsoft.com/fwlink/p/?linkid=841249)での移行に役立てることができます。 「*ゴールドプロジェクト」と「ポートフォリオ管理*」で検索することによって、project の専門知識を持つすべての Microsoft パートナーの一覧を取得することができます。 
    
- **カスタマイズを計画**する-project server 2016 または project Online に移行する場合、project server 2007 環境で作業しているカスタマイズの多くが機能しない可能性があることに注意してください。 バージョン間の Project Server アーキテクチャには大きな違いがあります。また、必要なオペレーティングシステム、データベースサーバー、および新しいバージョンとの連携がサポートされているクライアント web ブラウザーもあります。 新しい環境で必要に応じてカスタマイズをテストまたは再構築する方法について、計画を立ててください。 アップグレードを計画することも、前方に移動するときに特定のカスタマイズが本当に必要かどうかを確認するのに十分な機会となります。 「 [2013 SharePoint へのアップグレード時に現在のカスタマイズの計画を作成](https://go.microsoft.com/fwlink/p/?linkid=842061)する」には、アップグレード時に現在のカスタマイズの評価と計画に関する重要な情報が含まれています。 
    
- **時間および**アップグレードの計画、実行、およびテストには、特に Project Server 2016 にアップグレードする場合は、多くの時間と労力が必要になります。 たとえば、Project Server 2007 から Project Server 2016 に移行する場合は、まず Project Server 2007 から Project Server 2010 に移行してから、データを確認してから、以降の各バージョンに移行するときに同じ操作を実行する必要があります。 Microsoft のパートナーに確認して、費用を比較し、お客様が実現するまでの時間とコストを比較してください。 
    
## <a name="migrate-to-project-online"></a>Project Online への移行

Project Server 2007 から Project Online に移行することを選択した場合は、次の操作を実行して、プロジェクト計画のデータを手動で移行できます。
  
1. プロジェクト計画を Project Server 2003 からに保存します。MPP 形式
    
2. Project Professional 2013、Project Professional 2016、または Project Online デスクトップクライアントを使用して、各 .mpp ファイルを開き、Project Online に保存して発行します。
    
Project Online で手動で PWA 構成を作成できます (たとえば、必要なユーザー設定フィールドやエンタープライズカレンダーを再作成します)。 また、Microsoft のパートナーもお手伝いできます。
  
主なリソース:
  
|**Resource**|**説明**|
|:-----|:-----|
|[Project Online の使用を開始する](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Project Online をセットアップして使用する方法について説明します。  <br/> |
|[Project Online サービスの説明](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |利用できるさまざまな Project Online プランに関する情報。  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>新しいオンプレミスバージョンの Project Server に移行する

Project Online に移行することによって、最高の価値とユーザーの利便性を実現できるとは確信していますが、一部の組織ではプロジェクトデータをオンプレミス環境に保持する必要があることも理解しています。 プロジェクトデータをオンプレミスで保持することを選択した場合は、project server 2007 環境を Project server 2010、Project Server 2013、または Project Server 2016 に移行できます。
  
Project Online に移行できない場合は、Project Server 2016 に移行することをお勧めします。 Project Server 2016 には、Project Server の以前のリリースに含まれていたすべての機能と概要が含まれており、project Online で利用できる機能に最も近いものがあります (ただし、一部の機能は Project Online でのみ利用可能です)。
  
各移行が完了したら、データが正常に移行されたことを確認する必要があります。
  
> [!NOTE]
> オンプレミスのソリューションに制限されている場合にのみ Project Server 2010 への移行を検討する場合は、さらに多くのサポートが残されることに注意することが重要です。 Project Server 2010 Service Pack 2 サポート終了日は10/13/2020 です。 サポート終了日の詳細については、「 [Microsoft 製品ライフサイクルポリシー](https://go.microsoft.com/fwlink/p/?linkid=842066)」を参照してください。 
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>Project Server 2016 に移行する方法

Project Server 2007 と Project Server 2016 のアーキテクチャの違いにより、直接移行のパスが妨げられています。 これは、project server 2016 にアップグレードするまで、project server 2007 データを次のバージョンの Project Server に移行する必要があることを意味します。
  
Project Server 2016 にアップグレードするには、次の手順を実行する必要があります。
  
1. 手順 1: Project Server 2007 から Project Server 2010 に移行します。
    
2. 手順 2: Project Server 2010 から Project Server 2013 に移行します。
    
3. 手順 3: Project Server 2013 から Project Server 2016 に移行します。
    
各移行が完了したら、データが正常に移行されたことを確認する必要があります。
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>手順 1: Project Server 2007 から Project Server 2010 に移行する

Project Server 2007 から Project Server 2010 にアップグレードするために必要な作業を完全に理解するには、TechNet の「 [Project server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812)コンテンツセットへのアップグレード」を参照してください。 
  
主なリソース:
  
|**Resource**|**説明**|
|:-----|:-----|
|[Project Server 2010 アップグレードの概要](https://go.microsoft.com/fwlink/p/?linkid=841813) <br/> |Project Server 2007 から Project Server 2010 にアップグレードするために必要な作業についての高度な理解を得ることができます。  <br/> |
|[Project Server 2010 へのアップグレードを計画する](https://go.microsoft.com/fwlink/p/?linkid=841815) <br/> |システム要件を含め、Project Server 2007 から Project Server 2010 にアップグレードするときに必要な計画の考慮事項について確認します。  <br/> |
   
#### <a name="how-do-i-upgrade"></a>アップグレードする方法

アップグレードの詳細については、「 [Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812)コンテンツセットへのアップグレード」を参照してください。アップグレードには、次の2つの異なる方法があることを理解しておくことが重要です。 
  
- **データベース接続アップグレード:** この方法では、環境内のコンテンツのみがアップグレードされ、構成設定はアップグレードされません。 Office Project Server 2007 から、32ビットのサーバーオペレーティングシステムのみをサポートするハードウェアに展開されている場合は、これをアップグレードする必要があります。 データベース接続アップグレードには、次の2種類の方法があります。 
    
  - **データベース-アタッチ完全アップグレード**-Office project Server 2007 データベースに格納されているプロジェクトデータ、および SharePoint コンテンツデータベースに格納されている Microsoft Project Web APP (PWA) サイトデータを移行します。 
    
  - **データベース接続コアアップグレード**-project Server データベースに格納されているプロジェクトデータのみを移行します。 
    
- **一括アップグレード**: ファームの構成データとファームのすべてのコンテンツは、既存のハードウェアの固定の順序でアップグレードされます。 一括アップグレードプロセスを開始すると、セットアップはファーム全体をオフラインにし、アップグレードが完了するまで Web サイトと Microsoft Project Web App サイトは使用できなくなります。その後、セットアップはサーバーを再起動します。 一括アップグレードを開始した後は、アップグレードを一時停止したり、以前のバージョンにロールバックしたりすることはできません。 運用環境ではなく、運用環境のミラー化されたイメージを作成し、この環境への一括アップグレードを実行することを強くお勧めします。 
    
その他のリソース:
  
- [Microsoft Project Server 2010 アップグレードの SuperFlow](https://go.microsoft.com/fwlink/p/?linkid=841277)
    
- [Project Server 2007 から Project Server 2010 への移行](https://go.microsoft.com/fwlink/p/?linkid=841278)
    
- [Project Web App Web パーツのアップグレードに関する考慮事項](https://go.microsoft.com/fwlink/p/?linkid=841276)
    
- [Project Software Development Kit (SDK)](https://go.microsoft.com/fwlink/p/?linkid=841275)
    
### <a name="step-2-migrate-to-project-server-2013"></a>手順 2: Project Server 2013 に移行する

Project Server 2010 に移行し、データが正常に移行されたことを確認した後、次の手順では、データを Project Server 2013 に移行します。
  
Project Server 2010 から Project Server 2013 にアップグレードするために必要な作業を完全に理解するには、TechNet の「 [Project server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822)コンテンツセットへのアップグレード」を参照してください。 
  
主なリソース:
  
|**Resource**|**説明**|
|:-----|:-----|
|[Project Server 2013 のアップグレード プロセスの概要](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Project Server 2010 から Project Server 2013 にアップグレードするために必要な作業についての高度な理解を得ることができます。  <br/> |
|[Project Server 2013 へのアップグレードを計画する](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |システム要件を含め、Project Server 2010 から Project Server 2013 にアップグレードするときに必要な計画の考慮事項について確認します。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>このバージョンへのアップグレードに関する注意事項

[Project Server 2013 アップグレードの新機能](https://go.microsoft.com/fwlink/p/?linkid=841824)このバージョンでのアップグレードに関していくつかの重要な変更を示します。 
  
- Project Server 2013 への一括アップグレードはありません。 Project Server 2010 から Project Server 2013 へのアップグレードでサポートされている唯一の方法は、データベース接続方式です。
    
- アップグレードプロセスでは、Project Server 2010 のデータを Project server 2013 形式に変換するだけでなく、4つの Project Server 2010 データベースを1つの Project Web App データベースにも統合するようになります。
    
- SharePoint Server 2013 と Project Server 2013 の両方が、以前のバージョンからクレームベース認証に変更されました。 従来の認証を使用している場合は、アップグレード時に考慮する必要があります。 詳細については、「[SharePoint 2013 でクラシックモードからクレームベース認証に移行する](https://go.microsoft.com/fwlink/p/?linkid=841825)」を参照してください。
    
その他のリソース:
  
- [Project Server 2013 へのアップグレード プロセスの概要](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [データベースおよび Project Web App サイト コレクションをアップグレードする (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Microsoft Project Server のアップグレードプロセスの図](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [高度なデータベース統合、Project Server 2010 から2013への移行は、簡単な手順で8つ](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>手順 3: Project Server 2016 に移行する

Project Server 2013 に移行し、データが正常に移行されたことを確認した後、次の手順では、データを Project Server 2016 に移行します。
  
Project Server 2013 から Project Server 2016 にアップグレードするために必要な作業を完全に理解するには、TechNet の「Project Server 2016 コンテンツセットへのアップグレード」を参照してください。
  
主なリソース:
  
|**Resource**|**説明**|
|:-----|:-----|
|[Project Server 2016 のアップグレード プロセスの概要](https://go.microsoft.com/fwlink/p/?linkid=841260) <br/> |Project Server 2013 から Project Server 2016 にアップグレードするために必要な作業についての高度な理解を得ることができます。  <br/> |
|[Project Server 2016 へのアップグレードを計画する](https://go.microsoft.com/fwlink/p/?linkid=841826) <br/> |Project Server 2013 から Project Server 2016 (を含む) にアップグレードするときに必要な計画の考慮事項について確認します。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>このバージョンへのアップグレードに関する注意事項

[Project Server 2016 アップグレードに関して知っておく必要のある](https://go.microsoft.com/fwlink/p/?linkid=841827)ことは、このバージョンのアップグレードに関する重要な変更点を示しています。次のようにします。 
  
- Project server 2013 データを移行する Project Server 2016 環境を作成する場合は、Project server の2016インストールファイルが SharePoint Server 2016 に含まれていることに注意してください。 詳細については、「 [Deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829)」を参照してください。
    
- Project Server 2016 では、リソース計画は廃止されました。 Project Server 2013 のリソース計画は、project Server 2016 および Project Online のリソース予約に移行されます。 詳細については、「[概要: リソース予約](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870)」を参照してください。 
    
## <a name="migrate-from-portfolio-server-2007"></a>ポートフォリオサーバーからの移行2007

プロジェクトポートフォリオサーバー2007は、ポートフォリオ戦略、優先度設定、および最適化のために Project Server 2007 で使用されていました。 このバージョン以降、プロジェクトポートフォリオサーバーの追加バージョンは作成されていません。 ただし、ポートフォリオ管理機能は Project Server 2016 と Premium バージョンの Project Online の両方で使用できます。 Project ポートフォリオ2007サーバーからのデータは、に移行できません。 ビジネスドライバーなどのデータは再作成する必要があります。
  
その他の技術情報:
  
- [Project Online サービスの説明](https://go.microsoft.com/fwlink/p/?linkid=841280): project Server 2016 および Project Online Premium に含まれているポートフォリオ管理機能を参照してください。
    
- [Microsoft Office Project ポートフォリオサーバー2007移行ガイド](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>関連項目

[SharePoint Server 2007 サポート終了ロードマップ](sharepoint-2007-end-of-support.md)
  
[Office 2007 のサーバーとクライアントからのアップグレードに役立つリソース](upgrade-from-office-2007-servers-and-products.md)
  

