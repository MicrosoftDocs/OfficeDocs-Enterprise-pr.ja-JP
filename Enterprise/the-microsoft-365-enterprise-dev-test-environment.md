---
title: Microsoft 365 Enterprise 開発/テスト環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: 概要:このテスト ラボ ガイドを使用して、Office 365 E5、Enterprise Mobility + Security (EMS) E5、Windows 10 Enterprise を実行しているコンピューターなどの開発/テスト環境を作成します。
ms.openlocfilehash: 5a4c23b3bde309a75a61e574e91823ecdd4629fe
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="3b42a-103">Microsoft 365 Enterprise 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="3b42a-103">The Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="3b42a-104">**概要:** このテスト ラボ ガイドを使用して、Office 365 E5、Enterprise Mobility + Security (EMS) E5、Windows 10 Enterprise を実行しているコンピューターなどの開発/テスト環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="3b42a-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes Office 365 E5, Enterprise Mobility + Security (EMS) E5, and a computer running Windows 10 Enterprise.</span></span>
  
<span data-ttu-id="3b42a-105">この記事では、[Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise) のフィーチャーと機能をテストするためのシンプルな環境を作成するための詳しい手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="3b42a-105">This article provides you with step-by-step instructions to create a simplified environment to test the features and functionality of Microsoft 365 Enterprise.</span></span>
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a><span data-ttu-id="3b42a-106">フェーズ 1: Office 365 E5 サブスクリプションを作成する</span><span class="sxs-lookup"><span data-stu-id="3b42a-106">Phase 1: Create your Office 365 E5 subscription</span></span>

<span data-ttu-id="3b42a-107">「[Office 365 開発/テスト環境](office-365-dev-test-environment.md)」のフェーズ 2 とフェーズ 3 の手順に従って、図 1 に示すように、Office 365 の軽量な開発/テスト環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="3b42a-107">Follow the steps in Phase 2 and Phase 3 of Office 365 dev/test environment to create a lightweight Office 365 dev/test environment, as shown in Figure 1.</span></span>
  
<span data-ttu-id="3b42a-108">**図 1: Azure Active Directory (AD) のテナントとユーザー アカウントの Office 365 E5 サブスクリプション**</span><span class="sxs-lookup"><span data-stu-id="3b42a-108">**Figure 1: Your Office 365 E5 subscription with its Azure Active Directory (AD) tenant and user accounts**</span></span>

![Microsoft 3656 Enterprise 開発/テスト環境のフェーズ 1](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)

> [!NOTE]
> <span data-ttu-id="3b42a-p101">Office 365 E5 試用版サブスクリプションの試用期間は 30 日間です。この試用期間は簡単に 60 日間にまで延長できます。永続的な開発/テスト環境については、少数のライセンスが付いた新しい有料サブスクリプションを作成してください。</span><span class="sxs-lookup"><span data-stu-id="3b42a-p101">The Azure trial  is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="3b42a-112">フェーズ 2: EMS を追加する</span><span class="sxs-lookup"><span data-stu-id="3b42a-112">Phase 2: Add EMS</span></span>

<span data-ttu-id="3b42a-113">このフェーズでは、EMS E5 試用版サブスクリプションにサインアップして、Office 365 E5 試用版サブスクリプションと同じ組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="3b42a-113">In this phase, you sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 E5 trial subscription.</span></span>
  
<span data-ttu-id="3b42a-114">最初に、EMS E5 試用版サブスクリプションを追加して、EMS ライセンスを全体管理者アカウントに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="3b42a-114">First, add the EMS E5 trial subscription and assign an EMS license to your global administrator account.</span></span>
  
1. <span data-ttu-id="3b42a-p102">インターネット ブラウザーのプライベート インスタンスで、全体管理者アカウントの資格情報を使用して、Office 365 ポータルにサインインします。ヘルプについては、「[Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b42a-p102">With a private instance of an Internet browser, sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="3b42a-117">**[管理]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-117">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="3b42a-118">ブラウザーの **[Office 管理センター]** タブの左側のナビゲーションで **[請求] > [サービスを購入する]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-118">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="3b42a-p103">**[サービスを購入]** ページで、 **[Enterprise Mobility + Security E5]** 項目を探します。その項目の上にマウス ポインターを移動させ、 **[無料試用版を起動する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="3b42a-121">**[注文の確認]** ページで、 **[今すぐ実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-121">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="3b42a-122">**[注文の受領書]** ページで、**[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-122">On the **Order receipt** page, click **Continue**.</span></span>
    
7. <span data-ttu-id="3b42a-123">ブラウザーの **[Office 365 管理センター]** タブの左側のナビゲーションで **[ユーザー] > [アクティブなユーザー]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-123">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
8. <span data-ttu-id="3b42a-124">全体管理者アカウントをクリックしてから、 **[製品ライセンス]** で **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-124">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
9. <span data-ttu-id="3b42a-125">**[製品ライセンス]** ウィンドウで、 **Enterprise Mobility + Security E5** の製品ライセンスを **[オン]** にして、 **[保存]** をクリックしてから、 **[閉じる]** を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-125">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
> [!NOTE]
> <span data-ttu-id="3b42a-p104">Enterprise Mobility + Security E5 試用版サブスクリプションの試用期間は 90 日間です。永続的な開発/テスト環境では、少数のライセンスを使用して新しい有料サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="3b42a-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
 <span data-ttu-id="3b42a-128">「[Office 365 開発/テスト環境](office-365-dev-test-environment.md)」の***フェーズ 3 を完了している場合***は、その他のすべてのアカウント (User 2、User 3、User 4、および User 5) に前述の手順 8 と手順 9 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="3b42a-128">***If you completed Phase 3 of the*** [Office 365 dev/test environment](office-365-dev-test-environment.md), repeat steps 8 and 9 of the previous procedure for all of your other accounts (User 2, User 3, User 4, and User 5).</span></span>
  
<span data-ttu-id="3b42a-129">開発/テスト環境は、次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="3b42a-129">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="3b42a-130">Office 365 E5 Enterprise と EMS E5 の試用版サブスクリプションが、ユーザー アカウントの一覧と同じ Azure AD テナントを共有している。</span><span class="sxs-lookup"><span data-stu-id="3b42a-130">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
- <span data-ttu-id="3b42a-131">すべての適切なアカウント (全体管理者のみまたは 5 つすべてのユーザー アカウントのどちらか) が、Office 365 E5 と EMS E5 を使用できるようになっている。</span><span class="sxs-lookup"><span data-stu-id="3b42a-131">All your appropriate user accounts (either just the global administrator or all five user accounts) are enabled to use Office 365 E5 and EMS E5.</span></span>
    
<span data-ttu-id="3b42a-132">図 2 は、EMS が追加された結果的な構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="3b42a-132">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="3b42a-133">**図 2: EMS 試用版サブスクリプションを追加**</span><span class="sxs-lookup"><span data-stu-id="3b42a-133">**Figure 2: Adding the EMS trial subscription**</span></span>

![Microsoft 3656 Enterprise 開発/テスト環境のフェーズ 2](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a><span data-ttu-id="3b42a-135">フェーズ 3: Windows 10 Enterprise コンピューターを作成する</span><span class="sxs-lookup"><span data-stu-id="3b42a-135">Phase 3: Create a Windows 10 Enterprise computer</span></span>

<span data-ttu-id="3b42a-136">このフェーズでは、Windows 10 Enterprise を実行するスタンドアロン コンピューターを作成します。</span><span class="sxs-lookup"><span data-stu-id="3b42a-136">In this phase, you create a standalone computer running Windows 10 Enterprise.</span></span>
  
### <a name="physical-computer"></a><span data-ttu-id="3b42a-137">物理コンピューター</span><span class="sxs-lookup"><span data-stu-id="3b42a-137">Physical computer</span></span>

<span data-ttu-id="3b42a-p105">パーソナル コンピューターを入手し、Windows 10 Enterprise をインストールします。Windows 10 Enterprise 試用版は、[ここ](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="3b42a-p105">Obtain a personal computer and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [herehttps://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine"></a><span data-ttu-id="3b42a-140">仮想マシン</span><span class="sxs-lookup"><span data-stu-id="3b42a-140">Virtual machine</span></span>

<span data-ttu-id="3b42a-p106">任意のハイパーバイザーを使用して仮想マシンを作成し、そのマシンに Windows 10 Enterprise をインストールします。Windows 10 Enterprise 試用版は、[ここ](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="3b42a-p106">Create a virtual machine using the hypervisor of your choice and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [herehttps://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine-in-azure"></a><span data-ttu-id="3b42a-143">Azure での仮想マシン</span><span class="sxs-lookup"><span data-stu-id="3b42a-143">Virtual machine in Azure</span></span>

<span data-ttu-id="3b42a-p107">Microsoft Azure で Windows 10 の仮想マシンを作成するには、***Visual Studio ベースのサブスクリプションが必要***です。このサブスクリプションにより、Windows 10 Enterprise のイメージにアクセスできます。試用版や有料のサブスクリプションなど、その他の種類の Azure サブスクリプションでは、このイメージにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="3b42a-p107">To create a Windows 10 virtual machine in Microsoft Azure, ***you must have a Visual Studio-based subscription***, which has access to the image for Windows 10 Enterprise. Other types of Azure subscriptions, such as trial and paid subscriptions, do not have access to this image.</span></span>
  
> [!NOTE]
> <span data-ttu-id="3b42a-p108">次のコマンド セットは、最新バージョンの Azure PowerShell を使用します。「[Azure PowerShell の概要](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)」を参照してください。このコマンド セットにより、WIN10 という名前の Windows 10 Enterprise の仮想マシンと、このマシンに必要なすべてのインフラストラクチャをビルドします。これには、リソース グループ、ストレージ アカウント、仮想ネットワークが含まれます。Azure インフラストラクチャ サービスを既に使い慣れている場合は、これらの手順は展開済みのインフラストラクチャに合わせて、実行してください。</span><span class="sxs-lookup"><span data-stu-id="3b42a-p108">The following command sets use Azure PowerShell 1.0.0 and later. See [Get started with Azure PowerShell cmdletshttps://docs.microsoft.com/powershell/azureps-cmdlets-docs/](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). These command sets build a Windows 10 Enterprise virtual machine named WIN10 and all of its required infrastructure, including a resource group, a storage account, and a virtual network. If you are already familiar with Azure infrastructure services, please adapt these instructions to suit your currently deployed infrastructure.</span></span> 
  
<span data-ttu-id="3b42a-150">最初に、Microsoft PowerShell プロンプトを起動します。</span><span class="sxs-lookup"><span data-stu-id="3b42a-150">First, start a Microsoft PowerShell prompt.</span></span>
  
<span data-ttu-id="3b42a-151">次のコマンドを使用して Azure アカウントにログインします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-151">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="3b42a-152">次のコマンドを使用して、サブスクリプションの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="3b42a-152">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="3b42a-p109">Azure サブスクリプションを設定します。二重引用符内のすべて (「\<」と「>」の文字を含む) を正しい名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3b42a-p109">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="3b42a-p110">次に、新しいリソース グループを作成します。一意のリソース グループ名を決定するには、このコマンドを使用して既存のリソース グループを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3b42a-p110">Next, create a new resource group. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="3b42a-p111">これらのコマンドを使用して、新しいリソース グループを作成します。二重引用符内のすべて (「\<」と「>」の文字を含む) を正しい名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3b42a-p111">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="3b42a-p112">次に、これらのコマンドを使用して新しい仮想ネットワークと WIN10 仮想マシンを作成します。ダイアログ ボックスが表示されたら、WIN10 の名前とローカル管理者アカウントのパスワードを指定し、これらを安全な場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="3b42a-p112">Next, you create a new virtual network and the WIN10 virtual machine with these commands. When prompted, provide the name and password of the local administrator account for WIN10 and store these in a secure location.</span></span>
  
```
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$pip=New-AzureRMPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName WIN10 -VMSize Standard_D1_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a><span data-ttu-id="3b42a-161">フェーズ 4: Windows 10 のコンピューターを Azure AD に参加させる</span><span class="sxs-lookup"><span data-stu-id="3b42a-161">Phase 4: Join your Windows 10 computer to Azure AD</span></span>

<span data-ttu-id="3b42a-162">Windows 10 Enterprise の物理マシンまたは仮想マシンの作成後、ローカル管理者アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-162">After the physical or virtual machine is created, configured with Windows 10 Enterprise, and is running, sign in with a local administrator account.</span></span>
  
> [!NOTE]
> <span data-ttu-id="3b42a-p113">Azure の仮想マシンの場合は、[この手順](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)に従って Azure に接続します。ローカル管理者アカウントの資格情報でサインインします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-p113">For a virtual machine in Azure, connect to it using [these instructionshttps://docs.microsoft.com/azure/virtual-machines/windows/connect-logon](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Sign in with the credentials of the local administrator account.</span></span> 
  
<span data-ttu-id="3b42a-165">次に、WIN10 コンピューターを Office 365 と EMS のサブスクリプションの Azure AD テナントに参加させます。</span><span class="sxs-lookup"><span data-stu-id="3b42a-165">Next, join the WIN10 computer to the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="3b42a-166">WIN10 コンピューターのデスクトップで、**[スタート] > [設定] > [アカウント] > [職場または学校にアクセスする] > [接続]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-166">At the desktop of the WIN10 computer, click **Start > Settings > Accounts > Access work or school > Connect**.</span></span>
    
2. <span data-ttu-id="3b42a-167">**[職場または学校アカウントの設定]** ダイアログ ボックスで、**[このデバイスを Azure Active Directory に参加させる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-167">In the **Set up a work or school account** dialog box, click **Join this device to Azure Active Directory**.</span></span>
    
3. <span data-ttu-id="3b42a-168">**[職場または学校アカウント]** に Office 365 サブスクリプションの全体管理者のアカウント名を入力して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-168">In **Work or school account**, type the global administrator account name of your Office 365 subscription, and then click **Next**.</span></span>
    
4. <span data-ttu-id="3b42a-169">**[パスワードの入力]** に全体管理者アカウントのパスワードを入力して、**[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-169">In **Enter password**, type the password for your global administrator account, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="3b42a-170">この組織で合っているか確認するダイアログ ボックスが表示されたら、**[参加]** をクリックしてから **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-170">When prompted to make sure this is your organization, click **Join**, and then click **Done**.</span></span>
    
6. <span data-ttu-id="3b42a-171">[設定] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="3b42a-171">Close the settings window.</span></span>
    
<span data-ttu-id="3b42a-172">次に、WIN10 コンピューターに Office 2016 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-172">Next, install Office 2016 on the WIN10 computer</span></span>
  
1. <span data-ttu-id="3b42a-p114">Microsoft Edge ブラウザーを開いて、全体管理者アカウントの資格情報を使用して、Office 365 ポータルにサインインします。ヘルプについては、「[Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b42a-p114">Open the Microsoft Edge browser and sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="3b42a-175">**[Microsoft Office Home]** タブで、**[Office 2016 のインストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-175">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
3. <span data-ttu-id="3b42a-176">操作内容を確認するダイアログ ボックスが表示されたら、**[実行]** をクリックし、**[ユーザー アカウント制御]** の **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-176">When prompted with what to do, click **Run**, and then click **Yes** for **User Account Control**.</span></span>
    
4. <span data-ttu-id="3b42a-p115">Office のインストールが完了するまで待ちます。**[準備が完了しました]** が表示されたら、**[閉じる]** を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="3b42a-p115">Wait for Office to complete its installation. When you see **You’re all set!**, click **Close** twice.</span></span>
    
<span data-ttu-id="3b42a-179">図 3 は、Office 365 と EMS のサブスクリプションの Azure AD テナントに参加した WIN10 コンピューターの様子を含め、結果的な環境を示しています。</span><span class="sxs-lookup"><span data-stu-id="3b42a-179">Figure 3 shows your resulting environment, which includes the WIN10 computer that has joined the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
<span data-ttu-id="3b42a-180">**図 3: WIN10 のコンピューター アカウントを Azure AD テナントに追加**</span><span class="sxs-lookup"><span data-stu-id="3b42a-180">**Figure 3: Adding the WIN10 computer account to the Azure AD tenant**</span></span>

![Microsoft 3656 Enterprise 開発/テスト環境のフェーズ 4](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
<span data-ttu-id="3b42a-182">これで、[Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise) の追加機能を試せるようになりました。</span><span class="sxs-lookup"><span data-stu-id="3b42a-182">You are now ready to experiment with additional features of [Microsoft 365 Enterprisehttps://www.microsoft.com/microsoft-365/enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="3b42a-183">次の手順</span><span class="sxs-lookup"><span data-stu-id="3b42a-183">Next steps</span></span>

<span data-ttu-id="3b42a-184">Microsoft 365 Enterprise の機能について確認するには、次に示す追加記事を使用します。</span><span class="sxs-lookup"><span data-stu-id="3b42a-184">Use these additional articles to explore features of Microsoft 365 Enterprise:</span></span>
  
- [<span data-ttu-id="3b42a-185">モバイル アプリケーション管理 (MAM) ポリシーの追加</span><span class="sxs-lookup"><span data-stu-id="3b42a-185">Add mobile application management (MAM) policies</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- <span data-ttu-id="3b42a-186">[iOS および Android デバイスの登録](https://technet.microsoft.com/library/mt743077.aspx)</span><span class="sxs-lookup"><span data-stu-id="3b42a-186">[Intune/EMS:](https://technet.microsoft.com/library/mt743077.aspx) Manage iOS and Android devices.</span></span>
    
- [<span data-ttu-id="3b42a-187">高度なセキュリティ管理の構成とテスト</span><span class="sxs-lookup"><span data-stu-id="3b42a-187">Configure and test Advanced Security Management</span></span>](https://technet.microsoft.com/library/mt757250.aspx)
    
- [<span data-ttu-id="3b42a-188">Advanced Threat Protection の構成とテスト</span><span class="sxs-lookup"><span data-stu-id="3b42a-188">Configure and test Advanced Threat Protection</span></span>](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a><span data-ttu-id="3b42a-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b42a-189">See Also</span></span>

- [<span data-ttu-id="3b42a-190">Microsoft 365 Enterprise のドキュメントとリソース</span><span class="sxs-lookup"><span data-stu-id="3b42a-190">Microsoft 365 Enterprise documentation and resources</span></span>](https://docs.microsoft.com/microsoft-365-enterprise/)
- <span data-ttu-id="3b42a-191">[Microsoft 365 Enterprise の展開](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)</span><span class="sxs-lookup"><span data-stu-id="3b42a-191">Microsoft 365 Enterprise[](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)</span></span>
- [<span data-ttu-id="3b42a-192">One Microsoft Cloud 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="3b42a-192">The One Microsoft Cloud dev/test environment</span></span>](the-one-microsoft-cloud-dev-test-environment.md)
- [<span data-ttu-id="3b42a-193">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="3b42a-193">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
