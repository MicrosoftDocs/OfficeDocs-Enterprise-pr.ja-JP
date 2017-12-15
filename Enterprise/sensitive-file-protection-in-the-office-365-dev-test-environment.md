---
title: "Office 365 の開発/テスト環境での機密性の高いファイルの保護"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- jan17entnews
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "概要: は、構成し、不適切な SharePoint Online サイト コレクションに投稿される場合でもに Office 365 の情報権利の管理が、機密性の高いファイルを保護する方法をデモンストレーションします。"
ms.openlocfilehash: a6547cf4327980e3909323d5bda4455dfffd37f4
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="de380-103">Office 365 の開発/テスト環境での機密性の高いファイルの保護</span><span class="sxs-lookup"><span data-stu-id="de380-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="de380-104">**の概要:**構成し、不適切な SharePoint Online サイト コレクションに投稿される場合でもに Office 365 の情報権利の管理が、機密性の高いファイルを保護する方法をデモンストレーションします。</span><span class="sxs-lookup"><span data-stu-id="de380-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="de380-p101">Office 365 の Information Rights Management (IRM) は、SharePoint Online ライブラリとリストからダウンロードしたドキュメントを保護する機能のセットです。ダウンロードしたファイルは暗号化されており、格納されていた SharePoint Online ライブラリを反映するアクセス許可 (オープン、コピー、保存、印刷) を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="de380-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="de380-107">この記事の手順に従い、Office 365 試用版のサブスクリプションを使用して、機密性の高い情報を含む可能性のあるファイルに対して Office 365 で IRM を有効にしてテストします。</span><span class="sxs-lookup"><span data-stu-id="de380-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="de380-108">[ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="de380-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="de380-109">フェーズ 1: Office 365 開発/テスト環境を構築する</span><span class="sxs-lookup"><span data-stu-id="de380-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="de380-110">最小要件で軽量な方法で機密性の高いファイルの保護をテストする場合は、フェーズ 2 と 3[の開発/テスト環境を Office 365](office-365-dev-test-environment.md)の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="de380-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="de380-111">シミュレートされた企業内の機密性の高いファイルの保護をテストする場合は、 [Office 365 の開発/テスト環境のディレクトリ同期](dirsync-for-your-office-365-dev-test-environment.md)に指示します。</span><span class="sxs-lookup"><span data-stu-id="de380-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="de380-p102">機密性の高いファイルの保護をテストするのに、インターネットに接続されたシミュレーション イントラネットと Windows Server AD フォレスト用のディレクトリ同期を含めた、シミュレーション エンタープライズの開発/テスト環境は必要ではありません。この指示は、一般的な組織と類似した環境で機密性の高いファイルの保護をテストしてお試しいただけるようオプションとしてここで提供しています。</span><span class="sxs-lookup"><span data-stu-id="de380-p102">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="de380-114">フェーズ 2:アクセス許可で保護されたサイトのドキュメントがどのようにリークされる場合があるのかをデモする</span><span class="sxs-lookup"><span data-stu-id="de380-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="de380-115">このフェーズでは、何者かによってドキュメントがアクセス許可で保護されたサイトからダウンロードされて、制限が緩いサイトにアップロードされることがあり得るということをデモします。</span><span class="sxs-lookup"><span data-stu-id="de380-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="de380-116">最初に、エグゼクティブを表す 3 つの新しいユーザー アカウントを追加して、Office 365 E5 ライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="de380-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="de380-117">PowerShell モジュール (必要な場合) をインストールしてから新しい Office 365 サービスに接続するには、 [Office 365 の PowerShell への接続](https://technet.microsoft.com/library/dn975125.aspx)の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="de380-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="de380-118">自分のコンピューター (ライトウェイトの Office 365 開発/テスト環境の場合)。</span><span class="sxs-lookup"><span data-stu-id="de380-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="de380-119">CLIENT1 仮想マシン (シミュレーションのエンタープライズ Office 365 開発/テスト環境の場合)。</span><span class="sxs-lookup"><span data-stu-id="de380-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="de380-120">**Windows PowerShell の資格情報の要求**] ダイアログ ボックスで、Office 365 グローバル管理者名を入力します (例: jdoe@contosotoycompany.onmicrosoft.com) と、Office 365 の試用版サブスクリプションのパスワードです。</span><span class="sxs-lookup"><span data-stu-id="de380-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="de380-121">組織名 (例: contosotoycompany) と、所属地域に該当する 2 文字の国別コードを入力して、Windows PowerShell 用 Windows Azure Active Directory Module のプロンプトから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="de380-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="de380-122">**新しい MsolUser**コマンドの表示から、生成されたアカウントのパスワードを最高経営責任者に注意してくださいし、安全な場所に記録します。</span><span class="sxs-lookup"><span data-stu-id="de380-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="de380-123">次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="de380-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="de380-124">**新しい MsolUser**コマンドの表示、CFO のアカウントのパスワードが生成されたパスワードに注意してくださいし、安全な場所に記録します。</span><span class="sxs-lookup"><span data-stu-id="de380-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="de380-125">次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="de380-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="de380-126">**新しい MsolUser**コマンドの表示、COO のアカウントのパスワードが生成されたパスワードに注意してくださいし、安全な場所に記録します。</span><span class="sxs-lookup"><span data-stu-id="de380-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="de380-127">次に、プライベート エグゼクティブ グループを作成し、そこに新しいエグゼクティブ アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="de380-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="de380-128">お使いのブラウザーでは、 [http://portal.office.com](http://portal.office.com)で、Office のポータルに移動し、Office 365 試用版サブスクリプションのグローバル管理者アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="de380-128">In your browser, go to the Office portal at [http://portal.office.com](http://portal.office.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="de380-129">簡易版の Office 365 開発/テスト環境を使用している場合は、Internet Explorer か任意のブラウザーのプライベート セッションを開いて、ローカル コンピューターからサインインします。</span><span class="sxs-lookup"><span data-stu-id="de380-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="de380-130">シミュレーション エンタープライズの Office 365 開発/テスト環境を使用している場合は、Azure ポータルを使用して CLIENT1 仮想マシンに接続し、CLIENT1 からサインインします。</span><span class="sxs-lookup"><span data-stu-id="de380-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="de380-131">[ **Microsoft Office のホーム**] タブをクリックして**管理 > グループ > グループ**、**グループの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="de380-132">**グループの追加**] グループの種類の**Office 365 のグループ**を選択**役員****名**と**グループ Id**、**プライバシー**、**プライベート**を選択し、入力し、[**所有者の選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="de380-133">リストで、全体管理者のアカウント名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="de380-134">**追加**] をクリックし、[**閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="de380-135">グループ] ボックスの一覧で、**経営幹部**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="de380-136">**メンバーの編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="de380-p103">[**メンバーの追加**] をクリックします。メンバーの一覧で、次のユーザー アカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="de380-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="de380-139">最高経営責任者</span><span class="sxs-lookup"><span data-stu-id="de380-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="de380-140">最高財務責任者</span><span class="sxs-lookup"><span data-stu-id="de380-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="de380-141">最高執行責任者</span><span class="sxs-lookup"><span data-stu-id="de380-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="de380-142">**保存**] をクリックし、[**閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="de380-143">**Office 管理者センター** ] タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="de380-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="de380-144">次に、エグゼクティブ サイト コレクションを作成し、エグゼクティブ グループのメンバーのみにこのコレクションへのアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="de380-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="de380-145">**Microsoft Office ホーム**] タブで、**管理者**のタイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="de380-146">**Office 管理者センター** ] タブで、クリックして**管理センター > SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="de380-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="de380-147">[ **SharePoint 管理センター** ] タブをクリックして**新規 > プライベート サイト コレクション**です。</span><span class="sxs-lookup"><span data-stu-id="de380-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="de380-148">新しいサイト コレクション] ウィンドウで、**タイトル**] に、[URL] ボックスで、経営**幹部**を入力で**管理者**は、グローバル管理者アカウントの名前を指定**]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="de380-p104">新しいサイト コレクションが作成されるまで待機します。完了すると、新しい経営陣のサイト コレクションの URL をコピーし、お使いのブラウザーの新しいタブに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="de380-p104">Wait until the new site collection has been created. When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="de380-151">**経営幹部**のサイト コレクションの右上に設定アイコンをクリック**と共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="de380-152">**共有 '経営'**の場合は、[**詳細**を] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="de380-153">SharePoint グループのリストでは、**経営幹部のメンバー**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="de380-154">**[ユーザーとグループ]** ページで、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="de380-155">**共有 '経営'**に**経営幹部**を入力、**経営幹部**のグループ、**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="de380-156">**ユーザーとグループ**] タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="de380-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="de380-157">次に、販売サイト コレクションへのアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="de380-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="de380-158">**SharePoint 管理者センター** ] タブで、販売サイト コレクションの URL をコピーし、ブラウザーの新しいタブに貼り付けます.</span><span class="sxs-lookup"><span data-stu-id="de380-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="de380-159">、右上の設定アイコンをクリックする**と共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="de380-160">**共有 '販売サイト コレクション'**の場合は、[**詳細**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="de380-161">、SharePoint グループの一覧では、**販売サイトのコレクションのメンバー**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="de380-162">**[ユーザーとグループ]** ページで、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="de380-163">**共有 '販売サイト コレクション'**に**Everyone**と入力、**外部のユーザーを除くすべて**] をクリックし、**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="de380-164">**販売サイト コレクション**、および**SharePoint**のタブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="de380-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="de380-165">次に、エグゼクティブ アカウントでサインインし、エグゼクティブ サイト コレクションでドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="de380-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="de380-166">[場所] タブの [ **Microsoft Office のホーム**右の [ユーザー] アイコンをクリックし、[**サインアウト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="de380-167">[Http://portal.office.com](http://portal.office.com)に移動します。</span><span class="sxs-lookup"><span data-stu-id="de380-167">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="de380-168">**Office 365 のサインイン**ページで、**別のアカウントを使用**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="de380-169">**最高経営責任者**のアカウント名とそのパスワードを入力し、[**サインイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="de380-170">お使いのブラウザーの新しいタブのエグゼクティブのサイト コレクションの URL を入力します ( **https://**\<組織名 >**.sharepoint.com/sites/executives**)。</span><span class="sxs-lookup"><span data-stu-id="de380-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="de380-171">**ドキュメント**] をクリックして、[**新規作成**] をクリックし、[ **Word 文書**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="de380-172">タイトル バーをクリックし、 **SensitiveData BeforeIRM**を入力します。</span><span class="sxs-lookup"><span data-stu-id="de380-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="de380-173">文書の本文に、**最新の委員会からの分**を入力をクリック**経営幹部**。</span><span class="sxs-lookup"><span data-stu-id="de380-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="de380-174">[**ドキュメント**] フォルダー内の**SensitiveData BeforeIRM.docx**を参照してくださいする必要があります。</span><span class="sxs-lookup"><span data-stu-id="de380-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="de380-175">次に、SensitiveData BeforeIRM.docx ドキュメントのローカル コピーをダウンロードして、販売サイト コレクションに誤って投稿します。</span><span class="sxs-lookup"><span data-stu-id="de380-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="de380-176">ローカル コンピューターに新しいフォルダーを作成します (たとえば、c:\\TLGs\\SensitiveDataTestFiles)。</span><span class="sxs-lookup"><span data-stu-id="de380-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="de380-177">お使いのブラウザーの [**ドキュメント**] タブで**SensitiveData BeforeIRM.docx**のドキュメントを選択して、楕円では、し、[**ダウンロード**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="de380-178">手順 1 で作成したフォルダーに**SensitiveData BeforeIRM.docx**のドキュメントを格納します。</span><span class="sxs-lookup"><span data-stu-id="de380-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="de380-179">お使いのブラウザーの新しいタブの販売サイト コレクションの URL を入力します ( **https://**\<組織名 >**.sharepoint.com/sites/sales**)。</span><span class="sxs-lookup"><span data-stu-id="de380-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="de380-180">の**販売サイト コレクション**の [**ドキュメント**] フォルダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="de380-181">**アップロード**する] をクリックし、手順 1 で作成したフォルダーに**SensitiveData BeforeIRM.docx**のドキュメントを指定し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="de380-182">**SensitiveData BeforeIRM.docx**ドキュメントが、[**ドキュメント**] フォルダーを確認します。</span><span class="sxs-lookup"><span data-stu-id="de380-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="de380-183">**販売**および**SharePoint**のタブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="de380-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="de380-184">次に、User5 としてサインインして、販売サイト コレクションのドキュメント noSensitiveData-BeforeIRM.docx を開いてみます。</span><span class="sxs-lookup"><span data-stu-id="de380-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="de380-185">[場所] タブの [ **Microsoft Office のホーム**右の [ユーザー] アイコンをクリックし、[**サインアウト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="de380-186">[Http://portal.office.com](http://portal.office.com)に移動します。</span><span class="sxs-lookup"><span data-stu-id="de380-186">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="de380-187">**Office 365 のサインイン**ページで、**別のアカウントを使用**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="de380-188">User5 アカウント名とそのパスワードを入力し、[**サインイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="de380-189">、お使いのブラウザーの新しいタブでは、営業サイト コレクションの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="de380-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="de380-190">の**販売サイト コレクション**の [**ドキュメント**] フォルダーでは、 **SensitiveData BeforeIRM.docx**のドキュメントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="de380-191">内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="de380-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="de380-192">**販売サイト コレクション**の**ドキュメント**とタブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="de380-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="de380-193">SensitiveData-BeforeIRM.docx ドキュメントを販売サイト コレクションに誤って投稿することにより、CEO はエグゼクティブ サイト コレクションのアクセス許可セキュリティをバイパスします。</span><span class="sxs-lookup"><span data-stu-id="de380-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="de380-194">Office 365 をフェーズ 3 と 4 のために準備するには、SharePoint Online の IRM を有効にします。</span><span class="sxs-lookup"><span data-stu-id="de380-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="de380-195">[場所] タブの [ **Microsoft Office のホーム**右の [ユーザー] アイコンをクリックし、[**サインアウト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="de380-196">[Http://portal.office.com](http://portal.office.com)に移動します。</span><span class="sxs-lookup"><span data-stu-id="de380-196">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="de380-197">**Office 365 のサインイン**ページで、グローバル管理者のアカウント名をクリックを選択し、そのパスワードを入力し、[**サインイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="de380-198">[ **Microsoft Office のホーム**] タブをクリックして**管理 > 管理センター > SharePoint**。</span><span class="sxs-lookup"><span data-stu-id="de380-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="de380-199">[場所] タブの [ **SharePoint の管理センター**には、[**設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="de380-200">[**設定**] ページで、**情報権利管理 (IRM)** ] セクションでは、**構成では、指定された IRM サービスを使用して**を選択し、 **IRM 設定の更新**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="de380-200">On the **Settings** page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="de380-201">**SharePoint 管理者センター** ] タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="de380-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="de380-202">フェーズ 3：SharePoint Information Rights Management を Office 365 のプライベート グループとともに使用する</span><span class="sxs-lookup"><span data-stu-id="de380-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="de380-203">このフェーズでは、SharePoint Information Rights Management を Office 365 のプライベート グループとともに使用することにより、機密性の高いドキュメントが制限の緩いサイトに投稿された場合でも、そのドキュメントへのアクセスが保護されるようにします。</span><span class="sxs-lookup"><span data-stu-id="de380-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="de380-204">最初に、エグゼクティブ サイト コレクションのドキュメント ライブラリ用に IRM を有効にして設定します。 </span><span class="sxs-lookup"><span data-stu-id="de380-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="de380-205">、お使いのブラウザーの新しいタブでは、経営幹部のサイト コレクションの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="de380-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="de380-206">[**ドキュメント**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="de380-207">、右に設定アイコンをクリックして**ライブラリの設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="de380-208">[**設定**] ページで、[**権限と管理**、**情報権利の管理**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="de380-209">[ **Information Rights Management 設定**] ページ。</span><span class="sxs-lookup"><span data-stu-id="de380-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="de380-210">**ダウンロード時にこのライブラリのドキュメントに対するアクセス許可を制限する**を選択します。</span><span class="sxs-lookup"><span data-stu-id="de380-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="de380-211">**アクセス許可ポリシーのタイトルの作成**、**経営幹部**を入力します。</span><span class="sxs-lookup"><span data-stu-id="de380-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="de380-212">**追加のアクセス許可ポリシーの説明**、**経営幹部の IRM**を入力します。</span><span class="sxs-lookup"><span data-stu-id="de380-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="de380-213">**オプションを表示する**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="de380-214">**IRM の追加のライブラリの設定を設定**すると、下には、 **IRM をサポートしていないドキュメントのアップロードを許可しない**を選択します。</span><span class="sxs-lookup"><span data-stu-id="de380-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="de380-215">**構成ドキュメントのアクセス権**、[**印刷を許可するビューアー**および**ダウンロードされたドキュメントのコピーを作成するのには許可のあるユーザー**を選択します。</span><span class="sxs-lookup"><span data-stu-id="de380-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="de380-216">**グループの保護および資格情報の間隔を設定**すると、[**グループの保護を許可する**] を選択しの**既定のグループ**を、**経営幹部**を入力します。</span><span class="sxs-lookup"><span data-stu-id="de380-216">Under **Set group protection and credentials interval**, select **Allow group protection** and for **Default group**, type **Executives**.</span></span>
    
10. <span data-ttu-id="de380-217">[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-217">Click **OK**.</span></span>
    
<span data-ttu-id="de380-218">次に、CEO として新しいドキュメントをエグゼクティブ ドキュメント フォルダーにアップロードし、それをダウンロードして、販売ドキュメント フォルダーに誤ってアップロードします。</span><span class="sxs-lookup"><span data-stu-id="de380-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="de380-219">**SensitiveData BeforeIRM.docx**ドキュメントを格納するローカル フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="de380-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="de380-220">**SensitiveData BeforeIRM.docx**を右クリックし、[**コピー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="de380-221">フォルダー内を右クリックし、[**貼り付け**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="de380-222">**SensitiveData AfterIRM.docx**に新しい**SensitiveData-BeforeIRM - Copy.docx**ファイルの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="de380-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="de380-223">**マイクロソフト オフィス ホーム**] タブからお使いのブラウザーで、右の [ユーザー] アイコンをクリックし、[**サインアウト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="de380-224">[Http://portal.office.com](http://portal.office.com)に移動します。</span><span class="sxs-lookup"><span data-stu-id="de380-224">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
7. <span data-ttu-id="de380-225">**Office 365 のサインイン**ページで、最高経営責任者のアカウント名をクリックして、そのパスワードを入力し、[**サインイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="de380-226">、お使いのブラウザーの新しいタブでは、経営幹部のサイト コレクションの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="de380-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="de380-227">[**ドキュメント**] ページで、[**アップロード**] をクリックを選択し、 **SensitiveData AfterIRM.docx**ドキュメントをローカル フォルダーに指定し、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="de380-228">**[ドキュメント**] ページで新しい**SensitiveData AfterIRM.docx**ドキュメントを選択、メニュー バーで、省略符号ボタン (...)] をクリックし、[**ダウンロード**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="de380-229">ダイアログ ボックスが表示されたら、元のバージョンを上書きする、ローカルのフォルダーに**SensitiveData AfterIRM.docx**のドキュメントを保存します。</span><span class="sxs-lookup"><span data-stu-id="de380-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="de380-230">**[ドキュメント**] ページのタブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="de380-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="de380-231">、お使いのブラウザーの新しいタブでは、営業サイト コレクションの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="de380-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="de380-232">[**ドキュメント**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="de380-233">[**ドキュメント**] ページで、[**アップロード**] をクリックを選択し、 **SensitiveData AfterIRM.docx**ドキュメントをローカル フォルダーに指定し、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="de380-234">**販売サイト コレクション**、および**SharePoint**のタブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="de380-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="de380-235">次に、通常のユーザーとして動作しているしようとする販売ドキュメント フォルダー内の**SensitiveData AfterIRM.docx**のドキュメントにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="de380-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="de380-236">**マイクロソフト オフィス ホーム**] タブからお使いのブラウザーで、右の [ユーザー] アイコンをクリックし、[**サインアウト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="de380-237">[Http://portal.office.com](http://portal.office.com)に移動します。</span><span class="sxs-lookup"><span data-stu-id="de380-237">Go to [http://portal.office.com](http://portal.office.com).</span></span>
    
3. <span data-ttu-id="de380-238">**Office 365 のサインイン**ページで、User5 のアカウント名をクリックを選択し、そのパスワードを入力し、[**サインイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="de380-239">、お使いのブラウザーの新しいタブでは、営業サイト コレクションの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="de380-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="de380-240">[**ドキュメント**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="de380-241">[**ドキュメント**] ページで、 **SensitiveData AfterIRM.docx**のドキュメントを開きます。</span><span class="sxs-lookup"><span data-stu-id="de380-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="de380-242">「申し訳ありません。このドキュメントは Information Rights Management (IRM) によって保護されているため、Word Online で開くことはできません。」というメッセージが表示されます。 </span><span class="sxs-lookup"><span data-stu-id="de380-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="de380-p105">**Word で編集**] をクリックします。場合は、ファイルを開くことが求められます。**[はい]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="de380-p106">サインインするメッセージが表示されたら、User5 のアカウントのアカウント名を入力し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="de380-p107">パスワードの入力を求められます。User5 アカウントのパスワードを入力し、[**サインイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="de380-250">次のメッセージが表示されます。「このドキュメントを開くための資格情報がありません。」</span><span class="sxs-lookup"><span data-stu-id="de380-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="de380-251">[**いいえ**を] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de380-251">Click **No**.</span></span>
    
<span data-ttu-id="de380-p108">IRM による保護を参照する別の方法では、ローカル フォルダー内のファイルを検索します。**SensitiveData AfterIRM.docx** **SensitiveData BeforeIRM.docx**ファイルをはるかに超える必要があります。**SensitiveData AfterIRM.docx**ファイルが暗号化されており、IRM 保護の情報が追加。</span><span class="sxs-lookup"><span data-stu-id="de380-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="de380-255">See Also</span><span class="sxs-lookup"><span data-stu-id="de380-255">See Also</span></span>

[<span data-ttu-id="de380-256">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="de380-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="de380-257">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="de380-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="de380-258">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="de380-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="de380-259">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="de380-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


