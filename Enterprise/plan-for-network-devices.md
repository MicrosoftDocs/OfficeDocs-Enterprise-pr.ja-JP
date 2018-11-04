---
title: Office 365 サービスに接続するネットワーク デバイスの計画
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 概要:Office 365 に接続するために使用されるネットワーク容量、WAN アクセラレータ、負荷分散装置に関する考慮事項について説明します。
ms.openlocfilehash: 023eb3f5ed4d81d1d49d18c69ef8c81032fd5851
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933124"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="2ef18-103">Office 365 サービスに接続するネットワーク デバイスの計画</span><span class="sxs-lookup"><span data-stu-id="2ef18-103">Plan for network devices that connect to Office 365 services</span></span>

 <span data-ttu-id="2ef18-104">**概要**:Office 365 に接続するために使用されるネットワーク容量、WAN アクセラレータ、負荷分散装置に関する考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ef18-104">**Summary**: Describes considerations for network capacity, WAN accelerators, and load balancing devices that are used to connect to Office 365.</span></span>
  
<span data-ttu-id="2ef18-p101">いくつかのネットワーク ハードウェアによっては、サポートされている同時セッションの数に制限があります。2,000 を超えるユーザーを持つ組織では、それらが他の Office 365 サービスのトラフィックを処理することを確認するようにネットワーク デバイスを監視するをお勧めします。簡易ネットワーク管理プロトコル (SNMP) 監視ソフトウェアは、この操作を行うのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2ef18-p101">Some network hardware may have limitations on the number of concurrent sessions that are supported. For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic. Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

||
|:-----|
| <span data-ttu-id="2ef18-108">この資料は、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://aka.ms/tune)の一部です。</span><span class="sxs-lookup"><span data-stu-id="2ef18-108">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

<span data-ttu-id="2ef18-p102">設置送信インターネット プロキシ設定は、クライアント アプリケーションで Office 365 サービスへの接続も影響します。マイクロソフトのクラウド サービスの Url とアプリケーションの接続を許可するネットワーク プロキシ デバイスを構成することもあります。すべての組織では異なります。準備マイクロソフトがこのプロセスおよび帯域幅の量を管理する方法を理解するため、[ケーススタディを読みます](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)。</span><span class="sxs-lookup"><span data-stu-id="2ef18-p102">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications. You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications. Every organization is different. To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="2ef18-113">次の Skype のビジネスに役立つ記事があるビジネス設定の Skype の詳細について。</span><span class="sxs-lookup"><span data-stu-id="2ef18-113">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="2ef18-114">管理者の Skype をビジネス オンラインのサインインのエラーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="2ef18-114">Troubleshooting Skype for Business Online sign-in errors for administrators</span></span>](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [<span data-ttu-id="2ef18-115">ビジネス用の Skype に接続できない場合や、オンプレミスのファイアウォールが接続をブロックするため、特定の機能は使用できません。</span><span class="sxs-lookup"><span data-stu-id="2ef18-115">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="2ef18-116">これらの設定の多くは、ビジネス固有の Skype です、ネットワークの構成に関する一般的なガイダンスはすべての Office 365 サービスに便利です。</span><span class="sxs-lookup"><span data-stu-id="2ef18-116">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="2ef18-117">ネットワーク キャパシティの決定</span><span class="sxs-lookup"><span data-stu-id="2ef18-117">Determining Network Capacity</span></span>

<span data-ttu-id="2ef18-p103">接続上に存在するすべてのネットワーク デバイスには、キャパシティの限界があります。このようなデバイスとしては、クライアントおよびサーバーのネットワーク アダプター、ルーター、スイッチ、それらを相互接続するハブなどがあります。適切なネットワーク キャパシティとは、これらのネットワーク デバイスのいずれもが過負荷にならないことです。ネットワーク アクティビティを監視することは、すべてのネットワーク デバイス上の実際の負荷が最大容量以下であることを確認するために不可欠です。ネットワーク容量は、プロキシ デバイスの性能に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="2ef18-p103">Every network device that exists on a connection has its capacity limit. These devices include the client and server network adapters, routers, switches, and hubs that interconnect them. Adequate network capacity means that none of them are saturated. Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity. Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="2ef18-p104">ほとんどの状況では、インターネット接続の帯域幅は、トラフィック量の制限を設定します。トラフィックのピーク時にパフォーマンスは、インターネット リンクの過度の使用による可能性があります。このような場合は、ブランチ オフィス シナリオでは、低速のワイド エリア ネットワーク (WAN) リンク経由でブランチ オフィスの本社にプロキシ デバイスにブランチ オフィスのプロキシ サーバー コンピューターが接続されているにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="2ef18-p104">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic. Weak performance during peak traffic hours is probably caused by excessive use of the Internet link. This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="2ef18-p105">ネットワーク容量をテストするには、プロキシのネットワーク インターフェイスのネットワーク活動を監視します。すべてのネットワーク インターフェイスの最大帯域幅の 75% 以上である場合が不適切なネットワーク インフラストラクチャの帯域幅を増やすことを検討してください。または、HTTP 圧縮などの高度な機能の使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="2ef18-p105">To test network capacity, monitor the network activity on the proxy network interface. If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate. Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="2ef18-129">WAN アクセラレータ</span><span class="sxs-lookup"><span data-stu-id="2ef18-129">WAN Accelerators</span></span>

<span data-ttu-id="2ef18-p106">組織は、ワイド エリア ネットワーク (WAN) アクセラレータ プロキシ ・ アプライアンスを使用して、Office 365 サービスにアクセスするときに問題が発生する可能性があります。または、ユーザーが Office 365 にアクセスするとき、一貫した機能できるようにするのにはの複数のネットワーク デバイスを最適化する必要があります。などの Office 365 サービスは、いくつかの Office 365 のコンテンツと TCP ヘッダーを暗号化します。デバイスは、このようなトラフィックを処理することがない場合があります。</span><span class="sxs-lookup"><span data-stu-id="2ef18-p106">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services. You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365. For example, Office 365 services encrypt some Office 365 content and the TCP header. Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="2ef18-134">[WAN 最適化コント ローラーの使用、または Office 365 とのトラフィックの検査とデバイス](https://support.microsoft.com/kb/2690045)に関するサポートの声明を読みます。</span><span class="sxs-lookup"><span data-stu-id="2ef18-134">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="2ef18-135">ハードウェアおよびソフトウェア負荷分散デバイス</span><span class="sxs-lookup"><span data-stu-id="2ef18-135">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="2ef18-p107">Active Directory フェデレーション サービス (AD FS) サーバーおよび/または Exchange ハイブリッド サーバーに対するリクエストを分散させるために、ハードウェア負荷分散 (HLB) またはネットワーク負荷分散 (NLB) ソリューションを使用する必要があります。負荷分散デバイスは社内サーバーへのネットワーク トラフィックを制御します。これらのサーバーはシングル サインオンおよび Exchange ハイブリッド展開の可用性を確保するうえで重要です。</span><span class="sxs-lookup"><span data-stu-id="2ef18-p107">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers. Load-balancing devices control the network traffic to the on-premises servers. These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="2ef18-p108">Windows Server に組み込まれたソフトウェア ・ ベースの NLB ソリューションを提供しています。Office 365 には、負荷分散を実現するには、このソリューションがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2ef18-p108">We provide a software-based NLB solution built into Windows Server. Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="2ef18-141">ファイアウォールとプロキシ</span><span class="sxs-lookup"><span data-stu-id="2ef18-141">Firewalls and proxies</span></span>

<span data-ttu-id="2ef18-142">ファイアウォール、およびデバイスと回路の選択に関する詳細については、 [Office 365 の管理の端点](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)、 [Office 365 へのネットワーク接続](network-connectivity.md)、および[Office 365 エンドポイントに関する FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)を参照して、Office 365 への接続にプロキシを設定する方法についての詳細については。</span><span class="sxs-lookup"><span data-stu-id="2ef18-142">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Network connectivity to Office 365](network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2ef18-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ef18-143">See also</span></span>

[<span data-ttu-id="2ef18-144">Office 365 サービスの展開アドバイザー</span><span class="sxs-lookup"><span data-stu-id="2ef18-144">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
