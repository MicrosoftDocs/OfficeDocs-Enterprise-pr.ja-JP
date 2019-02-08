---
title: Office 365 開発/テスト環境の Cloud App Security
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/05/2018
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
ms.assetid: 22248f2f-b370-435e-b6ac-0ae0cae36b96
description: '概要: Office 365 開発/テスト環境で Office 365 Cloud App Security を構成し、デモンストレーションします。'
ms.openlocfilehash: 2c29e650233348e44bf72adcb8b18580e1de8802
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897060"
---
# <a name="cloud-app-security-for-your-office-365-devtest-environment"></a><span data-ttu-id="c5b50-103">Office 365 開発/テスト環境の Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="c5b50-103">Cloud App Security for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="c5b50-104">**概要:** Office 365 開発/テスト環境で Office 365 Cloud App Security を構成し、デモンストレーションします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-104">**Summary:** Configure and demonstrate Office 365 Cloud App Security in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="c5b50-p101">Office 365 高度なセキュリティ管理、ポリシーを監視し、調査し、可能な改善策を実行できるように、Office 365 サブスクリプションの場合、不審なアクティビティの通知を作成することと呼ばれていた、office 365 のクラウド アプリケーション セキュリティアクションです。詳細については、[概要のクラウド アプリケーションのセキュリティでは、Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5b50-p101">Office 365 Cloud App Security, previously known as Office 365 Advanced Security Management, lets you create policies that monitor for and inform you of suspicious activities in your Office 365 subscription, so that you can investigate and take possible remediation action. For more information, see [Overview of Cloud App Security in Office 365](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475).</span></span>
  
<span data-ttu-id="c5b50-107">この記事の手順を使用して、Office 365 の試用版サブスクリプションで Cloud App Security を有効にし、テストできます。</span><span class="sxs-lookup"><span data-stu-id="c5b50-107">With the instructions in this article, you enable and test Cloud App Security in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="c5b50-108">
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="c5b50-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="c5b50-109">フェーズ 1:ライトウェイトの、またはシミュレーションのエンタープライズ Office 365 開発/テスト環境を構築する</span><span class="sxs-lookup"><span data-stu-id="c5b50-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="c5b50-110">最小要件で、負荷の小さい方法で Cloud App Security をテストする場合は、[Office 365 開発/テスト環境](office-365-dev-test-environment.md) のフェーズ 2 とフェーズ 3 の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="c5b50-110">If you just want to test Cloud App Security in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="c5b50-111">シミュレーションのエンタープライズで Cloud App Security をテストする場合は、[Office 365 開発/テスト環境の DirSync](dirsync-for-your-office-365-dev-test-environment.md) の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="c5b50-111">If you want to test Cloud App Security in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c5b50-p102">Cloud App Security のテストには、シミュレーションのエンタープライズ開発/テスト環境は必要ありません。シミュレーションのエンタープライズ開発/テスト環境には、インターネットに接続されたシミュレーションのイントラネット、Windows Server AD フォレスト用のディレクトリ同期が含まれています。この機能は、一般的な組織と類似した環境で Cloud App Security をテストしてお試しいただけるよう、オプションとしてここで提供されています。</span><span class="sxs-lookup"><span data-stu-id="c5b50-p102">Testing Cloud App Security does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test Cloud App Security and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-before-enabling-cloud-app-security-and-creating-a-policy"></a><span data-ttu-id="c5b50-114">フェーズ 2: Cloud App Security の有効化およびポリシーの作成の前に</span><span class="sxs-lookup"><span data-stu-id="c5b50-114">Phase 2: Before enabling Cloud App Security and creating a policy</span></span>

<span data-ttu-id="c5b50-115">この手順では、Cloud App Security を有効にする前の状態で、ユーザーのロールを変更しても全体管理者に電子メール通知が送信されないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c5b50-115">In this procedure, you demonstrate that before enabling Cloud App Security, changing a user's role provides no email notification to the global administrator.</span></span>
  
### <a name="test-the-default-notification-behavior-of-office-365"></a><span data-ttu-id="c5b50-116">Office 365 の既定の通知動作をテストする</span><span class="sxs-lookup"><span data-stu-id="c5b50-116">Test the default notification behavior of Office 365</span></span>

1. <span data-ttu-id="c5b50-117">Office 365 ポータルに移動 ([https://portal.office.com](https://portal.office.com)) し、グローバル管理者アカウントを使用して、Office 365 の試用版サブスクリプションにサインインします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-117">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="c5b50-118">ライトウェイトの Office 365 開発/テスト環境を使用している場合は、ローカル コンピューターからサインインします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-118">If you are using the lightweight Office 365 dev/test environment, sign in from your local computer.</span></span>
    
  - <span data-ttu-id="c5b50-119">シミュレーションのエンタープライズ Office 365 開発/テスト環境を使用している場合は、[Azure ポータル](https://portal.azure.com) を使用して CLIENT1 仮想マシンに接続し、CLIENT1 からサインインします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-119">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal](https://portal.azure.com) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="c5b50-120">ポータルのメイン ページで、 **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-120">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="c5b50-121">左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-121">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="c5b50-122">**[User 4]** アカウントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-122">Click the **User 4** account.</span></span>
    
5. <span data-ttu-id="c5b50-123">**[User 4]** ページで、 **[ロール]** 行の **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-123">On the **User 4** page, click **Edit** for the **Roles** row.</span></span>
    
6. <span data-ttu-id="c5b50-p103">**[ユーザー ロールの編集]** ページで、 **[全体管理者]** をクリックし、 **[代替電子メール アドレス]** に **user4@contoso.com** と入力し、 **[保存]** をクリックします。 **[閉じる]** を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-p103">On the **Edit user roles** page, click **Global administrator**, type **user4@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
7. <span data-ttu-id="c5b50-126">左上部分にあるアプリ起動ツールのアイコンを選択し、 **[メール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-126">Select the app launcher icon in the upper-left and choose **Mail**.</span></span>
    
8. <span data-ttu-id="c5b50-p104">30 分間待ちます。User 4 のロールが全体管理者に変更されたことを通知する電子メール メッセージが、受信トレイにないことにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="c5b50-p104">Wait 30 minutes. Notice that there is no email message in the inbox notifying you of the change in User 4's role as a global administrator.</span></span>
    
## <a name="phase-3-enable-cloud-app-security-and-create-a-policy"></a><span data-ttu-id="c5b50-129">フェーズ 3: Cloud App Security を有効にし、ポリシーを作成する</span><span class="sxs-lookup"><span data-stu-id="c5b50-129">Phase 3: Enable Cloud App Security and create a policy</span></span>

<span data-ttu-id="c5b50-p105">この手順では、Cloud App Security を有効にして新しいポリシーを作成し、ユーザー アカウントのロールが変更された場合に、電子メール通知を全体管理者のアカウントに送信するようにします。この手順では、以下が必要です。</span><span class="sxs-lookup"><span data-stu-id="c5b50-p105">In this procedure, you enable Cloud App Security and create a new policy to send email notifications to your global administrator account for changes in user account roles. This procedure requires:</span></span>
  
- <span data-ttu-id="c5b50-132">Office 365 試用版サブスクリプションの全体管理者のアカウント名とパスワード。</span><span class="sxs-lookup"><span data-stu-id="c5b50-132">The global administrator account name and password of your Office 365 trial subscription.</span></span>
    
- <span data-ttu-id="c5b50-133">Office 365 試用版サブスクリプションの User 5 アカウントの名前とパスワード。</span><span class="sxs-lookup"><span data-stu-id="c5b50-133">The name and password of the User 5 account of your Office 365 trial subscription.</span></span>
    
### <a name="enable-and-configure-cloud-app-security"></a><span data-ttu-id="c5b50-134">Cloud App Security を有効にし、構成する</span><span class="sxs-lookup"><span data-stu-id="c5b50-134">Enable and configure Cloud App Security</span></span>

1. <span data-ttu-id="c5b50-135">Office 365 ポータルに移動 ([https://portal.office.com](https://portal.office.com)) し、グローバル管理者アカウントを使用して、Office 365 の試用版サブスクリプションにサインインします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-135">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="c5b50-p106">**管理者**のタイルをクリックします。[場所] タブの [ **Office 管理者センター** **管理者 _gt セキュリティ & 準拠の中央に配置**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-p106">Click the **Admin** tile. On the **Office Admin center** tab, click **Admin centers > Security & Compliance**.</span></span>
    
3. <span data-ttu-id="c5b50-138">左側のナビゲーション ウィンドウで、 **[アラート] > [高度な警告の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-138">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
4. <span data-ttu-id="c5b50-139">**[高度な警告の管理]** ページで、 **[Office 365 Cloud App Security を有効にする]** をクリックし、 **[Office 365 Cloud App Security に移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-139">On the **Manage advanced alerts** page, click **Turn on Office 365 Cloud App Security**, and then click **Go to Office 365 Cloud App Security**.</span></span>
    
5. <span data-ttu-id="c5b50-140">新しい **[ダッシュボード]** タブから **[制御] > [ポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-140">On the new **Dashboard** tab, click **Control > Policies**.</span></span>
    
6. <span data-ttu-id="c5b50-141">**[ポリシー]** ページで、 **[ポリシーの作成]** をクリックし、次に **[アクティビティ ポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-141">On the **Policy** page, click **Create policy**, and then click **Activity policy**.</span></span>
    
7. <span data-ttu-id="c5b50-142">**[ポリシー名]** に「 **管理アクティビティ**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="c5b50-142">In **Policy name**, type **Administrative activity**.</span></span>
    
8. <span data-ttu-id="c5b50-143">**[ポリシー重要度]** で、 **[高]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-143">In **Policy severity**, click **High**.</span></span>
    
9. <span data-ttu-id="c5b50-144">**[カテゴリ]** で、 **[特権アカウント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-144">In **Category**, click **Privileged accounts**.</span></span>
    
10. <span data-ttu-id="c5b50-145">**[ポリシーのフィルターの作成]** の **[以下のすべてに該当するアクティビティ]** で、 **[管理アクティビティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-145">In **Create filters for the policy**, in **Activities matching all of the following**, click **Administrative activity**.</span></span>
    
11. <span data-ttu-id="c5b50-p107">**[アラート]** で、 **[アラートを電子メールとして送信する]** をクリックします。 **[送信先]** に、全体管理者アカウントの電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="c5b50-p107">In **Alerts**, click **Send alert as email**. In **To**, type the email address of your global administrator account.</span></span>
    
12. <span data-ttu-id="c5b50-148">ページの下部にある **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-148">At the bottom of the page, click **Create**.</span></span>
    
## <a name="phase-4-show-cloud-app-security-in-action"></a><span data-ttu-id="c5b50-149">フェーズ 4: Cloud App Security の動作を確認する</span><span class="sxs-lookup"><span data-stu-id="c5b50-149">Phase 4: Show Cloud App Security in action</span></span>

<span data-ttu-id="c5b50-150">この手順では、User 4 が User 5 をパスワード管理およびユーザー管理の管理者に設定したときに、Cloud App Security がどのようにアラートを作成し、電子メール通知を全体管理者に送信するかを確認します。</span><span class="sxs-lookup"><span data-stu-id="c5b50-150">In this procedure, you demonstrate how Cloud App Security creates alerts and sends email notifications to the global administrator account when User 4 makes User 5 a password and user management administrator.</span></span>
  
### <a name="demonstrate-email-notification-for-a-change-in-user-account-roles"></a><span data-ttu-id="c5b50-151">ユーザー アカウント ロールを変更する場合の電子メール通知のデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="c5b50-151">Demonstrate email notification for a change in user account roles</span></span>

1. <span data-ttu-id="c5b50-152">右上部分にあるユーザー アイコンをクリックし、次に **[サインアウト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-152">In the upper-right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="c5b50-153">[https://portal.office.com](https://portal.office.com) に移動します。</span><span class="sxs-lookup"><span data-stu-id="c5b50-153">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
3. <span data-ttu-id="c5b50-154">Office 365 のサインイン ページで、 **[別のアカウントを使用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-154">On the Office 365 sign in page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="c5b50-155">User 4 のアカウント名とパスワードを入力し、 **[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-155">Type the User 4 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="c5b50-156">必要であれば、User 4 アカウント パスワードを変更し、次に **[パスワードを変更してサインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-156">If needed, change the User 4 account password, and then click **Update password and sign in**.</span></span>
    
6. <span data-ttu-id="c5b50-157">Office 365 ポータル ページで、 **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-157">On the Office 365 portal page, click **Admin**.</span></span>
    
7. <span data-ttu-id="c5b50-158">管理者連絡先情報を更新するダイアログが表示された場合、必要であれば **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-158">If needed, click **cancel** when prompted to update your admin contact info.</span></span>
    
8. <span data-ttu-id="c5b50-159">ポータルのメイン ページで、**[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-159">From the main portal page, click **Admin**.</span></span>
    
9. <span data-ttu-id="c5b50-160">左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-160">In the left navigation, click **Users > Active users**.</span></span>
    
10. <span data-ttu-id="c5b50-161">**[User 5]** アカウントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-161">Click the **User 5** account.</span></span>
    
11. <span data-ttu-id="c5b50-162">**[User 5]** ページで、 **[ロール]** 行の **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-162">On the **User 5** page, click **Edit** for the **Roles** row.</span></span>
    
12. <span data-ttu-id="c5b50-p108">**[ユーザー ロールの編集]** ページで、 **[カスタマイズされた管理者]** をクリックし、 **[パスワード管理者]** と **[ユーザー管理の管理者]** をクリックします。 **[代替電子メール アドレス]** に **user5@contoso.com** と入力し、次に **[保存]** をクリックします。 **[閉じる]** を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-p108">On the **Edit user roles** page, click **Customized administrator**, click **Password administrator** and **User management administrator**, type **user5@contoso.com** in the **Alternative email address**, and then click **Save**. Click **Close** twice.</span></span>
    
13. <span data-ttu-id="c5b50-165">右上部分にあるユーザー アイコンをクリックし、次に **[サインアウト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-165">Click the user icon in the upper-right, and then click **Sign out**.</span></span> 
    
14. <span data-ttu-id="c5b50-166">[https://portal.office.com](https://portal.office.com) に移動します。</span><span class="sxs-lookup"><span data-stu-id="c5b50-166">Go to [https://portal.office.com](https://portal.office.com).</span></span>
    
15. <span data-ttu-id="c5b50-167">**[Office 365 サインイン]** ページで、全体管理者のアカウント名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-167">On the **Office 365 sign in** page, click your global administrator account name.</span></span>
    
16. <span data-ttu-id="c5b50-168">パスワードを入力し、 **[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-168">Type the password, and then click **Sign in**.</span></span>
    
17. <span data-ttu-id="c5b50-169">ポータルのメイン ページで、 **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-169">From the main portal page, click **Admin**.</span></span>
    
18. <span data-ttu-id="c5b50-170">**[セキュリティとコンプライアンス]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-170">Click the **Security &amp; Compliance** tile.</span></span>
    
19. <span data-ttu-id="c5b50-171">左側のナビゲーション ウィンドウで、 **[アラート] > [高度な警告の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-171">In the left navigation pane, click **Alerts > Manage advanced alerts**.</span></span>
    
20. <span data-ttu-id="c5b50-172">**[高度な警告の管理]** ページで、 **[Office 365 Cloud App Security に移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c5b50-172">On the **Manage advanced alerts** page, click **Go to Office 365 Cloud App Security**.</span></span>
    
21. <span data-ttu-id="c5b50-173">新しい **[ダッシュボード]** タブに、 **管理アクティビティ**用の 2 つの新しいアラートがあります。</span><span class="sxs-lookup"><span data-stu-id="c5b50-173">On the new **Dashboard** tab, notice the two new alerts for **Administrative activity**.</span></span>
    
22. <span data-ttu-id="c5b50-p109">**[Microsoft Office Home]** タブで、 **[メール]** をクリックします。最大 30 分間待ちます。</span><span class="sxs-lookup"><span data-stu-id="c5b50-p109">From the **Microsoft Office Home** tab, click **Mail**. Wait up to 30 minutes.</span></span> 
    
    <span data-ttu-id="c5b50-p110">受信トレイに 2 件の「 **Microsoft Azure AD Notification Service**」という題名の新しい電子メール メッセージが届いているはずです。1 件のメッセージは、User 5 のアカウントが **パスワード管理者**ロール に追加されたことを示しています。別のメッセージは、User 5 のアカウントが **ユーザー管理者**ロール (Office 365 管理センターでのユーザー管理の管理者ロールに等しい) に追加されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="c5b50-p110">You should see two new email messages in the inbox with the title **Microsoft Azure AD Notification Service**. One message indicates that the User 5 account was added to the **Password Administrator** role and another message indicates that the User 5 account was added to the **User Administrator** role (equal to the User management administrator role in the Office 365 Admin center).</span></span>
    
<span data-ttu-id="c5b50-p111">この環境を使用して新しいポリシーを作成し、さらに Office 365 Cloud App Security を試すことができます。その他の構成に関する記事へのリンクは、「[高度なセキュリティ管理の使用を開始する](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5b50-p111">You can now use this environment to create new policies and further experiment with Office 365 Cloud App Security. See [Get ready for Office 365 Cloud App Security](https://support.office.com/article/Get-ready-for-Office-365-Cloud-App-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) for links to additional configuration articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c5b50-180">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5b50-180">See Also</span></span>

[<span data-ttu-id="c5b50-181">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="c5b50-181">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="c5b50-182">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="c5b50-182">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="c5b50-183">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="c5b50-183">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="c5b50-184">Office 365 の Advanced Security Management の概要</span><span class="sxs-lookup"><span data-stu-id="c5b50-184">Overview of Cloud App Security in Office 365</span></span>](https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)


