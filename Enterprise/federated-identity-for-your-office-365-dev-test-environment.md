---
title: Office 365 開発/テスト環境のフェデレーション ID
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/06/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: '概要: Office 365 の開発/テスト環境に統合認証を構成します。'
ms.openlocfilehash: e1a2e4096dc14c2853af33a36b24d7b6ac9784bd
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="federated-identity-for-your-office-365-devtest-environment"></a>Office 365 開発/テスト環境のフェデレーション ID

 **の概要:**Office 365 の開発/テスト環境に統合認証を構成します。
  
Office 365 は、フェデレートされた識別情報をサポートします。これは、自身の資格情報の検証を実行するのではなく Office 365 を参照している接続のユーザー Office 365 を信頼するフェデレーション認証サーバーを意味します。ユーザーの資格情報が正しい場合は、フェデレーション認証サーバーはクライアントが、認証の証明として Office 365 に送信されるセキュリティ トークンを発行します。フェデレートされた識別情報は少なくて済み、Office 365 サブスクリプションと高度な認証とセキュリティのシナリオの認証のスケール アップのことができます。
  
この記事では、Office 365 開発/テスト環境用にフェデレーション認証を構成する方法について説明します。最終的には、次のとおりになります。
  
**図 1: Office 365 の開発/テスト環境のフェデレーション認証**

![Office 365 の開発/テスト環境の DirSync に追加された Web アプリケーション プロキシ サーバー](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
図 1 に示す構成の内容は、次のとおりです。  
  
- Office 365 E5 試用版サブスクリプション。このサブスクリプションは、作成時から 30 日で有効期限が切れます。
    
- インターネットに接続する組織の簡易型イントラネット。Azure 仮想ネットワークのサブネット上に配置された 5 つの仮想マシン (DC1、APP1、CLIENT1、ADFS1、PROXY1) で構成されます。APP1 では、Windows Server AD ドメインのアカウントの一覧を Office 365 に同期するために Azure AD Connect が実行されます。PROXY1 は、受信認証要求を受信します。ADFS1 は、DC1 で資格情報を検証し、セキュリティ トークンを発行します。
    
次に示す 5 つのフェーズで、この開発/テスト環境を設定します。
  
1. DirSync を使用する、シミュレートされたエンタープライズ Office 365 開発/テスト環境を作成する。
    
2. AD FS サーバー (ADFS1) を作成する。
    
3. Web プロキシ サーバー (PROXY1) を作成する。
    
4. 自己署名証明書を作成し、ADFS1 と PROXY1 を構成する。
    
5. フェデレーション ID に対応するよう Office 365 を構成する。
    
Azure 内の Office 365 のフェデレーション認証の運用環境の導入の手順、 [Azure で Office 365 の展開の高可用性フェデレーション認証](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)を参照してください。
  
> [!NOTE]
> Azure の試用版サブスクリプションで、この開発/テスト環境を構成することはできません。 
  
> [!TIP]
> 
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。
  
## <a name="phase-1-create-the-simulated-enterprise-office-365-devtest-environment-with-dirsync"></a>フェーズ 1:DirSync を使用する、シミュレートされたエンタープライズ Office 365 開発/テスト環境を作成する

APP1 ディレクトリ同期サーバーとしての Office 365 のシミュレートされたエンタープライズ開発/テスト環境を作成するのには[、Office 365 の開発/テスト環境のディレクトリ同期](dirsync-for-your-office-365-dev-test-environment.md)の指示に従って、Office 365 の間で識別情報を同期し、DC1 上で Windows Server AD のアカウントです。
  
次に、現在のドメイン名に基づく新しいパブリック DNS ドメイン名を作成し、Office 365 サブスクリプションに追加します。名前を使用することをお勧めします**testlab。** 。\<、パブリック ・ ドメイン >。たとえば、パブリック ドメイン名が contoso.com である場合は、パブリック ・ ドメイン名の testlab.contoso.com を追加します。
  
DNS プロバイダーで、適切な DNS レコードを作成し、ドメインを Office 365 試用版サブスクリプションに追加する方法については、[追加のユーザーと Office 365 にドメイン](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611)を参照してください。 
  
最終的な構成をここに示します。
  
**Office 365 の開発/テスト環境の図 2: ディレクトリの同期**

![ディレクトリ同期によって Office 365 の開発/テスト環境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
Office 365 の開発/テスト環境では、Azure の仮想ネットワーク上の Office 365 と CLIENT1、APP1、および DC1 バーチャル マシンを含むディレクトリの synchronizationc を図 2 に示します。
  
## <a name="phase-2-create-the-ad-fs-server"></a>フェーズ 2:AD FS サーバーを作成する

AD FS サーバーは、Office 365 と、DC1 でホストされている corp.contoso.com ドメイン内のアカウントとの間でのフェデレーション認証を提供します。
  
ADFS1 の Azure の仮想マシンを作成するに、サブスクリプションおよびリソース ・ グループと、基本構成では、Azure の場所の名前が入力し、Azure の PowerShell コマンド プロンプトで、ローカル コンピューターでこれらのコマンドを実行します。
  
```
$subscr="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
Login-AzureRMAccount
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
$staticIP="10.0.0.100"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzureRMNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!TIP]
> クリックしては、[ここでは](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0)この資料ですべての PowerShell コマンドを含むテキスト ファイルです。
  
次に、 [Azure ポータル](http://portal.azure.com)を使用して、ADFS1 のローカル管理者のアカウント名とパスワードを使用する ADFS1 の仮想マシンに接続し、Windows PowerShell コマンド プロンプトを開きます。
  
ADFS1、DC1 との間の名前解決とネットワーク通信を確認するには、 **ping dc1.corp.contoso.com**コマンドを実行し、4 つの応答があることを確認します。
  
次に、ADFS1 の Windows PowerShell プロンプトで次のコマンドを使用して、ADFS1 仮想マシンを CORP ドメインに参加させます。
  
```
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

最終的な構成をここに示します。
  
**図 3: AD FS サーバーを追加します。**

![Office 365 の開発/テスト環境の DirSync に追加された AD FS サーバー](images/da82f39e-426d-41e2-842a-c13b382d63d5.png)
  
図 3 は、Office 365 開発/テスト環境の DirSync に ADFS1 サーバーが追加されたことを示しています。
  
## <a name="phase-3-create-the-web-proxy-server"></a>フェーズ 3：Web プロキシ サーバーを作成する

PROXY1 は、認証しようとするユーザーと ADFS1 との間の認証メッセージのプロキシを提供します。
  
PROXY1 用の Azure 仮想マシンを作成するには、リソース グループ名と Azure の場所を入力し、次のコマンドをローカル コンピューターの Azure PowerShell コマンド プロンプトで実行します。
  
```
$rgName="<the resource group name of your Base Configuration>"
$staticIP="10.0.0.101"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzureRMNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> PROXY1 には静的パブリック IP アドレスが割り当てられます。この IP アドレスを指すパブリック DNS レコードが作成され、PROXY1 仮想マシンを再起動するときにこの IP アドレスを変更することはできないためです。 
  
次に、PROXY1 のプライベート IP アドレスと TCP ポート 443 をインターネットからの一方的な着信トラフィックを許可するのには、社内ネットワークのサブネットのネットワークのセキュリティ グループにルールを追加します。Azure の PowerShell コマンド プロンプトで、ローカル コンピューター上のこれらのコマンドを実行します。
  
```
$rgName="<the resource group name of your Base Configuration>"
Get-AzureRmNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzureRmNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzureRmNetworkSecurityGroup
```

次に、PROXY1 ローカル管理者のアカウント名とパスワードを使用して PROXY1 仮想マシンに接続するのには、 [Azure ポータル](http://portal.azure.com)を使用し、PROXY1 の Windows PowerShell コマンド プロンプトを開きます。
  
PROXY1、DC1 との間の名前解決とネットワーク通信を確認するには、 **ping dc1.corp.contoso.com**コマンドを実行し、4 つの応答があることを確認します。
  
次に、PROXY1 の Windows PowerShell プロンプトで次のコマンドを使用して、PROXY1 仮想マシンを CORP ドメインに参加させます。
  
```
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

ローカル コンピューターで次の Azure PowerShell コマンドを使用して、PROXY1 のパブリック IP アドレスを表示します。
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

次に、パブリック DNS プロバイダーを使用しての新しいパブリック DNS の A レコードを作成**fs.testlab です**。\<、DNS ドメイン名 >**のホストの書き込み**コマンドで表示される IP アドレスに解決します。**Fs.testlab です**。\<、DNS ドメイン名 > の*フェデレーション サービスの FQDN*とも呼ぶ。
  
CORP を使用して、DC1 バーチャル マシンへの接続を次に、 [Azure ポータル](http://portal.azure.com)を使用して\\User1 の資格情報、し、次の Windows PowerShell コマンド プロンプトで管理者レベル コマンドします。
  
```
$testZone="<the FQDN of your testlab domain from phase 1, example: testlab.contoso.com>"
$testZoneFile= $testZone + ".dns"
Add-DnsServerPrimaryZone -Name $testZone -ZoneFile $testZoneFile
Add-DnsServerResourceRecordA -Name "fs" -ZoneName $testZone -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```

これらのコマンドは、Azure 仮想ネットワーク上の仮想マシンが ADFS1 のプライベート IP アドレスに解決できる、フェデレーション サービス FQDN の DNS A レコードを作成します。
  
最終的な構成をここに示します。
  
**図 4: web アプリケーションのプロキシ サーバーを追加します。**

![Office 365 の開発/テスト環境の DirSync に追加された Web アプリケーション プロキシ サーバー](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
図 4 は、PROXY1 サーバーの追加を示しています。
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>フェーズ 4:自己署名証明書を作成し、ADFS1 と PROXY1 を構成する

このフェーズでは、フェデレーション サービス FQDN 用の自己署名入りデジタル証明書を作成し、ADFS1 と PROXY1 を AD FS ファームとして構成します。
  
CORP を使用して、DC1 バーチャル マシンへの接続を最初に、 [Azure ポータル](http://portal.azure.com)を使用して\\User1 の資格情報、しを開きます管理者レベルの Windows PowerShell コマンド プロンプトです。
  
次に、DC1 の Windows PowerShell コマンド プロンプトで次のコマンドを使用して、AD FS サービス アカウントを作成します。
  
```
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

このコマンドでは、アカウントのパスワードを入力するよう求められることにご注意ください。強力なパスワードを選択して、安全な場所に記録してください。このパスワードは、このフェーズとフェーズ 5 で必要になります。
  
CORP を使用して、ADFS1 の仮想マシンに接続するのには、 [Azure ポータル](http://portal.azure.com)を使用して\\User1 の資格情報です。ADFS1 で管理者レベルの Windows PowerShell コマンド プロンプトを開きます、フェデレーション サービスの FQDN を入力し、自己署名証明書を作成するのにはこれらのコマンドを実行します。
  
```
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

次いで、次の手順を使用して新しい自己署名証明書をファイルとして保存します。
  
1. [**スタート**] ボタン、 **mmc.exe**と入力し、 **Enter**キーを押します。
    
2. クリックして**ファイル > スナップインの追加と削除**。
    
3. **追加またはスナップインを削除する**には、利用できるスナップインの一覧に**証明書**をダブルクリックして、**コンピューター アカウント**] をクリックしてで、[**次へ**] をクリックします。
    
4. **コンピューターの選択]**、[**完了**] をクリックし、[ **OK**] をクリックします。
    
5. ツリー ウィンドウで開くには**[証明書 (ローカル コンピューター) > パーソナル > 証明書**。
    
6. フェデレーション サービスの FQDN を持つ証明書を右クリックし、**すべてのタスク**] をクリックし、[**エクスポート**] をクリックします。
    
7. [**ようこそ**] ページで、**次へ**をクリックします。
    
8. [**秘密キーのエクスポート**] ページで、 **[はい**] をクリックし、[**次へ**] をクリックします。
    
9. [**エクスポート ファイルの形式**] ページで、[**すべての拡張プロパティをエクスポート**する] をクリックし、[**次へ**] をクリックします。
    
10. [**セキュリティ**] ページで、[**パスワード**] をクリックし、[**パスワード**] にパスワードを入力し、**パスワードの確認入力します**。
    
11. [**エクスポートするファイル**] ページで [**参照**] をクリックします。
    
12. 参照して、 **c:\\証明書**フォルダー、**ファイル名**、 **SSL**を入力し、**を保存します**。
    
13. [**エクスポートするファイル**] ページで、**次へ**をクリックします。
    
14. [**証明書のエクスポート ウィザードの完了**] ページで [**完了**] をクリックします。ダイアログ ボックスが表示されたら、[ **OK**を] をクリックします。
    
次に、ADFS1 の Windows PowerShell コマンド プロンプトで次のコマンドを使用して、AD FS サービスをインストールします。
  
```
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

インストールが完了するまで待ちます。
  
次いで、次の手順で AD FS サービスを構成します。
  
1. **開始**] をクリックし、**サーバー マネージャー**のアイコンをクリックします。
    
2. サーバー マネージャーのツリー ペインでは、 **AD FS**をクリックします。
    
3. ツールバーの上部にある、オレンジ色の警告の記号をクリックし、**このサーバー上のフェデレーション サービスの構成**] をクリックします。
    
4. Active Directory フェデレーション サービスの構成ウィザードの [**ようこそ**] ページで、**次へ**をクリックします。
    
5. **AD DS への接続**] ページで、[**次へ**] クリックします。
    
6. [**サービス プロパティの指定**] ページ。
    
  - **SSL 証明書**の下向きの矢印をクリックし、フェデレーション サービスの FQDN の名前を持つ証明書] をクリックします。
    
  - **フェデレーション サービスの表示名**] には、架空の組織の名前を入力します。
    
  - [ **次へ**] をクリックします。
    
7. **サービス アカウントの指定**] ページで、**アカウント名**を [**選択**] をクリックします。
    
8. **選択のユーザーまたはサービス アカウント**で、 **ADFS サービス**を入力、[**名前の確認**] をクリックし、[ **OK**] をクリックします。
    
9. **アカウントのパスワード**の場合は、ADFS サービス アカウントのパスワードを入力し、[**次へ**] をクリックします。
    
10. **構成データベースの指定**] ページで、[**次へ**] クリックします。
    
11. **オプションの確認**] ページで、[**次へ**] クリックします。
    
12. **受講前提条件のチェック**] ページで、[**構成**を] をクリックします。
    
13. [**結果**] ページで [**閉じる**] をクリックします。
    
14. [**スタート**] ボタン、[電源] アイコンをクリックして、**再起動**、し、[**続行**] をクリックします。
    
[Azure ポータル](http://portal.azure.com)では、CORP と PROXY1 に接続\\User1 アカウントの資格情報です。
  
次に、以下の手順を使用して、自己署名証明書をインストールし、PROXY1 を構成します。
  
1. [**スタート**] ボタン、 **mmc.exe**と入力し、 **Enter**キーを押します。
    
2. クリックして**ファイル > スナップインの追加と削除**。
    
3. **追加またはスナップインを削除する**には、利用できるスナップインの一覧に**証明書**をダブルクリックして、**コンピューター アカウント**] をクリックしてで、[**次へ**] をクリックします。
    
4. **コンピューターの選択]**、[**完了**] をクリックし、[ **OK**] をクリックします。
    
5. ツリー ウィンドウで開くには**[証明書 (ローカル コンピューター) > パーソナル > 証明書**。
    
6. **個人**を右クリックし、**すべてのタスク**] をクリックし、[**インポート**] をクリックします。
    
7. [**ようこそ**] ページで、**次へ**をクリックします。
    
8. [**インポートするファイル**] ページで、次のように入力します。 ** \\ \\adfs1\\証明書\\ssl.pfx**、し、[**次へ**] をクリックしします。
    
9. [**秘密キーの保護**] ページで、**パスワード**、証明書のパスワードを入力しをクリックし、**次**。
    
10. [**証明書ストア**] ページをクリックして**次**。
    
11. [**完了**] ページで [**完了**] をクリックします。
    
12. [**証明書ストア**] ページで、**次へ**をクリックします。
    
13. ダイアログ ボックスが表示されたら、[ **OK**を] をクリックします。
    
14. ツリー ペインで [**証明書**] をクリックします。
    
15. 証明書を右クリックし、し、[**コピー**] をクリックします。
    
16. ツリー ウィンドウで開くには**信頼されたルート証明機関 > 証明書**。
    
17. 証明書がインストールされている、右クリックしをクリックし、一覧の下にマウスのポインターの移動**貼り付け**。
    
管理者レベルの PowerShell コマンド プロンプトを開き、次のコマンドを実行します。
  
```
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

インストールが完了するまで待ちます。
  
次の手順を使用して、Web アプリケーション プロキシ サービスを構成し、そのフェデレーション サーバーとして ADFS1 を使用します。
  
1. **開始**] をクリックし、[**サーバー マネージャー**] をクリックします。
    
2. ツリー ウィンドウで、**リモート アクセス**をクリックします。
    
3. ツールバーの上部にある、オレンジ色の警告の記号をクリックし、 **Web アプリケーションのプロキシのウィザードを開く**] をクリックします。
    
4. Web アプリケーションのプロキシの構成ウィザードの [**ようこそ**] ページで、**次へ**をクリックします。
    
5. **フェデレーション サーバー**のページ。
    
  - **フェデレーション サービスの名前**で、フェデレーション サービスの FQDN を入力します。
    
  - 型**株式会社\\User1** **ユーザー名**にします。
    
  - User1 アカウントのパスワードを [**パスワード**] に入力します。
    
  - [ **次へ**] をクリックします。
    
6. **AD FS プロキシの証明書**] ページで、下向きの矢印をクリックして、フェデレーション サービスの FQDN を持つ証明書、し、[**次へ**] をクリックします。
    
7. [**確認**] ページで、[**構成**を] をクリックします。
    
8. [**結果**] ページで [**閉じる**] をクリックします。
    
## <a name="phase-5-configure-office-365-for-federated-identity"></a>フェーズ 5:フェデレーション ID に対応するよう Office 365 を構成する

[Azure ポータル](http://portal.azure.com)を使用して、CORP と APP1 の仮想マシンに接続する\\User1 アカウントの資格情報です。
  
次の手順を使用して、フェデレーション認証に対応するよう Azure AD Connect と Office 365 サブスクリプションを構成します。
  
1. デスクトップで、 **Azure AD 接続**をダブルクリックします。
    
2. **Azure AD 接続へようこそ**] ページで、[**構成**] をクリックします。
    
3. [**追加のタスク**] ページ**変更ユーザー サインイン**] をクリックし、[**次へ**] をクリックします。
    
4. **Azure AD への接続**] ページで、Office 365 のグローバル管理者アカウント名とパスワードを入力し、[**次へ**] をクリックします。
    
5. **[ユーザー サインイン]** ページで、 **[AD FS とのフェデレーション]** をクリックしてから、 **[次へ]** をクリックします。
    
6. **AD FS ファーム**] ページで、**既存の AD FS のファームを使用**] をクリックし、**サーバー名**] に**ADFS1**を入力し、[**次へ**] をクリックします。
    
7. サーバーの資格情報のダイアログ ボックスが表示されたら、CORP の資格情報を入力してください。\\User1 アカウント、および、[ **OK**] をクリックします。
    
8. **ドメイン管理者**の資格情報] ページで、次のように入力します。**株式会社\\User1** **ユーザー名**と**パスワード**、アカウントのパスワードで、[**次へ**] をクリックしします。
    
9. **AD FS サービス アカウント**] ページで、次のように入力します。**株式会社\\ADFS サービス****ドメインのユーザー名**と**ドメイン ユーザーのパスワード**、アカウントのパスワードで、[**次へ**] をクリックしします。
    
10. **Azure AD ドメイン**ページで、**ドメイン**、以前に作成され、フェーズ 1 で、Office 365 のサブスクリプションに追加のドメインの名前を選択し、[**次へ**] をクリックします。
    
11. **構成する準備ができました**] ページで [**構成**を] をクリックします。
    
12. [**インストールの完了**] ページで [**確認**を] をクリックします。
    
    イントラネット構成とインターネット構成の両方が確認されたことを示すメッセージが表示されます。
    
13. **[インストールの完了]** ページで、 **[終了]** をクリックします。
    
フェデレーション認証が機能していることを実証するには、次の操作を実行します。
  
1. ローカル コンピューター上のブラウザーの場合は、新しいプライベート インスタンスを開きに移動[https://portal.office.com](https://portal.office.com)。
    
2. **@ User1**を入力して、サインイン資格情報を\<のフェーズ 1 で作成したドメイン >。 
    
    たとえば、テスト ドメインが**testlab.contoso.com**の場合は、 **user1@testlab.contoso.com**を入力します。TAB キーを押すか、自動的にリダイレクトするのには Office 365 を許可します。
    
    **接続されていないプライベート**ページが表示されます。デスクトップ コンピューターを検証できません ADFS1 に自己署名証明書をインストールしたため、これを表示しています。フェデレーション認証の運用環境の導入で信頼された証明機関から証明書を使用して、ユーザーはこのページが表示されません。
    
3. **接続されていないプライベート**] ページで、[**詳細設定**] をクリックし、**に進んで\<、フェデレーション サービスの FQDN >**。 
    
4. 架空の組織名のページで、次を使用してサインインします。
    
  - **株式会社\\User1**名の
    
  - User1 アカウント: パスワード
    
    **Microsoft Office ホーム**ページを参照してくださいする必要があります。
    
この手順では、DC1 上でホストされている Windows サーバー AD corp.contoso.com ドメインを Office 365 試用版サブスクリプションを連携させることを示しています。認証プロセスに関する基本事項を以下に示します。
  
1. フェーズ 1 で作成したフェデレーション ドメインをサインイン アカウント名で使用すると、Office 365 はブラウザーをフェデレーション サービス FQDN と PROXY1 にリダイレクトします。
    
2. PROXY1 は、ローカル コンピューターに架空の会社のサインイン ページを送信します。
    
3. CORP を送信すると\\ADFS1 に転送して User1 および PROXY1 にパスワードをします。
    
4. ADFS1 CORP を検証する\\User1 と DC1 とパスワード、ローカル コンピューターにセキュリティ トークンを送信するとします。
    
5. ローカル コンピューターは、セキュリティ トークンを Office 365 に送信します。
    
6. Office 365 は、セキュリティ トークンが ADFS1 によって作成されたことを検証して、アクセスを許可します。
    
これで、Office 365 試用版のサブスクリプションがフェデレーション認証を行うように構成されました。高度な認証シナリオで、この開発/テスト環境を使用できます。
  
## <a name="next-step"></a>次のステップ

本番運用に即応を展開する準備ができたら、Azure で Office 365 のフェデレーション認証の高可用性は[Azure で Office 365 の展開の高可用性フェデレーション認証](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)を参照してください。
  
## <a name="see-also"></a>関連項目

[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基本構成開発/テスト環境](base-configuration-dev-test-environment.md)
  
[Office 365 開発/テスト環境](office-365-dev-test-environment.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)
  
[Azure に Office 365 の高可用性フェデレーション認証を展開する](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)


