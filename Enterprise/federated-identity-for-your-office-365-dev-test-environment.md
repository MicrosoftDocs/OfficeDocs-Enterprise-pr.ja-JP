---
title: Office 365 開発/テスト環境のフェデレーション ID
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: '概要: Office 365 開発/テスト環境に向けたフェデレーション認証を構成します。'
ms.openlocfilehash: c2cb4bcd9085cd8dd91df5de2ad936076d11432c
ms.sourcegitcommit: 74b6d9fc3ce0873e8564fc4de51fe3afeb122447
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "37207393"
---
# <a name="federated-identity-for-your-office-365-devtest-environment"></a><span data-ttu-id="d8ba5-103">Office 365 開発/テスト環境のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="d8ba5-103">Federated identity for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="d8ba5-104">**概要:** Office 365 開発/テスト環境に向けたフェデレーション認証を構成します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-104">**Summary:** Configure federated authentication for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="d8ba5-p101">Office 365 は、フェデレーション ID をサポートします。つまり、資格情報自体の検証を実行する代わりに、Office 365 は、接続しようとしているユーザーを、Office 365 が信頼するフェデレーション認証サーバーに照会します。ユーザーの資格情報が正しい場合、フェデレーション認証サーバーはセキュリティ トークンを発行し、次いでクライアントは認証の証明としてそのセキュリティ トークンを Office 365 に送信します。フェデレーション ID を使用すると、Office 365 サブスクリプションの認証のオフロードとスケールアップや、認証とセキュリティの高度なシナリオが可能になります。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-p101">Office 365 supports federated identity. This means that instead of performing the validation of credentials itself, Office 365 refers the connecting user to a federated authentication server that Office 365 trusts. If the user's credentials are correct, the federated authentication server issues a security token that the client then sends to Office 365 as proof of authentication. Federated identity allows for the offloading and scaling up of authentication for an Office 365 subscription and advanced authentication and security scenarios.</span></span>
  
<span data-ttu-id="d8ba5-109">この記事では、Office 365 開発/テスト環境用にフェデレーション認証を構成する方法について説明します。最終的に、この環境は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-109">This article describes how you can configure federated authentication for the Office 365 dev/test environment, resulting in the following:</span></span>
  
<span data-ttu-id="d8ba5-110">**図 1: Office 365 開発/テスト環境のフェデレーション認証**</span><span class="sxs-lookup"><span data-stu-id="d8ba5-110">**Figure 1: The federated authentication for Office 365 dev/test environment**</span></span>

![Office 365 開発/テスト環境のフェデレーション認証](media/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="d8ba5-112">図 1 に示す構成の内容は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-112">The configuration shown in Figure 1 consists of:</span></span> 
  
- <span data-ttu-id="d8ba5-113">Office 365 E5 試用版サブスクリプション。このサブスクリプションは、作成時から 30 日で有効期限が切れます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-113">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
    
- <span data-ttu-id="d8ba5-p102">インターネットに接続する組織の簡易型イントラネット。Azure 仮想ネットワークのサブネット上に配置された 5 つの仮想マシン (DC1、APP1、CLIENT1、ADFS1、PROXY1) で構成されます。APP1 では、Active Directory Domain Services ドメインのアカウントの一覧を Office 365 に同期するために Azure AD Connect が実行されます。PROXY1 は、受信認証要求を受信します。ADFS1 は、DC1 で資格情報を検証し、セキュリティ トークンを発行します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-p102">A simplified organization intranet connected to the Internet, consisting of five virtual machines on a subnet of an Azure virtual network (DC1, APP1, CLIENT1, ADFS1, and PROXY1). Azure AD Connect runs on APP1 to synchronize the list of accounts in the Active Directory Domain Services domain to Office 365. PROXY1 receives the incoming authentication requests. ADFS1 validates credentials with DC1 and issues security tokens.</span></span>
    
<span data-ttu-id="d8ba5-118">次に示す 5 つのフェーズで、この開発/テスト環境を設定します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-118">There are five phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="d8ba5-119">DirSync を使用する、シミュレートされたエンタープライズ Office 365 開発/テスト環境を作成する。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-119">Create the simulated enterprise Office 365 dev/test environment with DirSync.</span></span>
    
2. <span data-ttu-id="d8ba5-120">AD FS サーバー (ADFS1) を作成する。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-120">Create the AD FS server (ADFS1).</span></span>
    
3. <span data-ttu-id="d8ba5-121">Web プロキシ サーバー (PROXY1) を作成する。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-121">Create the web proxy server (PROXY1).</span></span>
    
4. <span data-ttu-id="d8ba5-122">自己署名証明書を作成し、ADFS1 と PROXY1 を構成する。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-122">Create a self-signed certificate and configure ADFS1 and PROXY1.</span></span>
    
5. <span data-ttu-id="d8ba5-123">フェデレーション ID に対応するよう Office 365 を構成する。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-123">Configure Office 365 for federated identity.</span></span>
    
<span data-ttu-id="d8ba5-124">Azure での Office 365 用のフェデレーション認証の運用環境デプロイメントの手順については、「[Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-124">To step through a production deployment of federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="d8ba5-125">Azure の試用版サブスクリプションで、この開発/テスト環境を構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-125">You cannot configure this dev/test environment with an Azure Trial subscription.</span></span> 
  
> [!TIP]
> <span data-ttu-id="d8ba5-126">[ここ](http://aka.ms/catlgstack)をクリックして、Office 365 のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-126">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-simulated-enterprise-office-365-devtest-environment-with-dirsync"></a><span data-ttu-id="d8ba5-127">フェーズ 1: DirSync を使用する、シミュレートされたエンタープライズ Office 365 開発/テスト環境を作成する</span><span class="sxs-lookup"><span data-stu-id="d8ba5-127">Phase 1: Create the simulated enterprise Office 365 dev/test environment with DirSync</span></span>

<span data-ttu-id="d8ba5-128">「[Office 365 開発/テスト環境のディレクトリ同期](dirsync-for-your-office-365-dev-test-environment.md)」の手順に従って、シミュレートされたエンタープライズ Office 365 開発/テスト環境を作成します。この環境では、APP1 を DirSync サーバーとし、ID の同期を Office 365 と DC1 上の AD DS アカウントとの間で行います。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-128">Follow the instructions in [Directory synchronization for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to create the simulated enterprise Office 365 dev/test environment with APP1 as the DirSync server and synchronized identity between Office 365 and the AD DS accounts on DC1.</span></span>
  
<span data-ttu-id="d8ba5-p103">次に、現在のドメイン名に基づいて新しいパブリック DNS ドメイン名を作成し、Office 365 サブスクリプションに追加します。**testlab.**\<パブリック ドメイン> という名前を使用することをお勧めします。たとえば、パブリック ドメイン名が contoso.com である場合は、パブリック ドメイン名 testlab.contoso.com を追加します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-p103">Next, create a new public DNS domain name based on your current domain name and add it to your Office 365 subscription. We recommend using the name **testlab.**\<your public domain>. For example, if your public domain name is contoso.com, add the public domain name testlab.contoso.com.</span></span>
  
<span data-ttu-id="d8ba5-132">DNS プロバイダーで適切な DNS レコードを作成して、ドメインを Office 365 試用版サブスクリプションに追加する方法の手順については、「[ドメインとユーザーを Office 365 に追加する](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-132">For instructions on how to create the correct DNS records in your DNS provider and add the domain to your Office 365 trial subscription, see [Add users and domain to Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).</span></span> 
  
<span data-ttu-id="d8ba5-133">最終的な構成をここに示します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-133">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="d8ba5-134">**図 2: Office 365 開発/テスト環境のディレクトリ同期**</span><span class="sxs-lookup"><span data-stu-id="d8ba5-134">**Figure 2: Directory synchronization for the Office 365 dev/test environment**</span></span>

![ディレクトリ同期を使用した Office 365 開発/テスト環境](media/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="d8ba5-136">図 2 は、Office 365 開発/テスト環境のディレクトリ同期を示しています。この図には、Office 365 と、Azure 仮想ネットワーク内の CLIENT1、APP1、DC1 の各仮想マシンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-136">Figure 2 shows the directory synchronizationc for Office 365 dev/test environment, which includes Office 365 and CLIENT1, APP1, and DC1 virtual machines in an Azure virtual network.</span></span>
  
## <a name="phase-2-create-the-ad-fs-server"></a><span data-ttu-id="d8ba5-137">フェーズ 2: AD FS サーバーを作成する</span><span class="sxs-lookup"><span data-stu-id="d8ba5-137">Phase 2: Create the AD FS server</span></span>

<span data-ttu-id="d8ba5-138">AD FS サーバーは、Office 365 と、DC1 でホストされている corp.contoso.com ドメイン内のアカウントとの間でのフェデレーション認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-138">An AD FS server provides federated authentication between Office 365 and the accounts in the corp.contoso.com domain hosted on DC1.</span></span>
  
<span data-ttu-id="d8ba5-139">ADFS1 用の Azure 仮想マシンを作成するには、基本構成のサブスクリプション名、リソース グループ名、Azure の場所を入力して、次のコマンドをローカル コンピューターの Azure PowerShell コマンド プロンプトで実行します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-139">To create an Azure virtual machine for ADFS1, fill in the name of your subscription and the resource group and Azure location for your Base Configuration, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$subscrName="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
Connect-AzAccount
Select-AzSubscription -SubscriptionName $subscrName
$staticIP="10.0.0.100"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```
<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0) for a text file that has all the PowerShell commands in this article.
-->
  
<span data-ttu-id="d8ba5-140">次に、[Azure portal](http://portal.azure.com) で、ADFS1 のローカル管理者アカウント名とパスワードを使用して ADFS1 仮想マシンに接続し、Windows PowerShell コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-140">Next, use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the ADFS1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="d8ba5-141">ADFS1 と DC1 の間の名前の解決とネットワーク通信を確認するには、**ping dc1.corp.contoso.com** コマンドを実行し、4 つの応答があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-141">To check name resolution and network communication between ADFS1 and DC1, run the **ping dc1.corp.contoso.com** command and check that there are four replies.</span></span>
  
<span data-ttu-id="d8ba5-142">次に、ADFS1 の Windows PowerShell プロンプトで次のコマンドを使用して、ADFS1 仮想マシンを CORP ドメインに参加させます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-142">Next, join the ADFS1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on ADFS1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="d8ba5-143">最終的な構成をここに示します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-143">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="d8ba5-144">**図 3: AD FS サーバーの追加**</span><span class="sxs-lookup"><span data-stu-id="d8ba5-144">**Figure 3: Adding the AD FS server**</span></span>

![Office 365 開発/テスト環境の DirSync に追加された AD FS サーバー](media/da82f39e-426d-41e2-842a-c13b382d63d5.png)
  
<span data-ttu-id="d8ba5-146">図 3 は、Office 365 開発/テスト環境の DirSync に ADFS1 サーバーが追加されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-146">Figure 3 shows the addition of the ADFS1 server to the DirSync for Office 365 dev/test environment.</span></span>
  
## <a name="phase-3-create-the-web-proxy-server"></a><span data-ttu-id="d8ba5-147">フェーズ 3：Web プロキシ サーバーを作成する</span><span class="sxs-lookup"><span data-stu-id="d8ba5-147">Phase 3: Create the web proxy server</span></span>

<span data-ttu-id="d8ba5-148">PROXY1 は、認証しようとするユーザーと ADFS1 との間の認証メッセージのプロキシを提供します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-148">PROXY1 provides proxying of authentication messages between users trying to authenticate and ADFS1.</span></span>
  
<span data-ttu-id="d8ba5-149">PROXY1 用の Azure 仮想マシンを作成するには、リソース グループ名と Azure の場所を入力し、次のコマンドをローカル コンピューターの Azure PowerShell コマンド プロンプトで実行します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-149">To create an Azure virtual machine for PROXY1, fill in the name of your resource group and Azure location, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
$staticIP="10.0.0.101"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="d8ba5-150">PROXY1 には静的パブリック IP アドレスが割り当てられます。この IP アドレスを指すパブリック DNS レコードが作成され、PROXY1 仮想マシンを再起動するときにこの IP アドレスを変更することはできないためです。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-150">PROXY1 is assigned a static public IP address because you will create a public DNS record that points to it and it must not change when you restart the PROXY1 virtual machine.</span></span> 
  
<span data-ttu-id="d8ba5-p104">次に、CorpNet サブネットのネットワーク セキュリティ グループにルールを追加して、インターネットから PROXY1 のプライベート IP アドレスおよび TCP ポート 443 に着信する、受信者側が送信を要求していないトラフィックを許可します。ローカル コンピューターの Azure PowerShell コマンド プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-p104">Next, add a rule to the network security group for the CorpNet subnet to allow unsolicited inbound traffic from the Internet to PROXY1's private IP address and TCP port 443. Run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<the resource group name of your Base Configuration>"
Get-AzNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzNetworkSecurityGroup
```

<span data-ttu-id="d8ba5-153">次に、[Azure portal](http://portal.azure.com) で、PROXY1 のローカル管理者アカウント名とパスワードを使用して PROXY1 仮想マシンに接続し、PROXY1 で Windows PowerShell コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-153">Next, use the [Azure portal](http://portal.azure.com) to connect to the PROXY1 virtual machine using the PROXY1 local administrator account name and password, and then open a Windows PowerShell command prompt on PROXY1.</span></span>
  
<span data-ttu-id="d8ba5-154">PROXY1 と DC1 の間の名前の解決とネットワーク通信を確認するには、**ping dc1.corp.contoso.com** コマンドを実行し、4 つの応答があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-154">To check name resolution and network communication between PROXY1 and DC1, run the **ping dc1.corp.contoso.com** command and check that there are four replies.</span></span>
  
<span data-ttu-id="d8ba5-155">次に、PROXY1 の Windows PowerShell プロンプトで次のコマンドを使用して、PROXY1 仮想マシンを CORP ドメインに参加させます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-155">Next, join the PROXY1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on PROXY1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="d8ba5-156">ローカル コンピューターで次の Azure PowerShell コマンドを使用して、PROXY1 のパブリック IP アドレスを表示します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-156">Display the public IP address of PROXY1 with these Azure PowerShell commands on your local computer:</span></span>
  
```
Write-Host (Get-AzPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

<span data-ttu-id="d8ba5-p105">次に、パブリック DNS プロバイダーを操作して、**Write-Host** コマンドで表示される IP アドレスに解決される、**fs.testlab.**\<DNS ドメイン名> 用の新しいパブリック DNS A レコードを作成します。これ以降、**fs.testlab.**\<DNS ドメイン名> を*フェデレーション サービス FQDN* と呼びます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-p105">Next, work with your public DNS provider and create a new public DNS A record for **fs.testlab.**\<your DNS domain name> that resolves to the IP address displayed by the **Write-Host** command. The **fs.testlab.**\<your DNS domain name> is hereafter referred to as the  *federation service FQDN*  .</span></span>
  
<span data-ttu-id="d8ba5-159">次に、[Azure portal](http://portal.azure.com) で、CORP\\User1 の資格情報を使用して DC1 仮想マシンに接続し、管理者レベルの Windows PowerShell コマンド プロンプトで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-159">Next, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then run the following commands at an administrator-level Windows PowerShell command prompt:</span></span>
  
```
Add-DnsServerPrimaryZone -Name corp.contoso.com -ZoneFile corp.contoso.com.dns
Add-DnsServerResourceRecordA -Name "fs" -ZoneName corp.contoso.com -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```
<span data-ttu-id="d8ba5-160">これらのコマンドは、内部 DNS A レコードを作成します。これにより、Azure 仮想ネットワーク上の仮想マシンは内部フェデレーション FQDN を、ADFS1 のプライベート IP アドレスに解決できます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-160">These commands create a DNS A record for your federation service FQDN that virtual machines on the Azure virtual network can resolve to ADFS1's private IP address.</span></span>
  
<span data-ttu-id="d8ba5-161">最終的な構成をここに示します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-161">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="d8ba5-162">**図 4: Web アプリケーション プロキシ サーバーの追加**</span><span class="sxs-lookup"><span data-stu-id="d8ba5-162">**Figure 4: Adding the web application proxy server**</span></span>

![Office 365 開発/テスト環境の DirSync に追加された Web アプリケーション プロキシ サーバー](media/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="d8ba5-164">図 4 は、PROXY1 サーバーの追加を示しています。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-164">Figure 4 shows the addition of the PROXY1 server.</span></span>
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a><span data-ttu-id="d8ba5-165">フェーズ 4:自己署名証明書を作成し、ADFS1 と PROXY1 を構成する</span><span class="sxs-lookup"><span data-stu-id="d8ba5-165">Phase 4: Create a self-signed certificate and configure ADFS1 and PROXY1</span></span>

<span data-ttu-id="d8ba5-166">このフェーズでは、フェデレーション サービス FQDN 用の自己署名入りデジタル証明書を作成し、ADFS1 と PROXY1 を AD FS ファームとして構成します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-166">In this phase, you create a self-signed digital certificate for your federation service FQDN and configure ADFS1 and PROXY1 as an AD FS farm.</span></span>
  
<span data-ttu-id="d8ba5-167">まず、[Azure portal](http://portal.azure.com) で、CORP\\User1 の資格情報を使用して DC1 仮想マシンに接続し、管理者レベルの Windows PowerShell コマンド プロンプトを開きます。 </span><span class="sxs-lookup"><span data-stu-id="d8ba5-167">First, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="d8ba5-168">次に、DC1 の Windows PowerShell コマンド プロンプトで次のコマンドを使用して、AD FS サービス アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-168">Next, create AD FS service account with this command at the Windows PowerShell command prompt on DC1:</span></span>
  
```
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="d8ba5-p106">このコマンドでは、アカウントのパスワードを入力するよう求められることにご注意ください。強力なパスワードを選択して、安全な場所に記録してください。このパスワードは、このフェーズとフェーズ 5 で必要になります。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-p106">Note that this command prompts you to supply the account password. Choose a strong password and record it in a secured location. You will need it for this phase and Phase 5.</span></span>
  
<span data-ttu-id="d8ba5-p107">[Azure portal](http://portal.azure.com) で CORP\\User1 の資格情報を使用して、ADFS1 仮想マシンに接続します。ADFS1 で管理者レベルの Windows PowerShell コマンド プロンプトを開き、フェデレーション サービス FQDN を入力し、次のコマンドを実行して自己署名証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-p107">Use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the CORP\\User1 credentials. Open an administrator-level Windows PowerShell command prompt on ADFS1, fill in your federation service FQDN, and then run these commands to create a self-signed certificate:</span></span>
  
```
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

<span data-ttu-id="d8ba5-174">その次に、次の手順を使用して新しい自己署名証明書をファイルとして保存します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-174">Next, use these steps to save the new self-signed certificate as a file.</span></span>
  
1. <span data-ttu-id="d8ba5-175">**[スタート]** をクリックして、「**mmc.exe**」と入力し、**Enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-175">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="d8ba5-176">**[ファイル] > [スナップインの追加と削除]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-176">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="d8ba5-177">**[スナップインの追加と削除]** で、利用できるスナップインの一覧の **[証明書]** をダブルクリックして、**[コンピューター アカウント]**、**[次へ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-177">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="d8ba5-178">**[コンピューターの選択]** で、**[完了]**、**[OK]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-178">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="d8ba5-179">ツリー ウィンドウで、**[証明書 (ローカル コンピューター)] > [個人] > [証明書]** の順に開きます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-179">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="d8ba5-180">フェデレーション サービス FQDN を含む証明書を右クリックし、**[すべてのタスク]**、**[エクスポート]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-180">Right-click the certificate with your federation service FQDN, click **All tasks**, and then click **Export**.</span></span>
    
7. <span data-ttu-id="d8ba5-181">**[ようこそ]** ページで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-181">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="d8ba5-182">**[秘密キーのエクスポート]** ページで、**[はい]**、**[次へ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-182">On the **Export Private Key** page, click **Yes**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="d8ba5-183">**[エクスポート ファイルの形式]** ページで、**[すべての拡張プロパティをエクスポートする]**、**[次へ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-183">On the **Export File Format** page, click **Export all extended properties**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="d8ba5-184">**[セキュリティ]** ページで、**[パスワード]** をクリックして、**[パスワード]** と **[パスワードの確認入力]** にパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-184">On the **Security** page, click **Password** and type a password in **Password** and **Confirm password.**</span></span>
    
11. <span data-ttu-id="d8ba5-185">**[エクスポートするファイル]** ページで、**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-185">On the **File to Export** page, click **Browse**.</span></span>
    
12. <span data-ttu-id="d8ba5-186">**C:\\Certs** フォルダーを参照して、**[ファイル名]** に「**SSL**」と入力し、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-186">Browse to the **C:\\Certs** folder, type **SSL** in **File name**, and then click **Save.**</span></span>
    
13. <span data-ttu-id="d8ba5-187">**[エクスポートするファイル]** ページで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-187">On the **File to Export** page, click **Next**.</span></span>
    
14. <span data-ttu-id="d8ba5-p108">**[証明書のエクスポート ウィザードの完了]** ページで、**[完了]** をクリックします。ダイアログが表示されたら、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-p108">On the **Completing the Certificate Export Wizard** page, click **Finish**. When prompted, click **OK**.</span></span>
    
<span data-ttu-id="d8ba5-190">次に、ADFS1 の Windows PowerShell コマンド プロンプトで次のコマンドを使用して、AD FS サービスをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-190">Next, install the AD FS service with this command at the Windows PowerShell command prompt on ADFS1:</span></span>
  
```
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

<span data-ttu-id="d8ba5-191">インストールが完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-191">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="d8ba5-192">次いで、次の手順で AD FS サービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-192">Next, configure the AD FS service with these steps:</span></span>
  
1. <span data-ttu-id="d8ba5-193">**[スタート]** をクリックして、**[サーバー マネージャー]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-193">Click **Start**, and then click the **Server Manager** icon.</span></span>
    
2. <span data-ttu-id="d8ba5-194">サーバー マネージャーのツリー ウィンドウで、**[AD FS]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-194">In the tree pane of Server Manager, click **AD FS**.</span></span>
    
3. <span data-ttu-id="d8ba5-195">上部にあるツール バーで、オレンジ色の警告マークをクリックし、**[このサーバーにフェデレーション サービスを構成します]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-195">In the tool bar at the top, click the orange caution symbol, and then click **Configure the federation service on this server**.</span></span>
    
4. <span data-ttu-id="d8ba5-196">Active Directory フェデレーション サービス構成ウィザードの **[ようこそ]** ページで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-196">On the **Welcome** page of the Active Directory Federation Services Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="d8ba5-197">**[AD DS に接続]** ページで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-197">On the **Connect to AD DS** page, click **Next**.</span></span>
    
6. <span data-ttu-id="d8ba5-198">**[サービスのプロパティの指定]** ページで、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-198">On the **Specify Service Properties** page:</span></span>
    
  - <span data-ttu-id="d8ba5-199">**[SSL 証明書]** で、下向き矢印をクリックし、フェデレーション サービス FQDN の名前を含む証明書をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-199">For **SSL Certificate**, click the down arrow, and then click the certificate with the name of your federation service FQDN.</span></span>
    
  - <span data-ttu-id="d8ba5-200">**[フェデレーション サービスの表示名]** で、架空の組織名を入力します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-200">In **Federation Service Display Name**, type the name of your fictional organization.</span></span>
    
  - <span data-ttu-id="d8ba5-201">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-201">Click **Next**.</span></span>
    
7. <span data-ttu-id="d8ba5-202">**[サービス アカウントの指定]** ページで、**[アカウント名]** の **[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-202">On the **Specify Service Account** page, click **Select** for **Account name**.</span></span>
    
8. <span data-ttu-id="d8ba5-203">**[ユーザーまたはサービス アカウントの選択]** で、「**ADFS-Service**」と入力して、**[名前の確認]**、**[OK]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-203">In **Select User or Service Account**, type **ADFS-Service**, click **Check Names**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="d8ba5-204">**[アカウントのパスワード]** で、ADFS-Service アカウントのパスワードを入力して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-204">In **Account Password**, type the password for the ADFS-Service account, and then click **Next**.</span></span>
    
10. <span data-ttu-id="d8ba5-205">**[構成データベースの指定]** ページで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-205">On the **Specify Configuration Database** page, click **Next**.</span></span>
    
11. <span data-ttu-id="d8ba5-206">**[オプションの確認]** ページで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-206">On the **Review Options** page, click **Next**.</span></span>
    
12. <span data-ttu-id="d8ba5-207">**[前提条件の確認]** ページで、**[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-207">On the **Pre-requisite Checks** page, click **Configure**.</span></span>
    
13. <span data-ttu-id="d8ba5-208">**[結果]** ページで、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-208">On the **Results** page, click **Close**.</span></span>
    
14. <span data-ttu-id="d8ba5-209">**[スタート]** をクリックして、電源アイコン、**[再起動]**、**[続行]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-209">Click **Start**, click the power icon, click **Restart**, and then click **Continue**.</span></span>
    
<span data-ttu-id="d8ba5-210">[Azure portal](http://portal.azure.com) から、CORP\\User1 アカウントの資格情報を使用して PROXY1 に接続します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-210">From the [Azure portal](http://portal.azure.com), connect to PROXY1 with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="d8ba5-211">その次に、次の手順を使用して、自己署名証明書をインストールし、PROXY1 を構成します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-211">Next, use these steps to install the self-signed certificate and configure PROXY1.</span></span>
  
1. <span data-ttu-id="d8ba5-212">**[スタート]** をクリックして、「**mmc.exe**」と入力し、**Enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-212">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="d8ba5-213">**[ファイル] > [スナップインの追加と削除]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-213">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="d8ba5-214">**[スナップインの追加と削除]** で、利用できるスナップインの一覧の **[証明書]** をダブルクリックして、**[コンピューター アカウント]**、**[次へ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-214">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="d8ba5-215">**[コンピューターの選択]** で、**[完了]**、**[OK]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-215">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="d8ba5-216">ツリー ウィンドウで、**[証明書 (ローカル コンピューター)] > [個人] > [証明書]** の順に開きます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-216">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="d8ba5-217">**[個人]** を右クリックして、**[すべてのタスク]**、**[インポート]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-217">Right-click **Personal**, click **All tasks**, and then click **Import**.</span></span>
    
7. <span data-ttu-id="d8ba5-218">**[ようこそ]** ページで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-218">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="d8ba5-219">**[インポートする証明書ファイル]** ページで、「**\\\\adfs1\\certs\\ssl.pfx**」と入力し、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-219">On the **File to Import** page, type **\\\\adfs1\\certs\\ssl.pfx**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="d8ba5-220">**[秘密キーの保護]** ページで、**[パスワード]** に証明書のパスワードを入力して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-220">On the **Private key protection** page, type the certificate password in **Password**, and then click **Next.**</span></span>
    
10. <span data-ttu-id="d8ba5-221">**[証明書ストア]** ページで **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-221">On the **Certificate store** page, click **Next.**</span></span>
    
11. <span data-ttu-id="d8ba5-222">**[完了]** ページで、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-222">On the **Completing** page, click **Finish**.</span></span>
    
12. <span data-ttu-id="d8ba5-223">**[証明書ストア]** ページで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-223">On the **Certificate Store** page, click **Next**.</span></span>
    
13. <span data-ttu-id="d8ba5-224">ダイアログが表示されたら、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-224">When prompted, click **OK**.</span></span>
    
14. <span data-ttu-id="d8ba5-225">ツリー ウィンドウで、**[証明書]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-225">Click **Certificates** in the tree pane.</span></span>
    
15. <span data-ttu-id="d8ba5-226">証明書を右クリックして、**[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-226">Right-click the certificate, and then click **Copy**.</span></span>
    
16. <span data-ttu-id="d8ba5-227">ツリー ウィンドウで、**[信頼されたルート証明機関] > [証明書]** の順に開きます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-227">In the tree pane, open **Trusted Root Certification Authorities > Certificates**.</span></span>
    
17. <span data-ttu-id="d8ba5-228">インストールされている証明書の一覧の下にマウス ポインターを移動し、右クリックして、**[貼り付け]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-228">Move your mouse pointer below the list of installed certificates, right-click, and then click **Paste**.</span></span>
    
<span data-ttu-id="d8ba5-229">管理者レベルの PowerShell コマンド プロンプトを開き、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-229">Open an administrator-level PowerShell command prompt and run the following command:</span></span>
  
```
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

<span data-ttu-id="d8ba5-230">インストールが完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-230">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="d8ba5-231">次の手順を使用して、Web アプリケーション プロキシ サービスを構成し、そのフェデレーション サーバーとして ADFS1 を使用します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-231">Use these steps to configure the web application proxy service to use ADFS1 as its federation server:</span></span>
  
1. <span data-ttu-id="d8ba5-232">**[スタート]** をクリックしてから、**[サーバー マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-232">Click **Start**, and then click **Server Manager**.</span></span>
    
2. <span data-ttu-id="d8ba5-233">ツリー ウィンドウで、**[リモート アクセス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-233">In the tree pane, click **Remote Access**.</span></span>
    
3. <span data-ttu-id="d8ba5-234">上部にあるツール バーで、オレンジ色の警告マークをクリックし、**[Web アプリケーション プロキシ ウィザードを表示する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-234">In the tool bar at the top, click the orange caution symbol, and then click **Open the Web Application Proxy Wizard**.</span></span>
    
4. <span data-ttu-id="d8ba5-235">Web アプリケーション プロキシ構成ウィザードの **[ようこそ]** ページで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-235">On the **Welcome** page of the Web Application Proxy Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="d8ba5-236">**[フェデレーション サーバー]** ページで、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-236">On the **Federation Server** page:</span></span>
    
  - <span data-ttu-id="d8ba5-237">**[フェデレーション サービス名]** にフェデレーション サービス FQDN を入力します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-237">Type your federation service FQDN in **Federation service name**.</span></span>
    
  - <span data-ttu-id="d8ba5-238">**[ユーザー名]** に「**CORP\\User1**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-238">Type **CORP\\User1** in **User name**.</span></span>
    
  - <span data-ttu-id="d8ba5-239">**[パスワード]** に User1 アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-239">Type the password for the User1 account in **Password**.</span></span>
    
  - <span data-ttu-id="d8ba5-240">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-240">Click **Next**.</span></span>
    
6. <span data-ttu-id="d8ba5-241">**[AD FS プロキシ証明書]** ページで、下向き矢印をクリックし、フェデレーション サービス FQDN を含む証明書をクリックして、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-241">On the **AD FS Proxy Certificate** page, click the down arrow, click the certificate with your federation service FQDN, and then click **Next**.</span></span>
    
7. <span data-ttu-id="d8ba5-242">**[確認]** ページで、**[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-242">On the **Confirmation** page, click **Configure**.</span></span>
    
8. <span data-ttu-id="d8ba5-243">**[結果]** ページで、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-243">On the **Results** page, click **Close**.</span></span>
    
## <a name="phase-5-configure-office-365-for-federated-identity"></a><span data-ttu-id="d8ba5-244">フェーズ 5: フェデレーション ID に対応するよう Office 365 を構成する</span><span class="sxs-lookup"><span data-stu-id="d8ba5-244">Phase 5: Configure Office 365 for federated identity</span></span>

<span data-ttu-id="d8ba5-245">[Azure portal](http://portal.azure.com) を使用して、CORP\\User1 アカウントの資格情報で APP1 仮想マシンに接続します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-245">Use the [Azure portal](http://portal.azure.com) to connect to the APP1 virtual machine with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="d8ba5-246">次の手順を使用して、フェデレーション認証に対応するように Azure AD Connect と Office 365 サブスクリプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-246">Use these steps to configure Azure AD Connect and your Office 365 subscription for federated authentication:</span></span>
  
1. <span data-ttu-id="d8ba5-247">デスクトップで、**[Azure AD Connect]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-247">From the desktop, double-click **Azure AD Connect**.</span></span>
    
2. <span data-ttu-id="d8ba5-248">**[Azure AD Connect へようこそ]** ページで、**[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-248">On the **Welcome to Azure AD Connect** page, click **Configure**.</span></span>
    
3. <span data-ttu-id="d8ba5-249">**[追加のタスク]** ページで、**[ユーザー サインインの変更]**、**[次へ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-249">On the **Additional tasks** page, click **Change user sign-in**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="d8ba5-250">**[Azure AD に接続]** ページで、Office 365 全体管理者のアカウント名とパスワードを入力して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-250">On the **Connect to Azure AD** page, type your Office 365 global administrator account name and password, and then click **Next**.</span></span>
    
5. <span data-ttu-id="d8ba5-251">**[ユーザー サインイン]** ページで、**[AD FS とのフェデレーション]** をクリックしてから、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-251">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="d8ba5-252">**[AD FS ファーム]** ページで、**[既存の AD FS のファームを使用する]** をクリックして、**[サーバー名]** に「**ADFS1**」と入力し、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-252">On the **AD FS farm** page, click **Use an existing AD FS farm**, type **ADFS1** in **Server Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="d8ba5-253">サーバーの資格情報の入力を求められたら、CORP\\User1 アカウントの資格情報を入力し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-253">When prompted for server credentials, enter the credentials of the CORP\\User1 account, and then click **OK**.</span></span>
    
8. <span data-ttu-id="d8ba5-254">**[ドメイン管理者]** の資格情報ページで、**[ユーザー名]** に「**CORP\\User1**」と入力し、**[パスワード]** にアカウントのパスワードを入力して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-254">On the **Domain Administrator** credentials page, type **CORP\\User1** in **Username** and the account password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="d8ba5-255">**[AD FS サービス アカウント]** ページで、**[ドメイン ユーザー名]** に「**CORP\\ADFS-Service**」を入力し、**[ドメイン ユーザー パスワード]** にアカウントのパスワードを入力して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-255">On the **AD FS service account** page, type **CORP\\ADFS-Service** in **Domain Username** and the account password in **Domain User Password**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="d8ba5-256">**[Azure AD Domain]** ページの **[ドメイン]** で、あらかじめフェーズ 1 で作成して、Office 365 サブスクリプションに追加したドメイン名を選択して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-256">On the **Azure AD Domain** page, in **Domain**, select the name of the domain you previously created and added to your Office 365 subscription in Phase 1, and then click **Next**.</span></span>
    
11. <span data-ttu-id="d8ba5-257">**[構成の準備完了]** ページで、**[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-257">On the **Ready to configure** page, click **Configure**.</span></span>
    
12. <span data-ttu-id="d8ba5-258">**[インストールの完了]** ページで、**[確認]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-258">On the **Installation complete** page, click **Verify**.</span></span>
    
    <span data-ttu-id="d8ba5-259">イントラネット構成とインターネット構成の両方が確認されたことを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-259">You should see messages indicating that both the intranet and Internet configuration was verified.</span></span>
    
13. <span data-ttu-id="d8ba5-260">**[インストールの完了]** ページで、**[終了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-260">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="d8ba5-261">フェデレーション認証が機能していることを実証するには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-261">To demonstrate that federated authentication is working:</span></span>
  
1. <span data-ttu-id="d8ba5-262">ローカル コンピューター上でブラウザーの新しいプライベート インスタンスを開き、[https://admin.microsoft.com](https://admin.microsoft.com) にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-262">Open a new private instance of your browser on your local computer and go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
2. <span data-ttu-id="d8ba5-263">サインイン資格情報に、**user1@**\<フェース 1 で作成したドメイン> を入力します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-263">For the sign-in credentials, type **user1@**\<the domain created in Phase 1>.</span></span> 
    
    <span data-ttu-id="d8ba5-p109">たとえば、テスト ドメインが **testlab.contoso.com** の場合は、「user1@testlab.contoso.com」と入力します。TAB キーを押すか、Office 365 に自動的にリダイレクトさせます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-p109">For example, if your test domain is testlab.contoso.com, you would type user1@testlab.contoso.com. Press TAB or allow Office 365 to automatically redirect you.</span></span>
    
    <span data-ttu-id="d8ba5-p110">**[この接続ではプライバシーが保護されません]** ページが表示されます。これが表示されるのは、デスクトップ コンピューターで検証できない自己署名証明書を ADFS1 にインストールしたためです。フェデレーション認証の運用環境デプロイメントでは、信頼された証明機関からの証明書を使用するため、ユーザーにこのページは表示されません。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-p110">You should now see a **Your connection is not private** page. You are seeing this because you installed a self-signed certificate on ADFS1 that your desktop computer cannot validate. In a production deployment of federated authentication, you would use a certificate from a trusted certification authority and your users would not see this page.</span></span>
    
3. <span data-ttu-id="d8ba5-269">**[この接続ではプライバシーが保護されません]** ページで、**[詳細設定]**、**[\<フェデレーション サービス FQDN> に進む]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-269">On the **Your connection is not private** page, click **Advanced**, and then click **Proceed to \<your federation service FQDN>**.</span></span> 
    
4. <span data-ttu-id="d8ba5-270">架空の組織名のページで、次を使用してサインインします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-270">On the page with the name of your fictional organization, sign in with the following:</span></span>
    
  - <span data-ttu-id="d8ba5-271">名前: **CORP\\User1**</span><span class="sxs-lookup"><span data-stu-id="d8ba5-271">**CORP\\User1** for the name</span></span>
    
  - <span data-ttu-id="d8ba5-272">User1 アカウントのパスワード</span><span class="sxs-lookup"><span data-stu-id="d8ba5-272">The password for the User1 account</span></span>
    
    <span data-ttu-id="d8ba5-273">**[Microsoft Office Home]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-273">You should see the **Microsoft Office Home** page.</span></span>
    
<span data-ttu-id="d8ba5-p111">次の手順で、Office 365 試用版サブスクリプションが、DC1 上でホストされている AD DS corp.contoso.com ドメインとフェデレーションされていることを実証します。認証プロセスに関する基本事項を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-p111">This procedure demonstrates that your Office 365 trial subscription is federated with the AD DS corp.contoso.com domain hosted on DC1. Here are the basics of the authentication process:</span></span>
  
1. <span data-ttu-id="d8ba5-276">フェーズ 1 で作成したフェデレーション ドメインをサインイン アカウント名で使用すると、Office 365 はブラウザーをフェデレーション サービス FQDN と PROXY1 にリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-276">When you use the federated domain that you created in Phase 1 within the sign-in account name, Office 365 redirects your browser to your federation service FQDN and PROXY1.</span></span>
    
2. <span data-ttu-id="d8ba5-277">PROXY1 は、ローカル コンピューターに架空の会社のサインイン ページを送信します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-277">PROXY1 sends your local computer the fictional company sign-in page.</span></span>
    
3. <span data-ttu-id="d8ba5-278">CORP\\User1 とパスワードを PROXY1 に送信すると、それらは ADFS1 に転送されます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-278">When you send CORP\\User1 and the password to PROXY1, it forwards them to ADFS1.</span></span>
    
4. <span data-ttu-id="d8ba5-279">ADFS1 は、DC1 を使用して CORP\\User1 とパスワードを検証し、ローカル コンピューターにセキュリティ トークンを送信します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-279">ADFS1 validates CORP\\User1 and the password with DC1 and sends your local computer a security token.</span></span>
    
5. <span data-ttu-id="d8ba5-280">ローカル コンピューターは、セキュリティ トークンを Office 365 に送信します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-280">Your local computer sends the security token to Office 365.</span></span>
    
6. <span data-ttu-id="d8ba5-281">Office 365 は、セキュリティ トークンが ADFS1 によって作成されたことを検証して、アクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-281">Office 365 validates that the security token was created by ADFS1 and allows access.</span></span>
    
<span data-ttu-id="d8ba5-p112">これで、Office 365 試用版のサブスクリプションがフェデレーション認証を行うように構成されました。この開発/テスト環境は、高度な認証シナリオで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-p112">Your Office 365 trial subscription is now configured with federated authentication. You can use this dev/test environment for advanced authentication scenarios.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="d8ba5-284">次の手順</span><span class="sxs-lookup"><span data-stu-id="d8ba5-284">Next Step</span></span>

<span data-ttu-id="d8ba5-285">Azure で Office 365 に対する運用環境対応の高可用性フェデレーション認証をデプロイする準備が整っている場合は、「[Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8ba5-285">When you are ready to deploy production-ready, high availability federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d8ba5-286">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8ba5-286">See Also</span></span>

[<span data-ttu-id="d8ba5-287">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="d8ba5-287">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="d8ba5-288">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="d8ba5-288">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="d8ba5-289">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="d8ba5-289">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="d8ba5-290">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="d8ba5-290">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="d8ba5-291">Azure に Office 365 の高可用性フェデレーション認証を展開する</span><span class="sxs-lookup"><span data-stu-id="d8ba5-291">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)


