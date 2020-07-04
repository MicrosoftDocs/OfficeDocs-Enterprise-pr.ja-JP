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
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a>Microsoft Azure での Microsoft 365 ディレクトリ同期の展開

Azure Active Directory (Azure AD) Connect (以前のディレクトリ同期ツール、ディレクトリ同期ツール、または DirSync.exe ツール) は、ドメインに参加しているサーバーにインストールして、オンプレミスの Active Directory ドメインサービス (AD DS) ユーザーを Microsoft 365 サブスクリプションの Azure AD テナントに同期するアプリケーションです。 Microsoft 365 では、ディレクトリサービスに Azure AD を使用しています。 Microsoft 365 サブスクリプションには、Azure AD テナントが含まれています。 このテナントは他の SaaS アプリケーションと Azure のアプリを含む、他のクラウドのワークロードで組織の ID を管理するためにも使用されます。

Azure AD Connect はオンプレミス サーバーにインストールできますが、次の理由により、Azure の仮想マシンにもインストールできます。
  
- クラウド ベースのサーバーをより迅速にプロビジョニングして構成でき、ユーザーがすぐにサービスを利用できるようになります。
- Azure では、より少ない労力でより良いサイト可用性が得られます。
- 組織内のオンプレミス サーバーの数を削減できます。

This solution requires connectivity between your on-premises network and your Azure virtual network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md). 
  
> [!NOTE]
> この記事では、1 つのフォレスト内の単一ドメインの同期について説明します。 Azure AD Connect は、Active Directory フォレスト内のすべての AD DS ドメインを Microsoft 365 と同期します。 Microsoft 365 と同期する複数の Active Directory フォレストがある場合は、「[マルチフォレストディレクトリ同期とシングルサインオンシナリオ](https://go.microsoft.com/fwlink/p/?LinkId=393091)」を参照してください。 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a>Azure での Microsoft 365 ディレクトリ同期の展開の概要

次の図は、オンプレミスの AD DS フォレストを Microsoft 365 サブスクリプションに同期する azure AD Connect を示しています。 Azure AD Connect は Azure (ディレクトリ同期サーバー) の仮想マシンで実行されています。
  
![Azure の仮想マシン上の azure AD Connect ツールトラフィックフローを含む Microsoft 365 サブスクリプションの Azure AD テナントへのオンプレミスアカウントの同期](media/CP-DirSyncOverview.png)
  
In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where AD DS domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:
  
-  Azure AD Connect は、アカウントとパスワードの変更に関してオンプレミス ネットワーク上のドメイン コントローラーにクエリを実行します。
-  Azure AD Connect は、アカウントおよびパスワードへの変更を、Microsoft 365 サブスクリプションの Azure AD インスタンスに送信します。 ディレクトリ同期サーバーはオンプレミスネットワークの拡張部分にあるため、これらの変更は、オンプレミスネットワークのプロキシサーバー経由で送信されます。
    
> [!NOTE]
> このソリューションでは、1 つの Active Directory フォレスト内の単一 Active Directory ドメインの同期について説明します。 Azure AD Connect は、Active Directory フォレスト内のすべての Active Directory ドメインを Microsoft 365 と同期します。 Microsoft 365 と同期する複数の Active Directory フォレストがある場合は、「[マルチフォレストディレクトリ同期とシングルサインオンシナリオ](https://go.microsoft.com/fwlink/p/?LinkId=393091)」を参照してください。 
  
このソリューションをデプロイする場合には、次の 2 つの主要な手順があります。
  
1. Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
    
2. Azure のドメインに参加している仮想マシンに[AZURE AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)をインストールし、オンプレミスの ad DS を Microsoft 365 と同期します。 これには以下の手順を実行します。
    
    Azure AD Connect を実行するため、Azure Virtual Machine を作成します。
    
    [Azure AD Connect ](https://www.microsoft.com/download/details.aspx?id=47594) をインストールし、設定します。
    
    Azure AD Connect を構成するには、Azure AD 管理者アカウントおよび AD DS エンタープライズ管理者アカウントの資格情報 (ユーザー名とパスワード) が必要です。 Azure AD Connect はすぐに実行され、オンプレミスの AD DS フォレストを Microsoft 365 に同期します。
    
このソリューションを運用環境に展開する前に、シミュレートされた[エンタープライズ基本構成](https://docs.microsoft.com/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise)の手順を使用して、この構成を概念実証、デモンストレーション、または実験のために設定することができます。
  
> [!IMPORTANT]
> Azure AD Connect の設定が完了しても、AD DS エンタープライズ管理者アカウントの資格情報は保存されません。 
  
> [!NOTE]
> このソリューションでは、1つの AD DS フォレストを Microsoft 365 と同期する方法について説明します。 この記事で取り上げられているトポロジは、このソリューションを実装する 1 つの方法に過ぎません。 組織のトポロジは、固有のネットワーク要件とセキュリティに関する考慮事項によって異なる可能性があります。 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a>Azure で Microsoft 365 用のディレクトリ同期サーバーをホストするための計画
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>前提条件

開始する前に、このソリューションの以下の前提条件を確認してください。
  
- 「[Azure 仮想ネットワークの計画](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network)」に記されている関連する計画内容を確認します。
    
- Azure Virtual Network を構成するためのすべての「[前提条件](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites)」を満たしていることを確かめます。
    
- Active Directory 統合機能を含む Microsoft 365 サブスクリプションを所有していること。 Microsoft 365 サブスクリプションの詳細については、 [microsoft 365 サブスクリプションページ](https://products.office.com/compare-all-microsoft-office-products?tab=2)にアクセスしてください。
    
- Azure AD Connect を実行する1つの Azure 仮想マシンをプロビジョニングして、オンプレミスの AD DS フォレストを Microsoft 365 と同期させます。
    
    AD DS エンタープライズ管理者アカウントと Azure AD 管理者アカウントの資格情報 (名前とパスワード) が必要です。
    
### <a name="solution-architecture-design-assumptions"></a>ソリューション アーキテクチャ設計の前提条件

次の一覧では、このソリューションで採用された設計方針について説明します。
  
- This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that has one server, the directory sync server that is running Azure AD Connect. 
    
- オンプレミス ネットワークには、ドメイン コントローラーと DNS サーバーが存在します。
    
- Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](https://aka.ms/auth-options).
    
There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:
  
- 既存の Azure Virtual Network 内に既存の DNS サーバーがある場合、オンプレミス ネットワークの DNS サーバーではなく、それらをディレクトリ同期サーバーで使用して名前解決を行うかどうかを決定します。
    
- If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.
    
## <a name="deployment-roadmap"></a>展開のロードマップ

Azure の仮想マシンへの Azure AD Connect の展開には、3つのフェーズがあります。
  
- フェーズ 1:Azure 仮想ネットワークを作成および構成する
    
- フェーズ 2:Azure 仮想マシンを作成および構成する
    
- フェーズ 3: Azure AD Connect をインストールして構成する
    
展開後に、Microsoft 365 で新しいユーザーアカウントの場所とライセンスを割り当てる必要もあります。


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>フェーズ 1: Azure Virtual Network を作成および構成する

Azure 仮想ネットワークを作成および構成するには、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」の展開ロードマップにある「[フェーズ 1: オンプレミス ネットワークの準備](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network)」および「[フェーズ 2: Azure でのクロスプレミスの仮想ネットワークの作成](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure)」を完了してください。
  
以下が最終的な構成です。
  
![Azure でホストされている Microsoft 365 のディレクトリ同期サーバーのフェーズ1](media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
この図は、サイト間 VPN や ExpressRoute 接続を介してAzure 仮想ネットワークに接続しているオンプレミスネットワークを示しています。
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>フェーズ 2:Azure 仮想マシンを作成および構成する

Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:
  
- On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.
    
- **[サイズの選択]** ウィンドウで、 **A2 標準** サイズを選択します。
    
- On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.
    
内部 DNS をチェックして、ディレクトリ同期サーバーが DNS を正しく使用していることを検証し、仮想マシンに IP アドレスのアドレス (A) レコードが追加されたことを確認します。 
  
Use the instructions in [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises AD DS domain.
  
For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.
  
以下が最終的な構成です。
  
![Azure でホストされている Microsoft 365 のディレクトリ同期サーバーのフェーズ2](media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
この図に、クロスプレミス Azure 仮想ネットワーク内のディレクトリ同期サーバーとしての仮想マシンを示します。
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>フェーズ 3: Azure AD Connect をインストールして構成する

次の手順を実行します。
  
1. Connect to the directory sync server using a Remote Desktop Connection with an AD DS domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon).
    
2. ディレクトリ同期を使用して、「 [Microsoft 365 用のディレクトリ同期をセットアップ](set-up-directory-synchronization.md)する」という記事を開き、「パスワードのハッシュ同期を使用したディレクトリ同期」の指示に従います。
    
> [!CAUTION]
> Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.
  
以下が最終的な構成です。
  
![Azure でホストされている Microsoft 365 のディレクトリ同期サーバーのフェーズ3](media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
この図に、クロスプレミス Azure 仮想ネットワーク内の Azure AD Connect を使ったディレクトリ同期サーバーを示します。
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a>Microsoft 365 でユーザーに場所とライセンスを割り当てる

Azure AD Connect は、オンプレミス AD DS から Microsoft 365 サブスクリプションにアカウントを追加しますが、ユーザーが Microsoft 365 にサインインしてそのサービスを使用するには、アカウントを場所とライセンスで構成する必要があります。 次の手順で、適切なユーザーアカウントに場所を追加し、ライセンス認証を行います。
  
1. [Microsoft 365 管理センター](https://admin.microsoft.com)にサインインし、[**管理者**] をクリックします。
    
2. 左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。
    
3. ユーザーアカウントのリストで、アクティブにするユーザー名の隣にあるチェック ボックスをオンにします。
    
4. ユーザーのページで、**[製品ライセンス]** の **[編集]** をクリックします。
    
5. **[製品ライセンス]** ページの **[場所]** でユーザーの場所を選択し、ユーザーの適切なライセンスを有効にします。
    
6. 完了したら、**[保存]** をクリックし、2 回 **[閉じる]** をクリックします。
    
7. 別のユーザーについては、手順 3 に戻ります。
    
## <a name="see-also"></a>関連項目

[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.yml)
  
[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[Azure AD Connect をダウンロードする](https://www.microsoft.com/download/details.aspx?id=47594)
  
[Microsoft 365 のディレクトリ同期をセットアップする](set-up-directory-synchronization.md)
  
