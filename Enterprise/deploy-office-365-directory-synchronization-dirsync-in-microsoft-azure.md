---
title: Microsoft Azure で Office 365 のディレクトリ同期を展開します。
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: '概要: は、設置ディレクトリと、Office 365 サブスクリプションの Azure AD テナントとの間のアカウントを同期するのには Azure の仮想マシン上の Azure AD 接続を展開します。'
ms.openlocfilehash: af0c837ead0ddfce31d7f3635f3283f118d26dca
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="86fd9-103">Microsoft Azure で Office 365 のディレクトリ同期を展開します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-103">Deploy Office 365 Directory Synchronization in Microsoft Azure</span></span>

 <span data-ttu-id="86fd9-104">**の概要:**Azure の AD 接続、設置ディレクトリと、Office 365 サブスクリプションの Azure AD テナントとの間のアカウントを同期するのには Azure の仮想マシン上に配置します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-104">**Summary:** Deploy Azure AD Connect on a virtual machine in Azure to synchronize accounts between your on-premises directory and the Azure AD tenant of your Office 365 subscription.</span></span>
  
<span data-ttu-id="86fd9-p101">Azure Active Directory (AD) Connect (以前のディレクトリ同期ツール、Directory 同期ツール、DirSync.exe ツール) は、ドメインに参加しているサーバー上にインストールするサーバーベースのアプリケーションで、オンプレミスの Windows Server Active Directory ユーザーを Office 365 サブスクリプションの Azure Active Directory テナントと同期するために使用します。Azure AD Connect はオンプレミスのサーバーにインストールできますが、次の理由により、Azure の仮想マシンにもインストールできます。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p101">Azure Active Directory (AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is a server-based application that you install on a domain-joined server to synchronize your on-premises Windows Server Active Directory users to the Azure Active Directory tenant of your Office 365 subscription. You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for the following reasons:</span></span>
  
- <span data-ttu-id="86fd9-107">クラウド ベースのサーバーをより迅速に準備して構成でき、ユーザーがすぐにサービスを利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="86fd9-107">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
    
- <span data-ttu-id="86fd9-108">Azure では、より少ない労力でより良いサイト可用性が得られます。</span><span class="sxs-lookup"><span data-stu-id="86fd9-108">Azure offers better site availability with less effort.</span></span>
    
- <span data-ttu-id="86fd9-109">組織内のオンプレミス サーバーの数を削減できます。</span><span class="sxs-lookup"><span data-stu-id="86fd9-109">You can reduce the number of on-premises servers in your organization.</span></span>
    
> [!IMPORTANT]
> <span data-ttu-id="86fd9-p102">このソリューションには、オンプレミス ネットワークと Azure Virtual Network 間の接続が必要です。詳しくは、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p102">This solution requires connectivity between your on-premises network and your Azure Virtual Network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="86fd9-p103">この記事では、1 つのフォレスト内の単一ドメインの同期について説明します。Azure AD Connect は、Active Directory フォレスト内のすべての Windows Server AD ドメインを Office 365 と同期します。複数の Active Directory フォレストを Office 365 と同期する場合には、「[シングル サインオン シナリオでの Multi-forest ディレクトリ同期](https://go.microsoft.com/fwlink/p/?LinkId=393091)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p103">This article describes synchronization of a single domain in a single forest. Azure AD Connect synchronizes all Windows Server AD domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="86fd9-p104">Office 365 はディレクトリ サービスに Azure Active Directory (Azure AD) を使用します。Office 365 サブスクリプションには Azure AD テナントが含まれます。このテナントは他の SaaS アプリケーションと Azure のアプリを含む、他のクラウドのワークロードで組織の ID を管理するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p104">Office 365 uses Azure Active Directory (Azure AD) for its directory service. Your Office 365 subscription includes an Azure AD tenant. This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span> 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a><span data-ttu-id="86fd9-118">Azure における Office 365 ディレクトリ同期の展開に関する概要</span><span class="sxs-lookup"><span data-stu-id="86fd9-118">Overview of deploying Office 365 directory synchronization in Azure</span></span>
<span data-ttu-id="86fd9-119"><a name="Overview"> </a></span><span class="sxs-lookup"><span data-stu-id="86fd9-119"><a name="Overview"> </a></span></span>

<span data-ttu-id="86fd9-120">AnOffice 365 サブスクリプションへの設置型 Windows サーバーの AD フォレストを同期する (ディレクトリ同期サーバー) の Azure の仮想マシンで実行されている Azure の AD 接続を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-120">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises Windows Server AD forest to anOffice 365 subscription.</span></span>
  
![Azure 内の仮想マシン上の Azure AD 接続ツールが、トラフィック フローを伴う Office 365 サブスクリプションの Azure AD テナントに、オンプレミス アカウントを同期しています](images/CP_DirSyncOverview.png)
  
<span data-ttu-id="86fd9-p105">ダイアグラムでは、サイト間の VPN または ExpressRoute の接続で接続された 2 つのネットワークがあります。設置ネットワーク、Windows サーバーの AD ドメイン コント ローラーの位置と、ディレクトリ同期サーバー、仮想マシンと Azure の仮想ネットワークがある[Azure AD 接続](https://www.microsoft.com/download/details.aspx?id=47594)を実行します。ディレクトリ同期サーバーから送信された 2 つのメインのトラフィック フローがあります。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p105">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where Windows Server AD domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="86fd9-125">Azure AD Connect は、アカウントとパスワードの変更に関してオンプレミス ネットワーク上のドメイン コントローラーにクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-125">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
    
-  <span data-ttu-id="86fd9-p106">Azure AD 接続では、アカウントおよびパスワードには、Office 365 サブスクリプションの Azure AD インスタンスに変更を送信します。ディレクトリ同期サーバーは、オンプレミスのネットワークの拡張部分であるために、設置型ネットワークのプロキシ サーバーをこれらの変更が送信されます。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p106">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Office 365 subscription. Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="86fd9-p107">このソリューションでは、1 つの Active Directory フォレスト内の単一 Active Directory ドメインの同期について説明します。Azure AD Connect は、Active Directory フォレスト内のすべての Active Directory ドメインを Office 365 と同期します。複数の Active Directory フォレストを Office 365 と同期する場合には、「[シングル サインオン シナリオでの Multi-forest ディレクトリ同期](https://go.microsoft.com/fwlink/p/?LinkId=393091)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p107">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest. Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Office 365. If you have multiple Active Directory forests to synchronize with Office 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=393091).</span></span> 
  
<span data-ttu-id="86fd9-p108">どちらの場合であっても、Azure 仮想マシンで実行されている Azure AD Connect から発信されるトラフィックは Azure の仮想ネットワーク上のゲートウェイに送られ、その後、サイト間 VPN または ExpressRoute 接続を介してオンプレミス ネットワークの VPN gateway デバイスに送られます。オンプレミス ネットワークのルーティング インフラストラクチャにより、次に、ドメイン コントローラーやプロキシ サーバーなどの宛先にトラフィックが転送されます。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p108">In both cases, the traffic originated by Azure AD Connect running on the Azure virtual machine is forwarded to a gateway on the virtual network in Azure, which then forwards the traffic across the site-to-site VPN or ExpressRoute connection to the VPN gateway device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination, such as a domain controller or a proxy server.</span></span>
  
<span data-ttu-id="86fd9-133">このソリューションを展開する場合には、次の 2 つの主要な手順があります。</span><span class="sxs-lookup"><span data-stu-id="86fd9-133">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="86fd9-p109">Azure Virtual Network を作成し、オンプレミスネットワークに対するサイト間 VPN 接続を確立します。詳しくは、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p109">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="86fd9-p110">[Azure AD Connect ](https://www.microsoft.com/download/details.aspx?id=47594) を Azure のドメインに参加している仮想マシン上にインストールし、オンプレミス Windows Server AD を Office 365 に同期します。これには以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p110">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises Windows Server AD to Office 365. This involves:</span></span>
    
    <span data-ttu-id="86fd9-138">Azure AD Connect を実行するため、Azure Virtual Machine を作成します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-138">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="86fd9-139">[Azure AD Connect ](https://www.microsoft.com/download/details.aspx?id=47594) をインストールし、設定します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-139">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="86fd9-p111">Azure AD Connect の設定には、Azure AD 管理者アカウントの資格情報 (ユーザー名とパスワード) と、Windows Server AD エンタープライズ管理者アカウントが必要です。Azure AD Connect ツールはすぐに実行され、オンプレミスの Windows Server AD フォレストを Office 365 に継続的に同期します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p111">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a Windows Server AD enterprise administrator account. Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises Windows Server AD forest to Office 365.</span></span>
    
<span data-ttu-id="86fd9-142">実稼働環境でこのソリューションを展開する前に、デモ、または実験のための概念実証としてこの構成をセットアップするのには[、Office 365 の開発/テスト環境のディレクトリ同期処理](dirsync-for-your-office-365-dev-test-environment.md)の指示を使用します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-142">Before you deploy this solution in production, use the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="86fd9-143">Azure AD Connect の設定が完了しても、Windows Server AD エンタープライズ管理者アカウントの資格情報は保存されません。</span><span class="sxs-lookup"><span data-stu-id="86fd9-143">When Azure AD Connect configuration completes, it does not save the Windows Server AD enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="86fd9-p112">このソリューションは、1 つの Windows Server AD フォレストを Office 365 と同期する方法について説明しています。この記事で取り上げられているトポロジは、このソリューションを実装する 1 つの方法に過ぎません。組織のトポロジは、固有のネットワーク要件とセキュリティに関する考慮事項によって異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p112">This solution describes synchronizing a single Windows Server AD forest to Office 365. The topology discussed in this article represents only one way to implement this solution. Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a><span data-ttu-id="86fd9-147">Azure 内の Office 365 のディレクトリ同期サーバーをホストするための計画</span><span class="sxs-lookup"><span data-stu-id="86fd9-147">Plan for hosting a directory sync server for Office 365 in Azure</span></span>
<span data-ttu-id="86fd9-148"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="86fd9-148"><a name="PlanningVirtual"> </a></span></span>

### <a name="prerequisites"></a><span data-ttu-id="86fd9-149">前提条件</span><span class="sxs-lookup"><span data-stu-id="86fd9-149">Prerequisites</span></span>

<span data-ttu-id="86fd9-150">開始する前に、このソリューションの以下の前提条件を確認してください。</span><span class="sxs-lookup"><span data-stu-id="86fd9-150">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="86fd9-151">「[Azure 仮想ネットワークの計画](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual)」に記されている関連する計画内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-151">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual).</span></span>
    
- <span data-ttu-id="86fd9-152">Azure Virtual Network を構成するためのすべての「[前提条件](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites)」を満たしていることを確かめます。</span><span class="sxs-lookup"><span data-stu-id="86fd9-152">Ensure that you meet all [prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="86fd9-p113">Active Directory 統合機能が含まれている Office 365 サブスクリプションがあることを確認します。Office 365 サブスクリプションについて詳しくは、「[Office 365 サブスクリプションのページ](https://go.microsoft.com/fwlink/p/?LinkId=394278)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p113">Have an Office 365 subscription that includes the Active Directory integration feature. For information about Office 365 subscriptions, go to the [Office 365 subscription page](https://go.microsoft.com/fwlink/p/?LinkId=394278).</span></span>
    
- <span data-ttu-id="86fd9-155">Azure AD Connect を実行する 1 つの Azure Virtual Machine を準備し、オンプレミスの Windows Server AD フォレストを Office 365 と同期します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-155">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises Windows Server AD forest with Office 365.</span></span>
    
    <span data-ttu-id="86fd9-156">Windows Server AD エンタープライズ管理者アカウントと Azure Active Directory 管理者アカウントの資格情報 (名前とパスワード) が必要です。</span><span class="sxs-lookup"><span data-stu-id="86fd9-156">You must have the credentials (names and passwords) for a Windows Server AD enterprise administrator account and an Azure Active Directory Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="86fd9-157">ソリューション アーキテクチャ設計の前提条件</span><span class="sxs-lookup"><span data-stu-id="86fd9-157">Solution architecture design assumptions</span></span>

<span data-ttu-id="86fd9-158">次の一覧では、このソリューションで採用された設計方針について説明します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-158">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="86fd9-p114">このソリューションでは、サイト間 VPN 接続で 1 つの Azure 仮想ネットワークを使用します。Azure の仮想ネットワークは、1 つのサーバーを含むサブネットが 1 つ、Azure AD 接続を実行してディレクトリ同期サーバーをホストします。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p114">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that contains one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="86fd9-161">オンプレミス ネットワークには、ドメイン コントローラーと DNS サーバーが存在します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-161">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="86fd9-p115">Azure AD 接続では、シングル サインオンではなくパスワード ハッシュの同期を実行します。Active Directory フェデレーション サービス (AD FS) インフラストラクチャを導入する必要はありません。パスワード ハッシュの同期とシングル サインオンのオプションに関する詳細について[を使用するディレクトリの統合シナリオを決定する](https://go.microsoft.com/fwlink/p/?LinkId=393094)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p115">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Determine which directory integration scenario to use](https://go.microsoft.com/fwlink/p/?LinkId=393094).</span></span>
    
<span data-ttu-id="86fd9-p116">ご使用の環境でこのソリューションを展開する場合に考慮できるその他の設計に関する選択内容があります。それらには以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p116">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="86fd9-167">Azure の既存の仮想ネットワーク内の DNS サーバーが既に存在する場合は、オンプレミスのネットワーク上の DNS サーバーではなく、名前解決に使用するディレクトリ同期サーバーにするかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-167">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="86fd9-p117">Azure の既存の仮想ネットワーク内のドメイン コント ローラーがある場合は、Active Directory サイトとサービスを構成するとするのに適して可能性があるかどうかを決定します。ディレクトリ同期サーバーは、アカウントと、オンプレミスのネットワーク上のドメイン コント ローラーではなくパスワードの変更の Azure の仮想ネットワークのドメイン コント ローラーを照会できます。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p117">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="86fd9-170">展開のロードマップ</span><span class="sxs-lookup"><span data-stu-id="86fd9-170">Deployment roadmap</span></span>
<span data-ttu-id="86fd9-171"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="86fd9-171"><a name="DeploymentRoadmap"> </a></span></span>

<span data-ttu-id="86fd9-172">Azure の仮想マシンへの Azure AD Connect の展開には、3つのフェーズがあります。</span><span class="sxs-lookup"><span data-stu-id="86fd9-172">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="86fd9-173">フェーズ 1:Azure 仮想ネットワークを作成および構成する</span><span class="sxs-lookup"><span data-stu-id="86fd9-173">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="86fd9-174">フェーズ 2:Azure 仮想マシンを作成および構成する</span><span class="sxs-lookup"><span data-stu-id="86fd9-174">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="86fd9-175">フェーズ 3: Azure AD Connect をインストールして構成する</span><span class="sxs-lookup"><span data-stu-id="86fd9-175">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="86fd9-176">構成後、Office 365 の新しいユーザーアカウントに場所とライセンスを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="86fd9-176">After deployment, you must also assign locations and licenses for the new user accounts in Office 365.</span></span>
  
> [!TIP]
> <span data-ttu-id="86fd9-177">[Azure 展開キットのディレクトリ同期サーバー](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)には、このソリューション、PowerPoint や Visio 形式で図を生成する Microsoft Excel の構成のブックを構築するための Azure PowerShell ブロックのすべてが含まれていますAzure PowerShell コマンド ブロックの設定をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="86fd9-177">The [Directory Synchronization Server in Azure Deployment Kit](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded) contains all of the Azure PowerShell blocks to build out this solution, the diagrams in Microsoft PowerPoint and Visio format, and a Microsoft Excel configuration workbook that generates Azure PowerShell command blocks customized for your settings.</span></span>
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="86fd9-178">フェーズ 1: Azure 仮想ネットワークを作成および構成する</span><span class="sxs-lookup"><span data-stu-id="86fd9-178">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="86fd9-179">Azure 仮想ネットワークを作成および構成するには、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」の展開ロードマップにある「[フェーズ 1: オンプレミス ネットワークの準備](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1)」および「[フェーズ 2: Azure でのクロスプレミスの仮想ネットワークの作成](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2)」を完了してください。</span><span class="sxs-lookup"><span data-stu-id="86fd9-179">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="86fd9-180">以下が最終的な構成です。</span><span class="sxs-lookup"><span data-stu-id="86fd9-180">This is your resulting configuration.</span></span>
  
![Azure でホストされている Office 365 のディレクトリ同期サーバーの第 1 フェーズ](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="86fd9-182">この図は、サイト間 VPN や ExpressRoute 接続を介してAzure 仮想ネットワークに接続しているオンプレミスネットワークを示しています。</span><span class="sxs-lookup"><span data-stu-id="86fd9-182">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="86fd9-183">フェーズ 2:Azure 仮想マシンを作成および構成する</span><span class="sxs-lookup"><span data-stu-id="86fd9-183">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="86fd9-p118">「[Azure ポータルで最初の Windows 仮想マシンを作成する](https://go.microsoft.com/fwlink/p/?LinkId=393098)」の説明に従い、Azure に仮想マシンを作成します。以下の設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p118">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="86fd9-p119">**[基本]** ウィンドウで、仮想ネットワークと同じサブスクリプション、場所およびリソース グループを選択します。ユーザー名とパスワードを安全な場所に記録します。後ほど、仮想マシンに接続するときに必要になります。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p119">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="86fd9-189">**[サイズの選択]** ウィンドウで、 **A2 標準** サイズを選択します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-189">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="86fd9-p120">**設定**] ウィンドウで [**ストレージ**] セクションで、**標準的な**ストレージ ・ タイプを選択します。[**ネットワーク**] セクションでは、ディレクトリ同期サーバー (GatewaySubnet ではない) をホストするため、仮想ネットワークとサブネットの名前を選択します。その他のすべての設定を既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p120">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="86fd9-193">ディレクトリ同期サーバーは正しく使用している DNS、内部の DNS を確認することによって、IP アドレスを持つ仮想マシンのアドレス (A) レコードが追加されたことを確認することを確認します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-193">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="86fd9-p121">リモート デスクトップ接続を使用してディレクトリ同期サーバーに接続するため[の記号、仮想マシンに接続](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)することで指示を使用します。サインイン後、仮想マシンを設置型の Windows サーバーの AD ドメインに参加します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p121">Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises Windows Server AD domain.</span></span>
  
<span data-ttu-id="86fd9-p122">Azure AD 接続でインターネット リソースにアクセスできるように、設置型ネットワークのプロキシ サーバーを使用するディレクトリ同期サーバーを構成する必要があります。追加の構成手順を実行するネットワーク管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p122">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="86fd9-198">以下が最終的な構成です。</span><span class="sxs-lookup"><span data-stu-id="86fd9-198">This is your resulting configuration.</span></span>
  
![Azure でホストされている Office 365 のディレクトリ同期サーバーの第 2 段階](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="86fd9-200">この図のディレクトリ同期サーバーの仮想マシン間の施設内で Azure の仮想ネットワークです。</span><span class="sxs-lookup"><span data-stu-id="86fd9-200">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="86fd9-201">フェーズ 3: Azure AD Connect をインストールして構成する</span><span class="sxs-lookup"><span data-stu-id="86fd9-201">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="86fd9-202">次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-202">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="86fd9-p123">ローカル管理者権限を持つ Windows サーバーの AD ドメインのアカウントでリモート デスクトップ接続を使用してディレクトリ同期サーバーに接続します。[サインオン、仮想マシンへの接続](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p123">Connect to the directory sync server using a Remote Desktop Connection with a Windows Server AD domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on).</span></span>
    
2. <span data-ttu-id="86fd9-205">ディレクトリ同期サーバーから[Office 365 のディレクトリ同期を設定する](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)文書を開くし、パスワード ハッシュの同期とのディレクトリ同期の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="86fd9-205">From the directory sync server, open the [Set up directory synchronization in Office 365](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="86fd9-p124">セットアップによって、ローカル ユーザー組織単位 (OU) 内に **AAD_xxxxxxxxxxxx** というアカウントが作成されます。このアカウントは移動も削除も行わないでください。移動や削除を行うと、同期が失敗します。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p124">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="86fd9-208">以下が最終的な構成です。</span><span class="sxs-lookup"><span data-stu-id="86fd9-208">This is your resulting configuration.</span></span>
  
![Azure でホストされている Office 365 のディレクトリ同期サーバーのフェーズ 3](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="86fd9-210">この図の Azure AD 接続で、ディレクトリ同期サーバーで複数の環境に関する Azure の仮想ネットワークです。</span><span class="sxs-lookup"><span data-stu-id="86fd9-210">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a><span data-ttu-id="86fd9-211">Office 365 のユーザーに場所とライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="86fd9-211">Assign locations and licenses to users in Office 365</span></span>

<span data-ttu-id="86fd9-p125">Azure AD Connect はオンプレミスの Windows Server AD から Office 365 にアカウントを追加しますが、ユーザーが Office 365 にサインインしてそのサービスを利用するには、アカウントに場所とライセンスが設定されている必要があります。次の手順で、適切なユーザーアカウントに場所を追加し、ライセンス認証を行います。</span><span class="sxs-lookup"><span data-stu-id="86fd9-p125">Azure AD Connect adds accounts to your Office 365 subscription from the on-premises Windows Server AD, but in order for users to sign in to Office 365 and use its services, the accounts must configured with a location and licenses. Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="86fd9-214">[Office 365 ポータル ページ](https://portal.office.com) にサインインして、 **[管理者]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="86fd9-214">Sign in to the [Office 365 portal page](https://portal.office.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="86fd9-215">左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="86fd9-215">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="86fd9-216">ユーザーアカウントのリストで、アクティブにするユーザー名の隣にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="86fd9-216">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="86fd9-217">ユーザーのページで、 **[製品ライセンス]** の **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="86fd9-217">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="86fd9-218">**[製品ライセンス]** ページの **[場所]** でユーザーの場所を選択し、ユーザーの適切なライセンスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="86fd9-218">On the **Product licences** page, select a location for the user for **Location**, and then enable the appropriate licences for the user.</span></span>
    
6. <span data-ttu-id="86fd9-219">完了したら、 **[保存]** をクリックし、2回 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="86fd9-219">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="86fd9-220">別のユーザーについては、手順 3 に戻ります。</span><span class="sxs-lookup"><span data-stu-id="86fd9-220">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="86fd9-221">関連項目</span><span class="sxs-lookup"><span data-stu-id="86fd9-221">See Also</span></span>

<span data-ttu-id="86fd9-222"><a name="DeploymentRoadmap"> </a></span><span class="sxs-lookup"><span data-stu-id="86fd9-222"><a name="DeploymentRoadmap"> </a></span></span>

[<span data-ttu-id="86fd9-223">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="86fd9-223">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="86fd9-224">オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する</span><span class="sxs-lookup"><span data-stu-id="86fd9-224">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="86fd9-225">Azure AD Connect をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="86fd9-225">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="86fd9-226">Office 365 のディレクトリ同期をセットアップする</span><span class="sxs-lookup"><span data-stu-id="86fd9-226">Set up directory synchronization in Office 365</span></span>](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[<span data-ttu-id="86fd9-227">Azure 展開キットのディレクトリ同期サーバー</span><span class="sxs-lookup"><span data-stu-id="86fd9-227">Directory Synchronization server in Azure Deployment Kit</span></span>](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



