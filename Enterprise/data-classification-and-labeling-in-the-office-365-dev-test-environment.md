---
title: Office 365 開発/テスト環境でのデータ分類とラベルの作成
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
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: 概要：Office 365 開発/テスト環境で Azure Information Protection (AIP) クライアントを使用して、データ分類とラベルの設定とデモを行います。
ms.openlocfilehash: 69526f8bf0ae0b6cc7509653cfaa72581e10dbfe
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897440"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="eccd7-103">Office 365 開発/テスト環境でのデータ分類とラベルの作成</span><span class="sxs-lookup"><span data-stu-id="eccd7-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="eccd7-104">**概要：** Office 365 開発/テスト環境で Azure Information Protection (AIP) クライアントを使用して、データ分類とラベルの設定とデモを行います。</span><span class="sxs-lookup"><span data-stu-id="eccd7-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="eccd7-p101">Azure の情報保護のクライアントでは、Office 365 で SharePoint Online フォルダーにアップロードする前にドキュメントを分類することができます。この資料の手順についてでは、Azure の情報保護のクライアントをインストールして、データのクラス分けを実演します。詳細については、 [Azure の情報の保護](https://www.microsoft.com/cloud-platform/azure-information-protection)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eccd7-p101">The Azure Information Protection client lets you classify a document before you upload it to a SharePoint Online folder in Office 365. With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification. For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="eccd7-108">[ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="eccd7-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="eccd7-109">フェーズ 1: Office 365 開発/テスト環境を構築する</span><span class="sxs-lookup"><span data-stu-id="eccd7-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="eccd7-110">[Office 365 dev/test environment](office-365-dev-test-environment.md) の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="eccd7-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="eccd7-111">フェーズ 2:Azure Information Protection 試用版サブスクリプションを追加する</span><span class="sxs-lookup"><span data-stu-id="eccd7-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="eccd7-p102">このフェーズでは、Azure Information Protection を Office 365 開発/テスト環境に追加して、お使いのユーザー アカウントで有効にします。[Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx) を構成した場合、このフェーズをスキップします。Enterprise Mobility Suite 試用版サブスクリプションには、Azure Information Protection ライセンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="eccd7-p102">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts. If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase. The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="eccd7-115">最初に、Azure Information Protection 試用版サブスクリプションの新規登録を行います。</span><span class="sxs-lookup"><span data-stu-id="eccd7-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="eccd7-116">Azure Information Protection 試用版サブスクリプションの新規登録</span><span class="sxs-lookup"><span data-stu-id="eccd7-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="eccd7-117">移動するのには、Internet Explorer、またはお使いのブラウザーは、[http://portal.office.com](http://portal.office.com)と、Office 365 のグローバル管理者アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-117">In Internet Explorer or your browser, go to [http://portal.office.com](http://portal.office.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="eccd7-118">**[Microsoft Office Home]** タブで、**[管理者]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="eccd7-119">[Office 365 管理] タブの左側のナビゲーションで **[請求]、[サービスを購入する]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="eccd7-p103">**[サービスを購入]** ページで、**[Azure Information Protection Premium P2]** の項目を探します。マウスでポイントし、**[無料試用版の開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-p103">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item. Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="eccd7-122">**[注文の確認]** ページで、 **[今すぐ実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="eccd7-123">**[注文の受領書]** ページで、**[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="eccd7-124">次に、すべてのユーザー アカウントで Azure Information Protection  ライセンスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="eccd7-125">	[Office 365 管理センター] タブで *\*[ユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-125">On the Office 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="eccd7-126"> ユーザー アカウントの一覧で、全体管理者アカウントを選択し、*\*[製品ライセンス]** で *\*[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="eccd7-127">**Azure Information Protection Premium P2** の製品ライセンスを **[オン]** にし、**[保存]** をクリックしてから、**[閉じる]** を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="eccd7-128">他のユーザー アカウント (ユーザー 1 ～ユーザー 5) について、手順 2 と 3 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="eccd7-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="eccd7-129">Office 365 開発/テスト環境には、以下が含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="eccd7-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="eccd7-130">Office 365 E5 Enterprise と Azure Information Protection の試用版サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="eccd7-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="eccd7-131">すべてのユーザー アカウントで Office 365 E5 Enterprise と Azure Information Protection の両方が使用可能になっている。</span><span class="sxs-lookup"><span data-stu-id="eccd7-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="eccd7-132">フェーズ 3:データ分類のデモ </span><span class="sxs-lookup"><span data-stu-id="eccd7-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="eccd7-133">このフェーズでは、Azure Information Protection クライアントと既定の Azure Information Protection ポリシーを使用してデータ分類をデモします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="eccd7-134">シミュレーション エンタープライズの Office 365 開発/テスト環境を使用する場合は、最初に CLIENT1 で Office 2016 をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eccd7-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="eccd7-135">お使いのブラウザーを使用し、 [Azure ポータル](http://portal.azure.com)に移動します。</span><span class="sxs-lookup"><span data-stu-id="eccd7-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="eccd7-136">\*\*[リソース グループ] > \*\*[リソース グループ名] > \*\*[クライアント 1] > \*\*[コネクト] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="eccd7-137">CLIENT1 から Internet Explorer を実行で Office のポータルには、 [http://portal.office.com](http://portal.office.com)、User5 アカウント名とパスワードを使用してサインインしているとします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://portal.office.com](http://portal.office.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="eccd7-138">**[Microsoft Office Home]** タブで、**[Office 2016 のインストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="eccd7-p104">	画面の指示に従ってダウンロードを実行し、ユーザー アカウント制御のメッセージが表示されたら *\*[はい]** をクリックします。Office がインストールされるのを待ちます。完了したら、*\*[閉じる]** を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-p104">Run the download when prompted and click **Yes** when prompted by User Account Control. Wait for Office to install. When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="eccd7-142">次に、Azure Infomation Protection クライアントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="eccd7-143">ブラウザーまたは Internet Explorer、 [Microsoft Azure の情報保護のダウンロード ページ](https://www.microsoft.com/download/details.aspx?id=53018)に移動します。</span><span class="sxs-lookup"><span data-stu-id="eccd7-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="eccd7-144">Office 365 開発/テスト環境の簡易版を使用している場合は、ローカル コンピューターのブラウザーを使用します。</span><span class="sxs-lookup"><span data-stu-id="eccd7-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="eccd7-145">シミュレーション エンタープライズの Office 365 開発/テスト環境を使用している場合は、CLIENT1 から Internet Explorer を実行します。</span><span class="sxs-lookup"><span data-stu-id="eccd7-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="eccd7-146">**Microsoft Azure Information Protection** のダウンロード ページで、**[ダウンロード]**、**[AzInfoProtection.exe]**、**[次へ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="eccd7-147">指示に従い、AzInfoProtection.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="eccd7-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="eccd7-148">**[Azure Information Protection のインストール]** クライアント ボックスで、**[同意します]** をクリックし、ユーザー アカウント制御のメッセージが表示されたら、**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="eccd7-149">**[正常に完了しました]** ボックスで、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="eccd7-150">次に、ドキュメント分類をデモします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="eccd7-151">タスクバーの **[Word]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="eccd7-152">指示に従い、User5 のアカウント名とパスワードでサインインします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="eccd7-153">CLIENT1 で Office 2016 をインストールしたばかりの場合、**[はじめに]** のボックスで **[同意します]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="eccd7-154">**[空白の文書]** をクリックします。 </span><span class="sxs-lookup"><span data-stu-id="eccd7-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="eccd7-155">**[ホーム]** タブのリボンの **[保護]** セクションとドキュメント分類の行に注意します。</span><span class="sxs-lookup"><span data-stu-id="eccd7-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="eccd7-156">空白の文書にテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="eccd7-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="eccd7-157">**[ファイル] > [保存]** をクリックし、名前として「**BeforeAIP**」を入力し、**[OK]** をクリックします。 </span><span class="sxs-lookup"><span data-stu-id="eccd7-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="eccd7-158">ドキュメント分類の行で、**[シークレット]** の下矢印をクリックし、**[すべての会社]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="eccd7-159">**[ファイル] > [名前を付けて保存]** をクリックし、「**BeforeAIP**」と入力して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="eccd7-160">タスクバーの **[ファイル エクスプローラー]** をクリックして、**[ドキュメント]** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="eccd7-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="eccd7-p105">**BeforeAIP**と**AfterAIP**のドキュメントの別のファイルのサイズに注意してください。AfterAIP ドキュメントは、分類情報が含まれているために大きくなります。</span><span class="sxs-lookup"><span data-stu-id="eccd7-p105">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents. The AfterAIP document is larger because it has the classification information.</span></span>
    
<span data-ttu-id="eccd7-163">次に、すべてのユーザーにサポート サイト コレクションへのアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="eccd7-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="eccd7-164">**[Microsoft Office Home]** タブで **[SharePoint]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="eccd7-165">**[SharePoint]** タブから **[サポート サイト コレクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="eccd7-166">右上部分の **[設定]** アイコンをクリックし、**[共有アイテム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="eccd7-167">**共有 'サポート サイト コレクション'** の場合は、[**詳細**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="eccd7-168">SharePoint グループの一覧で **[サポート サイト コレクションのメンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="eccd7-169">**[ユーザーとグループ]** ページで、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="eccd7-170">**共有 'サポート サイト コレクション'**、**すべてのユーザー**を入力、**外部のユーザーを除くすべて**] をクリックし、**共有します**。</span><span class="sxs-lookup"><span data-stu-id="eccd7-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="eccd7-171">**[ユーザーとグループ]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="eccd7-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="eccd7-172">次に、User5 のアカウントでサインインし、AIP で保護されたドキュメントをサポート サイト コレクションのドキュメント フォルダーにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="eccd7-173">**[Microsoft Office Home]** タブの右上部分の [ユーザー] アイコンをクリックし、**[サインアウト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="eccd7-174">[http://portal.office.com](http://portal.office.com) に移動します。</span><span class="sxs-lookup"><span data-stu-id="eccd7-174">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="eccd7-175">**Office 365 のサインイン**ページで、User5 のアカウント名をクリックし、サインインします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-175">On the **Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="eccd7-176">**[Microsoft Office Home]** タブで、**[SharePoint] > [サポート サイト コレクション] > [ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="eccd7-177">**[ドキュメント]** をクリックし、**[アップロード]** をクリックし、**AfterAIP** ドキュメントを選択して **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eccd7-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="eccd7-178">サポート サイト コレクションのドキュメント フォルダーの AfterAIP.docx を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eccd7-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="eccd7-179">関連項目</span><span class="sxs-lookup"><span data-stu-id="eccd7-179">See Also</span></span>

[<span data-ttu-id="eccd7-180">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="eccd7-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="eccd7-181">Office 365 と EMS の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="eccd7-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="eccd7-182">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="eccd7-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


