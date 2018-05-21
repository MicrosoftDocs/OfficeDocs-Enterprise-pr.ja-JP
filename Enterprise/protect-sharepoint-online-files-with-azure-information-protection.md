---
title: Azure Information Protection を使用して SharePoint Online ファイルを保護する
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
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: '概要: Azure Information Protection を適用して、機密性の高い SharePoint Online チーム サイト内のファイルを保護します。'
ms.openlocfilehash: bab799a784cac579c92fb06ea17592d85fd59af2
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a>Azure Information Protection を使用して SharePoint Online ファイルを保護する

 **概要:** Azure Information Protection を適用して、機密性の高い SharePoint Online チーム サイト内のファイルを保護します。
  
この記事の手順を使用して、Azure Information Protection を構成し、機密性の高い SharePoint Online チーム サイト内のファイルの暗号化やアクセス許可を実施します。暗号化およびアクセス許可の保護は、ファイルをサイトからダウンロードした場合にも適用されます。機密性の高い SharePoint Online チーム サイトの詳細については、「[SharePoint Online サイトとファイルをセキュリティで保護する](secure-sharepoint-online-sites-and-files.md)」を参照してください。
  
> [!NOTE]
> Azure Information Protection 暗号化が Office 365 に格納されているファイルに適用される場合、このサービスはこれらのファイルのコンテンツを処理することはできません。共同編集、電子情報開示、検索、Delve、他の共同作業機能は動作しません。データ損失防止 (DLP) ポリシーが操作できるのはメタデータ (Office 365 ラベルを含む) のみで、それらのファイルのコンテンツ (ファイル内のクレジットカード番号など) を操作することはできません。 
  
まず、「[Office 365 管理センターから Azure Rights Management をアクティブ化する方法](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)」にある Office 365 サブスクリプションに関する指示を使用します。
  
次に、機密性の高い SharePoint Online チーム サイトの保護とアクセス許可用に、新たなスコープ付きポリシーとサブラベルを使用して Azure Information Protection を構成します。
  
1. セキュリティ管理者または会社管理者のロールのアカウントを使用して、Office 365 ポータルにサインインします。ヘルプを表示するには、「[Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。
    
2. ブラウザーで別のタブを開き、Azure portal ([https://portal.azure.com](https://portal.azure.com)) に移動します。
    
3. 初めて Azure Information Protection を構成する場合は、これらの[手順](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)を参照してください。
    
4. リスト ウィンドウで、**[すべてのサービス]** をクリックして、「**information**」と入力し、**[Azure Information Protection]** をクリックします。
    
5. **[Azure Information Protection]** ブレードで、 **[スコープ付きポリシー] > [+ 新しいポリシーの追加]** をクリックします。
    
6. **[ポリシー名]** に新しいポリシーの名前、 **[説明]** に説明を入力します。
    
7. **[このポリシーを取得するユーザーまたはグループを選択] > [ユーザー/グループ]** をクリックし、機密性の高い SharePoint Online チーム サイト用のサイト メンバー アクセス グループを選択します。 
    
8. **[選択] > [OK]** とクリックします。
    
9. **[非常に機密性の高い社外秘]** ラベルの場合は、省略記号 (...) をクリックしてから、 **[サブラベルの追加]** をクリックします。
    
10. **[名前]** にサブラベルの名前、 **[説明]** にラベルの説明を入力します。
    
11. **[このラベルを含むドキュメントやメールに対するアクセス許可の設定]** で、 **[保護]** をクリックします。
    
12. **[保護]** セクションで **[Azure (クラウド キー)]** をクリックします。
    
13. **[保護]** ブレードで **[保護設定]** の **[+ アクセス許可の追加]** をクリックします。
    
14. **[アクセス許可を追加する]** ブレードの **[ユーザーとグループの指定]** で、 **[+ ディレクトリを参照]** をクリックします。
    
15. **[AAD のユーザーとグループ]** ウィンドウで、機密性の高い SharePoint Online チーム サイトのサイト メンバー アクセス グループを選択し、 **[選択]** をクリックします。
    
16. **[プリセットからアクセス許可を選択]** で、 **[印刷]**、 **[コンテンツのコピーと抽出]**、および **[転送]** チェック ボックスをクリアします。
    
17. [ **OK**] を 2 回クリックします。
    
18. **[サブラベル]** ブレードで、 **[保存]** をクリックします。
    
19. 新しいスコープ付きポリシー ブレードを閉じます。
    
20. **[Azure Information Protection - スコープ付きポリシー]** ブレードで、 **[発行]** をクリックします。
    
これが高機密 SharePoint Online チーム サイトの最終的な構成になります。
  
![独立した SharePoint Online チーム サイトの Azure Information Protection ラベル。](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
これで、ドキュメントを作成して、Azure Information Protection および新しいラベルでそれらを保護する準備が整いました。
  
デバイスまたは Windows ベースのコンピューターに [Azure Information Protection クライアントをインストールする (](https://docs.microsoft.com/information-protection/rms-client/install-client-app)) 必要があります。インストールをスクリプトで記述して自動化するか、ユーザーがクライアントを手動でインストールできます。以下のリソースを参照してください。
  
- [クライアント側での Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [Azure Information Protection クライアントのインストール](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [手動インストールのためのダウンロード ページ](https://www.microsoft.com/download/details.aspx?id=53018)
    
インストールすると、ユーザーは Office アプリケーション (Microsoft Word など) を実行してからサインインするときに、Office 365 アカウントを使用します。ユーザーは新しい **[Information Protection]** バーを使用して、新しいラベルを選択できます。ユーザーが機密性の高いファイルを保護するための SharePoint Online チーム サイトと使用するラベルを知っていることを確認します。
  
> [!NOTE]
> 機密性の高い複数の SharePoint Online チーム サイトが存在する場合、上記の設定を使用して複数の Azure Information Protection スコープ付きポリシーとサブラベルを作成し、特定の SharePoint Online チーム サイトのサイト メンバー アクセス グループに設定されたサブラベルごとにアクセス許可を指定する必要があります。 
  
## <a name="see-also"></a>関連項目

[SharePoint Online サイトとファイルをセキュリティで保護する](secure-sharepoint-online-sites-and-files.md)
  
[開発/テスト環境の SharePoint Online サイトをセキュリティで保護する](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)




