---
title: Office 365 グローバル管理者アカウントの保護
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/15/2020
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
f1.keywords:
- NOCSH
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Office 365 サブスクリプションへのグローバル管理者アクセスを保護します。
ms.openlocfilehash: 4f3e7dcb23f467768d647b7a5e8db9c41af2d076
ms.sourcegitcommit: fa25333a28ad300a7be990c1491d95f09a214a12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2020
ms.locfileid: "44253294"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="91f28-103">Office 365 グローバル管理者アカウントの保護</span><span class="sxs-lookup"><span data-stu-id="91f28-103">Protect your Office 365 global administrator accounts</span></span>

<span data-ttu-id="91f28-104">*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="91f28-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="91f28-105">Office 365 サブスクリプションのセキュリティ侵害 (情報の収集、フィッシング攻撃など) は、通常、Office 365 全体管理者アカウントの資格情報を侵害することによって行われます。</span><span class="sxs-lookup"><span data-stu-id="91f28-105">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account.</span></span> <span data-ttu-id="91f28-106">クラウドのセキュリティは、お互いと Microsoft の間のパートナーシップです。</span><span class="sxs-lookup"><span data-stu-id="91f28-106">Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="91f28-107">Microsoft クラウドサービスは、信頼とセキュリティの基礎に基づいて構築されています。</span><span class="sxs-lookup"><span data-stu-id="91f28-107">Microsoft cloud services are built on a foundation of trust and security.</span></span> <span data-ttu-id="91f28-108">Microsoft は、データとアプリケーションを保護するためのセキュリティ制御と機能を提供しています。</span><span class="sxs-lookup"><span data-stu-id="91f28-108">Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="91f28-109">データと id、およびそれらを保護する責任、オンプレミスのリソースのセキュリティ、および管理するクラウドコンポーネントのセキュリティを所有しています。</span><span class="sxs-lookup"><span data-stu-id="91f28-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="91f28-110">Microsoft は、組織を保護するための機能を提供していますが、使用する場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="91f28-110">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them.</span></span> <span data-ttu-id="91f28-111">これらを使用しないと、攻撃にさらされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="91f28-111">If you do not use them, you may be vulnerable to attack.</span></span> <span data-ttu-id="91f28-112">全体管理者アカウントを保護するために、Microsoft は次のことを行うための詳細な指示にお役立てください。</span><span class="sxs-lookup"><span data-stu-id="91f28-112">To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="91f28-113">専任の Office 365 グローバル管理者アカウントを作成し、必要な場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="91f28-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="91f28-114">専用の Office 365 のグローバル管理者アカウントに対して多要素認証を構成し、最強のセカンダリ認証形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="91f28-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
> [!注]<span data-ttu-id="91f28-115"> この記事ではグローバル管理者アカウントに重点を置いていますが、サブスクリプション内のデータにアクセスするための広範な権限を持つ追加のアカウント (電子情報開示管理者やセキュリティまたはコンプライアンス管理者アカウントなど) を同じ方法で保護する必要があるかどうかを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91f28-115"> Although this article is focused on global administrator accounts, you should consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> <br > <span data-ttu-id="91f28-116">グローバル管理者アカウントは、ライセンスを追加することなく作成できます。</span><span class="sxs-lookup"><span data-stu-id="91f28-116">A global administrator account can be created without adding any licenses.</span></span>
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="91f28-117">手順 1.</span><span class="sxs-lookup"><span data-stu-id="91f28-117">Step 1.</span></span> <span data-ttu-id="91f28-118">専任の Office 365 グローバル管理者アカウントを作成し、必要な場合にのみ使用する</span><span class="sxs-lookup"><span data-stu-id="91f28-118">Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="91f28-119">グローバル管理者特権を必要とする、ユーザーアカウントへの役割の割り当てなど、比較的少数の管理タスクがあります。</span><span class="sxs-lookup"><span data-stu-id="91f28-119">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges.</span></span> <span data-ttu-id="91f28-120">そのため、グローバル管理者の役割が割り当てられている日常のユーザーアカウントを使用する代わりに、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="91f28-120">Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="91f28-121">グローバル管理者の役割が割り当てられているユーザーアカウントのセットを決定します。</span><span class="sxs-lookup"><span data-stu-id="91f28-121">Determine the set of user accounts that have been assigned the global admin role.</span></span> <span data-ttu-id="91f28-122">これを行うには、Azure Active (Azure AD) Directory PowerShell for Graph コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="91f28-122">You can do this with Azure Active (Azure AD) Directory PowerShell for Graph  command:</span></span>
  
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

2. <span data-ttu-id="91f28-123">グローバル管理者の役割が割り当てられているユーザーアカウントを使用して、Office 365 サブスクリプションにサインインします。</span><span class="sxs-lookup"><span data-stu-id="91f28-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="91f28-124">最大4つの専用のグローバル管理者ユーザーアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="91f28-124">Create up to a maximum of four dedicated global administrator user accounts.</span></span> <span data-ttu-id="91f28-125">**少なくとも12文字の強力なパスワードを使用してください。**</span><span class="sxs-lookup"><span data-stu-id="91f28-125">**Use strong passwords at least 12 characters long.**</span></span> <span data-ttu-id="91f28-126">詳細について[は、「強力なパスワードを作成する](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f28-126">See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information.</span></span> <span data-ttu-id="91f28-127">新しいアカウントのパスワードを安全な場所に格納します。</span><span class="sxs-lookup"><span data-stu-id="91f28-127">Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="91f28-128">新しい専用のグローバル管理者ユーザーアカウントに、グローバル管理者の役割を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="91f28-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="91f28-129">Office 365 からサインアウトします。</span><span class="sxs-lookup"><span data-stu-id="91f28-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="91f28-130">新しい専用のグローバル管理者ユーザーアカウントのいずれかを使用してサインインします。</span><span class="sxs-lookup"><span data-stu-id="91f28-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="91f28-131">手順1でグローバル管理者の役割が割り当てられている既存のユーザーアカウントごとに、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="91f28-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="91f28-132">グローバル管理者ロールを削除します。</span><span class="sxs-lookup"><span data-stu-id="91f28-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="91f28-133">そのユーザーのジョブ機能と責任に応じて、管理者の役割をアカウントに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="91f28-133">Assign admin roles to the account that are appropriate to that user's job function and responsibility.</span></span> <span data-ttu-id="91f28-134">Office 365 のさまざまな管理者ロールの詳細については、「[管理者の役割につい](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles)て」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f28-134">For more information about various admin roles in Office 365, see [About admin roles](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles).</span></span>
    
8. <span data-ttu-id="91f28-135">Office 365 からサインアウトします。</span><span class="sxs-lookup"><span data-stu-id="91f28-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="91f28-136">結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="91f28-136">The result should be:</span></span>
  
- <span data-ttu-id="91f28-137">グローバル管理者ロールを持つ、サブスクリプションのユーザー アカウントのみが、新しい専用のグローバル管理者アカウント セットとなります。</span><span class="sxs-lookup"><span data-stu-id="91f28-137">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts.</span></span> <span data-ttu-id="91f28-138">このことを確認するには、次の PowerShell コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="91f28-138">Verify this with the following PowerShell command:</span></span>
    
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

- <span data-ttu-id="91f28-139">サブスクリプションを管理するその他の通常のユーザー アカウントには、各自の職務に関連する管理ロールが割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="91f28-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="91f28-140">この時点から、グローバル管理者特権を必要とするタスクに対してのみ、専用のグローバル管理者アカウントを使用してサインインします。</span><span class="sxs-lookup"><span data-stu-id="91f28-140">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges.</span></span> <span data-ttu-id="91f28-141">他のすべての Office 365 管理は、他の管理役割をユーザーアカウントに割り当てることによって実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91f28-141">All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="91f28-142">これには、日常のユーザーアカウントとしてサインアウトし、専用のグローバル管理者アカウントでサインインするための追加の手順が必要になります。</span><span class="sxs-lookup"><span data-stu-id="91f28-142">This does require additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account.</span></span> <span data-ttu-id="91f28-143">ただし、この操作を実行する必要があるのは、全体管理者の操作の場合だけです。</span><span class="sxs-lookup"><span data-stu-id="91f28-143">But this only needs to be done occasionally for global administrator operations.</span></span> <span data-ttu-id="91f28-144">グローバル管理者アカウント違反の後に Office 365 サブスクリプションを回復するには、さらに多くの手順が必要になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="91f28-144">Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span>
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-additional-verification"></a><span data-ttu-id="91f28-145">手順 2. </span><span class="sxs-lookup"><span data-stu-id="91f28-145">Step 2.</span></span> <span data-ttu-id="91f28-146">専用の Office 365 のグローバル管理者アカウントに対して多要素認証を構成し、強力な検証方法を使用する</span><span class="sxs-lookup"><span data-stu-id="91f28-146">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of additional verification</span></span>

<span data-ttu-id="91f28-147">多要素認証 (MFA) には、アカウント名とパスワード以外の追加情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="91f28-147">Multi-factor authentication (MFA) requires additional information beyond the account name and password.</span></span> <span data-ttu-id="91f28-148">Office 365 では、次の追加の検証方法がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="91f28-148">Office 365 supports these additional verification methods:</span></span>
  
- <span data-ttu-id="91f28-149">Microsoft Authenticator アプリ</span><span class="sxs-lookup"><span data-stu-id="91f28-149">The Microsoft Authenticator app</span></span>

- <span data-ttu-id="91f28-150">電話</span><span class="sxs-lookup"><span data-stu-id="91f28-150">A phone call</span></span>
    
- <span data-ttu-id="91f28-151">テキストメッセージを使用して送信された、ランダムに生成された検証コード</span><span class="sxs-lookup"><span data-stu-id="91f28-151">A randomly generated verification code sent through a text message</span></span>
    
- <span data-ttu-id="91f28-152">スマート カード (仮想または物理)</span><span class="sxs-lookup"><span data-stu-id="91f28-152">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="91f28-153">生体認証デバイス</span><span class="sxs-lookup"><span data-stu-id="91f28-153">A biometric device</span></span>
    
>[!Note]
><span data-ttu-id="91f28-154">米国標準規格とテクノロジ (NIST) 標準に準拠する必要がある組織では、電話またはテキストメッセージベースの追加の検証方法を使用することは制限されています。</span><span class="sxs-lookup"><span data-stu-id="91f28-154">For organizations that must adhere to National Institute of Standards and Technology (NIST) standards, the use of a phone call or text message-based additional verification methods are restricted.</span></span> <span data-ttu-id="91f28-155">詳細については、[ここ](https://pages.nist.gov/800-63-FAQ/#q-b01)をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="91f28-155">Click [here](https://pages.nist.gov/800-63-FAQ/#q-b01) for the details.</span></span>
>

<span data-ttu-id="91f28-156">クラウドのみに格納されているユーザーアカウントを使用している小規模な企業 (クラウドのみの id モデル) の場合は、次の手順を使用して、電話呼び出しまたはスマートフォンに送信されたテキストメッセージの検証コードを使用して MFA を構成します。</span><span class="sxs-lookup"><span data-stu-id="91f28-156">If you are a small business that is using user accounts stored only in the cloud (the cloud-only identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="91f28-157">[MFA を設定](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)します。</span><span class="sxs-lookup"><span data-stu-id="91f28-157">[Set up MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span></span>
    
2. <span data-ttu-id="91f28-158">[Office 365 の MFA をセットアップ](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)して、認証方法として電話番号またはテキストメッセージのそれぞれの専用のグローバル管理者アカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="91f28-158">[Set up MFA for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="91f28-159">Office 365 ハイブリッド id モデルを使用している大規模な組織の場合は、さらに多くの検証オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="91f28-159">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options.</span></span> <span data-ttu-id="91f28-160">より強力なセカンダリ認証方法に対してセキュリティインフラストラクチャが既に配置されている場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="91f28-160">If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="91f28-161">[MFA を設定](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)します。</span><span class="sxs-lookup"><span data-stu-id="91f28-161">[Set up MFA](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication).</span></span>
    
2. <span data-ttu-id="91f28-162">[Office 365 の MFA をセットアップ](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)して、適切な検証方法にそれぞれの専用のグローバル管理者アカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="91f28-162">[Set up MFA for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="91f28-163">目的の強力な検証方法のセキュリティインフラストラクチャが、Office 365 MFA に適していない場合は、一時的なセキュリティ対策として、グローバル管理者アカウントのスマートフォンに送信されるテキストメッセージ検証コードを使用して、専用のグローバル管理者アカウントを MFA で構成することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="91f28-163">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure.</span></span> <span data-ttu-id="91f28-164">MFA で提供される追加の保護を行わずに、専用のグローバル管理者アカウントを残さないようにします。</span><span class="sxs-lookup"><span data-stu-id="91f28-164">Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="91f28-165">詳細については、「[Office 365 展開用の多要素認証の計画](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f28-165">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://docs.microsoft.com/office365/admin/security-and-compliance/multi-factor-authentication-plan).</span></span>
  
<span data-ttu-id="91f28-166">MFA と PowerShell を使用して Office 365 サービスに接続するには、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f28-166">To connect to Office 365 services with MFA and PowerShell, see these articles:</span></span>

- [<span data-ttu-id="91f28-167">ユーザーアカウント、グループ、ライセンスの Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="91f28-167">Office 365 PowerShell for user accounts, groups, and licenses</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)
- [<span data-ttu-id="91f28-168">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="91f28-168">Exchange Online</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-by-using-mfa)
- [<span data-ttu-id="91f28-169">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="91f28-169">SharePoint Online</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online#to-connect-with-multifactor-authentication-mfa)
- [<span data-ttu-id="91f28-170">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="91f28-170">Skype for Business Online</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell#connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication)

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="91f28-171">エンタープライズ組織のための追加の保護</span><span class="sxs-lookup"><span data-stu-id="91f28-171">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="91f28-172">手順1と2の後に、グローバル管理者アカウントと、それを使用して実行する構成ができる限り安全であることを確認するために、これらの追加の方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="91f28-172">After steps 1 and 2, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation"></a><span data-ttu-id="91f28-173">特権アクセスワークステーション</span><span class="sxs-lookup"><span data-stu-id="91f28-173">Privileged access workstation</span></span>

<span data-ttu-id="91f28-174">高い権限を持つタスクの実行が可能な限り安全であることを確認するには、特権アクセスワークステーション (PAW) を使用します。</span><span class="sxs-lookup"><span data-stu-id="91f28-174">To ensure that the execution of highly privileged tasks is as secure as possible, use a privileged access workstation (PAW).</span></span> <span data-ttu-id="91f28-175">PAW は、グローバル管理者アカウントを必要とする Office 365 構成など、機密性の高い構成タスクにのみ使用される専用のコンピューターです。</span><span class="sxs-lookup"><span data-stu-id="91f28-175">A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account.</span></span> <span data-ttu-id="91f28-176">このコンピューターはインターネットブラウジングや電子メールで毎日使用されていないため、インターネット攻撃および脅威から保護するのが適切です。</span><span class="sxs-lookup"><span data-stu-id="91f28-176">Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="91f28-177">PAW をセットアップする方法については、「」を参照してください [https://aka.ms/cyberpaw](https://aka.ms/cyberpaw) 。</span><span class="sxs-lookup"><span data-stu-id="91f28-177">For instructions on how to set up a PAW, see [https://aka.ms/cyberpaw](https://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management"></a><span data-ttu-id="91f28-178">Azure AD Privileged Identity Management</span><span class="sxs-lookup"><span data-stu-id="91f28-178">Azure AD Privileged Identity Management</span></span>

<span data-ttu-id="91f28-179">グローバル管理者アカウントにグローバル管理者の役割を永続的に割り当てるのではなく、Azure AD Privileged Identity Management (PIM) を使用して、必要に応じて、グローバル管理者の役割をオンデマンドで一度だけ割り当てられるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="91f28-179">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD Privileged Identity Management (PIM) to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="91f28-180">全体管理者アカウントを永続的な管理者として使用するのではなく、管理者となります。</span><span class="sxs-lookup"><span data-stu-id="91f28-180">Instead of your global administrator accounts being a permanent admin, they become eligible administrators.</span></span> <span data-ttu-id="91f28-181">グローバル管理者の役割は、ユーザーが必要とするまで非アクティブです。</span><span class="sxs-lookup"><span data-stu-id="91f28-181">The global administrator role is inactive until someone needs it.</span></span> <span data-ttu-id="91f28-182">次に、アクティブ化プロセスを完了して、グローバル管理者の役割を、あらかじめ決められた時間だけグローバル管理者アカウントに追加します。</span><span class="sxs-lookup"><span data-stu-id="91f28-182">You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time.</span></span> <span data-ttu-id="91f28-183">時間が経過すると、PIM はグローバル管理者アカウントから全体管理者の役割を削除します。</span><span class="sxs-lookup"><span data-stu-id="91f28-183">When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="91f28-184">PIM を使用すると、このプロセスによって、グローバル管理者アカウントが悪意のあるユーザーの攻撃および使用に対して脆弱になる時間が大幅に短縮されます。</span><span class="sxs-lookup"><span data-stu-id="91f28-184">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>

<span data-ttu-id="91f28-185">PIM は、Microsoft 365 Enterprise E5 または Enterprise Mobility + Security (EMS) E5 に含まれている Azure AD Premium P2 で利用できます。また、全体管理者アカウントの個別のライセンスを購入することもできます。</span><span class="sxs-lookup"><span data-stu-id="91f28-185">PIM is available with Azure AD Premium P2, which is included with Microsoft 365 Enterprise E5 or Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span>
  
<span data-ttu-id="91f28-186">詳細については、「 [AZURE AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f28-186">For more information, see [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="91f28-187">Office 365 ログ用のセキュリティ情報およびイベント管理 (SIEM) ソフトウェア</span><span class="sxs-lookup"><span data-stu-id="91f28-187">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="91f28-188">サーバー上での SIEM ソフトウェア実行では、アプリケーションとネットワークハードウェアによって作成されたセキュリティ通知とイベントのリアルタイム分析を実行します。</span><span class="sxs-lookup"><span data-stu-id="91f28-188">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware.</span></span> <span data-ttu-id="91f28-189">SIEM サーバーに Office 365 のセキュリティの警告とイベントを分析およびレポート機能に含めることができるようにするには、Azure AD をお客様の SEIM に統合します。</span><span class="sxs-lookup"><span data-stu-id="91f28-189">To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate Azure AD into you SEIM.</span></span> <span data-ttu-id="91f28-190">「 [Azure ログ統合の概要」を](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f28-190">See [Introduction to Azure Log Integration](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="91f28-191">次の手順</span><span class="sxs-lookup"><span data-stu-id="91f28-191">Next step</span></span>

<span data-ttu-id="91f28-192">Office 365 サブスクリプションの id を設定している場合は、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f28-192">If you're setting up identity for your Office 365 subscription, see:</span></span>

- <span data-ttu-id="91f28-193">クラウドのみの id を使用している場合は、[クラウドのみの id](cloud-only-identities.md)</span><span class="sxs-lookup"><span data-stu-id="91f28-193">[Cloud-only identities](cloud-only-identities.md) if you're using cloud-only identity</span></span>
- <span data-ttu-id="91f28-194">ハイブリッド id を使用している場合[にディレクトリ同期を準備](prepare-for-directory-synchronization.md)する</span><span class="sxs-lookup"><span data-stu-id="91f28-194">[Prepare for directory synchronization](prepare-for-directory-synchronization.md) if you're using hybrid identity</span></span>

  
## <a name="see-also"></a><span data-ttu-id="91f28-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="91f28-195">See also</span></span>

<span data-ttu-id="91f28-196">[Office 365 のセキュリティロードマップ](https://docs.microsoft.com/office365/securitycompliance/security-roadmap)。</span><span class="sxs-lookup"><span data-stu-id="91f28-196">[Office 365 security roadmap](https://docs.microsoft.com/office365/securitycompliance/security-roadmap).</span></span>
