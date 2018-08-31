---
title: Office 365 向け ExpressRoute の管理
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: Office 365 の ExpressRoute は、すべてのトラフィックをインターネットへの出口を必要とせず多くの Office 365 サービスにアクセスするのには代替ルーティング パスを提供します。Office 365 へのインターネット接続がまだ必要な優先するネットワーク内の他の構成がある場合を除き、直接 ExpressRoute 回路 BGP を通じてネットワークに Microsoft を通知する特定のルートになっています。ルーティングを管理するために構成することが 3 つの一般的な領域では、フィルタ リング、セキュリティ、およびコンプライアンスをプレフィックスします。
ms.openlocfilehash: 5345c4067f4ecf9b1b1bc1a0ad20d6e1f5273f65
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541572"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Office 365 向け ExpressRoute の管理

Office 365 の ExpressRoute は、すべてのトラフィックをインターネットへの出口を必要とせず多くの Office 365 サービスにアクセスするのには代替ルーティング パスを提供します。Office 365 へのインターネット接続がまだ必要な優先するネットワーク内の他の構成がある場合を除き、直接 ExpressRoute 回路 BGP を通じてネットワークに Microsoft を通知する特定のルートになっています。ルーティングを管理するために構成することが 3 つの一般的な領域では、フィルタ リング、セキュリティ、およびコンプライアンスをプレフィックスします。
  
> [!NOTE]
> マイクロソフトでは、Azure ExpressRoute の Microsoft Peering ルーティング ドメインを確認する方法を変更します。2017 年 7 月 31日の開始 Azure ExpressRoute のすべての顧客ができます Microsoft Peering Azure の管理コンソールから直接、または PowerShell を使用しています。Microsoft Peering を有効にすると、すべてのお客様は、Dynamics 365 お客様との契約のアプリケーション (CRM Online と呼ばれていました) の BGP ルートのアドバタイズを受信するルート フィルターを作成できます。Office 365 の Azure ExpressRoute を必要とするお客様は、ルート フィルターを作成するには Office 365 の前に、マイクロソフトからレビューを取得しなければなりません。Office 365 の ExpressRoute を有効にするためのレビューを要求する方法の詳細については、マイクロソフト アカウント チームにお問い合わせください。[エラー メッセージ](https://support.microsoft.com/kb/3181709)を取得するは、承認されていないサブスクリプションの Office 365 のルート フィルターを作成しようとしています。
  
## <a name="prefix-filtering"></a>プレフィックスのフィルター処理

お客様は、マイクロソフトから提供されるよう、すべての BGP 経路をそのまま使用、提供されているルートに対して、追加の調査にすべての利点を削除する厳格なレビューと検証のプロセスのことをお勧めします。ExpressRoute は、着信ルートが顧客側でのフィルタ リングなしでネイティブ IP プレフィックスの所有権、整合性、および拡張性などの推奨されるコントロールを提供します。
  
ExpressRoute パブリック ピアリング経由でルート所有権の追加の検証を必要とする場合は、 [Microsoft のパブリック IP の範囲](https://www.microsoft.com/download/details.aspx?id=53602)を表すすべての IPv4 と IPV6 プレフィックスのリストに対してアドバタイズされたルートを確認できます。これらの範囲がすべての Microsoft のアドレス空間をカバーし、頻繁に変更されない、マイクロソフトではないにリークしているルートを所有している懸念しているお客様にも追加の保護を提供する信頼性の高い一連のフィルターを適用する範囲を提供すること、環境です。変更がある場合に、月の最初に行われ、ファイルが更新されるたびに、ページの [**詳細**] セクションでバージョン番号が変更されます。
  
いくつかのプレフィックスのフィルターの一覧を生成するための[Office 365 の Url と IP アドレスの範囲](https://aka.ms/o365endpoints)の使用を回避するのには理由があります。次のようになります。
  
- Office 365 IP プレフィックスには、多数の頻繁に変更が行われます。

- Office 365 の Url と IP アドレスの範囲は、ファイアウォールの管理用に設計されたルーティングを許可リストおよびプロキシ インフラストラクチャでは、ありません。

- Office 365 の Url と IP アドレスの範囲は、ExpressRoute の接続のスコープ内で可能性のある他のマイクロソフト サービスをカバーしません。

| |
|**オプション**|**複雑さ**|**コントロールを変更します。**|
|:-----|:-----|:-----|
|Microsoft ルートをすべて受け付ける  <br/> |**低:** 顧客は、すべてのルートが正しく所有していることを確認するのにはマイクロソフトのコントロールに依存します。  <br/> |なし  <br/> |
|スーパー ネットを所有しているマイクロソフトのフィルターを適用します。  <br/> |**メディア:** お客様は、ルートを所有しているマイクロソフトのみを許可するフィルター リストの集計プレフィックスを実装します。  <br/> |ユーザーは、ルート フィルターの不定期の更新が反映されることを確認する必要があります。  <br/> |
|Office 365 の IP の範囲にフィルターを適用します。  <br/> [!CAUTION] 非推奨
|**高:** 顧客では、ルートが定義されている Office 365 IP プレフィックスに基づいてフィルター処理します。  <br/> |お客様は、毎月の更新プログラムの堅牢な変更管理プロセスを実装する必要があります。  <br/> [!CAUTION]このソリューションでは、重要な継続的な変更が必要です。変更がサービスの停止になる可能性がありますの時間で実装されていません。   |

Office 365 に接続する Azure ExpressRoute を使用するは、Office 365 エンドポイントが展開されているネットワークを表す特定の IP サブネットの BGP の提供情報に基づきます。Office 365 および Office 365 を構成するサービスの数のグローバル性質上、お客様多くの場合、ネットワーク上で使用する提供情報を管理する必要があります。心配がある場合、環境に通知されたプレフィックスの数を[BGP コミュニティ](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)機能により、Office 365 サービスの特定のセットに広告をフィルター処理できます。この機能は、プレビューのようになりました。
  
マイクロソフトから送信された BGP ルートのアドバタイズを管理する方法に関係なく Office 365 のサービスだけで、インターネット回線経由での Office 365 への接続と比較した場合に特別な危険度が得られない。マイクロソフトでは、同じセキュリティ、コンプライアンス、および顧客が Office 365 への接続に使用する回線の種類に関係なく、パフォーマンス レベルを維持します。
  
### <a name="security"></a>セキュリティ

維持すること、独自ネットワークおよびセキュリティ境界の制御 ExpressRoute を公開し、マイクロソフトのピアリングとの間を通過する接続の Office 365 サービスとの間の接続を含むことをお勧めします。バウンド ネットワークから Microsoft のネットワークへと同様に、ネットワークへのネットワークから受信したネットワーク要求のためにセキュリティ ・ コントロールがあります。
  
#### <a name="outbound-from-customer-to-microsoft"></a>Microsoft にお客様からのアウト バウンド
  
インターネットや ExpressRoute の回路に接続が行われたかどうかに関係なくエンドポイントの同じセットに接続するコンピューターは、Office 365 に接続するとき。回路が使用されているに関係なくより汎用的なインターネットの宛先よりも信頼されていると、Office 365 サービスを扱うことをお勧めします。送信セキュリティ コントロールは、ポートとプロトコルのリスクを軽減し、継続的なメンテナンスを最小限に抑えるに集中する必要があります。必要なポート情報は、 [Office 365 エンドポイント](https://aka.ms/o365endpoints)参照資料に使用できます。
  
追加されたコントロールは、インターネットや Office 365 に送信されるいくつかまたはすべてのネットワーク要求を検査または制限する FQDN のレベルのプロキシ インフラストラクチャ内でフィルター処理を使用できます。Fqdn の一覧を維持する機能がリリースされ、Office 365 サービスを進化させるより堅牢な変更管理と公開された[Office 365 エンドポイント](https://aka.ms/o365endpoints)への変更の追跡が必要です。
  
> [!CAUTION]
> Office 365 に送信のセキュリティを管理するために IP の接頭番号にのみに依存しないことをお勧めします。

|**オプション**|**複雑さ**|**コントロールを変更します。**|
|:-----|:-----|:-----|
|制限なし  <br/> |**低:** お客様は、マイクロソフトに送信無制限にアクセスできます。  <br/> |なし  <br/> |
|ポートの制限  <br/> |**低:** 顧客は、必要なポートがマイクロソフトに送信方向のアクセスを制限します。  <br/> |まれに発生します。  <br/> |
|FQDN の制限  <br/> |**高:** お客様は、公開されている Fqdn に基づいて、Office 365 に送信アクセスを制限します。  <br/> |毎月変更します。  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>お客様にマイクロソフトからの受信
  
ネットワークへの接続を開始するのには必要とするいくつかの省略可能な場合があります。
  
- サインインのパスワードの検証中に ADFS。

- [Exchange Server のハイブリッド展開](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)します。

- 設置型のホストに Exchange Online のテナントからメールです。

- オンライン メールの SharePoint は、SharePoint Online の設置型のホストに送信します。

- [SharePoint は、ハイブリッドの検索を統合](https://technet.microsoft.com/library/dn197174.aspx)します。

- [SharePoint ハイブリッド BCS](https://technet.microsoft.com/library/dn197239.aspx )。

- [ビジネスのハイブリッドの Skype](https://technet.microsoft.com/en-us/library/jj205403.aspx) 、 [Skype](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)。

- [Skype ビジネス クラウド コネクタ](https://technet.microsoft.com/library/mt605227.aspx )です。

ExpressRoute の回路の複雑さを軽減するのではなく、インターネット回線経由でこれらの接続を受け入れることをお勧めします。コンプライアンス、パフォーマンス、ExpressRoute の回路上でこれらの着信接続を受け入れる必要があります音声入力を必要とする場合は、スコープの承認済みの接続にファイアウォールまたはリバース プロキシを使用することをお勧めします。右の Fqdn と IP プレフィックスには、 [Office 365 エンドポイント](https://aka.ms/o365endpoints)を使用できます。
  
### <a name="compliance"></a>準拠

ここに頼らず、当社のコンプライアンス ・ コントロールのいずれかを使用するルーティングのパスです。かどうかに接続する Office 365 サービス、ExpressRoute、またはインターネット接続経由に関係なく、当社のコンプライアンス ・ コントロールは変更されません。さまざまなコンプライアンスと組織のニーズを満たす最適な選択肢を Office 365 のセキュリティ証明書のレベルを確認する必要があります。
  
戻るを使用することができます短いリンクを以下に示します。[https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>関連項目

[コンテンツ配信ネットワーク](content-delivery-networks.md)
  
[Office 365 の URL と IP アドレス範囲](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 エンドポイントを管理します。](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute for Office 365 のトレーニング](https://channel9.msdn.com/series/aer)
