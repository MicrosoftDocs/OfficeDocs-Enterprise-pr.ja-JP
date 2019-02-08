---
title: Office 365 全体管理者アカウントを保護する
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
description: これら 3 つの手順で Office 365 サブスクリプションをグローバル管理者のアクセスを保護します。
ms.openlocfilehash: 41168643fb8867017865860624c8b436460fa0b8
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897520"
---
# <a name="protect-your-office-365-global-administrator-accounts"></a><span data-ttu-id="f6cb5-103">Office 365 全体管理者アカウントを保護する</span><span class="sxs-lookup"><span data-stu-id="f6cb5-103">Protect your Office 365 global administrator accounts</span></span>

 <span data-ttu-id="f6cb5-104">**の概要:** Office 365 サブスクリプションをグローバル管理者アカウントの侵害に基づく攻撃から保護します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-104">**Summary:** Protect your Office 365 subscription from attacks based on the compromise of a global administrator account.</span></span> 
  
<span data-ttu-id="f6cb5-p101">情報収集を含め、Office 365 サブスクリプション、およびフィッシング攻撃では、セキュリティ侵害は通常、Office 365 のグローバル管理者アカウントの資格情報を侵害することで行われます。クラウドでのセキュリティは、お客様とマイクロソフトとのパートナーシップです。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p101">Security breaches of an Office 365 subscription, including information harvesting and phishing attacks, are typically done by compromising the credentials of an Office 365 global administrator account. Security in the cloud is a partnership between you and Microsoft:</span></span>
  
- <span data-ttu-id="f6cb5-p102">マイクロソフトのクラウド サービスは、信頼とセキュリティの基盤が構築されます。マイクロソフトでは、セキュリティ ・ コントロールと、データとアプリケーションを保護する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p102">Microsoft cloud services are built on a foundation of trust and security. Microsoft provides you security controls and capabilities to help you protect your data and applications.</span></span>
    
- <span data-ttu-id="f6cb5-109">データと id、および、設置型リソースのセキュリティ、および制御するクラウド コンポーネントのセキュリティを保護するための責任を所有します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-109">You own your data and identities and the responsibility for protecting them, the security of your on-premises resources, and the security of cloud components you control.</span></span>
    
<span data-ttu-id="f6cb5-p103">マイクロソフトは、お客様の組織を保護するための機能を提供していますが、それらを使用する場合にのみ有効です。それらを使用しない場合、は、攻撃に対する脆弱性が存在する必要があります。グローバル管理者アカウントを保護するには、マイクロソフトがお手伝いするに詳細が記載。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p103">Microsoft provides capabilities to help protect your organization, but they are effective only if you use them. If you do not use them, you may be vulnerable to attack. To protect your global administrator accounts, Microsoft is here to help you with detailed instructions to:</span></span>
  
1. <span data-ttu-id="f6cb5-113">専用の Office 365 のグローバル管理者アカウントを作成し、必要な場合のみに使用します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-113">Create dedicated Office 365 global administrator accounts and use them only when necessary.</span></span>
    
2. <span data-ttu-id="f6cb5-114">専用の Office 365 のグローバル管理者アカウントの複数要素の認証を構成し、最強の第 2 の認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-114">Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication.</span></span>
    
3. <span data-ttu-id="f6cb5-115">有効にし、不審なグローバル ・ アドミニストレータ ・ アカウント ・ アクティビティを監視する Office 365 のクラウド アプリケーションのセキュリティを構成します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-115">Enable and configure Office 365 Cloud App Security to monitor for suspicious global administrator account activity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="f6cb5-116">追加するかどうかを検討する必要がありますもこの資料は、グローバル ・ アドミニストレータ ・ アカウントに焦点を当てています、電子的証拠開示の管理者またはセキュリティやコンプライアンスなど、サブスクリプションのデータにアクセスするための広範なアクセス許可を持つアカウント同様に、管理者アカウントを保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-116">Although this article is focused on global administrator accounts, you should also consider whether additional accounts with wide-ranging permissions to access the data in your subscription, such as eDiscovery administrator or security or compliance administrator accounts, should be protected in the same way.</span></span> 
  
## <a name="step-1-create-dedicated-office-365-global-administrator-accounts-and-use-them-only-when-necessary"></a><span data-ttu-id="f6cb5-p104">手順 1 です。専用の Office 365 のグローバル管理者アカウントを作成し、必要な場合のみに使用</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p104">Step 1. Create dedicated Office 365 global administrator accounts and use them only when necessary</span></span>

<span data-ttu-id="f6cb5-p105">グローバル管理者権限を必要とするユーザー アカウントにロールを割り当てるなど、比較的少数の管理タスクがあります。したがって、グローバル管理者ロールが割り当てられている日常的なユーザー アカウントを使用するには、代わりに次の手順操作を行います。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p105">There are relatively few administrative tasks, such as assigning roles to user accounts, that require global administrator privileges. Therefore, instead of using everyday user accounts that have been assigned the global admin role, do these steps:</span></span>
  
1. <span data-ttu-id="f6cb5-p106">グローバル管理者ロールが割り当てられているユーザー アカウントのセットを決定します。Microsoft Azure Active Directory モジュールを Windows PowerShell コマンド プロンプトでこのコマンドを使用してこれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p106">Determine the set of user accounts that have been assigned the global admin role. You can do this with this command at the Microsoft Azure Active Directory Module for Windows PowerShell command prompt:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

2. <span data-ttu-id="f6cb5-123">グローバル管理者ロールが割り当てられているユーザー アカウントで Office 365 サブスクリプションに署名します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-123">Sign into your Office 365 subscription with a user account that has been assigned the global admin role.</span></span>
    
3. <span data-ttu-id="f6cb5-p107">少なくとも 1 つを作成し、最大で 5 つのグローバル管理者ユーザー アカウントを専用です。**強力なパスワードには、少なくとも 12 文字長の使用**詳細については、[強力なパスワードを作成する](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password)を参照してください。新しいアカウントのパスワードを安全な場所に格納します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p107">Create at least one and up to a maximum of five dedicated global administrator user accounts. **Use strong passwords at least 12 characters long.** See [Create a strong password](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) for more information. Store the passwords for the new accounts in a secure location.</span></span> 
    
4. <span data-ttu-id="f6cb5-128">新しい専用のグローバル管理者のユーザー アカウントのそれぞれには、グローバル管理者ロールを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-128">Assign the global admin role to each of the new dedicated global administrator user accounts.</span></span>
    
5. <span data-ttu-id="f6cb5-129">Office 365 からサインアウトします。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-129">Sign out of Office 365.</span></span>
    
6. <span data-ttu-id="f6cb5-130">新しい専用のグローバル管理者ユーザー アカウントのいずれかでサインインします。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-130">Sign in with one of the new dedicated global administrator user accounts.</span></span>
    
7. <span data-ttu-id="f6cb5-131">既存ユーザー アカウントごとに手順 1 からグローバル管理者ロールが割り当てられていました。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-131">For each existing user account that had been assigned the global admin role from step 1:</span></span>
    
  - <span data-ttu-id="f6cb5-132">グローバル管理者の役割を削除します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-132">Remove the global admin role.</span></span>
    
  - <span data-ttu-id="f6cb5-p108">ユーザーの職務と責任に対応するアカウントに管理者の役割を割り当てます。Office 365 のさまざまな管理者の役割の詳細については、 [Office 365 の管理者の役割](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p108">Assign admin roles to the account that are appropriate to that user's job function and responsibility. For more information about various admin roles in Office 365, see [About Office 365 admin roles](https://support.office.com/article/da585eea-f576-4f55-a1e0-87090b6aaa9d).</span></span>
    
8. <span data-ttu-id="f6cb5-135">Office 365 からサインアウトします。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-135">Sign out of Office 365.</span></span>
    
<span data-ttu-id="f6cb5-136">結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-136">The result should be:</span></span>
  
- <span data-ttu-id="f6cb5-p109">グローバル管理者の役割を持つサブスクリプションの場合、唯一のユーザー アカウントとは、専用のグローバル管理者アカウントの新しいセットです。次の PowerShell コマンドを使用してこれを確認します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p109">The only user accounts in your subscription that have the global admin role are the new set of dedicated global administrator accounts. Verify this with the following PowerShell command:</span></span>
    
  ```
  Get-MsolRoleMember -RoleObjectId (Get-MsolRole -RoleName "Company Administrator").ObjectId
  ```

- <span data-ttu-id="f6cb5-139">サブスクリプションを管理するその他の通常のユーザー アカウントには、各自の職務に関連する管理ロールが割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-139">All other everyday user accounts that manage your subscription have admin roles assigned that are associated with their job responsibilities.</span></span>
    
<span data-ttu-id="f6cb5-p110">この時点以降から署名する専用のグローバル管理者アカウントを使用してグローバル管理者権限を必要とするタスクに対してのみです。ユーザー アカウントにその他の管理役割を割り当てることによって、他のすべての Office 365 の管理を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p110">From this moment onward, you sign in with the dedicated global administrator accounts only for tasks that require global administrator privileges. All other Office 365 administration must be done by assigning other administration roles to user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f6cb5-p111">[はい] を日常的なユーザー アカウントでサインインし、専用のグローバル管理者アカウントを使ってサインインする追加の手順が必要です。グローバル管理者の操作が実行するだけで済みますが。グローバル管理者アカウントの侵害がより多くの手順を必要とした後、Office 365 サブスクリプションを回復することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p111">Yes, this requires additional steps to sign out as your everyday user account and sign in with a dedicated global administrator account. But this only needs to be done occasionally for global administrator operations. Consider that recovering your Office 365 subscription after a global administrator account breach requires a lot more steps.</span></span> 
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-office-365-global-administrator-accounts-and-use-the-strongest-form-of-secondary-authentication"></a><span data-ttu-id="f6cb5-p112">手順 2 です。専用の Office 365 のグローバル管理者アカウントに対して多要素認証を構成して、最強の第 2 の認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p112">Step 2. Configure multi-factor authentication for your dedicated Office 365 global administrator accounts and use the strongest form of secondary authentication</span></span>

<span data-ttu-id="f6cb5-p113">グローバル管理者アカウントには、多要素認証 (MFA) には、アカウント名とパスワード以外の追加情報が必要です。Office 365 には、これらの検証メソッドがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p113">Multi-factor authentication (MFA) for your global administrator accounts requires additional information beyond the account name and password. Office 365 supports these verification methods:</span></span>
  
- <span data-ttu-id="f6cb5-149">電話</span><span class="sxs-lookup"><span data-stu-id="f6cb5-149">A phone call</span></span>
    
- <span data-ttu-id="f6cb5-150">ランダムに生成されるパス コード</span><span class="sxs-lookup"><span data-stu-id="f6cb5-150">A randomly generated pass code</span></span>
    
- <span data-ttu-id="f6cb5-151">スマート カード (仮想または物理)</span><span class="sxs-lookup"><span data-stu-id="f6cb5-151">A smart card (virtual or physical)</span></span>
    
- <span data-ttu-id="f6cb5-152">生体認証デバイス</span><span class="sxs-lookup"><span data-stu-id="f6cb5-152">A biometric device</span></span>
    
<span data-ttu-id="f6cb5-153">クラウド (クラウドの識別情報モデル) にのみ保存されているユーザー アカウントを使用しているスモール ビジネスの場合は、電話またはスマート フォンに送信されるテキスト メッセージの検証コードを使用して MFA を構成するのには次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-153">If you are a small business that is using user accounts stored only in the cloud (the cloud identity model), use these steps to configure MFA using a phone call or a text message verification code sent to a smart phone:</span></span>
  
1. <span data-ttu-id="f6cb5-154">[MFA を有効に](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-154">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="f6cb5-155">検証方法として専用電話またはテキスト メッセージのグローバル管理者アカウントのそれぞれを構成するのには[Office 365 の 2 段階の検証を設定](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-155">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for phone call or text message as the verification method.</span></span> 
    
<span data-ttu-id="f6cb5-p114">Office 365 ハイブリッドの識別情報モデルを使用している大規模な組織である場合は、検証オプションが増えました。セキュリティ インフラストラクチャを既により強力な代替の認証方法のためにある場合は、次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p114">If you are a larger organization that is using an Office 365 hybrid identity model, you have more verification options. If you have the security infrastructure already in place for a stronger secondary authentication method, use these steps:</span></span>
  
1. <span data-ttu-id="f6cb5-158">[MFA を有効に](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6)します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-158">[Enable MFA](https://support.office.com/article/Set-up-multi-factor-authentication-for-Office-365-users-8f0454b2-f51a-4d9c-bcde-2c48e41621c6).</span></span>
    
2. <span data-ttu-id="f6cb5-159">それぞれを構成するのには[Office 365 の 2 段階の検証の設定](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14)は、適切な検証メソッドのグローバル管理者アカウントを専用です。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-159">[Set up 2-step verification for Office 365](https://support.office.com/article/Set-up-2-step-verification-for-Office-365-ace1d096-61e5-449b-a875-58eb3d74de14) to configure each dedicated global administrator account for the appropriate verification method.</span></span> 
    
<span data-ttu-id="f6cb5-p115">Office 365 の MFA の機能している目的のより強力な検証方法のセキュリティ インフラストラクチャがない場合は、強くお勧め MFA では、専用のグローバル管理者アカウントを構成すること、電話またはテキスト メッセージを使用して検証コードが暫定的なセキュリティ対策として、グローバル管理者アカウントにスマート フォンに送信します。MFA によって提供される追加の保護機能なし、専用のグローバル管理者アカウントをしないでください。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p115">If the security infrastructure for the desired stronger verification method is not in place and functioning for Office 365 MFA, we strongly recommend that you configure dedicated global administrator accounts with MFA using a phone call or a text message verification code sent to a smart phone for your global administrator accounts as an interim security measure. Do not leave your dedicated global administrator accounts without the additional protection provided by MFA.</span></span>
  
<span data-ttu-id="f6cb5-162">詳細については、「[Office 365 展開用の多要素認証の計画](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-162">For more information, see [Plan for multi-factor authentication for Office 365 Deployments](https://support.office.com/article/043807b2-21db-4d5c-b430-c8a6dee0e6ba).</span></span>
  
<span data-ttu-id="f6cb5-163">MFA と PowerShell を Office 365 サービスに接続するには、[この資料](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-163">To connect to Office 365 services with MFA and PowerShell, see [this article](https://blogs.technet.microsoft.com/solutions_advisory_board/2017/04/27/connect-to-office-365-services-with-multifactor-authentication-mfa-and-powershell/).</span></span>
  
## <a name="step-3-monitor-for-suspicious-global-administrator-account-activity"></a><span data-ttu-id="f6cb5-p116">ステップ 3 です。不審なグローバル ・ アドミニストレータ ・ アカウント ・ アクティビティの監視</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p116">Step 3. Monitor for suspicious global administrator account activity</span></span>

<span data-ttu-id="f6cb5-p117">Office 365 のクラウド アプリケーションのセキュリティを使用して、サブスクリプションの場合、不審な動作を通知するためのポリシーを作成できます。クラウド アプリケーションのセキュリティは、Office 365 の E5 に組み込まれていますが、個別のサービスとしても利用。などの Office 365 の E5 がない場合は、グローバル管理者、セキュリティ管理者、およびコンプライアンス管理者ロールに割り当てられているユーザー アカウント用の個々 のクラウド アプリケーションのセキュリティ ライセンスを購入できます。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p117">Office 365 Cloud App Security lets you create policies to notify you of suspicious behavior in your subscription. Cloud App Security is built into Office 365 E5, but is also available as a separate service. For example, if you do not have Office 365 E5, you can purchase individual Cloud App Security licenses for the user accounts that are assigned the global administrator, security administrator, and compliance administrator roles.</span></span>
  
<span data-ttu-id="f6cb5-169">クラウド アプリケーションのセキュリティがある場合、Office 365 サブスクリプションで、以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-169">If you have Cloud App Security in your Office 365 subscription, use these steps:</span></span>
  
1. <span data-ttu-id="f6cb5-170">セキュリティ管理者やコンプライアンス管理者の役割が割り当てられたアカウントを使用して Office 365 ポータルにサインインします。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-170">Sign into the Office 365 portal with an account that is assigned the Security Administrator or Compliance Administrator role.</span></span>
    
2. <span data-ttu-id="f6cb5-171">[Office 365 のクラウド アプリケーションのセキュリティを有効](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c)します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-171">[Turn on Office 365 Cloud App Security](https://support.office.com/article/ba919c73-d021-404d-9850-eec57e78678c).</span></span>
    
3. <span data-ttu-id="f6cb5-172">特権の管理活動の異常なパターンの e メールで通知する、 [Office 365 のクラウド アプリケーションのセキュリティでの異常検出ポリシー](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6)を確認します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-172">Review your [Anomaly detection policies in Office 365 Cloud App Security](https://support.office.com/article/88935b4e-dcb1-47f1-8aca-1bf8fb069db6) to notify you by email of anomalous patterns of privileged administrative activity.</span></span> 
    
<span data-ttu-id="f6cb5-173">セキュリティ管理者ロールにユーザー アカウントを追加するには専用のグローバル管理者アカウントと、MFA、 [Office 365 の PowerShell への接続](https://technet.microsoft.com/library/dn975125.aspx#step3)ををユーザー アカウントのユーザー プリンシパル名を入力し、し、これらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-173">To add a user account to the Security Administrator role, [connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx#step3) with a dedicated global administrator account and MFA, fill in the user principal name of the user account, and then run these commands:</span></span> 
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upn -RoleName "Security Administrator"
```

<span data-ttu-id="f6cb5-174">コンプライアンス管理者ロールにユーザー アカウントを追加するのにはユーザー アカウントのユーザー プリンシパル名を入力し、これらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-174">To add a user account to the Compliance Administrator role, fill in the user principal name of the user account, and then run these commands:</span></span>
  
```
$upn="<User principal name of the account>"
Add-MsolRoleMember -RoleMemberEmailAddress  $upn -RoleName "Compliance Administrator"
```

## <a name="additional-protections-for-enterprise-organizations"></a><span data-ttu-id="f6cb5-175">企業向けの付加的な保護</span><span class="sxs-lookup"><span data-stu-id="f6cb5-175">Additional protections for enterprise organizations</span></span>

<span data-ttu-id="f6cb5-176">手順 1 ~ 3 は、グローバル管理者アカウント、および構成を使用することを実行することを確認するのにはこれらのメソッドを使用して後、は、可能な限り安全です。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-176">After steps 1-3, use these additional methods to ensure that your global administrator account, and the configuration that you perform using it, are as secure as possible.</span></span>
  
### <a name="privileged-access-workstation-paw"></a><span data-ttu-id="f6cb5-177">特権アクセス ワークステーション (PAW)</span><span class="sxs-lookup"><span data-stu-id="f6cb5-177">Privileged Access Workstation (PAW)</span></span>

<span data-ttu-id="f6cb5-p118">高い特権を持つタスクの実行が可能な限り安全であることを確認するのには、PAW を使用します。PAW は、Office 365 の構成は、グローバル管理者アカウントを必要とするなど、機密性の高い構成のタスクにのみ使用される専用のコンピューターです。このコンピューターがインターネットの閲覧や電子メールを毎日使用しないためインターネットへの攻撃や脅威からよりよく保護されています。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p118">To ensure that the execution of highly privileged tasks is as secure as possible, use a PAW. A PAW is a dedicated computer that is only used for sensitive configuration tasks, such as Office 365 configuration that requires a global administrator account. Because this computer is not used daily for Internet browsing or email, it is better protected from Internet attacks and threats.</span></span>
  
<span data-ttu-id="f6cb5-181">PAW を設定する方法の詳細についてを参照してください[http://aka.ms/cyberpaw](http://aka.ms/cyberpaw)。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-181">For instructions on how to set up a PAW, see [http://aka.ms/cyberpaw](http://aka.ms/cyberpaw).</span></span>
  
### <a name="azure-ad-privileged-identity-management-pim"></a><span data-ttu-id="f6cb5-182">Azure AD 特権 Id 管理 (PIM)</span><span class="sxs-lookup"><span data-stu-id="f6cb5-182">Azure AD Privileged Identity Management (PIM)</span></span>

<span data-ttu-id="f6cb5-183">グローバル管理者アカウントをグローバル管理者ロールを割り当てられる恒久的にするのではなく、グローバル管理者ロールの割り当てをオン ・ デマンド、ジャスト ・ イン ・ タイムを有効にすることが必要なときに Azure AD の PIM を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-183">Rather than having your global administrator accounts be permanently assigned the global administrator role, you can use Azure AD PIM to enable on-demand, just-in-time assignment of the global administrator role when it is needed.</span></span>
  
<span data-ttu-id="f6cb5-p119">永続的な管理をされている、グローバル管理者アカウントではなく管理者を対象となります。誰かが必要となるまで、グローバル管理者ロールはアクティブではありません。あらかじめ決められた時間数のグローバル管理者アカウントに、グローバル管理者ロールを追加するのには、ライセンス認証プロセスを完了するとします。時間が経過すると、PIM は、グローバル ・ アドミニストレータ ・ アカウントから、グローバル管理者ロールを削除します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p119">Instead of your global administrator accounts being a permanent admin, they become eligible administrators. The global administrator role is inactive until someone needs it. You then complete an activation process to add the global administrator role to the global administrator account for a predetermined amount of time. When the time expires, PIM removes the global administrator role from the global administrator account.</span></span>
  
<span data-ttu-id="f6cb5-188">PIM を使用して、このプロセスは、グローバル ・ アドミニストレータ ・ アカウントは攻撃や悪意のあるユーザーが使用する脆弱性が存在する時間を大幅に削減します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-188">Using PIM and this process significantly reduces the amount of time that your global administrator accounts are vulnerable to attack and use by malicious users.</span></span>
  
<span data-ttu-id="f6cb5-189">詳細については、 [Azure AD の特権の構成の Id 管理](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-189">For more information, see [Configure Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).</span></span>
  
> [!NOTE]
> <span data-ttu-id="f6cb5-190">Azure Active ディレクトリ プレミアム p2、エンタープライズ ・ モビリティとセキュリティ (EMS) E5 に含まれては、使用可能な PIM を使用するか、グローバル管理者アカウントに個々 のライセンスを購入することができます。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-190">PIM is available with Azure Active Directory Premium P2, which is included with Enterprise Mobility + Security (EMS) E5, or you can purchase individual licenses for your global administrator accounts.</span></span> 
  
### <a name="security-information-and-event-management-siem-software-for-office-365-logging"></a><span data-ttu-id="f6cb5-191">Office 365 のログのセキュリティ情報およびイベント管理 (SIEM) ソフトウェア</span><span class="sxs-lookup"><span data-stu-id="f6cb5-191">Security information and event management (SIEM) software for Office 365 logging</span></span>

<span data-ttu-id="f6cb5-p120">SIEM ソフトウェアがサーバー上で実行では、セキュリティ警告は、アプリケーションおよびネットワークのハードウェアによって作成されるイベントのリアルタイムの分析を実行します。SIEM サーバーなど、Office 365 のセキュリティの警告イベントの分析とレポート作成機能では、SIEM システムでは、これらを統合します。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-p120">SIEM software run on a server performs real-time analysis of security alerts and events created by applications and network hardware. To allow your SIEM server to include Office 365 security alerts and events in its analysis and reporting functions, integrate these in your SIEM system:</span></span>
  
- <span data-ttu-id="f6cb5-194">Azure AD</span><span class="sxs-lookup"><span data-stu-id="f6cb5-194">Azure AD</span></span>
    
    <span data-ttu-id="f6cb5-195">詳細については、 [SIEM システムに Azure のリソースの統合ログ](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-195">For more information, see [Integrate logs from Azure resources into your SIEM systems](https://docs.microsoft.com/azure/security/security-azure-log-integration-overview).</span></span>
    
- <span data-ttu-id="f6cb5-196">Office 365 Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="f6cb5-196">Office 365 Cloud App Security</span></span>
    
    <span data-ttu-id="f6cb5-197">詳細については、 [Office 365 のクラウド アプリケーションのセキュリティと SIEM サーバーの統合](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-197">For more information, see [Integrate your SIEM server with Office 365 Cloud App Security](https://support.office.com/article/dd6d2417-49c4-4de6-9294-67fdabbf8532).</span></span>
    
## <a name="next-step"></a><span data-ttu-id="f6cb5-198">次の手順</span><span class="sxs-lookup"><span data-stu-id="f6cb5-198">Next step</span></span>

<span data-ttu-id="f6cb5-199">[Office 365 のセキュリティのベスト プラクティス](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6cb5-199">See [Security best practices for Office 365](https://support.office.com/article/9295e396-e53d-49b9-ae9b-0b5828cdedc3).</span></span>
  

