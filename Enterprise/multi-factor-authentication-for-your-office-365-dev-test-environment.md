---
title: Office 365 開発/テスト環境用の多要素認証
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/20/2019
audience: ITPro
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
ms.openlocfilehash: 6e78d826cd010230218048ef320d8f32430ac02b
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "38032132"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a>Office 365 開発/テスト環境用の多要素認証

 **概要:** Office 365 の開発/テスト環境で、スマート フォンに送信されるテキスト メッセージを使用して多要素認証を構成します。
  
Office 365 サブスクリプションにサインインするための追加のセキュリティレベルについては、Azure 多要素認証を有効にすることができます。これには、アカウントを認証するためにユーザー名とパスワードだけを必要とします。 Office 365 に多要素認証を使用する場合、ユーザーは電話での通話の承認、テキストメッセージで送信された検証コードの入力、またはスマートフォンのパスワードを正しく入力した後にアプリのパスワードを指定する必要があります。 この第 2 の認証要素が満たされた後でのみ、ユーザーはサインインできます。 
  
この記事では、特定の Office 365 アカウントに対してテキスト メッセージ ベースの認証を有効にしてテストする方法について説明します。
  
開発/テスト環境での Office 365 の多要素認証のセットアップには、次の 2 つのフェーズがあります。
  
1. Office 365 開発/テスト環境を作成します。
    
2. User 2 アカウントに対して、多要素認証を有効にしてテストします。
    
> [!TIP]
> [ここ](https://aka.ms/catlgstack)をクリックして、Office 365 のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップを確認してください。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>フェーズ 1: ライトウェイトの、またはシミュレーションのエンタープライズ Office 365 開発/テスト環境を構築する

最小要件での軽量な方法で多要素認証をテストするだけの場合は、 [Office 365 開発/テスト環境](office-365-dev-test-environment.md)のフェーズ2とフェーズ3の手順に従ってください。
  
シミュレートされたエンタープライズで多要素認証をテストする場合は、「 [365 Office のディレクトリ同期の開発/テスト環境](dirsync-for-your-office-365-dev-test-environment.md)」の手順に従ってください。
  
> [!NOTE]
> 多要素認証のテストでは、シミュレートされたエンタープライズ開発/テスト環境を使用する必要はありません。これには、インターネットに接続されたシミュレートされたイントラネットと Active Directory ドメインサービス (AD DS) フォレストのディレクトリ同期が含まれます。 この指示は、一般的な組織と類似した環境で多要素認証をテストしてお試しいただけるようオプションとしてここで提供しています。 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>フェーズ 2:User 2 アカウントに対して、多要素認証を有効にしてテストする

次の手順を実行して、User 2 アカウントに対して多要素認証を有効にしてテストします。
  
1. ブラウザーの別のインスタンスを開き、Office 365 ポータル ([https://www.office.com](https://www.office.com)) に移動し、全体管理者アカウントを使用して office 365 試用版サブスクリプションにサインインします。
    
2. ポータルのメイン ページで、**[管理]** をクリックします。
    
3. 左側のナビゲーションで、**[ユーザー] > [アクティブなユーザー]** をクリックします。
    
4. [アクティブなユーザー] ウィンドウで、[ **More > 多要素認証のセットアップ**] をクリックします。
    
5. リストで、 **User 2**アカウントを選択します。
    
6. **User 2** セクションで、**[クイック操作]** の **[有効にする]** をクリックします。
    
7. **[多要素認証を有効にする方法の概要]** ダイアログ ボックスで、**[Multi-Factor Auth を有効にする]** をクリックします。
    
8. [**更新が成功しまし**た] ダイアログボックスで、[**閉じる**] をクリックします。
    
9. **[Microsoft Office Home]** タブで、右上部分にあるユーザー アカウントのアイコンをクリックし、**[サインアウト]** をクリックします。
    
10. ブラウザー インスタンスを閉じます。
    
次の手順を実行して、User 2 アカウントで確認のためにテキスト メッセージを使用するように構成を完了し、それをテストします。
  
1. ブラウザーの新しいインスタンスを開きます。
    
2. Office 365 ポータル ([https://www.office.com](https://www.office.com)) に移動し、User 2 アカウントでサインインします (user2@\<組織名> onmicrosoft.com) とパスワード。
    
3. サインイン後、追加のセキュリティ検証のためにアカウントを設定するように求められます。**[今すぐセットアップ]** をクリックします。
    
4. **[追加のセキュリティ確認]** ページで、次の手順を実行します。 
    
  - 国または地域を選択します。
    
  - テキスト メッセージを受信するスマート フォンの電話番号を入力します。
    
  - [**メソッド**] の [**テキストメッセージでコードを送信する**] をクリックします。
    
5. **[次へ]** をクリックします。
    
6. スマート フォンで受信したテキスト メッセージに記載されている確認コードを入力して、**[確認]** をクリックします。
    
7. **[手順 3: 既存のアプリケーションを使用し続ける]** ページで、User 2 アカウント用に表示されているアプリ パスワードを安全な場所に記録してから、**[完了]** をクリックします。
    
8. User 2 アカウントでサインインするのが今回で初めての場合、パスワードの変更を求められます。元のパスワードと、新しいパスワードを 2 回入力して、**[パスワードを更新してサインイン]** をクリックします。新しいパスワードを安全な場所に記録します。
    
    ブラウザーの [ **Microsoft Office Home** ] タブに、ユーザー2用の Office 365 ポータルが表示されます。
    
## <a name="see-also"></a>関連項目

[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基本構成開発/テスト環境](base-configuration-dev-test-environment.md)
  
[Office 365 開発/テスト環境](office-365-dev-test-environment.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)

[Office 365 の展開で多要素認証を計画する](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

