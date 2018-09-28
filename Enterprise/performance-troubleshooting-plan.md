---
title: Office 365 のパフォーマンスに関するトラブルシューティングの計画
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 4/26/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c
description: 特定し、遅れて、ハング、および SharePoint のオンラインのビジネス、Exchange Online では、Skype のビジネス オンラインでは、OneDrive、クライアント コンピューターの間でパフォーマンスの低下を解決するための手順を理解する必要がありますか。サポートに連絡する前に、Office 365 のパフォーマンスに関する問題のトラブルシューティングを行うし、もいくつかの最も一般的な問題を解決するをこの資料に役立ちます。
ms.openlocfilehash: 0e588d35ff6caaa0796092bb2f964bced15f4e47
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975185"
---
# <a name="performance-troubleshooting-plan-for-office-365"></a><span data-ttu-id="491da-104">Office 365 のパフォーマンスに関するトラブルシューティングの計画</span><span class="sxs-lookup"><span data-stu-id="491da-104">Performance troubleshooting plan for Office 365</span></span>

<span data-ttu-id="491da-p102">特定し、遅れて、ハング、および SharePoint のオンラインのビジネス、Exchange Online では、Skype のビジネス オンラインでは、OneDrive、クライアント コンピューターの間でパフォーマンスの低下を解決するための手順を理解する必要がありますか。サポートに連絡する前に、Office 365 のパフォーマンスに関する問題のトラブルシューティングを行うし、もいくつかの最も一般的な問題を解決するをこの資料に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="491da-p102">Do you need to know the steps to take to identify and fix lags, hangs, and slow performance between SharePoint Online, OneDrive for Business, Exchange Online, or Skype for Business Online, and your client computer? Before you call support, this article can help you troubleshoot Office 365 performance issues and even fix some of the most common issues.</span></span>
  
<span data-ttu-id="491da-p103">この資料では、実際にアクション計画の例ですので、パフォーマンスの問題に関する貴重なデータをキャプチャする使用することができますが発生します。いくつか上の問題は、この資料にも含まれます。</span><span class="sxs-lookup"><span data-stu-id="491da-p103">This article is actually a sample action plan that you can use to capture valuable data about your performance issue as it's happening. Some top issues are also included in this article.</span></span>
    
<span data-ttu-id="491da-109">経験がない場合、ネットワーク パフォーマンスや、クライアント マシンと Office 365 の間のパフォーマンスを監視するための長期的な計画を作成するのに、 [Office 365 のパフォーマンスのチューニングとトラブルシューティングに管理者、IT プロフェッショナル](performance-tuning-using-baselines-and-history.md)を見てください。</span><span class="sxs-lookup"><span data-stu-id="491da-109">If you're new to network performance and want to make a long term plan to monitor performance between your client machines and Office 365, take a look at [Office 365 performance tuning and troubleshooting - Admin and IT Pro](performance-tuning-using-baselines-and-history.md).</span></span>
  
## <a name="sample-performance-troubleshooting-action-plan"></a><span data-ttu-id="491da-110">サンプル パフォーマンス トラブルシューティング ・ アクション ・ プラン</span><span class="sxs-lookup"><span data-stu-id="491da-110">Sample performance troubleshooting action plan</span></span>

<span data-ttu-id="491da-p104">このアクション ・ プランには、ふたつの部分が含まれています。準備フェーズでは、およびログのフェーズです。今、パフォーマンスに問題があるデータのコレクションを実行する必要がある場合は、この計画をすぐに使用を開始できます。</span><span class="sxs-lookup"><span data-stu-id="491da-p104">This action plan contains two parts; a preparation phase, and a logging phase. If you have a performance problem right now, and you need to do data collection, you can start using this plan right away.</span></span>
  
 <span data-ttu-id="491da-113">**クライアント コンピューターを準備します。**</span><span class="sxs-lookup"><span data-stu-id="491da-113">**Prepare the client computer**</span></span>
  
- <span data-ttu-id="491da-p105">パフォーマンス上の問題を再現できるクライアント コンピューターを検索します。このコンピューターは、トラブルシューティングの過程で使用されます。</span><span class="sxs-lookup"><span data-stu-id="491da-p105">Find a client computer that can reproduce the performance problem. This computer will be used during the course of troubleshooting.</span></span>
    
- <span data-ttu-id="491da-116">テストするときに準備することで発生するパフォーマンスの問題を発生させる手順をメモします。</span><span class="sxs-lookup"><span data-stu-id="491da-116">Write down the steps that cause the performance problem to happen so you're ready when it comes time to test.</span></span>
    
- <span data-ttu-id="491da-117">収集と情報を記録するためのツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="491da-117">Install tools for gathering and recording information:</span></span>
    
  - <span data-ttu-id="491da-118">[ネットワーク モニターの 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865)をインストール (または同等のネットワーク トレース ツールを使用)。</span><span class="sxs-lookup"><span data-stu-id="491da-118">Install [Netmon 3.4](https://www.microsoft.com/en-us/download/details.aspx?id=4865) (or use an equivalent network tracing tool).</span></span> 
    
  - <span data-ttu-id="491da-119">[HTTPWatch](https://www.httpwatch.com/download/)の無料の基本的なエディションをインストール (または同等のネットワーク トレース ツールを使用)。</span><span class="sxs-lookup"><span data-stu-id="491da-119">Install the free Basic Edition of [HTTPWatch](https://www.httpwatch.com/download/) (or use an equivalent network Tracing tool).</span></span> 
    
  - <span data-ttu-id="491da-120">画面レコーダーを使用するかには、Windows vista 以降では、テスト中に実行する手順の記録を保持するためにステップ記録ツール (PSR.exe) を実行します。</span><span class="sxs-lookup"><span data-stu-id="491da-120">Use a screen recorder or run the Steps Recorder (PSR.exe) that comes with Windows Vista and later, in order to keep a record of the steps you take during testing.</span></span>
    
 <span data-ttu-id="491da-121">**ログ、パフォーマンスの問題**</span><span class="sxs-lookup"><span data-stu-id="491da-121">**Log the performance issue**</span></span>
  
- <span data-ttu-id="491da-122">すべての不要なインターネット ブラウザーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="491da-122">Close all extraneous Internet browsers.</span></span>
    
- <span data-ttu-id="491da-123">ステップ記録ツールで、または別の画面レコーダーを起動します。</span><span class="sxs-lookup"><span data-stu-id="491da-123">Start the Steps Recorder, or another screen recorder.</span></span>
    
- <span data-ttu-id="491da-124">ネットワーク モニターのキャプチャ (またはネットワーク トレース ツール) を起動します。</span><span class="sxs-lookup"><span data-stu-id="491da-124">Start your Netmon capture (or network tracing tool).</span></span>
    
- <span data-ttu-id="491da-125">Ipconfig/flushdns を入力してコマンド ・ ラインからクライアント コンピューターの DNS キャッシュをクリアします。</span><span class="sxs-lookup"><span data-stu-id="491da-125">Clear your DNS cache on the client computer from the command line by typing ipconfig /flushdns.</span></span>
    
- <span data-ttu-id="491da-126">新しいブラウザー セッションを開始し、HTTPWatch をオンにします。</span><span class="sxs-lookup"><span data-stu-id="491da-126">Start a new browser session and turn on HTTPWatch.</span></span>
    
- <span data-ttu-id="491da-127">オプション: Exchange Online をテストするが場合、は、Office 365 の管理コンソールから Exchange クライアント パフォーマンス ・ アナライザー ツールを実行します。</span><span class="sxs-lookup"><span data-stu-id="491da-127">Optional: If you are testing Exchange Online, run the Exchange Client Performance Analyzer tool from the Office 365 admin console.</span></span>
    
- <span data-ttu-id="491da-128">パフォーマンス問題が発生する正確な手順を再現します。</span><span class="sxs-lookup"><span data-stu-id="491da-128">Reproduce the exact steps that cause the performance issue.</span></span>
    
- <span data-ttu-id="491da-129">ネットワーク モニター、またはその他のツールのトレースを停止します。</span><span class="sxs-lookup"><span data-stu-id="491da-129">Stop your Netmon or other tool's trace.</span></span>
    
- <span data-ttu-id="491da-130">コマンド ・ ラインで次のコマンドを入力し、し、ENTER キーを押して、Office 365 サブスクリプションの経路を追跡を実行します。</span><span class="sxs-lookup"><span data-stu-id="491da-130">At the command line, run a trace route to your Office 365 subscription by typing the following command and then pressing ENTER:</span></span>
    
    `tracert \< *subscriptionname*  \>.onmicrosoft.com` 
    
- <span data-ttu-id="491da-p106">ステップ記録ツールを停止し、ビデオを保存します。キャプチャし、良くも悪くもパフォーマンスを説明するかどうかの日時を含めることを確認します。</span><span class="sxs-lookup"><span data-stu-id="491da-p106">Stop the Steps Recorder and save the video. Be sure to include the date and time of the capture and whether it demonstrates good or bad performance.</span></span>
    
- <span data-ttu-id="491da-p107">トレース ファイルを保存します。もう一度、必ず日付と時刻のキャプチャとするかどうか良くも悪くもパフォーマンスを示します。</span><span class="sxs-lookup"><span data-stu-id="491da-p107">Save the trace files. Again, be sure to include the date and time of the capture and whether it demonstrates good or bad performance.</span></span>
    
<span data-ttu-id="491da-p108">この資料に記載されているツールを実行するに慣れていない場合は、心配するこれらの手順を次に提供されています。この種のネットワーク キャプチャを実行することに慣れて場合は、[ベースラインを収集する方法](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines)、フィルタ リングとログの参照方法について説明を省略できます。</span><span class="sxs-lookup"><span data-stu-id="491da-p108">If you're not familiar with running the tools mentioned in this article, don't worry because we provide those steps next. If you're accustomed to doing this kind of network capturing, you can skip to [How to collect baselines](performance-tuning-using-baselines-and-history.md#how-to-collect-baselines), which describes filtering and reading the logs.</span></span> 
  
## <a name="flush-the-dns-cache-first"></a><span data-ttu-id="491da-137">最初に DNS キャッシュをフラッシュします。</span><span class="sxs-lookup"><span data-stu-id="491da-137">Flush the DNS Cache first</span></span>

<span data-ttu-id="491da-p109">なぜでしょうか。DNS キャッシュをフラッシュしてから、テストを開始しています。キャッシュをオフにしている、最新のエントリを DNS のリゾルバーの内容をリセットします。フラッシュにホスト ファイルのエントリが削除されないことに注意してください。ホスト ファイルのエントリを頻繁に使用する場合別のディレクトリ内のファイルにこれらのエントリをコピーし、ホスト ・ ファイルを空にしてください。</span><span class="sxs-lookup"><span data-stu-id="491da-p109">Why? By flushing out the DNS cache you're starting your tests with a clean slate. By clearing the cache, you're resetting the DNS resolver contents to the most up-to-date entries. Remember that a flush does not remove HOSTs file entries. If you use HOST file entries extensively, you should copy those entries out to a file in another directory and then empty the HOST file.</span></span>
  
 <span data-ttu-id="491da-143">**DNS リゾルバー キャッシュをフラッシュします。**</span><span class="sxs-lookup"><span data-stu-id="491da-143">**Flush your DNS resolver cache**</span></span>
  
1. <span data-ttu-id="491da-144">コマンド プロンプトを開きます (**スタート**か、 \> **を実行** \> **cmd**または**Windows キー** \> **cmd**)。</span><span class="sxs-lookup"><span data-stu-id="491da-144">Open the command prompt, (either **Start** \> **Run** \> **cmd** or **Windows key** \> **cmd**).</span></span>
    
2. <span data-ttu-id="491da-145">次のコマンドを入力し、ENTER キーを押します。`ipconfig /flushdns`</span><span class="sxs-lookup"><span data-stu-id="491da-145">Type the following command and press ENTER: `ipconfig /flushdns`</span></span>
    
## <a name="netmon"></a><span data-ttu-id="491da-146">ネットワーク モニター</span><span class="sxs-lookup"><span data-stu-id="491da-146">Netmon</span></span>

<span data-ttu-id="491da-p110">マイクロソフトのネットワーク監視ツール ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)) は、パケットは、ネットワーク上のコンピューター間を通過するトラフィックを分析します。Office 365 をキャプチャすることができます表示、トラフィックのトレースしパケットのヘッダーを読み取り、間にあるデバイスを識別する、ネットワークのハードウェア上で重要な設定を確認するには、ネットワーク モニターを使用して、ドロップされたパケットは、検索し、企業内のコンピューター間のトラフィック フローに従い、ネットワークと Office 365。トラフィックの実際の本文が暗号化されているので、つまり、(SSL や TLS を使用してポート 443 での旅を読むことができません、ファイルが送信されます。代わりに、パスに問題の現象を追跡することができますパケットがフィルター処理されていないトレースを取得します。</span><span class="sxs-lookup"><span data-stu-id="491da-p110">Microsoft's Network Monitoring tool ([Netmon](https://www.microsoft.com/download/details.aspx?id=4865)) analyzes packets, that is traffic, that passes between computers on networks. By using Netmon to trace traffic with Office 365 you can capture, view, and read packet headers, identify intervening devices, check important settings on network hardware, look for dropped packets, and follow the flow of traffic between computers on your corporate network and Office 365. Because the actual body of the traffic is encrypted, that is, it(travels on port 443 via SSL/TLS, you can't read the files being sent. Instead, you get an unfiltered trace of the path that the packet takes which can help you track down the problem behavior.</span></span>
  
<span data-ttu-id="491da-p111">この時点でフィルターを適用しないことを確認します。代わりに、手順を実行し、トレースを停止して、保存する前に問題を再現します。</span><span class="sxs-lookup"><span data-stu-id="491da-p111">Be sure you don't apply a filter at this time. Instead, run through the steps and demonstrate the problem before stopping the trace and saving.</span></span>
  
<span data-ttu-id="491da-153">Netmon 3.4 をインストールすると、ツールを起動し、これらの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="491da-153">After you install Netmon 3.4, open the tool and take these steps:</span></span>
  
 <span data-ttu-id="491da-154">**Netmon トレースを実行し、問題を再現**</span><span class="sxs-lookup"><span data-stu-id="491da-154">**Take a Netmon trace and reproduce the issue**</span></span>
  
1. <span data-ttu-id="491da-155">3.4 のネットワーク モニターを起動します。</span><span class="sxs-lookup"><span data-stu-id="491da-155">Launch Netmon 3.4.</span></span>
    
    <span data-ttu-id="491da-p112">**スタート**ページには 3 つのペインがあります:**最新のキャプチャ**、**ネットワークの選択]**、および Microsoft ネットワーク モニターの 3.4 の概要の**です。注意**。ネットワークの選択] パネルも提供されます一連の既定のネットワークをキャプチャすることができます。ネットワーク カードがここで選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="491da-p112">There are three panes on the **Start** page: **Recent Captures**, **Select Networks**, and the **Getting Started with Microsoft Network Monitor 3.4. Notice**. The Select Networks panel will also give you a list of the default networks from which you can capture. Be sure that network cards are selected here.</span></span>
    
2. <span data-ttu-id="491da-p113">**新しいキャプチャ**を**開始**] ページの上部にあるをクリックします。**1 のキャプチャ**と呼ばれる、**スタート**ページ タブの横に新しいタブが追加されます。</span><span class="sxs-lookup"><span data-stu-id="491da-p113">Click **New Capture** at the top of the **Start** page. This adds a new tab beside the **Start** page tab called **Capture 1**.</span></span>
    
    ![Nemon のユーザーは、インターフェイスを使用して、新しいキャプチャを開始、および停止ボタンが強調表示されます。](media/d4527d84-62ec-4301-82d5-e0166ff71f20.PNG)
  
3. <span data-ttu-id="491da-162">単純なキャプチャを実行するには、ツールバーの [**開始**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="491da-162">To take a simple capture, click **Start** on the toolbar.</span></span> 
    
4. <span data-ttu-id="491da-163">パフォーマンス上の問題を表示する手順を再現します。</span><span class="sxs-lookup"><span data-stu-id="491da-163">Reproduce the steps that present a performance issue.</span></span>
    
5. <span data-ttu-id="491da-p114">[**停止**] をクリックして\>**ファイル** \> **として保存**します。日付とタイム ゾーンの時刻を指定して、不良であるか、または適切なパフォーマンスを示すかどうかは言うまでも注意してください。</span><span class="sxs-lookup"><span data-stu-id="491da-p114">Click **Stop** \> **File** \> **Save As**. Remember to give the date and time with the time zone and to mention if it demonstrates bad or good performance.</span></span>
    
## <a name="httpwatch"></a><span data-ttu-id="491da-166">HTTPWatch</span><span class="sxs-lookup"><span data-stu-id="491da-166">HTTPWatch</span></span>

<span data-ttu-id="491da-p115">[HTTPWatch](https://www.httpwatch.com/download/)には、充電と無料版です。無料の基本的なエディションでは、このテストに必要なものすべてについて説明します。HTTPWatch モニターは、ブラウザー ウィンドウから直接トラフィックとページの読み込み時間をネットワークします。HTTPWatch は Internet Explorer のパフォーマンスを視覚的に説明するプラグインです。解析を保存して、HTTPWatch Studio で表示します。</span><span class="sxs-lookup"><span data-stu-id="491da-p115">[HTTPWatch](https://www.httpwatch.com/download/) comes in charged, and a free edition. The free Basic Edition covers everything you need for this test. HTTPWatch monitors network traffic and page load time right from your browser window. HTTPWatch is a plug-in to Internet Explorer that graphically describes performance. The analysis can be saved and viewed in HTTPWatch Studio.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="491da-p116">Google のクロム、Firefox などの別のブラウザーを使用する場合、または HTTPWatch を Internet Explorer にインストールできない場合は、新しいブラウザー ウィンドウを開くし、キーボードの f12 キーを押します。お使いのブラウザーの下部にあるポップアップの開発者ツールを参照してくださいする必要があります。Opera を使用する場合 Web インスペクターの CTRL + SHIFT + I を押して、 **[ネットワーク**] タブをクリックし、以下のテストが完了します。情報はわずかに異なるになりますが、読み込み時間をミリ秒単位で表示されます。> HTTPWatch は、SharePoint Online のページの読み込み時間の問題を非常に有用なもあります。</span><span class="sxs-lookup"><span data-stu-id="491da-p116">If you use another browser, such as Firefox, Google Chrome, or if you can't install HTTPWatch in Internet Explorer, open a new browser window and press F12 on your keyboard. You should see the Developer Tool pop-up at the bottom of your browser. If you use Opera, press CTRL+SHIFT+I for Web Inspector, then click the **Network** tab and complete the testing outlined below. The information will be slightly different, but load times will still be displayed in milliseconds. > HTTPWatch is also very useful for issues with SharePoint Online page load times.</span></span> 
  
 <span data-ttu-id="491da-177">**HTTPWatch を実行し、問題を再現**</span><span class="sxs-lookup"><span data-stu-id="491da-177">**Run HTTPWatch and reproduce the issue**</span></span>
  
1. <span data-ttu-id="491da-p117">HTTPWatch はブラウザーのプラグイン、ブラウザーのツールを公開することは、Internet Explorer のバージョンごとに若干異なります。通常、Internet Explorer ブラウザーのコマンド バーの下、HTTPWatch を検索できます。</span><span class="sxs-lookup"><span data-stu-id="491da-p117">HTTPWatch is a browser plug-in, so exposing the tool in the browser is slightly different for each version of Internet Explorer. Typically, you can find HTTPWatch under the Commands bar in the Internet Explorer browser. </span></span><br/><span data-ttu-id="491da-p118">チェック、ブラウザーのバージョンでヘルプをクリックして、ブラウザー ウィンドウで、HTTPWatch プラグインが表示されない場合、\>歯車記号および Internet Explorer に関する、または、新しいバージョンの Internet Explorer で、] をクリックします。**コマンド**バーを起動するに Internet Explorer のメニュー バーを右クリックし、**コマンド バー**] をクリックします。以前は、HTTPWatch が関連付けられているコマンドと、エクスプ ローラー バーの両方で、1 回インストールすると、**ツール**、およびツールバー アイコンの確認 (コンピューターを再起動後もアイコンがすぐに表示されない場合。ツールバーをカスタマイズすることができます、オプションを追加できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="491da-p118">If you don't see the HTTPWatch plug-in in your browser window, check the version of your browser by click Help \> About, or, in later versions of Internet Explorer, click the gear symbol and About Internet Explorer. To launch the **Commands** bar, right-click the menu bar in Internet Explorer and click **Commands bar**. In the past, HTTPWatch has been associated with both the Commands and the Explorer bars, so once you install, if you don't immediately see the icon (even after reboot) check **Tools**, and your toolbars for the icon. Remember that toolbars can be customized and options can be added to them.</span></span><br/>
    <span data-ttu-id="491da-184">![コマンド ツールバーを Internet Explorer の HTTPWatch] アイコンを表示します。](media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)</span><span class="sxs-lookup"><span data-stu-id="491da-184">![Internet Explorer's Command toolbar with the HTTPWatch icon displayed.](media/198590b0-d7b1-4bff-a6ad-e4ec3a1e83df.png)</span></span>
  
2. <span data-ttu-id="491da-p119">HTTPWatch に Internet Explorer のブラウザー ウィンドウを起動します。ブラウザー ウィンドウの下部にドッキングされて表示されます。[**レコード**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="491da-p119">Launch HTTPWatch in an Internet Explorer browser window. It will appear docked to the browser at the bottom of that window. Click **Record**.</span></span>
    
3. <span data-ttu-id="491da-p120">パフォーマンスの問題に関連する正確な手順を再現します。HTTPWatch に [**停止**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="491da-p120">Reproduce the exact steps involved in the performance issue. Click the **Stop** button in HTTPWatch.</span></span> 
    
4. <span data-ttu-id="491da-p121">HTTPWatch または**電子メールで送信**、**保存**します。日付と時刻の情報と、ウォッチに良くも悪くもパフォーマンスのデモが含まれているかどうかを示す値を含むファイルの名前を覚えておいてください。</span><span class="sxs-lookup"><span data-stu-id="491da-p121">**Save** the HTTPWatch or **Send by Email**. Remember to name the file so that it includes date and time information and an indication of whether your Watch contains a demonstration of good or bad performance.</span></span><br/><span data-ttu-id="491da-192">![Office 365 ホームページのページ読み込み用の [ネットワーク] タブを示す HTTPWatch。](media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)</span><span class="sxs-lookup"><span data-stu-id="491da-192">![HTTPWatch showing the Network tab for a page load of the Office 365 homepage.](media/021a2c64-d581-49fd-adf4-4c364f589d75.PNG)</span></span><br/>
    <span data-ttu-id="491da-p122">HTTPWatch のプロフェッショナル ・ バージョンは、このスクリーン ショットです。プロフェッショナル ・ バージョンと、コンピューターの基本的なバージョンからのトレースを表示でき、読み取ることがあります。余分な情報は、そのメソッドによって、トレースから使用可能な可能性があります。</span><span class="sxs-lookup"><span data-stu-id="491da-p122">This screen shot is from the Professional version of HTTPWatch. You can open traces taken in the Basic Version on a computer with a Professional version and read it there. Extra information may be available from the trace through that method.</span></span>
    
## <a name="problem-steps-recorder"></a><span data-ttu-id="491da-196">問題ステップ記録ツール</span><span class="sxs-lookup"><span data-stu-id="491da-196">Problem Steps Recorder</span></span>

<span data-ttu-id="491da-p123">ステップ記録ツール、または PSR.exe、発生時に問題を記録できます。非常に便利なツールは、実行するのには非常にシンプルです。</span><span class="sxs-lookup"><span data-stu-id="491da-p123">Steps Recorder, or PSR.exe, allows you to record issues as they are occurring. It's a very useful tool and very simple to run.</span></span>
  
 <span data-ttu-id="491da-199">**問題ステップ記録ツールの作業を記録する (PSR.exe) を実行します。**</span><span class="sxs-lookup"><span data-stu-id="491da-199">**Run Problem Steps Recorder (PSR.exe) to record your work**</span></span>
  
1. <span data-ttu-id="491da-200">**Start**を使用していずれかの\>**を実行** \> **PSR.exe**を入力\> **[ok]**、[ **Windows キー** ] をクリックして、または、 \> **PSR.exe**を入力\>し、ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="491da-200">Either use **Start** \> **Run** \> type **PSR.exe** \> **OK**, or, click the **Windows Key** \> type **PSR.exe** \> and then press ENTER.</span></span> 
    
2. <span data-ttu-id="491da-p124">PSR.exe 小さなウィンドウが表示されたら、**記録の開始**] をクリックし、パフォーマンスの問題を再現する手順を再現します。**コメントの追加**] をクリックして、必要に応じてコメントを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="491da-p124">When the small PSR.exe window appears, click **Start Record** and reproduce the steps that reproduce the performance issue. You can add comments as needed, by clicking **Add Comments**.</span></span>
    
3. <span data-ttu-id="491da-p125">手順が完了したら、 **[記録の停止**をクリックします。ページ レンダリングのパフォーマンスの問題が表示された場合、録画を停止する前にレンダリングするページを待ちます。</span><span class="sxs-lookup"><span data-stu-id="491da-p125">Click **Stop Record** when you have completed the steps. If the performance issue is a page render, wait for the page to render before you stop the recording.</span></span> 
    
4. <span data-ttu-id="491da-205">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="491da-205">Click **Save**.</span></span>
    
![ステップ記録ツールまたは PSR.exe のスクリーン ショットです。](media/8542b0aa-a3ff-4718-8dc4-43f5521c6c34.PNG)
  
<span data-ttu-id="491da-p126">するには、日付と時刻が記録されます。これは、HTTPWatch、Netmon のトレースに、PSR を時にリンクし、精度のトラブルシューティングに役立ちます。日付と時刻を PSR のレコードの 1 分が渡されることを表示できます、ログイン名と URL と、サイト管理者の部分的なレンダリングの例を参照の間です。</span><span class="sxs-lookup"><span data-stu-id="491da-p126">The date and time is recorded for you. This links your PSR to your Netmon trace and HTTPWatch in time, and helps with precision troubleshooting. The date and time in the PSR record can show that a minute passed between the login and browsing of the URL and the partial render of the admin site, for example.</span></span>
  
## <a name="read-your-traces"></a><span data-ttu-id="491da-210">トレースを読み取り</span><span class="sxs-lookup"><span data-stu-id="491da-210">Read your traces</span></span>

<span data-ttu-id="491da-p127">他の記事を使用して把握する必要があり、ネットワークのパフォーマンスのトラブルシューティングに関するすべての講義を行うことはありません。経験と知識、ネットワークの動作し、通常の実行のパフォーマンスを適切に対処がかかります。切り上げるには一番上の問題の一覧と、どのツールしやすく最も一般的な問題を解決するを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="491da-p127">It isn't possible to teach everything about network and performance troubleshooting that someone would need to know via an article. Getting good at performance takes experience, and knowledge of how your network works and usually performs. But it is possible to round up a list of top issues and show how tools can make it easier for you to eliminate the most common problems.</span></span>
  
<span data-ttu-id="491da-p128">Office 365 サイトのネットワーク トレースの読み取りのスキルを選択する場合は、定期的にページの読み込みのトレースを作成し、読み取ることの経験を積むよりも優れた先生はありません。などの可能性がある場合は、Office 365 サービスを読み込むし、プロセスをトレースします。DNS トラフィックの場合は、トレースをフィルター処理するか、参照するサービスの名前の FrameData を検索します。サービスが読み込まれるときに発生する手順を理解するためのトレースをスキャンします。これによって、どのような通常の学習ページを読み込む必要がありますようし、特に、パフォーマンス関連のトラブルシューティングの場合にトレースを比較することができますについて説明する多くします。</span><span class="sxs-lookup"><span data-stu-id="491da-p128">If you want to pick up skills reading network traces for your Office 365 sites, there is no better teacher than creating traces of page loads regularly and gaining experience reading them. For example, when you have a chance, load an Office 365 service and trace the process. Filter the trace for DNS traffic, or search the FrameData for the name of the service you browsed. Scan the trace to get an idea of the steps that occur when the service loads. This will help you learn what normal page load should look like, and in the case of troubleshooting, particularly around performance, comparing good to bad traces can teach you a lot.</span></span>
  
<span data-ttu-id="491da-p129">ネットワーク モニターは、[表示] フィルター フィールドの Microsoft Intellisense を使用します。Intellisense、または、インテリジェントなコード補完は、そのトリックの位置にピリオドを入力して、すべての利用可能なオプションは、ドロップダウン選択ボックスに表示されます。場合、たとえば、TCP ウィンドウ ・ スケーリングを心配は、フィルターする方法を検索できます (次のように`.protocol.tcp.window < 100`) この方法でします。</span><span class="sxs-lookup"><span data-stu-id="491da-p129">Netmon uses Microsoft Intellisense in the Display filter field. Intellisense, or intelligent code completion, is that trick where you type in a period and all available options are displayed in a drop-down selection box. If, for example, you are worried about TCP window scaling, you can find your way to a filter (such as  `.protocol.tcp.window < 100`) by this means.</span></span>
  
![Netmon のスクリーン ショットはことを示す表示フィルター] フィールドでは、intellisense を使用します。](media/75a56c11-9a60-47ee-a100-aabdfb1ba10f.PNG)
  
<span data-ttu-id="491da-p130">Netmon のトレースでは、それらの大量のトラフィックを持つことができます。それらを閲覧した経験がない場合に、トレースを最初に開くときに過負荷状態になりますが可能性があります。最初にすることは、トレースでは、バック グラウンド ノイズからの信号を分離します。、Office 365 を比較して表示するトラフィックであります。トレース内を移動するのにを使用した場合は、このリストをしない必要があります。</span><span class="sxs-lookup"><span data-stu-id="491da-p130">Netmon traces can have a lot of traffic in them. If you aren't experienced with reading them, it's likely you will be overwhelmed opening the trace the first time. The first thing to do is separate the signal from the background noise in the trace. You tested against Office 365, and that's the traffic you want to see. If you are used to navigating through traces, you may not need this list.</span></span>
  
<span data-ttu-id="491da-p131">トラフィックの本文が暗号化され、汎用的なネットワーク モニターのトレースで読み取ることができないことを示します、TLS を使用して、クライアントと Office 365 の間のトラフィックを通過します。パフォーマンス分析、パケット内の情報の詳細を知る必要はありません。ただし、パケットのヘッダーとそれに含まれる情報に非常に関心があります。</span><span class="sxs-lookup"><span data-stu-id="491da-p131">Traffic between your client and Office 365 travels via TLS, which means that the body of the traffic will be encrypted and not readable in a generic Netmon trace. Your performance analysis doesn't need to know the specifics of the information in the packet. It is, however, very interested in packet headers and the information that they contain.</span></span>
  
 <span data-ttu-id="491da-231">**正常なトレースを取得するためのヒント**</span><span class="sxs-lookup"><span data-stu-id="491da-231">**Tips to get a good trace**</span></span>
  
- <span data-ttu-id="491da-p132">クライアント コンピューターの IPv4 または IPv6 アドレスの値を知っています。コマンド プロンプトから**IPConfig**を入力し、し、ENTER キーを押して、これを取得できます。このアドレスを知ることがトレースでは、トラフィックが、クライアント コンピューターに直接関連するかどうかをひと目で判断できます。既知のプロキシがある場合は、に対して ping を実行しても、その IP アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="491da-p132">Know the value of the IPv4 or IPv6 address of your client computer. You can get this from the command prompt by typing **IPConfig** and then pressing ENTER. Knowing this address will let you tell at a glance whether the traffic in the trace directly involves your client computer. If there is a known proxy, ping it and get its IP address as well.</span></span> 
    
- <span data-ttu-id="491da-p133">DNS リゾルバー キャッシュをフラッシュし、可能であれば、テストを実行している 1 つを除くすべてのブラウザーを閉じます。これを行うことができない場合は、たとえば、サポートは、クライアント コンピューターのデスクトップを表示するいくつかのブラウザー ベースのツールを使用している場合、トレースにフィルターを適用する準備ができてあります。</span><span class="sxs-lookup"><span data-stu-id="491da-p133">Flush your DNS resolver cache and, if possible, close all browsers except the one in which you are running your tests. If you are not able to do this, for instance, if support is using some browser-based tool to see your client computer's desktop, be prepared to filter your trace.</span></span>
    
- <span data-ttu-id="491da-p134">トレースのビジーでは、使用している Office 365 のサービスを探します。しないか、ほとんど見たことの前に、トラフィック、これが役に立つの手順を使用して他のネットワークのノイズとパフォーマンスの問題を分離すること。これを行ういくつかの方法があります。直接、テストの前にまたはを使用して ping、特定のサービスの URL に、PsPing (`ping outlook.office365.com`と`psping -4 microsoft-my.sharepoint.com:443`の例については)。簡単に検索することができます (プロセス名) を指定してネットワーク モニターのトレースでは、その PsPing。検索を開始する場所が提供されます。</span><span class="sxs-lookup"><span data-stu-id="491da-p134">In a busy trace, locate the Office 365 service that you're using. If you've never or seldom seen your traffic before, this is a helpful step in separating the performance issue from other network noise. There are a few ways to do this. Directly before your test, you can use ping or, PsPing, to the URL of the specific service ( `ping outlook.office365.com` and/or  `psping -4 microsoft-my.sharepoint.com:443`, for examples) . You can also easily find that PsPing in a Netmon trace (by its process name). That will give you a place to start looking.</span></span>
    
    <span data-ttu-id="491da-p135">問題の時にのみネットワーク モニター トレースを使用している場合は問題ありませんが。たとえばのようなフィルターを使用して、`ContainsBin(FrameData, ASCII, "office")`または`ContainsBin(FrameData, ASCII, "outlook")`。トレース ファイルから、フレームの数を記録することができます。右側のフレームの概要ウィンドウをスクロールし、会話 ID] 列を検索することもできます。Id がこの特定の会話も記録して後で分離した状態で見ているが示された数値があります。その他のフィルターを適用する前にこのフィルターを削除してください。</span><span class="sxs-lookup"><span data-stu-id="491da-p135">If you're only using Netmon tracing at the time of the problem, that's okay too. To orient yourself, use a filter like  `ContainsBin(FrameData, ASCII, "office")` or  `ContainsBin(FrameData, ASCII, "outlook")`. You can record your frame number from the trace file. You may also want to scroll the Frame Summary pane all the way to the right and look for the Conversation ID column. There is a number indicated there for the ID of this specific conversation that you can also record and look at in isolation later. Remember to remove this filter before applying any other filtering.</span></span>
    
> [!TIP]
> <span data-ttu-id="491da-p136">ネットワーク モニターは、多くの便利な組み込みのフィルターを持っています。**表示**フィルター] ペインの上部にある [フィルターの読み込み] ボタンを実行してください。</span><span class="sxs-lookup"><span data-stu-id="491da-p136">Netmon has a lot of helpful built-in filters. Try the "Load Filter" button at the top of the **Display** filter pane.</span></span> 
  
![コマンド ライン クライアント コンピューター上で PSPing を使用して、IP を検索します。](media/4c43ac67-e28e-4536-842d-7add7aa28847.PNG)
  
![Netmon のトレースは、クライアントの TCP フィルターを同じ [PSPing] コマンドを表示します。Flags.Syn 1 を = =。](media/0ae7ef7d-e003-4d01-a006-dc49bd1fcef2.PNG)
  
<span data-ttu-id="491da-p137">トラフィックでは、慣れるし、必要な情報を検索する方法について説明します。たとえば、トレースにどのパケットのように"Outlook") を使用している Office 365 サービスが最初に参照を確認するについて説明します。</span><span class="sxs-lookup"><span data-stu-id="491da-p137">Get familiar with your traffic, and learn to locate the information you need. For example, learn to determine which packet in the trace has the first reference to the Office 365 service you're using (like "Outlook").</span></span>
    
<span data-ttu-id="491da-256">Office 365 Outlook オンラインを取る例として、トラフィックを以下のように開始します。</span><span class="sxs-lookup"><span data-stu-id="491da-256">Taking Office 365 Outlook Online as an example, the traffic begins something like this:</span></span>
  
- <span data-ttu-id="491da-p138">DNS の標準的なクエリと QueryIDs が一致する outlook.office365.com の DNS 応答します。名前解決の要求を送信するこのターンのようにどこの世界で Office 365 のグローバル DNS の時間オフセットに注意する必要があります。理想的には、世界中に途中ではなく、可能なローカルにします。(いくつかでこの後にすることがあります DNS トラフィックのオンラインのログインです)。</span><span class="sxs-lookup"><span data-stu-id="491da-p138">DNS Standard Query and DNS Response for outlook.office365.com with matching QueryIDs. It's important to note the Time Offset for this turn-around, as well as where in the world the Office 365 Global DNS sends the request for name resolution. Ideally, as locally as possible, rather than half-way across the world. (This may be followed by some DNS traffic the online login.)</span></span>
    
- <span data-ttu-id="491da-261">HTTP GET 要求ステータスが報告する移動完全に (301)</span><span class="sxs-lookup"><span data-stu-id="491da-261">A HTTP GET Request whose status report Moved Permanently (301)</span></span>
    
- <span data-ttu-id="491da-p139">RWS の接続を含む RWS のトラフィックでは、要求、応答を接続してください。(これは、リモート Winsock の接続を作成するためです)。</span><span class="sxs-lookup"><span data-stu-id="491da-p139">RWS Traffic including RWS Connect requests and Connect replies. (This is Remote Winsock making a connection for you.)</span></span>
    
- <span data-ttu-id="491da-p140">TCP SYN と TCP SYN と ACK の会話です。このスレッドの設定の多くのパフォーマンスに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="491da-p140">A TCP SYN and TCP SYN/ACK conversation. A lot of the settings in this conversation impact your performance.</span></span>
    
- <span data-ttu-id="491da-p141">一連の TLS:TLS のトラフィックは、TLS ハンドシェイクと TLS 証明書の会話を実行します。(データは、SSL や TLS を使用して暗号化を注意してください)。</span><span class="sxs-lookup"><span data-stu-id="491da-p141">Then a series of TLS:TLS traffic which is where the TLS handshake and TLS certificate conversations take place. (Remember the data is encrypted via SSL/TLS.)</span></span>
    
<span data-ttu-id="491da-p142">トラフィックのすべての部分が重要であり、接続には、トレースの部分が小さいため、これらの分野に注目してパフォーマンスのトラブルシューティング、という点で特に重要な情報が含まれています。十分なトラブルシューティング一般的な問題のトップ 10 のリストをコンパイルするのにはマイクロソフトの Office 365 のパフォーマンスがやったのでこれらの問題について、次にそれらのルートにあるツールを使用する方法にフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="491da-p142">All parts of the traffic are important and connected, but small portions of the trace contain information particularly important in terms of performance troubleshooting, so we'll focus on those areas. Also, since we've done enough Office 365 performance troubleshooting at Microsoft to compile a Top Ten list of common problems, we'll focus on those issues and how to use the tools we have to root them out next.</span></span>
  
<span data-ttu-id="491da-p143">それらをインストールしていない場合、すべて準備が次の表には、いくつかのツールを使用します。可能な場合です。インストール ポイントには、リンクが用意されています。一覧には、[ネットワーク モニター](https://www.microsoft.com/en-us/download/details.aspx?id=4865) [Wireshark](https://www.wireshark.org/)などの一般的なネットワーク トレース ツールが含まれますが、およびネットワーク トラフィックをフィルタ リングするのには慣れている、慣れている場合、トレース ツールを使用します。テストしているときに注意してください。</span><span class="sxs-lookup"><span data-stu-id="491da-p143">If you haven't installed them all ready, the matrix below makes use of several tools. Where possible. Links are provided to the installation points. The list includes common network tracing tools like [Netmon](https://www.microsoft.com/en-us/download/details.aspx?id=4865) and [Wireshark](https://www.wireshark.org/), but use any tracing tool you are comfortable with, and in which you're accustomed to filtering network traffic. When you're testing, remember:</span></span>
  
-  <span data-ttu-id="491da-p144">*ブラウザーを閉じるしテストを実行しているブラウザーを 1 つ*の全体的なトラフィックをキャプチャするが低きます。少ないトレースのほうです。</span><span class="sxs-lookup"><span data-stu-id="491da-p144">*Close your browsers, and test with only one browser running*  - This will reduce the overall traffic you capture. It makes for a less busy trace.</span></span> 
    
-  <span data-ttu-id="491da-277">*クライアント コンピューターでは、DNS リゾルバー キャッシュをフラッシュ*- これにより、白紙のキャプチャをクリーナーのトレースを開始するとします。</span><span class="sxs-lookup"><span data-stu-id="491da-277">*Flush your DNS resolver cache on the client computer*  - This will give you a clean slate when you start to take your capture, for a cleaner trace.</span></span> 
    
## <a name="some-top-issues"></a><span data-ttu-id="491da-278">いくつか上の問題</span><span class="sxs-lookup"><span data-stu-id="491da-278">Some Top Issues</span></span>

<span data-ttu-id="491da-279">いくつかの一般的な問題に直面することと、ネットワーク トレースでそれらを検索する方法です。</span><span class="sxs-lookup"><span data-stu-id="491da-279">Some common issues you may face and how to find them in your Network trace.</span></span>

### <a name="tcp-windows-scaling"></a><span data-ttu-id="491da-280">TCP ウィンドウのスケーリング</span><span class="sxs-lookup"><span data-stu-id="491da-280">TCP Windows Scaling</span></span>

<span data-ttu-id="491da-p145">SYN に SYN/確認のレガシ クライアントまたは古いハードウェアを使用にならない TCP ウィンドウのスケーリングを利用。 適切な TCP ウィンドウのスケーリングの設定をしなくても TCP ヘッダーの既定の 16 ビット バッファーをミリ秒単位で塗りつぶします。 トラフィックを受信したクライアントが元のデータが受信されたこと、遅延が発生するまで送信を続行できません。</span><span class="sxs-lookup"><span data-stu-id="491da-p145">Found in the SYN - SYN/ACK. Legacy or aging hardware may not take advantage of TCP windows scaling.  Without proper TCP windows scaling settings, the default 16-bit buffer in TCP headers fills in milliseconds.  Traffic cannot continue to send until the client receives an acknowledgment that the original data has been received, causing delays.</span></span>

#### <a name="tools"></a><span data-ttu-id="491da-285">ツール:</span><span class="sxs-lookup"><span data-stu-id="491da-285">Tools:</span></span>

- <span data-ttu-id="491da-286">ネットワーク モニター</span><span class="sxs-lookup"><span data-stu-id="491da-286">Netmon</span></span>
- <span data-ttu-id="491da-287">Wireshark</span><span class="sxs-lookup"><span data-stu-id="491da-287">Wireshark</span></span> 

#### <a name="what-youre-looking-for"></a><span data-ttu-id="491da-288">何を探しています。</span><span class="sxs-lookup"><span data-stu-id="491da-288">What you're looking for:</span></span>

<span data-ttu-id="491da-p146">ネットワーク トレースでは、トラフィックを SYN の SYN と ACK を探します。 ネットワーク モニターでのようなフィルターを使用して、 `tcp.flags.syn == 1`。このフィルターは、Wireshark で同じです。</span><span class="sxs-lookup"><span data-stu-id="491da-p146">Look for the SYN - SYN/ACK traffic in your network trace.  In Netmon, use a filter like  `tcp.flags.syn == 1`. This filter is the same in Wireshark.</span></span>  

![両方のツールのために Syn パケットをネットワーク モニターまたは Wireshark でフィルター: TCP です。Flags.Syn 1 を = =。](media/4b9a12a1-c915-43c8-ac2f-a679d0435a29.PNG)         
<span data-ttu-id="491da-293">すべて SYN に対しては (SYN ACK)、関連する受信確認メッセージの宛先のポート (DstPort) に一致するソース (任意) のポート番号に注意してください。</span><span class="sxs-lookup"><span data-stu-id="491da-293">Notice that for every SYN there is a source port (SrcPort) number that is matched in the destination port (DstPort) of the related Acknowledgment (SYN/ACK).</span></span> 

<span data-ttu-id="491da-294">ネットワーク接続で使用されるウィンドウ ・ スケーリングの値を表示するには、最初の SYN を展開し展開関連の SYN/確認</span><span class="sxs-lookup"><span data-stu-id="491da-294">To see the Windows Scaling value that is used by your network connection, expand first the SYN, and then the related SYN/ACK.</span></span>  

![グラフィックには DstPort を任意の時間差を取得するときに、トレースで一致する方法を示します。](media/6a4ca573-0253-4fbd-93e8-92821ee1c351.png)  

### <a name="tcp-idle-time-settings"></a><span data-ttu-id="491da-296">TCP アイドル時間の設定</span><span class="sxs-lookup"><span data-stu-id="491da-296">TCP Idle Time Settings</span></span>

<span data-ttu-id="491da-p147">従来、一時的な接続、つまり、アイドル状態の接続が終了する通常のほとんどの境界領域ネットワークが構成されています。アイドル状態の TCP セッションを終了するには、プロキシやファイアウォールが 100 ~ 300 秒より大きい値にします。これは Outlook のオンラインの問題を作成し、長期的な接続を使用してがアイドル状態かどうかです。</span><span class="sxs-lookup"><span data-stu-id="491da-p147">Historically, most perimeter networks are configured for transient connections, meaning idle connections are generally terminated. Idle TCP sessions can be terminated by proxies and firewalls at greater than 100 to 300 seconds. This is problematic for Outlook Online because it creates and uses long-term connections, whether they are idle or not.</span></span>  

<span data-ttu-id="491da-p148">プロキシによって接続が終了するか、ファイアウォール デバイスが、クライアントは情報を入手するとオンラインの Outlook を使用しようとすると、クライアント コンピューターと、しようと、繰り返し、新しいを作成する前に接続を回復します。ページのロード時に、製品、プロンプト、またはパフォーマンスの低下にハングするを参照してください可能性があります。</span><span class="sxs-lookup"><span data-stu-id="491da-p148">When connections are terminated by proxy or firewall devices, the client is not informed, and an attempt to use Outlook Online will mean a client computer will try, repeatedly, to revive the connection before making a new one. You may see hangs in the product, prompts, or slow performance on page load.</span></span>

#### <a name="tools"></a><span data-ttu-id="491da-302">ツール:</span><span class="sxs-lookup"><span data-stu-id="491da-302">Tools:</span></span>

- <span data-ttu-id="491da-303">ネットワーク モニター</span><span class="sxs-lookup"><span data-stu-id="491da-303">Netmon</span></span>
- <span data-ttu-id="491da-304">Wireshark</span><span class="sxs-lookup"><span data-stu-id="491da-304">Wireshark</span></span>

#### <a name="what-to-look-for"></a><span data-ttu-id="491da-305">何を検索するには。</span><span class="sxs-lookup"><span data-stu-id="491da-305">What to look for:</span></span>

<span data-ttu-id="491da-p149">ネットワーク モニターでのラウンドト リップ時間オフセット フィールドを見てください。ラウンドト リップは、クライアントがサーバーに要求を送信して、応答が戻るまでの時間です。クライアントと出口ポイントの確認 (例: クライアント--\>プロキシ)、または Office 365 クライアント (クライアント -\> Office 365)。これで多くの種類のパケットを表示できます。</span><span class="sxs-lookup"><span data-stu-id="491da-p149">In Netmon, look at the Time Offset field for a round-trip. A round-trip is the time between client sending a request to the server and receiving a response back. Check between the Client and the egress point (ex. Client --\> Proxy), or the Client to Office 365 (Client --\> Office 365). You can see this in many types of packets.</span></span> 

<span data-ttu-id="491da-311">たとえば、ネットワーク モニターでフィルター次のように`.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`、または、Wireshark、 `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`。</span><span class="sxs-lookup"><span data-stu-id="491da-311">As an example, the filter in Netmon may look like  `.Protocol.IPv4.Address == 10.102.14.112 AND .Protocol.IPv4.Address == 10.201.114.12`, or, in Wireshark,  `ip.addr == 10.102.14.112 &amp;&amp; ip.addr == 10.201.114.12`.</span></span>  

> [!TIP]
> <span data-ttu-id="491da-p150">トレースでは、IP アドレスが DNS サーバーに属しているかわからないでしょうか。コマンド ・ ラインで検索してみてください。[**スタート**] ボタン\>**を実行** \> **cmd**を入力するか、 **Windows キー**を押すと\>、 **cmd**と入力します。プロンプトで次のように入力します。 `nslookup <the IP address from the network trace>`。テストするには、自分のコンピューターの IP アドレスを nslookup を使用します。> マイクロソフトの IP 範囲の一覧を表示するには、 [Office 365 の Url と IP アドレスの範囲](https://technet.microsoft.com/en-us/library/hh373144.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="491da-p150">Don't know if the IP address in your trace belongs to your DNS server? Try looking it up at the command line. Click **Start** \> **Run** \> and type **cmd**, or press **Windows Key** \> and type **cmd**. At the prompt, type  `nslookup <the IP address from the network trace>`. To test, use nslookup against your own computer's IP address. > To see a list of Microsoft's IP ranges, see [Office 365 URLs and IP address ranges](https://technet.microsoft.com/en-us/library/hh373144.aspx).</span></span> 

<span data-ttu-id="491da-p151">問題がある場合の予想される長い時間のオフセット (Outlook オンライン)、ここでは、表示するのには特にアプリケーション ・ データの経過を表示する TLS:TLS パケット (など、ネットワーク モニターで表示を使用してアプリケーション データのパケット`.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`)。セッション間で時間内のスムーズな進行を参照してくださいする必要があります。オンラインの Outlook を更新するときに時間がかかるが表示された場合のリセットが送信されている高度これによる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="491da-p151">If there is a problem, expect long Time Offsets to appear, in this case (Outlook Online), particularly in TLS:TLS packets that show the passage of Application Data (for example, in Netmon you can find application data packets via  `.Protocol.TLS AND Description == "TLS:TLS Rec Layer-1 SSL Application Data"`). You should see a smooth progression in the time across the session. If you see long delays when refreshing your Outlook Online, this could be caused by a high degree of resets being sent.</span></span> 

### <a name="latencyround-trip-time"></a><span data-ttu-id="491da-321">遅延とラウンドが作動する時間</span><span class="sxs-lookup"><span data-stu-id="491da-321">Latency/Round Trip Time</span></span> 

<span data-ttu-id="491da-322">待ち時間は、多くの変数、そのようなエイジングのデバイスをアップグレードする、ネットワーク、およびネットワーク接続では、他のタスクによって消費されている、全体的な帯域幅の割合に多数のユーザーを追加することによって大幅な変更がメジャーです。</span><span class="sxs-lookup"><span data-stu-id="491da-322">Latency is a measure that can change a lot depending on many variables, such upgrading aging devices, adding a large number of users to a network, and the percentage of overall bandwidth consumed by other tasks on a network connection.</span></span> 

<span data-ttu-id="491da-323">Office 365 の帯域幅の計算機は[このネットワークの計画と Office 365 のパフォーマンスの調整](network-planning-and-performance.md)] ページから利用可能です。</span><span class="sxs-lookup"><span data-stu-id="491da-323">There are bandwidth calculators for Office 365 available from this [Network planning and performance tuning for Office 365](network-planning-and-performance.md) page.</span></span>  

<span data-ttu-id="491da-p152">接続、または、ISP への接続の帯域幅の速度を測定する必要がありますか。このサイト (またはそのようなサイト) を実行してください: [Speedtest の公式サイト](https://www.speedtest.net/)、および[Pingtest](http://www.pingtest.net/)。</span><span class="sxs-lookup"><span data-stu-id="491da-p152">Need to measure the speed of your connection, or your ISP connection's bandwidth? Try this site (or sites like it): [Speedtest Official Site](https://www.speedtest.net/), and [Pingtest](http://www.pingtest.net/).</span></span>

#### <a name="tools"></a><span data-ttu-id="491da-326">ツール:</span><span class="sxs-lookup"><span data-stu-id="491da-326">Tools:</span></span>

- <span data-ttu-id="491da-327">Ping</span><span class="sxs-lookup"><span data-stu-id="491da-327">Ping</span></span>
- <span data-ttu-id="491da-328">PsPing</span><span class="sxs-lookup"><span data-stu-id="491da-328">PsPing</span></span>
- <span data-ttu-id="491da-329">ネットワーク モニター</span><span class="sxs-lookup"><span data-stu-id="491da-329">Netmon</span></span>
- <span data-ttu-id="491da-330">Wireshark</span><span class="sxs-lookup"><span data-stu-id="491da-330">Wireshark</span></span>

#### <a name="what-to-look-for"></a><span data-ttu-id="491da-331">何を検索するには。</span><span class="sxs-lookup"><span data-stu-id="491da-331">What to look for:</span></span>

<span data-ttu-id="491da-p153">トレースでの待機時間を追跡するために利益が得られます Office 365 にクライアント コンピューターの IP アドレスと DNS サーバーの IP アドレスを記録することです。簡単なトレースのフィルター処理するためです。プロキシを介して接続すると、クライアント コンピューターの IP アドレス、プロキシ/出口となる IP アドレス、および Office 365 の DNS の IP アドレスで、作業を容易にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="491da-p153">To track latency in a trace, you will benefit from having recorded the client computer IP address and the IP address of the DNS server in Office 365. This is for the purpose of easier trace filtering. If you connect through a proxy, you will need your client computer IP address, the proxy/egress IP address, and the Office 365 DNS IP address, to make the work easier.</span></span>  

<span data-ttu-id="491da-p154">Outlook.office365.com に送信される ping 要求が送信されますが、要求を受信するデータ センターの名前 ping の*場合があります*商標の連続した ICMP パケットを送信するのには接続できない場合でも。PsPing (ダウンロードできる無料のツール)、および特定のポート (443) を使用すると、おそらく IPv4 を使用する (-4) が表示されます、平均 round-trip 時パケットが送信されるのです。これがこれで Office 365 サービスでは、他の Url のような`psping -4 yourSite.sharepoint.com:443`。実際には、次のように、平均すると、モデムより大きなサンプルを取得するのには ping の数を指定できます: `psping -4 -n 20 yourSite-my.sharepoint.com:443`。</span><span class="sxs-lookup"><span data-stu-id="491da-p154">A ping request sent to outlook.office365.com will tell you the name of the datacenter receiving the request, even if ping  *may*  not be able to connect to send the trademark consecutive ICMP packets. If you use PsPing (a free tool for download), and specific the port (443) and perhaps to use IPv4 (-4) you will get an average round-trip-time for packets sent. This will work this for other URLs in the Office 365 services, like  `psping -4 yourSite.sharepoint.com:443`. In fact, you can specify a number of pings to get a larger sample for your average, try something like:  `psping -4 -n 20 yourSite-my.sharepoint.com:443`.</span></span>  

> [!NOTE]
> <span data-ttu-id="491da-p155">PsPing では、ICMP パケットを送信しません。それに対して ping を実行 TCP パケットを特定のポート上でいずれかを開くことがわかってを使用できるようにします。Office 365 は、SSL や TLS を使用しているポートの接続を試してください: 443、PsPing にします。</span><span class="sxs-lookup"><span data-stu-id="491da-p155">PsPing doesn't send ICMP packets. It pings with TCP packets over a specific port, so you can use any one you know to be open. In Office 365, which uses SSL/TLS, try attaching port :443 to your PsPing.</span></span>

![Outlook.office365.com、および、PSPing を解決する作業を行うこと、ですが、また 6.5ms の平均 RTT をレポートに 443 と ping を表示する画面です。](media/c64339f2-2c96-45b8-b168-c2a060430266.PNG)        

<span data-ttu-id="491da-p156">ネットワーク トレースの実行中に低速の実行中の Office 365 ページをロードした場合のネットワーク モニターまたは Wireshark のトレースをフィルター処理する必要があります`DNS`。これは、探している ip アドレスのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="491da-p156">If you loaded the slow performing Office 365 page while doing a network trace, you should filter a Netmon or Wireshark trace for  `DNS`. This is one of the IPs we're looking for.</span></span>  

<span data-ttu-id="491da-p157">IP アドレスを取得 (および DNS の遅延時間を見て) に、Netmon をフィルター処理するための手順を次に示します。次の使用例は、outlook.office365.com を使用しますが、SharePoint Online テナント (たとえば hithere.sharepoint.com) の URL を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="491da-p157">Here are the steps to take to filter your Netmon to get the IP address (and take a look at DNS Latency). This example uses outlook.office365.com, but may also use the URL of a SharePoint Online tenant (hithere.sharepoint.com for example).</span></span>  

1. <span data-ttu-id="491da-347">URL に ping を実行`ping outlook.office365.com`と、結果の中に ping 要求が送信された DNS サーバーの IP アドレスと名前を記録します。</span><span class="sxs-lookup"><span data-stu-id="491da-347">Ping the URL `ping outlook.office365.com` and, in the results, record the name and IP address of the DNS server the ping request was sent to.</span></span> 
2. <span data-ttu-id="491da-348">ネットワーク トレースのページを開くまたはアクションを実行により、パフォーマンス上の問題、または、ネットワークをトレースする場合は、それ自体には、ping の遅延時間が長いを参照してください。</span><span class="sxs-lookup"><span data-stu-id="491da-348">Network trace opening the page, or doing the action that gives you the performance problem, or, if you see a high latency on the ping, itself, network trace it.</span></span> 
3. <span data-ttu-id="491da-p158">Dns とフィルターのネットワーク モニターでトレースを開く (このフィルターも Wireshark で動作するが、大文字と小文字を区別`-- dns`)。次のように複数の的確でネットワーク モニターを抽出する、ping から DNS サーバーの名前がわかっているためも可能性があります:`DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")`のようなこの Wireshark の dns では、フレームには、"namnorthwest"が含まれています。</span><span class="sxs-lookup"><span data-stu-id="491da-p158">Open the trace in Netmon and filter for DNS (this filter also works in Wireshark, but is sensitive to case `-- dns`). Since you know the name of the DNS server from your ping you may also filter more speedily in Netmon like this: `DNS AND ContainsBin(FrameData, ASCII, "namnorthwest")` , which looks like this in Wireshark dns and frame contains "namnorthwest".</span></span><br/><span data-ttu-id="491da-p159">応答パケットを開き、ネットワーク モニターのフレームの詳細] ウィンドウで [DNS の詳細を展開する] をクリックします。DNS 情報を Office 365 - の要求にした DNS サーバーの IP アドレスを検索します次のステップ (PsPing ツール) の IP アドレスを必要することになります。フィルターを削除する、ネットワーク モニターのフレームの概要で DNS 応答を右クリックし\>会話の検索\>DNS は、DNS クエリと応答サイド バイ サイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="491da-p159">Open the response packet and, in Frame Details window of Netmon, click DNS to expand for more information. In the DNS information you'll find the IP address of the DNS server the request went to in Office 365 -- you'll need this IP address for the next step (the PsPing tool). Remove the filter, right-click on the DNS Response in Netmon's Frame Summary \> Find Conversations \> DNS to see the DNS Query and Response side-by-side.</span></span> 
4. <span data-ttu-id="491da-p160">ネットワーク モニターでも、DNS の要求と応答の間で時間のオフセットの列に注意してください。次の手順、簡単にインストール、および[PsPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx)を使用してツールには、非常に便利ですが、ICMP は多くの場合、ファイアウォールでブロックされているためと PsPing が洗練された方法にミリ秒単位の待機時間を追跡するための両方です。PsPing は、アドレスとポート番号 (このケース開いているポート 443) への TCP 接続を完了します。</span><span class="sxs-lookup"><span data-stu-id="491da-p160">In Netmon, also note the Time Offset  column between the DNS Request and Response. In the next step, the easy-to-install and use [PsPing](https://technet.microsoft.com/en-us/sysinternals/jj729731.aspx) tool comes in very handy, both because ICMP is often blocked on Firewalls, and because PsPing elegantly tracks latency in milliseconds. PsPing completes a TCP connection to an address and port (in our case open port 443).</span></span> 
5. <span data-ttu-id="491da-357">PsPing をインストールします。</span><span class="sxs-lookup"><span data-stu-id="491da-357">Install PsPing.</span></span> 
6. <span data-ttu-id="491da-p161">コマンド プロンプトを開き (開始\>実行\>cmd、または Windows キーを入力\>cmd と入力します)、PsPing コマンドを実行する PsPing をインストールしたディレクトリにディレクトリを変更します。私の例で c ドライブのルート上の 'パフォーマンス' フォルダーの内容を確認できます。すばやくアクセスできる同じを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="491da-p161">Open a command prompt (Start \> Run \> type cmd, or Windows Key \> type cmd) and change directory to the directory where you installed PsPing to run the PsPing command. In my examples you can see I made a 'Perf' folder on the root of C. You can do the same for quick access.</span></span> 
7. <span data-ttu-id="491da-360">コマンドを入力して、以前のネットワーク モニターのトレースから Office 365 の DNS サーバーの IP アドレスに対して、PsPing を作成するように--ポート番号を追加することを忘れないでください。</span><span class="sxs-lookup"><span data-stu-id="491da-360">Type the command so that you're making your PsPing against the IP address of the Office 365 DNS server from your earlier Netmon trace -- remember to add the port number.</span></span> <br/><span data-ttu-id="491da-p162">つまり、 `psping -n 20 132.245.24.82:445`。20 の ping のサンプリングを使用すれば、PsPing が停止したときの遅延時間の平均します。</span><span class="sxs-lookup"><span data-stu-id="491da-p162">In other words, `psping -n 20 132.245.24.82:445`. This will give you a sampling of 20 pings and average the latency when PsPing stops.</span></span> 

<span data-ttu-id="491da-p163">しようとしている Office 365 プロキシ サーバーを介して場合の手順は多少異なります。プロキシ/出口とする時間をミリ秒で、平均待機時間の値を取得するのにはプロキシ サーバーに最初の PsPing の場合とし、PsPing を実行するか、プロキシで、または (1 つを元に戻すと、Office 365) 不足している値を取得するインターネットに直接接続を持つコンピューターにします。</span><span class="sxs-lookup"><span data-stu-id="491da-p163">If you're going to Office 365 through a proxy server, the steps are a little different. You would first PsPing to your proxy server to get an average latency value in milliseconds to proxy/egress and back, and then either run PsPing on the proxy, or on a computer with a direct Internet connection to get the missing value (the one to Office 365 and back).</span></span>  

<span data-ttu-id="491da-p164">プロキシから PsPing を実行する場合は、2 つのミリ秒の値が必要があります: プロキシ サーバーまたは出口点、および Office 365 にプロキシ サーバーへのクライアント コンピューターです。いる!とにかく値を記録します。</span><span class="sxs-lookup"><span data-stu-id="491da-p164">If you choose to run PsPing from the proxy, you'll have two millisecond values: Client computer to proxy server or egress point, and proxy server to Office 365. And you're done! Well, recording values, anyway.</span></span>  

<span data-ttu-id="491da-p165">インターネットに直接接続されている別のクライアント コンピューターで PsPing を実行する場合は、プロキシを使用せずする必要が 2 つのミリ秒の値: クライアント コンピューターがプロキシ サーバーまたは出口点、および Office 365 クライアント コンピューターです。この例では、クライアント コンピューターの値をプロキシ サーバーまたは出口のポイントに Office 365 では、クライアント コンピューターの値から減算および RTT の番号は、クライアント コンピューターから、プロキシ サーバーまたは出口ポイントする必要があるプロキシ サーバーまたは出口をポイント Office 365 です。</span><span class="sxs-lookup"><span data-stu-id="491da-p165">If you run PsPing on another client computer that has a direct connection to the Internet, that is, without a proxy, you will have two millisecond values: Client computer to proxy server or egress point, and client computer to Office 365. In this case, subtract the value of client computer to proxy server or egress point from the value of client computer to Office 365, and you will have the RTT numbers from your client computer to the proxy server or egress point, and from proxy server or egress point to Office 365.</span></span> 

<span data-ttu-id="491da-370">クライアント コンピューターは、直接接続されているか、またはプロキシをバイパスする脆弱性による影響の場所にあります場合するかどうか、問題を再現が最初を参照してくださいして、それ以降を使用してテストできます。</span><span class="sxs-lookup"><span data-stu-id="491da-370">However, if you can find a client computer in the impacted location that is directly connected, or bypasses the proxy, you may choose to see if the issue reproduces there to begin with, and test using it, thereafter.</span></span> 

<span data-ttu-id="491da-371">遅延、Netmon のトレースに示すようにそれらの余分な (ミリ秒) を追加できます、任意指定のセッションでは、それらの十分な場合。</span><span class="sxs-lookup"><span data-stu-id="491da-371">Latency, as seen in a Netmon trace, those extra milliseconds can add up, if there are enough of them in any given session.</span></span>  

![フレームの概要に Netmon の既定の [時間差] 列が追加された、Netmon の一般的な待ち時間。](media/7ad17380-8527-4bc2-9b9b-6310cf19ba6b.PNG)

> [!NOTE]
> <span data-ttu-id="491da-p166">あなたの IP アドレスは、ip アドレスの ping は、以上のような 157.56.0.0/16 または類似の範囲を返すことがあります、ここでは、表示とは異なる可能性があります。Office 365 で使用する範囲のリストは、 [Office 365 の Url と IP アドレスの範囲](https://technet.microsoft.com/en-us/library/hh373144.aspx)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="491da-p166">Your IP address may be different than the IPs shown here, for example, your ping may return something more like 157.56.0.0/16 or a similar range. For a list of ranges used by Office 365, check out [Office 365 URLs and IP address ranges](https://technet.microsoft.com/en-us/library/hh373144.aspx).</span></span> 

<span data-ttu-id="491da-375">、たとえば、132.245 を検索する場合は、(ボタンがこれの上部にある) のすべてのノードを展開してください。</span><span class="sxs-lookup"><span data-stu-id="491da-375">Remember to expand all the nodes (there's a button at the top for this) if you want to search for, for example, 132.245.</span></span>

### <a name="proxy-authentication"></a><span data-ttu-id="491da-376">プロキシ認証</span><span class="sxs-lookup"><span data-stu-id="491da-376">Proxy Authentication</span></span>

<span data-ttu-id="491da-p167">これだけに適用 プロキシ サーバーを経由する場合。それ以外の場合は、次の手順をスキップすることができます。正常に動作するとプロキシの認証する必要があります実行ミリ秒単位で一貫しています。(例) 使用率のピーク時に断続的なパフォーマンスの低下は表示されません。</span><span class="sxs-lookup"><span data-stu-id="491da-p167">This only applies to you if you're going through a proxy server. If not, you can skip these steps. When working properly, proxy authentication should take place in milliseconds, consistently. You shouldn't see intermittent bad performance during peak usage periods (for example).</span></span>  

<span data-ttu-id="491da-p168">プロキシ認証がある場合に、情報を取得するのには Office 365 に新しい TCP 接続を行うたびに、バック グラウンドでの認証プロセスを通過する必要があります。たとえば、Outlook のオンラインでのメールを予定表に切り替えると、を認証します。SharePoint online では、メディアまたは複数のサイトまたは場所からデータにページが表示される場合を認証する各別の TCP 接続のデータをレンダリングするために必要なのです。</span><span class="sxs-lookup"><span data-stu-id="491da-p168">If Proxy authentication is on, each time you make a new TCP connection to Office 365 to get information, you need to pass through an authentication process behind the scenes. So, for example, when switching from Calendar to Mail in Outlook Online, you will authenticate. And in SharePoint Online, if a page displays media or data from multiple sites or locations, you will authenticate for each different TCP connection that is needed in order to render the data.</span></span>  

<span data-ttu-id="491da-p169">オンラインの Outlook の予定表と自分のメールボックスの間で切り替えるか、SharePoint Online で表示の遅いページが読み込まれるたびに、低速の読み込み時間があります。ただし、これには記載されていないその他の現象があります。</span><span class="sxs-lookup"><span data-stu-id="491da-p169">In Outlook Online, you may experience slow load times whenever you switch between Calendar and your mailbox, or slow page loads in SharePoint Online. However, there are other symptoms not listed here.</span></span> 

<span data-ttu-id="491da-p170">プロキシ認証は、外部プロキシ サーバーの設定です。Office 365 で、パフォーマンスの問題の原因となって、ネットワーク チームを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="491da-p170">Proxy authentication is a setting on your egress proxy server. If it is causing a performance issue with Office 365, you must consult your networking team.</span></span>  

#### <a name="tool"></a><span data-ttu-id="491da-388">ツール:</span><span class="sxs-lookup"><span data-stu-id="491da-388">Tool:</span></span> 

- <span data-ttu-id="491da-389">ネットワーク モニター</span><span class="sxs-lookup"><span data-stu-id="491da-389">Netmon</span></span>
- <span data-ttu-id="491da-390">Wireshark</span><span class="sxs-lookup"><span data-stu-id="491da-390">Wireshark</span></span> 

#### <a name="what-to-look-for"></a><span data-ttu-id="491da-391">何を検索するには。</span><span class="sxs-lookup"><span data-stu-id="491da-391">What to look for:</span></span>

<span data-ttu-id="491da-p171">認証は、プロキシは、新しい TCP セッションがサーバーからファイルや情報を要求するには、一般的または情報を提供する、スピンする必要がありますたびに配置します。たとえば、HTTP GET または HTTP POST 要求をプロキシ認証を参照してください可能性があります。トレースでは、要求を認証するか、フレームを表示する場合は、Netmon に NTLMSSP 要約 ' 列を追加し、フィルター `.property.NTLMSSPSummary`。認証に時間がかかるを参照してください、時間デルタ] 列を追加します。</span><span class="sxs-lookup"><span data-stu-id="491da-p171">Proxy authentication takes place whenever a new TCP session must be spun up, commonly to request files or info from the server, or to supply info. For example, you may see proxy authentication around HTTP GET or HTTP POST requests. If you want to see the frames where you are authenticating requests in your trace, add the 'NTLMSSP Summary' column to Netmon and filter for  `.property.NTLMSSPSummary`. To see how long the authentication is taking, add the Time Delta column.</span></span> 

<span data-ttu-id="491da-396">Netmon に列を追加します。</span><span class="sxs-lookup"><span data-stu-id="491da-396">To add a column to Netmon:</span></span> 
1. <span data-ttu-id="491da-397">説明などの列を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="491da-397">Right-click on a column such as Description.</span></span> 
2. <span data-ttu-id="491da-398">列を選択する] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="491da-398">Click Choose Columns.</span></span> 
3. <span data-ttu-id="491da-399">NTLMSSP の概要] および [時刻の差分リストで見つけて追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="491da-399">Locate NTLMSSP Summary and Time Delta in the list and click Add.</span></span> 
4. <span data-ttu-id="491da-400">列を移動、新しい所定の位置にする前に、または [説明] 列の背後にある、サイド バイ サイドを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="491da-400">Move the new columns into place before or behind the Description column so you can read them side-by-side.</span></span>
5. <span data-ttu-id="491da-401">[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="491da-401">Click OK.</span></span> 

<span data-ttu-id="491da-p172">列を追加しない場合でも、ネットワーク モニターのフィルターは機能します。トラブルシューティングはであなたの認証には、どのようなステージを参照してください、ずっと使いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="491da-p172">Even if you don't add the column, the Netmon filter will work. But your troubleshooting will be much easier if you can see what stage of authentication you're in.</span></span> 

<span data-ttu-id="491da-p173">インスタンスのプロキシの認証に NTLM チャレンジ、またはメッセージの認証をすべてのフレームを分析することを確認してを見て、存在します。必要に応じて、トラフィックおよび検索の会話の特定の部分を右クリックし\>TCP です。これらの会話の中にデルタ値を把握します。</span><span class="sxs-lookup"><span data-stu-id="491da-p173">When looking for instances of Proxy Authentication, be sure to study all frames where there is an NTLM Challenge, or an Authenticate Message is present. If necessary, right-click the specific piece of traffic and Find Conversations \> TCP. Be aware of the Time Delta values in these Conversations.</span></span> 

![Netmon トレース表示プロキシの認証、対話形式でフィルターを適用します。](media/b640f176-0a52-4bbb-972e-60fb3d6aece2.PNG)        

<span data-ttu-id="491da-p174">Wireshark に示すように、4 秒の遅延はプロキシへの認証。**表示される前のフレームから時間デルタ**] 列は、フレームの詳細にある同じ名前のフィールドを右クリックし、列として追加を選択することによって行われました。</span><span class="sxs-lookup"><span data-stu-id="491da-p174">A four second delay in proxy authentication as seen in Wireshark. The **Time delta from previous displayed frame** column was made via right-clicking the field of the same name in the frame details and selecting Add as Column.  </span></span><br/> <span data-ttu-id="491da-410">![Wireshark でフレームの詳細にある同じ名前のフィールドを右クリックし、列として追加を選択することで '時間差分で前のフレームが表示されている' の列を作成できます。](media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)</span><span class="sxs-lookup"><span data-stu-id="491da-410">![In Wireshark, the 'Time delta from previous displayed frame' column can be made via right-clicking the field of the same name in the frame details and selecting Add as Column.](media/f5b7bde4-8067-4ee0-bc7f-e9062ce1ba6f.PNG)</span></span>        

### <a name="dns-performance"></a><span data-ttu-id="491da-411">DNS のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="491da-411">DNS Performance</span></span>

<span data-ttu-id="491da-412">最適な名前解決し、最速とその実行可能なクライアントの国にします。</span><span class="sxs-lookup"><span data-stu-id="491da-412">Name resolution works best and most quickly when it takes place as close to the client's country as possible.</span></span> 

<span data-ttu-id="491da-p175">DNS 名前解決が行われて海外ではページの読み込みに秒を追加できます。理想的には、100 ミリ秒未満で名前解決が行われます。行う必要がない場合は、調査をさらにします。</span><span class="sxs-lookup"><span data-stu-id="491da-p175">If DNS name resolution is taking place overseas, it can add seconds to page loads. Ideally, name resolution happens in under 100ms. If not, you should do further investigation.</span></span> 

> [!TIP]
> <span data-ttu-id="491da-p176">Office 365 で動作するクライアントの接続方法はわからないでしょうか。クライアント接続の参照ドキュメントを見て[ここでは](https://technet.microsoft.com/en-us/library/dn741250.aspx)。</span><span class="sxs-lookup"><span data-stu-id="491da-p176">Not sure how Client Connectivity works in Office 365? Take a look at the Client Connectivity Reference document [here](https://technet.microsoft.com/en-us/library/dn741250.aspx).</span></span>           

#### <a name="tools"></a><span data-ttu-id="491da-418">ツール:</span><span class="sxs-lookup"><span data-stu-id="491da-418">Tools:</span></span> 

- <span data-ttu-id="491da-419">ネットワーク モニター</span><span class="sxs-lookup"><span data-stu-id="491da-419">Netmon</span></span>
- <span data-ttu-id="491da-420">Wireshark</span><span class="sxs-lookup"><span data-stu-id="491da-420">Wireshark</span></span>
- <span data-ttu-id="491da-421">PsPing</span><span class="sxs-lookup"><span data-stu-id="491da-421">PsPing</span></span>

#### <a name="what-to-look-for"></a><span data-ttu-id="491da-422">何を検索するには。</span><span class="sxs-lookup"><span data-stu-id="491da-422">What to look for:</span></span>
<span data-ttu-id="491da-p177">ネットワーク トレースは通常、別のジョブは、DNS のパフォーマンスを分析します。しかし、PsPing も、または、考えられる原因を取り除くことに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="491da-p177">Analyzing DNS performance is typically another job for a network trace. However, PsPing is also helpful in ruling in, or out, a possible cause.</span></span> 

<span data-ttu-id="491da-p178">DNS トラフィックが TCP と UDP の要求に基づいて、その特定の応答に特定の要求に一致するように役立つ ID を使用して応答することが明白です。DNS が表示されますと、たとえば、SharePoint Online を使用して、ネットワーク名または URL web ページ上のトラフィックします。として一般に、ゾーンを転送するときにドキュメントを除くため、ネットワーク トラフィックの大部分は、UDP 経由で実行されます。</span><span class="sxs-lookup"><span data-stu-id="491da-p178">DNS traffic is based on TCP and UDP requests and responses are clearly marked with an ID that will help to match a specific request with its specific response. You'll see DNS traffic when, for example, SharePoint Online uses a network name or URL on a web page. As a rule of thumb, most of this traffic, excepting when transferring Zones, runs over UDP.</span></span> 

<span data-ttu-id="491da-p179">ネットワーク モニターと Wireshark、DNS トラフィックを確認することが最も基本的なフィルターは単に`dns`。フィルターを指定するときに、小文字を使用することを確認します。クライアント コンピューターに問題を再現する開始する前に、DNS リゾルバー キャッシュをフラッシュすることを忘れないでください。などのホーム ページの低速の SharePoint Online ページ読み込みの場合は、すべてのブラウザーを閉じて、新しいブラウザーを開いて、トレースを開始、DNS のリゾルバー キャッシュをフラッシュしてくださいに SharePoint Online サイトを参照します。ページ全体が解決した後、停止し、トレースを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="491da-p179">In both Netmon and Wireshark, the most basic filter that will let you look at DNS traffic is simply  `dns`. Be sure to use lower case when specifying the filter. Remember to flush your DNS resolver cache before you begin to reproduce the issue on your client computer. For example, if you have a slow SharePoint Online page load for the Home page, you should close all browsers, open a new browser, start tracing, flush your DNS resolver cache, and browse to your SharePoint Online site. Once the entire page resolves, you should stop and save the trace.</span></span>

![Netmon の DNS の基本フィルターは DNS です。](media/1bebc118-ca13-45f3-803f-ab73e7af401d.png)

<span data-ttu-id="491da-p180">オフセットをここでは時刻を確認するには。することができるように、次の手順を実行してネットワーク モニター**時間デルタ**] 列を追加するのには役に立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="491da-p180">You want to look at the time offset here. And it may be helpful to add the **Time Delta** column to Netmon which you can do by completing these steps:</span></span> 
1. <span data-ttu-id="491da-436">説明などの列を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="491da-436">Right-click on a column such as Description.</span></span> 
2. <span data-ttu-id="491da-437">列を選択する] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="491da-437">Click Choose Columns.</span></span> 
3. <span data-ttu-id="491da-438">一覧で時間デルタを見つけて、[追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="491da-438">Locate Time Delta in the list and click Add.</span></span> 
4. <span data-ttu-id="491da-439">新しい列に移動します場所の前に、または [説明] 列の背後にある、サイド バイ サイドを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="491da-439">Move the new column into place before or behind the Description column so you can read them side-by-side.</span></span>
5. <span data-ttu-id="491da-440">[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="491da-440">Click OK.</span></span> 

<span data-ttu-id="491da-p181">目的のクエリを検索する場合は、フレームの詳細パネルで、**会話の検索**を選択するには、そのクエリを右クリックし、それを分離することを検討してください\> **DNS**です。ネットワーク会話パネルが UDP トラフィックの特定の会話をログに記録する権利をジャンプすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="491da-p181">If you find a query of interest, consider isolating it by right-clicking that query in the frame details panel, choosing **Find Conversations** \> **DNS**. Notice that the Network Conversations panel jumps right to the specific conversation in its log of UDP traffic.</span></span> 

![Outlook のオンラインの負荷が DNS を使用するとフィルターのネットワーク モニターのトレースでは、結果を絞り込むには、会話、DNS を検索します。](media/763cf20e-7b48-4a37-9449-c9978cfe118b.PNG)        

<span data-ttu-id="491da-p182">Wireshark では、DNS に列を行うことができます。トレースを実行する (またはトレースを開く) Wireshark とフィルターで`dns`、または複数の確認、 `dns.time`。任意の DNS クエリをクリックし、[詳細を表示するパネルを展開、`Domain Name System (response)`の詳細です。時刻のフィールドが表示されます (たとえば、 ` [Time: 0.001111100 seconds] `。この時間を右クリックし、**列に適用**] を選択します。こう**時間**] 列には、トレースの並べ替えを高速にします。DNS 呼び出しを確認するための値を降順で並べ替えるには、新しい列をクリックしては、解決するために最も時間かかりました。</span><span class="sxs-lookup"><span data-stu-id="491da-p182">In Wireshark you can make a column for DNS time. Take your trace (or open a trace) in Wireshark and filter by  `dns`, or, more helpfully,  `dns.time`. Click on any DNS query, and, in the panel showing details, expand the  `Domain Name System (response)` details. You'll see a field for time (for example,  ` [Time: 0.001111100 seconds] `. Right-click this time and select **Apply as Column**. This will give you a **Time** column for quicker sorting of your trace. Click on the new column to sort by descending values to see which DNS call took the longest to resolve.</span></span> 

[<span data-ttu-id="491da-451">Wireshark で (小文字の) dns.time でフィルター処理し、詳細からの時間を列にして昇順で並べ替えた、SharePoint Online の参照。</span><span class="sxs-lookup"><span data-stu-id="491da-451">A browse of SharePoint Online filtered in Wireshark by (lowercase) dns.time, with the time from the details made into a column and sorted ascending.</span></span>](media/1439dcc2-12ff-4ee2-9ef3-1484cf79c384.PNG)

<span data-ttu-id="491da-p183">DNS 解決の時間をさらに調査を行う場合は、TCP によって使用される DNS ポートに対して、PsPing を実行してください (たとえば、 `psping <IP address of DNS server>:53`)。パフォーマンス上の問題が引き続き発生するか場合は、問題が解決を行うにヒットしている DNS のアプリケーション固有の問題よりも広範なネットワークを発行する可能性が高い。意味がも、もう一度、こと outlook.office365.com への ping が表示されます、Outlook のオンラインの DNS 名前解決が行われる (たとえば、outlook の namnorthwest.office365.com)。</span><span class="sxs-lookup"><span data-stu-id="491da-p183">If you would like to do more investigation of the DNS resolution time, try a PsPing against the DNS port used by TCP (for example,  `psping <IP address of DNS server>:53`) . Do you still see a performance issue? If you do, then the problem is more likely to be a broader network issue than an issue of specific the DNS application you're hitting to do resolution. It's also worth mentioning, again, that a ping to outlook.office365.com will tell you where DNS name resolution for Outlook Online is taking place (for example, outlook-namnorthwest.office365.com).  </span></span><br/> <span data-ttu-id="491da-456">問題特定の DNS を使用する場合は、DNS の構成とさらにこの問題を調査するように DNS フォワーダーを検討する IT 部門に連絡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="491da-456">If the issue looks to be DNS specific, it may be necessary to contact your IT department to look at DNS configurations and DNS Forwarders to further investigate this issue.</span></span> 

### <a name="proxy-scalability"></a><span data-ttu-id="491da-457">プロキシのスケーラビリティ</span><span class="sxs-lookup"><span data-stu-id="491da-457">Proxy Scalability</span></span>

<span data-ttu-id="491da-p184">Outlook でオンラインに Office 365 のようなサービスは、複数の長期的な接続をクライアントに付与します。したがって、各ユーザーは、寿命の延長を必要とするより多くの接続を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="491da-p184">Services like Outlook Online in Office 365 grant clients multiple long-term connections. Therefore, each user may use more connections that require a longer life.</span></span>  

> [!TIP]
> <span data-ttu-id="491da-p185">多くのユーザーを Office 365 に追加しようとしているために、帯域幅の使用を計画する必要がありますか。[Office 365 のインターネット帯域幅の使用を計画](https://technet.microsoft.com/en-us/library/hh852542.aspx)してください。ある帯域幅の計算機があります。</span><span class="sxs-lookup"><span data-stu-id="491da-p185">Need to plan for bandwidth use because you're about to add a lot users to Office 365? Try [Plan for Internet bandwidth usage for Office 365](https://technet.microsoft.com/en-us/library/hh852542.aspx). There are bandwidth calculators available there.</span></span>

#### <a name="tool"></a><span data-ttu-id="491da-463">ツール:</span><span class="sxs-lookup"><span data-stu-id="491da-463">Tool:</span></span>
 
<span data-ttu-id="491da-464">数値演算</span><span class="sxs-lookup"><span data-stu-id="491da-464">Math</span></span>  

#### <a name="what-to-look-for"></a><span data-ttu-id="491da-465">何を検索するには。</span><span class="sxs-lookup"><span data-stu-id="491da-465">What to look for:</span></span> 

<span data-ttu-id="491da-p186">ネットワーク トレースまたはトラブルシューティングのツールに固有です。代わりに、制限事項とその他の変数を指定した帯域幅の計算に基づいています。</span><span class="sxs-lookup"><span data-stu-id="491da-p186">There is no network trace or troubleshooting tool specific to this. Instead, it's based upon bandwidth calculations given limitations and other variables.</span></span>  

### <a name="tcp-max-segment-size"></a><span data-ttu-id="491da-468">TCP 最大セグメント サイズ</span><span class="sxs-lookup"><span data-stu-id="491da-468">TCP Max Segment Size</span></span>

<span data-ttu-id="491da-p187">-SYN SYN と確認でください。 TCP パケットが使用可能なデータの最大量を実行するために構成されていることを確認するのには作成した、パフォーマンスのネットワーク トレースでは、このチェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="491da-p187">Found in the SYN - SYN/ACK.  Do this check in any performance network trace you've taken to ensure that TCP packets are configured to carry the maximum amount of data possible.</span></span> 

<span data-ttu-id="491da-p188">目標では、データを送信するため、1,460 バイトの MSS を参照してください。あなたは、プロキシの背後にあるか、NAT を使用している場合は、クライアントが NAT またはプロキシ/出口とプロキシ/出口と NAT Office 365 に最適な結果を得るのためにこのテストを実行することを忘れないでください!これらは、別の TCP セッションです。</span><span class="sxs-lookup"><span data-stu-id="491da-p188">The goal is to see a MSS of 1460 bytes for transmission of data. If you're behind a proxy, or you are using a NAT, remember to run this test from client to proxy/egress/NAT, and from proxy/egress/NAT to Office 365 for best results! These are different TCP sessions.</span></span>

#### <a name="tool"></a><span data-ttu-id="491da-474">ツール:</span><span class="sxs-lookup"><span data-stu-id="491da-474">Tool:</span></span> 

<span data-ttu-id="491da-475">ネットワーク モニター</span><span class="sxs-lookup"><span data-stu-id="491da-475">Netmon</span></span>

#### <a name="what-to-look-for"></a><span data-ttu-id="491da-476">何を検索するには。</span><span class="sxs-lookup"><span data-stu-id="491da-476">What to look for:</span></span>

<span data-ttu-id="491da-p189">TCP 最大セグメント サイズ (MSS) は、SYN の SYN と ACK パケットに必要なデータが見つかることを意味する、ネットワーク トレースに 3 ウェイ ハンドシェイクのもう 1 つのパラメーターです。MSS を参照してくださいするのには実に簡単です。</span><span class="sxs-lookup"><span data-stu-id="491da-p189">TCP Max Segment Size (MSS) is another parameter of the three-way handshake in your network trace, that means you'll find the data you need in the SYN - SYN/ACK packet. MSS is actually pretty simple to see.</span></span> 

<span data-ttu-id="491da-479">パフォーマンスのネットワーク トレースを知り、接続を検索しているを開くか、パフォーマンスの問題を示しています。</span><span class="sxs-lookup"><span data-stu-id="491da-479">Open any performance network trace you have and find the connection you're curious about, or that demonstrates the performance problem.</span></span> 

> [!NOTE]
> <span data-ttu-id="491da-p190">トレースを見ているし、会話に関連するトラフィックを検索する必要がありますが、クライアントの ip アドレスまたはプロキシ サーバーまたは出口のポイント、またはその両方の ip アドレスでフィルター処理します。直接か、によって、トレース、およびフィルターでは、Office 365 の IP アドレスをテストしている URL に ping を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="491da-p190">If you are looking at a trace and need to find the traffic relevant to your conversation, filter by the IP of the Client, or the IP of the proxy server or egress point, or both. Going directly, you will need to ping the URL that you're testing for the IP address of Office 365 in the trace, and filter by it.</span></span> 

<span data-ttu-id="491da-p191">中古のトレースを検索しますか。自分の方向を設定するのにはフィルターを使用してください。ネットワーク モニターに次のように、URL に基づく検索を実行する`Containsbin(framedata, ascii, "sphybridExample")`、フレーム番号を書き留めます。</span><span class="sxs-lookup"><span data-stu-id="491da-p191">Looking at the trace second-hand? Try using filters to orient yourself. In Netmon, run a search based on the URL, such as  `Containsbin(framedata, ascii, "sphybridExample")`, take note of the frame number.</span></span> 

<span data-ttu-id="491da-p192">Wireshark でを使用して、次のように`frame contains "sphybridExample"`。(に表示されることとして、[PSH、ACK] Wireshark で) リモート Winsock (RWS) トラフィックを見つけたことを確認する場合は、RWS が接続できないことを注意してください説明したように関連する SYN の SYN と Ack、直前に表示されます。</span><span class="sxs-lookup"><span data-stu-id="491da-p192">In Wireshark use something like  `frame contains "sphybridExample"`. If you notice that you've found Remote Winsock (RWS) traffic (it may appear as a [PSH, ACK] in Wireshark), remember that RWS connects can be seen shortly before relevant SYN - SYN/ACKs, as discussed earlier.</span></span> 

<span data-ttu-id="491da-487">この時点ですることができますフレーム番号を記録して、フィルターを削除に最も近い SYN. を見て、ネットワーク モニターでネットワークの会話ウィンドウ内のすべてのトラフィック] をクリックして</span><span class="sxs-lookup"><span data-stu-id="491da-487">At this point, you can record the frame number, drop the filter, click All Traffic in the Network Conversations window in Netmon to look at the nearest SYN.</span></span> 

<span data-ttu-id="491da-488">重要なは、トレースの時に、IP アドレスの情報のいずれかを受信していない場合、URL の中の検索トレース (の一部では`sphybridExample-my.sharepoint.com`、たとえば)、によってフィルターを適用する IP アドレスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="491da-488">Importantly, if you didn't receive any of the IP address information at the time of the trace, finding your URL in the trace (part of `sphybridExample-my.sharepoint.com`, for example), will give you IP addresses to filter by.</span></span> 

<span data-ttu-id="491da-p193">興味を持ち始めているトレースの接続を検索します。いずれかが IP アドレス、ネットワーク モニターでネットワークの会話ウィンドウを使用して特定の会話 Id を選択して、フィルタ リングによって、トレースをスキャンすることによってこれを行うことができます。SYN パケットが決まったら、[TCP (Netmon) または (Wireshark) で、[フレームの詳細] パネルでの伝送制御プロトコルを展開します。TCP オプションと MaxSegementSize を展開します。関連の SYN ACK フレームと TCP オプションの展開と MaxSegmentSize を検索します。2 つの値の小さい方を最大セグメント サイズとなります。この図での TCP のトラブルシューティングを行うと呼ばれるネットワーク モニターでは、組み込みの列を使用します。</span><span class="sxs-lookup"><span data-stu-id="491da-p193">Locate the connection in the trace that you're interested in seeing. You may do this by either scanning the trace, by filtering by IP addresses, or by selecting specific Conversation IDs using the Network Conversations window in Netmon. Once you've found the SYN packet, expand TCP (in Netmon), or Transmission Control Protocol (in Wireshark) in the Frame Details panel. Expand TCP Options and MaxSegementSize. Locate the related SYN-ACK frame and Expand TCP Options and MaxSegmentSize. The smaller of the two values will be your Maximum Segment Size. In this picture, I make use of the built-in Column in Netmon called TCP Troubleshoot.</span></span>  

![ネットワーク トレースの組み込みの列を使用してネットワーク モニターでフィルター処理します。](media/e073df13-71f8-497a-83b4-bb9f70bd9833.PNG)

<span data-ttu-id="491da-p194">組み込みの列では、**フレームの詳細**] パネルの上部にあります。(、標準表示に切り替えるには、列をもう一度クリックしてタイム ゾーンを選択し。)</span><span class="sxs-lookup"><span data-stu-id="491da-p194">The built-in column is at the top of the **Frame Details** panel. (To switch back to your normal view, click Columns again, and then choose Time Zone.)</span></span> 

<span data-ttu-id="491da-499">![TCP トラブルシューティング オプション (フレームの概要の最上部) の [列] ドロップダウンの場所。](media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)         </span><span class="sxs-lookup"><span data-stu-id="491da-499">![Where to find the Columns drop down for the TCP Troubleshoot option (on top of the Frame Summary).](media/64fd4baa-a872-4f07-b959-752d7d37fd62.PNG)         </span></span>  
<span data-ttu-id="491da-p195">Wireshark でフィルター処理されたトレースは、ここで。MSS の値に固有のフィルターが ( `tcp.options.mss`)。SYN、SYN と ACK、ACK ハンドシェイクのフレームは、フレームの詳細と同等の Wireshark の下部にあるリンク (そのためフレームの ACK が 47、46 SYN-ACK へのリンク、43 の SYN へのリンク) このような作業を容易にします。</span><span class="sxs-lookup"><span data-stu-id="491da-p195">Here's a filtered trace in Wireshark. There is a filter specific to the MSS value ( `tcp.options.mss`). The frames of a SYN, SYN/ACK, ACK handshake are linked at the bottom of the Wireshark equivalent to Frame Details (so frame 47 ACK, links to 46 SYN/ACK, links to 43 SYN) to make this kind of work easier.</span></span> 

![Tcp.options.mss で最大セグメント サイズ (MSS) の Wireshark でフィルターをトレースします。](media/51e278db-801b-48bc-9b68-87cf92f03fd6.PNG)         
<span data-ttu-id="491da-504">選択的確認応答を確認する必要がある場合 (この行列の次のトピック) をトレースを終了しないでください。</span><span class="sxs-lookup"><span data-stu-id="491da-504">If you need to check Selective Acknowledgment (next topic in this matrix), don't close your trace!</span></span>

### <a name="selective-acknowledgment"></a><span data-ttu-id="491da-505">選択的確認応答</span><span class="sxs-lookup"><span data-stu-id="491da-505">Selective Acknowledgment</span></span>

<span data-ttu-id="491da-p196">SYN と SYN/確認オプションを選択受信確認 (SACK) の両方のアクセス許可では、データ パケットの再送を滑らかにするか不足しているパケットに SYN の記載を報告する SYN と確認する必要があります。デバイスでは、パフォーマンス上の問題につながることが、この機能を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="491da-p196">Found in the SYN - SYN/ACK. Must be reported as Permitted in both SYN and SYN/ACK. Selective Acknowledgment (SACK) allows for smoother retransmission of data when a packet or packets go missing. Devices can disable this feature, which can lead to performance problems.</span></span> 

<span data-ttu-id="491da-p197">あなたは、プロキシの背後にあるか、NAT を使用している場合は、クライアントが NAT またはプロキシ/出口とプロキシ/出口と NAT Office 365 に最適な結果を得るのためにこのテストを実行することを忘れないでください!これらは、別の TCP セッションです。</span><span class="sxs-lookup"><span data-stu-id="491da-p197">If you're behind a proxy, or you are using a NAT, remember to run this test from client to proxy/egress/NAT, and from proxy/egress/NAT to Office 365 for best results! These are different TCP sessions.</span></span>

#### <a name="tool"></a><span data-ttu-id="491da-512">ツール:</span><span class="sxs-lookup"><span data-stu-id="491da-512">Tool:</span></span> 

<span data-ttu-id="491da-513">ネットワーク モニター</span><span class="sxs-lookup"><span data-stu-id="491da-513">Netmon</span></span> 

#### <a name="what-to-look-for"></a><span data-ttu-id="491da-514">何を検索するには。</span><span class="sxs-lookup"><span data-stu-id="491da-514">What to look for:</span></span>

<span data-ttu-id="491da-p198">選択的受信確認 (SACK) とは、SYN-ACK SYN ハンドシェイクでもう 1 つのパラメーターです。SYN の SYN と ACK のさまざまな方法は、トレースをフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="491da-p198">Selective Acknowledgment (SACK) is another parameter in the SYN-SYN/ACK handshake. You can filter your trace for SYN - SYN/ACK many ways.</span></span> 

<span data-ttu-id="491da-p199">興味のいずれかのトレースをスキャンすることで表示される IP アドレス、ネットワーク モニターでネットワークの会話ウィンドウを使用して、会話 ID をクリックして、フィルター処理されるトレース内で、接続を探します。SYN パケットを見つけたら、まずは、ネットワーク モニターで TCP またはフレームの詳細セクションで Wireshark での伝送制御プロトコルを展開します。TCP オプション] を展開し、SACK。関連する SYN ACK フレームおよび TCP オプションの展開とその SACK フィールドを検索します。SACK が SYN と SYN/確認の両方で許可されていることを確認します。ネットワーク モニターと Wireshark の両方に示すように、SACK の値をここでは。</span><span class="sxs-lookup"><span data-stu-id="491da-p199">Locate the connection in the trace that you're interested in seeing either by scanning the trace, filtering by IP addresses, or by clicking a Conversation ID using the Network Conversations window in Netmon. Once you've found the SYN packet, expand TCP in Netmon, or Transmission Control Protocol in Wireshark in the Frame Details section. Expand TCP Options and then SACK. Locate the related SYN-ACK frame and Expand TCP Options and its SACK field. Make certain SACK is permitted in both SYN and SYN/ACK. Here are SACK values as seen in both Netmon and Wireshark.</span></span>

![ネットワーク モニターで選択的な受信確認 (SACK) 結果として tcp.flags.syn の 1 を = =。](media/216f556f-5031-4ed2-b066-a0d9b3251fa2.PNG)           <br/> ![Wireshark に表示されるとおり、tcp.flags.syn == 1 でフィルター処理された SACK。](media/0a6e26e5-43dc-403b-adc9-3349a55f4e4b.PNG)        

### <a name="dns-geolocation"></a><span data-ttu-id="491da-525">DNS の地理位置情報</span><span class="sxs-lookup"><span data-stu-id="491da-525">DNS Geolocation</span></span> 

<span data-ttu-id="491da-526">世界では、Office 365 が解決を試みますが、DNS は、接続速度の効果を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="491da-526">Where in the world Office 365 tries to resolve your DNS call effects your connection speed.</span></span> 

<span data-ttu-id="491da-p200">オンラインの Outlook の [最初の DNS 検索が完了したら、その DNS の場所は、最も近いデータ センターへの接続に使用されます。データが保存されているデータ センター (dC) に接続するためのバックボーン ネットワークを使用する Outlook のオンライン CA サーバーに接続されます。これは高速です。</span><span class="sxs-lookup"><span data-stu-id="491da-p200">In Outlook Online, after the first DNS lookup is completed, the location of that DNS will be used to connect to your nearest datacenter. You will be connected to an Outlook Online CAS server, which will use the backbone network to connect to the datacenter (dC) where your data is stored. This is faster.</span></span>

<span data-ttu-id="491da-530">本拠地での SharePoint Online を海外出張中のユーザーへのアクセスが表示されます、作業中のデータ センター - 場所は、SPO テナントに基づいてドメイン コント ローラーは、(そのため、アメリカ合衆国の dC 場合アメリカ合衆国ベースの場合、ユーザー)。</span><span class="sxs-lookup"><span data-stu-id="491da-530">When accessing SharePoint Online, a user traveling abroad will be directed to their active datacenter -- that's the dC whose location is based on their SPO tenant's home-base (so, a dC in the USA if the user if USA-based).</span></span>  <br/>  <span data-ttu-id="491da-p201">Lync オンライン時に、2 つ以上の dC でのアクティブ ノードには。要求は、Lync オンラインの場合、マイクロソフトのために送信 DNS は、世界中の要求の送信元、決定し、Lync オンラインは、アクティブな場所最も近い地域の dC からの IP アドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="491da-p201">Lync online has active nodes in more than one dC at a time. When requests are sent for Lync online instances, Microsoft's DNS will determine where in the world the request came from, and return IP addresses from the nearest regional dC where Lync online is active.</span></span> 

> [!TIP]
> <span data-ttu-id="491da-p202">クライアントが Office 365 に接続する方法の詳細を知る必要があるでしょうか。[クライアント接続](https://technet.microsoft.com/en-us/library/dn741250.aspx)の参照資料 (とその役に立つ画像) を見てください。</span><span class="sxs-lookup"><span data-stu-id="491da-p202">Need to know more about how clients connect to Office 365? Take a look at the [Client Connectivity](https://technet.microsoft.com/en-us/library/dn741250.aspx) reference article (and its helpful graphics).</span></span>           
#### <a name="tools"></a><span data-ttu-id="491da-535">ツール:</span><span class="sxs-lookup"><span data-stu-id="491da-535">Tools:</span></span>

- <span data-ttu-id="491da-536">Ping</span><span class="sxs-lookup"><span data-stu-id="491da-536">Ping</span></span>
- <span data-ttu-id="491da-537">PsPing</span><span class="sxs-lookup"><span data-stu-id="491da-537">PsPing</span></span>

#### <a name="what-to-look-for"></a><span data-ttu-id="491da-538">何を検索するには。</span><span class="sxs-lookup"><span data-stu-id="491da-538">What to look for:</span></span>

<span data-ttu-id="491da-p203">Microsoft の DNS サーバーにクライアントの DNS サーバーから名前解決の要求は、Microsoft DNS の地域データ センター (dC) の IP アドレスを返すことでほとんどの場合の結果にする必要があります。どういうことするのでしょうか。本社は、インドのバンガロールに、お使いのブラウザーは、Outlook をオンラインで要求を行う場合、米国で移動している場合は、Microsoft の DNS サーバーする必要がある IP アドレスに渡す--米国の地域のデータ センターでのデータ センター。Outlook からメールが必要な場合そのデータ転送のクイックのバックボーン ネットワーク経由でデータ センター間で。</span><span class="sxs-lookup"><span data-stu-id="491da-p203">Requests for name resolution from the client's DNS servers to Microsoft's DNS servers should in most cases result in Microsoft DNS returning the IP address of a regional datacenter (dC). What does this mean for you? If your headquarters are in Bangalore, India, but you are traveling in the United States, when your browser makes a request for Outlook Online, Microsoft's DNS servers should hand you IP addresses to datacenters in the United States -- a regional datacenter. If mail is needed from Outlook, that data will travel across Microsoft's quick backbone network between the datacenters.</span></span>

<span data-ttu-id="491da-p204">DNS は、できるだけユーザーの場所に名前解決が行われるときに最も機能します。ヨーロッパの場合はするには、ヨーロッパでは、Microsoft DNS (理想的に)、ヨーロッパのデータ センターを扱います。DNS およびアメリカのデータ センターにヨーロッパのクライアントからのパフォーマンスは遅くなります。</span><span class="sxs-lookup"><span data-stu-id="491da-p204">DNS works fastest when name resolution is done as close to the user location as possible. If you're in Europe, you want to go to a Microsoft DNS in Europe, and (ideally) deal with a datacenter in Europe. Performance from a client in Europe going to DNS and a datacenter in America will be slower.</span></span>

<span data-ttu-id="491da-p205">か、世界では、DNS 要求がルーティングされているかを確認するのには outlook.office365.com に対して Ping ツールを実行します。ヨーロッパの場合は、outlook emeawest.office365.com のようなものからの応答を参照してくださいする必要があります。南北アメリカでは、outlook namnorthwest.office365.com のようなものを期待します。</span><span class="sxs-lookup"><span data-stu-id="491da-p205">Run the Ping tool against outlook.office365.com to determine where in the world your DNS request is being routed. If you are in Europe, you should see a reply from something like outlook-emeawest.office365.com. In the Americas, expect something like outlook-namnorthwest.office365.com.</span></span> 

<span data-ttu-id="491da-p206">クライアント コンピューターでコマンド プロンプトを開きます (スタートを使用して\>を実行\>cmd または Windows キー \> cmd と入力します)。Ping outlook.office365.com を入力し、ENTER キーを押します。、を IPv4 経由で ping を実行することを指定する場合は、-4 を指定してください。ICMP パケットからの応答の取得に失敗する可能性がありますが、要求のルーティングに DNS の名前を表示する必要があります。参照する場合は、この接続のレーテンシー値 ping によって返されるサーバーの IP アドレスを PsPing してみてください。</span><span class="sxs-lookup"><span data-stu-id="491da-p206">Open the command prompt on the client computer (via Start \> Run \> cmd or Windows key \> type cmd). Type ping outlook.office365.com and press ENTER. Remember, to specify -4 if you want to specify to ping via IPv4. You may fail to get a reply from the ICMP packets, but you should see the name of the DNS to which the request was routed. If you want to see the latency numbers for this connection try PsPing to the IP address of the server that is returned by ping.</span></span>  

![outlook-namnorthwest の解決を示す、outlook.office365.com に対する Ping。](media/06c944d5-6159-43ec-aa31-757770695e8b.PNG)           
![28 ミリ秒の平均待機時間を表示する outlook.office365.com に、ping によって返される IP アドレスを PSPing。](media/f2b25a75-1a87-4479-b8a7-fa4375683507.PNG)           
### <a name="office-365-application-troubleshooting"></a><span data-ttu-id="491da-556">Office 365 アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="491da-556">Office 365 Application Troubleshooting</span></span>

#### <a name="tools"></a><span data-ttu-id="491da-557">ツール:</span><span class="sxs-lookup"><span data-stu-id="491da-557">Tools:</span></span> 

- <span data-ttu-id="491da-558">ネットワーク モニター</span><span class="sxs-lookup"><span data-stu-id="491da-558">Netmon</span></span>
- <span data-ttu-id="491da-559">HTTPWatch</span><span class="sxs-lookup"><span data-stu-id="491da-559">HTTPWatch</span></span>
- <span data-ttu-id="491da-560">ブラウザーでコンソールを f12 キーを押す</span><span class="sxs-lookup"><span data-stu-id="491da-560">F12 Console in the browser</span></span>

<span data-ttu-id="491da-p207">説明されていないネットワークに固有の「アプリケーション固有トラブルシューティングに使用するツールです。リソースを検索しますが、[このページで](https://support.office.com/en-us/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848)使用*できます*。</span><span class="sxs-lookup"><span data-stu-id="491da-p207">We don't cover tools used in application-specific troubleshooting in this network-specific article. But you'll find resources you  *can*  use [on this page](https://support.office.com/en-us/article/Network-planning-and-performance-tuning-for-Office-365-e5f1228c-da3c-4654-bf16-d163daee8848).</span></span>
   
## <a name="related-topics"></a><span data-ttu-id="491da-563">関連項目</span><span class="sxs-lookup"><span data-stu-id="491da-563">Related Topics</span></span>

[<span data-ttu-id="491da-564">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="491da-564">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="491da-565">Office 365 エンドポイントの FAQ</span><span class="sxs-lookup"><span data-stu-id="491da-565">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  

