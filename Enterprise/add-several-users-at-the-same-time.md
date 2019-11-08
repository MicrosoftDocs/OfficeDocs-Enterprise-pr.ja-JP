---
title: 同時に複数のユーザーを Office 365 に追加する - 管理者ヘルプ
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
audience: Admin
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
description: 'ワークシートまたはその他の CSV 形式のファイルのリストから、複数のユーザーを Office 365 に追加する方法について説明します。 Office 365 にアカウントを追加する方法を説明する YouTube のビデオを視聴してください。 このプロセスが完了すると、アカウントを持つ各ユーザーに Office 365 メールボックスが割り当てられます。 '
ms.openlocfilehash: a719b2626eada8abe225a6951af4a2d292667856
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030731"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a><span data-ttu-id="acfc4-105">同時に複数のユーザーを Office 365 に追加する - 管理者ヘルプ</span><span class="sxs-lookup"><span data-stu-id="acfc4-105">Add several users at the same time to Office 365 - Admin Help</span></span>

<span data-ttu-id="acfc4-p102">メールや Office などの Office 365 サービスにサインインしてアクセスするには、チームの各メンバーにユーザー アカウントが必要です。 ユーザー数が多い場合、Excel のスプレッドシートまたは CSV 形式で保存された他のファイルから、ユーザー アカウントを一括で追加することができます。 [CSV 書式の定義](add-several-users-at-the-same-time.md#__toc316652088)</span><span class="sxs-lookup"><span data-stu-id="acfc4-p102">Each person on your team needs a user account before they can sign in and access Office 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
## <a name="add-multiple-users-to-office-365-in-the-microsoft-365-admin-center"></a><span data-ttu-id="acfc4-109">Microsoft 365 管理センターの Office 365 に複数のユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="acfc4-109">Add multiple users to Office 365 in the Microsoft 365 admin center</span></span>

1. <span data-ttu-id="acfc4-110">職場または学校のアカウントを使用して、Office 365 にサインインします。</span><span class="sxs-lookup"><span data-stu-id="acfc4-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="acfc4-111">In the admin center, choose **Users** \> **Active users**.</span><span class="sxs-lookup"><span data-stu-id="acfc4-111">In the admin center, choose **Users** \> **Active users**.</span></span>
    
    ![管理センターで、[ユーザー]、[アクティブユーザー] の順に選択します。](media/12086d98-a8b4-4c48-89cf-b78ad8058ff1.png)
  
    
3. <span data-ttu-id="acfc4-113">[ **複数のユーザーをインポート**] パネルで、サンプルの CSV ファイルをサンプル データがある状態、またはない状態でダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-113">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    ![In the More drop-down, choose Import multiple users](media/77df8a4a-fd00-4fbe-bf1c-d234fc1d5e93.png)
  
    <span data-ttu-id="acfc4-115">スプレッドシートには、サンプルと **まったく同じ列見出し** が含まれている必要があります (ユーザー名、名、など)。テンプレートを使用する場合は、メモ帳などのテキスト編集ツールでテンプレートを開き、1 行目のすべてのデータをそのままにして実際のデータを 2 行目以降にのみ入力することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="acfc4-115">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="acfc4-116">スプレッドシートには、各ユーザーのユーザー名 (bob@contoso.com など) と表示名 (Bob Kelly など) の値を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="acfc4-116">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

4. <span data-ttu-id="acfc4-117">ボックスにファイル パスを入力するか、[ **参照**] を選択して CSV ファイルの場所を参照し、[ **確認**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-117">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
    
    ![Your CSV file is verified](media/a43d49db-b2ab-4200-8ddf-0bc846ac6fe5.png)
  
    <span data-ttu-id="acfc4-p103">ファイルに問題がある場合は、パネルにその問題が表示されます。ログ ファイルをダウンロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
5. <span data-ttu-id="acfc4-121">[ **ユーザー オプションの設定**] ダイアログで、サインイン状態を設定し、すべてのユーザーに割り当てられる製品ライセンスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-121">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
6. <span data-ttu-id="acfc4-122">[ **結果の表示**] ダイアログで、結果を自分や他のユーザーに送信するかどうかを選択できます (パスワードはプレーン テキストとなります)。作成されたユーザーの数も表示されます。新規ユーザーに割り当てるライセンスを追加購入することもできます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-122">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 
    
## <a name="watch-the-video"></a><span data-ttu-id="acfc4-123">ビデオの視聴</span><span class="sxs-lookup"><span data-stu-id="acfc4-123">Watch the video</span></span>
<span data-ttu-id="acfc4-124"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="acfc4-124"></span></span>

 <span data-ttu-id="acfc4-125">ユーザーの一括追加方法についての短いビデオを確認してください。</span><span class="sxs-lookup"><span data-stu-id="acfc4-125">Watch a short video that shows you how to bulk add users.</span></span> 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a><span data-ttu-id="acfc4-126">次の手順</span><span class="sxs-lookup"><span data-stu-id="acfc4-126">Next steps</span></span>
<span data-ttu-id="acfc4-127"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="acfc4-127"></span></span>

- <span data-ttu-id="acfc4-128">これらのユーザーはアカウントを所有しているので、 [office 365 または office 2016 を PC または Mac にダウンロードしてインストールまたは再](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658)インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="acfc4-128">Now that these people have accounts, they need to [Download and install or reinstall Office 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span></span> <span data-ttu-id="acfc4-129">チームのメンバー 1 人につき、最大 5 台の PC または Mac に Office 365 をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-129">Each person on your team can install Office 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="acfc4-130">各ユーザーは、1つの[モバイルデバイスで Office アプリとメール](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f)をセットアップすることもできます。これには、Iphones、Ipad、Android の携帯電話、タブレットなどの最大5台のタブレットと5台の電話機があります。</span><span class="sxs-lookup"><span data-stu-id="acfc4-130">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets.</span></span> <span data-ttu-id="acfc4-131">このようにすると、どこにいても Office のファイルを編集できます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-131">This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="acfc4-132">セットアップ手順のエンドツーエンドのリストについては、「 [Office 365 for business の](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)セットアップ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="acfc4-132">See [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a><span data-ttu-id="acfc4-133">Office 365 へのユーザー追加方法に関するその他の情報</span><span class="sxs-lookup"><span data-stu-id="acfc4-133">More information about how to add users to Office 365</span></span>
<span data-ttu-id="acfc4-134"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="acfc4-134"></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="acfc4-135">CSV 書式の定義</span><span class="sxs-lookup"><span data-stu-id="acfc4-135">Not sure what CSV format is?</span></span>
<span data-ttu-id="acfc4-136"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="acfc4-136"></span></span>

<span data-ttu-id="acfc4-p106">CSV ファイルは、コンマで区切られた値を含むファイルです。 テキスト エディターまたは Excel などのスプレッドシート プログラムを使って、このようなファイルを作成または編集することができます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="acfc4-p107">出発点として、[このサンプル スプレッドシート](https://www.microsoft.com/download/details.aspx?id=45485)をダウンロードして使うことができます。Office 365 には 1 行目の列見出しが必要なので、別のテキストで置き換えないでください。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p107">You can download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) as a starting point. Remember that Office 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="acfc4-141">新しい名前でファイルを保存し、CSV 形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="acfc4-141">Save the file with a new name, and specify CSV format.</span></span>
  
![Excel でファイルを CSV 形式で保存する方法を示した画像](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="acfc4-p108">ファイルを保存するときに、CSV 形式でファイルを保存すると、ブックの一部の機能が失われるというメッセージが表示されることがあります。 このメッセージは問題ありません。 [ **はい**] をクリックして続けます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![CSV 形式でファイルを保存するかどうかを確認する Excel メッセージの画像](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="acfc4-147">スプレッドシートの書式設定のヒント</span><span class="sxs-lookup"><span data-stu-id="acfc4-147">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="acfc4-148"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="acfc4-148"></span></span>

- <span data-ttu-id="acfc4-p109">**サンプル スプレッドシートと同じ列見出しにする必要はありますか?** はい。サンプル スプレッドシートの 1 行目には列見出しが含まれています。列見出しは必須です。見出しの下に、Office 365 に追加するユーザーごとに 1 行を作成します。列見出しのいずれかを追加、変更、または削除すると、Office 365 でファイル内の情報からユーザーを作成できなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Office 365, create a row under the heading. If you add, change, or delete any of the column headings, Office 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="acfc4-p110">**各ユーザーに必要な情報が揃っていない場合はどのようになりますか?** ユーザー名と表示名は必須で、この情報がないと新しいユーザーは追加できません。FAX 番号などの他の情報が一部欠けている場合は、フィールドが空白であることを示すために、スペースに加えてコンマを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="acfc4-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span><span class="sxs-lookup"><span data-stu-id="acfc4-p111">\*\* How small or large can the spreadsheet be? \*\* The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="acfc4-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span><span class="sxs-lookup"><span data-stu-id="acfc4-p112">\*\* What languages can I use? \*\* When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="acfc4-p113">**異なる国や地域のユーザーを追加する場合はどうですか?** 領域ごとに別のスプレッドシートを作成します。 スプレッドシートごとにユーザーの一括追加ウィザードの手順を実行し、処理中のファイルに含まれるすべてのユーザーを 1 つの場所にまとめるようにします。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="acfc4-p114">**使用できる文字数に制限はありますか?** 次の表は、サンプルのスプレッドシート内のユーザーデータの列ラベルと、それぞれの最大文字数を示しています。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="acfc4-171">**ユーザー データの 列 ラベル**</span><span class="sxs-lookup"><span data-stu-id="acfc4-171">**User data column label**</span></span>|<span data-ttu-id="acfc4-172">**最大文字数**</span><span class="sxs-lookup"><span data-stu-id="acfc4-172">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="acfc4-173">ユーザー名 (必須)</span><span class="sxs-lookup"><span data-stu-id="acfc4-173">User Name (Required)</span></span>  <br/> |<span data-ttu-id="acfc4-p115">name@domain.\<extension\> という形式で、@ 記号を含めて 79 文字です。 ユーザーの別名は 30 文字を超えることはできず、ドメイン名は 48 文字を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 30 characters, and the domain name cannot exceed 48 characters.</span></span>  <br/> |
|<span data-ttu-id="acfc4-176">名</span><span class="sxs-lookup"><span data-stu-id="acfc4-176">First Name</span></span>  <br/> |<span data-ttu-id="acfc4-177">64</span><span class="sxs-lookup"><span data-stu-id="acfc4-177">64</span></span>  <br/> |
|<span data-ttu-id="acfc4-178">姓</span><span class="sxs-lookup"><span data-stu-id="acfc4-178">Last Name</span></span>  <br/> |<span data-ttu-id="acfc4-179">64</span><span class="sxs-lookup"><span data-stu-id="acfc4-179">64</span></span>  <br/> |
|<span data-ttu-id="acfc4-180">表示名 (必須)</span><span class="sxs-lookup"><span data-stu-id="acfc4-180">Display Name (required)</span></span>  <br/> |<span data-ttu-id="acfc4-181">256</span><span class="sxs-lookup"><span data-stu-id="acfc4-181">256</span></span>  <br/> |
|<span data-ttu-id="acfc4-182">役職</span><span class="sxs-lookup"><span data-stu-id="acfc4-182">Job Title</span></span>  <br/> |<span data-ttu-id="acfc4-183">64</span><span class="sxs-lookup"><span data-stu-id="acfc4-183">64</span></span>  <br/> |
|<span data-ttu-id="acfc4-184">部署</span><span class="sxs-lookup"><span data-stu-id="acfc4-184">Department</span></span>  <br/> |<span data-ttu-id="acfc4-185">64</span><span class="sxs-lookup"><span data-stu-id="acfc4-185">64</span></span>  <br/> |
|<span data-ttu-id="acfc4-186">事務所番号</span><span class="sxs-lookup"><span data-stu-id="acfc4-186">Office Number</span></span>  <br/> |<span data-ttu-id="acfc4-187">128</span><span class="sxs-lookup"><span data-stu-id="acfc4-187">128</span></span>  <br/> |
|<span data-ttu-id="acfc4-188">会社電話</span><span class="sxs-lookup"><span data-stu-id="acfc4-188">Office Phone</span></span>  <br/> |<span data-ttu-id="acfc4-189">64</span><span class="sxs-lookup"><span data-stu-id="acfc4-189">64</span></span>  <br/> |
|<span data-ttu-id="acfc4-190">携帯電話</span><span class="sxs-lookup"><span data-stu-id="acfc4-190">Mobile Phone</span></span>  <br/> |<span data-ttu-id="acfc4-191">64</span><span class="sxs-lookup"><span data-stu-id="acfc4-191">64</span></span>  <br/> |
|<span data-ttu-id="acfc4-192">FAX</span><span class="sxs-lookup"><span data-stu-id="acfc4-192">Fax</span></span>  <br/> |<span data-ttu-id="acfc4-193">64</span><span class="sxs-lookup"><span data-stu-id="acfc4-193">64</span></span>  <br/> |
|<span data-ttu-id="acfc4-194">番地</span><span class="sxs-lookup"><span data-stu-id="acfc4-194">Address</span></span>  <br/> |<span data-ttu-id="acfc4-195">1023</span><span class="sxs-lookup"><span data-stu-id="acfc4-195">1023</span></span>  <br/> |
|<span data-ttu-id="acfc4-196">市区町村</span><span class="sxs-lookup"><span data-stu-id="acfc4-196">City</span></span>  <br/> |<span data-ttu-id="acfc4-197">128</span><span class="sxs-lookup"><span data-stu-id="acfc4-197">128</span></span>  <br/> |
|<span data-ttu-id="acfc4-198">都道府県</span><span class="sxs-lookup"><span data-stu-id="acfc4-198">State or Province</span></span>  <br/> |<span data-ttu-id="acfc4-199">128</span><span class="sxs-lookup"><span data-stu-id="acfc4-199">128</span></span>  <br/> |
|<span data-ttu-id="acfc4-200">郵便番号</span><span class="sxs-lookup"><span data-stu-id="acfc4-200">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="acfc4-201">40</span><span class="sxs-lookup"><span data-stu-id="acfc4-201">40</span></span>  <br/> |
|<span data-ttu-id="acfc4-202">国または地域</span><span class="sxs-lookup"><span data-stu-id="acfc4-202">Country or Region</span></span>  <br/> |<span data-ttu-id="acfc4-203">128</span><span class="sxs-lookup"><span data-stu-id="acfc4-203">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a><span data-ttu-id="acfc4-204">Office 365 にユーザーを追加するときの問題がまだ解決しない場合</span><span class="sxs-lookup"><span data-stu-id="acfc4-204">Still having problems when adding users to Office 365?</span></span>

- <span data-ttu-id="acfc4-p116">**スプレッドシートの形式が正しいかどうか慎重にチェックしてください。** サンプル ファイル内の見出しと一致しているか、列見出しをチェックします。文字数の制限に従い、各フィールドがカンマで区切られるようにします。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="acfc4-p117">\*\* If you don't see the new users in Office 365 right away, wait a few minutes. \*\* It can take a little while for changes to go across all the services in Office 365.</span><span class="sxs-lookup"><span data-stu-id="acfc4-p117">\*\* If you don't see the new users in Office 365 right away, wait a few minutes. \*\* It can take a little while for changes to go across all the services in Office 365.</span></span> 
    
## <a name="add-multiple-users-to-office-365-in-the-old-admin-center"></a><span data-ttu-id="acfc4-210">以前の管理センターで Office 365 に複数のユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="acfc4-210">Add multiple users to Office 365 in the old admin center</span></span>

1. <span data-ttu-id="acfc4-211">[このサンプル スプレッドシート](https://www.microsoft.com/download/details.aspx?id=45485)をダウンロードし、Excel で開きます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-211">Download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) and open it in Excel.</span></span> 
    
    <span data-ttu-id="acfc4-212">スプレッドシートには、サンプルと **まったく同じ列見出し** が含まれている必要があります ("ユーザー名"、"名" など)。テンプレートを使用する場合は、1 行目のすべてのデータをそのままにして実際のデータを 2 行目以降にのみ入力することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="acfc4-212">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="acfc4-p118">また、このスプレッドシートには各ユーザーのユーザー名 (たとえば akito@contoso.com) と表示名 (たとえば "佐藤 明人") が入力されている必要があります。その他のフィールドを空白のままにするには、次の図のように半角スペース 1 個とコンマを入力してください。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p118">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user. To leave other fields blank, enter a space plus a comma in the field as shown in the following figure.</span></span> 
    
    ![指定された空白行を含むサンプル CSV ファイル](media/9c596ba1-1053-4687-a46c-c9359e9818c9.png)
  
    <span data-ttu-id="acfc4-p119">複数の国に従業員がいる場合、国ごとにユーザーのスプレッドシートを 1 つ作成する必要があります。たとえば、米国で勤務している全ユーザーのスプレッドシートと、日本で勤務している全ユーザーのスプレッドシートを作成します。これは、Office 365 サービスを利用できるかどうかが、地域によって異なるためです。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p119">If you have people working in different countries, you'll need to create one spreadsheet for users in each country. For example, one spreadsheet that lists everyone who works in the US, and another that lists everyone who works in Japan. This is because the availability of Office 365 services varies by region.</span></span> 
    
    <span data-ttu-id="acfc4-p120">**ヒント:** 多数のユーザーを追加する前に、サンプル スプレッドシートで練習することもできます。たとえば、サンプル スプレッドシートを編集して、5 人や 10 人など、少数のユーザー データを含め、新しい名前でファイルを保存します。この手順に従って、結果を確認し、新しいアカウントを削除して、最初から実行し直します。このようにすると、あらゆるデータについて実際の状況に合わせて練習することができます。また、[スプレッドシートの書式設定のヒント](add-several-users-at-the-same-time.md#__toc314595848)も参照してください。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p120">**Tip:** Before you add many users to Office 365, you might want to practice with the sample spreadsheet. For example, edit the sample spreadsheet with data for a few of your users, say 5 or 10, and save the file with a new name. Run through steps described in this procedure, check the results, and then delete the new accounts and start over again. This way you can practice getting all of the data right for your situation. Also check out [Tips for formatting your spreadsheet](add-several-users-at-the-same-time.md#__toc314595848).</span></span>
    
2. <span data-ttu-id="acfc4-224">職場または学校のアカウントを使用して、Office 365 にサインインします。</span><span class="sxs-lookup"><span data-stu-id="acfc4-224">Sign in to Office 365 with your work or school account.</span></span> 
    
3. <span data-ttu-id="acfc4-225">管理センターに移動します。</span><span class="sxs-lookup"><span data-stu-id="acfc4-225">Go to the admin center.</span></span>
    
4. <span data-ttu-id="acfc4-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose \*\* Change license quantity \*\*. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span><span class="sxs-lookup"><span data-stu-id="acfc4-p121">For people to use Office 365 services, they need to be assigned a license. Before continuing, you might want to check that you have enough licenses for everyone listed in your spreadsheet. Choose **Billing** \> **Subscriptions** to see if you have enough. If you need to buy more licenses, choose \*\* Change license quantity \*\*. Or, you can run the wizard and assign the licenses you have, then buy more licenses later and rerun the wizard.</span></span> 
    
5. <span data-ttu-id="acfc4-p122">ユーザーの一括追加ウィザードを開き、[ **ユーザー**] \> [ **アクティブなユーザー**] を選びます。 次の図のように、![Office 365 に多数のユーザーを追加するためのアイコン](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) を選びます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p122">Now go to the Bulk add users wizard: choose **Users** \> **Active Users**. Choose ![The icon for adding many users to Office 365](media/3481ffea-d552-4a7f-9a3b-014504e69746.png) as shown in the following figure.</span></span> 
    
    ![管理センターの [ユーザー] セクションのイメージ](media/2cd5ff86-9c0b-438e-9bb9-13b12a2675de.png)
  
    <span data-ttu-id="acfc4-234">ユーザーの一括追加ウィザードが表示されます。画面の手順に従って、複数のユーザーを Office 365 に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-234">The Bulk add users wizard appears and steps you through adding a group of users to Office 365.</span></span> 
    
6. <span data-ttu-id="acfc4-235">次の図のように、作成したスプレッドシートを手順 1 の [CSV ファイルの選択] で指定します。</span><span class="sxs-lookup"><span data-stu-id="acfc4-235">In Step 1 - Select a CSV file, specify your own spreadsheet as shown in the following figure.</span></span>
    
    ![ユーザーの一括追加ウィザードの手順 1 - CSV ファイルを選ぶ](media/aeb837ed-1f86-427d-b038-c643c383829c.png)
  
7. <span data-ttu-id="acfc4-237">手順 2 の [確認] に、スプレッドシートの内容が正しい書式で設定されているかどうかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-237">In Step 2 - Verification, the wizard tells you whether the content in the spreadsheet is formatted correctly.</span></span>
    
    ![ユーザーの一括追加ウィザードのステップ 2 - 確認](media/3fd3cd2c-44d4-4593-b02c-b87c176affb3.png)
  
8. <span data-ttu-id="acfc4-p123">手順 3 の [設定] で [ **許可**] を選び、スプレッドシートに記載されたメンバーが Office 365 を使用できるようにします。また、メンバーが Office 365 を使用する国も選びます。組織内の一部のメンバーが異なる国で Office 365 を使用する場合、そのメンバー名が記載された別のスプレッドシートを作成し、ユーザーの一括追加ウィザードをもう一度実行して追加します。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p123">In Step 3 - Settings, choose **Allowed** so that the people listed in your spreadsheet will be able to use Office 365. Also choose the country in which these people will use Office 365. Remember if some people in your organization are going to use Office 365 in a different country, create a separate spreadsheet with their names and run the Bulk add users wizard again to add them.</span></span> 
    
    ![ユーザーの一括追加ウィザードの手順 3 - 設定](media/ff12ad34-5d8b-4e89-a02f-d827a94095b3.png)
  
9. <span data-ttu-id="acfc4-243">[ライセンスの割り当て] ページには、使用できるライセンス数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-243">The assign licenses page tells you how many licenses are available.</span></span> 
    
    ![ユーザーの一括追加ウィザードのステップ 4 - ライセンス](media/161ea34c-c67e-43be-962f-029f5426ff1b.png)
  
    <span data-ttu-id="acfc4-245">[追加の**ライセンスを購入**する] を選択することもできますが、ユーザーの一括追加ウィザードを使用して、Microsoft 365 管理センターの**請求書**に移動します。</span><span class="sxs-lookup"><span data-stu-id="acfc4-245">You can choose **Buy more licenses**, but you'll leave the Bulk add users wizard and go to **Billing** in the Microsoft 365 admin center.</span></span> <span data-ttu-id="acfc4-246">ライセンスを追加購入したら、注文の処理が完了するまで数分待ち、その後でユーザーの一括追加ウィザードを最初から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acfc4-246">After buying more licenses, you'll have to wait a few minutes for the order to be processed and then start the Bulk add users wizard from the beginning.</span></span> 
    
    <span data-ttu-id="acfc4-247">ライセンスを追加購入しない場合、スプレッドシートに記載されている全員分のアカウントは作成されません。</span><span class="sxs-lookup"><span data-stu-id="acfc4-247">If you don't buy more licenses, accounts won't be created for everyone listed in your spreadsheet.</span></span> 
    
    <span data-ttu-id="acfc4-248">この例では、ライセンスを追加購入せずに、ユーザーの一括追加ウィザードを続行します。</span><span class="sxs-lookup"><span data-stu-id="acfc4-248">In this example, we don't buy any more licenses and continue with the Bulk add users wizard.</span></span>
    
10. <span data-ttu-id="acfc4-249">In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet.</span><span class="sxs-lookup"><span data-stu-id="acfc4-249">In Step 5 - Send Results, type the email addresses of the people who you want to get an email that lists  *all*  of the Office 365 user names and temporary passwords for the people in the spreadsheet.</span></span> 
    
    ![ユーザーの一括追加ウィザードのステップ 5 - 結果の送信](media/5beeb825-4ba7-4ae0-bfb5-a1f8a785ebdb.png)
  
    <span data-ttu-id="acfc4-p125">手順 5 の [電子メール] で指定したすべてのメール アドレスに次のメールが送信されます。 このメールには、作成されたアカウントが記載されています。 この例では、ライセンス数が足りなかったため、一部のユーザーについてのアカウントは作成されませんでした。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p125">The following email is sent to all the email addresses you specified in Step 5 - Send results. This email indicates which accounts were created. Notice that accounts weren't created for some people because there weren't enough licenses.</span></span> 
    
    ![ユーザーの資格情報が記載されたメールの例](media/0a40c612-2078-4b5b-813e-f99bc53635a6.png)
  
    <span data-ttu-id="acfc4-p126">後でライセンスを追加購入し、同じスプレッドシートを使ってユーザーの一括追加ウィザードを再実行することができます。 既にアカウントがあるユーザーはスキップされます。既にアカウントが存在するユーザーであることを示す "重複するユーザー名です" という結果のレポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p126">You can buy more licenses later and rerun the Bulk add users wizard with the same spreadsheet. The wizard skips over the users that already have accounts; on the results report, it will say "duplicate user name" to indicate someone with that information already has an account.</span></span>
    
11. <span data-ttu-id="acfc4-257">ユーザーの一括追加ウィザードの最後のページには、次の図のように、ユーザー名と一時パスワードの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="acfc4-257">The final page in the Bulk add users wizard lists the user names and temporary passwords, as shown in the following figure.</span></span>
    
    ![ユーザーの一括追加ウィザードのステップ 6 - 結果の送信](media/0cd43832-071b-4b33-b57a-5d07959985ad.png)
  
12. <span data-ttu-id="acfc4-p127">ユーザーを Office 365 に追加した後は、Office 365 のアカウント情報についてユーザーに知らせる必要があります。新しいパスワードを通知する通常のプロセスを使ってください。</span><span class="sxs-lookup"><span data-stu-id="acfc4-p127">After you've added users to Office 365, you need to tell them about their Office 365 account information. Use your normal process for communicating new passwords.</span></span>
    

