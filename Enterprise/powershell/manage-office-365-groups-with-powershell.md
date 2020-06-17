---
title: PowerShell で Office 365 グループを管理する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords: CSH
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
ms.openlocfilehash: 71d48b133ce716995ec6059a60a0fed487fde208
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2020
ms.locfileid: "44736025"
---
# <a name="manage-office-365-groups-with-powershell"></a>PowerShell で Office 365 グループを管理する
 
この記事では、Microsoft PowerShell でグループの一般的な管理タスクを行うための手順について説明します。 また、グループの PowerShell コマンドレットを示します。 SharePoint サイトを管理する方法の詳細については、「[PowerShell を使用して SharePoint Online サイトを管理する](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)」を参照してください。

## <a name="link-to-your-office-365-groups-usage-guidelines"></a>Office 365 グループの使用に関するガイドラインへのリンク
<a name="BK_LinkToGuideLines"> </a>

ユーザーが [Outlook でグループを作成または編集](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)するときに、組織での使用に関するガイドラインへのリンクをそのユーザーに表示することができます。 たとえば、グループ名に特定のプレフィックスまたはサフィックスを追加する必要がある場合があります。
  
組織の Office 365 グループ使用ガイドラインをユーザーに参照させるには、Azure Active Directory PowerShell を使用します。 「[グループの設定を構成するための Azure Active Directory コマンドレット](https://go.microsoft.com/fwlink/?LinkID=827484)」の「**ディレクトリ レベルでの設定の作成**」の手順に従って、使用ガイドラインのハイパーリンクを定義します。 AAD コマンドレットを実行すると、ユーザーが Outlook でグループを作成または編集するときに、ガイドラインへのリンクが表示されます。 
  
![使用ガイドラインのリンクがある新しいグループを作成する](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![グループ使用ガイドラインをクリックして、組織の Office 365 グループのガイドラインを参照する](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a>ユーザーが Office 365 グループとして送信することを許可する
<a name="BK_LinkToGuideLines"> </a>
  
Office 365 グループの「メールボックス所有者として送信する」を有効にする場合は、[Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Add-RecipientPermission) と [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Get-Recipient) コマンドレットを使用して構成します。 この設定を有効にすると、Office 365 グループのユーザーは Outlook または Outlook on the web を使用して、Office 365 グループとしてメールを送信および返信することができます。 ユーザーはグループに移動し、新しいメールを作成して、「メールボックス所有者として送信する」フィールドをグループのメール アドレスに変更することができます。 

([Exchange 管理センターでもこれを行うことができます](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)。)
  
次のスクリプトを使用して、 *\<GroupAlias\>* 更新するグループのエイリアスと、 *\<UserAlias\>* アクセス許可を付与するユーザーのエイリアスを使用します。 [Exchange Online PowerShell に接続し](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)、このスクリプトを実行します。

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

コマンドレットが実行されると、**From** フィールドにグループ メール アドレスを追加することにより、ユーザーが Outlook または Outlook on the web に移動して、グループとして送信することができます。 

## <a name="create-classifications-for-office-groups-in-your-organization"></a>組織の Office グループの分類を作成する

組織内のユーザーが Microsoft 365 グループを作成するときに設定できる機密ラベルを作成できます。 グループを分類する場合は、前のグループ分類機能ではなく、機密ラベルを使用することをお勧めします。 機密ラベルの使用方法については、「 [Microsoft Teams、microsoft 365 グループ、および SharePoint サイトのコンテンツを保護するための機密情報を使用する](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)」を参照してください。

> [!IMPORTANT]
> 現在、分類ラベルを使用している場合、グループを作成するユーザーは、機密ラベルが有効になっていても使用できなくなります。

以前のグループ分類機能を使用することもできます。 組織内のユーザーが Office 365 グループを作成するときに設定できる分類を作成できます。 たとえば、作成するグループにユーザーが「標準」、「機密」、「極秘」といった分類を設定できるようにすることができます。 グループの分類は既定では設定されていないので、ユーザーに分類を設定させるには、分類を作成する必要があります。 組織の Office 365 グループ使用ガイドラインをユーザーに参照させるには、Azure Active Directory PowerShell を使用します。
  
「[グループの設定を構成するための Azure Active Directory コマンドレット](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets)」の「**ディレクトリ レベルでの設定の作成**」の手順に従って、Office 365 グループの分類を定義します。 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

各分類に説明を関連付けるために、定義する設定属性 *ClassificationDescriptions* を使用できます。
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

ここで、Classification は ClassificationList の文字列と一致します。

例:
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

上の Azure Active Directory コマンドレットを実行して分類を設定した後、特定のグループに分類を設定する場合は、[Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/Set-UnifiedGroup) コマンドレットを実行します。 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

または、分類を使用して新しいグループを作成します。
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

Exchange Online PowerShell の使用の詳細については、「[Exchange Online による PowerShell の使用](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)」および「[Exchange Online PowerShell への接続](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)」を参照してください。 
  
これらの設定を有効にした後、グループの所有者は、Outlook on the web および Outlook​​ のドロップダウン メニューから分類を選択し、[**編集**] グループ ページから分類を保存できるようになります。 
  
![Office 365 グループの分類を選択する](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a>GAL から Office 365 グループを非表示にする
<a name="BKMK_CreateClassification"> </a>

組織内のグローバルアドレス一覧 (GAL) およびその他のリストに Office 365 グループを表示するかどうかを指定できます。 たとえば、アドレス一覧に表示したくない法務部グループがある場合は、GAL にそのグループを表示しないようにすることができます。 アドレス一覧からグループを非表示にするには、次のように Set-UnifiedGroup コマンドレットを実行します。
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>Office 365 グループへのメッセージの送信を内部ユーザーにのみ許可する
<a name="BKMK_CreateClassification"> </a>

他の組織のユーザーが Office 365 グループに電子メールを送信できないようにするには、そのグループの設定を変更します。 これにより、内部のユーザーのみがグループにメールを送信できるようになります。 外部ユーザーがそのグループにメッセージを送信しようとしても、拒否されます。
  
この設定を更新するには、次のように Set-UnifiedGroup コマンドレットを実行します。

```
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a>Office 365 グループにメール ヒントを追加する
<a name="BKMK_CreateClassification"> </a>

送信者が Office 365 グループにメールを送信しようとするたびに、メール ヒントが表示されるようにすることができます。
  
グループにメール ヒントを追加するには、Set-UnifiedGroup コマンドレットを実行します。

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

メール ヒントと共に、MailTipTranslations を設定することもできます。これは、メール ヒントの追加言語を指定します。 スペイン語の翻訳を追加するとします。この場合は、次のコマンドを実行します。
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a>Office 365 グループの表示名を変更する

表示名は、Office 365 グループの名前を指定します。 この名前は、exchange 管理センターまたは Microsoft 365 管理センターで確認できます。 Set-UnifiedGroup コマンドを実行して、グループの表示名を編集するか、既存の Office 365 グループに表示名を割り当てることができます。

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>Outlook 用 Office 365 グループの既定の設定を公開または非公開に変更する
<a name="BKMK_CreateClassification"> </a>

Outlook の Office 365 グループは、既定で非公開として作成されます。 組織が既定で Office 365 グループを公開として作成する (または非公開に戻す) 場合は、次の PowerShell コマンドレット構文を使用します。
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
非公開に設定するには:
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
設定を確認するには: 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
詳細については、「[Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig)」および「[Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/Get-OrganizationConfig)」を参照してください。
  
## <a name="office-365-groups-cmdlets"></a>Office 365 グループのコマンドレット

次のコマンドレットは、Office 365 グループで使用できます。
  
|**コマンドレット名**|**Description**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |既存の Office 365 グループを検索し、グループ オブジェクトのプロパティを表示するには、このコマンドレットを使用します。  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |特定の Office 365 グループのプロパティを更新します。  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |新しい Office 365 グループを作成します。 このコマンドレットに用意されているパラメーター セットは最小限です。拡張プロパティの値を設定するには、新しいグループを作成した後に Set-UnifiedGroup を使用します。  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |既存の Office 365 グループを削除します。  <br/> |
|[Get-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Office 365 グループのメンバーシップと所有者情報を取得します。  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |数百、数千人のユーザー (新しい所有者) を既存の Office 365 グループに追加します。  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |所有者とメンバーを既存の Office 365 グループから削除します。  <br/> |
|[Get-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |アカウントと関連付けられたユーザーの写真について情報を表示します。 パスワードは Active Directory に格納されます。  <br/> |
|[Set-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |ユーザーの写真をアカウントに関連付けるために使用します。 パスワードは Active Directory に格納されます。  <br/> |
|[Remove-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Office 365 グループの写真を削除します。  <br/> |

## <a name="related-topics"></a>関連項目

[配布リストを Office 365 グループにアップグレードする](https://docs.microsoft.com/office365/admin/manage/upgrade-distribution-lists)

[Office 365 グループを作成できるユーザーを管理する](https://docs.microsoft.com/office365/admin/create-groups/manage-creation-of-groups)

[Office 365 グループへのゲスト アクセスを管理する](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[静的なグループメンバーシップを動的に変更する](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
