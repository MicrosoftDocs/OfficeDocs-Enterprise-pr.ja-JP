---
title: プロジェクトのサーバー 2010年の最後のサポートのロードマップ
ms.author: efrene
author: efrene
manager: pamg
ms.date: 10/12/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
description: 2020 年 10 月 13日に、Project Server 2010 のサポートが終了します。この資料を使用して、アップグレードを計画するようになりました。
ms.openlocfilehash: bdfc4dd81dca7fe137be5780e54252eba961910f
ms.sourcegitcommit: e89b5306338ecdb40ad88efcf9cae3b8d5692924
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/13/2018
ms.locfileid: "25549787"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>サポート ロードマップのプロジェクト Server 2010 の終了

2010 では、Office 2010 のサーバーおよびアプリケーションのサポートが終了し、移行の計画を検討する必要があります。Project Server 2010 を現在使用している場合は、それと関連するその他のこれらの製品が、次のサポート終了日を持つことに注意してください。
  
|**Product**|**サポート日の終わり**|
|:-----|:-----|
|Project Server 2010  <br/> |2020 年 10 月 13日  <br/> |
|プロジェクト ポートフォリオ Server 2010  <br/> |2020 年 10 月 13日  <br/> |
|プロジェクト 2010年の標準  <br/> |2020 年 10 月 13日  <br/> |
|プロジェクト 2010年プロフェッショナル  <br/> |2020 年 10 月 13日  <br/> |
   
退職後に到達する Office 2010 サーバーの詳細については、 [Office 2010 のサーバーとクライアントの製品からのアップグレード](https://docs.microsoft.com/office365/enterprise/plan-upgrade-previous-versions-office)を参照してください。
  
## <a name="what-does-end-of-support-mean"></a>サポートが終了するとどうなるのか

ほとんどすべてのマイクロソフト製品と同様に、project Server によって提供の新機能、バグ修正、セキュリティ修正プログラムなどのサポート ライフ サイクルがあります。このライフ サイクルは、通常製品の初期リリースの日付から 10 年間持続し、このライフ サイクルの最後は、製品のサポート終了と呼ばれます。。Project Server 2010 のサポートは 2020 年 10 月 10日には、上の最後に達すると、マイクロソフトは提供されなくなります。
  
- 発生する問題についてテクニカル サポートします。
    
- バグは修正で問題が検出され、安定性と、サーバーの可用性に影響を及ぼす可能性があります。
    
- セキュリティでは、脆弱性が発見されると、セキュリティ侵害に対して脆弱なサーバーを構成することがありますが修正されます。
    
- タイム ゾーンの更新。
    
Project Server 2010 のインストールに対しては、この日付より後に実行され続けます。ただし、変更のため、上の一覧に、強くお勧め、できるだけ早くに Project Server 2010 から移行することです。
  
## <a name="what-are-my-options"></a>使用できるオプション

Project Server 2010 を使用する場合は、移行オプションを検索する必要があります。
  
- プロジェクトをオンラインに移行します。
    
- Project Server (可能であればプロジェクト サーバー 2019) の新しい設置型バージョンに移行します。
    
|**プロジェクトをオンラインに移行する方がなぜ**|**プロジェクト サーバー 2019 に移行する方がなぜ**|
|:-----|:-----|
| モバイル ユーザーがあるとします。  <br/>  移行するためのコストは、(ハードウェア、ソフトウェア、時間などを実装するための努力) 大きな問題です。  <br/>  移行後は、自分の環境を維持するためのコストは、大きな問題になる (たとえば、自動更新、稼働時間などを保証します。) をします。  <br/> | ビジネス ルールでは、クラウドでビジネスを運用することから私を制限します。  <br/>  自分の環境に更新プログラムの制御が必要です。  <br/> |
   
> [!NOTE]
> Office 2010 のサーバーから移動するためのオプションの詳細については、 [2010 のサーバーとクライアントの Office からアップグレードするためのリソース](https://docs.microsoft.com/office365/enterprise/upgrade-from-office-2010-servers-and-products)を参照してください。Project Server は Project Server からのハイブリッド構成をサポートしていませんし、オンライン プロジェクトは、同じリソース共有元を共有できないことに注意してください。 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2010"></a>重要な考慮事項が Project Server 2010 の移行を計画する際に確認する必要があります。

Project Server 2010 に移行する計画する場合は、次を考慮する必要があります。
  
- チャレンジは、**マイクロソフトのパートナーからのヘルプを表示する**に Project Server 2010 からアップグレードする計画と多くの準備が必要です。セットアップし、最初に Project Server 2010 を構成しない場合は特に困難にできます。幸運はマイクロソフトのパートナー企業を見ていくことを作成している、これを行うサーバー 2019 のプロジェクトまたはプロジェクトをオンラインに移行する方法を計画するかどうか。[マイクロソフト ・ パートナー ・ センター](https://go.microsoft.com/fwlink/p/?linkid=841249)の移行を支援するマイクロソフトのパートナーを検索することができます。*ゴールド プロジェクトとポートフォリオの管理*、用語を検索することにより、プロジェクト内の専門知識を持つすべてのマイクロソフト パートナーの一覧をプルできます。 
    
- **独自の計画**を、カスタマイズした Project Server 2010 環境での多くが動作しないことサーバー 2019 のプロジェクトまたはプロジェクトをオンラインに移行するときに注意してください。バージョンと同様に、必要なオペレーティング システム、データベース サーバー、およびより新しいバージョンで動作するサポートされているクライアントの web ブラウザー間で Project Server のアーキテクチャが大きく異なるがあります。配置をテストするか、新しい環境で必要に応じて、カスタマイズを再構築する方法の計画があります。アップグレードの計画と、前方に移動すると、特定のカスタマイズが本当に必要なかどうかを確認するよい機会もできます。いくつか優れた全般についての評価とプランニング、現在のカスタマイズをアップグレードする場合に[SharePoint 2013 へのアップグレード中に現在のカスタマイズの計画を作成](https://go.microsoft.com/fwlink/p/?linkid=842061)します。 
    
- **時間と忍耐力**のアップグレード計画、実行、およびテストになります時間と残存作業時間、プロジェクトのサーバー 2019 にアップグレードする場合に特に。などサーバー 2019 のプロジェクトを Project Server 2010 から移行する場合は、Project Server 2013 では、Project Server 2010 から移行し、データを確認し、まず必要がありますしてバージョンごと (プロジェクトを移行するときに同じ処理を行う2016 をサーバーとし、Project Server 2019)。マイクロソフトのパートナーがどのくらいの時間がかかります、それを実行できるよう、どのようなコストの見積もりを見積もり、コストを比較すると確認することがあります。 
    
## <a name="migrate-to-project-online"></a>プロジェクトをオンラインに移行します。

オンライン プロジェクトを Project Server 2010 から移行する場合は、手動でデータを移行、プロジェクト計画には、次を行うことができます。
  
1. Project Server 2010 から、プロジェクト計画を保存します。MPP 形式です。
    
2. プロジェクト プロフェッショナル 2016、プロジェクト担当者 2019、またはプロジェクトのオンライン デスクトップ クライアントを使用すると、それぞれの .mpp ファイルを開くと保存してプロジェクトをオンラインに公開します。
    
プロジェクトをオンラインで、PWA の構成を手動で作成することができます (すべての必要なユーザー設定フィールドまたはエンタープライズ カレンダーを再作成など)。マイクロソフトのパートナーこともできますこれをします。
  
主要リソース:
  
|**リソース**|**説明**|
|:-----|:-----|
|[オンライン プロジェクトを開始します。](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |セットアップし、オンライン プロジェクトを使用する方法です。  <br/> |
|[プロジェクトのオンライン サービスの説明](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |使用可能なさまざまなオンライン プロジェクト プランに関する情報です。  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>新しい設置型バージョンの Project Server への移行します。

プロジェクトをオンラインに移行することで最高の値とユーザー エクスペリエンスを実現できることを強く信じ、中に一部の組織がオンプレミス環境でプロジェクトのデータを保持する必要があることをも理解します。プロジェクト データの設置型を保持する場合は、Project Server 2013、サーバー 2016 のプロジェクト、またはプロジェクト サーバー 2019、Project Server 2010 環境を移行できます。
  
プロジェクトをオンラインに移行できない場合は、プロジェクト サーバー 2019 に移行することをお勧めします。2019 の project Server には、Project Server の以前のリリースに含まれているの進歩により、機能キーのほとんどが含まれ、それに最も近い経験のプロジェクトをオンラインで利用可能な (ただし、一部の機能は、プロジェクトをオンラインでのみ使用可能)。
  
各移行を完了するは、正常に移行ができるかどうかを確認するのには、データを参照してください。
  
> [!NOTE]
> のみに移行する Project Server 2013 の場合は、オンプレミスのソリューションは、考慮する場合にのみ、さらに数年の残りのサポートを持っている注意してください。サポート日の最後は、Service Pack 2 を Project Server 2013 10/13/2023。サポート終了日の詳細については、[マイクロソフト製品のライフ サイクル ポリシー](https://go.microsoft.com/fwlink/p/?linkid=842066)を参照してください。 
  
### <a name="how-do-i-migrate-to-project-server-2019"></a>プロジェクト サーバー 2019 に移行する方法は?

Project Server 2010 とプロジェクトのサーバー 2019 のアーキテクチャの違いは、直接移行パスを防止します。つまりサーバー 2019 のプロジェクトをアップグレードするまで、プロジェクトのサーバーの次の連続するバージョンを Project Server 2010 データを移行する必要があります。
  
サーバー 2019 のプロジェクトをアップグレードするのには次の操作が必要になります。
  
1. 手順 1: は、Project Server 2013 に Project Server 2010 からのデータを移行します。
    
2. 手順 2: プロジェクト サーバー 2016 をプロジェクト提供 2013 からデータを移行します。
    
3. 手順 3: サーバー 2019 のプロジェクトにプロジェクト サーバー 2016 からデータを移行します。
    
各移行を完了するは、正常に移行ができるかどうかを確認するのには、データを参照してください。
  
    
### <a name="step-1-migrate-to-project-server-2013"></a>手順 1: Project Server 2013 に移行します。

プロジェクト サーバー 2019 に、Project Server 2010 のデータを移行する最初の手順では、最初に Project Server 2013 に移行します。 
  
Project Server 2013 を Project Server 2010 にアップグレードするために必要なものの包括的なを理解するには、TechNet のコンテンツ セットの[Project Server 2013 へのアップグレード](https://go.microsoft.com/fwlink/p/?linkid=841822)を参照してください。 
  
主要リソース:
  
|**リソース**|**説明**|
|:-----|:-----|
|[Project Server 2013 のアップグレード プロセスの概要](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Project Server 2013 を Project Server 2010 にアップグレードする必要のある高度な知識を取得します。  <br/> |
|[Project Server 2013 にアップグレードしようとしてください。](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |計画が必要なシステム要件を含む、Project Server 2013 に Project Server 2010 からアップグレードする際の考慮事項を確認します。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>このバージョンへのアップグレードに関する重要なポイント

[Project Server 2013 のアップグレードの新機能](https://go.microsoft.com/fwlink/p/?linkid=841824)と、最も注目すべきが、このバージョンのアップグレードのためのいくつかの重要な変更を指示します。 
  
- Project Server 2013 に、インプレース アップグレードはありません。データベースのアタッチ メソッドは、Project Server 2010 から Project Server 2013 へのアップグレードの方法のみがサポートされます。
    
- アップグレード プロセスはのみ、Project Server 2010 のデータは Project Server 2013 の形式に変換されませんも 1 つの Project Web App データベースに 4 つの Project Server 2010 データベースを統合して。
    
- SharePoint Server 2013 と Project Server 2013 の両方が以前のバージョンからクレーム ベース認証に変更します。クラシック認証を使用している場合のアップグレード時の考慮事項を確認する必要があります。詳細については、 [SharePoint 2013 でクレーム ベース認証をクラシック モードからの移行](https://go.microsoft.com/fwlink/p/?linkid=841825)を参照してください。
    
その他のリソース:
  
- [Project Server 2013 へのアップグレード プロセスの概要](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [データベースおよび Project Web App サイト コレクションをアップグレードする (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Microsoft Project Server のアップグレードのプロセス図](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [データベースの統合、8 つの簡単な手順でプロジェクトの Server 2010 から 2013 に移行](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-2-migrate-to-project-server-2016"></a>サーバー 2016年をプロジェクトに手順 2 に移行します。

Project Server 2013 に移行して、データの移行が正常に検証を行った後は、サーバー 2016 のプロジェクトにデータを移行します。
  
サーバー 2016 のプロジェクトを Project Server 2013 にアップグレードする必要がある包括的な知識、[プロジェクトのサーバー 2016 へのアップグレード](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016)のコンテンツ セットを参照してください。
  
主要リソース:
  
|**リソース**|**説明**|
|:-----|:-----|
|[Project Server 2016 のアップグレード プロセスの概要](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process) <br/> |サーバー 2016 のプロジェクトを Project Server 2013 にアップグレードする必要のある高度な知識を取得します。  <br/> |
|[Project Server 2016 へのアップグレードを計画する](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016) <br/> |サーバー 2016 のプロジェクトを Project Server 2013 からアップグレードする場合のために必要な計画の考慮事項を確認します。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>このバージョンへのアップグレードに関する重要なポイント

[プロジェクト サーバー 2016 を知っておく必要がありますアップグレード](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow)と、いくつかの重要な変更のこのバージョンでは、アップグレードなどを指示します。 
  
- Project Server 2013 のデータを移行する、プロジェクトのサーバー 2016 環境を作成するときは、SharePoint サーバーの 2016年のプロジェクト サーバー 2016 のインストール ファイルが含まれている注意してください。詳細については、[プロジェクト サーバー 2016 の展開](https://go.microsoft.com/fwlink/p/?linkid=841829)を参照してください。
    
- リソース計画は、プロジェクトのサーバー 2016 で推奨されていません。Project Server 2013 リソース計画は、プロジェクト サーバー 2016 とオンライン プロジェクトでリソースの導入に移行されます。参照してください[の概要: リソース契約](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870)の詳細について。 
    
### <a name="step-3-migrate-to-project-server-2019"></a>手順 3 に移行プロジェクトのサーバー 2019

サーバー 2016 のプロジェクトに移行すると、データの移行が正常に検証する、次に、サーバー 2019 のプロジェクトにデータを移行します。
  
サーバー 2016 のプロジェクトからプロジェクト サーバー 2019 にアップグレードを行う必要がある包括的な知識、[プロジェクトのサーバー 2019 へのアップグレード](https://docs.microsoft.com/en-us/Project/upgrade-to-project-server-2016)のコンテンツ セットを参照してください。
  
主要リソース:
  
|**リソース**|**説明**|
|:-----|:-----|
|[アップグレード プロセスのプロジェクトのサーバー 2019 の概要](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process) <br/> |サーバー 2016 のプロジェクトを Project Server 2013 にアップグレードする必要のある高度な知識を取得します。  <br/> |
|[サーバー 2019 のプロジェクトへのアップグレードの計画](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019) <br/> |サーバー 2016 のプロジェクトからプロジェクト サーバー 2019 にアップグレードするときのために必要な計画の考慮事項を確認します。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>このバージョンへのアップグレードに関する重要なポイント

[プロジェクト サーバー 2019 について知っておく必要がありますアップグレード](https://go.microsoft.com/fwlink/p/?linkid=841827)と、いくつかの重要な変更のこのバージョンでは、アップグレードなどを指示します。 
  
- SharePoint サーバー 2019年のコンテンツ データベースに、プロジェクトのサーバー 2016 データベースから、アップグレード プロセスは、データを移行します。 Project Server 2019 は作成されなくなった SharePoint サーバー ファーム内の Project Server データベースを所有しています。

- アップグレード後には、Project Web App でいくつかの変更を認識します。 、これらの説明は[の新プロジェクト サーバー 2019](https://docs.microsoft.com/en-us/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges)」を参照してください。


## <a name="migrate-from-portfolio-server-2010"></a>ポートフォリオ Server 2010 から移行します。

プロジェクト ポートフォリオ Server 2010 は、ポートフォリオ戦略、優先順位付け、および最適化の Project Server 2010 で使用されました。このバージョンにプロジェクトのポートフォリオ Server の他のバージョンは作成されませんでした。ただし、ポートフォリオ管理機能は、Project Server のそれ以降のバージョンとプロジェクトのオンラインのプレミアム バージョンで利用できます。いずれかの方法には、プロジェクトのポートフォリオ Server 2010 からのデータを移行できません。ビジネスの推進要因などのデータは、再作成する必要があります。
  
その他のリソース:
  
- [プロジェクトのオンライン サービスの説明](https://go.microsoft.com/fwlink/p/?linkid=841280): サーバー 2016 のプロジェクトとプロジェクトのオンラインのプレミアムに含まれているポートフォリオ管理機能を参照してください。
    
- [Microsoft Office プロジェクトのポートフォリオ Server 2010 移行ガイド](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>関連項目

[SharePoint 2010 からアップグレードします。](upgrade-from-sharepoint-2010.md)
  
[2010 のサーバーとクライアントの Office からアップグレードするためのリソース](upgrade-from-office-2010-servers-and-products.md)
  

