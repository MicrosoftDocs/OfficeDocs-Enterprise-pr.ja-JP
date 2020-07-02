---
title: 'Office 365 の URL と IP アドレスの範囲 '
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/29/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 'Summary: Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).'
hideEdit: true
ms.openlocfilehash: d75fa6d88255ff5df785fa335a9976c4bcca309d
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997445"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>Office 365 の URL と IP アドレスの範囲 

Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).
  
> [!NOTE]
> COVID-19 危機への対応の一環として、Microsoft は、計画されている URL および IP アドレスの変更を一時的に停止しています。 これは、お客様の IT チームが、在宅勤務での Office 365 シナリオに推奨されるネットワーク最適化を安心して簡単に実装できるようにするための措置です。 2020 年 3 月 24 日から 2020 年 6 月 30 日まで、この一時停止により、主要な Office 365 サービス (Exchange Online、SharePoint Online、Microsoft Teams) の最適化のカテゴリに含まれる IP 範囲と URL の変更が中止されます。 他のエンドポイント カテゴリの変更は、通常どおりに行われます。 この期間中、お客様は Office 365 最適化カテゴリのサービス エンドポイント定義を静的に使用して、クラウド側のネットワーク変更による Office 365 接続へのリスクを最小限に抑えながら、ターゲット ネットワークの最適化 (帯域幅予約や分割トンネル VPN の構成など) を行うことができます。 期間終了時にサービスの中断が発生しないようにするため、「[Office 365 エンドポイントの管理](managing-office-365-endpoints.md)」でのガイダンスに従って、Office 365 サービス エンドポイントの変更管理や自動化プロセスを実装することを強くお勧めします。

> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
*Office 365 世界 (+ GCC)* | [21Vianet が運営する Office 365](urls-and-ip-address-ranges-21vianet.md) | [Office 365 ドイツ](office-365-germany-endpoints.md) | [Office 365 米国政府機関向け DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 米国政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md) |
  
||||
|:-----|:-----|:-----|
|**最終更新日:** 06/29/2020- ![ RSS ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [変更ログサブスクリプション](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**ダウンロード:** 1 つの [JSON 形式](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)リスト内のすべての必須およびオプションの宛先。  <br/> | **使用:** プロキシ [PAC ファイル](managing-office-365-endpoints.md#pacfiles) <br/> |

 Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](office-365-ip-web-service.md) directly.

Endpoint data below lists requirements for connectivity from a user's machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections. See [Additional endpoints](additional-office365-ip-addresses-and-urls.md) for more information.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

次のデータ列が表示されます。

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as "Optimize", "Allow", or "Default". You can read about these categories and guidance for management of them at [New Office 365 endpoint categories](https://docs.microsoft.com/office365/enterprise/office-365-network-connectivity-principles#new-office-365-endpoint-categories). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.

[!INCLUDE [Office 365 worldwide endpoints](./includes/office-365-worldwide-endpoints.md)]

>[!Note]
>Yammer IP アドレスと URL に関する推奨事項は、[このブログの投稿](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592)を参照してください。
>

## <a name="related-topics"></a>関連項目

[Office 365 エンドポイントの管理](managing-office-365-endpoints.md)
  
[Office 365 の接続に関するトラブルシューティング](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[クライアント接続](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[コンテンツ配信ネットワーク](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Microsoft Azure データ センターの IP 範囲](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft パブリック IP スペース](https://www.microsoft.com/download/details.aspx?id=53602)
