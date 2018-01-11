---
title: "Office 365 開発/テスト環境用の多要素認証"
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
- TLG
- Ent_TLGs
ms.assetid: e2b354b9-7f18-4da0-9107-6245eae0f33f
description: "概要: Office 365 の開発/テスト環境でスマート フォンに送信されるテキスト メッセージを使用して複数要素の認証を構成します。"
ms.openlocfilehash: 66b0fadd097e6df940754c28cd7b95549eb3a761
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="9a155-103">Office 365 開発/テスト環境用の多要素認証</span><span class="sxs-lookup"><span data-stu-id="9a155-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="9a155-104">**の概要:**Office 365 の開発/テスト環境でスマート フォンに送信されるテキスト メッセージを使用して複数要素の認証を構成します。</span><span class="sxs-lookup"><span data-stu-id="9a155-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="9a155-p101">Office 365 サブスクリプションにサインインする際に追加のレベルのセキュリティが必要な場合、Azure 多要素認証を有効にできます。この認証には、アカウントを確認するために、ユーザー名とパスワード以上のものが必要になります。Office 365 用の多要素認証では、ユーザーは、パスワードを正しく入力した後に、電話に応答するか、テキスト メッセージで送信される確認コードを入力するか、スマート フォンでアプリ パスワードを入力する必要があります。この第 2 の認証要素が満たされた後でのみ、ユーザーはサインインできます。 </span><span class="sxs-lookup"><span data-stu-id="9a155-p101">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to verify an account. With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords. They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="9a155-108">この記事では、特定の Office 365 アカウントに対してテキスト メッセージ ベースの認証を有効にしてテストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a155-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="9a155-109">開発/テスト環境での Office 365 の多要素認証のセットアップには、次の 2 つのフェーズがあります。</span><span class="sxs-lookup"><span data-stu-id="9a155-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="9a155-110">Office 365 開発/テスト環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="9a155-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="9a155-111">User 2 アカウントに対して、多要素認証を有効にしてテストします。</span><span class="sxs-lookup"><span data-stu-id="9a155-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="9a155-112">
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="9a155-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="9a155-113">フェーズ 1:ライトウェイトの、またはシミュレーションのエンタープライズ Office 365 開発/テスト環境を構築する</span><span class="sxs-lookup"><span data-stu-id="9a155-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="9a155-114">最小要件で軽量な方法で複数要素の認証をテストする場合は、フェーズ 2 と 3[の開発/テスト環境を Office 365](office-365-dev-test-environment.md)の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="9a155-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="9a155-115">シミュレートされた企業内の複数要素の認証をテストする場合は、 [Office 365 の開発/テスト環境のディレクトリ同期](dirsync-for-your-office-365-dev-test-environment.md)に指示します。</span><span class="sxs-lookup"><span data-stu-id="9a155-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="9a155-p102">多要素認証をテストするのに、インターネットに接続されたシミュレーション イントラネットと Windows Server AD フォレスト用のディレクトリ同期を含めた、シミュレーション エンタープライズの開発/テスト環境は必要ではありません。この指示は、一般的な組織と類似した環境で多要素認証をテストしてお試しいただけるようオプションとしてここで提供しています。</span><span class="sxs-lookup"><span data-stu-id="9a155-p102">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="9a155-118">フェーズ 2:User 2 アカウントに対して、多要素認証を有効にしてテストする</span><span class="sxs-lookup"><span data-stu-id="9a155-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="9a155-119">次の手順を実行して、User 2 アカウントに対して多要素認証を有効にしてテストします。</span><span class="sxs-lookup"><span data-stu-id="9a155-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="9a155-120">お使いのブラウザーの別のインスタンスを開く、([https://portal.office.com](https://portal.office.com)) は、Office 365 ポータルに移動し、グローバル管理者アカウントを使用して、Office 365 の試用版サブスクリプションにサインインし、します。</span><span class="sxs-lookup"><span data-stu-id="9a155-120">Open a separate instance of your browser, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="9a155-121">ポータルのメイン ページで、 **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a155-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="9a155-122">左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a155-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="9a155-123">ユーザーのアクティブなウィンドウをクリックして**より > 多要素認証のセットアップの Azure**。</span><span class="sxs-lookup"><span data-stu-id="9a155-123">In the Active users pane, click **More > Setup Azure multi-factor auth**.</span></span>
    
5. <span data-ttu-id="9a155-124">の一覧では、 **2 のユーザー**アカウントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a155-124">In the list, click the **User 2** account.</span></span>
    
6. <span data-ttu-id="9a155-125">**ユーザー 2**で、[**クイック操作****を有効にする**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a155-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="9a155-126">**多要素認証を有効にする方法**の選択] ダイアログ ボックスでは、**多要素認証を有効にする**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a155-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="9a155-127">**更新は成功しました**] ダイアログ ボックスで [**閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a155-127">In the **Update successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="9a155-128">[場所] タブの [ **Microsoft Office のホーム**右上のユーザー アカウントのアイコンをクリックし、[**サインアウト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a155-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="9a155-129">ブラウザー インスタンスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9a155-129">Close your browser instance.</span></span>
    
<span data-ttu-id="9a155-130">次の手順を実行して、User 2 アカウントで確認のためにテキスト メッセージを使用するように構成を完了し、それをテストします。</span><span class="sxs-lookup"><span data-stu-id="9a155-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="9a155-131">ブラウザーの新しいインスタンスを開きます。</span><span class="sxs-lookup"><span data-stu-id="9a155-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="9a155-132">Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) と 2 のユーザー アカウントでサインインするには移動 (user2 @\<組織名 >. onmicrosoft.com) とパスワードです。</span><span class="sxs-lookup"><span data-stu-id="9a155-132">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="9a155-p103">サインイン後、追加のセキュリティ検証のためのアカウントを設定するように求められます。[**今すぐセットアップ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a155-p103">After signing in, you are prompted to set up the account for additional security validation. Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="9a155-135">**追加のセキュリティ検証**のページ。</span><span class="sxs-lookup"><span data-stu-id="9a155-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="9a155-136">国または地域を選択します。</span><span class="sxs-lookup"><span data-stu-id="9a155-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="9a155-137">テキスト メッセージを受信するスマート フォンの電話番号を入力します。</span><span class="sxs-lookup"><span data-stu-id="9a155-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="9a155-138">**テキスト メッセージによって、コードを送信してもらう**を選択します。</span><span class="sxs-lookup"><span data-stu-id="9a155-138">Select **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="9a155-139">**連絡先]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a155-139">Click **Contact me**.</span></span>
    
6. <span data-ttu-id="9a155-140">スマート電話で受信したテキスト メッセージの検証コードを入力し、し、[**確認**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a155-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="9a155-141">**ステップ 3: 既存のアプリケーションを保持**ページで、セキュリティで保護された場所に、アプリケーションが表示されているアカウントのパスワード、ユーザー 2 を記録し、[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a155-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="9a155-142">サインイン] ページで、[戻る 2 のユーザー アカウントのパスワードを入力し、[**サインイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a155-142">Back on the sign-in page, type the password for the User 2 account and click **Sign in**.</span></span>
    
9. <span data-ttu-id="9a155-143">スマート電話で受信したテキスト メッセージの検証コードを入力し、[**サインイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a155-143">Enter the verification code from the text message received on your smart phone, and then click **Sign in**.</span></span>
    
10. <span data-ttu-id="9a155-p104">これが初めてである場合、アカウントでサイン、ユーザー 2、表示されたら、パスワードを変更します。2 回、元のパスワードと新しいパスワードを入力し、**パスワードを更新し [サインイン**] をクリックします。安全な場所に新しいパスワードを記録します。</span><span class="sxs-lookup"><span data-stu-id="9a155-p104">If this is the first time you signed in with the User 2 account, you are prompted to change the password. Type the original password and a new password twice, and then click **Update password and sign in**. Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="9a155-147">User 2 用の Office 365 ポータルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9a155-147">You should see the Office 365 portal for User 2.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="9a155-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a155-148">See Also</span></span>

[<span data-ttu-id="9a155-149">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="9a155-149">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="9a155-150">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="9a155-150">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="9a155-151">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="9a155-151">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="9a155-152">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="9a155-152">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="9a155-153">Office 365 の展開の多要素認証の計画</span><span class="sxs-lookup"><span data-stu-id="9a155-153">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

