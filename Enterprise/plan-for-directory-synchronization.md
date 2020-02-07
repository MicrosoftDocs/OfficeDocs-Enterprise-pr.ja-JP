---
title: Office 365 のハイブリッド id とディレクトリ同期
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.date: 05/20/2019
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Office 365、Active Directory ドメインサービスクリーンアップ、および Azure Active Directory Connect ツールとのディレクトリ同期について説明します。
ms.openlocfilehash: 5368fc00aafe66ed51af80c50aaf72ee5f939041
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841764"
---
# <a name="hybrid-identity-and-directory-synchronization-for-office-365"></a><span data-ttu-id="fc0f8-103">Office 365 のハイブリッド id とディレクトリ同期</span><span class="sxs-lookup"><span data-stu-id="fc0f8-103">Hybrid identity and directory synchronization for Office 365</span></span>

<span data-ttu-id="fc0f8-104">*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="fc0f8-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="fc0f8-105">Office 365 を採用している企業のお客様にとっては、ビジネスニーズおよび技術的な要件に応じて、ハイブリッド id モデルとディレクトリ同期が最も一般的に選択されています。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-105">Depending on business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Office 365.</span></span> <span data-ttu-id="fc0f8-106">ディレクトリ同期を使用すると、Active Directory ドメインサービス (AD DS) 内の id を管理できます。また、ユーザーアカウント、グループ、および連絡先へのすべての更新は、Office 365 サブスクリプションの Azure Active Directory (Azure AD) テナントに同期されます。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-106">Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS) and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="fc0f8-107">AD DS ユーザーアカウントが初めて同期されると、Office 365 ライセンスが自動的に割り当てられることはなく、電子メールなどの Office 365 サービスにアクセスすることもできません。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-107">When AD DS user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license and cannot access Office 365 services, such as email.</span></span> <span data-ttu-id="fc0f8-108">これらのユーザーアカウントには、グループメンバーシップを使用して個別に、または動的にライセンスを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-108">You must assign a license to these user accounts, either individually or dynamically through group membership.</span></span>
>

## <a name="authentication-for-hybrid-identity"></a><span data-ttu-id="fc0f8-109">ハイブリッド id の認証</span><span class="sxs-lookup"><span data-stu-id="fc0f8-109">Authentication for hybrid identity</span></span>

<span data-ttu-id="fc0f8-110">ハイブリッド id モデルを使用する場合は、次の2種類の認証があります。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-110">There are two types of authentication when using the hybrid identity model:</span></span>

- <span data-ttu-id="fc0f8-111">管理された認証</span><span class="sxs-lookup"><span data-stu-id="fc0f8-111">Managed authentication</span></span>

  <span data-ttu-id="fc0f8-112">Azure AD は、ローカルに保存されているハッシュバージョンのパスワードを使用して認証プロセスを処理するか、社内の AD DS によって認証されるように社内ソフトウェアエージェントに資格情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-112">Azure AD handles the authentication process by using a locally stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS.</span></span>

- <span data-ttu-id="fc0f8-113">フェデレーション認証</span><span class="sxs-lookup"><span data-stu-id="fc0f8-113">Federated authentication</span></span>

  <span data-ttu-id="fc0f8-114">Azure AD は、別の id プロバイダーに接続するための認証を要求しているクライアントコンピューターをリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-114">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

### <a name="managed-authentication"></a><span data-ttu-id="fc0f8-115">管理された認証</span><span class="sxs-lookup"><span data-stu-id="fc0f8-115">Managed authentication</span></span>

<span data-ttu-id="fc0f8-116">管理された認証には、次の2種類があります。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-116">There are two types of managed authentication:</span></span>

- <span data-ttu-id="fc0f8-117">パスワードハッシュの同期 (PHS)</span><span class="sxs-lookup"><span data-stu-id="fc0f8-117">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="fc0f8-118">Azure AD は認証自体を実行します。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-118">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="fc0f8-119">パススルー認証 (PTA)</span><span class="sxs-lookup"><span data-stu-id="fc0f8-119">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="fc0f8-120">Azure AD は、AD DS で認証を実行しています。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-120">Azure AD has AD DS perform the authentication.</span></span>


#### <a name="password-hash-synchronization"></a><span data-ttu-id="fc0f8-121">パスワード ハッシュ同期</span><span class="sxs-lookup"><span data-stu-id="fc0f8-121">Password hash synchronization</span></span>

<span data-ttu-id="fc0f8-122">パスワードハッシュ同期 (PHS) を使用すると、AD DS のユーザーアカウントを Office 365 と同期し、オンプレミスでユーザーを管理することができます。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-122">With password hash synchronization (PHS), you synchronize your AD DS user accounts with Office 365 and manage your users on-premises.</span></span> <span data-ttu-id="fc0f8-123">ユーザーパスワードのハッシュは AD DS から Azure AD に同期されるため、ユーザーは社内とクラウドの両方で同じパスワードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-123">Hashes of user passwords are synchronized from your AD DS to Azure AD so that the users have the same password on-premises and in the cloud.</span></span> <span data-ttu-id="fc0f8-124">これは、Azure AD で AD DS id の認証を有効にする最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-124">This is the simplest way to enable authentication for AD DS identities in Azure AD.</span></span> 

![パスワードハッシュの同期 (PHS)](./media/plan-for-directory-synchronization/phs-authentication.png)

<span data-ttu-id="fc0f8-126">パスワードが変更されるか、オンプレミスでリセットされると、新しいパスワードハッシュが Azure AD に同期されるため、ユーザーは常にクラウドリソースとオンプレミスのリソースに対して同じパスワードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-126">When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources.</span></span> <span data-ttu-id="fc0f8-127">ユーザーパスワードが Azure AD に送信されることや、クリアテキストで Azure AD に保存されることはありません。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-127">The user passwords are never sent to Azure AD or stored in Azure AD in clear text.</span></span> <span data-ttu-id="fc0f8-128">Id 保護などの Azure AD の一部のプレミアム機能は、どの認証方法が選択されているかに関係なく、PHS を必要とします。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-128">Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected.</span></span>
  
<span data-ttu-id="fc0f8-129">詳細については、「 [PHS の選択](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-129">See [choosing PHS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="pass-through-authentication"></a><span data-ttu-id="fc0f8-130">パススルー認証</span><span class="sxs-lookup"><span data-stu-id="fc0f8-130">Pass-through authentication</span></span>

<span data-ttu-id="fc0f8-131">パススルー認証 (PTA) は、1つまたは複数のオンプレミスサーバー上で実行されているソフトウェアエージェントを使用して、AD DS に直接ユーザーを検証することにより、Azure AD 認証サービスの簡単なパスワード検証を提供します。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-131">Pass-through authentication (PTA) provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> <span data-ttu-id="fc0f8-132">パススルー認証 (PTA) を使用して、AD DS のユーザーアカウントを Office 365 と同期し、オンプレミスでユーザーを管理します。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-132">With pass-through authentication (PTA), you synchronize AD DS user accounts with Office 365 and manage your users on-premises.</span></span> 

![パススルー認証 (PTA)](./media/plan-for-directory-synchronization/pta-authentication.png)

<span data-ttu-id="fc0f8-134">PTA を使用すると、ユーザーはオンプレミスのアカウントとパスワードを使用して、オンプレミスと Office 365 の両方のリソースとアプリケーションの両方にサインインできます。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-134">PTA allows your users to sign in to both on-premises and Office 365 resources and applications using their on-premises account and password.</span></span> <span data-ttu-id="fc0f8-135">この構成では、Azure AD にパスワードハッシュを保存せずに、ユーザーのパスワードをオンプレミスの AD DS に対して直接検証します。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-135">This configuration validates users passwords directly against your on-premises AD DS without storing password hashes in Azure AD.</span></span> 

<span data-ttu-id="fc0f8-136">PTA は、組織に対して、オンプレミスのユーザーアカウントの状態、パスワードポリシー、およびログオン時間を即時に適用するセキュリティ要件を持つ組織のためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-136">PTA is also for organizations with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours.</span></span> 
  
<span data-ttu-id="fc0f8-137">詳細については、「 [PTA の選択](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-137">See [choosing PTA](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="fc0f8-138">フェデレーション認証</span><span class="sxs-lookup"><span data-stu-id="fc0f8-138">Federated authentication</span></span>

<span data-ttu-id="fc0f8-139">フェデレーション認証は、主に、より複雑な認証要件を持つ大規模なエンタープライズ組織に適しています。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-139">Federated authentication is primarily for large enterprise organizations with more complex authentication requirements.</span></span> <span data-ttu-id="fc0f8-140">AD DS id は Office 365 と同期され、ユーザーアカウントは社内で管理されます。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-140">AD DS identities are synchronized with Office 365 and users accounts are managed on-premises.</span></span> <span data-ttu-id="fc0f8-141">フェデレーション認証では、ユーザーは社内とクラウドの両方で同じパスワードを使用しており、Office 365 を使用するために再度サインインする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-141">With federated authentication, users have the same password on-premises and in the cloud and they do not have to sign in again to use Office 365.</span></span> 

<span data-ttu-id="fc0f8-142">フェデレーション認証は、スマートカードベースの認証、またはサードパーティの多要素認証などの追加の認証要件をサポートでき、組織が認証要件を持たない場合に通常は必要です。Azure AD でネイティブにサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-142">Federated authentication can support additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
 
<span data-ttu-id="fc0f8-143">詳細については、「[フェデレーション認証の選択](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-143">See [choosing federated authentication](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) to learn more.</span></span>
  
#### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="fc0f8-144">サードパーティの認証および id プロバイダー</span><span class="sxs-lookup"><span data-stu-id="fc0f8-144">Third-party authentication and identity providers</span></span>

<span data-ttu-id="fc0f8-145">オンプレミスのディレクトリオブジェクトは Office 365 に同期され、クラウドリソースアクセスは主にサードパーティの id プロバイダー (IdP) によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-145">On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> <span data-ttu-id="fc0f8-146">組織でサードパーティのフェデレーションソリューションを使用している場合は、サードパーティ製のフェデレーションソリューションが Azure AD と互換性があることを前提として、Office 365 でそのソリューションを使用してサインオンを構成できます。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-146">If your organization uses a third-party federation solution, you can configure sign-on with that solution for Office 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="fc0f8-147">詳細については、「 [AZURE AD フェデレーション互換性](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-147">See [Azure AD federation compatibility](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) to learn more.</span></span>
  
## <a name="ad-ds-cleanup"></a><span data-ttu-id="fc0f8-148">AD DS のクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="fc0f8-148">AD DS Cleanup</span></span>

<span data-ttu-id="fc0f8-149">同期を使用して Office 365 をシームレスに移行できるようにするには、Office 365 ディレクトリ同期の展開を開始する前に、AD DS フォレストを準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-149">To help ensure a seamless transition to Office 365 by using synchronization, you must prepare your AD DS forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="fc0f8-150">[Office 365 でディレクトリ同期](set-up-directory-synchronization.md)をセットアップする場合の手順の1つとして、 [idfix ツールをダウンロードして実行](install-and-run-idfix.md)する方法があります。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-150">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="fc0f8-151">IdFix ツールを使用して、ディレクトリの[クリーンアップ](prepare-directory-attributes-for-synch-with-idfix.md)に役立てることができます。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-151">You can use the IdFix tool to help with [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="fc0f8-152">ディレクトリのクリーンアップでは、次のタスクに焦点を当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-152">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="fc0f8-153">重複している**proxyAddress**属性と**userPrincipalName**属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-153">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="fc0f8-154">空白および無効な**userprincipalname**属性を有効な**userprincipalname**属性で更新します。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-154">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="fc0f8-155">**GivenName**、姓 ( **Sn** )、 **sAMAccountName**、 **displayName**、 **mail**、 **proxyAddresses**、 **mailNickname**、および**userPrincipalName**の各属性の無効で問題のある文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-155">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="fc0f8-156">属性の準備の詳細については、「 [Azure Active Directory 同期ツールによって同期される属性の一覧](https://go.microsoft.com/fwlink/p/?LinkId=396719)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-156">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="fc0f8-157">Azure AD Connect が同期するのと同じ属性です。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-157">These are the same attributes that Azure AD Connect synchronizes.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="fc0f8-158">複数フォレストの展開に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="fc0f8-158">Multi-forest deployment considerations</span></span>

<span data-ttu-id="fc0f8-159">複数のフォレストおよび SSO オプションでは、 [AZURE AD Connect のカスタムインストール](https://go.microsoft.com/fwlink/p/?LinkId=698430)を使用します。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-159">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="fc0f8-160">組織に認証用に複数のフォレストがある場合 (ログオンフォレスト)、次のことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-160">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="fc0f8-161">**フォレストを統合することを検討してください。**</span><span class="sxs-lookup"><span data-stu-id="fc0f8-161">**Consider consolidating your forests.**</span></span> <span data-ttu-id="fc0f8-162">一般に、複数のフォレストを維持するには、より多くのオーバーヘッドが必要になります。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-162">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="fc0f8-163">個別のフォレストの必要性を判断するセキュリティ上の制約が組織にない限り、オンプレミスの環境を簡素化することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-163">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="fc0f8-164">**プライマリのログオンフォレストでのみ使用します。**</span><span class="sxs-lookup"><span data-stu-id="fc0f8-164">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="fc0f8-165">Office 365 を最初に展開する場合は、プライマリのログオンフォレストにのみ Office 365 を展開することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-165">Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 

<span data-ttu-id="fc0f8-166">複数フォレストの AD DS 展開を統合できない場合や、他のディレクトリサービスを使用して id を管理している場合は、Microsoft またはパートナーのヘルプと同期することができます。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-166">If you can't consolidate your multi-forest AD DS deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="fc0f8-167">詳細については、「[シングルサインオンシナリオでのマルチフォレストディレクトリ同期](https://go.microsoft.com/fwlink/p/?LinkId=525321)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-167">See [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321) for more information.</span></span>
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a><span data-ttu-id="fc0f8-168">ディレクトリ同期に依存する機能</span><span class="sxs-lookup"><span data-stu-id="fc0f8-168">Features that are dependent on directory synchronization</span></span>
  
<span data-ttu-id="fc0f8-169">次の機能には、ディレクトリ同期が必要です。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-169">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="fc0f8-170">Azure AD のシームレスなシングルサインオン (SSO)</span><span class="sxs-lookup"><span data-stu-id="fc0f8-170">Azure AD Seamless Single Sign-On (SSO)</span></span>
- <span data-ttu-id="fc0f8-171">Skype の共存</span><span class="sxs-lookup"><span data-stu-id="fc0f8-171">Skype coexistence</span></span>
- <span data-ttu-id="fc0f8-172">Exchange ハイブリッド展開 (次のものが含まれる)</span><span class="sxs-lookup"><span data-stu-id="fc0f8-172">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="fc0f8-173">オンプレミスの Exchange 環境と Office 365 間の完全に共有されたグローバルアドレス一覧 (GAL)。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-173">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="fc0f8-174">別のメールシステムから GAL 情報を同期します。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-174">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="fc0f8-175">Office 365 サービスオファーリングにユーザーを追加したり、ユーザーを削除したりする機能。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-175">The ability to add users to and remove users from Office 365 service offerings.</span></span> <span data-ttu-id="fc0f8-176">これには、次のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-176">This requires the following:</span></span>
  - <span data-ttu-id="fc0f8-177">ディレクトリ同期のセットアップ中に、双ウェイの同期を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-177">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="fc0f8-178">既定では、ディレクトリ同期ツールは、ディレクトリ情報をクラウドにのみ書き込みます。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-178">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="fc0f8-179">双ウェイの同期を構成する場合は、制限された数のオブジェクト属性がクラウドからコピーされるように書き戻し機能を有効にしてから、ローカルの AD DS に書き戻します。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-179">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local AD DS.</span></span> <span data-ttu-id="fc0f8-180">書き戻しは、Exchange ハイブリッドモードとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-180">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="fc0f8-181">オンプレミスの Exchange ハイブリッド展開</span><span class="sxs-lookup"><span data-stu-id="fc0f8-181">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="fc0f8-182">他のユーザーのメールボックスをオンプレミスに保持したまま、一部のユーザーメールボックスを Office 365 に移動する機能。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-182">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="fc0f8-183">社内の信頼できる差出人と受信拒否リストは、Office 365 に複製されます。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-183">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="fc0f8-184">基本的な委任および代理送信電子メール機能。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-184">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="fc0f8-185">オンプレミスのスマートカードまたは多要素認証ソリューションが統合されている。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-185">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="fc0f8-186">写真、サムネイル、会議室、セキュリティグループの同期</span><span class="sxs-lookup"><span data-stu-id="fc0f8-186">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>

## <a name="next-step"></a><span data-ttu-id="fc0f8-187">次の手順</span><span class="sxs-lookup"><span data-stu-id="fc0f8-187">Next step</span></span>

<span data-ttu-id="fc0f8-188">ハイブリッド id を展開する準備ができたら、「[ユーザーをプロビジョニングするための準備](prepare-for-directory-synchronization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc0f8-188">When you are ready to deploy hybrid identity, see [prepare to provision users](prepare-for-directory-synchronization.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fc0f8-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc0f8-189">See also</span></span>

[<span data-ttu-id="fc0f8-190">Microsoft 365 Enterprise の概要</span><span class="sxs-lookup"><span data-stu-id="fc0f8-190">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)

