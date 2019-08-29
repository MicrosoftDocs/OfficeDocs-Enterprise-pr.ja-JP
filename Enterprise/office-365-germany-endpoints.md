---
title: Office 365 Germany のエンドポイント
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/28/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: 組織で Office 365 を使用していて、ネットワーク上のコンピューターがインターネットに接続できないように制限している場合は、次のように、送信許可一覧に含める必要があるエンドポイント (Fqdn、ポート、Url、および IPv4 および IPv6 アドレスの範囲) を確認します。コンピューターは Office 365 を正常に使用できます。
hideEdit: true
ms.openlocfilehash: 761cf4d6f3b6c214aae624138902d2f75a0e7a01
ms.sourcegitcommit: 0d21bd4edac07db94269e2a176c92469c02b2e26
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "36656022"
---
# <a name="office-365-germany-endpoints"></a>Office 365 Germany のエンドポイント

 *適用対象: Office 365 Admin*

**概要:** Office 365 には、インターネットへの接続が必要です。 以下のエンドポイントには、 **Office 365 ドイツ**プランのみを使用しているお客様には到達可能である必要があります。
  
> [!NOTE]
> Microsoft は、このページの IP アドレスと FQDN エントリのための REST ベースの Web サービスを開始しました。この新しいサービスは、ファイアウォールやプロキシ サーバーなどのネットワーク境界デバイスの構成と更新に役立ちます。エンドポイントのリスト、リストの現在のバージョン、または特定の変更をダウンロードすることができます。このサービスは、このページからリンクされている XML ドキュメント (2018 年 10 月 2 日に廃止済み) に代わるものです。この新しいサービスを試すには、[[Web サービス]](office-365-ip-web-service.md) にアクセスします。
 
 **Office 365 エンドポイント:** [(GCC を含む) 世界](urls-and-ip-address-ranges.md)  | [21Vianet が運営する Office 365](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 ドイツ* |  [Office 365 米国政府機関向け DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 米国政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**最終更新日:** 08/28/2019 ![-](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) RSS[変更ログサブスクリプション](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) |**ダウンロード:** 1 つの [JSON 形式](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)リスト内のすべての必須およびオプションの宛先。  <br/> |

[Office 365 エンドポイントの管理](managing-office-365-endpoints.md)から始めて、このデータを使用したネットワーク接続の管理に関する推奨事項を理解してください。 エンドポイントのデータは、各月の最初に、アクティブになる前に30日間公開された新しい IP アドレスと Url で更新されます。 これにより、自動更新を行っていないお客様は、新しい接続が必要になる前にプロセスを完了できます。 サポートのエスカレーション、セキュリティインシデント、またはその他の即時運用要件に対処する必要がある場合は、その月にエンドポイントを更新することもできます。 [変更ログサブスクリプション](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)は、いつでも参照できます。

このページに表示されるデータはすべて、REST ベースの web サービスから生成されます。 このデータにアクセスするためにスクリプトまたはネットワークデバイスを使用している場合は、 [Web サービス](office-365-ip-web-service.md)に直接移動する必要があります。

次のエンドポイント データは、ユーザーのコンピューターを Office 365 に接続するための要件の一覧です。Microsoft からお客様のネットワークへの接続 (“ハイブリッド ネットワーク接続” や ”受信ネットワーク接続” と呼ばれる場合があります) は含まれません。

エンドポイントは4つのサービス領域にグループ化されます。 最初の3つのサービス領域は、接続のために個別に選択できます。 4番目のサービスエリアは、一般的な依存関係 (Microsoft 365 Common および Office) で、常にネットワーク接続が必要です。

次のデータ列が表示されます。

- **ID**: エンドポイントのセットとして知られる、行の ID 番号です。この ID は、エンドポイントの Web サービスによって返されるものと同じです。

- **カテゴリ**: エンドポイントのセットが「最適化」、「許可」または「既定」のどれに分類されているかを示します。これらのカテゴリとその管理ガイダンスについては、[http://aka.ms/pnc](http://aka.ms/pnc) を参照してください。この列には、ネットワーク接続に必要なエンドポイントのセットが表示されます。ネットワーク接続が必要ないエンドポイントのセットの場合、このコラムには、エンドポイントのセットがブロックされた場合に使えなくなる機能に関する注意書きが書かれます。サービス領域全体を除外する場合は、ネットワーク接続が必要と記載されているエンドポイントのセットの接続は不要です。

- **ER**: 「**はい**」とある場合、エンドポイントのセットは Office 365 のルート プレフィックスを使用して Azure ExpressRoute でサポートされています。表示されているルートのプレフィックスを含む BGP コミュニティは、記載されているサービス領域と整合します。ER に「**いいえ**」とある場合、ExpressRoute はそのエンドポイントのセットでサポートされていないことを意味します。ただし、ER に「**いいえ**」とある場合でも、アドバタイズされたルートが 1 つも無いとは判断しないようにします。

- **アドレス**: FQDN またはワイルドカードを含むドメイン名と、エンドポイントのセットの IP アドレス範囲を一覧表示します。IP アドレスの範囲は CIDR 形式となり、指定されたネットワークの個別の IP アドレスが多数含まれる場合があることに注意してください。
 
- **ポート**: アドレスと組み合わさることによりネットワーク エンドポイントを形成する TCP または UDP ポートの一覧を表示します。異なるポートが記載されている場合、IP アドレス範囲が重複している場合があります。

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

