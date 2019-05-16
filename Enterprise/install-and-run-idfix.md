---
title: Office 365 IdFix ツールのインストールと実行
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Office 365 IdFix ツールをインストールして実行し、office 365 に同期する前に active directory をクリーンアップする方法について説明します。
ms.openlocfilehash: 4197694ce90ab600652aa729809ef0ddb0647e03
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067293"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="922f9-103">Office 365 IdFix ツールのインストールと実行</span><span class="sxs-lookup"><span data-stu-id="922f9-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="922f9-104">IdFix を使用すると、Office 365 と同期する前に、ディレクトリ内の重複や書式設定の問題などのエラーが識別されます。</span><span class="sxs-lookup"><span data-stu-id="922f9-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="922f9-105">このタスクを正常に完了するには、Active Directory 内のユーザー、グループ、および連絡先オブジェクトに慣れている必要があります。</span><span class="sxs-lookup"><span data-stu-id="922f9-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="922f9-106">このタスクを完了できない場合は、他にもいくつかの操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="922f9-106">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="922f9-107">これらのメソッドは簡単になる場合もありますが、時間がかかる場合や他の欠点がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="922f9-107">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="922f9-108">以下にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="922f9-108">They are:</span></span>
  
- <span data-ttu-id="922f9-109">**IdFix を実行せずにディレクトリ同期を実行します。**</span><span class="sxs-lookup"><span data-stu-id="922f9-109">**Run directory synchronization without running IdFix.**</span></span> <span data-ttu-id="922f9-110">IdFix ツールを実行せずにディレクトリを同期することはできますが、お勧めしません。</span><span class="sxs-lookup"><span data-stu-id="922f9-110">You can synchronize your directory without running the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="922f9-111">同期の前にエラーを修正するには時間がかかり、多くの場合、クラウドへの移行がよりスムーズになります。</span><span class="sxs-lookup"><span data-stu-id="922f9-111">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="922f9-112">**コンサルタントを雇う。**</span><span class="sxs-lookup"><span data-stu-id="922f9-112">**Hire a consultant.**</span></span> <span data-ttu-id="922f9-113">専門家のヘルプを利用することで、ユーザーの作業を迅速に行い、ディレクトリを同期させることができます。</span><span class="sxs-lookup"><span data-stu-id="922f9-113">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="922f9-114">IdFix を実行するために必要なこと</span><span class="sxs-lookup"><span data-stu-id="922f9-114">What you need to run IdFix</span></span>

<span data-ttu-id="922f9-115">IdFix を入手して実行する最も簡単な方法は、ドメインに参加しているコンピューターにインストールすることです。</span><span class="sxs-lookup"><span data-stu-id="922f9-115">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain.</span></span> <span data-ttu-id="922f9-116">必要であれば、ドメインコントローラー上で実行できますが、これは必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="922f9-116">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="922f9-117">IdFix のハードウェア要件</span><span class="sxs-lookup"><span data-stu-id="922f9-117">IdFix hardware requirements</span></span>

<span data-ttu-id="922f9-118">IdFix をインストールするコンピューターは、以下の最小ハードウェア要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="922f9-118">The computer where you install IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="922f9-119">4 GB の RAM</span><span class="sxs-lookup"><span data-stu-id="922f9-119">4 GB RAM</span></span>
- <span data-ttu-id="922f9-120">2 GB のハードディスク容量</span><span class="sxs-lookup"><span data-stu-id="922f9-120">2 GB of hard disk space</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="922f9-121">IdFix ソフトウェアの要件</span><span class="sxs-lookup"><span data-stu-id="922f9-121">IdFix software requirements</span></span>

<span data-ttu-id="922f9-122">IdFix をインストールするコンピューターは、ユーザーを Office 365 に同期するのと同じ Active Directory ドメインに参加させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="922f9-122">The computer where you install IdFix needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365.</span></span> <span data-ttu-id="922f9-123">また、コンピューターには .NET Framework 4.0 がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="922f9-123">The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="922f9-124">Windows Server 2008 または Windows Server 2012 を実行している場合は、.NET Framework が既にインストールされている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="922f9-124">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed.</span></span> <span data-ttu-id="922f9-125">それ以外の場合は、ダウンロードセンターから、または Windows Update を通じ[て .net 4.0 をダウンロード](https://go.microsoft.com/fwlink/p/?LinkId=400475)することができます。</span><span class="sxs-lookup"><span data-stu-id="922f9-125">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or via Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="922f9-126">IdFix 権限の要件</span><span class="sxs-lookup"><span data-stu-id="922f9-126">IdFix permissions requirements</span></span>

<span data-ttu-id="922f9-127">IdFix を実行するために使用するユーザーアカウントは、ディレクトリへの読み取り/書き込みアクセス権を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="922f9-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="922f9-128">ユーザーアカウントがこれらの要件を満たしているかどうかを確認できず、確認する方法がわからない場合でも、IdFix をインストールして実行することができます。</span><span class="sxs-lookup"><span data-stu-id="922f9-128">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix.</span></span> <span data-ttu-id="922f9-129">ユーザーアカウントが適切なアクセス許可を持っていない場合、IdFix は、実行しようとしたときにエラーを表示するだけです。</span><span class="sxs-lookup"><span data-stu-id="922f9-129">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="922f9-130">IdFix のインストール</span><span class="sxs-lookup"><span data-stu-id="922f9-130">Install IdFix</span></span>

<span data-ttu-id="922f9-131">IdFix をインストールするには、次のようにして、 **idfix .exe**をダウンロードして解凍します。</span><span class="sxs-lookup"><span data-stu-id="922f9-131">To install IdFix, download and unzip **IdFix.exe**:</span></span> 
  
1. <span data-ttu-id="922f9-132">IdFix ツールをインストールするコンピューターにログオンします。</span><span class="sxs-lookup"><span data-stu-id="922f9-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="922f9-133">[Idfix DirSync エラー修復ツール](https://go.microsoft.com/fwlink/?linkid=867219)の Microsoft ダウンロードサイトに移動します。</span><span class="sxs-lookup"><span data-stu-id="922f9-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="922f9-134">[**Download**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="922f9-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="922f9-135">メッセージが表示されたら、[**実行**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="922f9-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="922f9-136">[ **WinZip 自己抽出**機能] ダイアログボックスの [**フォルダーに解凍**] テキストボックスに、idfix ツールをインストールする場所を入力または参照します。</span><span class="sxs-lookup"><span data-stu-id="922f9-136">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool.</span></span> <span data-ttu-id="922f9-137">既定では、IdFix はに`C:\Deployment Tools\`インストールされます。</span><span class="sxs-lookup"><span data-stu-id="922f9-137">By default, IdFix is installed into `C:\Deployment Tools\`.</span></span> 
    
6. <span data-ttu-id="922f9-138">[ **Unzip**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="922f9-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="922f9-139">IdFix ツールを実行する</span><span class="sxs-lookup"><span data-stu-id="922f9-139">Run the IdFix tool</span></span>

<span data-ttu-id="922f9-140">IdFix をインストールした後、ツールを実行して、ディレクトリ内の問題を検索します。</span><span class="sxs-lookup"><span data-stu-id="922f9-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="922f9-141">ディレクトリへの読み取り/書き込みアクセス権を持つアカウントを使用して、IdFix をインストールしたコンピューターにログオンします。</span><span class="sxs-lookup"><span data-stu-id="922f9-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="922f9-142">エクスプローラーで、IdFix をインストールした場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="922f9-142">In File Explorer, go to the location where you installed IdFix.</span></span> <span data-ttu-id="922f9-143">インストール時に既定のフォルダーを選択した場合`C:\Deployment Tools\IdFix`は、に移動します。</span><span class="sxs-lookup"><span data-stu-id="922f9-143">If you chose the default folder during installation, go to `C:\Deployment Tools\IdFix`.</span></span>
    
3. <span data-ttu-id="922f9-144">[ **Idfix**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="922f9-144">Double-click **IdFix.exe**.</span></span> 
    
    ![IdFix .exe ファイルを選択します。](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="922f9-146">既定では、IdFix はマルチテナントルールセットを使用して、ディレクトリ内のエントリをテストします。</span><span class="sxs-lookup"><span data-stu-id="922f9-146">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="922f9-147">これは、ほとんどの Office 365 お客様のための適切なルールセットです。</span><span class="sxs-lookup"><span data-stu-id="922f9-147">This is the right rule set for most Office 365 customers.</span></span> <span data-ttu-id="922f9-148">ただし、Office 365 専用または ITAR (肘掛けされた国際トラフィック) のお客様の場合は、IdFix を構成して、代わりに専用のルールセットを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="922f9-148">However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="922f9-149">お客様の種類がわからない場合は、この手順を省略しても問題ありません。</span><span class="sxs-lookup"><span data-stu-id="922f9-149">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="922f9-150">ルールセットを専用に設定するには、メニューバーの歯車アイコンをクリックして、[**専用**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="922f9-150">To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="922f9-151">[**クエリ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="922f9-151">Choose **Query**.</span></span>
    
    ![IdFix で [クエリ] を選択します。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="922f9-153">既定では、IdFix はディレクトリ全体を検索してエラーを検出します。</span><span class="sxs-lookup"><span data-stu-id="922f9-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="922f9-154">ディレクトリのサイズによっては、クエリの実行に時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="922f9-154">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="922f9-155">ツールのメインウィンドウの下部にある進捗状況を確認できます。</span><span class="sxs-lookup"><span data-stu-id="922f9-155">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="922f9-156">[**キャンセル**] をクリックした場合は、最初から再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="922f9-156">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![IdFix クエリとエラーカウント。](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="922f9-158">IdFix がクエリを完了したら、エラーがない場合にディレクトリを同期することができます。</span><span class="sxs-lookup"><span data-stu-id="922f9-158">After IdFix completes the query, you can go ahead and synchronize your directory if there are no errors.</span></span> <span data-ttu-id="922f9-159">ディレクトリにエラーがある場合は、同期する前にそれらを修正することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="922f9-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="922f9-160">エラーの種類や、それぞれの問題を解決するための推奨事項についてのより詳細な情報が必要な場合は、このトピックの最後にあるリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="922f9-160">If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="922f9-161">同期する前にエラーを修正することは必須ではありませんが、IdFix から返されたすべてのエラーを少なくとも確認することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="922f9-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="922f9-162">各エラーは、ツールのメインウィンドウの独立した行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="922f9-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="922f9-163">[**更新**] 列の提案された変更に同意する場合は、[**アクション**] 列で、変更を実装するために idfix を実行する対象を選択し、[**適用**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="922f9-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="922f9-164">[**適用**] をクリックすると、ツールによってディレクトリ内の変更が行われます。</span><span class="sxs-lookup"><span data-stu-id="922f9-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="922f9-165">更新のたびに [**適用**] をクリックする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="922f9-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="922f9-166">その代わりに、[**適用**] をクリックする前にいくつかのエラーを修正し、idfix によってすべて同時に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="922f9-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="922f9-167">エラーの種類を一覧表示する列の上部にある [**エラー** ] をクリックすると、エラーの種類別にエラーを並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="922f9-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="922f9-168">1つの方法は、同じ種類のすべてのエラーを修正することです。たとえば、最初にすべての重複を修正して適用します。</span><span class="sxs-lookup"><span data-stu-id="922f9-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="922f9-169">次に、文字書式エラーなどを修正します。</span><span class="sxs-lookup"><span data-stu-id="922f9-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="922f9-170">変更を適用するたびに、IdFix ツールによって別のログファイルが作成されます。このファイルを使用すると、誤った変更を行った場合に、変更を元に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="922f9-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="922f9-171">[トランザクションログ](idfix-transaction-log.md)は、インストールした idfix のフォルダーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="922f9-171">The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.</span></span>  <span data-ttu-id="922f9-172">既定では、 _C:\windows 展開ツール \ 修正プログラム_が適用されます。</span><span class="sxs-lookup"><span data-stu-id="922f9-172">_C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![IdFix で修復エラーが発生しました。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="922f9-174">ディレクトリにすべての変更が加えられたら、IdFix を再度実行して、作成した修正プログラムで新しいエラーが発生していないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="922f9-174">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="922f9-175">必要な回数だけこれらの手順を繰り返すことができます。</span><span class="sxs-lookup"><span data-stu-id="922f9-175">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="922f9-176">同期する前に、このプロセスを何度か実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="922f9-176">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="922f9-177">検索を絞り込んだり、エラーに深く掘り下げたりするには、IdFix で何を実行できるか。</span><span class="sxs-lookup"><span data-stu-id="922f9-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="922f9-178">詳細については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="922f9-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="922f9-179">[IdFix ツールを使用して、Office 365 と同期するディレクトリ属性を準備](prepare-directory-attributes-for-synch-with-idfix.md)します。</span><span class="sxs-lookup"><span data-stu-id="922f9-179">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) .</span></span> <span data-ttu-id="922f9-180">ツールをインストールしたら、このトピックに移動して、ツールの実行方法、発生する一般的なエラー、推奨される修正、例、および多数のエラーが発生した場合の対処方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="922f9-180">After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="922f9-181">リファレンス: IdFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性</span><span class="sxs-lookup"><span data-stu-id="922f9-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="922f9-182">リファレンス: Office 365 IdFix トランザクション ログ</span><span class="sxs-lookup"><span data-stu-id="922f9-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="922f9-183">ビデオ トレーニング</span><span class="sxs-lookup"><span data-stu-id="922f9-183">Video training</span></span>

<span data-ttu-id="922f9-184">詳細については、レッスン「[インストールと使用](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US)」を参照してください。このツールは、LinkedIn Learning によって提供されています。</span><span class="sxs-lookup"><span data-stu-id="922f9-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US), brought to you by LinkedIn Learning.</span></span>
  

