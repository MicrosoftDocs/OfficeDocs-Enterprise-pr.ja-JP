---
title: Office 365 へのディレクトリ同期を通してユーザーをプロビジョニングするための準備
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: ディレクトリ同期を使用して Office 365 にユーザーをプロビジョニングするための準備方法と、この方法を使用する長期的な利点について説明します。
ms.openlocfilehash: af402950b3681285898d0d87b897d363a693bf98
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085106"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a><span data-ttu-id="cc3a6-103">Office 365 へのディレクトリ同期を通してユーザーをプロビジョニングするための準備</span><span class="sxs-lookup"><span data-stu-id="cc3a6-103">Prepare to provision users through directory synchronization to Office 365</span></span>

<span data-ttu-id="cc3a6-p101">ディレクトリ同期を使用するユーザーのプロビジョニングには、Office 365 で職場または学校のアカウントを直接管理するよりも多くの計画と準備が必要です。オンプレミスの active directory が Azure active directory に適切に同期されるようにするには、追加の計画と準備のタスクが必要です。組織には、次のような利点が追加されています。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p101">Provisioning users with directory synchronization requires more planning and preparation than simply managing your work or school account directly in Office 365. The additional planning and preparation tasks are required to ensure that your on-premises Active Directory synchronizes properly to Azure Active Directory. The added benefits to your organization include:</span></span>
  
- <span data-ttu-id="cc3a6-107">組織の管理プログラムの削減</span><span class="sxs-lookup"><span data-stu-id="cc3a6-107">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="cc3a6-108">オプションでシングルサインオンのシナリオを有効にする</span><span class="sxs-lookup"><span data-stu-id="cc3a6-108">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="cc3a6-109">Office 365 でのアカウントの変更の自動化</span><span class="sxs-lookup"><span data-stu-id="cc3a6-109">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="cc3a6-110">ディレクトリ同期を使用する利点の詳細については、「[ディレクトリ同期のロードマップ]( https://go.microsoft.com/fwlink/p/?LinkId=525398)」および「 [Office 365 id と Azure Active directory につい](about-office-365-identity.md)て」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-110">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
<span data-ttu-id="cc3a6-111">組織に最適なシナリオを特定するには、[ディレクトリ統合ツールの比較](https://go.microsoft.com/fwlink/p/?LinkId=525320)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-111">To determine which scenario is the best for your organization, review the [directory integration tools comparison](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span></span>
  
## <a name="directory-cleanup-tasks"></a><span data-ttu-id="cc3a6-112">ディレクトリのクリーンアップタスク</span><span class="sxs-lookup"><span data-stu-id="cc3a6-112">Directory cleanup tasks</span></span>

<span data-ttu-id="cc3a6-113">ディレクトリの同期を開始する前に、ディレクトリをクリーンアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-113">Before you begin synchronizing your directory, you need to clean up your directory.</span></span>
  
<span data-ttu-id="cc3a6-114">azure [AD Connect によって azure Active Directory に同期](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)された属性も確認します。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-114">Review also the [attributes synchronized to Azure Active Directory by Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="cc3a6-p102">同期の前にディレクトリのクリーンアップを実行しないと、展開プロセスに重大な悪影響が発生する可能性があります。ディレクトリ同期のサイクルを経て、エラーを特定し、再同期を実行するまでに、数日または数週間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p102">If you don't perform directory cleanup before you synchronize, there can be a significant negative effect on the deployment process. It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="cc3a6-117">オンプレミスディレクトリで、次のクリーンアップタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-117">In your on-premises directory, complete the following clean-up tasks:</span></span>
  
1. <span data-ttu-id="cc3a6-118">Office 365 サービスが割り当てられる各ユーザーについて、**proxyAddresses** 属性のメール アドレスが有効かつ一意であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-118">Ensure that each user who will be assigned Office 365 service offerings has a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="cc3a6-119">**proxyAddresses** 属性に重複する値が存在する場合は削除します。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-119">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="cc3a6-p103">可能な場合は、Office 365 サービスオファーリングを割り当てる各ユーザーに、ユーザーの**ユーザー**オブジェクトの**userPrincipalName**属性に有効な一意の値を指定します。最適な同期処理を行うには、オンプレミスの Active Directory upn がクラウド UPN に一致していることを確認してください。ユーザーが**userPrincipalName**属性の値を持っていない場合は、**ユーザー**オブジェクトに**sAMAccountName**属性の有効な一意の値が含まれている必要があります。**userPrincipalName**属性の重複する値を削除します。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p103">If possible, ensure that each user who will be assigned Office 365 service offerings has a valid and unique value for the **userPrincipalName** attribute in the user's **user** object. For best synchronization experience, ensure that the on-premises Active Directory UPN matches the cloud UPN. If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute. Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="cc3a6-124">グローバル アドレス一覧 (GAL) を最適に利用できるように、以下の属性の情報が正しいことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-124">For optimal use of the global address list (GAL), be sure the information in the following attributes is correct:</span></span>
    
  - <span data-ttu-id="cc3a6-125">givenName </span><span class="sxs-lookup"><span data-stu-id="cc3a6-125">givenName</span></span>
  - <span data-ttu-id="cc3a6-126">姓</span><span class="sxs-lookup"><span data-stu-id="cc3a6-126">surname</span></span>
  - <span data-ttu-id="cc3a6-127">displayName</span><span class="sxs-lookup"><span data-stu-id="cc3a6-127">displayName</span></span>
  - <span data-ttu-id="cc3a6-128">役職</span><span class="sxs-lookup"><span data-stu-id="cc3a6-128">Job Title</span></span>
  - <span data-ttu-id="cc3a6-129">部署</span><span class="sxs-lookup"><span data-stu-id="cc3a6-129">Department</span></span>
  - <span data-ttu-id="cc3a6-130">事業所</span><span class="sxs-lookup"><span data-stu-id="cc3a6-130">Office</span></span>
  - <span data-ttu-id="cc3a6-131">事業所電話番号</span><span class="sxs-lookup"><span data-stu-id="cc3a6-131">Office Phone</span></span>
  - <span data-ttu-id="cc3a6-132">携帯電話</span><span class="sxs-lookup"><span data-stu-id="cc3a6-132">Mobile Phone</span></span>
  - <span data-ttu-id="cc3a6-133">FAX 番号</span><span class="sxs-lookup"><span data-stu-id="cc3a6-133">Fax Number</span></span>
  - <span data-ttu-id="cc3a6-134">番地</span><span class="sxs-lookup"><span data-stu-id="cc3a6-134">Street Address</span></span>
  - <span data-ttu-id="cc3a6-135">市区町村</span><span class="sxs-lookup"><span data-stu-id="cc3a6-135">City</span></span>
  - <span data-ttu-id="cc3a6-136">都道府県</span><span class="sxs-lookup"><span data-stu-id="cc3a6-136">State or Province</span></span>
  - <span data-ttu-id="cc3a6-137">郵便番号</span><span class="sxs-lookup"><span data-stu-id="cc3a6-137">Zip or Postal Code</span></span>
  - <span data-ttu-id="cc3a6-138">国または地域</span><span class="sxs-lookup"><span data-stu-id="cc3a6-138">Country or Region</span></span>
    
## <a name="directory-object-and-attribute-preparation"></a><span data-ttu-id="cc3a6-139">ディレクトリ オブジェクトおよび属性の準備</span><span class="sxs-lookup"><span data-stu-id="cc3a6-139">Directory object and attribute preparation</span></span>

<span data-ttu-id="cc3a6-p104">オンプレミスディレクトリと Office 365 との間のディレクトリ同期を正常に行うには、オンプレミスのディレクトリ属性が適切に準備されている必要があります。たとえば、Office 365 環境と同期されている特定の属性に特定の文字が使用されないようにする必要があります。予期しない文字によってディレクトリ同期が失敗することはありませんが、警告が返されることがあります。無効な文字は、ディレクトリ同期が失敗する原因となります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p104">Successful directory synchronization between your on-premises directory and Office 365 requires that your on-premises directory attributes are properly prepared. For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment. Unexpected characters do not cause directory synchronization to fail but might return a warning. Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="cc3a6-p105">Active directory ユーザーの一部に1つ以上の重複した属性がある場合も、ディレクトリ同期は失敗します。各ユーザーは固有の属性を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p105">Directory synchronization will also fail if some of your Active Directory users have one or more duplicate attributes. Each user must have unique attributes.</span></span>
  
<span data-ttu-id="cc3a6-146">準備する必要がある属性を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-146">The attributes that you need to prepare are listed here:</span></span>
  
 <span data-ttu-id="cc3a6-147">**注:**[idfix ツール](install-and-run-idfix.md)を使用して、このプロセスを非常に簡単にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-147">**NOTE:** You can also use the [IdFix tool](install-and-run-idfix.md) to make this process a lot easier.</span></span> 
  
- <span data-ttu-id="cc3a6-148">**displayName**</span><span class="sxs-lookup"><span data-stu-id="cc3a6-148">**displayName**</span></span>
    
  - <span data-ttu-id="cc3a6-149">この属性がユーザー オブジェクトに存在する場合は、Office 365 と同期されます。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-149">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="cc3a6-p106">この属性がユーザー オブジェクトに存在する場合、値を割り当てる必要があります。この属性を空白にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p106">If this attribute exists in the user object, there must be a value for it. That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="cc3a6-152">最大文字数: 256</span><span class="sxs-lookup"><span data-stu-id="cc3a6-152">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="cc3a6-153">\*\*givenName \*\*</span><span class="sxs-lookup"><span data-stu-id="cc3a6-153">**givenName**</span></span>
    
  - <span data-ttu-id="cc3a6-154">ユーザー オブジェクトに存在する場合、この属性は Office 365 と同期されますが、Office 365 ではこの属性を必要とせず、使用されません。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-154">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="cc3a6-155">最大文字数: 64</span><span class="sxs-lookup"><span data-stu-id="cc3a6-155">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="cc3a6-156">**mail**</span><span class="sxs-lookup"><span data-stu-id="cc3a6-156">**mail**</span></span>
    
  - <span data-ttu-id="cc3a6-157">この属性値は、ディレクトリ内で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-157">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="cc3a6-p107">重複する値がある場合、値を持つ最初のユーザーが同期されます。以降のユーザーは、Office 365 に表示されません。両方のユーザーが office 365 に表示されるようにするには、office 365 の値を変更するか、オンプレミスのディレクトリの両方の値を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p107">If there are duplicate values, the first user with the value is synchronized. Subsequent users will not appear in Office 365. You must modify either the value in Office 365, or modify both of the values in the on-premises directory in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="cc3a6-161">**mailNickname** (Exchange エイリアス)</span><span class="sxs-lookup"><span data-stu-id="cc3a6-161">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="cc3a6-162">属性値はピリオド (.) で始めることはできません。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-162">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="cc3a6-163">この属性値は、ディレクトリ内で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-163">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="cc3a6-164">\*\*proxyAddresses \*\*</span><span class="sxs-lookup"><span data-stu-id="cc3a6-164">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="cc3a6-165">複数値の属性</span><span class="sxs-lookup"><span data-stu-id="cc3a6-165">Multiple-value attribute</span></span>
  - <span data-ttu-id="cc3a6-166">1 つの値に使用できる最大文字数:256</span><span class="sxs-lookup"><span data-stu-id="cc3a6-166">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="cc3a6-167">属性の値にスペースを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-167">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="cc3a6-168">この属性値は、ディレクトリ内で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-168">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="cc3a6-169">無効な文字\< \> : ();, [ ] "</span><span class="sxs-lookup"><span data-stu-id="cc3a6-169">Invalid characters: \< \> ( ) ; , [ ] "</span></span>
    
    <span data-ttu-id="cc3a6-170">無効な文字は、SMTP:User@contso.com が許可されていても、SMTP:user:M@contoso.com は許可されていませんが、型区切り記号の後の文字と ":" に適用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-170">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="cc3a6-p108">すべての簡易メール転送プロトコル (SMTP) アドレスは、電子メールメッセージング標準に準拠している必要があります。重複しているまたは不要なアドレスが存在する場合は、ヘルプトピックの「 [Exchange での重複および不要なプロキシアドレスの削除](https://go.microsoft.com/fwlink/?LinkId=293860)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p108">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards. If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="cc3a6-173">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="cc3a6-173">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="cc3a6-174">最大文字数: 20</span><span class="sxs-lookup"><span data-stu-id="cc3a6-174">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="cc3a6-175">この属性値は、ディレクトリ内で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-175">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="cc3a6-p109">無効な文字: [\ "|,/ \< \> : + =;?\* ]</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p109">Invalid characters: [ \ " | , / : \< \> + = ; ? \* ]</span></span>
  - <span data-ttu-id="cc3a6-178">ユーザーの **sAMAccountName** 属性が無効で、**userPrincipalName** 属性が有効な場合、ユーザー アカウントは Office 365 に作成されます。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-178">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="cc3a6-179">**sAMAccountName**と**userPrincipalName**の両方が無効な場合は、オンプレミスの Active Directory **userprincipalname**属性を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-179">If both **sAMAccountName** and **userPrincipalName** are invalid, the on-premises Active Directory **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="cc3a6-180">**sn** (姓)</span><span class="sxs-lookup"><span data-stu-id="cc3a6-180">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="cc3a6-181">ユーザー オブジェクトに存在する場合、この属性は Office 365 と同期されますが、Office 365 ではこの属性を必要とせず、使用されません。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-181">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="cc3a6-182">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="cc3a6-182">**targetAddress**</span></span>
    
    <span data-ttu-id="cc3a6-p110">ユーザーに対して設定されている**targetAddress**属性 (たとえば、SMTP:tom@contoso.com) を Office 365 GAL に表示する必要があります。サードパーティ製のメッセージング移行シナリオでは、オンプレミスのディレクトリに Office 365 スキーマ拡張が必要になります。office 365 スキーマ拡張機能は、オンプレミスディレクトリからのディレクトリ同期ツールを使用して設定された office 365 オブジェクトを管理するための便利な属性も追加します。たとえば、非表示のメールボックスまたは配布グループを管理する**msExchHideFromAddressLists**属性が追加されます。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p110">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL. In third-party messaging migration scenarios, this would require the Office 365 schema extension for the on-premises directory. The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from on-premises directory. For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="cc3a6-187">最大文字数: 256</span><span class="sxs-lookup"><span data-stu-id="cc3a6-187">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="cc3a6-188">属性の値にスペースを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-188">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="cc3a6-189">この属性値は、ディレクトリ内で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-189">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="cc3a6-190">無効な文字: \< \> \ ();, [ ] "</span><span class="sxs-lookup"><span data-stu-id="cc3a6-190">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="cc3a6-191">すべての SMTP (Simple Mail Transport Protocol) アドレスは、電子メール メッセージング標準に準拠する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="cc3a6-192">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="cc3a6-192">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="cc3a6-p111">**userPrincipalName**属性は、ユーザー名の後にアットマーク記号 (@) とドメイン名が続く、インターネットスタイルのサインイン形式にする必要があります。たとえば、user@contoso.com のようにします。すべての簡易メール転送プロトコル (SMTP) アドレスは、電子メールメッセージング標準に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p111">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com. All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="cc3a6-p112">**userPrincipalName** 属性の最大文字数は 113 です。アットマーク (@) の前後の文字数の制限は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p112">The maximum number of characters for the **userPrincipalName** attribute is 113. A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="cc3a6-197">アットマーク記号 (@) の前に来るユーザー名の最大文字数: 6464</span><span class="sxs-lookup"><span data-stu-id="cc3a6-197">Maximum number of characters for the user name that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="cc3a6-198">アットマーク記号 (@) の後に続くドメイン名の最大文字数: 48</span><span class="sxs-lookup"><span data-stu-id="cc3a6-198">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="cc3a6-p113">無効な文字: \ &amp; \* % +/=?{ } |\< \> ( ) ;: , [ ] "</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p113">Invalid characters: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "</span></span>
  - <span data-ttu-id="cc3a6-201">ウムラウトは、無効な文字でもあります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-201">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="cc3a6-202">各**userPrincipalName**値には @ 文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-202">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="cc3a6-203">**userPrincipalName** 値の 1 文字目に @ 文字を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-203">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="cc3a6-204">ユーザー名の最後の文字には、ピリオド (.)、アンパサンド&amp;()、スペース、またはアットマーク (@) を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-204">The user name cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="cc3a6-205">ユーザー名にスペースを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-205">The user name cannot contain any spaces.</span></span>
  - <span data-ttu-id="cc3a6-206">ルーティング可能なドメインを使用する必要があります。たとえば、ローカルまたは内部のドメインを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-206">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="cc3a6-207">ユニコードはアンダースコア文字に変換されます。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-207">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="cc3a6-208">ディレクトリ内で **userPrincipalName** の値が重複しないようにします。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-208">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 
    
## <a name="prepare-the-userprincipalname-attribute"></a><span data-ttu-id="cc3a6-209">userPrincipalName 属性の準備</span><span class="sxs-lookup"><span data-stu-id="cc3a6-209">Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="cc3a6-p114">Active Directory は、組織内のエンドユーザーが**sAMAccountName**または**userPrincipalName**のいずれかを使用してディレクトリにサインインできるように設計されています。同様に、エンドユーザーは職場または学校アカウントのユーザープリンシパル名 (UPN) を使用して Office 365 にサインインできます。ディレクトリ同期では、オンプレミスディレクトリにある同じ UPN を使用して、Azure Active directory に新しいユーザーを作成しようとしています。UPN は、電子メールアドレスのように書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p114">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**. Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account. Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your on-premises directory. The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="cc3a6-p115">Office 365 では、UPN は電子メールアドレスの生成に使用される既定の属性です。**userPrincipalName** (オンプレミスと Azure Active Directory) は簡単に取得でき、 **proxyAddresses**のプライマリ電子メールアドレスは異なる値に設定されます。複数の値が設定されている場合、管理者とエンドユーザーに混乱が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p115">In Office 365, the UPN is the default attribute that's used to generate the email address. It's easy to get **userPrincipalName** (on-premises and in Azure Active Directory) and the primary email address in **proxyAddresses** set to different values. When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="cc3a6-p116">これらの属性を調整して混乱を軽減することをお勧めします。Active directory フェデレーションサービス (AD FS) 2.0 を使用したシングルサインオンの要件を満たすには、Azure active directory の upn とオンプレミスの active directory が一致し、有効なドメイン名前空間を使用していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p116">It's best to align these attributes to reduce confusion. To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your on-premises Active Directory match and are using a valid domain namespace.</span></span>
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="cc3a6-219">AD DS に代替 UPN サフィックスを追加する</span><span class="sxs-lookup"><span data-stu-id="cc3a6-219">Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="cc3a6-p117">ユーザーの会社の資格情報を Office 365 環境に関連付けるには、代替 UPN サフィックスを追加する必要がある場合があります。upn サフィックスは、@ 記号の右側にある upn の一部です。シングルサインオンに使用される upn には、文字、数字、ピリオド、ダッシュ、およびアンダースコアを含めることができますが、その他の種類の文字は使用できません。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p117">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment. A UPN suffix is the part of a UPN to the right of the @ character. UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="cc3a6-223">Active directory に代替 UPN サフィックスを追加する方法の詳細については、「[ディレクトリ同期の準備]( https://go.microsoft.com/fwlink/p/?LinkId=525430)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-223">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a><span data-ttu-id="cc3a6-224">オンプレミスの upn と Office 365 upn を照合する</span><span class="sxs-lookup"><span data-stu-id="cc3a6-224">Match the on-premises UPN with the Office 365 UPN</span></span>

<span data-ttu-id="cc3a6-p118">ディレクトリ同期が既にセットアップされている場合、ユーザーの UPN for Office 365 は、オンプレミスのディレクトリサービスに定義されているユーザーのオンプレミス upn と一致しない場合があります。これは、ドメインが確認される前にユーザーにライセンスが割り当てられた場合に発生する可能性があります。この問題を解決するには、PowerShell を使用して重複した[upn を修正](https://go.microsoft.com/fwlink/p/?LinkId=396730)し、Office 365 upn が企業ユーザー名とドメインと一致するようにします。オンプレミスのディレクトリサービスで UPN を更新していて、Azure Active directory id と同期する必要がある場合は、オンプレミスで変更を行う前に、Office 365 でユーザーのライセンスを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p118">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's on-premises UPN that's defined in your on-premises directory service. This can occur when a user was assigned a license before the domain was verified. To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain. If you are updating the UPN in the on-premises directory service and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes on-premises.</span></span> 
  
<span data-ttu-id="cc3a6-229">[ディレクトリ同期のためのルーティングできないドメイン (たとえば、ローカルドメイン) を準備する方法](prepare-a-non-routable-domain-for-directory-synchronization.md)も参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-229">See also [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="cc3a6-230">ディレクトリ統合ツール</span><span class="sxs-lookup"><span data-stu-id="cc3a6-230">Directory integration tools</span></span>

<span data-ttu-id="cc3a6-p119">ディレクトリ同期とは、オンプレミスの active directory 環境から Azure active directory へのディレクトリオブジェクト (ユーザー、グループ、および連絡先) の同期です。使用可能なツールとその機能の一覧については、「[ディレクトリ統合ツール](https://go.microsoft.com/fwlink/p/?LinkID=510956)」を参照してください。推奨されるツールは、 [Microsoft Azure Active Directory 接続](https://go.microsoft.com/fwlink/p/?LinkID=510956)です。azure active directory Connect の詳細については、「[オンプレミス id と azure active directory の統合](https://go.microsoft.com/fwlink/p/?LinkId=527969)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p119">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure, Azure Active Directory. See [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality. The recommended tool is [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). For more information about Azure Active Directory Connect, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span>
  
<span data-ttu-id="cc3a6-p120">ユーザーアカウントが初めて Office 365 ディレクトリと同期されると、それらはアクティブでないとマークされます。電子メールを送受信することはできません。サブスクリプションのライセンスは使用されません。office 365 サブスクリプションを特定のユーザーに割り当てる準備ができたら、 [office 365 for business のユーザーにライセンスを割り当てる](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)ことによって、それらを選択してアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p120">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as not activated. They cannot send or receive email, and they don't consume subscription licenses. When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
  
<span data-ttu-id="cc3a6-p121">[PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097)を使用してライセンスを割り当てることもできます。自動化されたソリューションの[Office 365 ユーザーにライセンスを自動的に割り当てる](https://go.microsoft.com/fwlink/p?LinkID=329805)には、「PowerShell を使用する方法」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc3a6-p121">You can also use [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) to assign licenses. See [How to Use PowerShell to Automatically Assign Licenses to Your Office 365 Users](https://go.microsoft.com/fwlink/p?LinkID=329805) for an automated solution.</span></span>