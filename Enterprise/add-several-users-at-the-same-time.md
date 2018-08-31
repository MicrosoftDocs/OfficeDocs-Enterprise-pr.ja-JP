---
title: 複数のユーザーを同時に Office 365 に追加する - 管理者ヘルプ
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MED150
- GMA150
- MBS150
- GEA150
- BCS160
ms.assetid: 1f5767ed-e717-4f24-969c-6ea9d412ca88
description: '複数のユーザーが Office 365 のビジネス、スプレッドシートまたはその他の CSV で一覧から形式のファイルを追加する方法について説明します。アカウントを Office 365 に追加する方法を説明する YouTube でビデオを見る。このプロセスの最後に、アカウントを持つ各ユーザーは、Office 365 のメールボックスがあります。 '
ms.openlocfilehash: 1f91821ee552b59201ca01bdbce7edc0406929d6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541561"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="35753-105">複数のユーザーを同時に Office 365 に追加する - 管理者ヘルプ</span><span class="sxs-lookup"><span data-stu-id="35753-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="35753-p102">各チーム メンバー サインインし、電子メールや Office などの Office 365 サービスにアクセスする前にユーザー アカウントが必要があります。多くの人があれば、Excel のスプレッドシートまたはその他のファイルを CSV 形式で保存されてからすべてを一度に自分のアカウントを追加します。[どのような CSV 形式ではわからない場合は、?](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="35753-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
## <a name="add-multiple-users-to-office-365-in-the-office-365-admin-center"></a><span data-ttu-id="35753-109">Office 365 の管理センターで、Office 365 に複数のユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="35753-109">Add multiple users to Office 365 in the Office 365 admin center</span></span>

1. <span data-ttu-id="35753-110">職場または学校のアカウントを使用して、Office 365 にサインインします。</span><span class="sxs-lookup"><span data-stu-id="35753-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="35753-111">Office 365 管理センターで、[**ユーザ**] を選択します\>**アクティブなユーザー**です。</span><span class="sxs-lookup"><span data-stu-id="35753-111">In the Office 365 admin center, choose **Users** \> **Active users**.</span></span>
    
    ![管理センターの「ユーザーとし、アクティブなユーザーの使用」を選択していますください。](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
3. <span data-ttu-id="35753-113">**詳細**ボックスの一覧、**複数のユーザーのインポート**を選択します。</span><span class="sxs-lookup"><span data-stu-id="35753-113">In the **More** drop-down, choose **Import multiple users**.</span></span>
    
4. <span data-ttu-id="35753-114">[**複数のユーザーをインポート**] パネルで、サンプルの CSV ファイルのサンプル データの入力の有無にかかわらず必要に応じてダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="35753-114">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    ![詳細ボックスの一覧を次のように選択します。 複数のユーザーをインポートします。](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    <span data-ttu-id="35753-116">スプレッドシートを 1 つのサンプルと**まったく同じ列の見出し**を含める必要があります (ユーザー名、名などです。..)。テンプレートを使用する場合は、メモ帳などのテキスト編集ツールで開き、1 行のすべてのデータを残したままだけとだけデータを入力して下の行 2 を検討してください。</span><span class="sxs-lookup"><span data-stu-id="35753-116">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="35753-117">スプレッドシートでは、(bob@contoso.com) のようなユーザー名およびユーザーごとに (Bob 友野) のような表示名の値を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="35753-117">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. <span data-ttu-id="35753-118">ボックスにファイル パスを入力または**確認**をクリックし、CSV ファイルの場所を参照する**参照**を選択します。</span><span class="sxs-lookup"><span data-stu-id="35753-118">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
    
    ![CSV ファイルを確認します。](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    <span data-ttu-id="35753-p103">ファイルに問題がある場合は、問題がパネルに表示されます。ログ ファイルをダウンロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="35753-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
6. <span data-ttu-id="35753-122">**ユーザー オプションの設定**ダイアログ ボックスでは、サインイン状態を設定し、すべてのユーザーに割り当てられる製品のライセンスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="35753-122">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
7. <span data-ttu-id="35753-123">**結果の表示**] ダイアログを選択できますを自分自身または他のユーザーが (パスワードはテキスト形式で表示されます)、結果を送信して、どのように多くのユーザーが作成されているを参照してくださいいくつかの新しいユーザーに割り当てるには複数のライセンスを購入する必要がある場合とします。</span><span class="sxs-lookup"><span data-stu-id="35753-123">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 
    
## <a name="watch-the-video"></a><span data-ttu-id="35753-124">ビデオを見る</span><span class="sxs-lookup"><span data-stu-id="35753-124">Watch the video</span></span>
<span data-ttu-id="35753-125"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="35753-125"></span></span>

 <span data-ttu-id="35753-126">ビデオでは、短い一括する方法を示していますユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="35753-126">Watch a short video that shows you how to bulk add users.</span></span> 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a><span data-ttu-id="35753-127">次の手順</span><span class="sxs-lookup"><span data-stu-id="35753-127">Next steps</span></span>
<span data-ttu-id="35753-128"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="35753-128"></span></span>

- <span data-ttu-id="35753-p104">これらの人々 は、アカウントを持っている、これでは、[ダウンロードおよびインストールまたは Office 365 または PC または Mac 上の Office 2016 を再インストール](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658)する必要があります。各チーム メンバーは、最大 5 つの Pc または Mac 上の Office 365 をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="35753-p104">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658). Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="35753-p105">各ユーザーは、5 つまでのタブレットや 5 つの電話、iPhones、台もの Ipad、および Android フォンやタブレットなどの[Office アプリケーションとモバイル デバイスで電子メールの設定](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f)でこともできます。この方法では、任意の場所から Office ファイルを編集することができます。</span><span class="sxs-lookup"><span data-stu-id="35753-p105">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets. This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="35753-133">セットアップ手順のエンド ・ ツー ・ エンドの一覧については[企業向けの Office 365 のセットアップ](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35753-133">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="35753-134">ユーザーを Office 365 に追加する方法の詳細について</span><span class="sxs-lookup"><span data-stu-id="35753-134">More information about how to add users to Office 365</span></span>
<span data-ttu-id="35753-135"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="35753-135"></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="35753-136">わからない場合は、CSV 形式は次のとおりですか。</span><span class="sxs-lookup"><span data-stu-id="35753-136">Not sure what CSV format is?</span></span>
<span data-ttu-id="35753-137"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="35753-137"></span></span>

<span data-ttu-id="35753-p106">CSV ファイルは、コンマで区切られた値を持つファイルです。作成したり、任意のテキスト エディターまたは Excel などのスプレッドシート プログラムで次のようにファイルを編集することができます。</span><span class="sxs-lookup"><span data-stu-id="35753-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="35753-p107">開始点としては、[このサンプル スプレッドシート](https://www.microsoft.com/en-us/download/details.aspx?id=45485)をダウンロードできます。Office 365 の最初の行の列見出し、しないに置き換える以外に必要なことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="35753-p107">You can download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="35753-142">新しい名前でファイルを保存し、CSV 形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="35753-142">Save the file with a new name, and specify CSV format.</span></span>
  
![Excel で CSV 形式でファイルを保存する方法のイメージ](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="35753-p108">ファイルを保存すると、おそらく、ブック内の一部の機能が失われる場合は、CSV 形式でファイルを保存するように求めるメッセージが表示されます。これは、問題ありません。**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="35753-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![Excel では、CSV 形式でファイルを保存するかどうかを確認するから取得したメッセージの画像](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="35753-148">スプレッドシートを書式設定のヒント</span><span class="sxs-lookup"><span data-stu-id="35753-148">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="35753-149"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="35753-149"></span></span>

- <span data-ttu-id="35753-p109">**サンプルのスプレッドシートと同じ列見出しが必要ですか?** うん。サンプルのスプレッドシートには、最初の行の列見出しが含まれています。これらの見出しは、必要があります。Office 365 に追加するユーザーごとの見出しの下の行を作成します。追加、変更、または削除する列見出しのいずれかの場合は、Office 365 できないことがあります、ファイル内の情報からユーザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="35753-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="35753-p110">**ユーザーごとに必要なすべての情報がない場合ですか?** ユーザー名と表示名は必須で、この情報がない新しいユーザーを追加することはできません。Fax など、他の情報の一部を持っていない場合は、フィールドは空白のままする必要があることを示すためにスペースとコンマを使用できます。</span><span class="sxs-lookup"><span data-stu-id="35753-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="35753-p111">* * どのように小規模または大規模なスプレッドシートができますか。* * スプレッドシートには、少なくとも 2 つの行が必要です。1 つは、列見出し (ユーザー データの列ラベル) とユーザーのいずれかです。251 以上の行を持つことはできません。250 を超えるユーザーをインポートする場合は、複数のスプレッドシートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="35753-p111">** How small or large can the spreadsheet be? ** The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="35753-p112">* * どのような言語を使用できますか。* *、スプレッドシートを作成するとき、任意の言語または文字でユーザー データの列ラベルを入力することができますが、サンプルに示すように、ラベルの順序を変更する必要があります。任意の言語または文字を使用して、フィールドにエントリを作成し、Unicode または UTF-8 形式のファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="35753-p112">** What languages can I use? ** When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="35753-p113">**場合のさまざまな国や地域からのユーザーを追加しますか?** 領域ごとに個別のスプレッドシートを作成します。一括をステップ実行する必要がありますユーザーの追加ウィザード、各スプレッドシートを扱う場合、ファイルに含まれるすべてのユーザーの 1 つの場所を提供します。</span><span class="sxs-lookup"><span data-stu-id="35753-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="35753-p114">**を使用して文字の数に制限はありますか?** 次の表は、各サンプルのスプレッドシート内のユーザー データの列ラベルと最大文字数を示します。</span><span class="sxs-lookup"><span data-stu-id="35753-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="35753-172">**ユーザー データの列ラベル**</span><span class="sxs-lookup"><span data-stu-id="35753-172">**User data column label**</span></span>|<span data-ttu-id="35753-173">**最大文字数**</span><span class="sxs-lookup"><span data-stu-id="35753-173">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="35753-174">ユーザーの名前 (必須)</span><span class="sxs-lookup"><span data-stu-id="35753-174">User Name (Required)</span></span>  <br/> |<span data-ttu-id="35753-p115">79 など、アットマーク (@)、形式の name@domain にします。\<拡張\>。30 文字以内でユーザーのエイリアスとドメイン名が 48 文字を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="35753-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 30 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="35753-177">名</span><span class="sxs-lookup"><span data-stu-id="35753-177">First Name</span></span>  <br/> |<span data-ttu-id="35753-178">64</span><span class="sxs-lookup"><span data-stu-id="35753-178">64</span></span>  <br/> |
|<span data-ttu-id="35753-179">姓</span><span class="sxs-lookup"><span data-stu-id="35753-179">Last Name</span></span>  <br/> |<span data-ttu-id="35753-180">64</span><span class="sxs-lookup"><span data-stu-id="35753-180">64</span></span>  <br/> |
|<span data-ttu-id="35753-181">表示名 (必須)</span><span class="sxs-lookup"><span data-stu-id="35753-181">Display Name (required)</span></span>  <br/> |<span data-ttu-id="35753-182">256</span><span class="sxs-lookup"><span data-stu-id="35753-182">256</span></span>  <br/> |
|<span data-ttu-id="35753-183">役職</span><span class="sxs-lookup"><span data-stu-id="35753-183">Job Title</span></span>  <br/> |<span data-ttu-id="35753-184">64</span><span class="sxs-lookup"><span data-stu-id="35753-184">64</span></span>  <br/> |
|<span data-ttu-id="35753-185">部署</span><span class="sxs-lookup"><span data-stu-id="35753-185">Department</span></span>  <br/> |<span data-ttu-id="35753-186">64</span><span class="sxs-lookup"><span data-stu-id="35753-186">64</span></span>  <br/> |
|<span data-ttu-id="35753-187">Office の数</span><span class="sxs-lookup"><span data-stu-id="35753-187">Office Number</span></span>  <br/> |<span data-ttu-id="35753-188">128</span><span class="sxs-lookup"><span data-stu-id="35753-188">128</span></span>  <br/> |
|<span data-ttu-id="35753-189">事業所電話番号</span><span class="sxs-lookup"><span data-stu-id="35753-189">Office Phone</span></span>  <br/> |<span data-ttu-id="35753-190">64</span><span class="sxs-lookup"><span data-stu-id="35753-190">64</span></span>  <br/> |
|<span data-ttu-id="35753-191">携帯電話</span><span class="sxs-lookup"><span data-stu-id="35753-191">Mobile Phone</span></span>  <br/> |<span data-ttu-id="35753-192">64</span><span class="sxs-lookup"><span data-stu-id="35753-192">64</span></span>  <br/> |
|<span data-ttu-id="35753-193">Fax</span><span class="sxs-lookup"><span data-stu-id="35753-193">Fax</span></span>  <br/> |<span data-ttu-id="35753-194">64</span><span class="sxs-lookup"><span data-stu-id="35753-194">64</span></span>  <br/> |
|<span data-ttu-id="35753-195">アドレス</span><span class="sxs-lookup"><span data-stu-id="35753-195">Address</span></span>  <br/> |<span data-ttu-id="35753-196">1023</span><span class="sxs-lookup"><span data-stu-id="35753-196">1023</span></span>  <br/> |
|<span data-ttu-id="35753-197">市区町村</span><span class="sxs-lookup"><span data-stu-id="35753-197">City</span></span>  <br/> |<span data-ttu-id="35753-198">128</span><span class="sxs-lookup"><span data-stu-id="35753-198">128</span></span>  <br/> |
|<span data-ttu-id="35753-199">都道府県</span><span class="sxs-lookup"><span data-stu-id="35753-199">State or Province</span></span>  <br/> |<span data-ttu-id="35753-200">128</span><span class="sxs-lookup"><span data-stu-id="35753-200">128</span></span>  <br/> |
|<span data-ttu-id="35753-201">ZIP または郵便番号コード</span><span class="sxs-lookup"><span data-stu-id="35753-201">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="35753-202">40</span><span class="sxs-lookup"><span data-stu-id="35753-202">40</span></span>  <br/> |
|<span data-ttu-id="35753-203">国または地域</span><span class="sxs-lookup"><span data-stu-id="35753-203">Country or Region</span></span>  <br/> |<span data-ttu-id="35753-204">128</span><span class="sxs-lookup"><span data-stu-id="35753-204">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="35753-205">それでも問題が Office 365 にユーザーを追加する場合ですか。</span><span class="sxs-lookup"><span data-stu-id="35753-205">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="35753-p116">**、スプレッドシートの形式が正しいことを再確認してください**。サンプル ファイルの見出しと一致しているかどうかを確認するのには列見出しを確認します。確認している規則に従って、文字列の長さの各フィールドはコンマで区切っているとします。</span><span class="sxs-lookup"><span data-stu-id="35753-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="35753-p117">* * Office 365 で新しいユーザーがすぐ表示されない場合は、数分待ってからです。* * かかることが、もう少し転送されるので、Office 365 内のすべてのサービスへの変更の中に。</span><span class="sxs-lookup"><span data-stu-id="35753-p117">** If you don't see the new users in Office 365 right away, wait a few minutes. ** It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="add-multiple-users-to-office-365-in-the-old-office-365-admin-center"></a><span data-ttu-id="35753-211">古い Office 365 管理センターで、Office 365 に複数のユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="35753-211">Add multiple users to Office 365 in the old Office 365 admin center</span></span>

1. <span data-ttu-id="35753-212">[このサンプル スプレッドシート](https://www.microsoft.com/en-us/download/details.aspx?id=45485)をダウンロードし、Excel で開きます。</span><span class="sxs-lookup"><span data-stu-id="35753-212">Download [this sample spreadsheet](https://www.microsoft.com/en-us/download/details.aspx?id=45485) and open it in Excel.</span></span> 
    
    <span data-ttu-id="35753-213">スプレッドシートを 1 つのサンプルと**まったく同じ列の見出し**を含める必要があります (ユーザー名、名などです。..)。テンプレートを使用する場合は、1 行のすべてのデータを残したままだけとだけデータを入力して下の行 2 を検討してください。</span><span class="sxs-lookup"><span data-stu-id="35753-213">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="35753-p118">スプレッドシートでは、(bob@contoso.com) のようなユーザー名およびユーザーごとに (Bob 友野) のような表示名の値を含める必要があります。他のフィールドを空白にするには、スペースとコンマのフィールドに入力次の図に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="35753-p118">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user. To leave other fields blank, enter a space plus a comma in the field as shown in the following figure.</span></span> 
    
    ![指定された空白の行には、CVS ファイルのサンプル](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    <span data-ttu-id="35753-p119">さまざまな国で作業している人があれば、各国のユーザーの 1 つのスプレッドシートを作成する必要があります。たとえば、1 つのワークシートと、米国で働く社員の一覧が表示される日本で働く社員の一覧が表示されます。これは、Office 365 サービスの可用性は地域によって異なりますので。</span><span class="sxs-lookup"><span data-stu-id="35753-p119">If you have people working in different countries, you'll need to create one spreadsheet for users in each country. For example, one spreadsheet that lists everyone who works in the US, and another that lists everyone who works in Japan. This is because the availability of Office 365 services varies by region.</span></span> 
    
    <span data-ttu-id="35753-p120">**ヒント:** 多くのユーザーを Office 365 に追加する前に、サンプルのスプレッドシートを実際にことができます。たとえば、ユーザーのいくつかのデータ サンプルのスプレッドシートを編集、5、10 と新しい名前でファイルを保存します。この手順で説明されている手順を実行、結果を確認し、新しいアカウントを削除し、もう一度初めから。この方法では、データの右側のすべてを取得するのには、状況を練習することができます。また[、スプレッドシートを書式設定のヒント](add-several-users-at-the-same-time.md#__toc314595848)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="35753-p120">**Tip:** Before you add many users to Office 365, you might want to practice with the sample spreadsheet. For example, edit the sample spreadsheet with data for a few of your users, say 5 or 10, and save the file with a new name. Run through steps described in this procedure, check the results, and then delete the new accounts and start over again. This way you can practice getting all of the data right for your situation. Also check out [Tips for formatting your spreadsheet](add-several-users-at-the-same-time.md#__toc314595848).</span></span>
    
2. <span data-ttu-id="35753-225">職場または学校のアカウントを使用して、Office 365 にサインインします。</span><span class="sxs-lookup"><span data-stu-id="35753-225">Sign in to Office 365 with your work or school account.</span></span> 
    
3. <span data-ttu-id="35753-226">Office 365 管理センターに移動します。</span><span class="sxs-lookup"><span data-stu-id="35753-226">Go to the Office 365 admin center.</span></span>
    
4. <span data-ttu-id="35753-p121">Office 365 サービスを使用する人は、ライセンスが割り当てられるする必要があります。続行する前に、スプレッドシートに記載されているすべてのユーザーのための十分なライセンスがあることを確認することもできます。**請求先**を選択して\>**のサブスクリプション**の十分があるかどうかを参照してください。ライセンスを追加購入する場合を選択 * * ライセンスの数量を変更する * *。または、ウィザードを実行し、後でライセンスを購入し、ウィザードを再度実行するが、ライセンスを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="35753-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose ** Change license quantity **. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span></span> 
    
5. <span data-ttu-id="35753-p122">一括移動ユーザーのウィザードを追加する:**ユーザー**の選択\>**アクティブなユーザー**です。選択![の多くのユーザーを Office 365 に追加するアイコン](media/3481ffea-d552-4a7f-9a3b-014504e69746.png)次の図に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="35753-p122">Now go to the Bulk add users wizard: choose **Users** \> **Active Users**. Choose ![The icon for adding many users to Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) as shown in the following figure.</span></span> 
    
    ![Office 365 管理センターの [ユーザー] セクションのイメージ](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    <span data-ttu-id="35753-235">一括では、ユーザーのウィザードが表示され、Office 365 にユーザーのグループを追加する手順を追加します。</span><span class="sxs-lookup"><span data-stu-id="35753-235">The Bulk add users wizard appears and steps you through adding a group of users to Office 365.</span></span> 
    
6. <span data-ttu-id="35753-236">手順 1 で CSV ファイルを選択して、次の図に示すように、独自のワークシートを指定します。</span><span class="sxs-lookup"><span data-stu-id="35753-236">In Step 1 - Select a CSV file, specify your own spreadsheet as shown in the following figure.</span></span>
    
    ![手順 1、一括のユーザーの追加ウィザードの [CSV ファイル](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. <span data-ttu-id="35753-238">手順 2 の確認、ウィザードに指示するかどうか、スプレッドシート内のコンテンツの書式が正しくします。</span><span class="sxs-lookup"><span data-stu-id="35753-238">In Step 2 - Verification, the wizard tells you whether the content in the spreadsheet is formatted correctly.</span></span>
    
    ![手順 2 は、一括のユーザーの追加ウィザードの検証](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. <span data-ttu-id="35753-p123">手順 3 の設定では、スプレッドシートに記載されているユーザーが Office 365 を使用できるように、**許可**を選択します。これらのユーザーが Office 365 を使用する国を選択もできます。組織内の一部のユーザーが Office 365 を使用して、別の国で、その名前を持つ別のスプレッドシートを作成するか、その大部分を実行ユーザーの追加ウィザードに追加するには、もう一度注意してください。</span><span class="sxs-lookup"><span data-stu-id="35753-p123">In Step 3 - Settings, choose **Allowed** so that the people listed in your spreadsheet will be able to use Office 365. Also choose the country in which these people will use Office 365. Remember if some people in your organization are going to use Office 365 in a different country, create a separate spreadsheet with their names and run the Bulk add users wizard again to add them.</span></span> 
    
    ![手順 3、一括のユーザーの追加ウィザードの設定](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. <span data-ttu-id="35753-244">ライセンスの割り当てページは、ライセンスの数が利用可能なを指示します。</span><span class="sxs-lookup"><span data-stu-id="35753-244">The assign licenses page tells you how many licenses are available.</span></span> 
    
    ![ライセンスのユーザーの一括追加ウィザードの手順 4](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    <span data-ttu-id="35753-p124">**ライセンスを追加購入**をするを選択することができますが、大部分をしていくユーザーの追加ウィザードと Office 365 の管理センターでの**請求**に移動します。多くのライセンスを購入後、注文の処理には数秒間待機する必要があり、一括の開始ユーザーの追加ウィザード、最初から。</span><span class="sxs-lookup"><span data-stu-id="35753-p124">You can choose **Buy more licenses**, but you'll leave the Bulk add users wizard and go to **Billing** in the Office 365 admin center. After buying more licenses, you'll have to wait a few minutes for the order to be processed and then start the Bulk add users wizard from the beginning.</span></span> 
    
    <span data-ttu-id="35753-248">ライセンスを購入しない場合は、スプレッドシートに記載されているすべてのユーザーのアカウントを作成するはありません。</span><span class="sxs-lookup"><span data-stu-id="35753-248">If you don't buy more licenses, accounts won't be created for everyone listed in your spreadsheet.</span></span> 
    
    <span data-ttu-id="35753-249">この例ではない複数のライセンスを購入し続けると、一括でユーザーの追加ウィザード。</span><span class="sxs-lookup"><span data-stu-id="35753-249">In this example, we don't buy any more licenses and continue with the Bulk add users wizard.</span></span>
    
10. <span data-ttu-id="35753-250">手順 5 の結果を送信する、スプレッドシート内のユーザーの*すべて*の Office 365 のユーザー名と一時パスワードを一覧表示する電子メールを取得する人の電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="35753-250">In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet.</span></span> 
    
    ![手順の大部分の 5 ユーザーの追加ウィザードの結果](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    <span data-ttu-id="35753-p125">次のメールは、ステップ 5 で送信結果で指定したすべての電子メール アドレスに送信されます。この電子メールは、アカウントが作成されたことを示します。十分なライセンスがないため一部のユーザーのアカウントに作成されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="35753-p125">The following email is sent to all the email addresses you specified in Step 5 - Send results. This email indicates which accounts were created. Notice that accounts weren't created for some people because there weren't enough licenses.</span></span> 
    
    ![ユーザーの資格情報と電子メールのサンプル](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    <span data-ttu-id="35753-p126">購入できるより多くの後で、ライセンスと、一括追加を再実行したスプレッドシートにユーザーのウィザードです。ウィザードは、既にアカウントを持つユーザーはスキップします。結果レポートで、[重複するユーザー名] は「既にその情報を持つユーザー アカウントを持っているかを示す。</span><span class="sxs-lookup"><span data-stu-id="35753-p126">You can buy more licenses later and rerun the Bulk add users wizard with the same spreadsheet. The wizard skips over the users that already have accounts; on the results report, it will say "duplicate user name" to indicate someone with that information already has an account.</span></span>
    
11. <span data-ttu-id="35753-258">大部分の最後のページは、次の図に示すように、ユーザー名と一時パスワードは、ウィザードのユーザーを一覧表示を追加します。</span><span class="sxs-lookup"><span data-stu-id="35753-258">The final page in the Bulk add users wizard lists the user names and temporary passwords, as shown in the following figure.</span></span>
    
    ![6. 大半のユーザーの追加ウィザードの結果](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. <span data-ttu-id="35753-p127">ユーザーを Office 365 に追加した後、Office 365 のアカウント情報の内容を伝えてする必要があります。新しいパスワードを通信するため、通常のプロセスを使用します。</span><span class="sxs-lookup"><span data-stu-id="35753-p127">After you've added users to Office 365, you need to tell them about their Office 365 account information. Use your normal process for communicating new passwords.</span></span>
    

