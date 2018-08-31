---
title: Office 365 Germany エンドポイント
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: 組織では、Office 365 を使用すると、ネットワーク上のコンピューターをインターネットへの接続を制限、次のことがわかります (Fqdn、ポート、Url、および IPv4 と IPv6 のアドレス範囲のエンドポイントに含める必要があります、送信を許可することを確認するためのリスト、コンピューターは、Office 365 を正常に使用できます。
hideEdit: true
ms.openlocfilehash: fa5133391a24a3b9bb82a9dc5065e4dd10bb5bfe
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541506"
---
# <a name="office-365-germany-endpoints"></a><span data-ttu-id="83e2c-103">Office 365 Germany エンドポイント</span><span class="sxs-lookup"><span data-stu-id="83e2c-103">Office 365 Germany endpoints</span></span>

 <span data-ttu-id="83e2c-104">*Office 365 の管理者用に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="83e2c-104">*Applies To: Office 365 Admin*</span></span>

<span data-ttu-id="83e2c-p101">**の概要:** Office 365 には、インターネットへの接続が必要です。次のエンドポイントは、 **Office 365 のドイツ**の計画のみを使用して顧客に到達できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="83e2c-p101">**Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using **Office 365 Germany** plans only.</span></span>
  
> [!NOTE]
> <span data-ttu-id="83e2c-p102">Microsoft では、このページの IP アドレスと FQDN エントリのための REST ベースの Web サービスを開発しています。この新しいサービスは、ファイアウォールやプロキシ サーバーなどのネットワーク境界デバイスの構成と更新に役立ちます。エンドポイントのリスト、リストの現在のバージョン、または特定の変更をダウンロードすることができます。このサービスは、最終的にこのページの XML ドキュメント、RSS フィード、および IP アドレス、FQDN エントリを置き換えます。この新しいサービスを試すには、「[Web サービス](managing-office-365-endpoints.md#webservice)」にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="83e2c-p102">Microsoft is developing a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service will eventually replace the XML document, RSS feed, and the IP address and FQDN entries on this page. To try out this new service, go to [Web service](managing-office-365-endpoints.md#webservice).</span></span> 
  
 <span data-ttu-id="83e2c-112">**Office 365 エンドポイント:**[世界の検索サイト (GCC を含む)](urls-and-ip-address-ranges.md)  |  [21 Vianet 運用している office 365](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 のドイツ* | [Office 365 の米国政府の DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 米国政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md)  |</span><span class="sxs-lookup"><span data-stu-id="83e2c-112">**Office 365 endpoints:** [Worldwide (including GCC)](urls-and-ip-address-ranges.md)  | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany* | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="83e2c-113">**最終更新日:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Office 365 のドイツのエンドポイントへの変更の一覧](office-365-germany-endpoints-change-log.md)</span><span class="sxs-lookup"><span data-stu-id="83e2c-113">**Last updated:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [List of changes to the Office 365 Germany endpoints](office-365-germany-endpoints-change-log.md)</span></span>||

<span data-ttu-id="83e2c-p103">このデータを使用してネットワーク接続を管理するための当社の推奨事項を理解するのには[Office 365 の管理するエンドポイント](managing-office-365-endpoints.md)を開始します。エンドポイントのデータは、毎月新規の IP アドレスとアクティブにする前に 30 日間の公開 Url の先頭に更新されます。これにより、お客様にとってはまだ自動的に新しい接続が要求される前に、プロセスを完了するのには更新します。エンドポイントのアドレスのサポートのエスカレーション、セキュリティの問題、またはその他の即時の運用上の要件が必要な場合、月の中に更新も可能です。[Office 365 のドイツのエンドポイントへの変更の一覧](office-365-germany-endpoints-change-log.md)に常に参照できます。</span><span class="sxs-lookup"><span data-stu-id="83e2c-p103">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. You can always refer to the [list of changes to the Office 365 Germany endpoints](office-365-germany-endpoints-change-log.md).</span></span>

<span data-ttu-id="83e2c-p104">REST ベースの web サービスからは、このページの下に表示されているデータすべてが生成されます。このデータにアクセスするスクリプト、またはネットワーク デバイスを使用している場合、 [Web サービス](managing-office-365-endpoints.md#webservice)に直接移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83e2c-p104">The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](managing-office-365-endpoints.md#webservice) directly.</span></span>

<span data-ttu-id="83e2c-p105">エンドポイント データの下では、ユーザーのコンピューターから Office 365 への接続の要件を示します。マイクロソフトからお客様のネットワークとも言われますハイブリッドまたは着信ネットワーク接続のネットワーク接続は含まれません。</span><span class="sxs-lookup"><span data-stu-id="83e2c-p105">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="83e2c-p106">エンドポイントは、次の 4 つのサービス領域にグループ化されます。最初の 3 つのサービス分野個別に選択できますない接続用。4 番目のサービス エリアは一般的な依存関係 (Microsoft 365 共通と Office オンラインと呼ばれる) とネットワーク接続を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="83e2c-p106">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office Online) and must always have network connectivity.</span></span>

<span data-ttu-id="83e2c-126">表示されるデータ列は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="83e2c-126">Data columns shown are:</span></span>

- <span data-ttu-id="83e2c-p107">**ID**: エンドポイントのセットとも呼ばれる、行の ID 番号です。この ID は、エンドポイントの設定の web サービスによって返されるものと同じです。</span><span class="sxs-lookup"><span data-stu-id="83e2c-p107">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="83e2c-p108">**カテゴリ**: エンドポイントの設定を最適化」では、「許可」または「既定」として分類されたかどうかを示しています。については、これらのカテゴリとでそれらを管理するためのガイダンスを読むことができます[http://aka.ms/pnc](http://aka.ms/pnc)。このコラムでは、どのエンドポイントのセットは、ネットワークに接続する必要も一覧表示されます。ネットワークに接続する必要はありませんがセットのエンドポイント、エンドポイントのセットがブロックされている場合、どのような機能が失われるとを示すためにこのフィールドにメモを提供しています。サービス全体の領域を除外する場合は、必要に応じて表示されているエンドポイントのセットには接続は不要です。</span><span class="sxs-lookup"><span data-stu-id="83e2c-p108">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [http://aka.ms/pnc](http://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="83e2c-p109">**ER**: これは、 **[はい]** エンドポイントの設定は Office 365 のルートのプレフィックスを持つ Azure ExpressRoute 経由でサポートされている場合。一覧に [サービス] 領域に表示されているルートのプレフィックスを含む BGP コミュニティを配置します。ER が**No**の場合、このエンドポイントのセットの ExpressRoute がサポートされていないことを意味します。ただし、その必要がありますが想定されていなかった**なし**の ER が、エンドポイントのセットのルートをアドバタイズしないことです。</span><span class="sxs-lookup"><span data-stu-id="83e2c-p109">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="83e2c-p110">**アドレス**: Fqdn またはワイルドカード ドメイン名と IP アドレスの範囲のエンドポイントのセットを一覧表示します。IP アドレスの範囲は CIDR 形式では、指定されたネットワークでは多くの個々 の IP アドレスを含めることことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="83e2c-p110">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="83e2c-p111">**ポート**: TCP または UDP のポートを組み合わせて構成されるネットワーク エンドポイントを作成するアドレスの一覧が表示されます。一部重複する IP アドレスの範囲にすることがありますが別のポートを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="83e2c-p111">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

