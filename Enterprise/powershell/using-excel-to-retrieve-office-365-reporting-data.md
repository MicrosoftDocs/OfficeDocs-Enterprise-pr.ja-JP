---
title: "Excel を使用して Office 365 レポート データを取得する"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other, PowerShell
ms.assetid: 510d5528-ac00-4f54-9d38-75fa043d0a06
description: "概要: Microsoft Excel の OData 機能を使用して、Office 365 の展開に関する詳しいレポート情報を取得します。"
ms.openlocfilehash: 4347aad28e1e197c03eb986663ef7e59849493d1
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="using-excel-to-retrieve-office-365-reporting-data"></a>Excel を使用して Office 365 レポート データを取得する

 **概要:** Microsoft Excel の OData 機能を使用して、Office 365 の展開に関する詳しいレポート情報を取得します。
  
レポートは、システム管理の主要な部分です。Office 365 管理センターには、複数の定義済みのレポートが含まれており、左側のナビゲーションの**レポート** セクションからアクセスできます。利用状況レポートと、セキュリティとコンプライアンスのレポートがあります。
  
入手可能なレポートは、使用している Office 365 のバージョンや有効になっている Office 365 サービスによって異なります。詳細については、「[レポート ページ](https://technet.microsoft.com/ja-JP/library/office-365-reports.aspx)」を参照してください。
  
定義済みの管理センターのレポートは優れたリソースです。これらはメールボックスの利用状況や、ユーザーがオンライン会議に費やした時間 (分単位) などを簡単に確認できるようにします。ただし、Office 365 ドメインの詳細な分析に関して言えば、このレポートには制限があります。
  
これらの制限を回避する 1 つの方法は、Windows PowerShell または他の開発言語を使用して Office 365 レポート サービスにアクセスし、カスタム レポートを作成することです。カスタム レポートでは、Office 365 レポート サービスから返されるデータの種類 (およびその量) を決められます。カスタム レポートを作成すれば、データをソートおよびグループ化する方法を指定し、該当する場合は、データを保存する方法も指定することもできます。たとえば、データは XML 形式または Excel に簡単にインポートできるコンマ区切り形式で保存できます。 
  
さらに、カスタム スクリプト/アプリケーションを使用して、Office 365 管理センターでは入手できないレポートにアクセスすることができます。たとえば、管理センターは、ユーザーが所有する古いメールボックスの数を表示できますが、過去 30 日間にアクセスされなかったメールボックスを表示することはできません。カスタム PowerShell スクリプトを使用すれば、これを表示することができます。まとめるなら、短く簡単な Windows PowerShell スクリプトを作成する必要があるものの、柔軟性が大幅に広がるということになります。
  
> [!VISUAL BASIC NOTE] 詳細については、Office 365 レポート サービスの「[ホーム ページ](https://msdn.microsoft.com/ja-JP/library/office/jj984325%28v=office.15%29.aspx)」を参照してください。
  
このデータを取得するには、何らかのコードを作成する必要があります。組織が大規模であり、返される情報の量や種類を制限する必要がある場合は、これを行う価値があります。ただし、組織が小規模であり、返される情報の量や種類を制限する必要がない場合は、Office 365 レポートを Excel 内から開くことを検討してください。
  
ただし、いくつかの制限があります。主な制限には次のようなものがあります。返される前のデータをフィルター、ソート、選択、またはその他の操作を行うことはできません。その代わり、レポートで返される既定のデータ セットが得られます。これは十分なデータとは言えない場合があります。たとえば、レポートが 1 年ではなく先月のデータだけを返す場合があります。一方、データが多すぎる場合もあります。先月のデータだけを必要としているにもかかわらず、1 年のデータが返される場合もあります。
  
Excel 内から直接 Office 365 レポートを開くには、次の手順を完了します。
  
1. まず、Excel で新しいワークシートを開きます。そのワークシートで、**[データ]** をクリックし、**[その他のソース]** をクリックしてから、**[OData データ フィード]** をクリックします。これにより、**[データ接続ウィザード]** ダイアログ ボックスが表示されます。
    
     ![データ接続ウィザードの [データ フィードへの接続] ダイアログ ボックスの例です。](images/o365_reporting_connect_data_feed.png)
  
2. **[データ フィードへの接続]** ページで、データ フィードの場所として **https://reports.office365.com/ecp/reportingwebservice/reporting.svc/** を入力します。表示されているように、入力できるのはベース URL だけであることに注意してください。Select、Filter、Format ステートメントを追加することはできません。ベース URL 以外のものを入力した場合、データは何も返されません。代わりに、次のエラー メッセージだけが表示されます。
    
     ![Select、Filter、Format ステートメントを追加するときのエラー メッセージの例です。](images/o365_reporting_incorrect_data_feed.png)
  
3. レポート サービスの URL を入力した後、**[ログオン資格情報]** で **[この名前とパスワードを使用する]** を選択します。**[ユーザー名]** ボックスで、Office 365 ログオン名 (たとえば、admin@litwareinc.onmicrosoft.com) を入力します。**[パスワード]** ボックスで、Office 365 ログオン パスワードを入力してから、**[次へ]** をクリックします。Excel は、提供された資格情報を使用して、レポート サービスへの接続を試行します。
    
4. 認証されると、**[テーブルの選択]** ページが表示されます。表示したいレポート (たとえば、**MailTrafficTop**) を選択してから、**[次へ]** をクリックします。
    
     ![データ接続ウィザードの [テーブルの選択] ページの例です。](images/o365_reporting_select_tables.png)
  
    > [!NOTE]
    > 複数のレポートを選択できます。その結果、複数のテーブル/グラフが Excel スプレッドシートに追加されます。複数のレポートからのデータを組み合わせた単一のテーブル/グラフを作成することもできますが、それについてはこの入門記事では説明しません。 
  
5. **[次へ]** をクリックすると、**[データ接続ファイルを保存して終了]** ページが表示されます。
    
     ![データ接続ウィザードの [データ接続ファイルを保存して終了] ページの例です。](images/o365_reporting_odata_finish.png)
  
    ここでは、情報を入力する必要はありません。データを取得するには、**[終了]** をクリックするだけです。ただし、既定では、各データ接続に関する情報が Excel で保存されることに注意してください。このデータは、**[My Data Sources]** フォルダーに保存されます。
    
     ![[My Data Sources] フォルダーの [名前を付けて保存] ダイアログ ボックスの例です。](images/o365_reporting_save_data_source.png)
  
    このため、ダイアログ ボックスには、**[フレンドリ名]** と **[キーワード検索]** のようなラベルのテキスト ボックスが含まれます。このオプションにより、これらのデータ接続をカスタマイズすることができます。このようにしても、次のような一連のデータ ソースが存在することにはなりません。
    
  ```
  DataFeed_1_reports-office365-com ClientSoftwareBrowserDetail.odc
DataFeed_1_reports-office365-com MailTrafficTop.odc
DataFeed_1_reports-office365-com Multiple Tables.odc
DataFeed_2_reports-office365-com MailboxActivityWeekly.odc
DataFeed_2_reports-office365-com MailTrafficTop.odc
DataFeed_3_reports-office365-com ClientSoftwareBrowserDetail.odc
  ```

**[パスワードをファイルに保存する]** チェック ボックスを選択すると、これらのデータ フィードを再利用できるようになります。たとえば、データ接続を**クライアント ブラウザー レポート**として保存するとします。Office 365 ドメインへのアクセスに使用する Web ブラウザーに関する情報が次回必要になった場合、手順を追ってデータ接続ウィザードを使用する必要はありません。代わりに、Excel を開いて **[データ]** をクリックし、**[既存のソース]** をクリックするだけで済みます。**[既存の接続]** ダイアログ ボックスで目的のデータ接続を選択してから、**[OK]** をクリックします。
    
![[既存の接続] ダイアログ ボックスで目的のデータ接続を選択する例です。](images/o365_reporting_select_connection.png)
  
その時点で、Excel は接続を作成し、データを取得します。
    
これらの .ODC ファイルはプレーンテキストの XML ファイルです。これらのプレーンテキスト XML ファイルには、Office 365 のユーザー名とパスワードが含まれています。
    
\<odc:ConnectionString>Data Source=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/;Namespaces to Include=*;Max Received Message Size=4398046511104;Integrated Security=Basic; **User ID=admin@litwareinc.onmicrosoft.com;Password=MYpassw0rd!**;Persist Security Info=false;Service Document Url=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/\</odc:ConnectionString>
    
テキスト形式のファイルにユーザー名とパスワードを保存したくない場合には、**[パスワードをファイルに保存する]** というラベルのボックスをオンにしないでください。ただし、これを行った場合、これらのデータ接続を再利用できなくなることに注意してください。これは、ユーザー名とパスワードがなければ、Office 365 はサービスへのログオンの試行を認証できなくなるためです。
    
6. **[データ接続ファイルを保存して終了]** ページで **[終了]** をクリックすると、**[データのインポート]** ダイアログ ボックスが表示されます。
    
     ![[データのインポート] ダイアログ ボックスの例です。](images/o365_reporting_import_data.png)
  
7. 表示オプション (たとえば、**[ピボットテーブル レポート]**) を選択してから、**[OK]** をクリックします。すべてが正常に推移すれば、データはインポートされ、種類にかかわらず選択した表示オプションで表示されます。
    
     ![Excel ワークシートに正常にインポートされたデータの例です。](images/o365_reporting_sample_spreadsheet.png)
  
そのデータを使用して行う処理は、すべてユーザー次第です。いくつかの提案については、「[OData データ フィードを使用して Excel Services ダッシュボードを作成する](https://technet.microsoft.com/ja-JP/library/jj873965%28v=office.15%29.aspx)」を参照してください。この記事では Office 365 レポート サービスは使用されませんが、フィルターやスライサーを新規のダッシュボードに追加するなどの処理に関する役立つヒントが得られます。
  
## <a name="see-also"></a>関連項目

#### 

[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)
  
[Windows PowerShell を使用して Office 365 でレポートを作成する](use-windows-powershell-to-create-reports-in-office-365.md)

