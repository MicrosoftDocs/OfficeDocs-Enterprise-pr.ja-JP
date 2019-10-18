---
title: セキュリティで保護されたゲスト共有環境を作成する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Priority
description: Microsoft 365 でセキュリティで保護されたゲスト共有環境を作成する方法について説明します。
ms.openlocfilehash: 97aa0cf11159af483c307de8bdb2c3b15e704d36
ms.sourcegitcommit: c16ab90d0b9902228ce4337f1c64900592936cce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2019
ms.locfileid: "37108360"
---
# <a name="create-a-secure-guest-sharing-environment"></a><span data-ttu-id="95500-103">セキュリティで保護されたゲスト共有環境を作成する</span><span class="sxs-lookup"><span data-stu-id="95500-103">Create a secure guest sharing environment</span></span>

<span data-ttu-id="95500-104">この記事では、Microsoft 365 でセキュリティで保護されたゲスト共有環境を作成するためのさまざまなオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="95500-104">In this article, we'll walk through a variety of options for creating a secure guest sharing environment in Microsoft 365.</span></span> <span data-ttu-id="95500-105">これは、使用可能なオプションの概要を説明するシナリオ例です。</span><span class="sxs-lookup"><span data-stu-id="95500-105">This is an example scenario to give you an idea of the options available.</span></span> <span data-ttu-id="95500-106">これらの手順は、組織のセキュリティとコンプライアンスのニーズに合わせて、いろいろ組み合わせて使用できます。</span><span class="sxs-lookup"><span data-stu-id="95500-106">You can use these procedures in different combinations to meet the security and compliance needs of your organization.</span></span> <span data-ttu-id="95500-107">記事の最後にあるテスト ケースで、これらのオプションのいくつかを組み合わせて使用する方法を概観します。</span><span class="sxs-lookup"><span data-stu-id="95500-107">At the end of the article, we'll walk through a test case to see how some of these options work together.</span></span>

<span data-ttu-id="95500-108">このシナリオには次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="95500-108">This scenario includes the following configuration:</span></span>

- <span data-ttu-id="95500-109">ゲスト用の多要素認証を設定する。</span><span class="sxs-lookup"><span data-stu-id="95500-109">Setting up multi-factor authentication for guests.</span></span>
- <span data-ttu-id="95500-110">ゲスト用の利用規約を設定する。</span><span class="sxs-lookup"><span data-stu-id="95500-110">Setting up a terms of use for guests.</span></span>
- <span data-ttu-id="95500-111">ゲストがチームやサイトに対するアクセス許可をまだ必要としているか定期的に確認するため、四半期ごとのゲスト アクセス レビューを設定する。</span><span class="sxs-lookup"><span data-stu-id="95500-111">Setting up quarterly guest access reviews to periodically validate whether guests continue to need permissions to teams and sites.</span></span>
- <span data-ttu-id="95500-112">アンマネージド デバイスに対するゲストのアクセスを Web のみに制限する。</span><span class="sxs-lookup"><span data-stu-id="95500-112">Restricting guests to web-only access for unmanaged devices.</span></span>
- <span data-ttu-id="95500-113">ゲストを毎日認証するようにセッション タイムアウト ポリシーを構成する。</span><span class="sxs-lookup"><span data-stu-id="95500-113">Configuring a session timeout policy to ensure guests authenticate daily.</span></span>
- <span data-ttu-id="95500-114">コンテンツを分類するための秘密度ラベルを作成および公開する。</span><span class="sxs-lookup"><span data-stu-id="95500-114">Creating and publishing sensitivity labels to classify content.</span></span>
- <span data-ttu-id="95500-115">極秘プロジェクト向けの機密情報の種類を作成する。</span><span class="sxs-lookup"><span data-stu-id="95500-115">Creating a sensitive information type for a highly confidential project.</span></span>
- <span data-ttu-id="95500-116">*[極秘]* ラベルをその機密情報の種類を含むドキュメントに自動的に割り当てる。</span><span class="sxs-lookup"><span data-stu-id="95500-116">Automatically assigning a *highly confidential* label to documents that contain the sensitive information type.</span></span>
- <span data-ttu-id="95500-117">*[極秘]* のラベルが付けられたファイルから自動的にゲスト アクセスを削除する。</span><span class="sxs-lookup"><span data-stu-id="95500-117">Automatically removing guest access from files labeled as *highly confidential*.</span></span>

<span data-ttu-id="95500-118">この記事で説明するオプションの一部には、ゲストが Azure Active Directory のアカウントを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="95500-118">Some of the options discussed in this article require guests to have an account in Azure Active Directory.</span></span> <span data-ttu-id="95500-119">ファイルやフォルダーをゲストと共有する際、ゲストがそのディレクトリに含まれていることを確認するには、[SharePoint および OneDrive の Azure AD B2B (プレビュー) との統合](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)を使用します。</span><span class="sxs-lookup"><span data-stu-id="95500-119">To ensure that guests are included in the directory when you share files and folders with them, use the [SharePoint and OneDrive integration with Azure AD B2B Preview](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview).</span></span>

<span data-ttu-id="95500-120">この記事ではゲスト共有設定を有効化する方法については扱いません。</span><span class="sxs-lookup"><span data-stu-id="95500-120">Note that we won't discuss enabling guest sharing settings in this article.</span></span> <span data-ttu-id="95500-121">さまざまなシナリオでゲスト共有を有効化する方法の詳細については、「[組織外のユーザーとの共同作業](https://docs.microsoft.com/Office365/Enterprise/collaborating-with-people-outside-your-organization)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95500-121">See [Collaborating with people outside your organization](https://docs.microsoft.com/Office365/Enterprise/collaborating-with-people-outside-your-organization) for details about enabling guest sharing for different scenarios.</span></span>

## <a name="set-up-multi-factor-authentication-for-guests"></a><span data-ttu-id="95500-122">ゲスト用の多要素認証を設定する</span><span class="sxs-lookup"><span data-stu-id="95500-122">Set up multi-factor authentication for Office 365</span></span>

<span data-ttu-id="95500-123">多要素認証を行うと、アカウントが漏洩する可能性が大幅に軽減されます。</span><span class="sxs-lookup"><span data-stu-id="95500-123">Multi-factor authentication greatly reduces the chances of an account being compromised.</span></span> <span data-ttu-id="95500-124">ゲスト ユーザーはガバナンス ポリシーやベスト プラクティスに準拠していない個人用メール アカウントを使用している可能性があるため、ゲストに対して多要素認証を必須にすることは特に重要です。</span><span class="sxs-lookup"><span data-stu-id="95500-124">Since guest users may be using personal email accounts that don't adhere to any governance policies or best practices, it's especially important to require multi-factor authentication for guests.</span></span> <span data-ttu-id="95500-125">ゲスト ユーザーのユーザー名とパスワードが盗難された場合でも、2 番目の認証要素が要求されるため、不明なユーザーがサイトやファイルにアクセスする可能性を大幅に減少できます。</span><span class="sxs-lookup"><span data-stu-id="95500-125">If a guest user's username and password is stolen, requiring a second factor of authentication greatly reduces the chances of unknown parties gaining access to your sites and files.</span></span>

<span data-ttu-id="95500-126">この例では、Azure Active Directory で条件付きアクセス ポリシーを使用して、ゲスト用の多要素認証を設定します。</span><span class="sxs-lookup"><span data-stu-id="95500-126">In this example, we'll set up multi-factor authentication for guests by using a conditional access policy in Azure Active Directory.</span></span>

<span data-ttu-id="95500-127">ゲスト用の多要素認証を設定するには</span><span class="sxs-lookup"><span data-stu-id="95500-127">To set up multi-factor authentication for Office 365</span></span>
1. <span data-ttu-id="95500-128">Microsoft Azure で *[条件付きアクセス]* を検索します。</span><span class="sxs-lookup"><span data-stu-id="95500-128">In Microsoft Azure, search for *Conditional access*.</span></span>
2. <span data-ttu-id="95500-129">**[条件付きアクセス - ポリシー]** ブレードで、**[新しいポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-129">On the **Conditional Access - Policies** blade, click **New policy**.</span></span>
3. <span data-ttu-id="95500-130">**[名前]** フィールドに「*ゲストの MFA*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="95500-130">In the **Name** field, type *WCFCustomer*.</span></span>
4. <span data-ttu-id="95500-131">**[割り当て]** の下の **[ユーザーとグループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-131">Under **Assignments**, click **Users and groups**.</span></span>
5. <span data-ttu-id="95500-132">**[ユーザーとグループ]** ブレードで、**[ユーザーとグループの選択]** を選択し、**[すべてのゲストと外部ユーザー]** チェック ボックスをオンにして、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-132">On the **Users and groups** blade, select **Select users and groups**, select the **All guests and external users** check box, and then click **Done**.</span></span>
4. <span data-ttu-id="95500-133">**[アクセス制御]** で、**[許可]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-133">Under **Access controls**, click **Grant**.</span></span>
5. <span data-ttu-id="95500-134">**[許可]** ブレードで、**[多要素認証を要求する]** チェック ボックスをオンにし、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-134">On the **Grant** blade, select the **Require multi-factor authentication** check box, and then click **Select**.</span></span>
6. <span data-ttu-id="95500-135">**[新規]** ブレードの **[ポリシーの有効化]** で、**[オン]** をクリックして、**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-135">On the **New** blade, under **Enable policy**, click **On**, and then click **Create**.</span></span>

<span data-ttu-id="95500-136">これで、ゲストは、多要素認証に登録してからでなければ共有コンテンツ、サイト、チームにアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="95500-136">Now, guest will be required to enroll in multi-factor authentication before they can access shared content, sites, or teams.</span></span>

### <a name="more-information"></a><span data-ttu-id="95500-137">詳細情報</span><span class="sxs-lookup"><span data-stu-id="95500-137">More information</span></span>

[<span data-ttu-id="95500-138">クラウド ベースの Azure Multi-Factor Authentication のデプロイの計画</span><span class="sxs-lookup"><span data-stu-id="95500-138">Planning a cloud-based Azure Multi-Factor Authentication deployment</span></span>](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted)

## <a name="set-up-a-terms-of-use-for-guests"></a><span data-ttu-id="95500-139">ゲスト用の利用規約を設定する</span><span class="sxs-lookup"><span data-stu-id="95500-139">Set up a terms of use for guests</span></span>

<span data-ttu-id="95500-140">ゲスト ユーザーは、お客様の組織との機密保持契約その他の法的契約に署名していないことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="95500-140">Often times guest users may not have signed non-disclosure agreements or other legal agreements with your organization.</span></span> <span data-ttu-id="95500-141">ゲストが共有ファイルにアクセスできるようにする前に、利用規約への同意をゲストに要求することができます。</span><span class="sxs-lookup"><span data-stu-id="95500-141">You can require guests to agree to a terms of use before accessing files that are shared with them.</span></span> <span data-ttu-id="95500-142">この利用規約は、ゲストが初めて共有ファイルやサイトにアクセスしようとしたときに表示されるようにできます。</span><span class="sxs-lookup"><span data-stu-id="95500-142">The terms of use can be displayed the first time they attempt to access a shared file or site.</span></span>

<span data-ttu-id="95500-143">利用規約を作成するには、そのドキュメントを Word などのオーサリング プログラムでまず作成し、.pdf ファイルとして保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95500-143">To create a terms of use, you first need to create the document in Word or another authoring program, and then save it as a .pdf file.</span></span> <span data-ttu-id="95500-144">次に、このファイルを Azure AD にアップロードします。</span><span class="sxs-lookup"><span data-stu-id="95500-144">This file can then be uploaded to Azure AD.</span></span>

<span data-ttu-id="95500-145">Azure AD の利用規約を作成するには</span><span class="sxs-lookup"><span data-stu-id="95500-145">To create an Azure AD terms of use</span></span>
1. <span data-ttu-id="95500-146">Azure にグローバル管理者、セキュリティ管理者、または条件付きアクセス管理者としてサインインします。</span><span class="sxs-lookup"><span data-stu-id="95500-146">Sign in to Azure as a Global Administrator, Security Administrator, or Conditional Access Administrator.</span></span>
2. <span data-ttu-id="95500-147">[[利用規約]](https://aka.ms/catou) に移動します。</span><span class="sxs-lookup"><span data-stu-id="95500-147">Navigate to [Terms of use](https://aka.ms/catou).</span></span>
3. <span data-ttu-id="95500-148">**[新しい利用規約]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-148">Click **New terms**.</span></span></br>
   <span data-ttu-id="95500-149">![Azure AD の新しい利用規約設定のスクリーンショット](media/azure-ad-guest-terms-of-use.png)</span><span class="sxs-lookup"><span data-stu-id="95500-149">![Screenshot of Azure AD new terms of use settings](media/azure-ad-guest-terms-of-use.png)</span></span>
4. <span data-ttu-id="95500-150">**[名前]** ボックスと **[表示名]** ボックスに「*ゲストの利用規約*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="95500-150">In the **Name** and **Display name** boxes, type *Guest terms of use*.</span></span>
6. <span data-ttu-id="95500-151">**[利用規約のドキュメント]** には、作成した PDF ファイルを参照して選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-151">For **Terms of use document**, browse to the pdf file that you created and select it.</span></span>
7. <span data-ttu-id="95500-152">利用規約のドキュメントの言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-152">Select the language for your terms of use document.</span></span>
8. <span data-ttu-id="95500-153">**[ユーザーは使用条件を展開する必要があります]** を **[オン]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="95500-153">Set **Require users to expand the terms of use** to **On**.</span></span>
9. <span data-ttu-id="95500-154">**[条件付きアクセス]** の下にある **[Enforce with conditional access policy template] (条件付きアクセス ポリシーのテンプレートの適用)** リストから、**[後で条件付きアクセス ポリシーを作成する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-154">Under **Conditional Access**, in the **Enforce with Conditional Access policy template** list choose **Create conditional access policy later**.</span></span>
10. <span data-ttu-id="95500-155">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-155">Click **Create**.</span></span>

<span data-ttu-id="95500-156">利用規約の作成が完了したら、次に、ゲスト ユーザーにその利用規約を表示する条件付きアクセス ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="95500-156">Once you've created the terms of use, the next step is to create a conditional access policy that displays the terms of use to guest users.</span></span>

<span data-ttu-id="95500-157">条件付きアクセス ポリシーを作成するには</span><span class="sxs-lookup"><span data-stu-id="95500-157">To create a new conditional access policy:</span></span>
1. <span data-ttu-id="95500-158">Microsoft Azure で *[条件付きアクセス]* を検索します。</span><span class="sxs-lookup"><span data-stu-id="95500-158">In Microsoft Azure, search for *Conditional access*.</span></span>
2. <span data-ttu-id="95500-159">**[条件付きアクセス - ポリシー]** ブレードで、**[新しいポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-159">On the **Conditional Access - Policies** blade, click **New policy**.</span></span>
3. <span data-ttu-id="95500-160">**[名前]** ボックスに「*ゲスト ユーザー利用規約のポリシー*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="95500-160">In the **Name** box, type *Guest user terms of use policy*.</span></span>
4. <span data-ttu-id="95500-161">**[割り当て]** の下の **[ユーザーとグループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-161">Under **Assignments**, click **Users and groups**.</span></span>
5. <span data-ttu-id="95500-162">**[ユーザーとグループ]** ブレードで、**[ユーザーとグループの選択]** を選択し、**[すべてのゲストと外部ユーザー]** チェック ボックスをオンにして、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-162">On the **Users and groups** blade, select **Select users and groups**, select the **All guests and external users** check box, and then click **Done**.</span></span>
6. <span data-ttu-id="95500-163">**[割り当て]** の下の **[クラウド アプリまたはアクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-163">Under **Assignments**, click **Cloud apps or actions**.</span></span>
7. <span data-ttu-id="95500-164">**[含める]** タブで、**[アプリを選択]** を選択し、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-164">On the **Include** tab, select **Select apps**, and then click **Select**.</span></span>
8. <span data-ttu-id="95500-165">**[選択]** ブレードで、**Microsoft Teams**、**Office 365 SharePoint Online**、**Outlook Groups** を選択し、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-165">On the **Select** blade, select **Microsoft Teams**, **Office 365 SharePoint Online**, and **Outlook Groups**, and then click **Select**.</span></span>
9. <span data-ttu-id="95500-166">**[クラウド アプリまたはアクション]** ブレードで、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-166">On the **Cloud apps or actions** blade, click **Done**.</span></span>
10. <span data-ttu-id="95500-167">**[アクセス制御]** で、**[許可]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-167">Under **Access controls**, click **Grant**.</span></span>
11. <span data-ttu-id="95500-168">**[許可]** ブレードで、「**ゲストの利用規約**」と入力し、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-168">On the **Grant** blade, select **Guest terms of use**, and then click **Select**.</span></span>
12. <span data-ttu-id="95500-169">**[新規]** ブレードの **[ポリシーの有効化]** で、**[オン]** をクリックして、**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-169">On the **New** blade, under **Enable policy**, click **On**, and then click **Create**.</span></span>

<span data-ttu-id="95500-170">これで、ゲスト ユーザーがお客様の組織のコンテンツ、チームやサイトに初めてアクセスしようとしたときに、利用規約への同意を要求されるようになります。</span><span class="sxs-lookup"><span data-stu-id="95500-170">Now, the first time a guest user attempts to access content or a team or site in your organization, they will be required to accept the terms of use.</span></span>

### <a name="more-information"></a><span data-ttu-id="95500-171">詳細情報</span><span class="sxs-lookup"><span data-stu-id="95500-171">More information</span></span>
[<span data-ttu-id="95500-172">Azure Active Directory の利用規約</span><span class="sxs-lookup"><span data-stu-id="95500-172">Azure Active Directory terms of use</span></span>](https://docs.microsoft.com/azure/active-directory/conditional-access/terms-of-use)

## <a name="set-up-guest-access-reviews"></a><span data-ttu-id="95500-173">ゲスト アクセス レビューを設定する</span><span class="sxs-lookup"><span data-stu-id="95500-173">Set up guest access reviews</span></span>

<span data-ttu-id="95500-174">Azure AD のアクセス レビューを使用すると、さまざまなチームやグループに対するユーザー アクセスの定期的なレビューを自動化できます。</span><span class="sxs-lookup"><span data-stu-id="95500-174">With access reviews in Azure AD, you can automate a periodic review of user access to various teams and groups.</span></span> <span data-ttu-id="95500-175">特に、ゲストのアクセス レビューを必須にすることにより、ゲスト ユーザーが必要以上に長く組織の機密情報へのアクセス権を保持しないようにできます。</span><span class="sxs-lookup"><span data-stu-id="95500-175">By requiring an access review for guests specifically, you can help ensure guest users do not retain access to your organization's sensitive information for longer than is necessary.</span></span>

<span data-ttu-id="95500-176">アクセス レビューは、プログラムに整理できます。</span><span class="sxs-lookup"><span data-stu-id="95500-176">Access reviews can be organized into programs.</span></span> <span data-ttu-id="95500-177">プログラムとは、類似したアクセス レビューをグループ化したもので、アクセス レビューをレポート作成や監査の目的で整理するのに使用できます。</span><span class="sxs-lookup"><span data-stu-id="95500-177">A program is a grouping of similar access reviews that can be used to organize access reviews for reporting and auditing purposes.</span></span>

<span data-ttu-id="95500-178">この例では、ゲスト アクセス レビュー用のグループを作成します。</span><span class="sxs-lookup"><span data-stu-id="95500-178">In this example, we'll create a program for guest access reviews.</span></span>

<span data-ttu-id="95500-179">プログラムを作成するには</span><span class="sxs-lookup"><span data-stu-id="95500-179">To create a program for the package</span></span>
1. <span data-ttu-id="95500-180">Azure portal にログインして、[[Identity Governance]](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade) ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="95500-180">Sign in to the Azure portal and open the [Service Bus](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade) tab.</span></span>
2. <span data-ttu-id="95500-181">左側のメニューで、**[プログラム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-181">In the left menu, click **Websites**.</span></span>
3. <span data-ttu-id="95500-182">**[新しいプログラム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-182">Click **New program**.</span></span>
4. <span data-ttu-id="95500-183">**[名前]** ボックスに「*ゲスト アクセス レビュー プログラム*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="95500-183">In the **Name** box, type *Guest access review program*.</span></span>
5. <span data-ttu-id="95500-184">**[説明]** ボックスに「*ゲスト アクセス レビュー用プログラム*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="95500-184">In the **Description** box, type *Program for guest access reviews*.</span></span>
6. <span data-ttu-id="95500-185">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-185">Click **Create**.</span></span>

<span data-ttu-id="95500-186">プログラムの作成が完了したら、ゲスト アクセス レビューを作成して、プログラムに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="95500-186">Once the program has been created, we can create a guest access review and associate it with the program.</span></span>

<span data-ttu-id="95500-187">ゲスト ユーザー アクセス レビューを設定するには</span><span class="sxs-lookup"><span data-stu-id="95500-187">To set up a guest user access review</span></span>
1. <span data-ttu-id="95500-188">[[Identity Governance]](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade) ページの左側のメニューで、**[アクセス レビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-188">On the [Identity Governance page](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade), in the left menu, click **Access reviews**.</span></span>
2. <span data-ttu-id="95500-189">**[新しいアクセス レビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-189">Click **New access review**.</span></span></br>
   <span data-ttu-id="95500-190">![Azure AD のアクセス レビュー設定のスクリーンショット](media/azure-ad-create-access-review.png)</span><span class="sxs-lookup"><span data-stu-id="95500-190">![Screenshot of Azure AD access review settings](media/azure-ad-create-access-review.png)</span></span>
3. <span data-ttu-id="95500-191">**[名前]** ボックスに「*四半期ごとのゲスト アクセス レビュー*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="95500-191">In the **Name** box, type *Quarterly guest access review*.</span></span>
4. <span data-ttu-id="95500-192">**[頻度]** は、**[四半期に 1 回]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-192">For **Frequency**, choose **Quarterly**.</span></span>
5. <span data-ttu-id="95500-193">**[終了]** は、**[指定しない]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-193">For **End**, choose **Never**.</span></span>
6. <span data-ttu-id="95500-194">**[スコープ]** は、**[ゲスト ユーザーのみ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-194">For **Scope**, choose **Guest users only**.</span></span>
7. <span data-ttu-id="95500-195">**[グループ]** をクリックし、アクセス レビューに含めるグループを選択したら、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-195">Click **Group**, select the groups that you want to include in the access review, and then click **Select**.</span></span>
8. <span data-ttu-id="95500-196">**[プログラム]** の下の **[プログラムへのリンク]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-196">Under **Programs**, click **Link to program**.</span></span>
9. <span data-ttu-id="95500-197">**[プログラムの選択]** ブレードで、**[ゲスト アクセス レビュー プログラム]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-197">On the **Select a program** blade, choose **Guest access review program**</span></span>
10. <span data-ttu-id="95500-198">**[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-198">Click **Start**.</span></span>

<span data-ttu-id="95500-199">指定したグループごとに、別個のアクセス レビューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="95500-199">A separate access review is created for each group that you specify.</span></span> <span data-ttu-id="95500-200">各グループのグループ所有者は、四半期ごとにメールを受け取り、グループに対するゲスト アクセスを許可または拒否できます。</span><span class="sxs-lookup"><span data-stu-id="95500-200">Group owners of each groups will be emailed quarterly to approve or deny guest access to their groups.</span></span>

<span data-ttu-id="95500-201">重要な点として、ゲストにはチームやグループに対するアクセス権か、個々のファイルやフォルダーに対するアクセス権を付与できます。</span><span class="sxs-lookup"><span data-stu-id="95500-201">It's important to note that guests can be given access to teams or groups, or to individual files and folders.</span></span> <span data-ttu-id="95500-202">ファイルやフォルダーに対するアクセス権を与えられているゲストは、特定のグループに追加できません。</span><span class="sxs-lookup"><span data-stu-id="95500-202">When given access to files and folders, guests may not be added to any particular group.</span></span> <span data-ttu-id="95500-203">チームやグループに属していないゲスト ユーザーに対してアクセス レビューを実行する場合は、Azure AD ですべてのゲストが含まれる動的グループを作成して、そのグループに対するアクセス レビューを作成できます。</span><span class="sxs-lookup"><span data-stu-id="95500-203">If you want to do access reviews on guest users who don't belong to a team or group, you can create a dynamic group in Azure AD to contain all guests and then create an access review for that group.</span></span>

### <a name="more-information"></a><span data-ttu-id="95500-204">詳細情報</span><span class="sxs-lookup"><span data-stu-id="95500-204">More information</span></span>
[<span data-ttu-id="95500-205">Azure AD のアクセス レビューでゲスト アクセスを管理する</span><span class="sxs-lookup"><span data-stu-id="95500-205">Manage guest access with Azure AD access reviews</span></span>](https://docs.microsoft.com/azure/active-directory/governance/manage-guest-access-with-access-reviews)

[<span data-ttu-id="95500-206">グループまたはアプリケーションのアクセス レビューを Azure AD アクセス レビューで作成する</span><span class="sxs-lookup"><span data-stu-id="95500-206">Create an access review of groups or applications in Azure AD access reviews</span></span>](https://docs.microsoft.com/azure/active-directory/governance/create-access-review)

## <a name="set-up-web-only-access-for-guest-users"></a><span data-ttu-id="95500-207">ゲスト ユーザー用の Web 専用アクセスを設定する</span><span class="sxs-lookup"><span data-stu-id="95500-207">Set up web-only access for guest users</span></span>

<span data-ttu-id="95500-208">ゲスト ユーザーが Web ブラウザーのみを使用してチーム、サイト、ファイルにアクセスするように要求することにより、攻撃面を減少させて、管理を容易にできます。</span><span class="sxs-lookup"><span data-stu-id="95500-208">You can reduce your attack surface and ease administration by requiring guest users to access your teams, sites, and files by using a web browser only.</span></span> <span data-ttu-id="95500-209">これは、Azure AD 条件付きアクセス ポリシーで実現できます。</span><span class="sxs-lookup"><span data-stu-id="95500-209">This is done with an Azure AD conditional access policy.</span></span>

<span data-ttu-id="95500-210">ゲストのアクセスを Web のみに制限するには</span><span class="sxs-lookup"><span data-stu-id="95500-210">To restrict guests to web-ony access</span></span>
1. <span data-ttu-id="95500-211">Microsoft Azure で *[条件付きアクセス]* を検索します。</span><span class="sxs-lookup"><span data-stu-id="95500-211">In Microsoft Azure, search for *Conditional access*.</span></span>
2. <span data-ttu-id="95500-212">**[条件付きアクセス - ポリシー]** ブレードで、**[新しいポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-212">On the **Conditional Access - Policies** blade, click **New policy**.</span></span>
3. <span data-ttu-id="95500-213">**[名前]** ボックスに「*ゲスト ユーザー ブラウザー アクセス*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="95500-213">In the **Name** box, type *Guest user browser access*.</span></span>
4. <span data-ttu-id="95500-214">**[割り当て]** の下の **[ユーザーとグループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-214">Under **Assignments**, click **Users and groups**.</span></span>
5. <span data-ttu-id="95500-215">**[ユーザーとグループ]** ブレードで、**[ユーザーとグループの選択]** を選択し、**[すべてのゲストと外部ユーザー]** チェック ボックスをオンにして、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-215">On the **Users and groups** blade, select **Select users and groups**, select the **All guests and external users** check box, and then click **Done**.</span></span>
6. <span data-ttu-id="95500-216">**[割り当て]** の下の **[クラウド アプリまたはアクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-216">Under **Assignments**, click **Cloud apps or actions**.</span></span>
7. <span data-ttu-id="95500-217">**[含める]** タブで、**[アプリを選択]** を選択し、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-217">On the **Include** tab, select **Select apps**, and then click **Select**.</span></span>
8. <span data-ttu-id="95500-218">**[選択]** ブレードで、**Microsoft Teams**、**Office 365 SharePoint Online**、**Outlook Groups** を選択し、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-218">On the **Select** blade, select **Microsoft Teams**, **Office 365 SharePoint Online**, and **Outlook Groups**, and then click **Select**.</span></span>
9. <span data-ttu-id="95500-219">**[クラウド アプリまたはアクション]** ブレードで、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-219">On the **Cloud apps or actions** blade, click **Done**.</span></span>
10. <span data-ttu-id="95500-220">**[割り当て]** の下の **[条件]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-220">Under **Assignments**, click **Conditions**.</span></span>
11. <span data-ttu-id="95500-221">**[条件]** ブレードで、**[クライアント アプリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-221">On the **Conditions** blade, click **Client apps**.</span></span>
12. <span data-ttu-id="95500-222">**[クライアント アプリ]** ブレードで、**[構成する]** の **[はい]** をクリックし、**[モバイル アプリとデスクトップ クライアント]** と **[先進認証クライアント]** の設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-222">On the **Client apps** blade, click **Yes** for **Configure**, and then select the **Mobile apps and desktop clients** and **Modern authentication clients** settings.</span></span></br>
    <span data-ttu-id="95500-223">![Azure AD の条件付きアクセス クライアント アプリ設定のスクリーンショット](media/azure-ad-conditional-access-client-mobile.png)</span><span class="sxs-lookup"><span data-stu-id="95500-223">![Screenshot of Azure AD conditional access client apps settings](media/azure-ad-conditional-access-client-mobile.png)</span></span>
13. <span data-ttu-id="95500-224">**[完了]** をクリックし、**[条件]** ブレードでもう一度 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-224">Click **Done**, and then on the **Conditions** blade, click **Done** again.</span></span>
14. <span data-ttu-id="95500-225">**[アクセス制御]** で、**[許可]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-225">Under **Access controls**, click **Grant**.</span></span>
15. <span data-ttu-id="95500-226">**[許可]** ブレードで、**[デバイスは準拠としてマーク済みである必要がある]** および **[Hybrid Azure AD 参加済みデバイスが必要]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-226">On the **Grant** blade, select **Require device to be marked as compliant** and **Require Hybrid Azure AD joined device**.</span></span>
16. <span data-ttu-id="95500-227">**[複数のコントロールの場合]** の下の **[選択したコントロールのいずれかが必要]** を選択して、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-227">Under **For multiple controls**, select **Require one of the selected controls**, and then click **Select**.</span></span>
17. <span data-ttu-id="95500-228">**[新規]** ブレードの **[ポリシーの有効化]** で、**[オン]** をクリックして、**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-228">On the **New** blade, under **Enable policy**, click **On**, and then click **Create**.</span></span>

## <a name="configure-a-session-timeout-for-guest-users"></a><span data-ttu-id="95500-229">ゲスト ユーザー用のセッション タイムアウトを設定する</span><span class="sxs-lookup"><span data-stu-id="95500-229">Configure a session timeout for guest users</span></span>

<span data-ttu-id="95500-230">ゲストに定期的な認証を要求することにより、ゲスト ユーザーのデバイスがセキュリティで保護されていない場合も、不明なユーザーがお客様の組織のコンテンツにアクセスする可能性を減少できます。</span><span class="sxs-lookup"><span data-stu-id="95500-230">Requiring guests to authenticate on a regular basis can reduce the possibility of unknown users accessing your organization's content if a guest user's device isn't kept secure.</span></span> <span data-ttu-id="95500-231">ゲスト ユーザー用のセッション タイムアウト条件付きアクセス ポリシーを、Azure AD で設定できます。</span><span class="sxs-lookup"><span data-stu-id="95500-231">You can configure a session timeout conditional access policy for guest users in Azure AD.</span></span>

<span data-ttu-id="95500-232">ゲスト セッション タイムアウト ポリシーを設定するには</span><span class="sxs-lookup"><span data-stu-id="95500-232">To configure a guest session timeout policy</span></span>
1. <span data-ttu-id="95500-233">Microsoft Azure で *[条件付きアクセス]* を検索します。</span><span class="sxs-lookup"><span data-stu-id="95500-233">In Microsoft Azure, search for *Conditional access*.</span></span>
2. <span data-ttu-id="95500-234">**[条件付きアクセス - ポリシー]** ブレードで、**[新しいポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-234">On the **Conditional Access - Policies** blade, click **New policy**.</span></span>
3. <span data-ttu-id="95500-235">**[名前]** ボックスに「*ゲスト セッション タイムアウト*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="95500-235">In the **Name** box, type *Guest session timeout*.</span></span>
4. <span data-ttu-id="95500-236">**[割り当て]** の下の **[ユーザーとグループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-236">Under **Assignments**, click **Users and groups**.</span></span>
5. <span data-ttu-id="95500-237">**[ユーザーとグループ]** ブレードで、**[ユーザーとグループの選択]** を選択し、**[すべてのゲストと外部ユーザー]** チェック ボックスをオンにして、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-237">On the **Users and groups** blade, select **Select users and groups**, select the **All guests and external users** check box, and then click **Done**.</span></span>
6. <span data-ttu-id="95500-238">**[割り当て]** の下の **[クラウド アプリまたはアクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-238">Under **Assignments**, click **Cloud apps or actions**.</span></span>
7. <span data-ttu-id="95500-239">**[含める]** タブで、**[アプリを選択]** を選択し、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-239">On the **Include** tab, select **Select apps**, and then click **Select**.</span></span>
8. <span data-ttu-id="95500-240">**[選択]** ブレードで、**Microsoft Teams**、**Office 365 SharePoint Online**、**Outlook Groups** を選択し、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-240">On the **Select** blade, select **Microsoft Teams**, **Office 365 SharePoint Online**, and **Outlook Groups**, and then click **Select**.</span></span>
9. <span data-ttu-id="95500-241">**[クラウド アプリまたはアクション]** ブレードで、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-241">On the **Cloud apps or actions** blade, click **Done**.</span></span>
10. <span data-ttu-id="95500-242">**[アクセス制御]** で、**[セッション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-242">Under **Access controls**, click **Session**.</span></span>
11. <span data-ttu-id="95500-243">**[セッション]** ブレードで、**[サインイン頻度]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-243">On the **Session** blade, select **Sign-in frequency**.</span></span>
12. <span data-ttu-id="95500-244">期間として **[1]** および **[日]** を選択し、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-244">Select **1** and **Days** for the time period, and then click **Select**.</span></span>
13. <span data-ttu-id="95500-245">**[新規]** ブレードの **[ポリシーの有効化]** で、**[オン]** をクリックして、**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-245">On the **New** blade, under **Enable policy**, click **On**, and then click **Create**.</span></span>

## <a name="create-sensitivity-labels"></a><span data-ttu-id="95500-246">秘密度ラベルを作成する</span><span class="sxs-lookup"><span data-stu-id="95500-246">Create sensitivity labels</span></span>

<span data-ttu-id="95500-247">秘密度ラベルは、お客様の組織の情報を分類し保護するためにさまざまな方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="95500-247">Sensitivity labels can be used in a variety of ways to classify and protect your organization's information.</span></span> <span data-ttu-id="95500-248">この例では、共有ファイルやフォルダーに対するゲスト アクセスを管理するためにラベルを使用する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="95500-248">In this example, we'll look at how labels can be used to help you manage guest access to shared files and folders.</span></span>

<span data-ttu-id="95500-249">まず、Microsoft 365 コンプライアンス センターで次の 3 つの秘密度ラベルを作成します。</span><span class="sxs-lookup"><span data-stu-id="95500-249">First, we'll create three sensitivity labels in the Microsoft 365 Compliance Center:</span></span>

- <span data-ttu-id="95500-250">一般</span><span class="sxs-lookup"><span data-stu-id="95500-250">General</span></span>
- <span data-ttu-id="95500-251">社外秘</span><span class="sxs-lookup"><span data-stu-id="95500-251">Confidential</span></span>
- <span data-ttu-id="95500-252">極秘</span><span class="sxs-lookup"><span data-stu-id="95500-252">Highly Confidential</span></span>

<span data-ttu-id="95500-253">以下の手順を使用して、*[一般]* ラベルと *[社外秘]* ラベルを作成します。</span><span class="sxs-lookup"><span data-stu-id="95500-253">Use the following procedure to create the *General* and *Confidential* labels.</span></span>

<span data-ttu-id="95500-254">分類ラベル (一般および社外秘) を作成するには</span><span class="sxs-lookup"><span data-stu-id="95500-254">To create a classification label (General and Confidential)</span></span>
1. <span data-ttu-id="95500-255">[Microsoft 365 コンプライアンス センター](https://compliance.microsoft.com)の左側のナビゲーションで、**[分類]** を展開し、**[秘密度ラベル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-255">In the [Microsoft 365 Compliance Center](https://compliance.microsoft.com), in the left navigation, expand **Classification**, and then click **Sensitivity labels**.</span></span>
2. <span data-ttu-id="95500-256">**[ラベルの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-256">Click **Retention labels > Create a label**.</span></span>
3. <span data-ttu-id="95500-257">**[ラベル名]** に「*一般*」または「*社外秘*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="95500-257">In **Label name**, type *General* or *Confidential*.</span></span>
4. <span data-ttu-id="95500-258">**[ヒント]** に「*従業員、ゲスト、パートナーと共有できる一般情報*」または「*機密情報。従業員および承認されたゲストとのみ共有*」と入力し、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-258">In **Tooltip**, type *General information that can be shared with employees, guests, and partners* or *Confidential information. Share only with employees and authorized guests*, and then click **Next**.</span></span>
5. <span data-ttu-id="95500-259">[暗号化] を **[オフ]** のままにし、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-259">Leave encryption **Off** and click **Next**.</span></span>
6. <span data-ttu-id="95500-260">[コンテンツのマーキング] を **[オフ]** のままにし、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-260">Leave content marking **Off** and click **Next**.</span></span>
7. <span data-ttu-id="95500-261">[エンドポイントのデータ損失防止] を **[オフ]** のままにし、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-261">Leave endpoint data loss prevention **Off** and click **Next**.</span></span>
8. <span data-ttu-id="95500-262">[自動ラベル付け] を **[オフ]** のままにし、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-262">Leave auto labeling **Off** and click **Next**.</span></span>
9. <span data-ttu-id="95500-263">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-263">Click **Create**.</span></span>

<span data-ttu-id="95500-264">*[極秘]* ラベルでは、このラベルが付いたドキュメントの自動透かしを追加します。</span><span class="sxs-lookup"><span data-stu-id="95500-264">With the *Highly Confidential* label, we'll add automatic watermarking of documents with the label.</span></span>

<span data-ttu-id="95500-265">分類ラベル (極秘) を作成するには</span><span class="sxs-lookup"><span data-stu-id="95500-265">To create a classification label (Highly confidential)</span></span>
1. <span data-ttu-id="95500-266">**[ラベルの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-266">Click **Retention labels > Create a label**.</span></span>
2. <span data-ttu-id="95500-267">**[ラベル名]** に「*極秘*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="95500-267">In **Label name**, type *Highly confidential*.</span></span>
3. <span data-ttu-id="95500-268">**[ヒント]** に「*極秘情報。ゲストとの共有禁止*」と入力し、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-268">In **Tooltip**, type *Highly confidential information. Do not share with guests*, and then click **Next**.</span></span>
4. <span data-ttu-id="95500-269">[暗号化] を **[オフ]** のままにし、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-269">Leave encryption **Off** and click **Next**.</span></span>
5. <span data-ttu-id="95500-270">[コンテンツのマーキング] を **[オン]** にし、**[ヘッダーの追加]** チェック ボックスをオンにして、**[テキストをカスタマイズする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-270">Turn content marking **On**, select the **Add a header** check box, and then click **Customize text**.</span></span>
6. <span data-ttu-id="95500-271">[ヘッダー テキスト] に「*極秘*」と入力し、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-271">Type *Highly confidential* for the header text and click **Save**.</span></span>
7. <span data-ttu-id="95500-272">**[コンテンツのマーキング]** ページで、[コンテンツのマーキング] を **[オン]** にします。</span><span class="sxs-lookup"><span data-stu-id="95500-272">On the **Content marking** page, turn content marking **On**.</span></span>
8. <span data-ttu-id="95500-273">**[透かしの追加]** チェック ボックスをオンにして、**[テキストをカスタマイズする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-273">Select the **Add a watermark** check box, and then click **Customize text**.</span></span>
9. <span data-ttu-id="95500-274">**[透かしのテキスト]** に「*極秘*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="95500-274">For **Watermark text**, type *Highly Confidential*.</span></span>
10. <span data-ttu-id="95500-275">**[フォント サイズ]** に「*24*」と入力し、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-275">Type *24* for **Font size**, and then click **Save**.</span></span>
11. <span data-ttu-id="95500-276">**[コンテンツのマーキング]** ページで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-276">On the **Welcome** page, click **Next**.</span></span>
12. <span data-ttu-id="95500-277">[エンドポイントのデータ損失防止] を **[オフ]** のままにし、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-277">Leave endpoint data loss prevention **Off** and click **Next**.</span></span>
13. <span data-ttu-id="95500-278">[自動ラベル付け] を **[オフ]** のままにし、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-278">Leave auto labeling **Off** and click **Next**.</span></span>
14. <span data-ttu-id="95500-279">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-279">Click **Create**.</span></span>

![Microsoft 365 コンプライアンス センターの秘密度ラベルのスクリーンショット](media/microsoft-365-sharing-sensitivity-labels.png)

<span data-ttu-id="95500-281">ラベルの作成が完了したら、次にそれらのラベルを発行します。</span><span class="sxs-lookup"><span data-stu-id="95500-281">Once you've created the labels, the next step is to publish them.</span></span> 

<span data-ttu-id="95500-282">ラベルを発行するには</span><span class="sxs-lookup"><span data-stu-id="95500-282">To publish labels</span></span>
1. <span data-ttu-id="95500-283">**[秘密度ラベル]** ページで、**[ラベルの発行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-283">On the **Sensitivity labels** page, click **Publish labels**.</span></span>
2. <span data-ttu-id="95500-284">**[発行するラベルの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-284">Click **Choose labels to publish**.</span></span>
3. <span data-ttu-id="95500-285">**[追加]** をクリックして、作成したラベルを選択し、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-285">Click **Add**, select the labels that you created, and then click **Add**.</span></span>
4. <span data-ttu-id="95500-286">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-286">Click **Done**.</span></span>
5. <span data-ttu-id="95500-287">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-287">Click **Next**.</span></span>
6. <span data-ttu-id="95500-288">[ユーザーとグループ] は **[すべて]** に設定されたままにし、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-288">Leave the users and groups set to **All** and click **Next**.</span></span>
7. <span data-ttu-id="95500-289">**[既定でドキュメントとメールにこのラベルを適用する]** リストから **[一般]** を選択し、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-289">In the **Apply this label by default to documents and email** list, choose **General**, and then click **Next**.</span></span>
8. <span data-ttu-id="95500-290">**[ポリシー設定]** ページで、[名前] に「*ドキュメントの秘密度*」と入力し、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-290">On the **Policy settings** page, type *Document sensitivity* for the name, and then click **Next**.</span></span>
9. <span data-ttu-id="95500-291">**[発行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-291">Click **Publish**.</span></span>

<span data-ttu-id="95500-292">ラベルが発行され、Office デスクトップ アプリのユーザーが使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="95500-292">With the labels published, they're available to users of Office desktop apps.</span></span> <span data-ttu-id="95500-293">ユーザーが **[極秘]** ラベルを適用すると、そのドキュメントには透かしが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="95500-293">When users apply the **Highly Confidential** label, a watermark is automatically added to the document.</span></span>

### <a name="more-information"></a><span data-ttu-id="95500-294">詳細情報</span><span class="sxs-lookup"><span data-stu-id="95500-294">More information</span></span>
[<span data-ttu-id="95500-295">秘密度ラベルの概要</span><span class="sxs-lookup"><span data-stu-id="95500-295">Overview of sensitivity labels</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels)

## <a name="create-a-sensitive-information-type-for-a-highly-confidential-project"></a><span data-ttu-id="95500-296">極秘プロジェクト向けの機密情報の種類を作成する</span><span class="sxs-lookup"><span data-stu-id="95500-296">Create a sensitive information type for a highly confidential project</span></span>

<span data-ttu-id="95500-297">機密情報の種類は、コンプライアンス要件を適用するためにポリシー ワークフローで使用できる定義済みの文字列です。</span><span class="sxs-lookup"><span data-stu-id="95500-297">Sensitive information types are predefined strings that can be used in policy workflows to enforce compliance requirements.</span></span> <span data-ttu-id="95500-298">Microsoft 365 コンプライアンス センターには、運転免許証番号、クレジット カード番号、銀行口座番号など、100 を超える機密情報の種類が用意されています。</span><span class="sxs-lookup"><span data-stu-id="95500-298">The Microsoft 365 Compliance Center comes with over one hundred sensitive information types, including driver's license numbers, credit card numbers, bank account numbers, etc.</span></span>

<span data-ttu-id="95500-299">カスタムの機密情報の種類を作成して、お客様の組織に固有のコンテンツを管理するために利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="95500-299">You can create custom sensitive information types to help manage content specific to your organization.</span></span> <span data-ttu-id="95500-300">この例では、極秘プロジェクト向けにカスタムの機密情報の種類を作成します。</span><span class="sxs-lookup"><span data-stu-id="95500-300">In this example, we'll create a custom sensitive information type for a highly confidential project.</span></span> <span data-ttu-id="95500-301">そのようにすると、この機密情報の種類を使用して、分類ラベルを自動的に適用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="95500-301">We can then use this sensitive information type to automatically apply a classification label.</span></span>

<span data-ttu-id="95500-302">機密情報の種類を作成するには</span><span class="sxs-lookup"><span data-stu-id="95500-302">To create a sensitive information type</span></span>
1. <span data-ttu-id="95500-303">[Microsoft 365 コンプライアンス センター](https://compliance.microsoft.com)の左側のナビゲーションで、**[分類]** を展開し、**[機密情報の種類]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-303">In the [Microsoft 365 Compliance Center](https://compliance.microsoft.com), in the left navigation, expand **Classification**, and then click **Sensitive info types**.</span></span>
2. <span data-ttu-id="95500-304">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-304">Click **Create**.</span></span>
3. <span data-ttu-id="95500-305">**[名前]** と **[説明]** に「**Project Saturn**」と入力し、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-305">For **Name** and **Description**, type **Project Saturn**, and then click **Next**.</span></span>
4. <span data-ttu-id="95500-306">**[要素の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-306">Click **Add an app**.</span></span>
5. <span data-ttu-id="95500-307">**[次が含まれているコンテンツを検出する]** リストで **[キーワード]** を選択して、キーワード ボックスに「*Project Saturn*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="95500-307">On the **Detect content containing** list, select **Keywords**, and then type *Project Saturn* in the keyword box.</span></span>
6. <span data-ttu-id="95500-308">**[次へ]** をクリックし、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-308">Click **Next**, and then click **Finish**.</span></span>
7. <span data-ttu-id="95500-309">機密情報の種類をテストするかどうかをたずねられたら、**[いいえ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-309">If asked if you would like to test the sensitive information type, click **No**.</span></span>

### <a name="more-information"></a><span data-ttu-id="95500-310">詳細情報</span><span class="sxs-lookup"><span data-stu-id="95500-310">More information</span></span>
[<span data-ttu-id="95500-311">カスタムの機密情報の種類</span><span class="sxs-lookup"><span data-stu-id="95500-311">Custom sensitive information types</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/custom-sensitive-info-types)

## <a name="create-a-policy-to-assign-a-label-based-on-a-sensitive-information-type"></a><span data-ttu-id="95500-312">機密情報の種類に基づいてラベルを割り当てるポリシーを作成する</span><span class="sxs-lookup"><span data-stu-id="95500-312">Create a policy to assign a label based on a sensitive information type</span></span>

<span data-ttu-id="95500-313">機密情報の種類の作成が完了したら、Microsoft Cloud App Security でファイル ポリシーを作成して、*Project Saturn* という文字列を含むドキュメントに自動的に *[極秘]* ラベルを適用できます。</span><span class="sxs-lookup"><span data-stu-id="95500-313">Once the sensitive information type is created, we can create a file policy in Microsoft Cloud App Security to apply the *Highly Confidential* label to documents that contain the *Project Saturn* string automatically.</span></span>

> [!NOTE]
> <span data-ttu-id="95500-314">Cloud App Security で秘密度ラベルを使用できるようにするレプリケーション プロセスがあります。</span><span class="sxs-lookup"><span data-stu-id="95500-314">There is a replication process that makes sensitivity labels available in Cloud App Security.</span></span> <span data-ttu-id="95500-315">そのラベルはポリシーにすぐ利用できる状態ではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="95500-315">You may not see the label available for a policy right away.</span></span>

<span data-ttu-id="95500-316">機密情報の種類に基づくファイル ポリシーを作成するには</span><span class="sxs-lookup"><span data-stu-id="95500-316">To create a sensitive information type-based file policy</span></span>
1. <span data-ttu-id="95500-317">[Microsoft Cloud App Security](https://portal.cloudappsecurity.com) を開きます。</span><span class="sxs-lookup"><span data-stu-id="95500-317">[Microsoft Cloud App Security](https://portal.cloudappsecurity.com)</span></span>
2. <span data-ttu-id="95500-318">左側のナビゲーションで、**[コントロール]** を展開し、**[ポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-318">In the left navigation, expand **Control**, and then click **Policies**.</span></span>
3. <span data-ttu-id="95500-319">**[ポリシーの作成]** をクリックし、**[ファイル ポリシー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-319">Click **Create policy**, and then choose **File policy**.</span></span>
4. <span data-ttu-id="95500-320">**[ポリシー名]** に「*Project Saturn のラベル*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="95500-320">For **Policy name**, type *Project Saturn labeling*.</span></span>
5. <span data-ttu-id="95500-321">**[このポリシーの対象となるファイルのフィルターを作成する]** の下にある [X] を 2 回クリックして、既定のフィルターを削除します。</span><span class="sxs-lookup"><span data-stu-id="95500-321">Under **Create a filter for the files this policy will act on**, click X twice to delete the default filters.</span></span>
7. <span data-ttu-id="95500-322">**[フィルターの選択]** リストで **[アプリ]** を選択して、**[アプリの選択...]** リストから **[Microsoft SharePoint Online]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-322">In the **Select a filter** list, choose **App**, and then select **Microsoft SharePoint Online** from the **Select apps...** list.</span></span>
8. <span data-ttu-id="95500-323">**[検査方法]** の下の **[データ分類サービス]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-323">Under **Inspection method**, choose **Data classification service**.</span></span>
9. <span data-ttu-id="95500-324">**[検査の種類の選択]** リストで、**[機密情報の種類]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-324">On the **Choose inspection type** list, choose **Sensitive information type**.</span></span>
10. <span data-ttu-id="95500-325">*Project Saturn* 秘密度ラベルを検索して選択し、**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-325">Search for and select the *Project Saturn* sensitivity label, and then click **Done**.</span></span></br>
   <span data-ttu-id="95500-326">![Cloud App Security の検査方法設定のスクリーンショット](media/mcas-sensitive-info-type-project-saturn.png)</span><span class="sxs-lookup"><span data-stu-id="95500-326">![Screenshot of Cloud App Security inspection method settings](media/mcas-sensitive-info-type-project-saturn.png)</span></span>
11. <span data-ttu-id="95500-327">**[ガバナンス]** の下の **[Microsoft SharePoint Online]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="95500-327">Under **Governance**, expand **Microsoft SharePoint Online**.</span></span>
12. <span data-ttu-id="95500-328">**[分類ラベルを適用する]** チェック ボックスをオンにして、**[極秘]** ラベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-328">Select the **Apply classification label** check box and select the **Highly Confidential** label.</span></span>
13. <span data-ttu-id="95500-329">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-329">Click **Create**.</span></span>

<span data-ttu-id="95500-330">ポリシーが設定されている状態でユーザーがドキュメントに「Project Saturn」と入力すると、Cloud App Security がファイルをスキャンする際に *[極秘]* ラベルが自動的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="95500-330">With the policy in place, when a user types "Project Saturn" into a document, Cloud App Security will automatically apply the *Highly Confidential* label when it scans the file.</span></span>

### <a name="more-information"></a><span data-ttu-id="95500-331">詳細情報</span><span class="sxs-lookup"><span data-stu-id="95500-331">More information</span></span>
[<span data-ttu-id="95500-332">ファイル ポリシー</span><span class="sxs-lookup"><span data-stu-id="95500-332">File policies</span></span>](https://docs.microsoft.com/cloud-app-security/data-protection-policies)

## <a name="create-a-policy-to-remove-guest-access-to-highly-confidential-files"></a><span data-ttu-id="95500-333">極秘ファイルへのゲスト アクセスを削除するポリシーを作成する</span><span class="sxs-lookup"><span data-stu-id="95500-333">Create a policy to remove guest access to highly confidential files</span></span>

<span data-ttu-id="95500-334">この記事の例では、*[極秘]* ラベルが付いたファイルをゲストと共有することは禁止されています。</span><span class="sxs-lookup"><span data-stu-id="95500-334">In the example in this article, files with the *Highly Confidential* label shouldn't be shared with guests.</span></span> <span data-ttu-id="95500-335">Cloud App Security で、このラベルが付いたファイルからゲスト アクセスを自動的に削除するファイル ポリシーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="95500-335">We can create a file policy in Cloud App Security that automatically removes guest access from files with that label.</span></span>

<span data-ttu-id="95500-336">この操作で、ユーザーがこれらのファイルを共有したり、再共有したりできなくなるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="95500-336">Note that this doesn't prevent users from sharing or re-sharing these files.</span></span> <span data-ttu-id="95500-337">ゲスト共有が許可されているサイトに保存されているファイルのガバナンス ポリシーに従うかどうかは、依然としてユーザーに委ねられています。</span><span class="sxs-lookup"><span data-stu-id="95500-337">You're still reliant on your users to follow your governance policies for files that are stored in sites that allow guest sharing.</span></span> <span data-ttu-id="95500-338">とはいえ、このツールは、ゲストと共有された後に機密情報が追加されたファイルからゲスト アクセスを削除するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="95500-338">However, this can be a useful tool for removing guest access from files that had confidential information added to them after they were shared with guests.</span></span>

<span data-ttu-id="95500-339">ラベルに基づくファイル ポリシーを作成するには</span><span class="sxs-lookup"><span data-stu-id="95500-339">To create a label-based file policy</span></span>
1. <span data-ttu-id="95500-340">[Microsoft Cloud App Security](https://portal.cloudappsecurity.com) を開きます。</span><span class="sxs-lookup"><span data-stu-id="95500-340">[Microsoft Cloud App Security](https://portal.cloudappsecurity.com)</span></span>
2. <span data-ttu-id="95500-341">左側のナビゲーションで、**[コントロール]** を展開し、**[ポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-341">In the left navigation, expand **Control**, and then click **Policies**.</span></span>
3. <span data-ttu-id="95500-342">**[ポリシーの作成]** をクリックし、**[ファイル ポリシー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-342">Click **Create policy**, and then choose **File policy**.</span></span>
4. <span data-ttu-id="95500-343">**[ポリシー名]** に「*Project Saturn - ゲスト アクセスの削除*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="95500-343">For **Policy name**, type *Project Saturn - remove guest access*.</span></span>
5. <span data-ttu-id="95500-344">**[このポリシーの対象となるファイルのフィルターを作成する]** の下にある [X] を 2 回クリックして、既定のフィルターを削除します。</span><span class="sxs-lookup"><span data-stu-id="95500-344">Under **Create a filter for the files this policy will act on**, click X twice to delete the default filters.</span></span>
6. <span data-ttu-id="95500-345">**[フィルターの選択]** リストで **[アプリ]** を選択して、**[アプリの選択...]** リストから **[Microsoft SharePoint Online]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-345">In the **Select a filter** list, choose **App**, and then select **Microsoft SharePoint Online** from the **Select apps...** list.</span></span>
7. <span data-ttu-id="95500-346">**[フィルターの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-346">Click **Add a user**.</span></span>
8. <span data-ttu-id="95500-347">**[フィルターの選択]** リストで **[分類ラベル]** を選択して、**[フィルターの選択...]** リストから **[Azure Information Protection]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-347">In the **Select a filter** list, choose **Classification label**, and then select **Azure Information Protection** from the **Select filter...** list.</span></span>
9. <span data-ttu-id="95500-348">**[分類ラベルの選択]** リストで、**[極秘]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="95500-348">In the **Select classification label** list, select **Highly Confidential**.</span></span></br>
   <span data-ttu-id="95500-349">![Cloud App Security のポリシー フィルター設定のスクリーンショット](media/mcas-sharepoint-confidential-label-filter.png)</span><span class="sxs-lookup"><span data-stu-id="95500-349">![Screenshot of Cloud App Security policy filter settings](media/mcas-sharepoint-confidential-label-filter.png)</span></span>
10. <span data-ttu-id="95500-350">**[ガバナンス]** の下の **[Microsoft SharePoint Online]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="95500-350">Under **Governance**, expand **Microsoft SharePoint Online**.</span></span>
11. <span data-ttu-id="95500-351">**[ポリシー一致のダイジェストをファイル所有者へ送信]** チェック ボックスと **[外部ユーザーを削除する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="95500-351">Select the **Send policy-match digest to file owner** and **Remove external users** check boxes.</span></span>
12. <span data-ttu-id="95500-352">[カスタム通知メッセージ] に「*極秘ファイル。会社のポリシーによりゲストとの共有禁止*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="95500-352">For the custom notification message, type *This file is highly confidential. Company policy prohibits sharing it with guests*.</span></span>
13. <span data-ttu-id="95500-353">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95500-353">Click **Create**.</span></span>

<span data-ttu-id="95500-354">重要な点として、このポリシーが削除するのは *[特定のユーザー]* リンクを使用して共有されているファイルに対するアクセスです。</span><span class="sxs-lookup"><span data-stu-id="95500-354">It's important to note, that this policy removes access for files shared using a *Specific people* link.</span></span> <span data-ttu-id="95500-355">匿名 (*すべてのユーザー*) リンクからのアクセスは削除されません。</span><span class="sxs-lookup"><span data-stu-id="95500-355">It doesn't remove access from anonymous (*Anyone*) links.</span></span> <span data-ttu-id="95500-356">また、ゲストがサイトやチーム全体のメンバーである場合も、アクセスは削除されません。</span><span class="sxs-lookup"><span data-stu-id="95500-356">It also doesn't remove access if the guest is a member of the site or team as a whole.</span></span> <span data-ttu-id="95500-357">ゲスト メンバーのいるサイトやチームに極秘ドキュメントを作成する場合は、[チーム内の非公開チャネル](https://support.office.com/article/60ef929a-4d68-418b-bf4f-5784db184ec9)を使用して、その非公開チャネル内でお客様の組織のメンバーのみに許可することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="95500-357">If you plan to have highly confidential documents in a site or team with guest members, consider using [private channels in Teams](https://support.office.com/article/60ef929a-4d68-418b-bf4f-5784db184ec9) and only allowing members of your organization in the private channels.</span></span>

## <a name="test-the-solution"></a><span data-ttu-id="95500-358">ソリューションをテストする</span><span class="sxs-lookup"><span data-stu-id="95500-358">Test the solution</span></span>

<span data-ttu-id="95500-359">この記事で説明されているソリューションをテストするには、Word ドキュメントを作成し、ドキュメント ライブラリに保存します。</span><span class="sxs-lookup"><span data-stu-id="95500-359">To test the solution described in this article, create a Word document and save it to a document library.</span></span> <span data-ttu-id="95500-360">そのファイルをゲスト ユーザーと共有します。</span><span class="sxs-lookup"><span data-stu-id="95500-360">Share the file with a guest user.</span></span> <span data-ttu-id="95500-361">ゲストがドキュメントにアクセスしようとすると、多要素認証に登録して、利用規約に同意するように要求されるはずです。</span><span class="sxs-lookup"><span data-stu-id="95500-361">When the guest attempts to access the document, they should be required to enroll in multi-factor authentication, and then accept the terms of use.</span></span>

<span data-ttu-id="95500-362">ゲストがそのドキュメントにアクセスできるようになったら、そのドキュメントに「*Project Saturn*」と入力して保存します。</span><span class="sxs-lookup"><span data-stu-id="95500-362">Once the guest has access to the document, type *Project Saturn* in the document and save it.</span></span> <span data-ttu-id="95500-363">Cloud App Security がドキュメントをスキャンすると、*[極秘]* ラベルが適用され、そのゲスト ユーザーはドキュメントにアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="95500-363">Once Cloud App Security scans the document, the *Highly Confidential* label should be applied and the guest user should no longer have access to it.</span></span>

<span data-ttu-id="95500-364">この記事で説明されているツールをさまざまな組み合わせで使用することにより、組織にとって生産的でありながら安全なゲスト共有環境を作成できます。</span><span class="sxs-lookup"><span data-stu-id="95500-364">You can use the tools described in this article in various combinations to help create a productive but safe guest sharing environment for your organization.</span></span>

## <a name="see-also"></a><span data-ttu-id="95500-365">関連項目</span><span class="sxs-lookup"><span data-stu-id="95500-365">See Also</span></span>

[<span data-ttu-id="95500-366">ゲストと共有するときにファイルの偶発的な公開を制限する</span><span class="sxs-lookup"><span data-stu-id="95500-366">Limit accidental exposure to files when sharing with guests</span></span>](sharing-limit-accidental-exposure.md)

[<span data-ttu-id="95500-367">匿名ユーザーとファイルおよびフォルダーを共有するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="95500-367">Best practices for sharing files and folders with anonymous users</span></span>](best-practices-anonymous-sharing.md)
