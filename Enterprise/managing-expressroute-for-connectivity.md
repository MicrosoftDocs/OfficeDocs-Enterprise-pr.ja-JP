---
title: Office 365 向け ExpressRoute の接続を管理する
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: Office 365 用 ExpressRoute は、インターネットに送信されるすべてのトラフィックを必要とせずに、多くの Office 365 サービスにアクセスするための代替ルーティングパスを提供します。 Office 365 へのインターネット接続は依然として必要ですが、Microsoft が BGP を使用してネットワークにアドバタイズする際には、ネットワークに他の構成が存在しない限り、直接 ExpressRoute 回線を優先させる場合があります。 このルーティングを管理するために構成する共通領域には、プレフィックスのフィルター、セキュリティ、コンプライアンスがあります。
ms.openlocfilehash: 163b94bed1bf27b30a3ac8d3079d6fe70d7a1af0
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "38027551"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Office 365 向け ExpressRoute の接続を管理する

Office 365 用 ExpressRoute は、インターネットに送信されるすべてのトラフィックを必要とせずに、多くの Office 365 サービスにアクセスするための代替ルーティングパスを提供します。 Office 365 へのインターネット接続は依然として必要ですが、Microsoft が BGP を使用してネットワークにアドバタイズする際には、ネットワークに他の構成が存在しない限り、直接 ExpressRoute 回線を優先させる場合があります。 このルーティングを管理するために構成する共通領域には、プレフィックスのフィルター、セキュリティ、コンプライアンスがあります。
  
> [!NOTE]
> Microsoft は、Azure ExpressRoute の Microsoft ピアリングルーティングドメインの確認方法を変更しました。 2017年7月31日以降、Azure ExpressRoute のすべてのお客様は、Azure 管理コンソールまたは PowerShell を使用して、Microsoft のピアリングを直接有効にすることができます。 Microsoft ピアリングを有効にした後は、すべてのお客様は、Dynamics 365 カスタマーエンゲージメントアプリケーション (旧称 CRM Online) の BGP route 広告を受信するルートフィルターを作成できます。 Office 365 用の Azure ExpressRoute を必要とするお客様は、Office 365 のルートフィルターを作成する前に、マイクロソフトからレビューを受ける必要があります。 Office 365 ExpressRoute を有効にするためのレビューを要求する方法については、Microsoft アカウントチームにお問い合わせください。 承認されていないサブスクリプション Office 365 のルートフィルターを作成しようとすると、[エラーメッセージ](https://support.microsoft.com/kb/3181709)が表示される
  
## <a name="prefix-filtering"></a>プレフィックスフィルター

Microsoft では、すべての BGP ルートを Microsoft から提供されたとおりにお客様が受け入れることをお勧めします。提供されるルートには、追加された精査のメリットを排除するための厳密なレビューと検証プロセス ExpressRoute はネイティブに、お客様側で受信ルートフィルターを使用せずに、IP プレフィックスの所有権、整合性、スケールなどの推奨されるコントロールを提供します。
  
ExpressRoute のパブリックピア間でルートの所有権を追加で検証する必要がある場合は、アドバタイズされたルートを、 [Microsoft のパブリック ip 範囲](https://www.microsoft.com/download/details.aspx?id=53602)を表す IPv4 および IPv6 のすべての ip プレフィックスの一覧に対して確認できます。 これらの範囲は、完全な Microsoft アドレススペースをカバーしており、頻繁には変更されないため、フィルター処理する範囲の信頼性の高いセットを提供することにより、Microsoft が所有していないルートがリークしているユーザーが、environment. 変更がある場合は、その月の1日に実行され、ページの [**詳細**] セクションのバージョン番号は、ファイルが更新されるたびに変更されます。
  
プレフィックスフィルターリストを生成するために[Office 365 の url と IP アドレスの範囲](https://aka.ms/o365endpoints)を使用しないようにするには、いくつかの理由が考えられます。 次のものが含まれます。
  
- Office 365 の IP プレフィックスは、頻繁に多くの変更を行います。

- Office 365 の Url と IP アドレスの範囲は、ルーティングではなく、ファイアウォールの許可リストとプロキシインフラストラクチャを管理するために設計されています。

- Office 365 の Url と IP アドレスの範囲は、ExpressRoute 接続のスコープ内にある他の Microsoft サービスをカバーしていません。

| |
|**オプション**|**複雑さ**|**変更管理**|
|:-----|:-----|:-----|
|Microsoft のすべてのルートを受け入れる  <br/> |**低:** お客様は Microsoft コントロールに依存して、すべてのルートが適切に所有されていることを確認します。  <br/> |なし  <br/> |
|Microsoft が所有するスーパーネットにフィルターを適用する  <br/> |**中:** 顧客は、Microsoft が所有するルートのみを許可するように、集約されたプレフィックスフィルターリストを実装します。  <br/> |お客様は、頻度の低い更新プログラムがルートフィルターに反映されるようにする必要があります。  <br/> |
|Office 365 IP 範囲のフィルター処理  <br/> [!CAUTION] 推奨されない
|**高:** 顧客は、定義された Office 365 IP プレフィックスに基づいてルートをフィルター処理します。  <br/> |お客様は毎月の更新プログラムに対して、堅牢な変更管理プロセスを実装する必要があります。  <br/> [!CAUTION] このソリューションでは、継続的な変更が必要になります。 時間内に実装されていない変更は、サービスの停止につながる可能性があります。   |

Azure ExpressRoute を使用した Office 365 への接続は、Office 365 エンドポイントが展開されているネットワークを表す特定の IP サブネットの BGP 広告に基づいています。 Office 365 のグローバルな性質と Office 365 を構成するサービスの数により、多くの場合、お客様はネットワークにおいて受け入れる広告を管理する必要があります。 ご使用の環境にアドバタイズされているプレフィックスの数について懸念している場合は、 [BGP コミュニティ](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099)機能を使用して、特定の Office 365 サービスセットに対して広告をフィルター処理することができます。 これで、この機能はプレビューに表示されます。
  
Microsoft からの BGP ルート広告を管理する方法に関係なく、インターネット回線だけ経由で Office 365 に接続するのと比較して、Office 365 サービスに特別な影響を与えることはありません。 Microsoft は、お客様が Office 365 への接続に使用する回線の種類に関係なく、同じセキュリティ、コンプライアンス、およびパフォーマンスレベルを維持します。
  
### <a name="security"></a>セキュリティ

Microsoft では、Office 365 サービスとの接続を含む、ExpressRoute パブリックおよび Microsoft ピアとの間で送受信される接続について、独自のネットワークおよびセキュリティ境界の制御を維持することをお勧めします。 ネットワークから microsoft のネットワークへの受信だけでなく、ネットワークから Microsoft のネットワークへの送信を転送するネットワーク要求には、セキュリティコントロールを設定する必要があります。
  
#### <a name="outbound-from-customer-to-microsoft"></a>お客様から Microsoft への送信
  
コンピューターが Office 365 に接続する場合、接続がインターネットまたは ExpressRoute のどちらで行われているかにかかわらず、同じエンドポイントに接続されます。 使用されている回線に関係なく、Office 365 サービスは、一般的なインターネットの宛先よりも信頼度の高いものとして扱うことをお勧めします。 送信セキュリティ制御は、ポートとプロトコルに焦点を合わせて、公開を減らし、継続的な保守を最小限に抑えます。 必要なポート情報は、「 [Office 365 エンドポイント](https://aka.ms/o365endpoints)リファレンス」の記事で参照できます。
  
追加のコントロールについては、プロキシインフラストラクチャ内で FQDN レベルフィルターを使用して、インターネットまたは Office 365 宛ての一部またはすべてのネットワーク要求を制限または検査することができます。 機能がリリースされ、Office 365 オファーリングが進化するにつれて Fqdn のリストを維持するには、公開された[office 365 エンドポイント](https://aka.ms/o365endpoints)への変更をより強力に管理および追跡する必要があります。
  
> [!CAUTION]
> Microsoft では、Office 365 への送信セキュリティを管理するために IP プレフィックスだけに頼ることはお勧めしません。

|**オプション**|**複雑さ**|**変更管理**|
|:-----|:-----|:-----|
|制限なし  <br/> |**低:** お客様は、Microsoft への送信アクセスを無制限に許可します。  <br/> |なし  <br/> |
|ポートの制限  <br/> |**低:** お客様は、必要なポートで Microsoft への送信アクセスを制限しています。  <br/> |ときどき.  <br/> |
|FQDN の制限  <br/> |**高:** お客様は、公開された Fqdn に基づいて Office 365 への送信アクセスを制限します。  <br/> |月単位の変更。  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Microsoft からお客様への受信
  
Microsoft がネットワークへの接続を開始する必要がある、いくつかのオプションのシナリオがあります。
  
- サインインのパスワードの検証中に ADFS が有効になります。

- [Exchange Server のハイブリッド展開](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)。

- Exchange Online テナントから社内ホストへのメール。

- Sharepoint online からオンプレミスのホストへの SharePoint online メール送信。

- [SharePoint フェデレーションハイブリッド検索](https://technet.microsoft.com/library/dn197174.aspx)。

- [SharePoint ハイブリッド BCS](https://technet.microsoft.com/library/dn197239.aspx )。

- [Skype](https://technet.microsoft.com/library/jj205403.aspx) for business ハイブリッドおよび/または skype for business[フェデレーション](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)。

- [Skype For Business Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx )。

このような接続は、ExpressRoute 回線ではなく、インターネット回線を介して使用して、複雑さを軽減することをお勧めします。 コンプライアンスまたはパフォーマンスによって、これらの受信接続が ExpressRoute 回線経由で受け入れられるようにするには、ファイアウォールまたはリバースプロキシを使用して、受け入れられた接続のスコープを設定することをお勧めします。 [Office 365 エンドポイント](https://aka.ms/o365endpoints)を使用して、右側の FQDN と IP プレフィックスを調べることができます。
  
### <a name="compliance"></a>コンプライアンス

コンプライアンスコントロールに使用するルーティングパスに依存していません。 ExpressRoute またはインターネット回線経由で Office 365 サービスに接続するかどうかに関係なく、コンプライアンスコントロールは変更されません。 Office 365 のさまざまなコンプライアンスおよびセキュリティ証明レベルを確認して、組織のニーズを満たすための最適な選択を判断する必要があります。
  
ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>関連項目

[コンテンツ配信ネットワーク](content-delivery-networks.md)
  
[Office 365 の URL と IP アドレスの範囲](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 エンドポイントの管理](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute for Office 365 のトレーニング](https://channel9.msdn.com/series/aer)
