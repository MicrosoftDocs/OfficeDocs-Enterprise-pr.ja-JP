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
ms.openlocfilehash: 320a59043ab2a8810f9bfc03fdcf896241ec6b20
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915502"
---
# <a name="exchange-online-integration-for-your-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="16511-103">Office 365 と Dynamics 365 の開発/テスト環境の Exchange Online 統合</span><span class="sxs-lookup"><span data-stu-id="16511-103">Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="16511-104">**概要:** このテスト ラボ ガイドを使用して、Office 365 試用版サブスクリプションで Exchange Online 向けの Dynamics 365 統合を有効にします。</span><span class="sxs-lookup"><span data-stu-id="16511-104">**Summary:** Use this Test Lab Guide to enable Dynamics 365 integration for Exchange Online in your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="16511-p101">Microsoft Dynamics 365 の 1 つの有用な使用法は、適切なアクセス許可を持つユーザーが関連する顧客レコードすべてを参照できるよう、すべての顧客コミュニケーションを 1 つの場所に格納することです。たとえば、特定の連絡先、アカウント、営業案件、サポート案件などに関連付けられているすべての電子メールを閲覧できます。</span><span class="sxs-lookup"><span data-stu-id="16511-p101">A valuable use of Microsoft Dynamics 365 is to store all customer communications in one place, so anyone with the appropriate permissions can see all relevant customer records. For example, view all email associated with a particular contact, account, opportunity, or case.</span></span>
  
<span data-ttu-id="16511-p102">Dynamics 365 に電子メールと他のメッセージング レコードを保存するには、お使いのメール システムと Dynamics 365 を同期する必要があります。電子メールを同期する最適な方法は、サーバー側同期です。</span><span class="sxs-lookup"><span data-stu-id="16511-p102">To store email and other messaging records in Dynamics 365, you need to synchronize your email system with Dynamics 365. Server-side synchronization is the method of choice for email synchronization.</span></span>
  
<span data-ttu-id="16511-109">このテスト ラボ ガイドを使用して、Dynamics 365 に保存されている情報を Exchange Online と Outlook Online クライアントで活用するための構成とデモンストレーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="16511-109">Use this Test Lab Guide to configure and demonstrate how Exchange Online and the Outlook Online client can leverage the information stored in Dynamics 365.</span></span> 
  
## <a name="phase-1-build-out-the-office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="16511-110">フェーズ 1: Office 365 と Dynamics 365 開発/テスト環境を構成する</span><span class="sxs-lookup"><span data-stu-id="16511-110">Phase 1: Build out the Office 365 and Dynamics 365 dev/test environment</span></span>

<span data-ttu-id="16511-111">「[Office 365 と Dynamics 365 の開発/テスト環境](office-365-and-dynamics-365-dev-test-environment.md)」の手順を実行して、Office 365 と Dynamics 365 の開発/テスト環境のライトウェイト、またはシミュレーションのエンタープライズ バージョンを作成します。</span><span class="sxs-lookup"><span data-stu-id="16511-111">Use the instructions in [Office 365 and Dynamics 365 dev/test environment](office-365-and-dynamics-365-dev-test-environment.md) to create either a lightweight or simulated enterprise version of an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
> [!NOTE]
> <span data-ttu-id="16511-p103">この記事の構成には、シミュレーションのエンタープライズ開発/テスト環境は必要ありません。シミュレーションのエンタープライズ開発/テスト環境には、インターネットに接続されたシミュレーションのイントラネット、Windows Server Active Directory (AD) フォレスト用のディレクトリ同期が含まれています。この機能は、一般的な組織と類似した環境で Office 365 と Dynamics 365 を試していただけるよう、オプションとしてここで提供されています。</span><span class="sxs-lookup"><span data-stu-id="16511-p103">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server Active Directory (AD) forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization</span></span> 
  
## <a name="phase-2-configure-and-demonstrate-dynamics-365-integration-in-exchange-online"></a><span data-ttu-id="16511-114">フェーズ 2: Exchange Online の Dynamics 365 統合を構成しデモンストレーションする</span><span class="sxs-lookup"><span data-stu-id="16511-114">Phase 2: Configure and demonstrate Dynamics 365 integration in Exchange Online</span></span>

<span data-ttu-id="16511-115">以下の手順を使用して、Dynamics 365 と Exchange Online 統合用の全体管理者のメールボックスを構成します。</span><span class="sxs-lookup"><span data-stu-id="16511-115">Use these steps to configure the global administrator's mailbox for Dynamics 365 and Exchange Online integration:</span></span>
  
1. <span data-ttu-id="16511-116">お使いのブラウザーのプライベート ・ セッションを使用して[http://portal.office.com](http://portal.office.com)し、Office 365 のグローバル管理者アカウントを使用してサインインします。</span><span class="sxs-lookup"><span data-stu-id="16511-116">Using a private session of your browser, go to [http://portal.office.com](http://portal.office.com) and sign in using your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="16511-117">**Microsoft Office ホーム** ページで、 **[メール]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="16511-117">On the **Microsoft Office Home** page, click the **Mail** tile.</span></span>
    
3. <span data-ttu-id="16511-118">お使いのブラウザーの新しい **[メール]** タブで **[新規作成]** をクリックして、メッセージ入力ボックスの下のウィンドウ下部の隅に [マイ テンプレート] のアイコンが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="16511-118">On the new **Mail** tab in your browser, click **New** and notice how the bottom corner of the pane below the box for typing a message contains an icon for My Templates.</span></span>
    
     ![Dynamics 365 との統合なしの、新しい空の電子メール メッセージ。](media/879b54fd-a68f-4581-9f89-d5050df6f4de.png)
  
4. <span data-ttu-id="16511-120">**[破棄]** をクリックして、 **[メール]** タブを開いたままにします。</span><span class="sxs-lookup"><span data-stu-id="16511-120">Click **Discard** and leave the **Mail** tab open.</span></span>
    
5. <span data-ttu-id="16511-121">ブラウザーの **[Microsoft Office ホーム]** タブをクリックし、次いで **[管理者]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="16511-121">Click the **Microsoft Office Home** tab in your browser, and then click the **Admin** tile.</span></span>
    
6. <span data-ttu-id="16511-122">**[Office 管理センター]** タブの左側のナビゲーションで、 **[管理センター]、[Dynamics 365]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="16511-122">In the left navigation of the **Office Admin center** tab, click **Admin centers > Dynamics 365**.</span></span>
    
7. <span data-ttu-id="16511-123">お使いのブラウザーの新しい **[Dynamics 365]** タブで、Dynamics 365 のインスタンスの一覧から、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16511-123">On the new **Dynamics 365** tab in your browser, in the list of Dynamics 365 instances, click **Open**.</span></span>
    
8. <span data-ttu-id="16511-124">お使いのブラウザーの新しい **[管理]** タブで、ナビゲーション バーの **[設定]** の横の下矢印をクリックして、 **[システム]** の下にある **[電子メールの構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16511-124">On the new **Administration** tab in your browser, on the navigation bar, click the down arrow next to **Settings**, and then click **Email Configuration** under **System**.</span></span>
    
9.  <span data-ttu-id="16511-125">**[電子メールの構成]** ページで **[電子メール構成の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16511-125">On the **Email Configuration** page, click **Email Configuration Settings**.</span></span>
    
10. <span data-ttu-id="16511-126">**[システム設定]** ダイアログ ボックスの **[電子メール]** タブで、 **[予定、取引先担当者、タスク]** を **[サーバー側同期]** に変更し、次いで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16511-126">In the **Email** tab on the **System Settings** dialog box, change **Appointments, Contacts, and Tasks** to **Server-Side Synchronization**, and then click **OK**.</span></span>
    
11. <span data-ttu-id="16511-127">**[電子メールの構成]** ページで、 **[メールボックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16511-127">On the **Email Configuration** page, click **Mailboxes**.</span></span>
    
12. <span data-ttu-id="16511-128">左側のチェック マークの列で Office 365 の全体管理者名を選択し、ツール バーの **[既定の電子メール設定を適用]** をクリックし、次いで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16511-128">Select the Office 365 global administrator name in the left check mark column, click **Apply Default Email Settings** in the tool bar, and then click **OK**.</span></span>
    
13. <span data-ttu-id="16511-129">ツール バーの **[電子メールの承認]** をクリックし、次いで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16511-129">Click **Approve Email** in the tool bar, and then click **OK**.</span></span>
    
14. <span data-ttu-id="16511-130">左側のチェック マークの列で Office 365 の全体管理者名を選択し、ツール バーの **&amp;[メールボックスのテストと有効化]** をクリックし、次いで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16511-130">Select the Office 365 global administrator name in the left check mark column, click **Test &amp; Enable Mailboxes** in the tool bar, and then click **OK**.</span></span>
    
15. <span data-ttu-id="16511-131">開いている **[メール]** タブをクリックして全体管理者がテスト メッセージを受信したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="16511-131">Click the open **Mail** tab and confirm that the global administrator received a test message.</span></span>
    
16. <span data-ttu-id="16511-p104">ブラウザーで、メールボックスの **[自分のアクティブなメールボックス]** タブに戻り、ページを更新します。全体管理者のアカウント名で、 **[受信メールの状態]** と **[送信メールの状態]** の列が **[正常に完了]** に設定されるはずです。両方のテストを完了するのに 15 分ほどかかるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="16511-p104">Return to the **Mailboxes My Active Mailboxes** tab in your browser and refresh the page. The **Incoming Email Status** and **Outgoing Email Status** columns should be set to **Success** for the global administrator account name. Note that it can take up to 15 minutes to complete both tests.</span></span>
    
<span data-ttu-id="16511-135">以下の手順を使用して、Outlook 用の Dynamics 365 アプリをインストールし、全体管理者のメールボックス内で Dynamics 365 の機能をデモンストレーションします。</span><span class="sxs-lookup"><span data-stu-id="16511-135">Use these steps to install the Dynamics 365 App for Outlook and demonstrate Dynamics 365 features within the global administrator's mailbox:</span></span>
  
1. <span data-ttu-id="16511-136">ブラウザーのメールボックスの **[自分のアクティブなメールボックス]** タブで、 **[設定]** の隣の下矢印をクリックして、 **[システム]** の下にある **[Outlook 用 Dynamics 365 アプリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16511-136">On the **Mailboxes My Active Mailboxes** tab in your browser, click the down arrow next to **Settings**, and then click **Dynamics 365 App for Outlook** under **System**.</span></span>
    
2. <span data-ttu-id="16511-p105">**[Outlook 用 Microsoft Dynamics 365 アプリをお使いになる前に]** のページで、全体管理者名をクリックし、次いで **[Outlook へのアプリの追加]** をクリックします。 **[状態]** 列が **[保留中]** に変わります。</span><span class="sxs-lookup"><span data-stu-id="16511-p105">On the **Getting Started with Microsoft Dynamics 365 App for Outlook** page, click the global administrator name, and then click **Add App to Outlook**. The **Status** column changes to **Pending**.</span></span>
    
3. <span data-ttu-id="16511-p106">状態が **[Outlook に追加済み]** に変わるまで、ページを更新します。この構成を完了するのに 15 分ほどかかるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="16511-p106">Refresh the page until the status changes to **Added to Outlook**. Note that it can take up to 15 minutes to complete this configuration.</span></span>
    
4. <span data-ttu-id="16511-141">ブラウザーの **[メール]** タブをクリックし、次いでそれを閉じます。</span><span class="sxs-lookup"><span data-stu-id="16511-141">Click on the **Mail** tab in your browser and then close it.</span></span>
    
5. <span data-ttu-id="16511-142">ブラウザーの **[Microsoft Office ホーム]** タブをクリックし、次いで **[メール]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="16511-142">Click the **Microsoft Office Home** tab in your browser, and then click the **Mail** tile.</span></span>
    
6. <span data-ttu-id="16511-p107">ブラウザーの新しい **[メール]** タブをクリックし、 **[新規作成]** をクリックします。メッセージ入力ボックスの下のウィンドウ下部の隅に [Dynamics 365] のアイコンが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="16511-p107">On the new **Mail** tab in your browser, click **New**. Notice that the bottom corner of the pane below the box for typing a message now contains an icon for Dynamics 365.</span></span>
    
     ![新しいアイコンが表示される、Dynamics 365 と統合された新しい空の電子メール メッセージ。](media/ecb822e1-45fe-4481-99a1-294317d1d2de.png)
  
7. <span data-ttu-id="16511-p108">[Dynamics 365] アイコンをクリックします。 **Dynamics 365** ウィンドウが表示されます。そこからこの電子メールを追跡したり、テンプレート、営業資料、記事などにアクセスしたりできます。</span><span class="sxs-lookup"><span data-stu-id="16511-p108">Click the Dynamics 365 icon. You should see a **Dynamics 365** pane, from which you can track this email or access templates, sales literature, or articles.</span></span>
    
8. <span data-ttu-id="16511-p109">電子メール メッセージの **[宛先]** フィールドに、 **alex.y.wu@outlook.com** とタイプし、次いで、 **Dynamics 365** ウィンドウの **[再試行]** をクリックします。 **Dynamics 365** ウィンドウの **[受信者]** セクションに、試用版サブスクリプションのサンプル データと共に提供されている、販売アプリケーションの取引先担当者 Alex Wu の情報が表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="16511-p109">In the **To** field of the email message, type **alex.y.wu@outlook.com**, and then click **Retry** in the **Dynamics 365** pane. You should see a **Recipients** section in the **Dynamics 365** pane with information on Alex Wu, a contact from the sales application that was provided with the sample data for your trial subscription.</span></span>
    
     ![Dynamics 365 に格納されている営業担当者用の Dynamics 365 情報ウィンドウ。](media/a010fa5f-3f1b-47d4-ab5e-d00d85a24a3f.png)
  
9. <span data-ttu-id="16511-151">**[破棄]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16511-151">Click **Discard**.</span></span>

> [!TIP]
> <span data-ttu-id="16511-152">[ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="16511-152">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="16511-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="16511-153">See Also</span></span>

[<span data-ttu-id="16511-154">Office 365 と Dynamics 365 の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="16511-154">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="16511-155">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="16511-155">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="16511-156">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="16511-156">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="16511-157">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="16511-157">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="16511-158">Office 365 開発/テスト環境の DirSync</span><span class="sxs-lookup"><span data-stu-id="16511-158">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="16511-159">Dynamics 365 (オンライン) のサブスクリプション管理</span><span class="sxs-lookup"><span data-stu-id="16511-159">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="16511-160">Dynamics 365 の管理</span><span class="sxs-lookup"><span data-stu-id="16511-160">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


