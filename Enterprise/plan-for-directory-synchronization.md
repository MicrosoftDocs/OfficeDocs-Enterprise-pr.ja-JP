---
title: Microsoft 365 のハイブリッド id とディレクトリ同期
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.date: 06/09/2020
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
description: Microsoft 365、Active Directory ドメインサービスクリーンアップ、および Azure Active Directory Connect ツールとのディレクトリ同期について説明します。
ms.openlocfilehash: 8bfb9a7d65bf76fdadafe1bb49da91115ee9d07c
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571160"
---
# <a name="hybrid-identity-and-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="67f9d-103">Microsoft 365 のハイブリッド id とディレクトリ同期</span><span class="sxs-lookup"><span data-stu-id="67f9d-103">Hybrid identity and directory synchronization for Microsoft 365</span></span>

<span data-ttu-id="67f9d-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="67f9d-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="67f9d-105">ビジネスニーズおよび技術的な要件に応じて、ハイブリッド id モデルおよびディレクトリ同期は、Microsoft 365 を採用しているエンタープライズのお客様にとって最も一般的な選択です。</span><span class="sxs-lookup"><span data-stu-id="67f9d-105">Depending on your business needs and technical requirements, the hybrid identity model and directory synchronization is the most common choice for enterprise customers who are adopting Microsoft 365.</span></span> <span data-ttu-id="67f9d-106">ディレクトリ同期を使用すると、Active Directory ドメインサービス (AD DS) 内の id を管理でき、ユーザーアカウント、グループ、および連絡先へのすべての更新は、Microsoft 365 サブスクリプションの Azure Active Directory (Azure AD) テナントに同期されます。</span><span class="sxs-lookup"><span data-stu-id="67f9d-106">Directory synchronization allows you to manage identities in your Active Directory Domain Services (AD DS) and all updates to user accounts, groups, and contacts are synchronized to the Azure Active Directory (Azure AD) tenant of your Microsoft 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="67f9d-107">AD DS ユーザーアカウントが初めて同期されると、Microsoft 365 ライセンスが自動的に割り当てられることはなく、電子メールなどの Microsoft 365 サービスにアクセスすることもできません。</span><span class="sxs-lookup"><span data-stu-id="67f9d-107">When AD DS user accounts are synchronized for the first time, they are not automatically assigned a Microsoft 365 license and cannot access Microsoft 365 services, such as email.</span></span> <span data-ttu-id="67f9d-108">最初に利用状況の場所を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="67f9d-108">You must first assign them a usage location.</span></span> <span data-ttu-id="67f9d-109">次に、グループメンバーシップを使用して、個別または動的にライセンスをこれらのユーザーアカウントに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="67f9d-109">Then, assign a license to these user accounts, either individually or dynamically through group membership.</span></span>
>

## <a name="authentication-for-hybrid-identity"></a><span data-ttu-id="67f9d-110">ハイブリッド id の認証</span><span class="sxs-lookup"><span data-stu-id="67f9d-110">Authentication for hybrid identity</span></span>

<span data-ttu-id="67f9d-111">ハイブリッド id モデルを使用する場合は、次の2種類の認証があります。</span><span class="sxs-lookup"><span data-stu-id="67f9d-111">There are two types of authentication when using the hybrid identity model:</span></span>

- <span data-ttu-id="67f9d-112">管理された認証</span><span class="sxs-lookup"><span data-stu-id="67f9d-112">Managed authentication</span></span>

  <span data-ttu-id="67f9d-113">Azure AD は、ローカルに保存されたハッシュバージョンのパスワードを使用して認証プロセスを処理するか、社内の AD DS によって認証されるように社内ソフトウェアエージェントに資格情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="67f9d-113">Azure AD handles the authentication process by using a locally-stored hashed version of the password or sends the credentials to an on-premises software agent to be authenticated by the on-premises AD DS.</span></span>

- <span data-ttu-id="67f9d-114">フェデレーション認証</span><span class="sxs-lookup"><span data-stu-id="67f9d-114">Federated authentication</span></span>

  <span data-ttu-id="67f9d-115">Azure AD は、認証を要求しているクライアントコンピューターを別の id プロバイダーにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="67f9d-115">Azure AD redirects the client computer requesting authentication to another identity provider.</span></span>

### <a name="managed-authentication"></a><span data-ttu-id="67f9d-116">管理された認証</span><span class="sxs-lookup"><span data-stu-id="67f9d-116">Managed authentication</span></span>

<span data-ttu-id="67f9d-117">管理された認証には、次の2種類があります。</span><span class="sxs-lookup"><span data-stu-id="67f9d-117">There are two types of managed authentication:</span></span>

- <span data-ttu-id="67f9d-118">パスワードハッシュの同期 (PHS)</span><span class="sxs-lookup"><span data-stu-id="67f9d-118">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="67f9d-119">Azure AD は認証自体を実行します。</span><span class="sxs-lookup"><span data-stu-id="67f9d-119">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="67f9d-120">パススルー認証 (PTA)</span><span class="sxs-lookup"><span data-stu-id="67f9d-120">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="67f9d-121">Azure AD は、AD DS で認証を実行しています。</span><span class="sxs-lookup"><span data-stu-id="67f9d-121">Azure AD has AD DS perform the authentication.</span></span>


#### <a name="password-hash-synchronization-phs"></a><span data-ttu-id="67f9d-122">パスワードハッシュの同期 (PHS)</span><span class="sxs-lookup"><span data-stu-id="67f9d-122">Password hash synchronization (PHS)</span></span>

<span data-ttu-id="67f9d-123">PHS では、AD DS のユーザーアカウントを Microsoft 365 と同期し、オンプレミスでユーザーを管理します。</span><span class="sxs-lookup"><span data-stu-id="67f9d-123">With PHS, you synchronize your AD DS user accounts with Microsoft 365 and manage your users on-premises.</span></span> <span data-ttu-id="67f9d-124">ユーザーパスワードのハッシュは AD DS から Azure AD に同期されるため、ユーザーは社内とクラウドの両方で同じパスワードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="67f9d-124">Hashes of user passwords are synchronized from your AD DS to Azure AD so that the users have the same password on-premises and in the cloud.</span></span> <span data-ttu-id="67f9d-125">これは、Azure AD で AD DS id の認証を有効にする最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="67f9d-125">This is the simplest way to enable authentication for AD DS identities in Azure AD.</span></span> 

![パスワードハッシュの同期 (PHS)](./media/plan-for-directory-synchronization/phs-authentication.png)

<span data-ttu-id="67f9d-127">パスワードが変更されるか、オンプレミスでリセットされると、新しいパスワードハッシュが Azure AD に同期されるため、ユーザーは常にクラウドリソースとオンプレミスのリソースに対して同じパスワードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="67f9d-127">When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources.</span></span> <span data-ttu-id="67f9d-128">ユーザーパスワードが Azure AD に送信されることや、クリアテキストで Azure AD に保存されることはありません。</span><span class="sxs-lookup"><span data-stu-id="67f9d-128">The user passwords are never sent to Azure AD or stored in Azure AD in clear text.</span></span> <span data-ttu-id="67f9d-129">Id 保護などの Azure AD の一部のプレミアム機能は、どの認証方法が選択されているかに関係なく、PHS を必要とします。</span><span class="sxs-lookup"><span data-stu-id="67f9d-129">Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected.</span></span>
  
<span data-ttu-id="67f9d-130">詳細について[は、「適切な認証方法を選択](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67f9d-130">See [choosing the right authentication method](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
#### <a name="pass-through-authentication-pta"></a><span data-ttu-id="67f9d-131">パススルー認証 (PTA)</span><span class="sxs-lookup"><span data-stu-id="67f9d-131">Pass-through authentication (PTA)</span></span>

<span data-ttu-id="67f9d-132">PTA は、1つまたは複数のオンプレミスサーバー上で実行されているソフトウェアエージェントを使用して、AD DS に直接ユーザーを検証することにより、Azure AD 認証サービスの簡単なパスワード検証を提供します。</span><span class="sxs-lookup"><span data-stu-id="67f9d-132">PTA provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> <span data-ttu-id="67f9d-133">PTA を使用すると、AD DS のユーザーアカウントを Microsoft 365 と同期し、オンプレミスでユーザーを管理することができます。</span><span class="sxs-lookup"><span data-stu-id="67f9d-133">With PTA, you synchronize AD DS user accounts with Microsoft 365 and manage your users on-premises.</span></span> 

![パススルー認証 (PTA)](./media/plan-for-directory-synchronization/pta-authentication.png)

<span data-ttu-id="67f9d-135">PTA を使用すると、ユーザーはオンプレミスのアカウントとパスワードを使用して、オンプレミスと Microsoft 365 の両方のリソースとアプリケーションの両方にサインインできるようになります。</span><span class="sxs-lookup"><span data-stu-id="67f9d-135">PTA allows your users to sign in to both on-premises and Microsoft 365 resources and applications using their on-premises account and password.</span></span> <span data-ttu-id="67f9d-136">この構成では、Azure AD にパスワードハッシュを保存せずに、ユーザーのパスワードをオンプレミスの AD DS に対して直接検証します。</span><span class="sxs-lookup"><span data-stu-id="67f9d-136">This configuration validates users passwords directly against your on-premises AD DS without storing password hashes in Azure AD.</span></span> 

<span data-ttu-id="67f9d-137">PTA は、組織に対して、オンプレミスのユーザーアカウントの状態、パスワードポリシー、およびログオン時間を即時に適用するセキュリティ要件を持つ組織のためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="67f9d-137">PTA is also for organizations with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours.</span></span> 
  
<span data-ttu-id="67f9d-138">詳細について[は、「適切な認証方法を選択](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67f9d-138">See [choosing the right authentication method](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="67f9d-139">フェデレーション認証</span><span class="sxs-lookup"><span data-stu-id="67f9d-139">Federated authentication</span></span>

<span data-ttu-id="67f9d-140">フェデレーション認証は、主に、より複雑な認証要件を持つ大規模なエンタープライズ組織に適しています。</span><span class="sxs-lookup"><span data-stu-id="67f9d-140">Federated authentication is primarily for large enterprise organizations with more complex authentication requirements.</span></span> <span data-ttu-id="67f9d-141">AD DS id は Microsoft 365 と同期され、ユーザーアカウントは社内で管理されます。</span><span class="sxs-lookup"><span data-stu-id="67f9d-141">AD DS identities are synchronized with Microsoft 365 and users accounts are managed on-premises.</span></span> <span data-ttu-id="67f9d-142">フェデレーション認証では、ユーザーは社内とクラウドの両方で同じパスワードを使用しており、Microsoft 365 を使用するために再度サインインする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="67f9d-142">With federated authentication, users have the same password on-premises and in the cloud and they do not have to sign in again to use Microsoft 365.</span></span> 

<span data-ttu-id="67f9d-143">フェデレーション認証は、スマートカードベースの認証、またはサードパーティの多要素認証などの追加の認証要件をサポートしており、一般に、組織が Azure AD でネイティブにサポートされていない認証要件を使用する場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="67f9d-143">Federated authentication can support additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
 
<span data-ttu-id="67f9d-144">詳細について[は、「適切な認証方法を選択](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67f9d-144">See [choosing the right authentication method](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) to learn more.</span></span>
  
#### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="67f9d-145">サードパーティの認証および id プロバイダー</span><span class="sxs-lookup"><span data-stu-id="67f9d-145">Third-party authentication and identity providers</span></span>

<span data-ttu-id="67f9d-146">オンプレミスのディレクトリオブジェクトは、Microsoft 365 に同期することができ、クラウドリソースアクセスは主にサードパーティの id プロバイダー (IdP) によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="67f9d-146">On-premises directory objects may be synchronized to Microsoft 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> <span data-ttu-id="67f9d-147">組織でサードパーティのフェデレーションソリューションを使用している場合は、Microsoft 365 でそのソリューションを使用してサインオンを構成することができます。これにより、サードパーティ製のフェデレーションソリューションが Azure AD と互換性があることが提供されます。</span><span class="sxs-lookup"><span data-stu-id="67f9d-147">If your organization uses a third-party federation solution, you can configure sign-on with that solution for Microsoft 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="67f9d-148">詳細については、「 [AZURE AD フェデレーション互換性リスト](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67f9d-148">See the [Azure AD federation compatibility list](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) to learn more.</span></span>
  
## <a name="ad-ds-preparation"></a><span data-ttu-id="67f9d-149">AD DS の準備</span><span class="sxs-lookup"><span data-stu-id="67f9d-149">AD DS Preparation</span></span>

<span data-ttu-id="67f9d-150">同期を使用して Microsoft 365 にシームレスに移行できるようにするには、Microsoft 365 ディレクトリ同期の展開を開始する前に、AD DS フォレストを準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67f9d-150">To help ensure a seamless transition to Microsoft 365 by using synchronization, you must prepare your AD DS forest before you begin your Microsoft 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="67f9d-151">ディレクトリの準備では、次のタスクに焦点を当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="67f9d-151">Your directory preparation should focus on the following tasks:</span></span>

- <span data-ttu-id="67f9d-152">重複している**proxyAddress**属性と**userPrincipalName**属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="67f9d-152">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="67f9d-153">空白および無効な**userprincipalname**属性を有効な**userprincipalname**属性で更新します。</span><span class="sxs-lookup"><span data-stu-id="67f9d-153">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="67f9d-154">**GivenName**、姓 ( **Sn** )、 **sAMAccountName**、 **displayName**、 **mail**、 **proxyAddresses**、 **mailNickname**、および**userPrincipalName**の各属性の無効で問題のある文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="67f9d-154">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="67f9d-155">属性の準備の詳細については、「 [Azure Active Directory 同期ツールによって同期される属性の一覧](https://go.microsoft.com/fwlink/p/?LinkId=396719)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67f9d-155">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="67f9d-156">Azure AD Connect が同期するのと同じ属性です。</span><span class="sxs-lookup"><span data-stu-id="67f9d-156">These are the same attributes that Azure AD Connect synchronizes.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="67f9d-157">複数フォレストの展開に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="67f9d-157">Multi-forest deployment considerations</span></span>

<span data-ttu-id="67f9d-158">複数のフォレストおよび SSO オプションの場合は、 [AZURE AD Connect のカスタムインストール](https://go.microsoft.com/fwlink/p/?LinkId=698430)を使用します。</span><span class="sxs-lookup"><span data-stu-id="67f9d-158">For multiple forests and SSO options, use a [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="67f9d-159">組織に認証用に複数のフォレストがある場合 (ログオンフォレスト)、次のことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="67f9d-159">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="67f9d-160">**フォレストを統合することを検討してください。**</span><span class="sxs-lookup"><span data-stu-id="67f9d-160">**Consider consolidating your forests.**</span></span> <span data-ttu-id="67f9d-161">一般に、複数のフォレストを維持するには、より多くのオーバーヘッドが必要になります。</span><span class="sxs-lookup"><span data-stu-id="67f9d-161">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="67f9d-162">個別のフォレストの必要性を判断するセキュリティ上の制約が組織にない限り、オンプレミスの環境を簡素化することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="67f9d-162">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="67f9d-163">**プライマリのログオンフォレストでのみ使用します。**</span><span class="sxs-lookup"><span data-stu-id="67f9d-163">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="67f9d-164">Microsoft 365 の展開は、Microsoft 365 の初期の展開にプライマリのログオンフォレストでのみ行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="67f9d-164">Consider deploying Microsoft 365 only in your primary logon forest for your initial rollout of Microsoft 365.</span></span> 

<span data-ttu-id="67f9d-165">複数フォレストの AD DS 展開を統合できない場合や、他のディレクトリサービスを使用して id を管理している場合は、Microsoft またはパートナーのヘルプと同期することができます。</span><span class="sxs-lookup"><span data-stu-id="67f9d-165">If you can't consolidate your multi-forest AD DS deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="67f9d-166">詳細については、「 [AZURE AD Connect のトポロジ](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-topologies)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67f9d-166">See [Topologies for Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-topologies) for more information.</span></span>
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a><span data-ttu-id="67f9d-167">ディレクトリ同期に依存する機能</span><span class="sxs-lookup"><span data-stu-id="67f9d-167">Features that are dependent on directory synchronization</span></span>
  
<span data-ttu-id="67f9d-168">次の機能には、ディレクトリ同期が必要です。</span><span class="sxs-lookup"><span data-stu-id="67f9d-168">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="67f9d-169">Azure AD のシームレスなシングルサインオン (SSO)</span><span class="sxs-lookup"><span data-stu-id="67f9d-169">Azure AD Seamless Single Sign-On (SSO)</span></span>
- <span data-ttu-id="67f9d-170">Skype の共存</span><span class="sxs-lookup"><span data-stu-id="67f9d-170">Skype coexistence</span></span>
- <span data-ttu-id="67f9d-171">Exchange ハイブリッド展開 (次のものが含まれる)</span><span class="sxs-lookup"><span data-stu-id="67f9d-171">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="67f9d-172">オンプレミスの Exchange 環境と Microsoft 365 間の完全に共有されたグローバルアドレス一覧 (GAL)。</span><span class="sxs-lookup"><span data-stu-id="67f9d-172">Fully shared global address list (GAL) between your on-premises Exchange environment and Microsoft 365.</span></span>
  - <span data-ttu-id="67f9d-173">別のメールシステムから GAL 情報を同期します。</span><span class="sxs-lookup"><span data-stu-id="67f9d-173">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="67f9d-174">Microsoft 365 サービスオファーリングにユーザーを追加したり、ユーザーを削除したりする機能。</span><span class="sxs-lookup"><span data-stu-id="67f9d-174">The ability to add users to and remove users from Microsoft 365 service offerings.</span></span> <span data-ttu-id="67f9d-175">これには、次のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="67f9d-175">This requires the following:</span></span>
  - <span data-ttu-id="67f9d-176">ディレクトリ同期のセットアップ中に、双ウェイの同期を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67f9d-176">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="67f9d-177">既定では、ディレクトリ同期ツールは、ディレクトリ情報をクラウドにのみ書き込みます。</span><span class="sxs-lookup"><span data-stu-id="67f9d-177">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="67f9d-178">双ウェイの同期を構成する場合は、制限された数のオブジェクト属性がクラウドからコピーされるように書き戻し機能を有効にしてから、ローカルの AD DS に書き戻します。</span><span class="sxs-lookup"><span data-stu-id="67f9d-178">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local AD DS.</span></span> <span data-ttu-id="67f9d-179">書き戻しは、Exchange ハイブリッドモードとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="67f9d-179">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="67f9d-180">オンプレミスの Exchange ハイブリッド展開</span><span class="sxs-lookup"><span data-stu-id="67f9d-180">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="67f9d-181">他のユーザーのメールボックスをオンプレミスに保持したまま、一部のユーザーメールボックスを Microsoft 365 に移動する機能。</span><span class="sxs-lookup"><span data-stu-id="67f9d-181">The ability to move some user mailboxes to Microsoft 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="67f9d-182">オンプレミスの信頼できる差出人と受信拒否リストは、Microsoft 365 に複製されます。</span><span class="sxs-lookup"><span data-stu-id="67f9d-182">Safe senders and blocked senders on-premises are replicated to Microsoft 365.</span></span>
  - <span data-ttu-id="67f9d-183">基本的な委任および代理送信電子メール機能。</span><span class="sxs-lookup"><span data-stu-id="67f9d-183">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="67f9d-184">オンプレミスのスマートカードまたは多要素認証ソリューションが統合されている。</span><span class="sxs-lookup"><span data-stu-id="67f9d-184">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="67f9d-185">写真、サムネイル、会議室、セキュリティグループの同期</span><span class="sxs-lookup"><span data-stu-id="67f9d-185">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>

## <a name="next-step"></a><span data-ttu-id="67f9d-186">次の手順</span><span class="sxs-lookup"><span data-stu-id="67f9d-186">Next step</span></span>

<span data-ttu-id="67f9d-187">ハイブリッド id を展開する準備ができたら、「[ユーザーをプロビジョニングするための準備](prepare-for-directory-synchronization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67f9d-187">When you are ready to deploy hybrid identity, see [prepare to provision users](prepare-for-directory-synchronization.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="67f9d-188">関連項目</span><span class="sxs-lookup"><span data-stu-id="67f9d-188">See also</span></span>

[<span data-ttu-id="67f9d-189">Microsoft 365 Enterprise の概要</span><span class="sxs-lookup"><span data-stu-id="67f9d-189">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)

