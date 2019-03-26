---
title: Office 365 の開発/テスト環境での機密性の高いファイルの保護
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
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: '概要: Office 365 Information Rights Management が、誤った SharePoint Online サイトコレクションに投稿された場合でも、機密ファイルを保護する方法を構成し、デモンストレーションします。'
ms.openlocfilehash: 59d4cf56113f8b787f0caeaefddae135ad8e6249
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574071"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a><span data-ttu-id="7d627-103">Office 365 の開発/テスト環境での機密性の高いファイルの保護</span><span class="sxs-lookup"><span data-stu-id="7d627-103">Sensitive file protection in the Office 365 dev/test environment</span></span>

 <span data-ttu-id="7d627-104">**概要:** Office 365 Information Rights Management が、誤った SharePoint Online サイトコレクションに投稿された場合でも、機密ファイルを保護する方法を構成し、デモンストレーションします。</span><span class="sxs-lookup"><span data-stu-id="7d627-104">**Summary:** Configure and demonstrate how Office 365 Information Rights Management protects your sensitive files, even when they are posted to the wrong SharePoint Online site collection.</span></span>
  
<span data-ttu-id="7d627-p101">Office 365 の Information Rights Management (IRM) は、SharePoint Online ライブラリとリストからダウンロードしたドキュメントを保護する機能のセットです。ダウンロードしたファイルは暗号化されており、格納されていた SharePoint Online ライブラリを反映するアクセス許可 (オープン、コピー、保存、印刷) を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="7d627-p101">Information Rights Management (IRM) in Office 365 is a set of capabilities to protect documents that are downloaded from SharePoint Online libraries and lists. Downloaded files are encrypted and contain the open, copy, save, and print permissions that reflect the SharePoint Online library in which they were stored.</span></span>
  
<span data-ttu-id="7d627-107">この記事の手順に従い、Office 365 試用版のサブスクリプションを使用して、機密性の高い情報を含む可能性のあるファイルに対して Office 365 で IRM を有効にしてテストします。</span><span class="sxs-lookup"><span data-stu-id="7d627-107">With the instructions in this article, you enable and test IRM in Office 365 for files containing possible sensitive information in your Office 365 trial subscription.</span></span>
  
> [!TIP]
> <span data-ttu-id="7d627-108">[ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="7d627-108">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a><span data-ttu-id="7d627-109">フェーズ 1: Office 365 開発/テスト環境を構成する</span><span class="sxs-lookup"><span data-stu-id="7d627-109">Phase 1: Build out your Office 365 dev/test environment</span></span>

<span data-ttu-id="7d627-110">最小要件で機密性の高いファイル保護を簡易な方法でテストする場合は、[Office 365 dev/test environment](office-365-dev-test-environment.md)のフェーズ 2 と 3 の指示に従ってください。</span><span class="sxs-lookup"><span data-stu-id="7d627-110">If you just want to test sensitive file protection in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="7d627-111">シミュレーション エンタープライズで機密性の高いファイル保護をテストする場合は、[DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md)の指示に従ってください。</span><span class="sxs-lookup"><span data-stu-id="7d627-111">If you want to test sensitive file protection in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="7d627-p102">機密性の高いファイルの保護をテストするのに、インターネットに接続されたシミュレーション イントラネットと Windows Server AD フォレスト用のディレクトリ同期を含めた、シミュレーション エンタープライズの開発/テスト環境は必要ではありません。この指示は、一般的な組織と類似した環境で機密性の高いファイルの保護をテストしてお試しいただけるようオプションとしてここで提供しています。</span><span class="sxs-lookup"><span data-stu-id="7d627-p102">Testing sensitive file protection does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test sensitive file protection and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a><span data-ttu-id="7d627-114">フェーズ 2:アクセス許可で保護されたサイトのドキュメントがどのようにリークされる場合があるのかをデモする</span><span class="sxs-lookup"><span data-stu-id="7d627-114">Phase 2: Demonstrate how documents from permissions-protected sites can be leaked</span></span>

<span data-ttu-id="7d627-115">このフェーズでは、何者かによってドキュメントがアクセス許可で保護されたサイトからダウンロードされて、制限が緩いサイトにアップロードされることがあり得るということをデモします。</span><span class="sxs-lookup"><span data-stu-id="7d627-115">In this phase, you demonstrate that someone can download a document from a permissions-protected site and then upload it to a site that has wide-open permissions.</span></span>
  
<span data-ttu-id="7d627-116">最初に、エグゼクティブを表す 3 つの新しいユーザー アカウントを追加して、Office 365 E5 ライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7d627-116">First, you add three new user accounts that represent executives and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="7d627-117">「 [office 365 powershell に接続](https://technet.microsoft.com/library/dn975125.aspx)する」の手順を使用して、powershell モジュールをインストールし (必要な場合)、新しい Office 365 サブスクリプションに接続します。</span><span class="sxs-lookup"><span data-stu-id="7d627-117">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules (if needed) and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="7d627-118">自分のコンピューター (軽量の Office 365 開発/テスト環境の場合)。</span><span class="sxs-lookup"><span data-stu-id="7d627-118">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="7d627-119">CLIENT1 仮想マシン (シミュレーションのエンタープライズ Office 365 開発/テスト環境の場合)。</span><span class="sxs-lookup"><span data-stu-id="7d627-119">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="7d627-120">**[Windows PowerShell 資格情報の要求]** ダイアログ ボックスで、Office 365 全体管理者名 (例: jdoe@contosotoycompany.onmicrosoft.com) と Office 365 試用版のサブスクリプションのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="7d627-120">In the **Windows PowerShell Credential Request** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password of your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="7d627-121">組織名 (例: contosotoycompany) と、所属地域に該当する 2 文字の国別コードを入力して、Windows PowerShell 用 Windows Azure Active Directory Module のプロンプトから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="7d627-121">Fill in your organization name (example: contosotoycompany) and the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="7d627-122">**New-MsolUser** コマンドの表示から、CEO アカウント用に生成されたパスワードを見つけて、安全な場所に記録しておきます。</span><span class="sxs-lookup"><span data-stu-id="7d627-122">From the display of the **New-MsolUser** command, note the generated password for the CEO account and record it in a safe location.</span></span>
  
<span data-ttu-id="7d627-123">次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="7d627-123">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="7d627-124">**New-MsolUser** コマンドの表示から、CFO アカウント用に生成されたパスワードを見つけて、安全な場所に記録しておきます。</span><span class="sxs-lookup"><span data-stu-id="7d627-124">From the display of the **New-MsolUser** command, note the generated password for the CFO account and record it in a safe location.</span></span>
  
<span data-ttu-id="7d627-125">次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="7d627-125">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

<span data-ttu-id="7d627-126">**New-MsolUser** コマンドの表示から、COO アカウント用に生成されたパスワードを見つけて、安全な場所に記録しておきます。</span><span class="sxs-lookup"><span data-stu-id="7d627-126">From the display of the **New-MsolUser** command, note the generated password for the COO account and record it in a safe location.</span></span>
  
<span data-ttu-id="7d627-127">次に、プライベート エグゼクティブ グループを作成し、そこに新しいエグゼクティブ アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="7d627-127">Next, you create a private Executives group and add the new executive accounts to it.</span></span>
  
1. <span data-ttu-id="7d627-128">ブラウザーで、office ポータルに移動[http://admin.microsoft.com](http://admin.microsoft.com)し、全体管理者アカウントを使用して office 365 試用版サブスクリプションにサインインします。</span><span class="sxs-lookup"><span data-stu-id="7d627-128">In your browser, go to the Office portal at [http://admin.microsoft.com](http://admin.microsoft.com) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
  - <span data-ttu-id="7d627-129">簡易版の Office 365 開発/テスト環境を使用している場合は、Internet Explorer か任意のブラウザーのプライベート セッションを開いて、ローカル コンピューターからサインインします。</span><span class="sxs-lookup"><span data-stu-id="7d627-129">If you are using the lightweight Office 365 dev/test environment, open a private session of Internet Explorer or your browser and sign in from your local computer.</span></span>
    
  - <span data-ttu-id="7d627-130">シミュレーション エンタープライズの Office 365 開発/テスト環境を使用している場合は、Azure ポータルを使用して CLIENT1 仮想マシンに接続し、CLIENT1 からサインインします。</span><span class="sxs-lookup"><span data-stu-id="7d627-130">If you are using the simulated enterprise Office 365 dev/test environment, use the Azure portal to connect to the CLIENT1 virtual machine, and then sign in from CLIENT1.</span></span>
    
2. <span data-ttu-id="7d627-131">**[Microsoft Office Home]** タブで、**[管理]、[グループ]、[グループ]** の順にクリックして、**[グループを追加する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-131">On the **Microsoft Office Home** tab, click **Admin > Groups > Groups**, and then click **Add a group**.</span></span>
    
3. <span data-ttu-id="7d627-132">**[グループを追加]** で、グループの種類は **[Office 365 グループ]** を選びます。**[名前]** と **[グループ ID]** に「**エグゼクティブ**」と入力します。**[プライバシー]** は **[プライベート]** を選び、**[所有者の選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-132">In **Add a group**, select **Office 365 group** for the group type, type **Executives** in **Name** and **Group Id**, select **Private** for **Privacy**, and then click **Select Owner**.</span></span>
    
4. <span data-ttu-id="7d627-133">リストで、全体管理者のアカウント名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-133">In the list, click your global administrator account name.</span></span>
    
5. <span data-ttu-id="7d627-134">**[追加]** をクリックして、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-134">Click **Add**, and then click **Close**.</span></span>
    
6. <span data-ttu-id="7d627-135">グループ リストで、**[エグゼクティブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-135">In the groups list, click **Executives**.</span></span>
    
7. <span data-ttu-id="7d627-136">**[メンバー用に編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-136">Click **Edit for Members**.</span></span>
    
8. <span data-ttu-id="7d627-p103">**[メンバーの追加]** をクリックします。メンバー リストで、次のユーザー アカウントを選びます。</span><span class="sxs-lookup"><span data-stu-id="7d627-p103">Click **Add members**. In the member list, select the following user accounts:</span></span>
    
  - <span data-ttu-id="7d627-139">最高経営責任者</span><span class="sxs-lookup"><span data-stu-id="7d627-139">Chief Executive Officer</span></span>
    
  - <span data-ttu-id="7d627-140">最高財務責任者</span><span class="sxs-lookup"><span data-stu-id="7d627-140">Chief Financial Officer</span></span>
    
  - <span data-ttu-id="7d627-141">最高執行責任者</span><span class="sxs-lookup"><span data-stu-id="7d627-141">Chief Operations Officer</span></span>
    
9. <span data-ttu-id="7d627-142">**[保存]** をクリックし、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-142">Click **Save**, and then click **Close**.</span></span>
    
10. <span data-ttu-id="7d627-143">**[Office 管理センター]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7d627-143">Close the **Office Admin center** tab.</span></span>
    
<span data-ttu-id="7d627-144">次に、エグゼクティブ サイト コレクションを作成し、エグゼクティブ グループのメンバーのみにこのコレクションへのアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="7d627-144">Next, you create an Executives site collection and allow just the members of the Executives group to access it.</span></span>
  
1. <span data-ttu-id="7d627-145">**[Microsoft Office Home]** タブで、**[管理者]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-145">On the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="7d627-146">[ **Office 管理センター** ] タブで、[**管理センター > SharePoint**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-146">On the **Office Admin center** tab, click **Admin centers > SharePoint**.</span></span>
    
3. <span data-ttu-id="7d627-147">[ **SharePoint 管理センター** ] タブで、[**新しい > のプライベートサイトコレクション**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-147">On the **SharePoint admin center** tab, click **New > Private site collection**.</span></span>
    
4. <span data-ttu-id="7d627-148">[サイトコレクションの新規作成] ウィンドウ\*\*\*\* の [ \*\*\*\* URL] ボックスに「役職」と入力し、**管理者**のグローバル管理者アカウントの名前を指定して、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-148">In the new site collection pane, type **Executives** in **Title**, executives in the URL box, specify the name of your global administrator account in **Administrator**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="7d627-149">新しいサイトコレクションが作成されるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="7d627-149">Wait until the new site collection has been created.</span></span> <span data-ttu-id="7d627-150">完了したら、新しい重役サイトコレクションの URL をコピーして、ブラウザーの新しいタブに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="7d627-150">When complete, copy the URL of the new Executives site collection and paste it into a new tab of your browser.</span></span>
    
6. <span data-ttu-id="7d627-151">**エグゼクティブ** サイト コレクションの右上部分にある [設定] アイコンをクリックし、**[共有アイテム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-151">In the upper right of the **Executives** site collection, click the settings icon, and then click **Shared with**.</span></span>
    
7. <span data-ttu-id="7d627-152">[**共有 ' エグゼクティブ '**] で、[**詳細設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-152">In **Share 'Executives'**, click **Advanced**.</span></span>
    
8. <span data-ttu-id="7d627-153">SharePoint グループの一覧で、**[エグゼクティブ メンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-153">In the list of SharePoint groups, click **Executives Members**.</span></span>
    
9. <span data-ttu-id="7d627-154">**[ユーザーとグループ]** ページで、**[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-154">On the **People and Groups** page, click **New**.</span></span>
    
10. <span data-ttu-id="7d627-155">[**共有 ' エグゼクティブ '**] で、「**エグゼクティブ**」と入力し、[**重役**] グループをクリックして、[**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-155">In **Share 'Executives'**, type **Executives**, click the **Executives** group, and then click **Share**.</span></span>
    
11. <span data-ttu-id="7d627-156">[**ユーザーとグループ**] タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7d627-156">Close the **People and groups** tab.</span></span>
    
<span data-ttu-id="7d627-157">次に、販売サイト コレクションへのアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="7d627-157">Next, you allow everyone to access the Sales site collection.</span></span>
  
1. <span data-ttu-id="7d627-158">[ **SharePoint 管理センター** ] タブから、Sales サイトコレクションの URL をコピーして、ブラウザーの新しいタブに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="7d627-158">From the **SharePoint admin center** tab, copy the URL of the Sales site collection and paste it into a new tab of your browser..</span></span>
    
2. <span data-ttu-id="7d627-159">右上部分で [設定] アイコンをクリックし、**[共有アイテム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-159">In the upper right, click the settings icon, and then click **Shared with**.</span></span>
    
3. <span data-ttu-id="7d627-160">[**共有 ' 販売サイトコレクション '**] で、[**詳細設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-160">In **Share 'Sales site collection'**, click **Advanced**.</span></span>
    
4. <span data-ttu-id="7d627-161">SharePoint グループの一覧で、**[販売サイト コレクション メンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-161">In the list of SharePoint groups, click **Sales site collection Members**.</span></span>
    
5. <span data-ttu-id="7d627-162">**[ユーザーとグループ]** ページで、**[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-162">On the **People and Groups** page, click **New**.</span></span>
    
6. <span data-ttu-id="7d627-163">[**共有 ' 販売サイトコレクション '**] に「 **everyone**」と入力し、[**外部ユーザー以外のすべてのユーザー**] をクリックして、[**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-163">In **Share 'Sales site collection'**, type **Everyone**, click **Everyone except external users**, and then click **Share**.</span></span>
    
7. <span data-ttu-id="7d627-164">**[販売サイト コレクション]** と **[SharePoint]** のタブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7d627-164">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="7d627-165">次に、エグゼクティブ アカウントでサインインし、エグゼクティブ サイト コレクションでドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="7d627-165">Next, you sign in with an executive account and create a document in the Executives site collection.</span></span>
  
1. <span data-ttu-id="7d627-166">**[Microsoft Office Home]** タブで、右上部分にある [ユーザー] アイコンをクリックし、**[サインアウト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-166">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="7d627-167">[http://admin.microsoft.com](http://admin.microsoft.com) に移動します。</span><span class="sxs-lookup"><span data-stu-id="7d627-167">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="7d627-168">**Office 365 のサインイン** ページで、**[別のアカウントを使用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-168">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="7d627-169">**CEO** アカウント名とパスワードを入力し、**[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-169">Type the **CEO** account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="7d627-170">ブラウザーの新しいタブで、エグゼクティブサイトコレクション ( **https://**\<organization name>) の URL を入力します\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7d627-170">On a new tab of your browser, type the URL to the Executives site collection ( **https://**\<organization name>**.sharepoint.com/sites/executives**).</span></span>
    
6. <span data-ttu-id="7d627-171">[**ドキュメント**]、[**新規作成**]、[ **Word 文書**] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-171">Click **Documents**, click **New,** and then click **Word Document**.</span></span>
    
7. <span data-ttu-id="7d627-172">タイトル バーをクリックして、「**SensitiveData BeforeIRM**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="7d627-172">Click in the title bar and type **SensitiveData-BeforeIRM**.</span></span>
    
8. <span data-ttu-id="7d627-173">ドキュメント本文をクリックして、「**取締役会の最新の会議メモ**」と入力し、**[エグゼクティブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-173">Click in the document body and type **Minutes from the latest board meeting**, and then click **Executives**.</span></span>
    
     <span data-ttu-id="7d627-174">**[ドキュメント]** フォルダーに、**SensitiveData BeforeIRM.docx** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d627-174">You should see **SensitiveData-BeforeIRM.docx** in the **Documents** folder.</span></span>
    
<span data-ttu-id="7d627-175">次に、SensitiveData BeforeIRM.docx ドキュメントのローカル コピーをダウンロードして、販売サイト コレクションに誤って投稿します。</span><span class="sxs-lookup"><span data-stu-id="7d627-175">Next, you download a local copy of the SensitiveData-BeforeIRM.docx document and then accidentally post it to the Sales site collection.</span></span>
  
1. <span data-ttu-id="7d627-176">ローカルコンピューターで、新しいフォルダーを作成します (たとえば、C:\\tlgs\\SensitiveDataTestFiles)。</span><span class="sxs-lookup"><span data-stu-id="7d627-176">On your local computer, create a new folder (for example, C:\\TLGs\\SensitiveDataTestFiles).</span></span>
    
2. <span data-ttu-id="7d627-177">ブラウザーの **[ドキュメント]** タブで、**SensitiveData BeforeIRM.docx** ドキュメントを選び、省略記号をクリックして、**[ダウンロード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-177">On the **Documents** tab of your browser, select the **SensitiveData-BeforeIRM.docx** document, click the ellipses, and then click **Download**.</span></span>
    
3. <span data-ttu-id="7d627-178">**SensitiveData BeforeIRM.docx** ドキュメントをステップ 1 で作成したフォルダーに格納します。</span><span class="sxs-lookup"><span data-stu-id="7d627-178">Store the **SensitiveData-BeforeIRM.docx** document in the folder created in step 1.</span></span>
    
4. <span data-ttu-id="7d627-179">ブラウザーの新しいタブで、Sales サイトコレクションの URL を入力します ( **https://**\<organization name>)\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7d627-179">On a new tab of your browser, type the URL to the Sales site collection ( **https://**\<organization name>**.sharepoint.com/sites/sales**).</span></span>
    
5. <span data-ttu-id="7d627-180">**販売サイト コレクション** の **[ドキュメント]** フォルダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-180">Click the **Documents** folder of the **Sales site collection**.</span></span>
    
6. <span data-ttu-id="7d627-181">**[アップロード]** をクリックし、ステップ 1 で作成したフォルダーの **SensitiveData BeforeIRM.docx** ドキュメントを指定して、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-181">Click **Upload**, and then specify **SensitiveData-BeforeIRM.docx** document in the folder created in step 1, and then click **OK**.</span></span>
    
7. <span data-ttu-id="7d627-182">**[ドキュメント]** フォルダーに、**SensitiveData BeforeIRM.docx** ドキュメントが表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7d627-182">Verify that the **SensitiveData-BeforeIRM.docx** document is in the **Documents** folder.</span></span>
    
8. <span data-ttu-id="7d627-183">**[販売]** と **[SharePoint]** のタブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7d627-183">Close the **Sales** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="7d627-184">次に、User5 としてサインインして、販売サイト コレクションのドキュメント noSensitiveData-BeforeIRM.docx を開いてみます。</span><span class="sxs-lookup"><span data-stu-id="7d627-184">Next, you sign in as User5 and try to open the SensitiveData-BeforeIRM.docx document in the Sales site collection.</span></span>
  
1. <span data-ttu-id="7d627-185">**[Microsoft Office Home]** タブで、右上部分にある [ユーザー] アイコンをクリックし、**[サインアウト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-185">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="7d627-186">[http://admin.microsoft.com](http://admin.microsoft.com) に移動します。</span><span class="sxs-lookup"><span data-stu-id="7d627-186">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="7d627-187">**Office 365 のサインイン** ページで、**[別のアカウントを使用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-187">On the **Office 365 sign in** page, click **Use another account**.</span></span>
    
4. <span data-ttu-id="7d627-188">User5 アカウント名とパスワードを入力して、**[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-188">Type the User5 account name and its password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="7d627-189">ブラウザーの新しいタブで、Sales サイトコレクションの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="7d627-189">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
6. <span data-ttu-id="7d627-190">**販売サイト コレクション**の **[ドキュメント]** フォルダーで、**SensitiveData-BeforeIRM.docx** ドキュメントをクリックします。 </span><span class="sxs-lookup"><span data-stu-id="7d627-190">In the **Documents** folder of the **Sales site collection**, click the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
    <span data-ttu-id="7d627-191">内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d627-191">You should see its contents.</span></span>
    
7. <span data-ttu-id="7d627-192">**[ドキュメント]** と **[販売サイト コレクション]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7d627-192">Close the **Documents** and **Sales site collection** tabs.</span></span>
    
<span data-ttu-id="7d627-193">SensitiveData-BeforeIRM.docx ドキュメントを販売サイト コレクションに誤って投稿することにより、CEO はエグゼクティブ サイト コレクションのアクセス許可セキュリティをバイパスします。</span><span class="sxs-lookup"><span data-stu-id="7d627-193">By accidentally posting the SensitiveData-BeforeIRM.docx document on the Sales site collection, the CEO bypassed the permissions security of the Executives site collection.</span></span>
  
<span data-ttu-id="7d627-194">Office 365 をフェーズ 3 と 4 のために準備するには、SharePoint Online の IRM を有効にします。</span><span class="sxs-lookup"><span data-stu-id="7d627-194">To prepare Office 365 for Phases 3 and 4, enable IRM for SharePoint Online.</span></span>
  
1. <span data-ttu-id="7d627-195">**[Microsoft Office Home]** タブで、右上部分にある [ユーザー] アイコンをクリックし、**[サインアウト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-195">On the **Microsoft Office Home** tab, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="7d627-196">[http://admin.microsoft.com](http://admin.microsoft.com) に移動します。</span><span class="sxs-lookup"><span data-stu-id="7d627-196">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="7d627-197">**Office 365 のサインイン** ページで、全体管理者のアカウント名をクリックし、パスワードを入力して、**[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-197">On the **Office 365 sign in** page, click the global administrator account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="7d627-198">**[Microsoft Office Home]** タブで、**[管理者]、[管理センター]、[SharePoint]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-198">On the **Microsoft Office Home** tab, click **Admin > Admin centers > SharePoint**.</span></span>
    
5. <span data-ttu-id="7d627-199">**[SharePoint 管理センター]** タブで、**[設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-199">On the **SharePoint admin center** tab, click **Settings**.</span></span>
    
6. <span data-ttu-id="7d627-200">**[設定]** ページの **[Information Rights Management (IRM)]** セクションで、**[構成で指定された IRM サービスを使用]** を選択し、**[IRM 設定を更新]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7d627-200">On the **Settings** page, in the **Information Rights Management (IRM)** section, select **Use the IRM service specified in your configuration**, and then select **Refresh IRM Settings**.</span></span>
    
7. <span data-ttu-id="7d627-201">**[SharePoint 管理センター]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7d627-201">Close the **SharePoint admin center** tab.</span></span>
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a><span data-ttu-id="7d627-202">フェーズ 3：SharePoint Information Rights Management を Office 365 のプライベート グループとともに使用する</span><span class="sxs-lookup"><span data-stu-id="7d627-202">Phase 3: Use SharePoint Information Rights Management with an Office 365 private group</span></span>

<span data-ttu-id="7d627-203">このフェーズでは、SharePoint Information Rights Management を Office 365 のプライベート グループとともに使用することにより、機密性の高いドキュメントが制限の緩いサイトに投稿された場合でも、そのドキュメントへのアクセスが保護されるようにします。</span><span class="sxs-lookup"><span data-stu-id="7d627-203">In this phase, you use SharePoint Information Rights Management with an Office 365 private group to protect access to a document with sensitive information, even when it is posted on a site with open permissions.</span></span>
  
<span data-ttu-id="7d627-204">最初に、エグゼクティブ サイト コレクションのドキュメント ライブラリ用に IRM を有効にして設定します。 </span><span class="sxs-lookup"><span data-stu-id="7d627-204">First, you enable and configure IRM for the documents library of the Executives site collection.</span></span> 
  
1. <span data-ttu-id="7d627-205">ブラウザーの新しいタブで、エグゼクティブサイトコレクションの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="7d627-205">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
2. <span data-ttu-id="7d627-206">**[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-206">Click **Documents**.</span></span>
    
3. <span data-ttu-id="7d627-207">右上部分にある [設定] アイコンをクリックし、**[ライブラリ設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-207">In the upper-right, click the settings icon, and then click **Library settings**.</span></span>
    
4. <span data-ttu-id="7d627-208">**[設定]** ページの **[権限と管理]** で、**[Information Rights Management]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-208">On the **Settings** page, under **Permissions and Management**, click **Information Rights Management**.</span></span>
    
5. <span data-ttu-id="7d627-209">**[Information Rights Management 設定]** ページで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="7d627-209">On the **Information Rights Management Settings** page:</span></span>
    
  - <span data-ttu-id="7d627-210">**[このライブラリのドキュメントへのアクセスをダウンロード時に制限する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7d627-210">Select **Restrict permission to documents in this library on download**.</span></span>
    
  - <span data-ttu-id="7d627-211">**[アクセス許可ポリシーのタイトルを作成]** に、「**サポート**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="7d627-211">For **Create a permission policy title**, type **Executives**.</span></span>
    
  - <span data-ttu-id="7d627-212">**[アクセス許可ポリシーの説明を追加]** に、「**エグゼクティブ用の IRM**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="7d627-212">For **Add a permission policy description**, type **IRM for executives**.</span></span>
    
6. <span data-ttu-id="7d627-213">[**オプションの表示**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-213">Click **Show Options**.</span></span>
    
7. <span data-ttu-id="7d627-214">**[IRM ライブラリの追加設定]** で、**[ユーザーに IRM をサポートしないドキュメントのアップロードを許可しない]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7d627-214">Under **Set additional IRM library settings**, select **Do not allow users to upload documents that do not support IRM**.</span></span>
    
8. <span data-ttu-id="7d627-215">**[ドキュメントのアクセス権の構成]** で、**[閲覧者に印刷を許可する]** と **[ダウンロードしたドキュメントのコピーに対する書き込みを閲覧者に許可する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7d627-215">Under **Configure document access rights**, select **Allow viewers to print** and **Allow viewers to write on a copy of the downloaded document**.</span></span>
    
9. <span data-ttu-id="7d627-216">**[グループの保護および資格情報の間隔を設定]** で、**[グループの保護を許可します]** を選択し、**[既定のグループ]** に対して「**エグゼクティブ**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="7d627-216">Under **Set group protection and credentials interval**, select **Allow group protection** and for **Default group**, type **Executives**.</span></span>
    
10. <span data-ttu-id="7d627-217">[**OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-217">Click **OK**.</span></span>
    
<span data-ttu-id="7d627-218">次に、CEO として新しいドキュメントをエグゼクティブ ドキュメント フォルダーにアップロードし、それをダウンロードして、販売ドキュメント フォルダーに誤ってアップロードします。</span><span class="sxs-lookup"><span data-stu-id="7d627-218">Next, acting as the CEO, you upload a new document to the Executives document folder, download it, then accidentally upload it to the Sales document folder.</span></span>
  
1. <span data-ttu-id="7d627-219">**SensitiveData BeforeIRM.docx** ドキュメントを格納したローカル フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="7d627-219">Open the local folder where you stored the **SensitiveData-BeforeIRM.docx** document.</span></span>
    
2. <span data-ttu-id="7d627-220">**SensitiveData-BeforeIRM.docx** を右クリックして、**[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-220">Right-click **SensitiveData-BeforeIRM.docx**, and then click **Copy**.</span></span>
    
3. <span data-ttu-id="7d627-221">フォルダー内を右クリックして、**[貼り付け]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-221">Right-click within the folder, and then click **Paste**.</span></span>
    
4. <span data-ttu-id="7d627-222">新しい**SensitiveData-beforeirm-.docx**ファイルの名前を**sensitivedata-afterirm.docx**に変更します。</span><span class="sxs-lookup"><span data-stu-id="7d627-222">Rename the new **SensitiveData-BeforeIRM - Copy.docx** file to **SensitiveData-AfterIRM.docx**.</span></span>
    
5. <span data-ttu-id="7d627-223">ブラウザーの **[Microsoft Office Home]** タブから、右上部分の [ユーザー] アイコンをクリックし、**[サインアウト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-223">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
6. <span data-ttu-id="7d627-224">[http://admin.microsoft.com](http://admin.microsoft.com) に移動します。</span><span class="sxs-lookup"><span data-stu-id="7d627-224">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
7. <span data-ttu-id="7d627-225">**Office 365 のサインイン** ページで、CEO アカウント名をクリックし、パスワードを入力して、**[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-225">On the **Office 365 sign in** page, click the CEO account name, type its password, and then click **Sign in**.</span></span>
    
8. <span data-ttu-id="7d627-226">ブラウザーの新しいタブで、エグゼクティブサイトコレクションの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="7d627-226">On a new tab of your browser, type the URL to the Executives site collection.</span></span>
    
9. <span data-ttu-id="7d627-227">**[ドキュメント]** ページで、**[アップロード]** をクリックし、ローカル フォルダーの **SensitiveData-AfterIRM.docx** ドキュメントを指定して、**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-227">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
10. <span data-ttu-id="7d627-228">**[ドキュメント]** ページで新しい **SensitiveData-AfterIRM.docx** ドキュメントを選び、メニュー バーの省略記号 (...) をクリックして、**[ダウンロード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-228">Select the new **SensitiveData-AfterIRM.docx** document in the **Documents** page, click the ellipsis (…) in the menu bar, and then click **Download**.</span></span>
    
11. <span data-ttu-id="7d627-229">画面の指示に従って **SensitiveData-AfterIRM.docx** ドキュメントをローカル フォルダーに保存して、元のバージョンを上書きします。</span><span class="sxs-lookup"><span data-stu-id="7d627-229">When prompted, save the **SensitiveData-AfterIRM.docx** document in your local folder, overwriting the original version.</span></span>
    
12. <span data-ttu-id="7d627-230">**[ドキュメント]** ページのタブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7d627-230">Close the tab for the **Documents** page.</span></span>
    
13. <span data-ttu-id="7d627-231">ブラウザーの新しいタブで、Sales サイトコレクションの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="7d627-231">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
14. <span data-ttu-id="7d627-232">**[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-232">Click **Documents**.</span></span>
    
15. <span data-ttu-id="7d627-233">**[ドキュメント]** ページで、**[アップロード]** をクリックし、ローカル フォルダーの **SensitiveData-AfterIRM.docx** ドキュメントを指定して、**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-233">On the **Documents** page, click **Upload**, specify the **SensitiveData-AfterIRM.docx** document in your local folder, and then click **Open**.</span></span>
    
16. <span data-ttu-id="7d627-234">**[販売サイト コレクション]** と **[SharePoint]** のタブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7d627-234">Close the **Sales site collection** and **SharePoint** tabs.</span></span>
    
<span data-ttu-id="7d627-235">次に、通常のユーザーとして販売ドキュメント フォルダーの **SensitiveData-AfterIRM.docx** ドキュメントにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="7d627-235">Next, acting as a normal user, you try to access the **SensitiveData-AfterIRM.docx** document in the Sales document folder.</span></span>
  
1. <span data-ttu-id="7d627-236">ブラウザーの **[Microsoft Office Home]** タブから、右上部分の [ユーザー] アイコンをクリックし、**[サインアウト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-236">From the **Microsoft Office Home** tab in your browser, click the user icon in the upper-right, and then click **Sign out**.</span></span>
    
2. <span data-ttu-id="7d627-237">[http://admin.microsoft.com](http://admin.microsoft.com) に移動します。</span><span class="sxs-lookup"><span data-stu-id="7d627-237">Go to [http://admin.microsoft.com](http://admin.microsoft.com).</span></span>
    
3. <span data-ttu-id="7d627-238">**Office 365 のサインイン**ページで、User5 のアカウント名をクリックし、パスワードを入力して、[**サインイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-238">On the **Office 365 sign in** page, click the User5 account name, type its password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="7d627-239">ブラウザーの新しいタブで、Sales サイトコレクションの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="7d627-239">On a new tab of your browser, type the URL to the Sales site collection.</span></span>
    
5. <span data-ttu-id="7d627-240">**[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-240">Click **Documents**.</span></span>
    
6. <span data-ttu-id="7d627-241">**[ドキュメント]** ページで、**SensitiveData-AfterIRM.docx** を開きます。 </span><span class="sxs-lookup"><span data-stu-id="7d627-241">On the **Documents** page, open the **SensitiveData-AfterIRM.docx** document.</span></span>
    
    <span data-ttu-id="7d627-242">「申し訳ありません。このドキュメントは Information Rights Management (IRM) によって保護されているため、Word Online で開くことはできません。」というメッセージが表示されます。 </span><span class="sxs-lookup"><span data-stu-id="7d627-242">You should see a message that states "Sorry, Word Online can't open this document because it's protected by Information Rights Management (IRM)."</span></span> 
    
7. <span data-ttu-id="7d627-p105">**[Word で編集]** をクリックします。ファイルを開くかどうかを尋ねられます。**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-p105">Click **Edit in Word**. You are prompted if you want to open the file. Click **Yes**.</span></span>
    
8. <span data-ttu-id="7d627-p106">サインインするように要求されます。User5 アカウントのアカウント名を入力し、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-p106">You are prompted to sign-in. Type the account name of the User5 account, and then click **Next**.</span></span>
    
9. <span data-ttu-id="7d627-p107">パスワードを入力するように要求されます。User5 アカウント用のパスワードを入力して、**[サインイン]** をクリックします。 </span><span class="sxs-lookup"><span data-stu-id="7d627-p107">You are prompted to provide the password. Type the password for the User5 account and then click **Sign in**.</span></span> 
    
    <span data-ttu-id="7d627-250">次のメッセージが表示されます。「このドキュメントを開くための資格情報がありません。」</span><span class="sxs-lookup"><span data-stu-id="7d627-250">You should see the a message that states: "You do not have the credentials that allow you to open this document."</span></span>
    
10. <span data-ttu-id="7d627-251">**[いいえ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d627-251">Click **No**.</span></span>
    
<span data-ttu-id="7d627-p108">IRM 保護を確認する別の方法として、ローカル フォルダー内のファイルを確認することもできます。**SensitiveData-AfterIRM.docx** ファイルは、**SensitiveData-BeforeIRM.docx** ファイルより大きいはずです。**SensitiveData-AfterIRM.docx** ファイルは暗号化されており、IRM 保護情報が追加されています。</span><span class="sxs-lookup"><span data-stu-id="7d627-p108">Another way to see the IRM protection is to look at the files in your local folder. The **SensitiveData-AfterIRM.docx** should be much larger than the **SensitiveData-BeforeIRM.docx** file. The **SensitiveData-AfterIRM.docx** file is encrypted and has the IRM protection information added to it.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7d627-255">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d627-255">See Also</span></span>

[<span data-ttu-id="7d627-256">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="7d627-256">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="7d627-257">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="7d627-257">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="7d627-258">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="7d627-258">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="7d627-259">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="7d627-259">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


