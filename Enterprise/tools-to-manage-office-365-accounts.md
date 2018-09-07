---
title: Office 365 アカウントを管理するツール
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: '使用して、Office 365 のユーザーとユーザーの id を管理する方法に依存して使用することができる方法を管理するには、どのようなツールについて説明します。 '
ms.openlocfilehash: 62467fb031090a521d0b9e067582b56fabe9e5fd
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541580"
---
# <a name="tools-to-manage-office-365-accounts"></a><span data-ttu-id="140f4-103">Office 365 アカウントを管理するツール</span><span class="sxs-lookup"><span data-stu-id="140f4-103">Tools to manage Office 365 accounts</span></span>

<span data-ttu-id="140f4-p101">構成によって、さまざまな方法で Office 365 のユーザーを管理できます。Office 365 管理センターで、Windows PowerShell では、設置型、ディレクトリ、または Active Directory の Azure 管理ポータルでユーザーを管理することができます。</span><span class="sxs-lookup"><span data-stu-id="140f4-p101">You can manage Office 365 users in several different ways, depending on your configuration. You can manage users in the Office 365 admin center, Windows PowerShell, your on-premises directory, or in Azure Active Directory admin portal.</span></span> 

<span data-ttu-id="140f4-p102">Office 365 を購入するとすぐに、管理センターと Windows PowerShell は、アカウントを管理するために使用できます。クラウド id を管理する場合、組織内のすべての人は、個別のユーザー ID とパスワード Office 365 のです。オンプレミス インフラストラクチャと統合し、ユーザー アカウントが存在する場合は、Office 365 と同期して、使用できます Azure Active Directory の接続 id の同期を提供し、必要に応じてパスワード同期を提供したり、完全なシングル サインオン機能します。</span><span class="sxs-lookup"><span data-stu-id="140f4-p102">As soon as you purchase Office 365, the admin center and Windows PowerShell can be used to manage accounts. When managing cloud identities every person in your organization has a separate user ID and password for Office 365. If you want to integrate with your on-premises infrastructure and have user accounts synchronized with Office 365, you can use Azure Active Directory Connect to provide synchronization of identities and optionally provide password synchronization, or full single sign-on functionality.</span></span>
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a><span data-ttu-id="140f4-109">ユーザー アカウントを管理する場所と方法の計画</span><span class="sxs-lookup"><span data-stu-id="140f4-109">Plan for where and how you will manage your user accounts</span></span>

<span data-ttu-id="140f4-p103">ユーザー アカウントを管理することができます場所や方法は、Office 365 を使用する識別情報モデルによって異なります。2 つの全体的なモデルは、クラウドの認証と統合認証です。</span><span class="sxs-lookup"><span data-stu-id="140f4-p103">Where and how you can manage your user accounts depends on the identity model you want to use for your Office 365. The two overall models are cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="140f4-112">クラウドの認証</span><span class="sxs-lookup"><span data-stu-id="140f4-112">Cloud authentication</span></span>

<span data-ttu-id="140f4-113"><<<<<<< 見出し</span><span class="sxs-lookup"><span data-stu-id="140f4-113"><<<<<<< HEAD</span></span>
- <span data-ttu-id="140f4-114">[クラウド認証](about-office-365-identity.md#cloud-authentication)- を作成し、Office 365 の管理センターでユーザーの管理、ユーザーを管理するために、Windows PowerShell、または Active Directory の Azure を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="140f4-114">[Cloud authentication](about-office-365-identity.md#cloud-authentication) - create and manage users in the Office 365 admin center, you can also use Windows PowerShell, or Azure Active Directory to manage your users.</span></span> 
    
=======
- <span data-ttu-id="140f4-115">[Office 365 の Id](about-office-365-identity.md)を作成し、Office 365 の管理センターでユーザーの管理、ユーザーを管理するために、Windows PowerShell、または Active Directory の Azure を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="140f4-115">[Office 365 Identity](about-office-365-identity.md) - create and manage users in the Office 365 admin center, you can also use Windows PowerShell, or Azure Active Directory to manage your users.</span></span>
>>>>>>> <span data-ttu-id="140f4-116">robmazz 変換</span><span class="sxs-lookup"><span data-stu-id="140f4-116">robmazz-conversion</span></span>
- <span data-ttu-id="140f4-p104">[シームレスなシングル サインオンとパスワードのハッシュが同期](about-office-365-identity.md)の Azure AD で設置ディレクトリ オブジェクトの認証を有効にする簡単な方法です。パスワード ハッシュ (PHS)、同期に、オンプレミスの Active Directory ユーザー アカウント オブジェクトを Office 365 と同期して、ユーザーの設置型の管理します。</span><span class="sxs-lookup"><span data-stu-id="140f4-p104">[Password hash sync with seamless single sign-on](about-office-365-identity.md) - The simplest way to enable authentication for on-premises directory objects in Azure AD. With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises.</span></span> 
- <span data-ttu-id="140f4-119">Azure AD の認証サービスと直接ユーザーを検証するためにソフトウェア エージェントは、1 つまたは複数のオンプレミスのサーバーで実行されているを使用して単純なパスワードの検証を提供する[シームレスなシングル サインオンでのパススルー認証](about-office-365-identity.md)が、Active Directory を設置します。</span><span class="sxs-lookup"><span data-stu-id="140f4-119">[Pass-through authentication with seamless single sign-on](about-office-365-identity.md) - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory.</span></span> 
    
### <a name="federated-authentication"></a><span data-ttu-id="140f4-120">フェデレーション認証</span><span class="sxs-lookup"><span data-stu-id="140f4-120">Federated authentication</span></span>

<span data-ttu-id="140f4-121"><<<<<<< 見出し</span><span class="sxs-lookup"><span data-stu-id="140f4-121"><<<<<<< HEAD</span></span>
- <span data-ttu-id="140f4-122">[シームレスなシングル サインオンでのパススルー認証](about-office-365-identity.md#pass-through-authentication-with-seamless-single-sign-on)をより複雑な認証の要件を持つ大規模な企業組織を主に設置型のディレクトリ オブジェクトは、Office 365 と同期し、ユーザー アカウントを管理設置します。</span><span class="sxs-lookup"><span data-stu-id="140f4-122">[Pass-through authentication with seamless single sign-on](about-office-365-identity.md#pass-through-authentication-with-seamless-single-sign-on) - Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises.</span></span> 
    
=======
- <span data-ttu-id="140f4-123">[Office 365 の Id](about-office-365-identity.md)でさらに複雑な認証の要件を持つ大規模な企業組織の主な設置ディレクトリ オブジェクトは、Office 365 と同期され、ユーザー アカウントは、管理対象の設置型です。</span><span class="sxs-lookup"><span data-stu-id="140f4-123">[Office 365 Identity](about-office-365-identity.md) - Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises.</span></span> 
>>>>>>> <span data-ttu-id="140f4-124">robmazz 変換</span><span class="sxs-lookup"><span data-stu-id="140f4-124">robmazz-conversion</span></span>
- <span data-ttu-id="140f4-125">[サード ・ パーティ製の認証と id プロバイダー](about-office-365-identity.md)の設置型のディレクトリ オブジェクトが Office 365 に同期させることがあり、クラウドのリソースへのアクセスは、主にサードパーティの id プロバイダー (IdP) によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="140f4-125">[Third-party authentication and identity providers](about-office-365-identity.md) - On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> 
    
## <a name="managing-accounts"></a><span data-ttu-id="140f4-126">アカウントを管理します。</span><span class="sxs-lookup"><span data-stu-id="140f4-126">Managing Accounts</span></span>

<span data-ttu-id="140f4-127">組織は作成され、アカウントの管理方法を決定するときは、以下を考慮します。</span><span class="sxs-lookup"><span data-stu-id="140f4-127">When deciding which way your organization will create and manage accounts, consider the following:</span></span>
  
- <span data-ttu-id="140f4-128">ディレクトリ同期ソフトウェアは、Office 365 との設置ディレクトリとの間の id を接続するのには、オンプレミス環境でサーバーにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="140f4-128">The directory synchronization software needs to be installed on servers within your on-premises environment to connect the identities between Office 365 and your on-premises directory.</span></span>
- <span data-ttu-id="140f4-p105">SSO オプションを含めて、ディレクトリ同期のオプションでは、オンプレミスのディレクトリの属性は、基準を満たす必要があります。[Office 365 ディレクトリ同期によってユーザーを提供する準備](prepare-for-directory-synchronization.md)は、ディレクトリにどのような属性を使用して、(存在する場合) は、どのようなクリーンアップが必要なの詳細を説明します。IdFix を使用して、ディレクトリのクリーンアップを自動化する方法について[をインストールして Office 365 の IdFix ツールの実行](install-and-run-idfix.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="140f4-p105">Any directory synchronization option, including SSO options, requires your on-premises directory attributes meet standards. The specifics of what attributes are used in your directory and what cleanup (if any) is needed are described in [Prepare to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md). See [Install and run the Office 365 IdFix tool](install-and-run-idfix.md) for instruction on how to use IdFix to automate directory cleanup.</span></span> 
    
## <a name="plan-how-you-are-going-to-create-office-365-accounts"></a><span data-ttu-id="140f4-132">Office 365 アカウントの作成を行う方法を計画します。</span><span class="sxs-lookup"><span data-stu-id="140f4-132">Plan how you are going to create Office 365 accounts</span></span>
<span data-ttu-id="140f4-133">次の表は、別のアカウントの管理ツールを一覧します。</span><span class="sxs-lookup"><span data-stu-id="140f4-133">The following table lists the different account management tools:</span></span>
    
|<span data-ttu-id="140f4-134">**オプション**</span><span class="sxs-lookup"><span data-stu-id="140f4-134">**Option**</span></span>|<span data-ttu-id="140f4-135">**メモ**</span><span class="sxs-lookup"><span data-stu-id="140f4-135">**Notes**</span></span>|
|:-----|:-----|
|<span data-ttu-id="140f4-136">**Office 365 管理センター**</span><span class="sxs-lookup"><span data-stu-id="140f4-136">**Office 365 admin center**</span></span> | <span data-ttu-id="140f4-137">- [ユーザー個別にまたは一括で Office 365 に追加の管理のヘルプ](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec)</span><span class="sxs-lookup"><span data-stu-id="140f4-137">- [Add users individually or in bulk to Office 365 - Admin Help](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec)</span></span> <br> <span data-ttu-id="140f4-138">-を追加し、ユーザー アカウントを変更する単純な web インターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="140f4-138">- Provides a simple web interface to add and change user accounts.</span></span> <br> <span data-ttu-id="140f4-139">がディレクトリ同期が有効になっている場合は、ユーザーを変更するのには使用不可 (場所およびライセンスの割り当てを設定することができます)。</span><span class="sxs-lookup"><span data-stu-id="140f4-139">- Can't be used to change users if directory synchronization is enabled (location and license assignment can be set).</span></span> <br> <span data-ttu-id="140f4-140">が SSO オプションを使用して使用不可。</span><span class="sxs-lookup"><span data-stu-id="140f4-140">- Can't be used with SSO options.</span></span> <br> |
|<span data-ttu-id="140f4-141">**Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="140f4-141">**Windows PowerShell**</span></span> | <span data-ttu-id="140f4-142">- [Windows PowerShell では、Office 365 を管理します。](https://go.microsoft.com/fwlink/p/?LinkId=698471)</span><span class="sxs-lookup"><span data-stu-id="140f4-142">- [Manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471)</span></span> <br> <span data-ttu-id="140f4-143">-を使用すると、Windows PowerShell スクリプトを使用してユーザーを一括でユーザーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="140f4-143">- Allows you to add users in bulk users by using a Windows PowerShell script.</span></span> <br> <span data-ttu-id="140f4-144">がアカウントの作成方法に関係なく、アカウントの場所およびライセンスを割り当てるには使用できます。</span><span class="sxs-lookup"><span data-stu-id="140f4-144">- Can be used to assign location and licenses to accounts, regardless of how the accounts are created.</span></span> <br> |
|<span data-ttu-id="140f4-145">**一括インポート**</span><span class="sxs-lookup"><span data-stu-id="140f4-145">**Bulk import**</span></span> | <span data-ttu-id="140f4-146">- [Office 365 の管理者のヘルプを同時に複数のユーザーを追加します。](add-several-users-at-the-same-time.md)</span><span class="sxs-lookup"><span data-stu-id="140f4-146">- [Add several users at the same time to Office 365 - Admin Help](add-several-users-at-the-same-time.md)</span></span> <br> <span data-ttu-id="140f4-147">-使用すると、Office 365 にユーザーのグループを追加するのには CSV ファイルをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="140f4-147">- Allows you to import a CSV file to add a group of users to Office 365.</span></span> <br> <span data-ttu-id="140f4-148">が SSO オプションを使用して使用不可。</span><span class="sxs-lookup"><span data-stu-id="140f4-148">- Can't be used with SSO options.</span></span> <br> |
|<span data-ttu-id="140f4-149">**Azure Active Directory**</span><span class="sxs-lookup"><span data-stu-id="140f4-149">**Azure Active Directory**</span></span> | <span data-ttu-id="140f4-p106">-は、Office 365 サブスクリプションで、Azure Active Directory の無料版を取得します。-セルフ サービス パスワードのリセット、クラウド ユーザーとサインインし、アクセス パネルのページのカスタマイズの無料版を使用して、ような機能を実行できます。</span><span class="sxs-lookup"><span data-stu-id="140f4-p106">- You get a free edition of Azure Active Directory with your Office 365 subscription. - You can perform functions like self-service password reset for cloud users, and customization of the Sign-in and Access Panel pages by using the free edition. </span></span><br> <span data-ttu-id="140f4-p107">-拡張機能を取得するには基本的なエディション、またはプレミアム ・ エディションのいずれかにアップグレードできます。サポートされている機能の一覧については、 [Azure Active Directory のエディション](https://go.microsoft.com/fwlink/p/?LinkId=698465)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="140f4-p107">- To get enhanced functionality, you can upgrade to either the basic edition, or the premium edition. See [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=698465) for the list of supported features. </span></span><br> |
|<span data-ttu-id="140f4-154">**ディレクトリ同期**</span><span class="sxs-lookup"><span data-stu-id="140f4-154">**Directory synchronization**</span></span> | <span data-ttu-id="140f4-155">- [Azure Active Directory で、設置型の id を統合します。](https://go.microsoft.com/fwlink/p/?LinkID=624168)</span><span class="sxs-lookup"><span data-stu-id="140f4-155">- [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168)</span></span> <br> <span data-ttu-id="140f4-156">-ディレクトリ同期パスワード同期の有無にかかわらず、[高速の設定を使用して、Azure の AD 接続](https://go.microsoft.com/fwlink/p/?LinkID=698537)を使用します。</span><span class="sxs-lookup"><span data-stu-id="140f4-156">- For directory synchronization with or without password synchronization, use [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537).</span></span>  <br>  <span data-ttu-id="140f4-157">-複数のフォレストと SSO のオプションの[カスタム インストールの Azure AD 接続](https://go.microsoft.com/fwlink/p/?LinkId=698430)を使用します。</span><span class="sxs-lookup"><span data-stu-id="140f4-157">- For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span> <br> <span data-ttu-id="140f4-158">SSO を有効にするために必要なインフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="140f4-158">- Provides the infrastructure that's necessary to enable SSO.</span></span> <br> <span data-ttu-id="140f4-159">必要な多くのハイブリッド シナリオ (段階的な移行、ハイブリッド交換)。</span><span class="sxs-lookup"><span data-stu-id="140f4-159">- Required for many hybrid scenarios (Staged migration, Hybrid Exchange)</span></span> <br> <span data-ttu-id="140f4-160">-セキュリティおよび設置ディレクトリからのメールが有効なグループを同期します。</span><span class="sxs-lookup"><span data-stu-id="140f4-160">- Synchronizes security and mail-enabled groups from your on-premises directory.</span></span> <br> |
   
<span data-ttu-id="140f4-p108">Office 365 にユーザー アカウントを追加する方法に関係なく、場所を指定する、ライセンスを割り当てるなど、いくつかのアカウント機能を管理するためにする必要があります。これらの機能から管理できる長期的な Office 365 の管理者センターまたは[Office 365 の PowerShell でのユーザー アカウントを作成](https://go.microsoft.com/fwlink/p/?LinkId=717083)することもできます。</span><span class="sxs-lookup"><span data-stu-id="140f4-p108">Regardless of how you intend to add the user accounts to Office 365, you need to manage several account features, such as assigning licenses, specifying location, and so on. These features can be managed long-term from the Office 365 admin center or you can also [create user accounts with Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).</span></span>
    
<span data-ttu-id="140f4-p109">追加し、Office 365 管理センターを使用してすべてのユーザーを管理する場合は、場所を指定して Office 365 のアカウントを作成すると同時にライセンスを割り当てます。その結果、あまり多くない計画が必要です。</span><span class="sxs-lookup"><span data-stu-id="140f4-p109">If you choose to add and manage all your users through the Office 365 admin center, you will specify the location and assign licenses at the same time as creating the Office 365 account. As a result, not much planning is required.</span></span>
    
> [!IMPORTANT]
> <span data-ttu-id="140f4-p110">(SharePoint Online に、たとえば) のライセンスを割り当てることには、Office 365 ポータルですがアカウントの所有者を表示することを意味せずに Office 365 のアカウントを作成すると、会社のサブスクリプション内のサービスのいずれかアクセスできません。場所と、ライセンスを割り当てると、サービスまたはサービスに割り当てたアカウントが複製されます。ユーザーは、自分のアカウントにサインインし、それらに割り当てられたサービスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="140f4-p110">Creating accounts in Office 365 without assigning a license (to SharePoint Online, for example) means that the account owner can view the Office 365 portal but can't access any of the services within your company's subscription. After you assign a location and the license, the account is replicated to the service or services that you assigned. The user can sign in to their account and use the services that you assigned to them.</span></span>