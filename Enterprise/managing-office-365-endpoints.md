---
title: Office 365 エンドポイントの管理
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/11/2019
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
description: 一部のエンタープライズネットワークは、一般的なインターネットの場所へのアクセスを制限するか、またはネットワークトラフィックの処理を大幅に行います。このようなネットワーク上のコンピューターが office 365 にアクセスできるようにするには、ネットワークおよびプロキシ管理者が、office 365 エンドポイントの一覧を構成する fqdn、url、IP アドレスの一覧を管理する必要があります。ネットワーク要求が Office 365 に到達できるようにするには、これらのルールを直接ルート、プロキシバイパス、またはファイアウォールルールおよび PAC ファイルに追加する必要があります。
ms.openlocfilehash: ed3a64ad3cd840987d105ae99a5ba5cbf41567e9
ms.sourcegitcommit: a8aedcfe0d6a6047a622fb3f68278c81c1e413bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "30053001"
---
# <a name="managing-office-365-endpoints"></a><span data-ttu-id="8ee6e-105">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="8ee6e-105">Managing Office 365 endpoints</span></span>

<span data-ttu-id="8ee6e-p102">複数のオフィスの場所を持ち、WAN を接続する多くの企業組織では、office 365 のネットワーク接続の構成が必要です。すべての信頼された Office 365 ネットワーク要求をファイアウォール経由で直接送信することにより、ネットワークを最適化することができます。これには、追加のすべてのパケットレベルの検査または処理を省略しますこれにより、遅延と境界容量の要件が減少します。Office 365 のネットワークトラフィックを特定することは、ユーザーに最適なパフォーマンスを提供するための最初の手順です。office 365 のネットワーク接続の詳細については、「 [office 365 のネットワーク接続の原則](office-365-network-connectivity-principles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p102">Most enterprise organizations that have multiple office locations and a connecting WAN will need to need configuration for Office 365 network connectivity. You can optimize your network by sending all trusted Office 365 network requests directly through your firewall, bypassing all additional packet level inspection or processing. This reduces latency and your perimeter capacity requirements. Identifying Office 365 network traffic is the first step in providing optimal performance for your users. For more information about Office 365 network connectivity, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md)</span></span>

<span data-ttu-id="8ee6e-111">office 365 ネットワークエンドポイントにアクセスして、 [office 365 の IP アドレスと URL Web サービス](office-365-ip-web-service.md)を使用して変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-111">Microsoft recommends you access the Office 365 network endpoints and changes to them using the [Office 365 IP Address and URL Web Service](office-365-ip-web-service.md)</span></span>

<span data-ttu-id="8ee6e-p103">office 365 の重要なネットワークトラフィックを管理する方法に関係なく、office 365 ではインターネット接続が必要です。接続が必要なその他のネットワークエンドポイントは[、Office 365 の IP アドレスと URL Web サービスに含まれていない追加のエンドポイント](additional-office365-ip-addresses-and-urls.md)に一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p103">Regardless of how you manage vital Office 365 network traffic, Office 365 requires Internet connectivity. Other network endpoints where connectivity is required are listed at [Additional endpoints not included in the Office 365 IP Address and URL Web service](additional-office365-ip-addresses-and-urls.md)</span></span>

<span data-ttu-id="8ee6e-p104">Office 365 のネットワークエンドポイントの使用方法は、エンタープライズ組織のネットワークアーキテクチャによって異なります。この記事では、エンタープライズネットワークアーキテクチャが Office 365 の IP アドレスと url と統合できるいくつかの方法について説明します。信頼するネットワーク要求を選択する最も簡単な方法は、各オフィスの場所で自動 Office 365 構成をサポートする sdwan デバイスを使用することです。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p104">How you use the Office 365 network endpoints will depend on your enterprise organization network architecture. This article outlines several ways that enterprise network architectures can integrate with Office 365 IP addresses and URLs. The easiest way to choose which network requests to trust is to use SDWAN devices that support automated Office 365 configuration at each of your office locations.</span></span> 

## <a name="sdwan-for-local-branch-egress-of-vital-office-365-network-traffic"></a><span data-ttu-id="8ee6e-117">重要な Office 365 ネットワークトラフィックのローカルブランチ出口の sdwan</span><span class="sxs-lookup"><span data-stu-id="8ee6e-117">SDWAN for local branch egress of vital Office 365 network traffic</span></span>

<span data-ttu-id="8ee6e-p105">各支社の場所には、office 365 の [エンドポイントの最適化] カテゴリのトラフィックをルーティングするように構成された sdwan デバイス、または Microsoft のネットワークに直接カテゴリを最適化して許可することができます。オンプレミスのデータセンタートラフィック、一般的なインターネット web サイトトラフィック、および Office 365 へのトラフィックを含むその他のネットワークトラフィックには、より大きなネットワーク境界を持つ別の場所に送信されます。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p105">At each branch office location, you can provide an SDWAN device that is configured to route traffic for Office 365 Optimize category of endpoints, or Optimize and Allow categories, directly to Microsoft's network. Other network traffic including on-premises datacenter traffic, general Internet web sites traffic, and traffic to Office 365 Default category endpoints is sent to another location where you have a more substantial network perimeter.</span></span>

<span data-ttu-id="8ee6e-p106">Microsoft は、自動構成を有効にするために sdwan プロバイダーと協力しています。詳細については、「 [Office 365 のネットワーキングパートナープログラム](office-365-networking-partner-program.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p106">Microsoft is working with SDWAN providers to enable automated configuration. For more information, see [Office 365 Networking Partner Program](office-365-networking-partner-program.md).</span></span>

<span data-ttu-id="8ee6e-122"><a name="pacfiles"> </a></span><span class="sxs-lookup"><span data-stu-id="8ee6e-122"></span></span>
## <a name="use-a-pac-file-for-direct-routing-of-vital-office-365-traffic"></a><span data-ttu-id="8ee6e-123">重要な Office 365 トラフィックの直接ルーティングに PAC ファイルを使用する</span><span class="sxs-lookup"><span data-stu-id="8ee6e-123">Use a PAC file for direct routing of vital Office 365 traffic</span></span>

<span data-ttu-id="8ee6e-p107">PAC または WPAD ファイルを使用して、Office 365 に関連付けられているが IP アドレスを持っていないネットワーク要求を管理します。プロキシまたは境界デバイス経由で送信される一般的なネットワーク要求は、待機時間が増加します。SSL ブレークと調査によって最大の待機時間が作成されますが、プロキシ認証や評価の参照などのサービスによって、パフォーマンスが低下し、ユーザーの作業が正しくない可能性があります。さらに、これらの境界ネットワークデバイスには、すべてのネットワーク接続要求を処理するのに十分な容量が必要です。ダイレクト Office 365 のネットワーク要求には、プロキシまたは検査デバイスをバイパスすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p107">Use PAC or WPAD files to manage network requests that are associated with Office 365 but don't have an IP address. Typical network requests that are sent through a proxy or perimeter device increase latency. While SSL Break and Inspect creates the largest latency, other services such as proxy authentication and reputation lookup can cause poor performance and a bad user experience. Additionally, these perimeter network devices need enough capacity to process all of the network connection requests. We recommend bypassing your proxy or inspection devices for direct Office 365 network requests.</span></span>
  
<span data-ttu-id="8ee6e-p108">[powershell Gallery の Get-pacfile](https://www.powershellgallery.com/packages/Get-PacFile)は powershell スクリプトで、Office 365 の IP アドレスと URL Web サービスから最新のネットワークエンドポイントを読み取り、サンプル PAC ファイルを作成します。スクリプトを変更して、既存の PAC ファイル管理と統合できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p108">[PowerShell Gallery Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) is a PowerShell script that reads the latest network endpoints from the Office 365 IP Address and URL Web service and creates a sample PAC file. You can modify the script so that it integrates with your existing PAC file management.</span></span> 

![ファイアウォールとプロキシを介して Office 365 に接続します。](media/34d402f3-f502-42a0-8156-24a7c4273fa5.png)

<span data-ttu-id="8ee6e-132">**図 1-単純なエンタープライズネットワーク境界**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-132">**Figure 1 - Simple enterprise network perimeter**</span></span>

<span data-ttu-id="8ee6e-p109">PAC ファイルは、図1のポイント1の web ブラウザーに展開されます。重要な Office 365 ネットワークトラフィックの直接出口に PAC ファイルを使用する場合は、ネットワーク境界ファイアウォール上のこれらの url の背後にある IP アドレスへの接続も許可する必要があります。これは、PAC ファイルで指定されているものと同じ Office 365 エンドポイントカテゴリの IP アドレスを取得し、それらのアドレスに基づいてファイアウォール acl を作成することによって行われます。ファイアウォールは図1のポイント3です。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p109">The PAC file is deployed to web browsers at point 1 in Figure 1. When using a PAC file for direct egress of vital Office 365 network traffic, you also need to allow connectivity to the IP addresses behind these URLs on your network perimeter firewall. This is done by fetching the IP addresses for the same Office 365 endpoint categories as specified in the PAC file and creating firewall ACLs based on those addresses. The firewall is point 3 in Figure 1.</span></span> 

<span data-ttu-id="8ee6e-p110">別の方法として、最適化カテゴリエンドポイントに対して直接ルーティングのみを選択した場合は、プロキシサーバーに送信する必要のある許可カテゴリエンドポイントがプロキシサーバーに表示され、それ以降の処理をバイパスする必要があります。たとえば、SSL ブレーク、検査、プロキシ認証は、[最適化] および [許可] カテゴリエンドポイントと互換性がありません。プロキシサーバーは図1のポイント2です。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p110">Separately if you choose to only do direct routing for the Optimize category endpoints, any required Allow category endpoints that you send to the proxy server will need to be listed in the proxy server to bypass further processing. For example, SSL break and Inspect and Proxy Authentication are incompatible with both the Optimize and Allow category endpoints. The proxy server is point 2 in Figure 1.</span></span>

<span data-ttu-id="8ee6e-p111">一般的な構成では、プロキシサーバーにヒットする Office 365 ネットワークトラフィックの宛先 IP アドレスについて、プロキシサーバーからのすべての送信トラフィックを処理することなく許可されます。SSL ブレークおよび検査に関する問題の詳細については、「 [Office 365 でサードパーティ製のネットワークデバイスまたはソリューションを使用する](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p111">The common configuration is to permit without processing all outbound traffic from the proxy server for the destination IP addresses for Office 365 network traffic that hits the proxy server. For information about issues with SSL Break and Inspect, see [Using third-party network devices or solutions on Office 365 traffic](https://support.microsoft.com/en-us/help/2690045/using-third-party-network-devices-or-solutions-with-office-365).</span></span>

<span data-ttu-id="8ee6e-142">pacfile スクリプトによって生成される PAC ファイルには、次の2種類があります。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-142">There are two types of PAC files that the Get-PacFile script will generate.</span></span>

|<span data-ttu-id="8ee6e-143">**型**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-143">**Type**</span></span>|<span data-ttu-id="8ee6e-144">**説明**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-144">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8ee6e-145">**1**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-145">**1**</span></span> <br/> |<span data-ttu-id="8ee6e-146">プロキシサーバーに対して、最適化エンドポイントトラフィックの直接送信およびその他すべてを送信します。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-146">Send Optimize endpoint traffic direct and everything else to the proxy server.</span></span> <br/> |
|<span data-ttu-id="8ee6e-147">**2**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-147">**2**</span></span> <br/> |<span data-ttu-id="8ee6e-p112">[最適化] および [エンドポイントのトラフィックを直接送信する] およびその他のすべてのプロキシサーバーを送信します。この型を使用して、Office 365 トラフィックに対してサポートされているすべての expressroute を expressroute ネットワークセグメントに、その他すべてをプロキシサーバーに送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p112">Send Optimize and Allow endpoint traffic direct and everything else to the proxy server. This type can also be used to send all supported ExpressRoute for Office 365 traffic to ExpressRoute network segments and everything else to the proxy server.</span></span> <br/> |

<span data-ttu-id="8ee6e-150">次に、PowerShell スクリプトを呼び出す簡単な例を示します。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-150">Here's a simple example of calling the PowerShell script:</span></span>

```
Get-PacFile -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7
```

<span data-ttu-id="8ee6e-151">スクリプトに渡すことのできるパラメーターはいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-151">There are a number of parameters you can pass to the script:</span></span>

|<span data-ttu-id="8ee6e-152">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-152">**Parameter**</span></span>|<span data-ttu-id="8ee6e-153">**説明**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-153">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8ee6e-154">**ClientRequestId**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-154">**ClientRequestId**</span></span> <br/> |<span data-ttu-id="8ee6e-155">これは必須であり、呼び出しを行うクライアントコンピューターを表す web サービスに渡される GUID です。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-155">This is required and is a GUID passed to the web service that represents the client machine making the call.</span></span> <br/> |
|<span data-ttu-id="8ee6e-156">**Instance**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-156">**Instance**</span></span> <br/> |<span data-ttu-id="8ee6e-p113">既定では、Office 365 service インスタンスが世界に設定されています。web サービスにも渡されます。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p113">The Office 365 service instance which defaults to Worldwide. Also passed to the web service.</span></span> <br/> |
|<span data-ttu-id="8ee6e-159">**TenantName**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-159">**TenantName**</span></span> <br/> |<span data-ttu-id="8ee6e-p114">Office 365 テナント名。web サービスに渡され、一部の Office 365 の url で置き換え可能なパラメーターとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p114">Your Office 365 tenant name. Passed to the web service and used as a replaceable parameter in some Office 365 URLs.</span></span> <br/> |
|<span data-ttu-id="8ee6e-162">**型**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-162">**Type**</span></span> <br/> |<span data-ttu-id="8ee6e-163">生成するプロキシ PAC ファイルの種類。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-163">The type of the proxy PAC file that you want to generate.</span></span> <br/> |

<span data-ttu-id="8ee6e-164">追加のパラメーターを使用して PowerShell スクリプトを呼び出す別の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-164">Here's another example of calling the PowerShell script with additional parameters.</span></span>

```
Get-PacFile -Type 2 -Instance Worldwide -TenantName Contoso -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 
```

## <a name="proxy-server-bypass-processing-of-office-365-network-traffic"></a><span data-ttu-id="8ee6e-165">Office 365 ネットワークトラフィックのプロキシサーバーのバイパス処理</span><span class="sxs-lookup"><span data-stu-id="8ee6e-165">Proxy server bypass processing of Office 365 network traffic</span></span> 

<span data-ttu-id="8ee6e-p115">PAC ファイルが直接送信トラフィックに使用されていない場合でも、プロキシサーバーを構成してネットワーク境界での処理をバイパスする必要があります。プロキシサーバーのベンダーによっては、 [Office 365 ネットワークパートナープログラム](office-365-networking-partner-program.md)で説明されているように、この機能の自動構成が有効になっている場合があります。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p115">Where PAC files are not used for direct outbound traffic, you still want to bypass processing on your network perimeter by configuring your proxy server. Some proxy server vendors have enabled automated configuration of this as described in the [Office 365 Networking Partner Program](office-365-networking-partner-program.md).</span></span> 

<span data-ttu-id="8ee6e-p116">これを手動で実行する場合は、Office 365 の IP アドレスと URL Web サービスから、[最適化] と [エンドポイントのカテゴリ] データを取得し、これらの処理をバイパスするようにプロキシサーバーを構成する必要があります。SSL ブレークを回避し、カテゴリエンドポイントの最適化と許可の認証とプロキシ認証を行うことが重要です。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p116">If you are doing this manually you will need to get the Optimize and Allow endpoint category data from the Office 365 IP Address and URL Web Service and configure your proxy server to bypass processing for these. It is important to avoid SSL Break and Inspect and Proxy Authentication for the Optimize and Allow category endpoints.</span></span> 
  
<span data-ttu-id="8ee6e-170"><a name="bkmk_changes"> </a></span><span class="sxs-lookup"><span data-stu-id="8ee6e-170"></span></span>
## <a name="change-management-for-office-365-ip-addresses-and-urls"></a><span data-ttu-id="8ee6e-171">Office 365 の IP アドレスおよび url の変更管理</span><span class="sxs-lookup"><span data-stu-id="8ee6e-171">Change management for Office 365 IP addresses and URLs</span></span>

<span data-ttu-id="8ee6e-p117">ネットワーク境界に適切な構成を選択することに加えて、Office 365 エンドポイントの変更管理プロセスを採用することが重要です。これらのエンドポイントは定期的に変更され、変更を管理していない場合は、新しい IP アドレスまたは URL が追加された後にユーザーがブロックされたり、パフォーマンスが低下したりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p117">In addition to selecting appropriate configuration for your network perimeter, it is critical that you adopt a change management process for Office 365 endpoints. These endpoints change regularly and if you do not manage the changes, you can end up with users blocked or with poor performance after a new IP address or URL is added.</span></span> 

<span data-ttu-id="8ee6e-p118">Office 365 の IP アドレスと url への変更は、通常、毎月の最終日付近に公開されます。運用、サポート、またはセキュリティ要件によって、そのスケジュールの外部で変更が公開されることがあります。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p118">Changes to the Office 365 IP addresses and URLs are usually published near the last day of each month. Sometimes a change will be published outside of that schedule due to operational, support, or security requirements.</span></span>

<span data-ttu-id="8ee6e-p119">IP アドレスまたは URL が追加されたために処理を必要とする変更が公開されている場合は、そのエンドポイントに Office 365 サービスが存在するまで、変更を公開するまでに30日の通知が表示されるはずです。この通知期間を対象としていますが、運用、サポート、またはセキュリティの要件によっては常に可能であるとは限りません。削除された IP アドレスや url、重要な変更の削減など、直ちに接続を維持する必要がない変更には、事前通知は含まれません。通知の種類に関係なく、各変更に対して予想されるサービスのアクティブな日付を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p119">When a change is published that requires you to act because an IP address or URL was added, you should expect to receive 30 days notice from the time we publish the change until there is an Office 365 service on that endpoint. Although we aim for this notification period, it may not always be possible due to operational, support, or security requirements. Changes that do not require immediate action to maintain connectivity, such as removed IP addresses or URLs or less significant changes, do not include advance notification. Regardless of what notification is provided, we list the expected service active date for each change.</span></span>

### <a name="change-notification-using-the-web-service"></a><span data-ttu-id="8ee6e-180">Web サービスを使用して通知を変更する</span><span class="sxs-lookup"><span data-stu-id="8ee6e-180">Change notification using the Web Service</span></span>

<span data-ttu-id="8ee6e-p120">Office 365 の IP アドレスと URL Web サービスを使用して、変更通知を取得することができます。Office 365 への接続に使用しているエンドポイントのバージョンを確認するには、 **/version** web メソッドを1時間ごとに呼び出すことをお勧めします。使用しているバージョンと比較してこのバージョンが変更された場合は、 **/エンドポイント**web メソッドから最新のエンドポイントデータを取得し、必要に応じて**変更/変更**web メソッドとの相違点を取得する必要があります。検索したバージョンが変更されていない場合は、/**エンドポイント**または **/変更**web メソッドを呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p120">You can use the Office 365 IP Address and URL Web Service to get change notification. We recommend you call the **/version** web method once an hour to check the version of the endpoints that you are using to connect to Office 365. If this version changes when compared to the version that you have in use, then you should get the latest endpoint data from the **/endpoints** web method and optionally get the differences from the **/changes** web method. It is not necessary to call the **/endpoints** or **/changes** web methods if there has not been any change to the version you found.</span></span> 

<span data-ttu-id="8ee6e-185">詳細については、「 [Office 365 の IP アドレスと URL Web サービス](office-365-ip-web-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-185">For more information, see [Office 365 IP Address and URL Web Service](office-365-ip-web-service.md).</span></span>

### <a name="change-notification-using-rss-feeds"></a><span data-ttu-id="8ee6e-186">RSS フィードを使用した変更通知</span><span class="sxs-lookup"><span data-stu-id="8ee6e-186">Change notification using RSS feeds</span></span>

<span data-ttu-id="8ee6e-p121">Office 365 の IP アドレスと URL Web サービスには、Outlook で購読できる RSS フィードが用意されています。各 Office 365 サービスインスタンス固有のページに、IP アドレスと url に関する RSS url へのリンクがあります。詳細については、「 [Office 365 の IP アドレスと URL Web サービス](office-365-ip-web-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p121">The Office 365 IP Address and URL Web Service provides an RSS feed that you can subscribe to in Outlook. There are links to the RSS URLs on each of the Office 365 service instance-specific pages for the IP addresses and URLs. For more information, see [Office 365 IP Address and URL Web Service](office-365-ip-web-service.md).</span></span>

### <a name="change-notification-and-approval-review-using-microsoft-flow"></a><span data-ttu-id="8ee6e-190">Microsoft Flow を使用して通知と承認レビューを変更する</span><span class="sxs-lookup"><span data-stu-id="8ee6e-190">Change notification and approval review using Microsoft Flow</span></span>

<span data-ttu-id="8ee6e-p122">各月に発生するネットワークエンドポイントの変更については、手動での処理が必要になる可能性があることを理解しています。Microsoft flow を使用して、電子メールで通知するフローを作成できます。 Office 365 ネットワークエンドポイントが変更されたときに、必要に応じて変更の承認プロセスを実行することもできます。レビューが完了すると、そのフローによって、ファイアウォールとプロキシサーバーの管理チームへの変更が自動的に電子メールで送信されるようになります。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p122">We understand that you might still require manual processing for network endpoint changes that come through each month. You can use Microsoft Flow to create a flow that notifies you by email and optionally runs an approval process for changes when Office 365 network endpoints have changes. Once review is completed, you can have the flow automatically email the changes to your firewall and proxy server management team.</span></span> 

<span data-ttu-id="8ee6e-194">microsoft flow のサンプルとテンプレートについては、「 [microsoft flow を使用して Office 365 の IP アドレスおよび url の変更に関する電子メールを受信する](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-194">For information about a Microsoft Flow sample and template, see [Use Microsoft Flow to receive an email for changes to Office 365 IP addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/td-p/240651)</span></span>
  
<span data-ttu-id="8ee6e-195"><a name="FAQ"> </a></span><span class="sxs-lookup"><span data-stu-id="8ee6e-195"></span></span>
## <a name="office-365-network-endpoints-faq"></a><span data-ttu-id="8ee6e-196">Office 365 ネットワークエンドポイントに関する FAQ</span><span class="sxs-lookup"><span data-stu-id="8ee6e-196">Office 365 network endpoints FAQ</span></span>

<span data-ttu-id="8ee6e-197">Office 365 の接続に関してよく寄せられる管理者の質問:</span><span class="sxs-lookup"><span data-stu-id="8ee6e-197">Frequently-asked administrator questions about Office 365 connectivity:</span></span>
  
### <a name="how-do-i-submit-a-question"></a><span data-ttu-id="8ee6e-198">質問を送信するにはどうすればよいですか?</span><span class="sxs-lookup"><span data-stu-id="8ee6e-198">How do I submit a question?</span></span>

<span data-ttu-id="8ee6e-p123">下部にあるリンクをクリックして、記事が役に立ったかどうかを示し、追加の質問を送信します。フィードバックを監視し、よく寄せられる質問にお答えします。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p123">Click the link at the bottom to indicate if the article was helpful or not and submit any additional questions. We monitor the feedback and update the questions here with the most frequently asked.</span></span>
  
### <a name="how-do-i-determine-the-location-of-my-tenant"></a><span data-ttu-id="8ee6e-201">テナントの場所を決定するにはどうすればよいですか?</span><span class="sxs-lookup"><span data-stu-id="8ee6e-201">How do I determine the location of my tenant?</span></span>

 <span data-ttu-id="8ee6e-202">**テナントの場所**は、[データセンターマップ](http://aka.ms/datamaps)を使用して決定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-202">**Tenant location** is best determined using our [datacenter map](http://aka.ms/datamaps).</span></span>
  
### <a name="am-i-peering-appropriately-with-microsoft"></a><span data-ttu-id="8ee6e-203">Microsoft に対して適切にピアリングを行いますか?</span><span class="sxs-lookup"><span data-stu-id="8ee6e-203">Am I peering appropriately with Microsoft?</span></span>

 <span data-ttu-id="8ee6e-204">**ピアリングの場所**の詳細については、「 [Microsoft とのピアリング](https://www.microsoft.com/peering)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-204">**Peering locations** are described in more detail in [peering with Microsoft](https://www.microsoft.com/peering).</span></span>
  
<span data-ttu-id="8ee6e-p124">2500を超える ISP ピアリング関係をグローバルおよび70のプレゼンス状態で使用すると、ネットワークから私たちをシームレスに取得する必要があります。数分で、ISP のピアリング関係が最も最適であることを確認するのには、[次の](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/)ようにしておくことができます。これは、良好なピアツーリングのネットワークへの最適な使用例です。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p124">With over 2500 ISP peering relationships globally and 70 points of presence, getting from your network to ours should be seamless. It can't hurt to spend a few minutes making sure your ISP's peering relationship is the most optimal, [here's a few examples](https://blogs.technet.microsoft.com/onthewire/2017/03/22/__guidance/) of good and not so good peering hand-offs to our network.</span></span> 
  
### <a name="i-see-network-requests-to-ip-addresses-not-on-the-published-list-do-i-need-to-provide-access-to-them"></a><span data-ttu-id="8ee6e-207">IP アドレスへのネットワーク要求が公開されたリストにないことを確認しました。それらへのアクセスを提供する必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-207">I see network requests to IP addresses not on the published list, do I need to provide access to them?</span></span>
<span data-ttu-id="8ee6e-208"><a name="bkmk_MissingIP"> </a></span><span class="sxs-lookup"><span data-stu-id="8ee6e-208"></span></span>

<span data-ttu-id="8ee6e-p125">ここでは、に直接ルーティングする必要がある Office 365 サーバーの IP アドレスのみを提供しています。これは、ネットワーク要求を表示するすべての IP アドレスの包括的なリストではありません。Microsoft およびサードパーティが所有する、公開されていない、IP アドレスへのネットワーク要求が表示されます。これらの IP アドレスは、変更されたときに適切な通知が行われないように動的に生成または管理されます。ファイアウォールがこれらのネットワーク要求の fqdn に基づいてアクセスを許可できない場合は、PAC または WPAD ファイルを使用して要求を管理します。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p125">We only provide IP addresses for the Office 365 servers you should route directly to. This isn't a comprehensive list of all IP addresses you'll see network requests for. You will see network requests to Microsoft and third-party owned, unpublished, IP addresses. These IP addresses are dynamically generated or managed in a way that prevents timely notice when they change. If your firewall can't allow access based on the FQDNs for these network requests, use a PAC or WPAD file to manage the requests.</span></span>
  
<span data-ttu-id="8ee6e-214">詳細については、「Office 365 に関連付けられている IP について」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-214">See an IP associated with Office 365 that you want more information on?</span></span>
  
1. <span data-ttu-id="8ee6e-215">[CIDR 計算機](http://jodies.de/ipcalc)を使用して、IP アドレスがより大きな公開範囲に含まれているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-215">Check if the IP address is included in a larger published range using a [CIDR calculator](http://jodies.de/ipcalc).</span></span>
2. <span data-ttu-id="8ee6e-p126">パートナーが[whois クエリ](https://dnsquery.org/)を使用して IP を所有しているかどうかを確認します。Microsoft が所有している場合は、内部パートナーである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p126">See if a partner owns the IP with a [whois query](https://dnsquery.org/). If it's Microsoft owned, it may be an internal partner.</span></span>
3. <span data-ttu-id="8ee6e-p127">証明書を確認するブラウザーで*HTTPS://\<\> *を使用して ip アドレスに接続するには、証明書に一覧表示されているドメインを調べて、ip アドレスに関連付けられているドメインを理解します。office 365 の ip アドレスの一覧ではなく、microsoft が所有する ip アドレスである場合は、ip アドレスが*MSOCDN.NET*などの microsoft CDN または公開された ip 情報を持たない別の microsoft ドメインに関連付けられている可能性があります。証明書に記載されているドメインが、IP アドレスの一覧を取得することを要求している場合は、お知らせください。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p127">Check the certificate, in a browser connect to the IP address using  *HTTPS://\<IP_ADDRESS\>*  , check the domains listed on the certificate to understand what domains are associated with the IP address. If it's a Microsoft owned IP address and not on the list of Office 365 IP addresses, it's likely the IP address is associated with a Microsoft CDN such as  *MSOCDN.NET*  or another Microsoft domain without published IP information. If you do find the domain on the certificate is one where we claim to list the IP address, please let us know.</span></span>

### <a name="why-do-i-see-names-such-as-nsatcnet-or-akadnsnet-in-the-microsoft-domain-names"></a><span data-ttu-id="8ee6e-221">nsatc.net や akadns.net などの名前が Microsoft ドメイン名に表示されるのはなぜですか?</span><span class="sxs-lookup"><span data-stu-id="8ee6e-221">Why do I see names such as nsatc.net or akadns.net in the Microsoft domain names?</span></span>
<span data-ttu-id="8ee6e-222"><a name="bkmk_akamai"> </a></span><span class="sxs-lookup"><span data-stu-id="8ee6e-222"></span></span>

<span data-ttu-id="8ee6e-p128">office 365 およびその他の Microsoft サービスでは、office 365 の動作を向上させるために、akamai や markmonitor などのサードパーティ製のサービスをいくつか使用します。最高の経験を常に提供できるように、今後これらのサービスを変更することがあります。そのため、多くの場合、所有しているサードパーティのドメイン、レコード、または IP アドレスを指す CNAME レコードを公開します。サードパーティのドメインは、CDN などのコンテンツをホストしたり、地理的トラフィック管理サービスなどのサービスをホストしたりすることができます。これらのサードパーティとの接続が表示されている場合、クライアントからの最初の要求ではなく、リダイレクトまたは紹介の形式になっています。お客様によっては、潜在的な fqdn サードパーティのサービスで使用される可能性のある長いリストを明示的に追加せずに、この形式の紹介とリダイレクトを確実に通過できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p128">Office 365 and other Microsoft services use several third-party services such as Akamai and MarkMonitor to improve your Office 365 experience. To keep giving you the best experience possible, we may change these services in the future. In doing so, we often publish the CNAME record which points to a third party owned domain, A record, or IP address. Third party domains may host content, such as a CDN, or they may host a service, such as a geographical traffic management service. When you see connections to these third parties, they're in the form of a redirect or referral, not an initial request from the client. Some customers need to ensure this form of referral and redirection is allowed to pass without explicitly adding the long list of potential FQDNs third party services may use.</span></span>
  
<span data-ttu-id="8ee6e-p129">サービスの一覧は、いつでも変更される可能性があります。現在使用中のサービスには、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p129">The list of services is subject to change at any time. Some of the services currently in use include:</span></span>
  
<span data-ttu-id="8ee6e-p130">\* \*nsatc.net\*を含む要求を表示するときに、 [markmonitor](https://www.markmonitor.com/)が使用されています。このサービスは、悪意のある動作から保護するためのドメイン名の保護と監視を提供します。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p130">[MarkMonitor](https://www.markmonitor.com/) is in use when you see requests that include  *\*.nsatc.net*  . This service provides domain name protection and monitoring to protect against malicious behavior.</span></span>
  
<span data-ttu-id="8ee6e-p131">[](https://www.marketingcloud.com/) exacttarget.com へ\* \*\* の要求が表示されている場合は、ExactTarget が使用されています。このサービスは、悪意のある動作からの電子メールリンクの管理と監視を提供します。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p131">[ExactTarget](https://www.marketingcloud.com/) is in use when you see requests to  *\*.exacttarget.com*  . This service provides email link management and monitoring against malicious behavior.</span></span>
  
<span data-ttu-id="8ee6e-p132">次の fqdn のいずれかを含む要求がある場合は、 [akamai](https://www.akamai.com/)が使用されています。このサービスは、geo DNS およびコンテンツ配信ネットワークサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p132">[Akamai](https://www.akamai.com/) is in use when you see requests that include one of the following FQDNs. This service offers geo-DNS and content delivery network services.</span></span>
  
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

### <a name="i-have-to-have-the-minimum-connectivity-possible-for-office-365"></a><span data-ttu-id="8ee6e-237">Office 365 で最低限の接続を可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-237">I have to have the minimum connectivity possible for Office 365</span></span>
<span data-ttu-id="8ee6e-238"><a name="bkmk_thirdparty"> </a></span><span class="sxs-lookup"><span data-stu-id="8ee6e-238"></span></span>

<span data-ttu-id="8ee6e-p133">Office 365 は、インターネット上で機能するように構築された一連のサービスで、信頼性と可用性の約束は、利用可能な多くの標準インターネットサービスに基づいています。たとえば、DNS、CRL、および cdns などの標準インターネットサービスは、最新のインターネットサービスを使用するためにアクセスできるようにするために、Office 365 を使用するために到達可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p133">Office 365 is a suite of services built to function over the internet, the reliability and availability promises are based on many standard internet services being available. For example, standard internet services such as DNS, CRL, and CDNs must be reachable to use Office 365 just as they must be reachable to use most modern internet services.</span></span>

<span data-ttu-id="8ee6e-p134">Office 365 スイートは、主なサービス領域に分割されています。接続に対して選択的に有効にすることができます。また、すべてのに依存する共通領域があり、常に必須です。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p134">The Office 365 suite is broken down into major service areas. These can be selectively enabled for connectivity and there is a Common area which is a dependency for all and is always required.</span></span>

|<span data-ttu-id="8ee6e-243">**サービスエリア**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-243">**Service Area**</span></span>|<span data-ttu-id="8ee6e-244">**説明**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-244">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8ee6e-245">**Exchange**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-245">**Exchange**</span></span> <br/> |<span data-ttu-id="8ee6e-246">exchange online および exchange online Protection</span><span class="sxs-lookup"><span data-stu-id="8ee6e-246">Exchange Online and Exchange Online Protection</span></span> <br/> |
|<span data-ttu-id="8ee6e-247">**SharePoint**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-247">**SharePoint**</span></span> <br/> |<span data-ttu-id="8ee6e-248">SharePoint Online と OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="8ee6e-248">SharePoint Online and OneDrive for Business</span></span> <br/> |
|<span data-ttu-id="8ee6e-249">**Skype for Business Online および Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-249">**Skype for Business Online and Microsoft Teams**</span></span> <br/> |<span data-ttu-id="8ee6e-250">Skype for business と Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8ee6e-250">Skype for Business and Microsoft Teams</span></span> <br/> |
|<span data-ttu-id="8ee6e-251">**一般的な**</span><span class="sxs-lookup"><span data-stu-id="8ee6e-251">**Common**</span></span> <br/> |<span data-ttu-id="8ee6e-252">office 365 Pro Plus、office Online、Azure AD、その他の一般的なネットワークエンドポイント</span><span class="sxs-lookup"><span data-stu-id="8ee6e-252">Office 365 Pro Plus, Office Online, Azure AD and other common network endpoints</span></span> <br/> |

<span data-ttu-id="8ee6e-p135">基本的なインターネットサービスに加えて、機能の統合にのみ使用されるサードパーティのサービスがあります。これらは統合のために必要ですが、Office 365 エンドポイントの記事ではオプションとしてマークされていますが、エンドポイントにアクセスできない場合にもサービスのコア機能が引き続き機能することを意味します。必要なネットワークエンドポイントには、必須属性が true に設定されます。任意のネットワークエンドポイント (省略可能) には、必須属性が false に設定され、notes 属性には、接続がブロックされている場合に期待する必要がある不足している機能が詳細に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p135">In addition to basic internet services, there are third-party services that are only used to integrate functionality. While these are needed for integration, they're marked as optional in the Office 365 endpoints article which means core functionality of the service will continue to function if the endpoint isn't accessible. Any network endpoint which is required will have the required attribute set to true. Any network endpoint which is optional will have the required attribute set to false and the notes attribute will detail the missing functionality you should expect if connectivity is blocked.</span></span>
  
<span data-ttu-id="8ee6e-257">Office 365 を使用しようとしていて、サードパーティのサービスにアクセスできないことが検出された場合は[、この記事に記載されている必須またはオプションとしてマークされたすべての fqdn を、プロキシとファイアウォール経由で許可](urls-and-ip-address-ranges.md)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-257">If you're trying to use Office 365 and are finding third party services aren't accessible you'll want to [ensure all FQDNs marked required or optional in this article are allowed through the proxy and firewall](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="how-do-i-block-access-to-microsofts-consumer-services"></a><span data-ttu-id="8ee6e-258">Microsoft のコンシューマーサービスへのアクセスをどのようにブロックするか。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-258">How do I block access to Microsoft's consumer services?</span></span>
<span data-ttu-id="8ee6e-259"><a name="bkmk_consumer"> </a></span><span class="sxs-lookup"><span data-stu-id="8ee6e-259"></span></span>

<span data-ttu-id="8ee6e-p136">コンシューマーサービスへのアクセスを制限することは、自己責任で行う必要があります。コンシューマーサービスをブロックする唯一の信頼できる方法は、 *login.live.com*の FQDN へのアクセスを制限することです。この FQDN は、MSDN、TechNet などの非コンシューマーサービスを含む広範なサービスセットによって使用されます。この FQDN は microsoft サポートのセキュリティで保護されたファイル Exchange プログラムによっても使用され、microsoft 製品のトラブルシューティングを容易にするためにファイルを転送するために必要です。 この FQDN へのアクセスを制限すると、これらのサービスに関連付けられているネットワーク要求のルールに対する例外も含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-p136">Restricting access to our consumer services should be done at your own risk, the only reliable way to block consumer services is to restrict access to the  *login.live.com*  FQDN. This FQDN is used by a broad set of services including non-consumer services such as MSDN, TechNet, and others. This FQDN is also used by Microsoft Support's Secure File Exchange program and is necessary to transfer files to facilitate troubleshooting for Microsoft products.  Restricting access to this FQDN may result in the need to also include exceptions to the rule for network requests associated with these services.</span></span>
  
<span data-ttu-id="8ee6e-264">Microsoft のコンシューマーサービスのみにアクセスをブロックしても、ネットワーク上のユーザーが Office 365 テナントまたはその他のサービスを使用して情報を exfiltrate することはできないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8ee6e-264">Keep in mind that blocking access to the Microsoft consumer services alone won't prevent the ability for someone on your network to exfiltrate information using an Office 365 tenant or other service.</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="8ee6e-265">関連トピック</span><span class="sxs-lookup"><span data-stu-id="8ee6e-265">Related Topics</span></span>

[<span data-ttu-id="8ee6e-266">Office 365 IP アドレスと URL の Web サービス </span><span class="sxs-lookup"><span data-stu-id="8ee6e-266">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="8ee6e-267">Microsoft Azure データ センターの IP 範囲</span><span class="sxs-lookup"><span data-stu-id="8ee6e-267">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="8ee6e-268">Microsoft パブリック IP スペース</span><span class="sxs-lookup"><span data-stu-id="8ee6e-268">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)
  
[<span data-ttu-id="8ee6e-269">Microsoft Intune のネットワークインフラストラクチャの要件</span><span class="sxs-lookup"><span data-stu-id="8ee6e-269">Network infrastructure requirements for Microsoft Intune</span></span>](https://docs.microsoft.com/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)
  
[<span data-ttu-id="8ee6e-270">ExpressRoute と power BI</span><span class="sxs-lookup"><span data-stu-id="8ee6e-270">ExpressRoute and Power BI</span></span>](https://powerbi.microsoft.com/documentation/powerbi-admin-power-bi-expressroute/)
  
[<span data-ttu-id="8ee6e-271">Office 365 の URL と IP アドレス範囲</span><span class="sxs-lookup"><span data-stu-id="8ee6e-271">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)
  
[<span data-ttu-id="8ee6e-272">Office 365 向け ExpressRoute の管理</span><span class="sxs-lookup"><span data-stu-id="8ee6e-272">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="8ee6e-273">Office 365 ネットワーク接続の原則</span><span class="sxs-lookup"><span data-stu-id="8ee6e-273">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)
