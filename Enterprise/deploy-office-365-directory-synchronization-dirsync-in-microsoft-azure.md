---
title: "Microsoft Azure での Office 365 ディレクトリ同期 (DirSync) の展開"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 9/7/2017
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
---

# Microsoft Azure での Office 365 ディレクトリ同期 (DirSync) の展開

 **概要:** Azure の仮想マシン上に Azure AD Connect (DirSync) を展開し、オンプレミス ディレクトリと Office 365 サブスクリプションの Azure AD テナントとの間でアカウントを同期します。
  
Azure Active Directory (AD) Connect (以前のディレクトリ同期ツール、Directory 同期ツール、DirSync.exe ツール) は、ドメインに参加しているサーバー上にインストールするサーバーベースのアプリケーションで、オンプレミスの Windows Server Active Directory ユーザーを Office 365 サブスクリプションの Azure Active Directory テナントと同期するために使用します。Azure AD Connect はオンプレミスのサーバーにインストールできますが、次の理由により、Azure の仮想マシンにもインストールできます。
  
- クラウド ベースのサーバーをより迅速に準備して構成でき、ユーザーがすぐにサービスを利用できるようになります。
    
- Azure では、より少ない労力でより良いサイト可用性が得られます。
    
- 組織内のオンプレミス サーバーの数を削減できます。
    
この記事では、以下の点が取り上げられています。
  
- [Azure における Office 365 ディレクトリ同期の展開に関する概要](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md#Overview)
    
- [Azure の Office 365 向けに DirSync サーバーをホストするための計画](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md#PlanningVirtual)
    
- [展開のロードマップ](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md#DeploymentRoadmap)
    
> [!IMPORTANT]
> このソリューションには、オンプレミス ネットワークと Azure Virtual Network 間の接続が必要です。詳しくは、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](81190961-5454-4a5c-8b0e-6ae75b9fb035.md)」をご覧ください。 
  
> [!IMPORTANT]
> この記事では、1 つのフォレスト内の単一ドメインの同期について説明します。Azure AD Connect は、Active Directory フォレスト内のすべての Windows Server AD ドメインを Office 365 と同期します。複数の Active Directory フォレストを Office 365 と同期する場合には、「[シングル サインオン シナリオでの Multi-forest ディレクトリ同期](https://go.microsoft.com/fwlink/p/?LinkId=393091)」をご覧ください。 
  
> [!NOTE]
> Office 365 はディレクトリ サービスに Azure Active Directory (Azure AD) を使用します。Office 365 サブスクリプションには Azure AD テナントが含まれます。このテナントは他の SaaS アプリケーションと Azure のアプリを含む、他のクラウドのワークロードで組織の ID を管理するためにも使用されます。 
  
## Azure における Office 365 ディレクトリ同期の展開に関する概要
<a name="Overview"> </a>

次の図は、オンプレミスの Windows Server AD フォレストを Office 365 サブスクリプションに同期する Azure AD Connect を示したものです。Azure AD Connect は Azure (DirSync サーバー) の仮想マシンで実行されています。
  
![Azure 内の仮想マシン上の Azure AD 接続ツールが、トラフィック フローを伴う Office 365 サブスクリプションの Azure AD テナントに、オンプレミス アカウントを同期しています](images/CP_DirSyncOverview.png)
  
この図には、サイト間 VPN または ExpressRoute 接続で接続されている 2 つのネットワークがあります。Windows Server AD ドメイン コントローラーがあるオンプレミス ネットワークと、[Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) を実行している仮想マシンであるディレクトリ同期サーバーが含まれる Azure 仮想ネットワークです。ディレクトリ同期サーバーを発信元とする 2 つの主要なトラフィック フローがあります。
  
- Azure AD Connect は、アカウントとパスワードの変更に関してオンプレミス ネットワーク上のドメイン コントローラーにクエリを実行します。
    
- Azure AD Connect は、アカウントとパスワードの変更を Office 365 サブスクリプションの Azure ADインスタンスに送信します。ディレクトリ同期サーバーはオンプレミス ネットワークの拡張部分であるため、これらの変更はオンプレミス ネットワークのプロキシ サーバーを経由して送信されます。
    
> [!NOTE]
> このソリューションでは、1 つの Active Directory フォレスト内の単一 Active Directory ドメインの同期について説明します。Azure AD Connect は、Active Directory フォレスト内のすべての Active Directory ドメインを Office 365 と同期します。複数の Active Directory フォレストを Office 365 と同期する場合には、「[シングル サインオン シナリオでの Multi-forest ディレクトリ同期](https://go.microsoft.com/fwlink/p/?LinkId=393091)」をご覧ください。 
  
どちらの場合であっても、Azure 仮想マシンで実行されている Azure AD Connect から発信されるトラフィックは Azure の仮想ネットワーク上のゲートウェイに送られ、その後、サイト間 VPN または ExpressRoute 接続を介してオンプレミス ネットワークの VPN gateway デバイスに送られます。オンプレミス ネットワークのルーティング インフラストラクチャにより、次に、ドメイン コントローラーやプロキシ サーバーなどの宛先にトラフィックが転送されます。
  
このソリューションを展開する場合には、次の 2 つの主要な手順があります。
  
1. Azure Virtual Network を作成し、オンプレミスネットワークに対するサイト間 VPN 接続を確立します。詳しくは、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](81190961-5454-4a5c-8b0e-6ae75b9fb035.md)」をご覧ください。
    
2. [Azure AD Connect ](https://www.microsoft.com/download/details.aspx?id=47594) を Azure のドメインに参加している仮想マシン上にインストールし、オンプレミス Windows Server AD を Office 365 に同期します。これには以下の手順を実行します。
    
1. Azure AD Connect を実行するため、Azure Virtual Machine を作成します。
    
2. [Azure AD Connect ](https://www.microsoft.com/download/details.aspx?id=47594) をインストールし、設定します。
    
    Azure AD Connect の設定には、Azure AD 管理者アカウントの資格情報 (ユーザー名とパスワード) と、Windows Server AD エンタープライズ管理者アカウントが必要です。Azure AD Connect ツールはすぐに実行され、オンプレミスの Windows Server AD フォレストを Office 365 に継続的に同期します。
    
運用でこのソリューションを展開する前に、「[Office 365 開発/テスト環境の DirSync](dirsync-for-your-office-365-dev-test-environment.md)」の手順を使用して、概念実証、デモンストレーション、実験用にこの構成を設定します。
  
> [!IMPORTANT]
> Azure AD Connect の設定が完了しても、Windows Server AD エンタープライズ管理者アカウントの資格情報は保存されません。 
  
> [!NOTE]
> このソリューションは、1 つの Windows Server AD フォレストを Office 365 と同期する方法について説明しています。この記事で取り上げられているトポロジは、このソリューションを実装する 1 つの方法に過ぎません。組織のトポロジは、固有のネットワーク要件とセキュリティに関する考慮事項によって異なる可能性があります。 
  
## Azure の Office 365 向けに DirSync サーバーをホストするための計画
<a name="PlanningVirtual"> </a>

### 前提条件

開始する前に、このソリューションの以下の前提条件を確認してください。
  
- 「[Azure 仮想ネットワークの計画](81190961-5454-4a5c-8b0e-6ae75b9fb035.md#PlanningVirtual)」に記されている関連する計画内容を確認します。
    
- Azure Virtual Network を構成するためのすべての「[前提条件](http://technet.microsoft.com/library/81190961-5454-4a5c-8b0e-6ae75b9fb035%28v=office.15%29.aspx#Prerequisites)」を満たしていることを確かめます。
    
- Active Directory 統合機能が含まれている Office 365 サブスクリプションがあることを確認します。Office 365 サブスクリプションについて詳しくは、「[Office 365 サブスクリプションのページ](https://go.microsoft.com/fwlink/p/?LinkId=394278)」をご覧ください。
    
- Azure AD Connect を実行する 1 つの Azure Virtual Machine を準備し、オンプレミスの Windows Server AD フォレストを Office 365 と同期します。
    
    Windows Server AD エンタープライズ管理者アカウントと Azure Active Directory 管理者アカウントの資格情報 (名前とパスワード) が必要です。
    
### ソリューション アーキテクチャ設計の前提条件

次の一覧では、このソリューションで採用された設計方針について説明します。
  
- このソリューションでは、サイト間 VPN 接続を伴う 1 つの Azure Virtual Network を使用します。Azure Virtual Network は 1 つのサブネットをホストし、このサブネットには Azure AD Connect を実行する 1 つのディレクトリ同期サーバーが含まれます。
    
- オンプレミス ネットワークには、ドメイン コントローラーと DNS サーバーが存在します。
    
- Azure AD Connect は、シングル サインオンではなくパスワード同期を実行します (Active Directory フェデレーション サービス (AD FS) インフラストラクチャを展開する必要はありません)。パスワード同期とシングル サインオンのオプションについて詳しくは、「[使用するディレクトリ統合シナリオを確認する](https://go.microsoft.com/fwlink/p/?LinkId=393094)」をご覧ください。
    
ご使用の環境でこのソリューションを展開する場合に考慮できるその他の設計に関する選択内容があります。それらには以下が含まれます。
  
- 既存の Azure Virtual Network 内に既存の DNS サーバーがある場合、オンプレミス ネットワークの DNS サーバーではなく、それらをディレクトリ同期サーバーで使用して名前解決を行うかどうかを決定します。
    
- 既存の Azure Virtual Network にドメイン コントローラーがある場合、Active Directory サイトとサービスを構成するのが優れた選択肢となるかどうかを判別します。DirSync サーバーは、オンプレミス ネットワークのドメイン コントローラーではなく Azure Virtual Network 内のドメイン コントローラーをクエリして、アカウントとパスワードの変更内容を調べます。
    
## 展開のロードマップ
<a name="DeploymentRoadmap"> </a>

Azure の仮想マシンへの Azure AD Connect の展開には、3つのフェーズがあります。
  
- フェーズ 1:Azure 仮想ネットワークを作成および構成する
    
- フェーズ 2:Azure 仮想マシンを作成および構成する
    
- フェーズ 3: Azure AD Connect をインストールして構成する
    
構成後、Office 365 の新しいユーザーアカウントに場所とライセンスを割り当てる必要があります。
  
> [!TIP]
> 「[Azure デプロイメント キットの DirSync サーバー](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)」には、このソリューションをビルドするためのすべての Azure PowerShell ブロック、Microsoft PowerPoint と Visio 形式のダイヤグラム、ユーザー設定用にカスタマイズされた Azure PowerShell コマンド ブロックを生成する Microsoft Excel 構成ワークブックが含まれています。 
  
### フェーズ 1:Azure 仮想ネットワークを作成および構成する

Azure 仮想ネットワークを作成および構成するには、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](81190961-5454-4a5c-8b0e-6ae75b9fb035.md)」の展開のロードマップにある「[フェーズ 1: オンプレミス ネットワークの準備](http://technet.microsoft.com/library/81190961-5454-4a5c-8b0e-6ae75b9fb035%28v=office.15%29.aspx#Phase1)」および「[フェーズ 2: Azure でのクロスプレミスの仮想ネットワークの作成](http://technet.microsoft.com/library/81190961-5454-4a5c-8b0e-6ae75b9fb035%28v=office.15%29.aspx#Phase2)」を完了してください。
  
以下が最終的な構成です。
  
![Azure でホストされている Office 365 のディレクトリ同期サーバーのフェーズ 1](images/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
この図は、サイト間 VPN や ExpressRoute 接続を介してAzure 仮想ネットワークに接続しているオンプレミスネットワークを示しています。
  
### フェーズ 2:Azure 仮想マシンを作成および構成する

「[Azure ポータルで最初の Windows 仮想マシンを作成する](https://go.microsoft.com/fwlink/p/?LinkId=393098)」の説明に従い、Azure に仮想マシンを作成します。以下の設定を使用します。
  
- **[基本]** ウィンドウで、仮想ネットワークと同じサブスクリプション、場所およびリソース グループを選択します。ユーザー名とパスワードを安全な場所に記録します。後ほど、仮想マシンに接続するときに必要になります。
    
- **[サイズの選択]** ウィンドウで、 **A2 標準** サイズを選択します。
    
- **[設定]** ウィンドウの **[ストレージ]** セクションで、 **[標準]** ストレージ タイプを選択します。 **[ネットワーク]** セクションで、(ゲートウェイ サブネットではなく) ディレクトリ同期サーバーをホストするための仮想ネットワークの名前とサブネットを選択します。他のすべての設定は、既定値のままにします。
    
内部 DNS をチェックして、ディレクトリ同期サーバーが DNS を正しく使用していることを検証し、仮想マシンに IP アドレスのアドレス (A) レコードが追加されたことを確認します。
  
「[仮想マシンへの接続とサインオン](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)」の説明を参照してリモートデスクトップ接続で DirSync サーバーに接続します。サインイン後、仮想マシンをオンプレミス Windows Server AD ドメインに参加させます。
  
Azure AD Connect がインターネット リソースにアクセスするには、オンプレミス ネットワークのプロキシ サーバーを使用するようディレクトリ同期サーバーを構成する必要があります。実行する追加の構成手順は、ネットワーク管理者に問い合わせてください。
  
以下が最終的な構成です。
  
![Azure でホストされている Office 365 のディレクトリ同期サーバーのフェーズ 2](images/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
この図に、クロスプレミス Azure 仮想ネットワークにある DirSync サーバーの仮想マシンを示します。
  
### フェーズ 3: Azure AD Connect をインストールして構成する

次の手順を実行します。
  
1. ローカル管理者権限を持つ Windows Server AD ドメイン アカウントを使用して、リモート デスクトップ接続でディレクトリ同期サーバーに接続します。「[仮想マシンへの接続とサインオン](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-hero-tutorial?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#connect-to-the-virtual-machine-and-sign-on)」を参照してください。
    
2. パスワード同期を使用したディレクトリ同期を行うには、ディレクトリ同期サーバーから「[Office 365 でディレクトリの同期をセットアップする](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)」という記事を開き、指示に従います。
    
> [!CAUTION]
> セットアップによって、ローカル ユーザー組織単位 (OU) 内に **AAD_xxxxxxxxxxxx** というアカウントが作成されます。このアカウントは移動も削除も行わないでください。移動や削除を行うと、同期が失敗します。
  
以下が最終的な構成です。
  
![Azure でホストされている Office 365 のディレクトリ同期サーバーのフェーズ 3](images/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
この図に、クロスプレミス Azure 仮想ネットワークにある Azure AD Connect を使った DirSync サーバーを示します。
  
### Office 365 のユーザーに場所とライセンスを割り当てます。

Azure AD Connect はオンプレミスの Windows Server AD から Office 365 にアカウントを追加しますが、ユーザーが Office 365 にサインインしてそのサービスを利用するには、アカウントに場所とライセンスが設定されている必要があります。次の手順で、適切なユーザーアカウントに場所を追加し、ライセンス認証を行います。
  
1. [Office 365 ポータル ページ](https://portal.office.com) にサインインして、 **[管理者]** をクリックします。
    
2. 左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。
    
3. ユーザーアカウントのリストで、アクティブにするユーザー名の隣にあるチェック ボックスをオンにします。
    
4. ユーザーのページで、 **[製品ライセンス]** の **[編集]** をクリックします。
    
5. **[製品ライセンス]** ページの **[場所]** でユーザーの場所を選択し、ユーザーの適切なライセンスを有効にします。
    
6. 完了したら、 **[保存]** をクリックし、2回 **[閉じる]** をクリックします。
    
7. 別のユーザーについては、手順 3 に戻ります。
    
## See Also
<a name="DeploymentRoadmap"> </a>

#### 

[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)
  
[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](81190961-5454-4a5c-8b0e-6ae75b9fb035.md)
#### 

[Azure AD Connect をダウンロードする](https://www.microsoft.com/download/details.aspx?id=47594)
  
[Office 365 のディレクトリ同期をセットアップする](https://support.office.com/article/Set-up-directory-synchronization-in-Office-365-1b3b5318-6977-42ed-b5c7-96fa74b08846)
  
[Azure デプロイメント キットの DirSync サーバー](https://gallery.technet.microsoft.com/DirSync-Server-in-Azure-32cb2ded)

