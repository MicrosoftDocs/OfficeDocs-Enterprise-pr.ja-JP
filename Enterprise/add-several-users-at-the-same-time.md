---
title: 同時に複数のユーザーを Office 365 に追加する - 管理者ヘルプ
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
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
ms.openlocfilehash: 864bdf788b0beefce49a53382795d522114aad5d
ms.sourcegitcommit: 23c8781d1a2b0472612c3a2cb6e5d13edb03e236
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2019
ms.locfileid: "38702218"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a>同時に複数のユーザーを Office 365 に追加する - 管理者ヘルプ

メールや Office などの Office 365 サービスにサインインしてアクセスするには、チームの各メンバーにユーザー アカウントが必要です。 ユーザー数が多い場合、Excel のスプレッドシートまたは CSV 形式で保存された他のファイルから、ユーザー アカウントを一括で追加することができます。 [CSV 書式の定義](add-several-users-at-the-same-time.md#__toc316652088)
  
> [!NOTE] 
> 新しい Microsoft 365 管理センターを利用していない場合、[ホーム] ページの上部にある [**新しい管理センターをお試しください**] の切り替えを選択して有効にすることができます。

## <a name="add-multiple-users-to-office-365-in-the-microsoft-365-admin-center"></a>Microsoft 365 管理センターの Office 365 に複数のユーザーを追加する

1. 職場または学校のアカウントを使用して、Office 365 にサインインします。 
    
2. In the admin center, choose **Users** \> **Active users**.

3. [**複数のユーザーを追加**] を選択します。

4. [ **複数のユーザーをインポート**] パネルで、サンプルの CSV ファイルをサンプル データがある状態、またはない状態でダウンロードできます。 
    
    スプレッドシートには、サンプルと **まったく同じ列見出し** が含まれている必要があります (ユーザー名、名、など)。テンプレートを使用する場合は、メモ帳などのテキスト編集ツールでテンプレートを開き、1 行目のすべてのデータをそのままにして実際のデータを 2 行目以降にのみ入力することを検討してください。 
    
    スプレッドシートには、各ユーザーのユーザー名 (bob@contoso.com など) と表示名 (Bob Kelly など) の値を含める必要があります。 
    
  ```
  User Name,First Name,Last Name,Display Name,Job Title,Department,Office Number,Office Phone,Mobile Phone,Fax,Address,City,State or Province,ZIP or Postal Code,Country or Region
  chris@contoso.com,Chris,Green,Chris Green,IT Manager,Information Technology,123451,123-555-1211,123-555-6641,123-555-9821,1 Microsoft way,Redmond,Wa,98052,United States
  ben@contoso.com,Ben,Andrews,Ben Andrews,IT Manager,Information Technology,123452,123-555-1212,123-555-6642,123-555-9822,1 Microsoft way,Redmond,Wa,98052,United States
  david@contoso.com,David,Longmuir,David Longmuir,IT Manager,Information Technology,123453,123-555-1213,123-555-6643,123-555-9823,1 Microsoft way,Redmond,Wa,98052,United States
  cynthia@contoso.com,Cynthia,Carey,Cynthia Carey,IT Manager,Information Technology,123454,123-555-1214,123-555-6644,123-555-9824,1 Microsoft way,Redmond,Wa,98052,United States
  melissa@contoso.com,Melissa,MacBeth,Melissa MacBeth,IT Manager,Information Technology,123455,123-555-1215,123-555-6645,123-555-9825,1 Microsoft way,Redmond,Wa,98052,United States
  
  ```

5. ボックスにファイル パスを入力するか、[ **参照**] を選択して CSV ファイルの場所を参照し、[ **確認**] を選びます。
  
    ファイルに問題がある場合は、パネルにその問題が表示されます。ログ ファイルをダウンロードすることもできます。
    
5. [ **ユーザー オプションの設定**] ダイアログで、サインイン状態を設定し、すべてのユーザーに割り当てられる製品ライセンスを選択できます。 
    
6. [ **結果の表示**] ダイアログで、結果を自分や他のユーザーに送信するかどうかを選択できます (パスワードはプレーン テキストとなります)。作成されたユーザーの数も表示されます。新規ユーザーに割り当てるライセンスを追加購入することもできます。 
    
## <a name="watch-the-video"></a>ビデオの視聴
<a name="bk_preview"> </a>

 ユーザーの一括追加方法についての短いビデオを確認してください。 
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/f4e7f161-8ae6-4264-a429-9297b539a8de?autoplay=false]
  
## <a name="next-steps"></a>次の手順
<a name="bk_preview"> </a>

- これらのユーザーはアカウントを所有しているので、 [office 365 または office 2016 を PC または Mac にダウンロードしてインストールまたは再](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658)インストールする必要があります。 チームのメンバー 1 人につき、最大 5 台の PC または Mac に Office 365 をインストールできます。 
    
- 各ユーザーは、1つの[モバイルデバイスで Office アプリとメール](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f)をセットアップすることもできます。これには、Iphones、Ipad、Android の携帯電話、タブレットなどの最大5台のタブレットと5台の電話機があります。 このようにすると、どこにいても Office のファイルを編集できます。 
    
    セットアップ手順のエンドツーエンドのリストについては、「 [Office 365 for business の](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)セットアップ」を参照してください。 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a>Office 365 へのユーザー追加方法に関するその他の情報
<a name="bk_preview"> </a>

### <a name="not-sure-what-csv-format-is"></a>CSV 書式の定義
<a name="__toc316652088"> </a>

CSV ファイルは、コンマで区切られた値を含むファイルです。 テキスト エディターまたは Excel などのスプレッドシート プログラムを使って、このようなファイルを作成または編集することができます。
  
出発点として、[このサンプル スプレッドシート](https://www.microsoft.com/download/details.aspx?id=45485)をダウンロードして使うことができます。Office 365 には 1 行目の列見出しが必要なので、別のテキストで置き換えないでください。 
  
新しい名前でファイルを保存し、CSV 形式を指定します。
  
![Excel でファイルを CSV 形式で保存する方法を示した画像](media/35a86ebe-63ab-4b4d-9a92-e177de33ebae.png)
  
ファイルを保存するときに、CSV 形式でファイルを保存すると、ブックの一部の機能が失われるというメッセージが表示されることがあります。 このメッセージは問題ありません。 [ **はい**] をクリックして続けます。 
  
![CSV 形式でファイルを保存するかどうかを確認する Excel メッセージの画像](media/51032a81-690c-45ef-bfc5-09ea7f790e98.png)
  
### <a name="tips-for-formatting-your-spreadsheet"></a>スプレッドシートの書式設定のヒント
<a name="__toc314595848"> </a>

- **サンプル スプレッドシートと同じ列見出しにする必要はありますか?** はい。サンプル スプレッドシートの 1 行目には列見出しが含まれています。列見出しは必須です。見出しの下に、Office 365 に追加するユーザーごとに 1 行を作成します。列見出しのいずれかを追加、変更、または削除すると、Office 365 でファイル内の情報からユーザーを作成できなくなる可能性があります。 
    
- **各ユーザーに必要な情報が揃っていない場合はどのようになりますか?** ユーザー名と表示名は必須で、この情報がないと新しいユーザーは追加できません。FAX 番号などの他の情報が一部欠けている場合は、フィールドが空白であることを示すために、スペースに加えてコンマを使用することができます。 
    
- ** How small or large can the spreadsheet be? ** The spreadsheet must have at least two rows. One is for the column headings (the user data column label) and one for the user. You cannot have more than 251 rows. If you need to import more than 250 users, you can create more than one spreadsheet. 
    
- ** What languages can I use? ** When you create your spreadsheet, you can enter user data column labels in any language or characters, but you must not change the order of the labels, as shown in the sample. You can then make entries into the fields, using any language or characters, and save your file in a Unicode or UTF-8 format. 
    
- **異なる国や地域のユーザーを追加する場合はどうですか?** 領域ごとに別のスプレッドシートを作成します。 スプレッドシートごとにユーザーの一括追加ウィザードの手順を実行し、処理中のファイルに含まれるすべてのユーザーを 1 つの場所にまとめるようにします。 
    
- **使用できる文字数に制限はありますか?** 次の表は、サンプルのスプレッドシート内のユーザーデータの列ラベルと、それぞれの最大文字数を示しています。 
    
|**ユーザー データの 列 ラベル**|**最大文字数**|
|:-----|:-----|
|ユーザー名 (必須)  <br/> |name@domain.\<extension\> という形式で、@ 記号を含めて 79 文字です。 ユーザーの別名は 30 文字を超えることはできず、ドメイン名は 48 文字を超えることはできません。  <br/> |
|名  <br/> |64  <br/> |
|姓  <br/> |64  <br/> |
|表示名 (必須)  <br/> |256  <br/> |
|役職  <br/> |64  <br/> |
|部署  <br/> |64  <br/> |
|事務所番号  <br/> |128  <br/> |
|会社電話  <br/> |64  <br/> |
|携帯電話  <br/> |64  <br/> |
|FAX  <br/> |64  <br/> |
|番地  <br/> |1023  <br/> |
|市区町村  <br/> |128  <br/> |
|都道府県  <br/> |128  <br/> |
|郵便番号  <br/> |40  <br/> |
|国または地域  <br/> |128  <br/> |
   
### <a name="still-having-problems-when-adding-users-to-office-365"></a>Office 365 にユーザーを追加するときの問題がまだ解決しない場合

- **スプレッドシートの形式が正しいかどうか慎重にチェックしてください。** サンプル ファイル内の見出しと一致しているか、列見出しをチェックします。文字数の制限に従い、各フィールドがカンマで区切られるようにします。 
    
- **Office 365 で新しいユーザーがすぐに表示されない場合は、数分待機してください。** Office 365 のすべてのサービスに変更が加えられるのに少し時間がかかる場合があります。 
    
