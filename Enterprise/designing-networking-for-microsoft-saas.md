---
title: "Microsoft SaaS のためのネットワーク デザイン"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: "概要: Office 365、Microsoft Intune、Dynamics 365 を含む Microsoft の SaaS サービスにアクセスするためにネットワークを最適化する方法を理解します。"
ms.openlocfilehash: e4d83f9ab88408b3eb5ca98379bbc709ec8f31a7
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="fa873-103">Microsoft SaaS のためのネットワーク デザイン</span><span class="sxs-lookup"><span data-stu-id="fa873-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="fa873-104">**概要:** Office 365、Microsoft Intune、Dynamics 365 を含む Microsoft の SaaS サービスにアクセスするためにネットワークを最適化する方法を理解します。</span><span class="sxs-lookup"><span data-stu-id="fa873-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="fa873-105">Microsoft SaaS サービス向けにネットワークを最適化するには、インターネット エッジ、クライアント デバイス、および標準の IT 運用を慎重に分析する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa873-105">Optimizing your network for Microsoft SaaS services requires careful analysis of your Internet edge, your client devices, and typical IT operations.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="fa873-106">Microsoft SaaS サービスを利用するためのネットワークの準備の手順</span><span class="sxs-lookup"><span data-stu-id="fa873-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="fa873-107">Microsoft SaaS サービス向けにネットワークを最適化するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="fa873-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="fa873-108">[Microsoft クラウド接続の一般的な要素](common-elements-of-microsoft-cloud-connectivity.md)の「**Microsoft クラウド サービスを利用するためのネットワークの準備の手順**」セクションを読んでください。</span><span class="sxs-lookup"><span data-stu-id="fa873-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="fa873-109">プロキシ サーバーの推奨事項を使用して、Microsoft SaaS サービス向けにインターネット出口を最適化します。</span><span class="sxs-lookup"><span data-stu-id="fa873-109">Optimize your Internet egress for Microsoft SaaS services using the proxy server recommendations.</span></span>
    
3. <span data-ttu-id="fa873-110">近接性および場所に関する推奨事項を使用して、インターネット スループットを最適化します。</span><span class="sxs-lookup"><span data-stu-id="fa873-110">Optimize your Internet throughput using the proximity and location recommendations.</span></span>
    
4. <span data-ttu-id="fa873-111">クライアント使用の考慮事項に基づいて配置されたクライアント コンピューターおよびイントラネットのパフォーマンスを最適化します。</span><span class="sxs-lookup"><span data-stu-id="fa873-111">Optimize the performance of your client computers and the intranet on which they are located using the client usage considerations.</span></span>
    
5. <span data-ttu-id="fa873-112">必要に応じて、IT 運用上の考慮事項に基づき、データの移行と同期のパフォーマンスを最適化します。</span><span class="sxs-lookup"><span data-stu-id="fa873-112">As needed, optimize the performance of data migrations and synchronization using the IT operations considerations.</span></span>
    
## <a name="internet-edge-considerations"></a><span data-ttu-id="fa873-113">インターネット エッジの考慮事項</span><span class="sxs-lookup"><span data-stu-id="fa873-113">Internet edge considerations</span></span>

<span data-ttu-id="fa873-114">ここでは、インターネット エッジおよびMicrosoft SaaS サービスへのスループットを最適化するための考慮事項を説明します。</span><span class="sxs-lookup"><span data-stu-id="fa873-114">Here are some things to consider optimize your Internet edge and throughput to Microsoft SaaS services.</span></span>
  
<span data-ttu-id="fa873-115">**図 1:マイクロソフト SaaS サービスの接続オプション**</span><span class="sxs-lookup"><span data-stu-id="fa873-115">**Figure 1: Connection options for Microsoft SaaS services**</span></span>

![図 1:マイクロソフト SaaS サービスの接続オプション](images/Network_Poster/SaaS1.png)
  
<span data-ttu-id="fa873-117">図 1 はインターネット パイプまたは ExpressRoute によって Microsoft SaaS サービスに接続しているオンプレミスのネットワークを示しています。</span><span class="sxs-lookup"><span data-stu-id="fa873-117">Figure 1 shows an on-premises network connecting to Microsoft SaaS services over an Internet pipe or ExpressRoute.</span></span>
  
<span data-ttu-id="fa873-118">プロキシ サーバーを最適化するための推奨事項を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="fa873-118">Here are some recommendations to optimize your proxy server:</span></span>
  
- <span data-ttu-id="fa873-119">WPAD、PAC、または GPO を使用して Web クライアントを構成します</span><span class="sxs-lookup"><span data-stu-id="fa873-119">Configure web clients using WPAD, PAC, or GPO</span></span>
    
- <span data-ttu-id="fa873-120">SSL インターセプトを使用しません</span><span class="sxs-lookup"><span data-stu-id="fa873-120">Don't use SSL interception</span></span>
    
- <span data-ttu-id="fa873-121">PAC ファイルを使用して、Microsoft SaaS サービスの DNS 名に関するプロキシをバイパスします</span><span class="sxs-lookup"><span data-stu-id="fa873-121">Use a PAC file to bypass the proxy for Microsoft SaaS service DNS names</span></span>
    
- <span data-ttu-id="fa873-122">CRL/OCSP 検証のためのトラフィックを許可します</span><span class="sxs-lookup"><span data-stu-id="fa873-122">Allow traffic for CRL/OCSP verification</span></span>
    
<span data-ttu-id="fa873-123">確認する必要のあるプロキシ サーバーのボトルネックを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="fa873-123">Here are some proxy server bottlenecks to check:</span></span>
  
- <span data-ttu-id="fa873-124">不十分な常時接続 (Outlook)</span><span class="sxs-lookup"><span data-stu-id="fa873-124">Insufficient persistent connections (Outlook)</span></span>
    
- <span data-ttu-id="fa873-125">容量の不足</span><span class="sxs-lookup"><span data-stu-id="fa873-125">Insufficient capacity</span></span>
    
- <span data-ttu-id="fa873-126">オフ ネットワーク評価の実行</span><span class="sxs-lookup"><span data-stu-id="fa873-126">Doing off-network evaluation</span></span>
    
- <span data-ttu-id="fa873-127">認証の要求</span><span class="sxs-lookup"><span data-stu-id="fa873-127">Requiring authentication</span></span>
    
- <span data-ttu-id="fa873-128">UDP トラフィックがサポートされていない (Skype for Business)</span><span class="sxs-lookup"><span data-stu-id="fa873-128">No support for UDP traffic (Skype for Business)</span></span>
    
<span data-ttu-id="fa873-129">近接性と場所に関する推奨事項を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="fa873-129">Here are some proximity and location recommendations:</span></span>
  
- <span data-ttu-id="fa873-130">プライベート WAN によってインターネット トラフィックをルーティングしないようにします</span><span class="sxs-lookup"><span data-stu-id="fa873-130">Don't route your Internet traffic over the private WAN</span></span>
    
- <span data-ttu-id="fa873-131">地域外ユーザーに対して地域内 DNS とインターネット トラフィック フローを使用します</span><span class="sxs-lookup"><span data-stu-id="fa873-131">Use in-region DNS and Internet traffic flow for out-of-region users</span></span>
    
- <span data-ttu-id="fa873-132">Office 365 のための高帯域幅、および Azure サービスとの同時接続のために、ExpressRoute を使用します</span><span class="sxs-lookup"><span data-stu-id="fa873-132">Use ExpressRoute for high bandwidth to Office 365 and concurrent connectivity with Azure services</span></span>
    
<span data-ttu-id="fa873-133">Office 365 のトラフィックに必要な送信ポートを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="fa873-133">Here are the outbound ports needed for Office 365 traffic:</span></span>
  
- <span data-ttu-id="fa873-134">TCP 80 (CRL/OCSP チェックのため)</span><span class="sxs-lookup"><span data-stu-id="fa873-134">TCP 80 (for CRL/OCSP checks)</span></span>
    
- <span data-ttu-id="fa873-135">TCP 443</span><span class="sxs-lookup"><span data-stu-id="fa873-135">TCP 443</span></span>
    
- <span data-ttu-id="fa873-136">UDP 3478</span><span class="sxs-lookup"><span data-stu-id="fa873-136">UDP 3478</span></span>
    
- <span data-ttu-id="fa873-137">TCP 5223</span><span class="sxs-lookup"><span data-stu-id="fa873-137">TCP 5223</span></span>
    
- <span data-ttu-id="fa873-138">TCP 50000 ～ 59999</span><span class="sxs-lookup"><span data-stu-id="fa873-138">TCP 50000-59999</span></span>
    
- <span data-ttu-id="fa873-139">UDP 50000 ～ 59999</span><span class="sxs-lookup"><span data-stu-id="fa873-139">UDP 50000-59999</span></span>
    
## <a name="client-usage-considerations"></a><span data-ttu-id="fa873-140">クライアント使用に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="fa873-140">Client usage considerations</span></span>

<span data-ttu-id="fa873-141">最初に、次のようなクライアントが使用するサービスのセットを構成します。</span><span class="sxs-lookup"><span data-stu-id="fa873-141">First, configure the set of services that your clients will be using, such as:</span></span>
  
- <span data-ttu-id="fa873-142">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="fa873-142">Azure Active Directory</span></span>
    
- <span data-ttu-id="fa873-143">Office 365</span><span class="sxs-lookup"><span data-stu-id="fa873-143">Office 365</span></span>
    
  - <span data-ttu-id="fa873-144">Office クライアント アプリ</span><span class="sxs-lookup"><span data-stu-id="fa873-144">Office client apps</span></span>
    
  - <span data-ttu-id="fa873-145">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="fa873-145">SharePoint Online</span></span>
    
  - <span data-ttu-id="fa873-146">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="fa873-146">Exchange Online</span></span>
    
  - <span data-ttu-id="fa873-147">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="fa873-147">Skype for Business</span></span>
    
- <span data-ttu-id="fa873-148">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="fa873-148">Microsoft Intune</span></span>
    
- <span data-ttu-id="fa873-149">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="fa873-149">Dynamics 365</span></span>
    
<span data-ttu-id="fa873-150">クライアント コンピューターに関して、以下の点を決定します。</span><span class="sxs-lookup"><span data-stu-id="fa873-150">For your client computers, determine the following:</span></span>
  
- <span data-ttu-id="fa873-151">同時に接続できる最大数 (時刻、季節、使用状況のピークと谷)</span><span class="sxs-lookup"><span data-stu-id="fa873-151">Maximum number at any one time (time of day, seasonal, peaks and troughs in usage)</span></span>
    
- <span data-ttu-id="fa873-152">ピーク時に必要な帯域幅の合計</span><span class="sxs-lookup"><span data-stu-id="fa873-152">Total bandwidth needed for peaks</span></span>
    
- <span data-ttu-id="fa873-153">インターネット出口デバイスの待機時間</span><span class="sxs-lookup"><span data-stu-id="fa873-153">Latency to the Internet egress device</span></span>
    
- <span data-ttu-id="fa873-154">元の国 vs. データセンター コロケーションの国</span><span class="sxs-lookup"><span data-stu-id="fa873-154">Country of origin vs. country of datacenter co-location</span></span>
    
<span data-ttu-id="fa873-155">各種のクライアント (PC、スマート フォン、タブレット) に関して、以下の現状を確認します。</span><span class="sxs-lookup"><span data-stu-id="fa873-155">For each type of client (PC, smartphone, tablet), ensure the current:</span></span>
  
- <span data-ttu-id="fa873-156">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="fa873-156">Operating system</span></span>
    
- <span data-ttu-id="fa873-157">インターネット ブラウザー</span><span class="sxs-lookup"><span data-stu-id="fa873-157">Internet browser</span></span>
    
- <span data-ttu-id="fa873-158">TCP/IP スタック</span><span class="sxs-lookup"><span data-stu-id="fa873-158">TCP/IP stack</span></span>
    
- <span data-ttu-id="fa873-159">ネットワーク ハードウェア</span><span class="sxs-lookup"><span data-stu-id="fa873-159">Network hardware</span></span>
    
- <span data-ttu-id="fa873-160">ネットワーク ハードウェアの OS ドライバー</span><span class="sxs-lookup"><span data-stu-id="fa873-160">OS drivers for network hardware</span></span>
    
- <span data-ttu-id="fa873-161">更新と修正プログラムがインストールされている</span><span class="sxs-lookup"><span data-stu-id="fa873-161">Updates and patches are installed</span></span>
    
<span data-ttu-id="fa873-162">さらに、イントラネット接続のスループット (有線、ワイヤレス、または VPN) を最適化します。</span><span class="sxs-lookup"><span data-stu-id="fa873-162">Additionally, optimize intranet connection throughput (wired, wireless, or VPN).</span></span>
  
<span data-ttu-id="fa873-163">詳細については、[Office 365 の NAT サポート](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fa873-163">For more information, see [NAT support with Office 365](https://support.office.com/article/NAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9).</span></span>
  
<span data-ttu-id="fa873-164">ExpressRoute with Office 365 の使用に関する最新の推奨事項については、「[Office 365 向け Azure ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fa873-164">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
<span data-ttu-id="fa873-165">イントラネットのパフォーマンスを最適化するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="fa873-165">To optimize your intranet performance, do the following:</span></span>
  
- <span data-ttu-id="fa873-166">ツールを使用して、インターネット エッジ デバイス (PsPing、Ping、Tracert、TraceTCP、ネットワーク モニター) へのラウンド トリップ時間(RTT) を計測します</span><span class="sxs-lookup"><span data-stu-id="fa873-166">Use tools to gauge round trip times (RTTs) to your Internet edge devices (PsPing, Ping, Tracert, TraceTCP, Network Monitor)</span></span>
    
- <span data-ttu-id="fa873-167">フロー プロトコルを使用して出口パスの解析を行います</span><span class="sxs-lookup"><span data-stu-id="fa873-167">Perform egress path analysis using flow protocols</span></span>
    
- <span data-ttu-id="fa873-168">中間デバイスの分析 (使用年数、正常性など) を実行します</span><span class="sxs-lookup"><span data-stu-id="fa873-168">Perform analysis of intermediate devices (age, health, etc.)</span></span>
    
<span data-ttu-id="fa873-169">詳細については、[PsPing ツール](https://technet.microsoft.com/sysinternals/jj729731.aspx) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa873-169">For more information, see the [PsPing tool](https://technet.microsoft.com/sysinternals/jj729731.aspx).</span></span>
  
## <a name="it-operations-considerations"></a><span data-ttu-id="fa873-170">IT 運用上の考慮事項</span><span class="sxs-lookup"><span data-stu-id="fa873-170">IT operations considerations</span></span>

<span data-ttu-id="fa873-171">Microsoft SaaS サービスで IT ワークロードを操作する場合の考慮事項を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="fa873-171">Here are some things to consider when operating an IT workload in a Microsoft SaaS service.</span></span>
  
### <a name="one-time-migrations"></a><span data-ttu-id="fa873-172">ワン タイム移行</span><span class="sxs-lookup"><span data-stu-id="fa873-172">One-time migrations</span></span>

<span data-ttu-id="fa873-173">ワン タイム移行の例としては、クラウド ベース アプリケーションまたはアーカイブ ストレージのための一括データ移行が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="fa873-173">Examples of one-time migrations are bulk data transfer for cloud-based applications or archival storage.</span></span>
  
<span data-ttu-id="fa873-174">ワン タイム移行のためにネットワークを最適化するには:</span><span class="sxs-lookup"><span data-stu-id="fa873-174">To optimize your network for on-time migrations:</span></span>
  
- <span data-ttu-id="fa873-175">ネットワーク使用状況のピーク時およびコンピューターのパッチ処理時を避けます</span><span class="sxs-lookup"><span data-stu-id="fa873-175">Avoid peak network usage and computer patching times</span></span>
    
- <span data-ttu-id="fa873-176">ベースラインおよびパイロットであるべきで、実際に移行する前にネットワークの正常性を評価し、問題を解決する必要があります</span><span class="sxs-lookup"><span data-stu-id="fa873-176">Should be baselined and piloted, assess network health and resolve issues before attempting actual migration</span></span>
    
- <span data-ttu-id="fa873-177">将来の移行のために事後分析を行います</span><span class="sxs-lookup"><span data-stu-id="fa873-177">Perform post-mortem for future migrations</span></span>
    
### <a name="ongoing-synchronizations"></a><span data-ttu-id="fa873-178">継続的な同期</span><span class="sxs-lookup"><span data-stu-id="fa873-178">Ongoing synchronizations</span></span>

<span data-ttu-id="fa873-179">継続的な同期の例として、ディレクトリ情報、設定、またはファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="fa873-179">Examples of ongoing synchronizations are directory information, settings, or files.</span></span>
  
<span data-ttu-id="fa873-180">継続的な同期のためにネットワークを最適化するには:</span><span class="sxs-lookup"><span data-stu-id="fa873-180">To optimize your network for ongoing synchronizations:</span></span>
  
- <span data-ttu-id="fa873-181">ネットワーク帯域幅監視システムが機能していることを確認し、収集したエラーを解決するか、消します</span><span class="sxs-lookup"><span data-stu-id="fa873-181">Ensure that a network bandwidth monitoring system is in place, resolve or dismiss collected errors</span></span>
    
- <span data-ttu-id="fa873-182">帯域幅監視の結果に基づいて、ネットワークの変更の必要性 (スケール アップまたはアウト、新しい回線、またはデバイスの追加) を判断します。</span><span class="sxs-lookup"><span data-stu-id="fa873-182">Use bandwidth monitoring results to determine need for network changes (scale-up/out, new circuits, or adding devices)</span></span>
    
<span data-ttu-id="fa873-183">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa873-183">For more information, see:</span></span>
  
- [<span data-ttu-id="fa873-184">Office 365 のネットワークと移行の計画</span><span class="sxs-lookup"><span data-stu-id="fa873-184">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="fa873-185">Office 365 のパフォーマンス管理 Microsoft Virtual Academy コース</span><span class="sxs-lookup"><span data-stu-id="fa873-185">Office 365 Performance Management Microsoft Virtual Academy course</span></span>](https://aka.ms/o365perf)
    
- [<span data-ttu-id="fa873-186">Office 365 用 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="fa873-186">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)

## <a name="next-step"></a><span data-ttu-id="fa873-187">次の手順</span><span class="sxs-lookup"><span data-stu-id="fa873-187">Next step</span></span>

[<span data-ttu-id="fa873-188">Microsoft Azure PaaS のためのネットワーク デザイン</span><span class="sxs-lookup"><span data-stu-id="fa873-188">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="fa873-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa873-189">See also</span></span>

[<span data-ttu-id="fa873-190">エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク</span><span class="sxs-lookup"><span data-stu-id="fa873-190">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="fa873-191">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="fa873-191">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="fa873-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span><span class="sxs-lookup"><span data-stu-id="fa873-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



