---
title: Office 365 ID と Azure Active Directory について
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Office 365 のユーザー id を管理する方法について説明します。
ms.openlocfilehash: 14d1ec8a3ebc4620a72f831c0ec80253f7b3072c
ms.sourcegitcommit: dcb57859ad40090cf70586ac350472eb0fc8d9c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2018
ms.locfileid: "25639636"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a><span data-ttu-id="a6539-103">Office 365 ID と Azure Active Directory について</span><span class="sxs-lookup"><span data-stu-id="a6539-103">Understanding Office 365 identity and Azure Active Directory</span></span>

<span data-ttu-id="a6539-p101">Office 365 は、ユーザーを管理するのにクラウド ベースのユーザー id と認証サービス Azure Active Directory (AD の Azure) を使用します。選択する id 管理は、設置型の組織と Office 365 の間で構成されている場合は、初期の決定であり、クラウド インフラストラクチャの基盤の 1 つは。後でこの構成を変更することは難しい場合があるため、組織のニーズに最適を決定するためのオプションを慎重に検討します。設定し、自動的にユーザー アカウントを管理するのには Office 365 で 2 つの主要な認証モデルから選択することができます。**クラウドの認証**と**統合認証**します。</span><span class="sxs-lookup"><span data-stu-id="a6539-p101">Office 365 uses the cloud-based user identity and authentication service Azure Active Directory (Azure AD) to manage users. Choosing if identity management is configured between your on-premises organization and Office 365 is an early decision that is one of the foundations of your cloud infrastructure. Because changing this configuration later can be difficult, carefully consider the options to determine what works best for the needs of your organization. You can choose from two main authentication models in Office 365 to set up and manage user accounts; **cloud authentication** and **federated authentication**.</span></span>
  
<span data-ttu-id="a6539-p102">これら認証と id 取得するためのモデルのうちどれを慎重に検討する重要であり、実行中です。時間、既存の複雑性、および実装し、それぞれの認証と id のオプションを維持するコストを考えてください。これらの要素は組織ごとに異なります展開に使用する認証と識別情報モデルを選択するためのユーザー オプションの重要な概念を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6539-p102">It's important to carefully consider which of these authentication and identity models to use to get up and running. Think about the time, existing complexity, and cost to implement and maintain each of the authentication and identity options. These factors are different for every organization; and you should understand the key concepts for the identity options to help you choose the authentication and identity model you want to use for your deployment.</span></span>
  
## <a name="cloud-authentication"></a><span data-ttu-id="a6539-111">クラウドの認証</span><span class="sxs-lookup"><span data-stu-id="a6539-111">Cloud authentication</span></span>

<span data-ttu-id="a6539-112">によって Office 365 でユーザーの認証と id のサービスを管理するためのいくつかのオプションがある場合は、または、既存 Active Directory 環境の設置型を持っていない、します。</span><span class="sxs-lookup"><span data-stu-id="a6539-112">Depending if you have or don't have an existing Active Directory environment on-premises, you have several options to manage authentication and identity services for your users with Office 365.</span></span>
  
### <a name="cloud-only"></a><span data-ttu-id="a6539-113">クラウドのみ</span><span class="sxs-lookup"><span data-stu-id="a6539-113">Cloud-only</span></span>

<span data-ttu-id="a6539-p103">クラウド専用モデルでは、Office 365 でユーザーのアカウントは、のみを管理します。設置必要はありません。すべてによって処理される、クラウドで Azure AD。作成し、Office 365 の管理センターでユーザーを管理するか、Windows PowerShell を使用して[PowerShell コマンドレット](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell)と id と認証は完全にクラウドで Azure AD。クラウド専用のモデルは、通常、適切な選択肢の場合です。</span><span class="sxs-lookup"><span data-stu-id="a6539-p103">With the cloud-only model, you manage your user accounts in Office 365 only. No on-premises servers are required; it's all handled in the cloud by Azure AD. You create and manage users in the Office 365 admin center or by using Windows PowerShell [PowerShell cmdlets](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell) and identity and authentication are handled completely in the cloud by Azure AD. The cloud-only model is typically a good choice if:</span></span> 
  
- <span data-ttu-id="a6539-118">他のオンプレミス ユーザーのディレクトリがあるありません。</span><span class="sxs-lookup"><span data-stu-id="a6539-118">You have no other on-premises user directory.</span></span>
    
- <span data-ttu-id="a6539-119">オンプレミスで非常に複雑なディレクトリがあるし、単に統合できるので、作業は避けたいです。</span><span class="sxs-lookup"><span data-stu-id="a6539-119">You have a very complex on-premises directory and simply want to avoid the work to integrate with it.</span></span>
    
- <span data-ttu-id="a6539-p104">設置型の既存のディレクトリがあるが、試用版または Office 365 のパイロットを実行します。以降では、オンプレミス ディレクトリに接続する準備ができたら、クラウド ユーザーはオンプレミス ユーザーを照合できます。</span><span class="sxs-lookup"><span data-stu-id="a6539-p104">You have an existing on-premises directory, but you want to run a trial or pilot of Office 365. Later, you can match the cloud users to on-premises users when you are ready to connect to your on-premises directory.</span></span>
    
<span data-ttu-id="a6539-122">クラウド id を使用して開始するには、[ビジネス向けの Office 365 のセットアップ](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6539-122">To get started with cloud identity, see [Set up Office 365 for business](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).</span></span>
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a><span data-ttu-id="a6539-123">シームレスなシングル サインオンとパスワード ハッシュの同期</span><span class="sxs-lookup"><span data-stu-id="a6539-123">Password hash sync with seamless single sign-on</span></span>

<span data-ttu-id="a6539-p105">Azure AD で設置ディレクトリ オブジェクトの認証を有効にする最も簡単な方法です。パスワード ハッシュ (PHS)、同期に、オンプレミスの Active Directory ユーザー アカウント オブジェクトを Office 365 と同期して、ユーザーの設置型の管理します。ユーザーのパスワードのハッシュは、ユーザーが、同じパスワードを設置できるようにし、雲の中に、オンプレミスの Active Directory から Azure AD に同期されます。パスワードが変更された、設置型をリセットするときは、クラウド リソースおよび設置型リソースのユーザーが同じパスワードを常に使用できるように Azure AD に新しいパスワードのハッシュが同期されます。パスワードは Azure AD に送信またはクリア テキストで Azure AD に格納しないでください。Azure AD、アイデンティティの保護などのいくつかのプレミアム機能には、どの認証方法が選択されている PHS が必要です。シームレスなシングル サインオン、ユーザーに自動的にサインインしている Azure の AD に、企業内のデバイス上にあるし、企業ネットワークに接続されています。</span><span class="sxs-lookup"><span data-stu-id="a6539-p105">The simplest way to enable authentication for on-premises directory objects in Azure AD. With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises. Hashes of user passwords are synchronized from your on-premises Active Directory to Azure AD so that the users have the same password on-premises and in the cloud. When passwords are changed or reset on-premises, the new password hashes are synchronized to Azure AD so that your users can always use the same password for cloud resources and on-premises resources. The passwords are never sent to Azure AD or stored in Azure AD in clear text. Some premium features of Azure AD, such as Identity Protection, require PHS regardless of which authentication method is selected. With seamless single sign-on, users are automatically signed in to Azure AD when they are on their corporate devices and connected to your corporate network.</span></span>
  
<span data-ttu-id="a6539-131">[パスワード ハッシュの同期を選択して](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)、[シームレスなシングル サインオン](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="a6539-131">Learn more about [choosing password hash sync](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) and [seamless single sign-on](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).</span></span>
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a><span data-ttu-id="a6539-132">シームレスなシングル サインオンでのパススルー認証</span><span class="sxs-lookup"><span data-stu-id="a6539-132">Pass-through authentication with seamless single sign-on</span></span>

<span data-ttu-id="a6539-p106">Azure AD 認証サービスが、オンプレミスの Active Directory に直接ユーザーを検証するために 1 つまたは複数のオンプレミスのサーバーで実行されているソフトウェア ・ エージェントを使用して単純なパスワードの検証を提供します。パススルー認証 (PTA) では、オンプレミスの Active Directory ユーザー アカウント オブジェクトを Office 365 と同期して、ユーザーの設置型の管理します。により、ユーザーは、オンプレミスと Office 365 のリソースとアプリケーションの両方に設置型のアカウントとパスワードを使用してにサインインします。この構成では、Office 365 のパスワード ハッシュを送信することがなく、オンプレミスの Active Directory に対して直接ユーザーのパスワードを検証します。パスワード ポリシー、およびログオン時間は、この認証方式を使用は、オンプレミスのユーザー アカウントをすぐに適用するセキュリティ要件を持つ企業を示しています。シームレスなシングル サインオン、ユーザーに自動的にサインインしている Azure の AD に、企業内のデバイス上にあるし、企業ネットワークに接続されています。</span><span class="sxs-lookup"><span data-stu-id="a6539-p106">Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory. With pass-through authentication (PTA), you synchronize on-premises Active Directory user account objects with Office 365 and manage your users on-premises. Allows your users to sign in to both on-premises and Office 365 resources and applications using their on-premises account and password. This configuration validates users passwords directly against your on-premises Active Directory without sending password hashes to Office 365. Companies with a security requirement to immediately enforce on-premises user account states, password policies, and logon hours would use this authentication method. With seamless single sign-on, users are automatically signed in to Azure AD when they are on their corporate devices and connected to your corporate network.</span></span>
  
<span data-ttu-id="a6539-139">[パススルー認証を選択して](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)、[シームレスなシングル サインオン](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso)の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6539-139">Learn more about [choosing pass-through authentication](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) and [seamless single sign-on](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).</span></span>
  
## <a name="federated-authentication-options"></a><span data-ttu-id="a6539-140">フェデレーションの認証オプション</span><span class="sxs-lookup"><span data-stu-id="a6539-140">Federated authentication options</span></span>

<span data-ttu-id="a6539-141">既存 Active Directory 環境設置の場合は、Office 365 でユーザーの認証と id のサービスを管理するためにフェデレーション認証を使用して、ディレクトリを Office 365 に統合できます。</span><span class="sxs-lookup"><span data-stu-id="a6539-141">If you have an existing Active Directory environment on-premises, you can integrate Office 365 with your directory by using federated authentication to manage authentication and identity services for your users in Office 365.</span></span>
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a><span data-ttu-id="a6539-142">Active Directory フェデレーション サービス (AD FS) のフェデレーション id</span><span class="sxs-lookup"><span data-stu-id="a6539-142">Federated identity with Active Directory Federation Services (AD FS)</span></span>

<span data-ttu-id="a6539-p107">複雑な認証要件を持つ大規模な企業組織では、主に設置型のディレクトリ オブジェクトは、Office 365 と同期し、ユーザー アカウントは、管理対象の設置型です。AD FS では、ユーザーがある、同じパスワード、オンプレミスとクラウドで、もう一度サインインして Office 365 を使用するにはありません。このフェデレーション認証モデルは、スマート カード ベースの認証またはサード ・ パーティ製の多要素認証などの他の認証要件を提供することができ、組織で、認証の要件がある場合に通常必要とAzure AD でネイティブにサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a6539-p107">Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises. With AD FS, users have the same password on-premises and in the cloud and they do not have to sign in again to use Office 365. This federated authentication model can provide additional authentication requirements, such as smartcard-based authentication or a third-party multi-factor authentication and is typically required when organizations have an authentication requirement not natively supported by Azure AD.</span></span>
  
<span data-ttu-id="a6539-146">[AD FS のフェデレーション id の選択](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="a6539-146">Learn more about [choosing federated identity with AD FS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn).</span></span>
  
### <a name="third-party-authentication-and-identity-providers"></a><span data-ttu-id="a6539-147">サード ・ パーティ製の認証と id プロバイダー</span><span class="sxs-lookup"><span data-stu-id="a6539-147">Third-party authentication and identity providers</span></span>

<span data-ttu-id="a6539-p108">設置ディレクトリ オブジェクトは、Office 365 に同期させる可能性があり、クラウド リソースへのアクセスは、主に、サードパーティの id プロバイダー (IdP) によって管理されます。組織は、フェデレーションのサード ・ パーティ製ソリューションを使用している場合を構成できますサインオン ソリューションを Office 365 のフェデレーションのサード ・ パーティ製ソリューションが Azure AD と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="a6539-p108">On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP). If your organization uses a third-party federation solution, you can configure sign-on with that solution for Office 365 provided that the third-party federation solution is compatible with Azure AD.</span></span>
  
<span data-ttu-id="a6539-150">[Azure AD フェデレーションの互換性](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="a6539-150">Learn more about [Azure AD federation compatibility](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility).</span></span>
  
## <a name="configuring-identity-and-authentication-with-office-365"></a><span data-ttu-id="a6539-151">Office 365 の id と認証を構成します。</span><span class="sxs-lookup"><span data-stu-id="a6539-151">Configuring identity and authentication with Office 365</span></span>

<span data-ttu-id="a6539-p109">設置ディレクトリは、Office 365 と Azure AD との統合が単純化され[Azure AD 接続](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)とします。Azure AD 接続は、ディレクトリに接続する最良の方法で、ユーザーは、クラウドを同期するのには組織では、マイクロソフトの推奨です。</span><span class="sxs-lookup"><span data-stu-id="a6539-p109">Integrating your on-premises directories with Office 365 and Azure AD has been simplified with [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). Azure AD Connect is the best way to connect your directories and is Microsoft's recommendation for organizations to sync their users to the cloud.</span></span>
  
<span data-ttu-id="a6539-154">Azure AD アドバイザーを使用することもできます: [Azure AD 接続アドバイザー](https://aka.ms/aadconnectpwsync) [AD FS 展開のアドバイザー](https://aka.ms/adfsguidance)では、 [Azure AD のプレミアム ・ セットアップ ・ ガイド](https://aka.ms/aadpguidance)です。</span><span class="sxs-lookup"><span data-stu-id="a6539-154">You can also use the Azure AD advisors: the [Azure AD Connect advisor](https://aka.ms/aadconnectpwsync), the [AD FS deployment advisor](https://aka.ms/adfsguidance), and the [Azure AD Premium setup guide](https://aka.ms/aadpguidance).</span></span>
  
## <a name="video-training"></a><span data-ttu-id="a6539-155">ビデオ ・ トレーニング</span><span class="sxs-lookup"><span data-stu-id="a6539-155">Video training</span></span>

<span data-ttu-id="a6539-156">詳細については、ビデオのコースを参照してください[Office 365: Azure を使用してユーザーの管理の AD 接続](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)、LinkedIn の学習で。</span><span class="sxs-lookup"><span data-stu-id="a6539-156">For more information, see the video course [Office 365: Manage Identities Using Azure AD Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), brought to you by LinkedIn Learning.</span></span>
