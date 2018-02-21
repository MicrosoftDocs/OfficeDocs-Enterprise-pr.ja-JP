---
title: "基本構成開発/テスト環境"
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
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: "概要: は、Microsoft Azure で開発/テスト環境として、簡略化されたイントラネットを作成します。"
ms.openlocfilehash: 04da1037dbebed9f9a5d2aa2fb37b03b88218839
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2018
---
# <a name="base-configuration-devtest-environment"></a><span data-ttu-id="059b1-103">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="059b1-103">Base Configuration dev/test environment</span></span>

 <span data-ttu-id="059b1-104">**の概要:**Microsoft Azure で開発/テスト環境としては、簡略化されたイントラネットを作成します。</span><span class="sxs-lookup"><span data-stu-id="059b1-104">**Summary:** Create a simplified intranet as a dev/test environment in Microsoft Azure.</span></span>
  
<span data-ttu-id="059b1-105">この記事では、Azure で次の基本構成開発/テスト環境を作成するための詳しい手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="059b1-105">This article provides you with step-by-step instructions to create the following Base Configuration dev/test environment in Azure:</span></span>
  
<span data-ttu-id="059b1-106">**図 1: 基本構成の開発/テスト環境**</span><span class="sxs-lookup"><span data-stu-id="059b1-106">**Figure 1: The Base Configuration dev/test environment**</span></span>

![CLIENT1 仮想マシンを含む Azure のフェーズ 4 基本構成](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="059b1-p101">図 1 の基本構成開発/テスト環境は、インターネットに接続された簡略化されたプライベート イントラネットをシミュレートする、TestLab というクラウド専用 Azure 仮想ネットワーク内の企業ネットワーク サブネットで構成されています。Windows Server 2016 を実行している次の 3 つの Azure 仮想マシンが含まれます。</span><span class="sxs-lookup"><span data-stu-id="059b1-p101">The Base Configuration dev/test environment in Figure 1 consists of the Corpnet subnet in a cloud-only Azure virtual network named TestLab that simulates a simplified, private intranet connected to the Internet. It contains three Azure virtual machines running Windows Server 2016:</span></span>
  
- <span data-ttu-id="059b1-110">イントラネット ドメイン コントローラーとドメイン ネーム システム (DNS) サーバーとして構成されている DC1</span><span class="sxs-lookup"><span data-stu-id="059b1-110">DC1 is configured as an intranet domain controller and Domain Name System (DNS) server</span></span>
    
- <span data-ttu-id="059b1-111">一般的なアプリケーションおよび Web サーバーとして構成されている APP1</span><span class="sxs-lookup"><span data-stu-id="059b1-111">APP1 is configured as a general application and web server</span></span>
    
- <span data-ttu-id="059b1-112">	イントラネット クライアントとして動作する CLIENT1</span><span class="sxs-lookup"><span data-stu-id="059b1-112">CLIENT1 acts as an intranet client</span></span>
    
<span data-ttu-id="059b1-113">この構成では、DC1、APP1、CLIENT1、他の企業ネットワークのサブネットのコンピューターを、次のようにできます。 </span><span class="sxs-lookup"><span data-stu-id="059b1-113">This configuration allows DC1, APP1, CLIENT1, and additional Corpnet subnet computers to be:</span></span> 
  
- <span data-ttu-id="059b1-114">更新プログラムをインストールするのにはインターネットに接続されているをリアルタイムに、インターネット リソースにアクセスし、Microsoft Office 365 とその他の Azure のサービスなどのパブリック クラウド テクノロジに参加します。</span><span class="sxs-lookup"><span data-stu-id="059b1-114">Connected to the Internet to install updates, access Internet resources in real time, and participate in public cloud technologies such as Microsoft Office 365 and other Azure services.</span></span>
    
- <span data-ttu-id="059b1-115">	インターネットや組織のネットワークに接続されているコンピューターから、リモート デスクトップ接続を使用してリモートで管理する。</span><span class="sxs-lookup"><span data-stu-id="059b1-115">Remotely managed using Remote Desktop connections from your computer that is connected to the Internet or your organization network.</span></span>
    
<span data-ttu-id="059b1-116">作成したテスト環境を、次の目的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="059b1-116">You can use the resulting test environment:</span></span>
  
- <span data-ttu-id="059b1-117">アプリケーション開発とテスト。</span><span class="sxs-lookup"><span data-stu-id="059b1-117">For application development and testing.</span></span>
    
- <span data-ttu-id="059b1-118">独自設計の拡張されたテスト環境の初期構成としては、追加の仮想マシン、Azure のサービス、またはその他のマイクロソフトのクラウド サービス Office 365 およびエンタープライズ セキュリティ + 移動などを含みます。</span><span class="sxs-lookup"><span data-stu-id="059b1-118">As the initial configuration of an extended test environment of your own design that includes additional virtual machines, Azure services, or other Microsoft cloud offerings such as Office 365 and Enterprise Security + Mobility.</span></span>
    
<span data-ttu-id="059b1-119">Azure の基本構成テスト環境の設定には次の 4 つのフェーズがあります。</span><span class="sxs-lookup"><span data-stu-id="059b1-119">There are four phases to setting up the Base Configuration test environment in Azure:</span></span>
  
1. <span data-ttu-id="059b1-120">	仮想ネットワークを作成します。</span><span class="sxs-lookup"><span data-stu-id="059b1-120">Create the virtual network.</span></span>
    
2. <span data-ttu-id="059b1-121">	DC1 を構成します。</span><span class="sxs-lookup"><span data-stu-id="059b1-121">Configure DC1.</span></span>
    
3. <span data-ttu-id="059b1-122">	APP1 を構成します。</span><span class="sxs-lookup"><span data-stu-id="059b1-122">Configure APP1.</span></span>
    
4. <span data-ttu-id="059b1-123">	CLIENT1 を構成します。</span><span class="sxs-lookup"><span data-stu-id="059b1-123">Configure CLIENT1.</span></span>
    
<span data-ttu-id="059b1-p102">Azure サブスクリプションがあるない場合[と Azure](https://azure.microsoft.com/pricing/free-trial/)の無料試用版にサインアップすることができます。MSDN または Visual Studio のサブスクリプションがある場合は、 [Visual Studio のサブスクライバーに対して毎月 Azure のクレジット](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="059b1-p102">If you do not already have an Azure subscription, you can sign up for a free trial at [Try Azure](https://azure.microsoft.com/pricing/free-trial/). If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="059b1-p103">Azure の仮想マシンでは、実行されている場合に、継続的な金銭的コストが発生します。このコストは無料試用版を MSDN サブスクリプションに対して請求されるか、またはサブスクリプションを支払います。Azure の仮想マシンを実行しているの詳細については、コストは、[仮想マシンの価格設定の詳細](https://azure.microsoft.com/pricing/details/virtual-machines/)と[Azure の価格の計算](https://azure.microsoft.com/pricing/calculator/)を参照してください。コスト削減を維持、 [Azure でテスト環境の仮想マシンのコストを最小限に抑えること](base-configuration-dev-test-environment.md#mincost)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="059b1-p103">Virtual machines in Azure incur an ongoing monetary cost when they are running. This cost is billed against your free trial, MSDN subscription, or paid subscription. For more information about the costs of running Azure virtual machines, see [Virtual Machines Pricing Details](https://azure.microsoft.com/pricing/details/virtual-machines/) and [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/). To keep costs down, see [Minimizing the costs of test environment virtual machines in Azure](base-configuration-dev-test-environment.md#mincost).</span></span> 
  
![Microsoft Cloud のテスト ラボ ガイド](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="059b1-131">
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="059b1-131">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-virtual-network"></a><span data-ttu-id="059b1-132">フェーズ 1: 仮想ネットワークを作成する</span><span class="sxs-lookup"><span data-stu-id="059b1-132">Phase 1: Create the virtual network</span></span>

<span data-ttu-id="059b1-133">最初に、Azure PowerShell プロンプトを起動します。</span><span class="sxs-lookup"><span data-stu-id="059b1-133">First, start an Azure PowerShell prompt.</span></span>
  
> [!NOTE]
> <span data-ttu-id="059b1-p104">次のコマンド セットは、Azure の PowerShell の最新バージョンを使用します。[Azure の PowerShell コマンドレットの入門](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="059b1-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="059b1-136">次のコマンドを使用して Azure アカウントにログインします。</span><span class="sxs-lookup"><span data-stu-id="059b1-136">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="059b1-137">クリックして[ここでは](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d)この資料ですべての PowerShell コマンドを含むテキスト ファイルを取得します。</span><span class="sxs-lookup"><span data-stu-id="059b1-137">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="059b1-138">次のコマンドを使用して、サブスクリプションの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="059b1-138">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="059b1-p105">Azure サブスクリプションを設定します。二重引用符内のすべて (「<」と「>」の文字を含む) を正しい名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="059b1-p105">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="059b1-p106">次に、基本構成テスト ラボ用の新しいリソース グループを作成します。一意のリソース グループ名を特定するには、このコマンドを使用して既存のリソース グループを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="059b1-p106">Next, create a new resource group for your Base Configuration test lab. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="059b1-p107">これらのコマンドを使用して、新しいリソース グループを作成します。二重引用符内のすべて (< 文字と > 文字を含む) を正しい名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="059b1-p107">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="059b1-145">次に、基本構成の企業ネットワークのサブネットをホストする TestLab 仮想ネットワークを作成し、ネットワーク セキュリティ グループで保護します。</span><span class="sxs-lookup"><span data-stu-id="059b1-145">Next, you create the TestLab virtual network that will host the Corpnet subnet of the base configuration and protect it with a network security group.</span></span>
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
```

<span data-ttu-id="059b1-146">これは、現在の構成です。</span><span class="sxs-lookup"><span data-stu-id="059b1-146">This is your current configuration.</span></span>
  
![仮想ネットワークとサブネットを含む Azure のフェーズ 1 基本構成](images/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
## <a name="phase-2-configure-dc1"></a><span data-ttu-id="059b1-148">フェーズ 2:DC1 を構成する</span><span class="sxs-lookup"><span data-stu-id="059b1-148">Phase 2: Configure DC1</span></span>

<span data-ttu-id="059b1-149">このフェーズでは、DC1 仮想マシンを作成し、それを Windows Server Active Directory (AD) の corp.contoso.comis ドメインのドメイン コントローラー、および TestLab 仮想ネットワークの仮想マシン用の DNS サーバーとして構成します。</span><span class="sxs-lookup"><span data-stu-id="059b1-149">In this phase, we create the DC1 virtual machine and configure it as a domain controller for the corp.contoso.com Windows Server Active Directory (AD) domain and a DNS server for the virtual machines of the TestLab virtual network.</span></span>
  
<span data-ttu-id="059b1-150">DC1 用には、Azure の仮想マシンを作成するに、リソース グループの名前を入力し、Azure の PowerShell コマンド プロンプトで、ローカル コンピューターでこれらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="059b1-150">To create an Azure virtual machine for DC1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzureRMVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "StandardLRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="059b1-p108">DC1 のローカル管理者アカウントのユーザー名とパスワードを入力するようダイアログが表示されます。強力なパスワードを使用して、安全な場所に名前とパスワードの両方を記録します。</span><span class="sxs-lookup"><span data-stu-id="059b1-p108">You will be prompted for a user name and password for the local administrator account on DC1. Use a strong password and record both the name and password in a secure location.</span></span>
  
<span data-ttu-id="059b1-153">次に、DC1 仮想マシンに接続します。</span><span class="sxs-lookup"><span data-stu-id="059b1-153">Next, connect to the DC1 virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-local-administrator-account-credentials"></a><span data-ttu-id="059b1-154">ローカルの管理者アカウントの資格情報を使用して DC1 に接続する</span><span class="sxs-lookup"><span data-stu-id="059b1-154">Connect to DC1 using local administrator account credentials</span></span>

1. <span data-ttu-id="059b1-155">[Azure ポータル](https://portal.azure.com)をクリックして**リソース グループ >** <the name of your new resource group> **> DC1 > 接続**。</span><span class="sxs-lookup"><span data-stu-id="059b1-155">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** <the name of your new resource group> **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="059b1-156">、ダウンロードした DC1.rdp ファイルを開くし、[**接続**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="059b1-156">Open the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="059b1-157">DC1 のローカル管理者のアカウント名を指定します。</span><span class="sxs-lookup"><span data-stu-id="059b1-157">Specify the DC1 local administrator account name:</span></span>
    
  - <span data-ttu-id="059b1-158">Windows 7 の場合:</span><span class="sxs-lookup"><span data-stu-id="059b1-158">For Windows 7:</span></span>
    
    <span data-ttu-id="059b1-p109">**Windows セキュリティ**] ダイアログ ボックスで**別のアカウントを使用**] をクリックします。[**ユーザー名**を入力**DC1\\**[ローカルの管理者アカウントの名前]。</span><span class="sxs-lookup"><span data-stu-id="059b1-p109">In the **Windows Security** dialog box, click **Use another account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
  - <span data-ttu-id="059b1-161">Windows 8 または Windows 10 の場合:</span><span class="sxs-lookup"><span data-stu-id="059b1-161">For Windows 8 or Windows 10:</span></span>
    
    <span data-ttu-id="059b1-p110">**Windows セキュリティ**] ダイアログ ボックスでは**より多くの選択肢**をクリックし、**別のアカウントを使用**] をクリックします。[**ユーザー名**を入力**DC1\\**[ローカルの管理者アカウントの名前]。</span><span class="sxs-lookup"><span data-stu-id="059b1-p110">In the **Windows Security** dialog box, click **More choices**, and then click **Use a different account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="059b1-164">[**パスワード**] に、ローカル管理者アカウントのパスワードを入力し、し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="059b1-164">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="059b1-165">ダイアログ ボックスが表示されたら、[**はい**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="059b1-165">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="059b1-166">次に、DC1 上で管理者レベルの Windows PowerShell コマンド プロンプトで次のコマンドでドライブ文字 f: を持つ新しいボリュームとして、余分なデータ ディスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="059b1-166">Next, add an extra data disk as a new volume with the drive letter F: with this command at an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="059b1-p111">次に corp.contoso.com ドメインのドメイン コントローラーおよび DNS サーバーとして DC1 を構成します。管理者レベルの Windows PowerShell コマンド プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="059b1-p111">Next, configure DC1 as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs"
```

<span data-ttu-id="059b1-p112">セーフ モードの管理者パスワードを指定する必要があります。パスワードを安全な場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="059b1-p112">You will need to specify a safe mode administrator password. Store this password in a secure location.</span></span>
  
<span data-ttu-id="059b1-171">これらのコマンドの完了には数分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="059b1-171">Note that these commands can take a few minutes to complete.</span></span>
  
<span data-ttu-id="059b1-172">DC1 の再起動後に、DC1 仮想マシンに再接続します。</span><span class="sxs-lookup"><span data-stu-id="059b1-172">After DC1 restarts, reconnect to the DC1 virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-domain-credentials"></a><span data-ttu-id="059b1-173">ドメインの資格情報を使用して DC1 に接続する</span><span class="sxs-lookup"><span data-stu-id="059b1-173">Connect to DC1 using domain credentials</span></span>

1. <span data-ttu-id="059b1-174">[Azure ポータル](https://portal.azure.com)をクリックして**リソース グループ >** <your resource group name> **> DC1 > 接続**。</span><span class="sxs-lookup"><span data-stu-id="059b1-174">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** <your resource group name> **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="059b1-175">、ダウンロードした DC1.rdp ファイルを実行し、[**接続**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="059b1-175">Run the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="059b1-p113">**Windows セキュリティ**] で、**別のアカウントを使用して**をクリックします。[**ユーザー名**を入力**株式会社\\**[ローカルの管理者アカウントの名前]。</span><span class="sxs-lookup"><span data-stu-id="059b1-p113">In **Windows Security**, click **Use another account**. In **User name**, type **CORP\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="059b1-178">[**パスワード**] に、ローカル管理者アカウントのパスワードを入力し、し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="059b1-178">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="059b1-179">ダイアログ ボックスが表示されたら、[**はい**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="059b1-179">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="059b1-p114">次に、CORP ドメイン メンバー コンピューターにログインするときに使用する、Active Directory のユーザー アカウントを作成します。管理者レベルの Windows PowerShell コマンド プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="059b1-p114">Next, create a user account in Active Directory that will be used when logging in to CORP domain member computers. Run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="059b1-p115">このコマンドでは、User1 アカウントのパスワードを入力するよう求められることに注意してください。このアカウントは、すべての CORP ドメイン メンバー コンピューターのリモート デスクトップ接続に使用するため、強力なパスワードを選択してください。User1 アカウントのパスワードを記録し、セキュリティで保護された場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="059b1-p115">Note that this command prompts you to supply the User1 account password. Because this account will be used for remote desktop connections for all CORP domain member computers, choose a strong password. Record the User1 account password and store it in a secured location.</span></span>
  
<span data-ttu-id="059b1-p116">次に、エンタープライズ管理者として新しい User1 アカウントを構成します。管理者レベルの Windows PowerShell コマンド プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="059b1-p116">Next, configure the new User1 account as an Enterprise Administrator. Run this command at the administrator-level Windows PowerShell command prompt.</span></span>
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

<span data-ttu-id="059b1-187">DC1 とは、リモート デスクトップ セッションを終了し、再度接続 CORP を使用して\\User1 のアカウントです。</span><span class="sxs-lookup"><span data-stu-id="059b1-187">Close the Remote Desktop session with DC1 and then reconnect using the CORP\\User1 account.</span></span>
  
<span data-ttu-id="059b1-188">次に、Ping ツールのトラフィックを許可するため、管理者レベルの Windows PowerShell コマンド プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="059b1-188">Next, to allow traffic for the Ping tool, run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

<span data-ttu-id="059b1-189">これは、現在の構成です。</span><span class="sxs-lookup"><span data-stu-id="059b1-189">This is your current configuration.</span></span>
  
![DC1 仮想マシンを含む Azure のフェーズ 2 基本構成](images/49069908-29c3-4d73-87f7-debbea067261.png)
  
## <a name="phase-3-configure-app1"></a><span data-ttu-id="059b1-191">フェーズ 3:APP1 を構成する</span><span class="sxs-lookup"><span data-stu-id="059b1-191">Phase 3: Configure APP1</span></span>

<span data-ttu-id="059b1-192">APP1 は、Web サービスとファイル共有サービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="059b1-192">APP1 provides web and file sharing services.</span></span>
  
<span data-ttu-id="059b1-193">APP1 用の Azure 仮想マシンを作成するには、使用しているリソース グループの名前、Azure の場所、ストレージ アカウント名を入力し、ローカル コンピューターの Azure PowerShell コマンド プロンプトで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="059b1-193">To create an Azure Virtual Machine for APP1, fill in the name of your resource group, Azure location, and storage account name and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="059b1-194">次に、APP1 のローカル管理者アカウント名とパスワードを使用して APP1 仮想マシンに接続し、Windows PowerShell コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="059b1-194">Next, connect to the APP1 virtual machine using the APP1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="059b1-195">APP1 と DC1 との間の名前解決とネットワーク通信を確認するには、 **ping dc1.corp.contoso.com**コマンドを実行し、4 つの応答があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="059b1-195">To check name resolution and network communication between APP1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="059b1-196">次に、Windows PowerShell プロンプトでこれらのコマンドを使用して、APP1 仮想マシンを CORP ドメインに参加させます。</span><span class="sxs-lookup"><span data-stu-id="059b1-196">Next, join the APP1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="059b1-197">CORP を指定する必要があります注\\User1 ドメイン アカウントの資格情報、**コンピューターの追加**] コマンドを実行した後。</span><span class="sxs-lookup"><span data-stu-id="059b1-197">Note that you must supply the CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="059b1-198">APP1 を再起動した後は、CORP を使用して接続\\User1 のアカウント、しを開きます管理者レベルの Windows PowerShell コマンド プロンプトです。</span><span class="sxs-lookup"><span data-stu-id="059b1-198">After APP1 restarts, connect to it using the CORP\\User1 account, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="059b1-199">次に、APP1 の Windows PowerShell コマンド プロンプトで、このコマンドを使用して、APP1 を Web サーバーにします。</span><span class="sxs-lookup"><span data-stu-id="059b1-199">Next, make APP1 a web server with this command at the Windows PowerShell command prompt on APP1.</span></span>
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

<span data-ttu-id="059b1-200">次に、APP1 で共有フォルダーを次の PowerShell コマンドを使用して作成し、そのフォルダー内にテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="059b1-200">Next, create a shared folder and a text file within the folder on APP1 with these PowerShell commands.</span></span>
  
```
New-Item -path c:\\files -type directory
Write-Output "This is a shared file." | out-file c:\\files\\example.txt
New-SmbShare -name files -path c:\\files -changeaccess CORP\\User1
```

<span data-ttu-id="059b1-201">これは、現在の構成です。</span><span class="sxs-lookup"><span data-stu-id="059b1-201">This is your current configuration.</span></span>
  
![APP1 仮想マシンを含む Azure のフェーズ 3 基本構成](images/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
## <a name="phase-4-configure-client1"></a><span data-ttu-id="059b1-203">フェーズ 4:CLIENT1 を構成する</span><span class="sxs-lookup"><span data-stu-id="059b1-203">Phase 4: Configure CLIENT1</span></span>

<span data-ttu-id="059b1-204">CLIENT1 は、Contoso イントラネット上の一般的なノート PC、タブレット、デスクトップ コンピューターとして機能します。</span><span class="sxs-lookup"><span data-stu-id="059b1-204">CLIENT1 acts as a typical laptop, tablet, or desktop computer on the Contoso intranet.</span></span>
  
> [!NOTE]
> <span data-ttu-id="059b1-p117">CLIENT1 を作成する次のコマンド セット Azure サブスクリプションのすべての種類の動作を行うことができます Windows Server 2016 Datacenter を実行しています。Visual Studio ベースの Azure サブスクリプションがある場合は、 [Azure ポータル](https://portal.azure.com)で、CLIENT1 実行している Windows の 10、Windows 8 の場合、または Windows 7 を作成できます。</span><span class="sxs-lookup"><span data-stu-id="059b1-p117">The following command set creates CLIENT1 running Windows Server 2016 Datacenter, which can be done for all types of Azure subscriptions. If you have an Visual Studio-based Azure subscription, you can create CLIENT1 running Windows 10, Windows 8, or Windows 7 with the [Azure portal](https://portal.azure.com).</span></span> 
  
<span data-ttu-id="059b1-207">CLIENT1 用の Azure 仮想マシンを作成するには、使用しているリソース グループの名前、Azure の場所、ストレージ アカウント名を入力し、ローカル コンピューターの Azure PowerShell コマンド プロンプトで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="059b1-207">To create an Azure Virtual Machine for CLIENT1, fill in the name of your resource group, Azure location, and storage account name and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="059b1-208">次に、CLIENT1 のローカル管理者アカウント名とパスワードを使用して、CLIENT1 仮想マシンに接続し、管理者レベルの Windows PowerShell コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="059b1-208">Next, connect to the CLIENT1 virtual machine using the CLIENT1 local administrator account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="059b1-209">CLIENT1 と DC1 との間の名前解決とネットワーク通信を確認するには、Windows PowerShell コマンド プロンプトで**ping の dc1.corp.contoso.com**コマンドを実行し、4 つの応答があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="059b1-209">To check name resolution and network communication between CLIENT1 and DC1, run the **ping dc1.corp.contoso.com** command at a Windows PowerShell command prompt and verify that there are four replies.</span></span>
  
<span data-ttu-id="059b1-210">次に、Windows PowerShell プロンプトで次のコマンドを使用して、CLIENT1 仮想マシンを CORP ドメインに参加させます。</span><span class="sxs-lookup"><span data-stu-id="059b1-210">Next, join the CLIENT1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="059b1-211">CORP を指定する必要があります注\\User1 ドメイン アカウントの資格情報、**コンピューターの追加**] コマンドを実行した後。</span><span class="sxs-lookup"><span data-stu-id="059b1-211">Note that you must supply your CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="059b1-212">CLIENT1 の再起動後は、CORP を使用して接続\\User1 のアカウント名とパスワード、および、管理者レベルの Windows PowerShell コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="059b1-212">After CLIENT1 restarts, connect to it using the CORP\\User1 account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="059b1-213">次に、CLIENT1 から APP1 の Web リソースおよびファイル共有リソースにアクセスできることを確認します。</span><span class="sxs-lookup"><span data-stu-id="059b1-213">Next, verify that you can access web and file share resources on APP1 from CLIENT1.</span></span>
  
### <a name="verify-client-access-to-app1"></a><span data-ttu-id="059b1-214">APP1 への CLIENT アクセスを確認する</span><span class="sxs-lookup"><span data-stu-id="059b1-214">Verify CLIENT access to APP1</span></span>

1. <span data-ttu-id="059b1-215">サーバー マネージャーで、ツリー ペインで、**ローカル サーバー**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="059b1-215">In Server Manager, in the tree pane, click **Local Server**.</span></span>
    
2. <span data-ttu-id="059b1-216">**CLIENT1 のプロパティ**] で**の** **IE セキュリティ強化の構成**の横にあるをクリックします。</span><span class="sxs-lookup"><span data-stu-id="059b1-216">In **Properties for CLIENT1**, click **On** next to **IE Enhanced Security Configuration**.</span></span>
    
3. <span data-ttu-id="059b1-217">**Internet Explorer セキュリティ強化の構成**では、**管理者**および**ユーザー**を**オフ**] をクリックし、し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="059b1-217">In **Internet Explorer Enhanced Security Configuration**, click **Off** for **Administrators** and **Users**, and then click **OK**.</span></span>
    
4. <span data-ttu-id="059b1-218">開始] 画面で、 **Internet Explorer**] をクリックし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="059b1-218">From the Start screen, click **Internet Explorer**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="059b1-p118">アドレス ・ バーでは、 **http://app1.corp.contoso.com/**を入力し、ENTER キーを押します。APP1 の既定のインターネット インフォメーション サービスの web ページを参照してくださいする必要があります。</span><span class="sxs-lookup"><span data-stu-id="059b1-p118">In the Address bar, type **http://app1.corp.contoso.com/**, and then press ENTER. You should see the default Internet Information Services web page for APP1.</span></span>
    
6. <span data-ttu-id="059b1-221">デスクトップのタスクバーで [ファイル エクスプ ローラー] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="059b1-221">From the desktop taskbar, click the File Explorer icon.</span></span>
    
7. <span data-ttu-id="059b1-p119">アドレス バーに、入力**\\ \\app1\\ファイル**、し、ENTER キーを押します。ファイルの共有フォルダーの内容をフォルダー ウィンドウを参照してくださいする必要があります。</span><span class="sxs-lookup"><span data-stu-id="059b1-p119">In the address bar, type **\\\\app1\\Files**, and then press ENTER. You should see a folder window with the contents of the Files shared folder.</span></span>
    
8. <span data-ttu-id="059b1-p120">**ファイル**共有のフォルダー ウィンドウで、 **Example.txt**ファイルをダブルクリックします。Example.txt ファイルの内容を表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="059b1-p120">In the **Files** shared folder window, double-click the **Example.txt** file. You should see the contents of the Example.txt file.</span></span>
    
9. <span data-ttu-id="059b1-226">**Example.txt - メモ帳**と**ファイル**共有のフォルダー ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="059b1-226">Close the **example.txt - Notepad** and the **Files** shared folder windows.</span></span>
    
<span data-ttu-id="059b1-227">これは、最後の構成です。</span><span class="sxs-lookup"><span data-stu-id="059b1-227">This is your final configuration.</span></span>
  
![CLIENT1 仮想マシンを含む Azure のフェーズ 4 基本構成](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="059b1-229">Azure の基本構成は、アプリケーション開発とテスト、追加のテスト環境の作成を行うための準備ができました。</span><span class="sxs-lookup"><span data-stu-id="059b1-229">Your Base Configuration in Azure is now ready for application development and testing or for building additional test environments.</span></span> 
  
> [!TIP]
> <span data-ttu-id="059b1-230">[ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="059b1-230">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a><span data-ttu-id="059b1-231">Azure のテスト環境の仮想マシンのコストを最小限に抑える</span><span class="sxs-lookup"><span data-stu-id="059b1-231">Minimizing the costs of test environment virtual machines in Azure</span></span>
<span data-ttu-id="059b1-232"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="059b1-232"></span></span>

<span data-ttu-id="059b1-233">テスト環境の仮想マシンを実行するコストを最小限に抑えるには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="059b1-233">To minimize the cost of running the test environment virtual machines, you can do one of the following:</span></span>
  
- <span data-ttu-id="059b1-p121">テスト環境を作成し、できるだけ早く、必要なテストとデモを行います。完了したら、テスト環境のリソース グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="059b1-p121">Create the test environment and perform your needed testing and demonstration as quickly as possible. When complete, delete the resource group for the test environment.</span></span>
    
- <span data-ttu-id="059b1-236">	テスト環境の仮想マシンをシャットダウンして、割り当てが解除された状態にします。</span><span class="sxs-lookup"><span data-stu-id="059b1-236">Shut down your test environment virtual machines into a deallocated state.</span></span>
    
<span data-ttu-id="059b1-237">Azure PowerShell で仮想マシンをシャットダウンするには、リソース グループ名を入力し、次のコマンドを実行してください。</span><span class="sxs-lookup"><span data-stu-id="059b1-237">To shut down the virtual machines with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

<span data-ttu-id="059b1-238">すべての仮想マシンを停止 (割り当て解除) 状態から起動するときに正常に動作させるには、仮想マシンを次の順序で起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="059b1-238">To ensure that your virtual machines work properly when starting all of them from the Stopped (Deallocated) state, you should start them in the following order:</span></span>
  
1. <span data-ttu-id="059b1-239">DC1</span><span class="sxs-lookup"><span data-stu-id="059b1-239">DC1</span></span>
    
2. <span data-ttu-id="059b1-240">APP1</span><span class="sxs-lookup"><span data-stu-id="059b1-240">APP1</span></span>
    
3. <span data-ttu-id="059b1-241">CLIENT1</span><span class="sxs-lookup"><span data-stu-id="059b1-241">CLIENT1</span></span>
    
<span data-ttu-id="059b1-242">Azure PowerShell で仮想マシンを順番に起動するには、リソース グループ名を入力し、次のコマンドを実行してください。</span><span class="sxs-lookup"><span data-stu-id="059b1-242">To start the virtual machines in order with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a><span data-ttu-id="059b1-243">関連項目</span><span class="sxs-lookup"><span data-stu-id="059b1-243">See Also</span></span>

<span data-ttu-id="059b1-244"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="059b1-244"></span></span>

[<span data-ttu-id="059b1-245">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="059b1-245">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="059b1-246">Office 365 開発/テスト環境の DirSync</span><span class="sxs-lookup"><span data-stu-id="059b1-246">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="059b1-247">Office 365 開発/テスト環境の Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="059b1-247">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="059b1-248">Office 365 開発/テスト環境の Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="059b1-248">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="059b1-249">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="059b1-249">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


