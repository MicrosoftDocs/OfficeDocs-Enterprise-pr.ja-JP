---
title: Microsoft 365 IDFix ツールのダウンロードと実行
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Priority
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
description: Microsoft 365 IDFix ツールをダウンロードして実行し、Active Directory ドメイン サービス (AD DS) をクリーンアップしてから Microsoft 365 に同期する方法について説明します。
ms.openlocfilehash: beef13857ad00806cc3e62aedd7a1b3c48bfe4c0
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502662"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a><span data-ttu-id="2c089-103">Microsoft 365 IDFix ツールのダウンロードと実行</span><span class="sxs-lookup"><span data-stu-id="2c089-103">Download and run the Microsoft 365 IdFix tool</span></span>

<span data-ttu-id="2c089-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="2c089-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="2c089-105">IDFix は、Microsoft 365に同期する前に、Active Directory Domain Services (AD DS) ドメイン内にある重複や形式設定の問題などのエラーを特定します。</span><span class="sxs-lookup"><span data-stu-id="2c089-105">IdFix identifies errors such as duplicates and formatting problems in your Active Directory Domain Services (AD DS) domain before you synchronize to Microsoft 365.</span></span> 
  
<span data-ttu-id="2c089-106">このタスクを正常に終了するには、AD DS でユーザー、グループ、連絡先のオブジェクトを簡単に操作できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c089-106">To finish this task successfully, you should be comfortable working with user, group, and contact objects in AD DS.</span></span>
  
<span data-ttu-id="2c089-107">このタスクを完了できない場合は、他にいくつか方法があります。</span><span class="sxs-lookup"><span data-stu-id="2c089-107">If you can't complete this task, there are a couple of other things you can do.</span></span> <span data-ttu-id="2c089-108">これらの方法はより簡単ですが、時間がかかる場合や、他に不具合が出る場合があります。</span><span class="sxs-lookup"><span data-stu-id="2c089-108">These methods might be easier, but they might also take longer or have other drawbacks.</span></span> <span data-ttu-id="2c089-109">以下にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="2c089-109">They are:</span></span>
  
- <span data-ttu-id="2c089-110">**IDFix を実行せずにディレクトリ同期を実行する**</span><span class="sxs-lookup"><span data-stu-id="2c089-110">**Run directory synchronization without running IdFix**</span></span> 

  <span data-ttu-id="2c089-111">IDFix ツールを使用せずディレクトリを同期できますが、これは推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="2c089-111">You can synchronize your directory without using the IdFix tool, but we don't recommend it.</span></span> <span data-ttu-id="2c089-112">同期前のエラー修正は短時間で行うことができ、多くの場合、クラウドによりスムーズに移行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2c089-112">Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 

- <span data-ttu-id="2c089-113">**コンサルタントを雇う**</span><span class="sxs-lookup"><span data-stu-id="2c089-113">**Hire a consultant**</span></span> 

  <span data-ttu-id="2c089-114">専門家に援助してもらうと、ユーザーは迅速に実務に使用でき、管理者はディレクトリ同期を完了させることができます。</span><span class="sxs-lookup"><span data-stu-id="2c089-114">Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="2c089-115">IDFix を実行するために必要な事柄</span><span class="sxs-lookup"><span data-stu-id="2c089-115">What you need to run IdFix</span></span>

<span data-ttu-id="2c089-116">IDFix を実行するための最も簡単な方法は、ご使用の AD DS ドメインに参加しているコンピューターにダウンロードすることです。</span><span class="sxs-lookup"><span data-stu-id="2c089-116">The easiest way to get IdFix up and running is to download it onto a computer that is joined to your AD DS domain.</span></span> <span data-ttu-id="2c089-117">希望する場合にはドメイン コントローラーで実行できますが、必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="2c089-117">You can run it on the domain controller if you want, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="2c089-118">IDFix のハードウェア要件</span><span class="sxs-lookup"><span data-stu-id="2c089-118">IdFix hardware requirements</span></span>

<span data-ttu-id="2c089-119">IDFix をダウンロードするコンピューターは、以下のハードウェア要件を最低限満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c089-119">The computer where you download IdFix needs to meet these minimum hardware requirements:</span></span>
  
- <span data-ttu-id="2c089-120">4 GB RAM</span><span class="sxs-lookup"><span data-stu-id="2c089-120">4 GB RAM</span></span>
- <span data-ttu-id="2c089-121">2 GB のハードディスク容量</span><span class="sxs-lookup"><span data-stu-id="2c089-121">2 GB of hard disk space</span></span>
   
### <a name="idfix-software-requirements"></a><span data-ttu-id="2c089-122">IDFix のソフトウェア要件</span><span class="sxs-lookup"><span data-stu-id="2c089-122">IdFix software requirements</span></span>

<span data-ttu-id="2c089-123">IDFix をダウンロードするコンピューターは、Microsoft 365 に同期するユーザーが存在する AD DS ドメインと同じドメインに参加している必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c089-123">The computer where you download IdFix needs to be joined to the same AD DS domain from which you want to synchronize users to Microsoft 365.</span></span> 

<span data-ttu-id="2c089-124">またコンピューターには .NET Framework 4.0 をインストールしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c089-124">The computer also needs to have .NET Framework 4.0 installed.</span></span> <span data-ttu-id="2c089-125">Windows Server 2008 以降を実行している場合は、.NET Framework が既にインストールされている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2c089-125">If you are running Windows Server 2008 or later, the .NET Framework is probably already installed.</span></span> <span data-ttu-id="2c089-126">表示されていない場合は、[[ダウンロードセンター]](https://go.microsoft.com/fwlink/p/?LinkId=400475) または [Windows Update] から .NET 4.0 をダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="2c089-126">If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or with Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="2c089-127">IDFix アクセス許可の要件</span><span class="sxs-lookup"><span data-stu-id="2c089-127">IdFix permissions requirements</span></span>

<span data-ttu-id="2c089-128">IDFix を実行するためのユーザー アカウントには、AD DS ドメインへの読み取り/書き込みアクセス権が必要です。</span><span class="sxs-lookup"><span data-stu-id="2c089-128">The user account that you use to run IdFix must have read and write access to the AD DS domain.</span></span>
  
<span data-ttu-id="2c089-129">使用しているユーザー アカウントがこうした要件を満たしているかどうか不確かで、その確認方法が分からない場合であっても、IDFix のダウンロードして実行することは可能です。</span><span class="sxs-lookup"><span data-stu-id="2c089-129">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still download and run IdFix.</span></span> <span data-ttu-id="2c089-130">ユーザー アカウントに正しい許可がない場合、実行を試みると IDFix によってその旨のエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c089-130">If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="download-and-extract-idfix"></a><span data-ttu-id="2c089-131">IDFix をダウンロードして抽出する</span><span class="sxs-lookup"><span data-stu-id="2c089-131">Download and extract IdFix</span></span>

<span data-ttu-id="2c089-132">手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2c089-132">Follow these instructions.</span></span> 
  
1. <span data-ttu-id="2c089-133">IDFix ツールを実行するコンピューターにサインインします。</span><span class="sxs-lookup"><span data-stu-id="2c089-133">Sign in to the computer where you want to run the IdFix tool.</span></span>
    
2. <span data-ttu-id="2c089-134">[IDFix DirSync エラー修復ツール](https://github.com/microsoft/idfix) のサイトに移動します。</span><span class="sxs-lookup"><span data-stu-id="2c089-134">Go to the [IdFix DirSync Error Remediation Tool](https://github.com/microsoft/idfix) site.</span></span>
    
3. <span data-ttu-id="2c089-135">[**ClickOnce 起動**] セクションの [**起動**] をクリックして、zip ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="2c089-135">Click **launch** in the **ClickOnce Launch** section to download the zip file.</span></span> <span data-ttu-id="2c089-136">Zip ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="2c089-136">Open the zip file.</span></span>
    
4. <span data-ttu-id="2c089-137">[**IdFix**] ウィンドウで、[**抽出**] を選択し、**すべて抽出**します。</span><span class="sxs-lookup"><span data-stu-id="2c089-137">In the **IdFix** window, choose **Extract**, and then **Extract all**.</span></span> <span data-ttu-id="2c089-138">既定では、IDFix は `C:\Users\<your user name>\Documents\IdFix` に抽出されます。</span><span class="sxs-lookup"><span data-stu-id="2c089-138">By default, IdFix is extracted to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
5. <span data-ttu-id="2c089-139">[**展開**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2c089-139">Choose **Extract**.</span></span>

<span data-ttu-id="2c089-140">手順は、使用している Windows のバージョンとインターネット ブラウザーによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2c089-140">Your steps might vary based on your version of Windows and your Internet browser.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="2c089-141">IDFix ツールの実行</span><span class="sxs-lookup"><span data-stu-id="2c089-141">Run the IdFix tool</span></span>

<span data-ttu-id="2c089-142">IDFix をダウンロードして抽出したら、それを実行して AD DS ドメインの問題を検索します。</span><span class="sxs-lookup"><span data-stu-id="2c089-142">After you download and extract IdFix, run it to search for problems in your AD DS domain.</span></span>
  
1. <span data-ttu-id="2c089-143">AD DS ドメインへの読み取り/書き込みアクセス権を持つアカウントを使用して、IDFix をダウンロードしたコンピューターにサインインします。</span><span class="sxs-lookup"><span data-stu-id="2c089-143">Using an account that has read/write access to your AD DS domain, sign in to the computer where you downloaded IdFix.</span></span>
    
2. <span data-ttu-id="2c089-144">ファイル エクスプローラーで、IDFix を抽出した場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="2c089-144">In File Explorer, go to the location where you extracted IdFix.</span></span> <span data-ttu-id="2c089-145">抽出中に既定のフォルダーを選択した場合は、`C:\Users\<your user name>\Documents\IdFix` に移動します。</span><span class="sxs-lookup"><span data-stu-id="2c089-145">If you chose the default folder during extraction, go to `C:\Users\<your user name>\Documents\IdFix`.</span></span> 
    
3. <span data-ttu-id="2c089-146">**IdFix.exe** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c089-146">Double-click **IdFix.exe**.</span></span> 
  
4. <span data-ttu-id="2c089-147">既定では、IDFix はマルチテナントのルール セットを使用して、ディレクトリ内の項目をテストします。</span><span class="sxs-lookup"><span data-stu-id="2c089-147">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory.</span></span> <span data-ttu-id="2c089-148">これは、ほとんどの Microsoft 365 のお客様にとって適正なルール セットです。</span><span class="sxs-lookup"><span data-stu-id="2c089-148">This is the right rule set for most Microsoft 365 customers.</span></span> <span data-ttu-id="2c089-149">ただし、Microsoft 365 Dedicated または ITAR (国際武器取引規約) のお客様は、代わりに Dedicated ルールを使用するように IDFix を構成できます。</span><span class="sxs-lookup"><span data-stu-id="2c089-149">However, if you are a Microsoft 365 Dedicated or International Traffic in Arms Regulations (ITAR)) customer, you can configure IdFix to use the Dedicated rule set instead.</span></span> <span data-ttu-id="2c089-150">お客様の種類が分からない場合には、この手順をスキップしても差し支えありません。</span><span class="sxs-lookup"><span data-stu-id="2c089-150">If you aren't sure what type of customer you are, you can safely skip this step.</span></span> <span data-ttu-id="2c089-151">Dedicated にルール セットを設定するには、メニュー バーで歯車のアイコンをクリックして **[Dedicated]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2c089-151">To set the rule set to Dedicated, click the gear icon in the menu bar, and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="2c089-152">[**クエリ**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="2c089-152">Choose **Query**.</span></span>
    
    ![IDFix でクエリを選択します。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="2c089-154">既定では、IDFix は、ディレクトリ全体のエラーを検索します。</span><span class="sxs-lookup"><span data-stu-id="2c089-154">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="2c089-155">ディレクトリのサイズによっては、照会の実行にしばらく時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="2c089-155">Depending on the size of your directory, running the query can take a while.</span></span> <span data-ttu-id="2c089-156">ツールのメイン ウィンドウの下部で進行状況を確認できます。</span><span class="sxs-lookup"><span data-stu-id="2c089-156">You can watch the progress at the bottom of the tool's main window.</span></span> <span data-ttu-id="2c089-157">**[キャンセル]** をクリックする場合、最初からやり直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c089-157">If you click **Cancel**, you'll need to restart from the beginning.</span></span>
  
7. <span data-ttu-id="2c089-158">IDFix による照会の完了後、ディレクトリにエラーがない場合には、続行してディレクトリを同期できます。</span><span class="sxs-lookup"><span data-stu-id="2c089-158">After IdFix completes the query, you can synchronize your directory if there are no errors.</span></span> <span data-ttu-id="2c089-159">ディレクトリ内にエラーがある場合は、同期する前にそれらを修正することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2c089-159">If there are errors in your directory, it is recommended that you fix them before you synchronize.</span></span> <span data-ttu-id="2c089-160">詳細については、[「IDFix ツールを使用して Microsoft 365 と同期するためにディレクトリ属性を準備する」](prepare-directory-attributes-for-synch-with-idfix.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c089-160">See [prepare directory attributes for synchronization with Microsoft 365](prepare-directory-attributes-for-synch-with-idfix.md) for more information.</span></span>
    
    <span data-ttu-id="2c089-161">同期の前にエラーを修正することは必須ではありませんが、IDFix によって戻されたエラーすべてを少なくても確認することを是非お勧めします。</span><span class="sxs-lookup"><span data-stu-id="2c089-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="2c089-162">各エラーは、ツールのメイン ウィンドウに別々の行で表示されます。</span><span class="sxs-lookup"><span data-stu-id="2c089-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="2c089-163">**[更新]** 列の提案されている変更に同意する場合、変更を実装するための IDFix による実行内容を **[アクション]** 列で選択し、**[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2c089-163">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**.</span></span> <span data-ttu-id="2c089-164">[**適用**] をクリックすると、ツールがディレクトリ内で変更を実行します。</span><span class="sxs-lookup"><span data-stu-id="2c089-164">When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="2c089-165">更新のたびに **[適用]** をクリックする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2c089-165">You don't have to click **Apply** after each update.</span></span> <span data-ttu-id="2c089-166">代わりに、**[適用]** をクリックする前に幾つかのエラーを修正すると、IDFix によって同時にすべてが変更されます。</span><span class="sxs-lookup"><span data-stu-id="2c089-166">Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time.</span></span> <span data-ttu-id="2c089-167">エラーの種類を示している列の上部にある [**エラー**] をクリックすると、エラーを種類ごとに並べることができます。</span><span class="sxs-lookup"><span data-stu-id="2c089-167">You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="2c089-168">1 つの方法として、同じ種類のエラーすべてを修正できます。たとえば、最初に、重複をすべて修正し、それらを適用します。</span><span class="sxs-lookup"><span data-stu-id="2c089-168">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them.</span></span> <span data-ttu-id="2c089-169">次に、文字形式のエラーを修正するなどします。</span><span class="sxs-lookup"><span data-stu-id="2c089-169">Next, fix the character format errors, and so on.</span></span> <span data-ttu-id="2c089-170">変更を適用するたびに、IDFix ツールによって別のログ ファイルが作成され、ミスが生じた場合にそうした変更を元に戻すために使用できます。</span><span class="sxs-lookup"><span data-stu-id="2c089-170">Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake.</span></span> <span data-ttu-id="2c089-171">[トランザクション ログ](idfix-transaction-log.md) は、IDFix を抽出したフォルダーに格納されます。これは、既定では _C:\Users\<your user name>\Documents\IdFix_ です。</span><span class="sxs-lookup"><span data-stu-id="2c089-171">The [transaction log](idfix-transaction-log.md) is stored in the folder where you extracted IdFix, which is _C:\Users\<your user name>\Documents\IdFix_ by default.</span></span> 
    
    ![IDFix でエラーを修復します。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="2c089-173">すべての変更をディレクトリに加えた後、IDFix をもう一度実行し、加えた修正により新しいエラーが生じていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2c089-173">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors.</span></span> <span data-ttu-id="2c089-174">これらの手順を必要なだけ繰り返すことができます。</span><span class="sxs-lookup"><span data-stu-id="2c089-174">You can repeat these steps as many times as you need to.</span></span> <span data-ttu-id="2c089-175">同期する前に、少々時間を取ってこの処理を行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2c089-175">It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="additional-resources-on-idfix"></a><span data-ttu-id="2c089-176">IDFix のその他のリソース</span><span class="sxs-lookup"><span data-stu-id="2c089-176">Additional resources on IdFix</span></span> 

- [<span data-ttu-id="2c089-177">IDFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性</span><span class="sxs-lookup"><span data-stu-id="2c089-177">IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="2c089-178">Microsoft 365 IDFix トランザクション ログ</span><span class="sxs-lookup"><span data-stu-id="2c089-178">Microsoft 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
