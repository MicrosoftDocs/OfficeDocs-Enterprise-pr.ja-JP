---
title: Office 365 開発/テスト環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: '概要: このテスト ラボ ガイドを使用すると、評価または開発/テスト用の Office 365 試用版サブスクリプションを作成できます。'
ms.openlocfilehash: 57fdf66f11d9c71faf81e2a88482093f8f17dfbd
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="office-365-devtest-environment"></a>Office 365 開発/テスト環境

 **概要:** このテスト ラボ ガイドを使用すると、評価または開発/テスト用の Office 365 試用版サブスクリプションを作成できます。
  
Office 365 試用版サブスクリプションを使用できます。また、アプリケーションの Office 365 開発/テスト環境を作成したり、Office 365 の機能をデモンストレーションすることができます。次の 2 つのバージョンがあります。
  
- 軽量の Office 365 開発/テスト環境は、メイン コンピューターからアクセスする Office 365 試用版サブスクリプションで構成されています。
    
    機能をすばやくデモンストレーションする場合には、この環境を使用してください。軽量の Office 365 開発/テスト環境の場合は、この記事のフェーズ 2 と 3 のみを完了します。
    
- シミュレーションのエンタープライズ Office 365 開発/テスト環境は、Office 365 試用版サブスクリプションと、Microsoft Azure インフラストラクチャ サービスでホストされる、インターネットに接続されたシンプルな組織のイントラネットで構成されています。この構成は Microsoft クラウドで完全に構築できます。
    
    この環境は、インターネットに接続された一般的な組織ネットワークと類似した環境で機能またはアプリをデモンストレーションする場合や、この種類の環境を必要とする機能に使用してください。シミュレーションのエンタープライズ Office 365 開発/テスト環境の場合は、この記事のフェーズ 1、2、3 を完了します。
    
> [!NOTE]
> この記事を印刷しておき、30 日間の Office 365 試用版サブスクリプションの終了後にこの環境で必要になる特定の値を記録しておくことをお勧めします。試用版サブスクリプションは、追加で 30 日間まで簡単に延長できます。永続的な開発/テスト環境では、少数のライセンスを使用して新しい有料サブスクリプションを作成します。 
  
![Microsoft Cloud のテスト ラボ ガイド](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップを確認してください。
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a>フェーズ 1: Azure に基本構成を作成する

「[基本構成開発/テスト環境](base-configuration-dev-test-environment.md)」の手順を実行します。
  
Azure サブスクリプションが必要になります。この構成には、[Azure の無料試用版](https://azure.microsoft.com/pricing/free-trial/)を使用できます。MSDN や Visual Studio のサブスクリプションを取得している場合は、「[Visual Studio サブスクライバー向けの月単位の Azure クレジット](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)」を参照してください。
  
最終的な構成は、次のようになります。
  
![Azure の基本構成開発/テスト環境](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
この構成は、Azure 仮想ネットワーク上の仮想マシン DC1、APP1、および CLIENT1 で成立します。
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a>フェーズ 2:Office 365 試用版サブスクリプションを作成する

Office 365 E5 試用版サブスクリプションを開始するには、最初に、架空の会社名と新しい Microsoft アカウントが必要になります。
  
1. この会社名には、会社名 Contoso のバリエーションを使用するようお勧めします (必須ではありません)。Contoso は、Microsoft のサンプル コンテンツで使用される架空の会社名です。ここに架空の会社名を記録してください: ![](./images/Common_Images/TableLine.png)
    
2. 新しい Microsoft アカウントにサインアップするには、[https://outlook.com](https://outlook.com) に移動して、新しい電子メール アカウントとアドレスでアカウントを作成します。このアカウントを使用して、Office 365 にサインアップします。
    
  - ここに新しいアカウントの姓名を記録してください: ![](./images/Common_Images/TableLine.png)
    
  - ここに新しい電子メール アカウントのアドレスを記録してください: ![](./images/Common_Images/TableLine.png)@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Office 365 E5 試用版サブスクリプションにサインアップする

1. 軽量の Office 365 開発/テスト環境の場合は、自分のコンピューターでブラウザーを起動して、[https://aka.ms/e5trial](https://aka.ms/e5trial) に移動します。 
    
    シミュレーションのエンタープライズ Office 365 開発/テスト環境の場合は、Azure portal から CORP\User1 アカウントを使用して CLIENT1 に接続します。

    スタート画面から Microsoft Edge を起動して、[https://aka.ms/e5trial](https://aka.ms/e5trial) に移動します。
    
2. **[ようこそ、必要事項をご記入ください]** ページで、次に示す項目を指定します。
    
  - 所在地
    
  - 新しい Microsoft アカウントの姓名
    
  - 新しい電子メール アドレス
    
  - 勤務先電話番号
    
  - 架空の会社名
    
  - 組織の規模に [250-999 人]
    
3. **[手順はあと 1 つだけです]** をクリックします。
    
4. **[ユーザー ID の作成]** ページで、新しい電子メール アドレスに応じたユーザー名を入力し、@ 記号の後に架空の会社名を入力します (名前に含まれる空白はすべて削除します)。次に、この新しい Office 365 アカウントのパスワードを 2 回入力します。 
    
    入力したパスワードを安全な場所に記録してください。
    
    架空の会社名を記録してください (この名前を**組織名**と呼ぶことにします): ![](./images/Common_Images/TableLine.png)
    
5. **[アカウントの作成]** をクリックします。
    
6. **[ロボットではないことを証明してください]** ページで、テキスト対応の電話の電話番号を入力して、**[自分にテキスト送信]** をクリックします。
    
7. 受信したテキスト メッセージの認証コードを入力して、**[次へ]** をクリックします。
    
8. ここにサインイン ページの URL を記録してください (選択してコピー): ![](./images/Common_Images/TableLine.png)
    
9. ここにユーザー ID を記録してください (選択してコピー): ![](./images/Common_Images/TableLine.png).onmicrosoft.com
    
    この値を**Office 365 全体管理者名**と呼ぶことにします。
    
10. **[準備が整いました]** が表示されたら、その表示をクリックします。
    
11. 次のページで、Office 365 のセットアップが完了して、すべてのタイルが使用できるようになるまで待機します。
    
Office 365 ポータルのメイン ページが表示されます。このページから、Office Online のサービスと Office 365 管理センターにアクセスできます。
  
シミュレーションのエンタープライズ Office 365 開発/テスト環境の、最終的な構成をここに示します。
  
![Office 365 開発/テスト環境](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
この構成は、次の内容で成立します。 
  
- Azure 仮想ネットワークのサブネット上の仮想マシン DC1、APP1、および CLIENT1。
    
- Office 365 E5 試用版サブスクリプション。
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a>フェーズ 3: Office 365 試用版サブスクリプションを構成する

このフェーズでは、追加のユーザーと SharePoint Online のチーム サイトで Office 365 のサブスクリプションを構成します。
  
まず、4 人分の新しいユーザーを追加して、E5 ライセンスを割り当てます。
  
「[Office 365 PowerShell への接続](https://technet.microsoft.com/library/dn975125.aspx)」の手順を使用して、PowerShell モジュールをインストールし、新しい Office 365 のサブスクリプション フォームに接続します。
  
- 自分のコンピューター (軽量の Office 365 開発/テスト環境の場合)。
    
- CLIENT1 仮想マシン (シミュレーションのエンタープライズ Office 365 開発/テスト環境の場合)。
    
 [Windows PowerShell 資格情報の要求] ダイアログ ボックスで、Office 365 全体管理者名 (例: jdoe@contosotoycompany.onmicrosoft.com) とパスワードを入力します。
  
組織名 (例: contosotoycompany)、所属地域に該当する 2 文字の国別コードを入力して、Windows PowerShell 用 Windows Azure Active Directory モジュールのプロンプトから次のコマンドを実行します。
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```
> [!TIP]
> この記事に掲載されているすべての PowerShell コマンドを含むテキスト ファイルを入手するには、[ここ](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34)をクリックしてください。

**New-MsolUser** コマンドの表示から、User 2 アカウント用に生成されたパスワードを見つけて、そのパスワードを安全な場所に記録します。
  
次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

**New-MsolUser** コマンドの表示から、User 3 アカウント用に生成されたパスワードを見つけて、そのパスワードを安全な場所に記録します。
  
次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

**New-MsolUser** コマンドの表示から、User 4 アカウント用に生成されたパスワードを見つけて、そのパスワードを安全な場所に記録します。
  
次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

**New-MsolUser** コマンドの表示から、User 5 アカウント用に生成されたパスワードを見つけて、そのパスワードを安全な場所に記録します。
  
次に、Sales (販売)、Production (生産)、および Support (サポート) の各部門ために、新しい SharePoint Online チーム サイトを 3 つ作成します。
  
### <a name="create-three-new-sharepoint-online-team-sites"></a>新しい SharePoint Online チーム サイトを 3 つ作成する

1. [SharePoint Online 管理シェル](https://go.microsoft.com/fwlink/p/?LinkId=255251) (x64 バージョン) をインストールします。
    
2. **[スタート]** をクリックし、「**sharepoint**」と入力してから、**[SharePoint Online 管理シェル]** をクリックします。
    
3. 組織名 (example: contosotoycompany) を入力し、SharePoint Online Management Shell プロンプトから次に示すコマンドを実行して、SharePoint Online サービスに接続します。
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. **[Microsoft Office SharePoint Online 管理シェル]** ダイアログ ボックスで、Office 365 全体管理者名 (例: jdoe@contosotoycompany.onmicrosoft.com) とパスワードを入力してから、**[サインイン]** をクリックします。
    
5. 新しい 3 つのチーム サイト (Sales、Production、および Support) を作成するには、Office 365 全体管理者名を入力して、SharePoint Online Management Shell プロンプトから次に示すコマンドを実行します。
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. このコマンドを実行して、これら 3 つの新しいサイトの URL を一覧表示します。
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. Internet Explorer で、Production サイトの URL を入力して、Production 部門の既定の SharePoint Online チーム サイトを確認します。
    
## <a name="record-values-for-future-reference"></a>将来の参考のために値を記録する

この環境で作業する場合や、この環境に追加のテスト ラボ ガイドラインを展開するために、次に示す値を記録しておきます。
  
- Office 365 全体管理者名: ![](./images/Common_Images/TableLine.png).onmicrosoft.com (フェーズ 2 の手順 9 で入力したもの)
    
    このアカウントのパスワードも安全な場所に記録してください。
    
- 試用版サブスクリプションの組織名: ![](./images/Common_Images/TableLine.png) (フェーズ 2 の手順 4 で入力したもの)
    
- User 2、User 3、User 4、および User 5 のアカウントを一覧表示するには、次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    ここにアカウント名を記録してください:
    
  - User 2 のアカウント名: user2@![](./images/Common_Images/TableLine.png).onmicrosoft.com
    
  - User 3 のアカウント名: user3@![](./images/Common_Images/TableLine.png).onmicrosoft.com
    
  - User 4 のアカウント名: user4@![](./images/Common_Images/TableLine.png).onmicrosoft.com
    
  - User 5 のアカウント名: user5@![](./images/Common_Images/TableLine.png).onmicrosoft.com
    
    これらのアカウントのパスワードも安全な場所に記録してください。
    
- Sales、Production、および Support チーム サイトの URL を一覧表示するには、次に示すコマンドを SharePoint Online 管理シェル プロンプトから実行します。
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - Production サイトの URL: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/production
    
  - Sales サイトの URL: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/sales
    
  - Support サイトの URL: https://![](./images/Common_Images/TableLine.png).sharepoint.com/sites/support
    
## <a name="next-steps"></a>次の手順

この Office 365 開発/テスト環境に、次の追加記事を使用します。
  
- [Office 365 開発/テスト環境のディレクトリ同期](dirsync-for-your-office-365-dev-test-environment.md)
    
- [Office 365 開発/テスト環境用の多要素認証](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [Office 365 開発/テスト環境のフェデレーション ID](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [Office 365 開発/テスト環境の Cloud App Security](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [Office 365 開発/テスト環境の Advanced Threat Protection](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [Office 365 の開発/テスト環境の Advanced eDiscovery](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [Office 365 の開発/テスト環境での機密性の高いファイルの保護](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [Office 365 開発/テスト環境での分離した SharePoint Online チーム サイト](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [Office 365 開発/テスト環境でのデータ分類とラベルの作成](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
他の Microsoft クラウド製品を含むように、Office 365 の開発/テスト環境を拡張します。
  
- [Microsoft 365 Enterprise 開発/テスト環境](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [Office 365 と Dynamics 365 の開発/テスト環境](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a>関連項目

- [クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
- [Office 365 と Dynamics 365 の開発/テスト環境](office-365-and-dynamics-365-dev-test-environment.md)
  
- [クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)


