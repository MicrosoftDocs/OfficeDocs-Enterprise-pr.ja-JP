---
title: "Office 365 開発/テスト環境でのデータ分類とラベルの作成"
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
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: "概要: は、構成し、データのクラス分けと Azure の情報の保護 (AIP) クライアントを使用して、Office 365 の開発/テスト環境でのラベル付けについて説明します。"
ms.openlocfilehash: 7243acecca0dd4c39ff6ef2aecd25091f25f2f53
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2018
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a><span data-ttu-id="fe0e0-103">Office 365 開発/テスト環境でのデータ分類とラベルの作成</span><span class="sxs-lookup"><span data-stu-id="fe0e0-103">Data classification and labeling in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="fe0e0-104">**の概要:**構成し、データのクラス分けと Azure の情報の保護 (AIP) クライアントを使用して、Office 365 の開発/テスト環境でのラベル付けについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-104">**Summary:** Configure and demonstrate data classification and labeling using the Azure Information Protection (AIP) client in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="fe0e0-p101">Azure の情報保護のクライアントを使用すると、Office 365 で SharePoint Online フォルダーにアップロードする前にドキュメントを分類できます。この資料の手順についてでは、Azure の情報保護のクライアントをインストールして、データのクラス分けを実演します。詳細については、 [Azure の情報の保護](https://www.microsoft.com/cloud-platform/azure-information-protection)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-p101">The Azure Information Protection client allows you to classify a document before you upload it to a SharePoint Online folder in Office 365. With the instructions in this article, you install the Azure Information Protection client and demonstrate data classification. For more information, see [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection).</span></span>
  
> [!TIP]
> <span data-ttu-id="fe0e0-108">
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="fe0e0-109">フェーズ 1: Office 365 開発/テスト環境を構築する</span><span class="sxs-lookup"><span data-stu-id="fe0e0-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="fe0e0-110">[Office 365 の開発/テスト環境](office-365-dev-test-environment.md)での指示に従います。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-110">Follow the instructions in [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a><span data-ttu-id="fe0e0-111">フェーズ 2:Azure Information Protection 試用版サブスクリプションを追加する</span><span class="sxs-lookup"><span data-stu-id="fe0e0-111">Phase 2: Add the Azure Information Protection trial subscription</span></span>

<span data-ttu-id="fe0e0-p102">このフェーズでは、Azure の情報の保護を Office 365 の開発/テスト環境に追加し、ユーザー アカウントを有効にします。[Office 365 と EMS の開発/テスト環境](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)を構成した場合は、このフェーズをスキップします。エンタープライズ ・ モビリティ ・ スイートの試用版サブスクリプションには、Azure の情報保護のライセンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-p102">In this phase, you add Azure Information Protection to your Office 365 dev/test environment and enable it for your user accounts. If you have configured the [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx), skip this phase. The Enterprise Mobility Suite trial subscription includes Azure Information Protection licenses.</span></span>
  
<span data-ttu-id="fe0e0-115">最初に、Azure Information Protection 試用版サブスクリプションの新規登録を行います。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-115">First, sign up for an Azure Information Protection trial subscription.</span></span>
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a><span data-ttu-id="fe0e0-116">Azure Information Protection 試用版サブスクリプションの新規登録</span><span class="sxs-lookup"><span data-stu-id="fe0e0-116">Sign up for an Azure Information Protection trial subscription</span></span>

1. <span data-ttu-id="fe0e0-117">Internet Explorer またはお使いのブラウザーでは、 [http://portal.office.com](http://portal.office.com)に移動し、Office 365 のグローバル管理者アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-117">In Internet Explorer or your browser, go to [http://portal.office.com](http://portal.office.com) and sign in with your Office 365 global administrator account.</span></span>
    
2. <span data-ttu-id="fe0e0-118">**Microsoft Office ホーム**] タブで、**管理者**のタイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-118">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="fe0e0-119">Office 365 の管理] タブの左側のナビゲーションでをクリックして**請求 > サービスを購入する**です。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-119">On the Office 365 Admin tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="fe0e0-p103">**購買サービス**] ページで、 **Azure の情報保護のプレミアム P2**の項目を検索します。上にマウス ポインターを置くし、**無料の試用期間の開始**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-p103">On the **Purchase services** page, find the **Azure Information Protection Premium P2** item. Hover your mouse over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="fe0e0-122">**[注文の確認]** ページで、 **[今すぐ実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-122">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="fe0e0-123">**[注文の受領書]** ページで、**[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-123">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="fe0e0-124">次に、すべてのユーザー アカウントで Azure Information Protection  ライセンスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-124">Next, you enable the Azure Information Protection license for all user accounts.</span></span>
  
1. <span data-ttu-id="fe0e0-125">[Office 365 管理センター] タブで、[**ユーザー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-125">On the Office 365 admin center tab, click **Users**.</span></span>
    
2.  <span data-ttu-id="fe0e0-126">、ユーザー アカウントの一覧でグローバル管理者アカウントを選択し、**製品ライセンス**の**編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-126">In the list of user accounts, select your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="fe0e0-127">**上**に**情報保護プレミアム P2 の Azure**の製品のライセンスを有効にする**、保存**、**閉じる**を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-127">Turn the product license for **Azure Information Protection Premium P2** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="fe0e0-128">他のユーザー アカウント (ユーザー 1 ～ユーザー 5) について、手順 2 と 3 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-128">Repeat steps 2 and 3 for your other user accounts (User 1 through User 5).</span></span>
    
<span data-ttu-id="fe0e0-129">Office 365 開発/テスト環境には、以下が含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="fe0e0-130">Office 365 E5 Enterprise と Azure Information Protection の試用版サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-130">Office 365 E5 Enterprise and Azure Information Protection trial subscriptions.</span></span>
    
- <span data-ttu-id="fe0e0-131">すべてのユーザー アカウントで Office 365 E5 Enterprise と Azure Information Protection の両方が使用可能になっている。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-131">All of your user accounts enabled to use both Office 365 E5 Enterprise and Azure Information Protection.</span></span>
    
## <a name="phase-3-demonstrate-data-classification"></a><span data-ttu-id="fe0e0-132">フェーズ 3:データ分類のデモ </span><span class="sxs-lookup"><span data-stu-id="fe0e0-132">Phase 3: Demonstrate data classification</span></span>

<span data-ttu-id="fe0e0-133">このフェーズでは、Azure Information Protection クライアントと既定の Azure Information Protection ポリシーを使用してデータ分類をデモします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-133">In this phase, you demonstrate data classification using the Azure Information Protection client and the default Azure Information Protection policy.</span></span>
  
<span data-ttu-id="fe0e0-134">シミュレーション エンタープライズの Office 365 開発/テスト環境を使用する場合は、最初に CLIENT1 で Office 2016 をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-134">If you are using the simulated enterprise Office 365 dev/test environment, you must first install Office 2016 on CLIENT1.</span></span>
  
1. <span data-ttu-id="fe0e0-135">お使いのブラウザーを使用し、 [Azure ポータル](http://portal.azure.com)に移動します。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-135">Use your browser and go to the [Azure portal](http://portal.azure.com).</span></span>
    
2. <span data-ttu-id="fe0e0-136">クリックして**リソース グループ >** [リソース グループ名] **> CLIENT1 > 接続**。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-136">Click **Resource Groups >** [your resource group name] **> CLIENT1 > Connect**.</span></span>
    
3. <span data-ttu-id="fe0e0-137">CLIENT1 で、Internet Explorer を実行で[http://portal.office.com](http://portal.office.com)Office のポータルに移動し、User5 アカウント名とパスワードを使用してサインインしています。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-137">From CLIENT1, run Internet Explorer, go to the Office portal at [http://portal.office.com](http://portal.office.com), and then sign in with the User5 account name and password.</span></span>
    
4. <span data-ttu-id="fe0e0-138">**Microsoft Office ホーム**] タブ、[ **Office 2016 のインストール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-138">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
5. <span data-ttu-id="fe0e0-p104">クリックするとメッセージが表示されたら [**はい]**ユーザー アカウント制御によって、ダウンロードを実行します。Office をインストールするを待ちます。完了したら、**閉じる**を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-p104">Run the download when prompted and click **Yes** when prompted by User Account Control. Wait for Office to install. When complete, click **Close** twice.</span></span>
    
<span data-ttu-id="fe0e0-142">次に、Azure Infomation Protection クライアントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-142">Next, you install the Azure Information Protection client.</span></span>
  
1. <span data-ttu-id="fe0e0-143">ブラウザーまたは Internet Explorer、 [Microsoft Azure の情報保護のダウンロード ページ](https://www.microsoft.com/download/details.aspx?id=53018)に移動します。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-143">In your browser or Internet Explorer, go to the [Microsoft Azure Information Protection download page](https://www.microsoft.com/download/details.aspx?id=53018).</span></span>
    
  - <span data-ttu-id="fe0e0-144">Office 365 開発/テスト環境の簡易版を使用している場合は、ローカル コンピューターのブラウザーを使用します。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-144">If you are using the lightweight version of the Office 365 dev/test environment, use the browser on your local computer.</span></span>
    
  - <span data-ttu-id="fe0e0-145">シミュレーション エンタープライズの Office 365 開発/テスト環境を使用している場合は、CLIENT1 から Internet Explorer を実行します。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-145">If you are using the simulated enterprise Office 365 dev/test environment, run Internet Explorer from CLIENT1.</span></span>
    
2. <span data-ttu-id="fe0e0-146">**Microsoft Azure の情報保護**のダウンロード] ページで、[**ダウンロード**] をクリックして**AzInfoProtection.exe**、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-146">On the **Microsoft Azure Information Protection** download page, click **Download**, click **AzInfoProtection.exe**, and then click **Next**.</span></span>
    
3. <span data-ttu-id="fe0e0-147">指示に従い、AzInfoProtection.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-147">When prompted, run AzInfoProtection.exe.</span></span>
    
4. <span data-ttu-id="fe0e0-148">**Azure の情報保護をインストールする**クライアント] ボックスで [**同意する**] をクリックし、 **[はい]**で [ユーザー アカウント制御メッセージが表示されたら。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-148">In the **Install the Azure Information Protection** client box, click **I agree**, and then click **Yes** when prompted by User Account Control.</span></span>
    
5. <span data-ttu-id="fe0e0-149">[**正常に完了しました**] ボックスに、**閉じる**。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-149">In the **Completed successfully** box, click **Close.**</span></span>
    
<span data-ttu-id="fe0e0-150">次に、ドキュメント分類をデモします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-150">Next, you demonstrate document classification.</span></span>
  
1. <span data-ttu-id="fe0e0-151">タスク バーの**Word**アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-151">Click the **Word** icon in the taskbar.</span></span>
    
2. <span data-ttu-id="fe0e0-152">指示に従い、User5 のアカウント名とパスワードでサインインします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-152">When prompted, sign in with the User5 account name and password.</span></span>
    
3. <span data-ttu-id="fe0e0-153">だけで client1 で、2016 を Office をインストールしたかどうか、**まず最初**ボックスで、[**承諾**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-153">If you just installed Office 2016 on CLIENT1, in the **First things first** box, click **Accept**.</span></span>
    
4. <span data-ttu-id="fe0e0-154">[**白紙の文書**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-154">Click **Blank document**.</span></span> 
    
    <span data-ttu-id="fe0e0-155">**リボンの**[ホーム**] タブ、ドキュメントの分類の行のセクション**に注意してください。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-155">Note the **Protection** section of the ribbon on the **Home** tab and the row of document classifications.</span></span>
    
5. <span data-ttu-id="fe0e0-156">空白の文書にテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-156">In the blank document, type some text.</span></span>
    
6. <span data-ttu-id="fe0e0-157">クリックして**ファイル > 保存**、 **BeforeAIP**名前を入力し、し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-157">Click **File > Save**, type the name **BeforeAIP**, and then click **OK**.</span></span> 
    
7. <span data-ttu-id="fe0e0-158">ドキュメント クラスの行の**シークレット**の下向き矢印をクリックし、**すべての会社**です。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-158">In the row of document classes, click the down arrow for **Secret**, and then click **All Company**.</span></span>
    
8. <span data-ttu-id="fe0e0-159">クリックして**ファイル > 名前を付けて保存**、 **AfterAIP**名前を入力し、し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-159">Click **File > Save As**, type the name **AfterAIP**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="fe0e0-160">タスク バーに、**ファイル エクスプ ローラー**をクリックし、[**ドキュメント**] フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-160">Click **File Explorer** in the taskbar, and then open the **Documents** folder.</span></span>
    
    <span data-ttu-id="fe0e0-p105">**BeforeAIP**と**AfterAIP**のドキュメントの別のファイルのサイズに注意してください。AfterAIP ドキュメントは、分類情報が含まれているために大きくなります。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-p105">Note the different file sizes of the **BeforeAIP** and **AfterAIP** documents. The AfterAIP document is larger because it contains the classification information.</span></span>
    
<span data-ttu-id="fe0e0-163">次に、すべてのユーザーにサポート サイト コレクションへのアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-163">Next, you allow everyone to access the Support site collection.</span></span>
  
1. <span data-ttu-id="fe0e0-164">**Microsoft Office ホーム**] タブ、[ **SharePoint**を] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-164">On the **Microsoft Office Home** tab, click **SharePoint**.</span></span>
    
2. <span data-ttu-id="fe0e0-165">[ **SharePoint** ] タブで、**サポートのサイト コレクション**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-165">From the **SharePoint** tab, click **Support site collection**.</span></span>
    
3. <span data-ttu-id="fe0e0-166">、右上の**設定**アイコンをクリックする**と共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-166">In the upper right, click the **Settings** icon, and then click **Shared with**.</span></span>
    
4. <span data-ttu-id="fe0e0-167">**共有 'サポート サイト コレクション'**の場合は、[**詳細**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-167">In **Share 'Support site collection'**, click **Advanced**.</span></span>
    
5. <span data-ttu-id="fe0e0-168">SharePoint グループのリストでは、**サポート サイト コレクションのメンバー**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-168">In the list of SharePoint groups, click **Support site collection Members**.</span></span>
    
6. <span data-ttu-id="fe0e0-169">**[ユーザーとグループ]** ページで、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-169">On the **People and Groups** page, click **New**.</span></span>
    
7. <span data-ttu-id="fe0e0-170">**共有 'サポート サイト コレクション'**、**すべてのユーザー**を入力、**外部のユーザーを除くすべて**] をクリックし、**共有します**。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-170">In **Share 'Support site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share.**</span></span>
    
8. <span data-ttu-id="fe0e0-171">**ユーザーとグループ**] タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-171">Close the **People and Groups** tab.</span></span>
    
<span data-ttu-id="fe0e0-172">次に、User5 のアカウントでサインインし、AIP で保護されたドキュメントをサポート サイト コレクションのドキュメント フォルダーにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-172">Next, you sign in with your User5 account and upload the AIP-protected document to the Documents folder of the Support site collection.</span></span>
  
1. <span data-ttu-id="fe0e0-173">[**マイクロソフト オフィス ホーム**] タブの右上にユーザー アイコンをクリックして [**サインアウト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-173">On the **Microsoft Office Home** tab, in the upper right, click the user icon, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="fe0e0-174">[Http://portal.office.com](http://portal.office.com)に移動します。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-174">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="fe0e0-175">* * Office 365 のサインイン * * ページ、User5 のアカウント名をクリックし、サインインします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-175">On the ** Office 365 sign in** page, click the User5 account name and sign in.</span></span>
    
4. <span data-ttu-id="fe0e0-176">[ **Microsoft Office のホーム**] タブをクリックして**SharePoint > サイト コレクションをサポートする**です。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-176">On the **Microsoft Office Home** tab, click **SharePoint > Support site collection**.</span></span>
    
5. <span data-ttu-id="fe0e0-177">**ドキュメント**] をクリックして、[**アップロード**] をクリックして、 **AfterAIP**のドキュメント] をクリックし、し、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-177">Click **Documents**, click **Upload**, click the **AfterAIP** document, and then click **Open**.</span></span>
    
    <span data-ttu-id="fe0e0-178">サポート サイト コレクションのドキュメント フォルダーの AfterAIP.docx を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe0e0-178">You should see AfterAIP.docx in the Documents folder on the Support site collection.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="fe0e0-179">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe0e0-179">See Also</span></span>

[<span data-ttu-id="fe0e0-180">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="fe0e0-180">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="fe0e0-181">Office 365 と EMS の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="fe0e0-181">Office 365 and EMS dev/test environment</span></span>](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[<span data-ttu-id="fe0e0-182">Azure の情報の保護</span><span class="sxs-lookup"><span data-stu-id="fe0e0-182">Azure Information Protection</span></span>](https://www.microsoft.com/cloud-platform/azure-information-protection)


