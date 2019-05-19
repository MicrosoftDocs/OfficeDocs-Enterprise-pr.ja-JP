---
title: Azure でのシミュレートされたクロスプレミスの仮想ネットワーク
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 0a3555dc-6f96-49a5-b9e2-7760e16630b3
description: '概要: 開発/テスト環境として、シミュレートされたクロスプレミスの仮想ネットワークを Microsoft Azure に作成します。'
ms.openlocfilehash: 595aa20595f43f481aaf090a14d0d7c0df000345
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162490"
---
# <a name="simulated-cross-premises-virtual-network-in-azure"></a><span data-ttu-id="05260-103">Azure でのシミュレートされたクロスプレミスの仮想ネットワーク</span><span class="sxs-lookup"><span data-stu-id="05260-103">Simulated cross-premises virtual network in Azure</span></span>

 <span data-ttu-id="05260-104">**概要:** 開発/テスト環境として、シミュレートされたクロスプレミスの仮想ネットワークを Microsoft Azure に作成します。</span><span class="sxs-lookup"><span data-stu-id="05260-104">**Summary:** Create a simulated cross-premises virtual network in Microsoft Azure as a dev/test environment.</span></span>
  
<span data-ttu-id="05260-p101">この記事では、2 つの Azure 仮想ネットワークを使用した、Microsoft Azure でのシミュレートされたハイブリッド クラウド環境の作成について順を追って説明します。最終的な構成は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="05260-p101">This article steps you through creating a simulated hybrid cloud environment with Microsoft Azure using two Azure virtual networks. Here is the resulting configuration.</span></span> 
  
![XPrem VNet に DC2 仮想マシンがある場合の、シミュレートされたクロスプレミスの仮想ネットワークネットワークの開発/テスト環境のフェーズ 3](media/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
<span data-ttu-id="05260-108">これは Azure IaaS ハイブリッド クラウド運用環境をシミュレートするもので、次のもので構成されます。</span><span class="sxs-lookup"><span data-stu-id="05260-108">This simulates an Azure IaaS hybrid cloud production environment and consists of:</span></span>
  
- <span data-ttu-id="05260-109">Azure 仮想ネットワークでホストされる、シミュレートおよび単純化されたオンプレミス ネットワーク (TestLab 仮想ネットワーク)。</span><span class="sxs-lookup"><span data-stu-id="05260-109">A simulated and simplified on-premises network hosted in an Azure virtual network (the TestLab virtual network).</span></span>
    
- <span data-ttu-id="05260-110">Azure でホストされる、シミュレートされたクロスプレミスの仮想ネットワーク (XPrem)。</span><span class="sxs-lookup"><span data-stu-id="05260-110">A simulated cross-premises virtual network hosted in Azure (XPrem).</span></span>
    
- <span data-ttu-id="05260-111">2 つの仮想ネットワーク間の VNet ピアリング関係。</span><span class="sxs-lookup"><span data-stu-id="05260-111">A VNet peering relationship between the two virtual networks.</span></span>
    
- <span data-ttu-id="05260-112">XPrem 仮想ネットワークのセカンダリ ドメイン コントローラー。</span><span class="sxs-lookup"><span data-stu-id="05260-112">A secondary domain controller in the XPrem virtual network.</span></span>
    
<span data-ttu-id="05260-113">これは次のことを行うための基礎および共通の開始点となります。</span><span class="sxs-lookup"><span data-stu-id="05260-113">This provides a basis and common starting point from which you can:</span></span> 
  
- <span data-ttu-id="05260-114">シミュレートされた Azure IaaS ハイブリッド クラウド環境におけるアプリケーションの開発およびテスト。</span><span class="sxs-lookup"><span data-stu-id="05260-114">Develop and test applications in a simulated Azure IaaS hybrid cloud environment.</span></span>
    
- <span data-ttu-id="05260-115">ハイブリッド クラウドベース IT ワークロードをシミュレートするための、コンピューターのテスト構成の作成 (TestLab 仮想ネットワーク内、および XPrem 仮想ネットワーク内)。</span><span class="sxs-lookup"><span data-stu-id="05260-115">Create test configurations of computers, some within the TestLab virtual network and some within the XPrem virtual network, to simulate hybrid cloud-based IT workloads.</span></span>
    
<span data-ttu-id="05260-116">次の 3 つの主要なフェーズを経て、この開発/テスト環境を設定します。</span><span class="sxs-lookup"><span data-stu-id="05260-116">There are three major phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="05260-117">TestLab 仮想ネットワークを構成します。</span><span class="sxs-lookup"><span data-stu-id="05260-117">Configure the TestLab virtual network.</span></span>
    
2. <span data-ttu-id="05260-118">クロスプレミスの仮想ネットワークを作成します。</span><span class="sxs-lookup"><span data-stu-id="05260-118">Create the cross-premises virtual network.</span></span>
    
3. <span data-ttu-id="05260-119">DC2 を構成します。</span><span class="sxs-lookup"><span data-stu-id="05260-119">Configure DC2.</span></span>
    
> [!NOTE]
> <span data-ttu-id="05260-120">この構成では、有料版の Azure サブスクリプションが必要です。</span><span class="sxs-lookup"><span data-stu-id="05260-120">This configuration requires a paid Azure subscription.</span></span> 
  
![Microsoft Cloud のテスト ラボ ガイド](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="05260-122">[ここ](http://aka.ms/catlgstack)をクリックして、Office 365 のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップを確認してください。</span><span class="sxs-lookup"><span data-stu-id="05260-122">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-configure-the-testlab-virtual-network"></a><span data-ttu-id="05260-123">フェーズ 1: TestLab 仮想ネットワークを構成する</span><span class="sxs-lookup"><span data-stu-id="05260-123">Phase 1: Configure the TestLab virtual network</span></span>

<span data-ttu-id="05260-124">「[基本構成開発/テスト環境](base-configuration-dev-test-environment.md)」の手順により、TestLab という名前の Azure 仮想ネットワークに DC1、APP1、CLIENT1 コンピューターを構成します。</span><span class="sxs-lookup"><span data-stu-id="05260-124">Use the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md) to configure the DC1, APP1, and CLIENT1 computers in the Azure virtual network named TestLab.</span></span>
  
<span data-ttu-id="05260-125">これは、現在の構成です。</span><span class="sxs-lookup"><span data-stu-id="05260-125">This is your current configuration.</span></span> 
  
![CLIENT1 仮想マシンを含む Azure の基本構成のフェーズ 4](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a><span data-ttu-id="05260-127">フェーズ 2: XPrem 仮想ネットワークを作成する</span><span class="sxs-lookup"><span data-stu-id="05260-127">Phase 2: Create the XPrem virtual network</span></span>

<span data-ttu-id="05260-128">このフェーズでは、新しい XPrem 仮想ネットワークを作成および構成し、それを VNet ピアリングで TestLab 仮想ネットワークに接続します。</span><span class="sxs-lookup"><span data-stu-id="05260-128">In this phase, you create and configure the new XPrem virtual network and then connect it to the TestLab virtual network with VNet peering.</span></span>
  
<span data-ttu-id="05260-129">最初に、ローカル コンピューターで Azure PowerShell プロンプトを起動します。</span><span class="sxs-lookup"><span data-stu-id="05260-129">First, start an Azure PowerShell prompt on your local computer.</span></span>
  
> [!NOTE]
> <span data-ttu-id="05260-p102">次のコマンド セットは、Azure PowerShell の最新版を使用します。「[Azure の PowerShell コマンドレットを使う](https://docs.microsoft.com/ja-JP/powershell/azureps-cmdlets-docs/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05260-p102">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="05260-132">このコマンドを使用して Azure アカウントにサインインします。</span><span class="sxs-lookup"><span data-stu-id="05260-132">Sign in to your Azure account with this command.</span></span>
  
```
Connect-AzAccount
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0) to get a text file that has all of the PowerShell commands in this article.
-->
  
<span data-ttu-id="05260-133">このコマンドを使用して、サブスクリプションの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="05260-133">Get your subscription name using this command.</span></span>
  
```
Get-AzSubscription | Sort Name | Select Name
```

<span data-ttu-id="05260-p103">Azure サブスクリプションを設定します。二重引用符内のすべて (「\<」と「>」の文字を含む) を正しい名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="05260-p103">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct names.</span></span>
  
```
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="05260-136">次に、これらのコマンドを使用して、XPrem 仮想ネットワークを作成し、ネットワーク セキュリティ グループで保護します。</span><span class="sxs-lookup"><span data-stu-id="05260-136">Next, create the XPrem virtual network and protect it with a network security group with these commands.</span></span>
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$Testnet=New-AzVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

<span data-ttu-id="05260-137">次に、これらのコマンドを使用して、TestLab と XPrem VNet 間の VNet ピアリング関係を作成します。</span><span class="sxs-lookup"><span data-stu-id="05260-137">Next, you create the VNet peering relationship between the TestLab and XPrem VNets with these commands.</span></span>
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

<span data-ttu-id="05260-138">これは、現在の構成です。</span><span class="sxs-lookup"><span data-stu-id="05260-138">This is your current configuration.</span></span> 
  
![XPrem VNet と VNet のピアリング関係がある場合の、シミュレートされたクロスプレミスの仮想ネットワークネットワークの開発/テスト環境のフェーズ 2](media/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a><span data-ttu-id="05260-140">フェーズ 3: DC2 を構成する</span><span class="sxs-lookup"><span data-stu-id="05260-140">Phase 3: Configure DC2</span></span>

<span data-ttu-id="05260-141">このフェーズでは、XPrem 仮想ネットワークにおいて DC2 仮想マシンを作成し、それをレプリカ ドメイン コントローラーとして構成します。</span><span class="sxs-lookup"><span data-stu-id="05260-141">In this phase, you create the DC2 virtual machine in the XPrem virtual network and then configure it as a replica domain controller.</span></span>
  
<span data-ttu-id="05260-p104">まず、DC2 用の仮想マシンを作成します。自分のローカル コンピューターの Azure PowerShell コマンド プロンプトで、これらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="05260-p104">First, create a virtual machine for DC2. Run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<your resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzVMConfig -VMName DC2 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="05260-144">次に、ローカル管理者のアカウント名とパスワードを使用して、[Azure portal](https://portal.azure.com) から新しい DC2 仮想マシンに接続します。</span><span class="sxs-lookup"><span data-stu-id="05260-144">Next, connect to the new DC2 virtual machine from the [Azure portal](https://portal.azure.com) using its local administrator account name and password.</span></span>
  
<span data-ttu-id="05260-p105">次に、Windows ファイアウォール ルールを構成して、基本的な接続テストのトラフィックを許可します。DC2 の管理者レベルの Windows PowerShell コマンド プロンプトから、これらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="05260-p105">Next, configure a Windows Firewall rule to allow traffic for basic connectivity testing. From an administrator-level Windows PowerShell command prompt on DC2, run these commands.</span></span> 
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

<span data-ttu-id="05260-p106">ping コマンドを実行すると、IP アドレス 10.0.0.4 から 4 つの正常な応答があります。これは、VNet ピアリング関係間のトラフィックのテストです。</span><span class="sxs-lookup"><span data-stu-id="05260-p106">The ping command should result in four successful replies from IP address 10.0.0.4. This is a test of traffic across the VNet peering relationship.</span></span> 
  
<span data-ttu-id="05260-149">次に、DC2 の Windows PowerShell コマンド プロンプトから次のコマンドを使用して、新しいボリュームとして別のデータ ディスクをドライブ文字 F: で追加します。</span><span class="sxs-lookup"><span data-stu-id="05260-149">Next, add the extra data disk as a new volume with the drive letter F: with this command from the Windows PowerShell command prompt on DC2.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="05260-p107">次に corp.contoso.com ドメインのレプリカ ドメイン コントローラーとして DC2 を構成します。DC2 の Windows PowerShell コマンド プロンプトから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="05260-p107">Next, configure DC2 as a replica domain controller for the corp.contoso.com domain. Run these commands from the Windows PowerShell command prompt on DC2.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

<span data-ttu-id="05260-152">CORP\\User1 パスワードおよびディレクトリ サービス復元モード (DSRM) パスワードの両方の入力、ならびに DC2 の再起動が必要となる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="05260-152">Note that you are prompted to supply both the CORP\\User1 password and a Directory Services Restore Mode (DSRM) password, and to restart DC2.</span></span> 
  
<span data-ttu-id="05260-p108">XPrem 仮想ネットワーク独自の DNS サーバー (DC2) の準備が整ったので、この DNS サーバーを使用するよう XPrem 仮想ネットワークを構成する必要があります。自分のローカル コンピューターの Azure PowerShell コマンド プロンプトから、これらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="05260-p108">Now that the XPrem virtual network has its own DNS server (DC2), you must configure the XPrem virtual network to use this DNS server. Run these commands from the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $rgName -Name "DC2"
```

<span data-ttu-id="05260-p109">ローカル コンピューター上の Azure portal から、CORP\\User1 の資格情報を使用して DC1 に接続します。コンピューターおよびユーザーがローカルのドメイン コントローラーを使用して認証を行うように CORP ドメインを構成するには、DC1 の管理者レベルの Windows PowerShell コマンド プロンプトから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="05260-p109">From the Azure portal on your local computer, connect to DC1 with the CORP\\User1 credentials. To configure the CORP domain so that computers and users use their local domain controller for authentication, run these commands from an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

<span data-ttu-id="05260-157">これは、現在の構成です。</span><span class="sxs-lookup"><span data-stu-id="05260-157">This is your current configuration.</span></span> 
  
![XPrem VNet に DC2 仮想マシンがある場合の、シミュレートされたクロスプレミスの仮想ネットワークネットワークの開発/テスト環境のフェーズ 3](media/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
<span data-ttu-id="05260-159">シミュレートされた Azure ハイブリッド クラウド環境をテストする準備ができました。</span><span class="sxs-lookup"><span data-stu-id="05260-159">Your simulated Azure hybrid cloud environment is now ready for testing.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="05260-160">次の手順</span><span class="sxs-lookup"><span data-stu-id="05260-160">Next step</span></span>

<span data-ttu-id="05260-161">この開発/テスト環境を使用して、[Azure でホストされる SharePoint Server 2016 イントラネット ファーム](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)をシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="05260-161">Use this dev/test environment to simulate a [SharePoint Server 2016 intranet farm hosted in Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="05260-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="05260-162">See Also</span></span>

[<span data-ttu-id="05260-163">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="05260-163">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="05260-164">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="05260-164">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="05260-165">Office 365 開発/テスト環境の DirSync</span><span class="sxs-lookup"><span data-stu-id="05260-165">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="05260-166">Office 365 開発/テスト環境の Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="05260-166">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="05260-167">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="05260-167">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


