---
title: Office 365 エンドポイントの管理
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/22/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 99cab9d4-ef59-4207-9f2b-3728eb46bf9a
description: 一部のエンタープライズ ネットワークは、汎用のインターネット上の場所へのアクセスを制限またはかなり backhaul ネットワーク トラフィックの処理など。確認するのには、Office 365 にアクセスできる、ネットワークとプロキシの管理者は、Fqdn では、Url のリストを管理する必要があります、および IP アドレスなどのネットワーク上のコンピューターは、Office 365 エンドポイントの一覧を構成します。これらの必要性の直接ルート、プロキシ バイ パス、およびファイアウォール規則とネットワーク要求は、Office 365 にアクセスできないことを確認するのには、PAC ファイルに追加するには。
ms.openlocfilehash: a240e3deea512dacd70b377b3d47a7b6f49a235c
ms.sourcegitcommit: 7f1e19fb2d7a448a2dec73d8b2b4b82f851fb5f7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2018
ms.locfileid: "25697973"
---
# <a name="managing-office-365-endpoints"></a><span data-ttu-id="e45bd-105">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="e45bd-105">Managing Office 365 endpoints</span></span>

<span data-ttu-id="e45bd-p102">複数のオフィスと WAN 接続を持つほとんどの企業は、Office 365 のネットワーク接続を構成する必要がある必要があります。すべての信頼されたファイアウォールを使用して直接 Office 365 のネットワーク要求を送信する、すべての他のパケット レベルの検査をバイパスする処理では、ネットワークを最適化できます。これにより、レーテンシーを削減し、境界領域の容量要件を軽減します。Office 365 ユーザーのための最適なパフォーマンスを提供する最初の手順は、Office 365 のネットワーク トラフィックを識別します。Office 365 のネットワーク接続の詳細については、 [Office 365 のネットワーク接続性の原則](office-365-network-connectivity-principles.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p102">Most enterprise organizations that have multiple office locations and a connecting WAN will need to need to have configuration for Office 365 network connectivity. You can optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet level inspection or processing. This reduces latency and reduces your perimeter capacity requirements. Identifying Office 365 network traffic is the first step in providing optimal performance for your Office 365 users. For more information about Office 365 network connectivity, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md)</span></span>

<span data-ttu-id="e45bd-111">Office 365 のネットワークの端点とそれらを使用して[Office 365 の IP アドレスと Web サービスの URL](office-365-ip-web-service.md)への変更にアクセスするをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e45bd-111">Microsoft recommends you access the Office 365 network endpoints and changes to them using the [Office 365 IP Address and URL Web Services](office-365-ip-web-service.md)</span></span>

<span data-ttu-id="e45bd-p103">重要な Office 365 のネットワーク トラフィックを管理する方法に関係なく Office 365 には、インターネット接続が必要です。他のネットワーク エンドポイントの接続が必要な場所は、 [Office 365 の IP アドレスおよび URL の Web サービスに含まれないその他のエンドポイント](additional-office365-ip-addresses-and-urls.md)に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p103">Regardless of how you manage vital Office 365 network traffic, Office 365 requires Internet connectivity. Other network endpoints where connectivity is required are listed at [Additional endpoints not included in the Office 365 IP Address and URL Web service](additional-office365-ip-addresses-and-urls.md)</span></span>

<span data-ttu-id="e45bd-p104">Office 365 のネットワーク エンドポイントを使用する方法は、エンタープライズ組織のネットワーク アーキテクチャによって異なります。この資料では、エンタープライズ ネットワーク アーキテクチャは、Office 365 の IP アドレスや Url と統合可能ないくつかの方法を説明します。ネットワークを信頼するように要求を選択する最も簡単な方法では、各オフィスの所在地、自動的に Office 365 構成をサポートする SDWAN デバイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p104">How you use the Office 365 network endpoints will depend on your enterprise organization network architecture. This article outlines several ways that enterprise network architectures can integrate with Office 365 IP addresses and URLs. The easiest way to choose which network requests to trust is to use SDWAN devices that support automated Office 365 configuration at each of your office locations.</span></span> 

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a><span data-ttu-id="e45bd-117">重要な Office 365 のネットワーク トラフィックをローカルの分岐出口の SDWAN</span><span class="sxs-lookup"><span data-stu-id="e45bd-117">SDWAN for local branch egress of vital Office 365 network traffic</span></span>

<span data-ttu-id="e45bd-p105">各ブランチ オフィスの場所には、カテゴリの Office 365 の最適化または最適化のルートの IP アドレスに構成されている、SDWAN デバイスを提供し、マイクロソフトのネットワークに直接、カテゴリを許可します。大幅なネットワーク境界がある別の場所には、オンプレミス データ センターのトラフィック、汎用のインターネット web サイトのトラフィック、およびカテゴリのトラフィックを Office 365 の既定値を含むその他のネットワーク トラフィックが送信されます。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p105">At each branch office location, you can provide an SDWAN device which is configured to route IP Addresses for Office 365 Optimize category, or Optimize and Allow categories, directly to Microsoft's network. Other network traffic including on-premises datacenter traffic, generic internet web sites traffic, and Office 365 Default category traffic is sent to another location where you have a more substantial network perimeter.</span></span> 

<span data-ttu-id="e45bd-p106">マイクロソフトは自動構成を有効にする SDWAN のプロバイダーと協力します。確認できる[Office 365 ネットワーク パートナー ・ プログラム](office-365-networking-partner-program.md)に関する詳細</span><span class="sxs-lookup"><span data-stu-id="e45bd-p106">Microsoft is working with SDWAN providers to enable automated configuration. You can read further about the [Office 365 Networking Partner Program](office-365-networking-partner-program.md)</span></span>

<span data-ttu-id="e45bd-122"><a name="pacfiles"> </a></span><span class="sxs-lookup"><span data-stu-id="e45bd-122"></span></span>
## <a name="use-of-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a><span data-ttu-id="e45bd-123">Office 365 の重要なトラフィックの直接のルーティングのための PAC ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="e45bd-123">Use of a PAC file for direct routing of vital Office 365 traffic</span></span>

<span data-ttu-id="e45bd-p107">WPAD PAC ファイルを使用すると、Office 365 に関連付けられているが、提供されている IP アドレスがないネットワーク要求を管理できます。プロキシまたは境界デバイス経由で送信される一般的なネットワーク要求には、追加の遅延が発生します。SSL を解除し、検査は、最大の税を負担して、プロキシの認証や評価の検索などの他のサービスが、ユーザー エクスペリエンスの低下します。さらに、これらの境界ネットワーク デバイスには、すべてのネットワーク接続要求を処理するために十分な容量が必要があります。Office 365 のネットワーク要求を渡すため、プロキシや検査のインフラストラクチャをバイパスすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p107">Use PAC or WPAD files to manage network requests that are associated with Office 365 but don't have an IP address provided. Typical network requests that are sent through a proxy or perimeter device incur additional latency. While SSL Break and Inspect incurs the largest tax, other services such as proxy authentication and reputation lookup can cause a poor user experience. Additionally, these perimeter network devices need enough capacity to process all of the network connection requests. We recommend bypassing your proxy or inspection infrastructure for direct Office 365 network requests.</span></span>
  
<span data-ttu-id="e45bd-129">[PowerShell ギャラリー Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile)は、web サービスから最新のネットワーク エンドポイントを読み取るし、PAC ファイルのサンプルを作成する PowerShell スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="e45bd-129">[PowerShell Gallery Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) is a PowerShell script that reads the latest network endpoints from the web services and creates a sample PAC file.</span></span> 

<span data-ttu-id="e45bd-p108">このスクリプトをダウンロードするは、PAC ファイルの生成に使用できます。既存の PAC ファイルの管理を統合できるようにスクリプトを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p108">Once you download this script, you can use it to generate a PAC file. You can also modify the script so that it integrates with your existing PAC file management.</span></span> 

<span data-ttu-id="e45bd-p109">![ファイアウォールやプロキシ経由で Office 365 に接続します。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)図 1 - 単純な企業ネットワークのペリメータ</span><span class="sxs-lookup"><span data-stu-id="e45bd-p109">![Connecting to Office 365 through firewalls and proxies.](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png) Figure 1 - Simple enterprise network perimeter</span></span>

<span data-ttu-id="e45bd-p110">PAC ファイルは、図 1 の (1) の時点でコンピューターに配置されます。重要な Office 365 のネットワーク トラフィックの直接の出口の PAC ファイルを使用している場合は、ネットワーク境界部のファイアウォールでこれらの Url の背後にある IP アドレスへの接続を許可する必要があります。これには、同じ Office 365 エンドポイント内のカテゴリとして指定した PAC ファイルの IP アドレスの取得をし、これらのアドレスに基づいて、ファイアウォールの Acl を作成します。ファイアウォールは、図 1 の (3) をポイントするように表示されます。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p110">The PAC file is deployed to computers at point (1) in Figure 1. When using a PAC file for direct egress of vital Office 365 network traffic, you also need to allow connectivity to the IP addresses behind these URLs on your network perimeter firewall. This is done by fetching the IP addresses for the same Office 365 endpoint categories as specified in the PAC file and creating firewall ACLs based on those addresses. The firewall is shown as point (3) in Figure 1.</span></span> 

<span data-ttu-id="e45bd-p111">別にする場合は直接のみのルーティング、ネットワーク トラフィックのルーティング、最適化カテゴリ エンドポイントの場合、プロキシ サーバーに送信するカテゴリのエンドポイントはこれ以上の処理をバイパスするプロキシ サーバーに登録する必要があります、必要な許可をします。たとえば、SSL の区切りと検査およびプロキシ認証と互換性がない最適化および許可の両方のカテゴリのエンドポイントです。図 1 の (2) をポイントするようにプロキシ サーバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p111">Separately if you choose to only do direct routing for the route network traffic for the Optimize category endpoints, any required Allow category endpoints that you send to the proxy server will need to be listed in the proxy server to bypass further processing. For example, SSL break and Inspect and Proxy Authentication are incompatible with both the Optimize and Allow category endpoints. The proxy server is shown as point (2) in Figure 1.</span></span>

<span data-ttu-id="e45bd-p112">一般的な構成では、プロキシ サーバーをヒットする Office 365 のネットワーク トラフィックの宛先 IP アドレスは必須ではありませんように、プロキシ サーバーからすべての送信トラフィックを許可します。SSL を解除し[を使用するサードパーティ製のネットワーク デバイス](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)やソリューションを Office 365 のトラフィックの検査に関する問題の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p112">The common configuration is to permit all outbound traffic from the proxy server such that destination IP addresses for Office 365 network traffic that hits the proxy server is not required. Read about issues with SSL Break and Inspect at [Using third-party network devices or solutions on Office 365 traffic](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).</span></span>

<span data-ttu-id="e45bd-143">Get PacFile スクリプトを生成する PAC ファイルの 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="e45bd-143">There are two types of PAC files that the Get-PacFile script will generate.</span></span>

|<span data-ttu-id="e45bd-144">**種類**</span><span class="sxs-lookup"><span data-stu-id="e45bd-144">**Type**</span></span>|<span data-ttu-id="e45bd-145">**説明**</span><span class="sxs-lookup"><span data-stu-id="e45bd-145">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e45bd-146">**1**</span><span class="sxs-lookup"><span data-stu-id="e45bd-146">**1**</span></span> <br/> |<span data-ttu-id="e45bd-147">プロキシ サーバーに直接およびその他すべてのエンドポイントのトラフィックを最適化するを送信します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-147">Send Optimize endpoint traffic direct and all else to the proxy server.</span></span> <br/> |
|<span data-ttu-id="e45bd-148">**2**</span><span class="sxs-lookup"><span data-stu-id="e45bd-148">**2**</span></span> <br/> |<span data-ttu-id="e45bd-p113">最適化を送信し、直接またはプロキシ サーバーにその他すべて、エンドポイントのトラフィックを許可します。ExpressRoute ネットワーク セグメントおよびプロキシ サーバーを他のすべてのトラフィックを Office 365 の ExpressRoute がサポートされているすべての送信にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p113">Send Optimize and Allow endpoint traffic direct and all else to the proxy server. Can also be used to send all supported ExpressRoute for Office 365 traffic to ExpressRoute network segments and all else to the proxy server.</span></span> <br/> |

<span data-ttu-id="e45bd-151">PowerShell スクリプトを呼び出すための簡単な例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-151">Here's a simple example of calling the PowerShell script:</span></span>

```
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

<span data-ttu-id="e45bd-152">いくつかのパラメーターをスクリプトに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="e45bd-152">There are a number of parameters you can pass to the script:</span></span>

|<span data-ttu-id="e45bd-153">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="e45bd-153">**Parameter**</span></span>|<span data-ttu-id="e45bd-154">**説明**</span><span class="sxs-lookup"><span data-stu-id="e45bd-154">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e45bd-155">**ClientRequestId**</span><span class="sxs-lookup"><span data-stu-id="e45bd-155">**ClientRequestId**</span></span> <br/> |<span data-ttu-id="e45bd-156">これは、必要とは、呼び出し元のクライアント マシンを表す web サービスに渡される GUID</span><span class="sxs-lookup"><span data-stu-id="e45bd-156">This is required and is a GUID passed to the web service that represents the client machine making the call</span></span> <br/> |
|<span data-ttu-id="e45bd-157">**Instance**</span><span class="sxs-lookup"><span data-stu-id="e45bd-157">**Instance**</span></span> <br/> |<span data-ttu-id="e45bd-p114">世界の検索サイトにデフォルト設定されている Office 365 のサービス インスタンスです。Web サービスに渡すことも</span><span class="sxs-lookup"><span data-stu-id="e45bd-p114">The Office 365 service instance which defaults to Worldwide. Also passed to the web service</span></span> <br/> |
|<span data-ttu-id="e45bd-160">**TenantName**</span><span class="sxs-lookup"><span data-stu-id="e45bd-160">**TenantName**</span></span> <br/> |<span data-ttu-id="e45bd-p115">Office 365 テナントの名前です。Web サービスに渡され、いくつかの Office 365 の Url で置き換え可能パラメーターとして使用</span><span class="sxs-lookup"><span data-stu-id="e45bd-p115">Your Office 365 tenant name. Passed to the web service and used as a replaceable parameter in some Office 365 URLs</span></span> <br/> |
|<span data-ttu-id="e45bd-163">**種類**</span><span class="sxs-lookup"><span data-stu-id="e45bd-163">**Type**</span></span> <br/> |<span data-ttu-id="e45bd-164">生成するプロキシの PAC ファイルの種類</span><span class="sxs-lookup"><span data-stu-id="e45bd-164">The type of the proxy PAC file that you want to generate</span></span> <br/> |

<span data-ttu-id="e45bd-165">追加のパラメーターを PowerShell スクリプトの呼び出しの別の例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-165">Here's another example of calling the PowerShell script with additional parameters:</span></span>

```
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a><span data-ttu-id="e45bd-166">プロキシ サーバーは、Office 365 のネットワーク トラフィックの処理をバイパスします。</span><span class="sxs-lookup"><span data-stu-id="e45bd-166">Proxy server bypass processing of Office 365 network traffic</span></span> 

<span data-ttu-id="e45bd-p116">PAC ファイルは直接の発信トラフィック用には使用しない場合はか、プロキシ サーバーを構成することによって、ネットワーク境界部での処理をバイパスします。いくつかのプロキシ サーバーの製造元は、 [Office 365 のパートナー ネットワークのプログラム](office-365-networking-partner-program.md)の説明に従って、これを自動的に構成を有効にしています。これを手動で行う場合は、最適化を取得し、Office 365 の IP アドレスと URL の Web サービスからエンドポイントのエンドポイントのカテゴリ データを許可する、これらの処理をバイパスするプロキシ サーバーを構成する必要があります。最適化の SSL を解除し、検査とプロキシの認証を回避し、カテゴリの端点が重要です。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p116">Where PAC files are not used for direct outbound traffic, you will still want to bypass processing on your network perimeter by configuring your proxy server. Some proxy server vendors have enabled automated configuration of this as described in the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). If you are doing this manually you will need to obtain the Optimize and Allow endpoint category endpoint data from the Office 365 IP Address and URL Web Services and configure your proxy server to bypass processing for these. It is important to avoid SSL Break and Inspect and Proxy Authentication for the Optimize and Allow category endpoints.</span></span> 
  
<span data-ttu-id="e45bd-171"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="e45bd-171"></span></span>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a><span data-ttu-id="e45bd-172">Office 365 の IP アドレスや Url の変更管理</span><span class="sxs-lookup"><span data-stu-id="e45bd-172">Change management for Office 365 IP Addresses and URLs</span></span>

<span data-ttu-id="e45bd-p117">だけでなく、ネットワーク境界部の適切な構成を選択すると、Office 365 エンドポイントの変更管理プロセスを採用することが重要です。これらのエンドポイントを定期的に変更や変更を管理していない場合でブロックされているユーザー終了することができますアドレスまたは URL の追加で新しい ip アドレスの後のパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p117">In addition to selecting appropriate configuration for your network perimeter, it is critical that you adopt a change management process for Office 365 endpoints. These endpoints change regularly and if you do not manage the changes you can end up with users blocked or with poor performance after a new IP address or URL is added.</span></span> 

<span data-ttu-id="e45bd-p118">Office 365 の IP アドレスおよび Url の変更は通常、各月の最終日近く公開します。変更は、その運用のためのスケジュール、サポート、またはセキュリティの要件以外で公開されます。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p118">Changes to the Office 365 IP addresses and URLs are usually published near the last day of each month. Sometimes a change will be published outside of that schedule due to operational, support, or security requirements.</span></span>

<span data-ttu-id="e45bd-p119">IP アドレスまたは URL が追加されたので、アクションを実行する必要がある変更が公開されたら、そのエンドポイントが実際の Office 365 サービスに変更を公開しました時点から 30 日間の通知を受け取ることが予想されます。マイクロソフトでは、この通知期間の目的としていますがある可能性がありますいない常に運用が可能なサポート、またはセキュリティ要件。変更など、接続を維持するために即時の操作を必要としない IP アドレスまたは Url を削除するか、大幅な変更は、以下 [事前通知します。どのような通知を提供するに関係なく必要なサービスの有効日を変更するたびに私たちが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p119">When a change is published that requires you to take action because an IP address or URL was added, you should expect to receive 30 days notice from the time we published the change until there is live Office 365 service on that endpoint. Although Microsoft aims for this notification period, it may not always be possible due to operational, support, or security requirements. Changes that do not require immediate action to maintain connectivity, such as removed IP Addresses or URLs or less significant changes, do not include advance notification. Regardless of what notification is provided, we will list the expected service active date for each change.</span></span>

### <a name="change-notification-using-web-services"></a><span data-ttu-id="e45bd-181">Web サービスを使用して変更通知</span><span class="sxs-lookup"><span data-stu-id="e45bd-181">Change notification using web services</span></span>

<span data-ttu-id="e45bd-p120">Office 365 の IP アドレスを使用することができ、変更通知を取得する Web サービスの URL です。メソッドを呼び出すと/version web 1 時間に一度 Office 365 への接続を使用しているエンドポイントのバージョンを確認することをお勧めします。使用されているバージョンと比較するときにこのバージョンが変更された場合する必要があります web メソッド、/endpoints から最新のエンドポイントのデータを取得し、必要に応じて取得の違い、/changes から web メソッドです。見つかった場合、バージョンへの変更されていない場合、/endpoints または/changes の web メソッドを呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p120">You can use the Office 365 IP Address and URL Web Services to get change notification. We recommend you call the /version web method once an hour to check the version of the endpoints that you are using to connect to Office 365. If this version changes when compared to the version that you have in use, then you should get the latest endpoint data from the /endpoints web method and optionally get the differences from the /changes web method. It is not necessary to call the /endpoints or /changes web methods if there has not been any change to the version you found.</span></span> 

<span data-ttu-id="e45bd-186">詳細については、 [Office 365 の IP アドレスおよび URL の Web サービス](office-365-ip-web-service.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e45bd-186">For more information, see [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

### <a name="change-notification-using-rss-feeds"></a><span data-ttu-id="e45bd-187">RSS フィードを使用して変更通知</span><span class="sxs-lookup"><span data-stu-id="e45bd-187">Change notification using RSS feeds</span></span>

<span data-ttu-id="e45bd-p121">Office 365 の IP アドレスと Web サービスの URL は、RSS フィードのことができますを購読することで Outlook を提供します。Office 365 サービス インスタンス固有のページの IP アドレスごとに RSS の Url や Url へのリンクがあります。RSS フィード[Office 365 の IP アドレスおよび URL の Web サービス](office-365-ip-web-service.md)の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p121">The Office 365 IP Address and URL Web Services provide an RSS feed that you can subscribe to in Outlook. There are links to the RSS URLs on each of the Office 365 service instance specific pages for the IP addresses and URLs. The RSS feed is further described in the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a><span data-ttu-id="e45bd-191">変更通知と承認は、マイクロソフトのフローを使用してを確認します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-191">Change notification and approval review using Microsoft Flow</span></span>

<span data-ttu-id="e45bd-p122">私たちを理解する 1 か月で得られるネットワーク エンドポイントの変更の手動処理を要求することも可能性があります。マイクロソフトのフローを使用するには電子メールで通知して、Office 365 のネットワーク エンドポイントが行った変更と、必要に応じて変更の承認プロセスを実行するフローを作成します。レビューを完了すると、ファイアウォールとプロキシ サーバーの管理チームへの変更を自動的にメール フローを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p122">We understand that you might still require manual processing for network endpoint changes that come through each month. You can use Microsoft Flow to create a flow that notifies you by email and optionally runs an approval process for changes when Office 365 network endpoints have changes. Once review is completed, you can have the flow automatically email the changes to your firewall and proxy server management team.</span></span> 

<span data-ttu-id="e45bd-195">マイクロソフトのフローのサンプルとテンプレートを[使用してマイクロソフトは Office 365 の IP アドレスや Url の変更に電子メールを受信するのにはフロー](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-195">Read about the Microsoft Flow sample and template at [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)</span></span>
  
<span data-ttu-id="e45bd-196"><a name="FAQ"> </a></span><span class="sxs-lookup"><span data-stu-id="e45bd-196"></span></span>
## <a name="office-365-network-endpoints-faq"></a><span data-ttu-id="e45bd-197">Office 365 のネットワーク エンドポイントに関する FAQ</span><span class="sxs-lookup"><span data-stu-id="e45bd-197">Office 365 network endpoints FAQ</span></span>

<span data-ttu-id="e45bd-198">Office 365 の接続性に関する管理者のよく寄せられる質問:</span><span class="sxs-lookup"><span data-stu-id="e45bd-198">Frequently-asked administrator questions about Office 365 connectivity:</span></span>
  
### <a name="how-do-i-submit-a-question"></a><span data-ttu-id="e45bd-199">質問を送信する方法は?</span><span class="sxs-lookup"><span data-stu-id="e45bd-199">How do I submit a question?</span></span>

<span data-ttu-id="e45bd-p123">か、記事が役に立ちましたかどうかを示すために下部にあるリンクをクリックし、新たな質問を送信します。私たちは、フィードバックを監視し、最も頻繁に寄せられる質問をここで更新します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p123">Click the link at the bottom to indicate if the article was helpful or not and submit any additional questions. We monitor the feedback and update the questions here with the most frequently asked.</span></span>
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a><span data-ttu-id="e45bd-202">自分のテナントの場所を確認する方法はありますか</span><span class="sxs-lookup"><span data-stu-id="e45bd-202">How do I determine the location of my tenant?</span></span>

 <span data-ttu-id="e45bd-203">**テナントの場所**は、当社の[データ センターのマップ](http://aka.ms/datamaps)を使用して最適な決定されます。</span><span class="sxs-lookup"><span data-stu-id="e45bd-203">**Tenant location** is best determined using our [datacenter map](http://aka.ms/datamaps).</span></span>
  
### <a name="am-i-peering-appropriately-with-microsoft"></a><span data-ttu-id="e45bd-204">Am にピアリング適切にマイクロソフトのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="e45bd-204">Am I peering appropriately with Microsoft?</span></span>

 <span data-ttu-id="e45bd-205">**Peering の場所**については、[マイクロソフトとピアリング](https://www.microsoft.com/peering)で詳細に説明します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-205">**Peering locations** are described in more detail in [peering with Microsoft](https://www.microsoft.com/peering).</span></span>
  
<span data-ttu-id="e45bd-p124">2500 以上の ISP のピアリング関係を持つグローバルなプレゼンス、70 ポイントへのネットワークから取得する必要がありますシームレスです。ISP のピアリング関係では、最適です[ここでいくつかの例では](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/)良好ではだめですねピアリングのやり取りに当社のネットワークのことを確認する数分を費やすのも悪くないことはできません。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p124">With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) of good and not so good peering hand-offs to our network.</span></span> 
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a><span data-ttu-id="e45bd-208">発行済みの一覧にない IP アドレスへのネットワーク要求を表示すると、必要へのアクセスを提供するでしょうか。</span><span class="sxs-lookup"><span data-stu-id="e45bd-208">I see network requests to IP addresses not on the published list, do I need to provide access to them?</span></span>
<span data-ttu-id="e45bd-209"><a name="bkmk_MissingIP"> </a></span><span class="sxs-lookup"><span data-stu-id="e45bd-209"></span></span>

<span data-ttu-id="e45bd-p125">のみ IP アドレスを提供する Office 365 サーバーに直接ルーティングする必要があります。すべての IP アドレスのネットワーク要求が表示されますの包括的なリストではありません。Microsoft およびサード ・ パーティ製の所有している、パブリッシュされていない場合、IP アドレスへのネットワーク要求が表示されます。これらの IP アドレスが動的に生成されるかを変更するときに、タイムリーな通知を防止する方法で管理します。場合は、ファイアウォールでは、これらのネットワーク要求の Fqdn に基づいてアクセスを許可することはできません、要求を管理するために、PAC または WPAD ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p125">We only provide IP addresses for the Office 365 servers you should route directly to. This isn't a comprehensive list of all IP addresses you'll see network requests for. You will see network requests to Microsoft and third-party owned, unpublished, IP addresses. These IP addresses are dynamically generated or managed in a way that prevents timely notice when they change. If your firewall can't allow access based on the FQDNs for these network requests, use a PAC or WPAD file to manage the requests.</span></span>
  
<span data-ttu-id="e45bd-215">IP は、Office 365 の詳細情報を表示するに関連付けられているを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e45bd-215">See an IP associated with Office 365 that you want more information on?</span></span>
  
1. <span data-ttu-id="e45bd-216">[CIDR の電卓](http://jodies.de/ipcalc)を使用して大規模な公開されている範囲の IP アドレスが含まれているかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e45bd-216">Check if the IP address is included in a larger published range using a [CIDR calculator](http://jodies.de/ipcalc).</span></span>
2. <span data-ttu-id="e45bd-p126">パートナーが[whois クエリ](https://dnsquery.org/)を使用して ip アドレスを所有しているかどうかを参照してください。マイクロソフトが所有している場合は、内部の相手がある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p126">See if a partner owns the IP with a [whois query](https://dnsquery.org/). If it's Microsoft owned, it may be an internal partner.</span></span>
3. <span data-ttu-id="e45bd-p127">証明書をチェックし、IP アドレスへの接続をブラウザーで*HTTPS://\<と\>*、IP アドレスに関連付けられているどのようなドメインを理解する証明書に記載されているドメインを確認します。場合 IP アドレスを所有している Microsoft は、Office 365 の IP アドレスの一覧ではなく可能性があります IP アドレスは、公開されている IP 情報を使用しないで Microsoft ドメインまたは*MSOCDN.NET*などの Microsoft CDN に関連付けられます。証明書のドメインは、いずれかの IP アドレスの一覧を表示する要求は、行う場合は、知らせてください。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p127">Check the certificate, in a browser connect to the IP address using  *HTTPS://\<IP_ADDRESS\>*  , check the domains listed on the certificate to understand what domains are associated with the IP address. If it's a Microsoft owned IP address and not on the list of Office 365 IP addresses, it's likely the IP address is associated with a Microsoft CDN such as  *MSOCDN.NET*  or another Microsoft domain without published IP information. If you do find the domain on the certificate is one where we claim to list the IP address, please let us know.</span></span>

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a><span data-ttu-id="e45bd-222">Nsatc.net や akadns.net では、マイクロソフトのドメイン名などの名前を参照してください理由は?</span><span class="sxs-lookup"><span data-stu-id="e45bd-222">Why do I see names such as nsatc.net or akadns.net in the Microsoft domain names?</span></span>
<span data-ttu-id="e45bd-223"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="e45bd-223"></span></span>

<span data-ttu-id="e45bd-p128">Office 365 とその他の Microsoft サービスは、Office 365 のエクスペリエンスを向上させるために akamai 社、MarkMonitor などのいくつかのサードパーティのサービスを使用します。最高のエクスペリエンスを提供してください、可能な場合があります変更これらのサービス、将来的にします。操作中に、サード パーティのドメインを所有している、レコード、または IP アドレスを指す CNAME レコード多くの場合発行されます。サード パーティのドメインが、CDN などのコンテンツをホストまたは地理的なトラフィック管理サービスなどのサービスをホストすることがあります。これらのサード パーティへの接続が表示されたら、これらはリダイレクトまたは参照は、最初の要求で、クライアントからではないのです。一部のお客様がこのフォームを参照のことを確認する必要があり、潜在的な Fqdn でサード パーティのサービスの長いリストを使用して可能性がありますを明示的に追加せずにリダイレクトを許可します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p128">Office 365 and other Microsoft services use several third-party services such as Akamai and MarkMonitor to improve your Office 365 experience. To keep giving you the best experience possible, we may change these services in the future. In doing so, we often publish the CNAME record which points to a third party owned domain, A record, or IP address. Third party domains may host content, such as a CDN, or they may host a service, such as a geographical traffic management service. When you see connections to these third parties, they're in the form of a redirect or referral, not an initial request from the client. Some customers need to ensure this form of referral and redirection is allowed to pass without explicitly adding the long list of potential FQDNs third party services may use.</span></span>
  
<span data-ttu-id="e45bd-p129">サービスの一覧は、いつでも変更されることがします。現在使用中のサービスの一部は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p129">The list of services is subject to change at any time. Some of the services currently in use include:</span></span>
  
<span data-ttu-id="e45bd-p130">含む要求が表示されたら、 [MarkMonitor](https://www.markmonitor.com/)を使用中は*\*です。 nsatc.net* 。このサービスは、ドメイン名の保護、悪意のある行為から保護するための監視を提供します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p130">[MarkMonitor](https://www.markmonitor.com/) is in use when you see requests that include  *\*.nsatc.net*  . This service provides domain name protection and monitoring to protect against malicious behavior.</span></span>
  
<span data-ttu-id="e45bd-p131">要求が表示されたら、 [ExactTarget](https://www.marketingcloud.com/)を使用中は*\*です。 exacttarget.com* 。このサービスは、電子メールのリンクの管理し、悪意のある行為に対する監視を提供します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p131">[ExactTarget](https://www.marketingcloud.com/) is in use when you see requests to  *\*.exacttarget.com*  . This service provides email link management and monitoring against malicious behavior.</span></span>
  
<span data-ttu-id="e45bd-p132">[Akamai 社](https://www.akamai.com/)は、Fqdn を次のいずれかを含む要求が表示された場合、使用中です。このサービスでは、geo DNS、コンテンツ配信ネットワーク サービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p132">[Akamai](https://www.akamai.com/) is in use when you see requests that include one of the following FQDNs. This service offers geo-DNS and content delivery network services.</span></span>
  
```
*.akadns.net
*.akam.net
*.akamai.com
*.akamai.net
*.akamaiedge.net
*.akamaihd.net
*.akamaized.net
*.edgekey.net
*.edgesuite.net
```

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a><span data-ttu-id="e45bd-238">Office 365 の使用可能な最小の接続が必須であります。</span><span class="sxs-lookup"><span data-stu-id="e45bd-238">I have to have the minimum connectivity possible for Office 365</span></span>
<span data-ttu-id="e45bd-239"><a name="bkmk_thirdparty"> </a></span><span class="sxs-lookup"><span data-stu-id="e45bd-239"></span></span>

<span data-ttu-id="e45bd-p133">Office 365 は、一連のサービスをインターネット経由で機能するように構築、使用可能な多くの標準的なインターネット サービスに基づく信頼性と可用性の約束です。などの DNS、CRL、および Cdn などの標準のインターネット サービスは、最近のほとんどのインターネット サービスを使用して到達できる必要があると同様に、Office 365 を使用するのには到達可能でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p133">Office 365 is a suite of services built to function over the internet, the reliability and availability promises are based on many standard internet services being available. For example, standard internet services such as DNS, CRL, and CDNs must be reachable to use Office 365 just as they must be reachable to use most modern internet services.</span></span>

<span data-ttu-id="e45bd-p134">Office 365 製品ファミリは、主要なサービス エリアに分割します。これらが選択的に有効にする接続とすべての依存関係は、常に必要な一般的な領域があります。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p134">The Office 365 suite is broken down into major service areas. These can be selectively enabled for connectivity and there is a Common area which is a dependency for all and is always required.</span></span>

|<span data-ttu-id="e45bd-244">**サービス エリア**</span><span class="sxs-lookup"><span data-stu-id="e45bd-244">**Service Area**</span></span>|<span data-ttu-id="e45bd-245">**説明**</span><span class="sxs-lookup"><span data-stu-id="e45bd-245">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e45bd-246">**Exchange**</span><span class="sxs-lookup"><span data-stu-id="e45bd-246">**Exchange**</span></span> <br/> |<span data-ttu-id="e45bd-247">オンラインの Exchange および Exchange のオンライン保護</span><span class="sxs-lookup"><span data-stu-id="e45bd-247">Exchange Online and Exchange Online Protection</span></span> <br/> |
|<span data-ttu-id="e45bd-248">**SharePoint**</span><span class="sxs-lookup"><span data-stu-id="e45bd-248">**SharePoint**</span></span> <br/> |<span data-ttu-id="e45bd-249">SharePoint Online と OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="e45bd-249">SharePoint Online and OneDrive for Business</span></span> <br/> |
|<span data-ttu-id="e45bd-250">**Skype**</span><span class="sxs-lookup"><span data-stu-id="e45bd-250">**Skype**</span></span> <br/> |<span data-ttu-id="e45bd-251">Skype ビジネスおよびマイクロソフトのチーム</span><span class="sxs-lookup"><span data-stu-id="e45bd-251">Skype for Business and Microsoft Teams</span></span> <br/> |
|<span data-ttu-id="e45bd-252">**共通**</span><span class="sxs-lookup"><span data-stu-id="e45bd-252">**Common**</span></span> <br/> |<span data-ttu-id="e45bd-253">Office 365 Pro と、Office オンライン、Azure AD やその他の一般的なネットワーク ・ エンドポイント</span><span class="sxs-lookup"><span data-stu-id="e45bd-253">Office 365 Pro Plus, Office Online, Azure AD and other common network endpoints</span></span> <br/> |

<span data-ttu-id="e45bd-p135">基本的なインターネットのサービス、機能を統合するためにのみ使用されるサードパーティ製のサービスがあります。これらが統合に必要なときに、サービスのコア機能は、エンドポイントがアクセス可能でない場合で機能しますが、Office 365 エンドポイントの資料では省略可能としてマークしています。必要なすべてのネットワーク エンドポイントが必要な属性が true に設定します。省略可能なすべてのネットワーク エンドポイントは必須の属性が false に設定があり、ノートの属性は接続がブロックされているかどうかを想定する必要があります不足している機能の詳細を。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p135">In addition to basic internet services, there are third-party services that are only used to integrate functionality. While these are needed for integration, they're marked as optional in the Office 365 endpoints article which means core functionality of the service will continue to function if the endpoint isn't accessible. Any network endpoint which is required will have the required attribute set to true. Any network endpoint which is optional will have the required attribute set to false and the notes attribute will detail the missing functionality you should expect if connectivity is blocked.</span></span>
  
<span data-ttu-id="e45bd-258">Office 365 を使用しようとするいるし、サードパーティのサービスにアクセスできない検索が[必須であるか、またはこの資料では省略可能にマークされているすべての Fqdn はプロキシとファイアウォールを通過できる](urls-and-ip-address-ranges.md)ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="e45bd-258">If you're attempting to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a><span data-ttu-id="e45bd-259">マイクロソフトのコンシューマー サービスへのアクセスをブロックする方法は?</span><span class="sxs-lookup"><span data-stu-id="e45bd-259">How do I block access to Microsoft's consumer services?</span></span>
<span data-ttu-id="e45bd-260"><a name="bkmk_consumer"> </a></span><span class="sxs-lookup"><span data-stu-id="e45bd-260"></span></span>

<span data-ttu-id="e45bd-p136">自己の責任において、消費者サービスへのアクセス制限を行う必要があります、コンシューマー サービスをブロックする唯一確実な方法は、 *login.live.com* FQDN へのアクセスを制限します。この FQDN は、MSDN、TechNet、およびその他のユーザーなどの非消費者サービスなどのサービスの広範なセットで使用されます。この FQDN へのアクセスを制限するもこれらのサービスに関連付けられているネットワークの要求のルールの例外を含める必要がある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e45bd-p136">Restricting access to our consumer services should be done at your own risk, the only reliable way to block consumer services is to restrict access to the  *login.live.com*  FQDN. This FQDN is used by a broad set of services including non-consumer services such as MSDN, TechNet, and others. Restricting access to this FQDN may result in the need to also include exceptions to the rule for network requests associated with these services.</span></span>
  
<span data-ttu-id="e45bd-264">Exfiltrate については、Office 365 テナントまたはその他のサービスを使用するネットワーク上の他のユーザーの Microsoft コンシューマー サービスだけにアクセスをブロックしない機能しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="e45bd-264">Keep in mind that blocking access to the Microsoft consumer services alone won't prevent the ability for someone on your network to exfiltrate information using an Office 365 tenant or other service.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="e45bd-265">関連トピック</span><span class="sxs-lookup"><span data-stu-id="e45bd-265">Related Topics</span></span>

[<span data-ttu-id="e45bd-266">Office 365 IP アドレスと URL の Web サービス </span><span class="sxs-lookup"><span data-stu-id="e45bd-266">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="e45bd-267">Microsoft Azure データ センターの IP 範囲</span><span class="sxs-lookup"><span data-stu-id="e45bd-267">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="e45bd-268">Microsoft パブリック IP スペース</span><span class="sxs-lookup"><span data-stu-id="e45bd-268">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
  
[<span data-ttu-id="e45bd-269">Microsoft Intune のネットワーク インフラストラクチャの要件</span><span class="sxs-lookup"><span data-stu-id="e45bd-269">Network infrastructure requirements for Microsoft Intune</span></span>](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[<span data-ttu-id="e45bd-270">電源の BI および ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="e45bd-270">Power BI and ExpressRoute</span></span>](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[<span data-ttu-id="e45bd-271">Office 365 の URL と IP アドレス範囲</span><span class="sxs-lookup"><span data-stu-id="e45bd-271">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)
  
[<span data-ttu-id="e45bd-272">Office 365 向け ExpressRoute の管理</span><span class="sxs-lookup"><span data-stu-id="e45bd-272">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="e45bd-273">Office 365 ネットワーク接続の原則</span><span class="sxs-lookup"><span data-stu-id="e45bd-273">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)
