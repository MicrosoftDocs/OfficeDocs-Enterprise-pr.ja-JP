---
title: Office 365 のディレクトリ同期をセットアップする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
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
description: Office 365 とオンプレミスの Active Directory との間のディレクトリ同期をセットアップする方法について説明します。
ms.openlocfilehash: 5cd56eb90e6421d530ff0c2b8739bd13be238eae
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814595"
---
# <a name="set-up-directory-synchronization-for-office-365"></a><span data-ttu-id="8b812-103">Office 365 のディレクトリ同期をセットアップする</span><span class="sxs-lookup"><span data-stu-id="8b812-103">Set up directory synchronization for Office 365</span></span>

<span data-ttu-id="8b812-104">*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="8b812-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="8b812-105">Office 365 では、Azure Active Directory (Azure AD) テナントを使用して、クラウドベースのリソースにアクセスするための id を認証およびアクセス許可用に保存および管理します。</span><span class="sxs-lookup"><span data-stu-id="8b812-105">Office 365 uses an Azure Active Directory (Azure AD) tenant to store and manage identities for authentication and permissions to access cloud-based resources.</span></span> 

<span data-ttu-id="8b812-106">オンプレミスの Active Directory ドメインサービス (AD DS) がある場合は、AD DS のユーザーアカウント、グループ、および連絡先を Office 365 サブスクリプションの Azure AD テナントと同期させることができます。</span><span class="sxs-lookup"><span data-stu-id="8b812-106">If you have an on-premises Active Directory Domain Services (AD DS), you can synchronize your AD DS user accounts, groups, and contacts with the Azure AD tenant of your Office 365 subscription.</span></span> <span data-ttu-id="8b812-107">これは、Office 365 のハイブリッド id です。</span><span class="sxs-lookup"><span data-stu-id="8b812-107">This is hybrid identity for Office 365.</span></span> <span data-ttu-id="8b812-108">そのコンポーネントは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8b812-108">Here are its components.</span></span>

![](./media/about-office-365-identity/hybrid-identity.png)

<span data-ttu-id="8b812-109">Azure AD Connect はオンプレミスのサーバー上で実行され、AD DS を Azure AD テナントと同期します。</span><span class="sxs-lookup"><span data-stu-id="8b812-109">Azure AD Connect runs on an on-premises server and synchronizes your AD DS with the Azure AD tenant.</span></span> <span data-ttu-id="8b812-110">ディレクトリ同期と共に、次の認証オプションを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="8b812-110">Along with directory synchronization, you can also specify these authentication options:</span></span>

- <span data-ttu-id="8b812-111">パスワードハッシュの同期 (PHS)</span><span class="sxs-lookup"><span data-stu-id="8b812-111">Password hash synchronization (PHS)</span></span>

  <span data-ttu-id="8b812-112">Azure AD は認証自体を実行します。</span><span class="sxs-lookup"><span data-stu-id="8b812-112">Azure AD performs the authentication itself.</span></span>

- <span data-ttu-id="8b812-113">パススルー認証 (PTA)</span><span class="sxs-lookup"><span data-stu-id="8b812-113">Pass-through authentication (PTA)</span></span>

  <span data-ttu-id="8b812-114">Azure AD は、AD DS で認証を実行しています。</span><span class="sxs-lookup"><span data-stu-id="8b812-114">Azure AD has AD DS perform the authentication.</span></span>

- <span data-ttu-id="8b812-115">フェデレーション認証</span><span class="sxs-lookup"><span data-stu-id="8b812-115">Federated authentication</span></span>

  <span data-ttu-id="8b812-116">Azure AD は、別の id プロバイダーに接続するための認証を要求しているクライアントコンピューターをリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="8b812-116">Azure AD redirects the client computer requesting authentication to contact another identity provider.</span></span>

<span data-ttu-id="8b812-117">詳細については、「[ハイブリッド id](plan-for-directory-synchronization.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b812-117">See [Hybrid identities](plan-for-directory-synchronization.md) for more information.</span></span>
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a><span data-ttu-id="8b812-118">1. Azure AD Connect の前提条件を確認する</span><span class="sxs-lookup"><span data-stu-id="8b812-118">1. Review prerequisites for Azure AD Connect</span></span>

<span data-ttu-id="8b812-119">Office 365 サブスクリプションを使用して、Azure AD サブスクリプションを無料で入手できます。</span><span class="sxs-lookup"><span data-stu-id="8b812-119">You get a free Azure AD subscription with your Office 365 subscription.</span></span> <span data-ttu-id="8b812-120">ディレクトリ同期をセットアップすると、オンプレミスのサーバーの1つに Azure AD Connect がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="8b812-120">When you set up directory synchronization, you will install Azure AD Connect on one of your on-premises servers.</span></span>
  
<span data-ttu-id="8b812-121">Office 365 の場合は、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b812-121">For Office 365 you'll need to:</span></span>
  
- <span data-ttu-id="8b812-122">オンプレミスのドメインを確認します。</span><span class="sxs-lookup"><span data-stu-id="8b812-122">Verify your on-premises domain.</span></span> <span data-ttu-id="8b812-123">Azure AD Connect ウィザードに従って、このことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="8b812-123">The Azure AD Connect wizard guides you through this.</span></span>
- <span data-ttu-id="8b812-124">Office 365 テナントおよび AD DS の管理者アカウントのユーザー名とパスワードを取得します。</span><span class="sxs-lookup"><span data-stu-id="8b812-124">Obtain the user names and passwords for the admin accounts of your Office 365 tenant and AD DS.</span></span>

<span data-ttu-id="8b812-125">Azure AD Connect をインストールするオンプレミスのサーバーでは、次のものが必要になります。</span><span class="sxs-lookup"><span data-stu-id="8b812-125">For your on-premises server on which you install Azure AD Connect, you'll need:</span></span>
  
|<span data-ttu-id="8b812-126">**サーバー OS**</span><span class="sxs-lookup"><span data-stu-id="8b812-126">**Server OS**</span></span>|<span data-ttu-id="8b812-127">**その他のソフトウェア**</span><span class="sxs-lookup"><span data-stu-id="8b812-127">**Other software**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8b812-128">Windows Server 2012 R2 以降</span><span class="sxs-lookup"><span data-stu-id="8b812-128">Windows Server 2012 R2 and later</span></span> | <span data-ttu-id="8b812-129">-PowerShell は既定でインストールされます。既定では、アクションは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="8b812-129">- PowerShell is installed by default, no action is required.</span></span>  <br> <span data-ttu-id="8b812-130">-Net 4.5.1 以降のリリースは、Windows Update を通じて提供されます。</span><span class="sxs-lookup"><span data-stu-id="8b812-130">- Net 4.5.1 and later releases are offered through Windows Update.</span></span> <span data-ttu-id="8b812-131">コントロールパネルで、Windows Server に最新の更新プログラムがインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8b812-131">Make sure you have installed the latest updates to Windows Server in the Control Panel.</span></span> |
|<span data-ttu-id="8b812-132">Windows Server 2008 R2 Service Pack 1 (SP1) \* \* または Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="8b812-132">Windows Server 2008 R2 with Service Pack 1 (SP1)\*\* or Windows Server 2012</span></span> | <span data-ttu-id="8b812-133">-最新バージョンの PowerShell は、Windows Management Framework 4.0 で利用できます。</span><span class="sxs-lookup"><span data-stu-id="8b812-133">- The latest version of PowerShell is available in Windows Management Framework 4.0.</span></span> <span data-ttu-id="8b812-134">[Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で検索します。</span><span class="sxs-lookup"><span data-stu-id="8b812-134">Search for it on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="8b812-135">-.Net 4.5.1 以降のリリースは、 [Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)から入手できます。</span><span class="sxs-lookup"><span data-stu-id="8b812-135">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |
|<span data-ttu-id="8b812-136">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="8b812-136">Windows Server 2008</span></span> | <span data-ttu-id="8b812-137">-最新サポートされている PowerShell のバージョンは、 [Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能な Windows Management Framework 3.0 で利用できます。</span><span class="sxs-lookup"><span data-stu-id="8b812-137">- The latest supported version of PowerShell is available in Windows Management Framework 3.0, available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span>  <br> <span data-ttu-id="8b812-138">-.Net 4.5.1 以降のリリースは、 [Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)から入手できます。</span><span class="sxs-lookup"><span data-stu-id="8b812-138">- .Net 4.5.1 and later releases are available on [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).</span></span> |

<span data-ttu-id="8b812-139">ハードウェア、ソフトウェア、アカウントとアクセス許可の要件、SSL 証明書の要件、および Azure AD Connect のオブジェクト制限の詳細については、「 [Azure Active Directory 接続の前提条件](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b812-139">See [Prerequisites for Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for the details of hardware, software, account and permissions requirements, SSL certificate requirements, and object limits for Azure AD Connect.</span></span>
  
<span data-ttu-id="8b812-140">また、Azure AD Connect[バージョンのリリース履歴](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history)で、各リリースに含まれているものを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="8b812-140">You can also review the Azure AD Connect [version release history](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) to see what is included and fixed in each release.</span></span>

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a><span data-ttu-id="8b812-141">2. Azure AD Connect をインストールしてディレクトリ同期を構成する</span><span class="sxs-lookup"><span data-stu-id="8b812-141">2. Install Azure AD Connect and configure directory synchronization</span></span>

<span data-ttu-id="8b812-142">開始する前に、以下のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8b812-142">Before you begin, make sure you have:</span></span>

- <span data-ttu-id="8b812-143">Office 365 のグローバル管理者のユーザー名とパスワード</span><span class="sxs-lookup"><span data-stu-id="8b812-143">The user name and password of an Office 365 global admin</span></span>
- <span data-ttu-id="8b812-144">AD DS ドメイン管理者のユーザー名とパスワード</span><span class="sxs-lookup"><span data-stu-id="8b812-144">The user name and password of an AD DS domain administrator</span></span>
- <span data-ttu-id="8b812-145">どの認証方法 (PHS、PTA、フェデレーション)</span><span class="sxs-lookup"><span data-stu-id="8b812-145">Which authentication method (PHS, PTA, federated)</span></span>
- <span data-ttu-id="8b812-146">[AZURE AD のシームレスなシングルサインオン (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)を使用するかどうか</span><span class="sxs-lookup"><span data-stu-id="8b812-146">Whether you want to use [Azure AD Seamless Single Sign-on (SSO)](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)</span></span>

<span data-ttu-id="8b812-147">次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="8b812-147">Follow these steps:</span></span>

1. <span data-ttu-id="8b812-148">[Microsoft 365 管理センター](https://admin.microsoft.com) https://admin.microsoft.com)にサインインし、左側のナビゲーションで [**ユーザー** \>の**アクティブなユーザー** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8b812-148">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) (https://admin.microsoft.com) and choose **Users** \> **Active Users** on the left navigation.</span></span>
2. <span data-ttu-id="8b812-149">[**アクティブなユーザー** ] ページで、[ **More** (3 \>つのドット)**ディレクトリ同期**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8b812-149">On the **Active users** page, choose **More** (three dots) \> **Directory synchronization**.</span></span>
  
3. <span data-ttu-id="8b812-150">[ **Azure Active Directory の準備**] ページで、[**ダウンロードセンターに移動して azure AD Connect ツールの**リンクを取得する] を選択して、作業を開始します。</span><span class="sxs-lookup"><span data-stu-id="8b812-150">On the **Azure Active Directory preparation** page, select the **Go to the Download center to get the Azure AD Connect tool** link to get started.</span></span> 
4. <span data-ttu-id="8b812-151">「 [AZURE Ad connect と AZURE Ad Connect 正常性インストールのロードマップ](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)」の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="8b812-151">Follow the steps in [Azure AD Connect and Azure AD Connect Health installation roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).</span></span>

## <a name="3-finish-setting-up-domains"></a><span data-ttu-id="8b812-152">3. ドメインの設定を終了する</span><span class="sxs-lookup"><span data-stu-id="8b812-152">3. Finish setting up domains</span></span>

<span data-ttu-id="8b812-153">DNS レコードを管理するときに、「 [CREATE dns records For Office 365](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) 」の手順に従って、ドメインの設定を完了します。</span><span class="sxs-lookup"><span data-stu-id="8b812-153">Follow the steps in [Create DNS records for Office 365 when you manage your DNS records](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) to finish setting up your domains.</span></span>

## <a name="next-step"></a><span data-ttu-id="8b812-154">次の手順</span><span class="sxs-lookup"><span data-stu-id="8b812-154">Next step</span></span>

[<span data-ttu-id="8b812-155">ユーザー アカウントにライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="8b812-155">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
