---
title: 高可用性フェデレーション認証のフェーズ 3 AD FS サーバーを構成する
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
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: 概要:Microsoft Azure で Office 365 の高可用性フェデレーション認証用に、Active Directory フェデレーション サービス (AD FS) を作成して構成します。
ms.openlocfilehash: 5ac87b0d19c43e8711e188d1a0f6a7f33a37871f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840154"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a><span data-ttu-id="2bce4-103">高可用性フェデレーション認証のフェーズ 3: AD FS サーバーを構成する</span><span class="sxs-lookup"><span data-stu-id="2bce4-103">High availability federated authentication Phase 3: Configure AD FS servers</span></span>

<span data-ttu-id="2bce4-104">Azure インフラストラクチャ サービスに Office 365 フェデレーション認証の高可用性を展開するために、このフェーズでは、内部ロード バランサーと 2 つの AD FS サーバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="2bce4-104">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="2bce4-105">このフェーズは、「[フェーズ 4: web アプリケーションプロキシを構成](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)する」に進む前に完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bce4-105">You must complete this phase before moving on to [Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md).</span></span> <span data-ttu-id="2bce4-106">すべてのフェーズについては、「[Azure に Office 365 の高可用性フェデレーション認証を展開する](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bce4-106">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a><span data-ttu-id="2bce4-107">Azure に AD FS サーバー仮想マシンを作成する</span><span class="sxs-lookup"><span data-stu-id="2bce4-107">Create the AD FS server virtual machines in Azure</span></span>

<span data-ttu-id="2bce4-p102">次に示す PowerShell コマンドのブロックを使用して、2 つの AD FS サーバーの仮想マシンを作成します。この PowerShell コマンド セットには、次の表の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="2bce4-p102">Use the following block of PowerShell commands to create the virtual machines for the two AD FS servers. This PowerShell command set uses values from the following tables:</span></span>
  
- <span data-ttu-id="2bce4-110">表 M: 仮想マシン用</span><span class="sxs-lookup"><span data-stu-id="2bce4-110">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="2bce4-111">表 R: リソース グループ用</span><span class="sxs-lookup"><span data-stu-id="2bce4-111">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="2bce4-112">表 V: 仮想ネットワークの設定用</span><span class="sxs-lookup"><span data-stu-id="2bce4-112">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="2bce4-113">表 S: サブネット用</span><span class="sxs-lookup"><span data-stu-id="2bce4-113">Table S, for your subnets</span></span>
    
- <span data-ttu-id="2bce4-114">表 I: 静的 IP アドレス用</span><span class="sxs-lookup"><span data-stu-id="2bce4-114">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="2bce4-115">表 A: 可用性セット用</span><span class="sxs-lookup"><span data-stu-id="2bce4-115">Table A, for your availability sets</span></span>
    
<span data-ttu-id="2bce4-116">「フェーズ 2: configure [Azure](high-availability-federated-authentication-phase-1-configure-azure.md)」の「[フェーズ 2: ドメインコントローラー](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)と表 R、V、S、I、A を構成する」で表 M を定義していることを思い出してください。</span><span class="sxs-lookup"><span data-stu-id="2bce4-116">Recall that you defined Table M in [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="2bce4-117">次のコマンド セットは、Azure PowerShell の最新版を使用します。</span><span class="sxs-lookup"><span data-stu-id="2bce4-117">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="2bce4-118">「 [Azure PowerShell の概要」を](https://docs.microsoft.com/powershell/azure/get-started-azureps)参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bce4-118">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="2bce4-119">まず、2 つの AD FS サーバー用に Azure の内部ロード バランサーを作成します。</span><span class="sxs-lookup"><span data-stu-id="2bce4-119">First, you create an Azure internal load balancer for the two AD FS servers.</span></span> <span data-ttu-id="2bce4-120">変数の値を指定し、文字\<と > を削除します。</span><span class="sxs-lookup"><span data-stu-id="2bce4-120">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="2bce4-121">適切な値をすべて指定したら、その結果のブロックを Azure PowerShell コマンド プロンプトまたは PowerShell ISE で実行します。</span><span class="sxs-lookup"><span data-stu-id="2bce4-121">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="2bce4-122">カスタム設定に基づいて、すぐに実行できる PowerShell コマンドブロックを生成するには、この[Microsoft Excel 構成ブック](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx)を使用します。</span><span class="sxs-lookup"><span data-stu-id="2bce4-122">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx).</span></span> 

```powershell
# Set up key variables
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$privIP="<Table I - Item 4 - Value column>"
$rgName=<Table R - Item 4 - Resource group name column>"

$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "ADFSServers-LBFE" -PrivateIPAddress $privIP -Subnet $subnet
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "ADFSServers-LBBE"

$healthProbe=New-AzLoadBalancerProbeConfig -Name WebServersProbe -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "HTTPSTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="2bce4-123">次に、AD FS サーバー仮想マシンを作成します。</span><span class="sxs-lookup"><span data-stu-id="2bce4-123">Next, create the AD FS server virtual machines.</span></span>
  
<span data-ttu-id="2bce4-124">適切な値をすべて指定したら、その結果のブロックを Azure PowerShell コマンド プロンプトまたは PowerShell ISE で実行します。</span><span class="sxs-lookup"><span data-stu-id="2bce4-124">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$avName="<Table A - Item 2 - Availability set name column>"
$rgNameTier="<Table R - Item 2 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first ADFS server virtual machine
$vmName="<Table M - Item 4 - Virtual machine name column>"
$vmSize="<Table M - Item 4 - Minimum size column>"
$staticIP="<Table I - Item 5 - Value column>"
$diskStorageType="<Table M - Item 4 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second AD FS virtual machine
$vmName="<Table M - Item 5 - Virtual machine name column>"
$vmSize="<Table M - Item 5 - Minimum size column>"
$staticIP="<Table I - Item 6 - Value column>"
$diskStorageType="<Table M - Item 5 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

```

> [!NOTE]
> <span data-ttu-id="2bce4-p105">これらの仮想マシンはイントラネット アプリケーション向けのため、パブリック IP アドレスや DNS ドメイン名のラベルが割り当てられていません。また、インターネットに公開もされていません。ただし、これは Azure ポータルから接続できないことも意味します。仮想マシンのプロパティを表示したときに、**[接続]** オプションは使用できない状態になります。リモート デスクトップ接続アクセサリなどのリモート デスクトップ ツールを使用して、仮想マシンのプライベート IP アドレスまたはイントラネット DNS 名で仮想マシンに接続します。</span><span class="sxs-lookup"><span data-stu-id="2bce4-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
<span data-ttu-id="2bce4-p106">仮想マシンごとに、お好みのリモート デスクトップ クライアントを使用して、リモート デスクトップ接続を作成します。イントラネット DNS を使用するか、ローカル管理者アカウントのコンピューター名と資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="2bce4-p106">For each virtual machine, use the remote desktop client of your choice and create a remote desktop connection. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="2bce4-131">仮想マシンごとに、Windows PowerShell プロンプトでこれらのコマンドを使用して、それらの仮想マシンを適切な Active Directory ドメインサービス (AD DS) ドメインに参加させます。</span><span class="sxs-lookup"><span data-stu-id="2bce4-131">For each virtual machine, join them to the appropriate Active Directory Domain Services (AD DS) domain with these commands at the Windows PowerShell prompt.</span></span>
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="2bce4-132">次に、このフェーズが正常に完了した結果の構成を示します。コンピューター名にはプレース ホルダーを使用しています。</span><span class="sxs-lookup"><span data-stu-id="2bce4-132">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="2bce4-133">**フェーズ 3:Azure での高可用性フェデレーション認証インフラストラクチャ用の AD FS サーバーと内部ロード バランサー**</span><span class="sxs-lookup"><span data-stu-id="2bce4-133">**Phase 3: The AD FS servers and internal load balancer for your high availability federated authentication infrastructure in Azure**</span></span>

![AD FS サーバーを使用した Azure における高可用性 Office 365 フェデレーション認証インフラストラクチャのフェーズ3](media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a><span data-ttu-id="2bce4-135">次の手順</span><span class="sxs-lookup"><span data-stu-id="2bce4-135">Next step</span></span>

<span data-ttu-id="2bce4-136">[「フェーズ 4: web アプリケーションプロキシを構成](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)する」を使用して、このワークロードの構成を続行します。</span><span class="sxs-lookup"><span data-stu-id="2bce4-136">Use [Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2bce4-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bce4-137">See Also</span></span>

[<span data-ttu-id="2bce4-138">Azure に Office 365 の高可用性フェデレーション認証を展開する</span><span class="sxs-lookup"><span data-stu-id="2bce4-138">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="2bce4-139">Office 365 開発/テスト環境のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="2bce4-139">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)


