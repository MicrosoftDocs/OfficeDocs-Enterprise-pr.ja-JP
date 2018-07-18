---
title: Office 365 ラベルと DLP による SharePoint ファイルの保護
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: '概要: 情報保護のレベルが多様な SharePoint Online チーム サイトに、Office 365 ラベルとデータ損失防止 (DLP) ポリシーを適用します。'
ms.openlocfilehash: 439f59f683090d39ea98730854aa1ca5dc8db482
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319268"
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a><span data-ttu-id="5ed2c-103">Office 365 ラベルと DLP による SharePoint ファイルの保護</span><span class="sxs-lookup"><span data-stu-id="5ed2c-103">Protect SharePoint Online files with Office 365 labels and DLP</span></span>

 <span data-ttu-id="5ed2c-104">**概要:** 情報保護のレベルが多様な SharePoint Online チーム サイトに、Office 365 ラベルとデータ損失防止 (DLP) ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-104">**Summary:** Apply Office 365 labels and data loss prevention (DLP) policies for SharePoint Online team sites with various levels of information protection.</span></span>
  
<span data-ttu-id="5ed2c-p101">この記事にある手順を使用して、ベースライン、機密、および高機密の SharePoint Online チーム サイト用の Office 365 ラベルおよび DLP ポリシーを設計および展開します。これらの 3 つの層の保護について詳しくは、「[Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-p101">Use the steps in this article to design and deploy Office 365 labels and DLP policies for baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="how-this-works"></a><span data-ttu-id="5ed2c-107">そのしくみ</span><span class="sxs-lookup"><span data-stu-id="5ed2c-107">How this solution works</span></span>
1. <span data-ttu-id="5ed2c-p102">目的のラベルを作成して発行します。それらが発行されるまでに、最大 12 時間かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-p102">Create the desired labels and publish these. It can take up to 12 hours for these to be published.</span></span>
2. <span data-ttu-id="5ed2c-110">目的の SharePoint サイトについて、ドキュメント ライブラリの設定を編集して、ライブラリ内の項目にラベルを適用します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-110">For the desired SharePoint sites, edit the document library settings to apply a label to items in the library.</span></span>
3. <span data-ttu-id="5ed2c-111">ラベルに基づいてアクションを実行する DLP ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-111">Create DLP policies to take action based on the labels.</span></span>

<span data-ttu-id="5ed2c-p103">ユーザーがドキュメントをライブラリに追加すると、文書は既定で割り当てられるラベルを受け取ります。ユーザーは、必要に応じてラベルを変更できます。ユーザーが組織外のドキュメントを共有する場合、DLP はラベルが割り当てられているかどうかを確認し、DLP ポリシーがラベルに一致する場合にアクションを実行します。DLP は同様に、他のポリシーの一致を探します。たとえば、クレジット カード番号によるファイルの保護などです (この種類のポリシーが設定されている場合)。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-p103">When users add a document to the library, the document will receive the assigned label by default. Users can change the label,if needed. When a user shares a document outside the organization, DLP will check to see if a label is assigned and take action if a DLP policy matches the label. DLP will look for other policy matches as well, such as protecting files with credit card numbers if this type of policy is configured.</span></span> 

## <a name="office-365-labels-for-your-sharepoint-online-sites"></a><span data-ttu-id="5ed2c-116">SharePoint Online サイトの Office 365 ラベル</span><span class="sxs-lookup"><span data-stu-id="5ed2c-116">Office 365 labels for your SharePoint Online sites</span></span>

<span data-ttu-id="5ed2c-117">Office 365 のラベルを作成し、SharePoint Online チーム サイトにラベルを割り当てるためのフェーズは 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-117">There are three phases to creating and then assigning Office 365 labels to SharePoint Online team sites.</span></span>
  
### <a name="phase-1-determine-the-office-365-label-names"></a><span data-ttu-id="5ed2c-118">フェーズ 1: Office 365 ラベル名を決定する</span><span class="sxs-lookup"><span data-stu-id="5ed2c-118">Phase 1: Determine the Office 365 label names</span></span>

<span data-ttu-id="5ed2c-p104">このフェーズでは、SharePoint Online チーム サイトに適用される 4 レベルの情報保護用に、Office 365 ラベルの名前を決定します。 次の表は、各レベルに推奨される名前の一覧です。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-p104">In this phase, you determine the names of your Office 365 labels for the four levels of information protection applied to SharePoint Online team sites. The following table lists the recommended names for each level.</span></span>
  
|<span data-ttu-id="5ed2c-121">**SharePoint Online チーム サイトの保護レベル**</span><span class="sxs-lookup"><span data-stu-id="5ed2c-121">**SharePoint Online team site protection level**</span></span>|<span data-ttu-id="5ed2c-122">**ラベル名**</span><span class="sxs-lookup"><span data-stu-id="5ed2c-122">**Label name**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5ed2c-123">ベースライン - パブリック</span><span class="sxs-lookup"><span data-stu-id="5ed2c-123">Baseline-Public</span></span>  <br/> |<span data-ttu-id="5ed2c-124">内部パブリック</span><span class="sxs-lookup"><span data-stu-id="5ed2c-124">Internal public</span></span>  <br/> |
|<span data-ttu-id="5ed2c-125">ベースライン - プライベート</span><span class="sxs-lookup"><span data-stu-id="5ed2c-125">Baseline-Private</span></span>  <br/> |<span data-ttu-id="5ed2c-126">Kirkland</span><span class="sxs-lookup"><span data-stu-id="5ed2c-126">Private</span></span>  <br/> |
|<span data-ttu-id="5ed2c-127">機密</span><span class="sxs-lookup"><span data-stu-id="5ed2c-127">Sensitive</span></span>  <br/> |<span data-ttu-id="5ed2c-128">機密</span><span class="sxs-lookup"><span data-stu-id="5ed2c-128">Sensitive</span></span>  <br/> |
|<span data-ttu-id="5ed2c-129">非常に機密性の高い社外秘</span><span class="sxs-lookup"><span data-stu-id="5ed2c-129">Highly Confidential</span></span>  <br/> |<span data-ttu-id="5ed2c-130">非常に機密性の高い社外秘</span><span class="sxs-lookup"><span data-stu-id="5ed2c-130">Highly Confidential</span></span>  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a><span data-ttu-id="5ed2c-131">フェーズ 2: Office 365 のラベルを作成する</span><span class="sxs-lookup"><span data-stu-id="5ed2c-131">Phase 2: Create the Office 365 labels</span></span>

<span data-ttu-id="5ed2c-132">このフェーズでは、さまざまなレベルの情報保護について決定したラベルを作成し、発行します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-132">In this phase, you create and then publish your determined labels for the different levels of information protection.</span></span>
  
<span data-ttu-id="5ed2c-133">ラベルを作成するには、Office 365 管理センターまたは Microsoft PowerShell を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-133">To create the labels, you can use the Office 365 Admin center or Microsoft PowerShell.</span></span>
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a><span data-ttu-id="5ed2c-134">Office 365 管理センターで Office 365 のラベルを作成する</span><span class="sxs-lookup"><span data-stu-id="5ed2c-134">Create Office 365 labels with the Office 365 Admin center</span></span>

1. <span data-ttu-id="5ed2c-p105">セキュリティ管理者または会社管理者のロールのアカウントを使用して、Office 365 ポータルにサインインします。ヘルプを表示するには、「[Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-p105">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="5ed2c-137">**[Microsoft Office Home]** タブで、**[管理者]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-137">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="5ed2c-138">ブラウザーの新しい **[Office 管理者センター]** タブで、**[管理センター] > [セキュリティとコンプライアンス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-138">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="5ed2c-139">ブラウザーの新しい **[ホーム – セキュリティとコンプライアンス]** タブをクリックして、**[分類] > [ラベル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-139">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="5ed2c-140">**[ホーム] > [ラベル]** ウィンドウで、**[ラベルの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-140">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="5ed2c-141">**[ラベルに名前をつける]** ウィンドウで、ラベルの名前を入力して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-141">On the **Name your label** pane, type the name of the label, and then click **Next**.</span></span>
    
7. <span data-ttu-id="5ed2c-142">**[ラベル設定]** ウィンドウで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-142">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="5ed2c-143">**[設定の確認]** ウィンドウで、**[このラベルを作成する]** をクリックして、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-143">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="5ed2c-144">追加ラベルについて手順 5 から 8 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-144">Repeat steps 5-8 for your additional labels.</span></span>
    
### <a name="create-office-365-labels-with-powershell"></a><span data-ttu-id="5ed2c-145">PowerShell で Office 365 のラベルを作成する</span><span class="sxs-lookup"><span data-stu-id="5ed2c-145">Create Office 365 labels with PowerShell</span></span>

1. <span data-ttu-id="5ed2c-146">[リモート PowerShell を使用して Office 365 セキュリティ &amp; コンプライアンス センターに接続](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409)し、セキュリティ管理者ロールまたは会社の管理者ロールを持つアカウントの資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-146">[Connect to the Office 365 Security &amp; Compliance Center using remote PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) and specify the credentials of an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="5ed2c-147">ラベル名の一覧を入力し、PowerShell コマンド プロンプトで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-147">Fill out the list of label names, and then run these commands at the PowerShell command prompt:</span></span>
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

<span data-ttu-id="5ed2c-148">次に、以下の手順で新しい Office 365 ラベルを発行します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-148">Next, use these steps to publish the new Office 365 labels.</span></span>
  
1. <span data-ttu-id="5ed2c-149">**[ホーム] > [ラベル]** ウィンドウの [セキュリティ &amp; コンプライアンス センター] で、**[ラベルの発行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-149">From the **Home > Labels** pane the Security &amp; Compliance Center, click **Publish labels**.</span></span>
    
2. <span data-ttu-id="5ed2c-150">**[発行するラベルを選択]** ウィンドウで、**[発行するラベルを選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-150">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
3. <span data-ttu-id="5ed2c-151">**[Choose labels]\(ラベルの選択\)** ウィンドウで、**[追加]** をクリックして 4 つのラベルをすべて選択します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-151">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
4. <span data-ttu-id="5ed2c-152">[ **完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-152">Click **Done**.</span></span>
    
5. <span data-ttu-id="5ed2c-153">**[発行するラベルを選択]** ウィンドウで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-153">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
6. <span data-ttu-id="5ed2c-154">**[場所の選択]** ウィンドウで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-154">On the **Choose locations** pane, click **Next**.</span></span>
    
7. <span data-ttu-id="5ed2c-155">**[ポリシーに名前をつける]** ウィンドウで、**[名前]** にラベルのセットの名前を入力し、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-155">On the **Name your policy** pane, type a name for your set of labels in **Name**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="5ed2c-156">**[設定の確認]** ウィンドウで、**[ラベルの発行]** をクリックして、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-156">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a><span data-ttu-id="5ed2c-157">フェーズ 3: SharePoint Online サイトに Office 365 ラベルを適用する</span><span class="sxs-lookup"><span data-stu-id="5ed2c-157">Phase 3: Apply the Office 365 labels to your SharePoint Online sites</span></span>

<span data-ttu-id="5ed2c-158">以下の手順で Office 365 ラベルを SharePoint Online チーム サイトのドキュメント フォルダーに適用します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-158">Use these steps to apply the Office 365 labels to the documents folders of your SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="5ed2c-159">ブラウザーの **Microsoft Office ホーム**のタブで、**[SharePoint]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-159">From the **Microsoft Office Home** tab of your browser, click the **SharePoint** tile.</span></span>
    
2. <span data-ttu-id="5ed2c-160">ブラウザーの新しい **SharePoint** タブで、Office 365 ラベルを割り当てる必要があるサイトをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-160">On the new **SharePoint** tab in your browser, click a site that needs an Office 365 label assigned.</span></span>
    
3. <span data-ttu-id="5ed2c-161">ブラウザーの新しい SharePoint サイト タブで、**[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-161">In the new SharePoint site tab of your browser, click **Documents**.</span></span>
    
4. <span data-ttu-id="5ed2c-162">設定アイコンをクリックし、**[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-162">Click the settings icon, and then click **Library settings**.</span></span>
    
5. <span data-ttu-id="5ed2c-163">**[権限と管理]** をクリックして、**[このライブラリ内の項目にラベルを適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-163">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
6. <span data-ttu-id="5ed2c-164">**[設定 - ラベルの適用]** で適切なラベルを選択し、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-164">In **Settings-Apply Label**, select the appropriate label, and then click **Save**.</span></span>
    
7. <span data-ttu-id="5ed2c-165">SharePoint Online サイトのタブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-165">Close the tab for the SharePoint Online site.</span></span>
    
8. <span data-ttu-id="5ed2c-166">手順 3 - 8 を繰り返して、その他の SharePoint Online サイトに Office 365 ラベルを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-166">Repeat steps 3-8 to assign Office 365 labels to your additional SharePoint Online sites.</span></span>
    
<span data-ttu-id="5ed2c-167">最終的な構成をここに示します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-167">Here is your resulting configuration.</span></span>
  
![4 種類の SharePoint Online チーム サイト用の Office 365 ラベル。](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a><span data-ttu-id="5ed2c-169">SharePoint Online サイトの DLP ポリシー</span><span class="sxs-lookup"><span data-stu-id="5ed2c-169">DLP policies for your SharePoint Online sites</span></span>

<span data-ttu-id="5ed2c-170">以下の手順で、SharePoint Online の機密チーム サイト上のドキュメントを組織外と共有するときにユーザーに通知する DLP ポリシーを構成します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-170">Use these steps to configure a DLP policy that notifies users when they share a document on a SharePoint Online sensitive team site outside the organization.</span></span>
  
1. <span data-ttu-id="5ed2c-171">ブラウザーの **[Microsoft Office Home]** タブで、**[セキュリティとコンプライアンス]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-171">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="5ed2c-172">ブラウザーの新しい **[セキュリティとコンプライアンス]** タブで、**[データ損失防止] > [ポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-172">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="5ed2c-173">**[データ損失防止]** ウィンドウで、 **[+ ポリシーの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-173">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="5ed2c-174">**[テンプレートを使って開始するか、カスタム ポリシーを作成する]** ウィンドウで、**[カスタム]** をクリックして、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-174">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="5ed2c-175">**[ポリシーに名前をつける]** ウィンドウの **[名前]** に機密レベル DLP ポリシーの名前を入力して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-175">In the **Name your policy** pane, type the name for the sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="5ed2c-176">**[場所の選択]** ウィンドウで、**[自分で特定の場所を選択する]** をクリックして、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-176">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="5ed2c-177">場所の一覧で、 **Exchange メール**と **OneDrive アカウント**の場所を無効にし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-177">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="5ed2c-178">**[保護する機密性の高い情報の種類をカスタマイズする]** ウィンドウで、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-178">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="5ed2c-179">**[保護するコンテンツの種類を選択する]** ウィンドウのドロップダウン ボックスで **[追加]** をクリックしてから、 **[ラベル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-179">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="5ed2c-180">**[ラベル]** ウィンドウで、 **[+ 追加]** をクリックして、 **[機密]** ラベルを選択し、 **[追加]** をクリックしてから、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-180">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="5ed2c-181">**[保護するコンテンツの種類を選択する]** ウィンドウで、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-181">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="5ed2c-182">**[Customize the types of sensitive info you want to protect]\(保護する機密情報の種類のカスタマイズ\)** ウィンドウで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-182">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="5ed2c-183">**[What do you want to do if we detect sensitive info?]\(機密情報が検出された場合の処理\)** ウィンドウで、**[Customize the tip and email]\(ヒントと電子メールをカスタマイズする)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-183">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="5ed2c-184">**[ポリシー ヒントと電子メール通知をカスタマイズする]** ウィンドウで、**[ポリシー ヒント テキストをカスタマイズする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-184">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="5ed2c-185">機密性の高いファイルを保護するために Azure Information Protection を実装したかどうかに応じて、テキスト ボックスに、次のいずれかのヒントを入力するか、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-185">In the text box, type or paste in one of the following tips, depending on if you implemented Azure Information Protection to protect highly confidential files:</span></span>
    
  - <span data-ttu-id="5ed2c-p106">組織外のユーザーと共有するには、ファイルをダウンロードしてから開きます。[ファイル]、[文書の保護]、[パスワードを使用して暗号化] の順にクリックし、強力なパスワードを指定します。別の電子メールまたはその他の通信手段でパスワードを送信します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-p106">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
  - <span data-ttu-id="5ed2c-p107">機密性の高いファイルは、暗号化によって保護されます。IT 部門によってこれらのファイルへのアクセス許可が与えられている外部ユーザーのみが、それらを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-p107">Highly confidential files are protected with encryption. Only external users who are granted permissions to these files by your IT department can read them.</span></span>
    
    <span data-ttu-id="5ed2c-p108">あるいは、組織外のファイルを共有する方法をユーザーに指示する独自のポリシー ヒントを入力するか、貼り付けます。Azure Information Protection で保護されているファイルに対するアクセス許可を外部ユーザーに付与する方法については、「外部ユーザーに対するアクセス許可の追加」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-p108">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization. For more information on giving external users permissions to files protected wiht Azure Information Protection, see Adding permissions for external users.</span></span>
    
16. <span data-ttu-id="5ed2c-193">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-193">Click **OK**.</span></span>
    
17. <span data-ttu-id="5ed2c-194">**[機密性の高い情報が検出された場合に実行する操作]** ウィンドウで、 **[ユーザーが共有できないようにし、共有コンテンツへのアクセスを制限する]** チェックボックスをクリアしてから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-194">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="5ed2c-195">**[ポリシーを有効にしますか、または最初にテストしますか?]** ウィンドウで、 **[すぐ有効にします]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-195">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="5ed2c-196">**[設定の確認]** ウィンドウで、**[作成]** をクリックして、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-196">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="5ed2c-197">機密 SharePoint Online チーム サイトの最終的な構成をここに示します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-197">Here is your resulting configuration for sensitive SharePoint Online team sites.</span></span>
  
![機密 Office 365 ラベルを使用している、独立した SharePoint Online チーム サイトの DLP ポリシー。](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
<span data-ttu-id="5ed2c-199">次に、以下の手順で、SharePoint Online の非常に機密性の高い社外秘チーム サイト上のドキュメントを組織外と共有するときにユーザーをブロックする DLP ポリシーを構成します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-199">Next, use these steps to configure a DLP policy that blocks users when they share a document on a SharePoint Online highly confidential team site outside the organization.</span></span>
  
1. <span data-ttu-id="5ed2c-200">ブラウザーの **[Microsoft Office Home]** タブで、**[セキュリティとコンプライアンス]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-200">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="5ed2c-201">ブラウザーの新しい **[セキュリティとコンプライアンス]** タブで、**[データ損失防止] > [ポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-201">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="5ed2c-202">**[データ損失防止]** ウィンドウで、 **[+ ポリシーの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-202">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="5ed2c-203">**[テンプレートを使って開始するか、カスタム ポリシーを作成する]** ウィンドウで、**[カスタム]** をクリックして、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-203">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="5ed2c-204">**[ポリシーに名前をつける]** ウィンドウの **[名前]** に高機密レベル DLP ポリシーの名前を入力して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-204">In the **Name your policy** pane, type the name for the highly sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="5ed2c-205">**[場所の選択]** ウィンドウで、**[自分で特定の場所を選択する]** をクリックして、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-205">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="5ed2c-206">場所の一覧で、 **Exchange メール**と **OneDrive アカウント**の場所を無効にし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-206">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="5ed2c-207">**[保護する機密性の高い情報の種類をカスタマイズする]** ウィンドウで、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-207">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="5ed2c-208">**[保護するコンテンツの種類を選択する]** ウィンドウのドロップダウン ボックスで **[追加]** をクリックしてから、 **[ラベル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-208">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="5ed2c-209">**[ラベル]** ウィンドウで、 **[+ 追加]** をクリックして、 **[高機密]** ラベルを選択し、 **[追加]** をクリックしてから、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-209">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="5ed2c-210">**[保護するコンテンツの種類を選択する]** ウィンドウで、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-210">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="5ed2c-211">**[Customize the types of sensitive info you want to protect]\(保護する機密情報の種類のカスタマイズ\)** ウィンドウで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-211">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="5ed2c-212">**[What do you want to do if we detect sensitive info?]\(機密情報が検出された場合の処理\)** ウィンドウで、**[Customize the tip and email]\(ヒントと電子メールをカスタマイズする)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-212">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="5ed2c-213">**[Customize policy tips and email notifications]\(ポリシー ヒントと電子メール通知のカスタマイズ\)** ウィンドウで、**[Customize the policy tip text]\(ポリシー ヒントのテキストをカスタマイズする\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-213">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="5ed2c-214">次の内容をテキスト ボックスに入力するか、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-214">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="5ed2c-p109">組織外のユーザーと共有するには、ファイルをダウンロードしてから開きます。[ファイル]、[文書の保護]、[パスワードを使用して暗号化] の順にクリックし、強力なパスワードを指定します。別の電子メールまたはその他の通信手段でパスワードを送信します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-p109">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="5ed2c-218">あるいは、ファイルを共有する方法について組織外のユーザーに指示する独自のポリシー ヒントを入力するか、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-218">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="5ed2c-219">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="5ed2c-220">**[機密性の高い情報が検出された場合に実行する操作]** ウィンドウで、 **[業務の妥当性を要求してオーバーライドする]** をクリックしてから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-220">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
18. <span data-ttu-id="5ed2c-221">**[ポリシーを有効にしますか、または最初にテストしますか?]** ウィンドウで、 **[すぐ有効にします]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="5ed2c-222">**[設定の確認]** ウィンドウで、**[作成]** をクリックして、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="5ed2c-223">非常に機密性の高い社外秘 SharePoint Online チーム サイトの最終的な構成をここに示します。</span><span class="sxs-lookup"><span data-stu-id="5ed2c-223">Here is your resulting configuration for high confidentiality SharePoint Online team sites.</span></span>
  
![高機密 Office 365 ラベルを使用している、独立した SharePoint Online チーム サイトの DLP ポリシー。](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a><span data-ttu-id="5ed2c-225">次の手順</span><span class="sxs-lookup"><span data-stu-id="5ed2c-225">Next step</span></span>

[<span data-ttu-id="5ed2c-226">Azure Information Protection を使用して SharePoint Online ファイルを保護する</span><span class="sxs-lookup"><span data-stu-id="5ed2c-226">Protect SharePoint Online files with Azure Information Protection</span></span>](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a><span data-ttu-id="5ed2c-227">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ed2c-227">See Also</span></span>

[<span data-ttu-id="5ed2c-228">SharePoint Online サイトとファイルをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="5ed2c-228">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="5ed2c-229">開発/テスト環境の SharePoint Online サイトをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="5ed2c-229">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="5ed2c-230">選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス</span><span class="sxs-lookup"><span data-stu-id="5ed2c-230">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="5ed2c-231">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="5ed2c-231">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


