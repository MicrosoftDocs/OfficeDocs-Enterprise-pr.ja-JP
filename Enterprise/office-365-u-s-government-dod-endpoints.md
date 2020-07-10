---
title: Office 365 米国政府の DoD エンドポイント
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
f1.keywords:
- NOCSH
description: '概要: Office 365 には、インターネットへの接続が必要です。 以下のエンドポイントには、Office 365 米国政府の DoD プランのみを使用しているお客様には到達可能である必要があります。'
hideEdit: true
ms.openlocfilehash: 824998ea1bcb89a151e9d249d9155bf5e9d785dc
ms.sourcegitcommit: 338e3bcf0a62842fbbb17145b67a4a93f3b90aac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2020
ms.locfileid: "45091194"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 米国政府の DoD エンドポイント

*適用対象: Office 365 Admin*

 Office 365 には、インターネットへの接続が必要です。 以下のエンドポイントには、Office 365 米国政府の DoD プランのみを使用しているお客様には到達可能である必要があります。
  
> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
 **Office 365 エンドポイント:** [(GCC を含む) 世界](urls-and-ip-address-ranges.md) | [21Vianet が運営する Office 365](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 ドイツ](office-365-germany-endpoints.md) |  *Office 365 米国政府機関向け DoD* | [Office 365 米国政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**最終更新日:** 07/09/2020- ![ RSS ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [変更ログサブスクリプション](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**ダウンロード:** [JSON 形式](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)の完全なリスト <br/> |

 [Office 365 エンドポイントの管理](managing-office-365-endpoints.md)から始めて、このデータを使用したネットワーク接続の管理に関する推奨事項を理解してください。 エンドポイントのデータは、各月の最初に、アクティブになる前に30日間公開された新しい IP アドレスと Url で更新されます。 これにより、自動更新を行っていないお客様は、新しい接続が必要になる前にプロセスを完了できます。 サポートのエスカレーション、セキュリティインシデント、またはその他の即時運用要件に対処する必要がある場合は、その月にエンドポイントを更新することもできます。 このページに表示されるデータはすべて、REST ベースの web サービスから生成されます。 このデータにアクセスするためにスクリプトまたはネットワークデバイスを使用している場合は、 [Web サービス](office-365-ip-web-service.md)に直接移動する必要があります。

以下のエンドポイントデータは、ユーザーのコンピューターから Office 365 への接続の要件を示しています。 Microsoft からお客様のネットワークへのネットワーク接続は含まれません。これは、ハイブリッドまたは受信ネットワーク接続と呼ばれることもあります。 詳細については、「 [web サービスに含まれていない追加のエンドポイント](additional-office365-ip-addresses-and-urls.md)」を参照してください。 

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

次のデータ列が表示されます。

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**: エンドポイントセットが Office 365 のルートプレフィックスを使用して Azure ExpressRoute でサポートされている場合は、これが**Yes**になります。 ルートプレフィックスを含む BGP コミュニティは、表示されている [サービス] 領域に配置されています。 ER が**No**の場合、このエンドポイントセットに対して ExpressRoute がサポートされていないことを意味します。 ただし、ER が**no**であるエンドポイントセットに対してルートがアドバタイズされていないと仮定してはなりません。 Azure AD Connect の使用を計画している場合は、 [「特別な考慮事項」セクション](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government)を参照して、適切な Azure ad connect 構成を持っていることを確認してください。

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
この表に関するメモ :

- セキュリティ/コンプライアンスセンター (SCC) は、Office 365 用の Azure ExpressRoute のサポートを提供します。 レポート作成、監査、高度な電子情報開示、統合 DLP、データガバナンスなど、SCC を通じて公開されている多くの機能についても同様です。 2つの特定の機能、PST インポートと電子情報開示のエクスポートは、現時点では、Azure Blob ストレージへの依存関係により、Office 365 ルートフィルターのみの Azure ExpressRoute をサポートしていません。 これらの機能を使用するには、azure のパブリックルートフィルターを使用したインターネット接続または Azure ExpressRoute を含む、サポート可能な Azure 接続オプションを使用して、Azure Blob ストレージに個別に接続する必要があります。 これらの機能の両方について、このような接続の確立を評価する必要があります。 Office 365 Information Protection team は、この制限を認識しており、両方の機能の Office 365 ルートフィルターに制限されているため、Office 365 用の Azure ExpressRoute のサポートを積極的に実行しています。

- リストに含まれていない、エンタープライズアプリケーション用の Microsoft 365 アプリを起動してドキュメントを編集するためにユーザーが必要としない、Microsoft 365 アプリ用の追加のオプションのエンドポイントがあります。 オプションのエンドポイントは Microsoft データセンターでホストされ、顧客データの処理、転送、保存は行われません。 これらのエンドポイントへのユーザー接続は、既定のインターネット出口境界に向けられるようにすることをお勧めします。
