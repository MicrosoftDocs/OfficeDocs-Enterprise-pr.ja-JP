---
title: "One Microsoft Cloud 開発/テスト環境"
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
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: "概要: ガイドを使用してこのテスト ラボを含むすべてのマイクロソフトのクラウド ソリューションの開発/テスト環境を作成します。"
ms.openlocfilehash: 2cbfb3e963927f18d2ee46ed1f5076b274a99154
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a>One Microsoft Cloud 開発/テスト環境

 **の概要:**マイクロソフトのクラウド ソリューションのすべてを含む開発/テスト環境を作成するのにには、このテスト ラボ ガイド 』 を使用します。
  
この記事の手順に従い、Microsoft Azure インフラストラクチャ サービスでシミュレートされたイントラネットを作成し、Microsoft Office 365、Microsoft Enterprise Mobility + Security (EMS)、Microsoft Dynamics 365 のサブスクリプションを追加します。その結果として、1 つの開発/テスト環境で Microsoft のクラウド サービスすべてを同時に使用する、シンプルな組織になります。  
  
![Azure、Office 365、EMS、Dynamics 365 が追加された One Microsoft Cloud 開発/テスト環境のフェーズ 3](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
最終的な構成を、次の目的に使用できます。
  
- Azure Active Directory (AD) で提供される共通 ID インフラストラクチャなどの、Microsoft のクラウド サービス間の統合を体験します。
    
- 複数の Microsoft Cloud のサービスを含む、エンド ツー エンドのシナリオを評価します。
    
- 複数の Microsoft Cloud のサービスを使用する、デモ、概念実証、開発/テスト構成などを作成します。
    
- プロフェッショナルな開発のため、Microsoft Cloud のスキルを構築します。
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a>フェーズ 1:シミュレートされたイントラネットを作成し、Office 365 を追加する

[Office 365 の開発/テスト環境のディレクトリ同期](dirsync-for-your-office-365-dev-test-environment.md)の指示に従います。
  
図 1 は、Office 365 と設置型の Windows サーバー ・ Active Directory (AD) フォレストと Azure インフラストラクチャ サービスとディレクトリ同期を実行しているシミュレートされたイントラネットが含まれています、結果として得られる構成を示しています。
  
**図 1: Office 365 で Azure でシミュレートされたイントラネット**

![DirSync を使用した Office 365 の開発/テスト環境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> Azure の試用版は、30 日間です。Office 365 エンタープライズ E5 の試用版サブスクリプションは、簡単に拡張できる別の 30 日間 30 日間です。永続的な開発/テスト環境では、作成新しい Azure サブスクリプションとライセンスの数が少ない新しい有料 Office 365 エンタープライズ E5 サブスクリプションを支払います。 
  
## <a name="phase-2-add-ems"></a>フェーズ 2:EMS を追加する

このフェーズでは、EMS 試用版サブスクリプションにサインアップして、Office 365 試用版サブスクリプションと同じ組織に追加します。
  
1. いずれかのブラウザーを使用して、デスクトップ コンピューター CLIENT1 からには、グローバル ・ アドミニストレータ ・ アカウントの資格情報を持つ[https://portal.office.com](https://portal.office.com)に Office 365 ポータルにサインインしているか。
    
2. 
            **[管理]** タイルをクリックします。
    
3. ブラウザーの **[Office 管理センター]** タブの左側のナビゲーションで **[請求] > [サービスを購入する]** の順にクリックします。
    
4. **[サービスを購入]** ページで、 **[Enterprise Mobility + Security E5]** 項目を探します。その項目の上にマウス ポインターを移動させ、 **[無料試用版を起動する]** をクリックします。
    
5. **[注文の確認]** ページで、 **[今すぐ実行]** をクリックします。
    
6. **[注文の受領書]** ページで、 **[続行]** をクリックします。
    
> [!NOTE]
> Enterprise Mobility + Security E5 試用版サブスクリプションの試用期間は 90 日間です。永続的な開発/テスト環境では、少数のライセンスを使用して新しい有料サブスクリプションを作成します。 
  
次に、すべてのユーザー アカウントに対して Enterprise Mobility + Security E5 ライセンスを有効にします。
  
1. ブラウザーの **[Office 365 管理センター]** タブの左側のナビゲーションで **[ユーザー] > [アクティブなユーザー]** の順にクリックします。
    
2. 全体管理者アカウントをクリックしてから、 **[製品ライセンス]** で **[編集]** をクリックします。
    
3. **[製品ライセンス]** ウィンドウで、 **Enterprise Mobility + Security E5** の製品ライセンスを **[オン]** にして、 **[保存]** をクリックしてから、 **[閉じる]** を 2 回クリックします。
    
4. 他のすべてのアカウント (User1、User 2、User 3、User 4、User 5) に対して、手順 2 と 3 を実行します。
    
開発/テスト環境には、以下が含まれるようになりました。
  
- Azure インフラストラクチャ サービスで実行されるシミュレートされたイントラネット。
    
- Office 365 E5 Enterprise と EMS の試用版サブスクリプションが、ユーザー アカウントの一覧と同じ組織および同じ Azure AD テナントを共有している。
    
- すべてのユーザー アカウントで Office 365 E5 Enterprise と EMS が使用可能になっている。
    
図 2 は、作成した構成に EMS が追加されたことを示しています。
  
**図 2: Office 365 と EMS の Azure でシミュレートされたイントラネット**

![Azure、Office 365、EMS が追加された One Microsoft Cloud 開発/テスト環境のフェーズ 2](images/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a>フェーズ 3: Dynamics 365 を追加します。

このフェーズでは、Dynamics 365 試用版サブスクリプションにサインアップして、Office 365 と EMS の試用版サブスクリプションと同じ組織に追加します。
  
1. デスクトップ コンピューターのいずれかのブラウザーを使用または、CLIENT1 からには、グローバル ・ アドミニストレータ ・ アカウントの資格情報を持つ[https://portal.office.com](https://portal.office.com)に Office 365 ポータルにサインインします。
    
2. 
            **[管理]** タイルをクリックします。
    
3. [ **Office 管理者センター** ] タブで、左側のナビゲーションでは、をクリックして**請求 > サービスを購入する**です。
    
4. **購買サービス**ページでは、 **Dynamics 365 1 Enterprise Edition の計画**の項目を検索します。上にマウス ポインターをポイントし、**無料の試用期間の開始**] をクリックします。
    
5. **[注文の確認]** ページで、 **[今すぐ実行]** をクリックします。
    
6. **[注文の受領書]** ページで、 **[続行]** をクリックします。
    
> [!NOTE]
> Dynamics 365 Plan 1 Enterprise Edition の試用版サブスクリプションは 30 日間有効です。試用版サブスクリプションは、追加で 30 日間まで簡単に延長できます。永続的な開発/テスト環境では、少数のライセンスを使用して新しい有料サブスクリプションを作成します。 
  
次の手順を使用して、Dynamics 365 ライセンスをグローバル管理者、User 2、User 3 のアカウントに割り当て、システム管理者とします。
  
1. [ **Office 管理者センター** ] タブをクリックして**ユーザー > アクティブなユーザー**。
    
2. 、アクティブなユーザーの一覧で、グローバル管理者アカウント] をクリックし、**製品ライセンス**の**編集**] をクリックします。
    
3. [**製品ライセンス**] ウィンドウで、**上**に**Dynamics 365 計画 1 のエンタープライズ エディション**の製品のライセンスを有効にする**、保存**、**閉じる**を 2 回クリックします。
    
4. User 2 と User 3 のアカウントに対して、手順 2 と 3 を実行します。
    
5. **Office 管理者センター** ] タブを閉じます。
    
次の手順を使用して、Dynamics 365 のシステム管理者として User 2 と User 3 のアカウントを構成します。
  
1. **Office 管理者センター** ] タブで、左側のナビゲーションでは、ブラウザーでの**管理を中央揃え**をクリック**Dynamics 365**です。
    
    Dynamics 365 がメニューに表示されるまで、Dynamics 365 のプロビジョニングの完了を待つ必要がある場合があります。
    
2. Dynamics 365] タブで**これらのすべて**] をクリックし、**セットアップを完了します**。
    
    セットアップが完了するまで待ちます。
    
    セットアップが完了すると、サブスクリプション記録の一部であるサンプル データに基づく販売活動のダッシュ ボードが表示されます。ビデオの**試用版の開始**を表示するのには、いくつかの時間がかかります。完了時にビデオ ウィンドウを閉じます。
    
3. ツールバーの上部にある、**販売**の横にある下向き矢印をクリックを選択し、**設定**] をクリックし、[**セキュリティ**] をクリックします。
    
4. [**セキュリティ**] ページで [**ユーザー**] をクリックします。
    
5. ユーザーの一覧では、**ユーザー 2**をクリックします。
    
6. ツール ・ バーでは、**ロールの管理**をクリックします。
    
7. **ロールの管理**は、**システム管理者**をクリックし、し、[ **OK**] をクリックします。
    
8. 上部にあるツールバーの [**セキュリティ**] をクリックします。
    
9. User 3 アカウントについて、手順 5 から 8 を繰り返します。
    
10. 閉じる、**ユーザー: User3**タブします。
    
> [!NOTE]
> Office 365 全体管理者アカウントに、Dynamics 365 のシステム管理者ロールが自動的に割り当てられました。 
  
開発/テスト環境には、以下が含まれるようになりました。
  
- Azure インフラストラクチャ サービスで実行されるシミュレートされたイントラネット。
    
- Office 365 E5 Enterprise、EMS、Dynamics 365 の試用版サブスクリプションが、ユーザー アカウントの一覧と同じ組織および同じ Azure AD テナントを共有している。
    
- すべてのユーザー アカウントで Office 365 E5 Enterprise と EMS が使用可能になっている。
    
- グローバル エンタープライズ管理者、User 2、および User 3 のアカウントが、Dynamics 365 を使用できるようになり、Dynamics 365 のシステム管理者になっている。
    
図 3 は、最終的な構成を示しています。
  
**図 3: Office 365、EMS、Dynamics 365 と Azure でシミュレートされたイントラネット**

![Azure、Office 365、EMS、Dynamics 365 が追加された One Microsoft Cloud 開発/テスト環境のフェーズ 3](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a>次の手順

これで、One Microsoft Cloud 開発/テスト環境を自由に試すことができます。ガイド付き体験のいくつかのアイデアをご紹介します。
  
- [Office 365 アプリケーションの EMS でモバイル アプリケーションの管理 (MAM) ポリシーを構成します。](https://technet.microsoft.com/library/mt764059.aspx)
    
- [Dynamics 365 の連絡先との統合を Office 365 で Exchange のオンライン デモンストレーションします。](https://technet.microsoft.com/library/mt798313.aspx)
    
- [Azure インフラストラクチャ サービスをサーバー ベースのワークロードをホストするためにシミュレートされた複数の環境に関するネットワークを作成します。](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a>関連項目

[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)
  
[ハイブリッド ソリューション](hybrid-solutions.md)
  
[セキュリティ ソリューション](security-solutions.md)





