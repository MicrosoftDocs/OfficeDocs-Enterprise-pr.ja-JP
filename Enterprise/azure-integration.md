---
title: Office 365 での Azure 統合
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
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
description: Office 365 サブスクリプションには、Azure AD へのサブスクリプションが含まれています。オンプレミス環境でパスワード同期またはシングルサインオンを行う場合は、Office 365 を Azure AD と統合します。
ms.openlocfilehash: 0ad1c064d2ffe29f0f06e1368cd728d8b3bd630b
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085476"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="67867-104">Office 365 での Azure 統合</span><span class="sxs-lookup"><span data-stu-id="67867-104">Azure integration with Office 365</span></span>

<span data-ttu-id="67867-p102">Office 365 では、azure Active Directory (azure AD) を使用して、バックグラウンドでユーザー id を管理しています。office 365 サブスクリプションには azure ad への無料サブスクリプションが含まれているため、office 365 を azure ad に統合できます。これにより、パスワードを同期したり、シングルサインオンをオンプレミスの環境でセットアップしたりすることができます。また、高度な機能を購入してアカウントをより適切に管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="67867-p102">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="67867-108">Azure では、Office 365 のサブスクリプションを拡張およびカスタマイズするために使用できる、統合アプリの管理などのその他の機能も提供されています。</span><span class="sxs-lookup"><span data-stu-id="67867-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="67867-109">ガイド付きセットアップおよび構成の手順には、Azure AD 展開アドバイザーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="67867-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience:</span></span>
 - [<span data-ttu-id="67867-110">Azure AD Connect advisor</span><span class="sxs-lookup"><span data-stu-id="67867-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="67867-111">AD FS 展開アドバイザー</span><span class="sxs-lookup"><span data-stu-id="67867-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="67867-112">Azure RMS 展開ウィザード</span><span class="sxs-lookup"><span data-stu-id="67867-112">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
 - [<span data-ttu-id="67867-113">Azure AD Premium セットアップガイド</span><span class="sxs-lookup"><span data-stu-id="67867-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="67867-114">Azure AD エディションおよび Office 365 id 管理</span><span class="sxs-lookup"><span data-stu-id="67867-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="67867-p103">Office 365 への有料サブスクリプションを所有している場合は、Azure AD への無料サブスクリプションも用意されています。Azure AD を使用して、ユーザーアカウントとグループアカウントを作成および管理できます。このサブスクリプションをアクティブ化するには、1回限りの登録を完了する必要があります。その後、Office 365 管理ポータルから Azure AD にアクセスできます。手順については、「 [Azure AD サブスクリプションを登録する](https://go.microsoft.com/fwlink/p/?LinkId=617127)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67867-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="67867-p104">上記の手順に従って、Office 365 のサブスクリプションに同梱されている無料の Azure AD サブスクリプションを登録します。azure.microsoft.com に直接アクセスしないと、Office 365 の無料のサブスクリプションとは別の、microsoft azure の試用版または有料版サブスクリプションが作成されることになります。</span><span class="sxs-lookup"><span data-stu-id="67867-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="67867-122">無料サブスクリプションを使用すると、オンプレミスのディレクトリと同期したり、シングルサインオンを設定したり、複数のソフトウェアとサービスアプリケーション (Salesforce、DropBox など) を同期したりできます。</span><span class="sxs-lookup"><span data-stu-id="67867-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="67867-p105">拡張された AD DS 機能、双方向同期、およびその他の管理機能が必要な場合は、無料のサブスクリプションを有料プレミアムサブスクリプションにアップグレードできます。詳細については、「 [Azure Active Directory のエディション](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67867-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span></span>
  
<span data-ttu-id="67867-125">office 365 と azure AD の詳細については、「 [office 365 id と azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9)について」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67867-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="67867-126">Office 365 テナントの機能を拡張する</span><span class="sxs-lookup"><span data-stu-id="67867-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="67867-127">**機能**</span><span class="sxs-lookup"><span data-stu-id="67867-127">**Feature**</span></span>|<span data-ttu-id="67867-128">**説明**</span><span class="sxs-lookup"><span data-stu-id="67867-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="67867-129">統合アプリ</span><span class="sxs-lookup"><span data-stu-id="67867-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="67867-p106">Office 365 データ (メール、予定表、連絡先、ユーザー、グループ、ファイル、フォルダーなど) へのアクセスを個別のアプリに許可できます。また、グローバル管理者レベルでこれらのアプリを承認し、Azure AD にアプリを登録することにより、会社全体でそれらを利用できるようにすることもできます。詳細については[、「Office 365 管理者向けの統合アプリと Azure AD」を](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)参照してください。</span><span class="sxs-lookup"><span data-stu-id="67867-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="67867-133">[Azure AD アプリケーションギャラリーおよびシングルサインオン](https://go.microsoft.com/fwlink/p/?LinkId=698604)も参照してください。</span><span class="sxs-lookup"><span data-stu-id="67867-133">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="67867-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="67867-134">PowerApps</span></span>  <br/> | <span data-ttu-id="67867-p107">Power apps は、SharePoint リストなどの既存のデータソースやその他のデータアプリに接続できるモバイルデバイス用の注目アプリケーションです。詳細については、「SharePoint Online および[PowerApps ページ](https://powerapps.microsoft.com/)[でリストの powerapp を作成する](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67867-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="67867-137">Microsoft Cloud および Office 365 に関するその他のリソースについては、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="67867-137">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="67867-138">エンタープライズ アーキテクトのための Microsoft クラウド ID</span><span class="sxs-lookup"><span data-stu-id="67867-138">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [<span data-ttu-id="67867-139">Microsoft Azure での Office 365 ディレクトリ同期 (DirSync) の展開</span><span class="sxs-lookup"><span data-stu-id="67867-139">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

<span data-ttu-id="67867-140">詳細については、「Office 365 管理者および[azure ad アプリケーションギャラリーとシングルサインオン](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)[の統合アプリおよび azure ad](integrated-apps-and-azure-ads.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67867-140">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

### <a name="power-apps"></a><span data-ttu-id="67867-141">パワーアプリ</span><span class="sxs-lookup"><span data-stu-id="67867-141">Power Apps</span></span>
<span data-ttu-id="67867-p108">Power apps は、SharePoint リストなどの既存のデータソースやその他のデータアプリに接続できるモバイルデバイス用の注目アプリケーションです。詳細については、「SharePoint Online および[PowerApps ページ](https://powerapps.microsoft.com/)[でリストの powerapp を作成する](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67867-p108">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>