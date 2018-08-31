---
title: Office 365 のネットワークと移行の計画
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: ネットワークの計画とテストに関する情報へのリンクと Office 365 への移行が含まれています。
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223059"
---
# <a name="network-and-migration-planning-for-office-365"></a><span data-ttu-id="315f0-103">Office 365 のネットワークと移行の計画</span><span class="sxs-lookup"><span data-stu-id="315f0-103">Network and migration planning for Office 365</span></span>

<span data-ttu-id="315f0-104">この資料には、ネットワークの計画とテストに関する情報へのリンクと Office 365 への移行が含まれています。</span><span class="sxs-lookup"><span data-stu-id="315f0-104">This article contains links to information about network planning and testing, and migration to Office 365.</span></span>
  
<span data-ttu-id="315f0-105">初めて展開したり、Office 365 に移行したりする前に、これらのトピックの情報を使って必要な帯域幅を見積もってから、Office 365 に展開または移行するだけの十分な帯域幅があることをテストし、確認します。</span><span class="sxs-lookup"><span data-stu-id="315f0-105">Before you deploy for the first time or migrate to Office 365, you can use the information in these topics to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Office 365.</span></span>

||
|:-----|
| <span data-ttu-id="315f0-106">この資料は、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://aka.ms/tune)の一部です。</span><span class="sxs-lookup"><span data-stu-id="315f0-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

|||
|:-----|:-----|
|![エンタープライズ設計者のポスターのクラウドのネットワークを参照してください。](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|<span data-ttu-id="315f0-108">、Office 365 とその他のマイクロソフトのクラウド プラットフォームおよびサービスのネットワークを最適化するための手順は、[エンタープライズ設計者向けのマイクロソフト クラウド ネットワーク](https://aka.ms/cloudarchnetworking)のポスターを参照してください。</span><span class="sxs-lookup"><span data-stu-id="315f0-108">For the steps to optimize your network for Office 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) poster.</span></span> |
   
## <a name="estimate-network-bandwidth-requirements"></a><span data-ttu-id="315f0-109">ネットワーク帯域幅の要件を見積もる</span><span class="sxs-lookup"><span data-stu-id="315f0-109">Estimate network bandwidth requirements</span></span>
<span data-ttu-id="315f0-110"><a name="EstimateBandwidthRequirements"> </a></span><span class="sxs-lookup"><span data-stu-id="315f0-110"></span></span>

<span data-ttu-id="315f0-p101">Office 365 を使用すると、組織のインターネット回線の使用率が向上します。現在利用可能な帯域幅は、Office 365 が少なくとも 20% のまま、完全に展開した後に予想される増加を処理するために十分なかどうかを決定することが重要、最もよく利用される日の処理能力です。</span><span class="sxs-lookup"><span data-stu-id="315f0-p101">Using Office 365 may increase the utilization of your organization's internet circuit. It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Office 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.</span></span>
  
<span data-ttu-id="315f0-113">帯域幅を見積もるには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="315f0-113">To estimate the bandwidth, use the following steps:</span></span>
  
1. <span data-ttu-id="315f0-p102">各インターネット出口を使用するクライアントの数を評価します。マルチ terabit ネットワーク処理の可能な接続を使用できます。</span><span class="sxs-lookup"><span data-stu-id="315f0-p102">Assess the number of clients that will use each Internet egress. Let our multi-terabit network handle as much of the connection as possible.</span></span> 
    
2. <span data-ttu-id="315f0-p103">Office 365 のサービスや機能を使用するクライアントに対して使用されますを決定します。グループのさまざまなサービスや利用状況プロファイルを持つユーザーが見込まれます。</span><span class="sxs-lookup"><span data-stu-id="315f0-p103">Determine which Office 365 services and features will be available for clients to use. You will likely have groups of people with different services or usage profiles.</span></span>
    
3. <span data-ttu-id="315f0-p104">クライアントのパイロット グループのネットワークの使用を測定します。パイロットのクライアントは、別の地理的な場所と同様に、組織内のユーザーのさまざまなプロファイルの担当者を確認します。ことができますクロス チェック結果、古い計算機に対して[交換](https://go.microsoft.com/fwlink/p/?LinkId=321550)と[ビジネス用の Skype](https://go.microsoft.com/fwlink/p/?LinkId=321551)または当社独自のネットワークで実行して、[ケース ・ スタディ](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)用です。</span><span class="sxs-lookup"><span data-stu-id="315f0-p104">Measure the network use for a pilot group of clients. Ensure the pilot clients are representative of the different profiles of people in the organization as well as the different geographic locations. You can cross-check your results against our old calculators for [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)and [Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=321551) or the [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) we performed on our own network.</span></span> 
    
4. <span data-ttu-id="315f0-121">パイロット グループからの測定値を使用して、組織全体のニーズを推定して、ネットワークに変更を加える前に、見積もりを検証するテストを再度実行します。</span><span class="sxs-lookup"><span data-stu-id="315f0-121">Use the measurements from the pilot group to extrapolate the entire organization's needs and re-test to validate the estimations before making any changes to your network.</span></span>
    
## <a name="test-your-existing-network"></a><span data-ttu-id="315f0-122">既存ネットワークをテストします。</span><span class="sxs-lookup"><span data-stu-id="315f0-122">Test your existing network</span></span>
<span data-ttu-id="315f0-123"><a name="calculators"> </a></span><span class="sxs-lookup"><span data-stu-id="315f0-123"></span></span>

 <span data-ttu-id="315f0-p105">**ネットワーク ツールです**。テストし、ダウンロード、アップロード、および待機時間の制約を確認するのには、インターネットの帯域幅を検証します。これらのツールを使用すると、移行のためには」と「完全に展開している後に、ネットワークの機能を判断しますできます。</span><span class="sxs-lookup"><span data-stu-id="315f0-p105">**Network tools.** Test and validate your Internet bandwidth to determine download, upload, and latency constraints. These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.</span></span> 
  
- <span data-ttu-id="315f0-p106">[Microsoft メッセージ アナライザー](https://technet.microsoft.com/library/jj649776.aspx): メッセージのアナライザーは、ネットワークの問題のトラブルシューティングのための効果的なツールです。メッセージ アナライザーをキャプチャが表示され、プロトコル ベースのメッセージング トラフィックとシステム メッセージを分析します。メッセージ アナライザーを使用して、インポート、集計、およびログ ファイルとトレース ファイルからデータを分析することもできます。</span><span class="sxs-lookup"><span data-stu-id="315f0-p106">[Microsoft Message Analyzer](https://technet.microsoft.com/library/jj649776.aspx): Message Analyzer is an effective tool for troubleshooting network issues. Message Analyzer captures, displays, and analyzes protocol-based messaging traffic and system messages. Message Analyzer also lets you import, aggregate, and analyze data from log and trace files.</span></span>
    
- <span data-ttu-id="315f0-130">[Microsoft リモート接続アナライザー](https://go.microsoft.com/fwlink/p/?LinkId=517243): Exchange のオンライン環境での接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="315f0-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.</span></span>
    
- <span data-ttu-id="315f0-131">Outlook と Office 365 の問題を解決するの[Microsoft のサポート、および Office 365 の回復時のアシスタント](https://diagnostics.office.com/#/Download?env=SOC)を使用します。</span><span class="sxs-lookup"><span data-stu-id="315f0-131">Use the [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Office 365 problems.</span></span> 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a><span data-ttu-id="315f0-132">Best practices for network planning and improving migration performance for Office 365</span><span class="sxs-lookup"><span data-stu-id="315f0-132">Best practices for network planning and improving migration performance for Office 365</span></span>
<span data-ttu-id="315f0-133"><a name="BestPractices"> </a></span><span class="sxs-lookup"><span data-stu-id="315f0-133"></span></span>

<span data-ttu-id="315f0-134">パフォーマンスについて少し掘り下げて、Office 365 の満足度の向上の詳細については、これらのベスト プラクティスにします。</span><span class="sxs-lookup"><span data-stu-id="315f0-134">Dig a little deeper into these best practices for more information about improving your Office 365 experience.</span></span>
  
1. <span data-ttu-id="315f0-p107">ユーザーをすぐに支援を開始するか。含む SharePoint Online Exchange Online では、Lync オンラインでは、ネットワークだけで協力されていない場合、Office 365 の使用に関するヒントについては、[低速のネットワーク上の Office 365 を使用するためのベスト プラクティス](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)を参照してください。この資料では、リンク先を TechNet および Support.office.com 上のコンテンツの読み込みを Office 365 のエクスペリエンスを最適化し、簡単に、web ページおよび Internet Explorer の設定を Office 365 で利用する最適な方法をカスタマイズする方法に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="315f0-p107">Want to get started helping your users right away? See [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for tips on using Office 365, including SharePoint Online, Exchange Online, and Lync Online, when your network just isn't cooperating. This article links out to loads of content on TechNet and Support.office.com for optimizing your Office 365 experience and includes information on easy ways to customize your web pages and how to set your Internet Explorer settings for the best Office 365 experience.</span></span> 
    
2. <span data-ttu-id="315f0-p108">安全に Office 365 のトラフィックを管理し、最高のパフォーマンスを取得するための接続の原理を理解するのには[Office 365 のネットワーク接続性の原則](https://aka.ms/o365networkingprinciples)を参照してください。この資料では Office 365 のネットワーク接続を安全に最適化するため、最新のガイダンスを理解できます。</span><span class="sxs-lookup"><span data-stu-id="315f0-p108">Read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance. This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span> 
    
3. <span data-ttu-id="315f0-p109">メールの移行のパフォーマンスを向上するには、Windows の更新プログラムのスケジュールを慎重に管理します。バッチ処理でクライアント コンピューターを更新し、すべてのクライアント コンピューターがネットワークの帯域幅の使用を規定するのには Office 365 に移行する前に更新されていることを確認できます。詳細については、[手動で更新し最新の更新プログラムの Office 365 のデスクトップの構成](https://support.microsoft.com/gp/office-2013-365-update)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="315f0-p109">Improve mail migration performance by carefully managing the schedule for Windows Updates. You can update your client computers in batches and ensure that all client computers are updated before migrating to Office 365 to regulate the use of network bandwidth. For more information, see [Manually update and configure desktops for Office 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).</span></span>
    
4. <span data-ttu-id="315f0-p110">ネットワークのトラフィックを office 365 は、信頼できるインターネット サービスとして扱われ、多くの従来のフィルタ リングや信頼されていないインターネット サービスへのネットワーク トラフィックの一部の組織に配置するスキャンをバイパスすることが、ときに発揮します。送信プロキシ ユーザーの認証とパケットの検査などの処理し同様に適切なネットワーク アドレス変換 (NAT) と十分な帯域幅の容量増加を処理するためにインターネットへのローカル出口の確保を削除することがあります。ネットワークに要求します。ネットワーク上の信頼できるインターネット サービスとして Office 365 を処理するためにネットワークの構成に関する追加のガイダンスについては、 [Office 365 の管理のエンドポイント](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)に参照してください。</span><span class="sxs-lookup"><span data-stu-id="315f0-p110">Office 365 network traffic performs best when it's treated as a trusted Internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted Internet services. This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the Internet with the proper Network Address Translation (NAT) and enough bandwidth capacity to handle the increased network requests. Refer to [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)for additional guidance on configuring your network to handle Office 365 as a trusted Internet service on your network.</span></span>
    
1. <span data-ttu-id="315f0-p111">[Office 365 の管理の端点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)を確認します。Office 365 に追加のトラフィックは、TLS または SSL 経由で、アウト バウンド プロキシ接続の増加とセキュリティで保護されたトラフィックが増加になります。</span><span class="sxs-lookup"><span data-stu-id="315f0-p111">Ensure [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). The additional traffic going to Office 365 results in an increase of outbound proxy connections as well as an increase in secure traffic over TLS/SSL.</span></span>
    
2. <span data-ttu-id="315f0-p112">アウト バウンド プロキシがユーザー認証を必要とする場合、接続が低速または機能の損失が発生することがあります。Office 365 のドメインの認証の要件をバイパスすると、このオーバーヘッドを軽減できます。</span><span class="sxs-lookup"><span data-stu-id="315f0-p112">If your outbound proxies require user authentication you may experience slow connectivity or a loss of functionality. Bypassing the authentication requirement for the Office 365 domains can reduce this overhead.</span></span>
    
3. <span data-ttu-id="315f0-p113">大量の予定表とメールボックスを共有している場合は、Outlook から Exchange への接続数が増加する可能性があります。たとえば、Outlook クライアントは、使用中の共有の予定表ごとに 2 つまでの追加の接続を開くことができます。この場合は、出口プロキシが接続を処理できることを保証するか、Outlook の Office 365 への接続用のプロキシをバイパスします。</span><span class="sxs-lookup"><span data-stu-id="315f0-p113">If you have a large number of shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange. For instance, the Outlook client may open up to two additional connections for each shared calendar in use. In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.</span></span>
    
4. <span data-ttu-id="315f0-p114">パブリック IP アドレスのサポートされているデバイスの最大数と複数の IP アドレスの間で負荷を分散する方法を決定します。詳細については、 [NAT は、Office 365 のサポート](nat-support-with-office-365.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="315f0-p114">Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses. For more information, see [NAT support with Office 365](nat-support-with-office-365.md).</span></span>
    
5. <span data-ttu-id="315f0-p115">接続性とパフォーマンスが場合は、ネットワーク上のコンピューターからの送信接続を調べているが向上、Office 365 のドメインにこのフィルターをバイパスします。さらに、送信頻度を検査をバイパスしてインターネット出口を 1 つの必要性を削除し、Office 365 の宛先のネットワーク要求をローカルのインターネット出力を有効にします。</span><span class="sxs-lookup"><span data-stu-id="315f0-p115">If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Office 365 domains will improve connectivity and performance. Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Office 365 destined network requests.</span></span>
    
6. <span data-ttu-id="315f0-p116">一部のお客様は、パフォーマンスに影響を与える可能性があります内部ネットワークの設定を検索します。オート ・ ネゴシエーションまたは自動検出、ネットワークの最大転送ユニット (MTU) のサイズなどの設定、インターネットへの最適のルートは一般的な場所です。</span><span class="sxs-lookup"><span data-stu-id="315f0-p116">Some customers find internal network settings may affect performance. Settings such as maximum transmission unit (MTU) size, network auto-negotiation or auto-detection, and sub-optimal routes to the Internet are common places to look.</span></span>
    
## <a name="network-planning-reference-for-office-365"></a><span data-ttu-id="315f0-159">Office 365 のネットワーク計画の参照</span><span class="sxs-lookup"><span data-stu-id="315f0-159">Network planning reference for Office 365</span></span>
<span data-ttu-id="315f0-160"><a name="NetReference"> </a></span><span class="sxs-lookup"><span data-stu-id="315f0-160"></span></span>

<span data-ttu-id="315f0-161">これらのトピックには、Office 365 ネットワークの詳細なリファレンス情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="315f0-161">These topics contain detailed Office 365 network reference information.</span></span>
  
- [<span data-ttu-id="315f0-162">Office 365 エンドポイントを管理します。</span><span class="sxs-lookup"><span data-stu-id="315f0-162">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [<span data-ttu-id="315f0-163">クライアント接続</span><span class="sxs-lookup"><span data-stu-id="315f0-163">Client connectivity</span></span>](client-connectivity.md)
    
- [<span data-ttu-id="315f0-164">コンテンツ配信ネットワーク</span><span class="sxs-lookup"><span data-stu-id="315f0-164">Content delivery networks</span></span>](content-delivery-networks.md)
    
- [<span data-ttu-id="315f0-165">Office 365 の外部のドメイン ネーム システムのレコード</span><span class="sxs-lookup"><span data-stu-id="315f0-165">External Domain Name System records for Office 365</span></span>](external-domain-name-system-records.md)
    
- [<span data-ttu-id="315f0-166">Office 365 サービスでの IPv6 サポート</span><span class="sxs-lookup"><span data-stu-id="315f0-166">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
    
- [<span data-ttu-id="315f0-167">Office 365 ネットワーク接続の原則</span><span class="sxs-lookup"><span data-stu-id="315f0-167">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
    
- [<span data-ttu-id="315f0-168">Microsoft 仮想アカデミー: Office 365 のパフォーマンス管理</span><span class="sxs-lookup"><span data-stu-id="315f0-168">Microsoft Virtual Academy: Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [<span data-ttu-id="315f0-169">Office 365 ビデオ ネットワークのよく寄せられる質問 (FAQ)</span><span class="sxs-lookup"><span data-stu-id="315f0-169">Office 365 video networking Frequently Asked Questions (FAQ)</span></span>](office-365-video-networking-faq.md)
    
- [<span data-ttu-id="315f0-170">Office 365 サービスに接続するネットワーク デバイスの計画</span><span class="sxs-lookup"><span data-stu-id="315f0-170">Plan for network devices that connect to Office 365 services</span></span>](plan-for-network-devices.md)
    
- [<span data-ttu-id="315f0-171">Office 365 サービスの展開アドバイザー</span><span class="sxs-lookup"><span data-stu-id="315f0-171">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
    

