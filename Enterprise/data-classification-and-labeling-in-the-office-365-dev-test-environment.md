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
ms.openlocfilehash: 66bdbb74ae88e10d5aa4fce2173f9a2b88a15e9b
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741353"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="8b319-103">Office 365 開発/テスト環境でのデータ分類とラベルの作成</span><span class="sxs-lookup"><span data-stu-id="8b319-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="8b319-104">**概要：** Office 365 開発/テスト環境で Azure Information Protection (AIP) クライアントを使用して、データ分類とラベルの設定とデモを行います。</span><span class="sxs-lookup"><span data-stu-id="8b319-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="8b319-105">Azure Information Protection クライアントを使用すると、Office 365 の SharePoint Online フォルダーにドキュメントをアップロードする前に、ドキュメントを分類できます。</span><span class="sxs-lookup"><span data-stu-id="8b319-105">The Azure Information Protection client lets you classify a document before you upload it to a SharePoint Online folder in Office 365.</span></span> <span data-ttu-id="8b319-106">この記事の指示に従って、Azure Information Protection クライアントをインストールし、データ分類をデモします。</span><span class="sxs-lookup"><span data-stu-id="8b319-106">With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification.</span></span> <span data-ttu-id="8b319-107">詳細については、「 [Azure information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b319-107">For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="8b319-108">Office 365 のテストラボガイドスタックにあるすべての記事のビジュアルマップについては、[ここ](http://aka.ms/catlgstack)をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="8b319-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="8b319-109">フェーズ 1: Office 365 開発/テスト環境を構成する</span><span class="sxs-lookup"><span data-stu-id="8b319-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="8b319-110">[Office 365 dev/test environment](office-365-dev-test-environment.md) の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="8b319-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="8b319-111">フェーズ 2:Azure Information Protection 試用版サブスクリプションを追加する</span><span class="sxs-lookup"><span data-stu-id="8b319-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="8b319-112">このフェーズでは、Azure Information Protection を Office 365 開発/テスト環境に追加して、お使いのユーザー アカウントで有効にします。</span><span class="sxs-lookup"><span data-stu-id="8b319-112">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts.</span></span> <span data-ttu-id="8b319-113">[Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx) を構成した場合、このフェーズをスキップします。</span><span class="sxs-lookup"><span data-stu-id="8b319-113">If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase.</span></span> <span data-ttu-id="8b319-114">Enterprise Mobility Suite 試用版サブスクリプションには、Azure Information Protection ライセンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8b319-114">The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="8b319-115">最初に、Azure Information Protection 試用版サブスクリプションの新規登録を行います。</span><span class="sxs-lookup"><span data-stu-id="8b319-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="8b319-116">Azure Information Protection 試用版サブスクリプションの新規登録</span><span class="sxs-lookup"><span data-stu-id="8b319-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="8b319-117">Internet Explorer またはブラウザーで、に[http://admin.microsoft.com](http://admin.microsoft.com)移動して、Office 365 のグローバル管理者アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="8b319-117">In Internet Explorer or your browser, go to [http://admin.microsoft.com](http://admin.microsoft.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="8b319-118">**[Microsoft Office Home]** タブで、**[管理者]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="8b319-119">[Office 365 管理] タブの左側のナビゲーションで **[請求]、[サービスを購入する]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="8b319-p103">**[サービスを購入]** ページで、**[Azure Information Protection Premium P2]** の項目を探します。マウスでポイントし、**[無料試用版の開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-p103">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item. Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="8b319-122">**[注文の確認]** ページで、**[今すぐ実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="8b319-123">**[注文の受領書]** ページで、**[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="8b319-124">次に、すべてのユーザー アカウントで Azure Information Protection  ライセンスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="8b319-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="8b319-125">[Microsoft 365 管理センター] タブで、[**ユーザー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-125">On the Microsoft 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="8b319-126"> ユーザー アカウントの一覧で、全体管理者アカウントを選択し、*\*[製品ライセンス]** で *\*[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="8b319-127">**Azure Information Protection Premium P2** の製品ライセンスを **[オン]** にし、**[保存]** をクリックしてから、**[閉じる]** を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="8b319-128">他のユーザー アカウント (ユーザー 1 ～ユーザー 5) について、手順 2 と 3 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="8b319-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="8b319-129">Office 365 開発/テスト環境には、以下が含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="8b319-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="8b319-130">Office 365 E5 Enterprise と Azure Information Protection の試用版サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="8b319-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="8b319-131">すべてのユーザー アカウントで Office 365 E5 Enterprise と Azure Information Protection の両方が使用可能になっている。</span><span class="sxs-lookup"><span data-stu-id="8b319-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="8b319-132">フェーズ 3:データ分類のデモ </span><span class="sxs-lookup"><span data-stu-id="8b319-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="8b319-133">このフェーズでは、Azure Information Protection クライアントと既定の Azure Information Protection ポリシーを使用してデータ分類をデモします。</span><span class="sxs-lookup"><span data-stu-id="8b319-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="8b319-134">シミュレーション エンタープライズの Office 365 開発/テスト環境を使用する場合は、最初に CLIENT1 で Office 2016 をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b319-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="8b319-135">ブラウザーを使用して、 [Azure portal](http://portal.azure.com)に移動します。</span><span class="sxs-lookup"><span data-stu-id="8b319-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="8b319-136">\*\*[リソース グループ] > \*\*[リソース グループ名] > \*\*[クライアント 1] > \*\*[コネクト] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="8b319-137">CLIENT1 から Internet Explorer を実行し、Office ポータル[http://admin.microsoft.com](http://admin.microsoft.com)に移動して、User5 のアカウント名とパスワードを使用してサインインします。</span><span class="sxs-lookup"><span data-stu-id="8b319-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://admin.microsoft.com](http://admin.microsoft.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="8b319-138">**[Microsoft Office Home]** タブで、**[Office 2016 のインストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="8b319-p104">	画面の指示に従ってダウンロードを実行し、ユーザー アカウント制御のメッセージが表示されたら *\*[はい]** をクリックします。Office がインストールされるのを待ちます。完了したら、*\*[閉じる]** を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-p104">Run the download when prompted and click **Yes** when prompted by User Account Control. Wait for Office to install. When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="8b319-142">次に、Azure Infomation Protection クライアントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="8b319-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="8b319-143">ブラウザーまたは Internet Explorer で、 [Microsoft Azure Information Protection のダウンロードページ](https://www.microsoft.com/download/details.aspx?id=53018)に移動します。</span><span class="sxs-lookup"><span data-stu-id="8b319-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="8b319-144">Office 365 開発/テスト環境の簡易版を使用している場合は、ローカル コンピューターのブラウザーを使用します。</span><span class="sxs-lookup"><span data-stu-id="8b319-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="8b319-145">シミュレーション エンタープライズの Office 365 開発/テスト環境を使用している場合は、CLIENT1 から Internet Explorer を実行します。</span><span class="sxs-lookup"><span data-stu-id="8b319-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="8b319-146">**Microsoft Azure Information Protection** のダウンロード ページで、**[ダウンロード]**、**[AzInfoProtection.exe]**、**[次へ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="8b319-147">指示に従い、AzInfoProtection.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="8b319-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="8b319-148">**[Azure Information Protection のインストール]** クライアント ボックスで、**[同意します]** をクリックし、ユーザー アカウント制御のメッセージが表示されたら、**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="8b319-149">**[正常に完了しました]** ボックスで、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="8b319-150">次に、ドキュメント分類をデモします。</span><span class="sxs-lookup"><span data-stu-id="8b319-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="8b319-151">タスクバーの **[Word]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="8b319-152">指示に従い、User5 のアカウント名とパスワードでサインインします。</span><span class="sxs-lookup"><span data-stu-id="8b319-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="8b319-153">CLIENT1 で Office 2016 をインストールしたばかりの場合、**[はじめに]** のボックスで **[同意します]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="8b319-154">**[空白の文書]** をクリックします。 </span><span class="sxs-lookup"><span data-stu-id="8b319-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="8b319-155">**[ホーム]** タブのリボンの **[保護]** セクションとドキュメント分類の行に注意します。</span><span class="sxs-lookup"><span data-stu-id="8b319-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="8b319-156">空白の文書にテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="8b319-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="8b319-157">**[ファイル] > [保存]** をクリックし、名前として「**BeforeAIP**」を入力し、**[OK]** をクリックします。 </span><span class="sxs-lookup"><span data-stu-id="8b319-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="8b319-158">ドキュメント分類の行で、**[シークレット]** の下矢印をクリックし、**[すべての会社]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="8b319-159">**[ファイル] > [名前を付けて保存]** をクリックし、「**BeforeAIP**」と入力して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="8b319-160">タスクバーの **[ファイル エクスプローラー]** をクリックして、**[ドキュメント]** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="8b319-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="8b319-161">**BeforeAIP** と **AfterAIP** のドキュメントのファイル サイズの違いに注意します。</span><span class="sxs-lookup"><span data-stu-id="8b319-161">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents.</span></span> <span data-ttu-id="8b319-162">beforeaip ドキュメントは、分類情報を持っているため、大きくなります。</span><span class="sxs-lookup"><span data-stu-id="8b319-162">The AfterAIP document is larger because it has the classification information.</span></span>
    
<span data-ttu-id="8b319-163">次に、すべてのユーザーにサポート サイト コレクションへのアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="8b319-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="8b319-164">**[Microsoft Office Home]** タブで **[SharePoint]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="8b319-165">**[SharePoint]** タブから **[サポート サイト コレクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="8b319-166">右上部分の **[設定]** アイコンをクリックし、**[共有アイテム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="8b319-167">[**共有 ' サポートサイトコレクション '**] で、[**詳細設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="8b319-168">SharePoint グループの一覧で **[サポート サイト コレクションのメンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="8b319-169">**[ユーザーとグループ]** ページで、**[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="8b319-170">[**共有 ' サポートサイトコレクション '**] で、「 **everyone**」と入力し、[**外部ユーザー以外のすべてのユーザー**] をクリックして、[共有] をクリックし**ます。**</span><span class="sxs-lookup"><span data-stu-id="8b319-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="8b319-171">**[ユーザーとグループ]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="8b319-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="8b319-172">次に、User5 のアカウントでサインインし、AIP で保護されたドキュメントをサポート サイト コレクションのドキュメント フォルダーにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="8b319-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="8b319-173">**[Microsoft Office Home]** タブの右上部分の [ユーザー] アイコンをクリックし、**[サインアウト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="8b319-174">[http://admin.microsoft.com](http://admin.microsoft.com) に移動します。</span><span class="sxs-lookup"><span data-stu-id="8b319-174">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="8b319-175">**Office 365 のサインイン**ページで、User5 のアカウント名をクリックして、サインインします。</span><span class="sxs-lookup"><span data-stu-id="8b319-175">On the **Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="8b319-176">**[Microsoft Office Home]** タブで、**[SharePoint] > [サポート サイト コレクション] > [ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="8b319-177">**[ドキュメント]** をクリックし、**[アップロード]** をクリックし、**AfterAIP** ドキュメントを選択して **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8b319-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="8b319-178">サポート サイト コレクションのドキュメント フォルダーの AfterAIP.docx を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b319-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="8b319-179">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b319-179">See Also</span></span>

[<span data-ttu-id="8b319-180">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="8b319-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="8b319-181">Office 365 と EMS の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="8b319-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="8b319-182">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="8b319-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


