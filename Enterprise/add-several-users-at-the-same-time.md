---
title: 同時に複数のユーザーを Office 365 に追加する - 管理者ヘルプ
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
description: 'スプレッドシート内またはその他の CSV 形式ファイル内の一覧から複数のユーザーを 一般法人向け Office 365 に追加する方法を説明します。 Office 365 にアカウントを追加する方法に関する YouTube 上のビデオをご覧ください。 このプロセスが終了すると、アカウントを持つそれぞれのユーザーに Office 365 メールボックスが付与されます。 '
ms.openlocfilehash: 9c24c52e280fcb316d9e77ea613a1812a235c2d2
ms.sourcegitcommit: c2f90c022ca323736d9c43929b5681c3f8db0e6f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "43901210"
---
# <a name="add-several-users-at-the-same-time-to-office-365---admin-help"></a>同時に複数のユーザーを Office 365 に追加する - 管理者ヘルプ

メールや Office などの Office 365 サービスにサインインしてアクセスするには、チームの各メンバーにユーザー アカウントが必要です。 ユーザー数が多い場合、Excel のスプレッドシートまたは CSV 形式で保存された他のファイルから、ユーザー アカウントを一括で追加することができます。 [CSV 書式の定義](add-several-users-at-the-same-time.md#__toc316652088)
  
> [!NOTE] 
> 新しい Microsoft 365 管理センターを利用していない場合、[ホーム] ページの上部にある [**新しい管理センターをお試しください**] の切り替えを選択して有効にすることができます。

## <a name="add-multiple-users-to-office-365-in-the-microsoft-365-admin-center"></a>Microsoft 365 管理センターで Office 365 に複数のユーザーを追加する

1. 職場または学校のアカウントを使用して Office 365 にサインインします。 
    
2. 管理センターで、[**ユーザー**] \> [**アクティブなユーザー**] の順に選択します。

3. [**複数ユーザーの追加**] を選択します。

4. 省略可能ですが、[**複数のユーザーのインポート**] パネルでは、サンプル CSV ファイルをサンプル データ入りまたはなしでダウンロードできます。 
    
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

5. ボックスにファイル パスを入力するか、[**参照**] を選択して CSV ファイルの場所を参照し、[**確認**] を選びます。
  
    ファイルに問題がある場合は、パネルにその問題が表示されます。ログ ファイルをダウンロードすることもできます。
    
5. [**ユーザー オプションの設定**] ダイアログで、サインイン状態を設定し、すべてのユーザーに割り当てられる製品ライセンスを選択できます。 
    
6. [**結果の表示**] ダイアログで、結果を自分や他のユーザーに送信するかどうかを選択できます (パスワードはプレーン テキストとなります)。作成されたユーザーの数も表示されます。新規ユーザーに割り当てるライセンスを追加購入することもできます。 

## <a name="next-steps"></a>次の手順
<a name="bk_preview"> </a>

- これで、これらのユーザーにアカウントが付与されました。次に、これらのユーザーは [Office 365 または Office 2016 を PC または Mac にダウンロードしてインストールまたは再インストールする](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658)必要があります。 チームの各ユーザーは、最大 5 台の PC または Mac に Office 365 をインストールできます。 
    
- 各ユーザーは、iPhone、iPad、Android のスマートフォンやタブレットなどの[モバイル デバイスで Office アプリとメールをセットアップ](https://support.office.com/article/7dabb6cb-0046-40b6-81fe-767e0b1f014f)でき、最大 5 台のタブレットと 5 台の スマートフォンでセットアップを行えます。 こうすることで、ユーザーはどこからでも Office ファイルを編集できるようになります。 
    
    詳細なセットアップ手順については、「[一般法人向け Office 365 のセットアップ](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)」を参照してください。 
    
## <a name="more-information-about-how-to-add-users-to-office-365"></a>Office 365 にユーザーを追加する方法に関するその他の情報
<a name="bk_preview"> </a>

### <a name="not-sure-what-csv-format-is"></a>CSV 形式とは。
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
    
- **スプレッドシートのサイズを小さくすることはできますか。** スプレッドシートには、少なくとも2つの行が必要です。1つは列見出し (ユーザーデータ列ラベル)、もう1つはユーザー用です。251行を超える行を設定することはできません。250を超えるユーザーをインポートする必要がある場合は、複数のスプレッドシートを作成できます。 
    
- **どの言語を使用できますか?** ワークシートを作成するときに、ユーザーデータの列ラベルを任意の言語または文字で入力できますが、サンプルで示されているように、ラベルの順序を変更する必要はありません。その後、任意の言語または文字を使用してフィールドにエントリを作成し、Unicode または UTF-8 形式でファイルを保存できます。 
    
- **異なる国や地域のユーザーを追加する場合はどうですか?** 領域ごとに別のスプレッドシートを作成します。 スプレッドシートごとにユーザーの一括追加ウィザードの手順を実行し、処理中のファイルに含まれるすべてのユーザーを 1 つの場所にまとめるようにします。 
    
- **使用できる文字数に制限はありますか?** 次の表は、サンプルのスプレッドシート内のユーザーデータの列ラベルと、それぞれの最大文字数を示しています。 
    
|**ユーザー データの 列 ラベル**|**最大文字数**|
|:-----|:-----|
|ユーザー名 (必須)  <br/> |79 name@domain の形式で、アットマーク (@) を含みます。\<拡張子\>。ユーザーのエイリアスは、50文字を超えることはできず、ドメイン名は48文字を超えることはできません。  <br/> |
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
    
- **新しいユーザーが Office 365 にすぐに表示されない場合は、数分間お待ちください。** Office 365 のすべてのサービスに変更が行き渡るまでに少し時間がかかる場合があります。 
    
## <a name="related-articles"></a>関連記事

[Office 365 にユーザーを個別に、またはまとめて追加する](https://docs.microsoft.com/office365/admin/add-users/add-users)




