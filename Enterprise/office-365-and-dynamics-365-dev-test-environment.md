---
title: Office 365 と Dynamics 365 の開発/テスト環境
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
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: '概要: は、Dynamics 365 を Office 365 の開発/テスト環境に追加するのには、このテスト ラボ ガイド 』 を使用します。'
ms.openlocfilehash: 24f121c9e5f8a25bae61ce4a59b42d528ffbda17
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a>Office 365 と Dynamics 365 の開発/テスト環境

 **の概要:**Dynamics 365 を Office 365 の開発/テスト環境に追加するのにには、このテスト ラボ ガイド 』 を使用します。
  
この記事の手順を使用して、Dynamics 365 試用版サブスクリプションを Office 365 開発/テスト環境と同じ組織に追加し、Office 365 と Dynamics 365 の開発/テスト環境を作成します。
  
Dynamics 365 試用版サブスクリプションを使用して、Dynamics 365 の機能をデモンストレーションすることができます。Dynamics 365 プラン 1、Enterprise Edition 試用版には、以下のソリューションが含まれています。
  
- [Microsoft Dynamics 365 販売](https://www.microsoft.com/dynamics365/sales)します。オートメーションと販売員の対応に専念し、手際よく作業を支援するデジタル インテリジェンスの売上を増加します。
    
- [Microsoft Dynamics 365 の顧客サービス](https://www.microsoft.com/dynamics365/customer-service)です。ロイヤルティを獲得するには、完全な情報とデジタル情報のシームレスなサービスを提供する必要があるエージェントを提供します。
    
- [フィールド サービス用の Microsoft Dynamics 365](https://www.microsoft.com/dynamics365/field-service)です。マスター サービスを呼び出す、スケジュールを最適化する、離れたり、人員、および予測ツールを使用して利益を向上させます。
    
- [Microsoft Dynamics 365 プロジェクト サービスの自動化のため](https://www.microsoft.com/en-us/dynamics365/project-service-automation)です。プロジェクトが正常に完了し、従業員の生産性を向上し、インテリジェントなツールを使用して収益性の高い関係を作成します。
    
Dynamics 365 試用版サブスクリプションでは、上記の 1 つ以上をお試しいただけます。
  
![Microsoft Cloud のテスト ラボ ガイド](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> 
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>フェーズ 1:ライトウェイトの、またはシミュレーションのエンタープライズ Office 365 開発/テスト環境を構築する

最小要件で軽量な方法で Office 365 と Dynamics 365 をテストする場合は、フェーズ 2 と 3[の開発/テスト環境を Office 365](office-365-dev-test-environment.md)の指示に従います。
  
シミュレートされた企業の Office 365 と Dynamics 365 をテストする場合は、 [Office 365 の開発/テスト環境のディレクトリ同期](dirsync-for-your-office-365-dev-test-environment.md)に指示します。
  
> [!NOTE]
> この記事の構成には、シミュレーションのエンタープライズ開発/テスト環境は必要ありません。シミュレーションのエンタープライズ開発/テスト環境には、インターネットに接続されたシミュレーションのイントラネット、Windows サーバー AD フォレスト用のディレクトリ同期が含まれています。この機能は、一般的な組織と類似した環境で Office 365 と Dynamics 365 を試していただけるようオプションとしてここで提供されています。 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a>フェーズ 2:Dynamics 365 試用版サブスクリプションを追加する

このフェーズでは、Office 365 試用版サブスクリプションにサインアップして、Office 365 試用版サブスクリプションと同じ組織に追加します。
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a>Dynamics 365 試用版サブスクリプションにサインアップする

1. デスクトップ コンピューター (軽量) のいずれかのブラウザーを使用してまたは CLIENT1 から (エンタープライズをシミュレートした) に Office 365 ポータルにサインインするのに[https://portal.office.com](https://portal.office.com)のグローバル管理者アカウントの資格情報を持つ。
    
2. 
            **[管理]** タイルをクリックします。
    
3. [ **Office 管理者センター** ] タブで、左側のナビゲーションでは、をクリックして**請求 > サービスを購入する**です。
    
4. **購買サービス**ページでは、 **Dynamics 365 1 Enterprise Edition の計画**の項目を検索します。上にマウス ポインターをポイントし、**無料の試用期間の開始**] をクリックします。
    
5. **[注文の確認]** ページで、 **[今すぐ実行]** をクリックします。
    
6. **[注文の受領書]** ページで、**[続行]** をクリックします。
    
> [!NOTE]
> Dynamics 365 Plan 1 Enterprise Edition の試用版サブスクリプションは 30 日間有効です。試用版サブスクリプションは、追加で 30 日間まで簡単に延長できます。永続的な開発/テスト環境では、少数のライセンスを使用して新しい有料サブスクリプションを作成します。 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a>フェーズ 3：Dynamics 365 ライセンスとシステム管理者を割り当てる

このフェーズでは、Dynamics 365 ライセンスをグローバル管理者、User 2、User 3 のアカウントに割り当て、システム管理者とします。
  
Dynamics 365 ライセンスを割り当てるには次の手順を使用します。
  
1. [ **Office 管理者センター** ] タブをクリックして**ユーザー > アクティブなユーザー**。
    
2. 、アクティブなユーザーの一覧で、グローバル管理者アカウント] をクリックし、**製品ライセンス**の**編集**] をクリックします。
    
3. [**製品ライセンス**] ウィンドウで、**上**に**Dynamics 365 計画 1 のエンタープライズ エディション**の製品のライセンスを有効にする**、保存**、**閉じる**を 2 回クリックします。
    
4. User 2 と User 3 のアカウントに対して、手順 2 と 3 を実行します。
    
5. **Office 管理者センター** ] タブを閉じます。
    
次の手順を使用して、Dynamics 365 のシステム管理者として User 2 と User 3 のアカウントを構成します。
  
1. **Microsoft Office ホーム**] タブから、[**管理**を] をクリックします。
    
2. [ **Office 管理者センター** ] タブで、左側のナビゲーションでは、**管理センター**をを**Dynamics 365**] をクリックします。
    
    Dynamics 365 がメニューに表示されるまで、Dynamics 365 のプロビジョニングの完了を待つ必要がある場合があります。
    
3. Dynamics 365] タブで**これらのすべて**] をクリックし、**セットアップを完了します**。
    
    セットアップが完了するまで待ちます。
    
    セットアップが完了すると、サブスクリプション記録の一部であるサンプル データに基づく販売活動のダッシュ ボードが表示されます。ビデオの**試用版の開始**を表示するのには、いくつかの時間がかかります。完了時にビデオ ウィンドウを閉じます。
    
4. ツールバーの上部にある、**販売**の横にある下向き矢印をクリックを選択し、**設定**] をクリックし、[**セキュリティ**] をクリックします。
    
5. [**セキュリティ**] ページで [**ユーザー**] をクリックします。
    
6. ユーザーの一覧では、**ユーザー 2**をクリックします。
    
7. ツール ・ バーでは、**ロールの管理**をクリックします。
    
8. **ロールの管理**は、**システム管理者**をクリックし、し、[ **OK**] をクリックします。
    
9. 上部にあるツールバーの [**セキュリティ**] をクリックします。
    
10. User 3 アカウントについて、手順 5 から 8 を繰り返します。
    
11. 閉じる、**ユーザー: User3**タブします。
    
> [!NOTE]
> Office 365 全体管理者アカウントに、Dynamics 365 のシステム管理者ロールが自動的に割り当てられました。 
  
この段階で、Office 365 と Dynamics 365 の開発/テスト環境の状態は次のようになっています。
  
- Office 365 E5 Enterprise と Dynamics 365 の試用版サブスクリプションが、ユーザー アカウントの一覧と同じ組織および同じ Azure AD テナントを共有している。
    
- グローバル エンタープライズ管理者、User 2、User 3 のアカウントが、Office 365 E5 Enterprise と Dynamics 365 の両方を使用できるようになり、Dynamics 365 のシステム管理者になっている。
    
## <a name="next-step"></a>次の手順

構成し、Office 365 と Dynamics 365 のしくみまとめて[Office 365 と Dynamics 365 の開発/テスト環境に Exchange Online](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)の統合オンラインの Exchange メールボックスを示します。
  
## <a name="see-also"></a>関連項目

[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基本構成開発/テスト環境](base-configuration-dev-test-environment.md)
  
[Office 365 開発/テスト環境](office-365-dev-test-environment.md)
  
[Office 365 開発/テスト環境の DirSync](dirsync-for-your-office-365-dev-test-environment.md)

[Dynamics 365 (オンライン) のサブスクリプション管理](https://technet.microsoft.com/library/jj679903.aspx)
  
[Dynamics 365 の管理](https://technet.microsoft.com/library/dn531101.aspx)


