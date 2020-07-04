---
title: Microsoft Azure での Microsoft 365 ディレクトリ同期の展開
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: '概要: azure の仮想マシン上に Azure AD Connect を展開し、オンプレミスのディレクトリと Microsoft 365 サブスクリプションの Azure AD テナントとの間でアカウントを同期します。'
ms.openlocfilehash: 6f2da528293de54d21bd88b31fcd347cfab9335c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998065"
---
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="9d010-103">Microsoft Azure での Microsoft 365 ディレクトリ同期の展開</span><span class="sxs-lookup"><span data-stu-id="9d010-103">Deploy Microsoft 365 Directory Synchronization in Microsoft Azure</span></span>

<span data-ttu-id="9d010-104">Azure Active Directory (Azure AD) Connect (以前のディレクトリ同期ツール、ディレクトリ同期ツール、または DirSync.exe ツール) は、ドメインに参加しているサーバーにインストールして、オンプレミスの Active Directory ドメインサービス (AD DS) ユーザーを Microsoft 365 サブスクリプションの Azure AD テナントに同期するアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="9d010-104">Azure Active Directory (Azure AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is an application that you install on a domain-joined server to synchronize your on-premises Active Directory Domain Services (AD DS) users to the Azure AD tenant of your Microsoft 365 subscription.</span></span> <span data-ttu-id="9d010-105">Microsoft 365 では、ディレクトリサービスに Azure AD を使用しています。</span><span class="sxs-lookup"><span data-stu-id="9d010-105">Microsoft 365 uses Azure AD for its directory service.</span></span> <span data-ttu-id="9d010-106">Microsoft 365 サブスクリプションには、Azure AD テナントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9d010-106">Your Microsoft 365 subscription includes an Azure AD tenant.</span></span> <span data-ttu-id="9d010-107">このテナントは他の SaaS アプリケーションと Azure のアプリを含む、他のクラウドのワークロードで組織の ID を管理するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="9d010-107">This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span>

<span data-ttu-id="9d010-108">Azure AD Connect はオンプレミス サーバーにインストールできますが、次の理由により、Azure の仮想マシンにもインストールできます。</span><span class="sxs-lookup"><span data-stu-id="9d010-108">You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for these reasons:</span></span>
  
- <span data-ttu-id="9d010-109">クラウド ベースのサーバーをより迅速にプロビジョニングして構成でき、ユーザーがすぐにサービスを利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9d010-109">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
- <span data-ttu-id="9d010-110">Azure では、より少ない労力でより良いサイト可用性が得られます。</span><span class="sxs-lookup"><span data-stu-id="9d010-110">Azure offers better site availability with less effort.</span></span>
- <span data-ttu-id="9d010-111">組織内のオンプレミス サーバーの数を削減できます。</span><span class="sxs-lookup"><span data-stu-id="9d010-111">You can reduce the number of on-premises servers in your organization.</span></span>

<span data-ttu-id="9d010-112">This solution requires connectivity between your on-premises network and your Azure virtual network.</span><span class="sxs-lookup"><span data-stu-id="9d010-112">This solution requires connectivity between your on-premises network and your Azure virtual network.</span></span> <span data-ttu-id="9d010-113">For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="9d010-113">For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="9d010-114">この記事では、1 つのフォレスト内の単一ドメインの同期について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d010-114">This article describes synchronization of a single domain in a single forest.</span></span> <span data-ttu-id="9d010-115">Azure AD Connect は、Active Directory フォレスト内のすべての AD DS ドメインを Microsoft 365 と同期します。</span><span class="sxs-lookup"><span data-stu-id="9d010-115">Azure AD Connect synchronizes all AD DS domains in your Active Directory forest with Microsoft 365.</span></span> <span data-ttu-id="9d010-116">Microsoft 365 と同期する複数の Active Directory フォレストがある場合は、「[マルチフォレストディレクトリ同期とシングルサインオンシナリオ](https://go.microsoft.com/fwlink/p/?LinkId=393091)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d010-116">If you have multiple Active Directory forests to synchronize with Microsoft 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a><span data-ttu-id="9d010-117">Azure での Microsoft 365 ディレクトリ同期の展開の概要</span><span class="sxs-lookup"><span data-stu-id="9d010-117">Overview of deploying Microsoft 365 directory synchronization in Azure</span></span>

<span data-ttu-id="9d010-118">次の図は、オンプレミスの AD DS フォレストを Microsoft 365 サブスクリプションに同期する azure AD Connect を示しています。 Azure AD Connect は Azure (ディレクトリ同期サーバー) の仮想マシンで実行されています。</span><span class="sxs-lookup"><span data-stu-id="9d010-118">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises AD DS forest to a Microsoft 365 subscription.</span></span>
  
![Azure の仮想マシン上の azure AD Connect ツールトラフィックフローを含む Microsoft 365 サブスクリプションの Azure AD テナントへのオンプレミスアカウントの同期](media/CP-DirSyncOverview.png)
  
<span data-ttu-id="9d010-120">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection.</span><span class="sxs-lookup"><span data-stu-id="9d010-120">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="9d010-121">There is an on-premises network where AD DS domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span><span class="sxs-lookup"><span data-stu-id="9d010-121">There is an on-premises network where AD DS domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span> <span data-ttu-id="9d010-122">There are two main traffic flows originating from the directory sync server:</span><span class="sxs-lookup"><span data-stu-id="9d010-122">There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="9d010-123">Azure AD Connect は、アカウントとパスワードの変更に関してオンプレミス ネットワーク上のドメイン コントローラーにクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="9d010-123">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
-  <span data-ttu-id="9d010-124">Azure AD Connect は、アカウントおよびパスワードへの変更を、Microsoft 365 サブスクリプションの Azure AD インスタンスに送信します。</span><span class="sxs-lookup"><span data-stu-id="9d010-124">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Microsoft 365 subscription.</span></span> <span data-ttu-id="9d010-125">ディレクトリ同期サーバーはオンプレミスネットワークの拡張部分にあるため、これらの変更は、オンプレミスネットワークのプロキシサーバー経由で送信されます。</span><span class="sxs-lookup"><span data-stu-id="9d010-125">Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="9d010-126">このソリューションでは、1 つの Active Directory フォレスト内の単一 Active Directory ドメインの同期について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d010-126">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest.</span></span> <span data-ttu-id="9d010-127">Azure AD Connect は、Active Directory フォレスト内のすべての Active Directory ドメインを Microsoft 365 と同期します。</span><span class="sxs-lookup"><span data-stu-id="9d010-127">Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Microsoft 365.</span></span> <span data-ttu-id="9d010-128">Microsoft 365 と同期する複数の Active Directory フォレストがある場合は、「[マルチフォレストディレクトリ同期とシングルサインオンシナリオ](https://go.microsoft.com/fwlink/p/?LinkId=393091)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d010-128">If you have multiple Active Directory forests to synchronize with Microsoft 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="9d010-129">このソリューションをデプロイする場合には、次の 2 つの主要な手順があります。</span><span class="sxs-lookup"><span data-stu-id="9d010-129">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="9d010-130">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network.</span><span class="sxs-lookup"><span data-stu-id="9d010-130">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network.</span></span> <span data-ttu-id="9d010-131">For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span><span class="sxs-lookup"><span data-stu-id="9d010-131">For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="9d010-132">Azure のドメインに参加している仮想マシンに[AZURE AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)をインストールし、オンプレミスの ad DS を Microsoft 365 と同期します。</span><span class="sxs-lookup"><span data-stu-id="9d010-132">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises AD DS to Microsoft 365.</span></span> <span data-ttu-id="9d010-133">これには以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="9d010-133">This involves:</span></span>
    
    <span data-ttu-id="9d010-134">Azure AD Connect を実行するため、Azure Virtual Machine を作成します。</span><span class="sxs-lookup"><span data-stu-id="9d010-134">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="9d010-135">[Azure AD Connect ](https://www.microsoft.com/download/details.aspx?id=47594) をインストールし、設定します。</span><span class="sxs-lookup"><span data-stu-id="9d010-135">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="9d010-136">Azure AD Connect を構成するには、Azure AD 管理者アカウントおよび AD DS エンタープライズ管理者アカウントの資格情報 (ユーザー名とパスワード) が必要です。</span><span class="sxs-lookup"><span data-stu-id="9d010-136">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a AD DS enterprise administrator account.</span></span> <span data-ttu-id="9d010-137">Azure AD Connect はすぐに実行され、オンプレミスの AD DS フォレストを Microsoft 365 に同期します。</span><span class="sxs-lookup"><span data-stu-id="9d010-137">Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises AD DS forest to Microsoft 365.</span></span>
    
<span data-ttu-id="9d010-138">このソリューションを運用環境に展開する前に、シミュレートされた[エンタープライズ基本構成](https://docs.microsoft.com/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise)の手順を使用して、この構成を概念実証、デモンストレーション、または実験のために設定することができます。</span><span class="sxs-lookup"><span data-stu-id="9d010-138">Before you deploy this solution in production, you can use the instructions in [The simulated enterprise base configuration](https://docs.microsoft.com/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="9d010-139">Azure AD Connect の設定が完了しても、AD DS エンタープライズ管理者アカウントの資格情報は保存されません。</span><span class="sxs-lookup"><span data-stu-id="9d010-139">When Azure AD Connect configuration completes, it does not save the AD DS enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="9d010-140">このソリューションでは、1つの AD DS フォレストを Microsoft 365 と同期する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d010-140">This solution describes synchronizing a single AD DS forest to Microsoft 365.</span></span> <span data-ttu-id="9d010-141">この記事で取り上げられているトポロジは、このソリューションを実装する 1 つの方法に過ぎません。</span><span class="sxs-lookup"><span data-stu-id="9d010-141">The topology discussed in this article represents only one way to implement this solution.</span></span> <span data-ttu-id="9d010-142">組織のトポロジは、固有のネットワーク要件とセキュリティに関する考慮事項によって異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9d010-142">Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a><span data-ttu-id="9d010-143">Azure で Microsoft 365 用のディレクトリ同期サーバーをホストするための計画</span><span class="sxs-lookup"><span data-stu-id="9d010-143">Plan for hosting a directory sync server for Microsoft 365 in Azure</span></span>
<span data-ttu-id="9d010-144"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="9d010-144"><a name="PlanningVirtual"> </a></span></span>

### <a name="prerequisites"></a><span data-ttu-id="9d010-145">前提条件</span><span class="sxs-lookup"><span data-stu-id="9d010-145">Prerequisites</span></span>

<span data-ttu-id="9d010-146">開始する前に、このソリューションの以下の前提条件を確認してください。</span><span class="sxs-lookup"><span data-stu-id="9d010-146">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="9d010-147">「[Azure 仮想ネットワークの計画](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network)」に記されている関連する計画内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="9d010-147">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).</span></span>
    
- <span data-ttu-id="9d010-148">Azure Virtual Network を構成するためのすべての「[前提条件](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites)」を満たしていることを確かめます。</span><span class="sxs-lookup"><span data-stu-id="9d010-148">Ensure that you meet all [Prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="9d010-149">Active Directory 統合機能を含む Microsoft 365 サブスクリプションを所有していること。</span><span class="sxs-lookup"><span data-stu-id="9d010-149">Have a Microsoft 365 subscription that includes the Active Directory integration feature.</span></span> <span data-ttu-id="9d010-150">Microsoft 365 サブスクリプションの詳細については、 [microsoft 365 サブスクリプションページ](https://products.office.com/compare-all-microsoft-office-products?tab=2)にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="9d010-150">For information about Microsoft 365 subscriptions, go to the [Microsoft 365 subscription page](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span></span>
    
- <span data-ttu-id="9d010-151">Azure AD Connect を実行する1つの Azure 仮想マシンをプロビジョニングして、オンプレミスの AD DS フォレストを Microsoft 365 と同期させます。</span><span class="sxs-lookup"><span data-stu-id="9d010-151">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises AD DS forest with Microsoft 365.</span></span>
    
    <span data-ttu-id="9d010-152">AD DS エンタープライズ管理者アカウントと Azure AD 管理者アカウントの資格情報 (名前とパスワード) が必要です。</span><span class="sxs-lookup"><span data-stu-id="9d010-152">You must have the credentials (names and passwords) for a AD DS enterprise administrator account and an Azure AD Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="9d010-153">ソリューション アーキテクチャ設計の前提条件</span><span class="sxs-lookup"><span data-stu-id="9d010-153">Solution architecture design assumptions</span></span>

<span data-ttu-id="9d010-154">次の一覧では、このソリューションで採用された設計方針について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d010-154">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="9d010-155">This solution uses a single Azure virtual network with a site-to-site VPN connection.</span><span class="sxs-lookup"><span data-stu-id="9d010-155">This solution uses a single Azure virtual network with a site-to-site VPN connection.</span></span> <span data-ttu-id="9d010-156">The Azure virtual network hosts a single subnet that has one server, the directory sync server that is running Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="9d010-156">The Azure virtual network hosts a single subnet that has one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="9d010-157">オンプレミス ネットワークには、ドメイン コントローラーと DNS サーバーが存在します。</span><span class="sxs-lookup"><span data-stu-id="9d010-157">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="9d010-158">Azure AD Connect performs password hash synchronization instead of single sign-on.</span><span class="sxs-lookup"><span data-stu-id="9d010-158">Azure AD Connect performs password hash synchronization instead of single sign-on.</span></span> <span data-ttu-id="9d010-159">You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure.</span><span class="sxs-lookup"><span data-stu-id="9d010-159">You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure.</span></span> <span data-ttu-id="9d010-160">To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](https://aka.ms/auth-options).</span><span class="sxs-lookup"><span data-stu-id="9d010-160">To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](https://aka.ms/auth-options).</span></span>
    
<span data-ttu-id="9d010-161">There are additional design choices that you might consider when you deploy this solution in your environment.</span><span class="sxs-lookup"><span data-stu-id="9d010-161">There are additional design choices that you might consider when you deploy this solution in your environment.</span></span> <span data-ttu-id="9d010-162">These include the following:</span><span class="sxs-lookup"><span data-stu-id="9d010-162">These include the following:</span></span>
  
- <span data-ttu-id="9d010-163">既存の Azure Virtual Network 内に既存の DNS サーバーがある場合、オンプレミス ネットワークの DNS サーバーではなく、それらをディレクトリ同期サーバーで使用して名前解決を行うかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="9d010-163">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="9d010-164">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you.</span><span class="sxs-lookup"><span data-stu-id="9d010-164">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you.</span></span> <span data-ttu-id="9d010-165">The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span><span class="sxs-lookup"><span data-stu-id="9d010-165">The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="9d010-166">展開のロードマップ</span><span class="sxs-lookup"><span data-stu-id="9d010-166">Deployment roadmap</span></span>

<span data-ttu-id="9d010-167">Azure の仮想マシンへの Azure AD Connect の展開には、3つのフェーズがあります。</span><span class="sxs-lookup"><span data-stu-id="9d010-167">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="9d010-168">フェーズ 1:Azure 仮想ネットワークを作成および構成する</span><span class="sxs-lookup"><span data-stu-id="9d010-168">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="9d010-169">フェーズ 2:Azure 仮想マシンを作成および構成する</span><span class="sxs-lookup"><span data-stu-id="9d010-169">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="9d010-170">フェーズ 3: Azure AD Connect をインストールして構成する</span><span class="sxs-lookup"><span data-stu-id="9d010-170">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="9d010-171">展開後に、Microsoft 365 で新しいユーザーアカウントの場所とライセンスを割り当てる必要もあります。</span><span class="sxs-lookup"><span data-stu-id="9d010-171">After deployment, you must also assign locations and licenses for the new user accounts in Microsoft 365.</span></span>


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="9d010-172">フェーズ 1: Azure Virtual Network を作成および構成する</span><span class="sxs-lookup"><span data-stu-id="9d010-172">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="9d010-173">Azure 仮想ネットワークを作成および構成するには、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」の展開ロードマップにある「[フェーズ 1: オンプレミス ネットワークの準備](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network)」および「[フェーズ 2: Azure でのクロスプレミスの仮想ネットワークの作成](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure)」を完了してください。</span><span class="sxs-lookup"><span data-stu-id="9d010-173">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="9d010-174">以下が最終的な構成です。</span><span class="sxs-lookup"><span data-stu-id="9d010-174">This is your resulting configuration.</span></span>
  
![Azure でホストされている Microsoft 365 のディレクトリ同期サーバーのフェーズ1](media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="9d010-176">この図は、サイト間 VPN や ExpressRoute 接続を介してAzure 仮想ネットワークに接続しているオンプレミスネットワークを示しています。</span><span class="sxs-lookup"><span data-stu-id="9d010-176">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="9d010-177">フェーズ 2:Azure 仮想マシンを作成および構成する</span><span class="sxs-lookup"><span data-stu-id="9d010-177">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="9d010-178">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098).</span><span class="sxs-lookup"><span data-stu-id="9d010-178">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098).</span></span> <span data-ttu-id="9d010-179">Use the following settings:</span><span class="sxs-lookup"><span data-stu-id="9d010-179">Use the following settings:</span></span>
  
- <span data-ttu-id="9d010-180">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network.</span><span class="sxs-lookup"><span data-stu-id="9d010-180">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network.</span></span> <span data-ttu-id="9d010-181">Record the user name and password in a secure location.</span><span class="sxs-lookup"><span data-stu-id="9d010-181">Record the user name and password in a secure location.</span></span> <span data-ttu-id="9d010-182">You will need these later to connect to the virtual machine.</span><span class="sxs-lookup"><span data-stu-id="9d010-182">You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="9d010-183">**[サイズの選択]** ウィンドウで、 **A2 標準** サイズを選択します。</span><span class="sxs-lookup"><span data-stu-id="9d010-183">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="9d010-184">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type.</span><span class="sxs-lookup"><span data-stu-id="9d010-184">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type.</span></span> <span data-ttu-id="9d010-185">In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet).</span><span class="sxs-lookup"><span data-stu-id="9d010-185">In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet).</span></span> <span data-ttu-id="9d010-186">Leave all other settings at their default values.</span><span class="sxs-lookup"><span data-stu-id="9d010-186">Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="9d010-187">内部 DNS をチェックして、ディレクトリ同期サーバーが DNS を正しく使用していることを検証し、仮想マシンに IP アドレスのアドレス (A) レコードが追加されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="9d010-187">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="9d010-188">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon) to connect to the directory sync server with a Remote Desktop Connection.</span><span class="sxs-lookup"><span data-stu-id="9d010-188">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon) to connect to the directory sync server with a Remote Desktop Connection.</span></span> <span data-ttu-id="9d010-189">After signing in, join the virtual machine to the on-premises AD DS domain.</span><span class="sxs-lookup"><span data-stu-id="9d010-189">After signing in, join the virtual machine to the on-premises AD DS domain.</span></span>
  
<span data-ttu-id="9d010-190">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server.</span><span class="sxs-lookup"><span data-stu-id="9d010-190">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server.</span></span> <span data-ttu-id="9d010-191">You should contact your network administrator for any additional configuration steps to perform.</span><span class="sxs-lookup"><span data-stu-id="9d010-191">You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="9d010-192">以下が最終的な構成です。</span><span class="sxs-lookup"><span data-stu-id="9d010-192">This is your resulting configuration.</span></span>
  
![Azure でホストされている Microsoft 365 のディレクトリ同期サーバーのフェーズ2](media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="9d010-194">この図に、クロスプレミス Azure 仮想ネットワーク内のディレクトリ同期サーバーとしての仮想マシンを示します。</span><span class="sxs-lookup"><span data-stu-id="9d010-194">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="9d010-195">フェーズ 3: Azure AD Connect をインストールして構成する</span><span class="sxs-lookup"><span data-stu-id="9d010-195">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="9d010-196">次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="9d010-196">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="9d010-197">Connect to the directory sync server using a Remote Desktop Connection with an AD DS domain account that has local administrator privileges.</span><span class="sxs-lookup"><span data-stu-id="9d010-197">Connect to the directory sync server using a Remote Desktop Connection with an AD DS domain account that has local administrator privileges.</span></span> <span data-ttu-id="9d010-198">See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon).</span><span class="sxs-lookup"><span data-stu-id="9d010-198">See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon).</span></span>
    
2. <span data-ttu-id="9d010-199">ディレクトリ同期を使用して、「 [Microsoft 365 用のディレクトリ同期をセットアップ](set-up-directory-synchronization.md)する」という記事を開き、「パスワードのハッシュ同期を使用したディレクトリ同期」の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="9d010-199">From the directory sync server, open the [Set up directory synchronization for Microsoft 365](set-up-directory-synchronization.md) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="9d010-200">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU).</span><span class="sxs-lookup"><span data-stu-id="9d010-200">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU).</span></span> <span data-ttu-id="9d010-201">Do not move or remove this account or synchronization will fail.</span><span class="sxs-lookup"><span data-stu-id="9d010-201">Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="9d010-202">以下が最終的な構成です。</span><span class="sxs-lookup"><span data-stu-id="9d010-202">This is your resulting configuration.</span></span>
  
![Azure でホストされている Microsoft 365 のディレクトリ同期サーバーのフェーズ3](media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="9d010-204">この図に、クロスプレミス Azure 仮想ネットワーク内の Azure AD Connect を使ったディレクトリ同期サーバーを示します。</span><span class="sxs-lookup"><span data-stu-id="9d010-204">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a><span data-ttu-id="9d010-205">Microsoft 365 でユーザーに場所とライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="9d010-205">Assign locations and licenses to users in Microsoft 365</span></span>

<span data-ttu-id="9d010-206">Azure AD Connect は、オンプレミス AD DS から Microsoft 365 サブスクリプションにアカウントを追加しますが、ユーザーが Microsoft 365 にサインインしてそのサービスを使用するには、アカウントを場所とライセンスで構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d010-206">Azure AD Connect adds accounts to your Microsoft 365 subscription from the on-premises AD DS, but in order for users to sign in to Microsoft 365 and use its services, the accounts must be configured with a location and licenses.</span></span> <span data-ttu-id="9d010-207">次の手順で、適切なユーザーアカウントに場所を追加し、ライセンス認証を行います。</span><span class="sxs-lookup"><span data-stu-id="9d010-207">Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="9d010-208">[Microsoft 365 管理センター](https://admin.microsoft.com)にサインインし、[**管理者**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d010-208">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="9d010-209">左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d010-209">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="9d010-210">ユーザーアカウントのリストで、アクティブにするユーザー名の隣にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="9d010-210">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="9d010-211">ユーザーのページで、**[製品ライセンス]** の **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d010-211">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="9d010-212">**[製品ライセンス]** ページの **[場所]** でユーザーの場所を選択し、ユーザーの適切なライセンスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9d010-212">On the **Product licenses** page, select a location for the user for **Location**, and then enable the appropriate licenses for the user.</span></span>
    
6. <span data-ttu-id="9d010-213">完了したら、**[保存]** をクリックし、2 回 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d010-213">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="9d010-214">別のユーザーについては、手順 3 に戻ります。</span><span class="sxs-lookup"><span data-stu-id="9d010-214">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="9d010-215">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d010-215">See also</span></span>

[<span data-ttu-id="9d010-216">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="9d010-216">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)
  
[<span data-ttu-id="9d010-217">オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する</span><span class="sxs-lookup"><span data-stu-id="9d010-217">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="9d010-218">Azure AD Connect をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="9d010-218">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="9d010-219">Microsoft 365 のディレクトリ同期をセットアップする</span><span class="sxs-lookup"><span data-stu-id="9d010-219">Set up directory synchronization for Microsoft 365</span></span>](set-up-directory-synchronization.md)
  
