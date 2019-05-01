---
title: Office 365 とオンプレミス環境との統合
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Office 365 と既存のディレクトリサービスを統合する方法について説明します。
ms.openlocfilehash: 112f543a9c647ea850d5e43bc14483308da0b2c7
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487407"
---
# <a name="office-365-integration-with-on-premises-environments"></a><span data-ttu-id="d8882-103">Office 365 とオンプレミス環境との統合</span><span class="sxs-lookup"><span data-stu-id="d8882-103">Office 365 integration with on-premises environments</span></span>

<span data-ttu-id="d8882-104">Office 365 を既存のディレクトリサービスに統合できます。また、Exchange server、Skype for business server 2015、または SharePoint server 2013 の社内インストールを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d8882-104">You can integrate Office 365 with your existing directory services and with an on-premises installation of Exchange Server, Skype for Business Server 2015, or SharePoint Server 2013.</span></span>
  
 - <span data-ttu-id="d8882-105">ディレクトリサービスと統合すると、両方の環境のユーザーアカウントを同期して管理することができます。</span><span class="sxs-lookup"><span data-stu-id="d8882-105">When you integrate with directory services, you can synchronize and manage user accounts for both environments.</span></span> <span data-ttu-id="d8882-106">また、ユーザーがオンプレミスの資格情報を使用して両方の環境にログオンできるように、パスワードハッシュ同期またはシングルサインオン (SSO) を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="d8882-106">You can also add password hash synchronization or single sign-on (SSO) so users can log on to both environments with their on-premises credentials.</span></span>
 - <span data-ttu-id="d8882-107">オンプレミスのサーバー製品と統合する場合は、ハイブリッド環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="d8882-107">When you integrate with on-premises server products, you create a hybrid environment.</span></span> <span data-ttu-id="d8882-108">ハイブリッド環境は、ユーザーまたは情報を Office 365 に移行する際に役立つことがあります。または、一部のユーザーまたは一部の情報を社内とクラウドに移行することができます。</span><span class="sxs-lookup"><span data-stu-id="d8882-108">A hybrid environment can help as you migrate users or information to Office 365, or you can continue to have some users or some information on-premises and some in the cloud.</span></span> <span data-ttu-id="d8882-109">ハイブリッド環境の詳細については、「 [Office 365 ハイブリッドクラウドソリューションの概要](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8882-109">For more information about hybrid environments, see [Office 365 hybrid cloud solutions overview](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).</span></span>

<span data-ttu-id="d8882-110">また、カスタマイズしたセットアップガイダンスに Azure AD アドバイザーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d8882-110">You can also use the Azure AD advisors for customized setup guidance:</span></span>
- [<span data-ttu-id="d8882-111">Azure AD Connect advisor</span><span class="sxs-lookup"><span data-stu-id="d8882-111">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
- [<span data-ttu-id="d8882-112">AD FS 展開アドバイザー</span><span class="sxs-lookup"><span data-stu-id="d8882-112">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
- [<span data-ttu-id="d8882-113">Azure RMS 展開ウィザード</span><span class="sxs-lookup"><span data-stu-id="d8882-113">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
- [<span data-ttu-id="d8882-114">Azure AD Premium のセットアップガイダンス</span><span class="sxs-lookup"><span data-stu-id="d8882-114">Azure AD Premium setup guidance</span></span>](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a><span data-ttu-id="d8882-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="d8882-115">Before you begin</span></span>
<span data-ttu-id="d8882-116">office 365 とオンプレミス環境を統合する前に、 [office 365 のネットワーク計画とパフォーマンスチューニング](network-planning-and-performance.md)にも参加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8882-116">Before you integrate Office 365 and an on-premises environment, you also need to attend to [network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span> <span data-ttu-id="d8882-117">Office 365 で利用可能な[id モデル](about-office-365-identity.md)についても理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8882-117">You will also want to understand the available [identity models](about-office-365-identity.md) in Office 365.</span></span> 

<span data-ttu-id="d8882-118">office 365 のユーザーおよびアカウントの管理に使用できるツールの一覧については、「 [office のユーザーアカウントを管理する場所](manage-office-365-accounts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8882-118">See [where to manage Office 365 user accounts](manage-office-365-accounts.md) for a list of tools you can use to manage Office 365 users and accounts.</span></span> 
  
## <a name="integrate-office-365-with-directory-services"></a><span data-ttu-id="d8882-119">Office 365 とディレクトリサービスの統合</span><span class="sxs-lookup"><span data-stu-id="d8882-119">Integrate Office 365 with directory services</span></span>
<span data-ttu-id="d8882-120">オンプレミスディレクトリに既存のユーザーアカウントがある場合は、それらのアカウントを Office 365 で再作成して、環境間での相違点やエラーを発生させないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8882-120">If you have existing user accounts in an on-premises directory, you don't want to re-create all of those accounts in Office 365 and risk introducing differences or errors between the environments.</span></span> <span data-ttu-id="d8882-121">ディレクトリ同期は、オンライン環境とオンプレミス環境との間でアカウントをミラーリングするのに便利です。</span><span class="sxs-lookup"><span data-stu-id="d8882-121">Directory synchronization helps you mirror those accounts between your online and on-premises environments.</span></span> <span data-ttu-id="d8882-122">ディレクトリ同期を使用すると、ユーザーは環境ごとに新しい情報を記憶する必要がなくなります。また、アカウントを2回作成または更新する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d8882-122">With directory synchronization, your users don't have to remember new information for each environment, and you don't have to create or update accounts twice.</span></span> <span data-ttu-id="d8882-123">ディレクトリ同期のために[オンプレミスのディレクトリを準備](prepare-for-directory-synchronization.md)する必要があります。これは手動で行うか、 [idfix](install-and-run-idfix.md)ツール (idfix ツールは Active directory でのみ動作) を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d8882-123">You will need to [prepare your on-premises directory](prepare-for-directory-synchronization.md) for directory synchronization, you can do this manually or use the [IdFix tool](install-and-run-idfix.md) (IdFix tool only works with Active Directory).</span></span> 
  
![ディレクトリ同期を使用してオンプレミスとオンラインのユーザーアカウント情報を同期された状態に保つ](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
<span data-ttu-id="d8882-125">ユーザーがオンプレミスの資格情報を使用して Office 365 にログオンできるようにする場合は、SSO を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d8882-125">If you want users to be able to log on to Office 365 with their on-premises credentials, you can also configure SSO.</span></span> <span data-ttu-id="d8882-126">SSO を使用すると、Office 365 は、ユーザー認証用にオンプレミス環境を信頼するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="d8882-126">With SSO, Office 365 is configured to trust the on-premises environment for user authentication.</span></span>
  
![シングルサインオンを使用すると、オンプレミスの環境とオンライン環境の両方で同じアカウントを使用できます。](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
<span data-ttu-id="d8882-128">次の表に示すように、ユーザーアカウントの管理方法によって、ユーザーに対して異なるエクスペリエンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="d8882-128">Different user account management techniques provide different experiences for your users, as shown in the following table.</span></span>
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a><span data-ttu-id="d8882-129">**パスワードのハッシュ同期またはパススルー認証の有無にかかわらずディレクトリ同期**</span><span class="sxs-lookup"><span data-stu-id="d8882-129">**Directory synchronization with or without password hash synchronization or pass-through authentication**</span></span>
<span data-ttu-id="d8882-130">ユーザーが自分のユーザーアカウント (domain\username) を使用してオンプレミス環境にログオンします。</span><span class="sxs-lookup"><span data-stu-id="d8882-130">A user logs on to their on-premises environment with their user account (domain\username).</span></span> <span data-ttu-id="d8882-131">Office 365 に移行する場合は、職場または学校のアカウント (user@domain.com) で再度ログオンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8882-131">When they go to Office 365, they must log on again with their work or school account (user@domain.com).</span></span> <span data-ttu-id="d8882-132">両方の環境で同じユーザー名が指定されています。</span><span class="sxs-lookup"><span data-stu-id="d8882-132">The user name is the same in both environments.</span></span> <span data-ttu-id="d8882-133">パスワードハッシュ同期またはパススルー認証を追加すると、ユーザーは両方の環境で同じパスワードを使用しますが、Office 365 にログオンするときにこれらの資格情報を再度提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8882-133">When you add password hash sync or pass-through authentication, the user has the same password for both environments, but will have to provide those credentials again when logging on to Office 365.</span></span> <span data-ttu-id="d8882-134">ディレクトリ同期とパスワードハッシュ同期は、最も一般的に使用されるディレクトリ同期のシナリオです。</span><span class="sxs-lookup"><span data-stu-id="d8882-134">Directory synchronization with password hash sync is the most commonly used directory sync scenario.</span></span>

<span data-ttu-id="d8882-135">ディレクトリ同期をセットアップするには、Azure Active directory Connect を使用します。</span><span class="sxs-lookup"><span data-stu-id="d8882-135">To set up directory synchronization, use Azure Active Directory Connect.</span></span> <span data-ttu-id="d8882-136">手順については、「 [Office 365 のディレクトリ同期をセットアップ](set-up-directory-synchronization.md)する」と「 [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8882-136">For instructions, read [Set up directory synchronization for Office 365](set-up-directory-synchronization.md), and [Use Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537).</span></span>

<span data-ttu-id="d8882-137">[Office 365 にディレクトリ同期を使用してユーザーをプロビジョニングするための準備](prepare-for-directory-synchronization.md)の詳細と、[オンプレミスと Azure Active directory の識別を統合](https://go.microsoft.com/fwlink/?LinkId=518101)する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d8882-137">Learn more about [preparing to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md) and [integrating your on-premises identifies with Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).</span></span>

### <a name="directory-synchronization-with-sso"></a><span data-ttu-id="d8882-138">**SSO を使用したディレクトリ同期**</span><span class="sxs-lookup"><span data-stu-id="d8882-138">**Directory synchronization with SSO**</span></span>
<span data-ttu-id="d8882-139">ユーザーが自分のユーザーアカウントを使用してオンプレミス環境にログオンします。</span><span class="sxs-lookup"><span data-stu-id="d8882-139">A user logs on to their on-premises environment with their user account.</span></span> <span data-ttu-id="d8882-140">Office 365 に移行すると、それらのユーザーは自動的にログオンするか、オンプレミス環境 (domain\username) に使用したものと同じ資格情報を使用してログオンします。</span><span class="sxs-lookup"><span data-stu-id="d8882-140">When they go to Office 365, they are either logged on automatically, or they log on using the same credentials they use for their on-premises environment (domain\username).</span></span>

<span data-ttu-id="d8882-141">SSO をセットアップするには、Azure AD Connect も使用します。</span><span class="sxs-lookup"><span data-stu-id="d8882-141">To set up SSO you also use Azure AD Connect.</span></span> <span data-ttu-id="d8882-142">手順については、「 [Azure AD Connect でカスタム設定を使用する](https://go.microsoft.com/fwlink/p/?LinkID=698430)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8882-142">For instructions, read [Use Azure AD Connect with custom settings](https://go.microsoft.com/fwlink/p/?LinkID=698430).</span></span>

<span data-ttu-id="d8882-143">[Azure Active Directory を使用したアプリケーションアクセスとシングルサインオン](https://go.microsoft.com/fwlink/p/?LinkId=698604)の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="d8882-143">Learn more about [application access and single sign-on with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>

## <a name="azure-ad-connect"></a><span data-ttu-id="d8882-144">Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="d8882-144">Azure AD Connect</span></span>
<span data-ttu-id="d8882-145">azure ad Connect は、DirSync、azure ad Sync などの id 統合ツールの以前のバージョンに置き換えられました。詳細については、「[オンプレミス id と Azure Active Directory の統合](https://go.microsoft.com/fwlink/p/?LinkId=527969)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8882-145">Azure AD Connect replaces older versions of identity integration tools such as DirSync and Azure AD Sync. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span> <span data-ttu-id="d8882-146">azure Active Directory 同期から azure AD Connect に更新する場合は、[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8882-146">If you want to update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span> <span data-ttu-id="d8882-147">[Microsoft Azure で Office 365 ディレクトリ同期 (DirSync)](https://go.microsoft.com/fwlink/?LinkId=517887)用に構築されたソリューションアーキテクチャを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8882-147">See a solution architecture built for [Office 365 Directory Synchronization (DirSync) in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).</span></span>