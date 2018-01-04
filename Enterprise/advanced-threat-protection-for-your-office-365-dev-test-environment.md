---
title: "Office 365 開発/テスト環境の Advanced Threat Protection"
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
ms.assetid: 51019757-20ac-498c-b51e-cae6d41a8c08
description: "概要: Office 365 の開発/テスト環境で Office 365 Advanced Threat Protection を構成し、デモンストレーションします。"
ms.openlocfilehash: 00b1fc8fea930346f082d3d2302a14dea7ad4309
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="advanced-threat-protection-for-your-office-365-devtest-environment"></a><span data-ttu-id="fa633-103">Office 365 開発/テスト環境の Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="fa633-103">Advanced Threat Protection for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="fa633-104">**概要:** Office 365 の開発/テスト環境で Office 365 Advanced Threat Protection を構成し、デモンストレーションします。</span><span class="sxs-lookup"><span data-stu-id="fa633-104">**Summary:** Configure and demonstrate Office 365 Advanced Threat Protection in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="fa633-p101">Office 365 Advanced Threat Protection (ATP) は、マルウェアから電子メールを保護する Exchange Online Protection (EOP) の機能です。ATP を使用して、Exchange 管理センター (EAC) またはセキュリティ/コンプライアンス センターでポリシーを作成し、常にユーザーが電子メール内の悪質なものではないと識別されたリンクまたは添付ファイルのみにアクセスするようにします。詳細については、「[安全な添付ファイルと安全なリンクのための高度な脅威保護](https://technet.microsoft.com/library/mt148491%28v=exchg.150%29.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa633-p101">Office 365 Advanced Threat Protection (ATP) is a feature of Exchange Online Protection (EOP) that helps keep malware out of your email. With ATP, you create policies in the Exchange admin center (EAC) or the Security & Compliance center that help ensure your users access only links or attachments in emails that are identified as not malicious. For more information, see  Advanced threat protection for safe attachments and safe links https://technet.microsoft.com/library/mt148491(v=exchg.150).aspx .</span></span>
  
<span data-ttu-id="fa633-108">この記事の手順を使用して、Office 365 の試用版サブスクリプションで ATP を構成してテストできます。</span><span class="sxs-lookup"><span data-stu-id="fa633-108">With the instructions in this article, you configure and test ATP in your Office 365 trial subscription.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="fa633-109">フェーズ 1:ライトウェイトの、またはシミュレーションのエンタープライズ Office 365 開発/テスト環境を構築する</span><span class="sxs-lookup"><span data-stu-id="fa633-109">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="fa633-110">最小要件でのライトウェイトの方法で ATP をテストする場合は、[Office 365 開発/テスト環境](office-365-dev-test-environment.md) のフェーズ 2 とフェーズ 3 の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="fa633-110">If you just want to test ATP in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="fa633-111">エンタープライズのシミュレーションで ATP をテストする場合は、[Office 365 開発/テスト環境の DirSync](dirsync-for-your-office-365-dev-test-environment.md) の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="fa633-111">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="fa633-p102">ATP のテストには、シミュレーションのエンタープライズ開発/テスト環境は必要ありません。シミュレーションのエンタープライズ開発/テスト環境には、インターネットに接続されたシミュレーションのイントラネット、Windows サーバー AD フォレスト用のディレクトリ同期が含まれています。この機能は、一般的な組織と類似した環境で ATP をテストしてお試しいただけるようオプションとしてここで提供されています。</span><span class="sxs-lookup"><span data-stu-id="fa633-p102">Testing ATP does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test ATP and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-the-default-email-delivery-behavior-of-office-365"></a><span data-ttu-id="fa633-114">フェーズ 2: Office 365 の既定の電子メール配信動作をデモンストレーションする</span><span class="sxs-lookup"><span data-stu-id="fa633-114">Phase 2: Demonstrate the default email delivery behavior of Office 365</span></span>

<span data-ttu-id="fa633-115">このフェーズでは、ATP ポリシーの構成前には、悪意のある可能性のある電子メールがスクリーニングまたは軽減策なしで Office 365 のメールボックスに配信されることをデモンストレーションします。</span><span class="sxs-lookup"><span data-stu-id="fa633-115">In this phase, you demonstrate that before configuring ATP policies, potentially malicious email gets delivered to Office 365 mailboxes without screening or mitigation.</span></span>
  
1. <span data-ttu-id="fa633-116">Internet Explorer を開き、[Office 365 開発/テスト環境](office-365-dev-test-environment.md) のフェーズ 2 で作成した Outlook アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="fa633-116">Open Internet Explorer and sign in to the Outlook account you created in Phase 2 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="fa633-117">ライトウェイトの Office 365 開発/テスト環境を使用している場合は、Internet Explorer のプライベート セッションを開いてローカル コンピューターからサインインします。</span><span class="sxs-lookup"><span data-stu-id="fa633-117">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="fa633-118">シミュレーションのエンタープライズ Office 365 開発/テスト環境を使用している場合は、[Azure ポータル]((https://portal.azure.com)) を使用して CLIENT1 仮想マシンに接続し、CLIENT1 からサインインします。</span><span class="sxs-lookup"><span data-stu-id="fa633-118">If you are using the simulated enterprise Office 365 dev/test environment, use the [Azure portal]((https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="fa633-119">メモ帳を起動し、テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="fa633-119">Run Notepad and enter some text.</span></span>
    
3. <span data-ttu-id="fa633-120">ファイルを **getKeys.js** としてドキュメント フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="fa633-120">Save the file to the Documents folder as **getKeys.js**.</span></span>
    
4. <span data-ttu-id="fa633-121">Internet Explorer の [Outlook メール] タブで、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-121">From the Outlook Mail tab of Internet Explorer, click **New**.</span></span>
    
5. <span data-ttu-id="fa633-122">**[送信先]** に、試用版サブスクリプションの Office 365 グローバル管理者名の電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="fa633-122">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
6. <span data-ttu-id="fa633-123">件名に、「 **新しいキー**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="fa633-123">For the subject, type **Your new keys**.</span></span>
    
7. <span data-ttu-id="fa633-124">本文に、「 **ファイルを添付します**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="fa633-124">In the body, type **Here is the file**.</span></span>
    
8. <span data-ttu-id="fa633-125">**[添付]** をクリックして、ドキュメント フォルダーの **getKeys.js** をダブルクリックし、 **[コピーとして添付]**、 **[送信]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-125">Click **Attach**, double-click **getKeys.js** in the Documents folder, click **Attach as a copy**, and then click **Send**.</span></span>
    
9. <span data-ttu-id="fa633-126">[ **新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-126">Click **New**.</span></span>
    
10. <span data-ttu-id="fa633-127">**[送信先]** に、試用版サブスクリプションの Office 365 グローバル管理者名の電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="fa633-127">In **To**, type the email address of the Office 365 global administrator name of your trial subscription.</span></span>
    
11. <span data-ttu-id="fa633-128">件名に、「 **新しい旅の Web サイト**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="fa633-128">For the subject, type **New travel web site**.</span></span>
    
12. <span data-ttu-id="fa633-129">本文に、「 **他のユーザーからこのサイトが自分に転送されました**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="fa633-129">In the body, type **Someone forwarded me this site**.</span></span>
    
13. <span data-ttu-id="fa633-130">本文で、「 **このサイト**」のテキストを選択して、ツールのハイパーリンク アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-130">In the body, select the **this site** text and click the hyperlink icon in the toolbar.</span></span>
    
14. <span data-ttu-id="fa633-131">**URL** に、 **http://www.spamlink.contoso.com/** と入力して、 **[OK]**、 **[送信]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-131">In **URL**, type **http://www.spamlink.contoso.com/**, click **OK**, and then click **Send**.</span></span>
    
15. <span data-ttu-id="fa633-132">プライベート ブラウズ モードで Internet Explorer のインスタンスを個別に開き、Office 365 ポータル ([(https://portal.office.com)]((https://portal.office.com))) に移動し、グローバル管理者アカウントで Office 365 試用版サブスクリプションにサインインします。</span><span class="sxs-lookup"><span data-stu-id="fa633-132">Open a separate instance of Internet Explorer in private browsing mode, go to the Office 365 portal ([(https://portal.office.com)]((https://portal.office.com))), and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
16. <span data-ttu-id="fa633-133">メイン ポータル ページで、アプリ タイルをクリックし、 **[メール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-133">From the main portal page, click the apps tile, and then click **Mail**.</span></span>
    
17. <span data-ttu-id="fa633-134">受信トレイで、件名が「 **新しいキー**」のメッセージをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-134">In the Inbox, click the message with the subject **Your new keys**.</span></span>
    
18. <span data-ttu-id="fa633-p103">迷惑メール フォルダーで、件名が「 **新しい旅の Web サイト**」のメッセージをクリックします。メッセージ内で、 **"このサイト"** リンクをクリックします。「申し訳ございません。spamlink.contoso.com が見つかりませんでした。」ページが表示されます。その場所には Web ページが存在しないので、これは正しい結果です。</span><span class="sxs-lookup"><span data-stu-id="fa633-p103">In the Junk Mail folder, click the message with the subject **New travel web site**. Within the message, click the **this site** link. You should see a "Oops! Internet Explorer could not find spamlink.contoso.com." page. This is the correct result because there is no web page at that location.</span></span>
    
<span data-ttu-id="fa633-p104">悪意のある可能性のあるこれらの両方の電子メールが配信されたことに注目してください。「 **新しいキー**」の電子メールには、検出されないマルウェアが含まれている可能性があり、「 **新しい旅の Web サイト**」の電子メールでは、ユーザーは悪意のある可能性のあるリンクをクリックすることが許可されました。</span><span class="sxs-lookup"><span data-stu-id="fa633-p104">Notice that both of these potentially malicious emails were delivered successfully. The **Your new keys** email could contain undetected malware and the user was allowed to click the potentially malicious link in the **New travel web site** email.</span></span>
  
## <a name="phase-3-configure-safe-attachment-and-safe-links-policies-for-atp"></a><span data-ttu-id="fa633-143">フェーズ 3:ATP の安全な添付ファイルと安全なリンクのポリシーを構成する</span><span class="sxs-lookup"><span data-stu-id="fa633-143">Phase 3: Configure safe attachment and safe links policies for ATP</span></span>

<span data-ttu-id="fa633-144">このフェーズでは、悪意のある可能性のファイルが添付された電子メールが配信されないようするために安全な添付ファイルに関するポリシーを、また安全でない可能性のある URL にユーザーがアクセスできないようにするために安全なリンクに関するポリシーを作成して、構成します。</span><span class="sxs-lookup"><span data-stu-id="fa633-144">In this phase, you create and configure a safe attachment policy to prevent email with potentially malicious attachments from being delivered and a safe links policy to keep users from traveling to potentially unsafe URLs.</span></span>
  
1. <span data-ttu-id="fa633-145">Internet Explorer の **[Microsoft Office Home]** タブで、 **[管理者]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-145">On the **Microsoft Office Home** tab of Internet Explorer, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="fa633-146">左側のナビゲーションで、 **[管理センター]** をクリックして、 **[Exchange]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-146">In the left navigation, click **Admin centers**, and then **Exchange**.</span></span>
    
3. <span data-ttu-id="fa633-147">[Exchange 管理センター] タブの左側のナビゲーションで、 **[高度な脅威]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-147">In the left navigation of the Exchange admin center tab, click **advanced threats**.</span></span>
    
4. <span data-ttu-id="fa633-148">**[安全な添付ファイル]** タブをクリックして、プラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-148">Click the **safe attachments** tab, and then click the plus sign.</span></span>
    
5. <span data-ttu-id="fa633-149">**[安全な添付ファイルの新しいポリシー]** ウィンドウの **[名前]** で、「 **安全な添付ファイルのポリシー - ブロック**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="fa633-149">In the **new safe attachments policy** window, in **Name**, type **Safe Attachment Policy - Block**.</span></span>
    
6. <span data-ttu-id="fa633-150">**[安全な添付ファイルの不明なマルウェアへの応答]** では、 **[ブロック]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-150">For **Safe attachments unknown malware response**, click **Block**.</span></span>
    
7. <span data-ttu-id="fa633-151">**[検出で添付ファイルをリダイレクトする]** では、 **[リダイレクトを有効にする]** をクリックして、Office 365 グローバル管理者アカウントの電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="fa633-151">For **Redirect attachment on detection**, click **Enable redirect** and type the email address of your Office 365 global administrator account.</span></span>
    
8. <span data-ttu-id="fa633-p105">**[適用対象]** では、下矢印をクリックして、 **[受信者のドメイン]** をクリックします。ウィンドウで、自分の組織名 (contoso.onmicrosoft.com など) をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-p105">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
9. <span data-ttu-id="fa633-p106">**[保存]** をクリックします。更新後、新しく、有効な **[安全な添付ファイルのポリシー - ブロック]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fa633-p106">Click **Save**. After the update, you should see the new and enabled **Safe Attachment Policy - Block**.</span></span>
    
10. <span data-ttu-id="fa633-156">**[安全なリンク]** タブをクリックして、プラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-156">Click the **safe links** tab, and then click the plus sign.</span></span>
    
11. <span data-ttu-id="fa633-157">**[安全なリンクの新しいポリシー]** ウィンドウの **[名前]** で、「 **安全なリンクのポリシー**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="fa633-157">In the **new safe links policy** window, in **Name**, type **Safe Link Policy**.</span></span>
    
12. <span data-ttu-id="fa633-158">**[メッセージ内の悪意のある可能性のある不明な URL に対するアクションを選択する]** では、 **[オン]** をクリックして、 **[ユーザーがクリックで元の URL に移動することを許可しない]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fa633-158">For **Select the action for unknown potentially malicious URLs in messages**, click **On**, and then select **Do not allow users to click through to original URL**.</span></span>
    
13. <span data-ttu-id="fa633-p107">**[適用対象]** では、下矢印をクリックして、 **[受信者のドメイン]** をクリックします。ウィンドウで、自分の組織名 (contoso.onmicrosoft.com など) をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-p107">For **Applied to**, click the down arrow, and then click **The recipient domain is**. In the window, click your organization name (such as contoso.onmicrosoft.com), and then click **OK**.</span></span>
    
14. <span data-ttu-id="fa633-p108">**[保存]** をクリックします。新しい **[安全なリンクのポリシー]** が有効になって表示されます。</span><span class="sxs-lookup"><span data-stu-id="fa633-p108">Click **Save**. You should see the new and enabled **Safe Link Policy**.</span></span>
    
## <a name="phase-4-show-atp-in-action"></a><span data-ttu-id="fa633-163">フェーズ 4: 実行中の ATP を表示する</span><span class="sxs-lookup"><span data-stu-id="fa633-163">Phase 4: Show ATP in action</span></span>

<span data-ttu-id="fa633-164">このフェーズでは、ATP が悪意のある可能性のある電子メールを処理する方法をデモンストレーションします。</span><span class="sxs-lookup"><span data-stu-id="fa633-164">In this phase, you demonstrate how ATP deals with potentially malicious email.</span></span>
  
1. <span data-ttu-id="fa633-165">フェーズ 2 で電子メールの送信に使用した Internet Explorer のインスタンスの左側のナビゲーションで、 **[アイテムの送信]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-165">From the instance of Internet Explorer that you used to send the email in Phase 2, in the left navigation, click **Sent Items.**</span></span>
    
2. <span data-ttu-id="fa633-166">「 **新しいキー**」というタイトルの電子メールをクリックして、下矢印アイコンをクリックし、 **[転送]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-166">Click the email titled **Your new keys**, click the down arrow icon, and then click **Forward**.</span></span>
    
3. <span data-ttu-id="fa633-167">新しいメッセージでの **[送信先]** に試用版サブスクリプションの Office 365 グローバル管理者名の電子メール アドレスを入力して、 **[送信]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-167">For the new message, in **To**, type the email address of the Office 365 global administrator name of your trial subscription, and then click **Send**.</span></span>
    
4. <span data-ttu-id="fa633-168">「 **新しい旅の Web サイト**」というタイトルの電子メールをクリックして、下矢印をクリックし、 **[全員へ返信]**、 **[送信]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-168">Click the email titled **New travel web site**, click the down arrow icon, click **Reply all**, and then click **Send**.</span></span>
    
5. <span data-ttu-id="fa633-p109">フェーズ 3 で ATP ポリシーの構成に使用した Internet Explorer のインスタンスで、[Exchange 管理センター] タブをクリックし、アプリ タイルをクリックして、 **[メール]** をクリックします。受信トレイに次の 2 つの新しい電子メール メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fa633-p109">From the instance of Internet Explorer that you used to configure ATP policies in Phase 3, click the Exchange admin center tab, click the apps tile, and then click **Mail**. You should see two new email messages in the Inbox:</span></span>
    
  - <span data-ttu-id="fa633-171">「 **Fw: 新しいキー**」というタイトルの電子メール メッセージ</span><span class="sxs-lookup"><span data-stu-id="fa633-171">One titled **Fw: Your new keys**</span></span>
    
  - <span data-ttu-id="fa633-172">「 **Fw: 新しい旅の Web サイト**」というタイトルの電子メール メッセージ</span><span class="sxs-lookup"><span data-stu-id="fa633-172">One titled **Fw: New travel web site**</span></span>
    
6. <span data-ttu-id="fa633-p110">「 **Fw: 新しい旅の Web サイト**」というタイトルの電子メール メッセージを開いて、「 **このサイト**」リンクをクリックします。「この Web サイトは悪意のあるサイトとして分類されました。」ページが表示されます。これは、ATP が悪意のある可能性のある Web サイトにユーザーがアクセスしないようにしていることを実証しています。</span><span class="sxs-lookup"><span data-stu-id="fa633-p110">Open the email message titled **Fw: New travel web site** and click the **this site** link. You should see a "This website has been classified as malicious." page. This demonstrates that ATP is preventing you from accessing the potentially malicious web site.</span></span>
    
7. <span data-ttu-id="fa633-177">Internet Explorer の [Exchange 管理センター] タブにある左側のナビゲーションで、 **[メール フロー]** をクリックします。。</span><span class="sxs-lookup"><span data-stu-id="fa633-177">In the Exchange admin center tab of Internet Explorer, in the left navigation, click **mail flow**.</span></span>
    
8. <span data-ttu-id="fa633-178">**[メッセージ追跡]** タブをクリックして、 **[検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa633-178">Click the **message trace** tab, and then click **search**.</span></span>
    
9. <span data-ttu-id="fa633-p111">**[メッセージ追跡の結果]** ウィンドウで、件名が「 **新しいキー**」のメッセージをダブルクリックします。このメッセージは受信トレイに正常に配信されました。このウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="fa633-p111">In the **Message Trace Results** window, double-click the message with the subject **Your new keys**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
10. <span data-ttu-id="fa633-p112">件名が「 **新しい旅の Web サイト**」のメッセージをダブルクリックします。このメッセージは受信トレイに正常に配信されました。このウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="fa633-p112">Double-click the message with the subject **New travel web site**. This message was successfully delivered to the Inbox. Close this window.</span></span>
    
11. <span data-ttu-id="fa633-p113">件名が「 **Fw: 新しいキー**」のメッセージをダブルクリックします。このメッセージが ATP によってどのように処理され、受信トレイに配信されたかに注目してください。このウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="fa633-p113">Double-click the message with the subject **Fw: Your new keys**. Note how this message was processed by ATP and then delivered to the Inbox. Close this window.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="fa633-p114">安全な添付ファイルに関するポリシーの目的は、添付ファイルに対し悪意のあるコードのスキャンを開始することでした。悪意のあるものとは判断されなかったので、getKeys.js の添付ファイルは許可されました。この手順により、ATP が添付ファイルのスキャンを実行したことがわかります。</span><span class="sxs-lookup"><span data-stu-id="fa633-p114">The purpose of the safe attachments policy was to begin scanning attachments for malicious code. The getKeys.js attachment was allowed because it was not determined to be malicious. This step shows that ATP did perform a scan of the attachment.</span></span> 
  
12. <span data-ttu-id="fa633-p115">件名が「 **Fw: 新しい旅の Web サイト**」のメッセージをダブルクリックします。このメッセージが受信トレイに正常に配信されたことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="fa633-p115">Double-click the message with the subject **Fw: New travel web site**. Note that this message was successfully delivered to the Inbox.</span></span>
    
<span data-ttu-id="fa633-193">これで、この環境を使用して、新しいポリシーを作成し ATP を試すことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="fa633-193">You can now use this environment to create new policies and experiment with ATP.</span></span>
  
> [!TIP]
> <span data-ttu-id="fa633-194">
            [ここ]((http://aka.ms/catlgstack))をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="fa633-194">Click [here]((http://aka.ms/catlgstack)) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fa633-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa633-195">See Also</span></span>

[<span data-ttu-id="fa633-196">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="fa633-196">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="fa633-197">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="fa633-197">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="fa633-198">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="fa633-198">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="fa633-199">Office 365 開発/テスト環境の DirSync</span><span class="sxs-lookup"><span data-stu-id="fa633-199">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="fa633-200">Office 365 開発/テスト環境の Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="fa633-200">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="fa633-201">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="fa633-201">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md) 

<span data-ttu-id="fa633-202">[安全な添付ファイルと安全なリンクのための高度な脅威保護]((https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653))</span><span class="sxs-lookup"><span data-stu-id="fa633-202">[Advanced threat protection for safe attachments and safe links]((https://support.office.com/article/Office-365-Advanced-Threat-Protection-E100FE7C-F2A1-4B7D-9E08-622330B83653))</span></span>


