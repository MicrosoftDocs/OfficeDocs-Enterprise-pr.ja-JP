---
title: PowerShell で Office 365 グループを管理する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Microsoft PowerShell で Office 365 グループの一般的な管理タスクを実行する方法について説明します。
ms.openlocfilehash: 6d7841595315507b0b7f28f6b86f9349705f1d8b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491764"
---
# <a name="manage-office-365-groups-with-powershell"></a>PowerShell で Office 365 グループを管理する

 *最終更新日2018年4月18日* 
  
この記事では、Microsoft PowerShell のグループに共通の管理タスクを実行する手順について説明します。 また、グループの PowerShell コマンドレットも一覧表示します。 sharepoint サイトの管理の詳細については、「 [PowerShell を使用した sharepoint Online サイトの管理](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)」を参照してください。

## <a name="link-to-your-office-365-groups-usage-guidelines"></a>Office 365 グループの使用に関するガイドラインへのリンク
<a name="BK_LinkToGuideLines"> </a>

ユーザーが[Outlook でグループを作成または編集](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)するときに、組織の使用ガイドラインへのリンクを表示することができます。 たとえば、特定のプレフィックスまたはサフィックスをグループ名に追加する必要がある場合などです。
  
Azure Active Directory PowerShell を使用して、Office 365 グループの組織の使用ガイドラインをユーザーに指定します。 [グループ設定を構成するための Azure Active Directory コマンドレット](https://go.microsoft.com/fwlink/?LinkID=827484)をチェックアウトし、「**設定をディレクトリレベルで作成**する」の手順に従って、使用法のガイドラインへのハイパーリンクを定義します。 AAD コマンドレットを実行すると、Outlook でグループを作成または編集するときに、ユーザーにはガイドラインへのリンクが表示されます。 
  
![利用状況ガイドラインリンクを使用して新しいグループを作成する](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![[グループの使用ガイドライン] をクリックして組織を表示する Office 365 グループのガイドライン](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a>ユーザーが Office 365 グループとして送信できるようにする
<a name="BK_LinkToGuideLines"> </a>
  
Office 365 グループを "送信者として送信" にできるようにするには、[追加のアクセス許可](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission)と、各ユーザーの[アクセス許可](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient)のコマンドレットを使用してこれを構成します。 この設定を有効にすると、office 365 グループのユーザーは、outlook または web 上の outlook を使用して、office 365 グループとして電子メールを送信および返信できます。 ユーザーはグループに移動し、新しい電子メールを作成し、"送信者" フィールドをグループの電子メールアドレスに変更できます。 

([これを Exchange 管理センターで行うこともでき](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)ます。)
  
次のスクリプトを使用して、 * \<groupalias\> *を更新するグループのエイリアスに置き換え、permssions を付与するユーザーのエイリアスを* \<useralias\> *に置き換えます。 [Exchange Online PowerShell に接続](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)してこのスクリプトを実行します。

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

コマンドレットを実行すると、グループの電子メールアドレスを**From**フィールドに追加することにより、ユーザーが outlook または web 上の outlook に移動してグループとして送信できるようになります。 

## <a name="create-classifications-for-office-groups-in-your-organization"></a>組織の Office グループに対する分類を作成する

組織内のユーザーが Office 365 グループを作成するときに設定できる分類を作成できます。 たとえば、ユーザーが作成したグループに "標準"、"secret"、"Top secret" の設定を許可できます。 グループの分類は既定では設定されておらず、ユーザーが設定できるようにするために作成する必要があります。 Azure Active Directory PowerShell を使用して、Office 365 グループの組織の使用ガイドラインをユーザーに指定します。
  
[グループ設定を構成するための Azure Active Directory コマンドレット](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets)をチェックアウトし、「**ディレクトリレベルで設定を作成**する」の手順に従って Office 365 グループの分類を定義します。 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

各分類に説明を関連付けるには、settings 属性*ClassificationDescriptions*を使用して定義します。
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

分類が ClassificationList 内の文字列と一致する場合。

例:
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

前述の Azure Active Directory コマンドレットを実行して分類を設定した後、特定のグループの分類を設定する場合は、 [set-unifiedgroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup)コマンドレットを実行します。 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

または、分類を使用して新しいグループを作成します。
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

Exchange Online PowerShell の使い方の詳細については、「[Exchange Online による PowerShell の使用](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)」および「[リモート PowerShell による Exchange への接続](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)」をご覧ください。 
  
これらの設定を有効にすると、グループの所有者は、outlook on the Web および outlook のドロップダウンメニューから分類を選択して、[グループの**編集**] ページから保存することができます。 
  
![Office 365 グループの分類を選択する](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a>Office 365 グループを GAL から非表示にする
<a name="BKMK_CreateClassification"> </a>

組織内のグローバルアドレス一覧 (GAL) およびその他のリストに Office 365 グループを表示するかどうかを指定できます。 たとえば、アドレス一覧に表示したくない法務部門のグループがある場合は、そのグループが GAL に表示されないようにすることができます。 Set 統合グループコマンドレットを実行して、次のようにグループをアドレス一覧から非表示にします。
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>Office 365 グループへのメッセージの送信を内部ユーザーにのみ許可する
<a name="BKMK_CreateClassification"> </a>

他の組織のユーザーが Office 365 グループに電子メールを送信できないようにするには、そのグループの設定を変更します。 内部ユーザーのみがグループに電子メールを送信できるようになります。 外部ユーザーがこのグループにメッセージを送信しようとすると、拒否されます。
  
この設定を更新するには、次のように set-unifiedgroup コマンドレットを実行します。

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a>Office 365 グループにメールヒントを追加する
<a name="BKMK_CreateClassification"> </a>

送信者が Office 365 グループに電子メールを送信しようとするたびに、メールヒントを表示できます。
  
Set 統合グループコマンドレットを実行して、グループにメールヒントを追加します。

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

メールヒントと共に、mailtip 翻訳を設定して、メールヒントに追加の言語を指定することもできます。 スペイン語の翻訳を取得する場合は、次のコマンドを実行します。
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a>Office 365 グループの表示名を変更する

[表示名] Office 365 グループの名前を指定します。 この名前は、exchange 管理センターまたは Office 365 管理ポータルに表示されます。 set-unifiedgroup コマンドを実行すると、グループの表示名を編集したり、既存の Office 365 グループに表示名を割り当てることができます。

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>Outlook の Office 365 グループの既定の設定をパブリックまたはプライベートに変更する
<a name="BKMK_CreateClassification"> </a>

既定では、Outlook の Office 365 グループはプライベートとして作成されます。 組織で Office 365 グループを既定でパブリックとして作成する (またはプライベートに戻す) 必要がある場合は、次の PowerShell コマンドレット構文を使用します。
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
Private に設定するには:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
設定を確認するには、次のようにします。 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
詳細については[](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) 、「」を参照[](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig)してください。
  
## <a name="office-365-groups-cmdlets"></a>Office 365 グループのコマンドレット

Office 365 グループでは、次のコマンドレットを使用できます。
  
|**コマンドレット名**|**説明**|
|:-----|:-----|
|[set-unifiedgroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |このコマンドレットを使用して、既存の Office 365 グループを検索し、グループオブジェクトのプロパティを表示します。  <br/> |
|[set-unifiedgroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |特定の Office 365 グループのプロパティを更新する  <br/> |
|[set-unifiedgroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |新しい Office 365 グループを作成します。 このコマンドレットは、最小限のパラメーターセットを提供します。拡張プロパティの値を設定するには、新しいグループを作成した後で set-unifiedgroup を使用します。  <br/> |
|[set-unifiedgroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |既存の Office 365 グループを削除する  <br/> |
|[UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Office 365 グループのメンバーシップと所有者の情報を取得する  <br/> |
|[UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |既存の Office 365 グループに100人または数千のユーザー、または新しい所有者を追加する  <br/> |
|[UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |既存の Office 365 グループから所有者とメンバーを削除する  <br/> |
|[取得-userphoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |アカウントに関連付けられたユーザーの写真に関する情報を表示するために使用します。 ユーザーの写真は Active Directory に格納されます。  <br/> |
|[設定-userphoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |ユーザーの写真をアカウントに関連付けるために使用します。 ユーザーの写真は Active Directory に格納されます。  <br/> |
|[削除-userphoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Office 365 グループの写真を削除する  <br/> |

## <a name="related-topics"></a>関連トピック

[配布リストを Office 365 グループにアップグレードする](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[Office 365 グループを作成できるユーザーを管理する](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[Office 365 グループへのゲスト アクセスを管理する](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[の静的グループのメンバーシップを動的に変更する](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
