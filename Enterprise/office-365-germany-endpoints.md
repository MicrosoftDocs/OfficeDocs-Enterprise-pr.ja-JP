---
title: Office 365 Germany のエンドポイント
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/29/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: 組織で Office 365 を使用していて、ネットワーク上のコンピューターがインターネットに接続できないように制限している場合は、次に示すように、送信許可一覧に含める必要があるエンドポイント (Fqdn、ポート、Url、および IPv4 アドレスの範囲) を検索して、コンピューターが正常に Office 365 を使用できるようにします。
hideEdit: true
ms.openlocfilehash: 89c9cf212e1101af222a915e60b0e1f82a3e5f26
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998286"
---
# <a name="office-365-germany-endpoints"></a>Office 365 Germany のエンドポイント

 *適用対象: Office 365 Admin*

Office 365 には、インターネットへの接続が必要です。 以下のエンドポイントには、 **Office 365 ドイツ**プランのみを使用しているお客様には到達可能である必要があります。
  
> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
 
 **Office 365 エンドポイント:** [(GCC を含む) 世界](urls-and-ip-address-ranges.md)  | [21Vianet が運営する Office 365](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 ドイツ* |  [Office 365 米国政府機関向け DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 米国政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**最終更新日:** 06/29/2020- ![ RSS ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [変更ログサブスクリプション](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) |**ダウンロード:** 1 つの [JSON 形式](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)リスト内のすべての必須およびオプションの宛先。  <br/> |

[Office 365 エンドポイントの管理](managing-office-365-endpoints.md)から始めて、このデータを使用したネットワーク接続の管理に関する推奨事項を理解してください。 エンドポイントのデータは、各月の最初に、アクティブになる前に30日間公開された新しい IP アドレスと Url で更新されます。 これにより、自動更新を行っていないお客様は、新しい接続が必要になる前にプロセスを完了できます。 サポートのエスカレーション、セキュリティインシデント、またはその他の即時運用要件に対処する必要がある場合は、その月にエンドポイントを更新することもできます。 [変更ログサブスクリプション](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)は、いつでも参照できます。

このページに表示されるデータはすべて、REST ベースの web サービスから生成されます。 このデータにアクセスするためにスクリプトまたはネットワークデバイスを使用している場合は、 [Web サービス](office-365-ip-web-service.md)に直接移動する必要があります。

Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

次のデータ列が表示されます。

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

