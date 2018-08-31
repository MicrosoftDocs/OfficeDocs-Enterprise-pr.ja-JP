---
title: PowerShell を使用して Office 365 のグループを管理します。
ms.author: dianef
author: dianef77
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: 最終更新 18 年 4 月、2018
ms.openlocfilehash: 8def3b304a19ad57887c992aa6342ea2cf14ba28
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541864"
---
# <a name="manage-office-365-groups-with-powershell"></a><span data-ttu-id="7a90d-103">PowerShell を使用して Office 365 のグループを管理します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-103">Manage Office 365 Groups with PowerShell</span></span>

 <span data-ttu-id="7a90d-104">*最終更新 18 年 4 月、2018*</span><span class="sxs-lookup"><span data-stu-id="7a90d-104">*Last updated 18 April, 2018*</span></span> 
  
<span data-ttu-id="7a90d-p101">PowerShell のマイクロソフト内のグループの一般的な管理タスクを行うための手順を説明します。PowerShell コマンドレットは、グループにも一覧表示されます。SharePoint サイトを管理する方法の詳細情報は、[チーム サイトの管理と PowerShell を使用して通信のサイト](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a90d-p101">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell. It also lists the PowerShell cmdlets for Groups. For info about managing SharePoint sites, see [Manage team sites and communication sites by using PowerShell](https://support.office.com/article/52ecc2ab-88c3-486e-b8ff-ef6a968ccd87).</span></span>
  
## <a name="common-tasks-for-managing-office-365-groups"></a><span data-ttu-id="7a90d-108">Office 365 のグループを管理するための一般的なタスク</span><span class="sxs-lookup"><span data-stu-id="7a90d-108">Common tasks for managing Office 365 Groups</span></span>

- [<span data-ttu-id="7a90d-109">アップグレードの配布リストを Outlook の Office 365 のグループ</span><span class="sxs-lookup"><span data-stu-id="7a90d-109">Upgrade distribution lists to Office 365 Groups in Outlook</span></span>](https://support.office.com/article/787d7a75-e201-46f3-a242-f698162ff09f)
    
- [<span data-ttu-id="7a90d-110">Office 365 のグループを作成できるユーザーを管理します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-110">Manage who can create Office 365 Groups</span></span>](https://support.office.com/article/4c46c8cb-17d0-44b5-9776-005fced8e618)
    
- [<span data-ttu-id="7a90d-111">Office 365 のグループへのゲスト アクセスを管理します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-111">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/7c713d74-a144-4eab-92e7-d50df526ff96)
    
- [<span data-ttu-id="7a90d-112">Azure Active Directory での動的なグループを管理します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-112">Manage groups dynamically in Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/?linkid=847632)
    
- <span data-ttu-id="7a90d-113">数百または数千のユーザーを Office 365 のグループに追加、[追加 UnifiedGroupLinks コマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=616191)を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-113">Add hundreds or thousands of users to Office 365 groups, use the [Add-UnifiedGroupLinks cmdlet](https://go.microsoft.com/fwlink/p/?LinkId=616191).</span></span>
    
### <a name="link-to-your-office-365-groups-usage-guidelines"></a><span data-ttu-id="7a90d-114">Office 365 のグループの使用方法のガイドラインへのリンクします。</span><span class="sxs-lookup"><span data-stu-id="7a90d-114">Link to your Office 365 Groups usage guidelines</span></span>
<span data-ttu-id="7a90d-115"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="7a90d-115"></span></span>

<span data-ttu-id="7a90d-p102">[Outlook でグループを作成する](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102)、ユーザーことができますを表示すると、組織の使用方法のガイドラインへのリンク。たとえば、特定のプレフィックスを必要とするか、グループ名に追加するサフィックスがある場合です。</span><span class="sxs-lookup"><span data-stu-id="7a90d-p102">When users [Create a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102), you can show them a link to your organization's usage guidelines. For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="7a90d-p103">Azure Active Directory の PowerShell を使用して、Office 365 のグループに対して、組織の使用方法のガイドラインをユーザーをポイントします。[Azure Active Directory グループの設定を構成するコマンドレット](https://go.microsoft.com/fwlink/?LinkID=827484)を確認しの使用方法のガイドラインのハイパーリンクを定義するのには、**ディレクトリ レベルで設定を作成する**手順を実行します。1 回 AAD コマンドレットを実行すると、ユーザーの表示されます、ガイドラインへのリンクを作成または Outlook でグループを編集するとき。</span><span class="sxs-lookup"><span data-stu-id="7a90d-p103">Use the Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups. Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink. Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![使用法のガイドラインのリンクを使用して新しいグループを作成します。](./../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![グループ] をクリックして、組織の Office 365 の使用方法のガイドラインは、ガイドラインをグループ化します。](./../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
### <a name="allow-users-to-send-as-the-office-365-group"></a><span data-ttu-id="7a90d-123">Office 365 グループとユーザーが送信を許可します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-123">Allow users to Send as the Office 365 Group</span></span>
<span data-ttu-id="7a90d-124"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="7a90d-124"></span></span>

<span data-ttu-id="7a90d-p104">Exchange 管理センターでにも実行できます。[として送信したり、グループの代理で送信を許可するメンバー](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a90d-p104">You can also do this in the Exchange Admin Center. See [Allow members to send as or send on behalf of a Group](https://support.office.com/article/0ad41414-0cc6-4b97-90fb-06bec7bcf590).</span></span>
  
<span data-ttu-id="7a90d-p105">[Office 365 のグループとして送信する] を有効にする場合は、これを構成するのには、[追加 RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960)と[Get RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239)コマンドレットを使用します。この設定を有効にすると Office 365 ユーザーをグループ化は送信し、Office 365 のグループとしての電子メールに返信する Outlook または web 上の Outlook を使用できます。ユーザーがアクセスするグループに、新しいメール アドレスを作成し、グループの電子メール アドレスとして送信] フィールドに変更します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-p105">If you want to enable your Office 365 groups to "Send As", use the [Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960) and the [Get-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=733239) cmdlets to configure this. Once you enable this setting, Office 365 group users can use Outlook or Outlook on the web to send and reply to email as the Office 365 group. Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="7a90d-130">メッセージがグループに送信され、グループの会話で表示できるように、メールを「として送信」を作成するときに、グループの電子メール アドレスを **[cc]** フィールドに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a90d-130">You'll need to add the group email address to the **Cc** field when you compose the "send as" email, so that the message is sent to the Group and appears in group conversations.</span></span> 
  
<span data-ttu-id="7a90d-131">この時点では、メールボックス ポリシーを更新する唯一の方法は、 [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx)を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-131">At this time, the only way to update the mailbox policy is through [PowerShell](https://technet.microsoft.com/en-us/library/cc482986.aspx).</span></span>
  
- <span data-ttu-id="7a90d-132">グループのエイリアスを設定するのにには、このコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-132">Use this command to set the group alias.</span></span>
    
  ```
  $groupAlias = "TestSendAs"
  ```

- <span data-ttu-id="7a90d-133">ユーザーのエイリアスを設定するのにには、このコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-133">Use this command to set the user alias.</span></span>
    
  ```
  $userAlias = "User"
  ```

- <span data-ttu-id="7a90d-134">このコマンドを使用して、受信者の詳細を取得する Get 受信者のコマンドレットに、groupalias を渡します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-134">Use this command to pass the groupalias to the Get-Recipient cmdlet to get the recipient details.</span></span>
    
  ```
  $groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias
  ```

- <span data-ttu-id="7a90d-p106">対象の受信者の名前 (グループ名) を追加 RecipientPermission コマンドレットに渡す必要があります。トラスティ パラメーターには、対象となる送信者アクセス許可が与えられます useralias が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="7a90d-p106">Then the target recipient name (Group name) needs to be passed to the Add-RecipientPermission cmdlet. The useralias for whom the sendas permission will be given will be assigned to the -Trustee parameter.</span></span>
    
  ```
  Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
  ```

- <span data-ttu-id="7a90d-137">コマンドレットを実行すると、ユーザーが **[差出人**] フィールドにグループの電子メール アドレスを追加することにより、グループとして送信するには、Outlook または Outlook web 上に移動できます。</span><span class="sxs-lookup"><span data-stu-id="7a90d-137">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 
    
### <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="7a90d-138">組織で Office のグループの分類を作成します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-138">Create classifications for Office groups in your organization</span></span>
<span data-ttu-id="7a90d-139"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="7a90d-139"></span></span>

<span data-ttu-id="7a90d-p107">組織内のユーザーが、Office 365 のグループを作成するときに設定する分類を作成します。などを作成するグループの「標準」、「秘密」、および「トップ シークレット」を設定するユーザーを許可できます。グループの分類は、既定で設定されていないし、それを設定するのには、ユーザーのために作成する必要があります。Azure Active Directory PowerShell を使用して、Office 365 のグループに対して、組織の使用方法のガイドラインをユーザーをポイントします。</span><span class="sxs-lookup"><span data-stu-id="7a90d-p107">You can create classifications that the users in your organization can set when they create an Office 365 group. For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create. Group classifications aren't set by default and you need to create it in order for your users to set it. Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="7a90d-144">[Azure Active Directory グループの設定を構成するコマンドレット](https://go.microsoft.com/fwlink/?LinkID=827484)を確認し、Office 365 のグループの分類を定義するのには**ディレクトリ レベルで設定を作成する**手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-144">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="7a90d-145">関連付ける各分類を使用することを説明するために属性を定義する*ClassificationDescriptions*の設定。</span><span class="sxs-lookup"><span data-stu-id="7a90d-145">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions*  to define.</span></span> 
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description", where Classification matches the strings in the ClassificationList.
```

<span data-ttu-id="7a90d-146">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-146">For example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="7a90d-147">分類を設定するのには上記の Azure Active Directory のコマンドレットを実行した後、特定のグループの分類を設定する場合は、[セット UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189)コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-147">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=616189) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="7a90d-148">または分類の新しいグループを作成します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-148">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="7a90d-149">Exchange オンライン PowerShell を使用しての詳細については[Exchange Online に PowerShell を使用して](https://go.microsoft.com/fwlink/?LinkID=402831) [Exchange のオンライン PowerShell への接続](https://go.microsoft.com/fwlink/?LinkID=722415)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="7a90d-149">Check out [Using PowerShell with Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) and [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="7a90d-150">これらの設定を有効にすると、グループの所有者が同じ outlook および Outlook のメニューのドロップダウンから分類を選択し、グループの**編集**] ページから保存することができます。</span><span class="sxs-lookup"><span data-stu-id="7a90d-150">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Office 365 のグループの分類を選択します。](./../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
### <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="7a90d-152">グローバル アドレス一覧から Office 365 のグループを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="7a90d-152">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="7a90d-153"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="7a90d-153"></span></span>

<span data-ttu-id="7a90d-p108">Office 365 グループがグローバル アドレス一覧 (GAL) と、組織内の他のリストに表示するかどうかを指定することができます。などの場合は、[アドレス] ボックスの一覧に表示したくない法務部門のグループがある場合は、グローバル アドレス一覧に表示されないようにするには、そのグループを停止できます。このようなアドレスの一覧からグループを非表示にする Set-Unified グループの内線番号を実行します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-p108">You can specify whether a Office 365 group appears in the global address list (GAL) and other lists in your organization. For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL. Run the Set-Unified Group commandlet to hide the group from address list like this:</span></span>
  
```
  Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

### <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="7a90d-157">内部ユーザーのみが Office 365 のグループにメッセージを送信できるように</span><span class="sxs-lookup"><span data-stu-id="7a90d-157">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="7a90d-158"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="7a90d-158"></span></span>

<span data-ttu-id="7a90d-p109">その他の組織のユーザーに Office 365 のグループに電子メールを送信しない場合は、そのグループの設定を変更できます。グループに電子メールを送信する内部ユーザーのみが許可されます。外部ユーザーがそのグループにメッセージを送信しようとした場合に拒否されます。</span><span class="sxs-lookup"><span data-stu-id="7a90d-p109">If you don't want users from other organization to send email to a Office 365 group, you can change the settings for that group. It will allow only internal users to send an email to your group. If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="7a90d-162">次のように、この設定を更新するためのセット-UnifiedGroup 内線番号を実行します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-162">Run the Set-UnifiedGroup commandlet to update this setting, like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Internal senders only" - RequireSenderAuthenticationEnabled $true
```

### <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="7a90d-163">メール ヒントを Office 365 のグループに追加します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-163">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="7a90d-164"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="7a90d-164"></span></span>

<span data-ttu-id="7a90d-165">送信者は、Office 365 のグループに電子メールを送信しようとするたびに、彼に、MailTip を表示できます。</span><span class="sxs-lookup"><span data-stu-id="7a90d-165">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to him.</span></span>
  
<span data-ttu-id="7a90d-166">MailTip をグループに追加するのには Set-Unified グループの内線番号を実行します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-166">Run the Set-Unified Group commandlet to add a mailTip to the group:</span></span>
  
```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="7a90d-p110">MailTip、および設定することも、顧客から受け取ったその他の言語を指定する MailTipTranslations、MailTip。スペイン語の翻訳があるし、次のコマンドを実行するとします。</span><span class="sxs-lookup"><span data-stu-id="7a90d-p110">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages fro the MailTip. Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

### <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="7a90d-169">Office 365 のグループの表示名を変更します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-169">Change Display name of the Office 365 group</span></span>
<span data-ttu-id="7a90d-170"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="7a90d-170"></span></span>

<span data-ttu-id="7a90d-p111">表示名は、Office 365 のグループの名前を指定します。Exchange 管理センターまたは o365 管理ポータルでは、この名前を表示できます。グループの表示名を編集または、セット UnifiedGroup コマンドを実行して、既存の Office 365 のグループに表示名を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="7a90d-p111">Display name specifies the name of the Office 365 group. You can see this name in your exchange admin center or o365 admin portal. You can edit the display name of the group or assign a display name to an exisiting Office 365 group by running Set-UnifiedGroup command:</span></span>
  
```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

### <a name="manage-user-photos-in-office-365-groups"></a><span data-ttu-id="7a90d-174">Office 365 のグループ内のユーザーの写真を管理します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-174">Manage user photos in Office 365 Groups</span></span>
<span data-ttu-id="7a90d-175"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="7a90d-175"></span></span>

<span data-ttu-id="7a90d-176">| |</span><span class="sxs-lookup"><span data-stu-id="7a90d-176"></span></span>
|<span data-ttu-id="7a90d-177">**コマンドレット名**</span><span class="sxs-lookup"><span data-stu-id="7a90d-177">**Cmdlet name**</span></span>|<span data-ttu-id="7a90d-178">**説明**</span><span class="sxs-lookup"><span data-stu-id="7a90d-178">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="7a90d-179">Get UserPhoto</span><span class="sxs-lookup"><span data-stu-id="7a90d-179">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="7a90d-p112">アカウントに関連付けられているユーザーの写真についての情報を表示する場合に使用されます。ユーザーの写真は、Active Directory に格納されます。</span><span class="sxs-lookup"><span data-stu-id="7a90d-p112">Used to view information about the user photo associated with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="7a90d-182">セット UserPhoto</span><span class="sxs-lookup"><span data-stu-id="7a90d-182">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="7a90d-p113">ユーザーの写真をアカウントに関連付ける場合に使用されます。ユーザーの写真は、Active Directory に格納されます。</span><span class="sxs-lookup"><span data-stu-id="7a90d-p113">Used to associate a user photo with an account. User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="7a90d-185">削除 UserPhoto</span><span class="sxs-lookup"><span data-stu-id="7a90d-185">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="7a90d-186">Office 365 のグループの写真を削除します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-186">Remove the photo for an Office 365 group</span></span>  <br/> |
   
### <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="7a90d-187">パブリックまたはプライベートに Outlook を Office 365 のグループの既定の設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-187">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="7a90d-188"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="7a90d-188"></span></span>

<span data-ttu-id="7a90d-p114">Office 365 デフォルトでは、Outlook 内のグループをプライベートとして作成されます。組織では、既定で (プライベートに) は、パブリックとして作成するように Outlook を Office 365 のグループを希望する場合は、次の PowerShell コマンドレットの構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-p114">Office 365 Groups in Outlook are created as Private by default. If your organization wants Office 365 Groups for Outlook to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="7a90d-191">プライベートに設定します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-191">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="7a90d-192">設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-192">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="7a90d-193">詳細については、[一連の OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816)と[Get OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a90d-193">To learn more, see [Set-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871816) and [Get-OrganizationConfig](https://go.microsoft.com/fwlink/?linkid=871817).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="7a90d-194">Office 365 グループ コマンドレット</span><span class="sxs-lookup"><span data-stu-id="7a90d-194">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="7a90d-p115">次のコマンドレットでは、最近行った利用可能な Office 365 のグループにします。これらを使用できない場合、Office 365 サブスクリプションがまだ更新されていませんこの機能を持つ。メッセージ センターと[Office 365 のロードマップ](http://roadmap.office.com/en-us)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="7a90d-p115">The following cmdlets were recently made available to Office 365 Groups. If you aren't able to use these, your Office 365 subscription has not been updated with this functionality yet. Check your Message Center and the [Office 365 Roadmap](http://roadmap.office.com/en-us).</span></span>
  
<span data-ttu-id="7a90d-198">| |</span><span class="sxs-lookup"><span data-stu-id="7a90d-198"></span></span>
|<span data-ttu-id="7a90d-199">**コマンドレット名**</span><span class="sxs-lookup"><span data-stu-id="7a90d-199">**Cmdlet name**</span></span>|<span data-ttu-id="7a90d-200">**説明**</span><span class="sxs-lookup"><span data-stu-id="7a90d-200">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="7a90d-201">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="7a90d-201">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="7a90d-202">このコマンドレットを使用して、Office 365 の既存のグループを検索し、グループ オブジェクトのプロパティを表示するのには</span><span class="sxs-lookup"><span data-stu-id="7a90d-202">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="7a90d-203">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="7a90d-203">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="7a90d-204">特定の Office 365 グループのプロパティを更新します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-204">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="7a90d-205">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="7a90d-205">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="7a90d-p116">Office 365 の新しいグループを作成します。このコマンドレットのパラメーターの最小限のセットを提供する、拡張プロパティの値の設定の新しいグループを作成した後セット UnifiedGroup を使用して</span><span class="sxs-lookup"><span data-stu-id="7a90d-p116">Create a new Office 365 group. This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="7a90d-208">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="7a90d-208">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="7a90d-209">既存の Office 365 のグループを削除します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-209">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="7a90d-210">Get UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="7a90d-210">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="7a90d-211">Office 365 グループのメンバーシップ、および所有者の情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-211">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="7a90d-212">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="7a90d-212">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="7a90d-213">追加 100 個または数千のユーザー、または既存の Office 365 のグループに、新しい所有者の</span><span class="sxs-lookup"><span data-stu-id="7a90d-213">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="7a90d-214">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="7a90d-214">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="7a90d-215">所有者およびメンバーを既存の Office 365 グループから削除します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-215">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
   
## <a name="for-more-information"></a><span data-ttu-id="7a90d-216">詳細情報</span><span class="sxs-lookup"><span data-stu-id="7a90d-216">For more information</span></span>

- [<span data-ttu-id="7a90d-217">PowerShell を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a90d-217">Using PowerShell</span></span>](https://technet.microsoft.com/en-us/library/cc482986.aspx)
    
- [<span data-ttu-id="7a90d-218">Outlook Web App のメールボックス ポリシーをメールボックスで適用または削除する</span><span class="sxs-lookup"><span data-stu-id="7a90d-218">Apply or remove an Outlook Web App mailbox policy on a mailbox</span></span>](https://technet.microsoft.com/en-us/library/dd876884%28v=exchg.150%29.aspx)
    
- [<span data-ttu-id="7a90d-219">グループの名前付けポリシーを office 365</span><span class="sxs-lookup"><span data-stu-id="7a90d-219">Office 365 Groups naming policy</span></span>](https://support.office.com/article/6ceca4d3-cad1-4532-9f0f-d469dfbbb552)
    

