---
title: "分離した SharePoint Online チーム サイトの管理"
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
ms.assetid: 79a61003-4905-4ba8-9e8a-16def7add37c
description: "概要: 以下の手順を使用して、分離した SharePoint Online チーム サイトを管理します。"
ms.openlocfilehash: 51e3bea35220781303ca6dfb49ce57b60e72ba3a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="manage-an-isolated-sharepoint-online-team-site"></a>分離した SharePoint Online チーム サイトの管理

 **概要:** 以下の手順を使用して、分離した SharePoint Online チーム サイトを管理します。
  
この記事では、分離した SharePoint Online チーム サイトの一般的な管理操作について説明します。
  
## <a name="add-a-new-user"></a>新しいユーザーを追加する

他のユーザーが新しいサイトに参加する場合は、サイトでの参加レベルを決定する必要があります。
  
- 管理:サイト管理者のアクセス グループに新しいユーザー アカウントを追加する
    
- アクティブ コラボレーション:サイト メンバーのアクセス グループにユーザー アカウントを追加する
    
- 表示:サイト ビューアーのアクセス グループにユーザー アカウントを追加する
    
Windows Server Active Directory (AD) を使用してユーザー アカウントとグループを管理している場合は、Windows Server AD ユーザーとグループの標準的な管理手順を使用して適切なユーザーを適切なアクセス グループに追加し、Office 365 サブスクリプションと同期されるまで待機します。
  
Office 365 を使用してユーザー アカウントとグループを管理する場合は、Office 管理者センターまたは Microsoft PowerShell を使用できます。
  
- Office 管理者センターでは、ユーザー アカウント管理者または会社管理者の役割が割り当てられているユーザー アカウントでサインインし、グループを使用して適切なユーザーを適切なアクセス グループに追加します。
    
- PowerShell の場合、最初に [Azure Active Directory V2 PowerShell モジュールを使用して接続](https://go.microsoft.com/fwlink/?linkid=842218)します。ユーザー アカウントをそのユーザー プリンシパル名 (UPN) が含まれるアクセス グループに追加するには、次の PowerShell コマンド ブロックを使用します。
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> すべての PowerShell コマンドを記載したテキスト ファイルと、使用しているグループおよびユーザー アカウント名に基づいて PowerShell コマンドを生成する Excel 構成ワークシートについては、[分離した SharePoint Online チーム サイトの展開キット]((https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907))をダウンロードしてください。 

表示名を使ってユーザー アカウントをアクセス グループに追加するには、次の PowerShell コマンド ブロックを使用します。

```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="add-a-new-group"></a>新しいグループを追加する

グループ全体にアクセスを追加するには、サイト内のグループのすべてのメンバーへの参加レベルを決定する必要があります。
  
- 管理:サイト管理者のアクセス グループにグループを追加する
    
- アクティブ コラボレーション:サイト メンバーのアクセス グループにグループを追加する
    
- 表示:サイト ビューアーのアクセス グループにグループを追加する
    
Windows Server AD を使用してユーザー アカウントとグループを管理している場合は、Windows Server AD ユーザーとグループの標準的な管理手順を使用して適切なグループを適切なグループに追加し、Office 365 サブスクリプションと同期されるまで待機します。
  
Office 365 を使用してユーザー アカウントとグループを管理する場合は、Office 管理者センターまたは PowerShell を使用できます。
  
- Office 管理者センターでは、ユーザー アカウント管理者または会社管理者の役割が割り当てられているユーザー アカウントでサインインし、グループを使用して適切なアクセス グループを適切なグループに追加します。
    
- PowerShell の場合、[最初に Azure Active Directory V2 PowerShell モジュールを使用して接続](https://go.microsoft.com/fwlink/?linkid=842218)します。その後、次の PowerShell コマンドを使用します。
 
```
$newGroupName="<display name of the new group to add>"
$siteGrpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $newGroupName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $siteGrpName }).ObjectID
```

## <a name="remove-a-user"></a>ユーザーを削除する

他のユーザーのアクセスをサイトから削除する必要がある場合は、サイトでの参加に基づいてそのユーザーが現在メンバーになっているアクセス グループから削除します。
  
- 管理:サイト管理者のアクセス グループからユーザー アカウントを削除する
    
- アクティブ コラボレーション:サイト メンバーのアクセス グループからユーザー アカウントを削除する
    
- 表示:サイト ビューアーのアクセス グループからユーザー アカウントを削除する
    
Windows Server AD を使用してユーザー アカウントとグループを管理している場合は、Windows Server AD ユーザーとグループの標準的な管理手順を使用して適切なユーザーを適切なアクセス グループから削除し、Office 365 サブスクリプションと同期されるまで待機します。
  
Office 365 を使用してユーザー アカウントとグループを管理する場合は、Office 管理者センターまたは PowerShell を使用できます。
  
- Office 管理者センターでは、ユーザー アカウント管理者または会社管理者の役割が割り当てられているユーザー アカウントでサインインし、グループを使用して適切なユーザーを適切なアクセス グループから削除します。
    
- PowerShell の場合、最初に [Azure Active Directory V2 PowerShell モジュールを使用して接続](https://go.microsoft.com/fwlink/?linkid=842218)します。ユーザー アカウントをそのユーザー プリンシパル名 (UPN) が含まれるアクセス グループから削除するには、次の PowerShell コマンド ブロックを使用します。
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

表示名を使ってアクセス グループからユーザー アカウントを削除するには、次の PowerShell コマンド ブロックを使用します。
    
```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="remove-a-group"></a>グループを削除する

グループ全体のアクセスを削除する必要がある場合は、サイトでの参加に基づいてそのグループが現在メンバーになっているアクセス グループから削除します。
  
- 管理:サイト管理者のアクセス グループからグループを削除する
    
- アクティブ コラボレーション:サイト メンバーのアクセス グループからグループを削除する
    
- 表示:サイト ビューアーのアクセス グループからグループを削除する
    
Windows Server Active Directory を使用してユーザー アカウントとグループを管理している場合は、Windows Server AD ユーザーとグループの標準的な管理手順を使用して適切なグループを適切なアクセス グループから削除し、Office 365 サブスクリプションと同期されるまで待機します。
  
Office 365 を使用してユーザー アカウントとグループを管理する場合は、Office 管理者センターまたは PowerShell を使用できます。
  
- Office 管理者センターでは、ユーザー アカウント管理者または会社管理者の役割が割り当てられているユーザー アカウントでサインインし、グループを使用して適切なグループを適切なアクセス グループから削除します。
    
- PowerShell については、まず「[Azure Active Directory V2 PowerShell モジュールを使用した接続](https://go.microsoft.com/fwlink/?linkid=842218)」を参照してください。    
表示名を使用してアクセス グループからグループを削除するには、次の PowerShell コマンド ブロックを使用します。
    
```
$groupMemberName="<display name of the group to remove>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="create-a-documents-subfolder-with-custom-permissions"></a>カスタムのアクセス許可を持つドキュメントのサブフォルダーを作成します。

分離したサイト内で作業している人々のサブセットでは、コラボレーションするためにプライバシー性の高い場所が必要になることがあります。SharePoint Online サイトでは、サイトの [ドキュメント] フォルダーにサブフォルダーを作成し、カスタムのアクセス許可を割り当てることがことができます。アクセス許可を持たないユーザーはサブフォルダーを表示できません。
  
カスタムのアクセス許可を持つドキュメントのサブフォルダーを作成するには、以下のことを行います。
  
1. サイト管理者のアクセス グループのメンバーであるアカウントを使用して Office 365 にサインインします。ヘルプを表示するには、「[一般法人向け Office 365 にサインインする場所]((https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4))」を参照してください。
    
2. 分離したチーム サイトに移動し、 **[ドキュメント]** をクリックします。
    
3. カスタムのアクセス許可を持つサブフォルダーを格納するフォルダーをドキュメントのフォルダーの中で参照し、そのフォルダーを作成して開きます。
    
4. [ **共有**] をクリックします。
    
5. **[共有相手] > [詳細]** をクリックします。
    
6. **[アクセス許可の継承の中止]** をクリックしてから、 **[OK]** をクリックします。
    
7. [ **共有**] をクリックします。
    
8. **[共有相手] > [詳細]** をクリックします。
    
9. **[アクセス許可の付与] > [共有相手] > [詳細]** をクリックします。
    
10. [アクセス権] ページで、リスト内の **[\<サイト名> のメンバー]** をクリックします。
    
11. **[\<サイト名> のメンバー]** ページで、サイト メンバーのアクセス グループの横にあるチェック ボックスを選択し、**[アクション]** をクリックし、**[グループからユーザーを削除する]** をクリックし、**[OK]** をクリックします。
    
12. 特定のメンバーをこのサブフォルダーに追加するには、**[新規] > [ユーザーの追加]** をクリックします。
    
13. **[共有]** ダイアログ ボックスで、サブフォルダー内のファイルでコラボレーションできるユーザー アカウントの名前を入力してから、 **[共有]** をクリックします。
    
14. Web ページを更新して新しい結果を表示します。
    
15. 左側のナビゲーションの **[グループ]** で、**[\<サイト名> の閲覧者]** グループをクリックし、(必要に応じて) 手順 11 から 14 を使用して、サブフォルダーでファイルを表示できるユーザー アカウントのセットを指定します。
    
16. 左側のナビゲーションの **[グループ]** で、**[\<サイト名> の所有者]** グループをクリックし、(必要に応じて) 手順 11 から 14 を使用して、サブフォルダーでファイルを表示できるユーザー アカウントのセットを指定します。
    
17. ブラウザーで **[ユーザーとグループ]** タブを閉じます。
    
## <a name="see-also"></a>関連項目

[分離した SharePoint Online チーム サイト](isolated-sharepoint-online-team-sites.md)
  
[分離した SharePoint Online チーム サイトの設計](design-an-isolated-sharepoint-online-team-site.md)
  
[セキュリティ ソリューション](security-solutions.md)

[分離した SharePoint Online チーム サイトの展開](deploy-an-isolated-sharepoint-online-team-site.md)



