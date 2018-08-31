---
title: 選挙運動用の開発/テスト環境でチーム サイトを作成する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/21/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.custom: ''
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: '概要: 選挙運動用の開発/テスト環境で、パブリック、プライベート、機密、および高機密の SharePoint Online チーム サイトを作成します。'
ms.openlocfilehash: 03e73a540d1a92d20446d8e12066df87bd179293
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915262"
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a><span data-ttu-id="d6110-103">選挙運動用の開発/テスト環境でチーム サイトを作成する</span><span class="sxs-lookup"><span data-stu-id="d6110-103">Create team sites in a political campaign dev/test environment</span></span>

 <span data-ttu-id="d6110-104">**概要:** 選挙運動用の開発/テスト環境で、パブリック、プライベート、機密、および高機密の SharePoint Online チーム サイトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d6110-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in your political campaign dev/test environment.</span></span> 
  
<span data-ttu-id="d6110-p101">この記事に示した手順を使用して、「[選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)」のソリューションに対応した 4 種類の SharePoint Online チーム サイトを含む開発/テスト環境を作成してください。これらのサイトについての詳細は、トピック 10 のタイトル「**SharePoint および OneDrive for Business**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6110-p101">Use the instructions in this article to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. These sites are described in detail on Topic 10, titled **SharePoint and OneDrive for Business**.</span></span>
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a><span data-ttu-id="d6110-107">フェーズ 1: 選挙運動用の開発/テスト環境を作成する</span><span class="sxs-lookup"><span data-stu-id="d6110-107">Phase 1: Create your political campaign dev/test environment</span></span>

<span data-ttu-id="d6110-108">最初に、「[選挙運動の開発/テスト環境用にグループとユーザーを構成する](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)」の手順に従って、サブスクリプション、ユーザー、およびグループを作成します。</span><span class="sxs-lookup"><span data-stu-id="d6110-108">First, follow the instructions in [Configure groups and users for a political campaign dev/test environment](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) to create your subscriptions, users, and groups.</span></span>
  
## <a name="phase-2-create-office-365-labels"></a><span data-ttu-id="d6110-109">フェーズ 2: Office 365 のラベルを作成する</span><span class="sxs-lookup"><span data-stu-id="d6110-109">Phase 2: Create Office 365 labels</span></span>

<span data-ttu-id="d6110-110">このフェーズでは、SharePoint Online チーム サイトのドキュメント フォルダーに対してさまざまなセキュリティ レベルのラベルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d6110-110">In this phase, you create the labels for the different levels of security for SharePoint Online team site document folders.</span></span>
  
1. <span data-ttu-id="d6110-p102">必要に応じて、Office 365 ポータルに、試用版サブスクリプション用の全体管理者アカウントの資格情報でサインインします。ヘルプについては、「[一般法人向け Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6110-p102">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d6110-113">**[Microsoft Office Home]** タブで、**[管理者]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-113">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="d6110-114">ブラウザーの新しい **[Office 管理者センター]** タブで、**[管理センター] > [セキュリティとコンプライアンス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-114">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="d6110-115">ブラウザーの新しい **[ホーム – セキュリティとコンプライアンス]** タブをクリックして、**[分類] > [ラベル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-115">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="d6110-116">**[ホーム] > [ラベル]** ウィンドウで、**[ラベルの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-116">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="d6110-117">**[ラベルに名前をつける]** ウィンドウで、「**内部**」と入力してから、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-117">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="d6110-118">**[ラベル設定]** ウィンドウで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-118">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="d6110-119">**[設定の確認]** ウィンドウで、 **[このラベルを作成する]** をクリックしてから **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-119">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="d6110-120">次の追加ラベルについて手順 5 から 8 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="d6110-120">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="d6110-121">Kirkland</span><span class="sxs-lookup"><span data-stu-id="d6110-121">Private</span></span>
    
  - <span data-ttu-id="d6110-122">機密</span><span class="sxs-lookup"><span data-stu-id="d6110-122">Sensitive</span></span>
    
  - <span data-ttu-id="d6110-123">非常に機密性の高い社外秘</span><span class="sxs-lookup"><span data-stu-id="d6110-123">Highly Confidential</span></span>
    
10. <span data-ttu-id="d6110-124">**[ホーム]、[ラベル]** ウィンドウで、**[Publish labels]\(ラベルの発行\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-124">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="d6110-125">**[発行するラベルを選択]** ウィンドウで、 **[発行するラベルを選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-125">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="d6110-126">**[Choose labels]\(ラベルの選択\)** ウィンドウで、**[追加]** をクリックして 4 つのラベルをすべて選択します。</span><span class="sxs-lookup"><span data-stu-id="d6110-126">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="d6110-127">[ **完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-127">Click **Done**.</span></span>
    
14. <span data-ttu-id="d6110-128">**[発行するラベルを選択]** ウィンドウで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-128">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="d6110-129">**[場所の選択]** ウィンドウで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-129">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="d6110-130">**[ポリシーに名前をつける]** ウィンドウで、**[名前]** に「**キャンペーン**」と入力して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-130">On the **Name your policy** pane, type **Campaign** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="d6110-131">**[設定の確認]** ウィンドウで、**[ラベルの発行]** をクリックして、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-131">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="d6110-132">フェーズ 3:SharePoint Online チーム サイトを作成する</span><span class="sxs-lookup"><span data-stu-id="d6110-132">Phase 3: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="d6110-133">このフェーズでは、SharePoint Online チーム サイトを作成し、4 つのタイプの SharePoint Online チーム サイトに対応する選挙運動用に構成します。</span><span class="sxs-lookup"><span data-stu-id="d6110-133">In this phase, you create and configure SharePoint Online team sites for your political campaign corresponding to the four types of SharePoint Online team sites.</span></span>
  
### <a name="campaign-wide-team-site"></a><span data-ttu-id="d6110-134">キャンペーン全体のチーム サイト</span><span class="sxs-lookup"><span data-stu-id="d6110-134">Campaign wide team site</span></span>

<span data-ttu-id="d6110-135">ベースラインのパブリック SharePoint Online チーム サイトを作成するには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="d6110-135">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="d6110-136">必要な場合は、ローカル コンピューターのブラウザーを使用して、全体管理者アカウントで Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="d6110-136">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="d6110-137">タイルのリストで、**[SharePoint]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-137">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="d6110-138">ブラウザーの新しい **SharePoint** タブで、**[+ サイトの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-138">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="d6110-139">**[サイトの作成]** ページで、**[チーム サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-139">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="d6110-140">**[サイト名]** に、「**キャンペーン全体**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d6110-140">In **Site name**, type **Campaign wide**.</span></span> 
    
6. <span data-ttu-id="d6110-141">**[チーム サイトの説明]** に、「**キャンペーン全体の SharePoint サイト**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d6110-141">In **Team site description**, type **SharePoint site for the entire campaign**.</span></span>
    
7. <span data-ttu-id="d6110-142">**[プライバシー設定]** で、**[パブリック - 組織の全ユーザーがこのサイトにアクセス可能]** を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-142">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d6110-143">**[誰を追加しますか]** ウィンドウで、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-143">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="d6110-144">次に、キャンペーン全体のチーム サイトのドキュメント フォルダーを [内部] ラベル用に構成します。</span><span class="sxs-lookup"><span data-stu-id="d6110-144">Next, configure the documents folder of the Campaign wide team site for the Internal label.</span></span>
  
1. <span data-ttu-id="d6110-145">ブラウザーの **[キャンペーン全体 – ホーム]** タブをクリックして、**[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-145">In the **Campaign wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="d6110-146">[設定] アイコンをクリックしてから、**[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-146">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="d6110-147">**[権限と管理]** をクリックして、**[このライブラリ内の項目にラベルを適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-147">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="d6110-148">**[設定 - ラベルの適用]** で **[内部]** をクリックし、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-148">In **Settings-Apply Label**, select **Internal**, and then click **Save**.</span></span>
    
### <a name="campaign-project-1-team-site"></a><span data-ttu-id="d6110-149">キャンペーン プロジェクト 1 のチーム サイト</span><span class="sxs-lookup"><span data-stu-id="d6110-149">Campaign project 1 team site</span></span>

<span data-ttu-id="d6110-150">キャンペーン内のプロジェクト用にベースラインのプライベート SharePoint Online チーム サイトを作成するには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="d6110-150">To create a baseline private SharePoint Online team site for a project within the campaign, do the following:</span></span>
  
1. <span data-ttu-id="d6110-151">必要な場合は、ローカル コンピューターのブラウザーを使用して、全体管理者アカウントで Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="d6110-151">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="d6110-152">タイルのリストで、**[SharePoint]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-152">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="d6110-153">ブラウザーの新しい **SharePoint** タブで、**[+ サイトの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-153">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="d6110-154">**[サイトの作成]** ページで、**[チーム サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-154">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="d6110-155">**[サイト名]** に、「**キャンペーン プロジェクト 1**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d6110-155">In **Site name**, type **Campaign project 1**.</span></span> 
    
6. <span data-ttu-id="d6110-156">**[チーム サイトの説明]** に、「**キャンペーン プロジェクト 1 の SharePoint サイト**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d6110-156">In **Team site description,** type **SharePoint site for Campaign project 1**.</span></span>
    
7. <span data-ttu-id="d6110-157">**[プライバシー設定]** で、**[プライベート - メンバーのみがこのサイトにアクセス可能**」を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-157">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d6110-158">**[誰を追加しますか]** ウィンドウで、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-158">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="d6110-159">次に、キャンペーン プロジェクト 1 チーム サイトのドキュメント フォルダーを [プライベート] ラベル用に構成します。</span><span class="sxs-lookup"><span data-stu-id="d6110-159">Next, configure the documents folder of the Campaign project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="d6110-160">ブラウザーの **[キャンペーン プロジェクト 1 – ホーム]** タブをクリックして、**[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-160">In the **Campaign project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="d6110-161">[設定] アイコンをクリックしてから、**[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-161">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="d6110-162">**[権限と管理]** をクリックして、 **[このライブラリ内の項目にラベルを適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-162">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="d6110-163">**[設定 - ラベルの適用]** で **[プライベート]** をクリックし、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-163">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
### <a name="campaign-marketing-team-site"></a><span data-ttu-id="d6110-164">キャンペーン マーケティング チーム サイト</span><span class="sxs-lookup"><span data-stu-id="d6110-164">Campaign marketing team site</span></span>

<span data-ttu-id="d6110-165">キャンペーン マーケティング リソース用の機密レベルの分離した SharePoint Online チーム サイトを作成するには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="d6110-165">To create a sensitive-level isolated SharePoint Online team site for campaign marketing resources, do the following:</span></span>
  
1. <span data-ttu-id="d6110-166">ローカル コンピューターのブラウザーを使用して、全体管理者アカウントで Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="d6110-166">Using a browser on your local computer, sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="d6110-167">タイルのリストで、**[SharePoint]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-167">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="d6110-168">ブラウザーの新しい **SharePoint** タブで、**[+ サイトの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-168">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="d6110-169">**[サイトの作成]** ページで、**[チーム サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-169">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="d6110-170">**[チーム サイト名]** に、「**キャンペーン マーケティング**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d6110-170">In **Team site name**, type **Campaign marketing**.</span></span>
    
6. <span data-ttu-id="d6110-171">**[チーム サイトの説明]** に、「**キャンペーン マーケティングの SharePoint サイト (機密)**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d6110-171">In **Team site description**, type **SharePoint site for campaign marketing (sensitive)**.</span></span>
    
7.  <span data-ttu-id="d6110-172">**[プライバシー設定]** で、**[プライベート - メンバーのみがこのサイトにアクセス可能**」を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-172">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d6110-173">**[誰を追加しますか]** ウィンドウで、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-173">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="d6110-174">ブラウザーの新しい **[キャンペーン マーケティング]** タブのツール バーで、設定アイコンをクリックし、**[サイトのアクセス許可]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-174">On the new **Campaign marketing** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="d6110-175">**[サイトの権限]** ウィンドウで、**[高度な権限の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-175">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="d6110-176">ブラウザーの新しい **[アクセス許可]** タブで、 **[アクセス要求の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-176">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="d6110-177">**[アクセス要求の設定]** ダイアログ ボックスで、**[サイトと個別のファイルおよびフォルダーの共有をメンバーに許可します]** および **[メンバーが、他のユーザーをサイト メンバー グループに招待することを許可します]** チェック ボックスをクリアし、**[すべてのアクセス要求を送信する]** に「**ITAdmin1@**<your organization name> **.onmicrosoft.com**」と入力し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-177">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**<your organization name> **.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="d6110-178">一覧にある **[キャンペーン マーケティング メンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-178">Click **Campaign marketing Members** in the list.</span></span>
    
14. <span data-ttu-id="d6110-179">**[ユーザーとグループ]** ページで、**[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-179">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="d6110-180">**[共有]** ダイアログ ボックスに「**戦略的シニア スタッフ**」と入力し、それを選択して、**[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-180">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="d6110-181">**[分析スタッフ]** グループおよび **Regular1** ユーザー アカウントで手順 14 と 15 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="d6110-181">Repeat steps 14 and 15 for the **Analytics staff** group and the **Regular1** user account.</span></span>
    
17. <span data-ttu-id="d6110-182">ブラウザーの戻るボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-182">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="d6110-183">一覧にある **[キャンペーン マーケティングの所有者]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-183">Click **Campaign marketing Owners** in the list.</span></span>
    
19. <span data-ttu-id="d6110-184">**[ユーザーとグループ]** ページで、**[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-184">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="d6110-185">**[共有]** ダイアログ ボックスに「 **IT スタッフ**」と入力し、それを選択して、 **[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-185">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="d6110-186">ブラウザーの戻るボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-186">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="d6110-187">ブラウザーの **[ユーザーとグループ]** タブを閉じ、ブラウザーの **[キャンペーン マーケティング - ホーム]** タブをクリックし、**[サイトのアクセス許可]** ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d6110-187">Close the **People and Groups** tab in your browser, click the **Campaign marketing-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="d6110-188">権限を構成した結果を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="d6110-188">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="d6110-189">**[キャンペーン マーケティング - メンバー]** SharePoint グループには、**[戦略的シニア スタッフ]** グループ (Candidate、ChiefOfStaff、および Strategic1 ユーザー アカウントを含む)、**[キャンペーン マーケティング]** グループ (グローバル管理者ユーザー アカウントを含む)、**[分析スタッフ]** グループ (DataScientist1 ユーザー アカウントを含む)、および **Regular1** ユーザー アカウントのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d6110-189">The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.</span></span>
    
- <span data-ttu-id="d6110-190">**[キャンペーン マーケティング - 所有者]** SharePoint グループには、**[IT スタッフ]** グループ (ITAdmin1 と ITAdmin2 ユーザー アカウントのみを含む) のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d6110-190">The **Campaign marketing-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="d6110-191">**[マーケティング キャンペーン - 閲覧者]** SharePoint グループには、グループまたはユーザー アカウントは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="d6110-191">The **Campaign marketing-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="d6110-192">メンバーはサイト レベルのアクセス許可を変更できません (これを実行できるのは、**[キャンペーン マーケティング- 所有者]** グループのメンバーだけです)。</span><span class="sxs-lookup"><span data-stu-id="d6110-192">Members cannot modify site-level permissions (this can only be done by members of the **Campaign marketing-Owners** group).</span></span>
    
- <span data-ttu-id="d6110-193">他のユーザー アカウントは、サイトやそのリソースにアクセスできませんが、サイトへのアクセスを要求することができます。これにより、ITAdmin1 ユーザー アカウントのメールボックスに電子メールが送信されます。</span><span class="sxs-lookup"><span data-stu-id="d6110-193">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="d6110-194">次に、キャンペーン マーケティング チーム サイトのドキュメント フォルダーを [機密] ラベル用に構成します。</span><span class="sxs-lookup"><span data-stu-id="d6110-194">Next, configure the documents folder of the Campaign marketing team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="d6110-195">ブラウザーの **[キャンペーン マーケティング - ホーム]** タブをクリックして、**[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-195">In the **Campaign marketing-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="d6110-196">[設定] アイコンをクリックしてから、**[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-196">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="d6110-197">**[権限と管理]** をクリックして、 **[このライブラリ内の項目にラベルを適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-197">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="d6110-198">**[設定 - ラベルの適用]** で **[機密]** をクリックし、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-198">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="d6110-p103">次に、機密ラベルの付いた SharePoint Online チーム サイト上のドキュメントを組織の外部と共有しようとしているユーザーに通知するデータ損失防止 (DLP) ポリシーを構成します。この DLP ポリシーは、キャンペーン マーケティング サイトのリソースに適用します。</span><span class="sxs-lookup"><span data-stu-id="d6110-p103">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label outside the organization. This DLP policy will apply to resources in the Campaign marketing site.</span></span>
  
1. <span data-ttu-id="d6110-201">ブラウザーの **[Microsoft Office Home]** タブで、**[セキュリティとコンプライアンス]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-201">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="d6110-202">ブラウザーの新しい **[セキュリティとコンプライアンス]** タブで、**[データ損失防止] > [ポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-202">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="d6110-203">**[データ損失防止]** ウィンドウで、 **[+ ポリシーの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-203">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="d6110-204">**[テンプレートを使って開始するか、カスタム ポリシーを作成する]** ウィンドウで、 **[カスタム]** をクリックしてから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-204">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="d6110-205">**[ポリシーに名前をつける]** ウィンドウで、 **[名前]** に「 **機密ラベル SharePoint Online チーム サイト**」と入力してから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-205">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="d6110-206">**[場所の選択]** ウィンドウで、 **[自分で特定の場所を選択する]** をクリックしてから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-206">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="d6110-207">場所の一覧で、 **Exchange メール**と **OneDrive アカウント**の場所を無効にし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-207">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d6110-208">**[保護する機密性の高い情報の種類をカスタマイズする]** ウィンドウで、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-208">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="d6110-209">**[保護するコンテンツの種類を選択する]** ウィンドウのドロップダウン ボックスで **[追加]** をクリックしてから、 **[ラベル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-209">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="d6110-210">**[ラベル]** ウィンドウで、 **[+ 追加]** をクリックして、 **[機密]** ラベルを選択し、 **[追加]** をクリックしてから、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-210">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="d6110-211">**[保護するコンテンツの種類を選択する]** ウィンドウで、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-211">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="d6110-212">**[Customize the types of sensitive info you want to protect]\(保護する機密情報の種類のカスタマイズ\)** ウィンドウで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-212">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="d6110-213">**[What do you want to do if we detect sensitive info?]\(機密情報が検出された場合の処理\)** ウィンドウで、**[Customize the tip and email]\(ヒントと電子メールをカスタマイズする)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-213">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="d6110-214">**[Customize policy tips and email notifications]\(ポリシー ヒントと電子メール通知のカスタマイズ\)** ウィンドウで、**[Customize the policy tip text]\(ポリシー ヒントのテキストをカスタマイズする\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-214">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="d6110-215">次の内容をテキスト ボックスに入力するか、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="d6110-215">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="d6110-p104">組織外のユーザーと共有するには、ファイルをダウンロードしてから開きます。[ファイル]、[文書の保護]、[パスワードを使用して暗号化] の順にクリックし、強力なパスワードを指定します。別の電子メールまたはその他の通信手段でパスワードを送信します。</span><span class="sxs-lookup"><span data-stu-id="d6110-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="d6110-219">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="d6110-220">**[機密性の高い情報が検出された場合に実行する操作]** ウィンドウで、 **[ユーザーが共有できないようにし、共有コンテンツへのアクセスを制限する]** チェックボックスをクリアしてから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-220">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="d6110-221">**[ポリシーを有効にしますか、または最初にテストしますか?]** ウィンドウで、 **[すぐ有効にします]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="d6110-222">**[設定の確認]** ウィンドウで、**[作成]** をクリックして、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
### <a name="campaign-strategy-team-site"></a><span data-ttu-id="d6110-223">キャンペーン戦略チーム サイト</span><span class="sxs-lookup"><span data-stu-id="d6110-223">Campaign strategy team site</span></span>

<span data-ttu-id="d6110-224">キャンペーン戦略リソース用に機密性の高いレベルで分離された SharePoint Online チーム サイトを作成するには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="d6110-224">To create an isolated SharePoint Online team site at the highly confidential level for campaign strategy resources, do the following:</span></span>
  
1. <span data-ttu-id="d6110-225">必要な場合は、ローカル コンピューターのブラウザーを使用して、全体管理者アカウントで Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="d6110-225">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="d6110-226">タイルのリストで、**[SharePoint]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-226">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="d6110-227">ブラウザーの新しい **SharePoint** タブで、**[+ サイトの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-227">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="d6110-228">**[サイトの作成]** ページで、**[チーム サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-228">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="d6110-229">**[チーム サイト名]** に、「**キャンペーン戦略**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d6110-229">In **Team site name**, type **Campaign strategy**.</span></span>
    
6. <span data-ttu-id="d6110-230">**[チーム サイトの説明]** に、「**キャンペーン戦略の SharePoint サイト (高機密)**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d6110-230">In **Team site description**, type **SharePoint site for campaign strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="d6110-231">**[プライバシー設定]** で、**[プライベート - メンバーのみがこのサイトにアクセス可能**」を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-231">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d6110-232">**[誰を追加しますか]** ウィンドウで、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-232">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="d6110-233">ブラウザーの新しい **[キャンペーン戦略]** タブのツール バーで、設定アイコンをクリックし、**[サイトのアクセス許可]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-233">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="d6110-234">**[サイトの権限]** ウィンドウで、**[高度な権限の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-234">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="d6110-235">ブラウザーの新しい **[アクセス許可]** タブで、 **[アクセス要求の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-235">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="d6110-236">**[アクセス要求の設定]** ダイアログ ボックスの **[サイトと個別のファイルおよびフォルダーの共有をメンバーに許可します]** と **[メンバーが、他のユーザーをサイト メンバー グループに招待することを許可します]** をクリアし (これによって、3 つのチェック ボックスがすべてクリアされる)、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-236">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="d6110-237">一覧にある **[キャンペーン戦略のメンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-237">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="d6110-238">**[ユーザーとグループ]** ページで、**[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-238">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="d6110-239">**[共有]** ダイアログ ボックスに「**戦略的シニア スタッフ**」と入力し、それを選択して、**[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-239">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="d6110-240">一覧にある **[キャンペーン戦略の所有者]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-240">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="d6110-241">**[ユーザーとグループ]** ページで、**[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-241">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="d6110-242">**[共有]** ダイアログ ボックスに「 **IT スタッフ**」と入力し、それを選択して、 **[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-242">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="d6110-243">ブラウザーの戻るボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-243">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="d6110-244">ブラウザーの **[ユーザーとグループ]** タブを閉じ、ブラウザーの **[キャンペーン戦略 - ホーム]** タブをクリックし、**[サイトのアクセス許可]** ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d6110-244">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="d6110-245">権限を構成した結果を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="d6110-245">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="d6110-246">**[キャンペーン戦略 - メンバー]** SharePoint グループには、**[戦略的シニア スタッフ]** グループ (Candidate、ChiefOfStaff、および Strategic1 ユーザー アカウントのみを含む)、**[キャンペーン戦略]** グループ (グローバル管理者ユーザー アカウントのみを含む) のみが含まれます。
</span><span class="sxs-lookup"><span data-stu-id="d6110-246">The **Campaign strategy-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains only the Candidate, ChiefOfStaff, and Strategic1 user accounts) and the **Campaign strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="d6110-247">**[キャンペーン戦略 - 所有者]** SharePoint グループには、**[IT スタッフ]** グループ (ITAdmin1 と ITAdmin2 ユーザー アカウントのみを含む) のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d6110-247">The **Campaign strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="d6110-248">**[キャンペーン戦略 - 閲覧者]** SharePoint グループには、グループまたはユーザー アカウントは含まれていません。	</span><span class="sxs-lookup"><span data-stu-id="d6110-248">The **Campaign strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="d6110-249">メンバーはサイト レベルのアクセス許可を変更できません (これを実行できるのは、**[キャンペーン戦略 - 所有者]** グループのメンバーだけです)。</span><span class="sxs-lookup"><span data-stu-id="d6110-249">Members cannot modify site-level permissions (this can only be done by members of the **Campaign strategy-Owners** group).</span></span>
    
- <span data-ttu-id="d6110-p105">その他のユーザー アカウントは、サイトやそのリソースにアクセスすることも、そのサイトへのアクセスを要求することもできません。サイトへの追加のアクセス許可は、グローバル管理者または **[キャンペーン戦略 - 所有者]** グループのメンバーが行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6110-p105">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Campaign strategy-Owners** group.</span></span>
    
<span data-ttu-id="d6110-252">次に、キャンペーン戦略チーム サイトのドキュメント フォルダーを [高機密] ラベル用に構成します。</span><span class="sxs-lookup"><span data-stu-id="d6110-252">Next, configure the documents folder of the Campaign strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="d6110-253">ブラウザーの **[キャンペーン戦略 - ホーム]** タブをクリックして、**[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-253">In the **Campaign strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="d6110-254">[設定] アイコンをクリックしてから、**[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-254">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="d6110-255">**[権限と管理]** をクリックして、 **[このライブラリ内の項目にラベルを適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-255">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="d6110-256">**[設定 - ラベルの適用]** で **[高機密]** をクリックし、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-256">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="d6110-p106">次に、高機密ラベルの付いた SharePoint Online チーム サイト上のドキュメントをユーザーが組織の外部と共有するのをブロックする DLP ポリシーを構成します。この PLD は、キャンペーン戦略サイトのリソースに適用します。</span><span class="sxs-lookup"><span data-stu-id="d6110-p106">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label outside the organization. This DLP policy will apply to resources in the Campaign strategy site.</span></span>
  
1. <span data-ttu-id="d6110-259">必要に応じて、ローカル コンピューターのブラウザーを使用して、セキュリティ管理者または会社管理者のロールのアカウントで、Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="d6110-259">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="d6110-260">ブラウザーの **[Microsoft Office Home]** タブで、**[セキュリティとコンプライアンス]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-260">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="d6110-261">ブラウザーの新しい **[セキュリティとコンプライアンス]** タブで、**[データ損失防止] > [ポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-261">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="d6110-262">**[データ損失防止]** ウィンドウで、 **[+ ポリシーの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-262">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="d6110-263">**[テンプレートを使って開始するか、カスタム ポリシーを作成する]** ウィンドウで、 **[カスタム]** をクリックしてから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-263">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="d6110-264">**[ポリシーに名前をつける]** ウィンドウで、 **[名前]** に「 **高機密ラベル SharePoint Online チーム サイト**」と入力してから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-264">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="d6110-265">**[場所の選択]** ウィンドウで、 **[自分で特定の場所を選択する]** をクリックしてから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-265">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d6110-266">場所の一覧で、 **Exchange メール**と **OneDrive アカウント**の場所を無効にし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-266">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="d6110-267">**[保護する機密性の高い情報の種類をカスタマイズする]** ウィンドウで、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-267">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="d6110-268">**[保護するコンテンツの種類を選択する]** ウィンドウのドロップダウン ボックスで **[追加]** をクリックしてから、 **[ラベル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-268">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="d6110-269">**[ラベル]** ウィンドウで、 **[+ 追加]** をクリックして、 **[高機密]** ラベルを選択し、 **[追加]** をクリックしてから、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-269">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="d6110-270">**[保護するコンテンツの種類を選択する]** ウィンドウで、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-270">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="d6110-271">**[Customize the types of sensitive info you want to protect]\(保護する機密情報の種類のカスタマイズ\)** ウィンドウで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-271">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="d6110-272">**[What do you want to do if we detect sensitive info?]\(機密情報が検出された場合の処理\)** ウィンドウで、**[Customize the tip and email]\(ヒントと電子メールをカスタマイズする)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-272">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="d6110-273">**[Customize policy tips and email notifications]\(ポリシー ヒントと電子メール通知のカスタマイズ\)** ウィンドウで、**[Customize the policy tip text]\(ポリシー ヒントのテキストをカスタマイズする\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-273">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="d6110-274">次の内容をテキスト ボックスに入力するか、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="d6110-274">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="d6110-p107">組織外のユーザーと共有するには、ファイルをダウンロードしてから開きます。[ファイル]、[文書の保護]、[パスワードを使用して暗号化] の順にクリックし、強力なパスワードを指定します。別の電子メールまたはその他の通信手段でパスワードを送信します。</span><span class="sxs-lookup"><span data-stu-id="d6110-p107">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="d6110-278">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-278">Click **OK**.</span></span>
    
18. <span data-ttu-id="d6110-279">**[機密性の高い情報が検出された場合に実行する操作]** ウィンドウで、 **[業務の妥当性を要求してオーバーライドする]** をクリックしてから、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-279">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="d6110-280">**[ポリシーを有効にしますか、または最初にテストしますか?]** ウィンドウで、 **[すぐ有効にします]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-280">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="d6110-281">**[設定の確認]** ウィンドウで、**[作成]** をクリックして、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-281">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="d6110-282">「[Office 365 管理センターから Azure Rights Management をアクティブ化する方法](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)」にある指示に従います。</span><span class="sxs-lookup"><span data-stu-id="d6110-282">Use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="d6110-283">次に、以下の手順に従い、保護とアクセス許可用の新しいスコープ付きポリシーとサブラベルを使用して、Azure Information Protection を構成します。</span><span class="sxs-lookup"><span data-stu-id="d6110-283">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="d6110-p108">セキュリティ管理者または会社管理者のロールのアカウントを使用して、Office 365 ポータルにサインインします。ヘルプを表示するには、「[Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6110-p108">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d6110-286">ブラウザーで別のタブを開き、Azure portal ([https://portal.azure.com](https://portal.azure.com)) に移動します。</span><span class="sxs-lookup"><span data-stu-id="d6110-286">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="d6110-287">初めて Azure Information Protection を構成する場合は、これらの[手順](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6110-287">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="d6110-288">リスト ウィンドウで、**[すべてのサービス]** をクリックして、「**information**」と入力し、**[Azure Information Protection]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-288">In the list pane, click **All services**, type **information**, and then click **Azure Information Protection**.</span></span>

5. <span data-ttu-id="d6110-289">**[ラベル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-289">Click **Labels**.</span></span>
    
6. <span data-ttu-id="d6110-290">**[非常に機密性の高い社外秘]** ラベルを右クリックしてから、**[サブラベルの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-290">Right-click the **Highly Confidential** label, and then click **Add a sub-label**.</span></span>
    
7. <span data-ttu-id="d6110-291">**[名前]** に「**CampaignStrategy**」と入力し、**[説明]** に「**キャンペーン戦略チーム サイトのドキュメントのラベル**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d6110-291">Type **CampaignStrategy** in **Name** and **Label for documents in the Campaign strategy team site** in **Description**.</span></span>
    
8. <span data-ttu-id="d6110-292">**[このラベルを含むドキュメントやメールに対するアクセス許可の設定]** で、**[保護]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-292">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
9. <span data-ttu-id="d6110-293">**[保護]** セクションで **[Azure (クラウド キー)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-293">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
10. <span data-ttu-id="d6110-294">**[保護]** ブレードで **[保護設定]** の **[+ アクセス許可の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-294">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
11. <span data-ttu-id="d6110-295">**[アクセス許可を追加する]** ブレードの **[ユーザーとグループの指定]** で、**[+ ディレクトリを参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-295">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
12. <span data-ttu-id="d6110-296">**[AAD ユーザーとグループ]** ウィンドウで、**[戦略的シニア スタッフ]** を選択し、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-296">On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.</span></span>
    
13. <span data-ttu-id="d6110-297">**[事前設定またはカスタムの設定からアクセス許可を選択する]** の **[カスタム]** をクリックし、次に **[権限の表示]**、**[コンテンツの編集]**、**[保存]**、**[返信]**、**[全員へ返信]** の各チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d6110-297">Under **Choose permissions from the preset or set custom**, click **Custom**, and then click the **View Rights**, **Edit Content**, **Save**, **Reply**, and **Reply all** check boxes.</span></span>
    
14. <span data-ttu-id="d6110-298">**[OK]** を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-298">Click **OK** twice.</span></span>
    
15. <span data-ttu-id="d6110-299">**[サブラベル]** ブレードで **[保存]** をクリックし、次に **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-299">On the **Sub-label** blade, click **Save**, and then click **OK**.</span></span>

16. <span data-ttu-id="d6110-300">**[Azure Information Protection]** ブレードで **[ポリシー] > [+ 新しいポリシーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-300">On the **Azure Information protection** blade, click **Policies > + Add a new policy**.</span></span>
    
17. <span data-ttu-id="d6110-301">**[名前]** に「**CampaignStrategy**」と入力し、**[説明]** に「**キャンペーン戦略チーム サイトのドキュメント**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d6110-301">Type **CampaignStrategy** in **Name** and **Documents in the Campaign strategy team site** in **Description**.</span></span>
    
18. <span data-ttu-id="d6110-302">**[このポリシーを取得するユーザーまたはグループを選択してください] > [ユーザー/グループ]** をクリックし、**[戦略的シニア スタッフ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d6110-302">Click **Select which users or groups get this policy > User/Groups**, and then select **Senior and strategic staff**.</span></span>
    
19. <span data-ttu-id="d6110-303">**[選択] > [OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-303">Click **Select > OK**.</span></span>

20. <span data-ttu-id="d6110-p109">**[ラベルの追加または削除]** をクリックします。**[ポリシー: ラベルの追加または削除]** ウィンドウで、**[CampaignStrategy]** をクリックしてから、**[OK]** をクリックます。</span><span class="sxs-lookup"><span data-stu-id="d6110-p109">Click **Add or remove labels**. In the **Policy: Add or remove labels** pane, click **CampaignStrategy**, and then click **OK**.</span></span>   

21. <span data-ttu-id="d6110-306">**[保存]** をクリックし、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6110-306">Click **Save**, and then click **OK**.</span></span>
  
<span data-ttu-id="d6110-307">これで、この 4 つのサイトでドキュメントの作成を開始し、さまざまなユーザー アカウントを使用してサイトへのアクセスをテストする準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="d6110-307">You are now ready to begin creating documents in these four sites and test access to them with various user accounts.</span></span> 
  
<span data-ttu-id="d6110-308">Azure Information Protection とこの新しいラベルでドキュメントを保護するには、テスト マシンに [Azure Information Protection クライアントをインストール](https://docs.microsoft.com/information-protection/rms-client/install-client-app)して、Office 365 ポータルから Office をインストールしてから、試用版サブスクリプションの **[戦略的シニア スタッフ]** グループのアカウントを使用して Microsoft Word からサインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6110-308">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d6110-309">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6110-309">See Also</span></span>

[<span data-ttu-id="d6110-310">選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス</span><span class="sxs-lookup"><span data-stu-id="d6110-310">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="d6110-311">選挙運動の開発/テスト環境用にグループとユーザーを構成する</span><span class="sxs-lookup"><span data-stu-id="d6110-311">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="d6110-312">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="d6110-312">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="d6110-313">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="d6110-313">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




