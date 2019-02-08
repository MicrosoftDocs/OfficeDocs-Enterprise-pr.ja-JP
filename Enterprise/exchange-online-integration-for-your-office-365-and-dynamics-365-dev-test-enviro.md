---
title: Office 365 と Dynamics 365 の開発/テスト環境の Exchange Online 統合
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 499c5823-427a-4ba2-8fc1-9553bc2ff2d3
description: '概要: このテスト ラボ ガイドを使用して、Office 365 試用版サブスクリプションで Exchange Online 向けの Dynamics 365 統合を有効にします。'
ms.openlocfilehash: 97e480bd148092f8e8e5ab610f0aed0a5eb2e20e
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897120"
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a>Office 365 と Dynamics 365 の開発/テスト環境の Exchange Online 統合

 **概要:** このテスト ラボ ガイドを使用して、Office 365 試用版サブスクリプションで Exchange Online 向けの Dynamics 365 統合を有効にします。
  
Microsoft Dynamics 365 の 1 つの有用な使用法は、適切なアクセス許可を持つユーザーが関連する顧客レコードすべてを参照できるよう、すべての顧客コミュニケーションを 1 つの場所に格納することです。たとえば、特定の連絡先、アカウント、営業案件、サポート案件などに関連付けられているすべての電子メールを閲覧できます。
  
Dynamics 365 に電子メールと他のメッセージング レコードを保存するには、お使いのメール システムと Dynamics 365 を同期する必要があります。電子メールを同期する最適な方法は、サーバー側同期です。
  
このテスト ラボ ガイドを使用して、Dynamics 365 に保存されている情報を Exchange Online と Outlook Online クライアントで活用するための構成とデモンストレーションを実行します。 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a>フェーズ 1: Office 365 と Dynamics 365 開発/テスト環境を構成する

「[Office 365 と Dynamics 365 の開発/テスト環境](office-365-and-dynamics-365-dev-test-environment.md)」の手順を実行して、Office 365 と Dynamics 365 の開発/テスト環境のライトウェイト、またはシミュレーションのエンタープライズ バージョンを作成します。
  
> [!NOTE]
> この記事の構成には、シミュレーションのエンタープライズ開発/テスト環境は必要ありません。シミュレーションのエンタープライズ開発/テスト環境には、インターネットに接続されたシミュレーションのイントラネット、Windows Server Active Directory (AD) フォレスト用のディレクトリ同期が含まれています。この機能は、一般的な組織と類似した環境で Office 365 と Dynamics 365 を試していただけるよう、オプションとしてここで提供されています。 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a>フェーズ 2: Exchange Online の Dynamics 365 統合を構成しデモンストレーションする

以下の手順を使用して、Dynamics 365 と Exchange Online 統合用の全体管理者のメールボックスを構成します。
  
1. お使いのブラウザーのプライベート ・ セッションを使用して[http://portal.office.com](http://portal.office.com)し、Office 365 のグローバル管理者アカウントを使用してサインインします。
    
2. **Microsoft Office ホーム** ページで、 **[メール]** タイルをクリックします。
    
3. ブラウザーの [新しい**メール**] タブ、[**新規**] をクリックし、メッセージを入力するボックスの下のウィンドウの下隅がマイ テンプレートのアイコンには、方法に注意してください。
    
     ![Dynamics 365 との統合なしの、新しい空の電子メール メッセージ。](media/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. **[破棄]** をクリックして、 **[メール]** タブを開いたままにします。
    
5. ブラウザーの **[Microsoft Office ホーム]** タブをクリックし、次いで **[管理者]** タイルをクリックします。
    
6. **[Office 管理センター]** タブの左側のナビゲーションで、 **[管理センター]、[Dynamics 365]** の順にクリックします。
    
7. お使いのブラウザーの新しい **[Dynamics 365]** タブで、Dynamics 365 のインスタンスの一覧から、 **[開く]** をクリックします。
    
8. お使いのブラウザーの新しい **[管理]** タブで、ナビゲーション バーの **[設定]** の横の下矢印をクリックして、 **[システム]** の下にある **[電子メールの構成]** をクリックします。
    
9.  **[電子メールの構成]** ページで **[電子メール構成の設定]** をクリックします。
    
10. **[システム設定]** ダイアログ ボックスの **[電子メール]** タブで、 **[予定、取引先担当者、タスク]** を **[サーバー側同期]** に変更し、次いで **[OK]** をクリックします。
    
11. **[電子メールの構成]** ページで、 **[メールボックス]** をクリックします。
    
12. 左側のチェック マークの列で Office 365 の全体管理者名を選択し、ツール バーの **[既定の電子メール設定を適用]** をクリックし、次いで **[OK]** をクリックします。
    
13. ツール バーの **[電子メールの承認]** をクリックし、次いで **[OK]** をクリックします。
    
14. 左側のチェック マークの列で Office 365 の全体管理者名を選択し、ツール バーの **&amp;[メールボックスのテストと有効化]** をクリックし、次いで **[OK]** をクリックします。
    
15. 開いている **[メール]** タブをクリックして全体管理者がテスト メッセージを受信したことを確認します。
    
16. ブラウザーで、メールボックスの **[自分のアクティブなメールボックス]** タブに戻り、ページを更新します。全体管理者のアカウント名で、 **[受信メールの状態]** と **[送信メールの状態]** の列が **[正常に完了]** に設定されるはずです。両方のテストを完了するのに 15 分ほどかかるかもしれません。
    
以下の手順を使用して、Outlook 用の Dynamics 365 アプリをインストールし、全体管理者のメールボックス内で Dynamics 365 の機能をデモンストレーションします。
  
1. ブラウザーのメールボックスの **[自分のアクティブなメールボックス]** タブで、 **[設定]** の隣の下矢印をクリックして、 **[システム]** の下にある **[Outlook 用 Dynamics 365 アプリ]** をクリックします。
    
2. **[Outlook 用 Microsoft Dynamics 365 アプリをお使いになる前に]** のページで、全体管理者名をクリックし、次いで **[Outlook へのアプリの追加]** をクリックします。 **[状態]** 列が **[保留中]** に変わります。
    
3. 状態が **[Outlook に追加済み]** に変わるまで、ページを更新します。この構成を完了するのに 15 分ほどかかるかもしれません。
    
4. ブラウザーの **[メール]** タブをクリックし、次いでそれを閉じます。
    
5. ブラウザーの **[Microsoft Office ホーム]** タブをクリックし、次いで **[メール]** タイルをクリックします。
    
6. ブラウザーの [新しい**メール**] タブ、[**新規**] をクリックします。今すぐメッセージを入力するためのボックスの下のウィンドウの下隅にある Dynamics 365 のアイコンに注目してください。
    
     ![新しいアイコンが表示される、Dynamics 365 と統合された新しい空の電子メール メッセージ。](media/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. [Dynamics 365] アイコンをクリックします。 **Dynamics 365** ウィンドウが表示されます。そこからこの電子メールを追跡したり、テンプレート、営業資料、記事などにアクセスしたりできます。
    
8. 電子メール メッセージの **[宛先]** フィールドに、 **alex.y.wu@outlook.com** とタイプし、次いで、 **Dynamics 365** ウィンドウの **[再試行]** をクリックします。 **Dynamics 365** ウィンドウの **[受信者]** セクションに、試用版サブスクリプションのサンプル データと共に提供されている、販売アプリケーションの取引先担当者 Alex Wu の情報が表示されるはずです。
    
     ![Dynamics 365 に格納されている営業担当者用の Dynamics 365 情報ウィンドウ。](media/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. **[破棄]** をクリックします。

> [!TIP]
> [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。
    
## <a name="see-also"></a>関連項目

[Office 365 と Dynamics 365 の開発/テスト環境](office-365-and-dynamics-365-dev-test-environment.md)
  
[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基本構成開発/テスト環境](base-configuration-dev-test-environment.md)
  
[Office 365 開発/テスト環境](office-365-dev-test-environment.md)
  
[Office 365 開発/テスト環境の DirSync](dirsync-for-your-office-365-dev-test-environment.md)

[Dynamics 365 (オンライン) のサブスクリプション管理](https://technet.microsoft.com/library/jj679903.aspx)
  
[Dynamics 365 の管理](https://technet.microsoft.com/library/dn531101.aspx)


