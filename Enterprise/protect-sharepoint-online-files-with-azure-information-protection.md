---
title: "Azure Information Protection を使用して SharePoint Online ファイルを保護する"
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
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: "概要: Azure Information Protection を適用して、機密性の高い SharePoint Online チーム サイト内のファイルを保護します。"
ms.openlocfilehash: 03a10c5d856c4c5518f18b9d02ffe76f2c8d2e7a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="d2d6e-103">Azure Information Protection を使用して SharePoint Online ファイルを保護する</span><span class="sxs-lookup"><span data-stu-id="d2d6e-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="d2d6e-104">**概要:**Azure Information Protection を適用して、機密性の高い SharePoint Online チーム サイト内のファイルを保護します。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="d2d6e-p101">この記事の手順を使用して、Azure Information Protection を構成し、機密性の高い SharePoint Online チーム サイト内のファイルの暗号化やアクセス許可を実施します。暗号化およびアクセス許可の保護は、ファイルをサイトからダウンロードした場合にも適用されます。機密性の高い SharePoint Online チーム サイトの詳細については、「[SharePoint Online サイトとファイルをセキュリティで保護する](secure-sharepoint-online-sites-and-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files in a highly confidential SharePoint Online team site. The encryption and permissions protection travels with a file even when it is downloaded from the site. For more information about highly confidential SharePoint Online team sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="d2d6e-p102">Azure Information Protection 暗号化が Office 365 に格納されているファイルに適用される場合、このサービスはこれらのファイルのコンテンツを処理することはできません。共同編集、電子情報開示、検索、Delve、他の共同作業機能は動作しません。データ損失防止 (DLP) ポリシーが操作できるのはメタデータ (Office 365 ラベルを含む) のみで、それらのファイルのコンテンツ (ファイル内のクレジットカード番号など) を操作することはできません。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-p102">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span> 
  
<span data-ttu-id="d2d6e-111">まず、「[Office 365 管理センターから Azure Rights Management をアクティブ化する方法](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)」にある Office 365 サブスクリプションに関する指示を使用します。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-111">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="d2d6e-112">次に、機密性の高い SharePoint Online チーム サイトの保護とアクセス許可用に、新たなスコープ付きポリシーとサブラベルを使用して Azure Information Protection を構成します。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-112">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="d2d6e-p103">セキュリティ管理者または会社管理者のロールのアカウントを使用して、Office 365 ポータルにサインインします。ヘルプを表示するには、「[Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d2d6e-115">ブラウザーで別のタブで、[(https://portal.azure.com)](https://portal.azure.com) の Azure Portal に移動します。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-115">In a separate tab of your browser, go to the Azure portal ([(https://portal.azure.com)](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="d2d6e-116">初めて Azure Information Protection を構成する場合は、これらの[手順](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-116">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="d2d6e-117">リスト ウィンドウで、 **[その他のサービス]** をクリックして、「 **information**」と入力し、 **[Azure Information Protection]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-117">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="d2d6e-118">**[Azure Information Protection]** ブレードで、 **[スコープ付きポリシー] > [+ 新しいポリシーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-118">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="d2d6e-119">**[ポリシー名]** に新しいポリシーの名前、 **[説明]** に説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-119">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="d2d6e-120">**[このポリシーを取得するユーザーまたはグループを選択] > [ユーザー/グループ]** をクリックし、機密性の高い SharePoint Online チーム サイト用のサイト メンバー アクセス グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-120">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="d2d6e-121">**[選択] > [OK]** とクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-121">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="d2d6e-122">**[非常に機密性の高い社外秘]** ラベルの場合は、省略記号 (...) をクリックしてから、 **[サブラベルの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-122">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="d2d6e-123">**[名前]** にサブラベルの名前、 **[説明]** にラベルの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-123">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="d2d6e-124">**[このラベルを含むドキュメントやメールに対するアクセス許可の設定]** で、 **[保護]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-124">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="d2d6e-125">**[保護]** セクションで、 **[Azure (クラウド キー)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-125">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="d2d6e-126">**[保護]** ブレードの **[保護の設定]** をクリックして **[+ アクセス許可を追加する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-126">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="d2d6e-127">**[アクセス許可を追加する]** ブレードの **[ユーザーとグループの指定]** で、 **[+ ディレクトリを参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-127">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="d2d6e-128">**[AAD のユーザーとグループ]** ウィンドウで、機密性の高い SharePoint Online チーム サイトのサイト メンバー アクセス グループを選択し、 **[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-128">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="d2d6e-129">**[プリセットからアクセス許可を選択]** で、 **[印刷]**、 **[コンテンツのコピーと抽出]**、および **[転送]** チェック ボックスをクリアします。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-129">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="d2d6e-130">[ **OK**] を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-130">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="d2d6e-131">**[サブラベル]** ブレードで、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-131">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="d2d6e-132">新しいスコープ付きポリシー ブレードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-132">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="d2d6e-133">**[Azure Information Protection - スコープ付きポリシー]** ブレードで、 **[発行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-133">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
<span data-ttu-id="d2d6e-134">これが高機密 SharePoint Online チーム サイトの最終的な構成になります。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-134">This is your resulting configuration for your highly confidential SharePoint Online team site.</span></span>
  
![独立した SharePoint Online チーム サイトの Azure Information Protection ラベル。](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
<span data-ttu-id="d2d6e-136">これで、ドキュメントを作成して、Azure Information Protection および新しいラベルでそれらを保護する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-136">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="d2d6e-p104">デバイスまたは Windows ベースのコンピューターに [Azure Information Protection クライアントをインストールする (](https://docs.microsoft.com/information-protection/rms-client/install-client-app)) 必要があります。インストールをスクリプトで記述して自動化するか、ユーザーがクライアントを手動でインストールできます。以下のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-p104">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- <span data-ttu-id="d2d6e-140">[クライアント側での Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/use-client)</span><span class="sxs-lookup"><span data-stu-id="d2d6e-140">[The client side of Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/use-client)</span></span>
    
- <span data-ttu-id="d2d6e-141">[Azure Information Protection クライアント管理者ガイド](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)</span><span class="sxs-lookup"><span data-stu-id="d2d6e-141">[Installing the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)</span></span>
    
- [<span data-ttu-id="d2d6e-142">手動インストールのためのダウンロード ページ</span><span class="sxs-lookup"><span data-stu-id="d2d6e-142">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="d2d6e-p105">インストールすると、ユーザーは Office アプリケーション (Microsoft Word など) を実行してからサインインするときに、Office 365 アカウントを使用します。ユーザーは新しい **[Information Protection]** バーを使用して、新しいラベルを選択できます。ユーザーが機密性の高いファイルを保護するための SharePoint Online チーム サイトと使用するラベルを知っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-p105">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d2d6e-146">機密性の高い複数の SharePoint Online チーム サイトが存在する場合、上記の設定を使用して複数の Azure Information Protection スコープ付きポリシーとサブラベルを作成し、特定の SharePoint Online チーム サイトのサイト メンバー アクセス グループに設定されたサブラベルごとにアクセス許可を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2d6e-146">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="d2d6e-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2d6e-147">See Also</span></span>

[<span data-ttu-id="d2d6e-148">SharePoint Online サイトとファイルをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="d2d6e-148">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="d2d6e-149">開発/テスト環境の SharePoint Online サイトをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="d2d6e-149">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="d2d6e-150">選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス</span><span class="sxs-lookup"><span data-stu-id="d2d6e-150">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="d2d6e-151">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="d2d6e-151">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




