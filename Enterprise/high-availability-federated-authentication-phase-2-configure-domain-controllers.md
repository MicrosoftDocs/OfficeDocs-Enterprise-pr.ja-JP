---
title: "高可用性の統合認証のフェーズ 2 を構成するドメイン コント ローラー"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: "概要: は、Microsoft Azure 内のドメイン コント ローラーと高可用性のフェデレーション認証が Office 365 のディレクトリ同期サーバーを構成します。"
ms.openlocfilehash: 5e2cc8b5c750b5b2cf48ff0c594a5bd716d5bcf2
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="33f47-103">高可用性フェデレーション認証のフェーズ 2:ドメイン コントローラーを構成する</span><span class="sxs-lookup"><span data-stu-id="33f47-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

 <span data-ttu-id="33f47-104">**の概要:**Microsoft Azure では、ドメイン コント ローラーと高可用性のフェデレーション認証が Office 365 のディレクトリ同期サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="33f47-104">**Summary:** Configure the domain controllers and DirSync server for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="33f47-p101">Azure インフラストラクチャ サービスに Office 365 フェデレーション認証の高可用性を展開するために、このフェーズでは、Azure の仮想ネットワークに 2 つのドメイン コントローラーと 1 つの DirSync サーバーを構成します。オンプレミス ネットワークへのサイト間 VPN 接続を経由して認証トラフィックを送信するのではなく、Azure 仮想ネットワーク内で認証に対するクライアント Web 要求を認証できます。</span><span class="sxs-lookup"><span data-stu-id="33f47-p101">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the DirSync server in the Azure virtual network. Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="33f47-107">Active Directory フェデレーション サービス (AD FS) では、Windows Server AD ドメイン コントローラーの代用として、Azure Active Directory Domain Services を使用できません。</span><span class="sxs-lookup"><span data-stu-id="33f47-107">Active Directory Federation Services (AD FS) cannot use Azure Active Directory Domain Services as a substitute for Windows Server AD domain controllers.</span></span> 
  
<span data-ttu-id="33f47-p102">上に移動する前に、このフェーズを完了する必要があります[高可用性の統合認証フェーズ 3: AD FS サーバーを構成する](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)です。フェーズのすべては、 [Azure で Office 365 の展開の高可用性フェデレーション認証](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33f47-p102">You must complete this phase before moving on to [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="33f47-110">Azure にドメイン コントローラー仮想マシンを作成する</span><span class="sxs-lookup"><span data-stu-id="33f47-110">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="33f47-111">まず、テーブル M の**仮想マシンの名前**] 列に入力し、[**最小サイズ**] 列で、必要に応じて仮想マシンのサイズを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33f47-111">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="33f47-112">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="33f47-112">**Item**</span></span>|<span data-ttu-id="33f47-113">**バーチャル マシンの名前**</span><span class="sxs-lookup"><span data-stu-id="33f47-113">**Virtual machine name**</span></span>|<span data-ttu-id="33f47-114">**ギャラリーの画像**</span><span class="sxs-lookup"><span data-stu-id="33f47-114">**Gallery image**</span></span>|<span data-ttu-id="33f47-115">**記憶域の種類**</span><span class="sxs-lookup"><span data-stu-id="33f47-115">**Storage type**</span></span>|<span data-ttu-id="33f47-116">**最小サイズ**</span><span class="sxs-lookup"><span data-stu-id="33f47-116">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="33f47-117">1.</span><span class="sxs-lookup"><span data-stu-id="33f47-117">1.</span></span>  <br/> |<span data-ttu-id="33f47-118">______________ (最初のドメイン コントローラー。例: DC1)</span><span class="sxs-lookup"><span data-stu-id="33f47-118">______________ (first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="33f47-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="33f47-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="33f47-120">StandardLRS</span><span class="sxs-lookup"><span data-stu-id="33f47-120">StandardLRS</span></span>  <br/> |<span data-ttu-id="33f47-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="33f47-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="33f47-122">2.</span><span class="sxs-lookup"><span data-stu-id="33f47-122">2.</span></span>  <br/> |<span data-ttu-id="33f47-123">______________ (2 番目のドメイン コントローラー。例: DC2)</span><span class="sxs-lookup"><span data-stu-id="33f47-123">______________ (second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="33f47-124">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="33f47-124">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="33f47-125">StandardLRS</span><span class="sxs-lookup"><span data-stu-id="33f47-125">StandardLRS</span></span>  <br/> |<span data-ttu-id="33f47-126">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="33f47-126">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="33f47-127">3.</span><span class="sxs-lookup"><span data-stu-id="33f47-127">3.</span></span>  <br/> |<span data-ttu-id="33f47-128">______________ (DirSync サーバー。例: DS1)</span><span class="sxs-lookup"><span data-stu-id="33f47-128">______________ (DirSync server, example DS1)</span></span>  <br/> |<span data-ttu-id="33f47-129">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="33f47-129">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="33f47-130">StandardLRS</span><span class="sxs-lookup"><span data-stu-id="33f47-130">StandardLRS</span></span>  <br/> |<span data-ttu-id="33f47-131">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="33f47-131">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="33f47-132">4.</span><span class="sxs-lookup"><span data-stu-id="33f47-132">4.</span></span>  <br/> |<span data-ttu-id="33f47-133">______________ (最初の AD FS サーバー。例: ADFS1)</span><span class="sxs-lookup"><span data-stu-id="33f47-133">______________ (first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="33f47-134">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="33f47-134">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="33f47-135">StandardLRS</span><span class="sxs-lookup"><span data-stu-id="33f47-135">StandardLRS</span></span>  <br/> |<span data-ttu-id="33f47-136">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="33f47-136">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="33f47-137">5.</span><span class="sxs-lookup"><span data-stu-id="33f47-137">5.</span></span>  <br/> |<span data-ttu-id="33f47-138">______________ (2 番目の AD FS サーバー。例: ADFS2)</span><span class="sxs-lookup"><span data-stu-id="33f47-138">______________ (second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="33f47-139">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="33f47-139">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="33f47-140">StandardLRS</span><span class="sxs-lookup"><span data-stu-id="33f47-140">StandardLRS</span></span>  <br/> |<span data-ttu-id="33f47-141">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="33f47-141">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="33f47-142">6.</span><span class="sxs-lookup"><span data-stu-id="33f47-142">6.</span></span>  <br/> |<span data-ttu-id="33f47-143">______________ (最初の Web アプリケーション プロキシ サーバー。例: WEB1)</span><span class="sxs-lookup"><span data-stu-id="33f47-143">______________ (first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="33f47-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="33f47-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="33f47-145">StandardLRS</span><span class="sxs-lookup"><span data-stu-id="33f47-145">StandardLRS</span></span>  <br/> |<span data-ttu-id="33f47-146">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="33f47-146">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="33f47-147">7.</span><span class="sxs-lookup"><span data-stu-id="33f47-147">7.</span></span>  <br/> |<span data-ttu-id="33f47-148">______________ (2 番目の Web アプリケーション プロキシ サーバー。例: WEB2)</span><span class="sxs-lookup"><span data-stu-id="33f47-148">______________ (second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="33f47-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="33f47-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="33f47-150">StandardLRS</span><span class="sxs-lookup"><span data-stu-id="33f47-150">StandardLRS</span></span>  <br/> |<span data-ttu-id="33f47-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="33f47-151">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="33f47-152">**M - Azure 内の Office 365 の高可用性のフェデレーション認証のための仮想マシンの表**</span><span class="sxs-lookup"><span data-stu-id="33f47-152">**Table M - Virtual machines for the high availability federated authentication for Office 365 in Azure**</span></span>
  
<span data-ttu-id="33f47-153">、仮想マシンのサイズの完全な一覧は、[仮想マシンのサイズ](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33f47-153">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="33f47-p103">Azure PowerShell の次のコマンド ブロックでは、2 つのドメイン コント ローラーの仮想マシンを作成します。削除して、変数の値を指定します\<と > の文字。Azure の PowerShell コマンド ブロックが次のテーブルから値を使用することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="33f47-p103">The following Azure PowerShell command block creates the virtual machines for the two domain controllers. Specify the values for the variables, removing the \< and > characters. Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="33f47-157">表 M: 仮想マシン用</span><span class="sxs-lookup"><span data-stu-id="33f47-157">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="33f47-158">表 R: リソース グループ用</span><span class="sxs-lookup"><span data-stu-id="33f47-158">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="33f47-159">表 V: 仮想ネットワークの設定用</span><span class="sxs-lookup"><span data-stu-id="33f47-159">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="33f47-160">表 S: サブネット用</span><span class="sxs-lookup"><span data-stu-id="33f47-160">Table S, for your subnets</span></span>
    
- <span data-ttu-id="33f47-161">表 I: 静的 IP アドレス用</span><span class="sxs-lookup"><span data-stu-id="33f47-161">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="33f47-162">表 A: 可用性セット用</span><span class="sxs-lookup"><span data-stu-id="33f47-162">Table A, for your availability sets</span></span>
    
<span data-ttu-id="33f47-163">テーブル R、V、S、I、および A で定義したことを思い出して[高可用性の統合認証フェーズ 1: 構成の Azure](high-availability-federated-authentication-phase-1-configure-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="33f47-163">Recall that you defined Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="33f47-p104">次のコマンド セットは、Azure の PowerShell の最新バージョンを使用します。[Azure の PowerShell コマンドレットの入門](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33f47-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="33f47-166">すべてに適切な値を指定したら、その結果のブロックを Azure PowerShell プロンプト、またはローカル コンピューターの PowerShell 統合スクリプト環境 (ISE) で実行します。</span><span class="sxs-lookup"><span data-stu-id="33f47-166">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
> [!TIP]
> <span data-ttu-id="33f47-167">すべての PowerShell コマンドは、この資料で即座に実行の PowerShell コマンド ブロックが、カスタム設定に基づくを生成する Microsoft Excel の構成のブックに含まれているテキスト ファイルを参照してください[Office 365 のフェデレーション認証Azure 展開キット](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)です。</span><span class="sxs-lookup"><span data-stu-id="33f47-167">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
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
> <span data-ttu-id="33f47-p105">これらの仮想マシンは、イントラネット アプリケーションには、ためいないパブリック IP アドレスまたは DNS ドメイン名のラベルが割り当てられているそしてインターネットに公開します。ただし、つまり、Azure ポータルからのそれらに接続できません。仮想マシンのプロパティを表示するときは、[**接続**] オプションは使用できません。プライベート IP アドレスまたはイントラネット DNS 名を使用して仮想マシンに接続するリモート デスクトップ接続の付属品、または別のリモート デスクトップ ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="33f47-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="33f47-172">最初のドメイン コントローラーを構成する</span><span class="sxs-lookup"><span data-stu-id="33f47-172">Configure the first domain controller</span></span>

<span data-ttu-id="33f47-p106">任意のリモート デスクトップ クライアントを使用して、最初のドメイン コント ローラー仮想マシンへのリモート デスクトップ接続を作成します。イントラネット DNS を使用するか、ローカル管理者アカウントのコンピューター名と資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="33f47-p106">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="33f47-175">このコマンドを使用して最初のドメイン コント ローラーに、Windows PowerShell コマンド プロンプト**で最初のドメイン コント ローラー仮想マシン**から、次に、余分なデータ ディスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="33f47-175">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="33f47-176">次に、名前と組織のネットワーク上のリソースの IP アドレスに対して ping を実行するのには、 **ping**コマンドを使用して、組織のネットワーク上の場所への最初のドメイン コント ローラーの接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="33f47-176">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="33f47-p107">この手順により、DNS の名前解決が正常に動作していること (仮想マシンがオンプレミスの DNS サーバーで正しく構成されていること) を確認します。また、クロスプレミスの仮想ネットワークでパケットが送受信できることを確認します。この基本的なテストに失敗した場合は、IT 部門に問い合わせて、DNS の名前解決とパケット配信に関する問題のトラブルシューティングを実施してください。</span><span class="sxs-lookup"><span data-stu-id="33f47-p107">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="33f47-179">次に、最初のドメイン コントローラーの Windows PowerShell コマンド プロンプトで、次に示すコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="33f47-179">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs" -Credential $cred
```

<span data-ttu-id="33f47-p108">ドメイン管理者アカウントの資格情報の入力を求めるダイアログが表示されます。コンピューターが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="33f47-p108">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="33f47-182">2 番目のドメイン コントローラーを構成する</span><span class="sxs-lookup"><span data-stu-id="33f47-182">Configure the second domain controller</span></span>

<span data-ttu-id="33f47-p109">任意のリモート デスクトップ クライアントを使用して、2 番目のドメイン コント ローラー仮想マシンへのリモート デスクトップ接続を作成します。イントラネット DNS を使用するか、ローカル管理者アカウントのコンピューター名と資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="33f47-p109">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="33f47-185">次に、余分なデータ ディスクを Windows PowerShell コマンド プロンプト**で 2 番目のドメイン コント ローラー仮想マシン**からこのコマンドを使用して 2 つ目のドメイン コント ローラーに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33f47-185">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="33f47-186">次に、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="33f47-186">Next, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs" -Credential $cred

```

<span data-ttu-id="33f47-p110">ドメイン管理者アカウントの資格情報の入力を求めるダイアログが表示されます。コンピューターが再起動されます。</span><span class="sxs-lookup"><span data-stu-id="33f47-p110">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
<span data-ttu-id="33f47-p111">次に、その Azure に仮想マシンの DNS サーバーとして使用する新しい 2 つのドメイン コント ローラーの IP アドレスが割り当てられますので、仮想ネットワークの DNS サーバーを更新する必要があります。変数を入力し、ローカル コンピューター上の Windows PowerShell コマンド プロンプトからこれらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="33f47-p111">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers. Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
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

<span data-ttu-id="33f47-p112">2 つのドメイン コントローラーを再起動して、これらが DNS サーバーとしてオンプレミスの DNS サーバーで構成されないようにします。これらはいずれも DNS サーバーなので、ドメイン コントローラーに昇格されたときに、自動的に DNS フォワーダーとして、オンプレミスの DNS サーバーで構成されていました。</span><span class="sxs-lookup"><span data-stu-id="33f47-p112">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="33f47-p113">次に、Active Directory のレプリケーション サイトを作成して、Azure 仮想ネットワークのサーバーがローカル ドメイン コントローラーを使用するようにする必要があります。ドメイン管理者アカウントを使用してどちらかのドメイン コントローラーに接続し、管理者レベルの Windows PowerShell プロンプトから次に示すコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="33f47-p113">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-dirsync-server"></a><span data-ttu-id="33f47-195">DirSync サーバーを構成する</span><span class="sxs-lookup"><span data-stu-id="33f47-195">Configure the DirSync server</span></span>

<span data-ttu-id="33f47-p114">任意のリモート デスクトップ クライアントを使用し、ディレクトリ同期サーバーの仮想マシンへのリモート デスクトップ接続を作成します。そのイントラネット DNS 名またはコンピューター名、ローカルの管理者アカウントの資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="33f47-p114">Use the remote desktop client of your choice and create a remote desktop connection to the DirSync server virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="33f47-198">次に、Windows PowerShell プロンプトでこれらのコマンドを使用して、適切な Windows Server AD ドメインに参加させます。</span><span class="sxs-lookup"><span data-stu-id="33f47-198">Next, join it to the appropriate Windows Server AD domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="33f47-199">次に、このフェーズが正常に完了した結果の構成を示します。コンピューター名にはプレース ホルダーを使用しています。</span><span class="sxs-lookup"><span data-stu-id="33f47-199">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="33f47-200">**フェーズ 2: ドメイン コント ローラーと Azure で、高可用性の統合認証インフラストラクチャのディレクトリ同期サーバー**</span><span class="sxs-lookup"><span data-stu-id="33f47-200">**Phase 2: The domain controllers and DirSync server for your high availability federated authentication infrastructure in Azure**</span></span>

![ドメイン コントローラーによる Azure での高可用性 Office 365 フェデレーション認証のフェーズ 2](images/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="33f47-202">次の手順</span><span class="sxs-lookup"><span data-stu-id="33f47-202">Next step</span></span>

<span data-ttu-id="33f47-203">使用[高可用性の統合認証フェーズ 3: AD FS サーバーを構成する](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)この作業負荷の構成を続行します。</span><span class="sxs-lookup"><span data-stu-id="33f47-203">Use [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="33f47-204">関連項目</span><span class="sxs-lookup"><span data-stu-id="33f47-204">See Also</span></span>

[<span data-ttu-id="33f47-205">Azure に Office 365 の高可用性フェデレーション認証を展開する</span><span class="sxs-lookup"><span data-stu-id="33f47-205">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="33f47-206">Office 365 開発/テスト環境のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="33f47-206">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="33f47-207">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="33f47-207">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="33f47-208">Office 365 のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="33f47-208">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


