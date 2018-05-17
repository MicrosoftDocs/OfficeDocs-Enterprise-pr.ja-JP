---
title: 選挙運動の開発/テスト環境用にグループとユーザーを構成する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: '要約: 選挙運動の開発/テスト環境向けのユーザーとグループで Office 365 と Enterprise Mobility + Security (EMS) の試用版サブスクリプションを作成します。'
ms.openlocfilehash: 8556040a648937d4c1bc338292be121e5d290dd9
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a>選挙運動の開発/テスト環境用にグループとユーザーを構成する

 **要約:** 選挙運動の開発/テスト環境向けのユーザーとグループで Office 365 と Enterprise Mobility + Security (EMS) の試用版サブスクリプションを作成します。
  
簡略化されたユーザー アカウントとグループを含む開発/テスト環境を「[選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)」ソリューション用に作成するには、この資料の手順を使用します。
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>フェーズ 1: Office 365 の開発/テスト環境を作成する

このフェーズでは、選挙運動を務める架空の組織用に Office 365 E5 と Enterprise Mobility + Security (EMS) E5 の試用版サブスクリプションを取得します。
  
まず、「[Office 365 開発/テスト環境](office-365-dev-test-environment.md)」の**フェーズ 2**に記されている手順を実行します
  
次に、EMS E5 試用版サブスクリプションにサインアップして、Office 365 試用版サブスクリプションと同じ組織に追加します。
  
1. 必要に応じて、Office 365 ポータルに、試用版サブスクリプション用の全体管理者アカウントの資格情報でサインインします。ヘルプについては、「[一般法人向け Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。
    
2. 
            **[管理]** タイルをクリックします。
    
3. ブラウザーの **[Office 管理センター]** タブの左側のナビゲーションで **[請求] > [サービスを購入する]** の順にクリックします。
    
4. **[サービスを購入]** ページで、 **[Enterprise Mobility + Security E5]** 項目を探します。その項目の上にマウス ポインターを移動させ、 **[無料試用版を起動する]** をクリックします。
    
5. **[注文の確認]** ページで、 **[今すぐ実行]** をクリックします。
    
6. **[注文の受領書]** ページで、**[続行]** をクリックします。
    
次に、全体管理者アカウントの EMS E5 ライセンスを有効にします。
  
1. ブラウザーの **[Office 365 管理センター]** タブの左側のナビゲーションで **[ユーザー] > [アクティブなユーザー]** の順にクリックします。
    
2. 全体管理者アカウントをクリックしてから、 **[製品ライセンス]** で **[編集]** をクリックします。
    
3. **[製品ライセンス]** ウィンドウで、 **Enterprise Mobility + Security E5** の製品ライセンスを **[オン]** にして、 **[保存]** をクリックしてから、 **[閉じる]** を 2 回クリックします。
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a>フェーズ 2: Azure Active Directory (AD) グループを作成して構成する

このフェーズでは、選挙運動用に Azure AD グループを作成して構成します。
  
最初に、Azure portal で一般的な選挙運動グループのセットを作成します。
  
1. ブラウザーの別タブで、Azure portal ([https://portal.azure.com](https://portal.azure.com)) に移動します。必要に応じて、Office 365 E5 試用版サブスクリプション用の全体管理者アカウントの資格情報でサインインします。
    
2. Azure portal で **[Azure Active Directory] > [ユーザーとグループ] > [すべてのグループ]** の順にクリックします。
    
3. このリストのグループ名ごとに、次の手順を実行します。
    
  - 戦略的シニア スタッフ
    
  - IT スタッフ
    
  - 分析スタッフ
    
  - 正規のコア スタッフ
    
  - 運用スタッフ
    
  - フィールド スタッフ
    
1. **[すべてのグループ]** ブレードで、**[+ 新しいグループ]** をクリックします。
    
2. リストにあるグループ名を **[名前]** に入力します。
    
3. **[メンバーシップ]** で **[動的ユーザー]** を選択します。
    
4. **[Office の機能を有効にする]** で **[はい]** をクリックします。
    
5. **[動的クエリの追加]** をクリックします。
    
6. **[ユーザーを追加する場所]** で、**[部署]** を選択します。
    
7. 次のフィールドで、**[等しい]** を選択します。
    
8. 次のフィールドで、リストにあるグループ名を入力します。
    
9. **[クエリの追加]** をクリックしてから、**[作成]** をクリックします。
    
10. **[ユーザーとグループ - すべてのグループ]** をクリックします。
    
次に、メンバーに Office 365 E5 および EMS E5 のライセンスが自動的に割り当てられるようにグループを構成します。
  
1. Azure portal で **[Azure Active Directory] > [ライセンス] > [すべての製品]** の順にクリックします。
    
2. 一覧で、**[Enterprise Mobility + Security E5]** と **[Office 365 Enterprise E5]** を選択して、**[+ 割り当て]** をクリックします。
    
3. **[ライセンスの割り当て]** ブレードで、**[ユーザーとグループ]** をクリックします。
    
4. グループの一覧で、次を選択します。
    
  - 分析スタッフ
    
  - フィールド スタッフ
    
  - IT スタッフ
    
  - 運用スタッフ
    
  - 正規のコア スタッフ
    
  - 戦略的シニア スタッフ
    
5. **[選択]** をクリックし、**[割り当て]** をクリックします。
    
6. ブラウザーの [Azure Portal] タブを閉じます。
    
## <a name="phase-3-add-your-user-accounts"></a>フェーズ 3:ユーザー アカウントを追加する

このフェーズでは、選挙運動のサンプル ユーザー アカウントを追加します。
  
まず、[Azure Active Directory V2 PowerShell モジュールを使用して接続](https://go.microsoft.com/fwlink/?linkid=842218)します。
  
次に、組織名、場所、および共通のパスワードを入力し、PowerShell コマンド プロンプトまたは Integrated Scripting Environment (ISE) からこれらのコマンドを実行します。
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> ここでは共通のパスワードを使用することで、自動化と、開発/テスト環境の構成を容易にしています。運用サブスクリプションでの使用はお勧めしません。これらの新しいユーザー アカウントでサインインするときに、パスワードの変更を求めるダイアログが表示されます。 
  
動的グループのメンバーシップとグループ ベースのライセンスが正常に機能していることを確認するには、次の手順を使用します。
  
1. ブラウザーの **[Microsoft Office Home]** タブで、**[管理者]** タイルをクリックします。
    
2. ブラウザーの新しい **Office 管理センター**のタブで、**[ユーザー]** をクリックします。
    
3. ユーザーの一覧で **[候補]** をクリックします。
    
4. **[候補]** ユーザー アカウントのプロパティを一覧表示するウィンドウで、次を確認します。
    
  - **[戦略的シニア スタッフ]** グループのメンバーである (**[グループ メンバーシップ]** 内)。
    
  - **[Enterprise Mobility + Security E5]** と **[Office 365 Enterprise E5]** のライセンスが割り当てられている (**[製品ライセンス]** 内)。
    
5. **[候補]** ユーザー アカウントのウィンドウを閉じます。
    
## <a name="record-values-for-future-reference"></a>将来の参考のために値を記録する

この開発/テスト環境で Office 365 と EMS の試用版サブスクリプションを使用するために、これらの値を記録します。
  
- 試用版サブスクリプションの組織名: _______________________________________________。 
    
    たとえば、試用版サブスクリプションのドメイン名 contoso.onmicrosoft.com の場合、組織名は "contoso" です。
    
- Office 365 グローバル管理者名: ____________________________________.onmicrosoft.com
    
    このアカウントのパスワードや、その他のユーザー アカウントの共通のパスワードを安全な場所に記録します。
    
## <a name="next-step"></a>次の手順

[Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md) を使用して、この開発/テスト環境で 4 つの異なる種類の SharePoint Online チーム サイトを作成します。
  
## <a name="see-also"></a>関連項目

[選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[選挙運動用の開発/テスト環境でチーム サイトを作成する](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)




