---
title: "オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 81190961-5454-4a5c-8b0e-6ae75b9fb035
description: "概要: Office サーバーのワークロードのためにクロスプレミスの Azure 仮想ネットワークを構成する方法について説明します。"
ms.openlocfilehash: 83e5842a4b3192ee2f65048cefe57790cd1e2341
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="connect-an-on-premises-network-to-a-microsoft-azure-virtual-network"></a>オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する

 **概要:** Office サーバーのワークロードのためにクロスプレミスの Azure 仮想ネットワークを構成する方法について説明します。
  
クロスプレミス Azure 仮想ネットワークをオンプレミスネットワークに接続することで、Azure インフラサービスにホストされているサブネットや仮想マシンを追加してネットワークを拡張します。この接続により、オンプレミスのネットワークにあるマシンと Azure の仮想マシンが相互に直接アクセスできるようになります。たとえば、Azure 仮想マシンで実行中のディレクトリ同期サーバーは、アカウントへの変更に関してオンプレミスのドメイン コントローラーのクエリを実行し、Office 365 のサブスクリプションにその変更を同期する必要があります。この資料では、Azure 仮想マシンをホストできるようにクロスプレミス Azure 仮想ネットワークを設定する方法を示します。
  
この記事では、以下の点が取り上げられています。
  
- [概要](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#Overview)
    
- [Azure 仮想ネットワークの計画](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#PlanningVirtual)
    
- [展開のロードマップ](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#DeploymentRoadmap)
    
## <a name="overview"></a>概要
<a name="Overview"> </a>

Azure の仮想マシンをオンプレミス環境から分離する必要はありません。Azure の仮想マシンをオンプレミスのネットワークリソースに接続するには、クロスプレミス Azure 仮想ネットワークを構成する必要があります。次の図は、Azure において仮想マシンが含まれるクロスプレミスの Azure 仮想ネットワークを展開するために必要なコンポーネントを示しています。
  
![サイト間 VPN 接続を使用して Microsoft Azure に接続されているオンプレミスのネットワーク](images/CP_ConnectOnPremisesNetworkToAzureVPN.png)
  
この図では、サイト間の仮想プライベート ネットワーク (VPN) 接続によって、2 つのネットワーク (オンプレミス ネットワークと Azure 仮想ネットワーク) が接続されています。サイト間の VPN 接続はオンプレミス ネットワークの VPN デバイスと Azure 仮想ネットワークの Azure VPN gatewayで終端されます。Azure 仮想ネットワークには仮想マシンがあります。Azure 仮想ネットワークの仮想マシンで発生したネットワーク トラフィックは VPN gatewayに送信され、次にこのトラフィックはサイト間 VPN 接続を介してオンプレミス ネットワーク上の VPN デバイスに送信されます。その後、オンプレミス ネットワークのルーティング インフラストラクチャによって、宛先にトラフィックが送られます。
  
Azure 仮想ネットワークとオンプレミス ネットワーク間の VPN 接続を設定するには、次の手順を実行します。 
  
1. **オンプレミス:** オンプレミスの VPN デバイスをポイントするオンプレミス ネットワーク ルートを、Azure 仮想ネットワークのアドレス空間上で定義して作成します。
    
2. **Microsoft Azure:**サイト間 VPN 接続では、Azure の仮想ネットワークを作成します。この資料については説明しません[ExpressRoute](https://azure.microsoft.com/services/expressroute/)を使用します。
    
3. **オンプレミス:** VPN 接続を終了するようにオンプレミスのハードウェアまたはソフトウェア VPN デバイスを構成します。これには、インターネット プロトコル セキュリティ (IPsec) が使用されます。
    
サイト間 VPN 接続を確立した後、仮想ネットワークのサブネットに Azure 仮想マシンを追加します。
  
## <a name="plan-your-azure-virtual-network"></a>Azure 仮想ネットワークの計画
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>前提条件
<a name="Prerequisites"> </a>

- Azure サブスクリプション。Azure サブスクリプションについては、「[Microsoft Azure サブスクリプション ページ](https://azure.microsoft.com/pricing/purchase-options/)」に移動します。
    
- 仮想ネットワークとサブネットに割り当て可能なプライベート IPv4 アドレス空間。現在、および将来の拡大で必要となる仮想マシン数に対応できる十分な空き領域が必要です。
    
- IPsec の要件に対応するサイト間 VPN 接続を終端するための VPN デバイスがオンプレミス ネットワークで利用可能なこと。詳しくは、「[サイト間 VPN Gateway 接続の VPN デバイスについて](https://go.microsoft.com/fwlink/p/?LinkId=393093)」をご覧ください。
    
- ルーティング インフラストラクチャを変更し、Azure Virtual Network のアドレス空間にルーティングされるトラフィックが、サイト間 VPN 接続をホストする VPN デバイスに送られること。
    
- オンプレミス ネットワークと Azure Virtual Network に接続するコンピューターにインターネットへのアクセスを提供する Web プロキシ。
    
### <a name="solution-architecture-design-assumptions"></a>ソリューション アーキテクチャ設計の前提条件
<a name="DesignAssumptions"> </a>

次の一覧に、このソリューション アーキテクチャ用に作られた設計の方針を示します。 
  
- このソリューションでは、サイト間 VPN 接続を伴う 1 つの Azure Virtual Network を使用します。Azure Virtual Network は、任意の数の仮想マシンを接続できる単一のサブネットをホストします。 
    
- Windows Server 2016 または Windows Server 2012 でルーティングとリモート アクセス サービス (RRAS) を使用してオンプレミス ネットワークと Azure 仮想ネットワーク間の IPsec サイト間 VPN 接続を確立できます。また、Cisco または Juniper Networks などの VPN デバイスも使用できます。
    
- オンプレミス ネットワークには、引き続き Windows Server Active Directory (AD)、ドメイン ネーム システム (DNS)、プロキシ サーバーなどのネットワーク サービスを配置することもできます。要件によっては、そうしたネットワーク リソースの一部を Azure 仮想ネットワークに配置する方がよい場合があります。
    
1 つ以上のサブネットを使用している既存の Azure 仮想ネットワークの場合、要件に基づいて、必要な仮想マシンをホストするための追加のサブネットのためのアドレス空間が残っているかどうかを判断します。追加のサブネット用のアドレス空間が残っていない場合には、独自のサイト間 VPN 接続を使用した仮想ネットワークを追加作成します。
  
### <a name="plan-the-routing-infrastructure-changes-for-the-azure-virtual-network"></a>Azure Virtual Network 用のルーティング インフラストラクチャの変更計画
<a name="routing"> </a>

オンプレミス ルーティング インフラストラクチャを構成し、Azure Virtual Network のアドレス空間宛てのトラフィックを、サイト間 VPN 接続をホストするオンプレミス VPN デバイスに送るようにする必要があります。
  
ルーティング インフラストラクチャを更新する詳細な方法は、ルーティング情報を管理する方法によって異なります。次の方法があります。
  
- ルーティング テーブルを手動構成で更新します。
    
- ルーティング テーブルを、ルーティング情報プロトコル (RIP) または Open Shortest Path First (OSPF) などのルーティング プロトコルに基づいて更新します。
    
ルーティングの専門家に相談し、Azure 仮想ネットワーク宛てのトラフィックがオンプレミス VPN デバイスに確実に送信されるようにしてください。
  
### <a name="plan-for-firewall-rules-for-traffic-to-and-from-the-on-premises-vpn-device"></a>オンプレミス VPN デバイスとの間のトラフィックに関するファイアウォール規則の計画
<a name="firewall"> </a>

VPN デバイスが境界ネットワーク上にあり、境界ネットワークとインターネット間にファイルウォールが存在する場合、サイト間 VPN 接続を行えるようにするため、以下の規則でファイアウォールを構成しなければならないことがあります。
  
- VPN デバイスへのトラフィック (インターネットからの受信):
    
  - VPN デバイスと IP プロトコル 50 の宛先 IP アドレス
    
  - VPN デバイスと UDP 宛先ポート 500 の宛先 IP アドレス
    
  - VPN デバイスと UDP 宛先ポート 4500 の宛先 IP アドレス
    
- VPN デバイスからのトラフィック (インターネットへの発信):
    
  - VPN デバイスと IP プロトコル 50 の発信元 IP アドレス
    
  - VPN デバイスと UDP 発信元ポート 500 の発信元 IP アドレス
    
  - VPN デバイスと UDP 発信元ポート 4500 の発信元 IP アドレス
    
### <a name="plan-for-the-private-ip-address-space-of-the-azure-virtual-network"></a>Azure Virtual Network 用のプライベート IP アドレス空間の計画
<a name="IPAddresses"> </a>

Azure Virtual Network のプライベート IP アドレス空間は、仮想ネットワークをホストするために Azure が使用するアドレスに対応できるとともに、Azure 仮想マシン用の十分なアドレスが含まれるサブネットが少なくとも 1 つ含まれていなければなりません。
  
サブネットに必要なアドレス数を判別するには、現在必要な仮想マシン数、および今後の拡張で必要となる推定数を数え、次の表を使用してサブネットのサイズを決定します。
  
|**必要な仮想マシンの数**|**必要なホスト ビット数**|**サブネットのサイズ**|
|:-----|:-----|:-----|
|1 ～ 3  <br/> |3  <br/> |/29  <br/> |
|4 ～11  <br/> |4  <br/> |/28  <br/> |
|12 ～27  <br/> |5  <br/> |/27  <br/> |
|28 ～ 59  <br/> |6  <br/> |/26  <br/> |
|60 ～123  <br/> |7  <br/> |/25  <br/> |
   
### <a name="planning-worksheet-for-configuring-your-azure-virtual-network"></a>Azure Virtual Network を構成するための計画ワークシート
<a name="worksheet"> </a>

仮想マシンをホストする Azure 仮想ネットワークを作成する前に、次の表で必要な設定を判別する必要があります。
  
仮想ネットワークの設定を表 V に記入してください。
  
 **表 V:クロスプレミスの仮想ネットワーク構成**
  
|**項目**|**構成要素**|**説明**|**値**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |仮想ネットワーク名  <br/> |Azure 仮想ネットワークに割り当てる名前 (DirSyncNet など)。  <br/> |__________________  <br/> |
|2.  <br/> |仮想ネットワークの場所  <br/> |仮想ネットワークが含まれる Azure データセンター (米国西部など)。  <br/> |__________________  <br/> |
|3.  <br/> |VPN デバイスの IP アドレス  <br/> |インターネット上の VPN デバイスのインターフェイスのパブリック IPv4 アドレス。IT 部門に尋ねてこのアドレスを特定してください。  <br/> |__________________  <br/> |
|4.  <br/> |仮想ネットワークのアドレス スペース  <br/> |仮想ネットワークのアドレス スペース (1 つのプライベート アドレス プレフィックスで定義されます)。IT 部門に尋ねてこのアドレス スペースを特定してください。アドレス スペースは、クラスレス ドメイン間ルーティング (CIDR) 形式 (別名、ネットワーク プレフィックス形式) でなければなりません。10.24.64.0/20 などです。  <br/> |__________________  <br/> |
|5.  <br/> |IPsec 共有キー  <br/> |32 文字のランダムな英数字文字列。サイト間 VPN 接続の両側を認証するために使用されます。IT 部門またはセキュリティ部門に尋ねて、このキー値を決定してからそれを安全な場所に格納します。または、「[IPsec 事前共有キーのランダム文字列を作成する](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx)」をご覧ください。<br/> |__________________  <br/> |
   
このソリューションのサブネットに関しては表 S に記入してください。
  
- 最初のサブネットについて、Azure ゲートウェイ サブネットの 28 ビットのアドレス空間 (プレフィックスの長さ /28) を決定します。このアドレス空間の計算方法については「[Azure 仮想ネットワークのゲートウェイ サブネット アドレス空間の計算](https://blogs.technet.microsoft.com/solutions_advisory_board/2016/12/01/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks/)」を参照してください。
    
- 2 番目のサブネットには、フレンドリ名、仮想ネットワークのアドレス スペースに基づく 1 つの IP アドレス スペース、わかりやすい目的を指定します。
    
IT 部門に尋ねて、仮想ネットワークのアドレス スペースに基づきこれらのアドレス スペースを決定してください。どちらのアドレス スペースも CIDR 形式でなければなりません。
  
 **表 S:仮想ネットワーク内のサブネット**
  
|**項目**|**サブネット名**|**サブネット アドレス スペース**|**目的**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |GatewaySubnet  <br/> |_____________________________  <br/> |Azure ゲートウェイが使用するサブネット。  <br/> |
|2.  <br/> |_____________________________  <br/> |_____________________________  <br/> |_____________________________  <br/> |
   
仮想ネットワーク内で仮想マシンを使用するオンプレミスの DNS サーバーに関して、表 D に記入してください。各 DNS サーバーにフレンドリ名と 1 つの IP アドレスを指定します。このフレンドリ名は、DNS サーバーのホスト名またはコンピューター名と同じでなくても構いません。空白のエントリが 2 つ表示されていますが、項目は追加できます。IT 部門に尋ねてこの一覧を特定してください。
  
 **表 D:オンプレミスの DNS サーバー**
  
|**項目**|**DNS サーバーのフレンドリ名**|**DNS サーバーの IP アドレス**|
|:-----|:-----|:-----|
|1.  <br/> |_____________________________  <br/> |_____________________________  <br/> |
|2.  <br/> |_____________________________  <br/> |_____________________________  <br/> |
   
Azure 仮想ネットワークから組織のネットワークにサイト間 VPN 接続を介してパケットをルーティングするには、ローカル ネットワークを使用して仮想ネットワークを構成する必要があります。このローカル ネットワークには、仮想ネットワーク内の仮想マシンが到達する必要がある組織のオンプレミス ネットワーク上のすべての場所に関するアドレス スペース (CIDR 形式) の一覧が含まれます。オンプレミス ネットワークまたはサブネットのすべての場所になる可能性があります。ローカル ネットワークを定義するアドレス スペースの一覧は一意である必要があり、他の仮想ネットワークで使用するアドレス スペースと重複させることはできません。
  
一連のローカル ネットワークのアドレス スペースに関しては表 L に記入します。3 つの空白のエントリが記載されていますが、多くの場合さらに必要となります。IT 部門に尋ねてこの表を記入してください。
  
 **表 L:ローカル ネットワークのアドレス プレフィックス**
  
|**項目**|**ローカル ネットワークのアドレス スペース**|
|:-----|:-----|
|1.  <br/> |_____________________________  <br/> |
|2.  <br/> |_____________________________  <br/> |
|3.  <br/> |_____________________________  <br/> |
   
## <a name="deployment-roadmap"></a>展開のロードマップ
<a name="DeploymentRoadmap"> </a>

クロスプレミス仮想ネットワークの作成と Azure への仮想マシンの追加には 3 つのフェーズがあります。
  
- フェーズ 1: オンプレミス ネットワークの準備
    
- フェーズ 2: Azure でのクロスプレミスの仮想ネットワークの作成
    
- フェーズ 3 (省略可能)：仮想コンピューターの追加
    
### <a name="phase-1-prepare-your-on-premises-network"></a>フェーズ 1: オンプレミス ネットワークの準備
<a name="Phase1"> </a>

仮想ネットワークのアドレス空間に向けたトラフィックを最終的にオンプレミスネットワークの境界にあるルーターへ送信できるよう、オンプレミスネットワークを設定する必要があります。ネットワーク管理者に問い合わせ、オンプレミス ネットワークのルーティング インフラストラクチャにルートを追加する方法を決定してください。
  
最終的な構成をここに示します。
  
![オンプレミスのネットワークには、VPN デバイスへつながる仮想ネットワークのアドレス スペースのルートが必要です。](images/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### <a name="phase-2-create-the-cross-premises-virtual-network-in-azure"></a>フェーズ 2: Azure でのクロスプレミスの仮想ネットワークの作成
<a name="Phase2"> </a>

最初に、Azure PowerShell プロンプトを開きます。Azure PowerShell をインストールしていない場合は、「[Azure の PowerShell コマンドレットを使う](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)」を参照してください。
  
> [!NOTE]
> これらのコマンドは Azure PowerShell 1.0 以降を対象としています。この記事に掲載されているすべての PowerShell コマンドを含むテキスト ファイルについては、[こちら](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-commands-for-5c5a7c19)をクリックしてください。 
  
次に、このコマンドを使用して Azure アカウントにログインします。
  
```
Login-AzureRMAccount
```

次のコマンドを使用して、サブスクリプションの名前を取得します。
  
```
Get-AzureRMSubscription | Sort SubscriptionName | Select SubscriptionName
```

これらのコマンドで Azure サブスクリプションを設定します。二重引用符内のすべて (< 文字と > 文字を含む) を正しいサブスクリプション名に置き換えます。
  
```
$subscrName="<subscription name>"
Select-AzureRMSubscription -SubscriptionName $subscrName -Current
```

次に、仮想ネットワーク用の新しいリソース グループを作成します。一意のリソース グループ名を決定するには、このコマンドを使用して既存のリソース グループを一覧表示します。
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

これらのコマンドを使用して、新しいリソース グループを作成します。
  
```
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName

```

リソース マネージャー ベースの仮想マシンでは、リソース マネージャー ベースのストレージ アカウントが必要です。選択するストレージ アカウント名は、小文字の英字と数字のみを含むグローバルに一意の名前でなければなりません。このコマンドを使用して、既存のストレージ アカウントを一覧表示できます。
  
```
Get-AzureRMStorageAccount | Sort Name | Select Name
```

提案されたストレージ アカウントの名前が一意かどうかをテストするには、このコマンドを使用します。
  
```
Get-AzureRmStorageAccountNameAvailability "<proposed name>"
```

新しいストレージ アカウントを作成するには、これらのコマンドを実行します。
  
```
$rgName="<your new resource group name>"
$locName="<the location of your new resource group>"
$saName="<unique storage account name>"
New-AzureRMStorageAccount -Name $saName -ResourceGroupName $rgName -Type Standard_LRS -Location $locName
```

次に、Azure 仮想ネットワークを作成します。
  
```
# Fill in the variables from previous values and from Tables V, S, and D
$rgName="<name of your new resource group>"
$locName="<Azure location of your new resource group>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$gwSubnetPrefix="<Table S - Item 1 - Subnet address space column>"
$SubnetName="<Table S - Item 2 - Subnet name column>"
$SubnetPrefix="<Table S - Item 2 - Subnet address space column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )

# Get the shortened version of the location
$rg=Get-AzureRmResourceGroup -Name $rgName
$locShortName=$rg.Location

# Create the Azure virtual network and a network security group that allows incoming remote desktop connections to the subnet that is hosting virtual machines
$gatewaySubnet=New-AzureRmVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnetPrefix
$vmSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name $SubnetName -AddressPrefix $SubnetPrefix
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gatewaySubnet,$vmSubnet -DNSServer $dnsServers
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName -Location $locShortName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $SubnetName -AddressPrefix $SubnetPrefix -NetworkSecurityGroup $nsg
```

最終的な構成をここに示します。
  
![仮想ネットワークは、オンプレミスのネットワークにまだ接続されていません。](images/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
次に、これらのコマンドを使用して、サイト間 VPN 接続のゲートウェイを作成します。
  
```
# Fill in the variables from previous values and from Tables V and L
$vnetName="<Table V - Item 1 - Value column>"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -SubnetId $vnet.Subnets[0].Id
# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig
# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix
# Create the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway
```

最終的な構成をここに示します。
  
![仮想ネットワークに、ゲートウェイがあるようになりました。](images/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
次に、Azure VPN gatewayに接続するためのオンプレミス VPN デバイスを構成します。詳しくは、「[サイト間 VPN Gateway 接続の VPN デバイスについて](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)」をご覧ください。
  
VPN デバイスを構成するために必要なものを以下に記します。
  
- 仮想ネットワーク用の Azure VPN ゲートウェイのパブリック IPv4 アドレス。 **Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** コマンドを使って、このアドレスを表示します。
    
- サイト間 VPN 接続の IPsec 事前共有キー (表 V - 項目 5 - [値] 列)。
    
最終的な構成をここに示します。
  
![仮想ネットワークが、オンプレミスのネットワークに接続されました。](images/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### <a name="phase-3-optional-add-virtual-machines"></a>フェーズ 3 (省略可能)：仮想マシンの追加
<a name="Phase2"> </a>

Azure で必要な仮想マシンを作成します。詳細は「[Azure ポータルで最初の Windows 仮想マシンを作成する](https://go.microsoft.com/fwlink/p/?LinkId=393098)」を参照してください。
  
以下の設定を使用します。
  
- **[基本]** ウィンドウで、仮想ネットワークと同じサブスクリプションおよびリソース グループを選択します。ユーザー名とパスワードを安全な場所に記録します。後ほど、仮想マシンにサインインするときに必要になります。
    
- **[サイズ]** ウィンドウで、適切なサイズを選択します。
    
- **[設定]** ウィンドウの **[ストレージ]** セクションで、 **[標準]** ストレージ タイプと仮想ネットワークを設定したストレージ アカウントを選択します。 **[ネットワーク]** セクションで、(ゲートウェイ サブネットではなく) 仮想マシンをホストするための仮想ネットワークの名前とサブネットを選択します。他のすべての設定は、既定値のままにします。
    
内部 DNS をチェックして A (Address) レコードが新しい仮想マシン用に追加されたことを確認し、仮想マシンが正しく DNS を使用していることを検証します。インターネットにアクセスするためには、Azure 仮想マシンを、オンプレミス ネットワークのプロキシ サーバーを使用するように構成する必要があります。サーバーで実行する追加の構成ステップについては、ネットワーク管理者にお尋ねください。
  
最終的な構成をここに示します。
  
![仮想ネットワークは、オンプレミスのネットワークからアクセス可能な仮想マシンをホストするようになりました。](images/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## <a name="see-also"></a>See Also

<a name="DeploymentRoadmap"> </a>

[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)
  
[Microsoft Azure での Office 365 ディレクトリ同期 (DirSync) の展開](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)

[仮想マシンの作成方法](https://go.microsoft.com/fwlink/p/?LinkId=393098)
  
[サイト間 VPN Gateway 接続の VPN デバイスについて](https://azure.microsoft.com/documentation/articles/vpn-gateway-about-vpn-devices/)
  
[Azure PowerShell のインストールおよび構成方法](https://azure.microsoft.com/documentation/articles/powershell-install-configure/#how-to-install-azure-powershell)



