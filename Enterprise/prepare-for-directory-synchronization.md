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
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: ディレクトリ同期し、このメソッドを使用する場合の長期的な利点を使用して、Office 365 にユーザーをプロビジョニングできるようにする方法について説明します。
ms.openlocfilehash: 78636fd3ec7aaaac8fa06ba8a0f2c37d76d1b045
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541778"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a><span data-ttu-id="71896-103">Office 365 へのディレクトリ同期を通してユーザーをプロビジョニングするための準備</span><span class="sxs-lookup"><span data-stu-id="71896-103">Prepare to provision users through directory synchronization to Office 365</span></span>

<span data-ttu-id="71896-p101">ディレクトリ同期によってユーザーをプロビジョニングするには、詳細の計画と準備をするだけで Office 365 に直接、職場、学校のアカウントを管理するよりもする必要があります。追加の計画と準備タスクは、Azure Active Directory に、オンプレミスの Active Directory が正しく同期することを確認する必要があります。組織に追加の利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="71896-p101">Provisioning users with directory synchronization requires more planning and preparation than simply managing your work or school account directly in Office 365. The additional planning and preparation tasks are required to ensure that your on-premises Active Directory synchronizes properly to Azure Active Directory. The added benefits to your organization include:</span></span>
  
- <span data-ttu-id="71896-107">組織の管理プログラムの削減</span><span class="sxs-lookup"><span data-stu-id="71896-107">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="71896-108">必要に応じてシングル サインオンのシナリオを有効にします。</span><span class="sxs-lookup"><span data-stu-id="71896-108">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="71896-109">Office 365 でのアカウントの変更の自動化</span><span class="sxs-lookup"><span data-stu-id="71896-109">Automating account changes in Office 365</span></span>
    
<span data-ttu-id="71896-110">ディレクトリ同期を使用する利点の詳細については、[ディレクトリ同期のロードマップ]( https://go.microsoft.com/fwlink/p/?LinkId=525398)」および「 [Office 365 Id を理解すると Azure Active Directory](about-office-365-identity.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71896-110">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
<span data-ttu-id="71896-111">シナリオではを組織にとって最適なを確認するのには、[ディレクトリの統合ツールの比較](https://go.microsoft.com/fwlink/p/?LinkId=525320)を確認します。</span><span class="sxs-lookup"><span data-stu-id="71896-111">To determine which scenario is the best for your organization, review the [directory integration tools comparison](https://go.microsoft.com/fwlink/p/?LinkId=525320).</span></span>
  
## <a name="directory-cleanup-tasks"></a><span data-ttu-id="71896-112">ディレクトリのクリーンアップ タスク</span><span class="sxs-lookup"><span data-stu-id="71896-112">Directory cleanup tasks</span></span>

<span data-ttu-id="71896-113">ディレクトリの同期を開始する前に、ディレクトリをクリーンアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="71896-113">Before you begin synchronizing your directory, you need to clean up your directory.</span></span>
  
<span data-ttu-id="71896-114">[Azure AD 接続で、Azure Active directory 属性を同期](https://go.microsoft.com/fwlink/p/?LinkId=746480)するも参照してください。</span><span class="sxs-lookup"><span data-stu-id="71896-114">Review also the [attributes synchronized to Azure Active Directory by Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=746480).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="71896-p102">同期する前に、ディレクトリのクリーンアップを実行しない、する場合があります、展開プロセスに重大な悪影響を及ぼす。日かかる、エラー、および再同期を識別する、ディレクトリ同期のサイクルを通過して、数週間にわたって、可能性があります。</span><span class="sxs-lookup"><span data-stu-id="71896-p102">If you don't perform directory cleanup before you synchronize, there can be a significant negative effect on the deployment process. It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="71896-117">設置ディレクトリには、次のクリーンアップ タスクを完了します。</span><span class="sxs-lookup"><span data-stu-id="71896-117">In your on-premises directory, complete the following clean-up tasks:</span></span>
  
1. <span data-ttu-id="71896-118">Office 365 サービスが割り当てられる各ユーザーについて、**proxyAddresses** 属性のメール アドレスが有効かつ一意であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="71896-118">Ensure that each user who will be assigned Office 365 service offerings has a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
    
2. <span data-ttu-id="71896-119">**proxyAddresses** 属性に重複する値が存在する場合は削除します。</span><span class="sxs-lookup"><span data-stu-id="71896-119">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="71896-p103">可能であれば、Office 365 サービスに割り当てられる各ユーザーがあるユーザーの**ユーザー**オブジェクトの**userPrincipalName**属性に対して有効で、一意の値を確認します。快適に同期、オンプレミスの Active ディレクトリ UPN がクラウドの UPN と一致していることを確認します。**UserPrincipalName**属性の値がなくても場合、**ユーザー**オブジェクトは**sAMAccountName**属性に対して有効で、一意の値を含める必要があります。**UserPrincipalName**属性内の重複する値を削除します。</span><span class="sxs-lookup"><span data-stu-id="71896-p103">If possible, ensure that each user who will be assigned Office 365 service offerings has a valid and unique value for the **userPrincipalName** attribute in the user's **user** object. For best synchronization experience, ensure that the on-premises Active Directory UPN matches the cloud UPN. If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute. Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="71896-124">グローバル アドレス一覧 (GAL) を最適に利用できるように、以下の属性の情報が正しいことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="71896-124">For optimal use of the global address list (GAL), be sure the information in the following attributes is correct:</span></span>
    
  - <span data-ttu-id="71896-125">givenName </span><span class="sxs-lookup"><span data-stu-id="71896-125">givenName</span></span>
  - <span data-ttu-id="71896-126">姓</span><span class="sxs-lookup"><span data-stu-id="71896-126">surname</span></span>
  - <span data-ttu-id="71896-127">表示名</span><span class="sxs-lookup"><span data-stu-id="71896-127">displayName</span></span>
  - <span data-ttu-id="71896-128">役職</span><span class="sxs-lookup"><span data-stu-id="71896-128">Job Title</span></span>
  - <span data-ttu-id="71896-129">部署</span><span class="sxs-lookup"><span data-stu-id="71896-129">Department</span></span>
  - <span data-ttu-id="71896-130">事業所</span><span class="sxs-lookup"><span data-stu-id="71896-130">Office</span></span>
  - <span data-ttu-id="71896-131">事業所電話番号</span><span class="sxs-lookup"><span data-stu-id="71896-131">Office Phone</span></span>
  - <span data-ttu-id="71896-132">携帯電話</span><span class="sxs-lookup"><span data-stu-id="71896-132">Mobile Phone</span></span>
  - <span data-ttu-id="71896-133">FAX 番号</span><span class="sxs-lookup"><span data-stu-id="71896-133">Fax Number</span></span>
  - <span data-ttu-id="71896-134">番地</span><span class="sxs-lookup"><span data-stu-id="71896-134">Street Address</span></span>
  - <span data-ttu-id="71896-135">市区町村</span><span class="sxs-lookup"><span data-stu-id="71896-135">City</span></span>
  - <span data-ttu-id="71896-136">都道府県</span><span class="sxs-lookup"><span data-stu-id="71896-136">State or Province</span></span>
  - <span data-ttu-id="71896-137">郵便番号</span><span class="sxs-lookup"><span data-stu-id="71896-137">Zip or Postal Code</span></span>
  - <span data-ttu-id="71896-138">国または地域</span><span class="sxs-lookup"><span data-stu-id="71896-138">Country or Region</span></span>
    
## <a name="directory-object-and-attribute-preparation"></a><span data-ttu-id="71896-139">ディレクトリ オブジェクトおよび属性の準備</span><span class="sxs-lookup"><span data-stu-id="71896-139">Directory object and attribute preparation</span></span>

<span data-ttu-id="71896-p104">設置ディレクトリと Office 365 のディレクトリ同期では、オンプレミスのディレクトリの属性が適切に準備されている必要があります。たとえば、特定の文字が Office 365 環境と同期している特定の属性で使用されていないことを確認する必要があります。予期しない文字は、ディレクトリ同期が失敗するが発生しないが、警告メッセージを返すことがあります。無効な文字には、ディレクトリ同期が失敗するが発生します。</span><span class="sxs-lookup"><span data-stu-id="71896-p104">Successful directory synchronization between your on-premises directory and Office 365 requires that your on-premises directory attributes are properly prepared. For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Office 365 environment. Unexpected characters do not cause directory synchronization to fail but might return a warning. Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="71896-p105">ディレクトリ同期は、1 つまたは複数の重複する属性がある、Active Directory のユーザーの場合も失敗します。各ユーザー固有の属性が必要です。</span><span class="sxs-lookup"><span data-stu-id="71896-p105">Directory synchronization will also fail if some of your Active Directory users have one or more duplicate attributes. Each user must have unique attributes.</span></span>
  
<span data-ttu-id="71896-146">準備する必要がある属性は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="71896-146">The attributes that you need to prepare are listed here:</span></span>
  
 <span data-ttu-id="71896-147">**注:** 非常に簡単にするのには[IdFix ツール](install-and-run-idfix.md)を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="71896-147">**NOTE:** You can also use the [IdFix tool](install-and-run-idfix.md) to make this process a lot easier.</span></span> 
  
- <span data-ttu-id="71896-148">**表示名**</span><span class="sxs-lookup"><span data-stu-id="71896-148">**displayName**</span></span>
    
  - <span data-ttu-id="71896-149">この属性がユーザー オブジェクトに存在する場合は、Office 365 と同期されます。</span><span class="sxs-lookup"><span data-stu-id="71896-149">If the attribute exists in the user object, it will be synchronized with Office 365.</span></span>
  - <span data-ttu-id="71896-p106">この属性がユーザー オブジェクトに存在する場合、値を割り当てる必要があります。この属性を空白にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="71896-p106">If this attribute exists in the user object, there must be a value for it. That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="71896-152">最大文字数: 256</span><span class="sxs-lookup"><span data-stu-id="71896-152">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="71896-153">**givenName **</span><span class="sxs-lookup"><span data-stu-id="71896-153">**givenName**</span></span>
    
  - <span data-ttu-id="71896-154">ユーザー オブジェクトに存在する場合、この属性は Office 365 と同期されますが、Office 365 ではこの属性を必要とせず、使用されません。</span><span class="sxs-lookup"><span data-stu-id="71896-154">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
  - <span data-ttu-id="71896-155">最大文字数: 64</span><span class="sxs-lookup"><span data-stu-id="71896-155">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="71896-156">**mail**</span><span class="sxs-lookup"><span data-stu-id="71896-156">**mail**</span></span>
    
  - <span data-ttu-id="71896-157">この属性値は、ディレクトリ内で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="71896-157">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="71896-p107">重複する値がある場合は、値を持つ最初のユーザーが同期されます。Office 365 では、後続のユーザーは表示されません。、Office 365 で、いずれかの値を変更または、両方のユーザーを Office 365 に表示するために、オンプレミス ディレクトリ内の値の両方を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71896-p107">If there are duplicate values, the first user with the value is synchronized. Subsequent users will not appear in Office 365. You must modify either the value in Office 365, or modify both of the values in the on-premises directory in order for both users to appear in Office 365.</span></span> 
  
- <span data-ttu-id="71896-161">**mailNickname** (Exchange エイリアス)</span><span class="sxs-lookup"><span data-stu-id="71896-161">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="71896-162">属性の値は、ピリオド (.) で始めることはできません。</span><span class="sxs-lookup"><span data-stu-id="71896-162">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="71896-163">この属性値は、ディレクトリ内で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="71896-163">The attribute value must be unique within the directory.</span></span>
    
- <span data-ttu-id="71896-164">**proxyAddresses **</span><span class="sxs-lookup"><span data-stu-id="71896-164">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="71896-165">複数値属性</span><span class="sxs-lookup"><span data-stu-id="71896-165">Multiple-value attribute</span></span>
  - <span data-ttu-id="71896-166">1 つの値に使用できる最大文字数:256</span><span class="sxs-lookup"><span data-stu-id="71896-166">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="71896-167">属性の値は、スペースを含めないでください。</span><span class="sxs-lookup"><span data-stu-id="71896-167">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="71896-168">この属性値は、ディレクトリ内で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="71896-168">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="71896-169">無効な文字: \< \> ();, [ ] "</span><span class="sxs-lookup"><span data-stu-id="71896-169">Invalid characters: \< \> ( ) ; , [ ] "</span></span>
    
    <span data-ttu-id="71896-170">型の区切り記号に続く文字列に無効な文字を適用することに注意してくださいと":"SMTP:User@contso.com も可能ですが、SMTP:user:M@contoso.com ではありませんように、します。</span><span class="sxs-lookup"><span data-stu-id="71896-170">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="71896-p108">すべての簡易メール転送プロトコル (SMTP) アドレスは、標準のメッセージを電子メールで従う必要があります。重複や不要なアドレスが存在する場合は、 [Exchange では重複や不要なプロキシを削除する](https://go.microsoft.com/fwlink/?LinkId=293860)ヘルプ トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="71896-p108">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards. If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="71896-173">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="71896-173">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="71896-174">最大文字数: 20</span><span class="sxs-lookup"><span data-stu-id="71896-174">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="71896-175">この属性値は、ディレクトリ内で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="71896-175">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="71896-p109">無効な文字: [\] |、/: \< \> + =;?\* ]</span><span class="sxs-lookup"><span data-stu-id="71896-p109">Invalid characters: [ \ " | , / : \< \> + = ; ? \* ]</span></span>
  - <span data-ttu-id="71896-178">ユーザーの **sAMAccountName** 属性が無効で、**userPrincipalName** 属性が有効な場合、ユーザー アカウントは Office 365 に作成されます。</span><span class="sxs-lookup"><span data-stu-id="71896-178">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Office 365.</span></span> 
  - <span data-ttu-id="71896-179">**SAMAccountName**と**userPrincipalName**の両方が無効な場合、オンプレミスの Active Directory の**userPrincipalName**属性を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71896-179">If both **sAMAccountName** and **userPrincipalName** are invalid, the on-premises Active Directory **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="71896-180">**sn** (姓)</span><span class="sxs-lookup"><span data-stu-id="71896-180">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="71896-181">ユーザー オブジェクトに存在する場合、この属性は Office 365 と同期されますが、Office 365 ではこの属性を必要とせず、使用されません。</span><span class="sxs-lookup"><span data-stu-id="71896-181">If the attribute exists in the user object, it will be synchronized with Office 365, but Office 365 does not require or use it.</span></span>
    
- <span data-ttu-id="71896-182">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="71896-182">**targetAddress**</span></span>
    
    <span data-ttu-id="71896-p110">必要と Office 365 のグローバル アドレス一覧にユーザーの設定は、 **targetAddress**属性 (たとえば、SMTP:tom@contoso.com) があります。サード ・ パーティ製メッセージングの移行シナリオでは、この必要がある Office 365 のスキーマ拡張設置ディレクトリにあります。設置ディレクトリからディレクトリ同期ツールを使用して指定されている Office 365 のオブジェクトを管理するために役立つその他の属性、Office 365 のスキーマ拡張機能も追加します。たとえば、非表示のメールボックスまたは配布グループを管理するために**msExchHideFromAddressLists**属性が追加されます。</span><span class="sxs-lookup"><span data-stu-id="71896-p110">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Office 365 GAL. In third-party messaging migration scenarios, this would require the Office 365 schema extension for the on-premises directory. The Office 365 schema extension would also add other useful attributes to manage Office 365 objects that are populated by using a directory synchronization tool from on-premises directory. For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="71896-187">最大文字数: 256</span><span class="sxs-lookup"><span data-stu-id="71896-187">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="71896-188">属性の値は、スペースを含めないでください。</span><span class="sxs-lookup"><span data-stu-id="71896-188">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="71896-189">この属性値は、ディレクトリ内で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="71896-189">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="71896-190">無効な文字: \ \< \> ();, [ ] "</span><span class="sxs-lookup"><span data-stu-id="71896-190">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="71896-191">すべての SMTP (Simple Mail Transport Protocol) アドレスは、電子メール メッセージング標準に準拠する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71896-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="71896-192">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="71896-192">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="71896-p111">**UserPrincipalName**属性は、インターネット スタイルのサインイン名の形式は、ユーザー名に続けてである必要があります、アット マーク (@) とドメイン名: user@contoso.com など。すべての簡易メール転送プロトコル (SMTP) アドレスは、標準のメッセージを電子メールで従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="71896-p111">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com. All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="71896-p112">**userPrincipalName** 属性の最大文字数は 113 です。アットマーク (@) の前後の文字数の制限は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="71896-p112">The maximum number of characters for the **userPrincipalName** attribute is 113. A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="71896-197">アットマーク記号 (@) の前に来るユーザー名の最大文字数: 6464</span><span class="sxs-lookup"><span data-stu-id="71896-197">Maximum number of characters for the user name that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="71896-198">アットマーク記号 (@) の後に続くドメイン名の最大文字数: 48</span><span class="sxs-lookup"><span data-stu-id="71896-198">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="71896-p113">無効な文字: \ % &amp; \* +/= でしょうか。{ } |\< \> ( ) ;: , [ ] "</span><span class="sxs-lookup"><span data-stu-id="71896-p113">Invalid characters: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "</span></span>
  - <span data-ttu-id="71896-201">ウムラウトが無効な文字もあります。</span><span class="sxs-lookup"><span data-stu-id="71896-201">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="71896-202">**UserPrincipalName**の各値に @ 文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="71896-202">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="71896-203">**userPrincipalName** 値の 1 文字目に @ 文字を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="71896-203">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="71896-204">ユーザー名は、ピリオド (.)、アンパサンドで終わることはできません (&amp;)、スペース、またはアットマーク (@)。</span><span class="sxs-lookup"><span data-stu-id="71896-204">The user name cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="71896-205">ユーザー名にスペースを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="71896-205">The user name cannot contain any spaces.</span></span>
  - <span data-ttu-id="71896-206">ルーティング可能なドメインを使用する必要があります。たとえば、ローカルまたは内部ドメインを使用できません。</span><span class="sxs-lookup"><span data-stu-id="71896-206">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="71896-207">ユニコードはアンダースコア文字に変換されます。</span><span class="sxs-lookup"><span data-stu-id="71896-207">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="71896-208">ディレクトリ内で **userPrincipalName** の値が重複しないようにします。</span><span class="sxs-lookup"><span data-stu-id="71896-208">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 
    
## <a name="prepare-the-userprincipalname-attribute"></a><span data-ttu-id="71896-209">userPrincipalName 属性の準備</span><span class="sxs-lookup"><span data-stu-id="71896-209">Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="71896-p114">**SAMAccountName**または**userPrincipalName**を使用して、ディレクトリにサインインするのには、組織内のエンド ・ ユーザーを許可するのには、active Directory は設計されています。同様に、エンド ・ ユーザーは、自分の仕事のユーザー プリンシパル名 (UPN) を使用して Office 365 にサインインやアカウントの学校です。ディレクトリ同期は、オンプレミス ディレクトリ内にある同一の UPN を使用して、Azure Active Directory で新しいユーザーを作成しようとします。UPN は、電子メール アドレスのように書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="71896-p114">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**. Similarly, end users can sign in to Office 365 by using the user principal name (UPN) of their work or school account. Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your on-premises directory. The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="71896-p115">Office 365 では、UPN は、電子メール アドレスを生成するために使用される既定の属性です。**UserPrincipalName**を取得するは簡単 (設置型と Azure Active Directory) と**proxyAddresses**が異なる値に設定でプライマリ電子メール アドレスです。異なる値に設定されている場合があります管理者とエンド ・ ユーザー用の混乱します。</span><span class="sxs-lookup"><span data-stu-id="71896-p115">In Office 365, the UPN is the default attribute that's used to generate the email address. It's easy to get **userPrincipalName** (on-premises and in Azure Active Directory) and the primary email address in **proxyAddresses** set to different values. When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="71896-p116">混乱を減らすためにこれらの属性を配置することをお勧めします。Active Directory フェデレーション サービス (AD FS) とシングル サインオンの要件を満たすために 2.0 では、Azure Active Directory と、オンプレミスの Active Directory で Upn を確認する必要がありますと一致し、有効なドメインの名前空間を使用しています。</span><span class="sxs-lookup"><span data-stu-id="71896-p116">It's best to align these attributes to reduce confusion. To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your on-premises Active Directory match and are using a valid domain namespace.</span></span>
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="71896-219">AD DS に代わりの UPN サフィックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="71896-219">Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="71896-p117">Office 365 環境で企業のユーザーの資格情報を関連付けるには、代わりの UPN サフィックスを追加する必要があります。ユーザー プリンシパル名サフィックス、UPN の右側の部分では、@ 文字。Upn は、シングル サインオンに使用するには、文字、番号、期間、ダッシュ、およびアンダー スコアがない他の種類の文字を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="71896-p117">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Office 365 environment. A UPN suffix is the part of a UPN to the right of the @ character. UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="71896-223">代わりの UPN サフィックスを Active Directory に追加する方法の詳細については、[ディレクトリ同期の準備]( https://go.microsoft.com/fwlink/p/?LinkId=525430)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71896-223">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a><span data-ttu-id="71896-224">Office 365 で、オンプレミスの UPN に一致する UPN</span><span class="sxs-lookup"><span data-stu-id="71896-224">Match the on-premises UPN with the Office 365 UPN</span></span>

<span data-ttu-id="71896-p118">ディレクトリ同期処理をされている場合、Office 365 のユーザーの UPN が設置ディレクトリ サービスで定義されているユーザーの設置型の UPN が一致しません。これは、ドメインを確認する前に、ユーザーにライセンスが割り当てられていた場合に発生します。これを修正するには、Office 365 の UPN が企業内のユーザー名とドメインと一致することを確認するのには、ユーザーの UPN を更新するのには[重複する UPN を解決するのに PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=396730)を使用します。設置ディレクトリ サービスの UPN を更新するし、Azure Active Directory ユーザーとの同期に、オンプレミスの変更を行う前に、Office 365 のユーザーのライセンスを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71896-p118">If you've already set up directory synchronization, the user's UPN for Office 365 may not match the user's on-premises UPN that's defined in your on-premises directory service. This can occur when a user was assigned a license before the domain was verified. To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Office 365 UPN matches the corporate user name and domain. If you are updating the UPN in the on-premises directory service and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Office 365 prior to making the changes on-premises.</span></span> 
  
<span data-ttu-id="71896-229">[ディレクトリ同期の .local ドメイン) などのルーティング不可能なドメインを準備する方法](prepare-a-non-routable-domain-for-directory-synchronization.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71896-229">See also [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="71896-230">ディレクトリ統合ツール</span><span class="sxs-lookup"><span data-stu-id="71896-230">Directory integration tools</span></span>

<span data-ttu-id="71896-p119">ディレクトリ同期は、ディレクトリ オブジェクト (ユーザー、グループ、および連絡先)、オンプレミスの Active Directory 環境から Office 365 のディレクトリ インフラストラクチャ、Azure Active Directory の同期です。使用できるツールとその機能の一覧については、[ディレクトリの統合ツール](https://go.microsoft.com/fwlink/p/?LinkID=510956)を参照してください。推奨されるツールは、 [Microsoft Azure Active Directory に接続](https://go.microsoft.com/fwlink/p/?LinkID=510956)します。Azure Active Directory の接続の詳細については、[オンプレミス ユーザー Azure Active Directory との統合](https://go.microsoft.com/fwlink/p/?LinkId=527969)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71896-p119">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure, Azure Active Directory. See [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality. The recommended tool is [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). For more information about Azure Active Directory Connect, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span>
  
<span data-ttu-id="71896-p120">マークされている場合、ユーザー アカウントは、最初に Office 365 のディレクトリと同期は、アクティブ化されていません。送信したり、電子メールを受信できないし、サブスクリプション ライセンスを消費しません。特定のユーザーに Office 365 のサブスクリプションを割り当てる準備ができたら、選択して、[ビジネス向けの Office 365 のユーザーにライセンスを割り当てる](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)ことによってそれらをアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71896-p120">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as not activated. They cannot send or receive email, and they don't consume subscription licenses. When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>
  
<span data-ttu-id="71896-p121">ライセンスを割り当てるには[PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097)を使用することもできます。自動化ソリューションは、 [Office 365 ユーザーにライセンスを自動的に割り当てるに PowerShell を使用する方法](https://go.microsoft.com/fwlink/p?LinkID=329805)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71896-p121">You can also use [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) to assign licenses. See [How to Use PowerShell to Automatically Assign Licenses to Your Office 365 Users](https://go.microsoft.com/fwlink/p?LinkID=329805) for an automated solution.</span></span>