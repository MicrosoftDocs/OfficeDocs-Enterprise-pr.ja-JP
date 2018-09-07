---
title: Office 365 の米国政府の GCC の高いエンドポイント
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: 組織では、Office 365 を使用すると、ネットワーク上のコンピューターをインターネットへの接続を制限、次のことがわかります (Fqdn、ポート、Url、IPv4 および IPv6 のアドレス範囲) のエンドポイントに含める必要があります、送信を許可することを確認するためのリスト、コンピューターは、Office 365 を正常に使用できます。
hideEdit: true
ms.openlocfilehash: eb1ac47ad8317b46ce19106e8eeab5dae3c25432
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541752"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a><span data-ttu-id="2b32f-103">Office 365 の米国政府の GCC の高いエンドポイント</span><span class="sxs-lookup"><span data-stu-id="2b32f-103">Office 365 U.S. Government GCC High endpoints</span></span>

 <span data-ttu-id="2b32f-104">*Office 365 の管理者用に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="2b32f-104">*Applies To: Office 365 Admin*</span></span>

<span data-ttu-id="2b32f-p101">**の概要:** Office 365 には、インターネットへの接続が必要です。次のエンドポイントは、Office 365 米国政府 GCC 高プランのみを使用して顧客に到達できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b32f-p101">**Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 U.S. Government GCC High plans only.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2b32f-p102">Microsoft では、このページの IP アドレスと FQDN エントリのための REST ベースの Web サービスを開発しています。この新しいサービスは、ファイアウォールやプロキシ サーバーなどのネットワーク境界デバイスの構成と更新に役立ちます。エンドポイントのリスト、リストの現在のバージョン、または特定の変更をダウンロードすることができます。このサービスは、最終的にこのページの XML ドキュメント、RSS フィード、および IP アドレス、FQDN エントリを置き換えます。この新しいサービスを試すには、「[Web サービス](managing-office-365-endpoints.md#webservice)」にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2b32f-p102">Microsoft is developing a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service will eventually replace the XML document, RSS feed, and the IP address and FQDN entries on this page. To try out this new service, go to [Web service](managing-office-365-endpoints.md#webservice).</span></span>
  
 <span data-ttu-id="2b32f-112">**Office 365 エンドポイント:**[世界の検索サイト (GCC を含む)](urls-and-ip-address-ranges.md) |  [21 Vianet 運用している office 365](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 のドイツ](office-365-germany-endpoints.md)  | [Office 365 の米国政府の DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 米国政府 GCC 高* |</span><span class="sxs-lookup"><span data-stu-id="2b32f-112">**Office 365 endpoints:** [Worldwide (including GCC)](urls-and-ip-address-ranges.md) | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md)  | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 U.S. Government GCC High* |</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="2b32f-113">**最終更新日:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [変更ログの購読](https://aka.ms/usendpointrss)</span><span class="sxs-lookup"><span data-stu-id="2b32f-113">**Last updated:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change Log subscription](https://aka.ms/usendpointrss)</span></span> <br/> |<span data-ttu-id="2b32f-114">**をダウンロード:** [XML 形式](https://aka.ms/usdefenseendpoints)の完全なリスト</span><span class="sxs-lookup"><span data-stu-id="2b32f-114">**Download:** the full list in [XML format](https://aka.ms/usdefenseendpoints)</span></span> <br/> |
   
 <span data-ttu-id="2b32f-p103">このデータを使用してネットワーク接続を管理するための当社の推奨事項を理解するのには[Office 365 の管理するエンドポイント](managing-office-365-endpoints.md)を開始します。エンドポイントのデータは、毎月新規の IP アドレスとアクティブにする前に 30 日間の公開 Url の先頭に更新されます。これにより、お客様にとってはまだ自動的に新しい接続が要求される前に、プロセスを完了するのには更新します。エンドポイントのアドレスのサポートのエスカレーション、セキュリティの問題、またはその他の即時の運用上の要件が必要な場合、月の中に更新も可能です。REST ベースの web サービスからは、このページの下に表示されているデータすべてが生成されます。このデータにアクセスするスクリプト、またはネットワーク デバイスを使用している場合、 [Web サービス](managing-office-365-endpoints.md#webservice)に直接移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b32f-p103">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](managing-office-365-endpoints.md#webservice) directly.</span></span>

<span data-ttu-id="2b32f-p104">エンドポイント データの下では、ユーザーのコンピューターから Office 365 への接続の要件を示します。マイクロソフトからお客様のネットワークとも言われますハイブリッドまたは着信ネットワーク接続のネットワーク接続は含まれません。</span><span class="sxs-lookup"><span data-stu-id="2b32f-p104">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="2b32f-p105">エンドポイントは、次の 4 つのサービス領域にグループ化されます。最初の 3 つのサービス分野個別に選択できますない接続用。4 番目のサービス エリアは一般的な依存関係 (Microsoft 365 共通と Office オンラインと呼ばれる) とネットワーク接続を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b32f-p105">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office Online) and must always have network connectivity.</span></span>

<span data-ttu-id="2b32f-126">表示されるデータ列は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2b32f-126">Data columns shown are:</span></span>

- <span data-ttu-id="2b32f-p106">**ID**: エンドポイントのセットとも呼ばれる、行の ID 番号です。この ID は、エンドポイントの設定の web サービスによって返されるものと同じです。</span><span class="sxs-lookup"><span data-stu-id="2b32f-p106">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="2b32f-p107">**カテゴリ**: エンドポイントの設定を最適化」では、「許可」または「既定」として分類されたかどうかを示しています。については、これらのカテゴリとでそれらを管理するためのガイダンスを読むことができます[http://aka.ms/pnc](http://aka.ms/pnc)。このコラムでは、どのエンドポイントのセットは、ネットワークに接続する必要も一覧表示されます。ネットワークに接続する必要はありませんがセットのエンドポイント、エンドポイントのセットがブロックされている場合、どのような機能が失われるとを示すためにこのフィールドにメモを提供しています。サービス全体の領域を除外する場合は、必要に応じて表示されているエンドポイントのセットには接続は不要です。</span><span class="sxs-lookup"><span data-stu-id="2b32f-p107">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [http://aka.ms/pnc](http://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="2b32f-p108">**ER**: これは、 **[はい]** エンドポイントの設定は Office 365 のルートのプレフィックスを持つ Azure ExpressRoute 経由でサポートされている場合。一覧に [サービス] 領域に表示されているルートのプレフィックスを含む BGP コミュニティを配置します。ER が**No**の場合、このエンドポイントのセットの ExpressRoute がサポートされていないことを意味します。ただし、その必要がありますが想定されていなかった**なし**の ER が、エンドポイントのセットのルートをアドバタイズしないことです。Azure AD 接続を使用する場合は、適切ながあることを確認するのには[特別な考慮事項のセクション](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud)を読んで Azure AD 接続を構成します。</span><span class="sxs-lookup"><span data-stu-id="2b32f-p108">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**. If you plan to use Azure AD Connect, read the [special considerations section](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud) to ensure you have the appropriate Azure AD Connect configuration.</span></span>

- <span data-ttu-id="2b32f-p109">**アドレス**: Fqdn またはワイルドカード ドメイン名と IP アドレスの範囲のエンドポイントのセットを一覧表示します。IP アドレスの範囲は CIDR 形式では、指定されたネットワークでは多くの個々 の IP アドレスを含めることことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2b32f-p109">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="2b32f-p110">**ポート**: TCP または UDP のポートを組み合わせて構成されるネットワーク エンドポイントを作成するアドレスの一覧が表示されます。一部重複する IP アドレスの範囲にすることがありますが別のポートを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="2b32f-p110">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

<span data-ttu-id="2b32f-143">この表に関するメモ :</span><span class="sxs-lookup"><span data-stu-id="2b32f-143">Notes for this table:</span></span>

- <span data-ttu-id="2b32f-p111">セキュリティとコンプライアンス センター (SCC) は、Office 365 の Azure ExpressRoute のサポートを提供します。SCC レポート作成、監査、高度な電子的証拠開示、DLP の統合、データ ・ ガバナンスなどを通じて公開される多くの機能にも当てはまります。、PST のインポートとエクスポートで電子的証拠開示の 2 つの特定機能はサポートされていません Azure ExpressRoute Azure のブロブ ストレージへの依存関係のためのルート フィルターのみを Office 365 にします。これらの機能を利用するには、Azure パブリック ルート フィルターを使用してインターネットに接続または Azure ExpressRoute が含まれて、Azure 接続をサポート可能なオプションを使用した Azure のブロブ ストレージへの個別の接続が必要です。これらの機能の両方のような接続を確立することを評価する必要があります。Office 365 の情報保護チームがこの制限を認識してルート フィルターを Office 365 にこれらの機能の両方の制限としての Office 365 の Azure ExpressRoute のサポートを提供する作業は、積極的にします。</span><span class="sxs-lookup"><span data-stu-id="2b32f-p111">The Security and Compliance Center (SCC) provides support for Azure ExpressRoute for Office 365. The same applies for many features exposed through the SCC such as Reporting, Auditing, Advanced eDiscovery, Unified DLP, and Data Governance. Two specific features, PST Import and eDiscovery Export, currently do not support Azure ExpressRoute with only Office 365 route filters due to their dependency on Azure Blob Storage. To consume those features, you need separate connectivity to Azure Blob Storage using any supportable Azure connectivity options, which include Internet connectivity or Azure ExpressRoute with Azure Public route filters. You have to evaluate establishing such connectivity for both of those features. The Office 365 Information Protection team is aware of this limitation and is actively working to bring support for Azure ExpressRoute for Office 365 as limited to Office 365 route filters for both of those features.</span></span>

- <span data-ttu-id="2b32f-p112">Office 365 用リソースに示されていないと、ユーザーが Office 365 用リソースのアプリケーションを起動し、ドキュメントを編集する必要はありませんがその他の省略可能なエンドポイントがあります。省略可能なエンドポイント マイクロソフトのデータ センターでホストされているとは処理、転送では、や顧客データを格納します。これらのエンドポイントへのユーザー接続は、既定のインターネットの出口周辺に転送することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2b32f-p112">There are additional optional endpoints for Office 365 ProPlus that are not listed and are not required for users to launch Office 365 ProPlus applications and edit documents. Optional endpoints are hosted in Microsoft datacenters and do not process, transmit, or store customer data. We recommend that user connections to these endpoints be directed to the default Internet egress perimeter.</span></span>
