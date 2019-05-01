---
title: 高可用性フェデレーション認証のフェーズ2ドメインコントローラーを構成する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 概要:Microsoft Azure で Office 365 の高可用性フェデレーション認証用に、ドメイン コントローラーと DirSync サーバーを構成します。
ms.openlocfilehash: bda22a1df0165724f660019e28a9f088280fea4f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491340"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="0bbc5-103">高可用性フェデレーション認証のフェーズ 2: ドメイン コントローラーを構成する</span><span class="sxs-lookup"><span data-stu-id="0bbc5-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

 <span data-ttu-id="0bbc5-104">**概要:** Microsoft Azure で Office 365 の高可用性フェデレーション認証用に、ドメイン コントローラーと DirSync サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-104">**Summary:** Configure the domain controllers and DirSync server for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="0bbc5-p101">Azure インフラストラクチャ サービスに Office 365 フェデレーション認証の高可用性を展開するために、このフェーズでは、Azure の仮想ネットワークに 2 つのドメイン コントローラーと 1 つの DirSync サーバーを構成します。オンプレミス ネットワークへのサイト間 VPN 接続を経由して認証トラフィックを送信するのではなく、Azure 仮想ネットワーク内で認証に対するクライアント Web 要求を認証できます。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-p101">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the DirSync server in the Azure virtual network. Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0bbc5-107">active directory フェデレーションサービス (AD FS) は、active directory ドメインサービスドメインコントローラーの代用として、Azure active directory ドメインサービスを使用できません。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-107">Active Directory Federation Services (AD FS) cannot use Azure Active Directory Domain Services as a substitute for Active Directory Domain Services domain controllers.</span></span> 
  
<span data-ttu-id="0bbc5-108">このフェーズは、「[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)」に進む前に完了しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-108">You must complete this phase before moving on to [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span></span> <span data-ttu-id="0bbc5-109">すべてのフェーズについては、「[Azure に Office 365 の高可用性フェデレーション認証を展開する](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-109">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="0bbc5-110">Azure にドメイン コントローラー仮想マシンを作成する</span><span class="sxs-lookup"><span data-stu-id="0bbc5-110">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="0bbc5-111">まず、「表 M」の「 **仮想マシン名** 」列に必要事項を入力し、必要に応じて、「 **最小サイズ** 」列で仮想マシンのサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-111">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="0bbc5-112">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="0bbc5-112">**Item**</span></span>|<span data-ttu-id="0bbc5-113">**仮想マシン名**</span><span class="sxs-lookup"><span data-stu-id="0bbc5-113">**Virtual machine name**</span></span>|<span data-ttu-id="0bbc5-114">**ギャラリー イメージ**</span><span class="sxs-lookup"><span data-stu-id="0bbc5-114">**Gallery image**</span></span>|<span data-ttu-id="0bbc5-115">**ストレージの種類**</span><span class="sxs-lookup"><span data-stu-id="0bbc5-115">**Storage type**</span></span>|<span data-ttu-id="0bbc5-116">**最小サイズ**</span><span class="sxs-lookup"><span data-stu-id="0bbc5-116">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="0bbc5-117">1.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-117">1.</span></span>  <br/> |<span data-ttu-id="0bbc5-118">![](./media/Common-Images/TableLine.png) (最初のドメイン コントローラー。例: DC1)</span><span class="sxs-lookup"><span data-stu-id="0bbc5-118">![](./media/Common-Images/TableLine.png) (first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="0bbc5-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="0bbc5-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="0bbc5-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="0bbc5-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="0bbc5-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="0bbc5-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="0bbc5-122">2.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-122">2.</span></span>  <br/> |<span data-ttu-id="0bbc5-123">![](./media/Common-Images/TableLine.png) (2 番目のドメイン コントローラー。例: DC2)</span><span class="sxs-lookup"><span data-stu-id="0bbc5-123">![](./media/Common-Images/TableLine.png) (second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="0bbc5-124">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="0bbc5-124">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="0bbc5-125">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="0bbc5-125">Standard_LRS</span></span>  <br/> |<span data-ttu-id="0bbc5-126">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="0bbc5-126">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="0bbc5-127">3.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-127">3.</span></span>  <br/> |<span data-ttu-id="0bbc5-128">![](./media/Common-Images/TableLine.png)(DirSync サーバー、例 DS1)</span><span class="sxs-lookup"><span data-stu-id="0bbc5-128">![](./media/Common-Images/TableLine.png) (DirSync server, example DS1)</span></span>  <br/> |<span data-ttu-id="0bbc5-129">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="0bbc5-129">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="0bbc5-130">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="0bbc5-130">Standard_LRS</span></span>  <br/> |<span data-ttu-id="0bbc5-131">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="0bbc5-131">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="0bbc5-132">4.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-132">4.</span></span>  <br/> |<span data-ttu-id="0bbc5-133">![](./media/Common-Images/TableLine.png)(最初の AD FS サーバー、例 ADFS1)</span><span class="sxs-lookup"><span data-stu-id="0bbc5-133">![](./media/Common-Images/TableLine.png) (first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="0bbc5-134">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="0bbc5-134">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="0bbc5-135">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="0bbc5-135">Standard_LRS</span></span>  <br/> |<span data-ttu-id="0bbc5-136">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="0bbc5-136">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="0bbc5-137">5.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-137">5.</span></span>  <br/> |<span data-ttu-id="0bbc5-138">![](./media/Common-Images/TableLine.png)(2 番目の AD FS サーバー、例 ADFS2)</span><span class="sxs-lookup"><span data-stu-id="0bbc5-138">![](./media/Common-Images/TableLine.png) (second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="0bbc5-139">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="0bbc5-139">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="0bbc5-140">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="0bbc5-140">Standard_LRS</span></span>  <br/> |<span data-ttu-id="0bbc5-141">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="0bbc5-141">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="0bbc5-142">6.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-142">6.</span></span>  <br/> |<span data-ttu-id="0bbc5-143">![](./media/Common-Images/TableLine.png)(最初の web アプリケーションプロキシサーバー。例: WEB1)</span><span class="sxs-lookup"><span data-stu-id="0bbc5-143">![](./media/Common-Images/TableLine.png) (first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="0bbc5-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="0bbc5-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="0bbc5-145">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="0bbc5-145">Standard_LRS</span></span>  <br/> |<span data-ttu-id="0bbc5-146">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="0bbc5-146">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="0bbc5-147">7.</span><span class="sxs-lookup"><span data-stu-id="0bbc5-147">7.</span></span>  <br/> |<span data-ttu-id="0bbc5-148">![](./media/Common-Images/TableLine.png)(2 番目の web アプリケーションプロキシサーバー。例: WEB2)</span><span class="sxs-lookup"><span data-stu-id="0bbc5-148">![](./media/Common-Images/TableLine.png) (second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="0bbc5-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="0bbc5-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="0bbc5-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="0bbc5-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="0bbc5-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="0bbc5-151">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="0bbc5-152">**表 M-Azure での Office 365 の高可用性フェデレーション認証用の仮想マシン**</span><span class="sxs-lookup"><span data-stu-id="0bbc5-152">**Table M - Virtual machines for the high availability federated authentication for Office 365 in Azure**</span></span>
  
<span data-ttu-id="0bbc5-153">仮想マシンのサイズの一覧については、「[Azure の仮想マシンのサイズ](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-153">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="0bbc5-154">次に示す Azure PowerShell コマンド ブロックは、2 つのドメイン コントローラー用の仮想マシンを作成します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-154">The following Azure PowerShell command block creates the virtual machines for the two domain controllers.</span></span> <span data-ttu-id="0bbc5-155">変数の値を指定し、 \<および > 文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-155">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="0bbc5-156">なお、この Azure PowerShell コマンド ブロックは、次の表の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-156">Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="0bbc5-157">表 M: 仮想マシン用</span><span class="sxs-lookup"><span data-stu-id="0bbc5-157">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="0bbc5-158">表 R: リソース グループ用</span><span class="sxs-lookup"><span data-stu-id="0bbc5-158">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="0bbc5-159">表 V: 仮想ネットワークの設定用</span><span class="sxs-lookup"><span data-stu-id="0bbc5-159">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="0bbc5-160">表 S: サブネット用</span><span class="sxs-lookup"><span data-stu-id="0bbc5-160">Table S, for your subnets</span></span>
    
- <span data-ttu-id="0bbc5-161">表 I: 静的 IP アドレス用</span><span class="sxs-lookup"><span data-stu-id="0bbc5-161">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="0bbc5-162">表 A: 可用性セット用</span><span class="sxs-lookup"><span data-stu-id="0bbc5-162">Table A, for your availability sets</span></span>
    
<span data-ttu-id="0bbc5-163">表 R、V、S、I、A in[高可用性フェデレーション認証のフェーズ 1: Azure を構成](high-availability-federated-authentication-phase-1-configure-azure.md)したことを思い出してください。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-163">Recall that you defined Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="0bbc5-p104">次のコマンド セットは、Azure PowerShell の最新版を使用します。「[Azure PowerShell の概要](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="0bbc5-166">すべてに適切な値を指定したら、その結果のブロックを Azure PowerShell プロンプト、またはローカル コンピューターの PowerShell 統合スクリプト環境 (ISE) で実行します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-166">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
<!--
> [!TIP]
> For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
-->
  
```
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

# Create the DirSync server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the DirSync server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="0bbc5-p105">これらの仮想マシンはイントラネット アプリケーション向けのため、パブリック IP アドレスや DNS ドメイン名のラベルが割り当てられていません。また、インターネットに公開もされていません。ただし、これは Azure ポータルから接続できないことも意味します。仮想マシンのプロパティを表示したときに、**[接続]** オプションは使用できない状態になります。リモート デスクトップ接続アクセサリなどのリモート デスクトップ ツールを使用して、仮想マシンのプライベート IP アドレスまたはイントラネット DNS 名で仮想マシンに接続します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="0bbc5-171">最初のドメイン コントローラーを構成する</span><span class="sxs-lookup"><span data-stu-id="0bbc5-171">Configure the first domain controller</span></span>

<span data-ttu-id="0bbc5-p106">任意のリモート デスクトップ クライアントを使用して、最初のドメイン コント ローラー仮想マシンへのリモート デスクトップ接続を作成します。イントラネット DNS を使用するか、ローカル管理者アカウントのコンピューター名と資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-p106">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="0bbc5-174">次に、**最初のドメインコントローラー仮想マシン**の Windows PowerShell コマンドプロンプトから、次のコマンドを使用して、最初のドメインコントローラーに追加のデータディスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-174">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="0bbc5-175">次に、最初のドメイン コントローラーから組織ネットワーク上の場所への接続をテストします。テストには、組織ネットワーク上のリソースの名前と IP アドレスを探索する **ping** コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-175">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="0bbc5-p107">この手順により、DNS の名前解決が正常に動作していること (仮想マシンがオンプレミスの DNS サーバーで正しく構成されていること) を確認します。また、クロスプレミスの仮想ネットワークでパケットが送受信できることを確認します。この基本的なテストに失敗した場合は、IT 部門に問い合わせて、DNS の名前解決とパケット配信に関する問題のトラブルシューティングを実施してください。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-p107">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="0bbc5-178">次に、最初のドメイン コントローラーの Windows PowerShell コマンド プロンプトで、次に示すコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-178">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="0bbc5-p108">ドメイン管理者アカウントの資格情報の入力を求めるダイアログが表示されます。コンピューターが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-p108">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="0bbc5-181">2 番目のドメイン コントローラーを構成する</span><span class="sxs-lookup"><span data-stu-id="0bbc5-181">Configure the second domain controller</span></span>

<span data-ttu-id="0bbc5-p109">任意のリモート デスクトップ クライアントを使用して、2 番目のドメイン コント ローラー仮想マシンへのリモート デスクトップ接続を作成します。イントラネット DNS を使用するか、ローカル管理者アカウントのコンピューター名と資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-p109">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="0bbc5-184">次に、 **2 番目のドメインコントローラー仮想マシン**の Windows PowerShell コマンドプロンプトから、次のコマンドを使用して、2番目のドメインコントローラーに追加のデータディスクを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-184">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="0bbc5-185">次に、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-185">Next, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="0bbc5-p110">ドメイン管理者アカウントの資格情報の入力を求めるダイアログが表示されます。コンピューターが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-p110">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
<span data-ttu-id="0bbc5-188">次に、DNS サーバーとして使用する 2 つの新しいドメイン コントローラーの IP アドレスを Azure が仮想マシンに割り当てるように、仮想ネットワークの DNS サーバーを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-188">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers.</span></span> <span data-ttu-id="0bbc5-189">変数にデータを入力し、ローカルコンピューターの Windows PowerShell コマンドプロンプトから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-189">Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
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

$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzVM -ResourceGroupName $adrgName -Name $secondDCName
```

<span data-ttu-id="0bbc5-p112">2 つのドメイン コントローラーを再起動して、これらが DNS サーバーとしてオンプレミスの DNS サーバーで構成されないようにします。これらはいずれも DNS サーバーなので、ドメイン コントローラーに昇格されたときに、自動的に DNS フォワーダーとして、オンプレミスの DNS サーバーで構成されていました。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-p112">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="0bbc5-p113">次に、Active Directory のレプリケーション サイトを作成して、Azure 仮想ネットワークのサーバーがローカル ドメイン コントローラーを使用するようにする必要があります。ドメイン管理者アカウントを使用してどちらかのドメイン コントローラーに接続し、管理者レベルの Windows PowerShell プロンプトから次に示すコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-p113">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-dirsync-server"></a><span data-ttu-id="0bbc5-194">DirSync サーバーを構成する</span><span class="sxs-lookup"><span data-stu-id="0bbc5-194">Configure the DirSync server</span></span>

<span data-ttu-id="0bbc5-195">任意のリモートデスクトップクライアントを使用して、DirSync サーバー仮想マシンへのリモートデスクトップ接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-195">Use the remote desktop client of your choice and create a remote desktop connection to the DirSync server virtual machine.</span></span> <span data-ttu-id="0bbc5-196">イントラネット DNS を使用するか、ローカル管理者アカウントのコンピューター名と資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-196">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="0bbc5-197">次に、Windows PowerShell プロンプトでこれらのコマンドを使用して、適切な AD DS ドメインに参加させます。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-197">Next, join it to the appropriate AD DS domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="0bbc5-198">次に、このフェーズが正常に完了した結果の構成を示します。コンピューター名にはプレース ホルダーを使用しています。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-198">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="0bbc5-199">**フェーズ 2:Azure での高可用性フェデレーション認証インフラストラクチャ用のドメイン コントローラーと DirSync サーバー**</span><span class="sxs-lookup"><span data-stu-id="0bbc5-199">**Phase 2: The domain controllers and DirSync server for your high availability federated authentication infrastructure in Azure**</span></span>

![ドメインコントローラーを含む Azure における高可用性 Office 365 フェデレーション認証インフラストラクチャのフェーズ2](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="0bbc5-201">次の手順</span><span class="sxs-lookup"><span data-stu-id="0bbc5-201">Next step</span></span>

<span data-ttu-id="0bbc5-202">「[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)」を使用して、このワークロードの構成を続行します。</span><span class="sxs-lookup"><span data-stu-id="0bbc5-202">Use [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0bbc5-203">関連項目</span><span class="sxs-lookup"><span data-stu-id="0bbc5-203">See Also</span></span>

[<span data-ttu-id="0bbc5-204">Azure に Office 365 の高可用性フェデレーション認証を展開する</span><span class="sxs-lookup"><span data-stu-id="0bbc5-204">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="0bbc5-205">Office 365 開発/テスト環境のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="0bbc5-205">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="0bbc5-206">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="0bbc5-206">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="0bbc5-207">フェデレーション認証オプション</span><span class="sxs-lookup"><span data-stu-id="0bbc5-207">Federated authentication options</span></span>](about-office-365-identity.md#federated-authentication-options)


