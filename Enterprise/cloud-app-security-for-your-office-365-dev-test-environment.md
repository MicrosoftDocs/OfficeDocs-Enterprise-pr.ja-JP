---
title: "Office 365 開発/テスト環境の Cloud App Security"
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
- Ent_O365_Top
ms.custom:
- DecEntMigration
- TLG
- Ent_TLGs
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: "概要: Office 365 開発/テスト環境で Office 365 Cloud App Security を構成し、デモンストレーションします。"
ms.openlocfilehash: 1fab5ebfd6e0670ba59fe34b2cca8a7282e75723
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a>Office 365 開発/テスト環境の Cloud App Security

 **概要:** Office 365 開発/テスト環境で Office 365 Cloud App Security を構成し、デモンストレーションします。
  
Office 365 Cloud App Security (以前は「Office 365 の高度なセキュリティ管理」と呼ばれていた) を使用すると、Office 365 サブスクリプションでの不審なアクティビティを監視し、通知するポリシーを作成できます。それによって調査と、是正アクションの実行が可能になります。詳細については、「[Office 365 の Advanced Security Management の概要](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)」を参照してください。
  
この記事の手順を使用して、Office 365 の試用版サブスクリプションで Cloud App Security を有効にし、テストできます。
  
> [!TIP]
> [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a>フェーズ 1:ライトウェイトの、またはシミュレーションのエンタープライズ Office 365 開発/テスト環境を構築する

最小要件で、負荷の小さい方法で Cloud App Security をテストする場合は、[Office 365 開発/テスト環境](office-365-dev-test-environment.md) のフェーズ 2 とフェーズ 3 の手順に従ってください。
  
シミュレーションのエンタープライズで Cloud App Security をテストする場合は、[Office 365 開発/テスト環境の DirSync](dirsync-for-your-office-365-dev-test-environment.md) の手順に従ってください。
  
> [!NOTE]
> Cloud App Security のテストには、シミュレーションのエンタープライズ開発/テスト環境は必要ありません。シミュレーションのエンタープライズ開発/テスト環境には、インターネットに接続されたシミュレーションのイントラネット、Windows Server AD フォレスト用のディレクトリ同期が含まれています。この機能は、一般的な組織と類似した環境で Cloud App Security をテストしてお試しいただけるよう、オプションとしてここで提供されています。 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a>フェーズ 2: Cloud App Security の有効化およびポリシーの作成の前に

この手順では、Cloud App Security を有効にする前の状態で、ユーザーのロールを変更しても全体管理者に電子メール通知が送信されないことを確認します。
  
### <a name="test-the-default-notification-behavior-of-office-365"></a>Office 365 の既定の通知動作をテストする

1. Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) に移動し、グローバル管理者アカウントで Office 365 試用版サブスクリプションにサインインします。
    
  - ライトウェイトの Office 365 開発/テスト環境を使用している場合は、ローカル コンピューターからサインインします。
    
  - シミュレーションのエンタープライズ Office 365 開発/テスト環境を使用している場合は、[Azure ポータル](https://portal.azure.com) を使用して CLIENT1 仮想マシンに接続し、CLIENT1 からサインインします。
    
2. ポータルのメイン ページで、 **[管理]** をクリックします。
    
3. 左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。
    
4. **[User 4]** アカウントをクリックします。
    
5. **[User 4]** ページで、 **[ロール]**行の **[編集]** をクリックします。
    
6. **[ユーザー ロールの編集]** ページで、 **[全体管理者]** をクリックし、 **[代替電子メール アドレス]** に **user4@contoso.com** と入力し、 **[保存]** をクリックします。 **[閉じる]** を 2 回クリックします。
    
7. 左上部分にあるアプリ起動ツールのアイコンを選択し、 **[メール]** をクリックします。
    
8. 30 分間待ちます。User 4 のロールが全体管理者に変更されたことを通知する電子メール メッセージが、受信トレイにないことにご注意ください。
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a>フェーズ 3: Cloud App Security を有効にし、ポリシーを作成する

この手順では、Cloud App Security を有効にして新しいポリシーを作成し、ユーザー アカウントのロールが変更された場合に、電子メール通知を全体管理者のアカウントに送信するようにします。この手順では、以下が必要です。
  
- Office 365 試用版サブスクリプションの全体管理者のアカウント名とパスワード。
    
- Office 365 試用版サブスクリプションの User 5 アカウントの名前とパスワード。
    
### <a name="enable-and-configure-cloud-app-security"></a>Cloud App Security を有効にし、構成する

1. Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) に移動し、グローバル管理者アカウントで Office 365 試用版サブスクリプションにサインインします。
    
2. をクリックして、**セキュリティ&amp;準拠**を並べて表示します。
    
3. 左側のナビゲーション ウィンドウで、 **[アラート] > [高度な警告の管理]** をクリックします。
    
4. **[高度な警告の管理]** ページで、 **[Office 365 Cloud App Security を有効にする]** をクリックし、 **[Office 365 Cloud App Security に移動]** をクリックします。
    
5. 新しい **[ダッシュボード]** タブから **[制御] > [ポリシー]** をクリックします。
    
6. **[ポリシー]** ページで、 **[ポリシーの作成]** をクリックし、次に **[アクティビティ ポリシー]** をクリックします。
    
7. **[ポリシー名]** に「 **管理アクティビティ**」と入力します。
    
8. **[ポリシー重要度]** で、 **[高]** をクリックします。
    
9. **[カテゴリ]** で、 **[特権アカウント]** をクリックします。
    
10. **[ポリシーのフィルターの作成]** の **[以下のすべてに該当するアクティビティ]** で、 **[管理アクティビティ]** をクリックします。
    
11. **[アラート]** で、 **[アラートを電子メールとして送信する]** をクリックします。 **[送信先]** に、全体管理者アカウントの電子メール アドレスを入力します。
    
12. ページの下部にある **[作成]** をクリックします。
    
## <a name="phase-4-show-cloud-app-security-in-action"></a>フェーズ 4: Cloud App Security の動作を確認する

この手順では、User 4 が User 5 をパスワード管理およびユーザー管理の管理者に設定したときに、Cloud App Security がどのようにアラートを作成し、電子メール通知を全体管理者に送信するかを確認します。
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a>ユーザー アカウント ロールを変更する場合の電子メール通知のデモンストレーション

1. 右上部分にあるユーザー アイコンをクリックし、次に **[サインアウト]** をクリックします。
    
2. [https://portal.office.com](https://portal.office.com)を開きます。
    
3. Office 365 のサインイン ページで、 **[別のアカウントを使用する]** をクリックします。
    
4. User 4 のアカウント名とパスワードを入力し、 **[サインイン]** をクリックします。
    
5. 必要であれば、User 4 アカウント パスワードを変更し、次に **[パスワードを変更してサインイン]** をクリックします。
    
6. Office 365 ポータル ページで、 **[管理]** をクリックします。
    
7. 管理者連絡先情報を更新するダイアログが表示された場合、必要であれば **[キャンセル]** をクリックします。
    
8. ポータルのメイン ページで、 **[管理]** をクリックします。
    
9. 左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。
    
10. **[User 5]** アカウントをクリックします。
    
11. **[User 5]** ページで、 **[ロール]** 行の **[編集]** をクリックします。
    
12. **[ユーザー ロールの編集]** ページで、 **[カスタマイズされた管理者]** をクリックし、 **[パスワード管理者]** と **[ユーザー管理の管理者]** をクリックします。 **[代替電子メール アドレス]** に **user5@contoso.com** と入力し、次に **[保存]** をクリックします。 **[閉じる]** を 2 回クリックします。
    
13. 右上部分にあるユーザー アイコンをクリックし、次に **[サインアウト]** をクリックします。 
    
14. [https://portal.office.com](https://portal.office.com)を開きます。
    
15. **[Office 365 サインイン]** ページで、全体管理者のアカウント名をクリックします。
    
16. パスワードを入力し、 **[サインイン]** をクリックします。
    
17. ポータルのメイン ページで、 **[管理]** をクリックします。
    
18. をクリックして、**セキュリティ&amp;準拠**を並べて表示します。
    
19. 左側のナビゲーション ウィンドウで、 **[アラート] > [高度な警告の管理]** をクリックします。
    
20. **[高度な警告の管理]** ページで、 **[Office 365 Cloud App Security に移動]** をクリックします。
    
21. 新しい **[ダッシュボード]** タブに、 **管理アクティビティ**用の 2 つの新しいアラートがあります。
    
22. **[Microsoft Office Home]** タブで、 **[メール]** をクリックします。最大 30 分間待ちます。 
    
    受信トレイに 2 件の「 **Microsoft Azure AD Notification Service**」という題名の新しい電子メール メッセージが届いているはずです。1 件のメッセージは、User 5 のアカウントが **パスワード管理者**ロール に追加されたことを示しています。別のメッセージは、User 5 のアカウントが **ユーザー管理者**ロール (Office 365 管理センターでのユーザー管理の管理者ロールに等しい) に追加されたことを示しています。
    
この環境を使用して新しいポリシーを作成し、さらに Office 365 Cloud App Security を試すことができます。その他の構成に関する記事へのリンクは、「[高度なセキュリティ管理の使用を開始する](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)」を参照してください。
  
## <a name="see-also"></a>See Also

[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Office 365 開発/テスト環境](office-365-dev-test-environment.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)

[Office 365 の Advanced Security Management の概要](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


