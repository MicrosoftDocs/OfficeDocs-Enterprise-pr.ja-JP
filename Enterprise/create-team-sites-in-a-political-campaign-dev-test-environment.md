---
title: "選挙運動用の開発/テスト環境でチーム サイトを作成する"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: None
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: "概要: 政治キャンペーンの開発/テスト環境でパブリック、プライベート、機密、および機密性の高いオンラインの SharePoint のチーム サイトを作成します。"
ms.openlocfilehash: 82e671af271508dfdecac6169a7892a8a12b7865
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a><span data-ttu-id="8a458-103">選挙運動用の開発/テスト環境でチーム サイトを作成する</span><span class="sxs-lookup"><span data-stu-id="8a458-103">Create team sites in a political campaign dev/test environment</span></span>

 <span data-ttu-id="8a458-104">**の概要:**政治キャンペーンの開発/テスト環境でのパブリック、プライベート、機密、および機密性の高いオンラインの SharePoint のチーム サイトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8a458-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in your political campaign dev/test environment.</span></span> 
  
<span data-ttu-id="8a458-p101">[政治運動、慈善団体、およびその他のアジャイルな組織での Microsoft セキュリティ ガイダンス](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)については、4 種類の SharePoint Online のチーム サイトを含む、開発/テスト環境を作成するのには、この資料の手順を使用します。ソリューションです。これらのサイトは、 **SharePoint およびビジネスのための OneDrive**という名前のトピックの 10 で詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="8a458-p101">Use the instructions in this article to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. These sites are described in detail on Topic 10, titled **SharePoint and OneDrive for Business**.</span></span>
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a><span data-ttu-id="8a458-107">フェーズ 1: 選挙運動用の開発/テスト環境を作成する</span><span class="sxs-lookup"><span data-stu-id="8a458-107">Phase 1: Create your political campaign dev/test environment</span></span>

<span data-ttu-id="8a458-108">最初に、サブスクリプション、ユーザー、およびグループを作成するのには、[構成グループ](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)との政治キャンペーンの開発/テスト環境のユーザーの指示に従います。</span><span class="sxs-lookup"><span data-stu-id="8a458-108">First, follow the instructions in [Configure groups and users for a political campaign dev/test environment](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) to create your subscriptions, users, and groups.</span></span>
  
## <a name="phase-2-create-office-365-labels"></a><span data-ttu-id="8a458-109">フェーズ 2: Office 365 のラベルを作成する</span><span class="sxs-lookup"><span data-stu-id="8a458-109">Phase 2: Create Office 365 labels</span></span>

<span data-ttu-id="8a458-110">このフェーズでは、SharePoint Online チーム サイトのドキュメント フォルダーのセキュリティのレベルごとにラベルを作成します。</span><span class="sxs-lookup"><span data-stu-id="8a458-110">In this phase, you create the labels for the different levels of security for SharePoint Online team site document folders.</span></span>
  
1. <span data-ttu-id="8a458-p102">必要に応じて、Office 365 ポータルに、試用版サブスクリプション用の全体管理者アカウントの資格情報でサインインします。ヘルプについては、「[一般法人向け Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a458-p102">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="8a458-113">**[Microsoft Office Home]** タブで、 **[管理者]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-113">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="8a458-114">お使いのブラウザーの新しい**Office 管理者センター** ] タブからをクリックして**管理センター > セキュリティ&amp;準拠**。</span><span class="sxs-lookup"><span data-stu-id="8a458-114">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="8a458-115">新しいから**ホーム ・ セキュリティ&amp;準拠**タブ、ブラウザーのをクリックして**分類 > ラベル**。</span><span class="sxs-lookup"><span data-stu-id="8a458-115">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="8a458-116">**[ホーム] > [ラベル]** ウィンドウで、 **[ラベルの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-116">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="8a458-117">[ウィンドウ] の**名前ラベル**には、**内部**を入力し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-117">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="8a458-118">**[ラベル設定]** ウィンドウで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-118">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="8a458-119">**[設定の確認]** ウィンドウで、 **[このラベルを作成する]** をクリックしてから **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-119">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="8a458-120">次の追加ラベルについて手順 5 から 8 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="8a458-120">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="8a458-121">プライベート</span><span class="sxs-lookup"><span data-stu-id="8a458-121">Private</span></span>
    
  - <span data-ttu-id="8a458-122">機密</span><span class="sxs-lookup"><span data-stu-id="8a458-122">Sensitive</span></span>
    
  - <span data-ttu-id="8a458-123">高機密</span><span class="sxs-lookup"><span data-stu-id="8a458-123">Highly Confidential</span></span>
    
10. <span data-ttu-id="8a458-124">**[ホーム] > [ラベル]** ウィンドウで、 **[ラベルの発行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-124">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="8a458-125">**[発行するラベルを選択]** ウィンドウで、 **[発行するラベルを選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-125">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="8a458-126">**[ラベルの選択]** ウィンドウで、 **[追加]** をクリックして 4 つすべてのラベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="8a458-126">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="8a458-127">[ **完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-127">Click **Done**.</span></span>
    
14. <span data-ttu-id="8a458-128">**[発行するラベルを選択]** ウィンドウで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-128">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="8a458-129">**[場所の選択]** ウィンドウで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-129">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="8a458-130">**名ポリシー**ウィンドウで、**キャンペーン****名**を入力し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-130">On the **Name your policy** pane, type **Campaign** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="8a458-131">**[設定の確認]** ウィンドウで、 **[ラベルの発行]** をクリックしてから **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-131">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="8a458-132">フェーズ 3:SharePoint Online チーム サイトを作成する</span><span class="sxs-lookup"><span data-stu-id="8a458-132">Phase 3: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="8a458-133">このフェーズでは、SharePoint Online チーム サイトを作成し、4 つのタイプの SharePoint Online チーム サイトに対応する選挙運動用に構成します。</span><span class="sxs-lookup"><span data-stu-id="8a458-133">In this phase, you create and configure SharePoint Online team sites for your political campaign corresponding to the four types of SharePoint Online team sites.</span></span>
  
### <a name="campaign-wide-team-site"></a><span data-ttu-id="8a458-134">キャンペーン全体のチーム サイト</span><span class="sxs-lookup"><span data-stu-id="8a458-134">Campaign wide team site</span></span>

<span data-ttu-id="8a458-135">ベースラインのパブリック SharePoint Online チーム サイトを作成するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="8a458-135">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="8a458-136">必要な場合、ローカル コンピューター上のブラウザーを使用し、グローバル管理者アカウントを使用して、Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="8a458-136">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="8a458-137">タイルのリストで、 **[SharePoint]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-137">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="8a458-138">ブラウザーの新しい **[SharePoint]** タブで、 **[+ サイトの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-138">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="8a458-139">**[サイトの作成]** ページで、 **[チーム サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-139">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="8a458-140">**サイト名**、**キャンペーンの幅**を入力します。</span><span class="sxs-lookup"><span data-stu-id="8a458-140">In **Site name**, type **Campaign wide**.</span></span> 
    
6. <span data-ttu-id="8a458-141">**チーム サイトの説明**] には、**キャンペーン全体の SharePoint サイト**を入力します。</span><span class="sxs-lookup"><span data-stu-id="8a458-141">In **Team site description**, type **SharePoint site for the entire campaign**.</span></span>
    
7. <span data-ttu-id="8a458-142">**[プライバシー設定]** で、 **[パブリック - 組織の全ユーザーがこのサイトにアクセス可能]** を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-142">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="8a458-143">**[誰を追加しますか]** ウィンドウで、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-143">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="8a458-144">次に、キャンペーン全体のチーム サイトのドキュメント フォルダーを [内部] ラベル用に構成します。</span><span class="sxs-lookup"><span data-stu-id="8a458-144">Next, configure the documents folder of the Campaign wide team site for the Internal label.</span></span>
  
1. <span data-ttu-id="8a458-145">お使いのブラウザーの [**キャンペーンの全体にわたるホーム**] タブで [**ドキュメント**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-145">In the **Campaign wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="8a458-146">[設定] アイコンをクリックしてから、 **[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-146">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="8a458-147">**[権限と管理]** をクリックして、 **[このライブラリ内の項目にラベルを適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-147">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="8a458-148">**ラベルの設定の適用**] では、**内部**を選択し、し、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-148">In **Settings-Apply Label**, select **Internal**, and then click **Save**.</span></span>
    
### <a name="campaign-project-1-team-site"></a><span data-ttu-id="8a458-149">キャンペーン プロジェクト 1 のチーム サイト</span><span class="sxs-lookup"><span data-stu-id="8a458-149">Campaign project 1 team site</span></span>

<span data-ttu-id="8a458-150">キャンペーン内のプロジェクト用にベースラインのプライベート SharePoint Online チーム サイトを作成するには、以下のことを行います。</span><span class="sxs-lookup"><span data-stu-id="8a458-150">To create a baseline private SharePoint Online team site for a project within the campaign, do the following:</span></span>
  
1. <span data-ttu-id="8a458-151">必要な場合、ローカル コンピューター上のブラウザーを使用し、グローバル管理者アカウントを使用して、Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="8a458-151">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="8a458-152">タイルのリストで、 **[SharePoint]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-152">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="8a458-153">ブラウザーの新しい **[SharePoint]** タブで、 **[+ サイトの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-153">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="8a458-154">**[サイトの作成]** ページで、 **[チーム サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-154">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="8a458-155">**サイト名**、**キャンペーン プロジェクト 1**を入力します。</span><span class="sxs-lookup"><span data-stu-id="8a458-155">In **Site name**, type **Campaign project 1**.</span></span> 
    
6. <span data-ttu-id="8a458-156">**チーム サイトの説明**では、**キャンペーン プロジェクト 1 の SharePoint サイト**を入力します。</span><span class="sxs-lookup"><span data-stu-id="8a458-156">In **Team site description,** type **SharePoint site for Campaign project 1**.</span></span>
    
7. <span data-ttu-id="8a458-157">**[プライバシー設定]** で、 **[プライベート - メンバーのみがこのサイトにアクセス可能**」を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-157">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="8a458-158">**[誰を追加しますか]** ウィンドウで、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-158">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="8a458-159">次に、キャンペーン プロジェクト 1 チーム サイトのドキュメント フォルダーを [プライベート] ラベル用に構成します。</span><span class="sxs-lookup"><span data-stu-id="8a458-159">Next, configure the documents folder of the Campaign project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="8a458-160">**プロジェクト 1 のホームのキャンペーン**お使いのブラウザーのタブ、[**ドキュメント**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-160">In the **Campaign project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="8a458-161">[設定] アイコンをクリックしてから、 **[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-161">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="8a458-162">**[権限と管理]** をクリックして、 **[このライブラリ内の項目にラベルを適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-162">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="8a458-163">**[設定 - ラベルの適用]** で **[プライベート]** をクリックし、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-163">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
### <a name="campaign-marketing-team-site"></a><span data-ttu-id="8a458-164">キャンペーン マーケティング チーム サイト</span><span class="sxs-lookup"><span data-stu-id="8a458-164">Campaign marketing team site</span></span>

<span data-ttu-id="8a458-165">キャンペーン マーケティング リソース用の機密レベルの分離した SharePoint Online チーム サイトを作成するには、以下のことを行います。</span><span class="sxs-lookup"><span data-stu-id="8a458-165">To create a sensitive-level isolated SharePoint Online team site for campaign marketing resources, do the following:</span></span>
  
1. <span data-ttu-id="8a458-166">ブラウザーを使用して、ローカル コンピューター上で、グローバル管理者アカウントを使用して、Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="8a458-166">Using a browser on your local computer, sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="8a458-167">タイルのリストで、 **[SharePoint]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-167">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="8a458-168">ブラウザーの新しい **[SharePoint]** タブで、 **[+ サイトの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-168">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="8a458-169">**[サイトの作成]** ページで、 **[チーム サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-169">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="8a458-170">**チームのサイト名****キャンペーンのマーケティング**を入力します。</span><span class="sxs-lookup"><span data-stu-id="8a458-170">In **Team site name**, type **Campaign marketing**.</span></span>
    
6. <span data-ttu-id="8a458-171">**チーム サイトの説明**、 **(小文字) のマーケティング キャンペーン用の SharePoint サイト**を入力します。</span><span class="sxs-lookup"><span data-stu-id="8a458-171">In **Team site description**, type **SharePoint site for campaign marketing (sensitive)**.</span></span>
    
7.  <span data-ttu-id="8a458-172">**[プライバシー設定]** で、 **[プライベート - メンバーのみがこのサイトにアクセス可能**」を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-172">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="8a458-173">**[誰を追加しますか]** ウィンドウで、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-173">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="8a458-174">**キャンペーンのマーケティング**に新しいタブは、ブラウザー、ツール ・ バーの設定アイコンをクリックして**サイトのアクセス許可**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-174">On the new **Campaign marketing** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="8a458-175">**[サイトの権限]** ウィンドウで、 **[高度な権限の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-175">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="8a458-176">ブラウザーの新しい **[アクセス許可]** タブで、 **[アクセス要求の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-176">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="8a458-177">**アクセス要求の設定**] ダイアログ ボックスで、**サイトと個々 のファイルとフォルダーを共有するメンバーを許可して** **、サイトのメンバー グループの他のユーザーを招待するメンバーを許可する**チェック ボックスをオフ**@ ITAdmin1**を入力<your organization name> **。onmicrosoft.com** **アクセスに対するすべての要求を送信**] をクリック、し [ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-177">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**<your organization name> **.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="8a458-178">リストに**メンバーをマーケティング キャンペーン**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-178">Click **Campaign marketing Members** in the list.</span></span>
    
14. <span data-ttu-id="8a458-179">**[ユーザーとグループ]** ページで、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-179">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="8a458-180">[**共有**] ダイアログ ボックスで**シニアと戦略的なスタッフ**を入力して、選択し、し、[**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-180">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="8a458-181">**分析スタッフ**グループと**Regular1**のユーザー アカウントには、14 と 15 の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="8a458-181">Repeat steps 14 and 15 for the **Analytics staff** group and the **Regular1** user account.</span></span>
    
17. <span data-ttu-id="8a458-182">ブラウザーの戻るボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-182">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="8a458-183">リストの**所有者のマーケティング キャンペーン**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-183">Click **Campaign marketing Owners** in the list.</span></span>
    
19. <span data-ttu-id="8a458-184">**[ユーザーとグループ]** ページで、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-184">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="8a458-185">**[共有]** ダイアログ ボックスに「 **IT スタッフ**」と入力し、それを選択して、 **[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-185">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="8a458-186">ブラウザーの戻るボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-186">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="8a458-187">お使いのブラウザーで [**ユーザーとグループ**] タブを閉じてお使いのブラウザーでは、**キャンペーンのマーケティング ・ ホーム**] タブをクリックし、**サイトのアクセス許可**] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="8a458-187">Close the **People and Groups** tab in your browser, click the **Campaign marketing-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="8a458-188">権限を構成した結果を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="8a458-188">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="8a458-189">**キャンペーンのマーケティングのメンバー** SharePoint グループにのみ、**シニア、スタッフの戦略的な**グループ (候補、ChiefOfStaff、および Strategic1 のユーザー アカウントが含まれています) が含まれています、**キャンペーンのマーケティング**グループ (を含む、グローバル管理者ユーザー アカウントでは、**分析スタッフ**のグループ (DataScientist1 のユーザー アカウントが含まれています)、および**Regular1**のユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="8a458-189">The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.</span></span>
    
- <span data-ttu-id="8a458-190">**キャンペーンのマーケティングの所有者**SharePoint グループには、 **IT スタッフ**グループ (これは ITAdmin1 と ITAdmin2 のユーザー アカウントのみが含まれています) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8a458-190">The **Campaign marketing-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="8a458-191">**キャンペーンのマーケティング ユーザー**の SharePoint グループが含まれていますないグループまたはユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="8a458-191">The **Campaign marketing-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="8a458-192">メンバーは、(これのみ実行できます**キャンペーン マーケティング-Owners**グループのメンバーによって) サイト ・ レベルのアクセス許可を変更できません。</span><span class="sxs-lookup"><span data-stu-id="8a458-192">Members cannot modify site-level permissions (this can only be done by members of the **Campaign marketing-Owners** group).</span></span>
    
- <span data-ttu-id="8a458-193">他のユーザー アカウントは、サイトやそのリソースにアクセスできませんが、サイトへのアクセスを要求することができます。これにより、ITAdmin1 ユーザー アカウントのメールボックスに電子メールが送信されます。</span><span class="sxs-lookup"><span data-stu-id="8a458-193">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="8a458-194">次に、キャンペーン マーケティング チーム サイトのドキュメント フォルダーを [機密] ラベル用に構成します。</span><span class="sxs-lookup"><span data-stu-id="8a458-194">Next, configure the documents folder of the Campaign marketing team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="8a458-195">お使いのブラウザーの [**キャンペーンのマーケティング ・ ホーム**] タブで [**ドキュメント**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-195">In the **Campaign marketing-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="8a458-196">[設定] アイコンをクリックしてから、 **[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-196">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="8a458-197">**[権限と管理]** をクリックして、 **[このライブラリ内の項目にラベルを適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-197">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="8a458-198">**[設定 - ラベルの適用]** で **[機密]** をクリックし、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-198">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="8a458-p103">次に、組織外の機密ラベルを持つチームの SharePoint Online サイト上のドキュメントを共有する場合にユーザーに通知するデータ損失防止 (DLP) ポリシーを構成します。この DLP ポリシーは、キャンペーンのマーケティングのサイトのリソースに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8a458-p103">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label outside the organization. This DLP policy will apply to resources in the Campaign marketing site.</span></span>
  
1. <span data-ttu-id="8a458-201">お使いのブラウザーで [ **Microsoft Office のホーム**] タブをクリックして、**セキュリティ&amp;準拠**を並べて表示します。</span><span class="sxs-lookup"><span data-stu-id="8a458-201">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="8a458-202">新しい**セキュリティ&amp;準拠**お使いのブラウザーのタブをクリックして**データ損失防止 > ポリシー**。</span><span class="sxs-lookup"><span data-stu-id="8a458-202">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="8a458-203">**[データ損失防止]** ウィンドウで、 **[+ ポリシーの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-203">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="8a458-204">**[テンプレートを使って開始するか、カスタム ポリシーを作成する]** ウィンドウで、 **[カスタム]** をクリックしてから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-204">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="8a458-205">**[ポリシーに名前をつける]** ウィンドウで、 **[名前]** に「 **機密ラベル SharePoint Online チーム サイト**」と入力してから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-205">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="8a458-206">**[場所の選択]** ウィンドウで、 **[自分で特定の場所を選択する]** をクリックしてから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-206">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="8a458-207">場所の一覧で、 **Exchange メール**と **OneDrive アカウント**の場所を無効にし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-207">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="8a458-208">**[保護する機密性の高い情報の種類をカスタマイズする]** ウィンドウで、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-208">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="8a458-209">**[保護するコンテンツの種類を選択する]** ウィンドウのドロップダウン ボックスで **[追加]** をクリックしてから、 **[ラベル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-209">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="8a458-210">**[ラベル]** ウィンドウで、 **[+ 追加]** をクリックして、 **[機密]** ラベルを選択し、 **[追加]** をクリックしてから、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-210">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="8a458-211">**[保護するコンテンツの種類を選択する]** ウィンドウで、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-211">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="8a458-212">**[保護する機密性の高い情報の種類をカスタマイズする]** ウィンドウで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-212">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="8a458-213">**[機密性の高い情報が検出された場合に実行する操作]** ウィンドウで、 **[ヒントと電子メールをカスタマイズする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-213">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="8a458-214">**[ポリシー ヒントと電子メール通知をカスタマイズする]** ウィンドウで、 **[ポリシー ヒント テキストをカスタマイズする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-214">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="8a458-215">次の内容をテキスト ボックスに入力するか、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="8a458-215">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="8a458-p104">組織外のユーザーと共有するには、ファイルをダウンロードしてから開きます。[ファイル]、[文書の保護]、[パスワードを使用して暗号化] の順にクリックし、強力なパスワードを指定します。別の電子メールまたはその他の通信手段でパスワードを送信します。</span><span class="sxs-lookup"><span data-stu-id="8a458-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="8a458-219">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="8a458-220">**[機密性の高い情報が検出された場合に実行する操作]** ウィンドウで、 **[ユーザーが共有できないようにし、共有コンテンツへのアクセスを制限する]** チェックボックスをクリアしてから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-220">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="8a458-221">**[ポリシーを有効にしますか、または最初にテストしますか?]** ウィンドウで、 **[すぐ有効にします]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="8a458-222">**[設定の確認]** ウィンドウで、 **[作成]** をクリックしてから **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
### <a name="campaign-strategy-team-site"></a><span data-ttu-id="8a458-223">キャンペーン戦略チーム サイト</span><span class="sxs-lookup"><span data-stu-id="8a458-223">Campaign strategy team site</span></span>

<span data-ttu-id="8a458-224">キャンペーン戦略リソース用に機密性の高いレベルで分離された SharePoint Online チーム サイトを作成するには、以下のことを行います。</span><span class="sxs-lookup"><span data-stu-id="8a458-224">To create an isolated SharePoint Online team site at the highly confidential level for campaign strategy resources, do the following:</span></span>
  
1. <span data-ttu-id="8a458-225">必要な場合、ローカル コンピューター上のブラウザーを使用し、グローバル管理者アカウントを使用して、Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="8a458-225">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="8a458-226">タイルのリストで、 **[SharePoint]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-226">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="8a458-227">ブラウザーの新しい **[SharePoint]** タブで、 **[+ サイトの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-227">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="8a458-228">**[サイトの作成]** ページで、 **[チーム サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-228">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="8a458-229">**チームのサイト名****キャンペーンの戦略**を入力します。</span><span class="sxs-lookup"><span data-stu-id="8a458-229">In **Team site name**, type **Campaign strategy**.</span></span>
    
6. <span data-ttu-id="8a458-230">**チーム サイトの説明**では、**キャンペーンの計画 (極秘) の SharePoint サイト**を入力します。</span><span class="sxs-lookup"><span data-stu-id="8a458-230">In **Team site description**, type **SharePoint site for campaign strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="8a458-231">**[プライバシー設定]** で、 **[プライベート - メンバーのみがこのサイトにアクセス可能**」を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-231">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="8a458-232">**[誰を追加しますか]** ウィンドウで、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-232">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="8a458-233">ツール ・ バーで、ブラウザーで新規の**キャンペーン計画**] タブの設定アイコンをクリックして**サイトのアクセス許可**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-233">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="8a458-234">**[サイトの権限]** ウィンドウで、 **[高度な権限の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-234">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="8a458-235">ブラウザーの新しい **[アクセス許可]** タブで、 **[アクセス要求の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-235">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="8a458-236">**[アクセス要求の設定]** ダイアログ ボックスの **[サイトと個別のファイルおよびフォルダーの共有をメンバーに許可します]** と **[メンバーが、他のユーザーをサイト メンバー グループに招待することを許可します]** をクリアし (これによって、3 つのチェック ボックスがすべてクリアされる)、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-236">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="8a458-237">**キャンペーン計画のメンバー**リストをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-237">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="8a458-238">**[ユーザーとグループ]** ページで、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-238">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="8a458-239">[**共有**] ダイアログ ボックスで**シニアと戦略的なスタッフ**を入力して、選択し、し、[**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-239">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="8a458-240">**キャンペーン計画の所有者**を一覧でクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-240">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="8a458-241">**[ユーザーとグループ]** ページで、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-241">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="8a458-242">**[共有]** ダイアログ ボックスに「 **IT スタッフ**」と入力し、それを選択して、 **[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-242">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="8a458-243">ブラウザーの戻るボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-243">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="8a458-244">お使いのブラウザーで [**ユーザーとグループ**] タブを閉じてお使いのブラウザーでは、**キャンペーンの戦略ホーム**] タブをクリックし、**サイトのアクセス許可**] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="8a458-244">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="8a458-245">権限を構成した結果を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="8a458-245">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="8a458-246">**キャンペーン戦略のメンバー** SharePoint グループには、**シニアとスタッフの戦略的な**グループのみ (これは、候補者、ChiefOfStaff、および Strategic1 のユーザー アカウントのみが含まれています) と、**キャンペーンの戦略**(を含むグループが含まれています。グローバル管理者ユーザー アカウントのみ)。</span><span class="sxs-lookup"><span data-stu-id="8a458-246">The **Campaign strategy-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains only the Candidate, ChiefOfStaff, and Strategic1 user accounts) and the **Campaign strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="8a458-247">**キャンペーン戦略の所有者**SharePoint グループには、 **IT スタッフ**グループ (これは ITAdmin1 と ITAdmin2 のユーザー アカウントのみが含まれています) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8a458-247">The **Campaign strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="8a458-248">**キャンペーン戦略の閲覧者**の SharePoint グループが含まれていますないグループまたはユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="8a458-248">The **Campaign strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="8a458-249">メンバーは、(これのみ実行できます**キャンペーン戦略-Owners**グループのメンバーによって) サイト ・ レベルのアクセス許可を変更できません。</span><span class="sxs-lookup"><span data-stu-id="8a458-249">Members cannot modify site-level permissions (this can only be done by members of the **Campaign strategy-Owners** group).</span></span>
    
- <span data-ttu-id="8a458-p105">他のユーザー アカウントは、サイトまたはそのリソースにアクセスまたはサイトへのアクセスを要求できません。グローバル管理者によって、または**キャンペーンの戦略-Owners**グループのメンバーでは、サイトに追加のアクセス許可を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a458-p105">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Campaign strategy-Owners** group.</span></span>
    
<span data-ttu-id="8a458-252">次に、キャンペーン戦略チーム サイトのドキュメント フォルダーを [高機密] ラベル用に構成します。</span><span class="sxs-lookup"><span data-stu-id="8a458-252">Next, configure the documents folder of the Campaign strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="8a458-253">**戦略ホームのキャンペーン**お使いのブラウザーのタブ、[**ドキュメント**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-253">In the **Campaign strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="8a458-254">[設定] アイコンをクリックしてから、 **[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-254">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="8a458-255">**[権限と管理]** をクリックして、 **[このライブラリ内の項目にラベルを適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-255">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="8a458-256">**[設定 - ラベルの適用]** で **[高機密]** をクリックし、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-256">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="8a458-p106">次に、ポリシーを構成する DLP ブロックのユーザーが組織外の機密度の高いラベルを持つチームの SharePoint Online サイト上のドキュメントを共有する場合。この DLP ポリシーは、キャンペーンの戦略サイト内のリソースに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8a458-p106">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label outside the organization. This DLP policy will apply to resources in the Campaign strategy site.</span></span>
  
1. <span data-ttu-id="8a458-259">必要な場合は、ブラウザーを使用して、ローカル コンピューターにし、セキュリティ管理者または企業の管理者の役割を持つアカウントを使用して Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="8a458-259">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="8a458-260">お使いのブラウザーで [ **Microsoft Office のホーム**] タブをクリックして、**セキュリティ&amp;準拠**を並べて表示します。</span><span class="sxs-lookup"><span data-stu-id="8a458-260">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="8a458-261">新しい**セキュリティ&amp;準拠**お使いのブラウザーのタブをクリックして**データ損失防止 > ポリシー**。</span><span class="sxs-lookup"><span data-stu-id="8a458-261">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="8a458-262">**[データ損失防止]** ウィンドウで、 **[+ ポリシーの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-262">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="8a458-263">**[テンプレートを使って開始するか、カスタム ポリシーを作成する]** ウィンドウで、 **[カスタム]** をクリックしてから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-263">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="8a458-264">**[ポリシーに名前をつける]** ウィンドウで、 **[名前]** に「 **高機密ラベル SharePoint Online チーム サイト**」と入力してから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-264">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="8a458-265">**[場所の選択]** ウィンドウで、 **[自分で特定の場所を選択する]** をクリックしてから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-265">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="8a458-266">場所の一覧で、 **Exchange メール**と **OneDrive アカウント**の場所を無効にし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-266">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="8a458-267">**[保護する機密性の高い情報の種類をカスタマイズする]** ウィンドウで、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-267">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="8a458-268">**[保護するコンテンツの種類を選択する]** ウィンドウのドロップダウン ボックスで **[追加]** をクリックしてから、 **[ラベル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-268">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="8a458-269">**[ラベル]** ウィンドウで、 **[+ 追加]** をクリックして、 **[高機密]** ラベルを選択し、 **[追加]** をクリックしてから、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-269">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="8a458-270">**[保護するコンテンツの種類を選択する]** ウィンドウで、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-270">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="8a458-271">**[保護する機密性の高い情報の種類をカスタマイズする]** ウィンドウで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-271">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="8a458-272">**[機密性の高い情報が検出された場合に実行する操作]** ウィンドウで、 **[ヒントと電子メールをカスタマイズする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-272">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="8a458-273">**[ポリシー ヒントと電子メール通知をカスタマイズする]** ウィンドウで、 **[ポリシー ヒント テキストをカスタマイズする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-273">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="8a458-274">次の内容をテキスト ボックスに入力するか、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="8a458-274">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="8a458-p107">組織外のユーザーと共有するには、ファイルをダウンロードしてから開きます。[ファイル]、[文書の保護]、[パスワードを使用して暗号化] の順にクリックし、強力なパスワードを指定します。別の電子メールまたはその他の通信手段でパスワードを送信します。</span><span class="sxs-lookup"><span data-stu-id="8a458-p107">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="8a458-278">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-278">Click **OK**.</span></span>
    
18. <span data-ttu-id="8a458-279">**[機密性の高い情報が検出された場合に実行する操作]** ウィンドウで、 **[業務の妥当性を要求してオーバーライドする]** をクリックしてから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-279">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="8a458-280">**[ポリシーを有効にしますか、または最初にテストしますか?]** ウィンドウで、 **[すぐ有効にします]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-280">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="8a458-281">**[設定の確認]** ウィンドウで、 **[作成]** をクリックしてから **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-281">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="8a458-282">[Office 365 の管理センターでの Azure RMS のライセンス認証](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a458-282">Use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="8a458-283">次に、以下の手順に従い、保護とアクセス許可用の新しいスコープ付きポリシーとサブラベルを使用して、Azure Information Protection を構成します。</span><span class="sxs-lookup"><span data-stu-id="8a458-283">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="8a458-p108">セキュリティ管理者または会社管理者のロールのアカウントを使用して、Office 365 ポータルにサインインします。ヘルプを表示するには、「[Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a458-p108">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="8a458-286">ブラウザーで別のタブで、[https://portal.azure.com](https://portal.azure.com) の Azure Portal に移動します。</span><span class="sxs-lookup"><span data-stu-id="8a458-286">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="8a458-287">初めて Azure Information Protection を構成する場合は、これらの[手順](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a458-287">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="8a458-288">リスト ウィンドウで、 **[その他のサービス]** をクリックして、「 **information**」と入力し、 **[Azure Information Protection]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-288">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="8a458-289">**[Azure Information Protection]** ブレードで、 **[スコープ付きポリシー] > [+ 新しいポリシーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-289">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="8a458-290">**ポリシーの名前**と**説明**で**、キャンペーンの戦略チームのサイト内のドキュメントのラベル**の**CampaignStrategy**を入力します。</span><span class="sxs-lookup"><span data-stu-id="8a458-290">Type **CampaignStrategy** in **Policy name** and **Label for documents in the Campaign strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="8a458-291">をクリックして**このポリシーを取得するユーザーまたはグループを選択 > ユーザー/グループの**、**シニアとスタッフの戦略的な**選択です。</span><span class="sxs-lookup"><span data-stu-id="8a458-291">Click **Select which users or groups get this policy > User/Groups**, and then select **Senior and strategic staff**.</span></span>
    
8. <span data-ttu-id="8a458-292">**[選択] > [OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-292">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="8a458-293">**[非常に機密性の高い社外秘]** ラベルの場合は、省略記号 (...) をクリックしてから、 **[サブラベルの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-293">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="8a458-294">**[名前]** にサブラベルの名前、 **[説明]** にラベルの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="8a458-294">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="8a458-295">**[このラベルを含むドキュメントやメールに対するアクセス許可の設定]** で、 **[保護]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-295">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="8a458-296">**[保護]** セクションで、 **[Azure (クラウド キー)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-296">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="8a458-297">**[保護]** ブレードの **[保護の設定]** をクリックして **[+ アクセス許可を追加する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-297">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="8a458-298">**[アクセス許可を追加する]** ブレードの **[ユーザーとグループの指定]** で、 **[+ ディレクトリを参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-298">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="8a458-299">**AAD のユーザーおよびグループ**のペイン**シニアと戦略的なスタッフ**を選択し、**選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-299">On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="8a458-300">**[プリセットからアクセス許可を選択]** で、 **[印刷]**、 **[コンテンツのコピーと抽出]**、および **[転送]** チェック ボックスをクリアします。</span><span class="sxs-lookup"><span data-stu-id="8a458-300">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="8a458-301">[ **OK**] を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-301">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="8a458-302">**[サブラベル]** ブレードで、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-302">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="8a458-303">新しいスコープ付きポリシー ブレードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="8a458-303">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="8a458-304">**[Azure Information Protection - スコープ付きポリシー]** ブレードで、 **[発行]** をクリックしてから、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a458-304">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="8a458-305">これら 4 つのサイトでドキュメントの作成を開始し、試用版サブスクリプションでさまざまなユーザー アカウントを使用して、それらへのアクセスをテストする準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="8a458-305">You are now ready to begin creating documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span> 
  
<span data-ttu-id="8a458-306">Azure の情報の保護と、この新しいラベル文書を保護するには、 [Azure の情報保護クライアントのインストール](https://docs.microsoft.com/information-protection/rms-client/install-client-app)をテスト コンピューターで行う必要があります、Office 365 ポータルから Office をインストールするサイン インし、Microsoft Word から、**にアカウントを持つシニアとスタッフの戦略的な**の試用版サブスクリプションのグループです。</span><span class="sxs-lookup"><span data-stu-id="8a458-306">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8a458-307">See Also</span><span class="sxs-lookup"><span data-stu-id="8a458-307">See Also</span></span>

[<span data-ttu-id="8a458-308">選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス</span><span class="sxs-lookup"><span data-stu-id="8a458-308">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="8a458-309">選挙運動の開発/テスト環境用にグループとユーザーを構成する</span><span class="sxs-lookup"><span data-stu-id="8a458-309">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="8a458-310">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="8a458-310">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="8a458-311">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="8a458-311">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




