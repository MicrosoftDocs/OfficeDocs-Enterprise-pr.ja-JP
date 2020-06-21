---
title: Project Server 2010 サポート終了のロードマップ
ms.author: efrene
author: efrene
manager: pamg
ms.date: 04/14/2020
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
description: Project Server 2010 のサポートは、2021年4月13日に終了します。 この記事は、Project Online またはオンプレミスの Project Server の新しいバージョンにアップグレードするためのガイドとして使用してください。
ms.openlocfilehash: e9bbe47c93b9e73e37abd352f02872149d28ce90
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "44775066"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Project Server 2010 サポート終了ロードマップ

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

Project Server 2010 は **、2021年4月 13**日のサポート終了に到達します。 この日付は、2020年10月13日の以前のサポート終了日から延長されました。 現在 Project Server 2010 を使用している場合は、これらの他の関連製品に次のサポート終了日があることに注意してください。
  
|**Product**|**サポート終了日**|
|:-----|:-----|
|Project 2010 Standard <br/> |2020年10月13日  <br/> |
|Project 2010 Professional  <br/> |2020年10月13日  <br/> |

   
Office 2010 サーバーのサポートが終了するまでの詳細については、「 [Upgrade From office 2010 servers and client products](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office)」を参照してください。
  
## <a name="what-does-end-of-support-mean"></a>サポートが終了するとどうなるのか

ほぼすべての Microsoft 製品と同様に、Project Server には、新機能、バグ修正、およびセキュリティ更新プログラムを提供するサポートライフサイクルがあります。 このライフサイクルは通常、製品の最初のリリースから10年後に持続し、このライフサイクルの最後は製品のサポート終了と呼ばれます。 Project Server 2010 が2021年4月13日のサポート終了日に達すると、Microsoft は提供しなくなります。
  
- 発生する可能性のある問題のテクニカルサポート。
    
- 検出された問題についてバグ修正を行い、サーバーの安定性と有用性に影響を与える可能性があります。
    
- 検出された脆弱性に対するセキュリティ修正プログラムによって、サーバーがセキュリティ侵害に対して脆弱になる可能性がある。
    
- タイム ゾーンの更新。
    
Project Server 2010 のインストールは、この日付以降も引き続き実行されます。 ただし、上記の変更によって、Project Server 2010 からできるだけ早く移行することを強くお勧めします。
  
## <a name="what-are-my-options"></a>使用できるオプション

Project Server 2010 を使用している場合は、次のような移行オプションを調べる必要があります。
  
- Project Online への移行
    
- 新しいオンプレミスバージョンの Project Server に移行します (Project Server 2019 を推奨)。

Project Server 2010 のサポート終了を回避するために取ることができる2つのパスを次に示します。

![Project Server 2010 のアップグレードパス](./media/project-server-2010-end-of-support/project-server-2010-end-of-support-timeline.png)

    


|**Project Server 2019 への移行を希望するのはなぜですか?**|**Project Online への移行を希望するのはなぜですか?**|
|:-----|:-----|
|ビジネスルールは、クラウドでのビジネスの運営から制限されています。  <br/>  環境に対して更新プログラムを制御する必要がある。  <br/> | モバイルまたはリモートのユーザーがいます。  <br/>  オンプレミスサーバーを移行するためのコストとしては、大きな懸念があります (ハードウェア、ソフトウェア、時間および実装の労力など)。  <br/>  移行後に、環境を維持するためのコストは大きな懸念事項です (たとえば、自動更新、稼働状態の保証など)。  <br/>  |

   
> [!NOTE]
> Office 2010 サーバーから移行するためのオプションの詳細については、「 [office 2010 サーバーおよびクライアントからのアップグレードに役立つリソース](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products)」を参照してください。 Project server と Project Online は同じリソース共有元を共有できないため、Project Server はハイブリッド構成をサポートしていないことに注意してください。 

### <a name="what-are-my-options-for-project-client"></a>Project クライアントのオプションとは
Project Professional 2010 または Project Standard 2010 を使用していて、移行オプションを調査する場合は、次の選択肢があります。
- Project Professional または Project Standard の新しいバージョンに移行する。
- Project Online や Project などのオンラインソリューションに web 用に移行します。
 
#### <a name="moving-to-a-newer-version-of-project-client"></a>新しいバージョンの Project クライアントに移行する

Project Standard 2010 から移行する場合は、project standard の新しいバージョン (Project Standard 2016 または Project Standard 2019) に移行できます。  最新の機能を利用するには、最新のバージョンに移行することをお勧めします。 また、現在のバージョンよりも古いバージョンに移行する (Project Standard 2016) ことは、サポートの終了日が近づくにつれて、このバージョンから移行する必要があることを意味します。

同様に、Project Professional 2010 から移行する場合は、新しいバージョンに移行することを選択できます (Project Professional 2019 または Project Professional 2016)。 可能であれば、最新バージョンに移行することをお勧めします。  Project Professional を使用して Project Server に接続している場合は、使用している Project Server のバージョンとの接続がサポートされているバージョンの Project Professional に移行するようにしてください。

Project Professional 2010 ユーザーは、Project Online デスクトップクライアントへの移行を選択することもできます。 Project Professional 2019 のサブスクリプションベースのバージョンであり、プロジェクト計画3およびプロジェクト計画5のサブスクリプションに含まれています。 

#### <a name="moving-to-an-online-solution"></a>オンラインソリューションへの移行

Project Professional 2010 または Project Standard 2010 からプロジェクトのサブスクリプションベースのオンラインソリューションへの移行を選択することもできます。 プロジェクトプラン3とプラン5の両方に、Project Online と、 [web 用の](https://support.office.com/article/what-can-you-do-with-project-for-the-web-b30f5442-be5f-43d2-9072-c95bff778ea1)最新のクラウドサービスが含まれています。 どちらにも、探索価値のある新機能とメリットが多数提供されています。

両方に含まれている機能の詳細、およびプロジェクト計画のライセンスに含まれる機能については、 [Microsoft project サービスの説明](https://docs.microsoft.com/office365/servicedescriptions/project-online-service-description/project-online-service-description)を参照してください。



  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>Project Server 2010 からの移行を計画する際に必要となる重要な考慮事項

Project Server 2010 からの移行を計画する場合は、次の点を考慮する必要があります。
  
- **Microsoft solution provider からのヘルプの取得**-Project Server 2010 からのアップグレードは課題となり、多くの準備と計画が必要になることがあります。 Project Server 2010 を最初にセットアップして構成する必要がない場合は、特に難しいことがあります。 さいわい、Project Server 2019 への移行または Project Online への移行を計画している場合には、この作業を行うことができる Microsoft ソリューションプロバイダーがあります。 Microsoft solution provider を検索すると、microsoft ソリューション[プロバイダセンター](https://go.microsoft.com/fwlink/p/?linkid=841249)での移行に役立てることができます。 
    
- **カスタマイズを計画**する-project server 2019 または project Online に移行する場合、project server 2010 環境で作業しているカスタマイズの多くが機能しない可能性があることに注意してください。 バージョン間の Project Server アーキテクチャには大きな違いがあります。また、必要なオペレーティングシステム、データベースサーバー、および新しいバージョンとの連携がサポートされているクライアント web ブラウザーもあります。 新しい環境で必要に応じてカスタマイズをテストまたは再構築する方法について、計画を立ててください。 アップグレードを計画することも、前方に移動するときに特定のカスタマイズが本当に必要かどうかを確認するのに十分な機会となります。 「 [2013 SharePoint へのアップグレード時に現在のカスタマイズの計画を作成]( https://docs.microsoft.com/SharePoint/upgrade-and-update/create-a-plan-for-current-customizations-during-upgrade-to-sharepoint-2013)する」には、アップグレード時に現在のカスタマイズの評価と計画に関する重要な情報が含まれています。 
    
- **時間および**アップグレードの計画、実行、およびテストは、特に Project Server 2019 にアップグレードする場合には、多くの時間と労力を必要とします。 たとえば、Project Server 2010 から Project Server 2019 に移行する場合は、まず Project Server 2010 から project Server 2013 に移行してから、データを確認してから、以降の各バージョンに移行するときに同じ操作を実行する必要があります (Project Server の場合は、次に、project 2016 Server の場合)。 Microsoft ソリューションプロバイダーに確認して、見積もりコストと、それが実現するのにかかる時間とコストを比較することができます。 
    
## <a name="migrate-to-project-online"></a>Project Online への移行

Project Server 2010 から Project Online に移行することを選択した場合は、次の操作を実行して、プロジェクト計画のデータを手動で移行できます。
  
1. プロジェクト計画を Project Server 2010 からに保存します。MPP 形式
    
2. Project Professional 2016、Project Professional 2019、または Project Online デスクトップクライアントを使用して、各 .mpp ファイルを開き、Project Online に保存して発行します。
    
Project Online で手動で PWA 構成を作成できます (たとえば、必要なユーザー設定フィールドやエンタープライズカレンダーを再作成します)。 Microsoft ソリューションプロバイダーは、このことを支援することもできます。
  
主なリソース:
  
|**Resource**|**説明**|
|:-----|:-----|
|[Project Online の使用を開始する](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Project Online をセットアップして使用する方法について説明します。  <br/> |
|[Project Online サービスの説明](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |利用できるさまざまな Project Online プランに関する情報。  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>新しいオンプレミスバージョンの Project Server に移行する

Project Online に移行することによって、最高の価値とユーザーの利便性を実現できるとは確信していますが、一部の組織ではプロジェクトデータをオンプレミス環境に保持する必要があることも理解しています。 プロジェクトデータをオンプレミスで保持することを選択した場合は、project server 2010 環境を Project server 2013、Project Server 2016、または Project Server 2019 に移行できます。
  
Project Online に移行できない場合は、Project Server 2019 に移行することをお勧めします。 Project Server 2019 には、Project Server の以前のリリースに含まれていた機能と機能の大部分が含まれており、project Online で利用できる機能に最も近いものがあります (一部の機能は、Project Online でのみ利用可能です)。
  
各移行が完了したら、データが正常に移行されたことを確認する必要があります。
  
> [!NOTE]
> オンプレミスのソリューションに制限されている場合にのみ Project Server 2013 への移行を検討する場合は、さらに多くのサポートが残されることに注意することが重要です。 Project Server 2013 Service Pack 2 サポート終了日は10/13/2023 です。 サポート終了日の詳細については、「 [Microsoft 製品ライフサイクルポリシー](https://go.microsoft.com/fwlink/p/?linkid=842066)」を参照してください。 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>Project Server 2019 に移行する方法

Project Server 2010 と Project Server 2019 のアーキテクチャの違いにより、直接移行のパスが妨げられています。 これは、project server 2019 にアップグレードするまで、project server 2010 データを次のバージョンの Project Server に移行する必要があることを意味します。
  
Project Server 2010 を Project Server 2019 にアップグレードするには、次の手順を実行する必要があります。
  
1. Project Server 2013 に移行します。
    
2. プロジェクトサービス2013から Project Server 2016 に移行します。
    
3. Project Server 2016 から Project Server 2019 に移行します。
    
各移行が完了したら、データが正常に移行されたことを確認する必要があります。
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>手順 1: Project Server 2013 に移行する

Project server 2010 データを Project Server 2019 に移行するための最初の手順は、最初に Project Server 2013 に移行することです。 
  
Project Server 2010 から Project Server 2013 にアップグレードするために必要な作業を完全に理解するには、「 [upgrade To Project server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822)」を参照してください。 
  
主なリソース:
  
|||
|:-----|:-----|
|[Project Server 2013 のアップグレード プロセスの概要](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Project Server 2010 から Project Server 2013 にアップグレードするために必要な作業についての高度な理解を得ることができます。  <br/> |
|[Project Server 2013 へのアップグレードを計画する](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |システム要件を含め、Project Server 2010 から Project Server 2013 にアップグレードするときに必要な計画の考慮事項について確認します。  <br/> |
   
[Project Server 2013 アップグレードの新機能](https://go.microsoft.com/fwlink/p/?linkid=841824)このバージョンでのアップグレードに関していくつかの重要な変更を示します。 
  
- Project Server 2013 への一括アップグレードはありません。 Project Server 2010 から Project Server 2013 へのアップグレードでサポートされている唯一の方法は、データベース接続方式です。
    
- アップグレードプロセスでは、Project Server 2010 のデータを Project server 2013 形式に変換するだけでなく、4つの Project Server 2010 データベースを1つの Project Web App データベースにも統合するようになります。
    
- SharePoint Server 2013 と Project Server 2013 の両方が、以前のバージョンからクレームベース認証に変更されました。 従来の認証を使用している場合は、アップグレード時に考慮する必要があります。 詳細については、「[SharePoint 2013 でクラシックモードからクレームベース認証に移行する]( https://docs.microsoft.com/sharepoint/upgrade-and-update/migrate-from-classic-mode-to-claims-based-authentication-in-sharepoint-2013)」を参照してください。
    
主なリソース:
  
- [Project Server 2013 へのアップグレード プロセスの概要](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [データベースおよび Project Web App サイト コレクションをアップグレードする (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Microsoft Project Server のアップグレードプロセスの図](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [高度なデータベース統合、Project Server 2010 から2013への移行は、簡単な手順で8つ](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>手順 2: Project Server 2016 に移行する

Project Server 2013 に移行し、データが正常に移行されたことを確認した後、次の手順では、データを Project Server 2016 に移行します。
  
Project Server 2013 から Project Server 2016 にアップグレードするために必要な作業を完全に理解するには、「 [upgrade To Project server 2016](https://docs.microsoft.com/Project/upgrade-to-project-server-2016)」を参照してください。
  
主なリソース:
  
|||
|:-----|:-----|
|[Project Server 2016 のアップグレード プロセスの概要](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |Project Server 2013 から Project Server 2016 にアップグレードするために必要な作業についての高度な理解を得ることができます。  <br/> |
|[Project Server 2016 へのアップグレードを計画する](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |Project Server 2013 から Project Server 2016 にアップグレードするときに必要な計画の考慮事項について確認します。  <br/> |
   
[Project Server 2016 アップグレードに関して知っておく必要のある](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow)ことは、このバージョンへのアップグレードに関する重要な変更点を示しています。これには次のようなものがあります。 
  
- Project server 2013 データを移行する Project Server 2016 環境を作成する場合は、Project server の2016インストールファイルが SharePoint Server 2016 に含まれていることに注意してください。 詳細については、「 [Deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829)」を参照してください。
    
- Project Server 2016 では、リソース計画は廃止されました。 Project Server 2013 のリソース計画は、project Server 2016 および Project Online のリソース予約に移行されます。 詳細については、「[概要: リソース予約](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870)」を参照してください。 
    
### <a name="step-3-migrate-to-project-server-2019"></a>手順 3: Project Server 2019 に移行する

Project Server 2016 に移行し、データが正常に移行されたことを確認した後、次の手順では、データを Project Server 2019 に移行します。
  
Project Server 2016 から Project Server 2019 にアップグレードするために必要な作業を完全に理解するには、「 [upgrade To Project server 2019](https://docs.microsoft.com/Project/upgrade-to-project-server-2016)」を参照してください。
  
主なリソース:
  
|||
|:-----|:-----|
|[Project Server 2019 のアップグレードプロセスの概要](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |Project Server 2013 から Project Server 2016 にアップグレードするために必要な作業についての高度な理解を得ることができます。  <br/> |
|[Project Server 2019 へのアップグレードを計画する](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |Project Server 2016 から Project Server 2019 にアップグレードするときに必要な計画の考慮事項について確認します。  <br/> |
   
[Project Server 2019 アップグレードに関して知っておく必要のある](https://go.microsoft.com/fwlink/p/?linkid=841827)ことは、このバージョンへのアップグレードに関する重要な変更点を示しています。これには次のようなものがあります。 
  
- アップグレードプロセスによって、Project Server 2016 データベースから SharePoint Server 2019 コンテンツデータベースにデータが移行されます。  Project Server 2019 は、SharePoint Server ファームに独自の Project Server データベースを作成しなくなります。

- アップグレード後に、Project Web App のいくつかの変更に注意してください。  これらの詳細については、「 [Project Server 2019 の新機能](https://docs.microsoft.com/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges)」を参照してください。

  
その他の技術情報:
  
- [Project Online サービスの説明](https://go.microsoft.com/fwlink/p/?linkid=841280): project Server 2016 および Project Online Premium に含まれているポートフォリオ管理機能を参照してください。
    
- [Microsoft Office Project ポートフォリオサーバー2010移行ガイド](https://go.microsoft.com/fwlink/p/?linkid=841279)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Office 2010 のクライアントおよびサーバーおよび Windows 7 のオプションの概要

Office 2010 のクライアントおよびサーバーおよび Windows 7 のアップグレード、移行、およびクラウドの移行オプションの視覚的な概要については、「[サポートの終了」ポスター](./media/upgrade-from-office-2010-servers-and-products/Office2010Windows7EndOfSupport.pdf)を参照してください。

[![Office 2010 クライアントおよびサーバー サポート終了についての画像、 Windows 7 のポスター](./media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](./media/upgrade-from-office-2010-servers-and-products/Office2010Windows7EndOfSupport.pdf)

この1ページのポスターは、Office 2010 のクライアントおよびサーバー製品と Windows 7 のサポートが終了しないようにするために実行できるさまざまなパスを簡単に理解する方法です。 Microsoft 365 Enterprise では、優先パスとオプションのサポートが強調表示されています。

このポスターを[ダウンロード](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/migration-microsoft-365-enterprise-workload/Office2010Windows7EndOfSupport.pdf)して、レター、リーガル、またはタブロイド (11 x 17) 形式で印刷することもできます。
   
## <a name="related-topics"></a>関連項目

[SharePoint 2010 からアップグレードする](upgrade-from-sharepoint-2010.md)
  
[Office 2010 サーバー/クライアントからアップグレードする](upgrade-from-office-2010-servers-and-products.md)
  

