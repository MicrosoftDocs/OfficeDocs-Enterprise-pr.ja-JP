---
title: Office 365 の米国政府の DoD のエンドポイント
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
description: '概要: Office 365 には、インターネットへの接続が必要です。次のエンドポイントは、Office 365 の米国政府の DoD のプランのみを使用して顧客に到達できる必要があります。'
hideEdit: true
ms.openlocfilehash: 3faca62176b1467829f0333b76a57ce0d5124a96
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541528"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 の米国政府の DoD のエンドポイント

*Office 365 の管理者用に適用されます。*

 **の概要:** Office 365 には、インターネットへの接続が必要です。次のエンドポイントは、Office 365 の米国政府の DoD のプランのみを使用して顧客に到達できる必要があります。
  
> [!NOTE]
> Microsoft では、このページの IP アドレスと FQDN エントリのための REST ベースの Web サービスを開発しています。この新しいサービスは、ファイアウォールやプロキシ サーバーなどのネットワーク境界デバイスの構成と更新に役立ちます。エンドポイントのリスト、リストの現在のバージョン、または特定の変更をダウンロードすることができます。このサービスは、最終的にこのページの XML ドキュメント、RSS フィード、および IP アドレス、FQDN エントリを置き換えます。この新しいサービスを試すには、「[Web サービス](managing-office-365-endpoints.md#webservice)」にアクセスします。
  
 **Office 365 エンドポイント:**[世界の検索サイト (GCC を含む)](urls-and-ip-address-ranges.md) |  [21 Vianet 運用している office 365](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 のドイツ](office-365-germany-endpoints.md) | *Office 365 の米国政府の DoD* | [Office 365 米国政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**最終更新日:** 8/1/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [変更ログの購読](https://aka.ms/dodendpointrss) <br/> |**をダウンロード:** [XML 形式](https://aka.ms/usdodendpoints)の完全なリスト <br/> |
   
 このデータを使用してネットワーク接続を管理するための当社の推奨事項を理解するのには[Office 365 の管理するエンドポイント](managing-office-365-endpoints.md)を開始します。エンドポイントのデータは、毎月新規の IP アドレスとアクティブにする前に 30 日間の公開 Url の先頭に更新されます。これにより、お客様にとってはまだ自動的に新しい接続が要求される前に、プロセスを完了するのには更新します。エンドポイントのアドレスのサポートのエスカレーション、セキュリティの問題、またはその他の即時の運用上の要件が必要な場合、月の中に更新も可能です。REST ベースの web サービスからは、このページの下に表示されているデータすべてが生成されます。このデータにアクセスするスクリプト、またはネットワーク デバイスを使用している場合、 [Web サービス](managing-office-365-endpoints.md#webservice)に直接移動する必要があります。

エンドポイント データの下では、ユーザーのコンピューターから Office 365 への接続の要件を示します。マイクロソフトからお客様のネットワークとも言われますハイブリッドまたは着信ネットワーク接続のネットワーク接続は含まれません。

エンドポイントは、次の 4 つのサービス領域にグループ化されます。最初の 3 つのサービス分野個別に選択できますない接続用。4 番目のサービス エリアは一般的な依存関係 (Microsoft 365 共通と Office オンラインと呼ばれる) とネットワーク接続を持つ必要があります。

表示されるデータ列は次のとおりです。

- **ID**: エンドポイントのセットとも呼ばれる、行の ID 番号です。この ID は、エンドポイントの設定の web サービスによって返されるものと同じです。

- **カテゴリ**: エンドポイントの設定を最適化」では、「許可」または「既定」として分類されたかどうかを示しています。については、これらのカテゴリとでそれらを管理するためのガイダンスを読むことができます[http://aka.ms/pnc](http://aka.ms/pnc)。このコラムでは、どのエンドポイントのセットは、ネットワークに接続する必要も一覧表示されます。ネットワークに接続する必要はありませんがセットのエンドポイント、エンドポイントのセットがブロックされている場合、どのような機能が失われるとを示すためにこのフィールドにメモを提供しています。サービス全体の領域を除外する場合は、必要に応じて表示されているエンドポイントのセットには接続は不要です。

- **ER**: これは、 **[はい]** エンドポイントの設定は Office 365 のルートのプレフィックスを持つ Azure ExpressRoute 経由でサポートされている場合。一覧に [サービス] 領域に表示されているルートのプレフィックスを含む BGP コミュニティを配置します。ER が**No**の場合、このエンドポイントのセットの ExpressRoute がサポートされていないことを意味します。ただし、その必要がありますが想定されていなかった**なし**の ER が、エンドポイントのセットのルートをアドバタイズしないことです。Azure AD 接続を使用する場合は、適切ながあることを確認するのには[特別な考慮事項のセクション](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud)を読んで Azure AD 接続を構成します。

- **アドレス**: Fqdn またはワイルドカード ドメイン名と IP アドレスの範囲のエンドポイントのセットを一覧表示します。IP アドレスの範囲は CIDR 形式では、指定されたネットワークでは多くの個々 の IP アドレスを含めることことに注意してください。
 
- **ポート**: TCP または UDP のポートを組み合わせて構成されるネットワーク エンドポイントを作成するアドレスの一覧が表示されます。一部重複する IP アドレスの範囲にすることがありますが別のポートを一覧表示します。
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
この表に関するメモ :

- セキュリティとコンプライアンス センター (SCC) は、Office 365 の Azure ExpressRoute のサポートを提供します。SCC レポート作成、監査、高度な電子的証拠開示、DLP の統合、データ ・ ガバナンスなどを通じて公開される多くの機能にも当てはまります。、PST のインポートとエクスポートで電子的証拠開示の 2 つの特定機能はサポートされていません Azure ExpressRoute Azure のブロブ ストレージへの依存関係のためのルート フィルターのみを Office 365 にします。これらの機能を利用するには、Azure パブリック ルート フィルターを使用してインターネットに接続または Azure ExpressRoute が含まれて、Azure 接続をサポート可能なオプションを使用した Azure のブロブ ストレージへの個別の接続が必要です。これらの機能の両方のような接続を確立することを評価する必要があります。Office 365 の情報保護チームがこの制限を認識してルート フィルターを Office 365 にこれらの機能の両方の制限としての Office 365 の Azure ExpressRoute のサポートを提供する作業は、積極的にします。

- Office 365 用リソースに示されていないと、ユーザーが Office 365 用リソースのアプリケーションを起動し、ドキュメントを編集する必要はありませんがその他の省略可能なエンドポイントがあります。省略可能なエンドポイント マイクロソフトのデータ センターでホストされているとは処理、転送では、や顧客データを格納します。これらのエンドポイントへのユーザー接続は、既定のインターネットの出口周辺に転送することをお勧めします。
