---
title: 21Vianet が運営する Office 365の URL と IP アドレス範囲
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/30/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- GMA150
- GPA150
- GEA150
ms.assetid: 5c47c07d-f9b6-4b78-a329-bfdc1b6da7a0
description: この記事は、中国の 21 vianet が運営する Office 365 に適用されます。この記事では、21Vianet が運営する Office 365 で使用される URL と IP アドレス範囲の一覧が表示されます。
hideEdit: true
ms.openlocfilehash: 54ebb54211c14d7279d9942372570c1985820d58
ms.sourcegitcommit: 8d1cc95b3641afe547c6d0e05f2dad5d013a0773
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "37975842"
---
# <a name="urls-and-ip-address-ranges-for-office-365-operated-by-21vianet"></a>21Vianet が運営する Office 365の URL と IP アドレス範囲

 *適用先: 21Vianet が運営する Office 365 の中小企業管理者、21Vianet が運営する Office 365 の管理者*

**概要**: 次のエンドポイント (FQDN、ポート、URL、IPv4、および IPv6 プレフィックス) は 21Vianet が運営する Office 365 に適用され、これらのプランだけを活用して生産性サービスを組織へ提供できるように設計されています。
  
> [!NOTE]
> Microsoft は、このページの IP アドレスと FQDN エントリのための REST ベースの Web サービスを開始しました。この新しいサービスは、ファイアウォールやプロキシ サーバーなどのネットワーク境界デバイスの構成と更新に役立ちます。エンドポイントのリスト、リストの現在のバージョン、または特定の変更をダウンロードすることができます。このサービスは、このページからリンクされている XML ドキュメント (2018 年 10 月 2 日に廃止済み) に代わるものです。この新しいサービスを試すには、[[Web サービス]](office-365-ip-web-service.md) にアクセスします。
  
 **Office 365 エンドポイント:** [(GCC を含む) 世界](urls-and-ip-address-ranges.md)  | *21Vianet が運営する Office 365* | [Office 365 ドイツ](office-365-germany-endpoints.md) |  [Office 365 米国政府機関向け DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 米国政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**最終更新日:** 2019 年 9 月 30 日 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [ログ サブスクリプションの変更](https://endpoints.office.com/version/China?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**ダウンロード:** 1 つの [JSON 形式](https://endpoints.office.com/endpoints/China?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)リスト内のすべての必須およびオプションの宛先。  <br/> |

はじめに 「[Office 365 エンドポイントを管理する](managing-office-365-endpoints.md)」を読み、以下のデータを使用してネットワーク接続を管理するための推奨事項を確認します。エンドポイント データは毎月月初めに更新され、新しい IP アドレスと URL は、それらがアクティブになる 30 日前に公開されます。これにより、お客様がまだ自動更新の設定を行っていない場合でも、新しい接続が必要になる前にプロセスを完了していただけます。サポートのエスカレーション、セキュリティ インシデント、またはその他の即時の運用要件に対応するために、月の途中にエンドポイントが更新される場合があります。このページの下に表示されるデータは、すべて REST ベースの Web サービスから生成されたものです。スクリプトやネットワーク デバイスを使用してこのデータにアクセスする場合、[[Web サービス](office-365-ip-web-service.md)] に直接移動する必要があります。

次のエンドポイント データは、ユーザーのコンピューターを Office 365 に接続するための要件の一覧です。Microsoft からお客様のネットワークへの接続 (“ハイブリッド ネットワーク接続” や ”受信ネットワーク接続” と呼ばれる場合があります) は含まれません。

エンドポイントは 4 つのサービス領域にグループ分けされます。最初の 3 つのサービス領域は個別に接続の選択ができます。4 番目のサービス領域は共通の依存関係 ("Microsoft 365 Common および Office Online" と呼ばれる) で、常時ネットワーク接続されている必要があります。

次のデータ列が表示されます。

- **ID**: エンドポイントのセットとして知られる、行の ID 番号です。この ID は、エンドポイントの Web サービスによって返されるものと同じです。

- **カテゴリ**: エンドポイントのセットが「最適化」、「許可」または「既定」のどれに分類されているかを示します。これらのカテゴリとその管理ガイダンスについては、[https://aka.ms/pnc](https://aka.ms/pnc) を参照してください。この列には、ネットワーク接続に必要なエンドポイントのセットが表示されます。ネットワーク接続が必要ないエンドポイントのセットの場合、このコラムには、エンドポイントのセットがブロックされた場合に使えなくなる機能に関する注意書きが書かれます。サービス領域全体を除外する場合は、ネットワーク接続が必要と記載されているエンドポイントのセットの接続は不要です。

- **ER**: 「**はい**」とある場合、エンドポイントのセットは Office 365 のルート プレフィックスを使用して Azure ExpressRoute でサポートされています。表示されているルートのプレフィックスを含む BGP コミュニティは、記載されているサービス領域と整合します。ER に「**いいえ**」とある場合、ExpressRoute はそのエンドポイントのセットでサポートされていないことを意味します。ただし、ER に「**いいえ**」とある場合でも、アドバタイズされたルートが 1 つも無いとは判断しないようにします。

- **アドレス**: FQDN またはワイルドカードを含むドメイン名と、エンドポイントのセットの IP アドレス範囲を一覧表示します。IP アドレスの範囲は CIDR 形式となり、指定されたネットワークの個別の IP アドレスが多数含まれる場合があることに注意してください。
 
- **ポート**: アドレスと組み合わさることによりネットワーク エンドポイントを形成する TCP または UDP ポートの一覧を表示します。異なるポートが記載されている場合、IP アドレス範囲が重複している場合があります。

[!INCLUDE [Office 365 operated by 21Vianet endpoints](./includes/office-365-operated-by-21vianet-endpoints.md)]


