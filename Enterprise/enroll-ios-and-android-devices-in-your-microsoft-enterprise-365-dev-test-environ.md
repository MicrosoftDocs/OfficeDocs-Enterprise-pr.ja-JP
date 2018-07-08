---
title: Microsoft 365 Enterprise 開発/テスト環境に iOS および Android デバイスを登録する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: '概要: ガイドを使用してこのテスト ラボ Microsoft 365、開発/テスト環境でデバイスを登録し、それらをリモートで管理します。'
ms.openlocfilehash: a5d43a0ef3ed090f84c8415de3ac26f53fdafe0a
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188105"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 Enterprise 開発/テスト環境に iOS および Android デバイスを登録する

 **の概要:** Microsoft 365、開発/テスト環境でデバイスを登録し、それらをリモートで管理するには、このテスト ラボ ガイド 』 を使用します。
  
Microsoft エンタープライズ モビリティ スイート (EMS) では、組織のデータを保護しながら、お気に入りのアプリケーションとデバイスを使用して生産性の高い従業員を保つことができます。詳細については、[エンタープライズ ・ モビリティとセキュリティ (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)を参照してください。
  
デバイス ・ レベルでセキュリティを適用する場合は、Microsoft Intune にデバイスを登録する必要があります。デバイスの登録を組織が所有するデバイスを管理するために役立つだけでなく個人 (BYOD) と共有デバイスには、組織が法的なのもいますが、ポリシーです。
  
によって、この資料に記載されている手順に従うことができます登録し、iOS および Android デバイスの基本的なモバイル デバイス管理の機能を Microsoft 365 開発/テスト環境でテストします。
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>フェーズ 1: Microsoft 365 の開発/テスト環境を作成します。

[[Microsoft 365 エンタープライズ開発/テスト環境](the-microsoft-365-enterprise-dev-test-environment.md)での指示に従います。
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>フェーズ 2: iOS および Android デバイスを登録します。

指示を使用して、最初に、[をインストールし、会社のポータル アプリケーションにサインイン](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios)、開発/テストのテナントの Microsoft Intune 会社のポータル アプリケーションをカスタマイズするのには。

次に、手順を使用[、会社のリソースへのアクセス権を設定](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)iOS デバイスを登録します。

次に、手順を使用[Intune に Android デバイスの登録](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)Android のデバイスを登録します。

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a>フェーズ 2: は、iOS および Android のデバイスをリモートで管理します。

Microsoft Intune には、リモート ロック機能とパスコードのリセット機能あります。ユーザーがデバイスを紛失した場合は、デバイスをリモートからロックできます。ユーザーがパスコードを忘れた場合は、パスコードをリモートから削除できます。
  
iOS デバイスをリモートからロックするには、
  
1.  新しいタブを開きに移動http://manage.microsoft.com(必要な場合)。 

2.  お使いのブラウザーの Microsoft Intune 管理コンソールで、左側のナビゲーションの**グループ**をクリックします。

3. **[グループ]** ウィンドウで、**[すべてのデバイス]、[すべてのモバイル デバイス]、[ダイレクト管理されているすべてのデバイス]** の順に開きます。
    
4. **[ダイレクト管理されているすべてのデバイス]** ウィンドウで、**[デバイス]** タブをクリックします。
    
5. デバイスの一覧で、対象の iOS デバイスをクリックします。  
    
6. iOS デバイスから、そのデバイスのメイン画面が表示されていることを確認します。  
    
7. 管理用コンピューターから、タスクバーで、**[リモート タスク]、[リモート ロック]** をクリックします。対象の iOS デバイスがロックアウト画面に切り替わる様子を確認します。
    
パスコードを削除するには、
  
1. 管理用コンピューターから、**[ダイレクト管理されているすべてのデバイス]** ウィンドウで、**[デバイス]** タブをクリックします。
    
2. 一覧で、対象の iOS デバイスをクリックします。タスクバーで、**[リモート タスク]、[パスコードのリセット]** をクリックします。1 分間待機します。
    
3. 対象の iOS デバイスから、そのデバイスのロックを解除して、パスコードがなくなっていることを確認します。パスコードを変更して元に戻すには、**[設定]**、**[パスコード]** の順に移動します。
    
Android デバイスをリモートからロックするには、
  
1. お使いのブラウザーの Microsoft Intune 管理コンソールで、左側のナビゲーションの**グループ**をクリックします。
    
2. **[グループ]** ウィンドウで、**[すべてのデバイス]、[すべてのモバイル デバイス]、[ダイレクト管理されているすべてのデバイス]** の順に開きます。
    
3. **[ダイレクト管理されているすべてのデバイス]** ウィンドウで、**[デバイス]** タブをクリックします。
    
4. デバイスの一覧で、目的の Android デバイスをクリックします。  
    
5. 対象の Android デバイスから、そのデバイスのメイン画面が表示されていることを確認します。  
    
6. 管理用コンピューターから、タスクバーで、**[リモート タスク]、[リモート ロック]** をクリックします。ダイアログが表示されたら、**[はい]** をクリックします。
    
7. 対象の Android デバイスがロックアウト画面に切り替わる様子を確認します。
    
Android デバイスのパスコードをリセットすると、Intune 管理ポータルを生成し、強力なパスコードを設定します。
  
パスコードをリモートからリセットするには、
  
1. 管理用コンピューターから、ブラウザーの Microsoft Intune 管理コンソール タブにある **[ダイレクト管理されているすべてのデバイス]** ウィンドウで、目的の Android デバイスをクリックします。
    
2. タスクバーで、**[リモート タスク] > [パスコードのリセット]** をクリックします。
    
3. **[リモート タスク: パスコードのリセット]** ダイアログで、**[はい]** をクリックします。1 分間待機します。
    
4. **[ダイレクト管理されているすべてのデバイス]** ウィンドウで、**[プロパティの表示]** をクリックします。
    
5. **[パスコードのリセット]** の下に、新しいパスコードが表示されています。
    
6. Android でデバイスのロックアウト画面から、新しいパスコードを入力します。  
    
7. パスコードを変更して元に戻すには、**[設定]** に移動し、**[デバイス]**、**[ロック画面]** の順にタップして、新しいパスコードを再度入力し、**[画面のロック]** をタップしてパスコードを選択します。
    

> [!TIP]
> [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。
  
## <a name="see-also"></a>関連項目

[Microsoft 365 Enterprise 開発/テスト環境](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 Enterprise 開発/テスト環境の MAM のポリシー](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[エンタープライズ モビリティとセキュリティ (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


