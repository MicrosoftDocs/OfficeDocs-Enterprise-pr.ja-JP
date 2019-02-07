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
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="f68e6-103">PowerShell で Office 365 グループを管理する</span><span class="sxs-lookup"><span data-stu-id="f68e6-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="f68e6-104">*最終更新 18 年 4 月、2018*</span><span class="sxs-lookup"><span data-stu-id="f68e6-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="f68e6-p101">PowerShell のマイクロソフト内のグループの一般的な管理タスクを行うための手順を説明します。PowerShell コマンドレットは、グループにも一覧表示されます。SharePoint サイトを管理する方法の詳細情報は、 [PowerShell を使用して SharePoint Online の管理のサイト](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f68e6-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="f68e6-108">Office 365 グループの使用に関するガイドラインへのリンク</span><span class="sxs-lookup"><span data-stu-id="f68e6-108">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="f68e6-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="f68e6-109"></span></span>

<span data-ttu-id="f68e6-p102">ユーザー[を作成または Outlook 内のグループを編集](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)、表示できます、組織の使用方法のガイドラインへのリンクです。たとえば、特定のプレフィックスを必要とするか、グループ名に追加するサフィックスがある場合です。</span><span class="sxs-lookup"><span data-stu-id="f68e6-p102">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="f68e6-p103">Azure Active Directory の PowerShell を使用して、Office 365 のグループに対して、組織の使用方法のガイドラインをユーザーをポイントします。[Azure Active Directory グループの設定を構成するコマンドレット](https://go.microsoft.com/fwlink/?LinkID=827484)を確認しの使用方法のガイドラインのハイパーリンクを定義するのには、**ディレクトリ レベルで設定を作成する**手順を実行します。1 回 AAD コマンドレットを実行すると、ユーザーの表示されます、ガイドラインへのリンクを作成または Outlook でグループを編集するとき。</span><span class="sxs-lookup"><span data-stu-id="f68e6-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![使用法のガイドラインのリンクを使用して新しいグループを作成します。](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![グループ] をクリックして、組織の Office 365 の使用方法のガイドラインは、ガイドラインをグループ化します。](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="f68e6-117">Office 365 グループとユーザーが送信を許可します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-117">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="f68e6-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="f68e6-118"></span></span>
  
<span data-ttu-id="f68e6-p104">[Office 365 のグループとして送信する] を有効にする場合は、これを構成するのには、[追加 RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission)と[Get RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient)コマンドレットを使用します。この設定を有効にすると Office 365 ユーザーをグループ化は送信し、Office 365 のグループとしての電子メールに返信する Outlook または web 上の Outlook を使用できます。ユーザーがアクセスするグループに、新しいメール アドレスを作成し、グループの電子メール アドレスとして送信] フィールドに変更します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-p104">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="f68e6-122">([またこれを行う Exchange 管理センターで](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)の)。</span><span class="sxs-lookup"><span data-stu-id="f68e6-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/en-us/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="f68e6-p105">次を使用してスクリプトを作成、置換*\<GroupAlias\>* を更新するには、グループのエイリアスを持つと*\<UserAlias\>* アクセス許可を付与するユーザーのエイリアスを持つ。このスクリプトを実行する[Exchange のオンライン PowerShell への接続](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)をします。</span><span class="sxs-lookup"><span data-stu-id="f68e6-p105">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permssions. [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="f68e6-125">コマンドレットを実行すると、ユーザーが **[差出人**] フィールドにグループの電子メール アドレスを追加することにより、グループとして送信するには、Outlook または Outlook web 上に移動できます。</span><span class="sxs-lookup"><span data-stu-id="f68e6-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="f68e6-126">組織の Office グループに対する分類を作成する</span><span class="sxs-lookup"><span data-stu-id="f68e6-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="f68e6-p106">組織内のユーザーが、Office 365 のグループを作成するときに設定する分類を作成します。などを作成するグループの「標準」、「秘密」、および「トップ シークレット」を設定するユーザーを許可できます。グループの分類は、既定で設定されていないし、それを設定するのには、ユーザーのために作成する必要があります。Azure Active Directory PowerShell を使用して、Office 365 のグループに対して、組織の使用方法のガイドラインをユーザーをポイントします。</span><span class="sxs-lookup"><span data-stu-id="f68e6-p106">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="f68e6-131">[Azure Active Directory グループの設定を構成するコマンドレット](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets)を確認し、Office 365 のグループの分類を定義するのには**ディレクトリ レベルで設定を作成する**手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-131">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="f68e6-132">関連付ける各分類を使用することを説明するために属性を定義する*ClassificationDescriptions*の設定。</span><span class="sxs-lookup"><span data-stu-id="f68e6-132">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="f68e6-133">場所の分類は、ClassificationList 内の文字列と一致します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-133">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="f68e6-134">例:</span><span class="sxs-lookup"><span data-stu-id="f68e6-134">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="f68e6-135">分類を設定するのには上記の Azure Active Directory のコマンドレットを実行した後、特定のグループの分類を設定する場合は、[セット UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup)コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-135">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="f68e6-136">または分類の新しいグループを作成します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-136">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="f68e6-137">Exchange Online PowerShell の使い方の詳細については、「[Exchange Online による PowerShell の使用](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)」および「[リモート PowerShell による Exchange への接続](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f68e6-137">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="f68e6-138">これらの設定を有効にすると、グループの所有者が同じ outlook および Outlook のメニューのドロップダウンから分類を選択し、グループの**編集**] ページから保存することができます。</span><span class="sxs-lookup"><span data-stu-id="f68e6-138">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Office 365 のグループの分類を選択します。](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="f68e6-140">グローバル アドレス一覧から Office 365 のグループを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="f68e6-140">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="f68e6-141"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="f68e6-141"></span></span>

<span data-ttu-id="f68e6-p107">Office 365 グループがグローバル アドレス一覧 (GAL) と、組織内の他のリストに表示するかどうかを指定することができます。などの場合は、[アドレス] ボックスの一覧に表示したくない法務部門のグループがある場合は、グローバル アドレス一覧に表示されないようにするには、そのグループを停止できます。このようなアドレスの一覧からグループを非表示にする Set-Unified グループのコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-p107">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="f68e6-145">内部ユーザーのみが Office 365 のグループにメッセージを送信できるように</span><span class="sxs-lookup"><span data-stu-id="f68e6-145">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="f68e6-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="f68e6-146"></span></span>

<span data-ttu-id="f68e6-p108">その他の組織のユーザーに Office 365 のグループに電子メールを送信しない場合は、そのグループの設定を変更できます。グループに電子メールを送信する内部ユーザーのみが許可されます。外部ユーザーがそのグループにメッセージを送信しようとした場合に拒否されます。</span><span class="sxs-lookup"><span data-stu-id="f68e6-p108">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="f68e6-150">次のように、この設定を更新するセット UnifiedGroup コマンドレットを実行するには。</span><span class="sxs-lookup"><span data-stu-id="f68e6-150">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="f68e6-151">メール ヒントを Office 365 のグループに追加します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-151">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="f68e6-152"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="f68e6-152"></span></span>

<span data-ttu-id="f68e6-153">送信者は、Office 365 のグループに電子メールを送信しようとするたびに、それらに、MailTip を表示できます。</span><span class="sxs-lookup"><span data-stu-id="f68e6-153">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="f68e6-154">MailTip をグループに追加するのには Set-Unified グループのコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-154">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="f68e6-p109">MailTip と、MailTipTranslations、MailTip の他の言語を指定するを設定することもできます。スペイン語の翻訳があるし、次のコマンドを実行するとします。</span><span class="sxs-lookup"><span data-stu-id="f68e6-p109">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="f68e6-157">Office 365 のグループの表示名を変更します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-157">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="f68e6-p110">表示名は、Office 365 のグループの名前を指定します。Exchange 管理センターまたは Office 365 管理ポータルでは、この名前を表示できます。グループの表示名を編集または、セット UnifiedGroup コマンドを実行して、既存の Office 365 グループに表示名を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="f68e6-p110">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or Office 365 admin portal. You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="f68e6-161">パブリックまたはプライベートに Outlook を Office 365 のグループの既定の設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-161">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="f68e6-162"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="f68e6-162"></span></span>

<span data-ttu-id="f68e6-p111">Office 365 デフォルトでは、Outlook 内のグループをプライベートとして作成されます。組織では、Office 365 のグループ (またはプライベートに) デフォルトで Public として作成する必要がある場合は、次の PowerShell コマンドレットの構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-p111">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="f68e6-165">プライベートに設定します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-165">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="f68e6-166">設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-166">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="f68e6-167">詳細については、[一連の OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig)と[Get OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f68e6-167">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="f68e6-168">Office 365 グループ コマンドレット</span><span class="sxs-lookup"><span data-stu-id="f68e6-168">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="f68e6-169">Office 365 のグループでは、次のコマンドレットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f68e6-169">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="f68e6-170">**コマンドレット名**</span><span class="sxs-lookup"><span data-stu-id="f68e6-170">**Cmdlet name**</span></span>|<span data-ttu-id="f68e6-171">**説明**</span><span class="sxs-lookup"><span data-stu-id="f68e6-171">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="f68e6-172">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="f68e6-172">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="f68e6-173">このコマンドレットを使用して、Office 365 の既存のグループを検索し、グループ オブジェクトのプロパティを表示するのには</span><span class="sxs-lookup"><span data-stu-id="f68e6-173">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="f68e6-174">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="f68e6-174">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="f68e6-175">特定の Office 365 グループのプロパティを更新します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-175">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="f68e6-176">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="f68e6-176">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="f68e6-p112">Office 365 の新しいグループを作成します。このコマンドレットのパラメーターの最小限のセットを提供する、拡張プロパティの値の設定の新しいグループを作成した後セット UnifiedGroup を使用して</span><span class="sxs-lookup"><span data-stu-id="f68e6-p112">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="f68e6-179">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="f68e6-179">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="f68e6-180">既存の Office 365 のグループを削除します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-180">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="f68e6-181">Get UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="f68e6-181">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="f68e6-182">Office 365 グループのメンバーシップ、および所有者の情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-182">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="f68e6-183">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="f68e6-183">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="f68e6-184">追加 100 個または数千のユーザー、または既存の Office 365 のグループに、新しい所有者の</span><span class="sxs-lookup"><span data-stu-id="f68e6-184">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="f68e6-185">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="f68e6-185">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="f68e6-186">所有者およびメンバーを既存の Office 365 グループから削除します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-186">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="f68e6-187">Get UserPhoto</span><span class="sxs-lookup"><span data-stu-id="f68e6-187">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="f68e6-p113">アカウントに関連付けられているユーザーの写真についての情報を表示する場合に使用されます。ユーザーの写真は、Active Directory に格納されます。</span><span class="sxs-lookup"><span data-stu-id="f68e6-p113">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="f68e6-190">セット UserPhoto</span><span class="sxs-lookup"><span data-stu-id="f68e6-190">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="f68e6-p114">ユーザーの写真をアカウントに関連付ける場合に使用されます。ユーザーの写真は、Active Directory に格納されます。</span><span class="sxs-lookup"><span data-stu-id="f68e6-p114">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="f68e6-193">削除 UserPhoto</span><span class="sxs-lookup"><span data-stu-id="f68e6-193">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="f68e6-194">Office 365 のグループの写真を削除します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-194">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="f68e6-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="f68e6-195">Related topics</span></span>

[<span data-ttu-id="f68e6-196">Office 365 のグループへのアップグレードの配布リスト</span><span class="sxs-lookup"><span data-stu-id="f68e6-196">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="f68e6-197">Office 365 グループを作成できるユーザーを管理する</span><span class="sxs-lookup"><span data-stu-id="f68e6-197">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/en-us/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="f68e6-198">Office 365 グループへのゲスト アクセスを管理する</span><span class="sxs-lookup"><span data-stu-id="f68e6-198">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="f68e6-199">動的に静的なグループ メンバーシップを変更します。</span><span class="sxs-lookup"><span data-stu-id="f68e6-199">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
