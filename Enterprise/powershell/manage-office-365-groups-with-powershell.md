---
title: PowerShell を使用して Microsoft 365 グループを管理する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: この記事では、PowerShell での Microsoft 365 グループの一般的な管理タスクの実行方法について説明します。
ms.openlocfilehash: 899205fbf53821758f848fd4e1c75f25fd16e223
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605953"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a><span data-ttu-id="ab849-103">PowerShell を使用して Microsoft 365 グループを管理する</span><span class="sxs-lookup"><span data-stu-id="ab849-103">Manage Microsoft 365 Groups with PowerShell</span></span>
 
<span data-ttu-id="ab849-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="ab849-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="ab849-105">この記事では、Microsoft PowerShell でグループの一般的な管理タスクを行うための手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab849-105">This article provides the steps for doing common management tasks for Groups in Microsoft PowerShell.</span></span> <span data-ttu-id="ab849-106">また、グループの PowerShell コマンドレットを示します。</span><span class="sxs-lookup"><span data-stu-id="ab849-106">It also lists the PowerShell cmdlets for Groups.</span></span> <span data-ttu-id="ab849-107">SharePoint サイトを管理する方法の詳細については、「[PowerShell を使用して SharePoint Online サイトを管理する](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab849-107">For info about managing SharePoint sites, see [Manage SharePoint Online sites using PowerShell](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell).</span></span>

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a><span data-ttu-id="ab849-108">Microsoft 365 グループの使用ガイドラインへのリンク</span><span class="sxs-lookup"><span data-stu-id="ab849-108">Link to your Microsoft 365 Groups usage guidelines</span></span>
<span data-ttu-id="ab849-109"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="ab849-109"><a name="BK_LinkToGuideLines"> </a></span></span>

<span data-ttu-id="ab849-110">ユーザーが [Outlook でグループを作成または編集](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)するときに、組織での使用に関するガイドラインへのリンクをそのユーザーに表示することができます。</span><span class="sxs-lookup"><span data-stu-id="ab849-110">When users [create or edit a group in Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), you can show them a link to your organization's usage guidelines.</span></span> <span data-ttu-id="ab849-111">たとえば、グループ名に特定のプレフィックスまたはサフィックスを追加する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="ab849-111">For example, if you require a specific prefix or suffix to be added to a group name.</span></span>
  
<span data-ttu-id="ab849-112">Azure Active Directory (Azure AD) PowerShell を使用して、Microsoft 365 グループの組織の使用ガイドラインをユーザーに示します。</span><span class="sxs-lookup"><span data-stu-id="ab849-112">Use the Azure Active Directory (Azure AD) PowerShell to point your users to your organization's usage guidelines for Microsoft 365 groups.</span></span> <span data-ttu-id="ab849-113">「[グループの設定を構成するための Azure Active Directory コマンドレット](https://go.microsoft.com/fwlink/?LinkID=827484)」の「**ディレクトリ レベルでの設定の作成**」の手順に従って、使用ガイドラインのハイパーリンクを定義します。</span><span class="sxs-lookup"><span data-stu-id="ab849-113">Check out [Azure Active Directory cmdlets for configuring group settings](https://go.microsoft.com/fwlink/?LinkID=827484) and follow the steps in the **Create settings at the directory level** to define the usage guideline hyperlink.</span></span> <span data-ttu-id="ab849-114">AAD コマンドレットを実行すると、ユーザーが Outlook でグループを作成または編集するときに、ガイドラインへのリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab849-114">Once you run the AAD cmdlet, user's will see the link to your guidelines when they create or edit a group in Outlook.</span></span> 
  
![使用ガイドラインのリンクがある新しいグループを作成する](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)
  
![グループ使用ガイドラインをクリックして、組織の Office 365 グループのガイドラインを参照する](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)
  
## <a name="allow-users-to-send-as-the-microsoft-365-group"></a><span data-ttu-id="ab849-117">ユーザーが Microsoft 365 グループとして送信できるようにする</span><span class="sxs-lookup"><span data-stu-id="ab849-117">Allow users to Send as the Microsoft 365 Group</span></span>
<span data-ttu-id="ab849-118"><a name="BK_LinkToGuideLines"> </a></span><span class="sxs-lookup"><span data-stu-id="ab849-118"><a name="BK_LinkToGuideLines"> </a></span></span>
  
<span data-ttu-id="ab849-119">Microsoft 365 グループを [送信者として送信] にできるようにする場合は、この機能を構成するために、[アドインのアクセス許可](https://docs.microsoft.com/powershell/module/exchange/Add-RecipientPermission)と対象ユーザーの[アクセス許可](https://docs.microsoft.com/powershell/module/exchange/Get-Recipient)のコマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="ab849-119">If you want to enable your Microsoft 365 groups to "Send As", use the [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Add-RecipientPermission) and the [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/Get-Recipient) cmdlets to configure this.</span></span> <span data-ttu-id="ab849-120">この設定を有効にすると、Microsoft 365 グループのユーザーは、Outlook または web 上の Outlook を使用して、Microsoft 365 グループとして電子メールを送信および返信できます。</span><span class="sxs-lookup"><span data-stu-id="ab849-120">Once you enable this setting, Microsoft 365 group users can use Outlook or Outlook on the web to send and reply to email as the Microsoft 365 group.</span></span> <span data-ttu-id="ab849-121">ユーザーはグループに移動し、新しいメールを作成して、「メールボックス所有者として送信する」フィールドをグループのメール アドレスに変更することができます。</span><span class="sxs-lookup"><span data-stu-id="ab849-121">Users can go to the group, create a new email, and change the "Send As" field to the group's email address.</span></span> 

<span data-ttu-id="ab849-122">([Exchange 管理センターでもこれを行うことができます](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)。)</span><span class="sxs-lookup"><span data-stu-id="ab849-122">([You can also do this in the Exchange Admin Center](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)</span></span>
  
<span data-ttu-id="ab849-123">次のスクリプトを使用して、 *\<GroupAlias\>* 更新するグループのエイリアスと、 *\<UserAlias\>* アクセス許可を付与するユーザーのエイリアスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ab849-123">Use the following script, replacing *\<GroupAlias\>* with the alias of the group that you want to update, and *\<UserAlias\>* with the alias of the user to whom you want to grant permissions.</span></span> <span data-ttu-id="ab849-124">[Exchange Online PowerShell に接続し](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)、このスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="ab849-124">[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) to run this script.</span></span>

```PowerShell
$groupAlias = "<GroupAlias>"

$userAlias = "<UserAlias>"


$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

<span data-ttu-id="ab849-125">コマンドレットが実行されると、**From** フィールドにグループ メール アドレスを追加することにより、ユーザーが Outlook または Outlook on the web に移動して、グループとして送信することができます。</span><span class="sxs-lookup"><span data-stu-id="ab849-125">Once the cmdlet is executed, users can go to Outlook or Outlook on the web to send as the group, by adding the group email address to the **From** field.</span></span> 

## <a name="create-classifications-for-office-groups-in-your-organization"></a><span data-ttu-id="ab849-126">組織の Office グループの分類を作成する</span><span class="sxs-lookup"><span data-stu-id="ab849-126">Create classifications for Office groups in your organization</span></span>

<span data-ttu-id="ab849-127">組織内のユーザーが Microsoft 365 グループを作成するときに設定できる機密ラベルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ab849-127">You can create sensitivity labels that the users in your organization can set when they create a Microsoft 365 Group.</span></span> <span data-ttu-id="ab849-128">グループを分類する場合は、前のグループ分類機能ではなく、機密ラベルを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ab849-128">If you want to classify groups, we recommend using sensitivity labels instead of the previous groups classification feature.</span></span> <span data-ttu-id="ab849-129">機密ラベルの使用方法については、「 [Microsoft Teams、microsoft 365 グループ、および SharePoint サイトのコンテンツを保護するための機密情報を使用する](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab849-129">For information about using sensitivity labels, see [Use sensitivity labels to protect content in Microsoft Teams, Microsoft 365 groups, and SharePoint sites](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab849-130">現在、分類ラベルを使用している場合、グループを作成するユーザーは、機密ラベルが有効になっていても使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ab849-130">If you are currently using classification labels, they will no longer be available to users who create groups once sensitivity labels are enabled.</span></span>

<span data-ttu-id="ab849-131">以前のグループ分類機能を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ab849-131">You can still use the previous groups classification feature.</span></span> <span data-ttu-id="ab849-132">組織内のユーザーが Office 365 グループを作成するときに設定できる分類を作成できます。</span><span class="sxs-lookup"><span data-stu-id="ab849-132">You can create classifications that the users in your organization can set when they create an Office 365 group.</span></span> <span data-ttu-id="ab849-133">たとえば、作成するグループにユーザーが「標準」、「機密」、「極秘」といった分類を設定できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ab849-133">For example, you can allow users to set "Standard", "Secret", and "Top Secret" on groups they create.</span></span> <span data-ttu-id="ab849-134">グループの分類は既定では設定されていないので、ユーザーに分類を設定させるには、分類を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab849-134">Group classifications aren't set by default and you need to create it in order for your users to set it.</span></span> <span data-ttu-id="ab849-135">組織の Office 365 グループ使用ガイドラインをユーザーに参照させるには、Azure Active Directory PowerShell を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab849-135">Use Azure Active Directory PowerShell to point your users to your organization's usage guidelines for Office 365 groups.</span></span>
  
<span data-ttu-id="ab849-136">「[グループの設定を構成するための Azure Active Directory コマンドレット](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets)」の「**ディレクトリ レベルでの設定の作成**」の手順に従って、Office 365 グループの分類を定義します。</span><span class="sxs-lookup"><span data-stu-id="ab849-136">Check out [Azure Active Directory cmdlets for configuring group settings](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) and follow the steps in the **Create settings at the directory level** to define the classification for Office 365 groups.</span></span> 
  
```
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

<span data-ttu-id="ab849-137">各分類に説明を関連付けるために、定義する設定属性 *ClassificationDescriptions* を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ab849-137">In order to associate a description to each classification you can use the settings attribute  *ClassificationDescriptions* to define.</span></span>
  
```
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

<span data-ttu-id="ab849-138">ここで、Classification は ClassificationList の文字列と一致します。</span><span class="sxs-lookup"><span data-stu-id="ab849-138">where Classification matches the strings in the ClassificationList.</span></span>

<span data-ttu-id="ab849-139">例:</span><span class="sxs-lookup"><span data-stu-id="ab849-139">Example:</span></span>
  
```
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

<span data-ttu-id="ab849-140">上の Azure Active Directory コマンドレットを実行して分類を設定した後、特定のグループに分類を設定する場合は、[Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/Set-UnifiedGroup) コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="ab849-140">After you run the above Azure Active Directory cmdlet to set your classification, run the [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/Set-UnifiedGroup) cmdlet if you want to set the classification for a specific group.</span></span> 
  
```
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact> 
```

<span data-ttu-id="ab849-141">または、分類を使用して新しいグループを作成します。</span><span class="sxs-lookup"><span data-stu-id="ab849-141">Or create a new group with a classification.</span></span>
  
```
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public> 
```

<span data-ttu-id="ab849-142">Exchange Online PowerShell の使用の詳細については、「[Exchange Online による PowerShell の使用](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)」および「[Exchange Online PowerShell への接続](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab849-142">Check out [Using PowerShell with Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) for more details on using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="ab849-143">これらの設定を有効にした後、グループの所有者は、Outlook on the web および Outlook​​ のドロップダウン メニューから分類を選択し、[**編集**] グループ ページから分類を保存できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ab849-143">Once these settings are enabled, the group owner will be able to choose a classification from the drop down menu in Outlook on the Web and Outlook, and save it from the **Edit** group page.</span></span> 
  
![Office 365 グループの分類を選択する](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)
  
## <a name="hide-office-365-groups-from-gal"></a><span data-ttu-id="ab849-145">GAL から Office 365 グループを非表示にする</span><span class="sxs-lookup"><span data-stu-id="ab849-145">Hide Office 365 Groups from GAL</span></span>
<span data-ttu-id="ab849-146"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="ab849-146"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="ab849-147">組織内のグローバルアドレス一覧 (GAL) およびその他のリストに Office 365 グループを表示するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ab849-147">You can specify whether an Office 365 group appears in the global address list (GAL) and other lists in your organization.</span></span> <span data-ttu-id="ab849-148">たとえば、アドレス一覧に表示したくない法務部グループがある場合は、GAL にそのグループを表示しないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ab849-148">For example, if you have a legal department group that you don't want to show up in the address list, you can stop that group from appearing in GAL.</span></span> <span data-ttu-id="ab849-149">アドレス一覧からグループを非表示にするには、次のように Set-UnifiedGroup コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="ab849-149">Run the Set-Unified Group cmdlet to hide the group from address list like this:</span></span>
  
```
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-office-365-group"></a><span data-ttu-id="ab849-150">Office 365 グループへのメッセージの送信を内部ユーザーにのみ許可する</span><span class="sxs-lookup"><span data-stu-id="ab849-150">Allow only internal users to send message to Office 365 group</span></span>
<span data-ttu-id="ab849-151"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="ab849-151"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="ab849-152">他の組織のユーザーが Office 365 グループに電子メールを送信できないようにするには、そのグループの設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="ab849-152">If you don't want users from other organization to send email to an Office 365 group, you can change the settings for that group.</span></span> <span data-ttu-id="ab849-153">これにより、内部のユーザーのみがグループにメールを送信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ab849-153">It will allow only internal users to send an email to your group.</span></span> <span data-ttu-id="ab849-154">外部ユーザーがそのグループにメッセージを送信しようとしても、拒否されます。</span><span class="sxs-lookup"><span data-stu-id="ab849-154">If external user try to send message to that group they will be rejected.</span></span>
  
<span data-ttu-id="ab849-155">この設定を更新するには、次のように Set-UnifiedGroup コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="ab849-155">Run the Set-UnifiedGroup cmdlet to update this setting, like this:</span></span>

```
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-the-office-365-groups"></a><span data-ttu-id="ab849-156">Office 365 グループにメール ヒントを追加する</span><span class="sxs-lookup"><span data-stu-id="ab849-156">Add MailTips to the Office 365 Groups</span></span>
<span data-ttu-id="ab849-157"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="ab849-157"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="ab849-158">送信者が Office 365 グループにメールを送信しようとするたびに、メール ヒントが表示されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ab849-158">Whenever a sender tries to send an email to an Office 365 group, a MailTip can be shown to them.</span></span>
  
<span data-ttu-id="ab849-159">グループにメール ヒントを追加するには、Set-UnifiedGroup コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="ab849-159">Run the Set-Unified Group cmdlet to add a mailTip to the group:</span></span>

```
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

<span data-ttu-id="ab849-160">メール ヒントと共に、MailTipTranslations を設定することもできます。これは、メール ヒントの追加言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab849-160">Along with MailTip, you can also set MailTipTranslations, which specifies additional languages for the MailTip.</span></span> <span data-ttu-id="ab849-161">スペイン語の翻訳を追加するとします。この場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ab849-161">Suppose you want to have the Spanish translation, then run the following command:</span></span>
  
```
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-display-name-of-the-office-365-group"></a><span data-ttu-id="ab849-162">Office 365 グループの表示名を変更する</span><span class="sxs-lookup"><span data-stu-id="ab849-162">Change Display name of the Office 365 group</span></span>

<span data-ttu-id="ab849-163">表示名は、Office 365 グループの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab849-163">Display name specifies the name of the Office 365 group.</span></span> <span data-ttu-id="ab849-164">この名前は、exchange 管理センターまたは Microsoft 365 管理センターで確認できます。</span><span class="sxs-lookup"><span data-stu-id="ab849-164">You can see this name in your exchange admin center or Microsoft 365 admin center.</span></span> <span data-ttu-id="ab849-165">Set-UnifiedGroup コマンドを実行して、グループの表示名を編集するか、既存の Office 365 グループに表示名を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="ab849-165">You can edit the display name of the group or assign a display name to an existing Office 365 group by running the Set-UnifiedGroup command:</span></span>

```
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-office-365-groups-for-outlook-to-public-or-private"></a><span data-ttu-id="ab849-166">Outlook 用 Office 365 グループの既定の設定を公開または非公開に変更する</span><span class="sxs-lookup"><span data-stu-id="ab849-166">Change the default setting of Office 365 Groups for Outlook to Public or Private</span></span>
<span data-ttu-id="ab849-167"><a name="BKMK_CreateClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="ab849-167"><a name="BKMK_CreateClassification"> </a></span></span>

<span data-ttu-id="ab849-168">Outlook の Office 365 グループは、既定で非公開として作成されます。</span><span class="sxs-lookup"><span data-stu-id="ab849-168">Office 365 Groups in Outlook are created as Private by default.</span></span> <span data-ttu-id="ab849-169">組織が既定で Office 365 グループを公開として作成する (または非公開に戻す) 場合は、次の PowerShell コマンドレット構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab849-169">If your organization wants Office 365 Groups to be created as Public by default (or back to Private), use this PowerShell cmdlet syntax:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Public`
  
<span data-ttu-id="ab849-170">非公開に設定するには:</span><span class="sxs-lookup"><span data-stu-id="ab849-170">To set to Private:</span></span>
  
 `Set-OrganizationConfig -DefaultGroupAccessType Private`
  
<span data-ttu-id="ab849-171">設定を確認するには:</span><span class="sxs-lookup"><span data-stu-id="ab849-171">To verify the setting:</span></span> 
  
 `Get-OrganizationConfig | ft DefaultGroupAccessType`
  
<span data-ttu-id="ab849-172">詳細については、「[Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig)」および「[Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/Get-OrganizationConfig)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab849-172">To learn more, see [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig) and [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/Get-OrganizationConfig).</span></span>
  
## <a name="office-365-groups-cmdlets"></a><span data-ttu-id="ab849-173">Office 365 グループのコマンドレット</span><span class="sxs-lookup"><span data-stu-id="ab849-173">Office 365 Groups cmdlets</span></span>

<span data-ttu-id="ab849-174">次のコマンドレットは、Office 365 グループで使用できます。</span><span class="sxs-lookup"><span data-stu-id="ab849-174">The following cmdlets can be used with Office 365 Groups.</span></span>
  
|<span data-ttu-id="ab849-175">**コマンドレット名**</span><span class="sxs-lookup"><span data-stu-id="ab849-175">**Cmdlet name**</span></span>|<span data-ttu-id="ab849-176">**Description**</span><span class="sxs-lookup"><span data-stu-id="ab849-176">**Description**</span></span>|
|:-----|:-----|
|[<span data-ttu-id="ab849-177">Get-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="ab849-177">Get-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |<span data-ttu-id="ab849-178">既存の Office 365 グループを検索し、グループ オブジェクトのプロパティを表示するには、このコマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="ab849-178">Use this cmdlet to look up existing Office 365 Groups, and to view properties of the group object</span></span>  <br/> |
|[<span data-ttu-id="ab849-179">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="ab849-179">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |<span data-ttu-id="ab849-180">特定の Office 365 グループのプロパティを更新します。</span><span class="sxs-lookup"><span data-stu-id="ab849-180">Update the properties of a specific Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="ab849-181">New-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="ab849-181">New-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |<span data-ttu-id="ab849-182">新しい Office 365 グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="ab849-182">Create a new Office 365 group.</span></span> <span data-ttu-id="ab849-183">このコマンドレットに用意されているパラメーター セットは最小限です。拡張プロパティの値を設定するには、新しいグループを作成した後に Set-UnifiedGroup を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab849-183">This cmdlet provides a minimal set of parameters, for setting values for extended properties use Set-UnifiedGroup after creating the new group</span></span>  <br/> |
|[<span data-ttu-id="ab849-184">Remove-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="ab849-184">Remove-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |<span data-ttu-id="ab849-185">既存の Office 365 グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="ab849-185">Delete an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="ab849-186">Get-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="ab849-186">Get-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |<span data-ttu-id="ab849-187">Office 365 グループのメンバーシップと所有者情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="ab849-187">Retrieve membership and owner information for an Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="ab849-188">Add-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="ab849-188">Add-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |<span data-ttu-id="ab849-189">数百、数千人のユーザー (新しい所有者) を既存の Office 365 グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="ab849-189">Add hundred or thousands of users, or new owners, to an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="ab849-190">Remove-UnifiedGroupLinks</span><span class="sxs-lookup"><span data-stu-id="ab849-190">Remove-UnifiedGroupLinks</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |<span data-ttu-id="ab849-191">所有者とメンバーを既存の Office 365 グループから削除します。</span><span class="sxs-lookup"><span data-stu-id="ab849-191">Remove owners and members from an existing Office 365 Group</span></span>  <br/> |
|[<span data-ttu-id="ab849-192">Get-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="ab849-192">Get-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |<span data-ttu-id="ab849-193">アカウントと関連付けられたユーザーの写真について情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="ab849-193">Used to view information about the user photo associated with an account.</span></span> <span data-ttu-id="ab849-194">パスワードは Active Directory に格納されます。</span><span class="sxs-lookup"><span data-stu-id="ab849-194">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="ab849-195">Set-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="ab849-195">Set-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |<span data-ttu-id="ab849-196">ユーザーの写真をアカウントに関連付けるために使用します。</span><span class="sxs-lookup"><span data-stu-id="ab849-196">Used to associate a user photo with an account.</span></span> <span data-ttu-id="ab849-197">パスワードは Active Directory に格納されます。</span><span class="sxs-lookup"><span data-stu-id="ab849-197">User photos are stored in Active Directory</span></span>  <br/> |
|[<span data-ttu-id="ab849-198">Remove-UserPhoto</span><span class="sxs-lookup"><span data-stu-id="ab849-198">Remove-UserPhoto</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |<span data-ttu-id="ab849-199">Office 365 グループの写真を削除します。</span><span class="sxs-lookup"><span data-stu-id="ab849-199">Remove the photo for an Office 365 group</span></span>  <br/> |

## <a name="related-topics"></a><span data-ttu-id="ab849-200">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab849-200">Related topics</span></span>

[<span data-ttu-id="ab849-201">配布リストを Office 365 グループにアップグレードする</span><span class="sxs-lookup"><span data-stu-id="ab849-201">Upgrade distribution lists to Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/manage/upgrade-distribution-lists)

[<span data-ttu-id="ab849-202">Office 365 グループを作成できるユーザーを管理する</span><span class="sxs-lookup"><span data-stu-id="ab849-202">Manage who can create Office 365 Groups</span></span>](https://docs.microsoft.com/office365/admin/create-groups/manage-creation-of-groups)

[<span data-ttu-id="ab849-203">Office 365 グループへのゲスト アクセスを管理する</span><span class="sxs-lookup"><span data-stu-id="ab849-203">Manage guest access to Office 365 Groups</span></span>](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[<span data-ttu-id="ab849-204">静的なグループメンバーシップを動的に変更する</span><span class="sxs-lookup"><span data-stu-id="ab849-204">Change static group membership to dynamic in</span></span>](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
