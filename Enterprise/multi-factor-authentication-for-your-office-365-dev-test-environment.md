---
title: Office 365 開発/テスト環境用の多要素認証
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/20/2019
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
ms.openlocfilehash: 453dbc6bda3cfbc6806159d53c9a805c4c6cac97
ms.sourcegitcommit: 8e2760cbcaf564923595147ccf6da468edaed364
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/25/2019
ms.locfileid: "30242079"
---
# <a name="multi-factor-authentication-for-your-office-365-devtest-environment"></a><span data-ttu-id="46dfb-103">Office 365 開発/テスト環境用の多要素認証</span><span class="sxs-lookup"><span data-stu-id="46dfb-103">Multi-factor authentication for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="46dfb-104">**概要:** Office 365 の開発/テスト環境で、スマート フォンに送信されるテキスト メッセージを使用して多要素認証を構成します。</span><span class="sxs-lookup"><span data-stu-id="46dfb-104">**Summary:** Configure multi-factor authentication using text messages sent to a smart phone in an Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="46dfb-p101">Office 365 サブスクリプションにサインインするための追加のセキュリティレベルについては、Azure 多要素認証を有効にすることができます。これには、アカウントを認証するためにユーザー名とパスワードだけを必要とします。Office 365 に多要素認証を使用する場合、ユーザーは電話での通話の承認、テキストメッセージで送信された検証コードの入力、またはスマートフォンのパスワードを正しく入力した後にアプリのパスワードを指定する必要があります。この2番目の認証要因が満たされている場合にのみ、サインインできます。</span><span class="sxs-lookup"><span data-stu-id="46dfb-p101">For an additional level of security for signing in to your Office 365 subscription, you can enable Azure multi-factor authentication, which requires more than just a username and password to authenticate an account. With multi-factor authentication for Office 365, users are required to acknowledge a phone call, type a verification code sent in a text message, or specify an app password on their smart phones after correctly entering their passwords. They can sign in only after this second authentication factor has been satisfied.</span></span> 
  
<span data-ttu-id="46dfb-108">この記事では、特定の Office 365 アカウントに対してテキスト メッセージ ベースの認証を有効にしてテストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="46dfb-108">This article describes how to enable and test text message-based authentication for a specific Office 365 account.</span></span>
  
<span data-ttu-id="46dfb-109">開発/テスト環境での Office 365 の多要素認証のセットアップには、次の 2 つのフェーズがあります。</span><span class="sxs-lookup"><span data-stu-id="46dfb-109">There are two phases to setting up multi-factor authentication for Office 365 in a dev/test environment:</span></span>
  
1. <span data-ttu-id="46dfb-110">Office 365 開発/テスト環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="46dfb-110">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="46dfb-111">User 2 アカウントに対して、多要素認証を有効にしてテストします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-111">Enable and test multi-factor authentication for the User 2 account.</span></span>
    
> [!TIP]
> <span data-ttu-id="46dfb-112">[ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="46dfb-112">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="46dfb-113">フェーズ 1: ライトウェイトの、またはシミュレーションのエンタープライズ Office 365 開発/テスト環境を構築する</span><span class="sxs-lookup"><span data-stu-id="46dfb-113">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="46dfb-114">最小要件での軽量な方法で多要素認証をテストするだけの場合は、 [Office 365 開発/テスト環境](office-365-dev-test-environment.md)のフェーズ2とフェーズ3の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="46dfb-114">If you just want to test multi-factor authentication in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="46dfb-115">シミュレートされたエンタープライズで多要素認証をテストする場合は、「 [Office のディレクトリ同期の開発/テスト環境](dirsync-for-your-office-365-dev-test-environment.md)」の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="46dfb-115">If you want to test multi-factor authentication in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="46dfb-p102">多要素認証をテストするのに、インターネットに接続されたシミュレーション イントラネットと Windows Server AD フォレスト用のディレクトリ同期を含めた、シミュレーション エンタープライズの開発/テスト環境は必要ではありません。この指示は、一般的な組織と類似した環境で多要素認証をテストしてお試しいただけるようオプションとしてここで提供しています。</span><span class="sxs-lookup"><span data-stu-id="46dfb-p102">Testing multi-factor authentication does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test multi-factor authentication and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a><span data-ttu-id="46dfb-118">フェーズ 2:User 2 アカウントに対して、多要素認証を有効にしてテストする</span><span class="sxs-lookup"><span data-stu-id="46dfb-118">Phase 2: Enable and test multi-factor authentication for the User 2 account</span></span>

<span data-ttu-id="46dfb-119">次の手順を実行して、User 2 アカウントに対して多要素認証を有効にしてテストします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-119">Enable multi-factor authentication for the User 2 account with these steps:</span></span>
  
1. <span data-ttu-id="46dfb-120">ブラウザーの別のインスタンスを開き、office 365 ポータル ([https://portal.office.com](https://portal.office.com)) に移動し、全体管理者アカウントを使用して office 365 試用版サブスクリプションにサインインします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-120">Open a separate instance of your browser, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)), and then sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="46dfb-121">ポータルのメイン ページで、**[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-121">From the main portal page, click **Admin**.</span></span>
    
3. <span data-ttu-id="46dfb-122">左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-122">In the left navigation, click **Users > Active users**.</span></span>
    
4. <span data-ttu-id="46dfb-123">[アクティブなユーザー] ウィンドウで、[**その他の > 多要素認証のセットアップ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-123">In the Active users pane, click **More > Multi-factor authentication setup**.</span></span>
    
5. <span data-ttu-id="46dfb-124">リストで、 **User 2**アカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="46dfb-124">In the list, select the **User 2** account.</span></span>
    
6. <span data-ttu-id="46dfb-125">**User 2** セクションで、**[クイック操作]** の **[有効にする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-125">In the **User 2** section, under **Quick steps**, click **Enable**.</span></span>
    
7. <span data-ttu-id="46dfb-126">**[多要素認証を有効にする方法の概要]** ダイアログ ボックスで、**[Multi-Factor Auth を有効にする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-126">In the **About enabling multi-factor auth** dialog box, click **Enable multi-factor auth**.</span></span>
    
8. <span data-ttu-id="46dfb-127">[**更新が成功しまし**た] ダイアログボックスで、[**閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-127">In the **Updates successful** dialog box, click **Close**.</span></span>
    
9. <span data-ttu-id="46dfb-128">**[Microsoft Office Home]** タブで、右上部分にあるユーザー アカウントのアイコンをクリックし、**[サインアウト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-128">On the **Microsoft Office Home** tab, click the user account icon in the upper right, and then click **Sign out**.</span></span>
    
10. <span data-ttu-id="46dfb-129">ブラウザー インスタンスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="46dfb-129">Close your browser instance.</span></span>
    
<span data-ttu-id="46dfb-130">次の手順を実行して、User 2 アカウントで確認のためにテキスト メッセージを使用するように構成を完了し、それをテストします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-130">Complete the configuration for the User 2 account to use a text message for validation and test it with these steps:</span></span>
  
1. <span data-ttu-id="46dfb-131">ブラウザーの新しいインスタンスを開きます。</span><span class="sxs-lookup"><span data-stu-id="46dfb-131">Open a new instance of your browser.</span></span>
    
2. <span data-ttu-id="46dfb-132">Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) に移動し、User 2 アカウント (user2 @\<organization name>) とパスワードを使用してサインインします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-132">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in with the User 2 account (user2@\<organization name>.onmicrosoft.com) and password.</span></span>
    
3. <span data-ttu-id="46dfb-p103">サインイン後、追加のセキュリティ検証のためにアカウントを設定するように求められます。**[今すぐセットアップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-p103">After signing in, you are prompted to set up the account for additional security validation. Click **Set it up now**.</span></span>
    
4. <span data-ttu-id="46dfb-135">**[追加のセキュリティ確認]** ページで、次の手順を実行します。 </span><span class="sxs-lookup"><span data-stu-id="46dfb-135">On the **Additional security verification** page:</span></span>
    
  - <span data-ttu-id="46dfb-136">国または地域を選択します。</span><span class="sxs-lookup"><span data-stu-id="46dfb-136">Select your country or region.</span></span>
    
  - <span data-ttu-id="46dfb-137">テキスト メッセージを受信するスマート フォンの電話番号を入力します。</span><span class="sxs-lookup"><span data-stu-id="46dfb-137">Type phone number of the smart phone that will receive text messages.</span></span>
    
  - <span data-ttu-id="46dfb-138">[**メソッド**] の [**テキストメッセージでコードを送信する**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-138">in **Method**, click **Send me a code by text message**.</span></span>
    
5. <span data-ttu-id="46dfb-139">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-139">Click **Next**.</span></span>
    
6. <span data-ttu-id="46dfb-140">スマート フォンで受信したテキスト メッセージに記載されている確認コードを入力して、**[確認]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-140">Enter the verification code from the text message received on your smart phone, and then click **Verify**.</span></span>
    
7. <span data-ttu-id="46dfb-141">**[手順 3: 既存のアプリケーションを使用し続ける]** ページで、User 2 アカウント用に表示されているアプリ パスワードを安全な場所に記録してから、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46dfb-141">On the **Step 3: Keep your existing applications** page, record the displayed app password for the User 2 account in a secure location, and then click **Done**.</span></span>
    
8. <span data-ttu-id="46dfb-p104">User 2 アカウントでサインインするのが今回で初めての場合、パスワードの変更を求められます。元のパスワードと、新しいパスワードを 2 回入力して、**[パスワードを更新してサインイン]** をクリックします。新しいパスワードを安全な場所に記録します。</span><span class="sxs-lookup"><span data-stu-id="46dfb-p104">If this is the first time you signed in with the User 2 account, you are prompted to change the password. Type the original password and a new password twice, and then click **Update password and sign in**. Record the new password in a secure location.</span></span>
    
    <span data-ttu-id="46dfb-145">ブラウザーの [ **Microsoft office Home** ] タブに、ユーザー2用の Office 365 ポータルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="46dfb-145">You should see the Office 365 portal for User 2 on the **Microsoft Office Home** tab of your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="46dfb-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="46dfb-146">See Also</span></span>

[<span data-ttu-id="46dfb-147">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="46dfb-147">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="46dfb-148">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="46dfb-148">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="46dfb-149">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="46dfb-149">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="46dfb-150">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="46dfb-150">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="46dfb-151">Office 365 展開用の多要素認証の計画</span><span class="sxs-lookup"><span data-stu-id="46dfb-151">Plan for multi-factor authentication for Office 365 Deployments</span></span>](https://support.office.com/article/Plan-for-multi-factor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

