---
title: Microsoft 365 Enterprise 開発/テスト環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: '概要: は、Office 365 の E5 とエンタープライズ モビリティ + セキュリティ (EMS) E5 と 10 企業の Windows を実行するコンピューターを含む、開発/テスト環境を作成するのには、このテスト ラボ ガイド 』 を使用します。'
ms.openlocfilehash: 9ef1c13d7ae194ff4ba31abaf379529220ffa14f
ms.sourcegitcommit: 62c0630cc0d2611710e73e0592bddfe093e00783
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 Enterprise 開発/テスト環境

 **の概要:**このテスト ラボ ガイド 』 を使用すると、Office 365 の E5 とエンタープライズ モビリティ + セキュリティ (EMS) E5 と 10 企業の Windows を実行するコンピューターを含む、開発/テスト環境を作成できます。
  
この資料は、 [Microsoft 365 エンタープライズ](https://www.microsoft.com/microsoft-365/enterprise)の機能をテストするのにはシンプルな環境を作成する手順を提供します。
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a>フェーズ 1: Office 365 E5 サブスクリプションを作成する

図 1 に示すように、Office 365 の軽量の開発/テスト環境を作成するには、フェーズ 2 と[Office 365 の開発/テスト環境](office-365-dev-test-environment.md)の第 3 段階の手順を実行します。
  
**図 1: Azure Active Directory (AD) のテナントとユーザー アカウントを Office 365 の E5 サブスクリプション**

![Microsoft 3656 Enterprise 開発/テスト環境のフェーズ 1](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)

> [!NOTE]
> Office 365 の E5 の試用版サブスクリプションは、60 日間を簡単に拡張可能な 30 日間です。永続的な開発/テスト環境では、作成新しい有料サブスクリプションのライセンスの数が少ない。 
  
## <a name="phase-2-add-ems"></a>フェーズ 2: EMS を追加する

このフェーズでは、EMS E5 試用版サブスクリプションにサインアップして、Office 365 E5 試用版サブスクリプションと同じ組織に追加します。
  
まず、EMS の E5 の試用版サブスクリプションを追加し、EMS のライセンスをグローバル管理者アカウントに割り当てます。
  
1. プライベートのインターネット ブラウザーのインスタンスを表示するには、グローバル管理者アカウントの資格情報を使用して、Office 365 ポータルにサインインします。ヘルプについては、 [Office 365 にサインインするための場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)を参照してください。
    
2. 
            **[管理]** タイルをクリックします。
    
3. ブラウザーの **[Office 管理センター]** タブの左側のナビゲーションで **[請求] > [サービスを購入する]** の順にクリックします。
    
4. **[サービスを購入]** ページで、 **[Enterprise Mobility + Security E5]** 項目を探します。その項目の上にマウス ポインターを移動させ、 **[無料試用版を起動する]** をクリックします。
    
5. **[注文の確認]** ページで、 **[今すぐ実行]** をクリックします。
    
6. **[注文の受領書]** ページで、**[続行]** をクリックします。
    
7. ブラウザーの **[Office 365 管理センター]** タブの左側のナビゲーションで **[ユーザー] > [アクティブなユーザー]** の順にクリックします。
    
8. 全体管理者アカウントをクリックしてから、 **[製品ライセンス]** で **[編集]** をクリックします。
    
9. **[製品ライセンス]** ウィンドウで、 **Enterprise Mobility + Security E5** の製品ライセンスを **[オン]** にして、 **[保存]** をクリックしてから、 **[閉じる]** を 2 回クリックします。
    
> [!NOTE]
> Enterprise Mobility + Security E5 試用版サブスクリプションの試用期間は 90 日間です。永続的な開発/テスト環境では、少数のライセンスを使用して新しい有料サブスクリプションを作成します。 
  
 ***の第 3 段階を完了する場合、***[Office 365 の開発/テスト環境](office-365-dev-test-environment.md)手順 8 と 9 の前の手順のすべての他のアカウント (ユーザー 2、3 のユーザー、ユーザー 4、およびユーザーの 5)。
  
開発/テスト環境には、以下が含まれるようになりました。
  
- Office 365 E5 エンタープライズおよび EMS E5 試用版サブスクリプションはユーザー アカウントの一覧と同じ Azure AD テナントの共有します。
- Office 365 の E5 と E5 の EMS を使用するのには、すべての適切なユーザー アカウント (グローバル管理者のみまたはすべての 5 つのユーザー アカウント) が有効になります。
    
図 2 は、EMS が追加された結果的な構成を示しています。
  
**図 2: EMS の試用版サブスクリプションを追加します。**

![Microsoft 3656 Enterprise 開発/テスト環境のフェーズ 2](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a>フェーズ 3:Windows 10 Enterprise コンピューターを作成する

このフェーズでは、Windows 10 Enterprise を実行するスタンドアロン コンピューターを作成します。
  
### <a name="physical-computer"></a>物理コンピューター

パーソナル コンピューターを取得し、10 企業の Windows をインストールします。10 企業の Windows 試用版[は、ここ](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)をダウンロードできます。
  
### <a name="virtual-machine"></a>仮想マシン

好みのハイパーバイザーを使用して仮想マシンを作成し、10 企業の Windows をインストールします。10 企業の Windows 試用版[は、ここ](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)をダウンロードできます。
  
### <a name="virtual-machine-in-azure"></a>Azure での仮想マシン

***Visual Studio ベースのサブスクリプションを持つ必要があります***、Windows の 10 企業のイメージへのアクセスを持っている、Microsoft Azure で 10 の Windows 仮想マシンを作成します。Azure サブスクリプションの場合、試用版と有料のサブスクリプションなどの他の種類では、このイメージへのアクセスを必要はありません。
  
> [!NOTE]
> 次のコマンド セットは、Azure の PowerShell の最新バージョンを使用します。[Azure の PowerShell コマンドレットの入門](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)を参照してください。WIN10 とすべてのリソース グループ、ストレージ アカウント、および仮想ネットワークを含め、必要なインフラストラクチャは、これらのコマンド セットのビルド 10 企業の Windows 仮想マシンの名前。Azure インフラストラクチャ サービスに慣れている場合は、展開済みのインフラストラクチャに合わせて、次の手順に対応してください。 
  
最初に、Microsoft PowerShell プロンプトを起動します。
  
次のコマンドを使用して Azure アカウントにログインします。
  
```
Login-AzureRMAccount
```

次のコマンドを使用して、サブスクリプションの名前を取得します。
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

Azure サブスクリプションを設定します。など、二重引用符内のすべてを交換して、\<と > 正しい名前の文字です。
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

次に、新しいリソース グループを作成します。一意のリソース グループ名を決定するには、このコマンドを使用して既存のリソース グループを一覧表示します。
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

これらのコマンドを使用して、新しいリソース グループを作成します。など、二重引用符内のすべてを交換して、\<と > 文字は、正しい名前を持つ。
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

次に、これらのコマンドを使用して新しい仮想ネットワークと WIN10 仮想マシンを作成します。ダイアログ ボックスが表示されたら、WIN10 の名前とローカル管理者アカウントのパスワードを指定し、これらを安全な場所に保存します。
  
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

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a>フェーズ 4:Windows 10 のコンピューターを Azure AD に参加させる

物理または仮想マシンで Windows の 10 のエンタープライズを作成すると後、は、ローカルの管理者アカウントでサインインします。
  
> [!NOTE]
> Azure のバーチャル マシンでは、[次の手順](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)を使用して接続します。ローカル管理者アカウントの資格情報でサインインします。 
  
次に、WIN10 コンピューターを Office 365 と EMS のサブスクリプションの Azure AD テナントに参加させます。
  
1. WIN10 コンピューターのデスクトップをクリックして**スタート > 設定 > アカウント > アクセス職場または学校 > 接続**。
    
2. **職場または学校のアカウントの設定**] ダイアログ ボックスでは、 **Azure Active Directory には、このデバイスへの参加**をクリックします。
    
3. **作業や学校のアカウント**、Office 365 サブスクリプションのグローバル管理者アカウント名を入力し、[**次へ**] をクリックします。
    
4. **パスワードの入力**の場合は、グローバル管理者アカウントのパスワードを入力し、し、[**サインイン**] をクリックします。
    
5. 組織は、このことを確認するメッセージが表示されたら**に参加**する] をクリックし、し、[**完了**] をクリックします。
    
6. [設定] ウィンドウを閉じます。
    
WIN10 コンピューター上で Office 2016 を次に、インストールします。
  
1. マイクロソフトのエッジのブラウザーが開き、グローバル管理者アカウントの資格情報を使用して、Office 365 ポータルにサインインします。ヘルプについては、 [Office 365 にサインインするための場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)を参照してください。
    
2. **Microsoft Office ホーム**] タブ、[ **Office 2016 のインストール**] をクリックします。
    
3. どのようなメッセージが表示されたら**を実行**] をクリックし、**ユーザー アカウント制御**の [**はい**] をクリックします。
    
4. Office のインストールを完了するまで待機します。参照してください**準備ができました!**、2 回 [**閉じる**] をクリックします。
    
図 3 は、Office 365 と EMS のサブスクリプションの Azure AD テナントに参加した WIN10 コンピューターの様子を含め、結果的な環境を示しています。
  
**図 3: Azure AD テナントに WIN10 のコンピューター アカウントを追加します。**

![Microsoft 3656 Enterprise 開発/テスト環境のフェーズ 4](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
[Microsoft 365 エンタープライズ](https://www.microsoft.com/microsoft-365/enterprise)の他の機能を実験する準備が整いました。
  
## <a name="next-steps"></a>次の手順

Microsoft 365 Enterprise の機能について確認するには、これらの追加記事を使用します。
  
- [モバイル アプリケーション管理 (MAM) ポリシーを追加します。](https://technet.microsoft.com/library/mt764059.aspx)
    
- [IOS および Android のデバイスを登録します。](https://technet.microsoft.com/library/mt743077.aspx)
    
- [構成および高度なセキュリティ管理のテスト](https://technet.microsoft.com/library/mt757250.aspx)
    
- [構成および高度な脅威保護をテストします。](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a>Concepts

- [Microsoft 365 エンタープライズ ドキュメント](https://docs.microsoft.com/microsoft-365-enterprise/)
- [Microsoft 365 エンタープライズを展開します。](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)
- [1 つのマイクロソフトのクラウド開発/テスト環境](the-one-microsoft-cloud-dev-test-environment.md)
- [クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
