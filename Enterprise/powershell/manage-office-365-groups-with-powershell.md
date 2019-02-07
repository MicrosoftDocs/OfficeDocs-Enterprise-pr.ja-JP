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
description: PowerShell のマイクロソフトの Office 365 のグループの一般的な管理タスクを実行する方法について説明します。
ms.openlocfilehash: 6d7841595315507b0b7f28f6b86f9349705f1d8b
ms.sourcegitcommit: 662d75796991bac4e959348ded4999008875422e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2019
ms.locfileid: "29760059"
---
# <a name="manage-office-365-groups-with-powershell"></a>PowerShell で Office 365 グループを管理する

 *最終更新 18 年 4 月、2018* 
  
PowerShell のマイクロソフト内のグループの一般的な管理タスクを行うための手順を説明します。PowerShell コマンドレットは、グループにも一覧表示されます。SharePoint サイトを管理する方法の詳細情報は、 [PowerShell を使用して SharePoint Online の管理のサイト](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)を参照してください。

## <a name="link-to-your-office-365-groups-usage-guidelines"></a>Office 365 グループの使用に関するガイドラインへのリンク
<a name="BK_LinkToGuideLines"> </a>

ユーザー[を作成または Outlook 内のグループを編集](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)、表示できます、組織の使用方法のガイドラインへのリンクです。たとえば、特定のプレフィックスを必要とするか、グループ名に追加するサフィックスがある場合です。
  
Azure Active Directory の PowerShell を使用して、Office 365 のグループに対して、組織の使用方法のガイドラインをユーザーをポイントします。[Azure Active Directory グループの設定を構成するコマンドレット](https://go.microsoft.com/fwlink/?LinkID=827484)を確認しの使用方法のガイドラインのハイパーリンクを定義するのには、**ディレクトリ レベルで設定を作成する**手順を実行します。1 回 AAD コマンドレットを実行すると、ユーザーの表示されます、ガイドラインへのリンクを作成または Outlook でグループを編集するとき。 
  
![使用法のガイドラインのリンクを使用して新しいグループを作成します。](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![グループ] をクリックして、組織の Office 365 の使用方法のガイドラインは、ガイドラインをグループ化します。](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a>Office 365 グループとユーザーが送信を許可します。
<a name="BK_LinkToGuideLines"> </a>
  
[Office 365 のグループとして送信する] を有効にする場合は、これを構成するのには、[追加 RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission)と[Get RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient)コマンドレットを使用します。この設定を有効にすると Office 365 ユーザーをグループ化は送信し、Office 365 のグループとしての電子メールに返信する Outlook または web 上の Outlook を使用できます。ユーザーがアクセスするグループに、新しいメール アドレスを作成し、グループの電子メール アドレスとして送信] フィールドに変更します。 

([またこれを行う Exchange 管理センターで](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)の)。
  
次を使用してスクリプトを作成、置換*\<GroupAlias\>* を更新するには、グループのエイリアスを持つと*\<UserAlias\>* アクセス許可を付与するユーザーのエイリアスを持つ。このスクリプトを実行する[Exchange のオンライン PowerShell への接続](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)をします。

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

コマンドレットを実行すると、ユーザーが **[差出人**] フィールドにグループの電子メール アドレスを追加することにより、グループとして送信するには、Outlook または Outlook web 上に移動できます。 

## <a name="create-classifications-for-office-groups-in-your-organization"></a>組織の Office グループに対する分類を作成する

組織内のユーザーが、Office 365 のグループを作成するときに設定する分類を作成します。などを作成するグループの「標準」、「秘密」、および「トップ シークレット」を設定するユーザーを許可できます。グループの分類は、既定で設定されていないし、それを設定するのには、ユーザーのために作成する必要があります。Azure Active Directory PowerShell を使用して、Office 365 のグループに対して、組織の使用方法のガイドラインをユーザーをポイントします。
  
[Azure Active Directory グループの設定を構成するコマンドレット](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets)を確認し、Office 365 のグループの分類を定義するのには**ディレクトリ レベルで設定を作成する**手順を実行します。 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

関連付ける各分類を使用することを説明するために属性を定義する*ClassificationDescriptions*の設定。
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

場所の分類は、ClassificationList 内の文字列と一致します。

例:
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

分類を設定するのには上記の Azure Active Directory のコマンドレットを実行した後、特定のグループの分類を設定する場合は、[セット UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup)コマンドレットを実行します。 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

または分類の新しいグループを作成します。
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

Exchange Online PowerShell の使い方の詳細については、「[Exchange Online による PowerShell の使用](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)」および「[リモート PowerShell による Exchange への接続](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)」をご覧ください。 
  
これらの設定を有効にすると、グループの所有者が同じ outlook および Outlook のメニューのドロップダウンから分類を選択し、グループの**編集**] ページから保存することができます。 
  
![Office 365 のグループの分類を選択します。](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a>グローバル アドレス一覧から Office 365 のグループを非表示にします。
<a name="BKMK_CreateClassification"> </a>

Office 365 グループがグローバル アドレス一覧 (GAL) と、組織内の他のリストに表示するかどうかを指定することができます。などの場合は、[アドレス] ボックスの一覧に表示したくない法務部門のグループがある場合は、グローバル アドレス一覧に表示されないようにするには、そのグループを停止できます。このようなアドレスの一覧からグループを非表示にする Set-Unified グループのコマンドレットを実行します。
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a>内部ユーザーのみが Office 365 のグループにメッセージを送信できるように
<a name="BKMK_CreateClassification"> </a>

その他の組織のユーザーに Office 365 のグループに電子メールを送信しない場合は、そのグループの設定を変更できます。グループに電子メールを送信する内部ユーザーのみが許可されます。外部ユーザーがそのグループにメッセージを送信しようとした場合に拒否されます。
  
次のように、この設定を更新するセット UnifiedGroup コマンドレットを実行するには。

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a>メール ヒントを Office 365 のグループに追加します。
<a name="BKMK_CreateClassification"> </a>

送信者は、Office 365 のグループに電子メールを送信しようとするたびに、それらに、MailTip を表示できます。
  
MailTip をグループに追加するのには Set-Unified グループのコマンドレットを実行します。

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

MailTip と、MailTipTranslations、MailTip の他の言語を指定するを設定することもできます。スペイン語の翻訳があるし、次のコマンドを実行するとします。
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a>Office 365 のグループの表示名を変更します。

表示名は、Office 365 のグループの名前を指定します。Exchange 管理センターまたは Office 365 管理ポータルでは、この名前を表示できます。グループの表示名を編集または、セット UnifiedGroup コマンドを実行して、既存の Office 365 グループに表示名を割り当てることができます。

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a>パブリックまたはプライベートに Outlook を Office 365 のグループの既定の設定を変更します。
<a name="BKMK_CreateClassification"> </a>

Office 365 デフォルトでは、Outlook 内のグループをプライベートとして作成されます。組織では、Office 365 のグループ (またはプライベートに) デフォルトで Public として作成する必要がある場合は、次の PowerShell コマンドレットの構文を使用します。
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
プライベートに設定します。
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
設定を確認します。 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
詳細については、[一連の OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig)と[Get OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig)を参照してください。
  
## <a name="office-365-groups-cmdlets"></a>Office 365 グループ コマンドレット

Office 365 のグループでは、次のコマンドレットを使用できます。
  
|**コマンドレット名**|**説明**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |このコマンドレットを使用して、Office 365 の既存のグループを検索し、グループ オブジェクトのプロパティを表示するのには  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |特定の Office 365 グループのプロパティを更新します。  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |Office 365 の新しいグループを作成します。このコマンドレットのパラメーターの最小限のセットを提供する、拡張プロパティの値の設定の新しいグループを作成した後セット UnifiedGroup を使用して  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |既存の Office 365 のグループを削除します。  <br/> |
|[Get UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Office 365 グループのメンバーシップ、および所有者の情報を取得します。  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |追加 100 個または数千のユーザー、または既存の Office 365 のグループに、新しい所有者の  <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |所有者およびメンバーを既存の Office 365 グループから削除します。  <br/> |
|[Get UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |アカウントに関連付けられているユーザーの写真についての情報を表示する場合に使用されます。ユーザーの写真は、Active Directory に格納されます。  <br/> |
|[セット UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |ユーザーの写真をアカウントに関連付ける場合に使用されます。ユーザーの写真は、Active Directory に格納されます。  <br/> |
|[削除 UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Office 365 のグループの写真を削除します。  <br/> |

## <a name="related-topics"></a>関連項目

[Office 365 のグループへのアップグレードの配布リスト](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[Office 365 グループを作成できるユーザーを管理する](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[Office 365 グループへのゲスト アクセスを管理する](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[動的に静的なグループ メンバーシップを変更します。](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
