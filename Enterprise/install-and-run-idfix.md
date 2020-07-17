---
title: Microsoft 365 IdFix ツールをダウンロードして実行する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_HRCSetupAADConnectIDFixLM617036
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Microsoft 365 IdFix ツールをダウンロードして実行し、Active Directory ドメインサービス (AD DS) をクリーンアップしてから、Microsoft 365 に同期させる方法。
ms.openlocfilehash: c4df63e6162b1d53cb7a45f046542443177b25ff
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774862"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a><span data-ttu-id="9a9a0-103">Microsoft 365 IdFix ツールをダウンロードして実行する</span><span class="sxs-lookup"><span data-stu-id="9a9a0-103">Download and run the Microsoft 365 IdFix tool</span></span>

<span data-ttu-id="9a9a0-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="9a9a0-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="9a9a0-105">IdFix は、Microsoft 365 に同期する前に Active Directory ドメインサービス (AD DS) ドメイン内の重複や書式設定の問題などのエラーを識別します。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-105">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Microsoft 365.</span></span> 
  
<span data-ttu-id="9a9a0-106">このタスクを正常に完了するには、AD DS 内のユーザー、グループ、および連絡先オブジェクトに慣れている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-106">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="9a9a0-107">このタスクを完了できない場合は、他にもいくつかの操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-107">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="9a9a0-108">これらのメソッドは簡単になる場合もありますが、時間がかかる場合や他の欠点がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-108">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="9a9a0-109">以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-109">They are:</span></span>
  
- <span data-ttu-id="9a9a0-110">**IdFix を実行せずにディレクトリ同期を実行する**</span><span class="sxs-lookup"><span data-stu-id="9a9a0-110">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="9a9a0-111">IdFix ツールを使用せずにディレクトリを同期することはできますが、お勧めしません。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-111">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="9a9a0-112">同期の前にエラーを修正するには時間がかかり、多くの場合、クラウドへの移行がよりスムーズになります。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-112">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="9a9a0-113">**コンサルタントの雇用**</span><span class="sxs-lookup"><span data-stu-id="9a9a0-113">**Hire a consultant**</span></span> 

  <span data-ttu-id="9a9a0-114">専門家のヘルプを利用することで、ユーザーの作業を迅速に行い、ディレクトリを同期させることができます。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-114">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="9a9a0-115">IdFix を実行するために必要なこと</span><span class="sxs-lookup"><span data-stu-id="9a9a0-115">What you need to run IdFix</span></span>

<span data-ttu-id="9a9a0-116">IdFix を入手して実行する最も簡単な方法は、AD DS ドメインに参加しているコンピューターにダウンロードすることです。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-116">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="9a9a0-117">必要であれば、ドメインコントローラー上で実行できますが、これは必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-117">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="9a9a0-118">IdFix のハードウェア要件</span><span class="sxs-lookup"><span data-stu-id="9a9a0-118">IdFix hardware requirements</span></span>

<span data-ttu-id="9a9a0-119">IdFix をダウンロードするコンピューターは、以下の最小ハードウェア要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-119">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="9a9a0-120">4 GB の RAM</span><span class="sxs-lookup"><span data-stu-id="9a9a0-120">4 GB RAM</span></span>
- <span data-ttu-id="9a9a0-121">2 GB のハードディスク容量</span><span class="sxs-lookup"><span data-stu-id="9a9a0-121">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="9a9a0-122">IdFix ソフトウェアの要件</span><span class="sxs-lookup"><span data-stu-id="9a9a0-122">IdFix software requirements</span></span>

<span data-ttu-id="9a9a0-123">IdFix をダウンロードしたコンピューターは、ユーザーを Microsoft 365 に同期するのと同じ AD DS ドメインに参加させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-123">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Microsoft 365.</span></span> 

<span data-ttu-id="9a9a0-124">また、コンピューターには .NET Framework 4.0 がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-124">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="9a9a0-125">Windows Server 2008 以降を実行している場合は、.NET Framework が既にインストールされている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-125">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="9a9a0-126">それ以外の場合は、ダウンロードセンターまたは Windows Update[から .net 4.0 をダウンロード](https://go.microsoft.com/fwlink/p/?LinkId=400475)することができます。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-126">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="9a9a0-127">IdFix 権限の要件</span><span class="sxs-lookup"><span data-stu-id="9a9a0-127">IdFix permissions requirements</span></span>

<span data-ttu-id="9a9a0-128">IdFix を実行するために使用するユーザーアカウントには、AD DS ドメインに対する読み取りおよび書き込みアクセス権が必要です。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-128">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="9a9a0-129">ユーザーアカウントがこれらの要件を満たしているかどうかがわからず、確認する方法がわからない場合でも、IdFix をダウンロードして実行することができます。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-129">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="9a9a0-130">ユーザーアカウントが適切なアクセス許可を持っていない場合、IdFix は、実行しようとしたときにエラーを表示するだけです。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-130">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="9a9a0-131">IdFix のダウンロードと抽出</span><span class="sxs-lookup"><span data-stu-id="9a9a0-131">Download and extract IdFix</span></span>

<span data-ttu-id="9a9a0-132">次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-132">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="9a9a0-133">IdFix ツールを実行するコンピューターにサインインします。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-133">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="9a9a0-134">[Idfix DirSync Error 修復ツール](https://github.com/microsoft/idfix)サイトに移動します。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-134">Go to the [IdFix DirSync Error Remediation Tool](https://github.com/microsoft/idfix) site.</span></span>
    
3. <span data-ttu-id="9a9a0-135">**ClickOnce 起動**セクションの [**起動**] をクリックして、zip ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-135">Click **launch** in the **ClickOnce Launch** section to download the zip file.</span></span> <span data-ttu-id="9a9a0-136">Zip ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-136">Open the zip file.</span></span>
    
4. <span data-ttu-id="9a9a0-137">**Idfix**ウィンドウで、[**抽出**] を選択し、[**すべて抽出**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-137">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="9a9a0-138">既定では、IdFix はに展開され `C:\Users\<your user name>\Documents\IdFix` ます。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-138">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
5. <span data-ttu-id="9a9a0-139">[**展開**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-139">Choose **Extract**.</span></span>

<span data-ttu-id="9a9a0-140">手順は、使用している Windows およびインターネットブラウザーのバージョンによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-140">Your steps might vary based on your version of Windows and your Internet browser.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="9a9a0-141">IdFix ツールを実行する</span><span class="sxs-lookup"><span data-stu-id="9a9a0-141">Run the IdFix tool</span></span>

<span data-ttu-id="9a9a0-142">IdFix をダウンロードして抽出した後、それを実行して AD DS ドメインの問題を検索します。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-142">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="9a9a0-143">AD DS ドメインに対する読み取り/書き込みアクセス権を持つアカウントを使用して、IdFix をダウンロードしたコンピューターにサインインします。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-143">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="9a9a0-144">エクスプローラーで、IdFix を抽出した場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-144">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="9a9a0-145">抽出中に既定のフォルダーを選択した場合は、に移動 `C:\Users\<your user name>\Documents\IdFix` します。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-145">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="9a9a0-146">[ **IdFix.exe**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-146">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="9a9a0-147">既定では、IdFix はマルチテナントルールセットを使用して、ディレクトリ内のエントリをテストします。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-147">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="9a9a0-148">これは、ほとんどの Microsoft 365 お客様のための適切なルールセットです。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-148">This is the right rule set for most Microsoft 365 customers.</span></span> <span data-ttu-id="9a9a0-149">ただし、Microsoft 365 の専用または国際トラフィック (ITAR) のお客様の場合は、IdFix を構成して、代わりに専用のルールセットを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-149">However, if you are a Microsoft 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="9a9a0-150">お客様の種類がわからない場合は、この手順を省略しても問題ありません。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-150">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="9a9a0-151">ルールセットを専用に設定するには、メニューバーの歯車アイコンをクリックして、[**専用**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-151">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="9a9a0-152">[**クエリ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-152">Choose **Query**.</span></span>
    
    ![IdFix で [クエリ] を選択します。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="9a9a0-154">既定では、IdFix はディレクトリ全体を検索してエラーを検出します。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-154">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="9a9a0-155">ディレクトリのサイズによっては、クエリの実行に時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-155">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="9a9a0-156">ツールのメインウィンドウの下部にある進捗状況を確認できます。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-156">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="9a9a0-157">[**キャンセル**] をクリックした場合は、最初から再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-157">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="9a9a0-158">IdFix がクエリを完了した後、エラーがない場合はディレクトリを同期することができます。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-158">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="9a9a0-159">ディレクトリにエラーがある場合は、同期する前にそれらを修正することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="9a9a0-160">詳細については、「 [Microsoft 365 と同期するためのディレクトリ属性の準備](prepare-directory-attributes-for-synch-with-idfix.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-160">See [prepare directory attributes for synchronization with Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="9a9a0-161">同期する前にエラーを修正することは必須ではありませんが、IdFix から返されたすべてのエラーを少なくとも確認することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="9a9a0-162">各エラーは、ツールのメインウィンドウの独立した行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="9a9a0-163">[**更新**] 列の提案された変更に同意する場合は、[**アクション**] 列で、変更を実装するために idfix を実行する対象を選択し、[**適用**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="9a9a0-164">[**適用**] をクリックすると、ツールによってディレクトリ内の変更が行われます。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="9a9a0-165">更新のたびに [**適用**] をクリックする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="9a9a0-166">その代わりに、[**適用**] をクリックする前にいくつかのエラーを修正し、idfix によってすべて同時に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="9a9a0-167">エラーの種類を一覧表示する列の上部にある [**エラー** ] をクリックすると、エラーの種類別にエラーを並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="9a9a0-168">1つの方法は、同じ種類のすべてのエラーを修正することです。たとえば、最初にすべての重複を修正して適用します。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="9a9a0-169">次に、文字書式エラーなどを修正します。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="9a9a0-170">変更を適用するたびに、IdFix ツールによって別のログファイルが作成されます。このファイルを使用すると、誤った変更を行った場合に、変更を元に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="9a9a0-171">[トランザクションログ](idfix-transaction-log.md)は、idfix を抽出したフォルダーに格納されます。これは、既定では_C:\Users \<your user name> \Documents\IdFix_です。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-171">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![IdFix で修復エラーが発生しました。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="9a9a0-173">ディレクトリにすべての変更が加えられたら、IdFix を再度実行して、作成した修正プログラムで新しいエラーが発生していないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-173">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="9a9a0-174">必要な回数だけこれらの手順を繰り返すことができます。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-174">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="9a9a0-175">同期する前に、このプロセスを何度か実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9a9a0-175">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="9a9a0-176">IdFix に関するその他の技術情報</span><span class="sxs-lookup"><span data-stu-id="9a9a0-176">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="9a9a0-177">IdFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性</span><span class="sxs-lookup"><span data-stu-id="9a9a0-177">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="9a9a0-178">Microsoft 365 IdFix トランザクションログ</span><span class="sxs-lookup"><span data-stu-id="9a9a0-178">Microsoft 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
