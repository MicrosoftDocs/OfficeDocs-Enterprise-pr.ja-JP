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
description: ネットワークの計画とテスト、および Office 365 への移行に関する情報へのリンクが含まれています。
ms.openlocfilehash: 02576933a1be615e65b695a7dd72c19eed311c91
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574041"
---
# <a name="network-and-migration-planning-for-office-365"></a><span data-ttu-id="1abd0-103">Office 365 のネットワークと移行の計画</span><span class="sxs-lookup"><span data-stu-id="1abd0-103">Network and migration planning for Office 365</span></span>

<span data-ttu-id="1abd0-104">この記事には、ネットワークの計画とテスト、および Office 365 への移行に関する情報へのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="1abd0-104">This article contains links to information about network planning and testing, and migration to Office 365.</span></span>
  
<span data-ttu-id="1abd0-105">office 365 に初めて展開するか、office に移行する前に、これらのトピックの情報を使用して必要な帯域幅を推定し、office 365 に展開または移行するのに十分な帯域幅があるかどうかをテストして確認することができます。</span><span class="sxs-lookup"><span data-stu-id="1abd0-105">Before you deploy for the first time or migrate to Office 365, you can use the information in these topics to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Office 365.</span></span>

||
|:-----|
| <span data-ttu-id="1abd0-106">この記事は[、Office 365 のネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)に含まれています。</span><span class="sxs-lookup"><span data-stu-id="1abd0-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

|||
|:-----|:-----|
|![「エンタープライズアーキテクトのための Microsoft クラウドネットワーク」のポスターを参照してください。](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|<span data-ttu-id="1abd0-108">Office 365 およびその他の microsoft クラウドプラットフォームおよびサービスに対してネットワークを最適化するための手順については、「[エンタープライズアーキテクトのための microsoft クラウドネットワーク](https://aka.ms/cloudarchnetworking)」のポスターを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1abd0-108">For the steps to optimize your network for Office 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) poster.</span></span> |
   
## <a name="estimate-network-bandwidth-requirements"></a><span data-ttu-id="1abd0-109">ネットワーク帯域幅の要件を見積もる</span><span class="sxs-lookup"><span data-stu-id="1abd0-109">Estimate network bandwidth requirements</span></span>
<span data-ttu-id="1abd0-110"><a name="EstimateBandwidthRequirements"> </a></span><span class="sxs-lookup"><span data-stu-id="1abd0-110"></span></span>

<span data-ttu-id="1abd0-111">Office 365 を使用すると、組織のインターネット回線の使用率が向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1abd0-111">Using Office 365 may increase the utilization of your organization's internet circuit.</span></span> <span data-ttu-id="1abd0-112">Office 365 が完全に展開され、少なくとも 20% の容量を維持している間に、使用可能な帯域幅の量が増加しているかどうかを判断することが重要です。</span><span class="sxs-lookup"><span data-stu-id="1abd0-112">It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Office 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.</span></span>
  
<span data-ttu-id="1abd0-113">帯域幅を推定するには、次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="1abd0-113">To estimate the bandwidth, use the following steps:</span></span>
  
1. <span data-ttu-id="1abd0-114">各インターネット出口を使用するクライアントの数を評価します。</span><span class="sxs-lookup"><span data-stu-id="1abd0-114">Assess the number of clients that will use each Internet egress.</span></span> <span data-ttu-id="1abd0-115">terabit ネットワークが可能な限り多くの接続を処理できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1abd0-115">Let our multi-terabit network handle as much of the connection as possible.</span></span> 
    
2. <span data-ttu-id="1abd0-116">クライアントが使用できる Office 365 サービスと機能を決定します。</span><span class="sxs-lookup"><span data-stu-id="1abd0-116">Determine which Office 365 services and features will be available for clients to use.</span></span> <span data-ttu-id="1abd0-117">さまざまなサービスや利用状況のプロファイルを持つユーザーのグループが存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1abd0-117">You will likely have groups of people with different services or usage profiles.</span></span>
    
3. <span data-ttu-id="1abd0-118">クライアントのパイロットグループに対するネットワークの使用を測定します。</span><span class="sxs-lookup"><span data-stu-id="1abd0-118">Measure the network use for a pilot group of clients.</span></span> <span data-ttu-id="1abd0-119">パイロットクライアントが、組織内のユーザーのさまざまなプロファイルおよび地理的に異なる場所を代表するものであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1abd0-119">Ensure the pilot clients are representative of the different profiles of people in the organization as well as the different geographic locations.</span></span> <span data-ttu-id="1abd0-120">[Exchange](https://go.microsoft.com/fwlink/p/?LinkId=321550)と[Skype for business](https://go.microsoft.com/fwlink/p/?LinkId=321551)の従来の電卓や、自分のネットワークで実行した[ケーススタディ](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)に対して、結果をクロスチェックすることができます。</span><span class="sxs-lookup"><span data-stu-id="1abd0-120">You can cross-check your results against our old calculators for [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)and [Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=321551) or the [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) we performed on our own network.</span></span> 
    
4. <span data-ttu-id="1abd0-121">ネットワークに変更を加える前に、パイロットグループの測定値を使用して、組織のニーズ全体を推定し、見積もりを検証するために再テストします。</span><span class="sxs-lookup"><span data-stu-id="1abd0-121">Use the measurements from the pilot group to extrapolate the entire organization's needs and re-test to validate the estimations before making any changes to your network.</span></span>
    
## <a name="test-your-existing-network"></a><span data-ttu-id="1abd0-122">既存のネットワークをテストする</span><span class="sxs-lookup"><span data-stu-id="1abd0-122">Test your existing network</span></span>
<span data-ttu-id="1abd0-123"><a name="calculators"> </a></span><span class="sxs-lookup"><span data-stu-id="1abd0-123"></span></span>

 <span data-ttu-id="1abd0-124">**ネットワークツール。**</span><span class="sxs-lookup"><span data-stu-id="1abd0-124">**Network tools.**</span></span> <span data-ttu-id="1abd0-125">インターネット帯域幅をテストおよび検証して、ダウンロード、アップロード、および待機時間の制約を決定します。</span><span class="sxs-lookup"><span data-stu-id="1abd0-125">Test and validate your Internet bandwidth to determine download, upload, and latency constraints.</span></span> <span data-ttu-id="1abd0-126">これらのツールは、完全に展開された後と同様に、移行のためのネットワークの機能を決定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1abd0-126">These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.</span></span> 
  
- <span data-ttu-id="1abd0-127">[Microsoft メッセージアナライザー](https://technet.microsoft.com/library/jj649776.aspx): メッセージアナライザーは、ネットワークの問題をトラブルシューティングするための効果的なツールです。</span><span class="sxs-lookup"><span data-stu-id="1abd0-127">[Microsoft Message Analyzer](https://technet.microsoft.com/library/jj649776.aspx): Message Analyzer is an effective tool for troubleshooting network issues.</span></span> <span data-ttu-id="1abd0-128">メッセージアナライザーは、プロトコルベースのメッセージングトラフィックおよびシステムメッセージをキャプチャ、表示、および分析します。</span><span class="sxs-lookup"><span data-stu-id="1abd0-128">Message Analyzer captures, displays, and analyzes protocol-based messaging traffic and system messages.</span></span> <span data-ttu-id="1abd0-129">メッセージアナライザーを使用すると、ログファイルとトレースファイルからデータをインポート、集計、および分析することもできます。</span><span class="sxs-lookup"><span data-stu-id="1abd0-129">Message Analyzer also lets you import, aggregate, and analyze data from log and trace files.</span></span>
    
- <span data-ttu-id="1abd0-130">[Microsoft リモート接続アナライザー](https://go.microsoft.com/fwlink/p/?LinkId=517243): Exchange Online 環境での接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="1abd0-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.</span></span>
    
- <span data-ttu-id="1abd0-131">Outlook および office 365 の問題を修正するには、 [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC)を使用します。</span><span class="sxs-lookup"><span data-stu-id="1abd0-131">Use the [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Office 365 problems.</span></span> 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a><span data-ttu-id="1abd0-132">Office 365 のネットワーク計画と移行パフォーマンスの向上のためのベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="1abd0-132">Best practices for network planning and improving migration performance for Office 365</span></span>
<span data-ttu-id="1abd0-133"><a name="BestPractices"> </a></span><span class="sxs-lookup"><span data-stu-id="1abd0-133"></span></span>

<span data-ttu-id="1abd0-134">Office 365 の動作を向上させる方法の詳細については、これらのベストプラクティスをさらに掘り下げて説明します。</span><span class="sxs-lookup"><span data-stu-id="1abd0-134">Dig a little deeper into these best practices for more information about improving your Office 365 experience.</span></span>
  
1. <span data-ttu-id="1abd0-135">すぐにユーザーのサポートを開始する必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="1abd0-135">Want to get started helping your users right away?</span></span> <span data-ttu-id="1abd0-136">ネットワークが連携していない場合に、SharePoint online、Exchange online、Lync online などの office 365 を使用する際のヒントについては、「 [office 365 を低速ネットワークで使用するためのベストプラクティス](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1abd0-136">See [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for tips on using Office 365, including SharePoint Online, Exchange Online, and Lync Online, when your network just isn't cooperating.</span></span> <span data-ttu-id="1abd0-137">この記事では、office 365 の動作を最適化するための TechNet および Support.office.com のコンテンツのロードについて説明し、web ページをカスタマイズする簡単な方法について説明します。また、最適な office 365 環境に合わせて Internet Explorer 設定を設定する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="1abd0-137">This article links out to loads of content on TechNet and Support.office.com for optimizing your Office 365 experience and includes information on easy ways to customize your web pages and how to set your Internet Explorer settings for the best Office 365 experience.</span></span> 
    
2. <span data-ttu-id="1abd0-138">「 [office 365 のネットワーク接続の原則](https://aka.ms/o365networkingprinciples)」を参照して、office 365 のトラフィックを安全に管理し、最適なパフォーマンスを得るための接続の原則について理解します。</span><span class="sxs-lookup"><span data-stu-id="1abd0-138">Read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> <span data-ttu-id="1abd0-139">この記事は、Office 365 ネットワーク接続を安全に最適化するための最新のガイダンスを理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1abd0-139">This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span> 
    
3. <span data-ttu-id="1abd0-140">Windows 更新プログラムのスケジュールを慎重に管理することによって、メールの移行のパフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="1abd0-140">Improve mail migration performance by carefully managing the schedule for Windows Updates.</span></span> <span data-ttu-id="1abd0-141">クライアントコンピューターをバッチ処理で更新し、ネットワーク帯域幅の使用を制限するために Office 365 に移行する前にすべてのクライアントコンピューターが更新されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="1abd0-141">You can update your client computers in batches and ensure that all client computers are updated before migrating to Office 365 to regulate the use of network bandwidth.</span></span> <span data-ttu-id="1abd0-142">詳細については、「 [Office のデスクトップを手動で更新および構成する (最新の更新プログラム](https://support.microsoft.com/gp/office-2013-365-update))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1abd0-142">For more information, see [Manually update and configure desktops for Office 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).</span></span>
    
4. <span data-ttu-id="1abd0-143">Office 365 のネットワークトラフィックは、信頼されたインターネットサービスとして扱われ、組織によっては、信頼されていないインターネットサービスへのネットワークトラフィックに関する、従来のフィルタリングやスキャンの多くをバイパスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="1abd0-143">Office 365 network traffic performs best when it's treated as a trusted Internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted Internet services.</span></span> <span data-ttu-id="1abd0-144">これには、プロキシユーザー認証やパケット検査などの送信処理の削除に加えて、適切なネットワークアドレス変換 (NAT) を使用してインターネットへのローカル出口を保証することや、増加を処理するのに十分な帯域幅容量が含まれます。ネットワーク要求。</span><span class="sxs-lookup"><span data-stu-id="1abd0-144">This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the Internet with the proper Network Address Translation (NAT) and enough bandwidth capacity to handle the increased network requests.</span></span> <span data-ttu-id="1abd0-145">ネットワーク上の信頼されたインターネットサービスとして office 365 を処理するようにネットワークを構成する方法の詳細については、「 [office 365 エンドポイントの管理](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1abd0-145">Refer to [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)for additional guidance on configuring your network to handle Office 365 as a trusted Internet service on your network.</span></span>
    
1. <span data-ttu-id="1abd0-146">[Office 365 エンドポイントの管理](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)を確認します。</span><span class="sxs-lookup"><span data-stu-id="1abd0-146">Ensure [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).</span></span> <span data-ttu-id="1abd0-147">Office 365 に送られる追加のトラフィックは、送信プロキシ接続の増加と、TLS/SSL を介したセキュリティで保護されたトラフィックの増加につながります。</span><span class="sxs-lookup"><span data-stu-id="1abd0-147">The additional traffic going to Office 365 results in an increase of outbound proxy connections as well as an increase in secure traffic over TLS/SSL.</span></span>
    
2. <span data-ttu-id="1abd0-148">送信プロキシでユーザー認証が必要な場合は、接続が遅くなったり、機能が失われたりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="1abd0-148">If your outbound proxies require user authentication you may experience slow connectivity or a loss of functionality.</span></span> <span data-ttu-id="1abd0-149">Office 365 ドメインの認証要件を省略すると、このオーバーヘッドを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="1abd0-149">Bypassing the authentication requirement for the Office 365 domains can reduce this overhead.</span></span>
    
3. <span data-ttu-id="1abd0-150">多数の共有予定表とメールボックスがある場合、Outlook から Exchange への接続数が増加する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1abd0-150">If you have a large number of shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange.</span></span> <span data-ttu-id="1abd0-151">たとえば、Outlook クライアントは、使用されている共有予定表ごとに、最大2つの追加の接続を開くことができます。</span><span class="sxs-lookup"><span data-stu-id="1abd0-151">For instance, the Outlook client may open up to two additional connections for each shared calendar in use.</span></span> <span data-ttu-id="1abd0-152">このような状況では、出口プロキシが接続を処理できることを確認するか、Outlook 用 Office 365 への接続のプロキシをバイパスするようにします。</span><span class="sxs-lookup"><span data-stu-id="1abd0-152">In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.</span></span>
    
4. <span data-ttu-id="1abd0-153">パブリック IP アドレスに対してサポートされるデバイスの最大数と、複数の IP アドレス間で負荷分散を行う方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="1abd0-153">Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses.</span></span> <span data-ttu-id="1abd0-154">詳細については、[Office 365 の NAT サポート](nat-support-with-office-365.md)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1abd0-154">For more information, see [NAT support with Office 365](nat-support-with-office-365.md).</span></span>
    
5. <span data-ttu-id="1abd0-155">ネットワーク上のコンピューターからの送信接続を調査している場合は、このフィルター処理を Office 365 ドメインにバイパスすると、接続性とパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="1abd0-155">If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Office 365 domains will improve connectivity and performance.</span></span> <span data-ttu-id="1abd0-156">さらに、送信検査をバイパスすることで、単一のインターネット出口の必要性がなくなり、Office 365 の宛先のネットワーク要求に対してローカルのインターネット出口が有効になります。</span><span class="sxs-lookup"><span data-stu-id="1abd0-156">Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Office 365 destined network requests.</span></span>
    
6. <span data-ttu-id="1abd0-157">内部ネットワーク設定を見つけるお客様は、パフォーマンスに影響を与える場合があります。</span><span class="sxs-lookup"><span data-stu-id="1abd0-157">Some customers find internal network settings may affect performance.</span></span> <span data-ttu-id="1abd0-158">最大転送単位 (MTU) サイズ、ネットワーク自動ネゴシエーションまたは自動検出、インターネットへのサブ最適なルートなどの設定は、よく見られる場所です。</span><span class="sxs-lookup"><span data-stu-id="1abd0-158">Settings such as maximum transmission unit (MTU) size, network auto-negotiation or auto-detection, and sub-optimal routes to the Internet are common places to look.</span></span>
    
## <a name="network-planning-reference-for-office-365"></a><span data-ttu-id="1abd0-159">Office 365 のネットワーク計画リファレンス</span><span class="sxs-lookup"><span data-stu-id="1abd0-159">Network planning reference for Office 365</span></span>
<span data-ttu-id="1abd0-160"><a name="NetReference"> </a></span><span class="sxs-lookup"><span data-stu-id="1abd0-160"></span></span>

<span data-ttu-id="1abd0-161">これらのトピックには、詳細な Office 365 のネットワーク参照情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1abd0-161">These topics contain detailed Office 365 network reference information.</span></span>
  
- [<span data-ttu-id="1abd0-162">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="1abd0-162">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [<span data-ttu-id="1abd0-163">クライアント接続</span><span class="sxs-lookup"><span data-stu-id="1abd0-163">Client connectivity</span></span>](client-connectivity.md)
    
- [<span data-ttu-id="1abd0-164">コンテンツ配信ネットワーク</span><span class="sxs-lookup"><span data-stu-id="1abd0-164">Content delivery networks</span></span>](content-delivery-networks.md)
    
- [<span data-ttu-id="1abd0-165">Office 365 の外部ドメイン ネーム システムのレコード</span><span class="sxs-lookup"><span data-stu-id="1abd0-165">External Domain Name System records for Office 365</span></span>](external-domain-name-system-records.md)
    
- [<span data-ttu-id="1abd0-166">Office 365 サービスでの IPv6 サポート</span><span class="sxs-lookup"><span data-stu-id="1abd0-166">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
    
- [<span data-ttu-id="1abd0-167">Office 365 ネットワーク接続の原則</span><span class="sxs-lookup"><span data-stu-id="1abd0-167">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
    
- [<span data-ttu-id="1abd0-168">Office 365 のビデオネットワークについてよく寄せられる質問 (FAQ)</span><span class="sxs-lookup"><span data-stu-id="1abd0-168">Office 365 video networking Frequently Asked Questions (FAQ)</span></span>](office-365-video-networking-faq.md)
    
- [<span data-ttu-id="1abd0-169">Office 365 サービスに接続するネットワークデバイスを計画する</span><span class="sxs-lookup"><span data-stu-id="1abd0-169">Plan for network devices that connect to Office 365 services</span></span>](plan-for-network-devices.md)
    
- [<span data-ttu-id="1abd0-170">Office 365 サービスの展開アドバイザー</span><span class="sxs-lookup"><span data-stu-id="1abd0-170">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
    

