---
title: Azure Information Protection を使用して SharePoint Online ファイルを保護する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/08/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: '概要: Azure Information Protection を適用して、機密性の高い SharePoint Online チーム サイト内のファイルを保護します。'
ms.openlocfilehash: 4ea6c1da8b39f22a56ba4f4d555518b671f07b70
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915312"
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="d9ac8-103">Azure Information Protection を使用して SharePoint Online ファイルを保護する</span><span class="sxs-lookup"><span data-stu-id="d9ac8-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="d9ac8-104">**概要:** Azure Information Protection を適用して、機密性の高い SharePoint Online チーム サイト内のファイルを保護します。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="d9ac8-p101">この記事の手順を使用して、Azure Information Protection を構成し、ファイルの暗号化やアクセス許可を実施します。これらのファイルは、高度な機密保護のために構成された SharePoint ライブラリに追加することができます。あるいは、サイトからファイルを直接開き、Azure Information Protection クライアントを使用して暗号化を追加することもできます。暗号化およびアクセス許可の保護は、ファイルをサイトからダウンロードした場合にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files. These files can be added to a SharePoint library configured for highly confidential protection. Or, you can open a file directly from the site and use the Azure Information Protection client to add encryption. The encryption and permissions protection travels with a file even when it is downloaded from the site.</span></span> 

<span data-ttu-id="d9ac8-p102">これらの手順は、SharePoint サイトとそれらのサイト内のファイルの高度な機密保護を構成するための大きなソリューションの一部です。詳細については、「[SharePoint Online サイトとファイルをセキュリティで保護する](secure-sharepoint-online-sites-and-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-p102">These steps are part of a larger solution for configuring highly confidential protection for SharePoint sites and the files within these sites. For more information, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span> 

<span data-ttu-id="d9ac8-111">SharePoint Online 内のファイルに Azure Information Protection を使用することは、すべてのお客様に推奨されるものではなく、ファイルの一部に対してこの保護レベルを必要としているお客様向けのオプションです。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-111">Using Azure Information Protection for files in SharePoint Online is not recommended for all customers, but is an option for customers who need this level of protection for a subset of files.</span></span>

<span data-ttu-id="d9ac8-112">このソリューションに関する重要な注意点がいくつかあります:</span><span class="sxs-lookup"><span data-stu-id="d9ac8-112">Some important notes about this solution:</span></span>
- <span data-ttu-id="d9ac8-p103">Azure Information Protection 暗号化が Office 365 に格納されているファイルに適用される場合、このサービスはこれらのファイルのコンテンツを処理することはできません。共同編集、電子情報開示、検索、Delve、他の共同作業機能は動作しません。データ損失防止 (DLP) ポリシーが操作できるのはメタデータ (Office 365 ラベルを含む) のみで、それらのファイルのコンテンツ (ファイル内のクレジットカード番号など) を操作することはできません。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-p103">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span>
- <span data-ttu-id="d9ac8-p104">このソリューションでは、Azure Information Protection からの保護が適用されるラベルを、ユーザーが選択する必要があります。自動的な暗号化と、インデックスを作成してファイルを検査するための SharePoint の機能を必要とする場合は、SharePoint Online で Information Rights Management (IRM) を使用することを検討してください。IRM 用に SharePoint ライブラリを構成する場合、ファイルが編集用にダウンロードされるときに、ファイルは自動的に暗号化されます。SharePoint IRM には、意思決定に影響を与える可能性のある制限があります。詳細については、「[SharePoint 管理センターで Information Rights Management (IRM) を設定する](https://support.office.com/ja-JP/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-p104">This solution requires a user to select a label that applies the protection from Azure Information Protection. If you require automatic encryption and the ability for SharePoint to index and inspect the files, consider using Information Rights Management (IRM) in SharePoint Online. When you configure a SharePoint library for IRM, files are automatically encrypted when they are downloaded for editing.  SharePoint IRM includes limitations that might influence your decision. For more information, see [Set up Information Rights Management (IRM) in SharePoint admin center](https://support.office.com/ja-JP/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C).</span></span>

##<a name="admin-setup"></a><span data-ttu-id="d9ac8-121">管理者セットアップ</span><span class="sxs-lookup"><span data-stu-id="d9ac8-121">Admin setup</span></span>
<span data-ttu-id="d9ac8-122">まず、「[Office 365 管理センターから Azure RMS をアクティブ化する方法](https://docs.microsoft.com/information-protection/deploy-use/activate-office365)」にある Office 365 サブスクリプションに関する指示を使用します。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-122">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="d9ac8-123">次に、機密性の高い SharePoint Online チーム サイトの保護とアクセス許可用に、新たなスコープ付きポリシーとサブラベルを使用して Azure Information Protection を構成します。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-123">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="d9ac8-p105">セキュリティ管理者または会社管理者のロールのアカウントを使用して、Office 365 ポータルにサインインします。ヘルプを表示するには、「[Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-p105">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="d9ac8-126">ブラウザーで別のタブを開き、Azure portal ([https://portal.azure.com](https://portal.azure.com)) に移動します。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-126">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="d9ac8-127">初めて Azure Information Protection を構成する場合は、これらの[手順](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-127">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>

4. <span data-ttu-id="d9ac8-128">リスト ウィンドウで、**[すべてのサービス]** をクリックして、「**information**」と入力し、**[Azure Information Protection]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-128">In the list pane, click **All services**, type **information**, and then click **Azure Information Protection**.</span></span>

5. <span data-ttu-id="d9ac8-129">**[ラベル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-129">Click **Labels**.</span></span>
    
6. <span data-ttu-id="d9ac8-130">**[非常に機密性の高い社外秘]** ラベルを右クリックしてから、**[サブラベルの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-130">Right-click the **Highly Confidential** label, and then click **Add a sub-label**.</span></span>
    
7. <span data-ttu-id="d9ac8-131">**[名前]** にサブラベルの名前、 **[説明]** にサブラベルの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-131">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
8. <span data-ttu-id="d9ac8-132">**[このラベルを含むドキュメントやメールに対するアクセス許可の設定]** で、 **[保護]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-132">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
9. <span data-ttu-id="d9ac8-133">**[保護]** セクションで **[Azure (クラウド キー)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-133">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
10. <span data-ttu-id="d9ac8-134">**[保護]** ブレードで **[保護設定]** の **[アクセス許可の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-134">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
11. <span data-ttu-id="d9ac8-135">**[アクセス許可を追加する]** ブレードの **[ユーザーとグループの指定]** で、 **[ディレクトリを参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-135">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
12. <span data-ttu-id="d9ac8-136">**[AAD のユーザーとグループ]** ウィンドウで、機密性の高い SharePoint Online チーム サイトのサイト メンバー アクセス グループを選択し、 **[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-136">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
13. <span data-ttu-id="d9ac8-137">**[事前設定またはカスタムの設定からアクセス許可を選択する]** の **[カスタム]** をクリックし、次に **[権限の表示]**、**[コンテンツの編集]**、**[保存]**、**[返信]**、**[全員へ返信]** の各チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-137">Under **Choose permissions from the preset or set custom**, click **Custom**, and then click the **View Rights**, **Edit Content**, **Save**, **Reply**, and **Reply all** check boxes.</span></span>
    
14. <span data-ttu-id="d9ac8-138">**[OK]** を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-138">Click **OK** twice.</span></span>
    
15. <span data-ttu-id="d9ac8-139">**[サブラベル]** ブレードで **[保存]** をクリックし、次に **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-139">On the **Sub-label** blade, click **Save**, and then click **OK**.</span></span>

16. <span data-ttu-id="d9ac8-140">**[Azure Information Protection]** ブレードで **[ポリシー] > [+ 新しいポリシーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-140">On the **Azure Information protection** blade, click **Policies > + Add a new policy**.</span></span>
    
17. <span data-ttu-id="d9ac8-141">**[ポリシー名]** に新しいポリシーの名前、 **[説明]** に説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-141">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
18. <span data-ttu-id="d9ac8-142">**[このポリシーを取得するユーザーまたはグループを選択] > [ユーザー/グループ]** をクリックし、機密性の高い SharePoint Online チーム サイト用のサイト メンバー アクセス グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-142">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span>
    
19. <span data-ttu-id="d9ac8-143">**[選択] > [OK]** とクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-143">Click **Select > OK**.</span></span>

20. <span data-ttu-id="d9ac8-p106">**[ラベルの追加または削除]** をクリックします。**[ポリシー: ラベルの追加または削除]** ウィンドウで、サブラベルの名前をクリックしてから、**[OK]** をクリックます。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-p106">Click Add or remove labels. In the Policy: Add or remove labels pane, click CampaignStrategy, and then click OK.</span></span>   

21. <span data-ttu-id="d9ac8-146">**[保存]** をクリックし、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-146">Click **Save**, and then click **OK**.</span></span>
 
##<a name="client-setup"></a><span data-ttu-id="d9ac8-147">クライアントのセットアップ</span><span class="sxs-lookup"><span data-stu-id="d9ac8-147">Client setup</span></span>
<span data-ttu-id="d9ac8-148">これで、ドキュメントを作成して、Azure Information Protection および新しいラベルでそれらを保護する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-148">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="d9ac8-p107">デバイスまたは Windows ベースのコンピューターに [Azure Information Protection クライアントをインストールする (](https://docs.microsoft.com/information-protection/rms-client/install-client-app)) 必要があります。インストールをスクリプトで記述して自動化するか、ユーザーがクライアントを手動でインストールできます。以下のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-p107">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="d9ac8-152">クライアント側での Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="d9ac8-152">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="d9ac8-153">Azure Information Protection クライアントのインストール</span><span class="sxs-lookup"><span data-stu-id="d9ac8-153">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="d9ac8-154">手動インストールのためのダウンロード ページ</span><span class="sxs-lookup"><span data-stu-id="d9ac8-154">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="d9ac8-p108">インストールすると、ユーザーは Office アプリケーション (Microsoft Word など) を実行してからサインインするときに、Office 365 アカウントを使用します。ユーザーは新しい **[Information Protection]** バーを使用して、新しいラベルを選択できます。ユーザーが機密性の高いファイルを保護するための SharePoint Online チーム サイトと使用するラベルを知っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-p108">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d9ac8-158">機密性の高い複数の SharePoint Online チーム サイトが存在する場合、上記の設定を使用して複数の Azure Information Protection スコープ付きポリシーとサブラベルを作成し、特定の SharePoint Online チーム サイトのサイト メンバー アクセス グループに設定されたサブラベルごとにアクセス許可を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-158">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
##<a name="adding-permissions-for-external-users"></a><span data-ttu-id="d9ac8-159">外部ユーザーに対するアクセス許可の追加</span><span class="sxs-lookup"><span data-stu-id="d9ac8-159">Adding permissions for external users</span></span>
<span data-ttu-id="d9ac8-p109">Azure Information Protection で保護されているファイルへのアクセス権を外部ユーザーに付与するには、2 つの方法があります。どちらの場合も外部ユーザーには Azure AD アカウントが必要です。外部ユーザーが Azure AD を使用する組織のメンバーでない場合は、サインアップ ページ ([https://aka.ms/aip-signup](https://aka.ms/aip-signup)) を使用して個人で Azure AD アカウントを取得できます。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-p109">There are two ways you can grant external users access to files protected with Azure Information Protection. In both cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this signup page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span></span>

 - <span data-ttu-id="d9ac8-p110">外部ユーザーを、ラベルの保護の構成に使用する Azure AD グループに追加します。最初に、ご使用のディレクトリでアカウントを B2B ユーザーとして追加する必要があります。[Azure Rights Management によるグループ メンバーシップのキャッシュ](https://docs.microsoft.com/ja-JP/azure/information-protection/plan-design/prepare#group-membership-caching-by-azure-information-protection)は、数時間かかる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-p110">Add external users to an Azure AD group that is used to configure protection for a label. You'll need to first add the account as a B2B user in your directory. It can take a couple of hours for [group memership caching by Azure Rights Management](https://docs.microsoft.com/ja-JP/azure/information-protection/plan-design/prepare#group-membership-caching-by-azure-information-protection).</span></span>  
 - <span data-ttu-id="d9ac8-p111">外部ユーザーを直接、ラベル保護に追加します。組織 (例: Fabrikam.com) のすべてのユーザー、Azure AD グループ (例: 組織内の財務グループ)、またはユーザーを追加できます。たとえば、監督機関の外部チームをラベルの保護に加えることができます。</span><span class="sxs-lookup"><span data-stu-id="d9ac8-p111">Add external users directly to the label protection. You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or user. For example, you can add an external team of regulators to the protection for a label.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9ac8-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9ac8-169">See Also</span></span>

[<span data-ttu-id="d9ac8-170">SharePoint Online サイトとファイルをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="d9ac8-170">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="d9ac8-171">開発/テスト環境の SharePoint Online サイトをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="d9ac8-171">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="d9ac8-172">選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス</span><span class="sxs-lookup"><span data-stu-id="d9ac8-172">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="d9ac8-173">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="d9ac8-173">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




