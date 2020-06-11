---
title: Microsoft 365 に同時に複数のユーザーを追加する-管理者ヘルプ
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_AddUsersCSV
- O365M_AddUsersCSV
- O365E_AddUsersCSV
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
description: 'ワークシートまたはその他の CSV 形式のファイルのリストから、複数のユーザーを Microsoft 365 に追加する方法について説明します。 アカウントを Microsoft 365 に追加する方法を説明する YouTube のビデオをご覧ください。 このプロセスの最後に、アカウントを持つ各ユーザーには、Microsoft 365 メールボックスがあります。 '
ms.openlocfilehash: 88c83b7163bfa6d389995704595d80458ddc8198
ms.sourcegitcommit: ff1d21fe5eb8eba7a65d250aa37aadc8f503a10a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2020
ms.locfileid: "44699244"
---
# <a name="add-several-users-at-the-same-time-to-microsoft-365---admin-help"></a><span data-ttu-id="c12b6-105">Microsoft 365 に同時に複数のユーザーを追加する-管理者ヘルプ</span><span class="sxs-lookup"><span data-stu-id="c12b6-105">Add several users at the same time to Microsoft 365 - Admin Help</span></span>

<span data-ttu-id="c12b6-p102">チームの各ユーザーは、サインインして Microsoft 365 サービス (電子メールや Office など) にアクセスできるようにするために、ユーザーアカウントを必要とします。多数のユーザーがいる場合は、Excel ワークシートまたは CSV 形式で保存されたその他のファイルから、すべてのアカウントを一度に追加できます。[CSV 形式がわからない](add-several-users-at-the-same-time.md#__toc316652088)場合</span><span class="sxs-lookup"><span data-stu-id="c12b6-p102">Each person on your team needs a user account before they can sign in and access Microsoft 365 services, such as email and Office. If you have a lot of people, you can add their accounts all at once from an Excel spreadsheet or other file saved in CSV format. [Not sure what CSV format is?](add-several-users-at-the-same-time.md#__toc316652088)</span></span>
  
> [!NOTE] 
> <span data-ttu-id="c12b6-109">新しい Microsoft 365 管理センターを利用していない場合、[ホーム] ページの上部にある [**新しい管理センターをお試しください**] の切り替えを選択して有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="c12b6-109">If you're not using the new Microsoft 365 admin center, you can turn it on by selecting the **Try the new admin center** toggle located at the top of the Home page.</span></span>

## <a name="add-multiple-users-in-the-microsoft-365-admin-center"></a><span data-ttu-id="c12b6-110">Microsoft 365 管理センターで複数のユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="c12b6-110">Add multiple users in the Microsoft 365 admin center</span></span>

1. <span data-ttu-id="c12b6-111">職場または学校のアカウントを使用して、Microsoft 365 にサインインします。</span><span class="sxs-lookup"><span data-stu-id="c12b6-111">Sign in to Microsoft 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="c12b6-112">管理センターで、[**ユーザー**] \> [**アクティブなユーザー**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="c12b6-112">In the admin center, choose **Users** \> **Active users**.</span></span>

3. <span data-ttu-id="c12b6-113">[**複数ユーザーの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c12b6-113">Select **Add multiple users**.</span></span>

4. <span data-ttu-id="c12b6-114">省略可能ですが、[**複数のユーザーのインポート**] パネルでは、サンプル CSV ファイルをサンプル データ入りまたはなしでダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="c12b6-114">On the **Import multiple users** panel, you can optionally download a sample CSV file with or without sample data filled in.</span></span> 
    
    <span data-ttu-id="c12b6-115">スプレッドシートには、サンプルと **まったく同じ列見出し** が含まれている必要があります (ユーザー名、名、など)。テンプレートを使用する場合は、メモ帳などのテキスト編集ツールでテンプレートを開き、1 行目のすべてのデータをそのままにして実際のデータを 2 行目以降にのみ入力することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="c12b6-115">Your spreadsheet needs to include the **exact same column headings** as the sample one (User Name, First Name, etc...). If you use the template, open it in a text editing tool, like Notepad, and consider leaving all the data in row 1 alone, and only entering data in rows 2 and below.</span></span> 
    
    <span data-ttu-id="c12b6-116">スプレッドシートには、各ユーザーのユーザー名 (bob@contoso.com など) と表示名 (Bob Kelly など) の値を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="c12b6-116">Your spreadsheet also needs to include values for the user name (like bob@contoso.com) and a display name (like Bob Kelly) for each user.</span></span> 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. <span data-ttu-id="c12b6-117">ボックスにファイル パスを入力するか、[**参照**] を選択して CSV ファイルの場所を参照し、[**確認**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="c12b6-117">Enter a file path into the box, or choose **Browse** to browse to the CSV file location, then choose **Verify**.</span></span>
  
    <span data-ttu-id="c12b6-p103">ファイルに問題がある場合は、パネルにその問題が表示されます。ログ ファイルをダウンロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c12b6-p103">If there are problems with the file, the problem is displayed in the panel. You can also download a log file.</span></span>
    
5. <span data-ttu-id="c12b6-120">[**ユーザー オプションの設定**] ダイアログで、サインイン状態を設定し、すべてのユーザーに割り当てられる製品ライセンスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c12b6-120">On the **Set user options** dialog you can set the sign-in status and choose the product license that will be assigned to all users.</span></span> 
    
6. <span data-ttu-id="c12b6-121">[**結果の表示**] ダイアログで、結果を自分や他のユーザーに送信するかどうかを選択できます (パスワードはプレーン テキストとなります)。作成されたユーザーの数も表示されます。新規ユーザーに割り当てるライセンスを追加購入することもできます。</span><span class="sxs-lookup"><span data-stu-id="c12b6-121">On the **View your result** dialog you can choose to send the results to either yourself or other users (passwords will be in plain text) and you can see how many users were created, and if you need to purchase more licenses to assign to some of the new users.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="c12b6-122">次の手順</span><span class="sxs-lookup"><span data-stu-id="c12b6-122">Next steps</span></span>
<span data-ttu-id="c12b6-123"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="c12b6-123"><a name="bk_preview"> </a></span></span>

- <span data-ttu-id="c12b6-124">これらのユーザーはアカウントを所有しているので、 [Microsoft 365 または Office 2016 を PC または Mac にダウンロードしてインストールまたは再](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658)インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c12b6-124">Now that these people have accounts, they need to [Download and install or reinstall Microsoft 365 or Office 2016 on a PC or Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658).</span></span> <span data-ttu-id="c12b6-125">チームの各ユーザーは、最大5台の Pc または Mac に Microsoft 365 をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="c12b6-125">Each person on your team can install Microsoft 365 on up to 5 PCs or Macs.</span></span> 
    
- <span data-ttu-id="c12b6-126">各ユーザーは、iPhone、iPad、Android のスマートフォンやタブレットなどの[モバイル デバイスで Office アプリとメールをセットアップ](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f)でき、最大 5 台のタブレットと 5 台の スマートフォンでセットアップを行えます。</span><span class="sxs-lookup"><span data-stu-id="c12b6-126">Each person can also [Set up Office apps and email on a mobile device](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f) on up to 5 tablets and 5 phones, such as iPhones, iPads, and Android phones and tablets.</span></span> <span data-ttu-id="c12b6-127">こうすることで、ユーザーはどこからでも Office ファイルを編集できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c12b6-127">This way they can edit Office files from anywhere.</span></span> 
    
    <span data-ttu-id="c12b6-128">セットアップ手順のエンドツーエンドのリストについては、「 [Microsoft 365 for business を](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)セットアップする」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c12b6-128">See [Set up Microsoft 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa) for an end-to-end list of the setup steps.</span></span> 
    
## <a name="more-information-about-how-to-add-users-to-microsoft-365"></a><span data-ttu-id="c12b6-129">Microsoft 365 へのユーザーの追加方法に関する詳細情報</span><span class="sxs-lookup"><span data-stu-id="c12b6-129">More information about how to add users to Microsoft 365</span></span>
<span data-ttu-id="c12b6-130"><a name="bk_preview"> </a></span><span class="sxs-lookup"><span data-stu-id="c12b6-130"><a name="bk_preview"> </a></span></span>

### <a name="not-sure-what-csv-format-is"></a><span data-ttu-id="c12b6-131">CSV 形式とは。</span><span class="sxs-lookup"><span data-stu-id="c12b6-131">Not sure what CSV format is?</span></span>
<span data-ttu-id="c12b6-132"><a name="__toc316652088"> </a></span><span class="sxs-lookup"><span data-stu-id="c12b6-132"><a name="__toc316652088"> </a></span></span>

<span data-ttu-id="c12b6-p106">CSV ファイルは、コンマで区切られた値を含むファイルです。 テキスト エディターまたは Excel などのスプレッドシート プログラムを使って、このようなファイルを作成または編集することができます。</span><span class="sxs-lookup"><span data-stu-id="c12b6-p106">A CSV file is a file with comma separated values. You can create or edit a file like this with any text editor or spreadsheet program, such as Excel.</span></span>
  
<span data-ttu-id="c12b6-p107">[このサンプルスプレッドシート](https://www.microsoft.com/download/details.aspx?id=45485)は、開始点としてダウンロードできます。Microsoft 365 では、最初の行に列見出しが必要なので、他の項目には置き換えないでください。</span><span class="sxs-lookup"><span data-stu-id="c12b6-p107">You can download [this sample spreadsheet](https://www.microsoft.com/download/details.aspx?id=45485) as a starting point. Remember that Microsoft 365 requires column headings in the first row so don't replace them with something else.</span></span> 
  
<span data-ttu-id="c12b6-137">新しい名前でファイルを保存し、CSV 形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="c12b6-137">Save the file with a new name, and specify CSV format.</span></span>
  
![Excel でファイルを CSV 形式で保存する方法を示した画像](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
<span data-ttu-id="c12b6-p108">ファイルを保存するときに、CSV 形式でファイルを保存すると、ブックの一部の機能が失われるというメッセージが表示されることがあります。 このメッセージは問題ありません。 [ **はい**] をクリックして続けます。</span><span class="sxs-lookup"><span data-stu-id="c12b6-p108">When you save the file, you'll probably get a prompt that some features in your workbook will be lost if you save the file in CSV format. This is okay. Click **Yes** to continue.</span></span> 
  
![CSV 形式でファイルを保存するかどうかを確認する Excel メッセージの画像](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a><span data-ttu-id="c12b6-143">スプレッドシートの書式設定のヒント</span><span class="sxs-lookup"><span data-stu-id="c12b6-143">Tips for formatting your spreadsheet</span></span>
<span data-ttu-id="c12b6-144"><a name="__toc314595848"> </a></span><span class="sxs-lookup"><span data-stu-id="c12b6-144"><a name="__toc314595848"> </a></span></span>

- <span data-ttu-id="c12b6-p109">**サンプルのスプレッドシートと同じ列見出しが必要な場合**うん。サンプルのスプレッドシートには、最初の行の列見出しが含まれています。これらの見出しは必須です。Microsoft 365 に追加するユーザーごとに、見出しの下に行を作成します。列見出しのいずれかを追加、変更、または削除すると、Microsoft 365 はファイル内の情報からユーザーを作成できなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="c12b6-p109">**Do I need the same column headings as in the sample spreadsheet?** Yes. The sample spreadsheet contains column headings in the first row. These headings are required. For each user you want to add to Microsoft 365, create a row under the heading. If you add, change, or delete any of the column headings, Microsoft 365 might not be able to create users from the information in the file.</span></span> 
    
- <span data-ttu-id="c12b6-p110">**各ユーザーに必要な情報が揃っていない場合はどのようになりますか?** ユーザー名と表示名は必須で、この情報がないと新しいユーザーは追加できません。FAX 番号などの他の情報が一部欠けている場合は、フィールドが空白であることを示すために、スペースに加えてコンマを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="c12b6-p110">**What if I don't have all the information required for each user?** The user name and display name are required, and you cannot add a new user without this information. If you don't have some of the other information, such as the fax, you can use a space plus a comma to indicate that the field should remain blank.</span></span> 
    
- <span data-ttu-id="c12b6-p111">**スプレッドシートのサイズを小さくすることはできますか。** スプレッドシートには、少なくとも2つの行が必要です。1つは列見出し (ユーザーデータ列ラベル)、もう1つはユーザー用です。251行を超える行を設定することはできません。250を超えるユーザーをインポートする必要がある場合は、複数のスプレッドシートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c12b6-p111">**How small or large can the spreadsheet be?** The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet.</span></span> 
    
- <span data-ttu-id="c12b6-p112">**どの言語を使用できますか?** ワークシートを作成するときに、ユーザーデータの列ラベルを任意の言語または文字で入力できますが、サンプルで示されているように、ラベルの順序を変更する必要はありません。その後、任意の言語または文字を使用してフィールドにエントリを作成し、Unicode または UTF-8 形式でファイルを保存できます。</span><span class="sxs-lookup"><span data-stu-id="c12b6-p112">**What languages can I use?** When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format.</span></span> 
    
- <span data-ttu-id="c12b6-p113">**異なる国や地域のユーザーを追加する場合はどうですか?** 領域ごとに別のスプレッドシートを作成します。 スプレッドシートごとにユーザーの一括追加ウィザードの手順を実行し、処理中のファイルに含まれるすべてのユーザーを 1 つの場所にまとめるようにします。</span><span class="sxs-lookup"><span data-stu-id="c12b6-p113">**What if I'm adding users from different countries or regions?** Create a separate spreadsheet for each area. You'll need to step through the Bulk add users wizard which each spreadsheet, giving a single location of all users included in the file that you're working with.</span></span> 
    
- <span data-ttu-id="c12b6-p114">**使用できる文字数に制限はありますか?** 次の表は、サンプルのスプレッドシート内のユーザーデータの列ラベルと、それぞれの最大文字数を示しています。</span><span class="sxs-lookup"><span data-stu-id="c12b6-p114">**Is there a limit to the number of characters I can use?** The following table shows the user data column labels and the maximum character length for each in the sample spreadsheet.</span></span> 
    
|<span data-ttu-id="c12b6-167">**ユーザー データの 列 ラベル**</span><span class="sxs-lookup"><span data-stu-id="c12b6-167">**User data column label**</span></span>|<span data-ttu-id="c12b6-168">**最大文字数**</span><span class="sxs-lookup"><span data-stu-id="c12b6-168">**Maximum character length**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c12b6-169">ユーザー名 (必須)</span><span class="sxs-lookup"><span data-stu-id="c12b6-169">User Name (Required)</span></span>  <br/> |<span data-ttu-id="c12b6-p115">79 name@domain の形式で、アットマーク (@) を \<extension\> 含みます。ユーザーのエイリアスは、50文字を超えることはできず、ドメイン名は48文字を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="c12b6-p115">79 including the at sign (@), in the format name@domain.\<extension\>. The user's alias cannot exceed 50 characters, and the domain name cannot exceed 48 characters.  </span></span><br/> |
|<span data-ttu-id="c12b6-172">名</span><span class="sxs-lookup"><span data-stu-id="c12b6-172">First Name</span></span>  <br/> |<span data-ttu-id="c12b6-173">64</span><span class="sxs-lookup"><span data-stu-id="c12b6-173">64</span></span>  <br/> |
|<span data-ttu-id="c12b6-174">姓</span><span class="sxs-lookup"><span data-stu-id="c12b6-174">Last Name</span></span>  <br/> |<span data-ttu-id="c12b6-175">64</span><span class="sxs-lookup"><span data-stu-id="c12b6-175">64</span></span>  <br/> |
|<span data-ttu-id="c12b6-176">表示名 (必須)</span><span class="sxs-lookup"><span data-stu-id="c12b6-176">Display Name (required)</span></span>  <br/> |<span data-ttu-id="c12b6-177">256</span><span class="sxs-lookup"><span data-stu-id="c12b6-177">256</span></span>  <br/> |
|<span data-ttu-id="c12b6-178">役職</span><span class="sxs-lookup"><span data-stu-id="c12b6-178">Job Title</span></span>  <br/> |<span data-ttu-id="c12b6-179">64</span><span class="sxs-lookup"><span data-stu-id="c12b6-179">64</span></span>  <br/> |
|<span data-ttu-id="c12b6-180">部署</span><span class="sxs-lookup"><span data-stu-id="c12b6-180">Department</span></span>  <br/> |<span data-ttu-id="c12b6-181">64</span><span class="sxs-lookup"><span data-stu-id="c12b6-181">64</span></span>  <br/> |
|<span data-ttu-id="c12b6-182">事務所番号</span><span class="sxs-lookup"><span data-stu-id="c12b6-182">Office Number</span></span>  <br/> |<span data-ttu-id="c12b6-183">128</span><span class="sxs-lookup"><span data-stu-id="c12b6-183">128</span></span>  <br/> |
|<span data-ttu-id="c12b6-184">会社電話</span><span class="sxs-lookup"><span data-stu-id="c12b6-184">Office Phone</span></span>  <br/> |<span data-ttu-id="c12b6-185">64</span><span class="sxs-lookup"><span data-stu-id="c12b6-185">64</span></span>  <br/> |
|<span data-ttu-id="c12b6-186">携帯電話</span><span class="sxs-lookup"><span data-stu-id="c12b6-186">Mobile Phone</span></span>  <br/> |<span data-ttu-id="c12b6-187">64</span><span class="sxs-lookup"><span data-stu-id="c12b6-187">64</span></span>  <br/> |
|<span data-ttu-id="c12b6-188">FAX</span><span class="sxs-lookup"><span data-stu-id="c12b6-188">Fax</span></span>  <br/> |<span data-ttu-id="c12b6-189">64</span><span class="sxs-lookup"><span data-stu-id="c12b6-189">64</span></span>  <br/> |
|<span data-ttu-id="c12b6-190">番地</span><span class="sxs-lookup"><span data-stu-id="c12b6-190">Address</span></span>  <br/> |<span data-ttu-id="c12b6-191">1023</span><span class="sxs-lookup"><span data-stu-id="c12b6-191">1023</span></span>  <br/> |
|<span data-ttu-id="c12b6-192">市区町村</span><span class="sxs-lookup"><span data-stu-id="c12b6-192">City</span></span>  <br/> |<span data-ttu-id="c12b6-193">128</span><span class="sxs-lookup"><span data-stu-id="c12b6-193">128</span></span>  <br/> |
|<span data-ttu-id="c12b6-194">都道府県</span><span class="sxs-lookup"><span data-stu-id="c12b6-194">State or Province</span></span>  <br/> |<span data-ttu-id="c12b6-195">128</span><span class="sxs-lookup"><span data-stu-id="c12b6-195">128</span></span>  <br/> |
|<span data-ttu-id="c12b6-196">郵便番号</span><span class="sxs-lookup"><span data-stu-id="c12b6-196">ZIP or Postal Code</span></span>  <br/> |<span data-ttu-id="c12b6-197">40</span><span class="sxs-lookup"><span data-stu-id="c12b6-197">40</span></span>  <br/> |
|<span data-ttu-id="c12b6-198">国または地域</span><span class="sxs-lookup"><span data-stu-id="c12b6-198">Country or Region</span></span>  <br/> |<span data-ttu-id="c12b6-199">128</span><span class="sxs-lookup"><span data-stu-id="c12b6-199">128</span></span>  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-microsoft-365"></a><span data-ttu-id="c12b6-200">引き続き Microsoft 365 にユーザーを追加するときに問題が発生しますか?</span><span class="sxs-lookup"><span data-stu-id="c12b6-200">Still having problems when adding users to Microsoft 365?</span></span>

- <span data-ttu-id="c12b6-p116">**スプレッドシートの形式が正しいかどうか慎重にチェックしてください。** サンプル ファイル内の見出しと一致しているか、列見出しをチェックします。文字数の制限に従い、各フィールドがカンマで区切られるようにします。</span><span class="sxs-lookup"><span data-stu-id="c12b6-p116">**Double-check that the spreadsheet is formatted correctly.** Check the column headings to make sure they match the headings in the sample file. Make sure you're following the rules for character lengths and that each field is separated by a comma.</span></span> 
    
- <span data-ttu-id="c12b6-204">**Microsoft 365 で新しいユーザーがすぐに表示されない場合は、数分待機してください。**</span><span class="sxs-lookup"><span data-stu-id="c12b6-204">**If you don't see the new users in Microsoft 365 right away, wait a few minutes.**</span></span> <span data-ttu-id="c12b6-205">Microsoft 365 のすべてのサービスに変更が加えられるのに少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c12b6-205">It can take a little while for changes to go across all the services in Microsoft 365.</span></span> 
    
## <a name="related-articles"></a><span data-ttu-id="c12b6-206">関連記事</span><span class="sxs-lookup"><span data-stu-id="c12b6-206">Related articles</span></span>

[<span data-ttu-id="c12b6-207">Microsoft 365 にユーザーを個別にまたは一括して追加する</span><span class="sxs-lookup"><span data-stu-id="c12b6-207">Add users individually or in bulk to Microsoft 365</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)




