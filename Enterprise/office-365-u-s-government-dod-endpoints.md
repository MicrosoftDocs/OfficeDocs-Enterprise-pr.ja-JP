---
title: Office 365 の米国政府の DoD のエンドポイント
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
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
ms.openlocfilehash: f4412f18407eeb1f9adcb750687f75de8f704fc2
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872318"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 の米国政府の DoD のエンドポイント

*Office 365 の管理者用に適用されます。*

 **の概要:** Office 365 には、インターネットへの接続が必要です。次のエンドポイントは、Office 365 の米国政府の DoD のプランのみを使用して顧客に到達できる必要があります。
  
> [!NOTE]
> Microsoft は、このページの IP アドレスと FQDN エントリのための REST ベースの Web サービスを開始しました。この新しいサービスは、ファイアウォールやプロキシ サーバーなどのネットワーク境界デバイスの構成と更新に役立ちます。エンドポイントのリスト、リストの現在のバージョン、または特定の変更をダウンロードすることができます。このサービスは、このページからリンクされている XML ドキュメント (2018 年 10 月 2 日に廃止済み) に代わるものです。この新しいサービスを試すには、[[Web サービス]](office-365-ip-web-service.md) にアクセスします。
  
 **Office 365 エンドポイント:** [(GCC を含む) 世界](urls-and-ip-address-ranges.md) | [21Vianet が運営する Office 365](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 ドイツ](office-365-germany-endpoints.md) |  *Office 365 米国政府機関向け DoD* | [Office 365 米国政府 GCC 高](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**最終更新日:** 11/28/2018 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [変更ログの購読](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**をダウンロード:** 、 [JSON 形式](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)の完全なリスト <br/> |
   
 このデータを使用してネットワーク接続を管理するための当社の推奨事項を理解するのには[Office 365 の管理するエンドポイント](managing-office-365-endpoints.md)を開始します。エンドポイントのデータは、毎月新規の IP アドレスとアクティブにする前に 30 日間の公開 Url の先頭に更新されます。これにより、自動的に新しい接続が要求される前に、プロセスを完了するのには更新しないとはまだのお客様です。エンドポイントのアドレスのサポートのエスカレーション、セキュリティの問題、またはその他の即時の運用上の要件が必要な場合、月の中に更新も可能です。REST ベースの web サービスからは、このページの下に表示されているデータすべてが生成されます。このデータにアクセスするスクリプト、またはネットワーク デバイスを使用している場合、 [Web サービス](office-365-ip-web-service.md)に直接移動する必要があります。

次のエンドポイント データは、ユーザーのコンピューターを Office 365 に接続するための要件の一覧です。Microsoft からお客様のネットワークへの接続 (“ハイブリッド ネットワーク接続” や ”受信ネットワーク接続” と呼ばれる場合があります) は含まれません。

エンドポイントは 4 つのサービス領域にグループ分けされます。最初の 3 つのサービス領域は個別に接続の選択ができます。4 番目のサービス領域は (“Microsoft 365 Common および Office Online” と呼ばれる) 一般的な依存関係と常時ネットワーク接続されている必要があります。

次のデータ列が表示されます。

- **ID**: エンドポイントのセットとして知られる、行の ID 番号です。この ID は、エンドポイントの Web サービスによって返されるものと同じです。

- **カテゴリ**: エンドポイントのセットが「最適化」、「許可」または「既定」のどれに分類されているかを示します。これらのカテゴリとその管理ガイダンスについては、[http://aka.ms/pnc](http://aka.ms/pnc) を参照してください。この列には、ネットワーク接続に必要なエンドポイントのセットが表示されます。ネットワーク接続が必要ないエンドポイントのセットの場合、このコラムには、エンドポイントのセットがブロックされた場合に使えなくなる機能に関する注意書きが書かれます。サービス領域全体を除外する場合は、ネットワーク接続が必要と記載されているエンドポイントのセットの接続は不要です。

- **ER**: これは、 **[はい]** エンドポイントの設定は Office 365 のルートのプレフィックスを持つ Azure ExpressRoute 経由でサポートされている場合。一覧に [サービス] 領域に表示されているルートのプレフィックスを含む BGP コミュニティを配置します。ER が**No**の場合、このエンドポイントのセットの ExpressRoute がサポートされていないことを意味します。ただし、その必要がありますが想定されていなかった**なし**の ER が、エンドポイントのセットのルートをアドバタイズしないことです。Azure AD 接続を使用する場合は、適切ながあることを確認するのには[特別な考慮事項のセクション](https://docs.microsoft.com/azure/active-directory/connect/active-directory-AADconnect-instances#microsoft-azure-government-cloud)を読んで Azure AD 接続を構成します。

- **アドレス**: FQDN またはワイルドカードを含むドメイン名と、エンドポイントのセットの IP アドレス範囲を一覧表示します。IP アドレスの範囲は CIDR 形式となり、指定されたネットワークの個別の IP アドレスが多数含まれる場合があることに注意してください。
 
- **ポート**: アドレスと組み合わさることによりネットワーク エンドポイントを形成する TCP または UDP ポートの一覧を表示します。異なるポートが記載されている場合、IP アドレス範囲が重複している場合があります。
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
この表に関するメモ :

- セキュリティとコンプライアンス センター (SCC) は、Office 365 の Azure ExpressRoute のサポートを提供します。SCC レポート作成、監査、高度な電子的証拠開示、DLP の統合、データ ・ ガバナンスなどを通じて公開される多くの機能にも当てはまります。、PST のインポートとエクスポートで電子的証拠開示の 2 つの特定機能はサポートされていません Azure ExpressRoute Azure のブロブ ストレージへの依存関係のためのルート フィルターのみを Office 365 にします。これらの機能を利用するには、Azure パブリック ルート フィルターを使用してインターネットに接続または Azure ExpressRoute が含まれて、Azure 接続をサポート可能なオプションを使用した Azure のブロブ ストレージへの個別の接続が必要です。これらの機能の両方のような接続を確立することを評価する必要があります。Office 365 の情報保護チームがこの制限を認識してルート フィルターを Office 365 にこれらの機能の両方の制限としての Office 365 の Azure ExpressRoute のサポートを提供する作業は、積極的にします。

- Office 365 用リソースに示されていないと、ユーザーが Office 365 用リソースのアプリケーションを起動し、ドキュメントを編集する必要はありませんがその他の省略可能なエンドポイントがあります。省略可能なエンドポイント マイクロソフトのデータ センターでホストされているとは処理、転送では、や顧客データを格納します。これらのエンドポイントへのユーザー接続は、既定のインターネットの出口周辺に転送することをお勧めします。
