---
title: Office 365 ラベルと DLP による SharePoint ファイルの保護
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: '概要: 情報保護のレベルが多様な SharePoint Online チーム サイトに、Office 365 ラベルとデータ損失防止 (DLP) ポリシーを適用します。'
ms.openlocfilehash: 52617e43f5c1bcb2ab958e751734a2f948ceba37
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a>Office 365 ラベルと DLP による SharePoint ファイルの保護

 **概要:** 情報保護のレベルが多様な SharePoint Online チーム サイトに、Office 365 ラベルとデータ損失防止 (DLP) ポリシーを適用します。
  
この記事にある手順を使用して、ベースライン、機密、および高機密の SharePoint Online チーム サイト用の Office 365 ラベルおよび DLP ポリシーを設計および展開します。これらの 3 つの層の保護について詳しくは、「[Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md)」を参照してください。
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a>SharePoint Online サイトの Office 365 ラベル

Office 365 のラベルを作成し、SharePoint Online チーム サイトにラベルを割り当てるためのフェーズは 3 つあります。
  
### <a name="phase-1-determine-the-office-365-label-names"></a>フェーズ 1: Office 365 ラベル名を決定する

このフェーズでは、SharePoint Online チーム サイトに適用される 4 レベルの情報保護用に、Office 365 ラベルの名前を決定します。 次の表は、各レベルに推奨される名前の一覧です。
  
|**SharePoint Online チーム サイトの保護レベル**|**ラベル名**|
|:-----|:-----|
|ベースライン - パブリック  <br/> |内部パブリック  <br/> |
|ベースライン - プライベート  <br/> |Kirkland  <br/> |
|機密  <br/> |機密  <br/> |
|非常に機密性の高い社外秘  <br/> |非常に機密性の高い社外秘  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a>フェーズ 2: Office 365 のラベルを作成する

このフェーズでは、さまざまなレベルの情報保護について決定したラベルを作成し、発行します。
  
ラベルを作成するには、Office 365 管理センターまたは Microsoft PowerShell を使用できます。
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a>Office 365 管理センターで Office 365 のラベルを作成する

1. セキュリティ管理者または会社管理者のロールのアカウントを使用して、Office 365 ポータルにサインインします。ヘルプを表示するには、「[Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。
    
2. **[Microsoft Office Home]** タブで、**[管理者]** タイルをクリックします。
    
3. ブラウザーの新しい **[Office 管理者センター]** タブで、**[管理センター] > [セキュリティとコンプライアンス]** をクリックします。
    
4. ブラウザーの新しい **[ホーム – セキュリティとコンプライアンス]** タブをクリックして、**[分類] > [ラベル]** をクリックします。
    
5. **[ホーム] > [ラベル]** ウィンドウで、**[ラベルの作成]** をクリックします。
    
6. **[ラベルに名前をつける]** ウィンドウで、ラベルの名前を入力して、**[次へ]** をクリックします。
    
7. **[ラベル設定]** ウィンドウで、**[次へ]** をクリックします。
    
8. **[設定の確認]** ウィンドウで、**[このラベルを作成する]** をクリックして、**[閉じる]** をクリックします。
    
9. 追加ラベルについて手順 5 から 8 を繰り返します。
    
### <a name="create-office-365-labels-with-powershell"></a>PowerShell で Office 365 のラベルを作成する

1. [リモート PowerShell を使用して Office 365 セキュリティ &amp; コンプライアンス センターに接続](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409)し、セキュリティ管理者ロールまたは会社の管理者ロールを持つアカウントの資格情報を指定します。
    
2. ラベル名の一覧を入力し、PowerShell コマンド プロンプトで次のコマンドを実行します。
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

次に、以下の手順で新しい Office 365 ラベルを発行します。
  
1. **[ホーム] > [ラベル]** ウィンドウの [セキュリティ &amp; コンプライアンス センター] で、**[ラベルの発行]** をクリックします。
    
2. **[発行するラベルを選択]** ウィンドウで、**[発行するラベルを選択]** をクリックします。
    
3. **[Choose labels]\(ラベルの選択\)** ウィンドウで、**[追加]** をクリックして 4 つのラベルをすべて選択します。
    
4. [ **完了**] をクリックします。
    
5. **[発行するラベルを選択]** ウィンドウで、 **[次へ]** をクリックします。
    
6. **[場所の選択]** ウィンドウで、**[次へ]** をクリックします。
    
7. **[ポリシーに名前をつける]** ウィンドウで、**[名前]** にラベルのセットの名前を入力し、**[次へ]** をクリックします。
    
8. **[設定の確認]** ウィンドウで、**[ラベルの発行]** をクリックして、**[閉じる]** をクリックします。
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a>フェーズ 3: SharePoint Online サイトに Office 365 ラベルを適用する

以下の手順で Office 365 ラベルを SharePoint Online チーム サイトのドキュメント フォルダーに適用します。
  
1. ブラウザーの **Microsoft Office ホーム**のタブで、**[SharePoint]** タイルをクリックします。
    
2. ブラウザーの新しい **SharePoint** タブで、Office 365 ラベルを割り当てる必要があるサイトをクリックします。
    
3. ブラウザーの新しい SharePoint サイト タブで、**[ドキュメント]** をクリックします。
    
4. 設定アイコンをクリックし、**[ライブラリの設定]** をクリックします。
    
5. **[権限と管理]** をクリックして、**[このライブラリ内の項目にラベルを適用]** をクリックします。
    
6. **[設定 - ラベルの適用]** で適切なラベルを選択し、**[保存]** をクリックします。
    
7. SharePoint Online サイトのタブを閉じます。
    
8. 手順 3 - 8 を繰り返して、その他の SharePoint Online サイトに Office 365 ラベルを割り当てます。
    
最終的な構成をここに示します。
  
![4 種類の SharePoint Online チーム サイト用の Office 365 ラベル。](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a>SharePoint Online サイトの DLP ポリシー

以下の手順で、SharePoint Online の機密チーム サイト上のドキュメントを組織外と共有するときにユーザーに通知する DLP ポリシーを構成します。
  
1. ブラウザーの **[Microsoft Office Home]** タブで、**[セキュリティとコンプライアンス]** タイルをクリックします。
    
2. ブラウザーの新しい **[セキュリティとコンプライアンス]** タブで、**[データ損失防止] > [ポリシー]** をクリックします。
    
3. **[データ損失防止]** ウィンドウで、 **[+ ポリシーの作成]** をクリックします。
    
4. **[テンプレートを使って開始するか、カスタム ポリシーを作成する]** ウィンドウで、**[カスタム]** をクリックして、**[次へ]** をクリックします。
    
5. **[ポリシーに名前をつける]** ウィンドウの **[名前]** に機密レベル DLP ポリシーの名前を入力して、**[次へ]** をクリックします。
    
6. **[場所の選択]** ウィンドウで、**[自分で特定の場所を選択する]** をクリックして、**[次へ]** をクリックします。
    
7. 場所の一覧で、 **Exchange メール**と **OneDrive アカウント**の場所を無効にし、 **[次へ]** をクリックします。
    
8. **[保護する機密性の高い情報の種類をカスタマイズする]** ウィンドウで、 **[編集]** をクリックします。
    
9. **[保護するコンテンツの種類を選択する]** ウィンドウのドロップダウン ボックスで **[追加]** をクリックしてから、 **[ラベル]** をクリックします。
    
10. **[ラベル]** ウィンドウで、 **[+ 追加]** をクリックして、 **[機密]** ラベルを選択し、 **[追加]** をクリックしてから、 **[完了]** をクリックします。
    
11. **[保護するコンテンツの種類を選択する]** ウィンドウで、 **[保存]** をクリックします。
    
12. **[Customize the types of sensitive info you want to protect]\(保護する機密情報の種類のカスタマイズ\)** ウィンドウで、**[次へ]** をクリックします。
    
13. **[What do you want to do if we detect sensitive info?]\(機密情報が検出された場合の処理\)** ウィンドウで、**[Customize the tip and email]\(ヒントと電子メールをカスタマイズする)** をクリックします。
    
14. **[Customize policy tips and email notifications]\(ポリシー ヒントと電子メール通知のカスタマイズ\)** ウィンドウで、**[Customize the policy tip text]\(ポリシー ヒントのテキストをカスタマイズする\)** をクリックします。
    
15. 次の内容をテキスト ボックスに入力するか、貼り付けます。
    
  - 組織外のユーザーと共有するには、ファイルをダウンロードしてから開きます。[ファイル]、[文書の保護]、[パスワードを使用して暗号化] の順にクリックし、強力なパスワードを指定します。別の電子メールまたはその他の通信手段でパスワードを送信します。
    
    あるいは、ファイルを共有する方法について組織外のユーザーに指示する独自のポリシー ヒントを入力するか、貼り付けます。
    
16. **[OK]** をクリックします。
    
17. **[機密性の高い情報が検出された場合に実行する操作]** ウィンドウで、 **[ユーザーが共有できないようにし、共有コンテンツへのアクセスを制限する]** チェックボックスをクリアしてから、 **[次へ]** をクリックします。
    
18. **[ポリシーを有効にしますか、または最初にテストしますか?]** ウィンドウで、 **[すぐ有効にします]** をクリックし、 **[次へ]** をクリックします。
    
19. **[設定の確認]** ウィンドウで、**[作成]** をクリックして、**[閉じる]** をクリックします。
    
機密 SharePoint Online チーム サイトの最終的な構成をここに示します。
  
![機密 Office 365 ラベルを使用している、独立した SharePoint Online チーム サイトの DLP ポリシー。](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
次に、以下の手順で、SharePoint Online の非常に機密性の高い社外秘チーム サイト上のドキュメントを組織外と共有するときにユーザーをブロックする DLP ポリシーを構成します。
  
1. ブラウザーの **[Microsoft Office Home]** タブで、**[セキュリティとコンプライアンス]** タイルをクリックします。
    
2. ブラウザーの新しい **[セキュリティとコンプライアンス]** タブで、**[データ損失防止] > [ポリシー]** をクリックします。
    
3. **[データ損失防止]** ウィンドウで、 **[+ ポリシーの作成]** をクリックします。
    
4. **[テンプレートを使って開始するか、カスタム ポリシーを作成する]** ウィンドウで、**[カスタム]** をクリックして、**[次へ]** をクリックします。
    
5. **[ポリシーに名前をつける]** ウィンドウの **[名前]** に高機密レベル DLP ポリシーの名前を入力して、**[次へ]** をクリックします。
    
6. **[場所の選択]** ウィンドウで、**[自分で特定の場所を選択する]** をクリックして、**[次へ]** をクリックします。
    
7. 場所の一覧で、 **Exchange メール**と **OneDrive アカウント**の場所を無効にし、 **[次へ]** をクリックします。
    
8. **[保護する機密性の高い情報の種類をカスタマイズする]** ウィンドウで、 **[編集]** をクリックします。
    
9. **[保護するコンテンツの種類を選択する]** ウィンドウのドロップダウン ボックスで **[追加]** をクリックしてから、 **[ラベル]** をクリックします。
    
10. **[ラベル]** ウィンドウで、 **[+ 追加]** をクリックして、 **[高機密]** ラベルを選択し、 **[追加]** をクリックしてから、 **[完了]** をクリックします。
    
11. **[保護するコンテンツの種類を選択する]** ウィンドウで、 **[保存]** をクリックします。
    
12. **[Customize the types of sensitive info you want to protect]\(保護する機密情報の種類のカスタマイズ\)** ウィンドウで、**[次へ]** をクリックします。
    
13. **[What do you want to do if we detect sensitive info?]\(機密情報が検出された場合の処理\)** ウィンドウで、**[Customize the tip and email]\(ヒントと電子メールをカスタマイズする)** をクリックします。
    
14. **[Customize policy tips and email notifications]\(ポリシー ヒントと電子メール通知のカスタマイズ\)** ウィンドウで、**[Customize the policy tip text]\(ポリシー ヒントのテキストをカスタマイズする\)** をクリックします。
    
15. 次の内容をテキスト ボックスに入力するか、貼り付けます。
    
  - 組織外のユーザーと共有するには、ファイルをダウンロードしてから開きます。[ファイル]、[文書の保護]、[パスワードを使用して暗号化] の順にクリックし、強力なパスワードを指定します。別の電子メールまたはその他の通信手段でパスワードを送信します。
    
    あるいは、ファイルを共有する方法について組織外のユーザーに指示する独自のポリシー ヒントを入力するか、貼り付けます。
    
16. **[OK]** をクリックします。
    
17. **[機密性の高い情報が検出された場合に実行する操作]** ウィンドウで、 **[業務の妥当性を要求してオーバーライドする]** をクリックしてから、 **[次へ]** をクリックします。
    
18. **[ポリシーを有効にしますか、または最初にテストしますか?]** ウィンドウで、 **[すぐ有効にします]** をクリックし、 **[次へ]** をクリックします。
    
19. **[設定の確認]** ウィンドウで、**[作成]** をクリックして、**[閉じる]** をクリックします。
    
非常に機密性の高い社外秘 SharePoint Online チーム サイトの最終的な構成をここに示します。
  
![高機密 Office 365 ラベルを使用している、独立した SharePoint Online チーム サイトの DLP ポリシー。](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a>次の手順

[Azure Information Protection を使用して SharePoint Online ファイルを保護する](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a>関連項目

[SharePoint Online サイトとファイルをセキュリティで保護する](secure-sharepoint-online-sites-and-files.md)
  
[開発/テスト環境の SharePoint Online サイトをセキュリティで保護する](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)


