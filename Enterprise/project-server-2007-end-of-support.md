---
title: Project Server 2007 のサポート終了ロードマップ
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 1/31/2018
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
ms.assetid: d379018f-72b7-4284-b40a-6c23c8ae38fe
description: 2017 年 10 月 10日には、Project Server 2007、プロジェクト ポートフォリオ サーバー、および Project 2007 のサポートが終了しました。この資料を使用して、アップグレードを計画するようになりました。
ms.openlocfilehash: 5b2fb194d4819b5427cb2844a5189b2b03753800
ms.sourcegitcommit: a9c84d02e94c99ff6b1099b4a9ae695be08210e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "21169899"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Project Server 2007 のサポート終了ロードマップ

2017、Office 2007 サーバーおよびアプリケーションのサポートが終了し、移行の計画を検討する必要があります。Project Server 2007 を現在使用している場合、次のサポートの終了の日付、およびその他の関連製品を持つことに注意してください。
  
|**製品**|**サポート日の終わり**|
|:-----|:-----|
|Project Server 2007  <br/> |2017 年 10 月 10 日  <br/> |
|プロジェクト ポートフォリオ Server 2007  <br/> |2017 年 10 月 10 日  <br/> |
|プロジェクト 2007年の標準  <br/> |2017 年 10 月 10 日  <br/> |
|Project 2007 Professional  <br/> |2017 年 10 月 10 日  <br/> |
   
退職後に到達する Office 2007 サーバーの詳細については、 [Office 2007 のサーバーおよびクライアント製品からのアップグレード](upgrade-from-office-2007-servers-and-products.md)を参照してください。
  
## <a name="what-does-end-of-support-mean"></a>サポートの平均の最後は何でしょうか。

ほとんどすべてのマイクロソフト製品と同様に、project Server によって提供の新機能、バグ修正、セキュリティ修正プログラムなどのサポート ライフ サイクルがあります。このライフ サイクルは、通常製品の初期リリースの日付から 10 年間持続し、このライフ サイクルの最後は、製品のサポート終了と呼ばれます。。Project Server 2007 がサポートは 2017 年 10 月 10日、上の最後に達したためマイクロソフトは提供されなくなります。
  
- 発生する問題についてテクニカル サポートします。
    
- バグは修正で問題が検出され、安定性と、サーバーの可用性に影響を及ぼす可能性があります。
    
- セキュリティでは、脆弱性が発見されると、セキュリティ侵害に対して脆弱なサーバーを構成することがありますが修正されます。
    
- タイム ゾーンを更新します。
    
Project Server 2007 のインストールに対しては、この日付より後に実行され続けます。ただし、変更のため、上の一覧に、強くお勧め、できるだけ早くに Project Server 2007 から移行することです。
  
## <a name="what-are-my-options"></a>オプションを挙げてください。

Project Server 2007 を使用する場合は、移行オプションを検索する必要があります。
  
- プロジェクトをオンラインに移行します。
    
- Project Server (可能であればプロジェクト サーバー 2016) の新しい設置型バージョンに移行します。
    
|**プロジェクトをオンラインに移行する方がなぜ**|**プロジェクト サーバー 2016 に移行する方がなぜ**|
|:-----|:-----|
| モバイル ユーザーがあるとします。  <br/>  移行するためのコストは、(ハードウェア、ソフトウェア、時間などを実装するための努力) 大きな問題です。  <br/>  移行後は、自分の環境を維持するためのコストは、大きな問題になる (たとえば、自動更新、稼働時間などを保証します。) をします。  <br/> | ビジネス ルールでは、クラウドでビジネスを運用することから私を制限します。  <br/>  自分の環境に更新プログラムの制御が必要です。  <br/> |
   
> [!NOTE]
> Office 2007 サーバーから移動するためのオプションの詳細については、 [2007 のサーバーとクライアントの Office からアップグレードするためのリソース](upgrade-from-office-2007-servers-and-products.md)を参照してください。Project Server は Project Server からのハイブリッド構成をサポートしていませんし、オンライン プロジェクトは、同じリソース共有元を共有できないことに注意してください。 
  
## <a name="important-considerations-you-need-to-make-when-planning-to-migrate-from-project-server-2007"></a>重要な考慮事項が Project Server 2007 からの移行を計画するときに作成する必要があります。

Project Server 2007 からの移行を計画するとき、次を考慮する必要があります。
  
- **マイクロソフトのパートナーからのヘルプを表示する**に Project Server 2007 からアップグレードすることは容易でおよび多くの準備と計画が必要です。セットアップし、最初に Project Server 2007 を構成するにはなかった場合は特に困難にできます。幸運はマイクロソフトのパートナー企業を見ていくことを作成している、これを行うサーバー 2016 のプロジェクトまたはプロジェクトをオンラインに移行する方法を計画するかどうか。[マイクロソフト ・ パートナー ・ センター](https://go.microsoft.com/fwlink/p/?linkid=841249)の移行を支援するマイクロソフトのパートナーを検索することができます。*ゴールド プロジェクトとポートフォリオの管理*、用語を検索することにより、プロジェクト内の専門知識を持つすべてのマイクロソフト パートナーの一覧をプルできます。 
    
- **独自の計画**を、カスタマイズした Project Server 2007 環境内での多くが動作しないことサーバー 2016 のプロジェクトまたはプロジェクトをオンラインに移行するときに注意してください。バージョンと同様に、必要なオペレーティング システム、データベース サーバー、およびより新しいバージョンで動作するサポートされているクライアントの web ブラウザー間で Project Server のアーキテクチャが大きく異なるがあります。配置をテストするか、新しい環境で必要に応じて、カスタマイズを再構築する方法の計画があります。アップグレードの計画と、前方に移動すると、特定のカスタマイズが本当に必要なかどうかを確認するよい機会もできます。いくつか優れた全般についての評価とプランニング、現在のカスタマイズをアップグレードする場合に[SharePoint 2013 へのアップグレード中に現在のカスタマイズの計画を作成](https://go.microsoft.com/fwlink/p/?linkid=842061)します。 
    
- **時間と忍耐力**のアップグレード計画、実行、およびテストになります多くの時間と労力、サーバー 2016 のプロジェクトをアップグレードする場合は特に。たとえば、サーバー 2016 のプロジェクトを Project Server 2007 から移行する場合最初に Project Server 2010 では、Project Server 2007 に移行し、データを確認する必要があります、バージョンごとに移行する場合に同じ操作を行います。どのくらいの時間がかかります、それを実行できるよう、どのようなコストの見積もりをコストを比較するマイクロソフトのパートナーに確認する可能性があります。 
    
## <a name="migrate-to-project-online"></a>プロジェクトをオンラインに移行します。

Project Server 2007 からプロジェクトをオンラインに移行する場合は、手動でデータを移行、プロジェクト計画には、次を行うことができます。
  
1. Project Server 2003 からプロジェクト計画を保存します。MPP 形式です。
    
2. プロジェクト評価のためのプロフェッショナル 2016 のプロジェクト、またはプロジェクトのオンライン デスクトップ クライアントを使用すると、それぞれの .mpp ファイルを開くと保存してプロジェクトをオンラインに公開します。
    
プロジェクトをオンラインで、PWA の構成を手動で作成することができます (すべての必要なユーザー設定フィールドまたはエンタープライズ カレンダーを再作成など)。マイクロソフトのパートナーこともできますこれをします。
  
主要リソース:
  
|**リソース**|**説明**|
|:-----|:-----|
|[オンライン プロジェクトを開始します。](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |セットアップし、オンライン プロジェクトを使用する方法です。  <br/> |
|[プロジェクトのオンライン サービスの説明](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |使用可能なさまざまなオンライン プロジェクト プランに関する情報です。  <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>新しい設置型バージョンの Project Server への移行します。

プロジェクトをオンラインに移行することで最高の値とユーザー エクスペリエンスを実現できることを強く信じ、中に一部の組織がオンプレミス環境でプロジェクトのデータを保持する必要があることをも理解します。プロジェクト データの設置型を保持する場合は、Project Server 2010、Project Server 2013 では、プロジェクトのサーバーの 2016 を Project Server 2007 環境を移行できます。
  
プロジェクトをオンラインに移行できない場合は、プロジェクト サーバー 2016 に移行することをお勧めします。Project Server 2016 には、すべての機能と Project Server の以前のリリースに含まれている機能が含まれています、それに最も近い経験のプロジェクトをオンラインで利用可能な (ただし、一部の機能は、プロジェクトをオンラインでのみ使用可能)。
  
各移行を完了するは、正常に移行ができるかどうかを確認するのには、データを参照してください。
  
> [!NOTE]
> オンプレミスのソリューションに制限する場合は、Project Server 2010 にのみ移行を検討している場合にだけ、さらに数年の残りのサポートを持っている注意してください。プロジェクトのサポートの日の最後は、Service Pack 2 でのサーバー 2010年 2020/10/13 です。サポート終了日の詳細については、[マイクロソフト製品のライフ サイクル ポリシー](https://go.microsoft.com/fwlink/p/?linkid=842066)を参照してください。 
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>サーバー 2016 のプロジェクトを移行する方法は?

Project Server 2007 とプロジェクトのサーバー 2016 のアーキテクチャの相違点は、直接移行パスを防止します。つまりサーバー 2016 のプロジェクトをアップグレードするまで、プロジェクトのサーバーの次の連続するバージョンを Project Server 2007 データを移行する必要があります。
  
サーバー 2016 のプロジェクトをアップグレードするのには次の操作が必要になります。
  
1. 手順 1: は、プロジェクトの Server 2010 には、Project Server 2007 から移行します。
    
2. 手順 2: は、Project Server 2013 には、プロジェクト サーバー 2010 から移行します。
    
3. 手順 3: は、サーバー 2016年のプロジェクトを Project Server 2013 から移行します。
    
各移行を完了するは、正常に移行ができるかどうかを確認するのには、データを参照してください。
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>Server 2010 のプロジェクトを Project Server 2007 からのステップ 1: 移行します。

Project Server 2007 から Project Server 2010 にアップグレードするために必要なものの包括的なを理解するには、TechNet のコンテンツ セットの[Project Server 2010 へのアップグレード](https://go.microsoft.com/fwlink/p/?linkid=841812)を参照してください。 
  
主要リソース:
  
|**リソース**|**説明**|
|:-----|:-----|
|[プロジェクト サーバー 2010 のアップグレードの概要です。](https://go.microsoft.com/fwlink/p/?linkid=841813) <br/> |Project Server 2007 から Project Server 2010 にアップグレードする必要のある高度な知識を取得します。  <br/> |
|[プロジェクトの Server 2010 へのアップグレードを計画します。](https://go.microsoft.com/fwlink/p/?linkid=841815) <br/> |計画が必要なシステム要件を含む、Project Server 2010 に Project Server 2007 からアップグレードする際の考慮事項を確認します。  <br/> |
   
#### <a name="how-do-i-upgrade"></a>アップグレードする方法ですか。

アップグレードする方法の詳細については、 [Project Server 2010 へのアップグレード](https://go.microsoft.com/fwlink/p/?linkid=841812)のコンテンツ セットを参照して、アップグレードを使用することができます 2 つの異なる方法があることを理解する必要が。 
  
- **データベース接続アップグレード:** このメソッドは、お客様の環境および構成の設定ではなくコンテンツのみをアップグレードします。32 ビット版サーバー オペレーティング システムのみをサポートするハードウェアに展開された、Office Project Server 2007 からアップグレードする場合は不要です。2 つの種類のデータベース接続アップグレードの方法。 
    
  - **データベース接続のフル ・ アップグレード**には、Office Project Server 2007 データベースに格納されているプロジェクトのデータと、SharePoint のコンテンツ データベースに格納されている Microsoft Project Web App (PWA) サイトのデータを移行します。 
    
  - **データベース接続コア アップグレード**では、Project Server データベースに格納されているプロジェクト データのみを移行します。 
    
- **インプレース アップグレード**: ファームとファーム上のすべてのコンテンツの構成データを一定の順序で、既存のハードウェアにアップグレードします。インプレース アップグレード プロセスを開始してセットアップは、ファーム全体をオフラインと Web サイトは、Microsoft Project Web App サイトはアップグレードが完了し、サーバーが再起動し、までご利用いただけません。インプレース アップグレードを開始した後は、アップグレードを一時停止または以前のバージョンにロールバックできません。運用環境のミラー イメージを作成して、このような環境を運用環境ではなく、インプレース アップグレードを実行するを強くお勧めします。 
    
その他のリソース:
  
- [Microsoft Project Server 2010 のアップグレードのための superFlow](https://go.microsoft.com/fwlink/p/?linkid=841277)
    
- [Server 2010 のプロジェクトを Project Server 2007 からの移行](https://go.microsoft.com/fwlink/p/?linkid=841278)
    
- [プロジェクト Web App Web パーツのアップグレードに関する考慮事項](https://go.microsoft.com/fwlink/p/?linkid=841276)
    
- [プロジェクトのソフトウェア開発キット (SDK)](https://go.microsoft.com/fwlink/p/?linkid=841275)
    
### <a name="step-2-migrate-to-project-server-2013"></a>ステップ 2: 移行を Project Server 2013

Project Server 2010 に移行すると、データの移行が正常に検証する、次の手順は、データを Project Server 2013 に移行します。
  
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
    
### <a name="step-3-migrate-to-project-server-2016"></a>手順 3: 移行プロジェクトのサーバー 2016

Project Server 2013 に移行して、データの移行が正常に検証を行った後は、サーバー 2016 のプロジェクトにデータを移行します。
  
サーバー 2016 のプロジェクトを Project Server 2013 にアップグレードするために必要なものの包括的なを理解するには、TechNet の設定プロジェクト サーバー 2016 のコンテンツへのアップグレードを参照してください。
  
主要リソース:
  
|**リソース**|**説明**|
|:-----|:-----|
|[Project Server 2016 のアップグレード プロセスの概要](https://go.microsoft.com/fwlink/p/?linkid=841260) <br/> |サーバー 2016 のプロジェクトを Project Server 2013 にアップグレードする必要のある高度な知識を取得します。  <br/> |
|[Project Server 2016 へのアップグレードを計画する](https://go.microsoft.com/fwlink/p/?linkid=841826) <br/> |Project server を含め、2016 から Project Server 2013 にアップグレードするときのために必要な考慮事項を計画することを確認します。  <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>このバージョンへのアップグレードに関する重要なポイント

[プロジェクト サーバー 2016 を知っておく必要がありますアップグレード](https://go.microsoft.com/fwlink/p/?linkid=841827)と、いくつかの重要な変更のこのバージョンでは、アップグレードなどを指示します。 
  
- Project Server 2013 のデータを移行する、プロジェクトのサーバー 2016 環境を作成するときは、SharePoint サーバーの 2016年のプロジェクト サーバー 2016 のインストール ファイルが含まれている注意してください。詳細については、[プロジェクト サーバー 2016 の展開](https://go.microsoft.com/fwlink/p/?linkid=841829)を参照してください。
    
- リソース計画は、プロジェクトのサーバー 2016 で推奨されていません。Project Server 2013 リソース計画は、プロジェクト サーバー 2016 とオンライン プロジェクトでリソースの導入に移行されます。参照してください[の概要: リソース契約](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870)の詳細について。 
    
## <a name="migrate-from-portfolio-server-2007"></a>ポートフォリオ Server 2007 からの移行します。

プロジェクト ポートフォリオ Server 2007 は、ポートフォリオ戦略、優先順位付け、および最適化の Project Server 2007 で使用されました。このバージョンにプロジェクトのポートフォリオ Server の他のバージョンは作成されませんでした。ただし、ポートフォリオ管理機能は、プロジェクト サーバー 2016 とプレミアム バージョンの両方のプロジェクトをオンラインで利用できます。いずれかの方法には、プロジェクト ポートフォリオ Server 2007 からデータを移行できません。ビジネスの推進要因などのデータは、再作成する必要があります。
  
その他のリソース:
  
- [プロジェクトのオンライン サービスの説明](https://go.microsoft.com/fwlink/p/?linkid=841280): サーバー 2016 のプロジェクトとプロジェクトのオンラインのプレミアムに含まれているポートフォリオ管理機能を参照してください。
    
- [Microsoft Office プロジェクトのポートフォリオ Server 2007 の移行ガイド](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>関連項目

[サポート ロードマップの SharePoint Server 2007 の終了](sharepoint-2007-end-of-support.md)
  
[2007 のサーバーとクライアントの Office からアップグレードするためのリソース](upgrade-from-office-2007-servers-and-products.md)
  

