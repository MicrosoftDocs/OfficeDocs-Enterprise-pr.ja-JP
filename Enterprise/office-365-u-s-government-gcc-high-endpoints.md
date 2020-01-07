---
title: Office 365 米国政府 GCC GCC (高) エンドポイント
ms.author: laurawi
author: LauraWi
manager: laurawi
ms.date: 01/02/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: 組織で Office 365 を使用していて、ネットワーク上のコンピューターがインターネットに接続できないように制限している場合は、次に示すように、送信許可一覧に含める必要のあるエンドポイント (Fqdn、ポート、Url、IPv4、IPv6 アドレスの範囲) を検索して、コンピューターは Office 365 を正常に使用できます。
hideEdit: true
ms.openlocfilehash: 9d4b0538256a2c65d299572f665c908f678b4538
ms.sourcegitcommit: f9888d1c27e38d3c489a0cbed7684a2e67c3afbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "40951552"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Office 365 米国政府 GCC GCC (高) エンドポイント

 *適用対象: Office 365 Admin*

**概要:** Office 365 には、インターネットへの接続が必要です。 次のエンドポイントには、Office 365 を使用しているお客様が利用できるようにする必要があります。米国政府機関 GCC の高プランのみ
  
> [!NOTE]
> Microsoft は、このページの IP アドレスと FQDN エントリのための REST ベースの Web サービスを開始しました。この新しいサービスは、ファイアウォールやプロキシ サーバーなどのネットワーク境界デバイスの構成と更新に役立ちます。エンドポイントのリスト、リストの現在のバージョン、または特定の変更をダウンロードすることができます。このサービスは、このページからリンクされている XML ドキュメント (2018 年 10 月 2 日に廃止済み) に代わるものです。この新しいサービスを試すには、[[Web サービス]](office-365-ip-web-service.md) にアクセスします。
  
 **Office 365 エンドポイント:** [(GCC を含む) 世界](urls-and-ip-address-ranges.md) | [21Vianet が運営する Office 365](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 ドイツ](office-365-germany-endpoints.md)  |  [Office 365 米国政府機関向け DoD](office-365-u-s-government-dod-endpoints.md) | *Office 365 米国政府 GCC 高* |
  
|||
|:-----|:-----|
|**最終更新日:** 01/02/2020 ![-](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) RSS[変更ログサブスクリプション](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**ダウンロード:** [JSON 形式](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)の完全なリスト <br/> |
   
 [Office 365 エンドポイントの管理](managing-office-365-endpoints.md)から始めて、このデータを使用したネットワーク接続の管理に関する推奨事項を理解してください。 エンドポイントのデータは、各月の最初に、アクティブになる前に30日間公開された新しい IP アドレスと Url で更新されます。 これにより、自動更新を行っていないお客様は、新しい接続が必要になる前にプロセスを完了できます。 サポートのエスカレーション、セキュリティインシデント、またはその他の即時運用要件に対処する必要がある場合は、その月にエンドポイントを更新することもできます。 このページに表示されるデータはすべて、REST ベースの web サービスから生成されます。 このデータにアクセスするためにスクリプトまたはネットワークデバイスを使用している場合は、 [Web サービス](office-365-ip-web-service.md)に直接移動する必要があります。

次のエンドポイント データは、ユーザーのコンピューターを Office 365 に接続するための要件の一覧です。Microsoft からお客様のネットワークへの接続 (“ハイブリッド ネットワーク接続” や ”受信ネットワーク接続” と呼ばれる場合があります) は含まれません。

エンドポイントは 4 つのサービス領域にグループ分けされます。最初の 3 つのサービス領域は個別に接続の選択ができます。4 番目のサービス領域は共通の依存関係 ("Microsoft 365 Common および Office Online" と呼ばれる) で、常時ネットワーク接続されている必要があります。

次のデータ列が表示されます。

- **ID**: エンドポイントのセットとして知られる、行の ID 番号です。この ID は、エンドポイントの Web サービスによって返されるものと同じです。

- **カテゴリ**: エンドポイントのセットが「最適化」、「許可」または「既定」のどれに分類されているかを示します。これらのカテゴリとその管理ガイダンスについては、[https://aka.ms/pnc](https://aka.ms/pnc) を参照してください。この列には、ネットワーク接続に必要なエンドポイントのセットが表示されます。ネットワーク接続が必要ないエンドポイントのセットの場合、このコラムには、エンドポイントのセットがブロックされた場合に使えなくなる機能に関する注意書きが書かれます。サービス領域全体を除外する場合は、ネットワーク接続が必要と記載されているエンドポイントのセットの接続は不要です。

- **ER**: エンドポイントセットが Office 365 のルートプレフィックスを使用して Azure ExpressRoute でサポートされている場合は、これが**Yes**になります。 ルートプレフィックスを含む BGP コミュニティは、表示されている [サービス] 領域に配置されています。 ER が**No**の場合、このエンドポイントセットに対して ExpressRoute がサポートされていないことを意味します。 ただし、ER が**no**であるエンドポイントセットに対してルートがアドバタイズされていないと仮定してはなりません。 Azure AD Connect の使用を計画している場合は、 [「特別な考慮事項」セクション](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government)を参照して、適切な Azure ad connect 構成を持っていることを確認してください。

- **アドレス**: FQDN またはワイルドカードを含むドメイン名と、エンドポイントのセットの IP アドレス範囲を一覧表示します。IP アドレスの範囲は CIDR 形式となり、指定されたネットワークの個別の IP アドレスが多数含まれる場合があることに注意してください。
 
- **ポート**: アドレスと組み合わさることによりネットワーク エンドポイントを形成する TCP または UDP ポートの一覧を表示します。異なるポートが記載されている場合、IP アドレス範囲が重複している場合があります。
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](./includes/office-365-u.s.-government-gcc-high-endpoints.md)]

この表に関するメモ :

- セキュリティ/コンプライアンスセンター (SCC) は、Office 365 用の Azure ExpressRoute のサポートを提供します。 レポート作成、監査、高度な電子情報開示、統合 DLP、データガバナンスなど、SCC を通じて公開されている多くの機能についても同様です。 2つの特定の機能、PST インポートと電子情報開示のエクスポートは、現時点では、Azure Blob ストレージへの依存関係により、Office 365 ルートフィルターのみの Azure ExpressRoute をサポートしていません。 これらの機能を使用するには、azure のパブリックルートフィルターを使用したインターネット接続または Azure ExpressRoute を含む、サポート可能な Azure 接続オプションを使用して、Azure Blob ストレージに個別に接続する必要があります。 これらの機能の両方について、このような接続の確立を評価する必要があります。 Office 365 Information Protection team は、この制限を認識しており、両方の機能の Office 365 ルートフィルターに制限されているため、Office 365 用の Azure ExpressRoute のサポートを積極的に実行しています。

- Office 365 ProPlus には追加オプションのエンドポイントがありますが、ユーザーが Office 365 ProPlus アプリケーションを起動してドキュメントを編集するために必要ではありません。 オプションのエンドポイントは Microsoft データセンターでホストされ、顧客データの処理、転送、保存は行われません。 これらのエンドポイントへのユーザー接続は、既定のインターネット出口境界に向けられるようにすることをお勧めします。

