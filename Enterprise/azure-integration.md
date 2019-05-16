---
title: Azure と Office 365 との統合
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
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
ms.openlocfilehash: 51ed71aa94bc5317d9b5ff76d0aa6af2762c429e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068223"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="c190c-104">Azure と Office 365 との統合</span><span class="sxs-lookup"><span data-stu-id="c190c-104">Azure integration with Office 365</span></span>

<span data-ttu-id="c190c-105">Office 365 では、Azure Active Directory (Azure AD) を使用して、バックグラウンドでユーザー id を管理しています。</span><span class="sxs-lookup"><span data-stu-id="c190c-105">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes.</span></span> <span data-ttu-id="c190c-106">Office 365 サブスクリプションには Azure AD への無料サブスクリプションが含まれているため、Office 365 を Azure ad に統合できます。これにより、パスワードを同期したり、シングルサインオンをオンプレミスの環境でセットアップしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="c190c-106">Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment.</span></span> <span data-ttu-id="c190c-107">また、高度な機能を購入してアカウントをより適切に管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="c190c-107">You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="c190c-108">Azure では、Office 365 のサブスクリプションを拡張およびカスタマイズするために使用できる、統合アプリの管理などのその他の機能も提供されています。</span><span class="sxs-lookup"><span data-stu-id="c190c-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="c190c-109">ガイド付きセットアップおよび構成の手順には、Azure AD 展開アドバイザーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c190c-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience:</span></span>
 - [<span data-ttu-id="c190c-110">Azure AD Connect advisor</span><span class="sxs-lookup"><span data-stu-id="c190c-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="c190c-111">AD FS 展開アドバイザー</span><span class="sxs-lookup"><span data-stu-id="c190c-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="c190c-112">Azure RMS 展開ウィザード</span><span class="sxs-lookup"><span data-stu-id="c190c-112">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
 - [<span data-ttu-id="c190c-113">Azure AD Premium セットアップガイド</span><span class="sxs-lookup"><span data-stu-id="c190c-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="c190c-114">Azure AD エディションおよび Office 365 id 管理</span><span class="sxs-lookup"><span data-stu-id="c190c-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="c190c-115">Office 365 への有料サブスクリプションを所有している場合は、Azure AD への無料サブスクリプションも用意されています。</span><span class="sxs-lookup"><span data-stu-id="c190c-115">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD.</span></span> <span data-ttu-id="c190c-116">Azure AD を使用して、ユーザーアカウントとグループアカウントを作成および管理できます。</span><span class="sxs-lookup"><span data-stu-id="c190c-116">You can use Azure AD to create and manage user and group accounts.</span></span> <span data-ttu-id="c190c-117">このサブスクリプションをアクティブ化するには、1回限りの登録を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c190c-117">To activate this subscription you have to complete a one-time registration.</span></span> <span data-ttu-id="c190c-118">その後、Office 365 管理ポータルから Azure AD にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c190c-118">Afterward, you can access Azure AD from your Office 365 admin portal.</span></span> <span data-ttu-id="c190c-119">手順については、「 [AZURE AD サブスクリプションを登録する](https://go.microsoft.com/fwlink/p/?LinkId=617127)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c190c-119">For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="c190c-120">上記の手順に従って、Office 365 のサブスクリプションに同梱されている無料の Azure AD サブスクリプションを登録します。</span><span class="sxs-lookup"><span data-stu-id="c190c-120">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365.</span></span> <span data-ttu-id="c190c-121">Azure.microsoft.com に直接アクセスしないと、Office 365 の無料のサブスクリプションとは別の、Microsoft Azure の試用版または有料版サブスクリプションが作成されることになります。</span><span class="sxs-lookup"><span data-stu-id="c190c-121">Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="c190c-122">無料サブスクリプションを使用すると、オンプレミスのディレクトリと同期したり、シングルサインオンを設定したり、複数のソフトウェアとサービスアプリケーション (Salesforce、DropBox など) を同期したりできます。</span><span class="sxs-lookup"><span data-stu-id="c190c-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="c190c-123">拡張された AD DS 機能、双方向同期、およびその他の管理機能が必要な場合は、無料のサブスクリプションを有料プレミアムサブスクリプションにアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="c190c-123">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription.</span></span> <span data-ttu-id="c190c-124">詳細については、「 [Azure Active Directory のエディション](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c190c-124">For details see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span></span>
  
<span data-ttu-id="c190c-125">Office 365 と Azure AD の詳細については、「 [office 365 id と Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9)について」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c190c-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="c190c-126">Office 365 テナントの機能を拡張する</span><span class="sxs-lookup"><span data-stu-id="c190c-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="c190c-127">**機能**</span><span class="sxs-lookup"><span data-stu-id="c190c-127">**Feature**</span></span>|<span data-ttu-id="c190c-128">**説明**</span><span class="sxs-lookup"><span data-stu-id="c190c-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c190c-129">統合アプリ</span><span class="sxs-lookup"><span data-stu-id="c190c-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="c190c-130">Office 365 データ (メール、予定表、連絡先、ユーザー、グループ、ファイル、フォルダーなど) へのアクセスを個別のアプリに許可できます。</span><span class="sxs-lookup"><span data-stu-id="c190c-130">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders.</span></span> <span data-ttu-id="c190c-131">また、グローバル管理者レベルでこれらのアプリを承認し、Azure AD にアプリを登録することにより、会社全体でそれらを利用できるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c190c-131">You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD.</span></span> <span data-ttu-id="c190c-132">詳細については[、「Office 365 管理者向けの統合アプリと AZURE AD」を](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)参照してください。</span><span class="sxs-lookup"><span data-stu-id="c190c-132">For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).</span></span>  <br/> <span data-ttu-id="c190c-133">[AZURE AD アプリケーションギャラリーおよびシングルサインオン](https://go.microsoft.com/fwlink/p/?LinkId=698604)も参照してください。</span><span class="sxs-lookup"><span data-stu-id="c190c-133">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="c190c-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="c190c-134">PowerApps</span></span>  <br/> | <span data-ttu-id="c190c-135">Power apps は、SharePoint リストなどの既存のデータソースやその他のデータアプリに接続できるモバイルデバイス用の注目アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="c190c-135">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps.</span></span> <span data-ttu-id="c190c-136">詳細については、「SharePoint Online および[PowerApps ページ](https://powerapps.microsoft.com/)[でリストの Powerapp を作成する](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c190c-136">See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>  <br/> |
   
<span data-ttu-id="c190c-137">Microsoft Cloud および Office 365 に関するその他のリソースについては、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c190c-137">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="c190c-138">エンタープライズ アーキテクトのための Microsoft クラウド ID</span><span class="sxs-lookup"><span data-stu-id="c190c-138">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [<span data-ttu-id="c190c-139">Microsoft Azure での Office 365 ディレクトリ同期 (DirSync) の展開</span><span class="sxs-lookup"><span data-stu-id="c190c-139">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

<span data-ttu-id="c190c-140">詳細については、「Office 365 管理者および[azure ad アプリケーションギャラリーとシングルサインオン](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)[の統合アプリおよび azure Ad](integrated-apps-and-azure-ads.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c190c-140">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

### <a name="power-apps"></a><span data-ttu-id="c190c-141">パワーアプリ</span><span class="sxs-lookup"><span data-stu-id="c190c-141">Power Apps</span></span>
<span data-ttu-id="c190c-142">Power apps は、SharePoint リストなどの既存のデータソースやその他のデータアプリに接続できるモバイルデバイス用の注目アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="c190c-142">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps.</span></span> <span data-ttu-id="c190c-143">詳細については、「SharePoint Online および[PowerApps ページ](https://powerapps.microsoft.com/)[でリストの Powerapp を作成する](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c190c-143">See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>