---
title: Office 365 のグローバル管理者アカウントを保護する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 4/10/2018
ms.audience: Admin
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
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: 次の3つの手順に従って、Office 365 サブスクリプションへのグローバル管理者アクセスを保護します。
ms.openlocfilehash: 23d47ec1f5fc4126113dd69e1ac6400d003ca41f
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573921"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="1ed0c-103">Office 365 のグローバル管理者アカウントを保護する</span><span class="sxs-lookup"><span data-stu-id="1ed0c-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="1ed0c-104">**概要:** グローバル管理者アカウントの侵害に基づいて、Office 365 サブスクリプションを攻撃から保護します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="1ed0c-105">office 365 サブスクリプションのセキュリティ侵害 (情報の収集、フィッシング攻撃など) は、通常、office 365 全体管理者アカウントの資格情報を侵害することによって行われます。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-105">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account.</span></span> <span data-ttu-id="1ed0c-106">クラウドのセキュリティは、お互いと Microsoft の間のパートナーシップです。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-106">Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="1ed0c-107">Microsoft クラウドサービスは、信頼とセキュリティの基礎に基づいて構築されています。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-107">Microsoft cloud services are built on a foundation of trust and security.</span></span> <span data-ttu-id="1ed0c-108">Microsoft は、データとアプリケーションを保護するためのセキュリティ制御と機能を提供しています。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-108">Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="1ed0c-109">データと id、およびそれらを保護する責任、オンプレミスのリソースのセキュリティ、および管理するクラウドコンポーネントのセキュリティを所有しています。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="1ed0c-110">Microsoft は、組織を保護するための機能を提供していますが、使用する場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-110">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them.</span></span> <span data-ttu-id="1ed0c-111">これらを使用しないと、攻撃にさらされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-111">If you do not use them, you may be vulnerable to attack.</span></span> <span data-ttu-id="1ed0c-112">全体管理者アカウントを保護するために、Microsoft は次のことを行うための詳細な指示にお役立てください。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-112">To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="1ed0c-113">専任の Office 365 グローバル管理者アカウントを作成し、必要な場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="1ed0c-114">専用の Office 365 のグローバル管理者アカウントに対して多要素認証を構成し、最強のセカンダリ認証形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="1ed0c-115">Office 365 Cloud App Security を有効にして構成し、不審な全体管理者アカウントアクティビティを監視します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="1ed0c-116">この記事ではグローバル管理者アカウントに重点を置いていますが、サブスクリプション内のデータにアクセスするための広範な権限を持つその他のアカウント (電子情報開示管理者やセキュリティ、コンプライアンスなど) についても考慮する必要があります。管理者アカウントは、同じ方法で保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="1ed0c-117">手順 1.</span><span class="sxs-lookup"><span data-stu-id="1ed0c-117">Step 1.</span></span> <span data-ttu-id="1ed0c-118">専任の Office 365 グローバル管理者アカウントを作成し、必要な場合にのみ使用する</span><span class="sxs-lookup"><span data-stu-id="1ed0c-118">Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="1ed0c-119">グローバル管理者特権を必要とする、ユーザーアカウントへの役割の割り当てなど、比較的少数の管理タスクがあります。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-119">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges.</span></span> <span data-ttu-id="1ed0c-120">そのため、グローバル管理者の役割が割り当てられている日常のユーザーアカウントを使用する代わりに、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-120">Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="1ed0c-121">グローバル管理者の役割が割り当てられているユーザーアカウントのセットを決定します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-121">Determine the set of user accounts that have been assigned the global admin role.</span></span> <span data-ttu-id="1ed0c-122">これを行うには、Windows PowerShell コマンドプロンプトの Microsoft Azure Active Directory モジュールで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-122">You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="1ed0c-123">グローバル管理者の役割が割り当てられているユーザーアカウントを使用して、Office 365 サブスクリプションにサインインします。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="1ed0c-124">少なくとも1つの専用のグローバル管理者ユーザーアカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-124">Create at least one and up to a maximum of five dedicated global administrator user accounts.</span></span> <span data-ttu-id="1ed0c-125">**少なくとも12文字の強力なパスワードを使用してください。**</span><span class="sxs-lookup"><span data-stu-id="1ed0c-125">**Use strong passwords at least 12 characters long.**</span></span> <span data-ttu-id="1ed0c-126">詳細について[は、「強力なパスワードを作成する](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-126">See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information.</span></span> <span data-ttu-id="1ed0c-127">新しいアカウントのパスワードを安全な場所に格納します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-127">Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="1ed0c-128">新しい専用のグローバル管理者ユーザーアカウントに、グローバル管理者の役割を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="1ed0c-129">Office 365 からサインアウトします。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="1ed0c-130">新しい専用のグローバル管理者ユーザーアカウントのいずれかを使用してサインインします。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="1ed0c-131">手順1でグローバル管理者の役割が割り当てられている既存のユーザーアカウントごとに、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="1ed0c-132">グローバル管理者ロールを削除します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="1ed0c-133">そのユーザーのジョブ機能と責任に応じて、管理者の役割をアカウントに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-133">Assign admin roles to the account that are appropriate to that user's job function and responsibility.</span></span> <span data-ttu-id="1ed0c-134">office 365 のさまざまな管理者ロールの詳細については、「 [office 2013 管理者の役割につい](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)て」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-134">For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="1ed0c-135">Office 365 からサインアウトします。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="1ed0c-136">結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-136">The result should be:</span></span>
  
- <span data-ttu-id="1ed0c-137">グローバル管理者の役割を持つサブスクリプションで唯一のユーザーアカウントは、専用のグローバル管理者アカウントの新しいセットです。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-137">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts.</span></span> <span data-ttu-id="1ed0c-138">このことを確認するには、次の PowerShell コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-138">Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="1ed0c-139">サブスクリプションを管理するその他の通常のユーザー アカウントには、各自の職務に関連する管理ロールが割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="1ed0c-140">この時点から、グローバル管理者特権を必要とするタスクに対してのみ、専用のグローバル管理者アカウントを使用してサインインします。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-140">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges.</span></span> <span data-ttu-id="1ed0c-141">他のすべての Office 365 管理は、他の管理役割をユーザーアカウントに割り当てることによって実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-141">All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="1ed0c-142">はい。これには、日常のユーザーアカウントとしてサインアウトし、専用のグローバル管理者アカウントでサインインするための追加の手順が必要になります。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-142">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account.</span></span> <span data-ttu-id="1ed0c-143">ただし、この操作を実行する必要があるのは、全体管理者の操作の場合だけです。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-143">But this only needs to be done occasionally for global administrator operations.</span></span> <span data-ttu-id="1ed0c-144">グローバル管理者アカウント違反の後に Office 365 サブスクリプションを回復するには、さらに多くの手順が必要になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-144">Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="1ed0c-145">手順 2.</span><span class="sxs-lookup"><span data-stu-id="1ed0c-145">Step 2.</span></span> <span data-ttu-id="1ed0c-146">専用の Office 365 のグローバル管理者アカウントに対して多要素認証を構成し、最強のセカンダリ認証形式を使用する</span><span class="sxs-lookup"><span data-stu-id="1ed0c-146">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="1ed0c-147">グローバル管理者アカウントの多要素認証 (MFA) には、アカウント名とパスワード以外の追加情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-147">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password.</span></span> <span data-ttu-id="1ed0c-148">Office 365 では、次の認証方法がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-148">Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="1ed0c-149">電話</span><span class="sxs-lookup"><span data-stu-id="1ed0c-149">A phone call</span></span>
    
- <span data-ttu-id="1ed0c-150">ランダムに生成されるパス コード</span><span class="sxs-lookup"><span data-stu-id="1ed0c-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="1ed0c-151">スマート カード (仮想または物理)</span><span class="sxs-lookup"><span data-stu-id="1ed0c-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="1ed0c-152">生体認証デバイス</span><span class="sxs-lookup"><span data-stu-id="1ed0c-152">A biometric device</span></span>
    
<span data-ttu-id="1ed0c-153">クラウド (クラウド id モデル) のみに格納されているユーザーアカウントを使用している小規模な企業では、次の手順を使用して、電話呼び出しまたはスマートフォンに送信されたテキストメッセージ検証コードを使用して MFA を構成します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="1ed0c-154">[MFA を有効に](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="1ed0c-155">[Office 365 の2段階認証をセットアップ](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)して、認証方法として電話呼び出しまたはテキストメッセージの各専用のグローバル管理者アカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="1ed0c-156">Office 365 ハイブリッド id モデルを使用している大規模な組織の場合は、さらに多くの検証オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-156">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options.</span></span> <span data-ttu-id="1ed0c-157">より強力なセカンダリ認証方法に対してセキュリティインフラストラクチャが既に配置されている場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-157">If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="1ed0c-158">[MFA を有効に](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="1ed0c-159">[Office 365 の2段階認証をセットアップ](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)して、適切な検証方法にそれぞれの専用のグローバル管理者アカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="1ed0c-160">目的の強力な検証方法のセキュリティインフラストラクチャが、Office 365 MFA に適していない場合は、電話呼び出しまたはテキストメッセージを使用して MFA で専用のグローバル管理者アカウントを構成することを強くお勧めします。中間のセキュリティ対策として、グローバル管理者アカウントのスマートフォンに送信される検証コード。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-160">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure.</span></span> <span data-ttu-id="1ed0c-161">MFA で提供される追加の保護を行わずに、専用のグローバル管理者アカウントを残さないようにします。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-161">Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="1ed0c-162">詳細については、「[Office 365 展開用の多要素認証の計画](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="1ed0c-163">MFA と PowerShell を使用して Office 365 サービスに接続するには、[この記事](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="1ed0c-164">手順 3.</span><span class="sxs-lookup"><span data-stu-id="1ed0c-164">Step 3.</span></span> <span data-ttu-id="1ed0c-165">疑わしいグローバル管理者アカウントアクティビティを監視する</span><span class="sxs-lookup"><span data-stu-id="1ed0c-165">Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="1ed0c-166">Office 365 Cloud App Security では、サブスクリプションの不審な動作を通知するポリシーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-166">Office 365 Cloud App Security lets you create policies to notify you of suspicious behavior in your subscription.</span></span> <span data-ttu-id="1ed0c-167">Cloud App Security は Office 365 E5 に組み込まれていますが、別のサービスとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-167">Cloud App Security is built into Office 365 E5, but is also available as a separate service.</span></span> <span data-ttu-id="1ed0c-168">たとえば、Office 365 E5 がない場合は、グローバル管理者、セキュリティ管理者、およびコンプライアンス管理者の役割が割り当てられているユーザーアカウントの個別の Cloud App Security ライセンスを購入することができます。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-168">For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="1ed0c-169">Office 365 サブスクリプションに Cloud App Security がある場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="1ed0c-170">セキュリティ管理者またはコンプライアンス管理者の役割が割り当てられているアカウントを使用して、Microsoft 365 管理センターにサインインします。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-170">Sign into the Microsoft 365 admin center with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="1ed0c-171">[Office 365 Cloud App Security を有効](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c)にします。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="1ed0c-172">[Office 365 Cloud App Security の異常検出ポリシー](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6)を確認して、特権のある管理アクティビティの異常なパターンを電子メールで通知します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="1ed0c-173">ユーザーアカウントをセキュリティ管理者の役割に追加するには、専用のグローバル管理者アカウントと MFA を使用して[Office 365 PowerShell に接続](https://technet.microsoft.com/library/dn975125.aspx#step3)し、ユーザーアカウントのユーザープリンシパル名を入力してから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="1ed0c-174">ユーザーアカウントをコンプライアンス管理者の役割に追加するには、ユーザーアカウントのユーザープリンシパル名を入力してから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="1ed0c-175">エンタープライズ組織のための追加の保護</span><span class="sxs-lookup"><span data-stu-id="1ed0c-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="1ed0c-176">手順1-3 の後に、次の追加の方法を使用して、全体管理者アカウントと、それを使用して実行する構成を可能な限り安全なものにするようにします。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="1ed0c-177">特権アクセスワークステーション (PAW)</span><span class="sxs-lookup"><span data-stu-id="1ed0c-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="1ed0c-178">高度な権限のあるタスクの実行が可能な限り安全であることを確認するには、PAW を使用します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-178">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW.</span></span> <span data-ttu-id="1ed0c-179">PAW は、グローバル管理者アカウントを必要とする Office 365 構成など、機密性の高い構成タスクにのみ使用される専用のコンピューターです。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-179">A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account.</span></span> <span data-ttu-id="1ed0c-180">このコンピューターはインターネットブラウジングや電子メールで毎日使用されていないため、インターネット攻撃および脅威から保護するのが適切です。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-180">Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="1ed0c-181">PAW をセットアップする方法については、「 [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="1ed0c-182">Azure AD Privileged Identity Management (PIM)</span><span class="sxs-lookup"><span data-stu-id="1ed0c-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="1ed0c-183">グローバル管理者アカウントにグローバル管理者の役割を永続的に割り当てずに、Azure AD PIM を使用して、必要に応じて、グローバル管理者の役割をオンデマンドで一度だけ割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="1ed0c-184">全体管理者アカウントを永続的な管理者として使用するのではなく、管理者となります。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-184">Instead of your global administrator accounts being a permanent admin, they become eligible administrators.</span></span> <span data-ttu-id="1ed0c-185">グローバル管理者の役割は、ユーザーが必要とするまで非アクティブです。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-185">The global administrator role is inactive until someone needs it.</span></span> <span data-ttu-id="1ed0c-186">次に、アクティブ化プロセスを完了して、グローバル管理者の役割を、あらかじめ決められた時間だけグローバル管理者アカウントに追加します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-186">You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time.</span></span> <span data-ttu-id="1ed0c-187">時間が経過すると、PIM はグローバル管理者アカウントから全体管理者の役割を削除します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-187">When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="1ed0c-188">PIM を使用すると、このプロセスによって、グローバル管理者アカウントが悪意のあるユーザーの攻撃および使用に対して脆弱になる時間が大幅に短縮されます。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="1ed0c-189">詳細については、「 [Azure AD の特権 id 管理を構成する](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="1ed0c-190">PIM は、Enterprise Mobility + Security (EMS) E5 に含まれる Azure Active Directory Premium P2 で利用できます。また、全体管理者アカウントの個別のライセンスを購入することもできます。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="1ed0c-191">Office 365 ログ用のセキュリティ情報およびイベント管理 (SIEM) ソフトウェア</span><span class="sxs-lookup"><span data-stu-id="1ed0c-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="1ed0c-192">サーバー上での SIEM ソフトウェア実行では、アプリケーションとネットワークハードウェアによって作成されたセキュリティ通知とイベントのリアルタイム分析を実行します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-192">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware.</span></span> <span data-ttu-id="1ed0c-193">SIEM サーバーに Office 365 のセキュリティの警告とイベントを分析およびレポート機能に含めることができるようにするには、これらを SIEM システムに統合します。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-193">To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="1ed0c-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="1ed0c-194">Azure AD</span></span>
    
    <span data-ttu-id="1ed0c-195">詳細については、「 [Azure リソースからのログを SIEM システムに統合する](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="1ed0c-196">Office 365 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="1ed0c-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="1ed0c-197">詳細については、「 [SIEM server を Office 365 Cloud App Security と統合する](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="1ed0c-198">次の手順</span><span class="sxs-lookup"><span data-stu-id="1ed0c-198">Next step</span></span>

<span data-ttu-id="1ed0c-199">「 [Office 365 のセキュリティのベストプラクティス」を](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3)参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ed0c-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

