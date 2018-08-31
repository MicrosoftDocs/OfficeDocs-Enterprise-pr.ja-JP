---
title: 高可用性は、認証フェーズ 4 を構成する web アプリケーションのプロキシをフェデレーション
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
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: '概要: は、Microsoft Azure 内の Office 365 のフェデレーション認証を高可用性の web アプリケーションのプロキシ サーバーを構成します。'
ms.openlocfilehash: 0f0299fe8fecdea608330eebc12aea01098f8cec
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915812"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a><span data-ttu-id="9406e-103">高可用性フェデレーション認証のフェーズ 4:Web アプリケーション プロキシを構成する</span><span class="sxs-lookup"><span data-stu-id="9406e-103">High availability federated authentication Phase 4: Configure web application proxies</span></span>

 <span data-ttu-id="9406e-104">**の概要:** Microsoft Azure では、Office 365 のフェデレーション認証の高可用性を実現、web アプリケーションのプロキシ サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="9406e-104">**Summary:** Configure the web application proxy servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="9406e-105">Azure インフラストラクチャ サービスに Office 365 フェデレーション認証の高可用性を展開するために、このフェーズでは、内部ロード バランサーと 2 つの AD FS サーバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="9406e-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="9406e-p101">上に移動する前に、このフェーズを完了する必要があります[高可用性の統合認証フェーズ 5: Office 365 のフェデレーション認証を構成する](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)です。フェーズのすべては、 [Azure で Office 365 の展開の高可用性フェデレーション認証](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9406e-p101">You must complete this phase before moving on to [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a><span data-ttu-id="9406e-108">Azure でインターネット接続ロード バランサーを作成する</span><span class="sxs-lookup"><span data-stu-id="9406e-108">Create the Internet-facing load balancer in Azure</span></span>

<span data-ttu-id="9406e-109">Azure がインターネットからの着信クライアント認証トラフィックを 2 つの Web アプリケーション プロキシ サーバーに均等に分散するように、インターネット接続ロード バランサーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9406e-109">You must create an Internet-facing load balancer so that Azure distributes the incoming client authentication traffic from the Internet evenly among the two web application proxy servers.</span></span>
  
> [!NOTE]
> <span data-ttu-id="9406e-p102">次に示すコマンド セットは、Azure PowerShell の最新版を使用します。「[Azure PowerShell の概要](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9406e-p102">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="9406e-112">場所とリソース グループの値を指定したら、その結果のブロックを Azure PowerShell コマンド プロンプトまたは PowerShell ISE で実行します。</span><span class="sxs-lookup"><span data-stu-id="9406e-112">When you have supplied location and resource group values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="9406e-113">すべての PowerShell コマンドは、この資料で即座に実行の PowerShell コマンド ブロックが、カスタム設定に基づくを生成する Microsoft Excel の構成のブックに含まれているテキスト ファイルを参照してください[Office 365 のフェデレーション認証Azure 展開キット](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)です。</span><span class="sxs-lookup"><span data-stu-id="9406e-113">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzureRmPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzureRmLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzureRMLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzureRMLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzureRMLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="9406e-114">インターネット接続ロード バランサーに割り当てられたパブリック IP アドレスを表示するには、ローカル コンピューターの Azure PowerShell コマンド プロンプトで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9406e-114">To display the public IP address assigned to your Internet-facing load balancer, run these commands at the Azure PowerShell command prompt on your local computer:</span></span>
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a><span data-ttu-id="9406e-115">フェデレーション サービス FQDN を決定してて、DNS レコードを作成する</span><span class="sxs-lookup"><span data-stu-id="9406e-115">Determine your federation service FQDN and create DNS records</span></span>

<span data-ttu-id="9406e-p103">インターネット上でフェデレーション サービス名を識別するには、DNS 名を決定する必要があります。Azure AD Connect は、フェーズ 5 でこの名前を使用して Office 365 を構成します。この名前は、セキュリティ トークンを取得するために Office 365 が接続クライアントに送信する URL の一部になります。たとえば、fs.contoso.com (fs はフェデレーション サービスを表します) です。</span><span class="sxs-lookup"><span data-stu-id="9406e-p103">You need to determine the DNS name to identify your federation service name on the Internet. Azure AD Connect will configure Office 365 with this name in Phase 5, which will become part of the URL that Office 365 sends to connecting clients to get a security token. An example is fs.contoso.com (fs stands for federation service).</span></span>
  
<span data-ttu-id="9406e-119">フェデレーション サービス FDQN を取得後、Azure インターネット接続ロード バランサーのパブリック IP アドレスに解決される、フェデレーション サービス FDQN のパブリック DNS ドメイン A レコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="9406e-119">Once you have your federation service FDQN, create a public DNS domain A record for the federation service FDQN that resolves to the public IP address of the Azure Internet-facing load balancer.</span></span>
  
|<span data-ttu-id="9406e-120">**名前**</span><span class="sxs-lookup"><span data-stu-id="9406e-120">**Name**</span></span>|<span data-ttu-id="9406e-121">**種類**</span><span class="sxs-lookup"><span data-stu-id="9406e-121">**Type**</span></span>|<span data-ttu-id="9406e-122">**TTL**</span><span class="sxs-lookup"><span data-stu-id="9406e-122">**TTL**</span></span>|<span data-ttu-id="9406e-123">**値**</span><span class="sxs-lookup"><span data-stu-id="9406e-123">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="9406e-124">フェデレーション サービス FDQN</span><span class="sxs-lookup"><span data-stu-id="9406e-124">federation service FDQN</span></span>  <br/> |<span data-ttu-id="9406e-125">A</span><span class="sxs-lookup"><span data-stu-id="9406e-125">A</span></span>  <br/> |<span data-ttu-id="9406e-126">3600</span><span class="sxs-lookup"><span data-stu-id="9406e-126">3600</span></span>  <br/> |<span data-ttu-id="9406e-127">Azure インターネット接続ロード バランサーのパブリック IP アドレス (前のセクションの **Write-Host** コマンドで表示されます)</span><span class="sxs-lookup"><span data-stu-id="9406e-127">public IP address of the Azure Internet-facing load balancer (displayed by the **Write-Host** command in the previous section)</span></span> <br/> |
   
<span data-ttu-id="9406e-128">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9406e-128">Here is an example:</span></span>
  
|<span data-ttu-id="9406e-129">**名前**</span><span class="sxs-lookup"><span data-stu-id="9406e-129">**Name**</span></span>|<span data-ttu-id="9406e-130">**種類**</span><span class="sxs-lookup"><span data-stu-id="9406e-130">**Type**</span></span>|<span data-ttu-id="9406e-131">**TTL**</span><span class="sxs-lookup"><span data-stu-id="9406e-131">**TTL**</span></span>|<span data-ttu-id="9406e-132">**値**</span><span class="sxs-lookup"><span data-stu-id="9406e-132">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="9406e-133">fs.contoso.com</span><span class="sxs-lookup"><span data-stu-id="9406e-133">fs.contoso.com</span></span>  <br/> |<span data-ttu-id="9406e-134">A</span><span class="sxs-lookup"><span data-stu-id="9406e-134">A</span></span>  <br/> |<span data-ttu-id="9406e-135">3600</span><span class="sxs-lookup"><span data-stu-id="9406e-135">3600</span></span>  <br/> |<span data-ttu-id="9406e-136">131.107.249.117</span><span class="sxs-lookup"><span data-stu-id="9406e-136">131.107.249.117</span></span>  <br/> |
   
<span data-ttu-id="9406e-137">次に、フェデレーション サービス FQDN を AD FS サーバーの内部ロード バランサーに割り当てられたプライベート IP アドレスに解決する、組織のプライベート DNS 名前空間に DNS アドレス レコードを追加します (「表 I」、「項目 4」、「値」列)。</span><span class="sxs-lookup"><span data-stu-id="9406e-137">Next, add a DNS address record to your organization's private DNS namespace that resolves your federation service FQDN to the private IP address assigned to the internal load balancer for the AD FS servers (Table I, item 4, Value column).</span></span>
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a><span data-ttu-id="9406e-138">Azure に Web アプリケーション プロキシ サーバーの仮想マシンを作成する</span><span class="sxs-lookup"><span data-stu-id="9406e-138">Create the web application proxy server virtual machines in Azure</span></span>

<span data-ttu-id="9406e-139">次に示す Azure PowerShell コマンドのブロックを使用して、2 つの Web アプリケーション プロキシ サーバーの仮想マシンを作成します。 </span><span class="sxs-lookup"><span data-stu-id="9406e-139">Use the following block of Azure PowerShell commands to create the virtual machines for the two web application proxy servers.</span></span> 
  
<span data-ttu-id="9406e-140">次に示す Azure PowerShell コマンド セットには、次の表の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="9406e-140">Note that the following Azure PowerShell command sets use values from the following tables:</span></span>
  
- <span data-ttu-id="9406e-141">表 M: 仮想マシン用</span><span class="sxs-lookup"><span data-stu-id="9406e-141">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="9406e-142">表 R: リソース グループ用</span><span class="sxs-lookup"><span data-stu-id="9406e-142">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="9406e-143">表 V: 仮想ネットワークの設定用</span><span class="sxs-lookup"><span data-stu-id="9406e-143">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="9406e-144">表 S: サブネット用</span><span class="sxs-lookup"><span data-stu-id="9406e-144">Table S, for your subnets</span></span>
    
- <span data-ttu-id="9406e-145">表 I: 静的 IP アドレス用</span><span class="sxs-lookup"><span data-stu-id="9406e-145">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="9406e-146">表 A: 可用性セット用</span><span class="sxs-lookup"><span data-stu-id="9406e-146">Table A, for your availability sets</span></span>
    
<span data-ttu-id="9406e-147">テーブル M が定義されていることを思い出して[高可用性の統合認証フェーズ 2: ドメイン コント ローラーを構成する](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)とテーブル R、V、S、I、および A で[の高可用性の統合認証フェーズ 1: Azure の構成](high-availability-federated-authentication-phase-1-configure-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="9406e-147">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
<span data-ttu-id="9406e-148">適切な値をすべて指定したら、その結果のブロックを Azure PowerShell コマンド プロンプトまたは PowerShell ISE で実行します。</span><span class="sxs-lookup"><span data-stu-id="9406e-148">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzureRMVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="9406e-p104">これらの仮想マシンはイントラネット アプリケーション向けのため、パブリック IP アドレスや DNS ドメイン名のラベルが割り当てられていません。また、インターネットに公開もされていません。ただし、これは Azure ポータルから接続できないことを意味します。仮想マシンのプロパティを表示したときに、**接続**オプションは使用できない状態になります。リモート デスクトップ接続アクセサリなどのリモート デスクトップ ツールを使用して、仮想マシンのプライベート IP アドレスやイントラネット DNS 名、ローカル管理者アカウントの資格情報で仮想マシンに接続します。</span><span class="sxs-lookup"><span data-stu-id="9406e-p104">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="9406e-153">次に、このフェーズが正常に完了した結果の構成を示します。コンピューター名にはプレース ホルダーを使用しています。</span><span class="sxs-lookup"><span data-stu-id="9406e-153">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="9406e-154">**フェーズ 4:Azure での高可用性フェデレーション認証インフラストラクチャ用のインターネット接続ロード バランサーと Web アプリケーション プロキシ サーバー**</span><span class="sxs-lookup"><span data-stu-id="9406e-154">**Phase 4: The Internet-facing load balancer and web application proxy servers for your high availability federated authentication infrastructure in Azure**</span></span>

![Web アプリケーション プロキシ サーバーによる Azure での高可用性 Office 365 フェデレーション認証のフェーズ 4](media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a><span data-ttu-id="9406e-156">次の手順</span><span class="sxs-lookup"><span data-stu-id="9406e-156">Next step</span></span>

<span data-ttu-id="9406e-157">「[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)」を使用して、このワークロードの構成を続行します。</span><span class="sxs-lookup"><span data-stu-id="9406e-157">Use [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9406e-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="9406e-158">See Also</span></span>

[<span data-ttu-id="9406e-159">Azure に Office 365 の高可用性フェデレーション認証を展開する</span><span class="sxs-lookup"><span data-stu-id="9406e-159">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="9406e-160">Office 365 開発/テスト環境のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="9406e-160">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="9406e-161">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="9406e-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="9406e-162">フェデレーションの認証オプション</span><span class="sxs-lookup"><span data-stu-id="9406e-162">Federated authentication options</span></span>](about-office-365-identity.md#federated-authentication-options)


