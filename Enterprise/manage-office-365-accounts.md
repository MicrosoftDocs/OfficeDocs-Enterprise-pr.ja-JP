---
title: Microsoft 365 アカウントを管理するためのツール
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: 'Microsoft 365 ユーザーを管理するために使用するツールについて説明します。 '
ms.openlocfilehash: ba73d899dee002fa08f373faaed4d772da546b13
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571030"
---
# <a name="tools-to-manage-microsoft-365-accounts"></a><span data-ttu-id="c5fbb-103">Microsoft 365 アカウントを管理するためのツール</span><span class="sxs-lookup"><span data-stu-id="c5fbb-103">Tools to manage Microsoft 365 accounts</span></span>

<span data-ttu-id="c5fbb-104">構成に応じて、さまざまな方法で Microsoft 365 ユーザーを管理することができます。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-104">You can manage Microsoft 365 users in several different ways, depending on your configuration.</span></span> <span data-ttu-id="c5fbb-105">[Microsoft 365 管理センター](https://admin.microsoft.com)、Windows PowerShell、Active Directory ドメインサービス (AD DS)、または Azure Active Directory (azure AD) 管理ポータルでユーザーを管理できます。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-105">You can manage users in the [Microsoft 365 admin center](https://admin.microsoft.com), Windows PowerShell, in Active Directory Domain Services (AD DS), or in the Azure Active Directory (Azure AD) admin portal.</span></span> 

<span data-ttu-id="c5fbb-106">Microsoft 365 を購入すると、管理センターと Windows PowerShell を使用してアカウントを管理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-106">As soon as you purchase Microsoft 365, the admin center and Windows PowerShell can be used to manage accounts.</span></span> <span data-ttu-id="c5fbb-107">クラウド id を管理する場合、組織内のすべてのユーザーには、Microsoft 365 に対して個別のユーザー ID とパスワードがあります。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-107">When managing cloud identities, every person in your organization has a separate user ID and password for Microsoft 365.</span></span> <span data-ttu-id="c5fbb-108">オンプレミスのインフラストラクチャと統合して、ユーザーアカウントを Microsoft 365 と同期させる場合は、Azure AD Connect を使用して、シングルサインオン機能の id とパスワードの同期を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-108">If you want to integrate with your on-premises infrastructure and have user accounts synchronized with Microsoft 365, you can use Azure AD Connect to provide synchronization of identities and passwords for single sign-on functionality.</span></span>
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a><span data-ttu-id="c5fbb-109">ユーザーアカウントを管理する場所と方法を計画します。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-109">Plan for where and how you will manage your user accounts</span></span>

<span data-ttu-id="c5fbb-110">ユーザーアカウントを管理する場所と方法は、Microsoft 365 で使用する id モデルによって異なります。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-110">Where and how you can manage your user accounts depends on the identity model you want to use for your Microsoft 365.</span></span> <span data-ttu-id="c5fbb-111">これらのモデル全体は、クラウド認証とフェデレーション認証です。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-111">The two overall models are cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="c5fbb-112">クラウド認証</span><span class="sxs-lookup"><span data-stu-id="c5fbb-112">Cloud authentication</span></span>

- <span data-ttu-id="c5fbb-113">Cloud authentication-Microsoft 365 管理センターでユーザーを作成および管理します。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-113">Cloud authentication - Create and manage users in the Microsoft 365 admin center.</span></span> <span data-ttu-id="c5fbb-114">Windows PowerShell または Azure AD を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-114">You can also use Windows PowerShell or Azure AD .</span></span> 
    
- <span data-ttu-id="c5fbb-115">シームレスなシングルサインオンを備えたパスワードハッシュ同期 (PHS)。 Azure AD で AD DS オブジェクトの認証を有効にする最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-115">Password hash sync (PHS) with seamless single sign-on - The simplest way to enable authentication for AD DS objects in Azure AD.</span></span> <span data-ttu-id="c5fbb-116">PHS では、AD DS のユーザーアカウントオブジェクトを Microsoft 365 と同期し、オンプレミスでユーザーを管理します。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-116">With PHS, you synchronize your AD DS user account objects with Microsoft 365 and manage your users on-premises.</span></span> 
    
- <span data-ttu-id="c5fbb-117">シームレスなシングルサインオンを備えたパススルー認証 (PTA)-1 つ以上のオンプレミスサーバー上で実行されているソフトウェアエージェントを使用して、AD DS に直接ユーザーを検証することにより、Azure AD 認証サービスの簡単なパスワード検証を提供します。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-117">Pass-through authentication (PTA) with seamless single sign-on - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your AD DS.</span></span> 
    
### <a name="federated-authentication"></a><span data-ttu-id="c5fbb-118">フェデレーション認証</span><span class="sxs-lookup"><span data-stu-id="c5fbb-118">Federated authentication</span></span>

- <span data-ttu-id="c5fbb-119">フェデレーション認証オプション-主に、より複雑な認証要件を持つ大規模な企業組織では、AD DS オブジェクトは Microsoft 365 と同期され、ユーザーアカウントは社内で管理されます。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-119">Federated authentication options - Primarily for large enterprise organizations with more complex authentication requirements, AD DS objects are synchronized with Microsoft 365 and users accounts are managed on-premises.</span></span> 
    
- <span data-ttu-id="c5fbb-120">[サードパーティの認証および id プロバイダー](about-office-365-identity.md) -AD DS オブジェクトを Microsoft 365 に同期させることができます。また、クラウドリソースへのアクセスは、主にサードパーティの id プロバイダー (IDP) によって管理されます。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-120">[Third-party authentication and identity providers](about-office-365-identity.md) - AD DS objects may be synchronized to Microsoft 365 and cloud resource access is primarily managed by a third-party identity provider (IDP).</span></span> 
    
## <a name="managing-accounts"></a><span data-ttu-id="c5fbb-121">アカウントの管理</span><span class="sxs-lookup"><span data-stu-id="c5fbb-121">Managing Accounts</span></span>

<span data-ttu-id="c5fbb-122">組織がアカウントを作成および管理する方法を決定するときは、次の要件を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-122">When deciding which way your organization will create and manage accounts, consider the following requirements:</span></span>
  
- <span data-ttu-id="c5fbb-123">Microsoft 365 と AD DS 間で id を接続するには、ディレクトリ同期ソフトウェアを社内環境内のサーバーにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-123">The directory synchronization software needs to be installed on servers within your on-premises environment to connect the identities between Microsoft 365 and your AD DS.</span></span>
    
- <span data-ttu-id="c5fbb-124">SSO オプションを含むディレクトリ同期オプションでは、AD DS の属性が標準に適合している必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-124">Any directory synchronization option, including SSO options, requires your AD DS attributes meet standards.</span></span> <span data-ttu-id="c5fbb-125">ディレクトリ同期を使用して、「 [Microsoft 365 へのディレクトリ同期によってユーザーをプロビジョニングする](prepare-for-directory-synchronization.md)」で説明されている、ディレクトリで使用されている属性と、必要に応じてクリーンアップを行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-125">The specifics of what attributes are used in your directory and what cleanup (if any) is needed are described in [Prepare to provision users through directory synchronization to Microsoft 365](prepare-for-directory-synchronization.md).</span></span> 
    
- <span data-ttu-id="c5fbb-126">Microsoft 365 アカウントを作成する方法を計画します。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-126">Plan how you are going to create Microsoft 365 accounts.</span></span>
    
    <span data-ttu-id="c5fbb-127">次の表に、さまざまなアカウント管理ツールを示します。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-127">The following table lists the different account management tools.</span></span>
    
|<span data-ttu-id="c5fbb-128">**オプション**</span><span class="sxs-lookup"><span data-stu-id="c5fbb-128">**Option**</span></span>|<span data-ttu-id="c5fbb-129">**メモ**</span><span class="sxs-lookup"><span data-stu-id="c5fbb-129">**Notes**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c5fbb-130">管理センター</span><span class="sxs-lookup"><span data-stu-id="c5fbb-130">Admin center</span></span>  <br/> |[<span data-ttu-id="c5fbb-131">ユーザーを個別にまたは一括して追加する</span><span class="sxs-lookup"><span data-stu-id="c5fbb-131">Add users individually or in bulk</span></span>](https://docs.microsoft.com/microsoft-365/admin/add-users/add-users) <br/>  <span data-ttu-id="c5fbb-132">ユーザーアカウントを追加および変更するための簡単な web インターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-132">Provides a simple web interface to add and change user accounts.</span></span>  <br/>  <span data-ttu-id="c5fbb-133">ディレクトリ同期が有効になっている場合、ユーザーの変更には使用できません (場所およびライセンスの割り当てを設定できます)。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-133">Can't be used to change users if directory synchronization is enabled (location and license assignment can be set).</span></span>  <br/>  <span data-ttu-id="c5fbb-134">SSO オプションを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-134">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="c5fbb-135">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c5fbb-135">Windows PowerShell</span></span>  <br/> |[<span data-ttu-id="c5fbb-136">Windows PowerShell を使用して Microsoft 365 を管理する</span><span class="sxs-lookup"><span data-stu-id="c5fbb-136">Manage Microsoft 365 with Windows PowerShell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  <span data-ttu-id="c5fbb-137">Windows PowerShell スクリプトを使用して、ユーザーを一括ユーザーで追加できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-137">Allows you to add users in bulk users by using a Windows PowerShell script.</span></span>  <br/>  <span data-ttu-id="c5fbb-138">アカウントの作成方法に関係なく、アカウントに場所とライセンスを割り当てるために使用できます。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-138">Can be used to assign location and licenses to accounts, regardless of how the accounts are created.</span></span>  <br/> |
|<span data-ttu-id="c5fbb-139">一括インポート</span><span class="sxs-lookup"><span data-stu-id="c5fbb-139">Bulk import</span></span>  <br/> |[<span data-ttu-id="c5fbb-140">同時に複数のユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="c5fbb-140">Add several users at the same time</span></span>](add-several-users-at-the-same-time.md) <br/>  <span data-ttu-id="c5fbb-141">CSV ファイルをインポートして、ユーザーのグループを Microsoft 365 に追加できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-141">Allows you to import a CSV file to add a group of users to Microsoft 365.</span></span>  <br/>  <span data-ttu-id="c5fbb-142">SSO オプションを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-142">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="c5fbb-143">Azure AD</span><span class="sxs-lookup"><span data-stu-id="c5fbb-143">Azure AD</span></span>  <br/> |<span data-ttu-id="c5fbb-144">Microsoft 365 のサブスクリプションを使用して、Azure AD の無料版を入手できます。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-144">You get a free edition of Azure AD with your Microsoft 365 subscription.</span></span> <span data-ttu-id="c5fbb-145">クラウドユーザーのセルフサービスによるパスワードのリセットなどの機能を実行したり、無料版を使用してサインインページとアクセスパネルページをカスタマイズしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-145">You can perform functions like self-service password reset for cloud users, and customization of the Sign-in and Access Panel pages by using the free edition.</span></span> <span data-ttu-id="c5fbb-146">拡張機能を利用するには、basic edition、Azure AD Premium P1、または Azure AD Premium P2 にアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-146">To get enhanced functionality, you can upgrade to the basic edition, Azure AD Premium P1, or Azure AD Premium P2.</span></span> <span data-ttu-id="c5fbb-147">サポートされている機能の一覧については、「 [AZURE AD エディション](https://go.microsoft.com/fwlink/p/?LinkId=698465)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-147">See [Azure AD editions](https://go.microsoft.com/fwlink/p/?LinkId=698465) for the list of supported features.</span></span>  <br/> |
|<span data-ttu-id="c5fbb-148">ディレクトリ同期</span><span class="sxs-lookup"><span data-stu-id="c5fbb-148">Directory synchronization</span></span>  <br/> |[<span data-ttu-id="c5fbb-149">オンプレミス id と Azure AD の統合</span><span class="sxs-lookup"><span data-stu-id="c5fbb-149">Integrating your on-premises identities with Azure AD</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  <span data-ttu-id="c5fbb-150">パスワード同期の有無にかかわらずディレクトリ同期を行うには、 [AZURE AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537)を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-150">For directory synchronization with or without password synchronization, use [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537).</span></span>  <br/>  <span data-ttu-id="c5fbb-151">複数のフォレストおよび SSO オプションでは、 [AZURE AD Connect のカスタムインストール](https://go.microsoft.com/fwlink/p/?LinkId=698430)を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-151">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>  <br/>  <span data-ttu-id="c5fbb-152">SSO を有効にするために必要なインフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-152">Provides the infrastructure that's necessary to enable SSO.</span></span>  <br/>  <span data-ttu-id="c5fbb-153">多くのハイブリッドシナリオに必要です。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-153">Required for many hybrid scenarios:</span></span>  <br/>  <span data-ttu-id="c5fbb-154">段階的な移行</span><span class="sxs-lookup"><span data-stu-id="c5fbb-154">Staged migration</span></span>  <br/>  <span data-ttu-id="c5fbb-155">ハイブリッド Exchange</span><span class="sxs-lookup"><span data-stu-id="c5fbb-155">Hybrid Exchange</span></span>  <br/>  <span data-ttu-id="c5fbb-156">セキュリティおよびメールが有効なグループを AD DS から同期します。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-156">Synchronizes security and mail-enabled groups from your AD DS.</span></span>  <br/> |
   
- <span data-ttu-id="c5fbb-157">ユーザーアカウントを Microsoft 365 に追加する方法に関係なく、ライセンスの割り当て、場所の指定など、いくつかのアカウント機能を管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-157">Regardless of how you intend to add the user accounts to Microsoft 365, you need to manage several account features, such as assigning licenses, specifying location, and so on.</span></span> <span data-ttu-id="c5fbb-158">これらの機能は、管理センターから長期的に管理することも、 [PowerShell を使用してユーザーアカウントを作成](https://go.microsoft.com/fwlink/p/?LinkId=717083)することもできます。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-158">These features can be managed long-term from the admin center or you can also [create user accounts with PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).</span></span>
    
    <span data-ttu-id="c5fbb-159">管理センターを使用してすべてのユーザーの追加と管理を選択する場合は、Microsoft 365 アカウントを作成するときと同時に、場所を指定してライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-159">If you choose to add and manage all your users through the admin center, you will specify the location and assign licenses at the same time as creating the Microsoft 365 account.</span></span> <span data-ttu-id="c5fbb-160">そのため、計画はあまり必要ありません。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-160">As a result, not much planning is required.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="c5fbb-161">Microsoft 365 で、ライセンスを割り当てずに (たとえば SharePoint Online に) アカウントを作成することは、アカウント所有者が Microsoft 365 center を表示できるが、会社のサブスクリプション内のサービスにアクセスできないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-161">Creating accounts in Microsoft 365 without assigning a license (to SharePoint Online, for example) means that the account owner can view the Microsoft 365 center but can't access any of the services within your company's subscription.</span></span> <span data-ttu-id="c5fbb-162">場所とライセンスを割り当てた後、割り当てたサービスにアカウントがレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-162">After you assign a location and the license, the account is replicated to the service or services that you assigned.</span></span> <span data-ttu-id="c5fbb-163">ユーザーは、自分のアカウントにサインインして、自分に割り当てられているサービスを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="c5fbb-163">The user can sign in to their account and use the services that you assigned to them.</span></span> 
  
## <a name="next-steps"></a><span data-ttu-id="c5fbb-164">次の手順</span><span class="sxs-lookup"><span data-stu-id="c5fbb-164">Next steps</span></span>

[<span data-ttu-id="c5fbb-165">Microsoft 365 とオンプレミス環境との統合</span><span class="sxs-lookup"><span data-stu-id="c5fbb-165">Microsoft 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
## <a name="see-also"></a><span data-ttu-id="c5fbb-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5fbb-166">See Also</span></span>

[<span data-ttu-id="c5fbb-167">Microsoft 365 でユーザーとグループを管理する</span><span class="sxs-lookup"><span data-stu-id="c5fbb-167">Manage users and groups in Microsoft 365</span></span>](https://docs.microsoft.com/microsoft-365/admin/add-users)
  

