---
title: Office 365 Germany エンドポイント
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/01/2018
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
ms.openlocfilehash: 080f37d8f8cc6ad201ec9fd65489072c0ec1e585
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933114"
---
# <a name="office-365-germany-endpoints"></a>Office 365 Germany エンドポイント

 *Office 365 の管理者用に適用されます。*

**の概要:** Office 365 には、インターネットへの接続が必要です。次のエンドポイントは、 **Office 365 のドイツ**の計画のみを使用して顧客に到達できる必要があります。
  
> [!NOTE]
> マイクロソフトでは、IP アドレスと FQDN エントリをこのページでの REST ベースの web サービスをリリースしました。構成し、ファイアウォールやプロキシ サーバーなどのネットワーク境界デバイスを更新するには、この新しいサービスが役立ちます。エンドポイント、リスト、または特定の変更の現在のバージョンの一覧をダウンロードすることができます。このサービスでは、2018 年 10 月 2日では使用されなくなりましたが、このページからリンクされている XML ドキュメントが置き換えられます。この新しいサービスを試して、 [Web サービス](office-365-ip-web-service.md)に移動します。
  
 **Office 365 エンドポイント:** [(GCC を含む) 世界](urls-and-ip-address-ranges.md)  | [21Vianet が運営する Office 365](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 ドイツ* |  [Office 365 米国政府機関向け DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 米国政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**最終更新日:** 11/1/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [変更ログの購読](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) |**をダウンロード:** [JSON 形式](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)の 1 つのリスト内のすべての必須および省略可能な宛先です。  <br/> |

このデータを使用してネットワーク接続を管理するための当社の推奨事項を理解するのには[Office 365 の管理するエンドポイント](managing-office-365-endpoints.md)を開始します。エンドポイントのデータは、毎月新規の IP アドレスとアクティブにする前に 30 日間の公開 Url の先頭に更新されます。これにより、自動的に新しい接続が要求される前に、プロセスを完了するのには更新しないとはまだのお客様です。エンドポイントのアドレスのサポートのエスカレーション、セキュリティの問題、またはその他の即時の運用上の要件が必要な場合、月の中に更新も可能です。の[ログのサブスクリプションを変更](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)するのには常に参照できます。

REST ベースの web サービスからは、このページの下に表示されているデータすべてが生成されます。このデータにアクセスするスクリプト、またはネットワーク デバイスを使用している場合、 [Web サービス](office-365-ip-web-service.md)に直接移動する必要があります。

次のエンドポイント データは、ユーザーのコンピューターを Office 365 に接続するための要件の一覧です。Microsoft からお客様のネットワークへの接続 (“ハイブリッド ネットワーク接続” や ”受信ネットワーク接続” と呼ばれる場合があります) は含まれません。

エンドポイントは 4 つのサービス領域にグループ分けされます。最初の 3 つのサービス領域は個別に接続の選択ができます。4 番目のサービス領域は (“Microsoft 365 Common および Office Online” と呼ばれる) 一般的な依存関係と常時ネットワーク接続されている必要があります。　 

次のデータ列が表示されます。

- **ID**: エンドポイントのセットとして知られる、行の ID 番号です。この ID は、エンドポイントの Web サービスによって返されるものと同じです。

- **カテゴリ**: エンドポイントのセットが「最適化」、「許可」または「既定」のどれに分類されているかを示します。これらのカテゴリとその管理ガイダンスについては、[http://aka.ms/pnc](http://aka.ms/pnc) を参照してください。この列には、ネットワーク接続に必要なエンドポイントのセットが表示されます。ネットワーク接続が必要ないエンドポイントのセットの場合、このコラムには、エンドポイントのセットがブロックされた場合に使えなくなる機能に関する注意書きが書かれます。サービス領域全体を除外する場合は、ネットワーク接続が必要と記載されているエンドポイントのセットの接続は不要です。

- **ER**: 「**はい**」とある場合、エンドポイントのセットは Office 365 のルート プレフィックスを使用して Azure ExpressRoute でサポートされています。表示されているルートのプレフィックスを含む BGP コミュニティは、記載されているサービス 領域と整合します。ER に「**いいえ**」とある場合、ExpressRoute はそのエンドポイントのセットでサポートされていないことを意味します。ただし、ER に「**いいえ**」とある場合でも、アドバタイズされたルートが 1 つも無いとは判断しないようにします。

- **アドレス**: FQDN またはワイルドカードを含むドメイン名と、エンドポイントのセットの IP アドレス範囲を一覧表示します。IP アドレスの範囲は CIDR 形式となり、指定されたネットワークの個別の IP アドレスが多数含まれる場合があることに注意してください。
 
- **ポート**: アドレスと組み合わさることによりネットワーク エンドポイントを形成する TCP または UDP ポートの一覧を表示します。異なるポートが記載されている場合、IP アドレス範囲が重複している場合があります。

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

