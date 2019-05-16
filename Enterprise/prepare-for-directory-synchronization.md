---
title: Office 365 へのディレクトリ同期を介したユーザーのプロビジョニングの準備をする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
ms.openlocfilehash: 0b2fe552911797337541bd25f0efcb81eab303bf
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071033"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a><span data-ttu-id="3c7f3-103">Office 365 へのディレクトリ同期を介したユーザーのプロビジョニングの準備をする</span><span class="sxs-lookup"><span data-stu-id="3c7f3-103">Prepare to provision users through directory synchronization to Office 365</span></span>

<span data-ttu-id="3c7f3-104">ディレクトリ同期を使用するユーザーのプロビジョニングには、Office 365 で職場または学校のアカウントを直接管理するよりも多くの計画と準備が必要です。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-104">Provisioning users with directory synchronization requires more planning and preparation than simply managing your work or school account directly in Office 365.</span></span> <span data-ttu-id="3c7f3-105">オンプレミスの Active Directory が Azure Active Directory に適切に同期されるようにするには、追加の計画と準備のタスクが必要です。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-105">The additional planning and preparation tasks are required to ensure that your on-premises Active Directory synchronizes properly to Azure Active Directory.</span></span> <span data-ttu-id="3c7f3-106">組織には、次のような利点が追加されています。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-106">The added benefits to your organization include:</span></span>
  
- <span data-ttu-id="3c7f3-107">組織内の管理プログラムを減らす</span><span class="sxs-lookup"><span data-stu-id="3c7f3-107">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="3c7f3-108">オプションでシングルサインオンのシナリオを有効にする</span><span class="sxs-lookup"><span data-stu-id="3c7f3-108">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="3c7f3-109">Office 365 でのアカウントの変更の自動化</span><span class="sxs-lookup"><span data-stu-id="3c7f3-109">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="3c7f3-110">ディレクトリ同期を使用する利点の詳細については、「[ディレクトリ同期のロードマップ]( https://go.microsoft.com/fwlink/p/?LinkId=525398)」および「 [Office 365 Id と Azure Active directory につい](about-office-365-identity.md)て」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-110">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
<span data-ttu-id="3c7f3-111">組織に最適なシナリオを特定するには、[ディレクトリ統合ツールの比較](https://go.microsoft.com/fwlink/p/?LinkId=525320)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-111">To determine which scenario is the best for your organization, review the [directory integration tools comparison](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span></span>
  
## <a name="directory-cleanup-tasks"></a><span data-ttu-id="3c7f3-112">ディレクトリのクリーンアップタスク</span><span class="sxs-lookup"><span data-stu-id="3c7f3-112">Directory cleanup tasks</span></span>

<span data-ttu-id="3c7f3-113">ディレクトリの同期を開始する前に、ディレクトリをクリーンアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-113">Before you begin synchronizing your directory, you need to clean up your directory.</span></span>
  
<span data-ttu-id="3c7f3-114">Azure [AD Connect によって Azure Active Directory に同期](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)された属性も確認します。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-114">Review also the [attributes synchronized to Azure Active Directory by Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="3c7f3-115">同期の前にディレクトリのクリーンアップを実行しないと、展開プロセスに重大な悪影響が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-115">If you don't perform directory cleanup before you synchronize, there can be a significant negative effect on the deployment process.</span></span> <span data-ttu-id="3c7f3-116">ディレクトリ同期のサイクルを経て、エラーを特定し、再同期を実行するまでに、数日または数週間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-116">It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="3c7f3-117">オンプレミスディレクトリで、次のクリーンアップタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-117">In your on-premises directory, complete the following clean-up tasks:</span></span>
  
1. <span data-ttu-id="3c7f3-118">Office 365 サービスオファーリングに割り当てられる各ユーザーに、 **proxyAddresses**属性に有効で一意の電子メールアドレスが設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-118">Ensure that each user who will be assigned Office 365 service offerings has a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="3c7f3-119">**ProxyAddresses**属性の重複する値を削除します。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-119">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="3c7f3-120">可能な場合は、Office 365 サービスオファーリングを割り当てる各ユーザーに、ユーザーの**ユーザー**オブジェクトの**userPrincipalName**属性に有効な一意の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-120">If possible, ensure that each user who will be assigned Office 365 service offerings has a valid and unique value for the **userPrincipalName** attribute in the user's **user** object.</span></span> <span data-ttu-id="3c7f3-121">最適な同期処理を行うには、オンプレミスの Active Directory UPN がクラウド UPN に一致していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-121">For best synchronization experience, ensure that the on-premises Active Directory UPN matches the cloud UPN.</span></span> <span data-ttu-id="3c7f3-122">ユーザーが**userPrincipalName**属性の値を持っていない場合は、**ユーザー**オブジェクトに**sAMAccountName**属性の有効な一意の値が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-122">If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute.</span></span> <span data-ttu-id="3c7f3-123">**UserPrincipalName**属性の重複する値を削除します。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-123">Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="3c7f3-124">グローバルアドレス一覧 (GAL) を最適に使用するには、次の属性の情報が正しいことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-124">For optimal use of the global address list (GAL), be sure the information in the following attributes is correct:</span></span>
    
  - <span data-ttu-id="3c7f3-125">givenName</span><span class="sxs-lookup"><span data-stu-id="3c7f3-125">givenName</span></span>
  - <span data-ttu-id="3c7f3-126">surname</span><span class="sxs-lookup"><span data-stu-id="3c7f3-126">surname</span></span>
  - <span data-ttu-id="3c7f3-127">displayName</span><span class="sxs-lookup"><span data-stu-id="3c7f3-127">displayName</span></span>
  - <span data-ttu-id="3c7f3-128">役職</span><span class="sxs-lookup"><span data-stu-id="3c7f3-128">Job Title</span></span>
  - <span data-ttu-id="3c7f3-129">部署</span><span class="sxs-lookup"><span data-stu-id="3c7f3-129">Department</span></span>
  - <span data-ttu-id="3c7f3-130">事業所</span><span class="sxs-lookup"><span data-stu-id="3c7f3-130">Office</span></span>
  - <span data-ttu-id="3c7f3-131">事業所電話番号</span><span class="sxs-lookup"><span data-stu-id="3c7f3-131">Office Phone</span></span>
  - <span data-ttu-id="3c7f3-132">携帯電話番号</span><span class="sxs-lookup"><span data-stu-id="3c7f3-132">Mobile Phone</span></span>
  - <span data-ttu-id="3c7f3-133">FAX 番号</span><span class="sxs-lookup"><span data-stu-id="3c7f3-133">Fax Number</span></span>
  - <span data-ttu-id="3c7f3-134">番地</span><span class="sxs-lookup"><span data-stu-id="3c7f3-134">Street Address</span></span>
  - <span data-ttu-id="3c7f3-135">市区町村</span><span class="sxs-lookup"><span data-stu-id="3c7f3-135">City</span></span>
  - <span data-ttu-id="3c7f3-136">都道府県</span><span class="sxs-lookup"><span data-stu-id="3c7f3-136">State or Province</span></span>
  - <span data-ttu-id="3c7f3-137">郵便番号</span><span class="sxs-lookup"><span data-stu-id="3c7f3-137">Zip or Postal Code</span></span>
  - <span data-ttu-id="3c7f3-138">国または地域</span><span class="sxs-lookup"><span data-stu-id="3c7f3-138">Country or Region</span></span>
    
## <a name="directory-object-and-attribute-preparation"></a><span data-ttu-id="3c7f3-139">ディレクトリオブジェクトと属性の準備</span><span class="sxs-lookup"><span data-stu-id="3c7f3-139">Directory object and attribute preparation</span></span>

<span data-ttu-id="3c7f3-140">オンプレミスディレクトリと Office 365 との間のディレクトリ同期を正常に行うには、オンプレミスのディレクトリ属性が適切に準備されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-140">Successful directory synchronization between your on-premises directory and Office 365 requires that your on-premises directory attributes are properly prepared.</span></span> <span data-ttu-id="3c7f3-141">たとえば、Office 365 環境と同期されている特定の属性に特定の文字が使用されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-141">For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment.</span></span> <span data-ttu-id="3c7f3-142">予期しない文字によってディレクトリ同期が失敗することはありませんが、警告が返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-142">Unexpected characters do not cause directory synchronization to fail but might return a warning.</span></span> <span data-ttu-id="3c7f3-143">無効な文字は、ディレクトリ同期が失敗する原因となります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-143">Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="3c7f3-144">Active Directory ユーザーの一部に1つ以上の重複した属性がある場合も、ディレクトリ同期は失敗します。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-144">Directory synchronization will also fail if some of your Active Directory users have one or more duplicate attributes.</span></span> <span data-ttu-id="3c7f3-145">各ユーザーは固有の属性を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-145">Each user must have unique attributes.</span></span>
  
<span data-ttu-id="3c7f3-146">準備する必要がある属性を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-146">The attributes that you need to prepare are listed here:</span></span>
  
 <span data-ttu-id="3c7f3-147">**注:**[Idfix ツール](install-and-run-idfix.md)を使用して、このプロセスを非常に簡単にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-147">**NOTE:** You can also use the [IdFix tool](install-and-run-idfix.md) to make this process a lot easier.</span></span> 
  
- <span data-ttu-id="3c7f3-148">**displayName**</span><span class="sxs-lookup"><span data-stu-id="3c7f3-148">**displayName**</span></span>
    
  - <span data-ttu-id="3c7f3-149">属性が user オブジェクトに存在する場合は、Office 365 と同期されます。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-149">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="3c7f3-150">この属性が user オブジェクトに存在する場合は、その値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-150">If this attribute exists in the user object, there must be a value for it.</span></span> <span data-ttu-id="3c7f3-151">つまり、属性を空白にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-151">That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="3c7f3-152">最大文字数: 256</span><span class="sxs-lookup"><span data-stu-id="3c7f3-152">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="3c7f3-153">**名**</span><span class="sxs-lookup"><span data-stu-id="3c7f3-153">**givenName**</span></span>
    
  - <span data-ttu-id="3c7f3-154">属性が user オブジェクトに存在する場合は、Office 365 と同期されますが、Office 365 では必要ないか使用されません。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-154">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="3c7f3-155">最大文字数:64</span><span class="sxs-lookup"><span data-stu-id="3c7f3-155">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="3c7f3-156">**mail**</span><span class="sxs-lookup"><span data-stu-id="3c7f3-156">**mail**</span></span>
    
  - <span data-ttu-id="3c7f3-157">この属性の値は、ディレクトリ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-157">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="3c7f3-158">重複する値がある場合、値を持つ最初のユーザーが同期されます。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-158">If there are duplicate values, the first user with the value is synchronized.</span></span> <span data-ttu-id="3c7f3-159">以降のユーザーは、Office 365 に表示されません。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-159">Subsequent users will not appear in Office 365.</span></span> <span data-ttu-id="3c7f3-160">両方のユーザーが Office 365 に表示されるようにするには、Office 365 の値を変更するか、オンプレミスのディレクトリの両方の値を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-160">You must modify either the value in Office 365, or modify both of the values in the on-premises directory in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="3c7f3-161">**mailNickname**(Exchange エイリアス)</span><span class="sxs-lookup"><span data-stu-id="3c7f3-161">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="3c7f3-162">属性値はピリオド (.) で始めることはできません。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-162">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="3c7f3-163">この属性の値は、ディレクトリ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-163">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="3c7f3-164">**proxyAddresses**</span><span class="sxs-lookup"><span data-stu-id="3c7f3-164">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="3c7f3-165">複数値の属性</span><span class="sxs-lookup"><span data-stu-id="3c7f3-165">Multiple-value attribute</span></span>
  - <span data-ttu-id="3c7f3-166">値あたりの最大文字数: 256</span><span class="sxs-lookup"><span data-stu-id="3c7f3-166">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="3c7f3-167">属性の値にスペースを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-167">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="3c7f3-168">この属性の値は、ディレクトリ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-168">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="3c7f3-169">無効な文字\< \> : ();, [ ] "</span><span class="sxs-lookup"><span data-stu-id="3c7f3-169">Invalid characters: \< \> ( ) ; , [ ] "</span></span>
    
    <span data-ttu-id="3c7f3-170">無効な文字は、SMTP:User@contso.com が許可されていても、SMTP:user:M@contoso.com は許可されていませんが、型区切り記号の後の文字と ":" に適用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-170">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="3c7f3-171">すべての簡易メール転送プロトコル (SMTP) アドレスは、電子メールメッセージング標準に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-171">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span> <span data-ttu-id="3c7f3-172">重複しているまたは不要なアドレスが存在する場合は、ヘルプトピックの「 [Exchange での重複および不要なプロキシアドレスの削除](https://go.microsoft.com/fwlink/?LinkId=293860)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-172">If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="3c7f3-173">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="3c7f3-173">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="3c7f3-174">最大文字数:20</span><span class="sxs-lookup"><span data-stu-id="3c7f3-174">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="3c7f3-175">この属性の値は、ディレクトリ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-175">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="3c7f3-176">無効な文字: [\ "|,/ \< \> : + =;?</span><span class="sxs-lookup"><span data-stu-id="3c7f3-176">Invalid characters: [ \ " | , / : \< \> + = ; ?</span></span> <span data-ttu-id="3c7f3-177">\* ]</span><span class="sxs-lookup"><span data-stu-id="3c7f3-177"></span></span>
  - <span data-ttu-id="3c7f3-178">ユーザーの**sAMAccountName**属性が無効で、 **userPrincipalName**属性が有効な場合、Office 365 でユーザーアカウントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-178">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="3c7f3-179">**SAMAccountName**と**userPrincipalName**の両方が無効な場合は、オンプレミスの Active Directory **userprincipalname**属性を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-179">If both **sAMAccountName** and **userPrincipalName** are invalid, the on-premises Active Directory **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="3c7f3-180">**sn**姓</span><span class="sxs-lookup"><span data-stu-id="3c7f3-180">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="3c7f3-181">属性が user オブジェクトに存在する場合は、Office 365 と同期されますが、Office 365 では必要ないか使用されません。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-181">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="3c7f3-182">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="3c7f3-182">**targetAddress**</span></span>
    
    <span data-ttu-id="3c7f3-183">ユーザーに対して設定されている**targetAddress**属性 (たとえば、SMTP:tom@contoso.com) を OFFICE 365 GAL に表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-183">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL.</span></span> <span data-ttu-id="3c7f3-184">サードパーティ製のメッセージング移行シナリオでは、オンプレミスのディレクトリに Office 365 スキーマ拡張が必要になります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-184">In third-party messaging migration scenarios, this would require the Office 365 schema extension for the on-premises directory.</span></span> <span data-ttu-id="3c7f3-185">Office 365 スキーマ拡張機能は、オンプレミスディレクトリからのディレクトリ同期ツールを使用して設定された Office 365 オブジェクトを管理するための便利な属性も追加します。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-185">The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from on-premises directory.</span></span> <span data-ttu-id="3c7f3-186">たとえば、非表示のメールボックスまたは配布グループを管理する**msExchHideFromAddressLists**属性が追加されます。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-186">For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="3c7f3-187">最大文字数: 256</span><span class="sxs-lookup"><span data-stu-id="3c7f3-187">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="3c7f3-188">属性の値にスペースを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-188">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="3c7f3-189">この属性の値は、ディレクトリ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-189">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="3c7f3-190">無効な文字: \< \> \ ();, [ ] "</span><span class="sxs-lookup"><span data-stu-id="3c7f3-190">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="3c7f3-191">すべての簡易メール転送プロトコル (SMTP) アドレスは、電子メールメッセージング標準に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="3c7f3-192">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="3c7f3-192">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="3c7f3-193">**UserPrincipalName**属性は、ユーザー名の後にアットマーク記号 (@) とドメイン名が続く、インターネットスタイルのサインイン形式にする必要があります。たとえば、user@contoso.com のようにします。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-193">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com.</span></span> <span data-ttu-id="3c7f3-194">すべての簡易メール転送プロトコル (SMTP) アドレスは、電子メールメッセージング標準に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-194">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="3c7f3-195">**UserPrincipalName**属性の最大文字数は113です。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-195">The maximum number of characters for the **userPrincipalName** attribute is 113.</span></span> <span data-ttu-id="3c7f3-196">アットマーク (@) の前後には、次のように特定の文字数が許可されます。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-196">A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="3c7f3-197">アットマーク記号 (@) の前に表示されるユーザー名の最大文字数:64</span><span class="sxs-lookup"><span data-stu-id="3c7f3-197">Maximum number of characters for the user name that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="3c7f3-198">アットマーク記号 (@) の後に続くドメイン名の最大文字数:48</span><span class="sxs-lookup"><span data-stu-id="3c7f3-198">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="3c7f3-199">無効な文字: \ &amp; \* % +/=?</span><span class="sxs-lookup"><span data-stu-id="3c7f3-199">Invalid characters: \ % &amp; \* + / = ?</span></span> <span data-ttu-id="3c7f3-200">{ } | \< \> ( ) ; : , [ ] "</span><span class="sxs-lookup"><span data-stu-id="3c7f3-200"></span></span>
  - <span data-ttu-id="3c7f3-201">ウムラウトは、無効な文字でもあります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-201">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="3c7f3-202">各**userPrincipalName**値には @ 文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-202">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="3c7f3-203">各**userPrincipalName**値の先頭文字に @ 文字を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-203">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="3c7f3-204">ユーザー名の最後の文字には、ピリオド (.)、アンパサンド&amp;()、スペース、またはアットマーク (@) を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-204">The user name cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="3c7f3-205">ユーザー名にスペースを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-205">The user name cannot contain any spaces.</span></span>
  - <span data-ttu-id="3c7f3-206">ルーティング可能なドメインを使用する必要があります。たとえば、ローカルまたは内部のドメインを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-206">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="3c7f3-207">Unicode は、アンダースコア文字に変換されます。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-207">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="3c7f3-208">**userPrincipalName**には、ディレクトリ内に重複する値を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-208">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 
    
## <a name="prepare-the-userprincipalname-attribute"></a><span data-ttu-id="3c7f3-209">UserPrincipalName 属性を準備する</span><span class="sxs-lookup"><span data-stu-id="3c7f3-209">Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="3c7f3-210">Active Directory は、組織内のエンドユーザーが**sAMAccountName**または**userPrincipalName**のいずれかを使用してディレクトリにサインインできるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-210">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**.</span></span> <span data-ttu-id="3c7f3-211">同様に、エンドユーザーは職場または学校アカウントのユーザープリンシパル名 (UPN) を使用して Office 365 にサインインできます。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-211">Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account.</span></span> <span data-ttu-id="3c7f3-212">ディレクトリ同期では、オンプレミスディレクトリにある同じ UPN を使用して、Azure Active Directory に新しいユーザーを作成しようとしています。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-212">Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your on-premises directory.</span></span> <span data-ttu-id="3c7f3-213">UPN は、電子メールアドレスのように書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-213">The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="3c7f3-214">Office 365 では、UPN は電子メールアドレスの生成に使用される既定の属性です。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-214">In Office 365, the UPN is the default attribute that's used to generate the email address.</span></span> <span data-ttu-id="3c7f3-215">**UserPrincipalName** (オンプレミスと Azure Active Directory) は簡単に取得でき、 **proxyAddresses**のプライマリ電子メールアドレスは異なる値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-215">It's easy to get **userPrincipalName** (on-premises and in Azure Active Directory) and the primary email address in **proxyAddresses** set to different values.</span></span> <span data-ttu-id="3c7f3-216">複数の値が設定されている場合、管理者とエンドユーザーに混乱が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-216">When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="3c7f3-217">これらの属性を調整して混乱を軽減することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-217">It's best to align these attributes to reduce confusion.</span></span> <span data-ttu-id="3c7f3-218">Active Directory フェデレーションサービス (AD FS) 2.0 を使用したシングルサインオンの要件を満たすには、Azure Active Directory の Upn とオンプレミスの Active Directory が一致し、有効なドメイン名前空間を使用していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-218">To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your on-premises Active Directory match and are using a valid domain namespace.</span></span>
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="3c7f3-219">AD DS に代替 UPN サフィックスを追加する</span><span class="sxs-lookup"><span data-stu-id="3c7f3-219">Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="3c7f3-220">ユーザーの会社の資格情報を Office 365 環境に関連付けるには、代替 UPN サフィックスを追加する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-220">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment.</span></span> <span data-ttu-id="3c7f3-221">UPN サフィックスは、@ 文字の右側の UPN の一部です。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-221">A UPN suffix is the part of a UPN to the right of the @ character.</span></span> <span data-ttu-id="3c7f3-222">シングル サインオンに使用する UPN には文字、数字、ピリオド、ダッシュ、アンダースコアを含めることができますが、その他の種類の文字を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-222">UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="3c7f3-223">Active Directory に代替 UPN サフィックスを追加する方法の詳細については、「[ディレクトリ同期の準備]( https://go.microsoft.com/fwlink/p/?LinkId=525430)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-223">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a><span data-ttu-id="3c7f3-224">オンプレミスの UPN と Office 365 UPN を照合する</span><span class="sxs-lookup"><span data-stu-id="3c7f3-224">Match the on-premises UPN with the Office 365 UPN</span></span>

<span data-ttu-id="3c7f3-225">ディレクトリ同期が既にセットアップされている場合、ユーザーの UPN for Office 365 は、オンプレミスのディレクトリサービスに定義されているユーザーのオンプレミス UPN と一致しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-225">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's on-premises UPN that's defined in your on-premises directory service.</span></span> <span data-ttu-id="3c7f3-226">ドメインが確認される前にユーザーにライセンスを割り当てた場合、この状況が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-226">This can occur when a user was assigned a license before the domain was verified.</span></span> <span data-ttu-id="3c7f3-227">この問題を解決するには、PowerShell を使用して重複した[upn を修正](https://go.microsoft.com/fwlink/p/?LinkId=396730)し、OFFICE 365 upn が企業ユーザー名とドメインと一致するようにします。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-227">To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain.</span></span> <span data-ttu-id="3c7f3-228">オンプレミスのディレクトリサービスで UPN を更新していて、Azure Active Directory id と同期する必要がある場合は、オンプレミスで変更を行う前に、Office 365 でユーザーのライセンスを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-228">If you are updating the UPN in the on-premises directory service and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes on-premises.</span></span> 
  
<span data-ttu-id="3c7f3-229">[ディレクトリ同期のためのルーティングできないドメイン (たとえば、ローカルドメイン) を準備する方法](prepare-a-non-routable-domain-for-directory-synchronization.md)も参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-229">See also [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="3c7f3-230">ディレクトリ統合ツール</span><span class="sxs-lookup"><span data-stu-id="3c7f3-230">Directory integration tools</span></span>

<span data-ttu-id="3c7f3-231">ディレクトリ同期とは、オンプレミスの active directory 環境から Azure active directory 365 へのディレクトリオブジェクト (ユーザー、グループ、および連絡先) の同期です。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-231">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure, Azure Active Directory.</span></span> <span data-ttu-id="3c7f3-232">使用可能なツールとその機能の一覧については、「[ディレクトリ統合ツール](https://go.microsoft.com/fwlink/p/?LinkID=510956)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-232">See [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality.</span></span> <span data-ttu-id="3c7f3-233">推奨されるツールは、 [Microsoft Azure Active Directory 接続](https://go.microsoft.com/fwlink/p/?LinkID=510956)です。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-233">The recommended tool is [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956).</span></span> <span data-ttu-id="3c7f3-234">Azure Active Directory Connect の詳細については、「[オンプレミス id と Azure Active directory の統合](https://go.microsoft.com/fwlink/p/?LinkId=527969)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-234">For more information about Azure Active Directory Connect, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span>
  
<span data-ttu-id="3c7f3-235">ユーザーアカウントが初めて Office 365 ディレクトリと同期されると、それらはアクティブでないとマークされます。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-235">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as not activated.</span></span> <span data-ttu-id="3c7f3-236">電子メールを送受信することはできません。サブスクリプションのライセンスは使用されません。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-236">They cannot send or receive email, and they don't consume subscription licenses.</span></span> <span data-ttu-id="3c7f3-237">Office 365 サブスクリプションを特定のユーザーに割り当てる準備ができたら、 [office 365 for business のユーザーにライセンスを割り当てる](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)ことによって、それらを選択してアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-237">When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
  
<span data-ttu-id="3c7f3-238">[PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097)を使用してライセンスを割り当てることもできます。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-238">You can also use [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) to assign licenses.</span></span> <span data-ttu-id="3c7f3-239">自動化されたソリューションの[Office 365 ユーザーにライセンスを自動的に割り当てる](https://go.microsoft.com/fwlink/p?LinkID=329805)には、「PowerShell を使用する方法」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c7f3-239">See [How to Use PowerShell to Automatically Assign Licenses to Your Office 365 Users](https://go.microsoft.com/fwlink/p?LinkID=329805) for an automated solution.</span></span>