---
title: 'Office 365 の URL と IP アドレスの範囲 '
ms.author: laurawi
author: LauraWi
manager: laurawi
ms.date: 11/27/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: '概要: Office 365 には、インターネットへの接続が必要です。Office 365 のプランを利用する予定のお客様は (政府機関コミュニティ クラウド (GCC) を含む)、次のエンドポイントに到達できる必要があります。'
hideEdit: true
ms.openlocfilehash: eecd07a471c1ca07387e89d7c3b4dbca4277e14d
ms.sourcegitcommit: e70808dccc1622d18b1cc5e1e4babd4238112838
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "40744491"
---
# <a name="office-365-urls-and-ip-address-ranges"></a><span data-ttu-id="31e68-104">Office 365 の URL と IP アドレスの範囲 </span><span class="sxs-lookup"><span data-stu-id="31e68-104">Office 365 URLs and IP address ranges</span></span>

 <span data-ttu-id="31e68-p102">**概要**: Office 365 には、インターネットへの接続が必要です。Office 365 のプランを利用する予定のお客様は (政府機関コミュニティ クラウド (GCC) を含む)、次のエンドポイントに到達できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="31e68-p102">**Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).</span></span>
  
> [!NOTE]
> <span data-ttu-id="31e68-p103">Microsoft は、このページの IP アドレスと FQDN エントリのための REST ベースの Web サービスを開始しました。この新しいサービスは、ファイアウォールやプロキシ サーバーなどのネットワーク境界デバイスの構成と更新に役立ちます。エンドポイントのリスト、リストの現在のバージョン、または特定の変更をダウンロードすることができます。このサービスは、このページからリンクされている XML ドキュメント (2018 年 10 月 2 日に廃止済み) に代わるものです。この新しいサービスを試すには、[[Web サービス]](office-365-ip-web-service.md) にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="31e68-p103">Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).</span></span>
  
<span data-ttu-id="31e68-112">*Office 365 世界 (+ GCC)* | [21Vianet が運営する Office 365](urls-and-ip-address-ranges-21vianet.md) | [Office 365 ドイツ](office-365-germany-endpoints.md) | [Office 365 米国政府機関向け DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 米国政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md) |</span><span class="sxs-lookup"><span data-stu-id="31e68-112">*Office 365 Worldwide (+GCC)* | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md) | [Office 365 Germany](office-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |</span></span>
  
||||
|:-----|:-----|:-----|
|<span data-ttu-id="31e68-113">**最終更新日:** 2019 年 11 月 27 日 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [ログ サブスクリプションの変更](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="31e68-113">**Last updated:** 11/27/2019 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change Log subscription](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span> <br/> |<span data-ttu-id="31e68-114">**ダウンロード:** 1 つの [JSON 形式](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)リスト内のすべての必須およびオプションの宛先。</span><span class="sxs-lookup"><span data-stu-id="31e68-114">**Download:** all required and optional destinations in one [JSON formatted](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) list.</span></span>  <br/> | <span data-ttu-id="31e68-115">**使用:** プロキシ [PAC ファイル](managing-office-365-endpoints.md#pacfiles)</span><span class="sxs-lookup"><span data-stu-id="31e68-115">**Use:** our proxy [PAC files](managing-office-365-endpoints.md#pacfiles)</span></span> <br/> |
   
 <span data-ttu-id="31e68-p104">はじめに 「[Office 365 エンドポイントを管理する](managing-office-365-endpoints.md)」を読み、以下のデータを使用してネットワーク接続を管理するための推奨事項を確認します。エンドポイント データは毎月月初めに更新され、新しい IP アドレスと URL は、それらがアクティブになる 30 日前に公開されます。これにより、お客様がまだ自動更新の設定を行っていない場合でも、新しい接続が必要になる前にプロセスを完了していただけます。サポートのエスカレーション、セキュリティ インシデント、またはその他の即時の運用要件に対応するために、月の途中にエンドポイントが更新される場合があります。このページの下に表示されるデータは、すべて REST ベースの Web サービスから生成されたものです。スクリプトやネットワーク デバイスを使用してこのデータにアクセスする場合、[[Web サービス](office-365-ip-web-service.md)] に直接移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31e68-p104">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](office-365-ip-web-service.md) directly.</span></span>

<span data-ttu-id="31e68-p105">次のエンドポイント データは、ユーザーのコンピューターを Office 365 に接続するための必要条件の一覧です。Microsoft からお客様のネットワークへの接続 (“ハイブリッド ネットワーク接続” や ”受信ネットワーク接続” と呼ばれる場合があります) は含まれません。詳細については [追加のエンドポイント](additional-office365-ip-addresses-and-urls.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31e68-p105">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections. See [Additional endpoints](additional-office365-ip-addresses-and-urls.md) for more information.</span></span>

<span data-ttu-id="31e68-p106">エンドポイントは 4 つのサービス領域にグループ分けされます。最初の 3 つのサービス領域は個別に接続の選択ができます。4 番目のサービス領域は共通の依存関係 ("Microsoft 365 Common および Office Online" と呼ばれる) で、常時ネットワーク接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="31e68-p106">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.</span></span>

<span data-ttu-id="31e68-128">次のデータ列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="31e68-128">Data columns shown are:</span></span>

- <span data-ttu-id="31e68-p107">**ID**: エンドポイントのセットとして知られる、行の ID 番号です。この ID は、エンドポイントの Web サービスによって返されるものと同じです。</span><span class="sxs-lookup"><span data-stu-id="31e68-p107">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="31e68-p108">**カテゴリ**: エンドポイントのセットが「最適化」、「許可」または「既定」のどれに分類されているかを示します。これらのカテゴリとその管理ガイダンスについては、[https://aka.ms/pnc](https://aka.ms/pnc) を参照してください。この列には、ネットワーク接続に必要なエンドポイントのセットが表示されます。ネットワーク接続が必要ないエンドポイントのセットの場合、このコラムには、エンドポイントのセットがブロックされた場合に使えなくなる機能に関する注意書きが書かれます。サービス領域全体を除外する場合は、ネットワーク接続が必要と記載されているエンドポイントのセットの接続は不要です。</span><span class="sxs-lookup"><span data-stu-id="31e68-p108">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="31e68-p109">**ER**: 「**はい**」とある場合、エンドポイントのセットは Office 365 のルート プレフィックスを使用して Azure ExpressRoute でサポートされています。表示されているルートのプレフィックスを含む BGP コミュニティは、記載されているサービス領域と整合します。ER に「**いいえ**」とある場合、ExpressRoute はそのエンドポイントのセットでサポートされていないことを意味します。ただし、ER に「**いいえ**」とある場合でも、アドバタイズされたルートが 1 つも無いとは判断しないようにします。</span><span class="sxs-lookup"><span data-stu-id="31e68-p109">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="31e68-p110">**アドレス**: FQDN またはワイルドカードを含むドメイン名と、エンドポイントのセットの IP アドレス範囲を一覧表示します。IP アドレスの範囲は CIDR 形式となり、指定されたネットワークの個別の IP アドレスが多数含まれる場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="31e68-p110">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="31e68-p111">**ポート**: アドレスと組み合わさることによりネットワーク エンドポイントを形成する TCP または UDP ポートの一覧を表示します。異なるポートが記載されている場合、IP アドレス範囲が重複している場合があります。</span><span class="sxs-lookup"><span data-stu-id="31e68-p111">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 worldwide endpoints](./includes/office-365-worldwide-endpoints.md)]

>[!Note]
><span data-ttu-id="31e68-144">Yammer IP アドレスと URL に関する推奨事項は、[このブログの投稿](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31e68-144">For recommendations on Yammer IP addresses and URLs, see [this blog post](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592).</span></span>
>


## <a name="related-topics"></a><span data-ttu-id="31e68-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="31e68-145">Related Topics</span></span>

[<span data-ttu-id="31e68-146">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="31e68-146">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)
  
[<span data-ttu-id="31e68-147">Office 365 の接続に関するトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="31e68-147">Troubleshooting Office 365 connectivity</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[<span data-ttu-id="31e68-148">クライアント接続</span><span class="sxs-lookup"><span data-stu-id="31e68-148">Client connectivity</span></span>](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[<span data-ttu-id="31e68-149">コンテンツ配信ネットワーク</span><span class="sxs-lookup"><span data-stu-id="31e68-149">Content delivery networks</span></span>](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[<span data-ttu-id="31e68-150">Microsoft Azure データ センターの IP 範囲</span><span class="sxs-lookup"><span data-stu-id="31e68-150">Microsoft Azure Datacenter IP Ranges</span></span>](https://www.microsoft.com/download/details.aspx?id=41653)
  
[<span data-ttu-id="31e68-151">Microsoft パブリック IP スペース</span><span class="sxs-lookup"><span data-stu-id="31e68-151">Microsoft Public IP Space</span></span>](https://www.microsoft.com/download/details.aspx?id=53602)

