---
title: 基本構成開発/テスト環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
ms.audience: ITPro
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
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: '概要: Microsoft Azure で、開発/テスト環境として簡略化されたイントラネットを作成します。'
ms.openlocfilehash: a38fc04ffe4ffa9a76430cf44543174570d398bc
ms.sourcegitcommit: dffbcfb1cbc9776a29229a787c1eab4192e55cff
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2019
ms.locfileid: "30948618"
---
# <a name="base-configuration-devtest-environment"></a><span data-ttu-id="07567-103">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="07567-103">Base Configuration dev/test environment</span></span>

 <span data-ttu-id="07567-104">**概要:** Microsoft Azure で、開発/テスト環境として簡略化されたイントラネットを作成します。</span><span class="sxs-lookup"><span data-stu-id="07567-104">**Summary:** Create a simplified intranet as a dev/test environment in Microsoft Azure.</span></span>
  
<span data-ttu-id="07567-105">この記事では、Azure で次の基本構成開発/テスト環境を作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="07567-105">This article provides you with instructions to create the following Base Configuration dev/test environment in Azure:</span></span>
  
![Azure での基本構成](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="07567-107">**図 1: 基本構成開発/テスト環境**</span><span class="sxs-lookup"><span data-stu-id="07567-107">**Figure 1: The Base Configuration dev/test environment**</span></span>

<span data-ttu-id="07567-p101">図 1 の基本構成開発/テスト環境は、インターネットに接続された簡略化されたプライベート イントラネットをシミュレートする、TestLab というクラウド専用 Azure Virtual Network 内の企業ネットワーク サブネットで構成されています。Windows Server 2016 を実行している次の 3 つの Azure 仮想マシンが含まれます。</span><span class="sxs-lookup"><span data-stu-id="07567-p101">The Base Configuration dev/test environment in Figure 1 consists of the Corpnet subnet in a cloud-only Azure virtual network named TestLab that simulates a simplified, private intranet connected to the Internet. It has three Azure virtual machines running Windows Server 2016:</span></span>
  
- <span data-ttu-id="07567-110">イントラネット ドメイン コントローラーとドメイン ネーム システム (DNS) サーバーとして構成されている DC1</span><span class="sxs-lookup"><span data-stu-id="07567-110">DC1 is configured as an intranet domain controller and Domain Name System (DNS) server</span></span>
    
- <span data-ttu-id="07567-111">一般的なアプリケーションおよび Web サーバーとして構成されている APP1</span><span class="sxs-lookup"><span data-stu-id="07567-111">APP1 is configured as a general application and web server</span></span>
    
- <span data-ttu-id="07567-112">イントラネット クライアントとして動作する CLIENT1</span><span class="sxs-lookup"><span data-stu-id="07567-112">CLIENT1 acts as an intranet client</span></span>
    
<span data-ttu-id="07567-113">この構成では、DC1、APP1、CLIENT1、他の企業ネットワークのサブネットのコンピューターを、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="07567-113">This configuration lets DC1, APP1, CLIENT1, and additional Corpnet subnet computers to be:</span></span> 
  
- <span data-ttu-id="07567-114">更新プログラムをインストールするためにインターネットに接続して、リアルタイムでインターネット リソースにアクセスし、Microsoft Office 365 とその他の Azure サービスなどのパブリック クラウド テクノロジに参加する。</span><span class="sxs-lookup"><span data-stu-id="07567-114">Connected to the Internet to install updates, access Internet resources in real time, and participate in public cloud technologies such as Microsoft Office 365 and other Azure services.</span></span>
    
- <span data-ttu-id="07567-115">インターネットや組織のネットワークに接続されているコンピューターから、リモート デスクトップ接続を使用してリモートで管理する。</span><span class="sxs-lookup"><span data-stu-id="07567-115">Remotely managed using Remote Desktop connections from your computer that is connected to the Internet or your organization network.</span></span>
    
<span data-ttu-id="07567-116">作成したテスト環境を、次の目的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="07567-116">You can use the resulting test environment:</span></span>
  
- <span data-ttu-id="07567-117">アプリケーション開発とテスト。</span><span class="sxs-lookup"><span data-stu-id="07567-117">For application development and testing.</span></span>
    
- <span data-ttu-id="07567-118">追加の仮想マシン、Azure サービス、その他の Microsoft クラウド サービス (Office 365 や Enterprise Mobility + Security (EMS) など) を含む、独自の設計の拡張されたテスト環境の初期構成として。</span><span class="sxs-lookup"><span data-stu-id="07567-118">As the initial configuration of an extended test environment of your own design that includes additional virtual machines, Azure services, or other Microsoft cloud offerings such as Office 365 and Enterprise Mobility + Security (EMS).</span></span>
    
<span data-ttu-id="07567-119">このような環境を作成するには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="07567-119">There are two methods to creating this environment:</span></span>

1. <span data-ttu-id="07567-120">Azure Resource Manager のテンプレート</span><span class="sxs-lookup"><span data-stu-id="07567-120">An Azure Resource Manager template</span></span>
2. <span data-ttu-id="07567-121">Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="07567-121">Azure Powershell</span></span>

## <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a><span data-ttu-id="07567-122">方法 1: Azure Resource Manager テンプレートを使用して、シミュレートされたイントラネットを構築する</span><span class="sxs-lookup"><span data-stu-id="07567-122">Method 1: Build your simulated intranet with an Azure Resource Manager template</span></span>

<span data-ttu-id="07567-p102">この方法では、Azure Resource Manager (ARM) テンプレートを使用してシミュレートされたイントラネットを構築します。ARM テンプレートには、Azure ネットワーク インフラストラクチャおよび仮想マシンを作成して構成するためのすべての手順が含まれています。</span><span class="sxs-lookup"><span data-stu-id="07567-p102">In this method, you use an Azure Resource Manager (ARM) template to build out the simulated intranet. ARM templates contain all of the instructions to create and configure the Azure networking infrastructure and the virtual machines.</span></span>

<span data-ttu-id="07567-125">テンプレートを展開する前に「[テンプレートの Readme ページ](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm)」を確認し、次の情報をご用意ください。</span><span class="sxs-lookup"><span data-stu-id="07567-125">Prior to deploying the template, read through the [template README page](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) and have the following information ready:</span></span>

- <span data-ttu-id="07567-p103">Azure サブスクリプションの名前。**[カスタムの導入]** ページの **[サブスクリプション]** フィールドにこのラベルを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07567-p103">The Azure subscription name. You’ll need to enter this label in the **Subscription** field of the **Custom deployment** page.</span></span>
- <span data-ttu-id="07567-p104">Azure リソース グループの名前。**[カスタムの導入]** ページの **[リソース グループ]** フィールドにこのラベルを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07567-p104">The Azure resource group name. You’ll need to enter this label in the **Resource group** field of the **Custom deployment** page.</span></span>
- <span data-ttu-id="07567-p105">仮想マシンのパブリック IP アドレスの URL の DNS ラベル プレフィックス。[**カスタム デプロイ**] ページの [**DNS ラベル プレフィックス**] フィールドにこのラベルを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07567-p105">A DNS label prefix for the URLs of the public IP addresses of your virtual machines. You’ll need to enter this label in the **Dns Label Prefix** field of the **Custom deployment** page.</span></span>

<span data-ttu-id="07567-132">手順をすべて確認したら、[[テンプレートの Readme ページ](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm)] で [**Azure に展開**] をクリックして展開を開始します。</span><span class="sxs-lookup"><span data-stu-id="07567-132">After reading through the instructions, click **Deploy to Azure** on the [template README page](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) to get started.</span></span>

>[!Note]
><span data-ttu-id="07567-133">ARM テンプレートで作成されたシミュレートされたイントラネットでは、Azure の有料サブスクリプションが必要です。</span><span class="sxs-lookup"><span data-stu-id="07567-133">The simulated intranet built by the ARM template requires a paid Azure subscription.</span></span>
>

<span data-ttu-id="07567-134">こちらがテンプレート完了後の構成です。</span><span class="sxs-lookup"><span data-stu-id="07567-134">Here is your configuration after the template is complete.</span></span>

![Azure での基本構成](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


## <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a><span data-ttu-id="07567-136">方法 2: Azure PowerShell を使用してシミュレートされたイントラネットを構築する</span><span class="sxs-lookup"><span data-stu-id="07567-136">Method 2: Build your simulated intranet with Azure PowerShell</span></span>

<span data-ttu-id="07567-137">この方法では、Windows PowerShell と Azure PowerShell モジュールを使用してネットワーク インフラストラクチャ、仮想マシン、およびその構成を構築します。</span><span class="sxs-lookup"><span data-stu-id="07567-137">In this method, you use Windows PowerShell and the Azure PowerShell module to build out the networking infrastructure, the virtual machines, and their configuration.</span></span>

<span data-ttu-id="07567-p106">Azure インフラストラクチャの要素を作成する作業を、PowerShell でコマンド ブロックを 1 つずつ進める方法で経験してみたいという場合は、この方法をお使いください。その後、Azure で他の仮想マシンを展開するために PowerShell コマンドのブロックをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="07567-p106">Use this method if you want to get experience creating elements of Azure infrastructure one command block at a time with PowerShell. You can then customize the PowerShell command blocks for your own deployment of other virtual machines in Azure.</span></span>

<span data-ttu-id="07567-140">Azure PowerShell を使った基本構成テスト環境の設定には次の 4 つのステップがあります。</span><span class="sxs-lookup"><span data-stu-id="07567-140">There are four steps to setting up the Base Configuration test environment using Azure PowerShell:</span></span>
  
1. <span data-ttu-id="07567-141">仮想ネットワークを作成します。</span><span class="sxs-lookup"><span data-stu-id="07567-141">Create the virtual network.</span></span>
    
2. <span data-ttu-id="07567-142">DC1 を構成します。</span><span class="sxs-lookup"><span data-stu-id="07567-142">Configure DC1.</span></span>
    
3. <span data-ttu-id="07567-143">APP1 を構成します。</span><span class="sxs-lookup"><span data-stu-id="07567-143">Configure APP1.</span></span>
    
4. <span data-ttu-id="07567-144">CLIENT1 を構成します。</span><span class="sxs-lookup"><span data-stu-id="07567-144">Configure CLIENT1.</span></span>
    
<span data-ttu-id="07567-p107">まだ Azure サブスクリプションを取得していない場合は、「[Azure の無料アカウントを今すぐ作成しましょう](https://azure.microsoft.com/pricing/free-trial/)」で無料トライアルにサインアップできます。MSDN や Visual Studio のサブスクリプションを取得している場合は、「[Visual Studio サブスクライバー向けの月単位の Azure クレジット](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07567-p107">If you do not already have an Azure subscription, you can sign up for a free trial at [Try Azure](https://azure.microsoft.com/pricing/free-trial/). If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="07567-p108">Azure の仮想マシンは、実行中に継続して金銭的なコストが発生します。このコストは、無料試用版、MSDN サブスクリプション、有料版サブスクリプションに対して請求されます。Azure 仮想マシンの実行にかかるコストの詳細については、「[Linux Virtual Machines の料金](https://azure.microsoft.com/pricing/details/virtual-machines/)」と「[料金計算ツール](https://azure.microsoft.com/pricing/calculator/)」を参照してください。コストを低く抑えるには、「[Azure のテスト環境の仮想マシンのコストを最小限に抑える](base-configuration-dev-test-environment.md#mincost)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07567-p108">Virtual machines in Azure incur an ongoing monetary cost when they are running. This cost is billed against your free trial, MSDN subscription, or paid subscription. For more information about the costs of running Azure virtual machines, see [Virtual Machines Pricing Details](https://azure.microsoft.com/pricing/details/virtual-machines/) and [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/). To keep costs down, see [Minimizing the costs of test environment virtual machines in Azure](base-configuration-dev-test-environment.md#mincost).</span></span> 
  
![Microsoft Cloud のテスト ラボ ガイド](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="07567-152">[ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="07567-152">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
### <a name="step-1-create-the-virtual-network"></a><span data-ttu-id="07567-153">ステップ 1: 仮想ネットワークを作成します。</span><span class="sxs-lookup"><span data-stu-id="07567-153">Step 1: Create the virtual network</span></span>

<span data-ttu-id="07567-154">このステップでは、Azure で TestLab 仮想ネットワークを作成します。</span><span class="sxs-lookup"><span data-stu-id="07567-154">In this step, you the TestLab virtual network in Azure.</span></span>

<span data-ttu-id="07567-155">最初に、Azure PowerShell プロンプトを起動します。</span><span class="sxs-lookup"><span data-stu-id="07567-155">First, start an Azure PowerShell prompt.</span></span>
  
> [!NOTE]
> <span data-ttu-id="07567-p109">次に示すコマンド セットは、Azure PowerShell の最新版を使用します。「[Azure PowerShell の概要](https://docs.microsoft.com/ja-JP/powershell/azureps-cmdlets-docs/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07567-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/ja-JP/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="07567-158">次のコマンドを使用して Azure アカウントにログインします。</span><span class="sxs-lookup"><span data-stu-id="07567-158">Sign in to your Azure account with the following command.</span></span>
  
```
Connect-AzAccount
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) to get a text file that has all the PowerShell commands in this article.
-->

<span data-ttu-id="07567-159">次のコマンドを使用して、サブスクリプションの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="07567-159">Get your subscription name using the following command.</span></span>
  
```
Get-AzSubscription | Sort Name | Select Name
```

<span data-ttu-id="07567-p110">Azure サブスクリプションを設定します。二重引用符内のすべて (「<」と「>」の文字を含む) を正しい名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="07567-p110">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="07567-p111">次に、基本構成テスト ラボ用の新しいリソース グループを作成します。一意のリソース グループ名を特定するには、このコマンドを使用して既存のリソース グループを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="07567-p111">Next, create a new resource group for your Base Configuration test lab. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="07567-p112">これらのコマンドを使用して、新しいリソース グループを作成します。二重引用符内のすべて (< 文字と > 文字を含む) を正しい名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="07567-p112">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="07567-166">次に、基本構成の企業ネットワークのサブネットをホストする TestLab 仮想ネットワークを作成し、ネットワーク セキュリティ グループで保護します。</span><span class="sxs-lookup"><span data-stu-id="07567-166">Next, you create the TestLab virtual network that will host the Corpnet subnet of the base configuration and protect it with a network security group.</span></span>
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
```

<span data-ttu-id="07567-167">こちらが現在の構成です。</span><span class="sxs-lookup"><span data-stu-id="07567-167">This is your current configuration.</span></span>
  
![仮想ネットワークとサブネットを含む Azure の基本構成、ステップ 1](media/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
### <a name="step-2-configure-dc1"></a><span data-ttu-id="07567-169">ステップ 2: DC1 を構成する</span><span class="sxs-lookup"><span data-stu-id="07567-169">Step 2: Configure DC1</span></span>

<span data-ttu-id="07567-170">このステップでは、DC1 仮想マシンを作成し、それを Windows Server Active Directory (AD) の corp.contoso.comis ドメインのドメイン コントローラー、および TestLab 仮想ネットワークの仮想マシン用の DNS サーバーとして構成します。</span><span class="sxs-lookup"><span data-stu-id="07567-170">In this step, we create the DC1 virtual machine and configure it as a domain controller for the corp.contoso.com Windows Server Active Directory (AD) domain and a DNS server for the virtual machines of the TestLab virtual network.</span></span>

> [!NOTE]
> <span data-ttu-id="07567-p113">以下のコマンド ブロックを実行する前に、選択した Azure リージョン (場所) が Azure の仮想マシンのサイズをサポートしているか確認してください。既定では、Standard_A1 に設定されています。[ここ](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines)をクリックすると Azure 仮想マシンのサイズと場所を確認できます。</span><span class="sxs-lookup"><span data-stu-id="07567-p113">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="07567-173">DC1 用の Azure 仮想マシンを作成するには、リソース グループの名前を入力して、次に示すコマンドをローカル コンピューターの Azure PowerShell コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="07567-173">To create an Azure virtual machine for DC1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="07567-p114">DC1 のローカル管理者アカウントのユーザー名とパスワードを入力するようダイアログが表示されます。強力なパスワードを使用して、安全な場所に名前とパスワードの両方を記録します。</span><span class="sxs-lookup"><span data-stu-id="07567-p114">You will be prompted for a user name and password for the local administrator account on DC1. Use a strong password and record both the name and password in a secure location.</span></span>
  
<span data-ttu-id="07567-176">次に、DC1 仮想マシンに接続します。</span><span class="sxs-lookup"><span data-stu-id="07567-176">Next, connect to the DC1 virtual machine.</span></span>
  
1. <span data-ttu-id="07567-177">[Azure portal](https://portal.azure.com) で、**[リソース グループ] >**「新しいリソース グループの名前」\*\* > [DC1] > [接続]\*\* の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="07567-177">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [the name of your new resource group] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="07567-p115">起動ウィンドウで **[RDP ファイルのダウンロード]** をクリックします。ダウンロードされる DC1.rdp ファイルを開いてから、**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="07567-p115">In the open pane, click **Download RDP file**. Open the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="07567-180">DC1 のローカル管理者アカウント名を指定します。</span><span class="sxs-lookup"><span data-stu-id="07567-180">Specify the DC1 local administrator account name:</span></span>
    
  - <span data-ttu-id="07567-181">Windows 7 の場合:</span><span class="sxs-lookup"><span data-stu-id="07567-181">For Windows 7:</span></span>
    
    <span data-ttu-id="07567-p116">**[Windows セキュリティ]** ダイアログ ボックスで、**[別のアカウントを使用]** をクリックします。**[ユーザー名]** に「**DC1\\**[ローカル管理者アカウント名]」を入力します。</span><span class="sxs-lookup"><span data-stu-id="07567-p116">In the **Windows Security** dialog box, click **Use another account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
  - <span data-ttu-id="07567-184">Windows 8 または Windows 10 の場合:</span><span class="sxs-lookup"><span data-stu-id="07567-184">For Windows 8 or Windows 10:</span></span>
    
    <span data-ttu-id="07567-p117">**[Windows セキュリティ]** ダイアログ ボックスで、**[その他]** をクリックし、**[別のアカウントを使用する]** をクリックします。**[ユーザー名]** に、「**DC1\\**[ローカル管理者アカウント名]」を入力します。</span><span class="sxs-lookup"><span data-stu-id="07567-p117">In the **Windows Security** dialog box, click **More choices**, and then click **Use a different account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="07567-187">**[パスワード]** にローカル管理者アカウントのパスワードを入力して、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="07567-187">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="07567-188">ダイアログが表示されたら、**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="07567-188">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="07567-189">次に、DC1 の管理者レベルの Windows PowerShell コマンド プロンプトで次のコマンドを使用して、新しいボリュームとして別のデータ ディスク (ドライブ文字 F:) を追加します。</span><span class="sxs-lookup"><span data-stu-id="07567-189">Next, add an extra data disk as a new volume with the drive letter F: with this command at an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="07567-p118">次に corp.contoso.com ドメインのドメイン コントローラーおよび DNS サーバーとして DC1 を構成します。管理者レベルの Windows PowerShell コマンド プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="07567-p118">Next, configure DC1 as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
<span data-ttu-id="07567-p119">セーフ モードの管理者パスワードを指定する必要があります。パスワードを安全な場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="07567-p119">You will need to specify a safe mode administrator password. Store this password in a secure location.</span></span>
  
<span data-ttu-id="07567-194">これらのコマンドの完了には数分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="07567-194">Note that these commands can take a few minutes to complete.</span></span>
  
<span data-ttu-id="07567-195">DC1 の再起動後に、ドメインの資格情報を使って DC1 仮想マシンに再接続します。</span><span class="sxs-lookup"><span data-stu-id="07567-195">After DC1 restarts, reconnect to the DC1 virtual machine using domain credentials.</span></span>
  
1. <span data-ttu-id="07567-196">[Azure portal](https://portal.azure.com) で、**[リソース グループ] > **[リソース グループ名]** > [DC1] > [接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="07567-196">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [your resource group name] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="07567-197">ダウンロードされる DC1.rdp ファイルを実行して、**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="07567-197">Run the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="07567-p120">**[Windows セキュリティ]** で **[別のアカウントを使用]** をクリックします。**[ユーザー名]** に「**CORP\\**[ローカル管理者アカウント名]」を入力します。</span><span class="sxs-lookup"><span data-stu-id="07567-p120">In **Windows Security**, click **Use another account**. In **User name**, type **CORP\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="07567-200">**[パスワード]** にローカル管理者アカウントのパスワードを入力して、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="07567-200">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="07567-201">ダイアログが表示されたら、**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="07567-201">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="07567-p121">次に、CORP ドメイン メンバー コンピューターにログインするときに使用する、Active Directory のユーザー アカウントを作成します。管理者レベルの Windows PowerShell コマンド プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="07567-p121">Next, create a user account in Active Directory that will be used when logging in to CORP domain member computers. Run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="07567-p122">このコマンドでは、User1 アカウントのパスワードを入力するよう求められることに注意してください。このアカウントは、すべての CORP ドメイン メンバー コンピューターのリモート デスクトップ接続に使用するため、強力なパスワードを選択してください。User1 アカウントのパスワードを記録し、セキュリティで保護された場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="07567-p122">Note that this command prompts you to supply the User1 account password. Because this account will be used for remote desktop connections for all CORP domain member computers, choose a strong password. Record the User1 account password and store it in a secured location.</span></span>
  
<span data-ttu-id="07567-p123">次に、エンタープライズ管理者として新しい User1 のアカウントを構成します。管理者レベルの Windows PowerShell コマンド プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="07567-p123">Next, configure the new User1 account as an Enterprise Administrator. Run this command at the administrator-level Windows PowerShell command prompt.</span></span>
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

<span data-ttu-id="07567-209">DC1 とのリモート デスクトップ セッションを終了し、CORP\\User1 のアカウントを使用して再接続します。</span><span class="sxs-lookup"><span data-stu-id="07567-209">Close the Remote Desktop session with DC1 and then reconnect using the CORP\\User1 account.</span></span>
  
<span data-ttu-id="07567-210">次に、Ping ツールのトラフィックを許可するため、管理者レベルの Windows PowerShell コマンド プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="07567-210">Next, to allow traffic for the Ping tool, run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

<span data-ttu-id="07567-211">こちらが現在の構成です。</span><span class="sxs-lookup"><span data-stu-id="07567-211">This is your current configuration.</span></span>
  
![DC1 仮想マシンを含む Azure の基本構成、ステップ 2](media/49069908-29c3-4d73-87f7-debbea067261.png)
  
### <a name="step-3-configure-app1"></a><span data-ttu-id="07567-213">ステップ 3: APP1 を構成する</span><span class="sxs-lookup"><span data-stu-id="07567-213">Step 3: Configure APP1</span></span>

<span data-ttu-id="07567-214">このステップでは、Web およびファイル共有サービスを提供する APP1 を作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="07567-214">In this step, you create and configure APP1, which provides web and file sharing services.</span></span>

> [!NOTE]
> <span data-ttu-id="07567-p124">以下のコマンド ブロックを実行する前に、選択した Azure リージョン (場所) が Azure の仮想マシンのサイズをサポートしているか確認してください。既定では、Standard_A1 に設定されています。[ここ](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines)をクリックすると Azure 仮想マシンのサイズと場所を確認できます。</span><span class="sxs-lookup"><span data-stu-id="07567-p124">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="07567-217">APP1 用の Azure 仮想マシンを作成するには、リソース グループの名前を入力して、次に示すコマンドをローカル コンピューターの Azure PowerShell コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="07567-217">To create an Azure Virtual Machine for APP1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="07567-218">次に、APP1 のローカル管理者アカウント名とパスワードを使用して APP1 仮想マシンに接続し、Windows PowerShell コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="07567-218">Next, connect to the APP1 virtual machine using the APP1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="07567-219">APP1 と DC1 の間の名前の解決とネットワーク通信を確認するには、**ping dc1.corp.contoso.com** コマンドを実行し、4 つの応答があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="07567-219">To check name resolution and network communication between APP1 and DC1, run the **ping dc1.corp.contoso.com** command and check that there are four replies.</span></span>
  
<span data-ttu-id="07567-220">次に、Windows PowerShell プロンプトでこれらのコマンドを使用して、APP1 仮想マシンを CORP ドメインに参加させます。</span><span class="sxs-lookup"><span data-stu-id="07567-220">Next, join the APP1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="07567-221">**Add-Computer** コマンドの実行後には、CORP\\User1 ドメイン アカウントの資格情報を入力する必要がある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="07567-221">Note that you must supply the CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="07567-222">APP1 の再起動後に、CORP\\User1 のアカウントを使用して接続し、管理者レベルの Windows PowerShell コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="07567-222">After APP1 restarts, connect to it using the CORP\\User1 account, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="07567-223">次に、APP1 の Windows PowerShell コマンド プロンプトで、このコマンドを使用して、APP1 を Web サーバーにします。</span><span class="sxs-lookup"><span data-stu-id="07567-223">Next, make APP1 a web server with this command at the Windows PowerShell command prompt on APP1.</span></span>
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

<span data-ttu-id="07567-224">次に、APP1 で共有フォルダーを次の PowerShell コマンドを使用して作成し、そのフォルダー内にテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="07567-224">Next, create a shared folder and a text file within the folder on APP1 with these PowerShell commands.</span></span>
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

<span data-ttu-id="07567-225">こちらが現在の構成です。</span><span class="sxs-lookup"><span data-stu-id="07567-225">This is your current configuration.</span></span>
  
![APP1 仮想マシンを含む Azure の基本構成、ステップ 3](media/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
### <a name="step-4-configure-client1"></a><span data-ttu-id="07567-227">ステップ 4: CLIENT1 を構成する</span><span class="sxs-lookup"><span data-stu-id="07567-227">Step 4: Configure CLIENT1</span></span>

<span data-ttu-id="07567-228">このステップでは、Contoso イントラネット上の一般的なラップトップ、タブレット、またはデスクトップ コンピューターとして機能する CLIENT1 を作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="07567-228">In this step, you create and configure CLIENT1, which acts as a typical laptop, tablet, or desktop computer on the Contoso intranet.</span></span>

> [!NOTE]  
> <span data-ttu-id="07567-p125">次のコマンド セットでは、Windows Server 2016 Datacenter を実行する CLIENT1 を作成します。これは、すべての Azure サブスクリプションのタイプに対して実行できます。Visual Studio ベースの Azure サブスクリプションがある場合は、[Azure portal](https://portal.azure.com) で、Windows 10 を実行する CLIENT1 を作成できます。</span><span class="sxs-lookup"><span data-stu-id="07567-p125">The following command set creates CLIENT1 running Windows Server 2016 Datacenter, which can be done for all types of Azure subscriptions. If you have an Visual Studio-based Azure subscription, you can create CLIENT1 running Windows 10 with the [Azure portal](https://portal.azure.com).</span></span> 
  

> [!NOTE]
> <span data-ttu-id="07567-p126">以下のコマンド ブロックを実行する前に、選択した Azure リージョン (場所) が Azure の仮想マシンのサイズをサポートしているか確認してください。既定では、Standard_A1 に設定されています。[ここ](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines)をクリックすると Azure 仮想マシンのサイズと場所を確認できます。</span><span class="sxs-lookup"><span data-stu-id="07567-p126">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="07567-233">CLIENT1 用の Azure 仮想マシンを作成するには、リソース グループの名前を入力して、次に示すコマンドをローカル コンピューターの Azure PowerShell コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="07567-233">To create an Azure Virtual Machine for CLIENT1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="07567-234">次に、CLIENT1 のローカル管理者アカウント名とパスワードを使用して、CLIENT1 仮想マシンに接続し、管理者レベルの Windows PowerShell コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="07567-234">Next, connect to the CLIENT1 virtual machine using the CLIENT1 local administrator account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="07567-235">CLIENT1 と DC1 の間の名前の解決とネットワーク通信を確認するには、Windows PowerShell コマンド プロンプトで **ping dc1.corp.contoso.com** コマンドを実行し、4 つの応答があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="07567-235">To check name resolution and network communication between CLIENT1 and DC1, run the **ping dc1.corp.contoso.com** command at a Windows PowerShell command prompt and check that there are four replies.</span></span>
  
<span data-ttu-id="07567-236">次に、Windows PowerShell プロンプトで次のコマンドを使用して、CLIENT1 仮想マシンを CORP ドメインに参加させます。</span><span class="sxs-lookup"><span data-stu-id="07567-236">Next, join the CLIENT1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="07567-237">**Add-Computer** コマンドの実行後に、CORP\\User1 ドメイン アカウントの資格情報を入力する必要がある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="07567-237">Note that you must supply your CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="07567-238">CLIENT1 の再起動後に、CORP\\User1 のアカウント名とパスワードを使用して接続し、管理者レベルの Windows PowerShell コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="07567-238">After CLIENT1 restarts, connect to it using the CORP\\User1 account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="07567-239">次に、CLIENT1 から APP1 の Web リソースおよびファイル共有リソースにアクセスできることを確認します。</span><span class="sxs-lookup"><span data-stu-id="07567-239">Next, check that you can access web and file share resources on APP1 from CLIENT1.</span></span>
  
1. <span data-ttu-id="07567-240">サーバー マネージャーのツリー ウィンドウで、**[ローカル サーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="07567-240">In Server Manager, in the tree pane, click **Local Server**.</span></span>
    
2. <span data-ttu-id="07567-241">**[CLIENT1 のプロパティ]** で、**[IE セキュリティ強化の構成]** の横にある **[オン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="07567-241">In **Properties for CLIENT1**, click **On** next to **IE Enhanced Security Configuration**.</span></span>
    
3. <span data-ttu-id="07567-242">**[Internet Explorer セキュリティ強化の構成]** で、**[管理者]** と **[ユーザー]** の **[オフ]** をクリックしてから、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="07567-242">In **Internet Explorer Enhanced Security Configuration**, click **Off** for **Administrators** and **Users**, and then click **OK**.</span></span>
    
4. <span data-ttu-id="07567-243">スタート画面で、**[Internet Explorer]** をクリックしてから、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="07567-243">From the Start screen, click **Internet Explorer**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="07567-p127">アドレス バーに「**http:\//app1.corp.contoso.com/**」と入力してから、ENTER キーを押します。APP1 の既定のインターネット インフォメーション サービスの Web ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="07567-p127">In the Address bar, type **http:\//app1.corp.contoso.com/**, and then press ENTER. You should see the default Internet Information Services web page for APP1.</span></span>
    
6. <span data-ttu-id="07567-246">デスクトップのタスクバーで、[エクスプローラー] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="07567-246">From the desktop taskbar, click the File Explorer icon.</span></span>
    
7. <span data-ttu-id="07567-p128">アドレス バーに「**\\\\app1\\Files**」と入力して、ENTER キーを押します。フォルダー ウィンドウにファイルの共有フォルダーのコンテンツが表示されます。</span><span class="sxs-lookup"><span data-stu-id="07567-p128">In the address bar, type **\\\\app1\\Files**, and then press ENTER. You should see a folder window with the contents of the Files shared folder.</span></span>
    
8. <span data-ttu-id="07567-p129">**[ファイル]** の共有フォルダー ウィンドウで、**[Example.txt]** ファイルをダブルクリックします。Example.txt ファイルのコンテンツが表示されます。</span><span class="sxs-lookup"><span data-stu-id="07567-p129">In the **Files** shared folder window, double-click the **Example.txt** file. You should see the contents of the Example.txt file.</span></span>
    
9. <span data-ttu-id="07567-251">**[example.txt - メモ帳]** と **[ファイル]** の共有フォルダーのウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="07567-251">Close the **example.txt - Notepad** and the **Files** shared folder windows.</span></span>
    
<span data-ttu-id="07567-252">これが、最終的な構成です。</span><span class="sxs-lookup"><span data-stu-id="07567-252">This is your final configuration.</span></span>
  
![CLIENT1 仮想マシンを含む Azure の基本構成、ステップ 4](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="07567-254">Azure の基本構成は、アプリケーション開発とテスト、追加のテスト環境の作成を行うための準備ができました。</span><span class="sxs-lookup"><span data-stu-id="07567-254">Your Base Configuration in Azure is now ready for application development and testing or for building additional test environments.</span></span> 
  
> [!TIP]
> <span data-ttu-id="07567-255">[ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="07567-255">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
<span data-ttu-id="07567-256"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="07567-256"><a name="mincost"> </a></span></span>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a><span data-ttu-id="07567-257">Azure のテスト環境の仮想マシンのコストを最小限に抑える</span><span class="sxs-lookup"><span data-stu-id="07567-257">Minimizing the costs of test environment virtual machines in Azure</span></span>

<span data-ttu-id="07567-258">テスト環境の仮想マシンを実行するコストを最小限に抑えるには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="07567-258">To minimize the cost of running the test environment virtual machines, you can do one of the following:</span></span>
  
- <span data-ttu-id="07567-p130">テスト環境を作成し、できるだけ早く、必要なテストとデモを行います。完了したら、テスト環境のリソース グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="07567-p130">Create the test environment and perform your needed testing and demonstration as quickly as possible. When complete, delete the resource group for the test environment.</span></span>
    
- <span data-ttu-id="07567-261">テスト環境の仮想マシンをシャットダウンして、割り当てが解除された状態にします。</span><span class="sxs-lookup"><span data-stu-id="07567-261">Shut down your test environment virtual machines into a deallocated state.</span></span>
    
<span data-ttu-id="07567-262">Azure PowerShell で仮想マシンをシャットダウンするには、リソース グループ名を入力し、次のコマンドを実行してください。</span><span class="sxs-lookup"><span data-stu-id="07567-262">To shut down the virtual machines with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Stop-AzVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzVM -ResourceGroupName $rgName -Name "DC1" -Force
```

<span data-ttu-id="07567-263">すべての仮想マシンを停止 (割り当て解除) 状態から起動するときに正常に動作させるには、仮想マシンを次の順序で起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07567-263">To ensure that your virtual machines work properly when starting all of them from the Stopped (Deallocated) state, you should start them in the following order:</span></span>
  
1. <span data-ttu-id="07567-264">DC1</span><span class="sxs-lookup"><span data-stu-id="07567-264">DC1</span></span>
2. <span data-ttu-id="07567-265">APP1</span><span class="sxs-lookup"><span data-stu-id="07567-265">APP1</span></span>
3. <span data-ttu-id="07567-266">CLIENT1</span><span class="sxs-lookup"><span data-stu-id="07567-266">CLIENT1</span></span>
    
<span data-ttu-id="07567-267">Azure PowerShell で仮想マシンを順番に起動するには、リソース グループ名を入力し、次のコマンドを実行してください。</span><span class="sxs-lookup"><span data-stu-id="07567-267">To start the virtual machines in order with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Start-AzVM -ResourceGroupName $rgName -Name "DC1"
Start-AzVM -ResourceGroupName $rgName -Name "APP1"
Start-AzVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a><span data-ttu-id="07567-268">関連項目</span><span class="sxs-lookup"><span data-stu-id="07567-268">See Also</span></span>

- [<span data-ttu-id="07567-269">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="07567-269">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
- [<span data-ttu-id="07567-270">Office 365 開発/テスト環境の DirSync</span><span class="sxs-lookup"><span data-stu-id="07567-270">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="07567-271">Office 365 開発/テスト環境の Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="07567-271">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="07567-272">Office 365 開発/テスト環境の Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="07567-272">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="07567-273">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="07567-273">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
