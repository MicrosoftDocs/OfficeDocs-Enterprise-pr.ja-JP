---
title: "Office 365 の開発/テスト環境のアドバンスト eDiscovery"
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
description: "概要: は、構成して、Office 365 の開発/テスト環境でサンプル データを Office 365 の高度な電子的証拠開示を実演します。"
ms.openlocfilehash: c55a466f05eba4e9f06ce2930dfc7c762d7fceae
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a><span data-ttu-id="1d6f5-103">Office 365 の開発/テスト環境のアドバンスト eDiscovery</span><span class="sxs-lookup"><span data-stu-id="1d6f5-103">Advanced eDiscovery for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="1d6f5-104">**の概要:**構成して、Office 365 の開発/テスト環境でサンプル データを Office 365 の高度な電子的証拠開示を実演します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-104">**Summary:** Configure and demonstrate Office 365 Advanced eDiscovery with sample data in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="1d6f5-p101">Office 365 の高度な電子情報開示をすばやく検索して、電子メールやドキュメントなど、Office 365 に格納されているデータの間で関連情報を分析できます。訴訟の状況で特に膨大な時間と経費を節約できます。詳細については、[電子的証拠開示の Office 365 の詳細](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-p101">Office 365 Advanced eDiscovery allows you to quickly find and analyze relevant information across the data that is stored in Office 365, including email and documents. This can save enormous amounts of time and expense, especially in litigation situations. For more information, see [Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4).</span></span>
  
<span data-ttu-id="1d6f5-108">この記事の手順では、架空の契約問題に関するデータの小さなセットを作成し、そのデータをアドバンスト eDiscovery で分析します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-108">With the instructions in this article, you create a small set of data for a fictional contract dispute and analyze it with Advanced eDiscovery.</span></span>
  
> [!TIP]
> <span data-ttu-id="1d6f5-109">
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-109">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="1d6f5-110">フェーズ 1: Office 365 の開発/テスト環境を作成する</span><span class="sxs-lookup"><span data-stu-id="1d6f5-110">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="1d6f5-111">最小要件、軽量化による高度な電子的証拠開示をテストする場合は、フェーズ 2 と[Office 365 の開発/テスト環境](office-365-dev-test-environment.md)の第 3 段階で指示します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-111">If you just want to test Advanced eDiscovery in a lightweight way with the minimum requirements, follow the instructions in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="1d6f5-112">シミュレートされた企業で高度な電子的証拠開示をテストする場合は、 [Office 365 の開発/テスト環境のディレクトリ同期](dirsync-for-your-office-365-dev-test-environment.md)に指示します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-112">If you want to test Advanced eDiscovery in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="1d6f5-p102">高度な電子的証拠開示のテストは、シミュレートされたエンタープライズ環境には、シミュレートされたイントラネットをインターネットに接続されていると Windows サーバーの AD フォレストの場合、ディレクトリ同期します。ここでは、オプションを表す一般的な組織環境でのテストや実験を行うことができますように。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-p102">Testing Advanced eDiscovery does not require the simulated enterprise environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can perform testing and experimentation in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a><span data-ttu-id="1d6f5-115">フェーズ 2:アドバンスト eDiscovery 用のサンプル データを作成する</span><span class="sxs-lookup"><span data-stu-id="1d6f5-115">Phase 2: Create example data for Advanced eDiscovery</span></span>

<span data-ttu-id="1d6f5-116">この手順では、電子メール メッセージを作成します。このメッセージをアドバンスト eDiscovery のケースで分析することになります。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-116">In this procedure, you create email messages that will you later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="1d6f5-117">Internet Explorer を開き、[Office 365 の開発/テスト環境](office-365-dev-test-environment.md)の第 2 フェーズで作成した Outlook のアカウントを[https://outlook.com](https://outlook.com)にサインインします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-117">Open Internet Explorer and sign in at [https://outlook.com](https://outlook.com) to the Outlook account you created in Phase 2 of[Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
    
  - <span data-ttu-id="1d6f5-118">ライトウェイトの開発/テスト環境を使用している場合は、Internet Explorer のプライベート セッションを開いて、ローカル コンピューターからサインインします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-118">If you are using the lightweight dev/test environment, open a private session of Internet Explorer and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="1d6f5-119">シミュレートされたエンタープライズ開発/テスト環境を使用する場合は、CLIENT1 バーチャル マシンに接続して、CLIENT1 からサインインし、Azure ポータル ([https://portal.azure.com](https://portal.azure.com)) を使用します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-119">If you are using the simulated enterprise dev/test environment, use the Azure portal ([https://portal.azure.com](https://portal.azure.com)) to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="1d6f5-120">**Outlook のメール**] タブで [**新規**を] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-120">On the **Outlook Mail** tab, click **New**.</span></span>
    
3. <span data-ttu-id="1d6f5-p103">試用版サブスクリプションの User6 のアカウントの電子メール アドレスを入力**する**」( **user6 @** 。<organization name> **. onmicrosoft.com**)。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-p103">In **To**, type the email address of the User6 account of your trial subscription ( **user6@.**<organization name> **.onmicrosoft.com**).</span></span>
    
4. <span data-ttu-id="1d6f5-123">件名、**テスト電子メール 1**を入力します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-123">For the subject, type **Test email 1**.</span></span>
    
5. <span data-ttu-id="1d6f5-124">本文には、 **Tailspin 契約のドラフト**を入力し、[**送信**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-124">In the body, type **Tailspin contract draft**, and then click **Send**.</span></span>
    
6. <span data-ttu-id="1d6f5-125">**Outlook のメール**] タブで [**新規**を] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-125">On the **Outlook Mail** tab, click **New**.</span></span>
    
7. <span data-ttu-id="1d6f5-126">****試用版サブスクリプションの User6 のアカウントの電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-126">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
8. <span data-ttu-id="1d6f5-127">件名、**テスト電子メール 2**を入力します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-127">For the subject, type **Test email 2**.</span></span>
    
9. <span data-ttu-id="1d6f5-128">本文に、 **Tailspin ランチ ミーティング**の場合は、入力し、**送信**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-128">In the body, type **Tailspin lunch meeting**, and then click **Send**.</span></span>
    
10. <span data-ttu-id="1d6f5-129">**Outlook のメール**] タブで [**新規**を] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-129">On the **Outlook Mail** tab, click **New**.</span></span>
    
11. <span data-ttu-id="1d6f5-130">****試用版サブスクリプションの User6 のアカウントの電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-130">In **To**, type the email address of the User6 account of your trial subscription.</span></span>
    
12. <span data-ttu-id="1d6f5-131">件名、**テスト電子メール 3**を入力します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-131">For the subject, type **Test email 3**.</span></span>
    
13. <span data-ttu-id="1d6f5-132">本文には、 **Tailspin コントラクトの不一致**を入力し、[**送信**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-132">In the body, type **Tailspin contract disagreement**, and then click **Send**.</span></span>
    
14. <span data-ttu-id="1d6f5-133">右上隅で [ユーザー] アイコンをクリックし、[**サインアウト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-133">Click the user icon in the upper right corner, and then click **Sign out**.</span></span>
    
15. <span data-ttu-id="1d6f5-134">新しいタブを開くし、アカウント名と、試用版サブスクリプションの User6 のアカウントのパスワードを Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-134">Open a new tab and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with the account name and password of the User6 account of your trial subscription.</span></span>
    
16. <span data-ttu-id="1d6f5-135">**Office 365 ポータル**] タブで、[**メール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-135">On the **Office 365 portal** tab, click **Mail**.</span></span>
    
17. <span data-ttu-id="1d6f5-136">[場所] タブの [ **Outlook のメール - User6 -** User6 が Outlook の電子メール アカウントからすべての 3 つの電子メールを受信したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-136">On the **Mail - User6 - Outlook** tab, verify that User6 received all three emails from the Outlook email account.</span></span>
    
18. <span data-ttu-id="1d6f5-137">User6 は、 **Office 365 ポータル] タブ**に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-137">Switch back to the **Office 365 portal tab** for User6.</span></span>
    
19. <span data-ttu-id="1d6f5-138">右上隅で [ユーザー] アイコンをクリックし] をクリックし、**からサインアウトします**。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-138">Click the user icon in the upper right corner, and then click **Sign out.**</span></span>
    
<span data-ttu-id="1d6f5-139">この手順では、2 つの Word 文書を作成します。この文書をアドバンスト eDiscovery のケースで分析することになります。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-139">In this procedure, you create two Word documents that will you will later analyze in an Advanced eDiscovery case.</span></span>
  
1. <span data-ttu-id="1d6f5-140">[ **Office** ] ページで、グローバル ・ アドミニストレータ ・ アカウントの資格情報で**サインインするのには、**記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-140">On the **Office** page, click **Sign in,** sign in with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="1d6f5-141">新しいタブでは、本番環境の SharePoint サイトの URL へのアクセス: **https://** <fictional organization name> **.sharepoint.com/sites/production**</span><span class="sxs-lookup"><span data-stu-id="1d6f5-141">On a new tab, access the URL of your Production SharePoint site: **https://**<fictional organization name> **.sharepoint.com/sites/production**</span></span>
    
3. <span data-ttu-id="1d6f5-142">**運用サイト コレクション**] タブの [**ドキュメント**] の下でをクリックして**新規 > Word 文書**。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-142">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
4. <span data-ttu-id="1d6f5-143">**Word のオンライン**のページでは、 **Tailspin ドラフト契約**を入力、[**保存された**が、タイトルに表示されるまで待ってから、**オンラインの Word**の [ページ] タブを閉じてください。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-143">On the **Word Online** page, type **Tailspin draft contract**, wait until it displays **Saved** in the title, and then close the **Word Online** page tab.</span></span>
    
5. <span data-ttu-id="1d6f5-144">**運用サイト コレクション**] タブの [**ドキュメント**] の下でをクリックして**新規 > Word 文書**。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-144">On the **Production site collection** tab, under **Documents**, click **New > Word Document**.</span></span>
    
6. <span data-ttu-id="1d6f5-145">**Word の [オンライン**] タブで、[ **Tailspin 契約争議のノート**を入力、**保存された**が、タイトルに表示されるまでの待機し、 **Word の [オンライン**] タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-145">On the **Word Online** tab, type **Tailspin contract dispute notes**, wait until it displays **Saved** in the title, and then close the **Word Online** tab.</span></span>
    
7. <span data-ttu-id="1d6f5-146">**運用サイト コレクション**] タブで、[ドキュメントの一覧で、**文書**と**文書 1**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-146">On the **Production site collection** tab, you should see **Document** and **Document1** in the list of documents.</span></span>
    
8. <span data-ttu-id="1d6f5-147">**運用サイト コレクション**] タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-147">Close the **Production site collection** tab.</span></span>
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a><span data-ttu-id="1d6f5-148">フェーズ 3: 使用して高度な電子的証拠開示の法的な争い</span><span class="sxs-lookup"><span data-stu-id="1d6f5-148">Phase 3: Use Advanced eDiscovery for a legal dispute</span></span>

<span data-ttu-id="1d6f5-p104">残念ながら、組織と Tailspin toys 社の契約紛争は、法的措置のポイントに達した。この手順で作成して構成する、高度な電子的証拠開示のケースを検索し、電子メールと「Tailspin 契約」のテキストを含むドキュメントを分析します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-p104">Unfortunately, a contract dispute between your organization and Tailspin Toys has reached the point of legal action. In this procedure, you create and configure an Advanced eDiscovery case to search for and analyze email and documents that contain the text "Tailspin contract".</span></span>
  
<span data-ttu-id="1d6f5-151">アドバンスト eDiscovery を使用するためのプロセスは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-151">The process for using Advanced eDiscovery is the following:</span></span>
  
- <span data-ttu-id="1d6f5-152">セキュリティで検索を作成する&amp;コンプライアンス センターが、その結果を分析し、高度な電子的証拠開示の結果を準備します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-152">Create a search in the Security &amp; Compliance center, analyze its results, and then prepare the results for Advanced eDiscovery.</span></span>
    
- <span data-ttu-id="1d6f5-153">アドバンスト eDiscovery でケースを作成して構成し、検索結果を分析します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-153">Create and configure a case in Advanced eDiscovery and analyze the search results.</span></span>
    
<span data-ttu-id="1d6f5-154">この手順で、セキュリティで検索を作成する&amp;コンプライアンスの中央に「Tailspin 契約」では、検索結果を高度な電子的証拠開示の結果を準備します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-154">In this procedure, you create a search in the Security &amp; Compliance center for "Tailspin contract", look at the results, and then prepare the results for Advanced eDiscovery.</span></span>
  
1. <span data-ttu-id="1d6f5-155">**Office 365 ポータル**] タブから、[**管理**を] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-155">From the **Office 365 portal** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="1d6f5-156">センターの管理] タブの左側のナビゲーションでをクリックして**管理センター > コンプライアンス**。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-156">In the left navigation of the Admin center tab, click **Admin centers > Compliance**.</span></span>
    
3. <span data-ttu-id="1d6f5-157">上の**セキュリティ&amp;準拠**] タブで、[**アクセス許可**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-157">On the **Security &amp; Compliance** tab, click **Permissions**.</span></span>
    
4. <span data-ttu-id="1d6f5-158">**アクセス許可**] ボックスの一覧では、**組織の管理**をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-158">In the **Permissions** list, double-click **Organization Management**.</span></span>
    
5. <span data-ttu-id="1d6f5-159">**ロール グループ**] ウィンドウで [**メンバー**] で、プラス記号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-159">In the **Role Group** window, under **Members**, click the plus sign.</span></span>
    
6. <span data-ttu-id="1d6f5-160">**メンバーの選択]**ウィンドウで、あなたの管理者アカウントの名前をダブルクリックし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-160">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
7. <span data-ttu-id="1d6f5-161">**ロール グループ**] ウィンドウで [**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-161">In the **Role Group** window, click **Save**.</span></span>
    
8. <span data-ttu-id="1d6f5-162">**アクセス許可**] ボックスの一覧では、**電子的証拠開示マネージャー**をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-162">In the **Permissions** list, double-click **eDiscovery Manager**.</span></span>
    
9. <span data-ttu-id="1d6f5-163">**ロール グループ**] ウィンドウで、**管理者の電子的証拠開示**では、下にあるプラス アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-163">In the **Role Group** window, under **eDiscovery Administrator**, click the plus icon.</span></span>
    
10. <span data-ttu-id="1d6f5-164">**メンバーの選択]**ウィンドウで、あなたの管理者アカウントの名前をダブルクリックし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-164">In the **Select Members** window, double-click the name of your administrator account, and then click **OK**.</span></span>
    
11. <span data-ttu-id="1d6f5-165">**ロール グループ**] ウィンドウで [**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-165">In the **Role Group** window, click **Save**.</span></span>
    
12. <span data-ttu-id="1d6f5-166">左側のナビゲーションでをクリックして**検索&amp;調査 > コンテンツの検索**。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-166">In the left navigation, click **Search &amp; Investigation > Content search**.</span></span>
    
13. <span data-ttu-id="1d6f5-167">プラス記号のアイコンをクリックして、検索を追加します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-167">Click the plus icon to add a search.</span></span>
    
14. <span data-ttu-id="1d6f5-168">**新しい検索**ウィンドウでは、 **Tailspin 契約検索****名**を入力します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-168">In the **New search** window, type **Tailspin contract search** in **Name**.</span></span>
    
15. <span data-ttu-id="1d6f5-169">**場所を指定して検索することですか?** **、あらゆる場所を検索**選択**Exchange**、 **SharePoint**、および**パブリック フォルダー**をクリックし、[クリックして**次**。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-169">In **Where do you want us to look?**, click **Search everywhere,** select **Exchange**, **SharePoint**, and **Public Folders**, and then click **Next.**</span></span>
    
16. <span data-ttu-id="1d6f5-170">**たい項目を検索することですか?**と**Tailspin の契約**を入力し、[**検索**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-170">In **What do you want us to look for?**, type **Tailspin contract**, and then click **Search**.</span></span>
    
17. <span data-ttu-id="1d6f5-171">検索の一覧では、 **Tailspin 契約検索**名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-171">In the list of searches, click the **Tailspin contract search** name.</span></span>
    
18. <span data-ttu-id="1d6f5-p105">**Tailspin 契約の検索**ウィンドウで、[**結果**] で、**検索結果のプレビュー**をクリックします。生産の SharePoint サイト (**ドキュメント****文書 1**) と User6 に**テスト ・ メール 1**と**3 のテスト メール**のメールの 2 つのドキュメントの一覧を示すウィンドウが表示されます。ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-p105">In the **Tailspin contract search** pane, click **Preview search results** under **Results**. You should see a window listing the two documents on the Production SharePoint site ( **Document** and **Document1**) and the **Test email 1** and **Test email 3** emails to User6. Close the window.</span></span>
    
19. <span data-ttu-id="1d6f5-175">[**コンテンツ検索**] ウィンドウで、[**高度な電子的証拠開示の分析結果****分析の結果のプレビュー**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-175">In the **Content search** pane, under **Analyze results with Advanced eDiscovery**, click **Preview results for analysis**.</span></span>
    
20. <span data-ttu-id="1d6f5-176">**Tailspin 契約検索の結果が検索の準備**] ウィンドウで、**準備**] をクリックしを完了するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-176">In the **Prepare the search results for Tailspin contract search** window, click **Prepare** and wait for it to complete.</span></span>
    
<span data-ttu-id="1d6f5-177">この手順では、アドバンスト eDiscovery の新しケースを作成し、Tailspin contract search の結果を分析します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-177">In this procedure, you create a new case for Advanced eDiscovery and analyze the Tailspin contract search results.</span></span>
  
1. <span data-ttu-id="1d6f5-178">左側のナビゲーションでは、クリックしてで**電子的証拠開示****検索&amp;調査**。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-178">In the left navigation, click **eDiscovery** under **Search &amp; Investigation**.</span></span>
    
2. <span data-ttu-id="1d6f5-179">**電子的証拠開示**のウィンドウで [**高度な電子的証拠開示**します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-179">In the **eDiscovery** pane, click **Go to Advanced eDiscovery**.</span></span>
    
3. <span data-ttu-id="1d6f5-180">**電子的証拠開示の詳細**] タブで、新しいサポート案件を追加するのにはプラス記号のアイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-180">In the **Advanced eDiscovery** tab, click the plus icon to add a new case.</span></span>
    
4. <span data-ttu-id="1d6f5-p106">**追加の場合**のウィンドウでは、[**名前**] **Tailspin 契約争議**を入力し、し、[ **OK**] をクリックします。ケースを作成するを待ちます。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-p106">In the **Add case** pane, type **Tailspin contract dispute** in **Name**, and then click **OK**. Wait for the case to be created.</span></span>
    
5. <span data-ttu-id="1d6f5-183">**Tailspin 契約紛争**ケース、ボックスの一覧でをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-183">Double click the **Tailspin contract dispute** case in the list.</span></span>
    
6. <span data-ttu-id="1d6f5-p107">**コンテナー** ] ボックスの一覧で**Tailspin 契約検索**コンテナーをクリックし、[**プロセス**] をクリックします。処理が完了するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-p107">In the **Container** list, click the **Tailspin contract search** container, and then click **Process**. Wait for the processing to complete.</span></span>
    
7. <span data-ttu-id="1d6f5-186">**プロセス: 完了した**が表示されますウィンドウの下部には、概要を表示するのには左側のナビゲーションでの**プロセスの概要**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-186">When **Process: completed** appears at the bottom of the window, click **Process summary** in the left navigation to see a summary.</span></span>
    
8. <span data-ttu-id="1d6f5-187">上部のナビゲーションでは、[**分析**を] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-187">In the top navigation, click **Analyze**.</span></span>
    
9. <span data-ttu-id="1d6f5-188">[**セットアップ**] ページの [**テーマ**] の下には、**テーマの最大数**に**3**を入力します。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-188">On the **Setup** page, under **Themes**, type **3** in **Max number of themes**.</span></span>
    
10. <span data-ttu-id="1d6f5-p108">**分析**] をクリックし、分析を完了するまで待機します。ターゲット ・ カタログの作成、ドキュメント、電子メール、および添付ファイルの分析と円グラフの系列を参照してくださいする必要があります。詳細については、[結果の分析を表示する](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-p108">Click **Analyze** and wait for the analysis to complete. You should see a series of pie charts with analysis of the target population, documents, emails, and attachments. For more information, see [Viewing Analyze results](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e).</span></span>
    
<span data-ttu-id="1d6f5-192">この環境を使用して、新しいコンテンツ、新しい検索およびケースを作成できるようになりました。また、Office 365 のアドバンスト eDiscovery の実験をさらに進めることができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="1d6f5-192">You can now use this environment to create new content, new searches and cases, and experiment further with Advanced eDiscovery in Office 365.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1d6f5-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d6f5-193">See Also</span></span>

[<span data-ttu-id="1d6f5-194">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="1d6f5-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="1d6f5-195">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="1d6f5-195">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="1d6f5-196">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="1d6f5-196">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="1d6f5-197">Office 365 開発/テスト環境の DirSync</span><span class="sxs-lookup"><span data-stu-id="1d6f5-197">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="1d6f5-198">Office 365 開発/テスト環境の Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="1d6f5-198">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="1d6f5-199">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="1d6f5-199">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="1d6f5-200">Office 365 の高度な電子情報開示</span><span class="sxs-lookup"><span data-stu-id="1d6f5-200">Office 365 Advanced eDiscovery</span></span>](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


