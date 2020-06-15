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
ms.openlocfilehash: 6e75b8787fb5d077cf082d5beb47827c5132706e
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711940"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="6a8cd-103">高可用性フェデレーション認証のフェーズ 2: ドメイン コントローラーを構成する</span><span class="sxs-lookup"><span data-stu-id="6a8cd-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

<span data-ttu-id="6a8cd-104">Azure インフラストラクチャサービスに Microsoft 365 フェデレーション認証の高可用性を展開するためのこのフェーズでは、Azure 仮想ネットワークに2つのドメインコントローラーとディレクトリ同期サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-104">In this phase of deploying high availability for Microsoft 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the directory synchronization server in the Azure virtual network.</span></span> <span data-ttu-id="6a8cd-105">オンプレミス ネットワークへのサイト間 VPN 接続を経由して認証トラフィックを送信するのではなく、Azure 仮想ネットワーク内で認証に対するクライアント Web 要求を認証できます。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-105">Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="6a8cd-106">Active directory フェデレーションサービス (AD FS) は、Active Directory ドメインサービスドメインコントローラーの代用として、Azure Active Directory ドメインサービスを使用できません。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-106">Active Directory Federation Services (AD FS) cannot use Azure Active Directory Domain Services as a substitute for Active Directory Domain Services domain controllers.</span></span> 
  
<span data-ttu-id="6a8cd-107">[「フェーズ 3: AD FS サーバーを構成](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)する」に進む前に、このフェーズを完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-107">You must complete this phase before moving on to [Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span></span> <span data-ttu-id="6a8cd-108">すべてのフェーズについては、「 [Microsoft 365 の高可用性フェデレーション認証を Azure に展開](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-108">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="6a8cd-109">Azure にドメイン コントローラー仮想マシンを作成する</span><span class="sxs-lookup"><span data-stu-id="6a8cd-109">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="6a8cd-110">まず、「表 M」の「 **仮想マシン名** 」列に必要事項を入力し、必要に応じて、「 **最小サイズ** 」列で仮想マシンのサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-110">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="6a8cd-111">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="6a8cd-111">**Item**</span></span>|<span data-ttu-id="6a8cd-112">**仮想マシン名**</span><span class="sxs-lookup"><span data-stu-id="6a8cd-112">**Virtual machine name**</span></span>|<span data-ttu-id="6a8cd-113">**ギャラリー イメージ**</span><span class="sxs-lookup"><span data-stu-id="6a8cd-113">**Gallery image**</span></span>|<span data-ttu-id="6a8cd-114">**ストレージの種類**</span><span class="sxs-lookup"><span data-stu-id="6a8cd-114">**Storage type**</span></span>|<span data-ttu-id="6a8cd-115">**最小サイズ**</span><span class="sxs-lookup"><span data-stu-id="6a8cd-115">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="6a8cd-116">1.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-116">1.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png) <span data-ttu-id="6a8cd-118"> (最初のドメイン コントローラー。例: DC1)</span><span class="sxs-lookup"><span data-stu-id="6a8cd-118">(first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="6a8cd-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="6a8cd-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="6a8cd-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="6a8cd-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="6a8cd-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="6a8cd-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="6a8cd-122">2.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-122">2.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png) <span data-ttu-id="6a8cd-124"> (2 番目のドメイン コントローラー。例: DC2)</span><span class="sxs-lookup"><span data-stu-id="6a8cd-124">(second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="6a8cd-125">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="6a8cd-125">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="6a8cd-126">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="6a8cd-126">Standard_LRS</span></span>  <br/> |<span data-ttu-id="6a8cd-127">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="6a8cd-127">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="6a8cd-128">3.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-128">3.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png) <span data-ttu-id="6a8cd-130">(ディレクトリ同期サーバー、例 DS1)</span><span class="sxs-lookup"><span data-stu-id="6a8cd-130">(directory synchronization server, example DS1)</span></span>  <br/> |<span data-ttu-id="6a8cd-131">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="6a8cd-131">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="6a8cd-132">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="6a8cd-132">Standard_LRS</span></span>  <br/> |<span data-ttu-id="6a8cd-133">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="6a8cd-133">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="6a8cd-134">4.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-134">4.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png) <span data-ttu-id="6a8cd-136">(最初の AD FS サーバー、例 ADFS1)</span><span class="sxs-lookup"><span data-stu-id="6a8cd-136">(first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="6a8cd-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="6a8cd-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="6a8cd-138">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="6a8cd-138">Standard_LRS</span></span>  <br/> |<span data-ttu-id="6a8cd-139">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="6a8cd-139">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="6a8cd-140">5.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-140">5.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png) <span data-ttu-id="6a8cd-142">(2 番目の AD FS サーバー、例 ADFS2)</span><span class="sxs-lookup"><span data-stu-id="6a8cd-142">(second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="6a8cd-143">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="6a8cd-143">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="6a8cd-144">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="6a8cd-144">Standard_LRS</span></span>  <br/> |<span data-ttu-id="6a8cd-145">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="6a8cd-145">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="6a8cd-146">6.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-146">6.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png) <span data-ttu-id="6a8cd-148">(最初の web アプリケーションプロキシサーバー。例: WEB1)</span><span class="sxs-lookup"><span data-stu-id="6a8cd-148">(first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="6a8cd-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="6a8cd-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="6a8cd-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="6a8cd-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="6a8cd-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="6a8cd-151">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="6a8cd-152">7.</span><span class="sxs-lookup"><span data-stu-id="6a8cd-152">7.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png) <span data-ttu-id="6a8cd-154">(2 番目の web アプリケーションプロキシサーバー。例: WEB2)</span><span class="sxs-lookup"><span data-stu-id="6a8cd-154">(second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="6a8cd-155">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="6a8cd-155">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="6a8cd-156">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="6a8cd-156">Standard_LRS</span></span>  <br/> |<span data-ttu-id="6a8cd-157">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="6a8cd-157">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="6a8cd-158">**表 M-Azure での Microsoft 365 の高可用性フェデレーション認証用の仮想マシン**</span><span class="sxs-lookup"><span data-stu-id="6a8cd-158">**Table M - Virtual machines for the high availability federated authentication for Microsoft 365 in Azure**</span></span>
  
<span data-ttu-id="6a8cd-159">仮想マシンのサイズの一覧については、「[Azure の仮想マシンのサイズ](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-159">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="6a8cd-160">次に示す Azure PowerShell コマンド ブロックは、2 つのドメイン コントローラー用の仮想マシンを作成します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-160">The following Azure PowerShell command block creates the virtual machines for the two domain controllers.</span></span> <span data-ttu-id="6a8cd-161">変数の値を指定して、その文字を削除し \< and > ます。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-161">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="6a8cd-162">なお、この Azure PowerShell コマンド ブロックは、次の表の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-162">Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="6a8cd-163">表 M: 仮想マシン用</span><span class="sxs-lookup"><span data-stu-id="6a8cd-163">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="6a8cd-164">表 R: リソース グループ用</span><span class="sxs-lookup"><span data-stu-id="6a8cd-164">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="6a8cd-165">表 V: 仮想ネットワークの設定用</span><span class="sxs-lookup"><span data-stu-id="6a8cd-165">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="6a8cd-166">表 S: サブネット用</span><span class="sxs-lookup"><span data-stu-id="6a8cd-166">Table S, for your subnets</span></span>
    
- <span data-ttu-id="6a8cd-167">表 I: 静的 IP アドレス用</span><span class="sxs-lookup"><span data-stu-id="6a8cd-167">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="6a8cd-168">表 A: 可用性セット用</span><span class="sxs-lookup"><span data-stu-id="6a8cd-168">Table A, for your availability sets</span></span>
    
<span data-ttu-id="6a8cd-169">「[フェーズ 1: Azure を構成](high-availability-federated-authentication-phase-1-configure-azure.md)する」の表 R、V、S、I、A を定義していることを思い出してください。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-169">Recall that you defined Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="6a8cd-170">次のコマンド セットは、Azure PowerShell の最新版を使用します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-170">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="6a8cd-171">「 [Azure PowerShell の概要」を](https://docs.microsoft.com/powershell/azure/get-started-azureps)参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-171">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="6a8cd-172">すべてに適切な値を指定したら、その結果のブロックを Azure PowerShell プロンプト、またはローカル コンピューターの PowerShell 統合スクリプト環境 (ISE) で実行します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-172">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
> [!TIP]
> <span data-ttu-id="6a8cd-173">カスタム設定に基づいて、すぐに実行できる PowerShell コマンドブロックを生成するには、この[Microsoft Excel 構成ブック](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx)を使用します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-173">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx).</span></span> 

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
> <span data-ttu-id="6a8cd-p105">これらの仮想マシンはイントラネット アプリケーション向けのため、パブリック IP アドレスや DNS ドメイン名のラベルが割り当てられていません。また、インターネットに公開もされていません。ただし、これは Azure ポータルから接続できないことも意味します。仮想マシンのプロパティを表示したときに、**[接続]** オプションは使用できない状態になります。リモート デスクトップ接続アクセサリなどのリモート デスクトップ ツールを使用して、仮想マシンのプライベート IP アドレスまたはイントラネット DNS 名で仮想マシンに接続します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="6a8cd-178">最初のドメイン コントローラーを構成する</span><span class="sxs-lookup"><span data-stu-id="6a8cd-178">Configure the first domain controller</span></span>

<span data-ttu-id="6a8cd-p106">任意のリモート デスクトップ クライアントを使用して、最初のドメイン コント ローラー仮想マシンへのリモート デスクトップ接続を作成します。イントラネット DNS を使用するか、ローカル管理者アカウントのコンピューター名と資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-p106">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="6a8cd-181">次に、**最初のドメインコントローラー仮想マシン**の Windows PowerShell コマンドプロンプトから、次のコマンドを使用して、最初のドメインコントローラーに追加のデータディスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-181">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="6a8cd-182">次に、最初のドメイン コントローラーから組織ネットワーク上の場所への接続をテストします。テストには、組織ネットワーク上のリソースの名前と IP アドレスを探索する **ping** コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-182">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="6a8cd-p107">この手順により、DNS の名前解決が正常に動作していること (仮想マシンがオンプレミスの DNS サーバーで正しく構成されていること) を確認します。また、クロスプレミスの仮想ネットワークでパケットが送受信できることを確認します。この基本的なテストに失敗した場合は、IT 部門に問い合わせて、DNS の名前解決とパケット配信に関する問題のトラブルシューティングを実施してください。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-p107">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="6a8cd-185">次に、最初のドメイン コントローラーの Windows PowerShell コマンド プロンプトで、次に示すコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-185">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="6a8cd-p108">ドメイン管理者アカウントの資格情報の入力を求めるダイアログが表示されます。コンピューターが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-p108">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="6a8cd-188">2 番目のドメイン コントローラーを構成する</span><span class="sxs-lookup"><span data-stu-id="6a8cd-188">Configure the second domain controller</span></span>

<span data-ttu-id="6a8cd-p109">任意のリモート デスクトップ クライアントを使用して、2 番目のドメイン コント ローラー仮想マシンへのリモート デスクトップ接続を作成します。イントラネット DNS を使用するか、ローカル管理者アカウントのコンピューター名と資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-p109">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="6a8cd-191">次に、 **2 番目のドメインコントローラー仮想マシン**の Windows PowerShell コマンドプロンプトから、次のコマンドを使用して、2番目のドメインコントローラーに追加のデータディスクを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-191">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="6a8cd-192">次に、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-192">Next, run the following commands:</span></span>
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="6a8cd-p110">ドメイン管理者アカウントの資格情報の入力を求めるダイアログが表示されます。コンピューターが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-p110">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
<span data-ttu-id="6a8cd-195">次に、DNS サーバーとして使用する 2 つの新しいドメイン コントローラーの IP アドレスを Azure が仮想マシンに割り当てるように、仮想ネットワークの DNS サーバーを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-195">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers.</span></span> <span data-ttu-id="6a8cd-196">変数にデータを入力し、ローカルコンピューターの Windows PowerShell コマンドプロンプトから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-196">Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
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

<span data-ttu-id="6a8cd-p112">2 つのドメイン コントローラーを再起動して、これらが DNS サーバーとしてオンプレミスの DNS サーバーで構成されないようにします。これらはいずれも DNS サーバーなので、ドメイン コントローラーに昇格されたときに、自動的に DNS フォワーダーとして、オンプレミスの DNS サーバーで構成されていました。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-p112">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="6a8cd-p113">次に、Active Directory のレプリケーション サイトを作成して、Azure 仮想ネットワークのサーバーがローカル ドメイン コントローラーを使用するようにする必要があります。ドメイン管理者アカウントを使用してどちらかのドメイン コントローラーに接続し、管理者レベルの Windows PowerShell プロンプトから次に示すコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-p113">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a><span data-ttu-id="6a8cd-201">ディレクトリ同期サーバーを構成する</span><span class="sxs-lookup"><span data-stu-id="6a8cd-201">Configure the directory synchronization server</span></span>

<span data-ttu-id="6a8cd-202">任意のリモートデスクトップクライアントを使用して、ディレクトリ同期サーバー仮想マシンへのリモートデスクトップ接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-202">Use the remote desktop client of your choice and create a remote desktop connection to the directory synchronization server virtual machine.</span></span> <span data-ttu-id="6a8cd-203">イントラネット DNS を使用するか、ローカル管理者アカウントのコンピューター名と資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-203">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="6a8cd-204">次に、Windows PowerShell プロンプトでこれらのコマンドを使用して、適切な AD DS ドメインに参加させます。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-204">Next, join it to the appropriate AD DS domain with these commands at the Windows PowerShell prompt.</span></span>
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="6a8cd-205">次に、このフェーズが正常に完了した結果の構成を示します。コンピューター名にはプレース ホルダーを使用しています。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-205">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="6a8cd-206">**フェーズ 2: Azure の高可用性フェデレーション認証インフラストラクチャ用のドメインコントローラーおよびディレクトリ同期サーバー**</span><span class="sxs-lookup"><span data-stu-id="6a8cd-206">**Phase 2: The domain controllers and directory synchronization server for your high availability federated authentication infrastructure in Azure**</span></span>

![ドメインコントローラーを含む Azure における高可用性 Microsoft 365 フェデレーション認証インフラストラクチャのフェーズ2](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="6a8cd-208">次の手順</span><span class="sxs-lookup"><span data-stu-id="6a8cd-208">Next step</span></span>

<span data-ttu-id="6a8cd-209">[「フェーズ 3: AD FS サーバーを構成](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)する」を使用して、このワークロードの構成を続行します。</span><span class="sxs-lookup"><span data-stu-id="6a8cd-209">Use [Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6a8cd-210">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a8cd-210">See Also</span></span>

[<span data-ttu-id="6a8cd-211">Azure で Microsoft 365 の高可用性フェデレーション認証を展開する</span><span class="sxs-lookup"><span data-stu-id="6a8cd-211">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="6a8cd-212">Microsoft 365 開発/テスト環境のフェデレーション id</span><span class="sxs-lookup"><span data-stu-id="6a8cd-212">Federated identity for your Microsoft 365 dev/test environment</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)
  
[<span data-ttu-id="6a8cd-213">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="6a8cd-213">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)


