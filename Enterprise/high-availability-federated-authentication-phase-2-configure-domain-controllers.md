---
title: 高可用性の統合認証のフェーズ 2 を構成するドメイン コント ローラー
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 概要:Microsoft Azure で Office 365 の高可用性フェデレーション認証用に、ドメイン コントローラーと DirSync サーバーを構成します。
ms.openlocfilehash: 1e66403348bc2cd9a6dfab56f32735d62c986035
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915152"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a>高可用性フェデレーション認証のフェーズ 2:ドメイン コントローラーを構成する

 **概要:** Microsoft Azure で Office 365 の高可用性フェデレーション認証用に、ドメイン コントローラーと DirSync サーバーを構成します。
  
Azure インフラストラクチャ サービスに Office 365 フェデレーション認証の高可用性を展開するために、このフェーズでは、Azure の仮想ネットワークに 2 つのドメイン コントローラーと 1 つの DirSync サーバーを構成します。オンプレミス ネットワークへのサイト間 VPN 接続を経由して認証トラフィックを送信するのではなく、Azure 仮想ネットワーク内で認証に対するクライアント Web 要求を認証できます。
  
> [!NOTE]
> Active Directory フェデレーション サービス (AD FS) では、Windows Server AD ドメイン コントローラーの代用として、Azure Active Directory Domain Services を使用できません。 
  
上に移動する前に、このフェーズを完了する必要があります[高可用性の統合認証フェーズ 3: AD FS サーバーを構成する](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)です。フェーズのすべては、 [Azure で Office 365 の展開の高可用性フェデレーション認証](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)を参照してください。
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a>Azure にドメイン コントローラー仮想マシンを作成する

まず、「表 M」の「 **仮想マシン名** 」列に必要事項を入力し、必要に応じて、「 **最小サイズ** 」列で仮想マシンのサイズを変更します。
  
|**アイテム**|**仮想マシン名**|**ギャラリー イメージ**|**ストレージの種類**|**最小サイズ**|
|:-----|:-----|:-----|:-----|:-----|
|1.  <br/> |![](./media/Common-Images/TableLine.png) (最初のドメイン コントローラー。例: DC1)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|2.  <br/> |![](./media/Common-Images/TableLine.png) (2 番目のドメイン コントローラー。例: DC2)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|3.  <br/> |![](./media/Common-Images/TableLine.png)(ディレクトリ同期サーバー、DS1 の例)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|4.  <br/> |![](./media/Common-Images/TableLine.png)(最初 AD FS サーバー、ADFS1 の例)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|5.  <br/> |![](./media/Common-Images/TableLine.png)(2 回目 AD FS サーバー、ADFS2 の例)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|6.  <br/> |![](./media/Common-Images/TableLine.png)(最初の web アプリケーション プロキシ サーバー WEB1 の例)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|7.  <br/> |![](./media/Common-Images/TableLine.png)(第 2 web アプリケーション プロキシ サーバー WEB2 の例)  <br/> |Windows Server 2016 Datacenter  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
   
 **M - Azure 内の Office 365 の高可用性のフェデレーション認証のための仮想マシンの表**
  
仮想マシンのサイズの一覧については、「[Azure の仮想マシンのサイズ](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes)」を参照してください。
  
Azure PowerShell の次のコマンド ブロックでは、2 つのドメイン コント ローラーの仮想マシンを作成します。削除して、変数の値を指定します\<と > の文字。Azure の PowerShell コマンド ブロックが次のテーブルから値を使用することに注意してください。
  
- 表 M: 仮想マシン用
    
- 表 R: リソース グループ用
    
- 表 V: 仮想ネットワークの設定用
    
- 表 S: サブネット用
    
- 表 I: 静的 IP アドレス用
    
- 表 A: 可用性セット用
    
テーブル R、V、S、I、および A で定義したことを思い出して[高可用性の統合認証フェーズ 1: 構成の Azure](high-availability-federated-authentication-phase-1-configure-azure.md)。
  
> [!NOTE]
> 次のコマンド セットは、Azure PowerShell の最新版を使用します。「[Azure PowerShell の概要](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)」を参照してください。 
  
すべてに適切な値を指定したら、その結果のブロックを Azure PowerShell プロンプト、またはローカル コンピューターの PowerShell 統合スクリプト環境 (ISE) で実行します。
  
> [!TIP]
> すべての PowerShell コマンドは、この資料で即座に実行の PowerShell コマンド ブロックが、カスタム設定に基づくを生成する Microsoft Excel の構成のブックに含まれているテキスト ファイルを参照してください[Office 365 のフェデレーション認証Azure 展開キット](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)です。 
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the DirSync server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the DirSync server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> これらの仮想マシンは、イントラネット アプリケーションには、ためいないパブリック IP アドレスまたは DNS ドメイン名のラベルが割り当てられているそしてインターネットに公開します。ただし、つまり、Azure ポータルからのそれらに接続できません。仮想マシンのプロパティを表示するときは、[**接続**] オプションは使用できません。プライベート IP アドレスまたはイントラネット DNS 名を使用して仮想マシンに接続するリモート デスクトップ接続の付属品、または別のリモート デスクトップ ツールを使用します。
  
## <a name="configure-the-first-domain-controller"></a>最初のドメイン コントローラーを構成する

任意のリモート デスクトップ クライアントを使用して、最初のドメイン コント ローラー仮想マシンへのリモート デスクトップ接続を作成します。イントラネット DNS を使用するか、ローカル管理者アカウントのコンピューター名と資格情報を使用します。
  
このコマンドを使用して最初のドメイン コント ローラーに、Windows PowerShell コマンド プロンプト**で最初のドメイン コント ローラー仮想マシン**から、次に、余分なデータ ディスクを追加します。
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

次に、最初のドメイン コントローラーから組織ネットワーク上の場所への接続をテストします。テストには、組織ネットワーク上のリソースの名前と IP アドレスを探索する **ping** コマンドを使用します。
  
この手順により、DNS の名前解決が正常に動作していること (仮想マシンがオンプレミスの DNS サーバーで正しく構成されていること) を確認します。また、クロスプレミスの仮想ネットワークでパケットが送受信できることを確認します。この基本的なテストに失敗した場合は、IT 部門に問い合わせて、DNS の名前解決とパケット配信に関する問題のトラブルシューティングを実施してください。
  
次に、最初のドメイン コントローラーの Windows PowerShell コマンド プロンプトで、次に示すコマンドを実行します。
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

ドメイン管理者アカウントの資格情報の入力を求めるダイアログが表示されます。コンピューターが再起動されます。
  
## <a name="configure-the-second-domain-controller"></a>2 番目のドメイン コントローラーを構成する

任意のリモート デスクトップ クライアントを使用して、2 番目のドメイン コント ローラー仮想マシンへのリモート デスクトップ接続を作成します。イントラネット DNS を使用するか、ローカル管理者アカウントのコンピューター名と資格情報を使用します。
  
次に、余分なデータ ディスクを Windows PowerShell コマンド プロンプト**で 2 番目のドメイン コント ローラー仮想マシン**からこのコマンドを使用して 2 つ目のドメイン コント ローラーに追加する必要があります。
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

次に、以下のコマンドを実行します。
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

ドメイン管理者アカウントの資格情報の入力を求めるダイアログが表示されます。コンピューターが再起動されます。
  
次に、その Azure に仮想マシンの DNS サーバーとして使用する新しい 2 つのドメイン コント ローラーの IP アドレスが割り当てられますので、仮想ネットワークの DNS サーバーを更新する必要があります。変数を入力し、ローカル コンピューター上の Windows PowerShell コマンド プロンプトからこれらのコマンドを実行します。
  
```
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

$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzureRMVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $secondDCName
```

2 つのドメイン コントローラーを再起動して、これらが DNS サーバーとしてオンプレミスの DNS サーバーで構成されないようにします。これらはいずれも DNS サーバーなので、ドメイン コントローラーに昇格されたときに、自動的に DNS フォワーダーとして、オンプレミスの DNS サーバーで構成されていました。
  
次に、Active Directory のレプリケーション サイトを作成して、Azure 仮想ネットワークのサーバーがローカル ドメイン コントローラーを使用するようにする必要があります。ドメイン管理者アカウントを使用してどちらかのドメイン コントローラーに接続し、管理者レベルの Windows PowerShell プロンプトから次に示すコマンドを実行します。
  
```
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-dirsync-server"></a>DirSync サーバーを構成する

任意のリモート デスクトップ クライアントを使用し、ディレクトリ同期サーバーの仮想マシンへのリモート デスクトップ接続を作成します。そのイントラネット DNS 名またはコンピューター名、ローカルの管理者アカウントの資格情報を使用します。
  
次に、Windows PowerShell プロンプトでこれらのコマンドを使用して、適切な Windows Server AD ドメインに参加させます。
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

次に、このフェーズが正常に完了した結果の構成を示します。コンピューター名にはプレース ホルダーを使用しています。
  
**フェーズ 2:Azure での高可用性フェデレーション認証インフラストラクチャ用のドメイン コントローラーと DirSync サーバー**

![ドメイン コントローラーによる Azure での高可用性 Office 365 フェデレーション認証のフェーズ 2](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a>次の手順

「[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)」を使用して、このワークロードの構成を続行します。
  
## <a name="see-also"></a>関連項目

[Azure に Office 365 の高可用性フェデレーション認証を展開する](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Office 365 開発/テスト環境のフェデレーション ID](federated-identity-for-your-office-365-dev-test-environment.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)

[フェデレーションの認証オプション](about-office-365-identity.md#federated-authentication-options)


