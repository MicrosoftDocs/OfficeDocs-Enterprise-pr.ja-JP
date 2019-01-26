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
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Office 365 と、オンプレミスの Active Directory のディレクトリ同期をセットアップする方法について説明します。
ms.openlocfilehash: f2cd29e7a81854bb64f6317aa2b41e674ae22df4
ms.sourcegitcommit: a4546e1f3fe9e8e25a56ed350400d51eb7dd7f83
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "29555443"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="d4fce-103">Office 365 のディレクトリ同期のセットアップ</span><span class="sxs-lookup"><span data-stu-id="d4fce-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="d4fce-p101">Office 365 は、ユーザーを管理するのにクラウド ベースのユーザー id の管理の Azure Active Directory サービスを使用します。Azure AD を Office 365 で、オンプレミス環境を同期することにより、オンプレミスの Active Directory を統合することも。同期を設定すると、Azure AD 内で、または、設置ディレクトリ内のユーザー認証を決定できます。</span><span class="sxs-lookup"><span data-stu-id="d4fce-p101">Office 365 uses the cloud-based user identity management service Azure Active Directory to manage users. You can also integrate your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365. Once you set up synchronization you can decide to have their user authentication take place within Azure AD or within your on-premises directory.</span></span>
  
## <a name="office-365-directory-synchronization"></a><span data-ttu-id="d4fce-107">Office 365 ディレクトリ同期</span><span class="sxs-lookup"><span data-stu-id="d4fce-107">Office 365 directory synchronization</span></span>

<span data-ttu-id="d4fce-p102">同期の id や、設置型の組織と Office 365 の間でフェデレーション id を使用することができます。同期の id で、ユーザー設置を管理すると、同じパスワードを使用、クラウドでオンプレミスと Azure の AD によって認証します。これは、最も一般的なディレクトリ同期シナリオです。パススルー認証] または [フェデレーション id は、ユーザーの設置型を管理することをでき、オンプレミス ディレクトリで認証します。フェデレートされた識別情報は、追加の構成を必要とし、のみ 1 回サインインすることができます。詳細については、 [Office 365 の Id を理解して Azure Active Directory](about-office-365-identity.md)を読み取る。</span><span class="sxs-lookup"><span data-stu-id="d4fce-p102">You can either use synchronized identity or federated identity between your on-premises organization and Office 365. With synchronized identity, you manage your users on-premises, and they are authenticated by Azure AD when they use the same password in the cloud as on-premises. This is the most common directory synchronization scenario. Pass-through authentication or Federated identity, allows you to manage your users on-premises and they are authenticated by your on-premises directory. Federated identity requires additional configuration and enables your users to only sign in once. For details, read [Understanding Office 365 Identity and Azure Active Directory](about-office-365-identity.md).</span></span>
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a><span data-ttu-id="d4fce-114">Azure Active Directory に接続するのには、Windows Azure Active Directory 同期 (DirSync) からアップグレードする場合は、</span><span class="sxs-lookup"><span data-stu-id="d4fce-114">Want to upgrade from Windows Azure Active Directory sync (DirSync) to Azure Active Directory Connect?</span></span>

<span data-ttu-id="d4fce-115">ディレクトリ同期を現在使用してアップグレードする場合、ヘッドを[azure.com](https://azure.com)に[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)の。</span><span class="sxs-lookup"><span data-stu-id="d4fce-115">If you are currently using DirSync and want to upgrade, head over to [azure.com](https://azure.com) for [upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="prerequisites-for-azure-ad-connect"></a><span data-ttu-id="d4fce-116">Azure AD の前提条件を接続します。</span><span class="sxs-lookup"><span data-stu-id="d4fce-116">Prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="d4fce-p103">Azure AD に Office 365 サブスクリプションと無料サブスクリプションを取得します。、ディレクトリ同期をセットアップすると、Azure Active Directory の接続をインストール、オンプレミスのサーバーのいずれかにされます。</span><span class="sxs-lookup"><span data-stu-id="d4fce-p103">You get a free subscription to Azure AD with your Office 365 subscription. When you set up directory synchronization, you will install Azure Active Directory Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="d4fce-119">Office 365 用に必要になります。</span><span class="sxs-lookup"><span data-stu-id="d4fce-119">For Office 365 you will need to:</span></span>
  
- <span data-ttu-id="d4fce-120">(手順に従って、この)、オンプレミス ドメインを確認します。</span><span class="sxs-lookup"><span data-stu-id="d4fce-120">Verify your on-premises domain (the procedure will guide you through this).</span></span>
- <span data-ttu-id="d4fce-121">[ビジネス向けの Office 365 の管理者の役割を割り当てる](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504)アクセス許可を持つ、Office 365 テナントとオンプレミスの Active Directory です。</span><span class="sxs-lookup"><span data-stu-id="d4fce-121">Have [Assign admin roles in Office 365 for business](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) permissions for your Office 365 tenant and on-premises Active Directory.</span></span>

<span data-ttu-id="d4fce-122">Azure AD 接続をインストールする、設置型サーバーの次のソフトウェアが必要になります。</span><span class="sxs-lookup"><span data-stu-id="d4fce-122">For your on-premises server on which you install Azure AD Connect you will need the following software:</span></span>
  
|<span data-ttu-id="d4fce-123">**サーバ OS**</span><span class="sxs-lookup"><span data-stu-id="d4fce-123">**Server OS**</span></span>|<span data-ttu-id="d4fce-124">**その他のソフトウェア**</span><span class="sxs-lookup"><span data-stu-id="d4fce-124">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d4fce-125">**Windows Server 2012 R2**</span><span class="sxs-lookup"><span data-stu-id="d4fce-125">**Windows Server 2012 R2**</span></span> | <span data-ttu-id="d4fce-126">で PowerShell は、既定でインストール、操作する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d4fce-126">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="d4fce-p104">Net 4.5.1 以降のリリースが Windows Update で提供されているとします。コントロール パネルの Windows サーバーに最新の更新プログラムがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d4fce-p104">- Net 4.5.1 and later releases are offered through Windows Update. Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="d4fce-129">**パック 1 (SP1) のサービスを Windows Server 2008 R2**または**Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="d4fce-129">**Windows Server 2008 R2 with Service Pack 1 (SP1)** or **Windows Server 2012**</span></span> | <span data-ttu-id="d4fce-p105">-PowerShell の最新バージョンは、Windows Management Framework 4.0 で使用できます。[Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で検索します。</span><span class="sxs-lookup"><span data-stu-id="d4fce-p105">- The latest version of PowerShell is available in Windows Management Framework 4.0. Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  </span></span><br> <span data-ttu-id="d4fce-132">-.Net 4.5.1 およびそれ以降のリリースでは、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能です。</span><span class="sxs-lookup"><span data-stu-id="d4fce-132">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="d4fce-133">**Windows Server 2008**</span><span class="sxs-lookup"><span data-stu-id="d4fce-133">**Windows Server 2008**</span></span> | <span data-ttu-id="d4fce-134">-サポートされる最新バージョンの PowerShell は、Windows Management Framework 3.0 では、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能な時間があります。</span><span class="sxs-lookup"><span data-stu-id="d4fce-134">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="d4fce-135">-.Net 4.5.1 およびそれ以降のリリースでは、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能です。</span><span class="sxs-lookup"><span data-stu-id="d4fce-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

> [!NOTE]
> <span data-ttu-id="d4fce-p106">Azure Active Directory のディレクトリ同期を使用している場合は、Azure Active Directory に、オンプレミスの Active Directory から同期することができる配布グループのメンバーの最大数が 15,000 です。Azure AD 接続では、その番号は 50,000 です。</span><span class="sxs-lookup"><span data-stu-id="d4fce-p106">If you're using Azure Active Directory DirSync, the maximum number of distribution group members that you can synchronize from your on-premises Active Directory to Azure Active Directory is 15,000. For Azure AD Connect, that number is 50,000.</span></span> 
  
<span data-ttu-id="d4fce-138">Azure AD 接続のハードウェア、ソフトウェア、アカウントとアクセス許可の要件、SSL 証明書の要件、およびオブジェクトの制限をより慎重に確認、 [Azure Active Directory に接続するための前提条件](https://go.microsoft.com/fwlink/p/?LinkId=716896)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4fce-138">To more carefully review hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect, read [Prerequisites for Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).</span></span>
  
<span data-ttu-id="d4fce-139">Azure AD 接続[リリースのバージョン履歴](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history)に含まれており、各リリースでの修正内容を参照してくださいかを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="d4fce-139">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="to-set-up-directory-synchronization"></a><span data-ttu-id="d4fce-140">ディレクトリ同期を設定するには</span><span class="sxs-lookup"><span data-stu-id="d4fce-140">To set up directory synchronization</span></span>

1. <span data-ttu-id="d4fce-141">Office 365 の管理センターにサインインし、**ユーザー**の選択\>左のナビゲーションには、**アクティブなユーザー**です。</span><span class="sxs-lookup"><span data-stu-id="d4fce-141">Sign in to the Office 365 admin center and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="d4fce-142">Office 365 管理センターで、[**アクティブ ユーザ**] ページで [**詳細** \> **ディレクトリ同期**します。</span><span class="sxs-lookup"><span data-stu-id="d4fce-142">In the Office 365 admin center, on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span>

    ![[詳細] メニューの [ディレクトリ同期を選択します](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. <span data-ttu-id="d4fce-p107">[ **Active Directory の準備**] ページでは、**ツールのダウンロード Microsoft Azure Active Directory 接続**のリンクを開始するを選択します。Azure Active Directory 接続のインストール プロセスに関する詳細については、 [Azure 接続する AD と AD の Azure の接続の状態のインストール ・ ロードマップ](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4fce-p107">On the **Active Directory preparation** page, select the **Download Microsoft Azure Active Directory Connect tool** link to get started. For more information about the Azure Active Directory Connect installation process, see [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="assign-licenses-to-synchronized-users"></a><span data-ttu-id="d4fce-146">同期されたユーザーにライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="d4fce-146">Assign licenses to synchronized users</span></span>

<span data-ttu-id="d4fce-p108">同期したら、ユーザーが Office 365 は、作成されるが、メールなど、Office 365 の機能を使用するためにライセンスを割り当てる必要があります。手順については、[ビジネス向けの Office 365 のユーザーにライセンスを割り当てる](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4fce-p108">After you have synchronized your users to Office 365, they are created but you need to assign licenses to them so they can use Office 365 features, such as mail. For instructions, see [Assign licenses to users in Office 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).</span></span>

## <a name="finish-setting-up-domains"></a><span data-ttu-id="d4fce-149">ドメインのセットアップを完了します。</span><span class="sxs-lookup"><span data-stu-id="d4fce-149">Finish setting up domains</span></span>

<span data-ttu-id="d4fce-150">自分のドメインの設定を完了するのには[Office 365 の DNS レコードを管理するときに作成する DNS レコード](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d4fce-150">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) to finish setting up your domains.</span></span>