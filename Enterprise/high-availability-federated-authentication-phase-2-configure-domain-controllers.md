---
title: 高可用性フェデレーション認証のフェーズ2ドメインコントローラーを構成する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: '概要: Microsoft Azure の Microsoft 365 の高可用性フェデレーション認証用に、ドメインコントローラーおよびディレクトリ同期サーバーを構成します。'
ms.openlocfilehash: 14939691e8dc114a6234bfee1ade7212762eae04
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102525"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a>高可用性フェデレーション認証のフェーズ 2: ドメイン コントローラーを構成する

Azure インフラストラクチャサービスに Microsoft 365 フェデレーション認証の高可用性を展開するためのこのフェーズでは、Azure 仮想ネットワークに2つのドメインコントローラーとディレクトリ同期サーバーを構成します。 オンプレミス ネットワークへのサイト間 VPN 接続を経由して認証トラフィックを送信するのではなく、Azure 仮想ネットワーク内で認証に対するクライアント Web 要求を認証できます。
  
> [!NOTE]
> Active directory フェデレーションサービス (AD FS) は、Active Directory ドメインサービス (AD DS) ドメインコントローラーの代用として、Azure Active Directory (Azure AD) を使用できません。 
  
[「フェーズ 3: AD FS サーバーを構成](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)する」に進む前に、このフェーズを完了する必要があります。 すべてのフェーズについては、「 [Microsoft 365 の高可用性フェデレーション認証を Azure に展開](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)する」を参照してください。
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a>Azure にドメイン コントローラー仮想マシンを作成する

まず、「表 M」の「 **仮想マシン名** 」列に必要事項を入力し、必要に応じて、「 **最小サイズ** 」列で仮想マシンのサイズを変更します。
  
|**アイテム**|**仮想マシン名**|**ギャラリー イメージ**|**ストレージの種類**|**最小サイズ**|
|:-----|:-----|:-----|:-----|:-----|
|1.  <br/> |![線](./media/Common-Images/TableLine.png)  (最初のドメイン コントローラー。例: DC1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|2.  <br/> |![線](./media/Common-Images/TableLine.png)  (2 番目のドメイン コントローラー。例: DC2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|3.  <br/> |![線](./media/Common-Images/TableLine.png) (ディレクトリ同期サーバー、例 DS1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|4.  <br/> |![線](./media/Common-Images/TableLine.png) (最初の AD FS サーバー、例 ADFS1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|5.  <br/> |![線](./media/Common-Images/TableLine.png) (2 番目の AD FS サーバー、例 ADFS2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|6.  <br/> |![線](./media/Common-Images/TableLine.png) (最初の web アプリケーションプロキシサーバー。例: WEB1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|7.  <br/> |![線](./media/Common-Images/TableLine.png) (2 番目の web アプリケーションプロキシサーバー。例: WEB2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
   
 **表 M-Azure での Microsoft 365 の高可用性フェデレーション認証用の仮想マシン**
  
仮想マシンのサイズの一覧については、「[Azure の仮想マシンのサイズ](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes)」を参照してください。
  
次に示す Azure PowerShell コマンド ブロックは、2 つのドメイン コントローラー用の仮想マシンを作成します。 変数の値を指定して、その文字を削除し \< and > ます。 なお、この Azure PowerShell コマンド ブロックは、次の表の値を使用します。
  
- 表 M: 仮想マシン用
    
- 表 R: リソース グループ用
    
- 表 V: 仮想ネットワークの設定用
    
- 表 S: サブネット用
    
- 表 I: 静的 IP アドレス用
    
- 表 A: 可用性セット用
    
「[フェーズ 1: Azure を構成](high-availability-federated-authentication-phase-1-configure-azure.md)する」の表 R、V、S、I、A を定義していることを思い出してください。
  
> [!NOTE]
> 次のコマンド セットは、Azure PowerShell の最新版を使用します。 「 [Azure PowerShell の概要」を](https://docs.microsoft.com/powershell/azure/get-started-azureps)参照してください。 
  
すべてに適切な値を指定したら、その結果のブロックを Azure PowerShell プロンプト、またはローカル コンピューターの PowerShell 統合スクリプト環境 (ISE) で実行します。
  
> [!TIP]
> カスタム設定に基づいて、すぐに実行できる PowerShell コマンドブロックを生成するには、この[Microsoft Excel 構成ブック](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx)を使用します。 

```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Active Directory Domain Services (AD DS) data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for AD DS data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the directory synchronization server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the directory synchronization server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.
  
## <a name="configure-the-first-domain-controller"></a>最初のドメイン コントローラーを構成する

Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.
  
次に、**最初のドメインコントローラー仮想マシン**の Windows PowerShell コマンドプロンプトから、次のコマンドを使用して、最初のドメインコントローラーに追加のデータディスクを追加します。
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

次に、最初のドメイン コントローラーから組織ネットワーク上の場所への接続をテストします。テストには、組織ネットワーク上のリソースの名前と IP アドレスを探索する **ping** コマンドを使用します。
  
This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.
  
次に、最初のドメイン コントローラーの Windows PowerShell コマンド プロンプトで、次に示すコマンドを実行します。
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

You will be prompted to supply the credentials of a domain administrator account. The computer will restart.
  
## <a name="configure-the-second-domain-controller"></a>2 番目のドメイン コントローラーを構成する

Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.
  
次に、 **2 番目のドメインコントローラー仮想マシン**の Windows PowerShell コマンドプロンプトから、次のコマンドを使用して、2番目のドメインコントローラーに追加のデータディスクを追加する必要があります。
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

次に、以下のコマンドを実行します。
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

You will be prompted to supply the credentials of a domain administrator account. The computer will restart.
  
次に、DNS サーバーとして使用する 2 つの新しいドメイン コントローラーの IP アドレスを Azure が仮想マシンに割り当てるように、仮想ネットワークの DNS サーバーを更新する必要があります。 変数にデータを入力し、ローカルコンピューターの Windows PowerShell コマンドプロンプトから次のコマンドを実行します。
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$adrgName="<Table R - Item 1 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$onpremDNSIP1="<Table D - Item 1 - DNS server IP address column>"
$onpremDNSIP2="<Table D - Item 2 - DNS server IP address column>"
$staticIP1="<Table I - Item 1 - Value column>"
$staticIP2="<Table I - Item 2 - Value column>"
$firstDCName="<Table M - Item 1 - Virtual machine name column>"
$secondDCName="<Table M - Item 2 - Virtual machine name column>"

$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzVM -ResourceGroupName $adrgName -Name $secondDCName
```

Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.
  
Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a>ディレクトリ同期サーバーを構成する

任意のリモートデスクトップクライアントを使用して、ディレクトリ同期サーバー仮想マシンへのリモートデスクトップ接続を作成します。 イントラネット DNS を使用するか、ローカル管理者アカウントのコンピューター名と資格情報を使用します。
  
次に、Windows PowerShell プロンプトでこれらのコマンドを使用して、適切な AD DS ドメインに参加させます。
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

次に、このフェーズが正常に完了した結果の構成を示します。コンピューター名にはプレース ホルダーを使用しています。
  
**フェーズ 2: Azure の高可用性フェデレーション認証インフラストラクチャ用のドメインコントローラーおよびディレクトリ同期サーバー**

![ドメインコントローラーを含む Azure における高可用性 Microsoft 365 フェデレーション認証インフラストラクチャのフェーズ2](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a>次の手順

[「フェーズ 3: AD FS サーバーを構成](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)する」を使用して、このワークロードの構成を続行します。
  
## <a name="see-also"></a>関連項目

[Azure に Microsoft 365 の高可用性フェデレーション認証を展開する](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Microsoft 365 開発/テスト環境のフェデレーション id](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.yml)


