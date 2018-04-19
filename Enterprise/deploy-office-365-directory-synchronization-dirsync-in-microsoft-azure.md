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
ms.openlocfilehash: 31a72d027acd274c9908a7e63e83843bce9cec71
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="deploy-office-365-directory-synchronization-in-microsoft-azure"></a>Microsoft Azure で Office 365 のディレクトリ同期を展開します。

 **の概要:**Azure の AD 接続、設置ディレクトリと、Office 365 サブスクリプションの Azure AD テナントとの間のアカウントを同期するのには Azure の仮想マシン上に配置します。
  
Azure Active Directory (AD) Connect (以前のディレクトリ同期ツール、Directory 同期ツール、DirSync.exe ツール) は、ドメインに参加しているサーバー上にインストールするサーバーベースのアプリケーションで、オンプレミスの Windows Server Active Directory ユーザーを Office 365 サブスクリプションの Azure Active Directory テナントと同期するために使用します。Azure AD Connect はオンプレミスのサーバーにインストールできますが、次の理由により、Azure の仮想マシンにもインストールできます。
  
- クラウド ベースのサーバーをより迅速に準備して構成でき、ユーザーがすぐにサービスを利用できるようになります。
    
- Azure では、より少ない労力でより良いサイト可用性が得られます。
    
- 組織内のオンプレミス サーバーの数を削減できます。
    
> [!IMPORTANT]
> このソリューションには、オンプレミス ネットワークと Azure Virtual Network 間の接続が必要です。詳しくは、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」をご覧ください。 
  
> [!IMPORTANT]
> この記事では、1 つのフォレスト内の単一ドメインの同期について説明します。Azure AD Connect は、Active Directory フォレスト内のすべての Windows Server AD ドメインを Office 365 と同期します。複数の Active Directory フォレストを Office 365 と同期する場合には、「[シングル サインオン シナリオでの Multi-forest ディレクトリ同期](https://go.microsoft.com/fwlink/p/?LinkId=393091)」をご覧ください。 
  
> [!NOTE]
> Office 365 はディレクトリ サービスに Azure Active Directory (Azure AD) を使用します。Office 365 サブスクリプションには Azure AD テナントが含まれます。このテナントは他の SaaS アプリケーションと Azure のアプリを含む、他のクラウドのワークロードで組織の ID を管理するためにも使用されます。 
  
## <a name="overview-of-deploying-office-365-directory-synchronization-in-azure"></a>Azure における Office 365 ディレクトリ同期の展開に関する概要
<a name="Overview"> </a>

AnOffice 365 サブスクリプションへの設置型 Windows サーバーの AD フォレストを同期する (ディレクトリ同期サーバー) の Azure の仮想マシンで実行されている Azure の AD 接続を次の図に示します。
  
![Azure 内の仮想マシン上の Azure AD 接続ツールが、トラフィック フローを伴う Office 365 サブスクリプションの Azure AD テナントに、オンプレミス アカウントを同期しています](images/CP_DirSyncOverview.png)
  
ダイアグラムでは、サイト間の VPN または ExpressRoute の接続で接続された 2 つのネットワークがあります。設置ネットワーク、Windows サーバーの AD ドメイン コント ローラーの位置と、ディレクトリ同期サーバー、仮想マシンと Azure の仮想ネットワークがある[Azure AD 接続](https://www.microsoft.com/download/details.aspx?id=47594)を実行します。ディレクトリ同期サーバーから送信された 2 つのメインのトラフィック フローがあります。
  
-  Azure AD Connect は、アカウントとパスワードの変更に関してオンプレミス ネットワーク上のドメイン コントローラーにクエリを実行します。
    
-  Azure AD 接続では、アカウントおよびパスワードには、Office 365 サブスクリプションの Azure AD インスタンスに変更を送信します。ディレクトリ同期サーバーは、オンプレミスのネットワークの拡張部分であるために、設置型ネットワークのプロキシ サーバーをこれらの変更が送信されます。
    
> [!NOTE]
> このソリューションでは、1 つの Active Directory フォレスト内の単一 Active Directory ドメインの同期について説明します。Azure AD Connect は、Active Directory フォレスト内のすべての Active Directory ドメインを Office 365 と同期します。複数の Active Directory フォレストを Office 365 と同期する場合には、「[シングル サインオン シナリオでの Multi-forest ディレクトリ同期](https://go.microsoft.com/fwlink/p/?LinkId=393091)」をご覧ください。 
  
どちらの場合であっても、Azure 仮想マシンで実行されている Azure AD Connect から発信されるトラフィックは Azure の仮想ネットワーク上のゲートウェイに送られ、その後、サイト間 VPN または ExpressRoute 接続を介してオンプレミス ネットワークの VPN gateway デバイスに送られます。オンプレミス ネットワークのルーティング インフラストラクチャにより、次に、ドメイン コントローラーやプロキシ サーバーなどの宛先にトラフィックが転送されます。
  
このソリューションを展開する場合には、次の 2 つの主要な手順があります。
  
1. Azure Virtual Network を作成し、オンプレミスネットワークに対するサイト間 VPN 接続を確立します。詳しくは、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」をご覧ください。
    
2. [Azure AD Connect ](https://www.microsoft.com/download/details.aspx?id=47594) を Azure のドメインに参加している仮想マシン上にインストールし、オンプレミス Windows Server AD を Office 365 に同期します。これには以下の手順を実行します。
    
    Azure AD Connect を実行するため、Azure Virtual Machine を作成します。
    
    [Azure AD Connect ](https://www.microsoft.com/download/details.aspx?id=47594) をインストールし、設定します。
    
    Azure AD Connect の設定には、Azure AD 管理者アカウントの資格情報 (ユーザー名とパスワード) と、Windows Server AD エンタープライズ管理者アカウントが必要です。Azure AD Connect ツールはすぐに実行され、オンプレミスの Windows Server AD フォレストを Office 365 に継続的に同期します。
    
実稼働環境でこのソリューションを展開する前に、デモ、または実験のための概念実証としてこの構成をセットアップするのには[、Office 365 の開発/テスト環境のディレクトリ同期処理](dirsync-for-your-office-365-dev-test-environment.md)の指示を使用します。
  
> [!IMPORTANT]
> Azure AD Connect の設定が完了しても、Windows Server AD エンタープライズ管理者アカウントの資格情報は保存されません。 
  
> [!NOTE]
> このソリューションは、1 つの Windows Server AD フォレストを Office 365 と同期する方法について説明しています。この記事で取り上げられているトポロジは、このソリューションを実装する 1 つの方法に過ぎません。組織のトポロジは、固有のネットワーク要件とセキュリティに関する考慮事項によって異なる可能性があります。 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-office-365-in-azure"></a>Azure 内の Office 365 のディレクトリ同期サーバーをホストするための計画
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>前提条件

開始する前に、このソリューションの以下の前提条件を確認してください。
  
- 「[Azure 仮想ネットワークの計画](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual)」に記されている関連する計画内容を確認します。
    
- Azure Virtual Network を構成するためのすべての「[前提条件](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Prerequisites)」を満たしていることを確かめます。
    
- Active Directory 統合機能が含まれている Office 365 サブスクリプションがあることを確認します。Office 365 サブスクリプションについて詳しくは、「[Office 365 サブスクリプションのページ](https://go.microsoft.com/fwlink/p/?LinkId=394278)」をご覧ください。
    
- Azure AD Connect を実行する 1 つの Azure Virtual Machine を準備し、オンプレミスの Windows Server AD フォレストを Office 365 と同期します。
    
    Windows Server AD エンタープライズ管理者アカウントと Azure Active Directory 管理者アカウントの資格情報 (名前とパスワード) が必要です。
    
### <a name="solution-architecture-design-assumptions"></a>ソリューション アーキテクチャ設計の前提条件

次の一覧では、このソリューションで採用された設計方針について説明します。
  
- このソリューションでは、サイト間 VPN 接続で 1 つの Azure 仮想ネットワークを使用します。Azure の仮想ネットワークは、1 つのサーバーを含むサブネットが 1 つ、Azure AD 接続を実行してディレクトリ同期サーバーをホストします。 
    
- オンプレミス ネットワークには、ドメイン コントローラーと DNS サーバーが存在します。
    
- Azure AD 接続では、シングル サインオンではなくパスワード ハッシュの同期を実行します。Active Directory フェデレーション サービス (AD FS) インフラストラクチャを導入する必要はありません。パスワード ハッシュの同期とシングル サインオンのオプションに関する詳細については、 [Azure Active Directory ハイブリッドの id ソリューションの適切な認証方法を選択する](http://aka.ms/auth-options)を参照してください。
    
ご使用の環境でこのソリューションを展開する場合に考慮できるその他の設計に関する選択内容があります。それらには以下が含まれます。
  
- Azure の既存の仮想ネットワーク内の DNS サーバーが既に存在する場合は、オンプレミスのネットワーク上の DNS サーバーではなく、名前解決に使用するディレクトリ同期サーバーにするかどうかを決定します。
    
- Azure の既存の仮想ネットワーク内のドメイン コント ローラーがある場合は、Active Directory サイトとサービスを構成するとするのに適して可能性があるかどうかを決定します。ディレクトリ同期サーバーは、アカウントと、オンプレミスのネットワーク上のドメイン コント ローラーではなくパスワードの変更の Azure の仮想ネットワークのドメイン コント ローラーを照会できます。
    
## <a name="deployment-roadmap"></a>展開のロードマップ
<a name="DeploymentRoadmap"> </a>

Azure の仮想マシンへの Azure AD Connect の展開には、3つのフェーズがあります。
  
- フェーズ 1:Azure 仮想ネットワークを作成および構成する
    
- フェーズ 2:Azure 仮想マシンを作成および構成する
    
- フェーズ 3: Azure AD Connect をインストールして構成する
    
構成後、Office 365 の新しいユーザーアカウントに場所とライセンスを割り当てる必要があります。
  
> [!TIP]
> [Azure 展開キットのディレクトリ同期サーバー](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)には、このソリューション、PowerPoint や Visio 形式で図を生成する Microsoft Excel の構成のブックを構築するための Azure PowerShell ブロックのすべてが含まれていますAzure PowerShell コマンド ブロックの設定をカスタマイズします。
  
### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>フェーズ 1: Azure 仮想ネットワークを作成および構成する

Azure 仮想ネットワークを作成および構成するには、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」の展開ロードマップにある「[フェーズ 1: オンプレミス ネットワークの準備](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase1)」および「[フェーズ 2: Azure でのクロスプレミスの仮想ネットワークの作成](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Phase2)」を完了してください。
  
以下が最終的な構成です。
  
![Azure でホストされている Office 365 のディレクトリ同期サーバーの第 1 フェーズ](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
この図は、サイト間 VPN や ExpressRoute 接続を介してAzure 仮想ネットワークに接続しているオンプレミスネットワークを示しています。
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>フェーズ 2:Azure 仮想マシンを作成および構成する

「[Azure ポータルで最初の Windows 仮想マシンを作成する](https://go.microsoft.com/fwlink/p/?LinkId=393098)」の説明に従い、Azure に仮想マシンを作成します。以下の設定を使用します。
  
- **[基本]** ウィンドウで、仮想ネットワークと同じサブスクリプション、場所およびリソース グループを選択します。ユーザー名とパスワードを安全な場所に記録します。後ほど、仮想マシンに接続するときに必要になります。
    
- **[サイズの選択]** ウィンドウで、 **A2 標準** サイズを選択します。
    
- **設定**] ウィンドウで [**ストレージ**] セクションで、**標準的な**ストレージ ・ タイプを選択します。[**ネットワーク**] セクションでは、ディレクトリ同期サーバー (GatewaySubnet ではない) をホストするため、仮想ネットワークとサブネットの名前を選択します。その他のすべての設定を既定値のままにします。
    
ディレクトリ同期サーバーは正しく使用している DNS、内部の DNS を確認することによって、IP アドレスを持つ仮想マシンのアドレス (A) レコードが追加されたことを確認することを確認します。 
  
リモート デスクトップ接続を使用してディレクトリ同期サーバーに接続するため[の記号、仮想マシンに接続](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)することで指示を使用します。サインイン後、仮想マシンを設置型の Windows サーバーの AD ドメインに参加します。
  
Azure AD 接続でインターネット リソースにアクセスできるように、設置型ネットワークのプロキシ サーバーを使用するディレクトリ同期サーバーを構成する必要があります。追加の構成手順を実行するネットワーク管理者に問い合わせてください。
  
以下が最終的な構成です。
  
![Azure でホストされている Office 365 のディレクトリ同期サーバーの第 2 段階](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
この図のディレクトリ同期サーバーの仮想マシン間の施設内で Azure の仮想ネットワークです。
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>フェーズ 3: Azure AD Connect をインストールして構成する

次の手順を実行します。
  
1. ローカル管理者権限を持つ Windows サーバーの AD ドメインのアカウントでリモート デスクトップ接続を使用してディレクトリ同期サーバーに接続します。[サインオン、仮想マシンへの接続](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)を参照してください。
    
2. ディレクトリ同期サーバーから[Office 365 のディレクトリ同期を設定する](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)文書を開くし、パスワード ハッシュの同期とのディレクトリ同期の指示に従います。
    
> [!CAUTION]
> セットアップによって、ローカル ユーザー組織単位 (OU) 内に **AAD_xxxxxxxxxxxx** というアカウントが作成されます。このアカウントは移動も削除も行わないでください。移動や削除を行うと、同期が失敗します。
  
以下が最終的な構成です。
  
![Azure でホストされている Office 365 のディレクトリ同期サーバーのフェーズ 3](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
この図の Azure AD 接続で、ディレクトリ同期サーバーで複数の環境に関する Azure の仮想ネットワークです。
  
### <a name="assign-locations-and-licenses-to-users-in-office-365"></a>Office 365 のユーザーに場所とライセンスを割り当てます。

Azure AD Connect はオンプレミスの Windows Server AD から Office 365 にアカウントを追加しますが、ユーザーが Office 365 にサインインしてそのサービスを利用するには、アカウントに場所とライセンスが設定されている必要があります。次の手順で、適切なユーザーアカウントに場所を追加し、ライセンス認証を行います。
  
1. [Office 365 ポータル ページ](https://portal.office.com) にサインインして、 **[管理者]** をクリックします。
    
2. 左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。
    
3. ユーザーアカウントのリストで、アクティブにするユーザー名の隣にあるチェック ボックスをオンにします。
    
4. ユーザーのページで、 **[製品ライセンス]** の **[編集]** をクリックします。
    
5. **[製品ライセンス]** ページの **[場所]** でユーザーの場所を選択し、ユーザーの適切なライセンスを有効にします。
    
6. 完了したら、 **[保存]** をクリックし、2回 **[閉じる]** をクリックします。
    
7. 別のユーザーについては、手順 3 に戻ります。
    
## <a name="see-also"></a>関連項目

<a name="DeploymentRoadmap"> </a>

[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)
  
[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[Azure AD Connect をダウンロードする](https://www.microsoft.com/download/details.aspx?id=47594)
  
[Office 365 のディレクトリ同期をセットアップする](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[Azure 展開キットのディレクトリ同期サーバー](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)



