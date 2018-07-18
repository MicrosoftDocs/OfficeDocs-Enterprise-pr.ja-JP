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
ms.openlocfilehash: 2c4776f5795a5a0b07be0f04b4872abadb4d31ca
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319288"
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a>Azure Information Protection を使用して SharePoint Online ファイルを保護する

 **概要:** Azure Information Protection を適用して、機密性の高い SharePoint Online チーム サイト内のファイルを保護します。
  
この記事の手順を使用して、Azure Information Protection を構成し、ファイルの暗号化やアクセス許可を実施します。これらのファイルは、高度な機密保護のために構成された SharePoint ライブラリに追加することができます。あるいは、サイトからファイルを直接開き、Azure Information Protection クライアントを使用して暗号化を追加することもできます。暗号化およびアクセス許可の保護は、ファイルをサイトからダウンロードした場合にも適用されます。 

これらの手順は、SharePoint サイトとそれらのサイト内のファイルの高度な機密保護を構成するための大きなソリューションの一部です。詳細については、「[SharePoint Online サイトとファイルをセキュリティで保護する](secure-sharepoint-online-sites-and-files.md)」を参照してください。 

SharePoint Online 内のファイルに Azure Information Protection を使用することは、すべてのお客様に推奨されるものではなく、ファイルの一部に対してこの保護レベルを必要としているお客様向けのオプションです。

このソリューションに関する重要な注意点がいくつかあります:
- Azure Information Protection 暗号化が Office 365 に格納されているファイルに適用される場合、このサービスはこれらのファイルのコンテンツを処理することはできません。共同編集、電子情報開示、検索、Delve、他の共同作業機能は動作しません。データ損失防止 (DLP) ポリシーが操作できるのはメタデータ (Office 365 ラベルを含む) のみで、それらのファイルのコンテンツ (ファイル内のクレジットカード番号など) を操作することはできません。
- このソリューションでは、Azure Information Protection からの保護が適用されるラベルを、ユーザーが選択する必要があります。自動的な暗号化と、インデックスを作成してファイルを検査するための SharePoint の機能を必要とする場合は、SharePoint Online で Information Rights Management (IRM) を使用することを検討してください。IRM 用に SharePoint ライブラリを構成する場合、ファイルが編集用にダウンロードされるときに、ファイルは自動的に暗号化されます。SharePoint IRM には、意思決定に影響を与える可能性のある制限があります。詳細については、「[SharePoint 管理センターで Information Rights Management (IRM) を設定する](https://support.office.com/ja-JP/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C)」を参照してください。

##<a name="admin-setup"></a>管理者セットアップ
まず、「[Office 365 管理センターから Azure RMS をアクティブ化する方法](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)」にある Office 365 サブスクリプションに関する指示を使用します。
  
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
    
20. **[Azure Information Protection - スコープ付きポリシー]** ブレードで、**[発行]** をクリックします。
    
 
##<a name="client-setup"></a>クライアントのセットアップ
これで、ドキュメントを作成して、Azure Information Protection および新しいラベルでそれらを保護する準備が整いました。
  
デバイスまたは Windows ベースのコンピューターに [Azure Information Protection クライアントをインストールする (](https://docs.microsoft.com/information-protection/rms-client/install-client-app)) 必要があります。インストールをスクリプトで記述して自動化するか、ユーザーがクライアントを手動でインストールできます。以下のリソースを参照してください。
  
- [クライアント側での Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [Azure Information Protection クライアントのインストール](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [手動インストールのためのダウンロード ページ](https://www.microsoft.com/download/details.aspx?id=53018)
    
インストールすると、ユーザーは Office アプリケーション (Microsoft Word など) を実行してからサインインするときに、Office 365 アカウントを使用します。ユーザーは新しい **[Information Protection]** バーを使用して、新しいラベルを選択できます。ユーザーが機密性の高いファイルを保護するための SharePoint Online チーム サイトと使用するラベルを知っていることを確認します。
  
> [!NOTE]
> 機密性の高い複数の SharePoint Online チーム サイトが存在する場合、上記の設定を使用して複数の Azure Information Protection スコープ付きポリシーとサブラベルを作成し、特定の SharePoint Online チーム サイトのサイト メンバー アクセス グループに設定されたサブラベルごとにアクセス許可を指定する必要があります。 
  
##<a name="adding-permissions-for-external-users"></a>外部ユーザーに対するアクセス許可の追加
Azure Information Protection で保護されているファイルへのアクセス権を外部ユーザーに付与するには、2 つの方法があります。どちらの場合も外部ユーザーには Azure AD アカウントが必要です。外部ユーザーが Azure AD を使用する組織のメンバーでない場合は、サインアップ ページ ([https://aka.ms/aip-signup](https://aka.ms/aip-signup)) を使用して個人で Azure AD アカウントを取得できます。

 - 外部ユーザーを、ラベルの保護の構成に使用する Azure AD グループに追加します。最初に、ご使用のディレクトリでアカウントを B2B ユーザーとして追加する必要があります。[Azure Rights Management によるグループ メンバーシップのキャッシュ](https://docs.microsoft.com/ja-JP/azure/information-protection/plan-design/prepare#group-membership-caching-by-azure-information-protection)は、数時間かかる可能性があります。  
 - 外部ユーザーを直接、ラベル保護に追加します。組織 (例: Fabrikam.com) のすべてのユーザー、Azure AD グループ (例: 組織内の財務グループ)、またはユーザーを追加できます。たとえば、監督機関の外部チームをラベルの保護に加えることができます。

## <a name="see-also"></a>関連項目

[SharePoint Online サイトとファイルをセキュリティで保護する](secure-sharepoint-online-sites-and-files.md)
  
[開発/テスト環境の SharePoint Online サイトをセキュリティで保護する](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)




