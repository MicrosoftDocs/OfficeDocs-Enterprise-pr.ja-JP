---
title: Azure と Office 365 との統合
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
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Office 365 サブスクリプションには、Azure AD へのサブスクリプションが含まれています。 オンプレミス環境でパスワード同期またはシングルサインオンを行う場合は、Office 365 を Azure AD と統合します。
ms.openlocfilehash: 44231420ee92c37f14874d6fb0f9e926d8d4369d
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "38745790"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="9c1cb-104">Azure と Office 365 との統合</span><span class="sxs-lookup"><span data-stu-id="9c1cb-104">Azure integration with Office 365</span></span>

<span data-ttu-id="9c1cb-105">*この記事は、Office 365 Enterprise と Microsoft 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="9c1cb-105">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="9c1cb-106">Office 365 では、Azure Active Directory (Azure AD) を使用して、バックグラウンドでユーザー id を管理しています。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-106">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes.</span></span> <span data-ttu-id="9c1cb-107">Office 365 サブスクリプションには Azure AD への無料サブスクリプションが含まれているため、Office 365 を Azure ad に統合できます。これにより、パスワードを同期したり、シングルサインオンをオンプレミスの環境でセットアップしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-107">Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment.</span></span> <span data-ttu-id="9c1cb-108">また、高度な機能を購入してアカウントをより適切に管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-108">You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="9c1cb-109">Azure では、Office 365 のサブスクリプションを拡張およびカスタマイズするために使用できる、統合アプリの管理などのその他の機能も提供されています。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-109">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="9c1cb-110">ガイド付きのセットアップと構成の機能を実現するために、Azure AD 展開アドバイザーを使用することができます (Office 365 にサインインする必要があります)。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-110">You can use the Azure AD deployment advisors for a guided setup and configuration experience (you must be signed in to Office 365):</span></span>

 - [<span data-ttu-id="9c1cb-111">Azure AD Connect advisor</span><span class="sxs-lookup"><span data-stu-id="9c1cb-111">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="9c1cb-112">AD FS 展開アドバイザー</span><span class="sxs-lookup"><span data-stu-id="9c1cb-112">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="9c1cb-113">Azure AD Premium セットアップガイド</span><span class="sxs-lookup"><span data-stu-id="9c1cb-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="9c1cb-114">Azure AD エディションおよび Office 365 id 管理</span><span class="sxs-lookup"><span data-stu-id="9c1cb-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="9c1cb-115">Office 365 への有料サブスクリプションを所有している場合は、Azure AD への無料サブスクリプションも用意されています。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-115">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD.</span></span> <span data-ttu-id="9c1cb-116">Azure AD を使用して、ユーザーアカウントとグループアカウントを作成および管理できます。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-116">You can use Azure AD to create and manage user and group accounts.</span></span> <span data-ttu-id="9c1cb-117">このサブスクリプションをアクティブ化するには、1回限りの登録を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-117">To activate this subscription you have to complete a one-time registration.</span></span> <span data-ttu-id="9c1cb-118">その後、Office 365 管理ポータルから Azure AD にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-118">Afterward, you can access Azure AD from your Office 365 admin portal.</span></span> 

<span data-ttu-id="9c1cb-119">手順については、「 [Free AZURE AD サブスクリプションを使用する](https://go.microsoft.com/fwlink/p/?LinkId=617127)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-119">For instructions, see [use your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> <span data-ttu-id="9c1cb-120">指示に従って、Office 365 のサブスクリプションに同梱されている無料の Azure AD サブスクリプションを登録します。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-120">Follow the instructions to register the free Azure AD subscription that comes with your subscription to Office 365.</span></span> <span data-ttu-id="9c1cb-121">Azure.microsoft.com に直接アクセスしないと、Office 365 の無料のサブスクリプションとは別の、Microsoft Azure の試用版または有料版サブスクリプションが作成されることになります。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-121">Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="9c1cb-122">無料サブスクリプションを使用すると、オンプレミスのディレクトリと同期したり、シングルサインオンを設定したり、複数のソフトウェアとサービスアプリケーション (Salesforce、DropBox など) を同期したりできます。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="9c1cb-123">拡張された Active Directory ドメインサービス (AD DS) 機能、双方向同期、およびその他の管理機能が必要な場合は、無料のサブスクリプションを有料プレミアムサブスクリプションにアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-123">If you want enhanced Active Directory Domain Services (AD DS) functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription.</span></span> <span data-ttu-id="9c1cb-124">詳細については、「 [Azure Active Directory のエディション](https://azure.microsoft.com/pricing/details/active-directory/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-124">For details see [Azure Active Directory editions](https://azure.microsoft.com/pricing/details/active-directory/).</span></span>
  
<span data-ttu-id="9c1cb-125">Office 365 と Azure AD の詳細については、「 [office 365 id と Azure Active Directory](https://docs.microsoft.com/office365/enterprise/about-office-365-identity)について」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://docs.microsoft.com/office365/enterprise/about-office-365-identity).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="9c1cb-126">Office 365 テナントの機能を拡張する</span><span class="sxs-lookup"><span data-stu-id="9c1cb-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="9c1cb-127">**機能**</span><span class="sxs-lookup"><span data-stu-id="9c1cb-127">**Feature**</span></span>|<span data-ttu-id="9c1cb-128">**説明**</span><span class="sxs-lookup"><span data-stu-id="9c1cb-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="9c1cb-129">統合アプリ</span><span class="sxs-lookup"><span data-stu-id="9c1cb-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="9c1cb-130">Office 365 データ (メール、予定表、連絡先、ユーザー、グループ、ファイル、フォルダーなど) へのアクセスを個別のアプリに許可できます。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-130">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders.</span></span> <span data-ttu-id="9c1cb-131">また、グローバル管理者レベルでこれらのアプリを承認し、Azure AD にアプリを登録することにより、会社全体でそれらを利用できるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-131">You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD.</span></span> <span data-ttu-id="9c1cb-132">詳細については[、「Office 365 管理者向けの統合アプリと AZURE AD」を](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-132">For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span></span>  <br/> <span data-ttu-id="9c1cb-133">また、「[アプリケーションへのシングルサインオン](https://go.microsoft.com/fwlink/p/?LinkId=698604)」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-133">Also see [single sign-on to applications](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="9c1cb-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="9c1cb-134">PowerApps</span></span>  <br/> | <span data-ttu-id="9c1cb-135">Power apps は、SharePoint リストなどの既存のデータソースやその他のデータアプリに接続できるモバイルデバイス用の注目アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-135">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps.</span></span> <span data-ttu-id="9c1cb-136">詳細については、「SharePoint Online および[PowerApps ページ](https://powerapps.microsoft.com/)[でリストの Powerapp を作成する](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-136">See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>  <br/> |
   
<span data-ttu-id="9c1cb-137">詳細については、「Office 365 管理者および[azure ad アプリケーションギャラリーとシングルサインオン](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)[の統合アプリおよび azure ad](integrated-apps-and-azure-ads.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c1cb-137">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

## <a name="see-also"></a><span data-ttu-id="9c1cb-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c1cb-138">See also</span></span>

[<span data-ttu-id="9c1cb-139">Microsoft 365 Enterprise の概要</span><span class="sxs-lookup"><span data-stu-id="9c1cb-139">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
