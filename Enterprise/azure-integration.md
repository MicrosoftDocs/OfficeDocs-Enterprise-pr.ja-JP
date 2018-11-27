---
title: Office 365 での Azure 統合
ms.author: robmazz
author: robmazz
manager: laurawi
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
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Office 365 サブスクリプションには、Azure AD へのサブスクリプションが含まれています。オンプレミス環境でパスワード同期またはシングル サインオンをする場合は、Azure AD と Office 365 を統合します。
ms.openlocfilehash: 8b7af5ba8d5106900384369a3e6548af40f9e201
ms.sourcegitcommit: 9c493c4e18e83491d106c5e9bab55d1a89298879
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2018
ms.locfileid: "26674421"
---
# <a name="azure-integration-with-office-365"></a><span data-ttu-id="2672a-104">Office 365 での Azure 統合</span><span class="sxs-lookup"><span data-stu-id="2672a-104">Azure integration with Office 365</span></span>

<span data-ttu-id="2672a-p102">Office 365 は、バック グラウンドでユーザー id を管理する Azure Active Directory (AD の Azure) を使用します。Office 365 サブスクリプションには、パスワードを同期させるか、オンプレミス環境でのシングル サインオンを設定する場合、Azure AD で Office 365 を統合することができますように Azure AD への無料サブスクリプションが含まれています。資産を効率的に管理する高度な機能を購入することもできます。</span><span class="sxs-lookup"><span data-stu-id="2672a-p102">Office 365 uses Azure Active Directory (Azure AD) to manage user identities behind the scenes. Your Office 365 subscription includes a free subscription to Azure AD so that you can integrate Office 365 with Azure AD if you want to sync passwords or set up single sign-on with your on-premises environment. You can also buy advanced features to better manage your accounts.</span></span>
  
<span data-ttu-id="2672a-108">Azure には、拡張し、Office 365 サブスクリプションをカスタマイズするに使用できる、統合されたアプリケーションを管理するのと同様に、他の機能も提供しています。</span><span class="sxs-lookup"><span data-stu-id="2672a-108">Azure also offers other functionality, like managing integrated apps, that you can use to extend and customize your Office 365 subscriptions.</span></span>
  
<span data-ttu-id="2672a-109">ガイド付きのセットアップと構成のエクスペリエンスの Azure AD の導入アドバイザーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2672a-109">You can use the Azure AD deployment advisors for a guided setup and configuration experience:</span></span>
 - [<span data-ttu-id="2672a-110">Azure AD 接続アドバイザー</span><span class="sxs-lookup"><span data-stu-id="2672a-110">Azure AD Connect advisor</span></span>](https://aka.ms/aadconnectpwsync)
 - [<span data-ttu-id="2672a-111">AD FS 展開アドバイザー</span><span class="sxs-lookup"><span data-stu-id="2672a-111">AD FS deployment advisor</span></span>](https://aka.ms/adfsguidance)
 - [<span data-ttu-id="2672a-112">Azure の RMS の展開ウィザード</span><span class="sxs-lookup"><span data-stu-id="2672a-112">Azure RMS Deployment Wizard</span></span>](https://aka.ms/azuremsguidance)
 - [<span data-ttu-id="2672a-113">Azure AD のプレミアム ・ セットアップ ・ ガイド</span><span class="sxs-lookup"><span data-stu-id="2672a-113">Azure AD Premium setup guide</span></span>](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a><span data-ttu-id="2672a-114">Azure AD エディションと Office 365 の id 管理</span><span class="sxs-lookup"><span data-stu-id="2672a-114">Azure AD editions and Office 365 identity management</span></span>

<span data-ttu-id="2672a-p103">Office 365 サブスクリプションを購入する場合は、Azure AD への無料サブスクリプションもあります。Azure AD を使用するにを作成し、ユーザーおよびグループ アカウントを管理します。このサブスクリプションをアクティブにするには、1 回限りの登録を完了する必要があります。後で、Azure AD に、Office 365 管理ポータルからアクセスできます。手順についてを参照してください[登録無料の Azure AD サブスクリプション](https://go.microsoft.com/fwlink/p/?LinkId=617127)。</span><span class="sxs-lookup"><span data-stu-id="2672a-p103">If you have a paid subscription to Office 365, you also have a free subscription to Azure AD. You can use Azure AD to create and manage user and group accounts. To activate this subscription you have to complete a one-time registration. Afterward, you can access Azure AD from your Office 365 admin portal. For instructions, see [register your free Azure AD subscription](https://go.microsoft.com/fwlink/p/?LinkId=617127).</span></span> 
  
> [!TIP]
> <span data-ttu-id="2672a-p104">Office 365 サブスクリプションに付属している登録無料の Azure AD サブスクリプションに、上記の指示に従います。サインアップするのには azure.microsoft.com に直接移動しないかは Office 365 の無料の 1 つから別の Microsoft Azure への試用版または有料のサブスクリプションが終了しました。</span><span class="sxs-lookup"><span data-stu-id="2672a-p104">Follow the instructions above to register the free Azure AD subscription that comes with your subscription to Office 365. Don't go directly to azure.microsoft.com to sign up or you'll end up with a trial or paid subscription to Microsoft Azure that is separate from your free one for Office 365.</span></span> 
  
<span data-ttu-id="2672a-122">サブスクリプションでは、無料設置ディレクトリと同期させることができます、シングル サインオンを設定しなど、Salesforce、ドロップ ボックス、およびより多くのサービス アプリケーションとして、多くのソフトウェアと同期させます。</span><span class="sxs-lookup"><span data-stu-id="2672a-122">With the free subscription you can synchronize with on-premises directories, set up single sign-on, and synchronize with many software as service applications, such as Salesforce, DropBox and many more.</span></span>
  
<span data-ttu-id="2672a-p105">AD DS 機能の強化、双方向同期、およびその他の管理機能をする場合、無償のサブスクリプションを有料のプレミアム サブスクリプションにアップグレードできます。詳細については、 [Azure Active Directory のエディション](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2672a-p105">If you want enhanced AD DS functionality, bi-directional synchronization, and other management capabilities, you can upgrade your free subscription to a paid premium subscription. For details see [Azure Active Directory editions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis).</span></span>
  
<span data-ttu-id="2672a-125">Office 365 と Azure AD に関する詳細については、 [Office 365 の Id を理解して Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2672a-125">For more information about Office 365 and Azure AD, see [Understanding Office 365 Identity and Azure Active Directory](https://support.office.com/article/06a189e7-5ec6-4af2-94bf-a22ea225a7a9).</span></span>
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a><span data-ttu-id="2672a-126">Office 365 テナントの機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="2672a-126">Extend the capabilities of your Office 365 tenant</span></span>

|<span data-ttu-id="2672a-127">**機能**</span><span class="sxs-lookup"><span data-stu-id="2672a-127">**Feature**</span></span>|<span data-ttu-id="2672a-128">**説明**</span><span class="sxs-lookup"><span data-stu-id="2672a-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2672a-129">統合アプリケーション</span><span class="sxs-lookup"><span data-stu-id="2672a-129">Integrated apps</span></span>  <br/> |<span data-ttu-id="2672a-p106">個々 のアプリケーションのアクセスを許可するには、Office 365 のデータ、メール、予定表、連絡先、ユーザー、グループ、ファイル、およびフォルダーのようにします。グローバル管理者レベルでのこれらのアプリケーションを承認し、使用できるように会社全体に Azure AD でアプリケーションを登録することによってもできます。詳細については、[統合されたアプリケーションと Office 365 の管理者向けの Azure AD](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2672a-p106">You can grant individual apps access to your Office 365 data, like mail, calendars, contacts, users, groups, files, and folders. You can also authorize these apps at global admin level and make them available to your entire company by registering the apps in Azure AD. For details see [Integrated Apps and Azure AD for Office 365 administrators](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  </span></span><br/> <span data-ttu-id="2672a-133">参照してください[AD の Azure アプリケーション ギャラリーとシングル ・ サインオン](https://go.microsoft.com/fwlink/p/?LinkId=698604)。</span><span class="sxs-lookup"><span data-stu-id="2672a-133">See also [Azure AD application gallery and single-sign-on](https://go.microsoft.com/fwlink/p/?LinkId=698604).</span></span>  <br/> |
|<span data-ttu-id="2672a-134">PowerApps</span><span class="sxs-lookup"><span data-stu-id="2672a-134">PowerApps</span></span>  <br/> | <span data-ttu-id="2672a-p107">電源アプリケーションは、SharePoint リストなどのソースの既存のデータに接続できるモバイル デバイスのフォーカスのあるアプリケーションとその他のデータ アプリケーションです。詳細については、 [SharePoint Online の一覧については、PowerApp を作成](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)し、 [PowerApps のページ](https://powerapps.microsoft.com/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2672a-p107">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.  </span></span><br/> |
   
<span data-ttu-id="2672a-137">その他のリソースについて、マイクロソフトのクラウドと Office 365 では、これらのリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2672a-137">For other resources about the Microsoft Cloud and Office 365, see these resources:</span></span>
  
- [<span data-ttu-id="2672a-138">エンタープライズ アーキテクトのための Microsoft クラウド ID</span><span class="sxs-lookup"><span data-stu-id="2672a-138">Microsoft Cloud Identity for Enterprise Architects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=524586)
    
- [<span data-ttu-id="2672a-139">Microsoft Azure での Office 365 ディレクトリ同期 (DirSync) の展開</span><span class="sxs-lookup"><span data-stu-id="2672a-139">Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=517887)
    

<span data-ttu-id="2672a-140">[統合アプリケーションと Office 365 の管理者向けの Azure AD](integrated-apps-and-azure-ads.md)の詳細については、 [AD の Azure アプリケーション ギャラリーとシングル ・ サインオン](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)。</span><span class="sxs-lookup"><span data-stu-id="2672a-140">Learn more at [Integrated Apps and Azure AD for Office 365 administrators](integrated-apps-and-azure-ads.md) and [Azure AD application gallery and single-sign-on](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).</span></span>

### <a name="power-apps"></a><span data-ttu-id="2672a-141">電源アプリケーション</span><span class="sxs-lookup"><span data-stu-id="2672a-141">Power Apps</span></span>
<span data-ttu-id="2672a-p108">電源アプリケーションは、SharePoint リストなどのソースの既存のデータに接続できるモバイル デバイスのフォーカスのあるアプリケーションとその他のデータ アプリケーションです。詳細については、 [SharePoint Online の一覧については、PowerApp を作成](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab)し、 [PowerApps のページ](https://powerapps.microsoft.com/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2672a-p108">Power apps are focused apps for mobile devices that can connect to your existing data sources like SharePoint lists, and other data apps. See [Create a PowerApp for a list in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps page](https://powerapps.microsoft.com/) for details.</span></span>