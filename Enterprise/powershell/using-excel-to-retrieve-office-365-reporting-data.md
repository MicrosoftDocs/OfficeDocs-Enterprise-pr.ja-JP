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
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 510d5528-ac00-4f54-9d38-75fa043d0a06
description: "概要: Microsoft Excel の OData 機能を使用して、Office 365 の展開に関する詳しいレポート情報を取得します。"
ms.openlocfilehash: a4245029c337450f5f5ac3655e0b60a301ea80ec
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="using-excel-to-retrieve-office-365-reporting-data"></a><span data-ttu-id="4f3b1-103">Excel を使用して Office 365 レポート データを取得する</span><span class="sxs-lookup"><span data-stu-id="4f3b1-103">Using Excel to Retrieve Office 365 Reporting Data</span></span>

 <span data-ttu-id="4f3b1-104">**概要:** Microsoft Excel の OData 機能を使用して、Office 365 の展開に関する詳しいレポート情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-104">**Summary:** Use the oData feature in Microsoft Excel to retrieve detailed reporting information for your deployment of Office 365</span></span>
  
<span data-ttu-id="4f3b1-p101">レポートは、システム管理の主要な部分です。Office 365 管理センターには、複数の定義済みのレポートが含まれており、左側のナビゲーションの **レポート**セクションからアクセスできます。利用状況レポートとセキュリティとコンプライアンスのレポートがあります。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p101">Reporting is a key part of system administration. The Office 365 Admin center includes a number of predefined reports, which you can access from the **Reports** section of the left navigation. There are usage reports and security and compliance reports.</span></span>
  
<span data-ttu-id="4f3b1-p102">入手可能なレポートは、使用している Office 365 のバージョンや有効になっている Office 365 サービスによって異なります。詳細については、「[レポート ページ](https://technet.microsoft.com/ja-JP/library/office-365-reports.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p102">The reports available to you depend on the version of Office 365 you are using and which Office 365 services you have enabled. For more information, see the [Reports page](https://technet.microsoft.com/ja-JP/library/office-365-reports.aspx).</span></span>
  
<span data-ttu-id="4f3b1-p103">定義済みの管理センターのレポートは優れたリソースです。これらはメールボックスの利用状況や、ユーザーがオンライン会議に費やした時間 (分単位) などを簡単に確認できるようにします。ただし、Office 365 ドメインの詳細な分析に関して言えば、このレポートには制限があります。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p103">The pre-defined Admin center reports are an excellent resource. They make it easy to check on such things as mailbox usage or the number of minutes that your users have been spending in online conferences. However, when it comes to detailed analysis of your Office 365 domain, the reports do have their limitations.</span></span>
  
<span data-ttu-id="4f3b1-p104">これらの制限を回避する 1 つの方法は、Windows PowerShell または他の開発言語を使用して Office 365 レポート サービスにアクセスし、カスタム レポートを作成することです。カスタム レポートでは、Office 365 レポート サービスから返されるデータの種類 (およびその量) を決められます。カスタム レポートを作成すれば、データをソートおよびグループ化する方法を指定し、該当する場合は、データを保存する方法も指定することもできます。たとえば、データは XML 形式または Excel に簡単にインポートできるコンマ区切り形式で保存できます。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p104">One way to work around these limitations is to use Windows PowerShell or another development language to access the Office 365 reporting service and create custom reports; custom reports give you the ability to dictate which data (and how much data) is returned from the Office 365 reporting service. By writing custom reports you can also specify how the data should be sorted and grouped, and, if applicable, how that data should be saved; for example, you can save data in XML format or in a comma-separated values format that can easily be imported in Excel.</span></span> 
  
<span data-ttu-id="4f3b1-p105">さらに、カスタム スクリプト/アプリケーションを使用して、Office 365 管理センターでは入手できないレポートにアクセスすることができます。たとえば、管理センターは、ユーザーが所有する古いメールボックスの数を表示できますが、過去 30 日間にアクセスされなかったメールボックスを表示することはできません。カスタム PowerShell スクリプトを使用すれば、これを表示することができます。まとめるなら、短く簡単な Windows PowerShell スクリプトを作成する必要があるものの、柔軟性が大幅に広がるということになります。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p105">In addition, custom scripts/applications enable you to access reports that are not available in the Office 365 Admin center. For example, the Admin center can tell you how many stale mailboxes you have, but it can't tell which mailboxes haven't been accessed in the past 30 days. That is something that a custom PowerShell script can tell you. Taken together, this represents an enormous amount of flexibility in return for having to write a short and relatively-simple Windows PowerShell script.</span></span>
  
> [!VISUAL BASIC NOTE]<span data-ttu-id="4f3b1-119"> 詳細については、Office 365 レポート サービスの「[ホーム ページ](https://msdn.microsoft.com/en-us/library/office/jj984325%28v=office.15%29.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-119"> For more information, see the [home page](https://msdn.microsoft.com/en-us/library/office/jj984325%28v=office.15%29.aspx) for the Office 365 reporting service.</span></span>
  
<span data-ttu-id="4f3b1-p106">このデータを取得するには、何らかのコードを作成する必要があります。組織が大規模であり、返される情報の量や種類を制限する必要がある場合は、これを行う価値があります。ただし、組織が小規模であり、返される情報の量や種類を制限する必要がない場合は、Office 365 レポートを Excel 内から開くことを検討してください。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p106">In order to retrieve this data, you do have to write code of some kind. That's worth it if you are a larger organization that needs to limit the amount and the type of information that gets returned. But if you're a smaller organization, and you don't need to limit the amount and type of information that gets returned, you might consider opening the Office 365 reports from within Excel itself.</span></span>
  
<span data-ttu-id="4f3b1-p107">ただし、いくつかの制限があります。主な制限には次のようなものがあります。返される前のデータをフィルター、ソート、選択、またはその他の操作を行うことはできません。その代わり、レポートで返される既定のデータ セットが得られます。これは十分なデータとは言えない場合があります。たとえば、レポートが 1 年ではなく先月のデータだけを返す場合があります。一方、データが多すぎる場合もあります。先月のデータだけを必要としているにもかかわらず、1 年のデータが返される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p107">However, there are a few limitations here, the primary one being this: you cannot filter, sort, select, or otherwise manipulate the data that before it gets returned. Instead, you simply get back the default set of data returned by the report. In some cases that might not be enough data. For example, the report might return data for, say, only the previous month and not for the entire year. Conversely, in other cases that might be too much data: you might get back data for the entire year even though you only want data for the previous month.</span></span>
  
<span data-ttu-id="4f3b1-128">Excel 内から直接 Office 365 レポートを開くには、次の手順を完了します。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-128">To open an Office 365 report directly from within Excel, complete the following procedure:</span></span>
  
1. <span data-ttu-id="4f3b1-p108">まず、Excel で新しいワークシートを開きます。そのワークシートで、 **[データ]** をクリックし、 **[その他のソース]** をクリックしてから、 **[OData データ フィード]** をクリックします。これにより、 **[データ接続ウィザード]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p108">Start by opening a new worksheet in Excel. On that worksheet, click **Data**, click **From Other Sources**, and then click **From OData Data Feed**. That brings up the **Data Connection Wizard** dialog box:</span></span>
    
     ![データ接続ウィザードの [データ フィードへの接続] ダイアログ ボックスの例です。](images/o365_reporting_connect_data_feed.png)
  
2. <span data-ttu-id="4f3b1-p109">**[データ フィードへの接続]** ページで、データ フィードの場所として **https://reports.office365.com/ecp/reportingwebservice/reporting.svc/** を入力します。表示されているように、入力できるのはベース URL だけであることに注意してください。Select、Filter、Format ステートメントを追加することはできません。ベース URL 以外のものを入力した場合、データは何も返されません。代わりに、次のエラー メッセージだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p109">On the **Connect to a Data Feed** page, enter **https://reports.office365.com/ecp/reportingwebservice/reporting.svc/** as the data feed location. Note that you can only enter the base URL as shown; you cannot add any Select, Filter, or Format statements. If you enter anything but the base URL you won't get back any data; instead, you'll simply see the following error message:</span></span>
    
     ![Select、Filter、Format ステートメントを追加するときのエラー メッセージの例です。](images/o365_reporting_incorrect_data_feed.png)
  
3. <span data-ttu-id="4f3b1-p110">レポート サービスの URL を入力した後、 **[ログオン資格情報]** で **[この名前とパスワードを使用する]** を選択します。 **[ユーザー名]** ボックスで、Office 365 ログオン名 (たとえば、admin@litwareinc.onmicrosoft.com) を入力します。 **[パスワード]** ボックスで、Office 365 ログオン パスワードをログオンしてから、 **[次へ]** をクリックします。Excel は、提供された資格情報を使用して、レポート サービスへの接続を試行します。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p110">After entering the reporting service URL, select **Use this name and password** under **Log on credentials**. In the **User Name** box, enter your Office 365 logon name (for example, admin@litwareinc.onmicrosoft.com). In the **Password** box, enter your Office 365 logon password and then click **Next**. Excel will then attempt to connect to the reporting service using the supplied credentials.</span></span>
    
4. <span data-ttu-id="4f3b1-p111">認証されると、 **[テーブルの選択]** ページが表示されます。表示したいレポート (たとえば、 **MailTrafficTop** ) を選択してから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p111">After you have been authenticated, you'll see the **Select Tables** page. Select the report that you'd like to view (for example, **MailTrafficTop** ) and then click **Next**:</span></span>
    
     ![データ接続ウィザードの [テーブルの選択] ページの例です。](images/o365_reporting_select_tables.png)
  
    > [!NOTE]
    > <span data-ttu-id="4f3b1-p112">複数のレポートを選択できます。その結果、複数のテーブル/グラフが Excel スプレッドシートに追加されます。複数のレポートからのデータを組み合わせた単一のテーブル/グラフを作成することもできますが、それについてはこの入門記事では説明しません。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p112">It's possible to select multiple reports; that results in multiple tables/charts being added to your Excel spreadsheet. It's even possible to create a single table/chart that combines data from multiple reports. However, we won't discuss that in this introductory article.</span></span> 
  
5. <span data-ttu-id="4f3b1-147">**[次へ]** をクリックすると、 **[データ接続ファイルを保存して終了]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-147">After clicking **Next** you'll be presented with the **Save Data Connection File and Finish** page:</span></span>
    
     ![データ接続ウィザードの [データ接続ファイルを保存して終了] ページの例です。](images/o365_reporting_odata_finish.png)
  
    <span data-ttu-id="4f3b1-p113">ここでは、情報を入力する必要はありません。データを取得するには、 **[終了]** をクリックするだけです。ただし、既定では、各データ接続に関する情報が Excel で保存されることに注意してください。このデータは、 **[My Data Sources]** フォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p113">You don't have to enter any information here. All you need to do to retrieve your data is to click **Finish**. However, it's worth noting that, by default, Excel saves information about each data connection you make; this data is stored in your **My Data Sources** folder:</span></span>
    
     ![[My Data Sources] フォルダーの [名前を付けて保存] ダイアログ ボックスの例です。](images/o365_reporting_save_data_source.png)
  
    <span data-ttu-id="4f3b1-p114">このため、ダイアログ ボックスには、 **[フレンドリ名]** と **[キーワード検索]** のようなラベルのテキスト ボックスが含まれます。このオプションにより、これらのデータ接続をカスタマイズすることができます。このようにしても、次のような一連のデータ ソースが存在することにはなりません。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p114">That's why the dialog box includes text boxes with labels like **Friendly Name** and **Search Keywords**; these options give you the chance to customize these data connections. That way you do not end up with a whole bunch of data sources that look like these:</span></span>
    
  ```
  DataFeed_1_reports-office365-com ClientSoftwareBrowserDetail.odc
DataFeed_1_reports-office365-com MailTrafficTop.odc
DataFeed_1_reports-office365-com Multiple Tables.odc
DataFeed_2_reports-office365-com MailboxActivityWeekly.odc
DataFeed_2_reports-office365-com MailTrafficTop.odc
DataFeed_3_reports-office365-com ClientSoftwareBrowserDetail.odc
  ```

<span data-ttu-id="4f3b1-p115">**[パスワードをファイルに保存する]** チェック ボックスを選択すると、これらのデータ フィードを再利用できるようになります。たとえば、データ接続を **クライアント ブラウザー レポート** として保存するとします。Office 365 ドメインへのアクセスに使用する Web ブラウザーに関する情報が次回必要になった場合、手順を追ってデータ接続ウィザードを使用する必要はありません。代わりに、Excel を開いて **[データ]** をクリックし、 **[既存のソース]** をクリックするだけで済みます。 **[既存の接続]** ダイアログ ボックスで目的のデータ接続を選択してから、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p115">If you select the checkbox **Save password in file**, you'll be able to reuse these data feeds. For example, suppose you save a data connection as **Client Browser Report**. The next time you want information about the web browsers being used to access your Office 365 domain you don't have to walk through the data connection wizard. Instead, all you need to do is open Excel, click **Data**, and then click **Existing Sources**. Select the desired data connection in the **Existing Connections** dialog box and then click **OK**:</span></span>
    
![[既存の接続] ダイアログ ボックスで目的のデータ接続を選択する例です。](images/o365_reporting_select_connection.png)
  
<span data-ttu-id="4f3b1-161">その時点で、Excel は接続を作成し、データを取得します。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-161">At that point, Excel will make the connection for you and retrieve the data.</span></span>
    
<span data-ttu-id="4f3b1-p116">これらの .ODC ファイルはプレーンテキストの XML ファイルです。これらのプレーンテキスト XML ファイルには、Office 365 のユーザー名とパスワードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p116">Note that these .ODC files are plain-text XML files. Included in these plain-text XML files are your Office 365 user name and password:</span></span>
    
<span data-ttu-id="4f3b1-164">\<odc:ConnectionString>Data Source=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/;Namespaces to Include=\*;Max Received Message Size=4398046511104;Integrated Security=Basic; **User ID=admin@litwareinc.onmicrosoft.com;Password=MYpassw0rd!**;Persist Security Info=false;Service Document Url=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/\</odc:ConnectionString></span><span class="sxs-lookup"><span data-stu-id="4f3b1-164">\<odc:ConnectionString>Data Source=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/;Namespaces to Include=\*;Max Received Message Size=4398046511104;Integrated Security=Basic; **User ID=admin@litwareinc.onmicrosoft.com;Password=MYpassw0rd!**;Persist Security Info=false;Service Document Url=https://reports.office365.com/ecp/reportingwebservice/reporting.svc/\</odc:ConnectionString></span></span>
    
<span data-ttu-id="4f3b1-p117">テキスト形式のファイルにユーザー名とパスワードを保存したくない場合には、 **[パスワードをファイルに保存する]** というラベルのボックスをオンにしないでください。ただし、これを行った場合、これらのデータ接続を再利用できなくなることに注意してください。これは、ユーザー名とパスワードがなければ、Office 365 はサービスへのログオンの試行を認証できなくなるためです。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p117">If you don't like the idea of saving your user name and password in a plain-text file, then don't check the box labeled **Save password in file**. If you do that, however, keep in mind that you won't be able to reuse these data connections. That's because, without the user name and password, Office 365 will not be able to authenticate your attempt to log on to the service.</span></span>
    
6. <span data-ttu-id="4f3b1-168">**[データ接続ファイルを保存して終了]** ページで **[終了]** をクリックすると、 **[データのインポート]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-168">Click **Finish** on the **Save Data Connection File and Finish** page you'll be presented with the **Import Data** dialog box:</span></span>
    
     ![[データのインポート] ダイアログ ボックスの例です。](images/o365_reporting_import_data.png)
  
7. <span data-ttu-id="4f3b1-p118">表示オプション (たとえば、 **[ピボットテーブル レポート]** ) を選択してから、 **[OK]** をクリックします。すべてが正常に推移すれば、データはインポートされ、種類にかかわらず選択したビュー オプションで表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p118">Select your view options (for example, **PivotTable Report** ) and then click **OK**. If all goes well, your data will be imported and be presented in whichever view option you happened to choose:</span></span>
    
     ![Excel ワークシートに正常にインポートされたデータの例です。](images/o365_reporting_sample_spreadsheet.png)
  
<span data-ttu-id="4f3b1-p119">そのデータを使用して行う処理は、すべてユーザー次第です。いくつかの提案については、「[OData データ フィードを使用して Excel Services ダッシュボードを作成する](https://technet.microsoft.com/en-us/library/jj873965%28v=office.15%29.aspx)」を参照してください。この記事では Office 365 レポート サービスは使用されませんが、フィルターやスライサーを新規のダッシュボードに追加するなどの処理に関する役立つヒントが得られます。</span><span class="sxs-lookup"><span data-stu-id="4f3b1-p119">What you do with that data is then entirely up to you. For some suggestions. take a look at [Create an Excel Services dashboard using an oData data feed](https://technet.microsoft.com/en-us/library/jj873965%28v=office.15%29.aspx). Although that article doesn't use the Office 365 reporting service, it does provide some handy hints for doing things like adding filters and slicers to your new dashboard.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4f3b1-177">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f3b1-177">See also</span></span>

#### 

[<span data-ttu-id="4f3b1-178">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="4f3b1-178">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="4f3b1-179">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="4f3b1-179">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="4f3b1-180">Windows PowerShell を使用して Office 365 でレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="4f3b1-180">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

