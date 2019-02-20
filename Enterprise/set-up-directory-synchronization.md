---
title: Office 365 のディレクトリ同期のセットアップ
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Office 365 とオンプレミスの Active directory との間のディレクトリ同期をセットアップする方法について説明します。
ms.openlocfilehash: 5f6e5be2a2137ee183a7d592d9a3e6b086e5be9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085266"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="2ccfb-103">Office 365 のディレクトリ同期のセットアップ</span><span class="sxs-lookup"><span data-stu-id="2ccfb-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="2ccfb-p101">Office 365 は、クラウドベースのユーザー id 管理サービス Azure Active Directory を使用してユーザーを管理します。オンプレミスの環境と Office 365 を同期することによって、オンプレミスの Active Directory を Azure AD と統合することもできます。同期を設定すると、ユーザーの認証を Azure AD 内で行うか、オンプレミスのディレクトリ内で行うかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-p101">Office 365 uses the cloud-based user identity management service Azure Active Directory to manage users. You can also integrate your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365. Once you set up synchronization you can decide to have their user authentication take place within Azure AD or within your on-premises directory.</span></span>
  
## <a name="office-365-directory-synchronization"></a><span data-ttu-id="2ccfb-107">Office 365 ディレクトリ同期</span><span class="sxs-lookup"><span data-stu-id="2ccfb-107">Office 365 directory synchronization</span></span>

<span data-ttu-id="2ccfb-p102">オンプレミスの組織と Office 365 の間で、同期された id またはフェデレーション id を使用できます。同期された id を使用すると、オンプレミスのユーザーを管理できます。また、クラウドでオンプレミスと同じパスワードを使用する場合は、Azure AD によって認証されます。これは、最も一般的なディレクトリ同期のシナリオです。パススルー認証またはフェデレーション id を使用して、オンプレミスのユーザーを管理し、オンプレミスのディレクトリによって認証されます。フェデレーション id には追加の構成が必要であり、ユーザーは一度だけサインインできるようになります。詳細については、「 [Office 365 id と Azure Active Directory について](about-office-365-identity.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-p102">You can either use synchronized identity or federated identity between your on-premises organization and Office 365. With synchronized identity, you manage your users on-premises, and they are authenticated by Azure AD when they use the same password in the cloud as on-premises. This is the most common directory synchronization scenario. Pass-through authentication or Federated identity, allows you to manage your users on-premises and they are authenticated by your on-premises directory. Federated identity requires additional configuration and enables your users to only sign in once. For details, read [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a><span data-ttu-id="2ccfb-114">Windows azure active directory 同期 (DirSync) から azure active directory Connect へのアップグレードを希望する場合</span><span class="sxs-lookup"><span data-stu-id="2ccfb-114">Want to upgrade from Windows Azure Active Directory sync (DirSync) to Azure Active Directory Connect?</span></span>

<span data-ttu-id="2ccfb-115">現在 DirSync を使用していて、アップグレードする場合は、 [azure.com](https://azure.com)に移動して[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-115">If you are currently using DirSync and want to upgrade, head over to [azure.com](https://azure.com) for [upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="prerequisites-for-azure-ad-connect"></a><span data-ttu-id="2ccfb-116">Azure AD Connect の前提条件</span><span class="sxs-lookup"><span data-stu-id="2ccfb-116">Prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="2ccfb-p103">Office 365 サブスクリプションを使用して Azure AD への無料サブスクリプションを取得します。ディレクトリ同期をセットアップすると、オンプレミスサーバーの1つに Azure Active directory Connect がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-p103">You get a free subscription to Azure AD with your Office 365 subscription. When you set up directory synchronization, you will install Azure Active Directory Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="2ccfb-119">Office 365 の場合は、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-119">For Office 365 you will need to:</span></span>
  
- <span data-ttu-id="2ccfb-120">オンプレミスのドメインを確認します (手順を追って説明します)。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-120">Verify your on-premises domain (the procedure will guide you through this).</span></span>
- <span data-ttu-id="2ccfb-121">office 365 で office 365 テナントとオンプレミスの Active Directory のビジネスアクセス許可に対して[管理者ロールを割り当て](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504)ます。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-121">Have [Assign admin roles in Office 365 for business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissions for your Office 365 tenant and on-premises Active Directory.</span></span>

<span data-ttu-id="2ccfb-122">Azure AD Connect をインストールするオンプレミスサーバーでは、次のソフトウェアが必要になります。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-122">For your on-premises server on which you install Azure AD Connect you will need the following software:</span></span>
  
|<span data-ttu-id="2ccfb-123">**サーバー OS**</span><span class="sxs-lookup"><span data-stu-id="2ccfb-123">**Server OS**</span></span>|<span data-ttu-id="2ccfb-124">**その他のソフトウェア**</span><span class="sxs-lookup"><span data-stu-id="2ccfb-124">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2ccfb-125">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="2ccfb-125">**Windows Server 2012 R2**</span></span> | <span data-ttu-id="2ccfb-126">-PowerShell は既定でインストールされます。既定では、アクションは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-126">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="2ccfb-p104">-Net 4.5.1 以降のリリースは、Windows Update を通じて提供されます。コントロールパネルで、Windows Server に最新の更新プログラムがインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-p104">- Net 4.5.1 and later releases are offered through Windows Update. Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="2ccfb-129">**windows server 2008 R2 Service Pack 1 (SP1)** または**windows server 2012**</span><span class="sxs-lookup"><span data-stu-id="2ccfb-129">**Windows Server 2008 R2 with Service Pack 1 (SP1)** or **Windows Server 2012**</span></span> | <span data-ttu-id="2ccfb-p105">-最新バージョンの PowerShell は、Windows Management Framework 4.0 で利用できます。[Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で検索します。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-p105">- The latest version of PowerShell is available in Windows Management Framework 4.0. Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  </span></span><br> <span data-ttu-id="2ccfb-132">-.net 4.5.1 以降のリリースは、 [Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)から入手できます。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-132">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="2ccfb-133">**Windows Server 2008**</span><span class="sxs-lookup"><span data-stu-id="2ccfb-133">**Windows Server 2008**</span></span> | <span data-ttu-id="2ccfb-134">-最新サポートされている PowerShell のバージョンは、 [Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能な Windows Management Framework 3.0 で利用できます。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-134">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="2ccfb-135">-.net 4.5.1 以降のリリースは、 [Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)から入手できます。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

> [!NOTE]
> <span data-ttu-id="2ccfb-p106">azure active directory DirSync を使用している場合、オンプレミスの active directory から azure active directory に同期できる配布グループメンバーの最大数は15000です。Azure AD Connect の場合、この番号は5万です。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-p106">If you're using Azure Active Directory DirSync, the maximum number of distribution group members that you can synchronize from your on-premises Active Directory to Azure Active Directory is 15,000. For Azure AD Connect, that number is 50,000.</span></span> 
  
<span data-ttu-id="2ccfb-138">ハードウェア、ソフトウェア、アカウントとアクセス許可の要件、SSL 証明書の要件、および azure AD Connect のオブジェクト制限を慎重に確認するには、「 [azure Active Directory Connect の前提条件](https://go.microsoft.com/fwlink/p/?LinkId=716896)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-138">To more carefully review hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect, read [Prerequisites for Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span></span>
  
<span data-ttu-id="2ccfb-139">また、Azure AD Connect[バージョンのリリース履歴](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history)で、各リリースに含まれているものを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="to-set-up-directory-synchronization"></a><span data-ttu-id="2ccfb-140">ディレクトリ同期をセットアップするには</span><span class="sxs-lookup"><span data-stu-id="2ccfb-140">To set up directory synchronization</span></span>

1. <span data-ttu-id="2ccfb-141">Office 365 管理センターにサインインし、左側のナビゲーションで [**ユーザー** \>の**アクティブなユーザー** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-141">Sign in to the Office 365 admin center and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="2ccfb-142">Office 365 管理センターの [**アクティブなユーザー** ] ページで、[**その他** \>の**ディレクトリ同期**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-142">In the Office 365 admin center, on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span>

    ![[その他] メニューで、[ディレクトリ同期] を選択します。](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="2ccfb-p107">[ **active directory の準備**] ページで、[ **Microsoft Azure Active directory Connect ツールのダウンロード**] リンクをクリックして開始します。azure Active Directory 接続のインストールプロセスの詳細については、「 [azure ad connect と azure ad connect 正常性インストールのロードマップ](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-p107">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started. For more information about the Azure Active Directory Connect installation process, see [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="assign-licenses-to-synchronized-users"></a><span data-ttu-id="2ccfb-146">同期されたユーザーにライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="2ccfb-146">Assign licenses to synchronized users</span></span>

<span data-ttu-id="2ccfb-p108">ユーザーを office 365 に同期した後は、それらのユーザーが作成されますが、メールなどの office 365 機能を使用できるようにするためにライセンスを割り当てる必要があります。手順については、「一般[法人向け Office 365 のユーザーにライセンスを割り当てる](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-p108">After you have synchronized your users to Office 365, they are created but you need to assign licenses to them so they can use Office 365 features, such as mail. For instructions, see [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>

## <a name="finish-setting-up-domains"></a><span data-ttu-id="2ccfb-149">ドメインのセットアップを完了する</span><span class="sxs-lookup"><span data-stu-id="2ccfb-149">Finish setting up domains</span></span>

<span data-ttu-id="2ccfb-150">dns レコードを管理するときに、「 [Create dns records for Office 365](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) 」の手順に従って、ドメインの設定を完了します。</span><span class="sxs-lookup"><span data-stu-id="2ccfb-150">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>