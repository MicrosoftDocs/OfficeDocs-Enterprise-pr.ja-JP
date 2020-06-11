---
title: Microsoft 365 との Azure の統合
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/09/2019
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Microsoft 365 サブスクリプションには、Azure AD へのサブスクリプションが含まれています。 オンプレミス環境でのパスワード同期またはシングルサインオンを行う場合は、Microsoft 365 を Azure AD と統合します。
ms.openlocfilehash: ca38a7a8d5878c6efad228595cf2929650a5c869
ms.sourcegitcommit: ff1d21fe5eb8eba7a65d250aa37aadc8f503a10a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2020
ms.locfileid: "44698894"
---
# <a name="azure-integration-with-microsoft-365"></a><span data-ttu-id="29236-104">Microsoft 365 との Azure の統合</span><span class="sxs-lookup"><span data-stu-id="29236-104">Azure integration with Microsoft 365</span></span>

<span data-ttu-id="29236-105">*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="29236-105">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="29236-106">Microsoft 365 では、Azure Active Directory (Azure AD) を使用して、バックグラウンドでユーザー id を管理しています。</span><span class="sxs-lookup"><span data-stu-id="29236-106">Microsoft 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes.</span></span> <span data-ttu-id="29236-107">Microsoft 365 サブスクリプションには、Azure AD への無料サブスクリプションが含まれているため、Microsoft 365 を Azure ad に統合できます。これにより、パスワードを同期したり、シングルサインオンをオンプレミス環境でセットアップしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="29236-107">Your Microsoft 365 subscription includes a free subscription to Azure AD so that you can integrate Microsoft 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment.</span></span> <span data-ttu-id="29236-108">また、高度な機能を購入してアカウントをより適切に管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="29236-108">You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="29236-109">Azure では、Microsoft 365 サブスクリプションの拡張とカスタマイズに使用できる統合アプリの管理などのその他の機能も提供しています。</span><span class="sxs-lookup"><span data-stu-id="29236-109">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Microsoft 365 subscriptions.</span></span>
  
<span data-ttu-id="29236-110">ガイド付きのセットアップと構成の機能を実現するために、Azure AD 展開アドバイザーを使用することができます (Microsoft 365 にサインインする必要があります)。</span><span class="sxs-lookup"><span data-stu-id="29236-110">You can use the Azure AD deployment advisors for a guided setup and configuration experience (you must be signed in to Microsoft 365):</span></span>

 - [<span data-ttu-id="29236-111">Azure AD Connect advisor</span><span class="sxs-lookup"><span data-stu-id="29236-111">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="29236-112">AD FS 展開アドバイザー</span><span class="sxs-lookup"><span data-stu-id="29236-112">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="29236-113">Azure AD Premium セットアップガイド</span><span class="sxs-lookup"><span data-stu-id="29236-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a><span data-ttu-id="29236-114">Azure AD エディションと Microsoft 365 id 管理</span><span class="sxs-lookup"><span data-stu-id="29236-114">Azure AD editions and Microsoft 365 identity management</span></span>

<span data-ttu-id="29236-115">Microsoft 365 への有料サブスクリプションを保有している場合は、Azure AD への無料サブスクリプションも用意されています。</span><span class="sxs-lookup"><span data-stu-id="29236-115">If you have a paid subscription to Microsoft 365, you also have a free subscription to Azure AD.</span></span> <span data-ttu-id="29236-116">Azure AD を使用して、ユーザーアカウントとグループアカウントを作成および管理できます。</span><span class="sxs-lookup"><span data-stu-id="29236-116">You can use Azure AD to create and manage user and group accounts.</span></span> <span data-ttu-id="29236-117">このサブスクリプションをアクティブ化するには、1回限りの登録を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29236-117">To activate this subscription you have to complete a one-time registration.</span></span> <span data-ttu-id="29236-118">その後、Microsoft 365 管理センターから Azure AD にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="29236-118">Afterward, you can access Azure AD from your Microsoft 365 admin center.</span></span> 

<span data-ttu-id="29236-119">手順については、「 [Free AZURE AD サブスクリプションを使用する](https://go.microsoft.com/fwlink/p/?LinkId=617127)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29236-119">For instructions, see [use your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> <span data-ttu-id="29236-120">指示に従って、Microsoft 365 へのサブスクリプションに同梱されている無料の Azure AD サブスクリプションを登録します。</span><span class="sxs-lookup"><span data-stu-id="29236-120">Follow the instructions to register the free Azure AD subscription that comes with your subscription to Microsoft 365.</span></span> <span data-ttu-id="29236-121">Azure.microsoft.com に直接アクセスしてサインアップしないでください。 microsoft Azure の試用版または有料版サブスクリプションを使用して、Microsoft 365 の無料のサブスクリプションとは別のものにすることができます。</span><span class="sxs-lookup"><span data-stu-id="29236-121">Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Microsoft 365.</span></span> 
  
<span data-ttu-id="29236-122">無料サブスクリプションを使用すると、オンプレミスのディレクトリと同期したり、シングルサインオンを設定したり、複数のソフトウェアとサービスアプリケーション (Salesforce、DropBox など) を同期したりできます。</span><span class="sxs-lookup"><span data-stu-id="29236-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="29236-123">拡張された Active Directory ドメインサービス (AD DS) 機能、双方向同期、およびその他の管理機能が必要な場合は、無料のサブスクリプションを有料プレミアムサブスクリプションにアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="29236-123">If you want enhanced Active Directory Domain Services (AD DS) functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription.</span></span> <span data-ttu-id="29236-124">詳細については、「 [Azure Active Directory のエディション](https://azure.microsoft.com/pricing/details/active-directory/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29236-124">For details see [Azure Active Directory editions](https://azure.microsoft.com/pricing/details/active-directory/).</span></span>
  
<span data-ttu-id="29236-125">Microsoft 365 と Azure AD の詳細については、「 [microsoft 365 Identity と Azure Active Directory](about-office-365-identity.md)について」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29236-125">For more information about Microsoft 365 and Azure AD, see [Understanding Microsoft 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a><span data-ttu-id="29236-126">Microsoft 365 テナントの機能を拡張する</span><span class="sxs-lookup"><span data-stu-id="29236-126">Extend the capabilities of your Microsoft 365 tenant</span></span>

|<span data-ttu-id="29236-127">**機能**</span><span class="sxs-lookup"><span data-stu-id="29236-127">**Feature**</span></span>|<span data-ttu-id="29236-128">**説明**</span><span class="sxs-lookup"><span data-stu-id="29236-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="29236-129">統合アプリ</span><span class="sxs-lookup"><span data-stu-id="29236-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="29236-130">メール、予定表、連絡先、ユーザー、グループ、ファイル、およびフォルダーなど、Microsoft 365 データへの個別のアプリのアクセスを許可することができます。</span><span class="sxs-lookup"><span data-stu-id="29236-130">You can grant individual apps access to your Microsoft 365 data, like mail, calendars, contacts, users, groups, files, and folders.</span></span> <span data-ttu-id="29236-131">また、グローバル管理者レベルでこれらのアプリを承認し、Azure AD にアプリを登録することにより、会社全体でそれらを利用できるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="29236-131">You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD.</span></span> <span data-ttu-id="29236-132">詳細については[、「Microsoft 365 管理者向けの統合アプリと AZURE AD」を](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)参照してください。</span><span class="sxs-lookup"><span data-stu-id="29236-132">For details see [Integrated Apps and Azure AD for Microsoft 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span></span>  <br/> <span data-ttu-id="29236-133">また、「[アプリケーションへのシングルサインオン](https://go.microsoft.com/fwlink/p/?LinkId=698604)」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="29236-133">Also see [single sign-on to applications](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="29236-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="29236-134">PowerApps</span></span>  <br/> | <span data-ttu-id="29236-135">Power apps は、SharePoint リストなどの既存のデータソースやその他のデータアプリに接続できるモバイルデバイス用の注目アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="29236-135">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps.</span></span> <span data-ttu-id="29236-136">詳細については、「SharePoint Online および[PowerApps ページ](https://powerapps.microsoft.com/)[でリストの Powerapp を作成する](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29236-136">See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>  <br/> |
   
<span data-ttu-id="29236-137">詳細については、「Microsoft 365 管理者と[azure ad アプリケーションギャラリーおよびシングルサインオン](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)[の統合アプリと azure ad](integrated-apps-and-azure-ads.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29236-137">Learn more at [Integrated Apps and Azure AD for Microsoft 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

## <a name="see-also"></a><span data-ttu-id="29236-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="29236-138">See also</span></span>

[<span data-ttu-id="29236-139">Microsoft 365 Enterprise の概要</span><span class="sxs-lookup"><span data-stu-id="29236-139">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
