---
title: オンプレミス環境と office 365 の統合
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Office 365 を既存のディレクトリ サービスに統合する方法について説明します。
ms.openlocfilehash: b660dda74303a3bf0fa92bc8e3146cd2c9add662
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541674"
---
# <a name="office-365-integration-with-on-premises-environments"></a><span data-ttu-id="b7cdd-103">オンプレミス環境と office 365 の統合</span><span class="sxs-lookup"><span data-stu-id="b7cdd-103">Office 365 integration with on-premises environments</span></span>

<span data-ttu-id="b7cdd-104">ビジネス サーバー 2015、または SharePoint Server 2013 は、既存のディレクトリ サービスおよび Exchange Server、Skype のオンプレミスのインストールと Office 365 を統合できます。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-104">You can integrate Office 365 with your existing directory services and with an on-premises installation of Exchange Server, Skype for Business Server 2015, or SharePoint Server 2013.</span></span>
  
 - <span data-ttu-id="b7cdd-p101">ディレクトリ サービスと統合するときに同期し、両方の環境のユーザー アカウントを管理できます。追加することもパスワード ハッシュの同期またはシングル サインオン (SSO) のユーザーがログオンできるように、設置型の資格情報を持つ両方の環境にします。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-p101">When you integrate with directory services, you can synchronize and manage user accounts for both environments. You can also add password hash synchronization or single sign-on (SSO) so users can log on to both environments with their on-premises credentials.</span></span>
 - <span data-ttu-id="b7cdd-p102">オンプレミスのサーバー製品と統合する場合に、ハイブリッド環境を作成します。ハイブリッド環境は、ユーザーや情報を Office 365 に移行するか、一部のユーザーまたはいくつかについては、オンプレミスとクラウドの一部を続行するようにできます。ハイブリッド環境の詳細については、 [Office 365 のハイブリッド クラウド ソリューションの概要](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-p102">When you integrate with on-premises server products, you create a hybrid environment. A hybrid environment can help as you migrate users or information to Office 365, or you can continue to have some users or some information on-premises and some in the cloud. For more information about hybrid environments, see [Office 365 hybrid cloud solutions overview](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).</span></span>

<span data-ttu-id="b7cdd-110">Azure AD アドバイザーは、カスタマイズされたセットアップ ガイドのも使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-110">You can also use the Azure AD advisors for customized setup guidance:</span></span>
- [<span data-ttu-id="b7cdd-111">Azure AD 接続アドバイザー</span><span class="sxs-lookup"><span data-stu-id="b7cdd-111">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
- [<span data-ttu-id="b7cdd-112">AD FS 展開アドバイザー</span><span class="sxs-lookup"><span data-stu-id="b7cdd-112">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
- [<span data-ttu-id="b7cdd-113">Azure の RMS の展開ウィザード</span><span class="sxs-lookup"><span data-stu-id="b7cdd-113">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
- [<span data-ttu-id="b7cdd-114">Azure AD プレミアム セットアップ ガイド</span><span class="sxs-lookup"><span data-stu-id="b7cdd-114">Azure AD Premium setup guidance</span></span>](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a><span data-ttu-id="b7cdd-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="b7cdd-115">Before you begin</span></span>
<span data-ttu-id="b7cdd-p103">Office 365 と設置環境を統合すると、前に、[ネットワークの計画と Office 365 のパフォーマンスの調整](network-planning-and-performance.md)に参加する必要があります。Office 365 で利用可能な[識別情報モデル](about-office-365-identity.md)を理解するができます。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-p103">Before you integrate Office 365 and an on-premises environment, you also need to attend to [network planning and performance tuning for Office 365](network-planning-and-performance.md). You will also want to understand the available [identity models](about-office-365-identity.md) in Office 365.</span></span> 

<span data-ttu-id="b7cdd-118">[アカウントを Office 365 のユーザーを管理するのには、](manage-office-365-accounts.md) Office 365 ユーザー アカウントとアカウントを管理するために使用できるツールの一覧についてを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-118">See [where to manage Office 365 user accounts](manage-office-365-accounts.md) for a list of tools you can use to manage Office 365 users and accounts.</span></span> 
  
## <a name="integrate-office-365-with-directory-services"></a><span data-ttu-id="b7cdd-119">Office 365 ディレクトリ サービスと統合します。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-119">Integrate Office 365 with directory services</span></span>
<span data-ttu-id="b7cdd-p104">設置ディレクトリに既存のユーザー アカウントがあれば、すべての Office 365 との違いや環境間でのエラーを導入することのリスクでこれらのアカウントを再作成したくないです。ディレクトリ同期、オンラインの間でそれらのアカウントをミラー化することが、オンプレミス環境です。ディレクトリ同期によって、ユーザーは、環境ごとに新しい情報を記憶する必要はありません、作成またはアカウントを 2 回更新する必要はありません。ディレクトリ同期のため[のオンプレミス ディレクトリの準備](prepare-for-directory-synchronization.md)をする必要がありますは手動でまたは[IdFix ツール](install-and-run-idfix.md)(IdFix ツールでのみ機能する Active Directory) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-p104">If you have existing user accounts in an on-premises directory, you don't want to re-create all of those accounts in Office 365 and risk introducing differences or errors between the environments. Directory synchronization helps you mirror those accounts between your online and on-premises environments. With directory synchronization, your users don't have to remember new information for each environment, and you don't have to create or update accounts twice. You will need to [prepare your on-premises directory](prepare-for-directory-synchronization.md) for directory synchronization, you can do this manually or use the [IdFix tool](install-and-run-idfix.md) (IdFix tool only works with Active Directory).</span></span> 
  
![ディレクトリ同期を使用して、設置し、オンラインのユーザー アカウント情報を同期させる](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
<span data-ttu-id="b7cdd-p105">ユーザーが Office 365 の設置型の資格情報でログオンできる場合は、SSO を構成することもできます。SSO では、Office 365 は、オンプレミス環境にユーザーの認証を信頼するように構成します。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-p105">If you want users to be able to log on to Office 365 with their on-premises credentials, you can also configure SSO. With SSO, Office 365 is configured to trust the on-premises environment for user authentication.</span></span>
  
![シングル サインオンで、同じアカウントがオンプレミスとオンライン環境の両方で使用可能です](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
<span data-ttu-id="b7cdd-128">別のユーザー アカウント管理の手法は、次の表に示すように、ユーザー エクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-128">Different user account management techniques provide different experiences for your users, as shown in the following table.</span></span>
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a><span data-ttu-id="b7cdd-129">**ディレクトリ同期のパスワード ハッシュの同期またはパススルー認証の有無**</span><span class="sxs-lookup"><span data-stu-id="b7cdd-129">**Directory synchronization with or without password hash synchronization or pass-through authentication**</span></span>
<span data-ttu-id="b7cdd-p106">ユーザーが、ユーザー アカウント (ドメイン \ ユーザー名) に、オンプレミス環境にログオンするとします。Office 365 に移動するとする必要がありますもう一度アカウントでログオン、職場または学校 (user@domain.com)。ユーザー名は、両方の環境で同じです。パスワード ハッシュの同期またはパススルー認証を追加するとユーザーの両方の環境では、同じパスワードが Office 365 にログオンするときに、それらの資格情報を再度入力する必要があります。パスワード ハッシュの同期とのディレクトリ同期は、最も一般的に使用されるディレクトリ同期シナリオです。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-p106">A user logs on to their on-premises environment with their user account (domain\username). When they go to Office 365, they must log on again with their work or school account (user@domain.com). The user name is the same in both environments. When you add password hash sync or pass-through authentication, the user has the same password for both environments, but will have to provide those credentials again when logging on to Office 365. Directory synchronization with password hash sync is the most commonly used directory sync scenario.</span></span>

<span data-ttu-id="b7cdd-p107">ディレクトリ同期をセットアップするには、Azure Active Directory の接続を使用します。手順については、 [Office 365 のディレクトリ同期の設定](set-up-directory-synchronization.md)、および[高速の設定で、Azure を使用して AD 接続](https://go.microsoft.com/fwlink/p/?LinkId=698537)」を参照します。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-p107">To set up directory synchronization, use Azure Active Directory Connect. For instructions, read [Set up directory synchronization for Office 365](set-up-directory-synchronization.md), and [Use Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537).</span></span>

<span data-ttu-id="b7cdd-137">詳細について[Office 365 のディレクトリ同期を使用してユーザーをプロビジョニングするための準備](prepare-for-directory-synchronization.md)と、 [Azure Active Directory で、設置型の識別と統合します](https://go.microsoft.com/fwlink/?LinkId=518101)。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-137">Learn more about [preparing to provision users through directory synchronization to Office 365](prepare-for-directory-synchronization.md) and [integrating your on-premises identifies with Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).</span></span>

### <a name="directory-synchronization-with-sso"></a><span data-ttu-id="b7cdd-138">**SSO とのディレクトリ同期**</span><span class="sxs-lookup"><span data-stu-id="b7cdd-138">**Directory synchronization with SSO**</span></span>
<span data-ttu-id="b7cdd-p108">ユーザーは、オンプレミス環境のユーザー アカウントでログオンします。Office 365 に移動するとと、か、ログオンしている、自動的にまたはの設置環境 (ドメイン \ ユーザー名) を使用して、これらと同じ資格情報を使用してログオンします。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-p108">A user logs on to their on-premises environment with their user account. When they go to Office 365, they are either logged on automatically, or they log on using the same credentials they use for their on-premises environment (domain\username).</span></span>

<span data-ttu-id="b7cdd-p109">SSO を設定するのには、Azure AD 接続も使用します。手順については、[カスタム設定で Azure を使用して AD の接続](https://go.microsoft.com/fwlink/p/?LinkID=698430)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-p109">To set up SSO you also use Azure AD Connect. For instructions, read [Use Azure AD Connect with custom settings](https://go.microsoft.com/fwlink/p/?LinkID=698430).</span></span>

<span data-ttu-id="b7cdd-143">[アプリケーションへのアクセスと Azure Active Directory でのシングル サインオン](https://go.microsoft.com/fwlink/p/?LinkId=698604)の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-143">Learn more about [application access and single sign-on with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>

## <a name="azure-ad-connect"></a><span data-ttu-id="b7cdd-144">Azure AD Connect</span><span class="sxs-lookup"><span data-stu-id="b7cdd-144">Azure AD Connect</span></span>
<span data-ttu-id="b7cdd-p110">Azure AD 接続には、ディレクトリ同期、Azure AD 同期などの id の統合ツールの以前のバージョンが置き換えられます。詳細については[、オンプレミス ユーザーは、Azure Active Directory との統合](https://go.microsoft.com/fwlink/p/?LinkId=527969)」を参照してください。Azure Active Directory 同期から Azure AD 接続へ更新する場合は、[アップグレードの手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)を参照してください。[Office 365 ディレクトリ同期 (DirSync) で、Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887)用に作成されたソリューションのアーキテクチャを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7cdd-p110">Azure AD Connect replaces older versions of identity integration tools such as DirSync and Azure AD Sync. For more information, see [Integrating your on-premises identities with Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969). If you want to update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240). See a solution architecture built for [Office 365 Directory Synchronization (DirSync) in Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).</span></span>