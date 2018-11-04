---
title: 低速のネットワーク上の Office 365 の使用に関するベスト プラクティス
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: End User
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MET150
- MOP150
- MEW150
- BCS160
ms.assetid: fd16c8d2-4799-4c39-8fd7-045f06640166
description: できれば便利な場合は、インターネット接続が高速では常に上下のないでしょうか。おそらくその日が来ることはできます。その間、実用的なものの balky ネットワークを回避するにしても日常的な作業を行うことができます。
ms.openlocfilehash: 2287de562672f5ceb1ab32949168e8dfdeb31585
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933144"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a><span data-ttu-id="774e1-105">低速のネットワーク上の Office 365 の使用に関するベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="774e1-105">Best practices for using Office 365 on a slow network</span></span>

<span data-ttu-id="774e1-p102">できれば便利な場合は、インターネット接続が高速では常に上下のないでしょうか。おそらくその日が来ることはできます。その間、実用的なものの balky ネットワークを回避するにしても日常的な作業を行うことができます。Office 365 では、クラウド ベースのサービスですが、コンテンツをオフラインで作業してスムーズに、変更内容の同期を維持するのには、さまざまな方法も提供します。だけでなくになることが多くといって、アプリケーションがより速く実行し、ユーザー インターフェイスは応答性の高いコンテンツをオフラインで作業を効率化します。点は、この: Office 365 は、双方のメリットを提供します。利用する方法をここでは。</span><span class="sxs-lookup"><span data-stu-id="774e1-p102">Wouldn't it be nice if your Internet connection was always fast and never down? Perhaps that day will come. But in the meantime, there are practical things you can do to work around a balky network and still get your day-to-day work done. Although Office 365 is a cloud-based service, it also provides many ways to work with your content offline and to smoothly keep your changes synchronized. Besides, it's sometimes more efficient to work with content offline just because applications run faster and the user interface is more responsive. The point is this: Office 365 gives you the best of both worlds. Here's how to take advantage of that.</span></span> 
  
> [!TIP]
> <span data-ttu-id="774e1-p103">ネットワーク接続が低速方法 (高速) を表示しますか。[OOKLA の速度をテスト](https://www.speedtest.net/)するか、[ネットワークの速度をテスト アプリケーション](https://www.windowsphone.com/en-us/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70)を実行してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-p103">Want to see how slow (or fast) your network connection is? Try the [ OOKLA Speed test ](https://www.speedtest.net/) or the [Network Speed Test App](https://www.windowsphone.com/en-us/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70).</span></span> 
     
## <a name="why-is-my-network-so-slow"></a><span data-ttu-id="774e1-115">ネットワークが遅いはなぜですか。</span><span class="sxs-lookup"><span data-stu-id="774e1-115">Why is my network so slow?</span></span>

<span data-ttu-id="774e1-p104">自体、ネットワークのパフォーマンスを制御する必要はありません、ですが、バック グラウンドで何が起こって理解するに役立ちます。インターネットは非常に複雑ですの方が状況を理解するのに役立ついくつかの概念があります。「ベスト ・ プラクティスに従うと、パフォーマンス問題の回避策を支援し不満を減らすできます。</span><span class="sxs-lookup"><span data-stu-id="774e1-p104">Although you don't have control over network performance itself, it helps to understand what's going on behind the scenes. The Internet is enormously complex, but there are a few concepts that can help you understand the situation much better. Following the best practices in this article can help workaround performance issues and reduce frustration.</span></span>
  
<span data-ttu-id="774e1-119">**ネットワークのパフォーマンスに影響を与える主な要因**</span><span class="sxs-lookup"><span data-stu-id="774e1-119">**Major factors that affect network performance**</span></span>

![ネットワーク パフォーマンス要因](media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)
  
 <span data-ttu-id="774e1-121">**帯域幅とレーテンシー**ネットワークのパフォーマンスの最も重要な 2 つのメジャーは、帯域幅と遅延します。</span><span class="sxs-lookup"><span data-stu-id="774e1-121">**Bandwidth and latency** The two most important measures of network performance are bandwidth and latency:</span></span> 
  
- <span data-ttu-id="774e1-p105">帯域幅は、1 秒あたりのビット数で測定されるスループットの割合です。サイズをお勧めします。水パイプのように、帯域幅です。パイプが大きいほどを"配置から「水辺の方です。</span><span class="sxs-lookup"><span data-stu-id="774e1-p105">Bandwidth is the rate of throughput measured in bits per second. Bigger is better. Bandwidth is like a water pipe. The larger the pipe, the more water that you can "put through" it.</span></span>
    
- <span data-ttu-id="774e1-p106">待ち時間は、デバイスにサーバーまたはサービスから取得するコンテンツを使用しての単位はミリ秒の時間です。高速化をお勧めします。低帯域幅、低密度の接続では、転送時間などの要因によって遅延が起こります。</span><span class="sxs-lookup"><span data-stu-id="774e1-p106">Latency is the time it takes for content to get from a server or service to your device and is measured in milliseconds. Faster is better. Latency can be caused by a number of factors including low bandwidth, a sparse connection, or transmission time.</span></span>
    
 <span data-ttu-id="774e1-p107">**一般的な問題**だけでなく帯域幅と遅延、その他の問題はネットワークのパフォーマンスに影響を与えるし、多くの場合は予測できません。ネットワークのパフォーマンスは、時刻、または、物理的な場所にベースを変動することができます。急上昇自然災害や主要な公開イベントなど、インターネットを使用して特定のイベントが発生すると、ネットワークが目詰まりするとことができます。サイズと読み込まれているページの複雑さおよび数と転送されるファイルのサイズのパフォーマンスに直接影響があります。WiFi 接続が一時的に低下する可能性が: たとえば、全員が同時にツイートを要求することによって何千もの大規模な会議の会議をポーリングします。</span><span class="sxs-lookup"><span data-stu-id="774e1-p107">**Common issues** Besides bandwidth and latency, other issues have an impact on network performance and are often unpredictable. Network performance can fluctuate based on the time of the day or your physical location. The network can become clogged when certain events occur that spike the use of the Internet, such as a natural disaster or a major public event. The size and complexity of the page being loaded and the number and size of files being transferred have a direct bearing on performance. A WiFi connection can temporarily degrade: for example, you poll a large conference meeting of thousands by requesting everyone to tweet at the same time.</span></span> 
  
 <span data-ttu-id="774e1-p108">**衛星ネットワークに関する考慮事項**衛星ネットワークは、地上波ネットワークが現実的でバックの国、クルーズ船、またはリモートの科学領域などではない場合に便利です。これらのネットワークは、衛星の geosynchronous 軌道赤道の上の 22,000 マイルの位置に依存します。ただし、転送は、約 90,000 マイルを実際に移動し、衛星ネットワークが低速の待機時間 (500 ミリ秒以上) を持つための地上波ネットワーク (20 往復)。条件の最適なこの遅延は、気付かない場合がありますが、サイズの大きいファイルをダウンロード、ストリーミング ビデオ、およびゲームのプレイの可能性がありますが。衛星伝送を一時的に中断するにどの重天気予報、雷電など (猛吹雪)、「フェードの雨」別の問題です。</span><span class="sxs-lookup"><span data-stu-id="774e1-p108">**Considerations for a satellite network**A satellite network is useful when a terrestrial network is not feasible, such as the back country, a cruise ship, or a remote scientific area. These networks rely on satellites positioned in a geosynchronous orbit 22,000 miles above the equator. However, a transmission actually travels about 90,000 miles, and so a satellite network has a slower latency (500 ms or more) than a terrestrial network (20 to 50ms). Under the best of conditions, you may not notice this latency, but for downloading large files, streaming videos, and playing games, you probably will. Another issue is "rain fade" in which heavy weather, such as thunderstorms and blizzards, can temporarily interrupt satellite transmission.</span></span>
  
## <a name="are-you-sure-its-the-network"></a><span data-ttu-id="774e1-139">ネットワークであることを確認しているでしょうか。</span><span class="sxs-lookup"><span data-stu-id="774e1-139">Are you sure it's the network?</span></span>

<span data-ttu-id="774e1-p109">パフォーマンスの問題が発生するたびに最初のデバイスが問題の根本的な原因ではないことを確認します。大きな改善を行う可能性があります、行うことができます 2 つのことがあります。</span><span class="sxs-lookup"><span data-stu-id="774e1-p109">Whenever you experience performance problems, first make sure that your device is not the root cause of the problem. There are two things you can do that might make a big improvement:</span></span>
  
- <span data-ttu-id="774e1-142">デバイスを正しく実行し、コンピューター上にマルウェアがないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-142">Make sure your device is running well and there is no malware on your computer.</span></span>
    
- <span data-ttu-id="774e1-p110">可能であればより多くのメモリを購入します。最も簡単なと最も多くの場合は、メモリを追加するデバイスのパフォーマンスを向上させる効果的な方法です。それは、サイズの大きいファイルとビデオを操作する場合に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="774e1-p110">If possible, buy more memory. Adding memory is the simplest and often most effective way to improve performance on your device. It's especially helpful when working with large files and videos.</span></span>
    
<span data-ttu-id="774e1-146">詳細については、 [Windows のパフォーマンスとメンテナンス](https://windows.microsoft.com/en-us/windows/performance-maintenance-help#performance-maintenance-help)、および[システム パフォーマンスの問題を修正する Windows](https://support.microsoft.com/mats/slow_windows_performance/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-146">For more information, see [ Windows Performance and maintenance ](https://windows.microsoft.com/en-us/windows/performance-maintenance-help#performance-maintenance-help) and [Fix Windows system performance problems](https://support.microsoft.com/mats/slow_windows_performance/).</span></span>
   
## <a name="best-practices-for-using-your-browser"></a><span data-ttu-id="774e1-147">お使いのブラウザーを使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="774e1-147">Best practices for using your browser</span></span>

<span data-ttu-id="774e1-148">Office 365 へのゲートウェイをお使いのブラウザーでは、パフォーマンス、特にロードにかかる時間に影響を設定するためのページとラウンドする頻度が作動するオフィスに 365 のサービスです。</span><span class="sxs-lookup"><span data-stu-id="774e1-148">Your browser is your gateway to Office 365, so it can have an impact on performance, especially with the time it takes to load a page and how often you round trip to the Office 365 service.</span></span> 
  
 <span data-ttu-id="774e1-149">**一般的なブラウザー**</span><span class="sxs-lookup"><span data-stu-id="774e1-149">**Browsers in general**</span></span>
  
<span data-ttu-id="774e1-150">一般的なブラウザーのためのいくつかの提案を挙げます。</span><span class="sxs-lookup"><span data-stu-id="774e1-150">Here are some suggestions for browsers in general:</span></span>
  
- <span data-ttu-id="774e1-151">パフォーマンスに影響を及ぼす可能性がありますまたはする必要はありませんが、ブラウザーのアドオンを無効にします。</span><span class="sxs-lookup"><span data-stu-id="774e1-151">Disable browser add-ons that might impact performance or that you don't really need.</span></span>
    
- <span data-ttu-id="774e1-152">インターネット一時ファイルのキャッシュ サイズを増やします。</span><span class="sxs-lookup"><span data-stu-id="774e1-152">Increase the cache size for your temporary internet files.</span></span>
    
-  <span data-ttu-id="774e1-p111">職場、学校のアカウントにサインインしているとはブラウザーのウィンドウを開いた日中のままにします。もう一度サインインしなくても、他のタブやウィンドウを開くことができます。別のアカウントへのサインインが必要な場合は、プライベート ブラウズを使用します。</span><span class="sxs-lookup"><span data-stu-id="774e1-p111">Once you have signed into your work or school account, keep the browser window open throughout the day. You can open other tabs and windows without signing in again. If you need to sign in to another account, use Private Browsing.</span></span> 
    
- <span data-ttu-id="774e1-p112">各ページがダウンロードする開くと、開いたままにするにタブを使用しています。タブ間を移動して、1 日の後でページを使用する簡単です。そのページの最新データが必要な場合にのみ、ページを更新します。</span><span class="sxs-lookup"><span data-stu-id="774e1-p112">Once each page is downloaded and open, keep them open by using tabs. It's easy to navigate between tabs and use the page later on in the day. Refresh a page only if you need the latest data on that page.</span></span>
    
- <span data-ttu-id="774e1-159">ページは時間がかかりすぎてを開く場合は、ページのダウンロード (esc キーを押します) を停止し、(f5 キーを押して) ページを更新します。</span><span class="sxs-lookup"><span data-stu-id="774e1-159">If a page is taking too long to open, stop the page download (press ESC) and then refresh the page (press F5).</span></span> 
    
-  <span data-ttu-id="774e1-p113">可能であれば、Office 365 にラウンド トリップを削減します。たとえば、リストまたはライブラリを使用するページングではなくライブラリが大きいと、目的の結果を直接取得するのに] ボックスの一覧でのフィルター処理でファイルを検索するのに検索を使用します。または、ページの読み込み時間を最小限にするビューを作成します。詳細については、 [Office 365 の大規模なリストとライブラリの管理](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-p113">When possible, reduce round trips to Office 365. For example, rather than paging through lists or libraries, use search to locate files in a large library and filtering in a list to get directly to the results you want. Or, create views that minimize page load time. For more information, see [Manage large lists and libraries in Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES).</span></span>
    
- <span data-ttu-id="774e1-p114">ビデオ パフォーマンスが低下する場合は、ビデオをダウンロードし、デバイスを監視することができます。ダウンロードのリンク、またはビデオのリンクを右クリックし、**保存対象**を選択できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="774e1-p114">If video performance is poor, you may be able to download the video and watch it on your device. A download link may be available, or you may be able to right click the video link, and select **Save Target as**.</span></span> 
    
 <span data-ttu-id="774e1-166">**ブラウザー固有**</span><span class="sxs-lookup"><span data-stu-id="774e1-166">**Browser-specific**</span></span>
  
<span data-ttu-id="774e1-167">特定のブラウザーのいくつかの提案を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="774e1-167">Here are some suggestions for your specific browser:</span></span>
  
- <span data-ttu-id="774e1-p115">**Internet Explorer**以前のバージョンの Internet Explorer のバージョン 11、または大幅なパフォーマンス向上のために後でをアップグレードします。詳細については、 [Internet Explorer の修正の問題](https://support.microsoft.com/mats/ie_performance_and_safety)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-p115">**Internet Explorer** Upgrade to Internet Explorer Version 11 or later for substantial performance improvements over previous versions. For more information, see [ Fix Internet Explorer issues ](https://support.microsoft.com/mats/ie_performance_and_safety).</span></span>
    
- <span data-ttu-id="774e1-170">**FireFox**詳細については、 [Firefox が遅いか動作を停止](https://support.mozilla.org/en-US/products/firefox/fix-problems/slowness-or-hanging)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-170">**FireFox**For more information, see [Firefox is slow or stops working](https://support.mozilla.org/en-US/products/firefox/fix-problems/slowness-or-hanging).</span></span>
    
- <span data-ttu-id="774e1-171">**サファリ**詳細については、 [Apple の Safari](https://www.apple.com/safari/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-171">**Safari** For more information, see [Apple - Safari](https://www.apple.com/safari/).</span></span>
    
- <span data-ttu-id="774e1-172">**クロム**詳細については、[クロムのヘルプ](https://support.google.com/chrome/?hl=en)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-172">**Chrome** For more information, see [Chrome Help](https://support.google.com/chrome/?hl=en).</span></span>
  
## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a><span data-ttu-id="774e1-173">Outlook と Outlook Web App を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="774e1-173">Best practices for using Outlook and Outlook Web App</span></span>

<span data-ttu-id="774e1-p116">読み取り、書き込み、および整理する電子メールは、すべてのユーザーの 1 日の大きな部分です。Outlook および Outlook Web App (OWA) は、オフライン サポートを提供します。電子メール アプリケーションを使用して、スマート フォンには、他の便利な方法です。お客様のニーズに最も適した次のオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="774e1-p116">Reading, writing, and organizing email is a big part of everyone's day. Both Outlook and Outlook Web App (OWA) offer offline support. Using an email app on your smart phone is another useful alternative. Use the following options that best fit your needs:</span></span>
  
- <span data-ttu-id="774e1-178">以前のバージョンの Outlook 2013 sp1 または大幅なパフォーマンス向上のために後でをアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="774e1-178">Upgrade to Outlook 2013 SP1 or later for substantial performance improvements over previous versions.</span></span> 
    
-  <span data-ttu-id="774e1-p117">Outlook Web App を使用して、Office 365 に接続できないオフラインのメッセージ、連絡先、および OWA では、次にアップロードされる予定表のイベントを作成できます。設定し、OWA を使用してオフライン モードにする方法の詳細について[を使用して Outlook Web App オフライン](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-p117">Outlook Web App lets you create offline messages, contacts, and calendar events that are uploaded when OWA is next able to connect to Office 365. For more information about setting up and using OWA in offline mode, see [Using Outlook Web App offline](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36).</span></span>
    
- <span data-ttu-id="774e1-p118">Outlook では、先に自動的に接続可能な場合、キャッシュ モードで作業することができます。Outlook のメールボックス全体、またはその一部だけをダウンロードすることができます。詳細については、 [Exchange キャッシュ モードを有効にして](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c)、 [Outlook でオフラインで作業](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-p118">Outlook lets you work in cached mode, in which it automatically connects whenever possible. You can have Outlook download your entire mailbox, or just a portion of it. For more information, see [Turn on Cached Exchange Mode](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) and [Work offline in Outlook](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633).</span></span> 
    
- <span data-ttu-id="774e1-p119">Outlook には、オフライン モードも用意されています。これを行うには、自分のアカウントからの情報がコンピューターにコピーされるようはまずキャッシュ モードを設定する必要があります。オフライン モードで Outlook がしようとする送信を使用して接続し、設定が表示されるか、設定すると手動でオンラインで作業することです。詳細については、[データ接続料金を避けるためにオフラインで作業する](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282)[送信を変更しオフラインで作業するときの設定が表示される](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a)、[オンラインにするオフラインで作業してからスイッチ](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-p119">Outlook also offers an offline mode. To use this, you must first set up cached mode so that information from your account is copied down to your computer. In offline mode, Outlook will try to connect using the send and receive settings, or when you manually set it to work online. For more information, see [Work offline to avoid data connection charges](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282), [Change send and receive settings when you work offline](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a), and [Switch from working offline to online](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9).</span></span> 
    
- <span data-ttu-id="774e1-188">スマート フォンを使っている場合は、電話のキャリアのネットワーク経由で自分の電子メールと予定表をトリアージするのには使用できます。</span><span class="sxs-lookup"><span data-stu-id="774e1-188">If you have a smart phone, you can use it to triage your email and calendar over your phone carrier's network.</span></span> 
    
> [!NOTE]
> <span data-ttu-id="774e1-p120">Outlook または OWA を使用する場合のいくつかのガイダンスがあります。ディスク領域が、デバイス上の問題でない場合は、Outlook の機能の完全なセットがあり、可能性が最も効果的に機能します。ディスク領域が、デバイス上の問題の場合は、[機能のサブセットが、オンラインの状況で最適な動作も、OWA を使用して検討してください。もちろん、連携して動作するのでいずれかを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="774e1-p120">Here is some guidance on when to use Outlook or OWA. If disk space is not an issue on your device, Outlook has a full set of features and might work best for you. If disk space is an issue on your device, consider using OWA which has a subset of features, but also works best in an online situation. Of course, you can use either because they work well together.</span></span> 
  
## <a name="best-practices-for-using-onedrive-for-business"></a><span data-ttu-id="774e1-193">OneDrive を使用してビジネスのためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="774e1-193">Best practices for using OneDrive for Business</span></span>

<span data-ttu-id="774e1-p121">ビジネスの OneDrive 設計されています、地上からのファイルを扱う、オンラインとオフライン。一度設定すれば、自動的にかつ確実に、変更の同期が発生する場所とするたびにするようにします。ネットワークが低速の場合は、ファイルのオフライン バージョンで使用できます。</span><span class="sxs-lookup"><span data-stu-id="774e1-p121">OneDrive for Business is designed from the ground up to work with your files online and offline. Once you set it up, synchronization of changes occurs automatically and reliably wherever and whenever you make them. If the network is slow, you can work with the offline version of the files.</span></span>
  
<span data-ttu-id="774e1-p122">同期アプリケーションのビジネスの OneDrive は、Office 2013 のに加え、(標準エディション)、または Office 2013 アプリケーションを含む、Office 365 サブスクリプションで利用できます。Office 2013 をお持ちでない場合ことができます同期アプリケーションのビジネスの OneDrive[をダウンロード](https://support.microsoft.com/kb/2903984)は無料です。このアプリケーションは、**エクスプ ローラーで開く**] または [**アップロード**コマンドを使用するよりも高速化もできます。詳細については、[ビジネスのファイルを Office 365 では、OneDrive を同期するようにコンピューターの設定](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-p122">The OneDrive for Business sync app is available with Office 2013 (Professional Plus, or Standard editions), or an Office 365 subscription that includes Office 2013 applications. If you don't have Office 2013, you can [download](https://support.microsoft.com/kb/2903984) the OneDrive for Business sync app for free. This app is also faster than using the **Open in Explorer** or **Upload** commands. For more information, see [Set up your computer to sync your OneDrive for Business files in Office 365](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16).</span></span>
  
<span data-ttu-id="774e1-201">同期アプリケーションのビジネス用の OneDrive を使用するためにいくつか追加のガイダンスを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="774e1-201">Here's some additional guidance for using the OneDrive for Business sync app:</span></span>
  
- <span data-ttu-id="774e1-202">最初に、大規模なライブラリを同期している場合は、たとえば、夜間営業時間外の時に同期を開始します。</span><span class="sxs-lookup"><span data-stu-id="774e1-202">If you're syncing a large library for the first time, start the sync during off hours, for example, overnight.</span></span> 
    
- <span data-ttu-id="774e1-p123">[ビジネス アプリケーションの OneDrive を持つライブラリの同期を停止](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330)機能を使用するには更新プログラムの同期を一時的に停止します。ただし、サイズの大きいキューを避けるために、時に、いくつかの時間など、短時間にこの機能を使用といくつかのユーザーが同じドキュメントで作業する場合、マージの競合の危険性を最小限に抑えるため、更新プログラムの番号です。</span><span class="sxs-lookup"><span data-stu-id="774e1-p123">You can use the [Stop syncing a library with the OneDrive for Business app](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) feature to temporarily stop syncing updates. However, use this feature for brief periods, such as a few hours at a time, to avoid queuing large numbers of updates, and to minimize the risk of merge conflicts if several people work on the same document.</span></span> 
  
## <a name="best-practices-for-using-onenote"></a><span data-ttu-id="774e1-205">OneNote を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="774e1-205">Best practices for using OneNote</span></span>

<span data-ttu-id="774e1-p124">すべての SharePoint チーム サイトには組み込みの OneNote ノートブックと独自に作成することができます簡単にします。OneNote は、毎日実行するタスクを取得する必要があること、タイムリーな情報を収集する優れた方法です。など、多くのチームは、毎週の会議、プロジェクトのメモ、アイデア、計画、および進捗レポートのコレクション ポイントとして OneNote を使用します。ページ、セクション、およびタブを使用してさまざまな情報をきちんと整理できます。</span><span class="sxs-lookup"><span data-stu-id="774e1-p124">Every SharePoint team site has a built-in OneNote notebook and you can easily create your own. OneNote is a great way to collect timely information that you need every day to get tasks done. For example, many teams use OneNote as a collection point for weekly meetings, project notes, ideas, plans, and status reports. You can neatly organize this disparate information by using pages, sections, and tabs.</span></span>
  
<span data-ttu-id="774e1-p125">OneNote の利点は、そのコンテンツにアクセスできます、ほぼすべてのデバイスから、デスクトップ、ラップトップ、タブレット、またはスマート フォンかどうか。および保存したり、OneNote が代わりのための同期について心配する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="774e1-p125">But the beauty of OneNote is that you can access the content from virtually any device, whether a desktop, a laptop, a tablet, or a smart phone. And you don't have to worry about saving or synchronizing because OneNote does it for you.</span></span> 
  
<span data-ttu-id="774e1-212">詳細については、 [Microsoft OneNote](https://office.microsoft.com/en-us/onenote/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-212">For more information, see [Microsoft OneNote](https://office.microsoft.com/en-us/onenote/).</span></span>
  
## <a name="best-practices-for-using-lync-online"></a><span data-ttu-id="774e1-213">Lync Online の使用に関するヒント集</span><span class="sxs-lookup"><span data-stu-id="774e1-213">Best practices for using Lync Online</span></span>

<span data-ttu-id="774e1-214">ネットワークが低速のときは、Lync オンライン使用するための一般的なガイドラインは、次のように。</span><span class="sxs-lookup"><span data-stu-id="774e1-214">The following are general guidelines for using Lync Online when your network is slow:</span></span>
  
- <span data-ttu-id="774e1-215">低速ネットワークで正しく動作するために可能な限りは、インスタント メッセージングを使用します。</span><span class="sxs-lookup"><span data-stu-id="774e1-215">Use instant messaging whenever you can because it works well on a slow network.</span></span>
    
- <span data-ttu-id="774e1-216">仮想プライベート ネットワーク (VPN) またはリモート アクセス サービス (RAS) 接続経由で電話をかけたりしないようにします。</span><span class="sxs-lookup"><span data-stu-id="774e1-216">Avoid making phone calls over a virtual private network (VPN) or remote access service (RAS) connections.</span></span>
    
- <span data-ttu-id="774e1-p126">オーディオ デバイスを承認することを確認します。詳細については、[電話および Microsoft Lync の修飾されたデバイス](https://technet.microsoft.com/en-us/office/dn788944)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-p126">Make sure your audio device is approved. For more information, see [Phones and Devices Qualified for Microsoft Lync](https://technet.microsoft.com/en-us/office/dn788944).</span></span>
    
-  <span data-ttu-id="774e1-p127">オンライン プレゼンテーションの PowerPoint を使用している場合は、サイズと、スライドの複雑さを軽減します。詳細については、[プレゼンテーションのパフォーマンスを向上させるためのヒント](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-p127">When using PowerPoint in an online presentation, reduce the size and complexity of the slides. For more information, see [Tips for improving the performance of your presentation](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949).</span></span>
    
- <span data-ttu-id="774e1-p128">可能であれば、プログラムやデスクトップではなく、モニターを共有します。詳細については、[デスクトップまたは Lync でプログラムを共有する](https://support.office.com/article/33aaa965-eb32-42a9-8a9b-cdfffa364842)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-p128">Whenever possible, share a monitor, instead of a program or a desktop. For more information, see [Share your desktop or a program in Lync](https://support.office.com/article/33aaa965-eb32-42a9-8a9b-cdfffa364842).</span></span>
    
- <span data-ttu-id="774e1-p129">会議として、PowerPoint スライドの送信、共有するのではなく添付ファイルを要求するため、出席者は、クライアント デバイスにスライドを表示します。詳細については、 [Lync 会議を設定する](https://support.office.com/article/258f9d20-f06c-49a4-a77f-7f5ac635bb5d)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-p129">Instead of sharing, send out the PowerPoint slides ahead of time as a meeting request attachment so attendees view the slides on their client device. For more information, see [Set up a Lync Meeting](https://support.office.com/article/258f9d20-f06c-49a4-a77f-7f5ac635bb5d).</span></span>
    
-  <span data-ttu-id="774e1-p130">ビデオの性能はネットワークのパフォーマンスに非常に依存します。ネットワークの速度が遅い場合、ビデオを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="774e1-p130">Video performance is very dependent on network performance. Avoid using video if your network is slow.</span></span> 
    
<span data-ttu-id="774e1-227">詳細については、[音声またはビデオの品質 Lync オンラインに](https://support.microsoft.com/kb/2386655)し、[低速の画面では、Lync 2013 を更新](https://support.microsoft.com/kb/2958375)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-227">For more information, see [Poor audio or video quality in Lync Online](https://support.microsoft.com/kb/2386655) and [Slow screen update in Lync 2013](https://support.microsoft.com/kb/2958375).</span></span>
  
## <a name="best-practices-for-using-sharepoint-lists"></a><span data-ttu-id="774e1-228">SharePoint リストを使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="774e1-228">Best practices for using SharePoint lists</span></span>

<span data-ttu-id="774e1-p131">「スクラブ」、分析、または低速なネットワークの影響を最小限に抑えるための優れた方法は、データをレポートにリスト データをオフラインで作業します。読み取りし、それらにリンクすることで Microsoft Access 2013 からのほとんどのリストを記述できます。Excel のテーブルとリストの間の一方向のデータ接続を作成する Excel のテーブルにリストをエクスポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="774e1-p131">Working with list data offline to "scrub", analyze, or report data is a great way to minimize the impact of a slow network. You can read and write most lists from Microsoft Access 2013 by linking to them. You can also export a list to an Excel Table, which creates a one-way data connection between the Excel table and the list.</span></span>
  
<span data-ttu-id="774e1-p132">さらに、Access Services の機能がアクティブな場合、使用できるかなりより多くのデータ リスト ビューのしきい値を既定で最大 50,000 の項目で。Access 2013 Excel 2013 小さなバッチでリストのデータを自動的に処理し、データのサービスのパフォーマンスに悪影響を及ぼす影響を与えずにリスト ビューのしきい値よりもずっと多くのデータの操作を可能にする方法を再構成し、両方他のユーザーです。</span><span class="sxs-lookup"><span data-stu-id="774e1-p132">Furthermore, if the Access Services feature is activated, then you can work with considerably more data than the List View Threshold, up to 50,000 items by default. Both Access 2013 and Excel 2013 automatically process list data in small batches and then reassemble the data, a technique that enables working with substantially more data than the List View Threshold, and without adversely impacting the service performance of other users.</span></span> 
  
<span data-ttu-id="774e1-234">詳細については、 [Office 365 の大規模なリストとライブラリを管理](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784)することで「より大規模なリストの管理」に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-234">For more information, see the section "More about managing large lists" in [Manage large lists and libraries in Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784).</span></span>
  
## <a name="best-practices-for-customizing-web-pages"></a><span data-ttu-id="774e1-235">Web ページをカスタマイズするためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="774e1-235">Best practices for customizing web pages</span></span>

<span data-ttu-id="774e1-p133">Web ページをカスタマイズするときに誤ってページのパフォーマンスの低下が発生します。いくつかの要因には、ページ、リストまたはライブラリ アイテムの数を最初に表示されます、どのように多くの web パーツが追加され、ページのコードを記述する方法のサイズと複雑さなど、影響を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="774e1-p133">When you customize a web page, you may inadvertently cause poor performance with the page. A number of factors can have an impact, such as the complexity and size of the page, how many web parts are added, how many list or library items are initially displayed, and the way you code the page.</span></span>
  
<span data-ttu-id="774e1-238">詳細については、 [SharePoint Online のチューニングのパフォーマンス](https://docs.microsoft.com/office365/enterprise/tune-sharepoint-online-performance)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-238">For more information, see [Tune SharePoint Online performance](https://docs.microsoft.com/office365/enterprise/tune-sharepoint-online-performance).</span></span>
  
## <a name="best-practices-for-using-project-online"></a><span data-ttu-id="774e1-239">プロジェクト オンラインを使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="774e1-239">Best practices for using Project Online</span></span>

<span data-ttu-id="774e1-240">次のガイドラインは、ネットワークのパフォーマンスの向上に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="774e1-240">The following guidelines can help improve network performance.</span></span>
  
- <span data-ttu-id="774e1-p134">プロジェクト オンラインおよび SharePoint Online は、同期時間がかかる可能性がある必要があります。プロジェクト チームの回転率が低い場合は、プロジェクトの発行およびプロジェクト詳細ページのパフォーマンスを向上させるためにプロジェクト サイトの同期を無効にします。システムを使用し、大規模なグループの同期の後、潜在的なアクセス許可の問題を監視するのには実際に必要なリソースのグループを Active Directory の同期を制限します。</span><span class="sxs-lookup"><span data-stu-id="774e1-p134">Project Online and SharePoint Online require synchronization, which can be time consuming. If your project teams have low turnover, disable Project Site Sync to improve the Project Publish and Project Detail Pages performance. Limit Active Directory sync to groups of resources that actually need to use the system, and monitor any potential permission issues after the synchronization of large groups.</span></span> 
    
- <span data-ttu-id="774e1-p135">組織は、プロジェクトのサイトを使用している場合は、作成要求ではなく、自動的にします。これは、最初の発行のエクスペリエンスを高速化、不要なサイトとコンテンツの作成を回避できます。</span><span class="sxs-lookup"><span data-stu-id="774e1-p135">If your organization uses project sites, create them on demand rather than automatically. This speeds up the first publishing experience and avoids creating unnecessary sites and content.</span></span>
    
- <span data-ttu-id="774e1-p136">プロジェクト詳細ページ (PDP) では、プロジェクト全体の再計算を実行でき、パフォーマンスを必要とする操作は、どちらのワークフロー アクションを開始することができます。同じ PDP を同時に 2 つの更新プログラムのプロセスをトリガーするを避けるため、予定表のフィールド (開始日、終了日、状況報告日および現在の日付) とスケジュールされていないフィールド (プロジェクト名、説明、および所有者) の更新をしないでください。</span><span class="sxs-lookup"><span data-stu-id="774e1-p136">Project Detail Pages (PDP) can trigger a recalculation of the entire project and kick off workflow actions, both of which can be performance-intensive operations. To avoid triggering two update processes at the same time on the same PDP, avoid updating the calendar fields (Start date, Finish date, Status date, and Current date) and the non-scheduled fields (project name, description, and owner).</span></span> 
    
- <span data-ttu-id="774e1-p137">Web パーツおよび各 PDP に表示されるカスタム フィールドの数を減らします。負荷を改善し、時間を節約するのには更新の必要なフィールドだけでは、専用の PDP を作成します。</span><span class="sxs-lookup"><span data-stu-id="774e1-p137">Reduce the number of Web Parts and custom fields displayed on each PDP. Create a dedicated PDP with the only fields that require updating to improve load and save time.</span></span> 
    
- <span data-ttu-id="774e1-250">レポートの OData を使用する場合は、クエリを実行する実行時にサーバー側のフィルター処理を使用してデータの量を制限します。</span><span class="sxs-lookup"><span data-stu-id="774e1-250">When you use OData for reporting, limit the amount of data you query at runtime by using server-side filtering.</span></span>
    
<span data-ttu-id="774e1-251">詳細については、[パフォーマンスのチューニングのプロジェクトのオンライン](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-251">For more information, see [Tune Project Online performance](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c).</span></span>
  
## <a name="whats-the-best-way-to-report-problems"></a><span data-ttu-id="774e1-252">問題を報告する最善の方法とは何ですか。</span><span class="sxs-lookup"><span data-stu-id="774e1-252">What's the best way to report problems?</span></span>

<span data-ttu-id="774e1-p138">マイクロソフトの継続的に帯域幅の測定、ネットワークを監視して、Office 365 の全体的なパフォーマンスの向上し、データ センターのハードウェアを追加する、最小限のダウンロード戦略を使用するページの待機時間、ページのロード時間、ディスク I/O の削減、再設計を改善し、複数のデータ ・ センターを追加します。現在の状態をチェックし、問題を報告する方法の詳細については、[サービスの状態]](https://office.microsoft.com/en-us/office365-suite-help/view-the-status-of-your-services-HA102817837.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="774e1-p138">Microsoft continually improves the overall performance of Office 365 by monitoring the network, measuring bandwidth and latency, improving page load time, reducing disk I/O, redesigning pages to use Minimal Download Strategy, adding hardware to data centers and adding more data centers. For more information about checking your current status and reporting issues, see [View the status of your services](https://office.microsoft.com/en-us/office365-suite-help/view-the-status-of-your-services-HA102817837.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="774e1-255">関連項目</span><span class="sxs-lookup"><span data-stu-id="774e1-255">See also</span></span>

[<span data-ttu-id="774e1-256">Office 365 のネットワーク計画とパフォーマンス チューニング</span><span class="sxs-lookup"><span data-stu-id="774e1-256">Network planning and performance tuning for Office 365</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="774e1-257">Microsoft 仮想アカデミー コース、Office 365 のパフォーマンス管理</span><span class="sxs-lookup"><span data-stu-id="774e1-257">Microsoft Virtual Academy course—Office 365 performance management</span></span>](https://blogs.office.com/2014/12/03/microsoft-virtual-academy-course-office-365-performance-management/)
  
[<span data-ttu-id="774e1-258">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="774e1-258">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="774e1-259">Office 365 エンドポイントの FAQ</span><span class="sxs-lookup"><span data-stu-id="774e1-259">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

