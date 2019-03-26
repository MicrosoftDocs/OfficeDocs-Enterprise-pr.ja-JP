---
title: Microsoft Azure での Office 365 ディレクトリ同期の展開
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: '概要: Azure の仮想マシン上に Azure AD Connect を展開し、オンプレミス ディレクトリと Office 365 サブスクリプションの Azure AD テナントとの間でアカウントを同期します。'
ms.openlocfilehash: 4b248dd0a5f6fc775fca322b696703545a1ef465
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574031"
---
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="377b2-103">Microsoft Azure での Office 365 ディレクトリ同期の展開</span><span class="sxs-lookup"><span data-stu-id="377b2-103">Deploy Office 365 Directory Synchronization in Microsoft Azure</span></span>

 <span data-ttu-id="377b2-104">**概要:** Azure インフラストラクチャ サービスの仮想マシン上に Azure AD Connect をデプロイし、オンプレミス ディレクトリと Office 365 サブスクリプションの Azure AD テナントとの間でアカウントを同期します。</span><span class="sxs-lookup"><span data-stu-id="377b2-104">**Summary:** Deploy Azure AD Connect on a virtual machine in Azure infrastructure services to synchronize accounts between your on-premises directory and the Azure AD tenant of your Office 365 subscription.</span></span>
  
<span data-ttu-id="377b2-p101">Azure Active Directory (AD) Connect (以前は、ディレクトリ同期ツール、Directory Sync ツール、DirSync.exe ツールなどと呼ばれていました) は、ドメインに参加しているサーバーにインストールして、オンプレミスの Windows Server Active Directory (AD) ユーザーを Office 365 サブスクリプションの Azure AD テナントに同期するアプリケーションです。Office 365 では、ディレクトリ サービスに Azure Active Directory (Azure AD) を使用しています。Office 365 サブスクリプションには、Azure AD テナントが含まれています。このテナントは、他の SaaS アプリケーションや Azure のアプリなど、別のクラウド ワークロードで組織の ID を管理するためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="377b2-p101">Azure Active Directory (AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is an application that you install on a domain-joined server to synchronize your on-premises Windows Server Active Directory (AD) users to the Azure AD tenant of your Office 365 subscription. Office 365 uses Azure Active Directory (Azure AD) for its directory service. Your Office 365 subscription includes an Azure AD tenant. This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span>

<span data-ttu-id="377b2-109">Azure AD Connect はオンプレミス サーバーにインストールできますが、次の理由により、Azure の仮想マシンにもインストールできます。</span><span class="sxs-lookup"><span data-stu-id="377b2-109">You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for these reasons:</span></span>
  
- <span data-ttu-id="377b2-110">クラウド ベースのサーバーをより迅速にプロビジョニングして構成でき、ユーザーがすぐにサービスを利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="377b2-110">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
- <span data-ttu-id="377b2-111">Azure では、より少ない労力でより良いサイト可用性が得られます。</span><span class="sxs-lookup"><span data-stu-id="377b2-111">Azure offers better site availability with less effort.</span></span>
- <span data-ttu-id="377b2-112">組織内のオンプレミス サーバーの数を削減できます。</span><span class="sxs-lookup"><span data-stu-id="377b2-112">You can reduce the number of on-premises servers in your organization.</span></span>

<span data-ttu-id="377b2-p102">このソリューションには、オンプレミス ネットワークと Azure Virtual Network 間の接続が必要です。詳しくは、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="377b2-p102">This solution requires connectivity between your on-premises network and your Azure virtual network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="377b2-p103">この記事では、1 つのフォレスト内の単一ドメインの同期について説明します。Azure AD Connect は、Active Directory フォレスト内のすべての Windows Server AD ドメインを Office 365 と同期します。複数の Active Directory フォレストを Office 365 と同期する場合には、「[シングル サインオン シナリオでの Multi-forest ディレクトリ同期](https://go.microsoft.com/fwlink/p/?LinkId=393091)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="377b2-p103">This article describes synchronization of a single domain in a single forest. Azure AD Connect synchronizes all Windows Server AD domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a><span data-ttu-id="377b2-118">Azure における Office 365 ディレクトリ同期のデプロイに関する概要</span><span class="sxs-lookup"><span data-stu-id="377b2-118">Overview of deploying Office 365 directory synchronization in Azure</span></span>

<span data-ttu-id="377b2-119">次の図は、オンプレミスの Windows Server AD フォレストを Office 365 サブスクリプションに同期する Azure AD Connect を示したものです。Azure AD Connect は Azure (ディレクトリ同期サーバー) の仮想マシンで実行されています。</span><span class="sxs-lookup"><span data-stu-id="377b2-119">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises Windows Server AD forest to an Office 365 subscription.</span></span>
  
![Azure 内の仮想マシン上の Azure AD 接続ツールが、トラフィック フローを伴う Office 365 サブスクリプションの Azure AD テナントに、オンプレミス アカウントを同期しています](media/CP-DirSyncOverview.png)
  
<span data-ttu-id="377b2-p104">この図には、サイト間 VPN または ExpressRoute 接続で接続されている 2 つのネットワークがあります。具体的には、Windows Server AD ドメイン コントローラーが配置されているオンプレミス ネットワークと、ディレクトリ同期サーバーとして [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) を実行している仮想マシンが含まれる Azure 仮想ネットワークの 2 つです。ディレクトリ同期サーバーを発信元とする主要なトラフィック フローは 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="377b2-p104">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where Windows Server AD domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="377b2-124">Azure AD Connect は、アカウントとパスワードの変更に関してオンプレミス ネットワーク上のドメイン コントローラーにクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="377b2-124">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
-  <span data-ttu-id="377b2-p105">Azure AD Connect は、アカウントとパスワードの変更を Office 365 サブスクリプションの Azure AD インスタンスに送信します。ディレクトリ同期サーバーはオンプレミス ネットワークの拡張部分であるため、これらの変更はオンプレミス ネットワークのプロキシ サーバーを経由して送信されます。</span><span class="sxs-lookup"><span data-stu-id="377b2-p105">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Office 365 subscription. Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="377b2-p106">このソリューションでは、1 つの Active Directory フォレスト内の単一 Active Directory ドメインの同期について説明します。Azure AD Connect は、Active Directory フォレスト内のすべての Active Directory ドメインを Office 365 と同期します。複数の Active Directory フォレストを Office 365 と同期する場合には、「[シングル サインオン シナリオでの Multi-forest ディレクトリ同期](https://go.microsoft.com/fwlink/p/?LinkId=393091)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="377b2-p106">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest. Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="377b2-130">このソリューションをデプロイする場合には、次の 2 つの主要な手順があります。</span><span class="sxs-lookup"><span data-stu-id="377b2-130">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="377b2-p107">Azure Virtual Network を作成し、オンプレミスネットワークに対するサイト間 VPN 接続を確立します。詳しくは、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="377b2-p107">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="377b2-p108">[Azure AD Connect ](https://www.microsoft.com/download/details.aspx?id=47594) を Azure のドメインに参加している仮想マシン上にインストールし、オンプレミス Windows Server AD を Office 365 に同期します。これには以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="377b2-p108">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises Windows Server AD to Office 365. This involves:</span></span>
    
    <span data-ttu-id="377b2-135">Azure AD Connect を実行するため、Azure Virtual Machine を作成します。</span><span class="sxs-lookup"><span data-stu-id="377b2-135">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="377b2-136">[Azure AD Connect ](https://www.microsoft.com/download/details.aspx?id=47594) をインストールし、設定します。</span><span class="sxs-lookup"><span data-stu-id="377b2-136">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="377b2-p109">Azure AD Connect の設定には、Azure AD 管理者アカウントの資格情報 (ユーザー名とパスワード) と、Windows Server AD エンタープライズ管理者アカウントが必要です。Azure AD Connect ツールはすぐに実行され、オンプレミスの Windows Server AD フォレストを Office 365 に継続的に同期します。</span><span class="sxs-lookup"><span data-stu-id="377b2-p109">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a Windows Server AD enterprise administrator account. Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises Windows Server AD forest to Office 365.</span></span>
    
<span data-ttu-id="377b2-139">運用環境でこのソリューションをデプロイする前に、「[Office 365 開発/テスト環境のディレクトリ同期](dirsync-for-your-office-365-dev-test-environment.md)」の手順に従って、概念実証、デモンストレーション、実験用にこの構成を設定することができます。</span><span class="sxs-lookup"><span data-stu-id="377b2-139">Before you deploy this solution in production, you can use the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="377b2-140">Azure AD Connect の設定が完了しても、Windows Server AD エンタープライズ管理者アカウントの資格情報は保存されません。</span><span class="sxs-lookup"><span data-stu-id="377b2-140">When Azure AD Connect configuration completes, it does not save the Windows Server AD enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="377b2-p110">このソリューションは、1 つの Windows Server AD フォレストを Office 365 と同期する方法について説明しています。この記事で取り上げられているトポロジは、このソリューションを実装する 1 つの方法に過ぎません。組織のトポロジは、固有のネットワーク要件とセキュリティに関する考慮事項によって異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="377b2-p110">This solution describes synchronizing a single Windows Server AD forest to Office 365. The topology discussed in this article represents only one way to implement this solution. Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a><span data-ttu-id="377b2-144">Azure の Office 365 向けにディレクトリ同期サーバーをホストするための計画</span><span class="sxs-lookup"><span data-stu-id="377b2-144">Plan for hosting a directory sync server for Office 365 in Azure</span></span>
<span data-ttu-id="377b2-145"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="377b2-145"></span></span>

### <a name="prerequisites"></a><span data-ttu-id="377b2-146">前提条件</span><span class="sxs-lookup"><span data-stu-id="377b2-146">Prerequisites</span></span>

<span data-ttu-id="377b2-147">開始する前に、このソリューションの以下の前提条件を確認してください。</span><span class="sxs-lookup"><span data-stu-id="377b2-147">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="377b2-148">「[Azure 仮想ネットワークの計画](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network)」に記されている関連する計画内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="377b2-148">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).</span></span>
    
- <span data-ttu-id="377b2-149">Azure Virtual Network を構成するためのすべての「[前提条件](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites)」を満たしていることを確かめます。</span><span class="sxs-lookup"><span data-stu-id="377b2-149">Ensure that you meet all [Prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="377b2-p111">Active Directory 統合機能が含まれている Office 365 サブスクリプションがあることを確認します。Office 365 サブスクリプションについて詳しくは、「[Office 365 サブスクリプションのページ](https://products.office.com/compare-all-microsoft-office-products?tab=2)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="377b2-p111">Have an Office 365 subscription that includes the Active Directory integration feature. For information about Office 365 subscriptions, go to the [Office 365 subscription page](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span></span>
    
- <span data-ttu-id="377b2-152">Azure AD Connect を実行する 1 つの Azure Virtual Machine をプロビジョニングし、オンプレミスの Windows Server AD フォレストを Office 365 と同期します。</span><span class="sxs-lookup"><span data-stu-id="377b2-152">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises Windows Server AD forest with Office 365.</span></span>
    
    <span data-ttu-id="377b2-153">Windows Server AD エンタープライズ管理者アカウントと Azure AD 管理者アカウントの資格情報 (名前とパスワード) が必要です。</span><span class="sxs-lookup"><span data-stu-id="377b2-153">You must have the credentials (names and passwords) for a Windows Server AD enterprise administrator account and an Azure AD Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="377b2-154">ソリューション アーキテクチャ設計の前提条件</span><span class="sxs-lookup"><span data-stu-id="377b2-154">Solution architecture design assumptions</span></span>

<span data-ttu-id="377b2-155">次の一覧では、このソリューションで採用された設計方針について説明します。</span><span class="sxs-lookup"><span data-stu-id="377b2-155">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="377b2-p112">このソリューションでは、サイト間 VPN 接続を伴う 1 つの Azure Virtual Network を使用します。Azure Virtual Network は 1 つのサブネットをホストし、このサブネットには Azure AD Connect を実行する 1 つのディレクトリ同期サーバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="377b2-p112">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that has one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="377b2-158">オンプレミス ネットワークには、ドメイン コントローラーと DNS サーバーが存在します。</span><span class="sxs-lookup"><span data-stu-id="377b2-158">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="377b2-p113">Azure AD Connect は、シングル サインオンではなくパスワード ハッシュ同期を実行します (Active Directory フェデレーション サービス (AD FS) インフラストラクチャを展開する必要はありません)。パスワード ハッシュ同期とシングル サインオンのオプションの詳細については、「[Azure Active Directory ハイブリッド ID ソリューションの適切な認証方法の選択](http://aka.ms/auth-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="377b2-p113">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](http://aka.ms/auth-options).</span></span>
    
<span data-ttu-id="377b2-p114">ご使用の環境でこのソリューションを展開する場合に考慮できるその他の設計に関する選択内容があります。それらには以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="377b2-p114">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="377b2-164">既存の Azure Virtual Network 内に既存の DNS サーバーがある場合、オンプレミス ネットワークの DNS サーバーではなく、それらをディレクトリ同期サーバーで使用して名前解決を行うかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="377b2-164">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="377b2-p115">既存の Azure Virtual Network にドメイン コントローラーがある場合、Active Directory サイトとサービスを構成するという方法がより有効な選択肢となるかどうかを判別します。ディレクトリ同期サーバーはアカウントとパスワードの変更内容を調べるために、オンプレミス ネットワークのドメイン コントローラーではなく、Azure Virtual Network 内のドメイン コントローラーをクエリできます。</span><span class="sxs-lookup"><span data-stu-id="377b2-p115">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="377b2-167">展開のロードマップ</span><span class="sxs-lookup"><span data-stu-id="377b2-167">Deployment roadmap</span></span>

<span data-ttu-id="377b2-168">Azure の仮想マシンへの Azure AD Connect の展開には、3つのフェーズがあります。</span><span class="sxs-lookup"><span data-stu-id="377b2-168">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="377b2-169">フェーズ 1:Azure 仮想ネットワークを作成および構成する</span><span class="sxs-lookup"><span data-stu-id="377b2-169">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="377b2-170">フェーズ 2:Azure 仮想マシンを作成および構成する</span><span class="sxs-lookup"><span data-stu-id="377b2-170">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="377b2-171">フェーズ 3: Azure AD Connect をインストールして構成する</span><span class="sxs-lookup"><span data-stu-id="377b2-171">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="377b2-172">デプロイ後、Office 365 の新しいユーザー アカウントに場所とライセンスを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="377b2-172">After deployment, you must also assign locations and licenses for the new user accounts in Office 365.</span></span>

<!--  
> [!TIP]
> The [Directory Synchronization Server in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) has all of the Azure PowerShell blocks to build out this solution, the diagrams in Microsoft PowerPoint and Visio format, and a Microsoft Excel configuration workbook that generates Azure PowerShell command blocks customized for your settings.
-->
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="377b2-173">フェーズ 1: Azure Virtual Network を作成および構成する</span><span class="sxs-lookup"><span data-stu-id="377b2-173">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="377b2-174">Azure 仮想ネットワークを作成および構成するには、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」の展開ロードマップにある「[フェーズ 1: オンプレミス ネットワークの準備](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network)」および「[フェーズ 2: Azure でのクロスプレミスの仮想ネットワークの作成](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure)」を完了してください。</span><span class="sxs-lookup"><span data-stu-id="377b2-174">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="377b2-175">以下が最終的な構成です。</span><span class="sxs-lookup"><span data-stu-id="377b2-175">This is your resulting configuration.</span></span>
  
![Azure でホストされている Office 365 のディレクトリ同期サーバーのフェーズ 1](media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="377b2-177">この図は、サイト間 VPN や ExpressRoute 接続を介してAzure 仮想ネットワークに接続しているオンプレミスネットワークを示しています。</span><span class="sxs-lookup"><span data-stu-id="377b2-177">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="377b2-178">フェーズ 2:Azure 仮想マシンを作成および構成する</span><span class="sxs-lookup"><span data-stu-id="377b2-178">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="377b2-p116">「[Azure ポータルで最初の Windows 仮想マシンを作成する](https://go.microsoft.com/fwlink/p/?LinkId=393098)」の説明に従い、Azure に仮想マシンを作成します。以下の設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="377b2-p116">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="377b2-p117">**[基本]** ウィンドウで、仮想ネットワークと同じサブスクリプション、場所およびリソース グループを選択します。ユーザー名とパスワードを安全な場所に記録します。後ほど、仮想マシンに接続するときに必要になります。</span><span class="sxs-lookup"><span data-stu-id="377b2-p117">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="377b2-184">**[サイズの選択]** ウィンドウで、 **A2 標準** サイズを選択します。</span><span class="sxs-lookup"><span data-stu-id="377b2-184">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="377b2-p118">**[設定]** ウィンドウの **[ストレージ]** セクションで、**[標準]** ストレージ タイプを選択します。**[ネットワーク]** セクションで、(ゲートウェイ サブネットではなく) ディレクトリ同期サーバーをホストするための仮想ネットワークの名前とサブネットを選択します。他のすべての設定は、既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="377b2-p118">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="377b2-188">内部 DNS をチェックして、ディレクトリ同期サーバーが DNS を正しく使用していることを検証し、仮想マシンに IP アドレスのアドレス (A) レコードが追加されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="377b2-188">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="377b2-p119">「[仮想マシンへの接続とサインオン](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)」の説明を参照してリモートデスクトップ接続でディレクトリ同期サーバーに接続します。サインイン後、仮想マシンをオンプレミス Windows Server AD ドメインに参加させます。</span><span class="sxs-lookup"><span data-stu-id="377b2-p119">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises Windows Server AD domain.</span></span>
  
<span data-ttu-id="377b2-p120">Azure AD Connect がインターネット リソースにアクセスできるようにするには、オンプレミス ネットワークのプロキシ サーバーを使用するようディレクトリ同期サーバーを構成する必要があります。実行する追加の構成手順は、ネットワーク管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="377b2-p120">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="377b2-193">以下が最終的な構成です。</span><span class="sxs-lookup"><span data-stu-id="377b2-193">This is your resulting configuration.</span></span>
  
![Azure でホストされている Office 365 のディレクトリ同期サーバーのフェーズ 2](media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="377b2-195">この図に、クロスプレミス Azure 仮想ネットワーク内のディレクトリ同期サーバーとしての仮想マシンを示します。</span><span class="sxs-lookup"><span data-stu-id="377b2-195">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="377b2-196">フェーズ 3: Azure AD Connect をインストールして構成する</span><span class="sxs-lookup"><span data-stu-id="377b2-196">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="377b2-197">次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="377b2-197">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="377b2-p121">ローカル管理者権限を持つ Windows Server AD ドメイン アカウントを使用して、リモート デスクトップ接続でディレクトリ同期サーバーに接続します。「[仮想マシンへの接続とサインオン](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="377b2-p121">Connect to the directory sync server using a Remote Desktop Connection with a Windows Server AD domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span></span>
    
2. <span data-ttu-id="377b2-200">パスワード ハッシュ同期を使用したディレクトリ同期を行うには、ディレクトリ同期サーバーから「[Office 365 のディレクトリ同期をセットアップする](set-up-directory-synchronization.md)」という記事を開き、指示に従います。</span><span class="sxs-lookup"><span data-stu-id="377b2-200">From the directory sync server, open the [Set up directory synchronization for Office 365](set-up-directory-synchronization.md) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="377b2-p122">セットアップによって、ローカル ユーザー組織単位 (OU) 内に **AAD_xxxxxxxxxxxx** というアカウントが作成されます。このアカウントは移動も削除も行わないでください。移動や削除を行うと、同期が失敗します。</span><span class="sxs-lookup"><span data-stu-id="377b2-p122">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="377b2-203">以下が最終的な構成です。</span><span class="sxs-lookup"><span data-stu-id="377b2-203">This is your resulting configuration.</span></span>
  
![Azure でホストされている Office 365 のディレクトリ同期サーバーのフェーズ 3](media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="377b2-205">この図に、クロスプレミス Azure 仮想ネットワーク内の Azure AD Connect を使ったディレクトリ同期サーバーを示します。</span><span class="sxs-lookup"><span data-stu-id="377b2-205">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a><span data-ttu-id="377b2-206">Office 365 のユーザーに場所とライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="377b2-206">Assign locations and licenses to users in Office 365</span></span>

<span data-ttu-id="377b2-p123">Azure AD Connect はオンプレミスの Windows Server AD から Office 365 サブスクリプションにアカウントを追加しますが、ユーザーが Office 365 にサインインしてそのサービスを利用するには、アカウントに場所とライセンスが設定されている必要があります。次の手順で、適切なユーザー アカウントに場所を追加し、ライセンス認証を行います。</span><span class="sxs-lookup"><span data-stu-id="377b2-p123">Azure AD Connect adds accounts to your Office 365 subscription from the on-premises Windows Server AD, but in order for users to sign in to Office 365 and use its services, the accounts must be configured with a location and licenses. Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="377b2-209">[Office 365 ポータル ページ](https://www.office.com)にサインインして、**[管理者]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="377b2-209">Sign in to the [Office 365 portal page](https://www.office.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="377b2-210">左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="377b2-210">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="377b2-211">ユーザーアカウントのリストで、アクティブにするユーザー名の隣にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="377b2-211">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="377b2-212">ユーザーのページで、**[製品ライセンス]** の **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="377b2-212">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="377b2-213">**[製品ライセンス]** ページの **[場所]** でユーザーの場所を選択し、ユーザーの適切なライセンスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="377b2-213">On the **Product licenses** page, select a location for the user for **Location**, and then enable the appropriate licenses for the user.</span></span>
    
6. <span data-ttu-id="377b2-214">完了したら、**[保存]** をクリックし、2 回 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="377b2-214">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="377b2-215">別のユーザーについては、手順 3 に戻ります。</span><span class="sxs-lookup"><span data-stu-id="377b2-215">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="377b2-216">関連項目</span><span class="sxs-lookup"><span data-stu-id="377b2-216">See also</span></span>

[<span data-ttu-id="377b2-217">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="377b2-217">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="377b2-218">オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する</span><span class="sxs-lookup"><span data-stu-id="377b2-218">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="377b2-219">Azure AD Connect をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="377b2-219">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="377b2-220">Office 365 のディレクトリ同期のセットアップ</span><span class="sxs-lookup"><span data-stu-id="377b2-220">Set up directory synchronization for Office 365</span></span>](set-up-directory-synchronization.md)
  
<!--
[Directory Synchronization server in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)
-->


