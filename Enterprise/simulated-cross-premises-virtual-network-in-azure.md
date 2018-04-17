---
title: Azure でのシミュレートされたクロスプレミスの仮想ネットワーク
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
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 0a3555dc-6f96-49a5-b9e2-7760e16630b3
description: '概要: は、Microsoft Azure で開発/テスト環境とシミュレーションの間、設置型の仮想ネットワークを作成します。'
ms.openlocfilehash: 41988e8201e896a7c1900b645e6c38357d0bfcd0
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="simulated-cross-premises-virtual-network-in-azure"></a>Azure でのシミュレートされたクロスプレミスの仮想ネットワーク

 **の概要:**Microsoft Azure で開発/テスト環境としてのシミュレーションの間、設置型の仮想ネットワークを作成します。
  
この記事では、2 つの Azure 仮想ネットワークを使用した、Microsoft Azure でのシミュレートされたハイブリッド クラウド環境の作成について順を追って説明します。最終的な構成は、次のようになります。   
  
![XPrem VNet に DC2 仮想マシンがある場合の、シミュレートされたクロスプレミスの仮想ネットワークネットワークの開発/テスト環境のフェーズ 3](images/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
これは Azure IaaS ハイブリッド クラウド運用環境をシミュレートするもので、次のもので構成されます。
  
- 	Azure 仮想ネットワークでホストされる、シミュレートおよび単純化されたオンプレミス ネットワーク (TestLab 仮想ネットワーク)。
    
- 	Azure でホストされる、シミュレートされたクロスプレミスの仮想ネットワーク (XPrem)。
    
- 	2 つの仮想ネットワーク間の VNet ピアリング関係。
    
- 	XPrem 仮想ネットワークのセカンダリ ドメイン コントローラー。
    
これは次のことを行うための基礎および共通の開始点となります。  
  
- 	シミュレートされた Azure IaaS ハイブリッド クラウド環境におけるアプリケーションの開発およびテスト。
    
- 	ハイブリッド クラウドベース IT ワークロードをシミュレートするための、コンピューターのテスト構成の作成 (TestLab 仮想ネットワーク内、および XPrem 仮想ネットワーク内)。
    
次の 3 つの主要なフェーズを経て、この開発/テスト環境を設定します。
  
1. 	TestLab 仮想ネットワークを構成します。
    
2. クロスプレミスの仮想ネットワークを作成します。
    
3. DC2 を構成します。
    
> [!NOTE]
> この構成では、有料版の Azure サブスクリプションが必要です。 
  
![Microsoft Cloud のテスト ラボ ガイド](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> 
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。
  
## <a name="phase-1-configure-the-testlab-virtual-network"></a>フェーズ 1: TestLab 仮想ネットワークを構成する

[基本構成の開発/テスト環境](base-configuration-dev-test-environment.md)で、Azure 仮想ネットワークの名前付きテスト ラボに DC1、APP1、CLIENT1 コンピューターを構成する手順を使用します。
  
これは、現在の構成です。 
  
![CLIENT1 仮想マシンを含む Azure のフェーズ 4 基本構成](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>フェーズ 2: XPrem 仮想ネットワークを作成する

このフェーズでは、新しい XPrem 仮想ネットワークを作成および構成し、それを VNet ピアリングで TestLab 仮想ネットワークに接続します。
  
最初に、ローカル コンピューターで Azure PowerShell プロンプトを起動します。
  
> [!NOTE]
> 次のコマンド セットは、Azure の PowerShell の最新バージョンを使用します。[Azure の PowerShell コマンドレットの入門](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)を参照してください。 
  
次のコマンドを使用して Azure アカウントにログインします。
  
```
Login-AzureRMAccount
```

> [!TIP]
> クリックして[ここで](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0)すべての PowerShell コマンドは、この資料に含まれているテキスト ファイルを取得します。
  
次のコマンドを使用して、サブスクリプションの名前を取得します。
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Azure サブスクリプションを設定します。など、二重引用符内のすべてを交換して、\<と > 文字は、正しい名前を持つ。
  
```
$subscrName="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscrName | Select-AzureRmSubscription
```

次に、これらのコマンドを使用して、XPrem 仮想ネットワークを作成し、ネットワーク セキュリティ グループで保護します。
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$Testnet=New-AzureRMVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzureRMVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzureRMNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
```

次に、これらのコマンドを使用して、TestLab と XPrem VNet 間の VNet ピアリング関係を作成します。
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzureRmVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzureRmVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

これは、現在の構成です。 
  
![XPrem VNet と VNet のピアリング関係がある場合の、シミュレートされたクロスプレミスの仮想ネットワークネットワークの開発/テスト環境のフェーズ 2](images/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>フェーズ 3: DC2 を構成する

このフェーズでは、XPrem 仮想ネットワークにおいて DC2 仮想マシンを作成し、それをレプリカ ドメイン コントローラーとして構成します。
  
まず、DC2 用の仮想マシンを作成します。自分のローカル コンピューターの Azure PowerShell コマンド プロンプトで、これらのコマンドを実行します。
  
```
$rgName="<your resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzureRMVMConfig -VMName DC2 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "StandardLRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

次に、 [Azure ポータル](https://portal.azure.com)ローカル管理者のアカウント名とパスワードを使用してから新しい DC2 バーチャル マシンに接続します。
  
次に、Windows ファイアウォール ルールを構成して、基本的な接続テストのトラフィックを許可します。DC2 の管理者レベルの Windows PowerShell コマンド プロンプトから、これらのコマンドを実行します。  
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

ping コマンドを実行すると、IP アドレス 10.0.0.4 から 4 つの正常な応答があります。これは、VNet ピアリング関係間のトラフィックのテストです。  
  
DC2 上の Windows PowerShell コマンド プロンプトからこのコマンドを使用してドライブ文字 f: を持つ新しいボリュームとして余分なデータ ディスクを次に、追加します。
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

次に corp.contoso.com ドメインのレプリカ ドメイン コントローラーとして DC2 を構成します。DC2 の Windows PowerShell コマンド プロンプトから次のコマンドを実行します。
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\\NTDS" -LogPath "F:\\Logs" -SysvolPath "F:\\SYSVOL"
```

CORP の両方を指定するように求められますことに注意してください\\User1 のパスワードとディレクトリ サービス復元モード (DSRM) のパスワードでは、DC2 を再起動するとします。 
  
XPrem 仮想ネットワーク独自の DNS サーバー (DC2) の準備が整ったので、この DNS サーバーを使用するよう XPrem 仮想ネットワークを構成する必要があります。自分のローカル コンピューターの Azure PowerShell コマンド プロンプトから、これらのコマンドを実行します。
  
```
$vnet=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzureRmVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRmVM -ResourceGroupName $rgName -Name "DC2"
```

Azure ポータル、ローカル コンピューター上では、CORP を DC1 に接続\\User1 の資格情報です。コンピューターとユーザー認証のため、ローカル ドメイン コント ローラーを使用するように、CORP ドメインを構成するには、DC1 上で管理者レベルの Windows PowerShell コマンド プロンプトからこれらのコマンドを実行します。
  
```
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

これは、現在の構成です。 
  
![XPrem VNet に DC2 仮想マシンがある場合の、シミュレートされたクロスプレミスの仮想ネットワークネットワークの開発/テスト環境のフェーズ 3](images/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
シミュレートされた Azure ハイブリッド クラウド環境をテストする準備ができました。
  
## <a name="next-step"></a>次の手順

この開発/テスト環境を使用すると、 [Azure でホストされている SharePoint サーバー 2016年イントラネットのファーム](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)をシミュレートします。
  
## <a name="see-also"></a>関連項目

[基本構成開発/テスト環境](base-configuration-dev-test-environment.md)
  
[Office 365 開発/テスト環境](office-365-dev-test-environment.md)
  
[Office 365 開発/テスト環境の DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[Office 365 開発/テスト環境の Cloud App Security](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Office 365 開発/テスト環境の Advanced Threat Protection](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)


