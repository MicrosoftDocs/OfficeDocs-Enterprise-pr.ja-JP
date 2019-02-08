---
title: Office 365 開発/テスト環境用の多要素認証
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/22/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: 概要:Office 365 の開発/テスト環境で、スマート フォンに送信されるテキスト メッセージを使用して多要素認証を構成します。
ms.openlocfilehash: 6e2aefa9309e7e268c937055f7fe59600f8c87da
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897450"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Office 365 開発/テスト環境用の多要素認証

 **概要:** Office 365 の開発/テスト環境で、スマート フォンに送信されるテキスト メッセージを使用して多要素認証を構成します。
  
Office 365 サブスクリプションへのサインインのセキュリティのレベルを上げる、ためだけで複数のユーザー名とアカウントを認証するパスワードが必要ですが、Azure の多要素認証を有効にできます。Office 365 の多要素認証を使用する必要があります確認の電話、テキスト メッセージで送信された確認コードを入力、または自分のパスワードを正しく入力した後、スマート フォンのアプリのパスワードを指定します。この 2 番目の認証要素が満たされた後にのみ、サインインできます。 
  
この記事では、特定の Office 365 アカウントに対してテキスト メッセージ ベースの認証を有効にしてテストする方法について説明します。
  
開発/テスト環境での Office 365 の多要素認証のセットアップには、次の 2 つのフェーズがあります。
  
1. Office 365 開発/テスト環境を作成します。
    
2. User 2 アカウントに対して、多要素認証を有効にしてテストします。
    
> [!TIP]
> [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>フェーズ 1: ライトウェイトの、またはシミュレーションのエンタープライズ Office 365 開発/テスト環境を構築する

最小要件で軽量な方法で複数要素の認証をテストする場合は、フェーズ 2 と 3[の開発/テスト環境を Office 365](office-365-dev-test-environment.md)の指示に従います。
  
シミュレートされた企業内の複数要素の認証をテストする場合は、 [Office 365 の開発/テスト環境のディレクトリ同期](dirsync-for-your-office-365-dev-test-environment.md)に指示します。
  
> [!NOTE]
> 多要素認証をテストするのに、インターネットに接続されたシミュレーション イントラネットと Windows Server AD フォレスト用のディレクトリ同期を含めた、シミュレーション エンタープライズの開発/テスト環境は必要ではありません。この指示は、一般的な組織と類似した環境で多要素認証をテストしてお試しいただけるようオプションとしてここで提供しています。 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>フェーズ 2:User 2 アカウントに対して、多要素認証を有効にしてテストする

次の手順を実行して、User 2 アカウントに対して多要素認証を有効にしてテストします。
  
1. お使いのブラウザーの別のインスタンスを開き、Office 365 ポータルに移動 ([https://portal.office.com](https://portal.office.com)) にサインインし、グローバル管理者アカウントを使用して、Office 365 の試用版サブスクリプションにします。
    
2. ポータルのメイン ページで、**[管理]** をクリックします。
    
3. 左側のナビゲーションで、**[ユーザー] > [アクティブなユーザー]** をクリックします。
    
4. [アクティブなユーザー] ウィンドウで、**[その他] > [Azure Multi-Factor Authentication のセットアップ]** をクリックします。
    
5. の一覧では、 **2 のユーザー**アカウントを選択します。
    
6. **User 2** セクションで、**[クイック操作]** の **[有効にする]** をクリックします。
    
7. **[多要素認証を有効にする方法の概要]** ダイアログ ボックスで、**[Multi-Factor Auth を有効にする]** をクリックします。
    
8. **[更新が正常に完了しました]** ダイアログ ボックスで、**[閉じる]** をクリックします。
    
9. **[Microsoft Office Home]** タブで、右上部分にあるユーザー アカウントのアイコンをクリックし、**[サインアウト]** をクリックします。
    
10. ブラウザー インスタンスを閉じます。
    
次の手順を実行して、User 2 アカウントで確認のためにテキスト メッセージを使用するように構成を完了し、それをテストします。
  
1. ブラウザーの新しいインスタンスを開きます。
    
2. Office 365 ポータルに移動 ([https://portal.office.com](https://portal.office.com)) と 2 のユーザー アカウントでサインイン (user2 @\<組織 name>.onmicrosoft.com) とパスワードです。
    
3. サインイン後、追加のセキュリティ検証のためにアカウントを設定するように求められます。**[今すぐセットアップ]** をクリックします。
    
4. **[追加のセキュリティ確認]** ページで、次の手順を実行します。 
    
  - 国または地域を選択します。
    
  - テキスト メッセージを受信するスマート フォンの電話番号を入力します。
    
  - **メソッド**では、**コード、テキスト メッセージを送信してもらう**をクリックします。
    
5. [ **次へ**] をクリックします。
    
6. スマート フォンで受信したテキスト メッセージに記載されている確認コードを入力して、**[確認]** をクリックします。
    
7. **[手順 3: 既存のアプリケーションを使用し続ける]** ページで、User 2 アカウント用に表示されているアプリ パスワードを安全な場所に記録してから、**[完了]** をクリックします。
    
8. User 2 アカウントでサインインするのが今回で初めての場合、パスワードの変更を求められます。元のパスワードと、新しいパスワードを 2 回入力して、**[パスワードを更新してサインイン]** をクリックします。新しいパスワードを安全な場所に記録します。
    
    お使いのブラウザーの [ **Microsoft Office のホーム**] タブで、Office 365 ポータルのユーザー 2 のはずです。
    
## <a name="see-also"></a>関連項目

[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基本構成開発/テスト環境](base-configuration-dev-test-environment.md)
  
[Office 365 開発/テスト環境](office-365-dev-test-environment.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)

[Office 365 展開用の多要素認証の計画](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

