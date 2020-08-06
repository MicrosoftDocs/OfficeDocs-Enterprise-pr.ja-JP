---
title: Microsoft 365 とオンプレミス環境との統合
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 10/08/2019
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
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
description: Microsoft 365 と既存のディレクトリサービスを統合する方法について説明します。
ms.openlocfilehash: 1207c7549a0c81a45211581be2b068ca8067a35b
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571060"
---
# <a name="microsoft-365-integration-with-on-premises-environments"></a><span data-ttu-id="47449-103">Microsoft 365 とオンプレミス環境との統合</span><span class="sxs-lookup"><span data-stu-id="47449-103">Microsoft 365 integration with on-premises environments</span></span>

<span data-ttu-id="47449-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="47449-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="47449-105">Microsoft 365 と既存のディレクトリサービス、および Exchange Server、Skype for Business Server 2015、または SharePoint Server のオンプレミスインストールを統合することができます。</span><span class="sxs-lookup"><span data-stu-id="47449-105">You can integrate Microsoft 365 with your existing directory services and with an on-premises installation of Exchange Server, Skype for Business Server 2015, or SharePoint Server.</span></span>
  
 - <span data-ttu-id="47449-106">ディレクトリサービスと統合すると、両方の環境のユーザーアカウントを同期して管理することができます。</span><span class="sxs-lookup"><span data-stu-id="47449-106">When you integrate with directory services, you can synchronize and manage user accounts for both environments.</span></span> <span data-ttu-id="47449-107">また、ユーザーがオンプレミスの資格情報を使用して両方の環境にログオンできるように、パスワードハッシュ同期またはシングルサインオン (SSO) を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="47449-107">You can also add password hash synchronization or single sign-on (SSO) so users can log on to both environments with their on-premises credentials.</span></span>
 - <span data-ttu-id="47449-108">オンプレミスのサーバー製品と統合する場合は、ハイブリッド環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="47449-108">When you integrate with on-premises server products, you create a hybrid environment.</span></span> <span data-ttu-id="47449-109">ハイブリッド環境は、ユーザーまたは情報を Microsoft 365 に移行する際に役立つことがあります。または、一部のユーザーまたは一部の情報を社内とクラウドに移行することができます。</span><span class="sxs-lookup"><span data-stu-id="47449-109">A hybrid environment can help as you migrate users or information to Microsoft 365, or you can continue to have some users or some information on-premises and some in the cloud.</span></span> <span data-ttu-id="47449-110">ハイブリッド環境の詳細については、「[ハイブリッドクラウドの概要](https://docs.microsoft.com/Office365/Enterprise/hybrid-cloud-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47449-110">For more information about hybrid environments, see [Hybrid cloud overview](https://docs.microsoft.com/Office365/Enterprise/hybrid-cloud-overview).</span></span>

<span data-ttu-id="47449-111">カスタマイズしたセットアップガイダンスに Azure Active Directory (Azure AD) アドバイザーを使用することもできます (Microsoft 365 にサインインする必要があります)。</span><span class="sxs-lookup"><span data-stu-id="47449-111">You can also use the Azure Active Directory (Azure AD) advisors for customized setup guidance (you must be signed in to Microsoft 365):</span></span>

- [<span data-ttu-id="47449-112">組織のディレクトリからユーザーを同期する</span><span class="sxs-lookup"><span data-stu-id="47449-112">Sync users from your org's directory</span></span>](https://aka.ms/aadconnectpwsync)
- [<span data-ttu-id="47449-113">AD FS 展開アドバイザー</span><span class="sxs-lookup"><span data-stu-id="47449-113">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
- [<span data-ttu-id="47449-114">Azure AD セットアップガイド</span><span class="sxs-lookup"><span data-stu-id="47449-114">Azure AD setup guide</span></span>](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a><span data-ttu-id="47449-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="47449-115">Before you begin</span></span>

<span data-ttu-id="47449-116">Microsoft 365 とオンプレミス環境を統合する前に、[ネットワーク計画とパフォーマンスチューニング](network-planning-and-performance.md)にも参加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47449-116">Before you integrate Microsoft 365 and an on-premises environment, you also need to attend to [network planning and performance tuning](network-planning-and-performance.md).</span></span> <span data-ttu-id="47449-117">利用可能な[id モデル](about-office-365-identity.md)についても理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="47449-117">You will also want to understand the available [identity models](about-office-365-identity.md).</span></span> 

<span data-ttu-id="47449-118">365 Microsoft 365 アカウントを管理するために使用できるツールの一覧については、「 [microsoft アカウントの管理](manage-office-365-accounts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47449-118">See [where to manage Microsoft 365 accounts](manage-office-365-accounts.md) for a list of tools you can use to manage Microsoft 365 users and accounts.</span></span> 
  
## <a name="integrate-microsoft-365-with-directory-services"></a><span data-ttu-id="47449-119">Microsoft 365 とディレクトリサービスの統合</span><span class="sxs-lookup"><span data-stu-id="47449-119">Integrate Microsoft 365 with directory services</span></span>
<span data-ttu-id="47449-120">オンプレミスのディレクトリに既存のユーザーアカウントがある場合は、それらのアカウントを Microsoft 365 で再作成したり、環境間の相違点やエラーを発生させたりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="47449-120">If you have existing user accounts in an on-premises directory, you don't want to re-create all of those accounts in Microsoft 365 and risk introducing differences or errors between the environments.</span></span> <span data-ttu-id="47449-121">ディレクトリ同期は、オンライン環境とオンプレミス環境との間でアカウントをミラーリングするのに便利です。</span><span class="sxs-lookup"><span data-stu-id="47449-121">Directory synchronization helps you mirror those accounts between your online and on-premises environments.</span></span> <span data-ttu-id="47449-122">ディレクトリ同期を使用すると、ユーザーは環境ごとに新しい情報を記憶する必要がなくなります。また、アカウントを2回作成または更新する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="47449-122">With directory synchronization, your users don't have to remember new information for each environment, and you don't have to create or update accounts twice.</span></span> <span data-ttu-id="47449-123">ディレクトリ同期のために[、オンプレミスのディレクトリを準備](prepare-for-directory-synchronization.md)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47449-123">You will need to [prepare your on-premises directory](prepare-for-directory-synchronization.md) for directory synchronization.</span></span>
  
![ディレクトリ同期を使用してオンプレミスとオンラインのユーザーアカウント情報を同期された状態に保つ](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
<span data-ttu-id="47449-125">ユーザーがオンプレミスの資格情報を使用して Microsoft 365 にログオンできるようにする場合は、SSO を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="47449-125">If you want users to be able to log on to Microsoft 365 with their on-premises credentials, you can also configure SSO.</span></span> <span data-ttu-id="47449-126">SSO を使用すると、Microsoft 365 は、ユーザー認証用にオンプレミス環境を信頼するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="47449-126">With SSO, Microsoft 365 is configured to trust the on-premises environment for user authentication.</span></span>
  
![シングルサインオンを使用すると、オンプレミスの環境とオンライン環境の両方で同じアカウントを使用できます。](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
<span data-ttu-id="47449-128">次の表に示すように、ユーザーアカウントの管理方法によって、ユーザーに対して異なるエクスペリエンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="47449-128">Different user account management techniques provide different experiences for your users, as shown in the following table.</span></span>
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a><span data-ttu-id="47449-129">パスワードのハッシュ同期またはパススルー認証の有無にかかわらずディレクトリ同期</span><span class="sxs-lookup"><span data-stu-id="47449-129">Directory synchronization with or without password hash synchronization or pass-through authentication</span></span>

<span data-ttu-id="47449-130">ユーザーが自分のユーザーアカウント (domain\username) を使用してオンプレミス環境にログオンします。</span><span class="sxs-lookup"><span data-stu-id="47449-130">A user logs on to their on-premises environment with their user account (domain\username).</span></span> <span data-ttu-id="47449-131">Microsoft 365 に移行する場合は、職場または学校アカウント (user@domain.com) を使用して再度ログオンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="47449-131">When they go to Microsoft 365, they must log on again with their work or school account (user@domain.com).</span></span> <span data-ttu-id="47449-132">両方の環境で同じユーザー名が指定されています。</span><span class="sxs-lookup"><span data-stu-id="47449-132">The user name is the same in both environments.</span></span> <span data-ttu-id="47449-133">パスワードハッシュ同期またはパススルー認証を追加すると、ユーザーは両方の環境で同じパスワードを使用しますが、Microsoft 365 にログオンするときにこれらの資格情報を再度提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47449-133">When you add password hash sync or pass-through authentication, the user has the same password for both environments, but will have to provide those credentials again when logging on to Microsoft 365.</span></span> <span data-ttu-id="47449-134">ディレクトリ同期とパスワードハッシュ同期は、最も一般的に使用されるディレクトリ同期のシナリオです。</span><span class="sxs-lookup"><span data-stu-id="47449-134">Directory synchronization with password hash sync is the most commonly used directory sync scenario.</span></span>

<span data-ttu-id="47449-135">ディレクトリ同期をセットアップするには、Azure Active Directory Connect を使用します。</span><span class="sxs-lookup"><span data-stu-id="47449-135">To set up directory synchronization, use Azure Active Directory Connect.</span></span> <span data-ttu-id="47449-136">手順については、「 [Microsoft 365 のディレクトリ同期をセットアップする](set-up-directory-synchronization.md)」と「 [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47449-136">For instructions, read [Set up directory synchronization for Microsoft 365](set-up-directory-synchronization.md), and [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537).</span></span>

<span data-ttu-id="47449-137">[Microsoft 365 へのディレクトリ同期の準備](prepare-for-directory-synchronization.md)と[オンプレミスの統合](https://go.microsoft.com/fwlink/?LinkId=518101)の詳細については、「Azure Active directory」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47449-137">Learn more about [preparing for directory synchronization to Microsoft 365](prepare-for-directory-synchronization.md) and [integrating your on-premises identifies with Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).</span></span>

### <a name="directory-synchronization-with-sso"></a><span data-ttu-id="47449-138">SSO を使用したディレクトリ同期</span><span class="sxs-lookup"><span data-stu-id="47449-138">Directory synchronization with SSO</span></span>

<span data-ttu-id="47449-139">ユーザーが自分のユーザーアカウントを使用してオンプレミス環境にログオンします。</span><span class="sxs-lookup"><span data-stu-id="47449-139">A user logs on to their on-premises environment with their user account.</span></span> <span data-ttu-id="47449-140">Microsoft 365 に移行すると、それらのユーザーは自動的にログオンするか、オンプレミス環境 (domain\username) に使用したものと同じ資格情報を使用してログオンします。</span><span class="sxs-lookup"><span data-stu-id="47449-140">When they go to Microsoft 365, they are either logged on automatically, or they log on using the same credentials they use for their on-premises environment (domain\username).</span></span>

<span data-ttu-id="47449-141">SSO をセットアップするには、Azure AD Connect も使用します。</span><span class="sxs-lookup"><span data-stu-id="47449-141">To set up SSO you also use Azure AD Connect.</span></span> <span data-ttu-id="47449-142">手順については、「 [AZURE AD Connect のカスタムインストール](https://go.microsoft.com/fwlink/p/?LinkID=698430)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47449-142">For instructions, read [Custom installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkID=698430).</span></span>

<span data-ttu-id="47449-143">[Azure Active Directory でのアプリケーションへのシングルサインオン](https://go.microsoft.com/fwlink/p/?LinkId=698604)の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="47449-143">Learn more about [single sign-on to applications in Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>

## <a name="azure-ad-connect"></a><span data-ttu-id="47449-144">Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="47449-144">Azure AD Connect</span></span>

<span data-ttu-id="47449-145">Azure AD Connect は、DirSync、Azure AD Sync などの id 統合ツールの以前のバージョンに置き換えられました。詳細については、「 [Azure Active Directory でのハイブリッド id とは](https://go.microsoft.com/fwlink/p/?LinkId=527969)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47449-145">Azure AD Connect replaces older versions of identity integration tools such as DirSync and Azure AD Sync. For more information, see [What is hybrid identity with Azure Active Directory?](https://go.microsoft.com/fwlink/p/?LinkId=527969).</span></span> <span data-ttu-id="47449-146">Azure Active Directory 同期から Azure AD Connect に更新する場合は、[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47449-146">If you want to update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span> 

<span data-ttu-id="47449-147">「 [Deploy microsoft 365 Directory Synchronization In Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887)」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="47449-147">Also see [Deploy Microsoft 365 Directory Synchronization in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).</span></span>

## <a name="see-also"></a><span data-ttu-id="47449-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="47449-148">See also</span></span>

[<span data-ttu-id="47449-149">Microsoft 365 Enterprise の概要</span><span class="sxs-lookup"><span data-stu-id="47449-149">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
