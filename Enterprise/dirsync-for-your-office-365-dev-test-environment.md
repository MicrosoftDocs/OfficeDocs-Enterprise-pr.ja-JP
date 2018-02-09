---
title: "Office 365 開発/テスト環境の DirSync"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: "概要: Office 365 の開発/テスト環境のディレクトリ同期を構成します。"
ms.openlocfilehash: 32b9be8bb82d0efec2549dcacb5706c5e3dbc6f3
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="dirsync-for-your-office-365-devtest-environment"></a>Office 365 開発/テスト環境の DirSync

 **の概要:**Office 365 の開発/テスト環境のディレクトリ同期を構成します。
  
多くの組織は、Azure AD Connect とディレクトリ同期 (DirSync) を使用して、オンプレミスの Windows Server Active Directory (AD) フォレスト内のアカウントのセットを Office 365 内のアカウントのセットに同期しています。この記事では、Office 365 の開発/テスト環境にパスワード同期を伴う DirSync を追加する方法について説明します。最終的な構成は、次のとおりになります。
  
![DirSync を使用した Office 365 の開発/テスト環境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
この構成は、次の内容で成立します。  
  
- Office 365 E5 試用版サブスクリプション。このサブスクリプションは、作成時から 30 日で有効期限が切れます。
    
- インターネットに接続する組織の簡易型イントラネット。Azure 仮想ネットワークのサブネット上に配置された 3 つの仮想マシン (DC1、APP1、および CLIENT1) で構成されます。Azure AD Connect は、Windows Server AD ドメインを Office 365 に同期するために APP1 で実行します。
    
この開発/テスト環境は、次に示す 2 つのフェーズで構成します。
  
1. Office 365 の開発/テスト環境を作成します (Azure 仮想ネットワーク内の仮想マシン DC1、APP1、および CLIENT1 と、Office 365 E5 試用版サブスクリプションによる環境)。
    
2. APP1 に Azure AD Connect をインストールして構成します。
    
> [!TIP]
> 
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a>フェーズ 1: Office 365 の開発/テスト環境を作成する

フェーズ 1、2、および 3[の開発/テスト環境を Office 365](office-365-dev-test-environment.md)の資料の指示に従います。ここでは、結果として得られる構成です。
  
![Office 365 開発/テスト環境](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
この構成は、次の内容で成立します。  
  
- Office 365 E5 試用版サブスクリプション。
    
- インターネットに接続する組織の簡易型イントラネット。Azure 仮想ネットワークのサブネット上に配置された仮想マシン DC1、APP1、および CLIENT1 で構成されます。
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a>フェーズ 2: APP1 に Azure AD Connect をインストールする

インストールと構成が済ませてあると、Azure AD Connect は CORP Windows Server AD ドメインのアカウントのセットを Office 365 試用版サブスクリプションのアカウントのセットと同期します。次に示す手順を実行して、APP1 に Azure AD をインストールして、その動作を確認します。
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a>インストールし、APP1 の Azure AD 接続を構成します。

1. APP1 CORP でへの接続を[Azure ポータル](https://portal.azure.com)から\\User1 のアカウントです。
    
2. APP1 から、管理者レベルの Windows PowerShell コマンド プロンプトを起動して、次に示すコマンドを実行します。
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. タスク バーから [ **Internet Explorer** ] をクリックし、 [https://aka.ms/aadconnect](https://aka.ms/aadconnect)に移動します。
    
4. Microsoft Azure Active Directory に接続] ページで、[**ダウンロード**] をクリックし、[**実行**] をクリックします。
    
5. **Azure AD 接続へようこそ**] ページで、[**同意する**] をクリックし、[**続行**] をクリックします。
    
6. [**高速の設定**] ページで、**高速の設定を使用する**をクリックします。
    
7. **Azure AD への接続**] ページで、そのパスワードを [**パスワード**] に**ユーザー名**種類で、グローバル管理者のアカウント名を入力し、[**次へ**] をクリックします。
    
8. [ **AD DS への接続**] ページで、次のように入力します。**株式会社\\User1**で**ユーザー名、** **パスワード**にパスワードを入力し、[**次へ**] をクリックします。
    
9. **Azure AD サインインの構成**] ページで、**検証済みの任意のドメインなしで続行する**] をクリックし、[**次へ**] をクリックします。
    
10. **[構成の準備完了]** ページで、 **[インストール]** をクリックします。
    
11. [**構成の完了**] ページで [**終了**] をクリックします。
    
12. Internet Explorer のでは、Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) に移動し、Office 365 試用版サブスクリプションのグローバル管理者アカウントでサインインします。
    
13. ポータルのメイン ページで、 **[管理]** をクリックします。
    
14. 左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。
    
    **User1**をという名前のアカウントに注意してください。このアカウントは CORP Windows サーバーの AD ドメインとは、ディレクトリ同期が動作していたことの証明です。
    
15. **User1**アカウントをクリックします。製品のライセンスの [**編集**] をクリックします。
    
16. **製品のライセンス**では、国または地域を選択する.」をクリックして**Office 365 エンタープライズ E5** (へ**の**切り替え) の**電源を**コントロール、ページの下部にある**保存**を] をクリックし、[**閉じる**] をクリックします。
    
最終的な構成を示します。
  
![DirSync を使用した Office 365 の開発/テスト環境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
この構成は、次の内容で成立します。  
  
- Office 365 E5 試用版サブスクリプション。
    
- インターネットに接続する組織の簡易型イントラネット。Azure 仮想ネットワークのサブネット上に配置された仮想マシン DC1、APP1、および CLIENT1 で構成されます。Azure AD Connect は APP1 上で実行され、CORP Windows Server AD ドメインを 30 分ごとに Office 365 に同期します。
    
## <a name="next-step"></a>次のステップ

組織のディレクトリ同期を展開する準備ができたら、[展開 Office 365 ディレクトリ同期 (DirSync) で、Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)を参照してください。

## <a name="see-also"></a>関連項目

[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基本構成開発/テスト環境](base-configuration-dev-test-environment.md)
  
[Office 365 開発/テスト環境](office-365-dev-test-environment.md)
  
[Office 365 開発/テスト環境の Cloud App Security](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Office 365 開発/テスト環境の Advanced Threat Protection](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)




