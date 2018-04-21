---
title: Office 365 の開発/テスト環境のディレクトリの同期
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/04/2018
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
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: '概要: Office 365 の開発/テスト環境のディレクトリ同期を構成します。'
ms.openlocfilehash: ebb16cb65738e0440b40d0d14550cd1f9c5bb21c
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="directory-synchronization-for-your-office-365-devtest-environment"></a>Office 365 の開発/テスト環境のディレクトリの同期

 **の概要:**Office 365 の開発/テスト環境のディレクトリ同期を構成します。
  
多くの組織 Azure AD 接続および Office 365 のアカウントのセットに、オンプレミスの Windows サーバー ・ Active Directory (AD) フォレストのアカウントの設定を同期するディレクトリ同期します。この資料を追加する方法パスワード ハッシュの同期とのディレクトリ同期を Office 365 の開発/テスト環境では、次の構成の結果について説明します。
  
![ディレクトリ同期によって Office 365 の開発/テスト環境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
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
  Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. タスク バーから [ **Internet Explorer** ] をクリックしには、 [https://aka.ms/aadconnect](https://aka.ms/aadconnect)。
    
4. Microsoft Azure Active Directory に接続] ページで、[**ダウンロード**] をクリックし、[**実行**] をクリックします。
    
5. **Azure AD 接続へようこそ**] ページで、[**同意する**] をクリックし、[**続行**] をクリックします。
    
6. [**高速の設定**] ページで、**高速の設定を使用する**をクリックします。
    
7. **Azure AD への接続**] ページで、そのパスワードを [**パスワード**] に**ユーザー名**種類で、グローバル管理者のアカウント名を入力し、[**次へ**] をクリックします。
    
8. [ **AD DS への接続**] ページで、次のように入力します。**株式会社\\User1**で**ユーザー名、** **パスワード**にパスワードを入力し、[**次へ**] をクリックします。
    
9. **Azure AD サインインの構成**] ページで、**検証済みの任意のドメインなしで続行する**] をクリックし、[**次へ**] をクリックします。
    
10. **[構成の準備完了]** ページで、 **[インストール]** をクリックします。
    
11. [**構成の完了**] ページで [**終了**] をクリックします。
    
12. Internet Explorer、Office 365 ポータルに移動 ([https://portal.office.com](https://portal.office.com)) し、グローバル管理者アカウントを使用して、Office 365 の試用版サブスクリプションにサインインします。
    
13. ポータルのメイン ページで、 **[管理]** をクリックします。
    
14. 左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。
    
    **User1**をという名前のアカウントに注意してください。このアカウント CORP Windows サーバーの AD ドメインからは、ディレクトリ同期が正常に動作した証拠です。
    
15. **User1**アカウントをクリックします。製品のライセンスの [**編集**] をクリックします。
    
16. **製品のライセンス**では、国または地域を選択する.」をクリックして**Office 365 エンタープライズ E5** (へ**の**切り替え) の**電源を**コントロール、ページの下部にある**保存**を] をクリックし、[**閉じる**] をクリックします。
    
最終的な構成を示します。
  
![ディレクトリ同期によって Office 365 の開発/テスト環境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
この構成は、次の内容で成立します。  
  
- Office 365 E5 試用版サブスクリプション。
- インターネットに接続する組織の簡易型イントラネット。Azure 仮想ネットワークのサブネット上に配置された仮想マシン DC1、APP1、および CLIENT1 で構成されます。Azure AD Connect は APP1 上で実行され、CORP Windows Server AD ドメインを 30 分ごとに Office 365 に同期します。
    
## <a name="next-step"></a>次のステップ

組織のディレクトリ同期を展開する準備ができたら、 [Microsoft Azure で Office 365 の展開ディレクトリの同期](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)を参照してください。

## <a name="see-also"></a>関連項目

[クラウド導入のテスト ラボ ガイドの (TLGs)](cloud-adoption-test-lab-guides-tlgs.md)
[の開発/テスト環境の基本構成](base-configuration-dev-test-environment.md)
[の開発/テスト環境を Office 365](office-365-dev-test-environment.md)
[、Office 365 の開発/テスト環境のクラウド アプリケーションのセキュリティ](cloud-app-security-for-your-office-365-dev-test-environment.md)
 [Office 365 の開発/テスト環境の脅威保護を高度な](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
[クラウドを採用しハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)




