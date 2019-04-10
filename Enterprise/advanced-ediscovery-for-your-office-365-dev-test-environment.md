---
title: Office 365 の開発/テスト環境のアドバンスト eDiscovery
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
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: '概要: Office 365 の開発/テスト環境で、サンプル データを使用して Office 365 アドバンスト eDiscovery を構成し、デモンストレーションします。'
ms.openlocfilehash: b1cf2714f79d38e5a3349b331cee0862cd6aac52
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741454"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="426f9-103">Office 365 の開発/テスト環境のアドバンスト eDiscovery</span><span class="sxs-lookup"><span data-stu-id="426f9-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="426f9-104">**概要:** Office 365 の開発/テスト環境で、サンプル データを使用して Office 365 アドバンスト eDiscovery を構成し、デモンストレーションします。</span><span class="sxs-lookup"><span data-stu-id="426f9-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="426f9-105">office 365 Advanced 電子情報開示を使用すると、電子メールやドキュメントなど、office 365 に保存されているデータに関する関連情報をすばやく検索して分析できます。</span><span class="sxs-lookup"><span data-stu-id="426f9-105">Office 365 Advanced eDiscovery lets you quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents.</span></span> <span data-ttu-id="426f9-106">これにより、特に訴訟の状況では、時間と経費を大幅に節約できます。</span><span class="sxs-lookup"><span data-stu-id="426f9-106">This can save enormous amounts of time and expense, especially in litigation situations.</span></span> <span data-ttu-id="426f9-107">詳細については、「[Office 365 の高度な電子情報開示](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="426f9-107">For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="426f9-108">この記事の手順では、架空の契約問題に関するデータの小さなセットを作成し、そのデータをアドバンスト eDiscovery で分析します。</span><span class="sxs-lookup"><span data-stu-id="426f9-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="426f9-109">Office 365 のテストラボガイドスタックにあるすべての記事のビジュアルマップについては、[ここ](http://aka.ms/catlgstack)をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="426f9-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="426f9-110">フェーズ 1: Office 365 の開発/テスト環境を作成する</span><span class="sxs-lookup"><span data-stu-id="426f9-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="426f9-111">最小限の要件で高度な電子情報開示をテストする場合は、「フェーズ2」と「フェーズ 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md)」の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="426f9-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="426f9-112">シミュレートされたエンタープライズで高度な電子情報開示をテストする場合は、「 [Office のディレクトリ同期の開発/テスト環境](dirsync-for-your-office-365-dev-test-environment.md)」の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="426f9-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="426f9-113">高度な電子情報開示のテストでは、インターネットに接続されたシミュレートされたイントラネットと Active directory ドメインサービス (AD DS) フォレストのディレクトリ同期を含む、シミュレートされたエンタープライズ環境を必要としません。</span><span class="sxs-lookup"><span data-stu-id="426f9-113">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for an Active Directory Domain Services (AD DS) forest.</span></span> <span data-ttu-id="426f9-114">この記事は、一般的な組織を表す環境でテストと実験を実行できるようにするためのオプションとして提供されています。</span><span class="sxs-lookup"><span data-stu-id="426f9-114">It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="426f9-115">フェーズ 2:アドバンスト eDiscovery 用のサンプル データを作成する</span><span class="sxs-lookup"><span data-stu-id="426f9-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="426f9-116">この手順では、電子メール メッセージを作成します。このメッセージをアドバンスト eDiscovery のケースで分析することになります。</span><span class="sxs-lookup"><span data-stu-id="426f9-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="426f9-117">Internet Explorer を開き、 [https://outlook.com](https://outlook.com) [Office 365 開発/テスト環境](office-365-dev-test-environment.md)のフェーズ2で作成した Outlook アカウントにサインインします。</span><span class="sxs-lookup"><span data-stu-id="426f9-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="426f9-118">ライトウェイトの開発/テスト環境を使用している場合は、Internet Explorer のプライベート セッションを開いて、ローカル コンピューターからサインインします。</span><span class="sxs-lookup"><span data-stu-id="426f9-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="426f9-119">シミュレートされたエンタープライズ開発/テスト環境を使用している場合は、[https://portal.azure.com](https://portal.azure.com)Azure portal () を使用して client1 仮想マシンに接続し、client1 からサインインします。</span><span class="sxs-lookup"><span data-stu-id="426f9-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="426f9-120">**[Outlook メール]** タブで、**[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="426f9-121">[**宛先**] に、試用版サブスクリプションの User6 アカウントの電子メールアドレスを入力し\*\* user6@ます (。\*\*</span><span class="sxs-lookup"><span data-stu-id="426f9-121">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**</span></span><organization name> <span data-ttu-id="426f9-122">**. onmicrosoft.com**)。</span><span class="sxs-lookup"><span data-stu-id="426f9-122">**.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="426f9-123">件名に、「**Test email 1**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="426f9-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="426f9-124">本文に、「**Tailspin contract draft**」と入力して、**[送信]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="426f9-125">**[Outlook メール]** タブで、**[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="426f9-126">**[宛先]** に、試用版サブスクリプションの User6 アカウントの電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="426f9-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="426f9-127">件名に、「**Test email 2**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="426f9-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="426f9-128">本文に、「**Tailspin lunch meeting**」と入力して、**[送信]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="426f9-129">**[Outlook メール]** タブで、**[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="426f9-130">**[宛先]** に、試用版サブスクリプションの User6 アカウントの電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="426f9-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="426f9-131">件名に、「**Test email 3**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="426f9-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="426f9-132">本文に、「**Tailspin contract disagreement**」と入力して、**[送信]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="426f9-133">右上の隅にあるユーザー アイコンをクリックして、**[サインアウト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="426f9-134">新しいタブを開き、試用版サブスクリプションの User6 アカウントのアカウント[https://www.office.com](https://www.office.com)名とパスワードを使用して、Office 365 ポータル () にサインインします。</span><span class="sxs-lookup"><span data-stu-id="426f9-134">Open a new tab and sign in to the Office 365 portal ([https://www.office.com](https://www.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="426f9-135">**[Office 365 ポータル]** タブで、**[メール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="426f9-136">[ **User6** ] タブで、User6 が outlook の電子メールアカウントから3通のメールをすべて受信していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="426f9-136">On the **Mail - User6 - Outlook** tab, check that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="426f9-137">User6 の **Office 365 ポータルのタブ**に戻ります。</span><span class="sxs-lookup"><span data-stu-id="426f9-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="426f9-138">右上の隅にあるユーザー アイコンをクリックして、**[サインアウト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="426f9-139">この手順では、2 つの Word 文書を作成します。この文書をアドバンスト eDiscovery のケースで分析することになります。</span><span class="sxs-lookup"><span data-stu-id="426f9-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="426f9-140">**[Office]** ページで **[サインイン]** をクリックし、グローバル管理者アカウントの認証情報でサインインします。</span><span class="sxs-lookup"><span data-stu-id="426f9-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="426f9-141">新しいタブで、運用中の SharePoint サイトの URL にアクセスします: **https://** <fictional organization name> **。 sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="426f9-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="426f9-142">**[実稼働サイト コレクション]** タブの **[ドキュメント]** で **[新規] > [Word 文書]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="426f9-143">**[Word Online]** ページで、「**Tailspin draft contract**」と入力して、タイトルに **[保存済み]** と表示されるまで待ってから、**[Word Online]** ページのタブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="426f9-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="426f9-144">**[実稼働サイト コレクション]** タブの **[ドキュメント]** で **[新規] > [Word 文書]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="426f9-145">**[Word Online]** タブで、「**Tailspin contract dispute notes**」と入力して、タイトルに **[保存済み]** と表示されるまで待ってから、**[Word Online]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="426f9-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="426f9-146">**[運用サイト コレクション]** タブのドキュメントの一覧に、**Document** および **Document1** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="426f9-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="426f9-147">**[運用サイト コレクション]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="426f9-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="426f9-148">フェーズ 3: 法的な争議に高度な電子情報開示を使用する</span><span class="sxs-lookup"><span data-stu-id="426f9-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="426f9-149">残念なことに、Tailspin Toys との契約問題が訴訟にまで達してしまいました。</span><span class="sxs-lookup"><span data-stu-id="426f9-149">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action.</span></span> <span data-ttu-id="426f9-150">この手順では、「Tailspin contract」というテキストを含む電子メールとドキュメントを検索して分析するための高度な電子情報開示ケースを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="426f9-150">In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="426f9-151">アドバンスト eDiscovery を使用するためのプロセスは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="426f9-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="426f9-152">セキュリティ&amp; /コンプライアンスセンターで検索を作成し、その結果を分析して、上級電子情報開示のために結果を準備します。</span><span class="sxs-lookup"><span data-stu-id="426f9-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="426f9-153">アドバンスト eDiscovery でケースを作成して構成し、検索結果を分析します。</span><span class="sxs-lookup"><span data-stu-id="426f9-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="426f9-154">この手順では、「Tailspin contract」のセキュリティ&amp;コンプライアンスセンターで検索を作成し、結果を確認してから、高度な電子情報開示のために結果を準備します。</span><span class="sxs-lookup"><span data-stu-id="426f9-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="426f9-155">**Office 365 ポータル**のタブで、**[管理者]** をクリックします</span><span class="sxs-lookup"><span data-stu-id="426f9-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="426f9-156">管理センターのタブにある左側のナビゲーションで、**[管理センター]、[コンプライアンス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="426f9-157">[**セキュリティ&amp;のコンプライアンス**] タブで、[**アクセス許可**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="426f9-158">**[アクセス許可]** リストで、**[Organization Management]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="426f9-159">**[役割グループ]** ウィンドウで、**[メンバー]** のプラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="426f9-160">**[メンバーの選択]** ウィンドウで、管理者アカウントの名前をダブルクリックして、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="426f9-161">**[役割グループ]** ウィンドウで、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="426f9-162">**[アクセス許可]** リストで、**[電子情報開示マネージャー]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="426f9-163">**[役割グループ]** ウィンドウで、**[電子情報開示の管理者]** のプラス記号のアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="426f9-164">**[メンバーの選択]** ウィンドウで、管理者アカウントの名前をダブルクリックして、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="426f9-165">**[役割グループ]** ウィンドウで、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="426f9-166">左側のナビゲーションで、[**検索&amp;調査 > コンテンツ検索**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="426f9-167">プラス記号のアイコンをクリックして、検索を追加します。</span><span class="sxs-lookup"><span data-stu-id="426f9-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="426f9-168">**[新規検索]** ウィンドウで、**[名前]** に「**Tailspin contract search**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="426f9-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="426f9-169">**[どこを調べますか?]** で、**[すべての場所の検索]** をクリックし、**[Exchange]**、**[SharePoint]**、および **[パブリック フォルダー]** を選択して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="426f9-170">**[どこを調べますか?]** で、「**Tailspin contract**」と入力して、**[検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="426f9-171">検索のリストで、名前 **[Tailspin contract search]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="426f9-172">**[Tailspin contract search]** ウィンドウで、**[結果]** の **[検索結果のプレビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-172">In the **Tailspin contract search** pane, click **Preview search results** under **Results**.</span></span> <span data-ttu-id="426f9-173">作業中の SharePoint サイト (**ドキュメント**と**文書**1) に2つのドキュメントが一覧表示され、User6 への電子メールの**テスト**と**電子メール 3**の電子メールのテストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="426f9-173">You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6.</span></span> <span data-ttu-id="426f9-174">ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="426f9-174">Close the window.</span></span>
    
19. <span data-ttu-id="426f9-175">**[コンテンツ検索]** ウィンドウで、**[アドバンスト eDiscovery による結果の分析]** の **[分析用の結果のプレビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="426f9-176">**[Tailspin contract search の検索結果の準備]** ウィンドウで、**[準備]** をクリックして完了まで待機します。</span><span class="sxs-lookup"><span data-stu-id="426f9-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="426f9-177">この手順では、アドバンスト eDiscovery の新しケースを作成し、Tailspin contract search の結果を分析します。</span><span class="sxs-lookup"><span data-stu-id="426f9-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="426f9-178">左側のナビゲーションで、[**検索&amp;調査**] の下にある [**電子情報開示**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="426f9-179">**[電子情報開示]** ウィンドウで、**[アドバンスト eDiscovery に移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="426f9-180">**[アドバンスト eDiscovery]** タブで、プラス記号のアイコンをクリックして、新しいケースを追加します。</span><span class="sxs-lookup"><span data-stu-id="426f9-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="426f9-p106">**[ケースの追加]** ウィンドウで、**[名前]** に「**Tailspin contract dispute**」と入力して **[OK]** をクリックします。ケースが作成されるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="426f9-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="426f9-183">リスト内の **[Tailspin contract dispute]** ケースをダブルクリックします。 </span><span class="sxs-lookup"><span data-stu-id="426f9-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="426f9-184">[**コンテナー** ] ボックスの一覧で、[ **Tailspin contract] 検索**コンテナーをクリックし、[**プロセス**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-184">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**.</span></span> <span data-ttu-id="426f9-185">処理が完了するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="426f9-185">Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="426f9-186">ウィンドウの下側に **[処理: 完了]** が表示されたら、左側のナビゲーションで **[プロセスの概要]** をクリックして概要を確認します。</span><span class="sxs-lookup"><span data-stu-id="426f9-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="426f9-187">上部のナビゲーションで、**[分析]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426f9-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="426f9-188">**[セットアップ]** ページで、**[テーマ]** の **[最大テーマ数]** に「**3**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="426f9-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="426f9-189">**[分析]** をクリックして、分析が完了するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="426f9-189">Click **Analyze** and wait for the analysis to complete.</span></span> <span data-ttu-id="426f9-190">対象になる母集団、文書、電子メール、および添付ファイルの分析による一連の円グラフが表示されます。</span><span class="sxs-lookup"><span data-stu-id="426f9-190">You should see a series of pie charts with analysis of the target population, documents, emails, and attachments.</span></span> <span data-ttu-id="426f9-191">詳細については、「 [Analyze 結果の表示](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="426f9-191">For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="426f9-192">この環境を使用して、新しいコンテンツ、新しい検索およびケースを作成できるようになりました。また、Office 365 のアドバンスト eDiscovery の実験をさらに進めることができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="426f9-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="426f9-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="426f9-193">See Also</span></span>

[<span data-ttu-id="426f9-194">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="426f9-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="426f9-195">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="426f9-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="426f9-196">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="426f9-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="426f9-197">Office 365 開発/テスト環境の DirSync</span><span class="sxs-lookup"><span data-stu-id="426f9-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="426f9-198">Office 365 開発/テスト環境の Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="426f9-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="426f9-199">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="426f9-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="426f9-200">Office 365 Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="426f9-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


