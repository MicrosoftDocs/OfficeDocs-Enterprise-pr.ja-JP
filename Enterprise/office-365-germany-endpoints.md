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
# <a name="office-365-germany-endpoints"></a>Office 365 Germany エンドポイント

 *Office 365 の管理者用に適用されます。*

**の概要:** Office 365 には、インターネットへの接続が必要です。次のエンドポイントは、 **Office 365 のドイツ**の計画のみを使用して顧客に到達できる必要があります。
  
> [!NOTE]
> Microsoft では、このページの IP アドレスと FQDN エントリのための REST ベースの Web サービスを開発しています。この新しいサービスは、ファイアウォールやプロキシ サーバーなどのネットワーク境界デバイスの構成と更新に役立ちます。エンドポイントのリスト、リストの現在のバージョン、または特定の変更をダウンロードすることができます。このサービスは、最終的にこのページの XML ドキュメント、RSS フィード、および IP アドレス、FQDN エントリを置き換えます。この新しいサービスを試すには、「[Web サービス](managing-office-365-endpoints.md#webservice)」にアクセスします。 
  
 **Office 365 エンドポイント:**[世界の検索サイト (GCC を含む)](urls-and-ip-address-ranges.md)  |  [21 Vianet 運用している office 365](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 のドイツ* | [Office 365 の米国政府の DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 米国政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md)  |
  
|||
|:-----|:-----|
|**最終更新日:** 7/2/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Office 365 のドイツのエンドポイントへの変更の一覧](office-365-germany-endpoints-change-log.md)||

このデータを使用してネットワーク接続を管理するための当社の推奨事項を理解するのには[Office 365 の管理するエンドポイント](managing-office-365-endpoints.md)を開始します。エンドポイントのデータは、毎月新規の IP アドレスとアクティブにする前に 30 日間の公開 Url の先頭に更新されます。これにより、お客様にとってはまだ自動的に新しい接続が要求される前に、プロセスを完了するのには更新します。エンドポイントのアドレスのサポートのエスカレーション、セキュリティの問題、またはその他の即時の運用上の要件が必要な場合、月の中に更新も可能です。[Office 365 のドイツのエンドポイントへの変更の一覧](office-365-germany-endpoints-change-log.md)に常に参照できます。

REST ベースの web サービスからは、このページの下に表示されているデータすべてが生成されます。このデータにアクセスするスクリプト、またはネットワーク デバイスを使用している場合、 [Web サービス](managing-office-365-endpoints.md#webservice)に直接移動する必要があります。

エンドポイント データの下では、ユーザーのコンピューターから Office 365 への接続の要件を示します。マイクロソフトからお客様のネットワークとも言われますハイブリッドまたは着信ネットワーク接続のネットワーク接続は含まれません。

エンドポイントは、次の 4 つのサービス領域にグループ化されます。最初の 3 つのサービス分野個別に選択できますない接続用。4 番目のサービス エリアは一般的な依存関係 (Microsoft 365 共通と Office オンラインと呼ばれる) とネットワーク接続を持つ必要があります。

表示されるデータ列は次のとおりです。

- **ID**: エンドポイントのセットとも呼ばれる、行の ID 番号です。この ID は、エンドポイントの設定の web サービスによって返されるものと同じです。

- **カテゴリ**: エンドポイントの設定を最適化」では、「許可」または「既定」として分類されたかどうかを示しています。については、これらのカテゴリとでそれらを管理するためのガイダンスを読むことができます[http://aka.ms/pnc](http://aka.ms/pnc)。このコラムでは、どのエンドポイントのセットは、ネットワークに接続する必要も一覧表示されます。ネットワークに接続する必要はありませんがセットのエンドポイント、エンドポイントのセットがブロックされている場合、どのような機能が失われるとを示すためにこのフィールドにメモを提供しています。サービス全体の領域を除外する場合は、必要に応じて表示されているエンドポイントのセットには接続は不要です。

- **ER**: これは、 **[はい]** エンドポイントの設定は Office 365 のルートのプレフィックスを持つ Azure ExpressRoute 経由でサポートされている場合。一覧に [サービス] 領域に表示されているルートのプレフィックスを含む BGP コミュニティを配置します。ER が**No**の場合、このエンドポイントのセットの ExpressRoute がサポートされていないことを意味します。ただし、その必要がありますが想定されていなかった**なし**の ER が、エンドポイントのセットのルートをアドバタイズしないことです。

- **アドレス**: Fqdn またはワイルドカード ドメイン名と IP アドレスの範囲のエンドポイントのセットを一覧表示します。IP アドレスの範囲は CIDR 形式では、指定されたネットワークでは多くの個々 の IP アドレスを含めることことに注意してください。
 
- **ポート**: TCP または UDP のポートを組み合わせて構成されるネットワーク エンドポイントを作成するアドレスの一覧が表示されます。一部重複する IP アドレスの範囲にすることがありますが別のポートを一覧表示します。

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

