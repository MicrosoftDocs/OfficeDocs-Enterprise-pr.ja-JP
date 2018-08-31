---
title: Office 365 IdFix ツールをインストールして実行する
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: インストールし、Office 365 に同期する前に、active directory のクリーンアップのために Office 365 の IdFix ツールを実行する方法です。
ms.openlocfilehash: 642273c0171603d627a19273a78fe66662f4caaf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541533"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a><span data-ttu-id="cad56-103">Office 365 IdFix ツールをインストールして実行する</span><span class="sxs-lookup"><span data-stu-id="cad56-103">Install and run the Office 365 IdFix tool</span></span>

<span data-ttu-id="cad56-104">IdFix は、Office 365 に同期する前に複製し、ディレクトリ内の書式の問題のようなエラーを識別します。</span><span class="sxs-lookup"><span data-stu-id="cad56-104">IdFix identifies errors such as duplicates and formatting problems in your directory before you synchronize to Office 365.</span></span> 
  
<span data-ttu-id="cad56-105">このタスクを正常に完了するには、ユーザー、グループ、および Active Directory で連絡先オブジェクトで作業する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cad56-105">To finish this task successfully, you should be comfortable working with user, group, and contact objects in Active Directory.</span></span>
  
<span data-ttu-id="cad56-p101">このタスクを完了できない場合は、いくつかの他の操作を実行できます。これらのメソッドを簡単にする場合がありますが、可能性がありますも時間がかかる、またはその他の欠点があります。ものがあります。</span><span class="sxs-lookup"><span data-stu-id="cad56-p101">If you can't complete this task, there are a couple of other things you can do. These methods might be easier, but they might also take longer or have other drawbacks. They are:</span></span>
  
- <span data-ttu-id="cad56-p102">**IdFix を実行せずにディレクトリ同期を実行します**。IdFix ツールを実行しなくても、ディレクトリを同期するが、それはお勧めしません。同期する前に、エラーを修正する時間が少なくて済み、クラウドへのスムーズな移行は多くの場合、します。</span><span class="sxs-lookup"><span data-stu-id="cad56-p102">**Run directory synchronization without running IdFix.** You can synchronize your directory without running the IdFix tool, but we don't recommend it. Fixing errors before you synchronize takes less time and often provides a smoother transition to the cloud.</span></span> 
- <span data-ttu-id="cad56-p103">**コンサルタントを雇います。**  専門家に援助してもらうと、ユーザーは迅速に実務に使用でき、管理者はディレクトリ同期を完了させることができます。</span><span class="sxs-lookup"><span data-stu-id="cad56-p103">**Hire a consultant.** Getting expert help can get your users up and running quickly and your directory synchronized.</span></span> 
    
## <a name="what-you-need-to-run-idfix"></a><span data-ttu-id="cad56-114">IdFix を実行するために必要な事柄</span><span class="sxs-lookup"><span data-stu-id="cad56-114">What you need to run IdFix</span></span>

<span data-ttu-id="cad56-p104">IdFix を取得する方法の最も簡単な実行中、ドメインに参加しているコンピューターにインストールするには。、する場合は必要はありません、ドメイン コント ローラーでそれを実行できます。</span><span class="sxs-lookup"><span data-stu-id="cad56-p104">The easiest way to get IdFix up and running is to install it on a computer that is joined to your domain. You can run it on the domain controller if you want to, but it's not necessary.</span></span>
  
### <a name="idfix-hardware-requirements"></a><span data-ttu-id="cad56-117">IdFix のハードウェア要件</span><span class="sxs-lookup"><span data-stu-id="cad56-117">IdFix hardware requirements</span></span>

<span data-ttu-id="cad56-118">IdFix をインストールするコンピューターは、以下のハードウェア要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cad56-118">The computer where you install IdFix needs to meet these hardware requirements:</span></span>
  
- <span data-ttu-id="cad56-119">4 GB の RAM (最小)</span><span class="sxs-lookup"><span data-stu-id="cad56-119">4 GB RAM (minimum)</span></span>
- <span data-ttu-id="cad56-120">2 GB のハード ディスク容量 (最小)</span><span class="sxs-lookup"><span data-stu-id="cad56-120">2 GB of hard disk space (minimum)</span></span>
    
### <a name="idfix-software-requirements"></a><span data-ttu-id="cad56-121">IdFix のソフトウェア要件</span><span class="sxs-lookup"><span data-stu-id="cad56-121">IdFix software requirements</span></span>

<span data-ttu-id="cad56-p105">IdFix 必要がありますをインストールするコンピューターは、Office 365 にユーザーを同期する、同じ Active Directory ドメインに参加している必要があります。コンピューターでは、.NET Framework 4.0 がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cad56-p105">The computer where you install IdFix needs to needs to be joined to the same Active Directory domain from which you want to synchronize users to Office 365. The computer also needs to have .NET Framework 4.0 installed.</span></span> 
  
<span data-ttu-id="cad56-p106">Windows Server 2008 または Windows Server 2012 を実行している.NET Framework はインストールされて可能性があります。[ダウンロード センターから .NET 4.0 をダウンロード](https://go.microsoft.com/fwlink/p/?LinkId=400475)可能な場合、または Windows Update を使用しています。</span><span class="sxs-lookup"><span data-stu-id="cad56-p106">If you are running Windows Server 2008 or Windows Server 2012, then .NET Framework is probably already installed. If not, you can [download .NET 4.0 from the download center](https://go.microsoft.com/fwlink/p/?LinkId=400475) or by using Windows Update.</span></span> 
  
### <a name="idfix-permissions-requirements"></a><span data-ttu-id="cad56-126">IdFix アクセス許可の要件</span><span class="sxs-lookup"><span data-stu-id="cad56-126">IdFix permissions requirements</span></span>

<span data-ttu-id="cad56-127">IdFix を実行するためのユーザー アカウントには、ディレクトリへの読み取り/書き込みアクセス権が必要です。</span><span class="sxs-lookup"><span data-stu-id="cad56-127">The user account that you use to run IdFix needs to have read/write access to the directory.</span></span>
  
<span data-ttu-id="cad56-p107">わからない場合、ユーザー アカウントがこれらの要件を満たしているし、確認する方法がわからない場合、まだインストールし、IdFix を実行します。自分のユーザー アカウントには、適切なアクセス許可が割り当てられていない、IdFix だけでエラーが表示されますそれを実行しようとするとき。</span><span class="sxs-lookup"><span data-stu-id="cad56-p107">If you aren't sure if your user account meets these requirements, and you're not sure how to check, you can still install and run IdFix anyway. If your user account doesn't have the right permissions, IdFix will simply display an error when you try to run it.</span></span>
  
## <a name="install-idfix"></a><span data-ttu-id="cad56-130">IdFix のインストール</span><span class="sxs-lookup"><span data-stu-id="cad56-130">Install IdFix</span></span>

<span data-ttu-id="cad56-131">IdFix をインストールするには、以下の手順に従って **IdFix.exe** をダウンロードし、解凍します。</span><span class="sxs-lookup"><span data-stu-id="cad56-131">To install IdFix, you download and unzip **IdFix.exe** as described in these steps:</span></span> 
  
1. <span data-ttu-id="cad56-132">IdFix ツールをインストールするコンピューターにログオンします。</span><span class="sxs-lookup"><span data-stu-id="cad56-132">Log on to the computer where you want to install the IdFix tool.</span></span>
    
2. <span data-ttu-id="cad56-133">[IdFix ディレクトリ同期エラーの修復ツール](https://go.microsoft.com/fwlink/?linkid=867219)は、マイクロソフトのダウンロード サイトに移動します。</span><span class="sxs-lookup"><span data-stu-id="cad56-133">Go to the Microsoft download site for the [IdFix DirSync Error Remediation Tool](https://go.microsoft.com/fwlink/?linkid=867219).</span></span>
    
3. <span data-ttu-id="cad56-134">[**Download**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cad56-134">Choose **Download**.</span></span>
    
4. <span data-ttu-id="cad56-135">ダイアログ ボックスが表示されたら、**実行**を選択します。</span><span class="sxs-lookup"><span data-stu-id="cad56-135">When prompted, choose **Run**.</span></span>
    
5. <span data-ttu-id="cad56-p108">[ **WinZip Self-extractor** ] ダイアログ ボックスの**フォルダーに解凍**] テキスト ボックスに入力するか、IdFix ツールをインストールする場所を参照します。C:\Deployment ツールに既定では、IdFix がインストールされています。\.</span><span class="sxs-lookup"><span data-stu-id="cad56-p108">On the **WinZip Self-Extractor** dialog box, in the **Unzip to folder** text box, type or browse to the location where you want to install the IdFix tool. By default, IdFix is installed into C:\Deployment Tools\.</span></span> 
    
6. <span data-ttu-id="cad56-138">**解凍**」を選択します。</span><span class="sxs-lookup"><span data-stu-id="cad56-138">Choose **Unzip**.</span></span>
    
## <a name="run-the-idfix-tool"></a><span data-ttu-id="cad56-139">IdFix ツールの実行</span><span class="sxs-lookup"><span data-stu-id="cad56-139">Run the IdFix tool</span></span>

<span data-ttu-id="cad56-140">IdFix をインストールした後、次のようにツールを実行してディレクトリでの問題を検索します。</span><span class="sxs-lookup"><span data-stu-id="cad56-140">After you install IdFix, run the tool to search for problems in your directory:</span></span>
  
1. <span data-ttu-id="cad56-141">ディレクトリへの読み取り/書き込みアクセス権を持つアカウントを使用して、IdFix をインストールしたコンピューターにログオンします。</span><span class="sxs-lookup"><span data-stu-id="cad56-141">Using an account that has read/write access to the directory, log on to the computer where you installed IdFix.</span></span>
    
2. <span data-ttu-id="cad56-p109">エクスプローラーで、IdFix をインストールした場所に移動します。インストール時に既定のフォルダーを選択した場合は、C:\Deployment Tools\IdFix に移動します。</span><span class="sxs-lookup"><span data-stu-id="cad56-p109">In File Explorer, go to the location where you installed IdFix. If you chose the default folder during installation, go to C:\Deployment Tools\IdFix.</span></span>
    
3. <span data-ttu-id="cad56-144">**IdFix.exe** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="cad56-144">Double-click **IdFix.exe**.</span></span> 
    
    ![IdFix.exe ファイルを選択します。](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. <span data-ttu-id="cad56-p110">既定では、IdFix は、設定、ディレクトリ内のエントリをテストするのにはマルチ テナント型のルールを使用します。これは、右の規則が、ほとんどの Office 365 ユーザー セットです。ただし、専用の Office 365 または顧客の ITAR (武器規制の国際トラフィック) 場合は、設定の代わりに専用の規則を使用して IdFix を設定できます。顧客の種類がわからない場合、安全にこの手順を省略できます。専用] に設定するルールを設定するのにはメニュー バーの歯車アイコンをクリックして、**専用**です。</span><span class="sxs-lookup"><span data-stu-id="cad56-p110">By default, IdFix uses the Multi-Tenant rule set to test the entries in your directory. This is the right rule set for most Office 365 customers. However, if you are an Office 365 Dedicated or ITAR (International Traffic in Arms Regulations) customer, you can configure IdFix to use the Dedicated rule set instead. If you aren't sure what type of customer you are, you can safely skip this step. To set the rule set to Dedicated, click the gear icon in the menu bar and then choose **Dedicated**.</span></span>
    
5. <span data-ttu-id="cad56-151">**クエリ**を選択します。</span><span class="sxs-lookup"><span data-stu-id="cad56-151">Choose **Query**.</span></span>
    
    ![IdFix では、クエリを選択します。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. <span data-ttu-id="cad56-153">既定では、IdFix は、ディレクトリ全体のエラーを検索します。</span><span class="sxs-lookup"><span data-stu-id="cad56-153">By default, IdFix searches the entire directory for errors.</span></span>
    
    <span data-ttu-id="cad56-p111">サイズによっては、ディレクトリのクエリを実行することができます時間がかかります。ツールのメイン ウィンドウの下部にある進行状況を監視できます。**[キャンセル**] をクリックする場合は、先頭から再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cad56-p111">Depending on the size of your directory, running the query can take a while. You can watch the progress at the bottom of the tool's main window. If you click **Cancel**, you'll need to restart from the beginning.</span></span>
    
    ![IdFix クエリし、エラーの数です。](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. <span data-ttu-id="cad56-p112">IdFix による照会の完了後、ディレクトリにエラーがない場合には、続行してディレクトリを同期できます。ディレクトリ内にエラーがある場合は、同期する前にそれらを修正することをお勧めします。エラーの種類に関するより詳細な情報やそれぞれを修正する最善の方法についての推奨を確認するには、このトピックの末尾にあるリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cad56-p112">After IdFix completes the query, and if there are no errors in your directory, you can go ahead and synchronize your directory. If there are errors in your directory, it is recommended that you fix them before you synchronize. If you want more specific information about types of errors and recommendations about the best way to fix each of them, see the links at the end of this topic.</span></span> 
    
    <span data-ttu-id="cad56-161">同期の前にエラーを修正することは必須ではありませんが、IdFix によって戻されたエラーすべてを少なくても確認することを是非お勧めします。</span><span class="sxs-lookup"><span data-stu-id="cad56-161">While it is not mandatory to fix the errors before you synchronize, we strongly recommend that you at least review all the errors returned by IdFix.</span></span>
    
    <span data-ttu-id="cad56-162">各エラーは、ツールのメイン ウィンドウで別々 の行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cad56-162">Each error is displayed in a separate row in the tool's main window .</span></span> 
    
8. <span data-ttu-id="cad56-p113">**[UPDATE]** 列の提案されている変更に同意する場合、変更を実装するための IdFix による実行内容を **[ACTION]** 列で選択し、**[Apply]** をクリックします。**[Apply]** をクリックすると、ツールによってディレクトリに変更が加えられます。</span><span class="sxs-lookup"><span data-stu-id="cad56-p113">If you agree with the suggested change in the **UPDATE** column, in the **ACTION** column select what you want IdFix to do to implement the change and then click **Apply**. When you click **Apply**, the tool makes the changes in the directory.</span></span>
    
    <span data-ttu-id="cad56-p114">各更新後の [**適用**] をクリックする必要はありません。代わりに、 **[適用**] をクリックして、IdFix はすべてを同時にそれらを変更する前に、いくつかのエラーを修正できます。エラーの種類を一覧表示する列の上部にある**エラー**をクリックすると、エラーの種類ごとのエラーを並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="cad56-p114">You don't have to click **Apply** after each update. Instead, you can fix several errors before you click **Apply** and IdFix will change them all at the same time. You can sort the errors by error type by clicking **ERROR** at the top of the column that lists the error types.</span></span> 
    
    <span data-ttu-id="cad56-p115">1 つの戦略は、同じ型のすべてのエラーを修正するにはたとえば、最初に、すべての重複を修正し、それらを適用します。次に、文字の書式設定エラーを修正したりします。変更を適用するたびに、IdFix ツールは、誤りがあった場合に、変更内容を元に戻すに使用できる別のログ ファイルを作成します。[トランザクション ・ ログ](idfix-transaction-log.md)は、の IdFix をインストールしたフォルダーに格納されます。 デフォルトで_C:\Deployment の Tools\IdFix_にします。</span><span class="sxs-lookup"><span data-stu-id="cad56-p115">One strategy is to fix all the errors of the same type; for example, fix all the duplicates first, and apply them. Next, fix the character format errors, and so on. Each time you apply the changes, the IdFix tool creates a separate log file that you can use to undo your changes in case you make a mistake. The [transaction log](idfix-transaction-log.md) is stored in the folder that you installed IdFix in.  _C:\Deployment Tools\IdFix_ by default.</span></span> 
    
    ![IdFix でエラーを修復します。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. <span data-ttu-id="cad56-p116">すべての変更が行われますディレクトリに加えた修正していない新しいエラーが発生することを確認するには、再度 IdFix を実行します。手順を実行する必要がある回数だけを繰り返すことができます。同期する前に、何度かを処理を完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cad56-p116">After all of your changes are made to the directory, run IdFix again to ensure that the fixes you made didn't introduce new errors. You can repeat these steps as many times as you need to. It's a good idea to go through the process a few times before you synchronize.</span></span>
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a><span data-ttu-id="cad56-177">検索を絞り込むか、エラーをさらに掘り下げるには、IdFix でさらに何を行えますか?</span><span class="sxs-lookup"><span data-stu-id="cad56-177">I want to refine my search or dig deeper into the errors, what else can I do with IdFix?</span></span>

<span data-ttu-id="cad56-178">詳細な情報は以下のトピックに記載されています。</span><span class="sxs-lookup"><span data-stu-id="cad56-178">More in-depth information is available from these topics:</span></span>
  
- <span data-ttu-id="cad56-p117">[IdFix ツールを使用して Office 365 との同期のディレクトリ属性を準備](prepare-directory-attributes-for-synch-with-idfix.md)します。ツール、ツールの実行に関する詳細な手順については、このトピックへのジャンプをインストールした後、一般的なエラーが発生するは、修正、例、および多数のエラーがある場合の対処方法に関するベスト プラクティスを推奨します。</span><span class="sxs-lookup"><span data-stu-id="cad56-p117">[Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md) . After you have installed the tool, jump to this topic for more detailed instructions about running the tool, common errors you will encounter, suggested fixes, examples, and best practices for what to do when you have a large number of errors.</span></span> 
- [<span data-ttu-id="cad56-181">リファレンス: IdFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性</span><span class="sxs-lookup"><span data-stu-id="cad56-181">Reference: IdFix excluded and supported objects and attributes</span></span>](idfix-excluded-and-supported-objects-and-attributes.md)  
- [<span data-ttu-id="cad56-182">リファレンス: Office 365 IdFix トランザクション ログ</span><span class="sxs-lookup"><span data-stu-id="cad56-182">Reference: Office 365 IdFix transaction log</span></span>](idfix-transaction-log.md)
    
## <a name="video-training"></a><span data-ttu-id="cad56-183">ビデオ ・ トレーニング</span><span class="sxs-lookup"><span data-stu-id="cad56-183">Video training</span></span>

<span data-ttu-id="cad56-184">詳細については、LinkedIn の学習でレッスン[をインストールして IDFix ツールを使用して](https://support.office.com/article/4d81d73c-f172-4fd5-8542-f601c0c96aa9.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cad56-184">For more information, see the lesson [Install and use the IDFix tool](https://support.office.com/article/4d81d73c-f172-4fd5-8542-f601c0c96aa9.aspx), brought to you by LinkedIn Learning.</span></span>
  

