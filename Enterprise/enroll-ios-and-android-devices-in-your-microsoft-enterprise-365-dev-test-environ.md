---
title: "あっ、マイクロソフトのエンタープライズ 365 の開発/テスト環境でを登録します。"
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
- Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: "概要: ガイドを使用してこのテスト ラボ Microsoft 365、開発/テスト環境でデバイスを登録し、それらをリモートで管理します。"
ms.openlocfilehash: 8ad22ed62d8e7cac8aca225af42e389dc05cb2b5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="1127f-103">あっ、マイクロソフトのエンタープライズ 365 の開発/テスト環境でを登録します。</span><span class="sxs-lookup"><span data-stu-id="1127f-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="1127f-104">**の概要:**Microsoft 365、開発/テスト環境でデバイスを登録し、それらをリモートで管理するには、このテスト ラボ ガイド 』 を使用します。</span><span class="sxs-lookup"><span data-stu-id="1127f-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="1127f-p101">Microsoft エンタープライズ モビリティ スイート (EMS) では、組織のデータを保護しながら、お気に入りのアプリケーションとデバイスを使用して生産性の高い従業員を保つことができます。詳細については、[エンタープライズ ・ モビリティとセキュリティ (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1127f-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="1127f-p102">デバイス レベルでセキュリティを適用する必要がある場合は、Microsoft Intune にデバイスを登録する必要があります。デバイスの登録は、企業所有のデバイスだけでなく、個人用 (BYOD) および共有のデバイスを組織の法的ポリシーに応じて管理する際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1127f-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage corporate-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="1127f-109">によって、この資料に記載されている手順に従うことができます登録し、iOS および Android デバイスの基本的なモバイル デバイス管理の機能を Microsoft 365 開発/テスト環境でテストします。</span><span class="sxs-lookup"><span data-stu-id="1127f-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="1127f-110">フェーズ 1: Microsoft 365 の開発/テスト環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="1127f-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="1127f-111">[[Microsoft 365 エンタープライズ開発/テスト環境](the-microsoft-365-enterprise-dev-test-environment.md)での指示に従います。</span><span class="sxs-lookup"><span data-stu-id="1127f-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-customize-the-microsoft-intune-company-portal-app"></a><span data-ttu-id="1127f-112">フェーズ 2:Microsoft Intune ポータル サイト アプリをカスタマイズします</span><span class="sxs-lookup"><span data-stu-id="1127f-112">Phase 2: Customize the Microsoft Intune Company Portal app</span></span>

<span data-ttu-id="1127f-113">次に示す手順を使用して、Microsoft Intune ポータル サイト アプリを架空の会社に合わせてカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="1127f-113">Use these steps to customize the Microsoft Intune Company Portal app for your fictional company:</span></span>
  
1. <span data-ttu-id="1127f-114">新しいタブ、Microsoft Intune 管理コンソール ([https://manage.microsoft.com](https://manage.microsoft.com)) を開きます。</span><span class="sxs-lookup"><span data-stu-id="1127f-114">On a new tab, open the Microsoft Intune administration console ([https://manage.microsoft.com](https://manage.microsoft.com)).</span></span>
    
2. <span data-ttu-id="1127f-115">ナビゲーション ウィンドウの [**管理**] をクリックし、**管理**ウィンドウで [**モバイル デバイスの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-115">Click **Admin** in the navigation pane, and then click **Mobile Device Management** in the **Administration** pane.</span></span>
    
3. <span data-ttu-id="1127f-p103">**タスク**の一覧では、**モバイル デバイスの管理権限の設定**を選択します。**Microsoft Intune**に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1127f-p103">In the **Tasks** list, select **Set Mobile Device Management Authority**. Ensure that it is set to **Microsoft Intune**.</span></span>
    
4. <span data-ttu-id="1127f-118">**管理**ウィンドウでは、**企業ポータル**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-118">In the **Administration** pane, click **Company Portal**.</span></span>
    
5. <span data-ttu-id="1127f-119">**企業ポータル**ウィンドウで、次の設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="1127f-119">In the **Company Portal** pane, configure the following settings:</span></span>
    
  - <span data-ttu-id="1127f-120">会社名: \<、架空の会社名 ></span><span class="sxs-lookup"><span data-stu-id="1127f-120">Company name: \<your fictional company name></span></span>
    
  - <span data-ttu-id="1127f-121">IT 部門の連絡先の名前: **User5**</span><span class="sxs-lookup"><span data-stu-id="1127f-121">IT department contact name: **User5**</span></span>
    
  - <span data-ttu-id="1127f-122">IT 部門の電話番号: **555-1234**</span><span class="sxs-lookup"><span data-stu-id="1127f-122">IT department phone number: **555-1234**</span></span>
    
  - <span data-ttu-id="1127f-123">IT 部門の電子メール アドレス: **User5 @**\<の架空の組織名 > **. onmicrosoft.com** (User5 のアカウントの電子メール アドレス)</span><span class="sxs-lookup"><span data-stu-id="1127f-123">IT department e-mail address: **User5@**\<fictional organization name> **.onmicrosoft.com** (the email address of the User5 account)</span></span>
    
6. <span data-ttu-id="1127f-124">**カスタマイズ****テーマの色**の**緑**を選択します。</span><span class="sxs-lookup"><span data-stu-id="1127f-124">In **Customization**, select **Green** in **Theme color**.</span></span>
    
7. <span data-ttu-id="1127f-125">[ **保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-125">Click **Save**.</span></span>
    
<span data-ttu-id="1127f-126">次に、Microsoft Intune ポータル サイト アプリをインストールして、iOS デバイスまたは Android デバイスを登録します。その後、Microsoft Intune 管理コンソールから基本的な管理機能をテストします。</span><span class="sxs-lookup"><span data-stu-id="1127f-126">Next, you will install the Microsoft Intune Company Portal app and enroll an iOS or Android device, and then test basic management functionality from the Microsoft Intune administration console.</span></span>
  
## <a name="phase-3-for-ios-devices-only-enroll-and-manage-an-ios-device"></a><span data-ttu-id="1127f-127">フェーズ 3 (iOS デバイスのみ):iOS デバイスを登録して管理します</span><span class="sxs-lookup"><span data-stu-id="1127f-127">Phase 3 (for iOS devices only): Enroll and manage an iOS device</span></span>

<span data-ttu-id="1127f-128">Intune で管理するために iOS デバイス登録するには、次のものが必要になります。</span><span class="sxs-lookup"><span data-stu-id="1127f-128">To enroll an iOS device for management by Intune, you will need the following:</span></span>
  
- <span data-ttu-id="1127f-129">Apple iPad や iPhone などの iOS デバイス。</span><span class="sxs-lookup"><span data-stu-id="1127f-129">An iOS device such as an Apple iPad or iPhone.</span></span>
    
- <span data-ttu-id="1127f-130">IOS デバイスのパスコードのナレッジです。</span><span class="sxs-lookup"><span data-stu-id="1127f-130">Knowledge of the iOS device's passcode.</span></span>
    
- <span data-ttu-id="1127f-p104">Apple ID (アカウント名とパスワード)。まだ持っていない、 [Apple ID の web サイト](https://appleid.apple.com/#!&amp;page=signin)にアクセスし**、Apple ID の作成**をクリックします。Office 365 サブスクリプションのグローバル管理者アカウントに対応する Apple ID を作成します。新しい Apple ID のアカウント名とパスワードを安全な場所に記録します。</span><span class="sxs-lookup"><span data-stu-id="1127f-p104">An Apple ID (an account name and password). If you do not already have one, go to the [Apple ID website](https://appleid.apple.com/#!&amp;page=signin) and click **Create your Apple ID**. Create an Apple ID corresponding to the global administrator account of your Office 365 subscription. Record your new Apple ID account name and password in a secure location.</span></span>
    
<span data-ttu-id="1127f-p105">Apple プッシュ通知サービス (APNs) の証明書は、iOS と Mac を Intune で管理するために必要になります。この証明書を Intune に追加すると、ユーザーは、Microsoft Intune ポータル サイト アプリをインストールして、自分のデバイスを登録できるようになります。また、管理者は、企業所有の iOS デバイスの管理をセット アップできるようになります。</span><span class="sxs-lookup"><span data-stu-id="1127f-p105">An Apple Push Notification service (APNs) certificate is required for Intune to manage iOS and Mac devices. Once the certificate is added to Intune, users can install the Microsoft Intune Company Portal app to enroll their devices or the administrator can set up corporate-owned iOS device management.</span></span>
  
<span data-ttu-id="1127f-p106">Apple Push Certificates Portal から信頼関係の証明書を要求するには、証明書署名要求ファイルが必要です。証明書署名要求ファイルを取得するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1127f-p106">You need a certificate signing request file to request a trust relationship certificate from the Apple Push Certificates Portal. To get a certificate signing request file:</span></span>
  
1. <span data-ttu-id="1127f-139">Microsoft Intune 管理コンソールで、ナビゲーション ウィンドウで [**管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-139">In the Microsoft Intune administration console, click **Admin** in the navigation pane.</span></span>
    
    <span data-ttu-id="1127f-140">**管理**ウィンドウで開くには**モバイル デバイス管理 > iOS および Mac OS X**、**タスク**での**Apn の証明書のアップロード**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-140">In the **Administration** pane, open **Mobile Device Management > iOS and Mac OS X**, and then click **Upload an APNs Certificate** in **Tasks**.</span></span> 
    
2. <span data-ttu-id="1127f-p107">**Apn の証明書をアップロード**] ウィンドウで、 **Apn の証明書の要求をダウンロード**をクリックします。証明書署名要求 (.csr) のファイル名**の開発/テスト**をローカルに保存します。</span><span class="sxs-lookup"><span data-stu-id="1127f-p107">In the **Upload an APNs Certificate** pane, click **Download the APNs certificate request**. Save the certificate signing request (.csr) file locally with the name **dev-test**.</span></span>
    
<span data-ttu-id="1127f-143">Apple プッシュ通知サービス証明書を取得するには、</span><span class="sxs-lookup"><span data-stu-id="1127f-143">To get an Apple Push Notification service certificate:</span></span>
  
1. <span data-ttu-id="1127f-144">新しいタブを開く、 [Apple プッシュ証明書のポータル](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)に移動し、アップルの id。 を使用してサインイン</span><span class="sxs-lookup"><span data-stu-id="1127f-144">Open a new tab, go to the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2), and sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="1127f-145">[**開始**] ページで、**証明書の作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-145">On the **Get Started** page, click **Create a Certificate**.</span></span>
    
3. <span data-ttu-id="1127f-146">[**使用条件**] ページ**を読み、これらの条項および条件に同意する**] と、[**承諾**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-146">On the **Terms of Use** page, select **I have read and agree to these terms and conditions**, and then click **Accept**.</span></span>
    
4. <span data-ttu-id="1127f-p108">**プッシュの新しい証明書の作成**] ページで、[**参照**] をクリックし、前の手順で保存**開発 test.csr**ファイルを選択し、[**アップロード**] をクリックします。Json ファイルを開くダイアログ ボックスが表示されたら、開発 test.csr ファイルが保存されている同じフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="1127f-p108">On the **Create a New Push Certificate** page, click **Browse** and select the **dev-test.csr** file saved in the previous procedure, and then click **Upload**. When prompted to open a json file, save it to the same folder where the dev-test.csr file is stored.</span></span>
    
5. <span data-ttu-id="1127f-149">オープン[Apple プッシュ証明書のポータル](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2)で別のタブおよび**サード パーティのサーバーの証明書**の**ダウンロード**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-149">Open the [Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&amp;rv=2) in a different tab and for **Certificates for Third-Party Servers**, click **Download**.</span></span>
    
6. <span data-ttu-id="1127f-p109">.Pem ファイルを開くダイアログ ボックスが表示されたら、開発の test.csr ファイルが保存されている同じフォルダーに名前**開発 test.pem**で保存します。これは、Apn の証明書です。</span><span class="sxs-lookup"><span data-stu-id="1127f-p109">When prompted to open a .pem file, save it with the name **dev-test.pem** to the same folder where the dev-test.csr file is stored. This is your APNs certificate.</span></span>
    
<span data-ttu-id="1127f-152">APNs 証明書を Intune にアップロードするには、</span><span class="sxs-lookup"><span data-stu-id="1127f-152">To upload the APNs certificate into Intune:</span></span>
  
1. <span data-ttu-id="1127f-153">**Apn の証明書のアップロード**] ページで、[Microsoft Intune 管理コンソール] タブでは、 **Apn の証明書をアップロード**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-153">On the Microsoft Intune administration console tab, on the **Upload an APNs Certificate** page, click **Upload the APNs certificate**.</span></span>
    
2. <span data-ttu-id="1127f-154">[**参照**] をクリックし、**開発の test.pem**ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="1127f-154">Click **Browse** and specify the **dev-test.pem** file.</span></span>
    
3. <span data-ttu-id="1127f-p110">[**開く**] をクリックし、Apple ID アカウント名を入力し、[**アップロード**] をクリックします。**IOS と MaxOS X モバイル デバイス管理のセットアップ**] ページ**の登録の準備が完了**のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1127f-p110">Click **Open**, type your Apple ID account name, and then click **Upload**. You should see a **Ready for enrollment** message on the **iOS and MaxOS X Mobile Device Management Setup** page.</span></span>
    
<span data-ttu-id="1127f-157">APNs 証明書がインストールされていると、登録したデバイスにポリシーをプッシュすることで、Intune で iOS の登録と管理ができます。</span><span class="sxs-lookup"><span data-stu-id="1127f-157">With the APNs certificate installed, Intune can now enroll and manage iOS devices by pushing policy to enrolled mobile devices.</span></span>
  
<span data-ttu-id="1127f-158">Microsoft Intune ポータル サイト アプリをダウンロードして iOS デバイスを登録するには、</span><span class="sxs-lookup"><span data-stu-id="1127f-158">To download the Microsoft Intune Company portal app and enroll the iOS device:</span></span>
  
1. <span data-ttu-id="1127f-159">iOS デバイスから Apple ID でサインインします。</span><span class="sxs-lookup"><span data-stu-id="1127f-159">From your iOS device, sign in with your Apple ID.</span></span>
    
2. <span data-ttu-id="1127f-160">**アップル ストア**アプリケーションを開きます。</span><span class="sxs-lookup"><span data-stu-id="1127f-160">Open the **Apple Store** app.</span></span>
    
3. <span data-ttu-id="1127f-161">**Intune**を検索ボックスに入力し、 **Microsoft Intune 企業ポータル**では、**取得**、し**インストール**をタップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-161">Type **intune** in the search box and tap **Microsoft Intune Company Portal**, then **Get**, and then **Install**.</span></span>
    
4. <span data-ttu-id="1127f-162">後に**開く**のインストール] をタップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-162">After it installs, tap **Open**.</span></span>
    
5. <span data-ttu-id="1127f-163">**Intune 企業ポータル**画面には、Office 365 グローバル管理者アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="1127f-163">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
6. <span data-ttu-id="1127f-164">**企業アクセスのセットアップ**画面で、**開始**をタップして、**続行**2 回です。</span><span class="sxs-lookup"><span data-stu-id="1127f-164">On the **Company Access Setup** screen, tap **Begin**, and then tap **Continue** twice.</span></span>
    
7. <span data-ttu-id="1127f-165">**、次ですか?** ] 画面で、[**登録**] をタップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-165">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
8. <span data-ttu-id="1127f-166">**をアクティブにするデバイスの管理者ですか?**画面で、**アクティブにする**] をタップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-166">On the **Activate device administrator?** screen, tap **Activate**.</span></span>
    
9. <span data-ttu-id="1127f-167">[**プロファイルの管理**] 画面で、**インストール**をタップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-167">On the **Management Profile** screen, tap **Install**.</span></span>
    
10. <span data-ttu-id="1127f-168">**パスコードの入力**で、iOS デバイスのパスコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="1127f-168">In **Enter Passcode**, type your iOS device passcode.</span></span>
    
11. <span data-ttu-id="1127f-169">**何があっても次**の画面で、**登録**をタップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-169">On the **What comes next** screen, tap **Enroll**.</span></span>
    
12. <span data-ttu-id="1127f-170">**プロファイルのインストール**、**インストール**をタップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-170">In **Install Profile**, tap **Install**.</span></span>
    
13. <span data-ttu-id="1127f-171">[**警告**] ページで、**インストール**をタップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-171">On the **Warning** page, tap **Install**.</span></span>
    
14. <span data-ttu-id="1127f-172">**リモート管理**では、**信頼**をタップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-172">In **Remote Management**, tap **Trust**.</span></span>
    
15. <span data-ttu-id="1127f-173">登録プロセスを完了する**完了**をタップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-173">Tap **Done** to complete the enrollment process.</span></span>
    
16. <span data-ttu-id="1127f-174">メッセージが表示されたら**「Comp ポータル」では、このページを開いて?**、**開く**] をタップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-174">When prompted to **Open this page in "Comp Portal"?**, tap **Open**.</span></span>
    
17. <span data-ttu-id="1127f-175">**企業アクセスのセットアップ**画面で、**開始**をタップして、**行われます**。</span><span class="sxs-lookup"><span data-stu-id="1127f-175">On the **Company Access Setup** screen, tap **Begin**, and then tap **Done**.</span></span>
    
18. <span data-ttu-id="1127f-176">Microsoft Intune ポータル サイト アプリのメイン画面に、次のものが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1127f-176">On the main screen of the Microsoft Intune Company Portal app, you should see:</span></span>
    
  - <span data-ttu-id="1127f-177">緑色のバナー。</span><span class="sxs-lookup"><span data-stu-id="1127f-177">A green banner.</span></span>
    
  - <span data-ttu-id="1127f-178">左上に架空の会社名。</span><span class="sxs-lookup"><span data-stu-id="1127f-178">Your fictional company name in the upper left.</span></span>
    
  - <span data-ttu-id="1127f-179">**[マイ デバイス**] に表示されている iOS デバイス名です。</span><span class="sxs-lookup"><span data-stu-id="1127f-179">Your iOS device name listed in **My Devices**.</span></span>
    
  - <span data-ttu-id="1127f-180">[**ヘルプデスク**] セクションで電話番号**555-1234**と**電子メールを使用して連絡先**ボタンの**User5**の**連絡先の名前**。</span><span class="sxs-lookup"><span data-stu-id="1127f-180">In the **Helpdesk** section, the **Contact Name** of **User5** with the phone number of **555-1234** and a **Contact by email** button.</span></span>
    
<span data-ttu-id="1127f-p111">Microsoft Intune には、リモート ロック機能とパスコードのリセット機能あります。ユーザーがデバイスを紛失した場合は、デバイスをリモートからロックできます。ユーザーがパスコードを忘れた場合は、パスコードをリモートから削除できます。</span><span class="sxs-lookup"><span data-stu-id="1127f-p111">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="1127f-184">iOS デバイスをリモートからロックするには、</span><span class="sxs-lookup"><span data-stu-id="1127f-184">To lock an iOS device remotely:</span></span>
  
1. <span data-ttu-id="1127f-185">管理コンピューターからお使いのブラウザーでは、Microsoft Intune 管理コンソール] タブには、左側のナビゲーションの**グループ**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-185">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="1127f-186">**グループ**ウィンドウで開くには**のすべてのデバイス > すべてのモバイル デバイス > すべての直接管理されているデバイス**。</span><span class="sxs-lookup"><span data-stu-id="1127f-186">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="1127f-187">**すべての直接管理されているデバイス**のウィンドウで、[**デバイス**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-187">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="1127f-188">デバイスの一覧で、対象の iOS デバイスをクリックします。 </span><span class="sxs-lookup"><span data-stu-id="1127f-188">In the devices list, click your iOS device.</span></span> 
    
5. <span data-ttu-id="1127f-189">iOS デバイスから、そのデバイスのメイン画面が表示されていることを確認します。 </span><span class="sxs-lookup"><span data-stu-id="1127f-189">From your iOS device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="1127f-p112">管理コンピューターから、タスク バーをクリックして**リモート タスク > リモート ロック**。ロックアウトの画面に切り替わると、iOS のデバイスを監視します。</span><span class="sxs-lookup"><span data-stu-id="1127f-p112">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="1127f-192">パスコードを削除するには、</span><span class="sxs-lookup"><span data-stu-id="1127f-192">To remove the passcode:</span></span>
  
1. <span data-ttu-id="1127f-193">管理コンピューターから、**すべての直接管理されているデバイス**のウィンドウで、[**デバイス**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-193">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="1127f-p113">の一覧では、iOS デバイスをクリックします。タスク バーをクリックして**リモート タスク > パスコード リセット**。1 分間待機します。</span><span class="sxs-lookup"><span data-stu-id="1127f-p113">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="1127f-p114">お使いの iOS デバイスからロックを解除して、パスコードが不要になったことに注意してください。再度パスコードを変更するには、し、**パスコード****の設定**[に移動します。</span><span class="sxs-lookup"><span data-stu-id="1127f-p114">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
## <a name="phase-3-for-android-devices-only-enroll-and-manage-an-android-device"></a><span data-ttu-id="1127f-199">フェーズ 3 (Android デバイス専用):Android デバイスを登録して管理します</span><span class="sxs-lookup"><span data-stu-id="1127f-199">Phase 3 (for Android devices only): Enroll and manage an Android device</span></span>

<span data-ttu-id="1127f-200">Intune で管理するために Android デバイスを登録するには、次のものが必要になります。</span><span class="sxs-lookup"><span data-stu-id="1127f-200">You will need the following to enroll an Android device for management by Intune:</span></span>
  
- <span data-ttu-id="1127f-201">Android デバイス。</span><span class="sxs-lookup"><span data-stu-id="1127f-201">An Android device.</span></span>
    
- <span data-ttu-id="1127f-202">デバイスのパスコードのナレッジです。</span><span class="sxs-lookup"><span data-stu-id="1127f-202">Knowledge of the device's passcode.</span></span>
    
<span data-ttu-id="1127f-203">Intune ポータル サイト アプリをダウンロードして Android デバイスを登録するには、</span><span class="sxs-lookup"><span data-stu-id="1127f-203">To download the Intune Company portal app and enroll the Android device:</span></span>
  
1. <span data-ttu-id="1127f-204">Android デバイスでは、 **Google プレイ ストア**に移動し、**開始**] をタップし、します。</span><span class="sxs-lookup"><span data-stu-id="1127f-204">From your Android device, go to the **Google Play Store**, and then tap **Get Started**.</span></span>
    
2. <span data-ttu-id="1127f-205">**Intune**を [検索] ボックスに入力し、 **intune 企業ポータル**検索結果での順にタップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-205">Type **intune** in the search box, and then tap **intune company portal** in the search results.</span></span>
    
3. <span data-ttu-id="1127f-206">**Intune 企業ポータル**の項目をタップして、**インストール**します。</span><span class="sxs-lookup"><span data-stu-id="1127f-206">Tap the **Intune Company Portal** item, and then tap **Install**.</span></span>
    
4. <span data-ttu-id="1127f-207">**アカウントのセットアップの完了**画面では、**続行**、し、[**スキップ**をタップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-207">On the **For Complete account setup** screen, tap **Continue**, and then **Skip**.</span></span>
    
5. <span data-ttu-id="1127f-p115">** **Intune 企業ポータル**をタップします。**アプリケーションをインストールします。</span><span class="sxs-lookup"><span data-stu-id="1127f-p115">In **Intune Company Portal**, tap **Accept**. The app installs.</span></span>
    
6. <span data-ttu-id="1127f-210">、[**開く**] をタップし、[**サインイン**] をタップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-210">Tap **Open**, and then tap **Sign in**.</span></span>
    
7. <span data-ttu-id="1127f-211">**Intune 企業ポータル**画面には、Office 365 グローバル管理者アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="1127f-211">On the **Intune Company Portal** screen, sign in with your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="1127f-212">**企業アクセスのセットアップ**画面で、**開始**し、**続行**を 2 回タップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-212">On the **Company Access Setup** screen, tap **Begin**, and then **Continue** twice.</span></span>
    
9. <span data-ttu-id="1127f-213">**、次ですか?** ] 画面で、[**登録**] をタップします。</span><span class="sxs-lookup"><span data-stu-id="1127f-213">On the **What comes next?** screen, tap **Enroll**.</span></span>
    
10. <span data-ttu-id="1127f-214">**をアクティブにするデバイスの管理者ですか?**画面をタップして**をアクティブにする**。</span><span class="sxs-lookup"><span data-stu-id="1127f-214">On the **Activate device administrator?** screen, tap **Activate.**</span></span>
    
11. <span data-ttu-id="1127f-p116">[**プライバシー ポリシー** ] 画面では、**承認**を選択し、[**確認**] をタップします。登録処理が完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="1127f-p116">On the **Privacy Policy** screen, select **I acknowledge** and then tap **Confirm**. Wait for the enrollment process to complete.</span></span>
    
12. <span data-ttu-id="1127f-217">**会社のアクセスの設定**] 画面で**続行**をタップして、**行われます**。</span><span class="sxs-lookup"><span data-stu-id="1127f-217">In the **Company Access Setup** screen, tap **Continue**, and then tap **Done**.</span></span>
    
13. <span data-ttu-id="1127f-218">Microsoft Intune ポータル サイト アプリのメイン画面には、緑色のバナーと、架空の会社名が左上に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1127f-218">On the main screen of the Microsoft Intune Company Portal app, you should see a green banner and your fictional company name in the upper left.</span></span>
    
14. <span data-ttu-id="1127f-p117">**デバイス**をタップします。一覧に、Android のデバイス名を参照してくださいする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1127f-p117">Tap **My devices**. You should see your Android device name in the list.</span></span>
    
15. <span data-ttu-id="1127f-p118">**IT 管理者に連絡**] をタップします。**555-1234**、 **e メールでお問い合わせください**ボタンの電話番号が表示され、 **User5**の IT にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="1127f-p118">Tap **Contact IT**. You should see the phone number of **555-1234**, a **Contact by email** button, and the IT contact of **User5**.</span></span>
    
<span data-ttu-id="1127f-p119">Microsoft Intune には、リモート ロック機能とパスコードのリセット機能あります。ユーザーがデバイスを紛失した場合は、デバイスをリモートからロックできます。ユーザーがパスコードを忘れた場合は、パスコードをリモートからリセットできます。</span><span class="sxs-lookup"><span data-stu-id="1127f-p119">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset the passcode remotely.</span></span>
  
<span data-ttu-id="1127f-226">Android デバイスをリモートからロックするには、</span><span class="sxs-lookup"><span data-stu-id="1127f-226">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="1127f-227">管理コンピューターからお使いのブラウザーでは、Microsoft Intune 管理コンソール] タブには、左側のナビゲーションの**グループ**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-227">From your administration computer, on the Microsoft Intune administration console tab of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="1127f-228">**グループ**ウィンドウで開くには**のすべてのデバイス > すべてのモバイル デバイス > すべての直接管理されているデバイス**。</span><span class="sxs-lookup"><span data-stu-id="1127f-228">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="1127f-229">**すべての直接管理されているデバイス**のウィンドウで、[**デバイス**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-229">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="1127f-230">デバイスの一覧で、目的の Android デバイスをクリックします。 </span><span class="sxs-lookup"><span data-stu-id="1127f-230">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="1127f-231">対象の Android デバイスから、そのデバイスのメイン画面が表示されていることを確認します。 </span><span class="sxs-lookup"><span data-stu-id="1127f-231">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="1127f-p120">管理コンピューターから、タスク バーをクリックして**リモート タスク > リモート ロック**。ダイアログ ボックスが表示されたら、[**はい**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-p120">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="1127f-234">対象の Android デバイスがロックアウト画面に切り替わる様子を確認します。</span><span class="sxs-lookup"><span data-stu-id="1127f-234">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="1127f-235">Android デバイスのパスコードをリセットすると、Intune 管理ポータルを生成し、強力なパスコードを設定します。</span><span class="sxs-lookup"><span data-stu-id="1127f-235">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="1127f-236">パスコードをリモートからリセットするには、</span><span class="sxs-lookup"><span data-stu-id="1127f-236">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="1127f-237">管理コンピューターから Microsoft Intune 管理コンソール] タブの**すべての直接管理されているデバイス**のウィンドウに、ブラウザーの上には、Android デバイスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-237">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="1127f-238">タスク バーをクリックして**リモート タスク > パスコード リセット**。</span><span class="sxs-lookup"><span data-stu-id="1127f-238">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="1127f-p121">**リモート タスク: パスコード リセット**プロンプトで、[**はい**] をクリックします。1 分間待機します。</span><span class="sxs-lookup"><span data-stu-id="1127f-p121">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="1127f-241">**すべての直接管理されているデバイス**のウィンドウで、**ビューのプロパティ**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1127f-241">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="1127f-242">**パスコードのリセット**では、新しいパスコードを注意してください。</span><span class="sxs-lookup"><span data-stu-id="1127f-242">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="1127f-243">Android でデバイスのロックアウト画面から、新しいパスコードを入力します。 </span><span class="sxs-lookup"><span data-stu-id="1127f-243">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="1127f-244">再度パスコードを変更するに**設定**に**デバイス**をタップ、**ロック画面**をタップして、パスコードの新しいパスコードをもう一度、タップして**画面のロック**、および選択を入力してください。</span><span class="sxs-lookup"><span data-stu-id="1127f-244">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    
> [!TIP]
> <span data-ttu-id="1127f-245">クリックしては、[ここで](http://aka.ms/catlgstack)1 つのマイクロソフト クラウド テスト ラボ ガイド スタック内のアーティクルのすべてのビジュアル マップです。</span><span class="sxs-lookup"><span data-stu-id="1127f-245">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1127f-246">See Also</span><span class="sxs-lookup"><span data-stu-id="1127f-246">See Also</span></span>

[<span data-ttu-id="1127f-247">Microsoft 365 Enterprise 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="1127f-247">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="1127f-248">Microsoft 365 エンタープライズ開発/テスト環境の MAM のポリシー</span><span class="sxs-lookup"><span data-stu-id="1127f-248">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="1127f-249">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="1127f-249">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="1127f-250">エンタープライズ モビリティとセキュリティ (EMS)</span><span class="sxs-lookup"><span data-stu-id="1127f-250">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


