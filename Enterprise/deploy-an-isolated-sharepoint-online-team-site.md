---
title: "分離した SharePoint Online チーム サイトの展開"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: "概要: ステップごとの手順を使用して、分離した新しい SharePoint Online チーム サイトを展開します。"
ms.openlocfilehash: 31a1f588aefccd9e2cb353af86d8aa0d598696af
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a>分離した SharePoint Online チーム サイトの展開

 **概要:** ステップごとの手順を使用して、分離した新しい SharePoint Online チーム サイトを展開します。
  
この記事は、分離した SharePoint Online チーム サイトを Microsoft Office 365 で作成および構成するためのステップごとの展開ガイドです。これらの手順は、アクセス レベルごとに 1 つの Azure Active Directory (AD) ベースのアクセス グループが含まれる、3 つの既定の SharePoint グループとそれに対応するアクセス許可レベルの使用を前提としています。
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a>フェーズ 1:チーム サイト アクセス グループの作成と設定

このフェーズでは、3 つの既定の SharePoint グループに対して 3 つの Azure AD ベースのアクセス グループを作成し、それらに適切なユーザー アカウントを設定します。
  
> [!NOTE]
> 次の手順は、すべての必要なユーザー アカウントが既に存在し、適切なライセンスが割り当てられていることを前提としています。そうでない場合は、それらを追加して、手順 1 に進む前にライセンスを割り当てます。 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a>手順 1:サイトの SharePoint Online 管理者を一覧表示する

分離したチーム サイトの SharePoint Online 管理者に対応するユーザー アカウントのセットを決定します。
  
Office 365 を使用してユーザー アカウントとグループを管理していて、Windows PowerShell を使用する場合は、そのユーザー プリンシパル名 (UPN) のリストを作成します (UPN の例: belindan@contoso.com)。
  
### <a name="step-2-list-the-members-for-the-site"></a>手順 2: サイトのメンバーを一覧表示する

分離したチーム サイトのメンバーに対応するユーザー アカウントのセットを決定します。メンバーはサイト内に格納されているリソースで共同作業を行います。
  
Office 365 を使用してユーザー アカウントとグループを管理していて、PowerShell を使用する場合は、その UPN の一覧を作成します。サイト メンバーが数多く存在する場合は、UPN の一覧をテキスト ファイルに格納し、PowerShell コマンドを 1 回実行することですべて追加できます。
  
### <a name="step-3-list-the-viewers-for-the-site"></a>手順 3:サイトのビューアーを一覧表示する

分離したチーム サイトのビューアーに対応するユーザー アカウントのセットを決定します。ビューアーは、サイトに格納されているリソースを表示できますが、リソースを変更したり、そのコンテンツで直接共同作業を行ったりすることはできません。
  
Office 365 を使用してユーザー アカウントとグループを管理していて、PowerShell を使用する場合は、その UPN の一覧を作成します。サイト メンバーが数多く存在する場合は、UPN の一覧をテキスト ファイルに格納し、PowerShell コマンドを 1 回実行することですべて追加できます。
  
サイトのビューアーには、経営幹部、弁護士、または部門間の利害関係者などが含まれます。
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a>手順 4:Azure AD でサイト用の 3 つのアクセス グループを作成する

Azure AD で次のアクセス グループを作成する必要があります。
  
- サイト管理者 (手順 1 のリストが含まれます)
    
- サイト メンバー (手順 2 のリストが含まれます)
    
- サイト ビューアー (手順 3 のリストが含まれます)
    
1. お使いのブラウザーで、Azure Portal [(https://portal.azure.com)]((https://portal.azure.com)) に移動し、ユーザー管理の管理者または会社管理者のロールに割り当てられたアカウントの資格情報でサインインします。
    
2. Azure Portal で **[Azure Active Directory] > [ユーザーとグループ] > [すべてのグループ]** の順にクリックします。
    
3. **[すべてのグループ]** ブレードで、 **[+ 新しいグループ]** をクリックします。
    
4. **[グループ]** ブレードでの手順:
    
  - **[名前]** にグループ名を入力します。
    
  - **[メンバーシップ]** で **[割り当て済み]** を選択します。
    
  - **[Office の機能を有効にする]** で **[はい]** をクリックします。
    
5. **[作成]** をクリックして、 **[グループ]** ブレードを閉じます。
    
6. 追加グループについて手順 3 から 5 を繰り返します。
    
> [!NOTE]
> Office の機能を有効にできるグループを作成するには、Azure Portal を使用する必要があります。SharePoint Online の独立したサイトを、後から Azure Information Protection (AIP) のラベルを使用して高機密サイトとして構成し、ファイルを暗号化して特定のグループにアクセス許可を割り当てる場合、許可されるグループは Office の機能を有効にして作成する必要があります。Azure AD グループが作成された後は、その Office の機能の設定は変更できません。 
  
これで 3 つのサイトのアクセス グループの構成が完了します。
  
![独立した SharePoint Online サイトの展開用の 3 つのアクセス グループ。](images/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a>手順 5:アクセス グループにユーザー アカウントを追加する

この手順では、次の操作を行います。
  
1. 手順 1 のユーザーの一覧をサイト管理者のアクセス グループに追加する
    
2. 手順 2 のユーザーの一覧をサイト メンバーのアクセス グループに追加する
    
3. 手順 3 のユーザーの一覧をサイト ビューアーのアクセス グループに追加する
    
Windows Server AD を使用してユーザー アカウントとグループを管理している場合は、Windows Server AD ユーザーとグループの標準的な管理手順を使用してユーザーを適切なアクセス グループに追加し、Office 365 サブスクリプションと同期されるまで待機します。
  
Office 365 を使用してユーザー アカウントとグループを管理する場合は、Office 管理者センターまたは PowerShell を使用できます。アクセス グループのいずれかでグループ名が重複している場合、Office 管理者センターをご使用ください。
  
Office 管理者センターでは、ユーザー アカウント管理者または会社管理者の役割が割り当てられているユーザー アカウントでサインインし、グループを使用して適切なユーザー アカウントおよびグループを適切なアクセス グループに追加します。
  
PowerShell については、まず「[Azure Active Directory V2 PowerShell モジュールを使用した接続](https://go.microsoft.com/fwlink/?linkid=842218)」を参照してください。
  
次に、以下のコマンド ブロックを使用して、個々のユーザー アカウントをアクセス グループに追加します。
  
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> すべての PowerShell コマンドを記載したテキスト ファイルと、使用しているグループおよびユーザー アカウント名に基づいて PowerShell コマンドを生成する Excel 構成ワークシートについては、[分離した SharePoint Online チーム サイトの展開キット]((https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907))をダウンロードしてください。 
  
いずれかのアクセス グループのユーザー アカウントの UPN をテキスト ファイルに格納した場合は、次の PowerShell コマンド ブロックを使用して、それらすべてのユーザー アカウントを一度に追加します。
  
```
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

PowerShell の場合、次のコマンド ブロックを使用して、個々のグループをアクセス グループに追加します。
  
```
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

次のような結果が表示されます。
  
- サイト管理者の Azure AD グループには、サイト管理者のユーザー アカウントまたはグループが含まれる
    
- サイト メンバーの Azure AD グループには、サイト メンバーのユーザー アカウントまたはグループが含まれる
    
- サイト ビューアーの Azure AD グループには、サイトのコンテンツを表示できるユーザー アカウントまたはグループのみが含まれる
    
Office 管理者センターまたは次の PowerShell コマンド ブロックを使用して、各アクセス グループのグループ メンバーの一覧を検証します。
  
```
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

以下に示すのが、でき上がった構成で、この構成にはユーザー アカウントとグループが設定された3 つのサイトのアクセス グループが含まれます。
  
![ユーザー アカウントが設定された 3 つのアクセス グループ。](images/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a>フェーズ 2:分離したチーム サイトを作成し構成する

このフェーズでは、分離した SharePoint Online サイトを作成し、新しい Azure AD ベースのアクセス グループを使用するために既定の SharePoint Online アクセス許可レベルのアクセス許可を構成します。
  
最初に、次の手順で SharePoint Online チーム サイトを作成します。
  
1. SharePoint Online チーム サイト (SharePoint Online 管理者) の管理にも使用されるアカウントを使用して Office 365 ポータルにサインインします。ヘルプを表示するには、「[Office 365 にサインインする場所]((https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4))」を参照してください。
    
2. タイルのリストで、 **[SharePoint]** をクリックします。
    
3. ブラウザーの新しい **[SharePoint]** タブで、 **[+ サイトの作成]** をクリックします。
    
4. **[サイトの作成]** ページで、 **[チーム サイト]** をクリックします。
    
5. **[サイト名]** にチーム サイトの名前を入力します。 
    
6. **[チーム サイトの説明]** に、サイトの目的の説明 (オプション) を入力します。
    
7. **[プライバシー設定]** で、 **[プライベート - メンバーのみがこのサイトにアクセス可能**」を選択して **[次へ]** をクリックします。
    
8. **[誰を追加しますか]** ウィンドウで、 **[完了]** をクリックします。
    
次に、新しい SharePoint Online チーム サイトから、アクセス許可を構成します。
  
1. ツールバーで、設定アイコンをクリックしてから、 **[サイトの権限]** をクリックします。
    
2. **[サイトの権限]** ウィンドウで、 **[高度な権限の設定]** をクリックします。
    
3. ブラウザーの新しい **[権限]** タブで、 **[アクセス要求の設定]** をクリックします。
    
4. **[アクセス要求の設定]** ダイアログ ボックスの **[サイトと個別のファイルおよびフォルダーの共有をメンバーに許可します]** と **[アクセス要求の許可]** をクリアし (これによって、3 つのチェック ボックスがすべてクリアされる)、 **[OK]** をクリックします。
    
5. ブラウザーの **[アクセス権]** タブで、リスト内の **[\<サイト名> のメンバー]** をクリックします。
    
6. **[ユーザーとグループ]** で、 **[新規]** をクリックします。
    
7. **[共有]** ダイアログ ボックスで、サイト メンバーのアクセス グループの名前を入力し、それを選択してから、 **[共有]** をクリックします。
    
8. ブラウザーの戻るボタンをクリックします。
    
9. リスト内の **[\<サイト名> の所有者]** をクリックします。
    
10. **[ユーザーとグループ]** で、 **[新規]** をクリックします。
    
11. **[共有]** ダイアログ ボックスで、サイト管理者のアクセス グループの名前を入力し、それを選択してから、 **[共有]** をクリックします。
    
12. ブラウザーの戻るボタンをクリックします。
    
13. リスト内の **[\<サイト名> の閲覧者]** をクリックします。
    
14. **[ユーザーとグループ]** で、 **[新規]** をクリックします。
    
15. **[共有]** ダイアログ ボックスで、サイト ビューアーのアクセス グループの名前を入力し、それを選択してから、 **[共有]** をクリックします。
    
16. ブラウザーの **[アクセス権]** タブを閉じます。
    
これらのアクセス権の設定の結果は次のとおりです。
  
- **[\<サイト名> の所有者]** の SharePoint グループには、サイト管理者のアクセス グループが含まれます。このグループではすべてのメンバーに**フル コントロール** アクセス許可レベルが付与されています。
    
- **[\<サイト名> のメンバー**]の SharePoint グループには、サイト メンバーのアクセス グループが含まれます。このグループではすべてのメンバーに**編集**アクセス許可レベルが付与されています。
    
- **[\<サイト名> の閲覧者]**の SharePoint グループには、サイト ビューアーのアクセス グループが含まれます。このグループではすべてのメンバーに**読み取り**アクセス許可レベルが付与されています。
    
- メンバーが他のメンバーを招待したり、メンバー以外のユーザーがアクセス権を要求したりする機能は無効です。
    
以下に示すのができ上がった構成で、この構成にはユーザー アカウントと Azure AD グループが設定された 3 つのアクセス グループを使用するように構成されたサイト用の 3 つの SharePoint グループ含まれます。
  
![アクセス グループおよびユーザー アカウントが設定された、独立した SharePoint Online サイトの最終的な構成。](images/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
いずれかのアクセス グループのグループ メンバーシップを介して、サイトのメンバーとともにサイトのリソースを使用して共同作業を行えるようになります。
  
## <a name="next-step"></a>次の手順

サイト アクセス グループ メンバーシップを変更したり、カスタム アクセス許可を持つドキュメント フォルダーを作成したりする必要がある場合は、「[分離した SharePoint Online チーム サイトの管理](manage-an-isolated-sharepoint-online-team-site.md)」を参照してください。
  
## <a name="see-also"></a>関連項目

[分離した SharePoint Online チーム サイト](isolated-sharepoint-online-team-sites.md)
  
[分離した SharePoint Online チーム サイトの設計](design-an-isolated-sharepoint-online-team-site.md)
  
[分離した SharePoint Online チーム サイトの管理](manage-an-isolated-sharepoint-online-team-site.md)
  
[セキュリティ ソリューション](security-solutions.md)



